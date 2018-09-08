---
title: 'Suchen nach und Löschen von Nachrichten – Adminhilfe: Exchange 2013-Hilfe'
TOCTitle: Suchen nach und Löschen von Nachrichten – Administratorhilfe
ms:assetid: 8c36bb03-e716-4fdd-9958-4aa7a2a1db42
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff459253(v=EXCHG.150)
ms:contentKeyID: 52062756
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Suchen nach und Löschen von Nachrichten – Administratorhilfe

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-12-20_

Mithilfe des Cmdlets **Search-Mailbox** können Administratoren Benutzerpostfächer durchsuchen und anschließend Nachrichten aus Postfächern löschen.

Um Nachrichten in einem Schritt zu suchen und zu löschen, führen Sie das Cmdlet **Search-Mailbox** mit der Option *DeleteContent* aus. Dabei können Sie jedoch keine Suchergebnisse in einer Vorschau anzeigen und kein Protokoll der von der Suche zurückgegebenen Nachrichten generieren. Außerdem löschen Sie ggf. versehentlich Nachrichten, die Sie gar nicht löschen wollten. Um ein Protokoll der von der Suche gefundenen Nachrichten in der Vorschau anzuzeigen, bevor sie gelöscht werden, führen Sie das Cmdlet **Search-Mailbox** mit der Option *LogOnly* aus.

Als zusätzliche Schutzmaßnahme können Sie die Nachrichten zuerst in ein anderes Postfach kopieren; dazu verwenden Sie die Parameter *TargetMailbox* und *TargetFolder*. So behalten Sie eine Kopie der gelöschten Nachrichten für den Fall, dass Sie wieder auf sie zugreifen müssen.

## Was muss ich wissen, bevor ich beginne?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten. Die tatsächliche Zeit kann von der Größe des Postfachs und der Suchabfrage abhängen.

  - Diese Verfahren können nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Ihnen müssen die beiden folgenden Verwaltungsrollen zugewiesen sein, damit Sie in den Benutzerpostfächern nach Nachrichten suchen und Nachrichten löschen können:
    
      - **Postfachsuche**   Mit dieser Rolle können Sie organisationsweit in mehreren Postfächern nach Nachrichten suchen. Administratoren wird diese Rolle nicht standardmäßig zugewiesen. Wenn Sie sich diese Rolle selbst zuweisen möchten, damit Sie Postfächer durchsuchen können, fügen Sie sich als Mitglied der Rollengruppe "Discoveryverwaltung" hinzu. Weitere Informationen finden Sie unter [Zuweisen von eDiscovery-Berechtigungen in Exchange](https://technet.microsoft.com/de-de/library/Dd298059(v=EXCHG.150)).
    
      - **Postfachimport/-export**   Diese Rolle ermöglicht Ihnen das Löschen von Nachrichten aus einem Benutzerpostfach. Diese Rolle ist standardmäßig keiner Rollengruppe zugewiesen. Um Nachrichten aus Benutzerpostfächern zu löschen, können Sie der Rollengruppe "Organisationsverwaltung" die Rolle "Postfachimport/-export" hinzufügen. Weitere Informationen finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md) im Abschnitt "Hinzufügen einer Rolle zu einer Rollengruppe".

  - Wenn für das Postfach, aus dem Sie Nachrichten löschen möchten, die Wiederherstellung einzelner Elemente aktiviert ist, müssen Sie diese Funktion zuerst deaktivieren. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Wiederherstellung einzelner Elemente für ein Postfach](enable-or-disable-single-item-recovery-for-a-mailbox-exchange-2013-help.md).

  - Wenn für das Postfach, aus dem Sie Nachrichten löschen möchten, die Aufbewahrung für eventuelle Rechtsstreitigkeiten festgelegt wurde, sollten Sie bei der Datensatzverwaltungs- oder Rechtsabteilung nachfragen, bevor Sie die entsprechende Sperre aufheben und den Postfachinhalt löschen. Führen Sie nach dem Erhalt der Genehmigung die im Thema [Bereinigen des Ordners "Wiederherstellbare Elemente"](clean-up-the-recoverable-items-folder-exchange-2013-help.md) aufgeführten Schritte aus.

  - Mithilfe des Cmdlets **Search-Mailbox** können maximal 10.000 Postfächer durchsucht werden. Wenn Sie eine Exchange Online-Organisation mit mehr als 10.000 Postfächern haben, können Sie die Funktion „Compliancesuche\&quot; (oder das entsprechende Cmdlet **New-ComplianceSearch**) verwenden, um eine unbegrenzte Anzahl von Postfächern zu durchsuchen. Anschließend können Sie mit dem Cmdlet **New-ComplianceSearchAction** die Nachrichten löschen, die von der Compliancesuche zurückgegeben wurden. Weitere Informationen finden Sie unter [Suchen und Löschen von E-Mail-Nachrichten in Ihrer Office 365-Organisation – Administratorhilfe](https://go.microsoft.com/fwlink/p/?linkid=786856).

  - Wenn Sie eine Suchabfrage (durch Verwendung des Parameters *SearchQuery*) einschließen, gibt das Cmdlet **Search-Mailbox** maximal 10.000 Elemente in den Suchergebnissen zurück. Wenn Sie also eine Suchabfrage einschließen, müssen Sie den Befehl **Search-Mailbox** möglicherweise mehrere Male ausführen, um mehr als 10.000 Elemente zu löschen.

  - Archivpostfach des Benutzers wird auch gesucht werden soll, wenn Sie das **Search-Mailbox** -Cmdlet ausführen. In ähnlicher Weise werden Elemente in der primären Archivpostfach bei Verwendung das **Search-Mailbox** -Cmdlet mit der Option *DeleteContent* gelöscht. Um dies zu verhindern, können Sie die Option *DoNotIncludeArchive* einschließen. Darüber hinaus wird empfohlen, dass Sie nicht die Option *DeleteContent* verwenden, um Nachrichten in Exchange Online Postfächern löschen, die automatisch erweitert Archivierung aktiviert, da unerwartete Datenverlust auftreten kann, haben.

## Suchen von Nachrichten und Protokollieren der Suchergebnisse

In diesem Beispiel wird das Postfach von April Stewart nach Nachrichten mit dem Satz "Your bank statement" im Betrefffeld durchsucht. Die Suchergebnisse werden im Postfach des Administrators im Ordner "SearchAndDeleteLog" protokolliert. Nachrichten werden nicht in das Zielpostfach kopiert und nicht aus diesem gelöscht.

    Search-Mailbox -Identity "April Stewart" -SearchQuery 'Subject:"Your bank statement"' -TargetMailbox administrator -TargetFolder "SearchAndDeleteLog" -LogOnly -LogLevel Full

In diesem Beispiel werden alle Postfächer in der Organisation nach Nachrichten durchsucht, an die ein beliebiger Typ von Datei mit dem Namen "Trojan" angefügt ist. Anschließend wird eine Protokollnachricht an das Administratorpostfach gesendet.

    Get-Mailbox -ResultSize unlimited | Search-Mailbox -SearchQuery attachment:trojan* -TargetMailbox administrator -TargetFolder "SearchAndDeleteLog" -LogOnly -LogLevel Full

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)).

Nach oben

## Suchen und Löschen von Nachrichten

In diesem Beispiel wird das Postfach von April Stewart nach Nachrichten mit dem Satz "Your bank statement" im Betrefffeld durchsucht. Die Nachrichten werden aus dem Quellpostfach gelöscht, ohne dass die Suchergebnisse in einen anderen Ordner kopiert werden. Wie bereits erklärt muss Ihnen die Verwaltungsrolle "Postfachimport/-export" zugewiesen sein, damit Sie Nachrichten aus einem Benutzerpostfach löschen können.


> [!IMPORTANT]
> Wenn Sie das Cmdlet <STRONG>Search-Mailbox</STRONG> mit der Option <EM>DeleteContent</EM> verwenden, werden Nachrichten dauerhaft aus dem Quellpostfach gelöscht. Bevor Sie Nachrichten dauerhaft löschen, sollten Sie mit der Option <EM>LogOnly</EM> ein Protokoll der von der Suche gefundenen Nachrichten generieren, bevor sie gelöscht werden, oder die Nachrichten in ein anderes Postfach kopieren, bevor Sie sie aus dem Quellpostfach löschen.



    Search-Mailbox -Identity "April Stewart" -SearchQuery 'Subject:"Your bank statement"' -DeleteContent

In diesem Beispiel wird das Postfach von April Stewart nach Nachrichten mit dem Satz "Your bank statement" im Betrefffeld durchsucht. Die Suchergebnisse werden in den Ordner "AprilStewart-DeletedMessages" im Postfach "BackupMailbox" kopiert und aus dem Postfach von April Stewart gelöscht.

    Search-Mailbox -Identity "April Stewart" -SearchQuery 'Subject:"Your bank statement"' -TargetMailbox "BackupMailbox" -TargetFolder "AprilStewart-DeletedMessages" -LogLevel Full -DeleteContent

In diesem Beispiel werden alle Postfächer in der Organisation nach Nachrichten mit der Betreffzeile "Laden Sie diese Datei herunter" durchsucht und dauerhaft gelöscht.

    Get-Mailbox -ResultSize unlimited | Search-Mailbox -SearchQuery 'Subject:"Download this file"' -DeleteContent

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)).

Nach oben

## Verwenden des Parameters -LogLevel Full

In einigen der Beispiele oben wurde der Parameter *LogLevel* mit dem Wert `Full` verwendet, um detaillierte Informationen zu den vom Cmdlet **Search-Mailbox** zurückgegebenen Ergebnissen zu protokollieren. Wenn Sie diesen Parameter verwendet haben, wird eine E-Mail-Nachricht erstellt und an das im Parameter *TargetMailbox* angegebene Postfach gesendet. Die Protokolldatei (eine CSV-formatierte Datei mit dem Namen „Results.csv\&quot;) ist dieser E-Mail-Nachricht angefügt und wird in dem Ordner abgelegt, der im Parameter *TargetFolder* angegeben ist. Die Protokolldatei enthält eine Zeile für jede Nachricht, die in den vom Cmdlet **Search-Mailbox** zurückgegebenen Suchergebnissen aufgeführt ist.

