---
title: 'Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten: Exchange 2013 Help'
TOCTitle: Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten
ms:assetid: 66085107-4d4d-41c3-a425-82314acd9eee
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638136(v=EXCHG.150)
ms:contentKeyID: 50475845
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-11-12_

Die zum Konfigurieren von hoher Verfügbarkeit erforderlichen Berechtigungen richten sich nach dem verwendeten Verfahren bzw. nach dem Cmdlet, das Sie ausführen möchten. Weitere Informationen zu hoher Verfügbarkeit finden Sie unter [Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).

## Database Availability Group-Berechtigungen

Sie können die in der nachstehenden Tabelle aufgeführten Funktionen zum Hinzufügen, Entfernen und Konfigurieren von Einstellungen für DAGs verwenden.

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
<td><p>Mitgliedschaft in DAGs</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
</tr>
<tr class="even">
<td><p>Eigenschaften einer DAG</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
</tr>
<tr class="odd">
<td><p>Database Availability Groups (DAGs)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
</tr>
<tr class="even">
<td><p>Netzwerke für DAGs</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
</tr>
</tbody>
</table>


## Postfachdatenbankkopie-Berechtigungen

Sie können die in der nachstehenden Tabelle aufgeführten Features zum Hinzufügen, Entfernen, Aktualisieren und Aktivieren von Postfachdatenbankkopien verwenden.


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
<td><p>Datenbankwechsel</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="databases-role-exchange-2013-help.md">Rolle „Datenbanken“</a></p></td>
</tr>
<tr class="even">
<td><p>Postfachdatenbankkopien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-copies-role-exchange-2013-help.md">Rolle „Datenbankkopien“</a></p></td>
</tr>
<tr class="odd">
<td><p>Server-Switchover</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="databases-role-exchange-2013-help.md">Rolle „Datenbanken“</a></p></td>
</tr>
<tr class="even">
<td><p>Aktualisieren einer Postfachdatenbankkopie</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="database-copies-role-exchange-2013-help.md">Rolle „Datenbankkopien“</a></p></td>
</tr>
</tbody>
</table>

