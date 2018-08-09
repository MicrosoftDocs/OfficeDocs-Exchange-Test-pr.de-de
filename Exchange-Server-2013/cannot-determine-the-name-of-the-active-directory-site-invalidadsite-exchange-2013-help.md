---
title: 'Name des Active Directory-Standorts kann nicht bestimmt werden'
TOCTitle: Der Name des Active Directory-Standorts kann nicht bestimmt werden_InvalidADSite
ms:assetid: ef96e077-08a0-4108-9f7d-0d61758abcd4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.invalidadsite(v=EXCHG.150)
ms:contentKeyID: 50477041
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Der Name des Active Directory-Standorts kann nicht bestimmt werden\_InvalidADSite

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da dieser Server anscheinend nicht zu einem gültigen Standort des Verzeichnisdiensts Active Directory® gehört.

Für das Microsoft Exchange-Setup ist erforderlich, dass der Server, auf dem Exchange 2007 installiert werden soll, zu einem gültigen Active Directory-Standort gehört.

Überprüfen Sie zum Beheben dieses Problems, ob der lokale Server zu einem Active Directory-Standort gehört, und führen Sie das Setup von Exchange 2007 erneut aus.

Mithilfe des Parameters **/DsGetSite** des Befehlszeilenprogramms Nltest.exe können Sie die Standortzugehörigkeit anzeigen und überprüfen. Weitere Informationen finden Sie unter "Nltest.exe: NLTest Overview" im Abschnitt "Tools and Settings Collection" von *Windows Server 2003 Technical Reference* ([https://go.microsoft.com/fwlink/?LinkId=27734](https://go.microsoft.com/fwlink/?linkid=27734)).

Weitere Informationen zur Behandlung von Active Directory-Problemen finden Sie unter “Troubleshooting Active Directory Operations” in *Windows Server 2003: Vorgänge*(<https://go.microsoft.com/fwlink/?linkid=68099>)

