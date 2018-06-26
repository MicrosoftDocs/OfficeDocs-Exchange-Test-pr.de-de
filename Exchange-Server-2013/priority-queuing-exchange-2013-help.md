---
title: 'Prioritätswarteschlangen: Exchange 2013 Help'
TOCTitle: Prioritätswarteschlangen
ms:assetid: 6edbd826-fe55-435b-9c63-48e6365c3d09
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691107(v=EXCHG.150)
ms:contentKeyID: 51409312
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prioritätswarteschlangen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Bei der *Prioritätswarteschlange* handelt es sich um eine Funktion von Microsoft Exchange Server 2013, durch die die vom Absender definierte Priorität einer Nachricht Einfluss auf deren Verarbeitung durch den Transportdienst auf dem Postfachserver hat.

Die Nachrichtenpriorität wird vom Absender in Microsoft Outlook beim Erstellen und Senden der Nachricht zugewiesen. Der Absender kann die folgenden Werte für die Nachrichtenpriorität in Outlook festlegen:

  - Wichtigkeit "Niedrig"

  - Wichtigkeit "Normal"

  - Wichtigkeit "Hoch"

Die Standardpriorität für eine in Outlook oder Outlook Web App erstellte Nachricht ist "Normal". Die Priorität der Nachricht wird im Kopfzeilenfeld `X-Priority` des Nachrichtenkopfs gespeichert.

Jede Nachricht, die in einer Exchange 2013-Organisation gesendet oder empfangen wird, muss vom Transportdienst auf einem Postfachserver kategorisiert werden, bevor sie weitergeleitet und zugestellt werden kann. Das Kategorisierungsmodul im Transportdienst auf einem Postfachserver ruft jeweils eine Nachricht aus der Übermittlungswarteschlange ab und führt eine Empfängerauflösung, eine Routingauflösung und eine Inhaltskonvertierung für die Nachricht durch, bevor diese in eine Zustellungswarteschlange eingestellt wird. Weitere Informationen finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).

Zustellungswarteschlangen werden je nach dem Ziel einer Nachricht dynamisch erstellt. Weitere Informationen finden Sie unter [Warteschlangen](queues-exchange-2013-help.md).

Alle Nachrichten mit demselben Ziel werden in dieselbe Zustellungswarteschlange eingestellt. Prioritätswarteschlangen wirken sich auf die Übermittlung von Nachrichten aus einer Zustellungswarteschlange an den Messagingzielserver aus. Bei aktivierter Prioritätswarteschlange werden Nachrichten mit hoher Priorität vor Nachrichten mit normaler Priorität und Nachrichten mit normaler Priorität vor Nachrichten mit niedriger Priorität an das jeweilige Ziel übermittelt. Die priorisierte Zustellung von Nachrichten anhand der Nachrichtenpriorität kann bei der Definition bestimmter Anforderungen an Vereinbarungen zum Servicelevel hinsichtlich der Zustellungszeiten hilfreich sein.

## Optionen zum Konfigurieren von Prioritätswarteschlangen

Die Unterstützung für Prioritätswarteschlangen wird von Schlüsseln in der XML-Anwendungskonfigurationsdatei `%ExchangeInstallPath%bin\EdgeTransport.exe.config` bestimmt. Anweisungen zum Konfigurieren der Prioritätswarteschlange finden Sie unter [Aktivieren und Konfigurieren von Warteschlangen nach Priorität](enable-and-configure-priority-queuing-exchange-2013-help.md).

In der folgenden Tabelle werden die einzelnen Schlüssel ausführlicher beschrieben.

### Prioritätswarteschlangenschlüssel in der Datei "EdgeTransport.exe.config"

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Schlüssel</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>PriorityQueuingEnabled</em></p></td>
<td><p><code>false</code></p></td>
<td><p>Dieser Schlüssel aktiviert oder deaktiviert die Prioritätswarteschlange im Transportdienst auf dem Postfachserver. Gültige Eingaben für diesen Schlüssel sind <code>true</code> oder <code>false</code>.</p>
<p>Wenn dieser Schlüssel auf <code>false</code> festgelegt ist, wird die Prioritätswarteschlange deaktiviert, und alle Nachrichtenbeschränkungen für Prioritätswarteschlangen in der Datei &quot;EdgeTransport.exe.config&quot; werden ignoriert.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxHighPriorityMessageSize</em></p></td>
<td><p><code>250KB</code></p></td>
<td><p>Dieser Schlüssel gibt die maximal zulässige Größe einer Nachricht mit hoher Priorität an. Ist eine Nachricht mit hoher Priorität größer als der Wert dieses Schlüssels, wird die Nachricht automatisch von einer Nachricht mit hoher Priorität zu einer Nachricht mit normaler Priorität herabgestuft.</p>
<p>Der Wert dieses Schlüssels sollte deutlich unter dem Wert des Parameters <em>MaxSendMessageSize</em> im Cmdlet <strong>Set-TransportConfig</strong> liegen. Der Standardwert für diesen Parameter ist <code>10 MB</code>. Die Differenz bei diesen beiden Werten trägt zu gleichmäßigeren und berechenbareren Zustellungszeiten für Nachrichten mit hoher Priorität bei.</p>
<p>Wenn Sie einen Wert eingeben, qualifizieren Sie den Wert mit einer der folgenden Einheiten:</p>
<ul>
<li><p>KB (Kilobytes)</p></li>
<li><p>MB (Megabytes)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><em>LowPriorityDelayNotificationTimeout</em></p>
<p><em>NormalPriorityDelayNotificationTimeout</em></p>
<p><em>HighPriorityDelayNotificationTimeout</em></p></td>
<td><p><strong>Niedrig</strong> <code>8:00:00</code> (8 Stunden)</p>
<p><strong>Normal</strong> <code>4:00:00</code> (4 Stunden)</p>
<p><strong>Hoch</strong> <code>00:30:00</code> (30 Minuten)</p></td>
<td><p>Diese Schlüssel geben das Zeitüberschreitungsintervall für Benachrichtigungen über den Zustellungsstatus basierend auf der Nachrichtenpriorität an.</p>
<p>Jedes Mal, wenn eine Nachricht nicht zugestellt werden kann, generiert der Transportdienst eine Verzögerungsmeldung in Form einer Benachrichtigung über den Zustellungsstatus und legt diese zur Übermittlung an den Absender in der Warteschlange für unzustellbare Nachrichten ab. Diese DSN-Verzögerungsmeldung wird erst nach Ablauf des Timeoutintervalls für Verzögerungsbenachrichtigungen gesendet, und auch nur, wenn die Nachricht in dieser Zeit nicht übermittelt werden konnte. Diese Verzögerung verhindert, dass durch temporäre Nachrichtenübermittlungsfehler verursachte DSN-Verzögerungsmeldungen unnötigerweise gesendet werden.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p></td>
</tr>
<tr class="even">
<td><p><em>LowPriorityMessageExpirationTimeout</em></p>
<p><em>NormalPriorityMessageExpirationTimeout</em></p>
<p><em>HighPriorityMessageExpirationTimeout</em></p></td>
<td><p><strong>Niedrig</strong> <code>2.00:00:00</code> (2 Tage)</p>
<p><strong>Normal</strong> <code>2.00:00:00</code> (2 Tage)</p>
<p><strong>Hoch</strong> <code>8:00:00</code> (8 Stunden)</p></td>
<td><p>Diese Schlüssel geben die Höchstdauer an, die der Transportdienst versucht, eine nicht zugestellte Nachricht zuzustellen. Wenn die Nachricht nicht vor Ablauf des Timeoutintervalls erfolgreich zugestellt werden kann, erhält der Absender einen Unzustellbarkeitsbericht mit der ursprünglichen Nachricht oder dem Nachrichtenkopf.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxPerDomainLowPriorityConnections</em></p>
<p><em>MaxPerDomainNormalPriorityConnections</em></p>
<p><em>MaxPerDomainHighPriorityConnections</em></p></td>
<td><p><strong>Niedrig</strong>   2</p>
<p><strong>Normal</strong>   15</p>
<p><strong>Hoch</strong>   3</p></td>
<td><p>Diese Schlüssel geben die maximale Anzahl von Verbindungen an, die der Transportdienst mit einer beliebigen einzelnen Remotedomäne geöffnet haben darf. Die ausgehenden Verbindungen zu Remotedomänen entstehen bei Verwenden der Zustellungswarteschlangen und Sendeconnectors, die sich auf dem Postfachserver befinden.</p>
<p>Die Summe dieser drei Schlüssel sollte kleiner gleich dem Wert des Parameters <em>MaxPerDomainOutboundConnections</em> im Cmdlet <strong>Set-TransportService</strong> sein. Der Standardwert für diesen Parameter ist <code>20</code>.</p></td>
</tr>
</tbody>
</table>


## Auswirkungen der Prioritätswarteschlangen auf andere Nachrichtenbeschränkungen auf Postfachservern

Alle Nachrichten, die über den Transportdienst übermittelt werden, unterliegen verschiedenen Beschränkungen für die Wiederholung, die erneute Übermittlung und den Ablauf. Weitere Informationen finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

Bestimmte Nachrichtenbeschränkungen, die im Cmdlet **Set-TransportService** zur Verfügung stehen, weisen entsprechende Nachrichtenbeschränkungen für Prioritätswarteschlangen auf, die sich in der Konfigurationsdatei "EdgeTransport.exe.config" befinden. In der folgenden Tabelle werden die entsprechenden Nachrichtenbeschränkungen dargestellt.

### Nachrichtenbeschränkungen im Cmdlet "Set-TransportService", die den Nachrichtenbeschränkungen für Prioritätswarteschlangen in der Datei "EdgeTransport.exe.config" entsprechen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter oder Schlüssel</th>
<th>Standardwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p></td>
<td><p><em>DelayNotificationTimeOut</em></p></td>
<td><p><code>4:00:00</code> (4 Stunden)</p></td>
</tr>
<tr class="even">
<td><p>EdgeTransport.exe.config</p></td>
<td><p><em>NormalPriorityDelayNotificationTimeout</em></p></td>
<td><p><code>4:00:00</code> (4 Stunden)</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p></td>
<td><p><em>MessageExpirationTimeOut</em></p></td>
<td><p><code>2.00:00:00</code> (2 Tage)</p></td>
</tr>
<tr class="even">
<td><p>EdgeTransport.exe.config</p></td>
<td><p><em>NormalPriorityMessageExpirationTimeout</em></p></td>
<td><p><code>2.00:00:00</code> (2 Tage)</p></td>
</tr>
</tbody>
</table>


Bei deaktivierter Prioritätswarteschlange werden alle Nachrichtenbeschränkungen für Prioritätswarteschlangen in der Datei "EdgeTransport.exe.config" ignoriert. Die Nachrichtenbeschränkungen im Cmdlet **Set-TransportService** gelten für alle Nachrichten, die über den Transportdienst auf dem Postfachserver übermittelt werden.

Bei aktivierter Prioritätswarteschlange überschreiben die Nachrichtenbeschränkungen für Prioritätswarteschlangen in der Datei "EdgeTransport.exe.config" die entsprechenden Nachrichtenbeschränkungen im Cmdlet **Set-TransportService**. Alle weiteren Nachrichtenbeschränkungen im Cmdlet **Set-TransportService** gelten weiterhin für Nachrichten mit niedriger, normaler und hoher Priorität, die über den Transportdienst auf dem Postfachserver übermittelt werden.

## Benutzereinstellungen für Prioritätswarteschlangen

Das Cmdlet **Set-Mailbox** hat den Parameter *DowngradeHighPriorityMessagesEnabled*. Der Standardwert ist `$false`. Wenn dieser Parameter auf `$true` eingestellt wird, werden alle Nachrichten mit hoher Priorität, die aus dem Postfach gesendet werden, automatisch auf Nachrichten mit normaler Priorität herabgestuft.

