---
title: 'Exchange 2013-Speicherkonfigurationsoptionen: Exchange 2013 Help'
TOCTitle: Exchange 2013-Speicherkonfigurationsoptionen
ms:assetid: 37cdeacf-74f9-4399-9860-4d1dbec12bb1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee832792(v=EXCHG.150)
ms:contentKeyID: 50475477
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013-Speicherkonfigurationsoptionen

 

_**Gilt für:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Das grundlegende Verständnis der Speicheroptionen und Anforderungen für die Postfachserverrolle in Microsoft Exchange Server 2013 ist ein wichtiger Aspekt Ihrer Speicherentwurfslösung für den Postfachserver.

**Inhalt**

Speicherarchitekturen

Physische Datenträgertypen

Bewährte Methoden für unterstützte Speicherkonfigurationen

## Speicherarchitekturen

In der folgenden Tabelle werden unterstützte Speicherarchitekturen beschrieben und für die einzelnen Speicherarchitekturen ggf. Anleitungen zu bewährten Methoden bereitgestellt.

### Unterstützte Speicherarchitekturen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Speicherarchitektur</th>
<th>Beschreibung</th>
<th>Bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DAS (direkt angeschlossenes Speichersystem)</p></td>
<td><p>DAS ist ein digitales Speichersystem, das direkt an einen Server oder eine Arbeitsstation ohne zwischengeschaltetes Speichernetzwerk angeschlossen ist. Die DAS-Transportmöglichkeiten umfassen z. B. SAS (Serial Attached Small Computer System Interface) und SATA (Serial Attached Advanced Technology Attachment).</p></td>
<td><p>Nicht verfügbar.</p></td>
</tr>
<tr class="even">
<td><p>Storage Area Network (SAN): Internet Small Computer System Interface (iSCSI)</p></td>
<td><p>SAN ist eine Architektur, die Remotespeichergeräte für Computer (z. B. Datenträgerarrays und Bandarchive) derart an Server anschließt, dass die Geräte dem Betriebssystem als lokal angeschlossen angezeigt werden (z. B. Blockspeicher). iSCSI-SANs schließen SCSI-Befehle in IP-Pakete ein und verwenden die Standardnetzwerkinfrastruktur als Speichertransport (z. B. Ethernet).</p></td>
<td><p>Geben Sie keine physischen Datenträger, auf denen Exchange-Daten gesichert werden, für andere Anwendungen frei.</p>
<p>Verwenden Sie dedizierte Speichernetzwerke.</p>
<p>Verwenden Sie mehrere Netzwerkpfade für eigenständige Konfigurationen.</p></td>
</tr>
<tr class="odd">
<td><p>SAN: Fibre Channel</p></td>
<td><p>FC-SANs (Fibre Channel) schließen SCSI-Befehle in FC-Pakete ein und nutzen im Allgemeinen spezielle Fibre Channel-Netzwerke als Speichertransport.</p></td>
<td><p>Geben Sie keine physischen Datenträger, auf denen Exchange-Daten gesichert werden, für andere Anwendungen frei.</p>
<p>Verwenden Sie mehrere Fibre Channel-Netzwerkpfade für eigenständige Konfigurationen.</p>
<p>Befolgen Sie die bewährten Methoden des Speicheranbieters zum Abstimmen von Fibre Channel-Hostbusadaptern (HBA), z. B. die Warteschlangentiefe und das Warteschlangenziel.</p></td>
</tr>
</tbody>
</table>


Ein NAS-System (Network Attached Storage) ist ein mit einem Netzwerk verbundener eigenständiger Computer, der dem alleinigen Zweck dient, dateibasierte Datenspeicherdienste für andere Geräte im Netzwerk bereitzustellen. Das Betriebssystem und andere Software auf dem NAS-System stellen die Funktionalität für die Datenspeicherung, Dateisysteme und den Dateizugriff bereit und bieten außerdem die Verwaltung dieser Funktionen (z. B. Dateispeicherung).

Bei jedem vom Exchange verwendeten Speicher für Exchange-Daten muss es sich um Speicher auf Blockebene handeln, da Exchange 2013 die Verwendung von NAS-Volumes (Network Attached Storage) mit Ausnahme des in "[Exchange 2013-Virtualisierung](exchange-2013-virtualization-exchange-2013-help.md)" beschriebenen SMB 3.0-Szenarios nicht unterstützt. Außerdem wird in einer virtualisierten Umgebung NAS-Speicher, der für den Gast als Speicher auf Blockebene über den Hypervisor dargestellt wird, nicht unterstützt.

Die Verwendung von Speicherebenen wird nicht empfohlen, da diese sich negativ auf die Systemleistung auswirken kann. Aus diesem Grund lassen Sie nicht zu, dass der Speichercontroller die zuletzt geöffneten Dateien automatisch an "schnelleren" Speicher verschiebt.

Speicherarchitekturen

## Physische Datenträgertypen

In der folgenden Tabelle finden Sie eine Liste unterstützter physischer Datenträgertypen sowie ggf. Anleitungen zu bewährten Methoden für die einzelnen physischen Datenträger.

### Unterstützte physische Datenträgertypen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Physischer Datenträgertyp</th>
<th>Beschreibung</th>
<th>Unterstützt oder bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serial ATA (SATA)</p></td>
<td><p>SATA ist eine serielle Schnittstelle für ATA- und IDE-Datenträger (Integrated Device Electronics). SATA-Datenträger stehen mit einer Vielzahl von Formfaktoren, Geschwindigkeiten und Kapazitäten zur Verfügung.</p>
<p>Im Allgemeinen empfehlen sich SATA-Datenträger für Exchange 2013-Postfachspeicher, wenn folgende Anforderungen bestehen:</p>
<ul>
<li><p>Hohe Kapazität</p></li>
<li><p>Moderate Leistung</p></li>
<li><p>Moderater Energiebedarf</p></li>
</ul></td>
<td><p>Unterstützt:  Festplatten mit 512-Byte-Sektoren für Windows Server 2008 und Windows Server 2008 R2. Außerdem werden 512e-Festplatten für Windows Server 2008 R2 mit Folgendem unterstützt:</p>
<ul>
<li><p>Bei dem im folgenden Artikel beschriebenen <a href="https://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=982018">Microsoft Knowledge Base-Artikel 982018</a> Hotfix handelt es sich um ein Update, das die Kompatibilität von Windows 7 und Windows Server 2008 R2 mit Advanced Format-Datenträgern verbessert.</p></li>
<li><p>Windows Server 2008 R2 mit Service Pack 1 (SP1) und Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 und höher unterstützt Festplatten mit 4-KB-Sektoren und 512e-Festplatten. Für die Unterstützung müssen sich alle Kopien einer Datenbank auf demselben physischen Datenträgertyp befinden. Beispielsweise wird eine Konfiguration, bei der eine Kopie einer bestimmten Datenbank auf einer Festplatte mit 512-Byte-Sektoren und eine weitere Kopie derselben Datenbank auf einer 512e- oder 4K-Festplatte gespeichert ist, nicht unterstützt.</p>
<p>Bewährte Methode: Erwägen Sie die Verwendung von SATA-Datenträgern, die im Allgemeinen über bessere Merkmale bei Hitze, Vibration und Zuverlässigkeit verfügen.</p></td>
</tr>
<tr class="even">
<td><p>Serial Attached SCSI</p></td>
<td><p>SAS (Serial Attached SCSI) ist eine serielle Schnittstelle für SCSI-Datenträger. SAS-Datenträger stehen mit einer Vielzahl von Formfaktoren, Geschwindigkeiten und Kapazitäten zur Verfügung.</p>
<p>Im Allgemeinen empfehlen sich SAS-Datenträger für Exchange 2013-Postfachspeicher, wenn folgende Anforderungen bestehen:</p>
<ul>
<li><p>Moderate Kapazität</p></li>
<li><p>Hohe Leistung</p></li>
<li><p>Moderater Energiebedarf</p></li>
</ul></td>
<td><p>Unterstützt:  Festplatten mit 512-Byte-Sektoren für Windows Server 2008 und Windows Server 2008 R2. Außerdem werden 512e-Festplatten für Windows Server 2008 R2 mit Folgendem unterstützt:</p>
<ul>
<li><p>Bei dem im folgenden Artikel beschriebenen <a href="https://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=982018">Microsoft Knowledge Base-Artikel 982018</a> Hotfix handelt es sich um ein Update, das die Kompatibilität von Windows 7 und Windows Server 2008 R2 mit Advanced Format-Datenträgern verbessert.</p></li>
<li><p>Windows Server 2008 R2 mit Service Pack 1 (SP1) und Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 und höher unterstützt Festplatten mit 4-KB-Sektoren und 512e-Festplatten. Für die Unterstützung müssen sich alle Kopien einer Datenbank auf demselben physischen Datenträgertyp befinden. Beispielsweise wird eine Konfiguration, bei der eine Kopie einer bestimmten Datenbank auf einer Festplatte mit 512-Byte-Sektoren und eine weitere Kopie derselben Datenbank auf einer 512e- oder 4K-Festplatte gespeichert ist, nicht unterstützt.</p>
<p>Bewährte Methode: Der Schreibcache für physische Datenträger muss deaktiviert werden, wenn keine unterbrechungsfreie Stromversorgung (USV) verwendet wird.</p></td>
</tr>
<tr class="odd">
<td><p>Fibre Channel</p></td>
<td><p>Fibre Channel ist eine Schnittstelle für den Anschluss von Datenträgern an SANs, die auf Fibre Channel basieren. Fibre Channel-Datenträger sind mit verschiedenen Geschwindigkeiten und Kapazitäten verfügbar.</p>
<p>Im Allgemeinen empfehlen sich Fibre Channel-Datenträger für Exchange 2013-Postfachspeicher, wenn folgende Anforderungen bestehen:</p>
<ul>
<li><p>Moderate Kapazität</p></li>
<li><p>Hohe Leistung</p></li>
<li><p>SAN-Konnektivität</p></li>
</ul></td>
<td><p>Unterstützt:  Festplatten mit 512-Byte-Sektoren für Windows Server 2008 und Windows Server 2008 R2. Außerdem werden 512e-Festplatten für Windows Server 2008 R2 mit Folgendem unterstützt:</p>
<ul>
<li><p>Bei dem im folgenden Artikel beschriebenen <a href="https://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=982018">Microsoft Knowledge Base-Artikel 982018</a> Hotfix handelt es sich um ein Update, das die Kompatibilität von Windows 7 und Windows Server 2008 R2 mit Advanced Format-Datenträgern verbessert.</p></li>
<li><p>Windows Server 2008 R2 mit Service Pack 1 (SP1) und Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 und höher unterstützt Festplatten mit 4-KB-Sektoren und 512e-Festplatten. Für die Unterstützung müssen sich alle Kopien einer Datenbank auf demselben physischen Datenträgertyp befinden. Beispielsweise wird eine Konfiguration, bei der eine Kopie einer bestimmten Datenbank auf einer Festplatte mit 512-Byte-Sektoren und eine weitere Kopie derselben Datenbank auf einer 512e- oder 4K-Festplatte gespeichert ist, nicht unterstützt.</p>
<p>Bewährte Methode: Der Schreibcache für physische Datenträger muss deaktiviert werden, wenn keine unterbrechungsfreie Stromversorgung (USV) verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>Solid-State-Datenträger (SSD) (Flashlaufwerk)</p></td>
<td><p>Ein SSD ist ein Datenspeichergerät, das Festkörperspeicher zum Speichern beständiger Daten verwendet. Ein SSD emuliert die Schnittstelle eines Festplattenlaufwerks. SSD-Datenträger sind mit verschiedenen Geschwindigkeiten (unterschiedliche E/A-Leistung) und Kapazitäten verfügbar.</p>
<p>Im Allgemeinen empfehlen sich SSD-Datenträger für Exchange 2013-Postfachspeicher, wenn folgende Anforderungen bestehen:</p>
<ul>
<li><p>Geringe Kapazität</p></li>
<li><p>Sehr hohe Leistung</p></li>
</ul></td>
<td><p>Unterstützt:  Festplatten mit 512-Byte-Sektoren für Windows Server 2008 und Windows Server 2008 R2. Außerdem werden 512e-Festplatten für Windows Server 2008 R2 mit Folgendem unterstützt:</p>
<ul>
<li><p>Bei dem im folgenden Artikel beschriebenen <a href="https://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=982018">Microsoft Knowledge Base-Artikel 982018</a> Hotfix handelt es sich um ein Update, das die Kompatibilität von Windows 7 und Windows Server 2008 R2 mit Advanced Format-Datenträgern verbessert.</p></li>
<li><p>Windows Server 2008 R2 mit Service Pack 1 (SP1) und Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 und höher unterstützt Festplatten mit 4-KB-Sektoren und 512e-Festplatten. Für die Unterstützung müssen sich alle Kopien einer Datenbank auf demselben physischen Datenträgertyp befinden. Beispielsweise wird eine Konfiguration, bei der eine Kopie einer bestimmten Datenbank auf einer Festplatte mit 512-Byte-Sektoren und eine weitere Kopie derselben Datenbank auf einer 512e- oder 4K-Festplatte gespeichert ist, nicht unterstützt.</p>
<p>Bewährte Methode: Der Schreibcache für physische Datenträger muss deaktiviert werden, wenn keine unterbrechungsfreie Stromversorgung (USV) verwendet wird.</p>
<p>Im Allgemeinen erfordern Exchange 2013-Postfachserver nicht die Leistungsmerkmale von SSD-Speicher.</p></td>
</tr>
</tbody>
</table>


## Faktoren bei der Auswahl von Datenträgertypen

Bei der Auswahl von Datenträgertypen für Exchange 2013-Speicher müssen verschiedene Faktoren gegeneinander abgewogen werden. Der richtige Datenträger bietet das richtige Verhältnis von Leistung (sowohl sequenziell als auch zufällig) und Kapazität, Zuverlässigkeit, Energiebedarf sowie Kosten. Die folgende Tabelle unterstützter physischer Datenträgertypen bietet Informationen, die Ihnen bei der Berücksichtigung dieser Faktoren helfen.

Aus Leistungssicht ist die Verwendung größerer, langsamerer Datenträger für Exchange-Speicher in Ordnung, vorausgesetzt, dass die Datenträger unter Auslastung eine durchschnittliche Lese- und Schreibwartezeit von 20 ms oder weniger aufrechterhalten können.

### Faktoren bei der Auswahl des Datenträgertyps

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Datenträgergeschwindigkeit (RPM)</th>
<th>Datenträgerformfaktor</th>
<th>Schnittstelle oder Transport</th>
<th>Kapazität</th>
<th>Zufällige E/A-Leistung</th>
<th>Sequenzielle E/A-Leistung</th>
<th>Energiebedarf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5,400</p></td>
<td><p>2,5 Zoll</p></td>
<td><p>SATA</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Unzureichend</p></td>
<td><p>Unzureichend</p></td>
<td><p>Hervorragend</p></td>
</tr>
<tr class="even">
<td><p>5,400</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>SATA</p></td>
<td><p>Hervorragend</p></td>
<td><p>Unzureichend</p></td>
<td><p>Unzureichend</p></td>
<td><p>Überdurchschnittlich</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>2,5 Zoll</p></td>
<td><p>SATA</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Hervorragend</p></td>
</tr>
<tr class="even">
<td><p>7,200</p></td>
<td><p>2,5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Hervorragend</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>SATA</p></td>
<td><p>Hervorragend</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
</tr>
<tr class="even">
<td><p>7,200</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Hervorragend</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Fibre Channel</p></td>
<td><p>Hervorragend</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Durchschnittlich</p></td>
</tr>
<tr class="even">
<td><p>10,000</p></td>
<td><p>2,5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Unterdurchschnittlich</p></td>
<td><p>Hervorragend</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
</tr>
<tr class="odd">
<td><p>10,000</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>SATA</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
</tr>
<tr class="even">
<td><p>10,000</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Unterdurchschnittlich</p></td>
</tr>
<tr class="odd">
<td><p>10,000</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Fibre Channel</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Überdurchschnittlich</p></td>
<td><p>Unterdurchschnittlich</p></td>
</tr>
<tr class="even">
<td><p>15,000</p></td>
<td><p>2,5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Unzureichend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Durchschnittlich</p></td>
</tr>
<tr class="odd">
<td><p>15,000</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Hervorragend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Unterdurchschnittlich</p></td>
</tr>
<tr class="even">
<td><p>15,000</p></td>
<td><p>3.5 Zoll</p></td>
<td><p>Fibre Channel</p></td>
<td><p>Durchschnittlich</p></td>
<td><p>Hervorragend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Unzureichend</p></td>
</tr>
<tr class="odd">
<td><p>SSD: Unternehmensklasse</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>SATA, Serial Attached SCSI, Fibre Channel</p></td>
<td><p>Unzureichend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Hervorragend</p></td>
<td><p>Hervorragend</p></td>
</tr>
</tbody>
</table>


Speicherarchitekturen

## Bewährte Methoden für unterstützte Speicherkonfigurationen

In diesem Abschnitt werden Informationen zu bewährten Methoden für unterstützte Konfigurationen von Datenträgern und Arraycontrollern bereitgestellt.

RAID (Redundant Array of Independent Disks) wird häufig verwendet, um sowohl Leistungsmerkmale von einzelnen Datenträgern zu verbessern (indem Datenstripesets auf verschiedenen Datenträgern verwendet werden) als auch Schutz vor einzelnen Datenträgerfehlern zu bieten. Durch die Weiterentwicklungen hinsichtlich der Hochverfügbarkeit von Exchange 2013 ist RAID keine erforderliche Komponente für den Speicherentwurf von Exchange 2013. RAID ist jedoch weiterhin eine wesentliche Komponente im Exchange 2013-Speicherdesign für eigenständige Server sowie für Lösungen, die Fehlertoleranz für den Speicher erfordern.

**Betriebssystem, System oder Auslagerungsdateivolume**

Die empfohlene Konfiguration für ein Betriebssystem, System oder Auslagerungsdateivolume beseht in der Verwendung der RAID-Technologie, um diesen Datentyp zu schützen. Die empfohlene RAID-Konfiguration ist RAID-1 oder RAID-1/0, es werden jedoch alle RAID-Typen unterstützt.

**Getrennte Postfachdatenbank- und Protokollvolumes**

Wenn Sie eine eigenständige Postfach-Serverrollenarchitektur bereitstellen, ist die RAID-Technologie für Postfachdatenbank- und Protokollvolumes erforderlich. Die empfohlene RAID-Konfiguration für Postfachvolumes lautet RAID-1/0 (insbesondere bei Verwendung von 5.4K- oder 7.2K-Datenträgern). Es werden jedoch alle RAID-Typen unterstützt. Für Protokollvolumes ist RAID-1 oder RAID-1/0 die empfohlene RAID-Konfiguration.

Beachten Sie bei der Verwendung von RAID-5- oder RAID-6-Konfigurationen für das Betriebssystem, das System oder die Auslagerungsdatei oder Exchange-Datenvolumes Folgendes:

  - Für RAID-5-Konfigurationen, einschließlich Variationen wie RAID-50 und RAID-51, sollten nicht mehr als 7 Datenträger pro Arraygruppe verwendet werden und die Bereinigung mit hoher Priorität sowie Oberflächenüberprüfung für Arraycontroller aktiviert sein.

  - Bei RAID-6-Konfigurationen sollte die Bereinigung mit hoher Priorität und die Oberflächenüberprüfung für Arraycontroller aktiviert sein.

Obwohl JBOD in Architekturen mit hoher Verfügbarkeit, die drei oder mehr hochverfügbare Datenbankkopien aufweisen, unterstützt wird, da die Protokoll- und Postfachdatenbank-Volumes voneinander getrennt sind, wird JBOD nicht empfohlen.

**Zusammenstellung von Postfachdatenbank- und Protokollvolumes**

Die Zusammenstellung von Postfachdatenbank- und Protokollvolumes wird in eigenständigen Architekturen nicht empfohlen. In Architekturen mit hoher Verfügbarkeit gibt es zwei Möglichkeiten für dieses Szenario:

1.  Einzelne Datenbank pro Volume

2.  Mehrere Datenbanken pro Volume

**Einzelne Datenbank pro Volume**

Im Rahmen von Exchange bedeutet JBOD, dass sowohl die Datenbank als auch die zugeordneten Protokolle auf einem einzelnen Datenträger gespeichert werden. Bei der Bereitstellung auf mehreren Festplatten (JBOD) müssen Sie mindestens drei hochverfügbare Datenbankkopien bereitstellen. Die Verwendung eines einzelnen Datenträgers führt zu einer einzelnen Fehlerquelle, da bei einem Ausfall des Datenträgers die darauf befindliche Datenbankkopie verloren geht. Ein Minimum von drei Datenbankkopien sorgt für Fehlertoleranz, da bei einem Ausfall der Kopie (oder eines Datenträgers) zwei zusätzliche Kopien vorhanden sind. Die Platzierung von drei hochverfügbaren Datenbankkopien und die Verwendung verzögerter Datenbankkopien müssen jedoch beim Speicherentwurf berücksichtigt werden. Die folgende Tabelle enthält Richtlinien für RAID und JBOD.

### Überlegungen zu RAID oder JBOD

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Rechenzentrumsserver</th>
<th>Zwei hochverfügbare Kopien (gesamt)</th>
<th>Drei hochverfügbare Kopien (gesamt)</th>
<th>Mindestens zwei hochverfügbare Kopien pro Rechenzentrum</th>
<th>Eine verzögerte Kopie</th>
<th>Zwei oder mehr verzögerte Kopien pro Rechenzentrum</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Primäre Rechenzentrumsserver</p></td>
<td><p>RAID</p></td>
<td><p>RAID oder JBOD (zwei Kopien)</p></td>
<td><p>RAID oder JBOD</p></td>
<td><p>RAID</p></td>
<td><p>RAID oder JBOD</p></td>
</tr>
<tr class="even">
<td><p>Sekundäre Rechenzentrumsserver</p></td>
<td><p>RAID</p></td>
<td><p>RAID (eine Kopie)</p></td>
<td><p>RAID oder JBOD</p></td>
<td><p>RAID</p></td>
<td><p>RAID oder JBOD</p></td>
</tr>
</tbody>
</table>


Bei der Bereitstellung auf mehreren Festplatten (JBOD) für primäre Rechenzentrumsserver sind mindestens drei hochverfügbare Kopien in der DAG erforderlich. Wenn Sie verzögerte Kopien und hochverfügbare Datenbankkopien auf demselben Server kombinieren (wenn Sie also keine dedizierten Server für die verzögerten Datenbankkopien verwenden), sind mindestens zwei verzögerte Datenbankkopien erforderlich.

Auf sekundären Rechenzentrumsservern, die JBOD verwenden, sollten mindestens zwei hochverfügbare Datenbankkopien im sekundären Rechenzentrum bereitgestellt werden. Der Verlust einer Kopie im sekundären Rechenzentrum führt nicht zu einem erneuten Seeding im Fernnetz oder einer einzelnen Fehlerquelle bei der Aktivierung des sekundären Rechenzentrums. Wenn Sie verzögerte Datenbankkopien und hochverfügbare Datenbankkopien auf demselben Server kombinieren (wenn Sie also keine dedizierten Server für die verzögerten Datenbankkopien verwenden), sind mindestens zwei verzögerte Datenbankkopien erforderlich.

Bei dedizierten Servern für die verzögerten Datenbankkopien müssen mindestens zwei verzögerte Datenbankkopien im Rechenzentrum vorhanden sein, um JBOD verwenden zu können. Andernfalls führt der Verlust eines Datenträgers zum Verlust der verzögerten Datenbankkopie sowie zum Verlust des Schutzmechanismus.

**Mehrere Datenbanken pro Volume**

Mehrere Datenbanken pro Volume ist ein neues JBOD-Szenario in Exchange 2013, das aktive und passive Kopien (einschließlich verzögerter Kopien) zusammen auf einem einzelnen Datenträger zulässt, um eine bessere Datenträgerverwendung zu ermöglichen. Jedoch muss die automatische Wiedergabe verzögerter Protokolldateikopien aktiviert sei, um verzögerte Kopien auf diese Weise bereitzustellen. In der folgenden Tabelle sind Richtlinien für Überlegungen zu JBOD für mehrere Datenbanken pro Volume aufgeführt.

### Überlegungen zu JBOD

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Rechenzentrumsserver</th>
<th>3 oder mehr Kopien (insgesamt)</th>
<th>Zwei oder mehr Kopien pro Rechenzentrum</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Primäre Rechenzentrumsserver</p></td>
<td><p>JBOD</p></td>
<td><p>JBOD</p></td>
</tr>
<tr class="even">
<td><p>Sekundäre Rechenzentrumsserver</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>JBOD</p></td>
</tr>
</tbody>
</table>


Die folgende Tabelle enthält Anleitungen zu Speicherarraykonfigurationen für Exchange 2013.

### Unterstützte RAID-Typen für die Exchange 2013-Postfachserverrolle

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>RAID-Typ</th>
<th>Beschreibung</th>
<th>Unterstützt oder bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RAID-Stripesetgröße für Datenträgerarray (KB)</p></td>
<td><p>Die Stripesetgröße gibt die Einheit pro Datenträger der Datenverteilung innerhalb des RAID-Satzes an. Die Stripesetgröße wird auch als <em>Blockgröße</em> bezeichnet.</p></td>
<td><p>Bewährte Methode: 256 KB oder mehr. Befolgen Sie die bewährten Methoden des Anbieters.</p></td>
</tr>
<tr class="even">
<td><p>Cacheeinstellungen für Speicherarray</p></td>
<td><p>Die von einem batteriegepufferten Arraycontroller für das Caching bereitgestellten Cacheeinstellungen.</p></td>
<td><p>Bewährte Methode: 100 Prozent für Schreibcache (batteriegepufferter Cache oder Flash-Cache) für DAS-Speichercontroller in einer RAID- oder JBOD-Konfiguration. 75 Prozent für Schreibcache, 25 Prozent für Lesecache (batteriegepufferter Cache oder Flash-Cache) für andere Typen von Speicherlösungen, z. B. SAN. Wenn Ihr SAN-Anbieter über andere bewährte Methoden für die Cachekonfiguration auf ihrer Plattform verfügt, befolgen Sie die Anweisungen Ihres SAN-Anbieters.</p></td>
</tr>
<tr class="odd">
<td><p>Caching für Schreibvorgänge auf physischen Datenträgern</p></td>
<td><p>Die Einstellungen für den Cache befinden sich auf den einzelnen Datenträgern.</p></td>
<td><p>Unterstützt: Der Schreibcache für physische Datenträger muss deaktiviert werden, wenn keine unterbrechungsfreie Stromversorgung (USV) verwendet wird.</p></td>
</tr>
</tbody>
</table>


Die folgende Tabelle enthält Anleitungen zur Auswahl von Datenbank- und Protokolldateien.

### Auswahl der Datenbank- und Protokolldateien für die Exchange 2013-Postfachserverrolle

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Datenbank- und Protokolldateioptionen</th>
<th>Beschreibung</th>
<th>Eigenständig: Unterstützt oder bewährte Methode</th>
<th>Hohe Verfügbarkeit: Unterstützt oder bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dateiposition: Datenbank pro Protokollisolation</p></td>
<td><p>Die Angabe von Datenbank pro Protokollisolation bezieht sich auf das Positionieren der Datenbankdatei und der Protokolle von derselben Postfachdatenbank auf verschiedenen Volumes, die auf unterschiedlichen physischen Datenträgern gesichert werden.</p></td>
<td><p>Bewährte Methode: Verschieben Sie zum Zweck der Wiederherstellbarkeit die Datenbankdatei (EDB) und die Protokolle von derselben Datenbank auf verschiedene Volumes, die auf unterschiedlichen physischen Datenträgern gesichert werden.</p></td>
<td><p>Unterstützt: Isolierung von Protokollen und Datenbanken ist nicht erforderlich.</p></td>
</tr>
<tr class="even">
<td><p>Dateiposition: Datenbankdateien pro Volume</p></td>
<td><p>Die Angabe von Datenbankdateien pro Volume bezieht sich darauf, wie die Datenbankdateien innerhalb von Datenträgervolumes oder datenträgerübergreifend verteilt werden.</p></td>
<td><p>Bewährte Methode: Abhängig von der Sicherungsmethode.</p></td>
<td><p>Unterstützt: Erstellen Sie bei Verwendung von JBOD ein Volume mit unterschiedlichen Verzeichnissen für Datenbanken und Protokolldateien.</p></td>
</tr>
<tr class="odd">
<td><p>Dateiposition: Protokolldatenströme pro Volume</p></td>
<td><p>Die Angabe von Protokolldatenströmen pro Volume bezieht sich darauf, wie die Datenbankprotokolldateien innerhalb von Datenträgervolumes oder datenträgerübergreifend verteilt werden.</p></td>
<td><p>Bewährte Methode: Abhängig von der Sicherungsmethode.</p></td>
<td><p>Unterstützt: Erstellen Sie bei Verwendung von JBOD ein Volume mit unterschiedlichen Verzeichnissen für Datenbanken und Protokolldateien.</p>
<p>Bewährte Methode: Übernehmen Sie bei Verwendung von JBOD mehrere Datenbanken pro Volume.</p></td>
</tr>
<tr class="even">
<td><p>Datenbankgröße</p></td>
<td><p>Die Datenbankgröße bezieht sich auf die Größe der Datenbankdatei (EDB) auf dem Datenträger.</p></td>
<td><p>Unterstützt: Ungefähr 16 TB (Terabyte).</p>
<p>Bewährte Methode:</p>
<ul>
<li><p>200 GB (Gigabyte) oder weniger.</p></li>
<li><p>Bereitstellung für 120 Prozent der berechneten maximalen Datenbankgröße.</p></li>
</ul></td>
<td><p>Unterstützt: Ungefähr 16 TB (Terabyte).</p>
<p>Bewährte Methode:</p>
<ul>
<li><p>2 TB oder weniger.</p></li>
<li><p>Bereitstellung für 120 Prozent der berechneten maximalen Datenbankgröße.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Protokollabschneidemethode</p></td>
<td><p>Die Protokollabschneidemethode ist der Prozess zum Abschneiden und Löschen alter Protokolldateien der Datenbank. Es gibt zwei Mechanismen:</p>
<ul>
<li><p>Umlaufprotokollierung, bei der die Protokolle von Exchange gelöscht werden.</p></li>
<li><p>Abschneiden der Protokolle nach einer erfolgreichen vollständigen oder inkrementellen VSS-Sicherung (Volume Shadow Copy Service, Volumeschattenkopie-Dienst).</p></li>
</ul></td>
<td><p>Bewährte Methode:</p>
<ul>
<li><p>Verwenden Sie Sicherungen für das Abschneiden der Protokolle (z. B. deaktivierte Umlaufprotokollierung).</p></li>
<li><p>Bereitstellung für drei Tage Protokollgenerierungskapazität.</p></li>
</ul></td>
<td><p>Bewährte Methode:</p>
<ul>
<li><p>Aktivieren Sie die Umlaufprotokollierung für Bereitstellungen, die Datenschutzfunktionen von Exchange verwenden.</p></li>
<li><p>Bereitstellung für drei Tage Protokollgenerierungskapazität, über die Einstellung der Wiedergabeverzögerung hinaus.</p></li>
</ul></td>
</tr>
</tbody>
</table>


Die folgende Tabelle enthält Anleitungen zu Windows-Datenträgertypen.

### Windows-Datenträgertypen für die Exchange 2013-Postfachserverrolle

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows-Datenträgertyp</th>
<th>Beschreibung</th>
<th>Eigenständig: Unterstützt oder bewährte Methode</th>
<th>Hohe Verfügbarkeit: Unterstützt oder bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Basisdatenträger</p></td>
<td><p>Ein für die einfache Speicherung initialisierter Datenträger wird als Basisdatenträger bezeichnet. Ein Basisdatenträger enthält Basisvolumes, z. B. Primärpartitionen, erweiterte Partitionen oder logische Laufwerke.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Verwenden Sie Basisdatenträger.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Verwenden Sie Basisdatenträger.</p></td>
</tr>
<tr class="even">
<td><p>Dynamischer Datenträger</p></td>
<td><p>Ein für die dynamische Speicherung initialisierter Datenträger wird als dynamischer Datenträger bezeichnet. Ein dynamischer Datenträger enthält dynamische Volumes, z. B. einfache Volumes, übergreifende Volumes, Stripesetvolumes, gespiegelte Volumes oder RAID-5-Volumes.</p></td>
<td><p>Unterstützt.</p></td>
<td><p>Unterstützt.</p></td>
</tr>
</tbody>
</table>


Die folgende Tabelle enthält Anleitungen zu Volumekonfigurationen.

### Volumekonfigurationen für die Exchange 2013-Postfachserverrolle

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Volumekonfiguration</th>
<th>Beschreibung</th>
<th>Eigenständig: Unterstützt oder bewährte Methode</th>
<th>Hohe Verfügbarkeit: Unterstützt oder bewährte Methode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>GUID-Partitionstabelle (GPT)</p></td>
<td><p>GPT ist eine Datenträgerarchitektur, die das ältere MBR-Partitionierungsschema (Master Boot Record) erweitert. Die maximale Größe für NTFS-formatierte Partitionen beträgt 256 TB.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Verwenden Sie GPT-Partitionen.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Verwenden Sie GPT-Partitionen.</p></td>
</tr>
<tr class="even">
<td><p>MBR</p></td>
<td><p>Ein MBR oder Partitionssektor ist der 512 Byte große Bootsektor, bei dem es sich um den ersten Sektor (LBA-Sektor 0) eines partitionierten Datenspeichergeräts handelt, z. B. einer Festplatte. Die maximale Größe für NTFS-formatierte Partitionen beträgt 2 TB.</p></td>
<td><p>Unterstützt.</p></td>
<td><p>Unterstützt.</p></td>
</tr>
<tr class="odd">
<td><p>Partitionsausrichtung</p></td>
<td><p>Die Partitionsausrichtung bezieht sich auf die Ausrichtung von Partitionen an Sektorgrenzen, um eine optimale Leistung zu erreichen.</p></td>
<td><p>Unterstützt: Die Standardeinstellung für Windows Server 2008 R2 und Windows Server 2012 lautet 1 Megabyte (MB).</p></td>
<td><p>Unterstützt: Die Standardeinstellung für Windows Server 2008 R2 und Windows Server 2012 lautet 1 MB.</p></td>
</tr>
<tr class="even">
<td><p>Volumepfad</p></td>
<td><p>Der Volumepfad bezieht sich auf die Zugriffsmethode für ein Volume.</p></td>
<td><p>Unterstützt: Laufwerkbuchstabe oder Einbindungsspunkt.</p>
<p>Bewährte Methode: Das Hostvolume für den Einbindungspunkt muss für RAID aktiviert sein.</p></td>
<td><p>Unterstützt: Laufwerkbuchstabe oder Einbindungsspunkt.</p>
<p>Bewährte Methode: Das Hostvolume für den Einbindungspunkt muss für RAID aktiviert sein.</p></td>
</tr>
<tr class="odd">
<td><p>Dateisystem</p></td>
<td><p>Das Dateisystem ist eine Methode zum Speichern und Anordnen von Computerdateien und der darin enthaltenen Daten, damit diese einfach zu finden sind und leicht darauf zugegriffen werden kann.</p></td>
<td><p>Unterstützt: NTFS und ReFS.</p></td>
<td><p>Unterstützt: NTFS und ReFS.</p></td>
</tr>
<tr class="even">
<td><p>NTFS-Defragmentierung</p></td>
<td><p>Die NTFS-Defragmentierung ist ein Prozess zur Reduzierung des Fragmentierungsumfangs in Windows-Dateisystemen. Dies wird durch die physische Anordnung der Datenträgerinhalte erreicht, bei der die Teile der einzelnen Dateien dicht beieinander und angrenzend gespeichert werden.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Nicht erforderlich und nicht empfohlen. Es wird auch empfohlen, unter Windows Server 2012 das Feature für die automatische Optimierung und Fragmentierung von Datenträgern zu deaktivieren.</p></td>
<td><p>Unterstützt.</p>
<p>Bewährte Methode: Nicht erforderlich und nicht empfohlen. Es wird auch empfohlen, unter Windows Server 2012 das Feature für die automatische Optimierung und Fragmentierung von Datenträgern zu deaktivieren.</p></td>
</tr>
<tr class="odd">
<td><p>Einheitengröße für die NTFS-Zuordnung</p></td>
<td><p>Die Einheitengröße für die NTFS-Zuordnung stellt die kleinste Menge an Datenträgerspeicherplatz dar, die für das Ablegen einer Datei zugeordnet werden kann.</p></td>
<td><p>Unterstützt: Alle Größen von Zuordnungseinheiten.</p>
<p>Bewährte Methode: 64 KB für EDB- und Protokolldateivolumes.</p></td>
<td><p>Unterstützt: Alle Größen von Zuordnungseinheiten.</p>
<p>Bewährte Methode: 64 KB für EDB- und Protokolldateivolumes.</p></td>
</tr>
<tr class="even">
<td><p>NTFS-Komprimierung</p></td>
<td><p>Die NTFS-Komprimierung beschreibt den Prozess der Reduzierung der tatsächlichen Größe einer Datei, die auf der Festplatte gespeichert wird.</p></td>
<td><p>Unterstützt: Nicht unterstützt für Exchange-Datenbank- oder Protokolldateien.</p></td>
<td><p>Unterstützt: Nicht unterstützt für Exchange-Datenbank- oder Protokolldateien.</p></td>
</tr>
<tr class="odd">
<td><p>NTFS-verschlüsseltes Dateisystem (Encrypting File System, EFS)</p></td>
<td><p>EFS ermöglicht es Benutzern, einzelne Dateien, Ordner oder gesamte Datenlaufwerke zu verschlüsseln. Da EFS eine starke Verschlüsselung über Industriestandardalgorithmen und die Verschlüsselung mit öffentlichen Schlüsseln bietet, sind verschlüsselte Dateien geheim, selbst wenn ein Angreifer die Systemsicherheit umgeht.</p></td>
<td><p>Unterstützt: Nicht unterstützt für Exchange-Datenbank- oder Protokolldateien.</p></td>
<td><p>Nicht unterstützt für Exchange-Datenbank- oder Protokolldateien.</p></td>
</tr>
<tr class="even">
<td><p>Windows BitLocker (Volumeverschlüsselung)</p></td>
<td><p>Windows BitLocker ist eine Datenschutzfunktion in Windows Server 2008. BitLocker schützt Daten vor Diebstahl oder Offenlegung auf Computern, die verloren oder gestohlen wurden und bietet einen sichereren Löschvorgang für Daten, wenn Computer außer Betrieb genommen werden.</p></td>
<td><p>Unterstützt: Alle Exchange-Datenbank- und Protokolldateien.</p></td>
<td><p>Unterstützt: Sämtliche Exchange-Datenbank- und Protokolldateien. Für Windows-Failovercluster sind Windows Server 2008 R2 oder Windows Server 2008 R2 SP1 sowie der folgende Hotfix erforderlich: <a href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=2446607">In Windows Server 2008 R2 ist es nicht möglich, BitLocker auf einem Datenträgervolume zu aktivieren, wenn der Computer ein Failoverclusterknoten ist</a>. Exchange-Volumes mit Bitlocker-Aktivierung werden auf Windows-Failoverclustern unter früheren Windows-Versionen nicht unterstützt.</p>
<p>Weitere Informationen zur Windows 7-BitLocker-Verschlüsselung finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=220898">BitLocker-Laufwerksverschlüsselung in Windows 7: Häufig gestellte Fragen</a>.</p></td>
</tr>
<tr class="odd">
<td><p>SMB 3.0 (Server Message Block)</p></td>
<td><p>Das SMB-Protokoll (Server Message Block) ist ein Protokoll für die Netzwerkdateifreigabe, mit dem Anwendungen auf einem Computer auf Dateien und Ressourcen auf einem Remoteserver zugreifen können (SMB setzt auf TCP/IP oder anderen Netzwerkprotokollen auf). Es ermöglicht Anwendungen außerdem die Kommunikation mit einem beliebigen Serverprogramm, das für den Empfang von SMB-Clientanforderungen eingerichtet ist. In Windows Server 2012 wird die neue Version 3.0 des SMB-Protokolls eingeführt, die folgende Funktionen bietet:</p>
<ul>
<li><p>Transparentes Failover mit SMB</p></li>
<li><p>Horizontale Skalierung mit SMB</p></li>
<li><p>SMB Multichannel</p></li>
<li><p>SMB Direct</p></li>
<li><p>SMB-Verschlüsselung</p></li>
<li><p>VSS für SMB-Dateifreigaben</p></li>
<li><p>SMB-Verzeichnisleasing</p></li>
<li><p>SMB-PowerShell</p></li>
</ul></td>
<td><p>Beschränkter Support. Bei dem unterstützten Szenario handelt es sich um eine virtualisierte Bereitstellung, bei der die Datenträger auf VHDs auf einer SMB 3.0-Freigabe gehostet werden. Diese VHDs werden dem Host über einen Hypervisor bereitgestellt. Weitere Informationen finden Sie unter <a href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013-Virtualisierung</a>.</p></td>
<td><p>Beschränkter Support. Bei dem unterstützten Szenario handelt es sich um eine virtualisierte Bereitstellung, bei der die Datenträger auf VHDs auf einer SMB 3.0-Freigabe gehostet werden. Diese VHDs werden dem Host über einen Hypervisor bereitgestellt. Weitere Informationen finden Sie unter <a href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013-Virtualisierung</a>.</p></td>
</tr>
<tr class="even">
<td><p>Speicherplätze</p></td>
<td><p>Speicherplätze ist eine neue Speicherlösung, die Virtualisierungsfunktionen für Windows Server 2012 bereitstellt. Mit Speicherplätze können Sie physische Datenträger in Speicherpools organisieren, die einfach durch das Hinzufügen von Datenträgern problemlos erweitert werden können. Diese Datenträger können über USB, SATA oder SAS verbunden werden. Es werden auch virtuelle Festplatten (Plätze) verwendet, die sich genauso wie physische Festplatten verhalten. Sie weisen leistungsfähige Funktionen auf wie schlanke Speicherzuweisung und Ausfallsicherheit bei Ausfällen der zugrunde liegenden physischen Medien. Weitere Informationen zu Speicherplätzen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/hh831739.aspx">Grundlegendes zu Speicherplätzen</a></p></td>
<td><p>Unterstützt. Es gelten dieselben Einschränkungen, die unter diesem Thema für physische Festplattentypen aufgeführt sind.</p></td>
<td><p>Unterstützt. Es gelten dieselben Einschränkungen, die unter diesem Thema für physische Festplattentypen aufgeführt sind.</p></td>
</tr>
<tr class="odd">
<td><p>Robustes Dateisystem (Resilient File System (ReFS))</p></td>
<td><p>ReFS ist ein neu entwickeltes Dateisystem für Windows Server 2012, das auf NTFS basiert. ReFS weist ein hohes Maß an Kompatibilität mit NTFS auf und bietet gleichzeitig eine verbesserte Datenüberprüfung und Autokorrekturmethoden sowie eine integrierte End-to-End-Ausfallsicherheit bei Ausfällen, insbesondere bei Verwendung in Verbindung mit der Speicherplätze-Funktion. Weitere Informationen zu ReFS finden Sie unter <a href="https://technet.microsoft.com/de-de/library/hh831724.aspx">Grundlegendes zum robusten Dateisystem (ReFS)</a></p></td>
<td><p>Unterstützung für Volumes, die Exchange-Datenbankdateien, Protokolldateien und Inhaltsindizierungsdateien enthalten. Wenn Sie unter Windows Server 2012 bereitstellen, stellen Sie sicher, dass die folgenden Hotfixes für Windows Server 2012 installiert sind:</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717874">Windows 8 und Windows Server 2012-Updaterollup: April 2013</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717877">Dienst für virtuelle Datenträger oder Anwendungen, die den Dienst für virtuelle Datenträger verwenden, stürzen unter Windows Server 2012 ab oder frieren ein</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717879">Computer mit Windows 8 oder Windows Server 2012 frieren beim Ausführen des „dir“-Befehls für ein ReFs-Volume ein</a></p></li>
</ul>
<p>ReFS wird für Betriebssytemvolumes nicht unterstützt.</p>
<p>Bewährte Methode: Für die Exchange-Datenbankdateien (.edb) oder das Volume, auf dem diese Dateien gehostet sind, müssen die Datenintegritätsfunktionen deaktiviert werden.</p></td>
<td><p>Unterstützung für Volumes, die Exchange-Datenbankdateien, Protokolldateien und Inhaltsindizierungsdateien enthalten. Wenn Sie unter Windows Server 2012 bereitstellen, stellen Sie sicher, dass die folgenden Hotfixes für Windows Server 2012 installiert sind:</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717874">Windows 8 und Windows Server 2012-Updaterollup: April 2013</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717877">Dienst für virtuelle Datenträger oder Anwendungen, die den Dienst für virtuelle Datenträger verwenden, stürzen unter Windows Server 2012 ab oder frieren ein</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717879">Computer mit Windows 8 oder Windows Server 2012 frieren beim Ausführen des „dir“-Befehls für ein ReFs-Volume ein</a></p></li>
</ul>
<p>ReFS wird für Betriebssytemvolumes nicht unterstützt.</p>
<p>Bewährte Methode: Für die Exchange-Datenbankdateien (.edb) oder das Volume, auf dem diese Dateien gehostet sind, müssen die Datenintegritätsfunktionen deaktiviert werden.</p></td>
</tr>
<tr class="even">
<td><p>Datendeduplizierung</p></td>
<td><p>Die Datendeduplizierung ist eine neue Technik zur Optimierung der Speicherplatznutzung für Windows Server 2012. Es handelt sich um eine Methode zum Auffinden und Entfernen von Duplizierungen in Daten ohne Beeinträchtigung der Integrität oder Zuverlässigkeit. Ziel ist die Speicherung von mehr Daten in weniger Speicherplatz durch die Segmentierung von Dateien in kleinere Datenblöcke variabler Größe, die Identifizierung doppelt vorhandener Datenblöcke und die Beibehaltung nur einer Kopie eines jeden Datenblocks. Redundante Kopien eines Datenblocks werden durch einen Verweis auf die eine Kopie ersetzt, die Datenblöcke werden in Containerdateien organisiert, und die Container werden für eine weitere Speicherplatzoptimierung komprimiert.</p></td>
<td><p>Keine Unterstützung für Exchange-Datenbankdateien. Hinweis: Kann für Exchange-Datenbankdateien verwendet werden, die vollkommen offline sind (als Sicherungen oder Archive verwendet werden).</p></td>
<td><p>Keine Unterstützung für Exchange-Datenbankdateien. Hinweis: Kann für Exchange-Datenbankdateien verwendet werden, die vollkommen offline sind (als Sicherungen oder Archive verwendet werden).</p></td>
</tr>
</tbody>
</table>


Speicherarchitekturen

