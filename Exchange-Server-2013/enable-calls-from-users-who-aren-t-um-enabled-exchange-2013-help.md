---
title: 'Aktivieren v. Anrufen von Nicht-UM-aktivierten Benutzern: Exchange 2013-Hilfe'
TOCTitle: Aktivieren Sie Anrufe von Benutzern, die UM-aktivierten sind nicht
ms:assetid: 3c39c6df-6d7a-469f-b92b-85b3f14bad31
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb267006(v=EXCHG.150)
ms:contentKeyID: 50475366
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren Sie Anrufe von Benutzern, die UM-aktivierten sind nicht

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Sie können Anrufe von Benutzern aktivieren bzw. deaktivieren, die nicht für Unified Messaging (UM) aktiviert sind. Standardmäßig erlaubt Unified Messaging eingehende Anrufe von nicht authentifizierten Anrufern über eine automatische Telefonzentrale für UM-aktivierte Benutzer. Wenn diese Option aktiviert ist, können Benutzer außerhalb einer Organisation Anrufe an UM-aktivierte Benutzer weiterleiten.

Wenn diese Einstellung für einen UM-aktivierten Benutzer deaktiviert wurde, kann das Postfach des Benutzers mithilfe einer Verzeichnissuche dennoch ermittelt werden. Wenn ein externer Anrufer jedoch eine Weiterleitung an den Benutzer versucht, gibt das System die automatische Benachrichtigung aus, dass der Anruf nicht an diesen Benutzer weitergeleitet werden kann. Der Anrufer wird dann an die Vermittlungsstelle weitergeleitet, wenn eine solche für die automatische Telefonzentrale konfiguriert ist. Wenn keine Vermittlungsstelle für die automatische Telefonzentrale konfiguriert wurde, wird der Anruf an eine Vermittlungsstelle der Wähleinstellungen umgeleitet, wenn eine solche konfiguriert wurde. Wenn keine Vermittlungsstellendurchwahl für die sprachaktivierte automatische Telefonzentrale, die automatische DTMF-Fallback-Telefonzentrale oder die Wähleinstellungen konfiguriert wurde, gibt das System die automatische Benachrichtigung aus, dass weder die Vermittlungsstelle noch der Tonwahldienst verfügbar sind.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/voice-mail-enabled-user-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Aktivieren des Empfangs von Anrufen von nicht UM-aktivierten Benutzern mithilfe der Shell

In diesem Beispiel wird Tony Smith gestattet, Anrufe von nicht UM-aktivierten Benutzern zu empfangen.

    Set UMMailbox -Identity tony@contoso.com -AllowUMCallsFromNonUsers SearchEnabled

