---
title: 'Legen Sie die Adresse des Partners Voicemailvorschau: Exchange Online Help'
TOCTitle: Legen Sie die Adresse des Partners Voicemailvorschau
ms:assetid: 57fbed1e-1b14-4939-95e6-ef7c072f32a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630917(v=EXCHG.150)
ms:contentKeyID: 51409297
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die Adresse des Partners Voicemailvorschau

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-13_

Sie können eine Partneradresse für die Voicemailvorschau für eine Unified Messaging-Postfachrichtlinie festlegen. Nachdem Sie die Partneradresse für die Voicemailvorschau für eine UM-Postfachrichtlinie festgelegt haben, wird die Einstellung auf alle UM-aktivierten Benutzer angewendet, die mit der Postfachrichtlinie verknüpft sind.


> [!NOTE]
> Sie müssen die Shell zum Festlegen der Partneradresse einer Voicemailvorschau verwenden.



Weitere Informationen zum Voicemailvorschau-Partnerprogramm finden Sie unter [Ratgeber für Voicemailvorschau](https://technet.microsoft.com/de-de/library/Ee364730(v=EXCHG.150)).

Weitere Verwaltungsaufgaben im Zusammenhang mit der Voicemailvorschau finden Sie unter [Voice Mail Preview Prozeduren](https://technet.microsoft.com/de-de/library/JJ938009(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Festlegen der Partneradresse für die Voicemailvorschau für eine UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird die Partneradresse der Voicemailvorschau für eine UM-Postfachrichtlinie namens *MyUMMailboxPolicy* auf "exumvmp@fabrikam.com" festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerAddress exumvmp@fabrikam.com

