---
title: 'Festlegen der Anmeldeinformationen zur Verwendung mit dem Exchange UM-Problembehandlungstool: Exchange 2013 Help'
TOCTitle: Festlegen der Anmeldeinformationen zur Verwendung mit dem Exchange UM-Problembehandlungstool
ms:assetid: 542b7718-9345-40cc-bcb2-e307e70a1fa2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff630916(v=EXCHG.150)
ms:contentKeyID: 56271562
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen der Anmeldeinformationen zur Verwendung mit dem Exchange UM-Problembehandlungstool

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Das Microsoft Exchange 2010 UM-Problembehandlungstool ist ein Cmdlet der Exchange-Verwaltungsshell mit dem Namen **Test-ExchangeUMCallFlow**. Sie können das Cmdlet zur Diagnose von Konfigurationsfehlern in Szenarien mit Mailboxansage oder zum Testen der Voicemailfunktion verwenden, sowohl für lokale als auch für standortübergreifende UM-Bereitstellungen mit Microsoft Exchange Server 2010 Service Pack 1 (SP1) oder höher. Sie können dieses Cmdlet in Bereitstellungen mit Microsoft Office , Microsoft Lync Server 2010 oder später oder in UM-Bereitstellungen mit VoIP-Gateways, IP/PBX-Anlagen oder SBCs (Session Border Controller) verwenden.

Wenn Sie das UM-Problembehandlungstool ausführen, verwendet es standardmäßig die Anmeldeinformationen, die beim Anmelden am Computer verwendet wurden. Die verwendeten Anmeldeinformationen sind diejenigen, die für den anrufenden Teilnehmer angegeben sind. Sie müssen die Anmeldeinformationen festlegen oder angeben, wenn Sie das UM-Problembehandlungstool im `SIPClient`-Modus ausführen. Sie müssen die Anmeldeinformationen jedoch nicht festlegen, wenn Sie das UM-Problembehandlungstool im `Gateway`-Modus ausführen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "UM-Server" oder "UM-Dienste" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass Ihre Exchange 2010- oder Exchange 2013-Organisation die folgenden Anforderungen erfüllt:
    
      - Ein Satz UM-Wähleinstellungen wurde erstellt. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).
    
      - Eine UM-Postfachrichtlinie wurde erstellt. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).
    
      - Ein UM-IP-Gateway wurde erstellt. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).
    
      - Ein Exchange 2010 Unified MESSAGING-Server wurde mit dem UM-Wählplan hinzugefügt. Wenn Sie Exchange 2013 mit Lync Server verwenden, fügen Sie alle Clientzugriffs- und Postfachservern, die SIP-URI-Wählpläne. Ausführliche Schritte finden Sie unter [Hinzufügen einer UM-Servers zu einem Wählplan](https://go.microsoft.com/fwlink/p/?linkid=313051) oder [Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan](add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md).

  - Installieren des UM-Problembehandlungstools. Weitere Informationen finden Sie unter [Installieren des Exchange UM-Problembehandlungstools](install-the-exchange-um-troubleshooting-tool-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Wenn Sie den UM-Problembehandlungstool im <CODE>SIPClient</CODE> Modus verwenden, gibt es mehrere Office Communications Server 2007 R2 oder Microsoft Lync Server-Anforderungen und Voraussetzungen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=311961">Prüfliste: Bereitstellen von Office Communications Server 2007 R2 und Exchange 2010 Unified Messaging</A> oder <A href="checklist-integrate-exchange-2013-um-with-lync-server-exchange-2013-help.md">Prüfliste: Integrieren von Exchange 2013 UM in Lync Server</A>.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Festlegen der Anmeldeinformationen zur Verwendung mit dem UM-Problembehandlungstool

1.  Öffnen Sie im Menü **Start** das **Microsoft Exchange 2010 UM-Problembehandlungstool**.

2.  Geben Sie im Fenster **Microsoft Exchange 2010 UM-Problembehandlungstool** an der Eingabeaufforderung Folgendes ein, und drücken Sie die EINGABETASTE.
    
        $cred=Get-Credential

3.  Geben Sie im Fenster **Bei Windows PowerShell anmelden** den Domänen-\\Benutzernamen und das Kennwort ein, und klicken Sie dann auf **OK**.

4.  Geben Sie im Fenster **Microsoft Exchange 2010 UM-Problembehandlungstool** die erforderlichen Cmdlet-Parameter an, um den Anruffluss zu testen. Beispiel:
    
        Test-ExchangeUMCallFlow -Mode SIPClient -CallingParty tonysmith@contoso.com - CalledParty jamiestark@contoso.com NextHop ocsfe.contoso.com -Credential $cred

