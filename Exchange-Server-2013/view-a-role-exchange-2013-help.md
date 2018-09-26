---
title: 'Anzeigen einer Rolle: Exchange 2013 Help'
TOCTitle: Anzeigen einer Rolle
ms:assetid: 1875b15f-22db-4ede-b310-ea894d6211c8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335117(v=EXCHG.150)
ms:contentKeyID: 50475099
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen einer Rolle

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungrollen können auf unterschiedliche Weisen angezeigt werden, abhängig von den gewünschten Informationen. Sie können beispielsweise auswählen, dass nur Rollen von einem bestimmten Rollentyp oder nur Rollen mit bestimmten enthaltenen Cmdlets und Parametern zurückgegeben werden, oder Sie können die Details einer bestimmten Verwaltungsrolle anzeigen. Weitere Informationen zu Verwaltungsrollen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Informationen zum Anzeigen einer Liste aller Verwaltungsrolleneinträge für eine Rolle finden Sie unter [Anzeigen von rolleneinträgen](view-role-entries-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - In diesem Thema werden das Pipelining und die Cmdlets **Format-List** und **Format-Table** verwendet. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:
    
      - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))
    
      - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]  
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen einer bestimmten Verwaltungsrolle

Sie können die Details einer angegebenen Rolle auch durch Abrufen einer bestimmten Rolle mit dem Cmdlet **Get-ManagementRole** und durch Umleiten der Ausgabe an das Cmdlet **Format-List** anzeigen.

Verwenden Sie die folgende Syntax, um die Details einer bestimmten Rolle anzuzeigen.

```powershell
Get-ManagementRole <role name> | Format-List
```

In diesem Beispiel werden die Details zur Verwaltungsrolle "E-Mail-Empfänger" abgerufen.

```powershell
Get-ManagementRole "Mail Recipients" | Format-List
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten aller Verwaltungsrollen

Sie können eine Liste aller Verwaltungsrollen in Ihrer Organisation anzeigen, indem Sie das Cmdlet **Get-ManagementRole** ohne Angabe von Rollen ausführen. Standardmäßig schließen die Ergebnisse den Rollennamen und Rollentyp jeder Rolle ein.

In diesem Beispiel wird eine Liste aller Rollen in Ihrer Organisation zurückgegeben.

```powershell
Get-ManagementRole
```

Um eine Liste der spezifischen Eigenschaften für alle Rollen in Ihrer Organisation zurückzugeben, können Sie die Ergebnisse des Cmdlets **Format-Table** umleiten und angeben, welche Eigenschaften in der Ergebnisliste enthalten sein sollen. Verwenden Sie die folgende Syntax.

```powershell
Get-ManagementRole | Format-Table <property 1>, <property 2...>
```

In diesem Beispiel wird eine Liste aller Rollen in Ihrer Organisation wiedergegeben. Dabei werden die Eigenschaft **Name** und alle Eigenschaften, deren Eigenschaftsname mit dem Wort **Implicit** beginnt, eingeschlossen.

```powershell
Get-ManagementRole | Format-Table Name, Implicit*
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten der Verwaltungsrollen, die ein bestimmtes Cmdlet enthalten

Sie können eine Liste von Rollen zurückgeben, die ein angegebenes Cmdlet enthalten, indem Sie den Parameter *Cmdlet* für das Cmdlet **Get-ManagementRole** verwenden.

Verwenden Sie die folgende Syntax, um eine Liste von Rollen zurückzugeben, die das angegebene Cmdlet enthalten.

```powershell
Get-ManagementRole -Cmdlet <cmdlet>
```

In diesem Beispiel wird eine Liste von Rollen zurückgegeben, die das Cmdlet **New-Mailbox** enthalten.

```powershell
Get-ManagementRole -Cmdlet New-Mailbox
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten von Verwaltungsrollen, die einen bestimmten Parameter enthalten

Sie können eine Liste von Rollen zurückgeben, die mindestens einen angegebenen Parameter enthalten, indem Sie den Parameter *CmdletParameters* für das Cmdlet **Get-ManagementRole** verwenden. Nur Rollen, die alle angegebenen Parameter enthalten, werden zurückgegeben.

Bei Verwendung des Parameters *CmdletParameters* kann der Parameter *Cmdlet* wahlweise eingeschlossen werden. Wenn Sie den Parameter *Cmdlet* einschließen, werden nur Rollen zurückgegeben, die die für das bestimmte Cmdlet angegebenen Parameter enthalten. Wenn Sie den Parameter *Cmdlet* nicht einschließen, werden Rollen zurückgegeben, die die angegebenen Parameter enthalten, unabhängig davon, zu welchem Cmdlet sie gehören.

Verwenden Sie die folgende Syntax, um eine Liste von Rollen zurückzugeben, die die angegebenen Parameter enthalten.

```powershell
Get-ManagementRole [-Cmdlet <cmdlet>] -CmdletParameters <parameter 1>, <parameter 2...>
```

In diesem Beispiel wird eine Liste von Rollen zurückgegeben, die die Parameter *Database* und *Server* enthalten, unabhängig davon, zu welchen Cmdlets sie gehören.

```powershell
Get-ManagementRole -CmdletParameters Database, Server
```

In diesem Beispiel wird eine Liste von Rollen zurückgegeben, für die der Parameter *EmailAddresses* nur zum Cmdlet **Set-Mailbox** gehört.

```powershell
Get-ManagementRole -Cmdlet Set-Mailbox -CmdletParameters EmailAddresses
```

Sie können auch das Platzhalterzeichen (\*) mit dem Parameter *Cmdlet* oder *CmdletParameters* verwenden, um Übereinstimmungen mit Teilen von Cmdlet- oder Parameternamen zu ermitteln.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten von Verwaltungsrollen eines bestimmten Rollentyps

Sie können eine Liste von Rollen anhand eines angegebenen Rollentyps zurückgeben, indem Sie den Parameter *RoleType* für das Cmdlet **Get-ManagementRole** verwenden.

Verwenden Sie die folgende Syntax, um eine Liste von Rollen zurückzugeben, die dem angegebenen Rollentyp entsprechen.

```powershell
Get-ManagementRole -RoleType <roletype>
```

In diesem Beispiel wird eine Liste der Rollen vom Rollentyp `UmMailboxes` zurückgegeben.

```powershell
Get-ManagementRole -RoleType UmMailboxes
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten der unmittelbar untergeordneten Rollen einer übergeordneten Rolle

Sie können eine Liste von Rollen zurückgeben, die die unmittelbar untergeordneten Rollen der angegebenen übergeordneten Rolle sind, indem Sie den Parameter *GetChildren* für das Cmdlet **Get-ManagementRole** verwenden. Nur Rollen, die die angegebene Rolle als übergeordnete Rolle aufweisen, werden zurückgegeben.

Verwenden Sie die folgende Syntax, um eine Liste von Rollen zurückzugeben, die die unmittelbar untergeordneten Rollen einer übergeordneten Rolle sind.

```powershell
Get-ManagementRole <parent role name> -GetChildren
```

In diesem Beispiel wird eine Liste der unmittelbar untergeordneten Rollen der Rolle "Disaster Recovery" zurückgegeben.

```powershell
Get-ManagementRole "Disaster Recovery" -GetChildren
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).

## Auflisten aller untergeordneten Rollen unterhalb einer übergeordneten Rolle

Sie können eine Liste der gesamten Rollenkette von einer angegebenen übergeordneten Rolle bis zur letzten untergeordneten Rolle zurückgeben, indem Sie den Parameter *Recurse* für das Cmdlet **Get-ManagementRole** verwenden. Der Parameter *Recurse* für das Cmdlet **Get-ManagementRole** gibt an, dass rekursiv jede gefundene Beziehung zwischen übergeordneter und untergeordneter Rolle durchlaufen werden soll, bis die letzte untergeordnete Rolle erreicht ist. Die übergeordnete Rolle ist in der zurückgegebenen Liste enthalten.

In diesem Beispiel wird eine Liste aller untergeordneten Rollen einer übergeordneten Rolle zurückgegeben.

```powershell
Get-ManagementRole <parent role name> -Recurse
```

In diesem Beispiel werden alle untergeordneten Rollen der Rolle "Mail Recipients" zurückgegeben.

```powershell
Get-ManagementRole "Mail Recipients" -Recurse
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRole](https://technet.microsoft.com/de-de/library/dd351125\(v=exchg.150\)).