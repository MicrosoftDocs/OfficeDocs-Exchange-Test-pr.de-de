---
title: 'Transportregelaktionen: Exchange 2013 Help'
TOCTitle: Aktionen für Nachrichtenflussregeln
ms:assetid: 5d11a955-b1cc-4150-a0b9-a8cc48ba9bde
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998315(v=EXCHG.150)
ms:contentKeyID: 50475771
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportregelaktionen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-05-03_

Aktionen in Nachrichtenflussregeln (auch als Transportregeln bekannt) geben an, was mit Nachrichten geschehen soll, die den Bedingungen der Regel entsprechen. Sie können beispielsweise eine Regel erstellen, die eine Nachricht eines bestimmten Absenders an einen Moderator weiterleitet oder allen ausgehenden Nachrichten einen Haftungsausschluss oder eine personalisierte Signatur hinzugefügt.

Aktionen erfordern normalerweise zusätzliche Eigenschaften. Wenn durch die Regel beispielsweise eine Nachricht umgeleitet werden soll, müssen Sie angeben, wohin die Nachricht geleitet werden soll. Einige Aktionen weisen mehrere Eigenschaften auf, die verfügbar oder erforderlich sind. Wenn durch die Regel beispielsweise dem Nachrichtenkopf ein Kopfzeilenfeld hinzugefügt werden soll, müssen Sie den Namen und den Wert der Kopfzeile angeben. Wenn durch die Regel Nachrichten ein Haftungsausschluss hinzufügt werden soll, müssen Sie den Text für den Haftungsausschluss angeben. Darüber hinaus können Sie festlegen, wo der Text eingefügt werden soll und was passieren soll, wenn der Haftungsausschluss der Nachricht nicht hinzugefügt werden kann. Normalerweise können Sie in einer Regel mehrere Aktionen konfigurieren, einige Aktionen sind jedoch ausgeschlossen. Eine Regel kann z. B. nicht gleiche Nachricht gleichzeitig ablehnen und umleiten.

Weitere Informationen zu Nachrichtenflussregeln in Exchange Server 2013 finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md).

Weitere Informationen zu Bedingungen und Ausnahmen in Nachrichtenflussregeln finden Sie unter [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md).

Weitere Informationen zu Aktionen in Nachrichtenflussregeln in Exchange Online oder Exchange Online Protection finden Sie unter [Aktionen für Nachrichtenflussregeln in Exchange Online](https://technet.microsoft.com/de-de/library/jj919237\(v=exchg.150\)) oder [Aktionen für Nachrichtenflussregeln in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj920117\(v=exchg.150\)).

## Aktionen für Nachrichtenflussregeln auf Postfachservern

Die Aktionen, die in den Nachrichtenflussregeln auf Postfachservern verfügbar sind, werden in der folgenden Tabelle beschrieben. Gültige Werte für die Eigenschaften werden in Eigenschaftswerte beschrieben.

**Hinweise:** 

  - Nach dem Auswählen einer Aktion in der Exchange-Verwaltungskonsole (EAC) unterscheidet sich der Wert, der letztendlich im Feld **Gehen Sie wie folgt vor** angezeigt wird, häufig vom ausgewählten Klickpfad. Wenn Sie zudem neue Regeln erstellen, können Sie manchmal (je nach vorgenommener Auswahl) einen kurzen Aktionsnamen aus einer Vorlage (eine gefilterte Liste von Aktionen) wählen anstatt dem vollständigen Klickpfad zu folgen. Die kurzen Namen und vollständigen Klickpfadwerte werden in der Spalte „EAC“ in der Tabelle angezeigt.

  - Darüber hinaus unterscheiden sich die Namen einiger der Aktionen, die vom Cmdlet **Get-TransportRuleAction** zurückgegeben werden, von den entsprechenden Parameternamen. Für eine Aktion sind möglicherweise mehrere Parameter erforderlich.


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
<th>Aktion in der Exchange-Verwaltungskonsole</th>
<th>Aktionsparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaft</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Nachricht zur Genehmigung weiterleiten an… diese Personen</strong></p>
<p><strong>Nachricht zur Genehmigung weiterleiten an</strong> &gt; <strong>diese Personen</strong></p></td>
<td><p><em>ModerateMessageByUser</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Leitet die Nachricht als Anlage, die in eine Genehmigungsanforderung eingeschlossen ist, an die angegebenen Moderatoren weiter. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/common-message-approval-scenarios">Gängige Szenarien der Nachrichtengenehmigung</a>. Eine Verteilergruppe kann nicht als Moderator verwendet werden.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Nachricht zur Genehmigung weiterleiten an … den Vorgesetzten des Absenders</strong></p>
<p><strong>Nachricht zur Genehmigung weiterleiten an</strong> &gt; <strong>den Vorgesetzten des Absenders</strong></p></td>
<td><p><em>ModerateMessageByManager</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachricht zur Genehmigung weiterleiten an den Vorgesetzten des Absenders.</p>
<p>Diese Aktion funktioniert nur, wenn das <strong>Manager</strong>-Attribut des Absenders in Active Directory definiert ist. Andernfalls wird die Nachricht ohne Moderation an die Empfänger übermittelt.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Nachricht umleiten an...diese Empfänger</strong></p>
<p><strong>Die Nachricht umleiten an</strong> &gt; <strong>diese Empfänger</strong></p></td>
<td><p><em>RedirectMessageTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Leitet die Nachricht an die angegebene Empfänger um. Die Nachricht wird nicht an die Originalempfänger übermittelt, und der Absender und die Originalempfänger werden nicht benachrichtigt.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Nachricht mit Erklärung ablehnen</strong></p>
<p><strong>Nachricht blockieren</strong> &gt; <strong>Nachricht ablehnen und Erläuterung einfügen</strong></p></td>
<td><p><em>RejectMessageReasonText</em></p></td>
<td><p><code>String</code></p></td>
<td><p>Gibt die Nachricht in einem Unzustellbarkeitsbericht (auch als NDR bekannt) mit dem angegebenen Text als Ablehnungsgrund an den Absender zurück. Der Empfänger empfängt weder die Originalnachricht noch eine Benachrichtigung.</p>
<p>Der verwendete erweiterte Statuscode lautet standardmäßig <code>5.7.1</code>.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell können Sie den DSN-Code mithilfe des Parameters <em>RejectMessageEnhancedStatusCode</em> angeben.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nachricht ablehnen mit erweitertem Statuscode</strong></p>
<p><strong>Nachricht blockieren</strong> &gt; <strong>Nachricht ablehnen mit erweitertem Statuscode</strong></p></td>
<td><p><em>RejectMessageEnhancedStatusCode</em></p></td>
<td><p><code>DSNEnhancedStatusCode</code></p></td>
<td><p>Gibt die Nachricht in einem Unzustellbarkeitsbericht mit dem angegebenen erweiterten Delivery Status Notification (DSN)-Code an den Absender zurück. Der Empfänger empfängt weder die Originalnachricht noch eine Benachrichtigung.</p>
<p>Gültige DSN-Codes sind <code>5.7.1</code> oder <code>5.7.900</code> bis <code>5.7.999</code>.</p>
<p>Der Standardtext für den Grund lautet <code>Delivery not authorized, message refused</code>.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell können Sie den Text für den Ablehnungsgrund mithilfe des Parameters <em>RejectMessageReasonText</em> angeben.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Löschen der Nachricht ohne Benachrichtigung</strong></p>
<p><strong>Nachricht blockieren</strong> &gt; <strong>Nachricht ohne Benachrichtigung löschen</strong></p></td>
<td><p><em>DeleteMessage</em></p></td>
<td><p>N/V</p></td>
<td><p>Ignoriert die E-Mail-Nachricht, ohne eine Benachrichtigung an Empfänger oder Absender zu senden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>BCC-Empfänger hinzufügen</strong></p>
<p><strong>Empfänger hinzufügen</strong> &gt; <strong>zu Bcc-Feld</strong></p></td>
<td><p><em>BlindCopyTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>Bcc</strong> der Nachricht hinzu. Die Originalempfänger werden nicht benachrichtigt und können die zusätzlichen Adressen nicht sehen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>AN-Empfänger hinzufügen</strong></p>
<p><strong>Empfänger hinzufügen</strong> &gt; <strong>zu An-Feld</strong></p></td>
<td><p><em>AddToRecipients</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>To</strong> der Nachricht hinzu. Die Originalempfänger können die zusätzlichen Adressen sehen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>CC-Empfänger hinzufügen</strong></p>
<p><strong>Empfänger hinzufügen</strong> &gt; <strong>zu Cc-Feld</strong></p></td>
<td><p><em>CopyTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>Cc</strong> der Nachricht hinzu. Die Originalempfänger können die zusätzliche Adresse sehen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Vorgesetzten des Absenders als Empfänger hinzufügen</strong></p>
<p><strong>Empfänger hinzufügen</strong> &gt; <strong>Vorgesetzten des Absenders als Empfänger hinzufügen</strong></p></td>
<td><p><em>AddManagerAsRecipientType</em></p></td>
<td><p><code>AddedManagerAction</code></p></td>
<td><p>Fügt den Vorgesetzten des Absenders als angegebenen Empfängertyp der Nachricht hinzu (<strong>To</strong>, <strong>Cc</strong>, <strong>Bcc</strong>) oder leitet die Nachricht an den Vorgesetzten des Absenders ohne Benachrichtigung des Absenders oder des Empfängers um.</p>
<p>Diese Aktion funktioniert nur, wenn das <strong>Manager</strong>-Attribut des Absenders in Active Directory definiert ist.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Haftungsausschluss anfügen</strong></p>
<p><strong>Haftungsausschluss auf die Nachricht anwenden</strong> &gt; <strong>Haftungsausschluss anfügen</strong></p></td>
<td><p><em>ApplyHtmlDisclaimerText</em></p>
<p><em>ApplyHtmlDisclaimerFallbackAction</em></p>
<p><em>ApplyHtmlDisclaimerTextLocation</em></p></td>
<td><p>Erste Eigenschaft: <code>DisclaimerText</code></p>
<p>Zweite Eigenschaft: <code>DisclaimerFallbackAction</code></p>
<p>Dritte Eigenschaft (nur Exchange-Verwaltungsshell): <code>DisclaimerTextLocation</code></p></td>
<td><p>Fügt den angegebenen HTML-Haftungsausschluss am Ende der Nachricht ein.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell verwenden Sie den Parameter <em>ApplyHtmlDisclaimerTextLocation</em> mit dem Wert <code>Append</code>.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Dem Haftungsausschluss voranstellen</strong></p>
<p><strong>Haftungsausschluss auf die Nachricht anwenden</strong> &gt; <strong>Haftungsausschluss voranstellen</strong></p></td>
<td><p><em>ApplyHtmlDisclaimerText</em></p>
<p><em>ApplyHtmlDisclaimerFallbackAction</em></p>
<p><em>ApplyHtmlDisclaimerTextLocation</em></p></td>
<td><p>Erste Eigenschaft: <code>DisclaimerText</code></p>
<p>Zweite Eigenschaft: <code>DisclaimerFallbackAction</code></p>
<p>Dritte Eigenschaft (nur Exchange-Verwaltungsshell): <code>DisclaimerTextLocation</code></p></td>
<td><p>Fügt den angegebenen HTML-Haftungsausschluss am Anfang der Nachricht ein.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell verwenden Sie den Parameter <em>ApplyHtmlDisclaimerTextLocation</em> mit dem Wert <code>Prepend</code>.</p>
<p></p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diese Kopfzeile entfernen</strong></p>
<p><strong>Nachrichteneigenschaften ändern</strong> &gt; <strong>Nachrichtenkopfzeile entfernen</strong></p></td>
<td><p><em>RemoveHeader</em></p></td>
<td><p><code>MessageHeaderField</code></p></td>
<td><p>Entfernt das angegebene Feld für die Nachrichtenkopfzeilen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Nachrichtenkopf auf diesen Wert festlegen</strong></p>
<p><strong>Nachrichteneigenschaften ändern</strong> &gt; <strong>Nachrichtenkopfzeile festlegen</strong></p></td>
<td><p><em>SetHeaderName</em></p>
<p><em>SetHeaderValue</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>String</code></p></td>
<td><p>Ändert oder fügt das angegebene Kopfzeilenfeld im Nachrichtenkopf hinzu und legt das für das Kopfzeilenfeld den angegebenen Wert fest.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nachrichtenklassifikation anwenden</strong></p>
<p><strong>Nachrichteneigenschaften ändern</strong> &gt; <strong>Nachrichtenklassifikation anwenden</strong></p></td>
<td><p><em>ApplyClassification</em></p></td>
<td><p><code>MessageClassification</code></p></td>
<td><p>Wendet die angegebene Nachrichtenklassifikation auf die Nachricht an.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>SCL-Bewertung (Spam Confidence Level) festlegen</strong></p>
<p><strong>Nachrichteneigenschaften ändern</strong> &gt; <strong>SCL-Bewertung (Spam Confidence Level) festlegen</strong></p></td>
<td><p><em>SetSCL</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Legt die SCL-Bewertung (Spam Confidence Level) einer Nachricht auf den angegebenen Wert fest.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Rechteschutz auf Nachricht anwenden mit</strong></p>
<p><strong>Nachrichtensicherheit ändern</strong> &gt; <strong>Rechteschutz anwenden</strong></p></td>
<td><p><em>ApplyRightsProtectionTemplate</em></p></td>
<td><p><code>RMSTemplate</code></p></td>
<td><p>Wendet die angegebene RMS-Vorlage (Rights Management Services, Rechteverwaltungsdienst) auf die Nachricht an.</p>
<p>RMS erfordert Exchange-Enterprise-Clientzugriffslizenzen (CALs) für jedes Postfach. Weitere Informationen zu CALs finden Sie im Thema zur <a href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</a>.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>TLS-Verschlüsselung erforderlich</strong></p>
<p><strong>Nachrichtensicherheit ändern</strong> &gt; <strong>TLS-Verschlüsselung erforderlich</strong></p></td>
<td><p><em>RouteMessageOutboundRequireTls</em></p></td>
<td><p><code>n/a</code></p></td>
<td><p>Erzwingt eine Weiterleitung der ausgehenden Nachrichten über eine TLS-verschlüsselte Verbindung.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Dem Betreff der Nachricht Folgendes voranstellen</strong></p></td>
<td><p><em>PrependSubject</em></p></td>
<td><p><code>String</code></p></td>
<td><p>Fügt den angegebenen Text am Anfang des Felds <strong>Subject</strong> der Nachricht ein. Verwenden Sie ein Leerzeichen oder einen Doppelpunkt (:) als letztes Zeichen des angegebenen Texts, um ihn vom ursprünglichen Betrefftext zu unterscheiden.</p>
<p>Um zu verhindern, dass die gleiche Zeichenfolge Nachrichten hinzugefügt wird, die den Text bereits in der Betreffzeile (z. B. Antworten) enthalten, fügen Sie der Regel die Ausnahme <strong>Der Betreff enthält</strong> (<em>ExceptIfSubjectContainsWords</em>) hinzu.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Absender mit Richtlinientipp benachrichtigen</strong></p></td>
<td><p><em>NotifySender</em></p>
<p><em>RejectMessageReasonText</em></p>
<p><em>RejectMessageEnhancedStatusCode</em> (nur Exchange-Verwaltungsshell)</p></td>
<td><p>Erste Eigenschaft: <code>NotifySenderType</code></p>
<p>Zweite Eigenschaft: <code>String</code></p>
<p>Dritte Eigenschaft (nur Exchange-Verwaltungsshell): <code>DSNEnhancedStatusCode</code></p></td>
<td><p>Benachrichtigt den Absender oder blockiert die Nachricht, wenn die Nachricht einer DLP-Richtlinie entspricht.</p>
<p>Wenn Sie diese Aktion verwenden, müssen Sie die Bedingung <strong>Die Nachricht enthält vertrauliche Informationen</strong> (<em>MessageContainsDataClassification</em>) verwenden.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell ist der Parameter <em>RejectMessageReasonText</em> optional. Wenn Sie diesen Parameter nicht verwenden, wird der Standardtext <code>Delivery not authorized, message refused</code> verwendet.</p>
<p>In der Exchange-Verwaltungsshell können Sie auch den Parameter <em>RejectMessageEnhancedStatusCode</em> verwenden, um den erweiterten Statuscode anzugeben. Wenn Sie diesen Parameter nicht verwenden, wird der erweiterte Statuscode <code>5.7.1</code> verwendet.</p>
<p>Diese Aktion beschränkt andere Bedingungen, Ausnahmen und Aktionen, die Sie in der Regel konfigurieren können.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Schadensbericht generieren und senden an</strong></p></td>
<td><p><em>GenerateIncidentReport</em></p>
<p><em>IncidentReportContent</em></p></td>
<td><p>Erste Eigenschaft: <code>Addresses</code></p>
<p>Zweite Eigenschaft: <code>IncidentReportContent</code></p></td>
<td><p>Sendet einen Schadensbericht, der den angegebenen Inhalt an die angegebenen Empfänger enthält.</p>
<p>Ein Schadensbericht wird für Nachrichten generiert, die den Data Loss Prevention (DLP)-Richtlinien in Ihrer Organisation entsprechen.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Empfänger durch Nachricht benachrichtigen</strong></p></td>
<td><p><em>GenerateNotification</em></p></td>
<td><p><code>NotificationMessageText</code></p></td>
<td><p>Gibt den Text, HTML-Tags und Nachrichtenschlüsselwörter an, die in der Benachrichtigungs-E-Mail einbezogen werden sollen, die an die Empfänger der Nachricht gesendet wird. Sie können beispielsweise Empfänger benachrichtigen, dass die Nachricht von der Regel abgelehnt oder als Spam markiert und Ihrem Junk-E-Mail-Ordner zugestellt wurde.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p>Abschnitt <strong>Eigenschaften dieser Regel</strong> &gt; <strong>Überwachen Sie diese Regel mit Schweregrad</strong></p></td>
<td><p><em>SetAuditSeverity</em></p></td>
<td><p><code>AuditSeverityLevel</code></p></td>
<td><p>Gibt an, ob:</p>
<ul>
<li><p>die Generierung eines Schadensberichts und des entsprechenden Eintrags im Nachrichtenverfolgungsprotokoll verhindert werden soll.</p></li>
<li><p>ein Schadensbericht und der entsprechende Eintrag im Nachrichtenverfolgungsprotokoll mit dem angegebenen Schweregrad (niedrig, mittel oder hoch) generiert werden soll.</p></li>
</ul></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p>Abschnitt <strong>Eigenschaften dieser Regel</strong> &gt; <strong>Verarbeiten weiterer Regeln beenden</strong></p>
<p><strong>Weitere Optionen</strong> &gt; Abschnitt <strong>Eigenschaften dieser Regel</strong> &gt; <strong>Verarbeiten weiterer Regeln beenden</strong></p></td>
<td><p><em>StopRuleProcessing</em></p></td>
<td><p>N/V</p></td>
<td><p>Gibt an, dass die Nachricht nach dem Anwenden der Regel nicht mehr von anderen Regeln verarbeitet werden kann.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Aktionen für Nachrichtenflussregeln auf Edge-Transport-Servern

Eine kleine Teilmenge der Aktionen, die auf Postfachservern verfügbar sind, stehen auch auf Edge-Transport-Servern zur Verfügung. Es gibt jedoch einige Aktionen, die nur auf Edge-Transport-Servern zur Verfügung stehen. Es gibt keine Exchange-Verwaltungskonsole auf Edge-Transport-Servern. Daher können Sie nur die Nachrichtenflussregeln in der Exchange-Verwaltungsshell auf dem lokalen Edge-Transport-Server verwalten. Die Aktionen sind in der folgenden Tabelle beschrieben. Die Typen von Eigenschaften sind im Abschnitt Eigenschaftswerte beschrieben.


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
<th>Aktionsparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaft</th>
<th>Beschreibung</th>
<th>Verfügbar auf</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AddToRecipients</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>To</strong> der Nachricht hinzu. Die Originalempfänger können die zusätzlichen Adressen sehen.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>BlindCopyTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>Bcc</strong> der Nachricht hinzu. Die Originalempfänger werden nicht benachrichtigt und können die zusätzlichen Adressen nicht sehen.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>CopyTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Fügt einen oder mehrere Empfänger zum Feld <strong>Cc</strong> der Nachricht hinzu. Die Originalempfänger können die zusätzliche Adresse sehen.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>DeleteMessage</em></p></td>
<td><p>N/V</p></td>
<td><p>Ignoriert die E-Mail-Nachricht, ohne eine Benachrichtigung an Empfänger oder Absender zu senden.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>Disconnect</em></p></td>
<td><p>N/V</p></td>
<td><p>Beendet die SMTP-Verbindung zwischen dem sendenden Server und dem Edge-Transport-Server, ohne einen Unzustellbarkeitsbericht zu generieren.</p></td>
<td><p>Nur Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>LogEventText</em></p></td>
<td><p><code>String</code></p></td>
<td><p>Generiert ein Ereignis mit dem angegebenen Text im Anwendungsprotokoll des lokalen Edge-Transport-Servers. Jeder Eintrag enthält die folgenden Informationen:</p>
<ul>
<li><p><strong>Grad</strong> <code>Information</code></p></li>
<li><p><strong>Quelle</strong> <code>MSExchange Messaging Policies</code></p></li>
<li><p><strong>Ereignis-ID</strong> <code>4000</code></p></li>
<li><p><strong>Taskkategorie</strong> <code>Rules</code></p></li>
<li><p><strong>EventData</strong> <code>The following message is logged by an action in the rules: &lt;text you specify&gt;.</code></p></li>
</ul></td>
<td><p>Nur Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>PrependSubject</em></p></td>
<td><p><code>String</code></p></td>
<td><p>Fügt den angegebenen Text am Anfang des Felds <strong>Subject</strong> der Nachricht ein. Verwenden Sie ein Leerzeichen oder einen Doppelpunkt (:) als letztes Zeichen des angegebenen Texts, um ihn vom ursprünglichen Betreff zu unterscheiden.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>Quarantine</em></p></td>
<td><p>N/V</p></td>
<td><p>Übermittelt die Nachricht in das Quarantänepostfach, das in der Inhaltsfilter-Konfiguration auf dem Edge-Transport-Server definiert ist. Weitere Informationen finden Sie unter <a href="configure-a-spam-quarantine-mailbox-exchange-2013-help.md">Konfigurieren eines Spamquarantänepostfachs</a>.</p>
<p>Wenn das Quarantänepostfach nicht konfiguriert wurde, wird die Nachricht an den Absender in einem Unzustellbarkeitsbericht zurückgegeben.</p></td>
<td><p>Nur Edge-Transport-Server</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>RedirectMessageTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Leitet die Nachricht an die angegebene Empfänger um. Die Nachricht wird nicht an die Originalempfänger übermittelt, und der Absender und die Originalempfänger werden nicht benachrichtigt.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>RemoveHeader</em></p></td>
<td><p><code>MessageHeaderField</code></p></td>
<td><p>Entfernt das angegebene Feld für die Nachrichtenkopfzeilen.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>SetHeaderName</em></p>
<p><em>SetHeaderValue</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>String</code></p></td>
<td><p>Ändert oder fügt das angegebene Kopfzeilenfeld im Nachrichtenkopf hinzu und legt das für das Kopfzeilenfeld den angegebenen Wert fest.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>SetSCL</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Legt die SCL-Bewertung der Nachricht auf den angegebenen Wert fest.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>SmtpRejectMessageRejectText</em></p>
<p><em>SmtpRejectMessageRejectStatusCode</em></p></td>
<td><p>Erste Eigenschaft: <code>String</code></p>
<p>Zweite Eigenschaft: <code>SMTPStatusCode</code></p></td>
<td><p>Beendet die SMTP-Verbindung zwischen dem sendenden Server und dem Edge-Transport-Server mit dem angegebenen SMTP-Statuscode und dem angegebenen Ablehnungstext . Der Empfänger empfängt weder die Originalnachricht noch eine Benachrichtigung.</p>
<p>Gültige Werte für den SMTP-Statuscode sind ganze Zahlen von <code>400</code> bis <code>500</code> wie in RFC 3463 definiert.</p>
<p>Wenn Sie den Ablehnungstext angeben, ohne den SMTP-Statuscode anzugeben, wird der Standard-Code <code>550</code> verwendet.</p>
<p>Wenn Sie den SMTP-Statuscode ohne Angabe des Ablehnungstextes angeben, wird der Text <code>Delivery not authorized, message refused</code> verwendet.</p></td>
<td><p>Nur Edge-Transport-Server</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>StopRuleProcessing</em></p></td>
<td><p>N/V</p></td>
<td><p>Gibt an, dass die Nachricht nach dem Anwenden der Regel nicht mehr von anderen Regeln verarbeitet werden kann.</p></td>
<td><p>Postfachserver und Edge-Transport-Server</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


## Eigenschaftswerte

Die Eigenschaftswerte, die für die Aktionen in den Nachrichtenflussregeln verwendet werden, sind in der folgenden Tabelle beschrieben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Gültige Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>AddedManagerAction</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>n</strong></p></li>
<li><p><strong>Cc</strong></p></li>
<li><p><strong>Bcc</strong></p></li>
<li><p><strong>Redirect</strong></p></li>
</ul></td>
<td><p>Gibt an, wie der Vorgesetzte des Absenders in Nachrichten einbezogen werden soll.</p>
<ul>
<li><p>Bei Auswahl von <strong>n</strong>, <strong>Cc</strong> oder <strong>Bcc</strong> wird der Vorgesetzte des Absenders als Empfänger in das angegebene Feld eingefügt.</p></li>
<li><p>Bei Auswahl von <strong>Umleiten</strong> wird die Nachricht nur an den Vorgesetzten des Absenders ohne Benachrichtigung des Absenders oder des Empfängers übermittelt.</p></li>
</ul>
<p>Diese Aktion funktioniert nur, wenn das <strong>Manager</strong>-Attribut des Absenders in Active Directory definiert ist.</p></td>
</tr>
<tr class="even">
<td><p><code>Addresses</code></p></td>
<td><p>Exchange Empfänger</p></td>
<td><p>Abhängig von der Aktion können Sie möglicherweise ein beliebiges E-Mail-aktiviertes Objekt in der Organisation angeben, oder Sie sind auf einen bestimmten Objekttyp beschränkt. In der Regel können Sie mehrere Empfänger auswählen, Sie können einen Schadensbericht jedoch nur an einen Empfänger senden.</p></td>
</tr>
<tr class="odd">
<td><p><code>AuditSeverityLevel</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p>Deaktivieren Sie <strong>Diese Regel mit folgendem Schweregrad überwachen</strong>, oder wählen Sie <strong>Diese Regel mit folgendem Schweregrad überwachen</strong> mit dem Wert <strong>Nicht angegeben</strong> (<code>DoNotAudit</code>) aus.</p></li>
<li><p><strong>Niedrig</strong></p></li>
<li><p><strong>Mittel</strong></p></li>
<li><p><strong>Hoch</strong></p></li>
</ul></td>
<td><p>Die Werte <strong>Niedrig</strong>, <strong>Mittel</strong> oder <strong>Hoch</strong> legen den Schweregrad fest, der dem Schadensbericht und dem entsprechenden Eintrag im Nachrichtenverfolgungsprotokoll zugeordnet wird.</p>
<p>Der andere Wert verhindert, dass ein Schadensbericht erstellt und der entsprechende Eintrag in das Nachrichtenverfolgungsprotokoll geschrieben wird.</p></td>
</tr>
<tr class="even">
<td><p><code>DisclaimerFallbackAction</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>Umbruch</strong></p></li>
<li><p><strong>Ignorieren</strong></p></li>
<li><p><strong>Ablehnen</strong></p></li>
</ul></td>
<td><p>Gibt an, wie vorzugehen ist, wenn ein Haftungsausschluss nicht auf eine Nachricht angewendet werden kann. Es kann Situationen geben, in denen die Inhalte einer Nachricht nicht verändert werden können, z. B. wenn eine Nachricht verschlüsselt ist. Die verfügbaren Ausweichaktionen sind:</p>
<ul>
<li><p><strong>Umbruch</strong>  Die ursprüngliche Nachricht wird in einen neuen Nachrichtenumschlag umgebrochen, und der Haftungsausschlusstest wird in die neue Nachricht eingefügt. Dies ist der Standardwert.</p>
<p><strong>Hinweise:</strong></p>
<ul>
<li><p>Alle nachfolgenden Nachrichtenflussregeln werden auf den neuen Nachrichtenumschlag angewendet, nicht auf die ursprüngliche Nachricht. Konfigurieren Sie diese Regeln daher mit einer niedrigeren Priorität als die anderen Regeln.</p></li>
<li><p>Wenn die ursprüngliche Nachricht nicht in einen neuen Nachrichtenumschlag umgebrochen werden kann, wird die ursprüngliche Nachricht nicht übermittelt. Die Nachricht wird mit einem Unzustellbarkeitsbericht an den Absender zurückgesendet.</p></li>
</ul></li>
<li><p><strong>Ignorieren</strong>  Die Regel wird ignoriert, und die Nachricht wird ohne Haftungsausschluss zugestellt.</p></li>
<li><p><strong>Ablehnen</strong>  Die Nachricht wird in einem Unzustellbarkeitsbericht an den Absender zurückgeschickt.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><code>DisclaimerText</code></p></td>
<td><p>HTML-Zeichenfolge</p></td>
<td><p>Gibt den Haftungsausschluss-Text, der HTML-Tags, Inline Cascading Style Stylesheet (CSS)-Tags und Bilder enthalten kann, mithilfe des IMG-Tags an. Die Höchstlänge beträgt 5000 Zeichen einschließlich Tags.</p></td>
</tr>
<tr class="even">
<td><p><code>DisclaimerTextLocation</code></p></td>
<td><p>Einzelwert: <code>Append</code> oder <code>Prepend</code></p></td>
<td><p>In der Exchange-Verwaltungsshell verwenden Sie <em>ApplyHtmlDisclaimerTextLocation</em>, um die Position des Haftungsausschluss-Texts in der Nachricht anzugeben:</p>
<ul>
<li><p><code>Append</code>   Haftungsausschluss am Ende des Nachrichtentexts einfügen. Dies ist der Standardwert.</p></li>
<li><p><code>Prepend</code>   Haftungsausschluss am Anfang des Nachrichtentexts einfügen.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><code>DSNEnhancedStatusCode</code></p></td>
<td><p>DSN-Code-Einzelwert:</p>
<ul>
<li><p><code>5.7.1</code></p></li>
<li><p><code>5.7.900</code> bis <code>5.7.999</code></p></li>
</ul></td>
<td><p>Gibt den verwendeten DSN-Code an. Sie können mithilfe des Cmdlet <strong>New-SystemMessage</strong> benutzerdefinierte DSNs erstellen.</p>
<p>Wenn Sie den Text für den Ablehnungsgrund nicht mit dem DSN-Code angeben, wird der standardmäßige Grund verwendet: <code>Delivery not authorized, message refused</code>.</p>
<p>Beim Erstellen oder Ändern der Regel in der Exchange-Verwaltungsshell können Sie den Text für den Ablehnungsgrund mithilfe des Parameters <em>RejectMessageReasonText</em> angeben.</p></td>
</tr>
<tr class="even">
<td><p><code>IncidentReportContent</code></p></td>
<td><p>Einer oder mehrere der folgenden Werte:</p>
<ul>
<li><p><strong>Sender</strong></p></li>
<li><p><strong>Recipients</strong></p></li>
<li><p><strong>Subject</strong></p></li>
<li><p><strong>Cc'd recipients</strong> (<code>Cc</code>)</p></li>
<li><p><strong>Bcc'd recipients</strong> (<code>Bcc</code>)</p></li>
<li><p><strong>Severity</strong></p></li>
<li><p><strong>Sender override information</strong> (<code>Override</code>)</p></li>
<li><p><strong>Matching rules</strong> (<code>RuleDetections</code>)</p></li>
<li><p><strong>False positive reports</strong> (<code>FalsePositive</code>)</p></li>
<li><p><strong>Detected data classifications</strong> (<code>DataClassifications</code>)</p></li>
<li><p><strong>Matching content</strong> (<code>IdMatch</code>)</p></li>
<li><p><strong>Ursprüngliche E-Mail</strong> (<code>AttachOriginalMail</code>)</p></li>
</ul></td>
<td><p>Legt fest, dass die Liste der Eigenschaften der ursprünglichen Nachricht in den Schadensbericht aufgenommen werden soll. Sie können eine beliebige Kombination dieser Eigenschaften wählen. Zusätzlich zu den von Ihnen angegebenen Eigenschaften ist die Nachrichten-ID immer im Schadensbericht enthalten. Die verfügbaren Eigenschaften sind:</p>
<ul>
<li><p><strong>Sender</strong>   Der Absender der ursprünglichen Nachricht.</p></li>
<li><p><strong>Recipients</strong>, <strong>Cc'd recipients</strong> und <strong>Bcc'd recipients</strong>   Alle Empfänger der Nachricht oder nur die Empfänger in den Feldern <strong>Cc</strong> oder <strong>Bcc</strong>. Für jede Eigenschaft werden nur die ersten 10 Empfänger in den Schadensbericht eingeschlossen.</p></li>
<li><p><strong>Subject</strong>   Das Feld <strong>Subject</strong> der ursprünglichen Nachricht.</p></li>
<li><p><strong>Severity</strong>   Gibt den Überwachungsschweregrad der ausgelösten Regel an. Nachrichtennachverfolgungsprotokolle umfassen sämtliche Auditschweregrade, und sie können nach Auditschweregrad gefiltert werden. Wenn Sie in der Exchange-Verwaltungskonsole das Kontrollkästchen <strong>Diese Regel mit Schweregrad überwachen</strong> deaktivieren (in der Exchange-Verwaltungsshell: <em>SetAuditSeverity</em> Parameterwert <code>DoNotAudit</code>), werden Regelübereinstimmungen in den Regelberichten nicht angezeigt. Falls eine Nachricht von mehr als einer Regel verarbeitet wurde, wird der höchste Schweregrad in den Schadensberichten aufgenommen.</p></li>
<li><p><strong>Sender override information</strong>   Gibt an, dass ein Richtlinientipp vom Absender außer Kraft gesetzt wurde. Wenn der Absender eine Begründung angegeben hat, werden auch die ersten 100 Zeichen der Begründung hinzugefügt.</p></li>
<li><p><strong>Matching rules</strong>   Die Liste der von der Nachricht ausgelösten Regeln.</p></li>
<li><p><strong>False positive reports</strong>   Das falsch positive Ergebnis, wenn die Nachricht vom Absender für einen Richtlinientipp als falsch positiv gekennzeichnet wurde.</p></li>
<li><p><strong>Detected data classifications</strong>   Die Liste der Typen der in der Nachricht erkannten vertraulichen Informationen.</p></li>
<li><p><strong>Matching content</strong>   Der Typ von vertraulichen Information, der erkannt wurde, der exakte übereinstimmende Inhalt aus der Nachricht sowie die 150 Zeichen vor und nach den übereinstimmenden vertraulichen Informationen.</p></li>
<li><p><strong>Original Mail</strong> Die gesamte Nachricht, die die Regel ausgelöst hat, wird an den Schadensbericht angefügt.</p></li>
</ul>
<p>In der Exchange-Verwaltungsshell können Sie mehrere Werte durch Kommata getrennt angeben.</p></td>
</tr>
<tr class="odd">
<td><p><code>MessageClassification</code></p></td>
<td><p>Einzelnes Nachrichtenklassifikationsobjekt</p></td>
<td><p>Wählen Sie in der Exchange-Verwaltungskonsole aus der Liste der Nachrichtenklassifikationen aus, die Sie erstellt haben.</p>
<p>Verwenden Sie in der Exchange-Verwaltungsshell das Cmdlet <strong>Get-MessageClassification</strong>, um die verfügbaren Objekte für die Nachrichtenklassifikation anzuzeigen.</p></td>
</tr>
<tr class="even">
<td><p><code>MessageHeaderField</code></p></td>
<td><p>Einzelne Zeichenfolge</p></td>
<td><p>Gibt das SMTP-Kopfzeilenfeld der Nachricht zum Hinzufügen, Entfernen oder Ändern an.</p>
<p>Die <em>Nachrichtenkopfzeile</em> ist eine Sammlung erforderlicher und optionaler Kopffelder in der Nachricht. Beispiele für Kopfzeilenfelder sind <strong>To</strong>, <strong>From</strong>, <strong>Received</strong> und <strong>Content-Type</strong>. Offizielle Kopfzeilenfelder sind in RFC 5322 definiert. Inoffizielle Kopfzeilenfelder beginnen mit <strong>X-</strong> und werden als <em>X-Header</em> bezeichnet.</p></td>
</tr>
<tr class="odd">
<td><p><code>NotificationMessageText</code></p></td>
<td><p>Eine beliebige Kombination aus Nur-Text, HTML-Tags und Schlüsselwörtern</p></td>
<td><p>Gibt den Text an, der in einer Empfänger-Benachrichtigung verwendet werden soll.</p>
<p>Zusätzlich zu Nur-Text und HTML-Tags können Sie die folgenden Schlüsselwörter angeben, die Werte aus der ursprünglichen Nachricht verwenden:</p>
<ul>
<li><p><code>%%From%%</code></p></li>
<li><p><code>%%To%%</code></p></li>
<li><p><code>%%Cc%%</code></p></li>
<li><p><code>%%Subject%%</code></p></li>
<li><p><code>%%Headers%%</code></p></li>
<li><p><code>%%MessageDate%%</code></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>NotifySenderType</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>Absender benachrichtigen, aber Senden zulassen</strong> (<code>NotifyOnly</code>)</p></li>
<li><p><strong>Nachricht blockieren</strong> (<code>RejectMessage</code>)</p></li>
<li><p><strong>Nachricht blockieren, wenn es sich nicht um ein falsch positives Ergebnis handelt</strong> (<code>RejectUnlessFalsePositiveOverride</code>)</p></li>
<li><p><strong>Nachricht blockieren, dem Absender aber Außerkraftsetzen und Senden gestatten</strong> (<code>RejectUnlessSilentOverride</code>)</p></li>
<li><p><strong>Nachricht blockieren, aber Außerkraftsetzen und Senden durch Absender mit geschäftlicher Begründung zulassen</strong> (<code>RejectUnlessExplicitOverride</code>)</p></li>
</ul></td>
<td><p>Gibt den Typ des Richtlinientipps an, den der Absender erhält, wenn die Nachricht eine DLP-Richtlinie verletzt. Die Einstellungen werden in der folgenden Liste beschrieben:</p>
<ul>
<li><p><strong>Absender benachrichtigen, aber Senden zulassen</strong> Der Absender wird benachrichtigt, die Nachricht wird jedoch normal zugestellt..</p></li>
<li><p><strong>Nachricht blockieren</strong> Die Nachricht wird zurückgewiesen, und der Absender wird benachrichtigt.</p></li>
<li><p><strong>Nachricht blockieren, wenn es sich nicht um ein falsch positives Ergebnis handelt</strong> Die Nachricht wird zurückgewiesen, sofern sie vom Absender nicht als falsch positiv gekennzeichnet wurde.</p></li>
<li><p><strong>Nachricht blockieren, dem Absender aber Außerkraftsetzen und Senden gestatten</strong> Die Nachricht wird zurückgewiesen, sofern der Absender nicht die Richtlinieneinschränkung außer Kraft gesetzt hat.</p></li>
<li><p><strong>Nachricht blockieren, aber Außerkraftsetzen und Senden durch Absender mit geschäftlicher Begründung zulassen</strong> Dies ähnelt dem Typ <strong>Nachricht blockieren, dem Absender aber Außerkraftsetzen und Senden gestatten</strong>, der Absender gibt jedoch eine Begründung für das Außerkraftsetzen der Richtlinieneinschränkung an.</p></li>
</ul>
<p>Wenn Sie diese Aktion verwenden, müssen Sie Bedingung <strong>Die Nachricht enthält vertrauliche Informationen</strong> (<em>MessageContainsDataClassification</em>) verwenden.</p></td>
</tr>
<tr class="odd">
<td><p><code>RMSTemplate</code></p></td>
<td><p>Einzelnes RMS-Vorlagenobjekt</p></td>
<td><p>Gibt die RMS-Vorlage (Rights Management Services, Rechteverwaltungsdienst) an, die auf die Nachricht angewendet wurde.</p>
<p>In der Exchange-Verwaltungskonsole wählen Sie die RMS-Vorlage aus einer Liste aus.</p>
<p>In der Exchange-Verwaltungsshell verwenden Sie das Cmdlet <strong>Get-RMSTemplate</strong>, um die verfügbaren RMS-Vorlagen anzuzeigen.</p>
<p>RMS erfordert Exchange-Enterprise-Clientzugriffslizenzen (CALs) für jedes Postfach. Weitere Informationen zu CALs finden Sie im Thema zur <a href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</a>.</p></td>
</tr>
<tr class="even">
<td><p><code>SCLValue</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>Spamfilter umgehen</strong> (<code>-1</code>)</p></li>
<li><p>Ganze Zahlen 0 bis 9</p></li>
</ul></td>
<td><p>Gibt den Schwellenwert der SCL-Bewertung (Spam Confidence Level) an, der der Nachricht zugewiesen ist. Ein höherer SCL-Wert gibt an, dass eine Nachricht mit größerer Wahrscheinlichkeit Spam ist.</p></td>
</tr>
<tr class="odd">
<td><p><code>String</code></p></td>
<td><p>Einzelne Zeichenfolge</p></td>
<td><p>Gibt den Text an, der auf das angegebene Nachrichtenkopffeld, den Unzustellbarkeitsbericht oder den Ereignisprotokolleintrag angewendet wird.</p>
<p>Wenn der Wert in der Exchange-Verwaltungsshell Leerzeichen enthält, setzen Sie ihn in Anführungszeichen (&quot;).</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Weitere Informationen

[Verwalten von Nachrichtenflussregeln](https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

[Aktionen für Nachrichtenflussregeln in Exchange Online](https://technet.microsoft.com/de-de/library/jj919237\(v=exchg.150\)) für Exchange Online

[Aktionen für Nachrichtenflussregeln in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj920117\(v=exchg.150\)) für Exchange Online Protection

[Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen für E-Mail-Nachrichten in Office 365](https://technet.microsoft.com/de-de/library/dn600323\(v=exchg.150\))

