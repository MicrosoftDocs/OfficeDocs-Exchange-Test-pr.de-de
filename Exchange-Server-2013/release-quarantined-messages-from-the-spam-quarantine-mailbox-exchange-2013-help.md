---
title: 'Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam: Exchange 2013 Help'
TOCTitle: Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam
ms:assetid: 7a86bfde-f868-4689-bdec-5f01e52b510d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998920(v=EXCHG.150)
ms:contentKeyID: 50476076
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können Microsoft Outlook verwenden, um eine Nachricht in Quarantäne aus dem Spamquarantänepostfach wiederherzustellen.

Die Spamquarantäne ist eine Funktion des Inhaltsfilter-Agents, durch die das Risiko reduziert wird, dass legitime Nachrichten verloren gehen. Wenn eine Nachricht den Schwellenwert für Quarantäne erreicht, wird sie in einen Unzustellbarkeitsbericht (NDR, Non-Delivery Report) aufgenommen und an das Quarantänepostfach für Spam übergeben. Weitere Informationen zur Spam-Quarantänefunktion finden Sie unter [Quarantänepostfach für Spam](spam-quarantine-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachzugriff" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Für dieses Verfahren muss das Antispam-Quarantänepostfach konfiguriert sein. Weitere Informationen finden Sie unter [Konfigurieren eines Spamquarantänepostfachs](configure-a-spam-quarantine-mailbox-exchange-2013-help.md).

  - Um das Quarantänepostfach zuzugreifen, müssen Sie ein Outlook-Profil für dieses Postfach zu konfigurieren, und öffnen Sie das Postfach mithilfe von Outlook. Weitere Informationen zum Konfigurieren und verwenden mehrere Outlook-Profilen finden Sie unter [Übersicht über die in Outlook](https://go.microsoft.com/fwlink/p/?linkid=178975).

  - Um die Suche nach der wiederherzustellenden Nachricht zu erleichtern, können Sie ein benutzerdefiniertes Outlook-Formular erstellen und die Standardansicht so ändern, dass die ursprüngliche Absenderadresse in der Nachrichtenliste angezeigt wird. Weitere Informationen finden Sie unter [Konfigurieren von Outlook zum Anzeigen des ursprünglichen Absenders im Quarantänepostfach](configure-outlook-to-show-the-original-sender-in-the-quarantine-mailbox-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Freigeben einer Nachricht aus dem Spamquarantänepostfach mithilfe von Outlook 2010 oder Outlook 2013

1.  Öffnen Sie das Quarantänepostfach auf einem Clientcomputer in Outlook 2010 oder Outlook 2013.

2.  Suchen Sie in der Ansicht **E-Mail** die wiederherzustellende Nachricht im **Posteingang**, und doppelklicken Sie darauf, um sie zu öffnen.

3.  Klicken Sie im Menüband im Bereich **Verschieben** auf **Aktionen** \> **Diese Nachricht erneut senden**.

4.  Wenn die Nachricht geöffnet wird, klicken Sie auf **Senden**, um die Nachricht erneut an den vorgesehenen Empfänger zu senden.

## Freigeben einer Nachricht aus dem Spam-Quarantänepostfach mithilfe von Outlook 2007

1.  Öffnen Sie das Quarantänepostfach auf einem Clientcomputer in Outlook 2007.

2.  Suchen Sie in der Ansicht **E-Mail-Ordner** die wiederherzustellende Nachricht im **Posteingang**, und doppelklicken Sie darauf, um sie zu öffnen.

3.  Klicken Sie auf der Registerkarte **Bericht** in der Gruppe **Antworten** auf **Erneut senden**.

4.  Wenn die Nachricht geöffnet wird, klicken Sie auf **Senden**, um die Nachricht erneut an den vorgesehenen Empfänger zu senden.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Überprüfen, ob die Nachricht erfolgreich aus dem Spamquarantänepostfach freigegeben wurde, wenden Sie sich an den Empfänger, und fragen Sie, ob die E-Mail empfangen wurde.

