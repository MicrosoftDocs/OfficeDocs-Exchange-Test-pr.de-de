---
title: 'Konfigurieren Sie den Grenzwert auf persönliche Begrüßung für Outlook Voice Access-Benutzer: Exchange Online Help'
TOCTitle: Konfigurieren Sie den Grenzwert auf persönliche Begrüßung für Outlook Voice Access-Benutzer
ms:assetid: d400f250-0f55-45f5-9918-5f1d7819fbdf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201731(v=EXCHG.150)
ms:contentKeyID: 50554917
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie den Grenzwert auf persönliche Begrüßung für Outlook Voice Access-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Über die Einstellung **Beschränkung der persönlichen Begrüßungstexte (Minuten)** können Sie die maximale Dauer in Minuten angeben, die Benutzer, die der Unified Messaging-Postfachrichtlinie (UM) unterliegen, zum Aufzeichnen von Voicemailbegrüßungen verwenden können. Diese Einstellung gilt sowohl für die Standardvoicemail- als auch für Abwesenheitsansagen. Standardmäßig ist die maximale Dauer der Begrüßung auf fünf Minuten festgelegt. Sie können jedoch nach Wunsch einen Wert von 1 bis 10 Minuten festlegen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der maximalen Begrüßungsdauer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Allgemein** unter **Beschränkung der persönlichen Begrüßungstexte (Minuten)** die Anzahl der Minuten ein, die Voicemailbenutzer für persönliche Begrüßungen zur Verfügung stehen.

4.  Klicken Sie auf **Speichern**.

## Ändern der maximalen Begrüßungsdauer mithilfe der Shell

In diesem Beispiel wird die maximale Begrüßungsdauer für die UM-Postfachrichtlinie `MyUMMailboxPolicy` auf 3 Minuten festgelegt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy MaxGreetingDuration 3

