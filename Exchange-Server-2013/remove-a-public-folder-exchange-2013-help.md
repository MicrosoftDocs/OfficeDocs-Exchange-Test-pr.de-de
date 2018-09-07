---
title: 'Entfernen eines öffentlichen Ordners: Exchange 2013 Help'
TOCTitle: Entfernen eines öffentlichen Ordners
ms:assetid: 334b831d-e372-4d85-a407-5c8a5d0e78de
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997202(v=EXCHG.150)
ms:contentKeyID: 50475287
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen eines öffentlichen Ordners

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-11-16_

Sie müssen möglicherweise öffentliche Ordner entfernen, die nicht länger in Ihrer Organisation verwendet werden. Informationen dazu, welche Öffentlichen Ordner entfernt werden sollten, finden Sie unter [Anzeigen von Statistiken für öffentliche Ordner und Elemente öffentlicher Ordner](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/view-public-folder-statistics).

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit öffentlichen Ordnern finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Sie können einen E-Mail-aktivierten öffentlichen Ordner nicht löschen. Bevor Sie den Ordner löschen können, müssen Sie E-Mails für den öffentlichen Ordner deaktivieren. Weitere Informationen finden Sie unter [E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern](mail-enable-or-mail-disable-a-public-folder-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen eines öffentlichen Ordners mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Öffentliche Ordner** \> **Öffentliche Ordner**.

2.  Wählen Sie in der Listenansicht den öffentlichen Ordner aus, den Sie löschen möchten. Beim Klicken auf den Ordnernamen werden Unterordner innerhalb dieses Ordners angezeigt, sofern welche vorhanden sind. An diesem Punkt können Sie durch Klicken einen bestimmten Unterordner zum Entfernen auswählen.
    
    Wenn Sie einen Ordner oder Unterordner löschen möchten, klicken Sie auf eine beliebige Stelle der Ordnerzeile, außer auf den unterstrichenen Namen des Ordners, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"). Wenn Sie auf den unterstrichenen Namen des Ordners klicken, steht die Option **Löschen** nicht zur Verfügung.
    
    ![So wählen Sie einen öffentlichen Ordner zum Entfernen aus](images/Aa997202.8666290d-3f19-4c70-afe3-45569762718b(EXCHG.150).png "So wählen Sie einen öffentlichen Ordner zum Entfernen aus")  

3.  Sie werden in einem Warnungsfeld gefragt, ob Sie den öffentlichen Ordner wirklich löschen möchten. Klicken Sie auf **Ja**, um den Vorgang fortzusetzen.

## Löschen eines öffentlichen Ordners mithilfe der Shell

In diesem Beispiel wird der öffentliche Ordner "Help Desk\\Resolved" gelöscht. Bei diesem Befehl wird vorausgesetzt, dass der öffentliche Ordner "Resolved" keine Unterordner umfasst.

    Remove-PublicFolder -Identity "\Help Desk\Resolved"

In diesem Beispiel wird der vorherige Befehl ohne Änderungen getestet.

    Remove-PublicFolder -Identity "\HelpDesk\Resolved" -WhatIf

In diesem Beispiel wird der öffentliche Ordner "Marketing" mit allen Unterordnern entfernt, da der Befehl rekursiv ausgeführt wird.

    Remove-PublicFolder -Identity "\Marketing" -Recurse:$True

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-PublicFolder](https://technet.microsoft.com/de-de/library/bb124894\(v=exchg.150\)).

