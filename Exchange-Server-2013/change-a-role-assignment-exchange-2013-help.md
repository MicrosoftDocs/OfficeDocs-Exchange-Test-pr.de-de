---
title: 'Ändern einer Rollenzuweisung: Exchange 2013 Help'
TOCTitle: Ändern einer Rollenzuweisung
ms:assetid: 0fa77efc-e393-461f-b3c0-232cc56cee85
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335096(v=EXCHG.150)
ms:contentKeyID: 50475017
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern einer Rollenzuweisung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungsrollenzuweisungen weisen einem Rollenempfänger eine Verwaltungsrolle zu. Indem Sie die Rollenzuweisung ändern, können Sie steuern, welche Objekte Rollenempfänger ändern können, denen eine Rolle zugewiesen ist. Auf Rollenzuweisungen angewendete Verwaltungsrollenbereiche setzen den impliziten Schreibbereich der Rolle außer Kraft. Der implizite Lesebereich der Rolle hat jedoch weiterhin Gültigkeit. Bereiche, die Sie anwenden, können keine Objekte zurückgeben, die sich außerhalb des impliziten Lesebereichs der Rolle befinden.

Weitere Informationen zu Verwaltungsrollenbereichen und -zuweisungen in Microsoft Exchange Server 2013 finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollenzuweisungen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollenzuweisungen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren oder Deaktivieren einer Rollenzuweisung

Rollenzuweisungen sind standardmäßig aktiviert. Dies bedeutet, dass die zugeordnete Rolle auf den Rollenempfänger angewendet wird, dem die Rolle zugewiesen ist. Wenn eine Rollenzuweisung deaktiviert ist, wird die zugeordnete Rolle nicht auf den Rollenempfänger angewendet.

Verwenden Sie die folgende Syntax, um eine Rollenzuweisung zu aktivieren.

```powershell
Set-ManagementRoleAssignment <role assignment> -Enabled $true
```

Verwenden Sie die folgende Syntax, um eine Rollenzuweisung zu deaktivieren.

```powershell
Set-ManagementRoleAssignment <role assignment> -Enabled $false
```

In diesem Beispiel wird die Rollenzuweisung "Help Desk Assignment" deaktiviert.

```powershell
Set-ManagementRoleAssignment "Help Desk Assignment" -Enabled $false
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern der Verwaltungsrolle oder des Rollenempfängers einer Rollenzuweisung

Sie können die Verwaltungsrolle sowie den Rollenempfänger nicht ändern, die für eine Rollenzuweisung angegeben sind. Wenn Sie eine Rollenzuweisung einer anderen Rolle oder einem anderen Rollenempfänger zuordnen möchten, müssen Sie eine neue Rollenzuweisung erstellen und dann die alte löschen. Weitere Informationen zum Hinzufügen und Entfernen von Rollenzuweisungen finden Sie unter den folgenden Themen:

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

Wenn Sie Zuweisungen direkt für einen Benutzer oder eine universelle Sicherheitsgruppe (Universal Security Group, USG) erstellt haben, sollten Sie in Betracht ziehen, stattdessen Verwaltungsrollengruppen und Zuweisungsrichtlinien für Verwaltungsrollen zu verwenden. Mit Rollengruppen und Zuweisungsrichtlinien können Sie Ihr Berechtigungsmodell vereinfachen und die Anzahl der Rollenzuweisungen reduzieren, die Sie verwalten müssen. Weitere Informationen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Verwenden der Shell zum Ändern eines vordefinierten relativen Bereichs für eine Rollenzuweisung

Sie können einen vordefinierten relativen Bereich für eine Rollenzuweisung ändern oder hinzufügen. Wenn Sie einen vordefinierten Bereich hinzufügen oder ändern, werden ggf. alle zuvor angegebenen Empfängerbereiche von der Rollenzuweisung entfernt. Eine Liste vordefinierter Bereiche und ihrer Beschreibungen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Verwenden Sie die folgende Syntax, um einen vordefinierten Bereich für eine Rollenzuweisung zu ändern oder hinzuzufügen.

    Set-ManagementRoleAssignment <assignment name> -RecipientRelativeWriteScope < MyDistributionGroups | Organization | Self >

In diesem Beispiel wird der vordefinierte Bereich für die Rollenzuweisung "John's Assignment" zu "MyDistributionGroups" geändert.

```powershell
Set-ManagementRoleAssignment "John's Assignment" - RecipientRelativeWriteScope MyDistributionGroups
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern eines filterbasierten Empfängerbereichs für eine Rollenzuweisung

Sie können einen neuen empfängerfilterbasierten Bereich angeben oder den filterbasierten Empfängerbereich ändern, der bereits auf die Rollenzuweisung angewendet wurde. Wenn Sie einen filterbasierten Empfängerbereich hinzufügen, werden ggf. alle zuvor definierten Empfängerbereiche von der Rollenzuweisung entfernt.

Verwenden Sie die folgende Syntax, um einen neuen filterbasierten Empfängerbereich anzugeben oder einen vorhandenen zu ersetzen.

    Set-ManagementRoleAssignment <assignment name> -CustomRecipientWriteScope <role scope name>

In diesem Beispiel wird der filterbasierten Empfängerbereich "Redmond Recipients" hinzugefügt, oder der Bereich wird in "Redmond Recipients" geändert.

    Set-ManagementRoleAssignment "Redmond Recipient Administrators Assignment" -CustomRecipientWriteScope "Redmond Recipients"

Wenn Sie den filterbasierten Empfängerbereich beibehalten möchten, der auf die Rollenzuweisung angewendet wird, aber den Empfängerfilter ändern möchten, mit dem passende Empfängerobjekte ermittelt werden, müssen Sie den Empfängerfilter für den Bereich ändern. Weitere Informationen zum Ändern von Bereichen finden Sie unter [Ändern eines Rollenbereichs](change-a-role-scope-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern des serverfilter- oder listenbasierten Konfigurationsbereichs einer Rollenzuweisung

Sie können einen neuen serverfilter- oder listenbasierten Konfigurationsbereich angeben oder den Bereich ändern, der bereits auf die Rollenzuweisung angewendet wurde. Wenn Sie den Konfigurationsbereich hinzufügen oder ändern, werden ggf. alle zuvor angegebenen Konfigurationsbereiche von der Rollenzuweisung entfernt.

Verwenden Sie die folgende Syntax, um einen neuen Konfigurationsbereich anzugeben oder einen vorhandenen zu ersetzen.

```powershell
Set-ManagementRoleAssignment <assignment name> -CustomConfigWriteScope <role scope name>
```

In diesem Beispiel wird der Konfigurationsbereich "Redmond Servers" hinzugefügt, oder der Konfigurationsbereich wird in "Redmond Servers" geändert.

    Set-ManagementRoleAssignment "Redmond Administrators Assignment" -CustomConfigWriteScope "Redmond Servers"

Wenn Sie den Konfigurationsbereich beibehalten möchten, der auf die Rollenzuweisung angewendet wird, aber den Serverfilter oder die Serverliste für den Bereich ändern möchten, müssen Sie den Konfigurationsbereich ändern. Weitere Informationen zum Ändern von Bereichen finden Sie unter [Ändern eines Rollenbereichs](change-a-role-scope-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern des datenbankfilter- oder listenbasierten Konfigurationsbereichs für eine Rollenzuweisung

Sie können einen neuen datenbankfilter- oder listenbasierten Konfigurationsbereich angeben oder den Bereich ändern, der bereits auf die Rollenzuweisung angewendet wurde. Wenn Sie den Konfigurationsbereich hinzufügen oder ändern, werden ggf. alle zuvor angegebenen Konfigurationsbereiche von der Rollenzuweisung entfernt.

Verwenden Sie die folgende Syntax, um einen neuen Konfigurationsbereich anzugeben oder einen vorhandenen zu ersetzen.

```powershell
Set-ManagementRoleAssignment <assignment name> -CustomConfigWriteScope <role scope name>
```

In diesem Beispiel wird der Konfigurationsbereich "Redmond Databases" hinzugefügt, oder der Konfigurationsbereich wird in "Redmond Databases" geändert.

```powershell
Set-ManagementRoleAssignment "Redmond Database Admins" -CustomConfigWriteScope "Redmond Databases"
```

Wenn Sie den Konfigurationsbereich beibehalten möchten, der auf die Rollenzuweisung angewendet wird, aber den Datenbankfilter oder die Datenbankliste für den Bereich ändern möchten, müssen Sie den Konfigurationsbereich ändern. Weitere Informationen zum Ändern von Bereichen finden Sie unter [Ändern eines Rollenbereichs](change-a-role-scope-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern der Organisationseinheit einer Rollenzuweisung

Sie können eine neue Organisationseinheit hinzufügen oder eine Organisationseinheit ändern, die bereits auf die Rollenzuweisung angewendet wird. Wenn Sie eine neue OU angeben, werden ggf. alle zuvor angegebenen Empfängerbereiche von der Rollenzuweisung entfernt.

Verwenden Sie die folgende Syntax, um eine OU für eine Rollenzuweisung zu ändern oder eine neue hinzuzufügen.

```powershell
Set-ManagementRoleAssignment <assignment name> -RecipientOrganizationalUnitScope <OU>
```

In diesem Beispiel wird die OU "Engineering\\Users" in der Domäne "contoso.com" der Rollenzuweisung "Engineering Help Desk" hinzugefügt.

    Set-ManagementRoleAssignment "Engineering Help Desk" -RecipientOrganizationalUnitScope contoso.com/Engineering/Users

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

## Verwenden der Shell zum Ändern eines exklusiven Empfänger- oder Konfigurationsbereichs

Zum Ändern eines exklusiven Empfänger- oder Konfigurationsbereichs können Sie die in den oben genannten Abschnitten "Verwenden der Shell zum Ändern eines filterbasierten Empfängerbereichs für eine Rollenzuweisung", "Verwenden der Shell zum Ändern des serverfilter- oder listenbasierten Konfigurationsbereichs einer Rollenzuweisung" und "Verwenden der Shell zum Ändern des datenbankfilter- oder listenbasierten Konfigurationsbereichs für eine Rollenzuweisung" dargestellten Verfahren verwenden. Der einzige Unterschied besteht darin, dass Sie beim Ändern eines exklusiven Bereichs die folgenden exklusiven Parameter angeben müssen, abhängig davon, ob Sie einen exklusiven Empfängerbereich oder einen exklusiven Konfigurationsbereich ändern:

  - **Exklusive Empfängerbereiche**   Verwenden Sie den Parameter *ExclusiveRecipientWriteScope* anstelle des Parameters *CustomRecipientWriteScope*.

  - **Exklusive Server- und Datenbankkonfigurationsbereiche**   Verwenden Sie den Parameter *ExclusiveConfigWriteScope* anstelle des Parameters *CustomConfigWriteScope*.

Wie bei regulären Empfänger- und Konfigurationsbereichen werden beim Hinzufügen oder Ändern eines exklusiven Bereichs ggf. alle zuvor definierten Empfänger- oder Konfigurationsbereiche ersetzt.

In diesem Beispiel wird ein exklusiver Empfängerschreibbereich geändert.

    Set-ManagementRoleAssignment "Exclusive Executive Users" -ExclusiveRecipientWriteScope "Exclusive Executives"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\)).

