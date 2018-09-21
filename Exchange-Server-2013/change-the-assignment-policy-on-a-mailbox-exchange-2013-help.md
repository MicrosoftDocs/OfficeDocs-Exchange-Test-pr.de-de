---
title: 'Ändern der Zuweisungsrichtlinie für ein Postfach: Exchange 2013 Help'
TOCTitle: Ändern der Zuweisungsrichtlinie für ein Postfach
ms:assetid: 011690a5-233a-4c03-8842-92276f899a89
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638076(v=EXCHG.150)
ms:contentKeyID: 50474936
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern der Zuweisungsrichtlinie für ein Postfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-08_

Sie können die Richtlinie für die Verwaltungsrollenzuweisung für ein Postfach ändern. Wenn Sie die Zuweisungsrichtlinie eines Postfachs ändern, werden die Änderungen wirksam, sobald der Benutzer die Verbindung aktualisiert, z. B. wenn er sich das nächste Mal bei seinem Postfach anmeldet oder die Seite mit den Postfachoptionen öffnet. Weitere Informationen zu Zuweisungsrichtlinien in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Berechtigungen gibt? Weitere Informationen finden Sie hier: [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Ändern der Zuweisungsrichtlinie für ein Postfach mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie den Benutzer oder das Ressourcenpostfach aus, für den bzw. das die Zuweisungsrichtlinie geändert werden soll, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie **Postfachfunktionen** aus.

4.  Wählen Sie in der Liste **Rollenzuweisungsrichtlinie** die Zuweisungsrichtlinie aus, die dem Postfach zugewiesen werden soll, und klicken Sie auf **Speichern**.

## Verwenden der Shell zum Ändern der Zuweisungsrichtlinie für ein Postfach

Verwenden Sie zum Ändern der Zuweisungsrichtlinie für ein Postfach die folgende Syntax.

```powershell
Set-Mailbox <mailbox alias or name> -RoleAssignmentPolicy <assignment policy>
```

In diesem Beispiel wird die Zuweisungsrichtlinie für das Postfach "Brian" auf "Unified Messaging Users" festgelegt.

```powershell
Set-Mailbox Brian -RoleAssignmentPolicy "Unified Messaging Users"
```

## Verwenden der Shell zum Ändern der Zuweisungsrichtlinie für eine Gruppe von Postfächern, denen eine bestimmte Zuweisungsrichtlinie zugewiesen ist


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Ändern der Zuweisungsrichtlinie für mehrere Postfächer in einem Arbeitsschritt verwendet werden.



In diesem Verfahren werden Kenntnisse zum Pipelining, zum Cmdlet **Where** und zum Parameter *WhatIf* vorausgesetzt. Weitere Informationen zu diesen Konzepten finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

  - [Optionen "WhatIf", "Confirm" und "ValidateOnly"](whatif-confirm-and-validateonly-switches-exchange-2013-help.md)

Verwenden Sie die folgende Syntax, um die Zuweisungsrichtlinie für eine Gruppe von Postfächern zu ändern, denen eine bestimmte Zuweisungsrichtlinie zugewiesen ist.

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "<assignment policy to find>" } | Set-Mailbox -RoleAssignmentPolicy <assignment policy to set>

In diesem Beispiel werden alle Postfächer gesucht, die "Redmond Users - No Voicemail" zugewiesen sind, und die Zuweisungsrichtlinie wird in "Redmond Users - Voicemail Enabled" geändert.

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Redmond Users - No Voicemail" } | Set-Mailbox -RoleAssignmentPolicy "Redmond Users - Voicemail Enabled"

In diesem Beispiel ist der Parameter *WhatIf* enthalten, sodass Sie ohne tatsächliches Anwenden von Änderungen anzeigen können, welche Postfächer geändert würden.

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Redmond Users - No Voicemail" } | Set-Mailbox -RoleAssignmentPolicy "Redmond Users - Voicemail Enabled" -WhatIf

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) oder [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

