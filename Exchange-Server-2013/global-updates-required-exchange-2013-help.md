---
title: 'Globale Aktualisierungen erforderlich: Exchange 2013 Help'
TOCTitle: Globale Aktualisierungen erforderlich
ms:assetid: 0530f3c6-6fa6-456b-a33a-f3d2f7eaa2ef
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.globalupdaterequired(v=EXCHG.150)
ms:contentKeyID: 50474970
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Globale Aktualisierungen erforderlich

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2014-12-02_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, da der angemeldete Benutzer keine Berechtigungen zur Durchführung von globalen Änderungen an Active Directory besitzt.

Setup erfordert, dass der während der Exchange 2013-Installation angemeldete Benutzer über Berechtigungen zum Erstellen und Ändern von Objekten in Active Directory verfügt. Wenn Sie Exchange 2013-Setup erstmalig in Ihrer Organisation ausführen, muss es sich bei dem verwendeten Konto um ein Mitglied der Gruppen "Schema-Admins" und "Organisations-Admins" handeln. Diese Berechtigungen sind erforderlich, da Active Directory bei der erstmaligen Ausführung des Setups für Exchange 2013 vorbereitet werden muss. Nachdem Active Directory vorbereitet wurde, muss es sich bei dem für die Installation zusätzlicher Exchange 2013-Server verwendete Konto um ein Mitglied der Verwaltungsrollengruppe "Organisationsverwaltung" handeln.

Zum Beheben dieses Problems gewähren Sie dem angemeldeten Benutzer die geeigneten Berechtigungen, oder Sie melden sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen anschließend das Exchange 2013-Setup erneut aus.


> [!IMPORTANT]
> Eine gesamtstrukturübergreifende Installation von Exchange 2013 wird nicht unterstützt. Verwenden Sie ein Konto, das Mitglied der Active Directory-Gesamtstruktur ist, in der Sie Exchange 2013 installieren.



Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

