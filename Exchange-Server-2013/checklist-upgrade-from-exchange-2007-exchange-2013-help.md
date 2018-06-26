---
title: 'Prüfliste: Upgrade von Exchange 2007: Exchange 2013 Help'
TOCTitle: 'Prüfliste: Upgrade von Exchange 2007'
ms:assetid: 53aaa370-4562-43e4-9b75-7a705400c5a5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff805032(v=EXCHG.150)
ms:contentKeyID: 51409304
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste: Upgrade von Exchange 2007

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Führen Sie anhand dieser Prüfliste das Upgrade von Microsoft Exchange Server 2007 auf Exchange Server 2013 durch. Bevor Sie mit dieser Prüfliste arbeiten, machen Sie sich mit den Konzepten in folgenden Themen vertraut:

  - [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md)

  - [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md)

Diese Prüfliste hat insofern allgemeinen Charakter, als sie Hilfestellung für ein typisches Upgradeszenario bietet.


> [!NOTE]
> Der Exchange Server Bereitstellungs-Assistent bietet eine schrittweise Anleitung für die Bereitstellung von Exchange Server. Der Bereitstellungs-Assistent kann Sie bei Bereitstellung einer Neuinstallation von Exchange Server&nbsp;2013, dem Upgrade einer früheren Version auf Exchange&nbsp;2013 oder der Konfiguration einer Hybridbereitstellung von Exchange&nbsp;2013 und Exchange Online unterstützen. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.



## Prüfliste für das Upgrade von Exchange 2007 auf Exchange 2013


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
<td><p>1. Lesen Sie die Anmerkungen zu dieser Version.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Versionshinweise zu Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>2. Prüfen von Systemanforderungen</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>3. Bestätigen, dass die erforderlichen Schritte ausgeführt wurden</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p>
<p><a href="deployment-security-checklist-exchange-2013-help.md">Prüfliste für Bereitstellungssicherheit</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>4. Konfigurieren eines nicht zusammenhängenden Namespaces</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Ihre Organisation einen nicht zusammenhängenden Namespace verwendet.


</td>
<td><p><a href="configure-the-dns-suffix-search-list-for-a-disjoint-namespace-exchange-2013-help.md">Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>5. Auswählen eines Offlineadressbuchs für alle Exchange 2007-Postfachdatenbanken</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/?linkid=320546">Zuordnen von Empfängern für Downloads von Offlineadressbüchern</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>6. Erstellen eines Exchange-Legacyhostnamens</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/dn130105(v=exchg.150)">Erstellen eines Legacy-Exchange-Hostnamens</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>7. Installieren von Exchange 2013</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten</a></p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Überprüfen einer Exchange 2013-Installation</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Erstellen eines Exchange 2013-Postfachs</p></td>
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">Erstellen von Benutzerpostfächern</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Konfigurieren von Exchange-bezogenen virtuellen Verzeichnissen</p>

> [!NOTE]
> Dieser Schritt ist erforderlich, wenn Sie Exchange-Webdienste, Outlook Anywhere oder das Offlineadressbuch verwenden möchten. Er kann auch erforderlich sein, wenn Sie eine der Standardeinstellungen für die Exchange-Systemsteuerung, Microsoft OfficeOutlook Web App oder Exchange ActiveSync ändern müssen.<BR>


<p></p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Konfiguration des Exchange 2013-Clientzugriffsservers</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>10. Konfigurieren von Exchange 2013-Zertifikaten</p></td>
<td><p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Digitale Zertifikate und SSL</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Konfigurieren von Exchange 2007-Zertifikaten</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/?linkid=320553">Verwalten von SSL für einen Clientzugriffsserver</a></p></td>
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
<td> </td>
<td><p>13. Konfigurieren von Unified Messaging</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn in der Organisation Unified Messaging verwendet werden soll.


</td>
<td><p><a href="planning-for-unified-messaging-exchange-2013-help.md">Planen von Unified Messaging</a></p>
<p><a href="deploy-exchange-2013-um-exchange-2013-help.md">Bereitstellen von Exchange 2013 UM</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>14. Aktivieren und Konfigurieren von Outlook Anywhere</p></td>
<td><p><a href="outlook-anywhere-exchange-2013-help.md">Outlook Anywhere</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Konfigurieren des Dienstverbindungspunkts</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Konfiguration des Exchange 2013-Clientzugriffsservers</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>16. Konfigurieren von Exchange 2007-URLs</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/dn282262(v=exchg.150)">Konfigurieren von externen URLs für Exchange 2007</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>17. Konfigurieren von DNS-Einträgen</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/dn283988(v=exchg.150)">Konfigurieren von DNS-Einträgen für die Mehrserverinstallation von Exchange 2007</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>18. Verschieben von Postfächern von Exchange 2007 nach Exchange 2013</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>19. Verschieben von Daten in Öffentlichen Ordnern von Exchange 2013 nach Exchange 2013</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Ihre Organisation öffentliche Ordner verwendet.


</td>
<td><p><a href="public-folders-exchange-2013-help.md">Öffentliche Ordner</a></p>
<p><a href="https://technet.microsoft.com/de-de/library/jj150486(v=exchg.150)">Verwenden der seriellen Migration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>20. Tasks nach der Installation</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Aufgaben nach der Installation von Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

