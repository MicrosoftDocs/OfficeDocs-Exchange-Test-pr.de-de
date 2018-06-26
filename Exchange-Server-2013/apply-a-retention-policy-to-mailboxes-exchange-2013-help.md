---
title: 'Anwenden einer Aufbewahrungsrichtlinie auf Postfächer: Exchange 2013 Help'
TOCTitle: Anwenden einer Aufbewahrungsrichtlinie auf Postfächer
ms:assetid: 6ccc80db-d201-44f7-8d4b-473a89c14b2f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298052(v=EXCHG.150)
ms:contentKeyID: 50475945
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anwenden einer Aufbewahrungsrichtlinie auf Postfächer

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-10-01_

Aufbewahrungsrichtlinien ermöglichen Ihnen das Gruppieren eines oder mehrerer Aufbewahrungstags, um diese zur Durchsetzung von Nachrichtenaufbewahrungseinstellungen auf Postfächer anzuwenden. Ein Postfach kann nur eine Aufbewahrungsrichtlinie aufweisen.


> [!WARNING]
> Nachrichten laufen auf der Grundlage von Einstellungen ab, die in den mit der Richtlinie verknüpften Aufbewahrungstags definiert sind. Zu diesen Einstellungen gehören Aktionen wie das Verschieben von Nachrichten in das Archiv oder das endgültige Löschen. Vor dem Anwenden einer Aufbewahrungsrichtlinie auf ein oder mehrere Postfächer sollten Sie die Richtlinie testen und die zugeordneten Aufbewahrungstags prüfen.



Weitere Verwaltungsaufgaben im Zusammenhang mit der Messaging-Datensatzverwaltung (MRM) finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Anwenden von Aufbewahrungsrichtlinien" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anwenden einer Aufbewahrungsrichtlinie auf ein einzelnes Postfach mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dem Sie die Aufbewahrungsrichtlinie hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie in **Benutzerpostfach** auf **Postfachfunktionen**.

4.  Wählen Sie in der Liste **Aufbewahrungsrichtlinie** die Richtlinie aus, die auf das Postfach angewendet werden soll, und klicken Sie auf **Speichern**.

## Anwenden einer Aufbewahrungsrichtlinie auf mehrere Postfächer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Verwenden Sie in der Listenansicht die UMSCHALT- oder die STRG-TASTE, um mehrere Postfächer auszuwählen.

3.  Klicken Sie im Detailbereich auf **Weitere Optionen**.

4.  Klicken Sie unter **Aufbewahrungsrichtlinie** auf **Aktualisieren**.

5.  Wählen Sie in der Liste **Massenzuweisung von Aufbewahrungsrichtlinie** die Aufbewahrungsrichtlinie aus, die auf die Postfächer angewendet werden soll, und klicken Sie auf **Speichern**.

## Anwenden einer Aufbewahrungsrichtlinie auf ein einzelnes Postfach mithilfe der Shell

In diesem Beispiel wird die Aufbewahrungsrichtlinie "RP-Finance" auf das Postfach von Morris angewendet.

    Set-Mailbox "Morris" -RetentionPolicy "RP-Finance"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Anwenden einer Aufbewahrungsrichtlinie auf mehrere Postfächer mithilfe der Shell

In diesem Beispiel wird die neue Aufbewahrungsrichtlinie "New-Retention-Policy" auf alle Postfächer angewendet, die über die alte Richtlinie "Old-Retention-Policy" verfügen.

    $OldPolicy={Get-RetentionPolicy "Old-Retention-Policy"}.distinguishedName
    Get-Mailbox -Filter {RetentionPolicy -eq $OldPolicy} -Resultsize Unlimited | Set-Mailbox -RetentionPolicy "New-Retention-Policy"

In diesem Beispiel wird die Aufbewahrungsrichtlinie "RetentionPolicy-Corp" auf alle Postfächer in der Exchange-Organisation angewendet.

    Get-Mailbox -ResultSize unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Corp"

In diesem Beispiel wird die Aufbewahrungsrichtlinie "RetentionPolicy-Finance" auf alle Postfächer in der Organisationseinheit für Finanzen angewendet.

    Get-Mailbox -OrganizationalUnit "Finance" -ResultSize Unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Finance"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) und [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Überprüfen, ob die Aufbewahrungsrichtlinie angewendet wurde, führen Sie das Cmdlet [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) aus, um die Aufbewahrungsrichtlinie für das Postfach bzw. die Postfächer abzurufen.

In diesem Beispiel wird die Aufbewahrungsrichtlinie für das Postfach von Morris abgerufen.

    Get-Mailbox Morris | Select RetentionPolicy

Dieser Befehl ruft alle Postfächer ab, auf die die Aufbewahrungsrichtlinie "RP-Finance" angewendet wird.

    Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionPolicy -eq "RP-Finance"} | Format-Table Name,RetentionPolicy -Auto

