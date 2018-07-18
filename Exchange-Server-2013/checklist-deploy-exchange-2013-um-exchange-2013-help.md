---
title: 'Prüfliste: Bereitstellen von Exchange 2013 UM: Exchange 2013 Help'
TOCTitle: 'Prüfliste: Bereitstellen von Exchange 2013 UM'
ms:assetid: 41b666a2-0d0d-471f-90a3-07c3c562af85
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673520(v=EXCHG.150)
ms:contentKeyID: 52062851
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste: Bereitstellen von Exchange 2013 UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Verwenden Sie diese Prüfliste zum Installieren und Bereitstellen von Unified Messaging (UM) in Ihrer Organisation.

Bevor Sie mit dieser Prüfliste arbeiten, machen Sie sich mit den Konzepten in folgenden Themen vertraut:

  - [Unified Messaging](unified-messaging-exchange-2013-help.md)

  - [Neue Voicemailfeatures](new-voice-mail-features-exchange-2013-help.md)

  - [Planen von Unified Messaging](planning-for-unified-messaging-exchange-2013-help.md)

Schrittanleitungen zur Bereitstellung von UM und Microsoft Lync Server finden Sie unter [Prüfliste: Integrieren von Exchange 2013 UM in Lync Server](checklist-integrate-exchange-2013-um-with-lync-server-exchange-2013-help.md).

## Prüfliste für die Bereitstellung von Unified Messaging


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
<td><p>Stellen Sie Telefoniekomponenten bereit, und konfigurieren Sie sie.</p></td>
<td><p><a href="connect-um-to-your-telephone-system-exchange-2013-help.md">Verbinden von UM mit Ihrer Telefonanlage</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Überprüfen Sie die Systemanforderungen vor der Installation von Exchange 2013.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Stellen Sie sicher, dass die Voraussetzungen für die Installation erfüllt sind.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Installieren Sie die erforderlichen Clientzugriffs- und Postfachserver.</p>

> [!WARNING]
> Sie müssen mindestens einen Exchange&nbsp;2013-Postfachserver in Ihrer Organisation bereitstellen, bevor Sie die VoIP-Gateways oder IP/PBX-Systeme konfigurieren können, um UM-SIP- und RTP-Datenverkehr an die Exchange&nbsp;2013-Clientzugriffsserver zu senden.


</td>
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
<td><p>Erstellen Sie die erforderliche Anzahl von UM-Wählplänen für Ihre Organisation.</p></td>
<td><p><a href="create-a-um-dial-plan-exchange-2013-help.md">Erstellen eines UM-Wählplans</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie die Wählplansicherheitseinstellung.</p></td>
<td><p><a href="configure-the-voip-security-setting-exchange-2013-help.md">Konfigurieren der VoIP-Sicherheitseinstellung</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Konfigurieren Sie den UM-Startmodus für die einzelnen Clientzugriffs- und Postfachserver.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Postfachserver</a></p>
<p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Clientzugriffsserver</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie die Anzahl gleichzeitiger Anrufe auf Ihren Postfachservern.</p></td>
<td><p><a href="configure-the-number-of-incoming-calls-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren Sie die Anzahl eingehender Anrufe auf einem Postfachserver</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren Sie Outlook Voice Access-Nummern und andere Einstellungen.</p></td>
<td><p><a href="manage-a-um-dial-plan-exchange-2013-help.md">Verwalten eines UM-Wählplans</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie Outbound Dialing für Unified Messaging.</p></td>
<td><p><a href="authorize-calls-using-dialing-rules-exchange-2013-help.md">Autorisieren von Anrufen mit Wählregeln</a></p>
<p><a href="authorize-calls-for-users-in-a-dial-plan-exchange-2013-help.md">Autorisieren von Anrufen für Benutzer in einem Wählplan</a></p>
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
<td><p><strong> </strong></p></td>
<td><p>Erstellen, importieren und aktivieren Sie ein neues Exchange-Zertifikat für UM, oder aktivieren Sie ein Drittanbieterzertifikat mit gegenseitiger Vertrauensstellung. Importieren Sie das Zertifikat außerdem auf allen VoIP-Gateways, IP-Nebenstellenanlagen und SBCs.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Starten Sie den Microsoft Exchange Unified Messaging-Dienst und den Unified Messaging-Dienst für die Anrufweiterleitung auf allen Exchange-Servern neu, um die erforderlichen Zertifikate zu laden.</p></td>
<td><p><a href="stop-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Beenden des Microsoft Exchange Unified Messaging-Diensts</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Starten des Microsoft Exchange Unified Messaging-Diensts</a></p>
<p><a href="stop-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Starten des Microsoft Exchange Unified Messaging-Anrufrouterdiensts</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Erstellen Sie eine UM-Postfachrichtlinie, oder konfigurieren Sie die UM-Standardpostfachrichtlinie.</p></td>
<td><p><a href="create-a-um-mailbox-policy-exchange-2013-help.md">Erstellen einer UM-Postfachrichtlinie</a></p>
<p><a href="manage-a-um-mailbox-policy-exchange-2013-help.md">Verwalten einer UM-Postfachrichtlinie</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Aktivieren Sie Benutzer für Unified Messaging mit einer Durchwahlnummer und einer E.164-Nummer, falls erforderlich.</p></td>
<td><p><a href="enable-a-user-for-voice-mail-exchange-2013-help.md">Aktivieren eines Benutzers für Voicemail</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Aktivieren Sie eingehende Faxe (optional).</p></td>
<td><p><a href="enable-voice-mail-users-to-receive-faxes-exchange-2013-help.md">Aktivieren von Voicemailbenutzern für den Faxempfang</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Richten Sie geschützte Voicemail ein (optional).</p></td>
<td><p><a href="protect-voice-mail-exchange-2013-help.md">Schützen von Voicemail</a></p></td>
</tr>
</tbody>
</table>


Prüfliste für die Bereitstellung von Unified Messaging

