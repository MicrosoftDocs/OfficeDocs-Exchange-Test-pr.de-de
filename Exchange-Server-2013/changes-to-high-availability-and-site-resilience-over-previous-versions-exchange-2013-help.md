---
title: 'Änderungen bei hoher Verfügbarkeit und Ausfallsicherheit im Vergleich zu früheren Versionen: Exchange 2013 Help'
TOCTitle: Änderungen bei hoher Verfügbarkeit und Ausfallsicherheit im Vergleich zu früheren Versionen
ms:assetid: de53c00b-091c-4a31-aacc-1bd40c756ce2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn789066(v=EXCHG.150)
ms:contentKeyID: 62519853
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Änderungen bei hoher Verfügbarkeit und Ausfallsicherheit im Vergleich zu früheren Versionen

 

_**Gilt für:**Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Exchange 2013 verwendet DAGs, Postfachdatenbankkopien und weitere Funktionen, wie z. B. die Wiederherstellung einzelner Elemente, Aufbewahrungsrichtlinien und verzögerte Datenbankkopien, um Hochverfügbarkeit, Ausfallsicherheit für Standorte und einen systemeigenen Exchange-Datenschutz bereitzustellen. Sowohl die Hochverfügbarkeitsplattform als auch der Exchange-Informationsspeicher und das ESE-Modul (Extensible Storage Engine) wurden erweitert und bieten mehr Verfügbarkeit, eine vereinfachte Verwaltung und die Möglichkeit zur Kosteneinsparung. Diese Verbesserungen umfassen:

  - **Verringerung der IOPS gegenüber Exchange 2010**   Dies ermöglicht eine effizientere Nutzung großer Datenträger in Bezug auf Kapazität und IOPS.

  - **Verwaltete Verfügbarkeit**   Bei der verwalteten Verfügbarkeit werden eine interne Überwachung und wiederherstellungsorientierte Funktionen eng miteinander verzahnt, um Ausfälle zu vermeiden, Dienste proaktiv wiederherzustellen, ein Serverfailover automatisch einzuleiten oder den Administrator zu benachrichtigen, damit dieser entsprechende Maßnahmen ergreift. Der Schwerpunkt liegt eher auf der Überwachung und Verbesserung der Benutzerfreundlichkeit als darauf, nur den Betrieb von Servern und Komponenten sicherzustellen, damit die Dienste ohne Unterbrechung verfügbar sind.

  - **Verwalteter Speicher**   Als verwalteter Speicher werden die neu gestalteten Informationsspeicherprozesse in Exchange 2013 bezeichnet. Der neue verwaltete Speicher ist in C\# geschrieben und eng in den Microsoft Exchange-Replikationsdienst (MSExchangeRepl.exe) integriert, um eine verbesserte Resilienz und damit eine höhere Verfügbarkeit bereitzustellen.

  - **Unterstützung für mehrere Datenbanken pro Datenträger** Exchange 2013 bietet Verbesserungen, die Ihnen die Unterstützung mehrerer Datenbanken (eine Kombination aus aktiven und passiven Kopien) auf demselben Datenträger ermöglichen, wodurch größere Datenträger in Bezug auf Kapazität und E/A pro Sekunde effizienter genutzt werden können.

  - **AutoReseed**   Automatisches erneutes Seeding ermöglicht das schnelle Wiederherstellen von Datenbankredundanz nach einem Datenträgerausfall. Wenn ein Datenträger ausfällt, wird die auf diesem Datenträger gespeicherte Datenbankkopie aus der aktiven Datenbankkopie auf einen Ersatzdatenträger auf demselben Server kopiert. Wenn mehrere Datenbankkopien auf dem fehlerhaften Datenträger gespeichert waren, kann für diese automatisch ein erneutes Seeding auf einem Ersatzdatenträger ausgeführt werden. Damit kann das erneute Seeding schneller ausgeführt werden, da die aktiven Datenbanken sich wahrscheinlich auf mehreren Servern befinden und die Daten parallel kopiert werden können.

  - **Automatische Wiederherstellung nach Speicherfehlern**   Eine Weiterentwicklung der in Exchange 2010 eingeführten Funktion, die es dem System erlaubt, nach Ausfällen mit Auswirkung auf Resilienz oder Redundanz eine automatische Wiederherstellung durchzuführen. Zusätzlich zur Fehlerprüfung von Exchange 2010 bietet Exchange 2013 weitere Wiederherstellungsfunktionen bei langen E/A-Zeiten, übermäßige Speicherbelegungen durch "MSExchangeRepl.exe" und für gravierende Fälle, bei denen das System sich in einem so schlechten Zustand befindet, dass keine Threads geplant werden können.

  - **Verbesserungen in Bezug auf verzögerte Kopien**   Verzögerte Kopien können sich mithilfe der automatischen Protokollwiedergabe jetzt bis zu einem gewissen Grad selbst verwalten. Verzögerte Kopien geben in verschiedenen Situationen automatisch Protokolldateien wieder, wie zum Beispiel beim Seitenpatching und in Szenarien mit wenig Speicherplatz. Wenn das System ermittelt, dass für eine verzögerte Kopie ein Seitenpatching erforderlich ist, werden die Protokolle automatisch in die verzögerte Kopie wiedergegeben, um das Seitenpatching auszuführen. Verzögerte Kopien rufen die automatische Wiedergabefunktion auch auf, wenn ein Schwellenwert bezüglich zu wenig Speicherplatz erreicht wird und wenn die verzögerte Kopie während eines bestimmten Zeitraums die einzige verfügbare Kopie ist. Darüber hinaus nutzen verzögerte Kopien die Funktion "Sicherheitsnetz", mit der die Wiederherstellung oder Aktivierung wesentlich vereinfacht wird.

  - **Verbesserte Warnung zu einzelnen Kopien**   Die in Exchange 2010 eingeführte Warnung zu einzelnen Kopien wird nicht länger als separat geplantes Skript zur Verfügung gestellt. Es wurde in die Systemkomponenten für verwaltete Verfügbarkeit integriert und ist jetzt eine systemeigene Funktion von Exchange.

  - **Automatische Konfiguration von DAG-Netzwerken**   DAG-Netzwerke können basierend auf Konfigurationseinstellungen automatisch vom System konfiguriert werden. DAGs bieten nicht nur manuelle Konfigurationsoptionen, sondern können auch zwischen MAPI- und Replikationsnetzwerken unterscheiden und DAG-Netzwerke automatisch konfigurieren.

## Verringerung der IOPS gegenüber Exchange 2010

In Exchange 2010 weisen passive Datenbankkopien eine sehr geringe Prüfpunkttiefe auf, die für ein schnelles Failover erforderlich ist. Zusätzlich führen die passiven Kopien ein aggressives Preread von Daten durch, um einer Prüfpunkttiefe von 5 MB nachzukommen. Als Ergebnis einer geringen Prüfpunkttiefe und der Durchführung von aggressiven Prereadvorgängen entsprachen die IOPS für eine passive Datenbankkopie in Exchange 2010 den IOPS einer aktiven Kopie.

In Exchange 2013 ist das System in der Lage, ein schnelleres Failover durchzuführen, während gleichzeitig eine hohe Prüfpunkttiefe für die passive Kopie verwendet wird (100 MB). Aufgrund der 100-MB-Prüfpunkttiefe für passive Kopien sind aggressive Prereadvorgänge nicht länger nötig. Als Ergebnis der höheren Prüfpunkttiefe und der Verringerung aggressiver Prereadvorgänge weist eine passive Kopie in Exchange 2013 gegenüber einer aktiven Kopie etwa 50 Prozent weniger IOPS auf.

Die höhere Prüfpunkttiefe für passive Kopien hat weitere Änderungen zur Folge. Bei einem Failover in Exchange 2010 wird der Datenbankcache geleert, wenn die Datenbank von einer passiven Kopie in eine aktive Kopie konvertiert wird. In Exchange 2013 wurde die ESE-Protokollierung umgeschrieben, sodass der Cache beim Übergang von einer passiven auf eine aktive Kopie erhalten bleibt. Da ESE den Cache nicht leeren muss, kann das Failover schneller ausgeführt werden.

Eine weitere Änderung bezieht sich auf die Hintergrundwartung für Datenbanken. Bei der Hintergrundwartung für Datenbanken werden nun 1-2 MB pro Sekunde pro Kopie bearbeitet.

Als Ergebnis dieser Änderungen bietet Exchange 2013 gegenüber Exchange 2010 eine erhebliche Verringerung der IOPS.

## Verwaltete Verfügbarkeit

Die verwaltete Verfügbarkeit kombiniert vordefinierte Funktionen für die aktive Überwachung mit der Hochverfügbarkeitsplattform von Exchange 2013. Mit der verwalteten Verfügbarkeit kann das System basierend auf der Dienstintegrität entscheiden, wann ein Datenbankfailover durchgeführt werden sollte. Die verwaltete Verfügbarkeit ist eine interne Infrastruktur, die in den Clientzugriffs- und Postfachserverrollen von Exchange 2013 bereitgestellt wird. Sie umfasst drei asynchrone Hauptkomponenten, die kontinuierlich arbeiten. Die erste Komponente ist das Prüfmodul, das Messungen auf dem Server vornimmt und Daten sammelt. Die Ergebnisse dieser Messungen fließen in die zweite Komponente ein, den Monitor. Der Monitor umfasst die vollständige, vom System verwendete Geschäftslogik zur Definition des fehlerfreien Zustands von gesammelten Daten. Ähnlich wie bei einem Modul zur Mustererkennung achtet der Monitor auf die zahlreichen verschiedenen Muster aller gesammelten Messungen. Anschließend wird entschieden, ob eine Komponente als fehlerfrei betrachtet wird. Schließlich gibt es das Respondermodul, das für Wiederherstellungsaktionen verantwortlich ist. Wenn eine Komponente fehlerhaft ist, besteht die erste Aktion in dem Versuch, diese Komponente wiederherzustellen. Dies kann mehrstufige Wiederherstellungsaktionen umfassen. Der erste Versuch kann z. B. darin bestehen, dass der Anwendungspool neu gestartet wird, während der zweite Versuch den Neustart des Diensts und der dritte Versuch den Neustart des Servers umfasst. Ein nachfolgender Versuch könnte darin bestehen, den Server offline zu nehmen, damit kein Datenverkehr mehr angenommen wird. Wenn die Wiederherstellungsaktionen keinen Erfolg zeigen, eskaliert das System das Problem per Ereignisprotokollbenachrichtigung an einen Benutzer.

Die verwaltete Verfügbarkeit wird in Form von zwei Diensten implementiert:

  - **Exchange-Integritätsdienst (MSExchangeHMHost.exe)**   Dies ist ein Controllerprozess, der zur Verwaltung von Arbeitsprozessen verwendet wird. Mit diesem Prozess wird der Arbeitsprozess nach Bedarf erstellt, ausgeführt, gestartet und angehalten. Dieser Prozess wird auch zur Wiederherstellung des Arbeitsprozesses verwendet, falls dieser ausfällt. So soll verhindert werden, dass der Arbeitsprozess zu einer einzelnen Fehlerquelle wird.

  - **Arbeitsprozess des Exchange-Integritätsdiensts (MSExchangeHMWorker.exe)**   Dies ist der Arbeitsprozess, der für die Ausführung der Laufzeittasks zuständig ist.

Bei der verwalteten Verfügbarkeit wird ein beständiger Speicher verwendet, um die zugehörigen Funktionen auszuführen:

  - Zum Initialisieren der Arbeitselementdefinitionen während des Starts des Arbeitsprozesses werden XML-Konfigurationsdateien verwendet.

  - Die Registrierung wird zum Speichern von Laufzeitdaten wie z. B. Lesezeichen verwendet.

  - Die Crimson-Kanal-Ereignisprotokollinfrastruktur wird zum Speichern der Arbeitselementergebnisse verwendet.

Weitere Informationen zur verwalteten Verfügbarkeit finden Sie unter [Verwaltete Verfügbarkeit](managed-availability-exchange-2013-help.md).

## Verwalteter Speicher

Alle vorherigen Exchange Server-Versionen, von Exchange Server 4.0 bis Exchange Server 2010, haben die Ausführung einer einzelnen Instanz des Prozesses des Microsoft Exchange-Informationsspeichers (Store.exe) in der Serverrolle "Mailbox" unterstützt. Diese einzelne Speicherinstanz hostet alle Datenbanken auf diesem Server: aktive, passive, verzögerte und wiederhergestellte. In den bisherigen Exchange-Architekturen gibt es, wenn überhaupt, nur eine kleine Isolation zwischen den verschiedenen auf einem Mailbox-Server gehosteten Datenbanken. Ein Problem mit einer einzelnen Postfachdatenbank hat das Potenzial, sich auf alle anderen Datenbanken auszuwirken, und Ausfälle aufgrund der Beschädigung einer Datenbank können den Dienst für alle Benutzer, deren Datenbanken auf diesem Server gehostet werden, beeinträchtigen.

Eine weitere Herausforderung bei einer einzelnen Speicherinstanz von Exchange ist, dass Extensible Storage Engine (ESE) für 8 bis 12 Prozessorkerne angemessen skaliert ist, aber darüber hinaus Probleme mit prozessorübergreifender Kommunikation und Cache-Synchronisierung auftreten können. Angesichts der heutzutage verfügbaren viel größeren Server mit mehr als 16 Kernen würde dies die administrative Herausforderung bedeuten, die Affinität der 8 bis 12 Kerne für ESE zu verwalten und die anderen Kerne für Prozesse außerhalb des Speichers zu verwenden (z. B. Assistenten, Search Foundation, verwaltete Verfügbarkeit usw.). Außerdem waren die Aufwärtsskalierungsoptionen für den Informationsspeicherprozess in der bisherigen Architektur beschränkt.

Der Prozess Store.exe hat im Laufe der Jahre, in denen sich Exchange Server selbst entwickelt hat, auch eine bemerkenswerte Entwicklung durchgemacht, aber als einzelner Prozess ist seine Skalierbarkeit begrenzt, und er stellt auch eine einzelne Fehlerquelle dar. Aufgrund dieser Begrenzungen ist Store.exe in Exchange 2013 nicht mehr vorhanden und wird durch den verwalteten Speicher ersetzt.

Weitere Informationen finden Sie unter [Verwalteter Speicher](managed-store-exchange-2013-help.md).

## Mehrere Datenbanken pro Volume

Obwohl die Speicherverbesserungen in Exchange 2013 primär auf JBOD-Konfigurationen (Just a Bunch Of Disks) ausgerichtet sind, stehen sie für alle unterstützten Speicherkonfigurationen zur Verfügung. Eine dieser Verbesserungen ist die Fähigkeit, mehrere Datenbanken auf demselben Volume zu hosten. Dadurch ergibt sich eine bessere Unterstützung für große Datenträger in Exchange. Diese Verbesserungen führen zu einer sehr viel effizienteren Verwendung großer Datenträger in Bezug auf Kapazität, IOPS und Zeit für das erneute Seeding, und sie tragen dazu bei, den Herausforderungen bei der Ausführung in einer JBOD-Speicherkonfiguration zu begegnen:

  - Datenbankgrößen müssen verwaltbar sein.

  - Das erneute Seeding muss schnell und zuverlässig erfolgen.

  - Die Speicherkapazität nimmt zu, die IOPS jedoch nicht.

  - Datenträger mit passiven Datenbankkopien sind bezogen auf die IOPS nicht ausgelastet.

  - Verzögerte Kopien haben asymmetrische Speicheranforderungen.

  - Bei der Wiederherstellung nach Speicherplatzproblemen besteht nur geringe Flexibilität.

Der Trend hin zu steigenden Speicherkapazitäten setzt sich fort: Bald werden Laufwerke mit 8 TB zur Verfügung stehen. Bei Verwendung von 8-TB-Laufwerken im Einklang mit den empfohlenen Richtlinien zur maximalen Exchange-Datenbankgröße (2 TB) würden mehr als 5 TB an Speicherplatz vergeudet. Eine Lösung wäre die Vergrößerung der Datenbanken. Dadurch würde jedoch die Verwaltbarkeit eingeschränkt, da sich die Ausführungszeiten für das erneute Seeding erheblich verlängern würden – bis hin zur Nichtverwaltbarkeit bei Seedingvorgängen. Auch die Zuverlässigkeit beim Kopieren derartiger Datenmengen über das Netzwerk würde beeinträchtigt.

Darüber hinaus ist beim Exchange 2010-Modell der Datenträger, auf dem eine passive Kopie gespeichert wird, in Bezug auf die IOPS nicht ausgelastet. Im Falle einer verzögerten passiven Kopie ist der Datenträger nicht nur in Bezug auf die IOPS unterlastet, sondern auch in Bezug auf die Datenträger zum Speichern der aktiven und nicht verzögerten passiven Kopien in seiner Größe asymmetrisch.

Als Ergebnis der stetigen Weiterentwicklung wurde Exchange 2013 so optimiert, dass große Datenträger (8 TB) in einer JBOD-Konfiguration effizienter genutzt werden können. In Exchange 2013 können bei mehreren Datenbanken pro Datenträger gleich große Datenträger mehrere Datenbankkopien (verzögerte Kopien eingeschlossen) speichern. Das Ziel besteht darin, die Verteilung der Benutzer auf die Anzahl von vorhandenen Volumes zu verbessern und so ein symmetrisches Design zu erhalten, bei dem während des normalen Betriebs jedes DAG-Mitglied eine Kombination aus aktiven, passiven und (optional) verzögerten Kopien auf demselben Volume hostet.

Die nachstehende Abbildung zeigt eine Beispielkonfiguration mit mehreren Datenbanken pro Volume.

**Konfiguration, die mehrere Datenbanken pro Volume verwendet**

![Mehrere Datenbanken pro Volume](images/Dn789066.c5e7d6c8-3e77-4f72-a873-5e9aaded9aa3(EXCHG.150).gif "Mehrere Datenbanken pro Volume")

Die obige Konfiguration gewährleistet ein symmetrisches Design. Alle vier Server verfügen über dieselben vier Datenbanken, jeweils gehostet auf einem einzelnen Datenträger pro Server. Der entscheidende Punkt ist, dass die Anzahl von Kopien jeder Datenbank der Anzahl von Datenbankkopien pro Datenträger entsprechen sollte. Im obigen Beispiel gibt es vier Kopien jeder Datenbank: eine aktive Kopie, zwei passive Kopien und eine verzögerte Kopie. Da vier Kopien jeder Datenbank vorliegen, umfasst die ordnungsgemäße Konfiguration vier Kopien pro Volume. Zusätzlich wird die Aktivierungseinstellung so konfiguriert, dass ein Ausgleich über die DAG und die einzelnen Server gewährleistet ist. Wenn beispielsweise die Aktivierungseinstellung für die aktive Kopie den Wert 1 aufweist, erhält die erste passive Kopie eine Aktivierungseinstellung mit dem Wert 2, die zweite passive Kopie den Wert 3, und die verzögerte Kopie den Wert 4.

Zusätzlich zu einer besseren Verteilung der Benutzer auf die vorhandenen Volumes liegt ein weiterer Vorteil der Verwendung mehrerer Datenbanken pro Datenträger darin, dass die Zeit zur Wiederherstellung des Datenschutzes nach Fehlern verringert wird, die ein erneutes Seeding erforderlich machen (z. B. Datenträgerausfälle).

Je größer eine Datenbank ist, desto mehr Zeit wird für das erneute Seeding der Datenbank benötigt. Beispielsweise kann das erneute Seeding einer 2-TB-Datenbank 23 Stunden in Anspruch nehmen, bei einer 8-TB-Datenbank kann das erneute Seeding 93 Stunden dauern (beinahe 4 Tage). Beide Seedingvorgänge würden mit etwa 20 MB pro Sekunde erfolgen. Dies bedeutet im Allgemeinen, dass ein erneutes Seeding für eine sehr große Datenbank nicht innerhalb einer angemessenen Zeit durchgeführt werden kann.

Im Fall eines Szenarios mit einer einzelnen Datenbankkopie pro Datenträger ist der Seedingvorgang quellgebunden, da der Seedingvorgang des Datenträgers über eine einzelne Quelle erfolgt. Durch die Aufteilung des Volumes in mehrere Datenbankkopien und durch die Speicherung der aktiven Kopie der passiven Datenbanken auf einem bestimmten Volume auf separaten DAG-Mitgliedern ist das System beim erneuten Seeding des Datenträgers nicht an eine einzelne Quelle gebunden. Wenn ein fehlerhafter Datenträger ausgetauscht wird, kann das erneute Seeding über mehrere Quellen erfolgen. Auf diese Weise kann das System das erneute Seeding und die Wiederherstellung des Datenschutzes für diese Datenbanken innerhalb einer deutlich kürzeren Zeit abschließen.

Bei der Verwendung mehrerer Datenbanken pro Volume sollten die folgenden bewährten Methoden und Anforderungen befolgt werden:

  - Eine einzelne logische Datenträgerpartition pro physischem Datenträger muss verwendet werden. Erstellen Sie nicht mehrere Partitionen auf dem Datenträger. Jede Datenbankkopie und die zugehörigen Begleitdateien (wie z. B. Transaktionsprotokolle und Inhaltsindex) sollten in einem eindeutigen Verzeichnis auf der einzelnen Partition gehostet werden.

  - Die Anzahl von Datenbankkopien, die pro Volume konfiguriert werden, sollte der Anzahl an Kopien jeder Datenbank entsprechen. Wenn Sie beispielsweise über vier Kopien Ihrer Datenbanken verfügen, sollten Sie vier Datenbankkopien pro Volume verwenden.

  - Datenbankkopien sollten dieselben Nachbarelemente aufweisen. (Sie sollten sich beispielsweise alle auf dem gleichen Datenträger auf jedem jeweiligen Server befinden.)

  - Die Aktivierungseinstellungen in der DAG sollten abgeglichen werden, sodass jede Datenbankkopie auf einem bestimmten Datenträger einen eindeutigen Wert für die Aktivierungseinstellung aufweist.

## AutoReseed

Das automatische erneute Seeding, auch AutoReseed genannt, ist ein Feature zur Ersetzung der Aufgaben, die – als Reaktion auf einen Datenträgerfehler, eine Datenbankbeschädigung oder andere Probleme, die ein erneutes Seeding einer Datenbankkopie erforderlich machen – normalerweise von einem Administrator ausgeführt werden. Die AutoReseed-Funktion ist für die automatische Wiederherstellung der Datenbankredundanz nach einem Datenträgerfehler konzipiert. Hierbei wird auf Ersatzdatenträger zurückgegriffen, die im System bereitgestellt wurden.

Weitere Informationen finden Sie unter [AutoReseed](autoreseed-exchange-2013-help.md). Ausführliche Schritte zur Konfiguration von AutoReseed finden Sie unter [Konfigurieren von AutoReseed für eine Database Availability Group](configure-autoreseed-for-a-database-availability-group-exchange-2013-help.md).

## Automatische Wiederherstellung nach Speicherfehlern

Die automatische Wiederherstellung nach Speicherfehlern ist eine Weiterentwicklung der in Exchange 2010 eingeführten Funktion, die es dem System erlaubt, nach Ausfällen mit Auswirkung auf Resilienz oder Redundanz eine automatische Wiederherstellung durchzuführen. Zusätzlich zur Fehlerprüfung von Exchange 2010 bietet Exchange 2013 weitere Wiederherstellungsfunktionen bei langen E/A-Zeiten, übermäßigen Speicherbelegungen durch den Microsoft Exchange-Replikationsdienst (MSExchangeRepl.exe) und für gravierende Fälle, in denen keine Threads geplant werden können.

Selbst in JBOD-Umgebungen können Probleme mit Speicherarraycontrollern auftreten, beispielsweise können diese abstürzen oder nicht mehr reagieren. Exchange 2010 umfasste eine Erkennung von nicht mehr reagierenden E/A-Vorgängen sowie Wiederherstellungsfunktionen zur Verbesserung der Ausfallsicherheit. Diese Funktionen werden in der folgenden Tabelle aufgeführt.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Prüfung</th>
<th>Aktion</th>
<th>Schwellenwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Erkennung nicht reagierender E/A-Vorgänge für ESE-Datenbank</p></td>
<td><p>ESE-Prüfungen für ausstehende E/A-Vorgänge</p></td>
<td><p>Generiert ein Fehlerelement im Crimson-Kanal, um den Server neu zu starten</p></td>
<td><p>240 Sekunden</p></td>
</tr>
<tr class="even">
<td><p>Taktsignal für Fehlerelement im Kanal</p></td>
<td><p>Stellt sicher, dass Fehlerelemente in den Crimson-Kanal geschrieben und aus diesem gelesen werden können</p></td>
<td><p>Der Replikationsdienst sendet ein Taktsignal an den Crimson-Kanal und startet den Server bei Fehlern neu</p></td>
<td><p>30 Sekunden</p></td>
</tr>
<tr class="odd">
<td><p>Taktsignal für Systemdatenträger</p></td>
<td><p>Überprüft den Status des Systemdatenträgers auf dem Server</p></td>
<td><p>In regelmäßigen Abständen werden ungepufferte E/A an den Systemdatenträger gesendet, und der Server wird bei Auftreten eines Takttimeouts neu gestartet</p></td>
<td><p>120 Sekunden</p></td>
</tr>
</tbody>
</table>


Exchange 2013 verbessert die Ausfallsicherheit für Server und Speicher, indem neue Funktionen für weitere schwerwiegende Bedingungen bereitgestellt werden. Diese Bedingungen und Verhaltensweisen werden in der folgenden Tabelle beschrieben.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Prüfung</th>
<th>Aktion</th>
<th>Schwellenwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ungültiger Systemstatus</p></td>
<td><p>Keine Threadplanung möglich, nicht verwaltete Threads eingeschlossen</p></td>
<td><p>Der Server wird neu gestartet</p></td>
<td><p>302 Sekunden</p></td>
</tr>
<tr class="even">
<td><p>Lange E/A-Zeiten</p></td>
<td><p>Latenzmessungen für E/A-Vorgänge</p></td>
<td><p>Der Server wird neu gestartet</p></td>
<td><p>41 Sekunden</p></td>
</tr>
<tr class="odd">
<td><p>Speicherbelegung durch Replikationsdienst</p></td>
<td><p>Messung des Arbeitssatzes von &quot;MSExchangeRepl.exe&quot;</p></td>
<td><ol>
<li><p>Protokollierung von Ereignis 4395 im Crimson-Kanal, mit einer Anforderung zur Dienstbeendigung</p></li>
<li><p>Einleiten der Beendigung von &quot;MSExchangeRepl.exe&quot;</p></li>
<li><p>Serverneustart, wenn Dienst nicht erfolgreich beendet werden kann</p></li>
</ol></td>
<td><p>4 Gigabyte (GB)</p></td>
</tr>
<tr class="even">
<td><p>Systemereignis 129 (Bus-Reset)</p></td>
<td><p>Im Systemereignisprotokoll nach Ereignis 129 suchen</p></td>
<td><p>Der Server wird neu gestartet</p></td>
<td><p>Wenn das Ereignis auftritt</p></td>
</tr>
<tr class="odd">
<td><p>Clusterdatenbank reagiert nicht mehr</p></td>
<td><p>Globale Update-Manager-Updates werden blockiert</p></td>
<td><p>Der Server wird neu gestartet</p></td>
<td><p>Wenn das Ereignis auftritt</p></td>
</tr>
</tbody>
</table>


## Verbesserungen in Bezug auf verzögerte Kopien

Zu den Verbesserungen im Hinblick auf verzögerte Kopien gehören die Integration in das Sicherheitsnetz sowie die automatische Wiedergabe von Protokolldateien in bestimmten Szenarien. Das Sicherheitsnetz ist eine Funktion des Transportdiensts, die den Exchange 2010-Transportdumpster ersetzt. Das Sicherheitsnetz ähnelt dem Transportdumpster dahingehend, dass es sich um eine Zustellungswarteschlange handelt, die dem Transportdienst auf einem Postfachserver zugeordnet ist. Diese Warteschlange speichert Kopien von Nachrichten, die erfolgreich an die aktive Postfachdatenbank auf dem Postfachserver zugestellt wurden. Jede aktive Postfachdatenbank auf dem Postfachserver verfügt über eine eigene Warteschlange zum Speichern von Kopien der zugestellten Nachrichten. Sie können festlegen, wie lange das Sicherheitsnetz Kopien der erfolgreich zugestellten Nachrichten speichert, bis diese ablaufen und automatisch gelöscht werden.

Das Sicherheitsnetz übernimmt einige Aufgaben der Shadow-Redundanz in DAG-Umgebungen. In DAG-Umgebungen muss über die Shadow-Redundanz keine weitere Kopie der zugestellten Nachricht in einer Schattenwarteschlange speichern, während auf die Replikation der zugestellten Nachricht in die passiven Kopien der Postfachdatenbanken auf den anderen Postfachservern in der DAG gewartet wird. Die Kopie der zugestellten Nachricht wird bereits im Sicherheitsnetz gespeichert, daher kann die Shadow-Redundanz die Nachricht ggf. aus dem Sicherheitsnetz erneut zustellen.

Mit der Einführung des Sicherheitsnetzes wird die Aktivierung einer verzögerten Datenbankkopie erheblich vereinfacht. Angenommen, Sie verfügen über ein verzögerte Kopie mit einer Wiedergabeverzögerung von 2 Tagen. In diesem Fall würden sie das Sicherheitsnetz für einen Zeitraum von 2 Tagen konfigurieren. Wenn eine Situation eintritt, die die Verwendung einer verzögerten Kopie erforderlich macht, können Sie die Replikation für diese Kopie anhalten und die Kopie zweimal kopieren (zur Beibehaltung der Datenbankversion mit Verzögerung und zum Erstellen einer zusätzlichen Kopie, sofern diese benötigt wird). Anschließend nehmen Sie eine Kopie und entfernen alle Protokolldateien, mit Ausnahme der Protokolldateien im erforderlichen Bereich. Sie binden die Kopie ein, wodurch eine automatische Anforderung an das Sicherheitsnetz ausgelöst wird, die E-Mails der letzten zwei Tage erneut zuzustellen. Mit dem Sicherheitsnetz müssen Sie nicht länger ermitteln, ab welchem Zeitpunkt eine Beschädigung vorlag. Sie erhalten alle E-Mails der letzten zwei Tage zurück, abzüglich der Daten, die bei einem verlustbehafteten Failover regulär verloren gehen.

Verzögerte Kopien können sich jetzt bis zu einem gewissen Grad selbst verwalten und in bestimmten Szenarien eine automatische Protokollwiedergabe auslösen:

  - Wenn ein Schwellenwert für zu wenig Speicherplatz erreicht wird

  - Wenn die verzögerte Kopie eine physische Beschädigung aufweist und ein Seitenpatching erforderlich ist

  - Wenn für mehr als 24 Stunden weniger als drei fehlerfreie Kopien (nur aktiv oder passiv; verzögerte Datenbankkopien werden nicht gezählt) zur Verfügung stehen

In Exchange 2010 stand das Seitenpatching nicht für verzögerte Kopien zur Verfügung. In Exchange 2013 kann das Seitenpatching über die automatische Wiedergabefunktion für verzögerte Kopien genutzt werden. Wenn das System ermittelt, dass für eine verzögerte Kopie ein Seitenpatching erforderlich ist, werden die Protokolle automatisch in die verzögerte Kopie wiedergegeben, um das Seitenpatching auszuführen. Verzögerte Kopien rufen die automatische Wiedergabefunktion auch auf, wenn ein Schwellenwert bezüglich zu wenig Speicherplatz erreicht wird und wenn die verzögerte Kopie während eines bestimmten Zeitraums die einzige verfügbare Kopie ist.

Die Wiedergabe für verzögerte Kopien ist standardmäßig deaktiviert und kann durch Ausführung des folgenden Befehls aktiviert werden:

    Set-DatabaseAvailabilityGroup <DAGName> -ReplayLagManagerEnabled $true

Nach der Aktivierung wird eine Wiedergabe durchgeführt, wenn weniger als drei Kopien zur Verfügung stehen. Sie können den Standardwert 3 ändern, indem Sie den folgenden DWORD-Registrierungswert bearbeiten.

**HKLM\\Software\\Microsoft\\ExchangeServer\\v15\\Replay\\Parameters\\ReplayLagManagerNumAvailableCopies**

Sie müssen den folgenden Registrierungswert konfigurieren, um die Wiedergabe bei Erreichen von Schwellenwerten in Bezug auf zu wenig Speicherplatz zu aktivieren:

**HKLM\\Software\\Microsoft\\ExchangeServer\\v15\\Replay\\Parameters\\ReplayLagLowSpacePlaydownThresholdInMB**

Starten Sie nach der Konfiguration einer dieser Registrierungseinstellungen den Microsoft Exchange DAG-Verwaltungsdienst neu, damit die Änderungen übernommen werden.

Beispiel: Angenommen, eine Umgebung weist eine Datenbank mit 4 Kopien auf (3 hoch verfügbare Kopien und 1 verzögerte Kopie), und für *ReplayLagManagerNumAvailableCopies* wird die Standardeinstellung verwendet. Wenn eine nicht verzögerte Kopie aus irgendeinem Grund nicht verwendet werden kann (z. B. weil sie angehalten wurde), gibt die verzögerte Kopie ihre Protokolldateien automatisch in 24 Stunden wieder.

## Verbesserte Warnung zu einzelnen Kopien

Die Hauptziele beim täglichen Exchange 2013-Messaging bestehen unter anderem darin sicherzustellen, dass Ihre Server zuverlässig arbeiten und dass sich Ihre Datenbankkopien in einem fehlerfreien Zustand befinden. Sie müssen eine aktive Überwachung von Hardware, Windows-Betriebssystem und Exchange-Diensten sicherstellen. In einer Exchange 2013-Umgebung mit Ausfallsicherheit für Postfächer ist es jedoch auch wichtig, die Integrität und den Status der DAG und Ihrer Postfachdatenbankkopien zu überwachen. Es ist besonders wichtig, ein Risikomanagement durch Datenredundanz durchzuführen und auf Szenarien zu überwachen, in denen lediglich eine einzelne Kopie einer replizierten Datenbank vorliegt. Dies gilt insbesondere für Umgebungen, die kein RAID (Redundant Array of Independent Disks) verwenden und stattdessen JBOD-Konfigurationen bereitstellen. In einer RAID-Umgebung hat der Ausfall eines einzelnen Datenträgers keine Auswirkung auf eine aktive Postfachdatenbankkopie. In einer JBOD-Umgebung führt der Ausfall eines einzelnen Datenträgers jedoch zu einem Datenbankfailover.

In Exchange 2010 wurde das Skript "CheckDatabaseRedundancy.ps1" eingeführt. Wie sein Name vermuten lässt, besteht der Zweck dieses Skripts in der Überwachung der Redundanz replizierter Postfachdatenbanken, indem überprüft wird, ob mindestens zwei konfigurierte, fehlerfreie und aktuelle Kopien vorhanden sind. Falls nur eine fehlerfreie Kopie einer replizierten Datenbank vorhanden ist, führt dies zu einer Ereignisprotokollgenerierung und zur Ausgabe einer Warnung an den Administrator. In diesem Fall werden zum Bestimmen von Redundanz sowohl aktive als auch passive Kopien gezählt.

Eine Einzelkopiebedingung ist u. a. in diesen Fällen erfüllt:

  - Ausfall einer aktiven Kopie, die auf eine beliebige passive Kopie repliziert werden soll.

  - Ausfall aller passiven Kopien, was neben den Statuswerten "FailedAndSuspended" und "Fehler" auch den Status "Fehlerfrei" umfasst, wenn die Kopie in Bezug auf Protokollkopie oder -wiedergabe im Rückstand ist. Beachten Sie, dass verzögerte Kopien nicht als rückständig betrachtet werden, wenn sie bei der Protokollwiedergabe weniger als zehn Minuten gegenüber der festgelegten Verzögerungszeit zurückliegen.

  - Das System kann die aktuelle Protokollgenerierung der aktiven Kopie nicht genau ermitteln.

Da es für Administratoren von höchster Wichtigkeit ist, zu wissen, wann nur noch eine einzelne fehlerfreie Kopie einer Datenbank vorliegt, wurde das Skript "CheckDatabaseRedundancy.ps1" durch eine integrierte, systemeigene Funktion ersetzt, die zum DataProtection-Integritätssatz der verwalteten Verfügbarkeit gehört.

Die systemeigene Funktion warnt Administratoren weiterhin über Ereignisprotokollbenachrichtigungen und verwendet zur Unterscheidung von Exchange 2013-Warnungen von Exchange 2010-Warnungen die folgenden Ereignis-IDs für Exchange 2013:

  - Ereignis 4138 (roter Alarm)

  - Ereignis 4139 (grüner Alarm)

In Exchange 2013 wurde die systemeigene Funktion erweitert, um ein Warnungsrauschen zu verringern, das auftreten kann, wenn für mehrere Datenbanken auf demselben Server eine Einzelkopiebedingung erfüllt ist. In Exchange 2010 wurden Warnungen zu einzelnen Kopien auf Datenbankebene generiert. Bei Auftreten eines serverweiten Problems mit Auswirkung auf mehrere Datenbanken und Datenbankkopien konnte es daher zu einem Warnungssturm kommen. Da verschiedene Fehler, wie z. B. Controllerprobleme oder Arbeitsspeicherprobleme, serverweit auftreten, lag die Wahrscheinlichkeit eines solchen Warnungssturms bei diesen Fehlersituationen recht hoch. In Exchange 2013 werden diese Warnungen jetzt auf Serverbasis konfiguriert. Wenn ein Ausfall den gesamten Server betrifft und die Datenredundanz für mehrere Datenbankkopien gefährdet ist, wird nur eine Warnung pro Server generiert.

## Automatische Konfiguration von DAG-Netzwerken

Ein DAG-Netzwerk ist eine Sammlung aus einem oder mehreren Subnetzen, die für Replikations- oder MAPI-Verkehr verwendet werden. Jede DAG enthält maximal ein MAPI-Netzwerk und kein oder mehr Replikationsnetzwerke. In Exchange 2010 basieren die vom System erstellten anfänglichen DAG-Netzwerke (z. B. DAGNetzwerk01 und DAGNetzwerk02) basieren auf den vom Clusterdienst erkannten Subnetzen. In Umgebungen, die mehrere Netzwerke verwenden, und bei denen die Schnittstellen für ein bestimmtes Netzwerk (z. B. das MAPI-Netzwerk) sich im gleichen Subnetz befinden, musste ein Administrator nur wenige zusätzliche Konfigurationsaufgaben ausführen. In Umgebungen jedoch, in denen die Schnittstellen für ein bestimmtes Netzwerk sich in unterschiedlichen Subnetzen befanden, musste der Administrator eine sogenannte Zusammenfassung von DAG-Netzwerken durchführen.

In Exchange 2013 ist kein Zusammenfassen von DAG-Netzwerken mehr erforderlich. Exchange 2013 verwendet weiterhin die gleichen Erkennungsmechanismen, um zwischen den MAPI- und Replikationsnetzwerken zu unterscheiden. DAG-Netzwerke werden jetzt aber automatisch nach Bedarf zusammengefasst.

Zusätzlich werden DAG-Netzwerke ab sofort automatisch vom System verwaltet. Zur Anzeige der DAG-Netzwerkeigenschaften mithilfe der Exchange-Verwaltungskonsole müssen Sie die DAG für eine manuelle Netzwerksteuerung konfigurieren, indem Sie die Eigenschaften der DAG unter Verwendung der Exchange-Verwaltungskonsole ändern oder das Cmdlet **Set-DatabaseAvailabilityGroup** verwenden, um den Parameter *ManualDagNetworkConfiguration* auf `True` festzulegen.

## Änderungen in Bezug auf die Auswahl der besten Kopie

Die Auswahl der besten Kopie (Best Copy Selection, BCS) ist ein interner Algorithmenprozess zum Ermitteln der besten Kopie einer einzelnen Datenbank für die Aktivierung. Die Auswahl erfolgt basierend auf einer Liste potenzieller Kopien für die Aktivierung, die Integrität und Status jeder Kopie angibt. Active Manager wählt die beste verfügbare (und nicht blockierte) Kopie aus, die zur neuen aktiven Datenbankkopie wird, wenn die vorhandene aktive Datenbankkopie ausfällt oder wenn ein Administrator ein Switchover ohne Zielangabe ausführt. In Exchange 2010 wertete der BCS-Prozess verschiedene Aspekte der einzelnen Datenbankkopien aus, um zu ermitteln, welche Kopie am besten aktiviert werden sollte. Hierzu gehörten:

  - Länge der Kopiewarteschlange

  - Länge der Wiedergabewarteschlange

  - Status der Datenbank

  - Inhaltsindexzustand

In Exchange 2013 führt Active Manager dieselben BCS-Prüfungen und -Vorgänge aus, um die Replikationsintegrität zu ermitteln; jetzt wird jedoch zusätzlich eine Einschränkung der absteigenden Reihenfolge von Integritätsstatuswerten verwendet. Aufgrund dieser Änderungen lautet der Name dieser Funktion jetzt BCSS (Best Copy and Server Selection).

BCSS umfasst verschiedene neue Integritätsprüfungen, die Bestandteil der Überwachungskomponenten für die verwaltete Verfügbarkeit in Exchange 2013 sind. Active Manager führt vier zusätzliche Prüfungen durch (hier in der Ausführungsreihenfolge aufgeführt):

1.  **Alle Komponenten fehlerfrei**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten in einem fehlerfreien Status befinden.

2.  **Komponenten mit normaler Priorität fehlerfrei**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten mit normaler Priorität in einem fehlerfreien Status befinden.

3.  **Alle Komponenten besser als Quelle**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten in einem besseren Status als der aktuelle Server mit der betroffenen Kopie befinden.

4.  **Komponenten genauso wie Quelle**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten im gleichen Status wie der aktuelle Server mit der betroffenen Kopie befinden.

Wenn BCSS aufgrund eines Failovers aufgerufen wird, das von einer Überwachungskomponente der verwalteten Verfügbarkeit ausgelöst wird (z. B. über einen Failoverantwortdienst), wird eine zusätzliche obligatorische Einschränkung erzwungen, die erfordert, dass die Komponentenintegrität des Zielservers besser sein muss als die des Servers, auf dem das Failover ausgeführt wurde. Wenn z. B. ein Microsoft Office Outlook Web App-Fehler einen Failover der verwalteten Verfügbarkeit über einen Failoverantwortdienst auslöst, muss BCSS einen Server auswählen, der eine Kopie der betroffenen Datenbank hostet, auf dem Outlook Web App fehlerfrei ist.

## DAG-Verwaltungsdienste

Das kumulative Update 2 (CU2) für die RTM-Version von Exchange 2013 beinhaltet einen neue Dienste auf Postfachservern, die Mitglieder einer DAG sind. Dieser Dienst wird Microsoft Exchange DAT-Verwaltungsdienst (MSExchangeDAGMgmt) genannt. Dieser neue Dienst beinhaltet eine interne DAG-Überwachungsfunktion, wird bereits im Microsoft Exchange-Replikationsdienst (MSExchangeRepl) ausgeführt.

## DAGs ohne Administratorzugriffspunkt im Cluster

Alle DAGs mit Windows Server 2008 R2 oder Windows Server 2012 benötigen mindestens eine IP-Adresse in jedem Subnetz im MAPI-Netzwerk. Die IP-Adressen, die der DAG zugewiesen wurden, werden vom Cluster der DAG mit dem Administratorzugriffspunkt im Cluster (auch Clusternetzwerkname genannt) verwendet, um die Namensauflösung und Verbindungen mit dem Cluster (genauer gesagt, Verbindungen mit dem Clustermitglied, das der aktuelle Besitzer der Kernressourcengruppe des Clusters ist) unter Verwendung des Clusternamens zu ermöglichen. Windows Server 2012 R2 ermöglicht Ihnen, ein Failovercluster ohne Administratorzugriffspunkt zu erstellen. Windows-Failovercluster ohne Administratorzugriffspunkte weisen die folgenden Merkmale auf:

  - Dem Cluster ist keine IP-Adresse zugewiesen, und daher enthält die Kernressourcengruppe des Clusters keine IP-Adressressource.

  - Es ist kein Netzwerkname zum Cluster zugewiesen, und daher befindet sich keine Netzwerknamensressource in der Cluster-Hauptressourcengruppe

  - Der Name des Clusters ist nicht im DNS registriert und kann daher im Netzwerk nicht aufgelöst werden.

  - Ein Clusternamensobjekt (CNO) wird nicht in Active Directory erstellt.

  - Der Windows-Failovercluster kann nicht mit dem Tool für die Failover-Clusterverwaltung verwaltet werden. Er muss über Windows PowerShell verwaltet werden, und die PowerShell-Cmdlets müssen für die einzelnen Cluster-Mitglieder ausgeführt werden.

Unter Windows Server 2012 R2 oder höher ermöglicht Ihnen Service Pack 1 (SP1) für Exchange 2013 und höher eine DAG ohne Administratorzugriffspunkt im Cluster zu erstellen. Sie können mit der Exchange-Verwaltungskonsole oder der Shell DAGs ohne Administratorzugriffspunkt erstellen. Weitere Informationen finden Sie unter [Creating DAGs](managing-database-availability-groups-exchange-2013-help.md) und [Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md).

