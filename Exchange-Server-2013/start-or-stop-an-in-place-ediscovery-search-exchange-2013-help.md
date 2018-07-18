---
title: 'Starten oder Stoppen einer Compliance-eDiscovery-Suche: Exchange 2013 Help'
TOCTitle: Starten oder Stoppen einer Compliance-eDiscovery-Suche
ms:assetid: 0d546763-4bf5-4523-91f4-d181b7ee4ac2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335090(v=EXCHG.150)
ms:contentKeyID: 50475066
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Starten oder Stoppen einer Compliance-eDiscovery-Suche

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-07-14_

Sie können eine Compliance-eDiscovery-Suche jederzeit beenden oder neu starten. Wenn Sie beispielsweise Sucheigenschaften ändern möchten, z. B. Schlüsselwörter oder durchsuchte Postfächer, müssen Sie zuerst einen Suchvorgang beenden. Anschließend können Sie die Suche neu starten, nachdem Sie die erforderlichen Änderungen vorgenommen haben.


> [!WARNING]
> Wenn Sie eine Compliance-eDiscovery-Suche neu starten, werden die Suchergebnisse entfernt, die in das in der Suche festgelegte Discoverypostfach kopiert wurden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Starten oder Beenden einer Compliance-eDiscovery-Suche mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery & -Archiv**.

2.  Um einen Suchvorgang zu beenden, der ausgeführt wird, wählen Sie den Suchvorgang aus, und klicken Sie dann auf **Suche beenden**.

3.  Um einen Suchvorgang zu starten, der beendet wurde, wählen Sie den Suchvorgang aus, und klicken Sie dann auf **Suche neu starten**.

## Starten oder Beenden einer Compliance-eDiscovery-Suche mithilfe der Shell

Ein Beispiel zum Starten einer Compliance-eDiscovery-Suche ist in "Beispiel 1" unter [Start-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351245\(v=exchg.150\)) beschrieben.

Ein Beispiel zum Anhalten einer Compliance-eDiscovery-Suche ist in "Beispiel 1" unter [Stop-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351075\(v=exchg.150\)) beschrieben.

