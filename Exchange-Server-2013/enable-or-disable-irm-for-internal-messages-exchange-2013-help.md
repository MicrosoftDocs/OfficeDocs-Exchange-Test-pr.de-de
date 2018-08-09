---
title: 'Aktivieren oder Deaktivieren von IRM für interne Nachr.: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren von IRM für interne Nachrichten
ms:assetid: a6a17f57-5304-41f1-954d-7301857d54a1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124077(v=EXCHG.150)
ms:contentKeyID: 50476368
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von IRM für interne Nachrichten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

In Microsoft Exchange Server 2013 ist die Verwaltung von Informationsrechten (Information Rights Management, IRM) für interne Nachrichten standardmäßig aktiviert. Auf diese Weise können Sie Transportschutzregeln und Microsoft Outlook-Schutzregeln für IRM-geschützte Nachrichten im Transport und auf Clients mit Microsoft Outlook 2010 und höher erstellen. Das Aktivieren von IRM für interne Nachrichten ist eine Voraussetzung für alle weiteren IRM-Funktionen in Exchange Server 2013, wie beispielsweise Transportentschlüsselung, Journalregelentschlüsselung, IRM in Microsoft Office Outlook Web App und IRM in Microsoft Exchange ActiveSync.


> [!WARNING]
> Durch das Deaktivieren von IRM für interne Nachrichten werden alle IRM-Funktionen in der Exchange-Organisation deaktiviert. Die clientseitigen IRM-Funktionen in Outlook,&nbsp;beispielsweise die Funktion zum Lesen, Antworten auf, Weiterleiten und Erstellen von IRM-geschützten Nachrichten mithilfe eines Active Directory&nbsp;RMS-Servers (AD-Rechteverwaltungsdienste) sind nicht betroffen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Aktivieren oder Deaktivieren der IRM-Protokollierung für interne Nachrichten verwendet werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktivieren von IRM für interne Nachrichten mithilfe der Shell

In diesem Beispiel wird IRM für interne Nachrichten der Exchange-Organisation aktiviert.

    Set-IRMConfiguration -InternalLicensingEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Deaktivieren von IRM für interne Nachrichten mithilfe der Shell

In diesem Beispiel wird IRM für interne Nachrichten der Exchange-Organisation deaktiviert.

    Set-IRMConfiguration -InternalLicensingEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Verwenden Sie das Cmdlet [Get-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd776120\(v=exchg.150\)), um zu überprüfen, ob IRM für interne Nachrichten aktiviert oder deaktiviert wurde.

