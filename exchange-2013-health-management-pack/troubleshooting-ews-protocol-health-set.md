---
title: Problembehandlung beim EWS.Protocol-Integritätssatz
TOCTitle: Problembehandlung beim EWS.Protocol-Integritätssatz
ms:assetid: 826b2d5b-adbb-4bf5-94b6-0a8de2e3aac0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.ews.protocol(v=EXCHG.150)
ms:contentKeyID: 53181863
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim EWS.Protocol-Integritätssatz

 

_**Gilt für:** Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem EWS.Protocol-Integritätssatz wird das Kommunikationsprotokoll der Exchange-Webdienste (EWS) auf dem Postfachserver überwacht. Der EWS.Protocol-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

[Problembehandlung beim EWS-Integritätssatz](troubleshooting-ews-health-set.md)

[Problembehandlung beim EWS.Proxy-Integritätssatz](troubleshooting-ews-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im EWS.Protocol vorliegen, weist dies auf ein Problem hin, das Ihre Benutzer eventuell am Zugriff auf Exchange hindert.

## Erläuterung

Der EWS.Protocol-Integritätssatz besteht aus folgenden Tests:

1.  EwsSelfTestProbe

2.  EwsDeepTestProbe

Der EwsSelfTestProbe ist nicht vom Informationsspeicher abhängig. Der EwsDeepTestProbe jedoch ist vom Informationsspeicher abhängig. Beide Tests führen EWS-Vorgänge auf dem Postfachserver aus und verwenden dieselbe Authentifizierungsmethode wie ein Clientzugriffsserver. EwsSeftTestProbe ruft die Methode **ConvertId** auf und EwsDeepTestProbe die Methode **GetFolder**.


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
<td><p>EwsSelfTestProbe</p></td>
<td><p>EWS.Protocol</p></td>
<td><p>Active Directory</p></td>
<td><p>EWSSelfTestMonitor</p></td>
</tr>
<tr class="even">
<td><p>EwsDeepTestProbe</p></td>
<td><p>EWS.Protocol</p></td>
<td><p>Informationsspeicher</p></td>
<td><p>EWSDeepTestMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

Wenn Sie eine Warnung von diesem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

1.  Name des Postfachservers, von dem die Warnung gesendet wurde

2.  Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen

3.  Uhrzeit des Auftretens des Vorfalls

## Häufige Probleme

Bei diesem Test kann aus einer der folgenden häufigen Ursachen ein Fehler auftreten:

  - Der EWS-Anwendungspool auf dem überwachten Postfachserver funktioniert nicht ordnungsgemäß.

  - Die Domänencontroller reagieren nicht, oder sie können nicht mit dem Postfachserver kommunizieren.

  - Die Datenbank des Benutzers ist nicht eingebunden, oder ein bestimmtes Postfach hat keinen Zugriff auf den Informationsspeicher.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des EWS.Protocol-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "EWS.Protocol"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor, der sich in einem fehlerhaften Zustand befindet, zugeordnet ist. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **EWSSelfTestMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **EWSSelfTestProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe EWS.Protocol\EWSSelfTestProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## EWSSelfTestMonitor- und EWSDeepTestMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise für Postfachserver ausgegeben.

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu bestimmen, ob der "MSExchangeServicesAppPool" sowohl auf dem Clientzugriffsserver als auch auf dem Postfachserver ausgeführt wird.

2.  Suchen Sie die Postfachdatenbank für fehlgeschlagene Tests, und überprüfen Sie, ob die Postfachdatenbank auf dem Postfachserver aktiv und ob der Informationsspeicher fehlerfrei ist.

3.  Klicken Sie auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeServicesAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeServicesAppPool

4.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

5.  Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

6.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

7.  Wenn das Problem weiterhin besteht, überprüfen Sie die Protokolldateien auf dem Postfachserver. Auf dem Postfachserver befinden sich die Protokolle im Ordner "*\<Installationsverzeichnis des Exchange-Servers\>*\\Logging\\Ews".

8.  Erstellen Sie ein Testbenutzerkonto, und melden Sie sich dann beim angegebenen Postfachserver am Port 444 mithilfe des Testbenutzerkontos an, beispielsweise "https://*\<Servername\>*:444/ews/exchange.asmx". Wenn der Test erfolgreich ist, können die spezifische Postfachdatenbank oder der Postfachserver, auf dem sich das Überwachungspostfach befindet, von einem Problem betroffen sein. Versuchen Sie, diesen Schritt zu wiederholen, indem Sie ein Testkonto für diese Datenbank verwenden.

9.  Überprüfen Sie den EWS.Protocol-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das den bestimmten Postfachserver betrifft.

10. Wenn das Problem weiterhin besteht, starten Sie den Server neu. Führen Sie hierzu zuerst ein Failover der Datenbanken durch, die auf dem Server gehostet sind, indem Sie den folgenden Befehl verwenden:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $true
    
    In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.

11. Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
    
        Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status
    
    Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, kann der Server sicher neu gestartet werden. Starten Sie den Server neu.

12. Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

13. Ist der Test erfolgreich, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

14. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

