---
title: 'Konfig. d. Aktiv.richtl. f. Kopie e. Postfachdatenbank: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren der Aktivierungsrichtlinie für die Kopie einer Postfachdatenbank
ms:assetid: 6b37ed6e-2e36-4688-b485-8fdbb8193ec8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298046(v=EXCHG.150)
ms:contentKeyID: 50475885
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Aktivierungsrichtlinie für die Kopie einer Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-02_

Als *Aktivierung* einer Postfachdatenbankkopie wird die Umwandlung von einer passiven Kopie in eine aktive Kopie bezeichnet. Die Aktivierung wird automatisch vom während eines Failovers einer Datenbank oder eines Servers ausgeführt, kann jedoch auch manuell von einem Administrator im Rahmen eines Switchovervorgangs für eine Datenbank oder einen Server ausgeführt werden. Durch Sperren einer Datenbank für die Aktivierung kann verhindert werden, dass sie bei einem Datenbank- oder Serverfailover zur aktiven Kopie wird.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Postfachdatenbankkopien gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Aktivierungsrichtlinie für eine Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, die Sie konfigurieren möchten.

3.  Suchen Sie im Detailbereich unter **Datenbankkopien** die Datenbankkopie, die Sie konfigurieren möchten, und klicken Sie auf **Anhalten**.

4.  Fügen Sie optional einen Kommentar hinzu, und aktivieren Sie das Kontrollkästchen **Diese Kopie kann nur durch manuellen Eingriff aktiviert werden**.

5.  Klicken Sie auf **Speichern**, um die Konfigurationsänderungen für die Postfachdatenbankkopie zu speichern.

## Anhalten oder Fortsetzen der Aktivierung einer Datenbankkopie mithilfe der Shell

In diesem Beispiel wird die Kopie der Datenbank "DB1" auf dem Server "MBX2" für die Aktivierung gesperrt.

```powershell
    Suspend-MailboxDatabaseCopy -Identity DB1\MBX2 -ActivationOnly
```

In diesem Beispiel wird die Sperre der Aktivierung bei der Kopie der Datenbank "DB1" auf dem Server "MBX2" aufgehoben.

```powershell
    Resume-MailboxDatabaseCopy -Identity DB1\MBX2
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) oder [Resume-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335220\(v=exchg.150\)).

## Konfigurieren der Aktivierungsrichtlinie für einen Server mithilfe der Shell

In diesem Beispiel werden die Datenbankkopien auf MBX2 so konfiguriert, dass sie für die Aktivierung gesperrt sind.

```powershell
Set-MailboxServer -Identity MBX2 -DatabaseCopyAutoActivationPolicy Blocked
```

In diesem Beispiel werden die Datenbankkopien auf MBX3 so konfiguriert, dass sie für die Aktivierung außerhalb des Standorts gesperrt sind.

```powershell
Set-MailboxServer -Identity MBX3 -DatabaseCopyAutoActivationPolicy IntrasiteOnly
```

In diesem Beispiel werden die Datenbankkopien auf MBX4 so konfiguriert, dass Aktivierungssperre aufgehoben wird.

```powershell
Set-MailboxServer -Identity MBX4 -DatabaseCopyAutoActivationPolicy Unrestricted
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)), [Resume-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335220\(v=exchg.150\)) oder [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Aktivierungsrichtlinie zu überprüfen:

  - Führen Sie in der Shell den folgenden Befehl aus, um die Aktivierungseinstellungen für eine Datenbankkopie zu überprüfen:
    
    ```powershell
    Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List ActivationSuspended
    ```

  - Führen Sie in der Shell den folgenden Befehl aus, um die Aktivierungseinstellungen für ein DAG-Mitglied zu überprüfen:
    
    ```powershell
    Get-MailboxServer <ServerName> | Format-List DatabaseCopyAutoActivationPolicy
    ```

