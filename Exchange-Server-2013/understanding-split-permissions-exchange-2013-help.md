---
title: 'Grundlegendes zu geteilten Berechtigungen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu geteilten Berechtigungen
ms:assetid: 2b709e15-63a2-4841-94bc-b289b71166d0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638106(v=EXCHG.150)
ms:contentKeyID: 50475253
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu geteilten Berechtigungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Organisationen, in denen die Verwaltung von Microsoft Exchange Server 2013-Objekten und Active Directory-Objekten getrennt wird, verwenden ein sogenanntes *Modell mit geteilten Berechtigungen*. Über geteilte Berechtigungen können Organisationen bestimmte Berechtigungen und zugehörige Aufgaben bestimmten Gruppen innerhalb der Organisationen zuweisen. Diese Arbeitsteilung hilft, Standards zu wahren und Workflows aufrechtzuerhalten sowie Änderungen in der Organisation zu steuern.

Die höchste Stufe geteilter Berechtigungen besteht in der Trennung von Exchange-Verwaltung und Active Directory-Verwaltung. Zahlreiche Organisationen verfügen über zwei Gruppen: Administratoren, die die Exchange-Infrastruktur der Organisation, wie Server und Empfänger, verwalten, und Administratoren, die die Active Directory-Infrastruktur verwalten. Für viele Organisationen ist diese Trennung wichtig, da die Active Directory-Infrastruktur sich häufig über mehrere Standorte, Domänen, Anwendungen und auch Active Directory-Gesamtstrukturen erstreckt. Active Directory-Administratoren müssen sicherstellen, dass an Active Directory vorgenommene Änderungen sich nicht negativ auf andere Dienste auswirken. Deshalb ist im Allgemeinen nur eine kleine Gruppe Administratoren zur Verwaltung dieser Infrastruktur berechtigt.

Darüber hinaus kann auch die Infrastruktur für Exchange mit Servern und Empfängern komplex sein und besondere Fachkenntnisse erfordern. Außerdem speichert Exchange streng vertrauliche Informationen über die Geschäftstätigkeiten der Organisation. Exchange-Administratoren könnten auf diese Informationen zugreifen. Durch die Beschränkung der Anzahl von Exchange-Administratoren begrenzt die Organisation die Anzahl der Personen, die Änderungen an der Exchange-Konfiguration vornehmen und auf sensible Informationen zugreifen können.

Bei geteilten Berechtigungen wird üblicherweise zwischen der Erstellung von Sicherheitsprinzipalen in Active Directory, wie Benutzern und Sicherheitsgruppen, und der anschließenden Konfiguration dieser Objekte unterschieden. So können Sie steuern, wer Objekte erstellen darf, die den Zugriff auf das Netzwerk gewähren, und damit die Wahrscheinlichkeit nicht autorisierter Zugriffe auf das Netzwerk reduzieren. In den meisten Fällen können nur Active Directory-Administratoren Sicherheitsprinzipale erstellen, während andere Administratoren, z. B. Exchange-Administratoren, bestimmte Attribute in vorhandenen Active Directory-Objekten verwalten können.

Zur Unterstützung der unterschiedlichen Anforderungen an die getrennte Verwaltung von Exchange und Active Directory können Sie in Exchange 2013 auswählen, ob Sie ein Modell mit gemeinsamen Berechtigungen oder ein Modell mit geteilten Berechtigungen verwenden möchten. Exchange 2013 bietet zwei verschiedene Modelle mit geteilten Berechtigungen: RBAC und Active Directory. In Exchange 2013 wird standardmäßig ein Modell mit gemeinsamen Berechtigungen verwendet.

**Inhalt**

Erläuterung von rollenbasierter Zugriffssteuerung und Active Directory

Gemeinsame Berechtigungen

Geteilte Berechtigungen

Geteilte RBAC-Berechtigungen

Geteilte Active Directory-Berechtigungen

## Erläuterung von rollenbasierter Zugriffssteuerung und Active Directory


Damit die Funktionsweise geteilter Berechtigungen klar wird, müssen Sie verstehen, wie das Berechtigungsmodell für die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC) in Exchange 2013 mit Active Directory zusammenarbeitet. Das RBAC-Modell steuert, wer welche Aktionen durchführen kann und an welchen Objekten diese Aktionen durchgeführt werden können. Weitere Informationen zu den verschiedenen in diesem Thema erläuterten RBAC-Komponenten finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

In Exchange 2013 müssen alle an Exchange-Objekten ausgeführten Aufgaben über die Exchange-Verwaltungsshell oder die Exchange-Exchange-Verwaltungskonsole erfolgen. Beide Verwaltungstools verwenden RBAC zur Autorisierung aller ausgeführten Aufgaben.

Die Komponente RBAC ist auf allen Servern vorhanden, auf denen Exchange 2013 ausgeführt wird. RBAC prüft, ob der Benutzer, der eine Aktion durchführt, auch dazu berechtigt ist:

  - Ist der Benutzer nicht berechtigt, die Aktion durchzuführen, lässt RBAC nicht zu, dass die Aktion fortgesetzt wird.

  - Ist der Benutzer berechtigt, die Aktion durchzuführen, prüft RBAC, ob der Benutzer berechtigt ist, die Aktion für das jeweilige angeforderte Objekt durchzuführen:
    
      - Wenn der Benutzer berechtigt ist, lässt RBAC zu, dass die Aktion fortgesetzt wird.
    
      - Wenn der Benutzer nicht berechtigt ist, lässt RBAC nicht zu, dass die Aktion fortgesetzt wird.

Wenn RBAC zulässt, dass eine Aktion fortgesetzt wird, wird die Aktion im Kontext von "Exchange Trusted Subsystem" und nicht im Kontext des Benutzers ausgeführt. "Exchange Trusted Subsystem" ist eine universelle Sicherheitsgruppe (USG) mit umfangreichen Berechtigungen, die Lese- und Schreibzugriff auf jedes Exchange-bezogene Objekt in der Exchange-Organisation besitzt. Außerdem gehört sie zur lokalen Sicherheitsgruppe "Administrators" und zur USG "Exchange Windows Permissions", sodass Exchange das Erstellen und Verwalten von Active Directory-Objekten ermöglicht ist.


> [!WARNING]
> Nehmen Sie keine manuellen Änderungen an der Mitgliedschaft der Sicherheitsgruppe "Exchange Trusted Subsystem" vor. Fügen Sie die Gruppe auch nicht einer Objektzugriffssteuerungsliste hinzu oder entfernen sie daraus. Wenn Sie die universelle Exchange-Sicherheitsgruppe "Vertrauenswürdiges Subsystem" selbst ändern, könnten Sie Ihrer Exchange einen irreparablen Schaden zufügen.



Sie sollten wissen, dass es bei der Verwendung der Exchange-Verwaltungstools keine Rolle spielt, über welche Active Directory-Berechtigungen ein Benutzer verfügt. Ist der Benutzer via RBAC berechtigt, eine Aktion in den Exchange-Verwaltungstools auszuführen, kann der Benutzer die Aktion unabhängig von seinen Active Directory-Berechtigungen ausführen. Ebenso gilt, dass die Aktion eines Benutzers, der Organisationsadministrator in Active Directory ist, jedoch nicht über die Berechtigung zum Ausführen einer Aktion wie das Erstellen eines Postfachs in den Exchange-Verwaltungstools verfügt, nicht erfolgreich ist, da der Benutzer laut RBAC nicht die erforderlichen Berechtigungen besitzt.


> [!IMPORTANT]
> Obwohl das RBAC-Berechtigungsmodell nicht für das Active Directory-Benutzer- und -Computer-Verwaltungstool gilt, können Active Directory-Benutzer und -Computer die Exchange-Konfiguration nicht verwalten. Ein Benutzer kann somit durchaus über den Zugriff verfügen, um einige Attribute für Active Directory-Objekte wie den Anzeigenamen eines Benutzers zu ändern, er muss allerdings die Exchange-Verwaltungstools verwenden und somit durch RBAC zum Verwalten von Exchange-Attributen autorisiert sein.



Zurück zum Seitenanfang

## Gemeinsame Berechtigungen

Das Modell mit gemeinsamen Berechtigungen ist das Standardmodell für Exchange 2013. Wenn Sie dieses Berechtigungsmodell verwenden möchten, müssen Sie nichts ändern. Bei diesem Modell erfolgt die Verwaltung von Exchange- und Active Directory-Objekten in den Exchange-Verwaltungstools nicht getrennt. Es ermöglicht Administratoren, die die Exchange-Verwaltungstools verwenden, Sicherheitsprinzipale in Active Directory zu erstellen.

In der folgenden Tabelle sind die Rollen aufgeführt, die das Erstellen von Sicherheitsprinzipalen in Exchange ermöglichen, sowie die Verwaltungsrollengruppen, denen sie standardmäßig zugewiesen sind.

### Sicherheitsprinzipal-Verwaltungsrollen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrolle</th>
<th>Rollengruppe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="mail-recipient-creation-role-exchange-2013-help.md">Rolle „Erstellung von E-Mail-Empfängern“</a></p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p><a href="security-group-creation-and-membership-role-exchange-2013-help.md">Rolle „Sicherheitsgruppenerstellung und -mitgliedschaft“</a></p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


Nur Rollengruppen, Benutzer oder USGs, denen die Rolle "Erstellung von E-Mail-Empfängern" zugewiesen wurde, können Sicherheitsprinzipale wie Active Directory-Benutzer erstellen. Standardmäßig ist diese Rolle den Rollengruppen Organisationsverwaltung und Empfängerverwaltung zugewiesen. Daher können Mitglieder dieser Rollengruppen Sicherheitsprinzipale erstellen.

Nur Rollengruppen, Benutzer oder USGS, denen die Rolle "Sicherheitsgruppenerstellung und -mitgliedschaft" zugewiesen ist, können Sicherheitsgruppen erstellen oder ihre Mitgliedschaften verwalten. Standardmäßig ist diese Rolle nur der Rollengruppe Organisationsverwaltung zugewiesen. Daher können nur Mitglieder der Rollengruppe Organisationsverwaltung die Mitgliedschaft von Sicherheitsgruppen erstellen oder verwalten.

Sie können die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -verwaltung" anderen Rollengruppen, Benutzern oder USGs zuweisen, wenn Sie möchten, dass andere Benutzer Sicherheitsprinzipale erstellen können.

Um die Verwaltung vorhandener Sicherheitsprinzipale in Exchange 2013 zu ermöglichen, ist die Rolle "E-Mail-Empfänger" standardmäßig den Rollengruppen Organisationsverwaltung und Empfängerverwaltung zugewiesen. Nur Rollengruppen, Benutzer oder USGs, denen die Rolle "E-Mail-Empfänger" zugewiesen wurde, können vorhandene Sicherheitsprinzipale verwalten. Wenn Sie möchten, dass andere Rollengruppen, Benutzer oder USGs vorhandene Sicherheitsprinzipale verwalten können, müssen Sie ihnen die Rolle "E-Mail-Empfänger" zuweisen.

Weitere Informationen zum Hinzufügen von Rollen zu Rollengruppen, Benutzern oder USGs finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

Weitere Informationen zum Zurückwechseln zu einem Modell mit gemeinsamen Berechtigungen nach dem Wechseln zu einem Modell mit geteilten Berechtigungen finden Sie unter [Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen](configure-exchange-2013-for-shared-permissions-exchange-2013-help.md).

Zurück zum Seitenanfang

## Geteilte Berechtigungen

Wenn in Ihrer Organisation die Exchange-Verwaltung und die Active Directory-Verwaltung getrennt sind, müssen Sie Exchange so konfigurieren, dass das Modell mit geteilten Berechtigungen unterstützt wird. Bei einer ordnungsgemäßen Konfiguration können nur die von Ihnen festgelegten Administratoren, z. B. Active Directory-Administratoren, Sicherheitsprinzipale erstellen, und nur Exchange-Administratoren können die Exchange-Attribute für vorhandene Sicherheitsprinzipale ändern. Diese Teilung der Berechtigungen entspricht auch ungefähr der Teilung in Domänen- und Konfigurationspartitionen in Active Directory. Partitionen werden auch als Namenskontexte bezeichnet. In der Domänenpartition werden die Benutzer, Gruppen und sonstigen Objekte für eine bestimmte Domäne gespeichert. In der Konfigurationspartition werden die gesamtstrukturweiten Konfigurationsinformationen für die Dienste gespeichert, die Active Directory verwenden, z. B. Exchange. In der Domänenpartition gespeicherte Daten werden im Allgemeinen von Active Directory-Administratoren verwaltet, obwohl Objekte Exchange-spezifische Attribute enthalten können, die von Exchange-Administratoren verwaltet werden können. In der Konfigurationspartition gespeicherte Daten werden von den Administratoren für die jeweiligen Dienste verwaltet, die Daten in dieser Partition speichern. Bei Exchange sind dies in der Regel Exchange-Administratoren.

Exchange 2013 unterstützt die folgenden beiden Arten von geteilten Berechtigungen:

  - **Geteilte RBAC-Berechtigungen**   Die Berechtigungen zum Erstellen von Sicherheitsprinzipalen in der Active Directory-Domänenpartition werden von RBAC gesteuert. Nur Exchange-Server und -Dienste sowie Mitglieder der entsprechenden Rollengruppen können Sicherheitsprinzipale erstellen.

  - **Geteilte Active Directory-Berechtigungen**   Die Berechtigungen zum Erstellen von Sicherheitsprinzipalen in der Active Directory-Domänenpartition werden von allen Exchange-Benutzern, -Diensten und -Servern vollständig entfernt. In RBAC wird keine Option zum Erstellen von Sicherheitsprinzipalen bereitgestellt. In Active Directory müssen Sicherheitsprinzipale mithilfe von Active Directory-Verwaltungstools erstellt werden.
    

    > [!IMPORTANT]
    > Während geteilte Berechtigungen von Active Directory aktiviert oder deaktiviert werden können, indem das Setup auf einem Computer mit vorhandener Installation von Exchange 2013&nbsp;ausgeführt wird, gilt die Konfiguration für geteilte Berechtigungen von Active Directory sowohl für Exchange 2013-Server&nbsp;als auch für Exchange 2010-Server. Sie hat jedoch keine Auswirkungen auf Microsoft Exchange Server&nbsp;2007-Server.



Wenn Ihre Organisation ein Modell mit geteilten Berechtigungen statt eines Modells mit gemeinsamen Berechtigungen auswählt, sollten Sie das RBAC-Modell mit geteilten Berechtigungen verwenden. Das RBAC-Modell mit geteilten Berechtigungen ist deutlich flexibler und ermöglicht beinahe die gleiche administrative Trennung wie geteilte Active Directory-Berechtigungen, mit der Ausnahme, dass im RBAC-Modell mit geteilten Berechtigungen Exchange-Server und -Dienste Sicherheitsprinzipale erstellen können.

Sie werden während der Installation gefragt, ob Sie geteilte Active Directory-Berechtigungen aktivieren möchten. Wenn Sie geteilte Active Directory-Berechtigungen aktivieren und dann zu gemeinsamen Berechtigungen oder geteilten RBAC-Berechtigungen wechseln möchten, müssen Sie Setup erneut ausführen und die geteilten Active Directory-Berechtigungen deaktivieren. Diese Auswahl gilt für alle Exchange 2010- und Exchange 2013-Server in der Organisation.

In den folgenden Abschnitten werden RBAC und geteilte Active Directory-Berechtigungen detaillierter beschrieben.

Zurück zum Seitenanfang

## Geteilte RBAC-Berechtigungen

Das RBAC-Sicherheitsmodell teilt die standardmäßigen Verwaltungsrollenzuweisungen in Rollen, mit denen Sicherheitsprinzipale in der Active Directory-Domänenpartition erstellt werden können, und Rollen, mit denen die Exchange-Organisationsdaten in der Active Directory-Konfigurationspartition verwaltet werden. Sicherheitsprinzipale, also z. B. Benutzer mit Postfächern und Verteilergruppen, können von Administratoren erstellt werden, denen die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" zugewiesen sind. Diese Berechtigungen sind von den Berechtigungen getrennt, die zum Erstellen von Sicherheitsprinzipalen außerhalb der Exchange-Verwaltungstools erforderlich sind. Auch Exchange-Administratoren, denen nicht die Rollen "Erstellung von E-Mail-Empfängern" und "Sicherheitsgruppenerstellung und -mitgliedschaft" zugewiesen wurden, können Exchange-bezogene Attribute für Sicherheitsprinzipale ändern. Active Directory-Administratoren können außerdem die Exchange-Verwaltungstools verwenden, um Active Directory-Sicherheitsprinzipale zu erstellen.

Exchange-Server und "Exchange Trusted Subsystem" verfügen über die Berechtigung, in Active Directory Sicherheitsprinzipale im Auftrag von Benutzern und in RBAC integrierten Drittanbieterprogrammen zu erstellen.

Geteilte RBAC-Berechtigungen sind für Ihre Organisation geeignet, wenn Folgendes zutrifft:

  - In Ihrer Organisation ist es nicht erforderlich, dass Sicherheitsprinzipale nur mit Active Directory-Verwaltungstools und nur durch Benutzer mit speziellen Active Directory-Berechtigungen erstellt werden.

  - In Ihrer Organisation ist es zulässig, dass Dienste, wie Exchange-Server, Sicherheitsprinzipale erstellen.

  - Sie möchten das Erstellen von Postfächern, E-Mail-aktivierten Benutzern, Verteilergruppen und Rollengruppen vereinfachen, indem Sie ihre Erstellung über die Exchange-Verwaltungstools zulassen.

  - Sie möchten die Mitgliedschaft in Verteilergruppen und Rollengruppen über die Exchange-Verwaltungstools verwalten.

  - Sie verfügen über Drittanbieterprogramme, für die es erforderlich ist, dass Exchange-Server Sicherheitsprinzipale in ihrem Auftrag erstellen können.

Wenn in Ihrer Organisation eine vollständige Trennung der Exchange- und der Active Directory-Verwaltung erforderlich ist, bei der Active Directory nicht mit Exchange-Verwaltungstools oder Exchange-Diensten verwaltet werden darf, lesen Sie den Abschnitt Geteilte Active Directory-Berechtigungen weiter unten in diesem Thema.

Der Wechsel von gemeinsamen Berechtigungen zu geteilten RBAC-Berechtigungen ist ein manueller Vorgang, bei dem Sie die erforderlichen Erstellungsberechtigungen für Sicherheitsprinzipale von den Rollengruppen entfernen, denen sie standardmäßig gewährt werden. In der folgenden Tabelle sind die Rollen aufgeführt, die das Erstellen von Sicherheitsprinzipalen in Exchange ermöglichen, sowie die Verwaltungsrollengruppen, denen sie standardmäßig zugewiesen sind.

### Sicherheitsprinzipal-Verwaltungsrollen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrolle</th>
<th>Rollengruppe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="mail-recipient-creation-role-exchange-2013-help.md">Rolle „Erstellung von E-Mail-Empfängern“</a></p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p><a href="security-group-creation-and-membership-role-exchange-2013-help.md">Rolle „Sicherheitsgruppenerstellung und -mitgliedschaft“</a></p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


Standardmäßig können Mitglieder der Rollengruppen Organisationsverwaltung und Empfängerverwaltung Sicherheitsprinzipale erstellen. Sie müssen die Möglichkeit zum Erstellen von Sicherheitsprinzipalen von den integrierten Rollengruppen an eine neue, von Ihnen erstellte Rollengruppe übertragen.

Gehen Sie wie folgt vor, um geteilte RBAC-Berechtigungen zu konfigurieren:

1.  Deaktivieren Sie geteilte Active Directory-Berechtigungen, wenn diese aktiviert sind.

2.  Erstellen Sie eine Rollengruppe mit den Active Directory-Administratoren, die Sicherheitsprinzipale erstellen können sollen.

3.  Erstellen Sie reguläre und delegierende Rollenzuweisungen zwischen der Rolle "Erstellung von E-Mail-Empfängern" und der neuen Rollengruppe.

4.  Erstellen Sie reguläre und delegierende Rollenzuweisungen zwischen der Rolle "Sicherheitsgruppenerstellung und -verwaltung" und der neuen Rollengruppe.

5.  Entfernen Sie die regulären und die delegierenden Verwaltungsrollenzuweisungen zwischen der Rolle "Erstellung von E-Mail-Empfängern" und den Rollengruppen Organisationsverwaltung und Empfängerverwaltung.

6.  Entfernen Sie die regulären und die delegierenden Rollenzuweisungen zwischen der Rolle "Sicherheitsgruppenerstellung und -verwaltung" und der Rollengruppe Organisationsverwaltung.

Danach können nur die Mitglieder der von Ihnen erstellten neuen Rollegruppe Sicherheitsprinzipale, z. B. Postfächer, erstellen. Die neue Gruppe kann Objekte nur erstellen. Sie kann keine Exchange-Attribute für das neue Objekt konfigurieren. Ein Active Directory-Administrator, der Mitglied der neuen Gruppe ist, muss das Objekt erstellen, und danach muss ein Exchange-Administrator die Exchange-Attribute des Objekts konfigurieren. Exchange-Administratoren können die folgenden Cmdlets nicht verwenden:

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

Exchange-Administratoren können jedoch Exchange-spezifische Objekte erstellen und verwalten, beispielsweise Transportregeln, Verteilergruppen usw., und sie können Exchange-bezogene Attribute für beliebige Objekte verwalten.

Außerdem stehen die zugeordneten Funktionen in der Exchange-Verwaltungskonsole und in Outlook Web App, beispielsweise der Assistent für neue Postfächer, nicht mehr zur Verfügung, oder ihre Verwendung führt zu einem Fehler.

Wenn Sie möchten, dass die neue Rollengruppe auch die Exchange-Attribute für das neue Objekt verwalten kann, muss die Rolle "E-Mail-Empfänger" ebenfalls dieser neuen Rollengruppe zugewiesen werden.

Weitere Informationen zum Konfigurieren eines geteilten Berechtigungsmodells finden Sie unter [Konfigurieren von Exchange 2013 für geteilte Berechtigungen](configure-exchange-2013-for-split-permissions-exchange-2013-help.md).

Zurück zum Seitenanfang

## Geteilte Active Directory-Berechtigungen

Mit geteilten Active Directory-Berechtigungen muss die Erstellung von Sicherheitsprinzipalen in der Active Directory-Domänenpartition, z. B. von Postfächern und Verteilergruppen, mithilfe der Active Directory-Verwaltungstools durchgeführt werden. Es werden mehrere Änderungen an den Berechtigungen vorgenommen, die "Exchange Trusted Subsystem" und Exchange-Servern erteilt werden, um die Möglichkeiten von Exchange-Administratoren und -Servern einzuschränken. Die folgenden funktionalen Änderungen treten auf, wenn Sie geteilte Active Directory-Berechtigungen aktivieren:

  - Das Erstellen von Postfächern, E-Mail-aktivierten Benutzern, Verteilergruppen und sonstigen Sicherheitsprinzipalen wird aus den Exchange-Verwaltungstools entfernt.

  - Verteilergruppenmitglieder können nicht über die Exchange-Verwaltungstools hinzugefügt und entfernt werden.

  - Alle Berechtigungen zum Erstellen von Sicherheitsprinzipalen, die "Exchange Trusted Subsystem" und Exchange-Servern erteilt wurden, werden entfernt.

  - Exchange-Server und die Exchange-Verwaltungstools können nur die Exchange-Attribute vorhandener Sicherheitsprinzipale in Active Directory ändern.

Wenn Sie beispielsweise ein Postfach erstellen möchten, für das geteilte Active Directory-Berechtigungen aktiviert sind, muss zuerst ein Benutzer, der über die erforderlichen Active Directory-Berechtigungen verfügt, mithilfe der Active Directory-Tools einen Benutzer erstellen. Anschließend kann der Benutzer mithilfe der Exchange-Verwaltungstools für das Postfach aktiviert werden. Nur die Exchange-bezogenen Attribute des Postfachs können von Exchange-Administratoren mithilfe der Exchange-Verwaltungstools geändert werden.

Geteilte Active Directory-Berechtigungen sind für Ihre Organisation geeignet, wenn Folgendes zutrifft:

  - In Ihrer Organisation ist es erforderlich, dass Sicherheitsprinzipale nur mithilfe der Active Directory-Verwaltungstools oder nur von Benutzern mit bestimmten Berechtigungen in Active Directory erstellt werden.

  - Sie möchten die Möglichkeit zum Erstellen von Sicherheitsprinzipalen vollständig von den Benutzern trennen, die die Exchange-Organisation verwalten.

  - Sie möchten die gesamte Verwaltung von Verteilergruppen, einschließlich der Erstellung von Verteilergruppen und des Hinzufügens und Entfernens von Mitgliedern dieser Gruppen, mithilfe der Active Directory-Verwaltungstools durchführen.

  - Sie möchten nicht, dass Exchange-Server oder Drittanbieterprogramme, die Exchange in ihrem Auftrag verwenden, Sicherheitsprinzipale erstellen.


> [!IMPORTANT]
> Sie können den Wechsel zu geteilten Active Directory-Berechtigungen bei der Installation von Exchange 2013&nbsp;auswählen, indem Sie den Setup-Assistenten verwenden oder bei der Ausführung von <CODE>setup.exe</CODE> über die Befehlszeile den Parameter <EM>ActiveDirectorySplitPermissions</EM> verwenden. Sie können geteilte Active Directory-Berechtigungen außerdem nach der Installation von Exchange 2013 aktivieren oder deaktivieren, indem Sie <CODE>setup.exe</CODE> erneut über die Befehlszeile ausführen. Legen Sie den Parameter <EM>ActiveDirectorySplitPermissions</EM> auf <CODE>true</CODE> fest, um geteilte Active Directory-Berechtigungen zu aktivieren. Legen Sie ihn auf <CODE>false</CODE> fest, um geteilte Berechtigungen zu deaktivieren. Sie müssen stets die Option <EM>PrepareAD</EM> zusammen mit dem Parameter <EM>ActiveDirectorySplitPermissions</EM> angeben.<BR>Wenn Sie über mehrere Domänen in derselben Gesamtstruktur verfügen, müssen Sie entweder die Option <EM>PrepareAllDomains</EM> angeben, wenn Sie geteilte Active Directory-Berechtigungen anwenden, oder das Setupprogramm mit der Option <EM>PrepareDomain</EM> in jeder Domäne ausführen. Wenn Sie sich dafür entscheiden, das Setupprogramm mit der Option <EM>PrepareDomain</EM> in jeder Domäne auszuführen, anstatt die Option <EM>PrepareAllDomains</EM> zu verwenden, müssen Sie jede Domäne vorbereiten, die Exchange-Server, E-Mail-aktivierte Objekte oder globale Katalogserver enthält, auf die von einem Exchange-Server zugegriffen werden kann.




> [!IMPORTANT]
> Sie können geteilte Active Directory-Berechtigungen nicht aktivieren, wenn Sie Exchange 2010 oder Exchange 2013 auf einem Domänencontroller installiert haben.<BR>Nach dem Aktivieren oder Deaktivieren von geteilten Active Directory-Berechtigungen sollten Sie die Exchange 2010- und Exchange 2013-Server in Ihrer Organisation neu starten, um zu erzwingen, dass sie das neue Active Directory-Zugriffstoken mit den aktualisierten Berechtigungen einlesen.



In Exchange 2013 werden geteilte Active Directory-Berechtigungen implementiert, indem Berechtigungen und die Mitgliedschaft aus der Sicherheitsgruppe für Exchange Windows-Berechtigungen entfernt werden. Dieser Sicherheitsgruppe werden bei Verwendung von gemeinsamen Berechtigungen oder von geteilten RBAC-Berechtigungen die Berechtigungen für zahlreiche Objekte und Attribute, die nicht zu Exchange gehören, im gesamten Active Directory-Verzeichnis erteilt. Indem Sie die Berechtigungen und die Mitgliedschaft von dieser Sicherheitsgruppe entfernen, verhindern Sie, dass Exchange-Administratoren und -Dienste diese nicht zu Exchange gehörenden Active Directory-Objekte erstellen oder ändern.

Eine Liste der Änderungen an der Sicherheitsgruppe "Exchange Windows Permissions" und an anderen Exchange-Komponenten, die bei der Aktivierung oder Deaktivierung geteilter Active Directory-Berechtigungen vorgenommen werden, finden Sie in der folgenden Tabelle.


> [!NOTE]
> Rollenzuweisungen zu Rollengruppen, mit denen Exchange-Administratoren die Möglichkeit zum Erstellen von Sicherheitsprinzipalen erhalten, werden entfernt, wenn geteilte Active Directory-Berechtigungen aktiviert werden. Dies dient dazu, den Zugriff auf Cmdlets zu entfernen, bei deren Ausführung andernfalls ein Fehler generiert würde, da sie nicht über Berechtigungen zum Erstellen des zugeordneten Active Directory-Objekts verfügen.



### Änderungen bei geteilten Active Directory-Berechtigungen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktion</th>
<th>Von Exchange durchgeführte Änderungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aktivieren geteilter Active Directory-Berechtigungen bei der Installation des ersten Exchange 2013-Servers</p></td>
<td><p>Folgende Aktionen werden ausgeführt, wenn Sie geteilte Active Directory-Berechtigungen über den Setup-Assistenten oder durch Ausführen von <code>setup.exe</code> mit den Parametern <code>/PrepareAD</code> und <code>/ActiveDirectorySplitPermissions:true</code> aktivieren:</p>
<ul>
<li><p>Eine Organisationseinheit (OU) mit dem Namen <strong>Microsoft Exchange Protected Groups</strong> wird erstellt.</p></li>
<li><p>Die Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> wird in der Organisationseinheit <strong>Microsoft Exchange Protected Groups</strong> erstellt.</p></li>
<li><p>Die Sicherheitsgruppe <strong>Exchange Trusted Subsystem</strong> wird der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> nicht hinzugefügt.</p></li>
<li><p>Die Erstellung nicht delegierender Verwaltungsrollenzuweisungen zu Verwaltungsrollen mit den folgenden Verwaltungsrollentypen wird übersprungen:</p>
<ul>
<li><p><code>MailRecipientCreation</code></p></li>
<li><p><code>SecurityGroupCreationandMembership</code></p></li>
</ul></li>
<li><p>Zugriffssteuerungseinträge (Access Control Entries, ACEs), die der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> zugewiesen worden wären, werden dem Active Directory-Domänenobjekt nicht hinzugefügt.</p></li>
</ul>
<p>Wenn Sie das Setupprogramm mit den Optionen <em>PrepareAllDomains</em> oder <em>PrepareDomain</em> ausführen, geschieht in jeder vorbereiteten untergeordneten Domäne Folgendes:</p>
<ul>
<li><p>Alle ACEs, die der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> zugewiesen sind, werden vom Domänenobjekt entfernt.</p></li>
<li><p>In jeder Domäne werden ACEs festgelegt, mit Ausnahme aller ACEs, die der Sicherheitsgruppe <strong>Exchange Windows-Berechtigungen</strong> zugewiesen sind.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p>Wechseln von gemeinsamen Berechtigungen oder geteilten RBAC-Berechtigungen zu geteilten Active Directory-Berechtigungen</p></td>
<td><p>Folgende Aktionen werden ausgeführt, wenn Sie den Befehl <code>setup.exe</code> mit den Parametern <code>/PrepareAD</code> und <code>/ActiveDirectorySplitPermissions:true</code> ausführen:</p>
<ul>
<li><p>Eine Organisationseinheit mit dem Namen <strong>Microsoft Exchange Protected Groups</strong> wird erstellt.</p></li>
<li><p>Die Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> wird in die Organisationseinheit <strong>Microsoft Exchange Protected Groups</strong> verschoben.</p></li>
<li><p>Die Sicherheitsgruppe <strong>Exchange Trusted Subsystem</strong> wird aus der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> entfernt.</p></li>
<li><p>Alle nicht delegierenden Rollenzuweisungen zu Verwaltungsrollen mit den folgenden Rollentypen werden entfernt:</p>
<ul>
<li><p><code>MailRecipientCreation</code></p></li>
<li><p><code>SecurityGroupCreationandMembership</code></p></li>
</ul></li>
<li><p>Alle ACEs, die der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> zugewiesen sind, werden vom Domänenobjekt entfernt.</p></li>
</ul>
<p>Wenn Sie das Setupprogramm mit den Optionen <em>PrepareAllDomains</em> oder <em>PrepareDomain</em> ausführen, geschieht in jeder vorbereiteten untergeordneten Domäne Folgendes:</p>
<ul>
<li><p>Alle ACEs, die der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> zugewiesen sind, werden vom Domänenobjekt entfernt.</p></li>
<li><p>In jeder Domäne werden ACEs festgelegt, mit Ausnahme aller ACEs, die der Sicherheitsgruppe <strong>Exchange Windows-Berechtigungen</strong> zugewiesen sind.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Wechseln von geteilten Active Directory-Berechtigungen zu gemeinsamen Berechtigungen oder geteilten RBAC-Berechtigungen</p></td>
<td><p>Folgende Aktionen werden ausgeführt, wenn Sie den Befehl <code>setup.exe</code> mit den Parametern <code>/PrepareAD</code> und <code>/ActiveDirectorySplitPermissions:false</code> ausführen:</p>
<ul>
<li><p>Die Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> wird in die Organisationseinheit <strong>Microsoft Exchange Security Groups</strong> verschoben.</p></li>
<li><p>Die Organisationseinheit <strong>Microsoft Exchange Protected Groups</strong> wird entfernt.</p></li>
<li><p>Die Sicherheitsgruppe <strong>Exchange Trusted Subsystem</strong> wird der Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> hinzugefügt.</p></li>
<li><p>ACEs werden dem Domänenobjekt für die Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> hinzugefügt.</p></li>
</ul>
<p>Wenn Sie das Setupprogramm mit den Optionen <em>PrepareAllDomains</em> oder <em>PrepareDomain</em> ausführen, geschieht in jeder vorbereiteten untergeordneten Domäne Folgendes:</p>
<ul>
<li><p>ACEs werden dem Domänenobjekt für die Sicherheitsgruppe <strong>Exchange Windows Permissions</strong> hinzugefügt.</p></li>
<li><p>In jeder Domäne werden ACEs festgelegt, einschließlich der ACEs, die der Sicherheitsgruppe <strong>Exchange Windows-Berechtigungen</strong> zugewiesen sind.</p></li>
</ul>
<p>Rollenzuweisungen für die Rollen &quot;Erstellung von E-Mail-Empfängern&quot; und &quot;Sicherheitsgruppenerstellung und -verwaltung&quot; werden beim Wechsel von geteilten Active Directory-Berechtigungen zu gemeinsamen Berechtigungen nicht automatisch erstellt. Wenn delegierende Rollenzuweisungen vor der Aktivierung der geteilten Active Directory-Berechtigungen angepasst wurden, bleiben diese Anpassungen erhalten. Informationen zum Erstellen von Rollenzuweisungen zwischen diesen Rollen und der Rollengruppe Organisationsverwaltung finden Sie unter <a href="configure-exchange-2013-for-shared-permissions-exchange-2013-help.md">Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen</a>.</p></td>
</tr>
</tbody>
</table>


Nach dem Aktivieren der geteilten Active Directory-Berechtigungen sind die folgenden Cmdlets nicht mehr verfügbar:

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

Nach dem Aktivieren der geteilten Active Directory-Berechtigungen können Sie auf die folgenden Cmdlets zugreifen, aber mit ihnen keine Verteilergruppen erstellen und nicht die Mitgliedschaft in Verteilergruppen ändern:

  - **Add-DistributionGroupMember**

  - **New-DistributionGroup**

  - **Remove-DistributionGroup**

  - **Remove-DistributionGroupMember**

  - **Update-DistributionGroupMember**

Einige Cmdlets stehen bei Verwendung von geteilten Active Directory-Berechtigungen zwar noch zur Verfügung, bieten aber möglicherweise nur begrenzte Funktionalität. Grund hierfür ist, dass sie möglicherweise das Konfigurieren von Empfängerobjekten ermöglichen, die sich in der Active Directory-Domänenpartition befinden, sowie von Exchange-Konfigurationsobjekten, die sich in der Active Directory-Konfigurationspartition befinden. Außerdem können sie das Konfigurieren von Exchange-bezogenen Attributen für Objekte ermöglichen, die in der Domänenpartition gespeichert sind. Versuche, in der Domänenpartition mit den Cmdlets Objekte zu erstellen oder nicht auf Exchange bezogene Objektattribute zu ändern, führen zu einem Fehler. Wenn Sie beispielsweise versuchen, mit dem Cmdlet **Add-ADPermission** einem Postfach Berechtigungen hinzuzufügen, wird ein Fehler zurückgegeben. Beim Konfigurieren von Berechtigungen für einen Empfangsconnector wird das Cmdlet **Add-ADPermission** jedoch erfolgreich ausgeführt. Dies ist darauf zurückzuführen, dass ein Postfach in der Domänenpartition gespeichert wird, Empfangsconnectors jedoch in der Konfigurationspartition.

Außerdem stehen die zugeordneten Funktionen in der Exchange-Verwaltungskonsole und in Outlook Web App, beispielsweise der Assistent für neue Postfächer, nicht mehr zur Verfügung, oder ihre Verwendung führt zu einem Fehler.

Exchange-Administratoren können jedoch Exchange-spezifische Objekte wie Transportregeln erstellen und verwalten.

Weitere Informationen zum Konfigurieren eines Active Directory-Modells mit geteilten Berechtigungen finden Sie unter [Konfigurieren von Exchange 2013 für geteilte Berechtigungen](configure-exchange-2013-for-split-permissions-exchange-2013-help.md).

Zurück zum Seitenanfang

