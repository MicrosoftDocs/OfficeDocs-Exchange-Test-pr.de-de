---
title: 'Empf. für Dimensionierung und Konfig. von Exchange 2013: Exchange 2013-Hilfe'
TOCTitle: Empfehlungen für die Dimensionierung und Konfiguration von Exchange 2013
ms:assetid: 4c4ba2fc-014a-46fb-949a-2dabba92c4a5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn879075(v=EXCHG.150)
ms:contentKeyID: 63913009
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Empfehlungen für die Dimensionierung und Konfiguration von Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-03-27_

Exchange 2013 beansprucht mehr Systemressourcen als frühere Versionen von Exchange. Durch eine ordnungsgemäße Dimensionierung Ihrer Exchange 2013-Infrastruktur und anschließender empfohlener Konfiguration von Exchange-bezogenen Komponenten in dieser Infrastruktur können Sie die Grundlage für eine Bereitstellung mit optimaler Leistung bilden.

## Dimensionierung von Exchange 2013

Eine ordnungsgemäße Dimensionierung von Exchange 2013 ist eine der effektivsten Möglichkeiten zur Vermeidung von Leistungsproblemen. Der Exchange 2013 Server Role Requirements Calculator zum Berechnen der Serverrollenanforderungen ist [hier verfügbar](https://go.microsoft.com/fwlink/p/?linkid=523844). Die neueste Version ist 6.6, aber es wird empfohlen, die Seite regelmäßig nach Updates zu überprüfen. Für eine ordnungsgemäße Verwendung dieses Rechners sollten Sie die Anweisungen in den Blogbeiträgen [Exchange 2013 Server Role Requirements Calculator](https://go.microsoft.com/fwlink/p/?linkid=386677) und [Dimensionieren von Exchange 2013-Bereitstellungen](https://go.microsoft.com/fwlink/p/?linkid=301990) lesen.

Es ist wichtig, mit dem Rechner zu beginnen, bevor Sie Ihre Hardware erwerben und bereitstellen. Bestimmen Sie zunächst die gesamten Ressourcenanforderungen, basierend auf den Ergebnissen des Rechners. Sie können den Rechner verwenden, um die Anforderungen Ihrer Organisation einzugeben, und Ihre Hardware dann anhand der Ergebnisse skalieren. Der Rechner teilt Ihnen nicht mit, wie viele Server Sie verwenden sollten, ermöglicht Ihnen jedoch, die Auswirkungen einer Exchange-Arbeitsauslastung auf eine bestimmte Gruppe von Servern abzuschätzen. Experimentieren Sie mit verschiedenen Konfigurationen, um zu sehen, wie sich diese auf die Leistung auswirken, damit Sie die für Ihre Umgebung spezifischen Hardware- und Geschäftsanforderungen erfüllen können.

Zum Vereinfachen von Bereitstellungen und eine optimale Nutzung Ihrer Hardware empfiehlt die Exchange-Produktgruppe Server mit mehreren Rollen. Mit mehreren Rollen erhalten Sie eine bessere Verfügbarkeit auf der Clientzugriffsserver-Ebene, da mehr Clientzugriffsserver verfügbar sind, um Anforderungen während eines Fehlerszenarios zu verarbeiten. Die wichtigste Entwurfsüberlegung für Exchange 2013 ist die Verwendung „kleinerer“ handelsüblicher Server (für eine horizontale anstelle einer zentralen Skalierung). Design und Tests erfolgten mit Computern mit zwei Sockets und bis zu 20 Prozessorkernen mit bis zu 96 GB RAM. Wenn Ihre Hardware größer ist, sollten Sie andere Optionen in Betracht ziehen, z. B. die Verwendung dieser Hardware für andere Anforderungen und den Erwerb kleinerer Server für Ihre Exchange 2013-Umgebung oder Virtualisierung.

Sie sollten eher mehr Server erstellen (horizontale Skalierung), als Ressourcen zu vorhandenen, größeren Servern hinzufügen (zentrale Skalierung). Durch die horizontale Skalierung kann Ihre Umgebung die integrierten Hochverfügbarkeitsfeatures in Exchange 2013 nutzen. Um zu verstehen, warum diese Konfiguration empfohlen wird, lesen Sie die Beiträge [Die bevorzugte Architektur](https://go.microsoft.com/fwlink/p/?linkid=523782) und [Auswirkung der Ausfallsicherheit von Standorten auf die Verfügbarkeit](https://go.microsoft.com/fwlink/p/?linkid=523845) sorgfältig durch.

Der Rechner berücksichtigt keine Drittanbieterprodukte, die auf Exchange-Servern ausgeführt werden, oder Produkte, die mit Exchange interagieren (einschließlich intern entwickelter Anwendungen). Dies bedeutet, dass Sie sicherstellen müssen, diese während der Dimensionierung zu berücksichtigen. Beispielsweise können Lync Server und Exchange-Webdienste-Anwendungen (EWS) von Drittanbietern sowie ActiveSync-Geräte die CPU-Anforderungen pro Benutzer deutlich erhöhen. Informationen zu den jeweiligen Auswirkungen solcher Komponenten auf Exchange finden Sie in der Dokumentation zu den Drittanbieterprodukten. Es wird empfohlen, vor der Implementierung von Drittanbieterlösungen Grundwerte für die Leistung von Exchange zu erstellen.

## Empfohlene Leistungskonfigurationen

Die folgenden Leistungsoptimierungen werden für Ihre Exchange 2013-Umgebung empfohlen.

## Stromversorgung

Legen Sie im BIOS fest, dass das Betriebssystem die Stromversorgung verwalten kann.

Aktivieren Sie im Betriebssystem den Energiesparplan mit hoher Leistung.

## Verarbeitung

Deaktivieren Sie Hyperthreading auf physischen Exchange-Servern. Bei einer Virtualisierung kann das Hyperthreading auf dem physischen Server aktiviert werden, aber jeder virtuelle Server sollte nur der erforderlichen Anzahl von virtuellen CPUs zugeordnet werden (vermeiden Sie eine Überbelegung virtueller CPUs). Verwenden Sie für Dimensionierungsberechungen nur die Anzahl der physischen Prozessorkerne.

In Exchange Server 2013 Service Pack 1 oder höher können Sie die SSL-Verschiebung aktivieren, um die CPU-Auslastung von Clientzugriffsservern zu reduzieren. Die komplexe Konfiguration der SSL-Verschiebung wiegt die Vorteile möglicherweise jedoch nicht auf.

## .NET Framework


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange-Version</th>
<th>.NET Framework 4.7.1</th>
<th>.NET Framework 4.6.2</th>
<th>.NET Framework 4.6.1</th>
<th>.NET Framework 4.5.2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2013 CU19</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013 CU16 - CU18</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


Wenn Sie .Net 4.5.2 nicht installieren können, lesen Sie die Informationen im Microsoft Knowlege Base-Artikel 2995145 „[Leistungsprobleme oder Verzögerungen beim Herstellen einer Verbindung mit Exchange Server 2013 unter Windows Server](https://go.microsoft.com/fwlink/p/?linkid=524159)“. Die Korrekturen in diesem Artikel wurden basierend auf internen Ergebnissen zur Speicherauslastung des Store Worker-Prozesses entwickelt. Durch die Anwendung dieser Korrekturen verringern sich die gesamte Speicherauslastung für alle verwalteten Prozesse (einschließlich des Store Worker-Prozesses) und die Gesamt-CPU-Zeit, die für die automatische .NET-Speicherbereinigung aufgewendet wird.

## Hotfixes

Das Exchange-Leistungsteam empfiehlt die Installation aller der folgenden leistungsbezogenen Hotfixes.

  - [Verfügbarkeit eines Updates, das die Ausfallsicherheit der Cluster in Windows Server 2012 verbessert](https://go.microsoft.com/fwlink/p/?linkid=524088)

  - [Empfohlene Hotfixes und Updates für Windows Server 2012-basierte Failovercluster](https://go.microsoft.com/fwlink/p/?linkid=524089)

  - [Empfohlene Hotfixes und Updates für Windows Server 2012 R2-basierte Failovercluster](https://go.microsoft.com/fwlink/p/?linkid=524090)

  - [Falsche Zuordnung des RSS-Prozessors auf einem Windows 8- oder Windows Server 2012-basierten Computer mit Multi-Core-Prozessoren](https://go.microsoft.com/fwlink/p/?linkid=324140)

  - [Leistungsprobleme oder Verzögerungen beim Herstellen einer Verbindung mit Exchange Server 2013 unter Windows Server](https://go.microsoft.com/fwlink/p/?linkid=312962)

  - [Outlook-Verbindungsproblem, wenn SSLOffloading in Exchange 2013 „True“ ist](https://go.microsoft.com/fwlink/p/?linkid=524091)

  - [Lange Serververbindung für Outlook nach einem Datenbankfailover in Exchange Server 2013](https://go.microsoft.com/fwlink/p/?linkid=524092)

  - [Beeinträchtigung der Leistung in Outlook Web App, wenn Lync in Exchange Server 2013 integriert ist](https://go.microsoft.com/fwlink/p/?linkid=524093)

  - [EMS braucht sehr lang für die Ausführung des ersten Befehls in einer Exchange Server 2013-Umgebung mit dem kumulativen Update 5](https://go.microsoft.com/fwlink/p/?linkid=524094)

  - [Nachrichtenroutinglatenz, wenn IPv6 in Exchange Server 2013 aktiviert ist](https://go.microsoft.com/fwlink/p/?linkid=524095)

  - [Hohe CPU-Auslastung durch eine Anwendung, die von einem Microsoft LDAP-Client in Windows Server 2008 R2 SP1 abhängt](https://go.microsoft.com/fwlink/p/?linkid=530287)

  - [CPU-Auslastung ist hoch, wenn Sie RPC über HTTP-Protokoll in Windows 8.1 oder Windows Server 2012 R2 verwenden](https://go.microsoft.com/fwlink/p/?linkid=619127)

## Netzwerk

Für Exchange 2013 wird ein einzelner Netzwerkadapter empfohlen, da es nicht mehr notwendig ist, MAPI- und Replikationsnetzwerke aufzuteilen. Weitere Informationen finden Sie unter [Network requirements](planning-for-high-availability-and-site-resilience-exchange-2013-help.md).

Verwenden Sie die Standard-SNP-Verschiebungseinstellungen, sofern verfügbar, und stellen Sie sicher, dass RSS aktiviert ist (die Standardeinstellung in Windows Server 2012 und höher). RSS trägt dazu bei, die CPU-Auslastung zu skalieren, insbesondere bei 10 GbE.

Stellen Sie sicher, dass das Betriebssystem die Netzwerkkarte nicht ausschaltet, um Energie zu sparen.

Halten Sie NIC-Treiber auf dem neuesten Stand. Erkundigen Sie sich einmal im Monat bei Ihrem Anbieter, ob relevante Treiberupdates verfügbar sind.

## Internetinformationsdienste (IIS)

Während der Installation ändert Exchange einige Verbindungslimits für IIS. Es wird empfohlen, keine weitere Optimierung von IIS durchzuführen.

Vermeiden Sie Anpassungen, wann immer möglich. Jede Änderung an der web.config oder den Registrierungsschlüsseln kann von kumulativen Exchange-Updates oder Windows-Updates überschrieben werden.

## Speicher

Richtlinien für Exchange 2013-Speicher finden Sie unter [Exchange 2013-Speicherkonfigurationsoptionen](exchange-2013-storage-configuration-options-exchange-2013-help.md).

## Virtualisierung

Weitere Informationen finden Sie unter [Requirements for hardware virtualization](exchange-2013-virtualization-exchange-2013-help.md). Beachten Sie außerdem, dass Exchange NUMA (Non-Uniform Memory Access) unterstützt. Deshalb wird empfohlen, die Standard-NUMA-Einstellungen des Hardwareherstellers zu verwenden.

## Active Directory

Überwachen Sie die Leistung des Verzeichnisservers, da sich Active Directory-Abfragen direkt auf Ihre Exchange-Bereitstellung auswirken.

Die LDAP-Suchdauer ist ein wichtiger Leistungsindikator in Bezug auf die Active Directory-Integrität. Überwachen Sie die CPU auf Ihren Domänencontrollern. CPU-Probleme auf den Domänencontrollern werden als Leistungsspitze auf Exchange-Servern wiedergegeben.

Führen Sie die integrierte „Active Directory-Diagnose“ auf dem Domänencontroller im Systemmonitor unter „Datensammlersatz“ aus, um die Ursache von Leistungsproblemen im Domänencontroller zu ermitteln.

Planen Sie genügend RAM auf Domänencontrollern ein, um die vollständige AD-Datenbankdatei zwischenspeichern zu können.

Wir empfehlen die Bereitstellung von einem Kern für den globalen Active Directory-Katalog für jeweils acht Postfachkerne, die die aktive Last verarbeiten (basierend auf 64-Bit-Kernen für den globalen Katalog).

## Lastenausgleich

Alle Clientzugriffsserver sollten ungefähr dieselbe Anzahl eingehender Verbindungen empfangen.

Für alle Protokolle erfordert Exchange 2013 keine Sitzungsaffinität zwischen einem bestimmten Clientzugriffsserver und dem Lastenausgleich.

Ein Hardware- oder Softwarelastenausgleich sollte verwendet werden, um den gesamten eingehenden Datenverkehr zu Clientzugriffsservern zu verwalten. Die Auswahl des Zielservers kann mit Methoden wie „Roundrobin“ erfolgen, wobei jede eingehende Verbindung zum nächsten Server in einer Ringliste wechselt, oder mit „Least Connections“, wobei jede neue Verbindung vom Lastenausgleichsmodul an den Server mit den derzeit wenigsten aktiven Verbindungen gesendet wird. Diese Methoden werden ausführlich unter [Lastenausgleich](load-balancing-exchange-2013-help.md) beschrieben. Sie sollten auch Folgendes beachten:

  - Roundrobin hat das Problem einer langsamen Konvergenz mit langlebigen Verbindungen (wie RPC/HTTP). Wenn neue Computer online geschaltet werden, dauert es sehr lange, bis der Ausgleich der Verbindungen, die auf den Zielcomputern bereitgestellt werden, konvergiert ist.

  - Bei der „Least Connections“-Methode sollten Sie bedenken, dass ein Clientzugriffsserver während eines Ausfalls eines Clientzugriffsservers oder bei einer Patchwartung möglicherweise überlastet wird und nicht mehr reagiert. Im Kontext der Exchange-Leistung ist die Authentifizierung ein aufwändiger Vorgang.

Aufgrund einer Reihe von Einschränkungen mit dem Windows-Netzwerklastenausgleich in einer Exchange 2013-Umgebung, die detailliert unter [Lastenausgleich](load-balancing-exchange-2013-help.md) beschrieben sind, wird die Verwendung des Windows-Netzwerklastenausgleichs nicht empfohlen.

## Benutzer- und Datenbankenverteilung

Halten Sie eine ausgewogene Verteilung von Benutzern pro Datenbank und aktiven Datenbanken pro Server aufrecht. Verteilen Sie die Speicherplatzbelegung für Datenbanken gleichmäßig und Benutzer mit hohem Datenverkehrsaufkommen über alle Datenbanken.

Sie müssen Profile Ihrer Benutzerbasis erstellen, um zu verstehen, wie diese mit Exchange (Geräten, Outlook und OWA) interagieren, und welche Auswirkungen diese Interaktionen aus Leistungssicht haben. Informationen zum Erstellen von Profilen für die benutzerbasierte Exchange-Nutzung finden Sie in den Blogs zum Rechner, die in Abschnitt 2 aufgeführt sind.

Konfigurieren Sie die Einstellung für die Aktivierung von DB-Kopien und die Einstellungen für „MaximumPreferredActiveDatabases“ (pro Server), um die Balance bei einem Failover oder Switchover beizubehalten.

Mit dem Skript „RedistributeActiveDatabases.ps1“ können Sie aktive Datenbanken über die DAG-Knoten neu ausgleichen.

Erwägen Sie, strenge Einschränkungen für die Anzahl von Elementen zu erzwingen, die Office 365 entsprechen. Dafür können Sie das Cmdlet „Set-Mailbox“ und die Informationen unter [Begrenzungen für Postfachordner](https://go.microsoft.com/fwlink/p/?linkid=398779) verwenden.

## Auslagerungsdatei

Legen Sie eine maximale Größe für die Auslagerungsdatei von 32.778 MB fest, wenn Sie mehr als 32 GB RAM verwenden.

Die Auslagerungsdatei sollte nicht auf demselben Laufwerk wie Exchange-Datenbankdateien oder Datenbankprotokolldateien gehostet werden.

Es ist zwingend erforderlich, dass Sie eine feste Größe für die Auslagerungsdatei verwenden und nicht zulassen, dass Windows die Größe verwaltet. Das Erweitern der Auslagerungsdatei kann eine sehr ressourcenintensive Aufgabe sein und Probleme hervorrufen, wenn Exchange ausgelastet ist.

Wenn Sie ein vollständiges Kernel-Abbild benötigen, finden Sie weitere Informationen zu einer dedizierten Speicherabbilddatei im Microsoft Knowledge Base-Artikel 969028, [Generieren einer Kernel- oder vollständigen Speicherabbilddatei in Windows Server 2008 und Windows Server 2008 R2](https://go.microsoft.com/fwlink/p/?linkid=524044).

## Outlook-Modus

Es wird empfohlen, den Cachemodus zu verwenden. Informationen zu den Vorteilen der Verwendung des Cachemodus finden Sie unter [Wählen zwischen Exchange-Cache-Modus und Onlinemodus für Outlook 2013](https://go.microsoft.com/fwlink/p/?linkid=524045).

Sie sollten beachten, dass die Leistung sowohl von Server-Add-ins als auch von Outlook-Add-ins von Drittanbietern beeinträchtigt werden kann. Wenn Sie den Onlinemodus verwenden, können Sie für Clients einige Leistungsprobleme unter anderem durch Drittanbieter-Add-Ins, eine hohe Elementanzahl, eingeschränkte Ansichten und die Anzahl der Benutzer erwarten, den auf das Postfach zugreifen. Bei Legacyclients sind möglicherweise mehr von einer hohen Elementanzahl und der Leistung betroffen als in Outlook 2013.

Wenn die Konfiguration von Outlook im Onlinemodus in einer Organisation vor allem aufgrund von Sicherheitsbedenken erfolgt, sollten Sie stattdessen die Verwendung von BitLocker in Betracht ziehen.

Outlook 2013 bietet ein neues Synchronisierungsreglerfeature, um die Downloadzeit und die Größe der OST-Datei zu minimieren. Weitere Informationen finden Sie unter [Konfigurieren des Exchange-Cachemodus in Outlook 2013](https://go.microsoft.com/fwlink/p/?linkid=390456).

Überprüfen Sie einmal im Monat, ob Outlook-Clientupdates verfügbar sind, die in Ihrer Umgebung unterstützt werden.

## Software von Drittanbietern

Bewährte Praxis ist es, bei der Problembehandlung der Exchange-Leistung Software von Drittanbietern zu deinstallieren oder zu deaktivieren. Die folgende Liste enthält die Arten von Drittanbietersoftware, bei denen der Microsoft-Support am häufigsten Auswirkungen auf die Leistung von Exchange 2013 festgestellt hat.

  - Virenschutzlösungen

  - Eindringschutzsoftware

  - Sicherungssoftware

  - Überwachungssoftware für Dateien und Benutzer

  - Archivierungslösungen

