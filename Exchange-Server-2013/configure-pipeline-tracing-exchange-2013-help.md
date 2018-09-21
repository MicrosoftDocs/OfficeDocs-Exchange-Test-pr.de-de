---
title: 'Konfigurieren der Pipelineablaufverfolgung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Pipelineablaufverfolgung
ms:assetid: 10293c83-2157-474e-840d-942e064a4672
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ916678(v=EXCHG.150)
ms:contentKeyID: 52062832
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Pipelineablaufverfolgung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Pipelineablaufverfolgung erfasst Kopien von E-Mails, während diese die Transportpipeline im Transportdienst oder im Postfachtransportdienst auf Postfachservern und auf Edge-Transport-Servern durchlaufen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unterEinträge "Transportdienst" und "Postfachtransportdienst" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Die Pipelineablaufverfolgung kopiert den vollständigen Inhalt von E-Mails, die von der E-Mail-Adresse des Absenders gesendet werden. Um die unerwünschte Preisgabe vertraulicher Informationen zu vermeiden, müssen Sie für den Speicherort des Pipelineablaufverfolgungs-Ordners geeignete Sicherheitsberechtigungen festlegen.

  - Aktivieren Sie die Pipelineablaufverfolgung nicht für längere Zeiträume. Mithilfe der Pipelineablaufverfolgung werden mehrere Nachrichten-Momentaufnahmendateien erstellt, die sich schnell ansammeln können. Überwachen Sie bei aktivierter Pipelineablaufverfolgung immer den auf dem Datenträger verfügbaren Speicherplatz.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren und Konfigurieren der Pipelineablaufverfolgung

## Schritt 1: Konfigurieren der Absenderadresse für die Pipelineablaufverfolgung mithilfe der Shell

Verwenden Sie die folgende Syntax, um die Absenderadresse für die Pipelineablaufverfolgung zu konfigurieren.

    <Set-TransportService | Set-MailboxTransportService> <ServerIdentity> -PipelineTracingSenderAddress <SMTPAddress | "<>">

In diesem Beispiel wird die Pipelineablaufverfolgung so konfiguriert, dass Momentaufnahmen aller Nachrichten erfasst werden, die vom Absender "chris@contoso.com" im Transportdienst auf dem Postfachserver namens "Mailbox01" gesendet werden.

```powershell
Set-TransportService Mailbox01 -PipelineTracingSenderAddress chris@contoso.com
```

In diesem Beispiel wird die Pipelineablaufverfolgung so konfiguriert, dass Momentaufnahmen aller vom System generierten Nachrichten erfasst werden, die vom Transportdienst auf dem Postfachserver namens "Mailbox02" empfangen werden.

```powershell
Set-TransportService Mailbox02 -PipelineTracingSenderAddress "<>"
```


> [!WARNING]
> Durch das Konfigurieren der Pipelineablaufverfolgung für die Erfassung aller vom Server generierten Nachrichten in einem Transportdienst kann der Server erheblich belastet und der verfügbare Festplattenspeicher schnell aufgebraucht werden. Überwachen Sie bei aktivierter Pipelineablaufverfolgung immer den auf dem Datenträger verfügbaren Speicherplatz.



## Schritt 2: (Optional) Angeben eines benutzerdefinierten Pipelineablaufverfolgungs-Ordners mithilfe der Shell

Der Standardordner für die Pipelineablaufverfolgung ist erst dann vorhanden, wenn Sie die Pipelineablaufverfolgung aktiviert haben und Nachrichten den Transportdienst auf dem Server passieren, die den mithilfe des Parameters *PipelineTracingSenderAddress* angegebenen Kriterien entsprechen. Für den Transportdienst auf einem Postfachserver lautet der Standardspeicherort `%ExchangeInstallPath%TransportRoles\Logs\Hub\PipelineTracing`. Für den Postfachtransportdienst auf einem Postfachserver lautet der Standardspeicherort `%ExchangeInstallPath%TransportRoles\Logs\Mailbox\PipelineTracing`. Wenn Sie einen benutzerdefinierten Pfad angeben, muss sich der Pfad auf dem lokalen Exchange-Server befinden.

Verwenden Sie die folgende Syntax, um den Ordner für die Pipelineablaufverfolgung zu konfigurieren.

    <Set-TransportService | Set-MailboxTransportService> <ServerIdentity> -PipelineTracingPath <LocalFilePath>

In diesem Beispiel wird der Ordner für die Pipelineablaufverfolgung für den Transportdienst auf dem Postfachserver namens "Mailbox01" auf "D:\\Hub\\Pipeline Tracing" festgelegt.

    Set-TransportService Mailbox01 -PipelineTracingPath "D:\Hub\Pipeline Tracing"

## Schritt 3: Verwenden der Shell zum Aktivieren der Pipelineablaufverfolgung

Die Pipelineablaufverfolgung ist standardmäßig auf allen Exchange-Servern deaktiviert. Wenn Sie die Pipelineablaufverfolgung aktivieren, wird diese nur im angegebenen Transportdienst auf dem angegebenen Exchange-Server aktiviert. Bevor Sie die Pipelineablaufverfolgung aktivieren, müssen Sie die Absenderadresse wie in Schritt 1 beschrieben angeben.

Verwenden Sie die folgende Syntax, um die Pipelineablaufverfolgung zu aktivieren.

    <Set-TransportService | Set-MailboxTransportService> <ServerIdentity> -PipelineTracingEnabled $true

In diesem Beispiel wird die Pipelineablaufverfolgung im Transportdienst auf dem Postfachserver namens "Mailbox01" aktiviert.

```powershell
Set-TransportService Mailbox01 -PipelineTracingEnabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Pipelineablaufverfolgung ordnungsgemäß konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        <Get-TransportService | Get-MailboxTransportService> <ServerIdentity> | Format-List PipelineTracing*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

3.  Prüfen Sie den Ordner für die Pipelineablaufverfolgung für den Transportdienst oder den Postfachtransportdienst, und stellen Sie sicher, dass Nachrichten-Momentaufnahmendateien im Ordner erstellt werden.

## Deaktivieren der Pipelineablaufverfolgung

Aufgrund der mit der Pipelineablaufverfolgung verbundenen Bedenken hinsichtlich des Speicherplatzes und der Sicherheit ist die Pipelineablaufverfolgung eine vorübergehende Maßnahme zum Zweck der Diagnose und Problembehandlung. Wenn Sie die Pipelineablaufverfolgung aktivieren, denken Sie daran, sie nach Beendigung Ihrer Aufgaben wieder zu deaktivieren.

Verwenden Sie die folgende Syntax, um die Pipelineablaufverfolgung zu deaktivieren.

    <Set-TransportService | Set-MailboxTransportService> <ServerIdentity> -PipelineTracingEnabled $false

In diesem Beispiel wird die Pipelineablaufverfolgung im Transportdienst auf dem Postfachserver namens "Mailbox01" deaktiviert.

```powershell
Set-TransportService Mailbox01 -PipelineTracingEnabled $false
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Pipelineablaufverfolgung ordnungsgemäß deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        <Get-TransportService | Get-MailboxTransportService> <ServerIdentity> | Format-List PipelineTracingEnabled

2.  Stellen Sie sicher, dass der Wert des Parameters *PipelineTracingEnabled* "$false" lautet.

3.  Prüfen Sie den Ordner für die Pipelineablaufverfolgung, und stellen Sie sicher, dass keine weiteren Nachrichten-Momentaufnahmendateien im Ordner erstellt werden.

