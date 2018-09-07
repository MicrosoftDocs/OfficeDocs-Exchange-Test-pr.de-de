---
title: 'Rollback einer Migration öffentl. Ordner von Exchange 2013 zu Exchange Online'
TOCTitle: Ausführen eines Rollbacks einer Migration öffentlicher Ordner von Exchange 2013 zu Exchange Online
ms:assetid: bcd54aa0-aa45-4c68-b504-1475842d4b96
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt798259(v=EXCHG.150)
ms:contentKeyID: 74432743
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ausführen eines Rollbacks einer Migration öffentlicher Ordner von Exchange 2013 zu Exchange Online

 

_**Letztes Änderungsdatum des Themas:** 2017-03-20_

**Zusammenfassung:**  Führen Sie die hier beschriebenen Schritte durch, um ein Rollback Ihrer Infrastruktur von öffentlichen Ordnern in Ihre lokale Exchange 2013-Organisation auszuführen, mit einer Zurücksetzung in den Zustand vor der Migration.

Befolgen Sie die Anleitung unten, wenn Sie bei der Migration Ihrer öffentlichen Ordner zu Exchange Online auf Probleme stoßen oder Ihre Exchange 2013-basierten öffentlichen Ordner aus einem anderen Grund reaktivieren müssen.

## Durchführen eines Rollbacks der Migration

Beachten Sie: Wenn Sie ein Rollback der Migration ausführen, gehen alle Inhalte verloren, die nach der Migration zu den öffentlichen Ordnern in Exchange Online hinzugefügt worden sind, ob über Clients oder per E-Mail (im Falle E-Mail-aktivierter öffentlicher Ordner). Zum Speichern dieser Inhalte können Sie die nach der Migration in den öffentlichen Ordnern abgelegten Inhalte in eine PST-Datei exportieren. Diese Datei lässt sich dann nach Abschluss des Rollbacks in die lokalen öffentlichen Ordner importieren.

1.  Führen Sie den folgenden Befehl in Ihrer lokalen Exchange-Umgebung aus, um Ihre öffentlichen Ordner in Exchange 2013 zu entsperren (die Entsperrung kann mehrere Stunden dauern):
    
        Set-OrganizationConfig -PublicFolderMailboxesLockedForNewConnections:$false -PublicFolderMailboxesMigrationComplete:$false -PublicFoldersEnabled Local 

2.  Stellen Sie in Ihrer lokalen Exchange-Umgebung den Parameter `ExternalEmailAddress` bei jedem E-Mail-aktivierten öffentlichen Ordner wieder her, der von „SetMailPublicFolderExternalAddress.ps1“ aktualisiert worden ist (dem Skript, das Sie in *Schritt 8: Testen und Entsperren der öffentlichen Ordner in Exchange Online* im Artikel [Migrieren von Exchange 2013-basierten öffentlichen Ordnern zu Exchange Online mithilfe einer Batchmigration](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/batch-migration-of-exchange-2013-public-folders) verwendet haben). Welche Ordner geändert wurden, können Sie in der Übersichtsdatei nachlesen, die das Skript erstellt hat. Alternativ finden Sie die ursprünglichen Eigenschaften aller E-Mail-aktivierten öffentlichen Ordner in der Datei „OnPrem\_MEPF.xml“, die zuvor während desselben Batchmigrationsprozesses erstellt worden ist.

3.  Führen Sie in Exchange Online PowerShell die folgenden Befehle aus, um alle öffentlichen Ordner und Postfächer aus Exchange Online zu entfernen:
    
        Get-MailPublicFolder -ResultSize Unlimited | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
        Get-PublicFolder -GetChildren \ -ResultSize Unlimited | Remove-PublicFolder -Recurse -Confirm:$false
        $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
        Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        Get-Mailbox -PublicFolder -SoftDeletedMailbox | Remove-Mailbox -PublicFolder -PermanentlyDelete:$true

4.  Führen Sie den folgenden Befehl in Ihrer Exchange Online-Umgebung aus, um den Datenverkehr an die öffentlichen Ordner wieder in die lokale Organisation (Exchange 2013) umzuleiten:
    
        Set-OrganizationConfig -PublicFoldersEnabled Remote

5.  Unter [Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/set-up-modern-hybrid-public-folders) finden Sie eine Anleitung, wie Sie den Zugriff auf Ihre lokalen öffentlichen Ordner so umkonfigurieren können, dass sie für Ihre Exchange Online-Benutzer zugänglich sind.

