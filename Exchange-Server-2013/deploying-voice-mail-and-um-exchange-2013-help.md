---
title: 'Bereitstellen von Voicemail und UM: Exchange 2013 Help'
TOCTitle: Bereitstellen von Voicemail und UM
ms:assetid: 3df61b62-a1e4-41fb-969c-319189ae4e42
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673519(v=EXCHG.150)
ms:contentKeyID: 50475439
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Voicemail und UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit Exchange Unified Messaging (UM) können Sie den Benutzern in der Organisation Voicemaildienste bereitstellen. Wenn Sie Unified Messaging bereitstellen, müssen Sie die Exchange Server-Bereitstellung in das vorhandene Telefoniesystem Ihrer Organisation oder in Microsoft Lync Server integrieren. Für eine erfolgreiche Bereitstellung und die Durchführung der richtigen Planungsschritte für die Bereitstellung und Verwaltung von Voicemail in Unified Messaging ist eine sorgfältige Analyse Ihrer vorhandenen Telefonieinfrastruktur erforderlich. Wenn Sie eine Integration von Exchange in Lync Server anstreben, müssen Sie sich auch mit diesem Produkt vertraut machen.

Bei der Bereitstellung von Unified Messaging haben Sie verschiedene Optionen, die von der in Ihrer Organisation genutzten Telefoniehardware abhängen. Wenn Sie UM mit dem Telefonienetzwerk verbinden, muss eine der folgenden Telefoniekonfigurationen in Ihrer Organisation vorliegen:

  - Ein oder mehrere VoIP-Gateways mit einer oder mehreren Nebenstellenanlagen

  - Eine oder mehrere IP-Nebenstellenanlagen

  - Eine oder mehrere SIP-aktivierte Nebenstellenanlagen

  - Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server 2010 oder 2013


> [!WARNING]
> Wenn Sie Exchange UM in einer gehosteten oder Hybridumgebung bereitstellen, müssen Sie Session Border Controller (SBCs) bereitstellen. SBCs ermöglichen keine Verbindung von UM mit einem Telefonienetzwerk. Zudem stellen sie einer Organisation kein Freizeichen bereit. Sie verbinden jedoch Ihre lokale UM-Bereitstellung mit einem Datencenter. Dazu wird das IP-Protokoll über ein öffentliches oder privates WAN verwendet.



**Telefoniehardware**   Die Auswahl des geeigneten VoIP-Gateways, einer IP-Nebenstellenanlage oder eines SBC ist nur der erste Schritt zur Integration der UM-Funktion in Ihr Telefonienetzwerk. Sie müssen diese Geräte zur Zusammenarbeit mit UM konfigurieren, die erforderlichen Clientzugriffs- und Postfachserver bereitstellen sowie alle benötigten UM-Komponenten erstellen und konfigurieren. Diese Komponenten erlauben eine Verbindung zwischen dem leitungsbasierten Protokollnetzwerk und Ihrem IP-Datennetzwerk und ermöglichen die Verwendung von Voicemail für Benutzer in Ihrer Organisation. Weitere Informationen finden Sie unter [Telefonieratgeber für Exchange 2013](telephony-advisor-for-exchange-2013-exchange-2013-help.md).

**Microsoft Lync Server**   Unified Messaging kann Microsoft Lync Server nutzen, um Voicemessaging, Chat, erweiterte Anwesenheitsinformationen, Audio-/Videokonferenzen und E-Mail in einer vertrauten, integrierten Kommunikationsumgebung zu kombinieren. Die Integration von UM und Lync Server bietet folgende Vorteile:

  - Benachrichtigungen zur erweiterten Anwesenheitskontrolle für eine Vielzahl von Anwendungen, die Benutzer über die Verfügbarkeit von Kontakten informieren.

  - Integration von Chatfunktionen, Voicemessaging, Konferenzfunktionen, E-Mail und anderen Kommunikationsmethoden, mit deren Hilfe die Benutzer die für die Aufgabe optimal geeignete Methode auswählen können. Die Benutzer können bei Bedarf auch von einer Methode zu einer anderen wechseln.

  - Die Verfügbarkeit von Kommunikationsalternativen an beliebigen Standorten mit verfügbarer Internetverbindung.

  - Ein intelligenter Client (Microsoft Lync) für Telefonie, Chat und Konferenzen.

  - Einheitliche Benutzerfreundlichkeit über verschiedene Geräte hinweg.

Weitere Informationen zu Lync Server finden Sie unter [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752).

## Bereitstellungsschritte

Für Unified Messaging sind viele Bereitstellungsoptionen verfügbar. Alle Optionen weisen einige gemeinsame Schritte auf, die ausgeführt werden müssen, um ein skalierbares System mit hoher Verfügbarkeit zur Unterstützung einer großen Anzahl von Benutzern zu erstellen. Diese Schritte lauten wie folgt:

1.  Sie können Ihre Telefoniekomponenten oder Microsoft Lync Server mit Unified Messaging bereitstellen und konfigurieren.

2.  Überprüfen Sie, ob der Clientzugriffsserver und der Postfachserver, die für Unified Messaging erforderlich sind, korrekt installiert wurden.
    

    > [!WARNING]
    > Sie müssen in Ihrer Organisation mindestens einen Exchange 2013-Postfachserver bereitstellen, bevor Sie die VoIP-Gateways oder IP-PBXs so konfigurieren können, dass diese UM SIP- und RTP-Datenverkehr zum Exchange 2013-Clientzugriffsserver senden.



3.  Erstellen und konfigurieren Sie die für Unified Messaging erforderlichen Unified Messaging-Komponenten wie z. B. UM-Wähleinstellungen, UM-IP-Gateways, UM-Sammelanschlüsse und UM-Postfachrichtlinien.

4.  Führen Sie die nach der Bereitstellung relevanten Aufgaben durch, wie das Bereitstellen von Zertifikaten für MTLS, das Erstellen automatischer UM-Telefonzentralen und das Konfigurieren von Clientfunktionen.

Einzelheiten zur Bereitstellung von Unified Messaging finden Sie unter [Bereitstellen von Exchange 2013 UM](deploy-exchange-2013-um-exchange-2013-help.md).

Wenn Sie Ihre Unified Messaging-Umgebung in Microsoft Lync Server integrieren, sind weitere Planungsaspekte zu beachten. Weitere Informationen finden Sie unter [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md).

