---
title: 'Verwalten von Rollengruppenmitgliedern: Exchange 2013 Help'
TOCTitle: Verwalten von Rollengruppenmitgliedern
ms:assetid: c064729d-7cda-47fc-b105-acf4b300d430
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657492(v=EXCHG.150)
ms:contentKeyID: 50476617
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Rollengruppenmitgliedern

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-08_

In diesem Thema wird erläutert, wie Sie Mitglieder einer Verwaltungsrollengruppe in Microsoft Exchange Server 2013 hinzufügen, entfernen oder anzeigen können. Weitere Informationen zu Rollengruppen in Exchange 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Rollengruppen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Hinzufügen von Mitgliedern zu einer Rollengruppe

Damit ein Benutzer die Berechtigungen erhält, die von einer Rollengruppe erteilt werden, müssen Sie den Benutzer, eine universelle Sicherheitsgruppe (USG) oder eine andere Rollengruppe (deren Mitglied der Benutzer ist) als Mitglied der Rollengruppe hinzufügen.

## Hinzufügen von Mitgliedern zu einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, der Sie Mitglieder hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie im Abschnitt **Mitglieder** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie die Benutzer, universellen Sicherheitsgruppen oder Rollengruppen aus, die Sie der Rollengruppe hinzufügen möchten, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.

5.  Klicken Sie auf **Speichern**, um die Änderungen an der Rollengruppe zu speichern.

## Hinzufügen von Mitgliedern zu einer Rollengruppe mithilfe der Shell

Beispiele

Beispiele

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, dass Sie einer Rollengruppe erfolgreich ein oder mehrere Mitglieder hinzufügt haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, der Sie Mitglieder hinzugefügt haben.

3.  Vergewissern Sie sich im Detailbereich der Rollengruppe, dass die von Ihnen hinzugefügten Mitglieder aufgeführt werden.

## Entfernen von Mitgliedern aus einer Rollengruppe

Um die über eine Rollengruppe erteilten Berechtigungen eines Benutzers zu entfernen, muss der Benutzer – oder die universelle Sicherheitsgruppe, deren Mitglied der Benutzer ist – aus der Rollengruppe entfernt werden.

## Entfernen von Mitgliedern aus einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, aus der Sie Mitglieder entfernen möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie im Abschnitt **Mitglieder** die Mitglieder aus, die Sie entfernen möchten, klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") und anschließend auf **Speichern**.

## Entfernen von Mitgliedern aus einer Rollengruppe mithilfe der Shell

Beispiele

Beispiele

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, dass Sie ein oder mehrere Mitglieder erfolgreich aus einer Rollengruppe entfernt haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollegruppen aus, aus der Sie Mitglieder entfernen möchten.

3.  Vergewissern Sie sich im Detailbereich der Rollengruppe, dass die von Ihnen entfernten Mitglieder nicht mehr aufgeführt werden.

## Anzeigen der Mitglieder einer Rollengruppe

Die Mitglieder einer Rollengruppe erhalten die Berechtigungen der Verwaltungsrollen, die der Rollengruppe zugewiesen sind. Sie können die Mitglieder einer Rollengruppe anzeigen, um Benutzer, universelle Sicherheitsgruppen oder andere Rollengruppen zu ermitteln, denen über die von Ihnen angegebene Rollengruppe Berechtigungen erteilt werden.

## Anzeigen der Mitglieder einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppen aus, deren Mitglieder Sie anzeigen möchten.

3.  Zeigen Sie im Detailbereich der Rollengruppe die Rollengruppenmitglieder an.

## Anzeigen der Mitglieder einer Rollengruppe mithilfe der Shell

Beispiele

