---
title: 'Konfigurieren der Routingtabellenprotokollierung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Routingtabellenprotokollierung
ms:assetid: 7184f8f7-4eb8-468a-aafe-b2d72868f820
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201696(v=EXCHG.150)
ms:contentKeyID: 50475938
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Routingtabellenprotokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

In Routingtabellenprotokollen wird regelmäßig eine Momentaufnahme der Routingtabelle erfasst, die von Microsoft Exchange Server 2013 zum Weiterleiten von Nachrichten an ihre Ziele verwendet wird.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" und "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Sie müssen die XML-Anwendungskonfigurationsdatei "EdgeTransport.exe.config" bearbeiten, um das Zeitintervall für die automatische Neuberechnung der Routingtabelle zu konfigurieren. Änderungen, die Sie in dieser Datei speichern, werden nach einem Neustart des Microsoft Exchange-Transportdiensts angewendet. Wenn Sie diesen Dienst neu starten, wird die Nachrichtenübermittlung auf dem Server zeitweise unterbrochen.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren der Routingtabellenprotokollierung mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-TransportService <ServerIdentity> -RoutingTableLogMaxAge <dd.hh:mm:ss> -RoutingTableLogMaxDirectorySize <Size>  -RoutingTableLogPath <LocalFilePath>

In diesem Beispiel werden folgende Einstellungen für Routingtabellenprotokolle auf dem Postfachserver "Mailbox01" festgelegt:

  - Legt den Speicherort für die Protokolldateien der Routingtabellen auf "D:\\Routing Table Log" fest. Beachten Sie, dass der Ordner für Sie erstellt wird, wenn er nicht vorhanden ist.

  - Legt die maximale Größe des Ordners für Routingtabellenprotokolle auf 70 MB fest.

  - Legt das maximale Alter einer Protokolldatei für Routingtabellen auf 45 Tage fest.

<!-- end list -->

    Set-TransportService Mailbox01 -RoutingTableLogPath "D:\Routing Table Log" -RoutingTableLogMaxDirectorySize 70MB -RoutingTableLogMaxAge 45.00:00:00


> [!NOTE]
> Wenn Sie den Parameter <EM>RoutingTableLogMaxAge</EM> auf den Wert <CODE>00:00:00</CODE> festlegen, wird verhindert, dass Protokolldateien für Routingtabellen aufgrund ihres Alters automatisch gelöscht werden.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Routingtabellenprotokollierung erfolgreich konfiguriert wurde:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
        Get-TransportService <ServerIdentity> | Format-List RoutingTableLog*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Konfigurieren des Zeitintervalls für die automatische Neuberechnung der Routingtabelle in der Datei "EdgeTransport.exe.config" mithilfe der Eingabeaufforderung

1.  Führen Sie an einer Eingabeaufforderung folgenden Befehl aus, um die Anwendungskonfigurationsdatei "EdgeTransport.exe.config" im Editor zu öffnen:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

2.  Ändern Sie im Abschnitt `<appSettings>` folgenden Schlüssel.
    
        <add key="RoutingConfigReloadInterval" value="<hh:mm:ss>" />
    
    Verwenden Sie z. B. folgenden Wert, um das Intervall für die automatische Neuberechnung der Routingtabelle in 10 Stunden zu ändern:
    
        <add key="RoutingConfigReloadInterval" value="10:00:00" />

3.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

4.  Starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:
    
        net stop MSExchangeTransport && net start MSExchangeTransport

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie überprüfen möchten, ob das Intervall für die automatische Neuberechnung der Routingtabelle erfolgreich konfiguriert wurde, vergewissern Sie sich, dass das Routingtabellenprotokoll im angegebenen Zeitintervall aktualisiert wird.

Beachten Sie, dass die Routingtabelle früher neuberechnet und protokolliert wird als durch den Wert des Schlüssels *RoutingConfigReloadInterval* angegeben, wenn eine der folgenden Bedingungen eintritt:

  - Eine Änderung der Routingkonfiguration wird erkannt. Dies ist z. B. der Fall, wenn ein Sendeconnector oder ein Empfangsconnector hinzugefügt, entfernt oder geändert wird oder das Kerberos-Token nach 6 Stunden erneuert wird.

  - Der Microsoft Exchange-Transportdienst wurde gestartet.

