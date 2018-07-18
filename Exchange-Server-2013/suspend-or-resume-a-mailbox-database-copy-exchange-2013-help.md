---
title: 'Anhalten oder Fortsetzen der Kopie einer Postfachdatenbank: Exchange 2013 Help'
TOCTitle: Anhalten oder Fortsetzen der Kopie einer Postfachdatenbank
ms:assetid: 96aa1b82-3e15-4215-843e-3d583af9504b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298159(v=EXCHG.150)
ms:contentKeyID: 50476269
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anhalten oder Fortsetzen der Kopie einer Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-02_

Es gibt unterschiedliche Gründe für das Anhalten oder Fortsetzen einer Datenbankkopie, wie z. B. Wartungsarbeiten am Datenträger mit der Datenbankkopie oder das Anhalten einer einzelnen Datenbankkopie von der Aktivierung zur Notfallwiederherstellung.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Kopien von Postfachdatenbanken gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anhalten einer Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, deren Kopie Sie anhalten möchten.

3.  Klicken Sie im Detailbereich unter **Datenbankkopien** für die anzuhaltende Datenbankkopie auf **Anhalten**.

4.  Fügen Sie im Feld **Kommentare** einen Kommentar von bis zu 512 Zeichen ein, in dem Sie den Grund für das Anhalten beschreiben.

5.  Um die Datenbankkopie an der automatischen Aktivierung zu hindern, aktivieren Sie das Kontrollkästchen **Diese Kopie kann nur durch manuellen Eingriff aktiviert werden**.

6.  Klicken Sie auf **Speichern**, um die Datenbankkopie anzuhalten.

## Fortsetzen einer Postfachdatenbankkopie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, deren Kopie Sie fortsetzen möchten.

3.  Klicken Sie im Detailbereich unter **Datenbankkopien** für die fortzusetzende Datenbankkopie auf **Fortsetzen**.

4.  Klicken Sie auf **Ja**, um die Datenbankkopie fortzusetzen.

## Verwenden der Shell zum Anhalten einer Postfachdatenbankkopie

In diesem Beispiel die fortlaufende Replikation für eine Kopie der Datenbank "DB1" auf dem Server "MBX1" angehalten. Es wurde auch ein optionaler Kommentar angegeben.

    Suspend-MailboxDatabaseCopy -Identity DB1\MBX1 -SuspendComment "Maintenance on MBX1" -Confirm:$False

In diesem Beispiel wird die Aktivierung für eine Kopie der Datenbank "DB2" auf dem Server "MBX2" angehalten.

    Suspend-MailboxDatabaseCopy -Identity DB2\MBX2 -ActivationOnly -Confirm:$False

## Verwenden der Shell zum Fortsetzen einer Postfachdatenbankkopie

In diesem Beispiel wird eine Kopie der Datenbank "DB1" auf dem Server "MBX1" fortgesetzt.

    Resume-MailboxDatabaseCopy -Identity DB1\MBX1

In diesem Beispiel wird eine Kopie der Datenbank "DB2" auf dem Server "MBX2" ausschließlich zur Replikation fortgesetzt.

    Resume-MailboxDatabaseCopy -Identity DB2\MBX2 -ReplicationOnly

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um das erfolgreiche Anhalten oder Fortsetzen einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die geeignete Datenbank aus, und klicken Sie im Detailbereich auf **Details anzeigen**, um die Eigenschaften der Datenbankkopie anzuzeigen.

  - Führen Sie in der Shell den folgenden Befehl aus, um Statusinformationen zu einer Datenbankkopie anzuzeigen.
    
        Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List

