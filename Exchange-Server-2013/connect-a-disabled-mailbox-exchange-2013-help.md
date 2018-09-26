---
title: 'Verbinden eines deaktivierten Postfachs: Exchange 2013 Help'
TOCTitle: Verbinden eines deaktivierten Postfachs
ms:assetid: a8abd399-75fd-4ee2-b2e4-634b55e4f79f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863439(v=EXCHG.150)
ms:contentKeyID: 50554890
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbinden eines deaktivierten Postfachs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-13_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell ein deaktiviertes Postfach mit einem Active Directory-Benutzerkonto verbinden. Wenn Sie ein Postfach deaktivieren, behält Exchange das Postfach in der Postfachdatenbank bei und schaltet es in einen deaktivierten Status. Die Exchange-Attribute werden aus dem dazugehörigen Active Directory-Benutzerkonto entfernt, doch das Benutzerkonto bleibt erhalten. Das Postfach wird aufbewahrt, bis der Aufbewahrungszeitraum für gelöschte Postfächer abgelaufen ist, der standardmäßig 30 Tage beträgt. Danach wird es aus der Postfachdatenbank *endgültig gelöscht*.

Bis ein deaktiviertes Postfach endgültig aus der Exchange-Postfachdatenbank entfernt wird, können Sie es über die Exchange-Verwaltungskonsole oder Shell erneut mit dem ursprünglichen Active Directory-Benutzerkonto verbinden.

Weitere Informationen zu getrennten Postfächern und zum Durchführen anderer dazugehöriger Verwaltungsaufgaben finden Sie in den folgenden Themen:

  - [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md)

  - [Deaktivieren oder Löschen eines Postfachs](disable-or-delete-a-mailbox-exchange-2013-help.md)

  - [Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

  - [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Prüfen Sie mit dem Cmdlet **Get-User** in der Shell, ob das Active Directory-Benutzerkonto, mit dem Sie das deaktivierte Postfach verbinden möchten, vorhanden ist und ob es nicht bereits einem anderen Postfach zugeordnet ist. Damit ein deaktiviertes Postfach mit einem Benutzerkonto verbunden werden kann, muss das Konto vorhanden sein, und der Wert der Eigenschaft *RecipientType* muss `User` lauten, was bedeutet, dass das Konto nicht bereits für ein Postfach aktiviert ist.
    
    In lokalen Exchange-Organisationen können Sie diese Information auch in Active Directory-Benutzer und -Computer überprüfen.

  - Führen Sie den folgenden Befehl aus, um sicherzustellen, dass das deaktivierte Postfach, das Sie mit einem Benutzerkonto verbinden möchten, in der Postfachdatenbank vorhanden und kein vorläufig gelöschtes Postfach ist.
    
    ```powershell
    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,Database,DisconnectReason
    ```
    
    Um eine Verbindung mit einem deaktivierten Postfach herzustellen zu können, muss das Postfach in der Postfachdatenbank vorhanden sein, und der Wert der Eigenschaft *DisconnectReason* muss `Disabled` sein. Wenn das Postfach endgültig aus der Datenbank gelöscht wurde, gibt der Befehl keine Ergebnisse zurück.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]  
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Herstellen einer Verbindung mit einem deaktivierten Postfach mithilfe der Exchange-Verwaltungskonsole

Im folgenden Verfahren wird gezeigt, wie ein deaktiviertes Benutzerpostfach mit einem Benutzerkonto verbunden wird. Sie können auch verknüpfte und freigegebene Postfächer, die deaktiviert wurden, erneut mit dem gewünschten Benutzerkonto verbinden.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie auf **Mehr**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Postfach verbinden**.
    
    Es wird eine Liste mit Postfächern angezeigt, die auf dem ausgewählten Exchange-Server in Ihrer Exchange-Organisation getrennt sind.
    

    > [!NOTE]  
    > Diese Liste getrennter Postfächer enthält deaktivierte, gelöschte und nicht endgültig gelöschte Postfächer.



3.  Klicken Sie auf das deaktivierte Postfach, das Sie erneut mit einem Benutzerkonto verbinden möchten, und klicken Sie dann auf **Verbinden**.

4.  Klicken Sie in der Warnmeldung, die abfragt, ob Sie wirklich erneut eine Verbindung mit dem Postfach herstellen möchten, auf **Ja**.
    
    Exchange verbindet das deaktivierte Postfach erneut mit dem entsprechenden Benutzerkonto.

## Herstellen einer Verbindung mit einem deaktivierten Postfach mithilfe der Shell

Über das Cmdlet **Connect-Mailbox** in der Shell können Sie ein Benutzerkonto mit einem deaktivierten Postfach verbinden. Sie müssen den Typ des Postfachs angeben, mit dem Sie eine Verbindung herstellen. Es folgen Beispiele der Syntax für das erneute Verbinden von Benutzer-, verknüpften und freigegebenen Postfächern.

In diesem Beispiel wird ein Benutzerpostfach verbunden. Der Parameter *Identity* gibt das getrennte Postfach in der Exchange-Datenbank an. Der Parameter *User* gibt das Active Directory-Benutzerkonto an, mit dem das Postfach erneut verbunden wird.

```powershell
Connect-Mailbox -Identity "Jeffrey Zeng" -Database MBXDB01 -User "Jeffrey Zeng"
```

In diesem Beispiel wird ein verknüpftes Postfach verbunden. Der Parameter *Identity* gibt das getrennte Postfach in der Exchange-Datenbank an. Der Parameter *LinkedMasterAccount* gibt das Active Directory-Benutzerkonto in der Kontogesamtstruktur an, mit dem Sie das Postfach erneut verbinden möchten. Der Parameter *Alias* gibt den Alias, d. h. den Teil der E-Mail-Adresse links vom Symbol (@), des erneut verbundenen Postfachs an.

```powershell
Connect-Mailbox -Identity "Kai Axford" -Database MBXDB02 -LinkedDomainController FabrikamDC01 -LinkedMasterAccount kai.axford@fabrikam.com -Alias kaia
```

In diesem Beispiel wird ein freigegebenes Postfach verbunden.

```powershell
Connect-Mailbox -Identity "Corporate Shared Mailbox" -Database "Mailbox Database 03" -User "Corporate Shared Mailbox" -Alias corpshared -Shared
```


> [!NOTE]  
> Wenn Sie bei Ausführen des Cmdlets <STRONG>Connect-Mailbox</STRONG> den Parameter <EM>Alias</EM> nicht angeben, wird der im Parameter <EM>User</EM> oder <EM>LinkedMasterAccount</EM> angegebene Wert verwendet, um den Alias der E-Mail-Adresse des erneut verbundenen Postfachs zu erstellen.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Connect-Mailbox](https://technet.microsoft.com/de-de/library/aa997878\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um zu überprüfen, ob Sie ein deaktiviertes Postfach erfolgreich mit einem Benutzerkonto verbunden haben:

  - Klicken Sie in das Exchange-Verwaltungskonsole auf **Empfänger**, navigieren Sie zur entsprechenden Seite des Postfachtyps, mit dem Sie erneut eine Verbindung hergestellt haben, klicken Sie auf **Aktualisieren**![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)"), und prüfen Sie, ob das Postfach aufgeführt ist.

  - Klicken Sie in Active Directory-Benutzer und -Computer mit der rechten Maustaste auf das Benutzerkonto, dessen Postfach Sie aktiviert haben, und klicken Sie dann auf **Eigenschaften**. Auf der Registerkarte **Allgemein** sehen Sie, dass das Feld **E-Mail** die E-Mail-Adresse des erneut verbundenen Postfachs enthält.

  - Führen Sie in der Shell den folgenden Befehl aus.
    
    ```powershell
    Get-User <identity>
    ```
    
    Der Wert **UserMailbox** der Eigenschaft *RecipientType* gibt an, dass das Benutzerkonto und das Postfach verbunden sind. Sie können auch das Cmdlet **Get-Mailbox** ausführen, um zu prüfen, ob das Postfach vorhanden ist.

