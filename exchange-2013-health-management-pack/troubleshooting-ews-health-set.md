---
title: Problembehandlung beim EWS-Integritätssatz
TOCTitle: Problembehandlung beim EWS-Integritätssatz
ms:assetid: f5aaacdd-7f4a-4d63-8440-1c564e644dfc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.ews(v=EXCHG.150)
ms:contentKeyID: 53181879
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim EWS-Integritätssatz

 

_**Gilt für:**Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit dem EWS-Integritätssatz (Exchange-Webdienste) wird die Gesamtintegrität des EWS-Diensts überwacht. Der EWS-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

[Problembehandlung beim EWS.Protocol-Integritätssatz](troubleshooting-ews-protocol-health-set.md)

[Problembehandlung beim EWS.Proxy-Integritätssatz](troubleshooting-ews-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im EWS vorliegen, weist dies auf ein Problem hin, das Ihre Benutzer eventuell an der Kommunikation mit dem Exchange-Server hindert.

## Erläuterung

EWS wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>EwsCtpProbe</p></td>
<td><p>EWS</p></td>
<td><p>Informationsspeicher</p>
<p>Active Directory-Domänendienste (AD DS)</p></td>
<td><p>EwsCtpMonitor (EWS-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>EwsSelfTestProbe</p></td>
<td><p>EWS.Protocol</p></td>
<td><p>Active Directory-Domänendienste (AD DS)</p></td>
<td><p>EWSSelfTestMonitor</p></td>
</tr>
<tr class="odd">
<td><p>EwsDeepTestProbe</p></td>
<td><p>EWS.Protocol</p></td>
<td><p>Informationsspeicher</p></td>
<td><p>EWSDeepTestMonitor</p></td>
</tr>
</tbody>
</table>


Dieser Test führt unter Verwendung eines Überwachungskontos eine vollständige EWS-Anmeldung vom Clientzugriffsserver aus bei einem Postfachserver durch. Dieser Test ruft die Methode **GetFolder** für EWS auf. Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Bei diesem Test kann aus einer der folgenden häufigen Ursachen ein Fehler auftreten:

  - Zwischen dem von dem Test verwendeten Authentifizierungsmechanismus und dem, der im virtuellen Verzeichnis des Clientzugriffsservers verwendet wird, besteht ein Konflikt.

  - Der EWS-Anwendungspool auf dem überwachten Clientzugriffsserver reagiert nicht.

  - Der Clientzugriffsserver hat Netzwerkprobleme beim Herstellen einer Verbindung mit dem Postfachserver.

  - Der Clientzugriffsserver hat Kommunikationsprobleme beim Herstellen einer Verbindung mit Domänencontrollern.

  - Die Domänencontroller reagieren nicht.

  - Der EWS-Anwendungspool, der sich auf mindestens einem Postfachserver befindet, reagiert nicht.

  - Die Datenbank des Benutzers ist nicht eingebunden, oder ein bestimmtes Postfach hat keinen Zugriff auf den Informationsspeicher.

  - Der Informationsspeicherdienst auf mindestens einem Postfachserver hat Probleme.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.
    
    Wenn Sie eine Warnung von diesem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:
    
    1.  Name des Clientzugriffsservers, von dem die Warnung stammt
    
    2.  Name des Postfachservers, der von dem Test als Zielressource überwacht wurde
    
    3.  Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen
    
    4.  Uhrzeit des Auftretens des Vorfalls
    
    5.  Verwendeter Authentifizierungsmechanismus und Anmeldeinformationen
    
    Die Informationen der Ausnahmeablaufverfolgung bieten den wichtigsten Hinweis auf die Ursache für das Fehlschlagen des Tests. Die Eskalationsnachricht enthält auch die folgenden HTTP-Header:
    
    1.  **X-FEServer**   Gibt an, auf welchem Clientzugriffsserver der Test ausgeführt wurde
    
    2.  **X-TargetBEServer**   Gibt an, an welchen MBX-Server die Anforderung weitergeleitet wird
    
    3.  **X-DiagInfo**   Gibt den MBX-Server an, der die Anforderung empfangen hat

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des EWS-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "EWS"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise für den EWS-Integritätssatz **EWSCtpMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **EWSCtpProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe EWS\EWSCtpProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## EwsCtpMonitor-Wiederherstellungsaktionen

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu bestimmen, ob der Anwendungspool **MSExchangeServicesAppPool** sowohl auf dem Clientzugriffsserver als auch auf dem Postfachserver ausgeführt wird.

2.  Suchen Sie die Postfachdatenbank für fehlgeschlagene Tests. Überprüfen Sie dann, ob die Postfachdatenbank auf dem Postfachserver aktiv und ob der Postfachspeicher fehlerfrei ist.

3.  Klicken Sie auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeServicesAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeServicesAppPool

4.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

5.  Wenn das Problem weiterhin besteht, starten Sie den gesamten IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

6.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

7.  Wenn das Problem weiterhin besteht, überprüfen Sie die Protokolldateien auf dem Clientzugriffsserver und den Postfachservern. Die Protokolle für den Clientzugriffsserver befinden sich im Ordner "*\<Installationsverzeichnis des Exchange-Servers\>\\Logging\\HttpProxy\\Ews*". Auf dem Postfachserver befinden sich die Protokolle im Ordner "*\<Installationsverzeichnis des Exchange-Servers\>\\Logging\\Ews*".

8.  Erstellen Sie ein Testbenutzerkonto, und melden Sie sich dann an, indem Sie das Testbenutzerkonto auf dem angegebenen Clientzugriffsserver ausführen. Melden Sie sich beispielsweise über folgende URL an: https:// \<servername\>/ews/exchange.asmx. Wenn das Problem weiterhin besteht, versuchen Sie es mit einem anderen Clientzugriffsserver, um zu bestimmen, ob das Problem nur diesen Clientzugriffsserver betrifft und nicht auch den Postfachserver. Wenn der Testbenutzername akzeptiert wird, können die spezifische Postfachdatenbank oder der spezielle Postfachserver, auf dem sich das Überwachungspostfach befindet, von einem Problem betroffen sein. Versuchen Sie, diesen Schritt zu wiederholen, indem Sie ein Testkonto verwenden, das in der Postfachdatenbank vorhanden ist.

9.  Überprüfen Sie die Netzwerkkonnektivität zwischen dem Clientzugriffsserver und dem Postfachserver.

10. Überprüfen Sie den EWS.Proxy-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Clientzugriffsserver betrifft.

11. Überprüfen Sie den EWS.Protocol-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Postfachserver betrifft.

12. Wenn das Problem weiterhin besteht, starten Sie den Server neu. Führen Sie hierzu zuerst ein Failover der Datenbanken durch, die auf dem Server gehostet sind. Führen Sie dazu den folgenden Befehl aus:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $true
    
    **Hinweis**   In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.

13. Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
    
        Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status
    
    Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu.

14. Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

15. Ist der Test erfolgreich, führen Sie ein Failover der Datenbanken zurück auf den Postfachserver durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

16. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

