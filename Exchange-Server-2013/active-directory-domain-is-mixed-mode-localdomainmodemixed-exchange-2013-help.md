---
title: 'Active Directory domain is mixed mode_LocalDomainModeMixed: Exchange 2013 Help'
TOCTitle: Active Directory domain is mixed mode_LocalDomainModeMixed
ms:assetid: a6affcfe-7264-455b-8e5c-683fa87383f1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.localdomainmodemixed(v=EXCHG.150)
ms:contentKeyID: 50476386
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Active Directory domain is mixed mode\_LocalDomainModeMixed

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because an existing Active Directory domain is not set to Microsoft Windows®°2000 Server native mode or better.

Exchange 2007 setup will create Universal Security Groups that can only exist in Windows 2000 Server native mode, or better, domains.

To resolve this issue, follow these steps to raise the domain functional level to at least the Windows 2000 Server native level, and then rerun Exchange 2007 setup.

**To raise the domain functional level**

1.  Open Active Directory Domains and Trusts.

2.  In the console tree, right-click the domain for which you want to raise functionality, and then click **Raise Domain Functional Level**.

3.  In **Select an available domain functional level**, use one of the following procedures:
    
      - To raise the domain functional level to Windows 2000 Server native, click **Windows 2000 native**, and then click **Raise**.
    
      - To raise domain functional level to Windows Server® 2003, click **Windows Server 2003**, and then click **Raise.**


> [!WARNING]
> <BR>If you have or will have any domain controllers running Windows NT®&nbsp;4.0 and earlier, do not raise the domain functional level to Windows&nbsp;2000 Server native. After the domain functional level is set to Windows&nbsp;2000 Server native, it cannot be changed back to Windows&nbsp;2000 Server mixed.<BR>If you have or will have any domain controllers running Windows NT&nbsp;4.0 and earlier or Windows&nbsp;2000 Server, do not raise the domain functional level to Windows Server&nbsp;2003. After the domain functional level is set to Windows Server&nbsp;2003, it cannot be changed back to Windows&nbsp;2000 Server mixed or Windows&nbsp;2000 Server native.




