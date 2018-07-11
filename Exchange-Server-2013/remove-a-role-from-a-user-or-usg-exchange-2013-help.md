---
title: 'Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe: Exchange 2013 Help'
TOCTitle: Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe
ms:assetid: df3510ef-e0c2-4d3c-81b0-7dc3e70c01a0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351196(v=EXCHG.150)
ms:contentKeyID: 50476911
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-02_

Über Verwaltungsrollenzuweisungen wird einem Benutzer oder einer universellen Sicherheitsgruppe (Universal Security Group, USG) eine Verwaltungsrolle zugewiesen. Wenn Sie eine Verwaltungsrolle entfernen, können die der Rolle zugewiesenen Benutzer nicht mehr auf die für diese Rolle verfügbaren Cmdlets zugreifen. Weitere Informationen zu Verwaltungsrollenzuweisungen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollenzuweisungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Entfernen einer Verwaltungsrollenzuweisung

Wenn Sie den Namen der zu entfernenden Rollenzuweisung kennen, verwenden Sie die folgende Syntax.

    Remove-ManagementRoleAssignment <assignment name>

Um beispielsweise die Rollenzuweisung "Tier 2 Help Desk Assignment" zu entfernen, verwenden Sie den folgenden Befehl.

    Remove-ManagementRoleAssignment "Tier 2 Help Desk Assignment"

Wenn Sie den Namen der Rollenzuweisung nicht kennen, können Sie die folgende Syntax verwenden.

    Get-ManagementRoleAssignment -RoleAssignee <user or USG> -Role <role name> -Delegating <$true | $false> | Remove-ManagementRoleAssignment 

Um beispielsweise die reguläre Rollenzuweisung "Mail Recipients" von dem Benutzer "davids" zu entfernen, verwenden Sie den folgenden Befehl.

    Get-ManagementRoleAssignment -RoleAssignee davids -Role "Mail Recipients" -Delegating $false | Remove-ManagementRoleAssignment

