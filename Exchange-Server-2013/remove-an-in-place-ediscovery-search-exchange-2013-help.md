---
title: 'Entfernen einer Compliance-eDiscovery-Suche: Exchange Online Help'
TOCTitle: Entfernen einer Compliance-eDiscovery-Suche
ms:assetid: 78461a78-1255-4a26-9d36-c6b8eb82a4f9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298078(v=EXCHG.150)
ms:contentKeyID: 50475984
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer Compliance-eDiscovery-Suche

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-07-14_

In Microsoft Exchange Server 2013 können Sie die Compliance-eDiscovery zum Durchsuchen von Postfachinhalten verwenden. Sie können eine Compliance-eDiscovery-Suche jederzeit entfernen. Wenn Sie eine Compliance-eDiscovery-Suche entfernen, werden die Suchergebnisse aus dem Discoverypostfach entfernt.


> [!WARNING]
> Durch Löschen einer Compliance-eDiscovery-Suche werden alle Suchergebnisse gelöscht, die in ein Discovery-Postfach kopiert wurden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2-5 Minuten.

  - Wenn Sie eine Compliance-eDiscovery-Suche entfernen möchten, für die ein Compliance-Archiv aktiviert wurde, müssen Sie zuerst das Compliance-Archiv aus der Suche entfernen. Weitere Informationen finden Sie unter [Erstellen oder Entfernen eines Compliance-Archivs](https://docs.microsoft.com/de-de/exchange/security-and-compliance/create-or-remove-in-place-holds).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Entfernen einer Compliance-eDiscovery-Suche mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Wählen Sie in der Listenansicht die Compliance-eDiscovery-Suche aus, die Sie entfernen möchten, und klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Entfernen einer Compliance-eDiscovery-Suche mithilfe der Shell

Ein Beispiel zum Entfernen einer Compliance-eDiscovery-Suche ist im Abschnitt "Beispiele" in [Remove-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298130\(v=exchg.150\)) beschrieben.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Entfernung einer Compliance-eDiscovery-Suche zu überprüfen:

  - Verwenden Sie die Exchange-Verwaltungskonsole, um sich zu vergewissern, dass die Suche in der Listenansicht der Registerkarte **Compliance-eDiscovery & -Archiv** nicht mehr angezeigt wird.

  - Verwenden Sie das Cmdlet **Get-MailboxSearch**, um Compliance-eDiscovery-Suchen abzurufen. Ein Beispiel zum Abrufen einer Compliance-eDiscovery-Suche ist im Abschnitt "Beispiele" in [Get-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351021\(v=exchg.150\)) beschrieben.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


