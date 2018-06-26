---
title: 'Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen: Exchange 2013 Help'
TOCTitle: Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen
ms:assetid: 9eb23fc9-3f59-4d09-9077-85c89a051ee0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218685(v=EXCHG.150)
ms:contentKeyID: 50474881
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-13_

Die Gruppenbenennungsrichtlinie für Verteilergruppen wird nur auf Gruppen angewendet, die von Benutzern erstellt werden. Wenn Sie oder andere Administratoren mithilfe der Exchange-Verwaltungskonsole Verteilergruppen erstellen, wird die Gruppenbenennungsrichtlinie ignoriert und nicht auf den Gruppennamen angewendet.

Wenn Sie jedoch die Exchange-Verwaltungsshell verwenden, um eine Verteilergruppe zu erstellen oder umzubenennen, wird die Gruppenbenennungsrichtlinie auch auf die von Administratoren erstellten Gruppen angewendet, sofern Sie sie nicht mit dem Parameter *IgnoreNamingPolicy* außer Kraft setzen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Außerkraftsetzen der Gruppenbenennungsrichtlinie beim Erstellen einer neuen Gruppe mithilfe der Shell

Führen Sie folgenden Befehl aus, um eine Gruppenbenennungsrichtlinie außer Kraft zu setzen.

    New-DistributionGroup -Name <Group Name> -IgnoreNamingPolicy

Wenn die Gruppenbenennungsrichtlinie für die Organisation z. B. **DG\_\<Gruppenname\>\_Users** lautet, führen Sie den folgenden Befehl aus, um eine Gruppe mit dem Namen **All Administrators** zu erstellen.

    New-DistributionGroup -Name "All Administrators" -IgnoreNamingPolicy

Wenn Microsoft Exchange diese Gruppe erstellt, wird **All Administrators** für die Parameter *Name* und *DisplayName* verwendet.

## Außerkraftsetzen der Gruppenbenennungsrichtlinie beim Umbenennen einer Gruppe mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Gruppenbenennungsrichtlinie beim Umbenennen einer vorhandenen Gruppe mit der Shell außer Kraft zu setzen.

    Set-DistributionGroup -Identity <Old Group Name> -Name <New Group Name> -DisplayName <New Group Name> -IgnoreNamingPolicy

Ein Beispiel: Sie haben kurz vor Feierabend eine Gruppenbenennungsrichtlinie erstellt und am nächsten Morgen festgestellt, dass Sie die Textzeichenfolge im Präfix falsch geschrieben haben. Am nächsten Morgen sehen Sie, dass bereits eine neue Gruppe mit dem falsch geschriebenen Präfix erstellt wurde. Sie können die Gruppenbenennungsrichtlinie in der Exchange-Verwaltungskonsole korrigieren, zum Umbenennen der Gruppe mit dem falsch geschriebenen Namen müssen Sie jedoch die Shell verwenden. Führen Sie den folgenden Befehl aus.

    Set-DistributionGroup -Identity "Goverment_Contracts_NWRegion" -Name "Government_ContractEstimates_NWRegion" -DisplayName "Government_ContractEstimates_NWRegion" -IgnoreNamingPolicy


> [!IMPORTANT]
> Geben Sie beim Umbenennen einer Gruppe immer den Parameter <EM>DisplayName</EM> an. Andernfalls wird der alte Name weiter im freigegebenen Adressbuch und in den Feldern "An:", "Cc:" und "Von:" in E-Mails angezeigt.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Befehle aus, um zu überprüfen, ob eine Verteilergruppe, in der die Gruppenbenennungsrichtlinie ignoriert wird, erfolgreich erstellt oder umbenannt wurde.

    Get-DistributionGroup <Name> | FL DisplayName

    Get-OrganizationConfig | FL DistributionGroupNamingPolicy

Wenn sich das Format des Anzeigenamens für die Gruppe von dem Format unterscheidet, das durch die Gruppenbenennungsrichtlinie Ihrer Organisation erzwungen wird, war der Vorgang erfolgreich.

