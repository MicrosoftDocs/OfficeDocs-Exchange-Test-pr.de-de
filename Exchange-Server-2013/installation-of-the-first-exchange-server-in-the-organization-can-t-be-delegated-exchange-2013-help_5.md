---
title: 'Install. des ersten Exchange-Servers in Organis. kann nicht delegiert werden'
TOCTitle: Die Installation des ersten Exchange-Servers in der Organisation kann nicht delegiert werden
ms:assetid: 0f4c5b2f-85ae-4160-9a53-f4b890d8ccdb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.delegatedfrontendtransportfirstinstall(v=EXCHG.150)
ms:contentKeyID: 50475016
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Die Installation des ersten Exchange-Servers in der Organisation kann nicht delegiert werden

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2014-11-05_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, da der angemeldete Benutzer keine Berechtigungen zur Installation des ersten Exchange 2013-Servers in der Organisation besitzt.

Wenngleich das Exchange 2013-Setup die Delegierung der Installation nachfolgender Serverrollen zulässt, erfordert das Setup, dass der angemeldete Benutzer Mitglied der Windows-Sicherheitsgruppe "Organisations-Admins" ist, wenn der erste Exchange 2013-Server in der Organisation installiert wird. Dies ist erforderlich, da das Exchange 2013-Setup Objekte im Exchange-Organisationscontainer in Active Directory während der Installation erstellt und konfiguriert.


> [!NOTE]
> Wenn Sie das Active Directory-Schema für Exchange 2013 nicht vorbereitet haben, muss der angemeldete Benutzer auch Mitglied der Windows-Sicherheitsgruppe "Schema-Admins" sein. Alternativ kann ein anderer Benutzer, der Mitglied der Windows-Gruppe "Schema-Admins" ist, das Active Directory-Schema vorbereiten, bevor Exchange 2013 installiert wird.



Um dieses Problem zu beheben, fügen Sie den angemeldeten Benutzer als Mitglied der Sicherheitsgruppe "Organisations-Admins" hinzu. Oder melden Sie sich bei einem Konto an, das Mitglied der Sicherheitsgruppe "Organisations-Admins" ist. Führen Sie das Exchange 2013-Setup anschließend erneut aus.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

