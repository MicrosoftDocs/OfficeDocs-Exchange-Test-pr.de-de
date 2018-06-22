---
title: 'Leistungsfaktoren und bewährte Methoden für Hybridmigrationen: Exchange 2013 Help'
TOCTitle: Leistungsfaktoren und bewährte Methoden für Hybridmigrationen
ms:assetid: 120a7832-d2d3-47d7-b305-918360c2ef66
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt483789(v=EXCHG.150)
ms:contentKeyID: 70117978
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Leistungsfaktoren und bewährte Methoden für Hybridmigrationen

 

_<strong>Gilt für:</strong>Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_


Es gibt viele Wege für die Migration von Daten aus einer lokalen E-Mail-Organisation zu Office 365. Bei der Planung einer Migration zu Office 365 stellt sich häufig die Frage nach einer Verbesserung der Datenmigrationsleistung sowie nach einer Optimierung der Migrationsgeschwindigkeit. In diesem Artikel wird die Migrationsleistung für Exchange-Hybridbereitstellungen erläutert. Leistungsinformationen zu anderen Migrationsmethoden finden Sie unter [Office 365-Migrationsleistung und bewährte Methoden](http://go.microsoft.com/fwlink/p/?linkid=623651).

## Leistungsfaktoren und bewährte Methoden für Hybridmigrationen

Die Migration von Hybridbereitstellungen unterstützt die reibungslose Migration zwischen lokalen Exchange-Servern und Exchange Online in Office 365.

Die Hybridbereitstellungsmigration ist mit Abstand die schnellste Methode für die Migration von Postfachdaten zu Office 365. Bei echten Kundenbereitstellungen wurden bereits Durchsatzraten von 100 GB/Stunde gemessen. Die folgende Tabelle enthält eine Auflistung der Faktoren, die für systemeigene Office 365-Hybridmigrationsszenarien gelten.

Wenn Ihre lokale Umgebung mehrere Websites an geografisch verteilten Standorten enthält, können Sie die Migrationsleistung verbessern, indem Sie geografisch nah aneinander liegende Migrationsendpunkte erstellen. Dies liegt daran, dass die Migration in einem solchen Szenario das Microsoft-Netzwerk anstelle eines zentralen Migrationsendpunkts verwendet, der das lokale Netzwerk verwendet.

## Faktor 1: Datenquelle (Exchange Server)


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Prüfliste</th>
<th>Beschreibung</th>
<th>Bewährte Methoden</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Systemleistung</p></td>
<td><p>Das Extrahieren von Daten ist eine aufwändige Aufgabe. Das Quellsystem muss über ausreichend Ressourcen wie CPU-Zeit und Arbeitsspeicher verfügen, um eine bessere Migrationsleistung zu erzielen. Während der Migration erreicht das Quellsystem bei der Bereitstellung der regulären Benutzerarbeitsauslastung häufig beinahe die Kapazitätsgrenze. Manchmal beeinträchtigt die zusätzliche Migrationsarbeitsauslastung sogar den Endbenutzerzugriff, da nicht genügend Systemressourcen zur Verfügung stehen.</p></td>
<td><p>Überwachen Sie die Systemleistung im Rahmen einer Pilotmigration. Ist das System ausgelastet, wird von der Verwendung eines aggressiven Migrationsplans für dieses System abgeraten, da dies eine langsame Migration sowie Probleme mit der Dienstverfügbarkeit zur Folge haben kann. Verbessern Sie möglichst die Leistung des Quellsystems. Fügen Sie dazu Hardwareressourcen hinzu, und verringern Sie die Systemlast, indem Sie Aufgaben und Benutzer auf andere Server auslagern, die von der Migration nicht betroffen sind.</p>
<p>Weitere Informationen finden Sie unter:</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/?linkid=723566">Ask the Perf Guy: Sizing Exchange 2016 Deployments</a>.</p></li>
<li><p><a href="https://technet.microsoft.com/de-de/library/jj150551(v=exchg.150)">Serverstatus und -leistung</a></p></li>
<li><p><a href="http://technet.microsoft.com/de-de/library/dd351192.aspx">Grundlegendes zur Exchange 2010-Leistung</a></p></li>
</ul>
<p>Bei der Migration einer lokalen Exchange-Organisation mit mehreren Postfachservern und Datenbanken empfiehlt sich die Erstellung einer Migrationsbenutzerliste, die gleichmäßig über die verschiedenen Postfachserver und Datenbanken verteilt ist. Zur Maximierung des Durchsatzes kann diese Liste auf der Grundlage der Leistung des jeweiligen Servers noch weiter optimiert werden.</p>
<p>Verfügt Server A beispielsweise über eine um 50 Prozent höhere Ressourcenverfügbarkeit als Server B, bietet es sich an, in einem Migrationsbatch den Benutzeranteil von Server A um 50 Prozent zu erhöhen. Ähnliche Methoden können auch für andere Quellsysteme angewendet werden.</p>
<p>Migrationen sollten bei maximaler Ressourcenverfügbarkeit der Server ausgeführt werden, also beispielsweise außerhalb der Geschäftszeiten, an Wochenenden oder an Feiertagen.</p></td>
</tr>
<tr class="even">
<td><p>Back-End-Aufgaben</p></td>
<td><p>Andere Back-End-Aufgaben, die während der Migration ausgeführt werden. Da Migrationen üblicherweise außerhalb der Geschäftszeiten durchgeführt werden, kommt es oftmals zu Konflikten mit anderen Wartungsaufgaben, die auf den lokalen Servern ausgeführt werden (beispielsweise Datensicherungen).</p></td>
<td><p>Prüfen Sie, welche anderen Systemaufgaben möglicherweise während der Migration ausgeführt werden. Es wird empfohlen, die Datenmigration zu einer Zeit auszuführen, in der keine anderen ressourcenintensiven Aufgaben erledigt werden.</p>
<p><strong>Hinweis</strong>   Bei Kunden mit einem lokalen Microsoft Exchange-System handelt es sich bei den Back-End-Aufgaben häufig um Datensicherungslösungen sowie um die <a href="http://technet.microsoft.com/de-de/library/aa996226(exchg.65).aspx">Wartung von Exchange-Informationsspeichern</a>.</p></td>
</tr>
</tbody>
</table>


## Faktor 2: Migrationsserver

Bei der Hybridbereitstellungsmigration handelt es sich um eine von der Cloud initiierte Migrationsmethode mit Datenübertragung per Pull/Push, bei der ein Hybridserver mit Exchange als Migrationsserver fungiert. Dies wird häufig nicht berücksichtigt, und Kunden verwenden einen virtuellen Computer mit geringer Leistung als Migrationsserver. Das Ergebnis ist eine nicht zufriedenstellende Migrationsleistung.

**Bewährte Methode**

Neben den oben beschriebenen bewährten Methoden wurden folgende bewährte Methoden getestet, mit denen bei tatsächlichen Kundenmigrationen die Migrationsleistung verbessert werden konnte:

  - Verwenden Sie für die Exchange-Hybridserver leistungsstarke physische Computer auf Serverniveau statt virtueller Computer.

  - Verwenden Sie mehrere Hybridserver, die hinter dem Netzwerklastenausgleichsmodul des Kunden angeordnet sind.

So wurde beispielsweise bei tatsächlichen Kundenmigrationen mit der folgenden Konfiguration ein konstanter Durchsatz von 30 GB/Stunde erreicht:

  - **Netzwerk**  Ausgehende Pipe an das Internet mit 500 MB; internes Netzwerk mit 1 GB und Glasfaser-Backbone mit 10 GB.

  - **Hardware**   Spezifikationen für die beiden Clientzugriffsserver/HUB-Server (physisch):
    
      - CPU: Intel® Xeon® CPU E5520 @ 2,27 GHz 2,26 GHz (zwei Prozessoren).
    
      - RAM: 24 GB.
    
      - Datenträger: Acht mit jeweils 146 GB. RAID-5-Konfiguration = 960 GB insgesamt (Rohspeicher).

  - **MRSProxy**   Mit dem Parallelitätswert von "100" konfiguriert.

## Faktor 3: Migrationsmodul

Bei der Hybridbereitstellungsmigration werden die systemeigenen Office 365-Tools verwendet. Die Office 365-Migrationsdiensteinschränkung wird angewandt.

**Exchange 2003 im Vergleich mit höheren Versionen von Exchange**

Bei der Migration von Exchange 2003 gibt es einen bedeutenden Unterschied für die Endbenutzer. Im Gegensatz zu höheren Versionen von Exchange können Exchange 2003-Endbenutzer während der Datenmigration nicht auf ihre Postfächer zugreifen. Daher müssen Kunden mit Exchange 2003 üblicherweise genauer darauf achten, wann sie Migrationen ausführen und wie viel Zeit für die Migration benötigt wird. Dies gilt insbesondere bei geringer Migrationsleistung aufgrund von großen Postfächern oder geringer Netzwerkgeschwindigkeit.

Die Exchange 2003-Migration sind auch sehr empfindlich im Hinblick auf Unterbrechungen. Beispiel: Bei einer tatsächlichen Kundenmigration trat während der Migration eines 10-GB-Postfachs ein Dienstvorfall auf, als die Migration des Postfachs erst zur Hälfte abgeschlossen war. Der Office 365-Clientzugriffsserver, von dem die Datenmigration verarbeitet wurde, musste zur Behebung des Problems neu gestartet werden. In diesem Fall musste die Migration des Postfachs neu gestartet werden, sodass die gesamten 10 GB an Daten noch einmal migriert werden mussten. Die Migration konnte nicht an dem Punkt fortgesetzt werden, an dem sie unterbrochen wurde. Bei Exchange 2010 und höheren Exchange-Versionen können Migrationen dagegen nach Unterbrechungen fortgesetzt werden.

**Bewährte Methode**

Einige Kunden entscheiden sich bei der Migration umfangreicher Exchange 2003-Postfächer mit vertraulichen Daten für eine Migration in zwei Etappen:

  - **Erste Etappe**   Migrieren Sie die Postfächer aus Exchange 2003 zu einem Server mit Exchange 2010 oder höher (üblicherweise der Hybridserver). Bei der ersten Etappe handelt es sich zwar um eine Offlineverschiebung, es ist jedoch üblicherweise eine sehr schnelle Migration in einem lokalen Netzwerk.

  - **Zweite Etappe**   Migrieren Sie die Postfächer aus Exchange 2010 oder höher zu Office 365.

Die zweite Etappe ist eine Onlineverschiebung mit höherer Benutzerfreundlichkeit und Fehlertoleranz. Bei diesem Ansatz mit zwei Etappen wird für das temporäre lokale Benutzerpostfach eine Exchange-Lizenz benötigt.

**Proxy für den Postfachreplikationsdienst (MRSProxy)**

Der MRS-Proxy ist das lokale Migrationsfeature, das auf der Office 365-Seite mit dem Postfachreplikationsdienst zusammenarbeitet. Weitere Informationen finden Sie unter [Grundlegendes zu Verschiebungsanforderungen](http://technet.microsoft.com/de-de/library/dd298174.aspx).

**Bewährte Methode**

Die maximale Anzahl von MRS-Proxyverbindungen kann für den lokalen Exchange-Hybridserver konfiguriert werden. Führen Sie den folgenden Windows PowerShell-Befehl aus.

    Set-WebServicesVirtualDirectory -Identity "EWS (Default Web Site)" -MRSMaxConnections <number between 0 and unlimited; default is 100>


> [!NOTE]
> Bei den meisten Kundenmigrationen muss der Standardwert für "MRSMaxConnections" nicht geändert werden. Falls der Quellserver vor einer Überbeanspruchung durch die Migrationslast geschützt werden muss, können Kunden die Verbindungsanzahl verringern. Diese Einstellung gilt pro MRS-Proxyserver. Verfügt ein Kunde über zwei MRS-Proxyserver, von denen jeder auf zehn Verbindungen festgelegt ist, erhalten sie 20 (2 x 10) Verbindungen als Gesamtanzahl für die MRS-Proxyverbindungen. Weitere Informationen zum Konfigurieren des MRS-Proxydiensts in der lokalen Exchange&nbsp;2010-Organisation finden Sie unter <A href="http://technet.microsoft.com/de-de/library/ee732395.aspx">Starten des MRSProxy-Diensts auf einem Remote-Clientzugriffsserver</A>.



## Faktor 4: Netzwerk

**Überprüfungstests**

Bei Kunden mit Exchange 2010 oder höher kann die Netzwerkleistung für Hybridmigrationen durch Ausführen mehrerer Testpostfachmigrationen getestet werden. Alternativ können Sie tatsächliche Benutzerpostfächer mit der Option „-SuspendWhenReadyToComplete“ migrieren, um einen Eindruck von der Migrationsleistung zu erhalten. Entfernen Sie nach Abschluss des Tests die Verschiebungsanforderung, um negative Auswirkungen für die Endbenutzer zu vermeiden.

Weitere Informationen zu Verschiebungsanforderungen finden Sie unter [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Faktor 5: Office 365-Dienst

Office 365-Einschränkung aufgrund der Ressourcenintegrität betrifft Migrationen, die mit Office 365-Hybridbereitstellungsmigrationen ausgeführt werden. Weitere Einzelheiten finden Sie weiter oben im Abschnitt zur Office 365-Einschränkung aufgrund der Ressourcenintegrität.

