---
title: 'Abrufen von Statistiken zum Ordner "Wiederherstellbare Elemente": Exchange 2013 Help'
TOCTitle: Abrufen von Statistiken zum Ordner "Wiederherstellbare Elemente"
ms:assetid: dee77958-ee87-4908-85e4-ad053bacd8b0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff714343(v=EXCHG.150)
ms:contentKeyID: 52062913
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Abrufen von Statistiken zum Ordner \"Wiederherstellbare Elemente\"

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-22_

Der Ordner **Wiederherstellbare Elemente** enthält von Microsoft Outlook- und Microsoft OfficeOutlook Web App-Benutzern oder vom Postfach-Assistenten gelöschte Elemente. Die Zeitdauer, während der gelöschte Elemente in diesem Ordner beibehalten werden, basiert auf den Einstellungen für die Aufbewahrungszeit gelöschter Elemente, die für die Postfachdatenbank oder das Postfach konfiguriert sind. Für Postfachdatenbanken ist standardmäßig eine Aufbewahrungszeit für gelöschte Elemente von 14 Tagen konfiguriert. Für die Anzeige einer Warnung zum Kontingent für wiederherstellbare Elemente und für das Kontingent für wiederherstellbare Elemente sind 20 GB bzw. 30 GB festgelegt. Wenn für das Postfach jedoch ein Compliance-Archiv oder Beweissicherungsverfahren aktiv ist, können im Ordner Wiederherstellbare Elemente für eine längere Zeitdauer als die angegebene Aufbewahrungszeit gelöschte Elemente gespeichert werden. Zudem können unterschiedliche Versionen geänderter Postfachelemente verwaltet werden.

Wenn die Größe des Ordners **Wiederherstellbare Elemente** den für die Anzeige einer Warnung zum Kontingent für wiederherstellbare Elemente festgelegten Wert erreicht, wird im Anwendungsereignisprotokoll ein Warnereignis protokolliert. Wenn das Postfach keinem Beweissicherungsverfahren unterliegt, werden die Elemente nach dem First-in/First-out-Prinzip (FIFO) entfernt. Unterliegt das Postfach jedoch einem Beweissicherungsverfahren, wird das Postfach nie geleert, und beim Erreichen des Kontingents für wiederherstellbare Elemente wird die Postfachfunktionalität beeinträchtigt.

Daher ist es wichtig, das Ereignisprotokoll regelmäßig auf Warnungen zu überprüfen, die beim Erreichen des Kontingents für wiederherstellbare Elemente für ein Postfach generiert werden. Diese Vorgehensweise kann zudem zum Anzeigen von Statistiken für den Ordner "Wiederherstellbare Elemente" verwendet werden – insbesondere für Postfächer, die einem Beweissicherungsverfahren unterliegen.

Weitere Informationen finden Sie unter den folgenden Themen:

  - [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md)

  - [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachordner" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Abrufen von Statistiken für den Ordner **Wiederherstellbare Elemente** für ein Postfach verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Was möchten Sie machen?

## Abrufen von Statistiken für den Ordner "Wiederherstellbare Elemente" eines Postfachs

In diesem Beispiel werden Statistiken für den Ordner **Wiederherstellbare Elemente** von Soumya Singhi abgerufen, und die Ausgabe wird im Listenformat angezeigt.

    Get-MailboxFolderStatistics -Identity "Soumya Singhi" -FolderScope RecoverableItems | Format-List

In diesem Beispiel werden Statistiken für den Ordner **Wiederherstellbare Elemente** von Soumya Singhi abgerufen, und der Ordnername, der Ordnerpfad, die Anzahl von Elementen innerhalb des Ordners sowie die Ordnergröße werden im Tabellenformat angezeigt.

    Get-MailboxFolderStatistics -Identity "Soumya Singhi" -FolderScope RecoverableItems | Format-Table Name,FolderPath,ItemsInFolder,FolderAndSubfolderSize

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxFolderStatistics](https://technet.microsoft.com/de-de/library/aa996762\(v=exchg.150\)).

## Abrufen von Statistiken für den Ordner "Wiederherstellbare Elemente" für alle Postfächer, die dem Beweissicherungsverfahren unterliegen

In diesem Beispiel wird eine Liste aller Postfächer abgerufen, die einem Beweissicherungsverfahren unterliegen. Zudem werden für die einzelnen Postfächer Postfachordnerstatistiken für den Ordner "Wiederherstellbare Elemente" und seine Unterordner abgerufen. Die Eigenschaften **Identity** (Postfachordneridentität) und **FolderAndSubfolderSize** werden im Tabellenformat angezeigt.

    Get-Mailbox -ResultSize Unlimited -Filter {LitigationHoldEnabled -eq $true} | Get-MailboxFolderStatistics | Format-Table Identity,FolderAndSubfolderSize

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) und [Get-MailboxFolderStatistics](https://technet.microsoft.com/de-de/library/aa996762\(v=exchg.150\)).

## Kontingent für wiederherstellbare Elemente für ein Postfach abrufen

In diesem Beispiel wird das Kontingent und der Warngrenzwert für den Ordner "Wiederherstellbare Elemente" für ein Benutzerpostfach veranschaulicht. In diesem Beispiel werden außerdem Informationen abgerufen, ob für das Postfach ein Beweissicherungsverfahren aktiviert ist oder es im Compliance-Archiv platziert ist.

    Get-Mailbox -Identity <identity of mailbox> | Format-List RecoverableItems*,LitigationHoldEnabled,InPlaceHolds

In diesem Beispiel wird das Kontingent und der Warngrenzwert für den Ordner "Wiederherstellbare Elemente" für alle Benutzerpostfächer in Ihrer Organisation veranschaulicht. In dem Beispiel werden außerdem Archiv-Informationen abgerufen.

    Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Format-List Name,RecoverableItems*,LitigationHoldEnabled,InPlaceHolds

