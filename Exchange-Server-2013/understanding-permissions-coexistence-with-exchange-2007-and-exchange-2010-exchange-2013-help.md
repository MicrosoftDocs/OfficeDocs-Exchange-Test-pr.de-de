---
title: 'Grundlegendes zur Koexistenz von Berechtigungen in Exchange 2007 und Exchange 2010: Exchange 2013 Help'
TOCTitle: Grundlegendes zur Koexistenz von Berechtigungen in Exchange 2007 und Exchange 2010
ms:assetid: 28ab1433-23ee-4914-8f21-9a32578792e5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335157(v=EXCHG.150)
ms:contentKeyID: 54915041
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zur Koexistenz von Berechtigungen in Exchange 2007 und Exchange 2010

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Wenn Sie Microsoft Exchange Server 2013 in einer bestehenden Microsoft Exchange Server 2010- oder Microsoft Exchange Server 2007-Organisation installieren, müssen Sie wissen, wie sich Berechtigungen in der neuen Organisation verhalten. Lesen Sie den auf Ihre Organisation zutreffenden Abschnitt.

  - Installieren von Exchange 2013 in einer vorhandenen Exchange 2010-Organisation

  - Installieren von Exchange 2013 in einer vorhandenen Exchange 2010-Organisation

## Installieren von Exchange 2013 in einer vorhandenen Exchange 2010-Organisation

Exchange 2013 verwendet das Berechtigungsmodell der rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) wie Exchange 2010. Wenn Sie Exchange 2013 in einer vorhandenen Exchange 2010-Organisation installieren, werden dieselben Verwaltungsrollengruppen, Verwaltungsrollen und Verwaltungsbereiche auf Exchange 2013- und Exchange 2010-Server und -Empfänger angewendet. Mitglieder von Rollengruppen oder Rollen zugewiesenen Benutzern können alle Exchange 2013- oder Exchange 2013-Server oder Empfänger verwalten, die im Bereich der Rollengruppe oder Rolle enthalten sind. Verwenden Sie in Ihrer Organisation keine Bereiche und sollen die Mitglieder Ihrer bestehenden Rollengruppen Exchange 2010- und Exchange 2013-Server und Empfänger verwalten, sind keine weiteren Aktionen notwendig. Diese Administratoren können Exchange 2013-Server und Empfänger verwalten, die der Organisation hinzugefügt werden. Sollten Sie Informationen zur Funktionsweise von Berechtigungen in Exchange 2010 und Exchange 2013 benötigen, finden Sie diese unter [Berechtigungen](permissions-exchange-2013-help.md).

In der neuen Organisation möchten Sie möglicherweise die Verwaltung von Exchange 2010- und Exchange 2013-Servern und Empfängern trennen. Die Gruppe der für die Verwaltung von Exchange 2010-Servern und Empfängern zuständigen Administratoren dürfen möglicherweise keine Exchange 2013-Server und Empfänger verwalten und umgekehrt. In diesem Fall können Sie mit Verwaltungsbereichen die Server und Empfänger der einzelnen Administratorengruppen definieren, die Verwaltungsrechte erhalten sollen. Nach der Erstellung der gewünschten Bereiche können Sie vorhandene Rollengruppen kopieren, die Administratoren hinzufügen, die Mitglieder der Gruppen sein sollen und anschließend die Bereiche zu diesen Rollengruppen hinzufügen. Abschließend können die Mitglieder der einzelnen Rollengruppen nur die Server und Empfänger verwalten, die ihren jeweiligen Bereichen entsprechen.

Weitere Informationen zu Rollengruppen, Bereichen, dem Kopieren von Rollengruppen und dem Hinzufügen von Bereichen zu Rollengruppen finden Sie unter den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

## Installieren von Exchange 2013 in einer vorhandenen Exchange 2010-Organisation

Exchange 2013 beinhaltet rollenbasierten Zugriffssteuerung (Role Based Access Control (RBAC)), die das auf einem Active Directory-Zugriffsteuerungseintrag (Access Control Entry (ACE)) basierende Autorisierungsmodell von Microsoft Exchange Server 2007 ersetzt. RBAC steht für den in der Verwaltung von Exchange 2013 am häufigsten verwendeten Autorisierungsmechanismus. Dieser Mechanismus umfasst die folgenden Verwaltungsbereiche:

  - Exchange-Verwaltungsshell

  - Exchange-Verwaltungskonsole

  - Exchange-Webdienste

Weitere Informationen dazu, wie die Koexistenz zwischen Exchange 2013 und Exchange 2007 geplant werden kann, finden Sie unter [Aktualisieren von Exchange 2007 auf Exchange 2013](upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md).

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit Berechtigungen gibt? Weitere Informationen finden Sie hier: [Berechtigungen](permissions-exchange-2013-help.md).

## Exchange 2013-Berechtigungen

Das Exchange 2013 RBAC-Berechtigungsmodell besteht aus Verwaltungsrollengruppen, denen eine von mehreren Verwaltungsrollen zugewiesen wurde. Verwaltungsrollen umfassen Berechtigungen, die Administratoren das Ausführen von Aufgaben in der Exchange-Organisation ermöglichen. Administratoren werden als Mitglieder der Rollengruppen hinzugefügt und erhalten sämtliche Berechtigungen der Rollen. Die folgende Tabelle enthält Beispiele für Rollengruppen, den Rollengruppen zugewiesene Rollen sowie eine Beschreibung des Typs von Benutzer, der Mitglied der Rollengruppe sein kann.

### Beispiele für Rollengruppen und Rollen in Exchange 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrollengruppe</th>
<th>Verwaltungsrollen</th>
<th>Mitglieder dieser Rollengruppe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>Im Folgenden sind einige Rollen aufgeführt, die dieser Rollengruppe zugewiesen sind:</p>
<ul>
<li><p>Adresslisten</p></li>
<li><p>Exchange Servers</p></li>
<li><p>Journale</p></li>
<li><p>E-Mail-Empfänger</p></li>
<li><p>Öffentliche Ordner</p></li>
</ul></td>
<td><p>Benutzer, die die gesamte Exchange 2013-Organisation verwalten, sollten Mitglied dieser Rollengruppe sein. Mit einigen Ausnahmen können Mitglieder dieser Rollengruppe praktisch jeden Aspekt der Exchange 2013-Organisation verwalten.</p>
<p>Das zur Vorbereitung von Active Directory für Exchange 2013 verwendete Benutzerkonto ist standardmäßig Mitglied dieser Rollengruppe.</p>
<p>Weitere Informationen zu dieser Rollengruppe und eine umfassende Liste der Rollen, die dieser Rollengruppe zugewiesen sind, finden Sie unter <a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a>.</p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung – nur Leserechte</p></td>
<td><p>Im Folgenden sind die Rollen aufgeführt, die dieser Rollengruppe zugewiesen sind:</p>
<ul>
<li><p>Überwachung</p></li>
<li><p>Schreibgeschützte Konfiguration</p></li>
<li><p>Schreibgeschützte Empfänger</p></li>
</ul></td>
<td><p>Benutzer, die die Konfiguration der gesamten Exchange 2013-Organisation anzeigen, sollten Mitglied dieser Rollengruppe sein. Diese Benutzer müssen in der Lage sein, Informationen zur Serverkonfiguration und zu Empfängern anzuzeigen und Überwachungsfunktionen auszuführen, ohne die Organisations- oder Empfängerkonfiguration ändern zu können.</p>
<p>Weitere Informationen zu dieser Rollengruppe finden Sie unter <a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Empfängerverwaltung</p></td>
<td><p>Im Folgenden sind die Rollen aufgeführt, die dieser Rollengruppe zugewiesen sind:</p>
<ul>
<li><p>Verteilergruppen</p></li>
<li><p>E-Mail-aktivierte Öffentliche Ordner</p></li>
<li><p>Erstellen von E-Mail-Empfängern</p></li>
<li><p>E-Mail-Empfänger</p></li>
<li><p>Nachrichtenverfolgung</p></li>
<li><p>Migration</p></li>
<li><p>Postfächer verschieben</p></li>
<li><p>Empfängerrichtlinien</p></li>
</ul></td>
<td><p>Benutzer, die Empfänger (z. B. Postfächer, Kontakte und Verteilergruppen) in der Exchange 2013-Organisation verwalten, sollten Mitglied dieser Rollengruppe sein. Diese Benutzer können Empfänger erstellen, vorhandene Empfänger ändern oder löschen und Postfächer verschieben.</p>
<p>Weitere Informationen zu dieser Rollengruppe und eine umfassende Liste der Rollen, die dieser Rollengruppe zugewiesen sind, finden Sie unter <a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a>.</p></td>
</tr>
<tr class="even">
<td><p>Server Management</p></td>
<td><p>Im Folgenden sind einige Rollen aufgeführt, die dieser Rollengruppe zugewiesen sind:</p>
<ul>
<li><p>Datenbanken</p></li>
<li><p>Exchange-Connectors</p></li>
<li><p>Exchange Servers</p></li>
<li><p>Empfangsconnectors</p></li>
<li><p>Transportwarteschlangen</p></li>
</ul></td>
<td><p>Benutzer, die die Exchange-Serverkonfiguration (z. B. Empfangsconnectors, Zertifikate, Datenbanken und virtuelle Verzeichnisse) verwalten, sollten Mitglied dieser Rollengruppe sein. Diese Benutzer können die Exchange-Serverkonfiguration ändern, Datenbanken erstellen und Transportwarteschlangen neu starten und bearbeiten.</p>
<p>Weitere Informationen zu dieser Rollengruppe und eine umfassende Liste der Rollen, die dieser Rollengruppe zugewiesen sind, finden Sie unter <a href="server-management-exchange-2013-help.md">Serververwaltung</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Discoveryverwaltung</p></td>
<td><p>Im Folgenden sind die Rollen aufgeführt, die dieser Rollengruppe zugewiesen sind:</p>
<ul>
<li><p>Rechtliche Aufbewahrungspflicht</p></li>
<li><p>Postfachsuche</p></li>
</ul></td>
<td><p>Benutzer, die für juristische Vorgänge Postfächer durchsuchen oder die rechtliche Aufbewahrungspflicht konfigurieren, sollten Mitglied dieser Rollengruppe sein.</p>
<p>Dies ist ein Beispiel für eine Rollengruppe, die Mitglieder enthalten kann, bei denen es sich nicht um Exchange-Administratoren handelt (z. B. Mitarbeiter der Rechtsabteilung). Mitarbeiter der Rechtsabteilung können ihre Aufgaben ohne Eingriffe durch Exchange-Administratoren ausführen.</p>
<p>Weitere Informationen zu dieser Rollengruppe und eine umfassende Liste der Rollen, die dieser Rollengruppe zugewiesen sind, finden Sie unter <a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a>.</p></td>
</tr>
</tbody>
</table>


Diese Tabelle zeigt, dass in Exchange 2013 präzise gesteuert werden kann, welche Berechtigungen Administratoren erteilt werden. In Exchange 2013 sind 12 Rollengruppen verfügbar. Eine umfassende Liste der Rollengruppen und der Berechtigungen, die über diese Gruppen bereitgestellt werden, finden Sie unter [Integrierte Rollengruppen](built-in-role-groups-exchange-2013-help.md).

Da in Exchange 2013 viele Rollengruppen bereitgestellt werden und durch die Erstellung von Rollengruppen mit anderen Rollenkombinationen eine zusätzliche Anpassung möglich ist, ist das Bearbeiten von Zugriffssteuerungslisten für Active Directory-Objekte nicht mehr erforderlich und hat keine Auswirkungen. Zugriffssteuerungslisten werden nicht mehr zum Anwenden von Berechtigungen auf einzelne Administratoren oder Gruppen in Exchange 2013 verwendet. Sämtliche Aufgaben, z. B. die Postfacherstellung durch einen Administrator oder der Benutzerzugriff auf ein Postfach, werden über die rollenbasierte Zugriffssteuerung verwaltet. Die Berechtigung für eine Aufgabe wird über die rollenbasierte Zugriffsteuerung festgelegt, und Exchange führt, sofern zulässig, die Aufgabe im Namen des Benutzers aus. Exchange führt die Aufgabe in der universellen Sicherheitsgruppe "Exchange Trusted Subsystem" aus. Mit einigen Ausnahmen werden der universellen Sicherheitsgruppe "Active Directory Trusted Subsystem" sämtliche Berechtigungen in den Zugriffssteuerungslisten für Objekte in Exchange 2010 gewährt, auf die Exchange zugreifen muss. Dies ist eine grundlegende Änderung der Handhabung von Berechtigungen in Exchange 2007.

Die einem Benutzer in Active Directory erteilten Berechtigungen und die Berechtigungen, die dem Benutzer bei Verwendung der Exchange 2013-Verwaltungstools über die rollenbasierte Zugriffssteuerung erteilt werden, werden separat verwaltet.

Weitere Informationen zur rollenbasierten Zugriffssteuerung finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Exchange 2007-Berechtigungen

Das Exchange 2007-Verwaltungsmodell nutzt Active Directory-Gesamtstrukturen zur Definition von Sicherheitsgrenzen. Innerhalb einer bestimmten Gesamtstruktur gibt es keine Isolierung von Sicherheitsberechtigungen. Besitzer von Gesamtstrukturen und Organisationsadministratoren haben immer Zugriff auf alle Ressourcen in jeder Domäne. In Exchange 2007 müssen Sie möglicherweise Organisations- und Domänenadministratorrechte auf oberster Ebene temporär erteilen.

Exchange 2007 bietet die folgenden vordefinierten Administratorrollen:

  - **Exchange-Organisationsadministrator-Rolle**   Mit dieser Rolle erhält ein Benutzer Berechtigungen zum Steuern aller Aspekte der Exchange 2007-Organisation. Außerdem kann der Administrator, der über diese Rolle verfügt, anderen Exchange-Administratoren Berechtigungen erteilen. Diese Rolle wird dem Konto zugewiesen, mit dem Sie Exchange 2007 installieren.

  - **Rolle "Exchange-Administrator mit Leserechten"**   Mit dieser Rolle erhält ein Benutzer Berechtigungen zur Anzeige von Exchange-Konfigurationen. Ein Administrator, der über diese Rolle verfügt, kann jedoch keine Objekte in der Exchange 2007-Organisation ändern.

  - **Exchange-Empfängeradministrator-Rolle**   Mit dieser Rolle erhält ein Benutzer Berechtigungen zur Verwaltung von E-Mail-Empfängern. Ein Administrator, der über diese Rolle verfügt, kann Exchange-bezogene Elemente für Benutzer, Gruppen, Kontakte und Verteilergruppen ändern.

  - **Exchange-Serveradministrator-Rolle**   Mit dieser Rolle erhält ein Benutzer Berechtigungen zur Verwaltung eines bestimmten Servers. Diese Rolle erteilt jedoch keine Berechtigungen zum Ausführen von Aktionen, die globale Auswirkungen auf die Exchange 2007-Organisation haben.

  - **Rolle "Exchange Öffentlicher Ordner-Administrator"**   Diese Rolle wurde in Exchange 2007 Service Pack 1 hinzugefügt**.** Mit dieser Rolle erhält ein Benutzer Berechtigungen zur Verwaltung Öffentlicher Ordner in der Exchange 2007-Organisation.

Dieses Berechtigungsmodell verwendet universelle Sicherheitsgruppen für alle Rollen, ausgenommen für die Exchange-Serveradministratorrolle. Wenn Sie den Befehl Exchange 2007**Setup /PrepareAD** ausführen, erstellt das Setupprogramm die universellen Sicherheitsgruppen in der Stammdomäne und weist den Gruppen einen gesamtstrukturweiten Bereich zu. Den universellen Sicherheitsgruppen werden Zugriffssteuerungslisten zugewiesen, um Exchange-Objekte in Active Directory zu verwalten.

In Exchange 2007 können Sie Administratoren unterscheiden, indem Sie ihnen verschiedene Rollen zuweisen. Die Berechtigungen werden dem Benutzer oder der universellen Sicherheitsgruppe, deren Mitglied der Benutzer ist, direkt zugewiesen. Alle vom Benutzer ausgeführten Aktionen werden im Kontext des Active Directory-Kontos dieses Benutzers ausgeführt. In der folgenden Tabelle sind die Exchange 2007-Administratorrollen und die Exchange-bezogenen Berechtigungen aufgeführt:

### Exchange 2007-Administratorrollen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Administratorrolle</th>
<th>Mitglieder</th>
<th>Mitglied von</th>
<th>Exchange-Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Organisationsadministrator</p></td>
<td><p>Das Administratorkonto oder das zur Installation des ersten Exchange 2007-Servers verwendete Konto</p></td>
<td><p>Exchange-Empfängeradministrator</p>
<p>Administratoren der lokalen Gruppe von <em>&lt;Servername&gt;</em></p></td>
<td><p>Vollzugriff auf den Microsoft Exchange-Container in Active Directory</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Administrator mit Leserechten</p></td>
<td><p>Exchange-Empfängeradministratoren</p>
<p>Exchange-Serveradministratoren (<em>&lt;Servername</em>&gt;)</p></td>
<td><p>Exchange-Empfängeradministratoren</p>
<p>Exchange-Serveradministratoren</p></td>
<td><p>Lesezugriff auf den Microsoft Exchange-Container in Active Directory</p>
<p>Lesezugriff auf alle Windows-Domänen, die über Exchange-Empfänger verfügen</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Empfängeradministrator</p></td>
<td><p>Exchange-Organisationsadministratoren</p></td>
<td><p>Exchange-Administratoren mit Leserechten</p></td>
<td><p>Vollzugriff auf die Exchange-Eigenschaften für Active Directory-Benutzerobjekte</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Serveradministrator</p></td>
<td><p>Exchange-Organisationsadministratoren</p></td>
<td><p>Exchange-Administratoren mit Leserechten</p>
<p>Administratoren der lokalen Gruppe von <em>&lt;Servername</em>&gt;</p></td>
<td><p>Vollzugriff auf Exchange<em>&lt;Servername</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>Jedes Exchange 2007-Computerkonto</p></td>
<td><p>Exchange-Administratoren mit Leserechten</p></td>
<td><p>Sonderfall</p></td>
</tr>
<tr class="even">
<td><p>Exchange Öffentlicher Ordner-Administrator</p></td>
<td><p>Exchange-Organisationsadministratoren</p></td>
<td><p>Exchange-Administratoren mit Leserechten</p></td>
<td><p>Vollzugriff auf alle Öffentlichen Ordner (erweitertes Recht &quot;Öffentliche Ordner der obersten Ebene erstellen&quot; erteilt)</p></td>
</tr>
</tbody>
</table>


Wenn Sie präzisere Berechtigungszuweisungen erteilen müssen, können Sie die Zugriffssteuerungslisten für einzelne Exchange 2007-Objekte wie Adressen oder Datenbanken ändern. Sie müssen den Benutzer oder die Sicherheitsgruppe, in der der Benutzer Mitglied ist, direkt der Zugriffssteuerungsliste hinzufügen. Dann werden die Aktionen im Kontext des jeweiligen Benutzers ausgeführt.

Weitere Informationen dazu, wie Berechtigungen in Exchange 2007 verwaltet werden können, finden Sie unter [Konfigurieren von Berechtigungen in Exchange Server 2007](http://go.microsoft.com/fwlink/p/?linkid=90671) .

## Berechtigungen bei Koexistenz von Exchange 2013 und Exchange 2007

Da sich die Berechtigungsmodelle von Exchange 2013 und Exchange 2007 unterscheiden, sind die Berechtigungszuweisungen von Exchange 2013 getrennt von den Berechtigungszuweisungen von Exchange 2007. Dies gilt sogar dann, wenn beide Versionen von Exchange in derselben Gesamtstruktur installiert sind. Ohne zusätzliche Konfiguration verfügen Exchange 2013-Administratoren nicht über die benötigten Berechtigungen zum Verwalten von Exchange 2007-basierten Servern, und Exchange 2007-Administratoren verfügen nicht über die erforderlichen Berechtigungen zum Verwalten von Exchange 2013-basierten Servern. Sie sollten die folgenden Fragen berücksichtigen:

  - Möchten Sie Exchange 2013-Administratoren Zugriff auf zu verwaltende Exchange 2007-Server erteilen?

  - Möchten Sie Exchange 2007-Administratoren Zugriff auf zu verwaltende Exchange 2013-Server erteilen?

  - Sollen Exchange 2013-Berechtigungen so angepasst werden, dass sie den Anpassungen in Exchange 2007-Zugriffssteuerungslisten entsprechen?

## Zuweisen von Exchange 2013-Berechtigungen zu Exchange 2007-Administratoren

Wenn Exchange 2007-Administratoren Exchange 2013-Server verwalten sollen, müssen die Exchange 2007-Administratoren als Mitglieder zu einer oder mehreren Exchange 2013-Rollengruppen hinzugefügt werden. Sie können Benutzer oder universelle Sicherheitsgruppen zu Rollengruppen hinzufügen. Die Berechtigungen der Rollengruppen werden anschließend auf die Benutzer oder universellen Sicherheitsgruppen angewandt, die als Mitglieder hinzugefügt werden.


> [!IMPORTANT]
> Bei Verwendung domänenlokaler oder globaler Active Directory-Sicherheitsgruppen müssen diese in universelle Sicherheitsgruppen geändert werden, um als Mitglieder einer Exchange 2013-Rollengruppe hinzugefügt werden zu können. Exchange 2013 unterstützt ausschließlich universelle Sicherheitsgruppen.



Die folgende Tabelle beschreibt eine Zuordnung zwischen Exchange 2007-Administratorrollen und Exchange 2013-Rollengruppen.

### Exchange 2007-Administratorrollen und Exchange 2010-Rollengruppen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange 2007-Administratorrolle</th>
<th>Exchange 2013-Rollengruppe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Organisationsadministrator</p></td>
<td><p>Organisationsverwaltung</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Empfängeradministrator</p></td>
<td><p>Empfängerverwaltung</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Serveradministrator</p></td>
<td><p>Server Management</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Administrator mit Leserechten</p></td>
<td><p>Organisationsverwaltung – nur Leserechte</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>Keine entsprechende Rollengruppe in Exchange 2013</p>
<p>(Weitere Informationen zum Erstellen benutzerdefinierter Rollengruppen finden Sie unter <a href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</a>.)</p></td>
</tr>
<tr class="even">
<td><p>Exchange Öffentlicher Ordner-Administrator</p></td>
<td><p>Verwaltung Öffentlicher Ordner</p></td>
</tr>
</tbody>
</table>


Wenn sämtliche Exchange 2007-Administratoren Mitglied einer der Exchange 2007-Verwaltungsrollen sind, können Sie die Mitglieder der einzelnen Verwaltungsgruppen zu den entsprechenden Exchange 2013-Rollengruppen hinzufügen. Wenn Sie beispielsweise allen Exchange 2007-Organisationsadministratoren Vollzugriff auf Exchange 2013-Objekte erteilen möchten, fügen Sie die universelle Sicherheitsgruppe "Exchange Organization Administrators" zur Organisationsverwaltung-Rollengruppe hinzu.

Weitere Informationen zum Hinzufügen von Benutzern und universellen Sicherheitsgruppen zu Rollengruppen finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Wenn Sie Zugriffssteuerungslisten für Exchange 2007-Objekte ändern, um die Zuweisung von Berechtigungen für Exchange 2007-Administratoren präziser steuern zu können, und diesen Administratoren ähnliche Berechtigungen für Exchange 2013-Server zugewiesen werden sollen, führen Sie die folgenden Schritte aus:

1.  Überprüfen Sie die Anpassung der Zugriffssteuerungslisten für die Exchange 2007-Objekte, und ermitteln Sie die Administratoren, denen Berechtigungen für jedes Objekt erteilt wurden.

2.  Kategorisieren Sie jedes Exchange 2007-Objekt. Bestimmen Sie beispielsweise, ob das Objekt eine Datenbank, ein Server oder ein Empfängerobjekt ist.

3.  Ordnen Sie die Objekte der entsprechenden Exchange 2013-Rollengruppe zu. Eine Liste mit integrierten Rollengruppen finden Sie unter [Integrierte Rollengruppen](built-in-role-groups-exchange-2013-help.md).

4.  Fügen Sie die universellen Sicherheitsgruppen oder Benutzer für die einzelnen Objektarten zu den entsprechenden Exchange 2013-Rollengruppen hinzu. Weitere Informationen zum Hinzufügen von Benutzern und universellen Sicherheitsgruppen zu Rollengruppen finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Nachdem Sie diese Schritte abgeschlossen haben, sind die Exchange 2007-Administratoren Mitglieder bestimmter Rollengruppen, die den entsprechenden Exchange 2013-Objekten zugewiesen werden. Die Exchange 2007-Administratoren können zum Verwalten der Exchange 2013-Server und -Empfänger die Exchange 2013-Verwaltungstools verwenden.


> [!IMPORTANT]
> Im Allgemeinen müssen Exchange 2007-Server und -Empfänger über die Exchange 2007-Verwaltungstools, Exchange 2013-Server und -Empfänger über die Exchange 2013-Verwaltungstools verwaltet werden.



Wenn die integrierten Rollengruppen nicht über die spezifischen Berechtigungen verfügen, die einigen Administratoren zugewiesen werden sollen, können Sie benutzerdefinierte Rollengruppen erstellen. Beim Erstellen einer benutzerdefinierten Rollengruppe können Sie auswählen, welche Rollen dieser Gruppe zugewiesen werden sollen. So können Sie die spezifischen Funktionen definieren, die von den Mitgliedern der Rollengruppe verwaltet werden sollen. Wenn Administratoren z. B. ausschließlich Verteilergruppen verwalten sollen, können Sie eine benutzerdefinierte Rollengruppe erstellen und lediglich die Rolle "Verteilergruppen" auswählen. Anschließend können Mitglieder der benutzerdefinierten Rollengruppe nur Verteilergruppen verwalten. Weitere Informationen zum Erstellen benutzerdefinierter Rollengruppen finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

Wenn Sie für bestimmte Exchange 2007-Objekte spezifische Berechtigungen zugewiesen haben, sodass Administratoren z. B. lediglich zur Verwaltung bestimmter Datenbanken berechtigt sind, und Sie dieselbe Konfiguration auf Ihre Exchange 2013-Server anwenden möchten, finden Sie unter "Erneutes Erstellen der Anpassung einer Exchange 2007-Zugriffssteuerungsliste mithilfe von Verwaltungsbereichen in Exchange 2013" später in diesem Thema weitere Informationen.

## Zuweisen von Exchange 2007-Berechtigungen zu Exchange 2013-Administratoren

Wenn Sie möchten, dass Exchange 2013-Administratoren Exchange 2007-Server verwalten, müssen Sie Exchange 2013-Administratoren den universellen Sicherheitsgruppen oder der Sicherheitsgruppe, die der bestimmten Exchange 2007-Administratorrolle entspricht, hinzufügen. Alternativ können Sie die Administratoren den geeigneten Zugriffssteuerungslisten hinzufügen, wenn benutzerdefinierte Einstellungen der Zugriffssteuerungslisten vorhanden sind. Rollengruppen sind universelle Sicherheitsgruppen, also können Rollengruppen direkt zu universellen Sicherheitsgruppen der Exchange 2007-Administratorrolle hinzugefügt werden.

Anschließend sind die Exchange 2013-Administratoren Mitglieder der jeweiligen Exchange 2007-Administratorrolle oder -Rollen. Die Exchange 2013-Administratoren können zum Verwalten der Exchange 2007-Server und -Empfänger die Exchange 2007-Verwaltungstools verwenden.

## Erneutes Erstellen der Anpassung einer Exchange 2007-Zugriffssteuerungsliste mithilfe von Verwaltungsbereichen in Exchange 2013

Wenn Sie in Exchange 2007 einschränken möchten, welche Benutzer einen bestimmten Postfachspeicher oder bestimmte Benutzer verwalten können bzw. welche Benutzer steuern können, in welchem Postfachspeicher Postfächer erstellt werden, müssen die Zugriffssteuerungslisten für die entsprechenden Objekte geändert werden. Exchange 2013 bietet dieselben Funktionen, jedoch ohne das erforderliche Ändern von Zugriffssteuerungslisten. Stattdessen werden Verwaltungsbereiche verwendet, eine Komponente der rollenbasierten Zugriffssteuerung.

Verwaltungsbereiche stellen integrierte und benutzerdefinierte Bereiche zum Definieren der Objekte bereit, die von Administratoren verwaltet werden können. Durch das Anwenden von Verwaltungsbereichen können Sie definieren, welche Empfänger verwaltet werden können, in welchen Postfachdatenbanken Postfächer erstellt werden können und welche Empfänger oder Server ausschließlich von einer kleinen Gruppe von Administratoren verwaltet werden können.

Sie können die folgenden Arten von Verwaltungsbereichen erstellen:

  - **Vordefinierte relative Bereiche**   Vordefinierte relative Bereiche sind in Exchange 2013 enthalten. Sie können steuern, welche Informationen ein Benutzer anzeigen und ändern kann. Mithilfe von vordefinierten relativen Bereichen lässt sich z. B. steuern, ob Benutzer nur Informationen zu sich selbst oder zur gesamten Organisation anzeigen können.

  - **Empfängerbereiche**   Empfängerbereiche steuern, welche Empfänger ein Administrator erstellen, ändern oder löschen kann. Diese Auswahl kann auf einer Organisationseinheit oder einem Empfängerfilter basieren (oder beides). Empfängerfilter geben die Kriterien an, mit denen ein Empfänger übereinstimmen muss, um in den Bereich aufgenommen zu werden. Sie können z. B. einen filterbasierten Empfängerbereich mit allen Benutzern an einem bestimmten Standort oder in einer bestimmten Abteilung erstellen. Organisationseinheiten und Empfängerfilter können sogar kombiniert werden, um nur solche Benutzer zu berücksichtigen, die einer bestimmten Organisationseinheit zugehören und einem bestimmten Vorgesetzten berichten.

  - **Serverbereiche**   Serverbereiche steuern, welche Server ein Administrator verwalten kann. Sie können entweder Serverlisten oder Serverfilter angeben. Bei Serverlisten definieren Sie eine statische Liste mit Servern, die verwaltet werden können. Die Funktionsweise von Serverfiltern ist mit der Funktionsweise von Empfängerfiltern identisch: Sie geben Kriterien an, die erfüllt werden müssen. Sie können beispielsweise einen Serverbereich für alle Server innerhalb eines bestimmten Active Directory-Standorts erstellen.

  - **Datenbankbereiche**   Datenbankbereiche steuern, welche Datenbanken ein Administrator verwalten kann. Über diese Bereiche kann zudem gesteuert werden, in welchen Datenbanken Postfächer erstellt bzw. in welche Datenbanken Postfächer verschoben werden können. Wie Serverbereiche können diese Bereiche als Listen oder als Filter definiert werden. Beispielsweise können Sie eine Liste oder einen Filter erstellen, um Administratoren das Erstellen oder Verschieben von Postfächern in bestimmten Postfachdatenbanken zu ermöglichen, die von einer bestimmten Niederlassung verwaltet werden.

  - **Exklusive Bereiche**   Empfänger-, Server- und Datenbankbereiche können auch als exklusive Bereiche erstellt werden. Exklusive Bereiche funktionieren auf dieselbe Weise wie Zugriffssteuerungseinträge zum Verweigern des Zugriffs in Zugriffssteuerungslisten. Bei Übereinstimmung eines Objekts mit einem exklusiven Bereich können nur einem exklusiven Bereich zugeordnete Administratoren das Objekt verwalten. Dies trifft auch zu, wenn ein anderer, nicht exklusiver Bereich ebenfalls mit diesem Objekt übereinstimmt. Dies ist besonders bei Postfächern von Führungskräften nützlich, deren Verwaltung nur einigen wenigen Personen erlaubt sein sollte. Selbst wenn ein anderer, normaler Empfängerbereich das Postfach der Führungskraft enthält, können die Administratoren des umfangreicheren normalen Empfängerbereichs das Postfach der Führungskraft nur dann verwalten, wenn sie auch dem exklusiven Bereich zugewiesen sind.

Verwaltungsbereiche werden für Verwaltungsrollen, Verwaltungsrollenzuweisungen und Verwaltungsrollengruppen verwendet, um zu steuern, welche Benutzer welche Objekte wie verwalten können. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu exklusiven Bereichen](understanding-exclusive-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md)

Um dasselbe Berechtigungsmodell in Exchange 2013 unter Verwendung von Verwaltungsbereichen zu erstellen, die Sie möglicherweise mithilfe von angepassten Zugriffssteuerungslisten definiert haben, müssen Sie die angepassten Zugriffssteuerungslisten überprüfen und Verwaltungsbereiche erstellen, deren Berechtigungen den Berechtigungen dieser Listen entsprechen. Sie können die filterbaren Eigenschaften für Empfänger-, Server- und Datenbankobjekte verwenden, wenn Sie Verwaltungsbereiche erstellen möchten, die die Objekte enthalten, für die der Zugriff über die einzelnen Verwaltungsbereiche gesteuert werden soll. Weitere Informationen zu den Eigenschaften, die mit Verwaltungsbereichsfiltern verwendet werden können, finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).

Weitere Informationen zum Erstellen von Verwaltungsbereichen finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

