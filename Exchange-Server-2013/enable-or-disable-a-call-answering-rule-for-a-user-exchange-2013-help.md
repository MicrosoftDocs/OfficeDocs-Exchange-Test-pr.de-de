---
title: 'Aktiv. o. Deaktiv. von Mailboxansageregeln für Benutzer: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren einer Mailboxansageregel für einen Benutzer
ms:assetid: f9e40ac3-117f-44f6-9ab1-dc9f4c72e8ac
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn140252(v=EXCHG.150)
ms:contentKeyID: 54651518
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren einer Mailboxansageregel für einen Benutzer

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Shell verwenden, um eine oder mehrere Mailboxansageregeln für einen Benutzer zu aktivieren oder zu deaktivieren. Sie können auch die Cmdlets **Enable-UMCallAnsweringRule** oder **Disable-UMCallAnsweringRule** in einem Exchange-Verwaltungsshellskript verwenden, um Mailboxansageregeln für einen oder mehrere Benutzer zu aktivieren oder zu deaktivieren.

Mailboxansageregeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails. Wenn ein Benutzer für Unified Messaging (UM) aktiviert ist, werden standardmäßig keine Mailboxansageregeln konfiguriert. Eingehende Anrufe werden vom Mailsystem beantwortet, und Anrufer werden aufgefordert, eine Sprachnachricht zu hinterlassen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Mailboxansageregeln finden Sie unter [Weiterleiten von Anrufen Prozeduren](forwarding-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Mailboxansageregeln" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)). Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren einer Mailboxansageregel mithilfe der Shell

Beim Erstellen einer Mailboxansageregel wird diese aktiviert. Sie können mithilfe der Shell eine Mailboxansageregel aktivieren, die zuvor deaktiviert war. Durch das Aktivieren einer Mailboxansageregel kann das Cmdlet **Enable-UMCallAnsweringRule** die Mailboxansageregel einschließlich der für eine angegebene Mailboxansageregel definierten Bedingungen und Aktionen abrufen.

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith aktiviert.

    Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith

In diesem Beispiel wird die Option *WhatIf* verwendet, um zu testen, ob die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith aktiviert werden kann und ob innerhalb des Befehls Fehler vorliegen.

    Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -WhatIf

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith aktiviert, und der angemeldete Benutzer wird aufgefordert, das Aktivieren der Mailboxansageregel zu bestätigen.

    Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -Confirm

## Deaktivieren einer Mailboxansageregel mithilfe der Shell

Durch das Deaktivieren einer Mailboxansageregel wird verhindert, dass die Regel abgerufen und verarbeitet wird, wenn ein eingehender Anruf empfangen wird. Wenn Sie eine Mailboxansageregel erstellen, sollte Sie sie während der Einrichtung von Bedingungen und Aktionen deaktivieren. Dadurch wird verhindert, dass die Mailboxansageregel beim Empfang eines eingehenden Anrufs verarbeitet wird, bevor Sie die Mailboxansageregel ordnungsgemäß konfiguriert haben.

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith deaktiviert.

    Disable -UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith

In diesem Beispiel wird die Option *WhatIf* verwendet, um zu testen, ob die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith deaktiviert werden kann und ob innerhalb des Befehls Fehler vorliegen.

    Disable -UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -WhatIf

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` im Postfach für Tony Smith deaktiviert, und der angemeldete Benutzer wird aufgefordert, das Deaktivieren der Mailboxansageregel zu bestätigen.

    Disable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -Confirm

