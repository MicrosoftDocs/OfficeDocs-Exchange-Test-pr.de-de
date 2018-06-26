---
title: 'Freigabe- und Zusammenarbeitsberechtigungen: Exchange 2013 Help'
TOCTitle: Freigabe- und Zusammenarbeitsberechtigungen
ms:assetid: b7fa4b7c-1266-45bd-a14b-f66be0459cc5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150556(v=EXCHG.150)
ms:contentKeyID: 50476528
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Freigabe- und Zusammenarbeitsberechtigungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die zum Konfigurieren von Freigabe- und Zusammenarbeitsfeatures erforderlichen Berechtigungen richten sich nach dem verwendeten Verfahren bzw. nach dem Cmdlet, das Sie ausführen möchten. Weitere Informationen zu Freigabe und Zusammenarbeit finden Sie unter [Zusammenarbeit](collaboration-exchange-2013-help.md) und [Freigabe](sharing-exchange-2013-help.md).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).

## Berechtigungen für Freigabe- und Zusammenarbeitsfeatures

Mithilfe der Features, die in der folgenden Tabelle aufgeführt sind, können Sie Freigabe- und Zusammenarbeitsfeatures konfigurieren. Die Rollengruppen, die zum Konfigurieren der einzelnen Funktionen erforderlich sind, werden aufgeführt.

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
<td><p>Partneranwendungen – Konfiguration</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Öffentliche Ordner, E-Mail-aktiviert</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Öffentliche Ordner</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="public-folder-management-exchange-2013-help.md">Verwaltung Öffentlicher Ordner</a></p></td>
</tr>
<tr class="even">
<td><p>Websitepostfächer</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Bereitstellungsrichtlinie für Websitepostfächer</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
</tbody>
</table>

