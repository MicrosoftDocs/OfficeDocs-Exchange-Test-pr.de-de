---
title: Problembehandlung beim UM.CallRouter-Integritätssatz
TOCTitle: Problembehandlung beim UM.CallRouter-Integritätssatz
ms:assetid: 444a9038-0952-4823-98fb-99fa59f4a378
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.um.callrouter(v=EXCHG.150)
ms:contentKeyID: 53181858
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim UM.CallRouter-Integritätssatz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem Microsoft Exchange Unified Messaging-Anrufrouter-Integritätssatz (UM) wird die Gesamtintegrität des UM-Anrufrouterdiensts überwacht.

Wenn Sie eine Warnung erhalten, dass UM-Integritätsfehler vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell an der Verwendung des UM-Diensts in Ihrer Organisation hindert. Der UM-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

[Problembehandlung beim UM-Integritätssatz](troubleshooting-um-health-set.md)

[Problembehandlung beim UM.Protocol-Integritätssatz](troubleshooting-um-protocol-health-set.md)

## Erläuterung

Der UM.Protocol-Dienst wird mithilfe der folgenden Tests und Monitore überwacht


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Test</th>
<th>Integritätssatz</th>
<th>Abhängigkeiten</th>
<th>Zugehörige Monitore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UMCallRouterTestProbe</p></td>
<td><p>UM.CallRouter</p></td>
<td><p>Active Directory-Domänendienste (AD DS)</p></td>
<td><p>UMCallRouterTestMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des UM.CallRouter-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "UM.CallRouter"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor, der sich in einem fehlerhaften Zustand befindet, zugeordnet ist. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **UMCallRouterTestMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **UMCallRouterTestProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe UM.CallRouter\UMCallRouterTestMonitor -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## Schritte zur Problembehandlung

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Uhrzeit und Datum des Auftretens der Warnung

  - Verwendeter Authentifizierungsmechanismus und Anmeldeinformationen

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen
    
    **Hinweis**   Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt.

**SIP-Optionen zum UM-Anrufrouterdienst sind fehlgeschlagen**

Bestimmen Sie, ob der UM-Anrufrouterdienst deaktiviert ist. Wenn der UM-Anrufrouterdienst nicht gestartet oder deaktiviert ist, starten Sie den UM-Dienst neu.

**Mehr als 50 % der eingehenden Anrufe wurden vom UM-Anrufrouterdienst in der letzten Stunde zurückgewiesen**

Überprüfen Sie die Ereignisprotokolle auf dem Clientzugriffsserver, um zu bestimmen, ob die UM-Objekte wie **umipgateway** und **umhuntgroup** ordnungsgemäß konfiguriert sind.

Wenn die Ereignisprotokolle keine ausreichenden Informationen enthalten, müssen Sie eventuell die UM-Ereignisprotokolle mit der Stufe "Experte" aktivieren und dann die UM-Ablaufverfolgungs-Protokolldateien prüfen.

**Mehr als {0} % der Proxys für Benachrichtigungen über verpasste Anrufe waren in der letzten Stunde am UM-Anrufrouter fehlerhaft**

Überprüfen Sie die Ereignisprotokolle auf dem Clientzugriffsserver, um zu bestimmen, ob die UM-Objekte wie **umipgateway** und **umhuntgroup** ordnungsgemäß konfiguriert sind.

Wenn die Ereignisprotokolle keine ausreichenden Informationen enthalten, müssen Sie eventuell die UM-Ereignisprotokolle mit der Stufe "Experte" aktivieren und dann die UM-Ablaufverfolgungs-Protokolldateien prüfen.

**Das Microsoft Exchange Unified Messaging-Anrufrouterzertifikat nähert sich seinem Ablaufdatum**

Erneuern Sie das UM-Anrufrouterdienst-Zertifikat auf dem Clientzugriffsserver.

**Zusätzliche Schritte zur Problembehandlung:** 

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu bestimmen, ob der Anwendungspool **MSExchangeServicesAppPool** ausgeführt wird.

2.  Klicken Sie im IIS-Manager auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeServicesAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeServicesAppPool

3.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

4.  Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden oder den folgenden Befehl ausführen:
    
        Iisreset /noforce

5.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

6.  Wenn das Problem weiterhin besteht, starten Sie den Server neu.

7.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

[Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

