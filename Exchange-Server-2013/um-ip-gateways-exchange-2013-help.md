---
title: 'UM-IP-Gateways: Exchange 2013 Help'
TOCTitle: UM-IP-Gateways
ms:assetid: 991d77e0-3995-44ab-bedf-52ff7a0301ab
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123890(v=EXCHG.150)
ms:contentKeyID: 50476295
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-IP-Gateways

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2014-06-24_

Ein Unified Messaging-IP-Gateway (UM) repräsentiert ein physisches VoIP-Gateway (Voice over IP), eine IP-Nebenstellenanlage oder SBC-Hardwaregerät (Session Border Controller). Ehe ein VoIP-Gateway, eine IP-Nebenstellenanlage oder ein SBC zum Annehmen eingehender Anrufe und zum Senden ausgehender Anrufe für Voicemailbenutzer genutzt werden kann, muss im Verzeichnisdienst ein UM-IP-Gateway erstellt werden.

**Inhalt**

Übersicht über UM-IP-Gateways

UM-IP-Gateways

IPv6-Unterstützung für UM-IP-Gateways

Aktivieren und Deaktivieren von UM-IP-Gateways

## Übersicht über UM-IP-Gateways

Ursprünglich bezeichnete *Gateway* ein physisches Gerät, über das zwei inkompatible Netzwerke verbunden werden. Bei Exchange Unified Messaging und in anderen Unified Messaging-Lösungen wird das VoIP-Gateway verwendet, um zwischen dem öffentlichen Telefonnetz/Time Division Multiplex (TDM) oder dem leitungsvermittelten Telefonnetz und einem IP- oder paketvermittelten Datennetzwerk zu übersetzen. Eine IP-Nebenstellenanlage übersetzt auch zwischen dem öffentlichen Telefonnetz und einem paketvermittelten Netzwerk. Bei Verwenden einer IP-Nebenstellenanlage ist deshalb kein VoIP-Gateway erforderlich. Ein VoIP-Gateway ist nur erforderlich, wenn Sie ein älteres Nebenstellenanlagengerät mit Ihrer UM-Bereitstellung verbinden.


> [!NOTE]
> Ein paketvermitteltes Netzwerk ist ein Netzwerk, in dem Pakete (Nachrichten oder Fragmente von Nachrichten) einzeln zwischen Geräten wie Routern, Switches, VoIP-Gateways, IP-Nebenstellenanlagen und SBCs geroutet werden. Dagegen richtet ein leitungsvermitteltes Netzwerk eine dedizierte Verbindung zwischen zwei Knoten zur ausschließlichen Verwendung für die Dauer der Kommunikation ein.



Exchange Unified Messaging basiert auf der Fähigkeit des VoIP-Gateways, TDM-Protokolle oder Protokolle für leitungsvermittelte Telefonie, wie z. B. ISDN (Integrated Services Digital Network) oder QSIG, aus einer Nebenstellenanlage in auf VoIP oder IP basierende Protokolle, wie z. B. SIP (Session Initiation Protocol), RTP (Realtime Transport Protocol) oder T.38 für die Faxübermittlung, in Echtzeit zu übersetzen.

IP-Nebenstellenanlagen werden auch genutzt, um ein leitungsvermitteltes Telefonnetz mit einem daten- oder paketvermittelten Netzwerk zu verbinden. Sie dienen auch zum Übersetzen leitungsvermittelter Protokolle in Protokolle, die auf VoIP oder IP basieren, z. B. SIP, RTP und SRTP (Secure RTPC).

SBCs (Session Border Controllers) unterscheiden sich leicht von VoIP-Gateways und IP-Nebenstellenanlagen. Anstatt ein leitungsvermitteltes Netzwerk mit einem paketvermittelten Netzwerk zu verbinden, dienen sie zum Verbinden zweier Datennetzwerke über ein öffentliches Netzwerk wie das Internet oder über eine private WAN-Verbindung. Beim Unified Messaging (UM) werden SBCs in einer Hybridbereitstellung von UM eingesetzt, bei der UM einige Komponenten verwendet, die lokal vorhanden sind, und andere nutzt, z. B. Postfächer, die sich in der Cloud befinden.

## VoIP-Gerätekonfigurationen

Zwar gibt es viele verschiedene Typen und Hersteller von Nebenstellenanlagen, VoIP-Gateways, IP-Nebenstellenanlagen und SBCs, doch gibt es im Wesentlichen drei Typen von VoIP-Gerätekonfigurationen:

  - **IP-Nebenstellenanlage**   Ein einzelnes Gerät, das zwischen dem öffentlichen Festnetz/TDM oder leitungsvermittelten Telefonnetz und einem IP- oder paketvermittelten Datennetzwerk übersetzt

  - **Nebenstellenanlage (älteres Modell) und VoIP-Gateway**   Zwei getrennte Komponenten, die gemeinsam zwischen dem öffentlichen Festnetz/TDM oder leitungsvermittelten Telefonnetz und einem IP- oder paketvermittelten Datennetzwerk übersetzen

  - **SBC**   Ein oder mehrere Geräte, die zwei Typen von IP-Netzwerken, z. B. ein lokales Netzwerk und ein Rechenzentrum, verbinden.

Zur Unterstützung von Unified Messaging werden ein oder beide Typen von IP/VoIP-Gerätekonfigurationen verwendet, wenn eine Telefonnetzinfrastruktur mit einer Datennetzwerkinfrastruktur oder eine lokale Bereitstellung mit einer UM-Bereitstellung in der Cloud verbunden werden.

## UM-IP-Gateways

Das UM-IP-Gateway enthält einen oder mehrere UM-Sammelanschlüsse und Konfigurationseinstellungen. UM-Sammelanschlüsse dienen zum Verbinden eines UM-IP-Gateways mit einem UM-Wählplan. Durch die Kombination des UM-IP-Gateways mit einem UM-Sammelanschluss wird eine Verknüpfung zwischen einem VoIP-Gateway, einer IP-Nebenstellenanlage bzw. einem SBC und einem UM-Wählplan eingerichtet. Durch Erstellen mehrerer UM-Sammelanschlüsse kann ein einzelnes UM-IP-Gateway mehreren UM-Wähleinstellungen zugeordnet werden.

Nach dem Erstellen eines UM-IP-Gateways senden die mit dem UM-IP-Gateway verbundenen Exchange-Server eine SIP-Anforderung vom Typ OPTIONS an das VoIP-Gateway, die IP-Nebenstellenanlage oder den SBC, um zu prüfen, ob das Gerät antwortet. Wenn das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC nicht auf die Anforderung antwortet, protokolliert ein Exchange-Server ein Ereignis mit der ID 1400, das besagt, dass die Anforderung keinen Erfolg hatte. Sollte dies geschehen, stellen Sie sicher, dass das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC verfügbar und online ist und dass eine ordnungsgemäße Unified Messaging-Konfiguration vorliegt.

Ein Postfachserver kommuniziert nur mit VoIP-Gateways, IP-Nebenstellenanlagen und SBCs, die als vertrauenswürdige SIP-Peers aufgeführt sind. Wenn in einigen Fällen zwei VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs für die Verwendung derselben IP-Adresse konfiguriert sind, wird ein Ereignis mit der ID 1175 protokolliert. Unified Messaging schützt vor nicht autorisierten Anforderungen, indem die interne URL des virtuellen Unified Messaging-Webdiensteverzeichnisses abgerufen wird, auf dem der Clientzugriffsserver installiert ist. Anschließend wird mithilfe dieser URL die Liste der FQDNs für die vertrauenswürdigen SIP-Peers erstellt. Wenn zwei FQDNs in dieselbe IP-Adresse aufgelöst werden, wird dieses Ereignis protokolliert.

## IPv6-Unterstützung für UM-IP-Gateways

Internetprotokoll, Version 6, (IPv6) ist die aktuelle Version des Internetprotokolls (IP). Mit IPv6 sollen zahlreiche der Defizite von IPv4, der vorherigen IP-Version, korrigiert werden. In lokalen und Hybridbereitstellungen von Microsoft Exchange Server 2010 wird IPv6 vollständig unterstützt, allerdings nur, wenn auch IPv4 verwendet wird.

In lokalen und Hybridbereitstellungen von Exchange 2013 stehen UM-bezogene Komponenten und sprachbezogene Dienste auf Clientzugriffs- und Postfachservern zur Verfügung. Da sich die UM-Architektur geändert hat und nun die UCMA-API 4.0 (Unified Communications Managed) erfordert, um sowohl IPv4 und IPv6 als auch andere Exchange-Funktionen zu unterstützen, unterstützen die Clientzugriffs- und Postfachserver mit Unified Messaging-Komponenten und -Diensten IPv6-Netzwerke vollständig und erfordern kein IPv4.

In lokalen, Hybrid- und Exchange Online-Bereitstellungen können sowohl Unternehmens- als auch Exchange Online-UM-Administratoren IPv6 verwenden, wenn Sie UM mit IPv6-fähigen Geräten verbinden, so z. B. Geräten wie Routern, IP-Gateways, IP-Nebenstellenanlagen und Servern mit Microsoft Office Communications Server 2007 R2 und Microsoft Lync. Zum Zweck der Interoperabilität und Abwärtskompatibilität kann stattdessen IPv4 ohne weitere Konfigurationsänderungen verwendet werden, wenn der Parameter *IPAddressFamily* für UM-IP-Gateways auf `Any` festgelegt ist.

Exchange UM muss weiter direkt mit SIP-Peers (VoIP-Gateways, IP-Nebenstellenanlagen und SBCs) kommunizieren, die IPv6 in ihrer Software oder Firmware möglicherweise nicht unterstützen. Wenn diese IPv6 nicht unterstützen, muss UM direkt mit SIP-Peers kommunizieren können, die IPv4 verwenden. Wird Voicemail gehostet, kommuniziert UM mit Telefonieanlagen über SBCs, Lync Server 2010 oder Lync Server 2013. In gehosteten Umgebungen können IPv6-SIP-fähige Clients wie SBCs und Server mit Lync bereitgestellt werden, um die Umwandlung von IPv6 in IPv4 durchzuführen.

Für lokale und Hybridbereitstellungen müssen Sie nach der Installation der Clientzugriffs- und Postfachserver sowie für Exchange Online UM-Bereitstellungen UM-IP-Gateways erstellen. Wenn Ihre UM-IP-Gateways IPv6 unterstützen müssen, führen Sie außerdem die folgenden Schritte aus:

1.  Erstellen Sie ein neues UM-IP-Gateway, oder konfigurieren Sie ein vorhandenes UM-IP-Gateway mit einer IPv6-Adresse für jedes IP-Gateway, jede IP-Nebenstellenanlage oder jeden SBC in Ihrem Netzwerk. Wenn Sie die erforderlichen UM-IP-Gateways erstellen und konfigurieren, müssen Sie die IPv6-Adresse oder den FQDN (Fully Qualified Domain Name) für das UM-IP-Gateway hinzufügen. Wenn Sie dem UM-IP-Gateway den FQDN hinzufügen, müssen Sie zuvor die richtigen DNS-Einträge erstellt haben, um den FQDN des UM-IP-Gateways in die IPv6-Adresse aufzulösen. Für ein vorhandenes UM-IP-Gateway können Sie das Cmdlet **Set-UMIPgateway** verwenden, um die IPv6-Adresse oder den FQDN zu konfigurieren.

2.  Konfigurieren Sie den Parameter *IPAddressFamily* für jedes UM-IP-Gateway. Damit das VoIP-Gateway IPv6-Pakete akzeptieren kann, müssen Sie das UM-IP-Gateway so einrichten, dass es sowohl IPv4- als auch IPv6-Verbindungen oder nur IPv6-Verbindungen akzeptiert, indem Sie das Cmdlet **Set-UMIPgateway** verwenden.

3.  Nach der Konfiguration Ihrer UM-IP-Gateways müssen Sie auch die VoIP-Gateways, IP-Nebenstellenanlagen und SBCs in Ihrem Netzwerk für die Unterstützung von IPv6 konfigurieren. Erkundigen Sie sich bei Ihrem Hardwareanbieter nach einer Liste der Geräte, die IPv6 unterstützen, und nach Informationen zu einer ordnungsgemäßen Konfiguration dieser Geräte.


> [!NOTE]
> Die maximale Anzahl von UM-IP-Gateways pro Wählplan beträgt 200. Wenn Sie mehr als 200 erstellen, wird der UM-Dienst nicht gestartet.



## Aktivieren und Deaktivieren von UM-IP-Gateways

Standardmäßig wird ein UM-IP-Gateway nach seiner Erstellung im aktivierten Zustand belassen. Das UM-IP-Gateway kann jedoch aktiviert oder deaktiviert werden. Wenn Sie ein UM-IP-Gateway deaktivieren, können Sie es so einrichten, dass alle Exchange-Server gezwungen werden, bestehende Anrufe abzubrechen. Alternativ können Sie es so einrichten, dass dem UM-IP-Gateway zugeordnete Exchange-Server gezwungen werden, neue vom VoIP-Gateway, von der IP-Nebenstellenanlage oder vom SBC eingehende Anrufe anzunehmen.

Wenn Sie Unified Messaging mit Office Communications Server R2 oder Microsoft Lync Server integrieren, dürfen Sie nur einem UM-IP-Gateway erlauben, ausgehende Anrufe für Benutzer zu erstellen, und ausgehende Anrufe auf allen anderen UM-IP-Gateways deaktivieren, die Ihren SIP-URI-Wählplänen zugeordnet sind. Verwenden Sie entweder die Shell oder Exchange-Verwaltungskonsole, um ausgehende Anrufe zu deaktivieren.

Entscheiden Sie sich bei der Auswahl des UM-IP-Gateways, für das ausgehende Anrufe für lokale und Hybridbereitstellungen zugelassen werden, für dasjenige, das voraussichtlich den meisten Datenverkehr verarbeiten muss. Verhindern Sie, dass ausgehender Datenverkehr über ein IP-Gateway geleitet wird, das über eine Verbindung zu einem Pool mit Lync Server-Directors verfügt. Dies ist erforderlich, um sicherzustellen, dass ausgehende Anrufe externer Benutzer durch einen Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird (z. B. in "Wiedergabe über Telefon"-Szenarien) zuverlässig durch die Firewall des Unternehmens geleitet werden.

