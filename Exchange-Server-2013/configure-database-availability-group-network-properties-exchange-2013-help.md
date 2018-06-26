---
title: 'Konfigurieren der Eigenschaften von DAG-Netzwerken: Exchange 2013 Help'
TOCTitle: Konfigurieren der Eigenschaften von DAG-Netzwerken
ms:assetid: 41197639-988f-476c-9788-51d5191a7dce
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297927(v=EXCHG.150)
ms:contentKeyID: 50475481
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Eigenschaften von DAG-Netzwerken

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-31_

Für jedes DAG-Netzwerk (Database Availability Group) sind mehrere konfigurierbare Eigenschaften vorhanden. Dazu gehören der Name des DAG-Netzwerks, ein Beschreibungsfeld für das DAG-Netzwerk, eine Liste der vom DAG-Netzwerk verwendeten Subnetze und die Information, ob das DAG-Netzwerk für die Replikation aktiviert ist.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Sie können ein DAG-Netzwerk nur konfigurieren, wenn die automatische Netzwerkkonfiguration für eine DAG deaktiviert wurde. Genaue Anweisungen zum Deaktivieren der automatischen Netzwerkkonfiguration für eine DAG finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Eigenschaften eines DAG-Netzwerks mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**.

2.  Wählen Sie die DAG aus, die Sie konfigurieren möchten. Legen Sie dann im Detailbereich, unterhalb des zu konfigurierenden DAG-Netzwerks, die folgenden Einstellungen fest:
    
      - **Replikation deaktivieren** oder **Replikation aktivieren**   Konfiguriert die Replikationseinstellungen für das DAG-Netzwerk.
    
      - **Entfernen**   Entfernt ein DAG-Netzwerk. Sie müssen zunächst alle zugeordneten Subnetze aus dem DAG-Netzwerk entfernen, bevor Sie ein DAG-Netzwerk entfernen können.
    
      - **Details anzeigen**   Konfiguriert Eigenschaften eines DAG-Netzwerks, z. B. einen Namen, eine Beschreibung und dem DAG-Netzwerk zugeordnete Subnetze. Sie können auch die Netzwerkschnittstellen anzeigen, die diesen Subnetzen zugeordnet sind, und die Replikation für das DAG-Netzwerk aktivieren oder deaktivieren.

## Konfigurieren von Eigenschaften eines DAG-Netzwerks mit der Shell

In diesem Beispiel werden dem DAG-Netzwerk "MapiDagNetwork" in der DAG "DAG1" das Subnetz 10.0.0.0 und die Subnetzmaske 255.0.0.0 hinzugefügt.

    Set-DatabaseAvailabilityGroupNetwork -Subnets 10.0.0.0/8 -Identity DAG1\MapiDagNetwork

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob das DAG-Netzwerk erfolgreich konfiguriert wurde:

  - Führen Sie in der Shell den folgenden Befehl aus, um die Konfigurationseinstellungen für das DAG-Netzwerk anzuzeigen und sicherzustellen, dass das DAG-Netzwerk erfolgreich konfiguriert wurde.
    
        Get-DatabaseAvailabilityGroupNetwork <DAGNetworkName> | Format-List

## Weitere Informationen

[Set-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298008\(v=exchg.150\))

[Get-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd297938\(v=exchg.150\))

[New-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd335225\(v=exchg.150\))

[Remove-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298131\(v=exchg.150\))

