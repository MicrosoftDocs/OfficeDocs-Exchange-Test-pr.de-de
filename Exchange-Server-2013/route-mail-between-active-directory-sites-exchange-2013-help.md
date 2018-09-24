---
title: 'Weiterleiten v. E-Mails zw. Active Directory-Standorten: Exchange 2013-Hilfe'
TOCTitle: Weiterleiten von E-Mails zwischen Active Directory-Standorten
ms:assetid: 86b423e3-7bec-4430-9a5a-4f84ce9d82ea
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ916681(v=EXCHG.150)
ms:contentKeyID: 52062889
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Weiterleiten von E-Mails zwischen Active Directory-Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Ein Active Directory-Standort ist eine logische Konfigurationskomponente, die auf den physischen Aspekten des Netzwerks basiert. Der Hauptzweck, dem die Erstellung eines Active Directory-Standorts dient, ist die Definition, welche Subnetze im Netzwerk so verbunden sind, dass die Steuerung des Active Directory-Replikationsdatenverkehrs optimiert wird. Microsoft Exchange Server 2013 erkennt sowohl Database Availability Groups (DAGs) und Active Directory-Standorte als Routinggrenzen, und Exchange 2013-Server treffen Routingentscheidungen basierend auf der Active Directory-Standorttopologie.

Eine Active Directory-Gesamtstruktur enthält standardmäßig nur einen Active Directory-Standort. Der Standardname dieses Active Directory-Standorts ist `Default-First-Site-Name`. Wenn keine anderen Active Directory-Standorte erstellt werden, gehören alle Computer von Domänenmitgliedern in der Gesamtstruktur `Default-First-Site-Name` an. Sie müssen keine Zuordnung zwischen Subnetz und Standort konfigurieren. Wenn zusätzliche Active Directory-Standorte erstellt werden, müssen Sie die Subnetze angeben, die dem betreffenden Active Directory-Standort zugeordnet sind.

**Inhalt**

Bestimmen der Standortmitgliedschaft

IP-Standortverknüpfungen

Steuern der IP-Standortverknüpfungskosten

Implementieren von Hubstandorten

Topologieerkennung

## Bestimmen der Standortmitgliedschaft

Jeder Active Directory-Standort ist mindestens einem IP-Subnetz zugeordnet. Ein Administrator weist die Active Directory-Standortmitgliedschaft Computern zu, die als Domänencontroller und globale Katalogserver konfiguriert sind. Anderen Domänenmitgliedscomputern, z. B. Servercomputern mit Exchange, wird die Active Directory-Standortmitgliedschaft automatisch zugewiesen, wenn sie für die Verwendung einer IP-Adresse konfiguriert werden, die sich in einem IP-Subnetz befindet, das einem Active Directory-Standort zugeordnet ist. Bei Computern, die zum selben Active Directory-Standort gehören, wird davon ausgegangen, dass sie über eine gute Netzwerkverbindung verfügen. Ein Server ist immer Mitglied eines einzelnen Active Directory-Standorts.

Wenn eine Anwendung die Active Directory-Standortmitgliedschaft des Computers, auf dem sie installiert ist, sowie anderer Computer in der Gesamtstruktur bestimmen und diese Informationen zum Steuern des Kommunikationsflusses verwenden kann, handelt es sich um eine standortaktivierte Anwendung. Wenn standortaktivierte Anwendungen die Dienste eines anderen Servers verwenden müssen, z. B. eines Domänencontrollers oder eines globalen Katalogservers, erhalten die Server mit der gleichen Active Directory-Standortmitgliedschaft wie der Computer, der diese Dienste anfordert, Priorität.

Exchange 2013 ist eine standortabhängige Anwendung und verwendet die Active Directory-Topologie für das Nachrichtenrouting und die Kommunikation mit den Diensten, die auf Computern ausgeführt werden, auf denen andere Exchange 2013-Serverrollen installiert sind. Der Active Directory-Standort stellt nicht nur die Routinggrenze, sondern auch die Diensterkennungsgrenze dar.

Die Bestimmung der Standortmitgliedschaft für einen Domänenmitgliedscomputer hängt von einer Reihe von DNS-Abfragen ab, um die lokale IP-Adresse mit definierten Untermengen zu vergleichen und dann die entsprechende Standortmitgliedschaftszuordnung zu ermitteln. Um den Mehraufwand zu verringern, der mit DNS-Abfragen verbunden ist, enthalten die Active Directory-Schemaerweiterungen für Exchange 2013 das Attribut **msExchServerSite** für das Exchange-Serverobjekt. Der Wert dieses Attributs ist der Distinguished Name des Active Directory-Standorts eines Exchange-Servers. Dieses Attribut ist eine Eigenschaft jedes Exchange-Serverobjekts. Wenn die Standortmitgliedschaftsaffinität als ein Attribut des Serverobjekts gespeichert wird, kann die aktuelle Topologie direkt aus Active Directory gelesen werden, anstatt DNS-Abfragen verwenden zu müssen, und eine Standortmitgliedschaftszuordnung wird für einen Nicht-Domänencomputer aktiviert, z. B. für einen abonnierten Edge-Transport-Server.

Der Wert für das Attribut **msExchServerSite** wird vom Microsoft Exchange Active Directory-Topologiedienst mit Daten aufgefüllt und aktuell gehalten. Wenn ein Windows-basierter Computer gestartet wird, bestimmt der Netzwerkanmeldungsdienst die Standortmitgliedschaft für den Computer. Der Netzwerkanmeldungsdienst verwendet diese Informationen, um Domänencontroller zu ermitteln, die sich am gleichen Active Directory-Standort wie der lokale Computer befinden, und leitet dann Autorisierungs- und Authentifizierungsanforderungen an diese Server um. Der Microsoft Exchange Active Directory-Topologiedienst verwendet den API-Aufruf **DsGetSiteName** zum Abrufen des Werts der Standortmitgliedschaft aus dem Netzwerkanmeldungsdienst und schreibt den Distinguished Name des Active Directory-Standorts in das Attribut **msExchServerSite** für das Exchange-Serverobjekt in Active Directory.

Die folgende Tabelle zeigt, wie eine Organisation Active Directory-Standorte definieren kann. In diesem Beispiel werden drei Active Directory-Standorte definiert, und jedem Active Directory-Standort sind mehrere IP-Subnetze zugeordnet.

**Beispiel für die Zuordnung eines Active Directory-Standorts zu Subnetzen**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Active Directory-Standorts</th>
<th>Zugeordnete IP-Subnetze</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standort A</p></td>
<td><p>192.168.1.0/24</p>
<p>192.168.2.0/24</p></td>
</tr>
<tr class="even">
<td><p>Standort B</p></td>
<td><p>192.168.3.0/24</p>
<p>192.168.4.0/24</p></td>
</tr>
<tr class="odd">
<td><p>Standort C</p></td>
<td><p>192.168.5.0/24</p>
<p>192.168.6.0/24</p></td>
</tr>
</tbody>
</table>


Wenn der Server "Mailbox01" die IP-Adresse 192.168.1.1 hat, ist er Mitglied von Standort A. Durch Ändern der IP-Adresse eines Servers wird ggf. auch seine Standortmitgliedschaft geändert. Wenn Sie die IP-Adresse von "Mailbox01" in 192.168.2.1 ändern, ändert dies die Active Directory-Standortmitgliedschaft des Servers nicht, weil dieses Subnetz ebenfalls Standort A zugeordnet ist. Wenn Sie den Server jedoch verschieben, und die IP-Adresse ändert sich in 192.168.3.1, wird der Server als Mitglied von Standort B betrachtet.

Eine Änderung der Standortmitgliedschaft kann auch auftreten, wenn Sie die Zuordnung der Subnetze zu Active Directory-Standorten ändern. Wenn Sie z. B. das Subnetz 192.168.3.0 aus der Zuordnung zu Standort B entfernen und dann Standort A zuordnen, ändert sich auch die Standortmitgliedschaft eines Servers mit der IP-Adresse 192.168.3.1 in Standort A. Bei jeder Änderung einer Standortmitgliedschaft muss Exchange die Konfigurationsdaten aktualisieren, damit die Änderung berücksichtigt wird, wenn Exchange Routingentscheidungen trifft. Es entsteht eine Wartezeit zwischen dem Zeitpunkt, zu dem eine Änderung in einer Active Directory-Standortmitgliedschaft stattfindet, und dem Zeitpunkt, zu dem die Topologieänderung vollständig übermittelt ist.

Zurück zum Seitenanfang

## IP-Standortverknüpfungen

Standortverknüpfungen sind logische Pfade zwischen Active Directory-Standorten. Ein Standortverknüpfungsobjekt stellt eine Gruppe von Standorten dar, die zu einheitlichen Kosten zwischen Standorten kommunizieren können. Standortverknüpfungen entsprechen nicht dem tatsächlichen Pfad, den Netzwerkpakete im physischen Netzwerk durchlaufen. Die der Standortverknüpfung durch den Administrator zugewiesenen Kosten stehen jedoch normalerweise mit der zugrunde liegenden Netzwerkzuverlässigkeit, der Geschwindigkeit und der verfügbaren Bandbreite in Zusammenhang. Der Active Directory-Administrator würde z. B. einer Netzwerkverbindung mit einer Geschwindigkeit von 100 Megabit pro Sekunde (MBit/s) niedrigere Kosten zuweisen als einer Netzwerkverbindung mit 10 MBit/s.

Standardmäßig sind alle Standortverknüpfungen transitiv. Dies bedeutet, dass Standort A transitiv mit Standort C verknüpft ist, wenn Standort A eine Verknüpfung mit Standort B und Standort B eine Verknüpfung mit Standort C besitzt. Die transitive Verknüpfung zwischen Standort A und Standort C wird auch als *Standortverknüpfungsbrücke* bezeichnet.

Exchange verwendet nur IP-Standortverknüpfungen, um seine Routingtopologie für Active Directory-Standorte zu bestimmen. Die Kosten, die der IP-Standortverknüpfung zugewiesen werden, werden von der Routingkomponente von Exchange beim Berechnen einer Routingtabelle berücksichtigt. Diese Kosten werden zum Berechnen des kostengünstigsten Routingpfads zum Endziel einer Nachricht verwendet.

Jeder Active Directory-Standort muss mindestens einer IP-Standortverknüpfung zugeordnet sein. Es gibt eine einzelne standardmäßige IP-Standortverknüpfung namens `DEFAULTIPSITELINK`. Wenn Sie einen Active Directory-Standort erstellen, müssen Sie diesen Standort einer IP-Standortverknüpfung zuordnen. Sie können zusätzliche IP-Standortverknüpfungen erstellen, um die gewünschte Topologie zu implementieren, oder Sie können jeden Active Directory-Standort der Standardverknüpfung `DEFAULTIPSITELINK` zuordnen. Jeder Active Directory-Standort, der Teil einer IP-Standortverknüpfung ist, kann direkt mit jedem anderen Standort in dieser Verknüpfung zu einheitlichen Kosten kommunizieren.

In der folgenden Abbildung sind vier Active Directory-Standorte in der Gesamtstruktur konfiguriert. Jeder Standort wurde der Standortverknüpfung `DEFAULTIPSITELINK` zugeordnet. Daher kommuniziert jeder Active Directory-Standort direkt mithilfe der gleichen Kostenstruktur mit jedem anderen Standort. Es sind mehrere Kommunikationspfade angegeben, es ist jedoch nur eine IP-Standortverknüpfung definiert.

**Vollständig vernetzte Topologie mit einzelner IP-Standortverknüpfung**

![Vollständig vernetzte Topologie mit einzelner IP-Standortverknüpfung](images/JJ916681.af38d41d-e768-4221-ab4b-b782aa388b73(EXCHG.150).gif "Vollständig vernetzte Topologie mit einzelner IP-Standortverknüpfung")

In der folgenden Abbildung sind vier Active Directory-Standorte in der Gesamtstruktur konfiguriert. In dieser Topologie hat der Administrator IP-Standortverknüpfungen konfiguriert, um eine *Hub-and-Spoke-Topologie* der Active Directory-Standorte zu erstellen. Jeder Spokestandort kann direkt mit dem zentralen Standort kommunizieren, und die Spokestandorte können miteinander über transitive IP-Standortverknüpfungen kommunizieren.

**Hub-and-Spoke-Topologie der Active Directory-IP-Standortverknüpfungen**

![Hub-and-Spoke-Topologie von IP-Standortverknüpfungen](images/JJ916681.eca6cd51-8c2e-4996-81ea-070cd9766ef8(EXCHG.150).gif "Hub-and-Spoke-Topologie von IP-Standortverknüpfungen")

Es muss beachtet werden, dass Exchange Standortverknüpfungen nur für die Bestimmung des kostengünstigsten Pfads verwendet, aber immer eine Zustellung von Nachrichten direkt an den Exchange-Zielserver versucht. Wenn beispielsweise ein Benutzer an Standort B in der obigen Abbildung eine Nachricht an einen anderen Benutzer an Standort C sendet, stellt der Postfachserver an Standort B eine direkte Verbindung zum Postfachserver an Standort C her. Wenn erzwungen werden soll, dass Nachrichten über Standort A geleitet werden, müssen Sie diesen Standort als Hub-Standort aktivieren. Weitere Informationen zu Hub-Standorten finden Sie weiter unten unter "Implementieren von Hubstandorten".

Ein Active Directory-Administrator implementiert die Topologie, die am besten für die Verbindungs- und Kommunikationsanforderungen der Gesamtstruktur geeignet ist. Da die gleiche Topologie von Exchange verwendet wird, müssen Sie sicherstellen, dass die aktuelle Topologie effiziente Messagingkommunikation unterstützt.

Die Standardkosten für eine Standortverknüpfung haben den Wert 100. Gültige Standortverknüpfungskosten werden durch einen beliebigen Wert zwischen 1 und 99.999 angegeben. Wenn Sie redundante Verknüpfungen angeben, wird die Verknüpfung mit den niedrigsten zugewiesenen Kosten stets bevorzugt. Ein Exchange-Organisationsadministrator kann einer IP-Standortverknüpfung Exchange-spezifische Kosten zuweisen. Wenn Exchange-Kosten einer IP-Standortverknüpfung zugewiesen sind, werden sie von Exchange verwendet. Andernfalls werden die Active Directory-Kosten verwendet. Weitere Informationen zum Festlegen von Exchange-Kosten für eine IP-Standortverknüpfung finden Sie weiter unten in diesem Thema unter "Steuern der IP-Standortverknüpfungskosten". Ein Administrator, der Mitglied der Gruppe von Organisationsadministratoren ist, kann zusätzliche IP-Standortverknüpfungen erstellen.

Weitere Informationen zur Active Directory-Standortkonfiguration finden Sie unter [Entwerfen der Standorttopologie](https://go.microsoft.com/fwlink/p/?linkid=33551).

Zurück zum Seitenanfang

## Steuern der IP-Standortverknüpfungskosten

Active Directory-IP-Standortverknüpfungskosten beruhen auf der relativen Netzwerkgeschwindigkeit im Vergleich zu allen Netzwerkverbindungen im WAN und sollen für eine zuverlässige und effiziente Replikationstopologie sorgen. Daher sollten in den meisten Fällen die vorhandenen IP-Standortverknüpfungskosten für Exchange-Nachrichtenrouting gut funktionieren. Wenn Sie nach Abschluss der Dokumentation des vorhandenen Active Directory-Standorts und der IP-Standortverknüpfungstopologie feststellen, dass die Active Directory-IP-Standortverknüpfungskosten und die Datenverkehrsmuster für Exchange nicht optimal sind, können Sie die von Exchange ermittelten Kosten anpassen. Eine Änderung der einer IP-Standortverknüpfung zugewiesenen Kosten mithilfe von Active Directory-Tools wirkt sich auf die gesamte Umgebung aus. Verwenden Sie stattdessen das Cmdlet **Set-AdSiteLink** in der Exchange-Verwaltungsshell, um der IP-Standortverknüpfung Exchange-spezifische Kosten zuzuweisen. Führen Sie in der Shell den folgenden Befehl aus, um beispielsweise den Exchange-spezifischen Kostenwert 25 für die IP-Standortverknüpfung SITELINKAB zu konfigurieren: `Set-AdSiteLink SITELINKAB -ExchangeCost 25`.

Wenn einer IP-Standortverknüpfung Exchange-spezifische Kosten zugewiesen werden, überschreiben die Exchange-Kosten die Active Directory-Kosten für Nachrichtenroutingzwecke, und das Routing berücksichtigt nur die Exchange-Kosten, wenn der kostengünstigste Routingpfad ermittelt wird.

Das Anpassen der Kosten von IP-Standortverknüpfungen kann nützlich sein, wenn die Nachrichtenroutingtopologie von der Active Directory-Replikationstopologie abweichen muss. Exchange-Kosten können dazu dienen, alle Nachrichtenrouten zum Verwenden eines Hubstandorts zu zwingen. Exchange-Kosten können auch zum Steuern dienen, in welche Warteschlangen Nachrichten geleitet werden, wenn die Kommunikation mit einem Active Directory-Standort nicht erfolgreich ist. Die folgende Abbildung zeigt eine Active Directory-Topologie mit vier Standorten:

**Topologie mit für IP-Standortverknüpfungen konfigurierten Exchange-Kosten**

![Topologie mit Exchange-Kosten zu IP-Standortverknüpfungen](images/JJ916681.56ac2bab-99de-4ddf-b968-80cd34ab8c21(EXCHG.150).gif "Topologie mit Exchange-Kosten zu IP-Standortverknüpfungen")

In der Abbildung oben hat die Netzwerkverbindung zwischen Standort C und Standort D eine geringe Bandbreite und wird nur für die Active Directory-Replikation verwendet. Sie sollte nicht für das Nachrichtenrouting eingesetzt werden. Aufgrund der Active Directory-IP-Standortverknüpfungskosten wird diese Verknüpfung jedoch in den kostengünstigsten Routingpfad von allen anderen Active Directory-Standorten zu Standort D einbezogen. Aus diesem Grund werden die Nachrichten an Standort C in die Warteschlange für den Standort D eingereiht. Der Exchange-Administrator zieht es vor, für den kostengünstigsten Routingpfad stattdessen Standort B zu berücksichtigen, damit die Nachrichten an Standort B in Warteschlangen gespeichert werden, wenn Standort D nicht verfügbar ist. Durch das Konfigurieren hoher Exchange-Kosten für die IP-Standortverknüpfung zwischen Standort C und Standort D wird verhindert, dass die IP-Standortverknüpfung in den kostengünstigsten Routingpfad zu Standort D einbezogen wird.

Exchange bietet Unterstützung für die Konfiguration einer maximalen Nachrichtengröße für eine Active Directory-IP-Standortverknüpfung. Standardmäßig wendet Exchange keine maximale Nachrichtengröße auf Nachrichten an, die mittels Relay zwischen Exchange-Servern an verschiedenen Active Directory-Standorten weitergeleitet werden. Wenn Sie mit dem Cmdlet **Set-AdSiteLink** eine maximale Nachrichtengröße für eine Active Directory-IP-Standortverknüpfung konfigurieren, wird beim Routing ein Unzustellbarkeitsbericht für alle Nachrichten generiert, deren Größe die für die Active Directory-Standortverknüpfung auf dem kostengünstigsten Routingpfad konfigurierte, maximal zulässige Nachrichtengröße überschreitet. Diese Konfiguration ist nützlich, um die Größe von Nachrichten zu beschränken, die über Verbindungen mit niedriger Bandbreite an Active Directory-Remotestandorte gesendet werden. Weitere Informationen finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

Zurück zum Seitenanfang

## Implementieren von Hubstandorten

In Ihrer Exchange-Organisation können Sie erzwingen, dass die gesamte Nachrichtenübermittlung über einen bestimmten Active Directory-Standort erfolgt. Über die Shell können Sie einen Active Directory-Standort als Hubstandort definieren. Dadurch sorgen Sie allerdings für mehr Verarbeitungsaufwand, da an der Nachrichtenübermittlung mehr Server beteiligt sind. Angenommen, eine Nachricht wird von Standort A an Standort E gesendet. Wenn der kostengünstigste Routingpfad "Standort A - Standort B - Standort C - Standort D - Standort E" lautet und Sie Standort C als Hub-Standort festlegen, wird die Nachricht mittels Relay von Standort A an Standort C geleitet und dann von Standort C an Standort E.

Mit dem Cmdlet **Set-AdSite** wird ein Active Directory-Standort als Hubstandort definiert. Wenn entlang des kostengünstigsten Routingpfads für die Nachrichtenzustellung ein Hub-Standort vorhanden ist, werden die Nachrichten in einer Warteschlange gespeichert und dann vom Transportdienst auf Postfachservern am Hub-Standort verarbeitet, bevor sie mittels Relay an ihr Endziel weitergeleitet werden.

Nachdem der kostengünstigste Routingpfad ausgewählt wurde, bestimmt das Routing, ob in diesem Routingpfad ein Hub-Standort vorhanden ist. Wenn ein Hubstandort konfiguriert ist, werden die Nachrichten auf einem Postfachserver am Hubstandort angehalten, bevor sie mittels Relay an das Ziel weitergeleitet werden. Wenn im kostengünstigsten Routingpfad mehrere Hub-Standorte vorhanden sind, werden die Nachrichten an jedem Hub-Standort im Routingpfad angehalten.

Diese Variante des direkten Relayroutings tritt nur in Kraft, wenn sich der Hub-Standort im kostengünstigsten Routingpfad befindet. Die folgende Abbildung zeigt die richtige Verwendung eines Hub-Standorts. In dieser Abbildung ist Standort B als Hub-Standort konfiguriert. Nachrichten, die von Standort A an Standort D weitergeleitet werden, werden mittels Relay an Standort B geleitet, bevor sie an Standort D zugestellt werden.

**Nachrichtenübermittlung mit Hub-Standort**

![Nachrichtenübermittlung mit Hub-Standort](images/JJ916681.93238bcb-6bbc-4a48-aeb0-09342a421b5b(EXCHG.150).gif "Nachrichtenübermittlung mit Hub-Standort")

Die folgende Abbildung zeigt, wie sich die Kosten für die IP-Standortverknüpfung auf das Routing an einen Hub-Standort auswirken. In diesem Szenario wurde Standort B als Hub-Standort festgelegt. Standort B ist allerdings nicht im kostengünstigsten Routingpfad zwischen anderen Standorten enthalten. Nachrichten, die von Standort A an Standort D weitergeleitet werden, werden allerdings nicht mittels Relay an Standort B geleitet. Ein Active Directory-Standort wird nie als Hubstandort genutzt, wenn sich dieser nicht im kostengünstigsten Routingpfad zwischen anderen Standorten befindet.

**Falsch konfigurierter Hub-Standort**

![Falsch konfigurierter Hub-Standort](images/JJ916681.c010d4d8-5cd3-4b79-b7db-0367ba3cc287(EXCHG.150).gif "Falsch konfigurierter Hub-Standort")

Sie können jeden beliebigen Active Directory-Standort als Hubstandort konfigurieren. Damit diese Konfiguration ordnungsgemäß funktioniert, muss jedoch bereits mindestens ein Postfachserver am Hubstandort bereitgestellt sein.

Zurück zum Seitenanfang

## Topologieerkennung

Die Active Directory-Topologie wird für Exchange durch die folgenden erforderlichen Elemente bereitgestellt:

  - Microsoft Exchange Active Directory-Topologiedienst.

  - Das Topologieerkennungsmodul im Microsoft Exchange-Transportdienst.

Der Microsoft Exchange Active Directory-Topologiedienst wird auf allen Exchange 2013-Clientzugriffs- und Postfachservern ausgeführt. Diese Server verwenden den Microsoft Exchange Active Directory-Topologiedienst zum Ermitteln der Domänencontroller und globalen Katalogserver, die von den Exchange-Servern zum Lesen und Schreiben von Active Directory-Daten verwendet werden können. Exchange 2013 stellt eine Bindung mit den erkannten Verzeichnisservern her, wenn Exchange Daten aus Active Directory lesen oder in Active Directory schreiben muss.

Das Topologieerkennungsmodul ist Teil des Microsoft Exchange-Transportdiensts und stellt Informationen zur Active Directory-Topologie für Servercomputer mit Exchange bereit. Diese API erkennt die Servercomputer mit Exchange sowie die Serverrollen in der Organisation und ermittelt ihre Beziehung zu den Active Directory-Konfigurationsobjekten. Die Konfigurationsdaten werden aus Active Directory abgerufen und dann zwischengespeichert, damit die auf dem Computer ausgeführten Exchange-Dienste darauf zugreifen können.

Das Topologieerkennungsmodul führt die folgenden Schritte aus, um eine Exchange-Routingtopologie zu generieren:

1.  Daten werden aus Active Directory gelesen. Die folgenden Objekte werden abgerufen:
    
      - Active Directory-Standorte.
    
      - IP-Standortverknüpfungen.
    
      - Alle Exchange-Server.

2.  Die in Schritt 1 abgerufenen Daten werden zum Erstellen der anfänglichen Topologie und zum Verknüpfen und Zuordnen der zugehörigen Konfigurationsobjekte verwendet.

3.  Exchange-Server werden Active Directory-Standorten durch Abrufen des Werts des Standortattributs aus dem Exchange-Serverobjekt zugeordnet, das in Active Directory gespeichert ist.

4.  Routingtabellen werden mit der abgerufenen Informationssammlung aktualisiert.

Durch diesen Vorgang wird jeder Exchange 2013-Server für die anderen Exchange-Server in der Organisation aktiviert und über die Entfernung der Exchange-Server voneinander informiert.

Zurück zum Seitenanfang

