---
title: 'Aktualisieren von Exchange 2010 auf Exchange 2013: Exchange 2013 Help'
TOCTitle: Aktualisieren von Exchange 2010 auf Exchange 2013
ms:assetid: c0558850-d583-4c4e-a9a0-0d3593f84fcc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898583(v=EXCHG.150)
ms:contentKeyID: 51409338
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren von Exchange 2010 auf Exchange 2013

 

_**Gilt für:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Microsoft Exchange Server 2010 und Exchange Server 2007 haben zahlreiche Serverrollen: Clientzugriff, Postfach, Hub-Transport, Unified Messaging und Edge-Transport. Bei Exchange Server 2013 wurde die Anzahl der Serverrollen von fünf auf drei reduziert: Clientzugriff, Postfach und Edge-Transport. Unified Messaging wird nun als Komponente oder Teilfunktion der sprachbezogenen Funktionen betrachtet, die in Exchange 2013 verfügbar sind. (Weitere Details zu den Änderungen finden Sie unter "Exchange 2013-Architektur" in [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).)

Beim Upgrade einer vorhandenen Exchange 2010-Organisation auf Exchange 2013 sind für einen bestimmten Zeitraum sowohl Server mit Exchange 2010 als auch Exchange 2013 in Ihrer Organisation vorhanden. Sie können entweder diesen Modus für unbegrenzte Zeit beibehalten oder das Upgrade auf Exchange 2013 sofort abschließen, indem Sie alle Ressourcen von Exchange 2010 nach Exchange 2013 verschieben und die Exchange 2010-Server anschließend außer Betrieb nehmen. Wenn folgende Bedingungen erfüllt sind, liegt ein Koexistenzszenario vor:

  - Exchange 2013 wird in einer bestehenden Exchange-Organisation bereitgestellt.

  - Mehrere Microsoft Exchange-Versionen stellen Messagingdienste für die Organisation bereit.

Es ist nicht möglich, eine vorhandene Exchange 2003-Organisation direkt auf Exchange 2013 zu aktualisieren. Sie müssen zuerst Ihre Exchange 2003-Organisation auf eine Exchange 2007- oder Exchange 2010-Organisation aktualisieren. Erst dann können Sie die Exchange 2007- oder Exchange 2010-Organisation auf Exchange 2013 aktualisieren. Es empfiehlt sich, Ihre Organisation von Exchange 2003 auf Exchange 2010 zu aktualisieren und dann ein Upgrade von Exchange 2010 auf Exchange 2013 auszuführen.


> [!WARNING]
> Bevor Sie das Upgrade auf Exchange 2013 ausführen können, müssen Sie alle Instanzen von Exchange 2003 aus Ihrer Organisation entfernen.



Sie können alle Ihre Exchange 2003-Postfächer zu Exchange Online migrieren. Weitere Informationen zu diesem Ansatz finden Sie unter [Methoden zum Migrieren mehrerer E-Mail-Konten zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=524030).

In der folgenden Tabelle sind die Szenarien aufgelistet, in denen eine Koexistenz von Exchange 2013 und früheren Exchange-Versionen unterstützt wird.

### Koexistenz von Exchange 2013 und früheren Versionen von Exchange Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange-Version</th>
<th>Koexistenz von Exchange-Organisationen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Server 2003 und frühere Versionen</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2007</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>1Updaterollup 10 für Exchange 2007 Service Pack 3 (SP3) auf allen Exchange 2007-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 Kumulatives Update 2 (CU2) oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange 2010</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>2 Exchange 2010 SP3 auf allen Exchange 2010-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 CU2 oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Organisation mit gemischten Exchange 2010- und Exchange 2007-Umgebungen</p></td>
<td><p>Unterstützt mit den folgenden Mindestversionen von Exchange:</p>
<ul>
<li><p>1Updaterollup 10 für Exchange 2007 SP3 auf allen Exchange 2007-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>2 Exchange 2010 SP3 auf allen Exchange 2010-Servern in der Organisation, einschließlich Edge-Transport-Servern.</p></li>
<li><p>Exchange 2013 CU2 oder höher auf allen Exchange 2013-Servern in der Organisation.</p></li>
</ul></td>
</tr>
</tbody>
</table>


1   Wenn Sie ein EdgeSync-Abonnement zwischen einem Exchange 2007 Hub-Transport-Server und einem Exchange 2013 SP1 Edge-Transport-Server erstellen möchten, müssen Sie Exchange 2007 SP3 Updaterollup 13 oder höher auf dem Exchange 2007 Hub-Transport-Server installieren.

2   Wenn Sie ein EdgeSync-Abonnement zwischen einem Exchange 2010 Hub-Transport-Server und einem Exchange 2013 SP1 Edge-Transport-Server erstellen möchten, müssen Sie Exchange 2010 SP3 Updaterollup 5 oder höher auf dem Exchange 2010 Hub-Transport-Server installieren.

## Gemischter Modus: Koexistenz von Exchange 2013 und Exchange 2007 mit Exchange 2010

Wenn Sie über Active Directory-Standorte verfügen, in denen sowohl Exchange 2010 als auch Exchange 2007 installiert ist, folgen Sie den Upgradeanweisungen für Exchange 2010 und Exchange 2007, und führen Sie die für beide Versionen erforderlichen Upgradeschritte aus.

## Übersicht über den Upgradevorgang

Damit Sie sich einen Überblick über das Upgrade von Exchange 2010 auf Exchange 2013 verschaffen können, haben wir in der folgenden Tabelle Ressourcen zu den jeweiligen Hauptaufgaben zusammengestellt. Schrittweise Anweisungen finden Sie unter [Prüfliste: Upgrade von Exchange 2010](checklist-upgrade-from-exchange-2010-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Task</th>
<th>Thema</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Erfahren Sie mehr über Exchange 2013-Rollen und -Komponenten</p></td>
<td><p><a href="what-s-new-in-exchange-2013-exchange-2013-help.md">Neuerungen in Exchange 2013</a></p>
<p><a href="client-access-server-exchange-2013-help.md">Clientzugriffsserver</a></p>
<p><a href="mailbox-server-exchange-2013-help.md">Postfachserver</a></p>
<p><a href="mail-flow-exchange-2013-help.md">Nachrichtenübermittlung</a></p>
<p><a href="unified-messaging-exchange-2013-help.md">Unified Messaging</a></p></td>
</tr>
<tr class="even">
<td><p>Installieren von Exchange 2013</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Installieren von Exchange 2013 mithilfe des Setup-Assistenten</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten</a> (optional)</p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Überprüfen einer Exchange 2013-Installation</a></p></td>
</tr>
<tr class="odd">
<td><p>Hinzufügen digitaler Zertifikate auf dem Clientzugriffsserver</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Konfiguration des Exchange 2013-Clientzugriffsservers</a></p>
<p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Digitale Zertifikate und SSL</a></p>
<p><a href="create-a-digital-certificate-request-exchange-2013-help.md">Erstellen einer Anforderung für ein digitales Zertifikat</a></p></td>
</tr>
<tr class="even">
<td><p>Konfigurieren der Exchange-bezogenen virtuellen Verzeichnisse</p></td>
<td><p><a href="default-settings-for-exchange-virtual-directories-exchange-2013-help.md">Standardeinstellungen für virtuelle Exchange-Verzeichnisse</a></p></td>
</tr>
<tr class="odd">
<td><p>Verschieben von Postfächern von Exchange 2010</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Konfigurieren von Transportkomponenten</p></td>
<td><p><a href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</a> (nur erforderlich, wenn ein Edge-Transport-Server installiert ist)</p>
<p><a href="mail-routing-exchange-2013-help.md">E-Mail-Routing</a></p>
<p><a href="shadow-redundancy-exchange-2013-help.md">Shadow-Redundanz</a></p>
<p><a href="delivery-reports-for-administrators-exchange-2013-help.md">Übermittlungsberichte für Administratoren</a></p></td>
</tr>
<tr class="odd">
<td><p>Konfigurieren und Bereitstellen von UM</p></td>
<td><p><a href="planning-for-unified-messaging-exchange-2013-help.md">Planen von Unified Messaging</a></p>
<p><a href="deploying-voice-mail-and-um-exchange-2013-help.md">Bereitstellen von Voicemail und UM</a></p></td>
</tr>
</tbody>
</table>

