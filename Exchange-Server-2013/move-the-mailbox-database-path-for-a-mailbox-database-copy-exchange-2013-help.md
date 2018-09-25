---
title: 'Änd. d. Pfads d. Postfachdatenbank für Datenbankkopie: Exchange 2013-Hilfe'
TOCTitle: Ändern des Pfads der Postfachdatenbank für eine Postfachdatenbankkopie
ms:assetid: 324f255c-d95d-4a8a-a134-c8cee5c5b9cb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979782(v=EXCHG.150)
ms:contentKeyID: 50475425
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern des Pfads der Postfachdatenbank für eine Postfachdatenbankkopie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-05-07_

Nachdem eine Postfachdatenbank erstellt wurde, können Sie sie auf ein anderes Volume, in einen anderen Ordner, an einen anderen Standort oder in einen anderen Pfad verschieben, indem Sie entweder die Exchange-Verwaltungskonsole oder die Shell verwenden. Schrittanleitungen zum Verschieben eines Postfachdatenbankpfads für eine nicht replizierte Postfachdatenbank finden Sie unter [Move a mailbox database path](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

Wenn die zu verschiebende Postfachdatenbank in mindestens eine Postfachdatenbankkopie repliziert wird, müssen Sie das Verfahren in diesem Thema ausführen, um den Postfachdatenbankpfad zu verschieben. Alle Kopien einer Postfachdatenbank müssen sich auf jedem Server, der als Host für eine Kopie fungiert, im gleichen Pfad befinden. Wenn sich die Datenbank DB1 z. B. im Pfad "C:\\mountpoints\\DB1" auf Server EX1 befindet, müssen sich Kopien von DB1 auf den Servern EX2, EX3 usw. ebenfalls im Ordner "C:\\mountpoints\\DB1" befinden.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Postfachdatenbankkopien gibt? Weitere Informationen finden Sie hier: [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 Minuten, plus die Zeit, die zum Verschieben der Daten erforderlich ist. Dies ist abhängig von einer Vielzahl von Faktoren, beispielsweise von der Größe der Datenbank, der Geschwindigkeit, der verfügbaren Bandbreite, der Netzwerklatenz sowie der Speichergeschwindigkeit.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Um den Verschiebungsvorgang auszuführen, muss die Einbindung der Datenbank vorübergehend aufgehoben werden; sie steht dann für Benutzer nicht zur Verfügung. Ist die Einbindung der Datenbank aktuell aufgehoben, wird die Datenbank nach Abschluss des Befehls nicht erneut eingebunden.

  - Damit der Verschiebungsvorgang ausgeführt werden kann, muss die Replikation für die Datenbank für alle Kopien deaktiviert werden. Es ist nicht ausreichend, die Replikation anzuhalten. Sie müssen Sie mithilfe des Cmdlets [Remove-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335119\(v=exchg.150\)) deaktivieren, um die Datenbankkopien zu entfernen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Verschieben einer replizierten Postfachdatenbank in einen neuen Pfad


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Verschieben einer replizierten Postfachdatenbank in einen neuen Pfad verwendet werden.



1.  Notieren Sie sich alle Einstellungen für die Wiedergabe- oder Abschneideverzögerung für sämtliche Kopien der zu verschiebenden Postfachdatenbank. Die entsprechenden Informationen können mithilfe des Cmdlets [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)) abgerufen werden, wie in diesem Beispiel veranschaulicht.
    
        Get-MailboxDatabase DB1 | Format-List *lag*

2.  Wenn die Umlaufprotokollierung für die Datenbank aktiviert ist, muss diese deaktiviert werden, bevor Sie den Vorgang fortsetzen. Sie können die Umlaufprotokollierung für eine Postfachdatenbank mithilfe des Cmdlets [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)) deaktivieren, wie in diesem Beispiel veranschaulicht.
    
    ```powershell
    Set-MailboxDatabase DB1 -CircularLoggingEnabled $false
    ```

3.  Entfernen Sie alle Postfachdatenbankkopien für die zu verschiebende Datenbank. Weitere Informationen finden Sie unter [Entfernen einer Postfachdatenbankkopie](remove-a-mailbox-database-copy-exchange-2013-help.md). Nachdem alle Kopien entfernt wurden, sichern Sie die Datenbank- und Transaktionsprotokolldateien von den einzelnen Servern, von denen die Datenbankkopie entfernt werden soll, indem Sie sie an einen anderen Speicherort verschieben. Diese Dateien bleiben erhalten, sodass für die Datenbankkopien nach dem erneuten Hinzufügen kein Seeding erforderlich ist.

4.  Verschieben Sie den Pfad der Postfachdatenbank an den neuen Speicherort. Ausführliche Anleitungen finden Sie unter [Move a mailbox database path](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Während des Verschiebungsvorgangs muss die Einbindung der zu verschiebenden Datenbank aufgehoben werden. Bis der Verschiebungsvorgang abgeschlossen ist, führt dieser Prozess zu einer Unterbrechung des Diensts und für alle Benutzer mit Postfächern in der zu verschiebenden Datenbank zu einem Ausfall. Nachdem der Verschiebungsvorgang abgeschlossen ist, wird die Datenbank automatisch eingebunden.



5.  Erstellen Sie die erforderliche Ordnerstruktur auf den einzelnen Postfachservern, die zuvor eine passive Kopie der verschobenen Postfachdatenbank enthalten hatten. Wenn Sie z. B. die Datenbank nach "C:\\mountpoints\\DB1" verschoben haben, müssen Sie denselben Pfad auf den Postfachservern erstellen, die als Host einer Postfachdatenbankkopie fungieren werden.

6.  Nachdem Sie die Ordnerstruktur erstellt haben, verschieben Sie die passive Kopie der Postfachdatenbank und ihren Protokolldatenstrom an den neuen Speicherort. Dies sind die Dateien, die nach Schritt 3 erhalten bleiben. Wiederholen Sie diesen Prozess für jede Datenbankkopie, die in Schritt 3 entfernt wurde.

7.  Fügen Sie alle in Schritt 3 entfernten Datenbankkopien hinzu. Weitere Informationen finden Sie unter [Hinzufügen einer Kopie einer Postfachdatenbank](add-a-mailbox-database-copy-exchange-2013-help.md).

8.  Führen Sie auf jedem Server, der eine Kopie der zu entfernenden Postfachdatenbank enthält, die folgenden Befehle aus, um die Inhaltsindexdienste zu beenden und neu zu starten.
    
    ```powershell
        Net stop MSExchangeFastSearch
        Net start MSExchangeFastSearch
    ```
    
9.  Aktivieren Sie optional die Umlaufprotokollierung mithilfe des Cmdlets [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)), wie in diesem Beispiel veranschaulicht.
    
    ```powershell
    Set-MailboxDatabase DB1 -CircularLoggingEnabled $true
    ```

10. Konfigurieren Sie alle zuvor festgelegten Werte für die Wiedergabeverzögerung und die Abschneideverzögerung mithilfe des Cmdlets [Set-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298104\(v=exchg.150\)) erneut, wie in diesem Beispiel veranschaulicht.
    
    ```powershell
        Set-MailboxDatabaseCopy DB1\MBX2 -ReplayLagTime 00:15:00
    ```
    
11. Nachdem alle Kopien hinzugefügt wurden, empfehlen wir, dass Sie den Zustand und Status der Kopie überprüfen, bevor Sie die nächste Kopie hinzufügen. Sie können den Zustand und Status wie folgt überprüfen:
    
    1.  Untersuchen Sie das Ereignisprotokoll auf Fehler- oder Warnereignisse, die sich auf die Datenbank oder Datenbankkopie beziehen.
    
    2.  Verwenden Sie das Cmdlet [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\)), um den Zustand und Status der fortlaufenden Replikation für die Datenbankkopie zu überprüfen.
    
    3.  Verwenden Sie das Cmdlet [Test-ReplicationHealth](https://technet.microsoft.com/de-de/library/bb691314\(v=exchg.150\)), um den Zustand und Status der Database Availability Group (DAG) und der fortlaufenden Replikation zu überprüfen.

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\))

  - [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\))

  - [Set-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298104\(v=exchg.150\))

  - [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\))

  - [Test-ReplicationHealth](https://technet.microsoft.com/de-de/library/bb691314\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Verschiebung des Pfads für eine Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die Datenbank aus, die kopiert wurde. Im Detailbereich werden der Status der Datenbankkopie und der zugehörige Inhaltsindex angezeigt, zusammen mit der aktuellen Länge der Datenbankwarteschlange. Überprüfen Sie, ob als Status der Wert Fehlerfrei angezeigt wird.

  - Führen Sie in der Shell den folgenden Befehl aus, um sicherzustellen, dass die Postfachdatenbankkopie erstellt wurde und sich in einem fehlerfreien Zustand befindet.
    
    ```powershell
    Get-MailboxDatabaseCopyStatus <DatabaseCopyName>
    ```
    
    Status und Inhaltsindexzustand sollten beide den Wert Fehlerfrei anzeigen.

