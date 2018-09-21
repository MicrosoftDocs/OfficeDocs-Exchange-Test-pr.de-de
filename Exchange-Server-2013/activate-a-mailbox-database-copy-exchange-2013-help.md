---
title: 'Aktivieren einer Kopie einer Postfachdatenbank: Exchange 2013 Help'
TOCTitle: Aktivieren einer Kopie einer Postfachdatenbank
ms:assetid: d948269b-c902-4d8d-8c2b-269473359baa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364750(v=EXCHG.150)
ms:contentKeyID: 50476863
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren einer Kopie einer Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-01_

Beim Aktivieren einer Postfachdatenbankkopie wird eine bestimmte passive Kopie als neue aktive Kopie einer Postfachdatenbank festgelegt. Dieser Vorgang wird als *Datenbankswitchover* bezeichnet. Beim Datenbankswitchover wird die Einbindung der gegenwärtig aktiven Datenbank aufgehoben, und die Datenbankkopie wird auf dem angegebenen Server als neue aktive Postfachdatenbankkopie eingebunden. Die Datenbankkopie, die als aktive Postfachdatenbank festgelegt wird, muss einen fehlerfreien Zustand aufweisen und aktuell sein.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Kopien von Postfachdatenbanken gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verschieben der aktiven Postfachdatenbank mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, deren Kopie Sie aktivieren möchten.

3.  Klicken Sie im Detailbereich unter **Datenbankkopien** unter der Datenbankkopie, die Sie aktivieren möchten, auf **Aktivieren**.

4.  Klicken Sie auf **Ja**, um die Datenbankkopie zu aktivieren.

## Verschieben der aktiven Postfachdatenbank mithilfe der Shell

Bei diesem Beispiel wird eine Kopie der auf MBX3 gehosteten Datenbank DB4 als neue aktive Postfachdatenbank aktiviert und bereitgestellt. Über diesen Befehl wird DB4 die neue aktive Postfachdatenbank, und die Wähleinstellungen für die Datenbankeinbindung auf MBX3 werden nicht außer Kraft gesetzt.

```powershell
Move-ActiveMailboxDatabase DB4 -ActivateOnServer MBX3 -MountDialOverride:None
```

In diesem Beispiel wird ein Switchover der Datenbank DB2 auf den Postfachserver MBX1 ausgeführt. Wenn der Befehl abgeschlossen ist, hostet MBX1 die aktive Kopie von DB2. Da der Parameter *MountDialOverride* auf `None` festgelegt ist, bindet MBX1 die Datenbank mit den eigenen definierten AutoDatabaseMountDial-Einstellungen ein.

```powershell
Move-ActiveMailboxDatabase DB2 -ActivateOnServer MBX1 -MountDialOverride:None
```

In diesem Beispiel wird ein Switchover der Datenbank DB1 auf den Postfachserver MBX3 ausgeführt. Wenn der Befehl abgeschlossen ist, hostet MBX3 die aktive Kopie von DB1. Da für den Parameter *MountDialOverride* der Wert `Good Availability` angegeben ist, bindet MBX3 die Datenbank mit der AutoDatabaseMountDial-Einstellung *GoodAvailability* ein.

```powershell
Move-ActiveMailboxDatabase DB1 -ActivateOnServer MBX3 -MountDialOverride:GoodAvailability
```

In diesem Beispiel wird ein Switchover der Datenbank DB3 auf den Postfachserver MBX4 ausgeführt. Wenn der Befehl abgeschlossen ist, hostet MBX4 die aktive Kopie von DB3. Da der Parameter *MountDialOverride* nicht angegeben ist, bindet MBX4 die Datenbank mit der AutoDatabaseMountDial-Einstellung *Lossless* ein.

```powershell
Move-ActiveMailboxDatabase DB3 -ActivateOnServer MBX4
```

In diesem Beispiel wird ein Serverswitchover für den Postfachserver MBX1 ausgeführt. Alle aktiven Postfachdatenbankkopien auf MBX1 werden auf einem oder mehreren anderen Postfachservern mit fehlerfreien Kopien der aktiven Datenbanken auf MBX1 aktiviert.

```powershell
Move-ActiveMailboxDatabase -Server MBX1
```

In diesem Beispiel wird ein Switchover der Datenbank DB4 auf den Postfachserver MBX5 ausgeführt. In diesem Beispiel verfügt die Datenbankkopie auf MBX5 über eine Wiedergabewarteschlange mit mehr als sechs Elementen. Folglich muss der Parameter *SkipLagChecks* angegeben werden, um die Datenbankkopie auf MBX5 zu aktivieren.

```powershell
Move-ActiveMailboxDatabase DB4 MBX5 -SkipLagChecks
```

In diesem Beispiel wird ein Switchover der Datenbank DB5 auf den Postfachserver MBX6 ausgeführt. In diesem Beispiel weist der Parameter *ContentIndexState* der Datenbankkopie auf MBX6 den Wert Failed auf. Folglich muss der Parameter *SkipClientExperienceChecks* angegeben werden, um die Datenbankkopie auf MBX6 zu aktivieren.

```powershell
Move-ActiveMailboxDatabase DB5 MBX6 -SkipClientExperienceChecks
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Aktivierung einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die geeignete Datenbank aus, und klicken Sie im Detailbereich auf **Details anzeigen**, um die Eigenschaften der Datenbankkopie anzuzeigen.

  - Führen Sie in der Shell den folgenden Befehl aus, um Statusinformationen zu einer Datenbankkopie anzuzeigen.
    
    ```powershell
Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List
```

## Weitere Informationen

[Postfachdatenbankkopien](mailbox-database-copies-exchange-2013-help.md)

[Konfigurieren der Eigenschaften von Postfachdatenbankkopien](configure-mailbox-database-copy-properties-exchange-2013-help.md)

