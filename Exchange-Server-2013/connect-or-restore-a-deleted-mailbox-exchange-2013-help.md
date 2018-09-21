---
title: 'Verbinden oder Wiederherstellen eines gelöschten Postfachs: Exchange 2013 Help'
TOCTitle: Verbinden oder Wiederherstellen eines gelöschten Postfachs
ms:assetid: a5e6ac44-5901-4eab-9017-c6fae80a0f83
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863438(v=EXCHG.150)
ms:contentKeyID: 50554888
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbinden oder Wiederherstellen eines gelöschten Postfachs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-05-04_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell ein gelöschtes Postfach mit einem Active Directory-Benutzerkonto verbinden. Wenn Sie ein Postfach löschen, bewahrt Exchange das Postfach in der Postfachdatenbank auf und schaltet es in einen deaktivierten Status um. Das dazugehörige Active Directory-Benutzerkonto wird ebenfalls gelöscht. Das Postfach wird aufbewahrt, bis der Aufbewahrungszeitraum für gelöschte Postfächer abgelaufen ist, der standardmäßig 30 Tage beträgt. Danach wird es aus der Postfachdatenbank *endgültig gelöscht*.

Bis ein gelöschtes Postfach aus der Exchange-Postfachdatenbank endgültig gelöscht wird, können Sie es über die Exchange-Verwaltungskonsole oder Shell mit einem Active Directory-Benutzerkonto verbinden. Sie können auch die Shell verwenden, um den Inhalt des gelöschten Postfachs in einem vorhandenen Postfach wiederherzustellen.

Weitere Informationen zu getrennten Postfächern und zum Durchführen anderer dazugehöriger Verwaltungsaufgaben finden Sie in den folgenden Themen:

  - [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md)

  - [Deaktivieren oder Löschen eines Postfachs](disable-or-delete-a-mailbox-exchange-2013-help.md)

  - [Verbinden eines deaktivierten Postfachs](connect-a-disabled-mailbox-exchange-2013-help.md)

  - [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Erstellen Sie ein neues Benutzerkonto in Active Directory, mit dem das gelöschte Postfach verbunden werden soll. Oder prüfen Sie mit dem Cmdlet **Get-User** in der Shell, ob das Active Directory-Benutzerkonto, mit dem Sie das gelöschte Postfach verbinden möchten, vorhanden ist und ob es nicht bereits einem anderen Postfach zugeordnet ist. Damit ein gelöschtes Postfach mit einem Benutzerkonto verbunden werden kann, muss das Konto vorhanden sein, und der Wert der Eigenschaft *RecipientType* muss `User` lauten, was bedeutet, dass das Konto nicht bereits für ein Postfach aktiviert ist.
    
    In lokalen Exchange-Organisationen können Sie diese Information auch in **Active Directory-Benutzer und -Computer** überprüfen.
    

    > [!IMPORTANT]
    > Wenn Sie eine Verbindung mit gelöschten verknüpften, Ressourcen- oder freigegebenen Postfächern herstellen, muss das Active Directory-Benutzerkonto, das Sie mit dem Postfach verbinden, deaktiviert sein.



  - Um sicherzustellen, dass das gelöschte Postfach, das Sie mit einem Benutzerkonto verbinden möchten, in der Postfachdatenbank vorhanden und nicht ein vorläufig gelöschtes Postfach ist, führen Sie den folgenden Befehl aus.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,Database,DisconnectReason
    
    Das gelöschte Postfach muss in der Postfachdatenbank vorhanden sein, und der Wert der Eigenschaft *DisconnectReason* muss `Disabled` sein. Wenn das Postfach endgültig aus der Datenbank gelöscht wurde, gibt der Befehl keine Ergebnisse zurück.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)..

## Was möchten Sie machen?

## Herstellen einer Verbindung mit einem gelöschten Postfach

Wenn Sie eine Verbindung mit einem gelöschten Postfach herstellen, ordnen Sie das Postfach einem Benutzerkonto zu, das nicht für E-Mail aktiviert ist, was bedeutet, dass es noch kein Postfach hat. Zum Verbinden eines gelöschten Postfachs mit einem Benutzerkonto mit einem Postfach müssen Sie das gelöschte Postfach wiederherstellen. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt Wiederherstellen eines gelöschten Postfachs.

## Herstellen einer Verbindung mit einem gelöschten Postfach mithilfe der Exchange-Verwaltungskonsole

Im folgenden Verfahren wird gezeigt, wie ein gelöschtes Benutzerpostfach mit einem Benutzerkonto verbunden wird. Sie können dieses Verfahren auch befolgen, um verknüpfte, Ressourcen- oder freigegebene Postfächer, die gelöscht wurden, mit einem Benutzerkonto zu verbinden.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie auf **Mehr** ![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Postfach verbinden**.
    
    Es wird eine Liste mit Postfächern angezeigt, die auf dem ausgewählten Exchange-Server in Ihrer Exchange-Organisation getrennt sind.
    

    > [!NOTE]
    > Diese Liste getrennter Postfächer enthält deaktivierte, gelöschte und nicht endgültig gelöschte Postfächer.



3.  Klicken Sie auf das gelöschte Postfach, das Sie mit einem Benutzerkonto verbinden möchten, und klicken Sie dann auf **Verbinden**.

4.  Klicken Sie in der Warnmeldung, die abfragt, ob Sie wirklich eine Verbindung mit dem Postfach herstellen möchten, auf **Ja**.
    
    Eine Liste der Benutzerkonten, die nicht für E-Mail aktiviert sind, wird angezeigt.

5.  Klicken Sie auf das Benutzerkonto, mit dem Sie das gelöschte Postfach verbinden möchten, und klicken Sie dann auf **OK**.
    
    Exchange verbindet das gelöschte Postfach mit dem ausgewählten Benutzerkonto.

## Herstellen einer Verbindung mit einem gelöschten Postfach mithilfe der Shell

Über das Cmdlet **Connect-Mailbox** in der Shell können Sie ein gelöschtes Postfach mit einem Benutzerkonto verbinden, das nicht für E-Mail aktiviert ist. Sie müssen den Typ des Postfachs angeben, mit dem Sie eine Verbindung herstellen. Es folgen Beispiele der Syntax für das erneute Verbinden von Benutzer-, verknüpften, Raum-, Geräte- und freigegebenen Postfächern. In allen Beispielen wird der optionale Parameter *Alias* verwendet, um den E-Mail-Alias anzugeben. Dies ist der Teil links vom Symbol (@) der E-Mail-Adresse. Wenn Sie den Parameter *Alias* nicht angeben, wird der im Parameter *User* oder *LinkedMasterAccount* angegebene Wert verwendet, um den Alias der E-Mail-Adresse des erneut verbundenen Postfachs zu erstellen.


> [!NOTE]
> Wenn Sie eine Verbindung mit verknüpften, Ressourcen- oder freigegebenen Postfächern herstellen, muss (wie bereits erwähnt) das Active Directory-Benutzerkonto, das Sie mit dem Postfach verbinden, deaktiviert sein.



In diesem Beispiel wird ein Benutzerpostfach verbunden. Der Parameter *Identity* gibt den Anzeigenamen des gelöschten Postfachs an, das in der Postfachdatenbank MBXDB01 aufbewahrt wird. Der Parameter *User* gibt das Active Directory-Benutzerkonto an, mit dem das Postfach verbunden wird.

```powershell
Connect-Mailbox -Identity "Paul Cannon" -Database MBXDB01 -User "Robin Wood" -Alias robinw
```


> [!NOTE]
> Sie können zum Bestimmen des gelöschten Postfachs auch die Eigenschaften <CODE>LegacyDN</CODE> oder <CODE>MailboxGuid</CODE> verwenden.



In diesem Beispiel wird ein verknüpftes Postfach verbunden. Der Parameter *Identity* gibt das gelöschte Postfach in der Postfachdatenbank MBXDB02 an. Der Parameter *LinkedMasterAccount* gibt das Active Directory-Benutzerkonto in der Kontogesamtstruktur an, mit dem Sie das Postfach verbinden möchten. Der Parameter *LinkedDomainController* gibt einen Domänencontroller in der Kontogesamtstruktur an.

    Connect-Mailbox -Identity "Temp User" -Database MBXDB02 -LinkedDomainController FabrikamDC01 -LinkedMasterAccount danpark@fabrikam.com -Alias dpark

In diesem Beispiel wird ein Raumpostfach verbunden.

    Connect-Mailbox -Identity "rm2121" -Database "MBXResourceDB" -User "Conference Room 2121" -Alias ConfRm2121 -Room

In diesem Beispiel wird ein Gerätepostfach verbunden.

    Connect-Mailbox -Identity "MotorPool01" -Database "MBXResourceDB" -User "Van01 (12 passengers)" -Alias van01 -Equipment

In diesem Beispiel wird ein freigegebenes Postfach verbunden.

    Connect-Mailbox -Identity "Printer Support" -Database MBXDB01 -User "Corp Printer Support" -Alias corpprint -Shared


> [!NOTE]
> Sie können zum Bestimmen des gelöschten Postfachs auch die Werte <CODE>LegacyDN</CODE> oder <CODE>MailboxGuid</CODE> verwenden.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Connect-Mailbox](https://technet.microsoft.com/de-de/library/aa997878\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um zu überprüfen, ob Sie ein gelöschtes Postfach erfolgreich mit einem Benutzerkonto verbunden haben:

  - Klicken Sie in das Exchange-Verwaltungskonsole auf **Empfänger**, navigieren Sie zur entsprechenden Seite des Postfachtyps, mit dem Sie eine Verbindung hergestellt haben, klicken Sie auf **Aktualisieren** ![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)"), und prüfen Sie, ob das Postfach aufgeführt ist.

  - Klicken Sie in **Active Directory-Benutzer und -Computer** mit der rechten Maustaste auf das Benutzerkonto, mit dem Sie das Postfach verbunden haben, und klicken Sie dann auf **Eigenschaften**. Auf der Registerkarte **Allgemein** sehen Sie, dass das Feld **E-Mail** die E-Mail-Adresse des verbundenen Postfachs enthält.

  - Führen Sie in der Shell den folgenden Befehl aus.
    
    ```powershell
Get-User <identity>
```
    
    Der Wert **UserMailbox** der Eigenschaft *RecipientType* gibt an, dass das Benutzerkonto und das Postfach verbunden sind. Sie können auch den Befehl **Get-Mailbox \<identity\>** ausführen, um zu prüfen, ob das Postfach verbunden wurde.

## Wiederherstellen eines gelöschten Postfachs

Sie können auch über die Shell mit dem Cmdlet **New-MailboxRestoreRequest** ein gelöschtes Postfach in einem vorhandenen Postfach wiederherstellen. Wenn Sie ein gelöschtes Postfach wiederherstellen, wird der Inhalt in ein vorhandenes Postfach kopiert, das als *Zielpostfach* bezeichnet wird. Nachdem ein gelöschtes Postfach wiederhergestellt wurde, wird es weiter in der Postfachdatenbank aufbewahrt, bis es von einem Administrator oder nach Ablauf des Aufbewahrungszeitraums für gelöschte Postfächer dauerhaft gelöscht wird.

Nachdem eine Anforderung einer Postfachwiederherstellung erfolgreich erfüllt wurde, wird das Postfach standardmäßig 30 Tage aufbewahrt, ehe es entfernt wird. Mit dem Cmdlet **Remove-StoreMailbox** können Sie es früher entfernen.


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Wiederherstellen eines gelöschten Postfachs verwendet werden.



## Wiederherstellen eines gelöschten Postfachs mithilfe der Shell

Zum Erstellen einer Anforderung einer Postfachwiederherstellung müssen Sie den Anzeigenamen, Legacy-DN (Distinguished Name) oder die Postfach-GUID des gelöschten Postfachs angeben. Mit dem Cmdlet **Get-MailboxStatistics** können Sie die Werte der Eigenschaften `DisplayName`, `MailboxGuid` und `LegacyDN` des gelöschten Postfachs anzeigen, das Sie wiederherstellen möchten. Führen Sie beispielsweise den folgenden Befehl aus, um diese Informationen für alle deaktivierten und gelöschten Postfächer in Ihrer Organisation zurückzugeben.

    Get-MailboxDatabase | Get-MailboxStatistics | Where {$_.DisconnectReason -eq "Disabled"} | fl DisplayName,MailboxGuid,LegacyDN,Database

In diesem Beispiel wird das gelöschte Postfach, das vom Parameter *SourceStoreMailbox* bestimmt wird und in der Postfachdatenbank MBXDB01 enthalten ist, im Zielpostfach "Debra Garcia" wiederhergestellt. Der Parameter *AllowLegacyDNMismatch* wird verwendet, damit das Quellpostfach in einem anderen Postfach wiederhergestellt werden kann, das nicht über denselben Legacy-DN-Wert verfügt.

    New-MailboxRestoreRequest -SourceStoreMailbox e4890ee7-79a2-4f94-9569-91e61eac372b -SourceDatabase MBXDB01 -TargetMailbox "Debra Garcia" -AllowLegacyDNMismatch

In diesem Beispiel wird das gelöschte Archivpostfach von Pilar Pinilla in ihrem aktuellen Archivpostfach wiederhergestellt. Der Parameter *AllowLegacyDNMismatch* ist nicht erforderlich, da ein primäres Postfach und sein dazugehöriges Archivpostfach denselben Legacy-DN haben.

    New-MailboxRestoreRequest -SourceStoreMailbox "Personal Archive - Pilar Pinilla" -SourceDatabase "MDB01" -TargetMailbox pilarp@contoso.com -TargetIsArchive

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)).

## Wiederherstellen eines gelöschten Postfachs im öffentlichen Ordner mithilfe der Shell

Wenn Sie ein Postfach für öffentliche Ordner dauerhaft gelöscht haben und Sie es nun wiederherstellen möchten, und sich das Postfach innerhalb der Aufbewahrungszeit für gelöschte Elemente befindet (siehe [Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente](configure-deleted-item-retention-and-recoverable-items-quotas-exchange-2013-help.md)), können Sie das `Connect-Mailbox`-Cmdlet gefolgt vom `Update-StoreMailboxState`-Cmdlet verwenden. Ausführliche Syntax- und Parameterinformationen finden Sie unter [Connect-Mailbox](https://technet.microsoft.com/de-de/library/aa997878\(v=exchg.150\)) und [Update-StoreMailboxState](https://technet.microsoft.com/de-de/library/jj860462\(v=exchg.150\)).

Sie benötigen die GUID des gelöschten Postfachs auf einem öffentlichen Ordner sowie die GUID oder den Namen der Postfachdatenbank, die das Postfach auf dem öffentlichen Ordner enthielt. Wenn Sie nicht über diese Informationen verfügen, können Sie die folgenden Schritte ausführen:

1.  Rufen Sie die Active Directory-Gesamtstruktur und den vollqualifizierten Domänennamen (FQDN) des Domänencontrollers ab, indem Sie das folgende Cmdlet ausführen:
    
    ```powershell
Get-OrganizationConfig | fl OriginatingServer
```

2.  Suchen Sie anhand der in Schritt 1 zurückgegebenen Informationen im Container für gelöschte Objekte in Active Directory nach der GUID des Postfachs für öffentliche Ordner sowie nach der GUID bzw. nach dem Namen der Postfachdatenbank, in der das Postfach für öffentliche Ordner enthalten war.
    

    > [!TIP]
    > Sie können die gelöschten Objekte mithilfe eines benutzerdefinierten Skripts oder mithilfe des Ldp-Hilfsprogramms durchsuchen, das durch Eingabe von <STRONG>ldp.exe</STRONG> an einer PowerShell-Eingabeaufforderung geöffnet werden kann.



Wenn Sie die GUID des Postfachs für öffentliche Ordner und den Namen bzw. die GUID der Postfachdatenbank, in der das Postfach für öffentliche Ordner enthalten war, kennen, führen Sie die folgenden Befehle aus, um das Postfach für öffentliche Ordner wiederherzustellen.

1.  Erstellen Sie ein neues Active Directory-Objekt, indem Sie die folgenden Befehle ausführen (Sie werden möglicherweise aufgefordert, entsprechende Anmeldeinformationen einzugeben):
    
        New-MailUser <mailUserName> -ExternalEmailAddress <emailAddress> 
        
        Get-MailUser <mailUserName> | Disable-MailUser
    
    `<mailUserName>`, `<emailAddress>`, und `<mailUserName>` sind dabei Werte, die Sie auswählen. Im nächsten Schritt müssen Sie denselben `<mailUserName>`-Wert verwenden.

2.  Verbinden Sie das Postfach für öffentliche Ordner mit dem soeben erstellten Active Directory-Objekt, indem Sie den folgenden Befehl ausführen:
    
        Connect-Mailbox -Identity <public folder mailbox GUID> -Database <database name or GUID> -User <mailUserName>
    

    > [!NOTE]
    > Der <CODE>Identity</CODE>-Parameter gibt das Postfacobjekt in der Exchange-Datenbank an, das mit einem Active Directory-Benutzerobjekt verbunden werden soll. In dem Beispiel oben wird die GUID für das Postfach für öffentliche Ordner angegeben, Sie können jedoch auch den Wert für den Anzeigenamen oder den LegacyExchangeDN-Wert verwenden.



3.  Führen Sie `Update-StoreMailboxState` in dem Postfach für öffentliche Ordner aus, wie in dem folgenden Beispiel dargestellt:
    
        Update-StoreMailboxState -Identity <public folder mailbox GUID> -Database <database name or GUID>
    
    Wie in Schritt 2 akzeptiert der `Identity`-Parameter die Werte für die GUID, den Anzeigenamen oder LegacyExchangeDN für das Postfach für öffentliche Ordner.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie ein gelöschtes Postfach für öffentliche Ordner wiederhergestellt haben, führen Sie das Cmdlet **Get-PublicFolder -GetChildren -\<public folder mailbox GUID\>** aus. Wenn die Wiederherstellung erfolgreich war, funktioniert dieses Cmdlet.

Weitere Informationen finden Sie unter:

  - [Connect-Mailbox](https://technet.microsoft.com/de-de/library/aa997878\(v=exchg.150\))

  - [Update-StoreMailboxState](https://technet.microsoft.com/de-de/library/jj860462\(v=exchg.150\))

