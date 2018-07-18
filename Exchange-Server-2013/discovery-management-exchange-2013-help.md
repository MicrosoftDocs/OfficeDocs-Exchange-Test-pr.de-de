---
title: 'Erkennungsverwaltung: Exchange 2013 Help'
TOCTitle: Erkennungsverwaltung
ms:assetid: b8bc5922-a8c9-4707-906d-fa38bb87da8f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351080(v=EXCHG.150)
ms:contentKeyID: 50476554
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erkennungsverwaltung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Discoveryverwaltung Die Verwaltungsrollengruppe ist eine von mehreren integrierten Rollengruppen, aus denen das Modell der rollenbasierten Zugriffssteuerungsberechtigungen (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013 besteht. Rollengruppen wird mindestens eine Verwaltungsrolle zugewiesen, welche die zum Ausführen bestimmter Aufgaben erforderlichen Berechtigungen enthält. Den Mitgliedern einer Rollengruppe wird der Zugriff auf die Verwaltungsrollen erteilt, die der Rollengruppe zugewiesen sind. Weitere Informationen zu Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Administratoren oder Benutzer, die Mitglied der Rollengruppe Discoveryverwaltung sind, können Postfächer in der Exchange-Organisation nach Daten durchsuchen, die bestimmte Kriterien erfüllen, und außerdem Beweissicherungsverfahren für Postfächer konfigurieren. Weitere Informationen finden Sie unter [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md).


> [!IMPORTANT]
> Die Rollengruppe Organisationsverwaltung aktiviert nicht standardmäßig die Discoverysuchfunktion für Benutzer oder universelle Sicherheitsgruppen, die Mitglieder dieser Rollengruppe sind. Mitglieder der Rollengruppe Organisationsverwaltung müssen entweder als Mitglieder dieser Rollengruppe hinzugefügt werden, oder die später in diesem Thema aufgeführte Rolle für die Postfachsuche muss der Rollengruppe Organisationsverwaltung&nbsp;manuell zugewiesen werden. Informationen zum Zuweisen einer Rolle zu einer Rollengruppe finden Sie unter <A href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</A>.



Weitere Informationen zu RBAC finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Rollengruppenmitgliedschaft

Informationen dazu, wie Sie Mitglieder zu dieser Rollengruppe hinzufügen oder daraus entfernen, finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Standardmäßig können nur Mitglieder der Rollengruppe "Organisationsverwaltung" Mitglieder zu dieser Rollengruppe hinzufügen oder daraus entfernen. Weitere Informationen zum Hinzufügen zusätzlicher Rollengruppenstellvertreter finden Sie im Abschnitt "Hinzufügen oder Entfernen eines Rollengruppenstellvertreters" unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Sie können den folgenden Befehl verwenden, um eine Liste der Benutzer oder universellen Sicherheitsgruppen anzuzeigen, die Mitglieder dieser Rollengruppe sind.

    Get-RoleGroupMember "Discovery Management"

Weitere Informationen über die Mitglieder einer Rollengruppe finden Sie unter [View the members of a role group](manage-role-group-members-exchange-2013-help.md) in [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

## Rollengruppenanpassung

Dieser Rollengruppe werden standardmäßig Verwaltungsrollen zugewiesen. Die betreffenden Rollen sind im Abschnitt "Dieser Rollengruppe zugewiesene Verwaltungsrollen" aufgeführt. Sie können dieser Rollengruppe je nach den Anforderungen Ihrer Organisation Rollenzuweisungen hinzufügen oder diese aus der Rollengruppe entfernen.

Die mit Exchange 2013 bereitgestellten Rollengruppen wurden entwickelt, um abgestuften Aufgaben gerecht zu werden. Durch das Zuweisen von Rollen zu einer Rollengruppe ermöglichen Sie den Mitgliedern dieser Rollengruppe das Ausführen der zu dieser Rolle gehörenden Aufgaben. So ermöglicht beispielsweise die Rolle "Journale" das Verwalten von Journal-Agent und Journalregeln. Weitere Informationen über das Zuweisen von Rollen zu Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Die dieser Rollengruppe zugewiesenen Rollen erhalten Standardverwaltungsbereiche. Verwaltungsbereiche bestimmen, welche Exchange-Objekte durch die Mitglieder einer Rollengruppe angezeigt oder geändert werden können. Sie können die Bereiche, die Zuweisungen zwischen Rollen und Rollengruppen zugeordnet sind, ändern. Dies können Sie beispielsweise tun, wenn Sie möchten, dass Mitglieder einer Rollengruppe nur Empfänger ändern können, die einer bestimmten Organisationseinheit angehören oder sich an einem bestimmten Standort befinden. Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Weitere Informationen zum Anpassen dieser Rollengruppe finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md)

Wenn Sie eine neue Rollengruppe erstellen möchten und einige der dieser Rollengruppe zugeordneten Rollen zuweisen möchten, finden Sie weitere Informationen im Abschnitt "Erstellen einer Rollengruppe" unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

## Dieser Rollengruppe zugewiesene Verwaltungsrollen

In der folgenden Tabelle sind alle Verwaltungsrollen aufgeführt, die dieser Rollengruppe zugewiesen sind, sowie die folgenden Attribute der einzelnen Rollenzuweisungen:

  - **Reguläre Zuweisung**   Ermöglicht Mitgliedern der Rollengruppe den Zugriff auf die Verwaltungsrolleneinträge, die von der zugehörigen Verwaltungsrolle bereitgestellt werden.

  - **Delegierende Zuweisung**   Gibt Mitgliedern der Rollengruppe die Möglichkeit, die jeweilige Rolle anderen Rollengruppen, Rollenzuweisungsrichtlinien, Benutzern oder universellen Sicherheitsgruppen zuzuweisen.

  - **Empfängerlesebereich**   Bestimmt, welche Empfängerobjekte Mitglieder der Rollengruppe aus Active Directory lesen können.

  - **Empfängerschreibbereich**   Bestimmt, welche Empfängerobjekte Mitglieder der Rollengruppe in Active Directory ändern können.

  - **Konfigurationslesebereich**   Bestimmt, welche Konfigurations- und Serverobjekte Mitglieder der Rollengruppe aus Active Directory lesen können.

  - **Konfigurationsschreibbereich**   Bestimmt, welche Organisations- und Serverobjekte Mitglieder der Rollengruppe in Active Directory ändern können.

Weitere Informationen zu Rollenzuweisungen und Verwaltungsbereichen finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

### Dieser Rollengruppe zugewiesene Verwaltungsrollen

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrolle</th>
<th>Reguläre Zuweisung</th>
<th>Delegierende Zuweisung</th>
<th>Empfängerlesebereich</th>
<th>Empfängerschreibbereich</th>
<th>Konfigurationslesebereich</th>
<th>Konfigurationsschreibbereich</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="legal-hold-role-exchange-2013-help.md">Rolle „Gesetzliche Aufbewahrungspflicht“</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mailbox-search-role-exchange-2013-help.md">Rolle „Postfachsuche“</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
</tbody>
</table>

