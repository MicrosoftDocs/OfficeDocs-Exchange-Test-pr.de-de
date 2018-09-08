---
title: 'Std.ordner m. Unterst. f. Aufbewahrungsrichtlinientags: Exchange 2013-Hilfe'
TOCTitle: Standardordner, die Aufbewahrungsrichtlinientags unterstützen
ms:assetid: d2e2064f-4102-4018-b688-504d09da6d39
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn783294(v=EXCHG.150)
ms:contentKeyID: 62835944
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Standardordner, die Aufbewahrungsrichtlinientags unterstützen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-04-20_

Sie können [Aufbewahrungstags und Aufbewahrungsrichtlinien](https://technet.microsoft.com/de-de/library/Dd297955(v=EXCHG.150)) verwenden, um den E-Mail-Lebenszyklus zu verwalten. Aufbewahrungsrichtlinien enthalten Aufbewahrungstags, die Einstellungen darstellen, mit denen Sie festlegen können, wann eine Nachricht automatisch in das Archiv verschoben und wann es gelöscht werden soll.

Ein Aufbewahrungsrichtlinientag (Retention Policy Tag, RPT) ist eine Art Aufbewahrungstag, das Sie auf Standardordner in einem Postfach, wie z. B. **Posteingang** und **Gelöschte Elemente**, anwenden können.

![Aufbewahrungsrichtlinientag (Retention Policy Tag, RPT) erstellen](images/Dn783294.b59a96fd-94e1-4c9b-bff6-97a1bd98dfe7(EXCHG.150).png "Aufbewahrungsrichtlinientag (Retention Policy Tag, RPT) erstellen")

## Unterstützte Standardordner

Sie können Aufbewahrungsrichtlinientags für die in der folgenden Tabelle aufgeführten Standardordner erstellen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ordnername</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Archiv</p></td>
<td><p>Dieser Ordner ist das standardmäßige Ziel für Nachrichten, die mit der Schaltfläche zum Archivieren in Outlook archiviert werden. Das Feature für die Archivierung bietet eine schnelle Möglichkeit für Benutzer, Nachrichten aus dem Posteingang zu entfernen, ohne sie zu löschen.</p>
<p>Dieser RPT ist nur in Exchange Online verfügbar.</p></td>
</tr>
<tr class="even">
<td><p>Kalender</p></td>
<td><p>In diesem Standardordner werden Besprechungen und Termine gespeichert.</p></td>
</tr>
<tr class="odd">
<td><p>Unwichtige Elemente</p></td>
<td><p>Dieser Ordner enthält E-Mails mit niedriger Priorität. „Unwichtige Elemente“ prüft Ihre in der Vergangenheit vorgenommenen Aktionen, um zu bestimmen, welche Nachrichten Sie wahrscheinlich ignorieren. Es verschiebt diese Nachrichten dann in den Ordner <strong>Unwichtige Elemente</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Aufgezeichnete Unterhaltungen</p></td>
<td><p>Dieser Ordner wird von Microsoft Lync (ehemals Microsoft Office Communicator) erstellt. Obwohl dieser Ordner von Outlook nicht als Standardordner behandelt wird, wird er von Exchange als spezieller Ordner behandelt, auf den Aufbewahrungsrichtlinientags angewendet werden können.</p></td>
</tr>
<tr class="odd">
<td><p>Gelöschte Elemente</p></td>
<td><p>In diesem Ordner werden Elemente gespeichert, die aus anderen Ordnern im Postfach gelöscht wurden. Benutzer von Outlook und Outlook Web App können diesen Ordner manuell leeren. Sie können Outlook auch derart konfigurieren, dass der Ordner beim Schließen von Outlook geleert wird.</p></td>
</tr>
<tr class="even">
<td><p>Entwürfe</p></td>
<td><p>In diesem Ordner werden Nachrichtenentwürfe gespeichert, die vom Benutzer noch nicht gesendet wurden. In Outlook Web App wird dieser Ordner auch zum Speichern von Nachrichten verwendet, die vom Benutzer gesendet, aber noch nicht an den Hub-Transport-Server übermittelt wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Posteingang</p></td>
<td><p>In diesem Standardordner werden Nachrichten gespeichert, die an ein Postfach zugestellt wurden.</p></td>
</tr>
<tr class="even">
<td><p>Journal</p></td>
<td><p>Dieser Standardordner enthält vom Benutzer ausgewählte Aktionen. Diese Aktionen werden automatisch von Outlook aufgezeichnet und in einer Zeitachsenansicht angezeigt.</p></td>
</tr>
<tr class="odd">
<td><p>Junk-E-Mail</p></td>
<td><p>In diesem Standardordner werden Nachrichten gespeichert, die vom Inhaltsfilter auf einem Exchange-Server oder vom Antispamfilter in Outlook als Junk-E-Mails gekennzeichnet wurden.</p></td>
</tr>
<tr class="even">
<td><p>Notizen</p></td>
<td><p>In diesem Ordner werden die von Benutzern in Outlook erstellten Notizen gespeichert. Diese Notizen werden auch in Outlook Web App angezeigt.</p></td>
</tr>
<tr class="odd">
<td><p>Postausgang</p></td>
<td><p>In diesem Standardordner werden vom Benutzer gesendete Nachrichten temporär gespeichert, bis diese an einen Hub-Transport-Server übermittelt werden. Eine Kopie der gesendeten Nachrichten wird im Standardordner &quot;Gesendete Elemente&quot; gespeichert. Da die Nachrichten nur für kurze Zeit in diesem Ordner verbleiben, ist es nicht erforderlich, ein Aufbewahrungsrichtlinientag für diesen Ordner zu erstellen.</p></td>
</tr>
<tr class="even">
<td><p>RSS-Feeds</p></td>
<td><p>In diesem Standardordner sind die RSS-Feeds enthalten.</p></td>
</tr>
<tr class="odd">
<td><p>Wiederherstellbare Elemente</p></td>
<td><p>Hierbei handelt es sich um einen versteckten Ordner in der Nicht-IPM-Unterstruktur. Er enthält die Unterordner „Löschvorgänge“, „Versionen“, „Endgültige Löschvorgänge“, „In-Situ-Speicher“ und „Überwachungen“. Durch Aufbewahrungstags für diesen Ordner werden Elemente aus dem Ordner „Wiederherstellbare Elemente“ im primären Postfach des Benutzers in den Ordner „Wiederherstellbare Elemente“ im Archivpostfach des Benutzers verschoben. Sie können den Tags für diesen Ordner nur die Aufbewahrungsaktion <strong>In Archiv verschieben</strong> zuweisen. Weitere Informationen finden Sie unter <a href="recoverable-items-folder-exchange-2013-help.md">Ordner &quot;Wiederherstellbare Elemente&quot;</a>.</p></td>
</tr>
<tr class="even">
<td><p>Gesendete Elemente</p></td>
<td><p>In diesem Standardordner werden Nachrichten gespeichert, die an einen Hub-Transport-Server übermittelt wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Synchronisierungsprobleme</p></td>
<td><p>Dieser Ordner enthält Synchronisierungsprotokolle. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=198215">Ordner für Synchronisierungsprobleme</a>.</p></td>
</tr>
<tr class="even">
<td><p>Aufgaben</p></td>
<td><p>Dieser Standardordner wird verwendet, um Aufgaben zu speichern. Zum Erstellen einer Aufbewahrungsrichtlinie für den Ordner „Aufgaben“ müssen Sie Exchange-Verwaltungsshell verwenden. Weitere Informationen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/dd335226(v=exchg.150)">New-RetentionPolicyTag</a>. Nachdem Sie die Aufbewahrungsrichtlinie für den Ordner „Aufgaben“ erstellt haben, können Sie diese mithilfe des Exchange Admin Center verwalten.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

  - RPTs sind Aufbewahrungstags für Standardordner. Sie können für RPTs nur eine Löschaktion auswählen – either **Löschen und Wiederherstellung zulassen** oder **Permanent löschen**.

  - Sie können kein RPT erstellen, um Nachrichten in das Archiv zu verschieben. Um alte Elemente in das Archiv zu verschieben, können Sie ein *Standardrichtlinientag* (Default Policy Tag, DPT) erstellen, das für das gesamte Postfach gilt, oder *Persönliche Tags* erstellen, die in Outlook und Outlook Web App (OWA) als Archivrichtlinien angezeigt werden. Die Benutzer können sie auf Ordner oder einzelne Nachrichten anwenden.

  - Sie können Aufbewahrungsrichtlinientags nicht auf den Ordner "Kontakte" anwenden.

  - Sie können nur ein RPT für einen bestimmten Standardordner zu einer Aufbewahrungsrichtlinie hinzufügen. Wenn eine Aufbewahrungsrichtlinie beispielsweise über ein Tag für den Posteingang verfügt, können Sie ihr kein weiteres Aufbewahrungsrichtlinientag vom Typ "Posteingang" hinzufügen.

  - Informationen dazu, wie Sie RPTs oder andere Arten von Aufbewahrungstags erstellen und sie zu einer Aufbewahrungsrichtlinie hinzufügen, finden Sie unter [Erstellen einer Aufbewahrungsrichtlinie](https://technet.microsoft.com/de-de/library/JJ150573(v=EXCHG.150)).

  - In Exchange 2013 und Exchange Online gilt ein Standardrichtlinientag auch für die Standardordner **Kalender** und **Aufgaben**. Dies kann dazu führen, dass Elemente basierend auf den Einstellungen für das Standardrichtlinientag gelöscht oder ins Archiv verschoben werden. Damit die Einstellungen für das Standardrichtlinientag keine Elemente aus diesen Ordnern löschen, müssen Sie Aufbewahrungsrichtlinientags mit deaktivierter Aufbewahrung erstellen. Damit die Einstellungen für das Standardrichtlinientag keine Elemente aus einem Standardordner verschieben, können Sie mit der Aktion "In Archiv verschieben" ein deaktiviertes persönliches Tag erstellen, es zur Aufbewahrungsrichtlinie hinzufügen und Ihre Benutzer anweisen, es auf den betreffenden Standardordner anzuwenden. Details hierzu finden Sie im englischsprachigen Artikel [Prevent archiving of items in a default folder in Exchange 2010](https://go.microsoft.com/fwlink/?linkid=511071).

