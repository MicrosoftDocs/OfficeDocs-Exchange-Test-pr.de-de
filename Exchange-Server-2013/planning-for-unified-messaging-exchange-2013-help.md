---
title: 'Planen von Unified Messaging: Exchange 2013 Help'
TOCTitle: Planen von Unified Messaging
ms:assetid: 942788b1-b19d-40b3-a52e-2e1fef8df3f9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674306(v=EXCHG.150)
ms:contentKeyID: 50476209
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Planen von Unified Messaging

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Bei der Planung Ihrer Unified Messaging (UM)-Bereitstellung müssen Sie viele Faktoren berücksichtigen. Sie müssen die verschiedenen Elemente von Unified Messaging sowie jede Komponente und jede Funktion verstehen, damit Sie die Unified Messaging-Infrastruktur und -Bereitstellung entsprechend planen können. Wenn Sie Zeit für die Planung und die Analyse von Einzelaspekten vorsehen, können Sie Probleme bei der Bereitstellung von Unified Messaging in Ihrer Organisation verhindern.

Sie können Unified Messaging in einer neuen Exchange-Organisation bereitstellen oder ein Upgrade von einer Legacy- oder Drittanbieterlösung für Voicemail durchführen. Bei einem Upgrade müssen Sie entscheiden, ob Sie die Geräte, die leitungsbasierte Telefonieprotokolle akzeptieren, zu einem Datennetzwerk mit IP konvertieren oder eine Enterprise-VoIP-Lösung wie Microsoft Lync Server bereitstellen möchten. Dies ist lediglich der erste Schritt der Vorbereitung darauf, UM für Ihre Organisation zu planen und bereitzustellen.

## Planen Ihres Voicemailsystems

UM bietet Voicemail, Fax und E-Mail-Messaging in einem Informationsspeicher, auf den von einem Telefon, dem Computer eines Benutzers oder von einem mobilen Gerät aus zugegriffen werden kann. Benutzer erhalten über E-Mail-Clients wie Outlook oder Outlook Web App Zugriff auf Sprachnachrichten, E-Mails, Kalenderinformationen und persönliche Kontakte in ihrem Exchange-Postfach.

Clientzugriffsserver mit dem Microsoft Exchange Unified Messaging-Anrufrouterdienst sowie Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst bieten Voicemailfunktionen für Benutzer in Ihrer Organisation.

Postfachserver benötigen Clientzugriffsserver, die SIP-Datenverkehr aus eingehenden Anrufen weiterleiten und dann eine Verbindung mit einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem Session Border Controller (SBC) herstellen und den RTP/SRTP-Mediendatenverkehr annehmen. Alle Voicemail- und Faxnachrichten werden vom Microsoft Exchange Unified Messaging-Dienst auf einem Postfachserver gesendet, um an das Postfach des Benutzers übermittelt zu werden. Um die Voicemailfunktionen von Unified Messaging verwenden zu können, benötigt der Benutzer ein Exchange-Postfach.

## Planen der UM-Bereitstellung

Im Allgemeinen gilt: Je einfacher die Unified Messaging-Topologie, umso leichter ist UM bereitzustellen und zu verwalten. Installieren Sie so wenige Clientzugriffs- und Postfachserver wie möglich, und erstellen Sie so wenig Unified Messaging-Komponenten (z. B. UM-Wählpläne, automatische Telefonzentralen und UM-Postfachrichtlinien) wie möglich, um Ihre geschäftlichen und organisatorischen Ziele zu erreichen. Große Unternehmen mit komplexen Netzwerk- und Telefonieumgebungen, mehreren Geschäftseinheiten oder anderen komplizierten Strukturen erfordern eine ausführlichere Planung als kleine Organisationen mit relativ einfachen Unified Messaging-Anforderungen.

Im Folgenden werden einige der Bereiche beschrieben, die Sie bei der Planung von Unified Messaging in Ihrer Organisation berücksichtigen sollten:

  - **Organisatorische Anforderungen**   Bewerten Sie Ihre geschäftlichen Anforderungen, die Vorteile der Bereitstellung eines Voicemailsystems, die physische Topologie Ihres Netzwerks und Ihres Unternehmens sowie die Sicherheitsanforderungen für Ihre Organisation.

  - **Anforderungen im Hinblick auf die Telefonie**   Überprüfen Sie Ihr vorhandenes System für Telefonie, leitungsvermitteltes Netzwerk und Voicemail.

  - **Netzwerkanforderungen**   Analysieren Sie Ihre Netzwerktopologie, den Entwurf Ihres aktuellen paketvermittelten IP-Netzwerks einschließlich der LAN- und WAN-Verbindungen sowie die Geräte.

  - **Active Directory (Verzeichnisdienst)**   Untersuchen Sie Ihre aktuelle Implementierung und Ihren aktuellen Entwurf, und denken Sie über das Vorgehen zur Integration von UM nach.

  - **Bereitstellungsmodell**   Entscheiden Sie, ob Sie eine hybride, rein online oder rein lokal konfigurierte UM-Bereitstellung wünschen.

  - **Exchange-Anforderungen** Bestimmen Sie Folgendes:
    
      - Wie viele Benutzer Voicemail verwenden werden.
    
      - Welche UM-Funktionen und -Dienste Sie bereitstellen möchten, wie gleichzeitige Anrufe, internen und externen Zugriff für Benutzer, eingehende Faxe, Voicemailvorschau usw.
    
      - Die Anzahl der bereitzustellenden Clientzugriffs- und Postfachserver.
    
      - Die Speicheranforderungen und -kontingente für Voicemailbenutzer.
    
      - Den besten Entwurf für hohe Verfügbarkeit und Ausfallsicherheit der Standorte. Hierzu gehören UM-Systemanforderungen, die Bereitstellung einer hochgradig verfügbaren und skalierbaren UM-Bereitstellung sowie die Erfüllung von Anforderungen an die Systemhardware, um die Leistung sicherzustellen.

  - **Integration mit Telefoniekomponenten und -geräten**   Entscheiden Sie, ob Sie herkömmliche Telefoniegeräte oder Microsoft Lync Server verwenden möchten. Überlegen Sie, wo Sie VoIP-Gateways, Telefoniegeräte sowie Clientzugriffsserver und Postfachserver platzieren möchten und ob Sie in Ihrer Organisation Enterprise-VoIP aktivieren möchten.

## Verbinden des Telefonienetzwerks

Unified Messaging erfordert die Integration Ihrer Exchange Server-Bereitstellung in das vorhandene Telefoniesystem oder eine Integration in Microsoft Lync Server. Sie müssen die vorhandene Telefonieinfrastruktur und Microsoft Lync Server-Installation sorgfältig analysieren und dann die richtigen Planungsschritte befolgen, um UM-Voicemail erfolgreich bereitstellen und verwalten zu können.

**VoIP-Gateways** Die Auswahl des geeigneten VoIP-Gateways, einer IP-Nebenstellenanlage, einer SIP-aktivierten Nebenstellenanlage oder eines SBC ist nur der erste Schritt zur Integration der UM-Funktion in Ihr Telefoniesystem. Sie müssen diese Geräte zur Zusammenarbeit mit UM konfigurieren, die erforderlichen Clientzugriffs- und Postfachserver bereitstellen sowie alle benötigten UM-Komponenten erstellen und konfigurieren. Diese Komponenten erlauben eine Verbindung zwischen dem leitungsbasierten Protokollnetzwerk und Ihrem IP-Datennetzwerk und ermöglichen die Verwendung von Voicemail durch die Benutzer.

**Microsoft Lync Server**   Unified Messaging kann Microsoft Lync Server nutzen, um Voicemessaging, Chat, erweiterte Anwesenheitsinformationen, Audio-/Videokonferenzen und E-Mail in einer vertrauten, integrierten Kommunikationsumgebung zu kombinieren. Die Integration von UM und Microsoft Lync Server bietet folgende Vorteile:

  - Benachrichtigungen zur erweiterten Anwesenheitskontrolle für eine Vielzahl von Anwendungen, die Benutzer über die Verfügbarkeit von Kontakten informieren.

  - Integration von Instant Messaging, Voicemessaging, Konferenzfunktionen, E-Mail und anderen Kommunikationsmethoden, mit deren Hilfe die Benutzer die für die Aufgabe optimal geeignete Methode auswählen können. Die Benutzer können bei Bedarf auch von einer Methode zu einer anderen wechseln.

  - Die Verfügbarkeit von Kommunikationsalternativen an beliebigen Standorten mit verfügbarer Internetverbindung.

  - Ein intelligenter Client (Microsoft Lync) für Telefonie, Chat und Konferenzen.

  - Einheitliche Benutzerfreundlichkeit über verschiedene Geräte hinweg.

Weitere Informationen zu Microsoft Lync Server finden Sie unter [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752) .


> [!NOTE]
> Planung und Bereitstellung von Unified Messaging können Herausforderungen darstellen. Abhängig von Ihrer technischen Erfahrung mit Exchange- und Voicemailsystemen sollten Sie möglicherweise einen Unified Messaging-Spezialisten hinzuziehen. Ein Exchange Unified Messaging-Spezialist kann einen reibungslosen Übergang von einem Legacy- oder Drittanbieter-Voicemailsystem zu Exchange Unified Messaging sicherstellen. Für die Durchführung einer neuen Bereitstellung oder für das Upgrade eines Legacy-Voicemailsystems sind umfassende Kenntnisse zu VoIP-Gateways, Nebenstellenanlagen und Unified Messaging erforderlich. Weitere Informationen zur Kontaktaufnahme mit einem Unified Messaging-Spezialisten finden Sie unter <A href="http://go.microsoft.com/fwlink/p/?linkid=262708">Microsoft Exchange Server&nbsp;2013 Unified Messaging (UM) Specialists</A> .



## Bereitstellungsschritte

Für Unified Messaging sind viele Bereitstellungsoptionen verfügbar. Alle Optionen weisen einige gemeinsame Schritte auf, die ausgeführt werden müssen, um ein skalierbares System mit hoher Verfügbarkeit zur Unterstützung einer großen Anzahl von Benutzern zu erstellen. Diese Schritte lauten wie folgt:

1.  Sie können Ihre Telefoniekomponenten oder Microsoft Lync Server mit Unified Messaging bereitstellen und konfigurieren.

2.  Überprüfen Sie, ob der Clientzugriffsserver und der Postfachserver, die für Unified Messaging erforderlich sind, korrekt installiert wurden.

3.  Erstellen und konfigurieren Sie die für Unified Messaging erforderlichen Unified Messaging-Komponenten, wie z. B. UM-Wähleinstellungen, UM-IP-Gateways, UM-Sammelanschlüsse und UM-Postfachrichtlinien.

4.  Führen Sie die nach der Bereitstellung relevanten Aufgaben durch, wie das Beziehen von Zertifikaten für MTLS, das Erstellen automatischer UM-Telefonzentralen und das Konfigurieren der Faxfunktion.

Einzelheiten zur Bereitstellung von Unified Messaging finden Sie unter [Bereitstellen von Exchange 2013 UM](deploy-exchange-2013-um-exchange-2013-help.md).

Wenn Sie Ihre Unified Messaging-Umgebung in Microsoft Lync Server integrieren, sind weitere Planungsaspekte zu beachten. Weitere Informationen finden Sie unter [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md).

