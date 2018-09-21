---
title: 'Verwalten von Rollenzuweisungsrichtlinien: Exchange 2013 Help'
TOCTitle: Verwalten von Rollenzuweisungsrichtlinien
ms:assetid: f93d502e-5df4-4ba0-b68d-01a17ccffb4d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657511(v=EXCHG.150)
ms:contentKeyID: 50477103
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Rollenzuweisungsrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-09_

Wenn Sie die Berechtigungen anpassen möchten, Sie einer Gruppe von Endbenutzern zugewiesen sind, erstellen Sie eine neue benutzerdefinierte Zuweisungsrichtlinie für Verwaltungsrollen. Die erstellte Zuweisungsrichtlinie kann an die spezifischen Anforderungen der Endbenutzer angepasst werden. Weitere Informationen zu Zuweisungsrichtlinien in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungstasks es im Zusammenhang mit der Verwaltung von Berechtigungen gibt? Weitere Informationen finden Sie hier: [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Zuweisungsrichtlinien" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Hinzufügen einer Zuweisungsrichtlinie

Nach dem Erstellen der neuen Zuweisungsrichtlinie weisen Sie dieser Benutzer zu. Weitere Informationen finden Sie unter [Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md).

## Erstellen einer neuen Zuweisungsrichtlinie mithilfe der Exchange-Verwaltungskonsole


> [!NOTE]
> Sie können mit der Exchange-Verwaltungskonsole nur explizite Zuweisungsrichtlinien erstellen. Wenn Sie eine neue Standardzuweisungsrichtlinie erstellen möchten, müssen Sie hierzu die Exchange-Verwaltungsshell verwenden. Weitere Informationen finden Sie im Abschnitt "Erstellen einer standardmäßigen Zuweisungsrichtlinie mithilfe der Shell" weiter unten in diesem Thema.



1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Benutzerrollen**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Fenster "Rollenzuweisungsrichtlinie" einen Namen für die neue Zuweisungsrichtlinie ein.

3.  Aktivieren Sie das Kontrollkästchen neben den Rollen, die Sie der Zuweisungsrichtlinie hinzufügen möchten. Sie können mehrere Rollen auswählen, einschließlich der Endbenutzerrollen, die Sie hinzugefügt haben. Wenn Sie eine Rolle mit untergeordneten Rollen auswählen, werden die untergeordneten Rollen automatisch ausgewählt.

4.  Klicken Sie auf **Speichern**, um die Änderungen an der Zuweisungsrichtlinie zu speichern.

## Erstellen einer expliziten Zuweisungsrichtlinie mithilfe der Shell

Verwenden Sie die folgende Syntax, um eine explizite Zuweisungsrichtlinie zu erstellen, die manuell Postfächern zugeordnet werden kann.

```powershell
New-RoleAssignmentPolicy <assignment policy name> -Roles <roles to assign>
```

In diesem Beispiel wird die explizite Zuweisungsrichtlinie "Limited Mailbox Configuration" erstellt und den Rollen `MyBaseOptions`, `MyAddressInformation` und `MyDisplayName` zugeordnet.

    New-RoleAssignmentPolicy "Limited Mailbox Configuration" -Roles MyBaseOptions, MyAddressInformation, MyDisplayName

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638101\(v=exchg.150\)).

## Erstellen einer standardmäßigen Zuweisungsrichtlinie mithilfe der Shell

Verwenden Sie die folgende Syntax, um eine standardmäßige Zuweisungsrichtlinie zu erstellen, die neuen Postfächern zugeordnet wird.

```powershell
New-RoleAssignmentPolicy <assignment policy name> -Roles <roles to assign> -IsDefault
```

In diesem Beispiel wird die standardmäßige Zuweisungsrichtlinie "Limited Mailbox Configuration" erstellt und den Rollen `MyBaseOptions`, `MyAddressInformation` und `MyDisplayName` zugeordnet.

    New-RoleAssignmentPolicy "Limited Mailbox Configuration" -Roles MyBaseOptions, MyAddressInformation, MyDisplayName -IsDefault

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638101\(v=exchg.150\)).

## Entfernen einer Zuweisungsrichtlinie

Nicht mehr benötigte Zuweisungsrichtlinien für Verwaltungsrollen können entfernt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Sämtliche der Zuweisungsrichtlinie zugeordneten Benutzer müssen einer anderen Zuweisungsrichtlinie zugeordnet werden. Weitere Informationen zum Ändern einer Zuweisungsrichtlinie für ein Postfach finden Sie unter [Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md).

  - Sämtliche Verwaltungsrollenzuweisungen zwischen der Zuweisungsrichtlinie und den zugeordneten Verwaltungsrollen müssen entfernt werden. Weitere Informationen zum Entfernen einer Rollenzuweisung aus einer Zuweisungsrichtlinie finden Sie im Abschnitt Entfernen einer Rolle aus einer Zuweisungsrichtlinie mithilfe der Shell weiter unten in diesem Thema.

  - Wenn Sie eine Standardzuweisungsrichtlinie entfernen möchten, muss es sich um die letzte Zuweisungsrichtlinie in der Exchange 2013-Organisation handeln.

## Entfernen einer Zuweisungsrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Benutzerrollen**.

2.  Wählen Sie die Zuweisungsrichtlinie aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Entfernen einer Zuweisungsrichtlinie mithilfe der Shell

Verwenden Sie die folgende Syntax, um eine Zuweisungsrichtlinie zu entfernen.

```powershell
Remove-RoleAssignmentPolicy <role assignment policy>
```

In diesem Beispiel wird die Zuweisungsrichtlinie "New York Temporary Users" entfernt.

```powershell
Remove-RoleAssignmentPolicy "New York Temporary Users"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638190\(v=exchg.150\)).

## Anzeigen einer Liste von Zuweisungsrichtlinien oder Zuweisungsrichtliniendetails

Sie können Zuweisungsrichtlinien für Verwaltungsrollen auf mehrere Arten anzeigen, abhängig von den Informationen, die Sie benötigen, und ob Sie die Exchange-Verwaltungskonsole oder die -Shell verwenden.

In der Exchange-Verwaltungskonsole können Sie die Liste der Zuweisungsrichtlinien und den zugeordneten Rollen anzeigen. Sie können in der Shell alle Zuweisungsrichtlinien Ihrer Organisation anzeigen oder die Postfächer auflisten, denen eine bestimmte Richtlinie zugewiesen ist, und mehr.

## Anzeigen einer Liste von Zuweisungsrichtlinien mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Benutzerrollen**. Alle Zuweisungsrichtlinien in der Organisation sind hier aufgelistet.

2.  Wählen Sie zum Anzeigen der Details einer bestimmten Zuweisungsrichtlinie die anzuzeigende Zuweisungsrichtlinie aus. Die Beschreibung und die der Zuweisungsrichtlinie zugeordneten Rollen werden im Detailbereich angezeigt.

## Verwenden der Shell zum Anzeigen einer Liste von Zuweisungsrichtlinien

Sie können eine Liste aller Zuweisungsrichtlinien in Ihrer Organisation anzeigen, indem Sie bei Ausführung des Cmdlets **Get-RoleAssignmentPolicy** keine Zuweisungsrichtlinien angeben.

In dieser Vorgehensweise werden das Pipelining und das Cmdlet **Format-Table** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

Um eine Liste aller Zuweisungsrichtlinien in Ihrer Organisation zu erhalten, verwenden Sie den folgenden Befehl.

```powershell
Get-RoleAssignmentPolicy
```

Um eine Liste bestimmter Eigenschaften für alle Zuweisungsrichtlinien in Ihrer Organisation zu erhalten, können Sie das Ergebnis über Pipelining an das Cmdlet **Format-Table** umleiten und dabei die Eigenschaften angeben, die in der Ergebnisliste enthalten sein sollen. Verwenden Sie die folgende Syntax.

```powershell
Get-RoleAssignmentPolicy | Format-Table <property 1>, <property 2...>
```

Mit diesem Beispiel werden eine Liste aller Zuweisungsrichtlinien in Ihrer Organisation sowie die Eigenschaften **Name** und **IsDefault** zurückgegeben.

```powershell
Get-RoleAssignmentPolicy | Format-Table Name, IsDefault
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) oder [Get-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638195\(v=exchg.150\)).

## Verwenden der Shell zum Anzeigen von Details zu einer einzelnen Zuweisungsrichtlinie

Sie können die Details zu einer bestimmten Zuweisungsrichtlinie auch anzeigen, indem Sie das Cmdlet **Get-RoleAssignmentPolicy** verwenden und die Ausgabe über Pipelining an das Cmdlet **Format-List** umleiten.

In dieser Vorgehensweise werden das Pipelining und das Cmdlet **Format-List** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

Verwenden Sie die folgende Syntax, um die Details zu einer bestimmten Zuweisungsrichtlinie anzuzeigen.

```powershell
Get-RoleAssignmentPolicy <assignment policy name> | Format-List
```

Mit diesem Beispiel werden die Details zur Zuweisungsrichtlinie "Redmond-Benutzer - keine Textnachrichten (SMS)" angezeigt.

```powershell
Get-RoleAssignmentPolicy "Redmond Users - no Text Messaging" | Format-List
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) oder [Get-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638195\(v=exchg.150\)).

## Verwenden der Shell zum Suchen nach der Standardzuweisungsrichtlinie

Sie können nach der Standardzuweisungsrichtlinie suchen, indem Sie die Ausgabe des Cmdlets **Get-RoleAssignmentPolicy** über Pipelining an das Cmdlet **Where** umleiten. Filtern Sie die zurückgegebenen Daten mithilfe des Cmdlets **Where**, sodass nur die Zuweisungsrichtlinie angezeigt wird, für die die Eigenschaft *IsDefault* auf `$True` gesetzt ist.

In diesem Verfahren werden das Pipelining und das Cmdlet **Where** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

In diesem Beispiel wird die Standardzuweisungsrichtlinie zurückgegeben.

```powershell
Get-RoleAssignmentPolicy | Where {     Get-RoleAssignmentPolicy | Where { $_.IsDefault -eq $True }.IsDefault -eq $True }
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) oder [Get-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638195\(v=exchg.150\)).

## Verwenden der Shell zum Anzeigen von Postfächern, denen eine bestimmte Richtlinie zugewiesen ist

Sie können alle Postfächer ermitteln, denen eine bestimmte Zuweisungsrichtlinie zugeordnet ist, indem Sie die Ausgabe des Cmdlets **Get-Mailbox** an das Cmdlet **Where** umleiten. Filtern Sie die zurückgegebenen Daten mithilfe des Cmdlets **Where**, sodass nur die Postfächer angezeigt werden, für die die Eigenschaft *RoleAssignmentPolicy* auf die von Ihnen angegebene Zuweisungsrichtlinie gesetzt ist.

In diesem Verfahren werden das Pipelining und das Cmdlet **Where** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

Verwenden Sie die folgende Syntax.

```powershell
Get-Mailbox | Where {     Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "<role assignment policy>" }.RoleAssignmentPolicy -Eq "<role assignment policy>" }
```

In diesem Beispiel werden alle Postfächer ermittelt, denen die Richtlinie "Vancouver-Endbenutzer" zugewiesen ist.

```powershell
Get-Mailbox | Where {     Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Vancouver End Users" }.RoleAssignmentPolicy -Eq "Vancouver End Users" }
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) oder [Get-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638195\(v=exchg.150\)).

## Ändern der standardmäßigen Zuweisungsrichtlinie

Sie können die Richtlinie für die Verwaltungsrollenzuweisung ändern, die neu erstellten Postfächern zugeordnet wird. Durch das Ändern der standardmäßigen Rollenzuweisungsrichtlinie wird nicht automatisch die den vorhandenen Postfächern zugeordnete Zuweisungsrichtlinie geändert. Weitere Informationen zum Ändern der den vorhandenen Postfächern zugeordneten Zuweisungsrichtlinie finden Sie unter [Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md).


> [!NOTE]
> Sie können die standardmäßige Zuweisungsrichtlinie nicht mithilfe der Exchange-Verwaltungskonsole ändern. Sie müssen die Shell verwenden.



## Ändern der standardmäßigen Zuweisungsrichtlinie mithilfe der Shell

Verwenden Sie die folgende Syntax, um die standardmäßige Zuweisungsrichtlinie zu ändern.

```powershell
Set-RoleAssignmentPolicy <assignment policy name> -IsDefault
```

In diesem Beispiel wird die Zuweisungsrichtlinie "Vancouver End Users" als standardmäßige Zuweisungsrichtlinie festgelegt.

```powershell
Set-RoleAssignmentPolicy "Vancouver End Users" -IsDefault
```


> [!IMPORTANT]
> Neuen Postfächern wird die standardmäßige Zuweisungsrichtlinie selbst dann zugeordnet, wenn der Richtlinie keine Verwaltungsrollen zugewiesen wurden. Postfächern zugeordnete Zuweisungsrichtlinien ohne zugewiesene Verwaltungsrollen können nicht auf Funktionen für die Postfachkonfiguration in Microsoft Outlook Web App zugreifen.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RoleAssignmentPolicy](https://technet.microsoft.com/de-de/library/dd638090\(v=exchg.150\)).

## Hinzufügen einer Rolle zu einer Zuweisungsrichtlinie

## Hinzufügen einer Rolle zu einer Zuweisungsrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Benutzerrollen**.

2.  Wählen Sie die Zuweisungsrichtlinie aus, der Sie mindestens eine Rolle hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie das Kontrollkästchen neben den Rollen, die Sie der Zuweisungsrichtlinie hinzufügen möchten. Sie können mehrere Rollen auswählen, einschließlich der Endbenutzerrollen, die Sie hinzugefügt haben. Wenn Sie eine Rolle mit untergeordneten Rollen auswählen, werden die untergeordneten Rollen automatisch ausgewählt.

4.  Klicken Sie auf **Speichern**, um die Änderungen an der Zuweisungsrichtlinie zu speichern.

## Verwenden der Shell zum Hinzufügen einer Rolle zu einer Zuweisungsrichtlinie

Verwenden Sie zum Erstellen einer Verwaltungsrollenzuweisung zwischen einer Rolle und einer Zuweisungsrichtlinie die folgende Syntax.

    New-ManagementRoleAssignment -Name <role assignment name> -Role <role name> -Policy <assignment policy name>

In diesem Beispiel wird die Rollenzuweisung "Seattle Users - Voicemail" zwischen der Rolle "MyVoicemail" und der Zuweisungsrichtlinie "Seattle Users" erstellt.

    New-ManagementRoleAssignment -Name "Seattle Users - Voicemail" -Role MyVoicemail -Policy "Seattle Users"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Entfernen einer Rolle aus einer Zuweisungsrichtlinie

Wenn Sie Endbenutzern nicht die Berechtigungen zum Verwalten von Funktionen ihres Postfachs oder ihrer Verteilergruppe erteilen möchten, können Sie die Verwaltungsrolle, welche die Berechtigungen erteilt, aus der Zuweisungsrichtlinie für Verwaltungsrollen des Benutzers entfernen. Wenn anderen Benutzern dieselbe Zuweisungsrichtlinie zugewiesen ist, verlieren auch sie die Möglichkeit, diese Funktion zu verwalten.

## Entfernen einer Rolle aus einer Zuweisungsrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Benutzerrollen**.

2.  Wählen Sie die Zuweisungsrichtlinie aus, aus der Sie Rollen entfernen möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie das Kontrollkästchen neben den Rollen, die aus der Zuweisungsrichtlinie entfernt werden sollen. Wenn Sie das Kontrollkästchen für eine Rolle mit untergeordneten Rollen deaktivieren, werden auch die Kontrollkästchen der untergeordneten Rollen deaktiviert.

4.  Klicken Sie auf **Speichern**, um die Änderungen an der Zuweisungsrichtlinie zu speichern.

## Entfernen einer Rolle aus einer Zuweisungsrichtlinie mithilfe der Shell

Sie können Rollen aus Zuweisungsrichtlinien entfernen, indem Sie die zugehörige Verwaltungsrollenzuweisung mithilfe des Cmdlets **Get-ManagementRoleAssignment** abrufen und die zurückgegebene Rollenzuweisung an das Cmdlet **Remove-ManagementRoleAssignment** weiterleiten.

Weitere Informationen zu regulären und delegierenden Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Bei diesem Verfahren wird das Pipelining verwendet. Weitere Informationen zum Pipelining finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

Verwenden Sie die folgende Syntax, um eine Rolle aus einer Zuweisungsrichtlinie zu entfernen.

    Get-ManagementRoleAssignment -RoleAssignee <assignment policy name> -Role <role name> | Remove-ManagementRoleAssignment

In diesem Beispiel wird die Verwaltungsrolle "MyVoicemail", welche Benutzern die Verwaltung ihrer Voicemailoptionen ermöglicht, aus der Zuweisungsrichtlinie "Seattle Users" entfernt.

    Get-ManagementRoleAssignment -RoleAssignee "Seattle Users" -Role MyVoicemail | Remove-ManagementRoleAssignment

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351205\(v=exchg.150\)).

