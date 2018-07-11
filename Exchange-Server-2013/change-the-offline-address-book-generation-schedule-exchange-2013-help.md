---
title: 'Ändern des Zeitplans für die Generierung des Offlineadressbuchs: Exchange Online Help'
TOCTitle: Ändern des Zeitplans für die Generierung des Offlineadressbuchs
ms:assetid: d2b4d527-311e-442d-9f1f-54fac8371b80
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124719(v=EXCHG.150)
ms:contentKeyID: 50476784
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.OfflineAddressBookGeneralPage
ms.translationtype: MT
---

# Ändern des Zeitplans für die Generierung des Offlineadressbuchs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-12-05_

Ein Offlineadressbuch (OAB) ist eine Kopie eines Adressbuchs, das heruntergeladen wurde, damit ein Outlook-Benutzer auf die darin enthaltenen Informationen zugreifen kann, während keine Verbindung mit dem Server besteht. Sie können mit den Parametern *OABGeneratorWorkCycle* und *OABGeneratorWorkCycleCheckpoint* für das Cmdlet "Set-MailboxServer" konfigurieren, wie oft das OAB erstellt wird.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Offlineadressbücher finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der OAB-Eigenschaften mithilfe der Shell

Bei diesem Beispiel wird das Offlineadressbuch täglich alle sechs Stunden auf dem Postfachserver MBXServer01 erstellt.

    Set-MailboxServer -Identity MBXServer01 -OABGeneratorWorkCycle 01.00:00:00 -OABGeneratorWorkCycleCheckpoint 06:00:00 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OfflineAddressBook](https://technet.microsoft.com/de-de/library/aa996330\(v=exchg.150\)).

