---
title: 'Anhalten der Aufbewahrungszeit für ein Postfach: Exchange 2013 Help'
TOCTitle: Anhalten der Aufbewahrungszeit für ein Postfach
ms:assetid: 2baac4a7-3402-4142-bfb3-1649a950e677
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335168(v=EXCHG.150)
ms:contentKeyID: 50475390
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anhalten der Aufbewahrungszeit für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-14_

Wenn Sie für ein Postfach die Aufbewahrungszeit anhalten, wird die Verarbeitung einer Aufbewahrungsrichtlinie oder einer Postfachrichtlinie für verwalteten Ordner für dieses Postfach angehalten. Das Anhalten der Aufbewahrungszeit ist für Situationen gedacht, bei denen ein Benutzer z. B. im Urlaub oder vorübergehend abwesend ist.

Während die Aufbewahrungszeit angehalten wird, können sich die Benutzer an ihrem Postfach anmelden und Elemente ändern oder löschen. Wenn Sie eine Postfachsuche ausführen, werden gelöschte Elemente, die die Beibehaltungsdauer für gelöschte Element überschritten haben, in Suchergebnissen nicht zurückgegeben. Wenn Sie sicherstellen möchten, dass von Benutzern geänderte oder gelöschte Elemente in Szenarien mit rechtlichen Aufbewahrungspflichten erhalten bleiben, müssen Sie für das Postfach die rechtliche Aufbewahrungspflicht festlegen. Weitere Informationen finden Sie unter [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md).

Sie können auch Kommentare zur Aufbewahrung für Postfächer hinzufügen, für die Sie das Anhalten der Aufbewahrungszeit festgelegt haben. Die Kommentare werden in unterstützten Versionen von Microsoft Outlook angezeigt.

Weitere Verwaltungsaufgaben im Zusammenhang mit der Messaging-Datensatzverwaltung (MRM) finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht dazu verwendet werden, die Aufbewahrungszeit für ein Postfach anzuhalten. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Anhalten der Aufbewahrungszeit für ein Postfach

In diesem Beispiel wird die Aufbewahrungszeit für das Postfach von Michael Allen angehalten.

    Set-Mailbox "Michael Allen" -RetentionHoldEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Verwenden der Shell zum Aufheben des Anhaltens der Aufbewahrungszeit für ein Postfach

In diesem Beispiel wird das Anhalten der Aufbewahrungszeit für das Postfach von Michael Allen aufgehoben.

    Set-Mailbox "Michael Allen" -RetentionHoldEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Verwenden Sie das Cmdlet [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)), um die Postfacheigenschaft *RetentionHoldEnabled* abzurufen und so zu überprüfen, ob die Aufbewahrungszeit für das Postfach angehalten wurde.

Dieser Befehl ruft die Eigenschaft *RetentionHoldEnabled* für Michael Allens Postfach ab.

    Get-Mailbox "Michael Allen" | Select RetentionHoldEnabled

Dieser Befehl ruft alle Postfächer in der Exchange-Organisation ab, filtert nach den Postfächern, deren Aufbewahrungszeit angehalten wurde, und führt sie zusammen mit der Aufbewahrungsrichtlinie auf, die auf jedes Postfach angewendet wird.


> [!IMPORTANT]
> Da <EM>RetentionHoldEnabled</EM> keine filterbare Eigenschaft in Exchange 2013 ist, können Sie den Parameter <EM>Filter</EM> nicht mit dem Cmdlet <STRONG>Get-Mailbox</STRONG> verwenden, um nach Postfächern zu filtern, für die die Aufbewahrungszeit serverseitig angehalten wurde. Dieser Befehl ruft eine Liste aller Postfächer und Filter auf dem Client ab, auf dem die Shell-Sitzung ausgeführt wird. In großen Umgebungen mit Tausenden von Postfächern kann es sehr lange dauern, bis der Befehl vollständig ausgeführt wurde.



    Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionHoldEnabled -eq $true} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto

