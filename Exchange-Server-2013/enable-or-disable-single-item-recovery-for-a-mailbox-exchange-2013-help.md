---
title: 'Aktiv. o. Deaktiv. d. Wiederherst. v. Elem. f. Postf.: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren der Wiederherstellung einzelner Elemente für ein Postfach
ms:assetid: 2e7f1bcd-8395-45ad-86ce-22868bd46af0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633460(v=EXCHG.150)
ms:contentKeyID: 54651500
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der Wiederherstellung einzelner Elemente für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-13_

Mithilfe der Shell können Sie die Wiederherstellung einzelner Elemente für ein Postfach aktivieren oder deaktivieren. In Exchange Online ist die Wiederherstellung einzelner Elemente standardmäßig aktiviert, wenn ein neues Postfach erstellt wird. Standardmäßig ist die Wiederherstellung einzelner Elemente in Exchange 2013 bei der Erstellung eines Postfachs deaktiviert. Ist die Wiederherstellung einzelner Elemente aktiviert, werden vom Benutzer dauerhaft gelöschte Nachrichten im Ordner „Wiederherstellbare Elemente“ des Postfachs beibehalten, bis die Aufbewahrungszeit für gelöschte Elemente abgelaufen ist. Dadurch kann ein Administrator durch den Benutzer gelöschte Nachrichten wiederherstellen, bevor deren Aufbewahrungszeit für gelöschte Elemente abläuft. Zudem werden Kopien des ursprünglichen Elements, wenn die Wiederherstellung einzelner Elemente aktiviert ist, beibehalten, sofern die Nachricht durch einen Benutzer oder Prozess geändert wird.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Aufbewahrung und Aufbewahrungspflicht" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Wiederherstellung einzelner Elemente kann in Exchange Admin Center (EAC) nicht aktiviert oder deaktiviert werden.

  - In Exchange Online beträgt der Aufbewahrungszeitraum standardmäßig 14 Tage. Für diese Einstellung können Sie maximal 30 Tage festlegen. Weitere Informationen finden Sie unter [Ändern des Aufbewahrungszeitraums für gelöschte Elemente für ein Exchange Online-Postfach](https://technet.microsoft.com/de-de/library/dn163584\(v=exchg.150\))

  - In Exchange 2013 verwendet das Postfach standardmäßig die Einstellungen für die Aufbewahrung gelöschter Elemente der Postfachdatenbank. Für gelöschte Elemente ist ein Aufbewahrungszeitraum von 14 Tagen festgelegt. Den Standardwert können Sie jedoch mit der Konfiguration dieser Einstellung auf Postfachbasis überschreiben. Weitere Informationen finden Sie unter [Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente](configure-deleted-item-retention-and-recoverable-items-quotas-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)..

## Verwenden der Shell zum Aktivieren der Wiederherstellung einzelner Elemente

In diesem Beispiel wird die Wiederherstellung einzelner Elemente für das Postfach von April Summers aktiviert.

    Set-Mailbox -Identity "April Summers" -SingleItemRecoveryEnabled $true

In diesem Beispiel wird die Wiederherstellung einzelner Elemente für das Postfach von Pilar Pinilla aktiviert und die Aufbewahrungsfrist für gelöschte Elemente auf 30 Tage festgelegt.

    Set-Mailbox -Identity "Pilar Pinilla" -SingleItemRecoveryEnabled $true -RetainDeletedItemsFor 30

In diesem Beispiel wird die Wiederherstellung einzelner Elemente für alle Benutzerpostfächer in der Organisation aktiviert.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -SingleItemRecoveryEnabled $true

In diesem Beispiel wird die Wiederherstellung einzelner Elemente für alle Benutzerpostfächer in der Organisation aktiviert, und die Aufbewahrungsfrist für gelöschte Elemente wird auf 30 Tage festgelegt.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -SingleItemRecoveryEnabled $true -RetainDeletedItemsFor 30

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Verwenden der Shell zum Deaktivieren der Wiederherstellung einzelner Elemente

Sie müssen die Wiederherstellung einzelner Elemente für das Postfach eines Benutzers möglicherweise deaktivieren. Beispielsweise müssen Sie die Wiederherstellung einzelner Elemente deaktivieren, bevor Sie **Search-Mailbox –DeleteContent** zum dauerhaften Löschen von Inhalten aus einem Postfach verwenden können. Weitere Informationen finden Sie unter [Suchen nach und Löschen von Nachrichten – Administratorhilfe](search-for-and-delete-messages-admin-help-exchange-2013-help.md).

In diesem Beispiel wird die Wiederherstellung einzelner Elemente für das Postfach von Ayla Kol deaktiviert.

    Set-Mailbox -Identity "Ayla Kol" -SingleItemRecoveryEnabled $false

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie zur Überprüfung der Aktivierung der Wiederherstellung einzelner Elemente und zur Anzeige des Werts für die Länge der Aufbewahrungsfrist (in Tagen) folgenden Befehl aus.

    Get-Mailbox <Name> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor

Sie können denselben Befehl verwenden, um sicherzustellen, dass die Wiederherstellung einzelner Elemente für ein Postfach deaktiviert ist.

## Weitere Informationen

  - Weitere Informationen zur Wiederherstellung einzelner Elemente finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md). Informationen zur Wiederherstellung von vom Benutzer gelöschten Nachrichten vor Ablauf der Aufbewahrungsfrist finden Sie unter [Wiederherstellen von gelöschten Nachrichten im Postfach eines Benutzers](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages).

  - Wenn ein Postfach in einem In-Situ-Speicher oder Beweissicherungsverfahren platziert wird, werden Nachrichten im Ordner „Wiederherstellbare Elemente“ beibehalten, bis die Aufbewahrungsdauer abläuft. Wenn die Aufbewahrungsdauer unbegrenzt ist, werden die Elemente beibehalten, bis der Haltebereich entfernt oder die Aufbewahrungsdauer geändert wird.

