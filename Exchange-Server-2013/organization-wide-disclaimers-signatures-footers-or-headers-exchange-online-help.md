---
title: 'Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen'
TOCTitle: Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen
ms:assetid: e45e33c9-e53b-427c-ada5-70901bc399b8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn600437(v=EXCHG.150)
ms:contentKeyID: 61060919
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Sie können einen E-Mail-Haftungsausschluss, eine Verzichtserklärung, eine Offenlegungspflicht, eine Signatur oder andere Informationen an den Anfang oder das Ende der E-Mail-Nachrichten platzieren, die aus Ihrer Organisation verschickt oder von ihr empfangen werden. Dies kann erforderlich sein, um rechtliche, geschäftliche oder regulatorische Anforderungen zu erfüllen und potenziell unsichere E-Mails zu identifizieren - oder aus Gründen, die nur für Ihre Organisation gelten.

Zum Einrichten eines Haftungsausschlusses erstellen Sie eine Transportregel mit den entsprechenden Bedingungen, z. B. dass der Absender in einer bestimmten Gruppe ist oder die Nachricht spezielle Textmuster enthält, sowie mit dem hinzuzufügenden Text. Wenn Sie mehrere Haftungsausschlüsse in eine einzelne E-Mail einfügen möchten, müssen Sie mehrere Transportregeln verwenden.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>Wenn Sie möchten, dass die Informationen nur an ausgehende Nachrichten angehängt werden, müssen Sie Bedingungen der Art hinzufügen, dass die Empfänger sich außerhalb Ihrer Organisation befinden müssen. Standardmäßig werden Transportregeln sowohl auf eingehende als auch auf ausgehende Nachrichten angewendet.</P></LI></UL>



**Inhalt**

Beispiele

Festlegen des Gültigkeitsbereichs des Haftungsausschlusses

Formatierung des Haftungsausschlusses

Alternative Optionen, wenn der Haftungsausschluss nicht hinzugefügt werden kann

Weitere Informationen

Suchen Sie nach geeigneten Verfahren? Weitere Informationen finden Sie unter [Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen für E-Mail-Nachrichten in Office 365](https://technet.microsoft.com/de-de/library/dn600323\(v=exchg.150\)).

## Beispiele

Hier finden Sie einige Ideen zur Verwendung von Haftungsausschlüssen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Typ</th>
<th>Beispieltext hinzugefügt</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rechtlich - für ausgehende Nachrichten</p></td>
<td><p>Diese E-Mail und alle mit ihr versendeten Daten sind vertraulich und nur für den Gebrauch durch die Person oder die Einheit bestimmt, an die sie adressiert ist. Wenn Sie diese E-Mail fälschlicherweise empfangen haben, benachrichtigen Sie bitte den System-Manager.</p></td>
</tr>
<tr class="even">
<td><p>Rechtlich - für eingehende Nachrichten</p></td>
<td><p>Wir fordern unsere Mitarbeiter ausdrücklich auf, Verleumdungen, Verletzungen des Copyrights oder anderer Rechte sowie Billigungen dieser Rechtsverletzungen zu vermeiden. Mitarbeiter, die eine E-Mail mit solchen Inhalten empfangen, müssen sofort den Abteilungsleiter informieren.</p></td>
</tr>
<tr class="odd">
<td><p>Beachten Sie, dass die Nachricht an einen Alias gesendet wurde</p></td>
<td><p>Diese Nachricht wurde an die Diskussionsgruppe Vertrieb gesendet.</p></td>
</tr>
<tr class="even">
<td><p>Signatur – erfasst Daten für alle Mitarbeiter</p></td>
<td><p>Kathleen Mayer<br />
Sales Department<br />
Contoso<br />
www.contoso.com<br />
kathleen@contoso.com<br />
Telefon: 111-222-1234</p></td>
</tr>
<tr class="odd">
<td><p>Werbung</p></td>
<td><p>Klicken Sie hier für unsere speziellen März-Angebote</p></td>
</tr>
</tbody>
</table>


Die Beispiele in diesem Artikel sind nicht für die Verwendung "as-is" gedacht. Verändern Sie sie für Ihren Anforderungen.

## Festlegen des Gültigkeitsbereichs des Haftungsausschlusses

Wenn Sie an Ihren Haftungsausschlüssen arbeiten, überlegen Sie, für welche Nachrichten Sie gelten sollen. Sie können z. B. unterschiedliche Haftungsausschlüsse für interne und externe Nachrichten oder für Nachrichten erstellen, die von Benutzern in bestimmten Abteilungen gesendet werden. Wenn nur die erste Nachricht in einer Konversation einen Haftungsausschluss enthalten soll, fügen Sie eine Ausnahme hinzu, die nach einem eindeutigen Text in Ihrem Haftungsausschluss sucht.

Hier sehen Sie einige Beispiele für die Bedingungen und Ausnahmen, die Sie verwenden können.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Bedingungen und Ausnahmen in der EAC</th>
<th>Bedingungen und Ausnahmen in der Shell</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Außerhalb Ihrer Organisation, wenn die ursprüngliche Nachricht keinen Text aus Ihrem Haftungsausschluss enthält, wie “CONTOSO LEGAL NOTICE”</p></td>
<td><p>Bedingung: <strong>Der Absender befindet sich</strong> &gt; <strong>Innerhalb der Organisation</strong>.</p>
<p>Ausnahme: <strong>Betreff oder Nachrichtentext</strong> &gt; <strong>Betreff oder Nachrichtentext entspricht diesen Textmustern</strong> &gt; <strong>CONTOSO LEGAL NOTICE</strong></p></td>
<td>

```powershell
-FromScope NotInOrganization -ExceptIf -SubjectOrBodyMatches "CONTOSO LEGAL NOTICE"
```
</td>
</tr>
<tr class="even">
<td><p>Eingehende Nachrichten mit ausführbaren Anhängen</p></td>
<td><p>Bedingung 1: <strong>Der Absender befindet sich</strong> &gt; <strong>Außerhalb der Organisation</strong>.</p>
<p>Bedingung 2: <strong>Eine Anlage</strong> &gt; <strong>hat ausführbaren Inhalt</strong></p></td>
<td>

```powershell
-FromScope NotInOrganization -AttachmentHasExecutableContent
```
</td>
</tr>
<tr class="odd">
<td><p>Absender befindet sich in der Marketing-Abteilung</p></td>
<td><p>Bedingung: <strong>Absender</strong> &gt; <strong>ist Mitglied dieser Gruppe</strong> &gt; <strong>group name</strong></p></td>
<td>

```powershell
-FromMemberOf "Marketing Team"
```
</td>
</tr>
<tr class="even">
<td><p>Jede Nachricht, die von einem externen Absender an die Diskussionsgruppe "Vertrieb" gesendet wird</p></td>
<td><p>Bedingung 1: <strong>Der Absender befindet sich</strong> &gt; <strong>Außerhalb der Organisation</strong>.</p>
<p>Bedingung 2: <strong>Die Nachricht</strong> &gt; <strong>Feld „An“ oder „Cc“ enthält diese Person</strong> &gt; <strong>group name</strong></p></td>
<td>

```powershell
-FromScope NotInOrganization -SentTo "Sales Discussion Group" -PrependSubject "Sent to Sales Discussion Group: "
```
</td>
</tr>
<tr class="odd">
<td><p>Voranstellen einer Werbung in ausgehenden Nachrichten für einen Monat</p></td>
<td><p>Bedingung 1: <strong>Der Absender befindet sich</strong> &gt; <strong>Innerhalb der Organisation</strong>.</p>
<p>Geben Sie die Daten unten im Dialogfeld <strong>Neue Regel</strong> ein.</p></td>
<td><p>-ApplyHtmlDisclaimerLocation 'Prepend' -SentToScope 'NotInOrganization' –ActivationDate ‘03/1/2014’ –ExpiryDate ‘03/31/2014’</p></td>
</tr>
</tbody>
</table>


Eine vollständige Liste der Transportregelbedingungen, die Sie für den Haftungsausschluss verwenden, finden Sie in einer der folgenden Quellen:

  - [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\)) (Exchange Online)

  - [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md) (Exchange 2013)

  - [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\)) (Exchange Online Protection)

## Formatierung des Haftungsausschlusses

Sie können Ihren Haftungsausschluss nach Bedarf formatieren. Folgende Elemente können in den Text Ihres Haftungsausschlusses aufgenommen werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Art der Information</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Text</p></td>
<td><p>Die maximale Länge beträgt 5.000 Zeichen. Dabei werden alle HTML-Tags und Inline-Cascading Stylesheet-Tags (CSS) mitgezählt.</p></td>
</tr>
<tr class="even">
<td><p>HTML und Inline-CSS</p></td>
<td><p>Sie können HTML- und Inline-CSS-Formate verwenden, um den Text zu formatieren. Verwenden Sie z. B. den Tag <code>&lt;HR&gt;</code>, um eine Zeile vor dem Haftungsausschluss einzufügen.</p>
<p>HTML wird in einem Haftungsausschluss ignoriert, wenn der Haftungsausschluss in eine Nur-Text-Nachricht eingefügt wird.</p></td>
</tr>
<tr class="odd">
<td><p>Hinzufügen von Bildern</p></td>
<td><p>Verwenden Sie den Tag <code>&lt;IMG&gt;</code>, um auf ein Bild im Internet zu verweisen. Beispiel, <code>&lt;IMG src="http://contoso.com/images/companylogo.gif" alt="Contoso logo"&gt;</code></p>
<p>Denken Sie daran, dass Outlook Web App und Outlook externe Webinhalte, darunter Bilder, standardmäßig blockieren. Die Benutzer müssen möglicherweise eine bestimmte Aktion ausführen, wenn Sie den blockierten externen Inhalt anzeigen möchten. Das bedeutet, dass Bilder, die mithilfe des Tags <code>IMG</code> hinzugefügt wurden, eventuell standardmäßig nicht sichtbar sind. Es wird empfohlen, einen Haftungsausschluss mit <code>IMG</code>-Tags auf den E-Mail-Clients zu testen, die Ihre Empfänger wahrscheinlich verwenden. So können Sie sicherstellen, dass der Haftungsausschluss korrekt angezeigt wird.</p></td>
</tr>
<tr class="even">
<td><p>Hinzufügen von Informationen für persönliche Signaturen</p></td>
<td><p>Wenn Sie möchten, dass die Signaturen für alle Mitarbeiter auf dieselbe Weise formatiert sind und dieselben Informationen enthalten, können Sie eindeutige Namen für jeden Mitarbeiter hinzufügen, z. B. <code>DisplayName</code>, <code>FirstName</code>, <code>LastName</code>, <code>PhoneNumber</code>, <code>Email</code>, <code>FaxNumber</code> und <code>Department</code>. Diese Informationen müssen in zwei Prozentzeichen (%%) auf jeder Seite eingeschlossen sein. Wenn Sie z. B. <code>DisplayName</code> verwenden möchten, müssen Sie dies in ihren Haftungsausschluss als <strong>%%DisplayName%%</strong> eintragen.</p>
<p>Wenn eine Haftungsausschlussregel ausgelöst wird, werden die entsprechenden Werte für diesen Benutzer eingefügt. Die Daten werden aus dem Active Directory-Benutzerkonto des Absenders (wenn Exchange Server lokal installiert ist), oder bei Exchange Online aus dem Office 365-Konto des Benutzers entnommen.</p>
<p>Eine vollständige Liste der Attribute, die in Haftungsausschlüssen und persönlichen Signaturen verwendet werden können, finden Sie in der Beschreibung der Eigenschaft <code>ADAttribute</code> in <a href="mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md">Transportregelbedingungen (Prädikate)</a> (Exchange Server), <a href="https://technet.microsoft.com/de-de/library/jj919235(v=exchg.150)">Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online</a> (Exchange Online) oder <a href="https://technet.microsoft.com/de-de/library/jj919234(v=exchg.150)">Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online Protection</a> (Exchange Online Protection).</p></td>
</tr>
</tbody>
</table>


Hier finden Sie ein Beispiel für einen HTML-Haftungsausschluss, der eine Signatur, ein `IMG`-Tag und eingebettete CSS-Formate verwendet.

```HTML
    <div style="font-size:9pt;  font-family: 'Calibri',sans-serif;">
    %%displayname%%</br>
    %%title%%</br>
    %%company%%</br>
    %%street%%</br>
    %%city%%, %%state%% %%zipcode%%</div>
    &nbsp;</br>
    <div style="background-color:#D5EAFF; border:1px dotted #003333; padding:.8em; ">
    <div><img alt="Fabrikam"  src="http://fabrikam.com/images/fabrikamlogo.png"></div>
    <span style="font-size:12pt;  font-family: 'Cambria','times new roman','garamond',serif; color:#ff0000;">HTML Disclaimer Title</span></br>
    <p style="font-size:8pt; line-height:10pt; font-family: 'Cambria','times roman',serif;">This message contains confidential information and is intended only for the individual(s) addressed in the message. If you are not the named addressee, you should not disseminate, distribute, or copy this e-mail. If you are not the intended recipient, you are notified that disclosing, distributing, or copying this e-mail is strictly prohibited.  </p>
    <span style="padding-top:10px; font-weight:bold; color:#CC0000; font-size:10pt; font-family: 'Calibri',Arial,sans-serif; "><a href="http://www.fabrikam.com">Fabrikam, Inc. </a></span></br></br>
    </div>
```

## Alternative Optionen, wenn der Haftungsausschluss nicht hinzugefügt werden kann

Einige Nachrichten, z. B. verschlüsselte Nachrichten, hindern Exchange daran, den Inhalt der ursprünglichen Nachricht zu ändern. Sie können steuern, wie diese Nachrichten in Ihrer Organisation verarbeitet werden. Sie können entscheiden, ob eine nicht veränderbare Nachricht in einen Nachrichtenumschlag eingeschlossen werden soll, der den Haftungsausschluss enthält, ob die Nachricht verworfen werden soll, wenn kein Haftungsausschluss hinzugefügt werden kann, oder ob die Aktion zum Hinzufügen des Haftungsausschlusses gegebenenfalls ignoriert und die Nachricht ohne Haftungsausschluss gesendet werden soll.

Die folgende Liste beschreibt jede Ausweichaktion:

  - **Umschlag**   Wenn die Verzichtserklärung nicht in die Originalnachricht eingefügt werden kann, schließt Exchange die Originalnachricht in einen neuen Nachrichtenumschlag ein. Anschließend wird der Haftungsausschluss in die neue Nachricht eingefügt. Wenn die Originalnachricht nicht in einen neuen Nachrichtenumschlag verpackt werden kann, wird die Originalnachricht nicht übermittelt. Der Absender der Nachricht erhält einen Unzustellbarkeitsbericht (NDR), der erläutert, warum die Nachricht nicht übermittelt wurde.
    

    > [!IMPORTANT]
    > Wenn eine Originalnachricht in einen neuen Nachrichtenumschlag verpackt wird, werden die entsprechenden Transportregeln auf den neuen Nachrichtenumschlag angewendet statt auf die Originalnachricht. Daher müssen Transportregeln mit Haftungsausschlüssen, die Originalnachrichten in einen neuen Nachrichtentext einschließen, nach dem Konfigurieren anderer Transportregeln konfiguriert werden.



  - **Ablehnen**   Wenn der Haftungsausschluss nicht in die Originalnachricht eingefügt werden kann, stellt Exchange die Nachricht nicht zu. Der Absender der Nachricht empfängt einen NDR, der erläutert, warum die Nachricht nicht zugestellt wurde.

  - **Ignorieren**   Wenn der Haftungsausschluss nicht in die Originalnachricht eingefügt werden kann, stellt Exchange die Originalnachricht unverändert zu. Es wird kein Haftungsausschluss hinzugefügt.

## Weitere Informationen

[Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen für E-Mail-Nachrichten in Office 365](https://technet.microsoft.com/de-de/library/dn600323\(v=exchg.150\))

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange Server 2013)

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online)

[Nachrichtenflussregeln (Transportregeln) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/dn271424\(v=exchg.150\)) (Exchange Online Protection)

