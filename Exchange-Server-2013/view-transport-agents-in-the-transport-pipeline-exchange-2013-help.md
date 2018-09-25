---
title: 'Anzeigen von Transport-Agents in der Transportpipeline: Exchange 2013 Help'
TOCTitle: Anzeigen von Transport-Agents in der Transportpipeline
ms:assetid: bd715d8e-7b21-48de-8f68-d425d8506e4c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124395(v=EXCHG.150)
ms:contentKeyID: 51409332
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von Transport-Agents in der Transportpipeline

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können über die Exchange-Verwaltungsshell auf Postfach- und Clientzugriffsservern von Microsoft Exchange Server 2013 eine Liste der Transport-Agents in der Transportpipeline anzeigen. Insbesondere das Cmdlet **Get-TransportPipeline** zeigt Informationen zu den folgenden Typen von Transport-Agents in der Transportpipeline:

  - Agents basierend auf den Klassen **SmtpReceiveAgent**, **RoutingAgent**, **DeliveryAgent** und **StorageAgent** im Transportdienst auf Postfachservern.

  - Agents basierend auf der Klasse **SmtpReceiveAgentClass** im Postfachtransport-Zustellungsdienst auf Postfachservern.

  - Agents basierend auf der Klasse **SmtpReceiveAgentClass** im Front-End-Transport-Dienst auf Clientzugriffsservern.

Sie können eine Liste aller aktivierten Transport-Agents anzeigen, die Nachrichten in der Transportpipeline ermittelt haben, sowie die SMTP-Ereignisse, für die sie registriert sind. Weitere Informationen zu Transport-Agents finden Sie unter [Transport-Agents](transport-agents-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Anzeigen einer Liste mit Transport-Agents in der Transportpipeline mithilfe der Shell

Sie können über die Shell den folgenden Befehl ausführen, um eine Liste der Transport-Agents in der Transportpipeline auf einem Exchange-Server anzuzeigen:

```powershell
Get-TransportPipeline | Format-List
```

Führen Sie den folgenden Befehl aus, um die Ergebnisse in die Textdatei "C:\\My Documents\\Transport Agents.txt" zu exportieren:

```powershell
    Get-TransportPipeline | Format-List > "C:\My Documents\Transport Agents.txt"
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Das Cmdlet zeigt nur Transport-Agents mit Nachrichten in der Transportpipeline an, die zwischen dem Startzeitpunkt des Transportdiensts und der Ausführung des Cmdlets **Get-TransportPipeline** ermittelt wurden. Ein Transport-Agent, der keine Nachrichten in der Transportpipeline ermittelt hat, ist nicht in den vom Cmdlet **Get-TransportPipeline** angezeigten Ergebnissen enthalten, auch wenn dieser Transport-Agent aktiviert ist.

