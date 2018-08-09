﻿---
title: 'Das aktuelle Konto nicht an keiner Active Directory-Domäne angemeldet'
TOCTitle: Das aktuelle Konto nicht an keiner Active Directory-Domäne angemeldet
ms:assetid: 0e229d10-605a-420f-bf8b-58a7fcb5b259
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.loggedontodomain(v=EXCHG.150)
ms:contentKeyID: 50475010
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Das aktuelle Konto nicht an keiner Active Directory-Domäne angemeldet

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2014-12-02_

Microsoft Exchange Server 2013 Setup kann nicht fortgesetzt werden, da festgestellt wurde, dass das aktuelle Konto an keiner Active Directory-Domäne angemeldet ist. Sie müssen sich an einem Active Directory-Konto anmelden, das über die notwendigen Berechtigungen für die Installation von Exchange Server 2013 verfügt.

Setup erfordert, dass der während der Exchange 2013-Installation angemeldete Benutzer über Berechtigungen zum Erstellen und Ändern von Objekten in Active Directory verfügt. Wenn Sie Exchange 2013-Setup erstmalig in Ihrer Organisation ausführen, muss es sich bei dem verwendeten Konto um ein Mitglied der Gruppen "Schema-Admins" und "Organisations-Admins" handeln. Diese Berechtigungen sind erforderlich, da Active Directory bei der erstmaligen Ausführung des Setups für Exchange 2013 vorbereitet werden muss. Nachdem Active Directory vorbereitet wurde, muss es sich bei dem für die Installation zusätzlicher Exchange 2013-Server verwendete Konto um ein Mitglied der Verwaltungsrollengruppe "Organisationsverwaltung" handeln.

Zum Beheben dieses Problems gewähren Sie dem angemeldeten Benutzer die geeigneten Berechtigungen, oder Sie melden sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen anschließend das Exchange 2013-Setup erneut aus.


> [!IMPORTANT]
> Eine gesamtstrukturübergreifende Installation von Exchange 2013 wird nicht unterstützt. Verwenden Sie ein Konto, das Mitglied der Active Directory-Gesamtstruktur ist, in der Sie Exchange 2013 installieren.



Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

