---
title: 'Konfigurieren der Eigenschaften der Offlineadressbuch-Verteilung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Eigenschaften der Offlineadressbuch-Verteilung
ms:assetid: 8df985e9-75ba-47ea-9cc3-aa98a5d8acf4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123710(v=EXCHG.150)
ms:contentKeyID: 50476144
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.ClientAccess.OabDistributionGeneralPage
ms.translationtype: HT
---

# Konfigurieren der Eigenschaften der Offlineadressbuch-Verteilung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-14_

Für jeden OAB-Verteilungspunkt (Offlineadressbuch) in Exchange können zwei URLs konfiguriert werden: eine interne URL, auf die nur aus dem internen Unternehmensnetzwerk heraus zugegriffen werden kann, und eine externe URL, auf die über das Internet zugegriffen werden kann.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der OAB-Verteilungseigenschaften mithilfe der Shell

In diesem Beispiel wird das Abrufintervall für die OAB-Verteilung im virtuellen OAB-Verzeichnis "OAB" (Standardwebsite) auf sechs Stunden festgelegt.

    Set-OABVirtualDirectory "OAB (Default Web Site)" -PollInterval 360

In diesem Beispiel wird der externe Verteilungspunkt auf "https://contoso.com/OAB" für das virtuelle OAB-Standardverzeichnis "OAB" (Standardwebsite) festgelegt.

    Set-OABVirtualDirectory "OAB (Default Web Site)" -ExternalUrl https://contoso.com/OAB

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OabVirtualDirectory](https://technet.microsoft.com/de-de/library/bb124707\(v=exchg.150\)).

## Weitere Informationen

[Offlineadressbücher](offline-address-books-exchange-2013-help.md)

