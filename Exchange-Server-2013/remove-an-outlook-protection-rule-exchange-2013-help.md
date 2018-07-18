---
title: 'Entfernen Sie eine Outlook-Schutzregel: Exchange 2013 Help'
TOCTitle: Entfernen Sie eine Outlook-Schutzregel
ms:assetid: 569fc3be-b269-43f5-8797-73ab0691e685
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633467(v=EXCHG.150)
ms:contentKeyID: 50475690
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen Sie eine Outlook-Schutzregel

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit Microsoft Outlook-Schutzregeln, können Sie Nachrichten mit Information Rights Management (IRM) schützen, indem Sie eine [Active Directory-Rechteverwaltungsdienste (AD RMS)](https://technet.microsoft.com/en-us/library/hh831364.aspx) Vorlage in Outlook 2010 anwenden, bevor die Testnachrichten gesendet werden. Um zu verhindern, dass eine Outlook-Schutzregel angewendet wird, können Sie die Regel deaktivieren. Eine Outlook Schutzregel entfernen Entfernt die Regeldefinition aus Active Directory.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Entfernen von Outlook-Schutzregeln verwendet werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Entfernen einer Outlook-Schutzregel

In diesem Beispiel wird die Outlook-Schutzregel "OPR-DG-Finance" entfernt.

    Remove-OutlookProtectionRule -Identity "OPR-DG-Finance"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd297961\(v=exchg.150\)).

## Verwenden der Shell zum Entfernen aller Outlook-Schutzregeln

In diesem Beispiel werden alle Outlook-Schutzregeln in der Exchange-Organisation entfernt.

    Get-OutlookProtectionRule | Remove-OutlookProtectionRule

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd298004\(v=exchg.150\)) und [Remove-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd297961\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Verwenden Sie das Cmdlet [Get-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd298004\(v=exchg.150\)) zum Abrufen von Outlook-Schutzregeln, um sicherzustellen, dass eine Outlook-Schutzregel erfolgreich entfernt wurde. Ein Beispiel zum Abrufen von Outlook-Schutzregeln finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/dd298004\(exchg.150\)#examples) in **Get-OutlookProtectionRule**.

