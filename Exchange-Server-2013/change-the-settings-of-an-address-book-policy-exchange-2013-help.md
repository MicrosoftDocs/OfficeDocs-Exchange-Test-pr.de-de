---
title: 'Ändern der Einstellungen einer Adressbuchrichtlinie: Exchange 2013 Help'
TOCTitle: Ändern der Einstellungen einer Adressbuchrichtlinie
ms:assetid: ba1ca350-71c2-4c60-a612-33bfa9320b5e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529941(v=EXCHG.150)
ms:contentKeyID: 50476529
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern der Einstellungen einer Adressbuchrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-03-30_

Nach der Erstellung einer Adressbuchrichtlinie (Address Book Policy, ABP) können Sie deren Namen und die zugewiesene globale Adressliste (GAL), das Offlineadressbuch (OAB), die Raumliste und die Adresslisten anzeigen oder ändern.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adressbuchrichtlinien finden Sie unter [Verfahren für Adressbuchrichtlinien](address-book-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adressbuchrichtlinien" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Die Erstellung einer Adressbuchrichtlinie für eine Organisation ist ein Prozess mit vielen Schritten, der eine sorgfältige Planung erfordert. Weitere Informationen finden Sie unter [Szenario: Bereitstellen von Adressbuchrichtlinien](scenario-deploying-address-book-policies-exchange-2013-help.md)

  - Adressbuchrichtlinien können nicht in der Exchange-Verwaltungskonsole konfiguriert werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Was möchten Sie machen?

## Ändern des Offlineadressbuchs, der Raumliste und globalen Adressliste einer Adressbuchrichtlinie

In diesem Beispiel werden das Offlineadressbuch, die Raumliste und die globale Adressliste geändert, die von Postfachbenutzern verwendet werden, welche der Adressbuchrichtlinie namens "All Fabrikam ABP" zugewiesen sind.

    Set-AddressBookPolicy -Identity "All Fabrikam ABP" -OfflineAddressBook \Fabrikam-OAB-2 -GlobalAddressList "\All Fabrikam GAL" -RoomList "\All Fabrikam Rooms"

## Ersetzen von Adresslistes in einer Adressbuchrichtlinie

Die Adresslisten, die Sie für eine vorhandene Adressbuchrichtlinie angeben, ersetzen alle Adresslisten in der Adressbuchrichtlinie.

In diesem Beispiel werden die vorhandenen Adresslisten durch die Adresslisten „GovernmentAgencyA-Atlanta“ und „GovernmentAgencyA-Moscow“ für die Adressbuchrichtlinie namens „GovernmentAgencyA“ ersetzt.

    Set-AddressBookPolicy -Identity "Government Agency A" -AddressLists "GovernmentAgencyA-Atlanta","GovernmentAgencyA-Moscow"

## Hinzufügen von Adresslisten zu einer Adressbuchrichtlinie

Um Adresslisten beizubehalten, die bereits in einer Adressbuchrichtlinie definiert sind, müssen Sie diese Adresslisten angeben, wenn Sie die neuen zu der Adressbuchrichtlinie hinzufügen.

In diesem Beispiel wird die Adressliste mit dem Namen „Contoso-Chicago“ der Adressbuchrichtlinie mit dem Namen „ABP Contoso“ hinzugefügt, die bereits so konfiguriert ist, dass die Adressliste mit dem Namen „Contoso-Seattle“ verwendet wird.

    Set-AddressBookPolicy -Identity "ABP Contoso" -AddressLists "Contoso-Chicago","Contoso-Seattle"

## Entfernen von Adresslisten aus einer Adressbuchrichtlinie

Um vorhandene Adresslisten zu entfernen, die bereits in einer Adressbuchrichtlinie definiert sind, müssen Sie diese Adresslisten angeben, die Sie behalten möchten.

Die Adressbuchrichtlinie „ABP Fabrikam“ verwendet beispielsweise die Adresslisten mit dem Namen „Fabrikam-HR“ und „Fabrikam-Finance“. Geben Sie zum Entfernen der Adressliste „Fabrikam-HR“ aus der Adressbuchrichtlinie die Fabrikam-Finance-Adressliste an, die Sie behalten möchten.

    Set-AddressBookPolicy -Identity "ABP Fabrikam" -AddressLists Fabrikam-Finance

## Weitere Informationen

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-AddressBookPolicy](https://technet.microsoft.com/de-de/library/hh529945\(v=exchg.150\)).

