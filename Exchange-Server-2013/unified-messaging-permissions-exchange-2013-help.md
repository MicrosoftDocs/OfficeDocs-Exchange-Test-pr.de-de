---
title: 'Unified Messaging-Berechtigungen: Exchange 2013 Help'
TOCTitle: Unified Messaging-Berechtigungen
ms:assetid: d326c3bc-8f33-434a-bf02-a83cc26a5498
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638193(v=EXCHG.150)
ms:contentKeyID: 50476791
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Unified Messaging-Berechtigungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die zum Ausführen von Aufgaben auf Clientzugriffsservern, auf denen der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung ausgeführt wird, und auf Postfachservern, auf denen der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, richten sich nach dem durchzuführenden Vorgang bzw. nach dem auszuführenden Cmdlet.

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).

## UM-Komponentenberechtigungen

Sie können Einstellungen für die UM-Komponenten und -Features in der folgenden Tabelle konfigurieren.

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
<td><p>Automatische UM-Telefonzentralen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>UM-Mailboxansageregeln</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>UM-Anrufdaten und Zusammenfassungsberichte</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Clientzugriffsserver (UM-Dienst für die Anrufweiterleitung)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>UM-Wähleinstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>UM-Sammelanschlüsse</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>UM-IP-Gateways</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>UM-Postfachrichtlinien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>UM-Postfächer</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>UM-Telefonansagen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Postfachserver (UM-Dienst)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
</tbody>
</table>

