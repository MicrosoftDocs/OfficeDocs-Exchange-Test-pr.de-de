---
title: Problembehandlung beim Autodiscover.Proxy-Integritätssatz
TOCTitle: Problembehandlung beim Autodiscover.Proxy-Integritätssatz
ms:assetid: b6a817cf-0b85-4620-adb7-cc3616c11268
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.autodiscover.proxy(v=EXCHG.150)
ms:contentKeyID: 53181868
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim Autodiscover.Proxy-Integritätssatz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem Autodiscover.Proxy-Integritätssatz wird die Verfügbarkeit der AutoErmittlungs-Proxyinfrastruktur auf dem Clientzugriffsserver überwacht. Der Autodiscover.Proxy-Integritätssatz steht in enger Beziehung mit dem folgenden Integritätssatz:

[Troubleshooting ClientAccess.Proxy Health Set](troubleshooting-clientaccess-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im Autodiscover.Proxy vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Ermitteln ihrer Postfächer mithilfe des Exchange-AutoErmittlungsprozesses hindert.

## Erläuterung

Der AutoErmittlungsdienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>AutoDiscoverProxyTestProbe</p></td>
<td><p>Autodiscover.Proxy</p></td>
<td><p>Active Directory</p></td>
<td><p>AutodiscoverProxyTestMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Bei diesem Test kann aus einer der folgenden häufigen Ursachen ein Fehler auftreten:

  - Der Anwendungspool, der auf dem überwachten Clientzugriffsserver gehostet wird, funktioniert nicht ordnungsgemäß.

  - Die Anmeldeinformationen des Überwachungskontos sind fehlerhaft.

  - Die Domänencontroller reagieren nicht.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des Autodiscover.Protocol-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "Autodiscover.Protocol"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **AutodiscoverSelfTestMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **AutodiscoverSelfTestProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe Autodiscover.Protocol\AutodiscoverSelfTestProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## AutodiscoverProxyTestMonitor-Wiederherstellungsaktionen

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Clientzugriffsservers, von dem die Warnung gesendet wurde

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen
    
    Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein.

  - Uhrzeit und Datum des Auftretens des Problems

Führen Sie zum Behandeln dieses Problems die folgenden Schritte aus:

1.  Überprüfen Sie die Protokolle auf dem Clientzugriffsserver. Protokolle befinden sich auf dem jeweiligen Clientzugriffsserver im Ordner "*\<Installationsverzeichnis des Exchange-Servers\>*\\Logging\\HttpProxy*\\\<Protokoll\>*".

2.  Erstellen Sie ein Testbenutzerkonto, und melden Sie sich dann beim Clientzugriffsserver an, indem Sie das Testbenutzerkonto verwenden. Melden Sie sich beispielsweise über folgende URL an: https://*\<Servername\>*/owa.

3.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird. Überprüfen Sie, ob der MSExchangeAutodiscoverAppPool auf dem Clientzugriffsserver ausgeführt wird.

4.  Klicken Sie auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeAutoDiscoverAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeAutoDiscoverAppPool

5.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

6.  Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

7.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

8.  Wenn das Problem weiterhin besteht, starten Sie den Server neu.

9.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

10. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

[AutoErmittlungsdienst](https://technet.microsoft.com/de-de/library/bb124251\(v=exchg.150\))

