---
title: 'Die lokale Domäne muss aktualisiert werden_LocalDomainPrep: Exchange 2013 Help'
TOCTitle: Die lokale Domäne muss aktualisiert werden_LocalDomainPrep
ms:assetid: f33e6785-e85a-495e-a124-ebcb2b763e75
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.localdomainprep(v=EXCHG.150)
ms:contentKeyID: 50477067
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Die lokale Domäne muss aktualisiert werden\_LocalDomainPrep

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, weil der angemeldete Benutzer nicht über die Kontoberechtigungen verfügt, die für die Domänenvorbereitung erforderlich sind.

Das Setup von Exchange 2007 erfordert, dass der Benutzer, der beim Ausführen von **Setup /PrepareDomain** angemeldet ist, ein Mitglied der Gruppe Domänenadministratoren und Exchange-Organisationsadministratoren oder der Gruppe Organisationsadministratoren ist.

Um dieses Problem zu beheben, gewähren Sie dem angemeldeten Benutzer Domänenadministrator- und Exchange-Organisationsadministrator-Berechtigungen bzw. fügen ihn der Gruppe Organisationsadministratoren hinzu, oder melden Sie sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen Sie das Exchange 2007-Setup dann erneut aus.

Weitere Informationen zu den in Microsoft Exchange benötigten Active Directory-Berechtigungen finden Sie in „Arbeiten mit Active Directory-Berechtigungen in Exchange Server“ ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

