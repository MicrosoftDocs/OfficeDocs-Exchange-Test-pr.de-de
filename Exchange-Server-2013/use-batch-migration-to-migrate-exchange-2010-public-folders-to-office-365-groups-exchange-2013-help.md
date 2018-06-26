---
title: 'Verwenden der Stapelmigration zum Migrieren von öffentlichen Exchange 2010-Ordnern zu Office 365-Gruppen: Exchange 2013 Help'
TOCTitle: Verwenden der Stapelmigration zum Migrieren von öffentlichen Exchange 2010-Ordnern zu Office 365-Gruppen
ms:assetid: d018558d-3075-4dd3-9ff7-91ce66b8d5fb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt843875(v=EXCHG.150)
ms:contentKeyID: 74468753
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwenden der Stapelmigration zum Migrieren von öffentlichen Exchange 2010-Ordnern zu Office 365-Gruppen

 

_**Gilt für:**Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2018-04-30_

**Zusammenfassung:** Verschieben von öffentlichen Exchange 2010-Ordnern in Office 365-Gruppen.

Mit einem Prozess, der auch *Stapelmigration* genannt wird, können Sie einige oder alle Ihre öffentlichen Exchange 2010-Ordner in Office 365-Gruppen verschieben. Gruppen ist ein neues Angebot von Microsoft für die Zusammenarbeit, das bestimmte Vorteile für öffentliche Ordner bietet. Unter [Migrieren Ihrer öffentlichen Ordner zu Office 365-Gruppen](migrate-your-public-folders-to-office-365-groups-exchange-2013-help.md) finden Sie einen Überblick über die Unterschiede zwischen öffentlichen Ordnern und Gruppen sowie Gründe, warum Ihre Organisation möglicherweise von einem Wechsel zu Gruppen profitieren kann.

Dieser Artikel enthält die schrittweisen Verfahren zur Durchführung der tatsächlichen Stapelmigration Ihrer öffentlichen Exchange 2010-Ordner.

## Was sollten Sie wissen, bevor Sie beginnen?

Stellen Sie sicher, dass alle der folgenden Bedingungen erfüllt sind, bevor Sie mit der Vorbereitung der Migration beginnen.

  - Auf dem Exchange 2010-Server muss **Exchange 2010 SP3 RU8** oder höher ausgeführt werden.

  - In Exchange Online müssen Sie Mitglied der Rollengruppe „Organisationsverwaltung\&quot; sein. Diese Rollengruppe unterscheidet sich von den Berechtigungen, die Ihnen zugewiesen wurden, als Sie Office 365 oder Exchange Online abonniert haben. Details dazu, wie Sie die Rollengruppe „Organisationsverwaltung\&quot; aktivieren können, finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Sie müssen in Exchange 2010 Mitglied der Rollengruppe "Organisationsverwaltung" oder "Serververwaltung RBAC" sein. Nähere Informationen finden Sie unter [Hinzufügen von Mitgliedern zu einer Rollengruppe](https://go.microsoft.com/fwlink/?linkid=299212).

  - Bevor Sie Ihre öffentliche Ordner zu Office 365-Gruppen migrieren, wird empfohlen, zuerst Benutzerpostfächer in Office 365 für diese Benutzer zu verschieben, die Zugriff auf Office 365-Gruppen nach der Migration benötigen.

  - Outlook Anywhere muss auf dem Exchange Server 2010-Server aktiviert sein, der als Host für Ihre öffentlichen Ordnerdatenbanken dient. Weitere Informationen zum Aktivieren von Outlook Anywhere auf Exchange 2010-Servern finden Sie unter [Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=187249).

  - Dieses Verfahren kann nicht mithilfe des Exchange Admin Centers (EAC) oder der Exchange-Verwaltungskonsole (EMC) ausgeführt werden. Sie müssen auf den Exchange 2010-Servern die Exchange-Verwaltungsshell verwenden. Für Exchange Online müssen Sie die Exchange Online PowerShell verwenden. Weitere Informationen finden Sie unter [Verbinden mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/library/jj984289\(v=exchg.150\).aspx).

  - Derzeit können nur öffentliche Ordner des Typs Kalender und E-Mail zu Office 365-Gruppen migriert werden. Die Migration anderer Arten öffentlicher Ordner wird nicht unterstützt. Darüber hinaus sollten die Zielgruppen in Office 365 vor der Migration erstellt werden.

  - Bei der Stapelmigration werden nur Nachrichten- und Kalenderelemente aus öffentlichen Ordnern für die Migration zu Office 365-Gruppen kopiert. Es werden keine anderen Entitäten von öffentlichen Ordnern wie Richtlinien, Regeln und Berechtigungen kopiert.

  - Office 365-Gruppen verfügen über ein Postfach mit 50 GB Speicherplatz. Stellen Sie sicher, dass die Summe der Daten aus öffentlichen Ordnern, die Sie migrieren möchten, maximal 50 GB beträgt. Lassen Sie zudem Speicherplatz frei, damit Benutzer nach der Migration, zusätzliche Inhalte hinzufügen können. Es wird empfohlen, keine öffentlichen Ordner zu migrieren, die eine Gesamtgröße von 25 GB überschreiten.

  - Bei dieser Migration müssen Sie nicht zwangsläufig alles migrieren. Sie können bestimmte öffentliche Ordner für die Migration auswählen, damit nur diese öffentlichen Ordner migriert werden. Wenn der migrierten öffentliche Ordner Unterordner enthält, werden diese Unterordner nicht automatisch in die Migration einbezogen. Wenn Sie diese Unterordner migrieren möchten, müssen Sie sie explizit einbeziehen.

  - Die öffentlichen Ordner werden durch diese Migration in keinster Weise beeinträchtigt. Wenn Sie jedoch unser Sperrskript verwenden, um die migrierten öffentlichen Ordner mit einem Schreibschutz zu versehen, müssen die Benutzer Office 365-Gruppen anstelle von öffentlichen Ordnern verwenden.

  - Bevor Sie beginnen, sollten Sie diesen Artikel vollständig lesen, da für einige Schritte Ausfallzeiten erforderlich sind.

## Schritt 1: Abrufen der Skripts

Die Stapelmigration zu Office 365-Gruppen erfordert, wie unten in diesem Artikel beschrieben, die Ausführung einer Reihe von Skripts zu verschiedenen Zeitpunkten der Migration. Laden Sie die Skripts und die dazugehörigen unterstützenden Dateien [von diesem Speicherort](https://www.microsoft.com/en-us/download/details.aspx?id=55985) herunter. Nachdem alle Skripts und Dateien heruntergeladen wurden, speichern Sie sie am gleichen Speicherort, z. B. `c:\PFtoGroups\Scripts`.

Überprüfen Sie vor dem Fortfahren, ob Sie alle der folgenden Skripts und Dateien heruntergeladen und gespeichert haben:


> [!NOTE]
> Stellen Sie sicher, dass Sie alle Skripts und Dateien am gleichen Speicherort speichern.



  - **AddMembersToGroups.ps1**. Mit diesem Skript fügen Sie basierend auf Berechtigungseinträgen in der Quelle von öffentlichen Ordner Mitglieder und Besitzer zu Office 365-Gruppen hinzu.

  - **AddMembersToGroups.strings.psd1**. Diese Support-Datei wird vom Skript verwendet `AddMembersToGroups.ps1`.

  - **LockAndSavePublicFolderProperties.ps1**. Dieses Skript versetzt öffentliche Ordner in den schreibgeschützten Modus, um jegliche Änderungen zu verhindern, und es überträgt die E-Mail-bezogenen Eigenschaften der öffentlichen Ordner (vorausgesetzt, die öffentlichen Ordner sind E-Mail-aktiviert) auf die Zielgruppen, die E-Mails von den öffentlichen Ordnern zu den Zielgruppen umleiten. Mit diesem Skript werden zudem die Berechtigungseinträge und die E-Mail-Eigenschaften vor der Änderung gesichert.

  - **LockAndSavePublicFolderProperties.strings.psd1:** Diese Support-Datei wird vom Skript verwendet `LockAndSavePublicFolderProperties.ps1`.

  - **UnlockAndRestorePublicFolderProperties.ps1**. Mit diesem Skript werden Zugriffsrechte und E-Mail-Eigenschaften der öffentlichen Ordner mit von `LockandSavePublicFolderProperties.ps1` erstellten Sicherungsdateien wiederhergestellt.

  - **UnlockAndRestorePublicFolderProperties.strings.psd1**. Diese Support-Datei wird vom Skript verwendet `UnlockAndRestorePublicFolderProperties.ps1`.

  - **WriteLog.ps1**. Dieses Skript ermöglicht es den vorhergehenden drei Skripts, Protokolle zu schreiben.

  - **RetryScriptBlock.ps1**. Mit diesem Skript können die Skripts `AddMembersToGroups`, `LockAndSavePublicFolderProperties` und `UnlockAndRestorePublicFolderProperties` im Fall von vorübergehenden Fehlern bestimmte Aktionen wiederholen.

Details zu `AddMembersToGroups.ps1`, `LockAndSavePublicFolderProperties.ps1` und `UnlockAndRestorePublicFolderProperties.ps1` sowie den Aufgaben, die diese Skripts in Ihrer Umgebung ausführen, finden Sie unter Migrationsskripts weiter unten in diesem Artikel.

## Schritt 2: Vorbereiten der Migration

Die folgenden Schritte sind erforderlich, um Ihre Organisation für die Migration vorzubereiten:

1.  Kompilieren Sie eine Liste der öffentlichen Ordner (E-Mail- und Kalendertypen), die Sie in Office 365-Gruppen migrieren möchten.

2.  Erstellen Sie eine Liste der entsprechenden Zielgruppen für jeden öffentlichen Ordner, der migriert werden soll. Sie können entweder eine neue Gruppe in Office 365 für jeden öffentlichen Ordner erstellen oder eine vorhandene Gruppe verwenden. Wenn Sie eine neue Gruppe erstellen, erfahren Sie unter [Weitere Informationen zu Office 365-Gruppen](https://go.microsoft.com/fwlink/p/?linkid=858521) mehr über die für eine Gruppe erforderlichen Einstellungen. Wenn bei einem öffentlichen Ordner, den Sie migrieren, die Standardberechtigung auf **Author** oder höher eingestellt ist, sollten Sie die entsprechende Gruppe in Office 365 mit der Datenschutzeinstellung **Öffentlich** erstellen. Benutzer, die die öffentliche Gruppe unter dem Knoten der **Gruppen** in Outlook anzeigen, müssen jedoch weiterhin der Gruppe beitreten.

3.  Benennen Sie alle öffentlichen Ordner um, die einen umgekehrten Schrägstrich (**\\**) im Namen enthalten. Andernfalls werden diese öffentlichen Ordner möglicherweise nicht ordnungsgemäß migriert.

4.  Die Migrationsfunktion **PAW** muss für Ihren Office 365-Mandanten aktiviert sein. Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um dies zu überprüfen:
    
        Get-MigrationConfig
    
    Wenn in der Ausgabe unter **Features** der Eintrag **PAW** aufgeführt ist, ist die Funktion aktiviert und Sie können mit *Schritt 3: Generieren der CSV-Datei* fortfahren.
    
    Falls PAW für Ihren Mandanten noch nicht aktiviert ist, sind möglicherweise bereits Migrationsbatches vorhanden (entweder Batches mit öffentlichen Ordnern oder Benutzerbatches). Diese Batches könnten jeden Status haben, auch den Status „Abgeschlossen\&quot;. Sie müssen alle möglicherweise vorhandenen Migrationsbatches abschließen und entfernen, bis bei der Ausführung von `Get-MigrationBatch` keine Datensätze mehr zurückgegeben werden. Sobald Sie alle vorhandenen Batches entfernt haben, sollte PAW automatisch aktiviert werden. Es kann sein, dass die Änderung nicht sofort in der Ausgabe von `Get-MigrationConfig` sichtbar ist; das ist jedoch kein Problem. Bei Benutzermigrationen können Sie nach diesem Schritt mit der Erstellung neuer Batches fortfahren.

## Schritt 3: Generieren der CSV-Datei

Erstellen Sie eine CSV-Datei, um die Eingabe für eines der Migrationsskripts bereitzustellen.

Die CSV-Datei muss die folgenden Spalten enthalten:

  - **FolderPath**. Der Pfad des öffentlichen Ordners, der migriert werden soll.

  - **TargetGroupMailbox**. Die SMTP-Adresse der Zielgruppe in Office 365. Sie können den folgenden Befehl ausführen, um die primäre SMTP-Adresse anzuzeigen.
    
        Get-UnifiedGroup <alias of the group> | Format-Table PrimarySmtpAddress

CSV-Beispieldatei:

    "FolderPath","TargetGroupMailbox"
    "\Sales","sales@contoso.onmicrosoft.com"
    "\Sales\EMEA","emeasales@contoso.onmicrosoft.com"

Beachten Sie, dass ein E-Mail-Ordner und ein Kalenderordner in einer einzigen Gruppe in Office 365 zusammengeführt werden können. Alle anderen Szenarien, bei denen mehrere öffentliche Ordnern in einer einzigen Gruppe zusammenführt werden, werden in einem einzigen Migrationsbatch nicht unterstützt. Wenn Sie mehrere öffentliche Ordner der gleichen Office 365-Gruppe zuordnen müssen, können Sie zu diesem Zweck unterschiedliche Migrationsbatches fortlaufend und nacheinander ausführen. Jedes Migrationsbatch kann bis zu 500 Einträge umfassen.

Ein öffentliche Ordner sollte nur in eine Gruppe in einem Migrationsbatch migriert werden.

## Schritt 4: Starten der Migrationsanforderung

In diesem Schritt sammeln Sie Informationen aus Ihrer Exchange-Umgebung. Dann verwenden Sie diese Informationen, um ein Exchange Online PowerShell Migrationsbatch zu erstellen. Anschließend starten Sie die Migration.

1.  Führen Sie auf dem Exchange 2010-Server die folgenden Befehle zum Sammeln von Informationen aus, die erforderlich sind, um das Migrationsbatch zu erstellen:
    
    1.  Suchen Sie den **LegacyExchangeDN** für das Konto des Benutzers, der Mitglied der Administratorrolle für öffentliche Ordner ist, indem Sie den folgenden Befehl eingeben. Dies ist der gleiche Benutzer, dessen Anmeldeinformationen Sie in Schritt 3 dieses Verfahrens benötigen.
        
            Get-Mailbox <PublicFolder_Administrator_Account> | Select-Object LegacyExchangeDN
    
    2.  Suchen Sie den LegacyExchangeDN jedes Postfachservers mit einer Datenbank für öffentliche Ordner, indem Sie den folgenden Befehl eingeben:
        
            Get-ExchangeServer <public folder server> | Select-Object -Expand ExchangeLegacyDN
    
    3.  Suchen Sie den Vollqualifizierten Domänennamen (FQDN) des Outlook Anywhere-Hosts. Dabei handelt es sich um den externen Hostnamen. Wenn Sie mehrere Instanzen von Outlook Anywhere besitzen, sollten Sie entweder die Instanz wählen, die sich am nächsten am Migrationsendpunkt oder am nächsten an den Repliken der öffentlichen Ordner Ihrer Exchange Server 2010-Organisation befindet. Mit dem folgenden Befehl finden Sie alle Instanzen von Outlook Anywhere:
        
            Get-OutlookAnywhere | Format-Table Identity, ExternalHostName

2.  Verwenden Sie in Exchange Online PowerShell die Informationen, die in Schritt 1 zum Ausführen der folgenden Befehle zurückgegeben wurden. Die Variablen dieser Befehle sind Werte aus Schritt 1.
    
    1.  Übergeben Sie die Anmeldeinformationen eines Benutzers, der in der Exchange 2010-Umgebung über Administratorberechtigungen verfügt, an die Variable `$Source_Credential`. Wenn Sie die Migrationsanforderung schließlich in Exchange Online ausführen, verwenden Sie diese Anmeldeinformationen, um über Outlook Anywhere auf Ihre Exchange 2010-Server zuzugreifen und die Inhalte nach Exchange Online zu kopieren.
        
            $Source_Credential = Get-Credential
            <source_domain>\<PublicFolder_Administrator_Account>
    
    2.  Verwenden Sie den ExchangeLegacyDN des Migrationsbenutzers auf dem Exchange-Legacyserver, den Sie in Schritt 1a gefunden haben, und geben Sie diesen Wert an die Variable weiter`$Source_RemoteMailboxLegacyDN`.
        
            $Source_RemoteMailboxLegacyDN = "<LegacyExchangeDN from step 1a>"
    
    3.  Verwenden Sie den ExchangeLegacyDN des öffentlichen Ordnerservers, den Sie in Schritt 1b gefunden haben, und geben Sie diesen Wert an die Variable `$Source_RemotePublicFolderServerLegacyDN` weiter.
        
            $Source_RemotePublicFolderServerLegacyDN = "<LegacyExchangeDN from step 1b>"
    
    4.  Verwenden Sie den externen Hostnamen von Outlook Anywhere, der in Schritt 1c zurückgegeben wurde, und geben diesen Wert an die Variable `$Source_OutlookAnywhereExternalHostName` weiter.
        
            $Source_OutlookAnywhereExternalHostName = "<ExternalHostName from step 1c>"

3.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um einen Migrationsendpunkt zu erstellen:
    
        $PfEndpoint = New-MigrationEndpoint -PublicFolderToUnifiedGroup -Name PFToGroupEndpoint -RPCProxyServer $Source_OutlookAnywhereExternalHostName -Credentials $Source_Credential -SourceMailboxLegacyDN $Source_RemoteMailboxLegacyDN -PublicFolderDatabaseServerLegacyDN $Source_RemotePublicFolderServerLegacyDN -Authentication Basic

4.  Führen Sie den folgenden Befehl aus, um einen neuen öffentlichen Ordner im Office- 365-Gruppen-Migrationsbatch zu erstellen. Dabei gilt Folgendes:
    
      - **CSVData** ist die in*Schritt 3: Generieren der CSV-Datei* erstellte CSV-Datei. Achten Sie darauf, den vollständigen Pfad zu dieser Datei anzugeben. Falls die Datei aus irgendeinem Grund verschoben wurde, müssen Sie unbedingt den neuen Speicherort überprüfen und verwenden.
    
      - **NotificationEmails** ist ein optionaler Parameter, der verwendet werden kann, um E-Mail-Adressen festzulegen, an die Benachrichtigungen über den Status und Fortschritt der Migration übermittelt werden.
    
      - **AutoStart** ist ein optionaler Parameter, der verwendet wird, um den Migrationsbatch zu starten, sobald er erstellt wurde.
    
      - **PublicFolderToUnifiedGroup** ist der Parameter, in dem angegeben ist, dass es sich um einen öffentlichen Ordner des Office 365-Gruppen-Migrationsbatches handelt.
    
    <!-- end list -->
    
        New-MigrationBatch -Name PublicFolderToGroupMigration -CSVData (Get-Content <path to .csv file> -Encoding Byte) -PublicFolderToUnifiedGroup -SourceEndpoint $PfEndpoint.Identity [-NotificationEmails <email addresses for migration notifications>] [-AutoStart]

5.  Starten Sie die Migration mit dem folgenden Befehl Exchange Online PowerShell. Beachten Sie, dass dieser Schritt nur erforderlich ist, wenn der `-AutoStart`-Parameter beim Erstellen des Batches in Schritt 4 nicht verwendet wird.
    
        Start-MigrationBatch PublicFolderToGroupMigration

Batchmigrationen müssen zwar mit `New-MigrationBatch` Cmdlet in Exchange Online PowerShell erstellt werden, der Fortschritt der Migration wird jedoch in Exchange-Verwaltungskonsole angezeigt und verwaltet. Sie können den Fortschritt der Migration auch anzeigen, indem Sie die Cmdlets [Get-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219164\(v=exchg.150\)) und [Get-MigrationUser](https://technet.microsoft.com/de-de/library/jj218702\(v=exchg.150\)) ausführen. Das Cmdlet `New-MigrationBatch` initiiert eines Migrationsbenutzer für jedes Postfach der Office 365-Gruppe, und Sie können den Status dieser Anfragen auf der Seite der Postfachmigration anzeigen.

So zeigen Sie die Seite der Postfachmigration an:

1.  Öffnen Sie in Exchange Online Exchange-Verwaltungskonsole.

2.  Navigieren Sie zu **Empfänger**, und wählen Sie **Migration** aus.

3.  Wählen Sie die soeben erstellte Migrationsanforderung aus, und klicken Sie im Bereich **Details** auf **Details anzeigen**.

Wenn der Batchstatus **Abgeschlossen** lautet, können Sie mit *Schritt 5 fortfahren: Fügen Sie Mitglieder aus öffentlichen Ordnern zu Office 365-Gruppen hinzu*.

## Schritt 5: Hinzufügen von Mitglieder aus öffentlichen Ordnern zu Office 365-Gruppen

Sie können je nach Bedarf manuell Mitglieder zur Zielgruppe in Office 365 hinzufügen. Wenn Sie die Mitglieder jedoch basierend auf den Berechtigungseinträgen in den öffentlichen Ordnern zur Gruppe hinzufügen möchten, müssen Sie wie im folgenden Befehl dargestellt das Skript `AddMembersToGroups.ps1` auf dem Exchange 2010-Server ausführen. Benutzerpostfächer müssen mit Exchange Online synchronisiert werden, damit Sie als Mitglieder zu einer Office 365-Gruppe hinzugefügt werden. Wenn Sie wissen möchten, welche Berechtigungen für öffentliche Ordner als Mitglieder einer Gruppe in Office 365 hinzugefügt werden können, sehen Sie sich den Abschnitt Migrationsskripts weiter unten in diesem Artikel an.

Hinweise zum folgenden Befehl:

  - **MappingCsv** ist die CSV-Datei, die Sie in *Schritt 3: Generieren der CSV-Datei* erstellt haben. Achten Sie darauf, den vollständigen Pfad zu dieser Datei anzugeben. Falls die Datei aus irgendeinem Grund verschoben wurde, müssen Sie unbedingt den neuen Speicherort überprüfen und angeben.

  - **BackupDir** ist das Verzeichnis, in dem die Migrationsprotokolldateien gespeichert werden.

  - **ArePublicFoldersOnPremises** ist ein Parameter, mit dem angegeben werden kann, ob sich öffentliche Ordner auf einem lokalen Server oder in Exchange Online befinden.

  - **Credential** steht für den Benutzernamen und das Kennwort von Exchange Online.

<!-- end list -->

    .\AddMembersToGroups.ps1 -MappingCsv <path to .csv file> -BackupDir <path to backup directory> -ArePublicFoldersOnPremises $true -Credential (Get-Credential)

Sobald Benutzer zu einer Gruppe in Office 365 hinzugefügt wurden, können sie diese verwenden.

## Schritt 6: Sperren der öffentlichen Ordner (Downtime der öffentlichen Ordner erforderlich)

Wenn die Mehrzahl der Daten in Ihren öffentlichen Ordnern zu Office 365-Gruppen migriert wurde, können Sie das Skript `LockAndSavePublicFolderProperties.ps1` auf dem Exchange 2010-Server ausführen, um die öffentlichen Ordnern mit einem Schreibschutz zu versehen. Dadurch wird sichergestellt, dass keine neuen Daten zu den öffentlichen Ordnern hinzugefügt werden, bevor die Migration abgeschlossen ist.


> [!NOTE]
> Wenn in den migrierten öffentlichen Ordnern E-Mail-aktivierte öffentliche Ordner (MEPFs) vorhanden sind, werden in diesem Schritt einige Eigenschaften der MEPFs, wie z. B. SMTP-Adressen, in die entsprechende Gruppe in Office 365 kopiert und die E-Mail-Funktionen für die öffentlichen Ordner deaktiviert. Da die E-Mail-Funktionen der migrierten MEPFs nach der Ausführung dieses Skripts deaktiviert werden, werden an die MEPFs gesandte E-Mails in den entsprechenden Gruppen empfangen. Weitere Informationen hierzu finden Sie unter Migrationsskripts weiter unten in diesem Artikel.



Hinweise zum folgenden Befehl:

  - **MappingCsv** ist die CSV-Datei, die Sie in *Schritt 3: Generieren der CSV-Datei* erstellt haben. Achten Sie darauf, den vollständigen Pfad zu dieser Datei anzugeben. Falls die Datei aus irgendeinem Grund verschoben wurde, müssen Sie unbedingt den neuen Speicherort überprüfen und angeben.

  - **BackupDir** ist das Verzeichnis, in dem die Sicherungsdateien für Berechtigungseinträge, MEPF-Eigenschaften und Migrationsprotokolldateien gespeichert werden. Diese Sicherung wird nützlich sein, falls Sie einmal ein Rollback auf öffentliche Ordner durchführen müssen.

  - **ArePublicFoldersOnPremises** ist ein Parameter, mit dem angegeben werden kann, ob sich öffentliche Ordner auf einem lokalen Server oder in Exchange Online befinden.

  - **Credential** steht für den Benutzernamen und das Kennwort von Exchange Online.

<!-- end list -->

    .\LockAndSavePublicFolderProperties.ps1 -MappingCsv <path to .csv file> -BackupDir <path to backup directory> -ArePublicFoldersOnPremises $true -Credential (Get-Credential)

## Schritt 7: Fertigstellen des öffentlichen Ordners für die Migration in Office 365-Gruppen

Nachdem Sie Ihre öffentliche Ordner mit einem Schreibschutz versehen haben, müssen Sie die Migration erneut ausführen. Dies ist für eine endgültige inkrementelle Kopie der Daten erforderlich. Bevor Sie die Migration erneut ausführen können, müssen Sie den vorhandenen Batch entfernen, indem Sie den folgenden Befehl ausführen:

    Remove-MigrationBatch <name of migration batch>

Erstellen Sie anschließen einen neuen Batch mit der gleichen CSV-Datei, indem Sie den folgenden Befehl ausführen. Dabei gilt Folgendes:

  - **CSVData** ist die CSV-Datei, die Sie in *Schritt 3: Generieren der CSV-Datei* generiert haben. Achten Sie darauf, den vollständigen Pfad zu dieser Datei anzugeben. Falls die Datei aus irgendeinem Grund verschoben wurde, müssen Sie unbedingt den neuen Speicherort überprüfen und angeben.

  - **NotificationEmails** ist ein optionaler Parameter, der verwendet werden kann, um E-Mail-Adressen festzulegen, an die Benachrichtigungen über den Status und Fortschritt der Migration übermittelt werden.

  - **AutoStart** ist ein optionaler Parameter, der verwendet wird, um den Migrationsbatch zu starten, sobald er erstellt wurde.

<!-- end list -->

    New-MigrationBatch -Name PublicFolderToGroupMigration -CSVData (Get-Content <path to .csv file> -Encoding Byte) -PublicFolderToUnifiedGroup -SourceEndpoint $PfEndpoint.Identity [-NotificationEmails <email addresses for migration notifications>] [-AutoStart]

Nachdem der neue Batch erstellt wurde, starten Sie die Migration mit dem folgenden Befehl Exchange Online PowerShell. Beachten Sie, dass dieser Schritt nur notwendig ist, wenn der `-AutoStart`-Parameter nicht im vorstehenden Befehl verwendet wurde.

    Start-MigrationBatch PublicFolderToGroupMigration

Nachdem Sie diesen Schritt abgeschlossen haben (der Batchstatus lautet **Abgeschlossen**), stellen Sie sicher, dass alle Daten in die Office 365-Gruppen kopiert wurden. Wenn Sie mit der Gruppen-Erfahrung zufrieden sind, können Sie nun beginnen, die migrierten öffentlichen Ordner aus Ihrer Exchange Server 2010-Umgebung zu löschen.


> [!IMPORTANT]
> Es gibt zwar unterstützte Verfahren zum Zurücksetzen der Migration und zur Rückkehr zu öffentlichen Ordnern, dies ist jedoch nicht mehr möglich, nachdem die ursprünglichen öffentlichen Ordner gelöscht wurden. Weitere Informationen finden Sie unter Wie führe ich ein Rollback von Office 365-Gruppen zu öffentlichen Ordnern durch?.



## Bekannte Probleme

Die folgenden bekannten Probleme können während eine normale Migration von öffentlichen Ordnern zu Office 365-Gruppen auftreten.

  - Das Skript, das die SMTP-Adresse aus den E-Mail-aktivierten öffentlichen Ordnern in die Office 365-Gruppe überträgt, fügt die Adressen lediglich als sekundäre E-Mail-Adressen in Exchange Online hinzu. Wenn Sie Exchange Online Protection (EOP) oder die zentralisierte Nachrichtenübermittlung in Ihrer Umgebung eingerichtet haben, gibt es nach der Migration Probleme beim Senden von E-Mails an Gruppen (an die sekundären E-Mail-Adressen).

  - Weist die CSV-Zuordnungsdatei einen Eintrag mit ungültigem Pfad zum öffentlichen Ordner auf, wird das Migrationsbatch ohne Fehler als **abgeschlossen** angezeigt, und keine weiteren Daten werden kopiert.

## Migrationsskripts

Als Referenz enthält dieser Abschnitt detaillierte Beschreibungen für drei der Migrationsskripts und Aufgaben, die sie in Ihrer Exchange-Umgebung ausführen. Laden Sie die Skripts und die dazugehörigen unterstützenden Dateien [von diesem Speicherort](https://www.microsoft.com/en-us/download/details.aspx?id=55985) herunter.

## AddMembersToGroups.ps1

Mit diesem Skript werden die Berechtigungen der öffentlichen Ordner migriert, anschließend werden die Mitglieder und Besitzer folgendermaßen zu Office 365-Gruppen hinzugefügt:

  - Benutzer mit folgenden Berechtigungsrollen werden als Mitglieder zu einer Gruppe in Office 365 hinzugefügt. **Berechtigungsrollen:** Besitzer, PublishingEditor, Editor, PublishingAuthor, Autor

  - Darüber hinaus werden Benutzer mit den Mindestzugriffsrechten ebenfalls als Mitglieder zu einer Gruppe in Office 365 hinzugefügt. **Zugriffsrechte:** ReadItems, CreateItems, FolderVisible, EditOwnedItems, DeleteOwnedItems

  - Benutzer mit der Zugriffsberechtigung „Besitzer\&quot; werden als Besitzer einer Gruppe hinzugefügt, und Benutzer mit anderen berechtigten Zugriffsrechten werden als Mitglieder hinzugefügt.

  - Sicherheitsgruppen können nicht als Mitglieder zu Gruppen in Office 365 hinzugefügt werden. Daher werden diese erweitert, und anschließend werden die einzelnen Benutzer als Mitglieder oder Besitzer auf Grundlage der Zugriffsrechte auf die Sicherheitsgruppe zu den Gruppen hinzugefügt.

  - Wenn Benutzer mit Zugriffsrechten über einen öffentlichen Ordner in Sicherheitsgruppen selbst über ausdrückliche Berechtigungen über denselben öffentlichen Ordner verfügen, werden die ausdrücklichen Berechtigungen priorisiert behandelt. Sehen wir uns beispielsweise einen Fall an, in dem eine Sicherheitsgruppe mit der Bezeichnung „SG1\&quot; als Mitglieder Benutzer1 und Benutzer2 enthält. Berechtigungseinträge für den öffentlichen Ordner „PF1\&quot; lauten wie folgt:
    
    SG1: Autor in PF1
    
    Benutzer1: Besitzer in PF1
    
    In diesem Fall wird Benutzer1 als Besitzer zur Gruppe in Office 365 hinzugefügt werden.

  - Wenn die Standardberechtigung eines öffentlichen zu migrierenden Ordners „Autor\&quot; oder höher lautet, schlägt das Skript vor, Datenschutzeinstellungen der entsprechenden Gruppe als „Öffentlich\&quot; festzulegen.

Dieses Skript kann selbst nach dem Sperren der öffentlichen Ordner mit Parameter `ArePublicFoldersLocked` auf ` $true` festgelegt werden. In diesem Szenario liest das Skript die Berechtigungen aus der Sicherungsdatei aus, die während des Sperrens erstellt wurde.

## LockAndSavePublicFolderProperties.ps1

Dieses Skript versieht die zu migrierenden öffentlichen Ordner mit einem Schreibschutz. Beim Migrieren von E-Mail-aktivierten öffentlichen Ordnern sind sie zunächst E-Mail-deaktiviert und ihre SMTP-Adressen werden zu den entsprechenden Gruppen in Office 365 hinzugefügt. Anschließend werden die Berechtigungseinträge geändert, damit sie schreibgeschützt sind. Eine Sicherung der E-Mail-Eigenschaften der E-Mail-aktivierten öffentlichen Ordner sowie die Berechtigungseinträge aller öffentlichen Ordner werden vor dem Ausführen von Änderungen kopiert.

Wenn es mehrere Migrationsbatches gibt, sollte für jede CSV-Zuordnungsdatei ein separates Sicherungsverzeichnis verwendet werden.

Folgenden E-Mail-Eigenschaften werden zusammen mit den E-Mail-aktivierten öffentlichen Ordnern und Office 365-Gruppen gespeichert:

  - PrimarySMTPAddress

  - EmailAddresses

  - ExternalEmailAddress

  - EmailAddressPolicyEnabled

  - GrantSendOnBehalfTo

  - SendAs-Vertrauensnehmerliste

Die oben angegebenen E-Mail-Eigenschaften werden in einer CSV-Datei gespeichert, die im Rollback verwendet wird (wenn Sie zur Verwendung von öffentlichen Ordnern zurückkehren möchten, finden Sie weitere Informationen unter Wie führe ich ein Rollback von Office 365-Gruppen zu öffentlichen Ordnern durch?). Eine Momentaufnahme der Eigenschaften E-Mail-aktivierter Ordner wird außerdem in einer Datei mit der Bezeichnung PfMailProperties.csv gespeichert. Diese Datei ist für das Rollback nicht erforderlich, Sie können Sie jedoch als Referenz verwenden.

Die folgenden E-Mail-Eigenschaften werden als Teil der Sperre in die Zielgruppen migriert:

  - PrimarySMTPAddress

  - EmailAddresses

  - SendAs-Vertrauensnehmerliste

  - GrantSendOnBehalfTo

Das Skript stellt sicher, dass die PrimarySMTPAddress und EmailAddresses der zu migrierenden E-Mail-aktivierten öffentlichen Ordner als sekundäre SMTP-Adressen der entsprechenden Gruppen in Office 365 hinzugefügt werden. Darüber hinaus erhalten SendAs- und SendOnBehalfTo-Berechtigungen von Benutzern für E-Mail-aktivierte öffentliche Ordner die entsprechende Berechtigung in den entsprechenden Zielgruppen.

**Zulässige Zugriffsrechte**:

Nur folgende Zugriffsrechte sind für Benutzer zulässig, damit sichergestellt ist, dass die öffentlichen Ordner für alle Benutzer mit einem Schreibschutz versehen werden.

  - ReadItems

  - CreateSubfolders

  - FolderContact

  - FolderVisible

Die Berechtigungseinträge werden wie folgt geändert:

1.  ###  
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Vor dem Sperren</th>
    <th>Nach dem Sperren</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Keine</p></td>
    <td><p>Keine</p></td>
    </tr>
    <tr class="even">
    <td><p>AvailabilityOnly</p></td>
    <td><p>AvailabilityOnly</p></td>
    </tr>
    <tr class="odd">
    <td><p>LimitedDetails</p></td>
    <td><p>LimitedDetails</p></td>
    </tr>
    <tr class="even">
    <td><p>Mitwirkender</p></td>
    <td><p>FolderVisible</p></td>
    </tr>
    <tr class="odd">
    <td><p>Reviewer</p></td>
    <td><p>ReadItems, FolderVisible</p></td>
    </tr>
    <tr class="even">
    <td><p>NonEditingAuthor</p></td>
    <td><p>ReadItems, FolderVisible</p></td>
    </tr>
    <tr class="odd">
    <td><p>Aughor</p></td>
    <td><p>ReadItems, FolderVisible</p></td>
    </tr>
    <tr class="even">
    <td><p>Editor</p></td>
    <td><p>ReadItems, FolderVisible</p></td>
    </tr>
    <tr class="odd">
    <td><p>PublishingAuthor</p></td>
    <td><p>ReadItems, CreateSubfolders, FolderVisible</p></td>
    </tr>
    <tr class="even">
    <td><p>PublishingEditor</p></td>
    <td><p>ReadItems, CreateSubfolders, FolderVisible</p></td>
    </tr>
    <tr class="odd">
    <td><p>Besitzer</p></td>
    <td><p>ReadItems, CreateSubfolders, FolderContact, FolderVisible</p></td>
    </tr>
    </tbody>
    </table>


2.  Zugriffsrechte für Benutzer ohne Leseberechtigungen bleiben unverändert und erhalten weiterhin keine Leserechte.

3.  Für Benutzer mit benutzerdefinierten Rollen, deren Zugriffsrechte nicht ReadItems, CreateSubfolders, FolderContact oder FolderVisible lauten, werden diese entfernt. Für den Fall, dass die Benutzer nach dem Filtern keine Zugriffsrechte aus der zulässigen Liste erhalten haben, wird das Zugriffsrecht dieser Benutzer auf „Keine\&quot; festgelegt.

Möglicherweise gibt es eine Unterbrechung beim Senden von E-Mails an E-Mail-aktivierte öffentliche Ordner für den Zeitraum, wenn die Ordner E-Mail-deaktiviert sind und ihre SMTP-Adressen zu den Office 365-Gruppen hinzugefügt werden.

## UnlockAndRestorePublicFolderProperties.ps1

Dieses Skript weist die Berechtigungen auf Grundlage der Sicherungsdatei wieder den öffentlichen Ordnern zu, die während des Sperrens des öffentlichen Ordners erstellt wurde. Dieses Skript E-Mail-aktiviert zuvor E-Mail-deaktivierte öffentliche Ordner, nachdem es die SMTP-Adressen der Ordner aus den entsprechenden Gruppen in Office 365 entfernt hat. Es gibt möglicherweise eine geringe Ausfallzeit während dieses Vorgangs.

## Wie führe ich ein Rollback von Office 365-Gruppen zu öffentlichen Ordnern durch?

Für den Fall, dass Sie Ihre Meinung ändern und zu öffentliche Ordnern zurückkehren möchten, nachdem Sie Office 365-Gruppen verwendet haben, wird Ihre Umgebung durch den nachstehenden Befehl auf den Zustand vor der Migration zurückgesetzt. Ein Rollback kann ausgeführt werden, solange die Sicherungsdateien vorhanden sind und solange Sie die öffentlichen Ordner nach der Migration nicht gelöscht haben.

Führen Sie auf dem Exchange 2010-Server den folgenden Befehl aus. Dabei gilt Folgendes:

  - **BackupDir** ist das Verzeichnis, in dem die Sicherungsdateien für Berechtigungseinträge, MEPF-Eigenschaften und Migrationsprotokolldateien gespeichert werden. Vergewissern Sie sich, dass Sie denselben Speicherort verwenden, den Sie in *Schritt 6 angegeben haben: Sperren der öffentlichen Ordner (Downtime der öffentlichen Ordner erforderlich)*.

  - **ArePublicFoldersOnPremises** ist ein Parameter, mit dem angegeben werden kann, ob sich öffentliche Ordner auf einem lokalen Server oder in Exchange Online befinden.

  - **Credential** steht für den Benutzernamen und das Kennwort von Exchange Online.

<!-- end list -->

    .\UnlockAndRestorePublicFolderProperties.ps1 -BackupDir <path to backup directory> -ArePublicFoldersOnPremises $true -Credential (Get-Credential)

Beachten Sie, dass alle zu Gruppen in Office 365 hinzugefügte Elemente oder in den Gruppen durchgeführte Bearbeitungsvorgänge nicht zurück in die öffentlichen Ordner kopiert werden. Deshalb gehen Daten verloren, unter der Voraussetzung, dass neue Daten hinzugefügt wurden, als der öffentliche Ordner eine Gruppe war.

Beachten Sie außerdem, dass es nicht möglich ist, einen Teil der öffentlichen Ordner wiederherzustellen, d. h. alle öffentlichen Ordner, die migriert wurden, sollten wiederhergestellt werden.

Die entsprechenden Gruppen in Office 365 werden nicht als Teil des Rollbacks gelöscht. Sie müssen diese Gruppen manuell bereinigen oder löschen.

