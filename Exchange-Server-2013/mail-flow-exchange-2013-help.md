---
title: 'Nachrichtenübermittlung: Exchange 2013 Help'
TOCTitle: Nachrichtenübermittlung
ms:assetid: 14df5e1a-a5f7-4b0d-ba97-f53b76f0e7e0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996349(v=EXCHG.150)
ms:contentKeyID: 50475150
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichtenübermittlung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In Microsoft Exchange Server 2013 erfolgt die Nachrichtenübermittlung über die Transportpipeline. Die *Transportpipeline* besteht aus einer Sammlung von Diensten, Verbindungen, Komponenten und Warteschlangen, die gemeinsam eingesetzt werden, um alle Nachrichten an ein Kategorisierungsmodul im Transportdienst auf einem Postfachserver innerhalb der Organisation weiterzuleiten.

Möchten Sie wissen, welche anderen Themen es im Zusammenhang mit der Nachrichtenübermittlung gibt? Weitere Informationen finden Sie unter Dokumentation zur Nachrichtenübermittlung.

Informationen zum Konfigurieren von Transportregeln des Nachrichtenflusses in einer neuen Exchange 2013-Organisation finden Sie unter [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md).

**Inhalt**

Die Transportpipeline

Transportdienst auf Postfachservern

Dokumentation zur Nachrichtenübermittlung

## Die Transportpipeline

Die Transportpipeline umfasst die folgenden Dienste:

  - **Front-End-Transport-Dienst auf Clientzugriffsservern**   Dieser Dienst fungiert als zustandsloser Proxy für den gesamten eingehenden und (optional) ausgehenden externen SMTP-Datenverkehr für die Exchange 2013-Organisation. Der Front-End-Transport-Dienst überprüft nicht den Nachrichteninhalt, kommuniziert nicht mit dem Postfachtransportdienst auf Postfachservern und stellt Nachrichten nicht lokal in eine Warteschlange.

  - **Transportdienst auf Postfachservern**   Dieser Dienst ist weitestgehend mit der Hub-Transport-Serverrolle identisch, die es in früheren Exchange-Versionen gibt. Der Transportdienst verarbeitet den gesamten SMTP-Nachrichtenfluss für die Organisation, kategorisiert Nachrichten und untersucht die Nachrichteninhalte. Anders als in früheren Exchange-Versionen kommuniziert der Transportdienst nie direkt mit Postfachdatenbanken. Diese Aufgabe wird jetzt vom Postfachtransportdienst übernommen. Der Transportdienst leitet Nachrichten zwischen dem Postfachtransportdienst, dem Transportdienst, dem Front-End-Transportdienst und (je nach Ihrer Konfiguration) dem Transportdienst auf Edge-Transport-Servern weiter. Der Transportdienst auf Postfachservern wird später in diesem Thema genauer beschrieben.

  - **Postfachtransportdienst auf Postfachservern**   Dieser Dienst besteht aus zwei getrennten Diensten:: dem Dienst für die Postfachtransportübermittlung und dem Dienst für die Postfachtransportzustellung. Der Dienst für die Postfachtransportzustellung empfängt SMTP-Nachrichten vom Transportdienst auf dem lokalen Postfachserver oder auf anderen Postfachservern und stellt über einen Exchange-Remoteprozeduraufruf eine Verbindung mit der lokalen Postfachdatenbank her, um die Nachricht zuzustellen. Der Dienst für die Postfachtransportübermittlung stellt über einen Remoteprozeduraufruf eine Verbindung mit der lokalen Postfachdatenbank her, um die Nachrichten abzurufen, und übermittelt die Nachrichten per SMTP an den Transportdienst auf dem lokalen Postfachserver oder auf anderen Postfachservern. Der Dienst für die Postfachtransportübermittlung greift auf die gleichen Informationen zur Routingtopologie zu wie der Transportdienst. Wie der Front-End-Transport-Dienst platziert auch der Postfachtransportdienst keine Nachrichten in einer lokalen Warteschlange.

  - **Transportdienst auf Edge-Transport-Servern**   Dieser Dienst ist dem Transportdienst auf Postfachservern sehr ähnlich. Wenn Sie einen Edge-Transport-Server im Umkreisnetzwerk installiert haben, werden alle Nachrichten aus dem Internet oder in das Internet über den Edge-Transport-Server des Transportdienstes geleitet. Dieser Dienst wird an späterer Stelle in diesem Thema genauer erläutert.

In der folgenden Abbildung werden die Beziehungen zwischen den Komponenten in der Exchange 2013-Transportpipeline dargestellt.

**Übersicht über die Transportpipeline in Exchange 2013.**

![Übersicht über die Transportpipeline (Diagramm)](images/Aa996349.6f548b64-6ac2-4e98-9098-69ad6cd9f569(EXCHG.150).gif "Übersicht über die Transportpipeline (Diagramm)")

## Nachrichten von externen Absendern

Nachrichten von außerhalb der Organisation werden über einen Empfangsconnector im Front-End-Transportdienst auf dem Clientzugriffsserver an die Transportpipeline übermittelt und anschließend an den Transportdienst auf dem Postfachserver weitergeleitet.

Wenn im Umkreisnetzwerk ein Exchange 2013 Edge-Transport-Server installiert ist, gelangen Nachrichten von außerhalb der Organisation über einen Empfangsconnector im Transportdienst auf dem Edge-Transport-Server in die Transportpipeline. Wohin die Nachrichten dann weitergeleitet werden, hängt von der Konfiguration Ihrer internen Exchange-Server ab.

  - **Postfachserver und Clientzugriffsserver auf demselben Computer installiert**   In dieser Konfiguration wird der Clientzugriffsserver für eingehende Nachrichten verwendet. Die Nachrichten gelangen vom Transportdienst auf dem Edge-Transport-Server zum Front-End-Transportdienst auf dem Clientzugriffsserver und anschließend zum Transportdienst auf dem Postfachserver.

  - **Postfachserver und Clientzugriffsserver auf verschiedenen Computern installiert**   In dieser Konfiguration wird der Clientzugriffsserver für eingehende Nachrichten umgangen. Die Nachrichten gelangen vom Transportdienst auf dem Edge-Transport-Server zum Transportdienst auf dem Postfachserver.


> [!NOTE]
> Wenn in Ihrem Umkreisnetzwerk ein Exchange 2010- oder Exchange 2007-Edge-Transport-Server installiert ist, erfolgt der Nachrichtenfluss direkt zwischen dem Edge-Transport-Server und dem Transportdienst auf dem Postfachserver. Weitere Informationen finden Sie unter <A href="use-an-exchange-2010-or-2007-edge-transport-server-in-exchange-2013-exchange-2013-help.md">Verwenden eines Exchange&nbsp;2010 oder 2007 Edge-Transport-Servers in Exchange&nbsp;2013</A>.



## Nachrichten von internen Absendern

SMTP-Nachrichten innerhalb der Organisation werden mithilfe einer der folgenden Methoden über den Transportdienst auf einem Postfachserver in die Transportpipeline übermittelt:

  - Über einen Empfangsconnector.

  - Aus dem PICKUP-Verzeichnis oder dem Wiedergabeverzeichnis.

  - Über den Postfachtransportdienst.

  - Mithilfe der Agent-Übermittlung.

Die Nachricht wird auf Grundlage des Routingziels oder der Übermittlungsgruppe weitergeleitet. Weitere Informationen finden Sie unter [E-Mail-Routing](mail-routing-exchange-2013-help.md).

Wenn die Nachricht an externe Empfänger geht, wird sie vom Transportdienst auf dem Postfachserver ins Internet oder vom Postfachserver an den Front-End-Transportdienst auf einem Clientzugriffsserver und dann ins Internet geleitet, sofern der Sendeconnector für die Proxyweiterleitung ausgehender Nachrichten über den Clientzugriffsserver konfiguriert ist, Weitere Informationen finden Sie unter [Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden](create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md).

Wenn im Umkreisnetzwerk ein Edge-Transport-Server installiert ist, werden Nachrichten an externe Empfänger niemals durch den Front-End-Transportdienst auf einem Clientzugriffsserver geleitet. Die Nachricht wird vom Transportdienst auf einem Postfachserver zum Transportdienst auf dem Edge-Transport-Server geleitet.

## Transportdienst auf Postfachservern

Jede Nachricht, die in einer Exchange 2013-Organisation gesendet oder empfangen wird, muss im Transportdienst auf einem Postfachserver kategorisiert werden, bevor sie weitergeleitet und zugestellt werden kann. Nach der Kategorisierung wird die Nachricht in einer Übermittlungswarteschlange platziert, um an die Zielpostfachdatenbank, die Ziel-DAG (Database Availability Group), den Active Directory-Standort, die Active Directory-Gesamtstruktur oder die Zieldomäne außerhalb der Organisation übermittelt zu werden.

Der Transportdienst auf einem Postfachserver umfasst die folgenden Komponenten und Prozesse:

  - **SMTP-Empfang**   Wenn der Transportdienst Nachrichten empfängt, wird der Nachrichteninhalt überprüft, Transportregeln werden angewendet, und eine Antispam- und Antischadsoftwareüberprüfung wird durchgeführt, sofern diese Funktionen aktiviert sind. Die SMTP-Sitzung umfasst eine Reihe von Ereignissen, die in einer bestimmten Reihenfolge zusammenarbeiten, um den Inhalt von Nachrichten zu prüfen, bevor diese akzeptiert werden. Wenn eine Nachricht den SMTP-Empfang vollständig durchlaufen hat und nicht aufgrund von Empfangsereignissen oder von einem Antispam- oder Antischadsoftware-Agent zurückgewiesen wird, erfolgt die Platzierung in der Übermittlungswarteschlange.

  - **Übermittlung**   Als Übermittlung wird der Vorgang bezeichnet, mit dem Nachrichten in die Übermittlungswarteschlange gesetzt werden. Vom Kategorisierungsmodul wird jeweils eine Nachricht zwecks Kategorisierung entnommen. Die Übermittlung erfolgt über drei Methoden:
    
      - Vom SMTP-Empfang über einen Empfangsconnector.
    
      - Über das PICKUP-Verzeichnis oder das Wiedergabeverzeichnis. Diese Verzeichnisse sind auf Postfachservern und Edge-Transport-Servern vorhanden. Ordnungsgemäß formatierte Nachrichtendateien, die in das PICKUP- oder Wiedergabeverzeichnis kopiert werden, werden direkt in die Übermittlungswarteschlange gestellt.
    
      - Über einen Transport-Agent.

  - **Kategorisierungsmodul**   Das Kategorisierungsmodul entnimmt der Übermittlungswarteschlange immer nur jeweils eine Nachricht. Das Kategorisierungsmodul führt die folgenden Schritte aus:
    
      - Empfängerauflösung, wozu auch die Adressierung auf oberster Ebene, die Aufgliederung und die Verzweigung gehört.
    
      - Routingauflösung.
    
      - Inhaltskonvertierung.
    
    Darüber hinaus werden von der Organisation definierte Nachrichtenübermittlungsregeln angewendet. Nach der Kategorisierung werden die Nachrichten in einer Übermittlungswarteschlange platziert, die auf dem Ziel der Nachricht basiert. Nachrichten werden basierend auf der Zielpostfachdatenbank, der Ziel-DAG, dem Active Directory-Standort, der Active Directory-Gesamtstruktur oder der externen Domäne in Warteschlangen platziert.

  - **SMTP senden**   Die Art und Weise, in der Nachrichten vom Transportdienst weitergeleitet werden, hängt davon ab, wo sich die Nachrichtenempfänger relativ zum Postfachserver befinden, auf dem die Kategorisierung erfolgt. Die Nachricht könnte an eine der folgenden Stellen geleitet werden:
    
      - An den Postfachtransportdienst auf dem gleichen Postfachserver.
    
      - An den Postfachtransportdienst auf einem anderen Postfachserver, der Teil derselben DAG ist.
    
      - An den Transportdienst auf einem Postfachserver in einer anderen DAG, Active Directory Website oder Active Directory Struktur.
    
      - Zur Übermittlung ins Internet über einen Sendeconnector auf demselben Postfachserver, über den Transportdienst auf einem anderen Postfachserver, über den Front-End-Transportdienst auf einem Clientzugriffsserver oder über den Transportdienst auf einem Edge-Transport-Server im Umkreisnetzwerk.

## Transportdienst auf Edge-Transport-Servern

Die Komponenten des Transportdienstes auf Edge-Transport-Servern sind mit den Komponenten des Transportdienstes auf Postfachservern identisch. Was während jeder Stufe der Bearbeitung auf den Edge-Transport-Servern passiert, ist allerdings unterschiedlich. Die Unterschiede werden in der folgenden Liste beschrieben.

  - **SMTP-Empfang**   Wenn ein Edge-Transport-Server von einem internen Active Directory-Standort abonniert wurde, wird der Standard-Empfangsconnector automatisch für den Empfang von E-Mail-Nachrichten aus internen Postfachservern und aus dem Internet konfiguriert. Wenn Internetnachrichten am Edge-Transport-Server ankommen, filtern Anti-Spam-Agents die Verbindungen und die Nachrichteninhalte und helfen so bei der Identifikation des Senders und des Empfängers, während die Nachricht von der Organisation empfangen wird. Die Anti-Spam-Agents sind installiert und standardmäßig aktiviert. Zusätzliche Filterungen von Anhängen und Verbindungen sind verfügbar, aber es gibt keine integrierte Malware-Filterung. Transportregeln werden außerdem durch den Edge-Regel-Agent gesteuert. Verglichen mit dem Transportregel-Agent auf Postfachservern ist auf Edge-Transport-Servern nur eine kleine Teilmenge der Transportregel-Bedingungen verfügbar. Es gibt jedoch eindeutige Transportregel-Aktionen für SMTP-Verbindungen, die nur auf Edge-Transport-Servern verfügbar sind.

  - **Übermittlung**   Auf einem Edge-Transport-Server gelangen Nachrichten normalerweise über einen Empfangsconnector in die Übermittlungswarteschlange. Aber auch das Pickup- und das Replay-Verzeichnis stehen zur Verfügung.

  - **Kategorisierungsmodul**   Auf einem Edge-Transport-Server ist Kategorisierung ein kurzes Verfahren, in dem die Nachricht direkt in eine Zustellungswarteschlange zur Zustellung an interne oder externe Empfänger geleitet wird.

  - **SMTP-Senden**   Wenn ein Edge-Transport-Server von einem internen Active Directory-Standort abonniert wird, werden automatisch zwei Sendeconnectors erstellt und konfiguriert. Einer ist für das Senden ausgehender Mails an Internet-Empfänger verantwortlich, der andere für das Senden eingehender Mails aus dem Internet an interne Empfänger. Die eingehenden Nachrichten werden an den Transportdienst auf einem verfügbaren Postfachserver am abonnierten Active Directory-Standort gesendet.

## Dokumentation zur Nachrichtenübermittlung

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zur Nachrichtenübermittlung in Exchange 2013 sowie zur Verwaltung dieser Funktionen finden.


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
<td><p><a href="mail-routing-exchange-2013-help.md">E-Mail-Routing</a></p></td>
<td><p>Über das E-Mail-Routing wird festgelegt, wie Nachrichten zwischen Messagingservern übermittelt werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="connectors-exchange-2013-help.md">Connectors</a></p></td>
<td><p>Connectors definieren, wie und über welche Komponenten eingehende und ausgehende Nachrichten für Exchange-Server übermittelt werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="domains-exchange-2013-help.md">Domänen</a></p></td>
<td><p>Akzeptierte Domänen definieren die SMTP-Adressräume, die in der Exchange-Organisation verwendet werden. Mithilfe von Remotedomänen werden die Formatierungs- und Codierungseinstellungen für Nachrichten konfiguriert, die an externe Domänen gesendet werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="transport-agents-exchange-2013-help.md">Transport-Agents</a></p></td>
<td><p>Transport-Agents führen Aktionen für Nachrichten aus, während diese über die Exchange-Transportpipeline übermittelt werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="transport-high-availability-exchange-2013-help.md">Hohe Verfügbarkeit des Transports</a></p></td>
<td><p>Über die hohe Verfügbarkeit für den Transport wird festgelegt, wie Exchange 2013 redundante Kopien von Nachrichten während und nach der Übermittlung beibehält.</p></td>
</tr>
<tr class="even">
<td><p><a href="transport-logs-exchange-2013-help.md">Transportprotokolle</a></p></td>
<td><p>In Transportprotokollen wird aufgezeichnet, welche Aktionen für Nachrichten ausgeführt werden, während diese über die Transportpipeline übermittelt werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-message-approval">Verwalten der Nachrichtengenehmigung</a></p></td>
<td><p>Bei moderierten Transporten ist für Nachrichten, die an bestimmte Empfänger gesendet werden, eine Genehmigung erforderlich.</p></td>
</tr>
<tr class="even">
<td><p><a href="content-conversion-exchange-2013-help.md">Inhaltskonvertierung</a></p></td>
<td><p>Die Inhaltskonvertierung steuert die TNEF-Nachrichtenkonvertierungsoptionen (Transport Neutral Encoding Format) für externe Empfänger sowie die MAPI-Konvertierungsoptionen für interne Empfänger.</p></td>
</tr>
<tr class="odd">
<td><p><a href="dsns-and-ndrs-in-exchange-2013-exchange-2013-help.md">DSNs und NDRs in Exchange 2013</a></p></td>
<td><p>Benachrichtigungen über den Zustellungsstatus sind Systemnachrichten, die an die Absender einer Nachricht gesendet werden (beispielsweise Unzustellbarkeitsberichte).</p></td>
</tr>
<tr class="even">
<td><p><a href="track-messages-with-delivery-reports-exchange-2013-help.md">Nachverfolgen von Nachrichten mit Zustellungsberichten</a></p></td>
<td><p>Zustellungsberichte sind ein Nachrichtenverfolgungstool, mit dem Sie anhand des Übermittlungsstatus nach E-Mails suchen können, die mit einem bestimmten Betreff und von Benutzern oder an Benutzer im Adressbuch der Organisation gesendet wurden. Sie können Zustellungsinformationen zu Nachrichten nachverfolgen, die von einem bestimmten Postfach in der Organisation gesendet oder empfangen wurden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="message-size-limits-exchange-2013-help.md">Beschränkungen der Nachrichtengröße</a></p></td>
<td><p>In diesem Thema werden die Einschränkungen beschrieben, die im Hinblick auf die Größe und einzelne Komponenten für Nachrichten gelten.</p></td>
</tr>
<tr class="even">
<td><p><a href="queue-viewer-exchange-2013-help.md">Warteschlangenanzeige</a></p></td>
<td><p>Verwenden Sie die Warteschlangenanzeige in der Exchange Toolbox, um Aktionen für Warteschlangen und Nachrichten in Warteschlangen auszuführen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="pickup-directory-and-replay-directory-exchange-2013-help.md">PICKUP-Verzeichnis und Wiedergabeverzeichnis</a></p></td>
<td><p>Die PICKUP- und Wiedergabeverzeichnisse werden verwendet, um Nachrichtendateien in die Transportpipeline einzufügen.</p></td>
</tr>
<tr class="even">
<td><p><a href="use-an-exchange-2010-or-2007-edge-transport-server-in-exchange-2013-exchange-2013-help.md">Verwenden eines Exchange 2010 oder 2007 Edge-Transport-Servers in Exchange 2013</a></p></td>
<td><p>In diesem Thema werden die Aspekte beschrieben, die bei Verwendung eines Edge-Transport-Servers aus verschiedenen Exchange-Versionen in Exchange 2013 berücksichtigt werden sollten.</p></td>
</tr>
</tbody>
</table>

