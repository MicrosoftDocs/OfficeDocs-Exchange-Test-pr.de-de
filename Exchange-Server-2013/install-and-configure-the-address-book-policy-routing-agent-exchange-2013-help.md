---
title: 'Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien: Exchange 2013 Help'
TOCTitle: Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien
ms:assetid: 20e8a43d-4508-4388-a2c9-aa3073593cc2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ907308(v=EXCHG.150)
ms:contentKeyID: 51409284
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-01-09_

Der Routing-Agent für Adressbuchrichtlinien ist ein Transport-Agent, der auf dem Postfachserver ausgeführt wird, der die Auflösung von Empfängern in Ihrer Organisation steuert. Wenn der Routing-Agent für Adressbuchrichtlinien installiert und konfiguriert wird, werden Benutzer, die verschiedenen GALs zugeordnet sind, insofern als externe Empfänger angezeigt, als sie die Visitenkarten externer Empfänger nicht anzeigen können.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adressbuchrichtlinien finden Sie unter [Verfahren für Adressbuchrichtlinien](address-book-policy-procedures-exchange-2013-help.md).

Suchen Sie die Exchange Online-Version dieses Themas? Weitere Informationen finden Sie unter [Aktivieren des Adressbuchrichtlinien-Routings](https://technet.microsoft.com/de-de/library/jj891095\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 15 Minuten.

  - Nach der Installation und Konfiguration des Routing-Agenten für Adressbuchrichtlinien kann es bis zu 30 Minuten dauern, bis E-Mail in der Organisation vom Agent ausgewertet wird.

  - Dieses Verfahren kann nicht mit der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Installieren des Routing-Agents für Adressbuchrichtlinien

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Installieren Sie den Routing-Agent für Adressbuchrichtlinien durch Ausführen des folgenden Befehls. Dies sind der genaue Befehl und die Syntax, die Sie verwenden müssen.

    Install-TransportAgent -Name "ABP Routing Agent" -TransportAgentFactory "Microsoft.Exchange.Transport.Agent.AddressBookPolicyRoutingAgent.AddressBookPolicyRoutingAgentFactory" -AssemblyPath $env:ExchangeInstallPath\TransportRoles\agents\AddressBookPolicyRoutingAgent\Microsoft.Exchange.Transport.Agent.AddressBookPolicyRoutingAgent.dll

Sie erhalten eine Warnung, dass der Transportdienst neu gestartet werden muss, damit Ihre Änderungen in Kraft treten. Führen Sie jedoch zuerst Schritt 2 durch, damit Sie den Transportdienst nur einmal neu starten müssen.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Install-TransportAgent](https://technet.microsoft.com/de-de/library/aa997998\(v=exchg.150\)).

## Schritt 2: Aktivieren des Transportrouting-Agents

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Nachdem Sie den Routing-Agent für Adressbuchrichtlinien installiert haben, müssen Sie ihn mithilfe des folgenden Befehls aktivieren:

    Enable-TransportAgent "ABP Routing Agent"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Enable-TransportAgent](https://technet.microsoft.com/de-de/library/bb124921\(v=exchg.150\)).

## Schritt 3: Neustarten des Transportdienst und Sicherstellen der Installation und Aktivierung des Routing-Agents für Adressbuchrichtlinien

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

1.  Führen Sie den folgenden Befehl aus, um den Transportdienst neu zu starten.
    
        Restart-Service MSExchangeTransport

2.  Nach dem Neustart des Diensts prüfen Sie durch Ausführen des folgenden Cmdlets, ob der Routing-Agent für Adressbuchrichtlinien installiert und aktiviert wurde.
    
        Get-TransportAgent
    
    Wenn der Routing-Agent für Adressbuchrichtlinien aufgeführt wird, wurde der Agent ordnungsgemäß installiert.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-TransportAgent](https://technet.microsoft.com/de-de/library/bb123536\(v=exchg.150\)).

## Schritt 4: Aktivieren des Routing-Agents für Adressbuchrichtlinien

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportkonfiguration" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Der letzte Schritt in diesem Verfahren besteht darin, das Adressbuchrichtlinien-Routing für die Organisation zu aktivieren. Führen Sie den folgenden Befehl aus.

    Set-TransportConfig -AddressBookPolicyRoutingEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-TransportConfig](https://technet.microsoft.com/de-de/library/bb124151\(v=exchg.150\)).

