---
title: 'Nachrichtenfilter: Exchange 2013 Help'
TOCTitle: Nachrichtenfilter
ms:assetid: 8e6187c1-76f0-49da-bc24-2ab57cfb3c2c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123714(v=EXCHG.150)
ms:contentKeyID: 50476148
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Nachrichtenfilter

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Durch Filtern werden verschiedene Ansichten der Nachrichten in Warteschlangen generiert. Durch Angeben von Filterkriterien können Nachrichten schnell gefunden und entsprechende Aktionen für sie eingeleitet werden. Wenn eine E-Mail-Nachricht an mehrere Empfänger gesendet wird, kann sie sich in mehreren Warteschlangen befinden. Beim Filtern nach Nachrichteneigenschaften können Nachrichten in allen Warteschlangen gefunden werden. Die folgenden Szenarien stellen Beispiele für die Verwendung der Nachrichtenfilterung zum Verwalten der Nachrichtenübermittlung dar:

  - Die Übermittlungswarteschlange auf dem Postfach- oder Edge-Transport-Server, in die E-Mail aus dem Internet eingeht, enthält sehr viele Nachricht, die zur Zustellung in die Warteschlange gestellt wurden. Viele dieser Nachrichten besitzen den gleichen Betreff. Daher haben Sie den Verdacht, dass Spam an Ihre Organisation gesendet wird. Sie können einen Filter zum Anzeigen aller Nachrichten erstellen, die dem Betreffkriterium entsprechen. Wenn Sie feststellen, dass es sich bei den Nachrichten um Spam handelt, können Sie alle auswählen und sie aus der Zustellungswarteschlange löschen, ohne einen Unzustellbarkeitsbericht (NDR) zu senden.

  - Ein Benutzer meldet, dass die Nachrichtenübermittlung langsam ist. Sie untersuchen die Warteschlangen und stellen fest, dass viele Nachrichten einen zufällig erscheinenden Betreff aufweisen und aus einer einzigen Domäne stammen. Sie können einen Filter erstellen, um alle in den Warteschlangen vorhandenen Nachrichten aus der betreffenden Domäne anzuzeigen. Wenn Sie feststellen, dass es sich bei den Nachrichten um Spam handelt, können Sie alle auswählen und sie aus den Warteschlangen löschen, ohne einen Unzustellbarkeitsbericht (NDR) zu senden.

## Nachrichteneigenschaften als Filter

Anhand von Nachrichteneigenschaften können Sie einen Filter erstellen und Nachrichten finden, die den angegebenen Kriterien entsprechen. Sie können Filter in der Warteschlangenanzeige oder mithilfe des Parameters *Filter* für Cmdlets zur Nachrichtenverwaltung erstellen. Die Cmdlets zur Nachrichtenverwaltung unterstützen mehr filterbare Optionen als die Warteschlangenanzeige. In der folgenden Tabelle sind die Nachrichteneigenschaften, nach denen gefiltert werden kann, und die ihnen zugeordneten Werte aufgelistet.

### Nachrichteneigenschaften zum Filtern von Nachrichten

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nachrichteneigenschaft in der Warteschlangenanzeige</th>
<th>Nachrichteneigenschaft in der Shell</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Empfangsdatum</strong></p></td>
<td><p><code>DateReceived</code></p></td>
<td><p>Datum/Uhrzeit, an dem/zu der die Nachricht in die Warteschlange gestellt wurde.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>DeferReason</code></p></td>
<td><p>Diese Eigenschaft kennzeichnet, warum die Nachricht zurückgestellt wurde. Wenn die Nachricht nicht zurückgestellt war, hat diese Eigenschaft den Wert <code>None</code>. Eine zurückgestellte Nachricht wird an die Übermittlungswarteschlange aufgrund zeitweiliger Fehler zurückgegeben, die während der Empfängerauflösung aufgetreten sind. Weitere Informationen zu zurückgestellten Nachrichten finden Sie unter <a href="recipient-resolution-exchange-2013-help.md">Empfängerauflösung</a>. Die folgenden Werte sind möglich:</p>
<p><code>AD Transient Failure During Content Conversion</code></p>
<p><code>AD Transient Failure During Resolve</code></p>
<p><code>Agent</code></p>
<p><code>Ambiguous Recipient</code></p>
<p><code>Loop Detected</code></p>
<p><code>Marked As Retry Delivery If Rejected</code></p>
<p><code>Rerouted By Store Driver</code></p>
<p><code>Storage Transient Failure During Content Conversion</code></p>
<p><code>Transient Failure</code></p>
<p><code>Target Site Inbound Mail Disabled</code></p>
<p><code>Recipient Thread Limit Exceeded</code></p>
<p><code>Transient Attribution Failure</code></p>
<p><code>Transient Accepted Domains Load Failure</code></p></td>
</tr>
<tr class="odd">
<td><p><strong>Ablaufzeit</strong></p></td>
<td><p><code>ExpirationTime</code></p></td>
<td><p>Diese Eigenschaft enthält das Datum und die Uhrzeit, zu der die Nachricht abläuft und aus der Warteschlange gelöscht wird, falls sie nicht zugestellt werden kann.</p></td>
</tr>
<tr class="even">
<td><p><strong>Von Adresse</strong></p></td>
<td><p><code>FromAddress</code></p></td>
<td><p>Diese Eigenschaft enthält die SMTP-Adresse des Absenders.</p></td>
</tr>
<tr class="odd">
<td><p>N/V</p></td>
<td><p><code>Identity</code></p></td>
<td><p>Diese Eigenschaft bestimmt die ID der Nachricht in Form von <em>&lt;Server&gt;\&lt;Warteschlange&gt;\&lt;Nachrichtenganzzahl&gt;</em>. Weitere Informationen finden Sie im Abschnitt &quot;Nachrichtenidentität&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Internetnachrichten-ID</strong></p></td>
<td><p><code>InternetMessageId</code></p></td>
<td><p>Diese Eigenschaft enthält den Wert des Nachrichtenkopffelds <code>Message-ID:</code>, das sich im Nachrichtenkopf befindet. Der Wert wird als E-Mail-Adresse ausgedrückt, die eine GUID und den FQDN des absendenden SMTP-Servers enthält. Beispiel:</p>
<p><code>&lt;67D754D6103DC4FB3BA6BC7205DACABA61231@mailbox01.contoso.com&gt;</code></p></td>
</tr>
<tr class="odd">
<td><p><strong>Letzter Fehler</strong></p></td>
<td><p><code>LastError</code></p></td>
<td><p>Diese Eigenschaft enthält den Text des letzten für eine Nachricht aufgezeichneten Fehlers. Beispiel: <code>A matching connector cannot be found to route the external recipient</code>.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>MessageLatency</code></p></td>
<td><p>Diese Eigenschaft enthält den Zeitraum, der nach dem ersten Eingang der Nachricht in die Übermittlungswarteschlange auf dem Server und dem Ablegen der Nachricht in der Warteschlange verstrichen ist. Der Wert hat die Syntax <em>hh:mm:ss.ff</em> (<em>hh</em> = Stunde, <em>mm</em> = Minute, <em>ss</em> = Sekunde und <em>ff</em> = Sekundenbruchteile).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Name der Nachrichtenquelle</strong></p></td>
<td><p><code>MessageSourceName</code></p></td>
<td><p>Diese Eigenschaft enthält eine Textzeichenfolge mit dem Namen der Transportkomponente, die diese Nachricht an die Warteschlange übermittelt hat. Wenn die Nachricht beispielsweise durch einen Empfangsconnector eingegangen ist, lautet der Wert: <code>SMTP:</code><em>&lt;Connectorname&gt;</em>. Wenn die Nachricht eine Benachrichtigung über den Zustellungsstatus, lautet der Wert <code>DSN</code>.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>Priority</code></p></td>
<td><p>Diese Eigenschaft enthält die Priorität der Nachricht, die vom Benutzer in Outlook oder Outlook Web App zugewiesen wird. Die gültigen Werte sind <code>Low</code>, <code>Normal</code> und <code>High</code>. Weitere Informationen finden Sie unter <a href="priority-queuing-exchange-2013-help.md">Prioritätswarteschlangen</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Warteschlangen-ID</strong></p></td>
<td><p><code>Queue</code></p></td>
<td><p>Diese Eigenschaft bestimmt die ID der Warteschlange, in der sich die Nachricht befindet. Für die Warteschlangen-ID wird die Syntax <em>&lt;Server&gt;\&lt;Warteschlange&gt;</em> verwendet. Weitere Informationen finden Sie im Abschnitt &quot;Warteschlangenidentität&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
</tr>
<tr class="even">
<td><p>N/V</p></td>
<td><p><code>RetryCount</code></p></td>
<td><p>Diese Eigenschaft bestimmt, wie oft die Zustellung der Nachricht an das Ziel versucht wurde, entweder automatisch oder manuell.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SCL (Spam Confidence Level)</strong></p></td>
<td><p><code>SCL</code></p></td>
<td><p>Der Wert der SCL-Eigenschaft (Spam Confidence Level) gibt den SCL der Nachricht an. Gültige SCL-Einträge sind die ganzen Zahlen von 0 bis 9. Ein leerer SCL-Eigenschaftswert zeigt an, dass die Nachricht nicht vom Inhaltsfilter-Agent verarbeitet wurde.</p>
<p>Diese Eigenschaft gibt die SCL-Bewertung (Spam Confidence Level) einer Nachricht an. Gültige SCL-Einträge sind ganze Zahlen von 0 bis 9 und -1. Weitere Informationen finden Sie unter <a href="spam-confidence-level-threshold-exchange-2013-help.md">SCL-Schwellenwert</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Größe (KB)</strong></p></td>
<td><p><code>Size</code></p></td>
<td><p>Diese Eigenschaft gibt die Größe der Nachricht an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Quell-IP</strong></p></td>
<td><p><code>SourceIP</code></p></td>
<td><p>Diese Eigenschaft enthält die IP-Adresse des Servers, der die Nachricht an den Exchange-Server übermittelt hat, dessen Warteschlange die Nachricht enthält. Die Adresse kann die IP-Adresse eines SMTP-Remoteservers oder des lokalen Exchange-Servers sein.</p></td>
</tr>
<tr class="even">
<td><p><strong>Status</strong></p></td>
<td><p><code>Status</code></p></td>
<td><p>Diese Eigenschaft gibt den aktuellen Nachrichtenstatus an. Eine Nachricht kann einen der folgenden Statuswerte aufweisen:</p>
<p><code>Active</code></p>
<p><code>Locked</code></p>
<p><code>None</code></p>
<p><code>Pending Remove</code></p>
<p><code>Pending Suspend</code></p>
<p><code>Ready</code></p>
<p><code>Retry</code></p>
<p><code>Suspended</code></p>
<p>Weitere Informationen finden Sie im Abschnitt &quot;Nachrichteneigenschaften&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Subject</strong></p></td>
<td><p><code>Subject</code></p></td>
<td><p>Diese Eigenschaft gibt den Betreff der Nachricht im Kopffeld <code>Subject:</code> an, das sich im Nachrichtenkopf befindet.</p></td>
</tr>
</tbody>
</table>

