---
title: 'Dieser Server ist die Quelle für einen Sendeconnector'
TOCTitle: Dieser Server ist die Quelle für einen Sendeconnector_ServerIsSourceForSendConnector
ms:assetid: 151c0014-c90c-4c52-8e74-4b3f1bc7aaf1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.serverissourceforsendconnector(v=EXCHG.150)
ms:contentKeyID: 50475062
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Dieser Server ist die Quelle für einen Sendeconnector\_ServerIsSourceForSendConnector

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, die Hub-Transport-Serverrolle zu entfernen, ein Fehler aufgetreten ist. Der lokale Computer ist die Quelle für mindestens einen Sendeconnector in der Exchange-Organisation.

Der Sendeconnector stellt ein logisches Gateway dar, durch das ausgehende Nachrichten gesendet werden.

Das Setup von Exchange 2007 erfordert, dass alle Sendeconnectors für eine Exchange-Organisation vom Hub-Transport-Servercomputer verschoben oder entfernt wurden, bevor die Serverrolle gelöscht werden kann.

Um dieses Problem zu beheben, verschieben oder löschen Sie alle Sendeconnectors vom lokalen Computer und führen das Setup erneut aus.

Weitere Informationen zum Ändern oder Entfernen von Sendeconnectors finden Sie unter den folgenden Themen in der Exchange Server 2007-Produktdokumentation:

  - „Entfernen eines Sendeconnectors“ ([https://go.microsoft.com/fwlink/?LinkId=86655](https://go.microsoft.com/fwlink/?linkid=86655)).

  - „Ändern der Konfiguration eines Sendeconnectors“ ([https://go.microsoft.com/fwlink/?LinkId=86656](https://go.microsoft.com/fwlink/?linkid=86656)).

