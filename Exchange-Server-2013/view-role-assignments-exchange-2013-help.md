---
title: 'Anzeigen von Rollenzuweisungen: Exchange 2013 Help'
TOCTitle: Anzeigen von Rollenzuweisungen
ms:assetid: 0be4def9-af6d-476a-9c97-7155ae11b587
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335086(v=EXCHG.150)
ms:contentKeyID: 50475001
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von Rollenzuweisungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungsrollenzuweisungen weisen einem Rollenempfänger eine Verwaltungsrolle zu. Weitere Informationen zu Verwaltungsrollenzuweisungen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollenzuweisungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - In diesem Thema wird das Pipelining und das Cmdlet **Format-List** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:
    
      - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))
    
      - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen einer Liste aller Rollenzuweisungen

Sie können eine Liste aller in Ihrer Organisation konfigurierten Rollenzuweisungen anzeigen, indem Sie das Cmdlet **Get-ManagementRoleAssignment** ausführen. Um eine Liste von Rollenzuweisungen abzurufen, die mit einer angegebenen Teilzeichenfolge übereinstimmen, verwenden Sie Platzhalterzeichen (\*). In diesem Beispiel wird eine Liste aller Rollenzuweisungen abgerufen, die mit der Zeichenfolge "Tier 1" beginnen.

    Get-ManagementRoleAssignment "Tier 1*"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen der Details einer bestimmten Rollenzuweisung

Sie können die Details einer Rollenzuweisung anzeigen, indem Sie die Ergebnisse des Cmdlets **Get-ManagementRoleAssignment** an das Cmdlet **Format-List** umleiten. Verwenden Sie die folgende Syntax.

```powershell
Get-ManagementRoleAssignment <assignment name> | Format-List
```

In diesem Beispiel werden die Details der Rollenzuweisung "Help Desk Assignment" abgerufen.

```powershell
Get-ManagementRoleAssignment "Help Desk Assignment" | Format-List
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste von Rollenzuweisungen, die einem bestimmten Rollenempfänger zugewiesen sind

Verwenden Sie die folgende Syntax, um eine Liste der Rollenzuweisungen anzuzeigen, die einer Verwaltungsrollengruppe, Rolle oder Rollenzuweisungsrichtlinie oder einem Benutzer oder einer universellen Sicherheitsgruppe (Universal Security Group, USG) zugeordnet sind.

```powershell
Get-ManagementRoleAssignment -RoleAssignee <role assignee name>
```

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, die der Rollengruppe "Server Management" zugeordnet sind.

```powershell
Get-ManagementRoleAssignment -RoleAssignee "Server Management"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen von einer bestimmten Rolle zugeordneten Rollenzuweisungen

Jede Rolle kann über mehrere Rollenzuweisungen verfügen. Sie können das Cmdlet **Get-ManagementRoleAssigment** verwenden, um eine Liste der Rollenzuweisungen anzuzeigen, die einer angegebenen Rolle zugeordnet sind.

Verwenden Sie die folgende Syntax, um eine Liste der Rollenzuweisungen anzuzeigen, die einer angegebenen Rolle zugeordnet sind.

```powershell
Get-ManagementRoleAssignment -Role <role name>
```

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, die der Rolle "Mail Recipients" zugeordnet sind.

```powershell
Get-ManagementRoleAssignment -Role "Mail Recipients"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste von Rollenzuweisungen, die einen bestimmten vordefinierten Bereich verwenden

Verwenden Sie die folgende Syntax, um eine Liste der Rollenzuweisungen anzuzeigen, die einen bestimmten vordefinierten Bereich verwenden.

    Get-ManagementRoleAssignment -RecipientWriteScope < MyGAL | MyDistributionGroups | Organization | Self | CustomRecipientScope | ExecutiveRecipientScope >

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, die den vordefinierten Bereich "Organization" verwenden.

```powershell
Get-ManagementRoleAssignment -RecipientWriteScope Organization
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste von Rollenzuweisungen, deren Bereich eine bestimmte Organisationseinheit (Organizational Unit, OU) ist

Verwenden Sie die folgende Syntax, um eine Liste der Rollenzuweisungen anzuzeigen, deren Bereich eine bestimmte Organisationseinheit ist.

```powershell
Get-ManagementRoleAssignment -RecipientOrganizationalUnitScope <OU>
```

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, deren Bereich die OU "North America\\Engineering\\Users" in der Domäne "contoso.com" ist.

    Get-ManagementRoleAssignment -RecipientOrganizationalUnitScope "contoso.com/North America/Engineering/Users"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste von Zuweisungen, die einen bestimmten benutzerdefinierten Bereich verwenden

Um eine Liste der Rollenzuweisungen anzuzeigen, die einen bestimmten benutzerdefinierten Bereich verwenden, müssen Sie zuerst bestimmen, ob es sich bei dem Bereich um einen Empfängerbereich, einen Konfigurationsbereich, einen exklusiven Empfängerbereich oder einen exklusiven Konfigurationsbereich handelt. Jede Art von Bereich verwendet einen anderen Parameter für das Cmdlet **Get-ManagementRoleAssignment**. Die folgende Liste zeigt jeden Bereich und seine zugeordneten Parameter:

  - **Empfängerbereiche** *CustomRecipientWriteScope*

  - **Konfigurationsbereiche** *CustomConfigWriteScope*

  - **Exklusive Empfängerbereiche** *ExclusiveRecipientWriteScope*

  - **Exklusive Konfigurationsbereiche** *ExclusiveConfigWriteScope*

Die Syntax für jeden Parameter ist identisch. Geben Sie den Namen des Bereichs zusammen mit dem Parameter an, der dem Bereichstyp entspricht.

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, die den Empfängerbereich "Vancouver Recipients" verwenden.

```powershell
Get-ManagementRoleAssignment -CustomRecipientWriteScope "Vancouver Recipients"
```

In diesem Beispiel werden alle Rollenzuweisungen abgerufen, die den exklusiven Konfigurationsbereich "Seattle AD Site" verwenden.

```powershell
Get-ManagementRoleAssignment -ExclusiveConfigWriteScope "Seattle AD Site"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste exklusiver oder regulärer Bereiche

Verwenden Sie die folgende Syntax, um eine Liste exklusiver oder regulärer Rollenzuweisungen anzuzeigen.

```powershell
Get-ManagementRoleAssignment -Exclusive < $True | $False >
```

Führen Sie beispielsweise den folgenden Befehl aus, um eine Liste exklusiver Bereiche anzuzeigen:

```powershell
Get-ManagementRoleAssignment -Exclusive $True
```

Im folgenden Beispiel wird eine Liste regulärer Bereiche ohne exklusive Bereiche abgerufen.

```powershell
Get-ManagementRoleAssignment -Exclusive $False
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen der Rollenzuweisungen, die einen bestimmten Empfänger oder Server ändern können

Um eine Liste der Rollenzuweisungen anzuzeigen, die einen bestimmten Empfänger oder Server ändern können, verwenden Sie die Parameter *WritableRecipient* und *WritableServer*. Geben Sie den Namen des Empfängers im Parameter *WritableRecipient* und den Namen des Servers im Parameter *WritableServer* an.

In diesem Beispiel wird eine Liste von Rollenzuweisungen abgerufen, die den Empfänger "Brian" ändern können.

```powershell
Get-ManagementRoleAssignment -WritableRecipient "Brian"
```

Sie können die Parameter *WritableRecipient* und *WritableServer* mit anderen Parametern kombinieren, z. B. mit dem Parameter *RoleAssignee* und der Option *GetEffectiveUsers*, um Ihre Abfrage zu verfeinern und ggf. alle Rollengruppen oder USGs zu erweitern. In diesem Beispiel werden alle Benutzer abgerufen, die den Server "EX02" ändern können und die der Rollengruppe "Server Management" zugewiesen sind.

    Get-ManagementRoleAssignment -WritableServer EX02 -RoleAssignee "Server Management" -GetEffectiveUsers

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen der Benutzer, die Berechtigungen von einer Zuweisung über eine Rollengruppe oder USG erhalten

Verwenden Sie die folgende Syntax, um eine Liste der Benutzer anzuzeigen, die Berechtigungen von einer Rollenzuweisung erhalten.

```powershell
Get-ManagementRoleAssignment <assignment name> -GetEffectiveUsers
```

In diesem Beispiel wird eine Liste von Benutzern mit der Rollenzuweisung "Help Desk Assignment" abgerufen.

```powershell
Get-ManagementRoleAssignment "Help Desk Assignment" -GetEffectiveUsers
```

Außerdem können Sie die Option *GetEffectiveUsers* mit mehreren anderen Parametern für das Cmdlet **Get-ManagementRoleAssignment** kombinieren, um die Rollengruppen und USGs zu erweitern, denen die Rollenzuweisungen zugewiesen sind. Ein Beispiel für die Verwendung der Option *GetEffectiveUsers* mit anderen Parametern finden Sie unter "Anzeigen der Rollenzuweisungen, die einen bestimmten Empfänger oder Server ändern können" weiter oben in diesem Thema.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anzeigen einer Liste von Rollenzuweisungen, die aktiviert oder deaktiviert sind

Verwenden Sie die folgende Syntax, um eine Liste der Rollenzuweisungen anzuzeigen, die aktiviert oder deaktiviert sind.

```powershell
Get-ManagementRoleAssignment -Enabled < $True | $False >
```

In diesem Beispiel wird eine Liste der deaktivieren Rollenzuweisungen abgerufen.

```powershell
Get-ManagementRoleAssignment -Enabled $False
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

