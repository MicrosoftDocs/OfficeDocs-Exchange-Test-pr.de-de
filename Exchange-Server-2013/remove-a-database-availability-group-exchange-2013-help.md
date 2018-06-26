---
title: 'Entfernen einer Datenbankverfügbarkeitsgruppe: Exchange 2013 Help'
TOCTitle: Entfernen einer Datenbankverfügbarkeitsgruppe
ms:assetid: 071296e9-31b0-40f4-9a02-177d97486ebd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335069(v=EXCHG.150)
ms:contentKeyID: 50474982
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer Datenbankverfügbarkeitsgruppe

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-11-16_

Database Availability Groups (DAG) können schnell und problemlos entfernt werden. Sie können eine DAG mithilfe der Exchange-Verwaltungskonsole oder der Shell entfernen.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier: [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Bevor Sie eine DAG entfernen können, muss die DAG leer sein. Wenn die zu entfernende DAG Postfachserver enthält, müssen Sie die Server zunächst aus der DAG entfernen. Genaue Anweisungen zum Entfernen eines Postfachservers aus einer DAG finden Sie unter [Verwalten der Mitgliedschaft in DAGs](manage-database-availability-group-membership-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen einer Database Availability Group mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie zu **Server** \> **Database Availability Groups**.

2.  Wählen Sie die DAG aus, die entfernt werden soll, und klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie auf **Ja**, um die Warnung zu bestätigen und die Database Availability Group zu entfernen.

## Entfernen einer DAG mithilfe der Shell

In diesem Beispiel wird die DAG "DAG1" entfernt.

    Remove-DatabaseAvailabilityGroup -Identity DAG1

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die DAG erfolgreich entfernt wurde:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**, und überprüfen Sie, ob die DAG noch angezeigt wird.

  - Führen Sie in der Shell den folgenden Befehl aus, um zu überprüfen, ob die DAG weiterhin vorhanden ist:
    
        Get-DatabaseAvailabilityGroup <DAGName>
    
    Wenn die DAG erfolgreich gelöscht wurde, werden Sie bei Ausführung dieses Befehls in einer Fehlermeldung darauf hingewiesen, dass das Objekt nicht gefunden wurde.

