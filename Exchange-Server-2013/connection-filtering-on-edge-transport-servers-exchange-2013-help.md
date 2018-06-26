---
title: 'Verbindungsfilterung auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Verbindungsfilterung auf Edge-Transport-Servern
ms:assetid: b513755c-5d3e-44fa-a6cb-771d48b544ac
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124320(v=EXCHG.150)
ms:contentKeyID: 60828921
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verbindungsfilterung auf Edge-Transport-Servern

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die Verbindungsfilterung ist ein Antispamfeature in Microsoft Exchange Server 2013, das E-Mail basierend auf der Nachrichtenquelle zulässt oder blockiert. Die Verbindungsfilterung erfolgt durch den Verbindungsfilter-Agent, der nur auf Edge-Transport-Servern verfügbar ist. Der Verbindungsfilter-Agent verwendet die IP-Adresse der Mailservers, der die Verbindung herzustellen versucht, um ggf. die Aktion zu bestimmen, die auf eine eingehende Nachricht angewendet werden soll.

Der Verbindungsfilter-Agent ist standardmäßig der erste Antispam-Agent, der eine auf dem Edge-Transport-Server eingehende Nachricht prüft. Die IP-Quelladresse der SMTP-Verbindung wird mit den zugelassenen und blockierten IP-Adressen abgeglichen. Wenn die IP-Quelladresse zulässig ist, wird die Nachricht ohne weitere Verarbeitung durch andere Antispam-Agents an die Empfänger in Ihrer Organisation gesendet. Wenn die IP-Quelladresse nicht zulässig ist, wird die SMTP-Verbindung beendet. Wenn die IP-Quelladresse weder zulässig ist oder blockiert wird, durchläuft die Nachricht die Antispam-Agents auf dem Edge-Transport-Server.

Bei der Verbindungsfilterung wird die IP-Adresse des Quellmailservers mit den Werten in der IP-Zulassungsliste, IP-Sperrliste, Liste der Anbieter für zugelassene IP-Adressen und der IP-Sperrlistenanbieter verglichen. Sie müssen mindestens eine dieser vier IP-Adressdatenspeicher konfigurieren, damit die Verbindungsfilterung funktioniert. Wenn Sie keine IP-Adressdaten angeben, müssen Sie den Verbindungsfilter-Agent deaktivieren. Weitere Informationen finden Sie unter [Verwalten der Verbindungsfilterung auf Edge-Transport-Servern](manage-connection-filtering-on-edge-transport-servers-exchange-2013-help.md).

**Inhalt**

IP Block list

IP Allow list

IP Block List providers

IP Allow List providers

Test IP Block List providers and IP Allow List providers

Configure connection filtering on Edge Transport servers that aren't directly connected to the Internet

## IP-Sperrliste

Die IP-Sperrliste enthält die IP-Adressen der E-Mail-Server, die Sie blockieren möchten. Die IP-Adressen in der IP-Sperrliste werden manuell von Ihnen verwaltet. Sie können einzelne IP-Adressen oder IP-Adressbereiche hinzufügen. Sie können einen Ablaufzeitraum angeben, die bestimmt, wie lange der IP-Adresseintrag blockiert wird. Bei Erreichen des Ablaufzeitpunkts wird der IP-Adresseintrag in der IP-Sperrliste deaktiviert.

Wenn der Verbindungsfilter-Agent die IP-Quelladresse in der IP-Sperrliste findet, wird die SMTP-Verbindung beendet, nachdem alle **RCPT TO**-Kopfzeilen (Umschlagempfänger) in der Nachricht verarbeitet wurden.

IP-Adressen können der IP-Sperrliste auch mithilfe des Features der Absenderzuverlässigkeit des Protokollanalyse-Agents hinzugefügt werden. Weitere Informationen finden Sie unter [Absenderzuverlässigkeit und der Protokollanalyse-Agent](sender-reputation-and-the-protocol-analysis-agent-exchange-2013-help.md).

## IP-Zulassungsliste

Die IP-Zulassungsliste enthält die IP-Adressen der E-Mail-Server, die Sie als vertrauenswürdige E-Mail-Quellen einstufen möchten. E-Mail von Mailservern, die Sie in der IP-Zulassungsliste angeben, werden nicht von anderen Antispam-Agents von Exchange verarbeitet.

Die IP-Adressen in der IP-Zulassungsliste werden manuell von Ihnen verwaltet. Sie können einzelne IP-Adressen oder IP-Adressbereiche hinzufügen. Sie können einen Ablaufzeitraum angeben, die bestimmt, wie lange der IP-Adresseintrag zugelassen wird. Bei Erreichen des Ablaufzeitpunkts wird der Eintrag in der IP-Zulassungsliste deaktiviert.

Zurück zum Seitenanfang

## Anbieter für geblockte IP-Adressen

Beispiele

Wenn Sie die Verbindungsfilterung für die Nutzung eines IP-Sperrlistenanbieters konfigurieren, vergleicht der Verbindungsfilter-Agent die IP-Adresse des die Verbindung aufbauenden Mailservers mit der Liste der IP-Adressen beim IP-Sperrlistenanbieter. Bei einer Übereinstimmung gelangt die Nachricht nicht in Ihre Organisation. Sie können für die Verbindungsfilterung mehrere IP-Sperrlistenanbieter konfigurieren und jedem Anbieter unterschiedliche Prioritätswerte zuweisen.

Der Verbindungsfilter-Agent überprüft die IP-Quelladresse in der IP-Zulassungs- und der IP-Sperrliste. Wenn die IP-Adresse in keiner der Listen vorhanden ist, fragt der Verbindungsfilter-Agent den IP-Sperrlistenanbieter gemäß dem von Ihnen zugewiesenen Prioritätswert ab. Wenn die IP-Adresse bei einem IP-Sperrlistenanbieter vorhanden ist, wartet der Edge-Transport-Server auf die **RCPT TO**-Kopfzeile, verarbeitet diese, antwortet dem sendenden Mailserver mit dem Fehler `SMTP 550` und schließt die Verbindung. Die Verbindung wird nicht sofort beendet, damit der Verbindungsversuch protokolliert werden kann Sie Empfänger angeben können, deren Nachrichten keinen IP-Sperrlistenanbietern unterliegen.

Wenn die IP-Adresse bei keinem der IP-Sperrlistenanbieter angegeben ist, leitet der Inhaltsfilter-Agent die Nachricht an den nächsten Transport-Agent auf dem Edge-Transport-Server weiter.

Sie können für jeden IP-Sperrlistenanbieter den Fehler `SMTP 550` anpassen, der an den Absender zurückgegeben wird, wenn eine Nachricht blockiert wird. Sie müssen den IP-Sperrlistenanbieter angeben, der die Nachrichtenquelle als Spam identifiziert hat. Wenn ein legitimer Quellmailserver fälschlicherweise als Spamquelle eingestuft wird, kann der Administrator den IP-Sperrlistenanbieter kontaktieren und die erforderlichen Schritte zum Entfernen des Mailservers aus dem IP-Sperrlistenanbieter ausführen.

IP-Sperrlistenanbieter können unterschiedliche Codes zurückgeben, um anzugeben, warum eine IP-Adresse in ihren Listen enthalten ist. Die meisten IP-Sperrlistenanbieter geben Bitmasken oder absolute Werte als Datentypen zurück. Bei diesen Datentypen kann der IP-Sperrlistenanbieter mehrere Werte nutzen, um die IP-Adresse nach Bedrohungstyp einzustufen.

Bei Verwenden von IP-Sperrlistenanbietern müssen verschiedene Aspekte berücksichtigt werden:

  - Ausfälle oder Verzögerungen beim Dienst des IP-Sperrlistenanbieters können zu Verzögerungen bei der Verarbeitung von Nachrichten auf dem Edge-Transport-Server führen. Sie sollte stets zuverlässige IP-Sperrlistenanbieter wählen.

  - Quellserver, die Sie als legitim einschätzen, können fälschlicherweise als Spamquellen gekennzeichnet werden. Der Mailserver kann beispielsweise unbeabsichtigt für offenes Relay konfiguriert sein. Sie sollten sich stets für IP-Sperrlistenanbieter entscheiden, die eindeutige Verfahren zur Bewertung und Entfernung aus ihren Diensten bieten.

Zurück zum Seitenanfang

## Beispiele für Bitmasken und absolute Werte

Dieser Abschnitt enthält ein Beispiel der Statuscodes, die von den meisten IP-Sperrlistenanbietern zurückgegeben werden. Einzelheiten zu den vom Anbieter zurückgegebenen Statuscodes finden Sie in der Dokumentation des jeweiligen Anbieters.

Bei Bitmasken-Datentypen gibt der Dienst für IP-Sperrlistenanbieter den Statuscode "127.0.0.*x*" zurück, wobei die ganze Zahl *x* einem der in der folgenden Tabelle aufgeführten Werte entspricht.

### Werte und Statuscodes für Bitmasken-Datentypen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Statuscode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Die IP-Adresse steht in einer IP-Sperrliste.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Der SMTP-Server ist als offenes Relay konfiguriert.</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>Die IP-Adresse unterstützt eine Einwähl-IP-Adresse.</p></td>
</tr>
</tbody>
</table>


Bei absoluten Werten gibt der IP-Sperrlistenanbieter explizite Antworten zurück, die angeben, warum die IP-Adresse in ihren Sperrlisten enthalten ist. Die folgende Tabelle enthält Beispiele für absolute Werte und die dazugehörigen expliziten Antworten.

### Werte und Statuscodes für "Absoluter Wert"-Datentypen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Explizite Antwort</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>127.0.0.2</p></td>
<td><p>Die IP-Adresse ist eine direkte Spamquelle.</p></td>
</tr>
<tr class="even">
<td><p>127.0.0.4</p></td>
<td><p>Die IP-Adresse ist ein Massenversender von E-Mails.</p></td>
</tr>
<tr class="odd">
<td><p>127.0.0.5</p></td>
<td><p>Der Remoteserver, von dem die Nachricht gesendet wird, ist dafür bekannt, dass er mehrstufige offene Relays unterstützt.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Anbieter für zugelassene IP-Adressen

IP-Sperrlistenanbieter werden auch als *sichere Adressen* oder *Positivlisten* bezeichnet. Anbieter für zugelassene IP-Adressen werden wie IP-Sperrlistenanbieter konfiguriert, die Ergebnisse sind jedoch gegenteilig: Sie definieren E-Mail-Server-IP-Adressen, die definitiv nicht mit Spamaktivität verknüpft sind. Wenn die IP-Adresse des die Verbindung aufbauenden Mailservers bei einem Anbieter für zugelassene IP-Adressen verzeichnet ist, wird die Nachricht von keinen anderen Antispam-Agents von Exchange verarbeitet. Aus diesem Grund werden IP-Sperrlistenanbieter wesentlich häufiger als Anbieter für zugelassene IP-Adressen verwendet. Wählen Sie den Anbieter für zugelassene IP-Adressen sorgfältig aus.

Zurück zum Seitenanfang

## Testen von IP-Sperrlistenanbietern und Anbietern für zugelassene IP-Adressen

Nachdem Sie die Verbindungsfilterung für die Verwendung eines IP-Sperrlistenanbieters oder Anbieters für zugelassene IP-Adressen konfiguriert haben, können Sie mithilfe von Tests prüfen, ob die Anbieter ordnungsgemäß arbeiten. Die meisten Anbieter bieten IP-Testadressen zum Testen ihrer Dienste. Wenn Sie einen Anbieter testen, führt der Verbindungsfilter-Agent eine DNS-Abfrage aus, die in einer bestimmten Antwort des Anbieters resultieren sollte. Weitere Informationen zum Testen von IP-Adressen bei einem Anbieterdienst für blockierte bzw. für zugelassene IP-Adressen finden Sie unter [Verwalten der Verbindungsfilterung auf Edge-Transport-Servern](manage-connection-filtering-on-edge-transport-servers-exchange-2013-help.md).

Zurück zum Seitenanfang

## Konfigurieren der Verbindungsfilterung für Edge-Transport-Server, die nicht direkt mit dem Internet verbunden sind

Sie können die Verbindungsfilterung auf Edge-Transport-Servern nutzen, die E-Mail nicht direkt aus dem Internet empfangen. In diesem Szenario befindet sich der Edge-Transport-Server hinter einem anderen Mailserver, der direkt über das Internet eingehende Nachrichten empfängt und verarbeitet. Beispielsweise wenn Ihre Organisation E-Mail-Datenverkehr über einen Server, Dienst oder eine Appliance mit Antispamfunktion sendet, bevor die Nachrichten den Edge-Transport-Server erreichen. In diesem Szenario muss der Verbindungsfilter-Agent in der Lage sein, die richtige IP-Quelladresse aus der Nachricht zu extrahieren. Hierzu muss der Verbindungsfilter-Agent die Werte im Kopfzeilenfeld **Received** analysieren und diese Werte mit den bekannten IP-Adressen des Mailservers vergleichen, der sich zwischen dem Edge-Transport-Server und Internet befindet.

Jeder Mailserver, der eine SMTP-Nachricht akzeptiert und über den Übermittlungspfad weiterleitet, fügt der Nachrichtenkopfzeile ein eigenes Kopfzeilenfeld **Received** hinzu. Die Kopfzeile **Received** enthält meist den Domänennamen und die IP-Adresse des Mailservers, der die Nachricht verarbeitet hat.

Wenn der Edge-Transport-Server keine Nachrichten direkt aus dem Internet akzeptiert, müssen Sie den Parameter *InternalSMTPServers* des Cmdlets **Set-TransportConfig** auf einen Exchange 2013-Postfachserver anwenden, um die IP-Adresse des Mailservers anzugeben, der sich zwischen dem Edge-Transport-Server und Internet befindet. Die IP-Adressdaten werden von EdgeSync auf die Edge-Transport-Server repliziert. Wenn Nachrichten vom Edge-Transport-Server empfangen werden, nimmt der Verbindungsfilter-Agent an, dass eine IP-Adresse im Kopfzeilenfeld **Received**, die keinem Wert entspricht, der vom Parameter *InternalSMTPServers* angegeben wird, die zu prüfende IP-Quelladresse ist. Deshalb müssen Sie alle internen SMTP-Server angeben, damit die Verbindungsfilterung ordnungsgemäß funktioniert.

Zurück zum Seitenanfang

