---
title: 'Protokollierung: Exchange 2013 Help'
TOCTitle: Protokollierung
ms:assetid: 40da446b-bcc3-4a97-ace7-a54f6ddebd79
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997624(v=EXCHG.150)
ms:contentKeyID: 50475478
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Protokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Protokollaufzeichnungen enthalten SMTP-Unterhaltungen, die zwischen Messagingservern als Teil der Nachrichtenübermittlung stattfinden. Diese SMTP-Kommunikation erfolgt auf Sende- und Empfangsconnectors, die im Front-End-Transport-Dienst auf den Clientzugriffsservern, dem Transportdienst auf den Postfachservern und dem Postfachtransportdienst auf Postfachservern vorliegen. Sie können Protokolle zur Diagnose von Problemen bei der E-Mail-Nachrichtenübermittlung verwenden.

Die Protokollierung ist standardmäßig für alle Sende- und Empfangsconnectors deaktiviert. Die Protokollierung wird auf jedem Connector aktiviert oder deaktiviert. Weitere Protokollierungsoptionen sind für alle Empfangs- oder Sendeconnectors festgelegt, die in den jeweiligen Transportdiensten auf dem Server vorliegen. Alle Empfangsconnectors in einem Transportdienst verwenden gemeinsame Protokolldateien und -optionen. Diese Protokolldateien und -optionen werden getrennt von den Protokolldateien und -optionen der Sendeconnectors im Transportdienst auf demselben Server verwaltet.

Die folgenden Optionen stehen für die Protokollaufzeichnungen aller Sende- oder Empfangsconnectors im jeweiligen Transportdienst auf dem Exchange-Server zur Verfügung:

  - Festlegen des Speicherorts für die Protokolldateien der Sende- oder Empfangsconnectors.

  - Festlegen der maximalen Größe für die Protokolldateien der Sende- oder Empfangsconnectors. Die Standardgröße ist 10 MB.

  - Festlegen der maximalen Größe des Verzeichnisses, das die Protokolldateien der Sende- oder Empfangsconnectors enthält. Die Standardgröße liegt bei 250 MB.

  - Festlegen des Höchstalters für die Protokolldateien der Sende- oder Empfangsconnectors. Die Standardeinstellung beträgt 30 Tage.

Standardmäßig verwendet Exchange die Umlaufprotokollierung, um Größe und Alter der Protokolldateien zu begrenzen und somit den von den Protokolldateien benötigten Festplattenspeicherplatz zu verringern.

Ein besonderer Sendeconnector, der organisationsinterne Sendeconnector, liegt im Transportdienst auf jedem Postfachserver und im Front-End-Transport-Dienst auf jedem Clientzugriffsserver vor. Dieser Connector wird implizit erstellt, ist nicht sichtbar und erfordert keine Verwaltung. Der organisationsinterne Sendeconnector wird von den folgenden Transportdiensten verwendet:

  - **Transport-Service auf Postfachservern**
    
      - Weiterleiten von Nachrichten an den Transportdienst und den Postfachtransportdienst auf anderen Exchange 2013-Postfachservern in der Organisation.
    
      - Weiterleiten von Nachrichten an andere Exchange 2007- oder Exchange 2010-Hub-Transport-Server in der Organisation.
    
      - Weiterleiten von Nachrichten an Edge-Transport-Server im Umkreisnetzwerk.

  - **Front-End-Transport-Dienst auf Clientzugriffsservern**   Sorgen für die Weiterleitung von Nachrichten an den Transportdienst auf Exchange 2013-Postfachservern in der Organisation.

Ein vergleichbarer Sendeconnector, der Postfachzustellungs-Sendeconnector, liegt im Postfachtransportdienst auf jedem Postfachserver vor. Dieser Connector wird ebenfalls implizit erstellt, ist nicht sichtbar und muss nicht verwaltet werden. Der Postfachzustellungs-Sendeconnector wird zum Weiterleiten von Nachrichten an den Transportdienst und den Postfachtransportdienst auf anderen Postfachservern in der Organisation verwendet.

Die Protokollprotokollierung für den Postfachzustellungs-Sendeconnector ist standardmäßig deaktiviert. Sie können die Protokollierung für den Postfachzustellungs-Sendeconnector mithilfe des Parameters *MailboxDeliveryConnectorProtocolLoggingLevel* für das Cmdlet **Set-MailboxTransportService** aktivieren bzw. deaktivieren. Wenn Sie die Protokollierung für den Postfachzustellungs-Sendeconnector aktivieren, erfolgt diese in den Protokolldateien des Sendeconnectors für den Postfachtransportdienst auf dem Postfachserver.

**Inhalt**

Struktur der Protokolldateien

In das Protokoll geschriebene Informationen

## Struktur der Protokolldateien

Standardmäßig befinden sich die Protokolldateien an folgenden Speicherorten:

  - **Protokolldateien des Empfangsconnectors für den Transportdienst auf den Postfachservern**   %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpReceive

  - **Protokolldateien des Empfangsconnectors für den Postfachtransportdienst auf den Postfachservern**   %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpReceive

  - **Protokolldateien des Empfangsconnectors für den Front-End-Transport-Dienst auf den Clientzugriffsservern**   %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpReceive

  - **Protokolldateien des Sendeconnectors für den Transportdienst auf den Postfachservern**   %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpSend

  - **Protokolldateien des Sendeconnectors für den Postfachtransportdienst auf den Postfachservern**   %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpSend

  - **Protokolldateien des Sendeconnectors für den Front-End-Transport-Dienst auf den Clientzugriffsservern**   %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpSend

Die Namenskonvention für Protokolldateien in sämtlichen Protokollverzeichnissen lautet *prefixyyyymmdd-nnnn*.log. Die Platzhalter enthalten die folgenden Informationen:

  - Das Platzhalter*präfix* für Sendeconnectors lautet SEND und für Empfangsconnectors RECV.

  - Der Platzhalter *yyyymmdd* steht für das UTC-Datum (Coordinated Universal Time, koordinierte Weltzeit), an dem die Protokolldatei erstellt wurde. Für den Platzhalter gilt: *yyyy* = Jahr, *mm* = Monat und *dd* = Tag.

  - Der Platzhalter *nnnn* ist eine Instanznummer, die mit dem Wert 1 für jeden Tag beginnt.

Die Daten werden solange in die Protokolldatei geschrieben, bis die Dateigröße den maximal festgelegten Wert erreicht. Dann wird eine neue Datei mit der nächsthöheren Instanznummer geöffnet. Dieser Vorgang wird während des ganzen Tages wiederholt. Bei der Umlaufprotokollierung werden die ältesten Protokolldateien gelöscht, wenn das Protokollverzeichnis die festgelegte Maximalgröße oder eine Protokolldatei das festgelegte Höchstalter erreicht.

Bei den Protokolldateien handelt es sich um Textdateien, die Daten im CSV-Dateiformat enthalten. Jede Protokolldatei enthält eine Kopfzeile mit den folgenden Informationen:

  - **\#Software:**    Der Name der Software, mit der die Protokolldatei erstellt wurde. In der Regel lautet der Wert "Microsoft Exchange Server".

  - **\#Version:**    Die Versionsnummer der Software, mit der die Protokolldatei erstellt wurde. Der aktuelle Wert lautet 15.0.0.0.

  - **\#Log-Type**   Dieses Feld gibt an, ob es sich um das Protokoll für das SMTP-Empfangsprotokoll oder das SMTP-Sendeprotokoll handelt.

  - **\#Date:**    Datum und Uhrzeit (UTC) der Erstellung der Protokolldatei. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: *yyyy-mm-dd*T*hh:mm:ss.fff*Z, wobei *yyyy* = Jahr, *mm* = Monat, *dd* = Tag. T gibt an, dass eine Zeitangabe folgt. *hh* = Stunde,*mm* = Minute, *ss* = Sekunde, *fff* = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.

  - **\#Fields:**    Durch Trennzeichen getrennte Feldnamen, die in den Protokolldateien verwendet werden.

Zurück zum Seitenanfang

## In das Protokoll geschriebene Informationen

Bei der Protokollaufzeichnung wird jedes SMTP-Protokollereignis in einer separaten Zeile der Protokolldatei gespeichert. Die in den einzelnen Zeilen gespeicherten Informationen sind nach Feldern angeordnet. Diese Felder sind durch Trennzeichen getrennt. In der folgenden Tabelle werden die Felder beschrieben, die zum Klassifizieren der einzelnen Protokolle verwendet werden.

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
<td><p><strong>date-time</strong></p></td>
<td><p>UTC-Datum und -Uhrzeit des Protokollereignisses. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, wobei <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag. T gibt an, dass eine Zeitangabe folgt. <em>hh</em> = Stunde,<em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.</p></td>
</tr>
<tr class="even">
<td><p><strong>connector-id</strong></p></td>
<td><p>Der DN (Distinguished Name) des Connectors, der dem SMTP-Ereignis zugeordnet ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>session-id</strong></p></td>
<td><p>Eine GUID, die für jede SMTP-Sitzung eindeutig ist. Für jedes Ereignis, das dieser SMTP-Sitzung zugeordnet ist, wird dieselbe GUID verwendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>sequence-number</strong></p></td>
<td><p>Ein Zähler, der bei 0 beginnt und für jedes Ereignis innerhalb derselben SMTP-Sitzung erhöht wird.</p></td>
</tr>
<tr class="odd">
<td><p><strong>local-endpoint</strong></p></td>
<td><p>Der lokale Endpunkt einer SMTP-Sitzung. Dieser setzt sich aus einer IP-Adresse und einer TCP-Portnummer zusammen, die als <em>&lt;IP-Adresse&gt;</em>:<em>&lt;Port&gt;</em> formatiert ist.</p></td>
</tr>
<tr class="even">
<td><p><strong>remote-endpoint</strong></p></td>
<td><p>Der Remoteendpunkt einer SMTP-Sitzung. Dieser setzt sich aus einer IP-Adresse und einer TCP-Portnummer zusammen, die als <em>&lt;IP-Adresse&gt;</em>:<em>&lt;Port&gt;</em> formatiert ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>event</strong></p></td>
<td><p>Ein einzelnes Zeichen, mit dem das Protokollereignis dargestellt wird. Die möglichen Werte für das Ereignis lauten wie folgt:</p>
<ul>
<li><p><strong>+</strong>   Verbinden</p></li>
<li><p><strong>-</strong>   Trennen</p></li>
<li><p><strong>&gt;</strong>   Senden</p></li>
<li><p><strong>&lt;</strong>   Empfangen</p></li>
<li><p><strong>*</strong>   Informationen</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>data</strong></p></td>
<td><p>Textinformationen, die dem SMTP-Ereignis zugeordnet werden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>context</strong></p></td>
<td><p>Zusätzliche Kontextinformationen, die dem SMTP-Ereignis zugeordnet werden können.</p></td>
</tr>
</tbody>
</table>


Eine einzelne SMTP-Unterhaltung, die das Senden oder Empfangen einer einzelnen E-Mail-Nachricht umfasst, erzeugt mehrere SMTP-Ereignisse. Diese SMTP-Ereignisse werden in mehreren Zeilen in das Protokoll geschrieben. Mehrere SMTP-Unterhaltungen, die das Senden und Empfangen mehrerer E-Mail-Nachrichten umfassen, können gleichzeitig stattfinden. Auf diese Weise werden Protokolleinträge aus verschiedenen SMTP-Unterhaltungen erstellt, die miteinander verschränkt sind. Die Felder mit der Sitzungs-ID- und der Sequenznummer können verwendet werden, um die Protokolleinträge nach SMTP-Unterhaltung zu sortieren.

Zurück zum Seitenanfang

