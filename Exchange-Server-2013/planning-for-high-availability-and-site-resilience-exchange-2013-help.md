---
title: 'Planen v. Hochverfüg. und Ausfallsicherh. von Standorten: Exchange 2013-Hilfe'
TOCTitle: Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten
ms:assetid: 29bb0358-fc8e-4437-8feb-d2959ed0f102
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638104(v=EXCHG.150)
ms:contentKeyID: 50475248
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Während der Planungsphase sollten die Systemarchitekten, Administratoren und andere Entscheidungsträger die geschäftlichen Anforderungen und die Anforderungen im Hinblick auf die Architektur für die Bereitstellung identifizieren, insbesondere die Anforderungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten.

Für die Bereitstellung dieser Funktionen müssen allgemeine Anforderungen sowie Hardware-, Software- und Netzwerkanforderungen erfüllt werden.

**Inhalt**

Allgemeine Anforderungen

Hardwareanforderungen

Speicheranforderungen

Softwareanforderungen

Netzwerkanforderungen

Zeugenserveranforderungen

Planen der Ausfallsicherheit von Standorten

## Allgemeine Anforderungen

Stellen Sie sicher, dass die folgenden systemweiten Anforderungen erfüllt sind, bevor Sie eine Database Availability Group (DAG) bereitstellen und Postfachdatenbank-Kopien erstellen:

  - DNS (Domain Name System) muss ausgeführt werden. Der DNS-Server sollte im Idealfall dynamische Updates akzeptieren. Wenn der DNS-Server keine dynamischen Updates akzeptiert, müssen Sie einen DNS-Hosteintrag (A-Eintrag) für jeden Exchange-Server erstellen. Andernfalls funktioniert Exchange nicht ordnungsgemäß.

  - Jeder Postfachserver in einer DAG muss ein Mitgliedsserver in derselben Domäne sein.

  - Das Hinzufügen eines Exchange 2013-Postfachservers, der gleichzeitig ein Verzeichnisserver für eine DAG ist, wird nicht unterstützt.

  - Der von Ihnen der DAG zugeordnete Name muss ein gültiger, verfügbarer und eindeutiger Computername mit maximal 15 Zeichen sein.

Allgemeine Anforderungen

## Hardwareanforderungen

Grundsätzlich gibt es keine besonderen Hardwareanforderungen für DAGs oder Postfachdatenbankkopien. Die verwendeten Server müssen allen Anforderungen entsprechen, die in den Themen für [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md) und [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md) dargelegt wurden.

Allgemeine Anforderungen

## Speicheranforderungen

Grundsätzlich gibt es keine besonderen Speicheranforderungen für DAGs oder Postfachdatenbankkopien. Für DAGs ist kein clusterverwalteter gemeinsamer Speicher erforderlich, er wird von DAGs auch nicht verwendet. Clusterverwalteter gemeinsamer Speicher wird für die Verwendung in einer DAG nur unterstützt, wenn die DAG so konfiguriert ist, dass eine Lösung mit einer in Exchange 2013 integrierten Replikations-API von Drittanbietern verwendet wird.

Allgemeine Anforderungen

## Softwareanforderungen

DAGs sind sowohl in Exchange 2013 Standard als auch in Exchange 2013 Enterprise verfügbar. Außerdem kann eine DAG eine Kombination von Servern enthalten, die Exchange 2013 Standard und Exchange 2013 Enterprise ausführen.

Alle Mitglieder der DAG müssen auch dasselbe Betriebssystem ausführen. Exchange 2013 wird unter den Betriebssystemen Windows Server 2008 R2, Windows Server 2012 und Windows Server 2012 R2 unterstützt. Alle Mitglieder einer DAG müssen dasselbe Betriebssystem ausführen. Windows Server 2012 R2 wird nur für DAG-Mitglieder mit Exchange 2013 Service Pack 1 oder höher unterstützt.

Zusätzlich zur Einhaltung der Voraussetzungen für die Installation von Exchange 2013 müssen Betriebssystemanforderungen eingehalten werden. Da DAGs das Windows-Failoverclustering nutzen, ist die Enterprise- oder Datacenter-Version von Windows Server 2008 R2 bzw. die Standard- oder Datacenter-Version von Windows Server 2012 oder Windows Server 2012 R2 erforderlich.

Allgemeine Anforderungen

## Netzwerkanforderungen

Für jede DAG und für jedes Mitglied einer DAG müssen bestimmte Netzwerkanforderungen eingehalten werden. Jede DAG muss über ein einzelnes *MAPI-Netzwerk* verfügen, über das ein DAG-Mitglied mit anderen Servern (z. B. mit anderen Exchange 2013-Servern oder Verzeichnisservern) kommuniziert. Außerdem können *Replikationsnetzwerke* verwendet werden, bei denen es sich um dedizierte Netzwerke für den Protokollversand und das Seeding handelt.

In früheren Versionen von Exchange wurden mindestens zwei Netzwerke (ein MAPI-Netzwerk und ein Replikationsnetzwerk) für DAGs empfohlen. In Exchange 2013 werden mehrere Netzwerke unterstützt, aber unsere Empfehlung hängt von Ihrer physischen Netzwerktopologie ab. Wenn mehrere physisch getrennte Netzwerke zwischen Ihren DAG-Mitgliedern vorhanden sind, sorgt die Verwendung separater MAPI- und Replikationsnetzwerke für zusätzliche Redundanz. Wenn Sie mehrere Netzwerke haben, die teilweise physisch getrennt sind, aber letztlich in einem einzigen physischen Netzwerk zusammenlaufen (z. B. eine einzige WAN-Verbindung), wird die Verwendung eines einzelnen Netzwerks (vorzugsweise 10 Gigabit Ethernet) für den MAPI- und Replikationsdatenverkehr empfohlen. Dies vereinfacht das Netzwerk und den Netzwerkpfad.

Ziehen Sie folgende Punkte in Betracht, wenn Sie die Netzwerkinfrastruktur für Ihre DAG entwerfen:

  - Jedes Mitglied der DAG muss mindestens einen Netzwerkadapter besitzen, der mit allen anderen Mitgliedern der DAG kommunizieren kann. Bei einem einzelnen Netzwerkpfad wird empfohlen, ein Ethernet mit mindestens 1 Gigabit, vorzugsweise jedoch 10 Gigabit, zu verwenden. Außerdem wird bei Verwendung eines einzelnen Netzwerkadapters in den jeweiligen Mitgliedern der DAG empfohlen, dass Sie die Gesamtlösung unter Berücksichtigung des einzelnen Netzwerkadapters entwerfen.

  - Durch die Verwendung von zwei Netzwerkadaptern in den einzelnen Mitgliedern der DAG erhalten Sie ein MAPI-Netzwerk und ein Replikationsnetzwerk mit Redundanz für das Replikationsnetzwerk sowie die folgenden Verhaltensweisen bei der Wiederherstellung:
    
      - Falls ein Fehler auftritt, der das MAPI-Netzwerk beeinflusst, tritt ein Failover des Servers auf (unter der Annahme, dass fehlerfreie Postfachdatenbankkopien vorhanden sein, die aktiviert werden können).
    
      - Falls ein Fehler in Bezug auf das Replikationsnetzwerk auftritt, werden die Protokollversand- und Seedingoperationen so zurückgesetzt, dass sie das MAPI-Netzwerk verwenden, sofern dieses von dem Fehler nicht betroffen ist. Dies gilt selbst dann, wenn für das MAPI-Netzwerk die Eigenschaft *ReplicationEnabled* auf "False" festgelegt ist. Wenn das fehlerhafte Replikationsnetzwerk wiederhergestellt wurde und die Protokollversand- und Seedingoperationen fortgesetzt werden können, müssen Sie manuell zum Replikationsnetzwerk zurückwechseln. Zum Ändern der Replikation vom MAPI-Netzwerk auf ein wiederhergestelltes Replikationsnetzwerk können Sie die fortlaufende Replikation entweder mit den Cmdlets **Suspend-MailboxDatabaseCopy** und **Resume-MailboxDatabaseCopy** anhalten und wieder fortsetzen, oder Sie starten den Microsoft Exchange-Replikationsdienst neu. Es wird empfohlen, die Vorgänge anzuhalten und wieder fortzusetzen, um den kurzen Ausfall zu vermeiden, den ein Neustart des Microsoft Exchange-Replikationsdiensts zur Folge hat.

  - Jedes DAG-Mitglied muss über die gleiche Anzahl von Netzwerken verfügen. Wenn Sie z. B. planen, einen einzelnen Netzwerkadapter in einem Mitglied einer DAG zu verwenden, müssen alle anderen Mitglieder dieser DAG ebenfalls einen einzelnen Netzwerkadapter verwenden.

  - Jede DAG darf nicht mehr als ein MAPI-Netzwerk besitzen. Das MAPI-Netzwerk muss Verbindungen mit anderen Exchange-Servern sowie mit anderen Diensten wie Active Directory und DNS bereitstellen.

  - Zusätzliche Replikationsnetzwerke können je nach Bedarf hinzugefügt werden. Durch die Verwendung von NIC-Teaming (Bündelung von Netzwerkkarten) oder ähnlichen Technologien können Sie außerdem verhindern, dass ein einzelner Netzwerkadapter die einzige Fehlerquelle darstellen kann. Selbst durch die Bündelung wird jedoch nicht verhindert, dass das Netzwerk selbst die einzige Fehlerquelle sein kann. Darüber hinaus führt die Bündelung zu unnötiger Komplexität der DAG.

  - Jedes Netzwerk der einzelnen DAG-Mitgliedsserver muss sich in einem eigenen Subnetz des Netzwerks befinden. Jeder Server in der DAG kann sich in einem anderen Subnetz befinden, aber die MAPI- und Replikationsnetzwerke müssen routingfähig sein und Verbindungen bereitstellen, damit Folgendes zutrifft:
    
      - Jedes Netzwerk der einzelnen DAG-Mitgliedsserver befindet sich in einem eigenen Subnetz, das von den Subnetzen getrennt ist, die von den anderen Netzwerken auf dem Server verwendet werden.
    
      - Jedes MAPI-Netzwerk des DAG-Mitgliedsservers kann mit dem MAPI-Netzwerk aller anderen DAG-Mitglieder kommunizieren.
    
      - Jedes Replikationsnetzwerk des DAG-Mitgliedsservers kann mit dem Replikationsnetzwerk aller anderen DAG-Mitglieder kommunizieren.
    
      - Es erfolgt kein direktes Routing, das den Taktdatenverkehr vom Replikationsnetzwerk auf einem DAG-Mitgliedsserver zum MAPI-Netzwerk auf einem anderen DAG-Mitgliedsserver (oder umgekehrt) sowie zwischen mehreren Replikationsnetzwerken in der DAG gestattet.

  - Unabhängig von ihrem relativ zu anderen DAG-Mitgliedern gesehenen geografischen Standort darf kein Mitglied der DAG eine Roundtrip-Netzwerklatenz aufweisen, die zwischen den einzelnen Mitgliedern mehr als 500 Millisekunden beträgt. Wenn die Roundtriplatenz zwischen zwei Postfachservern, die Kopien einer Datenbank hosten, größer wird, steigt auch die Gefahr, dass die jeweilige Replikation nicht aktuell ist. Ungeachtet der Latenz der Lösung sollten Kunden sich vergewissern, dass die Netzwerke zwischen allen DAG-Mitgliedern in der Lage sind, die Datenschutz- und Verfügbarkeitsziele der Bereitstellung zu erfüllen. Für Konfigurationen mit größeren Latenzwerten kann eine spezielle Optimierung von DAG-, Replikations- und Netzwerkparametern erforderlich sein (z. B. Erhöhen der Anzahl von Datenbanken oder Verringern der Anzahl von Postfächern pro Datenbank), um die gewünschten Ziele zu erreichen.

  - Roundtrip-Latenzanforderungen sind vielleicht nicht die strikteste Anforderung an Netzwerkbandbreiten und Latenz für eine Konfiguration mit mehreren Datencentern. Sie müssen die gesamte Netzwerklast berechnen, zu welcher Clientzugriff, Active Directory, Transport, fortlaufende Replikation und anderer Anwendungsdatenverkehr gehört, um die erforderlichen Netzwerkvoraussetzungen für die Umgebung zu bestimmen.

  - DAG-Netzwerke unterstützen IPv4 (Internetprotokoll, Version 4) und IPv6. IPv6 wird nur unterstützt, wenn IPv4 ebenfalls verwendet wird. Reine IPv6-Umgebungen werden nicht unterstützt. Die Verwendung von IPv6-Adressen und IP-Adressbereichen wird nur unterstützt, wenn auf diesem Computer sowohl IPv6 als auch IPv4 aktiviert sind und wenn das Netzwerk beide IP-Adressversionen unterstützt. Wenn Exchange 2013 in dieser Konfiguration implementiert ist, können alle Serverrollen Daten an Geräte, Server und Clients senden bzw. von diesen empfangen, die IPv6-Adressen verwenden.

  - Die automatische Privat-IP-Adressierung (APIPA) ist ein Feature von Windows, mit dem IP-Adressen automatisch zugeordnet werden, wenn kein DHCP-Server (Dynamic Host Configuration Protocol) im Netzwerk verfügbar ist. APIPA-Adressen (einschließlich manuell zugeordneter Adressen aus dem APIPA-Adressbereich) werden nicht für die Verwendung durch DAGs oder Exchange 2013 unterstützt.

## Anforderungen an den DAG-Namen und die IP-Adresse

Während der Erstellung erhält jede DAG einen eindeutigen Namen und ihr wird mindestens eine statische IP-Adresse zugeordnet, sofern sie nicht für die Verwendung von DHCP konfiguriert wird. Unabhängig davon, ob Sie die Adressen statisch oder dynamisch zuordnen, müssen sich die einer DAG zugeordneten IP-Adressen im MAPI-Netzwerk befinden.

Jede DAG mit Windows Server 2008 R2 oder Windows Server 2012 erfordert mindestens eine IP-Adresse im MAPI-Netzwerk Eine DAG erfordert weitere IP-Adressen, wenn sich das MAPI-Netzwerk über mehrere Subnetze erstreckt. DAGs mit Windows Server 2012 R2, die ohne Cluster-Administratorzugriffspunkt erstellt wurden, benötigen keine IP-Adresse.

In der folgenden Abbildung ist eine DAG dargestellt, bei der sich das MAPI-Netzwerk aller Knoten in der DAG im gleichen Subnetz befinden.

**DAG mit MAPI-Netzwerk im selben Subnetz**

![DAG in einzelnem Subnetz](images/Dd638104.bcb7ef68-6d18-4516-a736-b936991c82cb(EXCHG.150).gif "DAG in einzelnem Subnetz")

In diesem Beispiel befindet sich das MAPI-Netzwerk der einzelnen DAG-Mitglieder im Subnetz 172.19.18.*x*. Daher erfordert die DAG in diesem Subnetz eine einzelne IP-Adresse.

In der nächsten Abbildung wird eine DAG mit einem MAPI-Netzwerk dargestellt, das sich über zwei Subnetze erstreckt: 172.19.18.*x* und 172.19.19.*x*.

**DAG mit MAPI-Netzwerk in mehreren Subnetzen**

![DAG erweitert über mehrere Subnetze](images/Dd638104.ffb57c64-3cb1-435c-8148-1b7154d1575c(EXCHG.150).gif "DAG erweitert über mehrere Subnetze")

In diesem Beispiel befindet sich das MAPI-Netzwerk der einzelnen DAG-Mitglieder in einem separaten Subnetz. Daher erfordert die DAG zwei IP-Adressen, eine für jedes Subnetz im MAPI-Netzwerk.

Sobald das MAPI-Netzwerk der DAG ein weiteres Subnetz umfasst, muss für dieses Subnetz eine weitere IP-Adresse für die DAG konfiguriert werden. Jeder für diese DAG konfigurierten IP-Adresse wird der der DAG zugrunde liegende Failovercluster zugeordnet, von dem diese Adresse auch verwendet wird. Der Name der DAG wird auch als Name für den zugrunde liegenden Failovercluster verwendet.

Der Cluster für die DAG verwendet jeweils nur eine der zugeordneten IP-Adressen. Diese IP-Adresse wird vom Windows-Failoverclustering im DNS registriert, wenn die IP-Adresse und die Netzwerknamensressourcen des Clusters online gestellt werden. Zusätzlich zur Verwendung einer IP-Adresse und eines Netzwerknamens wird ein Clusternamenobjekt (CNO) in Active Directory erstellt. Der Name, die IP-Adresse und das CNO für den Cluster werden intern vom System verwendet, um die DAG zu schützen und die interne Kommunikation zu unterstützen. Administratoren und Endbenutzer müssen keine Verbindung mit dem Namen oder der IP-Adresse der DAG herstellen.


> [!NOTE]
> Obwohl die IP-Adresse und der Netzwerkname des Clusters intern vom System verwendet werden, ist die Verfügbarkeit dieser Ressourcen in Exchange 2013 nicht zwingend erforderlich. Selbst wenn die IP-Adresse und die Netzwerknamensressourcen des zugrunde liegenden Cluster-Administratorzugriffspunkts offline sind, erfolgt die interne Kommunikation weiterhin innerhalb der DAG, indem die Servernamen des DAG-Mitglieds verwendet werden. Es wird jedoch empfohlen, dass Sie die Verfügbarkeit dieser Ressourcen regelmäßig überwachen, um sicherzustellen, dass sie nicht länger als 30&nbsp;Tage offline sind. Wenn der zugrunde liegende Cluster für mehr als 30&nbsp;Tage offline ist, wird das Konto des Clusternetzwerkobjekts möglicherweise vom Garbage Collection-Mechanismus in Active Directory außer Kraft gesetzt.



## Netzwerkadapterkonfiguration für DAGs

Jeder Netzwerkadapter muss entsprechend dem gewünschten Verwendungszweck konfiguriert werden. Die Konfiguration eines Netzwerkadapters, der für ein MAPI-Netzwerk verwendet wird, unterscheidet sich von der Konfiguration eines Netzwerkadapters, der für ein Replikationsnetzwerk verwendet wird. Zusätzlich zum ordnungsgemäßen Konfigurieren der einzelnen Netzwerkadapter müssen Sie auch die Netzwerkverbindungsreihenfolge in Windows konfigurieren, damit sich das MAPI-Netzwerk am Anfang der Verbindungsreihenfolge befindet. Genaue Anweisungen zum Ändern der Netzwerkverbindungsreihenfolge finden Sie unter [Ändern der Bindungsreihenfolge für Protokolle](https://go.microsoft.com/fwlink/p/?linkid=179138).

## Konfiguration des MAPI-Netzwerkadapters

Ein Netzwerkadapter, der für die Verwendung in einem MAPI-Netzwerk vorgesehen ist, sollte gemäß der Beschreibung in der folgenden Tabelle konfiguriert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Netzwerkfeatures</th>
<th>Einstellungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Client für Microsoft-Netzwerke</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="even">
<td><p>QoS-Paketplaner</p></td>
<td><p>Optional aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Datei- und Druckerfreigabe für Microsoft-Netzwerke</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="even">
<td><p>Internetprotokoll, Version 6 (TCP/IP v6)</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Internetprotokoll, Version 4 (TCP/IP v4)</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="even">
<td><p>E/A-Treiber für Verbindungsschicht-Topologieerkennungszuordnung</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Antwort für Verbindungsschicht-Topologieerkennung</p></td>
<td><p>Aktiviert</p></td>
</tr>
</tbody>
</table>


Die TCP/IP v4-Eigenschaften für einen MAPI-Netzwerkadapter werden wie folgt konfiguriert:

  - Die IP-Adresse für das MAPI-Netzwerk eines DAG-Mitglieds kann manuell zugeordnet oder zur Verwendung von DHCP konfiguriert werden. Bei der Verwendung von DHCP wird empfohlen, dauerhafte Reservierungen für die IP-Adresse des Servers zu verwenden.

  - Das MAPI-Netzwerk verwendet normalerweise ein Standardgateway, obwohl es nicht erforderlich ist.

  - Es muss mindestens eine DNS-Serveradresse konfiguriert werden. Aus Gründen der Redundanz wird empfohlen, mehrere DNS-Server zu verwenden.

  - Das Kontrollkästchen **Adressen dieser Verbindung in DNS registrieren** sollte aktiviert sein.

## Konfiguration des Replikationsnetzwerkadapters

Ein Netzwerkadapter, der für die Verwendung in einem Replikationsnetzwerk vorgesehen ist, sollte gemäß der Beschreibung in der folgenden Tabelle konfiguriert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Netzwerkfeatures</th>
<th>Einstellungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Client für Microsoft-Netzwerke</p></td>
<td><p>Deaktiviert</p></td>
</tr>
<tr class="even">
<td><p>QoS-Paketplaner</p></td>
<td><p>Optional aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Datei- und Druckerfreigabe für Microsoft-Netzwerke</p></td>
<td><p>Deaktiviert</p></td>
</tr>
<tr class="even">
<td><p>Internetprotokoll, Version 6 (TCP/IP v6)</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Internetprotokoll, Version 4 (TCP/IP v4)</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="even">
<td><p>E/A-Treiber für Verbindungsschicht-Topologieerkennungszuordnung</p></td>
<td><p>Aktiviert</p></td>
</tr>
<tr class="odd">
<td><p>Antwort für Verbindungsschicht-Topologieerkennung</p></td>
<td><p>Aktiviert</p></td>
</tr>
</tbody>
</table>


Die TCP/IP v4-Eigenschaften für einen Replikationsnetzwerkadapter werden wie folgt konfiguriert:

  - Die IP-Adresse für das Replikationsnetzwerk eines DAG-Mitglieds kann manuell zugeordnet oder zur Verwendung von DHCP konfiguriert werden. Bei der Verwendung von DHCP wird empfohlen, dauerhafte Reservierungen für die IP-Adresse des Servers zu verwenden.

  - Replikationsnetzwerke verfügen normalerweise nicht über Standardgateways. Wenn das MAPI-Netzwerk über ein Standardgateway verfügt, sollten keine anderen Netzwerke Standardgateways aufweisen. Das Routing des Netzwerkverkehrs in einem Replikationsnetzwerk kann mithilfe beständiger, statischer Routen zu entsprechenden Netzwerken auf anderen DAG-Mitgliedern konfiguriert werden, die Gatewayadressen verwenden, mit denen das Routing zwischen den Replikationsnetzwerken ausgeführt werden kann. Sämtlicher anderer Datenverkehr, der nicht dieser Route entspricht, wird vom Standardgateway verarbeitet, der am Adapter für das MAPI-Netzwerk konfiguriert wurde.

  - DNS-Serveradressen sollten nicht konfiguriert werden.

  - Das Kontrollkästchen **Adressen dieser Verbindung in DNS registrieren** sollte deaktiviert sein

Allgemeine Anforderungen

## Zeugenserveranforderungen

Ein *Zeugenserver* ist ein Server außerhalb einer DAG, der zum Erreichen und Erhalten des Quorums verwendet wird, wenn die DAG über eine gerade Anzahl von Mitgliedern verfügt. DAGs mit einer ungeraden Anzahl von Mitgliedern verwenden keinen Zeugenserver. Alle DAGs mit gerader Anzahl von Mitgliedern müssen einen Zeugenserver verwenden. Der Zeugenserver kann ein beliebiger Computer sein, auf dem Windows Server ausgeführt wird. Es ist nicht erforderlich, dass die Version des Windows Server-Betriebssystems des Zeugenservers mit dem Betriebssystem der DAG-Mitglieder übereinstimmt.

Das Quorum wird auf Clusterebene unterhalb der DAG aufrechterhalten. Für eine DAG besteht das Quorum, wenn die Mehrzahl ihrer Mitglieder online sind und mit den anderen Mitgliedern der DAG kommunizieren können, die ebenfalls online sind. Diese Auffassung eines Quorums stellt einen Aspekt des Quorumkonzepts beim Windows-Failoverclustering dar. Ein verwandter und erforderlicher Aspekt von Quoren in Failoverclustern ist die *Quorumressource*. Die Quorumressource ist eine Ressource innerhalb eines Failoverclusters, die einen Mechanismus für Entscheidungen bezüglich Mitgliedschaft und Clusterzustand bereitstellt. Die Quorumressource stellt außerdem einen permanenten Speicher zum Speichern von Konfigurationsinformationen bereit. Ein Begleiter der Quorumressource ist das *Quorumprotokoll*, bei dem es sich um eine Konfigurationsdatenbank für den Cluster handelt. Das Quorumprotokoll enthält z. B. Informationen dazu, welche Server Mitglieder des Clusters sind, welche Ressourcen im Cluster installiert sind sowie zum Zustand anderer Ressourcen (z. B. "online" oder "offline").

Es ist entscheidend, dass jedes DAG-Mitglied über eine konsistente Ansicht darauf verfügt, wie der der DAG zugrunde liegende Cluster konfiguriert ist. Das Quorum dient als definitives Repository für alle Konfigurationsinformationen über den Cluster. Mit dem Quorum werden zudem Konflikte gelöst, um ein *Split Brain-Syndrom* zu vermeiden. Das Split Brain-Syndrom stellt einen Zustand dar, der eintritt, wenn DAG-Mitglieder aktiv sind, aber nicht miteinander kommunizieren können. Das "Split Brain-Syndrom" wird verhindert, indem immer eine Mehrheit der DAG-Mitglieder (bei einer geraden Anzahl der Mitglieder wird der DAG-Zeugenserver einbezogen) verfügbar und aktiv sein muss, damit die DAG funktionsfähig ist.

Allgemeine Anforderungen

## Planen der Ausfallsicherheit von Standorten

Täglich erkennen immer mehr Unternehmen, dass der Zugriff auf ein zuverlässiges und verfügbares Messagingsystem für ihren Erfolg entscheidend ist. Für zahlreiche Unternehmen ist das Messagingsystem im Rahmen der Geschäftskontinuitätspläne erforderlich und die Ausfallsicherheit des Standorts muss in der Bereitstellung von Messagingdiensten berücksichtigt werden. Im Wesentlichen beinhalten viele Lösungen zur Ausfallsicherheit von Standorten die Bereitstellung von Hardware in einem zweiten Datencenter.

Letztendlich hängt der Gesamtentwurf einer DAG, einschließlich der Anzahl der DAG-Mitglieder und der Anzahl der Postfachdatenbankkopien, von den Vereinbarungen zum Servicelevel (SLA) für Wiederherstellungen im Unternehmen ab, die verschiedene Fehlerszenarien abdecken. Während der Planungsphase sollten die Architekten und Administratoren der Lösung die Anforderungen für die Bereitstellung identifizieren, insbesondere die Anforderungen für die Ausfallsicherheit von Standorten. Sie identifizieren die zu verwendenden Standorte und die erforderlichen Ziele für die Vereinbarungen zum Servicelevel für Wiederherstellungen. Die Vereinbarung zum Servicelevel identifiziert zwei bestimmte Elemente als Basis für den Entwurf einer Lösung, die eine hohe Verfügbarkeit und die Ausfallsicherheit von Standorten bietet: die angestrebte Wiederherstellungsdauer und der angestrebte Wiederherstellungszeitpunkt. Beide Werte werden in Minuten gemessen. Die angestrebte Wiederherstellungsdauer bezeichnet die Dauer, die für die Wiederherstellung des Diensts erforderlich ist. Der angestrebte Wiederherstellungszeitpunkt bezieht sich darauf, wie aktuell die Daten sind, nachdem die Wiederherstellung abgeschlossen ist. Es kann auch eine Vereinbarung zum Servicelevel für die Wiederherstellung des uneingeschränkten Diensts des primären Datencenters nach der Behebung seiner Probleme definiert werden.

Die Architekten und Administratoren der Lösung identifizieren außerdem, welche Benutzer den Ausfallsicherheitsschutz für Standorte erfordern, und bestimmen, ob die Lösung für mehrere Standorte eine Active/Passive- oder eine Active/Active-Konfiguration darstellen wird. Bei einer Active/Passive-Konfiguration werden normalerweise keine Benutzer im Ersatzdatencenter gehostet. Bei einer Active/Active-Konfiguration werden die Benutzer an beiden Standorten gehostet und ein Prozentsatz der Gesamtanzahl von Datenbanken in der Lösung verfügt über einen bevorzugten aktiven Standort in einem sekundären Datencenter. Wenn der Dienst für die Benutzer eines Datencenters ausfällt, werden diese Benutzer im anderen Datencenter aktiviert.

Die Erstellung der entsprechenden Vereinbarungen zum Servicelevel erfordert häufig die Beantwortung folgender grundlegender Fragen:

  - Welcher Servicelevel ist nach Ausfall des Hauptdatencenters erforderlich?

  - Benötigen Benutzer ihre Daten oder nur Messagingdienste?

  - Wie schnell werden die Daten benötigt?

  - Wie viele Benutzer müssen unterstützt werden?

  - Wie sollen die Benutzer auf ihre Daten zugreifen?

  - Wie lautet die Vereinbarung zum Servicelevel für die Aktivierung des Standbydatencenters?

  - Wie wird das Hauptdatencenter wieder in Betrieb genommen?

  - Sind die Ressourcen für die Ausfallsicherheitslösung von Standorten reserviert?

Durch die Beantwortung dieser Fragen bildet sich ein erster Entwurf Ihrer Messaginglösung für die Ausfallsicherheit von Standorten heraus. Eine wesentliche Anforderung der Wiederherstellung nach einem Standortausfall besteht in der Erstellung einer Lösung, mit der die erforderlichen Daten an das Sicherungsdatencenter übergeben werden, das den Ersatzmessagingdienst hostet.

## Zertifikatsplanung

Bei der Bereitstellung einer DAG in einem einzelnen Datencenter müssen hinsichtlich des Entwurfs von Zertifikaten keine eindeutigen oder speziellen Aspekte berücksichtigt werden. Wenn sich eine DAG jedoch in einer Konfiguration für die Standortausfallsicherheit über mehrere Datencenter erstreckt, gibt es hinsichtlich der Zertifikate einige bestimmte Überlegungen. Im Allgemeinen hängt der Zertifikatsentwurf von den verwendeten Clients sowie von den Zertifikatanforderungen anderer Anwendungen ab. Es gibt jedoch einige bestimmte Empfehlungen und bewährte Methoden, die Sie hinsichtlich des Typs und der Anzahl von Zertifikaten befolgen sollten.

Als bewährte Methode sollten Sie die Anzahl von Zertifikaten minimieren, die für Ihre Exchange-Server und Reverseproxyserver verwendet werden. Es wird empfohlen, für all diese Dienstendpunkte in den einzelnen Datencentern ein einzelnes Zertifikat zu verwenden. Bei diesem Ansatz wird die Anzahl der erforderlichen Zertifikate minimiert, wodurch Kosten und Komplexität der Lösung verringert werden.

Für Outlook Anywhere-Clients wird empfohlen, dass Sie für jedes Datencenter ein einzelnes SAN-Zertifikat (Subject Alternative Name) verwenden und mehrere Hostnamen in das Zertifikat einbeziehen. Damit die Outlook Anywhere-Konnektivität nach einem Datenbank-, Server- oder Datencenterswitchover sichergestellt ist, müssen Sie für jedes Zertifikat denselben Zertifikatprinzipalnamen verwenden und das Outlook-Anbieterkonfigurationsobjekt in Active Directory mit demselben Prinzipalnamen im Microsoft-Standardformular (msstd) konfigurieren. Wenn Sie z. B. den Zertifikatprinzipalnamen "mail.contoso.com" verwenden, würden Sie die Attribute wie folgt konfigurieren:

    Set-OutlookProvider EXPR -CertPrincipalName "msstd:mail.contoso.com"

Einige Anwendungen, die mit Exchange integriert werden, weisen bestimmte Zertifikatanforderungen auf, die möglicherweise die Verwendung zusätzlicher Zertifikate erfordern. Exchange 2013 kann gleichzeitig mit Office Communications Server (OCS) installiert sein. OCS erfordert Zertifikate mit 1024-Bit oder stärkerer Verschlüsselung, die den OCS-Servernamen als Zertifikatprinzipalnamen verwenden. Da bei Verwendung eines OCS-Servernamens als Zertifikatprinzipalnamen Outlook Anywhere nicht ordnungsgemäß ausgeführt werden kann, müssten Sie ein zusätzliches und separates Zertifikat für die OCS-Umgebung verwenden.

## Netzwerkplanung

Zusätzlich zu den bestimmten Netzwerkanforderungen, die für die einzelnen DAGs sowie für die einzelnen Server eingehalten werden müssen, die Mitglied einer DAG sind, gibt es einige Anforderungen und Empfehlungen, die nur für Konfigurationen mit Ausfallsicherheit von Standorten gelten. Wie bei allen DAGs, unabhängig davon, ob die DAG-Mitglieder an einem oder mehreren Standorten bereitgestellt werden, darf die Roundtrip-Netzwerklatenz zwischen DAG-Mitgliedern nicht mehr als 500 Millisekunden betragen. Außerdem gibt es bestimmte Konfigurationseinstellungen, die für DAGs empfohlen werden, die sich über mehrere Standorte erstrecken:

  - **MAPI-Netzwerke sollten von Replikationsnetzwerken getrennt werden**Windows-Netzwerkrichtlinien, Windows-Firewallrichtlinien oder Routerzugriffssteuerungslisten (Access Control Lists, ACLs) sollten verwendet werden, um den Datenverkehr zwischen MAPI-Netzwerk und Replikationsnetzwerken zu blockieren. Diese Konfiguration ist notwendig, um die Überkoppelung des Netzwerktakts zu verhindern.

  - **Den Clients zugewandte DNS-Datensätze sollten eine Gültigkeitsdauer (Time to Live, TTL) von 5 Minuten aufweisen**   Der Umfang der Ausfallzeit, die bei Clients auftritt, hängt nicht nur davon ab, wie schnell ein Switchover erfolgen kann, sondern auch davon, wie schnell die DNS-Replikation ausgeführt wird und wie schnell die Clients aktualisierte DNS-Informationen abfragen. Für die DNS-Datensätze aller Exchange-Clientdienste, einschließlich Microsoft Office Outlook Web App, Microsoft Exchange ActiveSync, Exchange-Webdienste, Outlook Anywhere, SMTP, POP3 und IMAP4 auf internen und externen DNS-Servern, sollte eine Gültigkeitsdauer von 5 Minuten festgelegt werden.

  - **Verwenden Sie statische Routen, um die Konnektivität zwischen Replikationsnetzwerken zu konfigurieren** Verwenden Sie beständige statische Routen, um die Netzwerkkonnektivität zwischen den einzelnen Replikationsnetzwerkadaptern bereitzustellen. Dies ist eine schnelle und einmalige Konfiguration, die auf jedem DAG-Mitglied ausgeführt wird, wenn statische IP-Adressen verwendet werden. Wenn Sie zum Abrufen der IP-Adressen für die Replikationsnetzwerke DHCP verwenden, können Sie damit auch statische Routen für die Replikation zuordnen und so den Konfigurationsprozess vereinfachen.

## Allgemeine Planung der Ausfallsicherheit für Standorte

Zusätzlich zu den zuvor aufgeführten Anforderungen für die hohe Verfügbarkeit gibt es weitere Empfehlungen für die Bereitstellung von Exchange 2013 in einer Konfiguration mit Ausfallsicherheit für Standorte (z. B. die Ausweitung einer DAG auf mehrere Datencenter). Was Sie während der Planungsphase ausführen, wirkt sich direkt auf den Erfolg der Lösung zur Standortausfallsicherheit aus. Ein schlechter Namespaceentwurf kann z. B. zu Problemen bei Zertifikaten führen und eine falsche Zertifikatskonfiguration kann Benutzer am Zugriff auf Dienste hindern.

Damit die Zeit minimiert wird, die erforderlich ist, um ein zweites Datencenter zu aktivieren und es dem zweiten Datencenter zu ermöglichen, die Dienstendpunkte eines fehlerhaften Datencenters zu hosten, muss die entsprechende Planung abgeschlossen werden. Es folgen Beispiele:

  - Die Ziele der Vereinbarung zum Servicelevel für die Lösung zur Standortausfallsicherheit müssen eindeutig sein und umfassend dokumentiert werden.

  - Die Server im zweiten Datencenter müssen über eine ausreichende Kapazität verfügen, um den kombinierten Benutzerbestand beider Datencenter zu hosten.

  - Für das zweite Datencenter müssen alle Dienste aktiviert sein, die im primären Datencenter bereitgestellt werden (außer der Dienst ist nicht im Rahmen der Vereinbarung zum Servicelevel für die Standortausfallsicherheit enthalten). Dies umfasst Active Directory, die Netzwerkinfrastruktur (z. B. DNS oder TCP/IP), Telefoniedienste (wenn Unified Messaging verwendet wird) und die Standortinfrastruktur (wie Energie oder Kühlung).

  - Damit einige Dienste die Benutzer des fehlerhaften Datencenters versorgen können, müssen für sie die richtigen Serverzertifikate konfiguriert werden. Einige Dienste lassen keine Instanziierung zu (z. B. POP3 und IMAP4) und ermöglichen nur die Verwendung eines einzelnen Zertifikats. In diesen Fällen muss das Zertifikat entweder ein SAN-Zertifikat sein, das mehrere Namen umfasst, oder die Namen müssen ähnlich genug sein, damit ein Platzhalterzertifikat verwendet werden kann (vorausgesetzt, die Sicherheitsrichtlinien der Organisation lassen die Verwendung von Platzhalterzertifikaten zu).

  - Die erforderlichen Dienste müssen im zweiten Datencenter definiert werden. Wenn das erste Datencenter z. B. über drei verschiedene SMTP-URLs auf unterschiedlichen Transportservern verfügt, muss die entsprechende Konfiguration im zweiten Datencenter definiert werden, um zumindest einen (wenn nicht alle drei) Transportserver als Host für die Arbeitsauslastung zu aktivieren.

  - Zur Unterstützung des Datencenterswitchovers muss die erforderliche Netzwerkkonfiguration vorhanden sein. Es muss u. U. sichergestellt werden, dass die Konfigurationen für den Lastenausgleich vorhanden sind, das globale DNS konfiguriert und die Internetverbindung mit entsprechend konfiguriertem Routing aktiviert ist.

  - Die Strategie zur Aktivierung der DNS-Änderungen, die für einen Datencenterswitchover erforderlich sind, muss verstanden werden. Die bestimmten DNS-Änderungen, einschließlich der Einstellungen für die Gültigkeitsdauer, müssen definiert und dokumentiert werden, um die geltende Vereinbarung zum Servicelevel zu unterstützen.

  - Eine Strategie zum Testen der Lösung muss ebenso eingerichtet und in der Vereinbarung für den Servicelevel berücksichtigt werden. Die regelmäßige Überprüfung der Bereitstellung stellt die einzige Möglichkeit dar, um sicherzustellen, dass sich die Qualität und Durchführbarkeit der Bereitstellung im Lauf der Zeit nicht verschlechtern. Nach der Überprüfung der Bereitstellung wird empfohlen, dass der Teil der Konfiguration explizit dokumentiert wird, der sich direkt auf den Erfolg der Lösung auswirkt. Außerdem wird empfohlen, dass Sie Ihre Änderungsverwaltungsprozesse um diese Segmente der Bereitstellung herum erweitern.

Allgemeine Anforderungen

