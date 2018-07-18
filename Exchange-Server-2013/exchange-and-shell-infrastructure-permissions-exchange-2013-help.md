---
title: 'Exchange- und Shellinfrastrukturberechtigungen: Exchange 2013 Help'
TOCTitle: Exchange- und Shellinfrastrukturberechtigungen
ms:assetid: 3646a4e8-36b2-41fb-89a4-79b0963fcb11
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638114(v=EXCHG.150)
ms:contentKeyID: 50475461
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange- und Shellinfrastrukturberechtigungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Berechtigungen, die zum Durchführen von Aufgaben zum Konfigurieren diverser Komponenten von Microsoft Exchange Server 2013 erforderlich sind, hängen von dem zu verwendenden Verfahren oder dem auszuführenden Cmdlet ab. Die einzelnen Abschnitte in diesem Thema enthalten weitere Informationen zu den entsprechenden Funktionen.

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).


> [!NOTE]
> Einige Funktionen erfordern u.&nbsp;U. lokale Administratorrechte für den Server, den Sie verwalten möchten. Um diese Funktionen zu verwalten, müssen Sie Mitglied der lokalen Administratorengruppe auf dem Server sein.



## Exchange-Infrastrukturberechtigungen

Die folgende Tabelle enthält die erforderlichen Berechtigungen für Aufgaben, bei denen allgemeine Exchange 2013-Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


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
<td><p>Administratorüberwachungsprotokollierung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Konfigurationseinstellungen für die Exchange-Verwaltungskonsole</p></td>
<td><p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="odd">
<td><p>Konnektivität der Exchange-Verwaltungskonsole</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Konfigurationseinstellungen von Exchange-Servern</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Hilfeeinstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenkategorien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="help-desk-exchange-2013-help.md">Helpdesk</a></p></td>
</tr>
<tr class="odd">
<td><p>Produktschlüssel</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Testen der Systemdiagnose</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Überwachungsprotokollierung für Administratoren mit Leserechten</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p>

> [!NOTE]
> Sie können die Verwaltungsrolle mit Leserechten für Überwachungsprotokolle auch manuell einer Verwaltungsrollengruppe zuordnen. Weitere Informationen finden Sie unter <A href="view-only-audit-logs-role-exchange-2013-help.md">Rolle „Überwachungsprotokolle nur anzeigen“</A>.


</td>
</tr>
<tr class="even">
<td><p>Schreiben in Überwachungsprotokolle</p></td>
<td><p>Benutzer, die Mitglieder einer beliebigen Rollengruppe sind oder denen eine beliebige Verwaltungsrolle zugeordnet ist, können in das Administratorüberwachungsprotokoll schreiben.</p></td>
</tr>
</tbody>
</table>


## Shell-Infrastrukturberechtigungen

Die folgende Tabelle enthält die erforderlichen Berechtigungen für Aufgaben, bei denen Funktionen konfiguriert werden, mit denen die Ausführung der Exchange-Verwaltungsshell gesteuert wird.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


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
<td><p>Active Directory-Servereinstellungen für Domänendienste</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Cmdlet-Erweiterungs-Agents</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Virtuelle PowerShell-Verzeichnisse</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>PowerShell- und WinRM-Installation</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="odd">
<td><p>Remoteshell</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


## Verbund- und Zertifikatberechtigungen

In der folgenden Tabelle werden die Berechtigungen aufgeführt, die für Aufgaben in Bezug auf Verbundvertrauensstellungen, OAuth-Konfiguration, die Verwaltung von Zertifikaten und die Konfiguration von Hybridbereitstellungen benötigt werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


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
<td><p>Zertifikatverwaltung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Verbundvertrauensstellungen, OAuth</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Testen der Verbundvertrauensstellungen, OAuth</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Konfiguration von Hybridbereitstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsinterne Connectors</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
</tr>
</tbody>
</table>

