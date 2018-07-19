---
title: Technische Übersicht zu Richtlinientipps in Exchange Online und Exchange 2013
TOCTitle: Richtlinientipps
ms:assetid: 4266b83c-dd8a-4b3d-99ff-402e68fc810c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150512(v=EXCHG.150)
ms:contentKeyID: 50474762
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Richtlinientipps

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-22_

Sie können das unangemessene Senden vertraulicher Informationen durch die E-Mail-Benutzer von Microsoft Outlook, Outlook Web App (OWA) und OWA for Devices in Ihrer Organisation verhindern, indem Sie Richtlinien zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) erstellen, die *Richtlinientipp*-Benachrichtigungen enthalten. Ähnlich wie E-Mail-Infos, die in Microsoft Exchange Server 2010 eingeführt wurden, werden Benutzern in Outlook Richtlinientipp-Benachrichtigungen angezeigt, wenn sie eine E-Mail-Nachricht verfassen. Richtlinientipp-Benachrichtigungen werden nur angezeigt, wenn Elemente in der E-Mail-Nachricht des Absenders gegen eine von Ihnen eingerichtete DLP-Richtlinie zu verstoßen scheinen und diese Richtlinie eine Regel umfasst, die den Absender benachrichtigt, wenn die konfigurierten Bedingungen erfüllt sind. Allgemeine Informationen zur Verhinderung von Datenverlust finden Sie unter [Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md).

Um den E-Mail-Absendern Richtlinientipps anzuzeigen, müssen Ihre Regeln die Aktion **Absender mit Richtlinientipp benachrichtigen** umfassen. Sie können diese Aktion im Regel-Editor der Exchange-Verwaltungskonsole hinzufügen. Weitere Informationen finden Sie unter [Richtlinientipps verwalten](how-to-configure-and-manage-policy-tips-a-dlp-feature-exchange.md).

Der Transportregel-Agent, der DLP-Richtlinien erzwingt, unterscheidet bei der Auswertung von Nachrichten und den in Ihren Richtlinien enthaltenen Bedingungen nicht zwischen E-Mail-Anlagen, Nachrichtentext oder Betreffzeile. Beispiel: Ein Benutzer erstellt eine E-Mail-Nachricht, die eine Kreditkartennummer im Nachrichtentext enthält. Anschließend versucht der Benutzer, die Nachricht an einen Empfänger außerhalb der Organisation zu senden. In einem solchen Fall kann dem Benutzer in Outlook oder Outlook Web App eine Richtlinientipp-Benachrichtigung angezeigt werden, in welcher der Benutzer an die in Ihrem Unternehmen geltenden Beschränkungen für die Weitergabe solcher Informationen erinnert wird. Diese Art der Benachrichtigung wird jedoch nur angezeigt, wenn Sie eine DLP-Richtlinie konfiguriert haben, mit der die beschriebenen Beispielhandlungen eingeschränkt werden – in diesem Fall das Hinzufügen eines externen E-Mail-Alias zur Kopfzeile einer Nachricht mit Kreditkarteninformationen. Es gibt zahlreiche verschiedene Bedingungen, Aktionen und Ausnahmen, die Sie beim Erstellen von DLP-Richtlinien auswählen können. Auf diese Weise können Sie die Richtlinien zur Verhinderung von Datenverlust in einer Weise anpassen, die genau auf die Anforderungen Ihres Unternehmens zugeschnitten ist.

Jedes Mal, wenn Sie entweder die Aktion zum Benachrichtigen des Absenders oder eine Außerkraftsetzungsaktion innerhalb einer Regel verwenden, empfiehlt es sich, auch die Bedingung einzuschließen, dass die Nachricht von innerhalb der Organisation gesendet wurde. Hierzu können Sie im Editor für Richtlinienregeln die folgende Bedingung hinzufügen: **Der Absender befindet sich in...** \> **Innerhalb der Organisation**. Weitere Informationen zum Ändern vorhandener DLP-Richtlinien finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md). Diese Empfehlung ist eine bewährte Methode, da die Aktion zum Benachrichtigen des Absenders als Bestandteil der Nachrichtenerstellung in Ihrem Unternehmen angewendet wird. Die Absender, auf welche die Aktion sich bezieht, sind die Verfasser von Nachrichten innerhalb Ihres Unternehmens. Die durch Richtlinientipps dargestellte Benutzerinteraktion kann für eingehende Nachrichten nicht durch Ihre Benutzer beeinflusst werden und wird ignoriert, wenn der Absender sich außerhalb der Organisation befindet. Sie können DLP-Richtlinien anwenden, um eingehende Nachrichten zu scannen und eine Vielzahl von Aktionen einzuleiten. Fügen Sie jedoch in diesem Fall nicht die Aktion zum Benachrichtigen von Absendern hinzu.

Wenn E-Mail-Absender in Ihrer Organisation beim Verfassen einer Nachricht mithilfe von Richtlinientipp-Benachrichtigungen in Echtzeit auf die in Ihrer Organisation geltenden Erwartungen und Standards hingewiesen werden, sind weniger Verstöße gegen Standards zu erwarten, die Ihre Organisation umsetzen möchte.


> [!NOTE]
> <UL>
> <LI>
> <P>Exchange Online: DLP ist ein Premium-Feature, für das ein Abonnement des Typs Exchange Online (Plan 2) erforderlich ist. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=286154">Exchange Online-Lizenzierung</A>.</P>
> <LI>
> <P>Exchange 2013: DLP ist ein Premium-Feature, für das eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) erforderlich ist. Weitere Informationen zu Clientzugriffslizenzen und zur Serverlizenzierung finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</A>.</P>
> <LI>
> <P>Falls in Ihrer Organisation Exchange 2013 SP1 oder Exchange Online verwendet wird, sind Richtlinientipps für Benutzer verfügbar, die E-Mails über Outlook 2013, Outlook Web App oder OWA für Geräte senden. Falls in Ihrer Organisation jedoch derzeit Exchange 2013 verwendet wird, sind Richtlinientipps nur für Benutzer verfügbar, die E-Mails über Outlook 2013 senden.</P></LI></UL>



## Standardtext für Richtlinientipps und Regeloptionen

Sie haben beim Hinzufügen von Regeln für die Absenderbenachrichtigung zu DLP-Richtlinien verschiedene Optionen. Wenn Sie eine Regel zur Absenderbenachrichtigung über die Aktion **Absender mit Richtlinientipp benachrichtigen** einer DLP-Richtlinie hinzufügen, können Sie festlegen, wie restriktiv die Regel sein soll. Die verfügbaren Benachrichtigungsoptionen sind in der folgenden Tabelle aufgeführt. Allgemeine Informationen zum Bearbeiten von Richtlinien finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md). Ausführliche Informationen zum Erstellen von Richtlinientipps finden Sie unter [Richtlinientipps verwalten](how-to-configure-and-manage-policy-tips-a-dlp-feature-exchange.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Benachrichtigungsregel</th>
<th>Bedeutung</th>
<th>Standardtext einer Richtlinientipp-Benachrichtigung, die Benutzern in Outlook angezeigt wird</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Nur benachrichtigen</strong></p></td>
<td><p>Ähnlich wie E-Mail-Infos erzeugt diese Einstellung eine Richtlinientipp-Informationsmeldung zu einer Richtlinienverletzung. Ein Absender kann über ein Optionsdialogfeld zu Richtlinientipps in Outlook die Anzeige dieser Art von Tipps verhindern.</p></td>
<td><p>Diese Nachricht enthält möglicherweise vertrauliche Inhalte. Alle Empfänger müssen autorisiert sein, diese Inhalte zu empfangen.</p></td>
</tr>
<tr class="even">
<td><p><strong>Nachricht zurückweisen</strong></p></td>
<td><p>Die Nachricht wird erst zugestellt, wenn die Bedingung nicht länger erfüllt ist. Der Absender kann über eine bereitgestellte Option angeben, dass die E-Mail-Nachricht keine vertraulichen Inhalte umfasst. Dies wird auch als Außerkraftsetzung eines falsch positiven Ergebnisses bezeichnet. Wenn der Benutzer dies angibt, lässt Outlook es zu, dass die Nachricht den Postausgang verlässt, damit der Benutzerbericht überprüft werden kann, Exchange verhindert jedoch, dass die Nachricht gesendet wird.</p></td>
<td><p>Diese Nachricht enthält möglicherweise vertrauliche Inhalte. Ihre Organisation lässt das Senden dieser Nachricht erst zu, wenn dieser Inhalt entfernt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Zurückweisen, sofern keine Außerkraftsetzung als falsch positiv vorliegt</strong></p></td>
<td><p>Das Ergebnis dieser Benachrichtigungsregel ähnelt dem der Benachrichtigungsregel <strong>Nachricht zurückweisen</strong>. Wenn Sie jedoch diese Option auswählen, lässt Exchange das Senden der Nachricht an den beabsichtigten Empfänger zu, statt die Nachricht zu blockieren.</p></td>
<td><p><strong>Bevor der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Diese Nachricht enthält möglicherweise vertrauliche Inhalte. Ihre Organisation lässt das Senden dieser Nachricht erst zu, wenn dieser Inhalt entfernt wurde.</p>
<p><strong>Nachdem der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Ihr Feedback wird beim Senden der Nachricht an den Administrator gesendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>Zurückweisen, sofern keine implizite Außerkraftsetzung vorliegt</strong></p></td>
<td><p>Die Nachricht wird erst zugestellt, wenn die Bedingung nicht länger erfüllt ist oder der Absender eine Außerkraftsetzung auswählt. Dem Absender wird eine Option angezeigt, die das Außerkraftsetzen der Richtlinie ermöglicht.</p></td>
<td><p><strong>Bevor der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Diese Nachricht enthält möglicherweise vertrauliche Inhalte. Ihre Organisation lässt das Senden dieser Nachricht erst zu, wenn dieser Inhalt entfernt wurde.</p>
<p><strong>Nachdem der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Sie haben die Richtlinie Ihrer Organisation für vertrauliche Inhalte in dieser Nachricht außer Kraft gesetzt. Die Aktion wird von Ihrer Organisation überwacht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Ablehnen, sofern keine explizite Außerkraftsetzung vorliegt</strong></p></td>
<td><p>Das Ergebnis dieser Benachrichtigungsregel ähnelt dem der Benachrichtigungsregel <strong>Zurückweisen, sofern keine implizite Außerkraftsetzung vorliegt</strong>, in diesem Fall müssen die Absender jedoch eine Begründung für die Richtlinienaußerkraftsetzung angeben.</p></td>
<td><p><strong>Bevor der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Diese Nachricht enthält möglicherweise vertrauliche Inhalte. Ihre Organisation lässt das Senden dieser Nachricht erst zu, wenn dieser Inhalt entfernt wurde.</p>
<p><strong>Nachdem der Absender eine Option für die Außerkraftsetzung auswählt:</strong> Sie haben die Richtlinie Ihrer Organisation für vertrauliche Inhalte in dieser Nachricht außer Kraft gesetzt. Die Aktion wird von Ihrer Organisation überwacht.</p></td>
</tr>
</tbody>
</table>


## Anpassen der Richtlinientipp-Benachrichtigungen

Wählen Sie zum Anpassen des Texts einer Richtlinientipp-Benachrichtigung, die E-Mail-Absender in ihrem E-Mail-Programm sehen, auf der Seite „Verhinderung von Datenverlust“ die Option **Richtlinientipps verwalten** aus. Damit Ihr benutzerdefinierter Text angezeigt wird, muss eine DLP-Richtlinie die Aktion **Absender mit Richtlinientipp benachrichtigen** enthalten. Fügen Sie die Aktion mithilfe des DLP-Regel-Editors einer Regel hinzu.

Verfahren zur Erläuterung der Erstellung eigener Richtlinientipps finden Sie unter [Richtlinientipps verwalten](how-to-configure-and-manage-policy-tips-a-dlp-feature-exchange.md). Der benutzerdefinierte Text, den Sie erstellen, kann den in der vorherigen Tabelle gezeigten Standardtext ersetzen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktionen und Einstellungen für Richtlinientipp-Benachrichtigungen</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Absender benachrichtigen</strong></p></td>
<td><p>Der Text wird nur angezeigt, wenn eine Aktion <strong>Absender benachrichtigen, aber Senden zulassen</strong> initiiert wird.</p></td>
</tr>
<tr class="even">
<td><p><strong>Außerkraftsetzen durch Absender zulassen</strong></p></td>
<td><p>Der Text wird nur angezeigt, wenn folgende Aktionen initiiert werden: <strong>Nachricht blockieren, wenn es sich nicht um ein falsch positives Ergebnis handelt</strong>, <strong>Nachricht blockieren, aber Außerkraftsetzen und Senden durch Absender zulassen</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nachricht blockieren</strong></p></td>
<td><p>Dieser Text wird nur angezeigt, wenn eine Aktion <strong>Nachricht blockieren</strong> initiiert wird.</p></td>
</tr>
<tr class="even">
<td><p><strong>Link zur URL zur Richtlinientreue</strong></p></td>
<td><p>Die Compliance-URL ist ein Link zu einer Webseite, auf der Sie Ihre Compliance- und Außerkraftsetzungsrichtlinien erklären können. Dieser Link wird im Richtlinientipp angezeigt, wenn ein Benutzer klickt auf den Link <strong>Weitere Details</strong> klickt.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md)

[Richtlinientipps verwalten](how-to-configure-and-manage-policy-tips-a-dlp-feature-exchange.md)

