---
title: 'Berechtigungen für die Rollenverwaltung: Exchange 2013 Help'
TOCTitle: Berechtigungen für die Rollenverwaltung
ms:assetid: cb9591c4-fbb3-4199-8007-6bbfdfd5a2e9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638186(v=EXCHG.150)
ms:contentKeyID: 50476737
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen für die Rollenverwaltung

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die zum Ausführen von Konfigurationsaufgaben für Verwaltungsrollen erforderlichen Berechtigungen richten sich nach dem verwendeten Verfahren bzw. nach dem Cmdlet, das Sie ausführen möchten. Weitere Informationen zu Verwaltungsrollen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).

## Berechtigungen für die Rollenverwaltung

Mithilfe der Funktionen in der folgenden Tabelle können Sie die Verwaltungsrollengruppen, Rollen, Zuweisungsrichtlinien, Zuweisungen und Bereiche verwalten, über welche die auf Administratoren und Endbenutzer anwendbaren Berechtigungen definiert werden. Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


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
<td><p>Verwaltungsrollen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Verwaltungsrollen ohne Bereichseinschränkung</p></td>
<td><p>Verwaltungsrolle <a href="unscoped-role-management-role-exchange-2013-help.md">Rolle „Rollenverwaltung ohne Bereichseinschränkung“</a></p></td>
</tr>
<tr class="odd">
<td><p>Rollengruppen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Zuweisungsrichtlinien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Rollenzuweisungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Verwaltungsbereiche</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltungsrolleneinträge</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Legacyberechtigungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Geteilte Active Directory-Berechtigungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>

> [!IMPORTANT]
> Um den Befehl <CODE>setup.exe</CODE> mit den Parametern <EM>PrepareAD</EM> und <EM>ActiveDirectorySplitPermissions</EM> auszuführen, muss das verwendete Konto Mitglied der Administratorengruppen Schema-Admins und Organisations-Admins sein.


</td>
</tr>
</tbody>
</table>

