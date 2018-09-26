---
title: 'Entfernen eines Rolleneintrags aus einer Rolle: Exchange 2013 Help'
TOCTitle: Entfernen eines Rolleneintrags aus einer Rolle
ms:assetid: 4736367a-750f-44d3-8a20-5149bd35e9ff
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297947(v=EXCHG.150)
ms:contentKeyID: 50475592
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen eines Rolleneintrags aus einer Rolle

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Die Verwaltungsrolleneinträge einer Verwaltungsrolle legen fest, welche Cmdlets und Parameter für die Verwaltungsrolle zur Verfügung stehen. Durch das Entfernen von Rolleneinträgen oder Parametern aus einem Rolleneintrag können Sie einschränken, welche Aufgaben die einer Verwaltungsrolle zugewiesenen Benutzer ausführen können. Weitere Informationen zu Verwaltungsrolleneinträgen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen eines einzelnen Rolleneintrags aus einer Rolle

Wenn Sie einen Rolleneintrag aus einer Rolle entfernen, entziehen Sie den dieser Rolle zugewiesenen Benutzern den Zugriff auf das zugeordnete Cmdlet oder Skript.

Verwenden Sie die folgende Syntax, um einen einzelnen Verwaltungsrolleneintrag aus einer Rolle zu entfernen.

```powershell
    Remove-ManagementRoleEntry <management role>\<management role entry>
```

In diesem Beispiel wird das Cmdlet **Enable-MailUser** aus der Rolle "Seattle Server Administrators" entfernt.

```powershell
    Remove-ManagementRoleEntry "Seattle Server Administrators\Enable-MailUser"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351187\(v=exchg.150\)).

## Entfernen mehrerer Rolleneinträge aus einer Rolle

Wenn Sie mehrere Rolleneinträge aus einer Rolle entfernen, entziehen Sie den dieser Rolle zugewiesenen Benutzern den Zugriff auf das zugeordnete Cmdlet oder Skript.

Um mehrere Rolleneinträge aus einer Rolle zu entfernen, müssen Sie die Liste der zu entfernenden Rolleneinträge mit dem Cmdlet **Get-ManagementRoleEntry** abrufen. Anschließend müssen Sie die Ausgabe mittels Pipe an das Cmdlet **Remove-ManagementRoleEntry** umleiten. Sie können Platzhalterzeichen mit dem Cmdlet **Get-ManagementRoleEntry** verwenden, um mehrere Rolleneinträge zu ermitteln. Stellen Sie mithilfe der Option *WhatIf* sicher, dass die richtigen Rolleneinträge entfernt werden. Verwenden Sie die folgende Syntax.

```powershell
    Get-ManagementRoleEntry <management role>\<role entry with wildcard character> | Remove-ManagementRoleEntry -WhatIf
```

In diesem Beispiel werden alle Rolleneinträge aus der Rolle "Seattle Server Administrators" entfernt, die das Wort "journal" enthalten.

```powershell
    Get-ManagementRoleEntry "Seattle Server Administrators\*Journal*" | Remove-ManagementRoleEntry -WhatIf
```

Wenn Sie den Befehl mit der Option *WhatIf* ausführen, gibt das Cmdlet eine Liste aller Rolleneinträge zurück, die entfernt würden. Wenn die Liste die richtigen Einträge enthält, führen Sie den Befehl ohne die Option *WhatIf* erneut aus, um die Rolleneinträge zu entfernen.

```powershell
    Get-ManagementRoleEntry "Seattle Server Administrators\*Journal*" | Remove-ManagementRoleEntry
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)) und [Remove-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351187\(v=exchg.150\)).

## Entfernen von Parametern aus einem Rolleneintrag für eine Rolle

Wenn Sie Parameter aus einem Rolleneintrag für eine Rolle entfernen, stehen diese Parameter den dieser Rolle zugewiesenen Benutzern nicht länger zur Verfügung.

Verwenden Sie die folgende Syntax, um Parameter aus einem Rolleneintrag zu entfernen.
```powershell
    Set-ManagementRoleEntry <management role>\<role entry> -Parameters <parameter 1>,<parameter 2...> -RemoveParameter
```

In diesem Beispiel werden die Parameter *MaxSafeSenders*, *MaxSendSize*, *SecondaryAddress* und *UseDatabaseQuotaDefaults* aus dem Rolleneintrag **Set-Mailbox** für die Rolle "Seattle Server Administrators" entfernt.
```powershell
    Set-ManagementRoleEntry "Seattle Server Administrators\Set-Mailbox" -Parameters MaxSafeSenders,MaxSendSize,SecondaryAddress,UseDatabaseQuotaDefaults -RemoveParameter
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

