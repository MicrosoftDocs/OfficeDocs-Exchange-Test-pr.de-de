---
title: 'Transport-Agents: Exchange 2013 Help'
TOCTitle: Transport-Agents
ms:assetid: e7389d63-3172-40d5-bf53-0d7cd7e78340
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125012(v=EXCHG.150)
ms:contentKeyID: 50476960
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transport-Agents

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit Transport-Agents können Sie benutzerdefinierte Software von Microsoft, Drittanbietern oder Ihrer Organisation auf einem Exchange-Server installieren. Diese Software kann dann E-Mail-Nachrichten verarbeiten, die die Transportpipeline passieren. In Microsoft Exchange Server 2013 besteht die Transportpipeline aus den folgenden Prozessen:

  - Dem Front-End-Transport-Dienst auf Clientzugriffsservern

  - Dem Transportdienst auf Postfachservern

  - Dem Postfach-Transportdienst auf Postfachservern

  - Dem Transportdienst auf Edge-Transport-Servern

Weitere Informationen zur Transportpipeline finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).

Wie bei den vorherigen Versionen von Exchange ermöglicht der Exchange 2013-Transport die Erweiterbarkeit über das Transport-Agents-SDK für Microsoft Exchange Server 2013. Die Exchange 2013-Version des SDK basiert auf Microsoft.NET Framework, Version 4.0, und ermöglicht Drittanbietern, die folgenden vordefinierten Klassen zu implementieren:

  - **SmtpReceiveAgent**

  - **RoutingAgent**

  - **DeliveryAgent**

Wenn sie mit Bibliotheken im SDK abgeglichen werden, werden die sich ergebenden Assemblys mit Exchange 2013 registriert, wodurch die Agents geladen und ihre Ereignishandler in bestimmten Phasen der SMTP-Sitzungen oder während der Nachrichtenverarbeitung aufgerufen werden. Diese Phasen oder Ereignisse sind Teil der Agent-Definitionen. Die Agent-Registrierungsinformationen werden in einer XML-Konfigurationsdatei gespeichert.

In der folgenden Liste werden die Anforderungen für die Verwendung von Transport-Agents in Exchange 2013 erläutert.

  - Der Transportdienst auf Postfachservern und Edge Transport-Servern unterstützt alle vordefinierten Klassen im SDK vollständig. Daher sollten alle Transport-Agents von Drittanbietern, die für die Hub-Transport- oder die Edge-Transport-Serverrolle in Microsoft Exchange Server 2010 geschrieben wurden, im Transportdienst in Exchange 2013 funktionieren.

  - Der Front-End-Transport-Dienst unterstützt nur die Klasse **SmtpReceiveAgent** im SDK und die Agents von Drittanbietern können nicht mit dem SMTP-Ereignis **OnEndOfData** ausgeführt werden.

  - Der Postfachtransportdienst unterstützt das SDK in keiner Weise, daher können Sie keine Agents von Drittanbietern im Postfachtransportdienst verwenden.

Die Unterstützung für Legacytransport-Agents, die auf Versionen vor .NET Framework, Version 4.0, basieren, ist nicht standardmäßig aktiviert, kann aber von Ihnen aktiviert werden. Anweisungen finden Sie unter [Aktivieren der Unterstützung für Transport-Agents einer Vorversion](enable-support-for-legacy-transport-agents-exchange-2013-help.md).

**Inhalt**

Updates für die Transport-Agent-Verwaltung

Transport-Agents und SMTP-Ereignisse

Priorität von Transport-Agents

Integrierte Transport-Agents

Problembehandlung von Transport-Agents

## Updates für die Transport-Agent-Verwaltung

Aufgrund der Updates für die Exchange 2013-Transportpipeline müssen die Transport-Agent-Cmdlets zwischen dem Transportdienst und dem Front-End-Transport-Dienst unterscheiden. Das gilt insbesondere, wenn der Clientzugriffsserver und der Postfachserver auf demselben Computer installiert sind. Weitere Informationen finden Sie unter [Verwalten von Transport-Agents](manage-transport-agents-exchange-2013-help.md).

Cmdlets zur Verwaltung von Transport-Agents bearbeiten eine Konfigurationsdatei, die sich unter `%ExchangeInstallPath%TransportRoles\Shared` befindet. Für den Transportdienst auf Postfachservern und Edge-Transport-Servern heißt diese Datei `agents.config`. Für den Front-End-Transport-Dienst auf Clientzugriffsservern heißt diese Datei `fetagents.config`. Beide Dateien verwenden dasselbe Format wie in Exchange 2010. Weitere Informationen zur Verwaltung von Transport-Agents finden Sie unter [Verwalten von Transport-Agents](manage-transport-agents-exchange-2013-help.md).

Zurück zum Seitenanfang

## Transport-Agents und SMTP-Ereignisse

Transport-Agents verwenden SMTP-Ereignisse. Diese Ereignisse werden ausgelöst, wenn Nachrichten die Transportpipeline durchlaufen. SMTP-Ereignisse erlauben Transport-Agents den Zugriff auf Nachrichten an bestimmten Punkten während der SMTP-Konversation und beim Routing von Nachrichten durch die Organisation.

Bitte beachten Sie, dass in Exchange 2013 SMTP-Empfangsereignisse zur Verfügung stehen. SMTP Receive ist im Front-End-Transportdienst auf Clientzugriffsservern, dem Transportdienst auf Postfachservern und Edge-Transport-Servern sowie dem Postfachtransport-Zustellungsdienst auf Postfachservern verfügbar. Das Kategorisierungsmodul existiert nur im Transportdienst auf Postfachservern und Edge-Transport-Servern. Weitere Informationen zu Transportdiensten und dem Kategorisierungsmodul finden Sie unter [E-Mail-Routing](mail-routing-exchange-2013-help.md).

In den folgenden Tabellen sind die SMTP-Ereignisse aufgeführt, die Zugriff auf Nachrichten in der Transportpipeline bieten.

### SMTP-Empfangsereignisse

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Reihenfolge</th>
<th>SMTP-Ereignis</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p><strong>OnConnectEvent</strong></p></td>
<td><p>Dieses Ereignis wird bei der Erstverbindung von einem Remote-SMTP-Host ausgelöst.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p><strong>OnHeloCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>HELO</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p><strong>OnEhloCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>EHLO</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p><strong>OnStartTlsCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>STARTTLS</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p><strong>OnAuthCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>AUTH</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p><strong>OnProcessAuthentication</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn die Authentifizierung am Remote-SMTP-Host verarbeitet wird.</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p><strong>OnEndOfAuthentication</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Remote-SMTP-Host die Authentifizierung abgeschlossen hat.</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p><strong>OnXSessionParamsCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>XSESSIONPARAMS</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p><strong>OnMailCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>MAIL FROM</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p><strong>OnRcptToCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>RCPT TO</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p><strong>OnDataCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>DATA</code> (Text) oder <code>BDAT</code> (binäre Daten) vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p><strong>OnEndOfHeaders</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Remote-SMTP-Host die Übermittlung der E-Mail-Nachrichtenkopfzeilen abgeschlossen hat. Dies wird durch eine leere Zeile (<code>&lt;CRLF&gt;</code>) angezeigt, die die Kopfzeile der Nachricht vom Nachrichtentext trennt.</p></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p><strong>OnProxyInboundMessage</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn eine eingehende SMTP-Sitzung mittels Relay oder <em>Proxyweiterleitung</em> durch den Front-End-Dienst auf einem Clientzugriffsserver an den Transportdienst auf einem Postfachserver gesendet wird.</p></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p><strong>OnEndOfData</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Remote-SMTP-Host den Befehl &quot;end of data&quot; ausgibt. Für durch den Befehl <code>DATA</code> gestartete Textsitzungen ist der Indikator für &quot;end of data&quot; <code>&lt;CRLF&gt;.&lt;CRLF&gt;</code>. Für durch den Befehl <code>BDAT</code> gestartete binäre Sitzungen ist der Indikator für &quot;end of data&quot; <code>BDAT LAST</code>.</p></td>
</tr>
<tr class="odd">
<td><p>**</p></td>
<td><p><strong>OnHelpCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>HELP</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>**</p></td>
<td><p><strong>OnNoopCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>NOOP</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>**</p></td>
<td><p><strong>OnReject</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der empfangende SMTP-Host einen temporären oder endgültigen Code für die Benachrichtigung über den Übermittlungsstatus an den sendenden SMTP-Host ausgibt.</p></td>
</tr>
<tr class="even">
<td><p>**</p></td>
<td><p><strong>OnRsetCommand</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn der Befehl <code>RSET</code> vom sendenden SMTP-Host ausgegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p><strong>OnDisconnectEvent</strong></p></td>
<td><p>Dieses Ereignis wird beim Trennen der Verbindung der SMTP-Konversation vom empfangenden oder sendenden SMTP-Host ausgelöst. Dies passiert normalerweise, wenn der Befehl <code>QUIT</code> vom Remote-SMTP-Host ausgegeben wird.</p></td>
</tr>
</tbody>
</table>


\*\* Diese Ereignisse können jederzeit nach **OnConnectEvent** und vor **OnDisconnectEvent** auftreten.

### Kategorisierungsereignisse

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Reihenfolge</th>
<th>Kategorisierungsereignis</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p><strong>OnSubmittedMessage</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn eine Nachricht in der Übermittlungswarteschlange im Transportdienst auf dem empfangenden Postfachserver oder Edge-Transport-Server ankommt.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p><strong>OnResolvedMessage</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, nachdem alle Empfänger aufgelöst wurden, jedoch bevor der nächste Hop für die einzelnen Empfänger bestimmt wurde. Das Routingereignis <strong>OnResolvedMessage</strong> ermöglicht nachfolgenden Ereignissen die Außer-Kraft-Setzung des standardmäßigen Routingverhaltens mithilfe der <strong>SetRoutingOverride</strong>-Methode auf Empfängerbasis.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p><strong>OnRoutedMessage</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, nachdem Nachrichten kategorisiert, Verteilerlisten erweitert und Empfänger aufgelöst wurden.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p><strong>OnCategorizedMessage</strong></p></td>
<td><p>Dieses Ereignis wird ausgelöst, wenn das Kategorisierungsmodul die Verarbeitung der Nachricht abgeschlossen hat.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Priorität von Transport-Agents

Zwei Faktoren entscheiden über die Reihenfolge, in der Transport-Agents Nachrichten in der Transportpipeline verarbeiten:

1.  Das SMTP-Ereignis, in dem der Transport-Agent registriert wird, und der Zeitpunkt, zu dem das SMTP-Ereignis Nachrichten verarbeitet.

2.  Der Prioritätswert, der dem Transport-Agent zugewiesen wird, wenn mehrere Agents für dasselbe SMTP-Ereignis registriert sind. Die höchste Priorität ist 1. Ein höherer Ganzzahlwert steht für eine niedrigere Agent-Priorität.

Angenommen, dass Sie z. B. die folgenden Transport-Agents konfiguriert haben:

  - Transport-Agent A mit der Priorität 1 und Transport-Agent C mit der Priorität 2 sind für das SMTP-Ereignis **OnEndOfHeaders** registriert.

  - Transport-Agent B mit der Priorität 4 ist für das SMTP-Ereignis **OnMailCommand** registriert.

Transport-Agent B wird zuerst auf Nachrichten angewendet, da das Ereignis **OnMailCommand** die Nachrichten vor dem Ereignis **OnEndOfHeaders** verarbeitet. Wenn die Nachrichten das Ereignis **OnEndOfHeaders** erreichen, wird Transport-Agent A vor Transport-Agent C angewendet, da Transport-Agent A eine höhere Priorität (geringerer Ganzzahlwert) als Transport-Agent C hat.

## Integrierte Transport-Agents

Exchange 2013 enthält viele integrierte Transport-Agents, die Funktion wie Antispam, Transportregeln und Journale bieten. Die meisten der integrierten Transport-Agents auf Exchange 2013-Postfachservern und Clientzugriffsservern sind unsichtbar und können durch die Cmdlets zur Verwaltung von Transport-Agents nicht bearbeitet werden. Praktisch alle integrierten Transport-Agents, die sichtbar sind und verwaltet werden können, befinden sich im Transportdienst auf Postfachservern und Edge-Transport-Servern.

Die interessantesten integrierten Transport-Agents auf Postfachservern werden in der folgenden Tabelle beschrieben. Bitte beachten Sie, dass die Tabelle viele der unsichtbaren und nicht zu verwaltenden Transport-Agents enthält.

### Interessante integrierte Transport-Agents auf Postfachservern

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Agents</th>
<th>Verwaltbar?</th>
<th>Priorität</th>
<th>SMTP- oder Kategorisierungsereignisse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transportregel-Agent</p></td>
<td><p>Ja</p></td>
<td><p>1</p></td>
<td><p><strong>OnResolvedMessage</strong></p></td>
</tr>
<tr class="even">
<td><p>Malware-Agent</p></td>
<td><p>Ja</p></td>
<td><p>2</p></td>
<td><p><strong>OnSubmittedMessage</strong></p></td>
</tr>
<tr class="odd">
<td><p>SMS-Routing-Agent</p></td>
<td><p>Ja</p></td>
<td><p>3</p></td>
<td><p><strong>OnSubmittedMessage</strong></p></td>
</tr>
<tr class="even">
<td><p>SMS-Zustellungs-Agent</p></td>
<td><p>Ja</p></td>
<td><p>4</p></td>
<td><p>N/V</p></td>
</tr>
<tr class="odd">
<td><p>Journal-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Nicht konfigurierbar</p></td>
<td><p><strong>OnRoutedMessage</strong></p></td>
</tr>
<tr class="even">
<td><p>Journalberichtentschlüsselungs-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Nicht konfigurierbar</p></td>
<td><p><strong>OnCategorizedMessage</strong></p></td>
</tr>
<tr class="odd">
<td><p>RMS-Entschlüsselungs-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Nicht konfigurierbar</p></td>
<td><p><strong>OnSubmittedMessage</strong></p></td>
</tr>
<tr class="even">
<td><p>RMS-Verschlüsselungs-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Nicht konfigurierbar</p></td>
<td><p><strong>OnSubmittedMessage</strong>, <strong>OnRoutedMessage</strong></p></td>
</tr>
<tr class="odd">
<td><p>RMS-Protokoll-Entschlüsselungs-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Nicht konfigurierbar</p></td>
<td><p><strong>OnEndOfData</strong></p></td>
</tr>
</tbody>
</table>


Auf Edge-Transport-Servern sind die meisten integrierten Transport-Agents sichtbar und durch die Cmdlets zur Verwaltung von Transport-Agents oder durch andere featurespezifische Cmdlets verwaltbar.

Die interessantesten integrierten Transport-Agents auf Edge-Transport-Servern werden in der folgenden Tabelle beschrieben. Bitte beachten Sie, dass die Tabelle keine unsichtbaren oder unverwaltbaren Transport-Agents enthält.

### Interessante integrierte Transport-Agents auf Edge-Transport-Servern

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Agents</th>
<th>Verwaltbar?</th>
<th>Priorität</th>
<th>SMTP- oder Kategorisierungsereignisse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verbindungsfilter-Agent</p></td>
<td><p>Ja</p></td>
<td><p>1</p></td>
<td><p><strong>OnConnectEvent</strong>, <strong>OnMailCommand</strong>, <strong>OnRcptComand</strong>, <strong>OnEndOfHeaders</strong></p></td>
</tr>
<tr class="even">
<td><p>Adressumschreibungs-Agent für eingehende Nachrichten</p></td>
<td><p>Ja</p></td>
<td><p>2</p></td>
<td><p><strong>OnRcptCommand</strong>, <strong>OnEndOfHeaders</strong></p></td>
</tr>
<tr class="odd">
<td><p>Edge-Regel-Agent</p></td>
<td><p>Ja</p></td>
<td><p>3</p></td>
<td><p><strong>OnEndOfData</strong></p></td>
</tr>
<tr class="even">
<td><p>Inhaltsfilter-Agent*</p></td>
<td><p>Ja</p></td>
<td><p>4</p></td>
<td><p><strong>OnEndOfData</strong></p></td>
</tr>
<tr class="odd">
<td><p>Absender-ID-Agent*</p></td>
<td><p>Ja</p></td>
<td><p>5</p></td>
<td><p><strong>OnEndOfHeaders</strong></p></td>
</tr>
<tr class="even">
<td><p>Absenderfilter-Agent*</p></td>
<td><p>Ja</p></td>
<td><p>6</p></td>
<td><p><strong>OnMailCommand</strong>, <strong>OnEndOfHeaders</strong></p></td>
</tr>
<tr class="odd">
<td><p>Empfängerfilter-Agent</p></td>
<td><p>Ja</p></td>
<td><p>7</p></td>
<td><p><strong>OnRcptCommand</strong></p></td>
</tr>
<tr class="even">
<td><p>Protokollanalyse-Agent*</p></td>
<td><p>Ja</p></td>
<td><p>8</p></td>
<td><p><strong>OnConnectEvent</strong>, <strong>OnEndOfHeaders</strong>, <strong>OnEndOfData</strong>, <strong>OnReject</strong>, <strong>OnRsetCommand</strong>, <strong>OnDisconnectEvent</strong></p></td>
</tr>
<tr class="odd">
<td><p>Anlagenfilter-Agent</p></td>
<td><p>Ja</p></td>
<td><p>9</p></td>
<td><p><strong>OnEndOfData</strong></p></td>
</tr>
<tr class="even">
<td><p>Adressumschreibungs-Agent für ausgehende Nachrichten</p></td>
<td><p>Ja</p></td>
<td><p>10</p></td>
<td><p><strong>OnSubmittedMessage</strong>, <strong>OnRoutedMessage</strong></p></td>
</tr>
</tbody>
</table>


\* Diese Antispam-Agents können Sie auch auf Postfachservern installieren und konfigurieren. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

Zurück zum Seitenanfang

## Problembehandlung von Transport-Agents

Zur Behebung von Problemen mit Transport-Agents können Sie die folgenden Features nutzen:

  - **Get-TransportPipeline**   Dieses Cmdlet zeigt alle SMTP-Ereignisse sowie die entsprechenden Transport-Agents an, die Nachrichten auf dem Exchange-Server verarbeiten. Weitere Informationen finden Sie unter [Anzeigen von Transport-Agents in der Transportpipeline](view-transport-agents-in-the-transport-pipeline-exchange-2013-help.md).

  - **Pipelineablaufverfolgung **  Die Pipelineablaufverfolgung ermöglicht das Erstellen eines genauen Snapshots einer Nachricht, bevor und nachdem sie auf die einzelnen Transport-Agents trifft. Dadurch können Sie nach Transport-Agents suchen, die unerwartete Ergebnisse herbeiführen. Weitere Informationen finden Sie unter [Pipelineablaufverfolgung](pipeline-tracing-exchange-2013-help.md).

Zurück zum Seitenanfang

