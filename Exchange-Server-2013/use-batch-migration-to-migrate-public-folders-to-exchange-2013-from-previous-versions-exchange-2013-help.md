---
title: 'Batchmigration von öffentl. Ordnern zu Exchange 2013 aus vorherigen Versionen'
TOCTitle: Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen
ms:assetid: da808e27-d2b7-4fbd-915c-a600751f526c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn912663(v=EXCHG.150)
ms:contentKeyID: 64129245
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-03-26_

**Zusammenfassung:**  In diesem Artikel erfahren Sie, wie Sie öffentliche Ordner von Exchange 2007 oder Exchange Server 2010 zu Exchange 2013 verschieben.

In diesem Artikel wird die Migration öffentlicher Ordner von Exchange Server 2010 SP3 RU8 oder Exchange 2007 SP3 RU15 zu Microsoft Exchange Server 2013 CU7 oder höher in derselben Gesamtstruktur beschrieben.

Server mit Exchange 2010 SP3 RU8 und Exchange 2007 SP3 RU15 werden als *Exchange-Legacyserver* bezeichnet.


> [!NOTE]
> Die in diesem Artikel beschriebene Methode der Batchmigration ist die einzige unterstützte Methode für die Migration von älteren öffentlichen Ordnern zu Exchange&nbsp;2013. Die alte Methode der seriellen Migration für die Migration öffentlicher Ordner ist veraltet und wird von Microsoft nicht mehr unterstützt.



Sie führen die Migration mithilfe der Cmdlets **\*MigrationBatch** und **\*PublicFolderMigrationRequest** für die Problembehandlung aus. Zusätzlich verwenden Sie die folgenden PowerShell-Skripts:

  - `Export-PublicFolderStatistics.ps1`   Dieses Skript erstellt die Datei zur Zuordnung von Ordnernamen zu Ordnergrößen.

  - ` Export-PublicFolderStatistics.psd1` Diese Unterstützungsdatei wird durch das Skript „Export-PublicFolderStatistics.ps1“ verwendet und sollte unter demselben Speicherort heruntergeladen werden.

  - `PublicFolderToMailboxMapGenerator.ps1`   Dieses Skript erstellt die Datei zur Zuordnung von öffentlichen Ordnern zu Postfächern.

  - `PublicFolderToMailboxMapGenerator.strings.psd1` Diese Unterstützungsdatei wird durch das Skript „PublicFolderToMailboxMapGenerator.ps1“ verwendet und sollte unter demselben Speicherort heruntergeladen werden.

  - `Create-PublicFolderMailboxesForMigration.ps1` Mit diesem Skript werden die Zielpostfächer für öffentliche Ordner für die Migration erstellt. Darüber hinaus wird mit diesem Skript, basierend auf den Richtlinien für die empfohlene Anzahl von Benutzeranmeldungen pro Postfach für öffentliche Ordner unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md), die Anzahl der zum Verarbeiten der geschätzten Benutzerlast notwendige Anzahl der Postfächer berechnet.

  - `Create-PublicFolderMailboxesForMigration.strings.psd1` Diese Unterstützungsdatei wird durch das Skript „Create-PublicFolderMailboxesForMigration.ps1“ verwendet und sollte unter demselben Speicherort heruntergeladen werden.

Schritt 1: Herunterladen der Migrationsskripts enthält nähere Informationen dazu, wo Sie diese Skripts herunterladen können. Stellen Sie sicher, dass alle Skripts unter demselben Speicherort heruntergeladen werden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Welche Versionen von Exchange werden für die Migration Öffentlicher Ordner zu Exchange 2013 unterstützt?

Exchange unterstützt das Verschieben Öffentlicher Ordner von den folgenden Legacyversionen von Exchange Server:

  - Exchange 2010 SP3 RU8 oder höher

  - Exchange 2007 SP3 RU15 oder höher

Wenn Sie Ihre öffentlichen Ordner zu Exchange 2013 verschieben müssen, auf Ihren lokalen Server aber nicht die minimal unterstützten Versionen von Exchange 2010 oder Exchange 2007 ausgeführt werden, lesen Sie [Verwenden der seriellen Migration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen](https://technet.microsoft.com/de-de/library/jj150486\(v=exchg.150\)). Obwohl es sich bei der seriellen Migration um eine Option handelt, empfehlen wir dringend, dass Sie ein Upgrade Ihrer lokalen Server vornehmen und die Batchmigration verwenden sollten. Die Batchmigration ist deutlich schneller und weitaus zuverlässiger.

Von Exchange 2003 können öffentliche Ordner nicht direkt migriert werden. Wenn Sie Exchange 2003 in Ihrer Organisation ausführen, müssen Sie alle Datenbanken und Replikate für öffentliche Ordner auf Exchange 2010 SP3 RU8 oder höher oder Exchange 2007 SP3 RU15 oder höher verschieben. Auf Exchange 2003 können keine Replikate öffentlicher Ordner verbleiben. Darüber hinaus kann keine E-Mail-Nachrichten für einen öffentlichen Ordner in Exchange 2013 über einen Exchange 2003-Server weitergeleitet werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Bevor Sie beginnen, sollten Sie dieses Thema vollständig lesen, da für einige Schritte Ausfallzeiten erforderlich sind.

  - Auf dem Exchange 2010-Server muss Exchange 2010 SP3 RU8 oder höher ausgeführt werden.

  - Auf dem Exchange 2007-Server muss Exchange 2007 SP3 RU15 oder höher ausgeführt werden.

  - Die maximale Anzahl von öffentlichen Ordnern, die zu Exchange 2013 in einer Migration migriert werden können, beträgt 500.000.

  - In Exchange 2013 müssen Sie Mitglied der Rollengruppe „Organisationsverwaltung“ sein. Weitere Informationen dazu, wie Sie die Rollengruppe "Organisationsverwaltung" aktivieren können, finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Sie müssen in Exchange 2010 ein Mitglied der Rollengruppe "Organisationsverwaltung" oder "Serververwaltung RBAC" sein. Nähere Informationen finden Sie unter [Hinzufügen von Mitgliedern zu einer Rollengruppe](https://go.microsoft.com/fwlink/?linkid=299212).

  - In Exchange 2007 muss Ihnen die Rolle "Exchange-Organisationsadministrator" oder "Exchange-Serveradministrator" zugewiesen sein. Darüber hinaus muss Ihnen die Rolle "Administrator für Öffentliche Ordner" zugewiesen sein, und Sie müssen Mitglied der lokalen Administratorengruppe für den Zielserver sein. Nähere Informationen finden Sie unter [Hinzufügen eines Benutzers oder einer Gruppe zu einer Administratorrolle](https://go.microsoft.com/fwlink/p/?linkid=81779).

  - Führen Sie auf dem Exchange 2007-Server ein Upgrade auf [Windows PowerShell 2.0 und WinRM 2.0 für Windows Server 2008 x64 Edition](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=968930) durch.

  - Bitte bedenken Sie vor der Migration die [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md).

  - Verschieben Sie vor dem Migrieren sämtliche Postfächer zu Exchange 2013, da Benutzer mit Exchange 2007- oder Exchange 2010-Postfächern keinen Zugriff auf öffentliche Ordner in Exchange 2013 haben. Details hierzu finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

  - In einer Umgebung mit mehreren Domänen funktionieren E-Mail-aktivierte öffentliche Ordner nach der Migration nach Exchange 2013 nicht mehr, wenn Exchange in einer untergeordneten Domäne ausgeführt wird. Dies liegt daran, dass sich E-Mail-aktivierte öffentliche Ordnerobjekte in Exchange 2013 unter der Stammdomäne befinden müssen. Um dieses Problem zu beheben, müssen Sie die E-Mail-Aktivierung Ihrer öffentlichen Ordner aufheben und sie dann erneut für E-Mail aktivieren; dies ermöglicht es Ihnen, sie zum korrekten Domänenort zu verschieben.

  - Nach Abschluss der Migration muss dem Benutzer mit dem Status **Anonym** zumindest die Berechtigung zum **Erstellen von Objekten** erteilt werden, wenn Sie zulassen möchten, dass externe Absender E-Mails an die migrierten E-Mail-aktivierten öffentlichen Ordner senden können. Wenn Sie diese Berechtigung nicht erteilt haben, erhalten externe Absender eine Zustellungsfehlerbenachrichtigung, und die Nachrichten werden dem migrierten E-Mail-aktivierten öffentlichen Ordner nicht zugestellt. Weitere Informationen zum Festlegen der Berechtigungen für anonyme Benutzer finden Sie unter [E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern](https://docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/enable-or-disable-mail-for-public-folder).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Herunterladen der Migrationsskripts

1.  Laden Sie alle Skripts und unterstützenden Dateien unter [Public Folders Migration Scripts](https://go.microsoft.com/fwlink/?linkid=299838) herunter.

2.  Speichern Sie die Skripts auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts. Stellen Sie sicher, dass alle Skripts unter demselben Speicherort gespeichert werden.

## Schritt 2: Vorbereiten der Migration

Führen Sie vor Beginn der Migration die folgenden erforderlichen Schritte durch.

**Erforderliche Schritte auf dem Exchange-Legacyserver**

1.  Zur Überprüfung am Ende der Migration sollten Sie zuerst die folgenden Befehle auf dem Exchange-Legacyserver ausführen, um Momentaufnahmen der aktuellen Bereitstellung öffentlicher Ordner zu erstellen:
    
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der ursprünglichen Quellordnerstruktur zu erstellen:
        
        ```powershell
            Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Legacy_PFStructure.xml
        ```
        
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Statistikdaten von öffentlichen Ordnern (wie Anzahl von Elementen, Größe und Besitzer) zu erstellen:
        
        ```powershell
            Get-PublicFolderStatistics | Export-CliXML C:\PFMigration\Legacy_PFStatistics.xml
        ```
        
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen zu erstellen:
        
        ```powershell
            Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML C:\PFMigration\Legacy_PFPerms.xml
        ```
        
    Speichern Sie die Informationen der vorangehenden Befehle für Vergleichszwecke nach Abschluss Ihrer Migration.

2.  Wenn der Name eines Öffentlichen Ordners einen umgekehrten Schrägstrich **\\** enthält, werden die Öffentlichen Ordner bei der Migration im übergeordneten Öffentlichen Ordner erstellt. Es wird empfohlen, vor der Migration alle Öffentlichen Ordner umzubenennen, deren Namen einen Schrägstrich aufweist.
    
    1.  Führen Sie in Exchange 2010 den folgenden Befehl aus, um Öffentliche Ordner zu finden, deren Name einen Schrägstrich aufweist:
        
        ```powershell
            Get-PublicFolderStatistics -ResultSize Unlimited | Where {($_.Name -like "*\*") -or ($_.Name -like "*/*") } | Format-List Name, Identity
        ```
    2.  Führen Sie in Exchange 2007 den folgenden Befehl aus, um Öffentliche Ordner zu finden, deren Name einen Schrägstrich aufweist:
        
        ```powershell
            Get-PublicFolderDatabase | ForEach {Get-PublicFolderStatistics -Server $_.Server | Where {$_.Name -like "*\*"}}
        ```
        
    3.  Wenn Öffentliche Ordner zurückgegeben werden, können Sie sie durch Ausführung des folgenden Befehls umbenennen:
        
        ```powershell
        Set-PublicFolder -Identity <public folder identity> -Name <new public folder name>
        ```

3.  Achten Sie darauf, dass kein vorheriger Datensatz einer erfolgreichen Migration vorhanden ist.
    
    1.  Im folgenden Beispiel wird der Migrationsstatus der Öffentlichen Ordner überprüft.
        
        ```powershell
        Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete
        ```
        
        Wenn zuvor eine erfolgreiche Migration erfolgt ist, lautet der Wert der *PublicFoldersLockedforMigration*- oder *PublicFolderMigrationComplete*-Eigenschaften `$true`. Verwenden Sie den Befehl in Schritt 3b, um den Wert auf `$false` festzulegen. Wenn der Wert auf `$true` festgelegt ist, tritt bei der Migrationsanforderung ein Fehler auf.
    
    2.  Wenn für den Status der Eigenschaft *PublicFoldersLockedforMigration* oder der Eigenschaft *PublicFolderMigrationComplete* der Wert `$true` angezeigt wird, führen Sie den folgenden Befehl aus, um den Wert auf `$false` festzulegen.
        
        ```powershell
        Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false
        ```
    

    > [!WARNING]
    > Nachdem Sie diese Eigenschaften zurückgesetzt haben, müssen Sie warten, bis Exchange die neuen Einstellungen erkennt. Dies kann bis zu zwei Stunden dauern.



Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-PublicFolder](https://technet.microsoft.com/de-de/library/aa997615\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/de-de/library/jj733416\(v=exchg.150\))

  - [Set-PublicFolder](https://technet.microsoft.com/de-de/library/aa998596\(v=exchg.150\))

  - [Get-PublicFolderStatistics](https://technet.microsoft.com/de-de/library/aa998663\(v=exchg.150\))

  - [Get-PublicFolderClientPermission](https://technet.microsoft.com/de-de/library/bb124365\(v=exchg.150\))

  - [Get-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183212)

  - [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183213)

**Erforderliche Schritte auf dem Exchange 2013-Server**

1.  Stellen Sie sicher, dass keine Migrationsanforderungen für öffentliche Ordner vorhanden sind. Wenn sie vorhanden sind, löschen Sie sie, da es sonst zu einem Fehler mit Ihrer eigenen Migrationsanforderung kommt. Dieser Schritt ist nicht in allen Fällen erforderlich. Er ist nur erforderlich, wenn Sie glauben, dass in der Pipeline möglicherweise bereits eine Migrationsanforderung vorhanden ist.
    
    Eine vorhandene Migrationsanforderung kann einen von zwei Typen haben: Batchmigration oder serielle Migration. Die Befehle zum Erkennen von Anforderungen für die einzelnen Typen und zum Entfernen von Anforderungen der einzelnen Typen sind nachfolgend aufgeführt.
    

    > [!IMPORTANT]
    > Bevor Sie eine Migrationsanforderung entfernen, ist es wichtig zu verstehen, warum eine solche Anforderung vorhanden war. Durch das Ausführen der folgenden Befehle können Sie bestimmen, wann eine frühere Anforderung erstellt wurde. Dies ist nützlich, um möglicherweise aufgetreten Probleme zu diagnostizieren. Sie müssen möglicherweise mit anderen Administratoren in Ihrer Organisation sprechen, um herauszufinden, warum die Änderung vorgenommen wurde.

    
    Im folgenden Beispiel werden vorhandene serielle Migrationsanforderungen ermittelt.
    
    ```powershell
        Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics -IncludeReport | Format-List
    ```
    
    Im folgenden Beispiel werden alle vorhandenen seriellen Migrationsanforderungen für öffentliche Ordner entfernt.
    
    ```powershell
    Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
    ```
    
    Im folgenden Beispiel werden vorhandene Batchmigrationsanforderungen ermittelt.
    
    ```powershell
        $batch = Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
    ```
    
    Im folgenden Beispiel werden alle vorhandenen Batchmigrationsanforderungen für öffentliche Ordner entfernt.
    
    ```powershell
    $batch | Remove-MigrationBatch -Confirm:$false
    ```

2.  Stellen Sie sicher, dass weder öffentliche Ordner noch Postfächer für öffentliche Ordner auf den Exchange 2013-Servern vorhanden sind.
    
    1.  Führen Sie den folgenden Befehl aus, um anzuzeigen, ob Postfächer für öffentliche Ordner vorhanden sind.
        
        ```powershell
            Get-Mailbox -PublicFolder 
        ```
        
    2.  Wenn der Befehl keine Öffentliche Ordner-Postfächer zurückgibt, fahren Sie mit Schritt 3: Generieren der CSV-Dateien fort. Wenn der Befehl öffentliche Ordner zurückgibt, führen Sie den folgenden Befehl aus, um herauszufinden, ob öffentliche Ordner vorhanden sind:
        
        ```powershell
        Get-PublicFolder
        ```
    
    3.  Wenn öffentliche Ordner vorliegen, führen Sie die folgenden PowerShell-Befehle aus, um sie zu entfernen. Stellen Sie sicher, dass Sie die in den öffentlichen Ordnern verfügbaren Informationen gespeichert haben.
        

        > [!NOTE]
        > Alle in den öffentlichen Ordnern enthaltenen Informationen werden dauerhaft gelöscht, wenn Sie sie entfernen.

        ```powershell
            Get-Mailbox -PublicFolder | Where{$_.IsRootPublicFolderMailbox -eq $false} | Remove-Mailbox -PublicFolder -Force -Confirm:$false
		```

        ```powershell
        Get-Mailbox -PublicFolder | Remove-Mailbox -PublicFolder -Force -Confirm:$false
        ```
		

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219164\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218718\(v=exchg.150\))

  - [Remove-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218625\(v=exchg.150\))

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Get-PublicFolder](https://technet.microsoft.com/de-de/library/aa997615\(v=exchg.150\))

  - [Get-MailPublicFolder](https://technet.microsoft.com/de-de/library/bb124772\(v=exchg.150\))

  - [Disable-MailPublicFolder](https://technet.microsoft.com/de-de/library/bb123781\(v=exchg.150\))

  - [Remove-PublicFolder](https://technet.microsoft.com/de-de/library/bb124894\(v=exchg.150\))

  - [Remove-Mailbox](https://technet.microsoft.com/de-de/library/aa995948\(v=exchg.150\))

## Schritt 3: Generieren der CSV-Dateien

1.  Führen Sie auf dem Exchange-Legacyserver das Skript `Export-PublicFolderStatistics.ps1` aus, um die Zuordnungsdatei für Ordnernamen zur Ordnergröße zu erstellen. Dieses Skript muss von einem lokalen Administrator ausgeführt werden. Die Datei enthält zwei Spalten: **FolderName** und **FolderSize**. Die Werte für die Spalte **FolderSize** werden in Byte angezeigt. Beispiel: **\\PublicFolder01,10000**.
    
    ```powershell
        .\Export-PublicFolderStatistics.ps1  <Folder to size map path> <FQDN of source server>
    ```
    
      - *FQDN of source server* entspricht dem vollqualifizierten Domänennamen des Postfachservers, auf dem die Hierarchie Öffentlicher Ordner gehostet wird.
    
      - *Folder to size map path* entspricht dem Dateinamen und dem Pfad im freigegebenen Netzwerkordner, in dem Sie die CSV-Datei speichern möchten. Später in diesem Thema benötigen Sie Zugriff über den Exchange 2013-Server auf diese Datei. Wenn Sie nur den Dateinamen angeben, wird die Datei auf dem lokalen Computer im aktuellen PowerShell-Verzeichnis generiert.

2.  Führen Sie das Skript `PublicFolderToMailboxMapGenerator.ps1` aus, um die Datei zur Zuordnung von Öffentlichen Ordnern zu Postfächern zu erstellen. Diese Datei wird verwendet, um die richtige Anzahl von Postfächern für öffentliche Ordner auf dem Exchange 2013-Postfachserver zu berechnen.
    

    > [!NOTE]
    > Wenn der Name eines Öffentlichen Ordners einen umgekehrten Schrägstrich <STRONG>&#92;</STRONG> enthält, werden die Öffentlichen Ordner im übergeordneten Öffentlichen Ordner erstellt. Es empfiehlt sich, die CSV-Datei zu prüfen und Namen zu bearbeiten, die einen umgekehrten Schrägstrich enthalten.

    ```powershell
        .\PublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes> <Folder to size map path> <Folder to mailbox map path>
    ```
    
      - *Maximum mailbox size in bytes* entspricht der maximalen Größe, die Sie für neue Postfächer für Öffentliche Ordner festlegen möchten. Wenn Sie diese Einstellung angeben, müssen Sie eine Zunahme einplanen, damit das Postfach für öffentliche Ordner vergrößert werden kann.
    
      - *Folder to size map path* entspricht dem Dateipfad der CSV-Datei, die Sie durch die Ausführung des Skripts `Export-PublicFolderStatistics.ps1` erstellt haben.
    
      - *Folder to mailbox map path* entspricht dem Dateinamen und -pfad der CSV-Datei für die Zuordnung von Ordnern zu Postfächern, die Sie in diesem Schritt erstellen. Wenn Sie nur den Dateinamen angeben, wird die Datei auf dem lokalen Computer im aktuellen PowerShell-Verzeichnis generiert.

## Schritt 4: Erstellen der Postfächer für öffentliche Ordner in Exchange 2013

1.  Führen Sie den folgenden Befehl aus, um die Zielpostfächer für öffentliche Ordner zu erstellen. Mit dem Skript wird ein Zielpostfach für jedes Postfach in der CSV-Datei erstellt, die Sie in Schritt 3 durch Ausführen des „PublicFoldertoMailboxMapGenerator.ps1„-Skripts generiert haben.
    
    ```powershell
        .\Create-PublicFolderMailboxesForMigration.ps1 -FolderMappingCsv Mapping.csv -EstimatedNumberOfConcurrentUsers:<estimate>
    ```
    
    *Mapping.csv* ist die Datei, die durch Ausführen des Skripts „PublicFoldertoMailboxMapGenerator.ps1“ in Schritt 3 generiert wurde. Die geschätzte Anzahl der gleichzeitigen Benutzerverbindungen beim Durchsuchen einer Hierarchie öffentlicher Ordner ist in der Regel kleiner als die Gesamtzahl der Benutzer in einer Organisation.

## Schritt 5: Starten der Migrationsanforderung

Die Schritte für die Migration von öffentlichen Exchange 2007-Ordnern unterscheiden sich von den Schritten für die Migration von öffentlichen Exchange 2010-Ordnern.


> [!TIP]
> Unabhängig davon, ob Sie die Migration von Exchange 2007 oder Exchange 2010 vornehmen, können Sie die Anforderungen anzeigen und sie in EAC verwalten, sobald Batchmigrationsanforderungen mit dem entsprechenden Cmdlet erstellt wurden.



**Migrieren von öffentlichen Exchange 2007-Ordnern**

1.  Öffentliche Ordner des Legacysystems wie OWAScratchPad und die Schemastammordner-Unterstruktur in Exchange 2007 werden nicht von Exchange 2013 erkannt und als ungültige Elemente behandelt. Dies führt dazu, dass die Migration nicht erfolgreich ist. Im Rahmen der Migrationsanforderung müssen Sie einen Wert für den `BadItemLimit`-Parameter angeben. Dieser Wert variiert je nach Anzahl der vorhandenen Datenbanken für Öffentliche Ordner. Die folgenden Befehle bestimmen, über wie viele Datenbanken für öffentliche Ordner Sie verfügen, und sie berechnen den `BadItemLimit`-Parameter für die Migrationsanforderung.
    
    ```powershell
		$PublicFolderDatabasesInOrg = @(Get-PublicFolderDatabase)
	```
    
	```powershell
        $BadItemLimitCount = 5 + ($PublicFolderDatabasesInOrg.Count -1)
	```

2.  Führen Sie auf dem Exchange 2013-Server den folgenden Befehl aus:
    
    ```powershell
        New-MigrationBatch -Name PFMigration -SourcePublicFolderDatabase (Get-PublicFolderDatabase -Server <Source server name>) -CSVData (Get-Content <Folder to mailbox map path> -Encoding Byte) -NotificationEmails <email addresses for migration notifications> -BadItemLimit $BadItemLimitCount 
    ```
    
3.  Starten Sie die Migration mit dem folgenden Befehl:
    
    ```powershell
    Start-MigrationBatch PFMigration
    ```

**Migrieren von öffentlichen Exchange 2010-Ordnern**

1.  Führen Sie auf dem Exchange 2013-Server den folgenden Befehl aus.
    
    ```powershell
        New-MigrationBatch -Name PFMigration -SourcePublicFolderDatabase (Get-PublicFolderDatabase -Server <Source server name>) -CSVData (Get-Content <Folder to mailbox map path> -Encoding Byte) -NotificationEmails <email addresses for migration notifications> 
    ```
    
    Der Parameter `NotificationEmails` ist optional.

2.  Starten Sie die Migration mit dem folgenden Befehl:
    
    ```powershell
    Start-MigrationBatch PFMigration
    ```
    
    – oder –
    
    Sie können die Migration in EAC starten.
    
    1.  Melden Sie sich bei Exchange Online an, und öffnen Sie EAC.
    
    2.  Navigieren Sie zu **Empfänger** \> **Migration**.
    
    3.  Wählen Sie den von Ihnen erstellen Migrationsbatch aus, und klicken Sie dann auf die Startschaltfläche.

Die Spalte **Status** zeigt den anfänglichen Batchstatus als **Erstellt** an. Der Status wird während der Migration zu **Synchronisierung** geändert. Wenn die Migrationsanforderung abgeschlossen ist, lautet der Status **Synchronisiert**. Sie können auf einen Batch doppelklicken, um den Status einzelner Postfächer im Batch anzuzeigen. Postfachaufträge beginnen mit dem Status **In die Warteschlange eingestellt**. Wenn der Auftrag beginnt, lautet der Status **Synchronisierung**. Sobald `InitialSync` abgeschlossen ist, lautet der Status **Synchronisiert**.

Status und Fertigstellung der Migration können angezeigt und in EAC verwaltet werden. Da das Cmdlet **New-MigrationBatch** eine Postfachmigrationsanforderung für jedes Postfach für öffentliche Ordner initiiert, können Sie den Status dieser Anforderungen mithilfe der Seite für die Postfachmigration anzeigen. Sie können zur Seite für die Postfachmigration wechseln und Migrationsberichte erstellen, die Ihnen per E-Mail gesendet werden können, indem Sie Folgendes vornehmen:

1.  Melden Sie sich bei Exchange Online an, und öffnen Sie EAC.

2.  Navigieren Sie zu **Postfach** \> **Migration**.

3.  Wählen Sie die soeben erstellte Migrationsanforderung aus, und klicken Sie im Bereich **Details** auf **Details anzeigen**.

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218636\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/de-de/library/jj733416\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218718\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequestStatistics](https://technet.microsoft.com/de-de/library/jj218697\(v=exchg.150\))

## Schritt 6: Sperren der Öffentlichen Ordner auf dem Exchange-Legacyserver für die endgültige Migration (Ausfallzeit erforderlich)

Bis zu diesem Zeitpunkt in der Migration konnten Benutzer auf Öffentliche Ordner zugreifen. In den nächsten Schritten werden die Benutzer von den älteren Öffentlichen Ordnern abgemeldet, und die Ordner werden gesperrt, bis die abschließende Synchronisierung im Rahmen des Migrationsvorgangs beendet ist. Während dieses Vorgangs können die Benutzer nicht auf Öffentliche Ordner zugreifen. Außerdem werden alle E-Mails, die an E-Mail-aktivierte Öffentliche Ordner gesendet werden, in die Warteschlange gestellt und erst nach Abschluss der Öffentliche Ordner-Migration übermittelt.

Bevor Sie den Befehl `PublicFoldersLockedForMigration` wie unten beschrieben ausführen, vergewissern Sie sich, dass alle Aufträge den Status **Synchronisiert** aufweisen. Führen Sie hierzu den Befehl `Get-PublicFolderMailboxMigrationRequest` aus. Fahren Sie mit diesem Schritt erst dann fort, nachdem Sie überprüft haben, ob alle Aufträge den Status **Synchronisiert** aufweisen.

Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die älteren Öffentlichen Ordner bis zum Abschluss des Vorgangs zu sperren.

```powershell
Set-OrganizationConfig -PublicFoldersLockedForMigration:$true
```


> [!NOTE]
> Wenn aus irgendeinem Grund die Migrationsbatchdatei nicht fertig gestellt wird (Für <STRONG>PublicFolderMigrationComplete</STRONG> wird <STRONG>False</STRONG> angezeigt), starten Sie den Informationsspeicher (IS) auf dem Legacyserver neu.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)).

Wenn Ihre Organisation über mehrere Datenbanken für Öffentliche Ordner verfügt, müssen Sie warten, bis die Replikation Öffentlicher Ordner abgeschlossen wurde, und sicherstellen, dass für alle Datenbanken für Öffentliche Ordner das Kennzeichen `PublicFoldersLockedForMigration` gesetzt ist und alle offenen Änderungen, die von Benutzern in letzter Zeit an Ordnern vorgenommen wurden, organisationsweit übernommen wurden. Dieser Vorgang kann mehrere Stunden in Anspruch nehmen.

## Schritt 7: Schließen Sie die Migration öffentlicher Ordner ab (Ausfallzeit erforderlich)

Führen Sie zuerst das folgende Cmdlet aus, um den Typ der Exchange 2013-Bereitstellung zu **Remote** zu ändern:

```powershell
Set-OrganizationConfig -PublicFoldersEnabled Remote
```

Nachdem dies erfolgt ist, können Sie die Migration öffentlicher Ordner abschließen, indem Sie den folgenden Befehl ausführen:

```powershell
Complete-MigrationBatch PublicFolderMigration
```

Alternativ können Sie die Migration in EAC abschließen, indem Sie auf **Migrationsbatch abschließen** klicken.

Nach Abschluss die Migration führt Exchange eine endgültige Synchronisierung zwischen dem Legacy-Exchange-Server und Exchange 2013 durch. Ist die abschließende Synchronisierung erfolgreich, werden die öffentlichen Ordner auf dem Exchange 2013-Server entsperrt, und der Status des Migrationsbatches wird in **Wird abgeschlossen** und dann in **Abgeschlossen** geändert. In der Regel dauert es einige Stunden, bis der Status des Migrationsbatches von **Synchronisiert** in **Wird abgeschlossen** geändert wird. Erst dann beginnt die abschließende Synchronisierung.

## Schritt 8: Testen und Entsperren der Migration Öffentlicher Ordner

Nachdem Sie die Migration Öffentlicher Ordner abgeschlossen haben, sollten Sie den folgenden Test durchführen und so sicherstellen, dass die Migration erfolgreich war. Dies ermöglicht Ihnen, die Hierarchie migrierter Öffentlicher Ordner zu testen, bevor Sie öffentliche Exchange 2013-Ordner verwenden.

1.  Führen Sie in der PowerShell folgenden Befehl aus, um einige Testpostfächer zuzuweisen und ein beliebiges neu migriertes Postfach für öffentliche Ordner als Standardpostfach für öffentliche Ordner zu verwenden.
    
    ```powershell
        Set-Mailbox -Identity <Test User> -DefaultPublicFolderMailbox <Public Folder Mailbox Identity>
    ```
    
2.  Melden Sie sich mit dem im vorherigen Schritt identifizierten Testbenutzer bei Outlook 2007 oder höher an, und führen Sie denn die folgenden Öffentliche Ordner-Tests durch:
    
      - Zeigen Sie die Hierarchie an.
    
      - Prüfen Sie die Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

3.  Wenn Probleme auftreten, lesen Sie Durchführen eines Rollbacks der Migration weiter unten in diesem Thema. Wenn der Inhalt und die Hierarchie des Öffentlichen Ordners akzeptabel sind und wie erwartet funktionieren, führen Sie folgenden Befehl aus, um die Öffentlichen Ordner für alle anderen Benutzer zu entsperren.
    
    ```powershell
    Get-Mailbox -PublicFolder | Set-Mailbox -PublicFolder -IsExcludedFromServingHierarchy $false
    ```
        

    > [!IMPORTANT]
    > Verwenden Sie nach Abschluss der anfänglichen Migrationsüberprüfung nicht den Parameter <EM>IsExcludedFromServingHierarchy</EM>, da dieser Parameter vom automatisierten Speicherverwaltungsdienst für Exchange Online verwendet wird.



4.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um anzugeben, dass die Migration der Öffentlichen Ordner abgeschlossen ist.
    
    ```powershell
    Set-OrganizationConfig -PublicFolderMigrationComplete:$true
    ```

5.  Nachdem Sie überprüft haben, dass die Migration abgeschlossen ist, führen Sie den folgenden Befehl aus:
    
    ```powershell
    Set-OrganizationConfig -PublicFoldersEnabled Local
    ```

6.  Dem Benutzer mit dem Status **Anonym** muss zumindest die Berechtigung **Objekte erstellen** erteilt werden, wenn Sie zulassen möchten, dass externe Absender E-Mails an migrierte E-Mail-aktivierte öffentliche Ordner senden können. Wenn Sie diese Berechtigung nicht erteilt haben, erhalten externe Absender eine Zustellungsfehlerbenachrichtigung, und die Nachrichten werden dem migrierten E-Mail-aktivierten öffentlichen Ordner nicht zugestellt.
    
    Sie können die Shell oder Outlook verwenden, um die Berechtigungen für den anonymen Benutzer festzulegen. Weitere Informationen zum Festlegen der Berechtigungen für anonyme Benutzer finden Sie unter [E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern](https://docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/enable-or-disable-mail-for-public-folder).

## Woher weiß ich, dass der Vorgang erfolgreich war?

Unter Schritt 2: Vorbereiten der Migration wurden Sie aufgefordert, Momentaufnahmen der Struktur Öffentlicher Ordner, der Statistikdaten und der Berechtigungen vor der Migration zu erstellen. Mit den folgenden Schritten können Sie überprüfen, ob die Migration Öffentlicher Ordner erfolgreich war, indem Sie die gleichen Momentaufnahmen nach Abschluss der Migration erstellen. Sie können dann die Daten in beiden Dateien vergleichen, um den Erfolg zu überprüfen.

1.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der neuen Ordnerstruktur zu erstellen.
    
    ```powershell
        Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Cloud_PFStructure.xml
    ```

2.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Statistikdaten von öffentlichen Ordnern (wie Anzahl von Elementen, Größe und Besitzer) zu erstellen.
    
    ```powershell
        Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\PFMigration\Cloud_PFStatistics.xml
    ```
    
3.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen zu erstellen.
    
    ```powershell
        Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML  C:\PFMigration\Cloud_PFPerms.xml
    ```
    
## Entfernen von Datenbanken für Öffentliche Ordner von den Exchange-Legacyservern

Sobald die Migration abgeschlossen ist und Sie sichergestellt haben, dass die öffentlichen Exchange 2013-Ordner erwartungsgemäß funktionieren, sollten Sie die Datenbanken für Öffentliche Ordner auf den Exchange-Legacyservern entfernen.

  - Nähere Informationen zum Entfernen von Öffentliche Ordner-Datenbanken von Exchange 2007-Servern finden Sie unter [Entfernen Öffentlicher Ordner-Datenbanken](https://go.microsoft.com/fwlink/?linkid=123678).

  - Nähere Informationen zum Entfernen von Öffentliche Ordner-Datenbanken von Exchange 2010-Servern finden Sie unter [Entfernen von Öffentliche Ordner-Datenbanken](https://go.microsoft.com/fwlink/?linkid=81409).

## Durchführen eines Rollbacks der Migration

Wenn bei der Migration Probleme auftreten und Sie die Öffentlichen Ordner von einem Exchange-Legacyserver erneut aktivieren müssen, führen Sie die folgenden Schritte aus.


> [!WARNING]
> Wenn Sie ein Rollback der Migration auf die Exchange-Legacyserver vornehmen, gehen alle E-Mails verloren, die an E-Mail-fähige öffentliche Ordner gesendet wurden, sowie Inhalte, die nach der Migration in öffentlichen Ordnern in Exchange 2013 bereitgestellt wurden. Um diese Inhalte zu speichern, müssen Sie die Inhalte der öffentlichen Ordner in einer PST-Datei speichern und diese dann nach Abschluss des Rollbacks in die älteren öffentlichen Ordner importieren.



1.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die älteren Öffentlichen Exchange-Ordner zu entsperren. Dieser Vorgang kann mehrere Stunden in Anspruch nehmen.
    
    ```powershell
    Set-OrganizationConfig -PublicFoldersLockedForMigration:$False
    ```

2.  Führen Sie auf dem Exchange 2013-Server folgende Befehle aus, um die Postfächer für öffentliche Ordner zu löschen.
    
    ```powershell
        Get-Mailbox -PublicFolder | Where{$_.IsRootPublicFolderMailbox -eq $false} | Remove-Mailbox -PublicFolder -Force -Confirm:$false
    ```
    
    ```powershell
    Get-Mailbox -PublicFolder | Remove-Mailbox -PublicFolder -Force -Confirm:$false
    ```

3.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die `PublicFolderMigrationComplete`-Kennzeichnung auf `$false` festzulegen.
    
    ```powershell
    Set-OrganizationConfig -PublicFolderMigrationComplete:$False
    ```

