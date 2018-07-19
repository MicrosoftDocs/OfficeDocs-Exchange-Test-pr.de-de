---
title: 'Warteschlangenfilter: Exchange 2013 Help'
TOCTitle: Warteschlangenfilter
ms:assetid: fbfbdcab-e0d2-4ed9-8f7f-e5fa2c87360d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125237(v=EXCHG.150)
ms:contentKeyID: 50477134
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Warteschlangenfilter

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Durch die Filterung werden unterschiedliche Ansichten von Warteschlangen generiert. Sie können die Warteschlangeneigenschaften als Filteroptionen verwenden. Durch die Angabe von Filterkriterien können Sie Warteschlangen schnell finden und Aktionen darauf anwenden. Die folgenden Szenarien stellen Beispiele für die Verwendung der Warteschlangenfilterung zum Verwalten der Nachrichtenübermittlung dar:

  - Sie von Microsoft System Center Operations Manager darüber benachrichtigt, dass die Länge einer Warteschlange den festgelegten Grenzwert überschritten hat. Sie möchten herausfinden, ob ein serverweites Nachrichtenübermittlungsproblem vorliegt.
    
    Sie können einen Filter erstellen, um alle Warteschlangen mit einer Nachrichtenanzahl anzuzeigen, die das normale Maß überschreitet. Liegt ein Problem bei der Nachrichtenübermittlung vor, können Sie alle Warteschlangen in den Filterergebnissen auswählen und anhalten, während Sie Ihre Untersuchung fortsetzen.

  - Sie halten mehrere Warteschlangen an, um die Ursache von Nachrichtenübermittlungsproblemen zu ermitteln. Sie stellen fest, dass das Problem von einer nicht ordnungsgemäßen Connectorkonfiguration verursacht wurde und nun behoben ist.
    
    Sie können einen Filter erstellen, um alle Warteschlangen mit dem Status Angehalten anzuzeigen, und anschließend alle Warteschlangen in den Filterergebnissen auswählen und wieder aktivieren.

## Beim Filtern von Warteschlangen zu verwendende Warteschlangeneigenschaften

Mithilfe der Warteschlangeneigenschaften können Sie einen Filter erstellen und Warteschlangen ermitteln, welche die angegebenen Kriterien erfüllen. Sie können Filter in der Warteschlangenanzeige oder in Warteschlangenverwaltungs-Cmdlets mit dem Parameter *Filter* erstellen. Beachten Sie, dass von Warteschlangenverwaltungs-Cmdlets mehr filterbare Eigenschaften unterstützt werden als von der Warteschlangenanzeige. Die folgende Tabelle enthält die Warteschlangeneigenschaften, nach denen Sie filtern können, sowie die gültigen Werte dieser Eigenschaften.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Warteschlangeneigenschaft in der Warteschlangenanzeige</th>
<th>Warteschlangeneigenschaft in der Shell</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>DeferredMessageCount</code></p></td>
<td><p>Diese Eigenschaft gibt die Anzahl von Nachrichten an, die aufgrund von vorübergehenden Fehlern, die während der Empfängerauflösung aufgetreten sind, an die Übermittlungswarteschlange zurückgegeben wurden. Weitere Informationen zu zurückgestellten Nachrichten finden Sie unter <a href="recipient-resolution-exchange-2013-help.md">Empfängerauflösung</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Zustellungstyp</strong></p></td>
<td><p><code>DeliveryType</code></p></td>
<td><p>Die gültigen Werte für <strong>DeliveryType</strong> werden im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;NextHopSolutionKey&quot; erläutert.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>Identity</code></p></td>
<td><p>Diese Eigenschaft gibt die Identität der Warteschlange im Format <em>&lt;Server&gt;\&lt;Warteschlange&gt;</em> an. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;Warteschlangenidentität&quot;.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>IncomingRate</code></p></td>
<td><p>Diese Eigenschaft entspricht einem berechneten Wert, der die Geschwindigkeit angibt, mit der Nachrichten bei der Warteschlange eingehen. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;IncomingRate, OutgoingRate und Velocity&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Letzter Fehler</strong></p></td>
<td><p><code>LastError</code></p></td>
<td><p>Diese Eigenschaft gibt die Textzeichenfolge des letzten für die Warteschlange aufgezeichneten Fehlers an.</p></td>
</tr>
<tr class="even">
<td><p><strong>Zeitpunkt der letzten Wiederholung</strong></p></td>
<td><p><code>LastRetryTime</code></p></td>
<td><p>Diese Eigenschaft gibt Datum und Uhrzeit des letzen Verbindungsversuchs für eine Warteschlange mit dem Status <code>Retry</code> an.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>LockedMessageCount</code></p></td>
<td><p>Diese Eigenschaft ist für die interne Verwendung durch Microsoft reserviert und wird nicht in lokalen Exchange 2013-Organisationen verwendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>Anzahl Nachrichten</strong></p></td>
<td><p><code>MessageCount</code></p></td>
<td><p>Diese Eigenschaft gibt die Anzahl der Nachrichten in der Warteschlange an.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>NextHopCategory</code></p></td>
<td><p>Mit dieser Eigenschaft wird der nächste Hop der Warteschlangen als <code>Internal</code> oder <code>External</code> gekennzeichnet. Sie basiert auf dem Wert der <strong>DeliveryType</strong>-Eigenschaft der Warteschlange. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;NextHopSolutionKey&quot;.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>NextHopConnector</code></p></td>
<td><p>Diese Eigenschaft gibt die GUID des nächsten Hops an und basiert auf dem Wert der <strong>DeliveryType</strong>-Eigenschaft der Warteschlange. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;NextHopSolutionKey&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nächste Hopdomäne</strong></p></td>
<td><p><code>NextHopDomain</code></p></td>
<td><p>Diese Eigenschaft gibt den Namen des nächsten Hops an und basiert auf dem Wert der <strong>DeliveryType</strong>-Eigenschaft der Warteschlange. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;NextHopSolutionKey&quot;.</p></td>
</tr>
<tr class="even">
<td><p><strong>Zeitpunkt der nächsten Wiederholung</strong></p></td>
<td><p><code>NextRetryTime</code></p></td>
<td><p>Diese Eigenschaft gibt Datum und Uhrzeit des nächsten Verbindungsversuchs für eine Warteschlange mit dem Status <code>Retry</code> an.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>OutgoingRate</code></p></td>
<td><p>Diese Eigenschaft entspricht einem berechneten Wert, der die Geschwindigkeit angibt, mit der Nachrichten die Warteschlange verlassen. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;IncomingRate, OutgoingRate und Velocity&quot;.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>RiskLevel</code></p></td>
<td><p>Diese Eigenschaft ist für die interne Verwendung durch Microsoft reserviert und wird nicht in lokalen Exchange 2013-Organisationen verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Status</strong></p></td>
<td><p><code>Status</code></p></td>
<td><p>Diese Eigenschaft gibt den aktuellen Warteschlangenstatus an. Eine Warteschlange kann einen der folgenden Statuswerte aufweisen: &quot;Aktiv&quot;, &quot;Verbindung wird hergestellt&quot;, &quot;Kein&quot;, &quot;Angehalten&quot;, &quot;Bereit&quot; oder &quot;Wiederholen&quot;. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;Warteschlangenstatus&quot;.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>TlsDomain</code></p></td>
<td><p>Diese Eigenschaft enthält den FQDN der Zieldomäne, sofern die Domäne für Domänensicherheit konfiguriert ist.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>Velocity</code></p></td>
<td><p>Diese Eigenschaft enthält einen berechneten Wert, der angibt, wie effektiv die Warteschlange entleert wird. Weitere Informationen finden Sie im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> unter &quot;IncomingRate, OutgoingRate und Velocity&quot;.</p></td>
</tr>
</tbody>
</table>

