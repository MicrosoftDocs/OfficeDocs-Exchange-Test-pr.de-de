---
title: 'Konfigurieren der Nachrichtenverfolgung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Nachrichtenverfolgung
ms:assetid: 50eb5213-cf27-4179-b427-38d751ee4a70
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997984(v=EXCHG.150)
ms:contentKeyID: 51409294
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Nachrichtenverfolgung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-18_

Die Nachrichtenverfolgung zeichnet die SMTP-Transportaktivitäten aller Nachrichten auf, die an den oder vom Transportdienst bzw. an oder von Postfächern auf einem Microsoft Exchange Server 2013-Postfachserver übertragen werden. Sie können Nachrichtenverfolgungsprotokolle für forensische Nachrichtenanalysen, Nachrichtenübermittlungsanalysen, die Berichterstellung und die Problembehandlung verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md) oder "Postfachserverkonfiguration" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Mithilfe der Exchange-Verwaltungskonsole können Sie die Nachrichtenverfolgung aktivieren oder deaktivieren oder den Pfad zum Nachrichtenverfolgungsprotokoll festlegen. Für alle übrigen Optionen der Nachrichtenverfolgung müssen Sie die Exchange-Verwaltungsshell verwenden.

  - Auf einem Exchange 2013-Postfachserver können Sie entweder das Cmdlet **Set-TransportService** oder das Cmdlet **Set-MailboxServer** zum Konfigurieren der Nachrichtenverfolgungsoptionen verwenden. In den Verfahren in diesem Thema wird das Cmdlet **Set-TransportService** eingesetzt.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der Nachrichtenverfolgung auf Postfachservern mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie den Postfachserver aus, den Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **Transportprotokolle**.

4.  Ändern Sie im Abschnitt **Protokoll der Nachrichtenverfolgung** nach Bedarf die folgenden Einstellungen:
    
      - **Protokoll für Nachrichtenverfolgung aktivieren**   Deaktivieren Sie das Kontrollkästchen, um Nachrichtenverfolgung auf dem Server zu deaktivieren. Aktivieren Sie das Kontrollkästchen, um die Nachrichtenverfolgung auf dem Server zu aktivieren.
    
      - **Pfad des Nachrichtenverfolgungsprotokolls**   Der angegebene Wert muss sich auf dem lokalen Exchange-Server befinden. Wenn der Ordner nicht vorhanden ist, wird er für Sie erstellt, wenn Sie auf **Speichern** klicken.

5.  Klicken Sie auf **Speichern**.

## Konfigurieren der Nachrichtenverfolgung mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Nachrichtenverfolgung zu konfigurieren:

```powershell
    Set-TransportService <ServerIdentity> -MessageTrackingLogEnabled <$true | $false> -MessageTrackingLogMaxAge <dd.hh:mm:ss> -MessageTrackingLogMaxDirectorySize <Size> -MessageTrackingLogMaxFileSize <Size> -MessageTrackingLogPath <LocalFilePath> -MessageTrackingLogSubjectLoggingEnabled <$true|$false>
```

In diesem Beispiel werden folgende Einstellungen für das Nachrichtenverfolgungsprotokoll auf dem Postfachserver "Mailbox01" festgelegt:

  -  Legt den Speicherort für die Protokolldateien der Nachrichtenverfolgung auf "D:\\Message Tracking Log" fest. Beachten Sie, dass der Ordner für Sie erstellt wird, wenn er nicht vorhanden ist.

  -  Legt die maximale Größe einer Protokolldatei der Nachrichtenverfolgung auf 20 MB fest.

  -  Legt die maximale Größe des Verzeichnisses für das Nachrichtenverfolgungsprotokoll auf 1,5 GB fest.

  -  Legt das maximale Alter einer Protokolldatei für die Nachrichtenverfolgung auf 45 Tage fest.

<!-- end list -->

```powershell
    Set-TransportService Mailbox01 -MessageTrackingLogPath "D:\Hub Message Tracking Log" -MessageTrackingLogMaxFileSize 20MB -MessageTrackingLogMaxDirectorySize 1.5GB -MessageTrackingLogMaxAge 45.00:00:00
```


> [!NOTE]
> <UL>
> <LI>
> <P>Wenn Sie den Parameter <EM>MessageTrackingLogPath</EM> auf <CODE>$null</CODE> festlegen, wird die Nachrichtenverfolgung deaktiviert. Lautet der Wert des Parameters <EM>MessageTrackingLogEnabled</EM> jedoch <CODE>$true</CODE>, werden Fehler im Ereignisprotokoll generiert.</P>
> <LI>
> <P>Wenn Sie den Parameter <EM>MessageTrackingLogMaxAge</EM> auf den Wert <CODE>00:00:00</CODE> festlegen, wird verhindert, dass Protokolldateien der Nachrichtenverfolgung aufgrund ihres Alters automatisch gelöscht werden.</P>
> <LI>
> <P>Auf Exchange 2013-Postfachservern entspricht die maximale Größe des Nachrichtenverfolgungs-Protokollverzeichnisses dem dreifachen Wert des Parameters <EM>MessageTrackingLogMaxDirectorySize</EM>. Auch wenn die Protokolldateien der Nachrichtenverfolgung, die von den vier unterschiedlichen Diensten generiert werden, vier verschiedene Namenspräfixe aufweisen, ist die Menge und die Häufigkeit der in <STRONG>MSGTRKMA</STRONG>-Protokolldateien geschriebenen Daten im Vergleich zu den drei übrigen Protokolldateipräfixen verschwindend gering. Weitere Informationen finden Sie im Abschnitt "Struktur der Nachrichtenverfolgungs-Protokolldateien" im Thema <A href="message-tracking-exchange-2013-help.md">Nachrichtenverfolgung</A>.</P></LI></UL>



In diesem Beispiel wird die Nachrichtenbetreffprotokollierung im Nachrichtenverfolgungsprotokoll auf dem Postfachserver "Mailbox01" deaktiviert:

```powershell
Set-TransportService Mailbox01 -MessageTrackingLogSubjectLoggingEnabled $false
```

In diesem Beispiel wird die Nachrichtenverfolgung auf dem Postfachserver namens "Mailbox01" deaktiviert:

```powershell
Set-TransportService Mailbox01 -MessageTrackingLogEnabled $false
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Nachrichtenverfolgung ordnungsgemäß konfiguriert wurde:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
    ```powershell
        Get-TransportService <ServerIdentity> | Format-List MessageTrackingLog*
    ```
    
2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

