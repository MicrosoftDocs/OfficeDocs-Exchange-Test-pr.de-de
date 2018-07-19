---
title: 'Grundlegendes zu Verwaltungsrollengruppen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollengruppen
ms:assetid: 2a92e06c-523e-4fd4-a937-152562b7741d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638105(v=EXCHG.150)
ms:contentKeyID: 50475252
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollengruppen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Eine *Verwaltungsrollengruppe* ist eine universelle Sicherheitsgruppe (Universal Security Group, USG), die im Modell der rollenbasierten Zugriffssteuerungsberechtigungen (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013 verwendet wird. Eine Verwaltungsrollengruppe vereinfacht die Zuweisung von Verwaltungsrollen an eine Gruppe von Benutzern. Allen Mitgliedern einer Rollengruppe werden dieselben Rollen zugewiesen. Rollengruppen sind zugewiesene Administrator- und Spezialistenrollen, die wichtige Verwaltungsaufgaben in Exchange 2013 definieren, z. B. Organisationsverwaltung, Empfängerverwaltung und andere Aufgaben. Mithilfe von Rollengruppen können Sie einer Gruppe von Administratoren oder spezialisierten Benutzern einfacher eine Reihe von Berechtigungen erteilen.


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



**Inhalt**

Rollengruppenebenen

Rollengruppenverwaltung

Integrierte Rollengruppen

Verknüpfte Rollengruppen

Rollengruppendelegierung

Rollengruppenmitgliedschaft

Rollengruppenerstellung (Workflow)


> [!NOTE]
> Informationen zum Zuweisen von Berechtigungen an Benutzer, damit diese die eigenen Postfächer oder Verteilergruppen verwalten können, finden Sie unter <A href="understanding-management-role-assignment-policies-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien</A>.



## Rollengruppenebenen

Im Folgenden handelt es sich um die Ebenen, aus denen das Rollengruppenmodell besteht:

  - **Rollengruppenmitglied**   Bei einem *Rollengruppenmitglied* kann es sich um ein Postfach, eine universelle Sicherheitsgruppe (Universal Security Group (USG) oder eine andere Rollengruppe handeln, die als Mitglied einer Rollengruppe hinzugefügt werden kann. Wenn ein Postfach, eine USG oder eine andere Rollengruppe der Rollengruppe als Mitglied hinzugefügt wird, werden alle Zuweisungen, die zwischen Verwaltungsrollen und Rollengruppen erfolgt sind, auf das neue Mitglied angewendet. Dadurch werden dem neuen Mitglied sämtliche von den Verwaltungsrollen bereitgestellten Berechtigungen erteilt.

  - **Verwaltungsrollengruppe**   Die *Verwaltungsrollengruppe* ist eine spezielle universelle Sicherheitsgruppe mit Postfächern, USGs und anderen Rollengruppen, die Mitglieder der Rollengruppe sind. Hier werden Mitglieder hinzugefügt und entfernt und auch Verwaltungsrollen zugewiesen. Die Kombination all dieser Rollen in einer Rollengruppe definiert alle Elemente, welche die einer Rollengruppe hinzugefügten Mitglieder in der Exchange-Organisation verwalten können.

  - **Verwaltungsrollenzuweisung**   Eine *Verwaltungsrollenzuweisung* verknüpft eine Verwaltungsrolle und eine Rollengruppe. Durch das Zuweisen einer Verwaltungsrolle zu einer Rollengruppe wird Mitgliedern der Rollengruppe die Möglichkeit gegeben, die in der Verwaltungsrolle definierten Cmdlets und Parameter zu verwenden. ‏Rollenzuweisungen können Verwaltungsbereiche verwenden, um zu steuern, wo die Zuweisung verwendet werden kann. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

  - **Verwaltungsrollenbereich**   Ein *Verwaltungsrollenbereich* ist der Einfluss- oder Wirkungsbereich einer Rollenzuweisung. Wird eine Rolle mit einem Bereich einer Rollengruppe zugewiesen, grenzt der Verwaltungsbereich genau ein, welche Objekte diese Zuweisung verwalten darf. Die Zuweisung und ihr Bereich werden dann auf die Mitglieder der Rollengruppe übertragen. Dadurch wird eingeschränkt, was diese Mitglieder verwalten können. Ein Bereich kann aus Listen von Servern oder Datenbanken, aus Organisationseinheiten oder aus Filtern für Server-, Datenbank- oder Empfängerobjekte bestehen. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

  - **Verwaltungsrolle**   Eine *Verwaltungsrolle* ist ein Container für eine Gruppierung von Verwaltungsrolleneinträgen. Rollen werden verwendet, um die spezifischen Aufgaben zu definieren, die von den Mitgliedern einer Rollengruppe, der die Rolle zugewiesen wird, ausgeführt werden können. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

  - **Verwaltungsrolleneinträge** *Verwaltungsrolleneinträge* sind die einzelnen Einträge in einer Verwaltungsrolle, die Zugriff auf Cmdlets, Skripts und andere spezielle Berechtigungen für die Durchführung einer bestimmten Aufgabe erteilen. Meistens bestehen Rolleneinträge aus einem Cmdlet oder Skript und den Parametern, auf die von der Verwaltungsrolle und damit der Rollengruppe, der die Rolle zugewiesen ist, zugegriffen werden kann.

Die folgende Abbildung zeigt die einzelnen Rollengruppenebenen in der vorhergehenden Liste und die Beziehung der einzelnen Ebenen zueinander an.

**Ebenen der Verwaltungsrollengruppen**

![Ebenen der Verwaltungsrollengruppen](images/Dd638105.a98c237c-7bdb-434b-8c98-22509e46cccf(EXCHG.150).gif "Ebenen der Verwaltungsrollengruppen")

Weitere Informationen zu RBAC finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

Zurück zum Seitenanfang

## Rollengruppenverwaltung

Wenn Sie eine Rollengruppe erstellen, erstellen Sie die universelle Sicherheitsgruppe für die Mitglieder der Rollengruppe, und Sie erstellen die Zuweisungen zwischen der Rollengruppe und den von Ihnen festgelegten Verwaltungsrollen. Sie können optional auch einen Verwaltungsbereich für die Rollenzuweisungen festlegen und Postfächer, die Mitglieder der neuen Rollengruppe werden sollen, hinzufügen.

Nachdem Sie eine Rollengruppe erstellt haben, wird jede Ebene zu einem unabhängigen Objekt. Die Rollengruppe ist auch weiterhin der zentrale Punkt, an dem alle Ebenen zusammentreffen. Allerdings wird jede Ebene einzeln verwaltet. Wenn Sie beispielsweise den Verwaltungsbereich ändern wollen, den Sie beim Erstellen der Rollengruppe angewendet haben, müssen Sie den Bereich nach dem Erstellen der Rollengruppe für jede einzelne Rollenzuweisung ändern. Die Verwaltung des Rollengruppenmodells erfolgt mithilfe der Cmdlets zur Verwaltung der einzelnen Ebenen des Rollengruppenmodells.

Die folgende Tabelle enthält eine Liste der Rollengruppenebenen und Links zu Vorgehensweisen bei der Verwaltung der einzelnen Ebenen.

### Rollengruppenverwaltung

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ebene des Rollengruppenmodells</th>
<th>Verwaltungsthema</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rollengruppenmitglied</p></td>
<td><p><a href="manage-role-group-members-exchange-2013-help.md">Verwalten von Rollengruppenmitgliedern</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Rollengruppe</p></td>
<td><p><a href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltungsrollen und -zuweisungen</p></td>
<td><p><a href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</a></p></td>
</tr>
<tr class="even">
<td><p>Verwaltungsrolleneinträge</p></td>
<td><p><a href="add-a-role-entry-to-a-role-exchange-2013-help.md">Hinzufügen eines Rolleneintrags zu einer Rolle</a></p>
<p><a href="change-a-role-entry-exchange-2013-help.md">Ändern Sie einen rolleneintrag</a></p>
<p><a href="remove-a-role-entry-from-a-role-exchange-2013-help.md">Entfernen eines Rolleneintrags aus einer Rolle</a></p>

> [!NOTE]
> Beim Ändern der Verwaltungsrolleneinträge in Verwaltungsrollen einer Rollengruppe handelt es sich um eine fortgeschrittene Aufgabe, die in den meisten Fällen nicht erforderlich ist. Sie können stattdessen wahrscheinlich eine bereits bestehende Verwaltungsrolle verwenden, die Ihren Anforderungen entspricht. Weitere Informationen finden Sie unter <A href="built-in-role-groups-exchange-2013-help.md">Integrierte Rollengruppen</A>.


</td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Integrierte Rollengruppen

Integrierte Rollengruppen sind Rollen, die im Lieferumfang von Exchange 2013 enthalten sind. Ihnen wird damit eine Reihe von Rollengruppen an die Hand gegeben, mit denen Sie verschiedene Ebenen an Administratorrechten für Benutzergruppen bereitstellen können. Sie können Benutzer allen integrierten Rollengruppen hinzufügen oder aus diesen entfernen. Sie können auch Rollenzuweisungen den meisten Rollengruppen hinzufügen oder aus diesen entfernen. Ausnahmen:

  - Sie können keine delegierenden Rollenzuweisungen aus der Rollengruppe Organisationsverwaltung entfernen.

  - Sie können die Rollenverwaltungsgruppe nicht aus der Rollengruppe Organisationsverwaltung entfernen.

Die folgende Tabelle führt alle in Exchange 2013 enthaltenen integrierten Rollengruppen auf. Weitere Informationen zu integrierten Rollengruppen finden Sie unter [Integrierte Rollengruppen](built-in-role-groups-exchange-2013-help.md).

### Integrierte Rollengruppen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rollengruppe</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Organisationsverwaltung sind, verfügen über Administratorzugriff auf die gesamte Exchange 2013-Organisation und können fast jede Aufgabe für beliebige Exchange 2013-Objekte durchführen, mit einigen Ausnahmen. Mitglieder dieser Rollengruppe können Postfachsuchen und die Verwaltung von Verwaltungsrollen oberster Ebene ohne Bereichseinschränkung standardmäßig nicht durchführen.</p></td>
</tr>
<tr class="even">
<td><p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Organisationsverwaltung – nur Leserechte sind, können die Eigenschaften aller Objekte in der Exchange-Organisation anzeigen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Empfängerverwaltung sind, haben Administratorzugriff zum Erstellen oder Ändern von Exchange 2013-Empfängern innerhalb der Exchange 2013-Organisation.</p></td>
</tr>
<tr class="even">
<td><p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe UM-Verwaltung sind, können Funktionen in der Exchange-Organisation wie z. B. UM-Dienste (Unified Messaging), UM-Eigenschaften für Postfächer, UM-Telefonansagen und automatische UM-Telefonzentralen konfigurieren und verwalten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a></p></td>
<td><p>Administratoren oder Benutzer, die Mitglied der Rollengruppe Discoveryverwaltung sind, können Postfächer in der Exchange-Organisation nach Daten durchsuchen, die mit bestimmten Kriterien übereinstimmen. Zudem können diese Mitglieder Beweissicherungsverfahren für Postfächer konfigurieren.</p></td>
</tr>
<tr class="even">
<td><p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
<td><p>Benutzer, die Mitglied der Rollengruppe Datensatzverwaltung sind, können Funktionen für die Einhaltung von Vorschriften, z. B. Aufbewahrungsrichtlinientags, Nachrichtenklassifikationen, Transportregeln usw., konfigurieren.</p></td>
</tr>
<tr class="odd">
<td><p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
<td><p>Administratoren, die Mitglied dieser Rollengruppe sind, können die serverspezifische Konfiguration von Transport-, Clientzugriffs- und Postfachfunktionen wie Datenbankkopien, Zertifikate, Transportwarteschlangen und Sendeconnectors, virtuelle Verzeichnisse und Clientzugriffsprotokolle konfigurieren.</p></td>
</tr>
<tr class="even">
<td><p><a href="help-desk-exchange-2013-help.md">Helpdesk</a></p></td>
<td><p>Benutzer, die Mitglied der Rollengruppe &quot;Helpdesk&quot; sind, können eine eingeschränkte Empfängerverwaltung von Exchange 2013-Empfängern ausführen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
<td><p>Benutzer, die Mitglied der Rollengruppe für die Verwaltung von aktivem Nachrichtenschutz sind, können die Antispam- und Antischadsoftwarefunktionen von Exchange 2013 konfigurieren. Drittanbieterprogramme, die in Exchange 2013 integriert werden können, können dieser Rollengruppe Dienstkonten hinzufügen, damit Programme Zugriff auf die Cmdlets haben, die zum Abrufen und Konfigurieren der Exchange-Konfiguration erforderlich sind.</p></td>
</tr>
<tr class="even">
<td><p><a href="compliance-management-exchange-2013-help.md">Verwaltung der Richtlinientreue</a></p></td>
<td><p>Benutzer, die Mitglied der Rollengruppe für die Verwaltung der Richtlinientreue sind, können die Exchange-Richtlinientreue in Übereinstimmung mit ihren Richtlinien konfigurieren und verwalten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="public-folder-management-exchange-2013-help.md">Verwaltung Öffentlicher Ordner</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe zur Verwaltung öffentlicher Ordner sind, können öffentliche Ordner auf Exchange 2013-Servern verwalten.</p></td>
</tr>
<tr class="even">
<td><p><a href="delegated-setup-exchange-2013-help.md">Delegiertes Setup</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Delegiertes Setup sind, können Exchange 2013-Server bereitstellen, die zuvor durch ein Mitglied der Rollengruppe Organisationsverwaltung bereitgestellt wurden.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Verknüpfte Rollengruppen

Verknüpfte Rollengruppen werden in Organisationen verwendet, die Exchange 2013 in einer dedizierten Ressourcengesamtstruktur installieren und Benutzer in anderen vertrauenswürdigen, fremden Gesamtstrukturen platzieren. Wie der Name bereits andeutet, erstellen verknüpfte Rollengruppen einen Link zwischen einer Rollengruppe in der Exchange-Gesamtstruktur und einer universellen Sicherheitsgruppe in einer fremden Gesamtstruktur. Dies ist hilfreich, wenn sich die Active Directory-Domänendienst-Benutzerkonten (AD DS) der Administratoren, die Exchange verwalten sollen, nicht in derselben Gesamtstruktur befinden wie Exchange. Verknüpfte Rollengruppen können nur einer fremden universellen Sicherheitsgruppe zugeordnet werden. Außerdem müssen Sie keine bidirektionale Vertrauensstellung zwischen der Exchange-Gesamtstruktur und der fremden Gesamtstruktur erstellen. Die Exchange-Gesamtstruktur muss der fremden Gesamtstruktur vertrauen, aber die fremde Gesamtstruktur muss der Exchange-Gesamtstruktur nicht vertrauen.

Weitere Informationen zu Berechtigungen in Topologien mit mehreren Gesamtstrukturen finden Sie unter [Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen](understanding-multiple-forest-permissions-exchange-2013-help.md).

Eine verknüpfte Rollengruppe besteht aus zwei Teilen:

  - **Verknüpfte Rollengruppe**   Die verknüpfte Rollengruppe ist ein Containerobjekt, das die fremde universelle Sicherheitsgruppe mit den der Rollengruppe zugewiesenen Verwaltungsrollenzuweisungen verknüpft.

  - **Fremde universelle Sicherheitsgruppe**   Die fremde universelle Sicherheitsgruppe enthält die Mitglieder, denen die von der verknüpften Rollengruppe bereitgestellten Berechtigungen erteilt werden sollten.

Wenn Sie eine verknüpfte Rollengruppe erstellen, stellen Sie einen Domänencontroller in der fremden Gesamtstruktur bereit, in der sich die Benutzer befinden, die die Exchange-Gesamtstruktur verwalten sollen, die universelle Sicherheitsgruppe mit diesen Benutzern als Mitglieder, den Namen der fremden universellen Sicherheitsgruppe sowie die für den Zugriff auf die fremde Gesamtstruktur erforderlichen Anmeldeinformationen. Exchange fügt die Sicherheits-ID (SID) der fremden universellen Sicherheitsgruppe der verknüpften Rollengruppe hinzu. Da die SID der universellen Sicherheitsgruppe die einzige Identifikation der fremden Gesamtstruktur darstellt, sollten Sie die fremde Gesamtstruktur unbedingt im Namen der Rollengruppe angeben, sofern mehrere Gesamtstrukturen vorliegen.

Eine verknüpfte Rollengruppe enthält keine Mitglieder. Alle Mitglieder der Rollengruppe werden mithilfe der fremden universellen Sicherheitsgruppe verwaltet. Das bedeutet, dass Sie die Cmdlets **Update-RoleGroupMember**, **Add-RoleGroupMember** oder **Remove-RoleGroupMember** nicht zum Hinzufügen oder Entfernen von Rollengruppenmitgliedern verwenden können. Wenn Sie der fremden universellen Sicherheitsgruppe Mitglieder hinzufügen, erhalten diese die von der verknüpften Rollengruppe bereitgestellten Berechtigungen.

Sie können eine Standardrollengruppe, die eigene Mitglieder enthält, nicht in eine verknüpfte Rollengruppe ändern oder umgekehrt. Wenn Sie eine Rollengruppe von einer Standardrollengruppe in eine verknüpfte Rollengruppe ändern möchten, müssen Sie eine neue verknüpfte Rollengruppe erstellen und die Verwaltungsrollenzuweisungen aus der Standardrollengruppe in der verknüpften Rollengruppe replizieren. Dies gilt auch für integrierte Rollengruppen, da es sich ebenfalls um Standardrollengruppen handelt. Wenn Sie die gesamte Verwaltung der Exchange-Gesamtstruktur aus einer fremden Gesamtstruktur ausführen möchten, müssen Sie neue verknüpfte Rollengruppen erstellen und die in den integrierten Rollengruppen vorhandenen Verwaltungsrollen den neuen verknüpften Rollengruppen hinzufügen. Weitere Informationen hierzu finden Sie unter [Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln](create-linked-role-groups-that-mirror-built-in-role-groups-exchange-2013-help.md).

Zurück zum Seitenanfang

## Rollengruppendelegierung

Standardmäßig können Mitglieder der Rollengruppe Organisationsverwaltung Mitglieder zu Rollengruppen hinzufügen und daraus entfernen. Unter Umständen möchten Sie jedoch Benutzern, die keine Mitglieder der Rollengruppe Organisationsverwaltung sind, das Hinzufügen und Entfernen von Rollengruppenmitgliedern ermöglichen. In diesem Fall können Sie die Rollengruppendelegierung verwenden.

Die Rollengruppendelegierung wird durch die Eigenschaft **ManagedBy** der jeweiligen Rollengruppe gesteuert. Die Eigenschaft **ManagedBy** enthält eine Liste der Benutzer, die Mitglieder zur Rollengruppe hinzufügen und daraus entfernen oder die Konfiguration einer Rollengruppe ändern können. Den Benutzern werden keine von der Rollengruppe erteilten Berechtigungen zugewiesen, sofern sie nicht zugleich Mitglieder der Rollengruppe sind.

Wird für eine Rollengruppe die Eigenschaft **ManagedBy** festgelegt, können nur die Benutzer, die als Rollengruppenmanager für diese Eigenschaft aufgeführt sind, eine Rollengruppe oder die Mitgliedschaft einer Rollengruppe standardmäßig ändern. Diese Einschränkung kann jedoch durch einen optionalen Parameter für Cmdlets zum Ändern von Rollengruppen oder Rollengruppenmitgliedschaften außer Kraft gesetzt werden. Die Option *BypassSecurityGroupManagerCheck* kann von Benutzern verwendet werden, die Mitglied der Rolle Organisationsverwaltung sind oder denen, direkt oder indirekt, die Verwaltungsrolle "Rollenverwaltung" zugewiesen wird. Wird diese Option verwendet, wird die Eigenschaft **ManagedBy** ignoriert, und der Benutzer kann die Rollengruppe oder Rollengruppenmitgliedschaft ändern.

Ist die Eigenschaft **ManagedBy** für eine Rollengruppe nicht festgelegt, können nur Benutzer eine Rollengruppe oder Rollengruppenmitgliedschaft ändern, die Mitglied der Rolle Organisationsverwaltung sind oder denen, direkt oder indirekt, die Verwaltungsrolle "Rollenverwaltung" zugewiesen ist.


> [!NOTE]
> Einer Rollengruppe zugewiesene Rollen können mithilfe der delegierenden Rollenzuweisung zugewiesen werden. Mit delegierenden Rollenzuweisungen können Mitglieder einer Rollengruppe, der eine delegierte Rolle zugewiesen ist, diese Rolle einer anderen Rollengruppe, Zuweisungsrichtlinie oder universellen Sicherheitsgruppe zuweisen. Mitglieder der Rollengruppe können nur diese Rolle zuweisen und nicht die Rollengruppe delegieren, es sei denn, sie werden auch der Eigenschaft <STRONG>ManagedBy</STRONG> hinzugefügt. Weitere Informationen zu delegierenden Rollenzuweisungen finden Sie unter <A href="understanding-management-role-assignments-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollenzuweisungen</A>.



Weitere Informationen zum Verwalten der Rollengruppendelegierung finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Zurück zum Seitenanfang

## Rollengruppenmitgliedschaft

Wenn ein Benutzer zum Mitglied einer Rollengruppe gemacht wird, werden die der Rollengruppe zugewiesenen Verwaltungsrollen dem Benutzer zugewiesen. Ist ein Benutzer Mitglied mehrerer Rollengruppen, werden die Verwaltungsrollen der einzelnen Rollengruppen zusammengefasst und dem Benutzer zugewiesen. Benutzer, universelle Sicherheitsgruppen und andere Rollengruppen können Mitglieder von Rollengruppen sein.

Nur Benutzer, die Mitglied der Rollengruppe Organisationsverwaltung oder "Rollenverwaltung" sind, und Benutzer, denen die Berechtigung zum Hinzufügen oder Entfernen von Benutzern zu bzw. aus Rollengruppen erteilt wurde, können Rollengruppenmitgliedschaften verwalten.

Weitere Informationen zum Verwalten der Rollengruppenmitgliedschaft finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

## Rollengruppenerstellung (Workflow)

Wie bereits erwähnt, besteht eine Rollengruppe aus mehreren Ebenen. Das Erstellen einer neuen Rollengruppe wird im folgenden Beispiel veranschaulicht.

    New-RoleGroup -Name "Seattle Recipient Management" -Roles "Mail Recipients", "Distribution Groups", "Move Mailboxes", "UM Mailboxes" -CustomRecipientWriteScope "Seattle Users", -ManagedBy "Brian", "David", "Katie" -Members "Ray", "Jenn", "Maria", "Chris", "Maija", "Carter", "Jenny", "Sam", "Lukas", "Isabel", "Katie"

Wenn der obige Befehl ausgeführt wird, geschieht Folgendes:

1.  Es wird ein neues Rollengruppenobjekt erstellt, bei dem es sich um eine spezielle universelle Sicherheitsgruppe mit dem Namen "Seattle Recipient Management" handelt.

2.  Die Postfächer für Ray, Jenn, Maria, Chris, Maija, Carter, Jenny, Sam, Lukas, Isabel und Katie werden als Mitglieder der Rollengruppe hinzugefügt. Diese Benutzer erhalten die von dieser Rollengruppe bereitgestellten Berechtigungen.

3.  Die Benutzer Brian und David werden der Eigenschaft **ManagedBy** der Rollengruppe hinzugefügt. Diese Benutzer können Mitglieder zur Rollengruppe hinzufügen und daraus entfernen, erhalten jedoch keine von der Rollengruppe bereitgestellten Berechtigungen, da sie keine Mitglieder sind. Auch Katie wird der Eigenschaft **ManagedBy** der Rollengruppe hinzugefügt. Da sie der Eigenschaft **ManagedBy** hinzugefügt wird und ein Mitglied der Rollengruppe ist, kann sie Mitglieder zur Rollengruppe hinzufügen und daraus entfernen und erhält darüber hinaus die von der Rollengruppe bereitgestellten Berechtigungen.

4.  Die folgenden Verwaltungsrollenzuweisungen werden erstellt. Die Rollenzuweisungen weisen der Rollengruppe jede im Befehl angegebene Verwaltungsrolle zu. Der Verwaltungsbereich "Seattle Users" wird jeder Rollenzuweisung hinzugefügt. Der Name der einzelnen Rollenzuweisungen besteht aus einer Kombination der zugewiesenen Verwaltungsrolle und des Rollengruppennamens.
    
      - `Mail Recipients_Seattle Recipient Management`
    
      - `Distribution Groups_Seattle Recipient Management`
    
      - `Move Mailboxes_Seattle Recipient Management`
    
      - `UM Mailboxes_Seattle Recipient Management`

Wenn Sie die Ergebnisse dieses Befehls mit der Abbildung zu den Ebenen der Verwaltungsrollengruppe weiter oben in diesem Thema vergleichen, können Sie sehen, in welchem Zusammenhang die einzelnen Schritte mit den Rollengruppenebenen stehen. Informationen zum Verwalten der einzelnen Rollengruppenebenen finden Sie weiter oben in den Themen zur Rollengruppenverwaltung.

Zurück zum Seitenanfang

