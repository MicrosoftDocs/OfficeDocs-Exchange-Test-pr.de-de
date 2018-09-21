---
title: 'Bereinigen des Ordners "Wiederherstellbare Elemente": Exchange 2013 Help'
TOCTitle: Bereinigen des Ordners "Wiederherstellbare Elemente"
ms:assetid: 82c310f8-de2f-46f2-8e1a-edb6055d6e69
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff678798(v=EXCHG.150)
ms:contentKeyID: 50554863
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- klassifizierter Nachrichtenüberlauf
- klassifizierter Nachrichtenüberlauf, Bereinigung
- klassifizierter Überlauf
- klassifizierter Überlauf, Bereinigung
- Nachrichtenüberlauf
- Nachrichtenüberlauf, Bereinigung
- Suchen und löschen
ms.translationtype: HT
---

# Bereinigen des Ordners \"Wiederherstellbare Elemente\"

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-09-30_

Der Ordner "Wiederherstellbare Elemente" (in früheren Versionen von Exchange als *Dumpster* bezeichnet) dient zum Schutz vor versehentlichen oder böswilligen Löschungen und zum Erleichtern der Suche nach Daten zur Vorbereitung auf Rechtsstreitigkeiten oder Untersuchungen. Weitere Informationen zum Ordner "Wiederherstellbare Elemente" finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

Das Bereinigungsverfahren für den Ordner "Wiederherstellbare Elemente" eines Postfachs hängt davon ab, ob das Postfach der Aufbewahrung im Compliance-Archiv oder für ein Beweissicherungsverfahren unterliegt oder ob die Wiederherstellung einzelner Elemente aktiviert ist:

  - Wenn ein Postfach nicht der Aufbewahrung im Compliance-Archiv oder für ein Beweissicherungsverfahren unterliegt und die Wiederherstellung einzelner Elemente nicht aktiviert ist, können Sie Elemente aus dem Ordner "Wiederherstellbare Elemente" einfach löschen. Nach dem Löschen können Sie die Elemente nicht mit der Wiederherstellung einzelner Elemente wiederherstellen.

  - Wenn das Postfach der Aufbewahrung im Compliance-Archiv oder für ein Beweissicherungsverfahren unterliegt oder die Wiederherstellung einzelner Elemente aktiviert ist, ist es wichtig, die Postfachdaten bis zur Aufhebung des Beweissicherungsverfahrens aufzubewahren. Daher müssen Sie detailliertere Schritte ausführen, um den Ordner "Wiederherstellbare Elemente" zu bereinigen.

Weitere Informationen zu Compliance-Archiv und Beweissicherungsverfahren finden Sie unter [In-Place Hold and Litigation Hold](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-and-litigation-holds). Weitere Informationen zum Wiederherstellen einzelner Elemente finden Sie unter "Wiederherstellung einzelner Elemente" in [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

Weitere Informationen zum Ordner **Wiederherstellbare Elemente** finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 30 Minuten. Dies kann abhängig von der Größe des Ordners "Wiederherstellbare Elemente" variieren

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Löschen von Postfachinhalten" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Da eine fehlerhafte Bereinigung des Ordners "Wiederherstellbare Elemente" zu Datenverlusten führen kann, ist es wichtig, dass Sie über den Ordner "Wiederherstellbare Elemente" und darüber, welche Auswirkungen das Entfernen seiner Inhalte haben kann, informiert sind. Vor der Durchführung dieses Verfahrens wird empfohlen, die Informationen unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md) zu lesen.

  - Diese Verfahren können nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Verwenden der Shell zum Löschen von Elementen aus dem Ordner "Wiederherstellbare Elemente" für Postfächer, die nicht der Aufbewahrung im Compliance-Archiv oder einem Beweissicherungsverfahren unterliegen und für die die Wiederherstellung einzelner Elemente nicht aktiviert ist

In diesem Beispiel werden Elemente dauerhaft aus dem Ordner "Wiederherstellbare Elemente" von Gurinder Singh gelöscht, und die Elemente werden in den Ordner "GurinderSingh-RecoverableItems" im Discoverysuchpostfach (einem vom Exchange-Setup erstellten Discoverypostfach) kopiert.

    Search-Mailbox -Identity "Gurinder Singh" -SearchDumpsterOnly -TargetMailbox "Discovery Search Mailbox" -TargetFolder "GurinderSingh-RecoverableItems" -DeleteContent


> [!NOTE]
> Um Elemente aus dem Postfach zu löschen, ohne sie in ein anderes Postfach zu kopieren, verwenden Sie den vorstehenden Befehl ohne die Parameter <EM>TargetMailbox</EM> und <EM>TargetFolder</EM>.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)).

## Verwenden der Shell zum Bereingen des Ordners "Wiederherstellbare Elemente" für Postfächer, die der Aufbewahrung im Compliance-Archiv oder einem Beweissicherungsverfahren unterliegen und für die die Wiederherstellung einzelner Elemente aktiviert ist

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Löschen von Postfachinhalten" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

Wenn für ein Postfach das Kontingent für wiederherstellbare Elemente erreicht wird, sollten Sie das Kontingent erhöhen, statt Elemente aus dem Ordner zu löschen. Sie können auch Ereignisse im Anwendungsprotokoll überwachen, die mit dem Warnungskontingent für wiederherstellbare Elemente in Zusammenhang stehen, und notwendige Aktionen durchführen (z. B. das Erhöhen des Kontingents oder das Untersuchen des Wachstums des Ordners "Wiederherstellbare Elemente" für Postfächer, die das Warnungskontingent erreicht haben).

Wenn Speicherbeschränkungen oder ähnliche Probleme dazu führen, dass Sie das Kontingent für wiederherstellbare Elemente nicht erhöhen können, und Sie Nachrichten aus dem Ordner "Wiederherstellbare Elemente" eines Postfachs löschen müssen, das der Aufbewahrung im Compliance-Archiv oder einem Beweissicherungsverfahren unterliegt oder für das die Wiederherstellung einzelner Elemente aktiviert ist, sollten Sie zuerst Daten aus dem Ordner "Wiederherstellbare Elemente" des Benutzers in ein anderes Postfach kopieren. Wenn Sie Elemente löschen, weil für ein Volume Speicherbeschränkungen bestehen, können Sie Elemente in ein Postfach auf einem Volume mit ausreichendem Speicher kopieren.

Bei diesem Vorgang werden Elemente aus dem Ordner "Wiederherstellbare Elemente" von Gurinder Singh in den Ordner "GurinderSingh-RecoverableItems" im Discoverysuchpostfach kopiert. Bevor Sie Elemente aus dem Ordner "Wiederherstellbare Elemente" kopieren und löschen, müssen Sie mehrere Schritte durchführen, um sicherzustellen, dass die Elemente nicht aus dem Ordner "Wiederherstellbare Elemente" gelöscht werden. Nachdem Sie die Elemente in ein Discovery- oder Sicherungspostfach kopiert und den Ordner bereinigt haben, können Sie zu den früheren Einstellungen des Postfachs zurückkehren.

1.  Rufen Sie die folgenden Kontingenteinstellungen ab. Notieren Sie sich die Werte unbedingt, damit Sie nach der Bereinigung des Ordners "Wiederherstellbare Elemente" zu diesen Einstellungen zurückkehren können:
    
      - *RecoverableItemsQuota*
    
      - *RecoverableItemsWarningQuota*
    
      - *ProhibitSendQuota*
    
      - *ProhibitSendReceiveQuota*
    
      - *UseDatabaseQuotaDefaults*
    
      - *RetainDeletedItemsFor*
    
      - *UseDatabaseRetentionDefaults*
    

    > [!NOTE]
    > Wenn der Parameter <EM>UseDatabaseQuotaDefaults</EM> auf <CODE>$true</CODE> festgelegt ist, werden die vorigen Kontingenteinstellungen nicht angewendet. Die entsprechenden für die Mailboxdatenbank konfigurierten Kontingenteinstellungen werden angewendet, auch wenn einzelne Postfacheinstellungen Werte enthalten.

    
        Get-Mailbox "Gurinder Singh" | Format-List RecoverableItemsQuota, RecoverableItemsWarningQuota, ProhibitSendQuota, ProhibitSendReceiveQuota, UseDatabaseQuotaDefaults, RetainDeletedItemsFor, UseDatabaseRetentionDefaults

2.  Rufen Sie die Zugriffseinstellungen für das Postfach ab. Notieren Sie sich diese Einstellungen zur späteren Verwendung.
    
        Get-CASMailbox "Gurinder Singh" | Format-List EwsEnabled, ActiveSyncEnabled, MAPIEnabled, OWAEnabled, ImapEnabled, PopEnabled

3.  Rufen Sie die aktuelle Größe des Ordners "Wiederherstellbare Elemente" ab. Notieren Sie sich die Größe, damit Sie in Schritt 6 die Kontingente erhöhen können.
    
        Get-MailboxFolderStatistics "Gurinder Singh" -FolderScope RecoverableItems | Format-List Name,FolderAndSubfolderSize

4.  Rufen Sie die aktuelle Arbeitszykluskonfiguration für den Assistenten für verwaltete Ordner ab. Notieren Sie sich die Einstellung zur späteren Verwendung.
    
    ```powershell
Get-MailboxServer "My Mailbox Server" | Format-List Name,ManagedFolderWorkCycle
```

5.  Deaktivieren Sie den Clientzugriff auf das Postfach, um sicherzustellen, dass während dieses Verfahrens keine Änderungen an Postfachdaten vorgenommen werden können.
    
        Set-CASMailbox "Gurinder Singh" -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false

6.  Um sicherzustellen, dass keine Elemente aus dem Ordner "Wiederherstellbare Elemente" gelöscht werden, erhöhen Sie das Kontingent für wiederherstellbare Elemente, erhöhen Sie das Warnungskontingent für wiederherstellbare Elemente, und legen Sie den Aufbewahrungszeitraum für gelöschte Elemente auf einen Wert fest, der größer ist als die aktuelle Größe des Ordners "Wiederherstellbare Elemente" des Benutzers. Dies ist besonders wichtig, um Nachrichten für Postfächer aufzubewahren, die der Aufbewahrung im Compliance-Archiv oder für ein Beweissicherungsverfahren unterliegen. Sie sollten den Wert dieser Einstellungen verdoppeln.
    
        Set-Mailbox "Gurinder Singh" -RecoverableItemsQuota 50Gb -RecoverableItemsWarningQuota 50Gb -RetainDeletedItemsFor 3650 -ProhibitSendQuota 50Gb -ProhibitSendRecieveQuota 50Gb -UseDatabaseQuotaDefaults $false -UseDatabaseRetentionDefaults $false

7.  Deaktivieren Sie den Assistenten für verwaltete Ordner auf dem Postfachserver.
    
    ```powershell
Set-MailboxServer MyMailboxServer -ManagedFolderWorkCycle $null
```
    

    > [!IMPORTANT]
    > Wenn sich das Postfach in einer Postfachdatenbank in einer Database Availability Group (DAG) befindet, müssen Sie den Assistenten für verwaltete Ordner auf jedem Mitglied der DAG deaktivieren, das eine Kopie der Datenbank hostet. Wenn für die Datenbank ein Failover zu einem anderen Server durchgeführt wird, kann der Assistent für verwaltete Ordner auf diesem Server keine Postfachdaten löschen.



8.  Deaktivieren Sie die Wiederherstellung einzelner Elemente, und heben Sie für das Postfach die Aufbewahrung für das Beweissicherungsverfahren auf.
    
    ```powershell
Set-Mailbox "Gurinder Singh" -SingleItemRecoveryEnabled $false -LitigationHoldEnabled $false
```
    

    > [!IMPORTANT]
    > Nach dem Ausführen dieses Befehls kann es bis zu einer Stunde dauern, bis die Wiederherstellung einzelner Elemente oder die Aufbewahrung für das Beweissicherungsverfahren deaktiviert ist. Sie sollten den nächsten Schritt erst nach Ablauf dieses Zeitraums durchführen.



9.  Kopieren Sie Elemente aus dem Ordner "Wiederherstellbare Elemente" in einen Ordner im Discoverysuchpostfach, und löschen Sie die Inhalte aus dem Quellpostfach.
    
        Search-Mailbox -Identity "Gurinder Singh" -SearchDumpsterOnly -TargetMailbox "Discovery Search Mailbox" -TargetFolder "GurinderSingh-RecoverableItems" -DeleteContent
    
    Wenn Sie nur Nachrichten löschen möchten, die bestimmte Bedingungen erfüllen, geben Sie die Bedingungen mit dem Parameter *SearchQuery* an. In diesem Beispiel werden Nachrichten gelöscht, in deren Feld **Subject** die Zeichenfolge "Your bank statement" enthalten ist.
    
        Search-Mailbox -Identity "Gurinder Singh" -SearchQuery "Subject:'Your bank statement'" -SearchDumpsterOnly -TargetMailbox "Discovery Search Mailbox" -TargetFolder "GurinderSingh-RecoverableItems" -DeleteContent
    

    > [!NOTE]
    > Sie müssen Elemente nicht in das Discoverysuchpostfach kopieren. Sie können Nachrichten in ein beliebiges Postfach kopieren. Um jedoch den Zugriff auf potenziell vertrauliche Postfachdaten zu verhindern, sollten Sie die Nachrichten in ein Postfach kopieren, auf das ausschließlich autorisierte Datensatzmanager zugreifen können. Standardmäßig können auf das Discoverysuchpostfach ausschließlich Mitglieder der Rollengruppe "Discoveryverwaltung" zugreifen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery">Compliance-eDiscovery</A>.



10. Wenn für das Postfach zuvor die Aufbewahrung für das Beweissicherungsverfahren festgelegt oder die Wiederherstellung einzelner Elemente aktiviert wurde, aktivieren Sie diese Funktionen erneut.
    
    ```powershell
Set-Mailbox "Gurinder Singh" -SingleItemRecoveryEnabled $true -LitigationHoldEnabled $true
```
    

    > [!IMPORTANT]
    > Nach dem Ausführen dieses Befehls kann es bis zu einer Stunde dauern, bis die Wiederherstellung einzelner Elemente oder die Aufbewahrung für das Beweissicherungsverfahren aktiviert ist. Sie sollten erst nach Ablauf dieses Zeitraums den Assistenten für verwaltete Ordner aktivieren und den Clientzugriff zulassen (Schritte 11 und 12).



11. Setzen Sie die folgenden Kontingente auf die in Schritt 1 notierten Werte zurück:
    
      - *RecoverableItemsQuota*
    
      - *RecoverableItemsWarningQuota*
    
      - *ProhibitSendQuota*
    
      - *ProhibitSendReceiveQuota*
    
      - *UseDatabaseQuotaDefaults*
    
      - *RetainDeletedItemsFor*
    
      - *UseDatabaseRetentionDefaults*
    
    In diesem Beispiel wird für das Postfach das Anhalten der Aufbewahrungszeit deaktiviert, die Aufbewahrungszeit für gelöschte Elemente wird auf den Standardwert von 14 Tagen zurückgesetzt, und für das Kontingent für wiederherstellbare Elemente wird die Verwendung desselben Werts konfiguriert wie für die Postfachdatenbank. Wenn die in Schritt 1 notierten Werte davon abweichen, müssen Sie die einzelnen Werte mithilfe der vorstehenden Parameter angeben und den Parameter *UseDatabaseQuotaDefaults* auf `$false` festlegen. Wenn die Parameter *RetainDeletedItemsFor* und *and UseDatabaseRetentionDefaults* zuvor auf einen anderen Wert festgelegt waren, müssen Sie sie auch auf die in Schritt 1 angegebenen Werte zurücksetzen.
    
        Set-Mailbox "Gurinder Singh" -RetentionHoldEnabled $false -RetainDeletedItemsFor 14 -RecoverableItemsQuota unlimited -UseDatabaseQuotaDefaults $true

12. Aktivieren Sie den Assistenten für verwaltete Ordner, indem Sie den Arbeitszyklus auf den in Schritt 4 notierten Wert zurücksetzen. In diesem Beispiel wird der Arbeitszyklus auf einen Tag festgelegt.
    
    ```powershell
Set-MailboxServer MyMailboxServer -ManagedFolderWorkCycle 1
```

13. Aktivieren Sie den Clientzugriff.
    
        Set-CASMailbox -ActiveSyncEnabled $true -EwsEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Get-CASMailbox](https://technet.microsoft.com/de-de/library/bb124754\(v=exchg.150\))

  - [Get-MailboxFolderStatistics](https://technet.microsoft.com/de-de/library/aa996762\(v=exchg.150\))

  - [Get-MailboxServer](https://technet.microsoft.com/de-de/library/bb123539\(v=exchg.150\))

  - [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\))

  - [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie zum Bestätigen, dass Sie den Ordner "Wiederherstellbare Elemente" eines Postfachs erfolgreich bereinigt haben, das Cmdlet [Get-MailboxFolderStatistics](https://technet.microsoft.com/de-de/library/aa996762\(v=exchg.150\)) aus, um die Größe des Ordners "Wiederherstellbare Elemente" zu überprüfen.

Bei diesem Beispiel wird die Größe des Ordners "Wiederherstellbare Elemente" und seiner Unterordner sowie die Anzahl der Elemente im Ordner und den einzelnen Unterordnern abgerufen.

    Get-MailboxFolderStatistics -Identity "Gurinder Singh" -FolderScope RecoverableItems | Format-Table Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders -Auto

