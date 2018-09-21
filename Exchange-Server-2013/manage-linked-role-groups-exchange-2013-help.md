---
title: 'Verwalten von verknüpften Rollengruppen: Exchange 2013 Help'
TOCTitle: Verwalten von verknüpften Rollengruppen
ms:assetid: e2a07395-90c2-4d62-b15d-ac3ff28fe786
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657502(v=EXCHG.150)
ms:contentKeyID: 50476942
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von verknüpften Rollengruppen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-09_

Sie können mit einer verknüpften Verwaltungsrollengruppe Mitglieder einer universellen Sicherheitsgruppe (USG) in einer fremden Active Directory-Gesamtstruktur dazu ermächtigen, eine Microsoft Exchange Server 2013-Organisation in einer Active Directory-Ressourcenstruktur zu verwalten. Wenn Sie eine universelle Sicherheitsgruppe in einer fremden Gesamtstruktur einer verknüpften Rollengruppe zuordnen, werden den Mitgliedern der Sicherheitsgruppe die Berechtigungen der Verwaltungsrollen gewährt, die der verknüpften Rollengruppe zugewiesen sind. Weitere Informationen zu verknüpften Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Mithilfe der Cmdlets **New-RoleGroup** und **Set-RoleGroup** können Sie verknüpfte Verwaltungsrollengruppen erstellen und konfigurieren. Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\))

  - [Set-RoleGroup](https://technet.microsoft.com/de-de/library/dd638182\(v=exchg.150\))

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Rollengruppen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 bis 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Verknüpfte Rollengruppen können nicht mithilfe der Exchange-Verwaltungskonsole erstellt oder konfiguriert werden. Sie müssen die Exchange-Verwaltungsshell verwenden.

  - Mindestvoraussetzung für die Konfiguration einer verknüpften Rollengruppe ist die Einrichtung einer unidirektionalen Vertrauensstellung zwischen der Active Directory-Ressourcengesamtstruktur, in der sich die verknüpfte Rollengruppe befinden soll, und der fremden Active Directory-Gesamtstruktur, in der sich die Benutzer bzw. die universellen Sicherheitsgruppen befinden. Zwischen der Ressourcengesamtstruktur und der fremden Gesamtstruktur muss eine Vertrauensstellung bestehen.

  - Sie müssen über die folgenden Informationen zur fremden Active Directory-Gesamtstruktur verfügen:
    
      - **Anmeldeinformationen**   Sie müssen über einen Benutzernamen und ein Kennwort verfügen, die den Zugriff auf die fremde Active Directory-Gesamtstruktur ermöglichen. Diese Informationen werden mit dem Parameter *LinkedCredential* der Cmdlets **New-RoleGroup** und **Set-RoleGroup** verwendet.
    
      - **Domänencontroller**   Sie müssen über den vollqualifizierten Domänennamen (FQDN) eines Active Directory-Domänencontrollers in der fremden Active Directory-Gesamtstruktur verfügen. Diese Informationen werden mit dem Parameter *LinkedDomainController* der Cmdlets **New-RoleGroup** und **Set-RoleGroup** verwendet.
    
      - **Fremde universelle Sicherheitsgruppe**   Sie müssen über den vollständigen Namen einer universellen Sicherheitsgruppe in der fremden Active Directory-Gesamtstruktur verfügen, die die Mitglieder enthält, die Sie der verknüpften Rollengruppe zuordnen möchten. Diese Informationen werden mit dem Parameter *LinkedForeignGroup* der Cmdlets **New-RoleGroup** und **Set-RoleGroup** verwendet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer verknüpften Rollengruppe

## Erstellen einer verknüpften Rollengruppe ohne Bereich mithilfe der Shell

Gehen Sie zum Erstellen einer verknüpften Rollengruppe und zum Zuordnen von Verwaltungsrollen folgendermaßen vor:

1.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen.
    
    ```powershell
$ForeignCredential = Get-Credential
```

2.  Erstellen Sie die verknüpfte Rollengruppe mit folgender Syntax.
    
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles <role1, role2, role3...>

3.  Fügen Sie mit Active Directory-Benutzer und -Computer auf einem Computer in der fremden Active Directory-Gesamtstruktur Mitglieder der fremden universellen Sicherheitsgruppe hinzu, oder entfernen Sie sie daraus.

In diesem Beispiel werden folgende Schritte ausgeführt:

  - Ruft die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur "users.contoso.com" ab. Mit diesen Anmeldeinformationen wird eine Verbindung mit dem Domänencontroller "DC01.users.contoso.com" in der fremden Gesamtstruktur hergestellt.

  - Erstellen der verknüpften Rollengruppe "Compliance Role Group" in der Ressourcengesamtstruktur, in der Exchange 2013 installiert ist.

  - Verknüpfen der neuen Rollengruppe mit der universellen Sicherheitsgruppe (USG) "Compliance Administrators" in der fremden Active Directory-Gesamtstruktur "users.contoso.com".

  - Zuordnen von Transportregeln und Journalverwaltungsrollen zu der neuen verknüpften Rollengruppe.

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
    New-RoleGroup "Compliance Role Group" -LinkedForeignGroup "Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles "Transport Rules", "Journaling"

## Erstellen einer verknüpften Rollengruppe mit einem benutzerdefinierten Verwaltungsbereich mithilfe der Shell

Sie können verknüpfte Rollengruppen mit benutzerdefinierten Empfängerverwaltungsbereichen und/oder benutzerdefinierten Konfigurationsverwaltungsbereichen erstellen. Gehen Sie zum Erstellen einer verknüpften Rollengruppe und zum Zuordnen von Verwaltungsrollen mit benutzerdefinierten Bereichen folgendermaßen vor:

1.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen.
    
    ```powershell
$ForeignCredential = Get-Credential
```

2.  Erstellen Sie die verknüpfte Rollengruppe mit folgender Syntax.
    
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -CustomConfigWriteScope <name of configuration scope> -CustomRecipientWriteScope <name of recipient scope> -LinkedCredential $ForeignCredential -Roles <role1, role2, role3...>

3.  Fügen Sie mit Active Directory-Benutzer und -Computer auf einem Computer in der fremden Active Directory-Gesamtstruktur Mitglieder der fremden universellen Sicherheitsgruppe hinzu, oder entfernen Sie sie daraus.

In diesem Beispiel werden folgende Schritte ausgeführt:

  - Ruft die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur "users.contoso.com" ab. Mit diesen Anmeldeinformationen wird eine Verbindung mit dem Domänencontroller "DC01.users.contoso.com" in der fremden Gesamtstruktur hergestellt.

  - Erstellen einer verknüpften Rollengruppe namens "Seattle Compliance Role Group" in der Ressourcengesamtstruktur, in der Exchange 2013 installiert ist.

  - Verknüpfen der neuen Rollengruppe mit der universellen Sicherheitsgruppe (USG) "Seattle Compliance Administrators" in der fremden Active Directory-Gesamtstruktur "users.contoso.com".

  - Zuordnen von Transportregeln und Journalverwaltungsrollen zu der neuen verknüpften Rollengruppe mit dem benutzerdefinierten Empfängerbereich "Seattle Recipients".

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
    New-RoleGroup "Seattle Compliance Role Group" -LinkedForeignGroup "Seattle Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -CustomRecipientWriteScope "Seattle Recipients" -Roles "Transport Rules", "Journaling"

Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

## Erstellen einer verknüpften Rollengruppe mit einem Organisationseinheitenbereich mithilfe der Shell

Sie können verknüpfte Rollengruppen erstellen, die einen Organisationseinheitenempfängerbereich verwenden. Gehen Sie zum Erstellen einer verknüpften Rollengruppe und zum Zuordnen von Verwaltungsrollen mit einem Organisationseinheitenbereich folgendermaßen vor:

1.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen.
    
    ```powershell
$ForeignCredential = Get-Credential
```

2.  Erstellen Sie die verknüpfte Rollengruppe mit folgender Syntax.
    
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -RecipientOrganizationalUnitScope <OU name> -Roles <role1, role2, role3...>

3.  Fügen Sie mit Active Directory-Benutzer und -Computer auf einem Computer in der fremden Active Directory-Gesamtstruktur Mitglieder der fremden universellen Sicherheitsgruppe hinzu, oder entfernen Sie sie daraus.

In diesem Beispiel werden folgende Schritte ausgeführt:

  - Ruft die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur "users.contoso.com" ab. Mit diesen Anmeldeinformationen wird eine Verbindung mit dem Domänencontroller "DC01.users.contoso.com" in der fremden Gesamtstruktur hergestellt.

  - Erstellen der verknüpften Rollengruppe "Executives Compliance Role Group" in der Ressourcengesamtstruktur, in der Exchange 2013 installiert ist.

  - Verknüpfen der neuen Rollengruppe mit der universellen Sicherheitsgruppe (USG) "Executives Compliance Administrators" in der fremden Active Directory-Gesamtstruktur "users.contoso.com".

  - Zuordnen von Transportregeln und Journalverwaltungsrollen zu der neuen verknüpften Rollengruppe mit dem Organisationseinheitenempfängerbereich "Executives OU".

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
    New-RoleGroup "Executives Compliance Role Group" -LinkedForeignGroup "Executives Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -RecipientOrganizationalUnitScope "Executives OU" -Roles "Transport Rules", "Journaling"

Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

## Ändern der fremden universellen Sicherheitsgruppe (USG) für eine verknüpfte Rollengruppe

## Ändern der fremden universellen Sicherheitsgruppe für eine verknüpfte Rollengruppe mithilfe der Shell

Gehen Sie zum Ändern der fremden universellen Sicherheitsgruppe für eine verknüpfte Rollengruppe folgendermaßen vor:

1.  Speichern Sie die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur in einer Variablen.
    
    ```powershell
$ForeignCredential = Get-Credential
```

2.  Ändern Sie die fremde universelle Sicherheitsgruppe für die vorhandene verknüpfte Rollengruppe mithilfe der folgenden Syntax.
    
        Set-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential 

In diesem Beispiel werden folgende Schritte ausgeführt:

  - Ruft die Anmeldeinformationen für die fremde Active Directory-Gesamtstruktur "users.contoso.com" ab. Mit diesen Anmeldeinformationen wird eine Verbindung mit dem Domänencontroller "DC01.users.contoso.com" in der fremden Gesamtstruktur hergestellt.

  - Ändern der fremden universellen Sicherheitsgruppe für die Rollengruppe "Compliance Role Group" in "Regulatory Compliance Officers".

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
    Set-RoleGroup "Compliance Role Group" -LinkedForeignGroup "Regulatory Compliance Officers" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential

