---
title: 'Prüfliste: Upgrade von Exchange 2010: Exchange 2013 Help'
TOCTitle: 'Prüfliste: Upgrade von Exchange 2010'
ms:assetid: 06c1045a-5fcf-4e24-a901-1a979302fb8d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee332309(v=EXCHG.150)
ms:contentKeyID: 51409262
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste: Upgrade von Exchange 2010

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Führen Sie anhand dieser Prüfliste das Upgrade von Microsoft Exchange 2010 auf Exchange 2013 durch. Machen Sie sich mit den Konzepten in folgenden Themen vertraut, bevor Sie diese Prüfliste durchgehen:

  - [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md)

  - [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md)

Diese Prüfliste hat insofern allgemeinen Charakter, als sie Hilfestellung für ein typisches Upgradeszenario bietet.


> [!NOTE]
> Der Exchange Server Bereitstellungs-Assistent bietet eine schrittweise Anleitung für die Bereitstellung von Exchange Server. Der Bereitstellungs-Assistent kann Sie bei Bereitstellung einer Neuinstallation von Exchange Server&nbsp;2013, dem Upgrade einer früheren Version auf Exchange&nbsp;2013 oder der Konfiguration einer Hybridbereitstellung von Exchange&nbsp;2013 und Exchange Online unterstützen. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.



## Prüfliste für das Upgrade von Exchange 2010 auf Exchange 2013


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Fertig?</p></td>
<td><p>Aufgabe</p></td>
<td><p>Themen</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1. Lesen der Anmerkungen zu dieser Version.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Versionshinweise zu Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>2. Prüfen von Systemanforderungen</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>3. Bestätigen, dass die erforderlichen Schritte ausgeführt wurden</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p>
<p><a href="deployment-security-checklist-exchange-2013-help.md">Prüfliste für Bereitstellungssicherheit</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>4. Konfigurieren eines nicht zusammenhängenden Namespaces</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Ihre Organisation einen nicht zusammenhängenden Namespace verwendet.


</td>
<td><p><a href="configure-the-dns-suffix-search-list-for-a-disjoint-namespace-exchange-2013-help.md">Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>5. Auswählen eines Offlineadressbuchs für alle Exchange 2010-Postfachdatenbanken</p></td>
<td><p><a href="manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md">Set mailbox database properties</a> in <a href="manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md">Verwalten von Postfachdatenbanken in Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>6. Installieren von Exchange 2013</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten</a></p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Überprüfen einer Exchange 2013-Installation</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>7. Erstellen eines Exchange 2013-Postfachs</p></td>
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">Erstellen von Benutzerpostfächern</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Konfigurieren von Exchange-bezogenen virtuellen Verzeichnissen</p>

> [!NOTE]
> Dieser Schritt ist erforderlich, wenn Sie Exchange-Webdienste, Outlook Anywhere oder das Offlineadressbuch verwenden möchten. Er kann auch erforderlich sein, wenn Sie eine der Standardeinstellungen für die Exchange-Systemsteuerung, Microsoft OfficeOutlook Web App oder Exchange ActiveSync ändern müssen.<BR>


</td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Konfiguration des Exchange 2013-Clientzugriffsservers</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Hinzufügen digitaler Zertifikate auf dem Clientzugriffsserver</p></td>
<td><p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Digitale Zertifikate und SSL</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>10. Verschieben des Vermittlungspostfachs</p></td>
<td><p><a href="move-the-exchange-2010-system-mailbox-to-exchange-2013-exchange-2013-help.md">Verschieben des Exchange 2010-Systempostfachs nach Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Konfigurieren von Unified Messaging</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn in der Organisation Unified Messaging verwendet werden soll.


</td>
<td><p><a href="upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md">Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>12. Konfigurieren des Edge-Transport-Servers</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Ihre Organisation einen Edge-Transport-Server verwendet.


</td>
<td><p><a href="configure-internet-mail-flow-through-a-subscribed-edge-transport-server-exchange-2013-help.md">Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>13. Aktivieren und Konfigurieren von Outlook Anywhere</p></td>
<td><p><a href="outlook-anywhere-exchange-2013-help.md">Outlook Anywhere</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>14. Konfigurieren des Dienstverbindungspunkts</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Konfiguration des Exchange 2013-Clientzugriffsservers</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Konfigurieren von DNS-Einträgen</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/dn307232(v=exchg.150)">Konfigurieren von DNS-Einträgen für Exchange 2010 mit einer multiplen Serverinstallation</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>16. Verschieben von Postfächern von Exchange 2010 nach Exchange 2013</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>17. Verschieben von Daten in Öffentlichen Ordnern von Exchange 2013 nach Exchange 2013</p></td>
<td><p><a href="public-folders-exchange-2013-help.md">Öffentliche Ordner</a></p>
<p><a href="https://technet.microsoft.com/de-de/library/jj150486(v=exchg.150)">Verwenden der seriellen Migration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>18. Tasks nach der Installation</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Aufgaben nach der Installation von Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

