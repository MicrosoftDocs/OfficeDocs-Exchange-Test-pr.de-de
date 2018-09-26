---
title: 'Konfigurieren der Protokollprotokollierung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Protokollprotokollierung
ms:assetid: c81cac9c-b990-492a-b899-5be8d08a6068
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124531(v=EXCHG.150)
ms:contentKeyID: 50476703
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Protokollprotokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-03-15_

Protokollaufzeichnungen enthalten SMTP-Unterhaltungen, die zwischen Sende- und Empfangsconnectors als Teil der Nachrichtenübermittlung stattfinden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst", "Front-End-Transportdienst", "Postfachtransportdienst", "Empfangsconnectors" und "Sendeconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Sie können die Exchange-Verwaltungskonsole (Exchange Administration Console, EAC) verwenden, um die Protokollierung für Sende- und Empfangsconnectors im Transportdienst auf Postfachservern und für Empfangsconnectors im Front-End-Transportdienst auf Clientzugriffsservern zu aktivieren oder zu deaktivieren. Mit der Exchange-Verwaltungskonsole können Sie zudem die Protokollpfade nur für den Transportdienst konfigurieren. Für alle anderen Protokollierungsoptionen müssen Sie die Shell verwenden.

  - Die Protokollierung wird auf jedem Connector aktiviert oder deaktiviert. Für alle Empfangsconnectors auf dem Exchange-Server werden die gleichen Protokolldateien und Protokolloptionen verwenden. Diese Protokolleinstellungen sind unabhängig von den Protokolldateien und Protokolloptionen für Sendeconnector auf dem gleichen Server.

    > [!WARNING]
    > Führen Sie dieses Verfahren auf keinem Edge-Transport-Server aus, der mithilfe von "EdgeSync" die Exchange-Organisation abonniert hat. Nehmen Sie stattdessen die Änderungen im Transportdienst auf dem Postfachserver vor. Die Änderungen werden dann mit der nächsten EdgeSync-Synchronisierung auf den Edge-Transport-Server repliziert.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Konfigurieren der Protokollierung

Führen Sie die folgenden Schritte aus, um mit der Exchange-Verwaltungskonsole die Protokollierung für einen Sende- oder Empfangsconnector im Transportdienst auf einem Postfachserver oder für einen Empfangsconnector im Front-End-Transportdienst auf einem Clientzugriffsserver zu aktivieren oder zu deaktivieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Sendeconnectors** oder **Nachrichtenfluss** \> **Empfangsconnectors**.

2.  Wählen Sie den Connector aus, den Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Protokolliergrad** eine der folgenden Optionen aus:
    
      - **Keine**   Protokollierung ist für den Connector deaktiviert.
    
      - **Ausführlich**   Protokollierung ist für den Connector aktiviert.
    
    Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

Führen Sie die folgenden Schritte aus, um mit der Exchange-Verwaltungskonsole Protokollpfade für Sende- und Empfangsconnectors im Transportdienst auf einem Postfachserver zu konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie den Postfachserver aus, den Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **Transportprotokolle**.

4.  Ändern Sie im Abschnitt **Protokoll** die folgenden Einstellungen:
    
      - **Protokollpfad senden**   Der angegebene Wert muss sich auf dem lokalen Exchange-Server befinden. Wenn der Ordner nicht vorhanden ist, wird er für Sie erstellt, wenn Sie auf **Speichern** klicken.
    
      - **Protokollpfad für Empfangsprotokoll**   Der angegebene Wert muss sich auf dem lokalen Exchange-Server befinden. Wenn der Ordner nicht vorhanden ist, wird er für Sie erstellt, wenn Sie auf **Speichern** klicken.
    
    Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um zu überprüfen, ob Sie die Protokollpfadeinstellungen erfolgreich mit der Exchange-Verwaltungskonsole konfiguriert haben:

1.  Navigieren Sie zum Speicherort, den Sie für die Sende- oder Empfangsconnectorprotokolle angegeben haben.

2.  Wenn die Protokollierung aktiviert ist, überprüfen Sie, ob eine Protokolldatei erstellt wird. Wenn Sie die Protokollierung deaktiviert haben, stellen Sie sicher, dass die letzte Protokolldatei nicht mehr aktualisiert wird.

## Aktivieren oder Deaktivieren der Protokollierung für einen Sende- oder Empfangsconnector mit der Shell

Führen Sie den folgenden Befehl aus, um die Protokollierung für einen Sende- oder Empfangsconnector zu aktivieren oder zu deaktivieren:

```powershell
    <Set-SendConnector |Set-ReceiveConnector> <ConnectorIdentity> -ProtocolLoggingLevel <Verbose | None>
```

In diesem Beispiel wird die Protokollierung für den Empfangsconnector "Connection from Contoso.com" aktiviert.

```powershell
Set-ReceiveConnector "Connection from Contoso.com" -ProtocolLoggingLevel Verbose
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie die Protokollierung erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
    ```command line
    <Get-SendConnector |Get-ReceiveConnector> | Format-List Name,ProtocolLoggingLevel
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Aktivieren oder Deaktivieren der Protokollierung für den organisationsinternen Sendeconnector mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Protokollierung für den impliziten und unsichtbaren organisationsinternen Sendeconnector, der im Transportdienst auf einem Postfachserver und im Front-End-Transportdienst auf einem Clientzugriffsserver vorhanden ist, zu aktivieren oder zu deaktivieren:

```powershell
    <Set-TransportService | Set-FrontEndTransportService> -IntraOrgConnectorProtocolLoggingLevel <Verbose | None>
```

In diesem Beispiel wird die Protokollierung für den organisationsinternen Sendeconnector im Transportdienst auf dem Postfachserver "Mailbox01" aktiviert.

```powershell
Set-TransportService Mailbox01 -IntraOrgConnectorProtocolLoggingLevel Verbose
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie die Protokollierung für den organisationsinternen Sendeconnector erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
    ```powershell
        <Get-TransportService | Get-FrontEndTransportService> <ServerIdentity> | Format-List IntraOrgConnectorProtocolLoggingLevel
    ```
    
2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Aktivieren oder Deaktivieren der Protokollierung für den Postfachzustellungs-Sendeconnector mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Protokollierung für den impliziten und unsichtbaren Postfachzustellungs-Sendeconnector, der im Postfachtransportdienst auf einem Postfachserver vorhanden ist, zu aktivieren oder zu deaktivieren:

```powershell
Set-MailboxTransportService -MailboxDeliveryConnectorProtocolLoggingLevel <Verbose | None>
```

In diesem Beispiel wird die Protokollierung für den Postfachzustellungs-Empfangsconnector im Postfachtransportdienst auf dem Postfachserver "Mailbox01" aktiviert.

```powershell
Set-MailboxTransportService Mailbox01 -MailboxDeliveryConnectorProtocolLoggingLevel Verbose
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie die Protokollierung für den Postfachzustellungsconnector erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
    ```powershell
        Get-MailboxTransportService <ServerIdentity> | Format-List MailboxDeliveryConnectorProtocolLoggingLevel
    ```
    
2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren der Protokolleinstellungen mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Protokolleinstellungen zu konfigurieren:

```powershell
    <Set-TransportService | Set-MailboxTransportService | Set-FrontEndTransportService> <ServerIdentity> -ReceiveProtocolLogPath <LocalFilePath> -SendProtocolLogPath <LocalFilePath> -ReceiveProtocolLogMaxFileSize <Size> -SendProtocolLogMaxFileSize <Size> -ReceiveProtocolLogMaxDirectorySize <Size> -SendProtocolLogMaxDirectorySize <Size> -ReceiveProtocolLogMaxAge <dd.hh:mm:ss> -SendProtocolLogMaxAge <dd.hh:mm:ss>
```

In diesem Beispiel werden die folgenden Protokolleinstellungen im Transportdienst auf dem Postfachserver "Mailbox01" festgelegt:

  -  Der Speicherort aller Empfangsconnectorprotokolle wird auf "D:\\Hub Receive SMTP Log" festgelegt, und für alle Sendeconnectorprotokolle wird er auf "D:\\Hub Send SMTP Log" festgelegt. Beachten Sie, dass der Ordner für Sie erstellt wird, wenn er nicht vorhanden ist.

  -  Die maximale Größe einer Empfangsconnector-Protokolldatei und einer Sendeconnector-Protokolldatei wird auf 20 MB festgelegt.

  -  Die maximale Größe eines Empfangsconnector-Protokollordners und eines Sendeconnector-Protokollordners wird auf 400 MB festgelegt.

  -  Das maximale Alter einer Empfangsconnector-Protokolldatei und einer Sendeconnector-Protokolldatei wird auf 45 Tage festgelegt.

<!-- end list -->

```powershell
    Set-TransportService Mailbox01 -ReceiveProtocolLogPath "D:\Hub Receive SMTP Log" -SendProtocolLogPath "D:\Hub Send SMTP Log" -ReceiveProtocolLogMaxFileSize 20MB -SendProtocolLogMaxFileSize 20MB -ReceiveProtocolLogMaxDirectorySize 400MB -SendProtocolLogMaxDirectorySize 400MB -ReceiveProtocolLogMaxAge 45.00:00:00 -SendProtocolLogMaxAge 45.00:00:00
```

> [!NOTE]
> <UL>
> <LI>
> <P>Verwenden Sie das Cmdlet <STRONG>Set-MailboxTransportService</STRONG>, um die Protokolleinstellungen im Postfachtransportdienst auf einem Postfachserver zu konfigurieren. Verwenden Sie das Cmdlet <STRONG>Set-FrontEndTransportService</STRONG>, um die Protokolleinstellungen im Front-End-Transportdienst auf einem Clientzugriffsserver zu konfigurieren.</P>
> <LI>
> <P>Wenn Sie die Parameter <EM>SendProtocolLogPath</EM> oder <EM>ReceiveProtocolLogPath</EM> auf den Wert <CODE>$null</CODE> festlegen, wird die Protokollierung für alle Sendeconnectors oder Empfangsconnectors auf dem Server effektiv deaktiviert. Wenn Sie jedoch einen dieser Parameter bei aktivierter Protokollierung für einen beliebigen Connector auf dem Server, einschließlich des organisationsinternen Sendeconnectors oder des Postfachzustellungs-Sendeconnectors, auf <CODE>$null</CODE> festlegen, werden Ereignisprotokollfehler generiert.</P>
> <LI>
> <P>Wenn Sie die Parameter <EM>ReceiveProtocolLogMaxAge</EM> oder <EM>SendProtocolLogMaxAge</EM> auf den Wert <CODE>00:00:00</CODE> festlegen, wird verhindert, dass Protokolldateien aufgrund ihres Alters automatisch entfernt werden.</P></LI></UL>



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie die Protokolleinstellungen erfolgreich konfiguriert haben:

1.  Führen Sie in der Shell den folgenden Befehl aus:
    
    ```powershell
        <Get-TransportService | Get-MailboxTransportService | Get-FrontEndTransportService> <ServerIdentity> | Format-List SendConnectorProtocolLog*,ReceiveConnectorProtocolLog*
    ```
    
2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

