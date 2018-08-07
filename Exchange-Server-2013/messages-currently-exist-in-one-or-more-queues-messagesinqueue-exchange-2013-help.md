---
title: 'Nachrichten befinden sich derzeit in einer oder mehreren Warteschlangen'
TOCTitle: Messages currently exist in one or more queues_MessagesInQueue
ms:assetid: 3ffcdc7e-c1b7-49a7-8e5f-b30c0397908d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.messagesinqueue(v=EXCHG.150)
ms:contentKeyID: 50475466
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Messages currently exist in one or more queues\_MessagesInQueue

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 zeigt diese Warnung an, da der Versuch der Deinstallation einer Transportfunktion zum Verlust von Daten in einer Transportwarteschlange führen kann.

Das Setup von Exchange 2007 prüft, ob die Transportwarteschlangen leer sind, bevor versucht wird, die mit der Verwaltung dieser Warteschlangen verknüpften Serverrollen zu entfernen.

Wenn Sie die Transportfunktionen vor der Übermittlung der noch in den Transportwarteschlangen enthaltenen Nachrichten entfernen, werden die Nachricht ggf. unbegrenzt lange aufbewahrt.

Untersuchen Sie zum Beheben dieses Problems die betreffenden Warteschlangen, um sicherzustellen, dass sie keine Nachrichten enthalten, bevor Sie das Setup fortsetzen.

**So zeigen Sie den Inhalt einer Warteschlange an**

1.  Öffnen Sie die Exchange-Verwaltungskonsole.

2.  Klicken Sie in der Konsolenstruktur auf **Toolbox**.

3.  Klicken Sie im Ergebnisbereich auf **Exchange-Warteschlangenanzeige**.

4.  Klicken Sie im Aktionsbereich auf **Tool öffnen**.

5.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht.

6.  Klicken Sie mit der rechten Maustaste auf die gewünschte Warteschlange, und wählen Sie **Eigenschaften** aus, um deren Eigenschaften anzuzeigen.

**So zeigen Sie die Nachrichten in einer Warteschlange an**

1.  Befolgen Sie die Schritte 1 bis 4.

2.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Eigenschaften**. Es wird eine Liste aller Nachrichten auf dem Server angezeigt, mit dem eine Verbindung besteht. Um die Ansicht auf eine einzelne Warteschlange einzuschränken, klicken Sie auf die Registerkarte **Warteschlangen**, doppelklicken Sie auf den Warteschlangennamen, und klicken Sie anschließend auf die angezeigte Registerkarte „Server\\Warteschlange“.

3.  Um detaillierte Informationen zu einer Nachricht anzuzeigen, wählen Sie eine Nachricht aus und klicken im Aktionsbereich auf **Eigenschaften**.

