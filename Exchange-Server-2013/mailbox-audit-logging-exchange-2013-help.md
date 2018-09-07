---
title: 'Überwachungsprotokollierung von Postfächern: Exchange 2013 Help'
TOCTitle: Überwachungsprotokollierung von Postfächern
ms:assetid: 29b67d58-eef9-4ad4-863f-562405ea8794
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff459237(v=EXCHG.150)
ms:contentKeyID: 50475245
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Überwachungsprotokollierung von Postfächern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Da Postfächer vertrauliche und für das Unternehmen zentrale Informationen sowie Informationen zur persönlichen Identifizierung enthalten können, ist es wichtig zu verfolgen, wer sich an den Postfächern in Ihrer Organisation anmeldet und welche Aktionen ausgeführt werden. Eine besondere Rolle spielt hierbei die Verfolgung des Postfachzugriffs durch Benutzer, die nicht mit dem Postfachbesitzer identisch sind. Diese Benutzer werden als *Stellvertretungsbenutzer* bezeichnet.

Mithilfe der *Postfachüberwachungsprotokollierung* können Sie den durch Postfachbesitzer, Stellvertretungen (einschließlich Administratoren mit vollständigen Postfachzugriffsberechtigungen) und Administratoren erfolgten Postfachzugriff protokollieren.

Wenn Sie die Überwachungsprotokollierung für ein Postfach aktivieren, können Sie angeben, welche Benutzeraktionen (beispielsweise Zugriff auf eine Nachricht, Verschieben oder Löschen einer Nachricht) für einen Anmeldetyp (Administrator, Stellvertretungsbenutzer oder Besitzer) protokolliert werden. Die Einträge im Überwachungsprotokoll umfassen auch Informationen wie die Client-IP-Adresse, den Hostnamen und den Prozess oder Client, der für den Zugriff auf das Postfach verwendet wurde. Bei verschobenen Elementen umfasst der Eintrag den Namen des Zielordners.

## Postfachüberwachungsprotokolle

Postfachüberwachungsprotokolle werden für jedes Postfach generiert, für das die Postfachüberwachungsprotokollierung aktiviert ist. Protokolleinträge werden im Unterordner "Überwachungen" des Ordners "Wiederherstellbare Elemente" des überwachten Postfachs gespeichert. Hierdurch ist sichergestellt, dass alle Überwachungsprotokolleinträge zentral verfügbar sind, und zwar unabhängig davon, welche Clientzugriffsmethode für den Zugriff auf das Postfach verwendet wurde oder welchen Server oder welche Arbeitsstation ein Administrator für den Zugriff auf das Postfachüberwachungsprotokoll verwendet hat. Wenn Sie ein Postfach zu einem anderen Postfachserver verschieben, werden die Postfachüberwachungsprotokolle ebenfalls verschoben, da sie sich im Postfach befinden.

Standardmäßig werden Postfachüberwachungsprotokolleinträge 90 Tage lang aufbewahrt und dann gelöscht. Sie können diese Aufbewahrungsfrist ändern, indem Sie den Parameter *AuditLogAgeLimit* mit dem Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) verwenden. Wenn für ein Postfach das Compliance-Archiv oder die Beweissicherung aktiviert wurde, werden Überwachungsprotokolleinträge nur so lange beibehalten, bis die Beibehaltungsdauer von Überwachungsprotokollen für das Postfach erreicht wurde. Wenn Sie Überwachungsprotokolleinträge länger beibehalten möchten, müssen Sie die Aufbewahrungsdauer verlängern, indem Sie den Wert des Parameters *AuditLogAgeLimit* ändern. Sie können auch die Überwachungsprotokolleinträge exportieren, bevor die Aufbewahrungsdauer erreicht ist. Weitere Informationen finden Sie unter:

  - [Exportieren von Postfachüberwachungsprotokollen](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)

  - [Erstellen einer Postfachüberwachungsprotokoll-Suche](create-a-mailbox-audit-log-search-exchange-2013-help.md)

## Aktivieren der Postfachüberwachungsprotokollierung

Die Postfachüberwachungsprotokollierung wird auf Postfachebene aktiviert. Verwenden Sie das Cmdlet **Set-Mailbox** zum Aktivieren oder Deaktivieren der Postfachüberwachungsprotokollierung. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach](enable-or-disable-mailbox-audit-logging-for-a-mailbox-exchange-2013-help.md).

Wenn die Postfachüberwachungsprotokollierung für ein Postfach aktiviert wird, werden der Zugriff auf das Postfach sowie bestimmte von Administratoren und Stellvertretungen ausgeführte Aktionen standardmäßig protokolliert. Damit vom Postfachbesitzer ausgeführte Aktionen protokolliert werden, müssen Sie angeben, welche Besitzeraktionen überwacht werden sollen.

## Durch die Postfachüberwachungsprotokollierung erfasste Postfachaktionen

In der folgenden Tabelle sind die Aktionen, die von der Postfachüberwachungsprotokollierung erfasst werden, sowie die Anmeldetypen aufgeführt, für die die Aktion protokolliert werden kann.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktion</th>
<th>Beschreibung</th>
<th>Administrator</th>
<th>Stellvertretung</th>
<th>Besitzer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kopieren</p></td>
<td><p>Ein Element wird in einen anderen Ordner kopiert.</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Create</p></td>
<td><p>Ein Element wird im Postfachordner „Kalender“, „Kontakte“, „Aufgaben“ oder „Notizen“ erstellt. Beispielsweise wird eine neue Besprechungsanfrage erstellt. Die Erstellung von Nachrichten oder Ordnern wird nicht überwacht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>FolderBind</p></td>
<td><p>Auf einen Postfachordner wird zugegriffen.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja**</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>HardDelete</p></td>
<td><p>Ein Element wird dauerhaft aus dem Ordner &quot;Wiederherstellbare Elemente&quot; gelöscht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>MessageBind</p></td>
<td><p>Auf ein Element wird im Lesebereich zugegriffen oder es wird im Lesebereich geöffnet.</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Verschieben</p></td>
<td><p>Ein Element wird in einen anderen Ordner verschoben.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>MoveToDeletedItems</p></td>
<td><p>Ein Element wird in den Ordner &quot;Gelöschte Elemente&quot; verschoben.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>SendAs</p></td>
<td><p>Eine Nachricht wird mithilfe der Berechtigung &quot;Senden als&quot; gesendet.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>SendOnBehalf</p></td>
<td><p>Eine Nachricht wird mithilfe der Berechtigung &quot;Senden im Auftrag von&quot; gesendet.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>SoftDelete</p></td>
<td><p>Ein Element wird aus dem Ordner &quot;Gelöschte Elemente&quot; gelöscht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Aktualisieren</p></td>
<td><p>Die Eigenschaften eines Elements werden aktualisiert.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


\* Wird standardmäßig überwacht, wenn die Überwachung für ein Postfach aktiviert wurde.

\*\* Einträge für Ordnerbindungsaktionen, die von Stellvertretungen ausgeführt werden, werden zusammengefasst. Für einzelne Ordnerzugriffe innerhalb eines Zeitraums von 24 Stunden wird ein eigener Protokolleintrag generiert.

Wenn die Überwachung bestimmte Postfachaktionen nicht mehr notwendig ist, sollten Sie die Überwachungsprotokollkonfiguration für das Postfach ändern, um die Überwachung dieser Aktionen zu deaktivieren. Vorhandene Protokolleinträge werden erst dann gelöscht, wenn für Überwachungsprotokolleinträge die Altersgrenze erreicht ist.

## Suchen nach Einträgen im Postfachüberwachungsprotokoll

Mithilfe der folgenden Methoden können Sie Postfachüberwachungsprotokolleinträge durchsuchen:

  - **Synchrone Suche in einem einzelnen Postfach**   Mit dem Cmdlet [Search-MailboxAuditLog](https://technet.microsoft.com/de-de/library/ff522360\(v=exchg.150\)) können Sie die Postfachüberwachungsprotokolleinträge für ein einzelnes Postfach synchron durchsuchen. Die Suchergebnisse werden im Fenster der Exchange-Verwaltungsshell angezeigt. Weitere Informationen finden Sie unter [Durchsuchen des Überwachungsprotokolls für ein Postfach](search-the-mailbox-audit-log-for-a-mailbox-exchange-2013-help.md).

  - **Asynchrone Suche in einem oder mehreren Postfächern**   Sie können eine Postfachüberwachungsprotokoll-Suche erstellen, um die Postfachüberwachungsprotokolle für ein oder mehrere Postfächer asynchron zu durchsuchen. Anschließend können die Suchergebnisse an eine bestimmte E-Mail-Adresse gesendet werden. Die Suchergebnisse werden als XML-Anlage gesendet. Verwenden Sie zum Erstellen der Suche das Cmdlet [New-MailboxAuditLogSearch](https://technet.microsoft.com/de-de/library/ff522362\(v=exchg.150\)). Weitere Informationen finden Sie unter [Erstellen einer Postfachüberwachungsprotokoll-Suche](create-a-mailbox-audit-log-search-exchange-2013-help.md).

  - **Verwenden von Überwachungsberichten in der Exchange-Verwaltungskonsole**   Mithilfe der Registerkarte **Überwachung** in der Exchange-Verwaltungskonsole können Sie einen Bericht zum Postfachzugriff durch Nicht-Besitzer ausführen oder Einträge aus dem Postfachüberwachungsprotokoll exportieren. Weitere Informationen finden Sie unter:
    
      - [Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/protected-voice-mail-procedures)
    
      - [Exportieren von Postfachüberwachungsprotokollen](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)

## Einträge im Postfachüberwachungsprotokoll

In der folgenden Tabelle werden die Felder beschrieben, die in einem Überwachungsprotokolleintrag für ein Postfach protokolliert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feld</th>
<th>Enthaltene Angaben</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Operation</strong></p></td>
<td><p>Eine der folgenden Aktionen:</p>
<ul>
<li><p>Kopieren</p></li>
<li><p>Erstellen</p></li>
<li><p>FolderBind</p></li>
<li><p>HardDelete</p></li>
<li><p>MessageBind</p></li>
<li><p>Verschieben</p></li>
<li><p>MoveToDeletedItems</p></li>
<li><p>SendAs</p></li>
<li><p>SendOnBehalf</p></li>
<li><p>SoftDelete</p></li>
<li><p>Aktualisieren</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>OperationResult</strong></p></td>
<td><p>Eines der folgenden Ergebnisse:</p>
<ul>
<li><p>Failed</p></li>
<li><p>PartiallySucceeded</p></li>
<li><p>Succeeded</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>LogonType</strong></p></td>
<td><p>Anmeldetyp des Benutzers, der den Vorgang ausgeführt hat. Folgende Anmeldetypen sind verfügbar:</p>
<ul>
<li><p>Besitzer</p></li>
<li><p>Stellvertretung</p></li>
<li><p>Administrator</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>DestFolderId</strong></p></td>
<td><p>Zielordner-GUID für Verschiebungsvorgänge.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DestFolderPathName</strong></p></td>
<td><p>Zielordnerpfad für Verschiebungsvorgänge.</p></td>
</tr>
<tr class="even">
<td><p><strong>FolderId</strong></p></td>
<td><p>Ordner-GUID.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FolderPathName</strong></p></td>
<td><p>Ordnerpfad.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientInfoString</strong></p></td>
<td><p>Details, die angeben, welcher Client oder welche Exchange-Komponente den Vorgang ausgeführt hat.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientIPAddress</strong></p></td>
<td><p>IP-Adresse des Clientcomputers.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientMachineName</strong></p></td>
<td><p>Name des Clientcomputers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientProcessName</strong></p></td>
<td><p>Name des Clientanwendungsprozesses.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersion</strong></p></td>
<td><p>Version der Clientanwendung.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InternalLogonType</strong></p></td>
<td><p>Anmeldetyp des Benutzers, der den Vorgang ausgeführt hat. Folgende Anmeldetypen sind verfügbar:</p>
<ul>
<li><p>Besitzer</p></li>
<li><p>Stellvertretung</p></li>
<li><p>Administrator</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>MailboxOwnerUPN</strong></p></td>
<td><p>Benutzerprinzipalname des Postfachbesitzers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MailboxOwnerSid</strong></p></td>
<td><p>Sicherheits-ID (SID) des Postfachbesitzers.</p></td>
</tr>
<tr class="even">
<td><p><strong>DestMailboxOwnerUPN</strong></p></td>
<td><p>Benutzerprinzipalname des Besitzers des Zielpostfachs; wird bei postfachübergreifenden Vorgängen protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DestMailboxOwnerSid</strong></p></td>
<td><p>SID des Besitzers des Zielpostfachs; wird bei postfachübergreifenden Vorgängen protokolliert.</p></td>
</tr>
<tr class="even">
<td><p><strong>DestMailboxOwnerGuid</strong></p></td>
<td><p>GUID des Besitzers des Zielpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CrossMailboxOperation</strong></p></td>
<td><p>Informationen, die angeben, ob es sich bei dem protokollierten Vorgang um einen postfachübergreifenden Vorgang handelt (beispielsweise Kopieren oder Verschieben von Nachrichten zwischen Postfächern).</p></td>
</tr>
<tr class="even">
<td><p><strong>LogonUserDisplayName</strong></p></td>
<td><p>Anzeigename des angemeldeten Benutzers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DelegateUserDisplayName</strong></p></td>
<td><p>Anzeigename des Stellvertretungsbenutzers.</p></td>
</tr>
<tr class="even">
<td><p><strong>LogonUserSid</strong></p></td>
<td><p>SID des angemeldeten Benutzers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SourceItems</strong></p></td>
<td><p>Element-ID von Postfachelementen, für die die protokollierte Aktion ausgeführt wird (beispielsweise Verschieben oder Löschen). bei Vorgängen, die für mehrere Elemente ausgeführt werden, wird dieses Feld als Auflistung von Elementen zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceFolders</strong></p></td>
<td><p>GUID des Quellordners.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ItemId</strong></p></td>
<td><p>Element-ID.</p></td>
</tr>
<tr class="even">
<td><p><strong>ItemSubject</strong></p></td>
<td><p>Betreff des Elements.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MailboxGuid</strong></p></td>
<td><p>Postfach-GUID.</p></td>
</tr>
<tr class="even">
<td><p><strong>MailboxResolvedOwnerName</strong></p></td>
<td><p>Aufgelöster Name des Postfachbenutzers im Format <em>DOMÄNE</em>\<em>SamKontoname</em>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastAccessed</strong></p></td>
<td><p>Zeitpunkt der Ausführung des Vorgangs.</p></td>
</tr>
<tr class="even">
<td><p><strong>Identity</strong></p></td>
<td><p>ID des Überwachungsprotokolleintrags.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

  - **Administratorzugriff auf Postfächer**   Nur in den folgenden Szenarien wird ein Postfachzugriff als Administratorzugriff erachtet:
    
      - [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md) wird zum Durchsuchen eines Postfachs verwendet.
    
      - Das Cmdlet [New-MailboxExportRequest](https://technet.microsoft.com/de-de/library/ff607299\(v=exchg.150\)) wird zum Exportieren eines Postfachs verwendet.
    
      - [Microsoft Exchange Server MAPI Editor](https://go.microsoft.com/fwlink/p/?linkid=204086) wird für den Zugriff auf das Postfach verwendet.

  - **Umgehen der Protokollierung der Postfachüberwachung**   Der Postfachzugriff durch autorisierte automatisierte Prozesse wie Konten, die von Drittanbietertools oder für die gesetzliche Überwachung verwendet werden, kann zu einer hohen Anzahl an Einträgen im Postfachüberwachungsprotokoll führen, und dies ist für Ihre Organisation möglicherweise nicht erforderlich. Sie können derartige Konten so konfigurieren, dass die Postfachüberwachungsprotokollierung umgangen wird. Weitere Informationen finden Sie unter [Umgehen der Postfachüberwachungsprotokollierung für ein Benutzerkonto](bypass-a-user-account-from-mailbox-audit-logging-exchange-2013-help.md).

  - **Protokollieren der Aktionen von Postfachbesitzern**   Bei Postfächern wie dem Discoverysuchpostfach, die vertraulichere Informationen enthalten können, sollten Sie die Aktivierung der Postfachüberwachungsprotokollierung für Aktionen von Postfachbesitzern, etwa für das Löschen von Nachrichten, in Erwägung ziehen.

Postfachüberwachungsprotokolle

