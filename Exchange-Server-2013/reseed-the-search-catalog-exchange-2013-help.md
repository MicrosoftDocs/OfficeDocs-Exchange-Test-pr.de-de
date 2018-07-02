---
title: 'Durchführen eines erneuten Seedings des Suchkatalogs: Exchange 2013 Help'
TOCTitle: Durchführen eines erneuten Seedings des Suchkatalogs
ms:assetid: 9d873bd4-0422-4975-b5e2-82a347479115
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633475(v=EXCHG.150)
ms:contentKeyID: 52062901
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Durchführen eines erneuten Seedings des Suchkatalogs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Wenn der Inhaltsindexkatalog für eine Postfachdatenbank beschädigt ist, müssen Sie ggf. ein erneutes Seeding für den Katalog ausführen. Beschädigte Inhaltsindizes werden im Anwendungsereignisprotokoll durch das folgende Ereignis angezeigt.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignis-ID</th>
<th>Stufe</th>
<th>Quelle</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>123</p></td>
<td><p>Fehler</p></td>
<td><p>ExchangeStoreDB</p></td>
<td><p>Um &lt;<em>Zeitstempel</em>&gt; hat die &lt;<em>Identität</em>&gt;-Datenbankkopie des Microsoft Exchange-Informationsspeichers auf diesem Server einen beschädigten Suchkatalog entdeckt. Überprüfen Sie das Ereignisprotokoll auf dem Server auf weitere Ereignisse vom Typ &quot;ExchangeStoreDb&quot; und &quot;MSExchange Search Indexer&quot;, um genauere Informationen zu dem Fehler zu erhalten. Es wird empfohlen, ein erneutes Seeding für den Katalog mithilfe des Tasks &quot;Update-MailboxDatabaseCopy&quot; auszuführen.</p></td>
</tr>
</tbody>
</table>


Wenn sich die Postfachdatenbankkopie auf einem Server befindet, der Teil einer Database Availability Group (DAG) ist, können Sie ein erneutes Seeding für den Inhaltsindexkatalog von einem anderen DAG-Mitglied durchführen.

Wenn es sich bei der Postfachdatenbankkopie um die einzige Kopie handelt, muss ein neuer Inhaltsindexkatalog erstellt werden.

Anderen Verwaltungsaufgaben in Bezug auf die Exchange-Suche finden Sie unter [Exchange-Suchverfahren](exchange-search-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten. Die tatsächliche Dauer des erneuten Seedings kann je nach Größe des betroffenen Inhaltsindexkatalogs variieren.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange-Suche" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Ausführen eines erneuten Seedings des Inhaltsindexkatalogs, wenn die Postfachdatenbank Teil einer DAG ist

Verwenden Sie eines der folgenden Verfahren, wenn sich die Postfachdatenbank auf einem Server befindet, der Teil einer DAG ist.

## Ausführen eines erneuten Seedings für den Inhaltsindexkatalog von einer beliebigen Quelle aus

In diesem Beispiel wird von einem beliebigen Quellserver in der DAG aus, der über eine Kopie der Datenbank verfügt, ein erneutes Seeding des Inhaltsindexkatalogs der Datenbankkopie "DB1" auf dem Postfachserver "MBX1" ausgeführt.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1 -CatalogOnly

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)).

## Ausführen eines erneuten Seedings für den Inhaltsindexkatalog von einer bestimmten Quelle aus

In diesem Beispiel wird vom Postfachserver "MBX2" aus, der auch über eine Kopie der Datenbank verfügt, ein erneutes Seeding für den Inhaltsindexkatalog der Datenbankkopie "DB1" auf dem Postfachserver "MBX1" ausgeführt.

    Update-MailboxDatabaseCopy -Identity DB1\MBX1 -SourceServer MBX2 -CatalogOnly

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)).

## Ausführen eines erneuten Seedings für den Inhaltsindexkatalog, wenn nur eine Kopie der Postfachdatenbank vorhanden ist

Wenn nur eine Kopie der Postfachdatenbank vorhanden ist, müssen Sie ein erneutes Seeding des Inhaltsindexkatalogs ausführen, indem Sie den Inhaltsindexkatalog neu erstellen.

1.  Führen Sie die folgenden Befehle aus, um den Microsoft Exchange-Such- und den Microsoft Exchange-Suchhost-Controllerdienst anzuhalten.
    
        Stop-Service MSExchangeFastSearch
    
        Stop-Service HostControllerService

2.  Löschen oder verschieben Sie den Ordner, der den Exchange-Inhaltsindexkatalog enthält, oder benennen Sie diesen um. Dieser Ordner heißt `%ExchangeInstallPath\Mailbox\<name of mailbox database>_Catalog\<GUID>12.1.Single`. Sie können den Ordner z. B. in `C:\Program Files\Microsoft\Exchange Server\V15\Mailbox\Mailbox Database 0657134726_Catalog\F0627A72-9F1D-494A-839A-D7C915C279DB12.1.Single_OLD` umbenennen.
    

    > [!NOTE]
    > Durch das Löschen dieses Ordners wird zusätzlicher Speicherplatz verfügbar. Alternativ können Sie den Ordner umbenennen oder verschieben, damit sie zu Problembehandlungszwecken darauf zurückgreifen können.



3.  Führen Sie die folgenden Befehle aus, um den Microsoft Exchange-Such- und den Microsoft Exchange-Suchhost-Controllerdienst neu zu starten.
    
        Start-Service MSExchangeFastSearch
    
        Start-Service HostControllerService
    
    Nachdem Sie diese Dienste neu gestartet haben, wird der Inhaltsindexkatalog von der Exchange-Suche neu erstellt.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Es kann einige Zeit dauern, bis die Exchange-Suche ein erneutes Seeding für den Inhaltsindexkatalog ausgeführt hat. Führen Sie den folgenden Befehl aus, um den Status des erneuten Seeding-Vorgangs anzuzeigen.

    Get-MailboxDatabaseCopyStatus | FL Name,*Index*

Während des erneuten Seedings des Suchkatalogs lautet der Wert der *ContentIndexState*-Eigenschaft **Crawling**. Wenn das erneute Seeding abgeschlossen ist, wird dieser Wert in **Healthy** geändert.

