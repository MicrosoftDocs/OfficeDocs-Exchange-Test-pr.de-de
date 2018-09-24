---
title: 'Netzwerkports f. Clients und Nach.fluss in Exchange 2013: Exchange 2013-Hilfe'
TOCTitle: Netzwerkports für Clients und Nachrichtenfluss in Exchange 2013
ms:assetid: fec09455-e99e-42eb-8b32-1ddc08d9a19e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb331973(v=EXCHG.150)
ms:contentKeyID: 64116870
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Netzwerkports für Clients und Nachrichtenfluss in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Dieses Thema enthält Informationen zu den von MicrosoftExchange Server 2013 für die Kommunikation mit E-Mail-Clients, Internet-E-Mail-Servern und anderen externen Diensten Ihrer lokalen Exchange-Organisation verwendeten Netzwerkports. Bevor wir dies vertiefen, möchten wir Sie zunächst mit den folgenden Grundregeln vertraut machen:

  - Das Beschränken oder Ändern des Netzwerkdatenverkehrs zwischen internen Exchange-Servern, zwischen internen Exchange-Servern und internen Lync-Servern oder Skype for Business-Servern oder zwischen internen Exchange-Servern und internen Active Directory-Domänencontrollern wird unabhängig vom Topologietyp nicht unterstützt. Wenn Sie über Firewalls oder Netzwerkgeräte verfügen, die diese Art von Netzwerkdatenverkehr möglicherweise einschränken oder ändern, müssen Sie Regeln konfigurieren, die eine freie und uneingeschränkte Kommunikation zwischen diesen Servern zulassen. (Dabei muss es sich um Regeln handeln, die ein- und ausgehenden Netzwerkdatenverkehr über alle Ports – einschließlich zufällige RPC-Ports – und Protokolle zulassen, die übertragene Bits in keinem Fall verändern.)

  - Edge-Transport-Server befinden sich fast immer in einem Umkreisnetzwerk, sodass erwartet wird, dass Sie den Netzwerkdatenverkehr zwischen dem Edge-Transport-Server und dem Internet sowie zwischen dem Edge-Transport-Server und Ihrer internen Exchange-Organisation beschränken. Diese Netzwerkports werden in diesem Thema beschrieben.

  - Es wird erwartet, dass Sie den Netzwerkverkehr zwischen externen Clients und Diensten und Ihrer internen Exchange-Organisation beschränken. Sie können auch den Netzwerkdatenverkehr zwischen internen Clients und internen Exchange-Servern beschränken. Diese Netzwerkports werden in diesem Thema beschrieben.

**Inhalt**

Für Clients und Dienste erforderliche Netzwerkports

Für den E-Mail-Fluss Netzwerkports (ohne Edge-Transport-Server)

Netzwerkports, die für den E-Mail-Fluss mit Edge-Transport-Servern erforderlich sind

Für Hybridbereitstellungen erforderliche Netzwerkports

Für Unified Messaging erforderliche Netzwerkports

## Für Clients und Dienste erforderliche Netzwerkports

Die Netzwerkports, die E-Mail-Clients für den Zugriff auf Postfächer und andere Dienste in der Exchange-Organisation benötigen, werden in der nachstehenden Abbildung und Tabelle beschrieben.

**Hinweise:** 

  - Das Ziel dieser Clients und Dienste ist ein Clientzugriffsserver. Dabei kann es sich um einen eigenständigen Clientzugriffsserver oder einen Clientzugriffsserver und Postfachserver handeln, die auf demselben Computer installiert sind.

  - Die Abbildung zeigt zwar Clients und Dienste aus dem Internet, die Konzepte für interne Clients (z. B. Clients in eine Kontengesamtstruktur, die auf Exchange-Server in einer Ressourcengesamtstruktur zugreifen) sind jedoch identisch. Entsprechend verfügt die Tabelle nicht über eine Quellspalte, da die Quelle ein beliebiger Ort außerhalb der Exchange-Organisation sein kann (z. B. das Internet oder eine Kontengesamtstruktur).

  - Edge-Transport-Server sind nicht am Netzwerkdatenverkehr beteiligt, der diesen Clients und Diensten zugeordnet ist.

![Für Clients und Dienste erforderliche Netzwerkports](images/Bb331973.f5ba3439-f001-43c8-848e-0e3fd0fce931(EXCHG.150).png "Für Clients und Dienste erforderliche Netzwerkports")


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Zweck</th>
<th>Ports</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verschlüsselte Webverbindungen werden von folgenden Clients und Diensten verwendet:</p>
<ul>
<li><p>AutoErmittlungsdienst</p></li>
<li><p>Exchange ActiveSync</p></li>
<li><p>Exchange Webdienste (EWS)</p></li>
<li><p>Offlineadressbuch-Verteilung</p></li>
<li><p>Outlook Anywhere (RPC über HTTP)</p></li>
<li><p>Outlook MAPI über HTTP</p></li>
<li><p>Outlook Web App</p></li>
</ul></td>
<td><p>443/TCP (HTTPS)</p></td>
<td><p>Weitere Informationen zu diesen Clients und Diensten finden Sie in den folgenden Themen:</p>
<ul>
<li><p><a href="autodiscover-service-for-exchange-2013.md">AutoErmittlungsdienst</a></p></li>
<li><p><a href="exchange-activesync-exchange-2013-help.md">Exchange ActiveSync</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/?linkid=529544">EWS-Referenz für Exchange</a></p></li>
<li><p><a href="offline-address-books-exchange-2013-help.md">Offlineadressbücher</a></p></li>
<li><p><a href="outlook-anywhere-exchange-2013-help.md">Outlook Anywhere</a></p></li>
<li><p><a href="mapi-over-http-exchange-2013-help.md">MAPI über HTTP</a></p></li>
<li><p><a href="what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md">Neuerungen bei Outlook Web App in Exchange 2013</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Unverschlüsselte Webverbindungen werden von folgenden Clients und Diensten verwendet:</p>
<ul>
<li><p>Veröffentlichen von Kalendern im Internet</p></li>
<li><p>Outlook Web App (Umleitung an 443/TCP)</p></li>
<li><p>AutoErmittlung (Fallback, wenn 443/TCP nicht verfügbar ist)</p></li>
</ul></td>
<td><p>80/TCP (HTTP)</p></td>
<td><p>Sofern möglich, empfehlen wir die Verwendung verschlüsselter Webverbindungen an 443/TCP zum Schutz von Daten und Anmeldeinformationen. Möglicherweise müssen einige Dienste jedoch für die Verwendung unverschlüsselter Webverbindungen mit dem Clientzugriffsserver an 80/TCP konfiguriert werden.</p>
<p>Weitere Informationen zu diesen Clients und Diensten finden Sie in den folgenden Themen:</p>
<ul>
<li><p><a href="enable-internet-calendar-publishing-exchange-2013-help.md">Aktivieren der Veröffentlichung von Kalenderinformationen im Internet</a></p></li>
<li><p><a href="what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md">Neuerungen bei Outlook Web App in Exchange 2013</a></p></li>
<li><p><a href="autodiscover-service-for-exchange-2013.md">AutoErmittlungsdienst</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>IMAP4-Clients</p></td>
<td><p>143/TCP (IMAP), 993/TCP (sicheres IMAP)</p></td>
<td><p>IMAP4 ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter <a href="pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md">POP3 und IMAP4 in Exchange Server 2013</a>.</p>
<p>Der IMAP4-Dienst auf dem Clientzugriffsserver dient als Proxy für Verbindungen mit dem IMAP4-Back-End-Dienst auf einem Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>POP3-Clients</p></td>
<td><p>110/TCP (POP3), 995/TCP (sicheres POP3)</p></td>
<td><p>POP3 ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter <a href="pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md">POP3 und IMAP4 in Exchange Server 2013</a>.</p>
<p>Der POP3-Dienst auf dem Clientzugriffsserver dient als Proxy für Verbindungen mit dem POP3-Back-End-Dienst auf einem Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>SMTP-Clients (authentifiziert)</p></td>
<td><p>587/TCP (authentifiziertes SMTP)</p></td>
<td><p>Der standardmäßige Empfangsconnector namens &quot;Client Frontend <em>&lt;Servername&gt;</em>&quot; lauscht an Port 587 des Clientzugriffsservers nach authentifizierten SMTP-Clientübermittlungen.</p>
<p><strong>Hinweis</strong></p>
<p>Wenn Sie über Clients verfügen, die authentifizierte SMTP-E-Mail nur an Port 25 übermitteln können, können Sie den Wert für Netzwerkadapterbindungen für diesen Empfangsconnector so ändern, dass er auf authentifizierte SMTP-E-Mail-Übermittlungen an Port 25 wartet.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Für den E-Mail-Fluss erforderliche Netzwerkports

Die Übermittlung von E-Mails an Ihre und aus Ihrer Exchange-Organisation richtet sich nach Ihrer Exchange-Topologie. Der wichtigste Faktor ist, ob Sie in Ihrem Umkreisnetzwerk einen abonnierten Edge-Transport-Server bereitgestellt haben.

## Für den E-Mail-Fluss Netzwerkports (ohne Edge-Transport-Server)

Die Netzwerkports, die für den E-Mail-Fluss in einer Exchange-Organisation mit nur Clientzugriffs- und Postfachservern erforderlich sind, werden in der folgenden Abbildung und Tabelle beschrieben. Obwohl die Abbildung getrennte Postfach- und Clientzugriffsserver zeigt, sind die Konzepte für auf demselben Computer oder auf getrennten Computern installierte Clientzugriffsserver und Postfachserver identisch.

![Für den E-Mail-Fluss Netzwerkports (ohne Edge-Transport-Server)](images/Bb331973.af54dfd3-fe6b-4b6e-bb8e-b00df94a0be0(EXCHG.150).png "Für den E-Mail-Fluss Netzwerkports (ohne Edge-Transport-Server)")


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Zweck</th>
<th>Ports</th>
<th>Quelle</th>
<th>Ziel</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Eingehende E-Mails</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Internet (alle)</p></td>
<td><p>Clientzugriffsserver</p></td>
<td><p>Der standardmäßige Empfangsconnector namens „Standard-Front-End <em>&lt;Client Access server name&gt;</em>“ auf dem Clientzugriffsserver lauscht an Port 25 nach anonymen eingehenden SMTP-E-Mails.</p>
<p>E-Mails werden vom Clientzugriffsserver mithilfe des impliziten und unsichtbaren organisationsinternen Sendeconnectors an einen Postfachserver weitergeleitet. Dieser Connector leitet E-Mails automatisch zwischen Exchange-Servern in der gleichen Organisation weiter.</p></td>
</tr>
<tr class="even">
<td><p>Ausgehende E-Mails</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Postfachserver</p></td>
<td><p>Internet (alle)</p></td>
<td><p>Standardmäßig erstellt Exchange keine Sendeconnectors, die das Senden von E-Mail an das Internet ermöglichen. Sie müssen Sendeconnectors manuell erstellen. Weitere Informationen finden Sie unter <a href="send-connectors-exchange-2013-help.md">Sendeconnectors</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Ausgehende E-Mails (bei Weiterleitung über den Clientzugriffsserver)</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Clientzugriffsserver</p></td>
<td><p>Internet (alle)</p></td>
<td><p>Ausgehende E-Mails werden nur dann über einen Clientzugriffsserver weitergeleitet, wenn ein Sendeconnector mit <strong>Proxy über Clientzugriffsserver</strong> im Exchange Admin Center oder <code>-FrontEndProxyEnabled $true</code> in der Exchange-Verwaltungsshell konfiguriert ist.</p>
<p>In diesem Fall lauscht der standardmäßige Empfangsconnector namens &quot;Outbound Proxy Frontend <em>&lt;Name des Clientzugriffsservers&gt;</em>&quot; auf dem Clientzugriffsserver nach ausgehenden E-Mails vom Postfachserver. Weitere Informationen finden Sie unter <a href="create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md">Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden</a>.</p></td>
</tr>
<tr class="even">
<td><p>DNS für die Namensauflösung des nächsten E-Mail-Hops (nicht abgebildet)</p></td>
<td><p>53/UDP, 53/TCP (DNS)</p></td>
<td><p>InternetfähigeExchange-Server (Clientzugriffsserver oder Postfachserver)</p></td>
<td><p>DNS-Server</p></td>
<td><p>Weitere Informationen finden Sie im Abschnitt Namensauflösung.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Netzwerkports, die für den E-Mail-Fluss mit Edge-Transport-Servern erforderlich sind

Ein abonnierter Edge-Transport-Server, der im Umkreisnetzwerk installiert ist, beseitigt im Wesentlichen den SMTP-E-Mail-Fluss durch den Clientzugriffsserver. Insbesondere gilt:

  - Ausgehende E-Mails von der Exchange-Organisation durchlaufen nie einen Clientzugriffsserver. E-Mails werden stets von einem Postfachserver am abonnierten Active Directory-Standort zum Edge-Transport-Server geleitet (ungeachtet der Version von Exchange auf dem Edge-Transport-Server).

  - Eingehende E-Mails durchlaufen nie einen eigenständigen Clientzugriffsserver. E-Mails werden vom Edge-Transport-Server an einen Postfachserver am abonnierten Active Directory-Standort geleitet. Wenn der Postfachserver und der Clientzugriffsserver auf demselben Computer installiert sind, werden E-Mails von einem Exchange 2013-Edge-Transport-Server zunächst zum Computer mit dem Front-End-Transportdienst (der Clientzugriffs-Serverrolle) geleitet, bevor sie zum Transportdienst (der Postfachserverrolle) geleitet werden. Exchange 2007 oder Exchange 2010-Edge-Transport-Server übertragen E-Mails immer direkt an den Transportdienst, selbst wenn Postfachserver und Clientzugriffsserver auf demselben Computer installiert sind.

Weitere Informationen finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).

Die Netzwerkports, die für den E-Mail-Fluss in Exchange-Organisationen erforderlich sind, die über Edge-Transport-Server verfügen, werden in der folgenden Abbildung und Tabelle beschrieben. Sofern nicht anders angegeben, gelten die Konzepte ungeachtet dessen, ob der Clientzugriffsserver und Postfachserver auf demselben Computer oder auf getrennten Computern installiert sind.

![Netzwerkports, die für den E-Mail-Fluss mit Edge-Transport-Servern erforderlich sind](images/Bb331973.110c79b3-dbd9-4cb5-bba1-02048363ee1c(EXCHG.150).png "Netzwerkports, die für den E-Mail-Fluss mit Edge-Transport-Servern erforderlich sind")


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Zweck</th>
<th>Ports</th>
<th>Quelle</th>
<th>Ziel</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Eingehende E-Mails - Internet zu Edge-Transport-Server</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Internet (alle)</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Der standardmäßige Empfangsconnector namens &quot;Default internal Receive connector <em>&lt;Name des Edge-Transport-Servers&gt;</em>&quot; auf dem Edge-Transport-Server lauscht an Port 25 nach anonymen SMTP-E-Mails.</p></td>
</tr>
<tr class="even">
<td><p>Eingehende E-Mails – Edge-Transport-Server zu interner Exchange-Organisation</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Postfachserver am abonnierten Active Directory-Standort</p></td>
<td><p>Der standardmäßige Sendeconnector mit dem Namen „EdgeSync – Inbound to <em>&lt;Name des Active Directory-Standorts&gt;</em>“ leitet an Port 25 eingehende E-Mails an beliebige Postfachserver am abonnierten Active Directory-Standort weiter. Weitere Informationen finden Sie im Abschnitt „Beim Edge-Abonnementprozess erstellte Sendeconnectors“ im Thema <a href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</a>.</p>
<p>Welcher Dienst E-Mails tatsächlich empfängt, hängt davon ab, ob Postfachserver und Clientzugriffsserver auf demselben Computer oder auf getrennten Computern installiert sind.</p>
<ul>
<li><p><strong>Eigenständiger Postfachserver</strong>   Der standardmäßige Empfangsconnector namens &quot;Default <em>&lt;Name des Postfachservers&gt;</em>&quot; lauscht an Port 25 nach eingehenden E-Mails (einschließlich E-Mails von Edge-Transport-Servern).</p></li>
<li><p><strong>Postfachserver und Clientzugriffsserver sind auf demselben Computer installiert</strong>   Der standardmäßige Empfangsconnector mit dem Namen „Default Frontend <em>&lt;Servername&gt;</em>“ im Front-End-Transportdienst (Clientzugriffs-Serverrolle) lauscht an Port 25 nach eingehenden E-Mails (einschließlich E-Mails von Exchange 2013-Edge-Transport-Servern).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Ausgehende E-Mails – interne Exchange-Organisation zu Edge-Transport-Server</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Postfachserver am abonnierten Active Directory-Standort</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Ausgehende E-Mails umgehen stets den Clientzugriffsserver.</p>
<p>E-Mails werden von einem beliebigen Postfachserver am abonnierten Active Directory-Standort mithilfe des impliziten und unsichtbaren organisationsinternen Sendeconnectors an einen Edge-Transport-Server weitergeleitet. Dieser Connector leitet E-Mails automatisch zwischen Exchange-Servern in derselben Organisation weiter.</p>
<p>Der standardmäßige Empfangsconnector mit dem Namen „Default internal Receive connector <em>&lt;Name des Edge-Transport-Server&gt;</em>“ auf dem Edge-Transport-Server lauscht an Port 25 nach SMTP-E-Mails von allen Postfachservern am abonnierten Active Directory-Standort.</p></td>
</tr>
<tr class="even">
<td><p>Ausgehende E-Mails – Edge-Transport-Server zu Internet</p></td>
<td><p>25/TCP (SMTP)</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Internet (alle)</p></td>
<td><p>Der standardmäßige Sendeconnector namens &quot;EdgeSync – <em>&lt;Name des Active Directory-Standorts&gt;</em> to Internet&quot; leitet an Port 25 ausgehende E-Mails vom Edge-Transport-Server an das Internet weiter.</p></td>
</tr>
<tr class="odd">
<td><p>EdgeSync-Synchronisierung</p></td>
<td><p>50636/TCP (sicheres LDAP)</p></td>
<td><p>Postfachserver am abonnierten Active Directory-Standort, die an der EdgeSync-Synchronisierung teilnehmen</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Wenn der Edge-Transport-Server für den Active Directory-Standort abonniert ist, nehmen alle Postfachserver, die zum jeweiligen Zeitpunkt an diesem Standort vorhanden sind, an der EdgeSync-Synchronisierung teil. Postfachserver, die Sie später hinzufügen, nehmen jedoch nicht automatisch an der EdgeSync-Synchronisierung teil.</p></td>
</tr>
<tr class="even">
<td><p>DNS für die Namensauflösung des nächsten E-Mail-Hops (nicht abgebildet)</p></td>
<td><p>53/UDP, 53/TCP (DNS)</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>DNS-Server</p></td>
<td><p>Weitere Informationen finden Sie im Abschnitt Namensauflösung.</p></td>
</tr>
<tr class="odd">
<td><p>Proxyserverdefinition für die Absenderzuverlässigkeit (nicht abgebildet)</p></td>
<td><p>Benutzerdefiniert</p></td>
<td><p>Edge-Transport-Server</p></td>
<td><p>Internet</p></td>
<td><p>Die Absenderzuverlässigkeit (der Protokollanalyse-Agent) analysiert die Pfade eingehender Nachrichten, um Spam zu reduzieren. Wenn Ihre Organisation einen Proxyserver zum Steuern des Zugriffs auf das Internet verwendet, müssen Sie Details zum Proxyserver definieren, damit die Absenderzuverlässigkeit ordnungsgemäß funktionieren kann (insbesondere die Erkennung offener Proxys und die Blockierung von Absendern). Sie geben die Parameter <em>ProxyServerName</em>, <em>ProxyServerPort</em> und <em>ProxyServerType</em> im Cmdlet <strong>Set-SenderReputationConfig</strong> an, um den Proxyserver Ihrer Organisation so zu definieren, dass die Absenderzuverlässigkeitsfunktion mit dem Internet eine erfolgreiche Verbindung herstellen kann. Weitere Informationen finden Sie unter <a href="manage-sender-reputation-exchange-2013-help.md">Verwalten der Absenderzuverlässigkeit</a>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Namensauflösung

DNS-Auflösung des nächsten E-Mail-Hops ist ein grundlegender Bestandteil des E-Mail-Flusses in jeder Exchange-Organisation. Exchange-Server, die für das Empfangen von eingehenden E-Mails oder das Übermitteln von ausgehenden E-Mails zuständig sind, müssen in der Lage sein, interne und externe Hostnamen für die richtige E-Mail-Weiterleitung aufzulösen. Alle internen Exchange-Server müssen in der Lage, interne Hostnamen für die richtige E-Mail-Weiterleitung aufzulösen . Es gibt zahlreiche Möglichkeiten zum Entwerfen einer DNS-Infrastruktur, doch wichtig ist es, eine ordnungsgemäße Funktionsweise der Namensauflösung des nächsten Hops für alle Exchange-Server sicherzustellen.

## Für Hybridbereitstellungen erforderliche Netzwerkports

Die Netzwerkports, die für eine Organisation erforderlich sind, in der sowohl Exchange 2013 als auch MicrosoftOffice 365 eingesetzt werden, finden Sie im Abschnitt "Protokolle, Ports und Endpunkte für Hybridbereitstellungen" in [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/de-de/library/hh534377\(v=exchg.150\)).

## Für Unified Messaging erforderliche Netzwerkports

Die Netzwerkports, die für Unified Messaging erforderlich sind, werden in den folgenden Themen behandelt:

  - [UM-Protokolle, Ports und Dienste](um-protocols-ports-and-services-exchange-2013-help.md)

  - [Poster der Exchange Server 2013 SP1-Architektur](https://go.microsoft.com/fwlink/p/?linkid=518646)

Zurück zum Seitenanfang

