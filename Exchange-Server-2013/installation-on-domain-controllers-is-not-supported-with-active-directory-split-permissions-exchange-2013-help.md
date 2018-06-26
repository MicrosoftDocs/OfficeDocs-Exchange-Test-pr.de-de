---
title: 'Installation auf Domänencontrollern mit geteilten Active Directory-Berechtigungen wird nicht unterstützt: Exchange 2013 Help'
TOCTitle: Installation auf Domänencontrollern mit geteilten Active Directory-Berechtigungen wird nicht unterstützt
ms:assetid: 977e3758-5e09-40a2-80c1-fe344b1d8a2a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.installondcinadsplitpermissionmode(v=EXCHG.150)
ms:contentKeyID: 50476273
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installation auf Domänencontrollern mit geteilten Active Directory-Berechtigungen wird nicht unterstützt

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-11-12_

Microsoft Exchange Server 2013-Setup hat ermittelt, dass Sie Setup auf einem Active Directory-Domänencontroller ausführen und eine der folgenden Bedingungen erfüllt ist:

  - Die Exchange-Organisation ist bereits für geteilte Active Directory-Berechtigungen konfiguriert.

  - Sie haben die Option für geteilte Active Directory-Berechtigungen im Exchange 2013-Setup ausgewählt.

Die Installation von Exchange 2013 auf Domänencontrollern wird nicht unterstützt, wenn die Exchange-Organisation für geteilte Active Directory-Berechtigungen konfiguriert ist.

Wenn Sie Exchange 2013 auf einem Domänencontroller installieren möchten, müssen Sie die Exchange-Organisation für geteilte RBAC-Berechtigungen (Role Based Access Control, rollenbasierte Zugriffssteuerung) oder gemeinsame Berechtigungen konfigurieren.


> [!IMPORTANT]
> Es wird nicht empfohlen, Exchange 2013 auf Active Directory-Domänencontrollern zu installieren. Weitere Informationen finden Sie unter <A href="installing-exchange-on-a-domain-controller-is-not-recommended-exchange-2013-help.md">Die Installation von Exchange auf einem Domänencontroller wird nicht empfohlen</A>.



Wenn Sie weiterhin geteilte Active Directory-Berechtigungen verwenden möchten, müssen Sie Exchange 2013 auf einem Mitgliedsserver installieren.

Weitere Informationen zu geteilten und gemeinsamen Berechtigungen in Exchange 2013 finden Sie in den folgenden Themen:

[Grundlegendes zu geteilten Berechtigungen](understanding-split-permissions-exchange-2013-help.md)

[Konfigurieren von Exchange 2013 für geteilte Berechtigungen](configure-exchange-2013-for-split-permissions-exchange-2013-help.md)

[Konfigurieren von Exchange 2013 für gemeinsame Berechtigungen](configure-exchange-2013-for-shared-permissions-exchange-2013-help.md)

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

