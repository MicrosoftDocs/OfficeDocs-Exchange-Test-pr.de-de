---
title: "\"Host\"-Eintrag für den lokalen Computer nicht in der DNS-Datenbank gefunden: Exchange 2013 Help"
TOCTitle: "\"Host\"-Eintrag für den lokalen Computer nicht in der DNS-Datenbank gefunden"
ms:assetid: 2f18cb65-29fe-4b72-8d68-52fd503d5673
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.hostrecordmissing(v=EXCHG.150)
ms:contentKeyID: 50475408
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# \"Host\"-Eintrag für den lokalen Computer nicht in der DNS-Datenbank gefunden

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Das Setup von Microsoft Exchange Server 2013 kann nicht fortgesetzt werden, da der "Host (A)"-Eintrag für diesen Computer nicht in der DNS-Datenbank (Domain Name System) gefunden wurde.

Für das Exchange 2013-Setup ist erforderlich, dass der lokale Computer über einen gültigen "HOST (A)"-Eintrag verfügt, der bei der autorisierenden DNS-Datenbank der Domäne registriert ist.

Exchange benötigt DNS-Einträge vom Typ "Host (A)" zum Auflösen der IP-Adresse des nächsten internen oder externen Zielservers.

So beheben Sie dieses Problem

  - Vergewissern Sie sich, dass die lokale TCP/IP-Konfiguration auf den ordnungsgemäßen DNS-Server zeigt. Weitere Informationen finden Sie unter [Konfigurieren von TCP/IP-Einstellungen](https://go.microsoft.com/fwlink/p/?linkid=108281).

  - Verwenden Sie, um zu überprüfen, ob der Eintrag "Host (A)" auf dem DNS-Server vorhanden ist. Weitere Informationen finden Sie unter [So überprüfen Sie, ob A-Ressourceneinträge in DNS vorhanden sind](https://go.microsoft.com/fwlink/?linkid=63001).

Weitere Informationen zu DNS-Namensauflösung, -Problembehandlung und -"Host (A)"-Einträgen finden Sie in den folgenden Quellen:

  - [Problembehandlung bei DNS](https://go.microsoft.com/fwlink/p/?linkid=294828)

  - [Verwalten von Ressourceneinträgen](https://go.microsoft.com/fwlink/p/?linkid=294829)

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

