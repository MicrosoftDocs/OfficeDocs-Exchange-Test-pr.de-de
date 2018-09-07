---
title: 'Hinzufügen und Entfernen von Adresslisten in einem Offlineadressbuch'
TOCTitle: Hinzufügen einer Adressliste zu oder Entfernen einer Adressliste aus einem Offlineadressbuch
ms:assetid: 86bd5651-ad41-4516-bf23-6579f4e4da03
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123563(v=EXCHG.150)
ms:contentKeyID: 50476093
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen einer Adressliste zu oder Entfernen einer Adressliste aus einem Offlineadressbuch

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Mithilfe der Shell können Sie einem Offlineadressbuch (OAB) eine Adressliste hinzufügen bzw. daraus entfernen. In der Standardeinstellung ist ein OAB mit der Bezeichnung "Standard-Offlineadressbuch" vorhanden, das die globale Adressliste (GAL) enthält. OABs werden auf der Grundlage der Adresslisten generiert, die sie enthalten. Um benutzerdefinierte OABs zu erstellen, die von Benutzern heruntergeladen werden können, können Sie OABs Adresslisten hinzufügen oder Adresslisten aus OABs entfernen. 

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - UNRESOLVED\_TOKENBLOCK\_VAL(GENL\_AddressListRole\_EXOnOP)

  - Änderungen an der Adressliste stehen erst für den Clientdownload zur Verfügung, nachdem das OAB, in dem die Adressliste gespeichert ist, generiert wurde. Weitere Informationen finden Sie unter [Aktualisieren eines Offlineadressbuchs](https://review.docs.microsoft.com/de-de/exchange/address-books/offline-address-books/update-offline-address-book).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Hinzufügen einer Adressliste zu einem OAB mithilfe der Shell

Bei Verwendung des Parameters *AddressLists* werden alle zurzeit vorhandenen Adresslisten überschrieben. Bei Verwendung des Parameters *AddressLists* müssen Sie vorhandene Adresslisten einschließen, damit diese Adresslisten weiterhin in Ihrem OAB generiert werden können. In diesem Beispiel wird den bereits vorhandenen Adresslisten "AddressList1" und "AddressList2" die Adressliste "AddressList3" hinzugefügt.

    Set-OfflineAddressBook -Identity "My OAB" -AddressLists AddressList1,AddressList2,AddressList3

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OfflineAddressBook](https://technet.microsoft.com/de-de/library/aa996330\(v=exchg.150\)).

## Entfernen einer Adressliste aus einem OAB mithilfe der Shell

Zum Entfernen einer Adressliste aus einem OAB lassen Sie diese Adressliste einfach in der Liste der Adresslisten aus. In diesem Beispiel wird "AddressList3" aus der Liste der vorhandenen Adresslisten "AddressList1", "AddressList2" und "AddressList3" entfernt.

    Set-OfflineAddressBook -Identity "My OAB" -AddressLists AddressList1,AddressList2

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OfflineAddressBook](https://technet.microsoft.com/de-de/library/aa996330\(v=exchg.150\)).

