---
title: 'Erstellen eines regulären oder exklusiven Bereichs: Exchange 2013 Help'
TOCTitle: Erstellen eines regulären oder exklusiven Bereichs
ms:assetid: b97a5be3-15cc-4954-ba30-a824a95e21be
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351083(v=EXCHG.150)
ms:contentKeyID: 50476557
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines regulären oder exklusiven Bereichs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Verwaltungsrollenbereiche bestimmen, welche Objekte einem Benutzer zur Verfügung gestellt werden, damit die Objekte mithilfe der ihm zugeordneten Cmdlets und Parameter geändert werden können. Durch das Hinzufügen eines Verwaltungsbereichs können Sie Verwaltungsrollenzuweisungen konfigurieren, sodass Benutzer bestimmte Server, Datenbanken, Empfänger und andere Objekte in Ihrer Organisation verwalten, jedoch keine anderen Objekte ändern können.


> [!IMPORTANT]
> Beim Erstellen eines regulären oder exklusiven Bereichs wird der Schreibbereich außer Kraft gesetzt, der für die von Ihnen zugewiesene Verwaltungsrolle definiert ist. Der für die Verwaltungsrolle konfigurierte Lesebereich kann nicht außer Kraft gesetzt werden.



Sie können einen benutzerdefinierten Verwaltungsbereich erstellen und eine Verwaltungsrollenzuweisung hinzufügen oder ändern. Informationen zum Erstellen einer Verwaltungsrollenzuweisung mit einem vordefinierten oder einem OU-Verwaltungsbereich (Organizational Unit, Organisationseinheit) finden Sie unter [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md).

Weitere Informationen zu Verwaltungsrollenbereichen und -zuweisungen in Microsoft Exchange Server 2013 finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Bereichen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsbereiche" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines benutzerdefinierten Bereichs

Wählen Sie zum Erstellen eines benutzerdefinierten Bereichs einen der folgenden Bereichstypen.

## Filterbasierter Empfängerbereich

Filterbasierte Empfängerbereiche werden unter Verwendung des Parameters *RecipientRestrictionFilter* mit dem Cmdlet **New-ManagementScope** erstellt. Beim Erstellen eines Empfängerfilters können Sie neben den zu filternden Empfängereigenschaften die Organisationseinheit angeben, in welcher die Filterabfrage ausgeführt wird. Bei Angabe einer Basisorganisationseinheit schränken Sie den Schreibbereich der Rolle weiter ein.

Weitere Informationen zu Verwaltungsbereichsfiltern finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Verwenden Sie zum Erstellen eines Einschränkungsfilterbereichs für Domänen mit einer Basisorganisationseinheit die folgende Syntax.

```powershell
    New-ManagementScope -Name <scope name> -RecipientRestrictionFilter <filter query> [-RecipientRoot <OU>]
```

In diesem Beispiel wird ein Bereich mit allen Postfächern innerhalb von "contoso.com/Sales OU" erstellt.

```powershell
    New-ManagementScope -Name "Mailboxes in Sales OU" -RecipientRestrictionFilter { RecipientType -eq 'UserMailbox' } -RecipientRoot "contoso.com/Sales OU"
```

> [!NOTE]
> Der Parameter <EM>RecipientRoot</EM> kann ausgelassen werden, wenn der Filter nicht nur innerhalb einer bestimmten Organisationseinheit, sondern auf den gesamten impliziten Lesebereich der Verwaltungsrolle angewendet werden soll.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Filterbasierter Serverkonfigurationsbereich

Filterbasierte Serverkonfigurationsbereiche werden unter Verwendung des Parameters *ServerRestrictionFilter* mit dem Cmdlet **New-ManagementScope** erstellt. Ein Serverfilter ermöglicht das Erstellen eines Bereichs, der nur auf Server angewendet wird, die mit den angegebenen Filterkriterien übereinstimmen.

Weitere Informationen zu Verwaltungsbereichsfiltern und eine Liste filterbarer Servereigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Verwenden Sie zum Erstellen eines Serverfilterbereichs die folgende Syntax.

```powershell
New-ManagementScope -Name <scope name> -ServerRestrictionFilter <filter query>
```

In diesem Beispiel wird ein Bereich erstellt, der alle Server im Active Directory-Standort "CN=Redmond,CN=Sites,CN=Configuration,DC=contoso,DC=com'" umfasst.

```powershell
    New-ManagementScope -Name "Servers in Seattle AD site" -ServerRestrictionFilter { ServerSite -eq 'CN=Redmond,CN=Sites,CN=Configuration,DC=contoso,DC=com' }
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Listenbasierter Serverkonfigurationsbereich

Listenbasierte Serverkonfigurationsbereiche werden unter Verwendung des Parameters *ServerList* mit dem Cmdlet **New-ManagementScope** erstellt. Ein listenbasierter Serverbereich ermöglicht das Erstellen eines Bereichs, der nur auf die in einer Liste angegebenen Server angewendet wird.

Verwenden Sie zum Erstellen eines listenbasierten Serverbereichs die folgende Syntax.

```powershell
New-ManagementScope -Name <scope name> -ServerList <server 1>, <server 2...>
```

In diesem Beispiel wird ein Bereich erstellt, der nur auf "MBX1", "MBX3" und "MBX5" angewendet wird.

```powershell
New-ManagementScope -Name "Mailbox servers" -ServerList MBX1,MBX3,MBX5
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Filterbasierter Datenbankkonfigurationsbereich

Filterbasierte Datenbankkonfigurationsbereiche werden unter Verwendung des Parameters *DatabaseRestrictionFilter* mit dem Cmdlet **New-ManagementScope** erstellt. Ein Datenbankfilter ermöglicht das Erstellen eines Bereichs, der nur auf Datenbanken angewendet wird, die mit den angegebenen Filterkriterien übereinstimmen.


> [!IMPORTANT]
> Die zu Datenbankbereichen zugeordneten Rollenzuweisungen werden nur auf Benutzer angewendet, die eine Verbindung mit Servern herstellen, auf denen Microsoft Exchange Server 2010 Service Pack&nbsp;1 (SP1) oder höher oder Exchange 2013 ausgeführt wird. Wenn ein Benutzer, dem eine Rollenzuweisung mit einem zugeordneten Datenbankbereich zugewiesen wurde, eine Verbindung mit einem Server herstellt, auf dem eine ältere Version als Exchange 2010 SP1 ausgeführt wird, dann wird die Rollenzuweisung nicht auf den Benutzer angewendet. Dem Benutzer werden dann keine von der Rollenzuweisung bereitgestellten Berechtigungen erteilt.



Weitere Informationen zu Verwaltungsbereichsfiltern und eine Liste filterbarer Datenbankeigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Verwenden Sie zum Erstellen eines Datenbankeinschränkungsfilters die folgende Syntax.

```powershell
New-ManagementScope -Name <scope name> -DatabaseRestrictionFilter <filter query>
```

In diesem Beispiel wird ein Bereich mit allen Datenbanken erstellt, deren Eigenschaft **Name** die Zeichenfolge "Executive" enthält.

```powershell
    New-ManagementScope -Name "Executive Databases" -DatabaseRestrictionFilter { Name -Like '*Executive*' }
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Listenbasierter Datenbankkonfigurationsbereich

Listenbasierte Datenbankkonfigurationsbereiche werden unter Verwendung des Parameters *DatabaseList* mit dem Cmdlet **New-ManagementScope** erstellt. Ein listenbasierter Datenbankbereich ermöglicht das Erstellen eines Bereichs, der nur auf die in einer Liste angegebenen Datenbanken angewendet wird.


> [!IMPORTANT]
> Die zu Datenbankbereichen zugeordneten Rollenzuweisungen werden nur auf Benutzer angewendet, die eine Verbindung mit Servern herstellen, auf denen Microsoft Exchange Server 2010 Service Pack&nbsp;1 (SP1) oder höher oder Exchange 2013 ausgeführt wird. Wenn ein Benutzer, dem eine Rollenzuweisung mit einem zugeordneten Datenbankbereich zugewiesen wurde, eine Verbindung mit einem Server herstellt, auf dem eine ältere Version als Exchange 2010 SP1 ausgeführt wird, dann wird die Rollenzuweisung nicht auf den Benutzer angewendet. Dem Benutzer werden dann keine von der Rollenzuweisung bereitgestellten Berechtigungen erteilt.



Verwenden Sie zum Erstellen eines listenbasierten Datenbankbereichs die folgende Syntax.

```powershell
New-ManagementScope -Name <scope name> -DatabaseList <database 1>, <database 2...>
```

In diesem Beispiel wird ein Bereich erstellt, der nur auf die Datenbanken "Database 1", "Database 2" und "Database 3" angewendet wird.

```powershell
New-ManagementScope -Name "Primary databases" -DatabaseList "Database 1", "Database 2", "Database 3"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Exklusiver Bereich

Sämtliche mit dem Cmdlet **New-ManagementScope** erstellten Bereiche können als exklusive Bereiche festgelegt werden. Zum Erstellen eines exklusiven Bereichs verwenden Sie dieselben Befehle wie in den vorangehenden Abschnitten, um einen filterbasierten Empfängerbereich, einen filterbasierten Serverbereich, einen listenbasierten Serverbereich, einen filterbasierten Datenbankbereich oder einen listenbasierten Datenbankbereich zu erstellen. Anschließend fügen Sie dem Befehl die Option *Exclusive* hinzu.


> [!WARNING]
> Wenn Sie exklusive Verwaltungsbereiche erstellen, können nur Rollenempfänger, denen exklusive Bereiche mit zu ändernden Objekten zugewiesen sind, auf diese Objekte zugreifen. Nur Administratoren, denen eine Rolle mit dem exklusiven Bereich zugewiesen ist, können auf diese exklusiven bzw. geschützten Objekte zugreifen.



In diesem Beispiel wird ein exklusiver filterbasierter Empfängerbereich für alle Benutzer in der Abteilung "Executives" erstellt.

```powershell
    New-ManagementScope "Executive Users Exclusive Scope" -RecipientRestrictionFilter { Department -Eq "Executives" } -Exclusive
```

Bei der Erstellung eines exklusiven Bereichs müssen Sie standardmäßig bestätigen, dass Sie einen exklusiven Bereich erstellt haben und sich der Auswirkungen eines exklusiven Bereichs auf vorhandene Rollenzuweisungen bewusst sind, die nicht exklusiv sind. Zum Unterdrücken der Warnmeldung können Sie die Option *Force* verwenden. In diesem Beispiel wird derselbe Bereich wie im vorherigen Beispiel erstellt, jedoch ohne die Warnmeldung.

```powershell
    New-ManagementScope "Executive Users Exclusive Scope" -RecipientRestrictionFilter { Department -Eq "Executives" } -Exclusive -Force
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\)).

## Schritt 2: Hinzufügen oder Ändern einer Verwaltungsrollenzuweisung

Nach dem Erstellen des Bereichs muss dieser zu einer neuen oder vorhandenen Verwaltungsrollenzuweisung hinzugefügt werden.

Wenn Sie einen Verwaltungsbereich erstellen und zu einer neuen Verwaltungsrollenzuweisung hinzufügen möchten, die erstellt werden soll, finden Sie unter den folgenden Themen weitere Informationen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

Wenn Sie einen Verwaltungsrollenbereich erstellen und zu einer vorhandenen Verwaltungsrollenzuweisung hinzufügen möchten, finden Sie unter den folgenden Themen weitere Informationen:

  - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

  - [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md)

