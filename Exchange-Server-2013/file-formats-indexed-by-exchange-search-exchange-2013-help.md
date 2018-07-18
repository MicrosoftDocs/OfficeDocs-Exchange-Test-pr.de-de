---
title: 'Von der Exchange-Suche indizierte Dateiformate: Exchange 2013 Help'
TOCTitle: Von der Exchange-Suche indizierte Dateiformate
ms:assetid: e5110ac1-28e1-4554-acc3-85d08c997bc5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633485(v=EXCHG.150)
ms:contentKeyID: 52062917
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Von der Exchange-Suche indizierte Dateiformate

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-21_

In MicrosoftExchange Server 2013 und Exchange Online bietet die Exchange-Suche Filter für die Indizierung der gängigsten Typen von Dateiformaten, die als Nachrichtenanlagen angefügt werden. Sie können auch Filter installieren, um zusätzliche Dateitypen zu indizieren.


> [!NOTE]
> In Exchange 2013 muss das Microsoft Office Filter Pack nicht installiert und registriert werden.



Bei der Verwaltung und Nutzung der Exchange-Suche und der abhängigen Funktionen (z. B. [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)) müssen Sie den Unterschied zwischen nicht durchsuchbaren Elementen und Dateiformaten berücksichtigen, die für die Indizierung deaktiviert sind oder Inhalte aufweisen, die nicht indiziert werden können:

  - **Nicht durchsuchbare Elemente**   Wenn die Exchange-Suche einen bestimmten Dateityp aus beliebigen Gründen nicht indizieren kann (da z. B. ein Filter nicht installiert ist), treten bei der Suche nach diesem Dateityp Fehler auf. Nachrichten mit solchen Anlagen werden als *teilweise indiziert* gekennzeichnet. Nicht durchsuchbare Elemente können mit dem Cmdlet [Get-FailedContentIndexDocuments](https://technet.microsoft.com/de-de/library/dd351154\(v=exchg.150\)) abgerufen werden. Wenn Sie Compliance-eDiscovery-Suchergebnisse in ein Discoverypostfach kopieren oder Suchergebnisse in eine PST-DAtei exportieren, können Sie nicht durchsuchbare Elemente einschließen. Weitere Informationen finden Sie unter [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md).

  - **Dateiformate mit Inhalten, die nicht indiziert werden können**   Bestimmte Dateien wie Windows Media Video (WMV) haben keine Inhalte, die indiziert werden können, und werden deshalb nicht indiziert. Nachrichten mit Anlagen mit solchen Dateitypen werden bei Compliance-eDiscovery-Suchen auch als nicht durchsuchbare Elemente zurückgegeben.

  - **Deaktivierte Dateiformate** Bei Organisationen mit lokaler Exchange-Version kann ein Administrator die Indizierung eines bestimmten Dateiformats deaktivieren. Nachrichten mit einer Anlage, die ein deaktiviertes Format hat, werden nicht als nicht durchsuchbare Elemente zurückgegeben.


> [!IMPORTANT]
> Auch wenn eine Nachrichtenanlage nicht durchsuchbar sein kann, können möglicherweise ihr Betreff, Text und andere Metadaten indiziert und bei Suchvorgängen zurückgegeben werden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Exchange-Suche in lokalen Organisationen finden Sie unter [Exchange-Suchverfahren](exchange-search-procedures-exchange-2013-help.md).

## Standardfilter

In der folgenden Tabelle sind die Standardsuchfilter aufgeführt, die auf einem Exchange 2013-Postfachserver und in Exchange Online installiert sind. Mit dem Cmdlet [Get-SearchDocumentFormat](https://technet.microsoft.com/de-de/library/jj873755\(v=exchg.150\)) können Sie die Liste der Standardfilter abrufen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Filter</th>
<th>Dateierweiterung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E-Mail-Nachricht</p></td>
<td><p>.eml</p></td>
</tr>
<tr class="even">
<td><p>Graphics Interchange Format</p></td>
<td><p>.gif</p></td>
</tr>
<tr class="odd">
<td><p>JPEG</p></td>
<td><p>.jpeg</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Excel</p></td>
<td><p>.xls, .xlt, .xlsx, .xlsm, .xlb, .xlc, .xlsb</p></td>
</tr>
<tr class="odd">
<td><p>Excel-Datei</p></td>
<td><p>odbcexcel</p></td>
</tr>
<tr class="even">
<td><p>Microsoft InfoPath</p></td>
<td><p>.infopathml</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Office Binder</p></td>
<td><p>.obt, obd</p></td>
</tr>
<tr class="even">
<td><p>Microsoft PowerPoint</p></td>
<td><p>.pptx, .pptm, .ppt, .ppsx, .ppsm, .pps, .ppam, .potm, .pot, .potx</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Publisher</p></td>
<td><p>.pub</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Word</p></td>
<td><p>.doc, .docm, .dotx, .dotm, .dot, .docx</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft XML Paper Specification</p></td>
<td><p>.xps</p></td>
</tr>
<tr class="even">
<td><p>OneNote</p></td>
<td><p>.one</p></td>
</tr>
<tr class="odd">
<td><p>OpenDocument-Präsentation</p></td>
<td><p>.odp</p></td>
</tr>
<tr class="even">
<td><p>OpenDocument-Kalkulationstabelle</p></td>
<td><p>.ods</p></td>
</tr>
<tr class="odd">
<td><p>OpenDocument-Text</p></td>
<td><p>.odt</p></td>
</tr>
<tr class="even">
<td><p>Outlook-Element</p></td>
<td><p>.msg</p></td>
</tr>
<tr class="odd">
<td><p>Portable Document Format</p></td>
<td><p>.pdf</p></td>
</tr>
<tr class="even">
<td><p>Rich-Text</p></td>
<td><p>.rtf</p></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td><p>.txt</p></td>
</tr>
<tr class="even">
<td><p>vCalendar</p></td>
<td><p>.vcs</p></td>
</tr>
<tr class="odd">
<td><p>vCard</p></td>
<td><p>.vcf</p></td>
</tr>
<tr class="even">
<td><p>Visio</p></td>
<td><p>.vdw, .vsd, .vss, .vst, .vsx, .vtx, .vssx, .vssm, .vsdm, .vstx, .vstm, .vdx</p></td>
</tr>
<tr class="odd">
<td><p>Webarchiv</p></td>
<td><p>.mhtml</p></td>
</tr>
<tr class="even">
<td><p>Webseite</p></td>
<td><p>.html</p></td>
</tr>
<tr class="odd">
<td><p>XML-Dokument</p></td>
<td><p>.xml</p></td>
</tr>
<tr class="even">
<td><p>ZIP-Archiv</p></td>
<td><p>.zip</p></td>
</tr>
</tbody>
</table>


## Deaktivierte Dateiformate

Die folgende Tabelle listet die Suchfilter auf, die für die standardmäßige Indizierung bei einem Exchange 2013-Postfachserver und in Exchange Online deaktiviert sind. Bei Exchange 2013 können Administratoren ein unterstütztes Dateiformat zur Indizierung deaktivieren oder erneut aktivieren, indem Sie [Set-SearchDocumentFormat](https://technet.microsoft.com/de-de/library/jj873756\(v=exchg.150\))-Cmdlet verwenden. Dieses Cmdlet ist in Exchange Online nicht verfügbar.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Filter</th>
<th>Dateierweiterung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AVI</p></td>
<td><p>.avi</p></td>
</tr>
<tr class="even">
<td><p>Bitmap</p></td>
<td><p>.bmp</p></td>
</tr>
<tr class="odd">
<td><p>MP3</p></td>
<td><p>.mp3</p></td>
</tr>
<tr class="even">
<td><p>MPEG</p></td>
<td><p>.mpeg</p></td>
</tr>
<tr class="odd">
<td><p>PNG</p></td>
<td><p>.png</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Windows Wave-Audio</p></td>
<td><p>.wav</p></td>
</tr>
</tbody>
</table>

