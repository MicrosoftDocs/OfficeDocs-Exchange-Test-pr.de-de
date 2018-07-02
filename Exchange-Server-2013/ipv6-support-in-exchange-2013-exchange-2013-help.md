---
title: 'IPv6-Unterstützung in Exchange 2013: Exchange 2013 Help'
TOCTitle: IPv6-Unterstützung in Exchange 2013
ms:assetid: 33543023-eb9a-4102-b990-84a818a52814
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg144561(v=EXCHG.150)
ms:contentKeyID: 50475292
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# IPv6-Unterstützung in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Internetprotokoll, Version 6, (IPv6) ist die aktuelle Version des Internetprotokolls (IP). Mit IPv6 sollen zahlreiche der Defizite von IPv4, der vorherigen IP-Version, korrigiert werden.

In Microsoft Exchange Server 2013 wird IPv6 nur dann unterstützt, wenn auch IPv4 installiert und aktiviert wird. Wenn Exchange 2013 in dieser Konfiguration bereitgestellt ist und das Netzwerk IPv4 und IPv6 unterstützt, können alle Exchange-Server Daten an Geräte, Server und Clients senden bzw. von diesen empfangen, die IPv6-Adressen verwenden.

In diesem Thema wird die IPv6-Adressierung in Exchange 2013 behandelt. Weitere Hintergrundinformationen zu IPv6 finden Sie unter [IPv6](https://go.microsoft.com/fwlink/p/?linkid=92582).

**Inhalt**

IPv6-Unterstützung in Exchange 2013-Komponenten

Aktivieren oder Deaktivieren von Protokollen im Betriebssystem

Grundlegende Informationen zu IPv6-Adressen

## IPv6-Unterstützung in Exchange 2013-Komponenten

In der folgenden Tabelle werden die Komponenten in Exchange 2013 beschrieben, die von IPv6 beeinflusst werden.

### Exchange 2013-Funktionen und IPv6

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>IPv6-Unterstützung</th>
<th>Anmerkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IP-Zulassungsliste und IP-Sperrliste im Verbindungsfilter-Agent</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Anbieter für zugelassene IP-Adressen und Anbieter für blockierte IP-Adressen im Verbindungsfilter-Agent.</p></td>
<td><p>Nein</p></td>
<td><p>Aktuell ist kein in ausreichendem Umfang als Branchenstandard akzeptiertes Protokoll für das Nachschlagen von IPv6-Adressen vorhanden. Die meisten IP-Sperrlistenanbieter unterstützen keine IPv6-Adressen. Wenn Sie anonyme Verbindungen von unbekannten IPv6-Adressen auf einem Empfangsconnector zulassen, erhöhen Sie das Risiko, dass Spammer die IP-Sperrlistenanbieter umgehen und Spam erfolgreich an Ihre Organisation zustellen.</p></td>
</tr>
<tr class="odd">
<td><p>Absenderzuverlässigkeit im Protokollanalyse-Agent</p></td>
<td><p>Nein</p></td>
<td><p>Der Protokollanalyse-Agent berechnet nicht den Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) für Nachrichten, die von IPv6-Absendern stammen. Weitere Informationen zur Absenderzuverlässigkeit finden Sie unter <a href="sender-reputation-and-the-protocol-analysis-agent-exchange-2013-help.md">Absenderzuverlässigkeit und der Protokollanalyse-Agent</a>.</p></td>
</tr>
<tr class="even">
<td><p>Sender ID</p></td>
<td><p>Ja</p></td>
<td><p>Weitere Informationen finden Sie unter <a href="sender-id-exchange-2013-help.md">Absender-ID</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Empfangsconnectors</p></td>
<td><p>Ja</p></td>
<td><p>IPv6-Adressen werden für die folgenden Komponenten akzeptiert:</p>
<ul>
<li><p>Lokale IP-Adressbindungen</p></li>
<li><p>Remote-IP-Adressen</p></li>
<li><p>IP-Adressbereiche</p></li>
</ul>
<p>Es wird dringend davon abgeraten, Empfangsconnectors so zu konfigurieren, dass anonyme Verbindungen von unbekannten IPv6-Adressen akzeptiert werden. Wenn Ihre Organisation E-Mail-Nachrichten von Absendern empfangen muss, die IPv6-Adressen verwenden, erstellen Sie einen dedizierten Empfangsconnector, der die Remote-IP-Adressen auf bestimmte IPv6-Adressen beschränkt, die diese Absender verwenden.</p>
<p>Weitere Informationen finden Sie unter <a href="receive-connectors-exchange-2013-help.md">Empfangsconnectors</a>.</p></td>
</tr>
<tr class="even">
<td><p>Sendeconnectors</p></td>
<td><p>Ja</p></td>
<td><p>IPv6-Adressen werden für die folgenden Komponenten akzeptiert:</p>
<ul>
<li><p>Smarthost-IP-Adressen</p></li>
<li><p>Der Parameter <em>SourceIPAddress</em> ist nur für Sendeconnectors gültig, die auf Edge-Transport-Servern konfiguriert sind</p></li>
</ul>

> [!NOTE]
> Wenn Sie eine IPv6-Adresse für den Parameter <EM>SourceIPAddress</EM> angeben möchten, vergewissern Sie sich, ob die entsprechenden DNS-AAAA- und MX-Einträge (Mail-Exchanger) ordnungsgemäß konfiguriert sind. Dies trägt dazu bei, die Nachrichtenzustellung sicherzustellen, wenn ein Remotemessagingserver versucht, einen Reverse-Lookup-Test für die angegebene IPv6-Adresse durchzuführen.


<p>Weitere Informationen finden Sie unter <a href="send-connectors-exchange-2013-help.md">Sendeconnectors</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Grenzwerte für die Nachrichtenrate von eingehenden Nachrichten</p></td>
<td><p>Teilweise</p></td>
<td><p>Die Grenzwerte für die Nachrichtenrate von eingehenden Nachrichten, die Sie für einen Empfangsconnector festlegen können, wie die Parameter <em>MaxInboundConnectionPercentagePerSource</em>, <em>MaxInboundConnectionPerSource</em> und <em>TarpitInterval</em>, gelten nur für eine globale IPv6-Adresse. Verbindungslokale und standortlokale IPv6-Adressen sind von den angegebenen Grenzwerten für die Nachrichtenrate von eingehenden Nachrichten nicht betroffen.</p></td>
</tr>
<tr class="even">
<td><p>Unified Messaging</p></td>
<td><p>Ja</p></td>
<td><p>Weitere Informationen finden Sie unter <a href="ipv6-support-in-unified-messaging-exchange-2013-help.md">IPv6-Unterstützung in Unified Messaging</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Mitglied der Database Availability Group (DAG)</p></td>
<td><p>Ja</p></td>
<td><p>Statische IPv6-Adressen werden von Windows Server und dem Clusterdienst unterstützt. Allerdings entspricht die Verwendung statischer IPv6-Adressen nicht den bewährten Methoden. Exchange 2013 bietet keine Unterstützung für die Konfiguration statischer IPv6-Adressen während des Setups.</p>
<p>Failovercluster unterstützen ISATAP (Intra-Site Automatic Tunnel Addressing Protocol). Es werden nur IPv6-Adressen unterstützt, die eine dynamische Registrierung in DNS ermöglichen. Verbindungslokale Adressen können in einem Cluster nicht verwendet werden.</p>
<p>Weitere Informationen zu DAG-Netzwerkanforderungen finden Sie im Abschnitt &quot;Netzwerkanforderungen&quot; unter <a href="planning-for-high-availability-and-site-resilience-exchange-2013-help.md">Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Aktivieren oder Deaktivieren von Protokollen im Betriebssystem

Exchange 2013-Server bieten vollständige Unterstützung für IPv6-Netzwerke. Selbst wenn Sie IPv6 nicht verwenden, besteht keine Notwendigkeit zur Deaktivierung von IPv6 auf Ihren Exchange-Servern.

Die IPv6-Unterstützung in Exchange 2013 erfordert, dass auf allen Exchange 2013-Servern IPv4 installiert ist. Eine Deinstallation von IPv4 von Ihren Exchange 2013-Servern wird nicht unterstützt.

Weitere Informationen zur IPv6-Unterstützung in Microsoft Windows finden Sie unter [IPv6 für Microsoft Windows: Häufig gestellte Fragen](https://go.microsoft.com/fwlink/p/?linkid=147465).

Zurück zum Seitenanfang

## Grundlegende Informationen zu IPv6-Adressen

Eine IPv6-Adresse ist 128 Bit lang. Die Adresse wird in der Doppelpunkt-Hexadezimaldarstellung notiert. Bei der Doppelpunkt-Hexadezimaldarstellung wird die 128-Bit-Adresse anhand von acht vierstelligen Hexadezimalzahlen mit je 16 Bit dargestellt, die durch einen Doppelpunkt (:) getrennt sind. Ein Beispiel für eine IPv6-Adresse in Doppelpunkt-Hexadezimaldarstellung ist 2001:0DB8:0000:0000:02AA:00FF:C0A8:640A.

Sie können eine IPv6-Adresse mit den folgenden Methoden ausdrücken:

  - **Unterdrückung führender Nullen**   Sie können die führenden Nullen in allen der acht vierstelligen Hexadezimalzahlen in einer IPv6-Adresse auslassen.

  - **Komprimierung durch doppelte Doppelpunkte**   Sie können zwei Doppelpunkte (::) verwenden, um aufeinanderfolgende 16-Bit-Hexadezimalzahlen darzustellen, die nur Nullen enthalten. Diese nur Nullen enthaltenden Zahlen können am Anfang, in der Mitte oder am Ende von IPv6-Adressen auftreten. Die Komprimierung durch doppelte Doppelpunkte darf in einer IPv6-Adresse nur einmal vorkommen.

  - **Abschließende Dezimaldarstellung mit Punkten**   Sie können die letzten 32 Bit am Ende einer IPv6-Adresse mittels Dezimaldarstellung mit Punkten ausdrücken, indem Sie die 8-Bit-Zahlen mit einem Punkt (.) trennen. Die abschließende Dezimaldarstellung mit Punkten wird häufig in Verbindung mit IPv4-kompatiblen Adressen verwendet.

Die folgende Tabelle enthält Beispiele für die Schreibweise von IPv6-Adressen und die entsprechende IPv6-Adresssyntax.

### Schreibweise und Syntax von IPv6-Adressen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Schreibweise von IPv6-Adressen</th>
<th>IPv6-Adresssyntax</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Vollständige IPv6-Adresse</p></td>
<td><p>2001:0DB8:0000:0000:02AA:00FF:C0A8:640A</p></td>
</tr>
<tr class="even">
<td><p>IPv6-Adresse mit unterdrückten führenden Nullen</p></td>
<td><p>2001:DB8:0:0:2AA:FF:C0A8:640A</p></td>
</tr>
<tr class="odd">
<td><p>IPv6-Adresse mit Komprimierung durch doppelte Doppelpunkte</p></td>
<td><p>2001:DB8::2AA:FF:C0A8:640A</p></td>
</tr>
<tr class="even">
<td><p>IPv6-Adresse mit abschließender Dezimaldarstellung mit Punkten</p></td>
<td><p>2001:DB8::2AA:FF:192.168.100.10</p></td>
</tr>
</tbody>
</table>


IPv6-Adressen werden wie folgt kategorisiert:

  - **Unicastadresse**   Ein Paket wird an eine Schnittstelle zugestellt.

  - **Multicastadresse**   Ein Paket wird an mehrere Schnittstellen zugestellt.

  - **Anycastadresse**   Ein Paket wird an die am nächsten liegende von mehreren Schnittstellen zugestellt. Die Entfernung zwischen den Schnittstellen wird durch die Routingkosten definiert.

Bei IPv6-Unicastadressen sind die folgenden Bereiche möglich:

  - **Verbindungslokal**   Der Bereich der IPv6-Adresse ist das lokale Subnetz. Verbindungslokale IPv6-Adressen sind mit den verbindungslokalen IPv4-Adressen vergleichbar, die in APIPA (Automatic Private IP Addressing, Automatische Privat-IP-Adressierung) verwendet werden.

  - **Standortlokal**   Der Bereich der IPv6-Adresse ist die lokale Organisation. Standortlokale Adressen wurden mit RFC 3879 als nicht mehr unterstützt erklärt und durch eindeutige lokale Adressen ersetzt, die in RFC 4193 definiert sind. Standortlokale IPv6-Adressen und eindeutige lokale IPv6-Adressen sind mit privaten IPv4-IP-Adressen vergleichbar.

  - **Global**   Der Bereich dieser IPv6-Adressen ist die gesamte Welt. Globale IPv6-Adressen sind mit öffentlichen IPv4-IP-Adressen vergleichbar.

Die folgende Tabelle enthält einen Vergleich der IPv4- und IPv6-Elemente.

### IPv4-Elemente vs. IPv6-Elemente

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>IPv4</th>
<th>IPv6</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Private IP-Adresse</p></td>
<td><p>10.0.0.0/8</p>
<p>172.16.0.0/12</p>
<p>192.168.0.0/16</p></td>
<td><p>FD00::/8</p></td>
</tr>
<tr class="even">
<td><p>Verbindungslokale Adresse</p></td>
<td><p>169.254.0.0/16</p></td>
<td><p>FE80::/64</p></td>
</tr>
<tr class="odd">
<td><p>Loopbackadresse</p></td>
<td><p>127.0.0.1</p></td>
<td><p>::1</p></td>
</tr>
<tr class="even">
<td><p>Nicht spezifizierte Adresse</p></td>
<td><p>0.0.0.0</p></td>
<td><p>::</p></td>
</tr>
<tr class="odd">
<td><p>Adressauflösung</p></td>
<td><p>ARP (Address Resolution-Protokoll)</p></td>
<td><p>ND (Neighbor Discovery, Nachbarsuche)</p></td>
</tr>
<tr class="even">
<td><p>DNS-Hostnamensauflösung (Domain Name System)</p></td>
<td><p>Adress-Eintrag (A-Eintrag)</p></td>
<td><p>AAAA-Eintrag oder A6-Eintrag</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zur IPv6-Adressierung finden Sie unter [IPv6-Adresstypen](https://go.microsoft.com/fwlink/p/?linkid=98357).

## Unterstützte IPv6-Adresseingabeformate

Die folgenden IPv6-Adresseingabeformate werden in Exchange 2013 unterstützt:

  - Eine einzelne IPv6-Adresse

  - Ein IPv6-Adressbereich

  - Eine IPv6-Adresse zusammen mit einer Subnetzmaske

  - Eine IPv6-Adresse zusammen mit einer Subnetzmaske, bei der die CIDR-Darstellung (Classless Inter-Domain Routing, klassenloses domänenübergreifendes Routing) verwendet wird

Die folgende Tabelle enthält Beispiele für die akzeptierten IPv6-Adresseingabeformate in Exchange 2013.

### Beispiele für IPv6-Adressen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Typ</th>
<th>Beispiel für eine IPv6-Adresse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einzelne Adresse</p></td>
<td><p>2001:DB8::2AA:FF:C0A8:640A</p></td>
</tr>
<tr class="even">
<td><p>Adressbereich</p></td>
<td><p>2001:DB8::2AA:FF:C0A8:640A-2001:DB8::2AA:FF:C0A8:6414</p></td>
</tr>
<tr class="odd">
<td><p>Adresse zusammen mit Subnetzmaske</p></td>
<td><p>2001:DB8::2AA:FF:C0A8:640A(FFFF:FFFF:FFFF:FFFF::)</p></td>
</tr>
<tr class="even">
<td><p>Adresse zusammen mit einer Subnetzmaske in CIDR-Schreibweise</p></td>
<td><p>2001:DB8::2AA:FF:C0A8:640A/64</p></td>
</tr>
</tbody>
</table>


In Exchange 2013 werden die folgenden Eingabeformate unterstützt:

  - Unterdrückung führender Nullen

  - Komprimierung durch doppelte Doppelpunkte

  - Abschließende Dezimaldarstellung mit Punkten

Zurück zum Seitenanfang

