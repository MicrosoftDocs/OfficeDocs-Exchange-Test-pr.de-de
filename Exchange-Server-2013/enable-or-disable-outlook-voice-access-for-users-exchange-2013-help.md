---
title: 'Aktivieren oder Deaktivieren von Outlook Voice Access für Benutzer: Exchange Online Help'
TOCTitle: Aktivieren oder Deaktivieren von Outlook Voice Access für Benutzer
ms:assetid: c0c244a0-ad2f-4adf-bc1f-1d55fd7ea2d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351106(v=EXCHG.150)
ms:contentKeyID: 52062774
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren von Outlook Voice Access für Benutzer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-12-12_

Der Zugriff auf Outlook Voice Access kann für UM-aktivierte Benutzer, die einer UM-Postfachrichtlinie (Unified Messaging) zugeordnet sind, aktiviert oder deaktiviert werden. Mit Outlook Voice Access können UM-aktivierte Benutzer über ein Telefon auf ihr Postfach zugreifen. Diese Einstellung ist standardmäßig aktiviert.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren von Outlook Voice Access mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie auf der Seite **UM-Postfachrichtlinie** das Kontrollkästchen für **Outlook Voice Access zulassen**.

4.  Klicken Sie auf **Speichern**.

## Aktivieren oder Deaktivieren von Outlook Voice Access mithilfe der Shell

Im folgenden Beispiel wird Benutzern, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, die Verwendung von Outlook Voice Access ermöglicht.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowSubscriberAccess $true

In diesem Beispiel wird verhindert, dass die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordneten Benutzer Outlook Voice Access verwenden können.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowSubscriberAccess $false

