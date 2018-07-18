---
title: 'Leistungsindikatoren für die Verwaltung von Nachrichtendatensätzen: Exchange 2013 Help'
TOCTitle: Leistungsindikatoren für die Verwaltung von Nachrichtendatensätzen
ms:assetid: b59def6f-4249-4e0c-8057-8ae6eb7c5676
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb310790(v=EXCHG.150)
ms:contentKeyID: 51409331
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Leistungsindikatoren für die Verwaltung von Nachrichtendatensätzen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mithilfe der in diesem Thema beschriebenen Leistungsindikatoren wird der Assistent für verwaltete Ordner beim Implementieren der Messaging-Datensatzverwaltung (Messaging Records Management, MRM) für Microsoft Exchange Server 2010 überwacht. Da es sich bei der Ausführung des Assistenten für verwaltete Ordner um einen ressourcenintensiven Vorgang handelt, sollten Sie ihn nur ausführen, wenn der Server die zusätzliche Auslastung abfangen kann. Sie müssen die Serverleistung auch überwachen, wenn der Assistent für verwaltete Ordner ausgeführt wird. Zusätzlich zu den in diesem Thema aufgeführten Leistungsindikatoren können Sie weitere Leistungsindikatoren verwenden, um u. a. die Datenträgerleistung und CPU-Auslastung zu überwachen.

Weitere Informationen zum Überwachen von Computern, auf denen MRM ausgeführt wird, finden Sie unter [Überwachen von messaging-datensatzverwaltung](monitoring-messaging-records-management-exchange-2013-help.md).

## Leistungsindikatoren für MRM

In der folgenden Tabelle werden die Leistungsindikatoren für MRM beschrieben.

### Leistungsindikatoren, Leistungsobjekte und Beschreibung

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Leistungsindikator</th>
<th>Leistungsobjekt</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Durchschnittliche Postfachverarbeitungszeit in Sekunden</p></td>
<td><p>MSExchange-Assistenten</p></td>
<td><p>Hiermit wird die durchschnittliche Zeit erfasst, die zeitbasierte Assistenten für die Verarbeitung von Postfächern benötigen.</p></td>
</tr>
<tr class="even">
<td><p>Verarbeitete Postfächer</p></td>
<td><p>MSExchange-Assistenten</p></td>
<td><p>Hiermit wird die Anzahl der seit dem Start des Diensts von zeitbasierten Assistenten verarbeiteten Postfächer erfasst.</p></td>
</tr>
<tr class="odd">
<td><p>Verarbeitete Postfächer/s</p></td>
<td><p>MSExchange-Assistenten</p></td>
<td><p>Hiermit wird die Rate der pro Sekunde von zeitbasierten Assistenten verarbeiteten Postfächer ermittelt.</p></td>
</tr>
<tr class="even">
<td><p>Gelöschte, aber wiederherstellbare Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner gelöschten Elemente erfasst. (Die Elemente können jedoch über den Ordner &quot;Wiederherstellbare Elemente&quot; wiederhergestellt werden.) Die Anzahl umfasst Elemente in den während des Zeitplanintervalls für die Verarbeitung vorgesehenen Postfächern sowie Elemente in allen von Ihnen für die Verarbeitung angegebenen Postfächern. Dieser Indikator wird zu Beginn jedes Zeitplanintervalls auf Null zurückgesetzt.</p></td>
</tr>
<tr class="odd">
<td><p>Im Journal erfasste Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner im Journal erfassten Elemente ermittelt. Die Anzahl umfasst Elemente in den Postfächern, die während des aktuellen Arbeitszyklus für die Verarbeitung vorgesehen sind, sowie Elemente in allen Postfächern, die für die Verarbeitung angegeben wurden. Dieser Indikator wird zu Beginn jedes Arbeitszyklus auf Null zurückgesetzt.</p></td>
</tr>
<tr class="even">
<td><p>Elemente mit Markierung für Überschreitung des Aufbewahrungsgrenzwerts</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der Elemente erfasst, die seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner als den Aufbewahrungsgrenzwert überschreitend markiert wurden. Die Anzahl umfasst Elemente in den Postfächern, die während des Zeitplanintervalls für die Verarbeitung vorgesehen sind, sowie Elemente in allen Postfächern, die für die Verarbeitung angegeben wurden. Dieser Indikator wird zu Beginn jedes Zeitplanintervalls auf Null zurückgesetzt.</p></td>
</tr>
<tr class="odd">
<td><p>Verschobene Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner verschobenen Elemente erfasst. Die Anzahl umfasst Elemente in den Postfächern, die während des Zeitplanintervalls für die Verarbeitung vorgesehen sind, sowie Elemente in allen Postfächern, die für die Verarbeitung angegeben wurden. Dieser Indikator wird zu Beginn jedes Zeitplanintervalls auf Null zurückgesetzt.</p></td>
</tr>
<tr class="even">
<td><p>Endgültig gelöschte Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner endgültig gelöschten Elemente erfasst. Die Anzahl umfasst Elemente in den Postfächern, die während des Zeitplanintervalls für die Verarbeitung vorgesehen sind, sowie Elemente in allen Postfächern, die für die Verarbeitung angegeben wurden. Dieser Indikator wird zu Beginn jedes Zeitplanintervalls auf Null zurückgesetzt.</p></td>
</tr>
<tr class="odd">
<td><p>Einer Aufbewahrungsrichtlinie unterliegende Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Hiermit wird die Anzahl der Elemente erfasst, die seit Beginn des letzten Zeitplanintervalls vom Assistenten für verwaltete Ordner einer Aufbewahrungsrichtlinie zugeordnet wurden. Die Anzahl umfasst Elemente in den Postfächern, die während des Zeitplanintervalls für die Verarbeitung vorgesehen sind, sowie Elemente in allen Postfächern, die für die Verarbeitung angegeben wurden. Dieser Indikator wird zu Beginn jedes Zeitplanintervalls auf Null zurückgesetzt. Dieser Leistungsindikator stellt die Summe aus den folgenden vier ablaufbezogenen Leistungsindikatoren dar:</p>
<ul>
<li><p>Im Journal erfasste Elemente</p></li>
<li><p>Elemente mit Markierung für Überschreitung des Aufbewahrungsgrenzwerts</p></li>
<li><p>Verschobene Elemente</p></li>
<li><p>Endgültig gelöschte Elemente</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>TotalSizeItemsExpired – Größe der Elemente, die der Aufbewahrungsrichtlinie unterliegen (in Byte)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Gesamtgröße der Elemente an, die vom Assistenten für verwaltete Ordner als abgelaufen erkannt wurden (und vorläufig gelöscht, dauerhaft gelöscht oder ins Archiv verschoben wurden).</p>
<p>Die folgenden Elemente sind enthalten:</p>
<ul>
<li><p>Nachrichten, die durch eine Postfachrichtlinie für verwalteten Ordner gelöscht oder in einen benutzerdefinierten Ordner verschoben werden</p></li>
<li><p>Nachrichten, die durch die Aufbewahrungsrichtlinie des Benutzers gelöscht oder in das Archiv verschoben werden</p></li>
<li><p>Nachrichten, die nach der Dumpsterrichtlinie abgelaufen sind</p></li>
<li><p>Nachrichten, die durch Systembereinigungstags bereinigt wurden</p></li>
</ul>
<p>Dieser Indikator wird an jedem Prüfpunkt des Arbeitszyklus des Assistenten für verwaltete Ordner auf Null zurückgesetzt.</p></td>
</tr>
<tr class="odd">
<td><p>TotalSizeItemsSoftDeleted – Größe der Elemente, die gelöscht wurden, aber wiederhergestellt werden können (in Byte)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Gesamtgröße der Elemente an, die vom Assistenten für verwaltete Ordner endgültig gelöscht wurden.</p>
<p>Die folgenden Elemente sind enthalten:</p>
<ul>
<li><p>Nachrichten, die durch eine Postfachrichtlinie für verwalteten Ordner vorläufig gelöscht wurden</p></li>
<li><p>Nachrichten, die durch eine Aufbewahrungsrichtlinie vorläufig gelöscht wurden</p></li>
</ul>
<p>Dieser Indikator wird an jedem Prüfpunkt des Arbeitszyklus des Assistenten für verwaltete Ordner auf Null zurückgesetzt.</p></td>
</tr>
<tr class="even">
<td><p>TotalSizeItemsPermanentlyDeleted – Größe der Elemente, die endgültig gelöscht wurden (in Byte)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Gesamtgröße der Elemente an, die vom Assistenten für verwaltete Ordner endgültig gelöscht wurden.</p>
<p>Die folgenden Elemente sind enthalten:</p>
<ul>
<li><p>Nachrichten, die durch eine Postfachrichtlinie für verwalteten Ordner dauerhaft gelöscht wurden</p></li>
<li><p>Nachrichten, die durch eine Aufbewahrungsrichtlinie dauerhaft gelöscht wurden</p></li>
<li><p>Nachrichten, die durch die Richtlinie für wiederherstellbare Elemente dauerhaft gelöscht wurden</p></li>
</ul>
<p>Dieser Indikator wird an jedem Prüfpunkt des Arbeitszyklus des Assistenten für verwaltete Ordner auf Null zurückgesetzt.</p></td>
</tr>
<tr class="odd">
<td><p>TotalSizeItemsMoved – Größe der Elemente, die infolge eines Archivierungsrichtlinientags verschoben wurden (in Byte)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Gesamtgröße der Elemente an, die vom Assistenten für verwaltete Ordner in einen Ordner oder das Archiv verschoben wurden.</p>
<p>Die folgenden Elemente sind enthalten:</p>
<ul>
<li><p>Nachrichten, die durch eine Postfachrichtlinie für verwalteten Ordner in einen verwalteten benutzerdefinierten Ordner verschoben wurden</p></li>
<li><p>Nachrichten, die durch eine Aufbewahrungsrichtlinie in das persönliche Archiv verschoben wurden</p></li>
</ul>
<p>Dieser Indikator wird an jedem Prüfpunkt des Arbeitszyklus des Assistenten für verwaltete Ordner auf Null zurückgesetzt.</p></td>
</tr>
<tr class="even">
<td><p>TotalItemsWithPersonalTag – Elemente, die mit einem persönlichen Tag markiert wurden (Ablauf- oder Archivtag)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Benutzeraktionen an, bei denen Elemente mit einem persönlichen Tag versehen wurden.</p>
<p>Dazu gehören sowohl Löschungs- als auch Archivtags.</p>
<p>Beispiel:</p>
<ul>
<li><p>Ein Element wird mit einem persönlichen Tag versehen.</p></li>
<li><p>Ein Element mit einem persönlichen Tag wird mit einem weiteren persönlichen Tag versehen.</p></li>
</ul>
<p>Wird ein Ordner mit einem persönlichen Tag versehen, wird der Indikator um die Gesamtanzahl der Elemente in diesem Ordner erhöht.</p></td>
</tr>
<tr class="odd">
<td><p>TotalItemsWithDefaultTag – Elemente, die mit einem Standardtag markiert wurden (Ablauf- oder Archivtag)</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, denen durch eine Benutzeraktion ein Standardrichtlinientag (Default Policy Tag, DPT) zugewiesen wurde, z. B. wenn ein Benutzer eine Nachricht mit einem persönlichen Tag auswählt und dann die Option <strong>Ordnerrichtlinie verwenden</strong> anwendet.</p>
<p>Wird einem neuen Benutzer eine Aufbewahrungsrichtlinie mit Standardrichtlinientag zugewiesen, erhöht sich der Indikator um die Anzahl der Elemente, denen aufgrund der Aufbewahrungsrichtlinie das Standardrichtlinientag zugewiesen wurde.</p>

> [!NOTE]
> Verfügt ein Benutzer über eine Aufbewahrungsrichtlinie mit Standardrichtlinientag, werden neue Nachrichten, die über den Nachrichtentransport empfangen werden, mit einem Standardrichtlinientag versehen. Diese Nachrichten werden von diesem Indikator nicht erfasst.


</td>
</tr>
<tr class="even">
<td><p>TotalItemsWithSystemCleanupTag – Elemente, die mit dem Systembereinigungstag markiert wurden</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die mit dem Systembereinigungstag versehen wurden. Enthalten sind auch die Postfach-Metadatenelemente, die für Benutzer nicht sichtbar sind.</p></td>
</tr>
<tr class="odd">
<td><p>TotalItemsExpiredByDefaultExpiryTag – Elemente, die aufgrund eines Standardablauftags abgelaufen sind</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die vom Assistenten für verwaltete Ordner aufgrund eines nicht persönlichen Tags (Standard- oder Systemtag) in einer Aufbewahrungsrichtlinie als abgelaufen erkannt wurden (und vorläufig oder dauerhaft gelöscht wurden).</p>
<p>Nicht enthalten sind die Elemente, die infolge der Bereinigung der wiederherstellbaren Elemente oder der Systembereinigung als abgelaufen erkannt wurden.</p></td>
</tr>
<tr class="even">
<td><p>TotalItemsExpiredByPersonalExpiryTag – Elemente, die aufgrund eines persönlichen Ablauftags abgelaufen sind</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die vom Assistenten für verwaltete Ordner aufgrund eines persönlichen Tags in der Aufbewahrungsrichtlinie als abgelaufen erkannt wurden (und vorläufig oder dauerhaft gelöscht wurden).</p></td>
</tr>
<tr class="odd">
<td><p>TotalItemsMovedByDefaultArchiveTag – Elemente, die aufgrund eines Standardarchivtags verschoben wurden</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die vom Assistenten für verwaltete Ordner aufgrund eines nicht persönlichen Archivtags (Standard- oder Systemarchivtag) in einer Aufbewahrungsrichtlinie in das Archiv verschoben wurden.</p>
<p>Nicht enthalten sind die Elemente, die durch eine Bereinigung der wiederherstellbaren Elemente in den Archivordner &quot;Wiederherstellbare Elemente&quot; verschoben wurden.</p></td>
</tr>
<tr class="even">
<td><p>TotalItemsMovedByPersonalArchiveTag – Elemente, die aufgrund eines Archivtags verschoben wurden</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die vom Assistenten für verwaltete Ordner aufgrund eines persönlichen Archivtags in einer Aufbewahrungsrichtlinie in das Archiv verschoben wurden.</p></td>
</tr>
<tr class="odd">
<td><p>TotalMovedDumpsterItems – Postfachdumpster: Verschobene Elemente</p></td>
<td><p>MSExchange-Assistent für verwaltete Ordner</p></td>
<td><p>Gibt die Anzahl der Elemente an, die durch eine Bereinigung der wiederherstellbaren Elemente in den Archivordner &quot;Wiederherstellbare Elemente&quot; verschoben wurden.</p></td>
</tr>
</tbody>
</table>

