---
title: 'DSNs und NDRs in Exchange 2013: Exchange 2013 Help'
TOCTitle: DSNs und NDRs in Exchange 2013
ms:assetid: 8e91de84-76fa-49b2-898c-c5eface76560
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232118(v=EXCHG.150)
ms:contentKeyID: 50476155
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DSNs und NDRs in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_


> [!NOTE]
> Wenn Sie Hilfe mit NDRs in Office 365 oder Exchange Online benötigen, finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=524931">E-Mail-Unzustellbarkeitsberichte in Office 365</A> entsprechende Informationen.



Sollte ein Problem bei der Zustellung einer Nachricht auftreten, sendet Exchange Server 2013 eine Benachrichtigung über den Zustellungsstatus (Delivery Status Notification, DSN) an den Nachrichtenabsender. Diese vom System generierten Nachrichten werden auch als Unzustellbarkeitsnachrichten bezeichnet, und sie enthalten einen Fehlercode, technische Informationen über das Problem und manchmal Problembehandlungsschritte für den Absender der Nachricht. Bei Unzustellbarkeitsnachrichten (Non-Delivery Report, NDR) handelt es sich um einen allgemeinen Typ einer Statusbenachrichtigung. In diesem Thema für E-Mail-Administratoren werden mögliche Ursachen und Lösungen für viele NDR-Statuscodes beschrieben. Sie erfahren auch wie Unzustellbarkeitsnachrichten gelesen und gedeutet werden.

**Inhalt**

Häufig vorkommende erweiterte Statuscodes

Abschnitte von Unzustellbarkeitsberichten

Beispiele

## Häufig vorkommende erweiterte Statuscodes

Die folgende Tabelle enthält eine Liste der erweiterten Statuscodes, die in Unzustellbarkeitsberichten bei den am häufigsten vorkommenden Nachrichtenzustellungsfehlern zurückgegeben werden.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Erweiterter Statuscode</th>
<th>Beschreibung</th>
<th>Mögliche Ursache</th>
<th>Weitere Informationen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>4.3.1</p></td>
<td><p><code>Insufficient system resources</code></p></td>
<td><p>Ein Fehler durch unzureichenden Speicher ist aufgetreten. Ein Ressourcenproblem, beispielsweise eine volle Festplatte, kann die Ursache sein.</p>
<p>Möglicherweise erhalten Sie anstelle eines Fehlers wegen eines vollen Datenträgers eine Fehlermeldung wegen unzureichendem Speicher.</p></td>
<td><p>Stellen Sie sicher, dass der Servercomputer mit Exchange über ausreichenden Datenträgerspeicherplatz verfügt.</p></td>
</tr>
<tr class="even">
<td><p>4.3.2</p></td>
<td><p><code>System not accepting network messages</code></p></td>
<td><p>Dieser Unzustellbarkeitsbericht wird erstellt, wenn eine Warteschlange fixiert wurde.</p></td>
<td><p>Dieser Zustand kann behoben werden, indem Sie die Fixierung der Warteschlange aufheben.</p></td>
</tr>
<tr class="odd">
<td><p>4.4.1</p></td>
<td><p><code>Connection timed out</code></p></td>
<td><p>Der Zielserver reagiert nicht. Vorübergehende Netzwerkbedingungen können diesen Fehler verursachen. Der Exchange-Server versucht automatisch erneut einen Verbindungsaufbau mit dem Server, um die Nachricht zu übermitteln. Wenn die Übermittlung nach mehreren Versuchen fehlschlägt, wird ein Unzustellbarkeitsbericht mit diesem Fehlercode erstellt.</p></td>
<td><p>Überwachen Sie den Zustand. Es handelt sich möglicherweise um ein vorübergehendes Problem, das sich eventuell von selbst löst.</p></td>
</tr>
<tr class="even">
<td><p>4.4.2</p></td>
<td><p><code>Connection dropped</code></p></td>
<td><p>Eine Verbindung zwischen den Servern wurde abgebrochen. Vorübergehende Netzwerkbedingungen oder ein Server mit Problemen können diesen Fehler verursachen. Der sendende Server versucht, innerhalb einer festgelegten Zeitspanne erneute Nachrichtenübermittlungen durchzuführen, wonach weitere Statusberichte erstellt werden.</p></td>
<td><p>Überwachen Sie die Situation während der erneuten Übermittlungsversuche des Servers. Es handelt sich möglicherweise um ein vorübergehendes Problem, das sich eventuell von selbst löst.</p>
<p>Diese Situation kann ebenfalls eintreten, wenn der Grenzwert für die Nachrichtengröße für die Verbindung erreicht wird, oder wenn die Nachrichtenübermittlungsrate für die Client-IP-Adresse den konfigurierten Grenzwert überschritten hat.</p></td>
</tr>
<tr class="odd">
<td><p>4.4.7</p></td>
<td><p><code>Message expired</code></p></td>
<td><p>Die Nachricht in der Warteschlange ist abgelaufen. Der sendende Server versuchte, die Nachricht weiterzugeben oder zu übermitteln, der Vorgang konnte jedoch nicht abgeschlossen werden, bevor die Ablaufzeit der Nachricht erreicht wurde. Der Bericht kann ebenfalls darauf hinweisen, dass eine Begrenzung des Nachrichtenheaders auf dem Remoteserver erreicht wurde oder während der Kommunikation mit dem Remoteserver das Zeitlimit eines anderen Protokolls erreicht wurde.</p></td>
<td><p>Diese Nachricht deutet üblicherweise auf ein Problem beim empfangenden Server. Überprüfen Sie die Gültigkeit der Empfängeradresse und die ordnungsgemäße Konfiguration zum Empfang von Nachrichten des empfangenden Servers.</p>
<p>Möglicherweise müssen Sie die Anzahl der Empfänger im Nachrichtenheader für den Host reduzieren, von dem Sie den Fehler erhalten haben. Beim erneuten Senden der Nachricht wird sie wieder in die Warteschlange gestellt. Wenn der empfangende Server erreichbar ist, wird die Nachricht übermittelt.</p></td>
</tr>
<tr class="even">
<td><p>5.0.0</p></td>
<td><p><code>HELO / EHLO requires domain address</code></p></td>
<td><p>Diese Situation ist ein dauerhafter Fehler. Zu den möglichen Ursachen gehören:</p>
<ul>
<li><p>Es ist keine Route für den angegebenen Adressraum verfügbar, beispielsweise ist ein SMTP-Connector konfiguriert, die Adresse stimmt jedoch nicht überein.</p></li>
<li><p>DNS gibt einen autoritativen Host zurück, der für die Domäne nicht gefunden wurde.</p></li>
<li><p>Ein SMTP-Fehler ist aufgetreten.</p></li>
</ul></td>
<td><p>Einige mögliche Lösungen sind unter anderem:</p>
<ul>
<li><p>Fügen Sie auf einem oder mehreren SMTP-Connectors ein Sternchen-Platzhalterzeichen (<strong>*</strong>) als SMTP-Adressraum hinzu.</p></li>
<li><p>Überprüfen Sie, ob DNS arbeitet.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>5.1.0</p></td>
<td><p><code>Sender denied</code></p></td>
<td><p>Dieser NDR wird durch einen allgemeinen Fehler verursacht (ungültige Adresse). Eine E-Mail-Adresse oder ein anderes Attribut kann in Active Directory-Domänendiensten nicht gefunden werden. Kontakteinträge ohne das Attribut <strong>targetAddress</strong> können dieses Problem verursachen. Eine weitere mögliche Ursache könnte sein, dass das <strong>homeMDB</strong>-Attribut eines Benutzers nicht bestimmt werden konnte. Das Attribut <strong>homeMDB</strong> gehört zu dem Exchange-Server, auf dem sich das Postfach des Benutzers befindet.</p>
<p>Eine weitere übliche Ursache für diesen Unzustellbarkeitsbericht liegt darin, dass Sie Microsoft Outlook zum Speichern einer E-Mail-Nachricht als Datei verwenden und diese Nachricht dann offline geöffnet und beantwortet wird. Die Nachrichteneigenschaft behält bei der Übermittlung durch <strong>legacyExchangeDN</strong> nur das Attribut Outlook bei, daher können beim Suchvorgang Fehler auftreten.</p></td>
<td><p>Entweder ist die Empfängeradresse nicht ordnungsgemäß formatiert, oder der Empfänger konnte nicht richtig aufgelöst werden. Der erste Schritt zur Lösung des Problems ist die Überprüfung der Empfängeradresse und das erneute Senden der Nachricht.</p></td>
</tr>
<tr class="even">
<td><p>5.1.1</p></td>
<td><p><code>Bad destination mailbox address</code></p></td>
<td><p>Dieser Fehler kann die folgenden Ursachen haben:</p>
<ul>
<li><p>Die E-Mail-Empfängeradresse wurde vom Absender falsch eingegeben.</p></li>
<li><p>Im E-Mail-Zielsystem ist kein Empfänger vorhanden.</p></li>
<li><p>Das Empfängerpostfach wurde verschoben, und der Outlook-Empfängercache auf dem Computer des Absenders wurde nicht aktualisiert.</p></li>
<li><p>Ein ungültiger Legacy-DN (Distinguished Name) ist für das Empfängerpostfach in Active Directory-Domänendiensten vorhanden.</p></li>
</ul></td>
<td><p>Dieser Fehler tritt normalerweise auf, wenn der Absender der Nachricht die E-Mail-Adresse des Empfängers falsch eingibt. Der Absender sollte die E-Mail-Adresse des Empfängers überprüfen und die Nachricht dann erneut senden. Dieser Fehler kann auch auftreten, wenn die E-Mail-Empfängeradresse in der Vergangenheit richtig war, sich jedoch geändert hat oder aus dem E-Mail-Zielsystem entfernt wurde.</p>
<p>Wenn sich der Absender in derselben Exchange-Organisation wie der Empfänger befindet und das Empfängerpostfach noch vorhanden ist, sollten Sie bestimmen, ob das Empfängerpostfach auf einen neuen E-Mail-Server verschoben wurde. Wenn dies der Fall ist, hat Outlook möglicherweise den Empfängercache nicht ordnungsgemäß aktualisiert. Weisen Sie den Absender an, die Empfängeradresse aus dem Outlook-Empfängercache des Absenders zu entfernen, und erstellen Sie dann eine neue Nachricht. Wenn Sie die ursprüngliche Nachricht erneut senden, tritt der gleiche Fehler nochmals auf.</p>
<p>Auch andere Probleme können zu diesem Fehler führen, z. B. ein ungültiger Legacy-DN (Distinguished Name) in Active Directory-Domänendiensten. Untersuchen und korrigieren Sie den Legacy-DN des Empfängerpostfachs. Weisen Sie den Absender dann an, die Empfängeradresse aus dem Outlook-Empfängercache des Absenders zu entfernen, und erstellen Sie dann eine neue Nachricht. Wenn Sie die ursprüngliche Nachricht erneut senden, tritt der gleiche Fehler nochmals auf.</p></td>
</tr>
<tr class="odd">
<td><p>5.1.2</p></td>
<td><p><code>Invalid X.400 address</code></p></td>
<td><p>Der Empfänger hat eine Nicht-SMTP-Adresse, für die kein entsprechendes Ziel gefunden werden kann. Die Adresse scheint nicht lokal zu sein, und es sind keine Connectors vorhanden, die mit Adressräumen konfiguriert sind, die die Adresse des Empfängers enthalten.</p></td>
<td><p>Überprüfen Sie, dass die Adresse des Empfängers richtig eingegeben wurde. Wenn sich die Adresse des Empfängers in einem Nicht-SMTP-E-Mail-System befindet, für das Sie dezidiert E-Mail-Zustellung bereitstellen möchten, müssen Sie Ihrer Topologie den geeigneten Connectortyp hinzufügen und so konfigurieren, dass die Verarbeitung für das E-Mail-System des Empfängers bereitgestellt wird.</p></td>
</tr>
<tr class="even">
<td><p>5.1.3</p></td>
<td><p><code>Invalid recipient address</code></p></td>
<td><p>Diese Meldung weist darauf hin, dass die Empfängeradresse fehlerhaft in der Nachricht angezeigt wird.</p></td>
<td><p>Entweder ist die Empfängeradresse nicht ordnungsgemäß formatiert, oder sie konnte nicht richtig aufgelöst werden. Der erste Schritt zur Lösung des Problems ist die Überprüfung der Empfängeradresse und das erneute Senden der Nachricht.</p>
<p>Überprüfen Sie außerdem die SMTP-Empfängerrichtlinie, und stellen Sie sicher, dass alle E-Mail-Domänen, für die E-Mail akzeptiert werden soll, richtig angezeigt werden.</p></td>
</tr>
<tr class="odd">
<td><p>5.1.4</p></td>
<td><p><code>Destination mailbox address ambiguous</code></p></td>
<td><p>Mindestens zwei Empfänger in der Exchange-Organisation besitzen die gleiche Adresse.</p></td>
<td><p>Dieser Fehler tritt normalerweise aufgrund einer Fehlkonfiguration in Active Directory-Domänendiensten auf. Möglicherweise aufgrund von Replikationsproblemen besitzen zwei Empfängerobjekte in Active Directory-Domänendiensten dieselbe SMTP-Adresse oder Exchange Server-Adresse (EX).</p></td>
</tr>
<tr class="even">
<td><p>5.1.7</p></td>
<td><p><code>Invalid address</code></p></td>
<td><p>Der Absender hat eine ungültige oder fehlende SMTP-Adresse, das Attribut <strong>mail</strong> im Verzeichnisdienst. Das E-Mail-Element kann nicht ohne ein gültiges <strong>mail</strong>-Attribut übermittelt werden.</p></td>
<td><p>Überprüfen Sie die Verzeichnisstruktur des Absenders, und prüfen Sie das Vorhandensein des Attributs <strong>mail</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>5.2.1</p></td>
<td><p><code>Mailbox cannot be accessed</code></p></td>
<td><p>Auf das Postfach kann nicht zugegriffen werden. Möglicherweise ist das Postfach offline oder deaktiviert, oder die Nachricht wurde von einer Regel isoliert.</p></td>
<td><p>Überprüfen Sie, ob die Empfängerdatenbank online ist, ob das Empfängerpostfach deaktiviert ist und ob die Nachricht isoliert wurde.</p></td>
</tr>
<tr class="even">
<td><p>5.2.2</p></td>
<td><p><code>Mailbox full</code></p></td>
<td><p>Das Postfach des Empfängers hat sein Speicherkontingent überschritten und kann keine weiteren neuen Nachrichten annehmen.</p></td>
<td><p>Dieser Fehler tritt auf, wenn das Postfach des Empfängers sein Speicherkontingent überschritten hat. Der Empfänger muss die Größe des Postfachs verringern, oder der Administrator muss das Speicherkontingent vergrößern, bevor die Zustellung erfolgreich durchgeführt werden kann.</p></td>
</tr>
<tr class="odd">
<td><p>5.2.3</p></td>
<td><p><code>Message too large</code></p></td>
<td><p>Die Nachricht ist zu groß und übersteigt die lokale Begrenzung. Beispielsweise kann ein Exchange-Remotebenutzer möglicherweise eine Beschränkung der maximalen Größe für eine eingehende Nachricht haben.</p></td>
<td><p>Senden Sie die Nachricht ohne Anlagen erneut, oder konfigurieren Sie den Server oder die clientseitige Beschränkung, damit größere Nachrichten ermöglicht werden.</p></td>
</tr>
<tr class="even">
<td><p>5.2.4</p></td>
<td><p><code>Mailing list expansion problem</code></p></td>
<td><p>Der Empfänger ist eine fehlerhaft konfigurierte dynamische Verteilergruppe. Entweder die Filterzeichenfolge oder der Basis-DN der dynamischen Verteilerliste ist ungültig.</p></td>
<td><p>Legen Sie den Ereignisprotokolliergrad des Kategorisierungsmoduls mindestens auf die niedrigste Stufe fest, und senden Sie eine weitere Nachricht an die dynamische Verteilerliste. Überprüfen Sie das Anwendungsereignisprotokoll auf ein Ereignis &quot;6025&quot; oder &quot;6026&quot;, in dem angegeben wird, welches Attribut für das dynamische Verteilerlistenobjekt fehlerhaft konfiguriert ist.</p></td>
</tr>
<tr class="odd">
<td><p>5.3.3</p></td>
<td><p><code>Unrecognized command</code></p></td>
<td><p>Wenn der Exchange-Remoteserver die Kapazitätsgrenzen des Festplattenspeicherplatzes für Nachrichten ereicht, kann er mit diesem Unzustellbarkeitsbericht darauf reagieren. Dieser Fehler tritt üblicherweise auf, wenn der sendende Server die Nachrichten mit dem Befehl ESMTP BDAT sendet. Dieser Fehler zeigt ebenfalls einen möglichen SMTP-Fehler an.</p></td>
<td><p>Stellen Sie sicher, dass der Remoteserver über ausreichenden Festplattenspeicherplatz für Nachrichten verfügt. Überprüfen Sie das SMTP-Protokoll.</p></td>
</tr>
<tr class="even">
<td><p>5.3.4</p></td>
<td><p><code>Message too big for system</code></p></td>
<td><p>Die Nachricht übersteigt die Größenbeschränkung, die für eine Transportkomponente oder Postfachdatenbank konfiguriert wurde, und kann nicht akzeptiert werden. Dieser Fehler kann vom sendenden E-Mail-System oder vom E-Mail-System des Empfängers generiert werden.</p></td>
<td><p>Dieser Fehler tritt auf, wenn die Größe der vom Absender gesendeten Nachricht die maximal zulässige Nachrichtengröße übersteigt, wenn diese eine Transportkomponente oder Postfachdatenbank durchläuft. Der Absender muss die Größe der Nachricht verkleinern, damit diese erfolgreich zugestellt werden kann. Weitere Informationen zum Konfigurieren von Grenzwerten zur Nachrichtengröße finden Sie unter <a href="message-size-limits-exchange-2013-help.md">Beschränkungen der Nachrichtengröße</a>.</p></td>
</tr>
<tr class="odd">
<td><p>5.3.5</p></td>
<td><p><code>System incorrectly configured</code></p></td>
<td><p>Es wurde eine E-Mail-Schleifensituation erkannt, worunter eine Konfiguration des Servers zu verstehen ist, in der er Nachrichten an sich selbst übermittelt.</p></td>
<td><p>Überprüfen Sie die Konfiguration der Connectors des Servers auf Schleifen, und stellen Sie sicher, dass jeder Connector durch einen eindeutigen eingehenden Port definiert ist. Wenn mehrere virtuelle Server vorhanden sind, darf kein Server eine Festlegung auf Alle nicht zugewiesenen aufweisen.</p></td>
</tr>
<tr class="even">
<td><p>5.4.4</p></td>
<td><p><code>Invalid arguments</code></p></td>
<td><p>Dieser Unzustellbarkeitsbericht tritt auf, wenn keine Route zur Nachrichtenübermittlung vorhanden ist oder das Kategorisierungsmodul nicht in der Lage ist, das nächste Hop-Ziel zu ermitteln.</p></td>
<td><p>Überprüfen Sie, dass der angegebene Domänenname gültig ist und dass ein MX-Eintrag (Mail Exchanger)(MX) vorhanden ist.</p></td>
</tr>
<tr class="odd">
<td><p>5.4.6</p></td>
<td><p><code>Routing loop detected</code></p></td>
<td><p>Ein Konfigurationsfehler hat zu einer E-Mail-Schleife geführt. Standardmäßig unterbricht Exchange nach 20 Iterationen eine E-Mail-Schleife und generiert einen Unzustellbarkeitsbericht an den Absender der Nachricht.</p></td>
<td><p>Dieser Fehler tritt auf, wenn die Zustellung einer Nachricht eine andere Nachricht als Antwort generiert. Diese Nachricht generiert dann eine dritte Nachricht. Der Vorgang wird wiederholt, und es entsteht eine Schleife. Zum Schutz einer Überlastung der Systemressourcen unterbricht Exchange die E-Mail-Schleife nach 20 Iterationen. Nachrichtenschleifen werden normalerweise erstellt, weil ein Konfigurationsfehler auf dem sendenden E-Mail-Server, dem empfangenden E-Mail-Server oder auf beiden Servern vorliegt. Überprüfen Sie die Konfiguration der Postfachregeln des Empfängers und Absenders, um zu bestimmen, ob automatische Nachrichtenweiterleitung aktiviert ist.</p></td>
</tr>
<tr class="even">
<td><p>5.5.2</p></td>
<td><p><code>Send hello first</code></p></td>
<td><p>Ein generischer SMTP-Fehler tritt auf, wenn SMTP-Befehle vom Ablauf abweichend gesendet werden. Beispielsweise versucht ein Server den Befehl AUTH (Authorization) zu senden, bevor er sich selbst mit dem Befehl EHLO identifiziert hat.</p>
<p>Dieser Fehler kann möglicherweise auch dann auftreten, wenn die Systemfestplatte voll ist.</p></td>
<td><p>Verwenden Sie das SMTP-Protokoll oder den Netzwerkmonitor zur Sicherstellung, dass ausreichender Festplattenspeicherplatz und virtueller Speicher zur Verfügung steht.</p></td>
</tr>
<tr class="odd">
<td><p>5.5.3</p></td>
<td><p><code>Too many recipients</code></p></td>
<td><p>Die kombinierte Gesamtsumme der Empfänger in den Zeilen An, Cc und Bcc der Nachricht übersteigt die Gesamtanzahl der zulässigen Empfänger für eine einzelne Nachricht.</p></td>
<td><p>Dieser Fehler tritt auf, wenn der Absender zu viele Empfänger für die Nachricht angegeben hat. Der Absender muss die Anzahl der Empfängeradressen in der Nachricht verringern, oder die maximal zulässige Anzahl von Empfängern muss erhöht werden, damit die Nachricht erfolgreich zugestellt werden kann.</p></td>
</tr>
<tr class="even">
<td><p>5.5.4</p></td>
<td><p><code>Invalid domain name</code></p></td>
<td><p>Die Nachricht enthält entweder einen ungültigen Absender oder ein fehlerhaftes Empfängeradressformat.</p>
<p>Eine mögliche Ursache ist, dass das Empfängeradressformat eventuell Zeichen enthält, die nicht den Internet-Standards entsprechen.</p></td>
<td><p>Überprüfen Sie die Empfängeradresse auf nicht standardgemäße Zeichen.</p></td>
</tr>
<tr class="odd">
<td><p>5.5.6</p></td>
<td><p><code>Invalid message content</code></p></td>
<td><p>Diese Meldung weist auf einen möglichen Protokollfehler hin.</p></td>
<td><p>Überprüfen Sie das Ereignisprotokoll auf mögliche Fehler.</p></td>
</tr>
<tr class="even">
<td><p>5.7.1</p></td>
<td><p><code>Delivery not authorized</code></p></td>
<td><p>Der Absender der Nachricht darf keine Nachrichten an den Empfänger senden.</p></td>
<td><p>Dieser Fehler tritt auf, wenn der Absender versucht, eine Nachricht an einen Empfänger zu senden, der Absender jedoch nicht autorisiert ist, einen solchen Vorgang auszuführen. Dieser Fehler tritt häufig auf, wenn ein Absender versucht, Nachrichten an eine Verteilergruppe zu senden, die so konfiguriert wurde, dass nur Nachrichten von Mitgliedern dieser Verteilergruppe oder anderen autorisierten Absendern akzeptiert werden. Der Absender muss die Berechtigung beantragen, Nachrichten an den Empfänger senden zu dürfen.</p>
<p>Dieser Fehler kann auch auftreten, wenn eine Exchange-Transportregel eine Nachricht zurückweist, weil die Nachricht Bedingungen erfüllt hat, die für die Transportregel konfiguriert sind.</p></td>
</tr>
<tr class="odd">
<td><p>5.7.1</p></td>
<td><p><code>Unable to relay</code></p></td>
<td><p>Das sendende E-Mail-System darf keine Nachrichten an ein E-Mail-System senden, wenn dieses E-Mail-System nicht das Endziel der Nachricht ist.</p></td>
<td><p>Dieser Fehler tritt auf, wenn das sendende E-Mail-System versucht, eine anonyme Nachricht an das empfangende E-Mail-System zu senden, und das empfangende E-Mail-System keine Nachrichten für die in mindestens einem Empfänger angegebene(n) Domäne(n) akzeptiert. Dieser Fehler hat meistens die folgenden Gründe:</p>
<ul>
<li><p>Ein Dritter versucht, das empfangende E-Mail-System zum Senden von Spamnachrichten zu verwenden, und das empfangende E-Mail-System weist den Versuch zurück. Aufgrund der Spamnachricht wurde die E-Mail-Adresse des Absenders möglicherweise gefälscht, und der sich ergebende Unzustellbarkeitsbericht wurde ggf. an die E-Mail-Adresse des nichts ahnenden Absenders gesendet. Es ist schwierig, diese Situation zu vermeiden.</p></li>
<li><p>Ein MX-Eintrag für eine Domäne verweist auf ein empfangendes E-Mail-System, in dem die Domäne nicht akzeptiert wird. Der für den betreffenden Domänennamen verantwortliche Administrator muss den MX-Eintrag korrigieren oder das empfangende E-Mail-System so konfigurieren, dass an diese Domäne gesendete Nachrichten akzeptiert werden, bzw. beide Vorgänge durchführen.</p></li>
<li><p>Ein sendendes E-Mail-System oder ein Client, der das empfangende E-Mail-System für das Weiterleiten von Nachrichten verwenden soll, verfügt nicht über die erforderlichen Berechtigungen, diesen Vorgang auszuführen.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>5.7.1</p></td>
<td><p><code>Client was not authenticated</code></p></td>
<td><p>Das sendende E-Mail-System hat keine Authentifizierung bei dem empfangenden E-Mail-System durchgeführt. Das empfangende E-Mail-System erfordert vor der Nachrichtenübermittlung eine Authentifizierung.</p></td>
<td><p>Dieser Fehler tritt auf, wenn der empfangende Server vor der Nachrichtenübermittlung authentifiziert werden muss, und das sendende E-Mail-System keine Authentifizierung bei dem empfangenden E-Mail-System durchgeführt hat. Der Administrator des sendenden E-Mail-Systems muss das sendende E-Mail-System für die Authentifizierung bei dem empfangenden E-Mail-System konfigurieren, damit die Zustellung erfolgreich ist. Dieser Fehler kann auftreten, wenn Sie versuchen, anonyme Nachrichten aus dem Internet mithilfe eines Postfachservers zu akzeptieren, der nicht für diesen Zweck konfiguriert wurde.</p></td>
</tr>
<tr class="odd">
<td><p>5.7.3</p></td>
<td><p><code>Not Authorized</code></p></td>
<td><p>Der Absender hat die Neuzuweisung zum Alternativempfänger nicht zugelassen.</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Abschnitte von Unzustellbarkeitsberichten

In Exchange 2013 sind Unzustellbarkeitsberichte so aufgebaut, dass sie sowohl von Endbenutzern als auch von Administratoren leicht gelesen und verstanden werden. Informationen, die in einem Unzustellbarkeitsbericht angezeigt werden, sind in die folgenden beiden Abschnitte unterteilt:

  - Abschnitt mit Benutzerinformationen

  - Abschnitt mit Administratorinformationen

Die Informationen in den einzelnen Abschnitten richten sich an die jeweiligen Leser des betreffenden Abschnitts. Der Abschnitt mit den Benutzerinformationen wird zuerst aufgeführt und enthält Feedback für den Benutzer, der mithilfe einer nicht technischen Beschreibung informiert wird, warum ein Fehler bei der Zustellung der Nachricht aufgetreten ist. Der Abschnitt **Diagnoseinformationen für Administratoren** stellt tiefer gehende technische Informationen wie den Originalnachrichtenkopf bereit, um E-Mail-Administratoren bei der Problembehandlung für ein bestehendes Zustellungsproblem zu unterstützen. Die folgende Abbildung zeigt den Abschnitt **Benutzerinformationen** und den Abschnitt „Diagnoseinformationen für Administratoren“ eines Unzustellbarkeitsberichts.

**Abschnitte von Unzustellbarkeitsberichten**

![Unzustellbarkeitsbericht mit Diagnoseinformationen für Benutzer und Administrator](images/Bb232118.96245455-5fb9-4669-a931-5563ddd3ab35(EXCHG.150).png "Unzustellbarkeitsbericht mit Diagnoseinformationen für Benutzer und Administrator")

## Abschnitt mit den Benutzerinformationen

Der Abschnitt mit Benutzerinformationen in einem von Exchange generierten Unzustellbarkeitsbericht enthält Informationen für einen Benutzer, der eine Nachricht gesendet hat, die später mit einem Unzustellbarkeitsbericht zurückgegeben wurde. Der in diesem Abschnitt angezeigte Text wird von dem Exchange-Server eingefügt, der den Unzustellbarkeitsbericht generiert hat.

Mithilfe des Texts im Abschnitt mit den Benutzerinformationen können Endbenutzer ermitteln, warum die Nachricht zurückgewiesen wurde und wie die Nachricht ggf. erfolgreich erneut gesendet werden kann. Ggf. ist der vollqualifizierte Domänenname (FQDN) des Servers, der die Nachricht zurückgewiesen hat, im Abschnitt „Benutzerinformationen“ enthalten. Wenn Zustellungsfehler bei mehreren Empfängern auftreten, wird die E-Mail-Adresse jedes Empfängers aufgelistet, und der Grund für den Fehler wird unter der E-Mail-Adresse des Empfängers angegeben.

Sie können den Text im Abschnitt „Benutzerinformationen“ mithilfe des **New-SystemMessage**-Cmdlets ändern. Durch die Erstellung einer benutzerdefinierten Nachricht können Sie Endbenutzern spezifische Informationen bereitstellen, beispielsweise die Telefonnummer zur Kontaktaufnahme mit der Helpdeskabteilung oder einen Hyperlink zum Abrufen der Selbsthilfe.

Zurück zum Seitenanfang

## Diagnoseinformationen für Administratoren

Der Abschnitt **Diagnoseinformationen für Administratoren** enthält ausführlichere Informationen zum jeweiligen Fehler, der bei der Zustellung der Nachricht aufgetreten ist, zum Server, der den Unzustellbarkeitsbericht generiert hat, sowie zum Server, der die Nachricht zurückgewiesen hat. Die folgenden Felder sind in den meisten Unzustellbarkeitsberichten vorhanden und werden weiter oben in diesem Thema in der Abbildung "Abschnitte von Unzustellbarkeitsberichten" dargestellt:

  - **Generierender Server**   Der generierende Server ist der SMTP-Server, der den Unzustellbarkeitsbericht erstellt hat. Der generierende Server nimmt den erweiterten Statuscode an, der weiter unten in diesem Thema erläutert wird. Dieser Code erstellt einen einfach zu lesenden Unzustellbarkeitsbericht. Wenn kein Remoteserver unter der E-Mail-Adresse des Absenders im Abschnitt **Diagnoseinformationen für Administratoren** aufgelistet wird, ist der generierende Server auch der Server, der die ursprüngliche E-Mail-Nachricht zurückgewiesen hat. Wenn ein Fehler bei der Nachrichtenzustellung auftritt, wenn die Nachricht an einen anderen Empfänger in der Exchange-Organisation gesendet wird, weist derselbe Server die ursprüngliche Nachricht normalerweise zurück und generiert den Unzustellbarkeitsbericht.

  - **Zurückgewiesener Empfänger**   Der zurückgewiesene Empfänger ist die E-Mail-Adresse des Empfängers, an die der Zustellungsfehler der ursprünglichen Nachricht aufgetreten ist. Wenn ein Zustellungsfehler an mehrere Empfänger aufgetreten ist, wird die E-Mail-Adresse jedes Empfängers aufgelistet. Das Feld Zurückgewiesener Empfänger enthält außerdem die folgenden Unterfelder für jede der ausgeführten E-Mail-Adressen:
    
      - **Remoteserver**   Das Feld Remoteserver enthält den FQDN des Servers, der die Zustellung der Nachricht während der SMTP-Unterhaltung zurückgewiesen hat. Das Feld Remoteserver wird nur mit Daten aufgefüllt, wenn die Zustellung an einen Remoteserver versucht wurde und dieser Zustellungsversuch zurückgewiesen wurde, bevor der empfangende Server die Nachricht nach dem Senden des Nachrichtentexts erfolgreich bestätigt hat. Wenn die ursprüngliche Nachricht vom empfangenden Server erfolgreich bestätigt wurde und dann z. B. aufgrund von Inhaltsbeschränkungen zurückgewiesen wurde, wird das Feld Remoteserver nicht mit Daten aufgefüllt.
    
      - **Erweiterter Statuscode**   Der erweiterte Statuscode ist der Code, der von dem Server zurückgegeben wird, der die ursprüngliche Nachricht zurückgewiesen hat. Der erweiterte Statuscode zeigt an, warum die ursprüngliche Nachricht zurückgewiesen wurde. Der erweiterte Statuscode wird von Exchange nicht umgeschrieben. Stattdessen wird anhand dieses Codes bestimmt, welcher Text im Abschnitt Benutzerinformationen angezeigt wird. Die häufigsten der erweiterten Statuscodes werden unter "Häufig vorkommende erweiterte Statuscodes" weiter unten in diesem Thema aufgeführt. Eine ausführliche Liste der erweiterten Statuscodes finden Sie in RFC 3463.
    
      - **SMTP-Antwort**   Die SMTP-Antwort ist der maschinenlesbare Text, der von dem Server zurückgegeben wird, der die ursprüngliche Nachricht zurückgewiesen hat. Die SMTP-Antwort enthält normalerweise eine kurze Zeichenfolge, die eine Erläuterung des erweiterten Statuscodes bereitstellt, der ebenfalls zurückgegeben wird. Die SMTP-Antwort wird von Exchange nicht umgeschrieben. Außerdem wird diese Antwort immer im US-ASCII-Format dargestellt.

  - **Ursprüngliche Nachrichtenkopfzeilen**   Der Abschnitt Ursprüngliche Nachrichtenkopfzeilen enthält die Nachrichtenkopfzeilen der zurückgewiesenen Nachricht. Diese Kopfzeilen können nützliche Diagnoseinformationen zur Verfügung stellen, z. B. Informationen, die beim Bestimmen des Pfades hilfreich sind, den die Nachricht vor ihrer Zurückweisung durchlaufen hat, oder anhand derer Sie ermitteln können, ob das Feld **An** der E-Mail-Adresse entspricht, die im Feld Zurückgewiesener Empfänger angegeben wird.

Zurück zum Seitenanfang

## Beispiele für Unzustellbarkeitsberichte

Die folgenden Abschnitte stellen Beispiele für die zwei Arten zur Verfügung, auf die Unzustellbarkeitsberichte generiert werden können:

  - Durch den gleichen Server

  - Durch verschiedene Server

## Vom selben Server generierter Unzustellbarkeitsbericht und zurückgewiesene Originalnachricht

Das folgende Beispiel zeigt, was passiert, wenn eine E-Mail-Remoteorganisation die Zustellung einer E-Mail-Nachricht über einen Edge-Transport-Server akzeptiert und diese Nachricht dann aufgrund einer Richtlinieneinschränkung für das Postfach des Empfängers zurückweist. In diesem Fall darf der Absender keine Nachrichten an den Empfänger senden. Edge-Transport-Server führen keine Überprüfung der Nachrichtengröße durch, sodass der Edge-Transport-Server in diesem Beispiel die Nachricht akzeptiert, weil sie eine gültige Empfängeradresse aufweist und gegen keine anderen Inhaltsbeschränkungen verstößt. Da die E-Mail-Remoteorganisation die gesamte Nachricht einschließlich des Nachrichteninhalts akzeptiert, ist die E-Mail-Remoteorganisation für das Zurückweisen der Nachricht und die Generierung des Unzustellbarkeitsberichts verantwortlich, der an den Absender gesendet werden soll.

**Vom gleichen Server generierter Unzustellbarkeitsbericht und zurückgewiesene Nachricht**

![Unzustellbarkeitsbericht mit demselben generierenden und zurückweisenden Server](images/Bb232118.c9a7cd2d-f35f-4d77-8225-c29585fa3ccd(EXCHG.150).gif "Unzustellbarkeitsbericht mit demselben generierenden und zurückweisenden Server")

Auch Nachrichten, die beim Senden an Empfänger zurückgewiesen werden, die Teil derselben Exchange-Organisation sind, werden normalerweise von demselben E-Mail-Server zurückgewiesen, der den Unzustellbarkeitsbericht generiert. An lokale Empfänger gesendete Nachrichten können aus verschiedenen Gründen zurückgewiesen werden, z. B., weil Postfächer ihr Kontingent überschritten haben, keine Autorisierung für das Senden von Nachrichten an die Empfängeradresse vorhanden ist oder Hardwarefehler aufgetreten sind, die zu einem lange anhaltenden Verlust der Verbindung mit anderen Servern in der Organisation führen.

In beiden Situationen ist unter der E-Mail-Adresse der im Unzustellbarkeitsbericht aufgelisteten Empfänger kein Remoteserver enthalten.

Zurück zum Seitenanfang

## Von verschiedenen Servern generierter Unzustellbarkeitsbericht und zurückgewiesene Originalnachricht

Das folgende Beispiel zeigt, was passiert, wenn eine E-Mail-Remoteorganisation die Zustellung einer E-Mail-Nachricht zurückweist, bevor die Nachricht überhaupt akzeptiert wird. In diesem Beispiel weist der Remoteserver die Nachricht zurück und gibt einen erweiterten Statuscode an den lokalen sendenden Server zurück, weil der angegebene Empfänger nicht vorhanden ist. Die Zurückweisung geschieht, bevor der empfangende Server die Nachricht bestätigen kann. Weil der empfangende Server die Nachricht nicht erfolgreich bestätigt, ist der empfangende Server nicht für die Nachricht verantwortlich. Auf diesem Grund generiert der lokale sendende Server den Unzustellbarkeitsbericht und sendet diesen an den Absender der ursprünglichen Nachricht.

**Von verschiedenen Servern generierter Unzustellbarkeitsbericht und zurückgewiesene Nachricht**

![Unzustellbarkeitsbericht mit verschiedenen generierenden/sendenden Servern](images/Bb232118.adfb8d5a-9c1d-4cd9-8a71-ce14224434f8(EXCHG.150).gif "Unzustellbarkeitsbericht mit verschiedenen generierenden/sendenden Servern")

Zurück zum Seitenanfang

## Siehe auch


[Was sind Exchange NDRs (Non-Delivery Reports) in Office 365?](https://go.microsoft.com/fwlink/p/?linkid=524931)

