---
title: 'Öffentliche Ordner: Exchange 2013 Help'
TOCTitle: Öffentliche Ordner
ms:assetid: 94c4fb69-9234-4b34-8c1c-da2a0a11da65
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150538(v=EXCHG.150)
ms:contentKeyID: 50476260
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Öffentliche Ordner

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-03-27_

Öffentliche Ordner ermöglichen den gemeinsamen Zugriff und stellen ein einfaches und effektives Mittel zum Erfassen, Organisieren und Freigeben von Informationen für andere Personen in der Arbeitsgruppe oder Organisation dar. Dieser Inhalt wird mithilfe öffentlicher Ordner in einer Hierarchie angeordnet, die einfach zu durchsuchen ist. Benutzern wird die vollständige Hierarchie in Outlook angezeigt, sodass sie sie leicht nach den Inhalten durchsuchen können, an denen sie interessiert sind.


> [!NOTE]
> Öffentliche Ordner stehen in den folgenden Outlook-Clients zur Verfügung: Outlook Web App für Exchange 2013, Outlook 2007, Outlook 2010, Outlook 2013 und Outlook für Mac.



Öffentliche Ordner können auch als Archivierungsmethode für Verteilergruppen verwendet werden. Wenn Sie einen öffentlichen Ordner für E-Mail aktivieren und der Verteilergruppe hinzufügen, werden an die Gruppe gesendete E-Mails automatisch dem öffentlichen Ordner hinzugefügt, damit sie später zur Verfügung stehen.


> [!NOTE]
> Für den Zugriff auf öffentliche Ordner auf Servern mit Exchange 2013 müssen Sie Outlook&nbsp;2007 oder höher verwenden.



Öffentliche Ordner sind nicht für Folgendes ausgelegt:

  - **Datenarchivierung** Benutzer, die Postfachbeschränkungen beachten müssen, verwenden zum Archivieren von Daten manchmal öffentliche Ordner anstelle von Postfächern. Diese Vorgehensweise wird nicht empfohlen, da dadurch Speicherplatz in öffentlichen Ordnern belegt wird und Postfachbeschränkungen ihren Sinn verlieren. Stattdessen wird die Verwendung von [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md) als Archivierungslösung empfohlen.

  - **Gemeinsame Nutzung von Dokumenten und Zusammenarbeit** Öffentliche Ordner stellen keine Versionsverwaltung oder andere Dokumentverwaltungsfunktionen wie z. B. gesteuerte Eincheck- und Auscheckfunktionen oder automatische Benachrichtigungen bei Inhaltsänderungen zur Verfügung. Stattdessen wird [SharePoint](https://go.microsoft.com/fwlink/?linkid=282474) als Dokumentfreigabelösung empfohlen.

Unter [Zusammenarbeit](collaboration-exchange-2013-help.md) finden Sie weitere Informationen zu öffentlichen Ordnern und anderen Methoden für die Zusammenarbeit in Exchange 2013.

Einige häufig gestellte Fragen zu öffentlichen Ordnern in Exchange 2013 finden Sie unter [FAQ: Öffentliche Ordner](faq-public-folders-exchange-2013-help.md).

Weitere Informationen zu den Grenzwerten und Kontingenten für öffentliche Ordner finden Sie unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md).

Eine Liste der Verwaltungsaufgaben für öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Sie suchen die Exchange Online-Version dieses Artikels? Lesen Sie [Öffentliche Ordner in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj200758\(v=exchg.150\)).

**Inhalt**

Architektur für öffentliche Ordner

Migrieren öffentlicher Ordner

Verschieben öffentlicher Ordner

Kontingente für öffentliche Ordner

Notfallwiederherstellung

## Architektur für öffentliche Ordner

In Exchange 2013 wurden öffentliche Ordner unter Einbeziehung der Postfachinfrastruktur weiterentwickelt, um in den Genuss der Hochverfügbarkeits- und Speichertechnologien der Postfachdatenbank zu kommen. Die Architektur für öffentliche Ordner verwendet speziell entworfene Postfächer, um sowohl die Hierarchie öffentlicher Ordner als auch ihren Inhalt zu speichern. Dies bedeutet auch, dass keine Datenbank für öffentliche Ordner mehr vorhanden ist. Die hohe Verfügbarkeit der Postfächer für öffentliche Ordner wird durch eine Database Availability Group (DAG) ermöglicht. Weitere Informationen zu DAGs finden Sie unter [Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md).

Die Hauptarchitekturkomponente öffentlicher Ordner sind Postfächer für öffentliche Ordner, die sich in einer oder mehreren Postfachdatenbanken befinden können.

## Postfächer für öffentliche Ordner

Es gibt zwei Arten von Postfächern für öffentliche Ordner: das *primäre Hierarchiepostfach* und die *sekundären Hierarchiepostfächer*. Beide Arten von Postfächern können Inhalte enthalten:

  - **Primäres Hierarchiepostfach**   Das primäre Hierarchiepostfach ist die einzige schreibbare Kopie der Hierarchie öffentlicher Ordner. Die Hierarchie öffentlicher Ordner wird auch in alle anderen Postfächer öffentlicher Ordner kopiert, ist dort jedoch schreibgeschützt.

  - **Sekundäre Hierarchiepostfächer**   Sekundäre Hierarchiepostfächer enthalten ebenfalls Inhalte öffentlicher Ordner sowie eine schreibgeschützte Kopie der Hierarchie öffentlicher Ordner.


> [!NOTE]
> Aufbewahrungsrichtlinien werden für Postfächer öffentlicher Ordner nicht unterstützt.



Es gibt zwei Möglichkeiten, Postfächer öffentlicher Ordner zu verwalten:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Öffentliche Ordner** \> **Postfächer für den öffentlichen Ordner**.

  - Verwenden Sie in der Exchange-Verwaltungsshell den Cmdlet-Satz **\*-Mailbox**. Die folgenden Parameter wurden dem Cmdlet [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)) hinzugefügt, um Postfächer für öffentliche Ordner zu unterstützen:
    
      - *PublicFolder*   Dieser Parameter wird mit dem Cmdlet **New-Mailbox** verwendet, um ein Postfach für öffentliche Ordner zu erstellen. Wenn Sie ein Postfach für öffentliche Ordner erstellen, wird ein neues Postfach mit dem Postfachtyp `PublicFolder` erstellt. Weitere Informationen finden Sie unter [Erstellen eines Postfachs für öffentliche Ordner](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/create-public-folder-mailbox).
    
      - *HoldForMigration*   Dieser Parameter kommt nur zum Einsatz, wenn Sie öffentliche Ordner aus einer früheren Version zu Exchange 2013 migrieren. Weitere Informationen finden Sie unter Migrieren öffentlicher Ordner weiter unten in diesem Thema.
    
      - *IsHierarchyReady*   Dieser Parameter gibt an, ob das Postfach für öffentliche Ordner bereit ist, Benutzern die Hierarchie öffentlicher Ordner bereitzustellen. Er wird erst dann auf `$True` gesetzt, wenn die gesamte Hierarchie mit dem Postfach für öffentliche Ordner synchronisiert wurde. Wenn der Parameter auf $False gesetzt ist, wird er von Benutzern beim Zugriff auf die Hierarchie nicht verwendet. Wenn Sie aber die Eigenschaft *DefaultPublicFolderMailbox* für ein Benutzerpostfach auf ein bestimmtes Postfach für öffentliche Ordner festlegen, kann der Benutzer auch dann auf das angegebene Postfach für öffentliche Ordner zugreifen, wenn der Parameter *IsHierarchyReady* auf `$False` festgelegt ist.
    
      - *IsExcludedFromServingHierarchy*   Dieser Parameter hindert Benutzer am Zugriff auf die Hierarchie öffentlicher Ordner für das angegebene Postfach für öffentliche Ordner. Standardmäßig werden Benutzer zum Lastenausgleich gleichmäßig über Postfächer für öffentliche Ordner verteilt. Ist dieser Parameter für ein Postfach für öffentliche Ordner festgelegt, wird dieses Postfach bei diesem automatischen Lastenausgleich nicht berücksichtigt, und Benutzer greifen zum Abrufen der Hierarchie öffentlicher Ordner nicht darauf zu. Wenn Sie jedoch die Eigenschaft *DefaultPublicFolderMailbox* für ein Benutzerpostfach auf ein bestimmtes Postfach für öffentliche Ordner festgelegt haben, greift der Benutzer auch dann noch auf das angegebene Postfach für öffentliche Ordner zu, wenn der Parameter *IsExcludedFromServingHierarchy* für das jeweilige Postfach für öffentliche Ordner festgelegt wurde.

Ein sekundäres Hierarchiepostfach stellt Benutzern nur Informationen der öffentlichen Ordnerhierarchie bereit, wenn dies explizit für die Benutzerpostfächer mithilfe der Eigenschaft *DefaultPublicFolderMailbox* festgelegt wurde oder wenn die folgenden Bedingungen zutreffen:

  - Die Eigenschaft *IsHierarchyReady* ist für das Postfach für öffentliche Ordner auf `$True` gesetzt.

  - Die Eigenschaft *IsExcludedFromServingHierarchy* ist für das Postfach für öffentliche Ordner auf `$False` festgelegt.

## Hierarchie öffentlicher Ordner

Die Hierarchie öffentlicher Ordner enthält die Eigenschaften der Ordner sowie organisatorische Informationen einschließlich der Baumstruktur. Jedes Postfach für öffentliche Ordner enthält eine Kopie der Hierarchie öffentlicher Ordner. Es gibt nur eine schreibbare Kopie der Hierarchie. Diese befindet sich im primären Postfach für öffentliche Ordner. Für einen bestimmten Ordner werden die Hierarchiedaten zum Identifizieren der folgenden Informationen verwenden:

  - Berechtigungen für den Ordner

  - Die Position des Ordners in der Struktur für öffentliche Ordner einschließlich der über- und untergeordneten Ordner


> [!NOTE]
> In der Hierarchie werden keine Informationen zu E-Mail-Adressen für E-Mail-aktivierte öffentliche Ordner gespeichert. Die E-Mail-Adressen werden im Verzeichnisobjekt in Active Directory gespeichert.



## Hierarchiesynchronisierung

Beim Synchronisierungsvorgang für die Hierarchie öffentlicher Ordner wird ICS (Incremental Change Synchronization) verwendet. So wird ein Mechanismus für die Überwachung und Synchronisierung von Änderungen an einer Exchange-Speicherhierarchie oder an Inhalten bereitgestellt. Die Änderungen umfassen das Erstellen, Ändern und Löschen von Ordnern und Nachrichten. Wenn Benutzer Verbindungen zu Inhaltspostfächern hergestellt haben und diese verwenden, tritt die Synchronisierung alle 15 Minuten auf. Wenn keine Benutzer über eine Verbindung zu einem Inhaltspostfach verfügen, wird die Synchronisierung weniger häufig ausgelöst (alle 24 Stunden). Wenn ein Schreibvorgang, wie die Erstellung eines Ordners, in der primären Hierarchie durchgeführt wird, wird die Synchronisierung zum Inhaltspostfach sofort (synchron) ausgelöst.


> [!IMPORTANT]
> Da nur eine schreibbare Kopie der Hierarchie vorhanden ist, wird die Ordnererstellung durch das Inhaltspostfach, mit dem Benutzer verbunden sind, an das Hierarchiepostfach weitergegeben.



In einer großen Organisation muss die Hierarchie, wenn Sie ein neues Postfach für öffentliche Ordner erstellen, mit diesem öffentlichen Ordner synchronisiert werden, bevor Benutzer eine Verbindung damit herstellen können. Andernfalls wird Benutzern ggf. eine unvollständige Struktur öffentlicher Ordner angezeigt, wenn Sie eine Verbindung mit Outlook herstellen. Damit für diese Synchronisierung genug Zeit bleib, ehe Benutzer versuchen, sich mit dem neuen Postfach für öffentliche Ordner zu verbinden, legen Sie den Parameter *IsExcludedFromServingHierarchy* für das Cmdlet **New-Mailbox** fest, wenn Sie das Postfach für öffentliche Ordner erstellen. Dieser Parameter hindert Benutzer am Herstellen einer Verbindung mit dem neu erstellten Postfach für öffentliche Ordner. Führen Sie nach Abschluss der Synchronisierung das Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) mit dem auf `false` festgelegten Parameter *IsExcludedFromServingHierarchy* aus, um anzugeben, dass eine Verbindung mit dem Postfach für öffentliche Ordner hergestellt werden kann. Sie können auch mithilfe des Cmdlets [Get-PublicFolderMailboxDiagnostics](https://technet.microsoft.com/de-de/library/jj218720\(v=exchg.150\)) den Synchronisierungsstatus anhand der Parameter *SyncInfo* und *AssistantInfo* anzeigen.

Weitere Informationen finden Sie unter [Erstellen eines öffentlichen Ordners](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/create-public-folder).

## Inhalte öffentlicher Ordner

Inhalte öffentlicher Ordner können E-Mails, Beiträge, Dokumente und eForms einschließen. Die Inhalte werden im Postfach des öffentlichen Ordners gespeichert, werden jedoch nicht in mehrere Postfächer öffentlicher Ordner repliziert. Alle Benutzer greifen auf dasselbe Postfach für öffentliche Ordner zu, um dieselben Inhalte abzurufen. Zwar steht eine Volltextsuche im Inhalt eines öffentlichen Ordners zur Verfügung; Inhalte sind jedoch nicht über öffentliche Ordner hinweg durchsuchbar und werden nicht von der Exchange-Suche indiziert.


> [!NOTE]
> Outlook Web App wird unterstützt, aber mit Einschränkungen. Sie können öffentliche Ordner als Favoriten hinzufügen und entfernen und Vorgänge auf Elementebene durchführen, wie das Erstellen, Bearbeiten, Löschen und Beantworten von Beiträgen. Sie können jedoch öffentliche Ordner nicht über Outlook Web App erstellen oder löschen. Außerdem können nur öffentliche E-Mail-, Post-, Kalender oder Kontaktordner zur Favoritenliste in Outlook Web App hinzugefügt werden.



## Migrieren öffentlicher Ordner

Sie können Ihre öffentlichen Ordner von früheren Exchange Server-Versionen zu Exchange 2013 migrieren oder von früheren Exchange Server-Versionen zu Exchange Online. Ebenso können Sie Exchange 2013-basierte öffentliche Ordner zu Exchange Online migrieren.

Wenn in Ihrer Organisation vor der Installation von Exchange 2013 bereits Exchange 2010 SP3- oder Exchange 2007 SP3 RU10-basierte öffentliche Ordner vorhanden sind, müssen Sie diese öffentlichen Ordner zu Exchange 2013 migrieren. Verwenden Sie hierzu den Cmdlet-Satz **PublicFolderMigrationRequst**. Weitere Informationen finden Sie unter [Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen](use-batch-migration-to-migrate-public-folders-to-exchange-2013-from-previous-versions-exchange-2013-help.md). Falls Ihre Organisation zu Exchange Online wechselt, können Sie die öffentlichen Ordner zur Cloud migrieren und dabei gleichzeitig aktualisieren. Details hierzu finden Sie unter [Verwenden der Stapelmigration zum Migrieren von öffentlichen Ordnern einer Vorgängerversion zu Office 365 und Exchange Online](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/batch-migration-of-legacy-public-folders) und [Migrieren von Exchange 2013-basierten öffentlichen Ordnern zu Exchange Online mithilfe einer Batchmigration](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/batch-migration-of-exchange-2013-public-folders).

Aufgrund der Änderungen an der Speicherung öffentlicher Ordner können ältere Exchange-Postfächer nicht mehr auf die Hierarchie öffentlicher Ordner auf Exchange 2013-Servern oder in Exchange Online zugreifen. Benutzerpostfächer auf Exchange 2013-Servern oder in Exchange Online können jedoch eine Verbindung mit älteren öffentlichen Ordnern herstellen. Öffentliche Exchange 2013-Ordner und ältere öffentliche Ordner dürfen in Ihrer Exchange-Organisation nicht gleichzeitig vorhanden sein. Dies bedeutet, dass keine Koexistenz zwischen Versionen möglich ist. Das Migrieren öffentlicher Ordner zu Exchange Server 2013 oder Exchange Online ist derzeit ein einmaliger Umstellungsprozess.

Aus diesem Grund wird empfohlen, dass Sie vor der Migration Ihrer öffentlichen Ordner zunächst Ihre älteren Postfächer zu Exchange 2013 oder Exchange Online migrieren. Weitere Informationen zur Postfachmigration finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md), [Durchführen einer Übernahmemigration von E-Mails zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=536689) und [Durchführen einer mehrstufigen Migration von E-Mails zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=536687).

## Verschieben öffentlicher Ordner

Sie können öffentliche Ordner in ein anderes Postfach für öffentliche Ordner oder Postfächer für öffentliche Ordner in eine andere Postfachdatenbank verschieben. Mithilfe der Cmdlet-Gruppe **PublicFolderMoveRequest** können Sie öffentliche Ordner in andere Postfächer für öffentliche Ordner verschieben. Unterordner unter dem öffentlichen Ordner, der verschoben wird, werden nicht standardmäßig verschoben. Wenn Sie eine Verzweigung öffentlicher Ordner verschieben möchten, können Sie das Skript `Move-PublicFolderBranch.ps1` verwenden, das standardmäßig mit Exchange 2013 installiert wird. Weitere Informationen finden Sie unter [Verschieben eines öffentlichen Ordners in ein anderes Postfach für öffentliche Ordner](move-a-public-folder-to-a-different-public-folder-mailbox-exchange-2013-help.md).

Mithilfe der Cmdlet-Gruppe **MoveRequest** können Sie Postfächer für öffentliche Ordner in andere Postfachdatenbanken verschieben. Dies ist dieselbe Cmdlet-Gruppe, die auch zum Verschieben normaler Postfächer verwendet wird. Weitere Informationen finden Sie unter [Verschieben eines Postfachs für öffentliche Ordner in eine andere Postfachdatenbank](move-a-public-folder-mailbox-to-a-different-mailbox-database-exchange-2013-help.md).

Die Cmdlets **PublicFolderMoveRequest** und **MoveRequest** verwenden den Postfachreplikationsdienst zum asynchronen Verschieben öffentlicher Ordner. Dies bedeutet, dass das Cmdlet nicht die tatsächliche Arbeit ausführen und dass während des Verschiebungsvorgangs der öffentliche Ordner und die Postfächer für öffentliche Ordner den Benutzern weiter zur Verfügung stehen. Da der Postfachreplikationsdienst Postfachverschiebungen, Import- und Exportanforderungen und Anforderungen zur Verschiebung öffentlicher Ordner durchführt, muss die Verwaltung von Einschränkungen und Arbeitslasten berücksichtigt werden:

## Kontingente für öffentliche Ordner

Bei ihrer Erstellung übernehmen Postfächer für öffentliche Ordner automatische die Größeneinschränkungen in den Standardeinstellungen der Postfachdatenbank. Um also den aktuellen Speicherkontingentstatus bei Verwenden des Cmdlets [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) präzise bewerten zu können, müssen Sie die Eigenschaft *UseDatabaseQuotaDefaults* zusätzlich zu den Eigenschaften *ProhibitSendQuota*, *ProhibitSendReceiveQuota* und *IssueWarningQuota* überprüfen. Wenn die Eigenschaft *UseDatabaseQuotaDefaults* auf `true` festgelegt ist, werden die postfachbezogenen Einstellungen ignoriert und die Einschränkungen für die Postfachdatenbank verwendet. Wenn diese Eigenschaft auf `true` und die Eigenschaften *ProhibitSendQuota*, *ProhibitSendReceiveQuota* und *IssueWarningQuota* auf `unlimited` festgelegt sind, ist die Postfachgröße nicht wirklich uneingeschränkt. Sie müssen stattdessen das Cmdlet **Get-MailboxDatabase** verwenden und die Speichergrenzwerte für die Postfachdatenbank überprüfen, um herauszufinden, welche Grenzwerte für das Postfach gelten. Wenn die Eigenschaft *UseDatabaseQuotaDefaults* auf `false` festgelegt ist, werden die postfachbezogenen Einstellungen verwendet. In Exchange 2013 gelten standardmäßig die folgenden Kontingentgrenzen für Postfachdatenbanken:

  - *Kontingent für Problemwarnung*: 1,9 GB

  - *Kontingent für Senden verbieten*: 2 GB

  - *Kontingent für Empfangen verbieten*: 2,3 GB

Führen Sie das Cmdlet [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)) aus, um die Kontingente für Postfachdatenbanken zu bestimmen:

Verwenden Sie das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)), um die Kontingente für ein Postfach für öffentliche Ordner festzulegen.

## Notfallwiederherstellung

Öffentliche Ordner in Exchange 2013 basieren auf der Postfachinfrastruktur und verwenden dieselben Mechanismen für Verfügbarkeit und Redundanz. Jedes Postfach für öffentliche Ordner kann wie normale Postfächer über mehrere redundante Kopien mit automatischem Failover verfügen. Weitere Informationen finden Sie unter [Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md).

Zusätzlich zum allgemeinen Szenario für die Notfallwiederherstellung können Sie öffentliche Ordner auch in den folgenden Situationen wiederherstellen:

  - **Wiederherstellung eines vorläufig gelöschten öffentlichen Ordners**   Der öffentliche Ordner wurde gelöscht, ohne dass der Aufbewahrungszeitraum abgelaufen ist.

  - **Wiederherstellung eines vorläufig gelöschten Postfachs für öffentliche Ordner**   Das Postfach für öffentliche Ordner wurde gelöscht, ohne dass der Aufbewahrungszeitraum für das Postfach abgelaufen ist.

  - **Wiederherstellung eines Postfachs für öffentliche Ordner aus einer Wiederherstellungsdatenbank**   Sie können ein einzelnes Postfach für öffentliche Ordner aus einer Sicherung wiederherstellen, wenn der Aufbewahrungszeitraum des gelöschten Postfachs abgelaufen ist. Anschließend extrahieren Sie Daten aus dem wiederhergestellten Postfach und kopieren sie in einen Zielordner oder führen sie mit einem anderen Postfach zusammen.

In allen diesen Situationen kann der öffentliche Ordner bzw. das Postfach für öffentliche Ordner mithilfe der Cmdlets **MailboxRestoreRequest** wiederhergestellt werden.

Weitere Informationen finden Sie unter [Wiederherstellen von öffentlichen Ordnern und Postfächern für öffentliche Ordner aus fehlerhaften Verschiebungen](restore-public-folders-and-public-folder-mailboxes-from-failed-moves-exchange-2013-help.md).

