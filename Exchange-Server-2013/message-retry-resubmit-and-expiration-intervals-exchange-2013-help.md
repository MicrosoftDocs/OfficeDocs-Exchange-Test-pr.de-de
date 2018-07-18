---
title: 'Wiederholungsintervalle, Intervalle für die erneute Übermittlung und Ablaufintervalle für Nachrichten: Exchange 2013 Help'
TOCTitle: Wiederholungsintervalle, Intervalle für die erneute Übermittlung und Ablaufintervalle für Nachrichten
ms:assetid: 03020e6f-4c01-4c6e-ae47-fd74d4c4f96a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ891103(v=EXCHG.150)
ms:contentKeyID: 51409260
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederholungsintervalle, Intervalle für die erneute Übermittlung und Ablaufintervalle für Nachrichten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In Microsoft Exchange Server 2013 werden auf Nachrichten, die nicht erfolgreich zugestellt werden können, basierend auf der Quelle und dem Ziel der Nachricht verschiedene Fristen für die Wiederholung, die erneute Übermittlung und den Ablauf angewendet. *Wiederholen* bezeichnet einen erneuten Verbindungsversuch mit dem Ziel. *Erneut übermitteln* bezeichnet das Zurücksenden von Nachrichten an die Übermittlungswarteschlange, damit das Kategorisierungsmodul diese Nachrichten erneut verarbeitet. Die Nachricht wird als *abgelaufen* bezeichnet, nachdem alle Zustellungsversuche innerhalb eines bestimmten Zeitraums gescheitert sind. Wenn eine Nachricht abgelaufen ist, wird der Absender über den Zustellungsfehler informiert. Anschließend wird die Nachricht aus der Warteschlange gelöscht.

In allen drei Fällen (Wiederholen, erneutes Übermitteln und Ablauf) können Sie manuell eingreifen, bevor automatische Aktionen für die Nachrichten ausgeführt werden.

Anweisungen zur Konfiguration dieser Intervalle finden Sie unter [Konfigurieren von Wiederholungsintervallen, Intervallen für die erneute Übermittlung und Ablaufintervallen für Nachrichten](configure-message-retry-resubmit-and-expiration-intervals-exchange-2013-help.md).

## Konfigurationsoptionen für die Wiederholung von Nachrichten

Wenn ein Transportserver keine Verbindung mit dem nächsten Hop herstellen kann, wird die Warteschlange in den Status Wiederholen versetzt. Verbindungsversuche werden fortgesetzt, bis die Warteschlange abläuft oder eine Verbindung hergestellt wird.

## Konfigurationsoptionen für die automatische Wiederholung von Nachrichten

Die Konfigurationsoptionen, die für Wiederholungsintervalle für Nachrichten verfügbar sind, werden in der folgenden Tabelle beschrieben.

### Konfigurationsoptionen, die für Wiederholungsintervalle für Nachrichten verfügbar sind

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter- oder Schlüsselname</th>
<th>Standardwert</th>
<th>Konfigurationsort</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>QueueGlitchRetryCount</em></p></td>
<td><p>4</p></td>
<td><p>EdgeTransport.exe.config</p></td>
<td><p>Dieser Schlüssel gibt die Anzahl der Verbindungsversuche an, die sofort unternommen werden, wenn auf einem Transportserver Probleme beim Herstellen einer Verbindung mit dem Zielserver auftreten. Solche Verbindungsprobleme werden in der Regel durch sehr kurze Netzwerkausfälle verursacht.</p>
<p>Die gültige Eingabe für diesen Schlüssel ist eine ganze Zahl von 0 bis 15.</p>
<p>Normalerweise müssen Sie diesen Schlüssel nur ändern, wenn das Netzwerk unzuverlässig ist und weiterhin häufig Verbindungen unterbrochen werden.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueGlitchRetryInterval</em></p></td>
<td><p><code>00:01:00</code> oder 1 Minute</p></td>
<td><p>EdgeTransport.exe.config</p></td>
<td><p>Dieser Schlüssel steuert das Verbindungsintervall zwischen den einzelnen Verbindungsversuchen, die mit dem Schlüssel <em>QueueGlitchRetryCount</em> festgelegt werden.</p>
<p>Normalerweise müssen Sie diesen Parameter nur ändern, wenn das Netzwerk unzuverlässig ist und weiterhin häufig Verbindungen unterbrochen werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>TransientFailureRetryCount</em></p></td>
<td><p>6</p></td>
<td><p>Cmdlet <strong>Set-TransportService</strong> oder Servereigenschaften in der Exchange-Verwaltungskonsole</p></td>
<td><p>Dieser Parameter gibt die Anzahl der Verbindungsversuche an, die unternommen werden, nachdem die mit den Schlüsseln <em>QueueGlitchRetryCount</em> und <em>QueueGlitchRetryInterval</em> gesteuerten Verbindungsversuche keinen Erfolg hatten. Verbindungsprobleme, die die Schlüssel <em>QueueGlitchRetryCount</em> und <em>QueueGlitchRetryInterval</em> überschreiten, können durch Serverneustarts oder Fehler bei zwischengespeicherten DNS-Lookups verursacht werden.</p>
<p>Gültige Eingaben für diesen Parameter sind Ganzzahlen von 0 bis 15. Wenn Sie diesen Parameter auf 0 setzen, wird der nächste Verbindungsversuch durch den Parameter <em>OutboundConnectionFailureRetryInterval</em> gesteuert.</p></td>
</tr>
<tr class="even">
<td><p><em>TransientFailureRetryInterval</em></p></td>
<td><ul>
<li><p>Transportdienst auf Postfachservern: <code>00:05:00</code> oder 5 Minuten</p></li>
<li><p>Edge-Transport-Server: <code>00:01:00</code> oder 10 Minuten</p></li>
</ul></td>
<td><p>Cmdlet <strong>Set-TransportService</strong> oder Servereigenschaften in der Exchange-Verwaltungskonsole</p></td>
<td><p>Dieser Parameter steuert das Verbindungsintervall zwischen den einzelnen Verbindungsversuchen, die mit dem Parameter <em>TransientFailureRetryCount</em> festgelegt werden.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundConnectionFailureRetryInterval</em></p></td>
<td><ul>
<li><p>Transportdienst auf Postfachservern: <code>00:10:00</code> oder 10 Minuten</p></li>
<li><p>Edge-Transport-Server: <code>00:30:00</code> oder 30 Minuten</p></li>
</ul></td>
<td><p>Cmdlet <strong>Set-TransportService</strong> oder Servereigenschaften in der Exchange-Verwaltungskonsole</p></td>
<td><p>Dieser Parameter gibt das Wiederholungsintervall für ausgehende Verbindungsversuche an, die zuvor nicht erfolgreich waren. Die zuvor fehlgeschlagenen Verbindungsversuche werden von den Parametern <em>TransientFailureRetryCount</em> und <em>TransientFailureRetryInterval</em> gesteuert.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p></td>
</tr>
<tr class="even">
<td><p><em>MessageRetryInterval</em></p></td>
<td><p><code>00:15:00</code> oder 15 Minuten</p></td>
<td><p>Cmdlet <strong>Set-TransportService</strong></p></td>
<td><p>Dieser Parameter gibt das Wiederholungsintervall für einzelne Nachrichten an, die den Status Wiederholen aufweisen. Es wird empfohlen, den Standardwert nur zu ändern, wenn Sie vom Microsoft Customer Service and Support dazu aufgefordert werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>MailboxDeliveryQueueRetryInterval</em></p></td>
<td><p><code>00:05:00</code> oder 5 Minuten</p></td>
<td><p>EdgeTransport.exe.config</p></td>
<td><p>Dieser Schlüssel gibt an, wie häufig die Warteschlangen versuchen, eine Verbindung mit dem Postfachtransport-Zustellungsdienst für eine Zielpostfachdatenbank herzustellen, die nicht erreichbar ist.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p>
<p>Gültige Eingaben für diesen Schlüssel liegen zwischen 00:00:01 und 1.00:00:00.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Konfigurationsoptionen für die manuelle Wiederholung von Nachrichten

Wenn eine Zustellungswarteschlange den Status "Wiederholen" aufweist, können Sie mit der Warteschlangenanzeige in der Exchange-Toolbox oder mit dem Cmdlet **Retry-Queue** in der Shell einen sofortigen Verbindungsversuch manuell erzwingen. Der manuelle Wiederholungsversuch setzt den nächsten geplanten Wiederholungszeitpunkt außer Kraft. Kommt keine Verbindung zustande, wird der nächste Wiederholungszeitpunkt zurückgesetzt. Die Zustellungswarteschlange muss den Status Wiederholen aufweisen, damit diese Aktion wirksam ist.

Weitere Informationen finden Sie im Abschnitt "Wiederholen von Warteschlangen" unter [Verwalten von Warteschlangen](manage-queues-exchange-2013-help.md).

Zurück zum Seitenanfang

## Konfigurationsoptionen für DSN-Verzögerungsmeldungen

Jedes Mal, wenn eine Nachricht nicht zugestellt werden kann, generiert der Edge-Transport-Server bzw. der Transportdienst auf dem Postfachserver eine DSN-Verzögerungsmeldung (Delivery Status Notification, Benachrichtigung über den Übermittlungsstatus) und legt diese zur Zustellung an den Absender in der Warteschlange für unzustellbare Nachrichten ab. Diese DSN-Verzögerungsmeldung wird erst nach Ablauf des Timeoutintervalls für Verzögerungsbenachrichtigungen gesendet, und zwar nur dann, wenn die Nachricht in dieser Zeit nicht übermittelt werden konnte. Standardmäßig beträgt das Timeoutintervall für Verzögerungsbenachrichtigungen 4 Stunden. Diese Verzögerung verhindert, dass durch temporäre Nachrichtenübermittlungsfehler verursachte DSN-Verzögerungsmeldungen unnötigerweise gesendet werden. Das Senden von DSN-Verzögerungsmeldungen kann selektiv für Nachrichten, die ihren Ursprung innerhalb oder außerhalb der Exchange-Organisation haben, aktiviert bzw. deaktiviert werden.

Die Konfigurationsoptionen, die für DSN-Verzögerungsmeldungen verfügbar sind, werden in der folgenden Tabelle beschrieben.

### Konfigurationsoptionen, die für DSN-Verzögerungsmeldungen verfügbar sind

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parametername</th>
<th>Standardwert</th>
<th>Ort</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>DelayNotificationTimeOut</em></p></td>
<td><p><code>4:00:00</code>4 Stunden</p></td>
<td><p><strong>Set-TransportService</strong> oder Servereigenschaften in der Exchange-Verwaltungskonsole</p></td>
<td><p>Dieser Parameter gibt an, wie lange der Server wartet, bevor er eine DSN-Verzögerungsmeldung an den Absender sendet. Der Wert dieses Parameters sollte immer größer sein als der Wert des Parameters <em>TransientFailureRetryCount</em> multipliziert mit dem Wert des Parameters <em>TransientFailureRetryInterval</em>.</p>
<p>Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalDelayDSNEnabled</em></p></td>
<td><p><code>$true</code></p></td>
<td><p><strong>Set-TransportConfig</strong></p></td>
<td><p>Dieser Parameter gibt an, ob DSN-Verzögerungsmeldungen an Nachrichtenabsender außerhalb der Exchange-Organisation gesendet werden können.</p>
<p>Gültige Eingaben für diesen Parameter sind <code>$true</code> oder <code>$false</code>.</p></td>
</tr>
<tr class="odd">
<td><p><em>InternalDelayDSNEnabled</em></p></td>
<td><p><code>$true</code></p></td>
<td><p><strong>Set-TransportConfig</strong></p></td>
<td><p>Dieser Parameter gibt an, ob DSN-Verzögerungsmeldungen an Nachrichtenabsender innerhalb der Exchange-Organisation gesendet werden können.</p>
<p>Gültige Eingaben für diesen Parameter sind <code>$true</code> oder <code>$false</code>.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Auf Exchange 2007-Hub-Transport-Servern stehen alle <EM>ExternalDSN*</EM>- und <EM>InternalDSN*</EM>-Parameter im Cmdlet <STRONG>Set-TransportServer</STRONG>, nicht im Cmdlet <STRONG>Set-TransportConfig</STRONG> zur Verfügung. Wenn Sie in Ihrer Organisation Exchange 2007-Hub-Transport-Server verwenden, müssen Sie Änderungen an diesen Werten über das Cmdlet <STRONG>Set-TransportServer</STRONG> auf jedem Exchange 2007-Hub-Transport-Server vornehmen.



Zurück zum Seitenanfang

## Konfigurationsoptionen für die erneute Nachrichtenübermittlung

Bei der erneuten Übermittlung von Nachrichten werden nicht zugestellte Nachrichten zurück an die Übermittlungswarteschlange gesendet, damit das Kategorisierungsmodul diese Nachrichten erneut verarbeitet.

## Automatische erneute Übermittlung von Nachrichten

Nicht zugestellte Nachrichten werden automatisch erneut übermittelt, wenn die Zustellungswarteschlange den Status Wiederholen aufweist und über einen angegebenen Zeitraum nicht in der Lage war, Nachrichten erfolgreich zuzustellen. Der Zeitraum wird über den Schlüssel *MaxIdleTimeBeforeResubmit* in der Anwendungskonfigurationsdatei "EdgeTransport.exe.config" gesteuert. Nur Nachrichten in Zustellungswarteschlangen kommen für die automatische erneute Übermittlung infrage.

Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.

Der Standardwert ist `12:00:00` oder 12 Stunden.

## Manuelle erneute Übermittlung von Nachrichten

Sie können Nachrichten manuell erneut übermitteln, die über den folgenden Status im Dienst "Transport" auf einem Postfach- oder einem Edge-Transport-Server verfügen:

  - Zustellungswarteschlangen mit dem Status "Wiederholen". Die Nachrichten in den Warteschlangen dürfen nicht den Status "Angehalten" aufweisen.

  - Nachrichten, die sich in der Nicht-erreichbar-Warteschlange befinden und nicht den Status Angehalten aufweisen.

  - Nachrichten, die sich in der Warteschlange für potenziell schädliche Nachrichten befinden.

Weitere Informationen zur Warteschlange für nicht verarbeitbare Nachrichten und zur Nicht-erreichbar-Warteschlange finden Sie unter "Informationen zur Warteschlange für nicht verarbeitbare Nachrichten und zur Nicht-erreichbar-Warteschlange" im Thema [Warteschlangen](queues-exchange-2013-help.md).

Wenn Sie Nachrichten, die sich in den Zustellungswarteschlangen oder in der Nicht-erreichbar-Warteschlange befinden, manuell erneut übermitteln möchten, ohne auf den Ablauf des Zeitraums zu warten, der durch den Parameter *MaxIdleTimeBeforeResubmit* festgelegt ist, müssen Sie das Cmdlet **Retry-Queue** mit dem Parameter *Resubmit* verwenden. Um Nachrichten manuell erneut zu übermitteln, die sich in der Warteschlange für potenziell schädliche Nachrichten befinden, können Sie die Warteschlangenanzeige oder das Cmdlet **Resume-Message** zum Fortsetzen der Nachricht verwenden. Weitere Informationen finden Sie im Abschnitt "Erneutes Übermitteln von Nachrichten in Warteschlangen" unter [Verwalten von Warteschlangen](manage-queues-exchange-2013-help.md).

Eine weitere Möglichkeit zum manuellen erneuten Übermitteln besteht darin, die Nachrichten anzuhalten, in Textdateien mit der Dateinamenerweiterung ".eml" zu exportieren und dann die EML-Dateien in das Wiedergabeverzeichnis auf einem beliebigen Postfachserver oder Edge-Transport-Server zu kopieren. Diese Methode zum erneuten Übermitteln kann für Nachrichten verwendet werden, die sich in den Zustellungswarteschlangen oder in der Nicht-erreichbar-Warteschlange befinden. Nachrichten in der Warteschlange für potenziell schädliche Nachrichten weisen bereits den Status Angehalten auf. Nachrichten in der Übermittlungswarteschlange können nicht angehalten oder exportiert werden.


> [!NOTE]
> Beim Exportieren von Nachrichten aus einer Warteschlange werden die Nachrichten nicht aus der jeweiligen Warteschlange entfernt. Nachdem die Nachrichten exportiert und erfolgreich mithilfe des Wiedergabeverzeichnisses erneut übermittelt wurden, müssen die angehaltenen Nachrichten entfernt werden, damit es zu keiner doppelten Zustellung der Nachrichten kommt.



Weitere Informationen finden Sie unter [Nachrichten aus Warteschlangen exportieren](export-messages-from-queues-exchange-2013-help.md).

Zurück zum Seitenanfang

## Konfigurationsoptionen für den Nachrichtenablauf

Das *Ablauftimeoutintervall für Nachrichten* legt die maximale Zeitspanne fest, in der ein Edge-Transport-Server oder der Transport-Dienst auf einem Postfachserver versucht, eine nicht zugestellte Nachricht zu übermitteln. Wenn die Nachricht nicht vor Ablauf des Timeoutintervalls erfolgreich zugestellt werden kann, erhält der Absender einen Unzustellbarkeitsbericht mit der ursprünglichen Nachricht oder den Nachrichtenköpfen.

## Automatischer Ablauf von Nachrichten

Das Timeoutintervall für den Ablauf von Nachrichten wird mit dem Parameter *MessageExpirationTimeOut* im Cmdlet **Set-TransportService** oder in den Servereigenschaften in der Exchange-Verwaltungskonsole gesteuert.

Geben Sie einen Wert als Zeitraum an: tt.hh:mm:ss, wobei t = Tage, h = Stunden, m = Minuten und s = Sekunden sind.

Der Standardwert ist `2.00:00:00` oder 2 Tage. Der gültige Eingabebereich für diesen Parameter liegt zwischen `00:00:05` und `90.00:00:00`.

## Manueller Ablauf von Nachrichten

Auch wenn Sie das Ablaufen von Nachrichten nicht manuell erzwingen können, haben Sie die Möglichkeit, Nachrichten aus einer beliebigen Warteschlange (mit Ausnahme der Übermittlungswarteschlange) mit oder ohne Unzustellbarkeitsbericht manuell zu entfernen.

Weitere Informationen finden Sie im Abschnitt "Entfernen von Nachrichten aus Warteschlangen" unter [Verwalten von Nachrichten in Warteschlangen](manage-messages-in-queues-exchange-2013-help.md).

Zurück zum Seitenanfang

