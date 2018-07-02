---
title: 'Serverrollen in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Serverrollen in Exchange-Hybridbereitstellungen
ms:assetid: 7a7eaf17-d2b0-4d62-90a2-45a0d2faca54
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659051(v=EXCHG.150)
ms:contentKeyID: 50477183
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Serverrollen in Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

Sie können anhand von Exchange 2013 und Exchange 2016 Hybridbereitstellungen konfigurieren. Die zum Unterstützen einer Hybridbereitstellung zu konfigurierenden Rollen hängen von der von Ihnen verwendeten Version von Exchange ab.

## Exchange 2016-Hybridbereitstellung

Wenn Sie eine Hybridbereitstellung in einer Exchange 2016-Organisation konfigurieren, müssen Sie keine zusätzlichen Exchange-Server in Ihrer vorhandenen Exchange-Organisation installieren. Postfachserver koordinieren die Kommunikation zwischen der vorhandenen Exchange 2016-Organisation und der Exchange Online-Organisation. Diese Kommunikation beinhaltet auch den Nachrichtentransport zwischen der lokalen und der Exchange Online-Organisation sowie Messagingfunktionen. Um die Zuverlässigkeit und die Verfügbarkeit der Funktionen der hybriden Bereitstellung zu verbessern, wird dringend empfohlen, mehrere Exchange-Server in der lokalen Organisation zu installieren.

Exchange 2016 verfügt nur über eine erforderliche Serverrolle, die Postfachrolle. Neben dem Hosting lokaler Empfängerpostfächer führt die Postfachrolle alle zur Unterstützung einer Hybridbereitstellung mit Exchange Online erforderlichen Funktionen. Dies beinhaltet die Verarbeitung sicherer E-Mail-Nachrichten, die zwischen der lokalen und der Exchange Online-Organisation gesendet werden, sowie die Verarbeitung von Transportregeln, Journalingrichtlinien und die Nachrichtenübermittlung an Benutzerpostfächer in Hybridbereitstellungen. Alle Features für Clientkonnektivität und Organisationsbeziehung wie Freigabe von Frei/Gebucht-Informationen werden auch vom Postfachserver verarbeitet.

Weitere Informationen zur Exchange 2016-Kapazitätsplanung finden Sie unter [Dimensionierung von Exchange 2016-Bereitstellungen](http://go.microsoft.com/fwlink/p/?linkid=301990).

## Exchange 2013-Hybridbereitstellung

Wenn Sie eine Hybridbereitstellung in einer Exchange 2013-Organisation konfigurieren, müssen Sie keine zusätzlichen Exchange-Server in Ihrer vorhandenen Exchange-Organisation installieren. Clientzugriffs- und Postfachserver koordinieren die Kommunikation zwischen der vorhandenen Exchange 2013-Organisation und der Exchange Online-Organisation. Diese Kommunikation beinhaltet auch den Nachrichtentransport zwischen der lokalen und der Exchange Online-Organisation sowie Messagingfunktionen. Um die Zuverlässigkeit und die Verfügbarkeit der Funktionen der hybriden Bereitstellung zu verbessern, wird dringend empfohlen, mehrere Exchange-Server in der lokalen Organisation zu installieren.

Im Folgenden können Sie sich einen raschen Überblick über die Exchange 2013-Serverrollen in einer Hybridbereitstellung verschaffen:

  - **Clientzugriffs-Serverrolle**   Über die Clientzugriffs-Serverrolle wird im Wesentlichen die gleiche Funktionalität bereitgestellt wie von anderen Clientzugriffsservern in der Exchange 2013-Organisation. Der Unterschied besteht in einigen Erweiterungen, die zur Unterstützung einer Hybridbereitstellung erforderlich sind. Der Clientzugriffsserver verarbeitet auch alle sicheren E-Mail-Nachrichten, die zwischen der lokalen und der Exchange Online-Organisation gesendet werden, sowie Transportregeln, Journalingrichtlinien und die Nachrichtenübermittlung an Benutzerpostfächer in Hybridbereitstellungen. Ein dedizierter Empfangsconnector wird standardmäßig auf dem Clientzugriffsserver konfiguriert, um den sicheren Hybrid-E-Mail-Transport zu unterstützen. Alle Clientverbindungen, einschließlich Outlook-Clientzugriff, Outlook Web App und Outlook Anywhere, erfolgen über die Clientzugriffs-Serverrolle. Auch Funktionen für die Organisationsbeziehung zwischen der lokalen und der Exchange Online-Organisation (z. B. Austausch von Frei/Gebucht-Informationen) werden von der Clientzugriffsserver-Rolle verarbeitet.
    
    Weitere Informationen finden Sie unter [Clientzugriffsserver](https://technet.microsoft.com/de-de/library/dd298114\(v=exchg.150\)).

  - **Postfachserverrolle**   Die Postfachserverrolle hostet die lokalen Empfängerpostfächer und kommuniziert mit der Exchange Online-Organisation mittels Proxy über den lokalen Clientzugriffsserver. Ein dedizierter Sendeconnector wird standardmäßig auf der Postfachserverrolle konfiguriert, um den sicheren Hybrid-E-Mail-Transport zu unterstützen.
    
    Weitere Informationen finden Sie unter [Postfachserver](https://technet.microsoft.com/de-de/library/jj150491\(v=exchg.150\)).

Je nach gewünschter Konfiguration für die Hybridbereitstellung müssen Sie auf einem Exchange 2013-Server eine oder beide Serverrollen installieren:

  - **Einzelner Exchange-Server**   Wenn Sie einen einzelnen Exchange-Server in Ihrer lokalen Organisation installieren, müssen Sie die Clientzugriffs- und Postfachserverrollen auf diesem Einzelserver installieren.

  - **Mehr als ein Exchange-Server**   Wenn Sie mehr als einen Exchange-Server in Ihrer lokalen Organisation installieren, können Sie die Serverrollen auf separaten Servern in Ihrer lokalen Organisation installieren. Sie können beispielsweise einen Exchange-Server installieren, auf dem sich die Postfach- und Clientzugriffs-Serverrollen befinden, und einen weiteren Exchange-Server konfigurieren, auf dem nur die Clientzugriffs-Serverrolle installiert wird. Als bewährte Methode und empfohlene Serverkonfiguration sollten Sie die Clientzugriffs- und die Postfachserverrolle jedoch auf *jedem* Server installieren, der in der lokalen Organisation bereitgestellt wird.

Weitere Informationen zur Exchange 2013-Kapazitätsplanung finden Sie unter [Grundlegendes zur Konfiguration mehrerer Serverrollen bei der Kapazitätsplanung](http://go.microsoft.com/fwlink/?linkid=266576).

## Exchange Server-Funktionalität in Hybridbereitstellungen

Ein Exchange-Server stellt in einer Hybridbereitstellung viele wichtige Funktionen für die lokale Organisation bereit:

  - **Partnerverbund**Exchange-Server ermöglichen die Erstellung einer Verbundvertrauensstellung mit Microsoft Federation Gateway für Ihre lokale Organisation. Microsoft Federation Gateway ist ein kostenloser, cloudbasierter Dienst von Microsoft, der als Vertrauensbroker zwischen der lokalen und der Office 365-Organisation fungiert. Der Verbund ist eine Voraussetzung für das Erstellen einer Organisationsbeziehung zwischen der lokalen und der Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Verbund](https://technet.microsoft.com/de-de/library/dd335047\(v=exchg.150\)).

  - **Organisationsbeziehungen**Exchange 2013-Server mit Clientzugriffsrolle und Exchange 2016-Server mit der Postfachrolle ermöglichen die Erstellung von Organisationsbeziehungen zwischen den lokalen Organisationen und den Exchange Online-Organisationen. Organisationsbeziehungen sind für viele andere Dienste in einer Hybridbereitstellung erforderlich, beispielsweise für die Freigabe von Kalender- und Frei/Gebucht-Informationen, für die Nachrichtenverfolgung sowie für das Verschieben von Postfächern zwischen der lokalen und der Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

  - **Nachrichtentransport**Exchange-Server mit der Clientzugriffs- und der Postfachserverrolle sind für den Nachrichtentransport in einer Hybridbereitstellung verantwortlich. Mithilfe von Sende- und Empfangsconnectors dienen sie als Verbindungsendpunkte für eingehende externe Nachrichten und sorgen zudem für die Zustellung ausgehender Nachrichten an das Internet und die Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Transportoptionen in Exchange-Hybridbereitstellungen](transport-options-in-exchange-hybrid-deployments-exchange-2013-help.md).

  - **Sicherheit des Nachrichtentransports**Exchange-Server mit der Clientzugriffs- und der Postfachserverrolle sorgen durch Verwendung der Domänensicherheitsfunktionalität in Exchange für eine sichere Nachrichtenübermittlung zwischen der lokalen und der Exchange Online-Organisation. Durch die Verwendung der gegenseitigen TLS-Authentifizierung (Transport Layer Security) und einer Verschlüsselung für die Nachrichtenübermittlung kann die Sicherheit noch erhöht werden.
    
    Weitere Informationen finden Sie unter [Grundlegendes zur Domänensicherheit](http://go.microsoft.com/fwlink/p/?linkid=266581).

  - **Outlook im Web (auch Outlook Web App in Exchange 2013):**  Exchange 2013-Server mit Clientzugriffsrolle und Exchange 2016-Server mit der Postfachrolle unterstützen die Konfiguration eines einzelnen URL-Endpunkts für externe Verbindungen mit lokalen und Exchange Online-Postfächern. Für lokale Postfächer werden Exchange-Server zur Verarbeitung von Outlook im Web-Anforderungen konfiguriert. Für Postfächer in Exchange Online-Organisationen werden Exchange-Server so konfiguriert, dass sie automatisch einen Link zum Outlook im Web-Endpunkt in der Exchange Online-Organisation anzeigen.
    
    Weitere Informationen finden Sie unter [Outlook Web App](https://technet.microsoft.com/de-de/library/jj657718\(v=exchg.150\)).

