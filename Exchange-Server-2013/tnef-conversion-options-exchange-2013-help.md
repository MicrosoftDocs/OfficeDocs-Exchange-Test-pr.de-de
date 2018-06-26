---
title: 'TNEF-Konvertierungsoptionen: Exchange 2013 Help'
TOCTitle: TNEF-Konvertierungsoptionen
ms:assetid: 989a62fc-4bc1-448f-90c8-7c7b56fe1084
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb310786(v=EXCHG.150)
ms:contentKeyID: 52062744
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# TNEF-Konvertierungsoptionen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie können angeben, ob TNEF-Informationen (Transport Neutral Encapsulation Format) in Nachrichten, die die Exchange-Organisation verlassen, beibehalten oder daraus entfernt werden sollen. TNEF, auch Outlook Rich Text Format oder Exchange Rich Text Format genannt, ist ein Microsoft-spezifisches Format für die Kapselung von MAPI-Nachrichteneigenschaften. Alle Versionen von MicrosoftOutlook verstehen TNEF vollständig. Outlook Web App übersetzt TNEF in MAPI und zeigt die formatierten Meldungen an. Andere E-Mail-Clients, die TNEF nicht verstehen, zeigen mit TNEF formatierte Nachrichten als einfache Textnachrichten mit Anlagen vom Typ "Winmail.dat" oder "Win.dat" an.

**Inhalt**

TNEF-Konvertierungsoptionen für Remotedomänen

TNEF-Konvertierungsoptionen für E-Mail-Benutzer und -Kontakte

TNEF-Konvertierungsoptionen in Outlook

Priorität von TNEF-Konvertierungsoptionen

## TNEF-Konvertierungsoptionen für Remotedomänen

Wenn Sie TNEF-Konvertierungsoptionen für eine Remotedomäne konfigurieren, werden diese TNEF-Konvertierungsoptionen auf alle an diese Domäne gesendeten Nachrichten angewendet.

  - Für Exchange Online Dedicated verwenden Sie die Exchange-Verwaltungskonsole (EAC), um unter **Nachrichtenfluss** \> **Remotedomänen** \> **Bearbeiten** (![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol")) \> **Exchange-Rich-Text-Format verwenden** TNEF-Konvertierungsoptionen für eine Remotedomäne festzulegen.

  - In Exchange Online und Exchange 2013 wird zum Konfigurieren der TNEF-Konvertierungsoptionen für eine Remotedomäne der Parameter *TnefEnabled* für das Cmdlet **Set-RemoteDomain** angegeben.

Für Remotedomänen in der Organisation stehen Ihnen die folgenden Konfigurationsoptionen für die TNEF-Konvertierung zur Verfügung:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>In der Exchange-Verwaltungskonsole</th>
<th>In der Shell</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TNEF wird für alle Nachrichten verwendet, die an die Remotedomäne gesendet werden.</p></td>
<td><p><strong>Always</strong></p></td>
<td><p><code>$true</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF wird niemals für Nachrichten verwendet, die an die Remotedomäne gesendet werden.</p></td>
<td><p><strong>Never</strong></p></td>
<td><p><code>$false</code></p></td>
</tr>
<tr class="odd">
<td><p>TNEF-Nachrichten werden für Empfänger in der Remotedomäne weder dediziert zugelassen noch verhindert. Ob TNEF-Nachrichten an Empfänger in der Remotedomäne gesendet werden, hängt von der speziellen Einstellung für den E-Mail-Kontakt oder -Benutzer oder von der durch den Absender in Outlook angegebenen Einstellung ab. Dies ist der Standardwert.</p></td>
<td><p><strong>Benutzereinstellungen verwenden</strong></p></td>
<td><p><code>$null</code> (leer)</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Remotedomänen finden Sie unter [Remotedomänen](remote-domains-exchange-2013-help.md) oder [Remotedomänen in Exchange Online](https://technet.microsoft.com/de-de/library/jj966211\(v=exchg.150\)).

Zurück zum Seitenanfang

## TNEF-Konvertierungsoptionen für E-Mail-Benutzer und -Kontakte

Wenn Sie die TNEF-Konvertierungsoptionen für einen E-Mail-Kontakt oder einen E-Mail-Benutzer konfigurieren, werden diese TNEF-Konvertierungsoptionen auf alle Nachrichten angewendet, die an den jeweiligen Empfänger gesendet werden. Zum Konfigurieren der TNEF-Konvertierungsoptionen für E-Mail-Benutzer und -Kontakte wird der Parameter *UseMapiRichTextFormat* für die Cmdlets **Set-MailUser** und **Set-MailContact** angegeben.

Für E-Mail-Benutzer und -Kontakte in der Organisation stehen Ihnen die folgenden Konfigurationsoptionen für die TNEF-Konvertierung zur Verfügung:

  - **Immer**   TNEF wird für alle Nachrichten verwendet, die an den Empfänger gesendet werden. Der entsprechende Wert für den Parameter *UseMapiRichTextFormat* ist `Always`.

  - **Nie**   TNEF wird nie für Nachrichten verwendet, die an den Empfänger gesendet werden. Der entsprechende Wert für den Parameter *UseMapiRichTextFormat* ist `Never`.

  - **Standardeinstellungen verwenden**   TNEF-Nachrichten werden für den E-Mail-Benutzer oder den E-Mail-Kontakt nicht dediziert zugelassen oder verhindert. Ob TNEF-Nachrichten an den Empfänger gesendet werden, hängt von der speziellen Einstellung für die entsprechende Remotedomäne oder von der durch den Absender in Outlook angegebenen Einstellung ab. Der entsprechende Wert für den Parameter *UseMapiRichTextFormat* ist `UseDefaultSettings`. Dies ist die Standardeinstellung.

Zurück zum Seitenanfang

## TNEF-Konvertierungsoptionen in Outlook

Absender können die standardmäßigen TNEF-Nachrichtenkonvertierungsoptionen für TNEF-Nachrichten steuern, die an alle Empfänger außerhalb der Exchange-Organisation gesendet werden. Diese Optionen werden als *Internet-Nachrichtenformatoptionen* bezeichnet. Die Optionen gelten nur für Remoteempfänger und nicht für Empfänger in der Exchange-Organisation.


> [!NOTE]
> Anhand der folgenden Optionen wird definiert, wie Nachrichten, die Outlook-Rich-Text enthalten, verarbeitet werden, wenn sie an externe Empfänger gesendet werden. Wenn Sie als Nachrichtenformat HTML oder Nur-Text verwenden, gelten diese Einstellungen nicht.



In Outlook stehen Ihnen die folgenden TNEF-Konvertierungsoptionen zur Verfügung:

  - **In HTML-Format konvertieren**   Dies ist die Standardoption. Alle TNEF-Nachrichten, die an Remoteempfänger gesendet werden, werden in das HTML-Format konvertiert. Die gesamte Formatierung der Nachricht sollte im Wesentlichen der der ursprünglichen Nachricht entsprechen. MIME-codierte HTML-Nachrichten werden von vielen, jedoch nicht von allen E-Mail-Clients unterstützt.

  - **In Nur-Text-Format konvertieren**   Alle TNEF-Nachrichten an Remoteempfänger werden in das Nur-Text-Format konvertiert. Die gesamte Formatierung der Nachricht geht damit verloren.

  - **Im Outlook-Rich-Text-Format senden**   Alle TNEF-Nachrichten an Remoteempfänger bleiben TNEF-Nachrichten.

Sie können diese Optionen an den folgenden Stellen in Outlook konfigurieren:

  - **Outlook 2010 oder Outlook 2013** **Datei** \> **Optionen** \> **E-Mail** \> **Nachrichtenformat**.

  - **Outlook 2007** **Extras** \> **Optionen** \> **E-Mail-Format** \> **Internetformat**.

Absender können auch die standardmäßigen TNEF-Nachrichtenkonvertierungsoptionen für TNEF-Nachrichten steuern, die an bestimmte Empfänger außerhalb der Exchange-Organisation gesendet werden. Diese Optionen werden als *Nachrichtenformat für Internetempfänger* bezeichnet. Die Optionen gelten nur für in Ihrem Ordner "Kontakte" gespeicherte Remoteempfänger und nicht für Empfänger in der Exchange-Organisation. Für Remoteempfänger im Ordner "Kontakte" stehen Ihnen die folgenden TNEF-Konvertierungsoptionen zur Verfügung:

  - **Outlook wählt das optimale Sendeformat**   Dies ist die Standardeinstellung. Mit dieser Einstellung wird Outlook gezwungen, die TNEF-Konvertierungsoption zu verwenden, die mit dem standardmäßigen Internetformat festgelegt wurde. Die möglichen Werte sind **In HTML-Format konvertieren**, **In Nur-Text-Format konvertieren** oder **Im Outlook-Rich-Text-Format senden**. Auf diese Weise kann die TNEF-Nachricht im TNEF-Format bleiben, in HTML oder in das Nur-Text-Format konvertiert werden. Wenn Sie sicherstellen möchten, dass die TNEF-Nachricht für diesen Empfänger im TNEF-Format bleibt, sollten Sie diese Einstellung von **Outlook wählt das optimale Sendeformat** in **Im Outlook-Rich-Text-Format senden** ändern.

  - **Als Nur-Text senden**   Alle TNEF-Nachrichten an den Empfänger werden in das Nur-Text-Format konvertiert. Die gesamte Formatierung der Nachricht geht damit verloren.

  - **Im Outlook-Rich-Text-Format senden**   Alle TNEF-Nachrichten an Remoteempfänger bleiben TNEF-Nachrichten.

Sie können diese Optionen für einen Kontakt an den folgenden Stellen in Outlook konfigurieren:

  - **Outlook 2010 oder Outlook 2013**   Öffnen Sie die Kontaktkarte, doppelklicken Sie auf die E-Mail-Adresse, klicken Sie auf das Symbol **Weitere Optionen für die Interaktion mit dieser Person anzeigen**, und wählen Sie **Outlook-Eigenschaften** aus. Wählen Sie im Dialogfeld **E-Mail-Eigenschaften** die Option **Internetformat**.

  - **Outlook 2007**   Öffnen Sie die Kontaktkarte, doppelklicken Sie auf das Feld **E-Mail**, und wählen Sie **Internetformat** aus.

Zurück zum Seitenanfang

## Priorität von TNEF-Konvertierungsoptionen

Exchange geht in der in der folgenden Liste beschriebenen Reihenfolge vor, um die TNEF-Konvertierungsoptionen für ausgehende Nachrichten festzulegen, die an Empfänger außerhalb der Exchange-Organisation gesendet werden:

1.  Remotedomäneneinstellungen

2.  E-Mail-Benutzer- oder E-Mail-Kontakteinstellungen

3.  Outlook-Einstellungen

In dieser Liste ist die Reihenfolge absteigend aufgeführt. Die TNEF-Einstellung in der Remotedomäne überschreibt die TNEF-Einstellungen für den Mailbenutzer oder Mailkontakt in Outlook. Wenn Sie z. B. in Outlook eine Rich-Text-Nachricht senden, aber der Empfänger sich in einer Domäne befindet, deren Remotedomäneneinstellung TNEF-formatiere Nachrichten nicht erlaubt, enthält der Empfänger die Nachricht als unformatierten Text oder im HTML-Format, aber nicht in TNEF.

Außerdem sendet Exchange keine STNEF-Nachrichten (Summary Transport Neutral Encoding Format) an externe Empfänger. Nur TNEF-Nachrichten können an Empfänger außerhalb der Exchange-Organisation gesendet werden.

Zurück zum Seitenanfang

