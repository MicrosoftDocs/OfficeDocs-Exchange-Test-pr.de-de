---
title: 'Verbinden von UM mit einem unterstützten VoIP-Gateway: Exchange 2013 Help'
TOCTitle: Verbinden von UM mit einem unterstützten VoIP-Gateway
ms:assetid: b8dfc8bd-2ee5-418d-b0a4-4fa2ec7e2a2e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124360(v=EXCHG.150)
ms:contentKeyID: 50554898
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbinden von UM mit einem unterstützten VoIP-Gateway

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-19_

Wenn Sie Unified Messaging (UM) einrichten, müssen Sie die VoIP-Gateways (Voice over IP), IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder Session Border Controllers (SBCs) in Ihrem Netzwerk für die Kommunikation mit den Clientzugriffsservern, auf denen der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird, und den Postfachserver konfigurieren, auf denen der Microsoft Exchange Unified Messaging-Dienst in Ihrer Exchange-Organisation ausgeführt wird. Sie müssen Clientzugriffs- und Postfachserver auch für die Kommunikation mit den VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder SBCs konfigurieren.


> [!NOTE]
> Nachdem Sie Ihre Clientzugriffs- und Postfachserver mit den VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen und SBCs in Ihrem Datennetzwerk verbunden haben, müssen Sie benötigen UM-Komponenten erstellen und außerdem Benutzer für Unified Messaging aktivieren, damit sie das Voicemailsystem nutzen können.



## Schritte

Es folgen die grundlegenden Schritte zum Verbinden von VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder SBCs mit Clientzugriffs- und Postfachservern:

Schritt 1: Installieren Sie die Clientzugriffs- und Postfachserver in Ihrer Organisation.

Schritt 2: Erstellen und konfigurieren Sie eine Telefondurchwahl, einen SIP-URI oder E.164-UM-Wählplan.

Schritt 3: Erstellen und konfigurieren Sie einen UM-IP-Gateway. Sie müssen ein UM-IP-Gateway für alle VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder SBCs erstellen und konfigurieren, die eingehende Anrufe annehmen und ausgehende Anrufe senden.

Schritt 4: Erstellen Sie bei Bedarf einen neuen UM-Sammelanschluss. Wenn Sie ein neues UM-IP-Gateway erstellen und keinen UM-Wählplan angeben, wird automatisch ein UM-Sammelanschluss erstellt.

In den folgenden Abschnitten erhalten Sie Informationen zu den einzelnen Schritten.

## Schritt 1: Installieren von Clientzugriffs- und Postfachservern

Wenn Sie Exchange-Server in Ihrer Organisation bereitstellen, können Sie den Clientzugriffs- und Postfachserver auf demselben oder getrennten Computern installieren. Führen Sie zum Installieren des Clientzugriffsservers auf dem Installationsdatenträger **Setup.exe** aus. Unabhängig davon, ob Sie den Clientzugriffsserver auf demselben Computer wie den Postfachserver oder auf einem anderen Computer installieren, verwenden Sie denselben Befehl. Weitere Informationen finden Sie unter [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md). Wenn Sie Ihrem vorhandenen Exchange-Server Features und Funktionalität hinzufügen, können Sie **Programme und Features** oder **Setup.exe** verwenden.

## Schritt 2: Erstellen und Konfigurieren von UM-Wähleinstellungen

Nachdem Sie die benötigten Server installiert haben, müssen Sie zunächst einen UM-Wählplan erstellen. Ein UM-Wählplan umfasst die Konfigurationseinstellungen, mit deren Hilfe Sie eine Verbindung mit Ihrem Telefonienetzwerk herstellen können, indem Sie ein oder mehrere UM-IP-Gateways verbinden. Ein UM-IP-Gateway und UM-Sammelanschluss sind direkt mit einem UM-Wählplan verbunden und ebenfalls erforderlich. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

Ein UM-Wählplan richtet einen Link zwischen der Durchwahlnummer eines Empfängers und einem UM-aktivierten Postfach ein. Wenn Sie einen UM-Wählplan erstellen, können Sie die Anzahl der Stellen in den Durchwahlnummern, den URI-Typ (Uniform Resource Identifier) und die VoIP-Sicherheitseinstellung für den Wählplan konfigurieren.

Es gibt drei Wählplantypen: Telefondurchwahl, SIP-URI (Session Initiation Protocol) und E.164. Wenn Sie einen UM-Wählplan erstellen und konfigurieren, müssen Sie den Typ der Informationen bestimmen, der von Ihrer IP-Nebenstellenanlage, SIP-fähigen Nebenstellenanlage oder Nebenstellenanlage gesendet wird, und ob die Anrufe in einem Telefondurchwahl- oder E.164-Format an einen Clientzugriffs- oder Postfachserver gesendet werden. Wenn Sie Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server bereitstellen, müssen Sie einen SIP-URI-Wählplan erstellen und konfigurieren.

## Schritt 3: Erstellen und Konfigurieren eines UM-IP-Gateways

Nach dem Erstellen eines UM-Wählplans müssen Sie ein UM-IP-Gateway erstellen, das alle VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs in Ihrem Netzwerk repräsentiert. Wenn Sie ein UM-IP-Gateway erstellen, können Sie es für die Verwendung einer IP-Adresse oder eines vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) konfigurieren. Wenn Sie einen FQDN verwenden, müssen Sie sicherstellen, dass Sie für das IP-Gateway einen DNS-Hosteintrag ordnungsgemäß konfiguriert haben, damit der Hostname richtig in eine IP-Adresse aufgelöst wird.

Nach der Installation eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines SBC müssen Sie ein UM-IP-Gateway erstellen, welches das physische Hardwaregerät repräsentiert. Nach der Erstellung eines UM-IP-Gateways sendet der Clientzugriffsserver, der das UM-IP-Gateway verwendet, eine SIP OPTIONS-Anforderung an das VoIP-Gateway, die IP-Nebenstellenanlage oder den SBC, um sicherzustellen, dass die jeweilige Komponente reagiert. Wenn das VoIP-Gateway, die IP-Nebenstellenanlage, SIP-fähige Nebenstellenanlage oder der SBC nicht antwortet, protokolliert der Clientzugriffsserver ein Ereignis mit der ID 1088, das besagt, dass die Anforderung keinen Erfolg hatte. Stellen Sie zum Beheben dieses Problems sicher, dass das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC verfügbar und online ist und die Unified Messaging-Konfiguration ordnungsgemäß ist.

Clientzugriffs- und Postfachserver kommunizieren nur mit VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs, wenn diese als vertrauenswürdige SIP-Peers aufgeführt sind. Wenn in einigen Fällen zwei VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs für die Verwendung derselben IP-Adresse konfiguriert sind, wird ein Ereignis mit der ID 1175 protokolliert. Dieses Ereignis kann auftreten, wenn Sie die DNS-Zonen mit einem vollqualifizierten Domänennamen (FQDN) für die VoIP-Gateways im Netzwerk konfiguriert haben. Unified Messaging schützt vor nicht autorisierten Anforderungen, indem die interne URL des virtuellen Unified Messaging-Webdiensteverzeichnisses abgerufen wird, das sich auf dem Server befindet, auf dem der Postfachserver installiert ist. Anschließend wird mithilfe dieser URL die Liste der FQDNs der vertrauenswürdigen SIP-Peers erstellt. Werden zwei FQDNs in dieselbe IP-Adresse aufgelöst, wird dieses Ereignis protokolliert.

Sie müssen den Microsoft Exchange Unified Messaging-Dienst neu starten, wenn ein IP-Gateway für die Verwendung eines FQDN konfiguriert ist und der DNS-Eintrag des UM-IP-Gateways nach dem Start des Diensts geändert wurde. Wenn Sie den Dienst nicht erneut starten, kann der Postfachserver das UM-IP-Gateway nicht finden. Dies ist darauf zurückzuführen, dass ein Postfachserver alle UM-IP-Gateways, IP-Nebenstellenanlagen oder SBCs in einem Cache zwischenspeichert und die DNS-Auflösung nur erfolgt, wenn der Dienst neu gestartet wird oder die Konfiguration eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines SBC geändert wurde.

Exchange Unified Messaging unterstützt mehrere Hersteller von VoIP-Gateways und weitere Hersteller von IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen und SBCs. Alle diese unterstützten VoIP-Gateways können mit Nebenstellenanlagensystemen von Drittanbietern eine Verbindung herstellen.

Ausführliche Informationen zu VoIP-Gateways finden Sie unter den folgenden Themen:

  - [Erstellen eines UM-IP-Gateways](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway)

  - [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/protected-voice-mail-procedures)

  - [Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM](connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md)

Weitere Informationen finden Sie unter [Verbinden Ihres Voicemailsystems mit Ihrem Telefonnetz](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/connect-voice-mail-system).

## Schritt 4: (Bedarfsabhängiges) Erstellen eines neuen UM-Sammelanschlusses

Der Begriff "Sammelanschluss" dient der Bezeichnung einer Gruppe von Durchwahlnummern von Nebenstellenanlagen bzw. IP-Nebenstellenanlagen, die von Benutzern gemeinsam verwendet werden. Sammelanschlüsse werden für das effiziente Verteilen der eingehenden und ausgehenden Anrufe einer bestimmten Unternehmenseinheit verwendet. Das Erstellen und Definieren eines Sammelanschlusses verringert die Wahrscheinlichkeit, dass der Anrufer bei einem eingehenden Anruf ein Besetztzeichen hört, wenn sein Anruf empfangen wird.

UM-Sammelanschlüsse spiegeln die von Nebenstellenanlagen und IP-Nebenstellenanlagen verwendeten Sammelanschlüsse. Wenn Sie Ihre Nebenstellenanlagen oder IP-Nebenstellenanlagen konfigurieren, müssen Sie mindestens einen UM-Sammelanschluss erstellen und konfigurieren. UM-Sammelanschlüsse fungieren als Verbindung zwischen UM-IP-Gateway und UM-Wählplan.

Abhängig von der Erstellung des UM-IP-Gateways müssen Sie möglicherweise mindestens einen neuen UM-Sammelanschluss erstellen. Wenn Sie beim Erstellen des UM-IP-Gateways dieses nicht mit einem Wählplan verbinden, wird standardmäßig ein einzelner UM-Sammelanschluss erstellt. Wenn Sie beim Erstellen des UM-IP-Gateways dieses mit einem Wählplan verbinden, werden alle eingehenden Anrufe durch die UM-IP-Gateways gesendet, woraufhin diese Anrufe von Clientzugriffs- oder Postfachservern angenommen werden. Wenn Sie beim Erstellen des UM-IP-Gateways dieses nicht mit einem Wählplan verbinden, müssen Sie einen UM-Sammelanschluss mit der ordnungsgemäßen Pilot-ID für eingehende Anrufe erstellen, damit diese von einem UM-IP-Gateway zu einem Wählplan weitergeleitet werden.

Wenn es mehrere Outlook Voice Access-Nummern und Nummern einer automatischen Telefonzentrale gibt und Sie ein UM-IP-Gateway mit einem Wählplan verbunden haben, müssen Sie den UM-Sammelanschluss löschen, der standardmäßig erstellt wurde, um mehrere UM-Sammelanschlüsse erstellen. Details zum Erstellen eines UM-Sammelanschlusses finden Sie unter [Erstellen eines UM-Sammelanschlusses](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-hunt-group).

