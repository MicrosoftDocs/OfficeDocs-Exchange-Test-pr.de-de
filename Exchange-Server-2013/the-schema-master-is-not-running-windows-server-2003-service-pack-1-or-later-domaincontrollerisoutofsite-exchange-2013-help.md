---
title: 'Auf dem Schemamaster wird nicht Windows Server 2003 Service Pack 1 oder höher ausgeführt_DomainControllerIsOutOfSite: Exchange 2013 Help'
TOCTitle: Auf dem Schemamaster wird nicht Windows Server 2003 Service Pack 1 oder höher ausgeführt_DomainControllerIsOutOfSite
ms:assetid: 5edbe0b8-7610-4a52-aaaa-38c6a99e7e53
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.domaincontrollerisoutofsite(v=EXCHG.150)
ms:contentKeyID: 50475791
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Auf dem Schemamaster wird nicht Windows Server 2003 Service Pack 1 oder höher ausgeführt\_DomainControllerIsOutOfSite

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil auf dem Domänencontroller, dem die Schemamasterrolle (auch Flexible Single Master Operations/FSMO genannt) des Active Directory-Verzeichnisdiensts zugewiesen ist, nicht Microsoft Windows Server 2003 Service Pack 1 (SP1) oder höher ausgeführt wird.

Für das Exchange 2007-Setup ist erforderlich, dass auf dem Domänencontroller, der als Schema-FSMO dient, Windows Server 2003 SP1 oder höher ausgeführt wird.

Der FSMO steuert alle Updates und Änderungen des Active Directory-Schemas.

Um dieses Problem zu beheben, führen Sie einen oder mehrere der folgenden Schritte aus:

  - Aktualisieren Sie den FSMO-Domänencontroller auf Windows Server 2003 SP1 oder höher und führen das Microsoft Exchange-Setup dann erneut aus.

  - Wenn ein FSMO-Domänencontroller vorhanden ist, der Microsoft Windows Server 2003 Service Pack 1 (SP1) oder eine höhere Version in der Exchange-Organisation ausführt, führen Sie das Exchange 2007-Setup so aus, dass der Parameter „/domaincontroller“ auf diesen FSMO-Domänencontroller verweist:
    
    \[*/DomainController* oder */dc\<FQDN of domain controller\>*\]
    
    Verwenden Sie den Parameter */DomainController*, um den Domänencontroller anzugeben, der für das Lesen aus und Schreiben in Active Directory während der Installation verwendet werden soll. Sie können das NetBIOS-Format oder den vollqualifizierten Domänennamen verwenden.

Das neueste Service Pack für Windows Server 2003 Server finden Sie im Windows Server TechCenter ([https://go.microsoft.com/fwlink/?LinkId=45315](https://go.microsoft.com/fwlink/?linkid=45315)).

Weitere Informationen zu den Installationsparametern von Exchange Server 2007 finden Sie unter "Installieren von Exchange 2007 im unbeaufsichtigten Modus" ([https://go.microsoft.com/fwlink/?LinkId=86476](https://go.microsoft.com/fwlink/?linkid=86476)) in der Exchange Server 2007-Produktdokumentation.

