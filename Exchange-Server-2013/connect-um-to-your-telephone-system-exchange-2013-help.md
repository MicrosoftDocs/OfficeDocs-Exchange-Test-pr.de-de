---
title: 'Verbinden von UM mit Ihrer Telefonanlage: Exchange 2013 Help'
TOCTitle: Verbinden von UM mit Ihrer Telefonanlage
ms:assetid: 92c3e029-f732-4d6d-b147-2b3006d5f088
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673544(v=EXCHG.150)
ms:contentKeyID: 50554878
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbinden von UM mit Ihrer Telefonanlage

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-30_

Unified Messaging (UM) kombiniert Sprachnachrichten und E-Mails in einem Postfach, auf das über verschiedene Geräte zugegriffen werden kann. Benutzer können die Voicemailnachrichten in ihrem E-Mail-Posteingang oder mit Outlook Voice Access auf einem beliebigen Telefon abhören.

Wenn Sie UM in einer Microsoft Exchange-Organisation bereitstellen, müssen Sie mindestens ein VoIP-Gateway installieren, bereitstellen und konfigurieren, um eine Verbindung mit den Nebenstellenanlagen in Ihrem Telefonienetzwerk herzustellen, oder SIP-fähige (Session Initiation Protocol) Nebenstellenanlagen oder IP-Nebenstellenanlagen installieren, bereitstellen und konfigurieren. Bei einem Upgrade Ihres aktuellen Voicemailsystems müssen Sie die Geräte bereitstellen, die mit Ihrem Telefonienetzwerk verbunden werden, Exchange-Clientzugriffs- und Postfachserver installieren und anschließend die benötigten UM-Komponenten erstellen, über die Ihr Telefonienetzwerk mit Ihrem Datennetzwerk verbunden wird. Dadurch wird ermöglicht, dass in Ihrem Telefonienetzwerk eingehende Anrufe mit Ihren VoIP-Gateways, IP-Nebenstellenanlagen oder SIP-fähigen Nebenstellenanlagen und diese Geräte mit Ihrer Exchange-Organisation verbunden werden.

Wenn Sie entweder Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server installieren, bereitstellen und konfigurieren, benötigen Sie keine VoIP-Gateways, IP-Nebenstellenanlagen oder SIP-fähige Nebenstellenanlagen, um eine direkte Verbindung mit Exchange Unified Messaging herzustellen. Stattdessen ermöglichen ein Lync-Vermittlungsserver oder VoIP-Gateway bzw. erweitertes VoIP-Gateway mit der Funktionalität eines Vermittlungsservers und VoIP-Gateways das Herstellen einer Verbindung mit Exchange UM. Für Enterprise-VoIP aktivierte UM-Benutzer können Sprachnachrichten abrufen, abhören und beantworten und ausgehende Anrufe tätigen. Sie haben über einen Office Communicator- oder Lync-Client außerdem Zugriff auf andere sich auf Lync beziehende Funktionen wie Anwesenheitsinformationen und Chat.

Mithilfe der folgenden Informationen können Sie UM einrichten und bereitstellen sowie Voicemailfunktionen für Benutzer in Ihrer Organisation aktivieren:

  - [Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM](connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md)Erfahren Sie, wie Sie UM-VoIP-Gateways oder IP-Nebenstellenanlagen mit UM verbinden.

  - [Telefonieratgeber für Exchange 2013](telephony-advisor-for-exchange-2013-exchange-2013-help.md)Erfahren Sie mehr über unterstützte VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen.

  - [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md)Erfahren Sie mehr über das Einrichten von VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen.

