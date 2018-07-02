---
title: 'Konfigurieren der Antispam-Agent-Protokollierung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Antispam-Agent-Protokollierung
ms:assetid: df157ca3-ad8e-4302-acbc-5fbb8570c21d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691337(v=EXCHG.150)
ms:contentKeyID: 50476887
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Antispam-Agent-Protokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Agent-Protokollierung zeichnet die Aktionen auf, die von bestimmten Exchange-Antispam-Agents ausgeführt werden. Welche Informationen in das Agent-Protokoll geschrieben werden, hängt vom Agent, vom SMTP-Ereignis und von der für die Nachricht ausgeführten Aktion ab.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" und "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktivieren der Antispam-Agent-Protokollierung mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-TransportService <ServerIdentity> -AgentLogEnabled <$true | $false> -AgentLogMaxAge <dd.hh:mm:ss> -AgentLogMaxDirectorySize <Size> -AgentLogMaxFileSize <Size> -AgentLogPath <LocalFilePath>

In diesem Beispiel werden folgende Agent-Protokolleinstellungen auf dem Postfachserver "Mailbox01" festgelegt:

  -  
    Legt den Speicherort der Agent-Protokolldateien auf "D:\\Anti-Spam Agent Log" fest. Beachten Sie, dass der Ordner für Sie erstellt wird, wenn er nicht vorhanden ist.

  -  
    Legt die maximale Größe einer Agent-Protokolldatei auf 20 MB fest.

  -  
    Legt die maximale Größe des Agent-Protokollverzeichnisses auf 400 MB fest.

  -  
    Legt das Höchstalter einer Agent-Protokolldatei auf 14 Tage fest.

<!-- end list -->

    Set-TransportService Mailbox01 -AgentLogPath "D:\Anti-Spam Agent Log" -AgentLogMaxFileSize 20MB -AgentLogMaxDirectorySize 400MB -AgentLogMaxAge 14.00:00:00


> [!NOTE]
> <UL>
> <LI>
> <P>Wenn Sie den Parameter <EM>AgentLogPath</EM> auf <CODE>$null</CODE> festlegen, wird die Agent-Protokollierung deaktiviert. Wenn Sie <EM>AgentLogPath</EM> hingegen auf <CODE>$null</CODE> festlegen, wenn der Parameter <EM>AgentLogEnabled</EM> den Wert <CODE>$true</CODE> aufweist, werden Fehler im Ereignisprotokoll protokolliert. Die bevorzugte Methode zum Deaktivieren der Agent-Protokollierung besteht darin, <EM>AgentLogEnabled</EM> auf <CODE>$false</CODE> festzulegen.</P>
> <LI>
> <P>Wenn Sie den Parameter <EM>AgentLogMaxAge</EM> auf den Wert <CODE>00:00:00</CODE> festlegen, wird verhindert, dass Agent-Protokolldateien aufgrund ihres Alters automatisch gelöscht werden.</P></LI></UL>



Ausführliche Informationen zu Syntax und Parametern finden Sie unter den *AgentLog*-Parametern in [Set-TransportService](https://technet.microsoft.com/de-de/library/jj215682\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die Antispam-Agent-Protokollierung erfolgreich konfiguriert haben:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
        Get-TransportService <ServerIdentity> | Format-List AgentLog*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

