---
title: 'Anzeigen von Rollenbereichen: Exchange 2013 Help'
TOCTitle: Anzeigen von Rollenbereichen
ms:assetid: 0bb3a434-6651-473a-94eb-4eb9a34e6f70
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335084(v=EXCHG.150)
ms:contentKeyID: 50474998
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen von Rollenbereichen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungsrollenbereiche bestimmen, welche Objekte einem Benutzer zur Verfügung gestellt werden, damit die Objekte mithilfe der ihm zugeordneten Cmdlets und Parameter geändert werden können. Sie können Bereiche anzeigen, um zu bestimmen, welche Bereiche Ihrer Organisation hinzugefügt wurden, welche Konfiguration ein bestimmter Bereich aufweist und welche Bereiche verwaist sind.

Weitere Informationen zu Verwaltungsrollenbereichen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollenbereichen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsbereiche" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - In diesem Thema wird das Pipelining und das Cmdlet **Format-List** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:
    
      - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))
    
      - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen eines bestimmten Bereichs

Sie können die Details eines Bereichs anzeigen, indem Sie die Ausgabe des Cmdlets **Get-ManagementScope** an das Cmdlet **Format-List** umleiten.

Verwenden Sie die folgende Syntax, um die Details eines bestimmten Bereichs anzuzeigen.

```powershell
Get-ManagementScope <scope name> | Format-List
```

In diesem Beispiel werden die Details des Bereichs "Seattle Servers" abgerufen.

```powershell
Get-ManagementScope "Seattle Servers" | Format-List
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementScope](https://technet.microsoft.com/de-de/library/dd298180\(v=exchg.150\)).

## Auflisten aller Bereiche

In diesem Beispiel wird eine Liste mit Bereichen in Ihrer Organisation abgerufen.

```powershell
Get-ManagementScope
```

Dieses Cmdlet ruft exklusive und reguläre Bereiche ab. Wenn Sie nur exklusive oder nur reguläre Bereiche zurückgeben möchten, lesen Sie "Ausschließliches Auflisten aller exklusiven oder aller regulären Bereiche" weiter unten in diesem Thema.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementScope](https://technet.microsoft.com/de-de/library/dd298180\(v=exchg.150\)).

## Auflisten aller verwaisten Bereiche

*Verwaiste Bereiche* sind Bereiche, die keinen Verwaltungsrollenzuweisungen zugeordnet sind.

In diesem Beispiel wird eine Liste verwaister Bereiche abgerufen.

```powershell
Get-ManagementScope -Orphan
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementScope](https://technet.microsoft.com/de-de/library/dd298180\(v=exchg.150\)).

## Ausschließliches Auflisten aller exklusiven oder aller regulären Bereiche

Standardmäßig gibt das Cmdlet **Get-ManagementScope** eine Liste von Bereichen zurück, die exklusive und reguläre Bereiche enthält. Verwenden Sie die folgende Syntax, wenn Sie nur exklusive oder nur reguläre Bereiche zurückgeben möchten.

```powershell
Get-ManagementScope -Exclusive < $true | $false >
```

In diesem Beispiel werden nur exklusive Bereiche zurückgegeben.

```powershell
Get-ManagementScope -Exclusive $true
```

In diesem Beispiel wird eine Liste nur regulärer Bereiche zurückgegeben.

```powershell
Get-ManagementScope -Exclusive $false
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementScope](https://technet.microsoft.com/de-de/library/dd298180\(v=exchg.150\)).

