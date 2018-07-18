---
title: 'Änderungen an der Spracharchitektur: Exchange 2013 Help'
TOCTitle: Änderungen an der Spracharchitektur
ms:assetid: 55d5ca4a-b0cd-45f1-9f47-e745ef208698
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150516(v=EXCHG.150)
ms:contentKeyID: 50475681
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Änderungen an der Spracharchitektur

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Microsoft Exchange Server 2013-Architektur unterscheidet sich von der Architektur in Exchange Server 2007 und Exchange Server 2010. In Exchange 2007 und Exchange 2010 wurden die Servertypen in mehrere Serverrollen unterteilt: Clientzugriff, Postfach, Hub-Transport und Unified Messaging. In Exchange 2013 werden die Serverrollen in zwei Servertypen kombiniert, und alle Komponenten oder Dienste dieser Serverrollen werden auf demselben physischen Server oder auf zwei getrennten Servern ausgeführt – dem Clientzugriffs- und dem Postfachserver. In diesem neuen Modell leitet der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird, den SIP-Datenverkehr (Session Initialization Protocol), der durch einen eingehenden Anruf generiert wird, an einen Postfachserver um. Anschließend wird ein Medienkanal (RTP \[Realtime Transport Protocol\] oder SRTP \[Secure RTP\]) zwischen dem VoIP-Gateway oder der IP-Nebenstellenanlage (Private Branch eXchange, PBX) und dem Postfachserver eingerichtet, der das Benutzerpostfach hostet. In Exchange 2013 führt der Postfachserver dieselben Prozesse aus wie die Unified Messaging-Serverrolle in Exchange 2007 und Exchange 2010. Auf dem Postfachserver werden sowohl der Microsoft Exchange Unified Messaging-Dienst als auch UM-Arbeitsprozesse ausgeführt. Der Clientzugriffsserver führt den Microsoft Exchange Unified Messaging-Anrufrouterdienst aus, der einen eingehenden Anruf empfängt und diesen an den Postfachserver weiterleitet.

**Inhalt**

Unterstützung für die neue Exchange-Architektur

UM-Ports

UM-Wählpläne

Leistungsindikatoren für UM-Anrufrouterdienst

## Unterstützung für die neue Exchange-Architektur

In Exchange 2013 ist der Clientzugriffsserver für AutoErmittlung, SSL (Secure Sockets Layer), Authentifizierung, Umleitung und Proxy zuständig. Der Clientzugriffsserver ist der Einstiegspunkt für alle eingehenden Anrufe oder SIP-Anforderungen für Unified Messaging (UM). Die Routinglogik und SIP REDIRECT werden als Dienst implementiert, der automatisch in einem Clientzugriffsserver integriert ist. Dieser Dienst wird als Microsoft Exchange Unified Messaging-Anrufrouterdienst bezeichnet. Er wird auf jedem Clientzugriffsserver in Ihrer Organisation installiert und ausgeführt. Wenn ein Clientzugriffsserver eine SIP INVITE-Anforderung für einen eingehenden Anruf empfängt, leitet der Microsoft Exchange Unified Messaging-Anrufrouterdienst den eingehenden Anruf an den Postfachserver um. Anschließend wird ein Medienkanal (RTP oder SRTP) zwischen VoIP-Gateway, IP-Nebenstellenanlage oder SBC (Session Border Controller) und dem Postfachserver eingerichtet. Obwohl der Clientzugriffsserver als SIP-Redirector fungiert, verarbeitet er ausschließlich SIP-Anforderungen von VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs. Er empfängt keinen Mediendatenverkehr. Mediendatenverkehr mit Verwendung von RTP oder SRTP wird ausschließlich zwischen dem Postfachserver und SIP-Peers wie z. B. VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs weitergeleitet – nicht jedoch an den Clientzugriffsserver. Wenn Sie Exchange 2013 und UM bereitstellen, müssen Sie Ihre VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs so konfigurieren, dass sie auf die installierten Clientzugriffsserver zeigen, damit eingehende Anrufe für UM ordnungsgemäß weitergeleitet werden.

In einigen Fällen ist es erforderlich, mehrere Clientzugriffsserver bereitzustellen, und die Clientzugriffsserver werden getrennt auf anderer physischer Hardware bereitgestellt als die Postfachserver. Clientzugriffsserver können in einem Array gruppiert werden, indem eine L4- oder L5-Hardwarekomponente zum Lastenausgleich oder eine Software zum Lastenausgleich verwendet wird. Es gibt jedoch keine auf Active Directory-Exchange-Objekten basierten Clientzugriffsserver-Arrays. Die Verwendung von Hardware- oder Softwarekomponenten für den Lastenausgleich vor den Clientzugriffsservern ist eine akzeptierte Methode in großen Exchange-Bereitstellungen.

Wenn ein Clientzugriffsserver installiert wird, wird der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt. Der Dienst bietet Folgendes:

  - Einlesen der lokalen Konfigurationsdatei namens "msexchangeumcallrouter.config" nach der Initialisierung.

  - Sprachgrammatikgenerierung unter Verwendung eine Vermittlungspostfachs für eine Organisation.

  - Unterstützung von TCP- (Transmission Control Protocol) und/oder TLS-Verbindungen (Transport Layer Security) – diese Einstellung kann konfiguriert werden.

  - Dienst wird nur beendet, wenn ein Konfigurationsfehler vorliegt oder die erforderlichen Ports nicht registriert werden können.

In Exchange 2013 ist der Postfachserver nicht für die Beantwortung von SIP-Anforderungen über eingehende Anrufe verantwortlich. Er ist nur für dem Empfang von SIP-Datenverkehr von einem Clientzugriffsserver zuständig und richtet anschließend eine RTP- oder SRTP-Verbindung mit dem VoIP-Gateway, der IP-Nebenstellenanlage oder dem SBC ein.

Nachdem ein Clientzugriffsserver einen eingehenden Anruf an einen Postfachserver weitergeleitet hat, wird ein Medienkanal zwischen VoIP-Gateway, IP-Nebenstellenanlage oder SBC und dem Postfachserver eingerichtet. Nach Einrichtung des Medienkanals spielt der Microsoft Exchange Unified Messaging-Dienst auf dem Postfachserver die Voicemailbegrüßung des Benutzers ab, verarbeitet Mailboxansageregeln für den Benutzer und fordert den Anrufer auf, eine Sprachnachricht zu hinterlassen. Der Postfachserver zeichnet die Sprachnachricht auf, erstellt eine Transkription der Nachricht und hinterlegt diese im Benutzerpostfach. Wenn Sie Exchange jedoch in Office Communications Server 2007 R2 oder Lync Server integrieren, werden sowohl die SIP- als auch RTP- oder SRTP-Medienkanäle für eingehende Anrufe von Lync-Servern und Postfachserver verarbeitet. In einer integrierten Lync-Umgebung gibt es keine VoIP-Gateways, IP-Nebenstellen oder SBCs. Gegenüber Lync ist der Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst lediglich ein Exchange 2010 UM-Server. Der Postfachserver und der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird, werden als vertrauenswürdige Peers eingestuft, da beide Server einem SIP-Wählplan hinzugefügt werden müssen. Lync leitet den eingehenden Anruf mit der Komponente für das eingehende Routing weiter, die SIP zur Kommunikation mit dem Clientzugriffsserver verwendet und den Anruf an einen Postfachserver weiterleitet.

Exchange 2010 UM-Administratoren können einen Satz an Eigenschaften für Unified Messaging auf jedem UM-Server konfigurieren. In Exchange 2013 stehen UM-Komponenten und Konfigurationseinstellungen für UM sowohl auf den Clientzugriffsservern als auch auf den Postfachservern zur Verfügung. Alle Konfigurationseinstellungen, die für einen einzelnen Computer mit der Unified Messaging-Serverrolle in Exchange 2010 gelten, sind weiterhin verfügbar. Einige dieser Eigenschaften und Konfigurationseinstellungen werden jedoch auf einem Clientzugriffsserver festgelegt, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird, und andere Einstellungen sind auf einem Postfachserver verfügbar, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. In einigen Fällen steht dieselbe Einstellung auf beiden Servern zur Verfügung. In der folgenden Liste sind die Cmdlets und Parameter aufgeführt, die auf Clientzugriffs- und Postfachservern verfügbar sind, sowie Fälle, in denen Änderungen an einem Cmdlet vorgenommen wurden, um Bereitstellungsszenarien mit früheren Versionen von Unified Messaging zu unterstützen.

  - **Set-UMService -DialPlans \<MultiValuedProperty\>**    Verfügbar auf Exchange 2013-Postfachservern, kann auch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings -DialPlans \<MultiValuedProperty\>**    Verfügbar auf Exchange 2013-Clientzugriffsservern, jedoch nicht für Exchange 2007- und Exchange 2010 Unified Messaging-Server.

  - **Set-UMService -MaxCallsAllowed \<Int32\>**    Verfügbar auf Exchange 2013-Postfachservern, kann auch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings -MaxCallsAllowed \<Int32\>**   Nicht verfügbar auf Exchange 2013-Clientzugriffsservern und auch nicht für Exchange 2007- und Exchange 2010 Unified Messaging-Server.

  - **Set-UMService -SipTcpListeningPort \<Int32\>**   Nicht konfigurierbar auf Exchange 2013-Postfachservern, kann jedoch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMService -SipTlsListeningPort \<Int32\>**   Nicht konfigurierbar auf Exchange 2013-Postfachservern, kann jedoch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings -SipTcpListeningPort \<Int32\>**    Verfügbar auf Exchange 2013-Clientzugriffsservern, kann jedoch nicht auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings -SipTlsListeningPort \<Int32\>**   Verfügbar auf Exchange 2013-Clientzugriffsservern, kann jedoch nicht auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMService - Status \<Enabled | Disabled | NoNewCalls\>**   Nicht verfügbar auf Exchange 2013-Postfachservern, kann jedoch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings - Status \<Enabled | Disabled | NoNewCalls\>**   Nicht verfügbar auf Exchange 2013-Clientzugriffsservern, kann auch nicht auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMService -UMStartupMode \<TCP | TLS | Dual\>**   Verfügbar auf Exchange 2013-Postfachservern, kann auch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Set-UMCallRouterSettings - UMStartupMode \<TCP | TLS | Dual\>**    Verfügbar auf Exchange 2013-Clientzugriffsservern, kann jedoch nicht auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Enable-UMService**    Nicht verfügbar auf Exchange 2013-Postfachservern, kann jedoch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

  - **Disable-UMService**    Nicht verfügbar auf Exchange 2013-Postfachservern, kann jedoch auf Exchange 2007- und Exchange 2010 Unified Messaging-Servern verwendet werden.

Für den Postfachserver verwenden Sie die Cmdlets **Set/Get/Enable/Disable-UMService**, um UM-Eigenschaften für den Microsoft Exchange Unified Messaging-Dienst auf Exchange 2013-Postfachservern oder Exchange 2007- oder Exchange 2010 Unified Messaging-Servern anzuzeigen oder zu konfigurieren. Ein anderer Satz an Cmdlets, **Set/Get-UMCallRouterSettings**, wird zur Anzeige und Konfiguration der Eigenschaften für den Microsoft Exchange Unified Messaging-Anrufrouterdienst auf einem Clientzugriffsserver verwendet. Auf diese Weise wird sichergestellt, dass die vorhandenen Cmdlets **Get-UMServer**, **Set-UMServer**, **Enable-UMServer** und **Disable-UMServer** aus Exchange 2007 und Exchange 2010 in einer Koexistenzumgebung mit Exchange 2013-Postfachservern weiterhin funktionieren. Außerdem wird gewährleistet, dass die Cmdlets auch funktionieren, wenn Postfach- und Clientzugriffsserver auf demselben oder unterschiedlichen Servern installiert sind.

Unterstützung für die neue Exchange-Architektur

## UM-Ports

Der Microsoft Exchange Unified Messaging-Call-Router-Dienst auf einem Clientzugriffsserver verwendet SIP über TCP (Transmission Control Protocol) oder MTLS (Mutual Transport Layer Security) zur Kommunikation mit Postfachservern, auf denen der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. Zur Vermeidung von TCP/UDP-Portkonflikten (User Datagram Protocol) verwenden der Microsoft Exchange Unified Messaging-Anrufrouterdienst und der Microsoft Exchange Unified Messaging-Dienst unterschiedliche Standardeinstellungen und überwachen unterschiedliche TCP-Ports. Sie können beide sowohl ungesicherte als auch gesicherte Verbindungen akzeptieren – abhängig davon, ob MTLS für SIP- und RTP-Datenverkehr eingesetzt wird. Standardmäßig überwacht ein Clientzugriffsserver sowohl TCP-Port 5060 im ungesicherten Modus als auch TCP-Port 5061 im SIP-gesicherten Modus auf SIP-Anforderungen, wenn MTLS verwendet wird. Diese Ports können mit dem Cmdlet **Set-UMCallRouterSettings** konfiguriert werden. Der Microsoft Exchange Unified Messaging-Anrufrouterdienst auf dem Clientzugriffsserver verarbeitet keinen Mediendatenverkehr (RTP oder SRTP), daher werden nur TCP-Ports und keine UDP-Ports verwendet. Standardmäßig überwacht ein Postfachserver sowohl TCP-Port 5062 im ungesicherten Modus als auch TCP-Port 5063 im SIP-gesicherten Modus auf SIP-Anforderungen, wenn MTLS verwendet wird. Diese Ports können nicht mithilfe von Cmdlets der Exchange-Verwaltungsshell konfiguriert werden. Auf dem Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, können keine TCP-Ports für den Exchange-Server konfiguriert werden – weder mit der Shell noch durch Konfigurationseinstellungen in der Registrierung. Der Microsoft Exchange Unified Messaging-Dienst auf dem Postfachserver akzeptiert Verbindungen von einem Clientzugriffsserver auf den SIP-Ports 5062 und 5063. Nachdem der Clientzugriffsserver die SIP-Anforderung an einen Postfachserver umgeleitet hat, wird ein RTP- oder SRTP-Medienkanal zwischen einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem SBC und dem Microsoft Exchange Unified Messaging-Arbeitsprozess auf dem Postfachserver eingerichtet.

In der folgenden Tabelle werden die Exchange 2013-Ports und -Protokolle zusammengefasst, und es wird angegeben, ob die Ports geändert werden können.

### UM-Abhörports

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protokoll</th>
<th>TCP-Port</th>
<th>UDP-Port</th>
<th>Können die Ports geändert werden?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SIP (Clientzugriffsserver – Microsoft Exchange Unified Messaging-Anrufrouterdienst)</p></td>
<td><p>5060 (ungesichert), 5061 (gesichert). Der Dienst lauscht an beiden Ports.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ja, mit dem Cmdlet <strong>Set-UMCallRouterSettings</strong>.</p></td>
</tr>
<tr class="even">
<td><p>SIP (Postfachserver – Microsoft Exchange Unified Messaging-Dienst)</p></td>
<td><p>5062 (ungesichert), 5063 (gesichert). Der Dienst lauscht an beiden Ports.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ports können nicht geändert werden.</p></td>
</tr>
<tr class="odd">
<td><p>SIP (Postfachserver – UM-Arbeitsprozess)</p></td>
<td><p>5065 und 5067 für TCP (ungesichert). 5066 und 5068 für MTLS (gesichert). Dies ist der Fall, wenn <em>UMStartupMode</em> auf <em>Dual</em> festgelegt wird. Wenn <em>UMStartUpMode</em> auf <em>TCP</em> oder <em>TLS</em> festgelegt wird, werden die Ports 5065 und 5066 verwendet. Der Standardwert für <em>UMStartupMode</em> lautet <em>TCP</em>.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ports können nicht geändert werden.</p></td>
</tr>
<tr class="even">
<td><p>RTP (Postfachserver – UM-Arbeitsprozess)</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ports zwischen 1024 und 65535.</p></td>
<td><p>Der Portbereich kann über die Registrierung geändert werden (dies ist jedoch keine unterstützte Konfiguration):</p>
<p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Speech Server\2.0\AudioConnectionMinPort</p>
<p>HKLM\SOFTWARE\Microsoft\Microsoft Speech Server\2.0\AudioConnectionMaxPort</p></td>
</tr>
</tbody>
</table>


Unterstützung für die neue Exchange-Architektur

## UM-Wählpläne

Die Zuordnung oder Zuweisung von UM-Wählplänen zu UM-Servern ist in Exchange 2013 nicht in der Weise erforderlich, wie es in Exchange 2007 und Exchange 2010 der Fall war. Clientzugriffsserver oder Postfachserver, auf denen UM-Dienste ausgeführt werden, müssen keinem Wählplan zugeordnet werden, da alle Clientzugriffsserver und Postfachserver eingehende Anrufe von VoIP-Gateways, IP-Nebenstellen oder SBCs empfangen. Eine Ausnahme stellen SIP-Wählpläne dar, die mit Lync 2013, Lync Server 2010 und Office Communications Server 2007 R2 verwendet werden. Diese müssen den bereitgestellten Clientzugriffsservern und Postfachservern zugeordnet werden. Beide Exchange-Servertypen müssen jedem SIP-Wählplan hinzugefügt werden, damit sie von Communications Server 2007 R2 oder Lync Server als vertrauenswürdige Peers eingestuft werden. Andernfalls lehnen Communications Server 2007 R2 oder Lync Server ausgehende Anrufe von Benutzern ab.

In der folgenden Tabelle wird die Beziehung zwischen Clientzugriffsservern und Postfachservern sowie UM-Wählplanen zusammengefasst.

### Zuordnen von UM-Wählplänen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topologie</th>
<th>Wählplan   </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriffsserver und Postfachserver befinden sich auf demselben Server (ohne Communications Server 2007 R2- oder Lync Server 2010-Nicht-SIP-Wählpläne)</p></td>
<td><p>Wählpläne müssen einem Clientzugriffs- oder Postfachserver nicht länger zugeordnet werden. Sie können den Clientzugriffs- oder Postfachserver keinem Wählplan hinzufügen. Wenn Sie das Cmdlet <strong>Set-UMService</strong> ausführen, wird ein Fehler bei dem Versuch generiert, den Postfachserver einem Nicht-SIP-Wählplan zuzuordnen.</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriffsserver und Postfachserver befinden sich auf unterschiedlichen Servern (ohne Communications Server 2007 R2- oder Lync Server 2010-Nicht-SIP-Wählpläne)</p></td>
<td><p>Wählpläne müssen Clientzugriffs- oder Postfachservern nicht länger zugeordnet werden. Sie können Clientzugriffs- oder Postfachserver keinem Wählplan hinzufügen. Wenn Sie das Cmdlet <strong>Set-UMService</strong> ausführen, wird ein Fehler bei dem Versuch generiert, den Postfachserver einem Nicht-SIP-Wählplan zuzuordnen.</p></td>
</tr>
<tr class="odd">
<td><p>Clientzugriffsserver und Postfachserver befinden sich auf demselben physischen Server (mit Communications Server 2007 R2 und Lync Server 2010 mit SIP-Wählplänen)</p></td>
<td><p>Fügen Sie bei einem einzelnen SIP-Wählplan alle Clientzugriffs- und Postfachserver zum SIP-Wählplan hinzu. Fügen Sie bei mehreren SIP-Wählplänen alle Clientzugriffs- und Postfachserver zu jedem SIP-Wählplan hinzu. Dadurch werden beide Server zu vertrauenswürdigen Peers für Office Communications Server 2007 R2 oder Lync Server. Sie müssen dasselbe Zertifikat in Ihrer Office Communications Server 2007 R2- oder Lync Server-Bereitstellung verwenden wie auf jedem Clientzugriffs- und Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriffsserver und Postfachserver befinden sich auf unterschiedlichen physischen Servern (mit Communications Server 2007 R2 und Lync Server 2010 mit SIP-Wählplänen)</p></td>
<td><p>Fügen Sie bei einem einzelnen SIP-Wählplan alle Clientzugriffs- und Postfachserver zum SIP-Wählplan hinzu. Fügen Sie bei mehreren SIP-Wählplänen alle Clientzugriffs- und Postfachserver zu jedem SIP-Wählplan hinzu. Dadurch werden beide Server zu vertrauenswürdigen Peers für Office Communications Server 2007 R2 oder Lync Server. Wenn sich die auf Clientzugriffs- und Postfachservern verwendeten Zertifikate unterscheiden, müssen Sie dasselbe Zertifikat in Ihrer Office Communications Server 2007 R2- oder Lync Server-Bereitstellung verwenden wie auf jedem Clientzugriffs- und Postfachserver in Ihrer Organisation.</p></td>
</tr>
</tbody>
</table>


Unterstützung für die neue Exchange-Architektur

## Leistungsindikatoren für UM-Anrufrouterdienst

Vorgängerversionen von Exchange umfassten die Unified Messaging-Serverrolle, die den Microsoft Exchange Unified Messaging-Dienst ausführte. Aufgrund der Architekturänderungen in Exchange 2013 führt der Clientzugriffsserver den Microsoft Exchange Unified Messaging-Anrufrouterdienst und der Postfachserver den Microsoft Exchange Unified Messaging-Dienst aus. Für die Verwaltung des Microsoft Exchange Unified Messaging-Diensts stehen dieselben Leistungsindikatoren zur Verfügung wie in früheren Versionen von Exchange UM. Es gibt jedoch zusätzliche Leistungsindikatoren, die Sie auf dem Clientzugriffsserver verwenden können, um den Status des Microsoft Exchange Unified Messaging-Anrufrouterdiensts zu überprüfen und eine Problembehandlung durchzuführen.

Zur Unterstützung des neuen Unified Messaging-Anrufrouterdiensts auf dem Clientzugriffsserver in Exchange 2013 stehen ab sofort die folgenden Leistungsindikatoren zur Verfügung.

### Leistungsindikatoren

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Leistungsindikatorkategorie</th>
<th>Indikatorname</th>
<th>Beschreibung</th>
<th>Schwellenwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MSExchangeUMRouterAvailability</p></td>
<td><p>% eingehende Anrufe: Vom Microsoft Exchange Unified Messaging-Anrufrouterdienst in der letzten Stunde zurückgewiesene</p></td>
<td><p>Gibt den Prozentsatz der eingehenden Anrufe an, die der Microsoft Exchange Unified Messaging-Anrufrouterdienst in der letzten Stunde zurückgewiesen hat.</p></td>
<td><p>Muss immer unter 5 Prozent liegen, sollte immer 0 sein.</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeUMRouterAvailability</p></td>
<td><p>Getrennte Anrufe aufgrund eines nicht behebbaren internen Fehlers für den Microsoft Exchange Unified Messaging-Anrufrouterdienst</p></td>
<td><p>Gibt die Anzahl von Anrufen an, die nach einem internen Systemfehler getrennt wurden.</p></td>
<td><p>Sollte immer 0 sein.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeUMRouterAvailability</p></td>
<td><p>Gesamtanzahl von eingehenden Anrufen, die vom Microsoft Exchange Unified Messaging-Anrufrouterdienst abgelehnt wurden</p></td>
<td><p>Gibt die Gesamtanzahl von eingehenden Anrufen an, die der Microsoft Exchange Unified Messaging-Anrufrouterdienst seit seinem Start abgelehnt hat.</p></td>
<td><p>Sollte immer 0 sein.</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeUMRouterAvailability</p></td>
<td><p>Gesamtanzahl von eingehenden Anrufen, die vom Microsoft Exchange Unified Messaging-Anrufrouterdienst empfangen wurden</p></td>
<td><p>Gibt die Gesamtanzahl von eingehenden Anrufen an, die der Microsoft Exchange Unified Messaging-Anrufrouterdienst seit seinem Start empfangen hat.</p></td>
<td><p>Sollte 0 oder größer sein.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeUMRouterAvailability</p></td>
<td><p>% eingehende Anrufe: Vom Microsoft Exchange Unified Messaging-Anrufrouterdienst in der letzten Stunde zurückgewiesene</p></td>
<td><p>Gibt den Prozentsatz der eingehenden Anrufe an, die der Microsoft Exchange Unified Messaging-Anrufrouterdienst in der letzten Stunde zurückgewiesen hat.</p></td>
<td><p>Sollte unter 5 Prozent liegen.</p></td>
</tr>
</tbody>
</table>


Unterstützung für die neue Exchange-Architektur

