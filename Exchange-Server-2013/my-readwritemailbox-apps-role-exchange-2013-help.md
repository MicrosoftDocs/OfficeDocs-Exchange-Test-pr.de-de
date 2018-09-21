---
title: 'Rolle „My ReadWriteMailbox Apps“: Exchange 2013 Help'
TOCTitle: Rolle „My ReadWriteMailbox Apps“
ms:assetid: febb73fb-3a0b-4c67-b53b-9566d7c32cd2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt793556(v=EXCHG.150)
ms:contentKeyID: 74418155
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Rolle „My ReadWriteMailbox Apps“

 

_**Letztes Änderungsdatum des Themas:** 2017-02-08_

Die Rolle „Eigene ReadWriteMailbox Apps“ ermöglicht einzelnen Benutzern das Hinzufügen von Add-Ins, für die die ReadWriteMailbox-Berechtigung im Manifest erforderlich ist.

Diese Verwaltungsrolle ist eine von mehreren integrierten Rollen im Modell für rollenbasierte Zugriffssteuerungsberechtigungen (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013. Verwaltungsrollen werden einer oder mehreren Verwaltungsrollengruppen, Zuweisungsrichtlinien für Verwaltungsrollen, Benutzern oder universellen Sicherheitsgruppen zugewiesen. Sie dienen als logische Gruppierung von Cmdlets oder Skripts, die zusammengefasst werden, um das Anzeigen oder Ändern der Konfiguration von Exchange 2013-Komponenten wie Postfachdatenbanken, Transportregeln und Empfängern zu ermöglichen. Wenn ein Cmdlet oder Skript und seine Parameter, die zusammen einen sogenannten Verwaltungsrolleneintrag bilden, in einer Rolle enthalten sind, können das Cmdlet bzw. Skript und seine Parameter von allen ausgeführt werden, denen die Rolle zugewiesen ist. Weitere Informationen zu Verwaltungsrollen und Verwaltungsrolleneinträgen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Weitere Informationen zu Verwaltungsrollen, Verwaltungsrollengruppen und anderen RBAC-Komponenten finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Verwaltungsrollenzuweisungen

Damit über diese Rolle Berechtigungen gewährt werden können, muss sie einem Rollenempfänger zugewiesen werden, beispielsweise einer Rollenzuweisungsrichtlinie. Die Zuweisung erfolgt über Verwaltungsrollenzuweisungen. Rollenzuweisungen verknüpfen Rollenempfänger und Rollen miteinander. Werden einem Rollenempfänger mehrere Rollen zugewiesen, wird dem Rollenempfänger die Gesamtheit aller Berechtigungen erteilt, die durch alle zugewiesenen Rollen erteilt werden.


> [!NOTE]
> Sie können diese Verwaltungsrolle auch einer Rollengruppe, einer universellen Sicherheitsgruppe oder einem Benutzer direkt zuweisen. Benutzerspezifische Rollen sind jedoch am effektivsten, wenn Sie mit Richtlinien für die Rollenzuweisung verwendet werden.



Diese benutzerspezifische ist mit impliziten Bereichen verknüpft, die nicht geändert werden können. Daher sollten Sie keine benutzerdefinierten Bereiche zu Rollenzuweisungen hinzufügen, die diese Rolle Rollenzuweisungsrichtlinien, Rollengruppen, universellen Sicherheitsgruppen oder Benutzern zuweisen.

Weitere Informationen zu Rollenzuweisungen und Bereichen finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Diese Rolle kann standardmäßig einer oder mehreren Zuweisungsrichtlinien zugewiesen sein. Weitere Informationen finden Sie im Abschnitt "Standard-Verwaltungsrollenzuweisungen".

Verwenden Sie den folgenden Befehl, wenn Sie eine Liste der dieser Rolle zugewiesenen Rollengruppen, Benutzer oder universellen Sicherheitsgruppen anzeigen möchten.

```powershell
Get-ManagementRoleAssignment -Role "<role name>"
```

## Reguläre und delegierende Rollenzuweisungen

Diese Rolle kann Rollenempfängern mithilfe von regulären oder delegierenden Rollenzuweisungen zugewiesen werden. Reguläre Rollenzuweisungen erteilen die dem Rollenempfänger von der Rolle bereitgestellten Berechtigungen. Delegierende Rollenzuweisungen geben dem Rollenempfänger die Möglichkeit, die Rolle anderen Rollenempfängern zuzuweisen. Weitere Informationen zu regulären Rollenzuweisungen und delegierenden Rollenzuweisungen finden Sie unter Grundlegendes zu Verwaltungsrollenzuweisungen[Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

## Hinzufügen oder Entfernen von Rollenzuweisungen

Sie können ändern, welchen Rollenempfängern diese Rolle zugewiesen wird. Dadurch ändern Sie, an wen die entsprechenden Berechtigungen erteilt werden. Sie können diese Rolle anderen integrierten Rollenzuweisungsrichtlinien zuweisen oder Rollenzuweisungsrichtlinien erstellen und diesen dann die Rolle zuweisen.

Zum Zuweisen dieser Rolle zu Rollenempfängern mithilfe einer delegierenden Rollenzuweisung muss die ‏Rolle einer Rollengruppe (deren Mitglied Sie sind), Ihnen direkt oder einer universellen Sicherheitsgruppe (deren Mitglied Sie sind) zugewiesen werden. Weitere Informationen zum Delegieren von Rollenzuweisungen finden Sie im Abschnitt "Reguläre und delegierende Rollenzuweisungen".

Sie können diese Rolle auch aus der standardmäßigen Rollenzuweisungsrichtlinie, aus von Ihnen erstellten Rollenzuweisungsrichtlinien und Rollengruppen, Benutzern und universellen Sicherheitsgruppen entfernen. Es muss jedoch stets mindestens eine delegierende Rollenzuweisung zwischen dieser Rolle und einer Rollengruppe oder universellen Sicherheitsgruppe bestehen. Die letzte delegierende Rollenzuweisung kann nicht gelöscht werden.

Weitere Informationen zum Hinzufügen oder Entfernen von Rollenzuweisungen zwischen dieser Rolle und Rollengruppen, Benutzern und universellen Sicherheitsgruppen finden Sie in den folgenden Themen:

  - "Hinzufügen einer Rolle zu einer Rollengruppe bzw. Entfernen einer Rolle aus einer Rollengruppe" im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

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
<th>Rollengruppe oder Zuweisungsrichtlinie</th>
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
<td><p> </p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
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


