---
title: 'Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln: Exchange 2013 Help'
TOCTitle: Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln
ms:assetid: 89dfcbb3-0568-4bbf-a885-746b91ba307e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876918(v=EXCHG.150)
ms:contentKeyID: 50476203
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Mithilfe verknüpfter Verwaltungsrollengruppen in Microsoft Exchange Server 2013 können Sie eine Rollengruppe in einer Exchange 2013-Ressourcengesamtstruktur mit einer universellen Sicherheitsgruppe in einer fremden Benutzergesamtstruktur verknüpfen. Dies ist hilfreich, wenn Administratoren mit Konten in der Benutzergesamtstruktur die Server, auf denen Exchange aktiv ist, in der Ressourcengesamtstruktur verwalten sollen. Weitere Informationen zu verknüpften Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Standardmäßig sind in Exchange 2013 eine Reihe von integrierten Rollengruppen vorhanden, die die Berechtigungen zum Verwalten unterschiedlicher Funktionen und Jobfunktionen bereitstellen. Dabei stellt jede Rollengruppe bestimmte Berechtigungen für jede Funktion und jede Jobfunktion bereit. Allerdings können diese Rollengruppen nicht mit universellen Sicherheitsgruppen in einer fremden Gesamtstruktur verknüpft werden. Sie können nur Benutzer und universelle Sicherheitsgruppen aus der lokalen Ressourcengesamtstruktur enthalten. Es besteht jedoch die Möglichkeit, diese integrierten Gruppen unter Verwendung verknüpfter Rollengruppen zu replizieren.

Sie können jede integrierte Rollengruppe als verknüpfte Rollengruppe neu erstellen. Dabei werden alle Verwaltungsrollen und Verwaltungsbereiche, die den einzelnen Rollengruppen zugeordnet sind, der neuen verknüpften Rollengruppe hinzugefügt. Weitere Informationen zu Verwaltungsrollen und -bereichen finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollengruppen gibt? Weitere Informationen finden Sie hier: [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Für die Konfiguration einer verknüpften Rollengruppe ist eine unidirektionale Vertrauensstellung zwischen der Active Directory-Ressourcengesamtstruktur, in der sich die verknüpfte Rollengruppe befinden soll, und der fremden Active Directory-Gesamtstruktur, in der sich die Benutzer oder Sicherheitsgruppen befinden, erforderlich. Zwischen der Ressourcengesamtstruktur und der fremden Gesamtstruktur muss eine Vertrauensstellung bestehen.

  - Sie müssen über die folgenden Informationen zur fremden Active Directory-Gesamtstruktur verfügen:
    
      - **Anmeldeinformationen**   Sie müssen über einen Benutzernamen und ein Kennwort verfügen, die den Zugriff auf die fremde Active Directory-Gesamtstruktur ermöglichen. Diese Informationen werden mit dem Parameter *LinkedCredential* des Cmdlets **New-RoleGroup** verwendet. Diese Informationen werden durch Ausführen des Cmdlets **Get-Credential** abgerufen. Das Format des Benutzernamens ist *Domäne*\\*Benutzername*.
    
      - **Domänencontroller**   Sie müssen über den vollqualifizierten Domänennamen (FQDN) eines Active Directory-Domänencontrollers in der fremden Active Directory-Gesamtstruktur verfügen. Diese Informationen werden mit dem Parameter *LinkedDomainController* des Cmdlets **New-RoleGroup** verwendet.
    
      - **Fremde universelle Sicherheitsgruppe**   Sie müssen über den vollständigen Namen einer universellen Sicherheitsgruppe in der fremden Active Directory-Gesamtstruktur verfügen, die die Mitglieder enthält, die Sie der verknüpften Rollengruppe zuweisen möchten. Diese Informationen werden mit dem Parameter *LinkedForeignGroup* des Cmdlets **New-RoleGroup** verwendet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Erstellen verknüpfter Rollengruppen, um integrierte Rollen zu replizieren

In jedem der folgenden Abschnitte wird erläutert, wie die einzelnen Rollengruppen als verknüpfte Rollengruppe neu erstellt werden. Führen Sie die in den einzelnen Abschnitten aufgeführten Schritte aus, um alle integrierten Rollengruppen als verknüpfte Rollengruppen neu zu erstellen.

## Erstellen der verknüpften Rollengruppe "Organisationsverwaltung"

Um die Rollengruppe Organisationsverwaltung als verknüpfte Rollengruppe neu zu erstellen, müssen Sie andere Schritte ausführen als die zur Neuerstellung integrierter Rollengruppen. Das liegt daran, dass zwischen der Rollengruppe Organisationsverwaltung und allen Verwaltungsrollen delegierende Rollenzuweisungen bestehen. Bei der Neuerstellung der delegierenden Rollenzuweisungen ist ein zusätzlicher Schritt erforderlich.

1.  Erstellen Sie in der fremden Gesamtstruktur eine universelle Sicherheitsgruppe, die mit der Rollengruppe Organisationsverwaltung verknüpft wird.

2.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen.
    
        $ForeignCredential = Get-Credential

3.  Speichern Sie alle Rollenzuweisungen der Rollengruppe Organisationsverwaltung in einer Variablen.
    
        $OrgMgmt  = Get-RoleGroup "Organization Management"

4.  Erstellen Sie die verknüpfte Rollengruppe Organisationsverwaltung, und fügen Sie ihr die Rollen hinzu, die der integrierten Rollengruppe Organisationsverwaltung zugewiesen sind.
    
        New-RoleGroup "Organization Management - Linked" -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles $OrgMgmt.Roles

5.  Entfernen Sie alle regulären Zuweisungen zwischen der neuen verknüpften Rollengruppe Organisationsverwaltung und den "My\*"-Endbenutzerrollen.
    
        Get-ManagementRoleAssignment -RoleAssignee "Organization Management - Linked" -Role My* | Remove-ManagementRoleAssignment

6.  Fügen Sie delegierende Rollenzuweisungen zwischen der neuen verknüpften Rollengruppe Organisationsverwaltung und allen Verwaltungsrollen hinzu.
    
        Get-ManagementRole | New-ManagementRoleAssignment -SecurityGroup "Organization Management - Linked" -Delegating

In diesem Beispiel wird angenommen, dass die folgenden Werte für die einzelnen Parameter verwendet werden:

  - **LinkedForeignGroup** `Organization Management Administrators`

  - **LinkedDomainController** `DC01.users.contoso.com`

Unter Verwendung der oben aufgeführten Werte wird in diesem Beispiel die Rollengruppe Organisationsverwaltung als verknüpfte Rollengruppe neu erstellt.

    $ForeignCredential = Get-Credential
    $OrgMgmt  = Get-RoleGroup "Organization Management"
    New-RoleGroup "Organization Management - Linked" -LinkedForeignGroup "Organization Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $OrgMgmt.Roles
    Get-ManagementRoleAssignment -RoleAssignee "Organization Management - Linked" -Role My* | Remove-ManagementRoleAssignment
    Get-ManagementRole | New-ManagementRoleAssignment -SecurityGroup "Organization Management - Linked" -Delegating

## Alle anderen verknüpften Rollengruppen erstellen

Um alle anderen integrierten Rollengruppen, die neben der Rollengruppe Organisationsverwaltung noch vorhanden sind, als verknüpfte Rollengruppen neu zu erstellen, müssen Sie für jede Gruppe die folgenden Schritte ausführen.

1.  Erstellen Sie in der fremden Gesamtstruktur eine universelle Sicherheitsgruppe für jede Rollengruppe, die mit den einzelnen neuen Rollengruppen verknüpft wird.

2.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen. Dieser Schritt muss nur einmal ausgeführt werden.
    
        $ForeignCredential = Get-Credential

3.  Rufen Sie eine Liste von Rollengruppen ab, indem Sie das folgende Cmdlet verwenden.
    
        Get-RoleGroup

4.  Gehen Sie für jede Rollengruppe mit Ausnahme der Rollengruppe Organisationsverwaltung folgendermaßen vor.
    
        $RoleGroup = Get-RoleGroup <name of role group to re-create>
        New-RoleGroup "<role group name> - Linked" -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles

5.  Wiederholen Sie den vorherigen Schritt für jede integrierte Rollengruppe, die als verknüpfte Rollengruppe neu erstellt werden soll.

In diesem Beispiel wird angenommen, dass die folgenden Werte für die einzelnen Parameter verwendet werden:

  - **LinkedDomainController** `DC01.users.contoso.com`

  - **Integrierte Rollengruppen, die als verknüpfte Rollengruppen neu erstellt werden sollen** `Recipient Management, Server Management`

  - **Fremde Gruppe für die verknüpfte Rollengruppe "Empfängerverwaltung"** `Recipient Management Administrators`

  - **Fremde Gruppe für die verknüpfte Rollengruppe "Server"** `Server Management Administrators`

Unter Verwendung der oben aufgeführten Werte werden in diesem Beispiel die Rollengruppen Empfängerverwaltung und "Serververwaltung" als verknüpfte Rollengruppen neu erstellt.

    $ForeignCredential = Get-Credential
    Get-RoleGroup
    $RoleGroup = Get-RoleGroup "Recipient Management"
    New-RoleGroup "Recipient Management - Linked" -LinkedForeignGroup "Recipient Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles
    $RoleGroup = Get-RoleGroup "Server Management"
    New-RoleGroup "Server Management - Linked" -LinkedForeignGroup "Server Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles

## Weitere Aufgaben

Nachdem Sie die verknüpften Rollengruppen erstellt haben, können Sie die folgenden Aufgaben ausführen:

Fügen Sie den universellen Sicherheitsgruppen Mitglieder hinzu, indem Sie Active Directory-Benutzer und -Computer in der fremden Gesamtstruktur verwenden.

Entfernen Sie Mitglieder der integrierten Rollengruppen. Weitere Informationen finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Fügen Sie den Bereich von Rollen in den neu verknüpften Rollengruppen hinzu bzw. entfernen oder ändern Sie diesen. Weitere Informationen finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Erstellen Sie weitere verknüpfte Rollengruppen. Weitere Informationen finden Sie unter [Verwalten von verknüpften Rollengruppen](manage-linked-role-groups-exchange-2013-help.md).

