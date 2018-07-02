---
title: 'Konfigurieren von Exchange 2013 für geteilte Berechtigungen: Exchange 2013 Help'
TOCTitle: Konfigurieren von Exchange 2013 für geteilte Berechtigungen
ms:assetid: 8c74f893-a6f3-4869-8571-3bc0f662cc87
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638155(v=EXCHG.150)
ms:contentKeyID: 50476222
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Exchange 2013 für geteilte Berechtigungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Mit geteilten Berechtigungen können zwei verschiedene Gruppen wie Active Directory-Administratoren und Microsoft Exchange Server 2013-Administratoren ihre jeweiligen Dienste, Objekte und Attribute verwalten. Dabei verwalten Active Directory-Administratoren Sicherheitsprinzipale wie beispielsweise Benutzer, die Berechtigungen für den Zugriff auf eine Active Directory-Gesamtstruktur bereitstellen, während Exchange-Administratoren die Exchange-Attribute für Active Directory-Objekte und die Exchange-spezifische Objekterstellung und -verwaltung verwalten.

Microsoft Exchange Server 2013 bietet die folgenden Modelltypen mit geteilten Berechtigungen an:

  - **Geteilte RBAC-Berechtigungen**   Berechtigungen zur Erstellung von Sicherheitsprinzipalen in der Active Directory-Domänenpartition werden von der rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) gesteuert. Nur Mitglieder der entsprechenden Rollengruppen können Sicherheitsprinzipale erstellen.

  - **Geteilte Active Directory-Berechtigungen**   Die Berechtigungen zum Erstellen von Sicherheitsprinzipalen in der Active Directory-Domänenpartition werden von allen Exchange-Benutzern, -Diensten und -Servern vollständig entfernt. In RBAC wird keine Option zur Erstellung von Sicherheitsprinzipalen bereitgestellt. Die Erstellung von Sicherheitsprinzipalen in Active Directory muss mithilfe von Active Directory-Verwaltungstools durchgeführt werden.
    

    > [!NOTE]
    > Geteilte Active Directory-Berechtigungen stehen in Organisationen zur Verfügung, in denen Microsoft Exchange Server 2010 Service Pack 1 (SP1) oder höher, Exchange 2013 oder beide Versionen von Exchange ausgeführt werden.



Das von Ihnen ausgewählte Modell hängt von der Struktur und den Anforderungen der Organisation ab. Wählen Sie das Verfahren aus, das auf das zu konfigurierende Modell zutrifft. Es wird empfohlen, dass Sie das geteilte RBAC-Berechtigungsmodell verwenden. Das geteilte RBAC-Berechtigungsmodell stellt wesentlich mehr Flexibilität sowie dieselbe Administrationstrennung wie geteilte Active Directory-Berechtigungen bereit.

Weitere Informationen zu Freigabe- und geteilten Berechtigungen finden Sie unter [Grundlegendes zu geteilten Berechtigungen](understanding-split-permissions-exchange-2013-help.md).

Weitere Informationen zum Verwalten von Rollengruppen, Verwaltungsrollen sowie regulären und delegierenden Verwaltungsrollenzuweisungen finden Sie in den folgenden Themen:

  - [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Berechtigungen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Geteilte Active Directory-Berechtigungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen die Windows PowerShell, die Windows Command Shell oder beide verwenden, um diese Verfahren durchzuführen. Weitere Informationen finden Sie unter den jeweiligen Verfahren.

  - Wenn in Ihrer Organisation Exchange 2010-Server vorhanden sind, wird das von Ihnen ausgewählte Berechtigungsmodell auch auf diese Server angewendet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Wechsel zu geteilten RBAC-Berechtigungen

Sie können Ihre Exchange 2013-Organisation für geteilte RBAC-Berechtigungen konfigurieren. Anschließend können nur Active Directory-Administratoren Active Directory-Sicherheitsprinzipale erstellen. Dies bedeutet, dass Exchange-Administratoren die folgenden Cmdlets nicht verwenden können:

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

Exchange-Administratoren können lediglich die Exchange-Attribute für bereits vorhandene Active Directory-Sicherheitsprinzipale verwalten. Sie können jedoch Exchange-spezifische Objekte wie Transportregeln und Verteilergruppen erstellen und verwalten. Weitere Informationen finden Sie im Abschnitt "Geteilte RBAC-Berechtigungen" unter [Grundlegendes zu geteilten Berechtigungen](understanding-split-permissions-exchange-2013-help.md).

Um Exchange 2013 für geteilte Berechtigungen zu konfigurieren, müssen Sie die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" einer Rollengruppe mit Mitgliedern zuordnen, bei denen es sich um Active Directory-Administratoren handelt. Anschließend müssen Sie die Zuweisungen zwischen diesen Rollen und allen Rollengruppen oder universellen Sicherheitsgruppen entfernen, die Exchange-Administratoren enthalten.

So konfigurieren Sie geteilte RBAC-Berechtigungen:

1.  Wenn Ihre Organisation derzeit für geteilte Active Directory-Berechtigungen konfiguriert ist, gehen Sie an einer Eingabeaufforderung der Windows-Verwaltungsshell folgendermaßen vor.
    
    1.  Deaktivieren Sie geteilte Active Directory-Berechtigungen, indem Sie von dem Exchange 2013-Installationsmedium aus den folgenden Befehl ausführen.
        
            setup.exe /PrepareAD /ActiveDirectorySplitPermissions:false
    
    2.  Starten Sie die Exchange 2013-Server in Ihrer Organisation neu, oder warten Sie, bis das Active Directory-Zugriffstoken alle Exchange 2013-Server repliziert hat.
        

        > [!NOTE]
        > Wenn in Ihrer Organisation Exchange 2010-Server vorhanden sind, müssen Sie diese Server auch neu starten.



2.  Führen Sie Folgendes an der Exchange-Verwaltungsshell aus:
    
    1.  Erstellen Sie eine Rollengruppe für die Active Directory-Administratoren. Neben der Rollengruppe werden mit dem Befehl auch die regulären Rollenzuweisungen zwischen der neuen Rollengruppe und der Rolle "Erstellung von E-Mail-Empfängern" und der Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" erstellt.
        
            New-RoleGroup "Active Directory Administrators" -Roles "Mail Recipient Creation", "Security Group Creation and Membership"
        

        > [!NOTE]
        > Wenn Sie möchten, dass Mitglieder dieser Rollengruppe Rollenzuweisungen erstellen können, müssen Sie die Rolle "Rollenverwaltung" einschließen. Sie müssen diese Rolle nicht zu diesem Zeitpunkt hinzufügen. Wenn Sie jedoch zu einem späteren Zeitpunkt die Rollen "Erstellung von E-Mail-Empfängern" oder "Sicherheitsgruppenerstellung und -mitgliedschaft" zu anderen Rollenempfängern zuweisen möchten, müssen Sie die Rolle "Rollenverwaltung" dieser neuen Rollengruppe zuweisen. Mithilfe der folgenden Schritte wird die Rollengruppe "Active Directory-Administratoren" als einzige Rollengruppe konfiguriert, die diese Rolle delegieren kann.

    
    2.  Erstellen Sie delegierende Rollenzuweisungen zwischen der neuen Rollengruppe und den Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft", indem Sie die folgenden Befehle verwenden.
        
            New-ManagementRoleAssignment -Role "Mail Recipient Creation" -SecurityGroup "Active Directory Administrators" -Delegating
            New-ManagementRoleAssignment -Role "Security Group Creation and Membership" -SecurityGroup "Active Directory Administrators" -Delegating
    
    3.  Fügen Sie der neuen Rollengruppe Mitglieder hinzu, indem Sie den folgenden Befehl verwenden.
        
            Add-RoleGroupMember "Active Directory Administrators" -Member <user to add>
    
    4.  Ersetzen Sie die Stellvertreterliste für die neue Rollengruppe, sodass nur Mitglieder der Rollengruppe Mitglieder hinzufügen oder entfernen können.
        
            Set-RoleGroup "Active Directory Administrators" -ManagedBy "Active Directory Administrators"
        

        > [!IMPORTANT]
        > Mitglieder der Rollengruppe Organisationsverwaltung oder Mitglieder, denen die Rolle "Rollenverwaltung" direkt oder über eine andere Rollengruppe oder universelle Sicherheitsgruppe zugewiesen wurde, können diese Sicherheitsprüfung für Stellvertreter umgehen. Wenn Sie verhindern möchten, dass sich ein Exchange-Administrator der neuen Rollengruppe selbst hinzufügt, müssen Sie die Rollenzuweisung zwischen der Rolle "Rollenverwaltung" und allen Exchange-Administratoren entfernen und diese einer anderen Rollengruppe zuordnen.

    
    5.  Ermitteln Sie alle regulären und delegierenden Rollenzuweisungen zur Rolle "Erstellung von E-Mail-Empfängern", indem Sie den folgenden Befehl verwenden. Der Befehl zeigt nur die Eigenschaften **Name**, **Role** und **RoleAssigneeName** an.
        
            Get-ManagementRoleAssignment -Role "Mail Recipient Creation" | Format-Table Name, Role, RoleAssigneeName -Auto
    
    6.  Entfernen Sie mit dem folgenden Befehl alle regulären und delegierenden Rollenzuweisungen zur Rolle "Erstellung von E-Mail-Empfängern", die nicht der neuen Rollengruppe oder anderen Rollengruppen, universellen Sicherheitsgruppen oder direkten Zuweisungen, die beibehalten werden sollen, zugeordnet sind.
        
            Remove-ManagementRoleAssignment <Mail Recipient Creation role assignment to remove>
        

        > [!NOTE]
        > Wenn Sie alle regulären und delegierenden Rollenzuweisungen der Rolle "Erstellung von E-Mail-Empfängern" oder jedes Rollenempfängers außer der Rollengruppe "Active Directory-Administratoren" entfernen möchten, verwenden Sie den folgenden Befehl. Die Option <EM>WhatIf</EM> zeigt die zu entfernenden Rollenzuweisungen an. Deaktivieren Sie die Option <EM>WhatIf</EM>, und führen Sie den Befehl erneut aus, um die Rollenzuweisungen zu entfernen.

        
            Get-ManagementRoleAssignment -Role "Mail Recipient Creation" | Where { $_.RoleAssigneeName -NE "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf
    
    7.  Ermitteln Sie alle regulären und delegierenden Rollenzuweisungen zur Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft", indem Sie den folgenden Befehl verwenden. Der Befehl zeigt nur die Eigenschaften **Name**, **Role** und **RoleAssigneeName** an.
        
            Get-ManagementRoleAssignment -Role "Security Group Creation and Membership" | Format-Table Name, Role, RoleAssigneeName -Auto
    
    8.  Entfernen Sie mit dem folgenden Befehl alle regulären und delegierenden Rollenzuweisungen zur Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft", die nicht der neuen Rollengruppe oder anderen Rollengruppen, universellen Sicherheitsgruppen oder direkten Zuweisungen, die beibehalten werden sollen, zugeordnet sind.
        
            Remove-ManagementRoleAssignment <Security Group Creation and Membership role assignment to remove>
        

        > [!NOTE]
        > Sie können denselben Befehl in der vorangehenden Anmerkung verwenden, um alle regulären und delegierenden Rollenzuweisungen zur Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" oder jedem Rollenempfänger außer der Rollengruppe "Active Directory-Administratoren" zu entfernen, wie in diesem Beispiel beschrieben.

        
            Get-ManagementRoleAssignment -Role "Security Group Creation and Membership" | Where { $_.RoleAssigneeName -NE "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\))

  - [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\))

  - [Add-RoleGroupMember](https://technet.microsoft.com/de-de/library/dd638207\(v=exchg.150\))

  - [Set-RoleGroup](https://technet.microsoft.com/de-de/library/dd638182\(v=exchg.150\))

  - [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\))

  - [Remove-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351205\(v=exchg.150\))

## Wechsel der geteilten Active Directory-Berechtigungen

Sie können Ihre Exchange 2013-Organisation für geteilte Active Directory-Berechtigungen konfigurieren. Geteilte Active Directory-Berechtigungen entfernen alle Berechtigungen vollständig, die zulassen, dass Exchange-Administratoren und -Server Sicherheitsprinzipale in Active Directory erstellen oder Nicht-Exchange-Attribute auf diesen Objekten ändern. Anschließend können nur Active Directory-Administratoren Active Directory-Sicherheitsprinzipale erstellen. Dies bedeutet, dass Exchange-Administratoren die folgenden Cmdlets nicht verwenden können:

  - **Add-DistributionGroupMember**

  - **New-DistributionGroup**

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-DistributionGroup**

  - **Remove-DistributionGroupMember**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

  - **Update-DistributionGroupMember**

Exchange-Administratoren und -Server können lediglich die Exchange-Attribute für bereits vorhandene Active Directory-Sicherheitsprinzipale verwalten. Sie können jedoch Exchange-spezifische Objekte wie Transportregeln und Unified Messaging-Wählpläne erstellen und verwalten.


> [!WARNING]
> Nach der Aktivierung von geteilten Active Directory-Berechtigungen können Exchange-Administratoren und -Server keine Sicherheitsprinzipale in Active Directory mehr erstellen und keine Mitgliedschaft in Verteilergruppen verwalten. Diese Aufgaben müssen mithilfe der Active Directory-Verwaltungstools mit den erforderlichen Active Directory-Berechtigungen durchgeführt werden. Vor dieser Änderung sollten Sie sich über die Auswirkungen bewusst sein, die sie auf Ihre Verwaltungsprozesse und Anwendungen von Drittanbietern, die im Exchange 2013- und RBAC-Berechtigungsmodell haben werden.<BR>Weitere Informationen finden Sie im Abschnitt "Geteilte Active Directory-Berechtigungen" unter <A href="understanding-split-permissions-exchange-2013-help.md">Grundlegendes zu geteilten Berechtigungen</A>.



So wechseln Sie von geteilten RBAC-Berechtigungen zu geteilten Active Directory-Berechtigungen:

1.  Führen Sie über eine Windows-Befehlsshell den folgendem Befehl auf dem Exchange 2013-Installationsmedium aus, um geteilte Active Directory-Berechtigungen zu aktivieren.
    
        setup.exe /PrepareAD /ActiveDirectorySplitPermissions:true

2.  Wenn Ihre Organisation mehrere Active Directory-Domänen umfasst, müssen Sie entweder `setup.exe /PrepareDomain` in jeder untergeordneten Domäne mit Exchange-Servern oder -Objekten ausführen oder `setup.exe /PrepareAllDomains` über einen Standort mit einem Active Directory-Server aus jeder Domäne ausführen.

3.  Starten Sie die Exchange 2013-Server in Ihrer Organisation neu, oder warten Sie, bis das Active Directory-Zugriffstoken alle Exchange 2013-Server repliziert hat.
    

    > [!NOTE]
    > Wenn in Ihrer Organisation Exchange 2010-Server vorhanden sind, müssen Sie diese Server auch neu starten.


