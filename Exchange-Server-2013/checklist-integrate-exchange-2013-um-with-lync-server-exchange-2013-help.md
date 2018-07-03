---
title: 'Prüfliste: Integrieren von Exchange 2013 UM in Lync Server: Exchange 2013 Help'
TOCTitle: 'Prüfliste: Integrieren von Exchange 2013 UM in Lync Server'
ms:assetid: 3b82e86f-9f30-4445-96ad-744082abeaeb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638120(v=EXCHG.150)
ms:contentKeyID: 52062858
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste: Integrieren von Exchange 2013 UM in Lync Server

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Verwenden Sie diese Prüfliste für die Installation und Bereitstellung von Unified Messaging (UM) und Microsoft Lync Server 2013. In diesem Thema bezieht "Lync Server" sich auch auf Lync Server 2010. Microsoft Office Communications Server 2007 R2 kann jedoch auch mit Unified Messaging bereitgestellt werden.

> [!NOTE]  


Bevor Sie mit dieser Prüfliste arbeiten, machen Sie sich mit den Konzepten in folgenden Themen vertraut:

  - [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md)

  - [Koexistenz mit Office Communications Server 2007 R2 und Lync Server](coexistence-with-office-communications-server-2007-r2-and-lync-server-exchange-2013-help.md)

Weitere Informationen zum Durchführen der für Lync Server erforderlichen Aufgaben finden Sie unter [Microsoft Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=265752).

## Prüfliste für die Bereitstellung von Microsoft Lync Server und Unified Messaging


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Erledigt?</th>
<th>Aufgaben</th>
<th>Thema</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Überprüfen Sie vor der Installation von Exchange Server 2013 die Systemanforderungen.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Stellen Sie sicher, dass die Voraussetzungen für die Installation erfüllt sind.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Überprüfen Sie die Voraussetzungen für die Integration von Microsoft Lync Server 2013 und Microsoft Exchange Server 2013.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282082">Voraussetzungen für die Integration von Microsoft Lync Server 2013 und Microsoft Exchange Server 2013</a></p>

> [!TIP]
> Die UCMA 4.0-Runtime (Unified Communications Managed API) ist für Exchange 2013 und für Lync Server 2010 und 2013 erforderlich und wird während der Installation installiert. Informationen zu UCMA 4.0 und die Möglichkeit zum Herunterladen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=258269">Unified Communications Managed API 4.0 Runtime</A>


</td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Installieren Sie die erforderlichen Clientzugriffs- und Postfachserver.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Überprüfen Sie die Installation, und prüfen Sie die Protokolle des Serversetups.</p></td>
<td><p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Überprüfen einer Exchange 2013-Installation</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Installieren Sie gegebenenfalls die erforderlichen UM-Sprachpakete.</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Installieren eines Sprachpakets</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Erstellen Sie die Anzahl von SIP-URI-Wähleinstellungen, die für Ihr Unternehmen erforderlich sind.</p></td>
<td><p><a href="create-a-um-dial-plan-exchange-2013-help.md">Erstellen eines UM-Wählplans</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie die Wählplansicherheitseinstellung.</p></td>
<td><p><a href="configure-the-voip-security-setting-exchange-2013-help.md">Konfigurieren der VoIP-Sicherheitseinstellung</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren Sie die Anzahl gleichzeitiger Anrufe auf Ihren Postfachservern.</p></td>
<td><p><a href="configure-the-number-of-incoming-calls-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren Sie die Anzahl eingehender Anrufe auf einem Postfachserver</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie Outlook Voice Access-Nummern und andere Einstellungen.</p></td>
<td><p><a href="manage-a-um-dial-plan-exchange-2013-help.md">Verwalten eines UM-Wählplans</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Fügen Sie jedem SIP-URI-Wählplan alle Clientzugriffsserver und Postfachserver hinzu.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie Outbound Dialing für Unified Messaging. Lassen Sie alle Anrufe in den SIP-URI-Wählplänen und UM-Postfachrichtlinien zu, die mit diesen Wählplänen verknüpft sind.</p></td>
<td><p><a href="authorize-calls-for-users-in-a-dial-plan-exchange-2013-help.md">Autorisieren von Anrufen für Benutzer in einem Wählplan</a></p>
<p><a href="authorize-calls-for-a-group-of-users-exchange-2013-help.md">Autorisieren von Anrufen für eine Gruppe von Benutzern</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen Sie die erforderliche Anzahl automatischer Telefonzentralen.</p></td>
<td><p><a href="create-a-um-auto-attendant-exchange-2013-help.md">Erstellen einer automatischen UM-Telefonzentrale</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Richten Sie alle automatischen UM-Telefonzentralen ein, und konfigurieren Sie sie.</p></td>
<td><p><a href="set-up-a-um-auto-attendant-exchange-2013-help.md">Einrichten einer automatischen UM-Telefonzentrale</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Erstellen, importieren und aktivieren Sie ein neues Exchange-Zertifikat für UM, oder aktivieren Sie ein Drittanbieterzertifikat mit gegenseitiger Vertrauensstellung.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Konfigurieren Sie den UM-Startmodus für jeden Clientzugriffs- und Postfachserver im Dual- oder TLS-Modus.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Postfachserver</a></p>
<p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Clientzugriffsserver</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Starten Sie den Microsoft Exchange Unified Messaging-Dienst und den Unified Messaging-Dienst für die Anrufweiterleitung auf allen Exchange-Servern neu, um die erforderlichen Zertifikate zu laden.</p></td>
<td><p><a href="stop-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Beenden des Microsoft Exchange Unified Messaging-Diensts</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Starten des Microsoft Exchange Unified Messaging-Diensts</a></p>
<p><a href="stop-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Starten des Microsoft Exchange Unified Messaging-Anrufrouterdiensts</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Erstellen Sie eine UM-Postfachrichtlinie, oder konfigurieren Sie die UM-Standardpostfachrichtlinie.</p></td>
<td><p><a href="create-a-um-mailbox-policy-exchange-2013-help.md">Erstellen einer UM-Postfachrichtlinie</a></p>
<p><a href="manage-a-um-mailbox-policy-exchange-2013-help.md">Verwalten einer UM-Postfachrichtlinie</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Aktivieren Sie Benutzer für Unified Messaging mit einer SIP-Adresse, und verknüpfen Sie sie mit einem SIP-URI-Wählplan.</p></td>
<td><p><a href="enable-a-user-for-voice-mail-exchange-2013-help.md">Aktivieren eines Benutzers für Voicemail</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Lesen Sie die Dokumentation zur Planung von Lync Server 2013.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282081">Planung</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Installieren Sie Lync Server 2013, und stellen Sie es bereit.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282051">Bereitstellen von Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Importieren Sie die interne PKI oder das Drittanbieterzertifikat mit gegenseitiger Vertrauensstellung, das auf die Exchange-UM-Server importiert wird.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281863">Konfigurieren von Zertifikaten für Server</a></p>
<p><a href="https://go.microsoft.com/fwlink/p/?linkid=281865">Konfigurieren von Zertifikaten auf dem Server, auf dem Microsoft Exchange Server Unified Messaging ausgeführt wird</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Starten Sie ggf. Lync-Dienste auf Servern, um die Zertifikate zu laden.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282084">Starten von Diensten auf Servern</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie das Skript &quot;exchucutil.ps1&quot; aus, das sich im Ordner &quot;%Programme%\Microsoft\Exchange Server\V15\Scripts&quot; befindet.</p>
<p></p></td>
<td><p><a href="configure-um-to-work-with-lync-server-exchange-2013-help.md">Konfigurieren der Zusammenarbeit von Unified Messaging mit Lync Server</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Überprüfen Sie die Anforderungen für Enterprise-VoIP.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281876">Erforderliche Software für Enterprise-VoIP</a></p>
<p><a href="https://go.microsoft.com/fwlink/p/?linkid=281875">Anforderungen an Sicherheit und Konfiguration für Enterprise-VoIP</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Stellen Sie Mediengateways oder Vermittlungsserver bereit, konfigurieren Sie diese, und definieren Sie Peers.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281872">Bereitstellen von Vermittlungsservern und Definieren von Peers</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren Sie einen Trunk zwischen einem Vermittlungsserver und einem oder mehreren Peers, um eine Festnetzverbindung (PSTN, Public Switched Telephone Network) bereitzustellen.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281868">Konfigurieren von Trunks</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Erstellen und konfigurieren Sie einen Lync-Wählplan, und erstellen und definieren Sie Normalisierungsregeln, und ordnen Sie diese zu.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281867">Konfigurieren von Wählplänen</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren Sie VoIP-Richtlinien, und definieren Sie die Telefonnutzung und Routen für ausgehende Anrufe.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281869">Konfigurieren von VoIP-Richtlinien, PSTN-Verwendungsdatensätzen und VoIP-Routen</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Führen Sie das Hilfsprogramm für die Exchange-Integration (ocsumutil.exe) aus, welches die Kontaktobjekte für Outlook Voice Access und für die automatischen Telefonzentralen erstellt.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281866">Konfigurieren von Lync Server 2013 für die Zusammenarbeit mit Unified Messaging auf Microsoft Exchange Server</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Definieren und konfigurieren Sie alle erforderlichen erweiterten Enterprise-VoIP-Funktionen, und stellen Sie diese bereit.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281871">Bereitstellen von erweiterten Enterprise-VoIP-Funktionen</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Aktivieren Sie die Benutzer für Enterprise-VoIP. Geben Sie einen Anschluss-URI ein, und weisen Sie eine VoIP-Richtlinie und einen Lync-Wählplan zu.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281873">Aktivieren von Benutzern für Enterprise-VoIP</a></p></td>
</tr>
</tbody>
</table>

