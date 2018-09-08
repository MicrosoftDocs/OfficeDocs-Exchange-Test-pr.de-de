---
title: 'Verb. v. VoIP-Gateways, IP-Neb.stell.anl. o. Session Border Controllern m. UM'
TOCTitle: Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM
ms:assetid: a7cecf59-b93a-413b-bb88-29f2669ef2cf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124084(v=EXCHG.150)
ms:contentKeyID: 50554889
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie müssen die Voice over IP-Gateways (VoIP) und IP-Nebenstellenanlagen (PBXs) korrekt konfigurieren, wenn Sie Unified Messaging (UM) für Ihre Organisation bereitstellen. Wenn Sie UM in einer Hybridumgebung bereitstellen, müssen Sie auch Ihre Session Border Controller (SBC) korrekt konfigurieren. Dafür müssen Sie die IP-Schnittstelle der VoIP-Gateways, IP-Nebenstellenanlagen und SBCs konfigurieren, die Sie für die Kommunikation mit den Clientzugriffsservern verwenden, die den Microsoft Exchange Unified Messaging-Call-Router-Dienst ausführen, sowie mit den Postfachservern, die den Microsoft Exchange Unified Messaging-Dienst ausführen.


> [!IMPORTANT]
> Beim Ausführen von Verwaltungsaufgaben für ein VoIP-Gateway, eine IP-Nebenstellenanlage oder einen SBC mithilfe eines Webbrowsers werden die HTTP-Anforderungen, die über das Netzwerk gesendet werden, nicht verschlüsselt. Zum Erhöhen des Sicherheitsniveaus für die VoIP-Gateways, die IP-Nebenstellenanlagen oder die SBCs im Netzwerk verwenden Sie IPSec (Internet Protocol Security) oder SSL (Secure Sockets Layer), um den Schutz der Verwaltungs-Anmeldeinformationen und der im Netzwerk übertragenen Daten zu verbessern. Außerdem wird empfohlen, strenge Authentifizierungsmechanismen und komplexe Adminstratorkennwörter zu verwenden, um die Anmeldeinformationen des Administrators für das Gerät zu schützen.



## Telefonie-IP-Geräteschnittstellen

Sie müssen verschiedene Arten von Ports oder Schnittstellen konfigurieren, damit eine Kommunikation zwischen einer Nebenstellenanlage, einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem SBC und den Clientzugriffs- und Postfachservern in Ihrem Netzwerk möglich wird. Beim Konfigurieren eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines SBC muss berücksichtigt werden, ob das Gerät analog, digital oder analog und digital ist.

Wenn die VoIP-Gatewayschnittstelle für die Verbindung mit einer Nebenstellenanlage analog ist, müssen Sie die entsprechenden Einstellungen ordnungsgemäß konfigurieren, um dem VoIP-Gateway die Kommunikation mit Clientzugriffs- und Postfachservern zu ermöglichen. Bei IP-Nebenstellenanlagen und SBCs müssen Sie außerdem die IP-Schnittstellen ordnungsgemäß konfigurieren, damit diese Geräte mit Clientzugriffs- und Postfachservern kommunizieren können. Alle diese Geräte weisen unterschiedliche Typen von Verbindungen bzw. Ports auf, die je nach Modell oder Hersteller des Gerät verfügbar sind.

So ermöglichen Sie die Kommunikation mit den Clientzugriffs- und Postfachservern in Ihrem Netzwerk:

  - Bei VoIP-Gateways müssen Sie die Telefonieschnittstellen für die Kommunikation mit Ihren Nebenstellenanlagen und die IP-Schnittstelle des Geräts konfigurieren.

  - Bei IP-Nebenstellenanlagen müssen Sie die leitungsbasierten und netzwerk- bzw. IP-basierten Verbindungen konfigurieren.

  - Bei SBCs müssen Sie beide IP-Schnittstellen konfigurieren: eine für das Netzwerk und die andere Schnittstelle, die über das Internet oder eine dedizierte WAN-Verbindung eine Verbindung herstellt.

Es folgt eine Liste der Ressourcen im Exchange TechCenter, die Informationen zur ordnungsgemäßen Konfiguration Ihrer VoIP-Gateways, IP-Nebenstellenanlagen und SBCs enthält:

  - **Dokumentation zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen**   [Telefonieratgeber für Exchange 2013](https://technet.microsoft.com/de-de/library/Ee364753(v=EXCHG.150)) bietet Konfigurationsdateien und Installationsinformationen, die Sie bei der Konfiguration von VoIP-Gateways, Nebenstellenanlagen, IP-Nebenstellenanlagen und SBCs befolgen können.

  - **Konfigurations- und technische Hinweise**   [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](https://technet.microsoft.com/de-de/library/JJ938013(v=EXCHG.150)) bietet Konfigurationsdateien und Installationsinformationen, die Sie bei der Konfiguration von VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen befolgen können.

  - **Konfigurationshinweise zu Exchange Online UM**   [Konfigurationshinweise für unterstützte Session Border Controller](https://technet.microsoft.com/de-de/library/JJ673565(v=EXCHG.150)) bietet Konfigurationsdateien und Installationsinformationen, die Sie bei der Konfiguration von SBCs befolgen können.

Unified Messaging-Spezialisten können Ihnen bei der Konfiguration Ihrer Telefonie- und IP-basierten Netzwerkgeräte behilflich sein. Ein Exchange Unified Messaging-Spezialist kann helfen, einen reibungslosen Übergang von einem Legacy- oder Drittanbieter-Voicemailsystem zu Unified Messaging zu sorgen, und Sie bei der Planung und Bereitstellung eines neuen Voicemailsystems mit Exchange Unified Messaging unterstützen. Für die Bereitstellung eines neuen Voicemailsystems oder das Upgrade eines Legacy-Voicemailsystems sind umfassende Kenntnisse zu VoIP-Gateways, IP-Nebenstellenanlagen, Nebenstellenanlagen und Unified Messaging erforderlich. Weitere Informationen zur Kontaktaufnahme mit einem Unified Messaging-Spezialisten finden Sie unter [Microsoft Exchange Server 2013 Unified Messaging (UM) Specialists](https://go.microsoft.com/fwlink/p/?linkid=262708) oder zu zertifizierten UM-Partnern unter [Microsoft Pinpoint](https://go.microsoft.com/fwlink/p/?linkid=261951).

Nach der Konfiguration einer VoIP-Gateway-, IP-Nebenstellenanlagen- oder SBC-IP-Schnittstelle müssen Sie ein UM-IP-Gateway erstellen und konfigurieren, das alle Geräte repräsentiert, die Sie bereitgestellt haben. Weitere Informationen zum Erstellen eines UM-IP-Gateways finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)).

Nach dem Erstellen eines UM-IP-Gateways senden die mit dem UM-IP-Gateway verbundenen Clientzugriffs- und Postfachserver eine SIP-Anforderung vom Typ OPTIONS an das VoIP-Gateway, die IP-Nebenstellenanlage oder den SBC, um zu prüfen, ob das Gerät antwortet. Wenn das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC nicht auf die Anforderung antwortet, protokolliert der Postfachserver ein Ereignis mit der ID 1088, das besagt, dass die Anforderung keinen Erfolg hatte. Um dieses Problem zu lösen, stellen Sie sicher, dass das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC verfügbar und online ist und dass eine ordnungsgemäße Unified Messaging-Konfiguration vorliegt.

Ein Clientzugriffs- und ein Postfachserver kommunizieren nur mit VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs, wenn diese als vertrauenswürdige SIP-Peers aufgeführt sind. Ein Ereignis mit der ID 1175 wird protokolliert, wenn mehrere DNS-Hosts dieselbe IP-Adresse verwenden. Dieses Ereignis kann auftreten, wenn Sie die DNS-Zonen mit vollqualifizierten Domänennamen (FQDN) für die VoIP-Gateways im Netzwerk konfiguriert haben. Unified Messaging schützt vor nicht autorisierten Anforderungen, indem die interne URL des virtuellen Unified Messaging-Webdiensteverzeichnisses abgerufen wird, das sich auf dem Server befindet, auf dem der Postfachserver installiert ist. Anschließend wird mithilfe dieser URL die Liste der FQDNs der vertrauenswürdigen SIP-Peers erstellt. Werden zwei FQDNs in dieselbe IP-Adresse aufgelöst, wird dieses Ereignis protokolliert.


> [!NOTE]
> Sie müssen den MicrosoftExchange Unified Messaging-Dienst neu starten, wenn ein VoIP-Gateway, eine IP-Nebenstellenanlage oder ein SBC für die Verwendung eines FQDN konfiguriert ist und der DNS-Eintrag des VoIP-Gateways, der IP-Nebenstellenanlage oder des SBCs nach dem Start des Diensts geändert wurde. Wenn Sie den Dienst nicht erneut starten, kann der Postfachserver das VoIP-Gateway, die IP-Nebenstellenanlage oder den SBC nicht finden. Dies ist darauf zurückzuführen, dass ein Postfachserver alle VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs in einem Cache zwischenspeichert und die DNS-Auflösung nur erfolgt, wenn der Dienst neu gestartet wird oder die Konfiguration eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines SBC geändert wurde.


