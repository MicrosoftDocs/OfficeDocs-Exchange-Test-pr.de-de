---
title: 'Konfig. der Voicemailvorschau-Partnerdienste f. Benutzer: Exchange 2013-Hilfe'
TOCTitle: Voicemailvorschau Partnerdienste für Benutzer konfigurieren
ms:assetid: 7bb914ca-5502-4e64-bae5-555034138d8a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630920(v=EXCHG.150)
ms:contentKeyID: 51409315
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Voicemailvorschau Partnerdienste für Benutzer konfigurieren

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können einen Voicemailvorschau-Partner für eine Unified Messaging-Postfachrichtlinie (UM) konfigurieren. Nachdem Sie die Einstellungen für den Voicemailvorschau-Partner konfiguriert haben, z. B. die ID und Adresse des Voicemailvorschau-Partners, gelten die von Ihnen konfigurierten Einstellungen für eine UM-Postfachrichtlinie für alle UM-aktivierten Benutzer, die dieser Postfachrichtlinie zugeordnet sind.


> [!NOTE]
> Sie müssen die Shell zum Konfigurieren eines Voicemailvorschau-Partners verwenden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Anmelden bei einem Partnerdienst

Um die Liste der certified Partner und ausführliche Informationen zum Registrieren ermittelt wird, finden Sie unter [Ratgeber für Voicemailvorschau](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/voice-mail-preview-advisor) oder finden Sie auf der Website [Microsoft Hindernissen bei](https://go.microsoft.com/fwlink/p/?linkid=281966) . Nachdem Sie sich angemeldet haben, bietet der Partner Voicemailvorschau Sie eine Partner-ID und die SMTP-Adresse verwenden, um die Sprachnachrichten weiterzuleiten.

In Schritt 2 wenden Sie die in Schritt 1 erhaltene Partner-ID und SMTP-Adresse auf die erforderlichen UM-Postfachrichtlinien an.

## Schritt 2: Festlegen der Adresse und ID des Voicemailvorschau-Partners

In diesem Beispiel wird als Adresse des Voicemailvorschau-Partners "exumvmp@fabrikam.com" und als ID der Wert "CON123-2010" für die Postfachrichtlinie *MyUMMailboxPolicy* festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerAddress exumvmp@fabrikam.com
    -VoiceMailPreviewPartnerAssignedID CON123-2010

## Schritt 3: Konfigurieren der erweiterten Einstellungen für den Voicemailvorschau-Partner

Wenn der Partner benutzerdefinierte Einstellungen erfordert, können Sie wie folgt zwei zusätzliche Parameter für den Voicemailvorschau-Partner festlegen:

  - *VoiceMailPreviewPartnerMaxMessageDuration*

  - *VoiceMailPreviewPartnerMaxDeliveryDelay*

In diesem Beispiel wird die maximale Nachrichtendauer auf 300 Sekunden (5 Minuten) und die maximale Zustellungsverzögerung auf 600 Sekunden (10 Minuten) für die UM-Postfachrichtlinie *MyUMMailboxPolicy* festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerMaxMessageDuration 300 -VoiceMailPreviewPartnerMaxDeliveryDelay 600

## Schritt 4: Zuordnen eines UM-aktivierten Benutzers zur UM-Postfachrichtlinie für einen Voicemailvorschau-Partner

Wenn Sie den Voicemailvorschau-Partnerdienst für einige, jedoch nicht für alle UM-aktivierten Benutzer in den UM-Wähleinstellungen konfigurieren möchten, müssen Sie eine neue UM-Postfachrichtlinie erstellen und die Partnereinstellungen konfigurieren. Wenn Sie diesen Vorgang abgeschlossen haben, können Sie die neue Richtlinie auf die ausgewählten UM-aktivierten Benutzer anwenden. Weitere Informationen zum Zuordnen von UM-aktivierten Benutzern zu einer UM-Postfachrichtlinie finden Sie in den folgenden Themen:

  - [Zuweisen einer um-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/assign-um-mailbox-policy)

  - [Set-UMMailbox](https://technet.microsoft.com/de-de/library/bb124893\(v=exchg.150\))

Weitere Informationen zum Voicemailvorschau-Partnerprogramm finden Sie unter [Ratgeber für Voicemailvorschau](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/voice-mail-preview-advisor).

