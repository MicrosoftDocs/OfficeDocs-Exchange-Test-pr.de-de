---
title: 'E-Mail-Routing: Exchange 2013 Help'
TOCTitle: E-Mail-Routing
ms:assetid: 6fd39079-9655-4fd9-9269-c7462c76e0a7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998825(v=EXCHG.150)
ms:contentKeyID: 50475921
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# E-Mail-Routing

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die Hauptaufgabe des Transportdiensts, der auf allen Postfachservern in Ihrer Microsoft Exchange Server 2013-Organisation vorhanden ist, besteht im Routing (d. h. im Weiterleiten) von Nachrichten, die von Benutzern und externen Quellen empfangen werden, an ihre endgültigen Bestimmungsorte. Routingentscheidungen werden während der Nachrichtenkategorisierung getroffen. Das Kategorisierungsmodul ist eine Komponente des Transportdiensts auf einem Postfachserver, die alle eingehenden Nachrichten verarbeitet und basierend auf Informationen zu ihren Zielen bestimmt, was mit den Nachrichten geschehen soll.

Das Routing in Exchange 2013 bietet ab sofort vollständige Unterstützung für Database Availability Groups (DAGs), und die DAG-Mitgliedschaft wird als Routinggrenze verwendet. Der Grund: In Exchange 2013 hosten alle Postfachserver den Transportdienst. Wenn also ein Postfachserver zu einer DAG gehört, ist der primäre Routingmechanismus für Nachrichten eng mit der DAG verbunden. Wenn eine DAG sich über mehrere Active Directory-Standorte erstreckt, ist es nicht effizient, den Active Directory-Standort als primäre Routinggrenze zu verwenden. Exchange 2013 nutzt die Mitgliedschaft in einem Active Directory-Standort auch als Routinggrenze für Postfachserver, die keiner DAG angehören, und zur Routinginteroperabilität mit früheren Exchange-Versionen. Zu den weiteren wichtigen Änderungen am Routing in Exchange 2013 gehören folgende:

  - Der Transportdienst auf einem Postfachserver kommuniziert niemals direkt mit einer Postfachdatenbank. Stattdessen kommuniziert der Transportdienst mit dem Postfachtransportdienst auf dem Postfachserver. Nur der Postfachtransportdienst kommuniziert mit der Postfachdatenbank auf dem lokalen Postfachserver. Wenn der Postfachserver Mitglied einer DAG ist, akzeptiert nur der Postfachtransportdienst auf dem Postfachserver, auf dem die aktive Kopie der Postfachdatenbank gespeichert ist, eine Nachricht für den Zielempfänger.

  - Remoteprozeduraufrufe (Remote Procedure Calls, RPCs) werden vom Postfachtransportdienst nur verwendet, um Nachrichten an die lokale Postfachdatenbank zu senden oder von dieser zu empfangen. Wenn der Postfachserver Mitglied einer DAG ist, verwendet der Postfachtransportdienst RPCs nur zur lokalen Kommunikation mit den aktiven Kopien der Postfachdatenbanken. Anders gesagt: RPCs werden nie für die serverübergreifende Kommunikation verwendet. Stattdessen kommunizieren der Postfachtransportdienst und die Transportdienste auf anderen Postfachservern immer über SMTP.

  - Exchange 2013 verwendet eine präzisere Warteschlangenverwaltung für Remoteziele. Anstatt eine Warteschlange für alle Ziele an einem Active Directory-Remotestandort zu verwenden, reiht Exchange 2013 Nachrichten für bestimmte Ziele innerhalb des Active Directory-Standorts, wie z. B. für einzelne Sendeconnectors, in die Warteschlange ein.

  - Verknüpfte Connectors werden nicht mehr verwendet. Bei einem verknüpften Connector handelte es sich um einen Empfangsconnector, der mit einem Sendeconnector verknüpft war. Alle vom Empfangsconnector empfangenen Nachrichten wurden automatisch zum Sendeconnector weitergeleitet.

**Inhalt**

Routingkomponenten

  - Routingziele

  - Zustellungsgruppen

  - Warteschlangen

Weiterleiten von Nachrichten

  - Routing von Nachrichten zwischen Active Directory-Standorten

  - Weiterleitung im Front-End-Transport-Dienst auf Clientzugriffsservern

  - Weiterleitung im Postfachtransportdienst auf Postfachservern

  - Weiterleitung im Transportdienst auf Edge-Transport-Servern

## Routingkomponenten

Wenn eine Nachricht vom Transportdienst auf einem Exchange 2013-Postfachserver empfangen wird, muss sie kategorisiert werden. Die erste Phase der Nachrichtenkategorisierung ist die Empfängerauflösung. Nachdem der Empfänger aufgelöst wurde, kann das Endziel bestimmt werden. In der nächsten Phase – dem Routing – wird bestimmt, wie dieses Ziel am besten erreicht werden kann. Für das Routing in Exchange 2013 wurden zwei Konzepte eingeführt, um das Verfahren flexibler und weniger komplex zu gestalten: Routingziele und Zustellungsgruppen.

## Routingziele

In Exchange 2013 wird das endgültige Ziel einer Nachricht als *Routingziel* bezeichnet. Es gibt folgende Routingziele in Exchange 2013:

  - **Eine Postfachdatenbank**   Dies ist das Routingziel für jeden Empfänger mit einem Postfach auf einem Postfachserver in der Exchange-Organisation. In Exchange 2013 stellen öffentliche Ordner eine Art von Postfach dar, das Routen von Nachrichten an Empfänger in öffentlichen Ordnern funktioniert also genauso wie das Routen von Nachrichten an Postfachempfänger.

  - **Ein Connector**   Ein Connector ist ein Sendeconnector für SMTP-Nachrichten, wenn er als Routingziel verwendet wird. Ein Zustellungs-Agent-Connector oder ein fremder Connector werden als Routingziel für Nachrichten verwendet, die nicht über SMTP gesendet werden.

  - **Ein Server für die Aufgliederung der Verteilergruppen**   Dies ist das Routingziel, wenn eine Verteilergruppe über einen designierten Server verfügt, der für die Aufgliederung der Mitgliedsliste der Gruppe zuständig ist. Ein Server für die Aufgliederung der Verteilergruppen ist immer ein Hub-Transport-Server oder ein Exchange 2013-Postfachserver.

Beachten Sie, dass die gleichen Routingziele bereits in früheren Exchange-Versionen existierten.

Zurück zum Seitenanfang

## Zustellungsgruppen

Jedes Routingziel in Exchange 2013 verfügt über einen Transportserver oder eine Sammlung von Transportservern, die für die Zustellung von Nachrichten an dieses Routingziel zuständig sind. Diese Sammlung von Transportservern wird als *Zustellungsgruppe* bezeichnet. Bei einem Transportserver kann es sich um einen Exchange 2013-Postfachserver, einen Exchange 2010-Server oder einen Exchange 2007-Server handeln, auf dem die Hub-Transport-Serverrolle installiert ist. Wenn das Routingziel eine Postfachdatenbank ist, müssen die Transportserver in der Zustellungsgruppe die gleiche Exchange-Version aufweisen wie die Postfachdatenbank. Wenn das Routingziel ein Connector oder Server für die Aufgliederung von Verteilergruppen ist, kann die Zustellungsgruppe sowohl Exchange 2013-Postfachserver als auch Exchange 2010- oder Exchange 2007-Hub-Transport-Server umfassen. Die Art und Weise, in der eine Nachricht weitergeleitet wird, richtet sich nach der Beziehung zwischen dem Quelltransportserver und der Zielzustellungsgruppe:

  - Wenn der Quelltransportserver sich in der Zielzustellungsgruppe befindet, ist das Routingziel selbst der nächste Hop für die Nachricht. Die Nachricht wird vom Quelltransportserver an die Postfachdatenbank oder den Connector auf einem Transportserver in der Zustellungsgruppe gesendet. Beachten Sie: Wenn ein Server für die Aufgliederung der Verteilergruppen das Routingziel ist, wurde die Verteilergruppe zu dem Zeitpunkt, an dem die Nachrichten die Kategorisierungsphase auf dem Server für die Aufgliederung der Verteilergruppen erreichen, bereits aufgegliedert. Daher ist das Routingziel des Servers für die Aufgliederung der Verteilergruppen immer eine Postfachdatenbank oder ein Connector.

  - Wenn sich der Quelltransportserver außerhalb der Zielzustellungsgruppe befindet, wird die Nachricht mittels Relay über den kostengünstigsten Routingpfad an die Zielzustellungsgruppe weitergeleitet. Je nach Größe und Komplexität der Exchange-Topologie wird die Nachricht über andere Transportserver entlang des kostengünstigsten Routingpfads oder direkt an einen Transportserver in der Zielzustellungsgruppe weitergeleitet.

In Exchange 2013 gibt es folgende Arten von Zustellungsgruppen:

  - **Routingfähige DAG**   Dies ist eine Sammlung von Exchange 2013-Postfachservern, die zu einer gemeinsamen DAG gehören. Die Postfachdatenbanken in der DAG sind die Routingziele, die von dieser Zustellungsgruppe bedient werden. Nachdem eine Nachricht vom Transportdienst auf einem Postfachserver empfangen wurde, der zu der DAG gehört, leitet der Transportdienst die Nachricht an den Postfachtransportdienst auf dem Postfachserver in der DAG weiter, auf dem derzeit die aktive Kopie der Zielpostfachdatenbank gespeichert ist. Der Postfachtransportdienst auf dem Zielpostfachserver sendet die Nachricht dann an die lokale Postfachdatenbank. Obwohl eine DAG Postfachserver aus verschiedenen Active Directory-Standorten umfassen kann, stellt die DAG die Grenze der Zustellungsgruppe dar.

  - **Postfachzustellungsgruppe**   Dies ist eine Sammlung von Exchange-Servern der gleichen Version, die sich am gleichen Active Directory-Standort befinden. Der Active Directory-Standort stellt die Grenze der Zustellungsgruppe dar. Die Routingziele und die Zustellungsgruppen, die diese bedienen, werden nach den Hauptversionen von Exchange am Active Directory-Standort getrennt. Die Postfachdatenbanken auf Exchange 2010-Postfachservern werden von den Exchange 2010-Hub-Transport-Servern am Active Directory-Standort bedient. Die Postfachdatenbanken auf Exchange 2007-Postfachservern werden von den Exchange 2007-Hub-Transport-Servern am Active Directory-Standort bedient. Die Postfachdatenbanken auf Exchange 2013-Postfachservern am Active Directory-Standort, die zu keiner DAG gehören, werden vom Transportdienst auf Exchange 2013-Postfachservern am Active Directory-Standort bedient. Die Art und Weise, in der eine Nachricht an die Postfachdatenbank gesendet wird, richtet sich nach der Exchange-Version:
    
      - **Exchange 2013**   Nachdem eine Nachricht auf dem Zielpostfachserver am Active Directory-Zielstandort empfangen wurde, leitet der Transportdienst die Nachricht unter Verwendung von SMTP an den Postfachtransportdienst weiter. Der Postfachtransportdienst sendet die Nachricht dann mithilfe eines RPC an die lokale Postfachdatenbank.
    
      - **Exchange 2010oder Exchange 2007**  Nachdem die Nachricht von einem beliebigen Hub-Transport-Server derselben Version am Active Directory-Zielstandort empfangen wurde, verwendet der Speichertreiber auf dem Hub-Transport-Server einen RPC, um die Nachricht in die Postfachdatenbank zu schreiben..

  - **Connectorquellserver**   Dies ist eine Mischung aus Exchange 2010- oder Exchange 2007-Hub-Transport-Servern oder Exchange 2013-Postfachservern, die als Quellserver für einen Sendeconnector, einen Zustellungs-Agent-Connector oder einen fremden Connector festgelegt wurden. Der Connector ist das Routingziel, das von dieser Routinggruppe bedient wird. Wenn ein Connector einem bestimmten Server zugeordnet wurde, darf nur dieser Server Nachrichten an Ziele weiterleiten, die vom Connector definiert wurden. Diese Zustellungsgruppe kann Exchange 2010- oder Exchange 2007-Hub-Transport-Server oder Exchange 2013-Postfachserver umfassen, die sich an verschiedenen Active Directory-Standorten befinden.

  - **AD-Standort**   Unter Umständen ist ein Active Directory-Standort nicht das endgültige Ziel einer Nachricht, sondern die Nachricht muss einen Exchange 2010- oder Exchange 2007-Hub-Transport-Server oder Exchange 2013-Postfachserver an diesem Active Directory-Standort durchlaufen. Dies kann in folgenden Fällen zutreffen:
    
      - Der Active Directory-Standort ist als Hubstandort konfiguriert. Wenn sich der Hubstand im kostengünstigsten Routingpfad für die Nachrichtenzustellung befindet, werden die Nachrichten in einer Warteschlange gespeichert und von einem Transportserver am Hubstandort verarbeitet, bevor sie mittels Relay an ihr endgültiges Ziel weitergeleitet werden.
    
      - Wenn ein Edge-Transport-Server vom Active Directory-Standort abonniert ist. Auf diese abonnierten Edge-Transport-Server kann von anderen Active Directory-Standorten nicht direkt zugegriffen werden. Bei dem Edge-Transport-Server kann es sich um Exchange 2013, Exchange 2010 oder Exchange 2007 handeln.
    

    > [!NOTE]
    > Die verzögerte Auffächerung wird nur verwendet, wenn es sich bei der Zustellungsgruppe um einen Active Directory-Standort handelt. Bei der verzögerten Auffächerung wird versucht, die Anzahl von Nachrichtenübermittlungen zu reduzieren, wenn mehrere Empfänger einen Teil des kostengünstigsten Routingpfads gemeinsam nutzen.



  - **Serverliste**   Dies ist eine Sammlung von mindestens einem Exchange 2010- oder Exchange 2007-Hub-Transport-Server oder Exchange 2013-Postfachserver, die als Server für die Aufgliederung der Verteilergruppe konfiguriert sind. Der Server für die Aufgliederung der Verteilergruppe ist das Routingziel, das von dieser Zustellungsgruppe bedient wird.

Eine Mitgliedschaft in mehreren Zustellungsgruppen ist möglich. Beispielsweise kann ein Exchange 2013-Postfachserver, der Mitglied einer DAG ist, auch der Quellserver eines Sendeconnectors mit Bereich sein. Ein solcher Postfachserver würde sowohl zur Zustellungsgruppe der routingfähigen DAG für die Postfachdatenbanken in der DAG als auch zu einer Zustellungsgruppe der Connectorquellserver für den Sendeconnector mit Bereich gehören.

Die folgende Tabelle zeigt eine Zuordnung der Routingziele zur jeweiligen Zustellungsgruppe, basierend auf der Exchange-Version:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Exchange 2013-Postfachserver</th>
<th>Exchange 2010- oder Exchange 2007-Hub-Transport-Server</th>
<th>Edge-Transport-Server im Umkreisnetzwerk</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Postfachdatenbank in einer DAG</p></td>
<td><p>Routingfähige DAG</p></td>
<td><p>Postfachzustellungsgruppe</p></td>
<td><p>N/V</p></td>
</tr>
<tr class="even">
<td><p>Postfachdatenbank außerhalb einer DAG</p></td>
<td><p>Postfachzustellungsgruppe</p></td>
<td><p>Postfachzustellungsgruppe</p></td>
<td><p>N/V</p></td>
</tr>
<tr class="odd">
<td><p>Connector</p></td>
<td><p>Connectorquellserver</p></td>
<td><p>Connectorquellserver</p></td>
<td><p>AD-Standort</p></td>
</tr>
<tr class="even">
<td><p>Server für die Aufgliederung der Verteilergruppe</p></td>
<td><p>Serverliste</p></td>
<td><p>Serverliste</p></td>
<td><p>N/V</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Warteschlangen

Aus der Perspektive des sendenden Servers stellt jede Zustellungswarteschlange das Ziel für eine bestimmte Nachricht dar. Wenn der Transportdienst auf dem Exchange 2013-Postfachserver das Ziel für eine Nachricht auswählt, wird das Ziel als Attribut **NextHopSolutionKey** auf den Empfänger gestempelt. Wenn eine einzelne Nachricht an mehrere Empfänger gesendet wird, verfügt jeder dieser Empfänger über das Attribut **NextHopSolutionKey**. Der empfangende Server führt ebenfalls Nachrichtenkategorisierung durch und reiht die Nachricht für die Zustellung in eine Warteschlange ein. Nachdem eine Nachricht in einer Warteschlange gespeichert wurde, können Sie den Zustellungstyp für eine bestimmte Warteschlange untersuchen, damit Sie bestimmen können, ob eine Nachricht nochmals mittels Relay weitergeleitet wird, wenn sie das nächste Hopziel erreicht. Jeder eindeutige Wert des Attributs **NextHopSolutionKey** entspricht einer separaten Zustellungswarteschlange.

Weitere Informationen finden Sie im Abschnitt "NextHopSolutionKey" im Thema [Warteschlangen](queues-exchange-2013-help.md).

Zurück zum Seitenanfang

## Weiterleiten von Nachrichten

Wenn eine Nachricht an eine Remotezustellungsgruppe gesendet werden muss, muss ein Routingpfad für die Nachricht ermittelt werden. verwendet folgende Logik, um den Routingpfad für eine Nachricht auszuwählen. Diese Logik wurde weitgehend unverändert aus Exchange 2010 übernommen:

1.  Es wird der kostengünstigste Routingpfad berechnet, indem die Kosten der IP-Standortverknüpfungen addiert werden, die zum Erreichen des Ziels durchlaufen werden müssen. Wenn das Ziel ein Connector ist, werden die dem Adressraum zugewiesenen Kosten zu den Kosten addiert, die zum Erreichen des ausgewählten Connectors erforderlich sind. Wenn mehrere Routingpfade möglich sind, wird der Routingpfad mit den geringsten Gesamtkosten verwendet.

2.  Wenn mehrere Routingpfade die gleichen Gesamtkosten aufweisen, wird die Anzahl der Hops in jedem Pfad ausgewertet, und der Routingpfad mit der geringsten Anzahl von Hops wird verwendet.

3.  Wenn dann immer noch mehrere Routingpfade zur Verfügung stehen, werden die Namen berücksichtigt, die den Active Directory-Standorten vor dem Ziel zugeordnet sind. Es wird der Routingpfad verwendet, in dem der Active Directory-Standort, der dem Ziel am nächsten ist, in der alphanumerischen Reihenfolge am niedrigsten ist. Wenn der Standort in größter Nähe zum Ziel für alle ausgewerteten Routingpfade identisch ist, wird ein früherer Standortname berücksichtigt.

In Exchange 2010 ist jeder Nachrichtenempfänger immer einem einzigen Active Directory-Standort zugeordnet, und es gibt nur einen kostengünstigsten Routingpfad vom Active Directory-Quellstandort zum Active Directory-Zielstandort. In Exchange 2013 kann sich eine Zustellungsgruppe über mehrere Active Directory-Standorte erstrecken, und es kann mehrere kostengünstigste Routingpfade zu mehreren Active Directory-Zielstandorten geben. legt einen einzigen Active Directory-Standort in der Zielzustellungsgruppe als *primären Standort* fest. Der primäre Standort ist der basierend auf der oben beschriebenen Routinglogik nächstgelegene Active Directory-Standort. In Exchange 2013 werden folgende Aspekte berücksichtigt, um Nachrichten erfolgreich zwischen Zustellungsgruppen weiterleiten zu können:

  - **Mindestens ein Hubstandort entlang des kostengünstigsten Routingpfads**   Wenn sich Hubstandorte im kostengünstigsten Routingpfad zum primären Standort befinden, müssen die Nachrichten durch die Hubstandorte geroutet werden. Der nächstgelegene Hubstandort im kostengünstigsten Routingpfad wird als neue Zustellungsgruppe vom Typ **AD site** ausgewählt und umfasst alle Transportserver am Hubstandort. Nachdem die Nachricht den Hubstandort durchlaufen hat, wird die Weiterleitung entlang des kostengünstigsten Routingpfads fortgesetzt. Wenn es sich beim primären Standort gleichzeitig um einen Hubstandort handelt, wird der primäre Standort aus folgenden Gründen weiterhin als Hubstandort betrachtet:
    
      - Wenn sich die Zielzustellungsgruppe über mehrere Active Directory-Standorte erstreckt, sollte der Quellserver nur eine Verbindung mit den Servern am Hubstandort herstellen.
    
      - Die Server am Hubstandort, die tatsächlich zur Zielzustellungsgruppe gehören, werden bevorzugt.
    
    Wie in vorherigen Exchange-Versionen werden alle Hubstandorte ignoriert, die sich nicht im kostengünstigsten Routingpfad zum primären Standort befinden.

  - **Der in der Zielroutinggruppe auszuwählende Exchange-Zielserver**   Wenn sich die Zielzustellungsgruppe über mehrere Active Directory-Standorte erstreckt, weist der Routingpfad zu bestimmten Servern innerhalb der Zustellungsgruppe möglicherweise unterschiedliche Kosten auf. Server, die sich am nächstgelegenen Active Directory-Standort befinden, werden basierend auf dem kostengünstigsten Routingpfad als Zielserver für die Zustellungsgruppe ausgewählt, und der Active Directory-Standort, an dem sich diese Server befinden, wird als primärer Standort ausgewählt.

  - **Rückgriff auf Fallbackoptionen, wenn eine Verbindungsherstellung mit keinem Server in der Zielroutinggruppe möglich ist**   Wenn sich die Zielzustellungsgruppe über mehrere Active Directory-Standorte erstreckt, besteht die erste Fallbackoption darin, alle anderen Server in der Zielzustellungsgruppe an anderen Active Directory-Standorten zu kontaktieren, die nicht als Zielserver ausgewählt sind. Die Server werden basierend auf den Kosten der Routingpfade zu diesen anderen Active Directory-Standorten ausgewählt. Wenn die Zielzustellungsgruppe über Server am lokalen Active Directory-Standort verfügt, gibt es keine weiteren Fallbackoptionen, da die Nachricht bereits so nah wie möglich an das Routingziel weitergeleitet wurde. Wenn die Zielzustellungsgruppe über Server an Active Directory-Remotestandorten verfügt, besteht die Option darin, zu versuchen, eine Verbindung mit allen anderen Servern im primären Standort herzustellen. Wenn dies nicht funktioniert, wird ein Backoffpfad im kostengünstigsten Routingpfad zum primären Standort verwendet. Exchange 2013 versucht, die Nachricht so nah wie möglich an das Ziel zu übermitteln, indem mithilfe des Backoffmechanismus der kostengünstigste Routingpfad Hop für Hop zurückverfolgt wird, bis eine Verbindung hergestellt werden kann.

Zurück zum Seitenanfang

## Routing von Nachrichten zwischen Active Directory-Standorten

Die Art und Weise, in der Exchange 2013 Nachrichten zwischen Active Directory-Standorten routet, ist weitestgehend die gleiche wie in Exchange 2010. Weitere Informationen finden Sie unter [Weiterleiten von E-Mails zwischen Active Directory-Standorten](route-mail-between-active-directory-sites-exchange-2013-help.md).

Zurück zum Seitenanfang

## Weiterleitung im Front-End-Transport-Dienst auf Clientzugriffsservern

Dieser Dienst fungiert als zustandsloser Proxy für den gesamten eingehenden und (optional) ausgehenden externen SMTP-Datenverkehr für die Exchange 2013-Organisation. Für ausgehende Nachrichten verwendet der Transportdienst Sendeconnectors zur Kommunikation mit dem Front-End-Transport-Dienst auf einem Clientzugriffsserver. Ausgehende Nachrichten werden insbesondere dann per Proxy über den Front-End-Transport-Dienst weitergeleitet, wenn der Parameter *FrontEndProxyEnabled* auf einem geeigneten Sendeconnector auf `$true` festgelegt ist oder wenn in den Eigenschaften des Sendeconnectors in der Exchange-Verwaltungskonsole die Option **Proxy über Clientzugriffsserver** ausgewählt ist. Es wird ein beliebiger Clientzugriffsserver am lokalen Active Directory-Standort ausgewählt. Der Front-End-Transport-Dienst hat keine Sendeconnectors.

Bei eingehenden Nachrichten muss der Front-End-Transport-Dienst schnell einen einzelnen, fehlerfreien Transportdienst auf einem Postfachserver finden, der die Nachrichtenübermittlung empfangen kann, unabhängig von Anzahl oder Typ der Empfänger. Falls dies nicht möglich, wird der E-Mail-Dienst von den externen Absendern als nicht verfügbar eingestuft. Ebenso wie der Transportdienst lädt der Front-End-Transport-Dienst Routingtabellen basierend auf Informationen aus Active Directory und verwendet Zustellungsgruppen, um die Weiterleitung von Nachrichten festzulegen. Die vom Front-End-Transport-Dienst verwendeten Routingtabellen weisen jedoch folgende einzigartige Merkmale auf:

  - Der Front-End-Transport-Dienst wird niemals als Mitglied einer Zustellungsgruppe betrachtet, selbst wenn der Postfachserver und der Clientzugriffsserver auf dem gleichen physischen Server installiert sind. Aus diesem Grund ist der Front-End-Transport-Dienst gezwungen, ausschließlich mit dem Transportdienst zu kommunizieren.

  - Die Routingtabellen enthalten keine Sendeconnectorrouten.

  - Die Routingtabellen enthalten eine spezielle Liste mit Postfachservern am lokalen Active Directory-Standort, damit ein schnelles Failover möglich ist.

Beim Routing im Front-End-Transport-Dienst werden die Namen der Nachrichtenempfänger in Postfachdatenbanken aufgelöst. Die Liste der vom Front-End-Transport-Dienst verwendeten Postfachserver basiert auf den Postfachdatenbanken der Nachrichtenempfänger. Beachten Sie, dass möglicherweise keiner der Empfänger über Postfächer verfügt, z. B. wenn der Empfänger eine Verteilergruppe oder ein E-Mail-Benutzer ist. Der Front-End-Transport-Dienst sucht für jede Postfachdatenbank die Zustellungsgruppe und die zugehörigen Routinginformationen. Folgende Zustellungsgruppen werden vom Front-End-Transport-Dienst verwendet:

  - Routingfähige DAG

  - Postfachzustellungsgruppe

  - AD-Standort

Je nach Anzahl und Typ der Empfänger führt der Front-End-Transport-Dienst eine der folgenden Aktionen aus:

  - Für Nachrichten, die an einen Empfänger mit einzelnem Postfach gerichtet sind, wird ein Postfachserver in der Zielzustellungsgruppe ausgewählt, dabei wird der Postfachserver bevorzugt, der dem Active Directory-Standort am nächsten gelegen ist. Die Weiterleitung von Nachrichten zum Empfänger umfasst möglicherweise die Weiterleitung der Nachricht über einen Hubstandort.

  - Für Nachrichten, die an Empfänger mit mehreren Postfächern gerichtet sind, werden die ersten 20 Empfänger verwendet, um einen Postfachserver in der am nächsten gelegenen Zustellungsgruppe auswählen, basierend auf der Nähe zum Active Directory-Standort. Beachten Sie, dass im Front-End-Transport-Dienst keine Nachrichtenverzweigung erfolgt, es wird also letztendlich nur ein Postfachserver ausgewählt, unabhängig von der Anzahl von Empfängern in einer Nachricht.

  - Wenn eine Nachricht keine Postfachempfänger enthält, wird ein zufälliger Postfachserver am lokalen Active Directory-Standort ausgewählt.

Zurück zum Seitenanfang

## Weiterleitung im Postfachtransportdienst auf Postfachservern

Dieser Dienst besteht aus zwei getrennten Diensten: dem Dienst für die Postfachtransportübermittlung und dem Dienst für die Postfachtransportzustellung. Bei eingehenden Nachrichten empfängt der Dienst für die Postfachtransportzustellung SMTP-Nachrichten vom Transportdienst und stellt über einen RPC eine Verbindung mit der lokalen Postfachdatenbank her, um die Nachricht zuzustellen. Bei ausgehenden Nachrichten stellt der Dienst für die Postfachtransportübermittlung über einen RPC eine Verbindung mit der lokalen Postfachdatenbank her, um die Nachrichten abzurufen, und übermittelt die Nachrichten per SMTP an den Transportdienst. Der Postfachtransportdienst ist zustandslos und stellt keine Nachrichten in die lokale Warteschlange.

Ebenso wie der Transportdienst lädt der Postfachtransportdienst Routingtabellen basierend auf Informationen aus Active Directory und verwendet Zustellungsgruppen, um die Weiterleitung von Nachrichten festzulegen. Der Postfachtransportdienst weist jedoch einige einzigartige Routingaspekte auf:

  - Da sich der Transportdienst und der Postfachtransportdienst auf dem gleichen Exchange 2013-Postfachserver befinden, gehört der Postfachtransportdienst immer zur gleichen Zustellungsgruppe wie der Postfachserver. Diese Zustellungsgruppe wird als *lokale Zustellungsgruppe* bezeichnet.

  - Der Dienst für die Postfachtransportübermittlung sendet Nachrichten nicht automatisch an den Transportdienst auf dem lokalen Postfachserver oder auf anderen Postfachservern in der eigenen lokalen Zustellungsgruppe. Der Dienst für die Postfachtransportübermittlung greift auf die gleichen Informationen zur Routingtopologie zu wie der Transportdienst und kann daher Nachrichten an den Transportdienst auf Postfachservern außerhalb der Zustellungsgruppe senden. Die Postfachserver in der lokalen Zustellungsgruppe werden als Fallbackoptionen genutzt und zur Zustellung an Empfänger ohne Postfach verwendet.

  - Der Postfachtransportdienst kommuniziert nur mit dem Transportdienst auf Exchange 2013-Postfachservern.

  - Der Postfachtransportdienst kommuniziert nur mit Postfachdatenbanken auf dem lokalen Exchange 2013-Postfachserver. Der Postfachtransportdienst kommuniziert niemals mit Postfachdatenbanken auf anderen Postfachservern.

Wenn ein Benutzer eine Nachricht aus dem Postfach sendet, löst der Dienst für die Postfachtransportübermittlung die Namen der Nachrichtenempfänger in Postfachdatenbanken auf. Die Liste der vom Dienst für die Postfachtransportübermittlung verwendeten Postfachserver basiert auf den Postfachdatenbanken der Nachrichtenempfänger. Beachten Sie, dass möglicherweise keiner der Empfänger über Postfächer verfügt, z. B. wenn der Empfänger eine Verteilergruppe oder ein E-Mail-Benutzer ist. Der Dienst für die Postfachtransportübermittlung sucht für jede Postfachdatenbank die Zustellungsgruppe und die zugehörigen Routinginformationen. Folgende Zustellungsgruppen werden vom Dienst für die Postfachtransportübermittlung verwendet:

  - Routingfähige DAG

  - Postfachzustellungsgruppe

  - AD-Standort

Je nach Anzahl und Typ der Empfänger führt der Dienst für die Postfachtransportübermittlung eine der folgenden Aktionen aus:

  - Für Nachrichten, die an einen Empfänger mit einzelnem Postfach gerichtet sind, wird ein Postfachserver in der Zielzustellungsgruppe ausgewählt, dabei wird der Postfachserver bevorzugt, der dem Active Directory-Standort am nächsten gelegen ist. Die Weiterleitung von Nachrichten zum Empfänger umfasst möglicherweise die Weiterleitung der Nachricht über einen Hubstandort.

  - Für Nachrichten, die an Empfänger mit mehreren Postfächern gerichtet sind, werden die ersten 20 Empfänger verwendet, um einen Postfachserver in der am nächsten gelegenen Zustellungsgruppe auswählen, basierend auf der Nähe zum Active Directory-Standort.

  - Wenn eine Nachricht keine Postfachempfänger enthält, wird ein Postfachserver in der lokalen Zustellungsgruppe ausgewählt.

Wenn der Dienst für die Postfachtransportzustellung eine Nachricht vom Transportdienst empfängt, kann der Dienst die Zustellung der Nachricht an eine lokale Postfachdatenbank akzeptieren oder ablehnen. Der Dienst für die Postfachtransportzustellung kann die Nachricht zustellen, wenn sich der Empfänger in einer aktiven Kopie einer lokalen Postfachdatenbank befindet. Befindet sich der Empfänger jedoch nicht in einer aktiven Kopie einer lokalen Postfachdatenbank, kann der Dienst für die Postfachtransportzustellung die Nachricht nicht zustellen und muss dem Transportdienst eine Unzustellbarkeitsbericht senden. Wenn die aktive Kopie der Postfachdatenbank z. B. kürzlich auf einen anderen Server verschoben wurde, überträgt der Transportdienst möglicherweise irrtümlich eine Nachricht an einen Postfachserver, auf dem sich jetzt eine inaktive Kopie der Postfachdatenbank befindet. Die Unzustellbarkeitsberichte, die der Dienst für die Postfachtransportzustellung an den Transportdienst zurückgibt, enthalten folgende Informationen:

  - Erneuter Zustellungsversuch

  - Generieren eines Unzustellbarkeitsberichts

  - Umleiten der Nachricht

Zurück zum Seitenanfang

## Weiterleitung im Transportdienst auf Edge-Transport-Servern

Wenn Sie in Ihrem Umkreisnetzwerk einen Edge-Transport-Server installiert haben, bietet der Transportdienst auf dem Edge-Transport-Server SMTP-Relay- (Simple Mail Transfer Protocol) und Smarthost-Dienste für den gesamten internetseitigen Nachrichtenfluss. Aus dem Internet stammende bzw. in das Internet gehende Nachrichten werden lokal auf dem Edge-Transport-Server in einer Warteschlange abgelegt. Die Warteschlangen entsprechen externen Domänen oder Sendeconnectors. Weitere Informationen finden Sie im Abschnitt "NextHopSolutionKey" im Thema [Warteschlangen](queues-exchange-2013-help.md).

Wenn Sie in Ihrem Umkreisnetzwerk einen Edge-Transport-Server installieren, müssen Sie in der Regel einen Active Directory-Standort für diesen Server abonnieren. Der Active Directory-Standort enthält die Postfachserver, die Nachrichten an den und von dem Edge-Transport-Server weiterleiten. Der Edge-Abonnementprozess erstellt eine Mitgliedschaft beim Active Directory-Standort für den Edge-Transport-Dienst. Durch die Standortmitgliedschaft können die Postfachserver im Active Directory-Standort Nachrichten mittels Relay an den Edge-Transport-Server für die Zustellung im Internet weiterleiten, ohne dass explizite Sendeconnectors konfiguriert werden müssen.

In Konfigurationen mit mehreren Standorten werden ausgehende Nachrichten von internen Empfängern an externe Empfänger zunächst an den abonnierten Active Directory-Standort weitergeleitet. Die Zustellungsgruppe ist der Active Directory-Zielstandort. Das Weiterleitungsziel ist der organisationsinterne Sendeconnector im Transportdienst auf einem der Postfachserver, die sich im abonnierten Active Directory-Standort befinden. Der *organisationsinterne Sendeconnector* ist ein spezieller Sendeconnector, der im Transportdienst auf jedem Postfachserver vorliegt. Dieser Sendeconnector wird implizit erstellt, ist nicht sichtbar, erfordert keine Verwaltung und wird dazu verwendet, Nachrichten zwischen Exchange-Servern weiterzuleiten.

Ausgehende Nachrichten für externe Empfänger werden vom Postfachserver an den Edge-Transport-Server weitergeleitet. Der Clientzugriffsserver ist an der Weiterleitung von Nachrichten an einen abonnierten Edge-Transport-Server nicht beteiligt. Nachrichten werden von dem organisationsinternen Sendeconnector im Transportdienst auf dem Postfachserver zu einem Empfangsconnector im Transportdienst auf dem Edge-Transport-Server übertragen. Auf einem abonnierten Edge-Transport-Server ist der Standardempfangsconnector so konfiguriert, dass er sowohl Verbindungen von internen, in dem abonnierten Active Directory-Standort befindlichen Postfachservern als auch anonyme Verbindungen aus dem Internet abfragt. Nachdem der Transportdienst auf dem Edge-Transport-Server die Nachricht kategorisiert hat, wird sie lokal in einer Warteschlange abgelegt, von der aus sie dann mittels des dedizierten Sendeconnectors, der gleichzeitig mit dem Edge-Abonnement erstellt wurde, an das Internet übermittelt wird.

Eingehende Nachrichten von externen Empfängern kommen über den Standardempfangsconnector auf dem Edge-Transport-Server an, werden dort kategorisiert und in einer Warteschlange gespeichert, in der sie auf die Zustellung warten. Die Nachrichten werden über den dedizierten Sendeconnector weitergeleitet, der gleichzeitig mit dem Edge-Abonnement erstellt wurde, und gelangen dann an die Exchange-Organisation. Wohin die Nachrichten dann als Nächstes gelangen, hängt davon ab, wie die internen Exchange-Server konfiguriert sind.

  - **Postfachserver und Clientzugriffsserver auf demselben Computer installiert**   In dieser Konfiguration wird der Clientzugriffsserver für die eingehende Nachrichtenübermittlung verwendet. Nachrichten werden vom Sendeconnector im Transportdienst auf dem Edge-Transport-Server an den Standardempfangsconnector im Front-End-Transport-Dienst auf dem Clientzugriffsserver und anschließend an den Standardempfangsconnector im Transportdienst auf dem Postfachserver übermittelt.

  - **Postfachserver und Clientzugriffsserver auf verschiedenen Computern installiert**   In dieser Konfiguration wird der Clientzugriffsserver bei der Übermittlung eingehender Nachrichten umgangen. Nachrichten werden vom Sendeconnector im Transportdienst auf dem Edge-Transport-Server zu dem Standardempfangsconnector im Transportdienst auf dem Postfachserver übertragen.

Wenn in Ihrem Umkreisnetzwerk ein Exchange 2007- oder Exchange 2010-Edge-Transport-Server installiert ist, werden eingehende und ausgehende Nachrichten immer direkt zwischen dem Edge-Transport-Server und dem Postfachsserver übermittelt. Der Clientzugriffsserver wird nicht verwendet.

Zurück zum Seitenanfang

