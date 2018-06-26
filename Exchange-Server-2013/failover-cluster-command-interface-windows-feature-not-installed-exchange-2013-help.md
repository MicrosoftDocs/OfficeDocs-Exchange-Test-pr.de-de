---
title: 'Failovercluster-Befehlsschnittstelle-Windows-Funktion nicht installiert: Exchange 2013 Help'
TOCTitle: Failovercluster-Befehlsschnittstelle-Windows-Funktion nicht installiert
ms:assetid: 0d839514-5ab7-497d-8945-41392b4c3980
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.rsatclusteringcmdinterfaceinstalled(v=EXCHG.150)
ms:contentKeyID: 51409265
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Failovercluster-Befehlsschnittstelle-Windows-Funktion nicht installiert

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2014-12-03_

Das Microsoft Exchange Server 2013-Setup kann nicht fortgesetzt werden, da auf dem lokalen Computer eine erforderliche Windows-Funktion nicht vorhanden ist. Sie müssen diese Windows-Funktion installieren, bevor Exchange 2013 fortgesetzt werden kann.

Für das Exchange 2013 Setup muss die Windows-Funktion für die **Failovercluster-Befehlszeilenschnittstelle** auf dem Computer installiert werden, bevor die Installation fortgesetzt werden kann.

Führen Sie die folgenden Schritte durch, um die Windows-Funktion auf diesem Computer zu installieren. Wenn zum Abschluss der Featureinstallation ein Neustart erforderlich ist, müssen Sie das Exchange 2013-Setup beenden, einen Neustart durchführen und das Setup erneut starten.


> [!NOTE]
> Bevor das Exchange 2013-Setup fortgesetzt werden kann, müssen möglicherweise weitere Windows-Funktionen oder -Updates installiert werden. Eine vollständige Liste der erforderlichen Windows-Funktionen und -Updates finden Sie in den <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>.



1.  Öffnen Sie die Windows PowerShell auf dem lokalen Computer.

2.  Führen Sie den folgenden Befehl aus, um die erforderliche Windows-Funktion zu installieren.
    
        Install-WindowsFeature RSAT-Clustering-CmdInterface

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

