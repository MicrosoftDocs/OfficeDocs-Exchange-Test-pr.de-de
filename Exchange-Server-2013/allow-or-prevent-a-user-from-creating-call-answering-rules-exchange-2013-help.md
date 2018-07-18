---
title: 'Ermöglichen Sie oder verhindern Sie, dass einen Benutzer erstellen Aufruf von mailboxansageregeln: Exchange Online Help'
TOCTitle: Ermöglichen Sie oder verhindern Sie, dass einen Benutzer erstellen Aufruf von mailboxansageregeln
ms:assetid: 81863440-8b21-4523-bdab-6a2311889a0d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298097(v=EXCHG.150)
ms:contentKeyID: 50554857
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen Sie oder verhindern Sie, dass einen Benutzer erstellen Aufruf von mailboxansageregeln

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können angeben, ob einzelne Benutzer in der Lage sein sollen, ihre eigenen Regeln für die Mailboxansage zu erstellen und zu verwalten, indem sie ihre Postfacheigenschaften konfigurieren. Standardmäßig können diese Benutzer Anrufbeantwortungsregeln erstellen.

Durch Konfigurieren von Mailboxansageregeln für einen UM-Wählplan oder eine UM-Postfachrichtlinie können Sie Mailboxansageregeln für mehrere Benutzer aktivieren oder deaktivieren, die für Unified Messaging (UM) aktiviert sind.


> [!NOTE]
> Diese Funktion kann nicht mit der Exchange-Verwaltungskonsole konfiguriert werden. Sie müssen zum Aktivieren oder Deaktivieren von Mailboxansageregeln die Shell verwenden.



Informationen zu weiteren Verwaltungsaufgaben zum Zulassen, dass Benutzer Anrufe weiterleiten, finden Sie unter [Weiterleiten von Anrufen Prozeduren](forwarding-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Aktivieren oder Deaktivieren von Regeln für die Mailboxansage für einen UM-aktivierten Benutzer

In diesem Beispiel werden für den Benutzer "tony@contoso.com" die Regeln für die Mailboxansage aktiviert.

    Set-UMMailbox -Identity tony@contoso.com -CallAnsweringRulesEnabled $true

In diesem Beispiel werden für den Benutzer "thorsten@contoso.com" die Regeln für die Mailboxansage deaktiviert.

    Set-UMMailbox -Identity tony@contoso.com -CallAnsweringRulesEnabled $false

