---
title: 'Wiederherstellen eines vorläufig gelöschten Postfachs: Exchange 2013 Help'
TOCTitle: Wiederherstellen eines vorläufig gelöschten Postfachs
ms:assetid: 4f3f5ce4-9d12-4ed8-9f70-d8a6aa8a1b2e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863435(v=EXCHG.150)
ms:contentKeyID: 50554823
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederherstellen eines vorläufig gelöschten Postfachs

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-11-29_

Verwenden Sie die Shell, um ein vorläufig gelöschtes Postfach mit einem Active Directory-Benutzerkonto zu verbinden. Ein Postfach wird aus der Quellpostfachdatenbank *vorläufig gelöscht*, wenn es in eine andere Postfachdatenbank verschoben wird. Exchange löscht das Postfach nach Abschluss des Vorgangs nicht vollständig aus der Quell-Postfachdatenbank. Stattdessen wird das Postfach der Quellpostfachdatenbank in einen Zustand vorläufiger Löschung versetzt. So können Sie das Quellpostfach wiederherstellen, falls während der Verschiebung ein Fehler oder eine Beschädigung des Postfachs in der Zieldatenbank auftritt. In diesem Fall können Sie das Quellpostfach wiederherstellen und die Verschiebung wiederholen.

Ein vorläufig gelöschtes Postfach wird in der Quelldatenbank aufbewahrt, bis der Aufbewahrungszeitraum für gelöschte Postfächer abgelaufen ist oder das vorläufige gelöschte Postfach mit dem Cmdlet **Remove-StoreMailbox** endgültig gelöscht wird. Bis ein vorläufig gelöschtes Postfach endgültig aus der Exchange-Postfachdatenbank gelöscht wird, können Sie die Shell verwenden, um die Inhalte des vorläufig gelöschten Postfachs in einem vorhandenen Postfach oder einem Archivpostfach wiederherzustellen.

Weitere Informationen zu vorläufig gelöschten Postfächern und zum Ausführen weiterer Verwaltungsaufgaben in diesem Zusammenhang finden Sie in den folgenden Themen:

  - [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md)

  - [Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

  - [Verwalten von Postfachwiederherstellungsanforderungen](manage-mailbox-restore-requests-exchange-2013-help.md)

  - [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Verfahren in diesem Thema können nur in der Shell ausgeführt werden. Die Exchange-Verwaltungskonsole kann nicht zum Wiederherstellen vorläufig gelöschter Postfächer verwendet werden.

  - Führen Sie den folgenden Befehl aus, um sicherzustellen, dass das vorläufig gelöschte Postfach, das Sie mit einem Benutzerkonto verbinden möchten, noch in der Postfachdatenbank vorhanden ist und es sich nicht um ein deaktiviertes Postfach handelt.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,DisconnectReason,DisconnectDate
    
    Das vorläufig gelöschte Postfach muss sich in der Postfachdatenbank befinden, und der Wert der Eigenschaft *DisconnectReason* muss `SoftDeleted` lauten. Falls das Postfach endgültig aus der Datenbank gelöscht wurde, werden nach Ausführen des Befehls keine Ergebnisse zurückgegeben.
    
    Alternativ können Sie zum Anzeigen aller vorläufig gelöschten Postfächer in Ihrer Organisation den folgenden Befehl ausführen.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisconnectReason -eq "SoftDeleted" } | fl DisplayName,DisconnectReason,DisconnectDate

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)..

## Wiederherstellen eines vorläufig gelöschten Postfachs mithilfe der Shell

Sie können die Shell verwenden, um ein vorläufig gelöschtes Postfach in einem vorhandenen Postfach mithilfe des Cmdlets **New-MailboxRestoreRequest** wiederherzustellen. Wenn Sie ein vorläufig gelöschtes Postfach wiederherstellen, werden dessen Inhalte in ein vorhandenes Postfach – das *Zielpostfach* – kopiert. Nachdem eine Postfachwiederherstellungsanforderung erfolgreich abgeschlossen wurde, wird die Anforderung standardmäßig für 30 Tage aufbewahrt, ehe sie entfernt wird. Sie können sie vorher mithilfe des Cmdlets **Remove-MailboxRestoreRequest** entfernen.

Nach der Wiederherstellung eines vorläufig gelöschten Postfachs wird das Postfach in der Postfachdatenbank bis zu seiner endgültigen Löschung durch einen Administrator bzw. bis zum Ablauf des Aufbewahrungszeitraums aufbewahrt.

Zum Erstellen einer Postfachwiederherstellungsanforderung müssen Sie den Anzeigenamen, die Postfach-GUID oder den Legacy-DN (Distinguished Name) des vorläufig gelöschten Postfachs verwenden. Verwenden Sie das Cmdlet **Get-MailboxStatistics**, um die Werte der Eigenschaften **DisplayName**, **MailboxGuid**- und **LegacyDN** für das vorläufig gelöschte Postfach anzuzeigen, das Sie wiederherstellen möchten. Führen Sie beispielsweise den folgenden Befehl aus, um diese Informationen für alle deaktivierten und vorläufig gelöschten Postfächer in Ihrer Organisation zurückzugeben.

    Get-MailboxDatabase | Get-MailboxStatistics | Where {$_.DisconnectReason -eq "SoftDeleted"} | fl DisplayName,MailboxGuid,LegacyDN,Database

In diesem Beispiel wird ein vorläufig gelöschtes Postfach im Zielpostfach "Debra Garcia" wiederhergestellt, das anhand des Anzeigenamens im Parameter *SourceStoreMailbox* identifiziert wird und sich in der Postfachdatenbank "MBXDB01" befindet. Der Parameter *AllowLegacyDNMismatch* wird verwendet, damit das Quellpostfach in einem Postfach wiederhergestellt werden kann, das nicht denselben Legacy-DN-Wert aufweist wie das vorläufig gelöschte Postfach.

    New-MailboxRestoreRequest -SourceStoreMailbox "Debra Garcia" -SourceDatabase MBXDB01 -TargetMailbox "Debra Garcia" -AllowLegacyDNMismatch

In diesem Beispiel wird das vorläufig gelöschte Postfach von Pilar Pinilla, das anhand der Postfach-GUID identifiziert wurde, in ihrem aktuellen Archivpostfach wiederhergestellt. Der Parameter *AllowLegacyDNMismatch* ist nicht erforderlich, da ein primäres Postfach und das zugehörige Archivpostfach denselben Legacy-DN aufweisen.

    New-MailboxRestoreRequest -SourceStoreMailbox dc35895a-a628-4bba-9aa9-650f5cdb9ae7 -SourceDatabase MBXDB02 -TargetMailbox pilarp@contoso.com -TargetIsArchive

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie ein vorläufig gelöschtes Postfach erfolgreich im Zielpostfach wiederhergestellt haben, führen Sie das Cmdlet **Get-MailboxRestoreRequest** oder **Get-MailboxRestoreRequestStatistics** aus, um Informationen zur Wiederherstellungsanforderung anzuzeigen. Wenn die Wiederherstellungsanforderung erfolgreich erstellt wurde, weist die Eigenschaft *Status* entweder den Wert **Queued**, **InProgress** oder **Completed** auf. Nach Abschluss der Wiederherstellungsanforderung befindet sich der Inhalt des vorläufig gelöschten Postfachs im Zielpostfach.

Weitere Informationen finden Sie unter:

  - [Verwalten von Postfachwiederherstellungsanforderungen](manage-mailbox-restore-requests-exchange-2013-help.md)

  - [Get-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829907\(v=exchg.150\))

  - [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/de-de/library/ff829912\(v=exchg.150\))

