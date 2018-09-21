---
title: 'Entfernen einer Rolle: Exchange 2013 Help'
TOCTitle: Entfernen einer Rolle
ms:assetid: 2fb6f453-f37a-4636-8353-3f9927f81298
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335178(v=EXCHG.150)
ms:contentKeyID: 50475272
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Rolle

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Sie können Verwaltungsrollen, die nicht länger benötigt werden, aus Ihrer Organisation entfernen. Sie können nur Verwaltungsrollen entfernen, die Sie erstellt haben. Integrierte Verwaltungsrollen können nicht entfernt werden. Weitere Informationen zu Verwaltungsrollen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Vor dem Entfernen einer Verwaltungsrolle müssen Sie alle Verwaltungsrollenzuweisungen entfernen. Weitere Informationen zum Entfernen einer Rollenzuweisung finden Sie unter [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen einer Verwaltungsrolle ohne untergeordnete Rollen

Verwenden Sie die folgende Syntax, um eine Rolle ohne untergeordnete Rollen zu entfernen.

```powershell
Remove-ManagementRole <role name>
```

In diesem Beispiel wird die Rolle "Seattle Server Administrators" entfernt.

```powershell
Remove-ManagementRole "Seattle Server Administrators"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRole](https://technet.microsoft.com/de-de/library/dd351170\(v=exchg.150\)).

## Entfernen einer Verwaltungsrolle mit untergeordneten Rollen

Wenn Sie eine Rolle mit untergeordneten Rollen entfernen wollen, müssen Sie auch die untergeordneten Rollen entfernen. Beim Versuch, eine Rolle mit untergeordneten Rollen zu entfernen, erhalten Sie eine Fehlermeldung, sofern Sie nicht die Option *Recurse* verwenden. Wenn Sie die Option *Recurse* beim Entfernen einer Rolle verwenden, wird die angegebene Rolle mit den untergeordneten Rollen entfernt.


> [!WARNING]
> Wenn Sie die Option <EM>Recurse</EM> verwenden, werden auch alle untergeordneten Rollen der zu entfernenden Rolle entfernt. Stellen Sie sicher, dass Sie wissen, welche Rollen entfernt werden, bevor Sie den Befehl ausführen.



Verwenden Sie die Option *WhatIf* zusammen mit dem Befehl, um sicherzustellen, dass Sie nur die Rollen entfernen, die Sie entfernen wollen. Verwenden Sie die folgende Syntax.

```powershell
Remove-ManagementRole <role name> -Recurse -WhatIf
```

Die Option *WhatIf* führt den Befehl ohne Commit von Änderungen aus und meldet, welche Rollen entfernt würden. Weitere Informationen zur Option *WhatIf* finden Sie unter [Optionen "WhatIf", "Confirm" und "ValidateOnly"](whatif-confirm-and-validateonly-switches-exchange-2013-help.md).

Nachdem Sie überprüft haben, dass nur die Rollen entfernt werden, die entfernt werden sollen, führen Sie denselben Befehl ohne die Option *WhatIf* aus. In diesem Beispiel werden die Rolle "London Administrators" und alle untergeordneten Rollen entfernt.

```powershell
Remove-ManagementRole "London Administrators" -Recurse
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRole](https://technet.microsoft.com/de-de/library/dd351170\(v=exchg.150\)).

## Entfernen einer Verwaltungsrolle ohne Bereichseinschränkung

Zum Entfernen einer Rolle ohne Bereichseinschränkung können Sie die unter Entfernen einer Verwaltungsrolle ohne untergeordnete Rollen und Entfernen einer Verwaltungsrolle mit untergeordneten Rollen beschriebenen Verfahren weiter oben in diesem Thema verwenden. Der einzige Unterschied besteht darin, dass Sie zum Entfernen einer Rolle ohne Bereichseinschränkung die Option *UnScopedTopLevel* beim Ausführen des Befehls verwenden müssen. In diesem Beispiel werden eine Rolle ohne Bereichseinschränkung und alle untergeordneten Rollen entfernt.

```powershell
Remove-ManagementRole "Custom IT Scripts" -Recurse -UnScopedTopLevel
```

Wie beim Entfernen anderer Rollen sollten Sie die Option *WhatIf* verwenden, um sicherzustellen, dass Sie die richtigen Rollen entfernen.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-ManagementRole](https://technet.microsoft.com/de-de/library/dd351170\(v=exchg.150\)).

