---
title: 'Legen Sie die Voicemailvorschau Partner-ID: Exchange Online Help'
TOCTitle: Legen Sie die Voicemailvorschau Partner-ID
ms:assetid: ab98c320-9952-47a7-b141-ddfc2c0ad419
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630924(v=EXCHG.150)
ms:contentKeyID: 51409324
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die Voicemailvorschau Partner-ID

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-13_

Sie können eine Voicemailvorschau-Partner-ID für eine Unified Messaging-Postfachrichtlinie (UM) festlegen. Nach dem Festlegen der Voicemailvorschau-Partner-ID für eine UM-Postfachrichtlinie wird die Einstellung auf alle UM-aktivierten Benutzer angewendet, die dieser UM-Postfachrichtlinie zugeordnet sind.


> [!NOTE]
> Sie müssen die Shell zum Festlegen der Voicemailvorschau-Partner-ID verwenden.



Weitere Informationen zum Voicemailvorschau-Partnerprogramm finden Sie unter [Ratgeber für Voicemailvorschau](voice-mail-preview-advisor-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Voicemailvorschau finden Sie unter [Voice Mail Preview Prozeduren](voice-mail-preview-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Festlegen der Voicemailvorschau-Partner-ID für eine UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird die Voicemailvorschau-Partner-ID für die UM-Postfachrichtlinie *MyUMMailboxPolicy* auf "CON123-2010" festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy 
    -VoiceMailPreviewPartnerAssignedID CON123-2010

