---
title: 'Konfigurieren lokaler öffentlicher Ordner aus Vorversionen für eine Hybridbereitstellung: Exchange Online Help'
TOCTitle: Konfigurieren lokaler öffentlicher Ordner aus Vorversionen für eine Hybridbereitstellung
ms:assetid: bcb0ac98-2949-486b-a8ab-8549c021651b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn249373(v=EXCHG.150)
ms:contentKeyID: 54915030
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren lokaler öffentlicher Ordner aus Vorversionen für eine Hybridbereitstellung

 

_**Gilt für:**Exchange Online, Exchange Server 2010, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2018-05-22_

**Zusammenfassung:** Befolgen Sie die Schritte in diesem Artikel, um öffentliche Ordner zwischen Office 365 und Ihrer lokalen Exchange 2007- oder Exchange Server 2010-Bereitstellung zu synchronisieren.

In einer Hybridbereitstellung können Ihre Benutzer in Exchange Online und/oder lokal sein, und Ihre öffentlichen Ordner sind entweder in Exchange Online oder lokal gespeichert. öffentliche Ordner können sich nur an einem Ort befinden. Sie müssen daher entscheiden, ob Sie Ihre öffentlichen Ordner in Exchange Online oder lokal speichern möchten. Sie können nicht an beiden Speicherorten abgelegt werden. Postfächer für Öffentliche Ordner werden über den Verzeichnissynchronisierungsdienst mit Exchange Online synchronisiert. E-Mail-aktivierte öffentliche Ordner werden allerdings nicht standortübergreifend synchronisiert.

In diesem Thema wird beschrieben, wie Sie E-Mail-aktivierte Öffentliche Ordner synchronisieren, wenn Ihre Benutzer in Office 365 gespeichert sind und Ihre öffentlichen Ordner für Exchange 2010 SP3 oder Exchange 2007 SP3 RU10 lokal gespeichert sind. Office 365-Benutzer, die nicht von einem lokalen MailUser-Objekt dargestellt werden (lokal in der Zielordnerhierarchie öffentlicher Ordner), können nicht auf ältere oder lokale öffentliche Exchange 2013-Ordner zugreifen.


> [!NOTE]
> In diesem Thema werden die Server mit Exchange 2010 SP3 und Exchange 2007 SP3 RU10 als <EM>Exchange-Legacyserver</EM> bezeichnet.



Sie synchronisieren hre E-Mail-aktivierten Öffentlichen Ordner mithilfe der folgenden Skripts, die von einer Windows-Aufgabe initiiert werden, die in der lokalen Umgebung ausgeführt wird:

1.  `Sync-MailPublicFolders.ps1`   Mit diesem Skript werden die E-Mail-aktivierten öffentlichen Ordnerobjekte zwischen Ihrer lokalen Exchange-Bereitstellung und Office 365 synchronisiert. Das Skript verwendet die lokale Exchange-Bereitstellung als Master zum Ermitteln der Änderungen, die auf Office 365 angewendet werden müssen. Es erstellt, aktualisiert oder löscht E-Mail-aktivierte öffentliche Ordnerobjekte in O365 Active Directory anhand derer, die in der lokalen Exchange-Bereitstellung enthalten sind.

2.  `SyncMailPublicFolders.strings.psd1`   Dabei handelt es sich eine Supportdatei, die vom vorangehenden Synchronisierungsskript verwendet wird und an den gleichen Speicherort wie das vorhergehenden Skript kopiert werden muss.

Wenn Sie dieses Verfahren abschließen, können Ihre lokalen und Office 365-Benutzer auf die gleiche lokale öffentliche Ordner-Infrastruktur zugreifen.

## Welche Hybridversionen von Exchange sind mit Öffentlichen Ordnern kompatibel?

Die folgende Tabelle enthält die unterstützten Versions- und Speicherortkombinationen von Benutzerpostfächern und Öffentlichen Ordnern. "Hybrid nicht möglich" ist ein unterstütztes Szenario, gilt aber nicht als Hybridszenario, da Öffentliche Ordner und Benutzer den gleichen Speicherort aufweisen.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>   </th>
<th>Lokales Benutzerpostfach in Exchange 2007 oder Exchange 2010</th>
<th>Lokales Benutzerpostfach in Exchange 2013</th>
<th>Exchange Online-Benutzerpostfach</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lokale Öffentliche Ordner in Exchange 2007 oder Exchange 2010</p></td>
<td><p>Hybrid nicht zutreffend</p></td>
<td><p>Hybrid nicht zutreffend</p></td>
<td><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Lokale Öffentliche Ordner in Exchange 2013</p></td>
<td><p>Hybrid nicht zutreffend</p></td>
<td><p>Hybrid nicht zutreffend</p></td>
<td><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td><p>Öffentliche Ordner in Exchange Online</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Hybrid nicht zutreffend</p></td>
</tr>
</tbody>
</table>


Eine Hybridkonfiguration mit Öffentlichen Ordnern in Exchange 2003 wird nicht unterstützt. Wenn Sie Exchange 2003 in Ihrer Organisation ausführen, müssen Sie alle Öffentliche Ordner-Datenbanken und -Replikate auf Exchange 2007 SP3 RU10 oder höher umstellen. Es können keine Öffentliche Ordner-Replikate in Exchange 2003 bleiben.


> [!NOTE]
> Outlook 2016 bietet keine Unterstützung für den Zugriff auf ältere öffentliche Ordner von Exchange 2007. Wenn Benutzer Outlook 2016 verwenden, müssen Sie die öffentlichen Ordner auf eine neuere Version von Exchange umstellen. Weitere Informationen zur Kompatibilität von Outlook 2016 und Office 2016 mit Exchange 2007 und früheren Versionen finden Sie in <A href="https://go.microsoft.com/fwlink/p/?linkid=849053">diesem Artikel</A>.



## Schritt 1: Was sollten Sie wissen, bevor Sie beginnen?

1.  Bei diesen Anleitungen wird davon ausgegangen, dass Sie zur Konfiguration und Synchronisierung Ihrer lokalen und Exchange Online-Umgebungen den Assistenten für die Hybridkonfiguration verwendet haben, und dass die DNS-Einträge für die AutoErmittlung bei den meisten Benutzern auf einen lokalen Endpunkt verweisen. Weitere Informationen finden Sie unter [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/de-de/library/hh529921\(v=exchg.150\)).

2.  Bei diesen Anweisungen wird vorausgesetzt, dass Outlook Anywhere aktiviert und auf den lokalen Legacy-Exchange-Servern funktionsbereit ist. Weitere Informationen über das Aktivieren von Outlook Anywhere finden Sie unter [Outlook Anywhere](outlook-anywhere-exchange-2013-help.md).

3.  Bei der Implementierung der Koexistenz öffentlicher Ordner aus älteren Versionen für eine Hybridbereitstellung von Exchange mit Office 365 müssen Sie während des Imports möglicherweise Konflikte beheben. Konflikte können aufgrund von E-Mail-aktivierten öffentlichen Ordnern zugewiesenen, nicht-routingfähigen E-Mail-Adressen auftreten, oder es können sich Konflikte mit anderen Benutzern und Gruppen in Office 365 oder aufgrund von anderen Attributen ergeben.

4.  Bei diesen Anleitungen wird davon ausgegangen, dass Ihre Exchange Online-Organisation auf eine Version aktualisiert wurde, die Öffentliche Ordner unterstützt.

5.  In Exchange Online müssen Sie ein Mitglied der Rollengruppe "Organisationsverwaltung" sein. Diese Rollengruppe unterscheidet sich von den Berechtigungen, die Ihnen zugewiesen wurden, als Sie Exchange Online abonniert haben. Weitere Informationen dazu, wie Sie die Rollengruppe "Organisationsverwaltung" aktivieren können, finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

6.  In Exchange 2010 müssen Sie ein Mitglied der Rollengruppen "Organisationsverwaltung" oder "Server Management RBAC" sein. Nähere Informationen finden Sie unter [Hinzufügen von Mitgliedern zu einer Rollengruppe](https://go.microsoft.com/fwlink/?linkid=299212)

7.  In Exchange 2007 muss Ihnen die Rolle "Exchange Organization Administrator" oder "Exchange Server Administrator" zugewiesen sein. Zudem müssen Sie für den Zielserver über die Rolle "Public Folder Administrator" verfügen und Mitglied der lokalen Administratorgruppe sein. Nähere Informationen finden Sie unter [Hinzufügen eines Benutzers oder einer Gruppe zu einer Administratorrolle](https://go.microsoft.com/fwlink/p/?linkid=81779).

8.  Wenn bei Ihnen Exchange Server 2007 unter Windows Server 2008 x64 ausgeführt wird, müssen Sie ein Upgrade auf [Windows PowerShell 2.0 und WinRM 2.0 für Windows Server 2008 x64 Edition](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=968930) durchführen. Wenn bei Ihnen Exchange Server 2007 unter Windows Server 2003 x64 ausgeführt wird, müssen Sie ein Upgrade auf Windows PowerShell 2.0 durchführen. Weitere Informationen finden Sie unter [Update für Windows Server 2003 x64 Edition](https://www.microsoft.com/en-us/download/details.aspx?id=10512).

9.  Um standortübergreifend auf Öffentliche Ordner zuzugreifen, müssen Benutzer ihre Outlook-Clients auf das Outlook-Update vom November 2012 oder höher aktualisieren.
    
    1.  Unter [Update für Microsoft Outlook 2010 (KB2687623) 32-Bit-Edition](https://www.microsoft.com/de-de/download/details.aspx?id=35702) können Sie das Outlook-Update vom November 2012 für Outlook 2010 herunterladen.
    
    2.  Unter [Update für Microsoft Office Outlook 2007 (KB2687404)](https://www.microsoft.com/de-de/download/details.aspx?id=35718) können Sie das Outlook-Update vom November 2012 für Outlook 2007 herunterladen.

10. Outlook 2016 für Mac (und frühere Versionen) sowie Outlook für Mac für Office 365 werden für standortübergreifende öffentliche Ordner nicht unterstützt. Benutzer müssen sich am selben Standort wie die öffentlichen Ordner befinden, damit sie mit Outlook für Mac oder Outlook für Mac für Office 365 darauf zugreifen können. Darüber hinaus können Benutzer, deren Postfächer sich in Exchange Online befinden, nicht über Outlook Web App auf lokale öffentliche Ordner zugreifen.

11. Nachdem Sie die Anweisungen in diesem Artikel zum Konfigurieren Ihrer lokalen öffentliche Ordner für eine Hybridbereitstellung ausgeführt haben, können Benutzer außerhalb Ihrer Organisation keine Nachrichten an die lokalen öffentlichen Ordner senden, wenn Sie keine zusätzliche Schritte ausführen. Sie können entweder die akzeptierte Domäne für die öffentlichen Ordner auf „Internes Relay“ festlegen (weitere Informationen finden Sie unter [Verwalten akzeptierter Domänen in Exchange Online](https://technet.microsoft.com/de-de/library/jj945194\(v=exchg.150\))), oder Sie deaktivieren das verzeichnisbasierte Edge-Blockierung (Directory Based Edge Blocking, DBEB), wie unter [Verwenden von verzeichnisbasierter Edge-Blockierung zum Ablehnen von Nachrichten, die an ungültige Empfänger gesendet wurden](https://technet.microsoft.com/de-de/library/dn600322\(v=exchg.150\)) beschrieben.

## Schritt 2: Sichtbarmachen von remote gespeicherten Öffentlichen Ordnern

1.  Wenn sich Ihre öffentlichen Ordner in Exchange 2010 oder höher befinden, müssen Sie die Clientzugriffs-Serverrolle auf allen Postfachservern installieren, auf denen sich eine Datenbank des Typs "Öffentlicher Ordner" befindet. Dadurch kann der Microsoft Exchange RpcClientAccess-Dienst ausgeführt werden, der allen Clients Zugriff auf öffentliche Ordner ermöglicht. Die Clientzugriffsrolle ist für Exchange 2007-Server mit öffentlichen Ordnern nicht erforderlich, sodass für diese Server dieser Schritt entfällt. Weitere Informationen finden Sie unter [Installieren von Exchange Server 2010](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md). Dieser Schritt ist für öffentliche Ordner in Exchange 2007 nicht erforderlich.
    

    > [!NOTE]
    > Dieser Server muss nicht Teil des Lastenausgleichs von Clientzugriffsservern sein. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/ff625247(v=exchg.141).aspx">Grundlegendes zum Lastenausgleich in Exchange 2010</A>.



2.  Erstellen Sie eine leere Postfachdatenbank auf jedem Server für öffentliche Ordner.
    
    Führen Sie bei Exchange 2010 den folgenden Befehl aus: Durch diesen Befehl wird die Postfachdatenbank vom Lastenausgleich für Postfachbereitstellung ausgeschlossen. Dadurch wird verhindert, dass neue Postfächer automatisch zu dieser Datenbank hinzugefügt werden.
    
        New-MailboxDatabase -Server <PFServerName_with_CASRole> -Name <NewMDBforPFs> -IsExcludedFromProvisioning $true
    
    Führen Sie bei Exchange 2007 den folgenden Befehl aus:
    
        New-MailboxDatabase -StorageGroup "<PFServerName>\StorageGroup>" -Name <NewMDBforPFs>
    

    > [!NOTE]
    > Es wird empfohlen, dass Sie nur das Proxypostfach, das Sie in Schritt&nbsp;3 erstellen, zu dieser Datenbank hinzufügen. In dieser Postfachdatenbank sollten keine anderen Postfächer erstellt werden.



3.  Erstellen Sie in der neuen Postfachdatenbank ein Proxypostfach, und blenden Sie das Postfach im Adressbuch aus. Das SMTP dieses Postfachs wird von der AutoErmittlung als das *DefaultPublicFolderMailbox*-SMTP zurückgegeben, sodass der Client durch Auflösung dieses SMTP den Exchange-Legacyserver erreichen kann, um Zugriff auf öffentliche Ordner zu erhalten.
    
        New-Mailbox -Name <PFMailbox1> -Database <NewMDBforPFs>
    
        Set-Mailbox -Identity <PFMailbox1> -HiddenFromAddressListsEnabled $true

4.  Aktivieren Sie bei Exchange 2010 die AutoErmittlung, um die Proxypostfächer für öffentliche Ordner zurückzugeben. Dieser Schritt ist bei Exchange 2007 nicht erforderlich.
    
        Set-MailboxDatabase <NewMDBforPFs> -RPCClientAccessServer <PFServerName_with_CASRole>

5.  Wiederholen Sie die vorhergehenden Schritte für jeden Öffentliche Ordner-Server in Ihrer Organisation.

## Schritt 3: Herunterladen der Skripts

1.  Laden Sie unter [Mail-enabled Public Folders - directory sync script](https://www.microsoft.com/en-us/download/details.aspx?id=46381) die folgenden Dateien herunter:
    
      - `Sync-MailPublicFolders.ps1`
    
      - `SyncMailPublicFolders.strings.psd1`

2.  Speichern Sie die Dateien auf dem lokalen Computer, auf dem Sie PowerShell ausführen. Verwenden Sie als Speicherort beispielsweise C:\\PFScripts.

## Schritt 4: Konfigurieren der Verzeichnissynchronisierung

Der Verzeichnissynchronisierungsdienst synchronisiert keine E-Mail-aktivierten Öffentlichen Ordner. Durch Ausführung der folgenden Skripts werden die E-Mail-aktivierten öffentlichen Ordner standortübergreifend synchronisiert. Spezifische Berechtigungen, die E-Mail-aktivierten öffentliche Ordnern zugewiesen wurden, müssen in der Cloud erneut erstellt werden, da standortübergreifende Berechtigungen nicht in Hybridbereitstellungen unterstützt werden. Weitere Informationen finden Sie unter [Exchange hybrid deployment documentation](https://technet.microsoft.com/de-de/59e32000-4fcf-417f-a491-f1d8f9aeef9b\(exchg.150\)#doc).


> [!NOTE]
> Synchronisierte E-Mail-aktivierte öffentliche Ordner werden für Nachrichtenflusszwecke als E-Mail-Kontaktobjekte angezeigt und werden im Exchange-Verwaltungskonsole nicht angezeigt. Siehe „Get-MailPublicFolder“-Befehl. Verwenden Sie zum erneuten Erstellen der SendAs-Berechtigungen in der Cloud den „RecipientPermission“-Befehl.



1.  Führen Sie auf dem älteren Exchange-Server den folgenden Befehl zum Synchronisieren von E-Mail-aktivierten öffentlichen Ordnern vom lokalen Active Directory mit O365 aus.
    
        Sync-MailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
    Dabei gilt: `Credential` ist Ihr Office 365-Benutzername und das Kennwort, und `CsvSummaryFile` ist der Pfad für das Verzeichnis, in dem Sie das Protokoll der Synchronisierungsvorgänge und Fehler im CSV-Format speichern möchten.


> [!NOTE]
> Vor der Ausführung des Skripts wird empfohlen, dass Sie die vom Skript ausgeführten Aktionen zunächst in Ihrer Umgebung simulieren, indem Sie dieses zunächst wie beschrieben mit dem <CODE>-WhatIf</CODE>-Parameter ausführen.<BR>Es wird empfohlen, dieses Skript täglich auszuführen, um Ihre E-Mail-aktivierten öffentlichen Ordner zu synchronisieren.



## Schritt 5: Konfigurieren des Zugriffs auf lokale öffentliche Ordner für Exchange Online-Benutzer

Der letzte Schritt in diesem Verfahren ist, die Exchange Online-Organisation zu konfigurieren und Zugriff auf die älteren lokalen öffentlichen Ordner zu gewähren.

Aktivieren Sie die Exchange-Onlineorganisation für den Zugriff auf lokale Öffentliche Ordner. Sie zeigen auf alle Öffentliche Ordner-Proxypostfächer, die Sie in Schritt 2: Sichtbarmachen von remote gespeicherten Öffentlichen Ordnern erstellt haben.

Führen Sie den folgenden Befehl in **Windows PowerShell** aus:

    Set-OrganizationConfig -PublicFoldersEnabled Remote -RemotePublicFolderMailboxes PFMailbox1,PFMailbox2,PFMailbox3

Die Änderungen werden erst angezeigt, wenn die Active Directory-Synchronisierung abgeschlossen ist. Es kann bis zu 3 Stunden dauern, bis dieser Vorgang abgeschlossen ist. Wenn Sie nicht auf die sich wiederholenden Synchronisierungen warten möchten, die alle drei Stunden stattfinden, können Sie die Verzeichnissynchronisierung jederzeit erzwingen. Ausführliche Schritte für das Erzwingen der Verzeichnissynchronisierung finden Sie unter [Erzwingen der Verzeichnissynchronisierung](http://technet.microsoft.com/de-de/library/jj151771.aspx) Office 365 wählt nach dem Zufallsprinzip ein Postfach für öffentliche Ordner, das in diesem Befehl angegeben wird.


> [!IMPORTANT]
> Office&nbsp;365-Benutzer, die nicht von einem lokalen MailUser-Objekt repräsentiert werden (lokal in der Zielhierarchie von öffentlichen Ordnern), können nicht auf öffentliche Ordner in Exchange&nbsp;2013 oder älteren Versionen zugreifen. Eine Lösung dazu finden Sie im Knowledge&nbsp;Base-Artikel <A href="https://go.microsoft.com/fwlink/p/?linkid=699451">Exchange&nbsp;Online-Benutzer können nicht auf öffentliche Ordner in Legacy-Versionen zugreifen</A>.



## Woher weiß ich, dass der Vorgang erfolgreich war?

1.  Melden Sie sich mit einem Benutzer bei Outlook an, der in Exchange Online gespeichert ist, und führen Sie die folgenden Tests für Öffentliche Ordner durch:
    
      - Zeigen Sie die Hierarchie an.
    
      - Prüfen Sie Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

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

