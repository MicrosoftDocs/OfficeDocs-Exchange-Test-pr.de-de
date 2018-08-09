---
title: 'Hub-Transportrolle an lokalem Standort nicht erkannt'
TOCTitle: Hub Transport role not detected in local site_BridgeheadRoleNotPresentInSite
ms:assetid: f318c947-81a8-4c18-975a-0f1e7868042a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.bridgeheadrolenotpresentinsite(v=EXCHG.150)
ms:contentKeyID: 50477054
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hub Transport role not detected in local site\_BridgeheadRoleNotPresentInSite

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup displays this warning because an existing Hub Transport server role could not be detected in the local Active Directory® directory service site.

You have chosen to install the Mailbox Server role before an instance of the Hub Transport role is installed in the Active Directory site.

Exchange 2007 Hub Transport Services are deployed inside your organization's Active Directory. Hub Transport Services handle all mail flow inside the organization, applies organizational mail flow routing rules, and are responsible for delivering messages to a recipient's mailbox.

Users will be able to log on to their mailboxes, but mail cannot be sent or received from this mailbox server until a Hub Transport role is installed.

