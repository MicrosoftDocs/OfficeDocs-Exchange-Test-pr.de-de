---
title: 'Unzureichende Berechtigungen zum Entfernen aller Serverrollen_CannotUninstallDelegatedServer: Exchange 2013 Help'
TOCTitle: Unzureichende Berechtigungen zum Entfernen aller Serverrollen_CannotUninstallDelegatedServer
ms:assetid: 214ae6f3-15e7-4337-99e8-40f9547c8e0c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.cannotuninstalldelegatedserver(v=EXCHG.150)
ms:contentKeyID: 50475334
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Unzureichende Berechtigungen zum Entfernen aller Serverrollen\_CannotUninstallDelegatedServer

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, alle Serverrollen zu deinstallieren, ein Fehler aufgetreten ist.

Das Setup von Exchange 2007 erfordert, dass der Benutzer, der beim Deinstallieren aller Serverrollen angemeldet ist, ein Mitglied der Gruppe „Exchange-Organisationsadministratoren\&quot; oder der Gruppe „Organisationsadministratoren\&quot; ist.

Um dieses Problem zu beheben, gewähren Sie dem angemeldeten Benutzer Exchange-Organisationsadministrator-Berechtigungen bzw. fügen ihn der Gruppe „Organisationsadministratoren\&quot; hinzu, oder melden Sie sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen Sie das Exchange 2007-Setup dann erneut aus.

Weitere Informationen zu Active Directory-Berechtigungen, die mit Microsoft Exchange erforderlich sind finden Sie unter "Arbeiten mit Active Directory-Berechtigungen in Exchange Server" ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

