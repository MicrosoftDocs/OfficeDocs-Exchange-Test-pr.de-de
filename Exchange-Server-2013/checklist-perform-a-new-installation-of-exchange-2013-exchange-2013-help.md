---
title: 'Prüfliste: Ausführen einer Neuinstallation von Exchange 2013: Exchange 2013 Help'
TOCTitle: 'Prüfliste: Ausführen einer Neuinstallation von Exchange 2013'
ms:assetid: f70d9dd3-7370-472e-b05e-1ea1671272b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff805042(v=EXCHG.150)
ms:contentKeyID: 50477089
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste: Ausführen einer Neuinstallation von Exchange 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Verwenden Sie diese Prüfliste für die Bereitstellung von Microsoft Exchange Server 2013. Machen Sie sich mit den Konzepten in folgenden Themen vertraut, bevor Sie diese Prüfliste durchgehen:

  - [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md)

  - [Prüfliste für Bereitstellungssicherheit](deployment-security-checklist-exchange-2013-help.md)

Diese Prüfliste ist dahingehend allgemein, dass sie Anleitungen für ein herkömmliches Szenario enthält.


> [!NOTE]
> Der Exchange Server Bereitstellungs-Assistent bietet eine schrittweise Anleitung für die Bereitstellung von Exchange Server. Der Bereitstellungs-Assistent kann Sie bei Bereitstellung einer Neuinstallation von Exchange Server&nbsp;2013, dem Upgrade einer früheren Version auf Exchange&nbsp;2013 oder der Konfiguration einer Hybridbereitstellung von Exchange&nbsp;2013 und Exchange Online unterstützen. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.



## Prüfliste für eine Neuinstallation von Exchange 2013


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Erledigt?</p></td>
<td><p>Task</p></td>
<td><p>Thema</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1. Lesen Sie die Anmerkungen zu dieser Version.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Versionshinweise zu Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>2. Überprüfen Sie die Systemanforderungen.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>3. Bestätigen Sie, dass die erforderlichen Schritte ausgeführt wurden.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>4. Konfigurieren Sie nicht zusammenhängende Namespaces.</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Ihre Organisation einen nicht zusammenhängenden Namespace verwendet.


</td>
<td><p><a href="disjoint-namespace-scenarios-exchange-2013-help.md">Szenarien mit nicht zusammenhängenden Namespaces</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>5. Installieren Sie die Postfachserverrolle.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>6. Installieren Sie die Clientzugriffs-Serverrolle.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>7. Installieren Sie die Serverrolle Edge-Transport.</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Sie den Edge-Transport-Server installieren möchten. Weitere Informationen finden Sie unter <A href="edge-transport-servers-exchange-2013-help.md">Edge-Transport-Server</A>.


</td>
<td><p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Erstellen eines EdgeSync-Abonnements</p>
<p>Dieser Schritt ist optional. Er ist nur erforderlich, wenn Sie einen Edge-Transport-Server installiert haben und das EdgeSync-Abonnement zwischen Ihrem Edge-Transport-Server und einem Hub-Transport-Server konfigurieren möchten. Weitere Informationen finden Sie unter <a href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</a>.</p></td>
<td><p><a href="configure-internet-mail-flow-through-a-subscribed-edge-transport-server-exchange-2013-help.md">Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Konfigurieren Sie den Transport.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 1: Create a Send connector</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>10. Fügen Sie weitere akzeptierte Domänen hinzu.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 2: Add additional accepted domains</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Konfigurieren Sie E-Mail-Adressrichtlinien.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 3: Configure the default email address policy</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>12. Konfigurieren Sie die Einstellungen für virtuelle Verzeichnisse, einschließlich Offlineadressbuch, Exchange-Webdienste, Exchange-Verwaltungskonsole, Outlook Web App und virtuelle Exchange ActiveSync-Verzeichnisse.</p>

> [!NOTE]
> Dieser Schritt ist erforderlich, wenn Sie Exchange-Webdienste, Outlook Anywhere oder das Offlineadressbuch verwenden möchten. Er kann auch erforderlich sein, wenn Sie Standardeinstellungen der Exchange-Verwaltungskonsole, von Outlook Web App oder Exchange ActiveSync ändern müssen.


</td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 4: Configure external URLs</a></p>
<p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 5: Configure internal URLs</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>13. Fügen Sie digitale Zertifikate auf dem Clientzugriffsserver hinzu.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 6: Configure an SSL certificate</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>14. Konfigurieren Sie Unified Messaging.</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn in der Organisation Unified Messaging verwendet werden soll.


</td>
<td><p><a href="deploying-voice-mail-and-um-exchange-2013-help.md">Bereitstellen von Voicemail und UM</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Konfigurieren Sie weitere Unified Messaging- und Lync Server-Einstellungen.</p>

> [!NOTE]
> Dieser Schritt ist optional. Er ist nur erforderlich, wenn Sie Unified Messaging in Ihrer Organisation konfiguriert haben und es mit Lync Server integrieren möchten.


</td>
<td><p><a href="deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md">Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>16. Tasks nach der Installation.</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Aufgaben nach der Installation von Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

