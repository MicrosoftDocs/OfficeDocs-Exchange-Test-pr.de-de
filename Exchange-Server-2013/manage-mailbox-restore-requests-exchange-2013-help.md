---
title: 'Verwalten von Postfachwiederherstellungsanforderungen: Exchange 2013 Help'
TOCTitle: Verwalten von Postfachwiederherstellungsanforderungen
ms:assetid: 8e668a52-c601-4d96-a51c-ab60267e1321
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863437(v=EXCHG.150)
ms:contentKeyID: 50554874
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Postfachwiederherstellungsanforderungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mithilfe von Postfachwiederherstellungsanforderungen werden getrennte Postfächer wiederhergestellt. Bei einem getrennten Postfach handelt es sich um ein Postfach in der Exchange-Postfachdatenbank, das keinem Active Directory-Benutzerkonto zugeordnet ist. Postfächer werden getrennt, wenn sie deaktiviert, gelöscht oder in eine andere Datenbank verschoben werden. Weitere Informationen finden Sie unter [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md).

Getrennte Postfächer verbleiben so lange in der Postfachdatenbank wie in den Einstellungen für die Aufbewahrung gelöschter Postfächer für die Postfachdatenbank angegeben. Der Standardwert für die Aufbewahrung getrennter Postfächer beträgt 30 Tage. Während des Aufbewahrungszeitraums kann der Inhalt eines gelöschten Postfachs in einem vorhandenen Postfach wiederhergestellt (d. h. in dieses kopiert) werden. In diesem Thema wird das Verwalten von Anforderungen zur Postfachwiederherstellung mithilfe der Shell beschrieben.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit getrennten Postfächern finden Sie in den folgenden Themen:

[Deaktivieren oder Löschen eines Postfachs](disable-or-delete-a-mailbox-exchange-2013-help.md)

[Verbinden eines deaktivierten Postfachs](connect-a-disabled-mailbox-exchange-2013-help.md)

[Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

[Wiederherstellen eines vorläufig gelöschten Postfachs](restore-a-soft-deleted-mailbox-exchange-2013-help.md)

[Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellungsanforderung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Verfahren in diesem Thema können nur in der Shell ausgeführt werden. Die Exchange-Verwaltungskonsole kann nicht zum Verwalten von Anforderungen zur Postfachwiederherstellung verwendet werden.

  - Führen Sie den folgenden Befehl aus, um den Wert der Eigenschaft *Identity* für alle Anforderungen zur Postfachwiederherstellung anzuzeigen.
    
    ```powershell
Get-MailboxRestoreRequest | Format-Table Identity
```
    
    Anhand dieses Identitätswerts können Sie beim Durchführen der Verfahren in diesem Thema eine bestimmte Anforderung zur Postfachwiederherstellung angeben.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen der Eigenschaften von Wiederherstellungsanforderungen mithilfe der Shell

Sie können die Eigenschaften einer Anforderung zur Postfachwiederherstellung anzeigen, die grundlegende Informationen zum Status einer Anforderung zur Postfachwiederherstellung bereitstellen.

Führen Sie den folgenden Befehl aus, um eine Liste und den Wert der Eigenschaft *Identity* für alle Anforderungen zur Postfachwiederherstellung anzuzeigen.

```powershell
Get-MailboxRestoreRequest | Format-Table Identity
```

Über die Identitätswert erhalten Sie Informationen zu bestimmten Anforderungen zur Postfachwiederherstellung.

In diesem Beispiel wird der Status der Wiederherstellungsanforderung "Pilar Pinilla\\MailboxRestore" mit dem Parameter *Identity* zurückgegeben.

    Get-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore"

Dieses Beispiel gibt alle Informationen zur zweiten Anforderung zur Postfachwiederherstellung für das Zielpostfach "Pilar Pinilla" zurück.

    Get-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1" | Format-List

In diesem Beispiel werden die Status von Wiederherstellungsanforderungen zurückgegeben, die aus der Quelldatenbank "MBD01" wiederhergestellt werden.

```powershell
Get-MailboxRestoreRequest -SourceDatabase MBD01
```

In diesem Beispiel werden alle Wiederherstellungsanforderungen zurückgegeben, die derzeit aktiv sind.

```powershell
Get-MailboxRestoreRequest -Status InProgress
```

Andere nützliche Status sind `Queued`, `Completed`, `Suspended` und `Failed`.

In diesem Beispiel werden alle Wiederherstellungsanforderungen zurückgegeben, die angehalten wurden.

```powershell
Get-MailboxRestoreRequest -Suspend $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829907\(v=exchg.150\)).

## Ausgabe von Get-MailboxRestoreRequest

Das Cmdlet **Get-MailboxRestoreRequest** gibt standardmäßig den Namen der Anforderung, das Zielpostfach, in dem die Daten wiederhergestellt werden, und den Status der Anforderung zurück. In der folgenden Tabelle sind nützliche Informationen aufgelistet, die zurückgegeben werden, wenn Sie die Ausgabe des Cmdlet an das Cmdlet **Format-List** weiterleiten.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>SourceDatabase</code></p></td>
<td><p>Gibt die Datenbank an, die das getrennte Postfach enthält, das wiederhergestellt wird.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetMailbox</code></p></td>
<td><p>Gibt das Postfach an, in dem die Daten wiederhergestellt werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>Name</code></p></td>
<td><p>Gibt den Namen der Anforderung an.</p></td>
</tr>
<tr class="even">
<td><p><code>RequestQueue</code></p></td>
<td><p>Gibt die Datenbank an, in der der Microsoft Exchange-Postfachreplikationsdienst den detaillierten Status der Anforderung speichert.</p></td>
</tr>
<tr class="odd">
<td><p><code>Status</code></p></td>
<td><p>Gibt den Status der Anforderung an.</p></td>
</tr>
<tr class="even">
<td><p><code>Suspend</code></p></td>
<td><p>Gibt an, ob die Anforderung angehalten ist. Eine Postfachwiederherstellung kann angehalten werden, wenn sie mit dem Cmdlet <strong>New-MailboxRestoreRequest</strong> unter Angabe des Parameters <em>Suspend</em> erstellt wird. Sie kann auch angehalten werden, wenn der Vorgang zur Postfachwiederherstellung misslingt oder ein Administrator das Cmdlet <strong>Suspend-MailboxRestoreRequest</strong> ausführt.</p></td>
</tr>
<tr class="odd">
<td><p><code>Identity</code></p></td>
<td><p>Gibt die Identität der Anforderung an. Diese Identität ist eine Kombination aus dem Namen des Zielpostfachs und dem Namen der Anforderung.</p></td>
</tr>
</tbody>
</table>


## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie das Cmdlet **Get-MailboxRestoreRequest** aus, um zu prüfen, ob Sie die Eigenschaften von Anforderungen zur Postfachwiederherstellung anzeigen können. Wenn das Cmdlet einen Fehler zurückgibt, prüfen Sie, ob Sie die ordnungsgemäße Syntax und Identität verwenden. Mitunter kann das Cmdlet erfolgreich ausgeführt werden und trotzdem keine Ergebnisse zurückgeben. Wenn Sie beispielsweise eine Anforderung zur Postfachwiederherstellung gestellt haben und den Befehl `Get-MailboxRestoreRequest -Status InProgress` ausführen, ohne dass Ergebnisse zurückgegeben werden, ist keine der Wiederherstellungsanforderungen derzeit aktiv.

## Anzeigen von Statistiken zu Wiederherstellungsanforderungen mithilfe der Shell

Sie können die Statistiken zu einer Anforderung zur Postfachwiederherstellung anzeigen, die für Problembehandlungszwecke detaillierte Informationen bereitstellen.

In diesem Beispiel werden die Standardstatistiken für die Wiederherstellungsanforderung "danp\\MailboxRestore1" zurückgegeben. Standardmäßig enthalten die zurückgegebenen Informationen den Namen, das Postfach, den Status und den Prozentsatz der Fertigstellung.

    Get-MailboxRestoreRequestStatistics -Identity danp\MailboxRestore1

In diesem Beispiel werden Statistiken für das Postfach von Dan Park zurückgegeben, und der Bericht wird in eine CSV-Datei exportiert.

    Get-MailboxRestoreRequestStatistics -Identity "Dan Park\MailboxRestore" | Export-CSV \\SERVER01\RestoreRequest_Reports\DanPark_Restorestats.csv

In diesem Beispiel werden zusätzliche Informationen zur Wiederherstellungsanforderung für das Postfach von Pilar Pinilla zurückgegeben, indem der Parameter *IncludeReport* verwendet und die Ergebnisse an das Cmdlet **Format-List** weitergeleitet werden.

    Get-MailboxRestoreRequestStatistics -Identity "Pilar Pinilla\MailboxRestore" -IncludeReport | Format-List 

In diesem Beispiel werden zusätzliche Informationen für alle Wiederherstellungsanforderungen mit dem Status `Failed` zurückgegeben. Zu diesem Zweck wird der Parameter *IncludeReport* verwendet, und die Informationen werden in der Textdatei "AllExportReports.txt" in dem Ordner gespeichert, in dem der Befehl ausgeführt wird.

    Get-MailboxRestoreRequest -Status Failed | Get-MailboxRestoreRequestStatistics -IncludeReport | Format-List > AllRestoreReports.txt

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/de-de/library/ff829912\(v=exchg.150\)) und [Get-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829907\(v=exchg.150\)).

## Ausgabe von Get-MailboxRestoreRequestStatistics

Standardmäßig gibt das Cmdlet [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/de-de/library/ff829912\(v=exchg.150\)) den Namen der Anforderung, den Status der Anforderung, den Alias des Zielpostfachs und den Prozentsatz der Fertigstellung zurück. In der folgenden Tabelle sind andere nützliche Informationen aufgelistet, die zurückgegeben werden, wenn Sie die Ausgabe des Cmdlets an das Cmdlet **Format-List** weiterleiten.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Name</code></p></td>
<td><p>Gibt den Namen der Anforderung an.</p></td>
</tr>
<tr class="even">
<td><p><code>Status</code></p></td>
<td><p>Gibt den Status der Anforderung an.</p></td>
</tr>
<tr class="odd">
<td><p><code>StatusDetail</code></p></td>
<td><p>Gibt weitere Details zum Status der Anforderung an. Wenn <code>Status</code> beispielsweise den Wert <code>InProgress</code> zurückgibt, werden für <code>StatusDetail</code> die speziellen Phasen für den Status <code>InProgress</code> zurückgegeben (z. B. <code>CreatingFolderHierarchy</code> und <code>CopyingMessages</code>).</p></td>
</tr>
<tr class="even">
<td><p><code>SyncStage</code></p></td>
<td><p>Gibt an, wie weit die Anforderung den Wiederherstellungsvorgang abgearbeitet hat.</p></td>
</tr>
<tr class="odd">
<td><p><code>Suspend</code></p></td>
<td><p>Gibt an, ob die Wiederherstellungsanforderung angehalten ist. Dieser Wert ist <code>true</code>, wenn eines der folgenden Szenarien vorliegt:</p>
<ul>
<li><p>Der Postfachreplikationsdienst hat die Anforderung wegen eines Fehlers gestoppt oder ist dabei, dies zu tun.</p></li>
<li><p>Ein Administrator hat die Anforderung angehalten.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>SourceExchangeGuid</code></p></td>
<td><p>Gibt die GUID des Quellpostfachs an, aus dem die Daten wiederhergestellt werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>SourceRootFolder</code></p></td>
<td><p>Gibt den Namen des Stammordners für die Hierarchie des Quellpostfachs an, aus dem die Daten wiederhergestellt werden. Ist dieser Wert leer, werden die Daten aus dem Ordner auf der obersten Ebene des Informationsspeichers wiederhergestellt.</p></td>
</tr>
<tr class="even">
<td><p><code>SourceDatabase</code></p></td>
<td><p>Gibt den Namen der Datenbank an, in der sich das Quellpostfach befindet.</p></td>
</tr>
<tr class="odd">
<td><p><code>MailboxRestoreFlags</code></p></td>
<td><p>Gibt an, dass das wiederherzustellende Postfach entweder <code>Disabled</code> oder <code>Soft-Deleted</code> ist.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetAlias</code></p></td>
<td><p>Gibt den Alias des Zielpostfachs an.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetIsArchive</code></p></td>
<td><p>Gibt an, ob das Postfach in einem Archiv wiederhergestellt wird.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetExchangeGuid</code></p></td>
<td><p>Gibt die GUID des Zielpostfachs an.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetRootFolder</code></p></td>
<td><p>Gibt den Namen des Stammordners in der Hierarchie des Zielpostfachs an, aus dem die Daten wiederhergestellt werden. Ist dieser Wert leer, werden die Daten in dem Ordner auf der obersten Ebene des Informationsspeichers wiederhergestellt.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetDatabase</code></p></td>
<td><p>Gibt den Namen der Datenbank an, in der sich das Zielpostfach befindet.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetMailboxIdentity</code></p></td>
<td><p>Gibt die Identität des Zielpostfachs an.</p></td>
</tr>
<tr class="even">
<td><p><code>IncludeFolders</code></p></td>
<td><p>Gibt die Liste der Ordner an, die wiederhergestellt werden sollen. Ist dieser Wert leer, wurden beim Erstellen der Anforderung keine Ordner angegeben, und es werden alle Ordner in dem Postfach wiederhergestellt (es sei denn, der Parameter <em>ExcludeFolders</em> wird zum Ausschließen bestimmter Ordner verwendet).</p></td>
</tr>
<tr class="odd">
<td><p><code>ExcludeFolders</code></p></td>
<td><p>Gibt die Liste der Ordner an, die beim Wiederherstellen ausgeschlossen werden sollen. Ist dieser Wert leer, wurden beim Erstellen der Anforderung keine Ordner angegeben, und es werden alle Ordner in dem Postfach wiederhergestellt (es sei denn, der Parameter <em>IncludeFolders</em> wird zum Einschließen bestimmter Ordner verwendet).</p></td>
</tr>
<tr class="even">
<td><p><code>ExcludeDumpster</code></p></td>
<td><p>Gibt an, ob der Ordner &quot;Wiederherstellbare Elemente&quot; beim Erstellen der Anforderung ausgeschlossen wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>ConflictResolutionOption</code></p></td>
<td><p>Gibt die Aktion an, die der Postfachreplikationsdienst ausführen soll, wenn in Ziel- und Quellordnern übereinstimmende Nachrichten vorliegen.</p></td>
</tr>
<tr class="even">
<td><p><code>AssociatedMessagesCopyOption</code></p></td>
<td><p>Gibt an, ob die zugeordneten Nachrichten beim Verarbeiten der Anforderung kopiert werden. Zugeordnete Nachrichten sind besondere Nachrichten, die ausgeblendete Daten mit Informationen zu Regeln, Ansichten und Formularen enthalten.</p></td>
</tr>
<tr class="odd">
<td><p><code>BadItemLimit</code></p></td>
<td><p>Gibt die Anzahl von ungültigen Elementen an, die der Postfachreplikationsdienst überspringt, wenn die Anforderung auf beschädigte Nachrichten stößt.</p></td>
</tr>
<tr class="even">
<td><p><code>BadItemsEncountered</code></p></td>
<td><p>Gibt die Anzahl von beschädigten Nachrichten an, auf die der Befehl gestoßen ist. Ist der Wert für <em>BadItemsEncountered</em> größer als der Wert für <em>BadItemLimit</em>, schlägt die Anforderung fehl.</p></td>
</tr>
<tr class="odd">
<td><p><code>QueuedTimeStamp</code></p></td>
<td><p>Gibt Datum und Uhrzeit der Ausgabe der Anforderung an den Postfachreplikationsdienst an.</p></td>
</tr>
<tr class="even">
<td><p><code>StartTimeStamp</code></p></td>
<td><p>Gibt Datum und Uhrzeit des Starts der Verarbeitung der Wiederherstellungsanforderung durch den Postfachreplikationsdienst an.</p></td>
</tr>
<tr class="odd">
<td><p><code>LastUpdateTimeStamp</code></p></td>
<td><p>Gibt Datum und Uhrzeit an, an dem bzw. zu der die Anforderung das letzte Mal geändert wurde. Die Änderung kann durch einen Administrator oder den Postfachreplikationsdienst vorgenommen worden sein.</p></td>
</tr>
<tr class="even">
<td><p><code>SuspendTimeStamp</code></p></td>
<td><p>Gibt Datum und Uhrzeit an, an dem bzw. zu der die Anforderung angehalten wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>OverallDuration</code></p></td>
<td><p>Gibt die Dauer an, die für das Verarbeiten der Anforderung benötigt wurde. Wenn sich die Anforderung im Zustand <code>Failed</code> befindet, gibt dieser Wert die Dauer zwischen der Ausgabe und dem Fehlschlagen der Anforderung an. Wenn die Anforderung nicht abgeschlossen ist, gibt dieser Wert die Dauer zwischen dem Beginn der Ausführung der Anforderung und dem Ausführen des Cmdlets <strong>Get-MailboxRestoreRequestStatistics</strong> an.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalSuspendedDuration</code></p></td>
<td><p>Gibt die Dauer an, für die sich die Anforderung im Zustand <code>Suspended</code> befunden hat.</p></td>
</tr>
<tr class="odd">
<td><p><code>TotalFailedDuration</code></p></td>
<td><p>Gibt die Dauer an, für die sich die Anforderung im Zustand <code>Failed</code> befunden hat.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalQueuedDuration</code></p></td>
<td><p>Gibt die Dauer an, für die sich die Anforderung im Zustand <code>Queued</code> befunden hat.</p></td>
</tr>
<tr class="odd">
<td><p><code>TotalInProgressDuration</code></p></td>
<td><p>Gibt die Dauer an, für die sich die Anforderung im Zustand <code>In Progress</code> befunden hat.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalStalledDueToHADuration</code></p></td>
<td><p>Gibt die Dauer an, für die die Anforderung aufgrund hoher Verfügbarkeit verzögert wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>MRSServerName</code></p></td>
<td><p>Gibt den Namen des Clientzugriffsservers an, der die Anforderung verarbeitet hat.</p></td>
</tr>
<tr class="even">
<td><p><code>EstimatedTransferSize</code></p></td>
<td><p>Gibt die Dateigröße an, die wiederhergestellt wurde oder vom Postfachreplikationsdienst als wiederherzustellend erwartet wird, wenn die Anforderung den Status <code>In Progress</code> hat.</p></td>
</tr>
<tr class="odd">
<td><p><code>EstimatedTransferItemCount</code></p></td>
<td><p>Gibt die Anzahl von wiederhergestellten Elementen oder die Anzahl von Elementen an, die der Postfachreplikationsdienst als wiederherzustellende Elemente erwartet, wenn die Anforderung sich im Zustand <code>In Progress</code> befindet.</p></td>
</tr>
<tr class="even">
<td><p><code>BytesTransferredPerMinute</code></p></td>
<td><p>Gibt die durchschnittliche Anzahl von Bytes an, die pro Minute übertragen wurden.</p></td>
</tr>
<tr class="odd">
<td><p><code>ItemsTransferred</code></p></td>
<td><p>Gibt die Anzahl von Elementen an, die übertragen wurden.</p></td>
</tr>
<tr class="even">
<td><p><code>PercentComplete</code></p></td>
<td><p>Gibt den Prozentsatz der Anforderung an, der abgeschlossen wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>CompletedRequestAgeLimit</code></p></td>
<td><p>Gibt an, wie lange eine abgeschlossene Wiederherstellungsanforderung aufbewahrt wird, ehe sie gelöscht wird. Der Standardwert beträgt 30 Tage.</p></td>
</tr>
<tr class="even">
<td><p><code>PositionInQueue</code></p></td>
<td><p>Falls die Anforderung noch nicht gestartet wurde, gibt dieser Wert die Position der Anforderung in der Warteschlange an.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureCode</code></p></td>
<td><p>Wenn ein Fehler aufgetreten ist, gibt dieser Wert den Fehlercode an.</p></td>
</tr>
<tr class="even">
<td><p><code>FailureType</code></p></td>
<td><p>Wenn ein Fehler aufgetreten ist, gibt dieser Wert den Fehlertyp an.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureSide</code></p></td>
<td><p>Wenn ein Fehler aufgetreten ist, gibt dieser Wert an, ob der Fehler für das Zielpostfach oder das Quellpostfach aufgetreten ist.</p></td>
</tr>
<tr class="even">
<td><p><code>Message</code></p></td>
<td><p>Wenn ein Fehler aufgetreten ist, gibt dieser Wert die Fehlermeldung an. Dieser Wert kann auch den Kommentar zum Anhalten angeben.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureTimestamp</code></p></td>
<td><p>Ist die Anforderung fehlgeschlagen, gibt dieser Wert Datum und Uhrzeit an, an dem bzw. zu der die Anforderung fehlgeschlagen ist.</p></td>
</tr>
<tr class="even">
<td><p><code>FailureContext</code></p></td>
<td><p>Ist die Anforderung fehlgeschlagen, gibt dieser Wert Informationen zu der Aktion an, die zum Fehlerzeitpunkt ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>ValidationMessage</code></p></td>
<td><p>War die Anforderung nicht gültig, gibt dieser Wert den Grund an.</p></td>
</tr>
<tr class="even">
<td><p><code>RequestQueue</code></p></td>
<td><p>Gibt die Datenbank an, in der der Postfachreplikationsdienst den detaillierten Status der Anforderung speichert.</p></td>
</tr>
<tr class="odd">
<td><p><code>Identity</code></p></td>
<td><p>Gibt die Identität der Anforderung an.</p></td>
</tr>
<tr class="even">
<td><p><code>Report</code></p></td>
<td><p>Wenn Sie den Parameter <em>IncludeReport</em> verwendet haben, gibt dieser Wert Informationen an, die zur Problembehandlung der Anforderung verwendet werden können.</p></td>
</tr>
</tbody>
</table>


## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie das Cmdlet **Get-MailboxRestoreRequestStatistics** aus, um zu prüfen, ob Sie die Statistiken von Anforderungen zur Postfachwiederherstellung anzeigen können. Wenn das Cmdlet einen Fehler zurückgibt, prüfen Sie, ob Sie die ordnungsgemäße Syntax und Identität für die Wiederherstellungsanforderung verwenden.

## Ändern der Eigenschaften von Wiederherstellungsanforderungen mithilfe der Shell

Wenn eine Anforderung zur Postfachwiederherstellung keinen Erfolg hat, können Sie mithilfe des Cmdlets **Set-MailboxRestoreRequest** die Eigenschaften der Anforderung ändern, um für eine erfolgreiche Wiederherstellung zu sorgen.

In diesem Beispiel wird festgelegt, dass die Wiederherstellungsanforderung "MailboxRestore1" für das Postfach von Debra Garcia zehn beschädigte Postfachelemente überspringt.

    Set-MailboxRestoreRequest -Identity "Debra Garcia\MailboxRestore1" -BadItemLimit 10

In diesem Beispiel wird festgelegt, dass die Wiederherstellungsanforderung "MailboxRestore1" für Florence Flipo Postfach 100 beschädigte Elemente überspringt. Da der Wert für *BadItemLimit* über 50 liegt, muss der Parameter *AcceptLargeDataLoss* angegeben werden.

    Set-MailboxRestoreRequest -Identity "Florence Flipo\MailboxRestore1" -BadItemLimit 100 -AcceptLargeDataLoss

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829909\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu prüfen, ob Sie die Eigenschaft einer Wiederherstellungsanforderung erfolgreich geändert haben, führen Sie das Cmdlet **Get-MailboxRestoreRequestStatistics** aus, um die geänderten Eigenschaften der Wiederherstellungsanforderung anzuzeigen. Wenn die Wiederherstellungsanforderung erfolgreich erstellt wurde, hat die Eigenschaft *Status* den Wert `Queued`, `InProgress` oder `Completed`. Nachdem die Wiederherstellungsanforderung abgeschlossen wurde, wird der Inhalt des vorläufig gelöschten Postfachs im Zielpostfach angezeigt.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/de-de/library/ff829912\(v=exchg.150\)).

## Verwenden der Shell zum Anhalten einer Wiederherstellungsanforderung

Sie können eine Wiederherstellungsanforderung jederzeit anhalten, nachdem die Anforderung erstellt wurde und bevor sie den Status `Completed` erreicht. Unter Fortsetzen einer Wiederherstellungsanforderung mithilfe der Shell weiter unten in diesem Thema finden Sie die Syntax des Befehls zum Fortsetzen der Wiederherstellungsanforderung mithilfe des Cmdlets [Resume-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829908\(v=exchg.150\)).

In diesem Beispiel wird die Wiederherstellungsanforderung MailboxRestore1 für das Postfach von Pilar Pinilla fortgesetzt.

    Suspend-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

In diesem Beispiel werden alle aktiven Wiederherstellungsanforderungen angehalten. Dazu werden zuerst alle Anforderungen mit dem Status `InProgress` abgerufen. Die Ausgabe wird dann mit dem Kommentar "Resume after FY13Q2 Maintenance" an das Cmdlet **Suspend-MailboxRestoreRequest** weitergeleitet.

    Get-MailboxRestoreRequest -Status InProgress | Suspend-MailboxRestoreRequest -SuspendComment "Resume after FY13Q2 Maintenance"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Suspend-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829906\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um das erfolgreiche Anhalten einer Anforderung zur Postfachwiederherstellung zu überprüfen:

```powershell
Get-MailboxRestoreRequest <identity> | Format-List Suspend,Status
```

Wenn die Eigenschaft *Suspend* den Wert `True` hat, wurde die Wiederherstellungsanforderung erfolgreich angehalten. Zudem gibt der Wert `Suspended` für die Eigenschaft *Status* an, dass die Wiederherstellungsanforderung angehalten wurde.

## Fortsetzen einer Wiederherstellungsanforderung mithilfe der Shell

Verwenden Sie das Cmdlet **Resume-MailboxRestoreRequest**, um eine Wiederherstellungsanforderung fortzusetzen, die angehalten wurde oder bei der Fehler aufgetreten sind.

In diesem Beispiel wird die Wiederherstellungsanforderung "Pilar Pinilla\\MailboxRestore1" fortgesetzt.

    Resume-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

In diesem Beispiel werden alle Wiederherstellungsanforderungen mit dem Status "Failed" fortgesetzt.

```powershell
Get-MailboxRestoreRequest -Status Failed | Resume-MailboxRestoreRequest
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Resume-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829908\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um zu prüfen, ob eine Wiederherstellungsanforderung fortgesetzt wurde.

```powershell
Get-MailboxRestoreRequest <identity> | Format-List Suspend,Status
```

Wenn die Eigenschaft *Suspend* den Wert `False` hat, wurde die Wiederherstellungsanforderung erfolgreich fortgesetzt. Zudem gibt der Wert `InProgress` für die Eigenschaft *Status* an, dass die Wiederherstellungsanforderung fortgesetzt wurde.

## Verwenden der Shell zum Entfernen einer Wiederherstellungsanforderung

Verwenden Sie das Cmdlet **Remove-MailboxRestoreRequest**, um Wiederherstellungsanforderungen für Postfächer zu entfernen. Wenn Sie eine Wiederherstellungsanforderung entfernen, nachdem begonnen wurde, Postfachdaten in das Zielpostfach zu kopieren, verbleiben die kopierten Postfachdaten im Zielpostfach.


> [!NOTE]
> Wie zuvor erwähnt, werden abgeschlossene Wiederherstellungsanforderungen standardmäßig 30&nbsp;Tage aufbewahrt, bevor sie automatisch gelöscht werden.



In diesem Beispiel wird die Wiederherstellungsanforderung "Pilar Pinilla\\MailboxRestore1" entfernt.

    Remove-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

In diesem Beispiel werden alle Wiederherstellungsanforderungen mit dem Status "Completed" entfernt.

```powershell
Get-MailboxRestoreRequest -Status Completed | Remove-MailboxRestoreRequest
```

In diesem Beispiel wird die Wiederherstellungsanforderung unter Verwendung des Parameters *RequestGuid* für eine in "MBXDB01" gespeicherte Anforderung abgebrochen. Der Parametersatz, für den die Parameter *RequestGuid* und *RequestQueue* erforderlich sind, wird ausschließlich für Debuggingzwecke des Replikationsdiensts von Microsoft verwendet. Sie sollten diesen Parametersatz nur verwenden, wenn Sie vom Kundensupport von Microsoft dazu aufgefordert werden.

```powershell
Remove-MailboxRestoreRequest -RequestQueue MBXDB01 -RequestGuid 25e0eaf2-6cc2-4353-b83e-5cb7b72d441f
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829910\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um das erfolgreiche Entfernen einer Anforderung zur Postfachwiederherstellung zu überprüfen:

```powershell
Get-MailboxRestoreRequest -Identity <identity of removed restore request>
```

Der Befehl gibt die Fehlermeldung zurück, dass die Wiederherstellungsanforderung nicht vorhanden ist.

Sie können auch das Cmdlet **Get-MailboxRestoreRequest** ausführen. Wenn die Wiederherstellungsanforderung erfolgreich entfernt wurde, ist sie nicht in den Ergebnissen enthalten.

