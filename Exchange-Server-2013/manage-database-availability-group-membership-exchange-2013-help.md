---
title: 'Verwalten der Mitgliedschaft in DAGs: Exchange 2013 Help'
TOCTitle: Verwalten der Mitgliedschaft in DAGs
ms:assetid: fb2ea15e-96d5-4045-b75b-b0aa5fc60479
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351278(v=EXCHG.150)
ms:contentKeyID: 50477127
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Mitgliedschaft in DAGs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-08-13_

Wenn einer Database Availability Group (DAG) ein Server hinzugefügt wird, wird dieser mit den anderen Servern in der Database Availability Group eingesetzt, um eine automatische Wiederherstellung auf Datenbankebene nach Datenbank-, Server- oder Netzwerkausfällen zu bieten. Wenn Sie einen Server aus einer DAG entfernen, ist der Server nicht länger automatisch vor Ausfällen geschützt.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier: [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten pro Server

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - DAGs nutzen Windows-Failoverclustering-Technologien. Für jeden Postfachserver, der Mitglied einer DAG ist, liegt ein Knoten im zugrunde liegenden Cluster vor, der von der DAG verwendet wird. Daher kann ein Postfachserver zu jeder Zeit nur Mitglied einer einzigen DAG sein. Da DAGs WFC-Technologie einsetzen, müssen alle Server, die einer DAG hinzugefügt werden, dasselbe Betriebssystem ausführen: entweder Windows Server 2008 R2 Enterprise bzw. Datacenter Edition oder Standard bzw. Datacenter Edition von Windows Server 2012 oder Windows Server 2012 R2.

  - Wenn Sie Postfachserver mit Windows Server 2012 hinzufügen, müssen Sie das Clusternamensobjekt provisorisch für die DAG bereitstellen. Wenn Sie Postfachserver unter Windows Server 2012 R2 hinzufügen und dem DAG kein Administratorzugriffspunkt zugewiesen ist, müssen Sie kein Clusternetzwerkobjekt (Cluster Network Object, CNO) provisorisch bereitstellen, da DAGs ohne Administratorzugriffspunkt keine CNOs verwenden. Genaue Anweisungen finden Sie unter [Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group](pre-stage-the-cluster-name-object-for-a-database-availability-group-exchange-2013-help.md).

  - Bevor Sie Mitglieder zu einer DAG hinzufügen können, müssen Sie die DAG erstellen. Weitere Informationen finden Sie unter [Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md).

  - Sie müssen alle replizierten Datenbankkopien vom Server entfernen, bevor Sie ihn aus einer DAG entfernen können.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwalten der Mitgliedschaft in einer Database Availability Group mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**.

2.  Wählen Sie die DAG aus, die Sie konfigurieren möchten, und klicken Sie dann auf ![Verwalten von DAG-Mitgliedern](images/Dd351278.d567ae56-d6cd-4edb-ab67-ad8f7c58f337(EXCHG.150).gif "Verwalten von DAG-Mitgliedern").
    
      - Wenn Sie einen oder mehrere Postfachserver zur DAG hinzufügen möchten, klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), wählen Sie die Server in der Liste aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.
    
      - Wenn Sie einen oder mehrere Postfachserver aus der DAG entfernen möchten, wählen Sie die Server aus, und klicken Sie dann auf das Minussymbol (-).

3.  Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

4.  Klicken Sie nach erfolgreichem Abschluss des Tasks auf **Schließen**.

## Verwalten der Mitgliedschaft in einer Database Availability Group mithilfe der Shell

In diesem Beispiel wird der Postfachserver "MBX1" in der DAG "DAG1" hinzugefügt.

```powershell
Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
```

In diesem Beispiel wird der Postfachserver "MBX1" aus der DAG "DAG1" entfernt. Bevor Sie diesen Befehl ausführen, sollten Sie sicherstellen, dass sich auf dem Postfachserver keine replizierten Datenbanken befinden.

```powershell
Remove-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
```

In diesem Beispiel werden die Konfigurationseinstellungen für den Postfachserver "MBX4" aus der DAG "DAG2" entfernt. Es wird davon ausgegangen, dass "MBX4" über einen längeren Zeitraum offline ist. Daher wird die zugehörige Konfiguration aus der DAG entfernt, während der Server offline ist, um ein Quorum mit den verbleibenden online geschalteten Mitgliedern der DAG einzurichten.

```powershell
Remove-DatabaseAvailabilityGroupServer -Identity DAG2 -MailboxServer MBX4 -ConfigurationOnly
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um zu überprüfen, dass Sie die DAG-Mitgliedschaft erfolgreich verwaltet haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**. Die aktuelle DAG-Mitgliedschaft wird in der Spalte **Mitgliedsserver** angezeigt.

  - Führen Sie den folgenden Befehl in der Shell aus, um DAG-Mitgliedschaftsinformationen anzuzeigen:
    
    ```powershell
    Get-DatabaseAvailabilityGroup <DAGName> | Format-List Servers
    ```

## Weitere Informationen

[Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd298049\(v=exchg.150\))

[Remove-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd297956\(v=exchg.150\))

