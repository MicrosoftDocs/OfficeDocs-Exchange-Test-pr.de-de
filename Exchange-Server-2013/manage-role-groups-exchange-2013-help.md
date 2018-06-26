---
title: 'Verwalten von Rollengruppen: Exchange 2013 Help'
TOCTitle: Verwalten von Rollengruppen
ms:assetid: ab9b7a3b-bf67-4ba1-bde5-8e6ac174b82c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657480(v=EXCHG.150)
ms:contentKeyID: 50476417
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Rollengruppen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-08_

In diesem Thema wird erläutert, wie Verwaltungsrollengruppen in Microsoft Exchange Server 2013 hinzugefügt, entfernt, kopiert und angezeigt werden können. Außerdem wird erläutert, wie Verwaltungsrollen zu Rollengruppen hinzugefügt, aus diesen entfernt sowie für sie aufgelistet und wie Verwaltungsbereiche und Stellvertretungen für Rollengruppen geändert werden können. Weitere Informationen zu Rollengruppen in Exchange 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Rollengruppen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 bis 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Rollengruppe

Wenn Sie die Berechtigungen anpassen möchten, die einer Gruppe von Benutzern zugewiesen werden können, erstellen Sie eine neue benutzerdefinierte Verwaltungsrollengruppe.

## Erstellen einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Fenster **Neue Rollengruppe** einen Namen für die neue Rollengruppe ein.

3.  Sie können nun die Rollen auswählen, die Sie der Rollengruppe und den Mitgliedern zuweisen möchten, die Sie der Rollengruppe hinzufügen möchten. Sie können diese Auswahl aber auch zu einem späteren Zeitpunkt vornehmen.

4.  Wählen Sie den Schreibbereich aus, den Sie auf die neue Rollengruppe anwenden möchten.

5.  Klicken Sie auf **Speichern**, um die Rollengruppe zu erstellen.

## Erstellen einer Rollengruppe mithilfe der Shell

Informationen zum Erstellen einer Rollengruppe finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/dd638181\(exchg.150\)#examples) unter [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass eine Rollengruppe erfolgreich erstellt wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Vergewissern Sie sich, dass die neue Rollengruppe in der Liste der Rollengruppen angezeigt wird, und wählen Sie die neue Rollengruppe aus.

3.  Vergewissern Sie sich, dass die Mitglieder, die zugewiesenen Rollen und der Bereich, die Sie für die neue Rollengruppe angegeben haben, im Detailbereich für Rollengruppen angezeigt werden.

## Kopieren einer Rollengruppe

## Kopieren einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

Wenn Sie eine Rollengruppe mit den Berechtigungen haben, die Sie Benutzern erteilen möchten, Sie aber einen anderen Verwaltungsbereich anwenden oder ein oder zwei Verwaltungsrollen hinzufügen bzw. entfernen möchten, ohne alle anderen Rollen manuell hinzufügen zu müssen, können Sie die vorhandene Rollengruppe kopieren.


> [!IMPORTANT]
> Die Exchange-Verwaltungskonsole kann nicht zum Kopieren einer Rollengruppe verwendet werden, wenn Sie für die Rollengruppe mit der Exchange-Verwaltungsshell mehrere Verwaltungsrollenbereiche oder exklusive Bereiche konfiguriert haben. Wenn Sie mehrere Bereiche oder exklusive Bereiche für die Rollengruppe konfiguriert haben, müssen Sie die Rollengruppe mithilfe der Verfahren für die Shell weiter unten in diesem Thema kopieren. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter <A href="understanding-management-role-scopes-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollenbereichen</A>.



1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, die Sie kopieren möchten, und klicken Sie dann auf **Kopieren**![Kopieren (Symbol)](images/JJ657480.ed7f7abf-39d8-4f43-a918-ccb3bff87ef5(EXCHG.150).gif "Kopieren (Symbol)").

3.  Geben Sie im Fenster **Neue Rollengruppe** einen Namen für die neue Rollengruppe ein.

4.  Überprüfen Sie die Rollen, die in die neue Rollengruppe kopiert wurden. Fügen Sie ggf. Rollen hinzu, oder entfernen Sie ggf. Rollen.

5.  Überprüfen Sie den Schreibbereich, und ändern Sie ihn nach Bedarf.

6.  Überprüfen Sie die Mitglieder, die in die neue Rollengruppe kopiert wurden. Fügen Sie ggf. Mitglieder hinzu, oder entfernen Sie ggf. Mitglieder.

7.  Klicken Sie auf **Speichern**, um die Rollengruppe zu erstellen.

## Verwenden der Shell zum Kopieren einer Rollengruppe ohne Bereich

1.  Verwenden Sie die folgende Syntax, um die Rollengruppe, die Sie kopieren möchten, in einer Variablen zu speichern.
    
        $RoleGroup = Get-RoleGroup <name of role group to copy>

2.  Verwenden Sie die folgende Syntax, um die neue Rollengruppe zu erstellen, der Rollengruppe Mitglieder hinzuzufügen und anzugeben, wer die neue Rollengruppe an andere Benutzer delegieren kann.
    
        New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -Members <member1, member2, member3...> -ManagedBy <user1, user2, user3...>

Mithilfe der folgenden Befehle können Sie z. B. die Rollengruppe "Organization Management" kopieren und die neue Rollengruppe "Limited Organization Management" nennen. Hinzugefügt werden die Mitglieder Isabelle, Carter und Lukas, zugewiesen werden kann sie von Jenny und Katie.

    $RoleGroup = Get-RoleGroup "Organization Management"
    New-RoleGroup "Limited Organization Management" -Roles $RoleGroup.Roles -Members Isabelle, Carter, Lukas -ManagedBy Jenny, Katie

Nach dem Erstellen einer neuen Rollengruppe können Sie u. a. Rollen hinzufügen oder entfernen und den Bereich von Rollenzuweisungen für die Rolle ändern.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-RoleGroup](https://technet.microsoft.com/de-de/library/dd638115\(v=exchg.150\)) und [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\)).

## Verwenden der Shell zum Kopieren einer Rollengruppe mit einem benutzerdefinierten Bereich

1.  Verwenden Sie die folgende Syntax, um die Rollengruppe, die Sie kopieren möchten, in einer Variablen zu speichern.
    
        $RoleGroup = Get-RoleGroup <name of role group to copy>

2.  Verwenden Sie die folgende Syntax, um die neue Rollengruppe mit einem benutzerdefinierten Bereich zu erstellen.
    
        New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuraiton scope name>

Mithilfe der folgenden Befehle können Sie beispielsweise die Rollengruppe "Organization Management" kopieren und eine neue Rollengruppe namens "Vancouver Organization Management" mit dem Empfängerbereich "Vancouver Users" und dem Konfigurationsbereich "Vancouver Servers" erstellen.

    $RoleGroup = Get-RoleGroup "Organization Management"
    New-RoleGroup "Vancouver Organization Management" -Roles $RoleGroup.Roles -CustomRecipientWriteScope "Vancouver Users" -CustomConfigWriteScope "Vancouver Servers"

Sie können der Rollengruppe auch Mitglieder hinzufügen, wenn Sie sie mit dem Parameter *Members* erstellen, wie unter Verwenden der Shell zum Kopieren einer Rollengruppe ohne Bereich weiter oben in diesem Thema veranschaulicht. Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Nach dem Erstellen einer neuen Rollengruppe können Sie u. a. Rollen hinzufügen oder entfernen und den Bereich von Rollenzuweisungen für die Rolle ändern.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-RoleGroup](https://technet.microsoft.com/de-de/library/dd638115\(v=exchg.150\)) und [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\)).

## Verwenden der Shell zum Kopieren einer Rollengruppe mit OU-Bereich

1.  Verwenden Sie die folgende Syntax, um die Rollengruppe, die Sie kopieren möchten, in einer Variablen zu speichern.
    
        $RoleGroup = Get-RoleGroup <name of role group to copy>

2.  Verwenden Sie die folgende Syntax, um die neue Rollengruppe mit einem benutzerdefinierten Bereich zu erstellen.
    
        New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -RecipientOrganizationalUnitScope <OU name>

Mithilfe der folgenden Befehle können Sie beispielsweise die Rollengruppe "Recipient Management" kopieren und eine neue Rollengruppe namens "Toronto Recipient Management" erstellen, die nur die Verwaltung von Benutzern in der Organisationseinheit "Toronto Users" zulässt.

    $RoleGroup = Get-RoleGroup "Recipient Management"
    New-RoleGroup "Toronto Recipient Management" -Roles $RoleGroup.Roles -RecipientOrganizationalUnitScope "contoso.com/Toronto Users"

Sie können der Rollengruppe auch Mitglieder hinzufügen, wenn Sie sie mit dem Parameter *Members* erstellen, wie unter Verwenden der Shell zum Kopieren einer Rollengruppe ohne Bereich weiter oben in diesem Thema veranschaulicht. Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Nach dem Erstellen einer neuen Rollengruppe können Sie u. a. Rollen hinzufügen oder entfernen und den Bereich von Rollenzuweisungen für die Rolle ändern.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-RoleGroup](https://technet.microsoft.com/de-de/library/dd638115\(v=exchg.150\)) und [New-RoleGroup](https://technet.microsoft.com/de-de/library/dd638181\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass eine Rollengruppe erfolgreich kopiert wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Vergewissern Sie sich, dass die kopierte Rollengruppe in der Liste der Rollengruppen angezeigt wird, und wählen Sie die Rollengruppe aus.

3.  Vergewissern Sie sich, dass die Mitglieder, die zugewiesenen Rollen und der Bereich, die Sie für die kopierte Rollengruppe angegeben haben, im Detailbereich für Rollengruppen angezeigt werden.

## Entfernen einer Rollengruppe

Wenn Sie eine Gruppe, die Sie erstellt haben, nicht mehr benötigen, können Sie sie entfernen. Wenn Sie eine Rollengruppe entfernen, werden die Verwaltungsrollenzuweisungen zwischen der Rollengruppe und den Verwaltungsrollen gelöscht. Die Verwaltungsrollen werden nicht entfernt. Wenn der Zugriff eines Benutzers auf eine Funktion von der Rollengruppe abhängig war, kann der Benutzer nicht länger auf diese Funktion zugreifen. Sie können keine integrierten Rollengruppen entfernen.

## Entfernen einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Überprüfen Sie, ob Sie die ausgewählte Rollengruppe tatsächlich entfernen möchten. Ist dies der Fall, beantworten Sie die Warnung mit **Ja**.

## Verwenden der Shell zum Entfernen einer Rollengruppe

Informationen zum Entfernen einer Rollengruppe finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/dd638141\(exchg.150\)#examples) unter [Remove-RoleGroup](https://technet.microsoft.com/de-de/library/dd638141\(v=exchg.150\)).

## Anzeigen von Rollengruppen

Sie können entweder eine Liste mit Rollengruppen oder die detaillierten Informationen zu einer bestimmten Rollengruppe in Ihrer Organisation anzeigen.

## Anzeigen einer Liste mit Rollengruppen sowie von Rollengruppendetails mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**. Alle Rollengruppen in Ihrer Organisation werden hier aufgelistet.

2.  Wählen Sie eine Rollengruppe aus, um die Mitglieder, die zugewiesenen Rollen und den Bereich anzuzeigen, die für die Rollengruppe konfiguriert sind.

## Anzeigen einer Liste mit Rollengruppen sowie von Rollengruppendetails mithilfe der Shell

Informationen zum Anzeigen einer Liste mit Rollengruppen finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/dd638115\(exchg.150\)#examples) unter [Get-RoleGroup](https://technet.microsoft.com/de-de/library/dd638115\(v=exchg.150\)).

## Hinzufügen einer Rolle zu einer Rollengruppe

Das Hinzufügen einer Verwaltungsrolle zu einer Rollengruppe ist die beste und einfachste Methode, einer Gruppe von Administratoren oder spezialisierten Benutzern Berechtigungen zu erteilen. Wenn Sie Benutzern, die Mitglieder einer Rollengruppe sind, die Berechtigung zum Verwalten einer Funktion erteilen möchten, fügen Sie der Rollengruppe die Verwaltungsrolle hinzu, die die Funktion verwaltet. Nach dem Hinzufügen der Rolle verfügen die Mitglieder der Rollengruppe über die Berechtigungen der Rolle.

## Hinzufügen einer Verwaltungsrolle zu einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole


> [!IMPORTANT]
> Die Exchange-Verwaltungskonsole kann nicht zum Hinzufügen von Rollen zu einer Rollengruppe verwendet werden, wenn Sie für die Rollengruppe mit der Shell mehrere Verwaltungsrollenbereiche oder exklusive Bereiche konfiguriert haben. Wenn Sie mehrere Bereiche oder exklusive Bereiche für die Rollengruppe konfiguriert haben, müssen Sie die weiter unten in diesem Thema beschriebenen Shellverfahren nutzen, um Rollen zur Rollengruppe hinzuzufügen. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter <A href="understanding-management-role-scopes-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollenbereichen</A>.



1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, der Sie eine Rolle hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie im Abschnitt **Rollen** die Rollen aus, die Sie der Rollengruppe hinzufügen möchten.

4.  Wenn Sie der Rollengruppe keine weiteren Rollen mehr hinzufügen möchten, klicken Sie auf **Speichern**.

## Erstellen einer Rollenzuweisung ohne Bereich mithilfe der Shell

Sie können eine Rollenzuweisung ohne Bereich zwischen einer Rolle und einer Rollengruppe erstellen. Wenn Sie dies machen, gelten die impliziten Lese- und Schreibbereiche der Rolle.

Verwenden Sie die folgende Syntax zum Zuweisen einer Rolle ohne Bereich zu einer Rollengruppe. Wenn Sie keinen Namen für die Rollenzuweisung angeben, wird automatisch ein Name erstellt.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name>

In diesem Beispiel wird die Verwaltungsrolle Transportregeln der Rollengruppe "Seattle Compliance" zugewiesen.

    New-ManagementRoleAssignment -SecurityGroup "Seattle Compliance" -Role "Transport Rules"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit vordefiniertem Bereich mithilfe der Shell

Wenn ein vordefinierter Bereich Ihren Geschäftsanforderungen entspricht, können Sie diesen Bereich auf die Rollenzuweisung anwenden, statt einen neuen zu erstellen. Eine Liste vordefinierter Bereiche und ihrer Beschreibungen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Weitere Informationen zu Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Anhand der folgenden Syntax weisen Sie einer Rollengruppe eine Rolle mit vordefiniertem Bereich zu. Wenn Sie keinen Namen für die Rollenzuweisung angeben, wird automatisch ein Name erstellt.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -RecipientRelativeWriteScope < MyGAL | MyDistributionGroups | Organization | Self >

In diesem Beispiel wird die Rolle Nachrichtenverfolgung der Rollengruppe "Enterprise Support" zugewiesen und der vordefinierte Bereich Organisation angewendet.

    New-ManagementRoleAssignment -SecurityGroup "Enterprise Support" -Role "Message Tracking" -RecipientRelativeWriteScope Organization

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem filterbasierten Empfängerbereich mithilfe der Shell

Wenn Sie einen filterbasierten Empfängerbereich erstellt haben, müssen Sie anhand des Parameters *CustomRecipientWriteScope* den Bereich in den Befehl aufnehmen, mit dem Sie die Rolle einer Rollengruppe zuweisen.

Beim Erstellen einer Rollenzuweisung mit Empfängerschreibbereich können Sie auch einen Konfigurationsschreibbereich einschließen.

Weitere Informationen zu Rollenzuweisungen und Bereichen finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Verwenden Sie die folgenden Syntax, um eine Rolle einer Rollengruppe mit einem filterbasierten Empfängerbereich zuzuweisen. Wenn Sie keinen Namen für die Rollenzuweisung angeben, wird automatisch ein Name erstellt.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -CustomRecipientWriteScope <role scope name>

In diesem Beispiel wird die Rolle Nachrichtenverfolgung der Rollengruppe "Seattle Recipient Admins" zugewiesen und der Bereich "Seattle Recipients" angewendet.

    New-ManagementRoleAssignment -SecurityGroup "Seattle Recipient Admins" -Role "Message Tracking" -CustomRecipientWriteScope "Seattle Recipients"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem Konfigurationsbereich mithilfe der Shell

Wenn Sie einen filter- oder listenbasierten Server- oder Datenbankkonfigurationsbereich erstellt haben, müssen Sie den Bereich über den Parameter *CustomConfigWriteScope* in den Befehl aufnehmen, um die Rolle einer Rollengruppe zuzuweisen.

Beim Erstellen einer Rollenzuweisung mit Konfigurationsschreibbereich können Sie auch einen Empfängerschreibbereich einschließen.

Weitere Informationen zu Rollenzuweisungen und Verwaltungsbereichen finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Verwenden Sie die folgende Syntax, um eine Rolle einer Rollengruppe mit einem Konfigurationsbereich zuzuweisen. Wenn Sie keinen Namen für die Rollenzuweisung angeben, wird automatisch ein Name erstellt.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -CustomConfigWriteScope <role scope name>

In diesem Beispiel wird die Rolle Datenbanken der Rollengruppe "Seattle Server Admins" zugewiesen und der Bereich "Seattle Servers" angewendet.

    New-ManagementRoleAssignment -SecurityGroup "Seattle Server Admins" -Role "Databases" -CustomConfigWriteScope "Seattle Servers"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit Organisationseinheitsbereich mithilfe der Shell

Wenn Sie den Schreibbereich einer Rolle auf eine Organisationseinheit festlegen möchten, können Sie die Organisationseinheit direkt im Parameter *RecipientOrganizationalUnitScope* angeben.

Weitere Informationen zu Rollenzuweisungen und Verwaltungsbereichen finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Verwenden Sie den folgenden Befehl, um einer Rollengruppe eine Rolle zuzuweisen und den Schreibbereich einer Rolle auf eine bestimmte Organisationseinheit zu beschränken. Wenn Sie keinen Namen für die Rollenzuweisung angeben, wird automatisch ein Name erstellt.

    New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -RecipientOrganizationalUnitScope <OU>

In diesem Beispiel wird die Rolle "Mail Recipients" der Rollengruppe "Seattle Recipient Admins" zugewiesen und der Bereich der Zuweisung auf die Organisationseinheit "Sales\\Users" in der Domäne "Contoso.com" festgelegt.

    New-ManagementRoleAssignment -SecurityGroup "Seattle Recipient Admins" -Role "Mail Recipients" -RecipientOrganizationalUnitScope contoso.com/sales/users

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass Rollen erfolgreich zu einer Rollengruppe hinzugefügt wurden:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, der Sie Rollen hinzugefügt haben. Überprüfen Sie im Detailbereich für Rollengruppen, ob die von Ihnen hinzugefügten Rollen aufgelistet werden.

## Entfernen einer Rolle aus einer Rollengruppe

Das Entfernen einer Rolle aus einer Verwaltungsrollengruppe ist die beste und einfachste Methode, einer Gruppe von Administratoren oder spezialisierten Benutzern erteilte Berechtigungen zu entziehen. Wenn Sie Administratoren oder spezialisierten Benutzern keine Berechtigungen zum Verwalten einer Funktion erteilen möchten, entfernen Sie die Verwaltungsrolle aus der Verwaltungsrollengruppe, über welche die Berechtigungen verwaltet werden. Nachdem die Rolle entfernt wurde, besitzen die Mitglieder der Rollengruppe nicht länger Berechtigungen zum Verwalten der Funktion.


> [!NOTE]
> Einige Rollengruppen – beispielsweise die Rollengruppe Organisationsverwaltung – beschränken, welche Rollen aus einer Rollengruppe entfernt werden können. Weitere Informationen finden Sie unter <A href="understanding-management-role-groups-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollengruppen</A>.<BR>Wenn ein Administrator Mitglied einer weiteren Rollengruppe mit Verwaltungsrollen ist, die das Verwalten der Funktion ermöglichen, müssen Sie den Administrator entweder auch aus diesen Rollengruppen entfernen oder die Rolle aus den weiteren Rollengruppen entfernen, die das Verwalten der Funktion ermöglicht.



## Entfernen einer Verwaltungsrolle aus einer Rollengruppe mithilfe der Exchange-Verwaltungskonsole


> [!IMPORTANT]
> Die Exchange-Verwaltungskonsole kann nicht zum Entfernen von Rollen aus einer Rollengruppe verwendet werden, wenn Sie für die Rollengruppe mit der Shell mehrere Bereiche oder exklusive Bereiche konfiguriert haben. Wenn Sie mehrere Bereiche oder exklusive Bereiche für die Rollengruppe konfiguriert haben, müssen Sie die weiter unten in diesem Thema beschriebenen Shellverfahren nutzen, um Rollen aus der Rollengruppe zu entfernen. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter <A href="understanding-management-role-scopes-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollenbereichen</A>.



1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, aus der Sie eine Rolle entfernen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie im Abschnitt **Rollen** die Rollen aus, die Sie aus der Rollengruppe entfernen möchten.

4.  Wenn Sie mit dem Entfernen von Rollen aus der Rollengruppe fertig sind, klicken Sie auf **Speichern**.

## Entfernen einer Rolle aus einer Rollengruppe mithilfe der Shell

Sie können Rollen aus Rollengruppen entfernen, indem Sie die zugehörige Verwaltungsrollenzuweisung mithilfe des Cmdlets **Get-ManagementRoleAssignment** abrufen und die zurückgegebene Rollenzuweisung an das Cmdlet **Remove-ManagementRoleAssignment** weiterleiten. Sofern Sie nicht sowohl delegierende als auch reguläre Rollenzuweisungen gleichzeitig entfernen möchten, geben Sie mit dem Parameter *Delegating* an, ob Sie reguläre oder delegierende Rollenzuweisungen entfernen möchten.

Weitere Informationen zu regulären und delegierenden Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Bei diesem Verfahren wird das Pipelining verwendet. Weitere Informationen zum Pipelining finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

Verwenden Sie die folgende Syntax, um eine Rolle aus einer Rollengruppe zu entfernen.

    Get-ManagementRoleAssignment -RoleAssignee <role group name> -Role <role name> -Delegating <$true | $false> | Remove-ManagementRoleAssignment

In diesem Beispiel wird die Rolle "Distribution Groups", die Administratoren das Verwalten von Verteilergruppen ermöglicht, aus der Rollengruppe "Seattle Recipient Administrators" entfernt. Da die Rollenzuweisung entfernt werden soll, mit der Berechtigungen zum Verwalten von Verteilergruppen gewährt werden, wird der Parameter *Delegating* auf `$False` festgelegt, sodass nur reguläre Rollenzuweisungen zurückgegeben werden.

    Get-ManagementRoleAssignment -RoleAssignee "Seattle Recipient Administrators" -Role "Distribution Groups" -Delegating $false | Remove-ManagementRoleAssignment

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351205\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass Rollen erfolgreich aus einer Rollengruppe entfernt wurden:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, aus der Sie Rollen entfernt haben. Überprüfen Sie im Detailbereich für Rollengruppen, ob die von Ihnen entfernten Rollen nicht mehr aufgelistet werden.

## Ändern des Bereichs einer Rollengruppe

Die Verwaltungsrollenzuweisungen zwischen einer Rollengruppe und einer Rolle enthalten Verwaltungsbereiche, die bestimmen, welche Objekte für Mitglieder dieser Rollengruppe verfügbar gemacht werden. Durch Ändern des Schreibbereichs einer Rollengruppe können Sie festlegen, welche Objekte den Rollengruppenmitgliedern zum Erstellen, Ändern oder Entfernen zur Verfügung gestellt werden. Der Lesebereich einer Rollengruppe kann nicht geändert werden.

Exchange 2013 umfasst Bereiche, die standardmäßig für Rollenzuweisungen verwendet werden, wenn keine benutzerdefinierten Bereiche erstellt werden. Wenn Sie einen benutzerdefinierten Bereich mit einer Rollenzuweisung für eine Rollengruppe verwenden möchten, müssen Sie diesen zuerst erstellen. Weitere Informationen zu der speziellen Aufgabe des Erstellens von benutzerdefinierten Bereichen finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

Weitere Informationen zu Verwaltungsrollenbereichen und -zuweisungen in Exchange 2013 finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

## Ändern des Bereichs für eine Rollengruppe mithilfe der Exchange-Verwaltungskonsole

Wenn Sie die Exchange-Verwaltungskonsole verwenden, um den Bereich für eine Rollengruppe zu ändern, dann ändern Sie tatsächlich den Bereich für alle Rollenzuweisungen zwischen der Rollengruppe und jeder der Verwaltungsrollen, die der Rollengruppe zugewiesen sind. Wenn Sie den Bereich für bestimmte Rollenzuweisungen ändern möchten, müssen Sie die später in diesem Thema folgenden Shell-Verfahren verwenden.


> [!IMPORTANT]
> Die Exchange-Verwaltungskonsole kann nicht zum Verwalten von Bereichen für Rollenzuweisungen zwischen Rollen und einer Rollengruppe verwendet werden, wenn Sie mehrere Bereiche oder exklusive Bereiche für diese Rollenzuweisungen mithilfe der Shell konfiguriert haben. Wenn Sie mehrere Bereiche oder exklusive Bereiche für diese Rollenzuweisungen konfiguriert haben, müssen Sie die Bereiche mithilfe der später in diesem Thema folgenden Verfahren für die Shell verwalten. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter <A href="understanding-management-role-scopes-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollenbereichen</A>.



1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie die Rollengruppe aus, für die Sie den Bereich ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie eine der beiden folgenden Optionen unter **Schreibbereich** aus:
    
      - Einen Schreibbereich im Dropdownfeld, in dem Sie entweder den Standardschreibbereich oder einen benutzerdefinierten Schreibbereich auswählen können.
    
      - **Organisationseinheit**   Wählen Sie diese Option aus, und stellen Sie eine Organisationseinheit bereit, wenn Sie dieser Rollengruppe eine Organisationseinheit als Bereich zuordnen wollen.

4.  Klicken Sie auf **Speichern**, um die Änderungen an der Rollengruppe zu speichern.

## Verwenden der Shell, um den Bereich aller Rollenzuweisungen für eine Rollengruppe gleichzeitig zu ändern

Rollenzuweisungen zwischen der Rollengruppe und den ihr zugewiesenen Rollen können den impliziten Bereich, den sie von den Rollen selbst erhalten, denselben benutzerdefinierten Bereich oder unterschiedliche benutzerdefinierte Bereiche verwenden. Weitere Informationen zu Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Die Bereiche für die Rollenzuweisungen werden mithilfe des Cmdlets **Set-ManagementRoleAssignment** verwaltet. Es ist nicht möglich, Bereiche mit dem Cmdlet **Set-RoleGroup** zu verwalten.

Wenn Sie den Bereich aller Rollenzuweisungen zwischen einer Rollengruppe und einer Gruppe von Verwaltungsrollen gleichzeitig ändern möchten, müssen Sie zuerst die Rollenzuweisungen für die Rollengruppe abrufen und anschließend den neuen Bereich für jede Zuweisung festlegen. Verwenden Sie zu diesem Zweck das Cmdlet **Get-ManagementRoleAssignment**, um die Rollenzuweisungen abzurufen, und übergeben sie diese anschließend mittels Pipelining an das Cmdlet **Set-ManagementRoleAssignment**.

Dieses Verfahren verwendet Pipelining und die Option *WhatIf*. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Optionen "WhatIf", "Confirm" und "ValidateOnly"](whatif-confirm-and-validateonly-switches-exchange-2013-help.md)

Verwenden Sie die folgende Syntax, um den Bereich aller Rollenzuweisungen für eine Rollengruppe gleichzeitig zu ändern.

    Get-ManagementRoleAssignment -RoleAssignee <name of role group> | Set-ManagementRoleAssignment -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuration scope name> -RecipientRelativeScopeWriteScope < MyDistributionGroups | Organization | Self> -ExclusiveRecipientWriteScope <exclusive recipient scope name> -ExclusiveConfigWriteScope <exclusive configuration scope name> -RecipientOrganizationalUnitScope <organizational unit>

Sie verwenden nur die zum Konfigurieren des zu verwendenden Bereichs erforderlichen Parameter. Wenn Sie beispielsweise den Empfängerbereich für alle Rollenzuweisungen der Rollengruppe "Sales Recipient Management" in "Direct Sales Employees" ändern möchten, müssen Sie den folgenden Befehl verwenden.

    Get-ManagementRoleAssignment -RoleAssignee "Sales Recipient Management" | Set-ManagementRoleAssignment -CustomRecipientWriteScope "Direct Sales Employees"


> [!NOTE]
> Mit der Option <EM>WhatIf</EM> können Sie sicherstellen, dass nur die Rollenzuweisungen geändert werden, die Sie tatsächlich ändern möchten. Führen Sie den oben beschriebenen Befehl mit der Option <EM>WhatIf</EM> aus, um die Ergebnisse zu überprüfen, und entfernen Sie die Option <EM>WhatIf</EM> anschließend, um die Änderungen anzuwenden.



Weitere Informationen zum Ändern von Verwaltungsrollenzuweisungen finden Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Verwenden der Shell, um den Bereich einzelner Rollenzuweisungen für eine Rollengruppe zu ändern

Rollenzuweisungen zwischen der Rollengruppe und den ihr zugewiesenen Rollen können den impliziten Bereich, den sie von den Rollen selbst erhalten, denselben benutzerdefinierten Bereich oder unterschiedliche benutzerdefinierte Bereiche verwenden. Weitere Informationen zu Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Die Bereiche für die Rollenzuweisungen werden mithilfe des Cmdlets **Set-ManagementRoleAssignment** verwaltet. Es ist nicht möglich, Bereiche mit dem Cmdlet **Set-RoleGroup** zu verwalten.

In diesem Verfahren werden Pipelining und das Cmdlet **Format-List** verwendet. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

Wenn Sie den Bereich einer Rollenzuweisung zwischen einer Rollengruppe und einer Verwaltungsrolle ändern möchten, müssen Sie zuerst den Namen der Rollenzuweisung ermitteln und anschließend den neuen Bereich für die Rollenzuweisung festlegen.

1.  Verwenden Sie den folgenden Befehl, um die Namen aller Rollenzuweisungen für eine Rollengruppe zu ermitteln. Indem Sie die Verwaltungsrollenzuweisungen mithilfe des Pipelinings an das Cmdlet **Format-List** übergeben, können Sie den vollständigen Namen der Zuweisung anzeigen.
    
        Get-ManagementRoleAssignment -RoleAssignee <role group name> | Format-List Name

2.  Ermitteln Sie den Namen der Rollenzuweisung, die Sie ändern möchten. Verwenden Sie den Namen der Rollenzuweisung im nächsten Schritt.

3.  Verwenden Sie die folgende Syntax, um den Bereich einer einzelnen Zuweisung festzulegen.
    
        Set-ManagementRoleAssignment <role assignment name> -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuration scope name> -RecipientRelativeScopeWriteScope < MyDistributionGroups | Organization | Self> -ExclusiveRecipientWriteScope <exclusive recipient scope name> -ExclusiveConfigWriteScope <exclusive configuration scope name> -RecipientOrganizationalUnitScope <organizational unit>

Sie verwenden nur die zum Konfigurieren des zu verwendenden Bereichs erforderlichen Parameter. Wenn Sie beispielsweise den Empfängerbereich für die Rollenzuweisung "Mail Recipients\_Sales Recipient Management" in "All Sales Employees" ändern möchten, müssen Sie den folgenden Befehl verwenden.

    Set-ManagementRoleAssignment "Mail Recipients_Sales Recipient Management" -CustomRecipientWriteScope "All Sales Employees"

Weitere Informationen zum Ändern von Verwaltungsrollenzuweisungen finden Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass der Bereich einer Rollenzuweisung für eine Rollengruppe erfolgreich geändert wurde:

  - Gehen Sie wie folgt vor, wenn Sie den Bereich für die Rollengruppe mit der Exchange-Verwaltungskonsole konfiguriert haben:
    
    1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen**\> **Administratorrollen**. Alle Rollengruppen in Ihrer Organisation werden hier aufgelistet.
    
    2.  Wählen Sie eine Rollengruppe aus, um den Bereich anzuzeigen, der für die Rollengruppe konfiguriert ist.

  - Gehen Sie wie folgt vor, wenn Sie den Bereich für die Rollengruppe mit der Shell konfiguriert haben:
    
    1.  Führen Sie folgenden Befehl in der Shell aus.
        
            Get-ManagementRoleAssignment -RoleAssignee <role group name> | Format-Table *WriteScope
    
    2.  Vergewissern Sie sich, dass der Schreibbereich für die Rollenzuweisungen in den Bereich geändert wurde, den Sie angegeben haben.

## Hinzufügen oder Entfernen einer Rollengruppenstellvertretung

Rollengruppenstellvertretungen sind Benutzer oder universelle Sicherheitsgruppen (Universal Security Groups, USGs), die Mitglieder zu Rollengruppen hinzufügen oder aus ihnen entfernen sowie die Eigenschaften einer Rollengruppe ändern können. Durch Hinzufügen oder Entfernen von Rollengruppenstellvertretern können Sie steuern, welche Personen eine Rollengruppe verwalten dürfen.


> [!IMPORTANT]
> Nachdem Sie einen Stellvertreter zu einer Rollengruppe hinzugefügt haben, kann die Rollengruppe nur von den Stellvertretern der Gruppe oder von Benutzern, denen entweder direkt oder indirekt die Verwaltungsrolle "Rollenverwaltung" zugewiesen wurde, verwaltet werden.<BR>Falls einem Benutzer entweder direkt oder indirekt die Verwaltungsrolle "Rollenverwaltung" zugewiesen wurden, dieser jedoch nicht als Stellvertreter der Rollengruppe hinzugefügt wurde, muss er bei den Cmdlets <STRONG>Add-RoleGroupMember</STRONG>, <STRONG>Remove-RoleGroupMember</STRONG>, <STRONG>Update-RoleGroupMember</STRONG> und <STRONG>Set-RoleGroup</STRONG> jeweils die Option <EM>BypassSecurityGroupManagerCheck</EM> verwenden, um die Rollengruppe verwalten zu können.




> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht dazu verwendet werden, eine Stellvertretung zu einer Rollengruppe hinzuzufügen.



## Verwenden der Shell zum Hinzufügen eines Stellvertreters zu einer Rollengruppe

Sie verwenden den Parameter *ManagedBy* für das Cmdlet **Set-RoleGroup**, um die Liste der Stellvertreter für eine Rollengruppe zu ändern. Der Parameter *ManagedBy* überschreibt die gesamte Stellvertreterliste für die Rollengruppe. Falls Sie einzelne Stellvertreter zu einer Rollengruppe hinzufügen möchten, statt die gesamte Stellvertreterliste zu ersetzen, führen Sie die folgenden Schritte aus:

1.  Speichern Sie die Rollengruppe mit dem folgenden Befehl in einer Variablen.
    
        $RoleGroup = Get-RoleGroup <role group name>

2.  Fügen Sie mit dem folgenden Befehl den Stellvertreter zu der in der Variablen gespeicherten Rollengruppe hinzu.
    
        $RoleGroup.ManagedBy += (Get-User <user to add>).Identity
    

    > [!NOTE]
    > Verwenden Sie das Cmdlet <STRONG>Get-Group</STRONG>, wenn Sie eine USG hinzufügen möchten.



3.  Wiederholen Sie Schritt 2 für jeden Stellvertreter, den Sie hinzufügen möchten.

4.  Wenden Sie die neue Liste der Stellvertreter mithilfe des folgenden Befehls auf die eigentliche Rollengruppe an.
    
        Set-RoleGroup <role group name> -ManagedBy $RoleGroup.ManagedBy

In diesem Beispiel wird der Benutzer David Strome als Stellvertreter der Rollengruppe Organisationsverwaltung hinzugefügt.

    $RoleGroup = Get-RoleGroup "Organization Management"
    $RoleGroup.ManagedBy += (Get-User "David Strome").Identity
    Set-RoleGroup "Organization Management" -ManagedBy $RoleGroup.ManagedBy

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RoleGroup](https://technet.microsoft.com/de-de/library/dd638182\(v=exchg.150\)).

## Verwenden der Shell zum Entfernen eines Stellvertreters aus einer Rollengruppe

Sie verwenden den Parameter *ManagedBy* für das Cmdlet **Set-RoleGroup**, um die Liste der Stellvertreter für eine Rollengruppe zu ändern. Der Parameter *ManagedBy* überschreibt die gesamte Stellvertreterliste für die Rollengruppe. Falls Sie einzelne Stellvertreter aus einer Rollengruppe entfernen möchten, statt die gesamte Stellvertreterliste zu ersetzen, führen Sie die folgenden Schritte aus:

1.  Speichern Sie die Rollengruppe mit dem folgenden Befehl in einer Variablen.
    
        $RoleGroup = Get-RoleGroup <role group name>

2.  Entfernen Sie mit dem folgenden Befehl den Stellvertreter aus der in der Variablen gespeicherten Rollengruppe.
    
        $RoleGroup.ManagedBy -= (Get-User <user to remove>).Identity
    

    > [!NOTE]
    > Verwenden Sie das Cmdlet <STRONG>Get-Group</STRONG>, wenn Sie eine USG entfernen möchten.



3.  Wiederholen Sie Schritt 2 für jeden Stellvertreter, den Sie entfernen möchten.

4.  Wenden Sie die neue Liste der Stellvertreter mithilfe des folgenden Befehls auf die eigentliche Rollengruppe an.
    
        Set-RoleGroup <role group name> -ManagedBy $RoleGroup.ManagedBy

In diesem Beispiel wird der Benutzer David Strome als Stellvertreter der Rollengruppe Organisationsverwaltung entfernt.

    $RoleGroup = Get-RoleGroup "Organization Management"
    $RoleGroup.ManagedBy -= (Get-User "David Strome").Identity
    Set-RoleGroup "Organization Management" -ManagedBy $RoleGroup.ManagedBy

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RoleGroup](https://technet.microsoft.com/de-de/library/dd638182\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass die Stellvertretungsliste für eine Rollengruppe erfolgreich geändert wurde:

1.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-RoleGroup <role group name> | Format-List ManagedBy

2.  Vergewissern Sie sich, dass in der Liste, die für die Eigenschaft *ManagedBy* erstellt wurde, nur Stellvertretungen enthalten sind, die die Rollengruppe verwalten dürfen.

