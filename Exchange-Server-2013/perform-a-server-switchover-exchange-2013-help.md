---
title: 'Ausführen eines Serverswitchovers: Exchange 2013 Help'
TOCTitle: Ausführen eines Serverswitchovers
ms:assetid: ffcefd56-b0a0-4229-9011-fff4197b7c74
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298187(v=EXCHG.150)
ms:contentKeyID: 62523872
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ausführen eines Serverswitchovers

 

_**Gilt für:** Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2014-06-23_

Ein Serverswitchover ist eine Aufgabe, die Sie durchführen, um alle aktiven Postfachdatenbankkopien vom aktuellen Postfachserver auf einen oder mehrere Postfachserver in einer Datenbankverfügbarkeitsgruppe zu verschieben. Diese Aufgabe wird typischerweise im Rahmen der Vorbereitung für einen geplanten Ausfall des aktuellen Postfachservers ausgeführt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Sekunden pro Datenbank

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Durchführen eines Serverswitchovers mithilfe des EAC

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

1.  Navigieren Sie im Exchange Admin Center zu **Server** \> **Server**.

2.  Wählen Sie den Postfachserver aus, für den Sie den Switchover durchführen möchten.

3.  Wählen Sie im Detailbereich **Serverswitchover** aus.

4.  Führen Sie auf der Seite **Serverswitchover** einen der folgenden Schritte durch:
    
    1.  Übernehmen Sie die Standardeinstellung **Automatisch einen Zielserver auswählen**. (In diesem Fall wählt das System automatisch den besten Postfachserver für jede Datenbank aus, die verschoben werden soll.) Klicken Sie anschließend auf **Speichern**.
    
    2.  Klicken Sie auf **Den angegebenen Server als Ziel für Switchover verwenden**, klicken Sie auf **Durchsuchen**, um einen Postfachserver auszuwählen, und klicken Sie anschließend auf **Speichern**.

5.  Wenn der Switchover abgeschlossen ist, klicken Sie auf **Schließen**, um die Seite **Serverswitchover** zu verlassen.

## Durchführen eines Serverswitchovers mithilfe der Shell

In diesem Beispiel wird ein Serverswitchover für den Server MBX1 ausgeführt. Das System wählt automatisch den besten Postfachserver für jede aktive Datenbank auf MBX1 aus.

    Move-ActiveMailboxDatabase -Server MBX1

In diesem Beispiel wird ein Serverswitchover des Postfachservers MBX4 ausgeführt. Nach Abschluss des Befehls hostet MBX5 die aktive Kopie der Datenbanken, die zuvor auf MBX4 aktiv waren.

    Move-ActiveMailboxDatabase -Server MBX4 -ActivateOnServer MBX5

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)).

