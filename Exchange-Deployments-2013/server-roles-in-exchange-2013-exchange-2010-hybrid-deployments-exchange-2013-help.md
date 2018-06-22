---
title: 'Serverrollen in Exchange 2013-/Exchange 2010-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Serverrollen in Exchange 2013-/Exchange 2010-Hybridbereitstellungen
ms:assetid: 7d774948-94f9-4405-af2b-0c67c0405c0f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn393966(v=EXCHG.150)
ms:contentKeyID: 59634185
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Serverrollen in Exchange 2013-/Exchange 2010-Hybridbereitstellungen

Dieses Thema ist in Bearbeitung.  

_<strong>Gilt für:</strong>Exchange Online, Exchange Server, Exchange Server 2013_

_<strong>Letztes Änderungsdatum des Themas:</strong>2017-02-16_

Wenn Sie eine Hybridbereitstellung in einer Exchange 2010-Organisation konfigurieren, müssen Sie in Ihrer vorhandenen Exchange 2007-Organisation mindestens einen Exchange 2010-Server mit den Clientzugriffs- und Postfachserverrollen installieren. Die Exchange 2013-Clientzugriffs- und Postfachserver koordinieren die Kommunikation zwischen der vorhandenen lokalen Exchange 2010-Organisation und der Exchange Online-Organisation. Diese Kommunikation beinhaltet auch den Nachrichtentransport zwischen der lokalen und der Exchange Online-Organisation sowie Messagingfunktionen.

Um die Zuverlässigkeit und die Verfügbarkeit der Funktionen der hybriden Bereitstellung zu verbessern, wird dringend empfohlen, mehrere Exchange 2013-Server in der lokalen Organisation zu installieren.

## Serverrollen in einer Hybridbereitstellung

Im Folgenden können Sie sich einen raschen Überblick über die Exchange 2013-Serverrollen in einer Hybridbereitstellung verschaffen:

  - **Clientzugriffs-Serverrolle**   Die Exchange 2013-Clientzugriffs-Serverrolle bietet weiterhin viele der Funktionen, die normalerweise von Exchange 2010-Clientzugriffsservern in Ihrer Organisation bereitgestellt werden. Darüber hinaus bietet sie einige zusätzliche Funktionen, die zur Unterstützung einer Hybridbereitstellung und der Koexistenz mit Exchange 2010 erforderlich sind. Der Clientzugriffsserver verarbeitet auch sichere E-Mail-Nachrichten, die von der Exchange Online-Organisation an die lokale Organisation gesendet werden, sowie Transportregeln und Journalrichtlinien, und stellt Nachrichten an Postfachserver in einer Hybridbereitstellung zu. Ein dedizierter Empfangsconnector wird auf dem Clientzugriffsserver konfiguriert, um den sicheren Hybrid-E-Mail-Transport zu unterstützen. Alle Clientverbindungen, einschließlich Outlook-Clientzugriff, Outlook Web App und Outlook Anywhere, erfolgen über die Clientzugriffs-Serverrolle. Auch Funktionen für die Organisationsbeziehung zwischen der lokalen und der Exchange Online-Organisation (z. B. Austausch von Frei/Gebucht-Informationen) werden von der Clientzugriffsserver-Rolle verarbeitet.
    
    Weitere Informationen finden Sie unter [Clientzugriffsserver](https://technet.microsoft.com/de-de/library/dd298114\(v=exchg.150\)).

  - **Postfachserverrolle**   Die Exchange 2013-Postfachserverrolle verarbeitet sichere E-Mail-Nachrichten, die von der lokalen Organisation an die Exchange Online-Organisation gesendet werden. Sie kann, was allerdings selten vorkommt, auch lokale Empfängerpostfächer hosten und per Proxyverbindung über den lokalen Clientzugriffsserver mit der Exchange Online-Organisation kommunizieren. Ein dedizierter Sendeconnector wird standardmäßig auf der Postfachserverrolle konfiguriert, um den sicheren Hybrid-E-Mail-Transport zu unterstützen.
    
    Weitere Informationen finden Sie unter [Postfachserver](https://technet.microsoft.com/de-de/library/jj150491\(v=exchg.150\)).

Je nach gewünschter Konfiguration für die Hybridbereitstellung müssen Sie auf einem Exchange 2013-Server eine oder beide Serverrollen installieren:

  - **Einzelner Exchange-Server**   Wenn Sie einen einzelnen Exchange-Server in Ihrer lokalen Organisation installieren, müssen Sie die Clientzugriffs- und Postfachserverrollen auf diesem Einzelserver installieren.

  - **Mehr als ein Exchange-Server**   Wenn Sie mehr als einen Exchange-Server in Ihrer lokalen Organisation installieren, können Sie die Serverrollen auf separaten Servern in Ihrer lokalen Organisation installieren. Sie können beispielsweise einen Exchange 2013-Server installieren, auf dem sich die Postfach- und Clientzugriffs-Serverrollen befinden, und einen weiteren Exchange-Server konfigurieren, auf dem nur die Clientzugriffs-Serverrolle installiert wird. Als bewährte Methode und empfohlene Serverkonfiguration sollten Sie die Clientzugriffs- und die Postfachserverrolle jedoch auf *jedem* Exchange 2013-Server installieren, der in der lokalen Organisation bereitgestellt wird.

Weitere Informationen zur Exchange-Kapazitätsplanung finden Sie unter [Grundlegendes zur Konfiguration mehrerer Serverrollen bei der Kapazitätsplanung](https://go.microsoft.com/fwlink/?linkid=266576).

## Exchange Server-Funktionalität in Hybridbereitstellungen

Ein Exchange-Server stellt in einer Hybridbereitstellung viele wichtige Funktionen für die lokale Organisation bereit:

  - **Partnerverbund** Exchange 2013- und Exchange 2010-Server ermöglichen die Erstellung einer Verbundvertrauensstellung mit Microsoft Federation Gateway für Ihre lokale Organisation. Microsoft Federation Gateway ist ein kostenloser, cloudbasierter Dienst von Microsoft, der als Vertrauensbroker zwischen der lokalen und der Office 365-Mandantenorganisation fungiert. Der Verbund ist eine Voraussetzung für das Erstellen einer Organisationsbeziehung zwischen der lokalen und der Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Verbund](https://technet.microsoft.com/de-de/library/dd335047\(v=exchg.150\)).

  - **Organisationsbeziehungen**   Exchange 2013-Server mit Clientzugriffs-Serverrolle ermöglichen die Erstellung von Organisationsbeziehungen zwischen den lokalen Organisationen und den Exchange Online-Organisationen. Organisationsbeziehungen sind für viele andere Dienste in einer Hybridbereitstellung erforderlich, beispielsweise für die Freigabe von Kalender- und Frei/Gebucht-Informationen, für die Nachrichtenverfolgung sowie für das Verschieben von Postfächern zwischen der lokalen und der Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

  - **Nachrichtentransport**   Exchange 2013-Server mit der Clientzugriffs- und der Postfachserverrolle sind für den Nachrichtentransport in einer Hybridbereitstellung verantwortlich. Mithilfe von Sende- und Empfangsconnectors dienen sie als Verbindungsendpunkte für eingehende externe Nachrichten und sorgen zudem für die Zustellung ausgehender Nachrichten an das Internet und die Exchange Online-Organisation.
    
    Weitere Informationen finden Sie unter [Transportoptionen in Exchange 2013-/Exchange 2010-Hybridbereitstellungen](transport-options-in-exchange-2013-exchange-2010-hybrid-deployments-exchange-2013-help.md).

  - **Sicherheit des Nachrichtentransports**   Exchange 2013-Server mit der Clientzugriffs- und der Postfachserverrolle sorgen durch Verwendung der Domänensicherheitsfunktionalität in Exchange 2013 für eine sichere Nachrichtenübermittlung zwischen der lokalen und der Exchange Online-Organisation. Durch die Verwendung der gegenseitigen TLS-Authentifizierung (Transport Layer Security) und einer Verschlüsselung für die Nachrichtenübermittlung kann die Sicherheit noch erhöht werden.
    
    Weitere Informationen finden Sie unter [Grundlegendes zur Domänensicherheit](https://go.microsoft.com/fwlink/p/?linkid=266581).

  - **Outlook Web App**   Exchange 2013-Server mit Clientzugriffs-Serverrolle unterstützen die Konfiguration eines einzelnen URL-Endpunkts für externe Verbindungen mit lokalen und Exchange Online-Postfächern. Für lokale Postfächer werden Clientzugriffsserver zur Verarbeitung von Outlook Web App-Anforderungen konfiguriert. Für Postfächer in Exchange Online-Organisationen werden Clientzugriffsserver so konfiguriert, dass sie automatisch einen Link zum Outlook Web App-Endpunkt in der Exchange Online-Organisation anzeigen.
    
    Weitere Informationen finden Sie unter [Outlook Web App](https://technet.microsoft.com/de-de/library/jj657718\(v=exchg.150\)).

## Exchange Server-Topologie

Wenn Sie zusätzliche Exchange 2013-Server zur Unterstützung Ihrer Hybridbereitstellung installieren, wird der Exchange-Server ähnlich wie ein beliebiger anderer Exchange-Server in Ihrer vorhandenen Exchange 2010-Organisation bereitgestellt. Zur Konfiguration Ihrer vorhandenen lokalen Exchange 2010-Organisation für eine Hybridbereitstellung ist keine besondere Exchange-Servertopologie erforderlich. Sie müssen auf Ihren Exchange 2010-Servern allerdings Exchange 2010 Service Pack 3 (SP3) und auch das kumulative Exchange 2013-Update 1 (CU1) oder höher installieren, um Kompatibilität und volle Hybridfunktionalität mit Office 365 zu ermöglichen.

Die folgende Tabelle umfasst eine kurze Beschreibung der Änderungen, die nach der Konfiguration einer Hybridbereitstellung für die Dienste berücksichtigt werden müssen.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Dienst</th>
<th>Vor Hybridbereitstellung</th>
<th>Nach Hybridbereitstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nachrichtentransport (eingehend und ausgehend)</p></td>
<td><p>Exchange 2010-Clientzugriffsserver</p></td>
<td><p>Exchange 2013-Clientzugriffsserver oder Exchange Online Protection (EOP) ist im Lieferumfang von Office 365 enthalten</p></td>
<td><p>Der MX-Eintrag (Mail Exchanger) für die Domäne kann unverändert bleiben oder zur Referenzierung von EOP aktualisiert werden.</p></td>
</tr>
<tr class="even">
<td><p>Öffentliche URL von Outlook Web App</p></td>
<td><p>Exchange 2010-Clientzugriffsserver</p></td>
<td><p>Exchange 2013-Clientzugriffsserver</p></td>
<td><p>Exchange 2013-Clientzugriffsserver leiten Outlook Web App-Anforderungen für lokale Postfächer an Exchange 2010-Clientzugriffsserver weiter. Für Outlook Web App-Anforderungen für Postfächer, die auf Exchange Online gehostet werden, wird ein Link zur Exchange Online-Outlook Web App-URL bereitgestellt.</p></td>
</tr>
</tbody>
</table>


## Exchange Server-Software

Exchange 2013 CU1 oder höher bietet über den Assistenten für die Hybridkonfiguration die Möglichkeit zur Bereitstellung von Funktionen für Hybridbereitstellungen. Bei der Installation zusätzlicher Exchange 2013-Server können Sie ein beliebiges Exchange 2013 CU1-Medium oder ein Medium höherer Version verwenden.

Weitere Informationen zum Herunterladen der aktuellen Version von Exchange 2013 finden Sie unter [Updates für Exchange 2013](https://technet.microsoft.com/library/jj907309).


> [!IMPORTANT]
> Sie müssen Ihren Hybridserver lizenzieren, wenn Sie eine Hybridbereitstellung mit Exchange 2013 oder 2010 und Office 365 konfigurieren. Um einen kostenlosen Exchange Server-Product Key für die Konfiguration Ihrer Hybridbereitstellung zu erhalten, verwenden Sie das <A href="https://aka.ms/hybridkey">Hybrid Edition Product Key-Tool</A>.


