---
title: 'Wiederherst. v. Daten mit Wiederherstellungsdatenbank: Exchange 2013-Hilfe'
TOCTitle: Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank
ms:assetid: d64c18e7-16af-4bd8-a5c5-01206984d4d1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee332351(v=EXCHG.150)
ms:contentKeyID: 50476814
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-10-01_

Eine Wiederherstellungsdatenbank ist eine spezielle Art von Postfachdatenbank, mit der Sie eine wiederhergestellte Postfachdatenbank einbinden und im Rahmen einer Wiederherstellung Daten daraus extrahieren können. Mithilfe von Wiederherstellungsdatenbanken können Sie Daten aus einer Sicherung oder Kopie der Datenbank wiederherstellen, ohne den Benutzerzugriff auf aktuelle Daten zu unterbrechen.

Nachdem Sie eine Wiederherstellungsdatenbank erstellt haben, können Sie mithilfe einer Sicherungsanwendung oder durch Kopieren einer Datenbank und deren Protokolldateien in die Ordnerstruktur der Wiederherstellungsdatenbank eine Postfachdatenbank in der Wiederherstellungsdatenbank wiederherstellen. Anschließend können Sie das Cmdlet [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)) verwenden, um Daten aus der wiederhergestellten Datenbank zu extrahieren. Nach dem Extrahieren können die Daten in einen Ordner exportiert oder in einem vorhandenen Postfach zusammengeführt werden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Wiederherstellungsdatenbanken finden Sie unter [Wiederherstellungsdatenbanken](recovery-databases-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute, plus die Zeit, die für das Versetzen der Datenbank in den Status "Clean Shutdown" und das Extrahieren der Daten erforderlich ist.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Mit einigen Sicherungsanwendungen können Exchange-Daten direkt in einer Wiederherstellungsdatenbank wiederhergestellt werden. Mit der Windows Server-Sicherung können nur Sicherungen auf Dateiebene in einer Wiederherstellungsdatenbank wiederhergestellt werden. Die Wiederherstellung von Sicherungen auf Anwendungsebene in einer Wiederherstellungsdatenbank ist damit nicht möglich.

  - Die Datenbank- und Protokolldateien mit den wiederhergestellten Daten müssen in der Ordnerstruktur der Wiederherstellungsdatenbank wiederhergestellt oder dorthin kopiert werden.

  - Die Datenbank muss den Status Clean Shutdown aufweisen. Da eine Wiederherstellungsdatenbank einen alternativen Wiederherstellungsort für alle Datenbanken darstellt, weisen alle wiederhergestellten Datenbanken den Status Dirty Shutdown auf. Sie müssen **Eseutil /R** verwenden, um wiederhergestellte Datenbanken in den Status "Clean Shutdown" zu versetzen.

## Wiederherstellen von Daten unter Verwendung einer Wiederherstellungsdatenbank mithilfe der Shell

1.  Kopieren Sie eine wiederhergestellte Datenbank und deren Protokolldateien an den Speicherort, den Sie für Ihre Wiederherstellungsdatenbank verwenden werden, bzw. stellen Sie eine Datenbank und deren Protokolldateien dort wieder her.

2.  Verwenden Sie Eseutil, um diese Datenbank in den Status "Clean Shutdown" zu versetzen. Im folgenden Beispiel stellt EXX das Protokollgenerierungspräfix für die Datenbank dar (z. B. E00, E01, E02 usw.).
    
        Eseutil /R EXX /l <RDBLogFilePath> /d <RDBEdbFolder>
    
    Das folgende Beispiel verwendet das Protokollgenerierungspräfix E01 und den Wiederherstellungsdatenbank- und Protokolldateipfad "E:\\Databases\\RDB1:
    
        Eseutil /R E01 /l E:\Databases\RDB1 /d E:\Databases\RDB1

3.  Erstellen einer Wiederherstellungsdatenbank Geben Sie der Wiederherstellungsdatenbank einen eindeutigen Namen. Verwenden Sie aber den Namen und Pfad der Datenbankdatei für den Parameter "EdbFilePath" und den Speicherort der wiederhergestellten Protokolldateien für den Parameter "LogFolderPath".
    
        New-MailboxDatabase -Recovery -Name <RDBName> -Server <ServerName> -EdbFilePath <RDBPathandFileName> -LogFolderPath <LogFilePath>
    
    Im folgenden Beispiel wird die Erstellung einer Wiederherstellungsdatenbank illustriert, die zur Wiederherstellung von "DB1.edb" und deren Protokolldateien verwendet wird, die unter "E:\\Databases\\RDB1" gespeichert sind.
    
        New-MailboxDatabase -Recovery -Name <RDBName> -Server <ServerName> -EdbFilePath "E:\Databases\RDB1\DB1.EDB" -LogFolderPath "E:\Databases\RDB1"

4.  Starten Sie den Microsoft Exchange-Informationsspeicherdienst neu:
    
        Restart-Service MSExchangeIS

5.  Binden Sie die Wiederherstellungsdatenbank ein:
    
        Mount-database <RDBName>

6.  Stellen Sie sicher, dass die eingebundene Datenbank das/die Postfach/Postfächer enthält, das/die Sie wiederherstellen möchten:
    
        Get-MailboxStatistics -Database <RDBName> | ft -auto

7.  Verwenden Sie das Cmdlet "New-MailboxRestoreRequest", um ein Postfach oder Elemente aus der Wiederherstellungsdatenbank in einem Produktionspostfach wiederherzustellen.
    
    Im folgenden Beispiel wird das Quellpostfach mit MailboxGUID "1d20855f-fd54-4681-98e6-e249f7326ddd" in der Postfachdatenbank "DB1" im Zielpostfach mit dem Alias "Morris" wiederhergestellt.
    
        New-MailboxRestoreRequest -SourceDatabase DB1 -SourceStoreMailbox 1d20855f-fd54-4681-98e6-e249f7326ddd -TargetMailbox Morris
    
    Im folgenden Beispiel wird der Inhalt des Quellpostfachs wiederhergestellt, das in der Postfachdatenbank "DB1" für das Archivpostfach von "Morris@contoso.com" den Anzeigenamen "Morris Cornejo" aufweist.
    
        New-MaiboxRestoreRequest -SourceDatabase DB1 -SourceStoreMailbox "Morris Cornejo" -TargetMailbox Morris@contoso.com -TargetIsArchive

8.  Prüfen Sie mit [Get-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829907\(v=exchg.150\)) regelmäßig den Status der Postfachwiederherstellungsanforderung.
    
    Sobald die Wiederherstellung den Status "Abgeschlossen" aufweist, entfernen Sie die Wiederherstellungsanforderung mit [Remove-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829910\(v=exchg.150\)). Beispiel:
    
        Get-MailboxRestoreRequest -Status Completed | Remove-MailboxRestoreRequest

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sich zu vergewissern, dass die Postfachdaten erfolgreich wiederhergestellt wurden, öffnen Sie das Zielpostfach mit Outlook oder Outlook Web App, und überprüfen Sie, ob die wiederhergestellten Daten vorhanden sind.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


