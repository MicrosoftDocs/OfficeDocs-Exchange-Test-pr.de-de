---
title: 'Sicherheitsnetz: Exchange 2013 Help'
TOCTitle: Sicherheitsnetz
ms:assetid: d0abb807-3b12-4c7d-bc7e-769b87c84ccb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657495(v=EXCHG.150)
ms:contentKeyID: 50476767
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Sicherheitsnetz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In Microsoft Exchange Server 2013 ist der primäre Mechanismus für hohe Verfügbarkeit von Postfächern die Database Availability Group (DAG). Weitere Informationen zu Database Availability Groups finden Sie unter [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md). Der *Transportdumpster* wurde mit Exchange 2007 eingeführt und in Exchange 2010 weiter verbessert. Jetzt unterstützt er redundante Kopien von Nachrichten, nachdem sie erfolgreich an die Postfächer in DAGs zugestellt wurden. In Exchange 2010 diente der Transportdumpster zum Schutz vor Datenverlusten. Dazu wurde eine Warteschlange erfolgreich zugestellter Nachrichten beibehalten, die noch nicht in passiven Postfachdatenbankkopien in der DAG repliziert wurden. Wenn aufgrund eines Ausfalls einer Postfachdatenbank oder eines Servers eine veraltete Kopie der Postfachdatenbank höher gestuft werden musste, wurden die Nachrichten im Transportdumpster automatisch an die neue aktive Kopie der Postfachdatenbank erneut übermittelt.

Der Transportdumpster wurde in Exchange 2013 verbessert und heißt jetzt *Sicherheitsnetz*.

So gleichen sich das Sicherheitsnetz und der Transportdumpster in Exchange 2010:

  - Das Sicherheitsnetz ist eine Warteschlange, die mit dem Transportdienst auf einem Postfachserver verbunden ist. In dieser Warteschlange werden Kopien von Nachrichten gespeichert, die vom Server erfolgreich verarbeitet wurden.

  - Sie können angeben, wie lange das Sicherheitsnetz Kopien der erfolgreich verarbeiteten Nachrichten speichert, bevor sie ablaufen und automatisch gelöscht werden. Der Standardwert beträgt 2 Tage.

So unterscheidet sich das Sicherheitsnetz in Exchange 2013:

  - Das Sicherheitsnetz erfordert keine DAGs. Für Postfachserver, die zu DAGs gehören, speichert das Sicherheitsnetz Kopien zugestellter Nachrichten auf anderen Postfachservern am lokalen Active Directory-Standort.

  - Das Sicherheitsnetz selbst ist jetzt redundant und nicht mehr eine einzelne Fehlerquelle. Damit werden die Konzepte des *primären Sicherheitsnetzes* und des *Shadow-Sicherheitsnetzes* eingeführt. Wenn das primäre Sicherheitsnetz für mehr als 12 Stunden nicht verfügbar ist, werden Anforderungen zur Neuübermittlung zu Anforderungen zur Shadow-Neuübermittlung, und Nachrichten werden aus dem Shadow-Sicherheitsnetz erneut übermittelt.

  - Das Sicherheitsnetz übernimmt einige Aufgaben der Shadow-Redundanz in DAG-Umgebungen. Für die Shadow-Redundanz muss keine zusätzliche Kopie der zugestellten Nachricht in einer Shadow-Warteschlange erhalten bleiben, während darauf gewartet wird, dass die zugestellte Nachricht in den passiven Kopien der Postfachdatenbank auf anderen Postfachservern in der DAG repliziert wird. Die Kopie der zugestellten Nachricht ist bereits im Sicherheitsnetz gespeichert. Die Nachricht kann also bei Bedarf über das Sicherheitsnetz erneut übermittelt werden.

  - In Exchange 2013 ist hohe Transportverfügbarkeit mehr als nur eine Bemühung für Nachrichtenredundanz. Exchange 2013 versucht, Nachrichtredundanz zu garantieren. Daher können Sie keine maximale Größenbeschränkung für das Sicherheitsnetz angeben. Sie können nur angeben, wie lange Nachrichten vom Sicherheitsnetz gespeichert werden, bevor sie automatisch gelöscht werden.

**Inhalt**

Funktionsweise des Sicherheitsnetzes

Erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz

Erneute Übermittlung von Nachrichten aus dem Shadow-Sicherheitsnetz

## Funktionsweise des Sicherheitsnetzes

Für die Shadow-Redundanz wird eine redundante Kopie der Nachricht gespeichert, während die Nachricht übertragen wird. Das Sicherheitsnetz bewahrt eine redundante Kopie einer Nachricht auf, nachdem die Nachricht erfolgreich verarbeitet wurde. Das Sicherheitsnetz setzt also da ein, wo die Shadow-Redundanz endet. Die gleichen Konzepte wie im Zusammenhang mit Shadow-Redundanz, einschließlich der Grenzen für hohe Transportverfügbarkeit, primäre Nachrichten, primäre Server, Shadow-Nachrichten und Shadow-Server, gelten auch für das Sicherheitsnetz. Weitere Informationen finden Sie unter [Shadow-Redundanz](shadow-redundancy-exchange-2013-help.md).

Das primäre Sicherheitsnetz befindet sich auf dem Postfachserver, auf dem die primäre Nachricht vorhanden war, bevor sie erfolgreich vom Transportdienst verarbeitet wurde. Dies könnte bedeuten, dass die Nachricht an den Postfachtransportdienst auf dem Zielpostfachserver zugestellt wurde. Die Nachricht könnte aber auch über den Postfachserver in einem Active Directory-Standort weitergeleitet worden sein, der als Hubstandort auf dem Weg zur Ziel-DAG oder zum Active Directory-Standort vorgesehen ist. Nachdem der primäre Server die primäre Nachricht verarbeitet hat, wird die Nachricht von der aktiven Warteschlange in das primäre Sicherheitsnetz auf demselben Server verschoben.

Das Shadow-Sicherheitsnetz befindet sich auf dem Postfachserver, auf dem die Shadow-Nachricht vorhanden war. Sobald der Shadow-Server ermittelt, dass der primäre Server die primäre Nachricht erfolgreich verarbeitet hat, verschiebt der Shadow-Server die Shadow-Nachricht aus der Shadow-Warteschlange in das Shadow-Sicherheitsnetz auf demselben Server. Es liegt nahe, dass für das Vorhandensein des Shadow-Sicherheitsnetzes die Shadow-Redundanz aktiviert sein muss, und die Shadow-Redundanz ist in Exchange 2013 standardmäßig aktiviert.

Die vom Sicherheitsnetz verwendeten Parameter werden in der folgenden Tabelle beschrieben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>SafetyNetHoldTime</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>2 Tage</p></td>
<td><p>Die Zeit, für die erfolgreich verarbeitete primäre Nachrichten im primären Sicherheitsnetz und bestätigte Shadow-Nachrichten im Shadow-Sicherheitsnetz gespeichert werden.</p>
<p>Sie können diesen Wert auch in der Exchange-Verwaltungskonsole unter <strong>Nachrichtenfluss</strong> &gt; <strong>Empfangsconnectors</strong> &gt; <strong>Weitere Optionen</strong><img src="images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif" title="Weitere Optionen (Symbol)" alt="Weitere Optionen (Symbol)" /> &gt; <strong>Einstellungen für Organisationstransport</strong> &gt; <strong>Sicherheitsnetz</strong> &gt; <strong>Aufbewahrungszeit für Sicherheitsnetz</strong> angeben.</p>
<p>Nicht bestätigte Shadow-Nachrichten laufen im Shadow-Sicherheitsnetz ab, nachdem die Summe aus <em>SafetyNetHoldTime</em> und <em>MessageExpirationTimeout</em> für <strong>Set-TransportService</strong> erreicht ist.</p>
<p>Um Datenverluste bei erneuten Übermittlungen aus dem Sicherheitsnetz zu vermeiden, muss der Wert von <em>SafetyNetHoldTime</em> größer oder gleich dem Wert von <em>ReplayLagTime</em> für <strong>Set-MailboxDatabaseCopy</strong> für die verzögerte Kopie der Postfachdatenbank sein.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplayLagTime</em> für <strong>Set-MailboxDatabaseCopy</strong></p></td>
<td><p>Nicht konfiguriert</p></td>
<td><p>Der Zeitraum, den der Microsoft Exchange-Replikationsdienst abwarten soll, bevor mit der Wiedergabe von Protokolldateien begonnen wird, die in die passive Datenbankkopie kopiert wurden. Wenn Sie diesen Parameter auf einen Wert größer als 0 festlegen, wird eine verzögerte Kopie der Postfachdatenbank erstellt. Der Höchstwert ist 14 Tage.</p>
<p>Um Datenverluste bei erneuten Übermittlungen aus dem Sicherheitsnetz zu vermeiden, muss der Wert von <em>ReplayLagTime</em> kleiner oder gleich dem Wert von <em>SafetyNetHoldTime</em> für <strong>Set-TransportConfig</strong> für die verzögerte Kopie der Postfachdatenbank sein.</p></td>
</tr>
<tr class="odd">
<td><p><em>MessageExpirationTimeout</em> für <strong>Set-TransportService</strong></p></td>
<td><p>2 Tage</p></td>
<td><p>Gibt an, wie lange eine Nachricht in einer Warteschlange verbleiben kann, bevor sie abläuft.</p></td>
</tr>
<tr class="even">
<td><p><em>ShadowRedundancyEnabled</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p><code>$true</code></p></td>
<td><ul>
<li><p><code>$true</code> aktiviert die Shadow-Redundanz auf allen Transportservern in der Organisation.</p></li>
<li><p><code>$false</code> deaktiviert die Shadow-Redundanz auf allen Transportservern in der Organisation.</p></li>
</ul>
<p>Für ein redundantes Sicherheitsnetz muss Shadow-Redundanz aktiviert sein.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz

Erneute Übermittlungen von Nachrichten aus dem Sicherheitsnetz werden von der Active Manager-Komponente des Microsoft Exchange-Replikationsdiensts ausgelöst, der DAGs und Postfachdatenbankkopien verwaltet. Zur erneuten Übermittlung von Nachrichten aus dem Sicherheitsnetz sind keine manuellen Aktionen erforderlich. Weitere Informationen zu Active Manager finden Sie in [Active Manager](active-manager-exchange-2013-help.md).

Es gibt zwei grundlegende Szenarien für die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz:

  - Nach dem automatischen oder manuellen Failover einer Postfachdatenbank in einer DAG.

  - Nachdem Sie eine verzögerte Kopie einer Postfachdatenbank aktivieren.

Eine *verzögerte Postfachdatenbankkopie* oder *verzögerte Kopie* ist eine passive Kopie einer Postfachdatenbank, bei der Aktualisierungen der Datenbank absichtlich verzögert werden, um einen Schutz vor logischer Beschädigung der Datenbank zu bieten. Weitere Informationen finden Sie unter [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

Der einzige signifikante Unterschied zwischen den beiden Szenarien ist der Zeitraum, für den Nachrichten aus dem Sicherheitsnetz erneut übermittelt werden. Bei einem Failover in einer DAG ist die neue aktive Kopie üblicherweise wenige Minuten bis einige Stunden älter als die alte aktive Kopie. Eine verzögerte Kopie einer Postfachdatenbank ist meist mehrere Tage älter als die alte aktive Kopie.

Bei einer verzögerten Kopie ist die wichtigste Anforderung für eine erfolgreiche erneute Übermittlung aus dem Sicherheitsnetz, dass die Dauer, für die Nachrichten im Sicherheitsnetz gespeichert sind, größer oder gleich der Verzögerung der verzögerten Kopie der Postfachdatenbank sein muss. Anders ausgedrückt muss der Wert von *SafetyNetHoldTime* für **Set-TransportConfig** größer oder gleich dem Wert von *ReplayLagTime* für **Set-MailboxDatabaseCopy** für die verzögerte Kopie sein.

Zurück zum Seitenanfang

## Erneute Übermittlung von Nachrichten aus dem Shadow-Sicherheitsnetz

Wie die erneute Übermittlung von Nachrichten aus dem primären Sicherheitsnetz ist auch die erneute Übermittlung von Nachrichten aus dem Shadow-Sicherheitsnetz vollständig automatisiert. Manuelle Eingriffe sind nicht erforderlich.

Wenn Active Manager die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz für einen bestimmten Zeitraum anfordert, wird die Anforderung an den Transportdienst auf den Postfachservern geleitet, auf denen das primäre Sicherheitsnetz Nachrichtenkopien für den erforderlichen Zeitraum aufbewahrt. In großen Exchange-Organisationen ist es wahrscheinlich, dass die erforderlichen Nachrichten auf mehreren Postfachservern vorhanden sind, insbesondere bei einem langen Zeitraum.

Ohne eine Optimierung könnte die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz zu einer großen Anzahl von doppelten Zustellungen führen. Innerhalb der Exchange-Organisation sind doppelte Zustellungen kein Problem, da durch die Erkennung doppelter Nachrichten verhindert wird, dass die Postfachbenutzer doppelte Kopien einer Nachricht sehen. Die doppelte Zustellung von Nachrichten an Empfänger außerhalb der Exchange-Organisation führt jedoch zu doppelten Kopien von Nachrichten. Erfreulicherweise wurde die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz in Exchange 2013 optimiert, um die doppelte Zustellung von Nachrichten zu reduzieren.

Wenn das primäre Sicherheitsnetz anfangs nicht reagiert oder während der erneuten Übermittlung von Nachrichten nicht mehr reagiert, versucht Active Manager für 12 Stunden, einen Kontakt herzustellen. Nach 12 Stunden wird eine Nachricht an den Transportdienst auf allen Postfachservern innerhalb der Grenzen für hohe Transportverfügbarkeit gesendet, mit der die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz für den erforderlichen Zeitraum und die erforderliche Postfachdatenbank angefordert wird. Wenn ein Shadow-Sicherheitsnetz reagiert, werden die Nachrichten für die erforderliche Postfachdatenbank nur für den erforderlichen Zeitraum erneut übermittelt.

Es gibt einige wichtige Überlegungen für die Shadow-Nachrichten, die im Shadow-Sicherheitsnetz gespeichert werden:

  - Im Shadow-Sicherheitsnetz gibt es keine Angabe dazu, wohin der primäre Server die primäre Nachricht übertragen hat.

  - Die Shadow-Nachrichten im Shadow-Sicherheitsnetz enthalten nur die ursprünglichen Empfänger im Nachrichten-Envelope, nicht die tatsächlichen Empfänger, an die die primäre Nachricht zugestellt wurde. Der Empfänger im Nachrichten-Envelope kann beispielsweise eine Verteilergruppe sein, die erweitert werden muss.

  - Die Nachrichten im Shadow-Sicherheitsnetz enthalten keine Aktualisierungen der Nachrichten, die nach der Verarbeitung der Nachrichten auf dem primären Server vorgenommen wurden. Beispiele: Nachrichtencodierung oder Inhaltskonvertierung.

Eine aus dem Shadow-Sicherheitsnetz erneut übermittelte Shadow-Nachricht muss durch den Transportdienst auf dem Postfachserver vollständig kategorisiert und verarbeitet werden. Die erneute Übermittlung einer großen Anzahl von Shadow-Nachrichten aus dem Shadow-Sicherheitsnetz kann die Ressourcen des Postfachservers stark beanspruchen. Erfreulicherweise wurde auch die erneute Übermittlung von Shadow-Nachrichten aus dem Shadow-Sicherheitsnetz optimiert, sodass nur Nachrichten im Shadow-Sicherheitsnetz für den angeforderten Zeitraum und die angeforderte Postfachdatenbank erneut übermittelt werden.

Im folgenden Szenario werden die Interaktionen des primären Sicherheitsnetzes und des Shadow-Sicherheitsnetzes während der erneuten Übermittlung von Nachrichten beschrieben.

1.  Active Manager fordert die erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz für eine Postfachdatenbank für den Zeitraum von 05:00:00 bis 9:00 Uhr an. Der Postfachserver mit dem primären Sicherheitsnetz ist jedoch aufgrund eines Hardwareausfalls abgestürzt. Active Manager versucht für 12 Stunden wiederholt, Kontakt mit dem primären Sicherheitsnetz aufzunehmen.

2.  Nach 12 Stunden sendet Active Manger eine Nachricht an den Transportdienst auf allen Postfachservern innerhalb der Grenzen für hohe Transportverfügbarkeit, um ein anderes Sicherheitsnetz zu finden, dass die Nachrichten für die Zielpostfachdatenbank für den Zeitraum von 5:00 bis 9:00 Uhr enthält. Die Reaktion des Shadow-Sicherheitsnetzes ist das erneute Senden von Nachrichten für die Postfachdatenbank für den Zeitraum von 5:00 bis 9:00 Uhr.

Zu einer interessanten Interaktion kommt es, wenn das primäre Sicherheitsnetz im angeforderten Zeitraum für die erneute Übermittlung teilweise offline war. Dies ist im folgenden Szenario beschrieben.

1.  Die Warteschlangendatenbank auf dem Postfachserver mit dem primären Sicherheitsnetz ist beschädigt, und eine neue Warteschlangendatenbank wird um 7:00 Uhr erstellt. Alle primären Nachrichten, die im primären Sicherheitsnetz von 1:00 Uhr bis 7:00 Uhr gespeichert wurden, sind verloren, aber der Server kann Kopien erfolgreich an das Sicherheitsnetz zugestellter Nachrichten ab 7:00 Uhr speichern.

2.  Active Manager fordert eine erneute Übermittlung von Nachrichten aus dem Sicherheitsnetz für eine Postfachdatenbank für den Zeitraum von 1:00 bis 9:00 Uhr an.

3.  Das primäre Sicherheitsnetz übermittelt die Nachrichten für den Zeitraum von 7:00 bis 9:00 Uhr erneut.

4.  Das primäre Sicherheitsnetz sendet eine Nachricht an den Transportdienst auf allen Postfachservern innerhalb der Grenzen für hohe Transportverfügbarkeit, um andere Sicherheitsnetze zu finden, die Nachrichten für die Zielpostfachdatenbank für den Zeitraum von 1:00 bis 7:00 Uhr enthalten. Für diesen Zeitraum gibt es im primären Sicherheitsnetz keine Nachrichten. Das Shadow-Sicherheitsnetz generiert im Namen des primären Sicherheitsnetzes eine zweite Anforderung zur erneuten Übermittlung, um die Shadow-Nachrichten aus der Zielpostfachdatenbank für den Zeitraum von 1:00 bis 7:00 Uhr erneut zu übermitteln.

Sie müssen einige weitere Probleme bedenken, wenn Nachrichten aus dem Sicherheitsnetz erneut übermittelt werden.

1.  Alle Benachrichtigungen über den Zustellungsstatus (Delivery Status Notifications, DSNs) und Unzustellbarkeitsberichte (Non-Delivery Reports, NDRs) werden für erneute Übermittlungen aus dem Sicherheitsnetz unterdrückt. Wenn beispielsweise die primäre Nachricht zu einem NDR geführt hat, wird der NDR der erneut übermittelten Nachricht nicht zugestellt.

2.  Aus einer Verteilergruppe entfernte Benutzer erhalten eine erneut übermittelte Nachricht möglicherweise nicht, wenn das Shadow-Sicherheitsnetz die Nachricht erneut übermittelt. Ein Beispiel: Eine Nachricht wird an eine Gruppe gesendet, die Benutzer A und Benutzer B enthält. Beide Empfänger erhalten die Nachricht. Benutzer B wird anschließend aus der Gruppe entfernt. Später wird vom primären Sicherheitsnetz eine erneute Übermittlung für die Postfachdatenbank angefordert, in der sich das Postfach von Benutzer B befindet. Das primäre Sicherheitsnetz ist jedoch für mehr als 12 Stunden nicht verfügbar, daher antwortet der Server mit dem Shadow-Sicherheitsnetz und übermittelt die betreffende Nachricht erneut. Während der erneuten Übermittlung mit der erweiterten Verteilergruppe ist Benutzer B kein Mitglied der Gruppe und erhält keine Kopie der erneut übermittelten Nachricht.

3.  Einer Verteilergruppe neu hinzugefügte Benutzer erhalten möglicherweise eine alte erneut übermittelte Nachricht, wenn das Shadow-Sicherheitsnetz die Nachricht erneut übermittelt. Ein Beispiel: Eine Nachricht wird an eine Gruppe gesendet, die Benutzer A und Benutzer B enthält. Beide Empfänger erhalten die Nachricht. Benutzer C wird anschließend der Gruppe hinzugefügt. Später wird vom primären Sicherheitsnetz eine erneute Übermittlung für die Postfachdatenbank angefordert, in der sich das Postfach von Benutzer C befindet. Der Server mit dem primären Sicherheitsnetz ist jedoch für mehr als 12 Stunden nicht verfügbar, daher antwortet der Server mit dem Shadow-Sicherheitsnetz und übermittelt die betreffende Nachricht erneut. Während der erneuten Übermittlung mit der erweiterten Verteilergruppe ist Benutzer C ein Mitglied der Gruppe und erhält eine Kopie der erneut übermittelten Nachricht.

Zurück zum Seitenanfang

