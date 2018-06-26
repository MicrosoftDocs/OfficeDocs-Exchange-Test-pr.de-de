---
title: 'Konfigurieren öffentlicher Exchange Online-Ordner für eine Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Konfigurieren öffentlicher Exchange Online-Ordner für eine Hybridbereitstellung
ms:assetid: d979edb3-967b-4431-8beb-0c236bf7f56d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt729076(v=EXCHG.150)
ms:contentKeyID: 72778039
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren öffentlicher Exchange Online-Ordner für eine Hybridbereitstellung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-15_

**Zusammenfassung:** In diesem Artikel erfahren Sie, wie Sie lokalen Exchange 2013-Benutzern den Zugriff auf öffentliche Ordner in Exchange Online ermöglichen können.

In einer Hybridbereitstellung können Ihre Benutzer in Exchange Online und/oder lokal sein, und Ihre öffentlichen Ordner sind entweder in Exchange Online oder lokal gespeichert. Manchmal müssen Ihre Onlinebenutzer auf öffentliche Ordner in Ihrer lokalen Exchange Server 2013-Umgebung zugreifen. Ebenso müssen Exchange 2013-Benutzer möglicherweise auf öffentliche Ordner in Office 365 oder Exchange Online zugreifen.

In diesem Artikel wird beschrieben, wie Sie es Benutzern in Ihrer lokalen Exchange 2013-Umgebung ermöglichen können, auf öffentliche Ordner in Exchange Online/Office 365 zuzugreifen. Wie Sie Exchange Online-/Office 365-Benutzern den Zugriff auf öffentliche Ordner in lokalen Exchange 2013-Umgebungen ermöglichen, können Sie im Artikel [Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung](configure-exchange-2013-public-folders-for-a-hybrid-deployment-exchange-2013-help.md) nachlesen.


> [!NOTE]
> Wenn Sie über öffentliche Exchange 2010- oder Exchange 2007-Ordner verfügen, finden Sie weitere Informationen unter <A href="configure-legacy-on-premises-public-folders-for-a-hybrid-deployment-exchange-2013-help.md">Konfigurieren lokaler öffentlicher Ordner aus Vorversionen für eine Hybridbereitstellung</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

1.  Bei diesen Anleitungen wird davon ausgegangen, dass Sie zur Konfiguration und Synchronisierung Ihrer lokalen und Exchange Online-Umgebungen den Assistenten für die Hybridkonfiguration verwendet haben, und dass die DNS-Einträge für die AutoErmittlung bei den meisten Benutzern auf einen lokalen Endpunkt verweisen. Weitere Informationen finden Sie unter [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/de-de/library/hh529921\(v=exchg.150\)).

2.  Bei diesen Anweisungen wird vorausgesetzt, dass Outlook Anywhere aktiviert und auf den lokalen Exchange-Servern funktionsbereit ist. Weitere Informationen über das Aktivieren von Outlook Anywhere finden Sie unter [Outlook Anywhere](outlook-anywhere-exchange-2013-help.md).

3.  Bei der Implementierung der Koexistenz öffentlicher Ordner für eine Hybridbereitstellung von Exchange mit Office 365 müssen Sie während des Imports möglicherweise Konflikte beheben. Konflikte können aufgrund von E-Mail-aktivierten öffentlichen Ordnern zugewiesenen, nicht-routingfähigen E-Mail-Adressen auftreten, oder es können sich Konflikte mit anderen Benutzern und Gruppen in Office 365 oder aufgrund von anderen Attributen ergeben.

4.  Um standortübergreifend auf Öffentliche Ordner zuzugreifen, müssen Benutzer ihre Outlook-Clients auf das Outlook-Update vom November 2012 oder höher aktualisieren.
    
    1.  Unter [Update für Microsoft Outlook 2010 (KB2687623) 32-Bit-Edition](https://www.microsoft.com/de-de/download/details.aspx?id=35702) können Sie das Outlook-Update vom November 2012 für Outlook 2010 herunterladen.
    
    2.  Unter [Update für Microsoft Office Outlook 2007 (KB2687404)](https://www.microsoft.com/de-de/download/details.aspx?id=35718) können Sie das Outlook-Update vom November 2012 für Outlook 2007 herunterladen.

5.  Outlook 2011 für Mac und Outlook für Mac für Office 365 werden für standortübergreifende öffentliche Ordner nicht unterstützt. Benutzer muss sich am selben Standort wie die öffentlichen Ordner befinden, damit sie mit Outlook 2011 für Mac oder Outlook für Mac für Office 365 darauf zugreifen können. Darüber hinaus können Benutzer, deren Postfächer sich in Exchange Online befinden, nicht über Outlook Web App auf lokale öffentliche Ordner zugreifen.
    

    > [!NOTE]
    > Outlook&nbsp;2016&nbsp;für&nbsp;Mac wird für standortübergreifende öffentliche Ordner unterstützt. Wenn Clients in Ihrer Organisation Outlook&nbsp;2016&nbsp;für&nbsp;Mac verwenden, müssen Sie sicherstellen, dass auf diesen Clients das Update vom April&nbsp;2016 installiert ist. Andernfalls können die Benutzer dieser Clients nicht auf öffentliche Ordner in einer Koexistenz oder einer Hybrid-Topologie zugreifen. Weitere Informationen finden Sie unter <A href="accessing-public-folders-with-outlook-2016-for-mac-exchange-2013-help.md">Zugreifen auf öffentliche Ordner mit Outlook&nbsp;2016&nbsp;für&nbsp;Mac</A>.



## Schritt 1: Herunterladen der Skripts

1.  Laden Sie die folgenden Dateien unter dem Link [Mail-enabled Public Folders - directory sync from EXO to On-prem script](https://go.microsoft.com/fwlink/p/?linkid=797795) herunter:
    
      - `Import-PublicFolderMailboxes.ps1`
    
      - `ImportPublicFolderMailboxes.strings.psd1`
    
      - `Sync-MailPublicFoldersCloudToOnprem.ps1`
    
      - `Sync-MailPublicFoldersCloudToOnprem.strings.psd1`

2.  Speichern Sie die Dateien auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts.

## Schritt 2: Konfigurieren der Verzeichnissynchronisierung

Bei Ausführung synchronisiert das Skript `Sync-MailPublicFoldersCloudToOnprem.ps1` die E-Mail-aktivierten öffentlichen Ordner aus Exchange Online und Ihrer lokalen Exchange 2013-Umgebung miteinander. Spezifische Berechtigungen, die E-Mail-aktivierten öffentlichen Ordnern zugewiesen wurden, müssen in der Cloud erneut erstellt werden, da standortübergreifende Berechtigungen nicht in Hybridbereitstellungen unterstützt werden. Weitere Informationen finden Sie unter [Exchange hybrid deployment documentation](https://technet.microsoft.com/de-de/59e32000-4fcf-417f-a491-f1d8f9aeef9b\(exchg.150\)#doc).


> [!NOTE]
> Synchronisierte E-Mail-aktivierte öffentliche Ordner werden für Nachrichtenflusszwecke als E-Mail-Kontaktobjekte angezeigt und werden im Exchange Admin Center nicht angezeigt. Siehe „Get-MailPublicFolder“-Befehl. Verwenden Sie zum erneuten Erstellen der SendAs-Berechtigungen in der Cloud den „RecipientPermission“-Befehl.



1.  Führen Sie auf dem Exchange 2013-Server den folgenden Befehl aus, um die E-Mail-aktivierten öffentlichen Ordner in Exchange Online/Office 365 mit Ihrem lokalen Active Directory zu synchronisieren:
    
        Sync-MailPublicFoldersCloudToOnprem.ps1 -Credential (Get-Credential)
    
    Geben Sie dabei für `Credential` Ihren Office 365-Benutzernamen samt Passwort ein.


> [!NOTE]
> Wir empfehlen Ihnen, dieses Skript täglich auszuführen, um Ihre E-Mail-aktivierten öffentlichen Ordner zu synchronisieren.



## Schritt 3: Konfigurieren des Zugriffs auf öffentliche Exchange Online-Ordner für lokale Benutzer

Im letzten Schritt dieses Verfahrens konfigurieren Sie die lokale Exchange 2013-Organisation so, dass Zugriff auf öffentliche Exchange Online-Ordner möglich ist.

Mithilfe des Skripts `Import-PublicFolderMailboxes.ps1` werden die Postfachobjekte des Typs „Öffentlicher Ordner“ als E-Mail-aktivierte Benutzer aus der Cloud in Ihre lokale Umgebung importiert. Das Skript konfiguriert die importierten Objekte zudem als Remote-Postfächer des Typs „Öffentlicher Ordner“.

1.  Führen Sie auf dem Exchange 2013-Server den folgenden Befehl aus, um die Postfachobjekte des Typs „Öffentlicher Ordner“ aus der Cloud in Ihr lokales Active Directory zu importieren:
    
        Import-PublicFolderMailboxes.ps1 -Credential (Get-Credential)
    
    Geben Sie dabei für `Credential` Ihren Office 365-Benutzernamen samt Passwort ein.
    

    > [!NOTE]
    > Wir empfehlen, dieses Skript täglich auszuführen, um Ihre Postfachobjekte des Typs „Öffentlicher Ordner“ zu importieren. Der Grund: Wann immer Postfächer des Typs „Öffentlicher Ordner“ ihren Kapazitätsschwellenwert erreichen, werden sie automatisch in mehrere neue Postfächer aufgeteilt. Daher sollten Sie immer sicherstellen, dass Sie die neuesten Postfächer des Typs „Öffentlicher Ordner“ aus der Cloud importiert haben.



2.  Aktivieren Sie für die lokale Exchange 2013-Organisation den Zugriff auf die öffentlichen Ordner in Exchange Online.
    
        Set-OrganizationConfig -PublicFoldersEnabled Remote


> [!NOTE]
> Die Änderungen werden erst angezeigt, wenn die Active Directory-Synchronisierung abgeschlossen ist. Es kann bis zu 3&nbsp;Stunden dauern, bis dieser Vorgang abgeschlossen ist. Wenn Sie nicht auf die sich wiederholenden Synchronisierungen warten möchten, die alle drei Stunden stattfinden, können Sie die Verzeichnissynchronisierung jederzeit erzwingen. Ausführliche Schritte für das Erzwingen der Verzeichnissynchronisierung finden Sie unter <A href="http://technet.microsoft.com/de-de/library/jj151771.aspx">Erzwingen der Verzeichnissynchronisierung</A>.



## Woher weiß ich, dass der Vorgang erfolgreich war?

1.  Melden Sie sich mit einem Benutzer bei Outlook an, der in Exchange Online gespeichert ist, und führen Sie die folgenden Tests für Öffentliche Ordner durch:
    
      - Zeigen Sie die Hierarchie an.
    
      - Prüfen Sie Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

