---
title: 'Verwalten von In-Situ-Archiven in Exchange 2013: Exchange 2013 Help'
TOCTitle: Verwalten von In-Situ-Archiven in Exchange 2013
ms:assetid: 49ef4a3e-d209-4fb2-80a3-6132b0f69bd0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ651146(v=EXCHG.150)
ms:contentKeyID: 50475576
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von In-Situ-Archiven in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-02-01_

In-Situ-Archive unterstützten Sie dabei, die Kontrolle über die Messagingdaten in Ihrer Organisation zurückzuerlangen, da keine PST-Dateien mehr benötigt werden und Sie den Organisationsanforderungen in Bezug auf Nachrichtenaufbewahrung und eDiscovery gerecht werden können. Mit aktivierter Archivierung können Benutzer Nachrichten in einem Archivpostfach speichern, auf das mithilfe von MicrosoftOutlook und Outlook Web App zugegriffen werden kann.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-Archive" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Es wird nicht unterstützt, das primäre Postfach eines Benutzers auf einer älteren Exchange-Version zu belassen als das Archiv des Benutzers. Falls sich das primäre Postfach des Benutzers noch auf Exchange 2010 befindet, müssen Sie es zu Exchange 2013 verschieben, wenn Sie das Archiv zu Exchange 2013 verschieben.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen eines Postfachs und Aktivierung eines lokalen Archivs

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie auf **Neu** \> **Benutzerpostfach**.

3.  Geben Sie auf der Seite **Neues Benutzerpostfach** im Feld **Alias** einen Alias für den Benutzer ein.
    

    > [!NOTE]
    > Wenn Sie dieses Feld leer lassen, wird der im Feld <STRONG>Benutzeranmeldename</STRONG> eingegebene Wert als Alias verwendet.



4.  
    
    Wählen Sie eine der folgenden Optionen aus:
    
      - **Vorhandener Benutzer**   Klicken Sie auf diese Schaltfläche, und klicken Sie dann auf **Durchsuchen**, um das Dialogfeld **Benutzer auswählen – Vollständige Gesamtstruktur** zu öffnen. Dieses Dialogfeld enthält eine Liste mit Active Directory-Benutzerkonten in der Gesamtstruktur, die nicht E-Mail-aktiviert sind bzw. nicht über Exchange-Postfächer verfügen. Wählen Sie das Benutzerkonto aus, das für E-Mail aktiviert werden soll, und klicken Sie auf **OK**. Wenn Sie diese Option auswählen, brauchen Sie keine Informationen zum Benutzerkonto anzugeben, da diese Informationen bereits in Active Directory vorhanden sind.
    
      - **Neuer Benutzer**   Klicken Sie auf diese Schaltfläche, um ein neues Benutzerkonto in Active Directory und ein Postfach für den Benutzer zu erstellen. Wenn Sie diese Option auswählen, müssen Sie die erforderlichen Informationen zum Benutzerkonto angeben.
    

    > [!NOTE]
    > Das Active Directory-Konto, das Benutzerpostfächern zugeordnet ist, muss sich in derselben Gesamtstruktur wie der Exchange-Server befinden. Sie müssen ein verknüpftes Postfach erstellen, um ein Postfach für ein Benutzerkonto zu erstellen, das sich in einer vertrauenswürdigen Gesamtstruktur befindet. Weitere Informationen finden Sie unter <A href="manage-linked-mailboxes-exchange-2013-help.md">Verwalten verknüpfter Postfächer</A>.



5.  
    
    Klicken Sie auf **Weitere Optionen**, um die folgenden Einstellungen zu konfigurieren.
    
      - **Postfachdatenbank**   Klicken Sie auf **Durchsuchen**, um eine Postfachdatenbank für die Speicherung des Postfachs auszuwählen. Wenn Sie keine Datenbank auswählen, weist Exchange automatisch eine zu.
    
      - **Archiv**   Aktivieren Sie dieses Kontrollkästchen, um ein Archivpostfach für das Postfach zu erstellen. Wenn Sie ein Archivpostfach erstellen, werden Postfachelemente automatisch entsprechend den standardmäßigen oder von Ihnen definierten Aufbewahrungsrichtlinien aus dem primären Postfach in das Archiv verschoben.
        
        Klicken Sie auf **Durchsuchen**, um zum Speichern des Archivpostfachs eine Datenbank auszuwählen, die sich in der lokalen Gesamtstruktur befindet.
        
        Weitere Informationen finden Sie unter [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md).
    
      - **Adressbuchrichtlinie**   Verwenden Sie diese Liste, um eine Adressbuchrichtlinie für das Postfach anzugeben. Adressbuchrichtlinien enthalten eine globale Adressbuchline (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Wenn sie Postfachbenutzern zugewiesen wird, kann diesen über die Adressbuchrichtlinie Zugriff auf eine angepasste GAL in Outlook und Outlook Web App bereitgestellt werden. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).

6.  
    
    Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um das Postfach zu erstellen.

## Verwenden der Shell

In diesem Beispiel wird der Benutzer "Chris Ashton" in Active Directory erstellt, in der Postfachdatenbank "DB01" wird ein Postfach erstellt, und es wird ein Archiv aktiviert. Das Kennwort muss bei der nächsten Anmeldung neu festgelegt werden. Um das anfängliche Kennwort festzulegen, erstellt dieses Beispiel eine Variable ($password), fordert Sie zur Eingabe eines Kennworts auf und weist dieses Kennwort der Variablen als SecureString-Objekt zu.

    $password = Read-Host "Enter password" -AsSecureString
    New-Mailbox -UserPrincipalName chris@contoso.com -Alias chris -Archive -Database "DB01" -Name ChrisAshton -OrganizationalUnit Users -Password $password -FirstName Chris -LastName Ashton -DisplayName "Chris Ashton" 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines Benutzerpostfachs mit einem lokalen Archiv zu überprüfen:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**, und wählen Sie dann das neue Benutzerpostfach aus der Liste aus. Bestätigen Sie im Detailbereich unter **Compliance-Archiv**, dass diese Option auf **Aktiviert** eingestellt ist. Klicken Sie auf **Details anzeigen**, um die Archiveigenschaften anzuzeigen. Dazu zählen der Archivstatus und die Postfachdatenbank, in der das Archiv erstellt ist.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen Benutzerpostfach und -archiv anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress,*Archive*

  - Verwenden Sie in der Shell das Cmdlet **Test-ArchiveConnectivity**, um die Konnektivität mit dem Archiv zu testen. Ein Beispiel für die Vorgehensweise zum Testen der Archivkonnektivität finden Sie im Abschnitt "Beispiele" unter [Test-ArchiveConnectivity](https://technet.microsoft.com/de-de/library/hh529914\(v=exchg.150\)).

## Aktivieren eines lokalen Archivs für ein vorhandenes Postfach

Sie können auch Archive für vorhandene Benutzer erstellen, die über ein Postfach verfügen, die aber nicht für die Archivierung aktiviert sind. Dieser Vorgang wird als *Aktivierung eines Archivs* für ein vorhandenes Postfach bezeichnet.

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie ein Postfach aus.

3.  Klicken Sie im Detailbereich unter **Compliance-Archiv** auf **Aktivieren**
    

    > [!TIP]
    > Sie können auch mehrere Archive gleichzeitig aktivieren, indem Sie mehrere Postfächer auswählen. (Verwenden Sie dazu die UMSCHALT- oder die STRG-Taste.) Klicken Sie nach der Auswahl mehrerer Postfächer im Detailbereich auf <STRONG>Weitere Optionen</STRONG>. Klicken Sie dann unter <STRONG>Archiv</STRONG> auf <STRONG>Aktivieren</STRONG>.



4.  Klicken Sie auf der Seite **Compliance-Archiv erstellen** auf **OK**, damit Exchange automatisch eine Postfachdatenbank für das Archiv auswählt, oder klicken Sie auf **Durchsuchen**, um eine auszuwählen.

## Verwenden der Shell

In diesem Beispiel wird das Archiv für das Postfach von Tony Smith aktiviert.

    Enable-Mailbox "Tony Smith" -Archive

In diesem Beispiel werden Postfächer in der Datenbank "DB01" abgerufen, für die weder ein lokales noch ein cloudbasiertes Archiv aktiviert ist und deren Name nicht mit "DiscoverySearchMailbox" beginnt. Das Ergebnis wird mittels Pipe an das Cmdlet **Enable-Mailbox** übergeben, um ein Archiv für alle Postfächer in der Postfachdatenbank "DB01" zu aktivieren.

    Get-Mailbox -Database DB01 -Filter {ArchiveGuid -Eq $null -AND ArchiveDomain -eq $null -AND Name -NotLike "DiscoverySearchMailbox*"} | Enable-Mailbox -Archive

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Enable-Mailbox](https://technet.microsoft.com/de-de/library/aa998251\(v=exchg.150\)) und [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Aktivierung eines lokalen Archivs für ein vorhandenes Postfach zu überprüfen:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**, und wählen Sie dann das Postfach aus der Liste aus. Bestätigen Sie im Detailbereich unter **Compliance-Archiv**, dass diese Option auf **Aktiviert** eingestellt ist. Klicken Sie auf **Details anzeigen**, um die Archiveigenschaften anzuzeigen. Dazu zählen der Archivstatus und die Postfachdatenbank, in der das Archiv erstellt ist.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen Archiv anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,*Archive*

  - Verwenden Sie in der Shell das Cmdlet **Test-ArchiveConnectivity**, um die Konnektivität mit dem Archiv zu testen. Beispiele für die Vorgehensweise zum Testen der Archivkonnektivität finden Sie unter [Test-ArchiveConnectivity](https://technet.microsoft.com/de-de/library/hh529914\(v=exchg.150\)).

## Deaktivieren eines lokalen Archivs

Sie können das Archiv eines Benutzers zur Problembehandlung oder vor dem Verschieben des Postfachs in eine Exchange-Version ohne Unterstützung von Compliance-Archiven deaktivieren. Wenn Sie ein lokales Archiv deaktivieren, verbleiben alle Informationen im Archiv in der Postfachdatenbank, bis die Aufbewahrungszeit für das Postfach abgelaufen ist und das Archiv endgültig gelöscht wird. (Standardmäßig behält Exchange getrennte Postfächer, einschließlich von Archivpostfächern, für dreißig Tage bei.)


> [!IMPORTANT]
> Beim Deaktivieren des Archivs wird dieses aus dem Postfach entfernt und in der Postfachdatenbank zum Löschen gekennzeichnet.



Wenn Sie das lokale Archiv wieder mit dem Postfach verbinden möchten, können Sie hierzu das Cmdlet [Connect-Mailbox](https://technet.microsoft.com/de-de/library/aa997878\(v=exchg.150\)) mit dem Parameter *Archive* verwenden.

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie ein Postfach aus.

3.  Klicken Sie im Detailbereich unter **Compliance-Archiv** auf **Deaktivieren**.
    

    > [!TIP]
    > Sie können auch mehrere Archive gleichzeitig deaktivieren, indem Sie mehrere Postfächer auswählen. (Verwenden Sie dazu die UMSCHALT- oder die STRG-Taste.) Klicken Sie nach der Auswahl mehrerer Postfächer im Detailbereich auf <STRONG>Weitere Optionen</STRONG>. Klicken Sie dann unter <STRONG>Archiv</STRONG> auf <STRONG>Deaktivieren</STRONG>.



## Verwenden der Shell

In diesem Beispiel wird das Archiv für das Postfach von Chris Ashton deaktiviert. Das Postfach wird nicht deaktiviert.

    Disable-Mailbox -Identity "Chris Ashton" -Archive

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Disable-Mailbox](https://technet.microsoft.com/de-de/library/aa997210\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Deaktivierung des Archivs zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole das Postfach aus. Prüfen Sie anschließend dessen Archivstatus im Detailbereich unter **Compliance-Archiv**.

  - Verwenden Sie in der Shell den folgenden Befehl, um die Archiveigenschaften für den Postfachbenutzer zu überprüfen.
    
        Get-Mailbox -Identity "Chris Ashton" | Format-List *Archive*
    
    Wenn das Archiv deaktiviert ist, werden für archivbezogene Eigenschaften die folgenden Werte zurückgegeben.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Eigenschaft</th>
    <th>Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>ArchiveDatabase (für lokale Archive)</p></td>
    <td><p>&lt;leer&gt;</p></td>
    </tr>
    <tr class="even">
    <td><p>ArchiveState</p></td>
    <td><p><code>None</code></p></td>
    </tr>
    <tr class="odd">
    <td><p>DisabledArchiveDatabase (für lokale Archive)</p></td>
    <td><p>&lt;Name der Postfachdatenbank&gt;</p></td>
    </tr>
    <tr class="even">
    <td><p>DisabledArchiveGuid</p></td>
    <td><p>&lt;GUID des deaktivierten Archivs&gt;</p></td>
    </tr>
    </tbody>
    </table>


## Herstellen einer Verbindung mit einem lokalen Archiv

Wenn Sie ein Archivpostfach deaktivieren, wird die Verbindung getrennt. Ein getrenntes Archivpostfach wird für einen festgelegten Zeitraum in der Postfachdatenbank aufbewahrt. Standardmäßig behält Exchange getrennte Archive 30 Tage lang bei. In diesem Zeitraum können Sie das Archiv wiederherstellen, indem Sie es einem vorhandenen Postfach zuordnen. Sie können die Aufbewahrungszeit für gelöschte Postfächer ändern, um ein gelöschtes Postfach oder ein Archiv für einen längeren oder einen kürzeren Zeitraum aufzubewahren.


> [!WARNING]
> Wenn Sie ein Archiv für einen Benutzer deaktivieren und anschließend ein Archiv für denselben Benutzer aktivieren, erhält der Benutzer ein neues Archiv. Das neue Archiv enthält keine der Daten, die im getrennten Benutzerarchiv vorlagen. Wenn Sie den Benutzer wieder mit seinem bzw. ihrem getrennten Archiv verbinden möchten, führen Sie hierzu das nachstehende Verfahren durch.




> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Verbinden eines getrennten Archivs mit einem Postfachbenutzer verwendet werden.



## Verwenden der Shell

1.  Wenn Sie den Namen des Archivs nicht kennen, können Sie diesen in der Shell anzeigen, indem Sie den folgenden Befehl ausführen. In diesem Beispiel wird die Postfachdatenbank "DB01" abgerufen und mittels Pipe an das Cmdlet **Get-MailboxStatistics** übergeben, um Postfachstatistiken für alle Postfächer in der Datenbank abzurufen. Dann wird das Cmdlet **Where-Object** zur Filterung der Ergebnisse und zum Abrufen einer Liste der getrennten Archive verwendet. Der Befehl zeigt zusätzliche Informationen zu jedem Archiv sowie die GUID und die Elementanzahl an.
    
        Get-MailboxDatabase "DB01" | Get-MailboxStatistics | Where {($_.DisconnectDate -ne $null) -and ($_.IsArchiveMailbox -eq $true)} | Format-List

2.  Verbinden Sie das Archiv mit dem primären Postfach. In diesem Beispiel wird das Archiv von Chris Ashton mit dem primären Postfach von Chris Ashton verbunden. Hierbei wird die GUID als Identität des Archivs verwendet.
    
        Enable-Mailbox -ArchiveGuid "8734c04e-981e-4ccf-a547-1c1ac7ebf3e2" -ArchiveDatabase "DB01" -Identity "Chris Ashton"

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\))

  - [Get-MailboxStatistics](https://technet.microsoft.com/de-de/library/bb124612\(v=exchg.150\))

  - [Enable-Mailbox](https://technet.microsoft.com/de-de/library/aa998251\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zur Überprüfung der erfolgreichen Verbindung eines getrennten Archivs mit einem Postfachbenutzer führen Sie den folgenden Shell-Befehl auf, um die Archiveigenschaften für den Postfachbenutzer abzurufen und die zurückgegebenen Werte für die Eigenschaften *ArchiveGuid* und *ArchiveDatabase* zu überprüfen:

    Get-Mailbox -Identity "Chris Ashton" | Format-List *Archive*

