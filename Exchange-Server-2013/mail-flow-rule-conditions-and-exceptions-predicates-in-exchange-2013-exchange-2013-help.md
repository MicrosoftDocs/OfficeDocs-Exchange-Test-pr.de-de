---
title: 'Transportregelbedingungen (Prädikate): Exchange 2013 Help'
TOCTitle: Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate)
ms:assetid: c918ea00-1e68-4b8b-8d51-6966b4432e2d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638183(v=EXCHG.150)
ms:contentKeyID: 50476721
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Transportregelbedingungen (Prädikate)

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-12-20_

Bedingungen und Ausnahmen in Nachrichtenflussregeln (auch als Transportregeln bekannt) identifizieren die Nachrichten, auf welche die Regel angewendet oder nicht angewendet wird. Wenn durch die Regel beispielsweise ein Haftungsausschluss zur Nachricht hinzufügt wird, können Sie die Regel so konfigurieren, dass sie nur auf Nachrichten angewendet wird, die bestimmte Wörter enthalten, auf Nachrichten, die von bestimmten Benutzern gesendete werden, oder auf alle Nachrichten mit Ausnahme derjenigen, die von Mitgliedern einer bestimmten Gruppe gesendet werden. Die Bedingungen und Ausnahmen in Nachrichtenflussregeln werden gemeinsam auch als *Prädikate* bezeichnet, da es für jede Bedingung eine entsprechende Ausnahme mit genau denselben Einstellungen und derselben Syntax gibt. Der einzigen Unterschied ist: Bedingungen geben die einzuschließenden Nachrichten an, während Ausnahmen auszuschließende Nachrichten angeben.

Die meisten Bedingungen und Ausnahmen haben eine Eigenschaft, die einen oder mehrere Werte erfordern. Beispielsweise erfordert die Bedingung **Der Absender lautet** die Angabe des Absenders der Nachricht. Einige Bedingungen weisen zwei Eigenschaften auf. Wenn Sie beispielsweise die Bedingung **Eine Nachrichtenkopfzeile enthält mindestens eines dieser Wörter** verwenden, muss eine Eigenschaft den Nachrichtenkopf und eine zweite Eigenschaft den zu suchenden Text im Nachrichtenkopf angeben. Einige Bedingungen oder Ausnahmen haben keine Eigenschaften. Beispielsweise sucht die Bedingung **Mindestens eine Anlage hat ausführbaren Inhalt** einfach nach Anlagen in Nachrichten, die ausführbaren Inhalt haben.

Weitere Informationen zu Nachrichtenflussregeln in Exchange Server 2013 finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md).

Weitere Informationen zu Bedingungen und Ausnahmen in e-Mail-Flussregeln in Exchange Online Protection oder Exchange Online finden Sie unter [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\)) oder [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj919234\(v=exchg.150\)).

## Bedingungen und Ausnahmen für Nachrichtenflussregeln auf Postfachservern

Die Tabellen in den folgenden Abschnitten wird beschrieben, die Bedingungen und Ausnahmen, die in der e-Mail-Flussregeln auf Postfachservern verfügbar sind. Die Eigenschaften sind im Abschnitt Eigenschaftentypen beschrieben.

Absender

Empfänger

Nachrichtenbetreff oder -text

Anlagen

Alle Empfänger

Nachrichten mit Typen vertraulicher Informationen, To- und Cc-Werte, Größe und Zeichensätze

Absender und Empfänger

Nachrichteneigenschaften

Nachrichtenkopfzeilen

**Hinweise:** 

  - Nach dem Auswählen einer Bedingung oder eine Ausnahme in der Exchange-Verwaltungskonsole (EAC) ist der Wert, der letztendlich im Feld **Diese Regel anwenden, wenn** oder **Außer, wenn** angezeigt wird, häufig anders (kürzer) als der ausgewählte Klickpfadwert. Wenn Sie zudem neue Regeln basierend auf einer Vorlage (eine gefilterte Liste von Szenarien) erstellen, können Sie häufig einen kurzen Bedingungsnamen auswählen anstatt dem vollständigen Klickpfad zu folgen. Die kurzen Namen und vollständigen Klickpfadwerte werden in der Spalte "EAC" in den Tabellen angezeigt.

  - Wenn Sie in der Exchange-Verwaltungskonsole **\[Auf alle Nachrichten anwenden\]** auswählen, können Sie keine anderen Bedingungen angeben. Das Äquivalent in der Exchange-Verwaltungsshell besteht darin, eine Regel ohne Angabe von Bedingungsparametern zu erstellen.

  - Die Einstellungen und Eigenschaften sind in Bedingungen und Ausnahmen gleich, daher werden in der Ausgabe des Cmdlet **Get-TransportRulePredicate** keine Ausnahmen separat aufgelistet. Darüber hinaus unterscheiden sich die Namen einiger der Prädikate, die von diesem Cmdlet zurückgegeben werden, von den entsprechenden Parameternamen. Ein Prädikat kann möglicherweise mehrere Parameter erfordern.

## Absender

Für Bedingungen und Ausnahmen, die die Adresse des Absenders überprüfen, können Sie festlegen, wo die Regel nach der Adresse des Absenders sucht.

Klicken Sie in der Exchange-Verwaltungskonsole im Abschnitt **Eigenschaften dieser Regel** auf **Absenderadresse in Nachricht vergleichen**. Beachten Sie, dass Sie möglicherweise benötigen auf **Weitere Optionen** klicken müssen, um diese Einstellung anzuzeigen. In der Exchange-Verwaltungsshelllautet der Parameter *SenderAddressLocation*. Die verfügbaren Werte sind:

  - **Kopfzeile**   Nur Absender in den Nachrichtenkopfzeilen auswerten (z. B. die Felder **From**, **Sender** oder **Reply-To**). Dies ist der Standardwert. So funktionierten Nachrichtenflussregeln vor dem Exchange 2013 kumulativen Update 1 (CU1).

  - **Umschlag**   Nur Absender aus dem Nachrichtenumschlag auswerten (der Wert **MAIL FROM**, der in der SMTP-Übermittlung verwendet wurde und in der Regel im Feld **Return-Path** gespeichert ist). Beachten Sie, dass die Nachrichtenumschlag-Suche nur für die folgenden Bedingungen (und die entsprechenden Ausnahmen) verfügbar ist:
    
      - **Der Absender ist** (*From*)
    
      - **Der Absender ist Mitglied von** (*FromMemberOf*)
    
      - **Die Absenderadresse enthält** (*FromAddressContainsWords*)
    
      - **Die Absenderadresse entspricht** (*FromAddressMatchesPatterns*)
    
      - **Die Domäne des Absenders ist** (*SenderDomainIs*)

  - **Kopfzeile oder Umschlag** (`HeaderOrEnvelope`) Absender in der Nachrichtenkopfzeile und dem Nachrichtenumschlag auswerten.


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Der Absender ist</strong></p>
<p><strong>Absender</strong> &gt; <strong>ist diese Person</strong></p></td>
<td><p><em>From</em></p>
<p><em>ExceptIfFrom</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, die durch die angegebenen Postfächer, E-Mail-Benutzer oder E-Mail-Kontakte innerhalb der Exchange Organisation gesendet werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Absender befindet sich in</strong></p>
<p><strong>Absender</strong> &gt; <strong>ist extern/intern</strong></p></td>
<td><p><em>FromScope</em></p>
<p><em>ExceptIfFromScope</em></p></td>
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Nachrichten, die entweder durch interne Absender oder externe Absender gesendet werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Absender ist Mitglied von</strong></p>
<p><strong>Absender</strong> &gt; <strong>ist Mitglied dieser Gruppe</strong></p></td>
<td><p><em>FromMemberOf</em></p>
<p><em>ExceptIfFromMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, die von einem Mitglied einer festgelegten Gruppe gesendet werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Absenderadresse enthält</strong></p>
<p><strong>Absender</strong> &gt; <strong>Adresse enthält eines dieser Wörter</strong></p></td>
<td><p><em>FromAddressContainsWords</em></p>
<p><em>ExceptIfFromAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, die die angegebenen Wörter in der E-Mail-Adresse des Absenders enthalten.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Absenderadresse entspricht</strong></p>
<p><strong>Absender</strong> &gt; <strong>Adresse entspricht jedem dieser Textmuster</strong></p></td>
<td><p><em>FromAddressMatchesPatterns</em></p>
<p><em>ExceptIfFromAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen die E-Mail-Adresse des Absenders Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die angegebenen Eigenschaften des Absenders enthalten eines dieser Wörter</strong></p>
<p><strong>Absender</strong> &gt; <strong>hat bestimmte Eigenschaften einschließlich eines dieser Wörter</strong></p></td>
<td><p><em>SenderADAttributeContainsWords</em></p>
<p><em>ExceptIfSenderADAttributeContainsWords</em></p></td>
<td><p>Erste Eigenschaft: <code>ADAttribute</code></p>
<p>Zweite Eigenschaft: <code>Words</code></p></td>
<td><p>Nachrichten, bei denen das angegebene Active DirectoryAttribut des Absenders eines der angegebenen Wörter enthält.</p>
<p>Beachten Sie, dass das Attribut <strong>Country</strong> den aus zwei Buchstaben bestehenden Ländercode (z. B. DE für Deutschland) erfordert.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die angegebenen Eigenschaften des Absenders entsprechen diesen Textmustern</strong></p>
<p><strong>Absender</strong> &gt; <strong>verfügt über bestimmte Eigenschaften, die diesen Textmustern entsprechen</strong></p></td>
<td><p><em>SenderADAttributeMatchesPatterns</em></p>
<p><em>ExceptIfSenderADAttributeMatchesPatterns</em></p></td>
<td><p>Erste Eigenschaft: <code>ADAttribute</code></p>
<p>Zweite Eigenschaft: <code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das angegebene Active Directory-Attribut des Absenders Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Absender hat den Richtlinientipp außer Kraft gesetzt</strong></p>
<p><strong>Der Absender</strong> &gt; <strong>hat den Richtlinientipp außer Kraft gesetzt</strong></p></td>
<td><p><em>HasSenderOverride</em></p>
<p><em>ExceptIfHasSenderOverride</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, bei denen der Absender ausgewählt hat, eine Data Loss Prevention (DLP)-Richtlinie außer Kraft zu setzen. Weitere Informationen zu DLP-Richtlinien finden Sie unter <a href="technical-overview-of-dlp-data-loss-prevention-in-exchange.md">Verhinderung von Datenverlust</a>.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Absender-IP-Adresse befindet sich im Bereich</strong></p>
<p><strong>Der Absender</strong> &gt; <strong>IP-Adresse ist in keinem dieser Bereiche oder stimmt mit keinem Bereich völlig überein</strong></p></td>
<td><p><em>SenderIPRanges</em></p>
<p><em>ExceptIfSenderIPRanges</em></p></td>
<td><p><code>IPAddressRanges</code></p></td>
<td><p>Nachrichten, in denen die IP-Adresse des Absenders der angegebenen IP-Adresse entsprecht oder innerhalb des angegebenen IP-Adressbereichs liegt.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Domäne des Absenders ist</strong></p>
<p><strong>Die Domäne</strong> &gt; <strong>es Absenders ist</strong></p></td>
<td><p><em>SenderDomainIs</em></p>
<p><em>ExceptIfSenderDomainIs</em></p></td>
<td><p><code>DomainName</code></p></td>
<td><p>Nachrichten, bei denen die Domäne der E-Mail-Adresse des Absenders dem angegebenen Wert entspricht.</p>
<p>Wenn Sie nach Absenderdomänen suchen müssen, welche die angegebene Domäne <em>enthalten</em> (z. B. eine Unterdomäne einer Domäne), verwenden Sie die Bedingung <strong>Die Absenderadresse entspricht</strong> (<em>FromAddressMatchesPatterns</em>), und geben Sie die Domäne mit folgender Syntax an: <code>'@domain\.com$'</code>.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Empfänger


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Der Empfänger ist</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>ist diese Person</strong></p></td>
<td><p><em>SentTo</em></p>
<p><em>ExceptIfSentTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, bei denen es sich bei einem der Empfänger um das angegebene Postfach, den E-Mail-Benutzer oder den E-Mail-Kontakt in der Organisation handelt. Die Empfänger können in den Feldern Exchange, <strong>To</strong>, <strong>Cc</strong> oder <strong>Bcc</strong> der Nachricht angegeben werden.</p>
<p><strong>Hinweis:</strong> Sie können keine Verteilergruppen oder E-Mail-aktivierte Sicherheitsgruppen angeben. Wenn Sie Aktionen für Nachrichten ausführen müssen, die an eine Gruppe gesendet werden, verwenden Sie stattdessen die Bedingung <strong>Feld „An&amp;quot; enthält</strong> (<em>AnyOfToHeader</em>).</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Empfänger befindet sich in</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>ist extern/extern</strong></p></td>
<td><p><em>SentToScope</em></p>
<p><em>ExceptIfSentToScope</em></p></td>
<td><p><code>UserScopeTo</code></p></td>
<td><p>Nachrichten, die an interne Empfänger, externe Empfänger, externe Empfänger in Partnerorganisationen oder externe Empfänger in Nicht-Partner-Organisationen gesendet werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Empfänger ist Mitglied von</strong></p>
<p><strong>Der Empfänger</strong> &gt; <strong>ist Mitglied dieser Gruppe</strong></p></td>
<td><p><em>SentToMemberOf</em></p>
<p><em>ExceptIfSentToMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, die Empfänger enthalten, die Mitglieder der angegebenen Gruppe sind. Die Gruppe kann in den Feldern <strong>To</strong>, <strong>Cc</strong> oder <strong>Bcc</strong> der Nachricht sein.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Empfängeradresse enthält</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>Adresse enthält eines dieser Wörter</strong></p></td>
<td><p><em>RecipientAddressContainsWords</em></p>
<p><em>ExceptIfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, die die angegebenen Wörter in der E-Mail-Adresse des Empfängers enthalten.</p>
<p><strong>Hinweis:</strong> Diese Bedingung berücksichtigt keine Nachrichten, die an Proxyadressen des Empfängers gesendet werden. Es werden nur Nachrichten berücksichtigt, die an die primäre E-Mail-Adresse des Empfängers gesendet werden.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Adresse des Empfängers entspricht</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>Adresse entspricht jedem dieser Textmuster</strong></p></td>
<td><p><em>RecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen die E-Mail-Adresse des Empfängers Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p>
<p><strong>Hinweis:</strong> Diese Bedingung berücksichtigt keine Nachrichten, die an Proxyadressen des Empfängers gesendet werden. Es werden nur Nachrichten berücksichtigt, die an die primäre E-Mail-Adresse des Empfängers gesendet werden.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die vom Empfänger angegebenen Eigenschaften enthalten eines dieser Wörter</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>hat bestimmte Eigenschaften einschließlich eines dieser Wörter</strong></p></td>
<td><p><em>RecipientADAttributeContainsWords</em></p>
<p><em>ExceptIfRecipientADAttributeContainsWords</em></p></td>
<td><p>Erste Eigenschaft: <code>ADAttribute</code></p>
<p>Zweite Eigenschaft: <code>Words</code></p></td>
<td><p>Nachrichten, bei denen das angegebene Active Directory-Attribut eines Empfängers eines der angegebenen Wörter enthält.</p>
<p>Beachten Sie, dass das Attribut <strong>Country</strong> den aus zwei Buchstaben bestehenden Ländercode (z. B. DE für Deutschland) erfordert.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die angegebenen Eigenschaften des Empfängers entsprechen diesen Textmustern</strong></p>
<p><strong>Empfänger</strong> &gt; <strong>verfügt über bestimmte Eigenschaften, die diesen Textmustern entsprechen</strong></p></td>
<td><p><em>RecipientADAttributeMatchesPatterns</em></p>
<p><em>ExceptIfRecipientADAttributeMatchesPatterns</em></p></td>
<td><p>Erste Eigenschaft: <code>ADAttribute</code></p>
<p>Zweite Eigenschaft: <code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das angegebene Active Directory-Attribut des Empfängers Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Domäne des Empfängers ist</strong></p>
<p><strong>Die Domäne</strong> &gt; <strong>es Empfängers ist</strong></p></td>
<td><p><em>RecipientDomainIs</em></p>
<p><em>ExceptIfRecipientDomainIs</em></p></td>
<td><p><code>DomainName</code></p></td>
<td><p>Nachrichten, bei denen die Domäne der E-Mail-Adresse des Empfängers dem angegebenen Wert entspricht.</p>
<p>Wenn Sie nach Empfängerdomänen suchen müssen, welche die angegebene Domäne <em>enthalten</em> (z. B. eine Unterdomäne einer Domäne), verwenden Sie die Bedingung <strong>Die Empfängeradresse entspricht</strong> (<em>RecipientAddressMatchesPatterns</em>), und geben Sie die Domäne mit folgender Syntax an: <code>'@domain\.com$'</code>.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichtenbetreff oder -text


> [!NOTE]
> Die Suche nach Wörtern oder Textmustern im Betreff oder anderen Kopfzeilenfeldern in der Nachricht tritt <EM>nach</EM> der Decodierung der Nachricht aus der MIME-Inhaltsübertragungscodierungsmethode ein, die für die Übermittlung der binären Nachricht zwischen SMTP-Servern im ASCII-Text verwendet wurde. Sie können keine Bedingungen oder Ausnahmen für die Suche nach Rohwerten (in der Regel Base64-codiert) im Betreff oder in anderen Kopfzeilenfeldern in Nachrichten verwenden.




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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Der Betreff oder Nachrichtentext enthält</strong></p>
<p><strong>Betreff oder Textkörper</strong> &gt; <strong>Betreff oder Nachrichtentext enthält mindestens eines dieser Wörter</strong></p></td>
<td><p><em>SubjectOrBodyContainsWords</em></p>
<p><em>ExceptIfSubjectOrBodyContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, deren Feld <strong>Subject</strong> oder Nachrichtentext die angegebenen Wörter enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Betreff oder Nachrichtentext entspricht</strong></p>
<p><strong>Betreff oder Textkörper</strong> &gt; <strong>Betreff oder Nachrichtentext entspricht diesen Textmustern</strong></p></td>
<td><p><em>SubjectOrBodyMatchesPatterns</em></p>
<p><em>ExceptIfSubjectOrBodyMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>Subject</strong> oder der Nachrichtentext Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Betreff enthält</strong></p>
<p><strong>Betreff oder Textkörper</strong> &gt; <strong>Betreff enthält eines der folgenden Wörter</strong></p></td>
<td><p><em>SubjectContainsWords</em></p>
<p><em>ExceptIfSubjectContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, deren Feld <strong>Subject</strong> die angegebenen Wörter enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Betreff entspricht</strong></p>
<p><strong>Betreff oder Textkörper</strong> &gt; <strong>Betreff entspricht diesen Textmustern</strong></p></td>
<td><p><em>SubjectMatchesPatterns</em></p>
<p><em>ExceptIfSubjectMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>Subject</strong> Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Anlagen

Weitere Informationen dazu, wie e-Mail-Flussregeln von Nachrichtenanlagen finden Sie unter [Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md).


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Inhalt mindestens einer Anlage enthält</strong></p>
<p><strong>Ein Anlageninhalt</strong> &gt; <strong>enthält eines dieser Wörter</strong></p></td>
<td><p><em>AttachmentContainsWords</em></p>
<p><em>ExceptIfAttachmentContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, bei denen eine Anlage die angegebenen Wörter enthält.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Inhalt mindestens einer Anlage entspricht</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>Inhalt stimmt mit diesen Textmustern überein</strong></p></td>
<td><p><em>AttachmentMatchesPatterns</em></p>
<p><em>ExceptIfAttachmentMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen eine Anlage Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p>
<p><strong>Hinweis:</strong> Nur die ersten 150 Kilobyte (KB) der Anlagen werden durchsucht.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Inhalt keiner Anlage konnte überprüft werden</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>Inhalt kann nicht überprüft werden</strong></p></td>
<td><p><em>AttachmentIsUnsupported</em></p>
<p><em>ExceptIfAttachmentIsUnsupported</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, in dem eine Anlage ist nicht vom Exchange systemintern erkannt und der erforderliche IFilter ist nicht auf dem Postfachserver installiert. Weitere Informationen finden Sie unter <a href="register-filter-pack-ifilters-with-exchange-2013-exchange-2013-help.md">Registrieren von Filterpaket-IFiltern für Exchange 2013</a>.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Der Dateiname mindestens einer Anlage entspricht</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>einen Dateinamen hat, der diesen Textmustern entspricht</strong></p></td>
<td><p><em>AttachmentNameMatchesPatterns</em></p>
<p><em>ExceptIfAttachmentNameMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen der Dateiname einer Anlage Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Dateierweiterung mindestens einer Anlage entspricht</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>eine Dateierweiterung hat, die diese Wörter enthält</strong></p></td>
<td><p><em>AttachmentExtensionMatchesWords</em></p>
<p><em>ExceptIfAttachmentExtensionMatchesWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, bei denen die Dateierweiterung einer Anlage einem der angegebenen Wörter entspricht.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Eine Anlage ist größer als oder gleich</strong></p>
<p><strong>Mindestens eine Anlage &gt; Größe ist größer oder gleich</strong></p></td>
<td><p><em>AttachmentSizeOver</em></p>
<p><em>ExceptIfAttachmentSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Nachrichten, bei denen eine Anlage größer oder gleich dem angegebenen Wert ist.</p>
<p>In der Exchange-Verwaltungskonsole können Sie nur die Größe in Kilobyte (KB) angeben.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Nachricht wurde nicht vollständig überprüft</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>Überprüfung nicht abgeschlossen wurde</strong></p></td>
<td><p><em>AttachmentProcessingLimitExceeded</em></p>
<p><em>ExceptIfAttachmentProcessingLimitExceeded</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, bei denen das Regelmodul das Prüfen der Anlagen nicht abschließen konnte. Sie können diese Bedingung zum Erstellen von Regeln verwenden, die zusammenarbeiten, um Nachrichten zu ermitteln und zu verarbeiten, deren Inhalt nicht vollständig überprüft werden konnte.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Mindestens eine Anlage hat ausführbaren Inhalt</strong></p>
<p><strong>Mindestens eine Anlage</strong> &gt; <strong>hat ausführbaren Inhalt</strong></p></td>
<td><p><em>AttachmentHasExecutableContent</em></p>
<p><em>ExceptIfAttachmentHasExecutableContent</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, bei denen eine Anlage eine ausführbare Datei ist. Das System untersucht die Dateieigenschaften anstatt sich auf die Dateierweiterung zu verlassen.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Jede Anlage ist kennwortgeschützt</strong></p>
<p><strong>Jede Anlage</strong> &gt; <strong>ist kennwortgeschützt</strong></p></td>
<td><p><em>AttachmentIsPasswordProtected</em></p>
<p><em>ExceptIfAttachmentIsPasswordProtected</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, bei denen eine Anlage kennwortgeschützt ist (und daher nicht überprüft werden kann). Die Kennworterkennung funktioniert nur bei Office-Dokumenten und ZIP-Dateien.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Alle Empfänger

Die Bedingungen und Ausnahmen in diesem Abschnitt bieten eine einzigartige Funktion, die sich auf *alle* Empfänger auswirkt, wenn die Nachricht mindestens einen der angegebenen Empfänger enthält. Nehmen wir z. B. an, Sie haben eine Regel, die Nachrichten ablehnt. Wenn Sie eine Empfängerbedingung aus dem Abschnitt Empfänger verwenden, wird die Nachricht nur bei diesen angegebenen Empfängern abgelehnt. Wenn die Regel beispielsweise den angegebenen Empfänger in einer Nachricht findet, die Nachricht aber fünf weitere Empfänger enthält. Die Nachricht wird für diesen einen Empfänger abgelehnt, aber an die fünf anderen Empfänger übermittelt.

Wenn Sie eine Empfängerbedingung aus diesem Abschnitt hinzufügen, wird die gleiche Nachricht für den erkannten Empfänger und die fünf anderen Empfänger abgelehnt.

Umgekehrt ist es so, dass eine Empfängerausnahme aus diesem Abschnitt *verhindert*, dass die Regelaktion auf *alle* Empfänger der Nachricht angewendet wird, nicht nur für die erkannten Empfänger.

**Hinweis:**  Diese Bedingung berücksichtigt keine Nachrichten, die an Proxyadressen des Empfängers gesendet werden. Es werden nur Nachrichten berücksichtigt, die an die primäre E-Mail-Adresse des Empfängers gesendet werden.


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Mindestens eine Empfängeradresse enthält</strong></p>
<p><strong>Mindestens ein Empfänger</strong> &gt; <strong>Adresse enthält eines dieser Wörter</strong></p></td>
<td><p><em>AnyOfRecipientAddressContainsWords</em></p>
<p><em>ExceptIfAnyOfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten mit den angegebenen Wörtern in den Feldern <strong>To</strong>, <strong>Cc</strong>oder <strong>Bcc</strong> der Nachricht.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Mindestens eine Adresse des Empfängers entspricht</strong></p>
<p><strong>Mindestens ein Empfänger</strong> &gt; <strong>Adresse entspricht jedem dieser Textmuster</strong></p></td>
<td><p><em>AnyOfRecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfAnyOfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>To</strong>, <strong>Cc</strong> oder <strong>Bcc</strong> Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichten mit Typen vertraulicher Informationen, To- und Cc-Werte, Größe und Zeichensätze

Die Bedingungen in diesem Abschnitt, die nach Werten in den Feldern **To** und **Cc** suchen, verhalten sich wie die Bedingungen im Abschnitt Alle Empfänger (*alle* Empfänger der Nachricht sind von der Regel betroffen, nicht nur die erkannten Empfänger).

**Hinweis:**  Diese Bedingung berücksichtigt keine Nachrichten, die an Proxyadressen des Empfängers gesendet werden. Es werden nur Nachrichten berücksichtigt, die an die primäre E-Mail-Adresse des Empfängers gesendet werden.


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Die Nachricht enthält vertrauliche Informationen</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>enthält einen dieser Typen vertraulicher Informationen</strong>.</p></td>
<td><p><em>MessageContainsDataClassifications</em></p>
<p><em>ExceptIfMessageContainsDataClassifications</em></p></td>
<td><p><code>SensitiveInformationTypes</code></p></td>
<td><p>Nachrichten, die vertraulichen Informationen enthalten, wie in den Data Loss Prevention (DLP)-Richtlinien definiert.</p>
<p>Diese Bedingung ist für Regeln erforderlich, die die Aktion <strong>Absender mit Richtlinientipp benachrichtigen</strong> (<em>NotifySender</em>) verwenden.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Das Feld &quot;An&quot; enthält</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>Feld &quot;An&quot; enthält diese Person</strong></p></td>
<td><p><em>AnyOfToHeader</em></p>
<p><em>ExceptIfAnyOfToHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>To</strong> einen oder mehrere der angegebenen Empfänger enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Das Feld &quot;An&quot; enthält ein Mitglied von</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>das Feld &quot;An&quot; enthält ein Mitglied dieser Gruppe</strong></p></td>
<td><p><em>AnyOfToHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfToHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>To</strong> einen Empfänger enthält, der Mitglied der angegebenen Gruppe ist.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Das Feld &quot;Cc&quot; enthält</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>Feld &quot;Cc&quot; enthält diese Person</strong></p></td>
<td><p><em>AnyOfCcHeader</em></p>
<p><em>ExceptIfAnyOfCcHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>Cc</strong> einen oder mehrere der angegebenen Empfänger enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Das Feld &quot;Cc&quot; enthält ein Mitglied von</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>enthält ein Mitglied dieser Gruppe</strong></p></td>
<td><p><em>AnyOfCcHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfCcHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>Cc</strong> einen Empfänger enthält, der Mitglied der angegebenen Gruppe ist.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Das Feld &quot;An&quot; oder &quot;Cc&quot; enthält</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>Feld &quot;An&quot; oder &quot;Cc&quot; enthält diese Person</strong></p></td>
<td><p><em>AnyOfToCcHeader</em></p>
<p><em>ExceptIfAnyOfToCcHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>To</strong> oder <strong>Cc</strong> einen oder mehrere der angegebenen Empfänger enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Das Feld &quot;An&quot; oder &quot;Cc&quot; enthält ein Mitglied von</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>das Feld &quot;An&quot; oder &quot;Cc&quot; enthält ein Mitglied dieser Gruppe</strong></p></td>
<td><p><em>AnyOfToCcHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfToCcHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, deren Feld <strong>To</strong> oder <strong>Cc</strong> einen Empfänger enthält, der Mitglied der angegebenen Gruppe ist.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Nachrichtengröße ist größer als oder gleich</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>Größe ist größer als oder gleich</strong></p></td>
<td><p><em>MessageSizeOver</em></p>
<p><em>ExceptIfMessageSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Nachrichten, deren Gesamtgröße (Nachricht sowie Anlagen) größer oder gleich dem angegebenen Wert ist.</p>
<p>In der Exchange-Verwaltungskonsole können Sie nur die Größe in Kilobyte (KB) angeben.</p>
<p><strong>Hinweis:</strong> Grenzwerte für die Nachrichtengröße für Postfächer werden vor E-Mail-Flussregeln ausgewertet. Eine Nachricht, die für ein Postfach zu groß ist, wird zurückgewiesen, bevor eine Regel mit dieser Bedingung auf diese Nachricht angewendet wird.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Name des Zeichensatzes der Nachricht enthält beliebige dieser Wörter</strong></p>
<p><strong>Die Nachricht</strong> &gt; <strong>Name des Zeichensatzes enthält beliebige dieser Wörter</strong></p></td>
<td><p><em>ContentCharacterSetContainsWords</em></p>
<p><em>ExceptIfContentCharacterSetContainsWords</em></p></td>
<td><p><code>CharacterSets</code></p></td>
<td><p>Nachrichten, die beliebige der angegebenen Zeichensatznamen enthalten.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Absender und Empfänger


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Der Absender ist einer der Empfänger</strong></p>
<p><strong>Der Absender und der Empfänger</strong> &gt; <strong>die Beziehung des Absenders zum ist</strong></p></td>
<td><p><em>SenderManagementRelationship</em></p>
<p><em>ExceptIfSenderManagementRelationship</em></p></td>
<td><p><code>ManagementRelationship</code></p></td>
<td><p>Nachrichten, bei denen entweder der Absender der Vorgesetzte eines Empfängers ist oder bei denen der Absender den Empfänger als Vorgesetzten hat.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Nachricht wird zwischen Mitgliedern dieser Gruppen übermittelt</strong></p>
<p><strong>Der Absender und der Empfänger</strong> &gt; <strong>die Nachricht wird zwischen Mitgliedern dieser Gruppen übermittelt</strong></p></td>
<td><p><em>BetweenMemberOf1</em> und <em>BetweenMemberOf2</em></p>
<p><em>ExceptIfBetweenMemberOf1</em> und <em>ExceptIfBetweenMemberOf2</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Nachrichten, die zwischen Mitgliedern der angegebenen Gruppen übermittelt werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Der Vorgesetzte des Absenders oder Empfängers ist</strong></p>
<p><strong>Der Absender und der Empfänger</strong> &gt; <strong>der Vorgesetzte des Absenders oder Empfängers ist diese Person</strong></p></td>
<td><p><em>ManagerForEvaluatedUser</em> und <em>ManagerAddress</em></p>
<p><em>ExceptIfManagerForEvaluatedUser</em> und <em>ExceptIfManagerAddress</em></p></td>
<td><p>Erste Eigenschaft: <code>EvaluatedUser</code></p>
<p>Zweite Eigenschaft: <code>Addresses</code></p></td>
<td><p>Nachrichten, bei denen entweder ein bestimmter Benutzer der Vorgesetzte des Absenders ist oder bei denen ein bestimmten Benutzer der Vorgesetzte eines Empfängers ist.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Absender- und Empfängereigenschaft wird verglichen als</strong></p>
<p><strong>Der Absender und der Empfänger</strong> &gt; <strong>die Absender- und Empfängereigenschaft wird verglichen als</strong>.</p></td>
<td><p><em>ADAttributeComparisonAttribute</em> und <em>ADComparisonOperator</em></p>
<p><em>ExceptIfADAttributeComparisonAttribute</em> und <em>ExceptIfADComparisonOperator</em></p></td>
<td><p>Erste Eigenschaft: <code>ADAttribute</code></p>
<p>Zweite Eigenschaft: <code>Evaluation</code></p></td>
<td><p>Nachrichten, bei denen das angegebene Active Directory-Attribut für den Absender und den Empfänger übereinstimmt oder nicht übereinstimmt.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichteneigenschaften


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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Der Nachrichttyp ist</strong></p>
<p><strong>Nachrichteneigenschaften</strong> &gt; <strong>Nachrichtentyp einschließen</strong></p></td>
<td><p><em>MessageTypeMatches</em></p>
<p><em>ExceptIfMessageTypeMatches</em></p></td>
<td><p><code>MessageType</code></p></td>
<td><p>Nachrichten vom angegebenen Typ.</p>

> [!NOTE]
> Wenn Outlook oder Outlook Web App so konfiguriert ist, dass eine Nachricht weitergeleitet wird, wird die Eigenschaft <STRONG>ForwardingSmtpAddress</STRONG> der Nachricht hinzugefügt. Der Nachrichtentyp wird nicht in <CODE>AutoForward</CODE> geändert.


</td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Nachricht ist klassifiziert als</strong></p>
<p><strong>Nachrichteneigenschaften</strong> &gt; <strong>diese Klassifikation einschließen</strong></p></td>
<td><p><em>HasClassification</em></p>
<p><em>ExceptIfHasClassification</em></p></td>
<td><p><code>MessageClassification</code></p></td>
<td><p>Nachrichten mit der angegebenen Klassifikation. Hierbei handelt es sich um eine benutzerdefinierte Nachrichtenklassifikation, die Sie in Ihrer Organisation mit dem Cmdlet <strong>New-MessageClassification</strong> erstellen können.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Die Nachricht ist nicht mit einer Klassifikation markiert</strong></p>
<p><strong>Nachrichteneigenschaften</strong> &gt; <strong>enthalten keine Klassifikation</strong></p></td>
<td><p><em>HasNoClassification</em></p>
<p><em>ExceptIfHasNoClassification</em></p></td>
<td><p>N/V</p></td>
<td><p>Nachrichten, die nicht über eine Nachrichtenklassifikation verfügen.</p></td>
<td><p>Exchange 2010 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Die Nachricht hat eine SCL-Bewertung größer oder gleich</strong></p>
<p><strong>Nachrichteneigenschaften</strong> &gt; <strong>mit einer SCL-Bewertung größer oder gleich</strong></p></td>
<td><p><em>SCLOver</em></p>
<p><em>ExceptIfSCLOver</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Nachrichten, deren SCL-Bewertung (Spam Confidence Level) mit dem angegebenen Wert übereinstimmt bzw. diesen Wert überschreitet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><strong>Für die Nachricht ist eine Wichtigkeit festgelegt von</strong></p>
<p><strong>Nachrichteneigenschaften</strong> &gt; <strong>Wichtigkeitsstufe einschließen</strong></p></td>
<td><p><em>WithImportance</em></p>
<p><em>ExceptIfWithImportance</em></p></td>
<td><p><code>Importance</code></p></td>
<td><p>Nachrichten mit der angegebenen Wichtigkeitsstufe.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichtenkopfzeilen


> [!NOTE]
> Die Suche nach Wörtern oder Textmustern im Betreff oder anderen Kopfzeilenfeldern in der Nachricht tritt <EM>nach</EM> der Decodierung der Nachricht aus der MIME-Inhaltsübertragungscodierungsmethode ein, die für die Übermittlung der binären Nachricht zwischen SMTP-Servern im ASCII-Text verwendet wurde. Sie können keine Bedingungen oder Ausnahmen für die Suche nach Rohwerten (in der Regel Base64-codiert) im Betreff oder in anderen Kopfzeilenfeldern in Nachrichten verwenden.




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
<th>Bedingung oder Ausnahme in der Exchange-Verwaltungskonsole</th>
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ein Nachrichtenkopf enthält</strong></p>
<p><strong>Eine Nachrichtenkopfzeile</strong> &gt; <strong>enthält mindestens eines dieser Wörter</strong></p></td>
<td><p><em>HeaderContainsMessageHeader</em> und <em>HeaderContainsWords</em></p>
<p><em>ExceptIfHeaderContainsMessageHeader</em> und <em>ExceptIfHeaderContainsWords</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>Words</code></p></td>
<td><p>Nachrichten, die das angegebene Header-Feld enthalten, und der Wert des Header-Felds enthält die angegebenen Wörter.</p>
<p>Der Name des Header-Felds und der Wert des Header-Felds werden immer zusammen verwendet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><strong>Ein Nachrichtenkopf entspricht</strong></p>
<p><strong>A message header</strong> &gt; <strong>matches these text patterns</strong></p></td>
<td><p><em>HeaderMatchesMessageHeader</em> und <em>HeaderMatchesPatterns</em></p>
<p><em>ExceptIfHeaderMatchesMessageHeader</em> und <em>ExceptIfHeaderMatchesPatterns</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>Patterns</code></p></td>
<td><p>Nachrichten, die das angegebene Header-Feld enthalten, und der Wert des Header-Felds enthält die angegebenen regulären Ausdrücke.</p>
<p>Der Name des Header-Felds und der Wert des Header-Felds werden immer zusammen verwendet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Bedingungen und Ausnahmen für Nachrichtenflussregeln auf Edge-Transport-Servern

Die Bedingungen und Ausnahmen, die in den Nachrichtenflussregeln auf Edge-Transport-Servern zur Verfügung stehen, sind nur ein kleiner Teil von dem, was auf Postfachservern verfügbar ist. Es gibt keine Exchange-Verwaltungskonsole auf Edge-Transport-Servern. Daher können Sie nur die Nachrichtenflussregeln in der Exchange-Verwaltungsshell auf dem lokalen Edge-Transport-Server verwalten. Die Bedingungen und Ausnahmen werden in der folgenden Tabelle beschrieben. Die Typen von Eigenschaften sind im Abschnitt Eigenschaftentypen beschrieben.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Bedingungs- und Ausnahmeparameter in der Exchange-Verwaltungsshell</th>
<th>Eigenschaftentyp</th>
<th>Beschreibung</th>
<th>Verfügbar in</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AnyOfRecipientAddressContainsWords</em></p>
<p><em>ExceptIfAnyOfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten mit den angegebenen Wörtern in den Feldern <strong>To</strong>, <strong>Cc</strong>oder <strong>Bcc</strong>.</p>
<p>Wenn eine Nachricht den angegebenen Empfänger enthält, wird die Regelaktion auf <em>alle</em> Empfänger der Nachricht angewendet (oder nicht angewendet). Die Nachricht wird beispielsweise für alle Empfänger der Nachricht abgelehnt, nicht nur für den angegebenen Empfänger.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>AnyOfRecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfAnyOfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>To</strong>, <strong>Cc</strong> oder <strong>Bcc</strong> Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p>
<p>Wenn eine Nachricht den angegebenen Empfänger enthält, wird die Regelaktion auf <em>alle</em> Empfänger der Nachricht angewendet (oder nicht angewendet). Die Nachricht wird beispielsweise für alle Empfänger der Nachricht abgelehnt, nicht nur für den angegebenen Empfänger.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>AttachmentSizeOver</em></p>
<p><em>ExceptIfAttachmentSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Nachrichten mit Anlagen, bei denen eine Anlage größer oder gleich dem angegebenen Wert ist.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>FromAddressContainsWords</em></p>
<p><em>ExceptIfFromAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, die die angegebenen Wörter in der E-Mail-Adresse des Absenders enthalten.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>FromAddressMatchesPatterns</em></p>
<p><em>ExceptIfFromAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen die E-Mail-Adresse des Absenders Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>FromScope</em></p>
<p><em>ExceptIfFromScope</em></p></td>
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Nachrichten, die entweder durch interne Absender oder externe Absender gesendet werden.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>HeaderContainsMessageHeader</em> und <em>HeaderContainsWords</em></p>
<p><em>ExceptIfHeaderContainsMessageHeader</em> und <em>ExceptIfHeaderContainsWords</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>Words</code></p></td>
<td><p>Nachrichten, die das angegebene Header-Feld enthalten, und der Wert des Header-Felds enthält die angegebenen Wörter.</p>
<p>Der Name des Header-Felds und der Wert des Header-Felds werden immer zusammen verwendet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>HeaderMatchesMessageHeader</em> und <em>HeaderMatchesPatterns</em></p>
<p><em>ExceptIfHeaderMatchesMessageHeader</em> und <em>ExceptIfHeaderMatchesPatterns</em></p></td>
<td><p>Erste Eigenschaft: <code>MessageHeaderField</code></p>
<p>Zweite Eigenschaft: <code>Patterns</code></p></td>
<td><p>Nachrichten, die das angegebene Header-Feld enthalten, und der Wert des Header-Felds enthält die angegebenen regulären Ausdrücke.</p>
<p>Der Name des Header-Felds und der Wert des Header-Felds werden immer zusammen verwendet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>MessageSizeOver</em></p>
<p><em>ExceptIfMessageSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Nachrichten, deren Gesamtgröße (Nachricht sowie Anlagen) größer oder gleich dem angegebenen Wert ist.</p></td>
<td><p>Exchange 2013 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>SCLOver</em></p>
<p><em>ExceptIfSCLOver</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Nachrichten, deren SCL-Bewertung mit dem angegebenen Wert übereinstimmt bzw. diesen Wert überschreitet.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>SubjectContainsWords</em></p>
<p><em>ExceptIfSubjectContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten mit den angegebenen Wörtern im Feld <strong>Subject</strong>.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>SubjectMatchesPatterns</em></p>
<p><em>ExceptIfSubjectMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>Subject</strong> Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="odd">
<td><p><em>SubjectOrBodyContainsWords</em></p>
<p><em>ExceptIfSubjectOrBodyContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Nachrichten, deren Feld <strong>Subject</strong> oder Nachrichtentext die angegebenen Wörter enthält.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
<tr class="even">
<td><p><em>SubjectOrBodyMatchesPatterns</em></p>
<p><em>ExceptIfSubjectOrBodyMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Nachrichten, bei denen das Feld <strong>Subject</strong> oder der Nachrichtentext Textmuster enthält, die mit dem angegebenen regulären Ausdruck übereinstimmen.</p></td>
<td><p>Exchange 2007 oder höher</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Eigenschaftentypen

Die in Bedingungen und Ausnahmen verwendeten Eigenschaftentypen werden in der folgenden Tabelle beschrieben.


> [!NOTE]
> Wenn die Eigenschaft eine Zeichenfolge ist, sind nachfolgende Leerzeichen nicht zulässig.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaftentyp</th>
<th>Gültige Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>ADAttribute</code></p></td>
<td><p>Wählen Sie aus einer vordefinierten Liste von Active Directory-Attributen aus.</p></td>
<td><p>UNRESOLVED_TOKENBLOCK_VAL(PD_Transport_Rules_ADAttributes_Snippet)</p>
<p>Trennen Sie in der Exchange-Verwaltungskonsole die Werte durch Kommata, um mehrere Wörter oder Textmuster für das gleiche Attribut anzugeben. Der Wert <strong>San Francisco, Palo Alto</strong> für das Attribut <strong>Stadt</strong> sucht beispielsweise nach &quot;Stadt entspricht San Francisco&quot; oder &quot;Stadt entspricht Palo Alto&quot;.</p>
<p>Verwenden Sie in der Exchange-Verwaltungsshell die Syntax <code>&quot;AttributeName1:Value1,Value 2 with spaces,Value3...&quot;,&quot;AttributeName2:Word4,Value 5 with spaces,Value6...&quot;</code>, wobei <code>Value</code> das Wort oder Textmuster ist, das Sie abgleichen möchten.</p>
<p>Zum Beispiel <code>&quot;City:San Francisco,Palo Alto&quot;</code> oder<code>&quot;City:San Francisco,Palo Alto&quot;</code>, <code>&quot;Department:Sales,Finance&quot;</code> .</p>
<p>Wenn Sie mehrere Attribute oder mehrere Werte für das gleiche Attribut angeben, wird der Operator <strong>or</strong> verwendet. Verwenden Sie keine Werte mit voran- oder nachgestellten Leerzeichen.</p>
<p>Beachten Sie, dass das Attribut <strong>Country</strong> den aus zwei Buchstaben bestehenden ISO 3166-1-Ländercode (z. B. DE für Deutschland) erfordert. Informationen zur Suche nach Werten finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=331680">https://go.microsoft.com/fwlink/p/?LinkId=331680</a>.</p></td>
</tr>
<tr class="even">
<td><p><code>Addresses</code></p></td>
<td><p>Exchange Empfänger</p></td>
<td><p>Je nach Art der Bedingung oder Ausnahme können Sie möglicherweise ein beliebiges E-Mail-aktiviertes Objekt in der Organisation (z. B. empfängerbezogene Bedingungen) angeben, oder Sie müssen sich möglicherweise auf einen bestimmten Objekttyp beschränken (z. B. Gruppen für Gruppenmitgliedschaftsbedingungen). Zudem kann es sein, dass die Bedingung oder Ausnahme einen Wert erfordert oder mehrere Werte zulässt.</p>
<p>Trennen Sie in der Exchange-Verwaltungsshell die einzelnen Werte durch Kommata.</p>
<p><strong>Hinweis:</strong> Diese Bedingung berücksichtigt keine Nachrichten, die an Proxyadressen des Empfängers gesendet werden. Es werden nur Nachrichten berücksichtigt, die an die primäre E-Mail-Adresse des Empfängers gesendet werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>CharacterSets</code></p></td>
<td><p>Array von Zeichensatznamen</p></td>
<td><p>Ein oder mehrere Inhaltszeichensätze, die in einer Nachricht vorhanden sind. Beispiel:</p>
<ul>
<li><p><code>Arabic/iso-8859-6</code></p></li>
<li><p><code>Chinese/big5</code></p></li>
<li><p><code>Chinese/euc-cn</code></p></li>
<li><p><code>Chinese/euc-tw</code></p></li>
<li><p><code>Chinese/gb2312</code></p></li>
<li><p><code>Chinese/iso-2022-cn</code></p></li>
<li><p><code>Cyrillic/iso-8859-5</code></p></li>
<li><p><code>Cyrillic/koi8-r</code></p></li>
<li><p><code>Cyrillic/windows-1251</code></p></li>
<li><p><code>Greek/iso-8859-7</code></p></li>
<li><p><code>Hebrew/iso-8859-8</code></p></li>
<li><p><code>Japanese/euc-jp</code></p></li>
<li><p><code>Japanese/iso-022-jp</code></p></li>
<li><p><code>Japanese/shift-jis</code></p></li>
<li><p><code>Korean/euc-kr</code></p></li>
<li><p><code>Korean/johab</code></p></li>
<li><p><code>Korean/ks_c_5601-1987</code></p></li>
<li><p><code>Turkish/windows-1254</code></p></li>
<li><p><code>Turkish/iso-8859-9</code></p></li>
<li><p><code>Vietnamese/tcvn</code></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>DomainName</code></p></td>
<td><p>Array von SMTP-Domänen</p></td>
<td><p>Zum Beispiel <code>contoso.com</code> oder <code>eu.contoso.com</code>.</p>
<p>In der Exchange-Verwaltungsshell können mehrere Domänen durch Kommata getrennt angegeben werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>EvaluatedUser</code></p></td>
<td><p>Einzelwert von <strong>Sender</strong> oder <strong>Recipient</strong></p></td>
<td><p>Gibt an, ob die Regel nach dem Vorgesetzten des Absenders oder dem Vorgesetzten des Empfängers sucht.</p></td>
</tr>
<tr class="even">
<td><p><code>Evaluation</code></p></td>
<td><p>Einzelwert von <strong>Equal</strong> oder <strong>Not equal</strong> (<code>NotEqual</code>)</p></td>
<td><p>Beim Vergleichen des Attributs Active Directory des Absenders und der Empfänger wird hiermit angegeben, ob die Werte übereinstimmen sollen oder nicht.</p></td>
</tr>
<tr class="odd">
<td><p><code>Importance</code></p></td>
<td><p>Einzelwert von <strong>Low</strong>, <strong>Normal</strong> oder <strong>High</strong></p></td>
<td><p>Die Wichtigkeitsstufe, die der Nachricht vom Absender in Outlook oder Outlook Web App zugewiesen wurde.</p></td>
</tr>
<tr class="even">
<td><p><code>IPAddressRanges</code></p></td>
<td><p>Array von IP-Adressen oder Adressbereichen</p></td>
<td><p>Sie geben die IPv4-Adressen mit der folgenden Syntax ein:</p>
<ul>
<li><p><strong>Einzelne IP-Adresse</strong>   Zum Beispiel <code>192.168.1.1</code>.</p></li>
<li><p><strong>IP-Adressbereich</strong>   Zum Beispiel <code>192.168.0.1-192.168.0.254</code>.</p></li>
<li><p><strong>Classless InterDomain Routing (CIDR) IP-Adressbereich</strong>   Zum Beispiel <code>192.168.0.1/25</code>.</p></li>
</ul>
<p>In der Exchange-Verwaltungsshell können mehrere IP-Adressen oder Bereiche durch Komma getrennt angegeben werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>ManagementRelationship</code></p></td>
<td><p>Einzelwert von <strong>Vorgesetzter</strong> oder <strong>DirectReport</strong>(<code>DirectReport</code>)</p></td>
<td><p>Gibt die Beziehung zwischen Absender und einem der Empfänger an. Die Regel überprüft das Attribut <strong>Manager</strong> in Active Directory, um festzustellen, ob der Absender der Vorgesetzte eines Empfängers ist oder ob der Absender den Empfänger als Vorgesetzten hat.</p></td>
</tr>
<tr class="even">
<td><p><code>MessageClassification</code></p></td>
<td><p>Einzelne Nachrichtenklassifikation</p></td>
<td><p>Wählen Sie in der Exchange-Verwaltungskonsole aus der Liste der Nachrichtenklassifikationen aus, die Sie erstellt haben.</p>
<p>Verwenden Sie in Exchange-Verwaltungsshell das Cmdlet <strong>Get-MessageClassification</strong> zur Ermittlung der Nachrichtenklassifikation. Verwenden Sie beispielsweise den folgenden Befehl, um nach Nachrichten mit der Klassifikation <code>Company Internal</code> zu suchen und dem Nachrichtenbetreff mit dem Wert <code>CompanyInternal</code> voranzustellen.</p>
<p><code>New-TransportRule &quot;Rule Name&quot; -HasClassification @(Get-MessageClassification &quot;Company Internal&quot;).Identity -PrependSubject &quot;CompanyInternal&quot;</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MessageHeaderField</code></p></td>
<td><p>Einzelne Zeichenfolge</p></td>
<td><p>Gibt den Namen des Header-Felds an. Der Name des Header-Felds wird immer zusammen mit dem Wert im Header-Feld angegeben (Wort- oder Text-Musterübereinstimmung).</p>
<p>Die <em>Nachrichtenkopfzeile</em> ist eine Sammlung erforderlicher und optionaler Kopfzeilenfelder in der Nachricht. Beispiele für Kopfzeilenfelder sind <strong>To</strong>, <strong>From</strong>, <strong>Received</strong> und <strong>Content-Type</strong>. Offizielle Kopfzeilenfelder sind in RFC 5322 definiert. Inoffizielle Kopfzeilenfelder beginnen mit <strong>X-</strong> und werden als <em>X-Header</em> bezeichnet.</p></td>
</tr>
<tr class="even">
<td><p><code>MessageType</code></p></td>
<td><p>Einzelner Nachrichtentypwert</p></td>
<td><p>Gibt einen der folgenden Nachrichtentypen an:</p>
<ul>
<li><p><strong>Automatische Antwort</strong> (<code>OOF</code>)</p></li>
<li><p><strong>Automatische Weiterleitung</strong> (<code>AutoForward</code>)</p></li>
<li><p><strong>Encrypted</strong></p></li>
<li><p><strong>Calendaring</strong></p></li>
<li><p><strong>Berechtigungsgesteuert</strong> (<code>PermissionControlled</code>)</p></li>
<li><p><strong>Voicemail</strong></p></li>
<li><p><strong>Signed</strong></p></li>
<li><p><strong>Genehmigungsanforderung</strong> (<code>ApprovalRequest</code>)</p></li>
<li><p><strong>Lesebestätigung</strong> (<code>ReadReceipt</code>)</p></li>
</ul>

> [!NOTE]
> Wenn Outlook oder Outlook Web App so konfiguriert ist, dass eine Nachricht weitergeleitet wird, wird die Eigenschaft <STRONG>ForwardingSmtpAddress</STRONG> der Nachricht hinzugefügt. Der Nachrichtentyp wird nicht in <CODE>AutoForward</CODE> geändert.


</td>
</tr>
<tr class="odd">
<td><p><code>Patterns</code></p></td>
<td><p>Array regulärer Ausdrücke</p></td>
<td><p>Gibt einen oder mehrere reguläre Ausdrücke an, die zur Identifizierung von Textmustern in Werte verwendet werden. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=180327">Syntax für reguläre Ausdrücke</a>.</p>
<p>In der Exchange-Verwaltungsshell geben Sie mehrere reguläre Ausdrücke durch Kommata getrennt an und setzen vor und nach jeden Ausdruck Anführungszeichen (&quot;).</p></td>
</tr>
<tr class="even">
<td><p><code>SCLValue</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>Spamfilter umgehen</strong> (<code>-1</code>)</p></li>
<li><p>Ganze Zahlen (0-9)</p></li>
</ul></td>
<td><p>Gibt den Schwellenwert der SCL-Bewertung (Spam Confidence Level) an, der einer Nachricht zugewiesen ist. Ein höherer SCL-Wert gibt an, dass eine Nachricht mit größerer Wahrscheinlichkeit Spam ist.</p></td>
</tr>
<tr class="odd">
<td><p><code>SensitiveInformationTypes</code></p></td>
<td><p>Array vertraulicher Informationstypen</p></td>
<td><p>Gibt einen oder mehrere in Ihrer Organisation definierte Typen vertraulicher Informationen an. Eine Liste der integrierten Typen vertraulicher Informationen finden Sie unter <a href="what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md">Wonach die Typen von vertraulichen Informationen in Exchange suchen</a>.</p>
<p>Verwenden Sie in der Exchange-Verwaltungsshell die Syntax <code>@{&lt;SensitiveInformationType1&gt;},@{&lt;SensitiveInformationType2&gt;},...</code>. Wenn Sie beispielsweise nach Inhalt suchen möchten, der mindestens zwei Kreditkartennummern und mindestens eine ABA Routing Number (US-Bankleitzahl) enthält, verwenden Sie z. B. den Wert <code>@{Name=&quot;Credit Card Number&quot;; minCount=&quot;2&quot;},@{Name=&quot;ABA Routing Number&quot;; minCount=&quot;1&quot;}</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>Size</code></p></td>
<td><p>Wert der einzelnen Größe</p></td>
<td><p>Gibt die Größe einer Anlage oder der gesamten Nachricht an.</p>
<p>In der Exchange-Verwaltungskonsole können Sie nur die Größe in Kilobyte (KB) angeben.</p>
<p>Wenn Sie in der Exchange-Verwaltungsshell einen Wert eingeben, qualifizieren Sie den Wert mit einer der folgenden Einheiten:</p>
<ul>
<li><p><code>B</code> (Bytes)</p></li>
<li><p><code>KB</code> (Kilobytes)</p></li>
<li><p><code>MB</code> (Megabytes)</p></li>
<li><p><code>GB</code> (Gigabytes)</p></li>
</ul>
<p>Beispiel, <code>20MB</code></p>
<p>Nicht qualifizierte Werte werden in der Regel als Byte behandelt, kleine Werte werden jedoch auf das nächsthöhere Kilobyte aufgerundet.</p></td>
</tr>
<tr class="odd">
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Einzelner Wert von <strong>innerhalb der Organisation</strong> (<code>InOrganization</code>) oder <strong>außerhalb der Organisation</strong> (<code>NotInOrganization</code>)</p></td>
<td><p>Ein Absender wird als innerhalb der Organisation befindlich angesehen, wenn eine der folgenden Bedingungen erfüllt ist:</p>
<ul>
<li><p>Bei dem Absender handelt es sich um ein Postfach, einen E-Mail-Benutzer, eine Gruppe oder einen E-Mail-aktivierten öffentlichen Ordner, der innerhalb von Active Directory der Organisation vorhanden ist.</p></li>
<li><p>Die E-Mail-Adresse des Absenders befindet sich in einer akzeptierten Domäne, die als autorisierende Domäne oder interne Relaydomäne konfiguriert ist, <strong>und</strong> die Nachricht wurde über eine authentifizierte Verbindung gesendet oder empfangen. Weitere Informationen zu akzeptierten Domänen finden Sie unter <a href="accepted-domains-exchange-2013-help.md">Akzeptierte Domänen</a>.</p></li>
</ul>
<p>Ein Absender wird als außerhalb der Organisation befindlich angesehen, wenn eine der folgenden Bedingungen erfüllt ist:</p>
<ul>
<li><p>Die E-Mail-Adresse des Absenders befindet sich nicht in einer akzeptierten Domäne.</p></li>
<li><p>Die E-Mail-Adresse des Absenders befindet sich in einer akzeptierten Domäne, die als externe Relaydomäne konfiguriert ist.</p></li>
</ul>

> [!NOTE]
> Um zu ermitteln, ob E-Mail-Kontakte als innerhalb oder außerhalb der Organisation befindlich angesehen werden, wird die Absenderadresse mit den akzeptierten Domänen der Organisation verglichen.


</td>
</tr>
<tr class="even">
<td><p><code>UserScopeTo</code></p></td>
<td><p>Einer der folgenden Werte:</p>
<ul>
<li><p><strong>Innerhalb der Organisation</strong> (<code>InOrganization</code>)</p></li>
<li><p><strong>Außerhalb der Organisation</strong> (<code>NotInOrganization</code>)</p></li>
<li><p><strong>In einer externen Partnerorganisation</strong> (<code>ExternalPartner</code>)</p></li>
<li><p><strong>In einer externen Nicht-Partnerorganisation</strong> (<code>ExternalNonPartner</code>)</p></li>
</ul></td>
<td><p>Ein Empfänger wird als innerhalb der Organisation befindlich angesehen, wenn eine der folgenden Bedingungen erfüllt ist:</p>
<ul>
<li><p>Bei dem Empfänger handelt es sich um ein Postfach, einen E-Mail-Benutzer, eine Gruppe oder einen E-Mail-aktivierten öffentlichen Ordner, der innerhalb von Active Directory der Organisation vorhanden ist.</p></li>
<li><p>Die E-Mail-Adresse des Empfängers befindet sich in einer akzeptierten Domäne, die als autorisierende Domäne oder interne Relaydomäne konfiguriert ist, <strong>und</strong> die Nachricht wurde über eine authentifizierte Verbindung gesendet oder empfangen.</p></li>
</ul>
<p>Ein Empfänger wird als außerhalb der Organisation befindlich angesehen, wenn eine der folgenden Bedingungen erfüllt ist:</p>
<ul>
<li><p>Die E-Mail-Adresse des Empfängers befindet sich nicht in einer akzeptierten Domäne.</p></li>
<li><p>Die E-Mail-Adresse des Empfängers befindet sich in einer akzeptierten Domäne, die als externe Relaydomäne konfiguriert ist.</p></li>
</ul>
<p>Externe Partnerorganisationen sind externe Domänen, in denen Sie die Domänensicherheit (gegenseitige TLS-Authentifizierung) zum Senden von E-Mails konfiguriert haben.</p>
<p>Externe Nicht-Partnerorganisationen sind alle anderen externen Domänen, die nicht als Partnerdomänen angesehen werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>Words</code></p></td>
<td><p>Array aus Zeichenfolgen</p></td>
<td><p>Gibt ein oder mehrere zu suchende Wörter an. Die Groß-/Kleinschreibung wird nicht berücksichtigt, und der Text kann von Leerzeichen und Satzzeichen umgeben sein. Platzhalter und teilweise Übereinstimmungen werden nicht unterstützt.</p>
<p>Beispiel: &quot;contoso&quot; stimmt mit &quot; Contoso.&quot; überein. Wenn der Text jedoch von anderen Zeichen umgeben ist, wird dies nicht als Übereinstimmung betrachtet. &quot;Contoso&quot; entspricht beispielsweise nicht den folgenden Werten:</p>
<ul>
<li><p>Acontoso</p></li>
<li><p>Contosoa</p></li>
<li><p>Acontosob</p></li>
</ul>
<p>Das Sternchen (*) wird als literales Zeichen betrachtet und nicht als Platzhalter verwendet.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Weitere Informationen

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md)

[Nachrichtenfluss- oder Transportregelverfahren](mail-flow-or-transport-rule-procedures-exchange-2013-help.md)

[Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\)) für Exchange Online

[Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj919234\(v=exchg.150\)) für Exchange Online Protection

