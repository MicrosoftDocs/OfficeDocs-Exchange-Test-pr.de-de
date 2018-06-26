---
title: 'Verwalten von Transport-Agents: Exchange 2013 Help'
TOCTitle: Verwalten von Transport-Agents
ms:assetid: f15ab7e4-015d-45b1-9c10-f733d7cd2a36
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125175(v=EXCHG.150)
ms:contentKeyID: 50477060
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Transport-Agents

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Transport-Agents verwenden SMTP-Ereignisse, um Nachrichten zu bearbeiten, während die Nachrichten die Transportpipeline durchlaufen. Die meisten integrierten Transport-Agents in Microsoft Exchange Server 2013 sind nicht sichtbar und nicht verwaltbar. Sie können in Ihrer Organisation jedoch Transport-Agents von Drittanbietern auf Exchange-Servern installieren und konfigurieren. Weitere Informationen zu Transport-Agents finden Sie unter [Transport-Agents](transport-agents-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Die Unterstützung von Legacy-Transport-Agents ist nicht standardmäßig aktiviert, aber sie kann von Ihnen aktiviert werden. Anweisungen finden Sie unter [Aktivieren der Unterstützung für Transport-Agents einer Vorversion](enable-support-for-legacy-transport-agents-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Informationen zu Transport-Agent-Verfahren im Front-End-Transport-Dienst auf Clientzugriffsservern

Sie können die Transport-Agents im Front-End-Transport-Dienst auf einem Clientzugriffsserver nicht mithilfe der Exchange-Verwaltungskonsole verwalten. Stattdessen müssen Sie die Windows PowerShell auf dem Clientzugriffsserver öffnen und dann die Exchange-Cmdlets in die Windows PowerShell-Sitzung importieren.


> [!WARNING]
> Das Ausführen von Exchange-Cmdlets in Windows PowerShell für andere Tasks als das Verwalten von Transport-Agents im Front-End-Transport-Dienst wird nicht unterstützt. Es kann schwerwiegende Folgen haben, wenn Sie die Exchange-Verwaltungsshell und die rollenbasierte Zugriffssteuerung (RBAC) umgehen, indem Sie Exchange-Cmdlets in Windows PowerShell ausführen. Exchange-Cmdlets sollten immer in der Exchange-Verwaltungsshell ausgeführt werden. Weitere Informationen finden Sie unter <A href="release-notes-for-exchange-2013-exchange-2013-help.md">Versionshinweise zu Exchange&nbsp;2013</A>.



Sie müssen die folgenden zusätzlichen Schritte ausführen, um eines der in diesem Thema beschriebenen Transport-Agent-Verfahren im Front-End-Transport-Dienst auszuführen:

1.  Öffnen Sie auf dem Clientzugriffsserver Windows PowerShell, und führen Sie dann den folgenden Befehl aus:
    
        Add-PSSnapin Microsoft.Exchange.Management.PowerShell.SnapIn

2.  Führen Sie den Befehl wie beschrieben aus, aber fügen Sie den folgenden Wert hinzu: `-TransportService FrontEnd`.
    
    Führen Sie z. B. den folgenden Befehl aus, um die Transport-Agents im Front-End-Transport-Dienst auf einem Clientzugriffsserver anzuzeigen:
    
        Get-TransportAgent -TransportService FrontEnd

## Installieren eines Transport-Agents mithilfe der Shell

Wenn Sie einen Transport-Agent installieren, registriert Exchange nur die DLLs, die dem Transport-Agent zugeordnet sind. Sie müssen sicherstellen, dass alle Dateien, Registrierungsschlüssel und anderen Objekte, von denen der Transport-Agent abhängig ist, ordnungsgemäß installiert und konfiguriert sind. Nachdem Exchange die DLLs geladen hat, wird nach Abschluss der Ausführung des Befehls weiterhin auf die DLLs verwiesen.

Transport-Agents haben Vollzugriff auf alle gefundenen E-Mail-Nachrichten. Exchange schränkt das Verhalten eines Transport-Agents nicht ein. Transport-Agents, die instabil sind oder Sicherheitsfehler enthalten, können die Stabilität und Sicherheit von Exchange beeinträchtigen. Aus diesem Grund dürfen Sie nur Transport-Agents installieren, die uneingeschränkt vertrauenswürdig sind und vollständig in einer Testumgebung getestet wurden.

Transport-Agents werden in deaktiviertem Zustand installiert, um sicherzustellen, dass der Nachrichtenfluss von noch nicht konfigurierten Transport-Agents unbeeinträchtigt bleibt. Sie müssen daher den Transport-Agent aktivieren, nachdem er ordnungsgemäß konfiguriert wurde.

Verwenden Sie die folgende Syntax, um einen Transport-Agent zu installieren.

    Install-TransportAgent -Name <TransportAgentIdentity> -TransportAgentFactory <"TransportAgentFactory"> -AssemblyPath <"FilePath">

In diesem Beispiel wird der fiktive Transport-Agent namens "Contoso Transport Agent" im Transportdienst auf einem Postfachserver installiert.

    Install-TransportAgent -Name "Contoso Transport Agent" -TransportAgentFactory "vendor.exchange.ContosoTransportAgentfactory" -AssemblyPath "C:\Program Files\Vendor\TransportAgent\ContosoTransportAgentFactory.dll"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den Befehl `Get-TransportAgent` aus, und stellen Sie sicher, dass der Transport-Agent aufgelistet ist und folglich erfolgreich installiert wurde.

## Aktivieren eines Transport-Agents mithilfe der Shell

Verwenden Sie die folgende Syntax, um einen Transport-Agent zu aktivieren.

    Enable-TransportAgent <TransportAgentIdentity>

In diesem Beispiel wird der Transport-Agent namens "Contoso Transport Agent" im Transportdienst auf einem Postfachserver aktiviert.

    Enable-TransportAgent "Contoso Transport Agent"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den Befehl `Get-TransportAgent | Format-List Name,Enabled` aus, und überprüfen Sie, ob der Transport-Agent aktiviert ist.

## Deaktivieren eines Transport-Agents mithilfe der Shell

Verwenden Sie die folgende Syntax, um einen Transport-Agent zu deaktivieren:

    Disable-TransportAgent <TransportAgentIdentity>

In diesem Beispiel wird der Transport-Agent namens "Fabrikam Transport Agent" im Transportdienst auf einem Postfachserver deaktiviert.

    Disable-TransportAgent "Fabrikam Transport Agent"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den Befehl `Get-TransportAgent | Format-List Name,Enabled` aus und überprüfen Sie, ob der Transport-Agent deaktiviert ist.

## Anzeigen von Transport-Agents mithilfe der Shell

Führen Sie zum Anzeigen einer Übersichtsliste aller Transport-Agents den folgenden Befehl aus:

    Get-TransportAgent

Führen Sie zum Anzeigen der ausführlichen Konfiguration eines bestimmten Transport-Agents den folgenden Befehl aus:

    Get-TransportAgent <TransportAgentIdentity> | Format-List

In diesem Beispiel wird die ausführliche Konfiguration des Transport-Agents namens "Transport Rule Agent" bereitgestellt.

    Get-TransportAgent "Transport Rule Agent" | Format-List

## Konfigurieren der Priorität eines Transport-Agents mithilfe der Shell

Transport-Agents mit einer Priorität, die 0 am nächsten ist, verarbeiten E-Mails zuerst. Das SMTP-Ereignis in der Transportpipeline, in der der Transport-Agent registriert ist, kann dazu führen, dass ein Agent mit niedrigerer Priorität die Nachricht bearbeitet, bevor ein Agent mit höherer Priorität die Möglichkeit dazu erhält.

Führen Sie den folgenden Befehl aus, um die Priorität eines vorhandenen Transport-Agents zu ändern:

    Set-TransportAgent <TransportAgentIdentity> -Priority <Integer>

In diesem Beispiel wird die Priorität des Agents für den vorhandenen Transport-Agent namens "Contoso Transport Agent" im Transportdienst auf einem Postfachserver auf den Wert "3" festgelegt.

    Set-TransportAgent "Contoso Transport Agent" -Priority 3

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den Befehl `Get-TransportAgent | Format-List Name,Priority` aus, und überprüfen Sie den Prioritätswert des Transport-Agents, um zu bestätigen, dass die Priorität eines Transport-Agents erfolgreich konfiguriert wurde.

## Deinstallieren eines Transport-Agents mithilfe der Shell

Wenn der Transport-Agent deinstalliert wird, hebt Exchange die Registrierung der mit dem Agent verwendeten DLL-Dateien auf. Exchange entfernt keine Dateien, Registrierungsschlüssel oder anderen Objekte, die durch die Installation des Transport-Agents hinzugefügt wurden.

Führen Sie den folgenden Befehl aus, um einen Transport-Agent zu deinstallieren:

    Uninstall-TransportAgent <TransportAgentIdentity>

In diesem Beispiel wird der Transport-Agent namens "Fabrikam Transport Agent" im Transportdienst auf einem Postfachserver deinstalliert.

    Uninstall-TransportAgent "Fabrikam Transport Agent"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den Befehl `Get-TransportAgent` aus, und stellen Sie sicher, dass der Transport-Agent nicht aufgeführt ist und folglich erfolgreich deinstalliert wurde.

