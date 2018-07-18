---
title: 'Überwachen von Datenbankverfügbarkeitsgruppen: Exchange 2013 Help'
TOCTitle: Überwachen von Datenbankverfügbarkeitsgruppen
ms:assetid: f5bdfd6e-e93c-4d96-8bc2-548750d51930
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351258(v=EXCHG.150)
ms:contentKeyID: 50477086
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Überwachen von Datenbankverfügbarkeitsgruppen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Sie können die Informationen in diesem Thema verwenden, um die Integrität und den Status von Postfachdatenbankkopien für Datenbankverfügbarkeitsgruppen (DAGs, Database Availability Groups) zu überwachen und Diagnoseinformationen zu sammeln sowie um einen Schwellenwert zur Überwachung geringen Speicherplatzes zu konfigurieren.

## Cmdlet "Get-MailboxDatabaseCopyStatus"

Mithilfe des Cmdlets [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\)) können Sie Statusinformationen zu Postfachdatenbankkopien anzeigen. Dieses Cmdlet ermöglicht Ihnen die Anzeige von Informationen über alle Kopien einer bestimmten Datenbank, über eine bestimmte Kopie einer Datenbank auf einem bestimmten Server oder über alle Datenbankkopien auf einem Server. In der folgenden Tabelle werden mögliche Werte für den Kopiestatus einer Postfachdatenbankkopie beschrieben.

### Status der Datenbankkopie

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Status der Datenbankkopie</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Failed</p></td>
<td><p>Die Postfachdatenbankkopie weist einen Fehlerzustand auf, da sie nicht angehalten wurde und keine Protokolldateien kopieren oder wiedergeben kann. Während sie sich im Fehlerzustand befindet und nicht angehalten wurde, überprüft das System in regelmäßigen Abständen, ob das Problem, das den fehlerhaften Kopierstatus verursacht hat, behoben wurde. Sobald das System ermittelt, dass das Problem gelöst wurde und keine weiteren Probleme vorliegen, wird der Kopierstatus automatisch in Healthy geändert.</p></td>
</tr>
<tr class="even">
<td><p>Seeding</p></td>
<td><p>Für die Postfachdatenbankkopie, den Inhaltsindex für die Postfachdatenbankkopie oder für beides wird ein Seeding durchgeführt. Bei erfolgreichem Abschluss des Seedingvorgangs sollte der Kopierstatus sich in Initializing ändern.</p></td>
</tr>
<tr class="odd">
<td><p>SeedingSource</p></td>
<td><p>Die Postfachdatenbankkopie wird als Quelle für einen Seedingvorgang für die Datenbankkopie verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Suspended</p></td>
<td><p>Die Postfachdatenbankkopie befindet sich in angehaltenem Zustand, weil ein Administrator die Datenbankkopie manuell durch Ausführen des Cmdlets <strong>Suspend-MailboxDatabaseCopy</strong> angehalten hat.</p></td>
</tr>
<tr class="odd">
<td><p>Healthy</p></td>
<td><p>Die Postfachdatenbankkopie kann Protokolldateien erfolgreich kopieren und wiedergeben oder hat alle verfügbaren Protokolldateien erfolgreich kopiert und wiedergegeben.</p></td>
</tr>
<tr class="even">
<td><p>ServiceDown</p></td>
<td><p>Der Microsoft Exchange-Replikationsdienst steht nicht zur Verfügung oder wird nicht auf dem Server ausgeführt, der die Postfachdatenbankkopie hostet.</p></td>
</tr>
<tr class="odd">
<td><p>Initializing</p></td>
<td><p>Die Postfachdatenbankkopie befindet sich im Initialisierungszustand, wenn eine Datenbankkopie erstellt wurde, wenn der Microsoft Exchange-Replikationsdienst gestartet wird oder gerade gestartet wurde sowie während der Übergänge aus den Zuständen Suspended, ServiceDown, Failed, Seeding oder SinglePageRestore in einen anderen Zustand. In diesem Zustand überprüft das System, ob die Datenbank und der Protokolldatenstrom sich in einem konsistenten Zustand befinden. In den meisten Fällen verbleibt der Kopierstatus für etwa 15 Sekunden im Initialisierungszustand. Im Allgemeinen sollte dieser Zustand nicht länger als 30 Sekunden andauern.</p></td>
</tr>
<tr class="even">
<td><p>Resynchronizing</p></td>
<td><p>Die Postfachdatenbankkopie und die zugehörigen Protokolldateien werden mit der aktiven Kopie der Datenbank verglichen, um Unterschiede zwischen beiden Kopien festzustellen. Der Kopierstatus verbleibt in diesem Zustand, bis Unterschiede ermittelt und gelöst wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Mounted</p></td>
<td><p>Die aktive Kopie ist online und nimmt Clientverbindungen an. Nur die aktive Kopie der Postfachdatenbank kann den Kopierstatus Mounted aufweisen.</p></td>
</tr>
<tr class="even">
<td><p>Dismounted</p></td>
<td><p>Die aktive Kopie ist offline und nimmt keine Clientverbindungen an. Nur die aktive Kopie der Postfachdatenbank kann den Kopierstatus Dismounted aufweisen.</p></td>
</tr>
<tr class="odd">
<td><p>Mounting</p></td>
<td><p>Die aktive Kopie wird online geschaltet und nimmt noch keine Clientverbindungen an. Nur die aktive Kopie der Postfachdatenbank kann den Kopierstatus Mounting aufweisen.</p></td>
</tr>
<tr class="even">
<td><p>Dismounting</p></td>
<td><p>Die aktive Kopie wird offline geschaltet, und Clientverbindungen werden beendet. Nur die aktive Kopie der Postfachdatenbank kann den Kopierstatus Dismounting aufweisen.</p></td>
</tr>
<tr class="odd">
<td><p>DisconnectedAndHealthy</p></td>
<td><p>Die Postfachdatenbankkopie ist nicht länger mit der aktiven Datenbankkopie verbunden. Sie war in fehlerfreiem Zustand, als die Verbindung verloren ging. Dieser Zustand stellt die Datenbankkopie im Hinblick auf ihre Verbindung mit der Quelldatenbankkopie dar. Er kann bei Netzwerkfehlern der DAG zwischen der Quellkopie und der Zieldatenbankkopie gemeldet werden.</p></td>
</tr>
<tr class="even">
<td><p>DisconnectedAndResynchronizing</p></td>
<td><p>Die Postfachdatenbankkopie ist nicht länger mit der aktiven Datenbankkopie verbunden. Sie befand sich im Zustand Resynchronizing, als die Verbindung verloren ging. Dieser Zustand stellt die Datenbankkopie im Hinblick auf ihre Verbindung mit der Quelldatenbankkopie dar. Er kann bei Netzwerkfehlern der DAG zwischen der Quellkopie und der Zieldatenbankkopie gemeldet werden.</p></td>
</tr>
<tr class="odd">
<td><p>FailedAndSuspended</p></td>
<td><p>Die Zustände Failed und Suspended wurden vom System gleichzeitig festgelegt, weil ein Fehler ermittelt wurde und die Lösung des Fehlers explizit einen Administratoreingriff erfordert. Ein Beispiel hierfür ist, wenn das System einen nicht behebbaren Unterschied zwischen der aktiven Postfachdatenbank und einer Datenbankkopie ermittelt. Im Gegensatz zum Zustand Failed prüft das System nicht regelmäßig, ob das Problem behoben wurde, und führt keine automatische Wiederherstellung durch. Stattdessen muss ein Administrator eingreifen, um die zugrunde liegende Ursache des Fehlers zu beheben, bevor die Datenbankkopie in einen fehlerfreien Zustand übergehen kann.</p></td>
</tr>
<tr class="even">
<td><p>SinglePageRestore</p></td>
<td><p>Dieser Zustand zeigt an, dass in der Postfachdatenbankkopie ein Wiederherstellungsvorgang für eine einzelne Seite stattfindet.</p></td>
</tr>
</tbody>
</table>


Das **Get-MailboxDatabaseCopyStatus**-Cmdlet leitet auch Einzelheiten zu den verwendeten Replikationsnetzwerken einschließlich *IncomingLogCopyingNetwork* weiter, die für passive Datenbankkopien umgeleitet werden, und *OutgoingConnections*, die für aktive Datenbanken umgeleitet werden, die über mehr als eine Kopie verfügen sowie für Datenbankkopien, die als Quelle für Datenbank-Seedvorgänge verwendet werden. Ausgehende Verbindungsinformationen werden für Datenbankkopien bereitgestellt, die sich in der Dateimodusreplikation befinden. Ausgehende Verbindungsinformationen werden nicht für Datenbankkopien bereitgestellt, die sich in der Blockmodusreplikation befinden.

## Beispiele für "Get-MailboxDatabaseCopyStatus"

In den folgenden Beispielen wird das Cmdlet **Get-MailboxDatabaseCopyStatus** verwendet. In jedem Beispiel wird das Ergebnis an das Cmdlet **Format-List** ausgegeben, um die Ausgabe im Listenformat anzuzeigen.

In diesem Beispiel werden Statusinformationen für alle Kopien der Datenbank "DB2" zurückgegeben.

    Get-MailboxDatabaseCopyStatus -Identity DB2 | Format-List

In diesem Beispiel wird der Status aller Datenbankkopien auf dem Postfachserver "MBX2" zurückgegeben.

    Get-MailboxDatabaseCopyStatus -Server MBX2 | Format-List

In diesem Beispiel wird der Status aller Datenbankkopien auf dem lokalen Postfachserver zurückgegeben.

    Get-MailboxDatabaseCopyStatus -Local | Format-List

Weitere Informationen zur Verwendung des Cmdlets **Get-MailboxDatabaseCopyStatus** finden Sie unter [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\)).

## Cmdlet "Test-ReplicationHealth"

Mithilfe des Cmdlets [Test-ReplicationHealth](https://technet.microsoft.com/de-de/library/bb691314\(v=exchg.150\)) können Sie fortlaufend Informationen über den Replikationsstatus von Postfachdatenbankkopien anzeigen. Dieses Cmdlet kann eingesetzt werden, um alle Aspekte von Replikation und Wiedergabestatus zu überprüfen und sich so einen vollständigen Überblick über einen bestimmten Postfachserver in einer DAG zu verschaffen.

Das Cmdlet **Test-ReplicationHealth** wurde für die proaktive Überwachung der fortlaufenden Replikation und der fortlaufenden Replikationspipeline, der Verfügbarkeit von Active Manager sowie des Status des zugrunde liegenden Clusterdiensts, Quorums und der zugrunde liegenden Netzwerkkomponenten entwickelt. Es kann lokal oder remote für jeden Postfachserver in einer DAG ausgeführt werden. Das Cmdlet **Test-ReplicationHealth** führt die in der folgenden Tabelle aufgeführten Tests durch.

### Tests des Cmdlets "Test-ReplicationHealth"

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Testname</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ClusterService</p></td>
<td><p>Überprüft, ob der Clusterdienst ausgeführt wird und auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="even">
<td><p>ReplayService</p></td>
<td><p>Überprüft, ob der Microsoft Exchange-Replikationsdienst ausgeführt wird und auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="odd">
<td><p>ActiveManager</p></td>
<td><p>Überprüft, ob die auf dem angegebenen Mitglied der DAG (bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server) ausgeführte Instanz von Active Manager in einer gültigen Rolle vorliegt (primär, sekundär oder eigenständig).</p></td>
</tr>
<tr class="even">
<td><p>TasksRpcListener</p></td>
<td><p>Überprüft, ob der Tasks-RPC-Server (Remote Procedure Call) ausgeführt wird und auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="odd">
<td><p>TcpListener</p></td>
<td><p>Überprüft, ob der TCP-Protokollkopielistener ausgeführt wird und auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="even">
<td><p>ServerLocatorService</p></td>
<td><p>Stellt sicher, dass der Active Manager Client/Server auf DAG-Mitgliedern und auf dem Clientzugriffsserver ausgeführt wird, der Lookups in Active Directory und im Aktive Manager ausführt, um festzulegen, wo die Postfachdatenbank eines Benutzers aktiv ist.</p></td>
</tr>
<tr class="odd">
<td><p>DagMembersUp</p></td>
<td><p>Überprüft, ob alle Mitglieder der DAG verfügbar sind, ausgeführt werden und erreichbar sind.</p></td>
</tr>
<tr class="even">
<td><p>ClusterNetwork</p></td>
<td><p>Überprüft, ob alle clusterverwalteten Netzwerke auf dem angegebenen Mitglied der DAG (bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server) verfügbar sind.</p></td>
</tr>
<tr class="odd">
<td><p>QuorumGroup</p></td>
<td><p>Überprüft, ob die Standardclustergruppe (Quorumgruppe) sich in einem fehlerfreien Onlinezustand befindet.</p></td>
</tr>
<tr class="even">
<td><p>FileShareQuorum</p></td>
<td><p>Überprüft, ob der für die DAG konfigurierte Zeugenserver sowie das Zeugenverzeichnis und die Zeugenfreigabe erreichbar sind.</p></td>
</tr>
<tr class="odd">
<td><p>DatabaseRedundancy</p></td>
<td><p>Stellt sicher, dass mindestens eine fehlerfreie Kopie der Datenbanken auf dem angegebenen DAG-Mitglieds bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="even">
<td><p>DatabaseAvailability</p></td>
<td><p>Überprüft, ob Datenbanken eine ausreichende Verfügbarkeit auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server erreichbar ist.</p></td>
</tr>
<tr class="odd">
<td><p>DBCopySuspended</p></td>
<td><p>Prüft, ob sich Postfachdatenbankkopien auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server im Zustand Suspended befinden.</p></td>
</tr>
<tr class="even">
<td><p>DBCopyFailed</p></td>
<td><p>Prüft, ob sich Postfachdatenbankkopien auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server im Zustand Fehler befinden.</p></td>
</tr>
<tr class="odd">
<td><p>DBInitializing</p></td>
<td><p>Prüft, ob sich Postfachdatenbankkopien auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server im Zustand Initializing befinden.</p></td>
</tr>
<tr class="even">
<td><p>DBDisconnected</p></td>
<td><p>Prüft, ob sich Postfachdatenbankkopien auf dem angegebenen Mitglied der DAG bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server im Zustand Disconnected befinden.</p></td>
</tr>
<tr class="odd">
<td><p>DBLogCopyKeepingUp</p></td>
<td><p>Überprüft, ob Protokollkopiervorgang und Inspektion durch die passiven Kopien von Datenbanken auf dem angegebenen Mitglied der DAG (bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server) mit der Aktivität zur Protokollgenerierung auf der aktiven Kopie Schritt halten können.</p></td>
</tr>
<tr class="even">
<td><p>DBLogReplayKeepingUp</p></td>
<td><p>Überprüft, ob die Wiedergabeaktivität für die passiven Kopien von Datenbanken auf dem angegebenen Mitglied der DAG (bzw., wenn kein Mitglied der DAG angegeben ist, auf dem lokalen Server) mit der Aktivität zur Protokollkopie und -inspektion Schritt halten kann.</p></td>
</tr>
</tbody>
</table>


## Beispiel für "Test-ReplicationHealth"

In diesem Beispiel wird das Cmdlet **Test-ReplicationHealth** zum Testen des Replikationsstatus für den Postfachserver "MBX1" verwendet.

    Test-ReplicationHealth -Identity MBX1

## Crimson-Kanal-Ereignisprotokollierung

Windows verfügt über zwei Kategorien von Ereignisprotokollen: Windows-Protokolle sowie Anwendungs- und Dienstprotokolle. Die Kategorie der Windows-Protokolle umfasst die Ereignisprotokolle, die in früheren Versionen von Windows verfügbar waren: Anwendungs-, Sicherheits- und Systemereignisprotokolle. Darüber hinaus gibt es zwei neue Protokolle: Das Setupprotokoll und das ForwardedEvents-Protokoll. In Windows-Protokollen werden Ereignisse aus älteren Anwendungen sowie Ereignisse gespeichert, die für das gesamte System gelten.

Bei Anwendungs- und Dienstprotokollen handelt es sich um eine neue Kategorie von Ereignisprotokollen. Anstelle von Ereignissen, die systemweite Auswirkungen haben können, werden in diesen Protokollen Ereignisse aus einer einzigen Anwendung oder Komponente gespeichert. Diese neue Kategorie von Ereignisprotokollen wird als Crimson-Kanal einer Anwendung bezeichnet.

Die Kategorie der Anwendungs- und Dienstprotokolle enthält vier Unterkategorien: Administrator-, Betriebs-, analytische und Debugprotokolle. Ereignisse in Administratorprotokollen sind vor allem relevant, wenn Sie die Einträge des Ereignisprotokolls zur Problembehandlung verwenden. Ereignisse im Administratorprotokoll enthalten Anweisungen, wie Sie auf die Ereignisse reagieren sollen. Ereignisse im Betriebsprotokoll sind ebenso hilfreich, erfordern jedoch mehr Interpretation. Administrator- und Debugprotokolle sind weniger benutzerfreundlich. In analytischen Protokollen, die standardmäßig ausgeblendet und deaktiviert sind, werden Ereignisse zur Nachverfolgung eines Problems gespeichert. Häufig wird eine hohe Anzahl von Ereignissen protokolliert. Debugprotokolle werden von Entwicklern beim Debuggen von Anwendungen verwendet.

Exchange 2013 protokolliert Ereignisse in Crimson-Kanälen im Anwendungs- und Dienstprotokollbereich. Sie können diese Kanäle folgendermaßen anzeigen:

1.  Öffnen Sie die Ereignisanzeige.

2.  Navigieren Sie in der Konsolenstruktur zu **Anwendungs- und Dienstprotokolle** \> **Microsoft** \> **Exchange**.

3.  Wählen Sie unter **Exchange** einen Crimson-Kanal wie **HighAvailability** oder **MailboxDatabaseFailureItems** aus, um DAG- und Datenbankkopien-Ereignisse anzuzeigen, oder **ActiveMonitoring** oder **ManagedAvailability**, um Ereignisse im Zusammenhang mit der verwalteten Verfügbarkeit anzuzeigen.

Der Kanal HighAvailability enthält Ereignisse im Zusammenhang mit dem Starten und Herunterfahren des Microsoft Exchange-Replikationsdiensts sowie mit den verschiedenen Komponenten, die innerhalb des Microsoft Exchange-Replikationsdiensts ausgeführt werden: Active Manager, die Drittanbieter-API zur synchronen Replikation, der Tasks-RPC-Server, TCP-Listener und VSS-Writer (Volume Shadow Copy Service, Volumeschattenkopie-Dienst). Der Kanal HighAvailability wird auch von Active Manager zum Protokollieren von Ereignissen im Zusammenhang mit der Active Manager-Rollenüberwachung sowie von Datenbankaktionsereignissen wie dem Vorgang zur Datenbankeinbindung und zum Abschneiden von Protokollen verwendet. Außerdem dient er zum Aufzeichnen von Ereignissen im Hinblick auf den zugrunde liegenden Cluster der DAG.

Der Kanal MailboxDatabaseFailureItems wird zum Protokollieren von Ereignissen im Zusammenhang mit Fehlern verwendet, die sich auf eine replizierte Postfachdatenbank auswirken.

Der Kanal ActiveMonitoring enthält Definitions- und Ergebnisereignisse für Tests, Monitore und Antwortsender in Zusammenhang mit verwalteter Verfügbarkeit.

Der Kanal ManagedAvailability enthält Wiederherstellungsaktionsprotokolle und -ergebnisse sowie damit zusammenhängende Ereignisse.

## Monitor für geringen Speicherplatz

Exchange 2013 Mit der verwalteten Verfügbarkeit werden in jeder Minute Hunderte von Systemmetriken und Komponenten überwacht, darunter die Menge des freien Speicherplatzes auf von der Serverrolle "Mailbox" verwendeten Volumes. In Versionen vor Exchange 2013 Service Pack 1 (SP1) überwacht Exchange den verfügbaren Speicherplatz auf allen lokalen Volumes, darunter auch auf solchen, die keine Datenbanken oder Protokolldateien enthalten. In der Version SP1 und höher werden nur Volumes überwacht, die Exchange-Datenbanken und Protokolldateien enthalten. In SP1 beträgt der Standardschwellenwert für den Monitor für geringen Speicherplatz 200 GB. In Exchange 2013 Kumulatives Update 6 und höher liegt der Standardschwellenwert bei 180 GB. In SP1 und höher können Sie den Schwellenwert konfigurieren, indem Sie den folgenden DWORD-Registrierungswert (in MB) auf jedem Postfachserver hinzufügen, den Sie anpassen möchten:

Pfad: **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\ExchangeServer\\v15\\Replay\\Parameters**

Wert: *SpaceMonitorLowSpaceThresholdInMB*

Wenn Sie z. B. den Schwellenwert auf 180 GB einstellen möchten, würden Sie den folgenden Registrierungswert konfigurieren:

**REG\_DWORD 186a0 (100000)**

Nach der Konfiguration oder Änderung des oben genannten Registrierungswerts müssen Sie den Microsoft Exchange-DAG-Verwaltungsdienst neu starten, damit die Änderung wirksam werden kann.

## Skript "CollectOverMetrics.ps1"

Exchange 2013 umfasst ein Skript namens CollectOverMetrics.ps1, das im Ordner Scripts gespeichert ist. CollectOverMetrics.ps1 liest Ereignisprotokolle von DAG-Mitgliedern, um Informationen zu Datenbankvorgängen (z. B. Datenbankeinbindungen, -verschiebungen und -failover) über einen bestimmten Zeitraum zu erfassen. Für jeden Vorgang zeichnet das Skript folgende Informationen auf:

  - Identität der Datenbank

  - Anfangs- und Endzeitpunkt des Vorgangs

  - Server, auf denen die Datenbank am Anfang und am Ende des Vorgangs eingebunden war

  - Grund des Vorgangs

  - Den Erfolg bzw. Misserfolg des Vorgangs (in diesem Fall mit den Fehlerdetails)

Das Skript schreibt diese Informationen in CSV-Dateien (pro Zeile ein Vorgang). Für jede DAG wird eine gesonderte CSV-Datei geschrieben.

Das Skript unterstützt Parameter, mit denen Sie das Verhalten und die Ausgabe des Skripts anpassen können. Mithilfe des Parameters *Database* oder *ReportFilter* kann z. B. das Ergebnis auf eine angegebene Untermenge beschränkt werden. Nur die Vorgänge, die diesen Filtern entsprechen, werden in den HTML-Zusammenfassungsbericht einbezogen. Die verfügbaren Parameter sind in der folgenden Tabelle aufgeführt.

### Parameter des Skripts "CollectOverMetrics.ps1"

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>DatabaseAvailabilityGroup</em></p></td>
<td><p>Gibt den Namen der DAG an, deren Metriken Sie erfassen möchten. Wird dieser Parameter ausgelassen, wird die DAG verwendet, welcher der lokale Server angehört. Platzhalterzeichen dienen beim Erstellen von Berichten zum Erfassen von Informationen aus mehreren DAGs.</p></td>
</tr>
<tr class="even">
<td><p><em>Database</em></p></td>
<td><p>Stellt eine Liste von Datenbanken bereit, für die der Bericht generiert werden soll. Platzhalterzeichen werden unterstützt, z. B. <code>-Database:&quot;DB1&quot;,&quot;DB2&quot;</code> oder <code>-Database:&quot;DB*&quot;</code>.</p></td>
</tr>
<tr class="odd">
<td><p><em>StartTime</em></p></td>
<td><p>Gibt die Dauer des Zeitraums an, für den der Bericht erstellt werden soll. Das Skript erfasst nur die in diesem Zeitraum protokollierten Ereignisse. Demzufolge erfasst das Skript ggf. nur Teildatensätze zu Vorgängen (z. B. nur das Ende eines Vorgangs zum Anfangszeitpunkt des Zeitraums oder umgekehrt). Wenn weder <em>StartTime</em> noch <em>EndTime</em> angegeben wird, ist der Standardzeitraum des Skripts die letzten 24 Stunden. Wenn nur ein Parameter angegeben wird, ist der Zeitraum 24 Stunden, der zum angegebenen Zeitpunkt entweder beginnt oder endet.</p></td>
</tr>
<tr class="even">
<td><p><em>EndTime</em></p></td>
<td><p>Gibt die Dauer des Zeitraums an, für den der Bericht erstellt werden soll. Das Skript erfasst nur die in diesem Zeitraum protokollierten Ereignisse. Demzufolge erfasst das Skript ggf. nur Teildatensätze zu Vorgängen (z. B. nur das Ende eines Vorgangs zum Anfangszeitpunkt des Zeitraums oder umgekehrt). Wenn weder <em>StartTime</em> noch <em>EndTime</em> angegeben wird, erfasst das Skript standardmäßig die letzten 24 Stunden. Wenn nur ein Parameter angegeben wird, ist der Zeitraum 24 Stunden, der zum angegebenen Zeitpunkt entweder beginnt oder endet.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReportPath</em></p></td>
<td><p>Gibt den Ordner an, in dem die Ergebnisse der Ereignisverarbeitung gespeichert werden sollen. Wird dieser Parameter ausgelassen, wird der Ordner Scripts verwendet. Falls angegeben, verwendet das Skript eine Liste mit vom Skript generierten CSV-Dateien als Quelldaten zum Erstellen eines HTML-Zusammenfassungsberichts. Der Bericht entspricht demjenigen, der mit der Option -GenerateHtmlReport erstellt wird. Die Dateien können mehrere DAGs übergreifend zu vielen verschiedenen Zeitpunkten und sogar mit überlappenden Zeiträumen erstellen werden. Das Skript sorgt dafür, dass alle Daten zusammengeführt werden.</p></td>
</tr>
<tr class="even">
<td><p><em>GenerateHtmlReport</em></p></td>
<td><p>Gibt an, dass das Skript alle aufgezeichneten Daten erfasst, die Daten nach Vorgangstyp gruppiert und anschließend eine HTML-Datei mit Statistiken zu jeder dieser Gruppen generiert. Der Bericht enthält die Gesamtanzahl von Vorgängen in jeder Gruppe, die Anzahl der nicht erfolgreichen Vorgänge und Statistiken zum Erfassungszeitraum innerhalb jeder Gruppe. Der Bericht enthält außerdem eine Aufgliederung der Typen von Fehlern, die zu misslungenen Vorgängen geführt haben.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShowHtmlReport</em></p></td>
<td><p>Gibt an, dass der in HTML generierte Bericht anschließend in einem Webbrowser angezeigt werden soll.</p></td>
</tr>
<tr class="even">
<td><p><em>SummariseCsvFiles</em></p></td>
<td><p>Gibt an, dass das Skript die Daten aus vorhandenen CSV-Dateien liest, die zuvor mithilfe des Skripts generiert wurden. Diese Daten dienen anschließend zum Generieren eines Zusammenfassungsberichts ähnlich demjenigen, der mit dem Parameter <em>GenerateHtmlReport</em> erstellt wird.</p></td>
</tr>
<tr class="odd">
<td><p><em>ActionType</em></p></td>
<td><p>Gibt die Arten der Vorgangsaktionen an, die das Skript erfassen soll. Die Werte für diesen Parameter sind <code>Move</code>, <code>Mount</code>, <code>Dismount</code> und <code>Remount</code>. Der Wert <code>Move</code> bezieht sich auf denjenigen Zeitpunkt, an dem die Datenbank ihren aktiven Server ändert (entweder aufgrund von Verschiebungen oder Failover). Die Werte <code>Mount</code>, <code>Dismount</code> und <code>Remount</code> beziehen sich auf Zeitpunkte, an denen die Datenbank ihren eingebundenen Status ändert, ohne auf einen anderen Computer verschoben zu werden.</p></td>
</tr>
<tr class="even">
<td><p><em>ActionTrigger</em></p></td>
<td><p>Gibt die Verwaltungsvorgänge an, die vom Skript erfasst werden sollen. Die Werte für diesen Parameter sind <code>Admin</code> und <code>Automatic</code>. Automatische Aktionen werden vom System automatisch ausgeführt (z. B. ein Failover, wenn ein Server offline geschaltet wird). Verwaltungsaktionen (Admin) werden von einem Administrator entweder über die Exchange-Verwaltungsshell oder die Exchange-Verwaltungskonsole ausgeführt.</p></td>
</tr>
<tr class="odd">
<td><p><em>RawOutput</em></p></td>
<td><p>Gibt an, dass das Skript die Ergebnisse, die normalerweise in CSV-Dateien geschrieben würden, direkt in den Ausgabedatenstrom schreibt (wie beim Vorgang Write-Output). Diese Informationen können an andere Befehle weitergeleitet werden.</p></td>
</tr>
<tr class="even">
<td><p><em>IncludedExtendedEvents</em></p></td>
<td><p>Gibt an, dass das Skript die Ereignisse erfassen soll, die Diagnosedetails zu den Zeiträumen liefern, die für das Einbinden von Datenbanken aufgewendet wurden. Dies kann eine sehr zeitaufwendige Phase sein, wenn das Ereignisprotokoll Anwendung auf den Servern sehr groß ist.</p></td>
</tr>
<tr class="odd">
<td><p><em>MergeCSVFiles</em></p></td>
<td><p>Gibt an, dass das Skript alle CSV-Dateien mit Daten zu jedem Vorgang verwendet und diese in einer einzelnen CSV-Datei zusammenführt.</p></td>
</tr>
<tr class="even">
<td><p><em>ReportFilter</em></p></td>
<td><p>Gibt an, dass mithilfe der Felder in den CSV-Dateien ein Filter auf die Vorgänge angewendet werden soll. Dieser Parameter verwendet dasselbe Format wie ein <code>Where</code>-Vorgang, bei dem jedes Element auf <code>$_</code> festgelegt ist und ein boolescher Wert zurückgegeben wird. Beispiel: <code>{$_DatabaseName -notlike &quot;Mailbox Database*&quot;}</code> dient zum Ausschließen der Standarddatenbanken aus dem Bericht.</p></td>
</tr>
</tbody>
</table>


## Beispiele für "CollectOverMetrics.ps1"

Im folgenden Beispiel werden Metriken für alle Datenbanken erfasst, die "DB\*" (mit Platzhalterzeichen) in der Datenbankverfügbarkeitsgruppe "DAG1" entsprechen. Nachdem die Metriken erfasst wurden, wird ein HTML-Bericht generiert und angezeigt.

    CollectOverMetrics.ps1 -DatabaseAvailabilityGroup DAG1 -Database:"DB*" -GenerateHTMLReport -ShowHTMLReport

Die folgenden Beispiele veranschaulichen Möglichkeiten zum Filtern des HTML-Zusammenfassungsberichts. Im ersten wird der Parameter *Database* genutzt, der eine Liste mit Datenbanken verwendet. Der Zusammenfassungsbericht enthält anschließend nur Daten zu diesen Datenbanken. In den folgenden beiden Beispielen wird der Parameter *ReportFilter* verwendet. Im letzten Beispiel werden alle Standarddatenbanken herausgefiltert.

    CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -Database MailboxDatabase123,MailboxDatabase456
    CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -ReportFilter { $_.DatabaseName -notlike "Mailbox Database*" }
    CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -ReportFilter { ($_.ActiveOnStart -like "ServerXYZ*") -and ($_.ActiveOnEnd -notlike "ServerXYZ*") }

## Skript "CollectReplicationMetrics.ps1"

Ein anderes in Exchange 2013 enthaltenes Skript für Statusmetriken ist CollectReplicationMetrics.ps1. Bei diesem Skript handelt es sich um eine aktive Form der Überwachung, da es Metriken in Echtzeit erfasst, während das Skript ausgeführt wird. CollectReplicationMetrics.ps1 erfasst Daten von Leistungsindikatoren im Zusammenhang mit der Datenbankreplikation. Das Skript erfasst Leistungsindikatordaten mehrerer Postfachserver, schreibt die Daten der einzelnen Server in eine CSV-Datei und kann anschließend verschiedene Statistiken anhand dieser Daten erstellen (z. B. den Zeitraum, den jede Kopie im Status "Fehler" oder "Angehalten" verbracht hat, die Durchschnittslänge der Kopie- oder Wiedergabewarteschlange oder die Dauer, in der Kopien sich außerhalb ihrer Failoverkriterien befunden haben).

Sie können entweder die Server einzeln oder ganze DAGs angeben. Sie können das Skript entweder ausführen, um die Daten zu erfassen und anschließend den Bericht zu erstellen, oder Sie können es ausführen, um nur Daten zu erfassen oder um nur einen Bericht zu Daten zu erstellen, die bereits erfasst wurden. Sie können die Häufigkeit angeben, mit der Daten erfasst werden sollen, und die Gesamtdauer der Datenerfassung bestimmen.

Die von jedem Server erfassten Daten werden in eine Datei mit dem Namen **CounterData.\<Servername\>.\<Zeitstempel\>.csv** geschrieben. Der Zusammenfassungsbericht wird in eine Datei mit dem Namen **HaReplPerfReport.\<Name der DAG\>.\<Zeitstempel\>.csv** oder **HaReplPerfReport.\<Zeitstempel\>.csv** geschrieben, wenn das Skript nicht mit dem Parameter *DagName* ausgeführt wurde.

Das Skript startet Windows PowerShell-Aufträge zum Erfassen der Daten von jedem Server. Diese Aufträge werden für den gesamten Zeitraum ausgeführt, in dem Daten erfasst werden sollen. Wenn Sie eine große Anzahl von Servern angeben, kann dieser Prozess sehr viel Arbeitsspeicher belegen. Die letzte Phase des Prozesses, in denen die Daten zu einem Zusammenfassungsbericht verarbeitet werden, kann bei großen Datenmengen auch relativ zeitaufwendig sein. Es ist möglich, die Erfassungsphase auf einem Computer auszuführen und die Daten anschließend zur Verarbeitung auf einen anderen Computer zu kopieren.

Das Skript CollectReplicationMetrics.ps1 unterstützt Parameter, mit denen Sie das Verhalten und die Ausgabe des Skripts anpassen können. Die verfügbaren Parameter sind in der folgenden Tabelle aufgeführt.

### Parameter des Skripts "CollectReplicationMetrics.ps1"

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>DagName</em></p></td>
<td><p>Gibt den Namen der DAG an, deren Metriken Sie erfassen möchten. Wird dieser Parameter ausgelassen, wird die DAG verwendet, welcher der lokale Server angehört.</p></td>
</tr>
<tr class="even">
<td><p><em>DatabaseNames</em></p></td>
<td><p>Stellt eine Liste von Datenbanken bereit, für die der Bericht generiert werden soll. Platzhalterzeichen werden unterstützt, z. B. <code>-DatabaseNames:&quot;DB1&quot;,&quot;DB2&quot;</code> oder <code>-DatabaseNames:&quot;DB*&quot;</code>.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReportPath</em></p></td>
<td><p>Gibt den Ordner an, in dem die Ergebnisse der Ereignisverarbeitung gespeichert werden sollen. Wird dieser Parameter ausgelassen, wird der Ordner Scripts verwendet.</p></td>
</tr>
<tr class="even">
<td><p><em>Duration</em></p></td>
<td><p>Gibt die Zeitspanne an, für die der Erfassungsvorgang ausgeführt werden soll. Typische Werte sind ein bis drei Stunden. Längere Zeiträume sollten nur bei längeren Intervallen zwischen jeder Erfassung verwendet werden. Möglich ist auch eine Folge kürzerer Aufträge, die als geplante Aufgaben ausgeführt werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>Frequency</em></p></td>
<td><p>Gibt die Häufigkeit an, mit der Datenmetriken erfasst werden. Typische Werte sind 30 Sekunden, eine Minute oder fünf Minuten. Unter normalen Umständen werden bei kürzeren Intervallen als diesen keine wesentlichen Unterschiede zwischen den einzelnen Erfassungen deutlich.</p></td>
</tr>
<tr class="even">
<td><p><em>Servers</em></p></td>
<td><p>Gibt die Identität der Server an, von denen Statistiken erfasst werden sollen. Sie können einen beliebigen Wert angeben, einschließlich Platzhalterzeichen und GUIDs.</p></td>
</tr>
<tr class="odd">
<td><p><em>SummariseFiles</em></p></td>
<td><p>Gibt eine Liste mit CSV-Dateien zum Generieren eines Zusammenfassungsberichts an. Diese Dateien heißen <strong>CounterData.&lt;Leistungsindikatordaten&gt;*</strong> und werden vom Skript CollectReplicationMetrics.ps1 erstellt.</p></td>
</tr>
<tr class="even">
<td><p><em>Mode</em></p></td>
<td><p>Gibt die Verarbeitungsphasen an, die das Skript ausführt. Folgende Werte können verwendet werden:</p>
<ul>
<li><p><code>CollectAndReport</code>   Dies ist der Standardwert. Dieser Wert bedeutet, dass das Skript Daten von den Servern erfassen und anschließend so verarbeiten soll, dass ein Zusammenfassungsbericht generiert wird.</p></li>
<li><p><code>CollectOnly</code>   Dieser Wert bedeutet, dass das Skript nur die Daten erfassen und keinen Bericht erstellen soll.</p></li>
<li><p><code>ProcessOnly</code>   Dieser Wert bedeutet, dass das Skript Daten aus verschiedenen CSV-Dateien importieren und anschließend so verarbeiten soll, dass ein Zusammenfassungsbericht generiert wird. Der Parameter <em>SummariseFiles</em> dient dazu, dem Skript die Liste mit den zu verarbeitenden Dateien bereitzustellen.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><em>MoveFilestoArchive</em></p></td>
<td><p>Gibt an, dass das Skript die Dateien nach der Verarbeitung in einen komprimierten Ordner verschieben soll.</p></td>
</tr>
<tr class="even">
<td><p><em>LoadExchangeSnapin</em></p></td>
<td><p>Gibt an, dass das Skript die Shellbefehle laden soll. Dieser Parameter ist nützlich, wenn das Skript außerhalb der Shell ausgeführt werden muss, z. B. in einer geplanten Aufgabe.</p></td>
</tr>
</tbody>
</table>


## Beispiel für "CollectReplicationMetrics.ps1"

Im folgenden Beispiel werden Daten über eine Stunde von allen Servern in der DAG namens "DAG1" in einminütigen Abständen in einem Zusammenfassungsbericht erfasst. Darüber hinaus wird der Parameter *ReportPath* angegeben, der bewirkt, dass das Skript alle Dateien im aktuellen Verzeichnis ablegt.

    CollectReplicationMetrics.ps1 -DagName DAG1 -Duration "01:00:00" -Frequency "00:01:00" -ReportPath

Im folgenden Beispiel werden Daten aus allen mit "CounterData\*" übereinstimmenden Dateien gelesen und in einem Zusammenfassungsbericht ausgegeben.

    CollectReplicationMetrics.ps1 -SummariseFiles (dir CounterData*) -Mode ProcessOnly -ReportPath

