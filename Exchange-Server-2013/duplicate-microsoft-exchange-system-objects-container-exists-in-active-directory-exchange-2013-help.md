---
title: 'Container "Microsoft Exchange-Systemobjekte" ist in Active Directory doppelt vorhanden: Exchange 2013 Help'
TOCTitle: Container "Microsoft Exchange-Systemobjekte" ist in Active Directory doppelt vorhanden
ms:assetid: cd0f45ab-89de-4653-b50d-c1157c2329d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.adiniterrorrule(v=EXCHG.150)
ms:contentKeyID: 50476741
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Container \"Microsoft Exchange-Systemobjekte\" ist in Active Directory doppelt vorhanden

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2013-02-18_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, weil ein doppelter Container "Microsoft Exchange-Systemobjekte" im Domänennamenskontext von Active Directory gefunden wurde. Wenn ein doppelter Container "Microsoft Exchange-Systemobjekte" von Setup gefunden wird, müssen Sie den doppelten Container löschen, damit Setup fortgesetzt werden kann. Wenn ein Container "Microsoft Exchange-Systemobjekte" doppelt vorhanden ist, kann das Problem nicht dadurch behoben werden, dass Sie **DomainPrep** erneut ausführen. Sie müssen den doppelten Container "Microsoft Exchange-Systemobjekte" identifizieren und löschen.

Wenn Sie dieses Problem beheben möchten, führen Sie folgende Schritte aus:

1.  Melden Sie sich am Domänencontroller mit Administratorenrechten an.

2.  Klicken Sie in **Verwaltungstools** auf **Active Directory-Benutzer und -Computer**.

3.  Klicken Sie im Bereich der Verwaltungskonsole **Active Directory-Benutzer und -Computer** im Menü der Symbolleiste auf **Ansicht**, und wählen Sie **Erweiterte Features** aus.

4.  Suchen Sie den doppelten Container "Microsoft Exchange-Systemobjekte".

5.  Überprüfen Sie, ob der doppelte Container "Microsoft Exchange-Systemobjekte" keine gültigen Active Directory-Objekte enthält.

6.  Klicken Sie mit der rechten Maustaste auf den doppelten Container "Microsoft Exchange-Systemobjekte", und klicken Sie dann auf **Löschen**.

7.  Bestätigen Sie den Löschvorgang, indem Sie im Dialogfeld **Active Directory** auf **Ja** klicken.


> [!NOTE]
> Wenn diese Änderung sofort repliziert werden soll, müssen Sie die Replikation zwischen den Domänencontrollern manuell initiieren.



Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

