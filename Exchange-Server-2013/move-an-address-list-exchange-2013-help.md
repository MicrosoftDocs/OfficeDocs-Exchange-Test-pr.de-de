---
title: 'Verschieben einer Adressliste: Exchange 2013 Help'
TOCTitle: Verschieben einer Adressliste
ms:assetid: c843bbd5-6c0e-41e1-b749-7ae87c1beb25
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124534(v=EXCHG.150)
ms:contentKeyID: 50476678
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verschieben einer Adressliste

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-14_

In diesem Thema wird erklärt, wie Sie eine vorhandene Adressliste in einen neuen Container unterhalb der Stammadressliste verschieben können.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verschieben einer Adressliste mithilfe der Shell

In diesem Beispiel wird die Adressliste anhand ihrer GUID in den Container "Building 4" verschoben, der sich im Container "All Users\\Sales" befindet.

    Move-AddressList -Identity c3fffd8e-026b-41b9-88c4-8c21697ac8ac -Target "\All Users\Sales\Building4"

Geben Sie **J** ein, um das Verschieben dieser Adressliste zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Move-AddressList](https://technet.microsoft.com/de-de/library/bb124520\(v=exchg.150\)).

