---
title: 'Verbindungsprotokollierung: Exchange 2013 Help'
TOCTitle: Verbindungsprotokollierung
ms:assetid: c31fd710-4ae4-4d9a-8936-d056e7ca2748
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124500(v=EXCHG.150)
ms:contentKeyID: 50476645
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbindungsprotokollierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit der Konnektivitätsprotokollierung wird die ausgehende Verbindungsaktivität bei der Übermittlung von Nachrichten von einem Transportdienst an den Exchange-Server protokolliert. Der Zweck der Konnektivitätsprotokollierung ist nicht das Verfolgen der Übertragung einzelner E-Mails. Stattdessen wird mit der Konnektivitätsprotokollierung die Verbindungsaktivität von der Quelle zum Ziel nachverfolgt, ganz gleich, wie viele Nachrichten übermittelt werden. Die Konnektivitätsprotokollierung ist im Front-End-Transport-Dienst auf Clientzugriffsservern, im Transportdienst auf Postfachservern und im Postfachtransportdienst auf Postfachservern verfügbar. In der folgenden Liste wird der im Konnektivitätsprotokoll aufgezeichnete Informationstyp erläutert:

  - Quelle

  - Destination

  - Daten zur DNS-Auflösung

  - Detaillierte Informationen zu Verbindungsfehlern

  - Anzahl von Nachrichten und übertragene Bytes

Verwenden Sie die Cmdlets **Set-TransportService**, **Set-FrontEndTransportService** und **Set-MailboxTransportService** in der Exchange-Verwaltungsshell, um alle Konfigurationsaufgaben für die Konnektivitätsprotokollierung durchzuführen. Die folgenden Optionen sind für Konnektivitätsprotokolle verfügbar:

  - Aktivieren bzw. Deaktivieren der Konnektivitätsprotokollierung. Standardmäßig ist diese aktiviert.

  - Angeben des Speicherorts der Konnektivitätsprotokolldateien.

  - Angeben einer maximalen Größe für einzelne Konnektivitätsprotokolldateien. Die Standardgröße beträgt 10 MB.

  - Angeben einer maximalen Größe für das Verzeichnis, in dem die Konnektivitätsprotokolldateien enthalten sind. Die Standardgröße ist 1.000 MB.

  - Angeben einer maximalen Alters für die Konnektivitätsprotokolldateien. Die Standardeinstellung beträgt 30 Tage.

Standardmäßig verwendet Exchange die Umlaufprotokollierung, um Größe und Alter der Konnektivitätsprotokolldateien zu begrenzen und somit den von den Protokolldateien benötigten Festplattenspeicherplatz zu verringern.

**Inhalt**

Struktur der Konnektivitätsprotokolldateien

Daten, die in das Konnektivitätsprotokoll geschrieben werden

## Struktur der Konnektivitätsprotokolldateien

Standardmäßig befinden sich die Konnektivitätsprotokolldateien an folgenden Speicherorten:

  - **Transport service**   %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\Connectivity

  - **Front End Transport service**   %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\Connectivity

  - **Mailbox Transport service**   %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\Connectivity

Die Namenskonvention für die Konnektivitätsprotokolldateien lautet CONNECTLOG*yyymmdd-nnnn*.log. Die Platzhalter enthalten die folgenden Informationen:

  - Der Platzhalter *yyyymmdd* entspricht dem UTC-Datum (Coordinated Universal Time, koordinierte Weltzeit), an dem die Protokolldatei erstellt wurde. Für diesen Platzhalter gilt Folgendes: *yyyy* = Jahr, *mm* = Monat und *dd* = Tag.

  - Der Platzhalter *nnnn* ist eine Instanznummer, die mit dem Wert 1 für jeden Tag beginnt.

Die Daten werden solange in die Protokolldatei geschrieben, bis die Dateigröße den maximal festgelegten Wert erreicht. Dann wird eine neue Datei mit der nächsthöheren Instanznummer geöffnet. Dieser Vorgang wird während des ganzen Tags wiederholt. Bei der Umlaufprotokollierung werden die ältesten Protokolldateien gelöscht, wenn das Konnektivitätsprotokollverzeichnis die festgelegte Maximalgröße oder eine Protokolldatei das festgelegte Höchstalter erreicht.

Bei den Konnektivitätsprotokolldateien handelt es sich um Textdateien, die Daten im CSV-Dateiformat (Comma Separated Value) enthalten. Jede Konnektivitätsprotokolldatei enthält eine Kopfzeile mit den folgenden Informationen:

  - **\#Software**   Name der Software, mit der die Konnektivitätsprotokolldatei erstellt wurde. In der Regel lautet der Wert "Microsoft Exchange Server".

  - **\#Version**   Versionsnummer der Software, mit der die Konnektivitätsprotokolldatei erstellt wurde. Der aktuelle Wert lautet 15.0.0.0.

  - **\#Log-Type**   Wert des Protokolltyps, in diesem Fall **Transport Connectivity Log**.

  - **\#Date**   Datum und Uhrzeit (UTC) der Erstellung der Protokolldatei. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: *yyyy-mm-dd*T*hh:mm:ss.fff*Z, wobei *yyyy* = Jahr, *mm* = Monat, *dd* = Tag. T gibt an, dass eine Zeitangabe folgt. *hh* = Stunde,*mm* = Minute, *ss* = Sekunde, *fff* = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.

  - **\#Fields**   Durch Kommas getrennte Feldnamen, die in den Konnektivitätsprotokolldateien verwendet werden.

Zurück zum Seitenanfang

## Daten, die in das Konnektivitätsprotokoll geschrieben werden

Das Konnektivitätsprotokoll speichert alle Verbindungsereignisse des ausgehenden Transportdiensts in einer einzelnen Zeile im Konnektivitätsprotokoll. Die in den einzelnen Zeilen gespeicherten Informationen sind nach Feldern angeordnet. Diese Felder sind durch Kommas getrennt. In der folgenden Tabelle werden die Felder beschrieben, mit denen jedes ausgehende Verbindungsereignis klassifiziert wird.

### Felder zum Klassifizieren der einzelnen Verbindungsereignisse

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
<td><p><strong>date-time</strong></p></td>
<td><p>Datum und -Uhrzeit des Verbindungsereignisses im UTC-Format. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, wobei <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag. T gibt an, dass eine Zeitangabe folgt. <em>hh</em> = Stunde,<em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.</p></td>
</tr>
<tr class="even">
<td><p><strong>session</strong></p></td>
<td><p>GUID, die für jede SMTP-Sitzung eindeutig ist. Für jedes Ereignis, das dieser SMTP-Sitzung zugeordnet ist, wird dieselbe GUID verwendet. Bei MAPI-Sitzungen im Postfachtransportdienst bleibt das Feld &quot;session&quot; leer.</p></td>
</tr>
<tr class="odd">
<td><p><strong>source</strong></p></td>
<td><p><strong>SMTP</strong> für SMTP-Verbindungen, <strong>MAPI</strong> für Postfachtransportdienst-Verbindungen zur lokalen Postfachdatenbank.</p></td>
</tr>
<tr class="even">
<td><p><strong>destination</strong></p></td>
<td><p>Name des Ziels.</p></td>
</tr>
<tr class="odd">
<td><p><strong>direction</strong></p></td>
<td><p>Einzelnes Zeichen, das den Anfang, die Mitte und das Ende der Verbindung darstellt. Mögliche Werte für das Richtungsfeld:</p>
<ul>
<li><p><strong>+</strong>   Verbinden</p></li>
<li><p><strong>-</strong>   Trennen</p></li>
<li><p><strong>&gt;</strong>   Senden</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>description</strong></p></td>
<td><p>Textinformationen für das Verbindungsereignis. Die folgenden Werte sind Beispielwerte für ein Beschreibungsfeld:</p>
<ul>
<li><p>Anzahl und Größe von übertragenen Nachrichten</p></li>
<li><p>Auflösungsinformationen für DNS MX-Ressourcendatensätze für Zieldomänen</p></li>
<li><p>DNS-Auflösungsinformationen für Zielpostfachserver</p></li>
<li><p>Meldungen zum Verbindungsaufbau</p></li>
<li><p>Meldungen zu Verbindungsfehlern</p></li>
</ul></td>
</tr>
</tbody>
</table>


Wenn der Transportdienst eine Verbindung zu einem Ziel herstellt, ist er möglicherweise darauf vorbereitet, eine oder mehrere Nachrichten zu senden. Die Verbindungs- und Nachrichtenzustellungsprozesse erzeugen mehrere Ereignisse, die in mehrere Zeilen des Konnektivitätsprotokolls geschrieben werden. Gleichzeitige Verbindungen mit unterschiedlichen Zielen erzeugen Konnektivitätsprotokolleinträge für verschiedene miteinander verbundene Ziele. Die Felder **date-time**, **session**, **source** und **direction** können jedoch verwendet werden, um die Konnektivitätsprotokolleinträge für die einzelnen Verbindungen von Anfang bis Ende anzuordnen.

Zurück zum Seitenanfang

