---
title: 'Die Installation von Exchange auf einem Domänencontroller wird nicht empfohlen: Exchange 2013 Help'
TOCTitle: Die Installation von Exchange auf einem Domänencontroller wird nicht empfohlen
ms:assetid: 48922de2-a68c-4092-96a5-d38c8e5f49f5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.warninginstallexchangerolesondomaincontroller(v=EXCHG.150)
ms:contentKeyID: 50475541
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Die Installation von Exchange auf einem Domänencontroller wird nicht empfohlen

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2013-03-22_

Microsoft Exchange Server 2013-Setup hat ermittelt, dass es sich bei dem Computer, auf dem Exchange 2013 installiert werden soll, um einen Active Directory-Domänencontroller handelt. Die Installation von Exchange 2013 auf einem Domänencontroller wird nicht empfohlen.

Wenn Sie Exchange 2013 auf einem Domänencontroller installieren, müssen Sie sich der folgenden Einschränkungen bewusst sein:

  - Die Konfiguration von Exchange 2013 für geteilte Active Directory-Berechtigungen wird nicht unterstützt.

  - Die universelle Exchange-Sicherheitsgruppe "Vertrauenswürdiges Subsystem" wird der Gruppe "Domänen-Admins" hinzugefügt, wenn Exchange auf einem Domänencontroller installiert wird. Auf diese Weise erhalten alle Exchange-Server in der Domäne Domänenadministratorrechte in dieser Domäne.

  - Sowohl Exchange Server als auch Active Directory sind ressourcenintensive Anwendungen. Wenn beide Anwendungen auf demselben Computer ausgeführt werden, müssen Sie möglicherweise mit Leistungsminderungen rechnen.

  - Sie müssen sicherstellen, dass es sich bei dem Domänencontroller, auf dem Exchange 2013 installiert wird, um einen globalen Katalogserver handelt.

  - Die Exchange-Dienste werden möglicherweise nicht ordnungsgemäß gestartet, wenn der Domänencontroller gleichzeitig als globaler Katalogserver konfiguriert ist.

  - Das Herunterfahren des Systems dauert erheblich länger, wenn die Exchange Server-Dienste nicht vor dem Herunterfahren oder Neustarten des Servers beendet werden.

  - Das Herabstufen eines Domänencontrollers auf einen Mitgliedsserver wird nicht unterstützt.

  - Das Ausführen von Exchange 2013 auf einem geclusterten Knoten, der auch als Active Directory-Domänencontroller fungiert, wird nicht unterstützt.

Es wird empfohlen, Exchange 2013 auf einem Mitgliedsserver zu installieren.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

