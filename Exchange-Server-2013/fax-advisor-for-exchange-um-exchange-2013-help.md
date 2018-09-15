---
title: 'Faxratgeber für Exchange UM: Exchange 2013 Help'
TOCTitle: Faxratgeber für Exchange UM
ms:assetid: 928a466d-cc0c-4160-bd4c-f0fc76b038d4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364747(v=EXCHG.150)
ms:contentKeyID: 52062760
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Faxratgeber für Exchange UM

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Unified Messaging (UM) verwendet zertifizierte Faxpartnerlösungen, um erweiterte Faxfunktionalität bereitzustellen, z. B. ausgehende Faxe oder Faxrouting. Benutzerkonten sind nicht standardmäßig für das Zulassen eingehender Faxnachrichten und die anschließende Zustellung an einen UM-aktivierten Benutzer konfiguriert. Exchange-Server senden die Faxanforderungen an eine zertifizierte Faxpartnerlösung. Der Server des Faxpartners empfängt die Faxdaten und sendet sie dann in einer E-Mail-Nachricht, in die das Fax als TIF-Anlage eingeschlossen ist, an das Empfängerpostfach. Weitere Informationen finden Sie unter [Aktivieren von Voicemailbenutzern für den Faxempfang](enable-voice-mail-users-to-receive-faxes-exchange-2013-help.md).


> [!IMPORTANT]
> Alle Kunden, die eine Bereitstellung von Unified Messaging planen, sollten einen Unified Messaging-Spezialisten zu Rate ziehen. Ein Unified Messaging-Spezialist unterstützt Sie beim Sicherstellen, dass der Übergang von einem älteren Voicemailsystem zu Unified Messaging reibungslos verläuft. Für die Durchführung einer neuen Bereitstellung oder für das Upgrade eines älteren Voicemailsystems sind umfassende Kenntnisse zu Nebenstellenanlagen und Unified Messaging erforderlich. Weitere Informationen zur Kontaktaufnahme mit einem Unified Messaging-Spezialisten finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=262708">Microsoft Exchange Server 2013 Unified Messaging-Spezialisten</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=261951">Microsoft Pinpoint für Unified Messaging</A>.



## Faxpartnerprogramm für Exchange Unified Messaging

Um Faxpartner mit zertifizierter Interoperabilität mit Exchange UM zu werden, muss der Partner die in der Interoperabilitätsspezifikation für Faxpartner (Fax Partner Interoperability Specification) enthaltenen Anforderungen implementieren, und die Faxlösung muss von einem unabhängigen Zertifikatanbieter zertifiziert werden. Wenn Sie an weiteren Informationen zur Zertifizierung eines Faxprodukts für die Zusammenarbeit mit Exchange Unified Messaging interessiert sind, senden Sie eine Anforderung an [Faxpartner für Exchange Unified Messaging](mailto:fax-part@microsoft.com).

## Als interoperabel mit Unified Messaging zertifizierte Faxpartnerlösungen

Wenn Sie Exchange Unified Messaging bereits bereitgestellt haben und auf der Suche nach einem Faxpartner sind, der eingehende Faxe in Ihrer Organisation ermöglicht, finden Sie weitere Informationen unter [Microsoft Pinpoint für Faxpartner](https://go.microsoft.com/fwlink/p/?linkid=190238). Diesen Softwareherstellern wurde Interoperabilität mit Exchange Server zertifiziert, und sie stellen zertifizierte Softwarelösungen für Unified Messaging bereit.

## Unterstützung von VoIP, Mediengateways und IP-Nebenstellenanlagen

Bei der Konfiguration von VoIP-Gateways in Ihrer Organisation handelt es sich um eine schwierige Bereitstellungsaufgabe, deren erfolgreicher Abschluss Voraussetzung dafür ist, dass Exchange Unified Messaging erfolgreich für eingehende Faxnachrichten bereitgestellt werden kann. Unter [Telefonieratgeber für Exchange 2013](https://technet.microsoft.com/de-de/library/Ee364753(v=EXCHG.150)) finden Sie Antworten auf Ihre Fragen und die neuesten Informationen zur Konfiguration von VoIP-Gateways. Unter [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](https://technet.microsoft.com/de-de/library/JJ938013(v=EXCHG.150)) finden Sie Hinweise zur VoIP-Gatewaykonfiguration und Dateien, die Sie für die Zusammenarbeit mit Exchange Unified Messaging ordnungsgemäß für die VoIP-Gateways, IP-Nebenstellenanlagen und SBCs in Ihrer Organisation konfigurieren müssen.

Das Testen der Interoperabilität von Exchange Unified Messaging mit VoIP-Gateways wurde in das Microsoft Unified Communications Open Interoperability Program integriert. Weitere Informationen hierzu finden Sie unter [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkid=140722).

Das Qualifizierungsprogramm für VoIP-Gateways und IP-Nebenstellenanlagen gemäß dem [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkid=140722) gewährleistet eine nahtlose Setup- und Supporterfahrung für unsere Kunden, wenn sie geeignete Telefoniegateways und IP-Nebenstellenanlagen mit Microsoft Unified Communications-Software verwenden.


> [!IMPORTANT]
> Das Senden und Empfangen von Faxen mit T.38 oder G.711 wird nicht in Umgebungen unterstützt, in denen Unified Messaging und Communications Server 2007 R2 oder Microsoft Lync Server integriert sind.



## Bereitstellen und Konfigurieren von Faxfunktionen

UM leitet eingehende Faxanrufe an eine dafür vorgesehene Faxpartnerlösung weiter, die dann die Faxverbindung mit dem Faxabsender aufbaut und die Nachricht für den UM-aktivierten Benutzer empfängt. Damit UM-aktivierte Benutzer Faxnachrichten in ihrem Postfach empfangen können, müssen Sie den Faxpartnerserver konfigurieren. Anschließend müssen Sie die UM-Wählpläne und UM-Postfachrichtlinien konfigurieren sowie UM-aktivierte Benutzer für den Faxempfang aktivieren. Weitere Informationen finden Sie unter [Einrichten von eingehenden Faxen](setting-up-incoming-faxing-exchange-2013-help.md).

