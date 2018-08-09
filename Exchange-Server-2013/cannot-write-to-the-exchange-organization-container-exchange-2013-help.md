---
title: 'Schreiben in Exchange-Organisationscontainer nicht mögl.: Exchange 2013-Hilfe'
TOCTitle: Schreiben in den Exchange-Organisationscontainer nicht möglich
ms:assetid: 17c4667b-7db1-4e0a-b824-1f6d51d980a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.globalserverinstall(v=EXCHG.150)
ms:contentKeyID: 50475093
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Schreiben in den Exchange-Organisationscontainer nicht möglich

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2014-11-05_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, da der angemeldete Benutzer nicht über die Kontoberechtigungen verfügt, die zum Schreiben in den Organisationscontainer im Active Directory-Verzeichnisdienst benötigt werden.

Setup erfordert, dass der während der Exchange 2013-Installation angemeldete Benutzer über Berechtigungen zum Erstellen und Ändern von Objekten in Active Directory verfügt. Wenn Sie Exchange 2013-Setup erstmalig in Ihrer Organisation ausführen, muss es sich bei dem verwendeten Konto um ein Mitglied der Gruppen "Schema-Admins" und "Organisations-Admins" handeln. Diese Berechtigungen sind erforderlich, da Active Directory bei der erstmaligen Ausführung des Setups für Exchange 2013 vorbereitet werden muss. Nachdem Active Directory vorbereitet wurde, muss es sich bei dem für die Installation zusätzlicher Exchange 2013-Server verwendete Konto um ein Mitglied der Verwaltungsrollengruppe "Organisationsverwaltung" handeln.

Zum Beheben dieses Problems gewähren Sie dem angemeldeten Benutzer die geeigneten Berechtigungen, oder Sie melden sich mit einem Konto an, das über diese Berechtigungen verfügt, und führen anschließend das Exchange 2013-Setup erneut aus.


> [!IMPORTANT]
> Eine gesamtstrukturübergreifende Installation von Exchange 2013 wird nicht unterstützt. Verwenden Sie ein Konto, das Mitglied der Active Directory-Gesamtstruktur ist, in der Sie Exchange 2013 installieren.



Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

