---
title: 'PBX- und IP-PBX-Konfigurationen: Exchange 2013 Help'
TOCTitle: PBX- und IP-PBX-Konfigurationen
ms:assetid: fb086680-6e3e-477a-a5d8-e24ca30196ee
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb430797(v=EXCHG.150)
ms:contentKeyID: 54652714
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# PBX- und IP-PBX-Konfigurationen

 

_**Gilt für:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Immer mehr Organisationen erwerben, installieren und verwalten die Hardwarekomponenten, die zur Unterstützung eigener Telefoniesysteme erforderlich sind, z. B. PBX-Anlagen (Private Branch eXchange) oder IP-PBX-Anlagen. Vielfach verfolgen Organisationen mit dem Erwerb einer eigenen Telefonieausrüstung und der entsprechenden Schulung ihrer Mitarbeiter das Ziel, die mit der Verwaltung des Telefonsystems verbundenen Kosten zu senken und mehr Einfluss auf die bereitgestellten Telefoniefunktionen zu nehmen.

Damit eine Organisation ein eigenes Telefonienetzwerk unterhalten kann, muss sie die dafür erforderlichen Hardwarekomponenten erwerben. Zusätzlich müssen die routinemäßige Verwaltung der Telefonieausrüstung und die Schulung der dafür zuständigen Mitarbeiter bedacht werden. In diesem Thema werden die unterschiedlichen Arten von Unternehmens- oder Organisationssystemen für die Telefonie sowie die jeweils erforderlichen Hardwarekomponenten behandelt. Außerdem umfasst das Thema Beispiele für die verschiedenen Arten an Telefoniekonfigurationen.


> [!IMPORTANT]
> Es wird allen Kunden, die eine Bereitstellung von Exchange 2013&nbsp;Unified Messaging planen, empfohlen, einen UM-Spezialisten zu Rate zu ziehen. Auf diese Weise wird ein reibungsloses Upgrade von einem Vorgänger-Voicemailsystem sichergestellt. Für die Implementierung einer neuen UM-Bereitstellung oder die Durchführung eines Upgrades von einem vorhandenen Voicemailsystem sind umfassende Kenntnisse von PBX- und IP-PBX-Anlagen sowie Unified Messaging erforderlich. Weitere Informationen zu Ansprechpartnern finden Sie auf der Website <A href="https://go.microsoft.com/fwlink/p/?linkid=261951">Microsoft PinPoint</A>.



**Inhalt**

Übersicht über Telefoniesysteme

Konfigurationen von Legacy-PBX-Anlagen bzw. traditionellen PBX-Anlagen

IP-PBX-Konfigurationen

Identifikation des anrufenden oder angerufenen Teilnehmers

## Übersicht über Telefoniesysteme

In leitungsvermittelten Netzwerken, wie z. B. dem Public Switched Telephone Network (Internationales Analogtelefonsystem, PSTN), werden mehrere Anrufe über dasselbe Übertragungsmedium übermittelt. Häufig handelt es sich bei dem im PSTN verwendeten Medium um Kupferkabel. Es können aber auch Glasfaserkabel verwendet werden.

Ein leitungsvermitteltes Netzwerk ist ein Netzwerk, in dem eine dedizierte Verbindung besteht. Eine dedizierte Verbindung ist ein Schaltkreis oder eine Leitung, der bzw. die zwischen zwei Knoten eingerichtet wird, um diesen die Kommunikation untereinander zu ermöglichen. Nachdem ein Anruf zwischen zwei Knoten aufgebaut wurde, kann die Verbindung nur von diesen beiden Knoten verwendet werden. Wenn der Anruf von einem der beiden Knoten beendet wird, wird auch die Verbindung unterbrochen.

In Unternehmen und Organisationen werden unterschiedliche Typen oder Kategorien von Telefonsystemen eingesetzt, u. a. leitungsvermittelte Netzwerke, IP-basierte Netzwerke oder beide. Jeder Typ von Telefonsystem weist besondere Vor- und Nachteile auf, die bei der Planung und Implementierung eines Telefonsystems berücksichtigt werden sollten.

  - **Centrex:**  Centrex ist ein Telefondienst, den Telefongesellschaften Unternehmen und Organisationen gegen Entgelt zur Verfügung stellen. Wenn sich ein Unternehmen oder eine Organisation für ein konventionelles Centrex-Telefonsystem entscheidet, entfällt der Kauf der Telefoniehardware, die am Standort der Organisation für das Telefonsystem verwendet wird. Üblicherweise werden Centrex-Systeme von kleinen Unternehmen verwendet, die Centrex-Dienste von einer Telefongesellschaft pro Leitung und Monat mieten. Mitunter werden Centrex-Telefonsysteme auch von größeren Organisationen eingesetzt, am häufigsten finden sie sich jedoch in Behörden, öffentlichen Einrichtungen und privaten Organisationen. Bei Centrex werden für die Verbindungen mit einem Unternehmen oder einer Organisation häufig analoge Telefonleitungen verwendet. Es können jedoch auch T1-Leitungen verwendet werden, wobei vor Ort ein Demultiplexer erforderlich ist, um analoge und digitale Telefone oder ISDN-Leitungen zu unterstützen.
    
    In einem Centrex-Telefonsystem fungiert die Zentrale der Telefongesellschaft als Vermittlungsstelle. Centrex ist speziell auf die Anforderungen einer bestimmten Organisation abgestimmt. Die Telefonzentrale leitet die ausgehenden Anrufe, die im Unternehmen getätigt werden, an die entsprechende interne oder externe Telefonnummer weiter. Bei Centrex werden interne Anrufe über die zentrale Vermittlungsstelle der Telefongesellschaft an eine Durchwahl zurückgeleitet. Mit Centrex erkennt die Vermittlungsstelle bzw. die Zentrale der Telefongesellschaft, welche Durchwahlnummern intern sind. Daher kann ein Mitarbeiter im Telefonienetzwerk einer Organisation einen anderen Mitarbeiter im gleichen Telefonienetzwerk oder mit denselben Wähleinstellungen unter einer vierstelligen Durchwahl erreichen. Wenn eine interne Durchwahl gewählt wird, wird der Anruf an die Zentrale der Telefongesellschaft weitergeleitet und von dort zurück an die Durchwahl geleitet, deren Nummer gewählt wurde.

Eine Variante des herkömmlichen Centrex-Telefonsystems wird als *IP-Centrex* bezeichnet. In einem IP-Centrex-Telefonsystem wird ein Anruf über ein VoIP-Gateway (Voice over IP) gesendet, das sich in der Zentrale einer Telefongesellschaft oder am Standort eines Dienstanbieters befindet. In einem Telefonsystem dieses Typs übersetzt das VoIP-Gateway einen Anruf in IP-Datenpakete, die über das Internet oder über ein VoIP-Netzwerk gesendet werden können. Ein Anruf, der über das Internet gesendet wird, wird hingegen normalerweise von einem anderen VoIP-Gateway empfangen, das ihn zurück in einen herkömmlichen leitungsvermittelten Anruf übersetzt.

Organisationen, die derzeit mit einem konventionellen Centrex-Telefonsystem arbeiten, müssen mindestens ein VoIP-Gateway installieren, bereitstellen und verwalten, um die ordnungsgemäße Funktion von Unified Messaging sicherzustellen. Damit Unified Messaging mit IP-Centrex eingesetzt werden kann, müssen unter Umständen VoIP-Gateways installiert, bereitgestellt und verwaltet werden. Ob ein VoIP-Gateway erforderlich ist, lässt sich anhand verschiedener Variablen ermitteln. Dazu zählen die in der Organisation verwendeten Telefontypen (analog, digital oder IP) sowie die vom IP-Centrex-System unterstützten Protokolle.

  - **Bürotelefonanlage:**  Bei einer Bürotelefonanlage ist die Zentrale der Telefongesellschaft über standardmäßige analoge oder digitale Telefonleitungen mit der Organisation verbunden. Eine einzelne Telefondurchwahl ist mit mehreren Telefonen verbunden, sodass bei einem Anruf, der unter dieser Telefonnummer bei der Organisation eingeht, alle dieser Leitung bzw. Durchwahl zugeordneten Telefone gleichzeitig klingeln.

Bei einer Bürotelefonanlage werden die gleichen Leitungen von mehreren Einzelbenutzern telefonübergreifend genutzt. Aus diesem Grund ist der Anschluss der Organisation nicht fortlaufend besetzt. Bürotelefonanlagen werden üblicherweise von kleinen Unternehmen eingesetzt, in denen das Aufkommen interner Anrufe hoch, das Aufkommen externer Anrufe dagegen gering ist.

Im Laufe der Zeit sind Bürotelefonanlagen immer weiter entwickelt worden, und sie können mit Unified Messaging eingesetzt werden, wenn ein VoIP-Gateway hinzugefügt wird. Allerdings gibt es auch weniger ausgereifte Systeme, die selbst mit einem unterstützten VoIP-Gateway hierfür nicht verwendet werden können.

  - **PBX-Anlage:**  Eine Legacy-PBX-Anlage ist ein Telefoniegerät, das als Vermittlungsstelle für Anrufe in einem Telefonie- oder leitungsvermittelten Netzwerk dient. Als Legacy-PBX-Anlage wird eine PBX-Anlage bezeichnet, die nicht über eine Netzwerkkarte verfügt und daher keine IP-Pakete vermitteln kann. Da PBX-Anlagen der Vorgängerversion keine IP-Pakete vermitteln können, haben manche Unternehmen und Organisationen diese durch IP-PBX-Anlagen ersetzt. Eine Liste der von Unified Messaging unterstützten PBX-Anlagen finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).
    
    PBX-Anlagen werden von den meisten mittleren und größeren Unternehmen verwendet. Eine PBX-Anlage ermöglicht den Benutzern bzw. Teilnehmern der Anlage die gemeinsame Nutzung einer bestimmten Anzahl von "Amtsleitungen" für Telefonanrufe, die von der PBX-Anlage als extern eingestuft werden. Eine PBX-Anlage stellt eine wesentlich kostengünstigere Lösung dar als die Bereitstellung einer dedizierten "Amtsleitung" für jeden Mitarbeiter eines Unternehmens. An eine PBX-Anlage können neben Telefonen auch Faxgeräte, Modems und viele andere Kommunikationsgeräte angeschlossen werden.
    
    Die PBX-Anlage wird normalerweise im Gebäude einer Organisation installiert, aus dem sie dann Anrufe zwischen den Telefonen, die in den Räumlichkeiten des Unternehmens aufgestellt sind, und der Telefongesellschaft verbindet. Normalerweise steht eine begrenzte Anzahl von externen Leitungen, auch als Amts- oder Fernleitungen bekannt, für eingehende und ausgehende Anrufe zur Verfügung, die außerhalb des Unternehmens liegen, also von einer externen Quelle wie dem PSTN stammen.
    
    Wenn Sie eine Legacy-PBX-Anlage mit Unified Messaging verwenden möchten, müssen Sie ein unterstütztes VoIP-Gateway bereitstellen. Eine Liste der unterstützten VoIP-Gateways finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).

  - **IP-PBX-Anlage:**  Eine IP-PBX-Anlage ist eine PBX-Anlage, die mit einer Netzwerkkarte ausgestattet ist, die das Internetprotokoll (Internet Protocol, IP) unterstützt. Ein solches Telefonvermittlungsgerät ist normalerweise im Gebäude einer Organisation oder eines Unternehmens untergebracht, nicht bei einer Telefongesellschaft. Es gibt zwei Arten von IP-PBX-Anlagen: konventionelle IP-PBX-Anlagen und IP-PBX-Hybridanlagen. Sowohl konventionelle IP-PBX-Anlagen als auch IP-PBX-Hybridanlagen unterstützen IP zum Übermitteln von Sprachdaten in Paketen an VoIP-Telefone. Allerdings verbinden IP-PBX-Hybridanlagen zusätzlich herkömmliche analoge und digitale Telefone.
    
    IP-PBX-Anlagen sind häufig einfacher zu verwalten als Legacy-PBX-Anlagen, weil Administratoren die IP-PBX-Dienste einfach über einen Internetbrowser oder ein anderes IP-basiertes Tool konfigurieren können. Darüber hinaus sind keine zusätzlichen Verdrahtungen erforderlich, und auch das Legen von Kabeln oder das Montieren von Patchpanels (Schaltfeldern) ist überflüssig. Bei einer IP-PBX-Anlage können Sie ein IP-basiertes Telefon ganz einfach räumlich verlegen, indem Sie das Telefon an der einen Stelle ausstecken und an einer anderen Stelle wieder einstecken. So entfallen kostspielige Kundendiensttelefonate, die zum Verlegen eines Telefons von Legacy-PBX-Anlagen erforderlich sind. Darüber hinaus entfallen bei Organisationen mit einer IP-PBX-Anlage die zusätzlichen Infrastrukturkosten, die für die Wartung und Verwaltung getrennter leitungs- und paketvermittelter Netzwerke entstehen. Eine Liste der für Unified Messaging unterstützten IP-PBX-Anlagen finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).
    
    Zurück zum Seitenanfang

## Konfigurationen von Legacy-PBX-Anlagen bzw. traditionellen PBX-Anlagen

In Telefonienetzwerken mit Legacy-PBX-Anlagen bzw. traditionellen PBX-Anlagen erfüllt die PBX-Anlage folgende Aufgaben:

  - Erstellen von Verbindungen zwischen den Telefonapparaten zweier Benutzer.

  - Aufrechterhalten der Verbindung, solange die Benutzer diese benötigen.

  - Bereitstellen von Informationen für die Abrechnung (z. B. Erfassen der Gesprächsdauer).

Zusätzlich zu den oben genannten drei Funktionen stellt eine PBX-Anlage möglicherweise weitere Anruffunktionen bereit, z. B. die folgenden:

  - Automatische Telefonzentralen

  - Abrechnen von Anrufen

  - Anrufannahme

  - Anrufübergabe

  - Anklopffunktion

  - Konferenzgespräche

  - DID (Direct Inward Dialing, Direktwahl nach innen)

  - DND (Do Not Disturb, Bitte nicht stören)

PBX-Anlagen werden zwar von verschiedenen Herstellern angeboten, doch lassen sie sich in zwei grundlegende Kategorien unterteilen: analog und digital. Diese Typen von PBX-Anlagen werden häufig als *Legacy-PBX-Anlagen* oder *traditionelle PBX-Anlagen* bezeichnet.

Üblicherweise sind PBX-Systeme über spezielle Telefonleitungen, die als T1- und E1-Leitungen bezeichnet werden, mit der Zentrale der Telefongesellschaft verbunden. T1- und E1-Leitungen weisen mehrere Kanäle auf. Diese Telefonleitungen werden auch als *Amtsleitungen* bezeichnet. Die Zentrale oder die PBX-Anlage kann über dieselbe Amtsleitung mehrere Anrufe gleichzeitig übermitteln, wodurch mit einer vereinfachten Verdrahtung eine höhere Effizienz erzielt wird. Auch mit Analog- oder ISDN-Leitungen kann eine PBX-Anlage eingesetzt werden.

Mit der richtigen Konfiguration der PBX-Anlage können Sie steuern, wie viele Kanäle bzw. Leitungen für den Empfang externer Anrufe konfiguriert werden und wie viele Kanäle bzw. Leitungen Anrufen vorbehalten sein sollen, die von Benutzern innerhalb der Organisation getätigt werden. Durch die Konfiguration der Anzahl von Kanälen bzw. Leitungen können Sie Besetztsignale vermeiden und festlegen, wie viele Kanäle bzw. Leitungen für Anwendungen wie Callcenter reserviert werden können. Die richtige Konfiguration der PBX-Anlage hilft Ihnen, bei der Verwaltung der Kanäle bzw. Leitungen in der Organisation Kosten zu sparen, denn die Anzahl der benötigten Mietleitungen wird reduziert.

Über eine PBX-Anlage kann ein Anruf unter einer bestimmten angewählten Telefonnummer an ein bestimmtes Telefon weitergeleitet werden, sodass jedem Benutzer eine eigene Telefonnummer oder Durchwahl zugeordnet werden kann. Eine solche Nummer wird als DID-Nummer (Direct Inward Dialing, Direktwahl nach innen) bezeichnet. Wenn die Telefonnummer eines Benutzers gewählt wird, sendet die Telefongesellschaft die DID-Nummer über DNIS (Dialed Number Identification Service, Zielrufnummererkennung) an die PBX-Anlage. Da die Telefongesellschaft zum Übermitteln der Nummer DNIS verwendet, ist keine Telefonvermittlung erforderlich, um den Anruf weiterzuleiten. Die PBX-Anlage verfügt über die Anrufinformationen, die erforderlich sind, um den Anruf an die richtige angewählte Nummer weiterzuleiten. Eine Liste der von Unified Messaging unterstützten PBX-Anlagen finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).

Zurück zum Seitenanfang

## Analoge und digitale PBX-Anlagen

Analoge PBX-Anlagen übermitteln Sprach- und Anrufsignalinformationen, z. B. die Wähltöne einer gewählten Telefonnummer, als analoge Audiodaten. Die Audiodaten werden also nie digitalisiert. Damit ein Anruf richtig weitergeleitet werden kann, müssen die PBX-Anlage und die Zentrale der Telefongesellschaft die Signalinformationen abhören.


> [!NOTE]
> Der technische Fachbegriff für die Tonwahl ist DTMF (Dual Tone Multi-Frequency, Mehrfrequenzwahlverfahren). Wenn ein Anrufer eine Taste auf der Telefontastatur drückt, werden zwei verschiedene Töne erzeugt, nämlich einer mit hoher und einer mit niedriger Frequenz. Wenn eine Person in das Telefon spricht, wird nur ein einzelner Ton bzw. eine einzelne Frequenz erzeugt. Dadurch, dass gleichzeitig zwei Töne mit unterschiedlichen Frequenzen übermittelt werden, wird das Risiko verringert, dass die Signaltöne als menschliche Stimme interpretiert werden oder umgekehrt eine menschliche Stimme als Signaltöne interpretiert wird.



Digitale PBX-Anlagen codieren die analogen Audiodaten im digitalen Format, d. h., sie digitalisieren sie. Üblicherweise werden dabei die Sprachdaten mit einem Audiocodec nach dem Industriestandard, z. B. G.711 oder G.729, codiert. Nach dem Codieren werden die digitalisierten Sprachdaten mithilfe der Leitungsvermittlung über einen Kanal übermittelt. Bei der Leitungsvermittlung wird eine offene End-to-End-Verbindung eingerichtet. Durch diese wird der Kanal über die Dauer des Anrufs exklusiv für den Anrufer offen gehalten. Die von der PBX-Anlage jeweils verwendete Signalmethode ist jedoch von Hersteller zu Hersteller verschieden. Unter Umständen verfügen die Hersteller von PBX-Anlagen über proprietäre Signalmethoden für die Anrufeinrichtung.


> [!NOTE]
> Digitale PBX-Anlagen können sowohl digitale als auch analoge Amtsleitungen unterstützen.



In größeren Organisationen ist es mit PBX-Anlagen möglich, dass Mitarbeiter an unterschiedlichen Standorten einfach eine Durchwahl wählen, um miteinander in Kontakt zu treten. Dies lässt sich mit einer einzigen PBX-Anlage oder mit mehreren untereinander vernetzten PBX-Anlagen bewerkstelligen. PBX-Anlagen an unterschiedlichen Standorten können über T1- oder E1-Leitungen mit einem einzigen transparenten, leitungsvermittelten Netzwerk verbunden werden. Leitungen, die PBX-Anlagen miteinander verbinden, werden auch als *Querverbindungen* bezeichnet. Über diese Querverbindungen kommunizieren die PBX-Anlagen mittels eines PBX-zu-PBX-Protokolls wie QSIG miteinander. Mit QSIG kann sich eine Gruppe von PBX-Anlagen wie eine einzige PBX-Anlage verhalten.

In einer PBX-Umgebung dieser Art können auch erweiterte Funktionen bereitgestellt werden, z. B. Anrufübergabe und Konferenzgespräche. Neben der Unterstützung erweiterter Funktionen bieten zwei miteinander verbundene PBX-Anlagen einer Organisation auch die Möglichkeit, Kosten einzusparen, da weniger Gebühren für Ferngespräche zwischen Mitarbeitern an unterschiedlichen Standorten anfallen. Eine Telefongespräch zwischen zwei Mitarbeitern wird nämlich über eine Querverbindung zwischen den PBX-Anlagen geführt. Statt ein Ferngespräch zu führen, muss der Anrufer lediglich eine Durchwahl wählen, um den gewünschten Gesprächspartner zu erreichen.

In einer Telefonieumgebung mit mindestens einer analogen oder digitalen PBX-Anlage ist ein VoIP-Gateway zwischen der PBX-Anlage und den Exchange 2013-Clientzugriffs- und Postfachservern erforderlich, um die leitungsvermittelten Protokolle eines Telefonienetzwerks in die IP-basierten Protokolle eines Datennetzwerks zu konvertieren. Weitere Informationen zu VoIP-Gateways finden Sie unter den folgenden Themen:

  - [UM-IP-Gateways](um-ip-gateways-exchange-2013-help.md)

  - [Anschließen eines VoIP-Gateways zur Kommunikation mit einer Nebenstellenanlage](connect-a-voip-gateway-to-communicate-with-a-pbx-exchange-2013-help.md)

Eine Liste der für Unified Messaging unterstützten VoIP-Gateways finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).

Zurück zum Seitenanfang

## IP-PBX-Konfigurationen

Eine IP-PBX-Anlage ist eine PBX-Anlage, die das Internetprotokoll (Internet Protocol, IP) unterstützt und Telefone über ein Ethernet- oder paketvermitteltes LAN miteinander verbindet. Sprachdaten werden von einer solchen Anlage in IP- oder Datenpaketen übermittelt. Eine IP-PBX-Anlage kann über mehrere Schnittstellen verfügen. Dazu zählen Schnittstellen für ein Datennetzwerk und andere Schnittstellen, die eine Verbindung mit einem Telefonie- oder leitungsvermittelten Netzwerk ermöglichen.

Dank der Entwicklung von Echtzeitinternetprotokollen ist es möglich, Sprach- und Faxnachrichten erfolgreich über ein Datennetzwerk zu übermitteln. Zu diesen Echtzeitinternetprotokollen zählen die mit Unified Messaging verwendeten VoIP-Protokolle: Session Initiation Protocol (SIP) über Transmission Control Protocol (TCP) für Voicemessaging. Diese Protokolle haben die erfolgreiche Übermittlung von Sprach- und Faxnachrichten über ein Datennetzwerk möglich gemacht. VoIP-Echtzeitprotokolle sind zum Senden von Sprachnachrichten über ein paketvermitteltes Netzwerk oder ein Datennetzwerk erforderlich, damit die Zustellungsreihenfolge und die zeitliche Abfolge von Datenpaketen beibehalten und gesteuert werden kann. Würden diese Protokolle nicht zur Verwaltung und Steuerung der Zustellungsreihenfolge und -zeit der Datenpakete eingesetzt, würde die menschliche Stimme zerlegt und daher unzusammenhängend klingen, oder Bilder würden verzerrt dargestellt. Eine Liste der für Unified Messaging unterstützten IP-PBX-Anlagen finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).


> [!NOTE]
> Unified Messaging unterstützt nur SIP über TCP.



## Traditionelle IP-PBX-Konfigurationen

Eine standardmäßige oder traditionelle IP-PBX-Anlage enthält mindestens eine einzelne Netzwerkschnittstelle, über die mittels VoIP-Protokollen eine Verbindung mit einem Datennetzwerk hergestellt wird. Darüber hinaus kann sie weitere Netzwerkschnittstellen oder andere Telefonieschnittstellen umfassen, über die eine Verbindung mit einem vorhandenen Telefonienetzwerk wie dem PSTN hergestellt werden kann. Über die Verbindung mit dem Datennetzwerk ist eine Kommunikation mit anderen VoIP-Hosts im Datennetzwerk mithilfe von IP-Datenpaketen möglich. Zu diesen VoIP-Hosts zählen andere IP-PBX-Anlagen, VoIP-Telefone, IP-Gateways und Clientzugriffs- und Postfachserver, die UM-Dienste ausführen. Eine traditionelle IP-PBX-Anlage unterstützt keine analogen oder digitalen Telefone, sondern ausschließlich VoIP-Telefone.

Da die IP-PBX-Anlage bereits eine Verbindung mit einem Datennetzwerk herstellen und die leitungsvermittelten Protokolle aus dem PSTN in paketvermittelte VoIP-Protokolle konvertieren kann, ist möglicherweise kein VoIP-Gateway für die Kommunikation mit Clientzugriffs- und Postfachservern im Datennetzwerk erforderlich.

## IP-PBX-Hybridkonfigurationen

IP-PBX-Hybridanlagen können analoge, digitale und VoIP-Funktionen bereitstellen. Wenn auf einer IP-PBX-Anlage die richtigen Schnittstellen installiert sind und die Software, die mehrere Schnittstellentypen unterstützt, korrekt installiert ist, wird die IP-PBX-Anlage als IP-PBX-Hybridanlage erachtet. Mit einer IP-PBX-Hybridanlage kann eine Mischung aus analogen, digitalen und IP-Telefonen verwendet werden.

Die meisten modernen IP-PBX-Anlagen unterstützen und bieten alle drei Typen der Sprachkommunikation. Eine traditionelle IP-PBX-Anlage kann zu einer IP-PBX-Hybridanlage aufgerüstet werden, indem die erforderlichen Schnittstellen und Software- bzw. Firmwareupdates installiert werden.

Dank der Mischung aus analogen, digitalen und IP-Telefonen können die Benutzer in der Organisation zahlreiche neue Funktionen nutzen, und die Telefonieumgebung wird erheblich flexibler. Die Verwendung einer IP-PBX-Hybridanlage ermöglicht zudem einen graduellen Übergang zu einer vollständig auf VoIP basierenden Telefonieumgebung und einem vollständig auf VoIP basierenden Voicemessagingsystem in der Organisation.

Ob für das Herstellen einer Verbindung mit Clientzugriffs- und Postfachservern ein VoIP-Gateway erforderlich ist, hängt von mehreren Faktoren ab. Einer dieser Faktoren ist die Kompatibilität der VoIP-Protokolle, die von der IP-PBX-Anlage oder der IP-PBX-Hybridanlage und von Unified Messaging verwendet werden. Wenn kein VoIP-Gateway erforderlich ist, ist die Telefonieinfrastruktur weniger komplex, und die Unterstützungsanforderungen für Unified Messaging sind folglich geringer.

Zurück zum Seitenanfang

## Identifikation des anrufenden oder angerufenen Teilnehmers

Die Identifikation des anrufenden oder angerufenen Teilnehmers ist ein von der Telefongesellschaft bereitgestellter Dienst, mit dem der angerufene Teilnehmer die Telefonnummer und mitunter auch den Namen des Anrufers erkennen kann sowie weitere Informationen zum Anruf erhält. Diese Informationen werden mithilfe der Anrufsignalisierung über ein serielles Kabel gesendet. Wenn ein Anruf von einer Telefongesellschaft bei einer PBX- oder IP-PBX-Anlage eingeht, enthält dieser Anruf auch Informationen zur Identifikation. Dazu gehören:

  - Nummer des anrufenden Teilnehmers

  - Nummer des angerufenen Teilnehmers

  - Statuscodes wie "ring-no-answer" (Klingeln, aber keine Antwort), Zustand der Leitung, Besetzt und CFA (Call forward always, generelle Anrufweiterleitung)

  - Für den Anruf verwendete Leitungs- oder Portnummer

  - Bei der Telefonie werden Signalinformationen verwendet, um Informationen zwischen den Endpunkten in einem Netzwerk auszutauschen, damit Anrufe eingerichtet, gesteuert und beendet werden können. Unified Messaging unterstützt verschiedene Signalmethoden, die von VoIP-Gateways und IP-PBX-Anlagen verwendet werden. Die jeweils verwendete Signalmethode ist vom verwendeten Gerätetyp und von der von der Telefongesellschaft verwendeten Signalmethode abhängig. Der wichtigste Faktor ist, dass das Gerät, von dem eine Verbindung mit der Telefongesellschaft und dem VoIP-Gateway oder der IP-PBX-Anlage hergestellt wird, mindestens eine der Signalmethoden unterstützt, die die Übermittlung und den Empfang von Informationen zur Identifikation des anrufenden oder angerufenen Teilnehmers ermöglichen. Weitere Informationen zur Signalkonfiguration für ein unterstütztes VoIP-Gateway finden Sie unter [Telefonieratgeber für Exchange 2013](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013).

Es können zwar noch weitere Signalmethoden verwendet werden, doch die beiden folgenden sind die beliebtesten Signalmethoden:

  - **Simplified Message Desk Interface (SMDI):**  SMDI ist ein Protokoll, über das Signale, Anrufsteuerung und Informationen zur Anrufidentifikation von einer Schnittstelle zwischen einem Telefonsystem und einem Voicemailsystem bereitgestellt werden. Dieses Protokoll stellt dem Voicemailsystem die Informationen zur Verfügung, die zum Verarbeiten eines eingehenden Anrufs erforderlich sind. Wann immer ein eingehender Anruf mittels SMDI über eine serielle oder eine RS-232-Schnittstelle gesendet wird, werden in den gesendeten Informationen die Leitung oder der Port, der Anruftyp und die Nummer des anrufenden oder angerufenen Teilnehmers angegeben. Über das SMDI-Kabel wird ein Gerät wie eine PBX-Anlage mit einem seriellen Anschluss am VoIP-Gateway verbunden. SMDI wird jedoch auch mit IP-PBX-Anlagen eingesetzt. Das SMDI-Protokoll unterstützt pro Nummer eines anrufenden und angerufenen Teilnehmers maximal 10 Ziffern. Diese Einschränkung ist im Protokoll festgelegt und kann nicht geändert werden.

  - **In-Band:**  Durch In-Band-Signale wird die Vermittlung von Signalen, Anrufsteuerung und Informationen zur Anrufidentifikation von einer Telefongesellschaft möglich. Diese Informationen werden über den gleichen Kanal und im gleichen Band (300 Hz bis 3,4 kHz) wie Sprache und andere Audiodaten eines Anrufs übermittelt. Wenn z. B. ein Benutzer einen Anruf mit dem DTMF- bzw. Tonwahlverfahren tätigt und mit dem angerufenen Teilnehmer spricht, wird für die Tonwahl- und Sprachdaten der gleiche Kanal und das gleiche Band verwendet. In-Band-Signale bieten weniger Sicherheit, da die Steuerungssignale dem Benutzer offen gelegt werden. Zudem ist diese Signalmethode weniger beliebt als SMDI. In-Band-Signale gelten nur für CAS (Channel Associated Signaling).

Zurück zum Seitenanfang

