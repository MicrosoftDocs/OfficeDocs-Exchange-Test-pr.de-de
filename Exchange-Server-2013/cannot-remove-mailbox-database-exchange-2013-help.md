---
title: 'Entfernen einer Postfachdatenbank nicht möglich: Exchange 2013 Help'
TOCTitle: Entfernen einer Postfachdatenbank nicht möglich
ms:assetid: 5881e4c0-c2e2-48db-84b4-7f9ce3cf46a7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.unwillingtoremovemailboxdatabase(v=EXCHG.150)
ms:contentKeyID: 50475740
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Postfachdatenbank nicht möglich

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-11-08_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, weil eine Benutzerpostfachdatenbank nicht ohne einen möglichen Datenverlust vom lokalen Server entfernt werden kann.

Das Exchange 2013-Setup prüft, ob alle Postfachdatenbanken vom Server entfernt wurden, bevor die Postfachserverrolle entfernt wird. Benutzerpostfächer sind jedoch ggf. weiterhin auf dem Server vorhanden.

Verschieben Sie zur Beseitigung des Problems alle auf dem Server vorhandenen Postfächer auf einen anderen Exchange-Server, oder deaktivieren Sie die Postfächer, wenn die Postfächer und die darin enthaltenen Daten nicht länger benötigt werden. Führen Sie das Exchange 2013-Setup anschließend erneut aus.

  - Weitere Informationen zum Identifizieren eines Postfachs in der Datenbank finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

  - Weitere Informationen zum Verschieben eines Postfachs finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

  - Weitere Informationen zum Deaktivieren eines Postfachs finden Sie unter [Disable-Mailbox](https://technet.microsoft.com/de-de/library/aa997210\(v=exchg.150\)).

  - Weitere Informationen zum Entfernen einer Postfachdatenbank finden Sie unter [Verwalten von Postfachdatenbanken in Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

