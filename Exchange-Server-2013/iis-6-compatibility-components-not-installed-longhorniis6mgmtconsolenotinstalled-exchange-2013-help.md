---
title: 'IIS 6 Compatibility components not installed_LonghornIIS6MgmtConsoleNotInstalled: Exchange 2013 Help'
TOCTitle: IIS 6 Compatibility components not installed_LonghornIIS6MgmtConsoleNotInstalled
ms:assetid: 8358eafb-def7-4b8d-8fe1-623bc5a0e20e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.longhorniis6mgmtconsolenotinstalled(v=EXCHG.150)
ms:contentKeyID: 50476162
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# IIS 6 Compatibility components not installed\_LonghornIIS6MgmtConsoleNotInstalled

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Der Versuch, die Clientzugriffs-Serverrolle, die Postfachserverrolle oder die Exchange 2007-Verwaltungstools auf den folgenden Windows-Betriebssystemen zu installieren, kann von Exchange Server 2007-Setup nicht fortgesetzt werden:

  - Windows Server 2008 R2

  - Windows Server 2008

  - Windows 7 (nur Verwaltungstools)

  - Windows Vista (nur Verwaltungstools)

Dieses Problem tritt auf, da die Komponente für die IIS 6-Metabasiskompatibilität und die Komponente für die IIS 6-Verwaltungskonsole nicht installiert sind.

Das Setup von Exchange 2007 erfordert, dass auf dem Computer, auf dem Sie die Exchange 2007-Clientzugriffs-Serverrolle, die Postfachserverrolle oder die Exchange 2007-Verwaltungstools installieren, die Komponente für die IIS 6-Metabase-Kompatibilität und die Komponenten für die IIS 6-Verwaltungskonsole installiert sind.

Um dieses Problem zu beheben, installieren Sie die Komponente für die IIS 6-Metabasiskompatibilität auf dem Zielserver, und führen Sie das Exchange-Setup anschließend erneut aus.

**Installieren der IIS 6.0-Komponente für .NET-Erweiterbarkeit in Windows Server 2008 oder in Windows Server 2008 R2 mithilfe des Server-Manager-Tools**

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Server-Manager**.

2.  Erweitern Sie im Navigationsbereich die Option **Rollen**, und klicken Sie dann mit der rechten Maustaste auf **Webserver (IIS)**. Wählen Sie dann **Rollendienste hinzufügen** aus.

3.  Führen Sie im Bereich **Funktionsdienste auswählen** einen Bildlauf bis zum Eintrag **Kompatibilität mit der IIS 6-Verwaltung** durch.

4.  Aktivieren Sie die Kontrollkästchen für **IIS 6-Metabasiskompatibilität**, **IIS 6-WMI-Kompatibilität** und **IIS 6-Verwaltungskonsole**.

5.  Klicken Sie auf der Seite **Rollendienste auswählen** auf **Weiter**.

6.  Klicken Sie auf der Seite **Installationsauswahl bestätigen** auf **Installieren**.

7.  Klicken Sie auf **Schließen**, um den Assistenten für das Hinzufügen von Funktionsdiensten zu beenden.

**Installieren der Komponenten für die IIS 6.0-Metabasiskompatibilität in Windows 7 oder in Windows Vista mithilfe der Systemsteuerung**

1.  Klicken Sie auf **Start**, klicken Sie auf **Systemsteuerung**, klicken Sie auf **Programme und Funktionen**, und klicken Sie dann auf **Windows-Funktionen ein- oder ausschalten**.

2.  Öffnen Sie **Internetinformationsdienste**.

3.  Öffnen Sie **Webverwaltungstools**.

4.  Öffnen Sie **Kompatibilität mit der IIS 6.0-Verwaltung**.

5.  Aktivieren Sie die Kontrollkästchen für **Kompatibilität mit IIS 6-Metabasis und IIS 6-Konfiguration**, **IIS 6-WMI-Kompatibilität** und **IIS 6-Verwaltungskonsole**.

6.  Klicken Sie auf **OK**.

