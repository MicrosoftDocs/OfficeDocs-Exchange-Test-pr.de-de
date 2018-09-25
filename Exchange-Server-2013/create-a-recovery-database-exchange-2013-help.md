---
title: 'Erstellen einer Wiederherstellungsdatenbank: Exchange 2013 Help'
TOCTitle: Erstellen einer Wiederherstellungsdatenbank
ms:assetid: 34d87491-b7b7-44a9-8d69-e1a9c1fe5852
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee332321(v=EXCHG.150)
ms:contentKeyID: 50475447
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Wiederherstellungsdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-01-21_

Sie können mithilfe der Shell eine Wiederherstellungsdatenbank erstellen, eine besondere Form von Postfachdatenbank, die im Rahmen eines Wiederherstellungsvorgangs zum Einbinden und Extrahieren von Daten aus der wiederhergestellten Datenbank verwendet wird. Nachdem Sie eine Wiederherstellungsdatenbank erstellt haben, können Sie eine wiederhergestellte Postfachdatenbank in die Wiederherstellungsdatenbank verschieben und dann das Cmdlet [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)) verwenden, um Daten aus der wiederhergestellten Datenbank zu extrahieren. Nach dem Extrahieren können die Daten in einen Ordner exportiert oder in einem vorhandenen Postfach zusammengeführt werden. Mithilfe von Wiederherstellungsdatenbanken können Sie Daten aus einer Sicherung oder Kopie der Datenbank wiederherstellen, ohne den Benutzerzugriff auf aktuelle Daten zu unterbrechen.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Wiederherstellungsdatenbanken gibt? Weitere Informationen finden Sie hier: [Wiederherstellungsdatenbanken](recovery-databases-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Erstellen einer Wiederherstellungsdatenbank

In diesem Beispiel wird die Wiederherstellungsdatenbank "RDB1" auf dem Postfachserver "MBX2" erstellt.

```powershell
New-MailboxDatabase -Recovery -Name RDB1 -Server MBX2
```

In diesem Beispiel wird die Wiederherstellungsdatenbank "RDB2" auf dem Postfachserver "MBX1" mithilfe eines benutzerdefinierten Pfads für die Datenbankdatei und den Protokollordner erstellt.

    New-MailboxDatabase -Recovery -Name RDB2 -Server MBX1 -EdbFilePath "C:\Recovery\RDB2\RDB2.EDB" -LogFolderPath "C:\Recovery\RDB2"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997976\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Wiederherstellungsdatenbank erfolgreich erstellt wurde:

  - Führen Sie in der Shell den folgenden Befehl aus, um Konfigurationsinformationen zur Wiederherstellungsdatenbank anzuzeigen:
    
    ```powershell
    Get-MailboxDatabase <RecoveryDatabaseName> | Format-List
    ```

## Weitere Aufgaben

Nachdem Sie eine Wiederherstellungsdatenbank erstellt haben, können Sie auch Daten mithilfe einer Wiederherstellungsdatenbank wiederherstellen. Weitere Informationen finden Sie unter [Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank](restore-data-using-a-recovery-database-exchange-2013-help.md).

