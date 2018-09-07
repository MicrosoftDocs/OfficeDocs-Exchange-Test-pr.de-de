---
title: 'Telefoniekonzepte und -komponenten: Exchange 2013 Help'
TOCTitle: Telefoniekonzepte und -komponenten
ms:assetid: ce70bf6a-db85-411b-8b93-2987703963a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124606(v=EXCHG.150)
ms:contentKeyID: 54652705
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Telefoniekonzepte und -komponenten

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-25_

Wenn Sie MicrosoftExchange 2013 Unified Messaging (UM) für Ihr Netzwerk planen und bereitstellen möchten, müssen Sie mit den Konzepten von Unified Messaging und Telefonienetzwerken vertraut sein. In diesem Thema erhalten Sie einen Überblick über Telefonieinfrastrukturkonzepte und -komponenten sowie Hilfestellungen bei der Planung und Bereitstellung von Servern mit Exchange 2013 Unified Messaging.

**Inhalt**

Übersicht

Konzepte und Komponenten

Leitungsvermittelte Netzwerke

Paketvermittelte Netzwerke

PBX-Anlagen

IP-PBX-Anlagen

SIP-aktivierte PBX-Anlagen

VoIP

VoIP-Gateways

## Übersicht

In Microsoft Exchange-Versionen vor Exchange Server 2007 bestand die Hauptaufgabe des Exchange-Administrators in der Verwaltung von E-Mail-Nachrichten und in seltenen Fällen auch in der Verwaltung einer Netzwerkinfrastruktur. Frühere Versionen von Exchange bieten keine Unified Messaging-Funktionen. Administratoren von Exchange Server, Version 5.5, Exchange 2000 Server und Exchange Server 2003 konzentrierten sich auf die Exchange-Umgebung und die Netzwerkinfrastruktur, wobei sie bei der Verwaltung der Telefonieumgebung und -infrastruktur in hohem Maße von Telekommunikationsspezialisten abhängig waren.

## Konzepte und Komponenten

Für die Bereitstellung eines Unified Messaging-Servers (UM) in Exchange 2013 benötigen Sie ein solides Verständnis grundlegender Telefoniekonzepte und -komponenten. Nachdem Sie ein solides Telefoniebasiswissen erworben haben, sind Sie in der Lage, Exchange 2013 Unified Messaging erfolgreich in eine Exchange 2013-Organisation zu integrieren. Die grundlegenden Konzepte und Komponenten umfassen Folgendes:

  - Leitungsvermittelte und paketvermittelte Netzwerke

  - PBX-Anlagen (Private Branch eXchange)

  - IP-PBX-Anlagen

  - VoIP (Voice over Internet Protocol)

  - VoIP-Gateways

## Leitungsvermittelte Netzwerke

In leitungsvermittelten Netzwerken, wie z. B. dem Public Switched Telephone Network (Internationales Analogtelefonsystem, PSTN), werden mehrere Anrufe über dasselbe Übertragungsmedium übermittelt. Häufig handelt es sich bei dem im PSTN verwendeten Medium um Kupferkabel. Es können aber auch Glasfaserkabel verwendet werden.

Ein leitungsvermitteltes Netzwerk ist ein Netzwerk, in dem eine dedizierte Verbindung besteht. Eine dedizierte Verbindung ist ein Schaltkreis oder eine Leitung, der/die zwischen zwei Knoten eingerichtet wird, um diesen die Kommunikation untereinander zu ermöglichen. Nachdem ein Anruf zwischen zwei Knoten aufgebaut wurde, kann die Verbindung nur von diesen beiden Knoten verwendet werden. Wenn der Anruf von einem der beiden Knoten beendet wird, wird auch die Verbindung unterbrochen.


> [!NOTE]
> PSTN ist ein internationaler Zusammenschluss der leitungsvermittelten Telefonnetzwerke. Dieser Zusammenschluss ähnelt dem Internet, das ein internationaler Zusammenschluss der öffentlichen IP-basierten paketvermittelten Netzwerke ist.



Es gibt zwei grundlegende Typen von leitungsvermittelten Netzwerken: analog und digital. Analoge Netzwerke wurden für die Übertragung von Sprache entwickelt. Über viele Jahre war das PSTN rein analog. Doch heutzutage haben leitungsvermittelte Netzwerke wie das PSTN den Übergang von der analogen zur Digitaltechnik vollzogen. Um ein analoges Sprachübertragungssignal über ein digitales Netzwerk zu unterstützen, muss das analoge Übertragungssignal in ein digitales Format codiert oder umgewandelt werden, bevor es in das Telefon-WAN eingespeist wird. Am Empfangsende der Verbindung muss dieses digitale Signal dann wieder in ein analoges Signalformat decodiert oder rückgewandelt werden.

Leitungsvermittelte Netzwerke haben Vor- und Nachteile: Die Nachteile überwiegen bei leitungsvermittelten Netzwerken. Leitungsvermittelte Netzwerke können relativ ineffizient sein, weil Bandbreite ungenutzt bleibt. Dies ist nicht der Fall, wenn VoIP in einem paketvermittelten Netzwerk verwendet wird. VoIP nutzt die verfügbare Bandbreite zusammen mit allen anderen Netzwerkanwendungen, wodurch die verfügbare Bandbreite wesentlich effizienter ausgelastet wird. Ein weiterer Nachteil von leitungsvermittelten Netzwerken ist, dass Kapazitäten für die maximale Anzahl von Telefonaten vorgehalten werden müssen, die möglicherweise zu Spitzennutzungszeiten benötigt werden. Für die Nutzung der Leitung bzw. Leitungen zur Abdeckung der potenziellen Maximalzahl von Anrufen fallen zusätzliche Kosten an.

Leitungsvermittlung hat gegenüber paketvermittelten Netzwerken einen großen Vorteil. In einem leitungsvermittelten Netzwerk steht Ihnen bei Verwendung einer Leitung die gesamte Leitung während des Nutzungszeitraums zur Verfügung, ohne dass Sie sie mit anderen Benutzern teilen müssten. Dies ist in paketvermittelten Netzwerken nicht der Fall.


> [!NOTE]
> SDH (Synchronous Digital Hierarchy) ist mittlerweile in den meisten PSTN-Netzwerken das primäre Übertragungsprotokoll. SDH wird über Glasfaserkabelnetzwerke übertragen.



Übersicht

## Paketvermittelte Netzwerke

Paketvermittlung ist ein Verfahren, bei dem eine Datennachricht in kleinere Einheiten aufgeteilt wird, die als Pakete bezeichnet werden. Pakete werden über die beste verfügbare Route an ihr Ziel gesendet, wo sie dann beim Empfänger wieder zusammengesetzt werden.

In paketvermittelten Netzwerken wie dem Internet werden Pakete über die zweckmäßigste Route an ihr Ziel geleitet, wobei aber nicht alle Pakete zwischen zwei Hosts dieselbe Route nehmen, auch nicht, wenn sie von einer einzigen Nachricht stammen. Bei dieser Vorgehensweise kann man davon ausgehen, dass die Pakete zu unterschiedlichen Zeiten und nicht in der richtigen Reihenfolge ankommen. In einem paketvermittelten Netzwerk werden Pakete (Nachrichten oder Fragmente von Nachrichten) einzeln zwischen Knoten über Datenverbindungen geroutet, die für andere Knoten freigegeben werden können. Bei der Paketvermittlung wird die verfügbare Bandbreite im Gegensatz zur Leitungsvermittlung für mehrere Verbindungen mit Knoten im Netzwerk freigegeben.


> [!NOTE]
> Bei der Leitungsvermittlung erreichen den Empfänger alle Pakete in der richtigen Reihenfolge und entlang einer einzigen Route.



Paketvermittelte Netzwerke ermöglichen weltweit die Datenkommunikation im Internet. Ein öffentliches Daten- oder paketvermitteltes Netzwerk ist das datenbasierte Gegenstück zum PSTN.

Paketvermittelte Netzwerke findet man auch in Netzwerkumgebungen wie LANs (Local Area Network) und WANs (Wide Area Network). Eine paketvermittelte WAN-Umgebung ist von Telefonleitungen abhängig, wobei die Leitungen aber so angeordnet sind, dass zwischen den Endpunkten eine ununterbrochene Verbindung aufrechterhalten wird. In einer paketvermittelten LAN-Umgebung, wie z. B. einem Ethernet-Netzwerk, erfolgt die Übermittlung der Datenpakete mithilfe von Paketswitches, -routern und LAN-Kabeln. In einem LAN stellt der Switch eine Verbindung zwischen zwei Segmenten her, die gerade lang genug sind, um das aktuelle Paket zu senden. Eingehende Pakete werden in einem temporären Speicherbereich oder in einem Puffer des Arbeitsspeichers abgelegt. In einem Ethernet-LAN enthält ein Ethernet-Frame die Nutzlast bzw. den Datenteil des Pakets sowie eine spezielle Kopfzeile, in der die MAC-Adressinformationen (Medienzugriffssteuerung, Media Access Control) der Quelle und des Ziels des Pakets enthalten sind. Wenn die Pakete an ihrem Ziel ankommen, werden sie von einem Modul zum Zusammensetzen der Pakete (Packet Assembler) wieder in die richtige Reihenfolge gebracht. Ein Packet Assembler ist wegen der potenziell unterschiedlichen Routen der Pakete erforderlich.

Paketvermittelte Netzwerke haben das Internet erst möglich und gleichzeitig Datennetzwerke, insbesondere LAN-basierte IP-Netzwerke, in höherem Maße verfügbar und stärker verbreitet gemacht.

Übersicht

## PBX-Anlagen

Eine Legacy-PBX-Anlage ist ein Telefoniegerät, das in einem Telefonie- oder leitungsvermittelten Netzwerk als Vermittlungsstelle für Anrufe fungiert.


> [!NOTE]
> Bei einer Legacy-PBX-Anlage handelt es sich um eine PBX-Anlage, die keine IP-Pakete vermitteln kann. In vielen Unternehmen wurden mittlerweile Legacy-PBX-Anlagen durch IP-PBX-Anlagen ersetzt.



Eine PBX-Anlage ist ein Telefoniegerät, das von den meisten mittleren und größeren Unternehmen verwendet wird. Eine PBX-Anlage ermöglicht den Benutzern bzw. Teilnehmern der Anlage die gemeinsame Nutzung einer bestimmten Anzahl von "Amtsleitungen" für Telefonanrufe, die von der PBX-Anlage als extern eingestuft werden. Eine PBX-Anlage stellt eine wesentlich kostengünstigere Lösung dar als die Bereitstellung einer dedizierten "Amtsleitung" für jeden Mitarbeiter eines Unternehmens. An eine PBX-Anlage können neben Telefonapparaten auch Faxgeräte, Modems und viele andere Kommunikationsgeräte angeschlossen werden.

Die physische PBX-Anlage wird normalerweise im Gebäude eines Unternehmens installiert, wo sie dann Anrufe zwischen den Telefonapparaten verbindet, die in den einzelnen Räumlichkeiten des Unternehmens aufgestellt und angeschlossen sind. Normalerweise steht eine begrenzte Anzahl von externen Leitungen, auch als Amts- oder Fernleitungen bekannt, für eingehende und ausgehende Anrufe zur Verfügung, die außerhalb des Unternehmens liegen, also von einer externen Quelle wie dem PSTN stammen.

Anrufe aus dem Unternehmen heraus an externe Rufnummern werden bei Verwendung einer PBX-Anlage bei manchen Systemen durch Vorwählen einer 9 oder 0 vor der externen Rufnummer hergestellt. Für die Herstellung der Verbindung wird automatisch eine abgehende Amtsleitung gewählt. Umgekehrt erfordern Telefonate zwischen Benutzern innerhalb des Unternehmens nicht notwendigerweise das Vorwählen einer bestimmten Zahl oder die Verwendung einer (externen) Amtsleitung. Der Grund hierfür ist, dass interne Telefonate von der PBX-Anlage zwischen den Telefonapparaten, die physisch an die PBX-Anlage angeschlossen sind, weitergeleitet bzw. vermittelt werden.

In mittleren bis größeren Unternehmen sind folgende PBX-Anlagenkonfigurationen möglich:

  - Eine einzelne PBX-Anlage, die das gesamte Unternehmen versorgt.

  - Eine Gruppe aus mindestens zwei PBX-Anlagen, die untereinander nicht vernetzt oder verbunden sind.

  - Eine Gruppe aus mindestens zwei PBX-Anlagen, die untereinander vernetzt oder verbunden sind.


> [!NOTE]
> Ein Exchange 2013 UM-Wählplan kann mehr als eine PBX-Anlage oder IP-PBX-Anlage umfassen.



Übersicht

## IP-PBX-Anlagen

Eine IP-PBX-Anlage ist eine PBX-Anlage, die das Internetprotokoll (Internet Protocol, IP) unterstützt, um Telefonapparate über ein Ethernet- oder paketvermitteltes LAN zu verbinden, und Sprachdaten in IP-Paketen übermittelt. Eine hybride IP-PBX-Anlage unterstützt das IP zum Senden von Sprache in Paketen, verbindet aber auch konventionelle, leitungsvermittelte TDM-Analog- und Digitaltelefone (Time Division Multiplex). Eine IP-PBX-Anlage gehört zu den Telefonvermittlungsgeräten, die im Gebäude des Unternehmens untergebracht sind, nicht bei einer Telefongesellschaft.

IP-PBX-Anlagen sind häufig einfacher zu verwalten als Legacy-PBX-Anlagen, weil Administratoren die IP-PBX-Dienste einfach über einen Internetbrowser oder ein anderes IP-basiertes Dienstprogramm konfigurieren können. Darüber hinaus sind keine zusätzlichen Verdrahtungen erforderlich, und auch das Legen von Kabeln oder das Montieren von Patchpanels (Schaltfeldern) ist überflüssig. Bei einer IP-PBX-Anlage ist das räumliche Verlegen eines IP-basierten Telefonapparats so einfach wie das Ausstecken eines Telefons an der einen und das Einstecken des Apparats an einer anderen Stelle. So entfallen kostspielige Kundendiensttelefonate, um ein Telefon von Legacy-PBX-Anlagenherstellern zu verlegen. Darüber hinaus entfallen bei Unternehmen mit einer IP-PBX-Anlage die zusätzlichen Infrastrukturkosten, die für die Wartung und Verwaltung von zwei getrennten leitungs- und paketvermittelten Netzwerken entstehen.

## SIP-aktivierte PBX-Anlagen

Eine SIP-aktivierte PBX-Anlage ist ein Telefoniegerät, das in einem Telefonie- oder leitungsvermittelten Netzwerk als Vermittlungsstelle für Anrufe fungiert. Der Unterschied zwischen einer SIP-aktivierten PBX-Anlage und einer herkömmlichen PBX-Anlage ist allerdings, dass die SIP-aktivierte PBX-Anlage eine Verbindung zum Internet herstellen und Anrufe über das Internet mithilfe des SIP-Protokolls tätigen kann.

SIP-aktivierte PBX-Anlagen verwenden ein Format für Anrufe, das ein SIP-URI umfasst, das eine globale E.164-Nummer und den "user=phone"-Parameter enthält. Beispiel: sip:+14255551234@contoso.com;user=phone

Die E.164-Nummer beginnt mit einem "+" und enthält keinen Telefon-Kontext-Parameter und keine Trennzeichen. SIP-aktivierte PBX-Anlagen unterstützen sowohl TCP als auch UDP. UDP ist bei älteren Systemen nach wie vor weit verbreitet. SIP-aktivierte PBX-Anlagen unterstützen auch MTLS (Mutual Transport Layer Security) und DNS-Suchen.

## VoIP

Voice over Internet Protocol (VoIP) ist eine Technologie, die Hardware- und Softwarekomponenten umfasst, die es ermöglichen, ein IP-basiertes Netzwerk als Übertragungsmedium für Telefonate zu verwenden. Bei VoIP werden Sprachdaten in Paketen über das Internetprotokoll (IP) gesendet, statt über konventionelle Leitungsübertragungen bzw. über leitungsvermittelte Telefonleitungen des PSTN. Ein VoIP-Gateway, der an Ihr IP-Netzwerk angeschlossen wird, verwendet VoIP-Protokolle zum Senden von Sprachdatenpaketen zwischen Exchange 2013-Clientzugriffsservern und -Postfachservern und einem PBX-System.

## VoIP-Gateways

Ein VoIP-Gateway ist ein Hardwaregerät oder -produkt eines Drittanbieters, das eine ältere PBX-Anlage mit Ihrem LAN verbindet. Der VoIP-Gateway erlaubt die Kommunikation zwischen dem PBX-System und Ihren Exchange 2013-Postfachservern und -Clientzugriffsservern, welche die Microsoft Exchange Unified Messaging- und Unified Messaging Call Router-Dienste ausführen.


> [!NOTE]
> Der VoIP-Gateway kann ebenfalls an PBX-Systeme angeschlossen werden, die anstelle leitungsvermittelter PSTN-Protokolle VoIP verwenden.



Exchange 2013 Unified Messaging basiert auf der Fähigkeit des VoIP-Gateways, TDM-Protokolle oder leitungsvermittelte Telefonieprotokolle, wie etwa ISDN (Integrated Services Digital Network) oder QSIG, von einer PBX-Anlage (Private Branch eXchange) in VoIP- oder IP-basierte Protokolle, wie etwa SIP (Session Initiation Protocol), RTP (Realtime Transport Protocol) oder T.38 für die Faxübermittlung in Echtzeit, zu übersetzen bzw. darin umzuwandeln. Das VoIP-Gateway ist ein integraler Bestandteil und Voraussetzung für die Funktionalität und den Betrieb von Unified Messaging.


> [!IMPORTANT]
> Nach der Installation des VoIP-Gateways, einer IP-Nebenstellenanlage oder einer SIP-aktivierten PBX-Anlage müssen Sie ein UM-IP-Gateway erstellen, welches das physische Gerät repräsentiert. Nach der Erstellung eines UM-IP-Gateways senden die Clientzugriffs- und Postfachserver, die dem UM-IP-Gateway zugeordnet sind, eine SIP OPTIONS-Anforderung an das VoIP-Gateway, die IP-Nebenstellenanlage oder die SIP-aktivierte PBX-Anlage, um sicherzustellen, dass die jeweilige Komponente reagiert. Wenn das VoIP-Gateway nicht auf die SIP OPTIONS-Anforderung des Postfachservers reagiert, protokolliert der Postfachserver ein Ereignis mit der ID&nbsp;1088, das besagt, dass diese Anforderung fehlerhaft verlaufen ist. Stellen Sie zum Beheben dieses Problems sicher, dass der VoIP-Gateway, die IP-Nebenstellenanlage oder die SIP-aktivierte PBX-Anlage verfügbar und online ist und die Unified Messaging-Konfiguration auf dem Clientzugriffs- und dem Postfachserver korrekt ist.



Weitere Informationen zu IP-PBX- und PBX-Konfigurationen finden Sie unter [PBX- und IP-PBX-Konfigurationen](pbx-and-ip-pbx-configurations-exchange-2013-help.md).

Übersicht

## Weitere Informationen

[UM-Protokolle, Ports und Dienste](um-protocols-ports-and-services-exchange-2013-help.md)

[Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013)

