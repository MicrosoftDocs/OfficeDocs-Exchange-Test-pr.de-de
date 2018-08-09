---
title: 'Aktiv. o. Deaktiv. d. Überw.protokoll. für Postfach: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach
ms:assetid: c4bbfd52-6196-49c7-8c31-777fbbee11f2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff461937(v=EXCHG.150)
ms:contentKeyID: 50476659
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-09-30_

Die Überwachungsprotokollierung ermöglicht das Nachverfolgen von Anmeldevorgängen für ein Postfach sowie von ausgeführten Aktionen, während der Benutzer angemeldet ist. Wenn die Überwachungsprotokollierung für ein Postfach aktiviert wird, werden einige von Administratoren und Stellvertretern ausgeführte Aktionen standardmäßig protokolliert. Keine der vom Postfachbesitzer ausgeführten Aktionen werden protokolliert. Weitere Informationen zur Postfachüberwachungsprotokollierung finden Sie unter [Überwachungsprotokollierung von Postfächern](mailbox-audit-logging-exchange-2013-help.md).


> [!WARNING]
> Die Überwachung der Aktionen von Postfachbesitzern kann zu einer großen Anzahl von Überwachungsprotokolleinträgen für ein Postfach führen und ist daher standardmäßig deaktiviert. Es wird empfohlen, die Überwachung nur für bestimmte Besitzeraktionen zu aktivieren, bei denen dies zum Erfüllen der Unternehmens- oder Sicherheitsanforderungen erforderlich ist.



Informationen zu weiteren Aufgaben in Verbindung mit der Postfachüberwachungsprotokollierung finden Sie unter [Verfahren der Postfachüberwachungsprotokollierung](mailbox-audit-logging-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Postfachüberwachungsprotokollierung kann nicht in der Exchange-Verwaltungskonsole aktiviert oder deaktiviert werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Überwachungsprotokollierung für Postfächer mithilfe der Shell

Mithilfe der Shell können Sie die Postfachüberwachungsprotokollierung für ein Postfach aktivieren oder deaktivieren. Damit wird die Protokollierung aller Vorgänge aktiviert oder deaktiviert, die für Administratoren, Stellvertretungen und den Postfachbesitzer festgelegt wurden.

In diesem Beispiel wird die Überwachungsprotokollierung für das Postfach von "Ben Smith" aktiviert.

    Set-Mailbox -Identity "Ben Smith" -AuditEnabled $true

In diesem Beispiel wird die Überwachungsprotokollierung für das Postfach von "Ben Smith" deaktiviert.

    Set-Mailbox -Identity "Ben Smith" -AuditEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Konfigurieren von Postfachüberwachungseinstellungen für den Zugriff durch Administratoren, Stellvertreter und Besitzer mithilfe der Shell

Wenn die Postfachüberwachungsprotokollierung für ein Postfach aktiviert ist, werden nur die Aktionen der Administratoren, Stellvertreter und Besitzer protokolliert, die in der Überwachungsprotokollierungskonfiguration des Postfachs angegeben wurden.

In diesem Beispiel wird festgelegt, dass die von Stellvertretern ausgeführten Aktionen `SendAs` oder `SendOnBehalf` für das Postfach von "Ben Smith" protokolliert werden.

    Set-Mailbox -Identity "Ben Smith" -AuditDelegate SendAs,SendOnBehalf -AuditEnabled $true

In diesem Beispiel wird festgelegt, dass die von Administratoren ausgeführten Aktionen `MessageBind` und `FolderBind` für das Postfach von "Ben Smith" protokolliert werden.

    Set-Mailbox -Identity "Ben Smith" -AuditAdmin MessageBind,FolderBind -AuditEnabled $true

In diesem Beispiel wird festgelegt, dass die vom Postfachbesitzer ausgeführte Aktion `HardDelete` für das Postfach von "Ben Smith" protokolliert wird.

    Set-Mailbox -Identity "Ben Smith" -AuditOwner HardDelete -AuditEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zur Sicherstellung, dass Sie die Postfachüberwachungsprotokollierung für ein Postfach erfolgreich aktiviert und die richtigen Protokollierungseinstellungen für den Zugriff von Administratoren, Stellvertretern und Besitzern festgelegt haben, verwenden Sie das Cmdlet [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)), um die Einstellungen für die Postfachüberwachungsprotokollierung für dieses Postfach abzurufen.

In diesem Beispiel werden die Postfacheinstellungen von Ben Smith abgerufen, und die angegebenen Überwachungseinstellungen einschließlich des Höchstalters werden an das Cmdlet **Format-List** übergeben.

    Get-Mailbox "Ben Smith" | Format-List *audit*

