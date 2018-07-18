---
title: 'UM-Dienste: Exchange 2013 Help'
TOCTitle: UM-Dienste
ms:assetid: f36835f2-1e5f-4e5a-88bc-0672af1e3498
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125191(v=EXCHG.150)
ms:contentKeyID: 50554941
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# UM-Dienste

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-18_

Clientzugriffsserver mit dem Microsoft Exchange Unified Messaging-Anrufrouterdienst sowie Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst ermöglichen die Bereitstellung von Unified Messaging (UM)- und Voicemailfunktionen für die Benutzer in Ihrer Organisation.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit UM-Diensten gibt? Weitere Informationen finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

**Inhalt**

Client Access and Mailbox servers

Server configuration settings

Server operation

## Clientzugriffs- und Postfachserver

In Exchange 2013 werden die Serverrollen in Exchange 2007 und Exchange 2010 zu zwei Servertypen kombiniert, und alle Komponenten oder Dienste dieser Serverrollen werden auf demselben physischen Server oder auf zwei getrennten Servern ausgeführt – dem Clientzugriffs- und dem Postfachserver.

Im neuen Modell ist der Clientzugriffsserver für AutoErmittlung, SSL (Secure Sockets Layer), Authentifizierung, Umleitung und Proxyfunktionen zuständig. Der Clientzugriffsserver ist der Einstiegspunkt für alle eingehenden Anrufe oder SIP-Anforderungen (Session Initiation Protocol) für Unified Messaging (UM). Die Routinglogik und SIP REDIRECT werden als Dienst implementiert, der automatisch auf einem Clientzugriffsserver integriert ist. Dieser Dienst wird als Microsoft Exchange Unified Messaging-Anrufrouterdienst bezeichnet. Er wird auf allen Clientzugriffsservern in Ihrer Organisation ausgeführt.

Wenn ein Clientzugriffsserver eine SIP INVITE-Anforderung für einen eingehenden Anruf empfängt, leitet der Microsoft Exchange Unified Messaging-Anrufrouterdienst den eingehenden Anruf an den Postfachserver um. Anschließend wird ein Medienkanal (RTP oder SRTP) zwischen VoIP-Gateway, IP-Nebenstellenanlage oder SBC (Session Border Controller) und dem Postfachserver eingerichtet, der das Postfach des Benutzers hostet. Obwohl der Clientzugriffsserver als SIP-Redirector fungiert, verarbeitet er ausschließlich SIP-Anforderungen von VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs. Er empfängt keinen Mediendatenverkehr. RTP- oder SRTP.Mediendatenverkehr wird ausschließlich zwischen dem Postfachserver und SIP-Peers wie z. B. VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs übergeben. Wenn Sie Exchange 2013 und UM bereitstellen, müssen Sie Ihre VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs so konfigurieren, dass sie auf die installierten Clientzugriffsserver zeigen, damit eingehende Anrufe für UM ordnungsgemäß weitergeleitet werden.

In Exchange 2013 übernimmt der Postfachserver dieselben Prozesse wie die Unified Messaging-Serverrolle in Exchange 2007 und Exchange 2010. Auf dem Postfachserver werden sowohl der Microsoft Exchange Unified Messaging-Dienst als auch UM-Arbeitsprozesse ausgeführt.

Nachdem Sie Ihre Clientzugriffs- und Postfachserver installiert und Unified Messaging bereitgestellt haben, müssen Sie UM-Wählplänen keine Clientzugriffs- oder Postfachserver zuordnen. Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe und bestimmen anschließend Benutzer mithilfe von UM-Wählplänen.

Wenn Sie Unified Messaging jedoch mit Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren, werden sowohl die SIP- als auch RTP- und SRTP-Medienkanäle für eingehende Anrufe von Lync-Servern und Postfachserver verarbeitet. In einer integrierten Lync-Umgebung gibt es keine VoIP-Gateways, IP-Nebenstellen oder SBCs. Gegenüber Lync ist der Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst lediglich ein Exchange 2010 UM-Server. Clientzugriffs- und Postfachserver gelten als vertrauenswürdige Peers, da beide Server einem SIP-Wählplan hinzugefügt werden müssen. Lync leitet den eingehenden Anruf mit der Komponente für das eingehende Routing weiter, die SIP zur Kommunikation mit dem Clientzugriffsserver verwendet und den Anruf an einen Postfachserver weiterleitet.

Zurück zum Seitenanfang

## Serverkonfigurationseinstellungen

Alle UM-Komponenten und Konfigurationseinstellungen, die für einen einzelnen Computer mit der Unified Messaging-Serverrolle in Exchange 2010 galten, sind weiterhin in Exchange 2013 verfügbar. Einige Komponenten und Konfigurationseinstellungen befinden sich jedoch auf einem Clientzugriffsserver, während andere auf einem Postfachserver verfügbar sind. In einigen Fällen steht dieselbe Einstellung auf beiden Servern zur Verfügung. In der folgenden Liste werden die Parameter und Einstellungen aufgeführt, die sowohl auf einem Clientzugriffsserver als auch auf einem Postfachserver zur Verfügung stehen.

  - \[-DialPlans \<MultiValuedProperty\>\]

  - \[-MaxCallsAllowed \<Int32\>\]

  - \[-SipTcpListeningPort \<Int32\>\]

  - \[-SipTlsListeningPort \<Int32\>\]

  - \[-Status \<Enabled | Disabled | NoNewCalls\>\]

  - \[-UMStartupMode \<TCP | TLS | Dual\>\]

Für den Postfachserver verwenden Sie die Cmdlets **Set-UMService**, **Get-UMService**, **Enable-UMService** und **Disable-UMService**, um UM-Eigenschaften für den Microsoft Exchange Unified Messaging-Dienst anzuzeigen oder zu konfigurieren. Ein anderer Satz mit Cmdlets, **Set-UMCallRouterSettings** und **Get-UMCallRouterSettings**, wird zur Anzeige und Konfiguration der Eigenschaften für den Microsoft Exchange Unified Messaging-Anrufrouterdienst auf einem Clientzugriffsserver verwendet. Auf diese Weise wird sichergestellt, dass die vorhandenen Cmdlets **Get-UMServer**, **Set-UMServer**, **Enable-UMServer** und **Disable-UMServer** aus Exchange 2007 und Exchange 2010 in einer Koexistenzumgebung mit Exchange 2013-Postfachservern weiterhin funktionieren. Außerdem wird gewährleistet, dass die Cmdlets auch funktionieren, wenn Postfach- und Clientzugriffsserver auf demselben oder unterschiedlichen Computern installiert sind.

Zurück zum Seitenanfang

## Serverbetrieb

Nach ihrer Installation werden Clientzugriffs- und Postfachserver automatisch aktiviert, damit sie ein- und ausgehende Anrufe tätigen und Voicemailnachrichten an die vorgesehenen Empfänger in Ihrer Exchange-Organisation weiterleiten können.

Sie können dem Microsoft Exchange Unified Messaging-Dienst auf einem Postfachserver oder dem Microsoft Exchange Unified Messaging-Anrufrouterdienst auf einem Clientzugriffsserver erlauben, neue Anrufe entgegenzunehmen, oder diese daran hindern. Standardmäßig nimmt ein Postfach- oder Clientzugriffsserver nach seiner Installation Anrufe an. Mit dem Cmdlet **Set-ServerComponentState** können Sie den Clientzugriffsserver für das Annehmen von Sprach-, Fax- und Outlook Voice Access-Anrufen sowie von Anrufen der automatischen Telefonzentrale einrichten.

Durch Konfigurieren des Wartungsmodus für einen Exchange 2013-Postfach- oder Clientzugriffsserver können Sie den Server außer Dienst nehmen. Ein außer Dienst genommener Postfachserver hostet keine aktiven Datenbanken, weist leere Transportwarteschlagen auf und kann keine eingehenden Anrufe von Clientzugriffsservern, VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder Session Border Controller (SBCs) annehmen. Ein außer Dienst genommener Clientzugriffsserver kann keine eingehenden Anrufe von VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder SBCs annehmen.

In Exchange 2007 und Exchange 2010 gab es einen Statusparameter, mit dem der Betriebsstatus eines Unified Messaging-Servers gesteuert werden konnte. In Exchange 2013 steht zu diesem Zweck für das Cmdlet **Set-UMService** für einen Postfachserver oder das Cmdlet **Set-UMCallRouterSettings** für einen Clientzugriffsserver kein Statusparameter zur Verfügung.

Wenngleich Clientzugriffs- und Postfachserver nach ihrer Installation den Status "Aktiviert" haben, können beide Server eingehende Anrufe an UM-aktivierte Benutzer erst dann ordnungsgemäß verarbeiten und weiterleiten, nachdem ein UM-Wählplan mindestens einem UM-IP-Gateway zugeordnet wurde.

Nachdem Verbinden eines Wählplans mit einem UM-IP-Gateway können Clientzugriffs- und Postfachserver alle UM-IP-Gateways bestimmen, die dem UM-Wählplan und VoIP-Gateways, IP-Nebenstellenanlagen und SBCs zugeordnet sind. Um Konfigurationsänderungen an UM-Wähleinstellungen oder UM-IP-Gateways zu erkennen und zu bestimmen, überprüfen Clientzugriffs- und Postfachserver die Konfiguration alle 10 Minuten.

Wenn das UM-IP-Gateway Konfigurationsänderungen erkennt, reagieren Clientzugriffs- und Postfachserver entsprechend und beginnen mit der Verwendung bzw. beenden die Verwendung der entsprechenden VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs. Sobald Clientzugriffs- und Postfachserver eingehende Anrufe für Benutzer beantworten, die einem UM-Wählplan zugeordnet sind, und die Kommunikation mit VoIP-Gateways, IP-Nebenstellenanlagen und SBCs ordnungsgemäß erfolgt, können Sie verschiedene Diagnosen durchführen. Mit ihrer Hilfe können Sie prüfen, ob die Komponenten ordnungsgemäß funktionieren und die Konnektivität zwischen den Exchange-Servern und VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs wie gewünscht ist.

Zurück zum Seitenanfang

