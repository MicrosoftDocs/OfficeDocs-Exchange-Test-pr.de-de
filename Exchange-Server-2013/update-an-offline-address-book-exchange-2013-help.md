---
title: 'Aktualisieren eines Offlineadressbuchs: Exchange 2013 Help'
TOCTitle: Aktualisieren eines Offlineadressbuchs
ms:assetid: 448a207e-41b4-4cef-9fe9-a68b81e2ec4e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997684(v=EXCHG.150)
ms:contentKeyID: 50475558
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren eines Offlineadressbuchs

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-11-15_

Wenn Sie ein OAB erstellen oder OAB-Einstellungen ändern, sind die Änderungen erst für Benutzer verfügbar, nachdem der Vorgang der OAB-Generierung (OABGen) abgeschlossen wurde.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktualisieren eines Offlineadressbuchs (OAB) mithilfe der Shell

In diesem Beispiel wird das OAB "My OAB" aktualisiert.

    Update-OfflineAddressBook -Identity "My OAB"

Ausführliche Informationen zur Syntax und zu den Parametern finden Sie unter [Update-OfflineAddressBook](https://technet.microsoft.com/de-de/library/aa995979\(v=exchg.150\)).

