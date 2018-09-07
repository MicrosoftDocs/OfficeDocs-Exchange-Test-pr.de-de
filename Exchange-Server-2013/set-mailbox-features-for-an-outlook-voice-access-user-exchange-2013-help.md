---
title: 'Festl. v. Postfachfeatures für Outlook Voice Access-Ben.: Exchange 2013-Hilfe'
TOCTitle: Festlegen von Postfachfeatures für einen Benutzer Outlook Voice Access
ms:assetid: a56bfd75-7bc5-49b9-b098-06855a720dcd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124030(v=EXCHG.150)
ms:contentKeyID: 50554871
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen von Postfachfeatures für einen Benutzer Outlook Voice Access

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

TUI-Einstellungen (Telephone User Interface, Telefonbenutzerschnittstelle) werden verwendet, wenn ein Benutzer unter Verwendung von Outlook Voice Access auf das Unified Messaging-System zugreift. Wenn Sie TUI-Konfigurationseinstellungen eines UM-aktivierten Benutzers ändern, ändern Sie Eigenschaften des Postfachs des UM-aktivierten Benutzers zusammen mit deren Werten.

Sie können die folgenden TUI-Einstellungen für einen UM-aktivierten Benutzer ändern:

  - Zulassen des Teilnehmerzugriffs

  - Zulassen des TUI-Zugriffs auf den Kalender

  - Zulassen des TUI-Zugriffs auf E-Mail

  - Zulassen von automatischer Spracherkennung

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Benutzer finden Sie unter [Festlegen von Postfachfeatures für einen Benutzer Outlook Voice Access](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/set-mailbox-features-for-a-user).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der vorhandene Exchange-Empfänger für Unified Messaging und Voicemail aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Ändern der TUI-Einstellungen eines einzelnen UM-aktivierten Benutzers mithilfe der Shell

In diesem Beispiel werden unter Verwendung der TUI-Einstellungen der Kalender- und E-Mail-Zugriff für den UM-aktivierten Benutzer Tony Smith aktiviert.

    Set-UMMailbox -Identity tony@contoso.com TUIAccessToCal True -TUIAccessToEmail True -OperatorNumber 111111 -DisableMissedCallNotification False -AnonCallBlock True


> [!NOTE]
> TUI-Einstellungen für Benutzer sind auch für UM-Postfachrichtlinien verfügbar. Das Ändern der TUI-Einstellungen einer UM-Postfachrichtlinie wirkt sich auf alle Benutzer aus, denen die UM-Postfachrichtlinie zugeordnet ist. Weitere Informationen zum Ändern von TUI-Einstellungen für eine UM-Postfachrichtlinie finden Sie unter <A href="set-mailbox-features-for-outlook-voice-access-users-exchange-2013-help.md">Festlegen von Postfachfunktionen für Outlook Voice Access-Benutzer</A>.


