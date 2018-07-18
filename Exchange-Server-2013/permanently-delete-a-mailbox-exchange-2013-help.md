---
title: 'Endgültiges Löschen eines Postfachs: Exchange 2013 Help'
TOCTitle: Endgültiges Löschen eines Postfachs
ms:assetid: df35765a-0bef-4561-9846-d91d69c0269c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863440(v=EXCHG.150)
ms:contentKeyID: 50554929
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Endgültiges Löschen eines Postfachs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-16_

Wenn Sie aktive und getrennte Postfächer endgültig löschen, werden sämtliche Postfachinhalte aus der Exchange-Postfachdatenbank unwiederbringlich entfernt. Wenn Sie ein aktives endgültig dauerhaft löschen, wird das dazugehörige Active Directory-Benutzerkonto ebenfalls gelöscht.

Eine Alternative zum endgültigen Löschen eines Postfachs ist, es zu trennen. Nachdem Sie ein Postfach getrennt haben, wird es standardmäßig 30 Tage in der Postfachdatenbank aufbewahrt. Dies gibt Ihnen die Möglichkeit, ein Postfach wieder zu verbinden oder wiederherzustellen, ehe es endgültig aus der Datenbank entfernt wird.

Weitere Informationen zu getrennten Postfächern und zum Durchführen anderer dazugehöriger Verwaltungsaufgaben finden Sie in den folgenden Themen:

  - [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md)

  - [Deaktivieren oder Löschen eines Postfachs](disable-or-delete-a-mailbox-exchange-2013-help.md)

  - [Verbinden eines deaktivierten Postfachs](connect-a-disabled-mailbox-exchange-2013-help.md)

  - [Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum endgültigen Löschen eines aktiven oder getrennten Postfachs verwendet werden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Endgültiges Löschen eines aktiven Postfachs

## Endgültiges Löschen eines aktiven Postfachs mithilfe der Shell

Führen Sie den folgenden Befehl aus, um ein aktives Postfach und das dazugehörige Active Directory-Benutzerkonto endgültig zu löschen.

    Remove-Mailbox -Identity <identity> -Permanent $true


> [!NOTE]
> Wenn Sie den Parameter <EM>Permanent</EM> nicht angeben, wird das gelöschte Postfach standardmäßig 30&nbsp;Tage in der Postfachdatenbank aufbewahrt, ehe es endgültig gelöscht wird.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-Mailbox](https://technet.microsoft.com/de-de/library/aa995948\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie ein aktives Postfach endgültig gelöscht haben, gehen Sie folgendermaßen vor:

1.  Stellen Sie sicher, dass das Postfach nicht mehr in der Exchange-Verwaltungskonsole aufgeführt ist.

2.  Vergewissern Sie sich, dass das dazugehörige Benutzerkonto nicht mehr in "Active Directory-Benutzer und -Computer" aufgeführt ist.

3.  Führen Sie den folgenden Befehl aus, um zu prüfen, ob das Postfach endgültig aus der Exchange-Postfachdatenbank gelöscht wurde.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" }
    
    Wenn Sie das Postfach erfolgreich endgültig gelöscht haben, gibt der Befehl keine Ergebnisse zurück. Wenn das Postfach nicht endgültig gelöscht wurde, gibt der Befehl Informationen zum Postfach zurück.

## Endgültiges Löschen eines getrennten Postfachs

## Endgültiges Löschen eines getrennten Postfachs mithilfe der Shell

Es gibt zwei Typen von getrennten Postfächern: deaktivierte und vorläufig gelöschte Postfächer. Sie müssen beim Ausführen des Cmdlets einen dieser Typen angeben, um das Postfach endgültig zu löschen. Stimmt der von Ihnen angegebene Typ nicht mit dem tatsächlichen Typ des getrennten Postfachs überein, wird der Befehl nicht ausgeführt.

Führen Sie den folgenden Befehl aus, um zu prüfen, ob ein getrenntes Postfach deaktiviert ist oder vorläufig gelöscht wurde.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,MailboxGuid,Database,DisconnectReason

Der Wert der Eigenschaft *DisconnectReason* bei getrennten Postfächern ist entweder `Disabled` oder `SoftDeleted`.

Sie können den folgenden Befehl ausführen, um den Typ aller getrennten Postfächer in Ihrer Organisation anzuzeigen.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisconnectReason -ne $null } | fl DisplayName,MailboxGuid,Database,DisconnectReason


> [!WARNING]
> Wenn Sie mit dem Cmdlet <STRONG>Remove-StoreMailbox</STRONG> ein getrenntes Postfach und dessen gesamten Inhalt aus der Postfachdatenbank löschen, ist der Datenverlust endgültig.



In diesem Beispiel wird das deaktivierte Postfach mit der GUID "2ab32ce3-fae1-4402-9489-c67e3ae173d3" endgültig aus der Postfachdatenbank "MBD01" gelöscht.

    Remove-StoreMailbox -Database MBD01 -Identity "2ab32ce3-fae1-4402-9489-c67e3ae173d3" -MailboxState Disabled

In diesem Beispiel wird das vorläufig gelöschte Postfach Dan Jump Ayla endgültig aus der Postfachdatenbank MBD01 gelöscht.

    Remove-StoreMailbox -Database MBD01 -Identity "Dan Jump" -MailboxState SoftDeleted

In diesem Beispiel werden alle vorläufig gelöschten Postfächer endgültig aus der Postfachdatenbank "MBD01" gelöscht.

    Get-MailboxStatistics -Database MBD01 | where {$_.DisconnectReason -eq "SoftDeleted"} | ForEach {Remove-StoreMailbox -Database $_.Database -Identity $_.MailboxGuid -MailboxState SoftDeleted}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-StoreMailbox](https://technet.microsoft.com/de-de/library/ff829913\(v=exchg.150\)) und [Get-MailboxStatistics](https://technet.microsoft.com/de-de/library/bb124612\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Prüfen, ob ein getrenntes Postfach endgültig auch aus der Exchange-Postfachdatenbank gelöscht wurde, führen Sie den folgenden Befehl aus.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" }

Wenn Sie das Postfach erfolgreich endgültig gelöscht haben, gibt der Befehl keine Ergebnisse zurück. Wenn das Postfach nicht endgültig gelöscht wurde, gibt der Befehl Informationen zum Postfach zurück.

