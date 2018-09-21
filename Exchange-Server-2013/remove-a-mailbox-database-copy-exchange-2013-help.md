---
title: 'Entfernen einer Postfachdatenbankkopie: Exchange 2013 Help'
TOCTitle: Entfernen einer Postfachdatenbankkopie
ms:assetid: 99fecdde-b158-4dfc-9ca7-ff7c0ada7819
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298164(v=EXCHG.150)
ms:contentKeyID: 50476297
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer Postfachdatenbankkopie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-06_

Diese Verfahren zeigen, wie Sie die Kopie einer Postfachdatenbank entfernen. Mithilfe dieser Schritte können Sie nicht die letzte Kopie einer Postfachdatenbank entfernen. Genaue Anweisungen zum Entfernen der letzen Kopie einer Postfachdatenbank finden Sie unter [Remove a mailbox database](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md) oder [Remove-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997931\(v=exchg.150\)).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Kopien von Postfachdatenbanken gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Kopien von Postfachdatenbanken können nur aus einer fehlerfreien Database Availability Group (DAG) entfernt werden. Ist eine solche Database Availability Group nicht fehlerfrei (weil beispielsweise der Cluster, in dem sich die Gruppe befindet, aufgrund von Quorumverlusten nicht verfügbar ist), können Sie keine Postfachdatenbankkopien entfernen.

  - Wenn Sie die letzte passive Kopie der Datenbank entfernen, darf die Umlaufprotokollierung der fortlaufenden Replikation (Continuous Replication Circular Logging, CRCL) für die angegebene Postfachdatenbank nicht aktiviert sein. Ist CRCL aktiviert, muss sie zunächst deaktiviert werden. Nachdem die Kopie der Postfachdatenbank entfernt wurde, kann die Umlaufprotokollierung wieder aktiviert werden. Sobald sie für eine nicht replizierte Postfachdatenbank aktiviert wurde, wird die JET-Umlaufprotokollierung anstelle von CRCL verwendet. Wenn Sie nicht die letzte passive Kopie einer Datenbank entfernen, müssen Sie CRCL nicht deaktivieren.

  - Nachdem Sie eine Datenbankkopie entfernt haben, müssen Sie manuell alle Datenbank- und Transaktionsprotokolldateien aus dem Server entfernen, aus dem die Datenbankkopie entfernt wurde.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen einer Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Postfachdatenbank aus, deren Kopie Sie entfernen möchten.

3.  Suchen Sie im Detailbereich die passive Kopie, die Sie entfernen möchten, und klicken Sie auf **Entfernen**.

4.  Bestätigen Sie das Entfernen im Warndialogfeld durch Klicken auf **Ja**.

5.  Klicken Sie auf **OK**, um das Entfernen nach der Überprüfung etwaiger Nachrichten zu bestätigen.

6.  Löschen Sie Datenbank- und Transaktionsprotokolldateien manuell vom Server, von dem die Datenbankkopie entfernt wurde.

## Verwenden der Shell zum Entfernen einer Postfachdatenbankkopie

In diesem Beispiel wird eine Kopie der Postfachdatenbank "DB1" vom Postfachserver "MBX1" entfernt.

    Remove-MailboxDatabaseCopy -Identity DB1\MBX1 -Confirm:$False

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Entfernung einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die entsprechende Datenbank aus. Im Detailbereich wird die entfernte passive Kopie nicht mehr aufgeführt.

  - Führen Sie in der Shell den folgenden Befehl aus, um das Entfernen der Kopie zu bestätigen.
    
    ```powershell
Get-MailboxDatabase <DatabaseName> | Format-List DatabaseCopies
```
    
    Die entfernte passive Kopie wird nicht mehr aufgeführt.

