---
title: 'Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen: Exchange 2013 Help'
TOCTitle: Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen
ms:assetid: 7d119977-b420-4b66-acf0-0a978b188cdd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638146(v=EXCHG.150)
ms:contentKeyID: 50476101
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Mithilfe von gemeinsamen Berechtigungen können Sie als Administrator von Microsoft Exchange Server 2013Active Directory-Sicherheitsprinzipale (beispielsweise Benutzer) erstellen und diese als Exchange-Empfänger konfigurieren. Anders als bei geteilten Berechtigungen, bei denen Verwaltungsaufgaben zwischen den Gruppen der Exchange-Administratoren und der Active Directory-Administratoren aufgeteilt sind, gibt es bei gemeinsamen Berechtigungen keine Aufgabenteilung.

Weitere Informationen zu gemeinsamen und geteilten Berechtigungen finden Sie unter [Grundlegendes zu geteilten Berechtigungen](understanding-split-permissions-exchange-2013-help.md).

Sie können für Ihre Exchange 2013-Organisation gemeinsame Berechtigungen konfigurieren, sofern Sie zuvor geteilte Berechtigungen verwendet haben. Das Verfahren zum Wechsel zu gemeinsamen Berechtigungen unterscheidet sich in Abhängigkeit davon, ob Sie aktuell geteilte Berechtigungen der rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) oder geteilte Active Directory-Berechtigungen verwenden. Wählen Sie das Verfahren aus den folgenden aus, das auf Ihre aktuelle Konfiguration anwendbar ist. Wenn Folgendes zutrifft, verwendet Ihr Unternehmen geteilte Active Directory-Berechtigungen:

  - Die Microsoft Exchange-Organisationseinheit "Geschützte Gruppen" ist vorhanden.

  - Die Sicherheitsgruppe "Exchange Windows Permissions" befindet sich in der Microsoft Exchange-Organisationseinheit "Geschützte Gruppen".

  - Die Sicherheitsgruppe "Exchange Trusted Subsystem" ist Mitglied der Sicherheitsgruppe "Exchange Windows Permissions".

  - Es gibt keine regulären Verwaltungsrollenzuordnungen zur Rolle "Erstellung von E-Mail-Empfängern" oder "Sicherheitsgruppenerstellung und -mitgliedschaft".

Falls für Ihre Organisation niemals geteilte Berechtigungen konfiguriert waren, müssen Sie dieses Verfahren nicht ausführen. Exchange 2013 wird standardmäßig mit gemeinsamen Berechtigungen konfiguriert.

Weitere Informationen zum Verwalten von Rollengruppen, Verwaltungsrollen sowie regulären und delegierenden Verwaltungsrollenzuweisungen finden Sie in den folgenden Themen:

  - [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Berechtigungen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Sie müssen die Windows PowerShell, die Windows Command Shell oder beide verwenden, um diese Verfahren durchzuführen. Weitere Informationen finden Sie unter den jeweiligen Verfahren.

  - Die Exchange 2013-Organisation muss aktuell für die rollenbasierte Zugriffssteuerung (RBAC) oder für geteilte Active Directory-Berechtigungen konfiguriert sein.

  - Wenn in Ihrer Organisation Exchange Server 2010-Server vorhanden sind, wird das Berechtigungsmodell, das Sie auswählen, auch auf diese Server angewendet.

  - Sie benötigen die Berechtigungen zum Delegieren der Verwaltungsrollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" an die Verwaltungsrollengruppe Organisationsverwaltung oder an eine andere Rollengruppe, der die Rolle "E-Mail-Empfänger" zugewiesen ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Wechseln von geteilten RBAC-Berechtigungen zu gemeinsamen Berechtigungen

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

Zum Wechseln von geteilten RBAC-Berechtigungen zu gemeinsamen Exchange 2013-Berechtigungen müssen die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" einer Rollengruppe zugewiesen werden, der auch die Rolle "E-Mail-Empfänger" zugewiesen ist und in der Exchange 2013-Administratoren Mitglied sind. In der standardmäßigen Konfiguration mit gemeinsamen Berechtigungen sind alle diese Rollen in der Rollengruppe Organisationsverwaltung enthalten. Daher wird in diesem Verfahren die Rollengruppe Organisationsverwaltung verwendet.

## Konfigurieren von gemeinsamen Berechtigungen

Führen Sie zum Konfigurieren von gemeinsamen Berechtigungen in der Rollengruppe Organisationsverwaltung die folgenden Schritte unter Verwendung eines Kontos aus, das über Berechtigungen zum Delegieren von Rollenzuweisungen für die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" verfügt:

1.  Fügen Sie mithilfe der folgenden Befehle eine delegierende Rollenzuweisung für die Rolle "Erstellung von E-Mail-Empfängern" und die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" zur Organisationsverwaltung-Rollengruppe hinzu.
    
        New-ManagementRoleAssignment -Role "Mail Recipient Creation" -SecurityGroup "Organization Management" -Delegating
        New-ManagementRoleAssignment -Role "Security Group Creation and Membership" -SecurityGroup "Organization Management" -Delegating
    

    > [!NOTE]
    > Der Rollengruppe (in diesem Verfahren die Rollengruppe "Active Directory-Administratoren"), die über delegierende Rollenzuweisungen für die Rolle "Erstellung von E-Mail-Empfängern" und für die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" verfügt, muss die Rolle "Rollenverwaltung" zugeordnet werden, um das Cmdlet <STRONG>New-ManagementRoleAssignment</STRONG> auszuführen. Der Rollenempfänger, der die Rolle "Rollenverwaltung" delegieren kann, muss diese Rolle der Rollengruppe "Active Directory-Administratoren" zuweisen.



2.  Fügen Sie mit den folgenden Befehlen den Rollengruppen Organisationsverwaltung und Empfängerverwaltung reguläre Rollenzuweisungen für die Rolle "Erstellung von E-Mail-Empfängern" hinzu.
    
        New-ManagementRoleAssignment -Role "Mail Recipient Creation" -SecurityGroup "Organization Management"
        New-ManagementRoleAssignment -Role "Security Group Creation and Membership" -SecurityGroup "Recipient Management"

3.  Fügen Sie mit dem folgenden Befehl der Rollengruppe Organisationsverwaltung eine reguläre Rollenzuweisung für die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" hinzu.
    
        New-ManagementRoleAssignment -Role "Security Group Creation and Membership" -SecurityGroup "Organization Management"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Entfernen von Berechtigungen von Active Directory-Administratoren (optional)

Sie können optional die Berechtigungen von Active Directory-Administratoren entfernen, falls diese nicht mehr Active Directory-Objekte mithilfe der Exchange-Verwaltungstools erstellen oder verwalten sollen. Wenn Sie Berechtigungen von Active Directory-Administratoren entfernen möchten, führen Sie dieses Verfahren durch.


> [!NOTE]
> Sie können zwar die Berechtigungen von Active Directory-Administratoren zum Verwalten von Active Directory-Objekten mithilfe der Exchange-Verwaltungstools entfernen. Allerdings können die Active Directory-Administratoren weiterhin Active Directory-Objekte mithilfe der Active Directory-Verwaltungstools verwalten, sofern ihre Active Directory-Berechtigungen dies ermöglichen. Sie sind jedoch nicht in der Lage, Exchange-spezifische Attribute für Active Directory-Objekte zu verwalten. Weitere Informationen finden Sie unter <A href="understanding-split-permissions-exchange-2013-help.md">Grundlegendes zu geteilten Berechtigungen</A>.



Gehen Sie zum Entfernen von Exchange-bezogenen geteilten Berechtigungen von Active Directory-Administratoren folgendermaßen vor:

1.  Entfernen Sie mit dem folgenden Befehl die regulären und delegierenden Rollenzuweisungen, die die Rolle "Erstellung von E-Mail-Empfängern" der Rollengruppe oder der universellen Sicherheitsgruppe (Universal Security Group, USG) zuweisen, in der die Active Directory-Administratoren Mitglied sind. In diesem Befehl wird die Rollengruppe "Active Directory-Administratoren" als Beispiel verwendet. Mithilfe der Option *WhatIf* können Sie anzeigen, welche Rollenzuweisungen entfernt werden. Entfernen Sie die Option *WhatIf*, und führen Sie den Befehl dann erneut aus, um die Rollenzuweisungen zu entfernen.
    
        Get-ManagementRoleAssignment -Role "Mail Recipient Creation" | Where { $_.RoleAssigneeName -EQ "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf

2.  Entfernen Sie mit dem folgenden Befehl die regulären und delegierenden Rollenzuweisungen, die die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" der Rollengruppe oder der USG zuweisen, in der die Active Directory-Administratoren Mitglied sind. In diesem Befehl wird die Rollengruppe "Active Directory-Administratoren" als Beispiel verwendet. Mithilfe der Option *WhatIf* können Sie anzeigen, welche Rollenzuweisungen entfernt werden. Entfernen Sie die Option *WhatIf*, und führen Sie den Befehl dann erneut aus, um die Rollenzuweisungen zu entfernen.
    
        Get-ManagementRoleAssignment -Role "Security Group Creation and Membership" | Where { $_.RoleAssigneeName -EQ "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf

3.  Optional. Falls Sie alle Exchange-Berechtigungen der Active Directory-Administratoren entfernen möchten, können Sie die Rollengruppe oder USG entfernen, in der diese Mitglied sind. Weitere Informationen zum Entfernen einer Rollengruppe finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)) oder [Remove-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351205\(v=exchg.150\)).

## Wechseln von geteilten Active Directory-Berechtigungen zu gemeinsamen Berechtigungen

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Geteilte Active Directory-Berechtigungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

Für den Wechsel von geteilten Active Directory-Berechtigungen zu gemeinsamen Exchange 2013-Berechtigungen, müssen Sie das Exchange-Setup erneut ausführen, um geteilte Active Directory-Berechtigungen in der Exchange-Organisation zu deaktivieren. Erstellen Sie dann Rollenzuweisungen zwischen einer Rollengruppe und den Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft". In der standardmäßigen Konfiguration mit gemeinsamen Berechtigungen sind alle diese Rollen in der Rollengruppe Organisationsverwaltung enthalten. Daher wird in diesem Verfahren die Rollengruppe Organisationsverwaltung verwendet.


> [!IMPORTANT]
> Der Befehl "setup.com" in diesem Verfahren nimmt Änderungen an Active Directory vor. Sie müssen ein Konto verwenden, das über Berechtigungen verfügt, die zur Durchführung dieser Änderungen erforderlich sind. Bei diesem Konto handelt es sich möglicherweise nicht um dasselbe Konto, das über Berechtigungen zum Erstellen von Rollenzuweisungen mithilfe des Cmdlets <STRONG>New-ManagementRoleAssignment</STRONG>&nbsp;verfügt. Verwenden Sie das Konto bzw. die Konten mit den erforderlichen Berechtigungen, um die einzelnen Schritte dieses Verfahrens erfolgreich auszuführen.



Gehen Sie wie folgt vor, um von geteilten Active Directory-Berechtigungen zu gemeinsamen Berechtigungen zu wechseln:

1.  Führen Sie über eine Windows-Befehlsshell den folgendem Befehl auf dem Exchange 2013-Installationsmedium aus, um geteilte Active Directory-Berechtigungen zu deaktivieren.
    
        setup.exe /PrepareAD /ActiveDirectorySplitPermissions:false

2.  Führen Sie über die Exchange-Verwaltungsshell die folgenden Befehle aus, um reguläre Rollenzuweisungen zwischen der Rolle "Erstellung von E-Mail-Empfängern" und der Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" sowie den Rollengruppen Organisationsverwaltung und Empfängerverwaltung hinzuzufügen.
    
        New-ManagementRoleAssignment "Mail Recipient Creation_Organization Management" -Role "Mail Recipient Creation" -SecurityGroup "Organization Management"
        New-ManagementRoleAssignment "Security Group Creation and Membership_Org Management" -Role "Security Group Creation and Membership" -SecurityGroup "Organization Management"
        New-ManagementRoleAssignment "Mail Recipient Creation_Recipient Management" -Role "Mail Recipient Creation" -SecurityGroup "Recipient Management"

3.  Starten Sie die Exchange 2013-Server im Unternehmen neu.
    

    > [!NOTE]
    > Wenn in Ihrer Organisation Exchange 2010-Server vorhanden sind, müssen Sie diese Server auch neu starten.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

