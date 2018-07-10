---
title: 'FAQ: Öffentliche Ordner: Exchange 2013 Help'
TOCTitle: 'FAQ: Öffentliche Ordner'
ms:assetid: 1cdcdcb7-f11b-45ca-ad23-7c38f640208c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ552408(v=EXCHG.150)
ms:contentKeyID: 50475129
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# FAQ: Öffentliche Ordner

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-03-27_

In diesem Thema finden Sie eine Liste häufig gestellter Fragen zu öffentlichen Ordnern in Exchange Server 2013. Weitere Informationen zu Öffentlichen Ordnern finden Sie unter [Öffentliche Ordner](public-folders-exchange-2013-help.md).

Haben Sie Fragen zu öffentlichen Ordnern, die in diesem Thema nicht beantwortet werden? Senden Sie uns eine E-Mail an [Ex2013HelpFeedback@microsoft.com](mailto:ex2013helpfeedback@microsoft.com).

## Häufig gestellte Fragen zur Migration öffentlicher Ordner

Dieser Abschnitt enthält häufig gestellte Fragen zur Migration öffentlicher Ordner. Weitere Informationen finden Sie unter [Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen](use-batch-migration-to-migrate-public-folders-to-exchange-2013-from-previous-versions-exchange-2013-help.md), [Verwenden der Stapelmigration zum Migrieren von öffentlichen Ordnern einer Vorgängerversion zu Office 365 und Exchange Online](use-batch-migration-to-migrate-legacy-public-folders-to-office-365-and-exchange-online-exchange-online-help.md) oder [Migrieren von Exchange 2013-basierten öffentlichen Ordnern zu Exchange Online mithilfe einer Batchmigration](use-batch-migration-to-migrate-exchange-2013-public-folders-to-exchange-online-exchange-online-help.md).

## Welche Szenarien werden für die Migration öffentlicher Postfächer unterstützt?

In der folgenden Liste werden die verfügbaren Optionen für die Migration von öffentlichen Ordnern zu Exchange 2013 oder Exchange Online aufgeführt.

  - Öffentliche Exchange 2007-Ordner (SP3 RU15 und höher) können zu Exchange 2013 oder Exchange Online migriert werden.

  - Öffentliche Exchange 2010-Ordner (SP3 RU8 und höher) können zu Exchange 2013 oder Exchange Online migriert werden.

  - Öffentliche Exchange 2013-Ordner (CU15 oder höher) können zu Exchange Online migriert werden.

Zurzeit werden nur Migrationen zu Exchange 2013 in derselben Active Directory-Gesamtstruktur unterstützt. Gesamtstrukturübergreifende Migrationen werden in Zukunft unterstützt.

## Wie wird nach der Migration mit der Hierarchie auf den Exchange 2010-Quellservern verfahren?

In der Abschlussphase der Migration wird der Quellserver gesperrt, sodass kein Benutzerzugriff möglich ist. Diese Sperrung bleibt erhalten, um nach Abschluss der Migration zu verhindern, dass Benutzer auf die öffentlichen Quellordner zugreifen. Sie können diese Sperrung zwar aufheben, dies wird jedoch nicht empfohlen, da die Änderungen nicht mit Exchange 2013 synchronisiert werden können.

## Wenn öffentliche Ordner migriert werden, was passiert dann mit den vorhandenen Regeln für öffentliche Ordner?

Regeln für öffentliche Ordner werden zusammen mit den Daten migriert und bleiben als Regeln für öffentliche Ordner erhalten. Sie werden nicht in Postfachregeln konvertiert.

## Was geschieht, wenn nach der Generierung der anfänglichen CSV-Datei Änderungen an der Quellhierarchie vorgenommen werden? Wie würden diese Änderungen auf die Zielhierarchie übertragen?

Anhand der CSV-Datei wird die Zuordnung zwischen der Quellhierarchie und dem Zielpostfach ermittelt. Diese Datei enthält lediglich drei Ordner auf oberster Ebene. Die untergeordneten Ordner werden automatisch migriert. Wenn also ein neuer untergeordneter Ordner hinzugefügt wird, wird dieser bei der Migration verschoben. Und wenn ein neuer Ordner auf oberster Ebene erstellt wird, wird dieser im Postfach mit der beschreibbaren Kopie der Hierarchie erstellt.

## Wie kann ich eine Deltasynchronisierung erzwingen, damit Benutzer während der finalen Synchronisierung auf öffentliche Ordner zugreifen können, wenn bei der Migration zu öffentlichen Ordnern in Exchange 2013 zwischen dem Anhalten und dem Abschließen des Vorgangs viel Zeit verstreicht?

Sie können vor dem Abschluss der Migration (vor dem Sperren der Quelle) eine Deltasynchronisierung erzwingen, indem Sie den folgenden Befehl in der Shell ausführen:

    Resume-PublicFolderMigrationRequest \PublicFolderMigration

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Resume-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218689\(v=exchg.150\)).

## Wie kann ich bei der Migration einer geografisch verteilten Hierarchie sicherstellen, dass die öffentlichen Ordner am nächstgelegenen Standort für die Zielbenutzer erstellt werden?

Als Teil der Migration wird eine CSV-Datei generiert (mit dem Skript `publicfoldertomailboxmapgenerator.ps1`). Diese Datei enthält die Zuordnung von Ordnern zu Postfächern für die neue Hierarchie. Sie können diese CSV-Datei verwenden, um Postfächer für öffentliche Ordner am geeigneten geografischen Standort zu erstellen, und die Datei so ändern, dass die erforderlichen Ordner im richtigen Postfach in der Nähe der Zielbenutzer bereitgestellt werden.

Die CSV-Eingabedatei kann mithilfe des Skripts `AggregatePFData.ps1` generiert werden, das sich im Verzeichnis "\<*Exchange-Installationsverzeichnis*\>\\V15\\Scripts" befindet. Führen Sie das Skript wie folgt aus:

    .\AggregatePFData.ps1 | Select-Object -property @{Name="FolderName"; Expression = {$_.Identity}}, @{Name="FolderSize"; Expression = {$_.TotalItemSize.Value.ToBytes()}} | Export-CSV -Path <Path followed by the name of the CSV>

## Werden vorhandene Berechtigungen für öffentliche Ordner migriert?

Ja, Berechtigungen werden automatisch auf Ordnerebene mit den Daten migriert. Dieser Schritt muss nicht separat ausgeführt werden.

## Werden öffentliche Ordner aus Exchange entfernt?

Nein. Öffentliche Ordner eignen sich hervorragend für die Outlook-Integration, für einfache Freigabeszenarios und für den Zugriff einer großen Zielgruppe auf dieselben Daten.

## Welche Clients unterstützen öffentliche Ordner?

Benutzer von Outlook 2007, Outlook 2010 und Outlook 2013 sowie Outlook 2011 für Mac können auf öffentliche Ordner zugreifen. Benutzer mit Postfächern auf Exchange Server 2013-Servern können allerdings über Clients, die Exchange-Webdienste wie Outlook für Mac verwenden, keine Verbindung zu öffentlichen Ordnern in Exchange 2007 oder Exchange 2010 herstellen. Wir empfehlen, ältere öffentliche Ordner zu Exchange 2013 zu migrieren, damit diese Benutzer weiterhin auf diese öffentlichen Ordner zugreifen können.

## Gibt es Einschränkungen bezüglich der Verwendung der Clients?

Outlook Web App wird unterstützt, aber mit Einschränkungen. Sie können öffentliche Ordner als Favoriten hinzufügen und entfernen (wenn sie öffentliche Mail-, Post- oder Kontakte-Ordner sind) und Vorgänge auf Elementebene durchführen, z. B. Beiträge erstellen, bearbeiten, löschen und beantworten. Folgende Aufgaben können in Outlook Web App allerdings nicht ausgeführt werden:

  - Erstellen oder Löschen öffentlicher Ordner

  - Drag und Drop von Inhalt

  - Zugreifen auf öffentliche Ordner, die sich auf Servern befinden, die ältere Versionen von Exchange ausführen


> [!NOTE]
> Sie können nur Regeln für öffentliche Ordner erstellen, die das Element <STRONG>Mit einer bestimmten Vorlage antworten</STRONG> in E-Mail-aktivierten öffentlichen Ordnern enthalten. Es ist möglich, dass bereits vorhandene Regeln mit <STRONG>Mit einer bestimmten Vorlage antworten</STRONG> weiterhin in nicht E-Mail-aktivierten öffentlichen Ordnern funktionieren. Für diese Ordner können Sie mit diesem Vorlagenelement keine neuen Regeln erstellen oder vorhandene Regeln mit diesem Element bearbeiten.



In einer Hybridbereitstellung werden Outlook im Web und Outlook 2011 für Mac für standortübergreifende öffentliche Ordner nicht unterstützt. Benutzer müssen sich am selben Standort wie die öffentlichen Ordner befinden, um sie über Outlook 2011 für Mac oder Outlook im Web aufzurufen. Benutzer von Outlook 2016 für Mac können in einem Hybridszenario auf öffentliche Ordner zugreifen, wenn die Verfahren unter [Hybrid-Bereitstellungsverfahren](https://technet.microsoft.com/de-de/library/jj200788\(v=exchg.150\).aspx) befolgt werden und das Update von April 2016 für Outlook 2016 für Mac auf allen Clients installiert wurde.

## Wie kann eine sehr umfangreiche Hierarchie in einem Postfach für öffentliche Ordner gespeichert werden?

Weitere Informationen über Speichergrenzwerte öffentlicher Ordner finden Sie unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md).

## Wie kann ich das Postfach mit der Hierarchie öffentlicher Ordner anzeigen?

Führen Sie den folgenden Befehl aus:

    Get-OrganizationConfig | Format-List RootPublicFolderMailbox

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997571\(v=exchg.150\)).

## Wie kann ich Inhaltspostfächer für öffentliche Ordner mithilfe der Cmdlets der Exchange-Verwaltungsshell erstellen?

Führen Sie den folgenden Befehl aus, um das erste Haupthierarchiepostfach für öffentliche Ordner und die sekundären Hierarchiepostfächer zu erstellen.

    New-Mailbox -PublicFolder -Name <name of public folder>

Weitere Informationen finden Sie unter [Erstellen eines öffentlichen Ordners](create-a-public-folder-exchange-2013-help.md).

## In früheren Exchange-Versionen konnte für jede Postfachdatenbank eine Datenbank für öffentliche Ordner angegeben werden. Wie ist dieser Aspekt in Exchange 2013 implementiert?

In Exchange 2013 gibt es keine Einstellung auf Datenbankebene. In Exchange 2013 besteht auf Postfachebene die Möglichkeit, das Postfach für öffentliche Ordner anzugeben. Standardmäßig ermittelt Exchange jedoch automatisch das Hierarchiepostfach pro Benutzer.

## Wie werden metrische Tools für öffentliche Ordner in Exchange 2013 verwendet?

In Exchange 2013 können Metrikdaten für öffentliche Ordner mit den Cmdlets [Get-PublicFolderStatistics](https://technet.microsoft.com/de-de/library/aa998663\(v=exchg.150\)) und [Get-PublicFolderItemStatistics](https://technet.microsoft.com/de-de/library/ee332344\(v=exchg.150\)) abgerufen werden. Dies entspricht der Implementierung aus Exchange 2010, sodass bei dieser Funktion keine Änderungen vorgenommen wurden. Öffentliche Ordner benötigen keine zusätzlichen Add-Ons für die Berichterstattung.

## Kann bei öffentlichen Ordnern zwischen einem internen Zugriff und dem Zugriff eines Dritten auf öffentliche Ordner unterschieden werden?

In Exchange 2013 werden Berechtigungen für öffentliche Ordner über die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC) verwaltet. Zugriffssteuerungslisten (Access Control Lists, ACLs) werden in Exchange 2013 nicht verwendet. Sie können mit den Cmdlets [Get-PublicFolderStatistics](https://technet.microsoft.com/de-de/library/aa998663\(v=exchg.150\)) und [Get-PublicFolderItemStatistics](https://technet.microsoft.com/de-de/library/ee332344\(v=exchg.150\)) die Konten nachverfolgen, die Verwaltungsaufgaben durchführen, und dann den Zugriff entsprechend überwachen. Weitere Informationen zur rollenbasierten Zugriffssteuerung finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Funktioniert die Postfachüberwachungsprotokollierung für öffentliche Ordner?

Nein. Diese Funktion kann gegenwärtig nicht verwendet werden.

## Welche Einschränkungen und Grenzwerte gelten für öffentliche Ordner? Nach welchen Empfehlungen sollte ich mich richten?

Weitere Informationen über Grenzwerte öffentlicher Ordner finden Sie unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md).

## Welche Empfehlungen gelten für das Aufteilen von Postfächern für öffentliche Ordner? Sollten diese Postfächer in derselben Datenbank platziert werden?

In vorherigen Versionen von Exchange konnten Sie öffentliche Ordner zwischen Datenbanken für öffentliche Ordner aufteilen. Sie können entscheiden, ob Sie den Inhalt eines Postfachs für öffentliche Ordner auf ein Postfach in derselben Postfachdatenbank oder in einer anderen Datenbank aufteilen. Normalerweise empfiehlt es sich, die Teilung in einer separaten Datenbank durchzuführen, weil dadurch Speicherplatz und E/A ausgeglichen werden sollen.

## Können Aufbewahrungsrichtlinien für öffentliche Ordner festgelegt werden?

Wie in früheren Versionen von Exchange können Sie Aufbewahrungslimits für Elemente festlegen. Weitere Informationen finden Sie unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md).

## Kann angegeben werden, welche Benutzer ein bestimmtes Postfach für öffentliche Ordner verwenden können?

In Exchange 2007 und Exchange 2010 konnten Sie angeben, welche Benutzer Zugriff auf bestimmte öffentliche Ordner hatten. In Exchange 2013 kann das standardmäßige Postfach für öffentliche Ordner auf Benutzerbasis angegeben werden. Führen Sie dazu das Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) mit dem Parameter *DefaultPublicFolderMailbox* aus.

    Set-Mailbox -Identity kweku@contoso.com -DefaultPublicFolderMailbox "PF_Administration"

## Wie wirkt sich ein Ausfall der Haupthierarchie auf die Benutzer aus?

Beim Ausfall des Haupthierarchiepostfachs für öffentliche Ordner können die Benutzer die öffentlichen Ordner anzeigen, aber nicht in sie schreiben. Ihre öffentlichen Ordner sollten Teil einer Database Availability Group (DAG) sein, um den Ausfall der Hierarchie zu verhindern. Weitere Informationen zu DAGs finden Sie unter [Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md).

## Kann geändert werden, welches Postfach für öffentliche Ordner das Haupthierarchiepostfach ist?

Nein. Wenn Sie versuchen, das Haupthierarchiepostfach zu ändern, wird ein Fehler ausgegeben.

## Verfügen öffentliche Ordner über Volltext-Suchfunktionen?

Ja, die Volltextsuche steht für öffentliche Ordner in Exchange 2013 zur Verfügung. Allerdings können Sie nicht in mehreren öffentlichen Ordnern suchen.

