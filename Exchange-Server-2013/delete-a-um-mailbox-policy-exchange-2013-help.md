---
title: 'Löschen einer um-Postfachrichtlinie: Exchange Online Help'
TOCTitle: Löschen einer um-Postfachrichtlinie
ms:assetid: c8758464-3c52-4dd3-b2a6-142a99bb0628
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124536(v=EXCHG.150)
ms:contentKeyID: 50554906
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Löschen einer um-Postfachrichtlinie

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-05_

Wenn eine Unified Messaging-Postfachrichtlinie (UM) gelöscht wird, kann diese UM-Postfachrichtlinie nicht mehr Empfängern zugeordnet werden, die für UM aktiviert sind. Sie können keine UM-Postfachrichtlinie löschen, auf die von UM-aktivierten Postfächern verwiesen wird. Und Sie können einen UM-Wählplan nicht löschen, wenn diesem eine UM-Postfachrichtlinie zugeordnet ist.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Löschen einer UM-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** auf der Symbolleiste auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Löschen einer UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird die UM-Postfachrichtlinie `MyUMMailboxPolicy` gelöscht.

    Remove-UMMailboxPolicy -Identity MyUMMailboxPolicy

