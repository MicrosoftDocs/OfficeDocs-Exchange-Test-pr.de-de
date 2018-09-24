---
title: 'In Registrierung ist das Außerkraftsetzen des Domänencontrollers festgelegt'
TOCTitle: In der Registrierung ist das Außerkraftsetzen des Domänencontrollers festgelegt_ConfigDCHostNameMismatch
ms:assetid: 3aef5470-d510-4b59-a4b6-36d274a984ae
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.configdchostnamemismatch(v=EXCHG.150)
ms:contentKeyID: 50475340
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# In der Registrierung ist das Außerkraftsetzen des Domänencontrollers festgelegt\_ConfigDCHostNameMismatch

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-15_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, den angegebenen Domänencontroller zu verwenden, ein Fehler aufgetreten ist. In der Registrierung wurde ein Domänencontroller statisch zugewiesen.

Das Setup von Exchange 2007 erfordert, dass der im Setup-Befehl angegebene Domänencontroller dem Domänencontroller entspricht, der mithilfe einer Außerkraftsetzung in der Registrierung statisch zugewiesen wurde.

Um dieses Problem zu beheben, führen Sie Setup erneut aus und geben dabei den statisch zugewiesenen Domänencontroller für den Parameter **/DomainController: \<***FQDN of thestatically mapped domain controller***\>** an.

Weitere Informationen über DSAccess und die Erkennung von Verzeichnisdiensten finden Sie unter Microsoft Knowledge Base-Artikel 250570, "Directory Service Server Erkennung und DSAccess Usage" ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=250570](https://go.microsoft.com/fwlink/?linkid=3052&kbid=250570)).

