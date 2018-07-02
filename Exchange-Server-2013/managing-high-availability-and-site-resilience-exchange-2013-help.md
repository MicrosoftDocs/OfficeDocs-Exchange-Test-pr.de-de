---
title: 'Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte: Exchange 2013 Help'
TOCTitle: Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte
ms:assetid: f9677392-88d2-457f-a488-245771a8c1f2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638215(v=EXCHG.150)
ms:contentKeyID: 50477121
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Nachdem Sie eine Microsoft Exchange Server 2013-Lösung für hohe Verfügbarkeit oder Ausfallsicherheit für Standorte erstellt, überprüft und bereitgestellt haben, wird die Lösung von der Bereitstellungsphase in die operative Phase des Gesamtlebenszyklus der Lösung überführt. Die operative Phase umfasst verschiedene Tasks, die alle in Zusammenhang mit einem der folgenden Bereiche stehen: Database Availability Groups (DAGs), Postfachdatenbankkopien, Durchführen einer proaktiven Überwachung und Verwalten von Switchover- und Failovervorgängen.

**Inhalt**

Database availability group management

Mailbox database copy management

Proactive monitoring

Switchovers and failovers

## Verwaltung von Database Availability Groups

Die Verwaltung von DAGs umfasst die folgenden Tasks:

  - **Erstellen von mindestens einer DAG**   Das Erstellen einer DAG ist üblicherweise ein einmaliger Vorgang, der während der Bereitstellungsphase des Lösungslebenszyklus durchgeführt wird. Es kann jedoch verschiedene Gründe geben, die das Erstellen von DAGs während der operativen Phase erforderlich machen. Beispiel:
    
      - Die DAG ist für den Drittanbieter-Replikationsmodus konfiguriert, und Sie möchten auf eine fortlaufende Replikation umstellen. Sie können eine DAG nicht auf die fortlaufende Replikation zurücksetzen; Sie müssen eine neue DAG erstellen.
    
      - Sie verfügen über Server in mehreren Domänen. Alle Mitglieder derselben DAG müssen auch Mitglieder derselben Domäne sein.

  - **Verwalten der DAG-Mitgliedschaft**   Das Verwalten der DAG-Mitglieder ist ein unregelmäßiger Task, der üblicherweise während der Bereitstellungsphase des Lösungslebenszyklus ausgeführt wird. Aufgrund der Flexibilität der inkrementellen Bereitstellung kann die Verwaltung der DAG-Mitgliedschaft jedoch auch in anderen Phasen im Lösungslebenszyklus durchgeführt werden.

  - **Konfigurieren von DAG-Eigenschaften**   Jede DAG weist verschiedene Eigenschaften auf, die nach Bedarf konfiguriert werden können. Zu diesen Eigenschaften zählen:
    
      - **Zeugenserver und Zeugenverzeichnis**   Der Zeugenserver ist ein Server außerhalb der DAG, der als Wähler für das Quorum fungiert, wenn die DAG eine gerade Zahl an Mitgliedern enthält. Das Zeugenverzeichnis ist ein Verzeichnis, das auf dem Zeugenserver erstellt und freigegeben und vom System für das Verwalten eines Quorums verwendet wird.
    
      - **IP-Adressen**   Jede DAG verfügt über mindestens eine IPv4-Adresse und optional über eine oder mehrere IPv6-Adressen. Die der DAG zugewiesenen IP-Adressen werden vom Cluster verwendet, der der DAG zugrunde liegt. Die Anzahl von IPv4-Adressen, die der DAG zugewiesen sind, entspricht der Anzahl von Subnetzen, aus denen sich das von der DAG verwendete MAPI-Netzwerk zusammensetzt. Sie können die DAGs zur Verwendung statischer IP-Adressen oder für den automatischen Bezug von Adressen über DHCP (Dynamic Host Configuration Protocol) konfigurieren.
    
      - **Datencenter-Aktivierungskoordinierungsmodus**   Bei diesem Modus handelt es sich um eine Eigenschafteneinstellung in einer DAG, die zur Vermeidung von Split Brain-Bedingungen auf Datenbankebene konzipiert wurde, in einem Szenario, in dem Sie den Dienst in einem primären Datencenter wiederherstellen, nachdem ein Datencenterswitchover ausgeführt wurde. Weitere Informationen zum Datencenter-Aktivierungskoordinierungsmodus finden Sie unter [Datencenter-Aktivierungsmodus](datacenter-activation-coordination-mode-exchange-2013-help.md).
    
      - **Alternativer Zeugenserver und alternatives Zeugenverzeichnis**   Der alternative Zeugenserver und das alternative Zeugenverzeichnis sind Werte, die Sie im Rahmen der Planung eines Datencenterswitchovers vorkonfigurieren können. Diese beziehen sich auf den Zeugenserver und das Zeugenverzeichnis, die verwendet werden, wenn ein Datencenterswitchover durchgeführt wurde.
    
      - **Replikationsport**   Alle DAGs verwenden standardmäßig TCP-Port 64327 für die fortlaufende Replikation. Sie können mit dem Parameter *ReplicationPort* des Cmdlets [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) einen anderen TCP-Port für die DAG konfigurieren.
    
      - **Netzwerkerkennung**   Sie können eine erneute Erkennung von Netzwerken und Netzwerkschnittstellen durch die DAG erzwingen. Dieser Vorgang wird verwendet, wenn Sie Netzwerke hinzufügen oder entfernen oder neue Subnetze einführen. Eine erneute Erkennung aller DAG-Netzwerke können Sie mit dem Parameter *DiscoverNetworks* des Cmdlets [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) erzwingen.
    
      - **Netzwerkkomprimierung**   Standardmäßig verwenden DAGs eine Komprimierung nur zwischen DAG-Netzwerken im unterschiedlichen Subnetzen. Sie können die Komprimierung für alle DAG-Netzwerke oder nur für Seedingvorgänge aktivieren, oder Sie können die Komprimierung für alle DAG-Netzwerke deaktivieren.
    
      - **Netzwerkverschlüsselung**   Standardmäßig verwenden DAGs eine Verschlüsselung nur zwischen DAG-Netzwerken im unterschiedlichen Subnetzen. Sie können die Verschlüsselung für alle DAG-Netzwerke oder nur für Seedingvorgänge aktivieren, oder Sie können die Verschlüsselung für alle DAG-Netzwerke deaktivieren.

  - **Herunterfahren von DAG-Mitgliedern**   Die Exchange 2013-Lösung für hohe Verfügbarkeit ist in den Prozess für das Herunterfahren von Windows integriert. Wenn ein Administrator oder eine Anwendung das Herunterfahren eines Windows-Servers in einer DAG mit einer eingebundenen Datenbank initiiert, die an eine oder mehrere DAG-Mitglieder repliziert wird, versucht das System, eine andere Kopie der eingebundenen Datenbanken zu aktivieren, bevor der Server heruntergefahren werden kann. Dieses neue Verhalten gewährleistet jedoch keine verlustfreie Aktivierung aller Datenbanken auf dem Server, der heruntergefahren wird. Aus diesem Grund sollte vor dem Herunterfahren eines Servers, der Mitglied einer DAG ist, ein Serverswitchover durchgeführt werden.

Genaue Anweisungen zum Erstellen einer DAG finden Sie unter [Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md). Ausführliche Anweisungen zum Konfigurieren von DAGs und deren Eigenschaften finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md). Informationen zu den oben beschriebenen Verwaltungstasks und zur allgemeinen Verwaltung von DAGs finden Sie unter [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verwaltung von Postfachdatenbankkopien

Die Verwaltung von Postfachdatenbankkopien umfasst die folgenden Tasks:

  - **Hinzufügen von Postfachdatenbankkopien**   Wenn Sie eine Kopie einer Postfachdatenbank hinzufügen, wird automatisch die fortlaufende Replikation zwischen der vorhandenen Datenbank und der Datenbankkopie aktiviert.

  - **Konfigurieren von Eigenschaften für Postfachdatenbankkopien**   Sie können eine Vielzahl von Eigenschaften konfigurieren, beispielsweise die Richtlinie zur Datenbankaktivierung, die Dauer (falls gewünscht) der Wiedergabeverzögerung und Abschneideverzögerung und die Aktivierungseinstellung für die Datenbankkopie.

  - **Anhalten oder Fortsetzen einer Postfachdatenbankkopie**   Sie können eine Postfachdatenbankkopie als Vorbereitung für das Seeding oder im Rahmen anderer Wartungsaufgaben anhalten oder fortsetzen. Sie können eine Postfachdatenbank auch nur für die Aktivierung anhalten. Diese Konfiguration hindert das System an einer automatischen Aktivierung der Kopie nach einem Fehler, ermöglicht es dem System jedoch, die Datenbankkopie durch Protokollversand und -wiedergabe auf dem neuesten Stand zu halten.

  - **Aktualisieren einer Postfachdatenbankkopie**   Als Aktualisierung oder *Seeding* wird der Vorgang bezeichnet, bei dem eine Kopie einer Postfachdatenbank einem anderen Postfachserver hinzugefügt wird. Diese wird zur Basisdatenbank für die Kopie. Nach dem ersten Seeding der Basisdatenbankkopie muss für die Datenbank nur in seltenen Fällen ein erneutes Seeding durchgeführt werden.

  - **Aktivieren einer Postfachdatenbankkopie**   Als Aktivierung einer Postfachdatenbankkopie wird die Zuweisung einer bestimmten passiven Kopie als neue aktive Kopie einer Postfachdatenbank bezeichnet. Dieser Vorgang wird auch *Switchover* genannt. Weitere Informationen finden Sie im Abschnitt "Switchover und Failover" weiter unten in diesem Thema.

  - **Entfernen einer Postfachdatenbankkopie**   Sie können eine Postfachdatenbankkopie jederzeit entfernen. Gelegentlich kann es erforderlich sein, eine Postfachdatenbankkopie zu entfernen. Sie können beispielsweise einen Postfachserver erst aus einer DAG entfernen, wenn Sie alle Postfachdatenbankkopien vom Server entfernt haben. Darüber hinaus müssen Sie alle Kopien einer Postfachdatenbank entfernen, bevor Sie den Pfad für eine Postfachdatenbank ändern können.

Ausführliche Anweisungen zum Hinzufügen einer Kopie einer Postfachdatenbank finden Sie unter [Hinzufügen einer Kopie einer Postfachdatenbank](add-a-mailbox-database-copy-exchange-2013-help.md). Ausführliche Anweisungen zum Konfigurieren von Postfachdatenbankkopien finden Sie unter [Konfigurieren der Eigenschaften von Postfachdatenbankkopien](configure-mailbox-database-copy-properties-exchange-2013-help.md). Informationen zu den oben beschriebenen Verwaltungstasks und zur allgemeinen Verwaltung von Postfachdatenbankkopien finden Sie unter [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md). Ausführliche Anweisungen zum Entfernen einer Kopie einer Postfachdatenbank finden Sie unter [Entfernen einer Postfachdatenbankkopie](remove-a-mailbox-database-copy-exchange-2013-help.md).

Zurück zum Seitenanfang

## Proaktive Überwachung

Die wichtigsten Ziele im Rahmen der täglichen Verwaltung sind, dass Ihre Server zuverlässig arbeiten und dass sich Ihre Datenbankkopien in einem fehlerfreien Zustand befinden. Exchange 2013 umfasst zahlreiche Funktionen, die zur Durchführung vielfältiger Statusüberprüfungen für DAGs und Postfachdatenbankkopien genutzt werden können. Hierzu zählen:

  - [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\))

  - [Test-ReplicationHealth](https://technet.microsoft.com/de-de/library/bb691314\(v=exchg.150\))

  - Crimson-Kanal-Ereignisprotokollierung

Zusätzlich zur Überwachung von Integrität und Status ist auch eine Überwachung auf Situationen wichtig, die die Verfügbarkeit gefährden können. Es wird beispielsweise empfohlen, die Redundanz Ihrer replizierten Datenbanken zu überwachen. Wichtig ist auch die Vermeidung von Situationen, in denen nur noch eine einzige Kopie einer Datenbank verfügbar ist. Dieses Szenario muss mit höchster Priorität behandelt werden und schnellstmöglich korrigiert werden.

Weitere ausführliche Informationen zur Überwachung der Integrität und des Status von DAGs und Postfachdatenbankkopien finden Sie unter [Überwachen von Datenbankverfügbarkeitsgruppen](monitoring-database-availability-groups-exchange-2013-help.md).

Zurück zum Seitenanfang

## Switchover und Failover

Als *Switchover* wird der Vorgang bezeichnet, bei dem ein Administrator eine oder mehrere Postfachdatenbankkopien manuell aktiviert. Ein Switchover kann auf Datenbank- oder Serverebene durchgeführt werden und erfolgt üblicherweise im Rahmen der Vorbereitung von Wartungsaktivitäten. Die Switchoververwaltung umfasst nach Bedarf das Ausführen von Switchovervorgängen auf Datenbank- oder Serverebene. Wenn Sie beispielsweise Wartungsarbeiten an einem Postfachserver in einer DAG durchführen müssen, führen Sie zunächst einen Serverswitchover durch, sodass der Server keine aktiven Postfachdatenbankkopien hostet. Genaue Anweisungen zum Durchführen eines Datenbankswitchovers finden Sie unter [Aktivieren einer Kopie einer Postfachdatenbank](activate-a-mailbox-database-copy-exchange-2013-help.md). Switchovervorgänge können auch auf Datencenterebene durchgeführt werden.

Ein *Failover* ist die automatische Aktivierung einer oder mehrerer Datenbankkopien durch das System als Reaktion auf einen Ausfall. Beispielsweise löst der Ausfall eines Festplattenlaufwerks in einer RAID-freien Umgebung ein Datenbankfailover aus. Der Verlust des MAPI-Netzwerks oder ein Stromausfall lösen ein Serverfailover aus.

Zurück zum Seitenanfang

