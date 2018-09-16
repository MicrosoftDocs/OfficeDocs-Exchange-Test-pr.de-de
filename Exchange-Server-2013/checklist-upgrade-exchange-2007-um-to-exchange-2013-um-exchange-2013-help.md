---
title: 'Prüfliste: Upgr. v. Exchange 2007 UM a. Exchange 2013 UM: Exchange 2013-Hilfe'
TOCTitle: 'Prüfliste: Upgrade von Exchange 2007 UM auf Exchange 2013 UM'
ms:assetid: 99b1a081-4052-4516-b63c-77622cbdf962
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn169229(v=EXCHG.150)
ms:contentKeyID: 54652699
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Prüfliste: Upgrade von Exchange 2007 UM auf Exchange 2013 UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Verwenden Sie diese Prüfliste für das Upgrade von Exchange 2007 Unified Messaging (UM) auf Exchange 2013 UM. Nutzen Sie die Informationen unbedingt beim Upgrade Ihrer Exchange 2007-Organisation und Ihrer UM-Bereitstellung auf Exchange 2013. Schrittweise Anleitungen für das Upgrade auf Exchange 2013 UM finden Sie unter [Aktualisieren von Exchange 2007 Unified MESSAGING auf Exchange 2013 UM](upgrade-exchange-2007-um-to-exchange-2013-um-exchange-2013-help.md).

Bevor Sie mit dieser Prüfliste arbeiten, machen Sie sich mit den Konzepten in folgenden Themen vertraut:

  - [Planen von Unified Messaging](planning-for-unified-messaging-exchange-2013-help.md)

  - [Telefonsystemintegration mit UM](https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephone-system-integration-with-um)

  - [Verbinden Ihres Voicemailsystems mit Ihrem Telefonnetz](https://technet.microsoft.com/de-de/library/JJ673554(v=EXCHG.150))

Eine Schritt-für-Schritt-Anleitung für das Upgrade von Exchange 2010 UM auf Exchange 2013 UM finden Sie unter [Prüfliste: Aktualisieren von Exchange 2010 UM auf Exchange 2013 UM](checklist-upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md).

## Prüfliste für das Upgrade von Exchange 2007 UM auf Exchange 2013 UM


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
<td><p>Bereitstellen und Konfigurieren der Telefoniekomponenten</p></td>
<td><p><a href="connect-um-to-your-telephone-system-exchange-2013-help.md">Verbinden von UM mit Ihrer Telefonanlage</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Überprüfen der Systemanforderungen vor der Installation von Exchange 2013</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Sicherstellen, dass die Voraussetzungen für die Installation erfüllt sind</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Installieren der erforderlichen Clientzugriffs- und Postfachserver</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Überprüfen der Installation und der Protokolle des Serversetups</p></td>
<td><p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Überprüfen einer Exchange 2013-Installation</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Gegebenenfalls Installieren der erforderlichen UM-Sprachpakete</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Installieren eines Sprachpakets</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Importieren von Wähleinstellungen und benutzerdefinierten Ansagen für die automatische Telefonzentrale</p></td>
<td><p><a href="import-custom-prompts-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Importieren benutzerdefinierter Ansagen von Exchange 2007 zu Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Exportieren und Importieren von Zertifikaten</p></td>
<td><p><a href="deploying-certificates-for-um-exchange-2013-help.md">Bereitstellen von Zertifikaten für Unified Messaging</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Konfigurieren des UM-Startmodus auf allen Exchange 2013-Clientzugriffsservern</p></td>
<td><p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Clientzugriffsserver</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren des UM-Startmodus auf allen Exchange 2013-Postfachservern</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Konfigurieren des Startmodus auf einem Postfachserver</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen oder Konfigurieren vorhandener UM-Wähleinstellungen</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan">Erstellen eines UM-Wählplans</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/manage-um-dial-plan">Verwalten eines UM-Wählplans</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Erstellen oder Konfigurieren vorhandener UM-IP-Gateways</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway">Erstellen eines UM-IP-Gateways</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/manage-um-ip-gateway">Verwalten eines UM-IP-Gateways</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen eines UM-Sammelanschlusses</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-hunt-group">Erstellen eines UM-Sammelanschlusses</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Erstellen oder Konfigurieren automatischer UM-Telefonzentralen</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant">Erstellen einer automatischen UM-Telefonzentrale</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/manage-um-auto-attendant">Verwalten einer automatischen UM-Telefonzentrale</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Erstellen oder Konfigurieren von UM-Postfachrichtlinien</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy">Erstellen einer UM-Postfachrichtlinie</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-um-mailbox-policy">Verwalten einer UM-Postfachrichtlinie</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Verschieben vorhandener UM-aktivierter Postfächer nach Exchange 2013</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Aktivieren neuer Benutzer für UM oder Konfigurieren von Einstellungen für einen vorhandenen UM-aktivierten Benutzer</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail">Aktivieren eines Benutzers für Voicemail</a></p>
<p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-voice-mail-settings">Verwalten von Voicemail-Einstellungen für einen Benutzer</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Konfigurieren der VoIP-Gateways, IP-Nebenstellenanlagen und SIP-aktivierten Nebenstellenanlagen für das Senden aller eingehenden Anrufe an die Exchange 2013-Clientzugriffsserver</p></td>
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/protected-voice-mail-procedures">Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen</a></p>
<p><a href="connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md">Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Deaktivieren der Mailboxansage auf den Exchange 2007-UM-Servern</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296353">Gewusst wie: Deaktivieren von Unified Messaging auf Exchange 2007</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Entfernen eines Exchange 2007-UM-Servers aus einem Satz Wähleinstellungen</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=194765">So entfernen Sie einen Unified Messaging-Servers aus einem Wählplan</a></p></td>
</tr>
</tbody>
</table>

