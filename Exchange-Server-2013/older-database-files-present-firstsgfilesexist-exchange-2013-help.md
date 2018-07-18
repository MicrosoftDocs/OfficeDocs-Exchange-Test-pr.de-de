﻿---
title: 'Older database files present_FirstSGFilesExist: Exchange 2013 Help'
TOCTitle: Older database files present_FirstSGFilesExist
ms:assetid: 907faeb8-1c6d-49fc-95a1-417f415a9d79
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.firstsgfilesexist(v=EXCHG.150)
ms:contentKeyID: 50476159
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Older database files present\_FirstSGFilesExist

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because it detected existing Microsoft Exchange database files in the target installation path.

Exchange 2007 setup requires that the target installation path be empty of Microsoft Exchange database files.

To resolve this issue, remove all existing files from target installation paths and then rerun setup.

**To delete existing Exchange Server database files from the target installation path**

1.  In My Computer or Windows Explorer, locate the target install path.
    

    > [!NOTE]
    > By default, the database files are located in:<BR>&lt;systemDrive&gt;:\Program Files\Microsoft\Exchange Server\Mailbox\First Storage Group.



2.  Right-click the files to be removed, and then select **Delete**.

3.  At the **Confirm File Delete** dialog, click **Yes**.

4.  Repeat steps 2 and 3 for all files in the target install paths.

