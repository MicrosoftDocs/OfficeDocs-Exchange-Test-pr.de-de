---
title: 'Warteschlangen: Exchange 2013 Help'
TOCTitle: Warteschlangen
ms:assetid: e7ad0ba5-3789-4a2b-9825-6bb1b321609c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125022(v=EXCHG.150)
ms:contentKeyID: 51409357
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Warteschlangen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Eine *Warteschlange* ist ein temporärer Speicherort für Nachrichten, die auf den Eintritt in die nächste Verarbeitungsphase oder die Zustellung an ihr jeweiliges Ziel warten. Jede Warteschlange stellt einen logischen Satz von Nachrichten dar, die von einem Exchange-Server in einer bestimmten Reihenfolge verarbeitet werden. In Microsoft Exchange Server 2013 werden Nachrichten vor, während und nach der Zustellung in Warteschlangen gehalten. Warteschlangen sind auf Postfachservern und Edge-Transport-Servern vorhanden. Postfachserver und Edge-Transport-Server werden in diesem Thema als *Transportserver* bezeichnet.

Wie in den Vorgängerversionen von Exchange wird in Exchange 2013 eine ESE-Datenbank (Extensible Storage Engine) für Warteschlangenspeicher verwendet.

Sie können Warteschlangen und die darin enthaltenen Nachrichten mit der Exchange-Verwaltungsshell und der Warteschlangenanzeige in der Exchange Toolbox verwalten. Beide Tools ermöglichen das Anzeigen des Status und Inhalts von Warteschlangen sowie detaillierter Nachrichteneigenschaften. Beide dienen auch zum Ausführen von Aktionen, mit denen Warteschlangen bzw. in diesen enthaltene Nachrichten geändert werden können.

**Inhalt**

  - Warteschlangentypen

  - Warteschlangendatenbank-Dateien

  - Warteschlangeneigenschaften
    
      - NextHopSolutionKey
    
      - IncomingRate, OutgoingRate und Velocity
    
      - Warteschlangenstatus
    
      - Weitere Warteschlangeneigenschaften

  - Nachrichteneigenschaften
    
      - Nachrichtenstatus
    
      - Weitere Nachrichteneigenschaften

  - Verwalten von Warteschlangen und Nachrichten in Warteschlangen

## Warteschlangentypen

In Exchange 2013 gibt es die folgenden Warteschlangentypen:

  - **Beständige Warteschlangen** *Beständige Warteschlangen* sind in jeder Exchange-Organisation auf jedem Transportserver vorhanden. Wie in den Vorgängerversionen von Exchange sind in Exchange 2013 drei beständige Warteschlangen enthalten:
    
      - **Übermittlungswarteschlange**   Die Übermittlungswarteschlange wird vom Kategorisierungsmodul zum Sammeln aller Nachrichten verwendet, die von Transport-Agents auf dem Transportserver aufgelöst, weitergeleitet und verarbeitet werden müssen. Alle Nachrichten, die von einem Transportserver empfangen werden, gelangen über die Übermittlungswarteschlange in die Verarbeitung. Nachrichten werden auf Postfachservern über einen Empfangsconnector, das PICKUP- oder Wiedergabeverzeichnis oder den Postfachtransport-Übermittlungsdienst übermittelt. Nachrichten werden auf Edge-Transport-Servern zumeist über einen Empfangsconnector übermittelt, doch das PICKUP- und Wiedergabeverzeichnis stehen ebenfalls zur Verfügung.
        
        Das Kategorisierungsmodul ruft Nachrichten aus dieser Warteschlange ab und bestimmt u. a. den Standort des Empfängers und die Route zu diesem Standort. Nach der Kategorisierung wird die Nachricht in eine Zustellungswarteschlange oder in die Nicht erreichbar-Warteschlange verschoben. Auf jedem Transportserver ist nur eine Übermittlungswarteschlange vorhanden. Nachrichten, die sich in der Übermittlungswarteschlange befinden, können sich nicht gleichzeitig in anderen Warteschlangen befinden. Weitere Informationen zum Kategorisierungsmodul und zur Transportpipeline finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).
    
      - **Nicht-erreichbar-Warteschlange**   In der Nicht-erreichbar-Warteschlange befinden sich Nachrichten, die nicht an die jeweiligen Ziele weitergeleitet werden können. Ein nicht erreichbares Ziel wird in der Regel durch Konfigurationsänderungen verursacht, durch die sich der Routingpfad für die Zustellung verändert hat. Unabhängig vom Ziel werden alle Nachrichten mit nicht erreichbaren Empfängern in dieser Warteschlange abgelegt. Auf jedem Transportserver ist nur eine Nicht-erreichbar-Warteschlange vorhanden.
        
        Wenn eine Routingänderung erkannt wird, werden Nachrichten in der Nicht-erreichbar-Warteschlange automatisch neu übermittelt. Sobald also der Zustands- oder Konfigurationsfehler behoben wird, der dazu führte, dass die Nachrichten in die Nicht-erreichbar-Warteschlange eingereiht wurden, müssen Sie nichts weiter tun, um die Nachrichten von dort zur Zustellung zu verschieben.
        
        Die Nicht-Erreichbar-Warteschlange ist normalerweise leer. Wenn die Nicht-erreichbar-Warteschlange keine Nachrichten enthält, wird sie in der Warteschlangenanzeige oder den Ergebnissen von **Get-Queue** nicht angezeigt.
    
      - **Warteschlange für nicht verarbeitbare Nachrichten**   Die Warteschlange für nicht verarbeitbare Nachrichten ist eine spezielle Warteschlange zum Isolieren von Nachrichten, die das Exchange 2013-System nach einem Transportserver- oder Dienstausfall möglicherweise beeinträchtigen können. Diese Nachrichten können aufgrund ihres Inhalts und Formats eine Gefahr darstellen. Sie können auch das Ergebnis eines fehlerhaft geschriebenen Agents sein, der beim Verarbeiten der verdächtigen Nachricht zu einem Ausfall des Servercomputers mit Exchange führte.
        
        Die Warteschlange für nicht verarbeitbare Nachrichten ist normalerweise leer. Wenn die Warteschlange für nicht verarbeitete Nachrichten keine Nachrichten enthält, wird sie in der Warteschlangenanzeige oder den Ergebnissen von **Get-Queue** nicht angezeigt. Die Nachrichten in der Warteschlange für potenziell schädliche Nachrichten werden niemals automatisch fortgesetzt und laufen nicht ab. Nachrichten verbleiben in der Warteschlange für nicht verarbeitbare Nachrichten, bis sie manuell von einem Administrator wieder aufgenommen oder entfernt werden.

  - **Zustellungswarteschlangen**   Zustellungswarteschlangen enthalten Nachrichten, die über SMTP an beliebige lokale oder Remoteziele zugestellt werden. Alle Nachrichten werden über SMTP zwischen Exchange-Servern übertragen. Für Nicht-SMTP-Ziele werden ebenfalls Zustellungswarteschlangen verwendet, wenn das Ziel von einem Zustellungs-Agent-Connector bedient wird. . Jede Zustellungswarteschlange enthält Nachrichten, die an dasselbe Ziel weitergeleitet werden. Es ist praktisch unvermeidbar, dass auf dem Transportserver mehrere Zustellungsquoten vorhanden sind. Zustellungswarteschlangen werden dynamisch erstellt, wenn sie benötigt werden, und automatisch gelöscht, sobald sie leer sind und die Ablaufzeit verstrichen ist. Die Warteschlangenablaufzeit wird im Cmdlet **Set-TransportService** über den Parameter *QueueMaxIdleTime* gesteuert. Der Standardwert beträgt drei Minuten.

  - **Shadow-Warteschlangen**   Shadow-Warteschlangen enthalten redundante Kopien von Nachrichten, die gerade übertragen werden. Weitere Informationen finden Sie unter [Shadow-Redundanz](shadow-redundancy-exchange-2013-help.md).

  - **Sicherheitsnetz**   Im Sicherheitsnetz werden Kopien von Nachrichten aufbewahrt, die erfolgreich an den Transportserver zugestellt wurden. Das Sicherheitsnetz ist im Grunde ebenfalls nur eine weitere Warteschlange in der Warteschlangendatenbank, auch wenn es nicht über Warteschlangenverwaltungstools zugänglich ist. Weitere Informationen finden Sie unter [Sicherheitsnetz](safety-net-exchange-2013-help.md).

Zurück zum Seitenanfang

## Warteschlangendatenbank-Dateien

Die unterschiedlichen Warteschlangen werden in einer einzigen ESE-Datenbank gespeichert. Diese Warteschlangendatenbank befindet sich standardmäßig auf dem Transportserver unter `%ExchangeInstallPath%TransportRoles\data\Queue`.

Wie jede ESE-Datenbank verwendet die Warteschlangendatenbank Protokolldateien, um Daten zu akzeptieren, nachzuverfolgen und zu warten. Zum Verbessern der Leistung werden alle Nachrichtentransaktionen zuerst in Protokolldateien und in den Arbeitsspeicher und dann in die Datenbankdatei geschrieben. Die Prüfpunktdatei verfolgt die Transaktionsprotokolleinträge, für die ein Commit in der Datenbank ausgeführt wurde. Während eines normalen Herunterfahrens des Microsoft Exchange-Transportdiensts wird für Änderungen an der Datenbank, für die noch kein Commit in der Datenbank vorgenommen wurde und die sich in den Transaktionsprotokollen befinden, ein Commit in der Datenbank ausgeführt.

Für die Warteschlangendatenbank wird die Umlaufprotokollierung verwendet. Dies bedeutet, dass der Verlauf der Transaktionen, für die ein Commit ausgeführt wurde und die sich in den Transaktionsprotokollen befinden, nicht erhalten bleibt. Alle Transaktionsprotokolle, die älter als der aktuelle Prüfpunkt sind, werden sofort und automatisch gelöscht. Daher können die Transaktionsprotokolle für die Wiederherstellung der Warteschlangendatenbank aus der Sicherung nicht wiedergegeben werden.

Nachrichten in der Warteschlangendatenbank werden von Exchange 2013 mithilfe von *Generierungstabellen* gespeichert und bereinigt. Statt einzelne Nachrichteneinträge aus einer großen Tabelle zu verarbeiten und zu löschen, werden Nachrichten von der Warteschlangendatenbank in zeitbasierten Tabellen gespeichert, die nur dann komplett gelöscht werden, nachdem alle darin enthaltenen Nachrichten erfolgreich verarbeitet wurden. Angenommen, alle zwischen 13:00 und 14:00 Uhr in Warteschlangen eingereihten Nachrichten werden unabhängig von Warteschlange oder Ziel in der Tabelle `1p-2p_msgs` gespeichert. Um 14:00 Uhr werden neue Nachrichten in der Tabelle `2p-3p_msgs` gespeichert. Um 16:00 Uhr wird eine neue Tabelle namens `4p-5p_msgs` erstellt, und die gesamte Tabelle `1p-2p_msgs` wird gelöscht – aber nur dann, wenn alle darin enthaltenen Nachrichten erfolgreich verarbeitet wurden. Diese Vorgehensweise, d. h. statt einzelner Nachrichten die gesamte Nachrichtentabelle zu löschen, trägt zu einer Verbesserung der E/A-Leistung des Laufwerks bei, auf dem die Warteschlangendatenbank gespeichert ist.

In der folgenden Tabelle sind die Dateien aufgelistet, aus denen die Warteschlangendatenbank besteht.

### Dateien, aus denen die Warteschlangendatenbank besteht

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Datei</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mail.que</p></td>
<td><p>In dieser Warteschlangendatenbank-Datei sind alle in der Warteschlange befindlichen Nachrichten gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>Tmp.edb</p></td>
<td><p>Diese temporäre Datenbankdatei wird verwendet, um das Schema der Warteschlangendatenbank beim Starten zu überprüfen.</p></td>
</tr>
<tr class="odd">
<td><p>Trn*.log</p></td>
<td><p>In diesem Transaktionsprotokoll werden alle Änderungen an der Warteschlangendatenbank aufgezeichnet. Änderungen an der Datenbank werden zuerst in das Transaktionsprotokoll geschrieben. Anschließend wird ein Commit in der Datenbank ausgeführt. Trn.log ist die derzeit aktive Transaktionsprotokolldatei. Trntmp.log ist die nächste bereitgestellte Transaktionsprotokolldatei, die im Voraus angelegt wird. Wenn die vorhandene Trn.log-Transaktionsprotokolldatei ihre maximale Größe erreicht, wird Trn.log in Trn<em>nnnn</em>.log umbenannt, wobei es sich bei <em>nnnn</em> um eine fortlaufende Nummer handelt. Trntmp.log wird anschließend in Trn.log umbenannt und wird zur aktuellen aktiven Transaktionsprotokolldatei.</p></td>
</tr>
<tr class="even">
<td><p>Trn.chk</p></td>
<td><p>Diese Prüfpunktdatei verfolgt die Transaktionsprotokolleinträge, für die ein Commit in der Datenbank ausgeführt wurde. Diese Datei befindet sich immer am gleichen Speicherort wie die Datei mail.que.</p></td>
</tr>
<tr class="odd">
<td><p>Trnres00001.jrs</p>
<p>Trnres00002.jrs</p></td>
<td><p>Diese Reserve-Transaktionsprotokolldateien dienen als Platzhalter. Sie werden nur verwendet, wenn die Festplatte, auf der die Transaktionsprotokolldateien gespeichert sind, nicht mehr genügend Speicherplatz aufweist, um ein ordnungsgemäßes Beenden der Warteschlangendatenbank zu ermöglichen.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Optionen für das Konfigurieren der Warteschlangendatenbank

Die Warteschlangendatenbank kann durch Hinzufügen oder Ändern von Schlüsseln in der XML-Anwendungskonfigurationsdatei `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` konfiguriert werden. Diese Datei ist mit dem Microsoft Exchange-Transportdienst verknüpft. Änderungen an der Datei "EdgeTransport.exe.config" werden nach einem Neustart des Microsoft Exchange-Transportdiensts wirksam.

Im Abschnitt `<appSettings>` der Datei "EdgeTransport.exe.config" können Sie neue Schlüssel hinzufügen oder vorhandene Schlüssel ändern. Falls ein bestimmter Schlüssel nicht vorhanden ist, können Sie ihn manuell hinzufügen, um seinen Wert zu ändern.

Die Schlüssel für die Warteschlangendatenbank, die in der Datei "EdgeTransport.exe.config" zur Verfügung stehen, werden in der folgenden Tabelle beschrieben.

### Schlüssel für die Nachrichtenwarteschlangen-Datenbank in der Datei "EdgeTransport.exe.config"

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Taste</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>QueueDatabaseBatchSize</em></p></td>
<td><p>40</p></td>
<td><p>Dieser Schlüssel gibt die Anzahl der Datenbank-E/A-Vorgänge an, die vor ihrer Ausführung in einer Gruppe zusammengefasst werden können. Dieser Schlüssel ist standardmäßig nicht in der Datei &quot;EdgeTransport.exe.config&quot; vorhanden.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseBatchTimeout</em></p></td>
<td><p>100</p></td>
<td><p>Dieser Schlüssel gibt den maximalen Zeitraum in Millisekunden an, für den die Datenbank auf die Gruppierung mehrerer Datenbank-E/A-Vorgänge wartet, bevor diese ausgeführt werden. Die Datenbank-E/A-Vorgänge werden ohne Warten auf weitere Vorgänge ausgeführt, wenn die folgenden Bedingungen erfüllt sind:</p>
<ul>
<li><p>Die vom Schlüssel <em>QueueDatabaseBatchSize</em> angegebene Anzahl der Datenbank-E/A-Vorgänge wurde nicht erreicht.</p></li>
<li><p>Der im Schlüssel <em>QueueDatabaseBatchTimeout</em> angegebene Zeitraum ist verstrichen.</p></li>
</ul>
<p>Dieser Schlüssel ist standardmäßig nicht in der Datei &quot;EdgeTransport.exe.config&quot; vorhanden.</p></td>
</tr>
<tr class="odd">
<td><p><em>QueueDatabaseMaxConnections</em></p></td>
<td><p>4</p></td>
<td><p>Dieser Schlüssel gibt die Anzahl der ESE-Datenbankverbindungen an, die geöffnet sein dürfen.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseLoggingBufferSize</em></p></td>
<td><p>5 MB</p></td>
<td><p>Dieser Schlüssel gibt den Arbeitsspeicher an, der zum Zwischenspeichern von Transaktionsdatensätzen verwendet wird, bevor diese in die Transaktionsprotokolldatei geschrieben werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>QueueDatabaseLoggingFileSize</em></p></td>
<td><p>5 MB</p></td>
<td><p>Dieser Schlüssel gibt die maximale Größe einer Transaktionsprotokolldatei an. Wenn die maximale Größe der Protokolldatei erreicht wird, wird eine neue Protokolldatei geöffnet.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseLoggingPath</em></p></td>
<td><p><code>%ExchangeInstallPath%TransportRoles\data\Queue</code></p></td>
<td><p>Dieser Schlüssel gibt das Standardverzeichnis für die Protokolldateien der Warteschlangendatenbank an. Anweisungen zum Ändern des Speicherorts der Warteschlangendatenbank finden Sie unter <a href="change-the-location-of-the-queue-database-exchange-2013-help.md">Ändern des Speicherorts der Warteschlangendatenbank</a>.</p></td>
</tr>
<tr class="odd">
<td><p><em>QueueDatabaseMaxBackgroundCleanupTasks</em></p></td>
<td><p>32</p></td>
<td><p>Dieser Schlüssel gibt die maximale Anzahl von Arbeitselementen der Hintergrundbereinigung an, die gleichzeitig in die Warteschlange des Datenbankmodul-Threadpools eingereiht sein können.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseOnlineDefragEnabled</em></p></td>
<td><p>True</p></td>
<td><p>Mit diesem Schlüssel wird eine geplante Onlinedefragmentierung der Nachrichtenwarteschlangen-Datenbank aktiviert oder deaktiviert. Dieser Schlüssel ist standardmäßig nicht in der Datei &quot;EdgeTransport.exe.config&quot; vorhanden.</p></td>
</tr>
<tr class="odd">
<td><p><em>QueueDatabaseOnlineDefragSchedule</em></p></td>
<td><p><code>1:00:00</code> oder 1:00 Uhr.</p></td>
<td><p>Dieser Schlüssel gibt die Tageszeit zum Starten der Onlinedefragmentierung der Nachrichtenwarteschlangen-Datenbank im 24-Stunden-Format an. Geben Sie den Wert als Zeitpunkt ein: <em>hh:MM:SS</em>, wobei <em>h</em> = Stunden, <em>M</em> = Minuten und <em>S</em> = Sekunden angibt.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueDatabaseOnlineDefragTimeToRun</em></p></td>
<td><p><code>3:00:00</code> oder 3 Stunden</p></td>
<td><p>Dieser Schlüssel gibt den Zeitraum an, in dem der Onlinedefragmentierungstask ausgeführt werden darf. Selbst wenn der Defragmentierungstask nicht in der angegebenen Zeit abgeschlossen wird, wird die Warteschlangendatenbank in einem konsistenten Zustand zurückgelassen. Geben Sie den Wert als Zeitraum ein: <em>hh:MM:SS</em>, wobei <em>h</em> = Stunden, <em>M</em> = Minuten und <em>S</em> = Sekunden angibt.</p></td>
</tr>
<tr class="odd">
<td><p><em>QueueDatabasePath</em></p></td>
<td><p><code>%ExchangeInstallPath%TransportRoles\data\Queue</code></p></td>
<td><p>Dieser Schlüssel gibt das Standardverzeichnis für die Dateien der Warteschlangendatenbank an. Anweisungen zum Ändern des Speicherorts der Warteschlangendatenbank finden Sie unter <a href="change-the-location-of-the-queue-database-exchange-2013-help.md">Ändern des Speicherorts der Warteschlangendatenbank</a>.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z.&nbsp;B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.



Zurück zum Seitenanfang

## Warteschlangeneigenschaften

Eine Warteschlange hat viele Eigenschaften, die ihren Zweck und Status beschreiben. Einige Warteschlangeneigenschaften werden beim Erstellen der Warteschlange angewendet und ändern sich nicht. Andere Eigenschaften geben Status, Größe, Zeit oder andere Indikatoren an, die häufig aktualisiert werden.

Zurück zum Seitenanfang

## NextHopSolutionKey

Das Ziel einer Nachricht wird von der Routingkomponente des Kategorisierungsmoduls im Microsoft Exchange-Transportdienst ausgewählt, und mithilfe dieses Ziels wird die Zustellungswarteschlange erstellt. Das Ziel wird für jeden Empfänger mit dem Attribut **NextHopSolutionKey** gekennzeichnet. Jeder eindeutige Wert des Attributs **NextHopSolutionKey** entspricht einer separaten Zustellungswarteschlange.

Das Attribut **NextHopSolutionKey** enthält die folgenden Felder:

  - **DeliveryType**   Der Wert dieses Felds stellt die Ergebnisse der Nachrichtenkategorisierung dar und gibt an, wie die Nachricht voraussichtlich vom Transportdienst an den nächsten Hop übermittelt wird. Dabei kann es sich um das endgültige Ziel der Nachricht oder einen Zwischenhop auf dem weiteren Weg handeln. Für **DeliveryType** wird vom Transportdienst eine vordefinierte Liste von Werten verwendet, die auf dem endgültigen Routingziel oder der Zustellungsgruppe basiert.

  - **NextHopDomain**   In diesem Feld werden besondere Werte verwendet, die auf dem Wert des Felds **DeliveryType** basieren. Bei Zustellungswarteschlangen entspricht der Wert dieses Felds praktisch dem Namen der Warteschlange. Der Wert von **NextHopDomain** ist nicht immer ein Domänenname. Der Wert könnte beispielsweise dem Namen des Active Directory-Zielstandorts oder der Database Availability Group (DAG) entsprechen. Stellen Sie sich dieses Feld als den Namen des nächsten Hops vor, wobei der Wert dem Namen des Routingziels oder der Zielzustellungsgruppe entspricht.

  - **NextHopConnector**   In diesem Feld werden besondere Werte verwendet, die auf dem Wert des Felds**DeliveryType** basieren. Der Wert wird immer als GUID ausgedrückt. Falls dieses Feld nicht verwendet wird, entspricht der Wert einer GUID, die nur aus Nullen besteht. Der Wert von **NextHopConnector** ist nicht immer die GUID eines Connectors. Der Wert könnte beispielsweise der GUID des Active Directory-Zielstandorts oder der DAG entsprechen. Stellen Sie sich dieses Feld als GUID des nächsten Hops vor, wobei der Wert der GUID des Routingziels oder der Zielzustellungsgruppe entspricht.

Auch die Eigenschaft **NextHopCategory** wird der Warteschlange von Exchange 2013 basierend auf dem Wert von **DeliveryType** hinzugefügt. Der Wert von **NextHopCategory** entspricht `External` oder `Internal`. Der Wert `External` gibt den nächsten Hop der Warteschlange außerhalb der Exchange-Organisation an. Der Wert `Internal` gibt den nächsten Hop der Warteschlange innerhalb der Exchange-Organisation an. Beachten Sie, dass für eine Nachricht an einen externen Empfänger unter Umständen ein oder mehrere interne Hops erforderlich sind, bevor sie extern zugestellt werden kann.

Die Werte von **DeliveryType**, **NextHopCategory**, **NextHopDomain** und **NextHopConnector** werden in der folgenden Tabelle beschrieben.


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Zustellungstyp in der Warteschlangenanzeige</th>
<th>&quot;DeliveryType&quot; in der Shell</th>
<th>Beschreibung</th>
<th>NextHopCategory</th>
<th>NextHopDomain</th>
<th>NextHopConnector</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Zustellungs-Agent</strong></p></td>
<td><p><strong>DeliveryAgent</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Empfänger in einem Nicht-SMTP-Adressbereich. Die Nachrichten werden mithilfe eines auf dem lokalen Server konfigurierten Zustellungs-Agent-Connectors zugestellt.</p></td>
<td><p>External</p></td>
<td><p>Dieser Wert entspricht dem Zieladressbereich, der für den Zustellungs-Agent-Connector konfiguriert ist.</p></td>
<td><p>Dieser Wert entspricht der GUID des Zustellungs-Agent-Connectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>DnsConnectorDelivery</strong></p></td>
<td><p><strong>DnsConnectorDelivery</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Empfänger in einem SMTP-Adressbereich. Die Nachrichten werden mithilfe eines auf dem lokalen Server konfigurierten Sendeconnectors zugestellt. Der Sendeconnector ist für die Verwendung von DNS-Routing konfiguriert.</p></td>
<td><p>External</p></td>
<td><p>Dieser Wert entspricht dem Zieladressbereich, der für den Sendeconnector konfiguriert ist. Beispiel: <code>contoso.com</code>.</p></td>
<td><p>Dieser Wert entspricht der GUID des Sendeconnectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NonSmtpGatewayDelivery</strong></p></td>
<td><p><strong>NonSmtpGatewayDelivery</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Empfänger in einem Nicht-SMTP-Adressbereich. Die Nachrichten werden mithilfe eines auf dem lokalen Server konfigurierten fremden Connectors zugestellt.</p></td>
<td><p>External</p></td>
<td><p>Dieser Wert entspricht dem Zieladressbereich, der für den fremden Connector konfiguriert ist.</p></td>
<td><p>Dieser Wert entspricht der GUID des fremden Connectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SmartHostConnectorDelivery</strong></p></td>
<td><p><strong>SmartHostConnectorDelivery</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Empfänger in einem SMTP-Adressbereich. Die Nachrichten werden mithilfe eines auf dem lokalen Server konfigurierten Sendeconnectors zugestellt. Der Sendeconnector ist für die Verwendung von Smarthostrouting konfiguriert.</p></td>
<td><p>External</p></td>
<td><p>Dieser Wert entspricht der Liste von Smarthosts, die für den Sendeconnector konfiguriert sind. Smarthosts können als FQDNs, IP-Adressen oder beides konfiguriert sein. Folgende Werte sind möglich:</p>
<ul>
<li><p><strong>FQDN</strong>   Die Syntax lautet <code>&lt;FQDN1,FQDN2,...&gt;</code>. Beispiel: <code>smarthost01.contoso.com</code> oder <code>smarthost01.contoso.com,smarthost02.fabrikam.com</code>.</p></li>
<li><p><strong>IP-Adresse</strong>   Die Syntax lautet <code>&lt;[IPAddress1],[IPAddress2],...&gt;</code>. Beispiel: <code>[10.10.10.100]</code> oder <code>[10.10.10.100],[10.10.10.101]</code>.</p></li>
<li><p><strong>FQDN und IP-Adresse</strong>   Die Syntax lautet <code>&lt;[IPAddress1],FQDN1,...&gt;</code> und hängt davon ab, wie die Smarthosts im Sendeconnector aufgelistet werden. Beispiel: <code>[172.17.17.7],relay.tailspintoys.com</code> oder <code>mail.contoso.com,[192.168.1.50]</code>.</p></li>
</ul></td>
<td><p>Dieser Wert entspricht der GUID des Sendeconnectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SMTP-Zustellung an Postfach</strong></p></td>
<td><p><strong>SmtpDeliveryToMailbox</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Exchange 2013-Postfachempfänger. Die Ziel-Postfachdatenbank befindet sich an einem der folgenden Speicherorte:</p>
<ul>
<li><p>Lokaler Exchange 2013-Postfachserver.</p></li>
<li><p>Exchange 2013-Postfachserver in derselben DAG.</p></li>
<li><p>Exchange 2013-Postfachserver an demselben Active Directory-Standort in Nicht-DAG-Umgebungen.</p></li>
</ul></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem Namen der Ziel-Postfachdatenbank. Beispiel: <code>Mailbox Database 0471695037</code>.</p></td>
<td><p>Dieser Wert entspricht der GUID der Ziel-Postfachdatenbank. Beispiel: <code>6dcb5a1e-0a88-4fc9-b8f9-634c34b1a123</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SMTP-Relay zu Sendeconnector-Quellservern</strong></p></td>
<td><p><strong>SmtpRelayToConnectorSourceServers</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an SMTP- oder Nicht-SMTP-Empfänger. Die Nachrichten werden mithilfe eines auf einem Remoteserver konfigurierten Sendeconnectors, Zustellungs-Agent-Connectors oder fremden Connectors zugestellt. Bei dem Remotetransportserver kann es sich um einen Exchange 2013-Postfachserver oder einen Exchange 2007- bzw. Exchange 2010-Hub-Transport-Server aus einer Vorgängerversion von Exchange handeln. Der Remoteserver kann sich am lokalen Active Directory-Standort oder an einem Active Directory-Remotestandort befinden.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem Namen des Zielsendeconnectors, Zustellungs-Agent-Connectors bzw. fremden Connectors. Beispiel: <code>Contoso.com Send Connector</code>.</p></td>
<td><p>Dieser Wert entspricht der GUID des Zielsendeconnectors, Zustellungs-Agent-Connectors bzw. fremden Connectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SMTP-Relay zur Database Availability Group</strong></p></td>
<td><p><strong>SmtpRelayToDag</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Exchange 2013-Postfachempfänger, wobei sich die Ziel-Postfachdatenbank in einer Remote-DAG befindet. Die Remote-DAG kann sich am lokalen Active Directory-Standort oder an einem Active Directory-Remotestandort befinden.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem Namen der Ziel-DAG. Beispiel: <code>DAG1</code>.</p></td>
<td><p>Dieser Wert entspricht der GUID der Ziel-DAG. Beispiel, <code>6dcb5a1e-0a88-4fc9-b8f9-634c34b1a123</code></p></td>
</tr>
<tr class="even">
<td><p><strong>SMTP-Relay zur Postfachzustellungsgruppe</strong></p></td>
<td><p><strong>SmtpRelayToMailboxDeliveryGroup</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an Legacypostfachempfänger, wobei sich das Zielpostfach auf einem Exchange 2007- oder Exchange 2010-Postfachserver befindet. Die Nachricht wird an einen Hub-Transport-Server weitergegeben, auf dem dieselbe Exchange-Version ausgeführt wird wie für das Zielpostfach. Der Ziel-Hub-Transport-Server kann sich am lokalen Active Directory-Standort oder an einem Active Directory-Remotestandort befinden.</p></td>
<td><p>Internal</p></td>
<td><p>Die Syntax des Warteschlangennamen lautet wie folgt: <code>Site:&lt;ADSiteName&gt;;Version:&lt;ExchangeVersion&gt;</code>, wobei <em>&lt;ADSiteName&gt;</em> dem Namen des Active Directory-Zielstandorts und <em>&lt;ExchangeVersion&gt;</em> der Exchange-Version auf dem Postfachserver entspricht.</p></td>
<td><p>Dieser Wert ist leer.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SMTP-Relay an einen Active Directory-Remotestandort</strong></p></td>
<td><p><strong>SmtpRelayToRemoteActiveDirectorySite</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an ein Remoteziel, und aufgrund der Routingtopologie muss die Nachricht über einen bestimmten Active Directory-Standort weitergeleitet werden. Der Standort ist ein Zwischenhop auf dem Weg zum endgültigen Ziel. Dieser Fall tritt unter folgenden Umständen ein:</p>
<ul>
<li><p>Die Nachricht muss über einen Hubstandort weitergeleitet werden.</p></li>
<li><p>Die Nachricht muss über einen Sendeconnector zugestellt werden, der auf einem Edge-Transport-Server mit abonniertem Active Directory-Remotestandort konfiguriert ist.</p></li>
</ul></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem Namen des Active Directory-Zielstandorts. Beispiel: <code>NorthAmericanSite</code>.</p></td>
<td><p>Dieser Wert entspricht der GUID des Active Directory-Zielstandorts. Beispiel: <code>bfd6c3df-5b65-8bfb-53f1f2c0d55c</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SMTP-Relay zu angegebenen Exchange-Servern</strong></p></td>
<td><p><strong>SmtpRelayToServers</strong></p></td>
<td><p>Die Warteschlangen enthält Nachrichten für die Zustellung an eine Verteilergruppe, die für einen bestimmten Server für die Aufgliederung der Verteilerlisten konfiguriert ist. Bei dem Server für die Aufgliederung der Verteilerlisten kann es sich um einen Exchange 2013-Postfachserver oder einen Exchange 2007- bzw. Exchange 2010-Hub-Transport-Server handeln. Der Server kann sich am lokalen Active Directory-Standort oder an einem Active Directory-Remotestandort befinden.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem FQDN des Zielservers für die Aufgliederung der Verteilerlisten. Beispiel: <code>mailbox01.contoso.com</code>.</p></td>
<td><p>Dieser Wert lautet <code>00000000-0000-0000-0000-000000000000</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SMTP-Relay in Active Directory-Standort zu Edge-Transport-Server</strong></p></td>
<td><p><strong>SmtpRelayWithinAdSiteToEdge</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten für die Zustellung an einen SMTP-Adressbereich. Die Nachrichten werden über einen Sendeconnector zugestellt, der auf einem Edge-Transport-Server mit abonniertem lokalem Active Directory-Standort konfiguriert ist.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem Namen des Sendeconnectors, über den ausgehende Nachrichten von der Organisation an das Internet gesendet werden. Dieser Sendeconnector wird vom Edge-Abonnement automatisch erstellt und <code>EdgeSync - &lt;ADSiteName&gt; to Internet</code> genannt. <em>&lt;ADSiteName&gt;</em> ist der Name des lokalen Active Directory-Standorts, der vom Edge-Transport-Server abonniert wurde.</p></td>
<td><p>Dieser Wert entspricht der GUID des Sendeconnectors. Beispiel: <code>4520e633-d83d-411a-bbe4-6a84648674ee</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Heartbeat</strong></p></td>
<td><p><strong>Heartbeat</strong></p></td>
<td><p>Dieser Wert ist für die interne Verwendung durch Microsoft reserviert. Weitere Informationen zum Taktsignal finden Sie unter <a href="shadow-redundancy-exchange-2013-help.md">Shadow-Redundanz</a>.</p></td>
<td><p>N/V</p></td>
<td><p>N/V</p></td>
<td><p>N/V</p></td>
</tr>
<tr class="odd">
<td><p><strong>Shadow-Redundanz</strong></p></td>
<td><p><strong>ShadowRedundancy</strong></p></td>
<td><p>Die Warteschlange enthält Nachrichten, die sich in einer Shadow-Warteschlange befinden. Eine Shadow-Warteschlange enthält redundante Kopien von Nachrichten, die gerade übermittelt werden, für den Fall, dass die Zustellung nicht erfolgreich ist. Weitere Informationen finden Sie unter <a href="shadow-redundancy-exchange-2013-help.md">Shadow-Redundanz</a>.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert entspricht dem FQDN des primären Servers, für den die Shadow-Warteschlange redundante Kopien der primären Nachrichten enthält. Beispiel: <code>mailbox01.contoso.com</code>.</p></td>
<td><p>Dieser Wert lautet <code>00000000-0000-0000-0000-000000000000</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Undefined</strong></p></td>
<td><p><strong>Undefined</strong></p></td>
<td><p>Dieser Wert wird nur für die Zustellungswarteschlange und die Warteschlange für nicht verarbeitete Nachrichten verwendet.</p></td>
<td><p>Internal</p></td>
<td><p>Für die Übermittlungswarteschlange lautet dieser Wert <code>Submisssion</code>. Für die Warteschlange für nicht verarbeitete Nachrichten lautet dieser Wert <code>Poison Message</code>.</p></td>
<td><p>Dieser Wert lautet <code>00000000-0000-0000-0000-000000000000</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nicht erreichbar</strong></p></td>
<td><p><strong>Unreachable</strong></p></td>
<td><p>Dieser Wert wird nur für die Nicht-erreichbar-Warteschlange verwendet.</p></td>
<td><p>Internal</p></td>
<td><p>Dieser Wert lautet <code>Unreachable Domain</code>.</p></td>
<td><p>Dieser Wert lautet <code>00000000-0000-0000-0000-000000000000</code>.</p></td>
</tr>
</tbody>
</table>


Beachten Sie, dass ältere **DeliveryType**-Werte von Exchange 2013 unterstützt werden, da es mit Vorgängerversionen von Exchange rückwärts kompatibel ist. Diese Werte stehen in der Warteschlangenanzeige und in der Shell zur Verfügung, werden von Exchange 2013 jedoch nicht verwendet. Diese älteren **DeliveryType**-Werte lauten wie folgt:

  - **MapiDelivery**   Die Warteschlange enthält Nachrichten für die Zustellung über einen Exchange 2007- oder Exchange 2010-Hub-Transport-Server an ein Postfach auf einem Exchange 2007- oder Exchange 2010-Postfachserver am lokalen Active Directory-Standort.

  - **SmtpRelayWithinAdSite**   Die Warteschlange enthält Nachrichten für die Zustellung über einen Exchange 2007- oder Exchange 2010-Hub-Transport-Server an einen anderen Hut-Transport-Server am selben Active Directory-Standort. Der Ziel-Hub-Transport-Server kann der Quellserver für einen Connector oder ein Server für die Aufgliederung der Verteilerliste einer Verteilergruppe sein.

  - **SmtpRelaytoTiRg**   Die Warteschlange enthält Nachrichten für die Zustellung über einen Exchange 2007- oder Exchange 2010-Hub-Transport-Server an eine Exchange Server 2003-Routinggruppe. Der Zielserver kann der Quellserver für einen Connector, ein Server für die Aufgliederung der Verteilerliste einer Verteilergruppe oder ein Exchange 2003-Bridgeheadserver sein.

Zurück zum Seitenanfang

## IncomingRate, OutgoingRate und Velocity

Die Raten der eingehenden und ausgehenden Nachrichten einer Warteschlange werden von Exchange 2013 ermittelt und in Warteschlangeneigenschaften gespeichert. Sie können diese Raten als Indikator für die Warteschlangen- und Transportserverintegrität verwenden. Die Eigenschaften lauten wie folgt:

  - **IncomingRate**   Diese Eigenschaft gibt die Rate an, mit der Nachrichten bei der Warteschlange eingehen.
    
    Dieser Wert ergibt sich aus der Anzahl der Nachrichten, die im Durchschnitt in den letzten 60 Sekunden alle 5 Sekunden bei der Warteschlange eingegangen sind. Die Formel kann durch `(i1+i2+i3+i4+i5+i6)/6` ausgedrückt werden, wobei i*n* der Anzahl der Nachrichten entspricht, die innerhalb von 5 Sekunden eingehen.

  - **OutgoingRate**   Diese Eigenschaft gibt die Rate an, mit der Nachrichten die Warteschlange verlassen.
    
    Dieser Wert ergibt sich aus der Anzahl der Nachrichten, die die Warteschlange im Durchschnitt in den letzten 60 Sekunden alle 5 Sekunden verlassen haben. Die Formel kann durch `(o1+o2+o3+o4+o5+o6)/6` ausgedrückt werden, wobei i*n* der Anzahl der Nachrichten entspricht, die innerhalb von 5 Sekunden ausgehen.

  - **Velocity**   Diese Eigenschaft gibt die Entleerungsrate der Warteschlange an und ergibt sich aus der Subtraktion des Werts für **IncomingRate** vom Wert für **OutgoingRate**.
    
    Wenn der Wert für **Velocity** größer als 0 ist, verlassen Nachrichten die Warteschlange schneller als dass sie bei ihr eingehen.
    
    Wenn der Wert für **Velocity** gleich 0 ist, verlassen Nachrichten die Warteschlange genauso schnell wie sie bei ihr eingehen. Dieser Wert wird auch angezeigt, wenn die Warteschlange inaktiv ist.
    
    Wenn der Wert für **Velocity** kleiner als 0 ist, gehen Nachrichten schneller bei der Warteschlange ein als dass sie sie verlassen.

Grundlegend lässt ein positiver **Velocity**-Wert auf eine fehlerfreie Warteschlange mit effizienter Entleerung schließen, während ein negativer **Velocity**-Wert auf eine Warteschlange hinweist, die nicht effizient entleert wird. Sie müssen jedoch auch die Werte für die Eigenschaften **IncomingRate**, **OutgoingRate** und **MessageCount** sowie die Größe des **Velocity**-Werts für die Warteschlange berücksichtigen. Beispielsweise sind ein großer negativer Wert für **Velocity**, ein großer Wert für **MessageCount**, ein kleiner Wert für **OutgoingRate** und ein großer Wert für **IncominRate** genaue Indikatoren dafür, dass die betreffende Warteschlange nicht richtig entleert wird. Eine Warteschlange mit einem gegen null gehenden negativen **Velocity**-Wert und ebenfalls sehr kleinen Werten für **IncomingRate**, **OutgoingRate** und **MessageCount** weist jedoch nicht auf Probleme mit der Warteschlange hin.

Zurück zum Seitenanfang

## Warteschlangenstatus

Der aktuelle Status einer Warteschlange wird in der **Status**-Eigenschaft der Warteschlange gespeichert. Eine Warteschlange kann einen der folgenden Statuswerte aufweisen:

  - **Aktiv**   Nachrichten werden aktiv von der Warteschlange übertragen.

  - **Verbindung wird hergestellt**   Es wird gerade eine Verbindung von der Warteschlange zum nächsten Hop hergestellt.

  - **Bereit**   Es wurden vor kurzem Nachrichten von der Warteschlangen übertragen, aber jetzt ist sie leer.

  - **Wiederholen**   Der letzte automatische oder manuelle Verbindungsversuch ist fehlgeschlagen, und die Warteschlange wartet darauf, einen neuen Verbindungsversuch zu unternehmen.

  - **Angehalten**   Die Warteschlange wurde von einem Administrator manuell angehalten, um die Zustellung von Nachrichten zu verhindern. Es können neue Nachrichten in die Warteschlange eingereiht werden, und Nachrichten, die gerade an den nächsten Hop übertragen werden, werden fertig zugestellt und aus der Warteschlange entfernt. Anderenfalls verlassen Nachrichten die Warteschlange erst dann, wenn sie von einem Administrator manuell fortgesetzt wird. Beachten Sie, dass das Anhalten einer Warteschlange keinen Einfluss auf den Status der einzelnen darin enthaltenen Nachrichten hat.
    
    Sie können eine Warteschlange anhalten, die den Status Aktiv oder Wiederholen aufweist. Auch die Nicht-erreichbar-Warteschlange und die Übermittlungswarteschlange können angehalten werden.
    
    Wenn Sie die Nicht-erreichbar-Warteschlange anhalten und Konfigurationsaktualisierungen erkannt werden, erfolgt keine automatische Neuübermittlung von Nachrichten an das Kategorisierungsmodul. Sie müssen die Nicht-erreichbar-Warteschlange manuell fortsetzen, damit diese Nachrichten automatisch neu übermitteln werden. Wenn die Übermittlungswarteschlange angehalten wird, werden vom Kategorisierungsmodul erst wieder Nachrichten abgeholt, wenn die Warteschlange fortgesetzt wird.

Zurück zum Seitenanfang

## Weitere Warteschlangeneigenschaften

Es gibt weitere Warteschlangeneigenschaften, die selbsterklärend sind. Sie können die meisten Warteschlangeneigenschaften als Filteroptionen verwenden. Durch die Angabe von Filterkriterien können Sie Warteschlangen schnell finden und Aktionen darauf anwenden. Eine vollständige Beschreibung der filterbaren Warteschlangeneigenschaften finden Sie unter [Warteschlangenfilter](queue-filters-exchange-2013-help.md).

Ebenfalls wichtig und erwähnenswert ist die Warteschlangeneigenschaft **MessageCount**, die die Anzahl der Nachrichten in einer Warteschlange anzeigt. Diese Eigenschaft ist ein wichtiger Indikator für die Warteschlangenintegrität. Wenn beispielsweise eine Zustellungswarteschlange, die eine große Anzahl von Nachrichten enthält, immer weiter wächst, ohne jemals kleiner zu werden, könnte dies auf ein Problem mit dem Routing oder der Transportpipeline hindeuten, das Ihrer Aufmerksamkeit bedarf.

Zurück zum Seitenanfang

## Nachrichteneigenschaften

Eine Nachricht in einer Warteschlange hat viele Eigenschaften. Viele der Eigenschaften spiegeln die Informationen wider, die zum Erstellen der Nachricht verwendet wurden. Einige der Nachrichtenstatus und Informationseigenschaften werden stark von entsprechenden Eigenschaften der Warteschlange beeinflusst. Allerdings kann eine Nachricht einen anderen Wert aufweisen als die entsprechende Eigenschaft der Warteschlange. Andere Eigenschaften umfassen Status-, Zeit- oder andere Indikatoren, die häufig aktualisiert werden.

Zurück zum Seitenanfang

## Nachrichtenstatus

Der aktuelle Status einer Nachricht wird in der **Status**-Eigenschaft der Nachricht gespeichert. Eine Nachricht kann einen der folgenden Statuswerte aufweisen:

  - **Aktiv   **Wenn die Nachricht sich in einer Zustellungswarteschlange befindet, wird die Nachricht an ihr Ziel zugestellt. Wenn die Nachricht sich in der Übermittlungswarteschlange befindet, wird sie vom Kategorisierungsmodul verarbeitet.

  - **Gesperrt**   Dieser Wert ist für die interne Verwendung durch Microsoft reserviert und wird nicht in lokalen Exchange-Organisationen verwendet.

  - **PendingRemove**   Die Nachricht wurde vom Administrator gelöscht, doch hatte ihre Übermittlung an den nächsten Hop bereits begonnen. Die Nachricht wird gelöscht, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.

  - **PendingSuspend**   Die Nachricht wurde vom Administrator angehalten, doch hatte ihre Übermittlung an den nächsten Hop bereits begonnen. Die Nachricht wird angehalten, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.

  - **Bereit**   Die Nachricht befindet sich in der Warteschlange und ist zur Verarbeitung bereit.

  - **Wiederholen**   Der letzte automatische oder manuelle Verbindungsversuch für die Warteschlange, in der sich die Nachricht befindet, ist fehlgeschlagen. Die Nachricht wartet auf den nächsten automatischen Verbindungsversuch der Warteschlange.

  - **Angehalten**   Die Nachricht wurde vom Administrator manuell angehalten. Alle Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten befinden sich in einem dauerhaft angehaltenen Zustand.

Zurück zum Seitenanfang

## Weitere Nachrichteneigenschaften

Es gibt weitere Nachrichteneigenschaften, die selbsterklärend sind. Sie können die meisten Nachrichteneigenschaften als Filteroptionen verwenden. Durch Angeben von Filterkriterien können Nachrichten schnell gefunden und entsprechende Aktionen für sie eingeleitet werden. Eine vollständige Beschreibung der filterbaren Nachrichteneigenschaften finden Sie unter [Nachrichtenfilter](message-filters-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verwalten von Warteschlangen und Nachrichten in Warteschlangen

Die Warteschlangenanzeige und praktisch alle Warteschlangen- und Nachrichtenverwaltungs-Cmdlets sind auf lediglich einen Exchange-Server beschränkt. Sie können einzelne oder mehrere Warteschlangen oder Nachrichten anzeigen oder bearbeiten, aber nur auf einem bestimmten Server.

In Exchange 2013 wird das Cmdlet **Get-QueueDigest** eingeführt, mit dem eine aggregierte Übersicht der Warteschlangenstatus auf allen Servern innerhalb eines bestimmten Bereichs bereitgestellt wird, z. B. in einer DAG, an einem Active Directory-Standort, in einer Serverliste oder innerhalb der Active Directory-Gesamtstruktur. Beachten Sie, dass Warteschlangen auf einem abonnierten Edge-Transport-Server im Umkreisnetzwerk nicht in den Ergebnissen enthalten sind. Zudem ist **Get-QueueDigest** zwar auf einem Edge-Transport-Server verfügbar, aber die Ergebnisse sind auf die Warteschlangen auf dem Edge-Transport-Server beschränkt.


> [!NOTE]
> Standardmäßig zeigt das <STRONG>Get-QueueDigest</STRONG>-Cmdlet Zustellungswarteschlangen an, die zehn oder mehr Nachrichten enthalten und deren Ergebnisse zwischen ein und zwei Minuten alt sind. Anweisungen zum Ändern der Standardwerte finden Sie unter <A href="configure-get-queuedigest-exchange-2013-help.md">Konfigurieren von Get-QueueDigest</A>.



In der folgenden Tabelle werden die Verwaltungsaufgaben beschrieben, die Sie für Warteschlangen oder Nachrichten in Warteschlangen ausführen können.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Task</th>
<th>Beschreibung</th>
<th>Zu verwendendes Tool</th>
<th>Anweisungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Warteschlangen auf einem Server anzeigen und filtern</p></td>
<td><p>Mit dieser Aktion werden eine oder mehrere Warteschlangen auf einem Transportserver angezeigt. Anhand der Ergebnisse können Sie Maßnahmen für die Warteschlangen ergreifen.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Get-Queue</strong>-Cmdlet.</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="even">
<td><p>Warteschlangen auf bestimmten Servern in bestimmten DAGs, an bestimmten Active Directory-Standorten oder innerhalb der Active Directory-Gesamtstruktur anzeigen und filtern.</p></td>
<td><p>Mit dieser Aktion wird eine Zusammenfassungsansicht der Warteschlangen innerhalb eines definierten Bereichs (Server, DAGs, Active Directory-Standort oder Active Directory-Gesamtstruktur) angezeigt.</p></td>
<td><p>Nur <strong>Get-QueueDigest</strong>-Cmdlet</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="odd">
<td><p>Warteschlangen anhalten</p></td>
<td><p>Mit dieser Aktion wird die Zustellung von Nachrichten, die sich gegenwärtig in der Warteschlange befinden, vorübergehend verhindert. Die Warteschlange nimmt weiter neue Nachrichten auf, ohne dass Nachrichten die Warteschlange verlassen.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Suspend-Queue</strong>-Cmdlet.</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="even">
<td><p>Warteschlangen fortsetzen</p></td>
<td><p>Mit dieser Aktion wird das Anhalten von Warteschlangen aufgehoben und die Zustellung der darin enthaltenen Nachrichten wieder aufgenommen.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Resume-Queue</strong>-Cmdlet.</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="odd">
<td><p>Warteschlangen wiederholen</p></td>
<td><p>Mit dieser Aktion wird sofort versucht, eine Verbindung zum nächsten Hop herzustellen. Wenn keine Verbindung zum nächsten Hop hergestellt werden kann, wird der Verbindungsversuch ohne manuellen Eingriff in bestimmten Zeitintervallen eine bestimmte Anzahl von Malen wiederholt.</p>
<p>Mit jedem Verbindungsversuch wird der nächste Wiederholungszeitpunkt zurückgesetzt, unabhängig davon, ob der Verbindungsversuch manuell oder automatisch erfolgt. Weitere Informationen finden Sie unter <a href="message-retry-resubmit-and-expiration-intervals-exchange-2013-help.md">Wiederholungsintervalle, Intervalle für die erneute Übermittlung und Ablaufintervalle für Nachrichten</a>.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Retry-Queue</strong>-Cmdlet.</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichten in Warteschlangen erneut übermitteln</p></td>
<td><p>Mit dieser Aktion werden Nachrichten in der Warteschlange erneut an die Übermittlungswarteschlange gesendet und müssen noch einmal den Kategorisierungsprozess durchlaufen.</p></td>
<td><p><strong>Retry-Queue</strong> mit dem Parameter <em>Resubmit</em></p>
<p>Beachten Sie, dass Sie zum erneuten Übermitteln von Nachrichten die Warteschlangenanzeige verwenden können, aber nur über die Warteschlange für nicht verarbeitete Nachrichten. Zum erneuten Übermitteln einer Nachricht in der Warteschlange für nicht verarbeitete Nachrichten setzen Sie die Nachricht in der Warteschlangenanzeige fort oder verwenden das Cmdlet <strong>Resume-Message</strong>.</p></td>
<td><p><a href="manage-queues-exchange-2013-help.md">Verwalten von Warteschlangen</a></p></td>
</tr>
<tr class="odd">
<td><p>Nachrichten in Warteschlangen anhalten</p></td>
<td><p>Mit dieser Aktion wird die Zustellung von Nachrichten vorübergehend verhindert. Über diese Aktion können Sie die Zustellung einer Nachricht an alle Empfänger in einer bestimmten Warteschlange oder an alle Empfänger in allen Warteschlangen anhalten.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Suspend-Message</strong>-Cmdlet.</p></td>
<td><p><a href="manage-messages-in-queues-exchange-2013-help.md">Verwalten von Nachrichten in Warteschlangen</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichten in Warteschlangen fortsetzen</p></td>
<td><p>Mit dieser Aktion wird das Anhalten von Nachrichten aufgehoben und die Zustellung der in Warteschlangen eingereihten Nachrichten wieder aufgenommen. Über diese Aktion können Sie die Zustellung einer Nachricht an alle Empfänger in einer bestimmten Warteschlange oder an alle Empfänger in allen Warteschlangen fortsetzen.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Resume-Message</strong>-Cmdlet.</p></td>
<td><p><a href="manage-messages-in-queues-exchange-2013-help.md">Verwalten von Nachrichten in Warteschlangen</a></p></td>
</tr>
<tr class="odd">
<td><p>Nachrichten aus Warteschlangen entfernen</p></td>
<td><p>Mit dieser Aktion wird die Zustellung von Nachrichten permanent verhindert. Über diese Aktion können Sie die Zustellung einer Nachricht an beliebige Empfänger in einer angegebenen Warteschlange oder an alle Empfänger in allen Warteschlangen verhindern. Sie können diese Aktion auch so konfigurieren, dass ein Unzustellbarkeitsbericht an den Absender gesendet wird, wenn die Nachricht entfernt wird.</p></td>
<td><p>Warteschlangenanzeige oder <strong>Remove-Message</strong>-Cmdlet.</p></td>
<td><p><a href="manage-messages-in-queues-exchange-2013-help.md">Verwalten von Nachrichten in Warteschlangen</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichten aus Warteschlangen exportieren</p></td>
<td><p>Mit dieser Aktion werden Nachrichten in den angegebenen Dateipfad kopiert. Die Nachrichten werden nicht aus der Warteschlange gelöscht, sondern es wird eine Kopie der Nachricht an einem Dateispeicherort gespeichert. Dadurch können Administratoren oder andere Unternehmensverantwortliche die Nachrichten später untersuchen. Bevor Sie Nachrichten exportieren, müssen Sie sie in der Warteschlange anhalten, damit die normale Zustellung während des Exportvorgangs nicht fortgesetzt wird.</p></td>
<td><p>Nur <strong>Export-Message</strong>-Cmdlet.</p></td>
<td><p><a href="export-messages-from-queues-exchange-2013-help.md">Nachrichten aus Warteschlangen exportieren</a></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

