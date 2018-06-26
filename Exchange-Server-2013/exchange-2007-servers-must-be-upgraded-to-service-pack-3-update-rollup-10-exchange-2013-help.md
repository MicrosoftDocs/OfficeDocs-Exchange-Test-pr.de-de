---
title: 'Exchange 2007-Server müssen auf Service Pack 3 Updaterollup 10 aktualisiert werden: Exchange 2013 Help'
TOCTitle: Exchange 2007-Server müssen auf Service Pack 3 Updaterollup 10 aktualisiert werden
ms:assetid: b8028a00-c451-412e-86f2-1669f6eee8fc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.e15e12coexistenceminversionrequirement(v=EXCHG.150)
ms:contentKeyID: 50476548
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2007-Server müssen auf Service Pack 3 Updaterollup 10 aktualisiert werden

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, da mindestens ein Exchange Server 2007-Server noch nicht auf Service Pack 3 (SP3) Rollup 10 (RU10) für Exchange Server 2007 aktualisiert wurde. Voraussetzung für die Installation von Exchange 2013 ist, dass alle Exchange 2007-Server in Ihrer Organisation auf Exchange 2007 SP3 RU10 aktualisiert wurden. Diese Voraussetzung gilt auch für die Edge-Transport-Server von Exchange 2007. Weitere Informationen finden Sie unter [Aktualisieren von Exchange 2007 auf Exchange 2013](upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md).


> [!IMPORTANT]
> Nachdem Sie Ihre Exchange 2007-Edge-Transport-Server auf Exchange 2007 SP3 RU10 aktualisiert haben, müssen Sie das Edge-Abonnement zwischen Ihrer Exchange-Organisation und den einzelnen Edge-Transport-Servern erneut erstellen, damit deren Serverversion in Active Directory aktualisiert wird. Weitere Informationen zum erneuten Erstellen von Edge-Abonnements in Exchange 2007 finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=282699">Abonnieren der Exchange-Organisation durch den Edge-Transport-Server</A>.


