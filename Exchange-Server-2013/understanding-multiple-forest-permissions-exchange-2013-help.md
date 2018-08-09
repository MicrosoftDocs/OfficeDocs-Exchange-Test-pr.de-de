---
title: 'Grundlegendes zu Berechtig. für mehrere Gesamtstrukturen: Exchange 2013-Hilfe'
TOCTitle: Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen
ms:assetid: 8241033f-e201-4799-b17c-4f120c6e6445
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298099(v=EXCHG.150)
ms:contentKeyID: 50476133
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Viele Organisationen stellen mehrere Gesamtstrukturen bereit, um Sicherheitsgrenzen innerhalb ihrer Organisationen zu erstellen. Das Verwenden mehrerer Gesamtstrukturen unterstützt Administratoren beim Definieren dieser Sicherheitsgrenzen, um die jeweiligen Sicherheitsanforderungen zu erfüllen – ob es sich darum handelt, den Zugriff auf eine Ressource auf möglichst wenige Personen zu beschränken, oder um Abteilungen innerhalb einer Organisation zu segmentieren.

Microsoft Exchange Server 2013 unterstützt zwei Arten von Topologien mit mehreren Gesamtstrukturen:

  - **Gesamtstrukturübergreifend**   Gesamtstrukturübergreifende Topologien können mehrere Gesamtstrukturen aufweisen, die jeweils über eine eigene Installation von Exchange verfügen.

  - **Ressourcengesamtstruktur**   Topologien mit Ressourcengesamtstrukturen weisen eine Exchange-Gesamtstruktur und mindestens eine Kontogesamtstruktur auf.

In diesem Thema wird die Gesamtstruktur, die die universellen Sicherheitsgruppen (Universal Security Groups, USGs) und Benutzer außerhalb der Gesamtstruktur umfasst, in der Exchange 2013 installiert ist, als fremde Gesamtstruktur bezeichnet – unabhängig davon, ob es sich um eine Konto- oder eine Ressourcengesamtstruktur handelt.

Die Konfiguration von Berechtigungen in einer Topologie mit mehreren Gesamtstrukturen basiert auf der ordnungsgemäßen Konfiguration von Gesamtstrukturvertrauensstellungen und der GAL-Synchronisierung (Global Address List, globale Adressliste) zur Erstellung verknüpfter Postfächer. Die Exchange 2013-Gesamtstruktur muss der fremden Gesamtstruktur vertrauen, welche die verknüpften Rollengruppen zugeordneten USGs und die verknüpften Postfächern zugeordneten Benutzer enthält.

Exchange 2013 verwendet ein Berechtigungsmodell für die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC). Die Verwaltungsrollengruppen, denen Administratoren angehören, sowie die Zuweisungsrichtlinien für Verwaltungsrollen, die den Endbenutzer zugewiesen sind, bestimmen, welche Aufgaben Administratoren und Endbenutzer ausführen können. Um Berechtigungen für mehrere Gesamtstrukturen verstehen zu können, müssen Sie mit dem RBAC-Modell vertraut sein. Weitere Informationen zu der rollenbasierten Zugriffssteuerung, Rollengruppen und Rollenzuweisungsrichtlinien finden Sie unter den folgenden Themen:

  - [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md)

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit der Berechtigungsverwaltung gibt? Weitere Informationen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

**Inhalt**

Berechtigungen in einer Topologie mit mehreren Gesamtstrukturen

Grenzübergreifende Berechtigungen

Konfigurieren von grenzübergreifenden Berechtigungen

## Berechtigungen in einer Topologie mit mehreren Gesamtstrukturen

Die rollenbasierte Zugriffssteuerung weist allen Exchange-Objekten innerhalb einer einzelnen Gesamtstruktur Berechtigungen zu und wird in jeder Gesamtstruktur unabhängig von allen anderen Gesamtstrukturen konfiguriert. Wenn Sie eine Rollengruppe in einer Gesamtstruktur erstellen, ist diese Rollengruppe in keiner anderen Gesamtstruktur vorhanden. Die Berechtigungen, die dieser Rollengruppe erteilt werden, gelten nur für die Gesamtstruktur, in der die Rollengruppe erstellt wurde. Beispielsweise kann ein Mitglied einer Rollengruppe, die Berechtigungen zum Erstellen eines Postfachs erteilt, Postfächer nur in der Gesamtstruktur erstellen, die diese Rollengruppe enthält.

Wenn Sie über mehrere Exchange-Gesamtstrukturen verfügen und identische Berechtigungen für alle Gesamtstrukturen konfigurieren möchten, müssen Sie die gleiche Konfiguration explizit auf jede Gesamtstruktur anwenden. Wenn Sie z. B. über zwei Exchange 2013-Gesamtstrukturen verfügen und eine Rollengruppe für die Verwaltung der Vorschrifteneinhaltung erstellen möchten, mit der die Berechtigungen für die Rechtsabteilung verwaltet werden sollen, müssen Sie folgendermaßen vorgehen:

  - Erstellen Sie in jeder Gesamtstruktur eine Rollengruppe namens "Verwaltung der Vorschrifteneinhaltung". Wenn sich Ihre Administratoren in einer separaten Gesamtstruktur befinden, die für beide Exchange-Gesamtstrukturen fremd ist, erstellen Sie beide Rollengruppen als verknüpfte Rollengruppen. Weitere Informationen zu Rollengruppen finden Sie im Abschnitt Grenzübergreifende Berechtigungen.

  - Erstellen Sie in jeder Gesamtstruktur Rollenzuweisungen zwischen den neuen Rollengruppen und den Rollen, die Sie verwenden möchten.

  - Optional können Sie den neuen Rollenzuweisungen Verwaltungsbereiche hinzufügen, die die Server- und Empfängerobjekte innerhalb jeder Gesamtstruktur umfassen.

  - Wenn Sie die Rollengruppen als verknüpfte Rollengruppen erstellt haben, müssen Sie der verknüpften universellen Sicherheitsgruppe in der fremden Gesamtstruktur Mitglieder hinzufügen.

Folgende Abbildung zeigt, wie die in Exchange 2013-Gesamtstrukturen konfigurierten Rollengruppen an ihre jeweilige Gesamtstruktur gebunden sind. Die Rollengruppe "Organisationsverwaltung" in der Exchange 2013-Gesamtstruktur A erteilt Berechtigungen ausschließlich zum Verwalten der Postfächer und Server in dieser Gesamtstruktur. Ebenso erteilen die Rollengruppen in der Exchange 2013-Gesamtstruktur B Berechtigungen nur für die Postfächer und Server innerhalb dieser Gesamtstruktur.

Die Abbildung zeigt ferner, dass die benutzerdefinierte Rollengruppe A in jeder Gesamtstruktur erstellt wird. Selbst wenn sie mit demselben Namen erstellt werden, handelt es sich bei jeder Rollengruppe um eine eigene Entität. Tatsächlich können jeder Rollengruppe (wie die Abbildung zeigt) in der jeweiligen Gesamtstruktur verschiedene Verwaltungsrollen zugewiesen werden. Der benutzerdefinierten Rollengruppe A in der Exchange 2013-Gesamtstruktur A sind die Rollen "Postfachsuche" und "Nachrichtenverfolgung" zugewiesen, während der benutzerdefinierten Rollengruppe A in der Exchange 2013-Gesamtstruktur B die Rollen "Postfachsuche" und "Aufbewahrungsmanagement" zugewiesen sind.

Schließlich sind Verwaltungsbereiche in jeder Gesamtstruktur ebenfalls an die Gesamtstruktur gebunden. Serverbereiche, die in einer Gesamtstruktur erstellt werden, können nur Server umfassen, die Mitglied dieser Gesamtstruktur sind. Der Serverbereich A kann nur Server innerhalb der Exchange 2013-Gesamtstruktur A enthalten, während der Serverbereich B nur Server innerhalb der Exchange 2013-Gesamtstruktur B enthalten kann. Ebenso kann der Empfängerbereich in der Exchange 2013-Gesamtstruktur B nur Postfächer enthalten, die sich innerhalb der Exchange 2013-Gesamtstruktur B befinden.

**Rollenbasierte Zugriffssteuerung und Gesamtstrukturbereichsgrenze – Beziehung**

![RBAC und Gesamtstruktur-Grenzbereich – Beziehungen](images/Dd298099.220da7c3-cbb8-42ac-9d58-084d996bf837(EXCHG.150).gif "RBAC und Gesamtstruktur-Grenzbereich – Beziehungen")

## Grenzübergreifende Berechtigungen

Mit den durch die rollenbasierte Zugriffssteuerung erteilten Berechtigungen können Benutzer Exchange-Objekte nur innerhalb einer bestimmten Gesamtstruktur anzeigen oder ändern. Sie können jedoch Benutzern, die sich außerhalb einer Gesamtstruktur befinden, Berechtigungen zum Anzeigen und Ändern von Exchange-Objekten in dieser Gesamtstruktur erteilen. Durch Verwendung von grenzübergreifenden Berechtigungen können Sie Exchange-Verwaltungskonten in einer einzigen Gesamtstruktur zentralisieren und müssen diese nicht in jeder einzelnen Gesamtstruktur zur Ausführung von Aufgaben authentifizieren.


> [!NOTE]
> Die Berechtigungen, die einem Benutzer außerhalb einer Exchange-Gesamtstruktur erteilt werden, gelten weiterhin nur für diese bestimmte Exchange-Gesamtstruktur. Wenn beispielsweise ein Benutzer in einer fremden Gesamtstruktur Mitglied der verknüpften Rollengruppe "Organisationsverwaltung" ist, die sich in Gesamtstruktur&nbsp;A befindet, kann dieser Benutzer nur diejenigen Exchange-Objekte verwalten, die in der Gesamtstruktur&nbsp;A enthalten sind. Ein Benutzer muss in jeder Exchange-Gesamtstruktur als Mitglied von verknüpften Rollengruppen festgelegt werden, damit ihm Berechtigungen für die Verwaltung jeder Gesamtstruktur erteilt werden können.



Mit grenzübergreifenden Berechtigungen können Sie Rollenzuweisungsrichtlinien auf die Postfächer von Benutzern anwenden, die über Postfächer in einer Exchange-Gesamtstruktur verfügen, deren Benutzerkonten sich jedoch in einer Kontogesamtstruktur befinden. Exchange 2013 unterstützt grenzübergreifende Berechtigungen durch Verwendung von verknüpften Rollengruppen und verknüpften Postfächern. Diese Konzepte werden in den folgenden Abschnitten erläutert.

## Administratorberechtigungen

Administrative Berechtigungen werden mithilfe von verknüpften Rollengruppen und verknüpften Postfächern gesamtstrukturübergreifend gewährt.

Eine verknüpfte Rollengruppe wird in der Exchange 2013-Organisation erstellt und über die Grenze der Gesamtstruktur hinweg mit einer universellen Sicherheitsgruppe in der fremden Gesamtstruktur verknüpft. Folgende universelle Sicherheitsgruppen (USG) können mit einer verknüpften Rollengruppe verknüpft werden:

  - Eine dedizierte USG zur Verwendung mit der verknüpften Rollengruppe

  - Eine USG, die über verknüpfte Rollengruppen in mehreren Exchange 2013-Gesamtstrukturen verknüpft ist

  - Eine Rollengruppen-USG in einer anderen Exchange 2013-Gesamtstruktur

  - Eine USG, die einer Exchange Server 2007-Verwaltungsrolle oder einer Exchange 2010-Rollengruppe zugeordnet ist

Die USG, mit der eine verknüpfte Rollengruppe verknüpft ist, muss sich in einer anderen Gesamtstruktur befinden. Sie können eine verknüpfte Rollengruppe nicht mit einer universellen Sicherheitsgruppe in derselben Gesamtstruktur verknüpfen.

Die folgende Abbildung zeigt, dass USGs in einer Kontogesamtstruktur Rollengruppen in mehreren Exchange 2013-Ressourcengesamtstrukturen zugeordnet werden können. Die Mitglieder der universellen Sicherheitsgruppen in den Kontogesamtstrukturen werden über die USGs zu Mitgliedern der Rollengruppen.

**Verknüpfte Rollengruppen, die USGs in einer separaten Gesamtstruktur zugeordnet sind**

![Verknüpfte Rollengruppe und universelle Sicherheitsgruppe – Beziehungen](images/Dd298099.23f245e8-b80f-4082-8628-ee6701259be6(EXCHG.150).gif "Verknüpfte Rollengruppe und universelle Sicherheitsgruppe – Beziehungen")

Wenn Sie eine verknüpfte Rollengruppe erstellen, können Sie dieser Rollengruppe in der Exchange 2013-Gesamtstruktur Rollen zuweisen. Die Zuweisungen zwischen den Rollen und der verknüpften Rollengruppe können bei Bedarf Verwaltungsbereiche umfassen. Diese Bereiche sind auf die Gesamtstruktur beschränkt, in der die verknüpfte Rollengruppe erstellt wurde.

Die Mitgliedschaft in der verknüpften Rollengruppe wird durch das Hinzufügen und Entfernen von Mitgliedern zu und aus der USG in der fremden Gesamtstruktur verwaltet. Wenn Sie dieser USG Mitglieder hinzufügen, werden diesen die Berechtigungen erteilt, die der verknüpften Rollengruppe in der Exchange 2013-Gesamtstruktur zugewiesen sind. Wenn Sie mehrere verknüpfte Rollengruppen mit der gleichen USG verknüpft haben, werden den Mitgliedern dieser USG die Berechtigungen erteilt, die jeder verknüpften Rollengruppe in jeder Exchange 2013-Gesamtstruktur zugewiesen sind.

Sie können die Mitgliedschaft in einer verknüpften Rollengruppe nicht in der Exchange 2013-Gesamtstruktur verwalten.

Eine zweite Methode zum Zuweisen administrativer Berechtigungen über Gesamtstrukturgrenzen hinweg stellen verknüpfte Postfächer dar. Damit Benutzer in einer Kontogesamtstruktur eine Exchange 2013-Bereitstellung in einer getrennten Exchange 2013-Ressourcengesamtstruktur nutzen können, müssen Sie ein verknüpftes Postfach für jeden Benutzer konfigurieren. Verknüpfte Postfächer können Rollengruppen in der Exchange 2013-Gesamtstruktur als Mitglieder hinzugefügt werden. Wenn ein verknüpftes Postfach Mitglied einer Rollengruppe wird, werden diesem Postfach und damit auch dem Benutzer in der Kontogesamtstruktur, dem dieses Postfach zugewiesen ist, die von der Rollengruppe bereitgestellten Berechtigungen erteilt.

Die folgende Abbildung zeigt die Beziehung zwischen Benutzern in einer Kontogesamtstruktur, den diesen Benutzern zugeordneten Postfächern und den Rollengruppen, in denen sie Mitglied sind.

**Benutzer in einer Kontogesamtstruktur, die verknüpften Postfächern zugeordnet sind, die Mitglieder von Rollengruppen sind**

![Rollengruppe und verknüpftes Postfach – Beziehungen](images/Dd298099.e59242f6-5c63-4114-90f7-6b6c2478570c(EXCHG.150).gif "Rollengruppe und verknüpftes Postfach – Beziehungen")

Verknüpfte Rollengruppen und verknüpfte Postfächer haben in Bezug auf die gesamtstrukturübergreifende Zuweisung administrativer Berechtigungen Vorteile und Nachteile. In der folgenden Tabelle werden einige davon beschrieben.

### Vor- und Nachteile verknüpfter Rollengruppen und verknüpfter Postfächer

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Verknüpfte Rollengruppen oder verknüpfte Postfächer</th>
<th>Vorteil</th>
<th>Nachteil</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verknüpfte Rollengruppen</p></td>
<td><p>Sie können mehrere verknüpfte Rollengruppen aus mehreren Exchange 2013-Gesamtstrukturen einer einzigen USG in einer Kontogesamtstruktur oder in einer anderen Exchange-Ressourcengesamtstruktur zuordnen. Auf diese Weise können Sie komplexe Exchange-Gesamtstrukturtopologien mithilfe einer geringen Anzahl von universellen Sicherheitsgruppen in einer einzigen Gesamtstruktur verwalten.</p></td>
<td><p>Eine herkömmliche Rollengruppe kann nicht in eine verknüpfte Rollengruppe geändert werden. Sie müssen verknüpfte Rollengruppen manuell erstellen, um jede herkömmliche Rollengruppe zu ersetzen, deren Berechtigungen Sie gesamtstrukturübergreifend erteilen möchten. Weitere Informationen finden Sie unter Konfigurieren von grenzübergreifenden Berechtigungen.</p></td>
</tr>
<tr class="even">
<td><p>Verknüpfte Postfächer</p></td>
<td><p>Mit verknüpften Postfächern können Sie die vorhandenen Rollengruppen innerhalb der Exchange-Gesamtstruktur verwenden. Verknüpfte Postfächer werden den vorhandenen Rollengruppen genauso wie normale Postfächer, universelle Sicherheitsgruppen und Benutzer in der gleichen Exchange-Gesamtstruktur als Mitglieder hinzugefügt.</p></td>
<td><p>Wenn Sie zum Erteilen von Berechtigungen in mehreren Exchange 2013-Gesamtstrukturen verknüpfte Postfächer verwenden, die mit einem einzigen Benutzer in einer Kontogesamtstruktur verknüpft sind, müssen Sie die Rollengruppenmitgliedschaft in jeder Exchange 2013-Gesamtstruktur ändern, wenn Sie die Berechtigungen für diesen Benutzer ändern möchten.</p></td>
</tr>
</tbody>
</table>


Es empfiehlt sich, verknüpfte Rollengruppen zum Erteilen von Berechtigungen über Gesamtstrukturgrenzen hinweg zu verwenden, wenn Sie planen, mehrere Exchange-Ressourcengesamtstrukturen einzurichten.

## Endbenutzerberechtigungen

Endbenutzerberechtigungen werden einzelnen Postfächern mithilfe von Rollenzuweisungsrichtlinien zugewiesen. Wenn Exchange 2013 in einer Ressourcengesamtstruktur installiert ist, werden verknüpfte Postfächer in der Ressourcengesamtstruktur erstellt und Benutzerkonten in der Kontogesamtstruktur zugeordnet.

Wenn Sie ein verknüpftes Postfach erstellen, wird es wie ein herkömmliches Postfach einer standardmäßigen Rollenzuweisungsrichtlinie zugeordnet. Die Rollenzuweisungsrichtlinie legt fest, welche Endbenutzerberechtigungen dem Postfach erteilt werden. Diese Berechtigungen ermöglichen den Benutzern das Anzeigen und Ändern von Einstellungen in Bezug auf die folgenden und weitere Funktionen:

  - Profilinformationen für Endbenutzer

  - Endbenutzer-Voicemail

  - Endbenutzermitgliedschaft in Verteilergruppen und Besitz

Wenn eine Rollenzuweisungsrichtlinie einem verknüpften Postfach zugewiesen wird, erhält der Benutzer in der Kontogesamtstruktur, der dem verknüpften Postfach zugeordnet ist, Berechtigungen zum Verwalten der Funktionen, die diesem Benutzer zur Verfügung stehen. Die Berechtigungen gelten nur für die Ressourcen in der Exchange-Gesamtstruktur, in der sich das verknüpfte Postfach befindet. Die folgende Abbildung zeigt die Beziehung zwischen dem Endbenutzer in der Kontogesamtstruktur, dem zugeordneten verknüpften Postfach und der Rollenzuweisungsrichtlinie, die dem verknüpften Postfach zugewiesen ist. Zusätzlich zu einer Rollenzuweisungsrichtlinie kann ein verknüpftes Postfach, das einem administrativen Benutzer in der Kontogesamtstruktur zugeordnet ist, mit mehreren Rollengruppen verknüpft werden.

**Benutzer in einer Kontogesamtstruktur, die verknüpften Postfächern zugeordnet sind, die jeweils einer Rollenzuweisungsrichtlinie zugewiesen sind**

![Rollengruppe und Zuweisungsrichtlinie – Beziehungen](images/Dd298099.785b9b35-4292-43ce-917b-117d0174742e(EXCHG.150).gif "Rollengruppe und Zuweisungsrichtlinie – Beziehungen")

Zurück zum Seitenanfang

## Konfigurieren von grenzübergreifenden Berechtigungen

Zum Konfigurieren von grenzübergreifenden Berechtigungen in einer Topologie mit mehreren Gesamtstrukturen müssen Sie verknüpfte Rollengruppen für jede der Rollengruppen erstellen, die Sie mit einer USG in einer fremden Gesamtstruktur verknüpfen möchten. Dies bedeutet, dass Sie eine verknüpfte Rollengruppe für jede integrierte Rollengruppe erstellen müssen. Folgende Schritte sind erforderlich:

1.  Erstellen Sie für die zu erstellenden verknüpften Rollengruppen eine USG in der fremden Gesamtstruktur. Fügen Sie dieser USG Mitglieder hinzu, denen Sie Berechtigungen erteilen möchten.

2.  Erstellen Sie eine verknüpfte Rollengruppe für jede integrierte Rollengruppe. Folgendes geschieht, wenn die verknüpfte Rollengruppe erstellt wird:
    
      - Die Rollen, die der integrierten Rollengruppe zugewiesen sind, werden der neuen verknüpften Rollengruppe zugewiesen.
    
      - Die verknüpfte Rollengruppe wird der USG in der fremden Gesamtstruktur zugeordnet.

3.  Erstellen Sie verknüpfte Rollengruppen für alle benutzerdefinierten Rollengruppen, die Sie erstellt haben.

4.  Weisen Sie den neuen verknüpften Rollengruppen optional benutzerdefinierte Bereiche zu.

Ausführliche Anweisungen zum Ausführen dieser Schritte finden Sie unter den folgenden Themen:

  - [Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln](create-linked-role-groups-that-mirror-built-in-role-groups-exchange-2013-help.md)

  - [Verwalten von verknüpften Rollengruppen](manage-linked-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

Informationen dazu, wie Sie die USG ändern, der eine verknüpfte Rollengruppe zugeordnet ist, finden Sie unter [Verwalten von verknüpften Rollengruppen](manage-linked-role-groups-exchange-2013-help.md).

Beim Erstellen eines verknüpften Postfachs wird dieses automatisch einer Rollenzuweisungsrichtlinie zugewiesen. Sie können die Rollenzuweisungsrichtlinie ändern, die dem verknüpften Postfach zugeordnet ist, oder Sie ändern die Rollenzuweisungsrichtlinie, die Postfächern bei deren Erstellung standardmäßig zugeordnet wird. Weitere Informationen hierzu finden Sie unter den folgenden Themen:

  - [Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md)

  - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

