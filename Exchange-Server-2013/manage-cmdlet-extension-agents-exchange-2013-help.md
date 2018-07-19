---
title: 'Verwalten von Cmdlet-Erweiterungs-Agents: Exchange 2013 Help'
TOCTitle: Verwalten von Cmdlet-Erweiterungs-Agents
ms:assetid: 9141b3cb-ad13-4415-be2f-aa89f91445f5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298143(v=EXCHG.150)
ms:contentKeyID: 50554858
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Cmdlet-Erweiterungs-Agents

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-19_

In diesem Thema wird das Aktivieren, Deaktivieren, Anzeigen und Ändern der Priorität von Cmdlet-Erweiterungs-Agents in Exchange Server 2013 erläutert. Weitere Informationen zu Cmdlet-Erweiterungs-Agents in Exchange 2013 finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: Weniger als 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Cmdlet-Erweiterungs-Agents" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Vor der Aktivierung von `Scripting Agent` müssen Sie sicherstellen, dass der Agent ordnungsgemäß konfiguriert ist. Weitere Informationen zu `Scripting Agent` finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren eines Cmdlet-Erweiterungs-Agents

Wenn Sie in Exchange 2013 einen Cmdlet-Erweiterungs-Agent aktivieren, wird dieser auf allen Servern mit Exchange 2013 in der Organisation ausgeführt. Wenn ein Agent aktiviert ist, wird er für Cmdlets verfügbar gemacht, die dann mithilfe des Agents weitere Vorgänge ausführen können.


> [!WARNING]
> Machen Sie sich vor dem Aktivieren von Agents mit der Funktionsweise des jeweiligen Agents und den Auswirkungen der Aktivierung in der Organisation vertraut.



In diesem Beispiel wird ein Cmdlet-Erweiterungs-Agent mithilfe des Cmdlets **Enable-CmdletExtensionAgent** aktiviert. Bei der Ausführung dieses Cmdlets müssen Sie den Namen des Agents angeben, der aktiviert werden soll. Vor der Aktivierung des `Scripting Agent` müssen Sie sicherstellen, dass die Konfigurationsdatei `ScriptingAgentConfig.xml` auf allen Servern in der Organisation bereitgestellt wurde. Wenn Sie `Scripting``Agent` aktivieren, ohne dass die Konfigurationsdatei bereitgestellt wurde, schlägt die Ausführung aller Cmdlets fehl, bei denen es sich nicht um **Get**-Cmdlets handelt. In diesem Beispiel wird `Scripting Agent` aktiviert.

    Enable-CmdletExtensionAgent "Scripting Agent"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Enable-CmdletExtensionAgent](https://technet.microsoft.com/de-de/library/dd335192\(v=exchg.150\)).

## Deaktivieren eines Cmdlet-Erweiterungs-Agents

Wenn Sie in Exchange 2013 einen Cmdlet-Erweiterungs-Agent deaktivieren, wird dieser auf allen Servern mit Exchange 2013 in der Organisation deaktiviert. Ist ein Agent deaktiviert, wird er Cmdlets nicht zur Verfügung gestellt. Cmdlets können den Agent nicht mehr für zusätzliche Operationen verwenden.


> [!WARNING]
> Machen Sie sich vor dem Deaktivieren von Agents mit der Funktionsweise des jeweiligen Agents und den Auswirkungen der Deaktivierung in der Organisation vertraut.



Um einen Cmdlet-Erweiterungs-Agent zu deaktivieren, verwenden Sie das Cmdlet **Disable-CmdletExtensionAgent**. Geben Sie beim Ausführen des Cmdlets den Namen des Agents an, den Sie deaktivieren möchten. In diesem Beispiel wird der Agent `Scripting Agent` deaktiviert.

    Disable-CmdletExtensionAgent "Scripting Agent"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Disable-CmdletExtensionAgent](https://technet.microsoft.com/de-de/library/dd298132\(v=exchg.150\)).

## Anzeigen vorhandener Cmdlet-Erweiterungs-Agents

Durch Anzeigen vorhandener Cmdlet-Erweiterungs-Agents können Sie prüfen, welche Agents zuerst ausgeführt werden und in einer Exchange 2013-Organisation aktiviert sind. Weitere Informationen zum Pipelining und zum Cmdlet **Format-Table** finden Sie unter den folgenden Themen:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md)

In diesem Beispiel werden mithilfe des Cmdlets **Get-CmdletExtensionAgent** Details eines bestimmten Cmdlet-Erweiterungs-Agents abgerufen. In diesem Beispiel werden die Details des `Mailbox Permissions Agent` zurückgegeben.

    Get-CmdletExtensionAgent "Mailbox Permissions Agent"

In diesem Beispiel werden mit dem Cmdlet **Get-CmdletExtensionAgent** mehrere Cmdlet-Erweiterungs-Agents abgerufen. Anschließend wird die Ausgabe an das Cmdlet **Format-Table** weitergeleitet. In diesem Beispiel wird eine Liste aller Cmdlet-Erweiterungs-Agents in der Organisation angezeigt. Durch Verwendung des Cmdlets **Format-Table** werden die Eigenschaften **Name**, **Enabled** und **Priority** der einzelnen Agents in einer Tabelle angezeigt.

    Get-CmdletExtensionAgent | Format-Table Name, Enabled, Priority

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-CmdletExtensionAgent](https://technet.microsoft.com/de-de/library/dd297946\(v=exchg.150\)).

## Ändern der Priorität eines Cmdlet-Erweiterungs-Agents

Die Möglichkeit, die Priorität eines Cmdlet-Erweiterungs-Agents in Exchange 2013 zu ändern, ist nützlich, wenn ein Cmdlet einen bestimmten Agent vor einem anderen Agent aufrufen soll. Dies ist insbesondere dann hilfreich, wenn Sie ein benutzerdefiniertes Skript erstellen, das im `Scripting Agent` ausgeführt wird, und dieses Skript Vorrang vor einem integrierten Agent haben soll. Weitere Informationen zu `Scripting Agent` finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).


> [!WARNING]
> Das Ändern der Priorität oder das Ersetzen der Funktionalität eines integrierten Agents stellt einen erweiterten Vorgang dar. Stellen Sie sicher, dass Sie die Auswirkungen der Änderungen vollständig verstehen, die Sie vornehmen.



Agents werden von 0 bis zur maximalen Anzahl von Agents geordnet. Je näher bei Null die Position eines Agents ist, umso höher ist die Priorität dieses Agents. Agents mit einer höheren Priorität werden zuerst aufgerufen. Weitere Informationen zur Priorität von Agents finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).

Im folgenden Beispiel wird die Priorität eines Cmdlet-Erweiterungs-Agents mithilfe des Cmdlets **Set-CmdletExtensionAgent** geändert. In diesem Beispiel wird die Priorität des `Scripting Agent`s in 3 geändert.

    Set-CmdletExtensionAgent "Scripting Agent" -Priority 3

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-CmdletExtensionAgent](https://technet.microsoft.com/de-de/library/dd335175\(v=exchg.150\)).

