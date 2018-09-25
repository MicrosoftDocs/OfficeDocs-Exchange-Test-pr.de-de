---
title: 'Verwenden einer Microsoft Azure-VM als DAG-Zeugenserver: Exchange 2013 Help'
TOCTitle: Verwenden einer Microsoft Azure-VM als DAG-Zeugenserver
ms:assetid: 03d1e215-518b-4b48-bfcd-8d187ff8f5ef
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn903504(v=EXCHG.150)
ms:contentKeyID: 63910991
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden einer Microsoft Azure-VM als DAG-Zeugenserver

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit Exchange Server 2013 können Sie Ihre Postfachdatenbanken in einer Database Availability Group (DAG) für ein automatisches Failover von Rechenzentren konfigurieren. Für diese Konfiguration sind drei separate physische Standorte erforderlich: zwei Rechenzentren für Postfachserver und ein dritter Standort zum Platzieren des Zeugenservers für die DAG. Organisationen mit nur zwei physischen Standorten können jetzt ebenfalls vom automatischen Failover von Rechenzentren profitieren, indem sie einen virtuellen Microsoft Azure-Dateiservercomputer verwenden, der als Zeugenserver der DAG agiert.

Der Schwerpunkt dieses Artikels liegt auf der Platzierung des DAG-Zeugenservers in Microsoft Azure. Es wird davon ausgegangen, dass Sie mit den Konzepten für die Ausfallsicherheit von Standorten vertraut sind und bereits über eine voll funktionsfähige DAG-Infrastruktur mit zwei Rechenzentren verfügen. Wenn Sie Ihre DAG-Infrastruktur noch nicht konfiguriert haben, wird empfohlen, dass Sie zunächst die folgenden Artikel lesen:

[Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md)

[Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md)

[Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten](planning-for-high-availability-and-site-resilience-exchange-2013-help.md)

## Änderungen in Microsoft Azure

Für diese Konfiguration ist ein VPN mit mehreren Standorten erforderlich. Es war schon immer möglich, das Netzwerk Ihrer Organisation über eine Standort-zu-Standort-VPN-Verbindung mit Microsoft Azure zu verbinden. In der Vergangenheit hat Azure jedoch nur ein einziges Standort-zu-Standort-VPN unterstützt. Da für das Konfigurieren einer DAG und ihres Zeugenservers über drei Rechenzentren mehrere Standort-zu-Standort-VPNs erforderlich sind, war die Platzierung des DAG-Zeugenservers auf einer Azure-VM anfänglich nicht möglich.

Im Juni 2014 wurde die Unterstützung für VPNs mit mehreren Standorten in Microsoft Azure eingeführt, mit der Organisationen mehrere Rechenzentren mit demselben virtuellen Azure-Netzwerk verbinden können. Diese Änderung ermöglichte auch Organisationen mit zwei Rechenzentren, Microsoft Azure als dritten Standort für die Platzierung der DAG-Zeugenserver zu nutzen. Weitere Informationen zum Feature für VPNs mit mehreren Standorten in Azure finden Sie unter [Konfigurieren eines VPNs mit mehreren Standorten](http://go.microsoft.com/fwlink/?linkid=522621).


> [!NOTE]
> Diese Konfiguration nutzt die virtuellen Azure-Computer und ein VPN mit mehreren Standorten für die Bereitstellung des Zeugenservers und verwendet nicht den Azure Cloud Witness.



## Microsoft Azure-Dateiserverzeuge

Das folgende Diagramm bietet eine Übersicht über die Verwendung einer Microsoft Azure-Dateiserver-VM als DAG-Zeuge. Sie benötigen ein virtuelles Azure-Netzwerk, ein VPN mit mehreren Standorten, das Ihre Rechenzentren mit Ihrem virtuellen Azure-Netzwerk verbindet, sowie einen Domänencontroller und einen Dateiserver, die auf virtuellen Azure-Computern bereitgestellt werden.


> [!NOTE]
> Es ist technisch möglich, eine einzige Azure-VM für diesen Zweck zu verwenden und die Dateizeugenfreigaben auf den Domänencontroller zu platzieren. Dies führt jedoch zu einer unnötigen Erhöhung von Berechtigungen. Daher ist dies keine empfohlene Konfiguration.



**DAG-Zeugenserver in Microsoft Azure**

![DAG-Zeuge von Exchange in der Azure-Übersicht](images/Dn903504.7cbda882-bbae-4be7-b0ea-60947b8aa4ef(EXCHG.150).png "DAG-Zeuge von Exchange in der Azure-Übersicht")

Zunächst müssen Sie ein Abonnement erwerben, um eine Microsoft Azure-VM für Ihren DAG-Zeugen verwenden zu können. Informationen zur besten Möglichkeit zum Erwerben eines Azure-Abonnements finden Sie unter [Azure erwerben](http://go.microsoft.com/fwlink/?linkid=398989).

Nachdem Sie Ihr Azure-Abonnement erworben haben, müssen Sie Folgendes in der angegebenen Reihenfolge ausführen:

1.  Vorbereiten des virtuellen Microsoft Azure-Netzwerks

2.  Konfigurieren eines VPN mit mehreren Standorten

3.  Konfigurieren von virtuellen Computern

4.  Konfigurieren des DAG-Zeugen


> [!NOTE]
> Ein erheblicher Anteil der Anweisungen in diesem Artikel beinhaltet eine Microsoft Azure-Konfiguration. Daher werden Links zur Azure-Dokumentation bereitgestellt, wann immer dies sinnvoll ist.



## Voraussetzungen

  - Zwei Rechenzentren, die eine Exchange-Bereitstellung mit hoher Verfügbarkeit und Ausfallsicherheit von Standorten unterstützen können. Weitere Informationen finden Sie unter [Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten](planning-for-high-availability-and-site-resilience-exchange-2013-help.md).

  - Eine öffentliche, nicht hinter NAT liegende IP-Adresse für die VPN-Gateways an jedem Standort

  - Ein VPN-Gerät an jedem Standort, das mit Microsoft Azure kompatibel ist. Weitere Informationen zu kompatiblen Geräten finden Sie unter [Informationen zu VPN-Geräten für virtuelle Netzwerke](http://go.microsoft.com/fwlink/?linkid=522619).

  - Erfahrung mit DAG-Konzepten und -Verwaltung

  - Erfahrung mit Windows PowerShell

## Phase 1: Vorbereiten des virtuellen Microsoft Azure-Netzwerks

Das Konfigurieren des Microsoft Azure-Netzwerks ist der wichtigste Teil des Bereitstellungsprozesses. Am Ende dieser Phase verfügen Sie über ein voll funktionsfähiges virtuelles Azure-Netzwerk, das mit Ihren beiden Rechenzentren über ein VPN mit mehreren Standorten verbunden ist.

## Registrieren von DNS-Servern

Da für diese Konfiguration eine Namensauflösung zwischen den lokalen Servern und Azure-VMs erforderlich ist, müssen Sie Azure für die Verwendung Ihrer eigenen DNS-Server konfigurieren. Im Thema [Namensauflösung (DNS)](http://msdn.microsoft.com/de-de/library/azure/jj156088.aspx) finden Sie eine Übersicht über Namensauflösung in Microsoft Azure.

Gehen Sie wie folgt vor, um Ihre DNS-Server zu registrieren:

1.  Wechseln Sie im Azure-Portal zu **Netzwerke**, und klicken Sie dann auf **NEU**.

2.  Klicken Sie auf **NETZWERKDIENSTE** \> **VIRTUELLES NETZWERK** \> **DNS-SERVER REGISTRIEREN**.

3.  Geben Sie den Namen und die IP-Adresse für Ihren DNS-Server ein. Der hier angegebene Name ist ein logischer Name, der im Verwaltungsportal verwendet wird und nicht mit dem tatsächlichen Namen Ihres DNS-Servers übereinstimmen muss.

4.  Wiederholen Sie die Schritte 1 bis 3 für alle anderen DNS-Server, die Sie hinzufügen möchten.
    

    > [!NOTE]
    > Die DNS-Server, die Sie registrieren, werden nicht nach dem Roundrobinverfahren verwendet. Azure-VMs verwenden den ersten aufgelisteten DNS-Server und benutzen zusätzliche Server nur, wenn der erste nicht verfügbar ist.



5.  Wiederholen Sie die Schritte 1 bis 3, um die IP-Adresse hinzuzufügen, die Sie für den in Microsoft Azure bereitgestellten Domänencontroller verwenden.

## Erstellen lokaler Netzwerkobjekte in Azure

Gehen Sie als Nächstes wie folgt vor, um logische Netzwerkobjekte zu erstellen, die Ihre Rechenzentren in Microsoft Azure darstellen:

1.  Wechseln Sie im Azure-Portal zu **Netzwerke**, und klicken Sie dann auf **NEU**.

2.  Klicken Sie auf **NETZWERKDIENSTE**\>**VIRTUELLES NETZWERK**\>**LOKALES NETZWERK HINZUFÜGEN**.

3.  Geben Sie den Namen für den ersten Rechenzentrumsstandort und die IP-Adresse des VPN-Geräts an diesem Standort ein. Diese IP-Adresse muss eine statische öffentliche IP-Adresse sind, die sich nicht hinter NAT befindet.

4.  Geben Sie auf dem nächsten Bildschirm die IP-Subnetze für den ersten Standort ein.

5.  Wiederholen Sie die Schritte 1 bis 4 für den zweiten Standort.

## Erstellen des virtuellen Azure-Netzwerks

Führen Sie nun Folgendes aus, um ein virtuelles Azure-Netzwerk zu erstellen, das von den VMs verwendet wird:

1.  Wechseln Sie im Azure-Portal zu **Netzwerke**, und klicken Sie dann auf **NEU**.

2.  Klicken Sie auf **NETZWERKDIENSTE**\>**VIRTUELLES NETZWERK**\>**BENUTZERDEFINIERTE ERSTELLEN**.

3.  Geben Sie auf der Seite **Details zum virtuellen Netzwerk** einen Namen für das virtuelle Netzwerk an, und wählen Sie einen geographischen Standort für das Netzwerk aus.

4.  Überprüfen Sie auf der Seite **DNS-Server und VPN-Konnektivität**, ob die zuvor registrierten DNS-Server als DNS-Server aufgeführt sind.

5.  Aktivieren Sie unter **Site-to-Site-Konnektivität** das Kontrollkästchen **Ein Site-to-Site-VPN konfigurieren**.
    

    > [!IMPORTANT]
    > Wählen Sie nicht <STRONG>ExpressRoute verwenden</STRONG> aus, da dadurch die erforderlichen Konfigurationsänderungen verhindert werden, die zum Einrichten eines VPN mit mehreren Standorten erforderlich sind.



6.  Wählen Sie unter **LOKALES NETZWERK** eines der beiden lokalen Netzwerke aus, die Sie konfiguriert haben.

7.  Geben Sie auf der Seite **Virtuelle Netzwerkadressräume** den IP-Adressbereich an, den Sie für Ihr virtuelles Azure-Netzwerk verwenden möchten.

## Checkpoint: Überprüfen der Netzwerkkonfiguration

Wenn Sie zu diesem Zeitpunkt zu **Netzwerke** wechseln, sollten das von Ihnen konfigurierte virtuelle Netzwerk unter **VIRTUELLE NETZWERKE**, Ihre lokalen Standorte unter **LOKALE NETZWERKE** und die registrierten DNS-Server unter **DNS-SERVER** angezeigt werden.

## Phase 2: Konfigurieren eines VPN mit mehreren Standorten

Im nächsten Schritt richten Sie die VPN-Gateways zu Ihren lokalen Standorten ein. Dafür müssen Sie Folgendes ausführen:

1.  Einrichten eines VPN-Gateways zu einem Ihrer Standorte mithilfe des Azure-Portals

2.  Exportieren der Konfigurationseinstellungen des virtuellen Netzwerks

3.  Ändern der Konfigurationsdatei für das VPN mit mehreren Standorten

4.  Importieren der aktualisierten Azure-Netzwerkkonfiguration

5.  Aufzeichnen der Azure-Gateway-IP-Adresse und der vorinstallierten Schlüssel

6.  Konfigurieren der lokalen VPN-Geräte

Weitere Informationen zum Konfigurieren eines VPN mit mehreren Standorten finden Sie unter [Konfigurieren eines VPNs mit mehreren Standorten](http://go.microsoft.com/fwlink/?linkid=522621).

## Einrichten eines VPN-Gateways für den ersten Standort

Beachten Sie beim Erstellen des virtuellen Gateways, dass Sie bereits angegeben haben, dass dieses mit Ihrem ersten lokalen Standort verbunden werden soll. Wenn Sie das Dashboard des virtuellen Netzwerks öffnen, sehen Sie, dass das Gateway nicht erstellt wurde.

Befolgen Sie zum Einrichten des VPN-Gateways auf der Azure-Seite die Anweisungen im Abschnitt [Starten Sie das Gateway des virtuellen Netzwerks](http://msdn.microsoft.com/de-de/library/azure/jj156210.aspx#bkmk+_startgateway) unter [Konfigurieren eines Gateways für ein virtuelles Netzwerk im Verwaltungsportal](http://msdn.microsoft.com/de-de/library/azure/jj156210.aspx).


> [!IMPORTANT]
> Führen Sie nur die Schritte im Abschnitt „Starten Sie das Gateway des virtuellen Netzwerks“ des Artikels, und fahren Sie nicht mit den nachfolgenden Abschnitten fort.



## Exportieren der Konfigurationseinstellungen des virtuellen Netzwerks

Im Azure-Verwaltungsportal können Sie derzeit kein VPN mit mehreren Standorten konfigurieren. Für diese Konfiguration müssen Sie die Konfigurationseinstellungen für das virtuelle Netzwerk in eine XML-Datei exportieren und dann diese Datei ändern. Befolgen Sie die Anweisungen unter [Exportieren von Einstellungen virtueller Netzwerke in eine Netzwerkkonfigurationsdatei](http://msdn.microsoft.com/de-de/library/azure/dn133804.aspx), um Ihre Einstellungen zu exportieren.

## Ändern der Netzwerkkonfigurationseinstellungen für das VPN mit mehreren Standorten

Öffnen Sie die exportierte Datei in einem beliebigen XML-Editor. Die Gatewayverbindungen zu Ihren lokalen Standorten sind im Abschnitt „ConnectionsToLocalNetwork“ aufgeführt. Suchen Sie in der XML-Datei nach diesem Begriff, um den Abschnitt zu finden. Dieser Abschnitt in der Konfigurationsdatei sieht wie folgt aus (vorausgesetzt, dass der Standortname, den Sie für Ihren lokalen Standort erstellt haben, „Site A“ lautet).

```powershell
    <ConnectionsToLocalNetwork>
    
        <LocalNetworkSiteRef name="Site A">
    
            <Connection type="IPsec" />
    
    </LocalNetworkSiteRef>
```

Fügen Sie zum Konfigurieren des zweiten Standorts einen weiteren Abschnitt „LocalNetworkSiteRef“ unter dem Abschnitt „ConnectionsToLocalNetwork“ hinzu. Der Abschnitt in der aktualisierten Konfigurationsdatei sieht wie folgt aus (unter der Annahmen, dass der Standortname für den zweiten lokalen Standort „Site B“ lautet).

```powershell
    <ConnectionsToLocalNetwork>
    
        <LocalNetworkSiteRef name="Site A">
    
            <Connection type="IPsec" />
    
        <LocalNetworkSiteRef name="Site B">
    
            <Connection type="IPsec" />
    
    </LocalNetworkSiteRef>
```

Speichern Sie die aktualisierte Datei mit den Konfigurationseinstellungen.

## Importieren der Konfigurationseinstellungen des virtuellen Netzwerks

Die zweite Standortreferenz, die Sie zur Konfigurationsdatei hinzugefügt haben, löst aus, dass Microsoft Azure einen neuen Tunnel erstellt. Importieren Sie die aktualisierte Datei mithilfe der Anweisungen unter [Importieren einer Netzwerkkonfigurationsdatei](http://msdn.microsoft.com/de-de/library/azure/jj156213.aspx). Nach Abschluss des Importvorgangs werden die Gatewayverbindungen zu beiden lokalen Standorten im Dashboard des virtuellen Netzwerks angezeigt.

## Aufzeichnen der Azure-Gateway-IP-Adresse und der vorinstallierten Schlüssel

Nachdem die neuen Netzwerkkonfigurationseinstellungen importiert wurden, wird im Dashboard des virtuellen Netzwerks die IP-Adresse für das Azure-Gateway angezeigt. Dies ist die IP-Adresse, mit der sich die VPN-Geräte an beiden Standorten verbinden. Zeichnen Sie diese IP-Adresse zu Referenzzwecken auf.

Sie müssen außerdem die vorinstallierten IPsec/IKE-Schlüssel für jeden erstellten Tunnel abrufen. Sie verwenden diese Schlüssel zusammen mit der Azure-Gateway-IP-Adresse, um Ihre lokalen VPN-Geräte zu konfigurieren.

Sie müssen PowerShell verwenden, um die vorinstallierten Schlüssel abzurufen. Wenn Sie nicht mit der Verwendung von PowerShell zum Verwalten von Azure vertraut sind, finden Sie weitere Informationen unter [Azure PowerShell](http://msdn.microsoft.com/de-de/library/azure/jj156055.aspx).

Verwenden Sie das Cmdlet [Get-AzureVNetGatewayKey](http://msdn.microsoft.com/de-de/library/azure/dn495198.aspx), um die vorinstallierten Schlüssel zu extrahieren. Führen Sie dieses Cmdlet für jeden Tunnel einmal aus. Das folgende Beispiel zeigt die Befehle, die Sie ausführen, um die Schlüssel für Tunnel zwischen dem virtuellen Netzwerk „Azure Site“ und den Standorten „Site A“ und „Site B“ zu extrahieren. In diesem Beispiel werden die Ausgaben in separaten Dateien gespeichert. Alternativ können Sie diese Schlüssel an andere PowerShell-Cmdlets weiterleiten oder in einem Skript verwenden.

```powershell
    Get-AzureVNETGatewayKey -VNetName "Azure Site" -LocalNetworkSiteName "Site A" > C:\Keys\KeysForTunnelToSiteA.txt 
```
```powershell
    Get-AzureVNETGatewayKey -VNetName "Azure Site" -LocalNetworkSiteName "Site B" > C:\Keys\KeysForTunnelToSiteB.txt
```

## Konfigurieren der lokalen VPN-Geräte

Microsoft Azure stellt Skripts für die VPN-Gerätekonfiguration für unterstützte VPN-Geräte bereit. Klicken Sie auf den Link **VPN-Geräteskript herunterladen** im Dashboard des virtuellen Netzwerks für das entsprechende Skript für Ihre VPN-Geräte.

Das Skript, das Sie herunterladen, enthält die Konfigurationseinstellung für den ersten Standort, den Sie beim Einrichten eines virtuellen Netzwerks konfiguriert haben, und kann ohne weitere Konfiguration verwendet werden, um das VPN-Gerät für diesen Standort zu konfigurieren. Wenn Sie beispielsweise beim Erstellen des virtuellen Netzwerks „Site A“ als **LOKALES NETZWERK** angegeben haben, kann das VPN-Geräteskript für Standort A verwendet werden. Sie müssen das Skript jedoch ändern, um das VPN-Gerät für Standort B zu konfigurieren. Sie müssen insbesondere den vorinstallierten Schlüssel so aktualisieren, dass er dem Schlüssel für den zweiten Standort entspricht.

Wenn Sie beispielsweise ein RRAS-VPN-Gerät (Routing and Remote Access Service) für Ihre Standorte verwenden, müssen Sie folgende Schritte ausführen:

1.  Öffnen Sie das Skript in einem Texteditor.

2.  Suchen Sie nach dem Abschnitt `#Add S2S VPN interface`.

3.  Suchen Sie nach dem Befehl **Add-VpnS2SInterface** in diesem Abschnitt. Überprüfen Sie, ob der Wert für den Parameter *SharedSecret* mit dem vorinstallierten Schlüssel für den Standort übereinstimmt, für den Sie das VPN-Gerät konfigurieren.

Für andere Geräte sind möglicherweise zusätzliche Überprüfungen erforderlich. Die Konfigurationsskripts für Cisco-Geräte legen z. B. ACL-Regeln mithilfe der lokalen IP-Adressbereiche fest. Sie müssen alle Verweise auf den lokalen Standort im Konfigurationsskript überprüfen und bestätigen, bevor Sie es verwenden. Weitere Informationen finden Sie in den folgenden Themen:

[Vorlagen für den Routing- und RAS-Dienst (RRAS)](http://msdn.microsoft.com/de-de/library/azure/dn133801.aspx)

[Cisco ASR-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133802.aspx)

[Cisco ISR-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133800.aspx)

[Juniper SRX-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133794.aspx)

[Juniper J-Series-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133799.aspx)

[Juniper ISG-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133797.aspx)

[Juniper SSG-Vorlagen](http://msdn.microsoft.com/de-de/library/azure/dn133796.aspx)

## Checkpoint: Überprüfen des VPN-Status

An diesem Punkt sind beide Standorte über die VPN-Gateways mit Ihrem virtuellen Azure-Netzwerk verbunden. Sie können den Status des VPN mit mehreren Standorten mithilfe des folgenden Befehls in PowerShell überprüfen.

```powershell
    Get-AzureVnetConnection -VNetName "Azure Site" | Format-Table LocalNetworkSiteName, ConnectivityState
```

Wenn beide Tunnel ausgeführt werden, sieht die Ausgabe dieses Befehls wie folgt aus.

```powershell
    LocalNetworkSiteName    ConnectivityState
    
    --------------------    -----------------
    
    Site A                  Connected
    
    Site B                  Connected
```

Sie können auch die Konnektivität überprüfen, indem Sie das Dashboard des virtuellen Netzwerks im Azure-Verwaltungsportal anzeigen. In der Spalte **STATUS** wird für beide Standorte **Verbunden** angezeigt.


> [!NOTE]
> Es kann mehrere Minuten nach der erfolgreichen Herstellung der Verbindung dauern, bis die Statusänderung im Azure-Verwaltungsportal angezeigt wird.



## Phase 3: Konfigurieren von virtuellen Computern

Sie müssen mindestens zwei virtuelle Computer in Microsoft Azure für diese Bereitstellung erstellen: einen Domänencontroller und einen Dateiserver, der als DAG-Zeuge fungiert.

1.  Erstellen Sie virtuelle Computer für Ihren Domänencontroller und Ihren Dateiserver mithilfe der Anleitungen unter [Erstellen eines virtuellen Computers unter Windows](http://azure.microsoft.com/de-de/documentation/articles/virtual-machines-windows-tutorial/). Stellen Sie sicher, dass Sie das virtuelle Netzwerk auswählen, das Sie für **REGION/AFFINITÄTSGRUPPE/VIRTUELLES NETZWERK** erstellt haben, wenn Sie die Einstellungen für die virtuellen Computer angeben.

2.  Geben Sie bevorzugte IP-Adressen für den Domänencontroller und den Dateiserver über Azure PowerShell an. Wenn Sie eine bevorzugte IP-Adresse für einen virtuellen Computer angeben, muss sie aktualisiert werden, wofür ein Neustart des virtuellen Computers erforderlich ist. Im folgenden Beispiel werden die IP-Adressen für Azure-DC und Azure-FSW auf 10.0.0.10 bzw. 10.0.0.11 festgelegt.
    
    ```powershell
        Get-AzureVM Azure-DC | Set-AzureStaticVNetIP -IPAddress 10.0.0.10 | Update-AzureVM
    ```
    ```powershell
        Get-AzureVM Azure-FSW | Set-AzureStaticVNetIP -IPAddress 10.0.0.11 | Update-AzureVM
    ```

    > [!NOTE]
    > Ein virtueller Computer mit einer bevorzugten IP-Adresse versucht, diese Adresse zu verwenden. Wenn die Adresse jedoch einer anderen VM zugewiesen wurde, wird die VM mit der Konfiguration für die bevorzugte IP-Adresse nicht gestartet. Um diese Situation zu vermeiden, stellen Sie sicher, dass die verwendete IP-Adresse keinem anderen virtuellen Computer zugeordnet ist. Weitere Informationen finden Sie unter <A href="http://msdn.microsoft.com/de-de/library/azure/dn630228.aspx">Konfigurieren einer statischen internen IP-Adresse für einen virtuellen Computer</A>.



3.  Stellen Sie die Domänencontroller-VM in Azure unter Verwendung der von Ihrer Organisation verwendeten Standards bereit.

4.  Bereiten Sie den Dateiserver mit den Voraussetzungen für einen Exchange-DAG-Zeugen vor:
    
    1.  Fügen Sie die Dateiserverrolle mithilfe des Assistenten zum Hinzufügen von Rollen und Features oder des Cmdlets [Add-WindowsFeature](http://technet.microsoft.com/de-de/library/ee662309.aspx) hinzu.
    
    2.  Fügen Sie die universelle Sicherheitsgruppe des vertrauenswürdigen Teilsystems in Exchange zur lokalen Administratorgruppe hinzu.

## Checkpoint: Überprüfen des Status virtueller Computer

An diesem Punkt sollten Ihre virtuellen Computer ausgeführt werden und mit Servern in beiden lokalen Rechenzentren kommunizieren können:

  - Stellen Sie sicher, dass der Domänencontroller in Azure mit Ihren lokalen Domänencontrollern repliziert.

  - Überprüfen Sie, ob Sie den Dateiserver in Azure nach Namen erreichen und eine SMB-Verbindung von Ihren Exchange-Servern herstellen können.

  - Stellen Sie sicher, dass Sie Ihre Exchange-Server nach Namen vom Dateiserver in Azure erreichen können.

## Phase 4: Konfigurieren des DAG-Zeugen

Abschließend müssen Sie Ihre DAG für die Verwendung der neuen Zeugenservers konfigurieren. Standardmäßig verwendet Exchange "C:\\DAGFileShareWitnesses" als Pfad für den Dateifreigabenzeugen auf Ihrem Zeugenserver. Wenn Sie einen benutzerdefinierten Dateipfad verwenden, sollten Sie auch das Zeugenverzeichnis für die jeweilige Freigabe aktualisieren.

1.  Stellen Sie eine Verbindung mit Exchange-Verwaltungsshell her.

2.  Führen Sie den folgenden Befehl aus, um den Zeugenserver für Ihre DAGs zu konfigurieren.
    
    ```powershell
    Set-DatabaseAvailabilityGroup -Identity DAG1 -WitnessServer Azure-FSW
    ```

Weitere Informationen finden Sie in den folgenden Themen:

[Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md)

[Set-DatabaseAvailabilityGroup](http://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\).aspx)

## Checkpoint: Überprüfen des DAG-Dateifreigabenzeugen

An diesem Punkt haben Sie die DAG für die Verwendung des Dateiservers in Azure als DAG-Zeugen konfiguriert. Führen Sie Folgendes aus, um Ihre Konfiguration zu überprüfen:

1.  Überprüfen Sie die DAG-Konfiguration mithilfe des folgenden Befehls.
    
    ```powershell
        Get-DatabaseAvailabilityGroup -Identity DAG1 -Status | Format-List Name, WitnessServer, WitnessDirectory, WitnessShareInUse
    ```

    Überprüfen Sie, ob der Parameter *WitnessServer* auf den Dateiserver in Azure festgelegt ist, der Parameter *WitnessDirectory* auf den richtigen Pfad festgelegt ist und der Parameter *WitnessShareInUse* den Wert **Primary** anzeigt.

2.  Wenn die DAG über eine gerade Anzahl von Knoten verfügt, wird der Dateifreigabenzeuge konfiguriert. Überprüfen Sie die Einstellung für den Dateifreigabenzeuge in den Clustereigenschaften mithilfe des folgenden Befehls. Der Wert für den Parameter *SharePath* muss auf den Dateiserver verweisen und den richtigen Pfad anzeigen.
    
    ```powershell
    Get-ClusterResource -Cluster MBX1 | Get-ClusterParameter | Format-List
    ```

3.  Überprüfen Sie als Nächstes den Status der Clusterressource „File Share Witness“ mithilfe des folgenden Befehls. Der *State* der Clusterressource muss **Online** anzeigen.
    
    ```powershell
    Get-ClusterResource -Cluster MBX1
    ```

4.  Stellen Sie abschließend sicher, dass die Freigabe erfolgreich auf dem Dateiserver erstellt wurde, indem Sie den Ordner im Datei-Explorer und die Freigaben im Server-Manager überprüfen.

## Siehe auch


[Planen einer hohen Verfügbarkeit und Ausfallsicherheit von Standorten](planning-for-high-availability-and-site-resilience-exchange-2013-help.md)  
[Switchover und Failover](switchovers-and-failovers-exchange-2013-help.md)  
[Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md)

