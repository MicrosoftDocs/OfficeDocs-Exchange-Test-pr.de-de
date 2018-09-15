---
title: 'Berechnung von Aufbewahrungszeiträumen: Exchange 2013 Help'
TOCTitle: Berechnung von Aufbewahrungszeiträumen
ms:assetid: a7daf7aa-0411-4b26-a422-eefd1b113f9f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb430780(v=EXCHG.150)
ms:contentKeyID: 50476400
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechnung von Aufbewahrungszeiträumen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-07-27_

Der Assistent für verwaltete Ordner ist einer von zahlreichen Prozessen vom Typ *Postfach-Assistent*, der auf Postfachservern ausgeführt wird. Seine Aufgabe besteht darin, Postfächer mit einer Aufbewahrungsrichtlinie zu verarbeiten, in der Richtlinie enthaltene Aufbewahrungstags auf das Postfach anzuwenden und die Elemente im Postfach zu verarbeiten. Wenn die Elemente ein Aufbewahrungstag aufweisen, prüft der Assistent das Alter dieser Elemente. Wenn das *Aufbewahrungslimit* eines Elements überschritten wurde, wird die entsprechende *Aufbewahrungsaktion* gestartet. Zu den Aufbewahrungsaktionen zählt das Verschieben von Elementen in das Archiv eines Benutzers, das Löschen von Elementen und Zulassen der Wiederherstellung oder das dauerhafte Löschen von Elementen.

Weitere Informationen finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](https://technet.microsoft.com/de-de/library/Dd297955(v=EXCHG.150)).

## Ermitteln des Alters von unterschiedlichen Elementtypen

Das Aufbewahrungslimit für Postfachelemente wird ab dem Datum der Zustellung oder dem Datum der Erstellung für Elemente berechnet, wie beispielsweise Entwürfe, die vom Benutzer erstellt, aber nicht zugestellt wurden. Wenn der Assistent für verwaltete Ordner Elemente in einem Postfach verarbeitet, werden alle Elemente, die Aufbewahrungstags mit der Aufbewahrungsaktion **Löschen und Wiederherstellung zulassen** oder **Endgültig löschen** aufweisen, mit einem Start- und einem Ablaufdatum gestempelt. Elemente, die ein Archivierungstag aufweisen, werden ebenfalls mit einem Verschiebungsdatum gestempelt.

Elemente im Ordner "Gelöschte Elemente" und Elemente mit einem Start- und Enddatum, wie beispielsweise Kalenderelemente (Besprechungen und Termine) und Aufgaben, werden anders behandelt (siehe Angaben in dieser Tabelle).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Typ</th>
<th>Element</th>
<th>Das Aufbewahrungslimit wird auf folgender Grundlage berechnet....</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>E-Mail</p></li>
<li><p>Dokument</p></li>
<li><p>Fax-</p></li>
<li><p>Journalelement</p></li>
<li><p>Besprechungsanfrage, -antwort oder -absage</p></li>
<li><p>Verpasster Anruf</p></li>
</ul></td>
<td><p>Nicht im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><p>Zustellungsdatum oder Erstellungsdatum</p></td>
</tr>
<tr class="even">
<td><ul>
<li><p>E-Mail</p></li>
<li><p>Dokument</p></li>
<li><p>Fax-</p></li>
<li><p>Journalelement</p></li>
<li><p>Besprechungsanfrage, -antwort oder -absage</p></li>
<li><p>Verpasster Anruf</p></li>
</ul></td>
<td><p>Im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><ul>
<li><p>Zustellungs- oder Erstellungsdatum, es sei denn, das Element wurde aus einem Ordner gelöscht, der weder ein geerbtes noch ein implizites Aufbewahrungstag aufweist.</p></li>
<li><p>Wenn sich ein Element in einem Ordner befindet, auf den ein geerbtes oder ein implizites Aufbewahrungstag angewendet wird, wird das Element vom Assistenten für verwaltete Ordner nicht verarbeitet und verfügt daher nicht über ein vom Assistenten gestempeltes Startdatum. Wenn der Benutzer ein solches Element löscht und der Assistent für verwaltete Ordner das Element zum ersten Mal im Ordner &quot;Gelöschte Elemente&quot; verarbeitet, kennzeichnet er das aktuelle Datum als Startdatum.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Kalender</p></td>
<td><p>Nicht im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><ul>
<li><p>Nicht-Kalenderserienelemente laufen entsprechend ihrem Enddatum ab.</p></li>
<li><p>Kalenderserienelemente laufen entsprechend dem Enddatum ihres letzten Auftretens ab. Kalenderserienelemente ohne Enddatum laufen niemals ab.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Kalender</p></td>
<td><p>Im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><ol>
<li><p>Ein Kalenderelement läuft entsprechend dem Wert des Parameters <code>message-received date</code> ab, sofern vorhanden.</p></li>
<li><p>Wenn der Parameter <code>message-received date</code> für ein Kalenderelement nicht angegeben wurde, läuft es entsprechend dem Wert des Parameters <code>message-creation date</code> ab.</p></li>
<li><p>Wenn für ein Kalenderelement weder der Parameter <code>message-received date</code> noch der Parameter <code>message-creation date</code> festgelegt wurde, läuft es nie ab.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Task</p></td>
<td><p>Nicht im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><ul>
<li><p>Nicht wiederkehrende Aufgaben:</p>
<ol>
<li><p>Eine nicht wiederkehrende Aufgabe läuft entsprechend dem Wert des Parameters <code>message-received date</code> ab, sofern vorhanden.</p></li>
<li><p>Wenn der Parameter <code>message-received date</code> für eine nicht wiederkehrende Aufgabe nicht angegeben wurde, läuft sie entsprechend dem Wert des Parameters <code>message-creation date</code> ab.</p></li>
<li><p>Wenn für eine nicht wiederkehrende Aufgabe weder der Parameter <code>message-received date</code> noch der Parameter <code>message-creation date</code> festgelegt wurde, läuft sie nie ab.</p></li>
</ol></li>
<li><p>Eine wiederkehrende Aufgabe (Aufgabenserie) läuft entsprechend dem Wert des Parameters <code>end date</code> des letzten Auftretens ab. Wenn für eine Aufgabenserie kein <code>end date</code> festgelegt wurde, läuft sie nie ab.</p></li>
<li><p>Eine Aufgabe, die erneut generiert wird (d. h. eine Aufgabenserie, die zu einem bestimmten Zeitpunkt nach Abschluss der vorherigen Instanz der Aufgabenserie erneut generiert wird), läuft nie ab.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Task</p></td>
<td><p>Im Ordner &quot;Gelöschte Elemente&quot;</p></td>
<td><ol>
<li><p>Eine Aufgabe läuft entsprechend dem Wert des Parameters <code>message-received date</code> ab, sofern vorhanden.</p></li>
<li><p>Wenn der Parameter <code>message-received date</code> für eine Aufgabe nicht angegeben wurde, läuft sie entsprechend dem Wert des Parameters <code>message-creation date</code> ab.</p></li>
<li><p>Wenn für eine Aufgabe weder der Parameter <code>message-received date</code> noch der Parameter <code>message-creation date</code> festgelegt wurde, läuft sie nie ab.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Kontakt</p></td>
<td><p>In allen Ordnern</p></td>
<td><p>Kontakte werden nicht mit einem Start- oder Ablaufdatum gestempelt. Sie werden vom Assistenten für verwaltete Ordner übersprungen und laufen nicht ab.</p></td>
</tr>
<tr class="even">
<td><p>Beschädigt</p></td>
<td><p>In allen Ordnern</p></td>
<td><p>Beschädigte Elemente werden vom Assistenten für verwaltete Ordner übersprungen und laufen nicht ab.</p></td>
</tr>
</tbody>
</table>


## Beispiele


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Der Benutzer...</th>
<th>Die Aufbewahrungstags für den Ordner...</th>
<th>Der Assistent für verwaltete Ordner...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Empfängt eine Nachricht im Posteingang am 26.01.2013.</p></li>
<li><p>Löscht die Nachricht am 27.02.2013.</p></li>
</ol>
<p></p></td>
<td><ul>
<li><p>Posteingang: Löschen in 365 Tagen</p></li>
<li><p>Gelöschte Elemente: Löschen in 30 Tagen</p></li>
</ul>
<p></p></td>
<td><ol>
<li><p>Verarbeitet die Nachricht im Posteingang am 26.01.2013, stempelt sie mit dem <em>Startdatum</em> 26.01.2013 und dem <em>Ablaufdatum</em> 26.01.2014.</p></li>
<li><p>Verarbeitet die Nachricht erneut im Ordner &quot;Gelöschte Elemente&quot; am 27.02.2013. Berechnet das Ablaufdatum basierend dem gleichen Startdatum (26.01.2013).</p></li>
<li><p>Da das Element älter als 30 Tage ist, läuft es sofort ab.</p></li>
</ol></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Empfängt eine Nachricht im Posteingang am 26.01.2013.</p></li>
<li><p>Löscht die Nachricht am 27.02.2013.</p></li>
</ol></td>
<td><ul>
<li><p>Posteingang: Keine (geerbt oder implizit)</p></li>
<li><p>Gelöschte Elemente: Löschen in 30 Tagen</p></li>
</ul></td>
<td><ol>
<li><p>Verarbeitet die Nachricht im Ordner &quot;Gelöschte Elemente&quot; am 27.02.2013 und ermittelt, dass das Element kein Startdatum hat. Das Element wird mit dem aktuellen Datum als Startdatum und &quot;27.03.2013&quot; als Ablaufdatum gekennzeichnet.</p></li>
<li><p>Das Element läuft am 27.03.2013 ab, d. h. 30 Tage, nachdem es vom Benutzer gelöscht oder in den Ordner &quot;Gelöschte Elemente&quot; verschoben wurde.</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Weitere Informationen

  - In Exchange Online verarbeitet der Assistent für verwaltete Ordner ein Postfach einmal in sieben Tagen. Dies kann dazu führen, dass Elemente maximal sieben Tage nach dem Ablaufdatum ablaufen, mit dem das Element gekennzeichnet wurde.

  - Elemente, für die das Anhalten der Aufbewahrungszeit aktiviert ist, werden erst vom Assistenten für verwaltete Postfächer verarbeitet, wenn das Anhalten der Aufbewahrungszeit aufgehoben wurde.

  - Wenn für ein Postfach das Compliance-Archiv oder das Beweissicherungsverfahren aktiviert ist, werden ablaufende Elemente aus dem Posteingang entfernt, aber so lange im Ordner "Wiederherstellbare Elemente" aufbewahrt, bis das Postfach aus dem [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md) entfernt wurde.

  - In Hybridbereitstellungen müssen die gleichen Aufbewahrungstags und Aufbewahrungsrichtlinien in Ihren lokalen Organisationen und Exchange Online-Organisationen vorhanden sein, damit Elemente zwischen beiden Organisationen konsistent verschoben werden und ablaufen können. Weitere Informationen finden Sie unter [Exportieren und Importieren von Aufbewahrungstags](export-and-import-retention-tags-exchange-2013-help.md).

