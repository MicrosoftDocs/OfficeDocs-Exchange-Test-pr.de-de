---
title: 'Wiederherst. der Standardkonfiguration für Detailvorlage: Exchange 2013-Hilfe'
TOCTitle: Stellen Sie eine Detailvorlage die Standardkonfiguration wieder her
ms:assetid: 84c5f49b-614d-4f0e-8701-0979a2eb90bf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232102(v=EXCHG.150)
ms:contentKeyID: 50476168
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Stellen Sie eine Detailvorlage die Standardkonfiguration wieder her

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

Der Detailvorlagen-Editor verfügt nicht über die Schaltfläche **Rückgängig**, und es gibt auch keine Tastenkombination, mit der eine Aktion rückgängig gemacht werden kann. Wenn Sie einer Vorlage ein Objekt hinzugefügt haben, können Sie es nur mit der ENTF-TASTE wieder löschen. Zum Rückgängigmachen eines Löschvorgangs müssen Sie die Einstellung erneut zuweisen. Sie können die ursprünglichen Einstellungen auch wiederherstellen, indem Sie den Detailvorlagen-Editor beenden, ohne die Änderungen zu speichern. Sollen nach dem Speichern Änderungen rückgängig gemacht werden, können Sie die Vorlage wiederherstellen. Beim Wiederherstellen einer Vorlage gehen sämtliche Anpassungen verloren, und die Vorlage verfügt wieder über die ursprüngliche Konfiguration.

In diesem Thema wird erläutert, wie die Standardkonfiguration einer Detailvorlage mithilfe der Exchange 2013 Toolbox oder der Exchange-Verwaltungsshell wiederhergestellt werden kann.

Weitere Informationen zu Detailvorlagen finden Sie unter [Detailvorlagen](details-templates-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Detailvorlagen" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wiederherstellen der Standardkonfiguration einer Detailvorlage mithilfe der Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange Toolbox**.

2.  Klicken Sie in **Exchange Toolbox** auf **Detailvorlagen-Editor**, und klicken Sie anschließend im Aktionsbereich auf **Tool öffnen**.

3.  Wählen Sie im **Detailvorlagen-Editor** im Detailbereich die wiederherzustellende Vorlage aus, und klicken Sie anschließend im Aktionsbereich auf **Wiederherstellen**.

4.  Klicken Sie auf **Ja**, um das Wiederherstellen des ursprünglichen Zustands der Vorlage zu bestätigen. Alle Anpassungen gehen dabei verloren.

## Wiederherstellen der Standardkonfiguration einer Detailvorlage mithilfe der Shell

In diesem Beispiel wird die Kontaktdetailvorlage für "Englisch USA" wiederhergestellt.

    Restore-DetailsTemplate -Identity "en-US\Contact"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Restore-DetailsTemplate](https://technet.microsoft.com/de-de/library/bb125188\(v=exchg.150\)).

