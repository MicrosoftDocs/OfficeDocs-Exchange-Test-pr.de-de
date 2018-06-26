---
title: 'Setup kann Exchange nicht auf einem schreibgeschützten Domänencontroller installieren_ComputerRODC: Exchange 2013 Help'
TOCTitle: Setup kann Exchange nicht auf einem schreibgeschützten Domänencontroller installieren_ComputerRODC
ms:assetid: 4934d755-65be-47e2-86b0-6ea1ab148a96
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.computerrodc(v=EXCHG.150)
ms:contentKeyID: 50475602
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Setup kann Exchange nicht auf einem schreibgeschützten Domänencontroller installieren\_ComputerRODC

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann die Installation nicht fortsetzen, weil der Zielcomputer ein schreibgeschützter Domänencontroller (Read-Only Domain Controller, RODC) ist.

Schreibgeschützte Domänencontroller sind ein Feature von Windows Server 2008 Active Directory. Der RODC ist eine der Domänencontroller-Installationsoptionen, die an Remotestandorten installiert werden kann, deren physikalische Sicherheit ggf. geringer ist.

Das Exchange-Setup erfordert Schreibzugriff auf dem Zielinstallationscomputer.

Um dieses Problem zu beheben, wählen Sie einen Zielinstallationscomputer aus, der nicht als RODC reserviert ist, und führen Sie Setup dann erneut aus.

