---
title: 'Berechtig. für Messagingrichtlinien und -kompatibilität: Exchange 2013-Hilfe'
TOCTitle: Berechtigungen für Messagingrichtlinien und -kompatibilität
ms:assetid: ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638205(v=EXCHG.150)
ms:contentKeyID: 50476998
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen für Messagingrichtlinien und -kompatibilität

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die zum Konfigurieren von Messagingrichtlinien und deren Einhaltung erforderlichen Berechtigungen richten sich nach dem verwendeten Verfahren bzw. nach dem Cmdlet, das Sie ausführen möchten. Weitere Informationen zu Messagingrichtlinien und deren Einhaltung finden Sie unter [Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).


> [!NOTE]
> Funktionen, die Sie verwalten möchten, können sich auch auf Edge-Transport-Servern befinden. Zum Verwalten von Funktionen auf Edge-Transport-Servern müssen Sie Mitglied der lokalen Administratorengruppe auf dem Edge-Transport-Server werden, den Sie verwalten möchten. Edge-Transport-Server verwenden keine rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC). Bei Funktionen, die auf Edge-Transport-Servern verwaltet werden können, ist in der Spalte "Erforderliche Berechtigungen" in der Tabelle unten "Lokaler Edge-Transport-Administrator" angegeben.



## Berechtigungen für Messagingrichtlinien und -kompatibilität

Mithilfe der Features in der folgenden Tabelle können Sie Features für Messagingrichtlinien und deren Einhaltung konfigurieren. Die Rollengruppen, die zum Konfigurieren der einzelnen Features erforderlich sind, werden aufgeführt.

Benutzern, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Features in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter [Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verhinderung von Datenverlusten (Data Loss Prevention, DLP)</p></td>
<td><p>Bei Verwendung von Office 365:</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Office 365 Globaler Administrator</a>, was Exchange <a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a> automatisch ausschließt</p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Office 365-Dienst-Administrator</a>, plus der <a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a> Adminisratorrollengruppe in Exchange</p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Office 365-Kennwortadministrator</a></p></li>
</ul>
<p>Nur bei Verwendung von Exchange Server 2013 oder Exchange Online:</p>
<ul>
<li><p><a href="compliance-management-exchange-2013-help.md">Verwaltung der Richtlinientreue</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Löschen von Postfachinhalt (unter Verwendung des Cmdlets <a href="https://technet.microsoft.com/de-de/library/dd298173(v=exchg.150)">Search-Mailbox</a> mit der Option <em>DeleteContent</em>)</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a> <strong>und</strong></p>
<p><a href="mailbox-import-export-role-exchange-2013-help.md">Rolle „Postfachimport/-export“</a></p>

> [!NOTE]
> Die Rolle für den Postfachimport/-export ist standardmäßig keiner Rollengruppe zugewiesen. Sie können einer integrierten oder benutzerdefinierten Rollengruppe, einem Benutzer oder einer universellen Sicherheitsgruppe eine Verwaltungsrolle zuweisen. Es wird empfohlen, eine Rolle zu einer Rollengruppe zuzuweisen. Weitere Informationen finden Sie unter <A href="add-a-role-to-a-user-or-usg-exchange-2013-help.md">Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe</A>.


</td>
</tr>
<tr class="odd">
<td><p>Discoverypostfächer – Erstellen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Journaling</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Postfachüberwachungsprotokollierung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenklassifizierungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Messaging-Datensatzverwaltung</p></td>
<td><p><a href="compliance-management-exchange-2013-help.md">Verwaltung der Richtlinientreue</a></p>
<p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Compliance-eDiscovery</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a></p>

> [!NOTE]
> Standardmäßig weist die Rollengruppe für die Discoveryverwaltung keine Mitglieder auf. Kein Benutzer (einschließlich Administratoren) verfügt über die erforderlichen Berechtigungen zum Durchsuchen von Postfächern. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/assign-ediscovery-permissions">Zuweisen von eDiscovery-Berechtigungen in Exchange</A>.


</td>
</tr>
<tr class="odd">
<td><p>Compliance-Archiv</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a></p>
<p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>

> [!IMPORTANT]
> Ein Benutzer benötigt zum Erstellen eines abfragebasierten Compliance-Archivs die Rollen "Postfachsuche" und "Beweissicherungsverfahren", die direkt oder über eine Mitgliedschaft in einer Rollengruppe, der beide Rollen zugewiesen sind, zugewiesen werden. Damit Sie ein Compliance-Archiv, bei dem das Beweissicherungsverfahren für alle Postfachelemente aktiviert wird, ohne Verwendung einer Abfrage erstellen können, muss Ihnen die Rolle "Beweissicherungsverfahren" zugewiesen sein. Der Rollengruppe "Discoveryverwaltung" werden beide Rollen zugewiesen.<BR>Der Rollengruppe "Organisationsverwaltung" wird die Rolle "Beweissicherungsverfahren" zugewiesen. Mitglieder der Rollengruppe "Organisationsverwaltung" können ein Compliance-Archiv für alle Elemente in einem Postfach aktivieren, jedoch kein abfragebasiertes Compliance-Archiv erstellen.


</td>
</tr>
<tr class="even">
<td><p>Compliance-Archiv</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Compliance-Archiv – Testverbindungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Konfiguration der Verwaltung von Informationsrechten (Information Rights Management, IRM)</p></td>
<td><p><a href="compliance-management-exchange-2013-help.md">Verwaltung der Richtlinientreue</a></p>
<p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Aufbewahrungsrichtlinien – Anwenden</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Aufbewahrungsrichtlinien – Erstellen</p></td>
<td><p>Siehe Eintrag zur Verwaltung von Nachrichtendatensätzen</p></td>
</tr>
<tr class="odd">
<td><p>Transportregeln</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
</tbody>
</table>

