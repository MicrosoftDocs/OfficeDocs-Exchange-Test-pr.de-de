---
title: 'Prüfl.: Aktual. v. Exchange 2010 UM auf Exchange 2013 UM: Exchange 2013-Hilfe'
TOCTitle: 'Prüfliste: Aktualisieren von Exchange 2010 UM auf Exchange 2013 UM'
ms:assetid: 799bd1b1-a918-4bd8-911e-e6ca08bd7b52
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn169228(v=EXCHG.150)
ms:contentKeyID: 54652693
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Prüfliste: Aktualisieren von Exchange 2010 UM auf Exchange 2013 UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Nutzen Sie diese Prüfliste als Hilfestellung beim Upgrade von Exchange 2010 Unified Messaging (UM) auf Exchange 2013 UM. Greifen Sie beim Upgrade Ihrer Exchange 2010-Organisation und Ihrer UM-Bereitstellung auf Exchange 2013 auf diese Informationen zurück. Weitere Informationen zur schrittweisen Anleitung beim Upgrade auf Exchange 2013 UM finden Sie unter [Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging](upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md).

Bevor Sie mit dieser Prüfliste arbeiten, machen Sie sich mit den Konzepten in folgenden Themen vertraut:

  - [Planen von Unified Messaging](planning-for-unified-messaging-exchange-2013-help.md)

  - [Telefonsystemintegration mit UM](telephone-system-integration-with-um-exchange-2013-help.md)

  - [Verbinden Ihres Voicemailsystems mit Ihrem Telefonnetz](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/connect-voice-mail-system)

Weitere Informationen zur schrittweisen Anleitung beim Upgrade von Exchange 2007 UM auf Exchange 2013 UM finden Sie unter [Aktualisieren von Exchange 2007 Unified MESSAGING auf Exchange 2013 UM](upgrade-exchange-2007-um-to-exchange-2013-um-exchange-2013-help.md).

## Prüfliste für das Upgrade von Exchange 2010 UM auf Exchange 2013 UM


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
<td><p></p></td>
<td><p>Stellen Sie sicher, dass die Voraussetzungen für die Installation erfüllt sind.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
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
<td><p></p></td>
<td><p>Installieren Sie gegebenenfalls die erforderlichen UM-Sprachpakete.</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Installieren eines Sprachpakets</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Verschieben Sie das Exchange 2010-Systempostfach für benutzerdefinierte UM-Ansagen nach Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p>

> [!NOTE]
> Wenn das Systempostfach bereits verschoben wurde, können Sie benutzerdefinierte Ansagen weiterhin nach den Anweisungen unter <A href="import-and-export-custom-greetings-announcements-menus-and-prompts-exchange-2013-help.md">Importieren und Exportieren angepasster Begrüßungen, Informationsansagen, Menüs und Menüansagen</A> manuell aus Exchange 2010 exportieren/importieren.


</td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Exportieren und importieren Sie Zertifikate.</p></td>
<td><p><a href="deploying-certificates-for-um-exchange-2013-help.md">Bereitstellen von Zertifikaten für Unified Messaging</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren Sie den UM-Startmodus auf allen Exchange 2013-Clientzugriffsservern.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Clientzugriffsserver</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie den UM-Startmodus auf allen Exchange 2013-Postfachservern.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Postfachserver</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen oder konfigurieren Sie UM-Wählpläne.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan">Erstellen eines UM-Wählplans</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/manage-um-dial-plan">Verwalten eines UM-Wählplans</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Erstellen oder konfigurieren Sie UM-IP-Gateways.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway">Erstellen eines UM-IP-Gateways</a></p>
<p><a href="manage-a-um-ip-gateway-exchange-2013-help.md">Verwalten eines UM-IP-Gateways</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen Sie einen UM-Sammelanschluss.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-hunt-group">Erstellen eines UM-Sammelanschlusses</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Erstellen oder konfigurieren Sie automatische UM-Telefonzentralen.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant">Erstellen einer automatischen UM-Telefonzentrale</a></p>
<p><a href="manage-a-um-auto-attendant-exchange-2013-help.md">Verwalten einer automatischen UM-Telefonzentrale</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen oder konfigurieren Sie UM-Postfachrichtlinien.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy">Erstellen einer UM-Postfachrichtlinie</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-um-mailbox-policy">Verwalten einer UM-Postfachrichtlinie</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Verschieben Sie vorhandene UM-aktivierte Postfächer nach Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Aktivieren Sie neue Benutzer für UM, oder konfigurieren Sie Einstellungen für einen vorhandenen UM-aktivierten Benutzer.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail">Aktivieren eines Benutzers für Voicemail</a></p>
<p><a href="manage-voice-mail-settings-for-a-user-exchange-2013-help.md">Verwalten von Voicemail-Einstellungen für einen Benutzer</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren Sie VoIP-Gateways, IP-Festnetztelefonanlagen und SIP-aktivierte PBX-Anlagen für das Senden aller eingehenden Anrufe an die Exchange 2013-Clientzugriffsserver.</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/protected-voice-mail-procedures">Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen</a> <a href="connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md">Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Deaktivieren Sie die Anrufbeantwortung auf Exchange 2010 UM-Servern.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296335">Deaktivieren von Unified Messaging auf Exchange 2010</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Entfernen Sie einen Exchange 2010 UM-Server aus einem Wählplan.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296336">Entfernen ein UM-Servers aus einem Wählplan</a></p></td>
</tr>
</tbody>
</table>

