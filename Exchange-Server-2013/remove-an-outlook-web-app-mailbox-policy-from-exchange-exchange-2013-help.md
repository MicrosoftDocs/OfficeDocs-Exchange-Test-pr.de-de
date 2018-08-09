---
title: 'Entf. einer Outlook Web App-Postfachrichtl. aus Exchange: Exchange 2013-Hilfe'
TOCTitle: Entfernen einer Outlook Web App-Postfachrichtlinie aus Exchange
ms:assetid: edab7bac-b62c-4b82-8f21-dcac77cf0e8f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351239(v=EXCHG.150)
ms:contentKeyID: 50477020
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Outlook Web App-Postfachrichtlinie aus Exchange

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-03-15_

Sie können eine MicrosoftOutlook Web App-Postfachrichtlinie aus einer Exchange-Organisation entfernen, indem Sie entweder die Exchange-Verwaltungskonsole oder die Shell verwenden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outlook Web App-Postfachrichtlinien finden Sie unter [Outlook Web App-Postfachrichtlinien](outlook-web-app-mailbox-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Web App-Postfachrichtlinien" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen einer Outlook Web App-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**.

2.  Klicken Sie im Ergebnisbereich, um die zu entfernende Postfachrichtlinie auszuwählen.

3.  Klicken Sie auf die Schaltfläche **Löschen**.

4.  Klicken Sie im Bestätigungsfenster auf **Ja**, um die Postfachrichtlinie zu entfernen, bzw. auf **Nein**, um den Vorgang abzubrechen.

## Entfernen einer Outlook Web App-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird die Outlook Web App-Postfachrichtlinie `Policy1` entfernt.

    Remove-OwaMailboxPolicy -Name Policy1 

Weitere Informationen zu Syntax und Parametern finden Sie unter [Remove-OwaMailboxPolicy](https://technet.microsoft.com/de-de/library/dd298103\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass Sie eine Outlook Web App-Postfachrichtlinie erfolgreich entfernt haben:

  - Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**. Die Richtlinie sollte nicht länger in der Liste angezeigt werden.

