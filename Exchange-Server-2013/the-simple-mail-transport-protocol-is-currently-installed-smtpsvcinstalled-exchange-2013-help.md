---
title: 'SMTP ist derzeit installiert'
TOCTitle: The Simple Mail Transport Protocol is currently installed_SMTPSvcInstalled
ms:assetid: f786a93c-876d-4f4e-adb6-4dfea3d820d1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.smtpsvcinstalled(v=EXCHG.150)
ms:contentKeyID: 50477107
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# The Simple Mail Transport Protocol is currently installed\_SMTPSvcInstalled

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because the Microsoft Windows Server™ 2003 Simple Mail Transfer Protocol (SMTP) service is installed on this computer.

Microsoft Exchange setup requires that the SMTP service not be installed on servers that are used for Exchange 2007.

To resolve this issue, uninstall the SMTP service and rerun Microsoft Exchange setup.

**To uninstall the SMTP service by using Add or Remove a Windows Component in Control Panel**

1.  On the **Start** menu, click **Control Panel**.

2.  Double-click **Add or Remove Programs**.

3.  Click **Add/Remove Windows Components**.

4.  In the **Components** list, select the **Application Server** check box and then click **Details**.

5.  Select **Internet Information Services Manager** and then click **Details**.

6.  Select **SMTP Service** and then click to clear the check box.

7.  Click **OK** two times to return to the **Components** list and then click **Next**.

8.  Click **Finish** when the SMTP service is uninstalled.

