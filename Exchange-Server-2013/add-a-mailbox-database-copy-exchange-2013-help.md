---
title: 'Hinzufügen einer Kopie einer Postfachdatenbank: Exchange 2013 Help'
TOCTitle: Hinzufügen einer Kopie einer Postfachdatenbank
ms:assetid: 784bf48f-8af5-422c-a63f-2f01fc0cf151
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298080(v=EXCHG.150)
ms:contentKeyID: 50476046
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hinzufügen einer Kopie einer Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-30_

Wenn Sie eine Kopie einer Postfachdatenbank hinzufügen, wird automatisch die fortlaufende Replikation zwischen der vorhandenen Datenbank und der Datenbankkopie aktiviert. Datenbankkopien wird automatisch eine Identität im Format \<*Datenbankname*\>\\\<*PostfachHostServerName*\> zugewiesen. Beispielsweise erhält die Kopie der Datenbank "DB1", die auf dem Server "MBX3" gehostet wird, den Namen "DB1\\MBX3".

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Kopien von Postfachdatenbanken gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 Minuten, plus die Zeit, die für das Seeding der Datenbankkopie erforderlich ist. Dies ist abhängig von einer Vielzahl von Faktoren, beispielsweise von der Größe der Datenbank, der Geschwindigkeit, der verfügbaren Bandbreite, der Netzwerklatenz sowie der Speichergeschwindigkeit.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Die aktive Kopie der Datenbank muss bereitgestellt sein.

  - Auf dem angegebenen Postfachserver darf sich noch keine Kopie der Datenbank befinden.

  - Der Pfad für die angegebene Datenbankkopie und deren Protokolldateien muss auf dem ausgewählten Postfachserver verfügbar sein.

  - Der Hostserver der aktiven Kopie und der Server, der die passive Kopie hosten soll, müssen sich in derselben Database Availability Group (DAG) befinden. Außerdem muss die DAG ein Quorum aufweisen und fehlerfrei sein.

  - Wenn Sie die zweite Kopie einer Datenbank hinzufügen (beispielsweise indem Sie die erste passive Kopie der Datenbank erstellen), darf die Umlaufprotokollierung für die angegebene Postfachdatenbank nicht aktiviert sein. Ist die Umlaufprotokollierung aktiviert, muss sie zunächst deaktiviert werden. Nachdem die Kopie der Postfachdatenbank hinzugefügt wurde, kann die Umlaufprotokollierung wieder aktiviert werden. Nach der Aktivierung der Umlaufprotokollierung für eine replizierte Postfachdatenbank wird die Umlaufprotokollierung der fortlaufenden Replikation (Continuous Replication Circular Logging, CRCL) anstelle der JET-Umlaufprotokollierung verwendet. Wenn Sie die dritte oder nachfolgende Kopie einer Datenbank hinzufügen, müssen Sie CRCL nicht deaktivieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Hinzufügen einer Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, die Sie kopieren möchten, und klicken Sie dann auf ![Hinzufügen von Datenbankkopien](images/Dd298080.435c15ff-abf2-4de8-b280-f053db1afa13(EXCHG.150).gif "Hinzufügen von Datenbankkopien").

3.  Klicken Sie auf der Seite **Postfachdatenbankkopie hinzufügen** auf **Durchsuchen...**, wählen Sie den Postfachserver aus, der die Datenbankkopie hosten soll, und klicken Sie dann auf **OK**.

4.  Konfigurieren Sie optional die **Aktivierungseinstellungsnummer** für die Datenbankkopie.

5.  Klicken Sie auf **Weitere Optionen…**, um die Datenbankkopie als verzögerte Datenbankkopie festzulegen, indem Sie einen Wiedergabeverzögerungszeitraum konfigurieren, oder um das automatische Seeding der Datenbankkopie zu verschieben.

6.  Klicken Sie auf **Speichern**, um die Konfigurationsänderungen zu speichern und die Postfachdatenbankkopie hinzuzufügen.

7.  Klicken Sie auf **OK**, um alle angezeigten Meldungen zu bestätigen.

## Hinzufügen einer Kopie einer Postfachdatenbank mithilfe der Shell

In diesem Beispiel wird dem Postfachserver MBX3 eine Kopie der Postfachdatenbank "DB1" hinzugefügt. Wiedergabeverzögerung und Abschneideverzögerung werden jeweils auf dem Standardwert 0 belassen, während die Aktivierungseinstellung mit dem Wert 2 konfiguriert wird.

```powershell
Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX3 -ActivationPreference 2
```

In diesem Beispiel wird dem Postfachserver "MBX4" eine Kopie der Postfachdatenbank "DB2" hinzugefügt. Wiedergabeverzögerung und Abschneideverzögerung werden jeweils auf dem Standardwert 0 belassen, während die Aktivierungseinstellung mit dem Wert `5` konfiguriert wird. Darüber hinaus wird das Seeding für diese Kopie verschoben, damit es mit einem lokalen Quellserver anstatt mit der aktuellen aktiven Datenbankkopie erfolgen kann, die von "MBX4" geografisch entfernt ist.

```powershell
Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX4 -ActivationPreference 5 -SeedingPostponed
```

In diesem Beispiel wird dem Postfachserver "MBX5" eine Kopie der Postfachdatenbank "DB3" hinzugefügt. Die Wiedergabeverzögerung wird auf 3 Tage festgelegt und die Abschneideverzögerung auf dem Standardwert 0 belassen, während die Aktivierungseinstellung mit dem Wert `4` konfiguriert wird.

    Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX5 -ReplayLagTime 3.00:00:00 -ActivationPreference 4

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Erstellung einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die Datenbank aus, die kopiert wurde. Im Detailbereich werden der Status der Datenbankkopie und der zugehörige Inhaltsindex angezeigt, zusammen mit der aktuellen Länge der Datenbankwarteschlange.

  - Führen Sie in der Shell den folgenden Befehl aus, um sicherzustellen, dass die Postfachdatenbankkopie erstellt wurde und sich in einem fehlerfreien Zustand befindet:
    
    ```powershell
Get-MailboxDatabaseCopyStatus <DatabaseCopyName>
```
    
    Status und Inhaltsindexzustand sollten beide den Wert Fehlerfrei anzeigen.

## Weitere Informationen

[Postfachdatenbankkopien](mailbox-database-copies-exchange-2013-help.md)

[Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md)

