---
title: 'Durchsuchen des Überwachungsprotokolls für ein Postfach: Exchange 2013 Help'
TOCTitle: Durchsuchen des Überwachungsprotokolls für ein Postfach
ms:assetid: 5b518a08-3b51-4ba3-bfbd-0e35cc5ff374
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff461930(v=EXCHG.150)
ms:contentKeyID: 50475751
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Durchsuchen des Überwachungsprotokolls für ein Postfach

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-03_

Sie können Überwachungsprotokolleinträge für Postfächer durchsuchen und gleichzeitig die Ergebnisse in der Shell anzeigen lassen.

Wenn Sie die Überwachungsprotokolle für mehrere Postfächer durchsuchen möchten und die Ergebnisse per E-Mail an festgelegte Adressen gesendet werden sollen, müssen Sie stattdessen eine Postfachüberwachungsprotokoll-Suche erstellen. Weitere Informationen finden Sie unter [Erstellen einer Postfachüberwachungsprotokoll-Suche](create-a-mailbox-audit-log-search-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Postfachüberwachungsprotokollierung finden Sie unter [Verfahren der Postfachüberwachungsprotokollierung](mailbox-audit-logging-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Überwachungsprotokollierung ist standardmäßig für alle Postfächer deaktiviert. Für jedes zu überwachende Postfach müssen Sie die Überwachungsprotokollierung aktivieren und die Aktionen des Postfachbesitzers, Stellvertreters oder Administrators angeben, die überwacht werden sollen. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach](enable-or-disable-mailbox-audit-logging-for-a-mailbox-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Durchsuchen des Postfachüberwachungsprotokolls nach einem Postfach verwendet werden. Sie können jedoch mithilfe der Exchange-Verwaltungskonsole einen Bericht zum Postfachzugriff durch Nicht-Besitzer ausführen oder nach einem solchen Bericht suchen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Durchsuchen des Postfachüberwachungsprotokolls nach einem Postfach

Beispiele zur Verwendung der Shell zum Durchsuchen des Postfachüberwachungsprotokolls nach einem Postfach finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/ff522360\(exchg.150\)#examples) in [Search-MailboxAuditLog](https://technet.microsoft.com/de-de/library/ff522360\(v=exchg.150\)).

