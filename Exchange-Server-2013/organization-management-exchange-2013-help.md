---
title: 'Organisationsverwaltung: Exchange 2013 Help'
TOCTitle: Organisationsverwaltung
ms:assetid: 0bfd21c1-86ac-4369-86b7-aeba386741c8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335087(v=EXCHG.150)
ms:contentKeyID: 50475060
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Organisationsverwaltung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Organisationsverwaltung Die Verwaltungsrollengruppe ist eine von mehreren integrierten Rollengruppen, aus denen das Modell der rollenbasierten Zugriffssteuerungsberechtigungen (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013 besteht. Rollengruppen wird mindestens eine Verwaltungsrolle zugewiesen, welche die zum Ausführen bestimmter Aufgaben erforderlichen Berechtigungen enthält. Den Mitgliedern einer Rollengruppe wird der Zugriff auf die Verwaltungsrollen erteilt, die der Rollengruppe zugewiesen sind. Weitere Informationen zu Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Administratoren, die Mitglieder der Rollengruppe Organisationsverwaltung sind, verfügen über Administratorzugriff auf die gesamte Exchange 2013-Organisation und können fast jede Aufgabe für beliebige Exchange 2013-Objekte durchführen, mit einigen Ausnahmen. Mitglieder dieser Rollengruppe können Postfachsuchen und die Verwaltung von Verwaltungsrollen oberster Ebene ohne Bereichseinschränkung standardmäßig nicht durchführen. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt "Ausschließlich delegierende Rollenzuweisungen".


> [!IMPORTANT]
> Die Rollengruppe Organisationsverwaltung umfasst sehr viele Berechtigungen. Daher sollten nur Benutzer oder universelle Sicherheitsgruppen (USGs), die Administratoraufgaben auf Organisationsebene mit potenziellen Auswirkungen auf die gesamte Exchange-Organisation durchführen, Mitglieder dieser Rollengruppe sein.



Dieser Rollengruppe entspricht die Exchange-Rolle "Organisationsadministratoren" in Exchange Server 2007.

Weitere Informationen zu RBAC finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Rollengruppenmitgliedschaft

Standardmäßig wird das Konto, mit dem Exchange 2013 in der Organisation installiert wird, als Mitglied der Rollengruppe Organisationsverwaltung hinzugefügt. Mit diesem Konto können dann bei Bedarf andere Mitglieder der Gruppe hinzugefügt werden.

Informationen dazu, wie Sie Mitglieder zu dieser Rollengruppe hinzufügen oder daraus entfernen, finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Standardmäßig können nur Mitglieder der Rollengruppe "Organisationsverwaltung" Mitglieder zu dieser Rollengruppe hinzufügen oder daraus entfernen. Weitere Informationen zum Hinzufügen zusätzlicher Rollengruppenstellvertreter finden Sie im Abschnitt "Hinzufügen oder Entfernen eines Rollengruppenstellvertreters" unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Sie können den folgenden Befehl verwenden, um eine Liste der Benutzer oder universellen Sicherheitsgruppen anzuzeigen, die Mitglieder dieser Rollengruppe sind.

    Get-RoleGroupMember "Organization Management"

Weitere Informationen über die Mitglieder einer Rollengruppe finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

## Rollengruppenanpassung

Dieser Rollengruppe werden standardmäßig Verwaltungsrollen zugewiesen. Die betreffenden Rollen sind im Abschnitt "Dieser Rollengruppe zugewiesene Verwaltungsrollen" aufgeführt. Sie können dieser Rollengruppe je nach den Anforderungen Ihrer Organisation Rollenzuweisungen hinzufügen oder diese aus der Rollengruppe entfernen.

Die mit Exchange 2013 bereitgestellten Rollengruppen wurden entwickelt, um abgestuften Aufgaben gerecht zu werden. Durch das Zuweisen von Rollen zu einer Rollengruppe ermöglichen Sie den Mitgliedern dieser Rollengruppe das Ausführen der zu dieser Rolle gehörenden Aufgaben. So ermöglicht beispielsweise die Rolle "Journale" das Verwalten von Journal-Agent und Journalregeln. Weitere Informationen über das Zuweisen von Rollen zu Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Die dieser Rollengruppe zugewiesenen Rollen erhalten Standardverwaltungsbereiche. Verwaltungsbereiche bestimmen, welche Exchange-Objekte durch die Mitglieder einer Rollengruppe angezeigt oder geändert werden können. Sie können die Bereiche, die Zuweisungen zwischen Rollen und Rollengruppen zugeordnet sind, ändern. Dies können Sie beispielsweise tun, wenn Sie möchten, dass Mitglieder einer Rollengruppe nur Empfänger ändern können, die einer bestimmten Organisationseinheit angehören oder sich an einem bestimmten Standort befinden. Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Weitere Informationen zum Anpassen dieser Rollengruppe finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md)

Wenn Sie eine neue Rollengruppe erstellen möchten und einige der dieser Rollengruppe zugeordneten Rollen zuweisen möchten, finden Sie weitere Informationen im Abschnitt "Erstellen einer Rollengruppe" unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Es folgen einige Möglichkeiten, diese Rolle anzupassen:

  - **Besitzer von Berechtigungen**   Wenn die Berechtigungen in Ihrer Organiszation von einer bestimmten Gruppe außer den Exchange-Administratoren gesteuert werden, können Sie eine Rollengruppe erstellen und die regulären und delegierenden Rollenzuweisungen für die Rolle "Rollenzuweisung" der neuen Rollengruppe zuweisen. So wird verhindert, dass Mitglieder der Rollengruppe Organisationsverwaltung RBAC-Berechtigungen verwalten.

  - **Geteilte Active Directory-Berechtigungen**   Wenn die Erstellung von Sicherheitsprinzipalen (z. B. Benutzerkonten) in Ihrer Organisation von einer spezifischen Gruppe außer den Exchange-Administratoren kontrolliert wird, können Sie eine Rollengruppe erstellen und die regulären und delegierenden Rollenzuweisungen für die Rolle "Erstellung von E-Mail-Empfängern" sowie die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" in die neue Rollengruppe verschieben. Dies hindert Mitglieder der Organisationsverwaltung-Rollengruppe am Erstellen von Active Directory-Objekten. Sie können jedoch die neuen Active Directory-Objekte weiterhin für E-Mail aktivieren. Weitere Informationen zu geteilten Berechtigungen finden Sie unter [Grundlegendes zu geteilten Berechtigungen](understanding-split-permissions-exchange-2013-help.md).

## Einschränkungen bei der Anpassung

Jede Rolle kann dieser Rollengruppe hinzugefügt oder daraus entfernt werden, mit den folgenden Einschränkungen:

  - Jede Rolle muss mindestens eine delegierende Rollenzuweisung für eine Rollengruppe oder USG besitzen, bevor die delegierende Rollenzuweisung aus dieser Rollengruppe entfernt werden kann.

  - Die Rolle "Rollenverwaltung" muss mindestens eine reguläre Rollenzuweisung für eine Rollengruppe oder USG besitzen, bevor die reguläre Rollenzuweisung aus dieser Rollengruppe entfernt werden kann.

Diese Einschränkungen sollen verhindern, dass Sie sich aus Versehen aus dem System aussperren. Da immer mindestens eine delegierende Rollenzuweisung zwischen jeder Rolle und einer oder mehreren Rollengruppen oder USGs vorhanden sein muss, können Sie Rollenempfängern immer Rollen zuweisen. Da immer mindestens eine reguläre Rollenzuweisung zwischen der Rollenverwaltungsrolle und einer oder mehreren Rollengruppen oder USGs vorhanden sein muss, können Sie Rollengruppen und Rollenzuweisungen immer konfigurieren.


> [!IMPORTANT]
> Aufgrund dieser Einschränkungen müssen Rollengruppen oder USGs die Ziele der delegierenden und regulären Rollenzuweisungen sein. Sie können eine delegierende Rollenzuweisung sowie die reguläre Zuweisung für die Rolle "Rollenverwaltung" nicht entfernen, wenn die letzte Zuweisung sich auf einen Benutzer bezieht.



## Ausschließlich delegierende Rollenzuweisungen

Einige Rollenzuweisungen zwischen der Rollengruppe Organisationsverwaltung und Verwaltungsrollen wie "Postfachsuche" und "Rollenverwaltung ohne Bereichseinschränkung" sind ausschließlich delegierende Rollenzuweisungen. Diese Rollen ermöglichen den Zugriff auf vertrauliche oder persönliche Informationen, z. B. den Inhalt von Postfächern, oder ermöglichen die Erstellung von Verwaltungsrollen ohne Bereichseinschränkung und mit zahlreichen Berechtigungen.

Mit ausschließlich delegierenden Rollenzuweisungen können Mitglieder der Rollengruppe Organisationsverwaltung ausschließlich die zugeordneten Rollen anderen Rollengruppen, Zuweisungsrichtlinien für Verwaltungsrollen, Benutzern oder USGs zuweisen. Mitglieder der Rolle Organisationsverwaltung erhalten standardmäßig keine Berechtigungen, die von den Rollen bereitgestellt werden. Dies dient dazu, versehentlichen Zugang zu persönlichen Informationen oder eine ungewollte Erhöhung von Berechtigungen zu vermeiden.

Mitglieder der Rollengruppe Organisationsverwaltung können sich selbst jedoch jede Rolle zuweisen. Somit können sie praktisch jede Aufgabe ausführen. Ein Mitglied der Rollengruppe Organisationsverwaltung kann der Rollengruppe Organisationsverwaltung z. B. die Rolle "Postfachsuche" zuweisen. Nach dem Vornehmen dieser Rollenzuweisung können Mitglieder der Rollengruppe Organisationsverwaltung alle Aufgaben ausführen, die ihnen die Rolle "Postfachsuche" ermöglicht.

Weitere Informationen zu delegierenden Rollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

## Zusätzliche Berechtigungen

Die Berechtigungen, die Mitgliedern der Rollengruppe Organisationsverwaltung erteilt werden, werden vor allem von den Verwaltungsrollen bestimmt, die der Rollengruppe zugewiesen sind. Es werden jedoch nicht alle von Ihnen auszuführenden Aufgaben durch Verwaltungsrollen abgedeckt. Einige Aufgaben fallen außerhalb der Exchange-Verwaltungstools an, sodass das RBAC-Berechtigungsmodell für sie nicht gilt. Für diese Aufgaben werden Berechtigungen bereitgestellt, indem die Rollengruppe Organisationsverwaltung den Zugriffssteuerungslisten (Access Control Lists, ACLs) bestimmter Active Directory-Objekte hinzufügt werden.

Den folgenden Aufgaben werden Berechtigungen über ACLs für Active Directory-Objekte erteilt statt über Verwaltungsrollen, die der Rollengruppe Organisationsverwaltung zugewiesen sind:

  - Ausführen von DomainPrep und ForestPrep mithilfe von Setup.exe

  - Bereitstellen weiterer Server in der Organisation

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
<td><p><a href="active-directory-permissions-role-exchange-2013-help.md">Rolle „Active Directory-Berechtigungen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="address-lists-role-exchange-2013-help.md">Rolle „Adresslisten“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="applicationimpersonation-role-exchange-2013-help.md">Rolle „ApplicationImpersonation“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="archiveapplication-role-exchange-2013-help.md">Rolle „ArchiveApplication“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="audit-logs-role-exchange-2013-help.md">Rolle „Überwachungsprotokolle“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="cmdlet-extension-agents-role-exchange-2013-help.md">Rolle „Cmdlet-Erweiterungs-Agents“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="data-loss-prevention-role-exchange-2013-help.md">Rolle „Verhinderung von Datenverlust“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="database-copies-role-exchange-2013-help.md">Rolle „Datenbankkopien“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="databases-role-exchange-2013-help.md">Rolle „Datenbanken“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="disaster-recovery-role-exchange-2013-help.md">Rolle „Notfallwiederherstellung“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="distribution-groups-role-exchange-2013-help.md">Rolle „Verteilergruppen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="edge-subscriptions-role-exchange-2013-help.md">Rolle „Edge-Abonnements“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="e-mail-address-policies-role-exchange-2013-help.md">Rolle „E-Mail-Adressrichtlinien“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="exchange-connectors-role-exchange-2013-help.md">Rolle „Exchange-Connectors“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="exchange-server-certificates-role-exchange-2013-help.md">Rolle „Exchange Server-Zertifikate“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="exchange-servers-role-exchange-2013-help.md">Rolle „Exchange-Server“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="exchange-virtual-directories-role-exchange-2013-help.md">Rolle „Virtuelle Exchange-Verzeichnisse“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="federated-sharing-role-exchange-2013-help.md">Rolle „Verbundfreigabe“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="information-rights-management-role-exchange-2013-help.md">Rolle „Information Rights Management“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="journaling-role-exchange-2013-help.md">Rolle „Journaling“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="legal-hold-role-exchange-2013-help.md">Rolle „Gesetzliche Aufbewahrungspflicht“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="legalholdapplication-role-exchange-2013-help.md">Rolle „LegalHoldApplication“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mail-enabled-public-folders-role-exchange-2013-help.md">Rolle „E-Mail-fähige öffentliche Ordner“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mail-recipient-creation-role-exchange-2013-help.md">Rolle „Erstellung von E-Mail-Empfängern“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mail-recipients-role-exchange-2013-help.md">Rolle „Nachrichtenempfänger“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mail-tips-role-exchange-2013-help.md">Rolle „E-Mail-Infos“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mailbox-import-export-role-exchange-2013-help.md">Rolle „Postfachimport/-export“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mailbox-search-role-exchange-2013-help.md">Rolle „Postfachsuche“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mailboxsearchapplication-role-exchange-2013-help.md">Rolle „MailboxSearchApplication“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="message-tracking-role-exchange-2013-help.md">Rolle „Nachrichtenverfolgung“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="migration-role-exchange-2013-help.md">Rolle „Migration“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="monitoring-role-exchange-2013-help.md">Rolle „Überwachung“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="move-mailboxes-role-exchange-2013-help.md">Rolle „Postfächer verschieben“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="officeextensionapplication-role-exchange-2013-help.md">Rolle „OfficeExtensionApplication“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="organization-client-access-role-exchange-2013-help.md">Rolle „Organisationsclientzugriff“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="organization-configuration-role-exchange-2013-help.md">Rolle „Organisationskonfiguration“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="organization-transport-settings-role-exchange-2013-help.md">Rolle „Organisationstransporteinstellungen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="pop3-and-imap4-protocols-role-exchange-2013-help.md">Rolle „POP3- und IMAP4-Protokolle“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="public-folders-role-exchange-2013-help.md">Rolle „Öffentliche Ordner“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="receive-connectors-role-exchange-2013-help.md">Rolle „Empfangsconnectors“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="recipient-policies-role-exchange-2013-help.md">Rolle „Empfängerrichtlinien“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="remote-and-accepted-domains-role-exchange-2013-help.md">Rolle „Remote- und akzeptierte Domänen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="reset-password-role-exchange-2013-help.md">Rolle „Kennwort zurücksetzen“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="retention-management-role-exchange-2013-help.md">Rolle „Aufbewahrungsmanagement“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="role-management-role-exchange-2013-help.md">Rolle „Rollenverwaltung“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="security-group-creation-and-membership-role-exchange-2013-help.md">Rolle „Sicherheitsgruppenerstellung und -mitgliedschaft“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="send-connectors-role-exchange-2013-help.md">Rolle „Sendeconnectors“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="support-diagnostics-role-exchange-2013-help.md">Rolle &quot;Diagnoseunterstützung&quot;</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="teammailboxlifecycleapplication-role-exchange-2013-help.md">Rolle „TeamMailboxLifecycleApplication“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="transport-agents-role-exchange-2013-help.md">Rolle „Transport-Agents“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="transport-hygiene-role-exchange-2013-help.md">Rolle „Transportschutz“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="transport-queues-role-exchange-2013-help.md">Rolle „Transportwarteschlangen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="transport-rules-role-exchange-2013-help.md">Rolle „Transportregeln“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="um-mailboxes-role-exchange-2013-help.md">Rolle „UM-Postfächer“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="um-prompts-role-exchange-2013-help.md">Rolle „UM-Ansagen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="unscoped-role-management-role-exchange-2013-help.md">Rolle „Rollenverwaltung ohne Bereichseinschränkung“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="unified-messaging-role-exchange-2013-help.md">Serverrolle UnifiedMessaging</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="userapplication-role-exchange-2013-help.md">Rolle „UserApplication“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="user-options-role-exchange-2013-help.md">Rolle „Benutzeroptionen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="view-only-audit-logs-role-exchange-2013-help.md">Rolle „Überwachungsprotokolle nur anzeigen“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="view-only-configuration-role-exchange-2013-help.md">Rolle „Konfiguration (nur Anzeige)“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="view-only-recipients-role-exchange-2013-help.md">Rolle „Empfänger mit Leserechten“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="workloadmanagement-role-exchange-2013-help.md">Rolle „WorkloadManagement“</a></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="my-custom-apps-role-exchange-2013-help.md">Rolle „Eigene benutzerdefinierte Apps“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="my-marketplace-apps-role-exchange-2013-help.md">Rolle „Eigene Marketplace-Apps“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mybaseoptions-role-exchange-2013-help.md">Rolle „MyBaseOptions“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mycontactinformation-role-exchange-2013-help.md">Rolle „MyContactInformation“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mydiagnostics-role-exchange-2013-help.md">Rolle „MyDiagnostics“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mydistributiongroupmembership-role-exchange-2013-help.md">Rolle „MyDistributionGroupMembership“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mydistributiongroups-role-exchange-2013-help.md">Rolle „MyDistributionGroups“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><a href="myprofileinformation-role-exchange-2013-help.md">Rolle „MyProfileInformation“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="myretentionpolicies-role-exchange-2013-help.md">Rolle „MyRetentionPolicies“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="myteammailboxes-role-exchange-2013-help.md">Rolle „MyTeamMailboxes“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mytextmessaging-role-exchange-2013-help.md">Rolle „MyTextMessaging“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="myvoicemail-role-exchange-2013-help.md">Rolle „MyVoiceMail“</a></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>

