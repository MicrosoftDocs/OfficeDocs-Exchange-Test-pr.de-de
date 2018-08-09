---
title: 'Verwenden d. Exchange 2010 oder 2007 Edge-Transport-Servers in Exchange 2013'
TOCTitle: Verwenden eines Exchange 2010 oder 2007 Edge-Transport-Servers in Exchange 2013
ms:assetid: ce99b4bd-868c-4767-9009-e22c17ac0ac7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150569(v=EXCHG.150)
ms:contentKeyID: 50476747
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden eines Exchange 2010 oder 2007 Edge-Transport-Servers in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Edge-Transport-Server ist in Microsoft Exchange Server 2013 Service Pack 1 (SP1) verfügbar. Sie können jedoch weiterhin vorhandene Exchange Server 2007- oder Exchange Server 2010-Edge-Transport-Server verwenden, die Sie im Umkreisnetzwerk bereitgestellt haben. Alternativ können Sie einen neuen Exchange 2007- oder Exchange 2010-Edge-Transport-Server im Umkreisnetzwerk für eine neue oder aktualisierte Exchange 2013-Organisation installieren.

Folgendes müssen wissen:

  - Ein Exchange 2007- oder Exchange 2010-Edge-Transport-Server erfordert eine Verbindung mit einem Hub-Transport-Server. In Exchange 2013 befindet sich der Transportdienst auf dem Postfachserver. Daher verläuft der Internetnachrichtenfluss zwischen dem Transportdienst auf dem Postfachserver und dem Edge-Transport-Server. Der Exchange 2013-Clientzugriffsserver wird also umgangen.

  - Sie können einen Exchange 2007- oder Exchange 2010-Edge-Transport-Server für einen Active Directory-Standort abonnieren, der nur Exchange 2013-Server enthält. Sie können die Edge-Abonnementdatei importieren und EdgeSync auf einem eigenständigen Exchange 2013-Postfachserver oder auf einem Server ausführen, bei dem der Postfachserver und der Clientzugriffsserver auf einem Computer installiert sind. Auf einem eigenständigen Exchange 2013-Clientzugriffsserver ist es nicht möglich, die Edge-Abonnementdatei zu importieren oder EdgeSync auszuführen.

  - Die Verfahren zur Bereitstellung eines neuen Exchange 2007- oder Exchange 2010-Edge-Transport-Servers in der Exchange 2013-Organisation gleichen im Wesentlichen denen früherer Versionen von Exchange. Jedoch werden alle Verfahren, die auf dem Hub-Transport-Server ausgeführt werden, in Exchange 2013 auf dem Postfachserver ausgeführt. Folgende Verfahren sind erforderlich:
    
      - [Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server](https://go.microsoft.com/fwlink/p/?linkid=275859)
    
      - [Konfigurieren der Nachrichtenübermittlung zwischen einem Edge-Transport-Server und Hub-Transport-Servern, ohne EdgeSync zu verwenden](https://go.microsoft.com/fwlink/p/?linkid=276661)

