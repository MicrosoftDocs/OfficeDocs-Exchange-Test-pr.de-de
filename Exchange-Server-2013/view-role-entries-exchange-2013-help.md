---
title: 'Anzeigen von rolleneinträgen: Exchange 2013 Help'
TOCTitle: Anzeigen von rolleneinträgen
ms:assetid: d9bb0d14-db59-456c-8f50-a8d7f7323df9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351179(v=EXCHG.150)
ms:contentKeyID: 50476871
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen von rolleneinträgen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Jeder Verwaltungsrolleneintrag repräsentiert ein Cmdlet oder Skript. Die Parameter eines Rolleneintrags bestimmen, auf welche Cmdlet- oder Skriptparameter ein Benutzer zugreifen kann.

Die Identität von Rolleneinträgen umfasst den Namen der Verwaltungsrolle, welcher der Rolleneintrag zugeordnet ist, sowie das Cmdlet oder Skript, das der Rolleeintrag referenziert. Weitere Informationen zu Rolleneinträgen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rolleneinträgen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - In diesem Thema werden das Pipelining, das Cmdlet **Format-List**, Objekte und Eigenschaften verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:
    
      - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))
    
      - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)
    
      - [Strukturierte Daten](https://technet.microsoft.com/de-de/library/aa996386\(v=exchg.150\))

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen einer Liste mit Rolleneinträgen

Sie können das Cmdlet **Get-ManagementRoleEntry** verwenden, um eine Liste mit Rolleneinträgen abzurufen. Bei Verwendung des Cmdlets **Get-ManagementRoleEntry** müssen Sie einen Wert angeben, der sowohl den Namen der Rolle mit den aufzulistenden Rolleneinträgen sowie den Namen des Cmdlets für den aufzulistenden Rolleneintrag enthält. Durch die Kombination des Rollen- und Cmdlet-Namens mit dem Platzhalterzeichen (\*) können Sie spezifische oder allgemeine Listen mit Rolleneinträgen zurückgeben.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

## Anzeigen einer Liste aller Rolleneinträge für eine Rolle

Verwenden Sie die folgende Syntax, um eine Liste aller Rolleneinträge für eine bestimmte Rolle anzuzeigen.

    Get-ManagementRoleEntry <role name>\*

In diesem Beispiel werden alle Rolleneinträge für die Rolle `Recipient Administrators` abgerufen.

    Get-ManagementRole "Recipient Administrators\*"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

## Anzeigen einer Liste mit Rollen, die einen bestimmten Rolleneintrag enthalten

Verwenden Sie die folgende Syntax, um eine Liste aller Rollen anzuzeigen, die einen bestimmen Rolleneintrag enthalten.

    Get-ManagementRoleEntry *\<cmdlet name>

In diesem Beispiel werden alle Rollen mit dem Rolleneintrag **Set-Mailbox** abgerufen.

    Get-ManagementRoleEntry *\Set-Mailbox

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

## Anzeigen einer gezielten Liste mit Rollen, die ähnliche Rolleneinträge enthalten

Verwenden Sie die folgende Syntax, um eine Liste mit Rollen anzuzeigen, die Cmdlets mit ähnlichen Namen enthalten.

    Get-ManagementRoleEntry *<partial role name>*\*<partial cmdlet name>*

In diesem Beispiel wird eine Liste mit Rolleneinträgen mit der Zeichenfolge `Mailbox` zurückgegeben, die Rollen mit der Zeichenfolge `Tier 1` zugeordnet sind.

    Get-ManagementRoleEntry "*Tier 1*\*Mailbox*"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

## Anzeigen einzelner Rolleneinträge

Verwenden Sie die folgende Syntax, um die Details eines einzelnen Rolleneintrags anzuzeigen.

    Get-ManagementRoleEntry <role name>\<cmdlet name> | Format-List

In diesem Beispiel werden die Details des Rolleneintrags **Set-Mailbox** für die Rolle `Recipient Administrators` abgerufen.

    Get-ManagementRoleEntry "Recipient Administrators\Set-Mailbox" | Format-List

Wenn der anzuzeigende Rolleneintrag mehr Parameter umfasst, als mit dem Cmdlet **Format-List** angezeigt werden können, finden Sie unter "Anzeigen der Parameter für einen einzelnen Rolleneintrag" weiter unten in diesem Thema zusätzliche Informationen.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

## Anzeigen der Parameter für einen einzelnen Rolleneintrag

Einige Rolleneinträge verfügen über eine größere Anzahl von Parametern, als bei Übergabe der Ergebnisse des Cmdlets **Get-ManagementRoleEntry** an das Cmdlet **Format-List** über eine Pipe angezeigt werden können. Um alle Parameter eines Rolleneintrags anzuzeigen, müssen Sie direkt auf die Eigenschaft **Parameters** des Rolleneintragobjekts zugreifen.

Verwenden Sie die folgende Syntax, um die in der Eigenschaft **Parameters** eines Rolleneintragobjekts gespeicherten Parameter anzuzeigen.

    (Get-ManagementRoleEntry <role name>\<cmdlet name>).Parameters

In diesem Beispiel werden die Parameter für den Rolleneintrag **Set-Mailbox** der Rolle "Mail Recipients" abgerufen.

    (Get-ManagementRoleEntry "Mail Recipients\Set-Mailbox").Parameters

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)).

