---
title: 'Re-create the Discovery system mailbox: Exchange 2013 Help'
TOCTitle: Re-create the Discovery system mailbox
ms:assetid: 5ae8426b-5661-4ecb-99c4-cdd342107fb1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg588318(v=EXCHG.150)
ms:contentKeyID: 50475722
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Re-create the Discovery system mailbox

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2018-01-17_

Compliance-eDiscovery verwendet ein Systempostfach zum Speichern von Compliance-eDiscovery-Suchmetadaten. Dieses Discoverysystempostfach verwendet den Anzeigenamen **SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}**. Da Systempostfächer in der Exchange-Verwaltungskonsole oder in Exchange-Adresslisten nicht angezeigt werden, werden sie selten versehentlich gelöscht.

Wird das Discoverysystempostfach aber dennoch unbeabsichtigt gelöscht, können Discovery-Manager Compliance-eDiscovery-Suchvorgänge nicht mehr durchführen und auch vorhandene Suchen nicht mehr verwalten. In diesem Fall müssen Sie das Discoverysystempostfach neu erstellen, um die eDiscovery-Funktion zu aktivieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Verwenden der Shell zur Neuerstellung des Discoverysystempostfachs

1.  Löschen Sie das Benutzerkonto SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9} aus Active Directory, sofern es vorhanden ist. Standardmäßig erstellt das Setupprogramm von Exchange Server 2013 das Postfach im Benutzercontainer in Active Directory. Weitere Informationen zum Löschen eines Benutzerkontos aus Active Directory finden Sie unter [Löschen eines Benutzerkontos](https://go.microsoft.com/fwlink/p/?linkid=215850).

2.  Aktivieren des Discoverysystempostfachs mithilfe der Shell.
    

    > [!NOTE]
    > Die Exchange-Verwaltungskonsole kann nicht zum Aktivieren des Discoverysystempostfachs verwendet werden.<BR>Der folgende Befehl muss aus dem gleichen Verzeichnis ausgeführt werden, in dem Sie die Exchange-Installationsmedien extrahiert.

    
    Führen Sie den folgenden Befehl, um das Systempostfach Discovery neu zu erstellen:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

## Woher weiß ich, dass der Vorgang erfolgreich war?

Verwenden Sie das Cmdlet **Get-Mailbox** mit der Option *Arbitration* zum Abrufen von Systempostfächern, um die erfolgreiche Neuerstellung des Discoverysystempostfachs zu überprüfen. Zeigen Sie die Ergebnisse des Befehls an, um sicherzustellen, dass das Systempostfach `SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}` neu erstellt wurde.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


