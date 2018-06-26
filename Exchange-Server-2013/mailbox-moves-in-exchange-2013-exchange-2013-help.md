---
title: 'Postfachverschiebungen in Exchange 2013: Exchange 2013 Help'
TOCTitle: Postfachverschiebungen in Exchange 2013
ms:assetid: 9c0a0bc9-2a39-4cf0-aa6e-6e5ef3fd38b5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150543(v=EXCHG.150)
ms:contentKeyID: 50476328
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Postfachverschiebungen in Exchange 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Wenn Sie ein Postfach verschieben, wird es aus einer *Quellpostfachdatenbank* in eine *Zielpostfachdatenbank* verschoben. Die Zielpostfachdatenbank kann sich auf demselben Server, auf einem anderen Server, in einer anderen Domäne, an einem anderen Active Directory-Standort oder in einer anderen Gesamtstruktur befinden.

## Gründe für das Verschieben von Postfächern

Postfächer müssen möglicherweise in folgenden Szenarien verschoben werden:

  - **Upgrade**   Beim Upgrade einer vorhandenen Microsoft Exchange Server 2007- oder Exchange Server 2010-Organisation auf Exchange Server 2013 verschieben Sie Postfächer von den vorhandenen Exchange-Servern auf einen Exchange 2013-Postfachserver.

  - **Neuausrichtung**   Sie können Postfächer zur Neuausrichtung verschieben. Sie können beispielsweise ein Postfach aus einer Datenbank in eine andere verschieben, die einen höheren Grenzwert für die Postfachgröße hat.

  - **Problemuntersuchung**   Wenn Sie ein Postfachproblem untersuchen müssen, können Sie das betreffende Postfach auf einen anderen Server verschieben. Sie können z. B. alle Postfächer mit hoher Aktivität auf einen anderen Server verschieben.

  - **Beschädigte Postfächer**   Wenn Sie beschädigte Postfächer entdecken, können Sie die Postfächer auf einen anderen Server oder in eine andere Datenbank verschieben. Die fehlerhaften Nachrichten werden nicht verschoben.

  - **Änderungen des physischen Standorts**   Sie können Postfächer auf einen Server an einem anderen Active Directory-Standort verschieben. Wenn z. B. ein Benutzer an einen anderen physischen Standort versetzt wird, können Sie das Postfach dieses Benutzers auf einen Server in der Nähe des neuen Arbeitsplatzes des Benutzers verschieben.

  - **Trennung von Administratorrollen**   Möglicherweise sollten Sie die Verwaltung von Exchange von der Verwaltung der Windows-Betriebssystemkonten trennen. Zu diesem Zweck können Sie Postfächer aus einer einzelnen Gesamtstruktur in ein Ressourcengesamtstrukturszenario verschieben. In diesem Szenario befinden sich die Exchange-Postfächer in einer Gesamtstruktur und die dazugehörigen Windows-Benutzerkonten in einer davon getrennten Gesamtstruktur.

  - **Auslagern der E-Mail-Verwaltung**   Sie können die E-Mail-Verwaltung auslagern und die Verwaltung von Windows-Benutzerkonten beibehalten. Zu diesem Zweck können Sie Postfächer aus einer einzelnen Gesamtstruktur in ein Ressourcengesamtstrukturszenario verschieben.

  - **Integrieren der E-Mail- und Benutzerkontenverwaltung**   Sie können von einem getrennten oder ausgelagerten E-Mail-Verwaltungsmodell zu einem Modell wechseln, bei dem E-Mail- und Benutzerkonten innerhalb derselben Gesamtstruktur verwaltet werden. Zu diesem Zweck können Sie Postfächer aus einem Ressourcengesamtstrukturszenario in eine einzelne Gesamtstruktur verschieben. In diesem Szenario befinden sich die Exchange-Postfächer und Windows-Benutzerkonten in derselben Gesamtstruktur.

## Exchange 2013-Verschiebevorgänge

In Microsoft Exchange Server 2013 wurde das Konzept von *Batchverschiebungen* und *Migrationsendpunkten* eingeführt. Migrationsendpunkte sind Verwaltungsobjekte, die den Remoteserver und die Verbindungen beschreiben, die mindestens einem Batch zugeordnet werden können. Die neue Architektur für Batchverschiebungen basiert auf der des Postfachreplikationsdiensts und bietet verbesserte Verwaltungsfunktionen. Die Architektur für Batchverschiebungen in Exchange 2013 bietet die folgenden Funktionen:

  - Möglichkeit, mehrere Postfächer in großen Batches zu verschieben.

  - E-Mail-Benachrichtigung bei Verschiebung mit Berichterstellung.

  - Automatische Wiederholung und automatische Priorisierung von Verschiebungen.

  - Primäre und persönliche Archivpostfächer können zusammen oder einzeln verschoben werden.

  - Option zum manuellen Abschließen der Verschiebungsanforderung, sodass Sie eine Verschiebung überprüfen können, ehe Sie sie abschließen.

  - Regelmäßige inkrementelle Synchronisierungen zum Migrieren von Änderungen.

In Exchange 2013 müssen Sie Postfächer zwischen Exchange 2007 und Exchange 2010 und Exchange 2013 mithilfe der Exchange 2013-Verwaltungskonsole und der Exchange-Verwaltungsshell verschieben.


> [!NOTE]
> Sie können in Exchange 2013 ähnlich wie in Exchange Server 2010 weiter einzelne Postfächer verschieben – entweder über die Exchange-Verwaltungskonsole oder Cmdlets für Verschiebungsanforderungen oder Migrationsbatches.




> [!NOTE]
> Lokale Postfächer können nicht aus Exchange Server&nbsp;2003 in Exchange 2013 verschoben werden.



Weitere Informationen zum Verwalten von neuen und vorhandenen Verschiebungen finden Sie unter [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).

## Migrationsendpunkte

Migrationsendpunkte dienen zum Erfassen von Remoteserverinformationen und speichern dauerhaft die benötigten Anmeldeinformationen zum Migrieren der Daten und die Einschränkungseinstellungen der Quelle. Mit Migrationsendpunkten können Sie Einstellungen für Remote- und gesamtstrukturübergreifende Verschiebungen konfigurieren. Für lokale Verschiebungen muss kein Endpunkt verwendet werden. (Bei lokalen Verschiebungen werden Postfächer zwischen zwei verschiedenen lokalen Exchange-Datenbanken verschoben.)

Die folgende Liste enthält die Bewegungstypen, die Migrationsendpunkte unterstützen:

  - **Gesamtstrukturübergreifende Verschiebung**   Verschieben von Postfächern zwischen zwei unterschiedlichen lokalen Exchange-Gesamtstrukturen. Für gesamtstrukturübergreifende Verschiebungen muss ein Exchange-"RemoteMove"-Endpunkt verwendet werden.

  - **Remoteverschiebung**   In einer hybriden Bereitstellung umfasst eine Remoteverschiebung *Onboarding-* oder *Offboardingmigrationen*. Für Remoteverschiebungen muss ein RemoteMove-Endpunkt verwendet werden. Beim Onboarding werden Postfächer aus einer lokalen Exchange-Organisation nach Exchange Online in Microsoft Office 365 verschoben. Als Quellendpunkt des Migrationsbatches wird ein "RemoteMove"-Endpunkt verwendet. Beim Offboarding werden Postfächer aus Exchange Online in Office 365 in eine lokale Exchange-Organisation verschoben. Als Zielendpunkt des Migrationsbatches wird ein Exchange-"RemoteMove"-Endpunkt verwendet.

Die folgende Tabelle enthält die Typen und Werte von Migrationsendpunkten, die Sie in Exchange 2013 verwalten können.

### Werte der Typen von Migrationsendpunkten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange RemoteMove</th>
<th>Exchange LocalMove</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MaxConcurrentMigrations</p></td>
<td><p>MaxConcurrentMigrations</p></td>
</tr>
<tr class="even">
<td><p>RemoteServer</p></td>
<td><p>Site</p></td>
</tr>
<tr class="odd">
<td><p>ArchiveDomain</p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>BadItemLimit</p></td>
<td><p>ArchiveDatabase</p></td>
</tr>
<tr class="odd">
<td><p>LargeItemLimit</p></td>
<td><p>BadItemLimit</p></td>
</tr>
<tr class="even">
<td><p>Databases</p></td>
<td><p>LargeItemLimit</p></td>
</tr>
<tr class="odd">
<td><p>TargetDeliveryDomain</p></td>
<td><p>PrimaryOnly</p></td>
</tr>
<tr class="even">
<td><p>PrimaryOnly</p></td>
<td><p>ArchiveDatabase</p></td>
</tr>
<tr class="odd">
<td><p>ArchiveDatabase</p></td>
<td><p>DAG</p></td>
</tr>
<tr class="even">
<td><p>ArchiveOnly</p></td>
<td><p>Forest</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Migrationsendpunkten finden Sie auf der Benutzeroberfläche für **Migration** in der Exchange-Verwaltungskonsole und unter [New-MigrationEndpoint](https://technet.microsoft.com/de-de/library/jj218611\(v=exchg.150\)).

Weitere Informationen zum Verwalten von neuen und vorhandenen Verschiebungen finden Sie unter [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).

