---
title: 'Nachrichteneinschränkungen: Exchange 2013 Help'
TOCTitle: Nachrichteneinschränkungen
ms:assetid: fba87902-2a79-42ac-b394-46a9016f667e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232205(v=EXCHG.150)
ms:contentKeyID: 50477131
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichteneinschränkungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

*Nachrichteneinschränkungen* beziehen sich auf eine Gruppe von Grenzwerten, die für die Anzahl Nachrichten und Verbindungen festgelegt wurden, die von einem Microsoft Exchange Server 2013-Computer verarbeitet werden können. Diese Grenzwerte verhindern die zufällige oder absichtliche Auslastung der Systemressourcen auf dem Exchange-Server.

**Inhalt**

Bereich von Nachrichteneinschränkungen

Nachrichtenkosten und Einschränkungen des Nachrichtenflusses

Nachrichteneinschränkungen auf Servern

Nachrichteneinschränkungen für Sendeconnectors

Nachrichteneinschränkungen für Empfangsconnectors

Nachrichteneinschränkungsrichtlinien

## Bereich von Nachrichteneinschränkungen

Nachrichteneinschränkungen umfassen eine Vielzahl von Grenzwerten für Nachrichtenverarbeitungsgeschwindigkeiten, SMTP-Verbindungsgeschwindigkeiten und Timeouts von SMTP-Sitzungen. Diese Grenzwerte sorgen in Kombination dafür, dass ein Exchange-Server nicht von der Menge der zu akzeptierenden und zu übermittelnden Nachrichten überlastet wird. Obwohl ggf. ein gewaltiger Rückstand an Nachrichten und Verbindungen auf die Verarbeitung wartet, versetzen die Grenzwerte der Nachrichteneinschränkung den Exchange-Server in die Lage, Nachrichten und Verbindungen ordnungsgemäß zu verarbeiten.

Neben den Nachrichteneinschränkungen können Sie auch Größenbeschränkungen für einzelne Nachrichtenkomponenten festlegen, z. B. die Anzahl von Empfängern, die Größe der Nachrichtenkopfzeile oder die Größe der einzelnen Anlagen. Weitere Informationen zu Größenbeschränkungen für Nachrichten finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

Ein weiteres Feature, das dazu beiträgt, eine Überlastung der Systemressourcen eines Exchange-Transportservers zu verhindern, ist die *Rückstaufunktion*. Die Rückstaufunktion überwacht die Systemressourcen im Transportdienst auf Postfachservern und Edge-Transport-Servern. Wenn für eine überwachte Systemressource, z. B. die Nutzung des Festplattenlaufwerks oder des Arbeitsspeichers, der angegebene Schwellenwert überschritten wird, nimmt der Server weniger neue Verbindungen und Nachrichten an und sorgt zunächst für die Übermittlung vorhandener Nachrichten. Wenn sich die Nutzung der überwachten Systemressourcen wieder normalisiert, steigert der Server die Anzahl der akzeptierten neuen Verbindungen langsam, bis der Normalwert erreicht wird.

Zurück zum Seitenanfang

## Nachrichtenkosten und Einschränkungen des Nachrichtenflusses

Zur Sicherstellung eines konsistenten Nachrichtendurchsatzes und einer vorhersagbaren Zustellungslatenz für Nachrichten berechnet Exchange 2013 einen kumulierten Kostenwert für Nachrichten. Dieses QoS-Feature (Quality of Service) wurde in Microsoft Exchange Server 2010 SP1 hinzugefügt. Der Kostenwert basiert auf den folgenden Kriterien:

  - Nachrichtengröße

  - Anzahl von Empfängern

  - Häufigkeit der Übertragung

Exchange 2013-Transport-Server protokollieren die durchschnittlichen Kosten von Nachrichten, die von den einzelnen Benutzern gesendet werden. Durch die Verwendung der Nachrichtenkosten stellt Exchange 2013 eine Reihe von Einstellungen zur Verfügung, mit denen die Auswirkungen eines Benutzers oder einer Verbindung auf eine Exchange-Organisation gesteuert werden können. Diese Einstellungen werden als *Einschränkungsrichtlinie* bezeichnet. Wenn ein Benutzer wiederholt Nachrichten mit hohen Kosten sendet, beispielsweise Nachrichten mit großen Anlagen oder zahlreichen Empfängern, verwenden Exchange 2013-basierte Transportserver eine Einschränkungsrichtlinie, um den Benutzernachrichten mit hohen Kosten eine niedrigere Priorität zuzuweisen, während Nachrichten mit geringeren Kosten weiterhin zugestellt werden. Dieses neue Verhalten fügt der Funktionalität zur Nachrichteneinschränkung in Exchange 2013 den Aspekt der Dienstqualität (Quality of Service, QoS) hinzu.


> [!NOTE]
> Aus Benutzersicht wirkt sich die Nachrichteneinschränkung nicht auf die Nachrichtenpriorität aus. Die ursprünglich vom Benutzer festgelegte Nachrichtenpriorität wird beibehalten. Beispielsweise sind Nachrichten weiterhin als Wichtig oder Dringend gekennzeichnet.



Zur Unterstützung dieser neuen Funktionalität verwendet Exchange 2013 die folgenden Mechanismen:

  - **Interner Priorisierungs-Agent** Dieser Agent wird bei Auftreten des **OnResolvedMessage**-Ereignisses ausgelöst und weist Nachrichten desselben Absenders, die einen hohen kumulierten Kostenwert aufweisen, eine niedrigere Priorität zu. Die Kosten werden über einen Zeitraum von einer Minute gemessen und betreffen Nachrichten, die an mehr als 500 Empfänger gesendet werden oder größer als 1 Megabyte (MB) sind.

  - **Kontingentbasierte Prioritätswarteschlange für Warteschlangentyp "MapiDelivery"**   Dieser Mechanismus veranlasst Exchange, Nachrichten in einer Warteschlange mit normaler Priorität schneller zuzustellen als Nachrichten in einer Warteschlange mit niedrigerer Priorität. Standardmäßig lautet das Verhältnis zwischen Warteschlangen normaler und niedriger Priorität 20:1. Neue Nachrichten aus einer Warteschlange mit niedriger Priorität werden jedoch nie früher zugestellt als neue Nachrichten aus einer Warteschlange mit höherer Priorität. Stellen Sie sich zum Beispiel das folgende Szenario vor:
    
    1.  Zwanzig Nachrichten mit der Priorität "Normal" werden gesendet. Standardmäßig ist die nächste zugestellte Nachricht eine Nachricht mit niedrigerer Priorität.
    
    2.  Zwei neue Nachrichten werden vom Transportserver empfangen: Eine Nachricht von einer Warteschlange höherer Priorität, und eine Nachricht von einer Warteschlange mit niedrigerer Priorität.
    
    In diesem Szenario wird die Nachricht aus der Warteschlange mit höherer Priorität zuerst zugestellt. Anschließend wird die Nachricht aus der Warteschlange mit niedrigerer Priorität zugestellt.

  - **Einschränkung gleichzeitiger Verbindungen basierend auf dem Status der Messagingdatenbank** Dieser Mechanismus überwacht den Status der Exchange-Messagingdatenbank (MDB) und schränkt gleichzeitige Verbindungen mit Exchange-Transportservern basierend auf einer zugewiesenen Statuskennzahl ein. Die MDB wird von der Ressourcenstatusmonitor-API im Transportdienst auf dem Postfachserver überwacht und erhält eine Statuskennzahl zwischen -1 und 100. Dieser Wert basiert auf der RPC-Leistungsstatistik, die mit jeder RPC-Antwort vom Prozess "Store.exe" im Postfachtransportdienst gesendet wird. Das Framework für die Ressourcenintegrität verwendet sowohl den Leistungsindikator **Anforderungen/s** als auch den Leistungsindikator **Durchschnittliche RPC-Wartezeit**, um eine Statuskennzahl für die Datenbank zu berechnen. Zur Aufrechterhaltung eines konsistenten Benutzererlebnisses bei der Interaktion mit dem Postfach senkt Exchange die Anzahl von gleichzeitigen Verbindungen, wenn die Statuskennzahl abnimmt. Die folgenden Statuswertebereiche stehen zur Verfügung:
    
      - **-1:**  Dieser Wert gibt an, dass der MDB-Status unbekannt ist. Dieser Wert wird beim Start der Datenbank zugewiesen. In diesem Szenario wird die Datenbank als fehlerfrei betrachtet.
    
      - **0:**  Dieser Wert wird zugewiesen, wenn die Datenbank sich in einem fehlerhaften Zustand befindet. In diesem Zustand sollte die Datenbank nicht abgefragt werden.
    
      - **1 bis 99:**  Diese Werte repräsentieren einen Zustand mittlerer Integrität. Ein niedrigerer Wert steht für eine Datenbank niedrigerer Integrität.
    
      - **100:**  Dieser Wert steht für eine fehlerfreie Datenbank.

Der Microsoft Exchange-Einschränkungsdienst stellt das Framework für die Einschränkung des Nachrichtenflusses bereit. Der Microsoft Exchange-Einschränkungsdienst verfolgt die Einschränkungseinstellungen für den Nachrichtenfluss für einen bestimmten Benutzer und speichert die Einschränkungsinformationen im Arbeitsspeicher zwischen. Die Einschränkungseinstellungen für den Nachrichtenfluss werden auch als *Budget* bezeichnet. Ein Neustart des Microsoft Exchange-Einschränkungsdiensts führt auch dazu, dass die Budgets zur Einschränkung des Nachrichtenflusses zurückgesetzt werden.

Sie können die in Exchange 2013 verfügbaren Cmdlets für Einschränkungsrichtlinien dazu verwenden, individuelle Budgeteinstellungen für eine Einschränkungsrichtlinie zu konfigurieren. Ein Budget entspricht dem Zugriffsumfang, der einem Benutzer oder einer Anwendung für eine bestimmte Einstellung zugewiesen ist. Ein Budget gibt an, wie viele Verbindungen ein Benutzer verwenden kann, oder wie hoch die Benutzeraktivität pro Minute sein darf. Beispielsweise kann durch das Konfigurieren eines Budgets die Zeitdauer festgelegt werden, für die ein Benutzer ein bestimmtes Feature in Exchange verwenden kann, beispielsweise ActiveSync, Outlook Web App oder Exchange-Webdienste. Dieser Schwellenwert wird in einer Einschränkungsrichtlinie gespeichert und definiert das Budget.

Zeiteinstellungen für ein Budget werden als Prozentsatz einer Minute festgelegt. Daher repräsentiert ein Schwellenwert von 100 einen Zeitraum von 60 Sekunden. Angenommen, Sie möchten Outlook Web App-Richtlinieneinstellungen festlegen, um die Zeitdauer einzuschränken, für die ein Benutzer Outlook Web App-Code auf einem Clientzugriffsserver ausführen kann, und Sie möchten die Zeit, die der Benutzer mit dem Clientzugriffsserver kommunizieren kann, auf 600 Millisekunden pro Minute einschränken. Hierzu müssen Sie den Wert der beiden folgenden Parameter auf 1 Prozent pro Minute (600 Millisekunden) festlegen:

  - **OWAPercentTimeInCAS:**  1

  - **OWAPercentTimeInMailboxRPC:**  1

Einem Benutzer, auf den diese Richtlinie angewendet wird, wird ein OWAPercentTimeInCAS-Budget von 600 Millisekunden und ein OWAPercentageTimeInMailboxRPC-Budget von 600 Millisekunden zugewiesen. In diesem Szenario kann der Benutzer bei Anmeldung an Outlook Web App bis zu 600 Millisekunden lang Clientzugriffscode ausführen. Nach Ablauf der 600 Millisekunden wird die Verbindung als "Über Budget" eingestuft, und der Exchange-Server lässt nach Überschreitung des Budgetgrenzwerts für eine Minute keine weitere Outlook Web App-Aktion zu. Nach Ablauf einer Minute kann der Benutzer für weitere 600 Millisekunden Outlook Web App-Clientzugriffscode ausführen.

Zurück zum Seitenanfang

## Nachrichteneinschränkungen auf Servern

Sie können die Nachrichteneinschränkungsoptionen an den folgenden Stellen festlegen:

  - Im Transportdienst

  - Auf einem Sendeconnector

  - Auf einem Empfangsconnector

Sie können alle Nachrichteneinschränkungsoptionen, die im Transportdienst auf Postfachservern, im Postfachtransportdienst auf Postfachservern oder im Front-End-Transport-Dienst auf Clientzugriffsservern verfügbar sind, mithilfe der Exchange-Verwaltungsshell festlegen. Einige dieser Optionen können Sie auch durch Konfiguration der Transportservereigenschaften in der Exchange-Verwaltungskonsole festlegen.

In der folgenden Tabelle sind die Nachrichteneinschränkungsoptionen, die auf Transportservern verfügbar sind, enthalten.

### Nachrichteneinschränkungsoptionen auf Transportservern

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p>
<p><strong>Set-MailboxTransportService</strong></p></td>
<td><p><em>MaxConcurrentMailboxDeliveries</em></p></td>
<td><p>20</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl an Zustellungsthreads an, die beim Senden von Nachrichten an Postfächer gleichzeitig im Transportdienst geöffnet sein dürfen. Der gültige Eingabebereich für diesen Parameter liegt zwischen 1 und 256. Es wird empfohlen, den Standardwert nur zu ändern, wenn Sie vom Microsoft-Kundendienst und -Support dazu aufgefordert werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-TransportService</strong></p>
<p><strong>Set-MailboxTransportService</strong></p></td>
<td><p><em>MaxConcurrentMailboxSubmissions</em></p></td>
<td><p>20</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl an Übermittlungsthreads an, die zum Senden von Nachrichten aus Postfächern gleichzeitig im Transportdienst geöffnet sein dürfen. Der gültige Eingabebereich für diesen Parameter liegt zwischen 1 und 256.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p></td>
<td><p><em>MaxConnectionRatePerMinute</em></p></td>
<td><p>1200</p></td>
<td><p>Dieser Parameter gibt die maximale Verbindungsrate für Verbindungen mit dem Transportdienst an. Wenn viele Verbindungen gleichzeitig mit dem Transportdienst hergestellt werden sollen, wird die Verbindungsrate über den Parameter <em>MaxConnectionRatePerMinute</em> begrenzt, sodass die Serverressourcen nicht überlastet werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-TransportService</strong> oder</p>
<p>Transportservereigenschaften</p></td>
<td><p><em>MaxOutboundConnections</em></p></td>
<td><p>1000</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl ausgehender Verbindungen an, die gleichzeitig geöffnet sein dürfen. Wenn Sie den Wert <code>unlimited</code> eingeben, wird die Anzahl der ausgehenden Verbindungen nicht beschränkt. Der Wert dieses Parameters muss größer als oder gleich dem Wert des Parameters <em>MaxPerDomainOutboundConnections</em> sein.</p>
<p>Dieser Wert kann auch über diese Optionen der Exchange-Verwaltungskonsole konfiguriert werden: <strong>Server</strong> &gt; <strong>Server</strong> &gt; <strong>Eigenschaften</strong> &gt; <strong>Transportgrenzwerte</strong> &gt; <strong>Einschränkungen für ausgehende Verbindungen</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-TransportService</strong> oder</p>
<p>Transportservereigenschaften</p></td>
<td><p><em>MaxPerDomainOutboundConnections</em></p></td>
<td><p>20</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl gleichzeitiger Verbindungen mit einer einzelnen Domäne an. Wenn Sie den Wert <code>unlimited</code> eingeben, wird die Anzahl der ausgehenden Verbindungen pro Domäne nicht beschränkt. Der Wert dieses Parameters muss größer als oder gleich dem Wert des Parameters <em>MaxOutboundConnections</em> sein.</p>
<p>Dieser Wert kann auch über diese Optionen der Exchange-Verwaltungskonsole konfiguriert werden: <strong>Server</strong> &gt; <strong>Server</strong> &gt; <strong>Eigenschaften</strong> &gt; <strong>Transportgrenzwerte</strong> &gt; <strong>Einschränkungen für ausgehende Verbindungen</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-TransportService</strong></p></td>
<td><p><em>PickupDirectoryMaxMessagesPerMinute</em></p></td>
<td><p>100</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl von Nachrichten an, die pro Minute vom PICKUP-Verzeichnis und vom Wiedergabeverzeichnis verarbeitet werden. Jedes Verzeichnis kann Nachrichtendateien unabhängig voneinander mit einer Geschwindigkeit verarbeiten, die durch diesen Parameter angegeben ist.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichteneinschränkungen für Sendeconnectors

In der folgenden Tabelle ist die Nachrichteneinschränkungsoption, die für Sendeconnectors verfügbar ist, enthalten. Sie müssen diese Option mithilfe der Exchange-Verwaltungsshell konfigurieren.

### Nachrichteneinschränkungsoptionen für Sendeconnectors

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-SendConnector</strong></p></td>
<td><p><em>ConnectionInactivityTimeOut</em></p></td>
<td><p>10 Minuten</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine geöffnete SMTP-Verbindung zu einem Zielmessagingserver im Leerlauf bleiben kann, bis die Verbindung geschlossen wird.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichteneinschränkungen für Empfangsconnectors

In der folgenden Tabelle sind die Nachrichteneinschränkungsoptionen enthalten, die für Empfangsconnectors verfügbar sind, die im Transportdienst auf einem Postfachserver oder einem Edge-Transport-Server konfiguriert sind. Sie müssen diese Optionen mithilfe der Exchange-Verwaltungsshell konfigurieren.

### Nachrichteneinschränkungsoptionen für Empfangsconnectors

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>ConnectionInactivityTimeOut</em></p></td>
<td><p>5 Minuten im Transportdienst auf Postfachservern</p>
<p>5 Minuten im Front-End-Transport-Dienst auf Clientzugriffsservern.</p>
<p>1 Minute auf Edge-Transport-Servern.</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine geöffnete SMTP-Verbindung zu einem Quellmessagingserver im Leerlauf bleiben kann, bis die Verbindung geschlossen wird. Der Wert dieses Parameters muss kleiner sein als der durch den Parameter <em>ConnectionTimeout</em> angegebene Wert.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>ConnectionTimeOut</em></p></td>
<td><p>10 Minuten im Transportdienst auf Postfachservern</p>
<p>10 Minuten im Front-End-Transport-Dienst auf Clientzugriffsservern.</p>
<p>5 Minuten auf Edge-Transport-Servern.</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine SMTP-Verbindung zu einem Quellmessagingserver geöffnet bleiben kann, und zwar auch dann, wenn der Messagingserver Daten überträgt. Der Wert dieses Parameters muss größer sein als der durch den Parameter <em>ConnectionInactivityTimeout</em> angegebene Wert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>MaxInboundConnection</em></p></td>
<td><p>5000</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl eingehender SMTP-Verbindungen an, die von diesem Empfangsconnector gleichzeitig zugelassen werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>MaxInboundConnectionPercentagePerSource</em></p></td>
<td><p>100 Prozent für den Standardempfangsconnector im Transportdienst auf einem Postfachserver</p>
<p>2 Prozent für die anderen Empfangsconnectors im Transportdienst auf Postfachservern und im Front-End-Transport-Dienst auf Clientzugriffsservern.</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl von SMTP-Verbindungen von einem einzigen Quellmessagingserver aus an, die von einem Empfangsconnector gleichzeitig zugelassen werden. Der Wert wird als Prozentsatz der verbleibenden verfügbaren Verbindungen auf einem Empfangsconnector ausgedrückt. Die maximale Anzahl von Verbindungen, die vom Empfangsconnector zugelassen werden, wird durch den Parameter <em>MaxInboundConnection</em> definiert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>MaxInboundConnectionPerSource</em></p></td>
<td><p>unlimited für den Standardempfangsconnector im Transportdienst auf einem Postfachserver</p>
<p>20 Prozent für die anderen Empfangsconnectors im Transportdienst auf Postfachservern und im Front-End-Transport-Dienst auf Clientzugriffsservern.</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl von SMTP-Verbindungen von einem einzigen Quellmessagingserver aus an, die von einem Empfangsconnector gleichzeitig zugelassen werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>MaxProtocolErrors</em></p></td>
<td><p>5</p></td>
<td><p>Dieser Parameter gibt die maximale Anzahl von SMTP-Protokollfehlern an, die von einem Empfangsconnector zugelassen werden, bevor dieser die Verbindung zu dem Quellmessagingserver beendet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-ReceiveConnector</strong></p></td>
<td><p><em>TarpitInterval</em></p></td>
<td><p>5 Sekunden</p></td>
<td><p>Dieser Parameter gibt die Verzögerung an, die in Verbindung mit dem <em>Teergrubenverfahren</em> verwendet wird. Beim Teergrubenverfahren werden SMTP-Antworten für bestimmte SMTP-Kommunikationsmuster, die auf einen Verzeichnisdiebstahlangriff oder andere unerwünschte Nachrichten hinweisen, künstlich verzögert. Ein <em>Verzeichnisdiebstahlangriff</em> ist der Versuch, gültige E-Mail-Adressen einer bestimmten Organisation zu sammeln, die dann als Ziel für unverlangte Werbe-E-Mails verwendet werden.</p>
<p>Die Verzögerung, die mit dem Parameter <em>TarpitInterval</em> angegeben wird, gilt nur für anonyme Verbindungen.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichteneinschränkungsrichtlinien

In Exchange 2013 verfügt jedes Postfach über eine *ThrottlingPolicy*-Einstellung. Der Standardwert für diese Einstellung ist leer (`$null`). Sie können den Parameter *ThrottlingPolicy* im Cmdlet **Set-Mailbox** verwenden, um eine Einschränkungsrichtlinie für ein Postfach zu konfigurieren.

Es ist eine Standardeinschränkungsrichtlinie vorhanden, um eine standardmäßige Budgetkonfiguration für Benutzer bereitzustellen, die sich mit Exchange verbinden. Erstellen Sie eine neue Einschränkungsrichtlinie, um angepasste Budgeteinstellungen für einen oder mehrere Benutzer zu konfigurieren. Wenden Sie die Richtlinie anschließend auf den geeigneten Benutzer oder eine geeignete Gruppe an.


> [!IMPORTANT]
> Wir empfehlen, die Standardeinschränkungsrichtlinie nicht zu ändern.



In der Exchange-Verwaltungsshell können alle Nachrichteneinschränkungsoptionen festgelegt werden, die für Postfachserver zur Verfügung stehen. Zum Verwalten von Einschränkungsrichtlinien stehen die folgenden Cmdlets zur Verfügung:

  - **Get-ThrottlingPolicy**

  - **Remove-ThrottlingPolicy**

  - **New-ThrottlingPolicy**

  - **Set-ThrottlingPolicy**

Mithilfe der Cmdlets **New-ThrottlingPolicy** und **Set-ThrottlingPolicy** können Sie konfigurieren, wie hoch die Benutzeraktivität in Exchange für eine bestimmte Verbindung oder einen bestimmten Zeitraum sein darf. Diese Einstellungen repräsentieren das Budget eines Benutzers. Sie können Einschränkungsrichtlinien konfigurieren, um den Zugriff auf die folgenden Exchange-Features zu steuern:

  - Exchange ActiveSync

  - Exchange-Webdienste

  - Outlook Web App

  - Unified Messaging

  - IMAP4

  - POP3

  - Outlook-Clientverbindungen (MAPI- oder RPC-Verbindungen)

  - Nachrichtenflusseinstellungen

  - PowerShell-Befehle

  - CPU-Auslastung

Zurück zum Seitenanfang

