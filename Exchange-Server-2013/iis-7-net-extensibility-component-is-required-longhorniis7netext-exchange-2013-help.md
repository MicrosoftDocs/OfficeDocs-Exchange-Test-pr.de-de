---
title: 'Die IIS 7-Komponente für .NET-Erweiterbarkeit ist erforderlich_LonghornIIS7NetExt: Exchange 2013 Help'
TOCTitle: Die IIS 7-Komponente für .NET-Erweiterbarkeit ist erforderlich_LonghornIIS7NetExt
ms:assetid: 8b481626-b68a-4fba-b66e-a02c03856bfd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.longhorniis7netext(v=EXCHG.150)
ms:contentKeyID: 50476218
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Die IIS 7-Komponente für .NET-Erweiterbarkeit ist erforderlich\_LonghornIIS7NetExt

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2010-Setup kann nicht fortgesetzt werden, da die erforderliche Komponente zur .NET-Erweiterbarkeit für Internet Information Server (IIS) 7 nicht auf dem Zielserver installiert ist.

Damit Exchange 2010 Windows PowerShell Remoting verwenden kann, muss auf dem Zielserver die IIS 7-Komponente für .NET-Erweiterbarkeit installiert sein.

Verwenden Sie zum Beheben dieses Fehlers den Server-Manager, um die IIS 7-Komponente für .NET-Erweiterbarkeit auf diesem Server zu installieren, und führen Sie dann Exchange 2010-Setup erneut aus.

Installieren der IIS 7-Komponente für .NET-Erweiterbarkeit in Windows Server 2008 oder in Windows Server 2008 R2 mithilfe des Server-Manager-Tools

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung** und dann auf **Server-Manager**.

2.  Erweitern Sie im linken Navigationsbereich **Rollen**, klicken Sie mit rechten Maustaste auf **Webserver (IIS)**, und wählen Sie **Rollendienste hinzufügen** aus.

3.  Führen Sie im Bereich **Funktionsdienste auswählen** einen Bildlauf bis zum Eintrag **Anwendungsentwicklung** durch.

4.  Aktivieren Sie das Kontrollkästchen unter **.NET-Erweiterbarkeit**.

5.  Klicken Sie im Bereich **Funktionsdienste auswählen** auf **Weiter**, und klicken Sie dann im Bereich **Installationsauswahl bestätigen** auf **Installieren**.

6.  Klicken Sie auf **Schließen**, um den Assistenten für das Hinzufügen von Funktionsdiensten zu beenden.

