---
title: 'Verwalteter Speicher: Exchange 2013 Help'
TOCTitle: Verwalteter Speicher
ms:assetid: efdaf80b-335c-491c-8eb5-1fafd297e8a2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn792020(v=EXCHG.150)
ms:contentKeyID: 62606261
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalteter Speicher

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-07-14_

Alle vorherigen Exchange Server-Versionen, von Exchange Server 4.0 bis Exchange Server 2010, haben die Ausführung einer einzelnen Instanz des Prozesses des Microsoft Exchange-Informationsspeichers (Store.exe) in der Serverrolle "Mailbox" unterstützt. Diese einzelne Speicherinstanz hostet alle Datenbanken auf diesem Server: aktive, passive, verzögerte und wiederhergestellte. In den bisherigen Exchange-Architekturen gibt es, wenn überhaupt, nur eine kleine Isolation zwischen den verschiedenen auf einem Mailbox-Server gehosteten Datenbanken. Ein Problem mit einer einzelnen Postfachdatenbank hat das Potenzial, sich auf alle anderen Datenbanken auszuwirken, und Ausfälle aufgrund der Beschädigung einer Datenbank können den Dienst für alle Benutzer, deren Datenbanken auf diesem Server gehostet werden, beeinträchtigen.

Eine weitere Herausforderung bei einer einzelnen Speicherinstanz von Exchange ist, dass Extensible Storage Engine (ESE) für 8 bis 12 Prozessorkerne angemessen skaliert ist, aber darüber hinaus Probleme mit prozessorübergreifender Kommunikation und Cache-Synchronisierung auftreten können. Angesichts der heutzutage verfügbaren viel größeren Server mit mehr als 16 Kernen würde dies die administrative Herausforderung bedeuten, die Affinität der 8 bis 12 Kerne für ESE zu verwalten und die anderen Kerne für Prozesse außerhalb des Speichers zu verwenden (z. B. Assistenten, Search Foundation, verwaltete Verfügbarkeit usw.). Außerdem waren die Aufwärtsskalierungsoptionen für den Informationsspeicherprozess in der bisherigen Architektur beschränkt.

Der Prozess Store.exe hat im Laufe der Jahre, in denen sich Exchange Server selbst entwickelt hat, auch eine bemerkenswerte Entwicklung durchgemacht, aber als einzelner Prozess ist seine Skalierbarkeit begrenzt, und er stellt auch eine einzelne Fehlerquelle dar. Aufgrund dieser Begrenzungen ist Store.exe in Exchange 2013 nicht mehr vorhanden und wird durch den verwalteten Speicher ersetzt.

## Verwalteter Speicher

Dies ist der Name für die Informationsspeicher-Prozesse in Exchange Server 2013. Der verwaltete Speicher verwendet ein Controller-/Arbeitsprozessmodell, das eine Speicherprozessisolation und ein schnelleres Datenbankfailover erlaubt. Zum verwalteten Speicher gehört auch ein neuer statischer Datenbankzwischenspeicherungsmechanismus, der den dynamischen Pufferalgorithmus in den bisherigen Versionen von Exchange Server ersetzt, Im vom verwalteten Speicher verwendeten Multiprozessmodell existieren ein einzelner Steuerungsprozess für den Speicherdienst (in diesem Falle Microsoft.Exchange.Store.Service.exe, auch bekannt als MSExchangeIS) und je ein Arbeitsprozess (in diesem Falle Microsoft.Exchange.Store.Worker.exe) für jede bereitgestellte Datenbank. Wenn eine Datenbank bereitgestellt wird, wird ein neuer Arbeitsprozess instanziert, der nur für diese Datenbank gilt. Wenn die Bereitstellung der Datenbank aufgehoben wird, wird der Arbeitsprozess für diese Datenbank beendet.

Wenn Sie z. B. 40 Datenbanken auf einem Server bereitgestellt haben, laufen 41 Prozesse für den verwalteten Speicher, einer für jede Datenbank und einer für den Speicherdienst-Steuerungsprozess.

Der Steuerungsprozess für den Speicherdienst ist sehr schlank und sehr zuverlässig, aber wenn er ausfällt oder beendet wird, werden auch alle entsprechenden Arbeitsprozesse beendet, nachdem sie erkannt haben, dass der Steuerungsprozess nicht mehr läuft. Der Steuerungsprozess für den Speicherdienst überwacht den korrekten Ablauf aller Speicherarbeitsprozesse auf dem Server. Eine erzwungene oder unerwartete Beendigung der Microsoft.Exchange.Store.Service.exe führt zu einem sofortigen Failover aller aktiven Datenbankkopien. Der verwaltete Speicher ist außerdem fest in den Microsoft Exchange-Replikationsdienst (MSExchangeRepl.exe) und in Active Manager integriert. Der Steuerungsprozess, die Arbeitsprozesse und der Replikationsdienst arbeiten zusammen, um Ihnen eine höhere Verfügbarkeit und Zuverlässigkeit zu bieten.

  - Prozess des Microsoft Exchange-Standortreplikationsdiensts (MSExchangeRepl.exe)
    
      - Verantwortlich für die Ausgabe der Bereitstellungs- und Bereitstellungsaufhebungsvorgänge im Speicher
    
      - Initiiert Wiederherstellungsaktionen nach vom Informationsspeicher, von Extensible Storage Engine (ESE) oder vom Antwortdienst für verwaltete Verfügbarkeit gemeldeten Speicherungs oder Datenbankausfällen
    
      - Erkennt unerwartete Datenbankfehler
    
      - Stellt die administrative Schnittstelle für Management-Aufgaben bereit

  - Informationsspeicher-Prozess/Dienstcontroller (Microsoft.Exchange.Store.Service.exe)
    
      - Verwaltet die Dauer jedes Arbeitsprozesses auf Grundlage der vom Replikationsdienst gemeldeten Bereitstellungs- und Bereitstellungsaufhebungsvorgänge
    
      - Verarbeitet eingehende Anforderungen vom Windows-Dienststeuerungs-Manager
    
      - Protokolliert Fehlerelemente, wenn Probleme in Speicherarbeitsprozessen erkannt wurden (z. B. Hängen oder unerwarteter Abbruch)
    
      - Beendet die Speicherarbeitsprozesse als Reaktion auf Failover-Ereignisse

  - Speicherarbeitsprozess (Microsoft.Exchange.Store.Worker.exe)
    
      - Verantwortlich für die Ausführung von RPC-Vorgängen für Postfächer in einer Datenbank
    
      - RPC-Endpunkt-Instanz im Arbeitsprozess ist die Datenbank-GUID
    
      - Stellt den Datenbankcache für eine Datenbank bereit

## Statischer Datenbankcaching-Algorithmus

Der Datenbankcaching-Algorithmus, der in Exchange Server 5.5 als dynamische Pufferzuweisung eingeführt wurde und auch vom Informationsspeicher in Exchange 2000 Server, Exchange Server 2003, Exchange Server 2007 und Exchange Server 2010 verwendet wurde, ist in Exchange 2013 nicht mehr vorhanden. Exchange 2013 verwendet einen sehr einfachen und unkomplizierten Algorithmus zur Festlegung des Datenbankcaches. Der verwaltete Speicher weist den Cache zwischen den Datenbanken nicht mehr dynamisch zu, wenn ein Failover auftritt. Dies vereinfacht die interne Cacheverwaltung enorm. Stattdessen beruht der für jeden Datenbankcache zugewiesene Speicher (z. B. jeder Speicherarbeitsprozess) auf der Anzahl der lokalen Datenbankkopien und dem Wert *MaximumActiveDatabases* (falls konfiguriert). Wenn der Wert *MaximumActiveDatabases* größer ist als die Anzahl der aktuellen Datenbankkopien, wird der Cache auf Grundlage der Anzahl der Datenbankkopien berechnet.

Der von Exchange 2013 verwendete statische Algorithmus weist Speicher für den ESE-Cache jedes Speicherarbeitsprozesses auf Grundlage des physischen RAM-Speichers zu. Dies wird als *maximales Cache-Ziel* einer Datenbank bezeichnet. 25% des gesamten Serverspeichers wird dem ESE-Cache zugewiesen. Dies wird als *Servercache-Größenziel* bezeichnet.


> [!NOTE]
> Das Servercache-Größenziel und damit die Menge des für den ESE-Cache zugewiesenen Speicherplatzes, kann mit dem Attribut <EM>msExchESEParamCacheSizeMax</EM> des <EM>InformationStore</EM>-Objekts in Active Directory überschrieben werden (der konfigurierte Wert ist die Anzahl von 32 KB Seiten, die auf alle Speicherprozesse verteilt werden müssen).



Eine statische Menge dieses Caches wird aktiven und passiven Kopien zugewiesen. Dem Speicherarbeitsprozess wird das maximale Cache-Ziel nur zugewiesen, wenn eine aktive Datenbankkopie verarbeitet wird. Passiven Datenbankkopien wird 20 Prozent des maximalen Cache-Ziels zugewiesen. Der Rest wird vom Informationsspeicher reserviert und dem Arbeitsprozess zugewiesen, wenn die Datenbank vom passiven in den aktiven Zustand wechselt.

Das maximale Cache-Ziel wird nur beim Start des Informationsspeichers berechnet. Deshalb müssen Sie, wenn Sie Datenbanken oder Datenbankkopien hinzufügen oder entfernen, den Speichersteuerungsdienst (MSExchangeIS) neu starten, damit der Cache entsprechend angepasst werden kann. Wenn der Dienst nicht neu gestartet wird, haben neu erstellte Datenbanken ein kleineres Cachegrößen-Ziel als Datenbanken, die vor dem Start des Dienstes erstellt wurden. in diesem Fall überschreitet die Summe der Datenbankcache-Größenziele wahrscheinlich das Servercache-Größenziel, bis MSExchangeIS neu gestartet wird.

## Beispielberechnungen des Datenbankcaches

Unten finden Sie Beispiele für die Berechnung der Datenbankcachegröße, die auf der Speicher- und Datenbankkonfiguration des Postfachservers beruhen.

**Beispiel 1**

In diesem Beispiel verfügt der Postfachserver über einen Speicher von 48 GB und hostet zwei aktive und zwei passive Datenbanken. Außerdem ist der Parameter *MaximumActiveDatabases* nicht konfiguriert. In dieser Konfiguration wird jedem Arbeitsprozess für eine aktive Datenbankkopie ein Datenbankcache von 3 GB zugewiesen, und jeder Arbeitsprozess für eine passive Datenbankkopie erhält 0,6 GB. Hier wird beschrieben, wie diese Werte berechnet wurden.

Multiplizieren Sie den Speicherbetrag mit 25 %, um das Servercache-Größenziel zu erhalten:

48 GB x 25 % = 12 GB

Teilen Sie dann, um das maximale Datenbankcache-Ziel zu erhalten, das Servercache-Größenziel durch die Gesamtzahl der aktiven und passiven Datenbanken:

12 GB / 4 Datenbanken = 3 GB

Um den Speicherbetrag zu bestimmen, der für die passiven Datenbankkopien verwendet wird, multiplizieren Sie das maximale Datenbankcache-Ziel mit 20 %:

3 GB x 20 % = 0,6 GB

Von den 12 GB Speicher, die dem Servercache-Größenziel zugewiesen wurden, werden 7,2 GB in Datenbankarbeitsprozessen belegt, und 4,8 GB werden vom Informationsspeicher für die zwei passiven Datenbankkopien für den Fall reserviert, dass aus diesen aktive Kopien werden. in diesem Fall nutzen sie ihr maximales Cache-Ziel von 3 GB.

**Beispiel 2**

In diesem Beispiel hat der Postfachserver ebenfalls 48 GB Speicher und hostet zwei aktive und zwei passive Datenbanken; der Parameter *MaximumActiveDatabases* ist jedoch mit dem Wert 2 konfiguriert. In dieser Konfiguration beträgt die Menge des Datenbankcaches für jeden Arbeitsprozess einer aktiven Datenbankkopie 5 GB und für jeden Arbeitsprozess einer passiven Datenbankkopie 0,2 GB. Hier wird beschrieben, wie diese Werte berechnet wurden.

Multiplizieren Sie den Speicherbetrag mit 25 %, um das Servercache-Größenziel zu erhalten:

48 GB x 25 % = 12 GB

Um das maximale Datenbankcache-Ziel zu erreichen, dividieren Sie das Servercache-Größenziel durch die Gesamtzahl der aktiven Datenbanken plus die Gesamtzahl der passiven Datenbanken, multipliziert mit 20 %:

12 GB / (2A + (2P x 20 %)) = 5 GB

Um den Speicherbetrag zu bestimmen, der für die passiven Datenbankkopien verwendet wird, multiplizieren Sie das maximale Datenbankcache-Ziel mit 20 %:

5 GB x 20 % = 1 GB

Von den 12 GB Speicher, die dem Servercache-Größenziel zugewiesen sind, werden 12 GB in Datenbankarbeitsprozessen belegt, und vom Informationsspeicher wird kein Speicherplatz für die zwei passiven Datenbankkopien reserviert, da diese in der Konfiguration nicht zu aktiven Datenbanken werden können (weil *MaximumActiveDatabases* mit dem Wert 2 konfiguriert ist und sich bereits 2 aktive Datenbankkopien auf dem Server befinden).

