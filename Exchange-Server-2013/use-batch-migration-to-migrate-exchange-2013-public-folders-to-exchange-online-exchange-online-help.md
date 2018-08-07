---
title: 'Batchmigration vonöffentl. Exchange 2013-Ordnern zu Exchange Online'
TOCTitle: Migrieren von Exchange 2013-basierten öffentlichen Ordnern zu Exchange Online mithilfe einer Batchmigration
ms:assetid: 25a5234c-dd2c-487b-8541-3655fbeb030a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt798260(v=EXCHG.150)
ms:contentKeyID: 74432744
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Migrieren von Exchange 2013-basierten öffentlichen Ordnern zu Exchange Online mithilfe einer Batchmigration

 

_**Letztes Änderungsdatum des Themas:** 2018-03-26_

**Zusammenfassung:**  In diesem Artikel erfahren Sie, wie Sie moderne öffentliche Ordner von Exchange 2013 nach Office 365 verschieben.

Die öffentlichen Ordner von Exchange 2013 zu Migration erfordert Exchange Server 2013 CU15 oder höher in Ihrer lokalen Umgebung.


> [!NOTE]
> Verwenden Sie zur Planung und Durchführung Ihrer Migration die <A href="https://go.microsoft.com/fwlink/p/?linkid=845314">Exchange&nbsp;2016-Version dieses Artikels</A>, falls Ihre Organisation sowohl Exchange&nbsp;2013-basierte als auch Exchange&nbsp;2016-basierte öffentliche Ordner verwendet und Sie alle diese Ordner nach Exchange&nbsp;Online verschieben möchten. Auf Ihren Exchange&nbsp;2013-Servern muss auch dann CU15 oder höher installiert sein.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Wenn Sie auf Exchange Server 2013 CU15 oder höher aktualisieren, müssen Sie auch Active Directory vorbereiten. Ansonsten schlägt die Migration Ihrer öffentlichen Ordner fehl. Durch die Active Directory-Vorbereitung wird sichergestellt, dass alle relevanten PowerShell-Cmdlets und -Parameter verfügbar sind, die Sie zur Vorbereitung und Durchführung der Migration benötigen. Weitere Informationen finden Sie unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).

  - In Exchange Online müssen Sie Mitglied der Rollengruppe „Organisationsverwaltung\&quot; sein. Diese Rollengruppe unterscheidet sich von den Berechtigungen, die Ihnen zugewiesen wurden, als Sie Office 365 oder Exchange Online abonniert haben. Details dazu, wie Sie die Rollengruppe „Organisationsverwaltung\&quot; aktivieren können, finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - In Exchange Server 2013 müssen Sie Mitglied der Rollengruppe „Organisationsverwaltung\&quot; oder der Rollengruppe „Serververwaltung RBAC\&quot; sein. Details hierzu finden Sie unter [Hinzufügen von Mitgliedern zu einer Rollengruppe](https://go.microsoft.com/fwlink/?linkid=299212).

  - Vor Beginn der Migration Ihrer öffentlichen Ordner empfehlen wir Folgendes: Falls ein öffentlicher Ordner in Ihrer Organisation größer als 25 GB ist, sollten Sie Inhalte aus diesem Ordner löschen, um ihn zu verkleinern, oder seine Inhalte auf mehrere kleinere öffentliche Ordner verteilen. Beachten Sie, dass der hier genannte Grenzwert von 25 GB nur für den öffentlichen Ordner selbst gilt, nicht für möglicherweise vorhandene untergeordnete Ordner oder Unterordner des Ordners. Wenn keine dieser Möglichkeiten infrage kommt, empfehlen wir Ihnen, von einer Verschiebung Ihrer öffentlichen Ordner nach Exchange Online abzusehen. Weitere Informationen finden Sie unter [Exchange Online-Begrenzungen](https://go.microsoft.com/fwlink/p/?linkid=391188).
    

    > [!NOTE]
    > Wenn Ihre aktuellen Kontingente für öffentliche Ordner in Exchange&nbsp;Online kleiner als 25&nbsp;GB sind, können Sie sie mithilfe der Parameter „DefaultPublicFolderIssueWarningQuota&amp;quot; und „DefaultPublicFolderProhibitPostQuota&amp;quot; des Cmdlets <A href="https://go.microsoft.com/fwlink/p/?linkid=844062">Set-OrganizationConfig</A> vergrößern.



  - In Office 365 und Exchange Online können Sie maximal 1.000 Postfächer für öffentliche Ordner erstellen.

  - Wenn Sie Benutzer zu Office 365 migrieren möchten, sollten Sie die Benutzermigration vor der Migration Ihrer öffentlichen Ordner abschließen. Weitere Informationen finden Sie unter [Methoden zum Migrieren mehrerer E-Mail-Konten zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=842798).

  - Der Proxy für den Postfachreplikationsdienst (Mailbox Replication Service, MRS) muss auf mindestens einem Exchange-Server aktiviert sein, und zwar auf einem Server, der auch Postfächer für öffentliche Ordner hostet. Details finden Sie unter [Aktivieren des Proxyendpunkts für den Postfachreplikationsdienst für Remoteverschiebungen](enable-the-mrs-proxy-endpoint-for-remote-moves-exchange-2013-help.md).

  - Die in diesem Artikel beschriebenen Migrationsverfahren lassen sich nicht über das Exchange Admin Center (EAC) durchführen. Sie müssen stattdessen die Exchange-Verwaltungsshell auf Ihren Exchange 2013-Servern verwenden. In Exchange Online müssen Sie Exchange Online PowerShell verwenden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=842801).

  - Die Migration gelöschter Elemente und gelöschter Ordner von Exchange 2013 zu Exchange Online wird unterstützt. Wir empfehlen Ihnen, vor Beginn der Migration alle gelöschten Ordner und Ordnerelemente zu überprüfen und alle Ordner und Elemente, die Sie in Exchange Online nicht benötigen, endgültig zu löschen. Beachten Sie: Sobald ein Element endgültig gelöscht wurde, kann es nicht wiederhergestellt werden.
    
    Mithilfe der folgenden Befehle können Sie eine Liste aller gelöschten öffentlichen Ordner im Exchange-Dumpster (in Ihrer lokalen Exchange-Umgebung) aufrufen:
    
        Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null"} | ft name,foldersize
    
    Zum endgültigen Löschen eines bestimmten Ordners (in diesem Beispiel ein Ordner namens „Calendar2\&quot;) können Sie den folgenden Befehl verwenden:
    
        Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null" -and $_.Name -eq "Calendar2"} | Remove-PublicFolder

  - Lesen Sie sich diesen Artikel vollständig durch, bevor Sie beginnen. Einige Schritte erfordern Downtime. Während dieser Downtime kann niemand auf die öffentlichen Ordner zugreifen.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Schritt 1: Herunterladen der Migrationsskripts

1.  Laden Sie alle Skripts und Unterstützungsdateien unter [Exchange 2013/2016 Public Folders Migration Scripts](https://go.microsoft.com/fwlink/p/?linkid=844893) herunter.

2.  Speichern Sie die Skripts auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts. Stellen Sie sicher, dass alle Skripts unter demselben Speicherort gespeichert werden.

Es werden folgende Skripts und Dateien heruntergeladen:

  - `Sync-ModernMailPublicFolders.ps1`: Dieses Skript synchronisiert alle Objekte des Typs „E-Mail-aktivierter öffentlicher Ordner\&quot; zwischen Ihrer lokalen Exchange-Umgebung und Office 365. Dieses Skript wird auf einem Exchange 2013-Server ausgeführt.

  - `SyncModernMailPublicFolders.strings.psd1`: Diese Unterstützungsdatei wird vom Skript „Sync-ModernMailPublicFolders.ps1\&quot; verwendet und sollte an denselben Speicherort heruntergeladen werden.

  - `Export-ModernPublicFolderStatistics.ps1`: Dieses Skript erstellt die Zuordnungsdatei, in der jeweils der Name und die Größe der Ordner sowie die Größe der gelöschten Elemente aufgeführt sind. Dieses Skript wird auf dem Exchange 2013-Server ausgeführt.

  - `Export-ModernPublicFolderStatistics.strings.psd1`: Diese Unterstützungsdatei wird vom Skript „Export-ModernPublicFolderStatistics.ps1\&quot; verwendet und sollte an denselben Speicherort heruntergeladen werden.

  - `ModernPublicFolderToMailboxMapGenerator.ps1`: Dieses Skript erstellt die Zuordnungsdatei, in der aufgeführt ist, welchem Postfach die öffentlichen Ordner zugewiesen sind. Es wird auf einem Exchange 2013-Server ausgeführt und verwendet die Ausgabe des Skripts „ModernPublicFolderStatistics.ps1\&quot; als Basis.

  - `ModernPublicFolderToMailboxMapGenerator.strings.psd1`: Diese Unterstützungsdatei wird vom Skript „ModernPublicFolderToMailboxMapGenerator.ps1\&quot; verwendet und sollte an denselben Speicherort heruntergeladen werden.

  - `SetMailPublicFolderExternalAddress.ps1`: Dieses Skript aktualisiert den Parameter `ExternalEmailAddress` der E-Mail-aktivierten öffentlichen Ordner in Ihrer lokalen Umgebung auf die Adresse ihrer jeweiligen Gegenstücke in Exchange Online. Dadurch wird sichergestellt, dass E-Mails an E-Mail-aktivierte öffentliche Ordner nach der Migration ordnungsgemäß an Exchange Online weitergeleitet werden. Dieses Skript muss auf einem Exchange 2013-Server ausgeführt werden.

  - `SetMailPublicFolderExternalAddress.strings.psd1`: Diese Unterstützungsdatei wird vom Skript „SetMailPublicFolderExternalAddress.ps1\&quot; verwendet und sollte an denselben Speicherort heruntergeladen werden.

## Schritt 2: Vorbereiten der Migration

Führen Sie alle erforderlichen Schritte durch, die in den folgenden Abschnitten beschrieben sind, bevor Sie mit der Migration Ihrer öffentlichen Ordner beginnen.

**Allgemeine erforderliche Schritte**

Damit Ihre Migration gelingt, sollten Sie Folgendes tun:

  - Stellen Sie sicher, dass in Active Directory keine verwaisten E-Mail-Objekte aus öffentlichen Ordnern vorhanden sind (d. h. Objekte in Active Directory, die kein Exchange-Objekt als Gegenstück haben).

  - Vergewissern Sie sich, dass die für die öffentlichen Ordner in Active Directory konfigurierten SMTP-E-Mail-Adressen mit den SMTP-E-Mail-Adressen der Exchange-Objekte übereinstimmen.

  - Stellen Sie sicher, dass keine doppelten Objekte des Typs „Öffentlicher Ordner\&quot; in Active Directory vorhanden sind. Das ist nötig, damit nicht zwei oder mehr Active Directory-Objekte auf denselben E-Mail-aktivierten öffentlichen Ordner verweisen.

**Erforderliche Schritte in der lokalen Exchange 2013-Serverumgebung**

Führen Sie die folgenden Schritte in der (lokalen) Exchange-Verwaltungsshell durch:

1.  Nach Abschluss der Migration dauert es einige Zeit, bis die DNS-Caches im Internet Nachrichten an Ihre E-Mail-aktivierten öffentlichen Ordner am neuen Speicherort in Exchange Online weiterleiten. Um sicherzustellen, dass die gerade migrierten E-Mail-aktivierten öffentlichen Ordner während dieser DNS-Umstellung Nachrichten empfangen, können Sie eine akzeptierte Domäne mit einem bekannten Namen erstellen. Führen Sie dazu den unten dargestellten Befehl in Ihrer lokalen Exchange-Umgebung aus. In diesem Beispiel ist `target domain` Ihre Office 365- oder Exchange Online-Domäne, für die bereits ein Sendeconnector im Hybrid Configuration Wizard konfiguriert wurde.
    
        New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName <target domain> -DomainType InternalRelay
    
    **Beispiel**:
    
        New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName "contoso.mail.onmicrosoft.com" -DomainType InternalRelay
    
    Falls diese akzeptierte Domäne bereits in Ihrer lokalen Umgebung existiert, benennen Sie sie um in `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99`. Lassen Sie dabei die anderen Attribute unverändert.
    
    Mit diesem Befehl können Sie prüfen, ob die akzeptierte Domäne bereits in Ihrer lokalen Umgebung existiert:
    
        Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" }
    
    Führen Sie den folgenden Befehl aus, um die akzeptierte Domäne in `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99` umzubenennen:
    
        Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" } | Set-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99
    

    > [!NOTE]
    > Sollen Ihre E-Mail-aktivierten öffentlichen Ordner in Exchange&nbsp;Online externe E-Mails aus dem Internet empfangen können, müssen Sie die verzeichnisbasierte Edge-Blockierung (DBEB, Directory Based Edge Blocking) in Exchange&nbsp;Online und Exchange&nbsp;Online&nbsp;Protection (EOP) deaktivieren. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/dn600322(v=exchg.150)">Verwenden von verzeichnisbasierter Edge-Blockierung zum Ablehnen von Nachrichten, die an ungültige Empfänger gesendet wurden</A>.



2.  Falls der Name eines öffentlichen Ordners einen umgekehrten Schrägstrich (**\\**) oder einen Schrägstrich (**/**) enthält, wird dieser öffentliche Ordner während des Migrationsprozesses möglicherweise nicht zu dem vorgesehenen Postfach migriert. Entfernen Sie diese Zeichen vor der Migration aus den Namen der betreffenden Ordner:
    
    1.  Führen Sie den folgenden Befehl aus, um öffentliche Ordner zu suchen, deren Name einen umgekehrten Schrägstrich enthält:
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Where {$_.Name -like "*\*" -or $_.Name -like "*/*"} | Format-List Name, Identity, EntryId
    
    2.  Wenn Öffentliche Ordner zurückgegeben werden, können Sie sie durch Ausführung des folgenden Befehls umbenennen:
        
            Set-PublicFolder -Identity "<public folder EntryId>" -Name "<new public folder name>"

3.  Gehen Sie wie unten beschrieben vor, um sich zu vergewissern, dass kein Datensatz einer vorherigen erfolgreichen Migration in Ihrer Organisation vorhanden ist. Falls ein solcher Datensatz vorhanden ist, müssen Sie den betreffenden Wert auf `$false` setzen.
    
    Vergewissern Sie sich vor einer Änderung der Werte, dass der vorherige Migrationsversuch verworfen werden kann, damit Sie nicht versehentlich eine zweite Migration durchführen.
    
    1.  Führen Sie den folgenden Befehl aus, um frühere Migrationen zu finden und den Status dieser Migrationen abzurufen:
        
            Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete, PublicFolderMailboxesLockedForNewConnections, PublicFolderMailboxesMigrationComplete
        

        > [!NOTE]
        > Falls der Parameter <CODE>PublicFoldersLockedforMigration</CODE> oder der Parameter <CODE>PublicFolderMigrationComplete</CODE> auf <CODE>$true</CODE> gesetzt ist, haben Sie in der Vergangenheit schon einmal öffentliche Ordner eines Legacy-Typs migriert. Stellen Sie sicher, dass alle möglicherweise vorhandenen Legacy-Datenbanken für öffentliche Ordner außer Betrieb gesetzt sind, bevor Sie mit Schritt&nbsp;3b fortfahren.

    
    2.  Falls einer der oben genannten Parameter mit dem Wert `$true` zurückgegeben wird, setzen Sie den Wert mithilfe des folgenden Befehls auf `$false`:
        
            Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false -PublicFolderMailboxesLockedForNewConnections:$false -PublicFolderMailboxesMigrationComplete:$false

4.  Wir empfehlen Ihnen, die nachfolgend aufgeführten Befehle auf allen betreffenden Exchange 2013-Servern auszuführen, damit Sie nach Abschluss der Migration den Migrationserfolg überprüfen können. Die Befehle erstellen Momentaufnahmen Ihrer aktuell bereitgestellten öffentlichen Ordner, die Sie später mit den migrierten öffentlichen Ordnern vergleichen können.
    

    > [!NOTE]
    > Abhängig von der Größe Ihrer Exchange-Organisation kann die Ausführung dieser Befehle einige Zeit dauern.

    
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der ursprünglichen Quellordnerstruktur zu erstellen.
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML OnPrem_PFStructure.xml
    
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Statistikdaten von Öffentlichen Ordnern (wie Anzahl von Elementen, Größe und Besitzer) zu erstellen.
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML OnPrem_PFStatistics.xml
    
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen der öffentlichen Ordner zu erstellen:
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML OnPrem_PFPerms.xml
    
      - Führen Sie den folgenden Befehl aus, um eine Momentaufnahme Ihrer E-Mail-aktivierten öffentlichen Ordner zu erstellen:
        
            Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML OnPrem_MEPF.xml
    
      - Speichern Sie die von den oben beschriebenen Befehlen generierten Dateien an einem sicheren Ort, um sie nach der Migration für einen Vergleich heranziehen zu können.

5.  Verwenden Sie Microsoft Azure Active Directory verbinden (Azure AD Connect) die lokalen Verzeichnisse mit Azure Active Directory zu synchronisieren, müssen Sie die folgenden Aktionen (Wenn Sie Azure AD Connect nicht verwenden, können Sie diesen Schritt überspringen):
    
    1.  Öffnen Sie auf einem lokalen Computer Microsoft Azure Active Directory Connect, und wählen Sie dann **Konfigurieren** aus.
    
    2.  Wählen Sie auf dem Bildschirm **Weitere Aufgaben** die Option **Synchronisierungsoptionen prüfen oder anpassen** aus, und klicken Sie dann auf **Weiter**.
    
    3.  Geben Sie auf dem Bildschirm **Mit Azure AD verbinden** die entsprechenden Anmeldeinformationen ein, und klicken Sie dann auf **Next**. Nachdem eine Verbindung hergestellt wurde, klicken Sie weiter auf **Weiter**, bis Sie sich auf dem Bildschirm **Optionale Features** befinden.
    
    4.  Vergewissern Sie sich, dass **Öffentliche Exchange-E-Mail-Ordner** nicht aktiviert ist. Wenn die Option nicht aktiviert ist, können Sie mit dem nächsten Abschnitt, *Erforderliche Schritte in Exchange Online*, fortfahren. Wenn die Option aktiviert ist, deaktivieren Sie das Kontrollkästchen, und klicken Sie dann auf **Weiter**.
        

        > [!NOTE]
        > Wenn Sie <STRONG>Öffentliche Exchange-E-Mail-Ordner</STRONG> nicht als Option auf dem Bildschirm <STRONG>Optionale Features</STRONG> sehen, können Sie Microsoft Azure Active Directory Connect beenden und mit dem nächsten Abschnitt, <EM>Erforderliche Schritte in Exchange Online</EM>, fortfahren.

    
    5.  Nachdem Sie die Option **Öffentliche Exchange-E-Mail-Ordner** deaktiviert haben, klicken Sie weiter auf **Weiter**, bis Sie sich auf dem Bildschirm **Bereit zur Konfiguration** befinden, und klicken Sie dann auf **Konfigurieren**.

**Erforderliche Schritte in Exchange Online**

Führen Sie die folgenden Schritte in Exchange Online PowerShell durch:

1.  Stellen Sie sicher, dass aktuell keine Migrationsanforderungen für öffentliche Ordner vorhanden sind. Falls welche vorhanden sind, müssen Sie sie löschen; andernfalls wird Ihre eigene Migrationsanforderung fehlschlagen. Dieser Schritt ist nur erforderlich, wenn Sie glauben, dass in der Pipeline möglicherweise bereits eine Migrationsanforderung vorhanden ist (eine Anforderung, die fehlgeschlagen ist oder die Sie abbrechen möchten).
    
    Eine bereits vorhandene Migrationsanforderung kann eine Anforderung für einen von zwei Migrationstypen sein: eine Batchmigration oder eine serielle Migration. Unten sehen Sie die Befehle, mit denen Sie die verschiedenen Anforderungstypen erkennen und entfernen können.
    
    Mit diesem Beispielbefehl können Sie alle vorhandenen Anforderungen für eine serielle Migration ermitteln:
    
        Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics 
    
    Mit diesem Beispielbefehl entfernen Sie alle vorhandenen Anforderungen für eine serielle Migration öffentlicher Ordner:
    
        Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
    
    Mit diesem Beispielbefehl können Sie alle vorhandenen Anforderungen für eine Batchmigration ermitteln:
    
        Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
    
    Mit diesem Beispielbefehl entfernen Sie alle vorhandenen Anforderungen für eine Batchmigration öffentlicher Ordner:
    
        Remove-MigrationBatch <name of migration batch> -Confirm:$false

2.  Die Migrationsfunktion **PAW** muss für Ihren Office 365-Mandanten aktiviert sein. Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um dies zu überprüfen:
    
        Get-MigrationConfig
    
    Wenn in der Ausgabe unter **Features** der Eintrag **PAW** aufgeführt ist, ist die Funktion aktiviert, und Sie können mit dem nächsten Schritt fortfahren.
    
    Falls PAW für Ihren Mandanten noch nicht aktiviert ist, sind möglicherweise bereits Migrationsbatches vorhanden (entweder Batches mit öffentlichen Ordnern oder Benutzerbatches). Diese Batches könnten jeden Status haben, auch den Status „Abgeschlossen\&quot;. Sie müssen alle möglicherweise vorhandenen Migrationsbatches abschließen und entfernen, bis `Get-MigrationBatch` keine Datensätze mehr zurückgibt. Sobald Sie alle vorhandenen Batches entfernt haben, sollte PAW automatisch aktiviert werden. Es kann sein, dass die Änderung nicht sofort in der Ausgabe von `Get-MigrationConfig` sichtbar ist; das ist jedoch kein Problem. Bei Benutzermigrationen können Sie nach diesem Schritt mit der Erstellung neuer Batches fortfahren.

3.  Stellen Sie sicher, dass in Exchange Online weder öffentliche Ordner noch Postfächer für öffentliche Ordner vorhanden sind. Sollten in Exchange Online nach Durchführung der unten beschriebenen Schritte noch öffentliche Ordner existieren, müssen Sie auf jeden Fall herausfinden, warum sie vorhanden sind und wer in Ihrer Organisation eine Hierarchie für öffentliche Ordner angelegt hat, bevor Sie irgendwelche öffentlichen Ordner oder Postfächer für öffentliche Ordner entfernen.
    
    1.  Führen Sie in Office 365 oder Exchange Online PowerShell den folgenden Befehl aus, um zu sehen, ob öffentliche Ordner-Postfächer vorhanden sind.
        
            Get-Mailbox -PublicFolder
    
    2.  Falls der Befehl keine Postfächer für öffentliche Ordner zurückgibt, fahren Sie fort mit Schritt 3: Generieren der CSV-Dateien. Gibt der Befehl Postfächer für öffentliche Ordner zurück, müssen Sie den folgenden Befehl ausführen, um nach öffentlichen Ordnern zu suchen:
        
            Get-PublicFolder -Recurse
    
    3.  Falls öffentliche Ordner in Office 365 oder Exchange Online vorhanden sind, müssen Sie sie mit dem PowerShell-Befehl unten entfernen (sofern sie nicht benötigt werden). Speichern Sie vor dem Löschen auf jeden Fall alle Informationen, die in diesen öffentlichen Ordnern vorhanden sind. Wenn Sie die öffentlichen Ordner entfernen, werden alle Informationen in ihnen endgültig gelöscht.
        
            Get-MailPublicFolder -ResultSize Unlimited | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
            Get-PublicFolder -GetChildren \ -ResultSize Unlimited | Remove-PublicFolder -Recurse -Confirm:$false
    
    4.  Sobald Sie die öffentlichen Ordner entfernt haben, können Sie mithilfe der folgenden Befehle alle Postfächer für öffentliche Ordner entfernen:
        
            $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
            Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
            Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
            Get-Mailbox -PublicFolder -SoftDeletedMailbox | Remove-Mailbox -PublicFolder -PermanentlyDelete:$true 

## Schritt 3: Generieren der CSV-Dateien

Verwenden Sie die zuvor heruntergeladenen Skripts, um die während der Migration zu verwendenden CSV-Dateien zu generieren.

1.  Führen Sie über die (lokale) Exchange-Verwaltungsshell das Skript `Export-ModernPublicFolderStatistics.ps1` aus, um die Zuordnungsdatei mit den Ordnernamen und Ordnergrößen zu erstellen. Sie müssen lokale Administratorberechtigungen besitzen, um dieses Skript ausführen zu können. Die ausgegebene Datei enthält drei Spalten: **FolderName**, **FolderSize** und **DeletedItemSize**. Die Werte in den Spalten **FolderSize** und **DeletedItemSize** werden in Byte angezeigt. Beispiel: **\\PublicFolder01,10240, 100** bedeutet, dass der öffentliche Ordner „PublicFolder01\&quot;, der als Stamm Ihrer Hierarchie fungiert, 10.240 Byte (10,240 MB) groß ist und wiederherstellbare Elemente im Umfang von 100 Byte enthält.
    
        .\Export-ModernPublicFolderStatistics.ps1 <Folder-to-size map path>
    
    **Beispiel**:
    
        .\Export-ModernPublicFolderStatistics.ps1 stats.csv

2.  Führen Sie das Skript `ModernPublicFolderToMailboxMapGenerator.ps1` aus, um eine CSV-Datei zu erstellen, die die als Quelle dienenden öffentlichen Ordner den entsprechenden Postfächern für öffentliche Ordner in Ihrem Exchange Online-Ziel zuordnet. Diese Datei wird verwendet, um die richtige Anzahl von Postfächern für öffentliche Ordner in Exchange Online zu berechnen.
    

    > [!NOTE]
    > Von <CODE>ModernPublicFolderToMailboxMapGenerator.ps1</CODE> generierte Datei enthält nicht den Namen eines jeden öffentlichen Ordner in der Organisation. Enthält Verweise auf die übergeordneten Ordner der größeren Ordnerstrukturen oder die Namen der Ordner sind die sehr großen. Sie können diese Datei vorstellen eine "Ausnahme" Datei verwendet, um sicherzustellen, dass bestimmte Ordnerstrukturen und größere Ordner in bestimmten öffentlichen Ordner e-Mail-Nachrichten abrufenFelder. Es ist normal, nicht jeden öffentlichen Ordner in dieser Datei sehen. Untergeordnete Ordner alle Ordner in diesem Zuordnungsdatei werden auch dasselbe Postfach für Öffentliche Ordner als den übergeordneten Ordner (außer einer anderen Position in der Zuordnungsdatei, die sie in eine andere Öffentliche Ordner Postfach verweist ausdrücklich) migriert.

    
        .\ModernPublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes><Maximum mailbox recoverable item size in bytes><Folder-to-size map path><Folder-to-mailbox map path>
    
      - `Maximum mailbox size in bytes` ist die Datenmenge, die Sie maximal zu einem einzelnen Postfach für öffentliche Ordner in Exchange Online migrieren möchten. Die Maximalgröße für dieses Feld liegt derzeit bei 50 GB. Wir empfehlen Ihnen jedoch, einen kleineren Wert zu verwenden (z. B. 50 % der Maximalgröße), um zukünftigem Wachstum Rechnung zu tragen.
    
      - `Maximum mailbox recoverable items size in bytes` ist das Kontingent von wiederherstellbaren Elementen in Ihren Exchange Online-Postfächern. Die Maximalgröße für Postfächer für öffentliche Ordner in Exchange Online liegt derzeit bei 50 GB. Wir empfehlen, den Parameter ` RecoverableItemsQuota` auf 15 GB oder weniger zu setzen.
    
      - `Folder-to-size map path` ist der Dateipfad der CSV-Datei, die Sie durch die Ausführung des Skripts `Export-ModernPublicFolderStatistics.ps1` erstellt haben.
    
      - `Folder-to-mailbox map path` ist der Dateipfad der Datei mit den Ordner-Postfach-Zuordnungen, die Sie in diesem Schritt erstellen. Wenn Sie nur einen Dateinamen angeben, wird die Datei im aktuellen PowerShell-Verzeichnis auf dem lokalen Computer generiert.

**Beispiel**:

    .\ModernPublicFolderToMailboxMapGenerator.ps1 -MailboxSize 25GB -MailboxRecoverableItemSize 1GB -ImportFile .\stats.csv -ExportFile map.csv


> [!NOTE]
> Ist die Anzahl der eindeutigen Ordner Postfächer in Exchange Online 100 unterstützt nicht migrieren von öffentliche Ordnern zu Exchange Online.



## Schritt 4: Erstellen der Postfächer für öffentliche Ordner in Exchange Online

Im nächsten Schritt erstellen Sie in Exchange Online PowerShell die Zielpostfächer für öffentliche Ordner, die Ihre migrierten öffentlichen Ordner enthalten sollen.

1.  Führen Sie das folgende Skript aus, um die Zielpostfächer für öffentliche Ordner zu erstellen. Das Skript erstellt ein Zielpostfach für jedes Postfach, das in der CSV-Datei aufgeführt ist, die Sie zuvor in *Schritt 3: Generieren der CSV-Dateien* durch Ausführung des Skripts `ModernPublicFoldertoMailboxMapGenerator.ps1` erstellt haben.
    
        $mappings = Import-Csv <Folder-to-mailbox map path>
        $primaryMailboxName = ($mappings | Where-Object FolderPath -eq "\" ).TargetMailbox
        New-Mailbox -HoldForMigration:$true -PublicFolder -IsExcludedFromServingHierarchy:$false $primaryMailboxName 
        ($mappings | Where-Object TargetMailbox -ne $primaryMailboxName).TargetMailbox | Sort-Object -unique | ForEach-Object { New-Mailbox -PublicFolder -IsExcludedFromServingHierarchy:$false $_ }
    
      - `Folder-to-mailbox map path` ist der Dateipfad der CSV-Datei mit den Ordner-Postfach-Zuordnungen, die das Skript `ModernPublicFoldertoMailboxMapGenerator.ps1` in *Schritt 3: Generieren der CSV-Dateien* generiert hat.

## Schritt 5: Starten der Migrationsanforderung

Nun müssen Sie einige Befehle in Ihrer lokalen Exchange 2013-Umgebung und in Exchange Online ausführen.

1.  Führen Sie das Skript unten auf einem Exchange 2013-Server aus, der Postfächer für öffentliche Ordner hostet. Dieses Skript synchronisiert die E-Mail-aktivierten öffentlichen Ordner in Ihrem lokalen Active Directory mit Exchange Online. Vergewissern Sie sich, dass Sie die aktuelle Version dieses Skripts heruntergeladen haben und dass Sie es über die Exchange-Verwaltungsshell ausführen.
    
        .\Sync-ModernMailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
      - `Credential` steht für den Benutzernamen und das Kennwort Ihres Exchange Online-Administratorkontos.
    
      - `CsvSummaryFile` ist der Dateipfad, unter dem die Protokolldatei mit den Synchronisierungsvorgängen und Synchronisierungsfehlern gespeichert werden soll. Das Protokoll wird im CSV-Format gespeichert.

2.  Suchen Sie auf dem Exchange 2013-Server den MRS-Proxyendpunktserver, und notieren Sie sich seinen Namen. Sie benötigen diese Information, um die Migrationsanforderung ausführen zu können. Speichern Sie die Information für Schritt 3b unten.

3.  Führen Sie in Exchange Online PowerShell die folgenden Befehle aus, um die Anmeldeinformationen und die MRS-Informationen aus dem vorherigen Schritt an die Cmdlet-Variablen zu übergeben, die in der Migrationsanforderung verwendet werden:
    
    1.  Übergeben Sie die Anmeldeinformationen eines Benutzers, der über Administratorberechtigungen in der lokalen Exchange 2013-Umgebung verfügt, an die Variable `$Source_Credential`. Die Migrationsanforderung, die Sie in Exchange Online ausführen, verwendet diese Anmeldeinformationen, um auf Ihre lokalen Exchange 2013-Server zuzugreifen und die Inhalte der öffentlichen Ordner nach Exchange Online zu kopieren.
        
            $Source_Credential = Get-Credential <source_domain>\<PublicFolder_Administrator_Account>
    
    2.  Übergeben Sie die Informationen zum MRS-Proxyserver in der Exchange 2013-Umgebung, die Sie in Schritt 2 oben ermittelt haben, an die Variable:
        
            $Source_RemoteServer = "<paste the value here>"

4.  Führen Sie die folgenden Befehle in Exchange Online PowerShell aus, um den Endpunkt für die Migration der öffentlichen Ordner und die Migrationsanforderung für die öffentlichen Ordner zu erstellen:
    
        $PfEndpoint = New-MigrationEndpoint -PublicFolder -Name PublicFolderEndpoint -RemoteServer $Source_RemoteServer -Credentials $Source_Credential
         
        [byte[]]$bytes = Get-Content -Encoding Byte <folder_mapping.csv>
        
        New-MigrationBatch -Name PublicFolderMigration -CSVData $bytes -SourceEndpoint $PfEndpoint.Identity -NotificationEmails <email addresses for migration notifications>
    

    > [!NOTE]
    > Trennen Sie mehrere E-Mail-Adressen durch Kommata.

    
    Dabei ist `folder_mapping.csv` die Zuordnungsdatei, die Sie unter *Schritt 3: Generieren der CSV-Dateien* generiert haben. Achten Sie darauf, den vollständigen Dateipfad anzugeben. Falls die Zuordnungsdatei aus irgendeinem Grund verschoben wurde, müssen Sie unbedingt den neuen Speicherort angeben.

5.  Führen Sie nun den folgenden Befehl in Exchange Online PowerShell aus, um die Migration zu starten:
    
        Start-MigrationBatch PublicFolderMigration

Zwar müssen Batchmigrationen mithilfe des Cmdlets „New-MigrationBatch\&quot; in Exchange Online PowerShell erstellt werden; Sie können den Fortschritt und den Abschluss der Migration jedoch im EAC oder mithilfe des Cmdlets „Get-MigrationBatch\&quot; nachverfolgen und verwalten. Das Cmdlet „New-MigrationBatch\&quot; initiiert eine Migrationsanforderung für Postfächer für jedes Postfach für öffentliche Ordner. Den Status dieser Anforderungen können Sie auf der Seite der Postfachmigration sehen.

So rufen Sie die Seite der Postfachmigration auf:

1.  Melden Sie sich bei Exchange Online an, und öffnen Sie das EAC.

2.  Navigieren Sie zu **Empfänger**, und wählen Sie **Migration** aus.

3.  Wählen Sie die soeben erstellte Migrationsanforderung aus, und klicken Sie im Bereich **Details** auf **Details anzeigen**.

Bevor Sie fortfahren mit *Schritt 6: Sperren der öffentlichen Ordner in der Exchange 2013-Umgebung*, müssen Sie sicherstellen, dass alle Daten kopiert worden sind und keine Fehler bei der Migration aufgetreten sind. Sobald Sie sich vergewissert haben, dass der Batch den Status **Synchronisiert** hat, erstellen Sie mithilfe der Befehle aus *Schritt 2: Vorbereiten der Migration* (letzter Schritt unter **Erforderliche Schritte in der lokalen Exchange 2013-Serverumgebung**) eine Momentaufnahme der lokalen öffentlichen Ordner. Nachdem Sie diese Befehle ausgeführt haben, können Sie mit dem nächsten Schritt fortfahren. Beachten Sie, dass es je nach Anzahl der Ordner eine Weile dauern kann, bis die Befehle abgeschlossen werden.

## Schritt 6: Sperren der öffentlichen Ordner in der Exchange 2013-Umgebung während der endgültigen Migration (Downtime der öffentlichen Ordner erforderlich)

Bis zu diesem Punkt im Migrationsprozess konnten die Benutzer auf Ihre lokalen öffentlichen Ordner zugreifen. In den folgenden Schritten werden die Benutzer von den öffentlichen Ordnern in Exchange 2013 abgemeldet, und die Ordner werden gesperrt, bis die abschließende Synchronisierung im Rahmen des Migrationsprozesses beendet ist. Während dieser Zeit können die Benutzer nicht auf die öffentlichen Ordner zugreifen. Außerdem werden alle Nachrichten, die an diese E-Mail-aktivierten öffentlichen Ordner gesendet werden, in die Warteschlange verschoben und erst zugestellt, wenn die Migration der öffentlichen Ordner abgeschlossen ist.

Bevor Sie den Befehl `PublicFolderMailboxesLockedForNewConnections` wie unten beschrieben ausführen, vergewissern Sie sich, dass alle Aufträge den Status **Synchronisiert** aufweisen. Führen Sie hierzu den Befehl `Get-PublicFolderMailboxMigrationRequest` aus. Fahren Sie mit diesem Schritt erst dann fort, nachdem Sie überprüft haben, ob alle Aufträge den Status **Synchronisiert** aufweisen.

Führen Sie den folgenden Befehl in Ihrer lokalen Umgebung aus, um die öffentlichen Ordner in Exchange 2013 während des Abschlusses der Migration zu sperren:

    Set-OrganizationConfig -PublicFolderMailboxesLockedForNewConnections $true


> [!NOTE]
> Falls Sie nicht auf den Parameter <CODE>-PublicFolderMailboxesLockedForNewConnections</CODE> zugreifen können, haben Sie Ihr Active&nbsp;Directory während des CU-Upgrades möglicherweise nicht vorbereitet, wie wir es oben im Abschnitt <EM>Was sollten Sie wissen, bevor Sie beginnen?</EM> empfohlen haben. Weitere Informationen finden Sie unter <A href="prepare-active-directory-and-domains-exchange-2013-help.md">Vorbereitung von Active Directory und Domänen</A>.<BR>Beachten Sie auch: Alle Benutzer, die Zugriff auf die öffentlichen Ordner benötigen, sollten zuerst migriert werden, d.&nbsp;h. <STRONG>bevor</STRONG> Sie die öffentlichen Ordner selbst migrieren.



Falls Ihre Organisation auf mehreren Exchange 2013-Servern Postfächer für öffentliche Ordner hat, müssen Sie warten, bis die AD-Replikation abgeschlossen ist. Sobald das geschehen ist, können Sie überprüfen, ob alle Postfächer für öffentliche Ordner das Flag `PublicFolderMailboxesLockedForNewConnections` übernommen haben und alle ausstehenden Änderungen, die Benutzer kürzlich an ihren öffentlichen Ordnern vorgenommen haben, organisationsweit angeglichen wurden. Dies alles kann mehrere Stunde dauern.

## Schritt 7: Abschließen der Migration der öffentlichen Ordner (Downtime der öffentlichen Ordner erforderlich)

Bevor Sie die Migration der öffentlichen Ordner abschließen können, müssen Sie bestätigen, dass es keine anderen Postfächer von öffentlichen Ordnern verschoben werden bzw. keine Verschiebungen öffentlicher Ordner in Ihre lokale Exchange-Umgebung stattfinden. Verwenden Sie hierzu die Cmdlets `Get-MoveRequest` und `Get-PublicFolderMoveRequest`, um alle vorhandenen Verschiebungen öffentlicher Ordner aufzulisten. Falls aktuell Verschiebungen stattfinden oder den Status **Abgeschlossen** aufweisen, entfernen Sie diese.

Führen Sie als Nächstes zum Abschließen der Migration der öffentlichen Ordner den folgenden Befehl in Exchange Online PowerShell aus:

    Complete-MigrationBatch PublicFolderMigration

Wenn Sie diesen Befehl ausführen, wird Exchange eine letzte Synchronisierung zwischen der lokalen Organisation und Exchange Online tun. Während dieses Zeitraums der Status des Stapels Migration zum **abschließen** von **synchronisiert** geändert und schließlich **beendet**. Wenn die letzte Synchronisierung erfolgreich ist, werden die öffentlichen Ordner in Exchange Online freigeschaltet.

In der Regel dauert es einige Stunden, bis der Status des Migrationsbatches von **Synchronisiert** in **Wird abgeschlossen** geändert wird. Erst dann beginnt die abschließende Synchronisierung.

## Schritt 8: Testen und Entsperren der öffentlichen Ordner in Exchange Online

Führen Sie nach Abschluss der Migration der öffentlichen Ordner die folgenden Schritte durch, um den Erfolg der Migration zu testen und den Abschluss offiziell zu bestätigen. Im Rahmen dieser abschließenden Aufgaben testen Sie die migrierte Hierarchie der öffentlichen Ordner, bevor Sie Ihre Organisation endgültig auf öffentliche Ordner in Exchange Online umstellen.

1.  Weisen Sie in Exchange Online PowerShell einigen Testbenutzerpostfächern eines Ihrer gerade migrierten Postfächer für öffentliche Ordner als Standardpostfach für öffentliche Ordner zu:
    
        Set-Mailbox -Identity <test user> -DefaultPublicFolderMailbox <public folder mailbox identity>
    
    Stellen Sie sicher, dass Ihre Testbenutzer die erforderlichen Berechtigungen zum Erstellen von öffentlichen Ordnern haben.

2.  Melden Sie sich bei Outlook mit Testbenutzer, den Sie im vorherigen Schritt festgelegt und dann im folgenden Ordner überprüft. Beachten Sie, dass es 15 bis 30 Minuten ändern zu kann. Sobald Outlook Änderungen ist, dass es mehrmals neu starten aufgefordert.
    
    1.  Zeigen Sie die Hierarchie an.
    
    2.  Prüfen Sie die Berechtigungen.
    
    3.  Erstellen Sie einige öffentliche Ordner, und löschen Sie sie anschließend wieder.
    
    4.  Veröffentlichen Sie Inhalte in einem öffentlichen Ordner, und löschen Sie Inhalte aus einem öffentlichen Ordner.
    
    Wenn Sie alle Probleme und feststellen, dass Sie keine öffentlichen Ordner Ihrer Organisation ausschließlich Exchange Online wechseln möchten, finden Sie unter [Ausführen eines Rollbacks einer Migration öffentlicher Ordner von Exchange 2013 zu Exchange Online](roll-back-a-public-folder-migration-from-exchange-2013-to-exchange-online-exchange-2013-help.md).

3.  Führen Sie folgenden Befehl im Exchange Online PowerShell entsperren Sie Öffentliche Ordner in Exchange Online. Nach dem Ausführen des Befehls dauert es etwa 15 bis 30 Minuten wirksam wird. Nach Outlook Änderungen wird, kann der Benutzer das Programm mehrmals neu aufgefordert werden.
    
        Set-OrganizationConfig -RemotePublicFolderMailboxes $Null -PublicFoldersEnabled Local

## Schritt 9: Lokales Abschließen der Migration

Um e-Mails an e-Mail-aktivierte Öffentliche Ordner lokal zu aktivieren, gehen Sie folgendermaßen vor:

1.  Führen Sie das folgende Skript in Ihrer lokalen Umgebung aus, um sicherzustellen, dass alle E-Mails an E-Mail-aktivierte öffentliche Ordner ordnungsgemäß an Exchange Online weitergeleitet werden. Das Skript weist E-Mail-aktivierten öffentlichen Ordnern einen Wert `ExternalEmailAddress` zu, der sie an ihre Gegenstücke in Exchange Online verweist:
    
        .\SetMailPublicFolderExternalAddress.ps1 -ExecutionSummaryFile:mepf_summary.csv

2.  Wenn der Test erfolgreich war, führen Sie nun in Ihrer lokalen Umgebung den folgenden Befehl aus, um zu bestätigen, dass die Migration der öffentlichen Ordner abgeschlossen ist:
    
        Set-OrganizationConfig -PublicFolderMailboxesMigrationComplete:$true -PublicFoldersEnabled Remote

## Woher weiß ich, dass der Vorgang erfolgreich war?

In Schritt 2: Vorbereiten der Migration haben Sie Momentaufnahmen der Struktur Ihrer lokalen öffentlichen Ordner sowie ihrer Kennzahlen und Berechtigungen erstellt. Mit den folgenden Schritten erstellen Sie nun nach der Migration dieselben Momentaufnahmen in Exchange Online. So können Sie überprüfen, ob die Migration Ihrer öffentlichen Ordner erfolgreich war. Vergleichen Sie einfach die Daten in den beiden Dateien.

1.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der neuen Ordnerstruktur zu erstellen:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML Cloud_PFStructure.xml

2.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der Kennzahlen der öffentlichen Ordner zu erstellen, einschließlich Elementanzahl, Größe und Besitzer:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderStatistics | Export-CliXML Cloud_PFStatistics.xml

3.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der Berechtigungen zu erstellen:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User, AccessRights | Export-CliXML Cloud_PFPerms.xml

4.  Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um eine Momentaufnahme der E-Mail-aktivierten öffentlichen Ordner zu erstellen:
    
        Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML Cloud_MEPF.xml

## Bekannte Probleme

Im folgenden werden häufige Migrationsprobleme für Öffentliche Ordner, die in Ihrer Organisation auftreten können.

  - Ist die Anzahl der eindeutigen Ordner Postfächer in Exchange Online 100 unterstützt nicht migrieren von öffentliche Ordnern zu Exchange Online.

  - Die Berechtigungen für den als Stammordner fungierenden öffentlichen Ordner und den Ordner EFORMS REGISTRY werden nicht zu Exchange Online migriert. Sie müssen sie manuell in Exchange Online anwenden. Führen Sie dazu den Befehl unten in Exchange Online PowerShell aus. Führen Sie den Befehl jeweils einmal für jeden Berechtigungseintrag aus, der lokal vorhanden ist, in Exchange Online aber fehlt:
    
        Add-PublicFolderClientPermission "\" -User <user> -AccessRights <access rights>
        Add-PublicFolderClientPermission "\NON_IPM_SUBTREE\EFORMS REGISTRY" -User <user> -AccessRights <access rights>

  - Einige Öffentliche Ordner Migrationen schlägt fehl, wenn Postfächer für Öffentliche Ordner keine Hierarchie der öffentlichen Ordner dienen. Dies bedeutet, dass der Parameter `IsExcludedFromServingHierarchy` auf ein oder mehrere Postfächer auf `$true`festgelegt ist. Um dies zu vermeiden, legen Sie alle Postfächer in Exchange Online zu der Hierarchie.

  - Die Berechtigungen **Send As** und **Senden im Auftrag von** werden nicht zu Exchange Online migriert. Falls dies bei Ihrer Migration der Fall ist, können Sie die Befehle unten in Ihrer lokalen Umgebung ausführen, um herauszufinden, wer diese Berechtigungen besitzt.
    
    So finden Sie heraus, welche öffentlichen Ordner lokal über Berechtigungen des Typs „Send As\&quot; verfügen:
    
        Get-MailPublicFolder | Get-ADPermission | ?{$_.ExtendedRights -like "*Send-As*"}
    
    So finden Sie heraus, welche öffentlichen Ordner lokal über Berechtigungen des Typs „Senden im Auftrag von\&quot; verfügen:
    
        Get-MailPublicFolder | ?{$_.GrantSendOnBehalfTo -ne "$null"} | ft name,GrantSendOnBehalfTo
    
    Geben Sie Folgendes in Exchange Online PowerShell ein, um einem E-Mail-aktivierten öffentlichen Ordner in Exchange Online die Berechtigung „Send As\&quot; hinzuzufügen:
    
        Add-RecipientPermission -Identity <mail-enabled public folder primary SMTP address> -Trustee <name of user to be assigned permission> -AccessRights SendAs
    
    **Beispiel**:
    
        Add-RecipientPermission -Identity send1 -Trustee Exo1 -AccessRights SendAs
    
    Geben Sie Folgendes in Exchange Online PowerShell ein, um einem E-Mail-aktivierten öffentlichen Ordner in Exchange Online die Berechtigung „Senden im Auftrag von\&quot; hinzuzufügen:
    
        Set-MailPublicFolder -Identity <name of public folder> -GrantSendOnBehalfTo <user or comma-separated list of users>
    
    **Beispiel**:
    
        Set-MailPublicFolder send2 -GrantSendOnBehalfTo exo1,exo2

  - Wenn mehr als 10.000 Ordner unter dem Ordner „\\NON\_IPM\_SUBTREE\\DUMPSTER\_ROOT\&quot; vorhanden sind, kann es zu einem Migrationsfehler kommen. Überprüfen Sie deshalb den Ordner „\\NON\_IPM\_SUBTREE\\DUMPSTER\_ROOT\&quot;, um festzustellen, ob er mehr als 10.000 direkte Unterordner (unmittelbar untergeordneten Elemente) hat. Sie können den folgenden Befehl verwenden, um die Anzahl der öffentlichen Ordner an diesem Speicherort zu ermitteln:
    
        (Get-PublicFolder -GetChildren "\NON_IPM_SUBTREE\DUMPSTER_ROOT").Count 
    
    Exchange Online unterstützt nicht mehr als 10.000 Unterordner, weshalb es bei Migrationen von mehr als 10.000 Ordnern zu einem Fehler kommt. Wir entwickeln zurzeit ein Skript, damit auch solche Konfigurationen unterstützt werden. In der Zwischenzeit wird empfohlen, mit der Migration Ihrer öffentlichen Ordner zu warten.

  - Migrationsaufträge gehen nicht voran oder werden unterbrochen. Dies kann geschehen, wenn zu viele Aufträge parallel ausgeführt werden, wodurch es zu zeitweiligen Fehlern bei den Aufträgen kommt. Sie können die Anzahl gleichzeitiger Aufträge reduzieren, indem Sie `MaxConcurrentMigrations` und `MaxConcurrentIncrementalSyncs` in eine niedrigere Zahl ändern. Verwenden Sie das folgende Beispiel, um diese Werte festzulegen:
    
        Set-MigrationEndpoint <PublicFolderEndpoint> -MaxConcurrentMigrations 30 -MaxConcurrentIncrementalSyncs 20  -SkipVerification 

  - Fehlerhafte Ausführung von Migrationsaufträgen mit Fehler „Fehler: Dumpster des Dumpster-Ordners.\&quot; Falls dieser Fehler angezeigt wird, sollte er behoben werden, wenn Sie den Batch beenden und dann erneut starten.

  - Migrationsaufgaben fehl und generieren eine "Anforderung wurde aufgrund des folgenden Fehlers isoliert: der angegebene Schlüssel war nicht im Wörterbuch vorhanden" Fehlermeldung. Dies geschieht, wenn ein beschädigtes Element in einem Ordner vorhanden ist, die Migrationsaufgaben kopieren kann. Um dieses Problem zu umgehen:
    
    1.  Beenden Sie den Migrationsbatch.
    
    2.  Identifizieren Sie den Ordner, der das fehlerhafte Element enthält. Der Migrationsbericht sollte Verweise auf den Ordner enthalten, der beim Auftreten des Fehlers kopiert wurde.
    
    3.  Verschieben Sie in Ihrer lokalen Umgebung den betroffenen Ordner in das Postfach des primären öffentlichen Ordners. Sie können das Cmdlet `New-PublicFolderMoveRequest` zum Verschieben von Ordnern verwenden.
    
    4.  Warten Sie auf das Verschieben abgeschlossen. Nach Abschluss entfernen Sie die verschiebungsanforderung. Starten Sie die migrationsbatch an.

## Entfernen von Postfächern für öffentliche Ordner aus Ihrer lokalen Exchange-Umgebung

Sobald die Migration abgeschlossen ist und Sie sichergestellt haben, dass Ihre öffentlichen Ordner in Exchange Online wie erwartet funktionieren und alle erwarteten Daten enthalten, können Sie Ihre lokalen Postfächer für öffentliche Ordner entfernen.

Beachten Sie, dass dieser Schritt nicht rückgängig gemacht werden, da gelöschte Postfächer für Öffentliche Ordner werden sie wiederhergestellt werden können. Daher wird dringend empfohlen, neben den Erfolg der Migration überprüfen Sie auch Online Exchange Öffentliche Ordner einige Wochen vor dem Entfernen der lokalen öffentlichen Ordner Postfächer überwachen.

