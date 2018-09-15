---
title: 'Ordner "Wiederherstellbare Elemente": Exchange 2013 Help'
TOCTitle: Ordner "Wiederherstellbare Elemente"
ms:assetid: efc48fb4-2ed8-4d05-93af-f3505fbc389d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364755(v=EXCHG.150)
ms:contentKeyID: 50477044
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ordner \"Wiederherstellbare Elemente\"

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Zum Schutz vor versehentlichen oder schädlichen Löschvorgängen und zum Erleichtern der Suche nach Daten zur Vorbereitung auf Rechtsstreitigkeiten oder Untersuchungen verwenden Microsoft Exchange Server 2013 und Exchange Online den Ordner „Wiederherstellbare Elemente“. Der Ordner "Wiederherstellbare Elemente" ersetzt die Funktion, die in früheren Versionen von Exchange als *Dumpster* bezeichnet wurde. Der Ordner "Wiederherstellbare Elemente" wird von den folgenden Exchange-Funktionen verwendet:

  - Aufbewahrungszeit für gelöschte Elemente

  - Wiederherstellung einzelner Elemente

  - Compliance-Archiv

  - Aufbewahrung für eventuelle Rechtsstreitigkeiten

  - Postfachüberwachungsprotokollierung

  - Kalenderprotokollierung

**Inhalt**

Terminologie

Ordner "Wiederherstellbare Elemente"

  - Aufbewahrungszeit für gelöschte Elemente

  - Wiederherstellung einzelner Elemente

  - Compliance-Archiv und Beweissicherungsverfahren

  - Schutz durch Kopie bei Schreibvorgang und geänderte Elemente

Postfachkontingente für "Wiederherstellbare Elemente"

## Terminologie

Sie sollten die folgenden Begriffe kennen, um den Inhalt in diesem Thema verstehen zu können.

  - **Löschen**  
    Beschreibt den Vorgang, bei dem ein Element aus einem Ordner gelöscht und im Standardordner "Gelöschte Elemente" platziert wird.

<!-- end list -->

  - **Endgültig löschen**  
    Beschreibt den Vorgang, bei dem ein Element aus dem Ordner "Gelöschte Elemente" gelöscht und im Standardordner "Wiederherstellbare Elemente" platziert wird. Beschreibt außerdem den Vorgang, bei dem ein Benutzer von Microsoft Outlook ein Element durch Drücken von UMSCHALT+ENTF löscht, wodurch der Ordner "Gelöschte Elemente" umgangen und das Element direkt im Ordner "Wiederherstellbare Elemente" platziert wird.

<!-- end list -->

  - **Gelöscht**  
    Beschreibt den Vorgang, bei dem ein Element zum dauerhaften Löschen aus der Postfachdatenbank markiert wird. Diese wird auch als *endgültiges Löschen* bezeichnet.

Zurück zum Seitenanfang

## Ordner "Wiederherstellbare Elemente"

Der Ordner "Wiederherstellbare Elemente" befindet sich in der Nicht-IPM-Unterstruktur der einzelnen Postfächer. Bei der Nicht-IPM-Unterstruktur handelt es sich um einen Speicherbereich innerhalb des Postfachs, der operative Daten zum Postfach enthält. Diese Unterstruktur ist für Benutzer von Outlook, Microsoft OfficeOutlook Web App oder anderen E-Mail-Clients nicht sichtbar.

Durch diese Änderung der Architektur ergeben sich die folgenden Vorteile:

  - Wird ein Postfach in eine andere Postfachdatenbank verschoben, wird der Ordner "Wiederherstellbare Elemente" ebenfalls verschoben.

  - Der Ordner "Wiederherstellbare Elemente" wird durch die Exchange-Suche indiziert und kann mithilfe der Compliance-eDiscovery durchsucht werden.

  - Der Ordner "Wiederherstellbare Elemente" besitzt ein eigenes Speicherkontingent.

  - Exchange kann verhindern, dass Daten aus dem Ordner "Wiederherstellbare Elemente" dauerhaft gelöscht werden.

  - Exchange kann Bearbeitungsvorgänge für bestimmte Inhalte nachverfolgen.

Der Ordner "Wiederherstellbare Elemente" enthält die folgenden Unterordner:

  - **Löschvorgänge**   Dieser Unterordner enthält alle Elemente, die aus dem Ordner „Gelöschte Elemente“ gelöscht wurden. (In Outlook können Sie Elemente dauerhaft löschen, indem Sie UMSCHALT+ENTF drücken.) Der Unterordner wird Benutzern über das Feature „Gelöschte Elemente wiederherstellen“ in Outlook und Outlook Web App angezeigt.

  - **Versionen**   Ist der In-Situ-Speicher oder Beweissicherungsverfahren aktiviert, enthält dieser Unterordner die ursprünglichen und die geänderten Versionen der gelöschten Elemente. Dieser Ordner ist für Endbenutzer nicht sichtbar.

  - **Löschvorgänge**   Ist das Beweissicherungsverfahren oder die Wiederherstellung einzelner Elemente aktiviert, enthält dieser Unterordner alle gelöschten Elemente. Dieser Ordner ist für Endbenutzer nicht sichtbar.

  - **Überwachungen**   Ist die Postfachüberwachungsprotokollierung für ein Postfach aktiviert, enthält dieser Unterordner die Überwachungsprotokolleinträge. Weitere Informationen zur Postfachüberwachungsprotokollierung finden Sie unter [Überwachungsprotokollierung von Postfächern](mailbox-audit-logging-exchange-2013-help.md).

  - **DiscoveryHolds**   Wenn In-Situ-Speicher aktiviert sind, enthält dieser Unterordner alle Elemente, die den Abfrageparametern des Archivs entsprechen und gelöscht werden.

  - **Kalenderprotokollierung**   Dieser Unterordner enthält Kalenderänderungen, die innerhalb eines Postfachs auftreten. Dieser Ordner ist für Benutzer nicht sichtbar.

Die folgende Abbildung zeigt die Unterordner in den Ordnern "Wiederherstellbare Elemente" Außerdem zeigt die Abbildung die Workflowprozesse der Aufbewahrung gelöschter Elemente, Wiederherstellung einzelner Elemente und Archivierung, die in den folgenden Abschnitten beschrieben werden.

![Ordner "Wiederherstellbare Elemente"](images/Ee364755.a1a08afc-3617-4adb-83ab-a6904516954e(EXCHG.150).gif "Ordner \"Wiederherstellbare Elemente\"")

Zurück zum Seitenanfang

## Aufbewahrungszeit für gelöschte Elemente

In folgenden Fällen gilt ein Element als dauerhaft gelöscht:

  - Ein Benutzer löscht ein Element oder leert alle Elemente aus dem Ordner "Gelöschte Elemente".

  - Ein Benutzer drückt UMSCHALT+ENTF, um ein Element aus einem anderen Postfachordner zu löschen.

Dauerhaft gelöschte Elemente werden in den Unterordner „Löschvorgänge“ des Ordners „Wiederherstellbare Elemente“ verschoben. Dies bietet zusätzliche Sicherheit, sodass Benutzer dauerhaft gelöschte Elemente wiederherstellen können, ohne den Helpdesk konsultieren zu müssen. Benutzer können das Feature „Gelöschte Elemente wiederherstellen“ in Outlook oder Outlook Web App verwenden, um ein gelöschtes Element wiederherzustellen. Benutzer können dieses Feature auch verwenden, um ein Element dauerhaft zu löschen. Weitere Informationen finden Sie unter:

  - [Wiederherstellen gelöschter Elemente in Outlook](https://go.microsoft.com/fwlink/p/?linkid=524923)

  - [Wiederherstellen gelöschter Elemente oder E-Mails in Outlook Online](https://go.microsoft.com/fwlink/p/?linkid=524924)

Elemente verbleiben im Unterordner "Löschvorgänge", bis das Ende der Aufbewahrungsdauer für gelöschte Elemente erreicht ist. Die Standardaufbewahrungsdauer für gelöschte Elemente beträgt für eine Postfachdatenbank 14 Tage. Sie können diese Dauer für eine Postfachdatenbank oder ein bestimmtes Postfach ändern. Neben der Aufbewahrungsdauer für gelöschte Elemente unterliegt der Ordner "Wiederherstellbare Elemente" auch Kontingenten. Weitere Informationen finden Sie später in diesem Thema unter Postfachkontingente für "Wiederherstellbare Elemente".

Nach Ablauf der Aufbewahrungsdauer für gelöschte Elemente wird das Element in den Ordner „Endgültige Löschvorgänge“ verschoben und ist für den Benutzer nicht mehr sichtbar. Wenn der Assistent für verwaltete Ordner das Postfach verarbeitet, werden Elemente im Ordner „Endgültige Löschvorgänge“ endgültig aus der Postfachdatenbank gelöscht und können nicht mehr wiederhergestellt werden.

Zurück zum Seitenanfang

## Wiederherstellung einzelner Elemente

Wird ein Element über das Feature "Gelöschte Elemente wiederherstellen" oder durch einen automatisierten Prozess wie den Assistenten für verwaltete Ordner aus dem Unterordner "Löschvorgänge" entfernt, kann das Element vom Benutzer nicht wiederhergestellt werden. In vorherigen Versionen von Exchange war für eine Wiederherstellung dieser Elemente die Wiederherstellung der Postfachdatenbank oder eines Postfachs aus Sicherungskopien durch einen Administrator erforderlich. Durch diesen Prozess verzögerte sich die Wiederherstellung um Minuten oder Stunden, je nachdem, welcher Sicherungsmechanismus verwendet wurde.

In Exchange 2013 können Sie die *Wiederherstellung einzelner Elemente* verwenden, um Elemente wiederherzustellen, ohne die Postfachdatenbanken mithilfe von Sicherungsmedien wiederherstellen zu müssen. Dies führt zu beträchtlich kürzeren Wiederherstellungszeiten. Wenn der Assistent für verwaltete Ordner den Ordner "Wiederherstellbare Elemente" für ein Postfach verarbeitet, für das die Wiederherstellung einzelner Elemente aktiviert ist, werden Elemente im Unterordner "Endgültige Löschvorgänge" nicht dauerhaft gelöscht, wenn die Aufbewahrungsdauer für das gelöschte Element noch nicht abgelaufen ist.

In der folgenden Tabelle sind die Inhalte und Aktionen aufgelistet, die im Ordner "Wiederherstellbare Elemente" durchgeführt werden können, wenn die Wiederherstellung einzelner Elemente aktiviert ist.

### Ordner "Wiederherstellbare Elemente" und Wiederherstellung einzelner Elemente

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Status der Wiederherstellung einzelner Elemente</th>
<th>Der Ordner „Wiederherstellbare Elemente“ enthält dauerhaft gelöschte Elemente</th>
<th>Der Ordner „Wiederherstellbare Elemente“ enthält gelöschte Elemente</th>
<th>Die Benutzer können Elemente im Ordner &quot;Wiederherstellbare Elemente&quot; dauerhaft löschen</th>
<th>Der Assistent für verwaltete Ordner löscht Elemente automatisch dauerhaft aus dem Ordner &quot;Wiederherstellbare Elemente&quot;</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aktiviert</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja. Benutzer können Elemente mit dem Feature „Gelöschte Elemente wiederherstellen“ in Outlook oder Outlook Web App löschen. Gelöschte Elemente werden erst dauerhaft gelöscht und aus der Postfachdatenbank entfernt, wenn der Aufbewahrungszeitraum für gelöschte Elemente abgelaufen ist.</p></td>
<td><p>Ja. Standardmäßig werden alle Elemente nach 14 Tagen dauerhaft gelöscht, mit Ausnahme von Kalendereinträgen, die nach 31 Tagen dauerhaft gelöscht werden.</p></td>
</tr>
<tr class="even">
<td><p>Deaktiviert</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja. In diesem Fall werden gelöschte Elemente zur dauerhaften Löschung aus der Postfachdatenbank gekennzeichnet und können nicht wiederhergestellt werden.</p></td>
<td><p>Ja. Standardmäßig werden alle Elemente nach 14 Tagen dauerhaft gelöscht, mit Ausnahme von Kalendereinträgen, die nach 31 Tagen dauerhaft gelöscht werden. Wenn der Warngrenzwert für &quot;Wiederherstellbare Elemente&quot; vor Ablauf der Aufbewahrungsdauer für gelöschte Elemente erreicht wird, werden Nachrichten nach der FIFO-Methode (First In, First Out) gelöscht, d. h. nach der Reihenfolge, in der sie im Ordner gespeichert wurden.</p></td>
</tr>
</tbody>
</table>


In Exchange 2013 ist die Wiederherstellung einzelner Elemente für neue Postfächer oder Postfächer, die aus einer früheren Version von Exchange verschoben wurden, nicht standardmäßig aktiviert. Sie müssen die Exchange-Verwaltungsshell verwenden, um die Wiederherstellung einzelner Elemente für ein Postfach zu aktivieren, und dann die Aufbewahrungsdauer für gelöschte Elemente konfigurieren oder ändern. Ausführliche Informationen zur Wiederherstellung einzelner Elemente finden Sie unter [Wiederherstellen von gelöschten Nachrichten im Postfach eines Benutzers](https://technet.microsoft.com/de-de/library/Ff660637(v=EXCHG.150)).

Zurück zum Seitenanfang

## Compliance-Archiv und Beweissicherungsverfahren

In Exchange 2013 und Exchange Online können Discovery Manager-Instanzen mithilfe der In-Situ-eDiscovery mit delegierten [Erkennungsverwaltung](discovery-management-exchange-2013-help.md)-Berechtigungen eDiscovery-Suchvorgänge für Postfachinhalte ausführen. Außerdem führen Exchange 2013 und Exchange Online den In-Situ-Speicher ein, mit der Sie Postfachelemente, die mit Abfrageparametern übereinstimmen, aufbewahren und sie vor dem Löschen durch Benutzer oder automatisierte Prozesse schützen können. Sie können das Beweissicherungsverfahren auch verwenden, um alle Elemente in Benutzerpostfächern aufzubewahren und die Elemente vor einer Löschung durch Benutzer oder automatisierte Prozesse zu schützen.

Bei Aktivieren der Compliance-Archivierung oder des Beweissicherungsverfahrens für ein Postfach wird der Assistent für verwaltete Ordner daran gehindert, Nachrichten automatisch aus den Unterordnern für Discovery-Archive und endgültige Löschvorgänge zu löschen. Darüber hinaus wird auch der Schutz durch Kopie bei Schreibvorgang für das Postfach aktiviert. Bei dem Verfahren zum Schutz durch Kopie bei Schreibvorgang wird eine Kopie des ursprünglichen Elements erstellt, bevor Änderungen in den Exchange-Speicher geschrieben werden. Wenn das Postfach aus dem Archiv entfernt wurde, setzt der Assistent für verwaltete Ordner das automatische dauerhafte Löschen fort.

In der folgenden Tabelle sind die Inhalte und Aktionen aufgelistet, die im Ordner "Wiederherstellbare Elemente" durchgeführt werden können, wenn die Aufbewahrung für das Beweissicherungsverfahren aktiviert ist.

### Ordner "Wiederherstellbare Elemente" und Archive

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Status der Aufbewahrung</th>
<th>Der Ordner „Wiederherstellbare Elemente“ enthält dauerhaft gelöschte Elemente</th>
<th>Der Ordner „Wiederherstellbare Elemente“ enthält geänderte und dauerhaft gelöschte Elemente</th>
<th>Die Benutzer können Elemente im Ordner &quot;Wiederherstellbare Elemente&quot; dauerhaft löschen</th>
<th>Der Assistent für verwaltete Ordner löscht Elemente automatisch dauerhaft aus dem Ordner &quot;Wiederherstellbare Elemente&quot;</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aktiviert</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja. Benutzer können Elemente mit dem Feature „Gelöschte Elemente wiederherstellen“ in Outlook oder Outlook Web App löschen. Der Assistent für verwaltete Ordner löscht diese Elemente jedoch nicht dauerhaft aus der Postfachdatenbank, wenn die Aufbewahrung für das Postfach aktiviert ist.</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Deaktiviert</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zur Compliance-eDiscovery, zum Compliance-Archiv und zum Beweissicherungsverfahren finden Sie in den folgenden Themen:

  - [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)

  - [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md)

Zurück zum Seitenanfang

## Schutz durch Kopie bei Schreibvorgang und geänderte Elemente

Nimmt ein Benutzer, für den das Compliance-Archiv oder das Beweissicherungsverfahren aktiviert ist, Änderungen an bestimmten Eigenschaften eines Postfachelements vor, wird vor dem Schreiben des geänderten Elements eine Kopie des ursprünglichen Postfachelements erstellt. Die ursprüngliche Kopie wird im Ordner "Versionen" gespeichert. Dieser Prozess ist als *Schutz durch Kopie bei Schreibvorgang* bezeichnet. Der Schutz durch Kopie bei Schreibvorgang gilt für Elemente, die sich in einem beliebigen Postfachordner befinden. Der Ordner "Versionen" ist für Benutzer nicht sichtbar.

In der folgenden Tabelle sind die Nachrichteneigenschaften aufgelistet, die den Schutz durch Kopie bei Schreibvorgang auslösen.

### Eigenschaften, die den Schutz durch Kopie bei Schreibvorgang auslösen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elementtyp</th>
<th>Eigenschaften, die den Schutz durch Kopie bei Schreibvorgang auslösen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nachrichten (IPM.Note*)</p>
<p>Beiträge (IPM.Post*)</p></td>
<td><ul>
<li><p>Betreff</p></li>
<li><p>Text</p></li>
<li><p>Anlagen</p></li>
<li><p>Absender und Empfänger</p></li>
<li><p>Sende- und Empfangsdatum</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Andere Elemente als Nachrichten und Beiträge</p></td>
<td><p>Jede Änderung an einer sichtbaren Eigenschaft mit folgenden Ausnahmen:</p>
<ul>
<li><p>Speicherort des Elements (wenn ein Element zwischen Ordnern verschoben wird)</p></li>
<li><p>Statusänderung des Elements (gelesen oder ungelesen)</p></li>
<li><p>Änderungen an dem einem Element zugewiesenen Aufbewahrungstag</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Elemente im Standardordner &quot;Entwürfe&quot;</p></td>
<td><p>Keine. Elemente im Ordner &quot;Entwürfe&quot; sind von dem Schutz durch Kopie bei Schreibvorgang ausgenommen.</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> Beim Schutz durch Kopie bei Schreibvorgang wird keine Version einer Besprechung gespeichert, wenn der Organisator einer Besprechung Antworten von Teilnehmern enthält und die Überwachungsinformationen der Besprechung aktualisiert werden. Auch Änderungen an RSS-Feeds werden nicht vom Kopie-bei-Schreibvorgang-Schutz erfasst.



Sind das Compliance-Archiv oder das Beweissicherungsverfahren für ein Postfach nicht länger aktiviert, werden Kopien geänderter Elemente, die im Ordner "Versionen" gespeichert sind, entfernt.

Zurück zum Seitenanfang

## Postfachkontingente für "Wiederherstellbare Elemente"

Wird ein Element in den Ordner "Wiederherstellbare Elemente" verschoben, wird seine Größe vom Postfachkontingent abgezogen und zur Größe des Ordners "Wiederherstellbare Elemente" hinzugefügt. In Exchange 2013 haben Postfachdatenbanken für den Ordner „Wiederherstellbare Elemente“ einen konfigurierbaren Warngrenzwert (*weiche Grenze*) von 20 GB und ein Kontingent (*harte Grenze*) von 30 GB. Diese Grenzwerte werden standardmäßig an alle Postfächer in der Datenbank vererbt. Sie können jedoch einzelne Postfächer mit anderen Kontingenten konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente](configure-deleted-item-retention-and-recoverable-items-quotas-exchange-2013-help.md).

In Exchange Online entsprechen die Standardbegrenzungen für das Kontingent „Wiederherstellbare Elemente“ dem Wert in Exchange 2013, die weiche Grenze liegt somit bei 20 GB und die harte Grenze bei 30 GB. Die Kontingente für den Ordner „Wiederherstellbare Elemente“ werden jedoch auf 90 bzw. 100 GB erhöht, wenn Sie für ein Postfach das Beweissicherungsverfahren aktivieren oder es im In-Situ-Speicher platzieren

Erreicht der Ordner "Wiederherstellbare Elemente" für ein Postfach das Kontingent für wiederherstellbare Elemente, können keine weiteren Elemente im Ordner gespeichert werden. Dies hat folgende Auswirkungen auf die Postfachfunktionen:

  - Postfachbenutzer können keine Elemente löschen.

  - Der Assistent für verwaltete Ordner kann keine Elemente auf der Grundlage von Aufbewahrungstags oder Einstellungen für verwaltete Ordner löschen.

  - Bei Postfächern, für die die Wiederherstellung einzelner Elemente, das Compliance-Archiv oder das Beweissicherungsverfahren aktiviert ist, kann der Prozess zum Schutz durch Kopie bei Schreibschutz keine Versionen von Elementen verwalten, die vom Benutzer bearbeitet wurden.

  - Bei Postfächern, für die die Postfachüberwachungsprotokollierung aktiviert ist, können keine Postfachüberwachungsprotokolle im Unterordner "Überwachungen" gespeichert werden.

Bei Postfächern, für die das Compliance-Archiv oder das Beweissicherungsverfahren nicht aktiviert ist, löscht der Assistent für verwaltete Ordner die Elemente aus dem Ordner "Wiederherstellbare Elemente" bei Ablauf der Aufbewahrungsdauer für gelöschte Elemente automatisch. Wenn der Ordner den Warngrenzwert für wiederherstellbare Elemente erreicht, löscht der Assistent Elemente automatisch nach dem FIFO-Verfahren.

Wenn der Ordner "Wiederherstellbare Elemente" die weichen und harten Standardgrenzwerte erreicht, werden Sie über ein Ereignisprotokoll und eine Warnung vom Microsoft System Center Operations Manager benachrichtigt. Diese Warnung wird ausgelöst, sobald der Ordner "Wiederherstellbare Elemente" die weichen und harten Standardgrenzwerte erreicht und anschließend einmal täglich.

In der folgenden Tabelle finden Sie eine Liste der Ereignisse, die protokolliert werden, wenn der Ordner "Wiederherstellbare Elemente" die weichen und harten Standardgrenzwerte erreicht.

### Kontingentwarnungen und -fehler für den Ordner "Wiederherstellbare Elemente"

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignis-ID</th>
<th>Typ</th>
<th>Quelle</th>
<th>Meldung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>10024</p></td>
<td><p>Warnung</p></td>
<td><p>MSExchangeIS-Postfachspeicher</p></td>
<td><p>Das Postfach für &lt;<em>Postfachbenutzer</em>&gt; (<em>GUID</em>) hat das Kontingent für wiederherstellbare Elemente, ab dem eine Warnung ausgegeben wird, überschritten. Entfernen Sie Elemente aus 'Wiederherstellbare Elemente', oder vergrößern Sie das Kontingent für wiederherstellbare Elemente, ab dem eine Warnung ausgegeben wird, und das Kontingent für wiederherstellbare Elemente. Wenn das Kontingent für wiederherstellbare Elemente überschritten wird, kann der Benutzer keine Elemente aus dem Postfach löschen.</p></td>
</tr>
<tr class="even">
<td><p>10023</p></td>
<td><p>Fehler</p></td>
<td><p>MSExchangeIS-Postfachspeicher</p></td>
<td><p>Das Postfach für &lt;<em>Postfachbenutzer</em>&gt; (<em>GUID</em>) hat das maximale Kontingent für wiederherstellbare Elemente überschritten. Es können keine Elemente aus diesem Postfach gelöscht werden. Der Postfachbesitzer sollte so bald wie möglich über diesen Zustand informiert werden. Entfernen Sie Elemente aus 'Wiederherstellbare Elemente', oder erhöhen Sie 'Kontingent für wiederherstellbare Elemente', damit die Funktionalität wiederhergestellt wird.</p></td>
</tr>
<tr class="odd">
<td><p>10023</p></td>
<td><p>Warnung</p></td>
<td><p>MSExchangeMailboxAssistants</p></td>
<td><p>Die Größe von &quot;Wiederherstellbare Elemente&quot; für &lt;<em>Postfachbenutzer</em>&gt; hat den Warngrenzwert für Kontingente überschritten. Aus den Ordnern für 'Wiederherstellbare Elemente' wurden Elemente gelöscht, um den Ausfall des Postfachs zu verhindern. Warngrenze für 'Wiederherstellbare Elemente': 20 GB (21.474.836.480 Bytes) Ursprungsgröße von 'Wiederherstellbare Elemente': 21475005311 Aktuelle Größe von 'Wiederherstellbare Elemente': 21474823820 Ordnerstatistik: - Verarbeitete Ordner: RecoverableItemsRoot, RecoverableItemsVersions, RecoverableItemsPurges, RecoverableItemsDeletions - Ursprüngliche Ordnergröße: 21391661934, 55190914, 1987247, 26157788 (Elementanzahl: 276828, 400, 84, 646) - Aktuelle Ordnergröße: 21391480443, 55190914, 1987247, 26157788 (Elementanzahl: 276817, 400, 84, 646)</p></td>
</tr>
</tbody>
</table>


Wenn für das Postfach das Compliance-Archiv oder das Beweissicherungsverfahren aktiviert ist, kann der Prozess zum Schutz durch Kopie bei Schreibvorgang keine Versionen geänderter Elemente verwalten. Zum Verwalten von Versionen geänderter Elemente müssen Sie die Größe des Ordners "Wiederherstellbare Elemente" reduzieren. Sie können das Cmdlet [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)) verwenden, um Nachrichten aus dem Ordner "Wiederherstellbare Elemente" eines Postfachs in ein Discoverypostfach zu kopieren und die Elemente anschließend aus dem Postfach zu löschen. Alternativ können Sie das Kontingent für den Ordner "Wiederherstellbare Elemente" für das Postfach heraufsetzen. Weitere Informationen finden Sie unter [Bereinigen des Ordners "Wiederherstellbare Elemente"](clean-up-the-recoverable-items-folder-exchange-2013-help.md).

Zurück zum Seitenanfang

## Weitere Informationen

  - Die Kopie-bei-Schreibvorgang-Funktion ist nur dann aktiviert, wenn für ein Postfach das Compliance-Archiv oder das Beweissicherungsverfahren aktiviert ist.

  - Sollte ein Benutzer gelöschte Elemente aus dem Ordner "Wiederherstellbare Elemente" wiederherstellen müssen, verweisen Sie ihn auf die folgenden Themen:
    
      - [Wiederherstellen gelöschter Elemente in Outlook](https://go.microsoft.com/fwlink/p/?linkid=524923)
    
      - [Wiederherstellen gelöschter Elemente oder E-Mails in Outlook Online](https://go.microsoft.com/fwlink/p/?linkid=524924)

Zurück zum Seitenanfang

