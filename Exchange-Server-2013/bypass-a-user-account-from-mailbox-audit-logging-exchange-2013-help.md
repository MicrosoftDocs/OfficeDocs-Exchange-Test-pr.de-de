---
title: 'Umgehen d. Postfachüberw.protokoll. für Benutzerkonto: Exchange 2013-Hilfe'
TOCTitle: Umgehen der Postfachüberwachungsprotokollierung für ein Benutzerkonto
ms:assetid: 98a87071-fe31-4b67-beb8-a73799e54df2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff461934(v=EXCHG.150)
ms:contentKeyID: 50476293
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Umgehen der Postfachüberwachungsprotokollierung für ein Benutzerkonto

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-05-21_

Wenn Sie die Postfachüberwachungsprotokollierung für ein Postfach aktivieren, werden bestimmte Postfachzugriffsereignisse (z. B. das Zugreifen auf einen Ordner oder eine Nachricht oder das dauerhafte Löschen einer Nachricht) protokolliert. Der Zugriff durch einige autorisierte Konten, z. B. Konten, die von Drittanbietertools oder für die legale Überwachung verwendet werden, kann jedoch zu einer hohen Anzahl von Einträgen im Postfachüberwachungsprotokoll führen und ist für Ihre Organisation möglicherweise nicht erforderlich.

Sie können ein Benutzer- oder Computerkonto so konfigurieren, dass die Postfachüberwachungsprotokollierung umgangen wird und von dem entsprechenden Benutzer oder Computer für ein Postfach durchgeführte Aktionen nicht protokolliert werden. Durch das Ausschließen vertrauenswürdiger Benutzer- oder Computerkonten, die häufig Zugriff auf Postfächer benötigen, können Sie unnötige Einträge in Postfachüberwachungsprotokollen vermeiden.


> [!WARNING]
> Wenn Sie die Postfachüberwachungsprotokollierung zum Überprüfen von Postfachzugriff und -aktionen verwenden, müssen Sie die Zuordnungen für die Umgehung der Postfachüberwachung regelmäßig überwachen. Wenn eine Zuordnung für die Umgehung der Postfachüberwachung für ein Konto hinzugefügt wird, kann das Konto auf alle Postfächer in der Organisation zugreifen, für die es Berechtigungen hat, ohne dass bei einem solchen Zugriff oder einer sonstigen durchgeführten Aktion (z.&nbsp;B. Postfachlöschungen) ein Eintrag im Postfachüberwachungsprotokoll generiert wird.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Postfachüberwachungsprotokollierung finden Sie unter [Verfahren der Postfachüberwachungsprotokollierung](mailbox-audit-logging-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Wird die Umgehung der Postfachüberwachungsprotokollierung für ein Konto konfiguriert, wird der Zugriff auf Postfächer durch das Konto nicht mehr protokolliert. Sie können ein Konto nicht so konfigurieren, dass die Protokollierung des Zugriffs auf ein bestimmtes Postfach umgangen wird.

  - Die Exchange-Verwaltungskonsole kann nicht zum Aktivieren oder Deaktivieren der Umgehung der Postfachüberwachungsprotokollierung für ein Konto verwendet werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Aktivieren oder Deaktivieren der Umgehung der Postfachüberwachungsprotokollierung für ein Konto

Ein Beispiel dazu, wie Sie die Postfachüberwachungsprotokollierung für ein Konto umgehen, finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/ff696758\(exchg.150\)#examples) unter [Set-MailboxAuditBypassAssociation](https://technet.microsoft.com/de-de/library/ff696758\(v=exchg.150\)).

Ein Beispiel dazu, wie Sie die Umgehung der Postfachüberwachungsprotokollierung für ein Konto deaktivieren, finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/ff696758\(exchg.150\)#examples) unter [Set-MailboxAuditBypassAssociation](https://technet.microsoft.com/de-de/library/ff696758\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nachdem Sie die Postfachüberwachungsprotokollierung für ein Konto umgangen haben, können Sie die entsprechenden Einstellungen mithilfe des Cmdlets [Get-MailboxAuditBypassAssociation](https://technet.microsoft.com/de-de/library/ff696741\(v=exchg.150\)) überprüfen.

Ein Beispiel zum Überprüfen der Zuordnungen für das Umgehen von Postfachüberwachungen finden Sie unter [Examples](https://technet.microsoft.com/de-de/ff696741\(exchg.150\)#examples) in [Get-MailboxAuditBypassAssociation](https://technet.microsoft.com/de-de/library/ff696741\(v=exchg.150\)).

