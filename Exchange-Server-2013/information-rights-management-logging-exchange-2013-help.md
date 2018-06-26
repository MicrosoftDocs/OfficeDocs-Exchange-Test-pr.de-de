---
title: 'Information Rights Management-Protokollierung: Exchange 2013 Help'
TOCTitle: Information Rights Management-Protokollierung
ms:assetid: e06f57f9-a9e2-43a2-b88c-288b324d71f0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff461940(v=EXCHG.150)
ms:contentKeyID: 50476922
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Information Rights Management-Protokollierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

In Microsoft Exchange Server 2013 werden IRM-Vorgänge (Verwaltung von Informationsrechten) in IRM-Protokollen erfasst. IRM-Protokolle ermöglichen Ihnen die Überwachung und Problembehandlung von Interaktionen zwischen dem RMS-Client (Rights Management Services, Rechteverwaltungsdienste) auf einem Exchange 2013-Server und dem Active Directory-Rechteverwaltungsdienste-Cluster (AD RMS) in Ihrer Organisation.

Weitere Informationen zu IRM finden Sie unter [Verwaltung von Informationsrechten](information-rights-management-exchange-2013-help.md).

**Inhalt**

Structure of IRM logs

Logging process

Information written to IRM logs

Managing IRM logs

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit IRM gibt? Informationen hierzu finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Struktur von IRM-Protokollen

Standardmäßig befinden sich IRM-Protokolle im Verzeichnis "C:\\Programme\\Microsoft\\Exchange Server\\V14\\Logging\\IRMLogs".

Die Benennung einer IRM-Protokolldatei erfolgt gemäß der Konvention "\<*Prozess*\>\_\<*Prozess-ID* oder *IIS-AppPool-ID*\>\_IRMLOG*jjjjmmtt*-*nnnn*.log" mit:

  - \<*Prozess*\>= Prozess, der die Protokolldatei erstellt. Für den Transportdienst ist dies beispielsweise "EdgeTransport".

  - \<*Prozess-ID* oder *IIS-AppPool-ID\>* =numerische ID des Prozesses.

  - *jjjjmmtt* = UTC-Datum (Coordinated Universal Time, koordinierte Weltzeit), an dem die Protokolldatei erstellt wurde.

  - *nnnn* = Instanznummer, die für jeden Tag mit 1 beginnt.

"EdgeTransport\_1056\_IRMLOG20101201-1.log" ist ein Beispiel für den Namen einer IRM-Protokolldatei.

In der folgenden Tabelle sind die Protokolle aufgeführt, die für verschiedene Serverrollen erstellt werden.

### Protokolle für Serverrollen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Serverrolle</th>
<th>Name einer IRM-Protokolldatei</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transportdienst</p></td>
<td><p>EdgeTransport_&lt;<em>Prozess-ID</em>&gt;_IRMLOG<em>jjjjmmtt</em>-<em>nnnn</em>.log</p></td>
<td><p>In diesem Protokoll werden alle RMS-Transaktionen protokolliert, die von der Transportpipeline im Transportdienst ausgeführt werden (z. B. Transportschutzregeln und Journalberichtentschlüsselung). Für die Erstellung des Protokolldateinamens wird die Prozess-ID (PID) des Prozesses &quot;edgetransport.exe&quot; verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Postfach</p></td>
<td><p>-msftefd_&lt;<em>Prozess-ID</em>&gt;_IRMLOG<em>jjjjmmtt</em>-<em>nnnn</em>.log</p></td>
<td><p>In diesem Protokoll werden alle RMS-Transaktionen protokolliert, die im Verlauf von Such- oder Indexanforderungen ausgeführt werden. Auf Exchange 2013-Postfachservern wird der Prozess &quot;msftefd.exe&quot; dazu verwendet, Inhalte zu indizieren. Für die Erstellung des Protokolldateinamens wird die PID des Prozesses &quot;msftefd.exe&quot; verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>Clientzugriff</p></td>
<td><p>w3wp_MSExchangeOWAAppOol_IRMLOG<em>jjjjmmtt</em>-<em>nnnn</em>.log</p></td>
<td><p>In diesem Protokoll werden alle Transaktionen protokolliert, die in Microsoft OfficeOutlook Web App für IRM ausgeführt werden.</p></td>
</tr>
<tr class="even">
<td><p>Alle Exchange 2013-Serverrollen</p></td>
<td><p>w3wp_MSExchangePowerShellAppPool_IRMLOG<em>jjjjmmtt</em>-<em>nnnn</em>.log</p></td>
<td><p>In diesem Protokoll werden alle IRM-RMS-Transaktionen protokolliert, die von Windows PowerShell ausgelöst werden (beispielsweise wenn das Cmdlet <strong>Test-IRMConfiguration</strong> ausgeführt wird).</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Protokollierungsprozess

In die jeweilige Protokolldatei werden solange Informationen geschrieben, bis die für die Datei angegebene maximale Größe erreicht ist. Sobald die maximale Größe erreicht ist, wird eine Protokolldatei erstellt, die eine inkrementierte Instanznummer hat. Dieser Vorgang wird während des ganzen Tags wiederholt. Bei der Umlaufprotokollierung werden die ältesten Protokolldateien gelöscht, wenn das IRM-Protokollverzeichnis seine festgelegte Maximalgröße oder eine Protokolldatei das Höchstalter erreicht hat, das auf jedem Server in der IRM-Protokollierungskonfiguration angegeben ist.

Zurück zum Seitenanfang

## Informationen, die in IRM-Protokolle geschrieben werden

IRM-Protokolldateien sind Textdateien, die Daten im CSV-Format (Comma Separated Value) enthalten. Jede IRM-Protokolldatei enthält eine Kopfzeile mit den folgenden Informationen:

  - **\#Software:**   Der Name der Software, von der die IRM-Protokolldatei erstellt wurde. Üblicherweise ist dies der Wert `Microsoft Exchange Server`.

  - **\#Version**   Die Versionsnummer der Software, von der die IRM-Protokolldatei erstellt wurde.

  - **\#Log-type**   Der Protokolltyp, der `Rms Client Manager Log` lautet.

  - **\#Date**   UTC-Datum und -Uhrzeit der Erstellung der Protokolldatei. UTC-Datum und -Uhrzeit werden im ISO-8601-Datums-/Uhrzeitformat dargestellt: *jjjj*-*mm*-*tt*T*hh*:*mm*:*ss.fff*Z, wobei:
    
      - jjjj = Jahr
    
      - *mm* = Monat
    
      - *tt* = Tag
    
      - T = Zeitkennzeichen, das den Anfang der Zeitkomponente kennzeichnet
    
      - *hh* = Stunde
    
      - *mm* = Minute
    
      - *ss* = Sekunde
    
      - *fff* = Bruchteile einer Sekunde
    
      - Z = Zulu, das eine andere Bezeichnung für UTC ist

  - **\#Fields**   Durch Kommas getrennte Feldnamen, die in IRM-Protokolldateien verwendet werden.
    
    In einem IRM-Protokoll wird jede RMS-Transaktion in einer einzelnen Zeile gespeichert, gegliedert in Feldern, die durch Kommas getrennt sind. In der folgenden Tabelle sind die Felder aufgelistet, die es in IRM-Protokollen für alle Serverrollen gibt, für die IRM-Funktionen aktiviert sind.
    
    ### Felder, die in IRM-Protokollen verwendet werden
    
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
    <td><p><strong>Date-time</strong></p></td>
    <td><p>Enthält den UTC-Zeitstempel.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Feature</strong></p></td>
    <td><p>Enthält den Namen der verwendeten RMS-Clientfunktion. Gültige Werte sind:</p>
    <ul>
    <li><p><code>RacClc</code></p></li>
    <li><p><code>Template</code></p></li>
    <li><p><code>Prelicense</code></p></li>
    <li><p><code>UseLicense</code></p></li>
    <li><p>Signaturüberprüfung</p></li>
    <li><p><code>ServerInfo</code></p></li>
    </ul></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Event-Type</strong></p></td>
    <td><p>Enthält den Ereignistyp. Gültige Werte sind:</p>
    <ul>
    <li><p><code>Acquire</code>   Es wird eine RMS-Lizenz oder -Vorlage angefordert.</p></li>
    <li><p><code>Success</code>   Eine RMS-Lizenz oder -Vorlage wurde erfolgreich angefordert.</p></li>
    <li><p><code>Exception</code>   Es ist ein Fehler aufgetreten.</p></li>
    <li><p><code>Queued</code>   Eine Anforderung wartet auf Verarbeitung.</p></li>
    </ul></td>
    </tr>
    <tr class="even">
    <td><p><strong>Tenant-Id</strong></p></td>
    <td><p>Für die interne Verwendung durch Microsoft reserviert.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Server-url</strong></p></td>
    <td><p>Enthält die URL des RMS-Servers, auf die bei dem Vorgang zugegriffen wurde.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Context</strong></p></td>
    <td><p>Wird vom aufrufenden Prozess dazu verwendet, mehrere RMS-Transaktionen zu verbinden. Gültige Werte sind:</p>
    <ul>
    <li><p><code>MessageID: &lt;Actual message ID&gt;</code></p></li>
    <li><p><code>MailboxGuid: &lt;Mailbox GUID&gt;</code></p></li>
    <li><p><code>AttachmentFileName: &lt;File name&gt;</code></p></li>
    </ul></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Transaction-id</strong></p></td>
    <td><p>Kennzeichnet eine eindeutige Transaktion. Alle Ereignisse, die im Verlauf derselben Transaktion auftreten, haben dieselbe Transaktions-ID.</p></td>
    </tr>
    </tbody>
    </table>


Zurück zum Seitenanfang

## Verwalten von IRM-Protokollen

Für jede Serverrolle, für die die IRM-Funktionen aktiviert sind, wird die IRM-Protokollierung standardmäßig aktiviert. Für jede Serverrolle können Sie die folgende IRM-Protokollkonfiguration ändern, indem Sie das **Set**-Cmdlet verwenden, das zur Serverrolle gehört. Wenn Sie beispielsweise die IRM-Protokollierung auf einem Postfachserver konfigurieren möchten, verwenden Sie das Cmdlet **Set-MailboxServer**.

### Konfigurationsparameter für IRM-Protokolle

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
<td><p><em>IrmLogEnabled</em></p></td>
<td><p>Aktiviert die Protokollierung von IRM-Transaktionen. Die IRM-Protokollierung ist standardmäßig aktiviert. Möchten Sie die IRM-Protokollierung für eine Serverrolle deaktivieren, legen Sie den Parameter auf <code>$false</code> fest.</p></td>
</tr>
<tr class="even">
<td><p><em>IrmLogMaxAge</em></p></td>
<td><p>Gibt das maximale Alter für eine IRM-Protokolldatei an. Dateien, deren Alter größer ist als das angegebene Alter, werden gelöscht. Der Standardwert lautet <code>30.00:00:00</code> (30 Tage).</p></td>
</tr>
<tr class="odd">
<td><p><em>IrmLogMaxDirectorySize</em></p></td>
<td><p>Gibt die maximale Größe aller IRM-Protokolle im Konnektivitätsprotokollverzeichnis an. Wenn die maximale Größe eines Verzeichnisses erreicht ist, löscht der Server zuerst die ältesten Protokolldateien. Der Standardwert ist <code>250 MB</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>IrmLogMaxFileSize</em></p></td>
<td><p>Gibt die maximale Größe für eine einzelne Protokolldatei an. Wenn eine Protokolldatei die angegebene Größe erreicht hat, wird eine Protokolldatei mit inkrementierter Instanznummer erstellt. Der Standardwert ist <code>10 MB</code>.</p></td>
</tr>
<tr class="odd">
<td><p><em>IrmLogPath</em></p></td>
<td><p>Gibt den Speicherort für IRM-Protokolle an. Der Standardpfad lautet &quot;%ExchangeInstallPath%Logging\IRMLogs&quot;.</p></td>
</tr>
</tbody>
</table>


Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\))

  - [Set-ClientAccessServer](https://technet.microsoft.com/de-de/library/bb125157\(v=exchg.150\))

  - [Set-TransportService](https://technet.microsoft.com/de-de/library/jj215682\(v=exchg.150\))

Zurück zum Seitenanfang

