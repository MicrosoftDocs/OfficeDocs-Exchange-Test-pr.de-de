---
title: 'Aktualisieren einer Postfachdatenbankkopie: Exchange 2013 Help'
TOCTitle: Aktualisieren einer Postfachdatenbankkopie
ms:assetid: bead3cc5-7d50-446f-95b7-e432bcb7968e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351100(v=EXCHG.150)
ms:contentKeyID: 50476600
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktualisieren einer Postfachdatenbankkopie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-02_

Als Aktualisieren oder *Seeding* wird der Vorgang bezeichnet, bei dem eine Kopie einer Postfachdatenbank einem anderen Postfachserver in einer Database Availability Group (DAG) hinzugefügt wird. Die neu hinzugefügte Kopie wird zur Grunddatenbank für die passive Kopie, in die Protokolldateien aus der aktiven Kopie übertragen werden. Seeding ist unter folgenden Bedingungen erforderlich:

  - Wenn eine neue passive Kopie einer Datenbank erstellt wird. Das Seeding kann bei einer neuen Postfachdatenbankkopie verschoben werden, doch letztlich muss für jede passive Datenbankkopie das Seeding durchgeführt werden, damit sie als redundante Datenbankkopie funktionieren kann.

  - Nach einem Failover, in dessen Verlauf Daten verloren gegangen sind, weil die passive Datenbankkopie abweicht und nicht wiederherstellbar ist.

  - Wenn das System eine fehlerhafte Protokolldatei entdeckt hat, die nicht in die passive Kopie der Datenbank wiedergegeben werden kann.

  - Nach einer Offlinedefragmentierung einer der Kopien der Datenbank.

  - Nachdem die Protokollgenerierungssequenz für die Datenbank auf 1 zurückgesetzt wurde.

Sie können das Seeding mithilfe einer der folgenden Methoden ausführen:

  - **Automatisches Seeding**   Beim automatischen Seeding wird auf dem Zielpostfachserver eine passive Kopie der aktiven Datenbank generiert. Das automatische Seeding erfolgt beim Erstellen einer Datenbank.

  - **Seeding unter Verwendung des Cmdlets "Update-MailboxDatabaseCopy"**   Mithilfe des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) können Sie in der Shell das Seeding einer Datenbankkopie jederzeit ausführen.

  - **Seeding mithilfe des Assistenten zum Aktualisieren von Postfachdatenbankkopien**   Mithilfe des Assistenten zum Aktualisieren von Postfachdatenbankkopien können Sie in der Exchange-Verwaltungskonsole das Seeding einer Datenbankkopie jederzeit ausführen.

  - **Manuelles Kopieren der Offlinedatenbank**   Sie können die Bereitstellung der aktiven Kopie der Datenbank aufheben und die Datenbankdatei an denselben Speicherort auf einem anderen Postfachserver in derselben DAG kopieren. Bei dieser Methode kommt es zu einer Betriebsunterbrechung, da es erforderlich ist, die Bereitstellung der Datenbank aufzuheben.

Das Aktualisieren einer Datenbankkopie kann viel Zeit in Anspruch nehmen, insbesondere wenn die kopierte Datenbank groß, die Netzwerklatenz hoch oder die Netzwerkbandbreite gering ist. Nach dem Start des Seedingprozesses dürfen Sie die Exchange-Verwaltungskonsole bzw. Shell erst nach Abschluss des Prozesses schließen. Andernfalls wird der Seedingvorgang beendet.

Für eine Datenbankkopie kann das Seeding entweder mithilfe der aktiven Kopie oder einer aktuellen passiven Kopie als Quelle des Seedings durchgeführt werden. Beim Seeding mithilfe einer passiven Kopie ist zu beachten, dass der Seedingvorgang unter folgenden Umständen mit einem Netzwerkkommunikationsfehler beendet wird:

  - Wenn sich der Status der Seedingquellkopie in "Failed" oder "FailedAndSuspended" ändert.

  - Wenn die Datenbank ein Failover in eine andere Kopie durchführt.

Für mehrere Datenbankkopien kann gleichzeitig ein Seeding durchgeführt werden. Doch wenn für mehrere Kopien gleichzeitig ein Seeding erfolgt, dürfen Sie nur für die Datenbankdatei ein Seeding durchführen und müssen den Inhaltsindexkatalog weglassen. Verwenden Sie hierzu den Parameter *DatabaseOnly* mit dem Cmdlet[Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)).


> [!NOTE]
> Wenn Sie bei einem Seeding mehrerer Ziele mithilfe derselben Quelle den Parameter <EM>DatabaseOnly</EM> nicht verwenden, tritt der "SeedInProgressException"-Fehler FE1C6491 auf.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Kopien von Postfachdatenbanken gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 Minuten, plus die Zeit, die für das Seeding der Datenbankkopie erforderlich ist. Dies ist abhängig von einer Vielzahl von Faktoren, beispielsweise von der Größe der Datenbank, der Geschwindigkeit, der verfügbaren Bandbreite, der Netzwerklatenz sowie der Speichergeschwindigkeit.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Die Postfachdatenbankkopie muss angehalten werden. Detaillierte Anweisungen finden Sie unter [Anhalten oder Fortsetzen der Kopie einer Postfachdatenbank](suspend-or-resume-a-mailbox-database-copy-exchange-2013-help.md).

  - Der Remoteregistrierungsdienst muss auf dem Server ausgeführt werden, auf dem sich die passive Datenbankkopie befindet, die Sie aktualisieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktualisieren einer Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Postfachdatenbank aus, deren passive Kopie Sie aktualisieren möchten.

3.  Klicken Sie im Detailbereich unter **Datenbankkopien** für die passive Datenbankkopie, für die das Seeding erfolgen soll, auf **Anhalten**. Geben Sie beliebige optionale Kommentare an, und klicken Sie auf **Speichern**.

4.  Klicken Sie im Detailbereich unter **Datenbankkopien** für die passive Datenbankkopie, für die das Seeding erfolgen soll, auf **Aktualisieren**.

5.  Die aktive Kopie der Datenbank dient standardmäßig als Quelldatenbank für das Seeding. Wenn Sie lieber eine passive Kopie der Datenbank für das Seeding verwenden möchten, klicken Sie auf **Durchsuchen**, um den Server auszuwählen, der die passive Kopie der Datenbank enthält, die Sie als Quelle verwenden möchten.

6.  Klicken Sie zum Aktualisieren der passiven Datenbankkopie auf **Speichern**.

## Aktualisieren einer Kopie einer Postfachdatenbank mithilfe der Shell

In diesem Beispiel wird das Seeding einer Kopie der Datenbank "DB1" auf "MBX1" veranschaulicht.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1

In diesem Beispiel wird das Seeding einer Kopie der Datenbank "DB1" auf "MBX1" veranschaulicht, wobei "MBX2" als Quellpostfachserver für den Seedingvorgang verwendet wird.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1 -SourceServer MBX2

In diesem Beispiel wird das Seeding einer Kopie der Datenbank "DB1" auf "MBX1" veranschaulicht, ohne dass ein Seeding des Inhaltsindexkatalogs erfolgt.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1 -DatabaseOnly

In diesem Beispiel wird das Seeding des Inhaltsindexkatalogs der Kopie der Datenbank "DB1" auf "MBX1" veranschaulicht, ohne dass ein Seeding der Datenbankdatei erfolgt.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1 -CatalogOnly

## Manuelles Kopieren einer Offlinedatenbank

1.  Wenn die Umlaufprotokollierung für die Datenbank aktiviert ist, muss diese deaktiviert werden, bevor Sie den Vorgang fortsetzen. Sie können die Umlaufprotokollierung für eine Postfachdatenbank mithilfe des Cmdlets [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)) deaktivieren, wie in diesem Beispiel veranschaulicht.
    
        Set-MailboxDatabase DB1 -CircularLoggingEnabled $false

2.  Heben Sie die Einbindung der Datenbank auf. Wie in diesem Beispiel gezeigt, können Sie hierzu das Cmdlet [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\)) verwenden.
    
        Dismount-Database DB1 -Confirm $false

3.  Kopieren Sie die Datenbankdateien (die Datenbankdateien sowie alle Protokolldateien) manuell an einen anderen Speicherort, z. B. auf ein externes Laufwerk oder auf eine Netzwerkfreigabe.

4.  Binden Sie die Datenbank ein. Wie in diesem Beispiel gezeigt, können Sie hierzu das Cmdlet [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\)) verwenden.
    
        Mount-Database DB1

5.  Kopieren Sie auf dem Server, der die Kopie hosten wird, die Datenbankdateien vom externen Laufwerk oder der Netzwerkfreigabe in denselben Pfad wie die aktive Datenbankkopie. Wenn beispielsweise der Pfad zur aktiven Datenbankkopie **D:\\DB1\\DB1.edb** und der Pfad zur Protokolldatei **D:\\DB1** lautet, müssen Sie die Datenbankdateien in das Verzeichnis **D:\\DB1** auf dem Server kopieren, der die Kopie hostet.

6.  Fügen Sie die Kopie der Postfachdatenbank über das Cmdlet [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) mit dem Parameter *SeedingPostponed* hinzu, wie in diesem Beispiel gezeigt.
    
        Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX3 -SeedingPostponed

7.  Wenn für die Datenbank die Umlaufprotokollierung aktiviert ist, aktivieren Sie sie mit dem Cmdlet [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)) erneut (siehe Beispiel).
    
        Set-MailboxDatabase DB1 -CircularLoggingEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um das erfolgreiche Seeding einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die Datenbank aus, für die das Seeding erfolgt ist. Im Detailbereich werden der Status der Datenbankkopie und der zugehörige Inhaltsindex angezeigt, zusammen mit der aktuellen Länge der Datenbankwarteschlange.

  - Führen Sie in der Shell den folgenden Befehl aus, um sicherzustellen, dass das Seeding der Postfachdatenbankkopie erfolgreich war und dass sie sich in einem fehlerfreien Zustand befindet.
    
        Get-MailboxDatabaseCopyStatus <DatabaseCopyName>
    
    **Status** und **Inhaltsindexzustand** sollten beide den Wert **Fehlerfrei** anzeigen.

