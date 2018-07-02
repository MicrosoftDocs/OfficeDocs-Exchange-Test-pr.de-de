---
title: 'Keine Exchange 2010- oder Exchange 2007-Server erkannt: Exchange 2013 Help'
TOCTitle: Keine Exchange 2010- oder Exchange 2007-Server erkannt
ms:assetid: 789cabab-c769-4a16-a6c8-3db82cff8861
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.noe14serverwarning(v=EXCHG.150)
ms:contentKeyID: 50476047
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Keine Exchange 2010- oder Exchange 2007-Server erkannt

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-11-08_

Microsoft Exchange Server 2013-Setup zeigt diese Warnung an, da keine Exchange Server 2010- oder Exchange Server 2007-Serverrollen in der Organisation vorhanden sind.


> [!WARNING]
> Wenn Sie die Installation von Exchange Server&nbsp;2013 fortsetzen, werden Sie später nicht in der Lage sein, Exchange 2010- oder Exchange 2007-Server zur Organisation hinzuzufügen.



Berücksichtigen Sie vor der Bereitstellung von Exchange 2013 die folgenden Punkte, die es möglicherweise erforderlich machen, vor der Exchange 2013-Bereitstellung Exchange 2010- oder Exchange 2007-Server bereitzustellen:

  - **Drittanbieter- oder selbst entwickelte Anwendungen**   Anwendungen, die für frühere Versionen von Exchange entwickelt wurden, sind möglicherweise nicht mit Exchange 2013 kompatibel. Sie müssen zur Unterstützung dieser Anwendungen möglicherweise weiterhin Exchange 2010- oder Exchange 2007-Server bereitstellen.

  - **Koexistenz- oder Migrationsanforderungen**   Wenn Sie eine Migration der Postfächer in Ihrer Organisation planen, ist für einige Lösungen möglicherweise die Verwendung von Exchange 2010- oder Exchange 2007-Servern erforderlich.

Wenn Sie entscheiden, dass die Bereitstellung von Exchange 2010- oder Exchange 2007-Servern erforderlich ist, müssen Sie diese vor der Installation von Exchange 2013 bereitstellen. Active Directory muss für jede Exchange-Version in der folgenden Reihenfolge vorbereitet werden:

1.  Exchange 2007

2.  Exchange 2010

3.  Exchange 2013

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

