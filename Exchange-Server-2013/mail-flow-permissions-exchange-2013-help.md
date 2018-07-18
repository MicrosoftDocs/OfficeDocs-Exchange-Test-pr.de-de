---
title: 'Berechtigungen für den Nachrichtenfluss: Exchange 2013 Help'
TOCTitle: Berechtigungen für den Nachrichtenfluss
ms:assetid: f49f4fb5-af75-43cb-900f-c5f7b8cfa143
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638213(v=EXCHG.150)
ms:contentKeyID: 50477072
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen für den Nachrichtenfluss

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die erforderlichen Berechtigungen für nachrichtenflussbezogene Tasks richten sich nach dem verwendeten Verfahren bzw. nach dem Cmdlet, das Sie ausführen möchten. Weitere Informationen zu Transportfeatures finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).

In diesem Thema werden die erforderlichen Berechtigungen für die Verwaltung der Nachrichtenflussfeatures in Microsoft Exchange Server 2013 aufgeführt. Weitere Informationen dazu, in welcher Beziehung Office 365-Berechtigungen zu Exchange-Berechtigungen stehen, finden Sie unter [Berechtigungen in Office 365](https://go.microsoft.com/fwlink/p/?linkid=335814).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).


> [!NOTE]
> Funktionen, die Sie verwalten möchten, können sich auch auf Edge-Transport-Servern befinden. Zum Verwalten von Funktionen auf Edge-Transport-Servern müssen Sie Mitglied der lokalen Administratorengruppe auf dem Edge-Transport-Server werden, den Sie verwalten möchten. Edge-Transport-Server verwenden keine rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC). Bei Funktionen, die auf Edge-Transport-Servern verwaltet werden können, ist in der Spalte "Erforderliche Berechtigungen" in der Tabelle unten "Lokaler Edge-Transport-Administrator" angegeben.




> [!NOTE]
> Einige Funktionen erfordern u.&nbsp;U. lokale Administratorrechte für den Server, den Sie verwalten möchten. Um diese Funktionen zu verwalten, müssen Sie Mitglied der lokalen Administratorengruppe auf dem Server sein.



## Berechtigungen für den Nachrichtenfluss

Mit den Features in den folgenden Tabellen konfigurieren Sie Nachrichtenflusseinstellungen im Front-End-Transport-Dienst auf Clientzugriffsservern, im Transportdienst auf Postfachservern, im Postfachtransportdienst auf Postfachservern und auf Edge-Transport-Servern. Die Berechtigungen, die zum Konfigurieren der einzelnen Features erforderlich sind, werden aufgeführt.

Benutzern, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Features in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter [Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).

**Postfachserver und Clientzugriffsserver**


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
<td><p>Akzeptierte Domänen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung von Active Directory-Standorten und Standortverknüpfungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Antispamfeatures</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="even">
<td><p>Antispamupdates</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="odd">
<td><p>Zertifikatverwaltung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Zustellungs-Agent-Connectors</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>DSNs</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>EdgeSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Fremde Connectors</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Front-End-Transportdienst</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="odd">
<td><p>Journaling</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Postfachzugriff</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Junk-E-Mail-Konfiguration für Postfächer</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="help-desk-exchange-2013-help.md">Helpdesk</a></p></td>
</tr>
<tr class="even">
<td><p>Postfachtransportdienst</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="odd">
<td><p>E-Mail-Infos</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenklassifizierungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Nachrichtenverfolgung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Moderierter Transport</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Warteschlangen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Empfangsconnectors</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="odd">
<td><p>Remotedomänen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Aggregation von Listen sicherer Adressen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Sendeconnectors</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Shadow-Redundanz</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Testen des Nachrichtenflusses</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Testen der Verarbeitung von Transportregeln</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Transport-Agents</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Transportkonfiguration</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Transportprotokolle</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Transportregeln</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Transportdienst</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="even">
<td><p>X.400-Domänen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


**Edge-Transport-Server**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Akzeptierte Domänen - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="even">
<td><p>Erneutes Schreiben von Adressen – Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="odd">
<td><p>Edge-Transport-Server</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="even">
<td><p>EdgeSync - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="odd">
<td><p>Warteschlangen - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="even">
<td><p>Empfangsconnectors - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="odd">
<td><p>Sendeconnectors - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="even">
<td><p>Transportkonfiguration - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="odd">
<td><p>Transportprotokolle - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
<tr class="even">
<td><p>Transportregeln - Edge-Transport</p></td>
<td><p>Edge-Transport - lokaler Administrator</p></td>
</tr>
</tbody>
</table>

