---
title: 'Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln: Exchange 2013 Help'
TOCTitle: Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln
ms:assetid: c0de687e-e33c-4e8a-b253-771494678795
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674307(v=EXCHG.150)
ms:contentKeyID: 50476625
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-27_

Sie können E-Mail-Anlagen in Ihrer Organisation überprüfen, indem Sie Transportregeln einrichten. Exchange bietet Transportregeln, mit denen E-Mail-Anhänge im Rahmen Ihrer Messaging-bezogenen Sicherheits- und Compliance-Anforderungen überprüft werden können. Wenn Sie Anlagen überprüfen, können Sie basierend auf deren Inhalten oder Merkmalen für die überprüften Nachrichten Aktionen durchführen. Hier einige anlagenbezogene Aufgaben, die Sie mit Transportregeln durchführen können:

  - Dateien in komprimierten Anhängen wie ZIP- und RAR-Dateien durchsuchen und, wenn Text mit einem von Ihnen angegebenen Muster übereinstimmt, am Ende der Nachricht eine Haftungsausschlusserklärung hinzufügen.

  - Inhalt in Anlagen überprüfen und, wenn er von Ihnen angegebene Stichwörter enthält, die Nachricht vor der Zustellung zur Genehmigung an einen Moderator weiterleiten.

  - Nachrichten auf Anlagen überprüfen, die nicht überprüft werden können, und dann das Senden der gesamten Nachricht verhindern.

  - Auf Anlagen prüfen, die eine bestimmte Größe überschreiten, und dann den Absender darüber informieren, wenn Sie die Zustellung der Nachricht verhindern möchten.

  - Benachrichtigungen für Benutzer erstellen, falls sie eine Nachricht senden, die mit einer Transportregel übereinstimmt.

  - Blockieren aller Nachrichten mit Anlagen. Beispiele finden Sie unter [Standardszenarien für Anlagensperre](common-attachment-blocking-scenarios-for-mail-flow-rules-exchange-2013-help.md).

Exchange-Administratoren können Transportregeln über **Exchange Admin Center** \> **Nachrichtenfluss** \> **Regeln** erstellen. Bevor Sie dieses Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Nachdem Sie mit der Erstellung einer neuen Regel begonnen haben, können Sie die vollständige Liste anlagenbezogener Bedingungen anzeigen, indem Sie unter **Diese Regel anwenden** auf **Weitere Optionen** \> **Mindestens eine Anlage** klicken. Die anlagenbezogenen Optionen sind im folgenden Diagramm dargestellt.

![Dialogfeld zur Auswahl anlagenbezogener Regeln](images/JJ674307.2ae4a179-bfd2-4a0e-abe1-53ed4e9e3368(EXCHG.150).jpg "Dialogfeld zur Auswahl anlagenbezogener Regeln")

Weitere Informationen zu Transportregeln, einschließlich sämtlicher zur Wahl stehender Bedingungen und Aktionen, finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md). Exchange Online Protection (EOP)-Kunden und Kunden mit einer Hybridbereitstellung können von den unter [Bewährte Methoden für das Konfigurieren von EOP](https://technet.microsoft.com/de-de/library/jj723164\(v=exchg.150\)) angegebenen Best Practices für Transportregeln profitieren. Wenn Sie bereit sind, mit der Erstellung von Regeln zu beginnen, finden Sie unter [Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md) entsprechende Informationen.

## Überprüfen des Anlageninhalts

Sie können die Transportregelbedingungen in der folgenden Tabelle verwenden, um den Inhalt von Nachrichtenanlagen zu überprüfen. Bei diesen Bedingungen werden nur die ersten 150 KB einer Anlage überprüft. Um diese Bedingungen beim Überprüfen von Nachrichten nutzen zu können, müssen Sie sie zu einer Transportregel hinzufügen. Weitere Informationen zur Erstellung oder Änderung von Regeln finden Sie unter [Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name der Bedingung in der Exchange-Verwaltungskonsole</th>
<th>Name der Bedingung in der Shell</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ein Anlageninhalt enthält eines dieser Wörter</strong></p></td>
<td><p><code>AttachmentContainsWords</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten mit unterstützen Dateitypenanlagen, die eine angegebene Zeichenfolge oder Zeichengruppe enthalten.</p></td>
</tr>
<tr class="even">
<td><p><strong>Ein Anlageninhalt stimmt mit diesen Textmustern überein</strong></p></td>
<td><p><code>AttachmentMatchesPatterns</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten mit unterstützten Dateitypenanlagen, die ein Textmuster enthalten, das mit einem angegebenen regulären Ausdruck übereinstimmt.</p></td>
</tr>
</tbody>
</table>


Die Exchange-Verwaltungsshell-Namen für die hier aufgeführten Bedingungen sind Parameter, für die das `TransportRule`-Cmdlet benötigt wird.

  -  Weitere Informationen zum Cmdlet erhalten Sie unter [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\)).

  -  Weitere Informationen zu Eigenschaftstypen für diese Bedingungen finden Sie unter [Conditions and exceptions for mail flow rules on Mailbox servers](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md).

Mit Transportregeln wird nur der Inhalt von unterstützten Dateitypen überprüft. Wenn der Transportregel-Agent eine Anlage ermittelt, die nicht in der Liste der unterstützten Dateitypen aufgeführt ist, wird die Bedingung `AttachmentIsUnsupported` ausgelöst. Die unterstützten Dateitypen werden im folgenden Abschnitt aufgelistet. Jede nicht aufgeführte Datei löst die Bedingung `AttachmentIsUnsupported` aus.

## Komprimierte Archivdateien

Wenn die Nachricht eine komprimierte Archivdatei wie eine ZIP- oder CAB-Datei enthält, prüft der Transportregel-Agent die in der Anlage befindlichen Dateien. Diese Nachrichten werden auf ähnliche Weise verarbeitet wie Nachrichten, die über mehrere Anlagen verfügen. Die Eigenschaften komprimierter Archivdateien werden nicht überprüft. Wenn beispielsweise der Dateityp "Container" Kommentare unterstützt, wird dieses Feld nicht überprüft.

## Unterstützte Dateitypen für die Inhaltsüberprüfung mit Transportregeln

In der folgenden Tabelle werden die Dateitypen aufgelistet, die von Transportregeln unterstützt werden. Das System erkennt Dateitypen durch Überprüfung der Dateieigenschaften anstatt der eigentlichen Dateierweiterung automatisch. Auf diese Weise wird verhindert, dass bösartige Hacker die Transportregelfilterung durch das Umbenennen von Dateien umgehen können. Eine Liste der Dateitypen mit ausführbarem Code, die im Kontext von Transportregeln überprüft werden können, finden Sie weiter unten in diesem Thema.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Kategorie</th>
<th>Dateierweiterung</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Office 2013, Office 2010 und Office 2007</p></td>
<td><p>.docm, .docx, .pptm, .pptx, .pub, .one, .xlsb, .xlsm, .xlsx</p></td>
<td><p>Microsoft OneNote- und Microsoft Publisher-Dateien werden nicht standardmäßig unterstützt. Sie können die Unterstützung für diese Dateitypen mithilfe der IFilter-Integration aktivieren. Weitere Informationen finden Sie unter <a href="register-filter-pack-ifilters-with-exchange-2013-exchange-2013-help.md">Registrieren von Filterpaket-IFiltern für Exchange 2013</a>.</p>
<p>Der Inhalt in diesen Dateitypen eingebetteter Teile wird ebenfalls überprüft. Objekte, die jedoch nicht eingebettet sind, z. B. verknüpfte Dokumente, werden nicht überprüft.</p></td>
</tr>
<tr class="even">
<td><p>Office 2003</p></td>
<td><p>.doc, .ppt, .xls</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>Weitere Office-Dateien</p></td>
<td><p>.rtf, .vdw, .vsd, .vss, .vst</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>Adobe PDF</p></td>
<td><p>.pdf</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p>.html</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>XML</p></td>
<td><p>.xml, .odp, .ods, .odt</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td><p>TXT, ASM, BAT, C, CMD, CPP, CXX, DEF, DIC, H, HPP, HXX, IBQ, IDL, INC, INF, INI, INX, JS, LOG, M3U, PL, RC, REG, TXT, VBS, WTX</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>OpenDocument</p></td>
<td><p>.odp, .ods, .odt</p></td>
<td><p>Von ODF-Dateien werden keine Teile verarbeitet. Wenn die ODF-Datei beispielsweise ein eingebettetes Dokument enthält, wird der Inhalt dieses eingebetteten Dokuments nicht überprüft.</p></td>
</tr>
<tr class="odd">
<td><p>AutoCAD-Zeichnung</p></td>
<td><p>.dxf</p></td>
<td><p>AutoCAD 2013-Dateien werden nicht unterstützt.</p></td>
</tr>
<tr class="even">
<td><p>Bild</p></td>
<td><p>.jpg, .tiff</p></td>
<td><p>Nur diesen Bilddateien zugeordneter Metadatentext wird überprüft. Es gibt keine optische Zeichenerkennung.</p></td>
</tr>
</tbody>
</table>


## Überprüfen der Dateieigenschaften von Anlagen

Die folgende Transportregelbedingung überprüft die Eigenschaften einer an eine Nachricht angehängten Datei. Um diese Bedingungen beim Überprüfen von Nachrichten nutzen zu können, müssen Sie sie zu einer Transportregel hinzufügen. Eine Liste der unterstützten Dateitypen mit ausführbarem Code, die im Kontext von Transportregeln überprüft werden können, finden Sie hier. Weitere Informationen zum Erstellen und Ändern von Regeln finden Sie unter [Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name der Bedingung in der Exchange-Verwaltungskonsole</th>
<th>Name der Bedingung in der Shell</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Mindestens eine Anlage... einen Dateinamen hat, der diesen Textmustern entspricht</strong></p></td>
<td><p><code>AttachmentNameMatchesPatterns</code></p></td>
<td><p>Diese Bedingung gleicht Nachrichten mit unterstützten Dateitypanlagen ab, wenn diese Anlagen einen Namen aufweisen, der die von Ihnen angegebenen Zeichen enthält.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mindestens eine Anlage... eine Dateierweiterung hat, die diese Wörter enthält</strong></p></td>
<td><p><code>AttachmentExtensionMatchesWords</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten mit unterstützten Dateitypanlagen, wenn die Dateinamenerweiterung mit Ihren Angaben übereinstimmt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Mindestens eine Anlage ist größer oder gleich</strong></p></td>
<td><p><code>AttachmentSizeOver</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten mit unterstützten Dateitypanlagen, wenn diese Anlagen die von Ihnen angegebene Größe überschreiten.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mindestens eine Anlage... Überprüfung nicht abgeschlossen wurde</strong></p></td>
<td><p><code>AttachmentProcessingLimitExceeded</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten, wenn eine Anlage vom Transportregel-Agenten nicht überprüft wird.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Mindestens eine Anlage hat ausführbaren Inhalt</strong></p></td>
<td><p><code>AttachmentHasExecutableContent</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten, die ausführbare Dateien als Anlagen enthalten. Die unterstützten Dateitypen finden Sie hier.</p></td>
</tr>
<tr class="even">
<td><p><strong>Jede Anlage ist kennwortgeschützt</strong></p></td>
<td><p><code>AttachmentIsPasswordProtected</code></p></td>
<td><p>Diese Bedingung ermittelt Nachrichten mit unterstützten Dateitypanlagen, wenn diese Anlagen durch ein Kennwort geschützt sind.</p></td>
</tr>
</tbody>
</table>


Die Exchange-Verwaltungsshell-Namen für die hier aufgeführten Bedingungen sind Parameter, für die das `TransportRule`-Cmdlet benötigt wird.

  -  Weitere Informationen zum Cmdlet erhalten Sie unter [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\)).

  -  Weitere Informationen zu Eigenschaftstypen für diese Bedingungen finden Sie unter [Conditions and exceptions for mail flow rules on Mailbox servers](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md).

## Unterstützte ausführbare Dateitypen für die Überprüfung mit Transportregeln

Der Transport-Agent verwendet True-Type-Erkennung, indem die Dateieigenschaften und nicht nur die Dateierweiterungen untersucht werden. Hierdurch wird verhindert, dass Hacker mit böswilligen Absichten Ihre Regel umgehen, indem sie eine Dateierweiterung umbenennen. In der folgenden Tabelle werden die ausführbaren Dateitypen aufgelistet, die von diesen Bedingungen unterstützt werden. Für Dateien, die nicht in dieser Liste aufgeführt sind, wird die Bedingung `AttachmentIsUnsupported` ausgelöst.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Dateityp</th>
<th>Systemeigene Erweiterung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mit WinRAR erstellte selbstextrahierende Archivdatei</p></td>
<td><p>.rar</p></td>
</tr>
<tr class="even">
<td><p>Ausführbare 32-Bit-Windows-Datei mit einer DLL-Erweiterung (Dynamic Link Library)</p></td>
<td><p>.dll</p></td>
</tr>
<tr class="odd">
<td><p>Selbstextrahierende, ausführbare Programmdatei</p></td>
<td><p>.exe</p></td>
</tr>
<tr class="even">
<td><p>Java-Archivdatei</p></td>
<td><p>.jar</p></td>
</tr>
<tr class="odd">
<td><p>Ausführbare Datei für die Deinstallation.</p></td>
<td><p>.exe</p></td>
</tr>
<tr class="even">
<td><p>Programm-Verknüpfungsdatei</p></td>
<td><p>.exe</p></td>
</tr>
<tr class="odd">
<td><p>Kompilierte Quellcodedatei oder 3D-Objektdatei oder Sequenzdatei</p></td>
<td><p>.obj</p></td>
</tr>
<tr class="even">
<td><p>Ausführbare 32-Bit-Windows-Datei</p></td>
<td><p>.exe</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Visio XML-Zeichnungsdatei</p></td>
<td><p>.vxd</p></td>
</tr>
<tr class="even">
<td><p>OS/2-Betriebssystemdatei</p></td>
<td><p>.os2</p></td>
</tr>
<tr class="odd">
<td><p>Ausführbare 16-Bit-Windows-Datei</p></td>
<td><p>.w16</p></td>
</tr>
<tr class="even">
<td><p>Disk Operating System-Datei</p></td>
<td><p>.dos</p></td>
</tr>
<tr class="odd">
<td><p>Standardmäßige Antivirus-Testdatei von European Institute for Computer Antivirus Research</p></td>
<td><p>.com</p></td>
</tr>
<tr class="even">
<td><p>Windows-Programminformationsdatei</p></td>
<td><p>.pif</p></td>
</tr>
<tr class="odd">
<td><p>Ausführbare Windows-Programmdatei</p></td>
<td><p>.exe</p></td>
</tr>
</tbody>
</table>


## Erweitern der Anzahl von unterstützten Dateitypen

Die in diesem Artikel aufgeführten Dateitypen können jederzeit mithilfe der IFilter-Integration überprüft werden. Weitere Informationen finden Sie unter [Registrieren von Filterpaket-IFiltern für Exchange 2013](register-filter-pack-ifilters-with-exchange-2013-exchange-2013-help.md).

Die Dateitypen, die Sie mit diesem Verfahren hinzufügen, werden zu unterstützten Dateitypen und lösen damit die Bedingung `AttachmentIsUnsupported` nicht mehr aus.

## Richtlinien zur Verhinderung von Datenverlust und Transportregeln für Anlagen

Um Ihnen die Verwaltung wichtiger Geschäftsinformationen in E-Mails zu erleichtern, können Sie neben den Regeln einer DLP-Richtlinie (Data Loss Prevention, Verhinderung von Datenverlust) eine beliebige anlagenbezogene Bedingung einschließen. So möchten Sie vielleicht z. B. das Senden von Nachrichten mit Ausweisnummern nur dann zulassen, wenn sich die Ausweisnummern in einer kennwortgeschützten Anlage befinden. Führen Sie dazu die folgenden Schritte aus:

  - Erstellen Sie eine DLP-Richtlinie, die E-Mails auf ausweisbezogene vertrauliche Informationen überprüft. Weitere Informationen finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md).

  - Fügen Sie die Ausnahme **Jede Anlage ist kennwortgeschützt** im Transportregelbereich **Außer wenn...** hinzu.

  - Definieren Sie eine Aktion, die bei E-Mails ausgeführt wird, die Ausweisnummern enthalten, die sich nicht in der geschützten Datei befinden.

DLP-Richtlinien und anlagenbezogene Bedingungen können Ihnen helfen, Ihren Geschäftsanforderungen gerecht zu werden, indem sie diese Anforderungen als Transportregelbedingungen, Ausnahmen und Aktionen definieren. Wenn Sie die Überprüfung vertraulicher Informationen in eine DLP-Richtlinie einschließen, werden Nachrichtenanlagen nur auf diese Informationen überprüft. Anlagenbezogene Bedingungen wie Größe oder Dateityp werden jedoch erst eingeschlossen, wenn Sie die in diesem Thema aufgeführten Bedingungen hinzufügen. DLP ist nicht in allen Versionen von Exchange verfügbar. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md).

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

[Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\)) in Exchange Online

