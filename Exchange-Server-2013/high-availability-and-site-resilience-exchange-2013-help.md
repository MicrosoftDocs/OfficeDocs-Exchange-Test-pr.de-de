---
title: 'Hohe Verfügbarkeit und Ausfallsicherheit von Standorten: Exchange 2013 Help'
TOCTitle: Hohe Verfügbarkeit und Ausfallsicherheit von Standorten
ms:assetid: 6628285e-d07c-443d-866b-be784ad1ed1e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638137(v=EXCHG.150)
ms:contentKeyID: 50475848
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hohe Verfügbarkeit und Ausfallsicherheit von Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-15_

Sie können Ihre Exchange Server 2013-Postfachdatenbanken und die darin enthaltenen Daten schützen, indem Sie Ihre Postfachdatenbanken für hohe Verfügbarkeit und Ausfallsicherheit für Standorte konfigurieren. Exchange 2013 senkt die Kosten und Komplexität für die Bereitstellung einer hochverfügbaren und ausfallsicheren Messaginglösung auf ein Minimum und bietet gleichzeitig hohe Dienst- und Datenverfügbarkeit sowie Unterstützung für sehr große Postfächer.

Exchange 2010 baut auf den systemeigenen Replikationsfunktionen und der Architektur für hohe Verfügbarkeit auf, die von Exchange 2013 eingeführt werden, wodurch Kunden beliebiger Größe und aus allen Sparten die Möglichkeit erhalten, einen Dienst zur Aufrechterhaltung des Messagings im Unternehmen kostengünstig bereitzustellen. Eine Liste der Änderungen über Exchange 2010 und Exchange 2007 finden Sie unter [Änderungen bei hoher Verfügbarkeit und Ausfallsicherheit im Vergleich zu früheren Versionen](changes-to-high-availability-and-site-resilience-over-previous-versions-exchange-2013-help.md).

**Inhalt**

Wichtige Terminologie

Datenbankverfügbarkeitsgruppen (DAGs)

Postfachdatenbankkopien

Active Manager

Ausfallsicherheit von Standorten

API für die Drittanbieterreplikation

Dokumentation zu Hochverfügbarkeit und Ausfallsicherheit für Standorte

## Wichtige Terminologie

Nachfolgend werden die wichtigsten Begriffe zum Verständnis von Hochverfügbarkeit und Ausfallsicherheit von Standorten erläutert:

  - *Active Manager*  
    Eine interne Exchange-Komponente, die im Microsoft Exchange-Replikationsdienst ausgeführt wird. Sie überwacht die Umgebung auf Ausfälle und führt Korrekturmaßnahmen aus, indem ein Failover innerhalb einer Database Availability Group (DAG) durchgeführt wird.

<!-- end list -->

  - *AutoDatabaseMountDial*  
    Eine Eigenschafteneinstellung eines Postfachservers, die basierend auf der Anzahl von fehlenden Protokolldateien für die einzubindende Kopie festlegt, ob eine passive Datenbankkopie automatisch als neue aktive Kopie eingebunden wird.

<!-- end list -->

  - *Fortlaufende Replikation – Blockmodus*  
    Im Blockmodus wird beim Schreiben jeder Aktualisierung in den aktiven Protokollpuffer der aktiven Datenbankkopie diese auch in einen Protokollpuffer aller passiven Postfachkopien übertragen. Sobald der Protokollpuffer voll ist, führt jede Datenbankkopie eine Überprüfung durch und erstellt dann die nächste Protokolldatei in der Generierungssequenz.

<!-- end list -->

  - *Fortlaufende Replikation – Dateimodus*  
    Im Dateimodus werden geschlossene Transaktionsprotokolldateien von der aktiven Datenbankkopie per Pushvorgang in eine oder mehrere passive Datenbankkopien kopiert.

<!-- end list -->

  - *Database Availability Group (DAG)*  
    Eine Gruppe von bis zu 16 Exchange 2013-Postfachservern, die eine Gruppe replizierter Datenbanken hostet.

<!-- end list -->

  - *Datenbankmobilität*  
    Die Fähigkeit, eine Exchange 2013-Postfachdatenbank zu replizieren und auf anderen Exchange 2013-Postfachservern einzubinden.

<!-- end list -->

  - *Datencenter*  
    In der Regel bezieht sich dieser Begriff auf einen Active Directory-Standort, es kann jedoch auch ein physischer Standort gemeint sein. Im Rahmen dieser Dokumentation entspricht ein Datencenter einem Active Directory-Standort.

<!-- end list -->

  - *Datencenter-Aktivierungsmodus*  
    Eine Eigenschaft der DAG-Einstellung, die bei Aktivierung erzwingt, dass der Microsoft Exchange-Replikationsdienst Berechtigungen zum Einbinden von Datenbanken beim Start erwirbt.

<!-- end list -->

  - *Notfallwiederherstellung*  
    Jeder Prozess zur manuellen Wiederherstellung nach einem Ausfall. Dies kann ein Ausfall sein, der ein einzelnes Element betrifft, oder ein Ausfall, der sich auf einen gesamten physischen Standort auswirkt.

<!-- end list -->

  - *Exchange-API für die Drittanbieterreplikation*  
    Eine mit Exchange bereitgestellte API, welche die Verwendung von Drittanbieterprodukten für die synchrone Replikation von DAGs anstelle einer fortlaufenden Replikation ermöglicht.

<!-- end list -->

  - *Hohe Verfügbarkeit*  
    Eine Lösung, die Dienstverfügbarkeit, Datenverfügbarkeit und eine automatische Wiederherstellung nach Ausfällen sicherstellt, die sich auf den Dienst oder Daten auswirken (z. B. Netzwerk-, Speicher- oder Serverausfall).

<!-- end list -->

  - *Inkrementelle Bereitstellung*  
    Die Fähigkeit zur Bereitstellung von hoher Verfügbarkeit und Ausfallsicherheit für Standorte, nachdem Exchange 2013 installiert wurde.

<!-- end list -->

  - *Verzögerte Postfachdatenbankkopie*  
    Eine passive Postfachdatenbankkopie, für die eine Wiedergabeverzögerung größer null festgelegt ist.

<!-- end list -->

  - *Postfachdatenbankkopie*  
    Eine Postfachdatenbank (EDB-Datei und Protokolle), die entweder aktiv oder passiv ist.

<!-- end list -->

  - *Ausfallsicherheit von Postfächern*  
    Der Name einer einheitlichen Lösung für hohe Verfügbarkeit und Ausfallsicherheit für Standorte in Exchange 2013.

<!-- end list -->

  - *Verwaltete Verfügbarkeit*  
    Ein Satz interner Prozesse bestehend aus Tests, Monitoren und Antwortdiensten, die Überwachung und Hochverfügbarkeit für alle Serverrollen und sämtliche Protokolle bereitstellen.

<!-- end list -->

  - *\*over* (englisch ausgesprochen, "Star over")  
    Abkürzung für *Switchover* und *Failover*. Ein Switchover ist die manuelle Aktivierung einer oder mehrerer Datenbankkopien. Ein Failover ist die automatische Aktivierung einer oder mehrerer Datenbankkopien nach einem Ausfall.

<!-- end list -->

  - *Sicherheitsnetz*  
    Dieses vormals als Transportdumpster bezeichnete Feature ist Bestandteil des Transportdiensts und speichert eine Kopie aller Nachrichten für *X* Tage. Die Standardeinstellung beträgt 2 Tage.

<!-- end list -->

  - *Shadow-Redundanz*  
    Ein Transportserverfeature, das Redundanz für Nachrichten bietet, während diese übertragen werden.

<!-- end list -->

  - *Ausfallsicherheit von Standorten*  
    Eine Konfiguration, mit der die Messaginginfrastruktur auf mehrere Active Directory-Standorte ausgeweitet wird, um bei einem Ausfall einer der Standorte einen unterbrechungsfreien Betrieb für das Messagingsystem zu gewährleisten.

Wichtige Terminologie

## Datenbankverfügbarkeitsgruppen (DAGs)

Eine Database Availability Group (DAG) ist die Basiskomponente des Systems für hohe Verfügbarkeit und Ausfallsicherheit für Standorte in Exchange 2013. Eine DAG besteht aus bis zu 16 Postfachservern, die eine Gruppe von Datenbanken hosten und eine automatische Wiederherstellung auf Datenbankebene nach Ausfällen bieten, die einzelne Datenbanken, Netzwerke oder Server betreffen. Jeder Server in einer DAG kann als Host für eine Kopie einer Postfachdatenbank eines beliebigen anderen Servers in der DAG fungieren. Wenn ein Server einer DAG hinzugefügt wird, wird dieser mit den anderen Servern in der DAG eingesetzt, um eine automatische Wiederherstellung nach Fehlern zu bieten, die Postfachdatenbanken betreffen, z. B. Datenträger- oder Serverfehler. Weitere Informationen zu Database Availability Groups finden Sie unter [Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md).

Wichtige Terminologie

## Postfachdatenbankkopien

Die erstmals in Exchange 2010 eingeführten Funktionen zur Bereitstellung von Hochverfügbarkeit und Ausfallsicherheit für Standorte werden in Exchange 2013 dazu verwendet, Datenbankkopien zu erstellen und zu verwalten. Exchange 2013 nutzt außerdem das Konzept der Datenbankmobilität, die von Exchange verwaltete Failoverfunktion auf Datenbankebene.

Im Rahmen der Datenbankmobilität werden Datenbanken von Servern getrennt und Unterstützung für bis zu 16 Kopien einer einzelnen Datenbank hinzugefügt. Zudem wird eine systemeigene Umgebung für das Erstellen von Kopien einer Datenbank bereitgestellt.

Das Festlegen einer Datenbankkopie als aktive Postfachdatenbank wird als *Switchover* bezeichnet. Wenn ein Fehler auftritt, der eine Datenbank oder den Zugriff auf eine Datenbank beeinträchtigt, und eine neue Datenbank als aktive Kopie festgelegt wird, wird dieser Vorgang als *Failover* bezeichnet. Dieser Vorgang bezieht sich auch auf einen Serverausfall, bei dem ein oder mehrere Server die Datenbank online schalten, die sich zuvor auf dem ausgefallenen Server befunden hat. Wenn entweder ein Switchover oder Failover erfolgt, wird dieses Ereignis von den Exchange 2013-Servern sofort erkannt, und der Client- und Messagingdatenverkehr wird an die neue aktive Datenbank umgeleitet.

Wenn beispielsweise eine aktive Datenbank in einer Database Availability Group aufgrund eines Fehlers der zugrunde liegenden Speicherkomponente ausfällt, führt Active Manager eine automatische Wiederherstellung durch, indem ein Failover auf eine Datenbankkopie auf einem anderen Postfachserver in der Database Availability Group durchgeführt wird. In Exchange 2013 umfasst die verwaltete Verfügbarkeit neue Verhaltensweisen zur Wiederherstellung nach einem Verlust des Protokollzugriffs auf eine Datenbank. Hierzu gehören das Recycling von Anwendungsprozesspools, das Neustarten von Diensten und Servern sowie das Einleiten eines Datenbankfailovers.

Weitere Informationen zu Postfachdatenbankkopien finden Sie unter [Postfachdatenbankkopien](mailbox-database-copies-exchange-2013-help.md).

Wichtige Terminologie

## Active Manager

Exchange 2013 nutzt die in Exchange 2010 eingeführte Active Manager-Komponente zum Verwalten der Integrität von Datenbanken und Datenbankkopien, für Status, fortlaufende Replikation und weitere Aspekte in Bezug auf die Hochverfügbarkeit von Postfachservern. Weitere Informationen zu Active Manager finden Sie in [Active Manager](active-manager-exchange-2013-help.md).

Wichtige Terminologie

## Ausfallsicherheit von Standorten

Obwohl in Exchange 2013 weiterhin DAGs und das Windows-Failoverclustering für die Postfachserverrolle für die Bereitstellung von Hochverfügbarkeit und Ausfallsicherheit für Standorte eingesetzt wird, ist die Ausfallsicherheit für Standorte nicht dieselbe wie in Exchange 2013. Die Ausfallsicherheit für Standorte ist in Exchange 2013 deutlich besser, da sie vereinfacht wurde. Die zugrunde liegenden Architekturänderungen in Exchange 2013 haben erhebliche Auswirkungen auf die Wiederherstellungsaspekte einer Konfiguration zur Ausfallsicherheit von Standorten.

In Exchange 2010 war die Wiederherstellung von Postfach- (DAG) und Clientzugriff (Clientzugriffsserver-Array) eng verknüpft. Bei einem Ausfall von sämtlichen Clientzugriffsservern, der VIP für das Array oder einem Ausfall großer Teile Ihrer DAG war es erforderlich, ein Datencenterswitchover durchzuführen. Dies ist ein gut dokumentierter und im Allgemeinen leicht verständlicher Vorgang, wenngleich die Ausführung Zeit kostet und der Vorgang von einem Benutzer gestartet werden muss.

Wenn Sie in Exchange 2013 aus beliebigen Gründen das Clientzugriffsserver-Array verlieren (z. B. weil das Lastenausgleichsmodul ausfällt), muss kein Datencenterswitchover durchgeführt werden. Mit der richtigen Konfiguration findet ein Failover auf Clientebene statt, und Clients werden automatisch an ein zweites Datencenter umgeleitet, das über funktionierende Clientzugriffsserver verfügt. Diese Clientzugriffsserver leiten die Kommunikation zurück an den Benutzerpostfachserver, der vom Ausfall nicht betroffen ist (da Sie kein Switchover durchgeführt haben). Statt daran zu arbeiten, den Dienst wiederherzustellen, stellt der Dienst sich selbst wieder her, und Sie können sich auf die Behebung des Hauptproblems konzentrieren (z. B. um den Austausch des Lastenausgleichmoduls).

Darüber hinaus wird es durch Änderungen wie z. B. die Vereinfachung von Namespaces, die Konsolidierung von Serverrollen, die Entkopplung von Serverrollenanforderungen der Active Directory-Standorte, die Trennung von Clientzugriffsserver-Array- und DAG-Wiederherstellung sowie Änderungen am Lastenausgleich in Exchange 2013 ab sofort möglich, die Clientzugriffsserver- und DAG-Wiederherstellung zu trennen und automatisch über Standorte hinweg auszuführen. Auf diese Weise werden Szenarien für ein Datencenterfailover unterstützt, wenn Sie über drei Standorte verfügen.

In Exchange 2010 konnten Sie eine DAG über zwei Datencenter hinweg bereitstellen, den Zeugenserver in einem dritten Datencenter hosten und ein Failover für die Postfachserverrolle für beide Datencenter aktivieren. Es gab jedoch kein Failover für die Lösung selbst, da der Namespace für die Nicht-Postfachserverrollen weiterhin manuell geändert werden musste.

In Exchange 2013 muss der Namespace nicht mit der DAG verschoben werden. Exchange nutzt die integrierte Fehlertoleranz des Namespace über mehrere IP-Adressen, Lastenausgleich (und, sofern erforderlich, die Fähigkeit zur Inbetriebnahme und Außerbetriebnahme von Servern). Moderne HTTP-Clients arbeiten automatisch mit dieser Redundanz. Der HTTP-Stack kann mehrere IP-Adressen für einen vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) akzeptieren, und wenn die erste IP-Adresse dauerhaft ausfällt (d. h. eine Verbindung nicht möglich ist), wird die nächste IP-Adresse in der Liste verwendet. Bei einem temporären Fehler (Verbindungsverlust nach dem Einrichten einer Sitzung, beispielsweise aufgrund eines zeitweiligen Fehlers im Dienst, bei dem ein Gerät Pakete verliert und außer Betrieb genommen werden muss), muss der Benutzer möglicherweise den Browser aktualisieren.

Dies bedeutet, dass der Namespace nicht länger eine einzelne Fehlerquelle ist, wie dies in Exchange 2010 der Fall war. In Exchange 2010 ist die womöglich größte einzelne Fehlerquelle im Messagingsystem der Benutzern zugewiesene FQDN, da er die Zieladresse angibt. Im Exchange 2010-Paradigma ist eine Änderung des FQDN-Ziels nicht einfach, da Sie die DNS-Einstellungen ändern und die DNS-Wartezeit berücksichtigen müssen, die in einigen Teilen der Erde sehr hoch liegt. Außerdem werden in Browsern Namencaches verwendet, die Daten typischerweise für 30 Minuten oder mehr zwischenspeichern, und dieser Tatsache muss Rechnung getragen werden.

Eine der Änderungen in Exchange 2013 besteht darin, mehrere Zieladressen für Clients zu ermöglichen. Die Tatsache, dass der Client mehrere Zieladressen verwenden kann (fast alle Clientzugriffsprotokolle in Exchange 2013 sind HTTP-basiert (wie z. B. Outlook, Outlook Anywhere, EAS, EWS, OWA und die Exchange-Verwaltungskonsole), und alle unterstützten HTTP-Clients können mehrere IP-Adressen verwenden), ermöglicht ein Failover auf Clientseite. Sie können DNS so konfigurieren, dass einem Client während der Namensauflösung mehrere IP-Adressen übergeben werden. Der Client fragt "mail.contoso.com" an und erhält beispielsweise zwei oder vier IP-Adressen. Viele der an den Client zurückgegebenen IP-Adressen können jedoch zuverlässig verwenden werden. Dies verbessert den Clientbetrieb, da der Client bei einem Ausfall einer der IP-Adressen weitere IP-Adressen zur Verbindungsherstellung zur Verfügung stehen. Wenn beim Versuch einer Verbindungsherstellung durch den Client ein Fehler auftritt, wartet der Client für etwa 20 Sekunden und versucht es dann mit der nächsten Adresse in der Liste. Wenn also die VIP für das Clientzugriffsserver-Array ausfällt, wird innerhalb von etwa 21 Sekunden eine automatische Clientwiederherstellung durchgeführt.

Hierdurch bieten sich folgende Vorteile:

  - Wenn in Exchange 2010 das Lastenausgleichsmodul im primären Datencenter ausfiel und an diesem Standort kein weiteres Lastenausgleichsmodul verfügbar war, musste ein Datencenterswitchover durchgeführt werden. Wenn in Exchange 2013 das Lastenausgleichsmodul am primären Standort ausfällt, schalten Sie es einfach ab (oder deaktivieren die VIP) und reparieren bzw. ersetzen es. Für Clients, die nicht bereits die VIP im sekundären Datencenter verwenden, wird ein automatisches Failover zur sekundären VIP durchgeführt – ohne Änderung des Namespace und ohne DNS-Änderungen. Dies bedeutet nicht nur, dass Sie keinen Switchover durchführen müssen, sondern auch keine Zeit für die normalerweise mit einem Datencenterswitchover verbundene Wiederherstellung aufwenden müssen. In Exchange 2010 mussten Sie die DNS-Wartezeit berücksichtigen (die empfohlene TTL-Einstellung (Time to Live) lautet 5 Minuten, und es muss eine Failback-URL eingeführt werden). In Exchange 2013 ist dies nicht erforderlich, da Sie ein schnelleres Failover (20 Sekunden) des Namespace zwischen VIPs (Datencentern) durchführen können.

  - Da jetzt ein Failover des Namespace zwischen Datencentern möglich ist, wird zum Erreichen eines Datencenterfailovers lediglich ein Mechanismus für ein datencenterübergreifendes Failover der Postfachserverrolle benötigt. Für ein automatisches Failover der DAG benötigen Sie lediglich eine Lösung, bei der die DAG gleichmäßig auf zwei Datencenter aufgeteilt ist. Anschließend platzieren Sie den Zeugenserver an einem dritten Standort, sodass er von DAG-Mitgliedern beider Datencenter vermittelt werden kann – unabhängig vom Status des Netzwerks zwischen den Datencentern, die die DAG-Mitglieder enthalten. Wenn Sie nur zwei Rechenzentren haben und kein dritter physischer Standort verfügbar ist, können Sie den Zeugenserver auf einen virtuellen Microsoft Azure-Computer platzieren. Weitere Informationen finden Sie unter [Verwenden einer Microsoft Azure-VM als DAG-Zeugenserver](using-a-microsoft-azure-vm-as-a-dag-witness-server-exchange-2013-help.md).

  - In diesem Szenario beschränken sich die Aufgaben des Administrators darauf, das vorliegende Problem zu lösen, eine Dienstwiederherstellung ist nicht erforderlich. Sie korrigieren lediglich die fehlerhafte Komponente, während der Dienst weiter ausgeführt und die Datenintegrität aufrechterhalten wird. Der Termindruck und der Stress bei der Reparatur eines beschädigten Geräts sind nicht zu vergleichen mit dem Termindruck und dem Stress, der mit der Wiederherstellung eines Diensts einhergeht. Das bedeutet Vorteile für den Endbenutzer und weniger Stress für den Administrator.

Sie können ein Failover durchführen, ohne Switchbacks auszuführen (gelegentlich fälschlich als Failbacks bezeichnet). Wenn Sie den Clientzugriffsserver im primären Datencenter verlieren und dies zu einer 20 Sekunden dauernden Dienstunterbrechung für die Clients führt, müssen Sie sich möglicherweise noch nicht einmal Gedanken über ein Failback machen. Zu diesem Zeitpunkt besteht Ihre Hauptsorge darin, das Kernproblem zu lösen (z. B. das ausgefallene Lastenausgleichsmodul zu ersetzen). Nachdem die Komponente wieder online und betriebsbereit ist, beginnen einige Clients damit, die Komponente erneut zu nutzen, und andere Clients nehmen Dienste über das zweite Datencenter in Anspruch.

Exchange 2013 bietet außerdem eine Funktionalität, die Administratoren die Handhabung von zeitweise auftretenden Fehlern ermöglicht. Ein zeitweiliger Fehler ist beispielsweise eine Situation, in der die anfängliche TCP-Verbindung hergestellt werden kann, dann jedoch ein Stillstand eintritt. Ein zeitweise auftretender Fehler erfordert einigen zusätzlichen Verwaltungsaufwand, da er das Ergebnis der Inbetriebnahme eines Ersatzgeräts sein kann. Während der Reparatur wird das Gerät möglicherweise eingeschaltet und akzeptiert einige Anforderungen, kann jedoch nicht wirklich für die Verarbeitung von Dienstanforderungen durch Clients verwendet werden, bis die erforderlichen Konfigurationsschritte ausgeführt wurden. In diesem Szenario kann der Administrator einen Namespaceswitchover durchführen, indem einfach die VIP für das im Austausch befindliche Gerät aus der DNS-Konfiguration entfernt wird. Dies führt dazu, dass Clients während der Wartungsphase nicht versuchen, eine Verbindung mit dem Gerät herzustellen. Nachdem der Austausch abgeschlossen wurde, kann der Administrator die VIP wieder in die DNS-Konfiguration einfügen, und Clients können das Gerät wieder verwenden.

Weitere Informationen zum Planen und Bereitstellen von Ausfallsicherheit für Standorte finden Sie unter [Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten](planning-for-high-availability-and-site-resilience-exchange-2013-help.md) und [Bereitstellen der hohen Verfügbarkeit und Ausfallsicherheit von Standorten](deploying-high-availability-and-site-resilience-exchange-2013-help.md).

Wichtige Terminologie

## API für die Drittanbieterreplikation

Exchange 2013 enthält eine API für die Drittanbieterreplikation, mit der Unternehmen anstelle der integrierten Funktion für die fortlaufende Replikation Lösungen anderer Anbieter für die synchrone Replikation verwenden können. Microsoft unterstützt Drittanbieterlösungen, die diese API verwenden, sofern die Lösung die benötigte Funktionalität bereitstellt, um sämtliche systemeigene Funktionalität für die fortlaufende Replikation zu ersetzen, die als Ergebnis der Verwendung der API deaktiviert ist. Lösungen werden nur unterstützt, wenn die API in einer DAG zum Verwalten und Aktivieren von Postfachdatenbankkopien verwendet wird. Die Verwendung der API darüber hinaus wird nicht unterstützt. Außerdem muss die Lösung die geltenden Supportanforderungen für Windows-Hardware erfüllen. (Für Support ist keine Testvalidierung erforderlich.)

Beim Bereitstellen einer Lösung, die die integrierte Drittanbieterreplikations-API verwendet, muss Ihnen klar sein, dass der Lösungsanbieter für den Primärsupport der Lösung zuständig ist. Microsoft unterstützt Exchange-Daten in sowohl replizierten als auch nicht replizierten Lösungen. Lösungen mit Datenreplikation müssen die Supportrichtlinie von Microsoft für die Datenreplikation befolgen. Siehe Microsoft Knowledge Base-Artikel 895847, [Unterstützung der Datenreplikation für mehrere Standorte durch Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=895847). Darüber hinaus müssen Lösungen, die das Ressourcenmodell "Windows-Failovercluster" nutzen, die Supportanforderungen für Windows-Cluster im Microsoft Knowledge Base-Artikel 943984 erfüllen: [Microsoft-Supportrichtlinie für Windows Server 2008- oder Windows Server 2008 R2 Failovercluster](https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=943984) oder [Microsoft-Supportrichtlinie für Windows Server 2012 Failovercluster](https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=2775067).

Die Supportrichtlinie für Sicherung und Wiederherstellung von Microsoft für Bereitstellungen mit Replikations-API-basierten Drittanbieterlösungen entspricht der Richtlinie für systemeigene Bereitstellungen der fortlaufenden Replikation.

Wenn Sie ein Partner sind, der nach Informationen zur Drittanbieter-API sucht, wenden Sie sich an Ihren Ansprechpartner bei Microsoft.

Wichtige Terminologie

## Dokumentation zu Hochverfügbarkeit und Ausfallsicherheit für Standorte

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zu DAGs, Postfachdatenbankkopien und Sicherung und Wiederherstellung für Exchange 2013 sowie zur Verwaltung dieser Funktionen finden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="database-availability-groups-dags-exchange-2013-help.md">Database Availability Groups (DAGs)</a></p></td>
<td><p>Hier erhalten Sie Informationen zu DAGs, Active Manager, DAC-Modus (Datacenter Activation Coordination) und Postfachdatenbankkopien.</p></td>
</tr>
<tr class="even">
<td><p><a href="planning-for-high-availability-and-site-resilience-exchange-2013-help.md">Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten</a></p></td>
<td><p>Hier erhalten Sie Informationen zu den allgemeinen Anforderungen und den Anforderungen für Hardware, Netzwerk, Zeugenserver und zu den bewährten Methoden für DAGs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="deploying-high-availability-and-site-resilience-exchange-2013-help.md">Bereitstellen der hohen Verfügbarkeit und Ausfallsicherheit von Standorten</a></p></td>
<td><p>Hier können Sie ein Beispielszenario für die Bereitstellung und Konfiguration von DAGs untersuchen.</p></td>
</tr>
<tr class="even">
<td><p><a href="managing-high-availability-and-site-resilience-exchange-2013-help.md">Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte</a></p></td>
<td><p>Hier erhalten Sie Informationen zu Verwaltungsaufgaben in Bezug auf DAGs, zu Switchover- und Failovervorgängen sowie zum Wartungsmodus.</p></td>
</tr>
<tr class="odd">
<td><p><a href="monitoring-database-availability-groups-exchange-2013-help.md">Überwachen von Datenbankverfügbarkeitsgruppen</a></p></td>
<td><p>Hier erhalten Sie Informationen zu den integrierten Cmdlets und Skripts für die Überwachung von DAGs und Datenbankkopien.</p></td>
</tr>
<tr class="even">
<td><p><a href="backup-restore-and-disaster-recovery-exchange-2013-help.md">Sicherung, Wiederherstellung und Notfallwiederherstellung</a></p></td>
<td><p>Hier erhalten Sie Informationen zur Sicherung und Wiederherstellung von Exchange-Datenbanken und Wiederherstellungsdatenbanken sowie zur Serverwiederherstellung.</p></td>
</tr>
</tbody>
</table>


Wichtige Terminologie

