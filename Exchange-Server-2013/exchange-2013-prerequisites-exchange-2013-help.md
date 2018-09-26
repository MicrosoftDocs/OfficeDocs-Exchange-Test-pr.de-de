---
title: 'Voraussetzungen für Exchange 2013: Exchange 2013 Help'
TOCTitle: Voraussetzungen für Exchange 2013
ms:assetid: e21cf744-7813-48b3-9293-5cecd89a6c25
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691354(v=EXCHG.150)
ms:contentKeyID: 50476939
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Voraussetzungen für Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-03-20_

In diesem Thema werden die Schritte zum Installieren der erforderlichen Komponenten der Betriebssysteme Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 mit Service Pack 1 (SP1) für die Postfach-, Clientzugriffs- und Edge-Transport-Serverrollen in Microsoft Exchange 2013 erläutert. Sie finden außerdem Informationen zu den Voraussetzungen für die Installation der Exchange 2013-Verwaltungstools auf Clientcomputern mit Windows 8, Windows 8.1 und Windows 7.

  - Was sollten Sie wissen, bevor Sie beginnen?

  - Active Directory-Vorbereitung

  - Voraussetzungen für Windows Server 2012 R2 und Windows Server 2012
    
      - Postfachserverrolle oder Clientzugriffs-Serverrolle
    
      - Edge-Transport-Serverrolle

  - Voraussetzungen für Windows Server 2008 R2 SP1
    
      - Postfachserverrolle oder Clientzugriffs-Serverrolle
    
      - Edge-Transport-Serverrolle

  - Voraussetzungen für Windows 7 (nur Verwaltungstools)

  - Voraussetzungen für Windows 8 und Windows 8.1 (nur Verwaltungstools)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Die Informationen in diesem Thema gelten für Service Pack 1 und höhere Versionen von Exchange 2013.

  - Die Edge-Transport-Serverrolle steht ab Exchange 2013 SP1 zur Verfügung.

  - Stellen Sie sicher, dass die Funktionsebene Ihrer Gesamtstruktur mindestens Windows Server 2003 entspricht und dass der Schemamaster Windows Server 2003 mit Service Pack 2 oder höher ausführt. Weitere Informationen zu Windows-Funktionsebenen finden Sie unter [Verwalten von Domänen und Gesamtstrukturen](https://go.microsoft.com/fwlink/p/?linkid=137037).

  - Die Option für die vollständige Installation von Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 SP1 muss für alle Server verwendet werden, auf denen Exchange 2013-Serverrollen oder -Verwaltungstools ausgeführt werden.

  - Sie müssen den Computer zuerst zu den entsprechenden internen Active Directory-Gesamtstrukturen und -Domänen hinzufügen.

  - Bei einigen Voraussetzungen müssen Sie den Server neu starten, um die Installation abzuschließen.

  - Installieren Sie die neuesten Windows-Updates auf Ihrem Computer. Weitere Informationen finden Sie unter [Prüfliste für Bereitstellungssicherheit](deployment-security-checklist-exchange-2013-help.md).
    

    > [!NOTE]
    > Wenn Sie die Postfachserverrolle installieren und der Server als Mitglied einer Database Availability Group (DAG) definiert werden soll, muss Windows Server 2012 R2 Standard oder Datacenter Edition, Windows Server 2012 Standard oder Datacenter Edition oder Windows Server 2008 R2 SP1 Enterprise Edition ausgeführt werden. Die Windows Server 2008 R2 SP 1 Standard Edition bietet keine Unterstützung für die Features, die für DAGs erforderlich sind.<BR>Sie können kein Upgrade für Windows durchführen, wenn Exchange auf dem Server installiert ist.<BR>Für das Upgrade auf Microsoft Unified Communications Managed API (UCMA) 4.0 müssen Sie zuerst alle vorherigen Versionen von UCMA über die Option <STRONG>Software</STRONG> deinstallieren.




> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Active Directory-Vorbereitung

Der Computer, den Sie für die Vorbereitung von Active Directory für Exchange 2013 verwenden möchten, muss bestimmte Voraussetzungen erfüllen.

Installieren Sie die folgende Software in der gezeigten Reihenfolge auf dem Computer, der für die Vorbereitung von Active Directory verwendet wird:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (im Funktionsumfang von Windows Server 2012 R2)

Nach der Installation der oben aufgeführten Software führen Sie die folgenden Schritte aus, um das Verwaltungspaket für Remotetools zu installieren. Nachdem Sie das Verwaltungspaket für Remotetools installiert haben, können Sie den Computer für die Vorbereitung von Active Directory verwenden. Weitere Informationen zum Vorbereiten von Active Directory finden Sie unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).

1.  Öffnen Sie Windows PowerShell.

2.  Installieren Sie das Verwaltungspaket für Remotetools.
    
      - Führen Sie auf einem Computer mit Windows Server 2012 R2 oder Windows Server 2012 den folgenden Befehl aus.
        
        ```powershell
        Install-WindowsFeature RSAT-ADDS
        ```
    
      - Führen Sie auf einem Computer mit Windows Server 2008 R2 SP1 den folgenden Befehl aus.
        
        ```powershell
        Add-WindowsFeature RSAT-ADDS
        ```

## Voraussetzungen für Windows Server 2012 R2 und Windows Server 2012

Die erforderlichen Voraussetzungen für die Installation von Exchange 2013 auf einem Computer mit Windows Server 2012 R2 oder Windows Server 2012 hängen davon ab, welche Exchange-Rollen Sie installieren möchten. Lesen Sie den Abschnitt unten zu den Rollen, die Sie installieren möchten.

## Postfachserverrolle oder Clientzugriffs-Serverrolle

Befolgen Sie die Anweisungen in diesem Abschnitt, um die erforderlichen Komponenten auf Computern mit Windows Server 2012 R2 oder Windows Server 2012 zu installieren, auf denen eine der folgenden Aktionen ausgeführt werden soll:

  - Installieren Sie nur die Postfachserverrolle auf einem Computer.

  - Installieren Sie nur die Clientzugriffs-Serverrolle auf einem Computer.

  - Installieren Sie die Postfachserverrolle und die Clientzugriffs-Serverrolle auf dem gleichen Computer.

Gehen Sie folgendermaßen vor, um die erforderlichen Windows-Rollen und -Features zu installieren:

1.  Öffnen Sie Windows PowerShell.

2.  Führen Sie den folgenden Befehl aus, um die erforderlichen Windows-Komponenten zu installieren.
    
    ```powershell
    Install-WindowsFeature AS-HTTP-Activation, Desktop-Experience, NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS
    ```

Nach der Installation der Betriebssystemrollen und -features installieren Sie folgende Softwareprodukte in der angegebenen Reihenfolge:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    

    > [!IMPORTANT]
    > Exchange 2013 CU16 und höher <STRONG>erfordert</STRONG> .NET Framework 4.6.2. Aktualisieren Sie die Server auf .NET Framework 4.6.2, bevor Sie Exchange 2013 CU16 installieren, oder Sie erhalten eine Fehlermeldung. Wenn .NET Framework 4.5.2 auf Ihren Exchange-Servern installiert ist, aktualisieren Sie Ihre Server vor der Installation von .NET Framework 4.6.2 auf Exchange 2013 CU15.



2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (im Funktionsumfang von Windows Server 2012 R2)

3.  [Microsoft Unified Communications Managed API 4.0, Core Runtime 64-Bit](https://go.microsoft.com/fwlink/p/?linkid=258269)

## Edge-Transport-Serverrolle

Befolgen Sie die Anweisungen in diesem Abschnitt, um die erforderlichen Komponenten auf Computern mit Windows Server 2012 R2 oder Windows Server 2012 R2 SP1 zu installieren, wenn Sie die Edge-Transport-Serverrolle auf einem Computer installieren möchten.

Gehen Sie folgendermaßen vor, um die erforderlichen Windows-Rollen und -Features zu installieren:

1.  Öffnen Sie Windows PowerShell.

2.  Führen Sie den folgenden Befehl aus, um die erforderlichen Windows-Komponenten zu installieren.
    
    ```powershell
    Install-WindowsFeature ADLDS
    ```

Installieren Sie die Version von Microsoft .NET Framework, die jener Version von Exchange 2013 entspricht, welche Sie installieren.

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    

    > [!IMPORTANT]
    > Exchange 2013 CU16 und höher <STRONG>erfordert</STRONG> .NET Framework 4.6.2. Aktualisieren Sie die Server auf .NET Framework 4.6.2, bevor Sie Exchange 2013 CU16 installieren, oder Sie erhalten eine Fehlermeldung. Wenn .NET Framework 4.5.2 auf Ihren Exchange-Servern installiert ist, aktualisieren Sie Ihre Server vor der Installation von .NET Framework 4.6.2 auf Exchange 2013 CU15.



2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (im Funktionsumfang von Windows Server 2012 R2)

## Voraussetzungen für Windows Server 2008 R2 SP1

Die erforderlichen Voraussetzungen für die Installation von Exchange 2013 auf einem Computer mit Windows Server 2008 R2 SP1 hängen davon ab, welche Exchange-Rollen Sie installieren möchten. Lesen Sie den Abschnitt unten zu den Rollen, die Sie installieren möchten.

## Postfachserverrolle oder Clientzugriffs-Serverrolle

Befolgen Sie die Anweisungen in diesem Abschnitt, um die Voraussetzungen auf Computern mit Windows Server 2008 R2 SP1 zu installieren, auf denen eine der folgenden Aktionen ausgeführt werden soll:

  - Installieren Sie nur die Postfachserverrolle auf einem Computer.

  - Installieren Sie nur die Clientzugriffs-Serverrolle auf einem Computer.

  - Installieren Sie die Postfachserverrolle und die Clientzugriffs-Serverrolle auf dem gleichen Computer.

Gehen Sie folgendermaßen vor, um die erforderlichen Windows-Rollen und -Features zu installieren:

1.  Öffnen Sie Windows PowerShell.

2.  Führen Sie den folgenden Befehl aus, um das Server-Manager-Modul zu laden.
    
    ```powershell
    Import-Module ServerManager
    ```

3.  Führen Sie den folgenden Befehl aus, um die erforderlichen Windows-Komponenten zu installieren.
    
    ```powershell
    Add-WindowsFeature Desktop-Experience, NET-Framework, NET-HTTP-Activation, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Web-Server, WAS-Process-Model, Web-Asp-Net, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, RSAT-ADDS
    ```
Nach der Installation der Betriebssystemrollen und -features installieren Sie folgende Softwareprodukte in der angegebenen Reihenfolge:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    

    > [!IMPORTANT]
    > Exchange 2013 CU16 und höher <STRONG>erfordert</STRONG> .NET Framework 4.6.2. Aktualisieren Sie die Server auf .NET Framework 4.6.2, bevor Sie Exchange 2013 CU16 installieren, oder Sie erhalten eine Fehlermeldung. Wenn .NET Framework 4.5.2 auf Ihren Exchange-Servern installiert ist, aktualisieren Sie Ihre Server vor der Installation von .NET Framework 4.6.2 auf Exchange 2013 CU15.



2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Microsoft Unified Communications Managed API 4.0, Core Runtime 64-Bit](https://go.microsoft.com/fwlink/p/?linkid=258269)

4.  [Microsoft Knowledge Base-Artikel KB974405: Beschreibung des Windows Identity Foundation (maschinelle Übersetzung)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=974405)

5.  [Knowledge Base-Artikel KB2619234: Ein Hotfix ist verfügbar, um die Zuordnung Cookie/GUID zu ermöglichen, die von RPC über HTTP verwendet wird, auch in der RPC-Schicht in Windows 7 und Windows Server 2008 R2 verwendet werden (maschinelle Übersetzung)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=2619234)

6.  [Knowledge Base-Artikel KB2533623: Microsoft-Sicherheitsempfehlung: Unsichere Bibliothekladevorgänge können eine Codeausführung von Remotestandorten aus ermöglichen](http://go.microsoft.com/fwlink/?linkid=3052&kbid=2533623)
    

    > [!NOTE]
    > Dieser Hotfix ist möglicherweise bereits installiert, wenn Sie Windows Update so konfiguriert haben, dass Sicherheitsupdates auf Ihrem Computer installiert werden.



## Edge-Transport-Serverrolle

Befolgen Sie die Anweisungen in diesem Abschnitt, um die Voraussetzungen auf Computern mit Windows Server 2008 R2 SP1 zu installieren, wenn Sie die Edge-Transport-Serverrolle auf einem Computer installieren möchten.

Gehen Sie folgendermaßen vor, um die erforderlichen Windows-Rollen und -Features zu installieren:

1.  Öffnen Sie Windows PowerShell.

2.  Führen Sie den folgenden Befehl aus, um das Server-Manager-Modul zu laden.
    
    ```powershell
    Import-Module ServerManager
    ```

3.  Führen Sie den folgenden Befehl aus, um die erforderlichen Windows-Komponenten zu installieren.
    
    ```powershell
    Add-WindowsFeature NET-Framework, ADLDS
    ```

Nach der Installation der Betriebssystemrollen und -features installieren Sie folgende Softwareprodukte in der angegebenen Reihenfolge:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    

    > [!IMPORTANT]
    > Exchange 2013 CU16 und höher <STRONG>erfordert</STRONG> .NET Framework 4.6.2. Aktualisieren Sie die Server auf .NET Framework 4.6.2, bevor Sie Exchange 2013 CU16 installieren, oder Sie erhalten eine Fehlermeldung. Wenn .NET Framework 4.5.2 auf Ihren Exchange-Servern installiert ist, aktualisieren Sie Ihre Server vor der Installation von .NET Framework 4.6.2 auf Exchange 2013 CU15.



2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Microsoft Unified Communications Managed API 4.0, Core Runtime 64-Bit](https://go.microsoft.com/fwlink/p/?linkid=258269)

## Voraussetzungen für Windows 7 (nur Verwaltungstools)

Befolgen Sie die Anweisungen in diesem Abschnitt, um die erforderlichen Komponenten auf zu Domänen gehörenden 64-Bit-Computern mit Windows 7 zu installieren, auf denen die Exchange-Verwaltungstools installiert werden sollen.

1.  Öffnen Sie die **Systemsteuerung**, und wählen Sie **Programme** aus.

2.  Klicken Sie auf **Windows-Features aktivieren oder deaktivieren**.

3.  Navigieren Sie zu **Internetinformationsdienste** \> **Webverwaltungstools** \> **IIS 6-Verwaltungskompatibilität**.

4.  Aktivieren Sie das Kontrollkästchen für **IIS 6-Verwaltungskonsole**, und klicken Sie auf **OK**.

Nach der Installation der Betriebssystemfeatures installieren Sie folgende Softwareprodukte in der angegebenen Reihenfolge:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Knowledge Base-Artikel KB974405: Beschreibung des Windows Identity Foundation (maschinelle Übersetzung)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=974405)

## Voraussetzungen für Windows 8 und Windows 8.1 (nur Verwaltungstools)

[.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

