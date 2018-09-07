---
title: 'Erstellen einer Adressbuchrichtlinie: Exchange Online Help'
TOCTitle: Erstellen einer Adressbuchrichtlinie
ms:assetid: 6359abaf-e6f6-4667-8c2b-3860728b39a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529931(v=EXCHG.150)
ms:contentKeyID: 50475818
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Adressbuchrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Adressbuchrichtlinien ermöglichen Ihnen die Einteilung von Benutzern in bestimmte Gruppen, um benutzerdefinierte Ansichten der globalen Adressliste Ihrer Organisation bereitzustellen. Bei der Erstellung einer ABP weisen Sie der Richtlinie eine globale Adressliste (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine oder mehrere Adresslisten zu. Anschließend können Sie die ABP Postfachbenutzern zuweisen und diesen den Zugriff auf eine benutzerdefinierte GAL in Outlook und Outlook Web App bereitstellen. Das Ziel besteht darin, einen einfacheren Mechanismus zum Durchführen der GAL-Segmentierung für lokale Organisationen bereitzustellen, die mehrere GALs benötigen. Weitere Informationen zu ABPs finden Sie unter [Adressbuchrichtlinien](https://review.docs.microsoft.com/de-de/exchange/address-books/address-book-policies/address-book-policies).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adressbuchrichtlinien finden Sie unter [Verfahren für Adressbuchrichtlinien](address-book-policy-procedures-exchange-2013-help.md).

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet werden? Weitere Informationen finden Sie unter [Szenario: Bereitstellen von Adressbuchrichtlinien](scenario-deploying-https://docs.microsoft.com/de-de/exchange/address-books/address-book-policies/address-book-policies).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adressbuchrichtlinien" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe\&quot; im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Die Erstellung einer Adressbuchrichtlinie für eine Organisation ist ein Prozess mit vielen Schritten, der eine sorgfältige Planung erfordert. Weitere Informationen finden Sie unter [Szenario: Bereitstellen von Adressbuchrichtlinien](scenario-deploying-https://docs.microsoft.com/de-de/exchange/address-books/address-book-policies/address-book-policies).

  - Adressbuchrichtlinien können nicht mithilfe der Exchange-Verwaltungskonsole erstellt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Erstellen einer Adressbuchrichtlinie mithilfe der Shell

In diesem Beispiel wird eine Adressbuchrichtlinie mit den folgenden Einstellungen erstellt:

  - **Name:**  All Fabrikam ABP

  - **GAL:**  All Fabrikam

  - **OAB:**  Fabrikam-All-OAB

  - **Raumliste:**  All Fabrikam Rooms

  - **Adresslisten:**  "All Fabrikam", "All Fabrikam Mailboxes", "All Fabrikam DLs" und "All Fabrikam Contacts"

<!-- end list -->

    New-AddressBookPolicy -Name "All Fabrikam ABP" -AddressLists "\All Fabrikam","\All Fabrikam Mailboxes","\All Fabrikam DLs","\All Fabrikam Contacts" -OfflineAddressBook \Fabrikam-All-OAB -GlobalAddressList "\All Fabrikam" -RoomList "\All Fabrikam Rooms"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-AddressBookPolicy](https://technet.microsoft.com/de-de/library/hh529913\(v=exchg.150\)).

## Weitere Informationen

[Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern](https://review.docs.microsoft.com/de-de/exchange/address-books/address-book-policies/assign-an-address-book-policy-to-mail-users)

