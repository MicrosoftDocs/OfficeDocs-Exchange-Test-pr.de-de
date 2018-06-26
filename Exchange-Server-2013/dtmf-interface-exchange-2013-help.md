---
title: 'DTMF-Schnittstelle: Exchange 2013 Help'
TOCTitle: DTMF-Schnittstelle
ms:assetid: 2c7c9d8a-ed12-4dcf-a5b7-3cea0e785e49
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996919(v=EXCHG.150)
ms:contentKeyID: 54651499
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DTMF-Schnittstelle

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Unified Messaging (UM) können Anrufer DTMF (Dual Tone Multi-Frequency), auch als Tonwahl bezeichnet, und Spracheingaben für die Interaktion mit dem System verwenden. Welches Verfahren Benutzer verwenden können, hängt davon ab, wie der UM-Wählplan und automatischen Telefonzentralen konfiguriert sind.

Die DTMF-Schnittstelle ermöglicht Anrufern, die Telefontastatur für die Suche nach Benutzern und für die Navigation im UM-Voicemail-Menüsystem zu verwenden, wenn sie eine Outlook Voice Access-Nummer anrufen, die für einen Wählplan konfiguriert ist, oder wenn sie eine Telefonnummer anrufen, die für eine automatische Telefonzentrale konfiguriert ist. In diesem Thema wird die DTMF-Schnittstelle und ihre Verwendung durch Anrufer bei der Suche nach Benutzern und der Navigation im  UM-Voicemail-Menüsystem behandelt.

**Inhalt**

DTMF (Übersicht)

UM-Wählpläne und "Wahl nach Namen"

DTMF-Zuordnungen

DTMF-Zuordnungen für Benutzer, die nicht für Unified Messaging aktiviert sind

DTMF-Zuordnungen für Benutzer, die für Unified Messaging aktiviert sind

Weitere Informationen

## DTMF (Übersicht)

Für DTMF ist es erforderlich, dass ein Anrufer eine Taste auf der Tastatur des Telefons drückt, die einer Unified Messaging-Menüoption entspricht, oder den Namen eines Benutzers mithilfe der Buchstaben auf den Tasten eingibt, indem er den Namen oder den E-Mail-Alias des Benutzers buchstabiert. Anrufer verwenden ggf. DTMF, weil die automatische Spracherkennung (Automatic Speech Recognition, ASR) nicht aktiviert wurde bzw. das Verwenden von Sprachbefehlen zu einem Fehler geführt hat. In beiden Fällen werden DTMF-Eingaben für die Navigation in Menüs und die Suche nach Benutzern verwendet.

In UM werden DTMF-Eingaben standardmäßig für Wählpläne verwendet und stellen die Anruferstandardschnittstelle für automatische UM-Telefonzentralen dar.

Anrufer können DTMF-Eingaben für Folgendes verwenden:

  - Wählplan-Teilnehmerzugriff mithilfe von Outlook Voice Access.

  - Wähleinstellungen-Verzeichnissuchvorgänge und Suchvorgänge nach Benutzern.

  - Automatische Telefonzentralen, die nicht sprachaktiviert sind.

  - Automatische Telefonzentralen, die sprachaktiviert sind und für die ggf. eine automatische DTMF-Fallback-Telefonzentrale konfiguriert ist.

  - Automatische DTMF-Fallback-Telefonzentralen (nicht sprachaktiviert).

## UM-Wählpläne und "Wahl nach Namen"

Wenn Sie einen Satz UM-Wähleinstellungen erstellen, können Sie die primäre und die sekundäre Eingabemethode konfigurieren, die Anrufer zum Nachschlagen von Namen verwenden, wenn sie nach einem Benutzer suchen oder mit diesem Kontakt aufnehmen möchten. Diese Einstellungen werden auf der Seite **Einstellungen** des Wählplans vorgenommen und als **Primäre Methode für Namenssuche** und **Sekundäre Methode für Namenssuche** bezeichnet. Nachstehende Optionen sind für die primäre und die sekundäre Methode für Namenssuche verfügbar:

  - Nachname Vorname

  - Vorname Nachname

  - SMTP-Adresse

Zusätzlich steht **Keine** als Option für die sekundäre Methode für Namenssuche zur Verfügung.

Standardmäßig ist **Nachname Vorname** als primäre Methode für Namenssuche ausgewählt, und **SMTP-Adresse** ist als sekundäre Methode für Namenssuche angegeben. Wenn sich ein Anrufer daher in die Teilnehmerzugriffsnummer einwählt, die für den UM-Wählplan konfiguriert ist, wird die Begrüßungsnachricht des Wählplans wiedergegeben, und die Vermittlungsstelle sagt z. B.: "Willkommen bei Contoso Outlook Voice Access. Wenn Sie auf Ihr Postfach zugreifen möchten, geben Sie Ihre Durchwahl ein. Um jemanden zu kontaktieren, drücken Sie die Rautetaste." Nachdem der Anrufer die Rautetaste gedrückt hat, antwortet das System mit "Buchstabieren Sie den Namen der Person, die Sie anrufen möchten. Geben Sie zuerst den Nachnamen an. Oder buchstabieren Sie den E-Mail-Alias. Drücken Sie dann zweimal die Rautetaste". In diesem Szenario fordert das System den Anrufer abhängig von der Konfiguration der Wähleinstellungen anschließend auf, zuerst den Nachnamen und dann den Vornamen des Benutzers (Nachname Vorname) einzugeben oder den E-Mail-Alias ohne den Domänennamen zu buchstabieren. Wenn der E-Mail-Alias des Benutzers z. B. "tscholl@contoso.com" lautet, gibt der Anrufer "tscholl" ein.

Wenn Sie diese Konfiguration ändern möchten, weil die Standardeinstellung nicht Ihren Anforderungen entspricht, können Sie Benutzern auch ermöglichen, zuerst den E-Mail-Alias des Benutzers oder den Vornamen, gefolgt vom Nachnamen, einzugeben. In diesem Fall konfigurieren Sie die Option **Primäre Methode für Namenssuche** mit der Einstellung **SMTP-Adresse** und die Option **Sekundäre Methode für Namenssuche** mit der Einstellung **Vorname Nachname**. Die Einstellungen für die Wahlmethoden nach Namen gelten auch für alle automatischen UM-Telefonzentralen, die den Wähleinstellungen zugeordnet sind. Damit Anrufer den Namen des Benutzers mithilfe von DTMF-Eingaben oder der Tasten auf der Telefontastatur eingeben können, müssen eine DTMF-Zuordnung und Werte für den Benutzer im Verzeichnis Ihrer Organisation vorhanden sein.

Weitere Informationen zum Ändern der primären und sekundären Wahlmethoden nach Namen für einen Satz UM-Wähleinstellungen finden Sie unter [Konfigurieren Sie die primäre Methode für Outlook Voice Access-Benutzer suchen](configure-the-primary-way-for-outlook-voice-access-users-to-search-exchange-2013-help.md) und [Konfigurieren Sie die sekundäre Methode für Outlook Voice Access-Benutzer suchen](configure-the-secondary-way-for-outlook-voice-access-users-to-search-exchange-2013-help.md).

DTMF (Übersicht)

## DTMF-Zuordnungen

In einer Exchange-Organisation wird ein Attribut namens **msExchUMDtmfMap** jedem Benutzer zugeordnet, der im Verzeichnis erstellt wird. Unified Messaging verwendet dieses Attribut für die Zuordnung des Vornamens, Nachnamens und des E-Mail-Alias zu einem Nummernsatz. Diese Zuordnung wird als DTMF-Zuordnung bezeichnet. Eine DTMF-Zuordnung ermöglicht Anrufern die Eingabe von Zahlen auf der Telefontastatur, die den Buchstaben des Namens oder des E-Mail-Alias des Benutzers entsprechen. Dieses Attribut enthält die Werte, die zum Erstellen einer DTMF-Zuordnung für den Vornamen des Benutzers, gefolgt vom Nachnamen, für den Nachnamen des Benutzers, gefolgt vom Vornamen, und für den E-Mail-Alias des Benutzers benötigt werden.

Die folgende Tabelle zeigt die DTMF-Zuordnungswerte, die in Active Directory für das Attribut **msExchUMDtmfMap** für einen UM-aktivierten Benutzer namens "Thorsten Scholl" mit dem Alias "tscholl@contoso.com" gespeichert werden.

**Für einen UM-aktivierten Benutzer namens "Thorsten Scholl" gespeicherte DTMF-Werte**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verzeichniseingabe</th>
<th>Name des Benutzers</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>firstNameLastName:866976484</p></li>
</ul></td>
<td><p>thorstenscholl</p></td>
</tr>
<tr class="even">
<td><ul>
<li><p>lastNameFirstName:764848669</p></li>
</ul></td>
<td><p>schollthorsten</p></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>emailAddress:876484</p></li>
</ul></td>
<td><p>tscholl</p></td>
</tr>
</tbody>
</table>


Namen und E-Mail-Aliase dürfen auch andere, nicht alphanumerische Zeichen enthalten (z. B. Kommas, Bindestriche, Unterstriche oder Punkte). Solche Zeichen werden jedoch nicht in einer DTMF-Zuordnung für einen Benutzer verwendet. Wenn der E-Mail-Alias für Thorsten Scholl z. B. "thorsten-scholl@contoso.com" lautet, ist der Wert der DTMF-Zuordnung 866976484. Der Bindestrich wird nicht berücksichtigt. Wenn der E-Mail-Alias eines Benutzers jedoch mindestens eine Ziffer enthält, z. B. "thorstenscholl123@contoso.com", werden die Ziffern in der DTMF-Zuordnung verwendet, die erstellt wird. Die DTMF-Zuordnung für "thorstenscholl123" lautet 866976484123.

Für einen Benutzer muss eine DTMF-Zuordnung vorhanden sein, damit Anrufer den Namen oder E-Mail-Alias des Benutzers eingeben können. Es ist jedoch nicht für alle Benutzer eine DTMF-Zuordnung mit ihrem Benutzerkonto verknüpft.

DTMF (Übersicht)

## DTMF-Zuordnungen für Benutzer, die nicht für Unified Messaging aktiviert sind

Benutzer sind nicht standardmäßig für Unified Messaging aktiviert. Dies gilt auch für postfachaktivierte Benutzer. Für das Attribut **msExchUMDtmfMap** werden die für DTMF-Zuordnungen erforderliche Werte für Benutzer eingegeben, die nicht für UM aktiviert wurden. Standardmäßig werden die folgenden DTMF-Zuordnungen für alle Benutzer erstellt, wenn für diese ein Postfach erstellt wird.

1.  emailAddress

2.  firstNameLastName

3.  lastNameFirstName

Hat ein Benutzer keine DTMF-Zuordnungswerte für sein Konto definiert, können Anrufer den Benutzer nicht kontaktieren, indem sie eine Telefontaste aus einem automatischen UM-Telefonzentralenmenü drücken oder eine Verzeichnissuche durchführen. Außerdem sind UM-aktivierte Benutzer nicht in der Lage, Nachrichten an Benutzer zu senden oder Anrufe an Benutzer umzuleiten, die keine DTMF-Zuordnung besitzen – es sei denn, sie können die automatische Spracherkennung verwenden. Damit Anrufer mithilfe der Telefontastatur Anrufe umleiten oder Kontakt zu nicht UM-aktivierten Benutzern aufnehmen können, müssen Sie die erforderlichen Werte für die DTMF-Zuordnung für Benutzer erstellen. Sie können das Cmdlet **Set-User** mit dem Parameter *-CreateDtmfMap* verwenden, um die DTMF-Zuordnung für einen einzelnen Benutzer zu erstellen oder zu aktualisieren oder eine DTMF-Zuordnung für einen Benutzer zu aktualisieren, wenn der Name des Benutzers geändert wurde, nachdem eine DTMF-Zuordnung erstellt wurde. Optional können Sie ein Exchange-Verwaltungsshellskript mithilfe dieses Cmdlets erstellen, um die Werte der DTMF-Zuordnung für mehrere Benutzer zu aktualisieren.

Weitere Informationen zum Cmdlet **Set-User** finden Sie unter [Set-User](https://technet.microsoft.com/de-de/library/aa998221\(v=exchg.150\)).

DTMF (Übersicht)

## DTMF-Zuordnungen für Benutzer, die für Unified Messaging aktiviert sind

Standardmäßig wird eine DTMF-Zuordnung für Benutzer erstellt, wenn diese für Unified Messaging aktiviert werden. Dadurch können Anrufe von externen Anrufern UM-aktivierten Benutzern, nicht UM-aktivierten Benutzern und von anderen UM-aktivierten Benutzern weitergeleitet werden, die die Telefontastatur zum Buchstabieren des Namens oder E-Mail-Alias des Benutzers verwenden.

Nachdem die DTMF-Zuordnungswerte für einen UM-aktivierten Benutzer erstellt wurden, können Anrufer die Verzeichnissuche verwenden. Anrufer nutzen die Verzeichnissuche, wenn sie in den folgenden Situationen die Telefontastatur verwenden:

  - So identifizieren oder suchen Sie einen Benutzers, wenn sie eine Outlook Voice Access-Nummer anrufen.

  - Suchen nach einem UM-aktivierten Benutzer oder Übergeben von Anrufen an diesen, wenn sie eine automatische UM-Telefonzentrale anrufen.

Weitere Informationen zum Aktivieren eines Benutzers für Unified Messaging finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

Manchmal ändert sich der Vorname, der Nachname oder das E-Mail-Alias eines Benutzers, nachdem er für UM aktiviert wurde. Die Werte der DTMF-Zuordnung werden nicht automatisch aktualisiert. Wenn ein Anrufer den neuen Namen oder das neue E-Mail-Alias eingibt und die DTMF-Zuordnung des Benutzers noch nicht mit der Änderung des Namens oder E-Mail-Alias aktualisiert wurde, kann der Anrufer den Benutzer nicht im Verzeichnis finden, keine Nachricht an ihn senden und keine Anrufe an den Benutzer übergeben. Wenn Sie die DTMF-Zuordnung eines Benutzers aktualisieren müssen, nachdem er für UM aktiviert wurde, können Sie das Cmdlet **Set-User** mit dem Parameter *-CreateDtmfMap* verwenden. Sie können auch ein Exchange-Verwaltungsshellskript mithilfe dieses Cmdlets erstellen, wenn Sie die Werte der DTMF-Zuordnungen für mehrere UM-aktivierte Benutzer aktualisieren möchten.


> [!WARNING]
> Es wird davon abgeraten, die DTMF-Werte für Benutzer manuell mithilfe eines Tools wie ADSI-Editor zu ändern, da diese Vorgehensweise zu inkonsistenten Konfigurationen oder anderen Fehlern führen kann. Zum Erstellen oder Aktualisieren von DTMF-Zuordnungen für Benutzer wird ausschließlich die Verwendung das Cmdlet <STRONG>Set-UMService</STRONG> oder das Cmdlet <STRONG>Set-User</STRONG> empfohlen.



## Weitere Informationen

[ADSI-Bearbeitung - Übersicht](https://go.microsoft.com/fwlink/p/?linkid=73175)

