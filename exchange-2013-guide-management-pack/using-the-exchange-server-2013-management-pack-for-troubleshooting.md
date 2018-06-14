---
title: Verwenden des Exchange Server 2013-Management Packs für die Problembehandlung
TOCTitle: Verwenden des Exchange Server 2013-Management Packs für die Problembehandlung
ms:assetid: c9672dad-1e67-4f07-bad9-539a67f2ac70
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn195913(v=EXCHG.150)
ms:contentKeyID: 53181887
ms.author: dstrome
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden des Exchange Server 2013-Management Packs für die Problembehandlung

 

_**Letztes Änderungsdatum des Themas:** 2013-04-09_

[Erste Schritte mit Exchange Server 2013 Management Pack](getting-started-with-exchange-server-2013-management-pack.md) bietet eine Übersicht über das Management Pack-Dashboard. In diesem Thema wird schrittweise erläutert, wie Sie damit ein Problem beheben können. Der Vorgang lässt sich am besten mit einem Beispiel erläutern. Betrachten Sie das folgende Szenario:

Rob Fielder ist ein Exchange-Administrator bei Contoso. Er öffnet die SCOM-Konsole und klickt im Exchange Server 2013-Dashboard auf **Serverstatus**, um den Status der Exchange-Server zu prüfen. Er stellt bei den **Dienstkomponenten** auf einem der CAS-Server einen kritischen Status fest.

![CAS-Server fehlgeschlagen](images/Dn195913.32a265d9-68e0-4d8c-9f83-1d10cdda1f84(EXCHG.150).png "CAS-Server fehlgeschlagen")

Rob doppelklickt auf den Server, wodurch das Fenster **Integritäts-Explorer** geöffnet wird. In diesem Fenster kann er sehen, dass es sich bei der Dienstkomponente, die einen fehlerhaften Zustand aufweist, um den OWA.Proxy-Integritätssatz handelt. Er klickt auf die Komponente, um die relevanten Informationen für diesen Integritätssatz anzuzeigen.

![CAS-Server fehlgeschlagen Details zu Integritätssatz](images/Dn195913.8e4d05a6-9128-40d8-b262-e60e9affc973(EXCHG.150).png "CAS-Server fehlgeschlagen Details zu Integritätssatz")

Der unter "External Knowledge Resources" angegebene Link führt Rob zum Thema [Problembehandlung beim OWA.Proxy-Integritätssatz](https://technet.microsoft.com/de-de/library/jj737712\(v=exchg.150\)). In diesem Artikel erfährt Rob, dass er als Erstes überprüfen muss, ob das Problem noch besteht. Er führt den folgenden Befehl gemäß Anleitung aus, um den aktuellen Zustand des OWA.Proxy-Integritätssatzes in der Shell zu überprüfen:

    Get-ServerHealth Server1.contoso.com | ?{$_.HealthSetName -eq "OWA.Proxy"}

Die Ausführung dieses Befehls liefert die folgende Ausgabe:

    Server          State           Name                 TargetResource       HealthSetName   AlertValue ServerComp
                                                                                                         onent
    ------          -----           ----                 --------------       -------------   ---------- ----------
    Server1         Online          OWAProxyTestMonitor  MSExchangeOWAAppPool OWA.Proxy       Unhealthy  OwaProxy
    Server1         Online          OWAProxyTestMonitor  MSExchangeOWACale... OWA.Proxy       Healthy    OwaProxy

Rob erkennt, dass das Problem im OWA-Anwendungspool liegt. Als nächsten Schritt muss er den Test erneut ausführen, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Aus der Tabelle im Thema "Problembehandlung beim OWA.Proxy-Integritätssatz" leitet er ab, dass er den Test "OWAProxyTestProbe" erneut ausführen muss. Er führt den folgenden Befehl aus:

    Invoke-MonitoringProbe OWA.Proxy\OWAProxyTestProbe -Server Server1.contoso.com | Format-List

Er prüft die Ausgabe für den Wert "ResultType" und stellt fest, dass beim Test ein Fehler auftrat:

    ResultType : Failed

Er fährt mit dem Abschnitt "OWAProxyTestMonitor-Wiederherstellungsaktionen" des Artikels fort. Er stellt über IIS-Manager eine Verbindung zu Server1 her, um zu sehen, ob der MSExchangeOWAAppPool auf dem IIS-Server ausgeführt wird. Nachdem er bestätigt hat, dass er ausgeführt wird, startet er den MSExchangeOWAAppPool neu, wie im nächsten Schritt beschrieben.

    C:\Windows\System32\Inetsrv\Appcmd recycle APPPOOL MSExchangeOWAAppPool

Als er feststellt, dass der MSExchangeOWAAppPool erfolgreich neu gestartet wurde, prüft er erneut, ob das Problem weiterhin besteht. Dazu führt er den Test mithilfe des Cmdlets Invoke-MonitoringProbe erneut aus, und er sieht, dass das Ergebnis diesmal positiv ist. Dann führt er den folgenden Befehl aus, um zu überprüfen, ob der Integritätssatz wieder den Status **Fehlerfrei** meldet:

    Get-ServerHealth Server1.contoso.com | ?{$_.HealthSetName -eq "OWA.Proxy"}

Diesmal sieht er, dass das Problem behoben ist.

    Server          State           Name                 TargetResource       HealthSetName   AlertValue ServerComp
                                                                                                         onent
    ------          -----           ----                 --------------       -------------   ---------- ----------
    Server1         Online          OWAProxyTestMonitor  MSExchangeOWAAppPool OWA.Proxy       Healthy    OwaProxy
    Server1         Online          OWAProxyTestMonitor  MSExchangeOWACale... OWA.Proxy       Healthy    OwaProxy

Er kehrt zur SCOM-Konsole zurück und bestätigt, dass das Problem behoben wurde.

![Zustand des Servers](images/Dn195908.c863be83-fc4b-4daf-a18b-27b1aae15b1d(EXCHG.150).png "Zustand des Servers")

Das oben beschriebene Szenario ist eine einfache Demonstration des Arbeitsablaufs zur Fehlerbehebung, wenn in der SCOM-Konsole eine Warnmeldung angezeigt wird. Sie können bei Problemen, die in der Konsole gemeldet werden, i. d. R. einen ähnlichen Arbeitsablauf zur Fehlerbehebung befolgen, auch wenn Einzelheiten variieren.

