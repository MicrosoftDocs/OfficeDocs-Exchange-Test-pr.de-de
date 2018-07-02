---
title: 'Erstellen eines DAG-Netzwerks: Exchange 2013 Help'
TOCTitle: Erstellen eines DAG-Netzwerks
ms:assetid: 6caec7be-788a-4058-87a7-f31c575b870c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298051(v=EXCHG.150)
ms:contentKeyID: 50475896
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen eines DAG-Netzwerks

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-02_

Bei Bedarf können Sie zusätzliche Netzwerke erstellen, die in einer Database Availability Group (DAG) verwendet werden. Sie können ein DAG-Netzwerk mithilfe der Exchange-Verwaltungskonsole oder der Shell erstellen.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier: [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Sie können ein DAG-Netzwerk nur erstellen, wenn die automatische Netzwerkkonfiguration für eine DAG deaktiviert wurde. Genaue Anweisungen zum Deaktivieren der automatischen Netzwerkkonfiguration für eine DAG finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md).

  - Beim Erstellen eines DAG-Netzwerks müssen Sie eindeutige Subnetze zuweisen, die von keinem anderen DAG-Netzwerk verwendet werden. Wenn Sie Subnetze verwenden, die bereits einem vorhandenen DAG-Netzwerk zugewiesen sind, werden diese aus diesem DAG-Netzwerk entfernt und dem neu erstellten DAG-Netzwerk hinzugefügt.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines DAG-Netzwerks mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**.

2.  Wählen Sie die DAG aus, die Sie konfigurieren möchten, und klicken Sie dann auf ![Hinzufügen von DAG-Netzwerken](images/Dd298051.befcdc4e-7f7a-451d-a0a8-608c79f5d186(EXCHG.150).gif "Hinzufügen von DAG-Netzwerken").

3.  
    
    Stellen Sie auf der Seite **Neues Netzwerk der Database Availability Group** folgende Informationen bereit:
    
      - **Name des Netzwerks der Database Availability Group**   Geben Sie in diesem Feld einen Namen für das Netzwerk ein, der in der DAG eindeutig ist.
    
      - **Beschreibung**   Stellen Sie in diesem Feld eine Textbeschreibung des DAG-Netzwerks bereit.
    
      - **Subnetze**   Ordnen Sie in diesem Feld dem DAG-Netzwerk mindestens ein Subnetz zu. Klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um ein Subnetz hinzuzufügen, klicken Sie auf ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um ein Subnetz zu bearbeiten, und klicken Sie auf das Minuszeichen (-), um ein Subnetz zu entfernen.

4.  Klicken Sie auf **Speichern**, um das DAG-Netzwerk zu erstellen.

## Verwenden der Shell zum Erstellen eines Netzwerks für DAGs

In diesem Beispiel wird das Netzwerk "ReplicationDagNetwork02" erstellt. Das Subnetz lautet 10.0.0.0, die Bitmaske ist 8 und der Name der DAG ist "DAG1". Die Replikation ist für dieses Netzwerk aktiviert, und es wird eine optionale Beschreibung des Netzwerks hinzugefügt.

    New-DatabaseAvailabilityGroupNetwork -DatabaseAvailabilityGroup DAG1 -Name ReplicationDagNetwork02 -Description "Replication network 2" -Subnets 10.0.0.0/8 -ReplicationEnabled:$True

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Erstellung eines DAG-Netzwerks zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**. Wählen Sie die entsprechende DAG, und das neu erstellte DAG-Netzwerk wird im Detailbereich angezeigt.

  - Führen Sie in der Shell folgenden Befehl aus, um zu überprüfen, ob das DAG-Netzwerk erstellt wurde, und um Konfigurationsinformationen zum DAG-Netzwerk anzuzeigen:
    
        Get-DatabaseAvailabilityGroupNetwork <DAGNetworkName> | Format-List

## Weitere Informationen

[Set-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298008\(v=exchg.150\))

[Get-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd297938\(v=exchg.150\))

[New-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd335225\(v=exchg.150\))

[Remove-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298131\(v=exchg.150\))

