---
title: 'Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory'
TOCTitle: Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory_ADUpdateRequired
ms:assetid: 1412d8a1-605a-4b1e-bee3-0c97f2cc9e65
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.adupdaterequired(v=EXCHG.150)
ms:contentKeyID: 50475056
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory\_ADUpdateRequired

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, die Domäne vorzubereiten, ein Fehler aufgetreten ist.

Das Setup von Exchange erfordert, dass der Active Directory-Verzeichnisdienst für Exchange Server 2007 geändert werden muss, bevor Domänen in Active Directory vorbereitet werden können.

Das Konto, das zum Ausführen des Befehls **setup /PrepareAD** verwendet wird, verfügt nicht über ausreichende Berechtigungen zum Ausführen dieses Befehls, obwohl es der Gruppe „Organisationsadministratoren\&quot; anzugehören scheint. Möglicherweise ist das Konto abgelaufen.

Um dieses Problem zu beheben, stellen Sie sicher, dass das angemeldete Benutzerkonto gültig ist und zur Gruppe „Organisationsadministratoren\&quot; gehört, oder melden Sie sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen Sie **setup /PrepareAD** dann erneut aus.

Weitere Informationen zum Ausführen des Prozesses PrepareAD, finden Sie unter "Wie zum Vorbereiten der Active Directory und Domänen" ([https://go.microsoft.com/fwlink/?LinkId=78453](https://go.microsoft.com/fwlink/?linkid=78453)).

Weitere Informationen zu Active Directory-Berechtigungen, die mit Microsoft Exchange erforderlich sind, finden Sie unter "Verwenden von Active Directory Berechtigungen in Exchange Server" ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

