---
title: 'Exchange 2013 – Systemanforderungen: Exchange 2013 Help'
TOCTitle: Exchange 2013 – Systemanforderungen
ms:assetid: 1e80857c-b870-4a6d-a0f4-ff7b3a7be037
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996719(v=EXCHG.150)
ms:contentKeyID: 50475184
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013 – Systemanforderungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Informationen zu Exchange 2013-Anforderungen, die Sie kennen müssen, bevor Sie Exchange 2013 installieren. Sie erhalten z. B. Informationen zu den Hardware-, Netzwerk- und Betriebssystemanforderungen.

Vor der Installation von Microsoft Exchange Server 2013 sollten Sie dieses Thema lesen, damit sichergestellt ist, dass das Netzwerk, die Hardware, die Software, die Clients und sonstige Komponenten die Anforderungen für Exchange 2013 erfüllen. Zudem müssen Sie mit den Koexistenzszenarien vertraut sein, die für Exchange 2013 und frühere Versionen von Exchange unterstützt werden.

## Unterstützte Koexistenzszenarien

In der folgenden Tabelle sind die Szenarien aufgelistet, in denen eine Koexistenz von Exchange 2013 und früheren Exchange-Versionen unterstützt wird.

### Koexistenz von Exchange 2013 und früheren Versionen von Exchange Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange-Version</th>
<th>Koexistenz von Exchange-Organisationen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Server 2003 und frühere Versionen</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2007</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>1Updaterollup 10 für Exchange 2007 Service Pack 3 (SP3) auf allen Exchange 2007-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 Kumulatives Update 2 (CU2) oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange 2010</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>2 Exchange 2010 SP3 auf allen Exchange 2010-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 CU2 oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Organisation mit gemischten Exchange 2010- und Exchange 2007-Umgebungen</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>1Updaterollup 10 für Exchange 2007 SP3 auf allen Exchange 2007-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>2 Exchange 2010 SP3 auf allen Exchange 2010-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 CU2 oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
</tbody>
</table>


1   Wenn Sie ein EdgeSync-Abonnement zwischen einem Exchange 2007 Hub-Transport-Server und einem Exchange 2013 SP1 Edge-Transport-Server erstellen möchten, müssen Sie Exchange 2007 SP3 Updaterollup 13 oder höher auf dem Exchange 2007 Hub-Transport-Server installieren.

2   Wenn Sie ein EdgeSync-Abonnement zwischen einem Exchange 2010 Hub-Transport-Server und einem Exchange 2013 SP1 Edge-Transport-Server erstellen möchten, müssen Sie Exchange 2010 SP3 Updaterollup 5 oder höher auf dem Exchange 2010 Hub-Transport-Server installieren.

## Unterstützte Hybridbereitstellungsszenarien

Exchange 2013 unterstützt Hybridbereitstellungen mit Office 365-Mandanten, die auf die neueste Version von Office 365 aktualisiert wurden. Weitere Informationen zu bestimmten Hybridbereitstellungen finden Sie unter [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/de-de/library/hh534377\(v=exchg.150\)).

## Netzwerk- und Verzeichnisserver

In der folgenden Tabelle werden die Anforderungen für die Netzwerk- und Verzeichnisserver in der Exchange 2013-Organisation aufgeführt.

**Anforderungen für die Netzwerk- und Verzeichnisserver für Exchange 2013**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Schemamaster</p></td>
<td><p>Der Schemamaster wird standardmäßig auf dem ersten in einer Gesamtstruktur installierten Active Directory-Domänencontroller ausgeführt. Auf dem Schemamaster muss eines der folgenden Betriebssysteme ausgeführt werden:</p>
<ul>
<li><p>Windows Server 2012 R2 Standard oder Datacenter1</p></li>
<li><p>Windows Server 2012 Standard oder Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard oder Enterprise</p></li>
<li><p>Windows Server 2008 R2 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2008 Standard oder Enterprise (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2008 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2003 Standard Edition mit Service Pack 2 (SP2) oder höher (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2003 Enterprise Edition mit SP2 oder höher (32-Bit oder 64-Bit)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Globaler Katalogserver</p></td>
<td><p>An jedem Active Directory-Standort, an dem Exchange 2013 installiert werden soll, muss mindestens ein globaler Katalogserver mit einem der folgenden Betriebssysteme vorhanden sein:</p>
<ul>
<li><p>Windows Server 2012 R2 Standard oder Datacenter1</p></li>
<li><p>Windows Server 2012 Standard oder Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard oder Enterprise</p></li>
<li><p>Windows Server 2008 R2 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2008 Standard oder Enterprise (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2008 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2003 Standard Edition mit Service Pack 2 (SP2) oder höher (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2003 Enterprise Edition mit SP2 oder höher (32-Bit oder 64-Bit)</p></li>
</ul>
<p>Weitere Informationen zu globalen Katalogservern finden Sie unter <a href="http://go.microsoft.com/fwlink/p/?linkid=178996">Wozu dient der globale Katalog?</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Domänencontroller</p></td>
<td><p>An jedem Active Directory-Standort, an dem Exchange 2013 installiert werden soll, muss mindestens ein schreibbarer Domänencontroller mit einem der folgenden Betriebssysteme vorhanden sein:</p>
<ul>
<li><p>Windows Server 2012 R2 Standard oder Datacenter1</p></li>
<li><p>Windows Server 2012 Standard oder Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard oder Enterprise SP1 oder höher</p></li>
<li><p>Windows Server 2008 R2 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2008 Standard oder Enterprise SP1 oder höher (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2008 Datacenter, RTM-Version oder höher</p></li>
<li><p>Windows Server 2003 Standard Edition mit Service Pack 2 (SP2) oder höher (32-Bit oder 64-Bit)</p></li>
<li><p>Windows Server 2003 Enterprise Edition mit SP2 oder höher (32-Bit oder 64-Bit)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Active Directory-Gesamtstruktur</p></td>
<td><p>Active Directory muss die Gesamtstrukturfunktionsebene von Windows Server 2003 oder höher2 verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>Unterstützung von DNS-Namespaces</p></td>
<td><p>Exchange 2013 unterstützt die folgenden DNS-Namespaces (Domain Name System):</p>
<ul>
<li><p>Zusammenhängend</p></li>
<li><p>Nicht zusammenhängend</p></li>
<li><p>Einteilige Domänen</p></li>
<li><p>Separat</p></li>
</ul>
<p>Weitere Informationen zu den von Exchange unterstützten DNS-Namespaces finden Sie im Microsoft Knowledge Base-Artikel 2269838 <a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2269838">Microsoft Exchange-Kompatibilität mit Domänen mit einfacher Bezeichnung, separaten Namespaces und unterbrochenen Namespaces</a>.</p></td>
</tr>
<tr class="even">
<td><p>IPv6-Unterstützung</p></td>
<td><p>In Microsoft Exchange 2013 wird IPv6 nur dann unterstützt, wenn auch IPv4 installiert und aktiviert wird. Wenn Exchange 2013 in dieser Konfiguration bereitgestellt ist und das Netzwerk IPv4 und IPv6 unterstützt, können alle Exchange-Server Daten an Geräte, Server und Clients senden bzw. von diesen empfangen, die IPv6-Adressen verwenden. Weitere Informationen finden Sie unter <a href="ipv6-support-in-exchange-2013-exchange-2013-help.md">IPv6-Unterstützung in Exchange 2013</a>.</p></td>
</tr>
</tbody>
</table>


1Windows Server 2012 R2 wird nur mit Exchange 2013 SP1 oder höher unterstützt.

2Windows Server 2012 Die R2-Gesamtstrukturebene wird nur mit Exchange 2013 SP1 oder höher unterstützt.

## Verzeichnisserverarchitektur

Durch die Verwendung von Active Directory-Domänencontrollern mit 64 Bit kann die Leistung des Verzeichnisdiensts für Exchange 2013 gesteigert werden.


> [!NOTE]
> Auf Windows Server 2008-Domänencontrollern in Umgebungen mit mehreren Domänen, auf denen das Active Directory-Gebietsschema auf Japanisch festgelegt ist, übernehmen die Server ggf. einige Attribute nicht, die während der eingehenden Replikation in einem Objekt gespeichert werden. Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 949189, <A href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=949189">Ein Windows Server 2008-Domänencontroller, der mit dem japanischen Gebietsschema konfiguriert, gelten möglicherweise nicht Updates für Attribute für ein Objekt während der eingehenden Replikation</A> (maschinelle Übersetzung).



## Installieren von Exchange 2013 auf Verzeichnisservern

Aus Sicherheits- und Leistungsgründen wird empfohlen, Exchange 2013 nur auf Mitgliedsservern und nicht auf Active Directory-Verzeichnisservern zu installieren. Sie können DCPromo jedoch nicht auf einem Computer ausführen, auf dem Exchange 2013 ausgeführt wird. Nach der Installation von Exchange 2013 wird das Ändern der Rolle von einem Mitgliedsserver in einen Verzeichnisserver (oder umgekehrt) nicht unterstützt.

## Hardware

Die empfohlenen Hardwareanforderungen für Exchange 2013-Server hängen von zahlreichen Faktoren ab, u. a. von den installierten Serverrollen und der erwarteten Serverauslastung.

Ausführliche Informationen zum ordnungsgemäßen Dimensionieren und Konfigurieren Ihrer Bereitstellung finden Sie unter [Empfehlungen für die Dimensionierung und Konfiguration von Exchange 2013](exchange-2013-sizing-and-configuration-recommendations-exchange-2013-help.md).

Informationen zum Bereitstellen von Exchange in einer virtualisierten Umgebung finden Sie unter [Exchange 2013-Virtualisierung](exchange-2013-virtualization-exchange-2013-help.md).

**Hardwareanforderungen für Exchange 2013**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Anforderung</th>
<th>Anmerkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Prozessor</p></td>
<td><ul>
<li><p>Auf der x64-Architektur basierender Computer mit Intel-Prozessor, der die Intel 64-Architektur (früher als Intel EM64T bezeichnet) unterstützt</p></li>
<li><p>AMD-Prozessor, der die AMD64-Plattform unterstützt</p></li>
<li><p>Intel Itanium IA64-Prozessoren werden nicht unterstützt</p></li>
</ul></td>
<td><p>Eine Liste der unterstützten Betriebssysteme finden Sie im Abschnitt &quot;Betriebssystem&quot; weiter unten in diesem Thema.</p></td>
</tr>
<tr class="even">
<td><p>Arbeitsspeicher</p></td>
<td><p>Variiert abhängig von den installierten Exchange-Rollen:</p>
<ul>
<li><p><strong>Postfach</strong>   Mindestens 8 GB</p></li>
<li><p><strong>Clientzugriff</strong>   Mindestens 4 GB</p></li>
<li><p><strong>Kombination von Postfach- und Clientzugriffsserver</strong>   Mindestens 8 GB</p></li>
<li><p><strong>Edge-Transport</strong>   mindestens 4 GB</p></li>
</ul></td>
<td><p>Keine.</p></td>
</tr>
<tr class="odd">
<td><p>Größe der Auslagerungsdatei</p></td>
<td><p>Die minimale und maximale Größe der Auslagerungsdatei muss auf den physischen Arbeitsspeicher (RAM) plus 10 MB und bis auf eine Maximalgröße von 32.778 MB festgelegt werden, wenn Sie mehr als 32 GB RAM nutzen.</p></td>
<td><p>Detaillierte Empfehlungen zur Auslagerungsdatei finden Sie im Abschnitt „Auslagerungsdatei“ unter <a href="exchange-2013-sizing-and-configuration-recommendations-exchange-2013-help.md">Empfehlungen für die Dimensionierung und Konfiguration von Exchange 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Festplattenspeicher</p></td>
<td><ul>
<li><p>Mindestens 30 GB auf dem Laufwerk der Exchange-Installation</p></li>
<li><p>Zusätzlich werden 500 MB verfügbarer Speicherplatz für jedes UM-Sprachpaket (Unified Messaging) benötigt, dessen Installation geplant ist</p></li>
<li><p>200 MB verfügbarer Speicherplatz auf dem Systemlaufwerk</p></li>
<li><p>Ein Festplattenlaufwerk, auf dem die Warteschlangendatenbank gespeichert wird, mit mindestens 500 MB freiem Speicherplatz.</p></li>
</ul></td>
<td><p>Detaillierte Informationen über Speicherempfehlungen finden Sie unter <a href="exchange-2013-storage-configuration-options-exchange-2013-help.md">Exchange 2013-Speicherkonfigurationsoptionen</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Laufwerk</p></td>
<td><p>DVD-ROM-Laufwerk (lokal oder mit Netzwerkzugriff)</p></td>
<td><p>Keine.</p></td>
</tr>
<tr class="even">
<td><p>Bildschirmauflösung</p></td>
<td><p>1024 x 768 Pixel oder höher</p></td>
<td><p>Keine.</p></td>
</tr>
<tr class="odd">
<td><p>Dateiformat</p></td>
<td><p>Als NTFS-Dateisysteme formatierte Festplattenpartitionen. Gilt für die folgenden Partitionen:</p>
<ul>
<li><p>Systempartition</p></li>
<li><p>Partitionen, auf denen Exchange-Binärdateien oder vom Exchange-Diagnoseprotokoll erzeugte Daten gespeichert werden.</p></li>
</ul>
<p>Festplattenpartitionen, die die folgenden Arten von Dateien enthalten, können als ReFS formatiert werden:</p>
<ul>
<li><p>Partitionen, die Transaktionsprotokolldateien enthalten</p></li>
<li><p>Partitionen, die Datenbankdateien enthalten</p></li>
<li><p>Partitionen, die Inhaltsindizierungsdateien enthalten</p></li>
</ul></td>
<td><p>Keine.</p></td>
</tr>
</tbody>
</table>


## Betriebssystem

In der folgenden Tabelle sind die unterstützten Betriebssysteme für Exchange 2013 aufgeführt.


> [!IMPORTANT]
> Die Installation von Exchange 2013 wird auf Computern, die im Windows Server Core-Modus ausgeführt werden, nicht unterstützt. Der Computer muss die vollständige Installation von Windows Server ausführen. Wenn Sie Exchange 2013 auf einem Computer installieren möchten, der im Windows Server Core-Modus ausgeführt wird, müssen Sie den Server über einen der folgenden Schritte in eine vollständige Installation von Windows Server umwandeln: 
> <UL>
> <LI>
> <P><STRONG>Windows Server 2008 R2</STRONG>&nbsp;&nbsp;&nbsp;Installieren Sie Windows Server neu, und wählen Sie die Option <STRONG>Vollständige Installation</STRONG> aus.</P>
> <LI>
> <P><STRONG>Windows Server 2012 R2</STRONG> oder <STRONG>Windows Server 2012</STRONG>&nbsp;&nbsp;&nbsp;Wandeln Sie Ihren im Windows Server Core-Modus ausgeführten Server mithilfe des folgenden Befehls in eine vollständige Installation um.</P><PRE><CODE>Install-WindowsFeature Server-Gui-Mgmt-Infra, Server-Gui-Shell -Restart</CODE></PRE></LI></UL>



**Unterstützte Betriebssysteme für Exchange 2013**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Postfach-, Clientzugriffs- und Edge-Transport-Serverrollen</p></td>
<td><p>Eines der folgenden Betriebssysteme kann verwendet werden:</p>
<ul>
<li><p>Windows Server 2012 R2 Standard oder Datacenter1</p></li>
<li><p>Windows Server 2012 Standard oder Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard mit Service Pack 1 (SP1)</p></li>
<li><p>Windows Server 2008 R2 Enterprise mit Service Pack 1 (SP1)</p></li>
<li><p>Windows Server 2008 R2 Datacenter RTM oder höher</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Verwaltungstools</p></td>
<td><p>Eines der folgenden Betriebssysteme kann verwendet werden:</p>
<ul>
<li><p>Windows Server 2012 R2 Standard oder Datacenter1</p></li>
<li><p>Windows Server 2012 Standard oder Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard mit SP1</p></li>
<li><p>Windows Server 2008 R2 Enterprise mit SP1</p></li>
<li><p>Windows Server 2008 R2 Datacenter RTM oder höher</p></li>
<li><p>64-Bit-Edition von Windows 8.12</p></li>
<li><p>64-Bit-Version von Windows 8</p></li>
<li><p>64-Bit-Version von Windows 7 mit Service Pack 1</p></li>
</ul></td>
</tr>
</tbody>
</table>


1   Windows Server 2012 R2 wird nur von Exchange 2013 SP1 oder höher unterstützt.

2   Windows 8.1 wird nur von Exchange 2013 SP1 oder höher unterstützt.

**Unterstützte Versionen von Windows Management Framework für Exchange 2013**

Exchange 2013 unterstützt nur die Version von Windows Management Framework, die in die Windows-Version, auf der Sie Exchange installieren, integriert ist. Installieren Sie Versionen von Windows Management Framework, die als eigenständige Downloads zur Verfügung gestellt werden, nicht auf Exchange-Servern.

## .NET Framework

Es wird dringend empfohlen, dass Sie die neueste Version von .NET Framework verwenden, die von der Exchange-Version unterstützt wird, die Sie installieren.


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


## Unterstützte Clients

Exchange 2013 unterstützt die folgenden Versionen von Outlook und Entourage für Mac:

  - Outlook 2016

  - Outlook 2013

  - Outlook 2010

  - Outlook 2007

  - Entourage 2008 für Mac, Web Services Edition

  - Outlook für Mac für Office 365

  - Outlook für Mac 2011

Eine Liste der Outlook-Versionen, die von Exchange unterstützt werden, finden Sie unter [Outlook-Updates](https://go.microsoft.com/fwlink/p/?linkid=513459).


> [!IMPORTANT]
> Es wird dringend empfohlen, die aktuellen Service Packs und Updates zu installieren, um eine maximale Benutzerfreundlichkeit beim Herstellen einer Verbindung mit Exchange sicherzustellen.



Outlook-Clients vor Outlook 2007 werden nicht unterstützt. E-Mail-Clients auf Mac-Betriebssystemen, die DAV erfordern (z. B. Entourage 2008 für Mac RTM und Entourage 2004) werden nicht unterstützt.

Outlook Web App unterstützt verschiedene Browser auf diversen Betriebssystemen und Geräten. Ausführliche Informationen finden Sie unter [Neuerungen bei Outlook Web App in Exchange 2013](what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md).

