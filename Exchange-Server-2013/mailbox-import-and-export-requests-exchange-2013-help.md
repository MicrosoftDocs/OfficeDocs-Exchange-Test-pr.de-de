---
title: 'Import- und Exportanforderungen für Postfächer: Exchange 2013 Help'
TOCTitle: Import- und Exportanforderungen für Postfächer
ms:assetid: 157a7d88-d3aa-4056-9a50-df67451b14be
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633455(v=EXCHG.150)
ms:contentKeyID: 50475068
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Import- und Exportanforderungen für Postfächer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Mit den Cmdlet-Sätzen **MailboxImportRequest** oder **MailboxExportRequest** der Exchange-Verwaltungsshell können Sie Daten aus PST-Dateien importieren oder in das PST-Format exportieren. Nach dem Initiieren einer Postfachimport- oder -exportanforderung wird der Vorgang vom Microsoft Exchange-Postfachreplikationsdienst asynchron ausgeführt. Der Postfachreplikationsdienst ist auf allen Exchange 2010-Clientzugriffsservern vorhanden und wird zum Verschieben von Postfächern sowie für den Import und Export von PST-Dateien eingesetzt.

**Inhalt**

Gründe für das Importieren oder Exportieren von Postfachdaten

Vorteile der Verwendung von Import- und Exportanforderungen

Überlegungen

Importieren von Postfachdaten

Exportieren von Postfachdaten

## Gründe für das Importieren oder Exportieren von Postfachdaten

Postfachdaten werden aus den folgenden Gründen importiert oder exportiert:

  - **Erfüllen von Anforderungen für die Einhaltung gesetzlicher Vorschriften**   Sie können die Postfachinhalte zur Einhaltung der Offenlegungspflicht in eine PST-Datei exportieren. Im Anschluss an den Export können Sie die Inhalte in ein Postfach importieren, das ausschließlich zum Nachweis der Einhaltung gesetzlicher Bestimmungen verwendet wird.

  - **Erstellen eines Snapshots des Postfachs**   Durch das Erstellen einer Shapshotsicherung von bestimmten Postfächern brauchen Sie nicht ständig einen kompletten Sicherungssatz einer Postfachdatenbank aufzubewahren.

  - **Verschieben einer PST-Benutzerdatei in das Postfach des Benutzers oder sein persönliches Archiv**   Microsoft Outlook-Benutzer können ihre E-Mails lokal als PST-Dateien speichern. Verwenden Sie das Cmdlet [New-MailboxImportRequest](https://technet.microsoft.com/de-de/library/ff607310\(v=exchg.150\)), um Daten aus einer PST-Benutzerdatei in das Postfach des Benutzers oder sein persönliches Archiv zu verschieben. Auf diese Weise lassen sich E-Mail-Daten problemlos vom lokalen Computer eines Benutzers an Exchange-Server übertragen.

## Vorteile der Verwendung von Import- und Exportanforderungen

Die Verwendung von Import- und Exportanforderungen in Exchange 2013 bietet u. a. folgende Vorteile:

  - Exchange 2013 enthält einen PST-Anbieter, der PST-Dateien lesen und schreiben kann.

  - Import- und Exportanforderungen werden asynchron verarbeitet. Der Prozess wird vom Postfachreplikationsdienst ausgeführt, der die Warteschlangen- und Drosselungsmechanismen nutzt.

  - Die PST-Dateien können direkt in das persönliche Archiv eines Benutzers importiert werden.

  - Es können gleichzeitig mehrere PST-Dateien importiert oder exportiert werden.

  - Die PST-Dateien können sich auf jedem freigegebenen Netzwerklaufwerk befinden, auf das die Exchange-Server zugreifen können.

  - Exchange 2013 unterstützt diese PST-Dateien: In Office Outlook 2007 und Outlook 2010 erstellte Unicode-Dateien

## Überlegungen

Beim Importieren oder Exportieren von Postfachdaten ist Folgendes zu berücksichtigen:

  - Zum Importieren oder Exportieren von Postfachdaten muss ein freigegebener Netzwerkordner eingerichtet sein, auf den alle Exchange-Server zugreifen können. Der Gruppe "Vertrauenswürdiges Exchange-Teilsystem" müssen Lese-/Schreibberechtigungen zugewiesen werden, damit diese Gruppe auf das Netzlaufwerk zugreifen kann, das für den Import und Export der Postfachdaten verwendet wird. Ohne diese Berechtigungen wird in einer Fehlermeldung angezeigt, dass Exchange keine Verbindung mit dem Zielpostfach herstellen kann.

  - Outlook unterstützt PST-Dateien bis zur maximalen Größe von 50 GB. Daher wird empfohlen, keine PST-Datei zu importieren, die größer als 50 GB ist. Für Postfächer mit mehr als 50 GB können Sie jedoch mehrere PST-Dateien erstellen, indem Sie bestimmte Ordner ein- oder ausschließen oder einen Inhaltsfilter verwenden.

  - Import- und Exportanforderungen werden vom Postfachreplikationsdienst ausgeführt, der auch die Anforderungen zum Verschieben und Wiederherstellen von Postfächern verarbeitet. Die Warteschlangen- und Drosselungsmechanismen für alle Anforderungen werden vom Postfachreplikationsdienst gesteuert.

  - Abhängig von der Dateigröße, der Netzwerkbandbreite und der Drosselung durch den Postfachreplikationsdienst kann das Importieren oder Exportieren von Postfachdaten mehrere Stunden in Anspruch nehmen.

  - Daten können nicht in einen Öffentlichen Ordner oder in eine Öffentliche Ordner-Datenbank importiert werden.

## Importieren von Postfachdaten

Verwenden Sie den Cmdlet-Satz **MailboxImportRequest**, um Daten aus einer PST-Datei in ein Postfach oder ein persönliches Archiv zu importieren. Beim Importieren von Daten aus einer PST-Datei können Sie die Optionen in folgender Liste angeben:


> [!NOTE]
> Das Postfach, in das die Daten importiert werden, muss vorhanden sein. Sie können keine Daten in ein Benutzerkonto importieren, das kein Postfach besitzt.



  - Die Daten können nicht nur in das Benutzerkonto importiert werden, aus dem sie exportiert wurden, sondern auch in ein anderes Benutzerkonto. Sie können beispielsweise Daten aus dem Postfach "john@contoso.com" exportieren und sie in das Postfach "legaldiscovery@contoso.com" importieren.

  - Durch Angabe des Parameters *IsArchive* können Sie Elemente ausschließlich in das persönliche Archiv des Benutzers importieren.

  - Wenn in der PST-Datei zugeordnete Ordnernachrichten vorhanden sind, können Sie diese mit dem Parameter *AssociatedMessagesCopyOption* importieren. Zugeordnete Nachrichten enthalten ausgeblendete Daten mit Informationen zu Regeln, Ansichten und Formularen. Alle Nachrichten aus dem Sicherheitsnetz werden importiert, sofern sie in der PST-Datei vorhanden sind.

  - Mit dem Parameter *IncludeFolders* oder *ExcludeFolders* können Sie bestimmte Ordner einbeziehen oder ausschließen.

  - Mit dem Parameter *ExcludeDumpster* wird der Ordner "Wiederherstellbare Elemente" ausgeschlossen. Standardmäßig wird der Ordner "Wiederherstellbare Elemente" in die Importanforderung einbezogen, wenn er in der PST-Datei enthalten ist.

## Cmdlets für Postfachimportanforderungen

Die folgenden Cmdlets werden für Postfachimportanforderungen verwendet.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607310(v=exchg.150)">New-MailboxImportRequest</a></p></td>
<td><p>Startet den Import einer PST-Datei in ein Postfach oder persönliches Archiv. Pro Postfach kann mehr als eine Importanforderung erstellt werden. Jede Anforderung muss einen eindeutigen Namen haben.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607317(v=exchg.150)">Set-MailboxImportRequest</a></p></td>
<td><p>Ändert die Optionen für die Importanforderung, nachdem die Anforderung erstellt oder nach einem Fehler wiederhergestellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607309(v=exchg.150)">Suspend-MailboxImportRequest</a></p></td>
<td><p>Hält eine Postfachimportanforderung jederzeit an, nachdem die Anforderung erstellt wurde, jedoch bevor die Anforderung den Status &quot;Erledigt&quot; erreicht.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607306(v=exchg.150)">Resume-MailboxImportRequest</a></p></td>
<td><p>Setzt eine Importanforderung fort, nachdem diese angehalten wurde oder ein Fehler aufgetreten ist.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607311(v=exchg.150)">Remove-MailboxImportRequest</a></p></td>
<td><p>Entfernt teilweise oder vollständig abgeschlossene Importanforderungen. Abgeschlossene Postfachimportanforderungen werden nicht automatisch gelöscht. Sie müssen mit diesem Cmdlet entfernt werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607368(v=exchg.150)">Get-MailboxImportRequest</a></p></td>
<td><p>Zeigt allgemeine Informationen zu einer Importanforderung an.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607315(v=exchg.150)">Get-MailboxImportRequestStatistics</a></p></td>
<td><p>Zeigt detaillierte Informationen zu einer Importanforderung an.</p></td>
</tr>
</tbody>
</table>


## Exportieren von Postfachdaten

Mit dem Cmdlet-Satz **MailboxExportRequest** werden Postfachdaten in eine PST-Datei exportiert. Sie können jeweils ein Postfach oder mehrere Postfächer exportieren, doch wird in jede PST-Datei immer nur eine Anforderung geschrieben. Beim Exportieren von Daten in eine PST-Datei können Sie die folgenden Optionen angeben:

  - Mit dem Parameter *IsArchive* exportieren Sie Daten aus dem persönlichen Archiv.

  - Mit dem Parameter *ContentFilter* werden die zu exportierenden Nachrichten gefiltert. Sie können nach Nachrichteninhalt, Anlage, Absender, Empfänger, Posteingangskategorie, Wichtigkeit, Nachrichtentyp, Nachrichtengröße sowie Sende-, Empfangs- oder Ablaufdatum filtern.

  - Mit dem Parameter *IncludeFolders* oder *ExcludeFolders* können Sie bestimmte Ordner einbeziehen oder ausschließen. Beim Exportieren von Daten aus einem Exchange 2013-Postfach können Sie zudem mit dem Parameter *ExcludeDumpster* den Ordner "Wiederherstellbare Elemente" ausschließen.

  - Mit dem Parameter *AssociatedMessagesCopyOption* werden zugeordnete Nachrichten exportiert. Zugeordnete Nachrichten enthalten ausgeblendete Daten mit Informationen zu Regeln, Ansichten und Formularen. Standardmäßig werden zugeordnete Elemente nicht in die PST-Datei kopiert.

## Cmdlets für Postfachexportanforderungen

Die folgenden Cmdlets werden für Postfachexportanforderungen verwendet.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607299(v=exchg.150)">New-MailboxExportRequest</a></p></td>
<td><p>Startet den Export von Daten aus einem primären Postfach oder einem persönlichen Archiv in eine PST-Datei. Pro Postfach können mehrere Exportanforderungen erstellt werden. Jede Anforderung muss einen eindeutigen Namen haben.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607312(v=exchg.150)">Set-MailboxExportRequest</a></p></td>
<td><p>Ändert die Optionen für die Exportanforderung, nachdem die Anforderung erstellt oder nach einem Fehler wiederhergestellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607305(v=exchg.150)">Suspend-MailboxExportRequest</a></p></td>
<td><p>Hält eine Postfachexportanforderung jederzeit an, nachdem die Anforderung erstellt wurde, jedoch bevor die Anforderung den Status &quot;Erledigt&quot; erreicht.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607476(v=exchg.150)">Resume-MailboxExportRequest</a></p></td>
<td><p>Setzt eine Exportanforderung fort, nachdem diese angehalten wurde oder ein Fehler aufgetreten ist.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607464(v=exchg.150)">Remove-MailboxExportRequest</a></p></td>
<td><p>Entfernt teilweise oder vollständig abgeschlossene Exportanforderungen. Abgeschlossene Postfachexportanforderungen werden nicht automatisch gelöscht. Sie müssen mit diesem Cmdlet entfernt werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607479(v=exchg.150)">Get-MailboxExportRequest</a></p></td>
<td><p>Zeigt allgemeine Informationen zu einer Exportanforderung an.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/ff607316(v=exchg.150)">Get-MailboxExportRequestStatistics</a></p></td>
<td><p>Zeigt detaillierte Informationen zu einer Exportanforderung an.</p></td>
</tr>
</tbody>
</table>

