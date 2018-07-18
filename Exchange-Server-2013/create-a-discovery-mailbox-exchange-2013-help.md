---
title: 'Erstellen eines Discoverypostfachs: Exchange 2013 Help'
TOCTitle: Erstellen eines Discoverypostfachs
ms:assetid: bc20285d-35e2-4e49-9bd3-38abf96114ba
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638177(v=EXCHG.150)
ms:contentKeyID: 50476582
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Discoverypostfachs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Server 2013-Setup erstellt standardmäßig ein Discoverypostfach. In Exchange Online wird ebenfalls standardmäßig ein Discoverypostfach erstellt. Discoverypostfächer sind als Zielpostfächer für [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)-Suchvorgänge im Exchange-Verwaltungskonsole (EAC) verfügbar. Sie können nach Bedarf zusätzliche Discoverypostfächer erstellen. Nachdem Sie ein neues Discoverypostfach erstellt haben, müssen Sie den betreffenden Benutzern Vollzugriff gewähren, damit sie auf die eDiscovery-Suchergebnisse zugreifen können, die in das Discoverypostfach kopiert werden.


> [!WARNING]
> Nachdem ein Discovery-Manager die Ergebnisse einer eDiscovery-Suche in ein Discoverypostfach kopiert hat, kann das Postfach potenziell vertrauliche Informationen enthalten. Sie sollten den Zugriff auf Discoverypostfächer daher kontrollieren und sicherstellen, dass nur autorisierte Benutzer darauf zugreifen können.



Weitere Informationen finden Sie unter [Discovery mailboxes](in-place-ediscovery-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Erstellen von Discoverypostfächern" im Thema[Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Für Discoverypostfächer gilt ein Postfachspeicherkontingent von 50 GB. Dieses Speicherkontingent kann nicht erhöht werden.

  - Mit der Exchange-Verwaltungskonsole können Sie kein Discoverypostfach erstellen oder Zugriffsrechte darauf gewähren. Sie müssen die Shell verwenden. In Office 365 verwenden Sie Remote PowerShell, das mit Ihrer Exchange Online-Organisation verbunden ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## (Optional) Schritt 1: Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell

Diesen Schritt müssen Sie nur ausführen, wenn Sie über eine Exchange Online- oder Office 365-Organisation verfügen. Wenn Sie über eine Exchange Server 2013-Organisation verfügen, fahren Sie mit dem nächsten Schritt fort und führen Sie den Befehl in der Exchange-Verwaltungsshell aus.

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

## Schritt 2: Erstellen eines Discoverypostfachs

In diesem Beispiel wird das Discoverypostfach "SearchResults" erstellt.

    New-Mailbox -Name SearchResults -Discovery 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

Um eine Liste aller Discoverypostfächer in einer Exchange-Organisation anzuzeigen, führen Sie den folgenden Befehl aus:

    Get-Mailbox -Resultsize unlimited -Filter {RecipientTypeDetails -eq "DiscoveryMailbox"}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

## Schritt 3: Zuweisen von Berechtigungen zu einem Discoverypostfach

Sie müssen Benutzern oder Gruppen explizit die Berechtigung zum Öffnen des von Ihnen erstellten Discoverypostfachs zuweisen. Verwenden Sie die folgende Syntax, um einem Benutzer oder einer Gruppe die Berechtigung zum Öffnen eines Discoverypostfachs und zum Anzeigen der Suchergebnisse zu gewähren:

    Add-MailboxPermission <Name of the discovery mailbox> -User <Name of user or group> -AccessRights FullAccess -InheritanceType all

Mit dem folgenden Befehl wird der Gruppe Litigation-Manager zum Beispiel Vollzugriff zugewiesen, sodass die Mitglieder dieser Gruppe das Discoverypostfach "Fabrikam Litigation" öffnen können.

    Add-MailboxPermission "Fabrikam Litigation" -User "Litigation Managers" -AccessRights FullAccess -InheritanceType all

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-MailboxPermission](https://technet.microsoft.com/de-de/library/bb124097\(v=exchg.150\)).

## Weitere Informationen

  - Standardmäßig haben Mitglieder der Rollengruppe "Discoveryverwaltung" nur auf das standardmäßige Discovery-Suchpostfach Vollzugriff. Sie müssen der Rollengruppe "Discoveryverwaltung" explizit den Vollzugriff zuweisen, damit die Mitglieder ein von Ihnen erstelltes Discoverypostfach öffnen können.

  - Auch wenn das Discoverypostfach in der Exchange-Adressenliste angezeigt wird, können die Benutzer keine E-Mail-Nachrichten an dieses Postfach senden. Die E-Mail-Zustellung an Discoverypostfächer ist aufgrund von Zustellungseinschränkungen unzulässig. Auf diese Weise wird die Integrität der Suchergebnisse gewährleistet, die in ein Discoverypostfach kopiert werden.

  - Ein Discoverypostfach kann nicht für einen anderen Zweck wiederverwendet oder in einen anderen Postfachtyp umgewandelt werden.

  - Sie können ein Discoverypostfach ebenso löschen wie jeden anderen Postfachtyp.

