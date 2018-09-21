---
title: 'Aktivieren einer verzögerten Kopie einer Postfachdatenbank: Exchange 2013 Help'
TOCTitle: Aktivieren einer verzögerten Kopie einer Postfachdatenbank
ms:assetid: 493d9c40-644d-49d6-9291-949acbcfdcb6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979786(v=EXCHG.150)
ms:contentKeyID: 50475606
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren einer verzögerten Kopie einer Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-01-28_

Eine verzögerte Postfachdatenbankkopie ist eine Postfachdatenbankkopie, für die ein Wiedergabeverzögerungswert von mehr als 0 konfiguriert wurde. Die Aktivierung und Wiederherstellung einer verzögerten Postfachdatenbankkopie ist ein einfacher Vorgang, wenn Sie möchten, dass alle Protokolldateien für die Datenbank wiedergegeben werden sollen und die Datenbankkopie auf den neuesten Stand gebracht werden soll. Wenn Sie die Protokolldateien nur bis zu einem bestimmten Zeitpunkt wiedergeben möchten, ist der Vorgang komplizierter, da Sie die Protokolldateien manuell bearbeiten und "Eseutil" ausführen müssen.

Benötigen Sie weitere Informationen zu verzögerten Postfachdatenbankkopien? Weitere Informationen finden Sie unter [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).


> [!NOTE]
> Wie lange es dauert, um eine verzögerte Postfachdatenbankkopie zu aktivieren, hängt unmittelbar davon ab, wie viele Protokolldateien wiedergegeben werden müssen und wie schnell die Wiedergabe durch die Hardware möglich ist. Es sollte mindestens eine Protokollwiedergaberate von zwei Protokollen pro Sekunde und Datenbank angezeigt werden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute zuzüglich der Zeit, die zum Duplizieren der verzögerten Kopie, zur Wiedergabe der erforderlichen Protokolldateien und zum Extrahieren der Daten oder zum Einbinden der Datenbank für die Clientaktivität benötigt wird.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Für die zu aktivierende Postfachdatenbankkopie muss ein Wiedergabeverzögerungszeitraum größer 0 konfiguriert sein.

  - Für die zu aktivierende Postfachdatenbankkopie müssen alle Protokolldateien bis zu dem Zeitpunkt verfügbar sein, bis zu dem die Datenbank wiederhergestellt werden soll. Bedenken Sie beim Festlegen des Zeitpunkts, bis zu dem die Wiederherstellung erfolgen soll, dass sich Datenbanktransaktionen über mehrere Protokolldateien erstrecken können.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Shell, um eine verzögerte Postfachdatenbankkopie bis zu einem bestimmten Zeitpunkt zu aktivieren


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht verwendet werden, um eine verzögerte Postfachdatenbankkopie bis zu einem bestimmten Zeitpunkt zu aktivieren. Stattdessen verwenden Sie die Shell und die Befehlszeile, um eine Reihe von Schritten auszuführen.



1.  In diesem Beispiel wird die Replikation für die verzögerte Kopie durch Verwendung des Cmdlets [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) aktiviert.
    
        Suspend-MailboxDatabaseCopy DB1\EX3 -SuspendComment "Activate lagged copy of DB1 on Server EX3" -Confirm:$false

2.  Erstellen Sie optional (zur Beibehaltung einer verzögerten Kopie) eine Kopie der Datenbankkopie und ihrer Protokolldateien.
    

    > [!NOTE]
    > Wenn Sie nun mit diesem Verfahren für das vorhandene Volume fortfahren, würde dies eine Beeinträchtigung der Copy-on-Write-Leistung (Kopie bei Schreibvorgang) nach sich ziehen. Falls dies nicht gewünscht ist, können Sie die Datenbank und die Protokolldateien auf ein anderes Volume kopieren, um die Wiederherstellung vorzunehmen.



3.  Ermitteln Sie, welche Protokolldateien für eine Wiedergabe in der Datenbank erforderlich sind, um Ihre Anforderungen im Hinblick auf den Zeitpunkt für diese Wiederherstellung zu erfüllen (Orientieren Sie sich hierbei an den in Windows-Explorer angezeigten Informationen zu Datum und Uhrzeit der Protokolldateien). Alle Protokolle, die nach diesem Zeitpunkt erstellt wurden, sollten so lange in ein anderes Verzeichnis verschoben werden, bis der Vorgang abgeschlossen ist und die Protokolle nicht mehr benötigt werden.

4.  Löschen Sie die Prüfpunktdatei (CHK) für die Datenbank.

5.  In diesem Beispiel wird "Eseutil" zum Ausführen des Wiederherstellungsvorgangs verwendet.
    
    ```powershell
Eseutil.exe /r eXX /a
```
    

    > [!NOTE]
    > Im vorherigen Beispiel stellt <EM>eXX</EM> das Protokollgenerierungspräfix für die Datenbank dar (z. B. "E00", "E01" und "E02").

    

    > [!IMPORTANT]
    > Wie viel Zeit dieser Schritt in Anspruch nimmt, hängt von verschiedenen Faktoren ab. Hierzu zählen die Länge des Wiedergabeverzögerungszeitraums, die Anzahl der in diesem Zeitraum generierten Protokolldateien und die Geschwindigkeit, mit der diese Protokolle von der vorhandenen Hardware in der wiederherzustellenden Datenbank wiedergegeben werden können.



6.  Wenn die Protokollwiedergabe beendet ist, befindet sich die Datenbank im Zustand "Clean Shutdown" und kann kopiert und zu Wiederherstellungszwecken verwendet werden.

7.  In diesem Beispiel wird nach Abschluss der Wiederherstellung die Replikation für die Datenbank fortgesetzt, die im Rahmen der Wiederherstellung verwendet wurde.
    
        Resume-MailboxDatabaseCopy DB1\EX3

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) oder [Resume-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335220\(v=exchg.150\)).

## Aktivieren einer verzögerten Postfachdatenbankkopie durch Wiedergabe aller Protokolldateien ohne Commit mithilfe der Shell

1.  Erstellen Sie optional (zur Beibehaltung einer verzögerten Kopie) eine Kopie der Datenbankkopie und ihrer Protokolldateien.
    
    1.  In diesem Beispiel wird die Replikation für die verzögerte Kopie durch Verwendung des Cmdlets [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) aktiviert.
        
            Suspend-MailboxDatabaseCopy DB1\EX3 -SuspendComment "Activate lagged copy of DB1 on Server EX3" -Confirm:$false
    
    2.  Erstellen Sie optional (zur Beibehaltung einer verzögerten Kopie) eine Kopie der Datenbankkopie und ihrer Protokolldateien.
        

        > [!NOTE]
        > Wenn Sie nun mit diesem Verfahren für das vorhandene Volume fortfahren, würde dies eine Beeinträchtigung der Copy-on-Write-Leistung (Kopie bei Schreibvorgang) nach sich ziehen. Falls dies nicht gewünscht ist, können Sie die Datenbank und die Protokolldateien auf ein anderes Volume kopieren, um die Wiederherstellung vorzunehmen.



2.  In diesem Beispiel wird die verzögerte Postfachdatenbankkopie mithilfe des Cmdlets [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)) mit dem Parameter *SkipLagChecks* aktiviert.
    
    ```powershell
Move-ActiveMailboxDatabase DB1 -ActivateOnServer EX3 -SkipLagChecks
```

## Aktivieren der verzögerten Postfachdatenbankkopie mithilfe der SafetyNet-Wiederherstellung und der Shell

1.  Erstellen Sie (zur Beibehaltung einer verzögerten Kopie) wahlweise eine dateisystembasierte (nicht Exchange-bezogene) VSS-Momentaufnahme (Volume Shadow Copy Service, Volumeschattenkopie-Dienst) der Volumes, auf denen sich die Datenbankkopie und die zugehörigen Protokolldateien befinden.
    
    1.  In diesem Beispiel wird die Replikation für die verzögerte Kopie durch Verwendung des Cmdlets [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) aktiviert.
        
            Suspend-MailboxDatabaseCopy DB1\EX3 -SuspendComment "Activate lagged copy of DB1 on Server EX3" -Confirm:$false
    
    2.  Erstellen Sie optional (zur Beibehaltung einer verzögerten Kopie) eine Kopie der Datenbankkopie und ihrer Protokolldateien.
        

        > [!NOTE]
        > Wenn Sie nun mit diesem Verfahren für das vorhandene Volume fortfahren, würde dies eine Beeinträchtigung der Copy-on-Write-Leistung (Kopie bei Schreibvorgang) nach sich ziehen. Falls dies nicht gewünscht ist, können Sie die Datenbank und die Protokolldateien auf ein anderes Volume kopieren, um die Wiederherstellung vorzunehmen.



2.  Ermitteln Sie die erforderlichen Protokolle für die verzögerte Datenbankkopie, indem Sie nach dem Wert "Log Required:" in der ESEUTIL-Datenbankkopfzeilenausgabe suchen.
    
    ```powershell
Eseutil /mh <DBPath> | findstr /c:"Log Required"
```
    
    Notieren Sie die Hexadezimalzahlen in Klammern. Der erste Wert ist die erforderliche niedrigste Generation (als LowGeneration bezeichnet) und der zweite Wert ist die erforderliche höchste Generation (als HighGeneration bezeichnet). Verschieben Sie alle Protokollgenerationsdateien, die über eine Generationssequenz größer als HighGeneration verfügen, an einen anderen Speicherort, damit sie nicht erneut in die Datenbank wiedergegeben werden.

3.  Löschen Sie auf dem Server, auf dem die aktive Kopie der Datenbank gehostet ist, entweder die Protokolldateien für die verzögerte Kopie, die aus der aktiven Kopie aktiviert wird, oder halten Sie den Microsoft Exchange-Replikationsdienst an.

4.  Führen Sie ein Datenbankswitchover durch, und aktivieren Sie die verzögerte Kopie. In diesem Beispiel wird die Datenbank mithilfe des Cmdlets [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)) mit verschiedenen Parametern aktiviert.
    
        Move-ActiveMailboxDatabase DB1 -ActivateOnServer EX3 -MountDialOverride BestEffort -SkipActiveCopyChecks -SkipClientExperienceChecks -SkipHealthChecks -SkipLagChecks

5.  An dieser Stelle wird die Datenbank automatisch eingebunden und die erneute Zustellung fehlender Nachrichten von SafetyNet angefordert.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Aktivierung einer verzögerten Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die geeignete Datenbank aus, und klicken Sie im Detailbereich auf **Details anzeigen**, um die Eigenschaften der Datenbankkopie anzuzeigen.

  - Führen Sie in der Shell den folgenden Befehl aus, um Statusinformationen zu einer Datenbankkopie anzuzeigen.
    
    ```powershell
Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List
```

