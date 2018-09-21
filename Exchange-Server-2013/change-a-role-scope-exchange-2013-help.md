---
title: 'Ändern eines Rollenbereichs: Exchange 2013 Help'
TOCTitle: Ändern eines Rollenbereichs
ms:assetid: 9180e1e0-c352-4ccd-8da6-885a2e309867
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298145(v=EXCHG.150)
ms:contentKeyID: 50476243
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern eines Rollenbereichs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungsrollenbereiche bestimmen, welche Objekte einem Benutzer zur Verfügung gestellt werden, damit die Objekte mithilfe der ihm zugeordneten Cmdlets und Parameter geändert werden können. Durch Ändern eines Bereichs können Sie festlegen, welche Objekte den Benutzern zum Erstellen, Ändern oder Entfernen zur Verfügung gestellt werden.

Sie können einen benutzerdefinierten Verwaltungsbereich ändern. Sie können entweder exklusive oder reguläre Bereiche ändern. Wenn Sie einen exklusiven Bereich ändern, wird der neue Bereich sofort wirksam. Wenn Sie eine Verwaltungsrollenzuweisung mit einem vordefiniererten oder OU-Verwaltungsbereich (Organisation Unit, Organisationseinheit) ändern möchten, sehen Sie unter [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md) nach.

Weitere Informationen zu Verwaltungsrollenbereichen und -zuweisungen in Microsoft Exchange Server 2013 finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollenbereichen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsbereiche" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Ändern eines Bereichnamens

Verwenden Sie die folgende Syntax, um den Namen eines Bereichs zu ändern.

```powershell
Set-ManagementScope <current scope name> -Name <new scope name>
```

In diesem Beispiel wird der Bereich "Seattle Servers" in "Seattle Exchange Servers" geändert.

```powershell
Set-ManagementScope "Seattle Servers" -Name "Seattle Exchange Servers"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\)).

## Ändern eines Empfängerfilters für einen Bereich

Verwenden Sie die folgende Syntax, um den Empfängerfilter für einen Bereich zu ändern.

```powershell
Set-ManagementScope <scope name> -RecipientRestrictionFilter { <new recipient filter> }
```

In diesem Beispiel wird der Empfängerfilter so geändert, dass alle Empfängerobjekte ermittelt werden, bei denen die Eigenschaft **Company** auf "contoso" festgelegt ist.

```powershell
Set-ManagementScope "Company Scope" -RecipientRestrictionFilter { Company -eq 'contoso' }
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\)).

Weitere Informationen zu Empfängerfiltern sowie eine Liste der filterbaren Empfängereigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

## Ändern der obersten Ebene der Organisationseinheit

Verwenden Sie die folgende Syntax, um die oberste Ebene der Organisationseinheit für einen Bereich zu ändern.

```powershell
Set-ManagementScope <scope name> -RecipientRoot <OU>
```

In diesem Beispiel wird die oberste Ebene der Organisationseinheit auf die Organisationseinheit "North America/Sales" des Bereichs "Sales Users" unter der Domäne "contoso.com" gesetzt.

```powershell
Set-ManagementScope "Sales Users" -RecipientRoot "contoso.com/North America/Sales"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\)).

## Ändern eines Serverfilters für einen Bereich

Verwenden Sie die folgende Syntax, um den Serverfilter für einen Bereich zu ändern.

```powershell
Set-ManagementScope <scope name> -ServerRestrictionFilter { <new server filter> }
```

In diesem Beispiel wird der Serverfilter so geändert, dass er mit allen Serverobjekten übereinstimmt, deren Eigenschaft **ServerSite** festgelegt ist auf 'CN=Redmond,CN=Sites,CN=Configuration,DC=contoso,DC=com'.

    Set-ManagementScope "Company Scope" -ServerRestrictionFilter { ServerSite -eq 'CN=Redmond,CN=Sites,CN=Configuration,DC=contoso,DC=com' }

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\)).

Weitere Informationen zu Serverfiltern sowie eine Liste der filterbaren Servereigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

## Ändern der Serverliste für einen Bereich

Sie können die Serverliste für einen Bereich nicht ändern. Wenn Sie die Serverliste ändern möchten, müssen Sie Folgendes ausführen:

1.  Rufen Sie ggf. die aktuelle Serverliste in dem Bereich ab, die ersetzt werden soll, indem Sie das unter dem Thema [Anzeigen von Rollenbereichen](view-role-scopes-exchange-2013-help.md) beschriebene Verfahren zum Anzeigen eines bestimmten Bereichs ausführen.

2.  Erstellen Sie einen Bereich mit dem neuen Server, indem Sie das Verfahren "Schritt 1: Erstellen eines benutzerdefinierten Bereichs" ausführen, das unter dem Thema [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md) beschrieben wird.

3.  Ändern Sie alle Verwaltungsrollenzuweisungen, die den alten Bereich verwenden, dahingehend, dass sie jetzt den neuen Bereich verwenden, indem Sie das unter dem Thema [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md) beschriebene Verfahren "Verwenden der Shell zum Ändern des Serverfilters oder listenbasierten Bereichs einer Rollenzuweisung" ausführen.

4.  Entfernen Sie den alten Bereich, indem Sie das unter dem Thema [Entfernen eines Bereichs Rolle](remove-a-role-scope-exchange-2013-help.md) beschriebene Verfahren ausführen.

## Ändern eines Datenbankfilters für einen Bereich

Verwenden Sie die folgende Syntax, um den Datenbankfilter für einen Bereich zu ändern.

```powershell
Set-ManagementScope <scope name> -DatabaseRestrictionFilter { <new database filter> }
```

In diesem Beispiel wird der Datenbankfilter so geändert, dass alle Datenbankobjekte ermittelt werden, bei denen die Eigenschaft **Name** die Zeichenfolge "Executive" enthält.

    Set-ManagementScope "Database Executive Scope" -DatabaseRestrictionFilter { Name -Like "*Executive*" }

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\)).

Weitere Informationen zu Datenbankfiltern sowie eine Liste der filterbaren Datenbankeigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

## Ändern der Datenbankliste für einen Bereich

Sie können die Datenbankliste für einen Bereich nicht ändern. Wenn Sie die Datenbankliste ändern möchten, müssen Sie Folgendes ausführen:

1.  Rufen Sie ggf. die aktuelle Datenbankliste in dem Bereich ab, der ersetzt werden soll, indem Sie das unter dem Thema [Anzeigen von Rollenbereichen](view-role-scopes-exchange-2013-help.md) beschriebene Verfahren zum Anzeigen eines bestimmten Bereichs ausführen.

2.  Erstellen Sie einen Bereich mit der neuen Datenbankliste, indem Sie das Verfahren "Schritt 1: Erstellen eines benutzerdefinierten Bereichs" ausführen, das unter dem Thema [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md) beschrieben wird.

3.  Ändern Sie alle Verwaltungsrollenzuweisungen, die den alten Bereich verwenden, dahingehend, dass sie jetzt den neuen Bereich verwenden, indem Sie das unter dem Thema [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md) beschriebene Verfahren "Verwenden der Shell zum Ändern des Datenbankfilters oder listenbasierten Bereichs für eine Rollenzuweisung" ausführen.

4.  Entfernen Sie den alten Bereich, indem Sie das unter dem Thema [Entfernen eines Bereichs Rolle](remove-a-role-scope-exchange-2013-help.md) beschriebene Verfahren ausführen.

