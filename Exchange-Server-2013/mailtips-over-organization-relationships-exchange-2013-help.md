---
title: 'E-Mail-Infos über Organisationsbeziehungen: Exchange 2013 Help'
TOCTitle: E-Mail-Infos über Organisationsbeziehungen
ms:assetid: 1784256f-abe1-4503-b8c4-26d544b73452
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ670165(v=EXCHG.150)
ms:contentKeyID: 50475172
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# E-Mail-Infos über Organisationsbeziehungen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

In Microsoft Exchange Server 2013 können Organisationsbeziehungen mit Microsoft Exchange Online oder anderen Exchange-Organisationen konfiguriert werden. Wenn Sie eine Organisationsbeziehung einrichten, können Sie die Benutzerfreundlichkeit bei der Interaktion mit anderen Organisationen verbessern. Beispielsweise können Sie Frei/Gebucht-Daten freigeben, einen sicheren Nachrichtenfluss konfigurieren und die Nachrichtenverfolgung innerhalb beider Organisationen aktivieren.

## Steuern der Zugriffsebene für E-Mail-Infos

Es kann sinnvoll sein, für bestimmte Arten von E-Mail-Infos Einschränkungen festzulegen. Sie können entweder zulassen, dass alle E-Mail-Infos zurückgegeben werden, oder nur eine begrenzte Menge von E-Mail-Infos zulassen, die Unzustellbarkeitsberichte verhindern würden. Sie können diese Einstellung mit dem Parameter *MailTipsAccessLevel* des Cmdlets **Set-OrganizationRelationship** konfigurieren. Die folgende Tabelle zeigt, welche E-Mail-Infos über die Organisationsbeziehung zurückgegeben werden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>E-Mail-Info</th>
<th>Ist die E-Mail-Info verfügbar, wenn für die Zugriffsebene &quot;All&quot; festgelegt ist?</th>
<th>Ist die E-Mail-Info verfügbar, wenn für die Zugriffsebene &quot;Limited&quot; festgelegt ist?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Große Benutzergruppe</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Automatische Antworten</p></td>
<td><p>Ja</p>
<p>Wenn die Remotedomäne des Empfängers als intern festgelegt ist, wird die interne automatische Antwort angezeigt. Andernfalls wird die externe automatische Antwort angezeigt.</p></td>
<td><p>Ja</p>
<p>Die externe automatische Antwort wird angezeigt.</p></td>
</tr>
<tr class="odd">
<td><p>Moderierter Empfänger</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Übergroße Nachricht</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Eingeschränkter Empfänger</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Postfach voll</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Benutzerdefinierte E-Mail-Infos</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Externe Empfänger</p></td>
<td><p>Ja</p>
<p>Wenn die Remotedomäne des Empfängers als intern festgelegt ist, wird diese E-Mail-Info unterdrückt. Andernfalls wird die externe E-Mail-Info zurückgegeben.</p></td>
<td><p>Ja</p>
<p>Wenn die Remotedomäne des Empfängers als intern festgelegt ist, wird diese E-Mail-Info unterdrückt. Andernfalls wird die externe E-Mail-Info zurückgegeben.</p></td>
</tr>
</tbody>
</table>


Genaue Anweisungen zum Konfigurieren von Zugriffsebenen für E-Mail-Infos finden Sie unter [Verwalten von E-Mail-Infos für Organisationsbeziehungen](manage-mailtips-for-organization-relationships-exchange-2013-help.md).

## Steuern des Zugriffsbereichs für E-Mail-Infos

Wenn Sie E-Mail-Infos über eine Organisationsbeziehung aktivieren und die Zugriffsebene auf `All` festlegen, werden für alle Benutzer die empfängerspezifischen E-Mail-Infos, E-Mail-Infos zu vollem Postfach, zu automatischen Antworten und benutzerdefinierten E-Mail-Infos zurückgegeben. Möglicherweise sollten Sie diese E-Mail-Infos jedoch nur für bestimmte Benutzer zulassen. Wenn Sie beispielsweise eine Organisationsbeziehung mit einem Partner einrichten, sollten Sie diese E-Mail-Infos möglicherweise nur für die Benutzer zulassen, die mit diesem Partner zusammenarbeiten.

Um dies zu erreichen, müssen Sie zuerst eine Gruppe erstellen und ihr alle Benutzer hinzufügen, denen Sie empfängerspezifische E-Mail-Infos an diese Gruppe senden möchten. Sie können diese Gruppe dann für die Organisationsbeziehung angeben.

Nachdem Sie diese Einschränkung implementiert haben, überprüfen Ihre Clientzugriffsserver zuerst, ob der Empfänger, für den sie eine E-Mail-Info-Abfrage erhalten haben, Mitglied dieser Gruppe ist. Wenn der Empfänger Mitglied dieser Gruppe ist, senden die Clientzugriffsserver als Proxys alle E-Mail-Infos zurück, einschließlich der empfängerspezifischen E-Mail-Infos. Andernfalls werden die empfängerspezifischen E-Mail-Infos nicht in die Antwort eingeschlossen.

Genaue Anweisungen zum Konfigurieren von Zugriffsebenen für E-Mail-Infos finden Sie unter [Verwalten von E-Mail-Infos für Organisationsbeziehungen](manage-mailtips-for-organization-relationships-exchange-2013-help.md).

