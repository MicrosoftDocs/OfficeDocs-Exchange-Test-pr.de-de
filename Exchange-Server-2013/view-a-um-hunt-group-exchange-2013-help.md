---
title: 'Anzeigen eines um-Sammelanschlusses: Exchange Online Help'
TOCTitle: Anzeigen eines um-Sammelanschlusses
ms:assetid: f038f7b4-4de9-4373-bd58-09d49e37a3ed
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125167(v=EXCHG.150)
ms:contentKeyID: 50554933
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen eines um-Sammelanschlusses

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Beim Anzeigen der Eigenschaften eines Unified Messaging-Sammelanschlusses (UM) können Sie die Eigenschaften, die einem einzelnen UM-Sammelanschluss zugeordnet sind, oder alle UM-Sammelanschlüsse anzeigen, die einem einzelnen UM-IP-Gateway zugeordnet sind. Wird kein Parameter angegeben, werden alle UM-Sammelanschlüsse zurückgegeben. Mithilfe der Exchange-Verwaltungskonsole können Sie keine Eigenschaften von UM-Sammelanschlüssen anzeigen. Dies ist nur über die Shell möglich.

Nach dem Erstellen eines UM-Sammelanschlusses können die konfigurierten Einstellungen nicht geändert werden. Wenn Sie eine Konfigurationseinstellung ändern möchten, wie z. B. die Pilot-ID eines UM-Sammelanschlusses, müssen Sie den vorhandenen UM-Sammelanschluss löschen und einen neuen UM-Sammelanschluss mit den gewünschten Einstellungen erstellen.

Informationen zu weiteren Aufgaben in Bezug auf UM-Sammelanschlüsse finden Sie unter [Um-Sammelanschlüsse Gruppieren von Prozeduren](https://technet.microsoft.com/de-de/library/JJ851063(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Sammelanschlüsse" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Sammelanschluss erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Sammelanschlusses](https://technet.microsoft.com/de-de/library/Aa997679(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Anzeigen der Eigenschaften eines UM-Sammelanschlusses mithilfe der Shell

In diesem Beispiel werden alle UM-Sammelanschlüsse in der Active Directory-Gesamtstruktur angezeigt.

    Get-UMHuntGroup

In diesem Beispiel werden die Details eines UM-Sammelanschlusses mit der Bezeichnung `MyUMHuntGroup` in einer formatierten Liste angezeigt.

    Get-UMHuntGroup -identity MyUMIPGateway\MyUMHuntGroup | Format-List


> [!NOTE]
> Bei Verwendung des Cmdlets <STRONG>Get-UMHuntGroup</STRONG> ist es nicht ausreichend, nur den Namen des UM-Sammelanschlusses anzugeben. Sie müssen auch den Namen des UM-IP-Gateways angeben, das dem UM-Sammelanschluss zugeordnet ist.


