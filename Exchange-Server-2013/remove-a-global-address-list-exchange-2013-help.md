---
title: 'Entfernen einer globalen Adressliste: Exchange 2013 Help'
TOCTitle: Entfernen einer globalen Adressliste
ms:assetid: 65d75b69-641b-4a37-a63c-47cf018f5f22
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232077(v=EXCHG.150)
ms:contentKeyID: 50475842
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer globalen Adressliste

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Eine globale Adressliste (Global Address List, GAL) ist ein Verzeichnis, das Einträge für alle Gruppen, Benutzer und Kontakte in einer Exchange-Organisation enthält.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Die globale Standardadressliste kann nicht entfernt werden.

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Entfernen einer globalen Adressliste

In diesem Beispiel wird die globale Adressliste "Fourth Coffee" vom Domänencontroller "ad-server.fourthcoffee.com" entfernt.

    Remove-GlobalAddressList -Identity "Fourth Coffee" -DomainController ad-server.fourthcoffee.com

Geben Sie **J** ein, um das Entfernen der GAL zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-GlobalAddressList](https://technet.microsoft.com/de-de/library/bb124368\(v=exchg.150\)).

