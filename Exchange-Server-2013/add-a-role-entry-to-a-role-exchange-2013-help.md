---
title: 'Hinzufügen eines Rolleneintrags zu einer Rolle: Exchange 2013 Help'
TOCTitle: Hinzufügen eines Rolleneintrags zu einer Rolle
ms:assetid: 30cd37bc-b3e8-4f39-a8ba-a4c20b1b27b7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335180(v=EXCHG.150)
ms:contentKeyID: 50475276
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen eines Rolleneintrags zu einer Rolle

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-04_

Wenn Sie Zugriff auf ein Cmdlet erteilen möchten, müssen Sie den zugehörigen Verwaltungsrolleneintrag zu einer Verwaltungsrolle hinzufügen. Wenn Sie einer Rolle den Rolleneintrag hinzugefügt haben, können die Benutzer, denen die Rolle zugewiesen wurde, auf das Cmdlet zugreifen. Weitere Informationen zu Verwaltungsrolleneinträgen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Rolleneinträge können nicht zu integrierten Rollen hinzugefügt werden. Wenn Sie Rollen anpassen möchten, müssen Sie eine neue Rolle erstellen. Weitere Informationen zum Erstellen einer neuen Rolle finden Sie unter [Erstellen einer Rolle](create-a-role-exchange-2013-help.md).


> [!NOTE]
> In diesem Thema wird nicht darauf eingegangen, wie Verwaltungsrolleneinträge ohne Bereichseinschränkungen einer Verwaltungsrolle ohne Bereichseinschränkungen hinzugefügt werden. Weitere Informationen zum Hinzufügen von Rolleneinträgen ohne Bereichseinschränkungen finden Sie unter <A href="add-a-role-entry-to-an-unscoped-top-level-role-exchange-2013-help.md">Hinzufügen eines Eintrags Rolle zu einem oberster Ebene ohne bereichseinschränkung</A>.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Ein Rolleneintrag, den Sie einer Verwaltungsrolle hinzufügen möchten, muss in der unmittelbaren übergeordneten Verwaltungsrolle der Rolle vorhanden sein.

  - In diesem Thema wird Pipelining verwendet. Weitere Informationen zum Pipelining finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Hinzufügen eines Rolleneintrags aus einer übergeordneten Rolle

Sie können einen Rolleneintrag mithilfe der folgenden Syntax genau so zu einer Rolle hinzufügen, wie dieser in der übergeordneten Rolle angezeigt wird.

```powershell
    Add-ManagementRoleEntry <child role name>\<cmdlet>
```

In diesem Beispiel wird das Cmdlet **Set-Mailbox** der Rolle "Recipient Administrators" hinzugefügt.

```powershell
    Add-ManagementRoleEntry "Recipient Administrators\Set-Mailbox"
```

Dieser Befehl überprüft die übergeordnete Rolle und fügt den Rolleneintrag zur untergeordneten Rolle hinzu, wenn dieser vorhanden ist. Wenn der Rolleneintrag in der untergeordneten Rolle bereits vorhanden ist, können Sie den Parameter *Overwrite* einbeziehen, um den vorhandenen Rolleneintrag zu überschreiben.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351236\(v=exchg.150\)).

## Hinzufügen eines Rolleneintrags aus einer übergeordneten Rolle nur mit spezifischen Parametern

Wenn Sie einen Rolleneintrag aus einer übergeordneten Rolle hinzufügen, aber nur spezifische Parameter in den Rolleneintrag der untergeordneten Rolle übernehmen möchten, verwenden Sie die folgende Syntax.

```powershell
    Add-ManagementRoleEntry <child role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...>
```

In diesem Beispiel wird das Cmdlet **Set-Mailbox** der Rolle "Help Desk" hinzugefügt, aber nur die Parameter *DisplayName* und *EmailAddresses* werden in den Eintrag für die untergeordnete Rolle übernommen.

```powershell
    Add-ManagementRoleEntry "Help Desk\Set-Mailbox" -Parameters DisplayName, EmailAddresses
```

Dieser Befehl überprüft die übergeordnete Rolle und fügt den Rolleneintrag zur untergeordneten Rolle hinzu, wenn dieser vorhanden ist. Wenn der Rolleneintrag in der untergeordneten Rolle bereits vorhanden ist, können Sie den Parameter *Overwrite* einbeziehen, um den vorhandenen Rolleneintrag zu überschreiben.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351236\(v=exchg.150\)).

## Hinzufügen mehrerer Rolleneinträge aus einer übergeordneten Rolle

Wenn Sie einer Rolle mehrere Rolleneinträge hinzufügen möchten, müssen Sie eine Liste der Rolleneinträge in der übergeordneten Rolle abrufen, die Sie der untergeordneten Rolle hinzufügen möchten, und diese dann der untergeordneten Rolle hinzufügen. Zu diesem Zweck rufen Sie die Liste der Rolleneinträge in einer übergeordneten Rolle mithilfe des Cmdlets **Get-ManagementRoleEntry** ab. Dann leiten Sie die Ausgabe des Cmdlets **Get-ManagementRoleEntry** mittels Pipeline an das Cmdlet **Add-ManagementRoleEntry** weiter. Um mehrere Rolleneinträge abzurufen, müssen Sie das Platzhalterzeichen (\*) verwenden.

Verwenden Sie die folgende Syntax, um mehrere Einträge aus einer übergeordneten Rolle zu einer untergeordneten Rolle hinzuzufügen.

```powershell
    Get-ManagementRoleEntry <parent role name>\*<partial cmdlet name>* | Add-ManagementRoleEntry -Role <child role name>
```

In diesem Beispiel werden alle Rolleneinträge, die die Zeichenfolge `Mailbox` im Cmdlet-Namen der übergeordneten Rolle "Mail Recipients" enthalten, der untergeordneten Rolle "Seattle Mail Recipients" hinzugefügt.

```powershell
    Get-ManagementRoleEntry "Mail Recipients\*Mailbox*" | Add-ManagementRoleEntry -Role "Seattle Mail Recipients"
```

Wenn die Rolleneinträge in der untergeordneten Rolle bereits vorhanden sind, können Sie den Parameter *Overwrite* einbeziehen, um die vorhandenen Rolleneinträge zu überschreiben.

Weitere Informationen zum Abrufen einer Liste von Verwaltungsrolleneinträgen finden Sie unter [Anzeigen von rolleneinträgen](view-role-entries-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd335210\(v=exchg.150\)) und [Add-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351236\(v=exchg.150\)).

