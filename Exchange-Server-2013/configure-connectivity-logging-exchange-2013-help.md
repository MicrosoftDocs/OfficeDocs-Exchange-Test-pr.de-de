---
title: 'Konfigurieren Sie die Protokollierung von Diensten: Exchange 2013 Help'
TOCTitle: Konfigurieren Sie die Protokollierung von Diensten
ms:assetid: 24e46a79-33ea-44e9-b03c-549db1c86a6f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996827(v=EXCHG.150)
ms:contentKeyID: 50475358
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die Protokollierung von Diensten

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-18_

Bei der Konnektivitätsprotokollierung wird die Aktivität ausgehender Verbindungen für die Übermittlung von Nachrichten von einem Transportdienst auf einem Exchange-Server aufgezeichnet. Im Rahmen der Konnektivitätsprotokollierung werden die Verbindungsquelle, das Ziel, die Anzahl von Nachrichten und übermittelten Bytes sowie Informationen zu Verbindungsfehlern erfasst.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst", "Front-End-Transport-Dienst" und "Postfachtransportdienst" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - In der Exchange-Verwaltungskonsole können Sie die Konnektivitätsprotokollierung aktivieren oder deaktivieren bzw. lediglich den Pfad des Konnektivitätsprotokolls angeben. Für alle anderen Konnektivitätsprotokollierungsoptionen in anderen Transportdiensten muss die Shell verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren der Konnektivitätsprotokollierung im Transportdienst mithilfe de Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie den Postfachserver aus, den Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **Transportprotokolle**.

4.  Ändern Sie im Abschnitt **Konnektivitätsprotokoll** nach Bedarf die folgenden Einstellungen:
    
      - **Konnektivitätsprotokoll aktivieren**   Deaktivieren Sie das Kontrollkästchen, um die Konnektivitätsprotokollierung auf dem Server zu deaktivieren. Zum Aktivieren der Konnektivitätsprotokollierung auf dem Server aktivieren Sie das Kontrollkästchen.
    
      - **Pfad des Konnektivitätsprotokolls**   Das angegebene Verzeichnis muss sich auf dem lokalen Exchange-Server befinden. Wenn der Ordner nicht vorhanden ist, wird er für Sie erstellt, wenn Sie auf **Speichern** klicken.
    
    Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren der Konnektivitätsprotokollierung mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Konnektivitätsprotokollierung zu konfigurieren:

    <Set-TransportService | Set-MailboxTransportService | Set-FrontEndTransportService> <ServerIdentity> -ConnectivityLogEnabled <$true | $false> -ConnectivityLogMaxAge <dd.hh:mm:ss> -ConnectivityLogMaxDirectorySize <Size> -ConnectivityLogMaxFileSize <Size> -ConnectivityLogPath <LocalFilePath>

In diesem Beispiel werden die Einstellungen für die Konnektivitätsprotokollierung im Transportdienst auf dem Postfachserver "Mailbox01" festgelegt:

  -  
    Legt den Speicherort der Konnektivitätsprotokolldateien auf "D:\\Hub Connectivity Log" fest. Beachten Sie, dass der Ordner für Sie erstellt wird, wenn er nicht vorhanden ist.

  -  
    Legt die maximale Größe einer Konnektivitätsprotokolldatei auf 20 MB fest.

  -  
    Legt die maximale Größe des Konnektivitätsprotokollverzeichnisses auf 1,5 GB fest.

  -  
    Legt das maximale Alter einer Konnektivitätsprotokolldatei auf 45 Tage fest.

<!-- end list -->

    Set-TransportService Mailbox01 -ConnectivityLogPath "D:\Hub Connectivity Log" -ConnectivityLogMaxFileSize 20MB -ConnectivityLogMaxDirectorySize 1.5GB -ConnectivityLogMaxAge 45.00:00:00


> [!NOTE]
> <UL>
> <LI>
> <P>Verwenden Sie das Cmdlet <STRONG>Set-MailboxTransportService</STRONG>, um die Einstellungen für das Konnektivitätsprotokoll im Postfachtransportdienst auf einem Postfachserver zu konfigurieren. Verwenden Sie das Cmdlet <STRONG>Set-FrontEndTransportService</STRONG>, um die Einstellungen für das Konnektivitätsprotokoll im Front-End-Transport-Dienst auf einem Clientzugriffsserver zu konfigurieren.</P>
> <LI>
> <P>Wenn Sie den Parameter <EM>ConnectivityLogPath</EM> auf <CODE>$null</CODE> festlegen, wird die Konnektivitätsprotokollierung deaktiviert. Lautet der Wert des Parameters <EM>ConnectivityLogEnabled</EM> jedoch <CODE>$true</CODE>, werden Fehler im Ereignisprotokoll generiert.</P>
> <LI>
> <P>Wenn Sie den Parameter <EM>ConnectivityLogMaxAge</EM> auf den Wert <CODE>00:00:00</CODE> festlegen, wird verhindert, dass Konnektivitätsprotokolldateien aufgrund ihres Alters automatisch gelöscht werden.</P></LI></UL>



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Konnektivitätsprotokollierung erfolgreich konfiguriert wurde:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
        <Get-TransportService | Get-FrontEndTransportService | Get-MailboxTransportService> <ServerIdentity> | Format-List ConnectivityLog*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

