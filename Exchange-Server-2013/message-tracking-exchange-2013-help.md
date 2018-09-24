---
title: 'Nachrichtenverfolgung: Exchange 2013 Help'
TOCTitle: Nachrichtenverfolgung
ms:assetid: bada2ea7-6d7c-4630-b7f1-67f56818f0ff
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124375(v=EXCHG.150)
ms:contentKeyID: 51409336
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichtenverfolgung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In Microsoft Exchange Server 2013 ist das Nachrichtenverfolgungsprotokoll eine detaillierte Aufzeichnung aller Nachrichtenaktivitäten, d. h. Übertragungen in und aus dem Transportdienst auf Postfachservern, Postfächern auf Postfachservern und Edge-Transport-Servern. Sie können Nachrichtenverfolgungsprotokolle für forensische Nachrichtenanalysen, Nachrichtenübermittlungsanalysen, die Berichterstellung und die Problembehandlung verwenden.

In Exchange 2013 können Sie mit den Cmdlets **Set-TransportService** und **Set-MailboxServer** alle Konfigurationsaufgaben für die Nachrichtenverfolgung ausführen, da sich der Transportdienst und die Postfächer auf dem Exchange 2013-Postfachserver befinden. Mit diesen Cmdlets können die folgenden Konfigurationsänderungen an der Nachrichtenverfolgung vorgenommen werden:

  - Aktiveren und Deaktivieren der Nachrichtenverfolgung. Standardmäßig ist diese aktiviert.

  - Angeben des Speicherorts der Nachrichtenverfolgungs-Protokolldateien.

  - Angeben einer Maximalgröße für die einzelnen Nachrichtenverfolgungs-Protokolldateien. Der Standardwert beträgt 10 MB.

  - Angeben einer Maximalgröße für das Verzeichnis, das die Protokolldateien der Nachrichtenverfolgung enthält. Der Standardwert beträgt 1.000 MB.

  - Angeben des Höchstalters für die Protokolldateien der Nachrichtenverfolgung: Der Standardwert beträgt 30 Tage.

  - Aktivieren und Deaktivieren der Nachrichtenbetreffprotokollierung in den Nachrichtenverfolgungsprotokollen. Standardmäßig ist diese aktiviert.


> [!NOTE]
> Sie können auch über die Exchange-Verwaltungskonsole die Nachrichtenverfolgung aktivieren oder deaktivieren und den Speicherort der Protokolldateien der Nachrichtenverfolgung angeben.



Standardmäßig verwendet Exchange die Umlaufprotokollierung, um Größe und Alter der Nachrichtenverfolgungsprotokolle zu begrenzen und somit den von diesen Protokolldateien benötigten Festplattenspeicherplatz zu verringern.

**Inhalt**

Durchsuchen des Nachrichtenverfolgungsprotokolls

Struktur der Protokolldateien der Nachrichtenverfolgung

Felder in den Protokolldateien für die Nachrichtenverfolgung

Ereignistypen im Nachrichtenverfolgungsprotokoll

Quellwerte im Nachrichtenverfolgungsprotokoll

Beispieleinträge im Nachrichtenverfolgungsprotokoll

Sicherheitsüberlegungen zum Nachrichtenverfolgungsprotokoll

## Durchsuchen des Nachrichtenverfolgungsprotokolls

In Nachrichtenverfolgungsprotokollen fallen große Datenmengen an, während sich Nachrichten durch einen Exchange 2013-Postfachserver bewegen. Zur Durchsuchung der Nachrichtenverfolgungsprotokolle haben Sie mehrere Möglichkeiten.

  - **Get-MessageTrackingLog**   Administratoren nutzen dieses Cmdlet zum Durchsuchen des Nachrichtenverfolgungsprotokolls nach Informationen zu Nachrichten mithilfe einer breiten Palette von Filterkriterien. Weitere Informationen finden Sie unter [Durchsuchen von Nachrichtenverfolgungsprotokollen](search-message-tracking-logs-exchange-2013-help.md).

  - **Zustellungsberichte für Administratoren**   Administratoren können über die Registerkarte **Zustellungsberichte** in der Exchange-Verwaltungskonsole oder die zugrunde liegenden Cmdlets **Search-MessageTrackingReport** und **Get-MesageTrackingReport** die Nachrichtenverfolgungsprotokolle nach Informationen zu Nachrichten durchsuchen, die von einem bestimmten Postfach in der Organisation gesendet oder empfangen wurden. Weitere Informationen finden Sie unter [Übermittlungsberichte für Administratoren](delivery-reports-for-administrators-exchange-2013-help.md).

  - **Zustellungsberichte für Benutzer**   Benutzer können über die Registerkarte **Zustellungsberichte** in Outlook Web App die Nachrichtenverfolgungsprotokolle nach Informationen zu Nachrichten durchsuchen, die von ihrem eigenen Postfach gesendet und empfangen wurden. Weitere Informationen finden Sie unter [Zustellungsberichte für Benutzer](https://go.microsoft.com/fwlink/?linkid=279920).

Zurück zum Seitenanfang

## Struktur der Protokolldateien der Nachrichtenverfolgung

Standardmäßig befinden Sich die Protokolldateien der Nachrichtenverfolgung in "% ExchangeInstallPath%TransportRoles\\Logs\\MessageTracking".

Die Benennungskonvention für Protokolldateien im Verzeichnis für die Nachrichtenverfolgungsprotokolle ist `MSGTRK`*yyyymmdd-nnnn*`.log`, `MSGTRKMA`*yyyymmdd-nnnn*`.log`, `MSGTRKMD`*yyyymmdd-nnnn*`.log` und `MSGTRKMS`*yyyymmdd-nnnn*`.log`. Die verschiedenen Protokolle werden von den folgenden Diensten verwendet:

  - **MSGTRK**   Diese Protokolle sind dem Transportdienst zugeordnet.

  - **MSGTRKMA**   Diese Protokolle sind den vom moderierten Transport zugeordneten Genehmigungen und Zurückweisungen zugeordnet. Weitere Informationen finden Sie unter [Verwalten der Nachrichtengenehmigung](https://technet.microsoft.com/de-de/library/Dd297936(v=EXCHG.150)).

  - **MSGTRKMD**   Diese Protokolle sind Nachrichten zugeordnet, die Postfächern vom Postfachtransport-Zustellungsdienst zugestellt werden.

  - **MSGTRKMS**   Diese Protokolle sind Nachrichten zugeordnet, die Postfächern vom Postfachtransport-Übermittlungsdienst gesendet werden.

Die Platzhalter in den Protokolldateinamen stehen für folgende Informationen:

  - Bei dem Platzhalter *yyyymmdd* handelt es sich um das UTC-Datum (Coordinated Universal Time), an dem die Protokolldatei erstellt wurde. *yyyy* = Jahr, *mm* = Monat und *dd* = Tag.

  - Der Platzhalter *nnnn* ist eine Instanznummer, die täglich mit dem Wert 1 für jedes Namenspräfix der Nachrichtenverfolgungsprotokoll-Datei beginnt.

In jede Protokolldatei werden Informationen geschrieben, bis die Dateigröße den für jede Protokolldatei angegebenen Maximalwert erreicht. Dann wird eine neue Protokolldatei mit der nächsthöheren Instanznummer geöffnet. Dieser Vorgang wird während des ganzen Tags wiederholt. Bei der Protokolldateirotation werden die ältesten Protokolldateien gelöscht, wenn eine der folgenden Bedingungen zutrifft:

  - Eine Protokolldatei erreicht ihr angegebenes Höchstalter.

  - Das Verzeichnis für Nachrichtenverfolgungsprotokolle erreicht seine festgelegte maximal zulässige Größe.
    

    > [!IMPORTANT]
    > Die Maximalgröße des Nachrichtenverfolgungsprotokoll-Verzeichnisses wird aus der Gesamtgröße aller Protokolldateien berechnet, die dasselbe Namenspräfix haben. Alle weiteren Dateien, die die Namenspräfixkonvention nicht einhalten, werden bei der Berechnung der Gesamtgröße des Verzeichnisses nicht berücksichtigt. Das Umbenennen alter Protokolldateien oder das Kopieren anderer Dateien in das Nachrichtenverfolgungsprotokoll-Verzeichnis kann dazu führen, dass das Verzeichnis seine angegebene Maximalgröße überschreitet.<BR>Bei Exchange 2013-Postfachservern entspricht die maximale Größe des Protokollverzeichnisses für die Nachrichtenverfolgung dem Zweifachen des angegebenen Werts. Wenngleich die Dateien für die Nachrichtenverfolgungsprotokolle von vier verschiedenen Diensten generiert werden und vier unterschiedliche Namenspräfixe haben, sind Umfang und Häufigkeit, wie der Daten in die <STRONG>MSGTRKMA</STRONG>-Protokolldateien geschrieben werden, im Vergleich zu den anderen drei Protokolldateipräfixen zu vernachlässigen.



Bei den Protokolldateien der Nachrichtenverfolgung handelt es sich um Textdateien, die Daten im CSV-Format (Comma Separated Value, durch Komma getrennte Werte) enthalten. Jede Datei enthält eine Kopfzeile mit den folgenden Informationen:

  - **\#Software:**    Name der Software, mit der die Nachrichtenverfolgungs-Protokolldatei erstellt wurde. In der Regel lautet der Wert "Microsoft Exchange Server".

  - **\#Version:**    Versionsnummer der Software, mit der die Nachrichtenverfolgungs-Protokolldatei erstellt wurde. Der aktuelle Wert lautet 15.0.0.0.

  - **\#Log-Type**   Wert des Protokolltyps, in diesem Fall Message Tracking Log.

  - **\#Date:**    Datum und Uhrzeit (UTC) der Erstellung der Protokolldatei. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: *yyyy-mm-dd*T*hh:mm:ss.fff*Z, wobei *yyyy* = Jahr, *mm* = Monat, *dd* = Tag. T gibt an, dass eine Zeitangabe folgt. *hh* = Stunde,*mm* = Minute, *ss* = Sekunde, *fff* = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.

  - **\#Fields:**    Durch Trennzeichen getrennte Feldnamen, die in den Protokolldateien für die Nachrichtenverfolgung verwendet werden.

Zurück zum Seitenanfang

## Felder in den Protokolldateien für die Nachrichtenverfolgung

Im Nachrichtenverfolgungsprotokoll werden die einzelnen Nachrichtenereignisse jeweils in einer einzelnen Zeile gespeichert. Die Nachrichtenereignisinformationen sind in Feldern organisiert, die durch Kommas voneinander getrennt sind. Anhand des Feldnamens kann im Allgemeinen festgestellt werden, welchen Informationstyp das jeweilige Feld enthält. Einige Felder sind möglicherweise jedoch leer, oder der im Feld gespeicherte Informationstyp kann sich auf Grundlage des Nachrichtenereignistyps und des Typs der Nachrichtenverfolgungs-Protokolldatei ändern, in der das Ereignis aufgezeichnet wurde. Allgemeine Beschreibungen der Felder, die zum Klassifizieren der einzelnen Protokollereignisse verwendet werden, werden in folgenden Tabelle erläutert.


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
<td><p>Datum und Uhrzeit des Nachrichtenverfolgungsereignisses im UTC-Datums-/Uhrzeitformat. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, wobei <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag. T gibt an, dass eine Zeitangabe folgt. <em>hh</em> = Stunde,<em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.</p></td>
</tr>
<tr class="even">
<td><p><strong>client-ip</strong></p></td>
<td><p>Die IPv4- oder IPv6-Adresse des Messagingservers oder -clients, der die Nachricht übermittelt hat.</p></td>
</tr>
<tr class="odd">
<td><p><strong>client-hostname</strong></p></td>
<td><p>Der Hostname oder FQDN des Messagingservers oder -clients, der die Nachricht übermittelt hat.</p></td>
</tr>
<tr class="even">
<td><p><strong>server-ip</strong></p></td>
<td><p>Die IPv4- oder IPv6-Adresse des Exchange-Quell- oder Zielservers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>server-hostname</strong></p></td>
<td><p>Der Hostname oder FQDN des Zielservers.</p></td>
</tr>
<tr class="even">
<td><p><strong>source-context</strong></p></td>
<td><p>Zusätzliche Informationen, die zum Feld <strong>source</strong> gehören. Beispiel: Transport-Agent-Informationen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>connector-id</strong></p></td>
<td><p>Der Name des Sendeconnectors oder Empfangsconnectors am Quell- oder Zielstandort. Beispiel: <em>Servername</em>\<em>Connectorname</em> oder <em>Connectorname</em>.</p></td>
</tr>
<tr class="even">
<td><p><strong>source</strong></p></td>
<td><p>Die für das Nachrichtenverfolgungsereignis zuständige Exchange-Transportkomponente. Die Werte in diesem Feld werden im Abschnitt Quellwerte im Nachrichtenverfolgungsprotokoll weiter unten in diesem Thema beschrieben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>event-id</strong></p></td>
<td><p>Der Nachrichtenereignistyp. Die Ereignistypen werden im Abschnitt Ereignistypen im Nachrichtenverfolgungsprotokoll weiter unten in diesem Thema beschrieben.</p></td>
</tr>
<tr class="even">
<td><p><strong>internal-message-id</strong></p></td>
<td><p>Eine Nachrichten-ID, die vom Exchange-Server zugewiesen wurde, der die Nachricht derzeit verarbeitet.</p>
<p>Der Wert <strong>internal-message-id</strong> einer bestimmten Nachricht ist im Nachrichtenverfolgungsprotokoll jedes Exchange-Servers unterschiedlich, der an der Zustellung der Nachricht beteiligt ist. Ein Beispielwert ist <code>73014444033</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>message-id</strong></p></td>
<td><p>Der Wert des Kopfzeilenfelds <strong>Nachrichten-ID:</strong> im Nachrichtenkopf. Wenn das Kopfzeilenfeld <strong>Nachrichten-ID:</strong> nicht vorhanden oder leer ist, wird ein beliebiger Wert zugewiesen. Dieser Wert ist für die Lebensdauer der Nachricht konstant. Für in Exchange erstellte Nachrichten hat der Wert das Format <code>&lt;GUID@ServerFQDN&gt;</code> einschließlich der eckigen Klammern (<code>&lt; &gt;</code>). Beispiel: <code>&lt;4867a3d78a50438bad95c0f6d072fca5@mailbox01.contoso.com&gt;</code>. Andere Messagingsysteme können eine andere Syntax oder andere Werte verwenden.</p></td>
</tr>
<tr class="even">
<td><p><strong>network-message-id</strong></p></td>
<td><p>Ein eindeutiger Nachrichten-ID-Wert, der bei Kopien der Nachricht erhalten bleibt, die ggf. durch eine Verzweigung oder Aufgliederung der Verteilergruppe erstellt wurden. Ein Beispielwert ist <code>1341ac7b13fb42ab4d4408cf7f55890f</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>recipient-address</strong></p></td>
<td><p>Die E-Mail-Adresse des Empfängers der Nachricht. Mehrere E-Mail-Adressen sind durch ein Semikolon (;) getrennt.</p></td>
</tr>
<tr class="even">
<td><p><strong>recipient-status</strong></p></td>
<td><p>Dieses Feld enthält den Empfängerstatus jedes Empfänger getrennt durch ein Semikolon (;). Die Statuswerte werden für die Empfänger in derselben Reihenfolge wie die Werte im Feld <strong>recipient-address</strong> dargestellt. Beispielstatuswerte sind <code>250 2.1.5 Recipient OK</code> und <code>550 4.4.7 QUEUE.Expired;&lt;ErrorText&gt;</code>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>total-bytes</strong></p></td>
<td><p>Die Größe der Nachricht, die Anlagen enthält, in Bytes.</p></td>
</tr>
<tr class="even">
<td><p><strong>recipient-count</strong></p></td>
<td><p>Die Gesamtzahl der Empfänger in der Nachricht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>related-recipient-address</strong></p></td>
<td><p>Dieses Feld wird mit Ereignissen vom Typ <strong>EXPAND</strong>, <strong>REDIRECT</strong> und <strong>RESOLVE</strong> verwendet, um die E-Mail-Adressen weiterer Empfänger anzuzeigen, die dieser Nachricht zugeordnet sind.</p></td>
</tr>
<tr class="even">
<td><p><strong>reference</strong></p></td>
<td><p>Das Feld enthält zusätzliche Informationen für bestimmte Ereignistypen. Beispiel:</p>
<p><strong>DSN</strong>   Enthält den Berichtslink, bei dem es sich um den<strong>Message-Id</strong>-Wert der dazugehörigen Benachrichtigung über den Zustellungsstatus handelt, falls eine solche im Anschluss an dieses Ereignis generiert wird. Wenn es sich um eine Benachrichtigung über den Zustellungsstatus handelt, enthält das Feld <strong>Reference</strong> den <strong>Message-Id</strong>-Wert der ursprünglichen Nachricht, für die diese Benachrichtigung über den Zustellungsstatus generiert wurde.</p>
<p><strong>EXPAND</strong>   Das Feld &quot;Reference&quot; enthält den<strong>related-recipient-address</strong>-Wert der dazugehörigen Nachrichten.</p>
<p><strong>RECEIVE</strong>   Das Feld &quot;Reference&quot; kann den <strong>Message-Id</strong>-Wert der dazugehörigen Nachricht enthalten, wenn die Nachricht durch andere Prozesse generiert wird, z. B. Journal- oder Posteingangsregeln.</p>
<p><strong>SEND</strong>   Das Feld &quot;Reference&quot; enthält den <strong>Internal-Message-Id</strong>-Wert beliebiger Benachrichtigungen über den Zustellungsstatus.</p>
<p><strong>THROTTLE</strong>   Das Feld &quot;Reference&quot; enthält den Grund, warum die Nachricht eingeschränkt wurde.</p>
<p><strong>TRANSFER</strong>   Das Feld Reference enthält den Wert Internet-Message-Id der Nachricht, die verzweigt wird.</p>
<p>Für von Poseingangsregeln generierte Nachrichten enthält das Feld <strong>Reference</strong> den <strong>Internal-Message-Id</strong>-Wert der eingehenden Nachricht, die bewirkt hat, dass die Posteingangsregel die ausgehende Nachricht generiert hat.</p>
<p>Bei anderen Ereignistypen kann das Feld <strong>Reference</strong> den Wert <strong>Internal-Message-Id</strong> für verzweigte Nachrichten enthalten.</p>
<p>Für anderen Ereignistypen ist das Feld <strong>Reference</strong> zumeist leer.</p></td>
</tr>
<tr class="odd">
<td><p><strong>message-subject</strong></p></td>
<td><p>Der Nachrichtenbetreff aus dem Kopfzeilenfeld <code>Subject:</code>. Die Nachverfolgen von Nachrichtenbetreffs wird über den Parameter <em>MessageTrackingLogSubjectLoggingEnabled</em> im Cmdlet <strong>Set-TransportService</strong> oder <strong>Set-MailboxServer</strong> gesteuert. Die Nachrichtenbetreffverfolgung ist in der Standardeinstellung aktiviert.</p></td>
</tr>
<tr class="even">
<td><p><strong>sender-address</strong></p></td>
<td><p>Die E-Mail-Adresse, die im Kopfzeilenfeld <code>Sender:</code> oder <code>From:</code> angegeben ist (falls <code>Sender:</code> nicht vorhanden ist).</p></td>
</tr>
<tr class="odd">
<td><p><strong>return-path</strong></p></td>
<td><p>Die E-Mail-Adresse des Absenders, die unter <code>MAIL FROM:</code> im Nachrichtenumschlag angegeben ist. Zwar ist dieses Feld niemals leer, es kann jedoch den Absenderadresswert Null enthalten, der durch <code>&lt;&gt;</code> dargestellt wird.</p></td>
</tr>
<tr class="even">
<td><p><strong>message-info</strong></p></td>
<td><p>Weitere Informationen zur Nachricht. Beispiel:</p>
<ul>
<li><p>UTC-Datum/Uhrzeit des Nachrichtenursprungs für die Ereignisse <strong>DELIVER</strong> und <strong>SEND</strong>. Hierbei handelt es sich um den Zeitpunkt, zu dem die Nachricht erstmals in die Exchange-Organisation eingetreten ist. Datum und Uhrzeit (UTC) werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, wobei <em>yyyy</em> = Jahr, <em>mm</em> = Monat, <em>dd</em> = Tag. T gibt an, dass eine Zeitangabe folgt. <em>hh</em> = Stunde,<em>mm</em> = Minute, <em>ss</em> = Sekunde, <em>fff</em> = Bruchteile einer Sekunde. Und Z steht für Zulu, eine weitere Möglichkeit zur Angabe von UTC.</p></li>
<li><p>Authentifizierungsfehler. Bei Auftreten von Authentifizierungsfehlern werden ggf. der Wert <code>11a</code> und der Typ der verwendeten Authentifizierung angezeigt.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>directionality</strong></p></td>
<td><p>Die Richtung der Nachricht. Beispielwerte sind <code>Incoming</code>, <code>Undefined</code> und <code>Originating</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>tenant-id</strong></p></td>
<td><p>Dieses Feld wird in lokalen Exchange 2013-Organisationen nicht verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>original-client-ip</strong></p></td>
<td><p>Die IPv4- oder IPv6-Adresse des ursprünglichen Clients.</p></td>
</tr>
<tr class="even">
<td><p><strong>original-server-ip</strong></p></td>
<td><p>Die IPv4- oder IPv6-Adresse des ursprünglichen Servers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>custom-data</strong></p></td>
<td><p>Dieses Feld enthält Daten in Bezug auf einen bestimmten Ereignistyp. Beispielsweise nutzt der Transportregel-Agent dieses Feld zum Aufzeichnen der GUID der Transportregel oder DLP-Richtlinie, die auf die Nachricht angewendet wurde. Weitere Informationen zu diesen Transportregel-Agent-Werten finden Sie im Abschnitt &quot;Datenprotokollierung&quot; im Thema <a href="view-dlp-policy-detection-reports-exchange-2013-help.md">Anzeigen von DLP-Richtlinienerkennungsberichten</a>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Ereignistypen im Nachrichtenverfolgungsprotokoll

Verschiedene Ereignistypen im Feld **event-id** dienen zum Klassifizieren der Nachrichtenereignisse im Nachrichtenverfolgungsprotokoll. Einige Nachrichtenereignisse werden nur in einem Typ von Protokolldatei für die Nachrichtenverfolgung angezeigt, andere hingegen in allen. Die Ereignistypen, die zum Klassifizieren der einzelnen Nachrichtenereignisse verwendet werden, sind in Tabelle 1 beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignisname</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AGENTINFO</strong></p></td>
<td><p>Dieses Ereignis wird von Transport-Agents verwendet, um benutzerdefinierte Daten zu protokollieren.</p></td>
</tr>
<tr class="even">
<td><p><strong>BADMAIL</strong></p></td>
<td><p>Vom PICKUP-Verzeichnis oder Wiedergabeverzeichnis wurde eine Nachricht übermittelt, die nicht zugestellt oder zurückgegeben werden kann.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DEFER</strong></p></td>
<td><p>Die Nachrichtenzustellung wurde verzögert.</p></td>
</tr>
<tr class="even">
<td><p><strong>DELIVER</strong></p></td>
<td><p>Eine Nachricht wurde an ein lokales Postfach zugestellt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DROP</strong></p></td>
<td><p>Eine Nachricht ohne Benachrichtigung über den Zustellungsstatus (auch als DSN, Unzustellbarkeitsnachricht oder NDR bezeichnet) wurde gelöscht. Beispiel:</p>
<ul>
<li><p>Die Moderation von Genehmigungsanforderungsnachrichten wurde abgeschlossen.</p></li>
<li><p>Spamnachrichten, die ohne NDR im Hintergrund gelöscht wurden.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>DSN</strong></p></td>
<td><p>Eine Benachrichtigung über den Zustellungsstatus wurde generiert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DUPLICATEDELIVER</strong></p></td>
<td><p>Eine doppelte Nachricht wurde dem Empfänger zugestellt. Eine Duplizierung kann ggf. erfolgen, wenn ein Empfänger Mitglied mehrerer geschachtelter Verteilergruppen ist. Doppelte Nachrichten werden vom Informationsspeicher erkannt und entfernt.</p></td>
</tr>
<tr class="even">
<td><p><strong>DUPLICATEEXPAND</strong></p></td>
<td><p>Während der Aufgliederung der Verteilergruppe wurde ein doppelter Empfänger erkannt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DUPLICATEREDIRECT</strong></p></td>
<td><p>Ein alternativer Empfänger für die Nachricht war bereits ein Empfänger.</p></td>
</tr>
<tr class="even">
<td><p><strong>EXPAND</strong></p></td>
<td><p>Eine Verteilergruppe wurde erweitert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FAIL</strong></p></td>
<td><p>Bei der Nachrichtenzustellung ist ein Fehler aufgetreten. Quellen sind u. a. <strong>SMTP</strong>, <strong>DNS</strong>, <strong>QUEUE</strong> und <strong>ROUTING</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>HADISCARD</strong></p></td>
<td><p>Eine Shadow-Nachricht wurde verworfen, nachdem die primäre Kopie an den nächsten Hop übermittelt wurde. Weitere Informationen finden Sie unter <a href="shadow-redundancy-exchange-2013-help.md">Shadow-Redundanz</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HARECEIVE</strong></p></td>
<td><p>Eine Shadow-Nachricht wurde vom Server in der lokalen Database Availability Group (DAG) oder vom lokalen Active Directory-Standort empfangen.</p></td>
</tr>
<tr class="even">
<td><p><strong>HAREDIRECT</strong></p></td>
<td><p>Eine Shadow-Nachricht erstellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HAREDIRECTFAIL</strong></p></td>
<td><p>Eine Shadow-Nachricht konnte nicht erstellt werden. Die Details werden im Feld <strong>source-context</strong> gespeichert.</p></td>
</tr>
<tr class="even">
<td><p><strong>INITMESSAGECREATED</strong></p></td>
<td><p>Eine Nachricht wurde an einen moderierten Empfänger gesendet, weshalb die Nachricht zwecks Genehmigung an das Vermittlungspostfach gesendet wurde. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-message-approval">Verwalten der Nachrichtengenehmigung</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LOAD</strong></p></td>
<td><p>Eine Nachricht wurde erfolgreich beim Starten geladen.</p></td>
</tr>
<tr class="even">
<td><p><strong>MODERATIONEXPIRE</strong></p></td>
<td><p>Ei Moderator eines moderierten Empfängers hat die Nachricht weder genehmigt noch abgelehnt, weshalb sie abgelaufen ist. Weitere Informationen zu moderierten Empfängern finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-message-approval">Verwalten der Nachrichtengenehmigung</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MODERATORAPPROVE</strong></p></td>
<td><p>Ein Moderator eines moderierten Empfängers hat die Nachricht genehmigt, weshalb sie dem moderierten Empfänger zugestellt wurde.</p></td>
</tr>
<tr class="even">
<td><p><strong>MODERATORREJECT</strong></p></td>
<td><p>Ein Moderator eines moderierten Empfängers hat die Nachricht abgelehnt, weshalb sie dem moderierten Empfänger nicht zugestellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MODERATORSALLNDR</strong></p></td>
<td><p>Alle Genehmigungsanforderungen, die an alle Moderatoren eines moderierten Empfängers gesendet wurden, waren unzustellbar, was zu Unzustellbarkeitsberichten geführt hat.</p></td>
</tr>
<tr class="even">
<td><p><strong>NOTIFYMAPI</strong></p></td>
<td><p>Im Postausgang eines Postfachs auf dem lokalen Server wurde eine Nachricht entdeckt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NOTIFYSHADOW</strong></p></td>
<td><p>Im Postausgang eines Postfachs auf dem lokalen Server wurde eine Nachricht entdeckt. Eine Shadow-Kopie der Nachricht muss erstellt werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>POISONMESSAGE</strong></p></td>
<td><p>Eine Nachricht wurde in die Warteschlange für nicht verarbeitete Nachrichten aufgenommen oder aus ihr entfernt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PROCESS</strong></p></td>
<td><p>Die Nachricht wurde erfolgreich verarbeitet.</p></td>
</tr>
<tr class="even">
<td><p><strong>PROCESSMEETINGMESSAGE</strong></p></td>
<td><p>Eine Besprechungsnachricht wurde vom Postfachtransport-Zustellungsdienst verarbeitet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RECEIVE</strong></p></td>
<td><p>Eine Nachricht wurde von der SMTP-Empfangskomponente des Transportdiensts oder dem PICKUP- oder Wiedergabeverzeichnis empfangen (Quelle: <code>SMTP</code>), oder eine Nachricht wurde aus einem Postfach an den Postfachtransport-Übermittlungsdienst gesendet (Quelle: <code>STOREDRIVER</code>).</p></td>
</tr>
<tr class="even">
<td><p><strong>REDIRECT</strong></p></td>
<td><p>Eine Nachricht wurde nach einer Active Directory-Suche an einen alternativen Empfänger umgeleitet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RESOLVE</strong></p></td>
<td><p>Die Empfänger einer Nachricht wurden nach einer Active Directory-Suche in verschiedene E-Mail-Adressen aufgelöst.</p></td>
</tr>
<tr class="even">
<td><p><strong>RESUBMIT</strong></p></td>
<td><p>Eine Nachricht wurde automatisch vom Sicherheitsnetz erneut übermittelt. Weitere Informationen finden Sie unter <a href="safety-net-exchange-2013-help.md">Sicherheitsnetz</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RESUBMITDEFER</strong></p></td>
<td><p>Eine vom Sicherheitsnetz erneut übermittelte Nachricht wurde zurückgestellt.</p></td>
</tr>
<tr class="even">
<td><p><strong>RESUBMITFAIL</strong></p></td>
<td><p>Fehler bei einer vom Sicherheitsnetz erneut übermittelten Nachricht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SEND</strong></p></td>
<td><p>Eine Nachricht wurde von SMTP zwischen Transportdiensten gesendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>SUBMIT</strong></p></td>
<td><p>Der Postfachtransport-Übermittlungsdienst hat die Nachricht erfolgreich an den Transportdienst übertragen. Für Ereignisse vom Typ <strong>SUBMIT</strong> enthält die Eigenschaft <strong>source-context</strong> die folgenden Details:</p>
<ul>
<li><p><strong>MDB</strong>   Die Postfachdatenbank-GUID.</p></li>
<li><p><strong>Mailbox</strong>   Die Postfach-GUID.</p></li>
<li><p><strong>Event</strong>   Die Ereignissequenznummer.</p></li>
<li><p><strong>MessageClass</strong>   Der Typ der Nachricht. Beispiel: <code>IPM.Note</code>.</p></li>
<li><p><strong>CreationTime</strong>   Datum / Uhrzeit des der Nachrichtenübermittlung.</p></li>
<li><p><strong>ClientType</strong>   Beispiel: <code>User</code>, <code>OWA</code> oder <code>ActiveSync</code>.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>SUBMITDEFER</strong></p></td>
<td><p>Die Nachrichtenübermittlung vom Postfachtransport-Übermittlungsdienst zum Transportdienst wurde zurückgestellt.</p></td>
</tr>
<tr class="even">
<td><p><strong>SUBMITFAIL</strong></p></td>
<td><p>Fehler bei der Nachrichtenübermittlung vom Postfachtransport-Übermittlungsdienst zum Transportdienst.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SUPPRESSED</strong></p></td>
<td><p>Die Nachrichtenübertragung wurde unterdrückt.</p></td>
</tr>
<tr class="even">
<td><p><strong>THROTTLE</strong></p></td>
<td><p>Die Nachricht wurde eingeschränkt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TRANSFER</strong></p></td>
<td><p>Empfänger wurden aufgrund von Inhaltskonvertierung und Nachrichtenempfängerbeschränkungen oder von Agents in eine verzweigte Nachricht verschoben. Quellen sind u. a. <strong>ROUTING</strong> oder <strong>QUEUE</strong>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Quellwerte im Nachrichtenverfolgungsprotokoll

Die Werte im Feld **source** im Nachrichtenverfolgungsprotokoll geben die Transportkomponente an, die für das Nachrichtenverfolgungsereignis zuständig ist. In der folgenden Tabelle werden die Werte des Felds **source** beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert von &quot;source&quot;</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ADMIN</strong></p></td>
<td><p>Die Ereignisquelle war menschliches Eingreifen. Beispiel: Ein Administrator hat in der Warteschlangenanzeige eine Nachricht gelöscht oder Nachrichtendateien mithilfe des Wiedergabeverzeichnisses übermittelt.</p></td>
</tr>
<tr class="even">
<td><p><strong>AGENT</strong></p></td>
<td><p>Die Ereignisquelle war ein Transport-Agent.</p></td>
</tr>
<tr class="odd">
<td><p><strong>APPROVAL</strong></p></td>
<td><p>Die Ereignisquelle war das Genehmigungssystem, das mit moderierten Empfänger verwendet wird. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-message-approval">Verwalten der Nachrichtengenehmigung</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>BOOTLOADER</strong></p></td>
<td><p>Die Ereignisquelle waren nicht verarbeitete Nachrichten, die auf dem Server beim Start vorhanden sind. Dies bezieht sich auf den Ereignistyp <strong>LOAD</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DNS</strong></p></td>
<td><p>Die Ereignisquelle war DNS.</p></td>
</tr>
<tr class="even">
<td><p><strong>DSN</strong></p></td>
<td><p>Die Ereignisquelle war eine Benachrichtigung über die Zustellungsstatus. Beispiel: ein Unzustellbarkeitsbericht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GATEWAY</strong></p></td>
<td><p>Die Ereignisquelle war ein fremder Connector. Weitere Informationen finden Sie unter <a href="foreign-connectors-exchange-2013-help.md">Fremde Connectors</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>MAILBOXRULE</strong></p></td>
<td><p>Die Ereignisquelle war eine Posteingangsregel. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/?linkid=285479">Posteingangsregeln</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MEETINGMESSAGEPROCESSOR</strong></p></td>
<td><p>Die Ereignisquelle war die Verarbeitung der Besprechungsnachrichten, die Kalender basierend auf Besprechungsaktualisierungen aktualisiert.</p></td>
</tr>
<tr class="even">
<td><p><strong>ORAR</strong></p></td>
<td><p>Die Quelle war ein Originator Requested Alternate Recipient (ORAR, vom Absender angeforderter Alternativempfänger). Über den Parameter <em>OrarEnabled</em> für die Cmdlets <strong>New-ReceiveConnector</strong> und <strong>Set-ReceiveConnector</strong> können Sie Unterstützung für ORAR oder Empfangsconnectors aktivieren oder deaktivieren.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PICKUP</strong></p></td>
<td><p>Die Ereignisquelle war das PICKUP-Verzeichnis. Weitere Informationen finden Sie unter <a href="pickup-directory-and-replay-directory-exchange-2013-help.md">PICKUP-Verzeichnis und Wiedergabeverzeichnis</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>POISONMESSAGE</strong></p></td>
<td><p>Die Ereignisquelle war die ID einer nicht verarbeitbaren Nachricht. Weitere Informationen zu nicht verarbeitbaren Nachrichten und zur Warteschlange für nicht verarbeitbare Nachrichten finden Sie unter <a href="queues-exchange-2013-help.md">Warteschlangen</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>PUBLICFOLDER</strong></p></td>
<td><p>Die Ereignisquelle war ein E-Mail-aktivierter öffentliche Ordner.</p></td>
</tr>
<tr class="even">
<td><p><strong>QUEUE</strong></p></td>
<td><p>Die Ereignisquelle war eine Warteschlange.</p></td>
</tr>
<tr class="odd">
<td><p><strong>REDUNDANCY</strong></p></td>
<td><p>Die Ereignisquelle war Shadow-Redundanz. Weitere Informationen finden Sie unter <a href="shadow-redundancy-exchange-2013-help.md">Shadow-Redundanz</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ROUTING</strong></p></td>
<td><p>Die Ereignisquelle war die Routingauflösungskomponente des Kategorisierungsmoduls im Transportdienst.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SAFETYNET</strong></p></td>
<td><p>Die Ereignisquelle war das Sicherheitsnetz. Weitere Informationen finden Sie unter <a href="safety-net-exchange-2013-help.md">Sicherheitsnetz</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SMTP</strong></p></td>
<td><p>Die Nachricht wurde von der SMTP-Sende- oder SMTP-Empfangskomponente des Transportdiensts übermittelt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>STOREDRIVER</strong></p></td>
<td><p>Die Ereignisquelle war eine MAPI-Übermittlung aus einem Postfach auf dem lokalen Server.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Beispieleinträge im Nachrichtenverfolgungsprotokoll

Eine ereignislose Nachricht, die zwischen zwei Benutzern gesendet wurde, generiert mehrere Einträge im Nachrichtenverfolgungsprotokoll. Sie können die Ergebnisse mit dem Cmdlet **Get-MessageTrackingLog** überprüfen. Weitere Informationen finden Sie unter [Durchsuchen von Nachrichtenverfolgungsprotokollen](search-message-tracking-logs-exchange-2013-help.md).

Dies ist ein verkürztes Beispiel für Einträge im Nachrichtenverfolgungsprotokoll, die erstellt wurden, als der Benutzer "chris@contoso.com" erfolgreich eine Testnachricht an die Benutzerin "michelle@contoso.com" gesendet hat. Beide Benutzer haben Postfächer auf demselben Server.

    EventId    Source      Sender            Recipients             MessageSubject
    -------    ------      ------            ----------             --------------
    NOTIFYMAPI STOREDRIVER                   {}
    RECEIVE    STOREDRIVER chris@contoso.com {michelle@contoso.com} test
    SUBMIT     STOREDRIVER chris@contoso.com {michelle@contoso.com} test
    HAREDIRECT SMTP        chris@contoso.com {michelle@contoso.com} test
    RECEIVE    SMTP        chris@contoso.com {michelle@contoso.com} test
    AGENTINFO  AGENT       chris@contoso.com {michelle@contoso.com} test
    SEND       SMTP        chris@contoso.com {michelle@contoso.com} test
    DELIVER    STOREDRIVER chris@contoso.com {michelle@contoso.com} test

Zurück zum Seitenanfang

## Sicherheitsüberlegungen zum Nachrichtenverfolgungsprotokoll

Im Nachrichtenverfolgungsprotokoll wird kein Nachrichteninhalt gespeichert. Standardmäßig wird die Betreffzeile einer E-Mail-Nachricht im Nachrichtenverfolgungsprotokoll gespeichert. Möglicherweise möchten Sie die Nachrichtenbetreffprotokollierung jedoch aufgrund von erhöhten Sicherheits- und Datenschutzanforderungen deaktivieren. Überprüfen Sie vor der Aktivierung oder Deaktivierung der Nachrichtenbetreffprotokollierung die Richtlinie Ihrer Organisation zum Anzeigen von Betreffzeileninformationen. Weitere Informationen finden Sie unter [Konfigurieren der Nachrichtenverfolgung](configure-message-tracking-exchange-2013-help.md).

Zurück zum Seitenanfang

