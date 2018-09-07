---
title: 'Stapelmigr. v. öfftl. Ordnern e. Vorgängerv. zu Office 365 u. Exchange Online'
TOCTitle: Verwenden der Stapelmigration zum Migrieren von öffentlichen Ordnern einer Vorgängerversion zu Office 365 und Exchange Online
ms:assetid: e8ab9309-7d12-4f02-bfc4-14e61a373958
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn874017(v=EXCHG.150)
ms:contentKeyID: 63892333
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden der Stapelmigration zum Migrieren von öffentlichen Ordnern einer Vorgängerversion zu Office 365 und Exchange Online

 

_**Gilt für:** Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-03-26_

**Zusammenfassung:**  Verwenden Sie diese Verfahren, um Ihre öffentlichen Exchange 2007- und Exchange 2010-Ordner in Office 365 zu verschieben.

Dieses Thema beschreibt das Migrieren Ihrer öffentlichen Ordner in einer ein- oder mehrstufigen Migration vom Updaterollup 8 für Exchange Server 2010 Service Pack 3 (SP3) oder Updaterollup 15 für Exchange 2007 SP3 zu Office 365 oder Exchange Online.

In diesem Thema werden die Server mit Exchange 2010 SP3 RU8 und Exchange 2007 SP3 RU15 als *Exchange-Legacyserver* bezeichnet. Die Schritte in diesem Thema gelten außerdem für Exchange Online genauso wie für Office 365. Die Begriffe werden in diesem Thema möglicherweise synonym verwendet.


> [!NOTE]
> Die in diesem Artikel beschriebene Methode der Batchmigration ist die einzige unterstützte Methode für die Migration von älteren öffentlichen Ordnern zu Office&nbsp;365 und Exchange&nbsp;Online. Die alte Methode der seriellen Migration für die Migration öffentlicher Ordner ist veraltet und wird von Microsoft nicht mehr unterstützt.



Es wird empfohlen, nicht das PST-Exportfeature von Outlook zum Migrieren öffentlicher Ordner zu Office 365 oder Exchange Online zu verwenden. Das Anwachsen des Postfachs für öffentliche Ordner in Office 365 und Exchange Online wird über ein Feature zur automatischen Aufteilung verwaltet, welches das Postfach für öffentliche Ordner aufteilt, wenn Größenkontingente überschritten werden. Das plötzliche Anwachsen der Postfächer für Öffentliche Ordner kann nicht von der automatischen Aufteilung verwaltet werden, wenn Sie Öffentliche Ordner über den PST-Export migrieren. Sie müssen dann möglicherweise bis zu zwei Wochen warten, bis die Daten durch automatische Aufteilung aus dem primären Postfach verschoben werden. Es wird empfohlen, den Cmdlet-basierten Anweisungen in diesem Dokument zu folgen, um öffentliche Ordner zu Office 365 und Exchange Online zu migrieren. Wenn Sie sich dennoch dafür entscheiden, Öffentliche Ordner per PST-Export zu migrieren, sollten Sie den Abschnitt Migrieren von öffentlichen Ordnern zu Office 365 mit PST-Export von Outlook weiter unten in diesem Thema lesen.

Die Migration wird mit den Cmdlets **\*-MigrationBatch** sowie mit den folgenden PowerShell-Skripts ausgeführt:

  - `Export-PublicFolderStatistics.ps1`   Dieses Skript erstellt die Datei zur Zuordnung von Ordnernamen zu Ordnergrößen. Sie führen dieses Skript auf dem Exchange-Legacyserver aus.

  - `Export-PublicFolderStatistics.psd1`   Diese Unterstützungsdatei wird von dem Skript `Export-PublicFolderStatistics.ps1` verwendet und sollte an den gleichen Speicherort heruntergeladen werden.

  - `PublicFolderToMailboxMapGenerator.ps1`   Dieses Skript erstellt mithilfe der Ausgabe aus dem Skript `Export-PublicFolderStatistics.ps1` die Datei zur Zuordnung von Öffentlichen Ordnern zu Postfächern. Sie führen dieses Skript auf dem Exchange-Legacyserver aus.

  - `PublicFolderToMailboxMapGenerator.strings.psd1`   Diese Unterstützungsdatei wird von dem Skript `PublicFolderToMailboxMapGenerator.ps1` verwendet und sollte an den gleichen Speicherort heruntergeladen werden.

  - `Create-PublicFolderMailboxesForMigration.ps1` Mit diesem Skript werden die Zielpostfächer für öffentliche Ordner für die Migration erstellt. Darüber hinaus wird mit diesem Skript, basierend auf den Richtlinien für die empfohlene Anzahl von Benutzeranmeldungen pro Postfach für öffentliche Ordner unter [Grenzwerte für öffentliche Ordner](limits-for-public-folders-exchange-2013-help.md), die Anzahl der zum Verarbeiten der geschätzten Benutzerlast notwendige Anzahl der Postfächer berechnet.

  - `Create-PublicFolderMailboxesForMigration.strings.psd1` Diese Unterstützungsdatei wird durch das Skript „Create-PublicFolderMailboxesForMigration.ps1“ verwendet und sollte unter demselben Speicherort heruntergeladen werden.

  - `Sync-MailPublicFolders.ps1`   Mit diesem Skript werden die E-Mail-aktivierten öffentlichen Ordnerobjekte zwischen Ihrer lokalen Exchange-Bereitstellung und Office 365 synchronisiert. Sie führen dieses Skript auf dem Exchange-Legacyserver aus.

  - `SyncMailPublicFolders.strings.psd1`   Dabei handelt es sich eine Supportdatei, die vom `Sync-MailPublicFolders.ps1`-Skript verwendet wird und an den gleichen Speicherort wie die vorhergehenden Skripts kopiert werden muss.

Schritt 1: Herunterladen der Migrationsskripts enthält nähere Informationen dazu, wo Sie diese Skripts herunterladen können. Stellen Sie sicher, dass alle Skripts unter demselben Speicherort heruntergeladen werden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Welche Versionen von Exchange werden für die Migration öffentlicher Ordner zu Office 365 und Exchange Online unterstützt?

Exchange unterstützt das Verschieben Ihrer öffentlichen Ordner von den folgenden Legacyversionen von Exchange Server zu Office 365 und Exchange Online:

  - Exchange 2010 SP3 RU8 oder höher

  - Exchange 2007 SP3 RU15 oder höher

Wenn Sie Ihre öffentlichen Ordner zu Exchange Online verschieben müssen, auf Ihren lokalen Server aber nicht die minimal unterstützten Versionen von Exchange 2010 oder Exchange 2007 ausgeführt werden, empfehlen wir dringend, dass Sie ein Upgrade Ihrer lokalen Server vornehmen und die Batchmigration verwenden, da es sich dabei um die einzige unterstützte Methode für die Migration öffentlicher Ordner handelt.

Von Exchange 2003 können öffentliche Ordner nicht direkt migriert werden. Wenn Sie Exchange 2003 in Ihrer Organisation ausführen, müssen Sie alle Datenbanken und Replikate für öffentliche Ordner auf Exchange 2010 SP3 RU8 oder höher oder Exchange 2007 SP3 RU10 oder höher verschieben. Auf Exchange 2003 können keine Replikate öffentlicher Ordner verbleiben. Darüber hinaus kann keine E-Mail-Nachrichten für einen öffentlichen Ordner in Exchange 2013 über einen Exchange 2003-Server weitergeleitet werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Auf dem Exchange 2010-Server muss Exchange 2010 SP3 RU8 oder höher ausgeführt werden.

  - Auf dem Exchange 2007-Server muss Exchange 2007 SP3 RU15 oder höher ausgeführt werden.

  - In Office 365 und Exchange Online müssen Sie ein Mitglied der Rollengruppe "Organisationsverwaltung" sein. Diese Rollengruppe unterscheidet sich von den Berechtigungen, die Ihnen zugewiesen wurden, als Sie Office 365 oder Exchange Online abonniert haben. Weitere Informationen dazu, wie Sie die Rollengruppe "Organisationsverwaltung" aktivieren können, finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Sie müssen in Exchange 2010 ein Mitglied der Rollengruppe "Organisationsverwaltung" oder "Serververwaltung RBAC" sein. Nähere Informationen finden Sie unter [Hinzufügen von Mitgliedern zu einer Rollengruppe](https://go.microsoft.com/fwlink/?linkid=299212).

  - In Exchange 2007 muss Ihnen die Rolle "Exchange-Organisationsadministrator" oder "Exchange-Serveradministrator" zugewiesen sein. Darüber hinaus muss Ihnen die Rolle "Administrator für Öffentliche Ordner" zugewiesen sein, und Sie müssen Mitglied der lokalen Administratorengruppe für den Zielserver sein. Nähere Informationen finden Sie unter [Hinzufügen eines Benutzers oder einer Gruppe zu einer Administratorrolle](https://go.microsoft.com/fwlink/p/?linkid=81779).

  - Führen Sie auf dem Exchange 2007-Server ein Upgrade auf [Windows PowerShell 2.0 und WinRM 2.0 für Windows Server 2008 x64 Edition](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=968930) durch.

  - Wenn es in Ihrer Organisation Öffentliche Ordner gibt, die größer als 2 GB sind, empfehlen wir, vor der Migration entweder Inhalte aus diesem Ordner zu löschen oder ihn in mehrere Öffentliche Ordner aufzuteilen. Wenn keine dieser Möglichkeiten infrage kommt, wird empfohlen, die öffentlichen Ordner nicht zu Office 365 und Exchange Online zu verschieben.

  - In Office 365 und Exchange Online können Sie maximal 1.000 Postfächer für öffentliche Ordner erstellen.

  - Bevor Sie Ihre öffentlichen Ordner migrieren, empfehlen wir, zuerst alle Benutzerpostfächer zu Office 365 und Exchange Online zu verschieben. Weitere Informationen finden Sie unter [Methoden zum Migrieren mehrerer E-Mail-Konten zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=524030).

  - Outlook Anywhere muss auf dem Exchange-Legacyserver aktiviert sein. Weitere Informationen zum Aktivieren von Outlook Anywhere auf Exchange 2010-Servern finden Sie unter [Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=187249). Weitere Informationen zum Aktivieren von Outlook Anywhere auf Exchange 2007-Servern finden Sie unter [Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=167210).

  - Dieses Verfahren kann nicht mithilfe des Exchange Admin Centers (EAC) oder der Exchange-Verwaltungskonsole (EMC) ausgeführt werden. Sie müssen auf den Exchange-Legacyservern die Exchange-Verwaltungsshell verwenden. Für Exchange Online müssen Sie die Exchange Online PowerShell verwenden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)).

  - Bevor Sie beginnen, sollten Sie dieses Thema vollständig lesen, da für einige Schritte Ausfallzeiten erforderlich sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Herunterladen der Migrationsskripts

1.  Laden Sie alle Skripts und unterstützenden Dateien unter [Public Folders Migration Scripts](https://go.microsoft.com/fwlink/?linkid=299838) herunter.

2.  Speichern Sie die Skripts auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts. Stellen Sie sicher, dass alle Skripts unter demselben Speicherort gespeichert werden.

3.  Laden Sie die folgenden Dateien von [E-Mail-aktivierten öffentlichen Ordnern – Skript für die Verzeichnissynchronisierung](https://go.microsoft.com/fwlink/p/?linkid=532376) herunter:
    
    1.  `Sync-MailPublicFolders.ps1`
    
    2.  `SyncMailPublicFolders.strings.psd1`

4.  Speichern Sie die Skripts am gleichen Speicherort, den Sie unter Schritt 2 verwendet haben, z. B. C:\\PFScripts.

## Schritt 2: Vorbereiten der Migration

Führen Sie vor Beginn der Migration die folgenden erforderlichen Schritte durch.

**Allgemeine erforderliche Schritte**

  - Stellen Sie sicher, dass keine verwaisten E-Mail-Objekte für öffentliche Ordner in Active Directory vorhanden sind, also Objekte in Active Directory ohne ein entsprechendes Exchange-Objekt.

  - Vergewissern Sie sich, dass die SMTP-E-Mail-Adresse, die für öffentliche Ordner in Active Directory konfiguriert wird, mit den SMTP-E-Mail-Adressen für die Exchange-Objekte übereinstimmt.

  - Stellen Sie sicher, dass keine doppelten Objekte für öffentliche Ordner in Active Directory vorhanden sind, um eine Situation zu vermeiden, bei der zwei oder mehrere Active Directory-Objekte auf den gleichen E-Mail-aktivierten öffentlichen Ordner verweisen.

**Erforderliche Schritte auf dem Exchange-Legacyserver**

1.  Stellen Sie auf dem Exchange-Legacyserver sicher, dass das Routing zu den E-Mail-aktivierten öffentlichen Ordnern, die für Exchange Online vorgesehen sind, weiterhin funktioniert, bis alle DNS-Caches über das Internet so aktualisiert wurden, dass sie auf den Exchange Online-DNS verweisen, auf dem sich Ihre Organisation nun befindet. Führen Sie dazu den folgenden Befehl aus, um eine akzeptierte Domäne mit einem bekannten Namen zu konfigurieren, die E-Mail-Nachrichten korrekt zur Exchange Online-Domäne routet.
    
        New-AcceptedDomain -Name "PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99" -DomainName contoso.onmicrosoft.com -DomainType InternalRelay 

2.  Wenn der Name eines Öffentlichen Ordners einen umgekehrten Schrägstrich **\\** enthält, werden die Öffentlichen Ordner bei der Migration im übergeordneten Öffentlichen Ordner erstellt. Es wird empfohlen, vor der Migration alle Öffentlichen Ordner umzubenennen, deren Namen einen Schrägstrich aufweist.
    
    1.  Führen Sie in Exchange 2010 den folgenden Befehl aus, um Öffentliche Ordner zu finden, deren Name einen Schrägstrich aufweist:
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Where {($_.Name -like "*\*") -or ($_.Name -like "*/*") } | Format-List Name, Identity
    
    2.  Führen Sie in Exchange 2007 den folgenden Befehl aus, um Öffentliche Ordner zu finden, deren Name einen Schrägstrich aufweist:
        
            Get-PublicFolderDatabase | ForEach {Get-PublicFolderStatistics -Server $_.Server | Where {$_.Name -like "*\*"}}
    
    3.  Wenn Öffentliche Ordner zurückgegeben werden, können Sie sie durch Ausführung des folgenden Befehls umbenennen:
        
            Set-PublicFolder -Identity <public folder identity> -Name <new public folder name>

3.  Achten Sie darauf, dass kein vorheriger Datensatz einer erfolgreichen Migration vorhanden ist. Falls ein solcher Datensatz vorhanden ist, müssen Sie den Wert auf `$false` festlegen. Wenn der Wert auf `$true` festgelegt ist, tritt bei der Migrationsanforderung ein Fehler auf.
    
    1.  Im folgenden Beispiel wird der Migrationsstatus der Öffentlichen Ordner überprüft.
        
            Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete
    
    2.  Wenn für den Status der Eigenschaft *PublicFoldersLockedforMigration* oder der Eigenschaft *PublicFolderMigrationComplete* der Wert `$true` angezeigt wird, führen Sie den folgenden Befehl aus, um den Wert auf `$false` festzulegen.
        
            Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false
    

    > [!WARNING]
    > Nachdem Sie diese Eigenschaften zurückgesetzt haben, müssen Sie warten, bis Exchange die neuen Einstellungen erkennt. Dies kann bis zu zwei Stunden dauern.



4.  Zur Überprüfung am Ende der Migration sollten Sie zuerst die folgenden Exchange-Verwaltungsshell-Befehle auf dem Exchange-Legacyserver ausführen, um Momentaufnahmen der aktuellen Bereitstellung öffentlicher Ordner zu erstellen:
    
    1.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der ursprünglichen Quellordnerstruktur zu erstellen.
        
            Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Legacy_PFStructure.xml
    
    2.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Statistikdaten von Öffentlichen Ordnern (wie Anzahl von Elementen, Größe und Besitzer) zu erstellen.
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\PFMigration\Legacy_PFStatistics.xml
    
    3.  Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen zu erstellen.
        
            Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML C:\PFMigration\Legacy_PFPerms.xml
    
    Speichern Sie die Informationen aus den oben aufgeführten Befehlen, um am Ende der Migration einen Vergleich durchführen zu können.

5.  Wenn Sie Microsoft Azure Active Directory Connect (Azure AD Connect) zum Synchronisieren Ihrer lokalen Verzeichnisse mit Azure Active Directory verwenden, müssen Sie Folgendes ausführen (wenn Sie nicht Azure AD Connect verwenden, können Sie diesen Schritt überspringen):
    
    1.  Öffnen Sie auf einem lokalen Computer Microsoft Azure Active Directory Connect, und wählen Sie dann **Konfigurieren** aus.
    
    2.  Wählen Sie auf dem Bildschirm **Weitere Aufgaben** die Option **Synchronisierungsoptionen prüfen oder anpassen** aus, und klicken Sie dann auf **Weiter**.
    
    3.  Geben Sie auf dem Bildschirm **Mit Azure AD verbinden** die entsprechenden Anmeldeinformationen ein, und klicken Sie dann auf **Next**. Nachdem eine Verbindung hergestellt wurde, klicken Sie weiter auf **Weiter**, bis Sie sich auf dem Bildschirm **Optionale Features** befinden.
    
    4.  Vergewissern Sie sich, dass **Öffentliche Exchange-E-Mail-Ordner** nicht aktiviert ist. Wenn die Option nicht aktiviert ist, können Sie mit dem nächsten Abschnitt, *Erforderliche Schritte in Office 365 oder Exchange Online*, fortfahren. Wenn die Option aktiviert ist, deaktivieren Sie das Kontrollkästchen, und klicken Sie dann auf **Weiter**.
        

        > [!NOTE]
        > Wenn Sie <STRONG>Öffentliche Exchange-E-Mail-Ordner</STRONG> nicht als Option auf dem Bildschirm <STRONG>Optionale Features</STRONG> sehen, können Sie Microsoft Azure Active Directory Connect beenden und mit dem nächsten Abschnitt, <EM>Erforderliche Schritte in Office&nbsp;365 oder Exchange Online</EM>, fortfahren.

    
    5.  Nachdem Sie die Option **Öffentliche Exchange-E-Mail-Ordner** deaktiviert haben, klicken Sie weiter auf **Weiter**, bis Sie sich auf dem Bildschirm **Bereit zur Konfiguration** befinden, und klicken Sie dann auf **Konfigurieren**.

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-AcceptedDomain](https://technet.microsoft.com/de-de/library/aa995975\(v=exchg.150\))

  - [Get-PublicFolder](https://technet.microsoft.com/de-de/library/aa997615\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/de-de/library/jj733416\(v=exchg.150\))

  - [Set-PublicFolder](https://technet.microsoft.com/de-de/library/aa998596\(v=exchg.150\))

  - [Get-PublicFolderStatistics](https://technet.microsoft.com/de-de/library/aa998663\(v=exchg.150\))

  - [Get-PublicFolderClientPermission](https://technet.microsoft.com/de-de/library/bb124365\(v=exchg.150\))

  - [Get-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183212)

  - [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183213)

**Erforderliche Schritte in Office 365 oder Exchange Online**

1.  Stellen Sie sicher, dass keine Migrationsanforderungen für öffentliche Ordner vorhanden sind. Wenn sie vorhanden sind, löschen Sie sie, da es sonst zu einem Fehler mit Ihrer eigenen Migrationsanforderung kommt. Dieser Schritt ist nicht in allen Fällen erforderlich. Er ist nur erforderlich, wenn Sie glauben, dass in der Pipeline möglicherweise bereits eine Migrationsanforderung vorhanden ist.
    
    Eine vorhandene Migrationsanforderung kann einen von zwei Typen haben: Batchmigration oder serielle Migration. Die Befehle zum Erkennen von Anforderungen für die einzelnen Typen und zum Entfernen von Anforderungen der einzelnen Typen sind nachfolgend aufgeführt.
    

    > [!IMPORTANT]
    > Bevor Sie eine Migrationsanforderung entfernen, ist es wichtig zu verstehen, warum eine solche Anforderung vorhanden war. Durch das Ausführen der folgenden Befehle können Sie bestimmen, wann eine frühere Anforderung erstellt wurde. Dies ist nützlich, um möglicherweise aufgetreten Probleme zu diagnostizieren. Sie müssen möglicherweise mit anderen Administratoren in Ihrer Organisation sprechen, um herauszufinden, warum die Änderung vorgenommen wurde.

    
    Im folgenden Beispiel werden vorhandene serielle Migrationsanforderungen ermittelt.
    
        Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics -IncludeReport | Format-List
    
    Im folgenden Beispiel werden alle vorhandenen seriellen Migrationsanforderungen für öffentliche Ordner entfernt.
    
        Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
    
    Im folgenden Beispiel werden vorhandene Batchmigrationsanforderungen ermittelt.
    
        $batch = Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
    
    Im folgenden Beispiel werden alle vorhandenen Batchmigrationsanforderungen für öffentliche Ordner entfernt.
    
        $batch | Remove-MigrationBatch -Confirm:$false

2.  Stellen Sie sicher, dass in Office 365 keine öffentlichen Ordner oder öffentliche Ordner-Postfächer vorhanden sind.
    

    > [!IMPORTANT]
    > Wenn in Office&nbsp;365 öffentliche Ordner angezeigt werden, ist es wichtig herauszufinden, warum sie vorhanden sind, und wer in Ihrer Organisation eine öffentliche Ordner-Hierarchie gestartet hat, bevor Sie die öffentlichen Ordner oder öffentliche Ordner-Postfächer entfernen.

    
    1.  Führen Sie in Office 365 oder Exchange Online PowerShell den folgenden Befehl aus, um zu sehen, ob öffentliche Ordner-Postfächer vorhanden sind.
        
            Get-Mailbox -PublicFolder 
    
    2.  Wenn der Befehl keine Öffentliche Ordner-Postfächer zurückgibt, fahren Sie mit Schritt 3: Generieren der CSV-Dateien fort. Wenn der Befehl Öffentliche Ordner-Postfächer zurückgibt, führen Sie den folgenden Befehl aus, um herauszufinden, ob Öffentliche Ordner vorhanden sind:
        
            Get-PublicFolder
    
    3.  Wenn in Office 365 oder Exchange Online öffentliche Ordner vorhanden sind, entfernen Sie diese, indem Sie den folgenden PowerShell-Befehl ausführen. Stellen Sie sicher, dass Sie alle Informationen gespeichert haben, die sich in den öffentlichen Ordnern in Office 365 befanden. Alle in den öffentlichen Ordnern enthaltenen Informationen werden endgültig gelöscht, wenn Sie die öffentlichen Ordner entfernen.
        
            Get-MailPublicFolder | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
            
            
            Get-PublicFolder -GetChildren \ | Remove-PublicFolder -Recurse -Confirm:$false
    
    4.  Führen Sie, nachdem die öffentlichen Ordner entfernt wurden, die folgenden Befehle aus, um alle Postfächer für öffentliche Ordner zu entfernen.
        
            $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
            
            Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false
            
            Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false

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

1.  Führen Sie auf dem Exchange-Legacyserver das Skript `Export-PublicFolderStatistics.ps1` aus, um die Zuordnungsdatei für Ordnernamen zur Ordnergröße zu erstellen. Dieses Skript muss immer von einem lokalen Administrator ausgeführt werden. Die Datei enthält zwei Spalten: **FolderName** und **FolderSize**. Die Werte für die Spalte **FolderSize** werden in Byte angezeigt. Beispiel: **\\PublicFolder01,10000**.
    
        .\Export-PublicFolderStatistics.ps1  <Folder to size map path> <FQDN of source server>
    
      - *FQDN of source server* entspricht dem vollqualifizierten Domänennamen des Postfachservers, auf dem die Hierarchie Öffentlicher Ordner gehostet wird.
    
      - *Folder to size map path* entspricht dem Dateinamen und dem Pfad im freigegebenen Netzwerkordner, in dem Sie die CSV-Datei speichern möchten. Weiter unten in diesem Thema müssen Sie über die Exchange Online PowerShell auf diese Datei zugreifen. Wenn Sie nur den Dateinamen angeben, wird die Datei auf dem lokalen Computer im aktuellen PowerShell-Verzeichnis generiert.
    
      - Falls erforderlich, entfernen Sie alle E-Mail-aktivierten Systemordner aus der Skriptausgabe, bevor Sie fortfahren.

2.  Führen Sie das Skript `PublicFolderToMailboxMapGenerator.ps1` aus, um die Datei zur Zuordnung von Öffentlichen Ordnern zu Postfächern zu erstellen. Diese Datei wird verwendet, um die richtige Anzahl von Postfächern für Öffentliche Ordner in Exchange Online zu berechnen.
    
        .\PublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes> <Folder to size map path> <Folder to mailbox map path>
    

    > [!IMPORTANT]
    > Die Datei zur Zuordnung von öffentlichen Ordnern zu Postfächern sollte 1.000 Zeilen nicht überschreiten. Wenn diese Datei 1.000 Zeilen überschreitet, muss die Struktur des öffentlichen Ordners vereinfacht werden. Das Fortfahren mit einer Datei von als 1.000 Zeilen wird nicht empfohlen, dabei kann es zu Migrationsfehlern kommen.

    
      - Bevor Sie das Skript ausführen, verwenden Sie das folgende Cmdlet, um die aktuellen Grenzwerte für öffentliche Ordner in Ihrem Exchange Online-Mandanten zu überprüfen. Notieren Sie sich dann die aktuellen Kontingentwerte für öffentliche Ordner. `Get-OrganizationConfig | fl *quota*`
        
        Der Standardwert in Exchange Online ist 1,7 GB für **DefaultPublicFolderIssueWarningQuota** und 2 GB für **DefaultPublicFolderProhibitPostQuota**.
    
      - *Maximum mailbox size in bytes* entspricht der maximalen Größe, die Sie für neue Postfächer für öffentliche Ordner festlegen möchten. Die maximale Größe von Postfächern für öffentliche Ordner in Exchange Online beträgt 100 GB. Es wird empfohlen, diese Einstellung auf 15 GB festzulegen, sodass das Anwachsen aller Öffentliche Ordner-Postfächer unterstützt wird. Exchange Online verfügt über ein Standardkontingent „Bereitstellen verbieten“ von 2 GB. Wenn Sie einzelne öffentliche Ordner besitzen, die größer als 2 GB sind, können Sie eine der folgenden Optionen verwenden, um dieses Problem zu beheben:
        
          - Bevor Sie das Migrationsbatch starten, erhöhen Sie das Standardkontingent „Bereitstellen verbieten“, indem Sie das folgende Cmdlet ausführen:
            
            `Set-OrganizationConfig -DefaultPublicFolderProhibitPostQuota <size value> -DefaultPublicFolderIssueWarningQuota <size value>`
        
          - Vor dem Start des Migrationsbatches löschen Sie die Inhalte des öffentlichen Ordners, um die Inhaltsgröße auf 2 GB oder weniger zu reduzieren.
        
          - Teilen Sie vor dem Start des Migrationsbatches den öffentlichen Ordner in mehrere öffentliche Ordner auf, die jeweils maximal 2 GB groß sind.
        

        > [!NOTE]
        > Wenn der öffentliche Ordner größer als 30 GB ist und das Löschen von Inhalten oder das Aufteilen in mehrere öffentliche Ordner nicht möglich ist, wird empfohlen, die öffentlichen Ordner nicht zu Exchange Online zu verschieben.

    
      - *Folder to size map path* ist der Dateipfad der .csv-Datei, die Sie durch die Ausführung des Skripts `Export-PublicFolderStatistics.ps1` erstellt haben.
    
      - *Folder to mailbox map path* entspricht dem Dateinamen und -pfad der .csv-Datei für die Zuordnung von Ordnern zu Postfächern, die Sie in diesem Schritt erstellen. Wenn Sie nur den Dateinamen angeben, wird die Datei auf dem lokalen Computer im aktuellen PowerShell-Verzeichnis generiert.


> [!NOTE]
> Nachdem die Skripts ausgeführt und die csv.-Dateien erstellt wurden, werden keine neuen öffentlichen Ordner oder Updates für vorhandene öffentliche Ordner erfasst.



## Schritt 4: Erstellen der Öffentliche Ordner-Postfächer in Exchange Online

1.  Führen Sie den folgenden Befehl aus, um die Zielpostfächer für öffentliche Ordner zu erstellen. Mit dem Skript wird ein Zielpostfach für jedes Postfach in der CSV-Datei erstellt, die Sie in Schritt 3 durch Ausführen des „PublicFoldertoMailboxMapGenerator.ps1„-Skripts generiert haben.
    
        .\Create-PublicFolderMailboxesForMigration.ps1 -FolderMappingCsv Mapping.csv -EstimatedNumberOfConcurrentUsers:<estimate>
    
    *Mapping.csv* ist die Datei, die durch Ausführen des Skripts „PublicFoldertoMailboxMapGenerator.ps1“ in Schritt 3 generiert wurde. Die geschätzte Anzahl der gleichzeitigen Benutzerverbindungen beim Durchsuchen einer Hierarchie öffentlicher Ordner ist in der Regel kleiner als die Gesamtzahl der Benutzer in einer Organisation.

## Schritt 5: Starten der Migrationsanforderung

1.  Führen Sie auf dem älteren Exchange-Server den folgenden Befehl zum Synchronisieren von für E-Mail aktivierten öffentlichen Ordnern vom lokalen Active Directory mit Exchange Online aus.
    
        Sync-MailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
    `Credential` ist Ihr Office 365-Benutzername und das Kennwort. `CsvSummaryFile` ist der Dateipfad für das Verzeichnis, in dem Sie das Protokoll der Synchronisierungsvorgänge und Fehler (im CSV-Format) speichern möchten.
    

    > [!NOTE]
    > Es wird empfohlen, dass Sie die vom Skript ausgeführten Aktionen zunächst simulieren, bevor Sie es tatsächlich ausführen. Führen Sie das Skript hierzu mit dem <CODE>-WhatIf</CODE>-Parameter aus.



2.  Rufen Sie auf dem Exchange-Legacyserver die folgenden Informationen ab, die zur Ausführung der Migrationsanforderung erforderlich sind:
    
    1.  Suchen Sie den `LegacyExchangeDN` des Kontos des Benutzers, der Mitglied der Rolle "Öffentlicher Ordner-Administrator" ist. Dies ist der gleiche Benutzer, dessen Anmeldeinformationen Sie in Schritt 3 dieses Verfahrens benötigen.
        
            Get-Mailbox <PublicFolder_Administrator_Account> | Select-Object LegacyExchangeDN
    
    2.  Suchen Sie den `LegacyExchangeDN` eines Postfachservers mit einer Datenbank für öffentliche Ordner.
        
            Get-ExchangeServer <public folder server> | Select-Object -Expand ExchangeLegacyDN
    
    3.  Suchen Sie den FQDN des Outlook Anywhere-Hostnamens. Wenn Sie mehrere Instanzen von Outlook Anywhere haben, wird empfohlen, die Instanz auszuwählen, die dem Migrationsendpunkt oder den Replikaten Öffentlicher Order in der Legacy-Exchange-Organisation am nächsten ist. Mit dem folgenden Befehl werden alle Instanzen von Outlook Anywhere gefunden:
        
            Get-OutlookAnywhere | Format-Table Identity,ExternalHostName

3.  Führen Sie in der Office 365 PowerShell die folgenden Befehle aus, um die im vorherigen Schritt zurückgegebenen Informationen an Variablen weiterzugeben, die dann in der Migrationsanforderung verwendet werden.
    
    1.  Geben Sie die Anmeldeinformationen eines Benutzers mit Administratorberechtigungen auf dem Exchange-Legacyserver an die Variable `$Source_Credential` weiter. Die Migrationsanforderung, die in Exchange Online ausgeführt wird, verwendet diese Anmeldeinformationen, um Zugriff auf Ihre Exchange-Legacyserver zu erhalten, um die Inhalte zu kopieren.
        
            $Source_Credential = Get-Credential <source_domain\PublicFolder_Administrator_Account>
    
    2.  Verwenden Sie den `ExchangeLegacyDN` des Migrationsbenutzers auf dem Exchange-Legacyservers, den Sie in Schritt 2a gefunden haben, und geben Sie ihn an die Variable `$Source_RemoteMailboxLegacyDN` weiter.
        
            $Source_RemoteMailboxLegacyDN = "<paste the value here>"
    
    3.  Verwenden Sie den `ExchangeLegacyDN` des Öffentlichen Ordnerservers, den Sie oben in Schritt 2b gefunden haben, und geben Sie ihn an die Variable `$Source_RemotePublicFolderServerLegacyDN` weiter.
        
            $Source_RemotePublicFolderServerLegacyDN = "<paste the value here>"
    
    4.  Verwenden Sie den externen Hostnamen von Outlook Anywhere, den Sie oben in Schritt 2c gefunden haben, und geben Sie ihn an die Variable `$Source_OutlookAnywhereExternalHostName` weiter.
        
            $Source_OutlookAnywhereExternalHostName = "<paste the value here>"

4.  Führen Sie abschließend in der Exchange Online PowerShell die folgenden Befehle aus, um die Migrationsanforderung zu erstellen.
    

    > [!NOTE]
    > Die Authentifizierungsmethode im folgenden Exchange-Verwaltungsshell-Beispiel muss mit Ihren Outlook Anywhere-Einstellungen übereinstimmen. Andernfalls tritt beim Ausführen des Befehls ein Fehler auf.

    
        $PfEndpoint = New-MigrationEndpoint -PublicFolder -Name PublicFolderEndpoint -RPCProxyServer $Source_OutlookAnywhereExternalHostName -Credentials $Source_Credential -SourceMailboxLegacyDN $Source_RemoteMailboxLegacyDN -PublicFolderDatabaseServerLegacyDN $Source_RemotePublicFolderServerLegacyDN -Authentication Basic
        
        [byte[]]$bytes = Get-Content -Encoding Byte <folder_mapping.csv>
        
        New-MigrationBatch -Name PublicFolderMigration -CSVData $bytes -SourceEndpoint $PfEndpoint.Identity -NotificationEmails <email addresses for migration notifications>
    
    Dabei ist die \<*folder\_mapping.csv*\> die Datei, die in Schritt 3: Generieren der CSV-Dateien generiert wurde.

5.  Starten Sie die Migration mit dem folgenden Befehl:
    
        Start-MigrationBatch PublicFolderMigration

Obwohl die Batchmigrationen mit dem **New-MigrationBatch**-Cmdlet in der Exchange-Verwaltungsshell erstellt werden müssen, können Status und Fertigstellung der Migration in EAC angezeigt und verwaltet werden. Da das **New-MigrationBatch**-Cmdlet eine Postfachmigrationsanforderung für jedes Postfach für öffentliche Ordner initiiert, können Sie den Status dieser Anforderungen mithilfe der Seite für die Postfachmigration anzeigen. Sie können zur Seite für die Postfachmigration wechseln und Migrationsberichte erstellen, die Ihnen per E-Mail gesendet werden können, indem Sie Folgendes vornehmen:

1.  Melden Sie sich bei Exchange Online an, und öffnen Sie EAC.

2.  Navigieren Sie zu **Postfach** \> **Migration**.

3.  Wählen Sie die soeben erstellte Migrationsanforderung aus, und klicken Sie im Bereich **Details** auf **Details anzeigen**.

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Get-ExchangeServer](https://technet.microsoft.com/de-de/library/bb123873\(v=exchg.150\))

  - [Get-OutlookAnywhere](https://technet.microsoft.com/de-de/library/bb124263\(v=exchg.150\))

  - [New-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218636\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/de-de/library/jj733416\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequest](https://technet.microsoft.com/de-de/library/jj218718\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequestStatistics](https://technet.microsoft.com/de-de/library/jj218697\(v=exchg.150\))

## Schritt 6: Sperren der Öffentlichen Ordner auf dem Exchange-Legacyserver für die endgültige Migration (Ausfallzeit erforderlich)

Bis zu diesem Zeitpunkt im Migrationsprozess konnten Benutzer auf Öffentliche Ordner zugreifen. In den nächsten Schritten werden die Benutzer von den älteren Öffentlichen Ordnern abgemeldet, und die Ordner werden gesperrt, bis die abschließende Synchronisierung im Rahmen des Migrationsvorgangs beendet ist. Während dieses Vorgangs können die Benutzer nicht auf Öffentliche Ordner zugreifen. Außerdem werden alle E-Mails, die an E-Mail-aktivierte Öffentliche Ordner gesendet werden, in die Warteschlange gestellt und erst nach Abschluss der Öffentliche Ordner-Migration übermittelt.

Bevor Sie den Befehl `PublicFoldersLockedForMigration` wie unten beschrieben ausführen, vergewissern Sie sich, dass alle Aufträge den Status **Synchronisiert** aufweisen. Führen Sie hierzu den Befehl `Get-PublicFolderMailboxMigrationRequest` aus. Fahren Sie mit diesem Schritt erst dann fort, nachdem Sie überprüft haben, ob alle Aufträge den Status **Synchronisiert** aufweisen.

Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die älteren Öffentlichen Ordner bis zum Abschluss des Vorgangs zu sperren.

    Set-OrganizationConfig -PublicFoldersLockedForMigration:$true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)).

Wenn Ihre Organisation über mehrere Datenbanken für Öffentliche Ordner verfügt, müssen Sie warten, bis die Replikation Öffentlicher Ordner abgeschlossen wurde, und sicherstellen, dass für alle Datenbanken für Öffentliche Ordner das Kennzeichen `PublicFoldersLockedForMigration` gesetzt ist und alle offenen Änderungen, die von Benutzern in letzter Zeit an Ordnern vorgenommen wurden, organisationsweit übernommen wurden. Dieser Vorgang kann mehrere Stunden in Anspruch nehmen.

## Schritt 7: Abschließen der Migration Öffentlicher Ordner (Ausfallzeit erforderlich)

Führen Sie zum Abschließen der Migration für öffentliche Ordner den folgenden Befehl aus:

    Complete-MigrationBatch PublicFolderMigration

Nach Abschluss die Migration führt Exchange eine endgültige Synchronisierung zwischen dem Legacy-Exchange-Server und Exchange Online durch. Ist die abschließende Synchronisierung erfolgreich, werden die öffentlichen Ordner auf dem Exchange Online-Server entsperrt, und der Status des Migrationsbatches wird in Wird abgeschlossen und dann in **Abgeschlossen** geändert. In der Regel dauert es einige Stunden, bis der Status des Migrationsbatches von **Synchronisiert** in **Wird abgeschlossen** geändert wird. Erst dann beginnt die abschließende Synchronisierung.

Wenn Sie eine Hybridbereitstellung zwischen Ihren lokalen Exchange-Servern und Office 365 konfiguriert haben, müssen Sie den folgenden Befehl in Exchange Online PowerShell ausführen, nachdem die Migration abgeschlossen ist:

    Set-OrganizationConfig -RemotePublicFolderMailboxes $Null -PublicFoldersEnabled Local

## Schritt 8: Testen und Entsperren der Migration Öffentlicher Ordner

Nachdem Sie die Migration Öffentlicher Ordner abgeschlossen haben, sollten Sie den folgenden Test durchführen und so sicherstellen, dass die Migration erfolgreich war. Dadurch können Sie die Hierarchie der migrierten öffentlichen Ordner testen, bevor Sie auf die Verwendung von öffentlichen Ordnern in Office 365 oder Exchange Online umstellen.

1.  Weisen Sie in Office 365 oder Exchange Online PowerShell einige Testpostfächer so zu, dass sie als das Standardpostfach für öffentliche Ordner ein neu migriertes Postfach für öffentliche Ordner verwenden.
    
        Set-Mailbox -Identity <Test User> -DefaultPublicFolderMailbox <Public Folder Mailbox Identity>

2.  Melden Sie sich mit dem im vorherigen Schritt identifizierten Testbenutzer bei Outlook 2007 oder höher an, und führen Sie denn die folgenden Öffentliche Ordner-Tests durch:
    
      - Zeigen Sie die Hierarchie an.
    
      - Prüfen Sie die Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

3.  Wenn Probleme auftreten, lesen Sie Durchführen eines Rollbacks der Migration weiter unten in diesem Thema. Wenn der Inhalt und die Hierarchie des öffentlichen Ordners akzeptabel sind und wie erwartet funktionieren, fahren Sie mit dem nächsten Schritt fort.

4.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um anzugeben, dass die Migration der Öffentlichen Ordner abgeschlossen ist.
    
        Set-OrganizationConfig -PublicFolderMigrationComplete:$true

5.  Nachdem Sie den Abschluss der Migration überprüft haben, führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um sicherzustellen, dass der *PublicFoldersEnabled*-Parameter für **Set-OrganizationConfig** auf `Local` festgelegt ist:
    
        Set-OrganizationConfig -PublicFoldersEnabled Local

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

[Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

[Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

[Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\))

## Woher weiß ich, dass der Vorgang erfolgreich war?

Unter Schritt 2: Vorbereiten der Migration wurden Sie aufgefordert, Momentaufnahmen der Struktur Öffentlicher Ordner, der Statistikdaten und der Berechtigungen vor der Migration zu erstellen. Mit den folgenden Schritten können Sie überprüfen, ob die Migration Öffentlicher Ordner erfolgreich war, indem Sie die gleichen Momentaufnahmen nach Abschluss der Migration erstellen. Sie können dann die Daten in beiden Dateien vergleichen, um den Erfolg zu überprüfen.

1.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der neuen Ordnerstruktur zu erstellen.
    
        Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Cloud_PFStructure.xml

2.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der Statistikdaten von Öffentlichen Ordnern (wie Anzahl von Elementen, Größe und Besitzer) zu erstellen.
    
        Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\PFMigration\Cloud_PFStatistics.xml

3.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen zu erstellen.
    
        Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML  C:\PFMigration\Cloud_PFPerms.xml

## Entfernen von Datenbanken für Öffentliche Ordner von den Exchange-Legacyservern

Nachdem die Migration abgeschlossen wurde und Sie sichergestellt haben, dass die Öffentlichen Exchange Online-Ordner erwartungsgemäß funktionieren, sollten Sie die Datenbanken für Öffentliche Ordner auf den Exchange-Legacyservern entfernen.


> [!IMPORTANT]
> Da all Ihre Postfächer vor der Migration der öffentlichen Ordner in Office 365 migriert wurden, wird dringend empfohlen, den Datenverkehr über Office 365 (dezentraler E-Mail-Verkehr) statt zentral über Ihre lokale Umgebung zu leiten. Wenn Sie den zentralen E-Mail-Verkehr beibehalten möchten, kann es zu Zustellproblemen bei Ihren öffentlichen Ordnern kommen, da Sie die Postfachdachtenbanken des öffentlichen Ordners aus Ihrer lokalen Organisation entfernt haben.



  - Nähere Informationen zum Entfernen von Öffentliche Ordner-Datenbanken von Exchange 2007-Servern finden Sie unter [Entfernen Öffentlicher Ordner-Datenbanken](https://go.microsoft.com/fwlink/?linkid=123678).

  - Nähere Informationen zum Entfernen von Öffentliche Ordner-Datenbanken von Exchange 2010-Servern finden Sie unter [Entfernen von Öffentliche Ordner-Datenbanken](https://go.microsoft.com/fwlink/?linkid=81409).

## Durchführen eines Rollbacks der Migration

Wenn bei der Migration Probleme auftreten und Sie die Öffentlichen Ordner von einem Exchange-Legacyserver erneut aktivieren müssen, führen Sie die folgenden Schritte aus.


> [!WARNING]
> Wenn Sie ein Rollback der Migration auf die Exchange-Legacyserver durchführen, gehen alle E-Mails verloren, die an E-Mail-aktivierte Öffentliche Ordner gesendet wurden, sowie Inhalte, die nach der Migration in Öffentlichen Ordnern bereitgestellt wurden. Um diese Inhalte zu speichern, müssen Sie die Inhalte der öffentlichen Ordner in einer PST-Datei speichern und diese dann nach Abschluss des Rollbacks in die älteren öffentlichen Ordner importieren.



1.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die älteren Öffentlichen Exchange-Ordner zu entsperren. Dieser Vorgang kann mehrere Stunden in Anspruch nehmen.
    
        Set-OrganizationConfig -PublicFoldersLockedForMigration:$False

2.  Führen Sie in Exchange Online PowerShell die folgenden Befehle aus, um alle Öffentlichen Exchange Online-Ordner zu entfernen.
    
        $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
        
        Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        
        Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force

3.  Führen Sie auf dem Exchange-Legacyserver den folgenden Befehl aus, um die `PublicFolderMigrationComplete`-Kennzeichnung auf `$false` festzulegen.
    
        Set-OrganizationConfig -PublicFolderMigrationComplete:$False

## Migrieren von Öffentlichen Ordnern zu Office 365 mit PST-Export von Outlook

Es wird empfohlen, nicht das PST-Exportfeature von Outlook zum Migrieren öffentlicher Ordner zu Office 365 oder Exchange Online zu verwenden, wenn die Hierarchie der öffentlichen Ordner mehr als 30 GB umfasst. Das Anwachsen des Postfachs für öffentliche Ordner in Office 365 wird über ein Feature zur automatischen Aufteilung verwaltet, welches das Postfach für öffentliche Ordner aufteilt, wenn Größenkontingente überschritten werden. Das plötzliche Anwachsen der Postfächer für Öffentliche Ordner kann nicht von der automatischen Aufteilung verwaltet werden, wenn Sie Öffentliche Ordner über den PST-Export migrieren. Sie müssen dann möglicherweise bis zu zwei Wochen warten, bis die Daten durch automatische Aufteilung aus dem primären Postfach verschoben werden. Zudem sollten Sie Folgendes bedenken, bevor Sie den PST-Export von Outlook verwenden, um öffentliche Ordner zu Office 365 oder Exchange Online zu exportieren:

  - Berechtigungen für Öffentliche Ordner gehen während dieses Vorgangs verloren. Erfassen Sie die aktuellen Berechtigungen vor der Migration, und fügen Sie sie nach der Migration manuell hinzu.

  - Wenn Sie komplexe Berechtigungen verwenden oder viele Ordner zu migrieren haben, sollten Sie die Cmdlet-Methode zur Migration verwenden.

  - Alle Änderungen an Elementen und Ordnern, die während der PST-Exportmigration an den Öffentlichen Quellordnern vorgenommen werden, gehen verloren. Daher wird empfohlen, die Cmdlet-Methode zu verwenden, wenn diese Export- und Importvorgänge lange dauern.

Wenn Sie Ihre Öffentlichen Ordner dennoch mithilfe von PST-Dateien migrieren möchten, sollten Sie die folgenden Schritte ausführen, um eine erfolgreiche Migration sicherzustellen.

1.  Befolgen Sie die Anweisungen in Schritt 1: Herunterladen der Migrationsskripts, um die Migrationsskripts herunterzuladen. Sie müssen nur die Datei `PublicFolderToMailboxMapGenerator.ps1` herunterladen.

2.  Führen Sie Schritt 2 von Schritt 3: Generieren der CSV-Dateien aus, um die Datei zur Zuordnung von Öffentlichen Ordnern zu Postfächern zu erstellen. Diese Datei wird verwendet, um die richtige Anzahl von Postfächern für Öffentliche Ordner in Exchange Online zu berechnen.

3.  Erstellen Sie die benötigten Postfächer für Öffentliche Ordner basierend auf der Zuordnungsdatei. Weitere Informationen finden Sie unter [Erstellen eines Postfachs für öffentliche Ordner](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/create-public-folder-mailbox).

4.  Erstellen Sie in jedem Postfach für Öffentliche Ordner mithilfe des Cmdlets New-PublicFolder den Öffentlichen Ordner der obersten Ebene, und geben Sie dabei den Parameter *Mailbox* an.

5.  Exportieren und importieren Sie die PST-Dateien mithilfe von Outlook.

6.  Legen Sie die Berechtigungen für die Öffentlichen Ordner mithilfe des Exchange Admin Centers (EAC) fest. Weitere Informationen finden Sie unter [Step 3: Assign permissions to the public folder](set-up-public-folders-in-a-new-organization-exchange-2013-help.md) im Thema [Einrichten öffentlicher Ordner in einer neuen Organisation](set-up-public-folders-in-a-new-organization-exchange-2013-help.md).


> [!WARNING]
> Wenn Sie bereits eine PST-Migration gestartet haben und ein Problem aufgetreten ist, weil das primäre Postfach voll ist, können Sie die PST-Migration auf zwei Arten wiederherstellen: 
> <OL>
> <LI>
> <P>Warten, bis die Daten von der automatischen Aufteilung aus dem primären Postfach verschoben werden. Dies kann bis zu zwei Wochen dauern. Allerdings können alle Öffentlichen Ordner in einem vollständig gefüllten Postfach für Öffentliche Ordner keine neuen Inhalte empfangen, bis die automatische Aufteilung abgeschlossen ist.</P>
> <LI>
> <P><A href="https://docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/create-public-folder-mailbox">Erstellen eines Postfachs für öffentliche Ordner</A> und anschließendes Verwenden des Cmdlets <STRONG>New-PublicFolder</STRONG> mit dem Parameter <EM>Mailbox</EM>, um die verbleibenden Öffentlichen Ordner im sekundären Postfach für Öffentliche Ordner zu erstellen. In diesem Beispiel wird ein neuer Öffentlicher Ordner mit dem Namen PF201 im sekundären Postfach für Öffentliche Ordner erstellt.</P><PRE><CODE>New-PublicFolder -Name PF201 -Mailbox SecondaryPFMbx</CODE></PRE></LI></OL>



## Neu bei Office 365?


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Bb123521.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="Das Kurzsymbol für LinkedIn Learning" alt="Das Kurzsymbol für LinkedIn Learning" /> <strong>Neu bei Office 365?</strong><br />
Entdecken Sie die kostenlosen Videokurse für <a href="https://support.office.com/de-de/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a>, präsentiert von LinkedIn Learning.</p></td>
</tr>
</tbody>
</table>

