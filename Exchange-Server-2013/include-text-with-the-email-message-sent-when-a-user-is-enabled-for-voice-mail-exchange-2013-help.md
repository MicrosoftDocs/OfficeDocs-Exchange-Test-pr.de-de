---
title: 'Hinzuf. v. Text d. gesend. E-Mail, wenn für Benutzer Voicemail aktiviert ist'
TOCTitle: Einschließen von Text mit der e-Mail-Nachricht gesendet, wenn ein Benutzer für Voicemail aktiviert ist
ms:assetid: 3e8292fb-0cdb-445d-8048-a59af7c38d63
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201679(v=EXCHG.150)
ms:contentKeyID: 51409290
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Einschließen von Text mit der e-Mail-Nachricht gesendet, wenn ein Benutzer für Voicemail aktiviert ist

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-16_

Wenn das Postfach eines Benutzers für UM-Voicemail (Unified Messaging) aktiviert wird, wird eine E-Mail-Nachricht gesendet, die den Benutzer bei Unified Messaging begrüßt. Diese Nachricht enthält die PIN-Informationen, die der Benutzer für den ersten Zugriff auf das Voicemailsystem verwendet.

Sie können den Text anpassen, der in der Begrüßungs-E-Mail gesendet wird, indem Sie Text im Textfeld **Wenn ein Benutzer für Unified Messaging aktiviert ist** für eine UM-Postfachrichtlinie eingeben. Sie können Informationen wie z. B. die Rufnummern des technischen Supports für Unified Messaging oder zusätzliche Outlook Voice Access-Nummern einschließen. Nachdem Sie den Text hinzugefügt haben, wird er in jede E-Mail-Nachricht eingefügt, die gesendet wird, wenn der UM-Postfachrichtlinie zugeordnete Benutzer für Unified Messaging aktiviert werden.


> [!NOTE]
> Der benutzerdefinierte Text, den Sie der Begrüßungsnachricht hinzufügen, ist auf 512&nbsp;Zeichen beschränkt und kann einfachen HTML-Text umfassen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anpassen des beim Aktivieren eines Postfach für Unified Messaging gesendeten Texts mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Nachrichtentext** im Textfeld für **Wenn ein Benutzer für Unified Messaging aktiviert ist** den Text ein, der in der E-Mail-Nachricht enthalten sein soll, die beim Aktivieren von Benutzern für Unified Messaging gesendet wird.

4.  Klicken Sie auf **Speichern**.

## Anpassen des beim Aktivieren eines Postfach für Unified Messaging gesendeten Texts mithilfe der Shell

In diesem Beispiel erhalten UM-aktivierte, mit einer UM-Postfachrichtlinie verknüpfte Benutzer die Möglichkeit, weitere Anleitungen zu Unified Messaging und der Rufnummer von Outlook Voice Access, mit der sie per Telefon auf ihre Postfächer zugreifen können, abzurufen.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -UMEnabledText "You've been enabled for Unified Messaging voice mail. To access your Exchange mailbox, call your internal telephone extension number. From outside your office, call 425-555-1234."

