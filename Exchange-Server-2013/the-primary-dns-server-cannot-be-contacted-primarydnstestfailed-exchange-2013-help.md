---
title: 'Der primäre DNS-Server kann nicht kontaktiert werden_PrimaryDNSTestFailed: Exchange 2013 Help'
TOCTitle: Der primäre DNS-Server kann nicht kontaktiert werden_PrimaryDNSTestFailed
ms:assetid: 5b39cb64-c8f1-4fd3-843b-ecd23f99fe3a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.primarydnstestfailed(v=EXCHG.150)
ms:contentKeyID: 50475750
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Der primäre DNS-Server kann nicht kontaktiert werden\_PrimaryDNSTestFailed

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, weil keine Verbindung mit dem primären DNS-Server (Domain Name System) hergestellt werden kann.

Für das Exchange 2007-Setup ist erforderlich, dass der lokale Computer mit der autorisierenden DNS-Datenbank der Domäne kommuniziert.

Microsoft Exchange benötigt DNS zum Auflösen der IP-Adresse des nächsten internen oder externen Zielservers.

Die Kommunikation mit dem primären DNS-Server kann aus folgenden Gründen fehlschlagen:

  - Die lokale TCP/IP-Konfiguration zeigt nicht auf den ordnungsgemäßen DNS-Server.

  - Der DNS-Server ist wegen eines Netzwerkfehlers oder aus anderen Gründen nicht verfügbar oder antwortet nicht.

So beheben Sie dieses Problem

  - Vergewissern Sie sich, dass die lokale TCP/IP-Konfiguration auf den ordnungsgemäßen DNS-Server zeigt.

**So überprüfen Sie die lokale TCP/IP-Konfiguration**

1.  Überprüfen Sie die lokale TCP/IP-Konfiguration:
    
    Weitere Informationen finden Sie unter „Konfigurieren von TCP/IP für die Verwendung von DNS“ ([https://go.microsoft.com/fwlink/?LinkId=68094](https://go.microsoft.com/fwlink/?linkid=68094)).

<!-- end list -->

  - Überprüfen Sie, ob der DNS-Server ausgeführt wird und kontaktiert werden kann.

**So überprüfen Sie, ob der DNS-Server ausgeführt wird und kontaktiert werden kann**

1.  Überprüfen Sie, ob der DNS-Server ausgeführt wird, indem Sie die folgenden Schritte ausführen:
    
      - Untersuchen Sie den Status des DNS-Servers mithilfe des DNS-Administrationsprogramms auf dem DNS-Server.
    
      - Starten Sie den DNS-Server neu.
        
        For more information, see „Starten, Beenden, Anhalten oder Neustarten eines DNS-Servers“ ([https://go.microsoft.com/fwlink/?LinkId=62999](https://go.microsoft.com/fwlink/?linkid=62999)).
    
      - Untersuchen Sie die Reaktionsbereitschaft des DNS-Servers mithilfe des Befehls **nslookup**.
        
        Weitere Informationen finden Sie unter „Überprüfen der Antwortbereitschaft eines DNS-Servers mithilfe des Befehls "nslookup"“ ([https://go.microsoft.com/fwlink/?LinkId=63000](https://go.microsoft.com/fwlink/?linkid=63000)).

