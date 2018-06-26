---
title: 'IPv6-Unterstützung in Unified Messaging: Exchange 2013 Help'
TOCTitle: IPv6-Unterstützung in Unified Messaging
ms:assetid: 91242c85-ce4e-422a-954e-ab623d3d6939
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150536(v=EXCHG.150)
ms:contentKeyID: 50476182
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# IPv6-Unterstützung in Unified Messaging

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Internetprotokoll, Version 6, (IPv6) ist die aktuelle Version des Internetprotokolls (IP). Mit IPv6 sollen zahlreiche der Defizite von IPv4, der vorherigen IP-Version, korrigiert werden. In Microsoft Exchange Server 2010 wird IPv6 nur dann unterstützt, wenn auch IPv4 verwendet wird. Eine reine IPv6-Exchange-Umgebung wird nicht unterstützt. Die Verwendung von IPv6-Adressen und IP-Adressbereichen wird nur unterstützt, wenn auf dem Computer mit Exchange 2010 sowohl IPv6 als auch IPv4 aktiviert sind und wenn das Netzwerk beide IP-Adressversionen unterstützt. Da es sich bei IPv4 und IPv6 um vollständig unterschiedliche Protokolle handelt, kann ein IPv4-Netzwerk jedoch nicht direkt mit einem IPv6-Netzwerk kommunizieren und umgekehrt. Um dieses Manko auszugleichen, müssen Netzwerkadministratoren Geräte wie Router bereitstellen, die Informationen zwischen IPv4- und IPv6-Netzwerken weiterleiten können. Wenn Exchange 2010 mit IPv4 und IPv6 bereitgestellt wurde, können alle Serverrollen außer Unified Messaging (UM) Daten an Geräte, Server und Clients senden bzw. von diesen empfangen, die IPv6-Adressen verwenden. Mit Exchange 2013 ist Unified Messaging keine separate Serverrolle mehr, wie die Serverrollen Transport, Clientzugriff und Postfach in Exchange 2007 und Exchange 2010. Komponenten im Zusammenhang mit UM sowie Sprachdienste werden ausschließlich auf Clientzugriffs- und Postfachservern ausgeführt.

Da die UM-Architektur in Exchange 2013 geändert wurde und nun die Unified Communications Managed API (UCMA) v4.0 erfordert, um IPv4 und IPv6 sowie andere Exchange-Funktionen zu unterstützen, unterstützen Clientzugriffs- und Postfachserver mit Unified Messaging-Komponenten und -Diensten IPv6-Netzwerke vollständig.

## IPv6-Unterstützung

Seit Exchange 2010 Service Pack 1 (SP1) verwendete die Unified Messaging-Serverrolle UCMA 2.0 für den zugrunde liegenden SIP-Signalverkehr (Session Initiation Protocol) und die Sprachverarbeitung. UCMA 2.0 ist die wichtigste Komponente für Sprachfunktionen in UM. UCMA 2.0 umfasst einen SIP-Stapel, einen Medienstapel sowie Sprachmodule für die automatische Spracherkennung (Automatic Speech Recognition, ASR) und die über TTS (Text-to-Speech) generierte Sprachsynthese.

In Exchange 2010 musste ein dualer Stack (IPv4 und IPv6) für alle Serverrollen ausgeführt werden außer für UM, da UM zwar UCMA 2.0 erforderte, aber nur IPv4 und nicht IPv6 unterstützte. In Exchange 2013 wird UCMA 4.0 von UM verwendet und ist erforderlich, um Exchange 2013 auf Clientzugriffs- und Postfachservern zu installieren. UCMA 4.0 ist erforderlich, um neue Funktionen und IPv6 zu unterstützen.

Einige der Gründe, aus denen UM jetzt UCMA 4.0 zur Unterstützung der neuen Funktionen in Exchange 2013 (einschließlich IPv6) verwendet, sind folgende:

  - Einige Behörden erfordern IPv6-Unterstützung für Produkte, die sie verwenden.

  - UM erfordert jetzt Kompatibilität mit Hardwaregeräten wie Routern, IP-Gateways, IP-Nebenstellenanlagen und Session Border Controllern (SBCs), auf denen ein dualer Stack (IPv4 und IPv6) oder nur IPv6 ausgeführt wird.

  - In Exchange 2013 wird der Microsoft Exchange Unified Messaging-Dienst auf dem Postfachserver ausgeführt und der Microsoft Exchange Unified Messaging-Anrufrouterdienst auf dem Clientzugriffsserver. Für die Serverrollen Postfach und Clientzugriff in Exchange 2013 sind IPv4 und IPv6 erforderlich.

  - Mithilfe von Onlinediensten können Clients wahlweise über IPv4 oder über IPv6 eine Verbindung mit ihrem Dienst herstellen.

  - Öffentlicher IPv4-Adressraum wird knapp. Für Exchange Server 2013 Enterprise ist dies im Hinblick auf UM nicht wirklich ein Problem, da UM stets mit internen SIP-Peers kommuniziert, die mit einem privaten IPv4-Adressraum bereitgestellt werden können. Für UM in Hosted Exchange müssen die Geräte des Kunden jedoch gehostetes UM mit IPv4 und IPv6 unterstützen.

Mit Ausnahme von UM und einem kleinen Teil von Transport kann Exchange 2013 Verbindungen mit Exchange 2010-Servern in einer Organisation herstellen, wenn entweder in Clientzugriffsserver oder ein Postfachserver im Modus für dualen Stack ausgeführt wird, wobei IPv4 und IPv6 aktiviert sind. Dies bedeutet, dass Kunden Exchange 2013 auf Computern installieren können, auf denen sowohl Adressen des IPv4-Stacks als auch des IPv6-Stacks konfiguriert sind. So können IPv6-Clients und andere Exchange-Server, einschließlich Exchange Server 2010, direkte Verbindungen mit Exchange 2013 herstellen.

UM funktioniert auf Windows-Servern, die im Modus für dualen Stack ausgeführt werden. Der Grund ist, dass Protokolle wie HTTP den Transporttyp ignorieren und UM Voice-over-IP (VoIP)-Protokolle verwendet (einschließlich SIP/RTP/STUN/TURN/ICE), zwischen denen keine gegenseitigen Abhängigkeiten bestehen. Hierzu gehört die Medienaushandlung (RTP/SRTP), bei der UM eine Liste von IP-Adressen ankündigt und für SIP-Peers bekanntgibt, wie IP-Gateways, IP-Nebenstellenanlagen oder SBCs.

## Was bedeutet es, IPv6 für UM zu unterstützen?

Um Exchange 2013 UM für die Unterstützung von IPv6 zu aktivieren, müssen Administratoren für Unternehmens- und Online-UM IPv6 nutzen können, wenn sie eine Verbindung von UM zu IPv6-fähigen Geräten herstellen. Dazu können Geräte gehören wie Router, IP-Gateways, IP-Nebenstellenanlagen sowie Server mit Office Communications Server 2007 R2 und Microsoft Lync. Wenn IPv6 jedoch aus Gründen der Interoperabilität und Abwärtskompatibilität mit früheren Exchange-Versionen nicht zur Verfügung steht, müssen Administratoren keine zusätzlichen Konfigurationsänderungen durchführen, und IPv4 kann stattdessen verwendet werden.

In Exchange 2013 Enterprise muss UM direkt mit SIP-Peers (IP-Gateways, IP-Nebenstellenanlagen und SBCs) kommunizieren, deren Software oder Firmware IPv6 möglicherweise nicht unterstützt. Daher muss UM direkt mit SIP-Peers kommunizieren können, die IPv4 und vor allem IPv6 unterstützen. In Hosted Exchange 2013 kommuniziert UM mit Kundengeräten über SBCs, Lync Server 2010 oder Lync Server 15. In gehosteten Exchange 2013-Umgebungen können IPv6 SIP-fähige Clients wie SBCs und Lync-Server bereitgestellt werden und die Konvertierung von IPv6 zu IPv4 verarbeiten.

## UM-Geräteunterstützung für IPv6

Da Postfach- und Clientzugriffsserver von Exchange 2013, auf denen UM-Komponenten und -Dienste ausgeführt werden, IPv6 unterstützen, müssen Anbieter von IP-Gateways, IP-Nebenstellenanlagen und SBC ebenfalls IPv6 unterstützen können. Es gibt einige Probleme bei der Geräteunterstützung für IPv6:

  - Es gibt IP-Gateways, IP-Nebenstellenanlagen und SBCs, die möglicherweise IPv6 unterstützen können, aber noch nicht mit IPv6 und UM getestet wurden. Diese Unterstützung wird möglicherweise zukünftig hinzugefügt; dies hängt jedoch vom Hardwareanbieter ab.

  - Einige IP-Gateways bieten zurzeit keine IPv6-Unterstützung.

  - Einige SBCs verfügen über IPv4-IPv6-Funktionalität, können jedoch zurzeit nicht für UM verwendet werden, weil sie nicht SRTP (Secure Real-time Transport Protocol)/SDES (Session Description Protocol Security) unterstützen.

  - Hierbei handelt es sich um IP-Nebenstellenanlagen, die einen dualen Stack sowie reines IPv6 nicht unterstützen; die Zusammenarbeit dieser Geräte mit Exchange 2013 wure jedoch noch nicht getestet.

Zurzeit ist UCMA 4.0 für IPv6 aktiviert, kann also IPv6-Verbindungen annehmen, wobei auch IPv4 angenommen werden kann, wenn der duale Modus verwendet wird oder wenn ausgehende Verbindungen hergestellt werden. Bei der Ausführung im dualen Modus können IPv4-Verbindungen hergestellt werden, wenn sie benötigt werden, um Verbindungen zu früheren Versionen von Exchange UM herzustellen. Bei Lync-Installationen wird dies von Lync Server durchgeführt. Diese Lösung bezieht in der aktuellen Version von Exchange Server die Versionsinformationen aus Active Directory. Damit herkömmliche Telefoniegeräte, einschließlich IP-Gateways, IP-Nebenstellenanlagen und SBCs, IPv6-Verbindungen ebenso wie IPv4 unterstützen können, müssen sie beide Arten von Verbindungen abfragen. Die Ursache hierfür ist, dass jeder SIP-Peer in der Lage sein muss, beide Arten von Verbindungen zu akzeptieren, um die Abwärtskompatibilität mit früheren Versionen von Exchange UM zu ermöglichen. Dies ist auch notwendig um beide Arten von Verbindungen selbst initiieren zu können.

## Konfiguration von UM zur Unterstützung von IPv6

Nach dem Installieren der Clientzugriffs- und Postfachserver müssen Sie Unified Messaging-Wählpläne, automatische Telefonzentralen, IP-Gateways und Sammelanschlüsse erstellen. Damit UM IPv6 unterstützen kann, müssen Sie:

  - Erstellen Sie ein neues UM-IP-Gateway, oder konfigurieren Sie ein vorhandenes UM-IP-Gateway mit einer IPv6-Adresse für jedes IP-Gateway, jede IP-Nebenstellenanlage oder jeden SBC in Ihrem Netzwerk. Wenn Sie die erforderlichen UM-IP-Gateways erstellen und konfigurieren, müssen Sie die IPv6-Adresse oder den FQDN (Fully Qualified Domain Name) für das UM-IP-Gateway hinzufügen. Wenn Sie dem UM-IP-Gateway den FQDN hinzufügen, müssen Sie zuvor die richtigen DNS-Einträge erstellt haben, um den FQDN des UM-IP-Gateways in die IPv6-Adresse aufzulösen. Für ein vorhandenes UM-IP-Gateway können Sie das Cmdlet **Set-UMIPgateway** verwenden, um die IPv6-Adresse oder den FQDN zu konfigurieren. Nach dem Erstellen oder Konfigurieren der UM-IP-Gateways können Sie das Cmdlet **Get-UMIPgateway** verwenden, um die Eigenschaften des UM-IP-Gateways anzuzeigen und sicherzustellen, dass die IPv6-Einstellungen richtig sind.

  - Konfigurieren Sie den Parameter *IPAddressFamily* für jedes UM-IP-Gateway. Damit das IP-Gateway IPv6-Pakete akzeptieren kann, müssen Sie festlegen, dass das UM-IP-Gateway sowohl IPv4- als auch IPv6-Verbindungen akzeptiert. Verwenden Sie hierzu das Cmdlet **Set-UMIPgateway**, und legen Sie den Parameter *IPAddressFamily* auf einen der folgenden Werte fest:
    
      - *IPv4* – Dies ist der Standardwert, der verwendet wird, wenn kein anderer Wert konfiguriert ist.
    
      - *IPv6* – Dies ermöglicht die Verwendung von IPv6. IPv4 wird jedoch nicht verwendet.
    
      - *Any* – Dies ermöglicht die Verwendung von IPv6; wenn das Gerät jedoch IPv6 nicht unterstützt, wird stattdessen IPv4 verwendet.

  - Nach dem Konfigurieren der UM-IP-Gateways müssen Sie auch die IP-Gateways, IP-Nebenstellenanlagen und SBCs in Ihrem Netzwerk konfigurieren, um IPv6 zu unterstützen. Erkundigen Sie sich bei Ihrem Hardwareanbieter nach einer Liste der Geräte, die IPv6 unterstützen, und nach Informationen zu einer ordnungsgemäßen Konfiguration dieser Geräte.

  - Optional müssen Sie möglicherweise festlegen, dass die Clientzugriffs- und Postfachserver IPv6-Datenverkehr akzeptieren, wenn für einen der Server nur das Empfangen von IPv4-Datenverkehr festgelegt ist. Die Standardeinstellung für Clientzugriffsserver mit dem Microsoft Exchange Unified Messaging-Anrufrouterdienst und für Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst ist jedoch das Akzeptieren von IPv4- und IPv6-Datenverkehr. Details zum Konfigurieren der IPv6-Einstellungen auf Clientzugriffs- und Postfachservern finden Sie unter [Set-UMCallRouterSettings](https://technet.microsoft.com/de-de/library/jj215758\(v=exchg.150\)) und [Set-UMService](https://technet.microsoft.com/de-de/library/jj552412\(v=exchg.150\)).
    
    Auf Clientzugriffs- und Postfachservern müssen möglicherweise die folgenden beiden Parameter konfiguriert werden, um IPv6 zu unterstützen: *IPAddressFamily* und *IPAddressFamilyConfigurable*. Damit ein Clientzugriffs- und ein Postfachserver IPv6-Pakete akzeptieren können, müssen Sie entweder festlegen, dass beide Server IPv4- und IPv6-Verbindungen akzeptieren oder dass beide Server nur IPv6-Verbindungen akzeptieren. Damit der Parameter *IPAddressFamily* konfiguriert werden kann, muss der Parameter *IPAddressFamilyConfigurable* auf `$true` festgelegt sein.

## Logik der UM-IP-Adressierung

Die Logik der IPv6-Unterstützung für UM in Exchange 2013 lautet wie folgt:

  - Clientzugriffs- und Postfachserver fragen sowohl IPv4- als auch IPv6-Schnittstellen ab, wenn der duale Stack aktiviert ist und wenn für die Server *IPv6* oder *Any* festgelegt ist. Andernfalls wird nur IPv4 verwendet.

  - Für ausgehende Anrufe verwendet UM den dualen Modus, wenn der Parameter *IPAddressFamily* für die UM-IP-Gateways, Clientzugriffs- und Postfachserver auf *IPv6* oder *Any* festgelegt ist. Andernfalls wird nur IPv4 verwendet.

Bei der Durchführung ausgehender Anrufe im dualen Modus gilt Folgendes, wenn der Parameter *IPAddressFamily* auf *IPv6* oder *Any* festgelegt ist:

  - UCMA ruft eine Liste von Adressen im FQDN für einen SIP-Peer ab, der erreicht werden soll.

  - UCMA versucht ggf. alle IPv6-Adressen.

  - Wenn UCMA ermittelt, dass eine Adresse nicht verfügbar ist, wird die Adresse in eine Liste aufgenommen und in einem konfigurierten Intervall nicht noch einmal versucht. Dadurch wird verhindert, dass UM unnötige Wiederholungen für bekanntermaßen nicht verfügbare Adressen durchführt.

  - Wenn keine IPv6-Adressen zur Verfügung stehen, verwendet UCMA IPv4-Adressen in der Adressenliste für SIP-Peers.

