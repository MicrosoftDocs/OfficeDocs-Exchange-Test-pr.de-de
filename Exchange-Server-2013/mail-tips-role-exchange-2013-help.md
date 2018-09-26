---
title: 'Rolle „E-Mail-Infos&quot;: Exchange 2013 Help'
TOCTitle: Rolle „E-Mail-Infos“
ms:assetid: 74495ded-6097-4f10-a829-c8ed81f5ba3e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876909(v=EXCHG.150)
ms:contentKeyID: 50476018
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Rolle „E-Mail-Infos\&quot;

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Verwaltungsrolle E-Mail-Infos ermöglicht Administratoren das Verwalten von E-Mail-Infos in einer Organisation.

Diese Verwaltungsrolle ist eine von mehreren integrierten Rollen im Modell für rollenbasierte Zugriffssteuerungsberechtigungen (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013. Verwaltungsrollen werden einer oder mehreren Verwaltungsrollengruppen, Zuweisungsrichtlinien für Verwaltungsrollen, Benutzern oder universellen Sicherheitsgruppen zugewiesen. Sie dienen als logische Gruppierung von Cmdlets oder Skripts, die zusammengefasst werden, um das Anzeigen oder Ändern der Konfiguration von Exchange 2013-Komponenten wie Postfachdatenbanken, Transportregeln und Empfängern zu ermöglichen. Wenn ein Cmdlet oder Skript und seine Parameter, die zusammen einen sogenannten Verwaltungsrolleneintrag bilden, in einer Rolle enthalten sind, können das Cmdlet bzw. Skript und seine Parameter von allen ausgeführt werden, denen die Rolle zugewiesen ist. Weitere Informationen zu Verwaltungsrollen und Verwaltungsrolleneinträgen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Weitere Informationen zu Verwaltungsrollen, Verwaltungsrollengruppen und anderen RBAC-Komponenten finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Verwaltungsrollenzuweisungen

Um über diese Rolle Berechtigungen erteilen zu können, muss sie einem Rollenempfänger zugewiesen werden. Dabei kann es sich um eine Rollengruppe, einen Benutzer oder eine universelle Sicherheitsgruppe handeln. Die Zuweisung erfolgt über Verwaltungsrollenzuweisungen. Rollenzuweisungen verknüpfen Rollenempfänger und Rollen miteinander. Werden einem Rollenempfänger mehrere Rollen zugewiesen, wird dem Rollenempfänger die Gesamtheit aller Berechtigungen erteilt, die durch alle zugewiesenen Rollen erteilt werden.

Neben der Link von Rollenempfängern mit Rollen können Rollenzuweisungen auch für benutzerdefinierte oder integrierte Verwaltungsbereiche gelten. Verwaltungsbereiche steuern, welche Empfänger-, Server- und Datenbankobjekte durch Rollenempfänger geändert werden können. Wenn diese Rolle einem Rollenempfänger zugewiesen wird, ein Verwaltungsbereich dem Rollenempfänger jedoch nur das Verwalten bestimmter Objekte auf der Basis eines definierten Bereichs erlaubt, kann der Rollenempfänger nur die Berechtigungen verwenden, die über diese Rolle für die jeweiligen Objekte erteilt werden. Die durch diese Rolle bereitgestellten Berechtigungen können nicht auf Objekte außerhalb des in der Rollenzuweisung definierten Bereichs angewendet werden. Weitere Informationen zu Rollenzuweisungen und Bereichen finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Diese Rolle wird standardmäßig einer oder mehreren Rollengruppen zugewiesen. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt "Standard-Verwaltungsrollenzuweisungen".

Verwenden Sie den folgenden Befehl, wenn Sie eine Liste der dieser Rolle zugewiesenen Rollengruppen, Benutzer oder universellen Sicherheitsgruppen anzeigen möchten.

```powershell
Get-ManagementRoleAssignment -Role "<role name>"
```

## Reguläre und delegierende Rollenzuweisungen

Diese Rolle kann Rollenempfängern mithilfe von regulären oder delegierenden Rollenzuweisungen zugewiesen werden. Reguläre Rollenzuweisungen erteilen die dem Rollenempfänger von der Rolle bereitgestellten Berechtigungen. Delegierende Rollenzuweisungen geben dem Rollenempfänger die Möglichkeit, die Rolle anderen Rollenempfängern zuzuweisen. Weitere Informationen zu regulären Rollenzuweisungen und delegierenden Rollenzuweisungen finden Sie unter Grundlegendes zu Verwaltungsrollenzuweisungen[Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

## Hinzufügen oder Entfernen von Rollenzuweisungen

Sie können ändern, welchen Rollenempfängern diese Rolle zugewiesen wird. Dadurch ändern Sie, an wen die entsprechenden Berechtigungen erteilt werden. Sie können diese Rolle anderen integrierten Rollengruppen zuweisen oder Rollengruppen erstellen und ihnen dann diese Rolle zuweisen. Sie können diese Rolle auch Benutzern oder universellen Sicherheitsgruppen zuweisen. Sie sollten die Zuweisung von Rollen an Benutzer und universelle Sicherheitsgruppen jedoch beschränken, da die Komplexität Ihres Berechtigungsmodells durch solche Zuweisungen stark zunehmen kann.

Um diese Rolle über eine delegierende Rollenzuweisung Rollenempfängern zuzuweisen, muss die ‏Rolle einer Rollengruppe (deren Mitglied Sie sind), Ihnen direkt oder einer universellen Sicherheitsgruppe (deren Mitglied Sie sind) zugewiesen werden. Weitere Informationen zum Delegieren von Rollenzuweisungen finden Sie im Abschnitt "Reguläre und delegierende Rollenzuweisungen".

Sie können diese Rolle auch aus integrierten Rollengruppen, selbst erstellten Rollengruppen, Benutzern und universellen Sicherheitsgruppen entfernen. Es muss jedoch stets mindestens eine delegierende Rollenzuweisung zwischen dieser Rolle und einer Rollengruppe oder universellen Sicherheitsgruppe bestehen. Die letzte delegierende Rollenzuweisung kann nicht gelöscht werden. Durch diese Einschränkung wird verhindert, dass Sie das System für sich selbst sperren.


> [!IMPORTANT]
> Es muss mindestens eine delegierende Rollenzuweisung zwischen dieser Rolle und einer Rollengruppe oder universellen Sicherheitsgruppe bestehen. Sie können die letzte delegierende Rollenzuweisung, die dieser Rolle zugeordnet ist, nicht entfernen, wenn es sich dabei um eine Zuweisung an einen Benutzer handelt.



Weitere Informationen zum Hinzufügen oder Entfernen von Rollenzuweisungen zwischen dieser Rolle und Rollengruppen, Benutzern und universellen Sicherheitsgruppen finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

## Ändern der Verwaltungsbereiche für Rollenzuweisungen

Sie können auch die Verwaltungsbereiche für vorhandene Rollenzuweisungen zwischen dieser Rolle und Rollenempfängern ändern. Durch das Ändern von Verwaltungsbereichen für Rollenzuweisungen steuern Sie, welche Objekte mithilfe der von dieser Rolle bereitgestellten Berechtigungen verwaltet werden können. Sie haben mehrere Möglichkeiten, wenn Sie den Bereich für eine Rollenzuweisung ändern. Sie können eine der folgenden Aktionen durchführen:

  - Fügen Sie einen neuen benutzerdefinierten Bereich mithilfe des Cmdlets **Set-ManagementRoleAssignment** hinzu. Weitere Informationen hierzu finden Sie in den folgenden Themen:
    
      - [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md)
    
      - [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md)

  - Fügen Sie den Bereich für eine Organisationseinheit mithilfe des Cmdlets **Set-ManagementRoleAssignment** hinzu oder ändern Sie diesen. Weitere Informationen finden Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

  - Fügen Sie einen vordefinierten Bereich mithilfe des Cmdlets **Set-ManagementRoleAssignment** hinzu oder ändern Sie diesen. Weitere Informationen finden Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

  - Ändern Sie den Empfänger-, Server- oder Datenbankbereich für den einer Rollenzuweisung zugeordneten benutzerdefinierten Bereich mithilfe des Cmdlets **Set-ManagementScope**. Weitere Informationen finden Sie unter [Ändern eines Rollenbereichs](change-a-role-scope-exchange-2013-help.md).

## Aktivieren oder Deaktivieren von Rollenzuweisungen

Durch das Aktivieren oder Deaktivieren einer Rollenzuweisung steuern Sie, ob diese Rollenzuweisung wirksam sein soll. Ist eine Rollenzuweisung deaktiviert, werden die von der zugehörigen Rolle erteilten Berechtigungen nicht auf den Rollenempfänger angewendet. Dies ist hilfreich, wenn Sie Berechtigungen vorübergehend entfernen möchten, ohne die Rollenzuweisung zu löschen. Weitere Informationen finden Sie unter Ändern einer Rollenzuweisung[Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

## Standard-Verwaltungsrollenzuweisungen

Diese Rolle verfügt über Rollenzuweisungen für einen oder mehrere Rollenempfänger. Die folgende Tabelle zeigt, ob diese Rollenzuweisung regulär oder delegierend ist. Außerdem gibt sie die auf die einzelnen Zuweisungen angewendeten Verwaltungsbereiche an. Die folgende Liste beschreibt jede Spalte:

  - **Reguläre Zuweisung**   Reguläre Rollenzuweisungen ermöglichen dem Rollenempfänger den Zugriff auf die von den Verwaltungsrolleneinträgen dieser Rolle bereitgestellten Berechtigungen.

  - **Delegierende Zuweisung**   Delegierende Rollenzuweisungen geben dem Rollenempfänger die Möglichkeit, diese Rolle zu Rollengruppen, Benutzern oder universellen Sicherheitsgruppen zuzuweisen.

  - **Empfängerlesebereich**  Der Empfängerlesebereich bestimmt, welche Empfängerobjekte der Rollenempfänger aus Active Directory lesen kann.

  - **Empfängerschreibbereich**  Der Empfängerschreibbereich bestimmt, welche Empfängerobjekte der Rollenempfänger in Active Directory ändern kann.

  - **Konfigurationslesebereich**  Der Konfigurationslesebereich bestimmt, welche Konfigurations- und Serverobjekte der Rollenempfänger aus Active Directory lesen kann.

  - **Konfigurationsschreibbereich**  Der Konfigurationsschreibbereich bestimmt, welche Organisations- und Serverobjekte der Rollenempfänger in Active Directory ändern kann.

### Standard-Verwaltungsrollenzuweisungen für diese Rolle

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Rollengruppe</th>
<th>Reguläre Zuweisung</th>
<th>Delegierende Zuweisung</th>
<th>Empfängerlesebereich</th>
<th>Empfängerschreibbereich</th>
<th>Konfigurationslesebereich</th>
<th>Konfigurationsschreibbereich</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>


## Verwaltungsrollenanpassung

Diese Rolle wurde konfiguriert, um einem Rollenempfänger alle erforderlichen Cmdlets und dazugehörigen Parameter für die Verwaltung der zu Beginn dieses Themas genannten Funktionen und Komponenten zur Verfügung zu stellen. Andere Rollen wurden ebenfalls bereitgestellt, um die Verwaltung anderer Funktionen zu ermöglichen. Durch das Hinzufügen und Entfernen von Rollen zu bzw. aus diesen Gruppen können Sie ein benutzerdefiniertes Berechtigungsmodell erstellen, ohne einzelne Verwaltungsrollen anpassen zu müssen. Eine vollständige Liste der Rollen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md). Weitere Informationen zum Anpassen von Rollengruppen finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Wenn Sie sich für das Erstellen einer benutzerdefinierten Version dieser Rolle entscheiden, müssen Sie eine dieser Rolle untergeordnete Rolle erstellen und die neue Rolle anpassen.


> [!WARNING]
> Mithilfe der folgenden Informationen können Sie eine erweiterte Verwaltung von Berechtigungen durchführen. Das Anpassen von Verwaltungsrollen kann die Komplexität Ihres Berechtigungsmodells erheblich erhöhen. Wenn Sie eine integrierte Verwaltungsrolle durch eine nicht ordnungsgemäß konfigurierte Rolle ersetzen, kann dies dazu führen, dass bestimmte Funktionen nicht mehr ausgeführt werden können.



Im Folgenden handelt es sich um die am häufigsten verwendeten Schritte, um eine benutzerdefinierte Rolle zu erstellen und diese einem Rollenempfänger zuzuweisen:

1.  Erstellen Sie eine Kopie dieser Rolle. Weitere Informationen finden Sie unter [Erstellen einer Rolle](create-a-role-exchange-2013-help.md).

2.  Ändern oder entfernen Sie die Rolleneinträge in der neuen Rolle mithilfe der Cmdlets **Set-ManagementRoleEntry** und **Remove-ManagementRoleEntry**. Sie können der neuen Rolle keine zusätzlichen Rolleneinträge hinzufügen, da sie nur die Rolleneinträge der übergeordneten integrierten Rolle enthalten darf. Weitere Informationen hierzu finden Sie in den folgenden Themen:
    
      - [Ändern Sie einen rolleneintrag](change-a-role-entry-exchange-2013-help.md)
    
      - [Entfernen eines Rolleneintrags aus einer Rolle](remove-a-role-entry-from-a-role-exchange-2013-help.md)

3.  Wenn Sie die integrierte Rolle durch diese neue benutzerdefinierte Rolle ersetzen möchten, entfernen Sie alle zu der integrierten Rolle gehörenden Rollenzuweisungen. Weitere Informationen hierzu finden Sie in den folgenden Themen:
    
      - "Hinzufügen einer Rolle zu einer Rollengruppe bzw. Entfernen einer Rolle aus einer Rollengruppe" im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)
    
      - [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

4.  Fügen Sie die neue benutzerdefinierte Rolle den erforderlichen Rollenempfängern hinzu. Weitere Informationen hierzu finden Sie in den folgenden Themen:
    
      - "Hinzufügen einer Rolle zu einer Rollengruppe bzw. Entfernen einer Rolle aus einer Rollengruppe" im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)
    
      - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)
        

        > [!IMPORTANT]
        > Wenn Sie möchten, dass neben dem Benutzer, der die Rolle erstellt hat, andere Benutzer die neue benutzerdefinierte Rolle ebenfalls zuweisen können, müssen Sie mindestens einem Rollenempfänger eine delegierende Rollenzuweisung hinzufügen. Weitere Informationen finden Sie unter <A href="delegate-role-assignments-exchange-2013-help.md">Delegieren von Rollenzuweisungen</A>.


