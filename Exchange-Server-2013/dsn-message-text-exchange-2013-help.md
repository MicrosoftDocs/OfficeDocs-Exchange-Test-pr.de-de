---
title: 'DSN-Nachrichtentext: Exchange 2013 Help'
TOCTitle: DSN-Nachrichtentext
ms:assetid: eae4a050-5ecb-4c87-b377-74edb93a5995
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125135(v=EXCHG.150)
ms:contentKeyID: 50477012
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DSN-Nachrichtentext

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie können Text zu einer benutzerdefinierten DSN-Nachricht (Delivery Status Notification, Benachrichtigung über den Zustellungsstatus) in Microsoft Exchange Server 2013 hinzufügen, und Sie können diesen Text in HTML formatieren.

Sie können beliebige Informationen hinzufügen, die Sie dem Empfänger der DSN-Nachricht anzeigen möchten. Sie können beispielsweise eine detaillierte DSN-Beschreibung, Helpdesk-Kontaktinformationen und einen Link zur Website des Supports Ihrer Abteilung hinzufügen. Eine DSN-Nachricht kann maximal 512 Zeichen enthalten.

Da DSN-Nachrichten als HTML angezeigt werden können, ist es möglich, HTML-Formatierungstags in den DSN-Nachrichtentext einzubetten. Wenn Sie beispielsweise bestimmten Text in Ihren DSN-Nachrichten fett anzeigen möchten, umgeben Sie den Text mit den HTML-Tags \<B\> und \</B\>. Die folgende Tabelle enthält Beispiele gültiger HTML-Tags, die Sie im DSN-Nachrichtentext verwenden können.

### Gültige HTML-Tags in DSN-Nachrichten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>HTML-Tag</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;B&gt;</p></td>
<td><p>Anfang der Fettformatierung</p></td>
</tr>
<tr class="even">
<td><p>&lt;/B&gt;</p></td>
<td><p>Ende der Fettformatierung</p></td>
</tr>
<tr class="odd">
<td><p>&lt;A HREF=&quot;url&quot;&gt;</p></td>
<td><p>Anfang des Links</p></td>
</tr>
<tr class="even">
<td><p>&lt;/A&gt;</p></td>
<td><p>Ende des Links</p></td>
</tr>
<tr class="odd">
<td><p>&lt;BR&gt;</p></td>
<td><p>Linkumbruch</p></td>
</tr>
<tr class="even">
<td><p>&lt;EM&gt;</p></td>
<td><p>Anfang der Kursivformatierung</p></td>
</tr>
<tr class="odd">
<td><p>&lt;/EM&gt;</p></td>
<td><p>Ende der Kursivformatierung</p></td>
</tr>
<tr class="even">
<td><p>&lt;P&gt;</p></td>
<td><p>Absatzanfang</p></td>
</tr>
<tr class="odd">
<td><p>&lt;/P&gt;</p></td>
<td><p>Absatzende</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Exchange sendet standardmäßig HTML-DSN-Nachrichten. Sie können jedoch konfigurieren, ob Exchange HTML-DSN-Nachrichten an interne Absender, externe Absender oder beide Absendertypen senden soll. Um dieses Verhalten zu konfigurieren, ändern Sie die Parameter <EM>InternalDsnSendHtml</EM> und <EM>ExternalDsnSendHtml</EM> mit dem Befehl <STRONG>Set-TransportService</STRONG>.<BR>Wenn der Parameter <EM>InternalDsnSendHtml</EM> auf <CODE>$false</CODE> festgelegt ist, unterdrückt Exchange HTML-Tags in DSN-Nachrichten, die an interne Absender gesendet werden. Wenn der Parameter <EM>ExternalDsnSendHtml</EM> auf <CODE>$false</CODE> festgelegt ist, unterdrückt Exchange HTML-Tags in DSN-Nachrichten, die an externe Absender gesendet werden.



Die folgenden Zeichen, die Exchange im DSN-Nachrichtentext verwendet, haben eine besondere Bedeutung:

  - Größer als-Zeichen (\>)

  - Kleiner als-Zeichen (\<)

  - Kaufmännisches Und (&)

  - Anführungszeichen (")

Mithilfe dieser Zeichen wird bestimmt, wo HTML-Tags anfangen und enden und wo Text, der Absendern angezeigt werden soll, anfängt und endet. Wenn Sie diese Zeichen in DSN-Nachrichten anzeigen möchten, müssen Sie die in der folgenden Tabelle enthaltenen Escapecodes verwenden.

Beispiel: Wenn Sie die Nachricht `"Please contact the Help Desk at <1234>."` anzeigen möchten, müssen Sie dem DSN-Nachrichtentext `"Please contact the Help Desk at &lt;1234&gt;." ` hinzufügen.

### Escapecodes für Zeichen in DSN-Nachrichten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Escapecode</th>
<th>Zeichen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&amp;lt;</p></td>
<td><p>&lt;</p></td>
</tr>
<tr class="even">
<td><p>&amp;gt;</p></td>
<td><p>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&amp;quot;</p></td>
<td><p>&quot;</p></td>
</tr>
<tr class="even">
<td><p>&amp;amp;</p></td>
<td><p>&amp;</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> Wenn Sie Ihrem DSN-Nachrichtentext ein HTML-Tag hinzufügen möchten, das Anführungszeichen (") enthält, wie z.&nbsp;B. <CODE>&lt;A HREF="url"&gt;</CODE>, müssen Sie den gesamten DSN-Nachrichtentext in einfache Anführungszeichen (') einschließen. Wenn Sie den gesamten DSN-Nachrichtentext und ein HTML-Tag in doppelte Anführungszeichen einschließen, wird eine Fehlermeldung angezeigt.


