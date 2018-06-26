---
title: 'Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung
ms:assetid: b828520f-022c-4fcb-ab68-e1c330e87c33
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn986544(v=EXCHG.150)
ms:contentKeyID: 65452455
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

**Zusammenfassung:** Anweisungen dazu, wie Benutzern von Exchange Online ermöglicht werden kann, auf lokale öffentliche Ordner in Ihrer Exchange 2013-Umgebung zuzugreifen.

In einer Hybridbereitstellung können Ihre Benutzer in Exchange Online und/oder lokal sein, und Ihre öffentlichen Ordner sind entweder in Exchange Online oder lokal gespeichert. Manchmal müssen Ihre Onlinebenutzer auf öffentliche Ordner in Ihrer lokalen Exchange Server 2013-Umgebung zugreifen. Ebenso müssen Exchange 2013-Benutzer möglicherweise auf öffentliche Ordner in Office 365 oder Exchange Online zugreifen.


> [!NOTE]
> Wenn Sie über öffentliche Exchange 2010- oder Exchange 2007-Ordner verfügen, finden Sie weitere Informationen unter <A href="configure-legacy-on-premises-public-folders-for-a-hybrid-deployment-exchange-2013-help.md">Konfigurieren lokaler öffentlicher Ordner aus Vorversionen für eine Hybridbereitstellung</A>.



In diesem Artikel wird beschrieben, wie Sie Ihren Benutzern von Exchange Online/Office 365 ermöglichen, auf öffentliche Ordner in Exchange 2013 zuzugreifen. Informationen dazu, wie Sie lokalen Benutzern von Exchange 2013 ermöglichen, auf Öffentliche Ordner in Exchange Online zuzugreifen, finden Sie unter [Konfigurieren öffentlicher Exchange Online-Ordner für eine Hybridbereitstellung](configure-exchange-online-public-folders-for-a-hybrid-deployment-exchange-2013-help.md).

Ein Exchange Online/Office 365-Benutzer muss in der lokalen Exchange-Umgebung durch ein MailUser-Objekt repräsentiert werden, um auf öffentliche Ordner in Exchange 2013 zugreifen zu können. Dieses MailUser-Objekt muss auch in der Zielhierarchie der öffentlichen Ordner in Exchange 2013 lokal existieren. Wenn Sie Office 365-Benutzer haben, die derzeit nicht lokal durch MailUser-Objekte repräsentiert werden, lesen Sie den Microsoft Knowledge Base-Artikel 3106618 ([Exchange Online-Benutzer können nicht auf lokale öffentliche Ordner in Legacy-Versionen zugreifen](https://go.microsoft.com/fwlink/p/?linkid=699451)), um die zugehörigen lokalen Entitäten zu erstellen.

## Was sollten Sie wissen, bevor Sie beginnen?

1.  Bei diesen Anleitungen wird davon ausgegangen, dass Sie zur Konfiguration und Synchronisierung Ihrer lokalen und Exchange Online-Umgebungen den Assistenten für die Hybridkonfiguration verwendet haben, und dass die DNS-Einträge für die AutoErmittlung bei den meisten Benutzern auf einen lokalen Endpunkt verweisen. Weitere Informationen finden Sie unter [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/de-de/library/hh529921\(v=exchg.150\)).

2.  Bei diesen Anweisungen wird vorausgesetzt, dass Outlook Anywhere aktiviert und auf den lokalen Exchange-Servern funktionsbereit ist. Weitere Informationen über das Aktivieren von Outlook Anywhere finden Sie unter [Outlook Anywhere](outlook-anywhere-exchange-2013-help.md).

3.  Bei der Implementierung der Koexistenz öffentlicher Ordner für eine Hybridbereitstellung von Exchange mit Office 365 müssen Sie während des Imports möglicherweise Konflikte beheben. Konflikte können aufgrund von E-Mail-aktivierten öffentlichen Ordnern zugewiesenen, nicht-routingfähigen E-Mail-Adressen auftreten, oder es können sich Konflikte mit anderen Benutzern und Gruppen in Office 365 oder aufgrund von anderen Attributen ergeben.

4.  Um standortübergreifend auf Öffentliche Ordner zuzugreifen, müssen Benutzer ihre Outlook-Clients auf das Outlook-Update vom November 2012 oder höher aktualisieren.
    
    1.  Unter [Update für Microsoft Outlook 2010 (KB2687623) 32-Bit-Edition](https://www.microsoft.com/de-de/download/details.aspx?id=35702) können Sie das Outlook-Update vom November 2012 für Outlook 2010 herunterladen.
    
    2.  Unter [Update für Microsoft Office Outlook 2007 (KB2687404)](https://www.microsoft.com/de-de/download/details.aspx?id=35718) können Sie das Outlook-Update vom November 2012 für Outlook 2007 herunterladen.

5.  Outlook 2011 für Mac und Outlook für Mac für Office 365 werden für standortübergreifende öffentliche Ordner nicht unterstützt. Benutzer müssen sich am selben Standort wie die öffentlichen Ordner befinden, damit sie mit Outlook 2011 für Mac oder Outlook für Mac für Office 365 auf diese Ordner zugreifen können. Darüber hinaus können Benutzer, deren Postfächer sich in Exchange Online befinden, nicht über Outlook Web App auf lokale öffentliche Ordner zugreifen.
    

    > [!NOTE]
    > Outlook&nbsp;2016&nbsp;für&nbsp;Mac wird für standortübergreifende öffentliche Ordner unterstützt. Wenn Clients in Ihrer Organisation Outlook&nbsp;2016&nbsp;für&nbsp;Mac verwenden, müssen Sie sicherstellen, dass auf diesen Clients das Update vom April&nbsp;2016 installiert ist. Andernfalls können die Benutzer dieser Clients nicht auf öffentliche Ordner in einer Hybridtopologie zugreifen. Weitere Informationen finden Sie unter <A href="accessing-public-folders-with-outlook-2016-for-mac-exchange-2013-help.md">Zugreifen auf öffentliche Ordner mit Outlook&nbsp;2016&nbsp;für&nbsp;Mac</A>.



## Schritt 1: Herunterladen der Skripts

1.  Laden Sie unter [Mail-enabled Public Folders - directory sync script](https://www.microsoft.com/en-us/download/details.aspx?id=46381) die folgenden Dateien herunter:
    
      - `Sync-MailPublicFolders.ps1`
    
      - `SyncMailPublicFolders.strings.psd1`

2.  Speichern Sie die Dateien auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts.

## Schritt 2: Konfigurieren der Verzeichnissynchronisierung

Der Verzeichnissynchronisierungsdienst synchronisiert keine E-Mail-aktivierten Öffentlichen Ordner. Durch Ausführung der folgenden Skripts werden die E-Mail-aktivierten öffentlichen Ordner standortübergreifend und Office 365 synchronisiert. Spezifische Berechtigungen, die E-Mail-aktivierten öffentliche Ordnern zugewiesen wurden, müssen in der Cloud erneut erstellt werden, da standortübergreifende Berechtigungen nicht in Hybridbereitstellungen unterstützt werden. Weitere Informationen finden Sie unter [Exchange hybrid deployment documentation](https://technet.microsoft.com/de-de/59e32000-4fcf-417f-a491-f1d8f9aeef9b\(exchg.150\)#doc).


> [!NOTE]
> Synchronisierte E-Mail-aktivierte öffentliche Ordner werden für Nachrichtenflusszwecke als E-Mail-Kontaktobjekte angezeigt und werden im Exchange-Verwaltungskonsole nicht angezeigt. Siehe „Get-MailPublicFolder“-Befehl. Verwenden Sie zum erneuten Erstellen der SendAs-Berechtigungen in der Cloud den „RecipientPermission“-Befehl.



1.  Führen Sie auf dem Exchange 2013-Server den folgenden Befehl zum Synchronisieren von E-Mail-aktivierten öffentlichen Ordnern vom lokalen Active Directory mit O365 aus.
    
        Sync-MailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
    Dabei gilt: `Credential` ist Ihr Office 365-Benutzername und das Kennwort, und `CsvSummaryFile` ist der Pfad für das Verzeichnis, in dem Sie das Protokoll der Synchronisierungsvorgänge und Fehler im CSV-Format speichern möchten.


> [!NOTE]
> Vor der Ausführung des Skripts wird empfohlen, dass Sie die vom Skript ausgeführten Aktionen zunächst in Ihrer Umgebung simulieren, indem Sie dieses zunächst wie beschrieben mit dem <CODE>-WhatIf</CODE>-Parameter ausführen.<BR>Es wird empfohlen, dieses Skript täglich auszuführen, um Ihre E-Mail-aktivierten öffentlichen Ordner zu synchronisieren.



## Schritt 3: Konfigurieren des Zugriffs auf lokale öffentliche Exchange 2013-Ordner für Exchange Online-Benutzer

Der letzte Schritt in diesem Verfahren ist, die Exchange-Onlineorganisation zu konfigurieren und Zugriff auf die öffentlichen Exchange 2013-Ordner zu gewähren.

Ermöglichen Sie der Exchange Online-Organisation den Zugriff auf lokale Öffentliche Ordner. Sie zeigen auf alle lokalen Öffentliche Ordner-Postfächer.

    Set-OrganizationConfig -PublicFoldersEnabled Remote -RemotePublicFolderMailboxes PFMailbox1,PFMailbox2,PFMailbox3


> [!NOTE]
> Die Änderungen werden erst angezeigt, wenn die Active Directory-Synchronisierung abgeschlossen ist. Es kann bis zu 3&nbsp;Stunden dauern, bis dieser Vorgang abgeschlossen ist. Wenn Sie nicht auf die sich wiederholenden Synchronisierungen warten möchten, die alle drei Stunden stattfinden, können Sie die Verzeichnissynchronisierung jederzeit erzwingen. Ausführliche Schritte für das Erzwingen der Verzeichnissynchronisierung finden Sie unter <A href="http://technet.microsoft.com/de-de/library/jj151771.aspx">Erzwingen der Verzeichnissynchronisierung</A>.



## Woher weiß ich, dass der Vorgang erfolgreich war?

1.  Melden Sie sich mit einem Benutzer bei Outlook an, der in Exchange Online gespeichert ist, und führen Sie die folgenden Tests für Öffentliche Ordner durch:
    
      - Zeigen Sie die Hierarchie an.
    
      - Prüfen Sie Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

