---
title: 'Erstellen einer Datenbankverfügbarkeitsgruppe: Exchange 2013 Help'
TOCTitle: Erstellen einer Datenbankverfügbarkeitsgruppe
ms:assetid: d6b98299-e203-488b-af73-50753fe152c8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351172(v=EXCHG.150)
ms:contentKeyID: 50476830
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Datenbankverfügbarkeitsgruppe

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Eine Datenbankverfügbarkeitsgruppe ist ein Satz aus bis zu 16 Microsoft Exchange Server 2013-Postfachservern, die eine automatische Wiederherstellung auf Datenbankebene nach einem Datenbank-, Server- oder Netzwerkfehler bieten. Wenn einer Datenbankverfügbarkeitsgruppe ein Postfachserver hinzugefügt wird, wird dieser mit den anderen Servern in der Datenbankverfügbarkeitsgruppe eingesetzt, um eine automatische Wiederherstellung auf Datenbankebene nach Datenbank-, Server- oder Netzwerkausfällen zu bieten.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier: [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Beim Erstellen einer DAG mit Postfachserver mit Windows Server 2012 müssen Sie das Clusternetzwerkobjekt (Cluster Network Object, CNO) provisorisch bereitstellen, bevor Sie der DAG Mitglieder hinzufügen. Wenn Sie eine DAG ohne einen Administratorzugriffspunkt mit Postfachservern erstellen, auf denen Windows Server 2012 R2 ausgeführt wird, müssen Sie für die DAG kein CNO provisorisch bereitstellen. Genaue Anweisungen finden Sie unter [Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group](pre-stage-the-cluster-name-object-for-a-database-availability-group-exchange-2013-help.md).

  - Beim Erstellen einer Datenbankverfügbarkeitsgruppe geben Sie einen eindeutigen Namen mit bis zu 15 Zeichen an. Außer einem Namen für die DAG müssen Sie der DAG auch eine oder mehrere IP-Adressen zuweisen (entweder IPv4 oder IPv4 und IPv6), es sei denn, Sie erstellen eine Windows Server 2012 R2-DAG ohne einen Administratorzugriffspunkt und weisen der DAG keine IP-Adressen hinzu. Andernfalls müssen die zugewiesenen IP-Adressen sich in jedem für das MAPI-Netzwerk vorgesehenen Subnetz befinden und verfügbar sein. Wenn Sie mindestens eine IPv4-Adresse angeben und Ihr System für die Verwendung von IPv6 konfiguriert ist, versucht der Task zudem, der DAG automatisch mindestens eine IPv6-Adresse zuzuweisen.

  - Beim Erstellen einer DAG haben Sie die Möglichkeit, einen Zeugenserver und ein Zeugenverzeichnis anzugeben. Wenn Sie einen Zeugenserver angeben, sollten Sie einen Clientzugriffsserver verwenden, auf dem die Postfachserverrolle nicht installiert ist. So ist einem Exchange-Administrator die Verfügbarkeit des Zeugenservers bewusst, und es ist sichergestellt, dass alle zum Verwenden des Zeugenservers erforderlichen erforderlichen Sicherheitsberechtigungen verfügbar sind.
    
    Die folgenden Kombinationen von Optionen und Verhalten sind verfügbar:
    
      - Sie können nur einen Namen für die DAG angeben und die Felder **Zeugenserver** und **Zeugenverzeichnis** leer lassen. In diesem Szenario sucht der Task nach einem Clientzugriffsserver, auf dem die Postfachserverrolle nicht installiert ist. Das Standardzeugenverzeichnis wird automatisch erstellt und auf diesem Clientzugriffsserver freigegeben, und die DAG wird für die Verwendung dieses Servers als Zeugenserver konfiguriert.
    
      - Sie können einen Namen für die Datenbankverfügbarkeitsgruppe, den Zeugenserver, den Sie verwenden möchten, sowie das Verzeichnis, das Sie erstellen und auf dem Zeugenserver freigeben möchten, angeben.
    
      - Sie können einen Namen für die DAG und den Zeugenserver angeben, den Sie verwenden möchten, und das Feld **Zeugenverzeichnis** leer lassen. In diesem Szenario erstellt der Task das Standardverzeichnis auf dem angegebenen Zeugenserver.
    
      - Sie können einen Namen für die DAG angeben, das Feld **Zeugenserver** leer lassen und das Verzeichnis angeben, das Sie auf dem Zeugenserver erstellen und freigeben möchten. In diesem Szenario sucht der Assistent nach einem Clientzugriffsserver, auf dem die Postfachserverrolle nicht installiert ist, und erstellt automatisch das angegebene Zeugenverzeichnis auf diesem Server. Er gibt das Verzeichnis frei und konfiguriert die DAG für die Verwendung dieses Clientzugriffsservers als Zeugenserver.
    

    > [!IMPORTANT]
    > Wenn der von Ihnen angegebene Zeugenserver kein Exchange 2013- oder Exchange 2010-Server ist, müssen Sie der lokalen Administratorgruppe auf dem Zeugenserver die universelle Exchange-Sicherheitsgruppe "Vertrauenswürdiges Subsystem" hinzufügen. Diese Sicherheitsrechte sind erforderlich, um sicherzustellen, dass mithilfe von Exchange ein Verzeichnis und eine Freigabe auf dem Zeugenserver bei Bedarf erstellt werden kann. Wenn die erforderlichen Berechtigungen nicht ordnungsgemäß konfiguriert werden, wird der folgende Fehler zurückgegeben:<BR><CODE>Error: An error occurred during discovery of the database availability group topology. Error: An error occurred while attempting a cluster operation. Error: Cluster API "AddClusterNode() (MaxPercentage=12) failed with 0x80070005. Error: Access is denied."</CODE>



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer Database Availability Group mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**.

2.  Klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine DAG zu erstellen.

3.  
    
    Geben Sie auf der Seite **Neue Database Availability Group** die folgenden Informationen für die DAG an:
    
      - **Database Availability Group-Name**   Geben Sie in diesem Feld einen gültigen und eindeutigen Namen für die DAG mit bis zu 15 Zeichen ein. Der Name entspricht einem Computernamen, und in Active Directory wird ein entsprechendes Clusternetzwerkobjekt (Cluster Network Object, CNO) mit diesem Namen erstellt. Dieser Name wird als Name der DAG und als Name des zugrunde liegenden Clusters verwendet.
    
      - **Zeugenserver**   Geben Sie in diesem Feld einen Zeugenserver für die DAG an. Wenn Sie dieses Feld leer lassen, versucht das System, automatisch einen Clientzugriffsserver im lokalen Active Directory-Standort auszuwählen, der nicht auf einem Computer mit dem als Zeugenserver zu verwendenden Postfachserver installiert ist.
        

        > [!NOTE]
        > Bei Angabe eines Zeugenservers müssen Sie einen Hostnamen oder einen vollqualifizierten Domänennamen angeben. Die Verwendung einer IP-Adresse oder eines Platzhalternamens wird nicht unterstützt. Ferner darf der angegebene Server kein Mitglied der DAG sein.

    
      - **Zeugenverzeichnis**   Geben Sie in diesem Feld den Pfad zu einem Verzeichnis auf dem Zeugenserver ein, in dem Zeugendaten gespeichert werden. Wenn das Verzeichnis nicht vorhanden ist, wird es durch das System auf dem Zeugenserver erstellt. Wenn Sie dieses Feld leer lassen, wird auf dem Zeugenserver das Standardverzeichnis ("%SystemDrive%\\DAGFileShareWitnesses\\\<DAG FQDN\>") erstellt.
    
      - **Database Availability Group-IP-Adressen**   Verwenden Sie dieses Feld, um der DAG mindestens eine statische IPv4-Adresse zuzuweisen. Geben Sie eine IPv4-Adresse ein, und klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um sie hinzuzufügen. Lassen Sie dieses Feld leer, wenn die DAG zum Abrufen der erforderlichen IPv4-Adressen DHCP (Dynamic Host Configuration Protocol) verwenden soll. Geben Sie optional "255.255.255.255" ein, um eine DAG ohne IP-Adresse oder Cluster-Administratorzugriffspunkt zu erstellen, was nur für DAGs gilt, die Postfachserver enthalten, auf denen Windows Server 2012 R2 ausgeführt wird.

4.  Klicken Sie auf **Speichern**, um die DAG zu erstellen.

## Erstellen einer Datenbankverfügbarkeitsgruppe mithilfe der Shell

In diesem Beispiel wird eine DAG namens "DAG1" erstellt, die für die Verwendung des Zeugenservers "FILESRV1" und des lokalen Verzeichnisses "C:\\DAG1" konfiguriert ist. Die Datenbankverfügbarkeitsgruppe "DAG1" wird zudem für die Verwendung von DHCP für ihre IP-Adressen konfiguriert.

    New-DatabaseAvailabilityGroup -Name DAG1 -WitnessServer FILESRV1 -WitnessDirectory C:\DAG1

In diesem Beispiel wird die Database Availability Group "DAG2" erstellt. Das System wählt automatisch einen Clientzugriffsserver im lokalen Active Directory-Standort aus, der die Postfachserverrolle nicht als Zeugenserver der DAG enthält. "DAG2" wird eine einzelne statische IP-Adresse zugewiesen, da sich in diesem Beispiel das MAPI-Netzwerk aller DAG-Mitglieder im selben Subnetz befindet.

    New-DatabaseAvailabilityGroup -Name DAG2 -DatabaseAvailabilityGroupIPAddresses 10.0.0.8

In diesem Beispiel wird die Database Availability Group "DAG3" erstellt. Die Datenbankverfügbarkeitsgruppe "DAG3" wird für die Verwendung des Zeugenservers "MBX2" und eines lokalen Verzeichnisses "C:\\DAG3" konfiguriert. "DAG3" werden mehrere statische IP-Adressen zugeordnet, da sich die DAG-Mitglieder im MAPI-Netzwerk in verschiedenen Subnetzen befinden.

    New-DatabaseAvailabilityGroup -Name DAG3 -WitnessServer MBX2 -WitnessDirectory C:\DAG3 -DatabaseAvailabilityGroupIPAddresses 10.0.0.8,192.168.0.8

In diesem Beispiel wird die DAG "DAG4" für die Verwendung von DHCP konfiguriert. Der Zeugenserver wird darüber hinaus durch das System automatisch ausgewählt, und das Standardzeugenverzeichnis wird erstellt.

    New-DatabaseAvailabilityGroup -Name DAG4

In diesem Beispiel wird die DAG "DAG5" erstellt, die keinen Administratorzugriffspunkt aufweist (nur für DAGs mit Windows Server 2012 R2 gültig). Darüber hinaus wird "MBX4" als Zeugenserver für die DAG verwendet, und das Standardzeugenverzeichnis wird erstellt.

    New-DatabaseAvailabilityGroup -Name DAG5 -DatabaseAvailabilityGroupIPAddresses ([System.Net.IPAddress]::None) -WitnessServer MBX4

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie erfolgreich eine DAG erstellt haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Database Availability Groups**. Die neu erstellte DAG wird angezeigt.

  - Führen Sie in der Shell folgenden Befehl aus, um zu überprüfen, ob die DAG erstellt wurde, und um die DAG-Eigenschaftsinformationen anzuzeigen:
    
        Get-DatabaseAvailabilityGroup <DAGName> | Format-List

## Weitere Informationen

[Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md)

[Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md)

[Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\))

[New-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351107\(v=exchg.150\))

[New-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd335225\(v=exchg.150\))

[Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd298049\(v=exchg.150\))

