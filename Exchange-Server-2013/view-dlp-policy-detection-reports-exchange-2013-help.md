---
title: 'Anzeigen von DLP-Richtlinienerkennungsberichten: Exchange 2013 Help'
TOCTitle: Anzeigen von DLP-Richtlinienerkennungsberichten
ms:assetid: 5c3f1cf6-d8c7-4d83-bb24-641ea9d50cbc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150520(v=EXCHG.150)
ms:contentKeyID: 50474783
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von DLP-Richtlinienerkennungsberichten

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-16_

Die DLP-Richtlinienerkennungsverwaltung (Data Loss Prevention, Verhinderung von Datenverlust) definiert die Maßnahmen, die eine Organisation ergreift, um Verstöße gegen DLP-Richtlinien zu identifizieren, zu untersuchen und zu beheben. Zum Verwalten von Vorfällen müssen Sie auf die Informationen zugreifen, welche die von den DLP-Richtlinien erkannten Verstöße identifizieren. Diese Erkennungsinformationen ist in vorhandene Microsoft Exchange Server 2013-Daten- und Protokollformate integriert, sodass Sie auf ein vorhandenes, umfangreiches Datensystem zur Verwaltung von Vorfällen im Zusammenhang mit dem E-Mail-Fluss zurückgreifen können.

Informationen zur Erstellung eines Schadensberichts zusammen mit einem einzigen Ereignis zur Richtlinienerkennung finden Sie unter [Erstellen von Schadensberichten für DLP-Richtlinienerkennungen](create-incident-reports-for-dlp-policy-detections-exchange-2013-help.md). Weitere Informationen zu Nachrichtenprotokollen finden Sie unter [Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md).


> [!NOTE]
> Exchange 2013: DLP ist ein Premium-Feature, für das eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) erforderlich ist. Weitere Informationen zu Clientzugriffslizenzen und zur Serverlizenzierung finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</A>.



## Überwachungsinformationen

Die Daten in Bezug auf das DLP-Erkennungsmanagement in Exchange sind in die Protokolle zur Nachrichtenverfolgung, die so genannten Zustellungsberichte, integriert. Die Funktionen greifen in hohem Maße auf das vorhandene Protokollierungsframework zurück, das im System verfügbar ist. Allgemeine Informationen, einschließlich grundlegender Informationen zur Struktur der Protokolldateien für die Nachrichtenverfolgung, finden Sie im Artikel [Grundlegendes zur Nachrichtenverfolgung](message-tracking-exchange-2013-help.md) oder unter [Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md).

Der Zustellungsbericht ist ein detailliertes Protokoll der gesamten Nachrichtenaktivität, die beim Übertragen von Nachrichten von einem Computer und an einen Computer auftritt, auf dem der Transportdienst im Postfachserver ausgeführt wird. Das Protokoll für die Nachrichtenverwaltung kann über die Exchange-Verwaltungsshell aufgerufen werden, indem Sie das Cmdlet **Get-MessageTrackingLog** verwenden. DLP-Daten sind in den Zustellungsbericht integriert und entsprechen den vorhandenen Datenformaten und -konventionen.

## Format für die Datenprotokollierung

Protokolle zur Nachrichtenverfolgung enthalten Daten der Agents, die an der Verarbeitung der Inhalte für den Nachrichtenfluss beteiligt sind. Für DLP wird der Transportregel-Agent dazu verwendet, eine eingehende Analyse von Nachrichteninhalten zu starten und die im Rahmen der ETRs definierten Richtlinien anzuwenden. Der vorhandene AgentInfo-Ereignis wird dazu verwendet, DLP-bezogene Einträge zum Protokoll für die Nachrichtenverfolgung hinzuzufügen.

Der Name des Agents lautet im AgentInfo-Ereignis **TRA** oder **Transportregel-Agent**. Pro Nachricht wird ein einzelnes AgentInfo-Ereignis protokolliert und beschreibt die auf die Nachricht angewendete DLP-Verarbeitung. Das Feld **CustomData** eines Protokolleintrags für die Nachrichtenverfolgung zeigt die vom Transportregel-Agent protokollierten DLP-Daten. Dieses Feld kann mehrere Einträge umfassen: eine Zeile für Datenklassifikation und Clientinformationen für jede in der Nachricht gefundene Datenklassifikation, eine Regelzeile für jede auf die Nachricht angewendete Regel und eine Zeile für die Integritätsüberwachung für jede Regel, für die der Schwellenwert für Last oder Ausführungszeit überschritten wird.

Nachfolgend wird ein Beispiel für einen DLP-Protokolleintrag gezeigt. Die Ausgabe wurde formatiert, um Zeichenfolgen in separaten Zeilen mit Leerzeilen anzuzeigen.

Quelle: AGENT

EventId: AGENTINFO

CustomData: S:TRA=DC|dcid=41BFDBC6C9D811E0816A3CD34824019B|count=10|conf=77;

S:TRA=DC|dcid=C7ECCBA0CA0011E0B6C00B124924019B|count=3|conf=81;

S:TRA=CI|sndOverride=or|just=Business Reason;

S:TRA=CI|sndOverride=fp;

S:TRA=ETR|ruleId=FC2AA60C9D811E0AFC076D34824019B|dlpid=1B81CC82C9DB11E09052C5D64824019B|st=2010-11-03 15:30T|action=PrependSubject|action=Encrypt|sev=2|mode=audit|dcid=41BFDBC6C9D811E0816A3CD34824019B|sndOverride=or;

S:TRA=ETR|ruleId=AB2AA60C9D811E0AFC076D34824019B|dlpid=1B81CC82C9DB11E09052C5D64824019B|st=2010-11-03 15:30T|action=Encrypt|sev=1|mode=enabled|dcid=C7ECCBA0CA0011E0B6C00B124924019B|sndOverride=fp;

S:TRA=ETRP|ruleId=C27D21EECA0311E0BCB896154924019B|LoadW=200|LoadC=100|ExecW=5500|ExecC=200;

Der Transportregel-Agent erfordert eine Gruppierung von Regel-ID, DLP-Richtlinien-ID (optional), Datum der letzten Änderung, Aktion, Schweregrad, Modus, erkannte Datenklassifikation (optional) und Außerkraftsetzung durch Absender (optional) basierend auf Regel-ID (angezeigt durch "TRA=ETR" in der Protokollzeile). Darüber hinaus müssen Datenklassifikations-ID, Anzahl und Bewertung von Klassifikationen nach Klassifikationsname gruppiert werden (angezeigt durch "TRA=DC" in der Protokollzeile).

Zusätzliche Gruppierungen umfassen Datenklassifikations-ID, Außerkraftsetzung durch Absender (optional) und Begründung für Außerkraftsetzung (optional) basierend auf der Datenklassifikations-ID für alle Klassifikationen, die auf dem Client erkannt wurden (angezeigt durch "TRA=CI" in der Protokollzeile). Der Transportregel-Agent erfordert außerdem eine Gruppierung von Regel-ID, Wanduhrzeit des Ladevorgangs (optional), CPU-Zeit des Ladevorgangs (optional), Wanduhrzeit der Ausführung (optional) und CPU-Zeit der Ausführung (optional) nach Regel-ID für alle Regeln, die die Schwellenwerte für die Wanduhr- oder CPU-Zeit des Lade- oder Ausführungsvorgangs überschreiten (angezeigt durch "TRA=ETRP" in der Protokollzeile).

Es folgt eine vollständige Liste dieser Datenfelder. Alle Daten im Protokoll für die Nachrichtenverfolgung sind vom Typ "string". Die Spalte "Format" beschreibt, wie jedes Feld im Protokoll für die Nachrichtenverfolgung erkannt wird. Die Spalte "Optionales Feld" gibt an, welche Felder bei einer Regelübereinstimmung möglicherweise nicht protokolliert werden. Die Spalte "DLP-spezifisch" zeigt, welche Felder speziell für die DLP-Funktion verwendet werden.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Feld</strong></p></td>
<td><p><strong>Beschreibung</strong></p></td>
<td><p><strong>Format</strong></p></td>
<td><p><strong>Optionales Feld</strong></p></td>
<td><p><strong>DLP-spezifisch</strong></p></td>
</tr>
<tr class="even">
<td><p>TRA</p></td>
<td><p>Transportregel-Agent, Typ: AgentName</p></td>
<td><p>TRA=DC, ETR, CI oder ETRP</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Gleichstrom</p></td>
<td><p>Datenklassifikation; Typ: groupName</p></td>
<td><p>TRA=DC</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>ETR</p></td>
<td><p>Exchange-Transportregel; Typ: groupName</p></td>
<td><p>TRA=ETR</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>CI</p></td>
<td><p>Clientinformationen; Typ: groupName</p></td>
<td><p>TRA=CI</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>ETRP</p></td>
<td><p>Leistung der Exchange-Transportregel; Typ: groupName</p></td>
<td><p>TRA=ETRP</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>dcid</p></td>
<td><p>ID der Datenklassifikation</p></td>
<td><p>dcid=GUID</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>count</p></td>
<td><p>Anzahl von Datenklassifikationen</p></td>
<td><p>count=Integer</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>conf</p></td>
<td><p>Bewertung der Datenklassifikation</p></td>
<td><p>conf=Integer (Prozent)</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>sndOverride</p></td>
<td><p>Außerkraftsetzung durch Absender; dieses Feld ist optional.</p>
<p>Wenn in der Zeile &quot;TRA=CI&quot; das Feld auf &quot;or&quot; festgelegt ist, bedeutet dies, dass die Datenklassifikation außer Kraft gesetzt wurde. Wenn das Feld auf &quot;fp&quot; festgelegt ist, wurde die Datenklassifikation als falsch positiv markiert.</p>
<p>Wenn das Feld in der Zeile &quot;TRA=ETR&quot; auf &quot;or&quot; festgelegt ist, wurde die Regel oder ein Teil der Regel außer Kraft gesetzt. Wenn das Feld auf &quot;fp&quot; festgelegt ist, wurde die Regel oder ein Teil der Regel als falsch positiv markiert.</p></td>
<td><p>sndOverride=or oder fp</p>
<p>Hierbei steht &quot;or&quot; für eine Außerkraftsetzung und &quot;fp&quot; für ein falsch positives Ergebnis. Das Feld &quot;sndOverride&quot; ist vorhanden, wenn ein Endbenutzer eine Außerkraftsetzung oder ein falsch positives Ergebnis für eine Regel gemeldet hat.</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>just</p></td>
<td><p>Begründung; das Feld ist optional und nur verfügbar, wenn das Feld für die Außerkraftsetzung durch den Absender in der Zeile &quot;TRA=CI&quot; auf &quot;or&quot; festgelegt ist. Die vom Endbenutzer angegebene Begründung für eine Außerkraftsetzung der Datenklassifikation.</p></td>
<td><p>just=IW (Zeichenfolge zur Eingabe der Begründung)</p>
<p>Das Feld für die Begründung wird nur protokolliert, wenn der Endbenutzer eine Außerkraftsetzung meldet.</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>ruleId</p></td>
<td><p>ID für eine Regel</p></td>
<td><p>ruleId=GUID</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>dlpId</p></td>
<td><p>ID für eine DLP-Richtlinie. Das Feld ist optional; wenn kein dlpld-Wert vorliegt, gehört die Regel nicht zu einer DLP-Richtlinie.</p></td>
<td><p>dlpId=GUID</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>st</p></td>
<td><p>Datum der letzten Änderung einer Regel</p></td>
<td><p>st=UTC date-time</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>action</p></td>
<td><p>Durch eine Regel durchgeführte Aktion; es können mehrere Aktionen pro Regel vorliegen</p></td>
<td><p>action=single action</p>
<p>Wenn mehrere Aktionen für eine Regel gelten, gibt es mehrere Aktionsfelder.</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>sev</p></td>
<td><p>Überwachungsschweregrad der Regel</p></td>
<td><p>sev=1, 2 oder 3</p>
<p>Hierbei steht 1 für niedrig, 2 für mittel und 3 für hoch.</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>mode</p></td>
<td><p>Status der Regel bei Auslösung (enforcement, audit oder auditandnotify).</p></td>
<td><p>mode=audit, auditandnotify oder enforcement</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>loadW</p></td>
<td><p>Wanduhrzeit des Ladevorgangs; das Feld ist optional</p></td>
<td><p>loadW=Zeit in Millisekunden</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>loadC</p></td>
<td><p>CPU-Zeit des Ladevorgangs; das Feld ist optional</p></td>
<td><p>loadC=Zeit in Millisekunden</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>execW</p></td>
<td><p>Wanduhrzeit der Ausführung; das Feld ist optional</p></td>
<td><p>execW=Zeit in Millisekunden</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>execC</p></td>
<td><p>CPU-Zeit der Ausführung; das Feld ist optional</p></td>
<td><p>execC=Zeit in Millisekunden</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichten-ID</p></td>
<td><p>ID der Nachricht</p></td>
<td><p>message-id=ID der Nachricht</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>date-time</p></td>
<td><p>Datum und Uhrzeit (in Weltzeit) der Übermittlung der Nachricht</p></td>
<td><p>date-time=UTC-Datum und -Uhrzeit</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>sender-address</p></td>
<td><p>Im Absenderfeld angegebene E-Mail-Adresse</p></td>
<td><p>sender-address=E-Mail-Adresse</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>recipient-address</p></td>
<td><p>E-Mail-Adresse(n) des bzw. der Nachrichtenempfänger(s)</p></td>
<td><p>recipient-address=E-Mail-Adresse</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>message-subject</p></td>
<td><p>Daten, die im Feld &quot;Betreff&quot; der Nachricht gefunden wurden</p></td>
<td><p>message-subject=Durch den Benutzer eingegebene Betreff-Daten</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Erstellen von Schadensberichten für DLP-Richtlinienerkennungen](create-incident-reports-for-dlp-policy-detections-exchange-2013-help.md)

[Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md)

