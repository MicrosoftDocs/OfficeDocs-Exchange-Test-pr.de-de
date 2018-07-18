---
title: 'Keine ausreichenden Berechtigungen zum Ausführen von „/PrepareDomain“_PrepareDomainNotAdmin: Exchange 2013 Help'
TOCTitle: Keine ausreichenden Berechtigungen zum Ausführen von „/PrepareDomain“_PrepareDomainNotAdmin
ms:assetid: c33a2bc0-5b07-49b8-a1c1-53baa4933d44
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.preparedomainnotadmin(v=EXCHG.150)
ms:contentKeyID: 50476646
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Keine ausreichenden Berechtigungen zum Ausführen von „/PrepareDomain“\_PrepareDomainNotAdmin

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, den Prozess **/PrepareDomain** auszuführen, ein Fehler aufgetreten ist. Der angemeldete Benutzer verfügt nicht über ausreichende Berechtigungen zum Ausführen des Prozesses **/PrepareDomain**.

Das Setup von Exchange 2007 erfordert, dass der Benutzer, der beim Ausführen von **/PrepareDomain** angemeldet ist, ein Mitglied der Gruppe Domänenadministratoren für die vorzubereitende Domäne und der Gruppe Exchange-Administratoren ist.

Um dieses Problem zu beheben, gewähren Sie dem angemeldeten Benutzer Domänenadministrator-Berechtigungen für die vorzubereitende Domäne und fügen ihn der Gruppe Exchange-Administratoren hinzu, oder melden Sie sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen Sie das Exchange 2007-Setup dann erneut aus.

Weitere Informationen zu den in Microsoft Exchange benötigten Active Directory-Berechtigungen finden Sie in „Arbeiten mit Active Directory-Berechtigungen in Exchange Server“ ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

