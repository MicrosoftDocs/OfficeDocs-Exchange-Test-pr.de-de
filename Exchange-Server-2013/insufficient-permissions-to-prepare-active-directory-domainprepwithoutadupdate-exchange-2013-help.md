---
title: 'Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory'
TOCTitle: Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory_DomainPrepWithoutADUpdate
ms:assetid: 4283c4b9-983f-460e-a5de-42b2772eae0d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.domainprepwithoutadupdate(v=EXCHG.150)
ms:contentKeyID: 50475487
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nicht ausreichende Berechtigungen zum Vorbereiten von Active Directory\_DomainPrepWithoutADUpdate

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, die Domäne vorzubereiten, ein Fehler aufgetreten ist.

Das Setup von Exchange erfordert, dass der Active Directory-Verzeichnisdienst für Exchange Server 2007 geändert werden muss, bevor Domänen in Active Directory vorbereitet werden können.

Das Konto, das zum Ausführen des Befehls **setup /PrepareAD** verwendet wird, verfügt nicht über ausreichende Berechtigungen zum Ausführen dieses Befehls, obwohl es der Gruppe „Organisationsadministratoren“ anzugehören scheint. Möglicherweise ist das Konto abgelaufen.

Um dieses Problem zu beheben, stellen Sie sicher, dass das angemeldete Benutzerkonto gültig ist und zur Gruppe „Organisationsadministratoren“ gehört, oder melden Sie sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen Sie **setup /PrepareAD** dann erneut aus.

Weitere Informationen zum Durchführen des PrepareAD-Vorgangs finden Sie unter „Vorbereiten von Active Directory und Domänen“ ([https://go.microsoft.com/fwlink/?LinkId=78453](https://go.microsoft.com/fwlink/?linkid=78453)).

Weitere Informationen zu den in Microsoft Exchange benötigten Active Directory-Berechtigungen finden Sie in „Arbeiten mit Active Directory-Berechtigungen in Exchange Server“ ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

