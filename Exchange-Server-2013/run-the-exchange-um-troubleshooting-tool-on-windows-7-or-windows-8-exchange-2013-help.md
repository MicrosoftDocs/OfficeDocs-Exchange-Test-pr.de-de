---
title: 'Ausführen des Exchange UM-Problembehandlungstools unter Windows 7/Windows 8'
TOCTitle: Ausführen des Exchange UM-Problembehandlungstools unter Windows 7 oder Windows 8
ms:assetid: 98d6869d-ee4a-4088-849d-ef75b0f5d932
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff851872(v=EXCHG.150)
ms:contentKeyID: 56271572
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ausführen des Exchange UM-Problembehandlungstools unter Windows 7 oder Windows 8

 

_**Gilt für:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das Microsoft Exchange 2010 UM-Problembehandlungstool ist ein Cmdlet der Exchange-Verwaltungsshell mit dem Namen **Test-ExchangeUMCallFlow**. Sie können das Cmdlet zur Diagnose von Konfigurationsfehlern in Szenarien mit Mailboxansage oder zum Testen der Voicemailfunktion verwenden, sowohl für lokale als auch für standortübergreifende UM-Bereitstellungen mit Microsoft Exchange Server 2010 Service Pack 1 (SP1) oder höher. Sie können dieses Cmdlet in Bereitstellungen mit Microsoft Office , Microsoft Lync Server 2010 oder später oder in UM-Bereitstellungen mit VoIP-Gateways, IP/PBX-Anlagen oder SBCs (Session Border Controller) verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "UM-Server" oder "UM-Dienste" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass Ihre Exchange 2010- oder Exchange 2013-Organisation die folgenden Anforderungen erfüllt:
    
      - Ein Satz UM-Wähleinstellungen wurde erstellt. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).
    
      - Eine UM-Postfachrichtlinie wurde erstellt. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).
    
      - Ein UM-IP-Gateway wurde erstellt. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).
    
      - UM-Wählplan wurde ein Exchange 2010 Unified MESSAGING-Server hinzugefügt. Bei Verwendung von Exchange 2013 mit Lync Server fügen Sie alle Clientzugriffs- und Postfachservern hinzu, die SIP-URI-Wählpläne. Ausführliche Schritte finden Sie unter [Hinzufügen einer UM-Servers zu einem Wählplan](https://go.microsoft.com/fwlink/p/?linkid=313051) oder [Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan](add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md).

  - Wenn Sie das UM-Problembehandlungstool auf einem lokalen UM-Server mit Exchange 2010 SP1 oder höher bzw. auf einem Exchange 2013-Postfachserver ausführen, müssen Sie u. U. nicht alle unten aufgeführten Voraussetzungen installieren. Sie wurden möglicherweise bereits zusammen mit der UM-Serverrolle installiert. Wenn Sie das UM-Problembehandlungstool jedoch auf einem 64-Bit-Computer installieren, bei dem es sich nicht um einen Server handelt, auf dem die UM-Serverrolle ausgeführt wird, müssen Sie die folgenden Komponenten installieren:
    
      - Microsoft .NET Framework 3.5 Servicepack 1 (SP1). Finden Sie unter [Microsoft .NET Framework 3.5 Servicepack 1](https://go.microsoft.com/fwlink/p/?linkid=152380).
    
      - Wenn das Tool auf einem Computer Windows, Vista oder Windows Server 2008 ausgeführt werden wird, finden Sie unter [Update der Microsoft .NET Framework 3.5-Familie für Windows Vista X64, und Windows Server 2008 X64](https://go.microsoft.com/fwlink/p/?linkid=178998).
    
      - Windows-Remoteverwaltung (WinRM) 2.0 und Windows PowerShell V2 (Windows6.0-KB968930.msu). Informationen finden Sie im Microsoft Knowledge Base-Artikel 968930, [Windows-Verwaltungsframework-Kernpaket (Windows PowerShell 2.0 und WinRM 2.0)](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=968930).
    
      - Microsoft Unified Communications Managed API 2.0 Core Runtime (UcmaRuntimeWebDownloadX64.msi). Finden Sie unter [Unified Communications Managed API 2.0, Core Runtime (64-Bit)](https://go.microsoft.com/fwlink/p/?linkid=198175).

  - Laden Sie das UM-Problembehandlungstool herunter, und installieren Sie es.
    
      - Laden Sie [Unified Messaging-Problembehandlungstool](https://go.microsoft.com/fwlink/p/?linkid=182625) aus dem Microsoft Download Center herunter.
    
      - Installieren Sie das Tool. Weitere Informationen finden Sie unter [Installieren des Exchange UM-Problembehandlungstools](install-the-exchange-um-troubleshooting-tool-exchange-2013-help.md).
        

        > [!IMPORTANT]
        > Wenn Sie den UM-Problembehandlungstool im <CODE>SIPClient</CODE> Modus verwenden, gibt es mehrere andere Office Communications Server 2007 R2 oder Microsoft Lync Server-Anforderungen und Voraussetzungen erfüllen müssen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=311961">Prüfliste: Bereitstellen von Office Communications Server 2007 R2 und Exchange 2010 Unified Messaging</A>.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Ausführen des UM-Problembehandlungstools unter Windows Vista, Windows 7 oder Windows 8

1.  Klicken Sie auf **Start** \> **Allle Programme** \> **Zubehör** \> **Windows PowerShell**.

2.  Klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und wählen Sie aus dem Popupmenü **Als Administrator ausführen** aus.

3.  Wechseln Sie an der Windows PowerShell-Eingabeaufforderung zu dem Ordner, in dem das UM-Problembehandlungstool installiert wurde, und führen Sie den folgenden Befehl aus:
    
        C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -psconsolefile .\Microsoft.Exchange.UM.TroubleshootingToolsnapin.psc1 -noexit -command ". '.\Microsoft.Exchange.UM.TroubleshootingTool.ps1' "

4.  Wenn Sie das UM-Problembehandlungstool unter Windows Vista, Windows 7 oder Windows 8 ausführen, müssen Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl ausführen:
    
        Set-ExecutionPolicy RemoteSigned

5.  Öffnen Sie im Menü **Start** das **Microsoft Exchange 2010 UM-Problembehandlungstool**.

6.  Geben Sie im Fenster **Microsoft Exchange 2010 UM-Problembehandlungstool** an der Eingabeaufforderung Folgendes ein, und drücken Sie die EINGABETASTE.
    
        $cred=Get-Credential

7.  Geben Sie im Fenster **Bei Windows PowerShell anmelden** den Domänen-\\Benutzernamen und das Kennwort ein, und klicken Sie dann auf **OK**.

8.  Geben Sie im Fenster **Microsoft Exchange 2010 UM-Problembehandlungstool** die erforderlichen Cmdlet-Parameter an, um den Anruffluss zu testen. Beispiel:
    
        Test-ExchangeUMCallFlow -Mode SIPClient -CallingParty tonysmith@contoso.com - CalledParty jamiestark@contoso.com NextHop ocsfe.contoso.com -Credential $cred

