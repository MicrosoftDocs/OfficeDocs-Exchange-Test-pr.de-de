---
title: 'Einrichten von Outlook Voice Access: Exchange 2013 Help'
TOCTitle: Einrichten von Outlook Voice Access
ms:assetid: 5ce8c877-35f3-4e55-a65e-5ca469aeae99
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298010(v=EXCHG.150)
ms:contentKeyID: 50554835
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichten von Outlook Voice Access

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Microsoft Outlook Voice Access ermöglicht Exchange Unified Messaging-aktivierten Benutzern den Zugriff auf ihr Postfach über analoge, digitale oder mobile Telefone.

Ein Outlook Voice Access-Benutzer (auch *Teilnehmer* genannt), ist ein Benutzer in einer Organisation, der für Unified Messaging aktiviert ist. Teilnehmer verwenden Outlook Voice Access, um per Telefon auf ihre Postfächer zuzugreifen und E-Mails, Voicemailnachrichten sowie Informationen zu persönlichen Kontakten und Kalenderdaten abzurufen.

**Inhalt**

Outlook Voice Access – Übersicht

Benutzerschnittstellen zu Outlook Voice Access

Outlook Voice Access-Szenarien

Verteilergruppen und Kontaktgruppen

Auswählen einer Sprache

Steuern von Outlook Voice Access-Features

## Outlook Voice Access – Übersicht

In Microsoft Exchange Unified Messaging kann ein UM-aktivierter Benutzer zum Zugriff auf sein Postfach eine interne oder externe Telefonnummer anrufen (die im UM-Wählplan konfiguriert ist) und das Outlook Voice Access-Menüsystem verwenden. Mithilfe des Menüs können UM-aktivierte Benutzer E-Mails lesen, Sprachnachrichten abhören, mit ihrem Outlook-Kalender arbeiten, auf ihre persönlichen Kontakte zugreifen und Aufgaben ausführen, beispielsweise das Konfigurieren ihrer Outlook Voice Access-PIN und das Aufzeichnen von Voicemails.

Zwei Benutzertypen (authentifiziert und nicht authentifiziert) können sich eine Outlook Voice Access-Nummer anrufen. Wenn ein nicht authentifizierter Benutzer eine Outlook Voice Access-Nummer anruft, die in einem UM-Wählplan festgelegt ist, kann er nur Verzeichnissuchen für Benutzer vornehmen. Authentifizierte Benutzer (jene, die ihre PIN eingeben) können Verzeichnissuchen vornehmen und sich an ihrem Postfach anmelden, um sich E-Mails, Kalenderelemente und Voicemail anzuhören und um persönliche Kontakte zu suchen. Wenn sie nach einem Benutzer im Verzeichnis oder nach persönlichen Kontakten suchen, können sie, nachdem der Benutzer gefunden wurde, Anrufe an den Benutzer weiterleiten oder die Benutzerdurchwahl anrufen.

## Benutzerschnittstellen zu Outlook Voice Access

Outlook Voice Access-Benutzern stehen zwei Unified Messaging-Benutzerschnittstellen zur Verfügung: die Benutzerschnittstelle für Telefoneingabe (Telephone User Interface, TUI) und die Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI), die die automatische Spracherkennung (Automatic Speech Recognition, ASR) verwendet.

Damit ein Benutzer die Benutzerschnittstelle für Spracheingabe in Outlook Voice Access verwenden kann, muss diese im UM-Wählplan und auch in der UM-Postfachrichtlinie für den Benutzer aktiviert werden. Wenn Sie einen Wählplan und eine UM-Postfachrichtlinie erstellen und die Voicemailfunktion für einen Benutzer aktivieren, kann der Benutzer standardmäßig die automatische Spracherkennung oder die Benutzerschnittstelle für Spracheingabe in Outlook Voice Access verwenden, um durch Menüs, Nachrichten und andere Optionen zu navigieren. Allerdings muss der Benutzer – selbst wenn er die Benutzerschnittstelle verwenden kann – zur Eingabe der PIN, zum Navigieren durch die persönlichen Optionen und zum Ausführen einer Verzeichnissuche die Telefontastatur verwenden. Die Standardeinstellungen sind in der folgenden Tabelle aufgeführt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UM-Komponente</th>
<th>Standardeinstellung</th>
<th>Exchange-Verwaltungsshell zum Aktivieren des VUI-Zugriffs – Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UM-Wähleinstellungen</p></td>
<td><p>Aktiviert</p></td>
<td><p><code>Set-UMDialPlan -id MyUMDialPlan -AutomaticSpeechRecognitionEnabled  $true</code></p></td>
</tr>
<tr class="even">
<td><p>UM-Postfachrichtlinie</p></td>
<td><p>Aktiviert</p></td>
<td><p><code>Set-UMMaiboxPolicy -id MyUMPolicy -AllowAutomaticSpeechRecognition  $true</code></p></td>
</tr>
<tr class="odd">
<td><p>Postfach des Benutzers</p></td>
<td><p>Aktiviert</p></td>
<td><p><code>Set-UMMailbox -id tonysmith -AutomaticSpeechRecognitionEnabled $true</code></p></td>
</tr>
</tbody>
</table>


Der folgende Abschnitt umfasst Szenarien, die die VUI-Funktionalität beschreiben.

Outlook Voice Access – Übersicht

## Outlook Voice Access-Szenarien

Beispiele zur Verwendung von Outlook Voice Access über ein Telefon:

  - **E-Mail-Zugriff**   Ein Outlook Voice Access-Benutzer wählt auf einem Telefon eine Outlook Voice Access-Nummer, um auf seine E-Mails zuzugreifen. Die Sprachansage lautet: "Willkommen. Sie sind mit MicrosoftExchange verbunden. Wenn Sie auf Ihr Postfach zugreifen möchten, geben Sie Ihre Durchwahlnummer ein. Um jemanden zu kontaktieren, drücken Sie die Rautetaste." Nachdem der Benutzer seine Postfachdurchwahlnummer eingegeben hat, lautet die Ansage: "Geben Sie Ihre PIN ein, und drücken Sie dann die Rautetaste." Nachdem der Benutzer eine PIN eingegeben hat, lautet die Ansage: "Es sind zwei neue Voicemails und 10 neue E-Mails vorhanden, und Ihre nächste Besprechung beginnt um 10:00 Uhr. Sagen Sie "Voicemail", "E-Mail", "Kalender', "Persönliche Kontakte", "Verzeichnis" oder "Persönliche Optionen"." Wenn der Benutzer "E-Mail" sagt, gibt das Voicemailsystem den Nachrichtenkopf und anschließend den Namen, den Betreff, die Zeit und die Priorität der Nachrichten im Postfach des Benutzers wieder.

  - **Kalenderzugriff**   Ein Outlook Voice Access-Benutzer wählt auf einem Telefon eine Outlook Voice Access-Nummer, um auf seinen Kalender zuzugreifen. Die Sprachansage lautet: "Willkommen. Sie sind mit MicrosoftExchange verbunden. Wenn Sie auf Ihr Postfach zugreifen möchten, geben Sie Ihre Durchwahl ein. Um jemanden zu kontaktieren, drücken Sie die Rautetaste." Nachdem der Benutzer seine Postfachdurchwahlnummer eingegeben hat, lautet die Ansage: "Geben Sie Ihre PIN ein, und drücken Sie dann die Rautetaste." Nachdem der Benutzer eine PIN eingegeben hat, lautet die Ansage: "Es sind zwei neue Voicemails und 10 neue E-Mails vorhanden, und Ihre nächste Besprechung beginnt um 10:00 Uhr. Sagen Sie "Voicemail", "E-Mail", "Kalender', "Persönliche Kontakte", "Verzeichnis" oder "Persönliche Optionen"." Wenn der Benutzer "Kalender" sagt, antwortet das Voicemailsystem "Gern, und welchen Tag soll ich öffnen?" Der Benutzer sagt: "Kalender für heute." Das Voicemailsystem antwortet mit dem Satz "Öffne Kalender für heute." Das Voicemailsystem liest dem Benutzer jeden Kalendertermin für den betreffenden Tag vor.
    

    > [!NOTE]
    > Wenn ein Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst ein beschädigtes Kalenderelement in einem Benutzerpostfach vorfindet, kann das Element nicht vorgelesen werden. Stattdessen wird der Anrufer wieder ins Outlook Voice Access-Hauptmenü geleitet, und das Vorlesen aller weiteren Termine, die möglicherweise für den Rest des Tages geplant sind, wird ausgelassen.



  - **Voicemailzugriff**   Ein Outlook Voice Access-Benutzer wählt auf einem Telefon eine Outlook Voice Access-Nummer, um auf seine Voicemail zuzugreifen. Die Sprachansage lautet: "Willkommen. Sie sind mit MicrosoftExchange verbunden. Wenn Sie auf Ihr Postfach zugreifen möchten, geben Sie Ihre Durchwahl ein. Um jemanden zu kontaktieren, drücken Sie die Rautetaste." Nachdem der Benutzer seine Postfachdurchwahlnummer eingegeben hat, lautet die Ansage: "Geben Sie Ihre PIN ein, und drücken Sie dann die Rautetaste." Nachdem der Benutzer eine PIN eingegeben hat, lautet die Ansage: "Es sind zwei neue Voicemails und 10 neue E-Mails vorhanden, und Ihre nächste Besprechung beginnt um 10:00 Uhr. Sagen Sie "Voicemail", "E-Mail", "Kalender', "Persönliche Kontakte", "Verzeichnis" oder "Persönliche Optionen"." Der Benutzer sagt "Voicemail", und das Voicemailsystem gibt den Nachrichtenkopf und anschließend den Namen, den Betreff, die Zeit und die Priorität der Sprachnachrichten im Postfach des Teilnehmers wieder.
    

    > [!NOTE]
    > Wenn die Spracherkennung aktiviert ist, können Benutzer mithilfe von Spracheingaben auf ihr UM-aktiviertes Postfach zugreifen. Die Teilnehmer können auch Tonwahl- bzw. DTMF-Eingaben (Dual Tone Multi-Frequency) verwenden, indem sie „0“ drücken. Die Spracherkennung ist für PIN-Eingaben nicht aktiviert.



  - **Ermitteln eines Benutzers im Verzeichnis**   Ein Outlook Voice Access-Benutzer ruft von einem Telefon eine Outlook Voice Access-Nummer an und möchte eine Person im Verzeichnis suchen, indem er ihren E-Mail-Alias buchstabiert. Die Sprachansage lautet: "Willkommen. Sie sind mit MicrosoftExchange verbunden. Um jemanden zu kontaktieren, drücken Sie die Rautetaste." Der Benutzer drückt die Rautetaste und buchstabiert dann mithilfe von Tonwahleingaben die SMTP-Adresse der Person.
    

    > [!NOTE]
    > Die Verzeichnissuchfunktion mit einer Outlook Voice Access-Nummer ist nicht sprachaktiviert. Benutzer können den Namen der Person, mit der sie Kontakt aufnehmen möchten, nur mithilfe von Tonwahleingaben buchstabieren.

    

    > [!IMPORTANT]
    > In einigen Unternehmen (insbesondere in Ostasien) weisen die Tasten von Bürotelefonen möglicherweise keine Buchstaben auf. Diese Tatsache macht eine Verwendung der Funktion zum Buchstabieren des Namens über die Tonwahlschnittstelle nahezu unmöglich, wenn die Tastenzuordnungen nicht bekannt sind. Standardmäßig verwendet Unified Messaging die E.161-Tastenzuordnung. d. h. 2=ABC, 3=DEF, 4=GHI, 5=JKL, 6=MNO, 7=PQRS, 8=TUV, 9=WXYZ.

    
    Beim Eingeben einer Kombination aus Buchstaben und Zahlen, z. B. "Mike1092", werden die numerischen Ziffern sich selbst zugeordnet. Damit ein E-Mail-Alias wie z. B. "Mike1092" richtig eingegeben wird, muss der Benutzer die Zifferntasten "64531092" drücken. Für andere Zeichen als A bis Z und 0 bis 9 gibt es kein Telefontastenäquivalent. Diese Zeichen sollten daher nicht eingegeben werden. Der E-Mail-Alias "jim.wilson" wird z. B. als "546945766" eingegeben. Obwohl 10 Zeichen einzugeben sind, werden vom Benutzer nur 9 Ziffern eingegeben, weil für den Punkt (.) keine Ziffernentsprechung vorhanden ist.

Outlook Voice Access – Übersicht

## Verteilergruppen und Kontaktgruppen

Benutzer können Outlook Voice Access zum Senden oder Weiterleiten von Sprachnachrichten, E-Mails oder Besprechungsanfragen verwenden. Nachrichten oder Besprechungsanfragen können an folgende Empfänger gesendet oder weitergeleitet werden:

  - Eine Person im persönlichen Ordner "Kontakte"

  - Eine Person im freigegebenen Adressbuch der Organisation

  - Eine Kontaktgruppe, die im Ordner "Kontakte" erstellt wurde

  - Eine Verteilergruppe im freigegebenen Adressbuch der Organisation

Sie können über die Benutzerschnittstelle für die Spracheingabe (sofern die automatische Spracherkennung aktiviert wurde) oder mittels Tonwahleingaben auf der Telefontastatur Nachrichten und Besprechungsanfragen senden. Sie können mit Outlook Voice Access auch Details zu einer Gruppe abhören, einschließlich der Mitglieder der Gruppe.


> [!NOTE]
> Wenn Benutzer versuchen, eine Nachricht an eine Gruppe zu senden (entweder eine Verteilergruppe im freigegebenen Adressbuch oder eine Kontaktgruppe in ihrem persönlichen Ordner "Kontakte"), die keine Mitglieder enthält, bietet das Voicemailsystem keine Optionen zum Senden oder Weiterleiten der Nachricht bzw. Besprechungsanfrage. Wenn sie versuchen, eine Gruppe ohne Mitglieder als Empfänger einer Besprechungsanfrage oder einer über das Telefon erstellten Nachricht hinzuzufügen, wird die Gruppe nicht hinzugefügt, und stattdessen hören sie eine Ansage dazu, dass die Nachricht nicht gesendet werden konnte, da der Kontakt anscheinend nicht über eine gültige E-Mail-Adresse verfügt.



## Auswählen einer Sprache

Benutzer können die Sprache, die Outlook Voice Access für Ansagen verwendet und der die Benutzer antworten, nicht ändern. Das Voicemailsystem versucht, die beste Übereinstimmung für die Sprache zu ermitteln und zu verwenden, die die Benutzer bei der ersten Anmeldung bei MicrosoftOutlook Web App oder auf der Registerkarte "Regional" in Outlook Web App ausgewählt haben. Falls die ausgewählte Sprache nicht von Outlook Voice Access unterstützt wird, wird die Sprache verwendet, die Anrufer hören, wenn sie aufgefordert werden, eine Sprachnachricht zu hinterlassen.

Outlook Voice Access – Übersicht

## Steuern von Outlook Voice Access-Features

Wenn sich Benutzer in Outlook Voice Access eingewählt haben, können sie standardmäßig per Telefon auf ihre Kalender, E-Mails und persönlichen Kontakte zugreifen sowie das Verzeichnis durchsuchen. Sie können die Shell dazu verwenden, um Benutzer am Zugriff auf eine oder mehrere dieser Features zu hindern, wenn sie Outlook Voice Access nutzen, um auf ihre Postfächer zuzugreifen. Wenn Sie Outlook Voice Access-Funktionen in einer UM-Postfachrichtlinie ändern, wirken sich die Änderungen auf alle Benutzer aus, die der UM-Postfachrichtlinie zugeordnet sind. Sie können auch einige Features für das Postfach eines einzelnen Benutzers deaktivieren, manche Features können jedoch nur per UM-Postfachrichtlinie deaktiviert werden und stehen nicht in einem einzelnen Postfach zur Verfügung.


> [!NOTE]
> Sie können die Outlook Voice Access-TUI-Einstellungen für UM-aktivierte Benutzer in einer UM-Postfachrichtlinie oder die UM-Postfachrichtlinien nur mithilfe der Shell ändern.



**Einstellungen der UM-Postfachrichtlinie**   In einer UM-Postfachrichtlinie können Sie für Benutzer den Zugriff auf folgende Outlook Voice Access-Funktionen deaktivieren:

  - Automatische Spracherkennung (Automatic Speech Recognition, ASR)

  - Zugriff ohne PIN auf Voicemail

  - Sprachantworten auf andere Nachrichten

  - TUI-Zugriff auf eigenen Kalender

  - TUI-Zugriff auf Verzeichnis

  - TUI-Zugriff auf eigene E-Mails

  - TUI-Zugriff auf eigene persönliche Kontakte

**UM-aktivierte Postfacheinstellungen**   Sie können den Zugriff eines Benutzers auf die folgenden Outlook Voice Access-Features für das Postfach des Benutzers deaktivieren:

  - TUI-Zugriff auf den Kalender

  - TUI-Zugriff auf E-Mails

  - Automatische Spracherkennung (Automatic Speech Recognition, ASR)

Sie können bei bestimmten Benutzern den Empfang von Voicemails verhindern, ihnen aber dennoch die Möglichkeit einräumen, über Outlook Voice Access auf ihr Postfach zuzugreifen. Sie können einen Benutzer für Unified Messaging aktivieren und sein Postfach mit einer Durchwahlnummer konfigurieren, die aktuell von keinem anderen Benutzer in der Organisation verwendet wird.

Outlook Voice Access – Übersicht

