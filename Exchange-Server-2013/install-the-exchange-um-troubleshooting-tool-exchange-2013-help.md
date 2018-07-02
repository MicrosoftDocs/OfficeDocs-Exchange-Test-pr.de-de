---
title: 'Installieren des Exchange UM-Problembehandlungstools: Exchange 2013 Help'
TOCTitle: Installieren des Exchange UM-Problembehandlungstools
ms:assetid: 84223af0-a717-49ee-add6-86313bb30d17
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff844714(v=EXCHG.150)
ms:contentKeyID: 56271570
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Installieren des Exchange UM-Problembehandlungstools

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das Microsoft Exchange 2010 UM-Problembehandlungstool ist ein Cmdlet der Exchange-Verwaltungsshell mit dem Namen **Test-ExchangeUMCallFlow**. Sie können das Cmdlet zur Diagnose von Konfigurationsfehlern in Szenarien mit Mailboxansage oder zum Testen der Voicemailfunktion verwenden, sowohl für lokale als auch für standortübergreifende UM-Bereitstellungen mit Microsoft Exchange Server 2010 Service Pack 1 (SP1) oder höher. Sie können dieses Cmdlet in Bereitstellungen mit Microsoft Office , Microsoft Lync Server 2010 oder später oder in UM-Bereitstellungen mit VoIP-Gateways, IP/PBX-Anlagen oder SBCs (Session Border Controller) verwenden.

Das UM-Problembehandlungstool kann auf einem lokalen Unified Messaging-Server, einem Exchange 2013-Postfachserver oder einem anderen 64-Bit-Computer installiert werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten

  - Für das UM-Problembehandlungstool ist die Installation der folgenden Komponenten auf einem Computer unter Windows Vista, Windows 7, Windows 8 oder der 64-Bit-Edition von Windows Server 2008 oder Windows Server 2012 oder höher erforderlich, bevor das Tool installiert wird:
    
      - Microsoft .NET Framework 3.5 Servicepack 1 (SP1) finden Sie unter [Microsoft .NET Framework 3.5 Servicepack 1](https://go.microsoft.com/fwlink/p/?linkid=152380).
    
      - Wenn das Tool auf einem Windows Vista oder Windows Server 2008 Computer ausgeführt wird, finden Sie unter [Update von Microsoft .NET Framework 3.5-Familie für Windows Vista X64, und Windows Server 2008 X64](https://go.microsoft.com/fwlink/p/?linkid=178998).
    
      - Windows-Remoteverwaltung (WinRM) 2.0 und Windows PowerShell V2 (Windows6.0-KB968930.msu). Informationen finden Sie im Microsoft Knowledge Base-Artikel 968930, [Windows-Verwaltungsframework-Kernpaket (Windows PowerShell 2.0 und WinRM 2.0)](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=968930).
    
      - Microsoft Unified Communications Managed API 2.0 Core Runtime (UcmaRuntimeWebDownloadX64.msi). Finden Sie unter [Unified Communications Managed API 2.0, Core Runtime (64-Bit)](https://go.microsoft.com/fwlink/p/?linkid=198175).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Installieren des UM-Problembehandlungstools

1.  Laden Sie das Unified Messaging-Problembehandlungstool aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=182625), und doppelklicken Sie dann auf den Installationsordner MicrosoftExchange2010UMTroubleshootingTool.msi.

2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.

3.  Überprüfen Sie auf der Seite **Endbenutzer-Lizenzvertrag** die angezeigten Lizenzbedingungen für die Software, und klicken Sie auf **Ich stimme den Bedingungen des Lizenzvertrags zu** und anschließend auf **Weiter**, wenn Sie zustimmen.

4.  Überprüfen Sie auf der Seite **Installationsordner auswählen** den Pfad zum Installationsordner, und klicken Sie auf **Weiter**.

5.  Klicken Sie auf der Seite **Installation bestätigen** auf **Weiter**, um die Installation zu starten.

6.  Klicken Sie auf der Seite **Die Installation ist abgeschlossen** auf **Schließen**.

