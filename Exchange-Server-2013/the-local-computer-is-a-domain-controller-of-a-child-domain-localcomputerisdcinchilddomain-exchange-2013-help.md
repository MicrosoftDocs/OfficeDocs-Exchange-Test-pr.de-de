---
title: 'Der lokale Computer ist ein Domänencontroller einer untergeordneten Domäne_LocalComputerIsDCInChildDomain: Exchange 2013 Help'
TOCTitle: Der lokale Computer ist ein Domänencontroller einer untergeordneten Domäne_LocalComputerIsDCInChildDomain
ms:assetid: 7db1dcc0-d953-41b8-b081-2a47a70950c4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.localcomputerisdcinchilddomain(v=EXCHG.150)
ms:contentKeyID: 50476111
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Der lokale Computer ist ein Domänencontroller einer untergeordneten Domäne\_LocalComputerIsDCInChildDomain

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da der lokale Computer ein Domänencontroller einer untergeordneten Domäne ist.

Das Exchange 2007-Setup kann nicht auf einem Domänencontroller einer untergeordneten Domäne ausgeführt werden, es sei denn, der Domänencontroller in ein globaler Katalogserver.

Um dieses Problem zu beheben, stufen Sie den Domänencontroller zu einem globalen Katalogserver herauf oder installieren Exchange 2007 auf einem Nicht-Domänencontroller, d. h. einem Mitgliedsserver, in der untergeordneten Domäne, und führen anschließend das Microsoft Exchange-Setup erneut aus.

So vermeiden Sie diese Warnung, indem Sie den Exchange-Server in einen globalen Katalogserver ändern

1.  Klicken Sie in dem Domänencontroller auf **Start**, zeigen Sie auf **Programme**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Active Directory-Standorte und -Dienste**.

2.  Doppelklicken Sie in der Konsolenstruktur auf **Standorte**, dann auf den Namen des Standorts und schließlich auf **Server**.

3.  Doppelklicken Sie auf den Zieldomänencontroller.

4.  Klicken Sie im Ergebnisbereich auf **NTDS-Einstellungen**, und wählen Sie **Eigenschaften** aus.

5.  Aktivieren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Globaler Katalogserver**.

6.  Starten Sie den Domänencontroller neu.

