---
title: 'Nachrichteneigenschaften und Suchoperatoren für Compliance-eDiscovery: Exchange 2013 Help'
TOCTitle: Nachrichteneigenschaften und Suchoperatoren für Compliance-eDiscovery
ms:assetid: 402b74e4-8853-4c51-9737-1a9c19f8e3dd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn774955(v=EXCHG.150)
ms:contentKeyID: 62617675
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichteneigenschaften und Suchoperatoren für Compliance-eDiscovery

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In diesem Thema werden die Eigenschaften von Exchange-E-Mails beschrieben, nach denen Sie mithilfe von In-Situ-eDiscovery & -Speicher in Exchange Server 2013 und Exchange Online suchen können. Außerdem werden in diesem Thema Boolesche Suchoperatoren und andere Suchabfragetechniken beschrieben, die Sie verwenden können, um eDiscovery-Suchergebnisse zu verfeinern.

Compliance-eDiscovery verwendet Keyword Query Language (KQL). Weitere Informationen dazu finden Sie unter [Keyword Query Language – Syntaxverweis](https://go.microsoft.com/fwlink/?linkid=269603).

## Durchsuchbare Eigenschaften in Exchange

In der folgenden Tabelle sind Eigenschaften von E-Mails aufgelistet, nach denen in einer Compliance-eDiscovery-Suche oder mithilfe von **New-MailboxSearch** oder des Cmdlets **Set-MailboxSearch** gesucht werden kann. Die Tabelle enthält ein Beispiel für die *property:value*-Syntax für jede Eigenschaft und eine Beschreibung der für jedes Beispiel zurückgegebenen Suchergebnisse.


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
<th>Beschreibung der Eigenschaft</th>
<th>Beispiele</th>
<th>Von den Beispielen zurückgegebene Suchergebnisse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Anhang</p></td>
<td><p>Die Namen der an eine E-Mail angefügten Dateien.</p></td>
<td><p>Anhang:Jahresbericht.ppt</p>
<p>Anhang:Jahresbericht*</p></td>
<td><p>Nachrichten, an die eine Datei namens Jahresbericht.ppt angehängt ist.</p>
<p>Im zweiten Beispiel werden, wenn Sie das Platzhalterzeichen verwenden, Nachrichten mit dem Wort &quot;Jahresbericht&quot; im Dateinamen eines Anhangs zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>Bcc</p></td>
<td><p>Das Feld „BCC“ einer E-Mail-Nachricht.1</p></td>
<td><p>bcc:pilarp@contoso.com</p>
<p>bcc:pilarp</p>
<p>bcc:&quot;Pilar Pinilla&quot;</p></td>
<td><p>In allen Beispielen werden Nachrichten mit dem Namen &quot;Pilar Pinilla&quot; im Bcc-Feld zurückgegeben.</p></td>
</tr>
<tr class="odd">
<td><p>Kategorie</p></td>
<td><p>Die Kategorien, nach denen gesucht wird. Kategorien können durch Benutzer mithilfe von Outlook oder Outlook Web App definiert werden. Die folgenden Werte sind möglich:</p>
<ul>
<li><p>blau</p></li>
<li><p>grün</p></li>
<li><p>orange</p></li>
<li><p>violett</p></li>
<li><p>rot</p></li>
<li><p>gelb</p></li>
</ul></td>
<td><p>Kategorie:=&quot;Rote Kategorie&quot;</p></td>
<td><p>Nachrichten, denen in den Quellpostfächern die rote Kategorie zugewiesen wurde.</p></td>
</tr>
<tr class="even">
<td><p>Cc</p></td>
<td><p>Das Feld „CC“ einer E-Mail-Nachricht.1</p></td>
<td><p>cc:pilarp@contoso.com</p>
<p>cc:&quot;Pilar Pinilla&quot;</p></td>
<td><p>In beiden Fällen Nachrichten mit dem Namen &quot;Pilar Pinilla&quot; im CC-Feld.</p></td>
</tr>
<tr class="odd">
<td><p>Von</p></td>
<td><p>Der Absender einer E-Mail-Nachricht.1</p></td>
<td><p>from:pilarp@contoso.com</p>
<p>Von:contoso.com</p></td>
<td><p>Nachrichten, die vom angegebenen Benutzer oder einer bestimmten Domäne gesendet wurden.</p></td>
</tr>
<tr class="even">
<td><p>Wichtigkeit</p></td>
<td><p>Die Wichtigkeit einer E-Mail-Nachricht, die ein Absender festlegen kann, wenn er eine Nachricht sendet. Standardmäßig werden Nachrichten mit normaler Wichtigkeit gesendet, außer wenn der Absender die Wichtigkeit auf <strong>Hoch</strong> oder <strong>Niedrig</strong> setzt.</p></td>
<td><p>Wichtigkeit:Hoch</p>
<p>Wichtigkeit:Mittel</p>
<p>Wichtigkeit:Niedrig</p></td>
<td><p>Nachrichten, deren Wichtigkeit auf &quot;Hoch&quot;, &quot;Mittel&quot; bzw. &quot;Niedrig&quot; eingestellt ist.</p></td>
</tr>
<tr class="odd">
<td><p>Art</p></td>
<td><p>Der Nachrichtentyp, nach dem gesucht wird. Mögliche Werte:</p>
<ul>
<li><p>contacts</p></li>
<li><p>docs</p></li>
<li><p>email</p></li>
<li><p>faxes</p></li>
<li><p>im</p></li>
<li><p>journals</p></li>
<li><p>meetings</p></li>
<li><p>notes</p></li>
<li><p>posts</p></li>
<li><p>rssfeeds</p></li>
<li><p>tasks</p></li>
<li><p>voicemail</p></li>
</ul></td>
<td><p>Art:email</p>
<p>Art:email OR Art:im OR Art:Voicemail</p></td>
<td><p>E-Mails, die den Suchkriterien entsprechen. Im zweiten Beispiel werden E-Mails, Instant Messaging-Konversationen und Sprachnachrichten zurückgegeben, die den Suchkriterien entsprechen.</p></td>
</tr>
<tr class="even">
<td><p>Teilnehmer</p></td>
<td><p>Alle Felder mit Personen in einer E-Mail-Nachricht. Diese Felder sind „Von“, „An“, „CC“ und „BCC“.1</p></td>
<td><p>participants:garthf@contoso.com</p>
<p>participants:contoso.com</p></td>
<td><p>Nachrichten, die von oder an garthf@contoso.com gesendet wurden.</p>
<p>Im zweiten Beispiel werden alle Nachrichten zurückgegeben, die von oder an einen Benutzer in der Domäne contoso.com gesendet wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Empfangen</p></td>
<td><p>Das Datum, an dem eine E-Mail-Nachricht von einem Empfänger empfangen wurde.</p></td>
<td><p>received:04/15/2014</p>
<p>received&gt;=01/01/2014 AND received&lt;=03/31/2014</p></td>
<td><p>Nachrichten, die am 15. April 2014 empfangen wurden. Im zweiten Beispiel werden alle Nachrichten zurückgegeben, die zwischen dem 1. Januar 2014 und dem 31. März 2014 empfangen wurden.</p></td>
</tr>
<tr class="even">
<td><p>Empfänger</p></td>
<td><p>Alle Felder mit Empfängern in einer E-Mail-Nachricht. Diese Felder sind „An“, „CC“ und „BCC“.1</p></td>
<td><p>recipients:garthf@contoso.com</p>
<p>recipients:contoso.com</p></td>
<td><p>Nachrichten, die an garthf@contoso.com gesendet wurden.</p>
<p>Im zweiten Beispiel werden Nachrichten zurückgegeben, die an einen beliebigen Empfänger in der Domäne contoso.com geschickt wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Gesendet</p></td>
<td><p>Das Datum, an dem eine E-Mail vom Absender gesendet wurde.</p></td>
<td><p>sent:07/01/2014</p>
<p>sent&gt;=06/01/2014 UND sent&lt;=07/01/2014</p></td>
<td><p>Nachrichten, die am angegebenen Tag oder im angegebenen Datumsbereich gesendet wurden.</p></td>
</tr>
<tr class="even">
<td><p>Größe</p></td>
<td><p>Die Größe eines Elements in Byte.</p></td>
<td><p>Größe &gt; 26214400</p>
<p>size:1..1048576</p></td>
<td><p>Nachrichten mit mehr als 25 MB.</p>
<p>Im zweiten Beispiel werden Nachrichten mit einer Größe von 1 bis 1.048.576 Byte (1 MB) zurückgegeben.</p></td>
</tr>
<tr class="odd">
<td><p>Betreff</p></td>
<td><p>Der Text in der Betreffzeile einer E-Mail.</p></td>
<td><p>Betreff:&quot;Vierteljährliche Finanzdaten&quot;</p>
<p>Betreff:northwind</p></td>
<td><p>Nachrichten mit dem exakten Ausdruck „Vierteljährliche Finanzdaten“ in der Betreffzeile.</p>
<p>Im zweiten Beispiel werden alle Nachrichten mit dem Wort &quot;northwind&quot; in der Betreffzeile zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>An</p></td>
<td><p>Das Feld „An“ einer E-Mail-Nachricht.1</p></td>
<td><p>to:annb@contoso.com</p>
<p>an:annb</p>
<p>an:&quot;Ann Beebe&quot;</p></td>
<td><p>In allen Beispielen wegen Nachrichten zurückgegeben, in deren Zeile &quot;An&quot; der Name &quot;Ann Beebe&quot; angegeben ist.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 1&nbsp;&nbsp;&nbsp;Für den Wert einer Empfängereigenschaft können sie die SMTP-Adresse, den Anzeigenamen oder den Alias verwenden, um einen Benutzer anzugeben. Sie können z.&nbsp;B. annb@contoso.com, Annb oder „Ann Beebe“ verwenden, um den Benutzer Ann Beebe anzugeben.



## Unterstützte Suchoperatoren

Boolesche Suchoperatoren wie **AND** und **OR** helfen Ihnen bei der Definition präziserer Postfachsuchen durch Einschluss oder Ausschluss bestimmter Wörter in die bzw. aus der Suchabfrage. Andere Verfahren wie die Verwendung von Eigenschaftsoperatoren (wie \>= or ..), Fragezeichen, Klammern und Platzhaltern helfen Ihnen, eDiscovery-Suchabfragen zu verfeinern. In der folgenden Tabelle sind die Operatoren aufgelistet, die Sie verwenden können, um Ihre Suchergebnisse einzugrenzen oder zu erweitern.


> [!IMPORTANT]
> Sie müssen boolesche Operatoren in einer Suchabfrage in Großbuchstaben angeben. Verwenden Sie beispielsweise <STRONG>AND</STRONG> und nicht <STRONG>and</STRONG>. Bei Suchoperatoren in Kleinbuchstaben in Suchabfragen wird ein Fehler zurückgegeben.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Operator</th>
<th>Verwendung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AND</p></td>
<td><p>Wort1 AND Wort2</p></td>
<td><p>Gibt Nachrichten zurück, die alle angegebenen Schlüsselwörter oder <code>property:value</code>-Ausdrücke enthalten.</p></td>
</tr>
<tr class="even">
<td><p>+</p></td>
<td><p>Wort1 +Wort2 +Wort3</p></td>
<td><p>Gibt die Elemente zurück, die <em>entweder</em><code>keyword2 </code> oder <code>keyword3</code><em>enthalten und</em>, die ebenfalls <code>keyword1</code> enthalten. Damit entspricht dieses Beispiel der Abfrage <code>(keyword2 OR keyword3) AND keyword1</code>.</p>
<p>Beachten Sie, dass die Abfrage <code>keyword1 + keyword2</code> (mit einem Leerzeichen nach dem <strong>+</strong>-Symbol) nicht der Verwendung des <strong>UND</strong>-Operators entspricht. Diese Abfrage wäre gleichbedeutend mit <code>&quot;keyword1 + keyword2&quot;</code> und gibt Elemente mit dem exakten Ausdruck <code>&quot;keyword1 + keyword2&quot;</code> zurück.</p></td>
</tr>
<tr class="odd">
<td><p>OR</p></td>
<td><p>Wort1 OR Wort2</p></td>
<td><p>Gibt Nachrichten zurück, die ein oder alle angegebenen Schlüsselwörter oder <code>property:value</code>-Ausdrücke enthalten.</p></td>
</tr>
<tr class="even">
<td><p>NOT</p></td>
<td><p>Wort1 NOT Wort2</p>
<p>NOT Von:&quot;Ann Beebe&quot;</p></td>
<td><p>Schließt Nachrichten mit einem bestimmten Schlüsselwort oder <code>property:value</code>-Ausdruck aus. Mit <code>NOT from:&quot;Ann Beebe&quot;</code> werden z. B. Nachrichten ausgeschlossen, die von Ann Beebe gesendet wurden.</p></td>
</tr>
<tr class="odd">
<td><p>-</p></td>
<td><p>Wort1 - Wort2</p></td>
<td><p>Identisch mit dem Operator <strong>NOT</strong>. Diese Abfrage gibt Elemente zurück, die <code>keyword1</code> enthalten und schließt Elemente aus, die <code>keyword2</code> enthalten.</p></td>
</tr>
<tr class="even">
<td><p>NEAR</p></td>
<td><p>Wort1 NEAR(n) Wort2</p></td>
<td><p>Gibt Nachrichten mit Wörtern zurück, die sich nah sind, wobei &quot;n&quot; der Anzahl der Wörter entspricht, die den Abstand zwischen den gesuchten Wörtern darstellen. <code>best NEAR(5) worst</code> gibt z. B. Nachrichten zurück, in denen sich das Wort &quot;schlecht&quot; höchstens fünf Wörter neben dem Wort &quot;gut&quot; befindet. Wenn keine Anzahl angegeben wird, wird der Standardabstand von 8 Wörtern verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>:</p></td>
<td><p>Eigenschaftswert</p></td>
<td><p>Der Doppelpunkt (:) in der <code>property:value</code>-Syntax gibt an, dass der Eigenschaftswert, nach dem gesucht wird, dem angegebenen Wert entspricht. <code>recipients:garthf@contoso.com</code> gibt z. B. jede an garthf@contoso.com gesendete Nachricht zurück.</p></td>
</tr>
<tr class="even">
<td><p>&lt;</p></td>
<td><p>Eigenschaft&lt;Wert</p></td>
<td><p>Zeigt an, dass die Eigenschaft, nach der gesucht wird, kleiner ist als der angegebene Wert.1</p></td>
</tr>
<tr class="odd">
<td><p>&gt;</p></td>
<td><p>Eigenschaft&gt;Wert</p></td>
<td><p>Zeigt an, dass die Eigenschaft, nach der gesucht wird, größer ist als der angegebene Wert.1</p></td>
</tr>
<tr class="even">
<td><p>&lt;=</p></td>
<td><p>Eigenschaft&lt;=Wert</p></td>
<td><p>Zeigt an, dass die Eigenschaft, nach der gesucht wird, kleiner gleich dem angegebenen Wert ist.1</p></td>
</tr>
<tr class="odd">
<td><p>&gt;=</p></td>
<td><p>Eigenschaft&gt;=Wert</p></td>
<td><p>Zeigt an, dass die Eigenschaft, nach der gesucht wird, größer gleich dem angegebenen Wert ist.1</p></td>
</tr>
<tr class="even">
<td><p>..</p></td>
<td><p>property:value1..value2</p></td>
<td><p>Zeigt an, dass die Eigenschaft, nach der gesucht wird, größer gleich Wert1 und kleiner gleich Wert2 ist.1</p></td>
</tr>
<tr class="odd">
<td><p>&quot; &quot;</p></td>
<td><p>&quot;fair Value&quot;</p>
<p>Betreff:&quot;Vierteljährliche Finanzdaten&quot;</p></td>
<td><p>Verwenden Sie doppelte Anführungszeichen (&quot; &quot;), um nach einem genauen Satz oder Begriff in Schlüsselwort- und <code>property:value</code>Suchanfragen zu suchen.</p></td>
</tr>
<tr class="even">
<td><p>*</p></td>
<td><p>cat*</p>
<p>Betreff:set*</p></td>
<td><p>Präfixsuchen mit Platzhalter (in denen das Sternchen an das Ende eines Wortes platziert wird) eignen sich für null oder mehr Zeichen in Schlüsselwort- oder <code>property:value</code>-Abfragen. <code>subject:set*</code> gibt z. B. Nachrichten zurück, in deren &quot;Betreff&quot;-Zeile das Wort set, setup oder setting (und andere Wörter, die mit &quot;set&quot; beginnen) enthalten ist.</p></td>
</tr>
<tr class="odd">
<td><p>( )</p></td>
<td><p>(fair OR frei) AND Von:contoso.com</p>
<p>(IPO OR Initiale) AND (Aktien OR Anteile)</p>
<p>(Vierteljährliche Finanzdaten)</p></td>
<td><p>Mit Klammern werden Boolesche Ausdrücke, <code>property:value</code>-Elemente und Schlüsselwörter gruppiert. <code>(quarterly financials)</code> gibt z. B. Elemente zurück, die die Wörter &quot;Vierteljährliche&quot; und &quot;Finanzdaten&quot; enthalten.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 1&nbsp;&nbsp;&nbsp;Verwenden Sie diesen Operator für Eigenschaften, die Datums- oder Zahlenwerte enthalten.



## Nicht unterstützte Zeichen in Suchabfragen

Nicht unterstützte Zeichen in einer Suchabfrage führen gewöhnlich zu einem Suchfehler oder zu unerwarteten Ergebnissen. Nicht unterstützte Zeichen sind häufig ausgeblendet und werden der Abfrage hinzugefügt, wenn Sie die Abfrage oder Teile davon aus anderen Anwendungen (z. B. Microsoft Word oder Microsoft Excel) in das Schlüsselwortfeld auf der Abfrageseite der In-Situ-eDiscovery-Suche kopieren.

Im Folgenden finden Sie eine Liste der nicht unterstützten Zeichen für eine In-Situ-eDiscovery-Suchabfrage.

  - **Typografische Anführungszeichen**   Typografische einfache und doppelte Anführungszeichen werden nicht unterstützt. Nur gerade Anführungszeichen können in einer Suchabfrage verwendet werden.

  - **Nicht druckbare Zeichen und Steuerzeichen**   Nicht druckbare Zeichen und Steuerzeichen stellen kein schriftliches Symbol dar, wie z. B. ein alphanumerisches Zeichen. Beispiele für nicht druckbare Zeichen und Steuerzeichen sind Zeichen, die Text formatieren oder Textzeilen trennen.

  - **Links-nach-rechts- und Rechts-nach-links-Markierungen**   Dies sind Steuerzeichen zur Anzeige der Textrichtung für Links-nach-rechts-Sprachen (wie Englisch und Spanisch) und Rechts-nach-links-Sprachen (wie Arabisch und Hebräisch).

  - **Boolesche Operatoren in Kleinbuchstaben**   Wie oben erläutert, müssen Sie in einer Suchabfrage boolesche Operatoren in Großbuchstaben verwenden, z. B. **AND** und **OR**. Beachten Sie, dass in der Abfragesyntax häufig die Verwendung eines booleschen Operators in Kleinbuchstaben angegeben sein kann, beispielsweise `(WordA or WordB) and (WordC or WordD)`.

**Wie können Sie nicht unterstützte Zeichen in Ihren Suchabfragen verhindern?**Die beste Möglichkeit zur Verhinderung nicht unterstützter Zeichen besteht darin, die Abfrage direkt in das Schlüsselwortfeld einzugeben. Alternativ können Sie eine Abfrage aus Word oder Excel kopieren und in einem Nur-Text-Editor, z. B. Microsoft Editor, in eine Datei einfügen. Speichern Sie dann die Textdatei, und wählen Sie **ANSI** in der Dropdownliste **Codierung** aus. Dadurch werden alle Formatierungen und nicht unterstützten Zeichen entfernt. Anschließend können Sie die Abfrage aus der Textdatei kopieren und im Schlüsselwort-Abfragefeld einfügen.

## Tipps und Tricks für die Suche

  - Schlüsselwortsuchen unterscheiden nicht zwischen Groß- und Kleinschreibung. Beispielsweise geben **katze** und **KATZE** dieselben Ergebnisse zurück.

  - Ein Leerzeichen zwischen zwei Schlüsselwörtern oder zwei `property:value`-Ausdrücken hat dieselbe Bedeutung wie die Verwendung des Operators **AND**. `from:"Sara Davis" subject:reorganization` gibt z. B. alle Nachrichten zurück, die von Sara David gesendet wurden und deren "Betreff"-Zeile das Wort **Reorganisation** enthält.

  - Verwenden Sie eine Syntax, die dem `property:value`-Format entspricht. Für die Werte ist die Groß- und Kleinschreibung unerheblich, aber es darf kein Leerzeichen hinter dem Operator stehen. Wenn dort ein Leerzeichen steht, wird eine Volltextsuche nach dem gewünschten Wert durchgeführt. Beispiel:**An: pilarp** wird z B. nach "pilarp" als Schlüsselwort gesucht statt nach Nachrichten, die an pilarp gesendet wurden.

  - Wenn Sie nach einer Empfängereigenschaft wie An, Von, Cc oder Empfänger suchen, können Sie eine SMTP-Adresse, einen Alias oder einen Anzeigenamen verwenden, um einen Empfänger anzugeben. Sie können z. B. pilarp@contoso.com, pilarp oder "Pilar Pinilla" verwenden.

  - Sie können nur Präfixsuchen mit Platzhalter verwenden – z. B. **cat\*** oder **set\***. Suffixsuchen mit Platzhalter (\*cat) oder Teilzeichenfolgensuchen mit Platzhalter (\*cat\*) werden nicht unterstützt.

  - Wenn Sie nach einer Eigenschaft suchen, verwenden Sie doppelte Anführungszeichen (" "), wenn der Suchwert aus mehreren Wörtern besteht. Für **Betreff:Budget Q1** werden z. B. Nachrichten zurückgegeben, deren „Betreff“-Zeile **Budget** enthält und denen irgendwo in der Nachricht oder einer der Nachrichteneigenschaften **Q1** vorkommt. Für **Betreff:"Budget Q1"** werden alle Nachrichten zurückgegeben, deren „Betreff“-Zeile **Budget Q1** enthält.

