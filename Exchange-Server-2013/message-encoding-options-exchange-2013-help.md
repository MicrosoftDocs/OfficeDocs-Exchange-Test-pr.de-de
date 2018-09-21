---
title: 'Nachrichtencodierungsoptionen: Exchange 2013 Help'
TOCTitle: Nachrichtencodierungsoptionen
ms:assetid: c1d9edbb-d87c-41e5-881b-cd612d83d7e4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb310794(v=EXCHG.150)
ms:contentKeyID: 50476633
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichtencodierungsoptionen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit den Nachrichtencodierungsoptionen, die in den Exchange zur Verfügung stehen, werden nachrichtenspezifische Eigenschaften wie MIME- und Nicht-MIME-Zeichensätze, Binärcodierung und Anlagenformate angegeben. Sie können Nachrichtencodierungsoptionen an folgenden Speicherorten angeben:

  - Remotedomäneneinstellungen

  - E-Mail-Benutzer- und E-Mail-Kontakteinstellungen

  - Microsoft Outlook-Einstellungen
    
      - Nachrichtenformat
    
      - Internet-Nachrichtenformat
    
      - Nachrichtenformat für Internetempfänger
    
      - Nachrichtenzeichensatz-Codierungsoptionen

**Inhalts-**

Nachrichtencodierungsoptionen für Nachrichten, die an Remotedomänen gesendet werden

Nachrichtencodierungsoptionen für E-Mail-Benutzer und E-Mail-Kontakte

In Outlook verfügbare Nachrichtencodierungsoptionen

In Outlook Web App verfügbare Nachrichtencodierungsoptionen

Priorität von Nachrichtencodierungsoptionen

Weitere Informationen

## Nachrichtencodierungsoptionen für Nachrichten, die an Remotedomänen gesendet werden

Bei der Konfiguration von Nachrichtencodierungsoptionen für Remotedomänen werden spezifische Einstellungen für alle an die Domäne gesendeten Nachrichten angewendet. Für Remotedomänen stehen in Ihrer Organisation die folgenden Konfigurationsoptionen für die Nachrichtencodierung zur Verfügung.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Einstellung</strong></p></td>
<td><p><strong>Verfügbar im EAC in Exchange Online Dedicated</strong></p></td>
<td><p><strong>Verfügbar in der Shell</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>MIME-Zeichensatz</strong>   Der hier angegebene Zeichensatz wird nur für MIME-Nachrichten verwendet, in denen kein eigener Zeichensatz angegeben ist. Durch das Festlegen dieses Parameters werden keine Zeichensätze außer Kraft gesetzt, die bereits in der ausgehenden Nachricht angegeben sind.</p>
<p><strong>Nicht-MIME-Zeichensatz</strong>   Diese Einstellung wird verwendet, wenn eine der folgenden Bedingungen erfüllt ist:</p>
<ul>
<li><p>Eingehende Nachrichten von einer Remotedomäne, in denen der Wert der Einstellung <em>charset=</em> im MIME-Inhaltstyp fehlt: Kopfzeilenfeld.</p></li>
<li><p>Ausgehende Nachrichten an eine Remotedomäne, in denen der Wert des MIME-Zeichensatzes fehlt.</p></li>
</ul>
<p></p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p><strong>Inhaltstyp</strong>   Dieser Parameter gibt den Inhaltstyp für MIME-Nachrichten an, die an Empfänger in der Remotedomäne gesendet werden. Sie können folgende Einstellungen verwenden:</p>
<ul>
<li><p><strong>MimeHtmlText</strong>   Alle Nachrichten werden in MIME-Nachrichten mit HTML-Formatierung konvertiert, es sei denn, die ursprüngliche Nachricht ist eine Textnachricht. Wenn die ursprüngliche Nachricht eine Textnachricht ist, handelt es sich bei der ausgehenden Nachricht um eine MIME-Nachricht mit Textformatierung. Dies ist die Standardeinstellung.</p></li>
<li><p><strong>MimeText</strong>   Alle Nachrichten werden in MIME-Nachrichten mit Textformatierung konvertiert.</p></li>
<li><p><strong>MimeHtml</strong>   Alle Nachrichten werden in MIME-Nachrichten mit HTML-Formatierung konvertiert.</p></li>
</ul></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Zeilenumbruchgröße</strong>   Sie können die maximale Anzahl von Zeichen angeben, die in einer einzelnen Textzeile im Nachrichtentext der E-Mail-Nachricht enthalten sein kann. Ältere E-Mail-Client-Anwendungen bevorzugen möglicherweise 78 Zeichen pro Zeile. Diese Option steht nur für die Shell zur Verfügung.</p>
<p></p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichtencodierungsoptionen für E-Mail-Benutzer und E-Mail-Kontakte

Wenn Sie Nachrichtencodierungsoptionen für einen E-Mail-Kontakt oder einen E-Mail-Benutzer konfigurieren, wird diese Option auf alle an den bestimmten Empfänger gesendeten Nachrichten angewendet. Für E-Mail-Kontakte oder einen E-Mail-Benutzer stehen in Ihrer Organisation die folgenden Konfigurationsoptionen für die Nachrichtencodierung zur Verfügung:

  - **UsePreferMessageFormat**   Dieser Parameter gibt an, ob die für den E-Mail-Kontakt konfigurierten Einstellungen für das Nachrichtenformat die globalen Einstellungen außer Kraft setzen sollen, die für die Remotedomäne konfiguriert sind. Wenn Sie diese Einstellung deaktivieren, ignoriert Exchange weitere Nachrichtencodierungsoptionen für diesen Empfänger. Die Nachrichtencodierung wird dann durch die Konfiguration der Remotedomäne oder den vom Absender der Nachricht konfigurierten Einstellungen bestimmt.

  - **MessageFormat**   Dieser Parameter gibt das Format einer Nachricht an. Sie können entweder "Text" oder "MIME" als Nachrichtenformat angeben. Der Wert dieser Einstellung ist von dem Parameter *MessageBodyFormat* abhängig. Wenn das Format des Nachrichtentexts "Html" oder "TextAndHtml" lautet, muss dieser Parameter auf "Mime" festgelegt werden.

  - **MessageBodyFormat**   Dieser Parameter gibt das Format des Nachrichtentexts an. Sie können "Text", "HTML" oder "TextAndHtml" angeben. Der Wert dieser Einstellung ist von dem Parameter *MessageFormat* abhängig. Wenn das Nachrichtenformat "Text" lautet, muss dieser Parameter auf "Text" festgelegt werden.

  - **MacAttachmentFormat**   Dieser Parameter gibt das Anlagenformat des Apple Macintosh-Betriebssystems für Nachrichten an. Sie können "BinHex", "UuEncode", "AppleSingle" oder "AppleDouble" angeben. Der Wert dieser Einstellung ist von dem Parameter *MessageFormat* abhängig. Wenn das Nachrichtenformat "Text" lautet, muss dieser Parameter auf "BinHex" oder "UuEncode" festgelegt werden. Wenn das Nachrichtenformat "Mime" lautet, muss dieser Parameter auf "BinHex", "AppleSingle" oder "AppleDouble" festgelegt werden.

Sie müssen diese Parameter in der Exchange-Verwaltungsshell verwenden, um die Nachrichtencodierungsoptionen für E-Mail-Benutzer und E-Mail-Kontakte festzulegen. Weitere Informationen hierzu finden Sie unter den folgenden Themen:

  - [Enable-MailContact](https://technet.microsoft.com/de-de/library/aa996001\(v=exchg.150\))

  - [New-MailContact](https://technet.microsoft.com/de-de/library/bb124519\(v=exchg.150\))

  - [Set-MailContact](https://technet.microsoft.com/de-de/library/aa995950\(v=exchg.150\))

  - [Enable-MailUser](https://technet.microsoft.com/de-de/library/aa996549\(v=exchg.150\))

  - [New-MailUser](https://technet.microsoft.com/de-de/library/aa996335\(v=exchg.150\))

  - [Set-MailUser](https://technet.microsoft.com/de-de/library/aa995971\(v=exchg.150\))

Zurück zum Seitenanfang

## In Outlook verfügbare Nachrichtencodierungsoptionen

Als Absender können Sie Nachrichtencodierungsoptionen in Outlook in jeder der folgenden Phasen angeben:

  - Konfigurieren des Standardnachrichtenformats auf "Nur-Text" oder "HTML".

  - Festlegen des Nachrichtenformats auf "Nur-Text" oder "HTML" auf der Registerkarte **Optionen** im Bereich **Format**.

  - Konfigurieren der Nachrichtencodierungsoptionen für Nachrichten, die an alle Empfänger außerhalb der Exchange-Organisation gesendet werden. Diese Optionen werden als *Internet-Nachrichtenformatoptionen* bezeichnet. Die Optionen gelten nur für Remoteempfänger und nicht für Empfänger in der Exchange-Organisation.

  - Konfigurieren der Nachrichtencodierungsoptionen für Nachrichten, die an bestimmte Empfänger außerhalb der Exchange-Organisation gesendet werden. Diese Optionen werden als *Nachrichtenformat für Internetempfänger* bezeichnet. Die Optionen gelten nur für Remoteempfänger in Ihrem Ordner "Kontakte" und nicht für Empfänger in der Exchange-Organisation.

Standardmäßig verwendet Outlook die automatische Zeichensatz-Nachrichtencodierung, indem der gesamte Text der ausgehenden Nachricht durchsucht wird, um die entsprechende Codierung für die Nachricht zu ermitteln. Diese Einstellung gilt für Nachrichten, die Sie an Internetempfänger und Empfänger in der Exchange-Organisation senden. Sie können dies jedoch umgehen und eine bevorzugte Codierung für ausgehende Nachrichten angegeben.

Zurück zum Seitenanfang

## In Outlook Web App verfügbare Nachrichtencodierungsoptionen

Als Absender können Sie Nachrichtencodierungsoptionen in Outlook Web App in jeder der folgenden Phasen angeben:

  - Durch Konfigurieren des Standardnachrichtenformats als "Nur-Text" oder "HTML" im Abschnitt **Nachrichtenformat** auf der Seite **Einstellungen** \>**Optionen** \> **Einstellungen**.

  - Durch Festlegen des Nachrichtenformats beim Erstellen einer Nachricht auf "Nur-Text" oder "HTML" über das Menü **Weitere Optionen (…)** und Auswählen von **Zu Nur-Text wechseln** oder **Zu HTML wechseln**.

Zurück zum Seitenanfang

## Priorität von Nachrichtencodierungsoptionen

Exchange geht in der Reihenfolge der folgenden Liste vor, um die Nachrichtencodierungsoptionen für ausgehende Nachrichten zu ermitteln, die an Empfänger außerhalb der Exchange-Organisation gesendet werden:

1.  Remotedomäneneinstellungen

2.  Einstellungen für Outlook Web App und Outlook

3.  E-Mail-Benutzer- oder E-Mail-Kontakteinstellungen

In dieser Liste ist die Reihenfolge absteigend aufgeführt. Eine auf einer höheren Ebene vorgenommene Einstellung kann eine Einstellung auf niedrigerer Ebene außer Kraft setzen.

In der folgenden Tabelle ist die Reihenfolge der Priorität (von der niedrigsten bis zur höchsten Priorität) für Codierungsoptionen von Nachrichtenzeichensätzen beschrieben.

### Reihenfolge der Priorität von der niedrigsten bis zur höchsten Priorität für Codierungsoptionen von Nachrichtenzeichensätzen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einstellung des Remotedomäneneintrags mithilfe von EAC oder <strong>Set-RemoteDomain</strong></p></td>
<td><p><em>CharacterSet</em></p></td>
<td><p>Angegeben</p></td>
</tr>
<tr class="even">
<td><p>Einstellung des Remotedomäneneintrags mithilfe von EAC oder <strong>Set-RemoteDomain</strong></p></td>
<td><p><em>NonMimeCharacterSet</em></p></td>
<td><p>Angegeben</p></td>
</tr>
<tr class="odd">
<td><p>Outlook-Einstellungen</p></td>
<td><p>Nachrichtenzeichensatzcodierung</p></td>
<td><ul>
<li><p>Automatische Auswahl</p></li>
<li><p>Angegeben</p></li>
</ul></td>
</tr>
</tbody>
</table>


Wenn Sie den Nicht-MIME-Zeichensatz für eine Remotedomäne festlegen, wird der Zeichensatz den folgenden Nachrichtentypen zugewiesen:

  - Ausgehende Nachrichten an eine konfigurierte Remotedomäne, die keinen bestimmten Zeichensatz enthalten.

  - Eingehende Nachrichten von einer konfigurierten Remotedomäne, die keinen bestimmten Zeichensatz enthalten.

Der Wert der Windows ANSI-Codeseite für den Transportserver wird zum Zuordnen eines Zeichensatzes zu folgenden Nachrichtentypen verwendet:

  - Interne Nachrichten, die keinen angegebenen Zeichensatz enthalten.

  - Interne Nachrichten, die einen bestimmten Zeichensatz, aber keine bestimmte Codeseite enthalten.

Wenn eine Nachricht einen angegebenen, aber ungültigen Zeichensatz enthält, versucht der Transportserver, den ungültigen Zeichensatz durch einen gültigen zu ersetzen.

In der folgenden Tabelle ist die Reihenfolge der Priorität (von der niedrigsten bis zur höchsten Priorität) für Nur-Text-Nachrichtencodierungsoptionen beschrieben.

### Reihenfolge der Priorität von der niedrigsten bis zur höchsten Priorität für Nur-Text-Nachrichtencodierungsoptionen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-RemoteDomain</strong></p></td>
<td><p><em>LineWrapSize</em></p></td>
<td><ul>
<li><p>0 bis 132</p></li>
<li><p>Unbeschränkt</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook-Einstellungen</p></td>
<td><p>Nachrichtenformat</p></td>
<td><p>Nur-Text</p></td>
</tr>
<tr class="odd">
<td><p>Outlook-Einstellungen</p></td>
<td><p>Internet-Nachrichtenformat</p></td>
<td><p>Nur-Text-Optionen:</p>
<ul>
<li><p>Anlagen von Nur-Text-Nachrichten mit &quot;UuEncode&quot; codieren</p></li>
<li><p>Automatischer Textumbruch bei <em>nn</em> Zeichen</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook-Einstellungen</p></td>
<td><p>Nachrichtenformat für Internetempfänger</p></td>
<td><p>Nur-Text-Format:</p>
<ul>
<li><p>Codieren von Anlagen im Format &quot;UuEncode&quot;</p></li>
<li><p>Verwenden des Anlagenformats &quot;BinHex&quot; für Mac</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>UsePreferMessageFormat</em></p></td>
<td><ul>
<li><p><code>$true</code></p></li>
<li><p><code>$false</code></p></li>
</ul>
<p>Wenn der Wert <code>$false</code> lautet oder der Empfänger nicht als E-Mail-Benutzer oder E-Mail-Kontakt in der Exchange-Organisation definiert ist, werden die Einstellungen des E-Mail-Benutzers oder E-Mail-Kontakts ignoriert.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MessageFormat</em></p></td>
<td><p>Text</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MessageBodyFormat</em></p></td>
<td><p>Text</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MacAttachmentFormat</em></p></td>
<td><ul>
<li><p>BinHex</p></li>
<li><p>UuEncode</p></li>
</ul></td>
</tr>
</tbody>
</table>


In der folgenden Tabelle ist die Reihenfolge der Priorität (von der niedrigsten bis zur höchsten Priorität) für MIME-Nachrichtencodierungsoptionen beschrieben.

### Reihenfolge der Priorität von der niedrigsten bis zur höchsten Priorität für MIME-Nachrichtencodierungsoptionen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-RemoteDomain</strong></p></td>
<td><p><em>ContentType</em></p></td>
<td><ul>
<li><p><code>MimeHtmlText</code></p></li>
<li><p><code>MimeText</code></p></li>
<li><p><code>MimeHtml</code></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Einstellungen für Outlook Web App und Outlook</p></td>
<td><p>Nachrichtenformat</p></td>
<td><ul>
<li><p>Nur-Text</p></li>
<li><p>HTML</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook-Einstellungen</p></td>
<td><p>Nachrichtenformat für Internetempfänger</p></td>
<td><p>MIME-Nachrichtenformat</p>
<ul>
<li><p>Nur-Text</p></li>
<li><p>Nur-Text und HTML</p></li>
<li><p>HTML</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>UsePreferMessageFormat</em></p></td>
<td><p><code>$true</code></p>
<p><code>$false</code></p>
<p>Wenn der Wert <code>$false</code> lautet oder der Empfänger nicht als E-Mail-Benutzer oder E-Mail-Kontakt in der Exchange-Organisation definiert ist, werden die Einstellungen des E-Mail-Benutzers oder E-Mail-Kontakts ignoriert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MessageFormat</em></p></td>
<td><ul>
<li><p>Text</p></li>
<li><p>Mime</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MessageBodyFormat</em></p></td>
<td><ul>
<li><p><code>Text</code></p></li>
<li><p><code>Html</code></p></li>
<li><p><code>TextAndHtml</code></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailContact</strong></p></td>
<td><p><em>MacAttachmentFormat</em></p></td>
<td><ul>
<li><p>BinHex</p></li>
<li><p>AppleSingle</p></li>
<li><p>AppleDouble</p></li>
</ul></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Weitere Informationen

[Nachrichtencodierungsoptionen](message-encoding-options-exchange-2013-help.md)

[TNEF-Konvertierungsoptionen](tnef-conversion-options-exchange-2013-help.md)

[Remotedomänen](remote-domains-exchange-2013-help.md)

[Remotedomänen in Exchange Online](https://technet.microsoft.com/de-de/library/jj966211\(v=exchg.150\))

[Verwalten von E-Mail-Benutzern](https://technet.microsoft.com/de-de/library/Bb124381(v=EXCHG.150))

[Verwalten von E-Mail-Kontakten](https://technet.microsoft.com/de-de/library/Aa998858(v=EXCHG.150))

[Ändern des Nachrichtenformats in Outlook](https://go.microsoft.com/fwlink/p/?linkid=397890)

