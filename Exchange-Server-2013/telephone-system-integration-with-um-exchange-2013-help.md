---
title: 'Telefonsystemintegration mit UM: Exchange 2013 Help'
TOCTitle: Telefonsystemintegration mit UM
ms:assetid: b8790117-b040-4c84-9d34-005c75088e76
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673558(v=EXCHG.150)
ms:contentKeyID: 50554897
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Telefonsystemintegration mit UM

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Für die Bereitstellung eines Unified Messaging-Servers (UM) benötigen Sie ein solides Verständnis grundlegender Telefoniekonzepte und -komponenten. Nachdem Sie sich mit den Grundlagen der Telefonie vertraut gemacht haben, können Sie UM in eine Exchange-Organisation integrieren. Die grundlegenden Konzepte und Komponenten umfassen Folgendes:

  - Leitungsvermittelte und paketvermittelte Netzwerke

  - PBX-Anlagen (Private Branch eXchange)

  - IP-PBX-Anlagen

  - VoIP (Voice over Internet Protocol)

  - VoIP-Gateways

In einer lokalen, Hybrid- oder Office 365-Umgebung ist das Verbinden und Konfigurieren der benötigten Telefoniekomponenten der komplexeste und wichtigste Schritt für eine erfolgreiche Bereitstellung von UM, ob mit oder ohne Lync Server Enterprise-VoIP. Für ein herkömmliches Telefonienetzwerk müssen Sie VoIP-Gateways, erweiterte VoIP-Gateways, Nebenstellenanlagen, IP-Nebenstellenanlagen und Session Border Controllers (SBCs) verbinden und konfigurieren und bei Verwenden von Microsoft Lync Server und UM mit einem Telefonienetzwerk verbinden.

Die Planung und Bereitstellung einer Neubereitstellung von UM oder ein Upgrade eines älteren Voicemailsystems kann für Organisationen mit Herausforderungen verbunden sein. Spezifische Kenntnisse zu VoIP-Gateways, Nebenstellenanlagen, IP-Nebenstellenanlagen, Microsoft Lync Server und Unified Messaging sind erforderlich. Abhängig von Ihrer technischen Erfahrung mit Exchange- und Voicemailsystemen sollten Sie möglicherweise einen Unified Messaging-Spezialisten hinzuziehen. Ein Exchange Unified Messaging-Spezialist kann einen reibungslosen Übergang von einem Legacy- oder Drittanbieter-Voicemailsystem zu Exchange Unified Messaging sicherstellen. Weitere Informationen zur Kontaktaufnahme mit einem Unified Messaging-Spezialisten finden Sie unter [Microsoft Exchange Server 2013 Unified Messaging (UM) Specialists](http://go.microsoft.com/fwlink/p/?linkid=262708) .

## Integrieren Ihres Telefonienetzwerks

Unified Messaging erfordert die Integration Ihrer Exchange Server-Bereitstellung in das vorhandene Telefoniesystem oder eine Integration in Microsoft Lync Server für Ihre Organisation. Für eine erfolgreiche Bereitstellung und Verwaltung von UM-Voicemail müssen Sie die vorhandene Telefonie-Infrastruktur bzw. Microsoft Lync Server Enterprise Voice-Bereitstellung sorgfältig analysieren und die entsprechenden Planungsschritte ausführen.

## VoIP-Gateways

Wenn Sie UM in einer Exchange-Organisation bereitstellen, müssen Sie mindestens ein VoIP-Gateway installieren, bereitstellen und konfigurieren, um eine Verbindung mit den Nebenstellenanlagen in Ihrem Telefonienetzwerk herzustellen, oder SIP-fähige (Session Initiation Protocol) Nebenstellenanlagen oder IP-Nebenstellenanlagen installieren, bereitstellen und konfigurieren.

Ein VoIP-Gateway ist ein Hardwaregerät eines Drittanbieters, das eine ältere Nebenstellenanlage mit Ihrem LAN verbindet. Das VoIP-Gateway ermöglicht der Nebenstellenanlage die Kommunikation mit den Exchange-Servern in Ihrer Organisation.

Unified Messaging basiert auf der Fähigkeit des VoIP-Gateways, TDM-Protokolle (Time Division Multiplexing) oder leitungsvermittelte Telefonieprotokolle wie ISDN oder QSIG von einer Nebenstellenanlage in IP- oder VoIP-basierte Protokolle wie SIP (Session Initiation Protocol), RTP (Realtime Transport Protocol) oder T.38 für die Faxübermittlung in Echtzeit zu übersetzen bzw. umzuwandeln. Das VoIP-Gateway ist ein integraler Bestandteil und Voraussetzung für die Funktionalität und den Betrieb von Unified Messaging. Der VoIP-Gateway kann ebenfalls an Nebenstellenanlagensysteme angeschlossen werden, die VoIP anstelle leitungsvermittelter Festnetzprotokolle verwenden.

Die Auswahl des geeigneten VoIP-Gateways, einer IP-Nebenstellenanlage, einer SIP-fähigen Nebenstellenanlage oder eines SBC ist nur der erste Schritt zur Integration der UM-Funktion in Ihr Telefoniesystem. Sie müssen diese Geräte für die Zusammenarbeit mit UM konfigurieren. Bei lokalen und Hybridbereitstellungen müssen Sie die benötigen Clientzugriffs- und Postfachserver bereitstellen sowie alle erforderlichen UM-Komponenten erstellen und konfigurieren. Für Office 365 mit gehosteter Voicemail müssen keine Server installiert und konfiguriert werden. Die Komponenten erlauben eine Verbindung zwischen Ihrem leitungsbasierten Telefonienetzwerk und Ihrem IP-Datennetzwerk, wodurch Voicemail für die Benutzer in Ihrer Organisation ermöglicht wird. Einzelheiten und unterstützte Telefoniegeräte finden Sie in den folgenden Ressourcen:

  - [Telefonieratgeber für Exchange 2013](telephony-advisor-for-exchange-2013-exchange-2013-help.md)

  - [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md)

  - [Konfigurationshinweise für unterstützte Session Border Controller](configuration-notes-for-supported-session-border-controllers-exchange-2013-help.md)

## Microsoft Lync Server

Unified Messaging kann Microsoft Lync Server nutzen, um Sprachnachrichten, Chat, erweiterte Anwesenheitsinformationen, Audio-/Videokonferenzen und E-Mail in einer vertrauten, integrierten Kommunikationsumgebung zu kombinieren. Das Bereitstellen von Enterprise Voice-Funktionen für die Benutzer in Ihrer Organisation durch Integration von UM und Microsoft Lync Server hat die folgenden Vorteile:

  - Benachrichtigungen zur erweiterten Anwesenheitskontrolle für eine Vielzahl von Anwendungen, die Benutzer über die Verfügbarkeit von Kontakten informieren.

  - Integration von Chat, Sprachnachrichten, Konferenzfunktionen, E-Mail und anderen Kommunikationsmodi, mit deren Hilfe die Benutzer den für die jeweilige Aufgabe optimal geeigneten Modus auswählen können. Die Benutzer können bei Bedarf auch von einem Modus in einen anderen wechseln.

  - Die Verfügbarkeit von Kommunikationsalternativen an beliebigen Standorten mit verfügbarer Internetverbindung.

  - Ein intelligenter Client (Microsoft Lync) für Telefonie, Chat und Konferenzen.

  - Einheitliche Benutzerfreundlichkeit über verschiedene Geräte hinweg.

Die Exchange UM-Routingkomponente übernimmt das Routing von Voicemail zwischen Lync Server und Exchange-Servern, um Lync Server mit Unified Messaging-Funktionen zu integrieren. Die Exchange UM-Routingkomponente in Lync Server übernimmt auch das erneute Routing von Voicemail über das Festnetz, wenn keine Exchange-Server verfügbar sind. Wenn Enterprise Voice an Zweigstellenstandorten bereitgestellt sind und diese Standorte keine ausfallsichere WAN-Verbindung zu einem zentralen Standort haben, stellt eine Survivable Branch Appliance, die Sie am Zweigstellenstandort bereitstellen, Voicemail für die Benutzer der Zweigstelle bereit, sollte eine WAN-Verbindung ausfallen. Wenn die WAN-Verbindung nicht verfügbar ist, führt die Survivable Branch Appliance folgende Aufgaben aus:

  - Erneutes Routing nicht beantworteter Anrufe über das Festnetz zu einem Exchange-Server am zentralen Standort.

  - Bereitstellen der Fähigkeit, dass Benutzer Sprachnachrichten über das Festnetz abrufen können.

  - Einreihen von Benachrichtigungen über verpasste Anrufe in eine Warteschlange und deren anschließendes Hochladen auf den Exchange-Server, wenn die WAN-Verbindung wieder besteht.

Weitere Informationen zu Microsoft Lync Server finden Sie unter [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752) .


> [!WARNING]
> Wenn Sie Unified Messaging und Lync Server in einer lokalen oder Hybridbereitstellung integrieren, stehen Benachrichtigungen über verpasste Anrufe Benutzern nicht zur Verfügung, die über ein Postfach auf einem Exchange&nbsp;2007- oder Exchange&nbsp;2010-Postfachserver verfügen. Es wird eine Benachrichtigung über einen verpassten Anruf generiert, wenn ein Benutzer sich abmeldet, bevor der Anruf an einen Postfachserver gesendet wurde.


