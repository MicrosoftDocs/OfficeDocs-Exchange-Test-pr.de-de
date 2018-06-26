---
title: 'Exchange 2013-Virtualisierung: Exchange 2013 Help'
TOCTitle: Exchange 2013-Virtualisierung
ms:assetid: 36184b2f-4cd9-48f8-b100-867fe4c6b579
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ619301(v=EXCHG.150)
ms:contentKeyID: 50475460
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013-Virtualisierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-08-08_

Sie können Microsoft Exchange Server 2013 in einer virtualisierten Umgebung bereitstellen. In diesem Thema erhalten Sie einen Überblick über die unterstützten Szenarien zur Bereitstellung von Exchange 2013 auf Hardwarevirtualisierungssoftware.

**Inhalt**

Anforderungen für die Hardwarevirtualisierung

Speicheranforderungen des Hostcomputers

Speicheranforderungen für Exchange

Arbeitsspeicheranforderungen und -empfehlungen für Exchange

Hostbasiertes Failoverclustering und Migration für Exchange

In dieser Erläuterung zur Exchange-Virtualisierung werden die folgenden Begriffe verwendet:

  - **Cold boot**   Wenn das Betriebssystem eines ausgeschalteten Systems neu gestartet wird, wird dies als *Kaltstart* bezeichnet. In diesem Fall bleibt der Zustand des Betriebssystems nicht erhalten.

  - **Saved state**   Beim Ausschalten eines virtuellen Computers können Hypervisoren normalerweise den Zustand des virtuellen Computers speichern, sodass der Computer beim nächsten Einschalten wieder diesen *gespeicherten Zustand* annimmt, statt die Schritte eines Kaltstarts durchlaufen zu müssen.

  - **Geplante Migration**   Wenn ein Systemadministrator die Verschiebung eines virtuellen Computers von einem Hypervisorhost auf einen anderen initiiert, wird dieser Vorgang als *geplante Migration* bezeichnet. Dabei kann es sich um eine einzelne Migration handeln, oder ein Systemadministrator kann dieses Ereignis als zeitgesteuerte automatische Verschiebung des virtuellen Computers konfigurieren. Eine geplante Migration kann auch das Ergebnis eines anderen Systemereignisses sein, bei dem es sich nicht um einen Hardware- oder Softwareausfall handelt. Entscheidend ist, dass sich der virtuelle Computer mit Exchange im Normalbetrieb befindet und aus bestimmten Gründen neu platziert werden muss. Hierzu kann eine Technologie wie die Livemigration oder vMotion verwendet werden. Wenn jedoch auf dem virtuellen Computer mit Exchange oder dem Hypervisorhost, auf dem sich der virtuelle Computer befindet, ein Fehler auftritt, wird dies nicht als eine geplante Migration bezeichnet.

## Anforderungen für die Hardwarevirtualisierung

Microsoft unterstützt Exchange 2013 in der Produktion mit Hardwarevirtualisierungssoftware nur, wenn die folgenden Bedingungen ausnahmslos erfüllt sind:

  - Die Hardwarevirtualisierungssoftware wird auf einer der folgenden Lösungen ausgeführt:
    
      - Beliebige Version von Windows Server mit Hyper-V-Technologie oder Microsoft Hyper-V Server
    
      - Beliebige Hypervisoren von Drittanbietern, die im Rahmen des [Windows Server-Virtualisierungsprogramms](https://go.microsoft.com/fwlink/p/?linkid=125375) getestet wurden.
    

    > [!NOTE]
    > Die Bereitstellung von Exchange 2013 auf IaaS-Anbietern (Infrastructure-as-a-Service) wird unterstützt, wenn alle Unterstützungsanforderungen erfüllt werden. Im Falle von Anbietern, die virtuelle Computer bereitstellen, gehört dazu, sicherzustellen, dass der für virtuelle Exchange-Computer verwendete Hypervisor vollständig unterstützt wird und dass die von Exchange zu verwendende Infrastruktur den Leistungsanforderungen gerecht wird, die während der Größenanpassung bestimmt wurden. Die Bereitstellung auf virtuellen Microsoft Azure-Computern wird unterstützt, wenn alle für Exchange-Datenbanken und Datenbanktransaktionsprotokolle verwendeten Speichervolumes (einschließlich Transportdatenbanken) für Azure Premium Storage konfiguriert sind.



  - Für den virtuellen Exchange-Gastcomputer gelten folgende Bedingungen:
    
      - Auf ihm wird Exchange 2013 ausgeführt.
    
      - Er wird unter Windows Server 2008 R2 SP1 (oder einer höheren Version), Windows Server 2012 oder Windows Server 2012 R2 bereitgestellt.

Für Bereitstellungen von Exchange 2013:

  - Auf einem virtuellen Computer werden alle Exchange 2013-Serverrollen unterstützt.

  - Virtuelle Computer mit Exchange-Server (einschließlich virtueller Computer mit der Exchange-Postfachserverrolle, die Teil einer Database Availability Group (DAG) sind) können mit hostbasiertem Failoverclustering und Migrationstechnologien kombiniert werden, sofern die virtuellen Computer so konfiguriert sind, dass beim Verschieben oder Offlineschalten keine Zustandsdaten auf dem Datenträger gespeichert oder vom Datenträger wiederhergestellt werden. Jede Failoveraktivität auf Hypervisorebene muss zu einem Kaltstart führen, wenn der virtuelle Computer auf dem Zielknoten aktiviert wird. Alle geplanten Migrationsvorgänge müssen entweder zum Herunterfahren und zu einem Kaltstart führen, oder es muss eine Onlinemigration mithilfe einer Technologie wie Hyper-V (Livemigration) durchgeführt werden. Die Hypervisormigration virtueller Maschinen wird vom Hypervisoranbieter unterstützt. Daher muss sichergestellt werden, dass der Hypervisoranbieter die Migration von virtuellen Exchange-Maschinen getestet hat und unterstützt. Microsoft unterstützt die Livemigration dieser virtuellen Maschinen mit Hyper-V.

  - Nur Verwaltungssoftware (z. B. Antivirensoftware, Sicherungssoftware oder Software für die Verwaltung virtueller Computer) kann auf dem physischen Hostcomputer bereitgestellt werden. Auf dem Hostcomputer dürfen keine weiteren serverbasierten Anwendungen (z. B. Exchange, SQL Server, Active Directory oder SAP) installiert sein. Der Hostcomputer sollte für die Ausführung der virtuellen Gastcomputer reserviert sein.

  - Einige Hypervisors enthalten Funktionen zum Erstellen von Momentaufnahmen virtueller Computer. Momentaufnahmen virtueller Computer erfassen den Zustand eines virtuellen Computers, während dieser ausgeführt wird. Diese Funktion ermöglicht das Erstellen mehrerer Momentaufnahmen eines virtuellen Computers und das anschließende Zurücksetzen des virtuellen Computers auf einen vorherigen Zustand, indem die Momentaufnahme auf den virtuellen Computer angewendet wird. Momentaufnahmen virtueller Computer sind jedoch nicht anwendungsaktiviert. Ihre Verwendung kann zu nicht beabsichtigten und unerwarteten Folgen für eine Serveranwendung führen, die Zustandsdaten verwaltet, z. B. Exchange. Aus diesem Grund wird das Erstellen von Momentaufnahmen eines virtuellen Exchange-Gastcomputers nicht unterstützt.

  - Bei vielen Hardwarevirtualisierungsprodukten können Sie die Anzahl der virtuellen Prozessoren angeben, die jedem virtuellen Gastcomputer zugewiesen werden sollen. Die virtuellen Prozessoren auf dem virtuellen Gastcomputer verwenden eine feste Anzahl physischer Prozessoren im physischen System gemeinsam. Exchange unterstützt ein Verhältnis von virtuellen zu physischen Prozessorkernen von maximal 2:1, wenngleich ein Verhältnis von 1:1 empfohlen wird. Ein Dualprozessorsystem mit Quad-Core-Prozessoren enthält beispielsweise insgesamt 8 physische Prozessorkernen im Hostsystem. Weisen Sie in einem System mit dieser Konfiguration der Kombination aller virtuellen Gastcomputer nicht mehr als insgesamt 16 virtuelle Prozessoren zu.

  - Wenn Sie die Gesamtanzahl der virtuellen Prozessoren berechnen, die für den Hostcomputer erforderlich sind, müssen Sie E/A- und Betriebssystemanforderungen berücksichtigen. In den meisten Fällen sind zwei virtuelle Prozessoren, die im Hostbetriebssystem für ein System erforderlich sind, das virtuelle Exchange-Computer hostet, vorhanden. Dieser Wert sollte als Basis für den virtuellen Prozessor des Hostbetriebssystems verwendet werden, wenn das Gesamtverhältnis von physischen Kernen zu virtuellen Prozessoren berechnet wird. Wenn die Leistungsüberwachung des Hostbetriebssystems anzeigt, dass mehr Prozessor beansprucht wird, als einer Auslastung von zwei Prozessoren entspricht, sollten Sie die Anzahl von virtuellen Prozessoren, die virtuellen Gastcomputern zugewiesen sind, entsprechend verringern. Stellen Sie außerdem sicher, dass das Gesamtverhältnis von virtuellen Prozessoren zu physischen Kernen nicht größer als 2:1 ist.

  - Das Betriebssystem für einen Exchange-Gastcomputer muss einen Datenträger verwenden, der mindestens 15 Gigabytes (GB) zuzüglich der Größe des dem Gastcomputer zugewiesenen virtuellen Speichers umfasst. Diese Anforderung muss erfüllt werden, um die Datenträgeranforderungen des Betriebssystems und der Auslagerungsdatei zu berücksichtigen. Wenn dem Gastcomputer z. B. 16 GB Speicher zugewiesen werden, beträgt der Mindestspeicherplatz des Datenträgers für das Gastbetriebssystem 31 GB.
    
    Außerdem kann verhindert werden, dass virtuelle Gastcomputer direkt mit im Hostcomputer installierten Fibre Channel- oder SCSI-Hostbusadaptern (HBAs) kommunizieren. In diesem Fall müssen Sie die Adapter im Betriebssystem des Hostcomputers konfigurieren und die logischen Gerätenummern (Logical Unit Numbers, LUNs) für die virtuellen Gastcomputer als virtuelle Datenträger oder Pass-Through-Datenträger darstellen.

  - Das Senden von E-Mails an externe Domänen aus Azure-Computeressourcen erfolgt ausschließlich über ein SMTP-Relay (auch als SMTP-Smarthost bezeichnet). Die Azure-Computeressource sendet die E-Mail an das SMTP-Relay. Anschließend wird die E-Mail vom SMTP-Relay-Anbieter an die externe Domäne übermittelt. Microsoft Exchange Online Protection ist ein Anbieter für SMTP-Relays. Es gibt jedoch auch eine Reihe von Drittanbietern. Weitere Informationen finden Sie im Microsoft Azure-Supportteam-Blogeintrag [Senden von E-Mails aus Azure-Computeressourcen an externe Domänen](https://go.microsoft.com/fwlink/p/?linkid=799723).

Anforderungen für die Hardwarevirtualisierung

## Speicheranforderungen des Hostcomputers

Es gelten für jeden Hostcomputer die folgenden Mindestanforderungen an den Festplattenspeicherplatz:

  - Hostcomputer in einigen Hardwarevirtualisierungsanwendungen erfordern ggf. Speicherplatz für ein Betriebssystem und seine Komponenten. Wenn Sie beispielsweise Windows Server 2008 R2 mit Hyper-V ausführen, benötigen Sie mindestens 10 GB, um die Anforderungen für Windows Server 2008 zu erfüllen. Weitere Informationen finden Sie unter [Systemanforderungen von Windows Server 2008 R2](https://go.microsoft.com/fwlink/p/?linkid=125378). Zur Unterstützung der Auslagerungsdatei des Betriebssystems, der Verwaltungssoftware sowie der Dateien für die Wiederherstellung nach einem Systemabsturz (Abbilddateien) ist zusätzlicher Speicherplatz erforderlich.

  - Einige Hypervisoren verwalten Dateien auf dem Hostcomputer, die für jeden virtuellen Gastcomputer eindeutig sind. In einer Hyper-V-Umgebung wird z. B. eine temporäre Arbeitsspeicherdatei (BIN-Datei) für jeden Gastcomputer erstellt und verwaltet. Die Größe jeder BIN-Datei ist mit der Größe des Arbeitsspeichers identisch, der dem Gastcomputer zugewiesen wurde. Außerdem werden ggf. weitere Dateien auf dem Hostcomputer für jeden Gastcomputer erstellt und verwaltet.

  - Wenn auf Ihrem Hostcomputer Windows Server 2012 Hyper-V oder Hyper-V 2012 ausgeführt wird und Sie einen hostbasierten Failovercluster konfigurieren, der Exchange-Postfachserver in einer DAG hostet, empfiehlt es sich, die Anleitungen im Microsoft Knowledge Base-Artikel 2872325, [Gastclusterknoten in Hyper-V können nicht erstellt werden oder ihnen kann nicht beigetreten werden](https://support.microsoft.com/kb/2872325), zu befolgen.

Anforderungen für die Hardwarevirtualisierung

## Speicheranforderungen für Exchange

Für Speicher, der mit einem virtualisierten Exchange-Server verbunden ist, gelten folgende Anforderungen:

  - Jedem Exchange-Gastcomputer muss auf dem Hostcomputer ausreichend Speicherplatz für den Datenträger mit fester Größe zugewiesen werden, der das Betriebssystem des Gastcomputers, temporäre verwendete Arbeitsspeicherdateien und zugehörige Dateien des virtuellen Computers enthält, die auf dem Hostcomputer gehostet werden. Außerdem müssen Sie jedem Exchange-Gastcomputer ausreichenden Speicherplatz für die Nachrichtenwarteschlangen sowie für die Datenbanken und Protokolldateien auf Postfachservern zuweisen.

  - Der vom Exchange-Gastcomputer verwendete Speicher für Exchange-Daten (beispielsweise Postfachdatenbanken und Transportwarteschlangen) kann virtueller Speicher mit einer festen Größe (beispielsweise feste VHDs \[Virtual Hard Drives, virtuelle Festplatten\] in einer Hyper-V-Umgebung), SCSI-Pass-Through-Speicher oder iSCSI-Speicher (Internet SCSI) sein. Passthroughspeicher ist auf Hostebene konfigurierter Speicher, der für einen Gastcomputer reserviert ist. Bei jedem vom Exchange-Gastcomputer verwendeten Speicher für Exchange-Daten muss es sich um Speicher auf Blockebene handeln, da Exchange 2013 die Verwendung von NAS-Volumes (Network Attached Storage) mit Ausnahme des weiter unten in diesem Thema beschriebenen SMB 3.0-Szenarios nicht unterstützt. Außerdem wird NAS-Speicher, der für den Gast als Speicher auf Blockebene über den Hypervisor dargestellt wird, nicht unterstützt.

  - Feste oder dynamische virtuelle Festplatten können in SMB 3.0-Dateifreigaben mit Sicherungsspeicher auf Blockebene gespeichert werden, wenn der Gastcomputer unter Windows Server 2012 Hyper-V (oder einer höheren Version von Hyper-V) ausgeführt wird. SMB 3.0-Dateifreigaben werden ausschließlich für Speichersysteme aus festen oder dynamischen virtuellen Festplatten (VHDs) unterstützt. Solche Dateifreigaben können nicht für die direkte Speicherung von Exchange-Daten verwendet werden. Wenn SMB 3.0-Dateifreigaben zur Speicherung fester oder dynamischer virtueller Festplatten verwendet werden, sollte der Speicher, der die Dateifreigabe unterstützt, für hohe Verfügbarkeit konfiguriert sein, um eine bestmögliche Verfügbarkeit des Exchange-Diensts zu gewährleisten.

  - Von Exchange verwendeter Speicher sollte in Datenträgerspindles gehostet werden, die von dem Speicher getrennt sind, der das Betriebssystem des virtuellen Gastcomputers hostet.

  - Die Konfiguration von iSCSI-Speicher für die Verwendung eines iSCSI-Initiators in einem virtuellen Exchange-Gastcomputer wird unterstützt. Diese Konfiguration ist jedoch durch eine verringerte Leistung gekennzeichnet, falls der Netzwerkstapel in einem virtuellen Computer nicht den vollen Funktionsumfang aufweist (beispielsweise unterstützen nicht alle virtuellen Netzwerkstapel Großrahmen).

Anforderungen für die Hardwarevirtualisierung

## Arbeitsspeicheranforderungen und -empfehlungen für Exchange

Einige Hypervisoren können die Arbeitsspeichergröße, die für einen bestimmten Gastcomputer zur Verfügung steht, anhand der erkannten Nutzung von Arbeitsspeicher im Gastcomputer im Vergleich zu den Anforderungen anderer Gastcomputer, die vom selben Hypervisor verwaltet werden, überzeichnen oder dynamisch anpassen. Diese Technologie ist sinnvoll für Arbeitsauslastungen, bei denen Arbeitsspeicher für kurze Zeitspannen benötigt wird und dann für andere Zwecke bereitgestellt werden kann. Sie sind nicht für Arbeitsauslastungen geeignet, die so ausgelegt sind, dass sie ständig Arbeitsspeicher nutzen. Exchange ist, ähnlich wie viele Serveranwendungen mit Leistungsoptimierung, die auf dem Zwischenspeichern von Daten im Arbeitsspeicher basieren, anfällig für eine schwache Systemleistung und eine nicht annehmbare Clientversorgung, wenn Exchange keine vollständige Kontrolle über den Arbeitsspeicher hat, der dem physischen oder virtuellen Computer zugeordnet ist, auf dem Exchange ausgeführt wird. Aus diesem Grund wird die Verwendung dynamischer Arbeitsspeicherfeatures für Exchange nicht unterstützt.

Anforderungen für die Hardwarevirtualisierung

## Hostbasiertes Failoverclustering und Migration für Exchange

Im Folgenden finden Sie Antworten auf einige häufig gestellte Fragen zu hostbasiertem Failoverclustering und zur Migrationstechnologie bei Exchange 2013-DAGs.

  - **Bietet Microsoft Unterstützung für Migrationstechnologien von Drittanbietern?**
    
    Microsoft kann nicht verbindlich zusagen, dass Hypervisorprodukte von Drittanbietern mit Verwendung dieser Technologien in Exchange integriert werden können, da diese Technologien nicht Teil des Programms zur Validierung der Servervirtualisierung (Server Virtualization Validation Program, SVVP) sind. Das SVVP deckt die weiteren Aspekte der Microsoft-Unterstützung für Hypervisoren von Drittanbietern ab. Sie müssen sicherstellen, dass Ihr Hypervisoranbieter die Kombination seiner Migrations- und Clusteringtechnologie mit Exchange unterstützt. Wenn der Hypervisoranbieter die Verwendung seiner Migrationstechnologie mit Exchange unterstützt, unterstützt Microsoft Exchange mit der jeweiligen Migrationstechnologie.

  - **Wie definiert Microsoft das hostbasierte Failoverclustering?**
    
    Das hostbasierte Failoverclustering bezieht sich auf jede Art von Technologie, die eine automatische Reaktion auf Fehler auf Hostebene und das Starten der betroffenen virtuellen Computer auf alternativen Servern ermöglicht. Die Verwendung dieser Technologie wird unterstützt, wenn in einem Fehlerszenario der virtuelle Computer per Kaltstart auf dem alternativen Host gestartet wird. Mithilfe dieser Technologie wird sichergestellt, dass der virtuelle Computer nie aus einem gespeicherten Zustand gestartet wird, der dauerhaft auf dem Datenträger gespeichert ist, da dieser Zustand verglichen mit den übrigen DAG-Mitgliedern veraltet ist.

  - **Was meint Microsoft mit Migrationsunterstützung?**
    
    Als Migrationstechnologie wird jede Art von Technologie bezeichnet, mit der eine geplante Verschiebung eines virtuellen Computers von einem Hostcomputer auf einen anderen möglich ist. Dabei kann es sich auch um eine automatisierte Verschiebung handeln, die im Rahmen eines Ressourcenlastenausgleichs stattfindet und nicht aufgrund eines Systemfehlers durchgeführt wird. Migrationen werden unterstützt, solange die virtuellen Computer nie aus einem gespeicherten Zustand gestartet werden, der dauerhaft auf dem Datenträger gespeichert ist. Dies bedeutet, dass Technologien zum Verschieben eines virtuellen Computers durch Übertragen des Status und des Arbeitsspeichers des virtuellen Computers über das Netzwerk ohne wahrnehmbare Ausfallzeit für die Verwendung mit Exchange unterstützt werden. Ein Drittanbieter für Hypervisoren muss Unterstützung für die Migrationstechnologie bereitstellen, während Microsoft bei Verwendung in dieser Konfiguration Unterstützung für Exchange bietet.

Anforderungen für die Hardwarevirtualisierung

