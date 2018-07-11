---
title: 'Legen Sie die maximale Dauer für einen Voicemailvorschau-partner: Exchange Online Help'
TOCTitle: Legen Sie die maximale Dauer für einen Voicemailvorschau-partner
ms:assetid: 18f928ff-f4cc-4eed-a466-de13388780b3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630912(v=EXCHG.150)
ms:contentKeyID: 51409271
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die maximale Dauer für einen Voicemailvorschau-partner

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-13_

Sie können die maximale Nachrichtendauer für einen Voicemailvorschau-Partner für eine UM-Postfachrichtlinie (Unified Messaging) festlegen. Nachdem Sie die maximale Nachrichtendauer festgelegt haben, wird die Einstellung auf alle UM-aktivierten Benutzer angewendet, die mit dieser Postfachrichtlinie verknüpft sind.


> [!NOTE]
> Sie müssen die Shell verwenden, um die maximale Nachrichtendauer für einen Voicemailvorschau-Partner festzulegen.



Weitere Informationen zum Voicemailvorschau-Partnerprogramm finden Sie unter [Ratgeber für Voicemailvorschau](voice-mail-preview-advisor-exchange-2013-help.md).

Weitere Verwaltungsaufgaben im Zusammenhang mit der Voicemailvorschau finden Sie unter [Voice Mail Preview Prozeduren](voice-mail-preview-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Festlegen der maximalen Nachrichtendauer für einen Voicemailvorschau-Partner

In diesem Beispiel wird die maximale Nachrichtendauer für einen Voicemailvorschau-Partner für eine UM-Postfachrichtlinie mit dem Namen *MyUMMailboxPolicy* auf 300 Sekunden (5 Minuten) festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerMaxMessageDuration 300

