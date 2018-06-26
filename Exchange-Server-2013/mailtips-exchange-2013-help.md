---
title: 'MailTips: Exchange 2013 Help'
TOCTitle: MailTips
ms:assetid: 9c989167-cc0c-40a6-82ba-383f573bd2d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649091(v=EXCHG.150)
ms:contentKeyID: 50476308
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# MailTips

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-04-28_

Bei E-Mail-Infos handelt es sich um informative Meldungen, die Benutzern beim Erstellen einer Nachricht angezeigt werden. Microsoft Exchange Server 2013 analysiert die Nachricht, einschließlich der Liste der Empfänger, an die sie gerichtet ist. Wird ein potenzielles Problem erkannt, wird der Benutzer vor dem Senden der Nachricht mithilfe von E-Mail-Infos benachrichtigt. Mithilfe der durch E-Mail-Infos bereitgestellten Informationen können Absender die verfasste Nachricht korrigieren, um unerwünschte Situationen oder Unzustellbarkeitsberichte (Non-Delivery Reports, NDRs) zu vermeiden.

## Funktionsweise von E-Mail-Infos

E-Mail-Infos werden als Webdienst in Exchange 2013 implementiert. Wenn ein Absender eine Nachricht erstellt, richtet die Clientsoftware einen Exchange-Webdienstaufruf an den Clientzugriffsserver, um die Liste der E-Mail-Infos abzurufen. Der Server gibt die Liste der E-Mail-Infos zurück, die für die jeweilige Nachricht gelten, und die Clientsoftware zeigt dem Absender die E-Mail-Infos an.

Die folgenden unproduktiven Messagingszenarien treten in allen Messagingumgebungen häufig auf:

  - Unzustellbarkeitsberichte aufgrund von Nachrichten, die in einer Organisation konfigurierte Einschränkungen verletzen, z. B. Einschränkungen der Nachrichtengröße oder der maximalen Anzahl von Empfängern pro Nachricht.

  - Unzustellbarkeitsberichte aufgrund von Nachrichten an Empfänger, die nicht vorhanden sind, für die Einschränkungen gelten oder deren Benutzerpostfächer voll sind.

  - Senden von Nachrichten an Benutzer, für die automatische Antworten konfiguriert sind.

In allen diesen Szenarien sendet der Benutzer eine Nachricht, erwartet ihre Zustellung und erhält stattdessen eine Antwort, die besagt, dass die Nachricht nicht zugestellt wurde. Sogar im Best-Case-Szenario, wie bei der automatischen Antwort, führen diese Ereignisse zu Produktivitätsverlusten. Im Fall eines Unzustellbarkeitsberichts kann es zu einem teuren Anruf beim Helpdesk kommen.

Des Weiteren gibt es mehrere Szenarien, in denen das Senden einer Nachricht nicht zu einem Fehler führt, aber unerwünschte und sogar peinliche Konsequenzen haben kann:

  - An extrem große Verteilergruppen gesendete Nachrichten.

  - An ungeeignete Verteilergruppen gesendete Nachrichten.

  - Versehentlich an Empfänger außerhalb Ihrer Organisation gesendete Nachrichten.

  - Auswählen von **Allen antworten** für eine Nachricht, bei der Sie Bcc-Empfänger waren.

Alle diese problematischen Szenarien können vermieden werden, indem die Benutzer über die möglichen Konsequenzen des Sendens der Nachricht informiert werden, während sie sie verfassen. Wenn Absender beispielsweise wissen, dass die Größe der zu sendenden Nachricht die Vorgaben der Unternehmensrichtlinie übersteigt, versuchen sie nicht, sie zu senden. Wenn Absender benachrichtigt werden, dass die zu sendende Nachricht an Personen außerhalb der Organisation zugestellt wird, stellen sie eher sicher, dass der Inhalt und der Tonfall der Nachricht geeignet sind.

Die folgenden Messagingclients unterstützen E-Mail-Infos:

  - Outlook Web App

  - Microsoft Outlook 2010 oder höher

## E-Mail-Infos in Exchange

Die folgende Tabelle listet die verfügbaren E-Mail-Infos in Exchange 2013 auf.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>E-Mail-Info</th>
<th>Verfügbarkeit</th>
<th>Szenario</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ungültiger interner Empfänger</p></td>
<td><p>Outlook</p></td>
<td><p>Die E-Mail-Info zu einem ungültigen internen Empfänger wird angezeigt, wenn der Absender einen organisationsinternen Empfänger hinzufügt, der jedoch nicht vorhanden ist.</p>
<p>Dieser Fall kann eintreten, wenn der Absender eine Nachricht an einen Benutzer richtet, der nicht mehr Mitglied des Unternehmens ist, dessen Adresse jedoch über den Namensauflösungs-Cache oder über einen Eintrag im Kontaktordner des Absenders aufgelöst wird. Oder wenn der Absender eine SMTP-Adresse mit einer Domäne eingibt, für die Exchange autoritativ ist, und die Adresse nicht in einen vorhandenen Absender aufgelöst wird.</p>
<p>Die E-Mail-Info zeigt den ungültigen Empfänger an und ermöglicht es dem Absender, den Empfänger aus der Nachricht zu entfernen.</p></td>
</tr>
<tr class="even">
<td><p>Postfach voll</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info zu einem vollen Postfach wird angezeigt, wenn der Absender einen Empfänger hinzufügt, dessen Postfach voll ist, und Ihre Organisation eine Richtlinie implementiert hat, mit der verhindert wird, dass Postfächer über einer angegebenen Größe Nachrichten empfangen.</p>
<p>Die E-Mail-Info zeigt den Empfänger an, dessen Postfach voll ist, und ermöglicht es dem Absender, den Empfänger aus der Nachricht zu entfernen.</p>
<p>Die E-Mail-Info ist zu dem Zeitpunkt, zu dem sie angezeigt wird, aktuell. Wenn die Nachricht nicht sofort gesendet wird, wird die E-Mail-Info alle zwei Stunden aktualisiert. Dies gilt auch für Nachrichten, die im Ordner &quot;Entwürfe&quot; gespeichert und nach zwei Stunden erneut geöffnet werden.</p></td>
</tr>
<tr class="odd">
<td><p>Automatische Antworten</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info für automatische Antworten wird angezeigt, wenn der Absender einen Empfänger hinzufügt, der automatische Antworten aktiviert hat.</p>
<p>Die E-Mail-Info gibt an, dass der Empfänger &quot;Automatische Antworten&quot; aktiviert hat, und zeigt auch die ersten 175 Zeichen der vom Empfänger konfigurierten automatischen Antwort.</p>
<p>Die E-Mail-Info ist zu dem Zeitpunkt, zu dem sie angezeigt wird, aktuell. Wenn die Nachricht nicht sofort gesendet wird, wird die E-Mail-Info alle zwei Stunden aktualisiert. Dies gilt auch für Nachrichten, die im Ordner &quot;Entwürfe&quot; gespeichert und nach zwei Stunden erneut geöffnet werden.</p>
<p>Wenn ein Teil Ihrer Benutzerpostfächer in Exchange Online gehostet wird und Sie die Koexistenz mit Exchange Online eingerichtet haben, hat die Einstellung für das Remotedomänenobjekt, das den Remotebereich Ihrer Organisation darstellt, direkte Auswirkungen auf die Verarbeitung dieser E-Mail-Info.</p>
<p>In Exchange 2013 können Benutzer unterschiedliche automatische Antworten für interne und externe Absender konfigurieren. Wenn die Remotedomäne als interne Domäne konfiguriert ist (der Parameter <em>IsInternal</em> des Remotedomänenobjekts ist auf <code>$true</code> festgelegt), wird die interne automatische Antwort an alle Benutzer in der Organisation unabhängig vom Standort ihres Postfachs zurückgegeben. Wenn die Remotedomäne nicht als interne Domäne konfiguriert ist, wird die interne automatische Antwort an alle Benutzer zurückgegeben, deren Postfächer sich in der lokalen Domäne befinden, und die externe automatische Antwort wird an die Benutzer zurückgegeben, deren Postfächer sich in der Remotedomäne befinden.</p></td>
</tr>
<tr class="even">
<td><p>Benutzerdefiniert</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Eine benutzerdefinierte E-Mail-Info wird angezeigt, wenn der Absender einen Empfänger hinzufügt, für den eine benutzerdefinierte E-Mail-Info konfiguriert ist.</p>
<p>Eine benutzerdefinierte E-Mail-Info kann hilfreich sein, um spezielle Informationen zu einem Empfänger bereitzustellen. Beispielsweise können Sie eine benutzerdefinierte E-Mail-Info für eine Verteilergruppe erstellen, in der Sie den Zweck der Verteilergruppe erläutern, damit sie seltener falsch verwendet wird. Weitere Informationen finden Sie unter <a href="configure-custom-mailtips-for-recipients-exchange-2013-help.md">Konfigurieren benutzerdefinierter E-Mail-Infos für Empfänger</a>.</p>
<p>Standardmäßig werden benutzerdefinierte E-Mail-Infos nicht angezeigt, wenn der Absender keine Nachrichten an diesen Empfänger senden darf. In diesem Fall wird die E-Mail-Info für eingeschränkte Empfänger angezeigt. Sie können diese Konfiguration jedoch ändern und auch die benutzerdefinierte E-Mail-Info anzeigen.</p></td>
</tr>
<tr class="odd">
<td><p>Eingeschränkter Empfänger</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info für eingeschränkte Empfänger wird angezeigt, wenn der Absender einen Empfänger hinzufügt, für den Zustellungseinschränkungen konfiguriert sind, sodass dieser Absender am Senden von Nachrichten gehindert wird.</p>
<p>In der E-Mail-Info wird der Empfänger angezeigt, an den der Absender keine Nachrichten senden darf, und der Absender erhält die Option, den Empfänger aus der Nachricht zu entfernen. Außerdem wird der Absender informiert, dass die Nachricht nicht übermittelt wird.</p>
<p>Wenn es sich bei dem eingeschränkten Empfänger um einen externen Empfänger oder um eine Verteilergruppe mit externen Empfängern handelt, wird auch diese Information dem Absender bereitgestellt. Die folgenden E-Mail-Infos werden jedoch ggf. unterdrückt:</p>
<ul>
<li><p>Automatische Antworten</p></li>
<li><p>Postfach voll</p></li>
<li><p>Benutzerdefinierte E-Mail-Infos</p></li>
<li><p>Moderierter Empfänger</p></li>
<li><p>Übergroße Nachricht</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Externe Empfänger</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info zu externen Empfängern wird angezeigt, wenn der Absender einen externen Empfänger oder eine Verteilergruppe mit externen Empfängern hinzufügt.</p>
<p>Mit dieser E-Mail-Info werden Absender informiert, wenn eine Nachricht, die sie schreiben, die Organisation verlassen wird. So können sie die richtigen Entscheidungen hinsichtlich Formulierungen, Tonfall und Inhalt treffen.</p>
<p>Standardmäßig ist diese E-Mail-Info deaktiviert. Sie können sie mit dem Cmdlet <strong>Set-OrganizationConfig</strong> aktivieren. Weitere Informationen finden Sie unter <a href="mailtips-over-organization-relationships-exchange-2013-help.md">E-Mail-Infos über Organisationsbeziehungen</a>.</p>
<p>Wenn ein Teil Ihrer Benutzerpostfächer in Exchange Online gehostet wird und Sie die Koexistenz mit Exchange Online eingerichtet haben, hat die Einstellung für das Remotedomänenobjekt, das den Remotebereich Ihrer Organisation darstellt, direkte Auswirkungen auf die Verarbeitung dieser E-Mail-Info.</p>
<p>Wenn die Remotedomäne als interne Domäne konfiguriert ist (der Parameter <em>IsInternal</em> für das Remotedomänenobjekt ist auf <code>$true</code> festgelegt), werden alle Empfänger in dieser Remotedomäne als intern behandelt, sodass für sie die E-Mail-Info für externe Empfänger nicht angezeigt wird. Wenn die Remotedomäne nicht als interne Domäne konfiguriert ist, werden die Empfänger in dieser Domäne als extern betrachtet, und beim Verfassen einer Nachricht an diese Empfänger wird diese E-Mail-Info angezeigt.</p>

> [!NOTE]
> Diese E-Mail-Info wird nicht ausgewertet, wenn eine Nachricht an eine Verteilergruppe in der Remotedomäne verfasst wird.


</td>
</tr>
<tr class="odd">
<td><p>Große Benutzergruppe</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info zu großer Benutzergruppe wird angezeigt, wenn der Absender eine Verteilergruppe hinzufügt, die mehr Mitglieder enthält, als für die Größe einer großen Benutzergruppe für Ihre Organisation konfiguriert ist. Standardmäßig wird diese E-Mail-Info in Exchange für Nachrichten an Verteilergruppen mit mehr als 25 Mitgliedern angezeigt. Weitere Informationen finden Sie unter <a href="configure-the-large-audience-size-for-your-organization-exchange-2013-help.md">Konfigurieren einer großen Benutzergruppe für Ihre Organisation</a>.</p>
<p>Die Größe der Verteilergruppen wird nicht jedes Mal berechnet. Stattdessen werden die Verteilergruppeninformationen aus den Gruppenmetrikdaten gelesen.</p></td>
</tr>
<tr class="even">
<td><p>Moderierter Empfänger</p></td>
<td><p>Outlook</p>
<p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info zu moderiertem Empfänger wird angezeigt, wenn der Absender einen moderierten Empfänger hinzufügt.</p>
<p>Die E-Mail-Info zeigt an, welcher Empfänger moderiert ist, und informiert den Absender, dass dies zu Verzögerungen bei der Zustellung führen kann.</p>
<p>Wenn der Absender zugleich der Moderator ist, wird diese E-Mail-Info nicht angezeigt. Ebenso wird sie nicht angezeigt, wenn dem Absender explizit gestattet wurde, Nachrichten an den Empfänger zu senden (indem der Name des Absenders zur Liste &quot;Nachrichten annehmen von&quot; des Empfängers hinzugefügt wurde).</p>
<p>Anweisungen zum Konfigurieren moderierter Empfänger in Exchange 2013 finden Sie unter <a href="common-message-approval-scenarios-exchange-2013-help.md">Gängige Szenarien der Nachrichtengenehmigung</a>.</p>
<p>Anweisungen zum Konfigurieren moderierter Empfänger in Exchange Online finden Sie unter <a href="https://technet.microsoft.com/de-de/library/jj983442(v=exchg.150)">Konfigurieren eines moderierten Empfängers in Exchange Online</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Antwort an alle bei Bcc</p></td>
<td><p>Outlook Web App</p></td>
<td><p>Die E-Mail-Info zur Antwort an alle bei Bcc wird angezeigt, wenn der Absender eine Bcc-Kopie einer Nachricht enthält und <strong>Allen antworten</strong> auswählt.</p>
<p>Wenn ein Benutzer für eine solche Nachricht <strong>Allen antworten</strong> auswählt, erfahren alle anderen Empfänger, an die die Nachricht gesendet wurde, dass dieser Benutzer eine Bcc-Kopie erhalten hat. Das dies in den seltensten Fällen erwünscht ist, wird der Benutzer mit dieser E-Mail-Info auf die Situation hingewiesen.</p></td>
</tr>
<tr class="even">
<td><p>Übergroße Nachricht</p></td>
<td><p>Outlook</p></td>
<td><p>Die E-Mail-Info zu übergroßer Nachricht wird angezeigt, wenn die vom Absender verfasste Nachricht die konfigurierten Einschränkungen der Nachrichtengröße in Ihrer Organisation übersteigt.</p>
<p>Die E-Mail-Info wird angezeigt, wenn die Nachrichtengröße eine der folgenden Größeneinschränkungen verletzt:</p>
<ul>
<li><p>Einstellung für maximale Sendegröße für das Postfach des Absenders</p></li>
<li><p>Einstellung für maximale Empfangsgröße für das Postfach des Absenders</p></li>
<li><p>Einschränkung für die maximale Nachrichtengröße für die Organisation</p></li>
</ul>

> [!NOTE]
> Aufgrund der Komplexität der Implementierung werden die Einschränkungen der Nachrichtengröße für die Connectors in Ihrer Organisation nicht berücksichtigt.


</td>
</tr>
</tbody>
</table>


## Einschränkungen von E-Mail-Infos

Für die E-Mail-Info gelten die folgenden Einschränkungen:

  - E-Mail-Infos werden bei der Arbeit im Offlinemodus von Outlook nicht unterstützt.

  - Wenn eine Nachricht an eine Verteilergruppe adressiert ist, werden die E-Mail-Infos für einzelne Empfänger, die Mitglieder dieser Verteilergruppe sind, nicht ausgewertet. Wenn es sich bei einem der Mitglieder jedoch um einen externen Empfänger handelt, wird die E-Mail-Info für externe Empfänger angezeigt, in der dem Absender die Anzahl externer Empfänger in der Verteilergruppe angezeigt wird.

  - Wenn die Nachricht an mehr als 200 Empfänger adressiert ist, werden aus Leistungsgründen keine E-Mail-Infos für einzelne Postfächer ausgewertet.

  - Benutzerdefinierte E-Mail-Infos sind auf 175 Zeichen beschränkt.

  - Während Exchange 2010 E-Mail-Infos in ihrer Gesamtheit auffüllt, werden in Exchange 2013 nur maximal 1000 Zeichen angezeigt.

  - Wenn der Absender beginnt, eine Nachricht zu erstellen, und sie für einen längeren Zeitraum geöffnet lässt, werden die E-Mail-Infos zu automatischen Antworten und vollem Postfach alle zwei Stunden ausgewertet.

