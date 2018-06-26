---
title: 'Delegieren von Rollenzuweisungen: Exchange 2013 Help'
TOCTitle: Delegieren von Rollenzuweisungen
ms:assetid: ed2d00d9-90c9-49dc-ab8a-cd791569aeed
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351237(v=EXCHG.150)
ms:contentKeyID: 50477002
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Delegieren von Rollenzuweisungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-02_

Die Delegierung von Verwaltungsrollen ermöglicht Rollenempfängern die Zuweisung einer bestimmten Verwaltungsrolle zu anderen Verwaltungsrollengruppen, Richtlinien für Verwaltungsrollenzuweisungen, Benutzern oder universellen Sicherheitsgruppen. Standardmäßig können nur Mitglieder der Verwaltungsrollengruppe Organisationsverwaltung Rollenzuweisungen delegieren. Wenn eine neue Installation von Microsoft Exchange Server 2013 bereitgestellt wird, ist nur das Benutzerkonto Mitglied der Rollengruppe Organisationsverwaltung, das Exchange 2013 installiert hat.

Wenn Sie einer Rollengruppe eine delegierende Rollenzuweisung zuweisen, kann jedes Mitglied der Rollengruppe die zugeordnete Verwaltungsrolle an andere Rollenempfänger delegieren.


> [!IMPORTANT]
> Durch das Delegieren von Rollenzuweisungen werden dem Rollenempfänger nicht die von der Rolle gewährten Berechtigungen erteilt, sondern nur die Möglichkeit, die Rolle anderen zuzuweisen. Wenn Sie dem Rollenempfänger außerdem die durch die Rolle gewährten Berechtigungen erteilen möchten, müssen Sie auch eine reguläre Rollenzuweisung erstellen. Informationen zum Erstellen einer regulären Rollenzuweisung finden Sie unter den folgenden Themen:<BR><A href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</A><BR><A href="manage-role-assignment-policies-exchange-2013-help.md">Verwalten von Rollenzuweisungsrichtlinien</A><BR><A href="add-a-role-to-a-user-or-usg-exchange-2013-help.md">Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe</A>




> [!NOTE]
> In diesem Thema wird die Delegierung der Verwaltungsrollenzuweisung erläutert. Wenn Sie delegieren möchten, wer den Rollengruppen Mitglieder hinzufügen oder daraus entfernen kann und welche Delegierungsmethode empfohlen wird, finden Sie weitere Informationen unter <A href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</A>.



Weitere Informationen zu regulären Rollenzuweisungen und delegierenden Verwaltungsrollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit der Verwaltung von Berechtigungen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollenzuweisungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Delegieren einer Verwaltungsrolle mithilfe der Shell

Delegierende Rollenzuweisungen können anhand derselben vordefinierten Bereiche, auf Empfängerfiltern oder Serverfiltern basierenden Bereiche, auf Serverlisten basierenden Bereiche und OU-Bereiche (Organisationseinheit) erstellt werden, die zum Erstellen regulärer oder exklusiver Bereiche verwendet werden können. Der einzige Unterschied zwischen der Erstellung einer regulären Rollenzuweisung und einer delegierenden Rollenzuweisung besteht darin, dass dem Befehl die Option *Delegating* hinzugefügt werden muss. Weitere Informationen zum Erstellen von Rollenzuweisungen finden Sie unter den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)


> [!NOTE]
> Eine delegierende Rollenzuweisung zu einer Richtlinie für Verwaltungsrollenzuweisungen kann nicht erstellt werden.



In diesem Beispiel wird eine delegierende Rollenzuweisung erstellt, um Mitgliedern der Rollengruppe "Senior Admins" das Zuweisen der Rolle E-Mail-Empfänger zu einem beliebigen Rollenempfänger in der Exchange-Organisation zu ermöglichen.

    New-ManagementRoleAssignment -Role "Mail Recipients" -SecurityGroup "Senior Admins" -Name "Mail Recipients_Senior Admin - Delegate" -Delegating

In diesem Beispiel wird eine delegierende Rollenzuweisung erstellt, um Mitgliedern der Rollengruppe "Senior Admins" das Zuweisen der Rolle E-Mail-Empfänger nur zu Benutzern in der Organisationseinheit "Sales/Users" in der Domäne "contoso.com" zu ermöglichen.

    New-ManagementRoleAssignment -Role "Mail Recipients" -SecurityGroup "Senior Admins" -Name "Mail Recipients_Senior Admins - Delegate" -RecipientOrganizationalUnitScope contoso.com/sales/users -Delegating

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

