---
title: 'UM-Protokolle, Ports und Dienste: Exchange 2013 Help'
TOCTitle: UM-Protokolle, Ports und Dienste
ms:assetid: 5997ce29-1755-48bb-8ff4-b08da549482a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998265(v=EXCHG.150)
ms:contentKeyID: 54652687
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-Protokolle, Ports und Dienste

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

MicrosoftExchange 2013 Unified Messaging (UM) erfordert die Verwendung mehrerer TCP- und UDP-Ports (User Datagram Protocol) zum Herstellen von Verbindungen zwischen Servern mit Exchange 2013 und anderen Geräten. Durch das Zulassen des Zugriffs über diese IP-Ports ermöglichen Sie die ordnungsgemäße Funktionsweise von Unified Messaging. In diesem Thema werden die TCP- und UDP-Ports erläutert, die in Exchange 2013 Unified Messaging verwendet werden.

## Unified Messaging-Protokolle und -Dienste

Exchange 2013 Unified Messaging-Funktionen und -Dienste arbeiten mit statischen und dynamischen TCP- und UDP-Ports, um die ordnungsgemäße Funktionsweise der Clientzugriffsserver, die den Microsoft Exchange Unified Messaging Call Router-Dienst ausführen, bzw. der Postfachserver, die den Microsoft Exchange Unified Messaging-Dienst ausführen, zu gewährleisten.Bei der Installation von Exchange 2013 werden statische Windows-Firewallregeln für Exchange hinzugefügt. Wenn Sie die TCP-Ports ändern, die von den Zugriffs- und Postfachservern verwendet werden, müssen Sie möglicherweise auch die Regeln der Windows-Firewall neu konfigurieren, damit Unified Messaging ordnungsgemäß funktioniert.


> [!IMPORTANT]
> Auf Exchange 2013-Zugriffs- und -Postfachservern, die UM-Komponenten und -Dienste ausführen, erstellt das Exchange-Setup Firewall-Regel für eingehende Nachrichten, damit eingehende Kommunikation ohne TCP-Porteinschränkungen möglich ist. Bei UM-Diensten werden die folgenden Regeln für eingehende Kommunikation hinzugefügt:



1.  **SESWorker (GFW) (TCP eingehend)**

2.  **UMCallRouter (GFW) (TCP-In)**

3.  **UMCallRouter (TCP-In)**

4.  **UMService (GFW) (TCP eingehend)**

5.  **UMService (TCP eingehend)**

6.  **UMWorkerProcess – RPC (TCP-In)**

7.  **UMWorkerProcess (GFW) (TCP eingehend)**

8.  **UMWorkerProcess (TCP eingehend)**

## Session Initiation-Protokoll

Das Session Initiation-Protokoll (SIP) ist ein Protokoll, das zum Einleiten, Ändern und Beenden einer interaktiven Benutzersitzung mit Multimediaelementen, z. B. Video, Sprache, Instant Messaging, Onlinespielen und virtueller Realität, verwendet wird. Es gehört zusammen mit H.323 zu den führenden Signalisierungsprotokollen für Voice over IP (VoIP). Die meisten auf Standards basierenden VoIP-Lösungen verwenden entweder H.323 oder SIP. Es gibt darüber hinaus jedoch auch verschiedene proprietäre Entwürfe und Protokolle. Die VoIP-Protokolle unterstützen normalerweise Funktionen wie Anklopffunktion, Konferenzgespräche und Anrufübergabe.

SIP-Clients, wie VoIP-Gateways und IP-Festnetztelefonanlagen, verwenden den TCP- und UDP-Port 5060 für eine Verbindung zu SIP-Servern, einschließlich Clientzugriffsservern, die den Microsoft Exchange Unified Messaging Call Router-Dienst ausführen. SIP wird nur beim Aufbauen und Beenden von Sprach- oder Videoanrufen verwendet. Die gesamte Sprach- und Videokommunikation erfolgt über RTP (Realtime Transport Protocol, Real-Time Transport-Protokoll).

## Real-Time Transport-Protokoll

RTP definiert ein standardisiertes Paketformat zur Übermittlung von Audio und Video über ein bestimmtes Netzwerk, z. B. das Internet. RTP transportiert nur Sprach-/Videodaten im Netzwerk. Anrufaufbau und -beendigung erfolgen im Allgemeinen über SIP.

RTP erfordert keinen standardmäßigen oder statischen TCP- oder UDP-Port für die Kommunikation. Die RTP-Kommunikation erfolgt über einen UDP-Port mit gerader Portnummer; der nächsthöhere Port mit ungerader Portnummer wird für die TCP-Kommunikation verwendet. Obwohl es keine standardmäßigen Portbereichszuweisungen gibt, wird RTP in der Regel für die Verwendung von Ports zwischen 1024 und 65535 konfiguriert, und Postfachserver, die den Microsoft Exchange Unified Messaging-Dienst ausführen, berücksichtigen diese Vereinbarung. RTP kann Firewalls nur schwer durchdringen, da es einen dynamischen Portbereich verwendet.

## Unified Messaging-Webdienste

Die auf Postfachserver installierten Unified Messaging-Webdienste verwenden IP für die Netzwerkkommunikation zwischen einem Client, dem Postfachserver und Computern, die andere Exchange 2013-Serverrollen ausführen. Es gibt mehrere Exchange 2013Outlook Web App- und Outlook 2013-Clientfunktionen, die auf die Unified Messaging-Webdienste angewiesen sind, um ordnungsgemäß zu funktionieren.

Die folgenden Unified Messaging-Clientfunktionen stützen sich auf die Unified Messaging-Webdienste:

  - Die in Exchange 2013Outlook Web App verfügbaren Voicemailoptionen, einschließlich der Funktion für die Wiedergabe über Telefon und der Möglichkeit zum Zurücksetzen einer PIN

  - Die Funktion "Wiedergabe über Telefon" in einem Outlook-Client.

## UM-Ports

Der Microsoft Exchange Unified Messaging-Call-Router-Dienst auf einem Clientzugriffsserver verwendet SIP über TCP (Transmission Control Protocol) oder MTLS (Mutual Transport Layer Security) zur Kommunikation mit Postfachservern, auf denen der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. Zur Vermeidung von TCP/UDP-Portkonflikten (User Datagram Protocol) verwenden der Microsoft Exchange Unified Messaging-Anrufrouterdienst und der Microsoft Exchange Unified Messaging-Dienst unterschiedliche Standardeinstellungen und überwachen unterschiedliche TCP-Ports. Sie können beide sowohl ungesicherte als auch gesicherte Verbindungen akzeptieren – abhängig davon, ob MTLS für SIP- und RTP-Datenverkehr eingesetzt wird. Standardmäßig überwacht ein Clientzugriffsserver sowohl TCP-Port 5060 im ungesicherten Modus als auch TCP-Port 5061 im SIP-gesicherten Modus auf SIP-Anforderungen, wenn MTLS verwendet wird. Diese Ports können mit dem Cmdlet **Set-UMCallRouterSettings** konfiguriert werden. Der Microsoft Exchange Unified Messaging-Anrufrouterdienst auf dem Clientzugriffsserver verarbeitet keinen Mediendatenverkehr (RTP oder SRTP), daher werden nur TCP-Ports und keine UDP-Ports verwendet. Standardmäßig überwacht ein Postfachserver sowohl TCP-Port 5062 im ungesicherten Modus als auch TCP-Port 5063 im SIP-gesicherten Modus auf SIP-Anforderungen, wenn MTLS verwendet wird. Diese Ports können nicht mithilfe von Cmdlets der Exchange-Verwaltungsshell konfiguriert werden. Der Microsoft Exchange Unified Messaging-Dienst auf dem Postfachserver akzeptiert Verbindungen von einem Clientzugriffsserver auf den SIP-Ports 5062 und 5063. Nachdem der Clientzugriffsserver die SIP-Anforderung an einen Postfachserver umgeleitet hat, wird ein RTP- oder SRTP-Medienkanal zwischen einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem SBC und dem Microsoft Exchange Unified Messaging-Arbeitsprozess auf dem Postfachserver eingerichtet.

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
<td><p>SIP (Clientzugriffsserver – Microsoft Unified Messaging-Call-Router-Dienst)</p></td>
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
<td><p>5065 und 5067 für TCP (ungesichert). 5065 und 5067 für MTLS (gesichert). Wenn Sie ihn auf den Dualmodus festgelegt haben, werden auch 5066 und 5068 verwendet.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ports können nicht geändert werden.</p></td>
</tr>
<tr class="even">
<td><p>RTP (Postfachserver – UM-Arbeitsprozess)</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ports zwischen 1024 und 65535.</p></td>
<td><p>Die Ports können in der Konfigurationsdatei <strong>msexchangeum.config</strong> geändert werden. Die Datei &quot;msexchangeum.config&quot; befindet sich auf einem Exchange 2013 Unified Messaging-Server im Ordner &quot;\Program Files\Microsoft\Exchange\V15\bin&quot;.</p></td>
</tr>
</tbody>
</table>


## Lync Server und UM-Ports

Exchange 2013 Unified Messaging unterstützt die NAT-Durchquerung (Network Address Translation, Netzwerkadressenübersetzung) und ermöglicht es RTP-Medien, eine NAT-Firewall eines Postfachservers mithilfe eines Tunnels zu passieren. Damit dies jedoch funktioniert, muss Microsoft Office Communications Server 2007 R2 und Microsoft Lync Server 2010 oder Microsoft Lync 2013 in Ihrer Umgebung installiert sein. Wenn Sie sowohl Exchange 2013 als auch Communications Server 2007 R2 oder Microsoft Lync Server 2010 oder Lync 2013 in Ihrem Netzwerk installiert haben, können Postfachserver dank dieser Bereitstellung den Microsoft Exchange Unified Messaging-Dienst ausführen, um mit Endpunkten außerhalb der NAT-Firewall zu kommunizieren. Der Postfachserver ist mit Communications Server 2007 R2, Microsoft Lync Server 2010 oder einem Lync 2013-Pool verknüpft und empfängt die entsprechenden Authentifizierungstoken vom A/V-Authentifizierungsdienst auf einem Computer, der diesem bestimmten Communications Server 2007- oder Lync Server-Pool zur Verfügung steht.

Der A/V-Authentifizierungsdienst wird verwendet, damit RTP-Sprachmedien NAT-Geräte und -Firewalls durchqueren können. Dies ist erforderlich, da Mediengateways nur Signale verarbeiten und Sprache nicht sicher über ein NAT-Gerät oder eine NAT-Firewall transportieren können. Wenn Sie einen Vermittlungsserver in Communications Server 2007 R2, Lync Server 2010 oder Lync 2013 konfigurieren, geben Sie den A/V-Edge-Server an, auf dem der A/V-Authentifizierungsdienst ausgeführt wird. Auf diese Weise ist der Vermittlungsserver darüber informiert, wohin die eingehenden Medienpakte weitergeleitet werden sollen.

Weitere Informationen zum Bereitstellen von Communications Server 2007 R2 oder Lync Server 2010 oder 2013 und Exchange 2013 Unified Messaging finden Sie in den folgenden Themen:

  - [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md)

  - [Prüfliste: Integrieren von Exchange 2013 UM in Lync Server](checklist-integrate-exchange-2013-um-with-lync-server-exchange-2013-help.md)

