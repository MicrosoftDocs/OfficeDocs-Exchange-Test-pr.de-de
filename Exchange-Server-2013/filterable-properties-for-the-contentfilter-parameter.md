---
title: 'Filterbare Eigenschaften für Parameter „-ContentFilter“: Exchange 2013 Help'
TOCTitle: Filterbare Eigenschaften für den Parameter „-ContentFilter“
ms:assetid: cf504a59-1938-489c-bb48-b27b2ac3234e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff601762(v=EXCHG.150)
ms:contentKeyID: 50554911
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Filterbare Eigenschaften für den Parameter „-ContentFilter\&quot;

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-09-10_

In diesem Thema werden die filterbaren Eigenschaften für den Parameter *ContentFilter* beschrieben. Der Parameter *ContentFilter* wird zum Exportieren von Nachrichten in eine PST-Datei verwendet, die mit den Filtereinstellungen übereinstimmen. Der Parameter *ContentFilter* wird im Cmdlet [New-MailboxExportRequest](https://technet.microsoft.com/de-de/library/ff607299\(v=exchg.150\)) verwendet.

## Filterbare Eigenschaften

Die meisten Eigenschaften für den Parameter *ContentFilter* akzeptieren Platzhalterzeichen. Bei Verwendung eines Platzhalterzeichens müssen Sie den Operator **-like** anstelle des Operators **-eq** verwenden. Der Operator **-like** wird zum Suchen nach Musterübereinstimmungen in Rich-Typen (z. B. Zeichenfolgen) verwendet, während der Operator **-eq** zum Suchen nach einer genauen Übereinstimmung verwendet wird.

Die folgende Tabelle zeigt eine Liste der filterbaren Eigenschaften für den Parameter *ContentFilter*. In dieser Tabelle werden der Name der Eigenschaft, eine Beschreibung, die akzeptablen Werte sowie ein Syntaxbeispiel aufgeführt. Weitere Informationen zu OPATH-Filtern finden Sie unter [Filter in Shell-Empfängerbefehlen](https://technet.microsoft.com/de-de/library/bb124268\(v=exchg.150\)).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Beschreibung</th>
<th>Werte</th>
<th>Beispielsyntax</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>All</p></td>
<td><p>Diese Eigenschaft gibt sämtliche Nachrichten mit einer bestimmten Zeichenfolge in einer indizierten Eigenschaft zurück. Verwenden Sie diese Eigenschaft z. B. zum Exportieren aller Nachrichten mit dem Namen &quot;Ayla&quot; als Empfänger, Absender oder im Nachrichtentext.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {All -like &#39;*Ayla*&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Attachment</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit der angegebenen Zeichenfolge im Inhalt einer Anlage oder im Dateinamen der Anlage zurück.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {Attachment -like &#39;*.jpg&#39;}</code></pre></td>
</tr>
<tr class="odd">
<td><p>BCC</p></td>
<td><p>Diese Eigenschaft gibt gesendete Nachrichten mit dem angegebenen Empfänger im Feld Bcc zurück.</p></td>
<td><p>Anzeigename</p>
<p>Alias</p>
<p>SMTP-Adresse</p>
<p>LegacyDN</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {(BCC -eq &#39;ayla@contoso.com&#39;) -or (BCC -eq &#39;tony@contoso.com&#39;)}</code></pre></td>
</tr>
<tr class="even">
<td><p>Body</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit der angegebenen Zeichenfolge im Nachrichtentext zurück.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {Body -like &#39;*prospectus*&#39;}</code></pre></td>
</tr>
<tr class="odd">
<td><p>Category</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit einer übereinstimmenden Kategorie zurück. Kategorien werden durch Benutzer oder Postfachregeln festgelegt.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {Category -like &#39;*Blue*&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>CC</p></td>
<td><p>Diese Eigenschaft gibt gesendete Nachrichten mit dem angegebenen Empfänger im Feld Cc zurück.</p></td>
<td><p>Anzeigename</p>
<p>Alias</p>
<p>SMTP-Adresse</p>
<p>LegacyDN</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {(CC -eq &#39;ayla@contoso.com&#39;) -or (CC -eq &#39;tony@contoso.com&#39;)}</code></pre></td>
</tr>
<tr class="odd">
<td><p>Expires</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit einem Zeitstempel für den Ablauf zurück.</p></td>
<td><p>Datums-/Uhrzeitstempel</p></td>
<td><pre><code>-ContentFilter {Expires -lt &#39;01/01/2013&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>HasAttachment</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit oder ohne Anlagen zurück.</p></td>
<td><p>Boolescher Wert</p>
<p><code>$true</code> oder  <code>$false</code></p></td>
<td><pre><code>-ContentFilter {HasAttachment -eq $true}</code></pre></td>
</tr>
<tr class="odd">
<td><p>Importance</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit einer angegebenen Wichtigkeitsstufe zurück.</p></td>
<td><p>0 oder &quot;Niedrig&quot;</p>
<p>1 oder &quot;Normal&quot;</p>
<p>2 oder &quot;Hoch&quot;</p></td>
<td><pre><code>-ContentFilter {Importance -eq &#39;high&#39;}</code></pre>
<pre><code>-ContentFilter {Importance -eq 2}</code></pre></td>
</tr>
<tr class="even">
<td><p>IsFlagged</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten zurück, die von einem Benutzer oder einer Postfachregel gekennzeichnet wurden.</p></td>
<td><p>Boolescher Wert</p>
<p><code>$true</code> oder <code>$false</code></p></td>
<td><pre><code>-ContentFilter {IsFlagged -eq $true}</code></pre></td>
</tr>
<tr class="odd">
<td><p>IsRead</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten zurück, die vom Benutzer gelesen bzw. nicht gelesen wurden.</p></td>
<td><p>Boolescher Wert</p>
<p><code>$true</code> oder <code>$false</code></p></td>
<td><pre><code>-ContentFilter {IsRead -eq $true}</code></pre></td>
</tr>
<tr class="even">
<td><p>MessageKind</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten zurück, die den angegebenen Typ aufweisen.</p></td>
<td><p>Kalender</p>
<p>Kontakt</p>
<p>Dokument</p>
<p>Email</p>
<p>Fax</p>
<p>InstantMessage</p>
<p>Journal</p>
<p>Notiz</p>
<p>Bereitstellen</p>
<p>RSSFeed</p>
<p>Aufgabe</p>
<p>Voicemail</p></td>
<td><pre><code>-ContentFilter {MessageKind -eq &#39;Calendar&#39;}</code></pre>
<pre><code>-ContentFilter {MessageKind -ne &#39;Email&#39;}</code></pre></td>
</tr>
<tr class="odd">
<td><p>MessageLocalee</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten zurück, die das angegebene Gebietsschema aufweisen.</p></td>
<td><p>CultureInfo</p></td>
<td><pre><code>-ContentFilter {MessageLocale -ne &#39;en-US&#39;}</code></pre>
<pre><code>-ContentFilter {MessageLocale -eq &#39;tr-TR&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Participants</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit dem angegebenen Empfänger im Feld An, Bcc oder Cc zurück.</p></td>
<td><p>Anzeigename</p>
<p>Alias</p>
<p>SMTP-Adresse</p>
<p>LegacyDN</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {(Participants -eq &#39;ayla@contoso.com&#39;) -or (Participants -eq &#39;tony@contoso.com&#39;)}</code></pre></td>
</tr>
<tr class="odd">
<td><p>PolicyTag</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit einem Richtlinientag zurück. Im Exchange-Informationsspeicher werden Richtlinientags dauerhaft als GUIDs gespeichert. Daher kann die Zeichenfolge entweder einen expliziten GUID-Wert enthalten, nach dem dann von PR_POLICY_TAG gesucht wird, oder eine Platzhalterzeichenfolge.</p>
<p>Wenn es sich bei dem angegebenen Wert nicht um eine GUID handelt, verwendet der Befehl zum Auflösen der Namen in GUIDs Active Directory-Informationen.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {PolicyTag -ne &#39;00000000-0000-0000-0000-000000000000&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Received</p></td>
<td><p>Diese Eigenschaft gibt empfangene Nachrichten mit dem angegebenen Empfangszeitstempel zurück.</p></td>
<td><p>Datums-/Uhrzeitstempel</p></td>
<td><pre><code>-ContentFilter {Received -lt &#39;01/01/2013 9:00&#39;}</code></pre>
<pre><code>-ContentFilter {(Received -lt &#39;01/01/2013&#39;) -and (Received -gt &#39;01/01/2012&#39;)}</code></pre></td>
</tr>
<tr class="odd">
<td><p>Sender</p></td>
<td><p>Diese Eigenschaften gibt Nachrichten vom angegebenen Absender zurück.</p></td>
<td><p>Anzeigename</p>
<p>Alias</p>
<p>SMTP-Adresse</p>
<p>LegacyDN</p>
<p>Platzhalter</p></td>
<td><pre><code>ContentFilter {Sender -eq &#39;tony&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Sent</p></td>
<td><p>Diese Eigenschaft gibt gesendete Nachrichten mit dem angegebenen Sendezeitstempel zurück.</p></td>
<td><p>Datums-/Uhrzeitstempel</p></td>
<td><pre><code>-ContentFilter {Sent -lt &#39;01/01/2013 9:00&#39;}</code></pre>
<pre><code>-ContentFilter {(Sent -lt &#39;01/01/2013&#39;) -and (Sent -gt &#39;01/01/2012&#39;)}</code></pre></td>
</tr>
<tr class="odd">
<td><p>Size</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit der angegebenen Größe zurück.</p></td>
<td><p>B (Bytes)</p>
<p>KB (Kilobytes)</p>
<p>MB (Megabytes)</p></td>
<td><pre><code>-ContentFilter {Size -gt &#39;10KB&#39;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Subject</p></td>
<td><p>Diese Eigenschaft gibt Nachrichten mit der angegebenen Zeichenfolge im Nachrichtenbetreff zurück.</p></td>
<td><p>Zeichenfolge</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {Subject -like &#39;*meeting*&#39;}</code></pre></td>
</tr>
<tr class="odd">
<td><p>To</p></td>
<td><p>Diese Eigenschaft gibt gesendete Nachrichten mit dem angegebenen Empfänger im Feld An zurück.</p></td>
<td><p>Anzeigename</p>
<p>Alias</p>
<p>SMTP-Adresse</p>
<p>LegacyDN</p>
<p>Platzhalter</p></td>
<td><pre><code>-ContentFilter {To -eq &#39;aylakol&#39;}</code></pre></td>
</tr>
</tbody>
</table>

