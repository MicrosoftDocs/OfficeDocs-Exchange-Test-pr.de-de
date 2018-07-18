---
title: Problembehandlung beim MRS-Integritätssatz
TOCTitle: Problembehandlung beim MRS-Integritätssatz
ms:assetid: 21947ed6-1584-4db9-9cd6-f6c1de22e352
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.mrs(v=EXCHG.150)
ms:contentKeyID: 53181857
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim MRS-Integritätssatz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem MRS-Integritätssatz (Postfachreplikationsdienst) wird die Gesamtintegrität des MRS-Diensts überwacht.

## Erläuterung

Der MRS-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>MRSServiceCrashingProbe</p></td>
<td><p>MRS</p></td>
<td><p>Informationsspeicher</p></td>
<td><p>MRSServiceCrashingMonitor</p></td>
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
        
        Um beispielsweise die Details des MRS-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "MRS"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **MRSServiceCrashingMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **MRSServiceCrashingProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe MRS\MRSServiceCrashingProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## Häufige Probleme

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Uhrzeit und Datum des Auftretens der Warnung

  - Verwendeter Authentifizierungsmechanismus und Anmeldeinformationen

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen
    
    Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt.

**Postfach gesperrt**

Wenn ein Postfach gesperrt ist, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*MailboxIdentity: namprd03.prod.outlook.com/Microsoft Exchange Hosted Organizations/example.com/User6 MailboxGuid: Primär (00000000-abcd-01234-5678-1234567890ab) RequestFlags: IntraOrg, Pull, Protected Datenbank: exampledb-db089 Ausnahme: MapiExceptionADUnavailable: Der Cache für Benutzer … kann nicht voraufgefüllt werden.*

Dies weist darauf hin, dass ein Postfach gesperrt ist. Führen Sie zum Aufheben der Sperrung des Postfachs den folgenden Befehl aus:

    New-MailboxRepairRequest -CorruptionType LockedMoveTarget -Identity <mailboxIdentity> [-Archive]

**Hinweis**   Ersetzen Sie in diesem Befehl \<*mailboxIdentity*\> durch den Namen des Postfachs, das in der E-Mail als **MailboxIdentity** angegeben ist. Wenn es sich bei dem Postfach um ein Archivpostfach handelt, müssen Sie das **–Archive**-Flag verwenden. Sie können bestimmen, ob ein Postfach ein primäres oder ein Archivpostfach ist, indem Sie das Feld **MailboxGuid** in der Warnung überprüfen.

**Beschädigter Migrationsauftrag**

Wenn ein beschädigter Migrationsauftrag auftritt, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*Benachrichtigung ausgelöst durch MailboxMigration am 07.09.2012 21:08:32. Details: Diagnoseinformationen: ProcessCacheEntry: Erste Organisation:: /o=ExchangeLabs/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=e80fc128879e452ebc882f6bca7007fa-Migration.8*

Beschädigungen treten auf, wenn bei den Migrationsmetadaten Probleme aufgetreten sind. Im Fall von Beschädigungen erhält Microsoft einen Watson-Bericht, der geprüft wird. Um dieses Problem zu beheben, müssen Sie den Migrationsbatch entfernen und dann neu erstellen. Führen Sie zu diesem Zweck die folgenden Schritte aus:

1.  Führen Sie zum Entfernen des beschädigten Batches den folgenden Befehl aus:
    
        Remove-MigrationBatch -Identity

2.  Führen Sie zum Neuerstellen des Batchauftrags den folgenden Befehl aus:
    
        New-MigrationBatch -Local -Name

Weitere Informationen finden Sie unter [Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

**MailboxMigration-Warnung: CriticalError**

Wenn ein kritischer Fehler währen der E-Mail-Migration auftritt, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*Benachrichtigung ausgelöst durch MailboxMigration am 07.09.2012 21:08:32. Details: Diagnoseinformationen: ProcessCacheEntry: Erste Organisation:: /o=ExchangeLabs/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=e80fc128879e452ebc882f6bca7007fa-Migration.8*

Führen Sie die Migration erneut aus, um dieses Problem zu beheben. Führen Sie hierzu den folgenden Befehl aus, oder klicken Sie in der Exchange-Verwaltungskonsole auf die Schaltfläche **Starten**.

    Call start-migrationbatch -Identity batchName

Wenn dieses Problem auftritt, wird eine Dr. Watson-Meldung zur Untersuchung an Microsoft gesendet.

**Der Microsoft Exchange-Replikationsdienst wird nicht ausgeführt**

Wenn diese Fehlerursache angezeigt wird, können Sie die Integrität des Diensts überprüfen, indem Sie den folgenden Befehl ausführen:

    Test-MRSHealth <servername> -MonitoringContext:$true

Sie können auch versuchen, den Dienst durch Ausführen des folgenden Befehls zu starten:

    Start-Service msexchangemailboxreplication

**Fehler bei MSExchangeMailboxReplication RCP-Ping**

Wenn diese Fehlerursache angezeigt wird, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*Ein Problem mit MRS wurde am 26.06.2012 06:08:47 erkannt. Details: Fehler bei der Überprüfung des MRS RPC-Ping für Server \<ServerName\> mit folgendem Fehler: Der RPC-Endpunkt für den Microsoft Exchange-Postfachreplikationsdienst konnte nicht antworten:*

Wenn dieses Problem auftritt, können Sie die Integrität des Diensts überprüfen, indem Sie den folgenden Befehl ausführen:

    Test-MRSHealth <servername> -MonitoringContext:$true

Sie können auch versuchen, den Dienst durch Ausführen des folgenden Befehls neu zu starten:

    Restart-Service msexchangemailboxreplication

**MSExchangeMailboxReplication-Dienst stürzt wiederholt ab**

Wenn der MSExchangeMailboxReplication-Dienst abstürzt oder nicht mehr reagiert, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*Der MRS-Prozess ist mindestens 3-mal in der letzten 01:00:00 abgestürzt. \<b\>Watson-Meldung:\</b\> Watson-Bericht wird gesendet für Prozess-ID: 41432, mit den Parametern: E12, \<ServerName\>, 15.00.0516.024, MSExchangeMailboxReplication, M.Exchange.MailboxReplicationService, M.E.M.BaseJob.BeginJob, System.ApplicationException, 7ec9, 15.00.0516.024. ErrorReportingEnabled: True.*

Wenn dieses Problem auftritt, können Sie die Integrität des Diensts überprüfen, indem Sie den folgenden Befehl ausführen:

    Test-MRSHealth <servername> -MonitoringContext:$true

Sie können auch versuchen, den Dienst durch Ausführen des folgenden Befehls neu zu starten:

    Restart-Service msexchangemailboxreplication

**MSExchangeMailboxReplication überprüft keine MDB-Warteschlangen**

Wenn der MSExchangeMailboxReplication-Dienst keine Warteschlangen mehr überprüft, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

*Ein Problem mit MRS wurde am 12.06.2012 18:20:44 erkannt. Details: Fehler bei der Überprüfung der MRS-Warteschlangenüberprüfung für Server \<ServerName\> mit folgendem Fehler: Der Microsoft Exchange-Postfachreplikationsdienst überprüft keine Postfachdatenbank-Warteschlangen auf Aufträge. Letzte Überprüfung: 04:38:02.1959439..*

Wenn dieses Problem auftritt, können Sie die Integrität des Diensts überprüfen, indem Sie den folgenden Befehl ausführen:

    Test-MRSHealth <servername> -MonitoringContext:$true

Sie können auch versuchen, den Dienst durch Ausführen des folgenden Befehls neu zu starten:

    Restart-Service msexchangemailboxreplication

**Zusätzliche Schritte zur Problembehandlung**

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu überprüfen, ob der Anwendungspool **MSExchangeServicesAppPool** ausgeführt wird.

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

