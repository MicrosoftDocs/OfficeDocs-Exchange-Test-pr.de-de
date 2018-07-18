---
title: 'Der OAB-Server wurde gelöscht_OffLineABServerDeleted: Exchange 2013 Help'
TOCTitle: Der OAB-Server wurde gelöscht_OffLineABServerDeleted
ms:assetid: 38b5dacf-ef65-4b25-97f6-d8dec956d7d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.offlineabserverdeleted(v=EXCHG.150)
ms:contentKeyID: 50475494
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Der OAB-Server wurde gelöscht\_OffLineABServerDeleted

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, die Clientzugriffs-Serverrolle zu installieren, ein Fehler aufgetreten ist. Der Exchange-Postfachserver, der für die Speicherung des Offlineadressbuchs (OAB) reserviert war, wurde gelöscht.

Für das Setup von Exchange 2007 ist ein gültiger Exchange-Postfachserver erforderlich, der als Host für die OAB-Generierung fungiert, damit die Installation der Clientzugriffs-Serverrolle fortgesetzt werden kann.

Um dieses Problem zu beheben, legen Sie einen gültigen Exchange-Postfachserver als OAB-Generierungshost fest, und führen Sie anschließend das Exchange 2007-Setup erneut aus.

Informationen dazu, wie Sie eine Exchange-Server den Host für die Generierung des Offlineadressbuchs zu bestimmen finden Sie unter "Wie zum Erstellen eines Offlineadressbuchs" ([https://go.microsoft.com/fwlink/?LinkId=86314](https://go.microsoft.com/fwlink/?linkid=86314)) in der Exchange 2007-Produktdokumentation.

