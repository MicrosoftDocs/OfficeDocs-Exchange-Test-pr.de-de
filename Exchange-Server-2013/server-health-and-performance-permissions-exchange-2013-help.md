---
title: 'Berechtigungen für Serverstatus und Leistung: Exchange 2013 Help'
TOCTitle: Berechtigungen für Serverstatus und Leistung
ms:assetid: 00b23fd3-6679-4b06-a3d4-51df3112b9cd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150479(v=EXCHG.150)
ms:contentKeyID: 50474931
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Berechtigungen für Serverstatus und Leistung

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

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



## Exchange-Berechtigungen für die Verwaltung der Arbeitsauslastung

In der folgenden Tabelle sind die erforderlichen Berechtigungen aufgeführt, um Aufgaben zur Verwaltung der Integrität und Leistung Ihrer Exchange 2013-Organisation auszuführen. Weitere Informationen finden Sie unter [Verwaltung von Exchange-Arbeitsauslastungen](exchange-workload-management-exchange-2013-help.md).

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
<td><p>Benutzereinschränkung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="even">
<td><p>Einschränkung der Exchange-Arbeitsauslastung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
</tbody>
</table>


## Exchange-Ereignisprotokollberechtigungen

In der folgenden Tabelle sind die erforderlichen Berechtigungen aufgeführt, um Aufgaben zum Verwalten der Exchange-Ereignisprotokolleinstellungen auszuführen.

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
<td><p>Exchange-Ereignisprotokollverwaltung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
</tbody>
</table>

