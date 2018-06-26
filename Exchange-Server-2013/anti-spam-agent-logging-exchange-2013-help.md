---
title: 'Antispam-Agent-Protokollierung: Exchange 2013 Help'
TOCTitle: Antispam-Agent-Protokollierung
ms:assetid: dbd478d2-7993-4931-80db-5b2f7d4269bd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124795(v=EXCHG.150)
ms:contentKeyID: 50476892
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Antispam-Agent-Protokollierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Agent-Protokolle zeichnen die Aktionen auf, die von bestimmten Antispam-Agents in Microsoft Exchange Server 2013 für eine Nachricht ausgeführt werden. Nur die folgenden Agents können Informationen in das Agent-Protokoll schreiben:

  - Verbindungsfilter-Agent

  - Inhaltsfilter-Agent

  - Edge-Regel-Agent

  - Empfängerfilter-Agent

  - Absenderfilter-Agent

  - Sender ID-Agent


> [!NOTE]
> Der Verbindungsfilter-Agent und der Agent für Edge-Regeln sind auf Postfachservern nicht verfügbar.



Die in das Agent-Protokoll geschriebenen Informationen hängen vom Agent, dem SMTP-Ereignis und der Aktion ab, die für die Nachricht ausgeführt wird.

Verwenden Sie das Cmdlet **Set-TransportService** in der Exchange-Verwaltungsshell, um alle Konfigurationsaufgaben für die Agent-Protokollierung auszuführen. Die folgenden Optionen sind für die Agent-Protokollierung verfügbar:

  - Aktivieren bzw. Deaktivieren der Agent-Protokollierung. Standardmäßig ist diese aktiviert.

  - Angeben des Speicherorts der Agent-Protokolldateien. Der Standardwert ist "%ExchangeInstallPath%TransportRoles\\Logs\\Hub\\AgentLog".

  - Angeben einer maximalen Größe für einzelne Agent-Protokolldateien. Die Standardgröße ist 10 MB.

  - Angeben einer maximalen Größe für das Verzeichnis, in dem die Agent-Protokolldateien enthalten sind. Die Standardgröße ist 250 MB.

  - Angeben einer maximalen Alters für die Agent-Protokolldateien. Die Standardeinstellung beträgt 7 Tage.

Exchange verwendet die Umlaufprotokollierung, um Größe und Alter der Agent-Protokolle zu begrenzen und somit den von den Protokolldateien benötigten Festplattenspeicherplatz zu verringern.

**Inhalt**

Übersicht über Transport-Agents

Struktur der Agent-Protokolldateien

In das Agent-Protokoll geschriebene Informationen

Durchsuchen der Agent-Protokolle

## Übersicht über Transport-Agents

Agents können nur an bestimmten Punkten in der SMTP-Befehlsfolge angewendet werden, die zum Transport der Nachrichten durch den Transportdienst auf einem Postfachserver oder einem Edge-Transport-Server verwendet wird. Diese Zugriffspunkte in der SMTP-Befehlsfolge werden *SMTP-Ereignisse* genannt. Jeder Agent hat einen Prioritätswert, der zugewiesen werden kann. Die SMTP-Ereignisse müssen allerdings stets in einer bestimmten Reihenfolge auftreten. Deshalb hängt die Agent-Priorität vom SMTP-Ereignis ab. Wenn zwei Agents während desselben SMTP-Ereignisses auf eine Nachricht angewendet werden können, wird der Agent mit der höchsten Priorität zuerst auf die Nachricht angewendet.

Die folgende Tabelle enthält die SMTP-Ereignisse in der Reihenfolge ihres Auftretens sowie die Agents, die Informationen in das Agent-Protokoll schreiben (in der Prioritätsreihenfolge vom höchsten zum niedrigsten Wert für jedes SMTP-Ereignis).

### SMTP-Ereignisse in der Reihenfolge ihres Auftretens sowie die Agents, die Informationen in das Agent-Protokoll schreiben, in der Prioritätsreihenfolge für jedes SMTP-Ereignis

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>SMTP-Ereignis</th>
<th>Agent</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>OnConnect</strong></p></td>
<td><p>Verbindungsfilter-Agent</p></td>
</tr>
<tr class="even">
<td><p><strong>OnMailCommand</strong></p></td>
<td><p>Verbindungsfilter-Agent</p>
<p>Absenderfilter-Agent</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnRcptCommand</strong></p></td>
<td><p>Verbindungsfilter-Agent</p>
<p>Empfängerfilter-Agent</p></td>
</tr>
<tr class="even">
<td><p><strong>OnEndOfHeaders</strong></p></td>
<td><p>Verbindungsfilter-Agent</p>
<p>Sender ID-Agent</p>
<p>Absenderfilter-Agent</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnEndOfData</strong></p></td>
<td><p>Edge-Regel-Agent</p>
<p>Inhaltsfilter-Agent</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Der Verbindungsfilter-Agent und der Agent für Edge-Regeln sind auf Postfachservern nicht verfügbar.



Weitere Informationen zu Agents, SMTP-Ereignissen und Agent-Priorität finden Sie unter [Transport-Agents](transport-agents-exchange-2013-help.md).

Zurück zum Seitenanfang

## Struktur der Agent-Protokolldateien

Die Agent-Protokolle befinden sich unter "%ExchangeInstallPath%TransportRoles\\Logs\\Hub\\AgentLog".

Die Benennungskonvention für die Agent-Protokolldateien lautet AGENTLOG*yyymmdd-nnnn*.log. Die Platzhalter enthalten die folgenden Informationen:

  - Der Platzhalter *yyyymmdd* entspricht dem UTC-Datum (Coordinated Universal Time, koordinierte Weltzeit), an dem die Protokolldatei erstellt wurde. Dabei entspricht *yyyy* dem Jahr, *mm* dem Monat und *dd* dem Tag.

  - Der Platzhalter *nnnn* ist eine Instanznummer, die mit dem Wert 1 für jeden Tag beginnt.

Die Daten werden solange in die Protokolldatei geschrieben, bis die Dateigröße den maximal festgelegten Wert erreicht. Dann wird eine neue Datei mit der nächsthöheren Instanznummer geöffnet. Dieser Vorgang wird während des ganzen Tags wiederholt. Bei der Umlaufprotokollierung werden die ältesten Protokolldateien gelöscht, wenn das Agent-Protokollverzeichnis die festgelegte Maximalgröße oder eine Protokolldatei das festgelegte Höchstalter erreicht.

Bei den Agent-Protokolldateien handelt es sich um Textdateien, die Daten im CSV-Dateiformat (Comma Separated Value) enthalten. Jede Agent-Protokolldatei enthält eine Kopfzeile mit den folgenden Informationen:

  - **\#Software**   Name der Software, mit der die Agent-Protokolldatei erstellt wurde. In der Regel lautet der Wert "Microsoft Exchange Server".

  - **\#Version**   Versionsnummer der Software, mit der die Agent-Protokolldatei erstellt wurde. Der aktuelle Wert lautet 15.0.0.0.

  - **\#Log-Type**   Wert des Protokolltyps, in diesem Fall **Agent Log**.

  - **\#Date**   Datum und Uhrzeit (UTC) der Erstellung der Protokolldatei. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: *yyyy-mm-dd*T*hh:mm:ss.fff*Z, wobei *yyyy* = Jahr, *mm* = Monat, *dd* = Tag. T gibt an, dass eine Zeitangabe folgt. *hh* = Stunde,*mm* = Minute, *ss* = Sekunde, *fff* = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.

  - **\#Fields**   Durch Kommas getrennte Feldnamen, die in den Agent-Protokolldateien verwendet werden.

Zurück zum Seitenanfang

## In das Agent-Protokoll geschriebene Informationen

Im Agent-Protokoll werden die einzelnen Agent-Transaktionen jeweils in einer einzelnen Zeile gespeichert. Die in den einzelnen Zeilen gespeicherten Informationen sind nach Feldern angeordnet. Diese Felder sind durch Kommas getrennt. Anhand des Feldnamens kann im Allgemeinen festgestellt werden, welchen Informationstyp das jeweilige Feld enthält. Einige Felder sind jedoch ggf. leer. Oder der Typ der im Feld gespeicherten Information kann sich basierend auf dem Agent oder der Aktion ändern, die vom Agent auf die Nachricht angewendet wird. In der folgenden Tabelle werden die Felder beschrieben, die zum Klassifizieren der einzelnen Agent-Transaktionen verwendet werden.

### Zum Klassifizieren der einzelnen Agent-Transaktionen verwendete Felder

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feld</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Timestamp</strong></p></td>
<td><p>Datum und Uhrzeit des Agent-Ereignisses im UTC-Format. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, wobei <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag. T gibt an, dass eine Zeitangabe folgt. <em>hh</em> = Stunde,<em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionId</strong></p></td>
<td><p>Eindeutige SMTP-Sitzungs-ID. Diese ID wird als 16-stelliger Hexadezimalwert angegeben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LocalEndpoint</strong></p></td>
<td><p>Lokale IP-Adresse und Portnummer, die die Nachricht angenommen hat. Für SMTP-Sitzungen wird meist Port 25 verwendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>RemoteEndpoint</strong></p></td>
<td><p>IP-Adresse und Portnummer des vorherigen SMTP-Servers, der sich zum Übermitteln der Nachricht mit diesem Server verbunden hat. Wenn Internetnachrichten über einen Edge-Transport-Server im Umkreisnetzwerk übermittelt werden, weist der Wert von <strong>RemoteEndpoint</strong> im Agent-Protokoll auf dem Postfachserver die IP-Adresse des Edge-Transport-Servers auf. Auch wenn die Nachricht über SMTP übertragen wird, ist die vom absendenden Server verwendete Portnummer eine beliebige Zahl größer als 1.024.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EnteredOrgFromIP</strong></p></td>
<td><p>Die IP-Adresse des SMTP-Remoteservers, der zum Zustellen der Nachricht zuerst eine Verbindung mit der Exchange-Organisation hergestellt hat. Auf einem Edge-Transport-Server ist der Wert von <strong>RemoteEndpoint</strong> und <strong>EnteredOrgFromIP</strong> identisch. Antispam-Agents verwenden die IP-Adresse in <strong>EnteredOrgFromIP</strong>, um eine Nachricht zu untersuchen.</p></td>
</tr>
<tr class="even">
<td><p><strong>MessageId</strong></p></td>
<td><p>Wert des Kopfzeilenfelds <code>MessageID</code>. Ist dieser Wert leer, weist der Exchange-Transportserver einen beliebigen Wert zu, jedoch nur, wenn die Nachricht angenommen wird. Nach der Zuweisung eines Werts, ist der Wert von <code>MessageID</code> für die Lebensdauer der Nachricht konstant.</p></td>
</tr>
<tr class="odd">
<td><p><strong>P1FromAddress</strong></p></td>
<td><p>E-Mail-Adresse des Absenders, die unter <code>MAIL FROM</code> im Nachrichten-Envelope angegeben ist. Dieser Wert dient zum Transportieren der Nachricht zwischen SMTP-Messagingservern. Dieser Wert dient zum Vergleich mit dem Wert von <strong>P2FromAddresses</strong>, um zu ermitteln, ob die Absenderadresse im Nachrichtenkopf gefälscht ist.</p></td>
</tr>
<tr class="even">
<td><p><strong>P2FromAddresses</strong></p></td>
<td><p>E-Mail-Adresse des Absenders im Kopfzeilenfeld <code>From</code> oder im Kopfzeilenfeld <code>Sender</code> im Nachrichtenkopf.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Recipient</strong></p></td>
<td><p>E-Mail-Adresse der Empfänger. Obgleich die ursprüngliche Nachricht mehrere Empfänger enthalten kann, wird im Agent-Protokoll pro Zeile nur ein Empfänger angezeigt.</p></td>
</tr>
<tr class="even">
<td><p><strong>NumRecipients</strong></p></td>
<td><p>Gesamtanzahl der Empfänger in der ursprünglichen Nachricht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Agent</strong></p></td>
<td><p>Name des Agents, der die Aktion durchführt. Die folgenden Werte sind möglich:</p>
<ul>
<li><p>Inhaltsfilter-Agent</p></li>
<li><p>Empfängerfilter-Agent</p></li>
<li><p>Absenderfilter-Agent</p></li>
<li><p>Sender ID-Agent</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Event</strong></p></td>
<td><p>SMTP-Ereignis, bei dem der Agent die Aktion ausgeführt hat. Der Wert von <strong>Event</strong> hängt vom Agent ab. Die SMTP-Ereignisse, die jedem Agent zur Verfügung stehen, wurden bereits in der ersten Tabelle weiter oben in diesem Thema beschrieben. Die möglichen Werte für <strong>Event</strong> lauten wie folgt:</p>
<ul>
<li><p>OnConnect</p></li>
<li><p>OnEndOfHeaders</p></li>
<li><p>OnEndOfData</p></li>
<li><p>OnMailCommand</p></li>
<li><p>OnRcptCommand</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Action</strong></p></td>
<td><p>Vom Agent auf die Nachricht angewendete Aktion. Die möglichen Werte für <strong>Action</strong> lauten wie folgt:</p>
<ul>
<li><p>AcceptMessage</p></li>
<li><p>DeleteMessage</p></li>
<li><p>DeleteRecipients</p></li>
<li><p>Disconnect</p></li>
<li><p>QuarantineMessage</p></li>
<li><p>QuarantineRecipients</p></li>
<li><p>RejectAuthentication</p></li>
<li><p>RejectCommand</p></li>
<li><p>RejectConnection</p></li>
<li><p>RejectMessage</p></li>
<li><p>RejectRecipients</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>SmtpResponse</strong></p></td>
<td><p>Enhanced SMTP-Antwort gemäß der Definition in RFC 2034.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reason</strong></p></td>
<td><p>Grund für die vom Agent durchgeführte Aktion.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReasonData</strong></p></td>
<td><p>Beschreibende Details zu der vom Agent durchgeführten Aktion.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Durchsuchen der Agent-Protokolle

Sie können das Cmdlet **Get-AgentLog** und das Skript **Get-AntiSpamFilteringReport.ps1** verwenden, um die Agent-Protokolle zu durchsuchen.

Das Skript **Get-AntiSpamFilteringReport.ps1** befindet sich in `%ExchangeInstallPath%Scripts`. Sie müssen das Skript im Ordner **Scripts** in der Shell ausführen. Führen Sie den folgenden Befehl aus, um den Speicherort der Shell in den Ordner **Scripts** zu ändern.

    Cd $env:ExchangeInstallPath\Scripts

Um das Skript im Ordner **Scripts** auszuführen, verwenden Sie folgende Syntax:

    .\Get-AntiSpamFilteringReport.ps1 -report <ReportValue> [<OptionalParameters>]

Führen Sie den folgenden Befehl aus, um Einzelheiten zum Verwenden des Skripts zu erfahren:

    Get-Help -Detailed .\Get-AntiSpamFilteringReport.ps1

Zurück zum Seitenanfang

