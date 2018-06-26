---
title: 'Wiederherstellen von Mitgliedsservern einer Datenbankverfügbarkeitsgruppe: Exchange 2013 Help'
TOCTitle: Wiederherstellen von Mitgliedsservern einer Datenbankverfügbarkeitsgruppe
ms:assetid: eccd8f61-9706-4bb7-a62a-ec7c166f8019
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638206(v=EXCHG.150)
ms:contentKeyID: 50476999
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederherstellen von Mitgliedsservern einer Datenbankverfügbarkeitsgruppe

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Wenn ein Postfachserver, der Mitglied einer Database Availability Group (DAG) ist, ausfällt oder ein anderer Fehler auftritt, sodass er nicht wiederhergestellt werden kann und ersetzt werden muss, können Sie eine Serverwiederherstellung durchführen. Microsoft Exchange Server 2013-Setup bietet die Option */m:RecoverServer*, die zum Durchführen der Serverwiederherstellung verwendet werden kann. Wenn Setup mit der Option */m:RecoverServer* ausgeführt wird, werden die Konfigurationsinformationen eines Servers mit dem gleichen Namen wie dem des Servers, auf Setup ausgeführt wird, aus Active Directory gelesen. Nachdem die Konfigurationsinformationen des Servers aus Active Directory erfasst wurden, werden die ursprünglichen Exchange-Dateien und -Dienste auf dem Server installiert, und die in Active Directory gespeicherten Rollen und Einstellungen werden auf den Server angewendet.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit DAGs gibt? Weitere Informationen finden Sie hier: [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Wenn Exchange nicht im Standardverzeichnis installiert wird, müssen Sie den Speicherort der Exchange-Programmdateien über die Option */TargetDir* für das Setup angeben. Wenn Sie die Option */TargetDir* nicht verwenden, werden die Exchange-Programmdateien im Standardverzeichnis (%programfiles%\\Microsoft\\Exchange Server\\V15) installiert.
    
    Führen Sie zum Ermitteln des Installationsverzeichnisses die folgenden Schritte aus:
    
    1.  Öffnen Sie **ADSIEDIT.MSC** oder **LDP.EXE**.
    
    2.  Navigieren Sie zu folgendem Verzeichnis: **CN=ExServerName,CN=Servers,CN=First Administrative Group,CN=Administrative Groups,CN=ExOrg Name,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=DomainName,CN=Com**
    
    3.  Klicken Sie mit der rechten Maustaste auf das Exchange-Serverobjekt, und klicken Sie dann auf **Eigenschaften**.
    
    4.  Suchen Sie nach dem Attribut **msExchInstallPath**. Dieses Attribut speichert den aktuellen Installationspfad.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden von Setup /m:RecoverServer zur Wiederherstellung eines Servers

1.  Abrufen von Wiedergabeverzögerungs- oder Abschneideverzögerungseinstellungen für Postfachdatenbankkopien auf dem wiederhergestellten Server mithilfe des Cmdlets [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)):
    
        Get-MailboxDatabase DB1 | Format-List *lag*

2.  Entfernen von Postfachdatenbankkopien auf dem wiederhergestellten Server mithilfe des Cmdlets [Remove-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335119\(v=exchg.150\)):
    
        Remove-MailboxDatabaseCopy DB1\MBX1

3.  Entfernen der Konfiguration des fehlerhaften Servers aus der DAG mithilfe des Cmdlets [Remove-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd297956\(v=exchg.150\)):
    
        Remove-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
    

    > [!NOTE]
    > Wenn das DAG-Mitglied, das entfernt wird, offline ist und nicht erneut online geschaltet werden kann, muss der Parameter <EM>ConfigurationOnly</EM> zum vorherigen Befehl hinzugefügt werden. Wenn Sie die Option <EM>ConfigurationOnly</EM> verwenden, müssen Sie den Knoten auch manuell aus dem Cluster entfernen.



4.  Zurücksetzen des Computerkontos des Servers in Active Directory. Weitere Informationen finden Sie unter [Zurücksetzen eines Computerkontos](http://go.microsoft.com/fwlink/p/?linkid=167188).

5.  Öffnen Sie ein Eingabeaufforderungsfenster. Führen Sie unter Verwendung der ursprünglichen Setupmedien den folgenden Befehl aus:
    
        Setup /m:RecoverServer

6.  Verwenden Sie nach Abschluss des Setupwiederherstellungsvorgangs das Cmdlet [Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd298049\(v=exchg.150\)), um den wiederhergestellten Server der DAG hinzuzufügen:
    
        Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1

7.  Nachdem der Server der DAG wieder hinzugefügt wurde, können Sie die Postfachdatenbankkopien mithilfe des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) neu konfigurieren. Wenn zuvor hinzugefügte Datenbankkopien über eine Wiedergabe- oder Abschneideverzögerung von mehr als 0 verfügten, können Sie diese Einstellungen mithilfe der Parameter *ReplayLagTime* und *TruncationLagTime* des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) neu konfigurieren:
    
        Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX1
        Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX1 -ReplayLagTime 3.00:00:00
        Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX1 -ReplayLagTime 3.00:00:00 -TruncationLagTime 3.00:00:00

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie das DAG-Mitglied erfolgreich wiederhergestellt haben:

  - Führen Sie in der Shell folgenden Befehl aus, um die Integrität und den Status des wiederhergestellten DAG-Mitglieds zu überprüfen:
    
        Test-ReplicationHealth <ServerName>
    
        Get-MailboxDatabaseCopyStatus -Server <ServerName>
    
    Sämtliche Statustests für die Replikation müssen erfolgreich ausgeführt werden, und die Statusangaben der Datenbanken und ihrer Inhaltsindizes müssen fehlerfrei sein.

