---
title: 'Steuern der automatischen Postfachverteilung mithilfe von Datenbankbereichen: Exchange 2013 Help'
TOCTitle: Steuern der automatischen Postfachverteilung mithilfe von Datenbankbereichen
ms:assetid: 8eaff177-2251-4c8b-8570-c91a77d0a6fc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff628332(v=EXCHG.150)
ms:contentKeyID: 50476150
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Steuern der automatischen Postfachverteilung mithilfe von Datenbankbereichen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Die automatische Postfachverteilung ist eine Funktion in Microsoft Exchange Server 2013, die eine Postfachdatenbank zufällig auswählt, um ein neues oder verschobenes Postfach darin zu speichern, wenn Sie nicht explizit eine Datenbank angeben. Diese Funktion kann nützlich sein, wenn unerfahrene Administratoren oder Helpdeskmitarbeiter Postfächer erstellen sollen, ohne unbedingt wissen zu müssen, in welcher Postfachdatenbank sie erstellt werden sollten.

Sie können mit Datenbankverwaltungsbereichen steuern, welche Postfachdatenbanken mithilfe der automatischen Postfachverteilung ausgewählt werden können. Wenn Sie Datenbankbereiche auf einen Administrator anwenden, stehen diesem Administrator ausschließlich die Datenbanken zur Verfügung, die dem definierten Datenbankbereich entsprechen. Da bei der automatischen Postfachverteilung der Kontext des aktuellen Benutzers verwendet wird, stellen auch die auf den Administrator angewendeten Datenbankbereiche Einschränkungen dar.

Weitere Informationen zur automatischen Postfachverteilung, zu Datenbankbereichen und zu Rollenzuweisungen finden Sie in den folgenden Themen:

  - [Automatische Postfachverteilung](automatic-mailbox-distribution-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Bereichen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsbereiche" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines Datenbankbereichs

Entscheiden Sie in diesem Schritt, welche Datenbanken Sie in den Datenbankbereich einschließen möchten. Entscheiden Sie außerdem, ob Sie eine statische Liste von Datenbanken angeben möchten oder ob Sie einen Datenbankfilter erstellen möchten, der nur die Datenbanken einschließt, die mit den angegebenen Kriterien übereinstimmen.


> [!IMPORTANT]
> Die zu Datenbankbereichen zugeordneten Rollenzuweisungen werden nur auf Benutzer angewendet, die eine Verbindung mit Servern herstellen, auf denen Microsoft Exchange Server 2010 Service Pack&nbsp;1 (SP1) oder höher oder Exchange 2013 ausgeführt wird. Wenn ein Benutzer, dem eine Rollenzuweisung mit einem zugeordneten Datenbankbereich zugewiesen wurde, eine Verbindung mit einem Server herstellt, auf dem eine ältere Version als Exchange 2010 SP1 ausgeführt wird, dann wird die Rollenzuweisung nicht auf den Benutzer angewendet. Dem Benutzer werden dann keine von der Rollenzuweisung bereitgestellten Berechtigungen erteilt.



## Verwenden eines listenbasierten Datenbankbereichs

Verwenden Sie eine Datenbankliste, wenn Sie eine statische Liste von Postfachdatenbanken definieren möchten, die in diesen Bereich eingeschlossen werden sollen. Verwenden Sie zum Erstellen eines listenbasierten Datenbankbereichs die folgende Syntax.

    New-ManagementScope -Name <scope name> -DatabaseList <database 1>, <database 2...>

In diesem Beispiel wird ein Bereich erstellt, der nur auf die Datenbanken "Database 1", "Database 2" und "Database 3" angewendet wird.

    New-ManagementScope -Name "Accounting databases" -DatabaseList "Database 1", "Database 2", "Database 3"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Verwenden eines filterbasierten Datenbankbereichs

Verwenden Sie einen Datenbankfilter, wenn Sie einen dynamischen Datenbankbereich erstellen möchten, der nur die Datenbanken einschließt, die mit den angegebenen Kriterien übereinstimmen. Dies kann hilfreich sein, wenn Sie den Datenbankbereich nach seiner Erstellung nicht verwalten möchten und Sie Standardwerte für Ihre Organisation definiert haben, mit denen bestimmte Sätze von Postfachdatenbanken identifiziert werden können.

Eine Liste filterbarer Datenbankeigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Verwenden Sie zum Erstellen eines filterbasierten Datenbankbereichs die folgende Syntax.

    New-ManagementScope -Name <scope name> -DatabaseRestrictionFilter <filter query>

In diesem Beispiel wird ein Bereich mit allen Datenbanken erstellt, deren Eigenschaft **Name** die Zeichenfolge "ACCT" enthält.

    New-ManagementScope -Name "Accounting Databases" -DatabaseRestrictionFilter { Name -Like '*ACCT*' }

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Schritt 2: Hinzufügen des Datenbankbereichs zu einer Verwaltungsrollenzuweisung

Nach dem Erstellen des Bereichs muss dieser zu einer neuen oder vorhandenen Verwaltungsrollenzuweisung hinzugefügt werden. Sie sollten Verwaltungsrollengruppen verwenden, um Administratorberechtigungen zu steuern. Daher wird in den Beispielen in diesem Schritt eine beispielhafte Rollengruppe mit dem Namen "Accounting Administrators" verwendet. Weitere Informationen zum Erstellen einer Rollengruppe finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Nachdem Sie die Rolle einer Rollengruppe mit dem Datenbankbereich zugewiesen haben, können die Mitglieder der Rollengruppe Postfächer ausschließlich in den Datenbanken im Bereich erstellen und dorthin verschieben.

Eine Liste mit integrierten Rollen, die Sie Rollengruppen zuweisen können, finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

## Hinzufügen einer neuen Rollenzuweisung

Verwenden Sie dieses Verfahren, wenn Sie gerade eine Rollengruppe erstellt haben und ihr nun Rollen hinzufügen möchten.

Verwenden Sie die folgende Syntax, um eine Rollenzuweisung zwischen der gewünschten Verwaltungsrolle und der neuen Rollengruppe mit dem neuen Datenbankbereich zu erstellen.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -CustomConfigWriteScope <database scope name>

In diesem Beispiel wird eine Rollenzuweisung zwischen den Rollen "Mail Recipients" und "Mail Recipient Creation" und der Rollengruppe "Accounting Administrators" erstellt; dabei wird der Datenbankbereich "Accounting Databases" verwendet.

    New-ManagementRoleAssignment -SecurityGroup "Accounting Administrators" -Role "Mail Recipients" -CustomConfigWriteScope "Accounting Databases"
    New-ManagementRoleAssignment -SecurityGroup "Accounting Administrators" -Role "Mail Recipient Creation" -CustomConfigWriteScope "Accounting Databases"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Ändern einer vorhandenen Rollenzuweisung

Verwenden Sie dieses Verfahren, wenn Sie über eine vorhandene Rollengruppe verfügen, bei der bereits Rollenzuweisungen zwischen der Rollengruppe und den Rollen bestehen, auf die Sie den neuen Datenbankbereich anwenden möchten.

Bei diesem Verfahren wird das Pipelining verwendet. Weitere Informationen finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

Verwenden Sie die folgende Syntax, um eine Rollenzuweisung zwischen der Verwaltungsrolle, auf die Sie den Datenbankbereich anwenden möchten, und einer vorhandenen Rollengruppe zu ändern.

    Get-ManagementRoleAssignment -RoleAssignee <role group name> -Role <role name> | Set-ManagementRoleAssignment -CustomConfigWriteScope <database scope name>

In diesem Beispiel wird der Datenbankbereich "Accounting Databases" den Rollen "Mail Recipients" und "Mail Recipient Creation" hinzugefügt, die der Rollengruppe "Accounting Administrators" zugewiesen sind.

    Get-ManagementRoleAssignment -RoleAssignee "Accounting Administrators" -Role "Mail Recipients" | Set-ManagementRoleAssignment -CustomConfigWriteScope "Accounting Databases"
    Get-ManagementRoleAssignment -RoleAssignee "Accounting Administrators" -Role "Mail Recipient Creation" | Set-ManagementRoleAssignment -CustomConfigWriteScope "Accounting Databases"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)) oder [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Schritt 3: Hinzufügen von Mitgliedern zu einer Rollengruppe (falls zutreffend)

Informationen zum Hinzufügen von Mitgliedern zu einer Rollengruppe finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).


> [!IMPORTANT]
> Wenn Sie dieser Rollengruppe Mitglieder hinzufügen, um einzuschränken, in welchen Datenbanken sie Benutzer erstellen können oder in welche Datenbanken sie Postfächer verschieben können, stellen Sie sicher, dass sie nicht zugleich Mitglied anderer Rollengruppen sind, die möglicherweise zusätzliche Rechte erteilen.



## Schritt 4: Entfernen von Mitgliedern aus einer Rollengruppe (falls zutreffend)

Wenn Sie einer neuen Rollengruppe Mitglieder hinzugefügt haben, um einzuschränken, in welchen Datenbanken sie Postfächer erstellen können oder in welche Datenbanken sie Postfächer verschieben können, und diese Mitglieder zugleich Mitglied einer anderen Rollengruppe sind, die zusätzliche Rechte besitzt, entfernen Sie sie aus der alten Rollengruppe. Weitere Informationen finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

