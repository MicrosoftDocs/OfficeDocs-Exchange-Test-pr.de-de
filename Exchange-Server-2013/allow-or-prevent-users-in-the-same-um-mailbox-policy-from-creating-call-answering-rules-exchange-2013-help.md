---
title: 'Zulassen oder Verhindern von Anrufantwortregeln in UM-Postfachrichtlinie'
TOCTitle: Ermöglichen Sie oder verhindern Sie, dass Benutzer in der gleichen UM-Postfachrichtlinie erstellen Aufruf von mailboxansageregeln
ms:assetid: e44acaa6-d5a8-41e8-94aa-100be0bd6391
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351209(v=EXCHG.150)
ms:contentKeyID: 50554934
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen Sie oder verhindern Sie, dass Benutzer in der gleichen UM-Postfachrichtlinie erstellen Aufruf von mailboxansageregeln

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können das Konfigurieren von Mailboxansageregeln durch Benutzer, die einer UM-Postfachrichtlinie zugeordnet sind, zulassen oder unterbinden. Wenn die Option zum Konfigurieren von Mailboxansageregeln für einen UM-Wählplan deaktiviert ist, steht diese Funktion für UM-aktivierte Benutzer, die dieser UM-Postfachrichtlinie unterliegen, nicht zur Verfügung. Die Option ist standardmäßig aktiviert.

Informationen zu weiteren Verwaltungsaufgaben zum Zulassen, dass Benutzer Anrufe weiterleiten, finden Sie unter [Weiterleiten von Anrufen Prozeduren](forwarding-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren von Mailboxansageregeln für eine UM-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **UM-Postfachrichtlinien** das Kontrollkästchen neben **Konfigurieren von Mailboxansageregeln durch Benutzer zulassen**.

4.  Klicken Sie auf **Speichern**.

## Aktivieren oder Deaktivieren von Mailboxansageregeln für eine UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel dürfen der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnete Benutzer Mailboxansageregeln erstellen.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowCallAnsweringRules $true

In diesem Beispiel wird verhindert, dass die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordneten Benutzer Mailboxansageregeln erstellen können.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowCallAnsweringRules $false

