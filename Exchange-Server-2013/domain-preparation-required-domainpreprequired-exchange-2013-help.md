---
title: 'Domänenvorbereitung erforderlich_DomainPrepRequired: Exchange 2013 Help'
TOCTitle: Domänenvorbereitung erforderlich_DomainPrepRequired
ms:assetid: f6feae6f-7404-4b1f-887f-ed63c26a6bcd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.domainpreprequired(v=EXCHG.150)
ms:contentKeyID: 50477087
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Domänenvorbereitung erforderlich\_DomainPrepRequired

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Versuch, die Serverrolle zu installieren, ein Fehler aufgetreten ist.

Das Setup von Microsoft Exchange erfordert, dass die lokale Domäne für Exchange Server 2007 vorbereitet wird, bevor bestimmte Serverrollen installiert werden können.

Die Vorbereitung der Domäne für Exchange Server 2007 besteht aus den folgenden Aufgaben:

  - Festlegen der Berechtigungen für den Domänencontainer für die Servercomputer mit Exchange Server, die Exchange-Organisationsadministratoren, die authentifizierten Benutzer und die Exchange-Postfachadministratoren.

  - Erstellen des Microsoft Exchange-Systemobjektecontainers (wenn dieser nicht bereits vorhanden ist) und Festlegen der Berechtigungen für diesen Container für die Servercomputer mit Exchange Server, die Exchange-Organisationsadministratoren und die authentifizierten Benutzer.

  - Erstellen einer neuen globalen Domänengruppe namens Exchange Install Domain Servers in der aktuellen Domäne.

  - Hinzufügen der Gruppe Exchange Install Domain Servers zur universellen Sicherheitsgruppe Exchange-Server in der Stammdomäne.

Um dieses Problem zu beheben, führen Sie **setup /PrepareDomain** aus, um die Domäne vorzubereiten und dann einen erneuten Installationsversuch der Serverrolle durchzuführen.

Weitere Informationen zum Durchführen des PrepareDomain-Vorgangs finden Sie unter „Vorbereiten von Active Directory und Domänen“ ([https://go.microsoft.com/fwlink/?LinkId=78453](https://go.microsoft.com/fwlink/?linkid=78453)).

