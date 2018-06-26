---
title: 'Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe: Exchange 2013 Help'
TOCTitle: Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe
ms:assetid: ae5608de-a141-4714-8876-bce7d2a22cb5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351056(v=EXCHG.150)
ms:contentKeyID: 50476476
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-03_

Mithilfe von Verwaltungsrollenzuweisungen können Sie einem Benutzer oder einer universellen Sicherheitsgruppe (Universal Security Group, USG) eine Verwaltungsrolle zuweisen. Durch das Zuweisen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe ermöglichen Sie den Benutzern das Ausführen von Aufgaben – abhängig davon, welche Cmdlets oder Skripts sowie Parameter für die Verwaltungsrolle definiert sind.

Wenn Sie einer Verwaltungsrollengruppe Rollen oder eine Zuweisungsrichtlinie für Verwaltungsrollen zuweisen möchten, finden Sie weitere Informationen in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

Wenn Sie Mitglieder zu einer Rollengruppe hinzufügen oder einem Endbenutzer eine Rollenzuweisungsrichtlinie zuordnen möchten, finden Sie weitere Informationen in diesen Themen:

  - [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md)

  - [Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md)

Weitere Informationen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollenzuweisungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Wenngleich Sie Benutzern und universellen Sicherheitsgruppen Rollen direkt zuweisen können, besteht die empfohlene Methode zum Gewähren von Berechtigungen für Administratoren und Endbenutzer darin, Verwaltungsrollengruppen und Zuweisungsrichtlinien für Verwaltungsrollen zu verwenden. Wenn Sie Rollengruppen und Zuweisungsrichtlinien verwenden, vereinfachen Sie Ihr Berechtigungsmodell.

  - Rollenzuweisungen sind additiv. Dies bedeutet, dass alle Rollen bei ihrer Auswertung addiert werden. Wenn einem Benutzer zwei Rollen zugewiesen werden und nur eine von ihnen ein Cmdlet enthält, steht das Cmdlet dem Benutzer dennoch zur Verfügung.
    
    Standardmäßig bieten Rollenzuweisungen nicht die Möglichkeit, anderen Benutzern Rollen zuzuweisen. Informationen dazu, wie Sie einem Benutzer das Zuweisen von Rollen zu anderen Benutzern oder universellen Sicherheitsgruppen zu ermöglichen, finden Sie unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).

  - Wenn Sie eine Zuweisung mit einem Bereich erstellen, setzt der Bereich den impliziten Schreibbereich der Rolle außer Kraft. Der implizite Lesebereich der Rolle hat jedoch weiterhin Gültigkeit. Der neue Bereich kann keine Objekte außerhalb des impliziten Lesebereichs der Rolle zurückgeben. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

  - Alle in diesem Thema genannten Verfahren verwenden den Parameter *SecurityGroup* zum Zuweisen von Rollen zu einer universellen Sicherheitsgruppe. Wenn Sie die Rolle einem spezifischen Benutzer zuweisen möchten, verwenden Sie anstelle von *User* den Parameter *SecurityGroup*. Die weitere Syntax für jeden Befehl ist identisch.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Rollenzuweisung ohne Bereich

Sie können eine Rollenzuweisung ohne Bereich erstellen. Wenn Sie dies machen, gelten die impliziten Lese- und Schreibbereiche der Rolle.

Verwenden Sie die folgende Syntax, um einer universellen Sicherheitsgruppe eine Rolle ohne Bereich zuzuweisen.

    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name>

In diesem Beispiel wird die Rolle "Exchange Servers" der universellen Sicherheitsgruppe "SeattleAdmins" zugewiesen.

    New-ManagementRoleAssignment -Name "Exchange Servers_SeattleAdmins" -SecurityGroup SeattleAdmins -Role "Exchange Servers"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem vordefinierten relativen Bereich

Wenn ein vordefinierter relativer Bereich Ihren Geschäftsanforderungen entspricht, können Sie diesen Bereich auf die Rollenzuweisung anwenden, statt einen benutzerdefinierten Bereich zu erstellen. Eine Liste vordefinierter Bereiche und ihrer Beschreibungen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Verwenden Sie die folgende Syntax, um einer universellen Sicherheitsgruppe eine Rolle mit einem vordefinierten Bereich zuzuweisen.

    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup < USG> -Role <role name> -RecipientRelativeWriteScope < MyDistributionGroups | Organization | Self >

In diesem Beispiel wird die Rolle "Exchange Servers" der universellen Sicherheitsgruppe "SeattleAdmins" zugewiesen und der vordefinierte Bereich "Organization" angewendet.

    New-ManagementRoleAssignment -Name "Exchange Servers_SeattleAdmins" -SecurityGroup SeattleAdmins -Role "Exchange Servers" -RecipientRelativeWriteScope Organization

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem filterbasierten Empfängerbereich

Wenn Sie einen filterbasierten Empfängerbereich erstellt haben und diesen bei einer Rollenzuweisung verwenden möchten, müssen Sie den Bereich unter Verwendung des Parameters *CustomRecipientWriteScope* in den Befehl zum Zuweisen der Rolle zu einer universellen Sicherheitsgruppe einschließen. Bei Verwendung des Parameters *CustomRecipientWriteScope* kann der Parameter *RecipientOrganizationalUnitScope* nicht verwendet werden.

Bevor Sie einer Rollenzuweisung einen Bereich hinzufügen können, müssen Sie einen erstellen. Weitere Informationen finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

Verwenden Sie die folgende Syntax, um einer universellen Sicherheitsgruppe eine Rolle mit filterbasiertem Empfängerbereich zuzuweisen.

    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup < USG> -Role <role name> -CustomRecipientWriteScope <role scope name>

In diesem Beispiel wird die Rolle "Mail Recipients" der universellen Sicherheitsgruppe "Seattle Recipient Admins" zugewiesen und der Bereich "Seattle Recipients" angewendet.

    New-ManagementRoleAssignment -Name "Mail Recipients_Seattle Recipient Admins" -SecurityGroup "Seattle Recipient Admins" -Role "Mail Recipients" -CustomRecipientWriteScope "Seattle Recipients"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem filter- oder listenbasierten Server- oder Datenbankkonfigurationsbereich

Wenn Sie einen filter- oder listenbasierten Server- oder Datenbankkonfigurationsbereich erstellt haben und diesen bei einer Rollenzuweisung verwenden möchten, müssen Sie den Bereich unter Verwendung des Parameters *CustomConfigWriteScope* in den Befehl zum Zuweisen einer Rolle zu einer universellen Sicherheitsgruppe einschließen.

Bevor Sie einer Rollenzuweisung einen Bereich hinzufügen können, müssen Sie einen erstellen. Weitere Informationen finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

Verwenden Sie die folgende Syntax, um einer universellen Sicherheitsgruppe eine Rolle mit einem Konfigurationsbereich zuzuweisen.

    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name> -CustomConfigWriteScope <role scope name>

In diesem Beispiel wird die Rolle "Exchange Servers" der universellen Sicherheitsgruppe "MailboxAdmins" zugewiesen und der Bereich "Mailbox Servers" angewendet.

    New-ManagementRoleAssignment -Name "Exchange Servers_MailboxAdmins" -SecurityGroup MailboxAdmins -Role "Exchange Servers" -CustomConfigWriteScope "Mailbox Servers"

Das vorstehende Beispiel zeigt, wie eine Rollenzuweisung mit einem Serverkonfigurationsbereich hinzugefügt werden kann. Die Syntax zum Hinzufügen eines Datenbankkonfigurationsbereich ist identisch. Anstelle eines Serverbereichs geben Sie den Namen eines Datenbankbereichs an.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit einem OU-Bereich

Wenn Sie den Schreibbereich einer Rolle auf eine Organisationseinheit (Organizational Unit, OU) beschränken möchten, können Sie die OU direkt im Parameter *RecipientOrganizationalUnitScope* angeben. Bei Verwendung des Parameters *RecipientOrganizationalUnitScope* kann der Parameter *CustomRecipientWriteScope* nicht verwendet werden.

Verwenden Sie die folgende Syntax, um einer universellen Sicherheitsgruppe eine Rolle zuzuweisen und den Schreibbereich einer Rolle auf eine spezifische OU zu beschränken.

    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name> -RecipientOrganizationalUnitScope <OU>

In diesem Beispiel wird die Rolle "Mail Recipients" der universellen Sicherheitsgruppe "SalesRecipientAdmins" zugewiesen und der Bereich auf die OU "sales/user" in der Domäne "contoso.com" festgelegt.

    New-ManagementRoleAssignment -Name "Mail Recipients_SalesRecipientAdmins" -SecurityGroup SalesRecipientAdmins -Role "Mail Recipients" -RecipientOrganizationalUnitScope contoso.com/sales/users

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

## Erstellen einer Rollenzuweisung mit exklusivem Empfänger- oder Konfigurationsbereich

Um eine exklusive Rollenzuweisung mit einem exklusiven Empfänger- oder Konfigurationsbereich zu erstellen, gelten die gleichen Verfahren, die in den Abschnitten Erstellen einer Rollenzuweisung mit einem filterbasierten Empfängerbereich und Erstellen einer Rollenzuweisung mit einem filter- oder listenbasierten Server- oder Datenbankkonfigurationsbereich vorgestellt wurden. Der einzige Unterschied besteht darin, dass beim Erstellen einer Rollenzuweisung mit exklusivem Bereich die folgenden exklusiven Parameter angegeben werden müssen – abhängig davon, ob Sie einen exklusiven Empfänger- oder Konfigurationsbereich verwenden:

  - **Exklusive Empfängerbereiche**   Verwenden Sie den Parameter *ExclusiveRecipientWriteScope* anstelle des Parameters *CustomRecipientWriteScope*.

  - **Exklusive Konfigurationsbereiche**   Verwenden Sie den Parameter *ExclusiveConfigWriteScope* anstelle des Parameters *CustomConfigWriteScope*.

Wenn Sie dieses Verfahren ausführen, kann der der Rolle zugewiesene Benutzer Aktionen für die Objekte ausführen, die im exklusiven Bereich enthalten sind. Weitere Informationen zu exklusiven Bereichen finden Sie unter [Grundlegendes zu exklusiven Bereichen](understanding-exclusive-scopes-exchange-2013-help.md).

Eine Rollenzuweisung kann nicht sowohl mit exklusiven als auch mit regulären Bereichen erstellt werden.

In diesem Beispiel wird die Rolle "Mail Recipients" der universellen Sicherheitsgruppe "Protected User Admins" zugewiesen und der exklusive Bereich "Protected Users" angewendet.

    New-ManagementRoleAssignment -Name "Mail Recipients_Protected User Admins" -SecurityGroup "Protected User Admins" -Role "Mail Recipients" -ExclusiveRecipientWriteScope "Protected Users"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\)).

