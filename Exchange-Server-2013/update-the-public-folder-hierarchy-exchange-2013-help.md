---
title: 'Aktualisieren der Öffentliche Ordner-Hierarchie: Exchange 2013 Help'
TOCTitle: Aktualisieren der Öffentliche Ordner-Hierarchie
ms:assetid: a7b2fb51-0207-4d7d-938d-466ae110bb90
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ945055(v=EXCHG.150)
ms:contentKeyID: 52062793
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren der Öffentliche Ordner-Hierarchie

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2014-04-03_

Sie müssen die Hierarchie öffentlicher Ordner nur aktualisieren, wenn Sie die Hierarchiesynchronisierung und den Postfach-Assistenten manuell aufrufen möchten. Beide werden für jedes Postfach für öffentliche Ordner in der Organisation mindestens alle 24 Stunden aufgerufen. Die Hierarchiesynchronisierung wird alle 15 Minuten aufgerufen, wenn Benutzer über Microsoft Outlook oder einen Microsoft Exchange-Webdienstclient an einem sekundären Postfach angemeldet sind.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange Online finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange Server 2013 finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Bei Ausführung dieses Befehls mit dem Parameter *InvokeSynchronizer* wird empfohlen, den Parameter *SuppressStatus* anzugeben. Wenn Sie diesen Parameter nicht mit dem Befehl verwenden, werden in der Ausgabe für eine Zeitdauer von bis zu einer Minute alle drei Sekunden Statusmeldungen angezeigt. Diese Instanz der Shell kann erst verwendet werden, wenn dieser Zeitraum von einer Minute verstrichen ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktualisieren der Öffentliche Ordner-Hierarchie

In diesem Beispiel wird die Hierarchie öffentlicher Ordner für das Postfach für öffentliche Ordner "PF\_marketing" aktualisiert, und die Ausgabe des Befehls wird unterdrückt.

    Update-PublicFolderMailbox -Identity PF_marketing -InvokeSynchronizer -SuppressStatus

In diesem Beispiel werden alle Postfächer für öffentliche Ordner aktualisiert, und die Ausgabe des Befehls wird unterdrückt.

    Get-Mailbox -PublicFolder | Update-PublicFolderMailbox InvokeSynchronizer -SuppressStatus

