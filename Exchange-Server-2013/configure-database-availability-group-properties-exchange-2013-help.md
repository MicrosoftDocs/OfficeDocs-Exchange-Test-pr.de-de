---
title: 'Konfigurieren der Eigenschaften einer DAG: Exchange 2013 Help'
TOCTitle: Konfigurieren der Eigenschaften einer DAG
ms:assetid: 50daeac5-a16f-4362-a325-19e0fe25d59d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297985(v=EXCHG.150)
ms:contentKeyID: 50475638
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Eigenschaften einer DAG

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-24_

Sie können die Exchange-Verwaltungskonsole oder die Shell verwenden, um die Eigenschaften einer Database Availability Group (DAG) zu konfigurieren, einschließlich der IP-Adresskonfiguration und des für die DAG verwendeten Zeugenservers und Zeugenverzeichnisses. Mit der Shell können Sie DAG-Eigenschaften konfigurieren, die nicht in der Exchange-Verwaltungskonsole zur Verfügung stehen, z. B. den alternativen Zeugenserver und das Zeugenverzeichnis, den für die Replikation verwendeten TCP-Port und den DAC-Modus (Datacenter Activation Coordination).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - DAG-Eigenschaftswerte werden in Active Directory und in der Clusterdatenbank gespeichert. Einige Eigenschaften werden jedoch nur in der Clusterdatenbank gespeichert. Das bedeutet, dass der zugrunde liegende Cluster für die DAG ausgeführt werden und ein Quorum besitzen muss, um folgende Eigenschaften festlegen zu können:
    
      - ReplicationPort
    
      - NetworkCompression
    
      - NetworkEncryption
    
      - DiscoverNetworks

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Eigenschaften einer DAG mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**.

2.  Wählen Sie die DAG aus, die Sie konfigurieren möchten, und klicken Sie auf ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Verwenden Sie die Seite **Allgemein**, um DAG-Mitgliedschaft und Betriebsstatus anzuzeigen sowie den Zeugenserver, das Zeugenverzeichnis und die automatische Netzwerkkonfiguration für die DAG zu konfigurieren:
    
      - **Zeugenserver**   Der Hostname oder vollqualifizierte Domänenname (FQDN) des Zeugenservers für die DAG. Auch wenn es sich um eine erforderliche Eigenschaft für alle DAGs handelt, wird der Zeugenserver nur verwendet, wenn eine gerade Anzahl von DAG-Mitgliedern vorliegt und das verwendete Quorummodell "Knoten- und Dateifreigabemehrheit" lautet.
    
      - **Zeugenverzeichnis**   Der vollständige Pfad zum Verzeichnis, in dem die Datei **witness.log** auf dem Zeugenserver gespeichert ist. Obwohl es sich um eine erforderliche Eigenschaft für alle DAGs handelt, wird das Zeugenverzeichnis nur verwendet, wenn der Zeugenserver der DAG im Einsatz ist.
    
      - **Server in Betrieb**   Ein schreibgeschütztes Feld, das eine Liste der DAG-Mitglieder und ihren aktuellen Betriebsstatus anzeigt.
    
      - **Database Availability Group-Netzwerke manuell konfigurieren**   Ein Kontrollkästchen, dass Sie aktivieren, wenn Sie alle DAG-Netzwerke manuell konfigurieren möchten. Wenn Sie dieses Kontrollkästchen nicht aktivieren, konfiguriert das System DAG-Netzwerke automatisch basierend auf der Netzwerkschnittstellenkonfiguration. Wenn das Kontrollkästchen nicht aktiviert ist, sind die Cmdlets **Set-DatabaseAvailabilityGroupNetwork** und **New-DatabaseAvailabilityGroupNetwork** zur Durchführung administrativer Aufgaben bezüglich der DAG deaktiviert.

4.  Auf der Seite **IP-Adressen** können Sie die IP-Adressen anzeigen und ändern, die der DAG zugewiesen sind:
    
      - Wählen Sie eine vorhandene IP-Adresse aus, und klicken Sie auf ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um sie zu ändern.
    
      - Wählen Sie eine vorhandene IP-Adresse aus, und klicken Sie auf das Minussymbol (Löschen), um die Adresse zu entfernen.
    
      - Geben Sie eine IP-Adresse ein, und klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um sie zur DAG hinzuzufügen.

5.  Klicken Sie auf **Speichern**, um alle vorgenommenen Änderungen zu speichern.

## Konfigurieren von Eigenschaften einer DAG mit der Shell

In diesem Beispiel wird das Zeugenverzeichnis für die DAG "DAG1" auf "C:\\DAG1DIR" festgelegt.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -WitnessDirectory C:\DAG1DIR

In diesem Beispiel werden der alternative Zeugenserver "CAS3" und das alternative Zeugenverzeichnis "C:\\DAGFileShareWitnesses\\DAG1.contoso.com" für die DAG "DAG1" vorkonfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -AlternateWitnessDirectory C:\DAGFileShareWitnesses\DAG1.contoso.com -AlternateWitnessServer CAS3

In diesem Beispiel wird die DAG "DAG1" zur Verwendung von Dynamic Host Configuration-Protokoll (DHCP) zum Abrufen einer IP-Adresse konfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -DatabaseAvailabilityGroupIPAddresses 0.0.0.0

In diesem Beispiel wird die DAG "DAG1" zur Verwendung der statischen IP-Adresse "10.0.0.8" konfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -DatabaseAvailabilityGroupIPAddresses 10.0.0.8

In diesem Beispiel wird die DAG "DAG1" mit mehreren Subnetzen mit mehreren statischen IP-Adressen konfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -DatabaseAvailabilityGroupIPAddresses 10.0.0.8,10.0.1.8

In diesem Beispiel wird die DAG "DAG1" für den DAC-Modus konfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -DatacenterActivationMode DagOnly

In diesem Beispiel wird der Replikationsport für die DAG "DAG1" als Port 63132 konfiguriert.

    Set-DatabaseAvailabilityGroup -Identity DAG1 -ReplicationPort 63132


> [!NOTE]
> Nach dem Ändern des Standardreplikationsports für eine DAG müssen Sie die Windows-Firewall-Ausnahmen für jedes Mitglied der DAG manuell so anpassen, dass die Kommunikation über den angegebenen Port zugelassen wird.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass die Konfiguration der DAG erfolgreich abgeschlossen wurde:

  - Führen Sie in der Shell den folgenden Befehl aus, um die DAG-Konfigurationseinstellungen anzuzeigen und sicherzustellen, dass die DAG erfolgreich konfiguriert wurde.
    
        Get-DatabaseAvailabilityGroup <DAGName> | Format-List

## Weitere Informationen

[Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md)

[Entfernen einer Datenbankverfügbarkeitsgruppe](remove-a-database-availability-group-exchange-2013-help.md)

[Erstellen eines DAG-Netzwerks](create-a-database-availability-group-network-exchange-2013-help.md)

[Verwalten der Mitgliedschaft in DAGs](manage-database-availability-group-membership-exchange-2013-help.md)

[Get-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351226\(v=exchg.150\))

[Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\))

