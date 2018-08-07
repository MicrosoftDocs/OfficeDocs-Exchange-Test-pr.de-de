---
title: 'Auf Schemamaster wird nicht Windows Server 2003 SP1 oder höher ausgeführt'
TOCTitle: Auf dem Schemamaster wird nicht Windows Server 2003 Service Pack 1 oder höher ausgeführt_SchemaFSMONotWin2003SPn
ms:assetid: 644a85ca-7b36-4ed0-bd21-c64f2742df70
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.schemafsmonotwin2003spn(v=EXCHG.150)
ms:contentKeyID: 50475840
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Auf dem Schemamaster wird nicht Windows Server 2003 Service Pack 1 oder höher ausgeführt\_SchemaFSMONotWin2003SPn

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil auf dem Domänencontroller, dem die Schemamasterrolle (auch Flexible Single Master Operations/FSMO genannt) des Active Directory-Verzeichnisdiensts zugewiesen ist, nicht Microsoft Windows Server 2003 Service Pack 1 (SP1) oder höher ausgeführt wird.

Für das Exchange 2007-Setup ist erforderlich, dass auf dem Domänencontroller, der als Schema-FSMO dient, Windows Server 2003 SP1 oder höher ausgeführt wird.

Der FSMO steuert alle Updates und Änderungen des Active Directory-Schemas.

Um dieses Problem zu beheben, führen Sie einen oder mehrere der folgenden Schritte aus:

  - Aktualisieren Sie den FSMO-Domänencontroller auf Windows Server 2003 SP1 oder höher und führen das Microsoft Exchange-Setup dann erneut aus.

  - Wenn ein FSMO-Domänencontroller vorhanden ist, der Microsoft Windows Server 2003 Service Pack 1 (SP1) oder eine höhere Version in der Exchange-Organisation ausführt, führen Sie das Exchange 2007-Setup so aus, dass der Parameter „/domaincontroller\&quot; auf diesen FSMO-Domänencontroller verweist:
    
    \[*/DomainController* oder */dc\<FQDN of domain controller\>*\]
    
    Verwenden Sie den Parameter */DomainController*, um den Domänencontroller anzugeben, der für das Lesen aus und Schreiben in Active Directory während der Installation verwendet werden soll. Sie können das NetBIOS-Format oder den vollqualifizierten Domänennamen verwenden.

Das neueste Servicepack für Windows Server 2003 finden Sie unter "Windows Server TechCenter" ([https://go.microsoft.com/fwlink/?LinkId=45315](https://go.microsoft.com/fwlink/?linkid=45315)).

Weitere Informationen zu Exchange Server 2007-Setup Parametern finden Sie unter "Wie zum Installieren von Exchange 2007 im unbeaufsichtigten Modus" ([https://go.microsoft.com/fwlink/?LinkId=86476](https://go.microsoft.com/fwlink/?linkid=86476)) in der Exchange Server 2007-Produktdokumentation.

