---
title: 'Active Manager: Exchange 2013 Help'
TOCTitle: Active Manager
ms:assetid: f4be27b7-1d7c-47b4-87ac-bfdfcc046f00
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd776123(v=EXCHG.150)
ms:contentKeyID: 50477070
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Active Manager

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Microsoft Exchange Server 2013 enthält eine Komponente namens *Active Manager*, mit der die Plattform mit hoher Verfügbarkeit verwaltet wird, die Database Availability Groups (DAGs) und Postfachdatenbankopien einbezieht. Active Manager wird innerhalb des Microsoft Exchange-Replikationsdiensts (MSExchangeRepl.exe) auf allen Postfachservern ausgeführt. Auf Postfachservern, die nicht Mitglied einer DAG sind, gibt es eine einzelne Active Manager-Rolle: *eigenständiger Active Manager*. Auf Servern, die zu einer DAG gehören, gibt es zwei Active Manager-Rollen: *Primary Active Manager* (PAM) und *Standby Active Manager* (SAM). PAM ist die Active Manager-Rolle in einer DAG, die entscheidet, welche Kopien aktiv oder passiv sind. Ein PAM ist zuständig für den Empfang von Benachrichtigungen zu Topologieänderungen und für das Reagieren auf Serverfehler. Das Mitglied der DAG mit der PAM-Rolle entspricht immer dem Mitglied, das derzeit die Clusterquorumressource (Standardclustergruppe) besitzt. Wenn der Server mit der Clusterquorumressource ausfällt, wird die PAM-Rolle automatisch auf einen funktionierenden Server verschoben, der den Besitz der Clusterquorumressource übernimmt. Wenn Sie den Server, auf dem die Clusterquorumressource gehostet wird, zu Wartungs- oder Upgradezwecken offline schalten müssen, müssen Sie zunächst die PAM-Rolle auf einen anderen Server in der DAG verschieben. Der PAM steuert alle Wechsel der Bezeichnung "Aktiv" zwischen den Kopien einer Datenbank. (Nur eine Kopie kann jeweils aktiv sein, und diese Kopie kann entweder eingebunden oder nicht eingebunden sein.) Der PAM führt außerdem die Funktionen der SAM-Rolle auf dem lokalen System durch (Erkennen von Fehlern der lokalen Datenbank und des lokalen Informationsspeichers).

Der SAM stellt anderen Komponenten von Exchange, auf denen eine Active Manager-Clientkomponente ausgeführt wird (z. B. Clientzugriffs- oder Transportdienste), Informationen darüber bereit, auf welchem Server die aktive Kopie einer Postfachdatenbank gehostet wird. Der SAM erkennt Fehler der lokalen Datenbanken und des lokalen Informationsspeichers. Er reagiert auf Fehler, indem er den PAM zum Einleiten eines Failovers auffordert (falls die Datenbank repliziert wird). Ein SAM bestimmt nicht das Ziel des Failovers und aktualisiert auch nicht den Speicherort der Datenbank im PAM. Er greift auf den aktuellen Speicherortzustand der aktiven Datenbankkopie zu, um eingehende Abfragen nach der aktiven Datenbankkopie zu beantworten.


> [!NOTE]
> exExchange2k13 ist keine Clusteranwendung. Stattdessen werden die in clusapi.dll implementierten Clusterbibliotheksfunktionen für Cluster-, Gruppen-, Clusternetzwerk- (Taktintervalle), Knotenverwaltungs-, Clusterregistrierungs- und einige Steuerungscodefunktionen eingesetzt. Außerdem speichert Active Manager aktuelle Informationen zur Postfachdatenbank (z.&nbsp;B. aktive und passive sowie eingebundene Daten) in der Clusterdatenbank (die auch als Clusterregistrierung bezeichnet wird). Auch wenn die Informationen direkt in der Clusterdatenbank abgelegt werden, greifen andere Komponenten nicht direkt darauf zu.



In Exchange 2013 wird die Integrität aller eingebundenen Datenbanken in regelmäßigen Abständen vom Microsoft Exchange-Replikationsdienst überwacht. Dieser überwacht außerdem die ESE (Extensible Storage Engine) auf E/A-Fehler oder Ausfälle. Wenn der Dienst einen Fehler erkennt, benachrichtigt er Active Manager. Anschließend bestimmt Active Manager, welche Datenbankkopie eingebunden werden soll und was dazu erforderlich ist. Zusätzlich wird die aktive Kopie einer Postfachdatenbank (basierend auf der zuletzt eingebundenen Kopie der Datenbank) verfolgt, und die Ergebnisse dieser Verfolgung werden dem Clientzugriffsserver bereitgestellt, mit dem der Client verbunden ist.

## Auswahl der besten Kopie

Wenn ein Fehler auftritt, der den Zugriff auf die aktive Kopie der replizierten Postfachdatenbank verhindert, führt Active Manager mehrere Schritte zur Wiederherstellung aus, wobei die bestmögliche passive Kopie der betroffenen zu aktivierenden Datenbank ausgewählt wird. Dieser Prozess wurde in Exchange 2010 als Auswahl der besten Kopie bezeichnet und wird nun in Exchange 2013 als Auswahl der besten Kopie und des besten Servers bezeichnet. Der allgemeine Prozess erfolgt in der folgenden Reihenfolge:

1.  Die verwaltete Verfügbarkeit oder Active Manager erkennt einen Fehler, oder ein Administrator leitet ein Switchover ohne Zielangabe ein.

2.  Der PAM führt den internen Algorithmus zur Auswahl der besten Kopie und des besten Servers aus.

3.  Ein Prozess, der *Versuch des Kopierens der letzten Protokolle (Attempt Copy Last Logs, ACLL)* genannt wird, erfolgt, bei dem versucht wird, alle fehlenden Protokolle vom Server zu kopieren, der die aktive Datenbankkopie vor dem Fehler oder dem Switchover gehostet hat.

4.  Nachdem der ACLL-Prozess abgeschlossen ist, wird der Wert des Parameters *AutoDatabaseMountDial* für die Postfachserver, die Kopien der Datenbank hosten, mit der Länge der Kopiewarteschlange der zu aktivierenden Datenbank verglichen. An dieser Stelle findet einer der beiden folgenden Vorgänge statt:
    
      - Die Anzahl der fehlenden Protokolldateien ist kleiner gleich dem Wert von *AutoDatabaseMountDial*. In diesem Fall wird Schritt 5 ausgeführt.
    
      - Die Anzahl der fehlenden Protokolldateien ist größer als der Wert von *AutoDatabaseMountDial*. In diesem Fall versucht Active Manager, die nächste verfügbare beste Kopie zu aktivieren (falls vorhanden).

5.  Der PAM sendet über einen RPC (Remote Procedure Call, Remoteprozeduraufruf) eine Einbindungsanforderung an den Microsoft Exchange-Informationsspeicher. An dieser Stelle findet einer der beiden folgenden Vorgänge statt:
    
      - Die Datenbank wird bereitgestellt und den Clients zur Verfügung gestellt.
    
      - Die Datenbank wird nicht eingebunden, und der PAM führt die Schritte 3 und 4 für die nächste bestmögliche Kopie (falls vorhanden) durch.

In Exchange 2010 wertete der BCS-Prozess verschiedene Aspekte der einzelnen Datenbankkopien aus, um zu ermitteln, welche Kopie am besten aktiviert werden sollte. Hierzu gehörten:

  - Länge der Kopiewarteschlange

  - Länge der Wiedergabewarteschlange

  - Status der Datenbank

  - Inhaltsindexzustand

In Exchange 2013 durchläuft Active Manager dieselben Prüfungen und Phasen für die Auswahl der besten Kopie, aber zusätzlich wird jetzt eine Einschränkung hinsichtlich der absteigenden Reihenfolge der Integritätsstatusangaben berücksichtigt. Insbesondere die Auswahl der besten Kopie und des besten Servers umfasst verschiedene neue Prüfungen, die Teil der integrierten Überwachungskomponenten für die verwaltete Verfügbarkeit in Exchange 2013 sind. Active Manager führt vier zusätzliche Prüfungen durch (hier in der Ausführungsreihenfolge aufgeführt):

1.  **Alle Komponenten fehlerfrei**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten in einem fehlerfreien Status befinden.

2.  **Komponenten mit normaler Priorität fehlerfrei**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten mit normaler Priorität in einem fehlerfreien Status befinden.

3.  **Alle Komponenten besser als Quelle**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten in einem besseren Status als der aktuelle Server mit der betroffenen Kopie befinden.

4.  **Komponenten genauso wie Quelle**   Prüft, ob ein Server mit einer Kopie der betroffenen Datenbank vorhanden ist, in der sich alle Überwachungskomponenten im gleichen Status wie der aktuelle Server mit der betroffenen Kopie befinden.

Wenn die Auswahl der besten Kopie und des besten Servers aufgrund eines Failovers aufgerufen wird, der von einer Überwachungskomponente (z. B. von einem Failoverantwortdienst) ausgelöst wurde, wird eine zusätzliche obligatorische Einschränkung erzwungen, bei der die Komponentenintegrität des Zielservers einen besseren Wert als die des Servers aufweisen muss, auf dem das Failover aufgetreten ist. Wenn z. B. ein Microsoft Outlook Web App-Fehler (OWA) ein Failover über einen Failoverantwortdienst auslöst, dann muss die Auswahl der besten Kopie und des besten Servers einen Server auswählen, der eine Kopie der betroffenen Datenbank hostet, auf dem Outlook Web App fehlerfrei ist.

## Auswahl der bestmöglichen Kopie

Hinsichtlich der Datenbankfehler (keine Protokollfehler) führt Active Manager in Exchange 2013 dieselben Prüfungen wie in Exchange 2010 aus. Active Manager beginnt den Prozess zur Auswahl der bestmöglichen Kopie mit dem Erstellen einer Liste mit Datenbankkopien, die potenzielle Kandidaten für die Aktivierung sind. Alle Datenbankkopien, die nicht erreicht werden können oder für die Aktivierung gesperrt sind, werden ignoriert und während des Auswahlprozesses nicht verwendet. Die Reihenfolge in der Liste hängt vom Wert des Parameters *AutoDatabaseMountDial* ab:

  - Wenn AutoDatabaseMountDial auf allen Servern, die eine Kopie der Datenbank hosten, mit einem anderen Wert als Lossless konfiguriert ist, sortiert Active Manager die Ergebnisliste mithilfe der Länge der Kopiewarteschlange als primären Schlüssel. Die Berechnung basiert auf dem Wert von LastLogInspected (aus Sicht der Kopie), sodass die Liste potenzieller Kopien anhand des höchsten Werts für LastLogInspected sortiert wird (bei der es sich um die Kopie mit der kürzesten Länge der Kopiewarteschlange handelt). Bei Bedarf sortiert Active Manager die Liste ein zweites Mal mit dem Wert für die Aktivierungseinstellung als zweitem Schlüssel, um mögliche Ausgleichbedingungen aufzulösen, bei denen zwei oder mehr passive Kopien dieselbe Länge für die Kopiewarteschlange aufweisen. Die Kopie mit dem niedrigsten Wert für die Aktivierungseinstellung hat die höchste Priorität in der Liste.

  - Wenn *AutoDatabaseMountDial* auf allen Servern, die eine Kopie der Datenbank hosten, mit dem Wert `Lossless` konfiguriert ist, sortiert Active Manager die Ergebnisliste mithilfe des Werts für die Aktivierungseinstellung als primärem Schlüssel in aufsteigender Reihenfolge. Wenn ein Administrator ein verlustfreies Server- oder Datenbankswitchover ohne Angabe eines Ziels ausführt, sortiert Active Manager die Ergebnisliste zusätzlich über den Wert für die Aktivierungseinstellung als primärem Schlüssel in aufsteigender Reihenfolge.

Als Nächstes versucht Active Manager, eine Postfachdatenbankkopie in der Liste mit dem Status Healthy, DisconnectedAndHealthy, DisconnectedAndResynchronizing oder SeedingSource zu finden, und bewertet anschließend das Aktivierungspotenzial aller Kopien in der Liste anhand einer Reihenfolgenliste mit zehn Kriterien. Active Manager bestimmt, ob ein Kandidat für die Aktivierung den ersten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Healthy.

  - Die Länge der Kopiewarteschlange beträgt weniger als zehn Protokolldateien.

  - Die Länge der Wiedergabewarteschlange beträgt weniger als 50 Protokolldateien.

Wenn keine der Datenbankkopien den ersten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den zweiten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Crawling.

  - Die Länge der Kopiewarteschlange beträgt weniger als zehn Protokolldateien.

  - Die Länge der Wiedergabewarteschlange beträgt weniger als 50 Protokolldateien.

Wenn keine der Datenbankkopien den zweiten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den dritten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Healthy.

  - Die Länge der Wiedergabewarteschlange beträgt weniger als 50 Protokolldateien.

Wenn keine der Datenbankkopien den dritten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den vierten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Crawling.

  - Die Länge der Wiedergabewarteschlange beträgt weniger als 50 Protokolldateien.

Wenn keine der Datenbankkopien den vierten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den fünften Kriteriensatz erfüllt:

  - Die Länge der Wiedergabewarteschlange beträgt weniger als 50 Protokolldateien.

Wenn keine der Datenbankkopien den fünften Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den sechsten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Healthy.

  - Die Länge der Kopiewarteschlange beträgt weniger als zehn Protokolldateien.

Wenn keine der Datenbankkopien den sechsten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den siebten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Crawling.

  - Die Länge der Kopiewarteschlange beträgt weniger als zehn Protokolldateien.

Wenn keine der Datenbankkopien den siebten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den achten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Healthy.

Wenn keine der Datenbankkopien den achten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu finden, die den neunten Kriteriensatz erfüllt:

  - Der zugehörige Inhaltsindex besitzt den Status Crawling.

Wenn keine der Datenbankkopien den zweiten Kriteriensatz erfüllt, versucht Active Manager eine Datenbank zu aktivieren, die den Status Healthy, DisconnectedAndHealthy, DisconnectedAndResynchronizing oder SeedingSource (den zehnten Kriteriensatz) hat. Wird keine Datenbankkopie gefunden, die den zehnten Kriteriensatz erfüllt, kann keine Datenbankkopie automatisch aktiviert werden.

Sobald eine oder mehrere Kopien gefunden wurden, die einen oder mehrere Kriteriensätze erfüllen, wird der ACLL-Vorgang ausgeführt, bei dem Protokolldateien aus der Originalquelle in die potenzielle neue aktive Kopie kopiert werden. Nach Abschluss des ACLL-Vorgangs sendet der primäre Active Manager eine Einbindungsanforderung ab. Die Datenbank wird entweder eingebunden und Clients zur Verfügung gestellt, oder die Datenbank wird nicht eingebunden, woraufhin der primäre Active Manager die nächste bestmögliche Kopie sucht (sofern vorhanden).

