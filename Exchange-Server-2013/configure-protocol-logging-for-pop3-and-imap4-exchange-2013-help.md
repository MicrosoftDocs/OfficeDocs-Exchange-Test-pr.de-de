---
title: 'Konfigurieren der Protokollierung für POP3 und IMAP4: Exchange 2013 Help'
TOCTitle: Konfigurieren der Protokollierung für POP3 und IMAP4
ms:assetid: 451b337b-cb6b-4460-8687-be0b19c469bc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997690(v=EXCHG.150)
ms:contentKeyID: 50554808
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Protokollierung für POP3 und IMAP4

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-27_

Sie können die Shell verwenden, um die Protokolleinstellungen für POP3 und IMAP4 zu aktivieren, zu deaktivieren oder zu ändern. Standardmäßig ist die Protokollierung nicht aktiviert.

Mithilfe der Protokollierung können Sie die POP3- und IMAP4-Verbindungen in Ihrer Exchange-Umgebung überprüfen. Dies kann bei der Problembehandlung in Bezug auf POP3- oder IMAP4-Leistung hilfreich sein. Weitere Informationen finden Sie unter [Protokollierung für POP3 und IMAP4](protocol-logging-for-pop3-and-imap4-exchange-2013-help.md). Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" und "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Shell, um die Protokollierung für POP3 oder IMAP4 zu aktivieren

In diesem Beispiel wird die Protokollierung für IMAP4 oder POP3 auf dem Clientzugriffsserver CAS01 aktiviert.

```powershell
    Set-ImapSettings -Server "CAS01" -ProtocolLogEnabled $true
    Set-PopSettings -Server "CAS01" -ProtocolLogEnabled $true
```


> [!NOTE]
> Nachdem Sie die Einstellungen für die Protokollierung für POP3 und IMAP4 angegeben haben, müssen Sie die verwendeten Dienste neu starten: POP3 oder IMAP4. Informationen zum Neustarten des POP3- und IMAP4-Diensts finden Sie unter <A href="start-and-stop-the-pop3-services-exchange-2013-help.md">Starten und Beenden des POP3-Diensts</A> und <A href="start-and-stop-the-imap4-services-exchange-2013-help.md">Starten und Stoppen der IMAP4-Dienste</A>.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)) und [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Verwenden der Shell, um die Protokollierung für POP3 oder IMAP4 zu deaktivieren

In diesem Beispiel wird die Protokollierung für IMAP4 oder POP3 auf dem Clientzugriffsserver "CAS01" deaktiviert.

```powershell
    Set-ImapSettings -Server "CAS01" -protocolLogEnabled $false
    Set-PopSettings -Server "CAS01" -protocolLogEnabled $false
```

> [!NOTE]
> Nachdem Sie die Einstellungen für die Protokollierung für POP3 und IMAP4 angegeben haben, müssen Sie die verwendeten Dienste neu starten: POP3 oder IMAP4. Informationen zum Neustarten des POP3- und IMAP4-Diensts finden Sie unter <A href="start-and-stop-the-pop3-services-exchange-2013-help.md">Starten und Beenden des POP3-Diensts</A> und <A href="start-and-stop-the-imap4-services-exchange-2013-help.md">Starten und Stoppen der IMAP4-Dienste</A>.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)) und [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Verwenden der Shell, um die Protokollierung für POP3 oder IMAP4 zu ändern

Führen Sie die Cmdlets **Set-ImapSettings** oder **Set-PopSettings** mit mindestens einem der folgenden Parameter aus, um POP3- oder IMAP4-Protokollierungseinstellungen zu ändern.

  - *LogFileLocation*   Dieser Parameter gibt den Speicherort für die POP3- oder IMAP4-Protokolldateien an. Standardmäßig befinden sich die POP3-Protokolldateien im Verzeichnis **C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\Pop3**. In diesem Beispiel wird POP3-Protokollierung auf dem Clientzugriffsserver "CAS01" aktiviert. Es wird außerdem das Verzeichnis für die POP3-Protokollierung in "C:\\Pop3Logging" geändert.
    
    ```powershell
        Set-PopSettings -Server "CAS01" -ProtocolLogEnabled $true -LogFileLocation "C:\Pop3Logging"
    ```

  - *LogFileRollOverSettings*   Dieser Parameter definiert, wie häufig von der POP3- oder IMAP4-Protokollierung eine neue Protokolldatei erstellt wird. Standardmäßig wird täglich eine neue Protokolldatei erstellt. Die folgenden Werte sind möglich:
    
    Stündlich
    
    Täglich
    
    Wöchentlich
    
    Monatlich
    
    Diese Einstellung wird nur angewendet, wenn der Wert für den Parameter *LogPerFileSizeQuota* auf Null festgelegt ist. In diesem Beispiel wird die POP3-Protokollierung auf dem Clientzugriffsserver "CAS01" geändert, um stündlich eine neue Protokolldatei zu erstellen.
    
    ```powershell
    Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota 0 -LogFileRollOverSettings Hourly
    ```

  - *LogPerFileSizeQuota*   Dieser Parameter definiert die maximale Größe einer POP3- oder IMAP4-Protokolldatei in Bytes. Standardmäßig ist dieser Wert auf Null festgelegt. Ist dieser Wert auf Null festgelegt, wird entsprechend der über den Parameter *LogFileRollOverSettings* festgelegten Häufigkeit eine neue Protokolldatei erstellt.
    
    In diesem Beispiel wird die POP3-Protokollierung auf dem Clientzugriffsserver "CAS01" geändert, um eine neue Protokolldatei zu erstellen, wenn die Protokolldatei eine Größe von 2 MB erreicht.
    
    ```powershell
    Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota 2000000
    ```
    
    In diesem Beispiel wird die POP3-Protokollierung auf dem Clientzugriffsserver "CAS01" geändert, um dieselbe Protokolldatei unabhängig von ihrem Erstellungsdatum und ihrer Größe zu verwenden.
    
    ```powershell
    Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota unlimited
    ```


> [!NOTE]
> Nachdem Sie die Einstellungen für die Protokollierung für POP3 und IMAP4 angegeben haben, müssen Sie die verwendeten Dienste neu starten: POP3 oder IMAP4. Informationen zum Neustarten des POP3- und IMAP4-Diensts finden Sie unter <A href="start-and-stop-the-pop3-services-exchange-2013-help.md">Starten und Beenden des POP3-Diensts</A> und <A href="start-and-stop-the-imap4-services-exchange-2013-help.md">Starten und Stoppen der IMAP4-Dienste</A>.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)) und [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überprüfen Sie mithilfe des folgenden Befehls in der Shell die Einstellungen für die POP3-Protokollierung. Wenn die POP3-Protokollierung aktiviert ist, ist der Wert für den Parameter *ProtocolLogEnabled* auf `True` festgelegt. Wenn die POP3-Protokollierung deaktiviert ist, lautet der Wert `False`. Sie können auch sicherstellen, dass die Werte für die Parameter *LogFileLocation*, *LogPerFileSizeQuota* und *LogFileRollOverSettings* richtig sind.

```powershell
Get-PopSettings | format-list
```

Überprüfen Sie mithilfe des folgenden Befehls in der Shell die Einstellungen für die IMAP4-Protokollierung. Wenn die IMAP4-Protokollierung aktiviert ist, ist der Wert für den Parameter *ProtocolLogEnabled* auf `True` festgelegt. Wenn die IMAP4-Protokollierung deaktiviert ist, lautet der Wert `False`. Sie können auch sicherstellen, dass die Werte für die Parameter *LogFileLocation*, *LogPerFileSizeQuota* und *LogFileRollOverSettings* richtig sind.

```powershell
Get-ImapSettings | format-list
```

## Weitere Informationen

Nachdem Sie Protokollierungseinstellungen für POP3 und IMAP4 konfiguriert haben, können Sie die folgenden Aufgaben ausführen:

[Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md)

[Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md)

