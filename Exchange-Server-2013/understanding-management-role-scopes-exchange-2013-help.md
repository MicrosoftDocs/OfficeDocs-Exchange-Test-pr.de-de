---
title: 'Grundlegendes zu Verwaltungsrollenbereichen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollenbereichen
ms:assetid: 24ed4a38-438a-4223-9f9c-5d4dea4b046b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335146(v=EXCHG.150)
ms:contentKeyID: 50475228
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollenbereichen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

*Verwaltungsrollenbereiche* ermöglichen Ihnen die Definition spezifischer Wirkungs- oder Einflussbereiche für eine Verwaltungsrolle, wenn eine Verwaltungsrollenzuweisung erstellt wird. Wenn Sie einen Bereich anwenden, kann der Rollenempfänger, dem die Rolle zugewiesen wird, nur die in diesem Bereich enthaltenen Objekte ändern. Ein Rollenempfänger kann eine Verwaltungsrollengruppe, eine Verwaltungsrolle, eine Richtlinie für eine Verwaltungsrollenzuweisung, ein Benutzer oder eine universelle Sicherheitsgruppe (Universal Security Group, USG) sein. Weitere Informationen zu Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



Jede Verwaltungsrolle, ob integrierte oder benutzerdefinierte Rolle, hat Verwaltungsbereiche. Es kann sich dabei um folgende Verwaltungsbereiche handeln:

  - **Regulär**   Ein *regulärer Bereich* ist nicht exklusiv. Er bestimmt, wo Objekte in Active Directory von Benutzern, denen die Verwaltungsrolle zugewiesen ist, angezeigt oder geändert werden können. Im Allgemeinen gibt eine Verwaltungsrolle an, was Sie erstellen oder ändern können, und ein Verwaltungsrollenbereich, wo Sie etwas erstellen oder ändern können. Reguläre Bereiche können implizite oder explizite Bereiche sein. Beide werden weiter unten in diesem Thema erläutert.

  - **Exklusive**   Ein *exklusiver Bereich* verhält sich nahezu identisch wie ein regulärer Bereich. Der wichtigste Unterschied besteht darin, dass Sie Benutzern den Zugriff auf Objekte innerhalb des exklusiven Bereichs verweigern können, wenn diesen Benutzern keine dem exklusiven Bereich zugeordnete Rolle zugewiesen ist. Alle exklusiven Bereiche sind explizite Bereiche, die weiter unten in diesem Thema erläutert werden.
    
    Weitere Informationen zu exklusiven Bereichen finden Sie unter [Grundlegendes zu exklusiven Bereichen](understanding-exclusive-scopes-exchange-2013-help.md).

Bereiche können von der Verwaltungsrolle geerbt, als vordefinierter relativer Bereich für eine Verwaltungsrollenzuweisung festgelegt oder mithilfe benutzerdefinierter Filter erstellt und einer Verwaltungsrollenzuweisung hinzugefügt werden. Von Verwaltungsrollen geerbte Bereiche werden *implizite Bereiche* genannt, während vordefinierte und benutzerdefinierte Bereiche als *explizite Bereiche* bezeichnet werden. In den folgenden Abschnitten werden die einzelnen Bereichstypen beschrieben:

  - Implizite Bereiche

  - Explizite Bereiche

  - Vordefinierte relative Bereiche

  - Benutzerdefinierte Bereiche
    
      - Filterbasierte Empfängerbereiche
    
      - Konfigurationsbereiche

Jede Rolle kann die folgenden Bereichstypen haben:

  - **Empfängerlesebereich**  Der implizite Empfängerlesebereich bestimmt, welche Empfängerobjekte der Benutzer, dem die Verwaltungsrolle zugewiesen wird, aus Active Directory lesen kann.

  - **Empfängerschreibbereich**  Der implizite Empfängerschreibbereich bestimmt, welche Empfängerobjekte der Benutzer, dem die Verwaltungsrolle zugewiesen wird, in Active Directory ändern kann.

  - **Konfigurationslesebereich**  Der implizite Konfigurationslesebereich bestimmt, welche Konfigurationsobjekte der Benutzer, dem die Verwaltungsrolle zugewiesen wird, aus Active Directory lesen kann.

  - **Konfigurationsschreibbereich**    Der implizite Konfigurationsschreibbereich bestimmt, welche Organisations-, Datenbank- und Serverobjekte der Benutzer, dem die Verwaltungsrolle zugewiesen wird, in Active Directory ändern kann.

Empfängerobjekte umfassen Postfächer, Verteilergruppen, E-Mail-aktivierte Benutzer und andere Objekte. Konfigurationsobjekte umfassen Server mit Microsoft Exchange Server 2013 sowie Datenbanken auf Servern mit Exchange. Bei den Bereichstypen kann es sich jeweils um einen impliziten oder einen expliziten Bereich handeln.

## Implizite Bereiche

Implizite Bereiche sind die für einen Verwaltungsrollentyp geltenden Standardbereiche. Da implizite Bereiche einem Verwaltungsrollentyp zugeordnet sind, besitzen alle übergeordneten und untergeordneten Verwaltungsrollen mit demselben Rollentyp auch dieselben impliziten Bereiche. Implizite Bereiche gelten sowohl für integrierte Verwaltungsrollen als auch für benutzerdefinierte Verwaltungsrollen. Weitere Informationen zu Verwaltungsrollen und Verwaltungsrollentypen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

In der folgenden Tabelle sind alle impliziten Bereiche aufgeführt, die für Verwaltungsrollen definiert werden können.

### Implizite Bereiche, die für Verwaltungsrollen definiert sind

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Implizite Bereiche</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Organization</code></p></td>
<td><p>Wenn im Schreibbereich des Rollenempfängers <code>Organization</code> enthalten ist, kann die Rolle Empfängerobjekte in der gesamten Exchange-Organisation erstellen oder ändern.</p>
<p>Wenn im Lesebereich des Rollenempfängers <code>Organization</code> enthalten ist, kann die Rolle Empfängerobjekte in der gesamten Exchange-Organisation anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>MyGAL</code></p></td>
<td><p>Wenn im Lesebereich des Rollenempfängers <code>MyGAL</code> enthalten ist, kann die Rolle die Eigenschaften aller Empfänger in der aktuellen globalen Adressliste des Benutzers (Global Address List, GAL) anzeigen.</p>
<p>Wenn im Lesebereich des Rollenempfängers <code>MyGAL</code> enthalten ist, kann die Rolle die Eigenschaften aller Empfänger in der aktuellen globalen Adressliste des Benutzers anzeigen.</p>
<p>Dieser Bereich wird nur mit Empfängerlesebereichen verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><code>Self</code></p></td>
<td><p>Ist im Schreibbereich des Rollenempfängers <code>Self</code> enthalten, kann die Rolle nur die Eigenschaften des Postfachs des aktuellen Benutzers ändern.</p>
<p>Ist im Lesebereich des Rollenempfängers <code>Self</code> enthalten, kann die Rolle nur die Eigenschaften des Postfachs des aktuellen Benutzers anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p>Wenn im Schreibbereich des Rollenempfängers <code>MyDistributionGroups</code> enthalten ist, kann die Rolle Verteilerlistenobjekte im Besitz des aktuellen Benutzers erstellen oder ändern.</p>
<p>Wenn im Lesebereich des Rollenempfängers <code>MyDistributionGroups</code> enthalten ist, kann die Rolle Verteilerlistenobjekte im Besitz des aktuellen Benutzers anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><code>OrganizationConfig</code></p></td>
<td><p>Wenn <code>OrganizationConfig</code> im Konfigurationsschreibbereich der Rolle vorhanden ist, kann die Rolle alle Server- oder Datenbankkonfigurationsobjekte in der gesamten Exchange-Organisation erstellen oder ändern.</p>
<p>Wenn <code>OrganizationConfig</code> im Konfigurationslesebereich der Rolle vorhanden ist, kann die Rolle alle Server- oder Datenbankkonfigurationsobjekte in der gesamten Exchange-Organisation anzeigen.</p>
<p>Dieser Bereich wird mit Konfigurationslese- und -schreibbereichen verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>None</code></p></td>
<td><p>Wenn sich <code>None</code> in einem Bereich befindet, ist dieser Bereich nicht für die Rolle verfügbar. Wenn beispielsweise im Empfängerschreibbereich einer Rolle <code>None</code> enthalten ist, kann die Rolle keine Empfängerobjekte in der Exchange-Organisation ändern.</p></td>
</tr>
</tbody>
</table>


Wird eine Rolle einem Rollenempfänger zugewiesen und es sind keine vordefinierten oder benutzerdefinierten Bereiche angegeben, werden die für die Rolle definierten impliziten Bereiche verwendet, um zu steuern, welche Empfänger- bzw. Organisationsobjekte der Benutzer anzeigen oder ändern kann.

Der implizite Schreibbereich einer Rolle ist stets kleiner oder gleich dem impliziten Lesebereich. Dies bedeutet, dass eine Rolle keine Objekte ändern kann, die vom Bereich nicht angezeigt werden können.

Sie können die für Verwaltungsrollen definierten impliziten Bereiche nicht ändern. Sie können jedoch den impliziten Schreibbereich und Konfigurationsbereich für eine Verwaltungsrolle außer Kraft setzen. Wenn ein vordefinierter relativer Bereich oder benutzerdefinierter Bereich für eine Rollenzuweisung verwendet wird, wird der implizite Schreibbereich der Rolle außer Kraft gesetzt, und der neue Bereich hat Vorrang. Der implizite Lesebereich einer Rolle ist stets gültig und kann nicht außer Kraft gesetzt werden. Weitere Informationen finden Sie unter Vordefinierte relative Bereiche und Benutzerdefinierte Bereiche.

Erweitern Sie die folgende Tabelle, um eine Liste aller integrierten Verwaltungsrollen und ihrer impliziten Bereiche anzuzeigen. Weitere Informationen zu den einzelnen integrierten Rollen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

## Implizite Bereiche integrierter Verwaltungsrollen


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrolle</th>
<th>Empfängerlesebereich</th>
<th>Empfängerschreibbereich</th>
<th>Konfigurationslesebereich</th>
<th>Konfigurationsschreibbereich</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Active Directory Permissions</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Address Lists</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>ApplicationImpersonation</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>ArchiveApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Audit Logs</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Cmdlet Extension Agents</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Data Loss Prevention</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Database Availability Groups</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Database Copies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Databases</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Disaster Recovery</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Distribution Groups</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Edge Subscriptions</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>E-Mail Address Policies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Exchange Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Exchange Server Certificates</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Exchange Servers</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Exchange Virtual Directories</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Federated Sharing</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Information Rights Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Journaling</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Legal Hold</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>LegalHoldApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mail Enabled Public Folders</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mail Recipient Creation</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mail Recipients</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mail Tips</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mailbox Import Export</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mailbox Search</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>MailboxSearchApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Message Tracking</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Migration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Monitoring</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Move Mailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>OfficeExtensionApplication</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>My Custom Apps</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>My Marketplace Apps</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyAddressInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyBaseOptions</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyContactInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyDiagnostics</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyDisplayName</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyDistributionGroupMembership</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyMobileInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyName</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyPersonalInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyProfileInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyRetentionPolicies</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyTeamMailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyTextMessaging</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyVoiceMail</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Organization Client Access</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Organization Configuration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Organization Transport Settings</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>POP3 And IMAP4 Protocols</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Public Folders</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Receive Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Recipient Policies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Remote and Accepted Domains</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Reset Password</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Retention Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Role Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Security Group Creation and Membership</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Send Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Support Diagnostics</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>TeamMailboxLifecycleApplication</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Transport Agents</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Transport Hygiene</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Transport Queues</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Transport Rules</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>UM Mailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>UM Prompts</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Unified Messaging</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>UnScoped Role Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>UserApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>User Options</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>View-Only Audit Logs</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>View-Only Configuration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>View-Only Recipients</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>WorkloadManagement</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>


## Explizite Bereiche

Explizite Bereiche sind Bereiche, die Sie selbst festlegen, um zu steuern, welche Objekte eine Verwaltungsrolle ändern kann. Während implizite Bereiche für eine Verwaltungsrolle definiert sind, sind explizite Bereiche für eine Verwaltungsrollenzuweisung definiert. Auf diese Weise können implizite Bereiche konsistent für alle Verwaltungsrollen angewendet werden, wenn sie nicht von Ihnen durch einen expliziten Bereich außer Kraft gesetzt werden. Weitere Informationen zu Verwaltungsrollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Explizite Bereiche setzen die impliziten Schreib- und Konfigurationsbereiche einer Verwaltungsrolle außer Kraft. Sie setzen nicht den impliziten Lesebereich einer Verwaltungsrolle außer Kraft. Der implizite Lesebereich definiert weiterhin, welche Objekte die Verwaltungsrolle lesen kann.

Explizite Bereiche sind nützlich, wenn der implizite Schreibbereich einer Verwaltungsrolle den Anforderungen Ihres Unternehmens nicht entspricht. Sie können einen expliziten Bereich hinzufügen, der nahezu alles Gewünschte enthält, solange der neue Bereich nicht die Grenzen des impliziten Lesebereichs überschreitet. Die zu einer Verwaltungsrolle gehörenden Cmdlets müssen Informationen zu den Objekten oder Containern lesen können, die Objekte enthalten, damit die Cmdlets Objekte erstellen oder ändern können. Wenn beispielsweise der implizite Lesebereich für eine Verwaltungsrolle auf `Self` festgelegt wird, können Sie keinen expliziten Schreibbereich `Organization` hinzufügen, da der explizite Schreibbereich die Grenzen des impliziten Lesebereichs überschreitet.

Weitere Informationen hierzu finden Sie in den folgenden Abschnitten:

  - Vordefinierte relative Bereiche

  - Benutzerdefinierte Bereiche

## Vordefinierte relative Bereiche

Exchange 2013 bietet mehrere vordefinierte relative Schreibbereiche, die Sie zum Ändern des Bereichs einer Verwaltungsrolle verwenden können. Vordefinierte relative Bereiche bieten eine einfache Möglichkeit, um stärker auf die Anforderungen Ihres Unternehmens einzugehen, ohne manuell benutzerdefinierte Bereiche erstellen zu müssen. Die Bereiche werden deshalb als relativ bezeichnet, weil sie relativ sind für den Rollenempfänger, dem die zugeordnete Rollenzuweisung zugewiesen wird. So beschränkt beispielsweise der vordefinierte relative Bereich `Self` den Schreibbereich allein auf den aktuellen Benutzer. Der vordefinierte relative Bereich `MyDistributionGroups` beschränkt den Schreibbereich auf die Verteilergruppe, die der aktuelle Benutzer besitzt. Vordefinierte relative Bereiche können nur für Empfängerobjektbereiche verwendet werden. Vordefinierte relative Bereiche können nicht für Konfigurationsobjektbereiche verwendet werden. In der folgenden Tabelle sind die vordefinierten relativen Bereiche aufgeführt, die Sie verwenden können.

### Vordefinierte relative Bereiche

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Implizite Bereiche</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Organization</code></p></td>
<td><p>Wenn im Schreibbereich des Rollenempfängers <code>Organization</code> enthalten ist, kann die Rolle Empfängerobjekte in der gesamten Exchange-Organisation erstellen oder ändern.</p>
<p>Wenn im Lesebereich des Rollenempfängers <code>Organization</code> enthalten ist, kann die Rolle Empfängerobjekte in der gesamten Exchange-Organisation anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>Self</code></p></td>
<td><p>Ist im Schreibbereich des Rollenempfängers <code>Self</code> enthalten, kann die Rolle nur die Eigenschaften des Postfachs des aktuellen Benutzers ändern.</p>
<p>Ist im Lesebereich des Rollenempfängers <code>Self</code> enthalten, kann die Rolle nur die Eigenschaften des Postfachs des aktuellen Benutzers anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p>Wenn im Schreibbereich des Rollenempfängers <code>MyDistributionGroups</code> enthalten ist, kann die Rolle Verteilerlistenobjekte im Besitz des aktuellen Benutzers erstellen oder ändern.</p>
<p>Wenn im Lesebereich des Rollenempfängers <code>MyDistributionGroups</code> enthalten ist, kann die Rolle Verteilerlistenobjekte im Besitz des aktuellen Benutzers anzeigen.</p>
<p>Dieser Bereich wird nur für Lese- und Schreibbereiche von Empfängern verwendet.</p></td>
</tr>
</tbody>
</table>


Vordefinierte relative Bereiche werden angewendet, wenn Sie eine neue Verwaltungsrollenzuweisung erstellen. Beim Erstellen der Rollenzuweisung können Sie mithilfe des Cmdlets **New-ManagementRoleAssignment** einen vordefinierten relativen Bereich mit dem Parameter *RecipientRelativeWriteScope* angeben. Wenn die neue Rollenzuweisung erstellt wird, setzt die neue vordefinierte Rolle den impliziten Schreibbereich der Verwaltungsrolle außer Kraft. Beim Erstellen einer Rollenzuweisung mit einem vordefinierten relativen Bereich können Sie keinen benutzerdefinierten Empfängerbereich angeben. Falls erforderlich, können Sie jedoch einen benutzerdefinierten Konfigurationsbereich angeben.

Weitere Informationen zum Hinzufügen einer Verwaltungsrollenzuweisung mit einem vordefinierten relativen Bereich finden Sie unter [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md).

## Benutzerdefinierte Bereiche

Benutzerdefinierte Bereiche sind erforderlich, wenn weder der implizite Schreibbereich noch die vordefinierten relativen Bereiche den Anforderungen Ihres Unternehmens entsprechen. Benutzerdefinierte Bereiche ermöglichen Ihnen eine genaue Definition des Bereichs, auf den Ihre Verwaltungsrolle angewendet werden soll. Dabei kann es sich beispielsweise um eine bestimmte Organisationseinheit, einen bestimmten Empfängertyp oder beides handeln. Möglicherweise möchten Sie auch nur einer Gruppe von Administratoren die Verwaltung einer bestimmten Gruppe von Postfachdatenbanken gestatten.

Genau wie vordefinierte relative Bereiche setzen auch benutzerdefinierte Bereiche die für Verwaltungsrollen definierten impliziten Schreib- und Organisationskonfigurationsbereiche außer Kraft. Der implizite Lesebereich für Verwaltungsrollen wird auch weiterhin angewendet, und der resultierende benutzerdefinierte Bereich darf die Grenzen des impliziten Lesebereichs nicht überschreiten. Sie können die folgenden drei Arten von benutzerdefinierten Bereichen erstellen:

  - **OU-Bereich**   Ein OU-Bereich (Organizational Unit, Organisationseinheit) ist der einfachste benutzerdefinierte Bereich und wird mithilfe des Parameters *RecipientOrganizationalUnitScope* für das Cmdlet **New-ManagementRoleAssignment** erstellt. Wenn beim Zuweisen einer Rolle ein OU-Bereich angegeben wird, kann der Rollenempfänger, dem die Rolle zugewiesen wird, nur Empfängerobjekte innerhalb dieser Organisationseinheit ändern. Weitere Informationen zum Hinzufügen einer Verwaltungsrollenzuweisung mit einem OU-Bereich finden Sie unter [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md).

  - **Filterbasierter Empfängerbereich**   Filterbasierte Empfängerbereiche umfassen bestimmte Empfänger, die ermittelt werden, indem nach dem Empfängertyp oder nach anderen Empfängereigenschaften wie Abteilung, Vorgesetztem, Standort usw. gefiltert wird. Weitere Informationen finden Sie im Abschnitt Filterbasierte Empfängerbereiche.

  - **Konfigurationsbereich**   Konfigurationsbereiche werden anhand von Filtern oder Listen festgelegt. Sie erfassen bestimmte Server anhand von Serverlisten oder filterbaren Eigenschaften, die für Server definiert werden können, z. B. einem Active Directory-Standort oder einer Serverrolle. Konfigurationsbereiche können auch anhand von Datenbankbereichen bestimmte Datenbanken erfassen. Hierfür werden Datenbanklisten oder filterbare Datenbankeigenschaften verwendet. Weitere Informationen finden Sie im Abschnitt Konfigurationsbereiche.

Einfache, umfassende oder komplexe, differenzierte benutzerdefinierte Empfänger- und Konfigurationsbereiche können mit dem Cmdlet **New-ManagementScope** erstellt werden. Wenn Sie einen Empfänger- oder Konfigurationsbereich erstellen, werden nur die Empfänger-, Server- oder Datenbankobjekte zurückgegeben, die dem jeweiligen Bereich entsprechen. Wenn diese Bereiche mithilfe des Cmdlets **New-ManagementRoleAssignment** oder **Set-ManagementRoleAssignment** auf eine Rollenzuweisung angewendet werden, können nur die Objekte, die dem jeweiligen Bereich entsprechen, von den Rollenempfängern geändert werden, denen die Rolle zugewiesen wird. Sie können den Bereichstyp nach dem Erstellen eines benutzerdefinierten Bereichs nicht mehr ändern. Ein Empfängerbereich bleibt stets Empfängerbereich, ein Konfigurationsbereich stets Konfigurationsbereich.

Standardmäßig ermöglicht ein benutzerdefinierter Bereich einem Rollenempfänger den Zugriff auf einen Satz von Objekten, die den von Ihnen definierten Bereichen entsprechen. Der Zugriff für andere Rollenempfänger, denen nicht der gleiche oder ein äquivalenter Bereich zugewiesen wurde, ist jedoch nicht aktiv ausgeschlossen. Jeder benutzerdefinierte Bereich kann auf dieselben Objekte zugreifen, wenn den Listen oder Filtern für diese Bereiche dieselben Objekte entsprechen. Dieses Verhalten ist für bestimmte Objekte möglicherweise nicht wünschenswert, z. B. bei Führungskräften. Für diese Objekte können Sie exklusive Bereiche definieren. Bei exklusiven Bereichen werden Filter oder Listen auf die gleiche Weise wie bei regulären Bereichen verwendet, aber anders als bei regulären Bereichen wird der Zugriff auf Objekte im Bereich allen Benutzern verweigert, die nicht demselben oder einem äquivalenten exklusiven Bereich angehören. Weitere Informationen zu exklusiven Bereichen finden Sie unter [Grundlegendes zu exklusiven Bereichen](understanding-exclusive-scopes-exchange-2013-help.md).

## Filterbasierte Empfängerbereiche

Mit filterbasierten Empfängerbereichen können Sie steuern, welche Empfängerobjekte Rollenempfänger verwalten können. Hierfür wird mindestens eine Eigenschaft eines Empfängerobjekts anhand eines Werts ausgewertet, den Sie in einer Filteranweisung angeben. Empfänger, die in Empfängerbereichen enthalten sind, sind Postfächer, E-Mail-aktivierte Benutzer, Verteilergruppen und E-Mail-Kontakte. Nur die Empfänger, die dem angegebenen Filter entsprechen, können von den Rollenempfängern mit dieser Rollenzuweisung verwaltet werden. Ein Beispiel für eine Filteranweisung ist `{ Name -Eq "David" }`, wobei **Name** die Eigenschaft des Empfängerobjekts ist, die ausgewertet wird, und **David** der Wert, den Sie anhand der Eigenschaft auswerten möchten. Der Vergleichsoperator **-Eq** zeigt an, dass der in der Eigenschaft gespeicherte Wert gleich dem angegebenen Wert sein muss, damit der Filter zu TRUE ausgewertet wird. Wenn der Filter zu TRUE ausgewertet wird, ist der Empfänger im Bereich enthalten.

Filterbasierte Empfängerbereiche werden erstellt, indem der Empfängerfilter angegeben wird, der mit dem Parameter *RecipientRestrictionFilter* des Cmdlets **New-ManagementScope** verwendet werden soll. Standardmäßig werden mit dem Cmdlet **New-ManagementScope** reguläre Bereiche erstellt. Wenn Sie einen exklusiven Bereich erstellen möchten, schließen Sie die Option *Exclusive* des Parameters *RecipientRestrictionFilter* ein.

Wenn Sie einen Empfängereinschränkungsfilter erstellen, wertet Exchange standardmäßig jedes Empfängerobjekt in der Organisation anhand des bereitgestellten Filters aus. Wenn Sie die für den Bereich auszuwertenden Empfänger beschränken möchten, können Sie den Parameter *RecipientRoot* zusammen mit dem Parameter *RecipientRestrictionFilter* verwenden. Im Parameter *RecipientRoot* kann eine Organisationseinheit angegeben werden. Wenn Sie den Parameter *RecipientRoot* verwenden, wertet Exchange nur die in die angegebene Organisationseinheit eingeschlossenen Empfänger anhand des bereitgestellten Filters aus.

Wenn Sie einer Rollenzuweisung einen filterbasierten Empfängerbereich hinzufügen, geben Sie den Namen des Empfängerbereichs im Parameter *CustomRecipientWriteScope* des Cmdlets **New-ManagementRoleAssignment** (beim Erstellen einer neuen Rollenzuweisung) oder des Cmdlets **Set-ManagementRoleAssignment** (beim Aktualisieren einer vorhandenen Rollenzuweisung) an. Jede Rollenzuweisung kann nur einen Empfängerbereich aufweisen, einschließlich vordefinierter relativer Bereiche. Sie können einer Rollenzuweisung, der Sie einen Empfängerbereich hinzugefügt haben, außerdem höchstens einen Konfigurationsbereich hinzufügen.

Weitere Informationen zur Filtersyntax und eine vollständige Liste filterbarer Empfängereigenschaften von Empfängern finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

## Konfigurationsbereiche   

Die folgenden beiden Arten von Konfigurationsbereichen stehen in Exchange 2013 zur Verfügung:

  - **Serverbereiche**   Es gibt zwei Arten von Serverbereichen, und zwar filterbasierte und listenbasierte Serverbereiche. Aspekte der Serverkonfiguration, die verwaltet werden können, wenn ein Serverobjekt in einen Serverbereich eingeschlossen ist, sind Empfangsconnectors, Transportwarteschlangen, Serverzertifikate, virtuelle Verzeichnisse usw.
    
      - **Filterbasierte Serverbereiche**   Mit filterbasierten Serverbereichen können Sie steuern, welche Serverobjekte Rollenempfänger verwalten können. Hierfür wird mindestens eine Eigenschaft eines Serverobjekts anhand eines Werts ausgewertet, den Sie in einer Filteranweisung angeben. Verwenden Sie den Parameter *ServerRestrictionFilter* des Cmdlets **New-ManagementScope**, um einen filterbasierten Serverbereich zu erstellen.
    
      - **Listenbasierte Serverbereiche**   Mit listenbasierten Serverbereichen können Sie steuern, welche Serverobjekte Rollenempfänger verwalten können. Hierfür definieren Sie eine Liste der Server, auf die der Rollenempfänger zugreifen kann. Verwenden Sie den Parameter *ServerList* des Cmdlets **New-ManagementScope**, um einen listenbasierten Serverbereich zu erstellen.

  - **Datenbankbereiche**   Es gibt zwei Arten von Datenbankbereichen, und zwar filterbasierte und listenbasierte Datenbankbereiche. Aspekte der Datenbankkonfiguration, die verwaltet werden können, wenn ein Datenbankobjekt in einen Datenbankbereich eingeschlossen ist, sind Datenbank-Kontingentgrenzwerte, Datenbankwartung, Replikation Öffentlicher Ordner, die Frage, ob eine Datenbank eingebunden ist, usw. Datenbankbereiche können neben der Datenbankkonfiguration auch verwendet werden, um zu steuern, in welchen Datenbanken Empfänger erstellt werden können. Wenn in Ihrer Organisation Server mit einer Version vor Exchange 2010 SP1 vorhanden sind, finden Sie im Abschnitt Datenbankbereiche und frühere Exchange-Versionen weiter unten in diesem Thema zusätzliche Informationen.
    
      - **Filterbasierte Datenbankbereiche**   Mit filterbasierten Datenbankbereichen können Sie steuern, welche Datenbankobjekte Rollenempfänger verwalten können. Hierfür wird mindestens eine Eigenschaft eines Datenbankobjekts anhand eines Werts ausgewertet, den Sie in einer Filteranweisung angeben. Verwenden Sie den Parameter *DatabaseRestrictionFilter* des Cmdlets **New-ManagementScope**, um einen filterbasierten Datenbankbereich zu erstellen.
    
      - **Listenbasierte Datenbankbereiche**   Mit listenbasierten Datenbankbereichen können Sie steuern, welche Datenbankobjekte Rollenempfänger verwalten können. Hierfür definieren Sie eine Liste der Datenbanken, auf die der Rollenempfänger zugreifen kann. Verwenden Sie den Parameter *DatabaseList* des Cmdlets **New-ManagementScope**, um einen listenbasierten Datenbankbereich zu erstellen.

Weitere Informationen zur Filtersyntax und eine vollständige Liste filterbarer Server- und Datenbankeigenschaften finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Sie können Server- und Datenbanklisten definieren, indem Sie jeden Server und jede Datenbank angeben, der/die in den jeweiligen Bereich eingeschlossen werden soll. Sie können mehrere Server oder Datenbanken in den entsprechenden Bereichen angeben, indem Sie die Server- und Datenbanknamen durch Kommas trennen.

Wenn Sie einer Rollenzuweisung einen Server- oder Datenbankkonfigurationsbereich hinzufügen, geben Sie den Namen dieses Bereichs im Parameter *CustomConfigWriteScope* des Cmdlets **New-ManagementRoleAssignment** (beim Erstellen einer neuen Rollenzuweisung) oder des Cmdlets **Set-ManagementRoleAssignment** (beim Aktualisieren einer vorhandenen Rollenzuweisung) an. Jede Rollenzuweisung kann nur einen Konfigurationsbereich aufweisen.

Mit Datenbankbereichen können Sie nicht nur steuern, welche Datenbanken Rollenempfänger verwalten können, sondern auch, in welchen Datenbanken Rollenempfänger Postfächer erstellen können. Dies wird separat davon gesteuert, welche Empfänger ein Rollenempfänger verwalten kann. Wenn ein Rollenempfänger über die Berechtigungen zum Erstellen eines neuen Postfachs, Einrichten der E-Mail-Aktivierung für einen vorhandenen Benutzer oder Verschieben von Postfächern verfügt, können Sie diese Berechtigungen weiter verfeinern, indem Sie mithilfe von Datenbankbereichen steuern, in welcher Datenbank das Postfach erstellt wird oder in welche Datenbank ein Postfach verschoben wird. Wenn Sie steuern möchten, welche Empfänger ein Rollenempfänger verwalten kann, verwenden Sie einen Empfängerbereich, der im Parameter *CustomRecipientWriteScope* des Cmdlets **New-ManagementRoleAssignment** oder **Set-ManagementRoleAssignment** angegeben wird. Wenn Sie steuern möchten, in welchen Datenbanken ein Postfach erstellt werden kann oder in welche Datenbanken es verschoben werden kann, verwenden Sie einen Datenbankbereich, der im Parameter *CustomConfigurationWriteScope* derselben Cmdlets angegeben wird.


> [!NOTE]
> Die automatische Postfachverteilung kann mithilfe von Datenbankbereichen gesteuert werden.



Für bestimmte Funktionen von Exchange müssen möglicherweise Serverbereiche, Datenbankbereiche oder beides verwaltet werden. Wenn für eine Funktion sowohl Server- als auch Datenbankbereiche verwaltet werden müssen, müssen Sie zwei Rollenzuweisungen erstellen und dem Rollenempfänger zuweisen, der über Verwaltungszugriff auf die Funktion verfügen soll. Ordnen Sie eine Rollenzuweisung dem Serverbereich zu und die andere dem Datenbankbereich.

Für einige Cmdlets werden möglicherweise Konfigurationsbereiche verwendet, die nicht sofort offensichtlich sind. Die folgende Tabelle enthält eine Liste von Cmdlets und den Konfigurationsbereichen, mit denen Sie ihre Verwendung steuern können. Für Cmdlets im Empfängerfunktionsbereich können Sie mit Konfigurationsbereichen steuern, in welchen Datenbanken Empfänger erstellt werden können. Sie steuern nicht, welche Empfänger verwaltet werden können. Die Spalte **Erforderliche Bereiche** kann Folgendes enthalten:

  - **Datenbank**   Zum Ausführen des Cmdlets muss der Rollenempfänger eine Rollenzuweisung mit einem Datenbankbereich erhalten, der die zu verwaltende Datenbank einschließt, oder der implizite Konfigurationsschreibbereich der Rolle muss die zu verwaltende Datenbank einschließen.

  - **Server**   Zum Ausführen des Cmdlets muss der Rollenempfänger eine Rollenzuweisung mit einem Serverbereich erhalten, der den zu verwaltenden Server einschließt, oder der implizite Konfigurationsschreibbereich der Rolle muss den zu verwaltenden Server einschließen.

  - **Server oder Datenbank**   Zum Ausführen des Cmdlets muss der Rollenempfänger eine Rollenzuweisung erhalten, in der ein Datenbankbereich die zu verwaltende Datenbank enthält oder in der ein Serverbereich den Server enthält, auf dem sich die Datenbank befindet. Alternativ muss der implizite Konfigurationsschreibbereich der Rolle die zu verwaltende Datenbank einschließen oder den Server enthalten, auf dem sich die Datenbank befindet, und die Rollenzuweisung darf nicht über einen benutzerdefinierten Schreibbereich verfügen.

  - **Server und Datenbank**   Zum Ausführen dieses Cmdlets muss der Rollenempfänger zwei Rollenzuweisungen erhalten. Die erste Rollenzuweisung muss einen Datenbankbereich enthalten, der die zu verwaltende Datenbank einschließt. Die zweite Rollenzuweisung muss einen Serverbereich enthalten, der den Server einschließt, auf dem sich die Datenbank befindet. Für die Rollenzuweisungen können benutzerdefinierte Konfigurationsbereiche definiert sein, oder die Rollenzuweisungen können den impliziten Konfigurationsschreibbereich von der Rolle erben. Damit der implizite Schreibbereich von der Rolle geerbt werden kann, darf die Rollenzuweisung nicht über einen benutzerdefinierten Schreibbereich verfügen.

### Funktionsbereiche und zugehörige Datenbank- und Serverbereiche

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktionsbereich</th>
<th>Cmdlet</th>
<th>Erforderliche Bereiche</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Databases</p></td>
<td><p><strong>Dismount-Database</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Datenbanken</p></td>
<td><p><strong>Mount-Database</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Datenbanken</p></td>
<td><p><strong>Move-DatabasePath</strong></p></td>
<td><p>Server und Datenbank</p></td>
</tr>
<tr class="even">
<td><p>Datenbanken</p></td>
<td><p><strong>Remove-MailboxDatabase</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="odd">
<td><p>Datenbanken</p></td>
<td><p><strong>Set-MailboxDatabase</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Add-DatabaseAvailabilityGroupServer</strong></p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Add-MailboxDatabaseCopy</strong></p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Move-ActiveMailboxDatabase</strong></p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Remove-DatabaseAvailabilityGroupServer</strong></p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Remove-MailboxDatabaseCopy</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="odd">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Resume-MailboxDatabaseCopy</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="even">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Set-MailboxDatabaseCopy</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="odd">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Suspend-MailboxDatabaseCopy</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="even">
<td><p>Hohe Verfügbarkeit</p></td>
<td><p><strong>Update-MailboxDatabaseCopy</strong></p></td>
<td><p>Server oder Datenbank</p></td>
</tr>
<tr class="odd">
<td><p>Empfänger</p></td>
<td><p><strong>Connect-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Empfänger</p></td>
<td><p><strong>Enable-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Empfänger</p></td>
<td><p><strong>New-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Empfänger</p></td>
<td><p><strong>New-MoveRequest</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Problembehandlung</p></td>
<td><p><strong>Test-MapiConnectivity</strong></p></td>
<td><p>Database</p></td>
</tr>
</tbody>
</table>


## Datenbankbereiche und frühere Exchange-Versionen

Datenbankbereiche wurden erstmalig in Microsoft Exchange 2010 Service Pack 1 (SP1) eingeführt und werden in Exchange 2013 weiterhin unterstützt. Exchange-Versionen vor Exchange 2010 SP1 unterstützen lediglich Empfängerbereiche und Serverkonfigurationsbereiche. Wenn Sie einen neuen Datenbankbereich auf einem Server mit Exchange 2010 SP1 oder höher erstellen, wird die folgende Warnung angezeigt:

```PowerShell
WARNING: Database management scopes will only be applied when a user connects to a server running Exchange 2010 SP1 or later. Servers running a version of Exchange prior to Exchange 2010 SP1 won't apply any roles from a role assignment linked to a database scope. Database management scopes also won't be visible to the Get-ManagementScope cmdlet when it's run from a pre-Exchange 2010 SP1 server.
```

Wenn Sie einen Datenbankbereich erstellen, wird er nur auf Benutzer angewendet, die Verbindungen mit Servern mit Exchange 2010 SP1 oder höher herstellen. Auf Benutzer, die Verbindungen mit Servern vor Exchange 2010 SP1 herstellen, werden keine Rollenzuweisungen mit Datenbankbereichen angewendet. Dies bedeutet, dass jegliche Berechtigungen, die von diesen Rollenzuweisungen bereitgestellt werden, Benutzern mit Servern vor Exchange 2010 SP1 bei der Verbindungsherstellung nicht erteilt werden. Datenbankbereiche können von Servern vor Exchange 2010 SP1 nicht erstellt, entfernt, geändert oder angezeigt werden.

Ein Datenbankbereich kann jegliche Datenbanken in der Exchange-Organisation einschließen. Dies umfasst Server mit Exchange Server 2007, Exchange 2010 und Exchange 2013. Hiermit können Sie unabhängig von der Exchange-Version steuern, welche Datenbanken Benutzer verwalten können. Wie bei anderen Datenbankbereichen auch, werden Rollenzuweisungen mit Datenbankbereichen, die Exchange 2007- und Exchange 2010-Datenbanken enthalten, nur dann auf Benutzer angewendet, wenn sie eine Verbindung mit einem Server mit Exchange 2010 SP1 oder höher herstellen.

Benutzer, die eine Verbindung mit einem Server vor Exchange 2010 SP1 herstellen, können Rollenzuweisungen anzeigen und ändern, die Datenbankbereichen zugeordnet sind. Hierzu gehört auch das Ändern des Konfigurationsbereichs einer vorhandenen Rollenzuweisung in einen Serverbereich, wenn er zurzeit einem Datenbankbereich zugeordnet ist. Wenn der Konfigurationsbereich einer Rollenzuweisung jedoch in einen Serverbereich geändert wird und ein Benutzer ihn später wieder in einen Datenbankbereich ändern möchte, oder wenn der Benutzer den Konfigurationsbereich in einen anderen Datenbankbereich ändern möchte, muss der Benutzer beim Vornehmen der Änderung über eine Verbindung mit einem Server mit Exchange 2010 SP1 oder höher verfügen. Benutzer, die über eine Verbindung mit einem Server vor Exchange 2010 SP1 verfügen, können beim Ändern des Konfigurationsbereichs für eine Rollenzuweisung nur Serverbereiche angeben.

