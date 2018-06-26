---
title: 'Protokollierung für POP3 und IMAP4: Exchange 2013 Help'
TOCTitle: Protokollierung für POP3 und IMAP4
ms:assetid: 212ed3d5-0c98-4346-a860-1cfcac5d73c4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335141(v=EXCHG.150)
ms:contentKeyID: 50554815
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Protokollierung für POP3 und IMAP4

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie anhand der Protokollierung die POP3- und IMAP4-Verbindungen in einer Exchange-Umgebung überprüfen. Dies kann bei der Problembehandlung in Bezug auf POP3- oder IMAP4-Leistung hilfreich sein.

## Aktivieren der POP3- und IMAP4-Protokollierung

Sie können die Protokollierung mithilfe der Exchange-Verwaltungsshell aktivieren, deaktivieren oder ändern. Wenn Sie die Protokollierung mithilfe der Shell aktivieren, werden die Standardprotokollierungseinstellungen verwendet. In den meisten Fällen sind die Standardeinstellungen ausreichend.

Alternativ können Sie Protokollierungsoptionen aktivieren, deaktivieren und ändern, indem Sie die Dateien "Microsoft.Exchange.Pop3.exe.config" und "Microsoft.Exchange.Imap4.exe.config" auf dem Microsoft Exchange Server 2013-Clientzugriffsserver bearbeiten. Weitere Informationen zum Verwalten von POP3- und IMAP4-Protokollierungseinstellungen finden Sie unter [Konfigurieren der Protokollierung für POP3 und IMAP4](configure-protocol-logging-for-pop3-and-imap4-exchange-2013-help.md).

## Überprüfen des Protokolls

Bei den Protokolldateien handelt es sich um Textdateien, die Daten im CSV-Dateiformat (Comma-Separated Value, durch Trennzeichen getrennte Datei) enthalten. Das Protokoll speichert jedes Protokollereignis in einer Zeile. Die in den einzelnen Zeilen gespeicherten Informationen sind nach Feldern angeordnet. Diese Felder sind durch Kommas getrennt. In der folgenden Tabelle werden die Felder beschrieben, die zum Klassifizieren einzelner Protokollereignisse verwendet werden.

### Felder, die zum Klassifizieren einzelner Protokollereignisse verwendet werden

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
<td><p>date-time</p></td>
<td><p>Das Datum und die Uhrzeit des Protokollereignisses. Der Wert wird formatiert als <em>yyyy-mm-ddhh:mm:ss.fffZ</em>, mit <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag, <em>hh</em> = Stunde, <em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde und <em>Z</em> = Zulu. Zulu ist ein anderes Verfahren zur Kennzeichnung der koordinierten Weltzeit (UTC, Universal Coordinated Time).</p></td>
</tr>
<tr class="even">
<td><p>connector-id</p></td>
<td><p>Dieses Feld wird nicht für die POP3- und IMAP4-Protokollierung verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>session-id</p></td>
<td><p>Eine GUID, mit der die SMTP-Sitzung eindeutig identifiziert wird, die mit einem Protokollereignis verknüpft ist.</p></td>
</tr>
<tr class="even">
<td><p>sequence-number</p></td>
<td><p>Ein Zähler, der bei 0 beginnt und für jedes Ereignis innerhalb derselben Sitzung erhöht wird.</p></td>
</tr>
<tr class="odd">
<td><p>local-endpoint</p></td>
<td><p>Der lokale Endpunkt einer POP3- oder IMAP4-Sitzung. Er setzt sich aus einer IP-Adresse und TCP-Portnummer im folgenden Format zusammen: <em>&lt;IP-Adresse&gt;</em>:<em>&lt;Port&gt;</em>.</p></td>
</tr>
<tr class="even">
<td><p>remote-endpoint</p></td>
<td><p>Der Remoteendpunkt einer POP3- oder IMAP4-Sitzung. Er setzt sich aus einer IP-Adresse und TCP-Portnummer im folgenden Format zusammen: <em>&lt;IP-Adresse&gt;</em>:<em>&lt;Port&gt;</em>.</p></td>
</tr>
<tr class="odd">
<td><p>event</p></td>
<td><p>Ein einzelnes Zeichen, mit dem das Protokollereignis dargestellt wird. Die möglichen Werte für das Ereignis lauten wie folgt:</p>
<ul>
<li><p>+   Verbinden</p></li>
<li><p>-   Trennen</p></li>
<li><p>&gt;   Senden</p></li>
<li><p>&lt;   Empfangen</p></li>
<li><p>*   Informationen</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>data</p></td>
<td><p>Textdaten, die dem POP3- oder IMAP4-Ereignis zugeordnet sind.</p></td>
</tr>
<tr class="odd">
<td><p>context</p></td>
<td><p>Dieses Feld wird nicht für die POP3- und IMAP4-Protokollierung verwendet.</p></td>
</tr>
</tbody>
</table>

