---
title: 'Ändern des Speicherorts der Warteschlangendatenbank: Exchange 2013 Help'
TOCTitle: Ändern des Speicherorts der Warteschlangendatenbank
ms:assetid: f170cb0c-04a9-4fa7-b594-206e3a787e14
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125177(v=EXCHG.150)
ms:contentKeyID: 51409361
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern des Speicherorts der Warteschlangendatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Eine *Warteschlange* ist ein temporärer Speicherort für Nachrichten, die auf den Eintritt in die nächste Verarbeitungsphase warten. Jede Warteschlange stellt einen logischen Satz von Nachrichten dar, die ein Transportserver in einer bestimmten Reihenfolge verarbeitet.

Wie in den Vorgängerversionen von Exchange wird in Microsoft Exchange Server 2013 eine ESE-Datenbank (Extensible Storage Engine) für Warteschlangenspeicher verwendet. Die unterschiedlichen Warteschlangen werden in einer einzigen ESE-Datenbank gespeichert. Warteschlangen sind nur auf Postfachservern oder Edge-Transport-Servern vorhanden.

Der Speicherort der Warteschlangendatenbank und der zugehörigen Transaktionsprotokolle wird von Schlüsseln in der XML-Anwendungskonfigurationsdatei `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` gesteuert. Diese Datei ist mit dem Microsoft Exchange-Transportdienst verknüpft. In der folgenden Tabelle werden die einzelnen Schlüssel ausführlicher beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Taste</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>QueueDatabasePath</em></p></td>
<td><p>Dieser Schlüssel gibt den Speicherort für die Dateien der Warteschlangendatenbank an. Dabei handelt es sich um folgende Dateien:</p>
<ul>
<li><p>Mail.que</p></li>
<li><p>Trn.chk</p></li>
</ul>
<p>Der Standardspeicherort ist <code>%ExchangeInstallPath%TransportRoles\data\Queue</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseLoggingPath</em></p></td>
<td><p>Dieser Schlüssel gibt den Speicherort für die Transaktionsprotokolldateien der Warteschlangendatenbank an. Dabei handelt es sich um folgende Dateien:</p>
<ul>
<li><p>Trn.log</p></li>
<li><p>Trntmp.log</p></li>
<li><p>Trn<em>nnn</em>.log</p></li>
<li><p>Trnres00001.jrs</p></li>
<li><p>Trnres00002.jrs</p></li>
<li><p>Temp.edb</p></li>
</ul>
<p>Beachten Sie, dass &quot;Temp.edb&quot; zum Überprüfen des Warteschlangendatenbank-Schemas verwendet wird, wenn der Microsoft Exchange-Transportdienst gestartet wird. Obwohl Temp.edb keine Transaktionsprotokolldatei ist, befindet sie sich dennoch am selben Speicherort wie die Transaktionsprotokolldateien.</p>
<p>Der Standardspeicherort ist <code>%ExchangeInstallPath%TransportRoles\data\Queue</code>.</p></td>
</tr>
</tbody>
</table>


## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - Wenn Sie den Microsoft Exchange-Transportdienst beenden oder neu starten, wird der Nachrichtenfluss auf dem Server unterbrochen.

  - Wenn Sie den Speicherort für die Warteschlangendatenbank oder die Transaktionsprotokolle ändern, werden die vorhandenen Warteschlangendatenbank- und Transaktionsprotokolldateien nicht verschoben. An dem neuen Speicherort werden eine neue Datenbank und neue Transaktionsprotokolle erstellt. Die vorhandenen Dateien verbleiben am bisherigen Speicherort. Sie werden allerdings nicht mehr verwendet. Wenn Sie die vorhandenen Warteschlangendatenbank- oder Transaktionsprotokolldateien am neuen Speicherort weiterverwenden möchten, müssen Sie sie zwischen Beendigung und Neustart des Microsoft Exchange-Transportdiensts an den neuen Speicherort verschieben.

  - Ist der Zielordner für die Warteschlangendatenbank oder die Transaktionsprotokolle nicht vorhanden, wird er automatisch erstellt, wenn für den übergeordneten Ordner folgende Berechtigungen gelten:
    
      - Netzwerkdienst: Vollzugriff
    
      - System: Vollzugriff
    
      - Administratoren: Vollzugriff

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Erstellen einer neuen Warteschlangendatenbank und neuer Transaktionsprotokolle an einem neuen Speicherort mithilfe der Eingabeaufforderung

1.  Erstellen Sie die Ordner, in denen die Warteschlangendatenbank und die Transaktionsprotokolle gespeichert werden sollen. Achten Sie darauf, den Ordnern die richtigen Berechtigungen zuzuweisen.

2.  Geben Sie in einem Eingabeaufforderungsfenster den folgenden Befehl ein, um die Datei "EdgeTransport.exe.config" in Notepad zu öffnen:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

3.  Ändern Sie im Abschnitt `<appSettings>` die folgenden Schlüssel.
    
        <add key="QueueDatabasePath" value="<LocalPath>" />
        <add key="QueueDatabaseLoggingPath" value="<LocalPath>" />
    
    Wenn Sie beispielsweise eine neue Warteschlangendatenbank in "D:\\Queue\\QueueDB" und neue Transaktionsprotokolle in "D:\\Queue\\QueueLogs" erstellen möchten, verwenden Sie folgende Werte:
    
        <add key="QueueDatabasePath" value="D:\Queue\QueueDB" />
        <add key="QueueDatabaseLoggingPath" value="D:\Queue\QueueLogs" />

4.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

5.  Starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:
    
        net stop MSExchangeTransport && net start MSExchangeTransport

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob das Erstellen einer neuen Warteschlangendatenbank und neuer Transaktionsprotokolle an einem neuen Speicherort erfolgreich verlaufen ist:

1.  Vergewissern Sie sich, dass die neuen Dateien "Mail.que" und "Trn.chk" am neuen Speicherort vorhanden sind.

2.  Vergewissern Sie sich, dass die neuen Transaktionsprotokolldateien "Trn.log", "Trntmp.log", "Trnres00001.jrs", "Trnres00002.jrs" und "Temp.edb" am neuen Speicherort vorhanden sind.

3.  Wenn Sie die alten Warteschlangendatenbank- und Transaktionsprotokolldateien aus dem alten Speicherort löschen können, nachdem der Microsoft Exchange-Transportdienst gestartet wurde, werden diese Dateien nicht mehr verwendet.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Was möchten Sie machen?

## Verschieben einer vorhandenen Warteschlangendatenbank und der zugehörigen Transaktionsprotokolle an einen neuen Speicherort mithilfe der Eingabeaufforderung

Nur bei Wiederherstellungsszenarien, in denen der Microsoft Exchange-Transportdienst nicht ordnungsgemäß heruntergefahren wurde oder in denen ein Festplattenfehler aufgetreten ist, ist es erforderlich, eine vorhandene Warteschlangendatenbank mit den zugehörigen Transaktionsprotokollen wiederherzustellen und zu verschieben.

Unter normalen Umständen ist es nicht erforderlich, vorhandene Transaktionsprotokolle weiterzuverwenden. Durch normales Herunterfahren des Microsoft Exchange-Transportdiensts werden alle noch nicht übergebenen Transaktionsprotokolleinträge in die Warteschlangendatenbank geschrieben. Außerdem wird Umlaufprotokollierung verwendet, damit keine Transaktionsprotokolle aufbewahrt werden, die zuvor vorgenommene Datenbankänderungen enthalten.

Gehen Sie wie folgt vor, um eine vorhandene Warteschlangendatenbank und die zugehörigen Transaktionsprotokolle mithilfe der Eingabeaufforderung an einen neuen Speicherort zu verschieben:

1.  Erstellen Sie die Ordner, in denen die Warteschlangendatenbank und die Transaktionsprotokolle gespeichert werden sollen. Achten Sie darauf, den Ordnern die richtigen Berechtigungen zuzuweisen.

2.  Geben Sie in einem Eingabeaufforderungsfenster den folgenden Befehl ein, um die Datei "EdgeTransport.exe.config" in Notepad zu öffnen:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

3.  Ändern Sie im Abschnitt `<appSettings>` die folgenden Schlüssel:
    
        <add key="QueueDatabasePath" value="<LocalPath>" />
        <add key="QueueDatabaseLoggingPath" value="<LocalPath>" />
    
    Wenn Sie beispielsweise den Speicherort der Warteschlangendatenbank in "D:\\Queue\\QueueDB" und den Speicherort der Transaktionsprotokolle in "D:\\Queue\\QueueLogs" ändern möchten, verwenden Sie folgende Werte:
    
        <add key="QueueDatabasePath" value="D:\Queue\QueueDB" />
        <add key="QueueDatabaseLoggingPath" value="D:\Queue\QueueLogs" />

4.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

5.  Beenden Sie den Microsoft Exchange-Transportdienst, indem Sie folgenden Befehl ausführen:
    
        net stop MSExchangeTransport

6.  Verschieben Sie die vorhandenen Datenbankdateien "Mail.que" und "Trn.chk" von dem ursprünglichen an den neuen Speicherort.

7.  Verschieben Sie die vorhandenen Transaktionsprotokolldateien "Trn.log", "Trntmp.log", "Trn*nnnnn*.log", "Trnres00001.jrs", "Trnres00002.jrs" und "Temp.edb" von dem alten an den neuen Speicherort.

8.  Starten Sie den Microsoft Exchange-Transportdienst, indem Sie folgenden Befehl ausführen:
    
        net start MSExchangeTransport

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob das Verschieben der vorhandenen Warteschlangendatenbank und der zugehörigen Transaktionsprotokolle an den neuen Speicherort erfolgreich verlaufen ist:

1.  Vergewissern Sie sich, dass die Warteschlangendatenbank-Dateien "Mail.que" und "Trn.chk" am neuen Speicherort vorhanden sind.

2.  Vergewissern Sie sich, dass die Transaktionsprotokolldateien "Trn.log", "Trntmp.log", "Trnres00001.jrs", "Trnres00002.jrs" und "Temp.edb" am neuen Speicherort vorhanden sind.

3.  Vergewissern Sie sich, dass keine Warteschlangendatenbank- oder Transaktionsprotokolldateien am ursprünglichen Speicherort vorhanden sind.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Was möchten Sie machen?

