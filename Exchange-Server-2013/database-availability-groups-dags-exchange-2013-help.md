---
title: 'Database Availability Groups (DAGs): Exchange 2013 Help'
TOCTitle: Database Availability Groups (DAGs)
ms:assetid: ab9b88ce-2f44-4334-96ad-a666b95888a0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979799(v=EXCHG.150)
ms:contentKeyID: 50476449
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Database Availability Groups (DAGs)

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-06-04_

Informationen zu Exchange DAG in Exchange Server 2013. Dieser Artikel beschreibt den DAG-Lebenszyklus (Database Availability Group) sowie das Verwenden einer DAG für hohe Verfügbarkeit und Ausfallsicherheit.

Eine Database Availability Group (DAG) ist die Basiskomponente des Frameworks für Postfachserver für hohe Verfügbarkeit und Ausfallsicherheit für Standorte in Microsoft Exchange Server 2013. Eine DAG besteht aus bis zu 16 Postfachservern, die einen Gruppe von Datenbanken hosten und eine automatische Wiederherstellung auf Datenbankebene nach Fehlern bieten, die einzelne Server oder Datenbanken betreffen.

Eine DAG stellt eine Abgrenzung für die Replikation der Postfachdatenbank, für Datenbank- und Serverswitchover und für Failover sowie für eine interne Komponente namens *Active Manager* dar. Active Manager, der auf jedem Postfachserver ausgeführt wird, verwaltet Switchover und Failover in DAGs. Weitere Informationen zu Active Manager finden Sie in [Active Manager](active-manager-exchange-2013-help.md).

Jeder Server in einer DAG kann als Host für eine Kopie einer Postfachdatenbank eines beliebigen anderen Servers in der DAG fungieren. Wenn einer DAG ein Server hinzugefügt wird, wird dieser mit den anderen Servern in der DAG eingesetzt, um eine automatische Wiederherstellung nach Fehlern zu bieten, die Postfachdatenbanken betreffen, z. B. Datenträger-, Server- oder Netzwerkfehler.

**Inhalt**

DAG-Lebenszyklus (Database Availability Group)

Verwenden einer DAG (Database Availability Group) für hohe Verfügbarkeit

Verwenden einer DAG (Database Availability Group) für Standortausfallsicherheit

## DAG-Lebenszyklus (Database Availability Group)

Für DAGs wird das Konzept der *inkrementellen Bereitstellung* genutzt. Hierbei handelt es sich um die Fähigkeit, die Dienst- und Datenverfügbarkeit für alle Postfachserver und Datenbanken bereitstellen zu können, nachdem Exchange installiert wurde. Nachdem Sie Exchange 2013-Postfachserver bereitgestellt haben, können Sie eine DAG erstellen, dieser Postfachserver hinzufügen und anschließend Postfachdatenbanken zwischen den DAG-Mitgliedern replizieren.


> [!NOTE]
> Es ist möglich, eine DAG zu erstellen, die eine Kombination aus physischen und virtualisierten Postfachservern enthält, sofern die Server und Lösung <A href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange&nbsp;2013 – Systemanforderungen</A> sowie den in <A href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013-Virtualisierung</A> festgelegten Anforderungen entsprechen. Wie bei allen Exchange-Hochverfügbarkeitskonfigurationen müssen Sie sicherstellen, dass alle Postfachserver in der DAG groß genug sind, um die erforderliche Arbeitslast während geplanter und ungeplanter Ausfälle zu verarbeiten.



Eine DAG wird mithilfe des Cmdlets [New-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351107\(v=exchg.150\)) erstellt. Eine DAG wird zunächst als leeres Objekt in Active Directory erstellt. Das Verzeichnisobjekt dient zum Speichern relevanter Informationen über die DAG, beispielsweise Servermitgliedschaftsinformationen und einige DAG-Konfigurationseinstellungen. Wenn Sie der DAG den ersten Server hinzufügen, wird automatisch ein Failovercluster für die DAG erstellt. Dieser Failovercluster wird ausschließlich von der DAG verwendet und muss ihr dediziert zugeordnet werden. Die Verwendung des Clusters für andere Zwecke wird nicht unterstützt.

Zusätzlich zur Erstellung eines Failoverclusters wird die Infrastruktur zur Überwachung der Server auf Netzwerk- oder Serverfehler initiiert. Der Failovercluster-Taktmechanismus und die Clusterdatenbank werden dann zum Verfolgen und Verwalten von Informationen zur DAG verwendet, die sich schnell ändern können, wie beispielsweise Datenbankeinbindungsstatus, Replikationsstatus und Standort der letzten Einbindung.

Während der Erstellung erhält die DAG einen eindeutigen Namen und ihr wird mindestens eine statische IP-Adresse zugeordnet, sofern sie nicht für die Verwendung von DHCP (Dynamic Host Configuration Protocol) konfiguriert wird oder ohne Cluster-Administratorzugriffspunkt erstellt wurde. DAGs ohne Cluster-Administratorzugriffspunkt können nur auf Servern erstellt werden, auf denen Exchange 2013 Service Pack 1 oder neuer auf Windows Server 2012 R2 Standard oder Datacenter Edition ausgeführt wird. DAGs ohne Cluster-Administratorzugriffspunkt haben folgende Eigenschaften:

  - Es sind keine IP-Adressen zu Cluster/DAG zugewiesen, und daher befindet sich keine IP-Adressenressource in der Cluster-Hauptressourcengruppe.

  - Es ist kein Netzwerkname zum Cluster zugewiesen, und daher befindet sich keine Netzwerknamensressource in der Cluster-Hauptressourcengruppe

  - Der Name von Cluster/DAG ist nicht in DNS registriert, und kann innerhalb des Netzwerks nicht aufgelöst werden.

  - Ein Clusternamensobjekt (CNO) wird nicht in Active Directory erstellt.

  - Der Cluster kann nicht über die Failoverclusterverwaltung verwaltet werden. Er muss über Windows PowerShell verwaltet werden, und die PowerShell-Cmdlets müssen für die einzelnen Cluster-Mitglieder ausgeführt werden.

In diesem Beispiel wird gezeigt, wie über die Shell eine DAG mit Cluster-Administratorzugriffspunkt erstellt werden kann, die drei Server hat. Zwei der Server (EX1 und EX2) befinden sich im selben Subnetz (10.0.0.0), der dritte Server (EX3) befindet sich in einem anderen Subnetz (192.168.0.0).

    New-DatabaseAvailabilityGroup -Name DAG1 -WitnessServer EX4 -DatabaseAvailabilityGroupIPAddresses 10.0.0.5,192.168.0.5
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX1
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX2
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX3

Die Befehle, um eine DAG ohne Cluster-Administratorzugriffspunkt zu erstellen, sind ähnlich:

    New-DatabaseAvailabilityGroup -Name DAG1 -WitnessServer EX4 -DatabaseAvailabilityGroupIPAddresses ([System.Net.IPAddress])::None
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX1
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX2
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer EX3

Der Cluster für DAG1 wird erstellt, wenn EX1 der DAG hinzugefügt wird. Während der Clustererstellung ruft das Cmdlet **Add-DatabaseAvailabilityGroupServer** die für die DAG konfigurierten IP-Adressen ab und ignoriert dabei alle Adressen, die nicht mit einem der Subnetze auf EX1 übereinstimmen. Im ersten Beispiel wird der Cluster für DAG1 mit der IP-Adresse 10.0.0.5 erstellt, die Adresse 192.168.0.5 wird ignoriert. Im zweiten Beispiel oben weist der Wert des *DatabaseAvailabilityGroupIPAddresses*-Parameters die Aufgabe an, ein Failovercluster für die DAG zu erstellen, die keinen Administratorzugriffspunkt hat. Daher wird der Cluster mit einer IP-Adresse oder Netzwerknamensressource in der Cluster-Hauptressourcengruppe erstellt.

Anschließend wird EX2 hinzugefügt, und das Cmdlet **Add-DatabaseAvailabilityGroupServer** ruft wieder die für die DAG konfigurierten IP-Adressen ab. Es gibt keine Änderungen an den IP-Adressen des Clusters, da EX2 sich im selben Subnetz befindet wie EX1.

Danach wird EX3 hinzugefügt, und das Cmdlet **Add-DatabaseAvailabilityGroupServer** ruft wieder die für die DAG konfigurierten IP-Adressen ab. Da ein Subnetz mit der Adresse 192.168.0.5 auf EX3 vorliegt, wird 192.168.0.5 als IP-Adressressource in der Clustergruppe hinzugefügt. Zusätzlich wird automatisch eine **OR**-Abhängigkeit für die Netzwerknamenressource jeder IP-Adressressource konfiguriert. Die Adresse 192.168.0.5 wird vom Cluster verwendet, wenn die Cluster-Hauptressourcengruppe auf EX3 verschoben wird.

für DAGs mit Cluster-Administratorzugriffspunkten werden beim Windows-Failoverclustering die IP-Adressen für den Cluster in DNS (Domain Name System) registriert, sobald die Netzwerknamensressource online geschaltet wird. Zudem wird ein Clusternamensobjekt (CNO) in Active Directory erstellt, wenn EX1 zum Cluster hinzugefügt wird. Netzwerkname, IP-Adresse(n) und CNO für den Cluster werden nicht für DAG-Funktionen verwendet. Administratoren und Endbenutzer müssen keine Verbindung zu dem Namen oder der IP-Adresse von Cluster/DAG herstellen. Einige Drittanbieteranwendungen stellen eine Verbindung zum Cluster-Administratorzugriffspunkt her, um Verwaltungsaufgaben wie Sicherung oder Überwachung durchzuführen. Wenn Sie keine Drittanbieteranwendungen verwenden, die einen Cluster-Administratorzugriffspunkt erfordern, und Ihre DAG Exchange 2013 SP1 oder neuer auf Windows Server 2012 R2 ausführt, empfehlen wir die Erstellung einer DAG ohne Administratorzugriffspunkt. Dies vereinfacht die DAG-Konfiguration, verhindert, dass eine oder mehrere IP-Adressen benötigt werden, und reduziert die Angriffsoberfläche einer DAG.

DAGs sind zudem für die Verwendung eines Zeugenservers und eines Zeugenverzeichnisses konfiguriert. Der Zeugenserver und das Zeugenverzeichnis werden entweder automatisch durch das System konfiguriert oder können manuell vom Administrator konfiguriert werden. In den Beispielen oben wird EX4 (ein Server, der kein Mitglied der DAG ist und dies nicht werden wird) manuell als Zeugenserver der DAG konfiguriert.

Standardmäßig ist eine DAG so konzipiert, dass sie die integrierte fortlaufende Replikation zum Replizieren von Postfachdatenbankservern in der DAG verwendet. Wenn Sie eine Drittanbieterlösung für die Datenreplikation verwenden, die die Exchange 2013-API für die Drittanbieterreplikation verwendet, müssen Sie die DAG im Drittanbieter-Replikationsmodus erstellen. Hierzu verwenden Sie das Cmdlet [New-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351107\(v=exchg.150\)) mit dem Parameter *ThirdPartyReplication*. Nachdem dieser Modus aktiviert wurde, kann er nicht mehr deaktiviert werden.

Nachdem die DAG erstellt wurde, können ihr Postfachserver hinzugefügt werden. Wenn der DAG der erste Server hinzugefügt wurde, wird ein Cluster für die DAG gebildet. Für DAGs wird die Windows-Failoverclusteringtechnologie genutzt, so etwa der Clustertakt, Clusternetzwerke und die Clusterdatenbank (zum Speichern von Daten, die sich ändern, beispielsweise Änderungen des Datenbankzustands von "Aktiv" nach "Passiv" oder umgekehrt oder von "Eingebunden" nach "Nicht eingebunden" und umgekehrt). Wird der DAG ein weiterer Server hinzugefügt, wird dieser in den zugrunde liegenden Cluster eingebunden (wobei das Quorummodell des Clusters automatisch von Exchange angepasst wird), und der Server wird dem DAG-Objekt in Active Directory hinzugefügt.

Nachdem Postfachserver einer DAG hinzugefügt wurden, können Sie verschiedene DAG-Eigenschaften konfigurieren, beispielsweise die Verwendung von Netzwerkverschlüsselung oder Netzwerkkomprimierung für die Datenbankreplikation innerhalb der DAG. Sie können außerdem DAG-Netzwerke konfigurieren und zusätzliche DAG-Netzwerke erstellen.

Nachdem Sie einer DAG Mitglieder hinzugefügt und die DAG konfiguriert haben, können die aktiven Postfachdatenbanken auf jedem Server auf die anderen DAG-Mitgliedern repliziert werden. Nach dem Erstellen von Postfachdatenbankkopien können Sie die Integrität und den Status der Kopien mithilfe einer Vielzahl integrierter Überwachungstools überwachen. Zusätzlich können Sie Datenbank- und Serverswitchover durchführen.

Weitere Informationen zum Erstellen von DAGs, zum Verwalten der DAG-Mitgliedschaft, zum Konfigurieren von DAG-Eigenschaften, zum Erstellen und Überwachen von Postfachdatenbankkopien und zum Durchführen eines Switchover finden Sie unter [Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte](managing-high-availability-and-site-resilience-exchange-2013-help.md).

## DAG-Quorummodelle (Database Availability Group)

Jeder DAG untergeordnet ist ein Windows-Failovercluster. Für Failovercluster gilt das Quorumkonzept. Hierbei wird eine Übereinstimmung von Wählern verwendet, um sicherzustellen, dass nur eine Teilmenge der Clustermitglieder (also entweder alle oder eine Mehrheit der Mitglieder) gleichzeitig funktionieren. Das Quorumkonzept ist keine neue Funktion von Exchange 2013. Auch hoch verfügbare Postfachserver in früheren Exchange-Versionen arbeiten mit Failoverclustern und dem dazugehörigen Quorumkonzept. Quorum steht für eine freigegebene Ansicht von Mitgliedern und Ressourcen, und der Begriff "Quorum" beschreibt außerdem die physischen Daten, welche die von allen Clustermitgliedern gemeinsam genutzte Konfiguration innerhalb des Clusters darstellen. Demzufolge erfordern alle DAGs, dass ihre zugrunde liegenden Failovercluster das Quorum besitzen. Wenn der Cluster das Quorum verliert, werden alle DAG-Operationen beendet, und die Bereitstellung aller in der DAG gehosteten Datenbanken wird aufgehoben. In diesem Fall ist ein Eingriff durch den Administrator erforderlich, um das Quorumproblem zu beheben und die DAG-Vorgänge wiederherzustellen.

Das Quorum dient zum Sicherstellen von Konsistenz, zum Lösen von Konflikten zur Vermeidung von Aufteilungen und zum Gewährleisten der Reaktionsfähigkeit des Clusters:

  - **Sicherstellen von Konsistenz**   Eine Hauptanforderung an ein Windows-Failovercluster ist, dass alle seine Mitglieder stets über eine Ansicht des Clusters verfügen, die mit den anderen Mitgliedern konsistent ist. Die Clusterstruktur dient als definitiver Datenspeicher aller Konfigurationsinformationen zum Cluster. Wenn die Clusterstruktur für ein DAG-Mitglied nicht lokal geladen werden kann, wird der Clusterdienst nicht gestartet, da er nicht gewährleisten kann, dass das Mitglied die Anforderung einer Ansicht des Clusters erfüllt, die mit den anderen Mitgliedern konsistent ist.

  - **Lösen von Konflikten**   Eine Quorumzeugenressource dient in DAGs mit einer geraden Anzahl von Mitgliedern zum Vermeiden des sog. Split Brain-Syndroms und zum Sicherstellen, dass nur eine Sammlung der Mitglieder in der DAG als "offiziell" angesehen wird. Wenn der Zeugenserver für das Quorum benötigt wird, können alle Mitglieder der DAG, die mit dem Zeugenserver kommunizieren können, eine SMB-Sperre (Server Message Block) für die Datei **witness.log** des Zeugenservers aktivieren. Das DAG-Mitglied, das den Zeugenserver sperrt (und als *Sperrknoten* bezeichnet wird), erhält für Quorumzwecke eine zusätzliche Stimme. Die DAG-Mitglieder in Kontakt mit dem Sperrknoten sind in der Mehrheit und behalten das Quorum. DAG-Mitglieder, die den Sperrknoten nicht kontaktieren können, sind in der Minderheit und verlieren deshalb das Quorum.

  - **Sicherstellen der Reaktionsfähigkeit**   Zum Sicherstellen der Reaktionsfähigkeit gewährleistet das Quorummodell, dass bei jeder Ausführung des Clusters genügend Mitglieder des verteilten Systems betriebs- und kommunikationsbereit sind und mindestens ein Replikat des aktuellen Zustands des Clusters garantiert werden kann. Es ist kein weiterer Aufwand erforderlich, um Mitglieder in Kommunikation miteinander zu bringen oder festzustellen, ob ein bestimmtes Replikat garantiert ist.

DAGs mit einer geraden Anzahl von Mitgliedern verwenden den Quorummodus **Knoten- und Dateifreigabemehrheit** des Failoverclusters, der zum Lösen von Konflikten mit einem externen Zeugenserver arbeitet. In diesem Quorummodus erhält jedes DAG-Mitglied eine Stimme. Außerdem wird einem DAG-Mitglied anhand des Zeugenservers eine gewichtige Stimme bereitgestellt (z. B. erhält es zwei Stimmen statt einer). Die Clusterquorumdaten werden standardmäßig auf den Systemdatenträgern der einzelnen DAG-Mitglieder gespeichert und auf diesen Datenträgern konsistent gehalten. Auf dem Zeugenserver wird hingegen keine Kopie der Quorumdaten gespeichert. In einer Datei auf dem Zeugenserver wird verfolgt, welches Mitglied die aktuelle Kopie der Daten besitzt. Auf dem Zeugenserver liegt jedoch keine Kopie der Clusterquorumdaten vor. In diesem Modus muss eine Mehrheit der Wähler (die DAG-Mitglieder plus Zeugenserver) zum Erhalten des Quorums für den Betrieb und die Kommunikation miteinander bereit sein. Wenn eine Mehrheit der Wähler nicht miteinander kommunizieren kann, verliert das der DAG zugrunde liegende Cluster das Quorum, sodass für die DAG ein Eingriff vonseiten des Administrators erforderlich ist, um wieder betriebsbereit zu werden.

DAGs mit einer ungeraden Anzahl von Mitgliedern verwenden den Quorummodus **Knotenmehrheit** des Clusters. In diesem Modus erhält jedes Mitglied eine Stimme, und der lokale Systemdatenträger der einzelnen Mitglieder dient zum Speichern der Clusterquorumdaten. Wenn sich die Konfiguration der DAG ändert, wird diese Änderung von den verschiedenen Datenträgern übernommen. Die Änderung gilt nur als dauerhaft gespeichert, wenn sie auf den Datenträgern der Hälfte der Mitglieder (nach Abrundung) plus eins erfolgt ist. Bei einer DAG mit fünf Mitgliedern muss diese Änderung beispielsweise bei zwei plus ein Mitglied bzw. insgesamt drei Mitgliedern erfolgt sein.

Das Quorum erfordert, dass eine Mehrheit der Wähler miteinander kommunizieren kann. Angenommen, eine DAG hat vier Mitglieder. Da diese DAG eine gerade Mitgliederanzahl umfasst, wird einem der Clustermitglieder von einem externer Zeugenserver eine fünfte Stimme zum Lösen von Konflikten bereitgestellt. Um eine Mehrheit der Wähler (und demzufolge das Quorum) zu erhalten, müssen mindestens drei Wähler miteinander kommunizieren können. Maximal zwei Wähler können offline sein, ohne dass der Dienst- und Datenzugriff unterbrochen wird. Wenn drei oder mehr Wähler offline sind, verliert die DAG das Quorum, sodass der Dienst- und Datenzugriff so lange unterbrochen wird, bis das Problem behoben ist.

Zurück zum Seitenanfang

## Verwenden einer DAG (Database Availability Group) für hohe Verfügbarkeit

Das nachfolgende Beispiel soll veranschaulichen, wie eine DAG eine hohe Verfügbarkeit für Ihre Postfachdatenbanken sicherstellen kann. Im Beispiel wird eine DAG mit fünf Mitgliedern verwendet. Diese DAG wird in der folgenden Abbildung dargestellt.

**DAG mit fünf Mitgliedern**

![Database Availability Group (DAG)](images/Dd979799.21fcbf7b-cb10-49c0-8e32-bdf3c03f825d(EXCHG.150).gif "Database Availability Group (DAG)")

In der vorstehenden Abbildung handelt es sich bei den grün dargestellten Datenbanken um aktive Postfachdatenbankkopien, die blau dargestellten Datenbanken sind passive Postfachdatenbankkopien. In diesem Beispiel werden die Datenbankkopien nicht auf jedem Server gespiegelt, sondern über mehrere Server verteilt. Auf diese Weise wird sichergestellt, dass keine zwei Server in der DAG über denselben Satz von Datenbankkopien verfügen. Auf diese Weise wird mehr Ausfallsicherheit für die DAG erzielt, wenn beispielsweise andere Komponenten aufgrund von Wartungsarbeiten nicht verfügbar sind.

Im folgenden Szenario wird anhand der zuvor genannten Beispiel-DAG die Ausfallsicherheit im Falle verschiedener Datenbank- und Serverfehler veranschaulicht.

Zunächst arbeiten alle Datenbanken und Server fehlerfrei. Sie müssen auf EX2 einige Betriebssystemupdates installieren. Dazu müssen Sie den Server im Wartungsmodus ausführen. Dadurch wird ein Serverswitchover ausgelöst, wodurch die Kopie von DB4 auf einem anderen Postfachserver aktiviert wird. Ein Serverswitchover wird durchführt, um alle aktiven Postfachdatenbankkopien vom aktuellen Server auf einen oder mehrere andere Postfachserver in der DAG zu verschieben, um den aktuellen Server auf einen geplanten Ausfall vorzubereiten. In diesem Beispiel gibt es nur eine aktive Postfachdatenbank auf EX2 (DB4), weshalb nur eine aktive Postfachdatenbankkopie verschoben wird.

**DAG mit einem Server, der zur Wartung offline geschaltet wurde**

![Database Availability Group (DAG) mit einem Offlineserver](images/Dd979799.f48f0e77-80e1-4f14-8c36-112393895bdc(EXCHG.150).gif "Database Availability Group (DAG) mit einem Offlineserver")

Während Sie die Wartungsarbeiten auf EX2 durchführen, kommt es auf EX3 zu einem schweren Hardwarefehler, sodass EX3 offline geht. Vor dem Ausfall von EX3 wurde die aktive Kopie von DB2 gehostet. Zur Wiederherstellung aktiviert das System innerhalb von 30 Sekunden automatisch die Kopie von DB2, die auf EX1 gehostet wird. Dieser Vorgang wird in der folgenden Abbildung dargestellt.

**DAG mit einem zur Wartung offline geschalteten Server und einem ausgefallenen Server**

![DAG mit einem Offlineserver und einem ausgefallenen Server](images/Dd979799.9bbfd9e7-3881-4957-ae8d-32318cbc208b(EXCHG.150).gif "DAG mit einem Offlineserver und einem ausgefallenen Server")

Nachdem die geplanten Wartungsarbeiten auf EX2 abgeschlossen wurden, schalten Sie den Server wieder online und nehmen ihn aus dem Wartungsmodus. Sobald EX2 wieder verfügbar ist, werden die weiteren Mitglieder der DAG benachrichtigt, und die Kopien von DB1, DB4 und DB5, die auf EX2 gehostet werden, werden automatisch mit der aktiven Kopie jeder Datenbank synchronisiert. Dieser Vorgang wird in der folgenden Abbildung dargestellt.

**DAG mit einem wiederhergestellten Server, dessen Datenbankkopien synchronisiert werden**

![DAG mit wiederhergestelltem Server und erneuter Synchronisierung der Datenbanken](images/Dd979799.58601531-e078-41d3-9287-e8e470ef7f41(EXCHG.150).gif "DAG mit wiederhergestelltem Server und erneuter Synchronisierung der Datenbanken")

Nachdem die ausgefallene Hardwarekomponente auf EX3 durch eine neue Komponente ersetzt wurde, wird EX3 online geschaltet. Sobald EX3 wieder verfügbar ist, werden die weiteren Mitglieder der DAG benachrichtigt, und die auf EX3 gehostet Kopien von DB2, DB3 und DB4 werden automatisch mit der aktiven Kopie jeder Datenbank synchronisiert. Dieser Vorgang wird in der folgenden Abbildung dargestellt.

**DAG mit einem repariertem Server, dessen Datenbankkopien synchronisiert werden**

![DAG mit Mitglied und erneuter Synchronisierung der Datenbankkopien](images/Dd979799.56259671-e840-4cf0-9ea2-3657dc36c035(EXCHG.150).gif "DAG mit Mitglied und erneuter Synchronisierung der Datenbankkopien")

Zurück zum Seitenanfang

## Verwenden einer DAG (Database Availability Group) für Standortausfallsicherheit

Zusätzlich zur Bereitstellung einer hohen Verfügbarkeit innerhalb eines Datencenters kann eine DAG auch auf ein oder mehrere Datencenter in einer Konfiguration ausgeweitet werden, die Ausfallsicherheit für ein oder mehrere Datencentern bietet. In den vorherigen Beispielabbildungen befindet sich die DAG in einem einzelnen Datencenter und an einem einzelnen Active Directory-Standort. Durch inkrementelle Bereitstellung kann diese DAG auf ein zweites Datencenter (und einen zweiten Active Directory-Standort) ausgeweitet werden, indem ein Postfachserver und die nötigen unterstützenden Ressourcen (mindestens ein Active Directory-Server sowie DNS-Dienste) bereitgestellt werden. Anschließend wird der Postfachserver, wie in der folgenden Abbildung dargestellt, der DAG hinzugefügt.

**Auf zwei Active Directory-Standorte erweiterte DAG**

![Auf zwei Active Directory-Standorte erweiterte DAG](images/Dd979799.28e96e9d-d7d6-451a-b7b8-c06122c81dc9(EXCHG.150).gif "Auf zwei Active Directory-Standorte erweiterte DAG")

In diesem Beispiel wird eine passive Kopie jeder aktiven Datenbank im Datencenter **Redmond** auf EX6 im Datencenter **Dublin** konfiguriert. Es gibt jedoch zahlreiche andere Beispiele für DAG-Konfigurationen, die für Ausfallsicherheit sorgen. Beispiel:

  - Anstatt nur passive Datenbankkopien zu hosten, kann EX6 alle aktiven Kopien oder eine Kombination aus aktiven und passiven Kopien hosten.

  - Zusätzlich zu EX6 können mehrere DAG-Mitglieder im Datencenter **Dublin** bereitgestellt werden, um weiteren Ausfallschutz zu bieten. Diese Konfiguration bietet zudem weitere Kapazität, sodass bei einem Ausfall des Datencenters **Redmond** das Datencenter **Dublin** weitaus mehr Benutzer unterstützen kann.

## Verwenden mehrerer DAGs (Database Availability Groups) für Standortausfallsicherheit

Im vorherigen Beispiel wurde eine DAG auf mehrere Datencenter ausgedehnt, um Ausfallsicherheit für ein oder beide Datencenter zu bieten. Bei Verwenden einer einzelnen DAG zum Bereitstellen von Ausfallsicherheit in einer Umgebung, in der jedes Datencenter, auf das Sie die DAG ausdehnen, einen aktiven Benutzerbestand hat, stellt die WAN-Verbindung eine einzelne Fehlerquelle dar. Aus diesem Grund erfordert das Quorum, dass eine Mehrheit der Wähler aktiv ist und miteinander kommunizieren kann.

Im vorherigen Beispiel befindet sich die Mehrheit der Wähler im Datencenter **Redmond**. Wenn das Datencenter **Dublin** aktive Postfachdatenbanken hostet und über einen lokalen Benutzerbestand verfügt, führt ein WAN-Ausfall zum Ausfall des Messagingsdiensts für die Benutzer in Dublin. Bei Unterbrechung der WAN-Verbindung behalten nur die DAG-Mitglieder im Datencenter **Redmond** das Quorum und stellen den Messagingdienst weiter zur Verfügung.

Zum Vermeiden, dass das WAN eine einzelne Fehlerquelle darstellt, wenn Sie Ausfallsicherheit für mehrere Datencenter mit aktivem Benutzerbestand bereitstellen müssen, ist es erforderlich, mehrere DAGs bereitzustellen, wobei jede DAG über eine Mehrheit der Wähler in einem separaten Datencenter verfügt. Bei einem WAN-Ausfall wird die Replikation so lange blockiert, bis die Verbindung wiederhergestellt ist. Die Benutzer können den Messagingdienst nutzen, da jede DAG weiter für ihren lokalen Benutzerbestand aktiv ist.

Zurück zum Seitenanfang

