---
title: 'Verwalten v. Warteschl. mit Exchange-Verwaltungsshell: Exchange 2013-HIlfe'
TOCTitle: Verwenden der Exchange-Verwaltungsshell zum Verwalten von Warteschlangen
ms:assetid: 5433c1d3-ad2e-4f82-b50d-b67964b32f26
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998047(v=EXCHG.150)
ms:contentKeyID: 51409296
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwenden der Exchange-Verwaltungsshell zum Verwalten von Warteschlangen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Wie in früheren Versionen von Exchange können Sie mithilfe der Exchange-Verwaltungsshell in Microsoft Exchange Server 2013 Informationen zu Warteschlangen und zu den darin enthaltenen Nachrichten anzeigen und Verwaltungsaktionen für Warteschlangen und Nachrichten durchführen. In Exchange 2013 sind Warteschlangen auf Postfachservern und Edge-Transport-Servern vorhanden. In diesem Thema werden diese Server als *Transportserver* bezeichnet.

Wenn Sie die Shell zum Anzeigen und Verwalten von Warteschlangen und Nachrichten in Warteschlangen auf Transportservern verwenden, müssen Sie wissen, wie die zu verwaltenden Warteschlangen oder Nachrichten identifiziert werden können. Normalerweise enthalten Transportserver eine große Anzahl von Warteschlangen und Nachrichten für die Zustellung. Sie verwenden die in den Cmdlets für die Warteschlangen- und Nachrichtenverwaltung verfügbaren Filterparameter für die Identifikation von Warteschlangen und Nachrichten, die Sie anzeigen oder verwalten möchten.

Beachten Sie, dass Sie auch die Warteschlangenanzeige in der Exchange-Toolbox für die Verwaltung von Warteschlangen und Nachrichten in Warteschlangen verwenden können. Die Cmdlets für die Warteschlangen- und Nachrichtenanzeige unterstützen jedoch mehr filterbare Eigenschaften und Filteroptionen als die Warteschlangenanzeige. Weitere Informationen zur Verwendung der Warteschlangenanzeige finden Sie unter [Warteschlangenanzeige](queue-viewer-exchange-2013-help.md).

**Inhalt**

  - Queue filtering parameters
    
      - Queue identity
    
      - Queue Filter parameter
    
      - Include and Exclude parameters

  - Get-QueueDigest

  - Message filtering parameters
    
      - Message identity
    
      - Message Filter parameter
    
      - Queue parameter

  - Comparison operators to use when filtering queues or messages

  - Advanced paging parameters

## Parameter zur Warteschlangenfilterung

In der folgenden Tabelle werden die Filterparameter beschrieben, die in den Cmdlets zur Warteschlangenverwaltung verfügbar sind.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Filterparameter</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Get-Queue</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p>
<p><em>Include</em></p>
<p><em>Exclude</em></p></td>
<td><p>Der Parameter <em>Identity</em> kann nicht innerhalb desselben Befehls verwendet werden wie der Parameter <em>Filter</em>. Die Parameter <em>Include</em> und <em>Exclude</em> können nicht innerhalb desselben Befehls verwendet werden wie der Parameter <em>Filter</em>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Resume-Queue</strong></p>
<p><strong>Retry-Queue</strong></p>
<p><strong>Suspend-Queue</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p></td>
<td><p>Sie müssen entweder den Parameter <em>Identity</em> oder den Parameter <em>Filter</em> verwenden, können jedoch nicht beide in demselben Befehl einsetzen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Get-QueueDigest</strong></p></td>
<td><p><em>Server</em></p>
<p><em>Dag</em></p>
<p><em>Site</em></p>
<p><em>Forest</em></p>
<p><em>Filter</em></p></td>
<td><p>Sie müssen den Parameter <em>Server</em>, <em>Dag</em>, <em>Site</em> oder <em>Forest</em> verwenden, können jedoch keinen davon in demselben Befehl kombinieren. Sie können den Parameter <em>Filter</em> mit allen übrigen Filterparametern verwenden.</p></td>
</tr>
</tbody>
</table>


Beachten Sie, dass ein Parameter *Server* für alle Cmdlets zur Warteschlangenverwaltung verfügbar ist. Im Cmdlet **Get-QueueDigest** ist der Parameter *Server* ein Bereichsparameter, der den oder die Server angibt, auf dem bzw. denen Sie Zusammenfassungsinformationen zu Warteschlangen anzeigen möchten. In allen übrigen Cmdlets zur Warteschlangenverwaltung verwenden Sie den Parameter *Server* zum Herstellen einer Verbindung mit einem bestimmten Server und führen die Befehle zur Warteschlangenverwaltung auf dem jeweiligen Server aus. Sie können den Parameter *Server* mit dem oder ohne den Parameter *Filter* verwenden. Der Parameter *Server* kann jedoch nicht mit dem Parameter *Identity* zusammen verwendet werden. Der Hostname oder der FQDN des Transportservers wird mit dem Parameter *Server* verwendet.

Zurück zum Seitenanfang

## Warteschlangenidentität

Der Parameter *Identity* in den Cmdlets für die Warteschlangenverwaltung bezeichnet eine bestimmte Warteschlange. Wenn Sie den Parameter *Identity* einsetzen, können Sie keine weiteren Parameter zur Warteschlangenfilterung angeben, da Sie die Warteschlange bereits eindeutig bezeichnet haben. Der Parameter *Identity* verwendet die grundlegende Syntax *\<Server\>*\\*\<Warteschlange\>*.

Der Platzhalter *\<Server\>* steht für den Hostnamen oder den FQDN des Exchange-Servers, z. B. `mailbox01` oder `mailbox01.contoso.com`. Wenn Sie den Bezeichner *\<Server\>* auslassen, wird der lokale Server angenommen.

Der Platzhalter \<*Warteschlange*\> nimmt einen der folgenden Werte an:

  - **Name einer beständigen Warteschlange**   Beständige Warteschlangen besitzen eindeutige, konsistente Namen auf allen Postfach- oder Edge-Transport-Servern. Die Namen beständiger Warteschlangen lauten:
    
      - **Übermittlung**   Die Warteschlange mit Nachrichten, die auf die Verarbeitung durch das Kategorisierungsmodul warten.
    
      - **Nicht erreichbar**   Diese Warteschlange enthält Nachrichten, die nicht weitergeleitet werden können. Diese Warteschlange ist nur dann vorhanden, wenn sich Nachrichten darin befinden.
    
      - **Nicht verarbeitbare Nachrichten**   Diese Warteschlange enthält Nachrichten, die als möglicherweise schädlich für den Exchange-Server ermittelt wurden. Diese Warteschlange ist nur dann vorhanden, wenn sich Nachrichten darin befinden.

  - **Name einer Zustellungswarteschlange**   Der Name einer Zustellungswarteschlange entspricht dem Wert der Warteschlangeneigenschaft **NextHopDomain**. Beispielsweise kann der Warteschlangenname dem Adressraum eines Sendeconnectors, dem Namen eines Active Directory-Standorts oder dem Namen einer DAG entsprechen. Weitere Informationen finden Sie im Abschnitt "NextHopSolutionKey" im Thema [Warteschlangen](queues-exchange-2013-help.md).

  - **Warteschlangenganzzahl**   Zustellungswarteschlangen und Shadow-Warteschlangen wird in der Warteschlangendatenbank ein eindeutiger Ganzzahlwert zugewiesen. Allerdings müssen Sie das Cmdlet **Get-Queue** ausführen, um den Ganzzahlwert für die Warteschlange in der Eigenschaft **Identity** oder **QueueIdentity** zu finden.

  - **Name einer Shadow-Warteschlange**   Eine Shadow-Warteschlange verwendet die Syntax `Shadow\`*\<Warteschlangenganzzahl\>*.

In der folgenden Tabelle wird die Syntax zusammengefasst, die Sie mit dem Parameter *Identity* in den Cmdlets für die Warteschlangenverwaltung verwenden können. In allen Werten bezeichnet *\<Server\>* den Hostnamen oder den FQDN des Servers.

### Formate der Warteschlangenidentität

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert des Identity-Parameters</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;PersistentQueueName&gt;</code> oder <code>&lt;PersistentQueueName&gt;</code></p></td>
<td><p>Eine beständige Warteschlange auf dem angegebenen oder dem lokalen Server.</p>
<p><em>&lt;PersistentQueueName&gt;</em> ist <code>Submission</code>, <code>Unreachable</code> oder <code>Poison</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\&lt;NextHopDomain&gt;</code> oder <code>&lt;NextHopDomain&gt;</code></p></td>
<td><p>Eine Zustellungswarteschlange auf dem angegebenen oder dem lokalen Server.</p>
<p><em>&lt;NextHopDomain&gt;</em> ist ein Routingziel oder eine Zustellungsgruppe für die Nachrichten in der Warteschlange. Weitere Informationen finden Sie im Abschnitt &quot;NextHopSolutionKey&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
</tr>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;QueueInteger&gt;</code> oder <code>&lt;QueueInteger&gt;</code></p></td>
<td><p>Eine Zustellungswarteschlange auf dem angegebenen oder dem lokalen Server.</p>
<p><em>&lt;QueueInteger&gt;</em> ist der eindeutige Ganzzahlwert der Warteschlange, der in der Eigenschaft <strong>Identity</strong> des Cmdlets <strong>Get-Queue</strong> angezeigt wird.</p></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\Shadow\&lt;QueueInteger&gt;</code> oder <code>Shadow\&lt;QueueInteger&gt;</code></p></td>
<td><p>Eine Shadow-Warteschlange auf dem angegebenen oder dem lokalen Server.</p></td>
</tr>
<tr class="odd">
<td><p><code>&lt;Server&gt;\*</code> oder <code>*</code></p></td>
<td><p>Alle Warteschlange auf dem angegebenen oder dem lokalen Server. Beachten Sie, dass diese Werte nur mit dem Cmdlet <strong>Get-Queue</strong> verwendet werden können.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Parameter zur Warteschlangenfilterung

Den Parameter *Filter* können Sie für alle Cmdlets zur Warteschlangenverwaltung verwenden, um die anzuzeigenden oder zu verwaltenden Warteschlangen basierend auf ihren Eigenschaften anzugeben. Der Parameter *Filter* erstellt einen Ausdruck mit Vergleichsoperatoren, der die Warteschlangenoperation auf Warteschlangen einschränkt, die den Filterkriterien entsprechen. Sie können den logischen Operator `-and` verwenden, um mehrere Bedingungen anzugeben, denen die Ergebnisse entsprechen sollen.

Eine vollständige Liste mit Warteschlangeneigenschaften, die Sie mit dem Parameter *Filter* verwenden können, finden Sie unter [Warteschlangen](queues-exchange-2013-help.md).

Eine Liste mit Vergleichsoperatoren, die mit dem Parameter *Filter* verwendet werden können, finden Sie im Abschnitt Comparison operators to use when filtering queues or messages in diesem Thema.

Beispiele für Vorgehensweisen, die den Parameter *Filter* zum Anzeigen und Verwalten von Warteschlangen verwenden, finden Sie unter [Verwalten von Warteschlangen](manage-queues-exchange-2013-help.md).

Zurück zum Seitenanfang

## Einschließen und Ausschließen von Parametern

In Exchange 2013 stehen die Parameter *Include* und *Exclude* im Cmdlet `Get-Queue` zur Verfügung. Sie können diese Parameter einzeln, zusammen und mit dem Parameter *Filter* einsetzen, um Ihre Abfrageergebnisse auf dem lokalen oder dem angegebenen Transportserver zu optimieren. Sie verfügen über folgende Möglichkeiten:

  - Ausschließen leerer Warteschlangen aus den Ergebnissen.

  - Ausschließen von Warteschlangen für externe Ziele aus den Ergebnissen.

  - Einbeziehen von Warteschlangen, die in den Ergebnissen einen bestimmten Wert für **DeliveryType** aufweisen.

Die Parameter *Include* und *Exclude* verwenden zum Filtern von Warteschlangen die folgenden Warteschlangeneigenschaften:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
<th>Beispiel für Shellcode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>DeliveryType</code></p></td>
<td><p>Dieser Wert schließt Warteschlangen basierend auf der Eigenschaft <strong>DeliveryType</strong> ein oder aus. Mehrere Werte können durch Kommata getrennt angegeben werden. Die gültigen Werte für <strong>DeliveryType</strong> werden im Abschnitt &quot;NextHopSolutionKey&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a> erläutert.</p></td>
<td><p>In diesem Beispiel werden alle Zustellungswarteschlangen auf dem lokalen Server zurückgegeben, bei deren nächsten Hop es sich um einen Sendeconnector auf dem lokalen Server handelt, der für das Smarthostrouting konfiguriert ist:</p>
<p><code>Get-Queue -Include SmartHostConnectorDelivery</code></p></td>
</tr>
<tr class="even">
<td><p><code>Empty</code></p></td>
<td><p>Dieser Wert schließt leere Warteschlangen ein oder aus. Leere Warteschlangen weisen den Wert <code>0</code> in der Eigenschaft <strong>MessageCount</strong> auf.</p></td>
<td><p>Dieses Beispiel gibt alle Warteschlangen auf dem lokalen Server zurück, die Nachrichten enthalten.</p>
<p><code>Get-Queue -Exclude Empty</code></p></td>
</tr>
<tr class="odd">
<td><p><code>External</code></p></td>
<td><p>Dieser Wert schließt Warteschlangen ein oder aus, deren Eigenschaft <strong>NextHopCategory</strong> den Wert <code>External</code> aufweist.</p>
<p>Externe Warteschlangen weisen immer einen der folgenden Werte für <strong>DeliveryType</strong> auf:</p>
<ul>
<li><p><code>DeliveryAgent</code></p></li>
<li><p><code>DnsConnectorDelivery</code></p></li>
<li><p><code>NonSmtpGatewayDelivery</code></p></li>
<li><p><code>SmartHostConnectorDelivery</code></p></li>
</ul>
<p>Weitere Informationen finden Sie im Abschnitt &quot;NextHopSolutionKey&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
<td><p>In diesem Beispiel werden alle internen Warteschlangen auf dem lokalen Server zurückgegeben</p>
<p><code>Get-Queue -Exclude External</code></p></td>
</tr>
<tr class="even">
<td><p><code>Internal</code></p></td>
<td><p>Dieser Wert schließt Warteschlangen ein oder aus, deren Eigenschaft <strong>NextHopCategory</strong> den Wert <code>Internal</code> aufweist. Weitere Informationen finden Sie im Abschnitt &quot;NextHopSolutionKey&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></td>
<td><p>In diesem Beispiel werden alle internen Warteschlangen auf dem lokalen Server zurückgegeben.</p>
<p><code>Get-Queue -Include Internal</code></p></td>
</tr>
</tbody>
</table>


Beachten Sie, dass Sie die Funktionalität der Parameter *Include* und *Exclude* verdoppeln können, indem Sie den Parameter *Filter* einsetzen. Beispielsweise erzielt der Befehl `Get-Queue -Exclude Empty` dasselbe Ergebnis wie `Get-Queue -Filter {MessageCount -gt 0}`. Die Syntax der Parameter *Include* und *Exclude* ist jedoch einfacher und leichter zu merken.

Zurück zum Seitenanfang

## Get-QueueDigest

Exchange 2013 fügt ein neues Warteschlangen-Cmdlet namens **Get-QueueDigest** hinzu. Mit diesem Cmdlet können Sie Informationen zu manchen oder allen Warteschlangen in Ihrer Exchange-Organisation mit nur einem einzigen Befehl anzeigen. Insbesondere ermöglicht das Cmdlet **Get-QueueDigest** es Ihnen, Informationen zu Warteschlangen basierend auf ihrem Speicherort auf Servern, in DAGs, an Active Directory-Standorten oder in der Active Directory-Gesamtstruktur als Ganzes anzuzeigen. Beachten Sie, dass Warteschlangen auf einem abonnierten Edge-Transport-Server im Umkreisnetzwerk nicht in den Ergebnissen enthalten sind. Zudem ist **Get-QueueDigest** zwar auf einem Edge-Transport-Server verfügbar, aber die Ergebnisse sind auf die Warteschlangen auf dem Edge-Transport-Server beschränkt.


> [!NOTE]
> Standardmäßig zeigt das <STRONG>Get-QueueDigest</STRONG>-Cmdlet Zustellungswarteschlangen an, die zehn oder mehr Nachrichten enthalten und deren Ergebnisse zwischen ein und zwei Minuten alt sind. Anweisungen zum Ändern der Standardwerte finden Sie unter <A href="configure-get-queuedigest-exchange-2013-help.md">Konfigurieren von Get-QueueDigest</A>.



In der folgenden Tabelle werden die Filter- und Sortierparameter beschrieben, die mit dem Cmdlet **Get-QueueDigest** verwendet werden können.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Dag</em>, <em>Server</em> oder <em>Site</em></p></td>
<td><p>Diese Parameter schließen sich gegenseitig aus und legen den Gültigkeitsbereich für das Cmdlet fest. Sie müssen einen dieser Parameter oder die Option <em>Forest</em> angeben. Normalerweise wird der Name des Servers, der DAG oder des Active Directory-Standorts verwendet. Sie können jedoch einen beliebigen Wert einsetzen, der den Server, die DAG oder den Standort eindeutig identifiziert. Mehrere Server, DAGs oder Standorte können durch Kommata getrennt angegeben werden.</p></td>
</tr>
<tr class="even">
<td><p><em>Forest</em></p></td>
<td><p>Diese Option ist erforderlich, wenn Sie die Parameter <em>Dag</em>, <em>Server</em> oder <em>Site</em> nicht verwenden. Mit dieser Option wird kein Wert angegeben. Bei Verwendung dieser Option erhalten Sie Warteschlangen von allen Exchange 2013-Postfachservern in der Active Directory-Gesamtstruktur. Sie können die Option <em>Forest</em> nicht zum Anzeigen von Warteschlangen in Active Directory-Remotegesamtstrukturen verwenden.</p></td>
</tr>
<tr class="odd">
<td><p><em>DetailsLevel</em></p></td>
<td><p>Dieser Parameter akzeptiert die Werte <code>None</code>, <code>Normal</code> und <code>Verbose</code>. Der Standardwert ist <code>Normal</code>. Wenn Sie den Wert <code>None</code> verwenden, wird die Warteschlange aus der Spalte <strong>Details</strong> in den Ergebnissen ausgeschlossen.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>Mit diesem Parameter können Sie Warteschlangen basierend auf den Eigenschaften der Warteschlange filtern. Wie im Thema <a href="queue-filters-exchange-2013-help.md">Warteschlangenfilter</a> beschrieben, können Sie beliebige der filterbaren Warteschlangeneigenschaften verwenden.</p></td>
</tr>
<tr class="odd">
<td><p><em>GroupBy</em></p></td>
<td><p>Dieser Parameter gruppiert die Warteschlangenergebnisse. Sie können die Ergebnisse nach einer der folgenden Eigenschaften gruppieren:</p>
<ul>
<li><p>DeliveryType</p></li>
<li><p>LastError</p></li>
<li><p>NextHopCategory</p></li>
<li><p>NextHopDomain</p></li>
<li><p>NextHopKey</p></li>
<li><p>Status</p></li>
<li><p>ServerName</p></li>
</ul>
<p>Standardmäßig werden die Ergebnisse nach <code>NextHopDomain</code> gruppiert. Informationen zu diesen Warteschlangeneigenschaften finden Sie unter <a href="queue-filters-exchange-2013-help.md">Warteschlangenfilter</a>.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>Dieser Parameter begrenzt die Warteschlangenergebnisse auf den von Ihnen angegebenen Wert. Die Warteschlangen werden in absteigender Reihenfolge basierend auf der Anzahl von Nachrichten in der Warteschlange sortiert und nach dem Wert gruppiert, der über den Parameter <em>GroupBy</em> angegeben wird. Der Standardwert lautet 1000. Damit zeigt der Befehl standardmäßig die ersten 1000 Warteschlangen an, gruppiert nach <strong>NextHopDomain</strong> und sortiert nach den Warteschlangen mit den meisten Nachrichten bis hin zu den Warteschlangen mit den wenigsten Nachrichten.</p></td>
</tr>
<tr class="odd">
<td><p><em>Timeout</em></p></td>
<td><p>Der Parameter gibt die Anzahl von Sekunden für die Zeitüberschreitung des Vorgangs an. Der Standardwert ist <code>00:00:10</code> oder 10 Sekunden.</p></td>
</tr>
</tbody>
</table>


In diesem Beispiel werden alle nicht leeren externen Warteschlangen auf den Exchange 2013-Postfachservern namens "Mailbox01", "Mailbox02" und "Mailbox03" zurückgegeben.

    Get-QueueDigest -Server Mailbox01,Mailbox02,Mailbox03 -Include External -Exclude Empty

Zurück zum Seitenanfang

## Parameter zur Nachrichtenfilterung

In der folgenden Tabelle werden die Filterparameter beschrieben, die in den Cmdlets zur Nachrichtenverwaltung verfügbar sind.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Filterparameter</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Get-Message</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p>
<p><em>Queue</em></p></td>
<td><p>Alle Filterparameter schließen sich gegenseitig aus, und Sie können sie zusammen in demselben Befehl verwenden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Remove-Message</strong></p>
<p><strong>Resume-Message</strong></p>
<p><strong>Suspend-Message</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p></td>
<td><p>Sie müssen entweder den Parameter <em>Identity</em> oder den Parameter <em>Filter</em> verwenden, können jedoch nicht beide in demselben Befehl einsetzen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Export-Message</strong></p></td>
<td><p><em>Identity</em></p></td>
<td><p>Der Parameter <em>Identity</em> ist erforderlich.</p></td>
</tr>
</tbody>
</table>


Beachten Sie, dass ein Parameter *Server* in allen Cmdlets zur Nachrichtenverwaltung verfügbar ist außer im Cmdlet **Export-Message**. Sie verwenden den Parameter *Server* zum Herstellen einer Verbindung mit einem bestimmten Server und führen die Befehle zur Nachrichtenverwaltung auf diesem Server aus. Sie können den Parameter *Server* mit dem oder ohne den Parameter *Filter* verwenden. Der Parameter *Server* kann jedoch nicht mit dem Parameter *Identity* zusammen verwendet werden. Der Hostname oder der FQDN des Transportservers wird mit dem Parameter *Server* verwendet.

Zurück zum Seitenanfang

## Nachrichtenidentität

Der Parameter *Identity* in den Cmdlets zur Nachrichtenverwaltung identifiziert eine bestimmte Nachricht in einer oder mehreren Warteschlangen. Wenn Sie den Parameter *Identity* einsetzen, können Sie keine weiteren Parameter zur Nachrichtenfilterung angeben, da Sie die Nachricht bereits eindeutig bezeichnet haben. Der Parameter *Identity* verwendet die grundlegende Syntax *\<Server\>*\\*\<Warteschlange\>*\\*\<MessageInteger\>*.

Der Platzhalter *\<Server\>* steht für den Hostnamen oder den FQDN des Exchange-Servers, z. B. `mailbox01` oder `mailbox01.contoso.com`. Wenn Sie den Bezeichner *\<Server\>* auslassen, wird der lokale Server angenommen.

Der Platzhalter \<*Warteschlange*\> steht für die Identität der Warteschlange entsprechend der Beschreibung im Abschnitt "Warteschlangenidentität" in diesem Thema. Beispielsweise können Sie den Namen der beständigen Warteschlange, den Wert **NextHopDomain** oder den eindeutigen Ganzzahlwert der Warteschlange in der Warteschlangendatenbank verwenden.

Der Platzhalter *\<MessageInteger\>* steht für den eindeutigen Ganzzahlwert, der der Nachricht zugewiesen wird, wenn sie erstmals in die Warteschlangendatenbank auf dem Server aufgenommen wird. Wen die Nachricht an mehrere Empfänger gesendet wird, für die mehrere Warteschlangen erforderlich sind, besitzen alle Kopien der Nachricht in allen Warteschlangen in der Warteschlangendatenbank denselben Ganzzahlwert. Allerdings müssen Sie das Cmdlet **Get-Message** ausführen, um den Ganzzahlwert für die Nachricht in der Eigenschaft **Identity** oder **MessageIdentity** zu finden.

In der folgenden Tabelle wird die Syntax zusammengefasst, die Sie mit dem Parameter *Identity* in den Cmdlets für die Nachrichtenverwaltung verwenden können. In allen Werten bezeichnet *\<Server\>* den Hostnamen oder den FQDN des Servers.

### Formate der Nachrichtenidentität

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert des Identity-Parameters</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;Queue&gt;\&lt;MessageInteger&gt;</code> oder <code>&lt;Queue&gt;\&lt;MessageInteger&gt;</code></p></td>
<td><p>Eine Nachricht in einer bestimmten Warteschlange auf dem angegebenen oder dem lokalen Server.</p>
<p><em>&lt;MessageInteger&gt;</em> ist der eindeutige Ganzzahlwert der Nachricht, der in der Eigenschaft <strong>Identity</strong> des Cmdlets <strong>Get-Message</strong> angezeigt wird.</p>
<p><em>&lt;Warteschlange&gt;</em> stellt einen der folgenden Werte dar:</p>
<ul>
<li><p><strong>Name der beständigen Warteschlange</strong>   Der Wert <code>Submission</code>, <code>Unreachable</code> oder <code>Poison</code>.</p></li>
<li><p><strong>Name einer Zustellungswarteschlange</strong>   Der Wert der Warteschlangeneigenschaft <strong>NextHopDomain</strong>, im Endeffekt der Name der Warteschlange. Dieser Wert kann ein Routingziel oder eine Verteilergruppe sein. Weitere Informationen finden Sie im Abschnitt &quot;NextHopSolutionKey&quot; im Thema <a href="queues-exchange-2013-help.md">Warteschlangen</a>.</p></li>
<li><p><strong>Warteschlangenganzzahl</strong>   Der eindeutige Ganzzahlwert der Zustellungs- oder Shadow-Warteschlange, der in der Eigenschaft <strong>Identity</strong> des Cmdlets <strong>Get-Message</strong> oder <strong>Get-Queue</strong> angezeigt wird.</p></li>
<li><p><strong>Name einer Shadow-Warteschlange</strong>   Die Identität einer Shadow-Warteschlange verwendet die Syntax <code>Shadow\&lt;QueueInteger&gt;</code>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\*\&lt;MessageInteger&gt;</code> oder <code>*\&lt;MessageInteger&gt;</code> oder <code>&lt;MessageInteger&gt;</code></p></td>
<td><p>Alle Kopien der Nachricht in allen Warteschlangen in der Warteschlangendatenbank auf dem angegebenen oder dem lokalen Server.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Parameter zur Nachrichtenfilterung

Mit dem Parameter *Filter* in den Cmdlets **Get-Message**, **Remove-Message**, **Resume-Message** und **Suspend-Message** können Sie die anzuzeigenden oder zu verwaltenden Nachrichten basierend auf den Nachrichteneigenschaften angeben. Der Parameter *Filter* erstellt einen Ausdruck mit Vergleichsoperatoren, der die Nachrichtenoperation auf Nachrichten einschränkt, die den Filterkriterien entsprechen. Sie können den logischen Operator `-and` verwenden, um mehrere Bedingungen anzugeben, denen die Ergebnisse entsprechen sollen.

Eine vollständige Liste mit Nachrichteneigenschaften, die Sie mit dem Parameter *Filter* verwenden können, finden Sie unter [Warteschlangen](queues-exchange-2013-help.md).

Eine Liste mit Vergleichsoperatoren, die mit dem Parameter *Filter* verwendet werden können, finden Sie im Abschnitt Comparison operators to use when filtering queues or messages in diesem Thema.

Beispiele für Vorgehensweisen, die den Parameter *Filter* zum Anzeigen und Verwalten von Nachrichten verwenden, finden Sie unter [Verwalten von Warteschlangen](manage-queues-exchange-2013-help.md).

Zurück zum Seitenanfang

## Der Queue-Parameter

Der Parameter *Queue* wird nur mit dem Cmdlet **Get-Message** verwendet. Mit diesem Parameter können Sie alle Nachrichten in einer bestimmten Warteschlange oder alle Nachrichten aus mehreren Warteschlangen abrufen, indem Sie das Platzhalterzeichen (\*) verwenden. Wenn Sie den Parameter *Queue* einsetzen, verwenden Sie das Warteschlangenidentitätsformat *\<Server\>*\\*\<Warteschlange\>* wie im Abschnitt "Warteschlangenidentität" in diesem Thema beschrieben.

Zurück zum Seitenanfang

## Beim Filtern von Warteschlangen oder Nachrichten verwendbare Vergleichsoperatoren

Wenn Sie mithilfe des Parameters *Filter* einen Filterausdruck für Warteschlangen oder Nachrichten erstellen, müssen Sie einen Vergleichsoperator für den abzugleichenden Eigenschaftswert einschließen. Die folgende Tabelle zeigt die Vergleichsoperatoren, die in Filterausdrücken verwendet werden können, sowie die Funktionsweise der einzelnen Operatoren. Bei allen Operatoren ist die Groß-/Kleinschreibung der verglichenen Werte nicht relevant.

### Vergleichsoperatoren

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Operator</th>
<th>Funktion</th>
<th>Beispiel für Shellcode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>-eq</code></p></td>
<td><p>Dieser Operator wird verwendet, um anzugeben, dass die Ergebnisse genau mit dem im Ausdruck übergebenen Eigenschaftenwert übereinstimmen müssen.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen mit dem Status <strong>Wiederholen</strong> an</p>
<p><code>Get-Queue -Filter {Status -eq &quot;Retry&quot;}</code></p>
<p>So zeigen Sie eine Liste aller Nachrichten an, die den Status <strong>Wiederholen</strong> aufweisen</p>
<p><code>Get-Message -Filter {Status -eq &quot;Retry&quot;}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-ne</code></p></td>
<td><p>Dieser Operator wird verwendet, um anzugeben, dass die Ergebnisse nicht mit dem im Ausdruck übergebenen Eigenschaftenwert übereinstimmen müssen.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen an, die nicht den Status <strong>Aktiv</strong> aufweisen</p>
<p><code>Get-Queue -Filter {Status -ne &quot;Active&quot;}</code></p>
<p>So zeigen Sie eine Liste aller Nachrichten an, die nicht den Status <strong>Aktiv</strong> aufweisen</p>
<p><code>Get-Message -Filter {Status -ne &quot;Active&quot;}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-gt</code></p></td>
<td><p>Dieser Operator wird für Eigenschaften verwendet, deren Wert als ganze Zahl oder als Datum/Zeit ausgedrückt wird. Die Filterergebnisse enthalten nur Warteschlangen oder Nachrichten, bei denen der Wert der angegebenen Eigenschaft größer als der im Ausdruck angegebene Wert ist.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen mit mehr als 1000 Nachrichten an</p>
<p><code>Get-Queue -Filter {MessageCount -gt 1000}</code></p>
<p>So zeigen Sie eine Liste aller Nachrichten an, die aktuell einen Wiederholungszähler von mehr als 3 aufweisen</p>
<p><code>Get-Message -Filter {RetryCount -gt 3}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-ge</code></p></td>
<td><p>Dieser Operator wird für Eigenschaften verwendet, deren Wert als ganze Zahl oder als Datum/Zeit ausgedrückt wird. Die Filterergebnisse enthalten nur Warteschlangen oder Nachrichten, bei denen der Wert der angegebenen Eigenschaft größer als oder gleich dem im Ausdruck angegebenen Wert ist.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen mit mindestens 1000 Nachrichten an</p>
<p><code>Get-Queue -Filter {MessageCount -ge 1000}</code></p>
<p>So zeigen Sie eine Liste der Nachrichten an, die derzeit einen Wiederholungszähler von 3 oder mehr aufweisen</p>
<p><code>Get-Message -Filter {RetryCount -ge 3}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-lt</code></p></td>
<td><p>Dieser Operator wird für Eigenschaften verwendet, deren Wert als ganze Zahl oder als Datum/Zeit ausgedrückt wird. Die Filterergebnisse enthalten nur Warteschlangen oder Nachrichten, bei denen der Wert der angegebenen Eigenschaft kleiner als der im Ausdruck angegebene Wert ist.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen mit weniger als 1000 Nachrichten an</p>
<p><code>Get-Queue -Filter {MessageCount -lt 1000}</code></p>
<p>So zeigen Sie eine Liste der Nachrichten an, die einen SCL kleiner als 6 aufweisen</p>
<p><code>Get-Message -Filter {SCL -lt 6}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-le</code></p></td>
<td><p>Dieser Operator wird für Eigenschaften verwendet, deren Wert als ganze Zahl oder als Datum/Zeit ausgedrückt wird. Die Filterergebnisse enthalten nur Warteschlangen oder Nachrichten, bei denen der Wert der angegebenen Eigenschaft kleiner als oder gleich dem im Ausdruck angegebenen Wert ist.</p></td>
<td><p>So zeigen Sie eine Liste aller Warteschlangen mit höchstens 1000 Nachrichten an</p>
<p><code>Get-Queue -Filter {MessageCount -le 1000}</code></p>
<p>So zeigen Sie eine Liste der Nachrichten an, die einen SCL von 6 oder weniger aufweisen</p>
<p><code>Get-Message -Filter {SCL -le 6}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-like</code></p></td>
<td><p>Dieser Operator wird für Eigenschaften verwendet, deren Wert als Textzeichenfolge ausgedrückt wird. Die Filterergebnisse enthalten nur Warteschlangen oder Nachrichten, bei denen der Wert der angegebenen Eigenschaft die im Ausdruck angegebene Textzeichenfolge enthält. Sie können das Platzhalterzeichen (*) in einem <strong>-like</strong>-Ausdruck angeben, der auf ein Textzeichenfolgenfeld angewendet wird, nicht jedoch für ein Feld vom Typ <strong>Aufzählung</strong>.</p></td>
<td><p>So zeigen Sie eine Liste mit Zustellungswarteschlangen an, deren Ziel eine beliebige SMTP-Domäne ist, die auf &quot;Contoso.com&quot; endet</p>
<p><code>Get-Queue -Filter {Identity -like &quot;*contoso.com&quot;}</code></p>
<p>So zeigen Sie eine Liste der Nachrichten mit einem Betreff an, der den Text &quot;Kredit am Zahltag&quot; enthält</p>
<p><code>Get-Messages -Filter {Subject -like &quot;*payday loan*&quot;}</code></p></td>
</tr>
</tbody>
</table>


Mithilfe des Vergleichsoperators **-and** können Sie einen Filter angeben, der mehrere Ausdrücke auswertet. Die Warteschlangen oder Nachrichten müssen alle Bedingungen des Filters erfüllen, um in die Ergebnisse aufgenommen zu werden.

Dieses Beispiel zeigt eine Liste der Warteschlangen an, deren Ziel eine beliebige auf "Contoso.com" endende SMTP-Domäne ist und die gegenwärtig mehr als 500 Nachrichten enthalten.

    Get-Queue -Filter {Identity -like "*contoso.com*" -and MessageCount -gt 500}

Dieses Beispiel zeigt eine Liste von Nachrichten an, die von einer beliebigen E-Mail-Adresse in der Domäne "contoso.com" gesendet werden und deren SCL-Wert größer ist als 5.

    Get-Message -Filter {FromAddress -like "*Contoso.com*" -and SCL -gt 5}

Zurück zum Seitenanfang

## Erweiterte Pagingparameter

Abhängig von der aktuellen Nachrichtenübermittlung können Abfragen auf Warteschlangen und Nachrichten eine große Menge von Objekten zurückgeben. Mithilfe der erweiterten Pagingparameter lässt sich steuern, wie Ergebnismengen abgerufen und angezeigt werden.

Wenn die Shell zum Anzeigen von Warteschlangen und Nachrichten in den Warteschlangen verwendet wird, rufen die Abfragen jeweils eine Seite Informationen ab. Die erweiterten Pagingparameter steuern die Größe der Ergebnismenge und können außerdem zum Sortieren der Ergebnisse verwendet werden. Alle erweiterten Pagingparameter sind optional und können mit allen Parametersätzen kombiniert werden, die mit den Cmdlets **Get-Queue** und **Get-Message** verwendet werden können. Wenn Sie keine erweiterten Pagingparameter angeben, gibt die Abfrage die Ergebnisse in aufsteigender Reihenfolge der Identität zurück.

Standardmäßig ist beim Angeben einer Sortierreihenfolge die Nachrichtenidentitätseigenschaft immer eingeschlossen und wird in aufsteigender Reihenfolge sortiert. Dies ist die Standardsortierbeziehung. Die Nachrichtenidentitätseigenschaft wird eingeschlossen, weil die anderen Eigenschaften, die in eine Sortierreihenfolge eingeschlossen werden können, nicht eindeutig sind. Indem Sie die Nachrichtenidentitätseigenschaft explizit in die Sortierreihenfolge einschließen, können Sie angeben, dass die Nachrichtenidentität in den Ergebnissen in absteigender Reihenfolge sortiert anzeigt wird.

Sie können die Parameter *BookmarkIndex* und *BookmarkObject* verwenden, um eine Position in der sortierten Ergebnismenge zu markieren. Wenn das Lesezeichenobjekt beim Abrufen der nächsten Seite mit Ergebnissen nicht mehr vorhanden ist, stellt die standardmäßige Sortierbeziehung sicher, dass die Ergebnismenge mit dem Objekt beginnt, das dem Lesezeichen zunächst liegt. Das nächst gelegene Objekt hängt von der angegebenen Sortierreihenfolge ab.

Die folgende Tabelle beschreibt die erweiterten Pagingparameter.

### Erweiterte Pagingparameter

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>BookmarkIndex</em></p></td>
<td><p>Dieser Parameter gibt die Position im Resultset an, an der die angezeigten Ergebnisse beginnen. Der Wert dieses Parameters ist ein auf 1 basierender Index im Gesamtresultset. Wenn der Wert kleiner als oder gleich Null ist, wird die erste vollständige Seite mit Ergebnissen zurückgegeben. Wenn der Wert auf <code>Int.MaxValue</code> festgelegt ist, wird die letzte vollständige Seite mit Ergebnissen zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p><em>BookmarkObject</em></p></td>
<td><p>Dieser Parameter gibt das Objekt im Resultset an, bei dem die angezeigten Ergebnisse beginnen. Wenn Sie ein Lesezeichenobjekt angeben, wird dieses Objekt als Ausgangspunkt für die Suche verwendet. Abhängig vom Wert des Parameters <em>SearchForward</em> werden die Zeilen vor oder nach diesem Objekt abgerufen. Die Parameter <em>BookmarkObject</em> und <em>BookmarkIndex</em> können nicht in einer einzigen Abfrage kombiniert werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>IncludeBookmark</em></p></td>
<td><p>Dieser Parameter gibt an, ob das Lesezeichenobjekt in das Resultset eingeschlossen werden soll. Standardmäßig ist dieser Wert auf <code>$true</code> festgelegt, und das Lesezeichenobjekt wird eingeschlossen. Sie können eine Abfrage ausführen, um eine eingeschränkte Ergebnisgröße zurückzugeben, und das letzte Element in der Ergebnismenge als Lesezeichen für die nächste Abfrage verwenden. In diesem Fall kann es sinnvoll sein, <em>IncludeBookmark</em> auf <code>$false</code> festzulegen, damit das Objekt nicht in beiden Resultsets enthalten ist.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>Dieser Parameter gibt die Anzahl der pro Seite anzuzeigenden Ergebnisse an. Wenn Sie keinen Wert angeben, wird die Standardergebnisgröße von 1.000 Objekten verwendet. Exchange beschränkt das Resultset auf 250.000.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReturnPageInfo</em></p></td>
<td><p>Dieser Parameter ist ein ausgeblendeter Parameter. Er gibt Informationen über die Gesamtanzahl der Ergebnisse und den Index des ersten Objekts der aktuellen Seite zurück. Der Standardwert ist <code>$false</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>SearchForward</em></p></td>
<td><p>Dieser Parameter gibt an, ob im Resultset vorwärts oder rückwärts gesucht werden soll. Dieser Parameter wirkt sich nicht auf die Reihenfolge aus, in der die Ergebnismenge zurückgegeben wird. Er bestimmt die Suchrichtung relativ zum Lesezeichenindex oder -objekt. Wenn kein Lesezeichenindex oder -objekt angegeben ist, bestimmt der Parameter <em>SearchForward</em>, ob die Suche beim ersten oder letzten Objekt in der Ergebnismenge beginnt.</p>
<p>Der Standardwert für diesen Parameter ist <code>$true</code>. Wenn dieser Parameter auf <code>$true</code> festgelegt und ein Lesezeichen angegeben ist, sucht die Abfrage vom Lesezeichen aus vorwärts. Wenn Sie diese Konfiguration verwenden und sich hinter dem Lesezeichen keine Ergebnisse befinden, gibt die Abfrage die letzte volle Seite mit Ergebnissen zurück.</p>
<p>Wenn der Parameter <em>SearchForward</em> auf <code>$false</code> festgelegt und ein Lesezeichen angegeben ist, sucht die Abfrage vom Lesezeichen aus rückwärts. Wenn Sie diese Konfiguration verwenden und sich weniger als eine volle Seite mit Ergebnissen jenseits des Lesezeichens befindet, gibt die Abfrage die erste volle Seite mit Ergebnissen zurück.</p></td>
</tr>
<tr class="odd">
<td><p><em>SortOrder</em></p></td>
<td><p>Dieser Parameter gibt ein Array mit Nachrichteneigenschaften an, die zum Steuern der Sortierreihenfolge des Resultsets verwendet werden. Die Eigenschaften für die Sortierreihenfolge werden absteigend nach ihrem Vorrang angegeben. Jede Eigenschaft wird durch ein Komma getrennt, und ihr wird ein Pluszeichen (+) angefügt, um in aufsteigender Reihenfolge zu sortieren, oder ein Minuszeichen (-), um in absteigender Reihenfolge zu sortieren.</p>
<p>Wenn durch die Verwendung dieses Parameters keine explizite Sortierreihenfolge angegeben wird, werden die der Abfrage entsprechenden Datensätze angezeigt und nach dem Identitätsfeld für den entsprechenden Objekttyp sortiert. Wenn keine Sortierreihenfolge explizit angegeben ist, werden die Ergebnisse immer nach der Identität in aufsteigender Reihenfolge sortiert.</p></td>
</tr>
</tbody>
</table>


Das folgende Codebeispiel zeigt die Verwendung der erweiterten Pagingparameter in einer Abfrage. In diesem Beispiel stellt der Befehl eine Verbindung mit dem angegebenen Server her und ruft eine Ergebnismenge ab, die 500 Objekte enthält. Die Ergebnisse werden sortiert angezeigt, zuerst in aufsteigender Reihenfolge nach der Absenderadresse und dann in absteigender Reihenfolge nach der Nachrichtengröße.

`Get-Message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size`

Wenn Sie aufeinander folgende Seiten anzeigen möchten, können Sie ein Lesezeichen für das letzte in einer Ergebnismenge abgerufene Objekt festlegen und eine weitere Abfrage ausführen. Zum Ausführen dieses Vorgangs müssen Sie die Skriptfähigkeit der Shell verwenden.

Im folgenden Beispiel wird ein Skript verwendet, um die erste Ergebnisseite abzurufen, das Lesezeichenobjekt festzulegen, das Lesezeichenobjekt aus der Ergebnismenge auszuschließen und anschließend die nächsten 500 Objekte auf dem angegebenen Server abzurufen.

1.  Öffnen Sie die Shell, und geben Sie den folgenden Befehl ein, um die erste Ergebnisseite abzurufen.
    
        $Results=Get-message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size

2.  Geben Sie zum Festlegen des Lesezeichenobjekts den folgenden Befehl ein, um das letzte Element der ersten Seite in einer Variablen zu speichern.
    
        $temp=$results[$results.length-1]

3.  Geben Sie den folgenden Befehl ein, um die nächsten 500 Objekte auf dem angegebenen Server abzurufen und das Lesezeichenobjekt auszuschließen.
    
        Get-message -Server mailbox01.contoso.com -BookmarkObject:$temp -IncludeBookmark $False -ResultSize 500 -SortOrder +FromAddress,-Size

Zurück zum Seitenanfang

