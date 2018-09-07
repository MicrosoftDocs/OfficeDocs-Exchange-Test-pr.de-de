---
title: 'Festlegen der max. Verzögerung für Voicemailvorschau-Partner'
TOCTitle: Legen Sie die maximale Verzögerung für einen Voicemailvorschau partner
ms:assetid: c9a07f6d-6f7f-4036-9a4a-d668d21e2c76
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630928(v=EXCHG.150)
ms:contentKeyID: 51409342
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die maximale Verzögerung für einen Voicemailvorschau partner

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-13_

Sie können die maximale Zustellungsverzögerung für einen Voicemailvorschau-Partner in einer Unified Messaging-Postfachrichtlinie (UM) festlegen. Nach dem Festlegen der maximalen Zustellungsverzögerung wird die Einstellung auf alle UM-aktivierten Benutzer angewendet, die dieser UM-Postfachrichtlinie zugeordnet sind.


> [!NOTE]
> Zum Festlegen der maximalen Zustellungsverzögerung für einen Voicemailvorschau-Partner muss die Shell verwendet werden.



Weitere Informationen zum Voicemailvorschau-Partnerprogramm finden Sie unter [Ratgeber für Voicemailvorschau](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/voice-mail-preview-advisor).

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Voicemailvorschau finden Sie unter [Voice Mail Preview Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/voice-mail-preview-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Festlegen der maximalen Zustellungsverzögerung für einen Voicemailvorschau-Partner mithilfe der Shell

In diesem Beispiel wird die maximale Zustellungsverzögerung in der UM-Postfachrichtlinie *MyUMMailboxPolicy* auf 600 Sekunden (10 Minuten) festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy - VoiceMailPreviewPartnerMaxDeliveryDelay 600

