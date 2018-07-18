---
title: 'Antispamstempel: Exchange 2013 Help'
TOCTitle: Antispamstempel
ms:assetid: 28d3a5c2-8509-4b25-9876-763536e77c27
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996878(v=EXCHG.150)
ms:contentKeyID: 50475244
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Antispamstempel

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Antispamstempel helfen Ihnen bei der Diagnose spambezogener Probleme, indem Diagnosemetadaten oder Stempel (z. B. absenderspezifische Informationen, Ergebnisse der Poststempelüberprüfung und Ergebnisse der Inhaltsfilterung) auf Nachrichten angewendet werden, während sie die Antispamfeatures passieren, die aus dem Internet eingehende Nachrichten filtern. Es gibt drei Antispamstempel: PCL-Stempel (Phishing Confidence Level), SCL-Stempel (Spam Confidence Level) und Sender ID-Stempel.

Sie können Antispamstempel als Diagnosetools verwenden, um zu ermitteln, welche Maßnahmen bei falsch positiven Ergebnissen und bei unter Spamverdacht stehenden Nachrichten zu ergreifen sind, die Personen in ihren Postfächern erhalten.

## Anzeigen von Antispamstempeln

Sie können Antispamstempel mithilfe von Microsoft Outlook anzeigen. Weitere Informationen finden Sie unter [Anzeigen von Antispamstempeln in Outlook](view-anti-spam-stamps-in-outlook-exchange-2013-help.md).

## Grundlegendes zum Antispambericht

Der Antispambericht ist ein Zusammenfassungsbericht der Ergebnisse der Antispamfilter, die auf eine E-Mail angewendet wurden. Der Inhaltsfilter-Agent wendet diesen Stempel auf den Nachrichtenumschlag in Form einer X-Header wie folgt an.

    X-MS-Exchange-Organization-Antispam-Report: DV:<DATVersion>;CW:CustomList;PCL:PhishingVerdict <verdict>;P100:PhishingBlock;PP:Presolve;SID:SenderIDStatus <status>;TIME:<SendReceiveDelta>;MIME:MimeCompliance 

In der folgenden Tabelle sind die Filterinformationen beschrieben, die in einem Antispambericht angezeigt werden können.


> [!NOTE]
> Der Antispambericht zeigt nur Informationen der Filter an, die auf die bestimmte Nachricht angewendet wurden. Ein Antispambericht enthält in der Regel nicht alle in der folgenden Tabelle aufgeführten Informationen. Sie können beispielsweise den folgenden Antispambericht erhalten: <CODE>DV:3.1.3924.1409;SID:SenderIDStatus Fail;PCL:PhishingLevel SUSPICIOUS;CW:CustomList;PP:Presolved;TIME:TimeBasedFeatures</CODE>.



### Filterinformationen in einem Antispambericht

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Stempel</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SID</p></td>
<td><p>Der Sender ID-Stempel (SID) basiert auf dem SPF (Sender Policy Framework), das die Verwendung von Domänen in E-Mails autorisiert. Das SPF wird im Nachrichtenumschlag als <code>Received-SPF</code> angezeigt. Der Auswertungsvorgang der Sender ID generiert einen Sender ID-Status für die Nachricht. Dieser Status kann als einer der folgenden Werte zurückgegeben werden:</p>
<ul>
<li><p><strong>Pass</strong>   Die IP-Adresse und die PRA (Purported Responsible Address) haben die Sender ID-Überprüfung bestanden.</p></li>
<li><p><strong>Neutral</strong>   Die veröffentlichten Sender ID-Daten sind explizit nicht eindeutig.</p></li>
<li><p><strong>Soft fail</strong>   Die IP-Adresse für die PRA ist möglicherweise im Nicht-Berechtigungssatz enthalten.</p></li>
<li><p><strong>Fail</strong>   Die IP-Adresse ist nicht zulässig; die eingehende E-Mail enthält keine PRA, oder die sendende Domäne ist nicht vorhanden.</p></li>
<li><p><strong>None</strong>   Es sind keine veröffentlichten SPF-Daten (Sender Policy Framework) im DNS des Absenders vorhanden.</p></li>
<li><p><strong>TempError</strong>   Es liegt ein vorübergehender DNS-Fehler vor, z. B. ein nicht verfügbarer DNS-Server.</p></li>
<li><p><strong>PermError</strong>   Der DNS-Datensatz ist ungültig, z. B. ein Fehler im Datensatzformat.</p></li>
</ul>
<p>Der Sender ID-Stempel wird wie folgt als X-Header im Nachrichtenumschlag angezeigt:</p>
<pre><code>X-MS-Exchange-Organization-SenderIdResult:&lt;status&gt;</code></pre>
<p>Weitere Informationen zur Sender ID finden Sie unter <a href="sender-id-exchange-2013-help.md">Absender-ID</a>.</p></td>
</tr>
<tr class="even">
<td><p>DV</p></td>
<td><p>Der Stempel &quot;DAT-Version (DV)&quot; kennzeichnet die Version der Spamdefinitionsdatei, die beim Überprüfen dieser Nachricht verwendet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>SA</p></td>
<td><p>Der SA-Stempel (Signature Action) gibt an, dass die Nachricht aufgrund einer in der Nachricht gefundenen Signatur entweder wiederhergestellt oder gelöscht wurde.</p></td>
</tr>
<tr class="even">
<td><p>SV</p></td>
<td><p>Der SV-Stempel (Signature DAT Version) kennzeichnet die Version der Signaturdatei, die beim Überprüfen der Nachricht verwendet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>PCL</p></td>
<td><p>Der PCL-Stempel zeigt die Bewertung der Nachricht auf Grundlage des Inhalts an. Er wird angewendet, wenn die Nachricht vom Inhaltsfilter-Agent verarbeitet wird. Dieser Status kann als einer der folgenden Werte zurückgegeben werden:</p>
<ul>
<li><p><strong>Neutral</strong>   Der Inhalt der Nachricht wird wahrscheinlich nicht zum Phishing genutzt.</p></li>
<li><p><strong>Verdächtig   </strong>Der Inhalt der Nachricht wird wahrscheinlich zum Phishing genutzt.</p></li>
</ul>
<p>Der PCL-Wert liegt zwischen 1 und 8. Eine PCL-Bewertung von 1 bis 3 gibt den Status <code>Neutral</code> zurück. Das bedeutet, der Inhalt der Nachricht wird wahrscheinlich nicht zum Phishing genutzt. Eine PCL-Bewertung zwischen 4 und 8 gibt den Status <code>Suspicious</code> zurück. Das bedeutet, der Inhalt der Nachricht wird wahrscheinlich zum Phishing genutzt.</p>
<p>Anhand dieser Werte wird ermittelt, welche Aktion Outlook für die Nachrichten ausführt. Outlook verwendet den PCL-Stempel, um den Inhalt von verdächtigen Nachrichten zu blockieren.</p>
<p>Der PCL-Stempel wird wie folgt als X-Header im Nachrichtenumschlag angezeigt:</p>
<pre><code>X-MS-Exchange-Organization-PCL:&lt;status&gt;</code></pre></td>
</tr>
<tr class="even">
<td><p>SCL (Spam Confidence Level)</p></td>
<td><p>Der SCL-Stempel der Nachricht zeigt die Bewertung der Nachricht auf Grundlage ihres Inhalts an. Der Inhaltsfilter-Agent verwendet Microsoft SmartScreen-Technologie für die Bewertung des Inhalts einer Nachricht sowie zum Zuweisen einer SCL-Bewertung zu jeder Nachricht. Der SCL-Wert liegt zwischen 0 und 9, wobei 0 mit geringerer Wahrscheinlichkeit und 9 mit höherer Wahrscheinlichkeit als Spam angesehen wird. Die von Exchange und Outlook eingeleiteten Maßnahmen hängen von Ihren Einstellungen für den SCL-Schwellenwert ab.</p>
<p>Der SCL-Stempel wird wie folgt als X-Header im Nachrichtenumschlag angezeigt:</p>
<pre><code>X-MS-Exchange-Organization-SCL:&lt;status&gt;</code></pre>
<p>Weitere Informationen zu SCL-Schwellenwerten und Maßnahmen finden Sie unter <a href="spam-confidence-level-threshold-exchange-2013-help.md">SCL-Schwellenwert</a>.</p></td>
</tr>
<tr class="odd">
<td><p>CW</p></td>
<td><p>Der CW-Stempel (Custom Weight) einer Nachricht gibt an, dass die Nachricht ein nicht zugelassenes Wort oder einen nicht zugelassenen Ausdruck enthält und dass der SCL-Wert bzw. die &quot;Gewichtung&quot; dieses nicht zugelassenen Worts oder Ausdrucks in die abschließende SCL-Bewertung einbezogen wurde:</p>
<ul>
<li><p>Nicht zugelassene Ausdrücke oder Sperrausdrücke haben eine maximale Gewichtung und ändern die SCL-Auswertung zu 9.</p></li>
<li><p>Zugelassene Wörter oder Ausdrücke oder Zulassungsausdrücke haben eine minimale Gewichtung und ändern die SCL-Auswertung zu 0.</p></li>
</ul>
<p>Weitere Informationen zum Hinzufügen zugelassener und nicht zugelassener Wörter oder Ausdrücke zum Inhaltsfilter-Agent finden Sie unter <a href="manage-content-filtering-exchange-2013-help.md">Verwalten der Inhaltsfilterung</a>.</p></td>
</tr>
<tr class="even">
<td><p>PP</p></td>
<td><p>Der PP-Stempel (Presolved Puzzle) gibt an, dass der Absender wahrscheinlich kein böswillige Absender ist, wenn dessen Nachricht einen gültigen, gelösten Rechenpoststempel enthält, der auf der E-Mail-Poststempelüberprüfung von Outlook basiert. In diesem Fall senkt der Inhaltsfilter-Agent die SCL-Bewertung.</p>
<p>Der Inhaltsfilter-Agent ändert die SCL-Bewertung nicht, wenn die E-Mail-Poststempelüberprüfung aktiviert ist und eine der folgenden Bedingungen zutrifft:</p>
<ul>
<li><p>Eine eingehende Nachricht enthält keine Kopfzeile mit Rechenpoststempel.</p></li>
<li><p>Die Kopfzeile mit dem Rechenpoststempel ist ungültig.</p></li>
</ul>
<p>Weitere Informationen zur Poststempelüberprüfung finden Sie unter <a href="content-filtering-exchange-2013-help.md">Inhaltsfilterung</a>.</p></td>
</tr>
<tr class="odd">
<td><p>TIME:TimeBasedFeatures</p></td>
<td><p>Der Stempel TIME gibt an, dass zwischen dem Absenden und dem Eingang der Nachricht ein beachtlicher Zeitunterschied herrscht. Der TIME-Stempel wird zum Bestimmen der abschließenden SCL-Bewertung für die Nachricht verwendet.</p></td>
</tr>
<tr class="even">
<td><p>MIME:MIMECompliance</p></td>
<td><p>Der MIME-Stempel gibt an, dass die E-Mail nicht MIME-kompatibel ist.</p></td>
</tr>
<tr class="odd">
<td><p>P100:PhishingBlock</p></td>
<td><p>Der P100-Stempel gibt an, dass die Nachricht eine URL enthält, die in einer Phishing-Definitionsdatei enthalten ist.</p></td>
</tr>
<tr class="even">
<td><p>IPOnAllowList</p></td>
<td><p>Der Stempel IPOnAllowList gibt an, dass sich die IP-Adresse des Absenders in der Liste der zulässigen IP-Adressen befindet. Weitere Informationen zur IP-Zulassungsliste finden Sie unter <a href="http://go.microsoft.com/fwlink/?linkid=268732">Grundlegendes zur Verbindungsfilterung</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MessageSecurityAntispamBypass</p></td>
<td><p>Der Stempel &quot;MessageSecurityAntispamBypass&quot; gibt an, dass der Inhalt der Nachricht nicht gefiltert wurde und dass dem Absender die Berechtigung erteilt wurde, die Antispamfilter zu umgehen.</p></td>
</tr>
<tr class="even">
<td><p>SenderBypassed</p></td>
<td><p>Der Stempel &quot;SenderBypassed&quot; gibt an, dass der Inhaltsfilter-Agent für Nachrichten keine Inhaltsfilterung ausführt, die von diesem Absender empfangen werden. Weitere Informationen finden Sie unter <a href="manage-content-filtering-exchange-2013-help.md">Verwalten der Inhaltsfilterung</a>.</p></td>
</tr>
<tr class="odd">
<td><p>AllRecipientsBypassed</p></td>
<td><p>Der Stempel &quot;AllRecipientsBypassed&quot; gibt an, dass eine der folgenden Bedingungen für alle in der Nachricht aufgeführten Empfänger zutrifft:</p>
<ul>
<li><p>Der Parameter <em>AntispamBypassedEnabled</em> ist für das Postfach des Empfängers auf den Wert <code>$true</code> eingestellt. Dies ist eine Einstellung auf Empfängerebene, die nur von einem Administrator und unter Verwendung des Cmdlets <strong>Set-Mailbox</strong> festgelegt werden kann.</p></li>
<li><p>Der Nachrichtenabsender befindet sich in der Outlook-Liste der sicheren Absender des Empfängers. Weitere Informationen zur Liste der sicheren Absender finden Sie unter <a href="manage-safelist-aggregation-exchange-2013-help.md">Verwalten der Aggregation von Listen sicherer Adressen</a>.</p></li>
<li><p>Der Inhaltsfilter-Agent führt keine Inhaltsfilterung für Nachrichten aus, die an diesen Empfänger gesendet wurden. Weitere Informationen zu Empfängerausnahmen finden Sie unter <a href="manage-content-filtering-exchange-2013-help.md">Verwalten der Inhaltsfilterung</a>.</p></li>
</ul></td>
</tr>
</tbody>
</table>

