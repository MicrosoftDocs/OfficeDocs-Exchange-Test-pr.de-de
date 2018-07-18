---
title: 'Entfernen eines Bereichs Rolle: Exchange 2013 Help'
TOCTitle: Entfernen eines Bereichs Rolle
ms:assetid: ad17cba0-a8d3-4f40-b3c9-c37e6e5c3f36
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351051(v=EXCHG.150)
ms:contentKeyID: 50476425
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen eines Bereichs Rolle

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-02_

Verwaltungsrollenbereiche legen fest, welche Objekte für einen Benutzer verfügbar gemacht werden, und der die Objekte anschließend unter Verwendung der Cmdlets und Parameter ändern kann, die dem Benutzer zugewiesen sind. Wenn Sie einen Bereich nicht mehr verwenden, kann dieser entfernt werden. Weitere Informationen zu Verwaltungsrollenbereichen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsbereiche" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Bevor Sie einen Bereich entfernen können, müssen Sie den Bereich aus allen Verwaltungsrollenzuweisungen entfernen, die den Bereich möglicherweise verwenden. Weitere Informationen zum Entfernen eines Bereichs aus einer Rollenzuweisung finden Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Entfernen eines Bereichs mithilfe der Shell

Verwenden Sie die folgende Syntax, um einen Bereich zu entfernen.

    Remove-ManagementScope <scope name>

Um beispielsweise den Bereich "Dublin Servers" zu entfernen, verwenden Sie den folgenden Befehl.

    Remove-ManagementScope "Dublin Servers"

