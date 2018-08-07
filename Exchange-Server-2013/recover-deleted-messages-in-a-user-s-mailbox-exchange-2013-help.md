---
title: 'Wiederherstellen v. gelöscht. Nachr. im Benutzerpostfach: Exchange 2013-Hilfe'
TOCTitle: Wiederherstellen von gelöschten Nachrichten im Postfach eines Benutzers
ms:assetid: 9e0e34ce-efc5-454e-8d15-57b4da867f12
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff660637(v=EXCHG.150)
ms:contentKeyID: 50554886
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederherstellen von gelöschten Nachrichten im Postfach eines Benutzers

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

(Dieses Thema richtet sich an Exchange-Administratoren.)

Administratoren können im Postfach eines Benutzers nach gelöschten E-Mails suchen und sie wiederherstellen. Dies schließt durch eine Person (mit der Funktion „Gelöschte Elemente wiederherstellen in Outlook oder Outlook Web App) dauerhafte gelöschte (bereinigte) Elemente oder Elemente ein, die durch einen automatischen Prozess gelöscht wurden, beispielsweise die Benutzerpostfächern zugewiesene Aufbewahrungsrichtlinie. In diesen Situationen können die gelöschten Elemente durch einen Benutzer nicht wiederhergestellt werden. Administratoren können jedoch gelöschte Nachrichten wiederherstellen, wenn die Beibehaltungsdauer für das gelöschte Element nicht abgelaufen ist.


> [!NOTE]
> Sie können dieses Verfahren nicht nur zum Suchen und Wiederherstellen gelöschter Elemente verwenden (die aus dem Ordner "Wiederherstellbare Elemente\Löschungen" verschoben werden, wenn die Wiederherstellung einzelner Elemente oder die Aufbewahrung für eventuelle Rechtsstreitigkeiten aktiviert ist), sondern auch zum Suchen nach Elementen in anderen Ordnern des Postfachs sowie zum Löschen von Elementen aus dem Quellpostfach (auch bekannt als <EM>Suchen und Vernichten</EM>).



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15-30 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Bevor das Element, das Sie wiederherstellen möchten, gelöscht wird, muss die Wiederherstellung einzelner Elemente für ein Postfach aktiviert sein. In Exchange Online ist die Wiederherstellung einzelner Elemente standardmäßig aktiviert, wenn ein neues Postfach erstellt wird. Standardmäßig ist die Wiederherstellung einzelner Elemente in Exchange 2013 bei der Erstellung eines Postfachs deaktiviert. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Wiederherstellung einzelner Elemente für ein Postfach](enable-or-disable-single-item-recovery-for-a-mailbox-exchange-2013-help.md).

  - Zum Suchen und Wiederherstellen von Elementen benötigen Sie die folgenden Informationen:
    
      - **Quellpostfach**   Dies ist das Postfach, das durchsucht wird.
    
      - **Zielpostfach**  Dies ist das Discoverypostfach, in dem Nachrichten wiederhergestellt werden. Exchange Setup erstellt ein Standarddiscoverypostfach. In Exchange Online wird ebenfalls standardmäßig ein Discoverypostfach erstellt. Falls erforderlich, können Sie zusätzliche Discoverypostfächer erstellen. Weitere Informationen finden Sie unter [Erstellen eines Discoverypostfachs](create-a-discovery-mailbox-exchange-2013-help.md).
        

        > [!NOTE]
        > Wenn Sie das Cmdlet <STRONG>Search-Mailbox</STRONG> verwenden, können Sie auch ein Zielpostfach angeben, bei dem es sich nicht um ein Discoverypostfach handelt. Sie können jedoch nicht dasselbe Postfach als Quell- und als Zielpostfach angeben.

    
      - **Suchkriterien**   Zu den Kriterien gehören Absender, Empfänger oder Schlüsselwörter (Wörter oder Begriffe) in der Nachricht.

  - Dieser Artikel konzentriert sich auf die Verwendung der PowerShell zur Wiederherstellung gelöschter Elemente im Postfach eines Benutzers. Sie können auch das GUI-basierte Tool für In-Situ-eDiscovery verwenden, um gelöschte Elemente zu finden und in eine PST-Datei zu exportieren. Der Benutzer verwendet diese PST-Datei zur Wiederherstellung von gelöschten Nachrichten in sein Postfach. Eine detaillierte Anleitung finden Sie unter [Wiederherstellen gelöschter Elemente im Postfach eines Benutzers - Hilfe für Administratoren](https://go.microsoft.com/fwlink/p/?linkid=722928).

## (Optional) Schritt 1: Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell

Diesen Schritt müssen Sie nur ausführen, wenn Sie über eine Exchange Online- oder Office 365-Organisation verfügen. Wenn Sie über eine Exchange 2013-Organisation verfügen, fahren Sie mit dem nächsten Schritt fort und führen Sie den Befehl in der Exchange-Verwaltungsshell aus.

1.  Öffnen Sie auf Ihrem lokalen Computer Windows PowerShell, und führen Sie dann den folgenden Befehl aus.
    
        $UserCredential = Get-Credential
    
    Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** den Benutzernamen und das Kennwort des globalen Office 365-Administratorkontos ein, und klicken Sie dann auf **OK**.

2.  Führen Sie den folgenden Befehl aus.
    
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

3.  Führen Sie den folgenden Befehl aus.
    
        Import-PSSession $Session

4.  Um zu prüfen, ob Sie mit Ihrer Exchange Online-Organisation verbunden sind, führen Sie den folgenden Befehl aus, um eine Liste aller Postfächer in Ihrer Organisation abzurufen.
    
        Get-Mailbox

Weitere Informationen oder Hinweise bei Problemen mit der Verbindung zu Ihrer Exchange Online-Organisation finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://go.microsoft.com/fwlink/p/?linkid=517283).

## Schritt 2: Suchen und Wiederherstellen fehlender Elemente

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).


> [!NOTE]
> Sie können die Compliance-eDiscovery in Exchange Admin Center (EAC) verwenden, um nach fehlenden Elementen zu suchen. Bei Verwenden der Exchange-Verwaltungskonsole können Sie allerdings die Suche nicht auf den Ordner <STRONG>Wiederherstellbare Elemente</STRONG> beschränken. Nachrichten, die Ihren Suchparametern entsprechen, werden zurückgegeben, auch wenn sie nicht gelöscht wurden. Nach ihrer Wiederherstellung im angegebenen Discoverypostfach müssen Sie ggf. die Suchergebnisse überprüfen und nicht benötigte Nachrichten entfernen, ehe Sie die verbleibenden Nachrichten im Postfach des Benutzers wiederherstellen oder diese in eine PST-Datei exportieren.<BR>Einzelheiten zum Durchführen einer Compliance-eDiscovery-Suche mithilfe der Exchange-Verwaltungskonsole finden Sie unter <A href="create-an-in-place-ediscovery-search-exchange-2013-help.md">Erstellen einer Compliance-eDiscovery-Suche</A>.



Der erste Schritt im Wiederherstellungsprozess besteht in der Suche nach Nachrichten im Quellpostfach. Durchsuchen Sie mithilfe einer der folgenden Methoden ein Benutzerpostfach, und kopieren Sie Nachrichten in ein Discoverypostfach.

In diesem Beispiel wird das Postfach von April Stewart nach Nachrichten durchsucht, die folgende Kriterien erfüllen:

  - Absender: Ken Kwok

  - Schlüsselwort: Seattle

<!-- end list -->

    Search-Mailbox "April Stewart" -SearchQuery "from:'Ken Kwok' AND seattle" -TargetMailbox "Discovery Search Mailbox" -TargetFolder "April Stewart Recovery" -LogLevel Full


> [!NOTE]
> Wenn Sie das Cmdlet <STRONG>Search-Mailbox</STRONG> verwenden, können Sie den Suchbereich mithilfe des Parameters <EM>SearchQuery</EM> definieren, um eine mit Keyword Query Language (KQL) formatierte Abfrage anzugeben. Sie können auch die Option <EM>SearchDumpsterOnly</EM> angeben, um nur Elemente im Ordner <STRONG>Wiederherstellbare Elemente</STRONG> zu suchen.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)).

**Woher wissen Sie, dass dieses Verfahren erfolgreich war?**

Um zu prüfen, ob Sie die Nachricht erfolgreich durchsucht haben, die Sie wiederherstellen möchten, melden Sie sich am Discoverypostfach an, das Sie als Zielpostfach ausgewählt haben, und überprüfen Sie die Suchergebnisse.

## Schritt 3: Wiederherstellen wiederhergestellter Elemente

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Zurückspeichern wiederhergestellter Elemente verwendet werden.



Nach dem Wiederherstellen von Nachrichten in einem Discoverypostfach können Sie diese mithilfe des Cmdlets **Search-Mailbox** im Postfach des Benutzers wiederherstellen. Außerdem können Sie in Exchange 2013 die Nachrichten mithilfe der Cmdlets **New-MailboxExportRequest** und **New-MailboxImportRequest** in eine PST-Datei exportieren oder daraus importieren.

## Verwenden der Shell zum Wiederherstellen von Nachrichten

In diesem Beispiel werden Nachrichten im Postfach von April Stewart wiederhergestellt und aus dem Disoverysuchpostfach gelöscht.

    Search-Mailbox "Discovery Search Mailbox" -SearchQuery "from:'Ken Kwok' AND seattle" -TargetMailbox "April Stewart" -TargetFolder "Recovered Messages" -LogLevel Full -DeleteContent

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-Mailbox](https://technet.microsoft.com/de-de/library/dd298173\(v=exchg.150\)).

**Woher wissen Sie, dass dieses Verfahren erfolgreich war?**

Um zu prüfen, ob Sie Nachrichten erfolgreich im Postfach des Benutzers wiederhergestellt haben, lassen Sie den Benutzer Nachrichten im Zielordner überprüfen, den Sie im obigen Befehl angegeben haben.

## (Exchange 2013) Verwenden der Shell zum Exportieren und Importieren von Nachrichten in und aus einer PST-Datei

Sie können Inhalte in Exchange 2013 aus einem Postfach in eine PST-Datei exportieren und den Inhalt einer PST-Datei in ein Postfach importieren. Weitere Informationen zu Postfachimport und -export finden Sie unter [Import- und Exportanforderungen für Postfächer](mailbox-import-and-export-requests-exchange-2013-help.md). Diese Aufgabe können Sie in Exchange Online nicht ausführen.

In diesem Beispiel werden die folgenden Einstellungen zum Exportieren von Nachrichten aus dem Ordner "April Stewart Recovery" im Disoverysuchpostfach in eine PST-Datei exportiert:

  - **Postfach**   Discoverysuchpostfach

  - **Quellordner**   April Stewart Recovery

  - **ContentFilter**   April travel plans

  - **Pfad der PST-Datei**   \\\\MYSERVER\\HelpDeskPst\\AprilStewartRecovery.pst

<!-- end list -->

    New-MailboxExportRequest -Mailbox "Discovery Search Mailbox" -SourceRootFolder "April Stewart Recovery" -ContentFilter {Subject -eq "April travel plans"} -FilePath \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxExportRequest](https://technet.microsoft.com/de-de/library/ff607299\(v=exchg.150\)).

In diesem Beispiel werden die folgenden Einstellungen zum Importieren von Nachrichten aus einer PST-Datei in den Ordner "Recovered By Helpdesk" im Postfach von April Stewart verwendet:

  - **Postfach**   April Stewart

  - **Zielordner**   Recovered By Helpdesk

  - **Pfad der PST-Datei**   \\\\MYSERVER\\HelpDeskPst\\AprilStewartRecovery.pst

<!-- end list -->

    New-MailboxImportRequest -Mailbox "April Stewart" -TargetRootFolder "Recovered By Helpdesk" -FilePath \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxImportRequest](https://technet.microsoft.com/de-de/library/ff607310\(v=exchg.150\)).

**Woher wissen Sie, dass dieses Verfahren erfolgreich war?**

Um zu prüfen, ob Sie Nachrichten erfolgreich in eine PST-Datei exportiert haben, öffnen Sie die PST-Datei in Outlook, und überprüfen Sie ihren Inhalt. Um zu prüfen, ob Sie Nachrichten erfolgreich aus der PST-Datei importiert haben, lassen Sie den Benutzer den Inhalt des Zielordners überprüfen, den Sie im obigen Befehl angegeben haben.

## Weitere Informationen

  - Die Fähigkeit, gelöschte Elemente wiederherzustellen, wird durch *Wiederherstellung einzelner Elemente* aktiviert. Hiermit kann ein Administrator eine Nachricht wiederherstellen, die durch einen Benutzer oder anhand der Aufbewahrungsrichtlinie gelöscht wurde, solange der Aufbewahrungszeitraum für gelöschte Elemente für dieses Element nicht abgelaufen ist. Weitere Informationen zur Wiederherstellung einzelner Elemente finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

  - Ein Exchange Online-Postfach ist so konfiguriert, dass gelöschte Elemente standardmäßig 14 Tage lang aufbewahrt werden. Für diese Einstellung können Sie maximal 30 Tage festlegen. Standardmäßig ist in Exchange 2013 eine Postfachdatenbank für eine Aufbewahrung gelöschter Elemente für 14 Tage konfiguriert. Sie können Einstellungen für die Aufbewahrung gelöschter Elemente für ein Postfach oder eine Postfachdatenbank konfigurieren. Weitere Informationen finden Sie unter:
    
      - [Ändern des Aufbewahrungszeitraums für gelöschte Elemente für ein Exchange Online-Postfach](https://technet.microsoft.com/de-de/library/dn163584\(v=exchg.150\))
    
      - [Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente](configure-deleted-item-retention-and-recoverable-items-quotas-exchange-2013-help.md)

  - Sie können auch, wie zuvor erläutert, das Tool für In-Situ-eDiscovery verwenden, um gelöschte Elemente zu finden und in eine PST-Datei zu exportieren. Der Benutzer verwendet diese PST-Datei zur Wiederherstellung von gelöschten Nachrichten in sein Postfach. Eine detaillierte Anleitung finden Sie unter [Wiederherstellen gelöschter Elemente im Postfach eines Benutzers - Hilfe für Administratoren](https://go.microsoft.com/fwlink/p/?linkid=722928).

  - Benutzer können ein gelöschtes Element wiederherstellen, wenn es nicht gelöscht wurde und wenn die Aufbewahrungsdauer für das gelöschte Element nicht abgelaufen ist. Sollte ein Benutzer gelöschte Elemente aus dem Ordner "Wiederherstellbare Elemente" wiederherstellen müssen, verweisen Sie ihn auf die folgenden Themen:
    
      - [Wiederherstellen gelöschter Elemente in Outlook 2010](https://go.microsoft.com/fwlink/p/?linkid=524923)
    
      - [Wiederherstellen gelöschter Elemente in Outlook 2013](https://go.microsoft.com/fwlink/p/?linkid=624829)
    
      - [Wiederherstellen gelöschter Elemente oder E-Mails in Outlook Online](https://go.microsoft.com/fwlink/p/?linkid=524924)

  - In diesem Thema wird die Verwendung des Cmdlets **Search-Mailbox** beschrieben, um fehlende Elemente zu suchen und wiederherzustellen. Mit diesem Cmdlet können Sie jeweils nur ein Postfach durchsuchen. Wenn Sie mehrere Postfächer gleichzeitig durchsuchen möchten, können Sie [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md) in Exchange Admin Center (EAC) oder das Cmdlet [New-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298064\(v=exchg.150\)) in Windows PowerShell verwenden.

  - Zusätzlich zur Verwendung dieser Prozedur zum Suchen und Wiederherstellen gelöschter Elemente können Sie auch eine ähnliche Prozedur verwenden, um nach Elementen in Benutzerpostfächern zu suchen und um diese dann aus dem Quellpostfach zu löschen. Weitere Informationen finden Sie unter [Suchen nach und Löschen von Nachrichten – Administratorhilfe](search-for-and-delete-messages-admin-help-exchange-2013-help.md).

