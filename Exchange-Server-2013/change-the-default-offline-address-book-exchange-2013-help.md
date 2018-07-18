---
title: 'Ändern des Standard-Offlineadressbuchs: Exchange 2013 Help'
TOCTitle: Ändern des Standard-Offlineadressbuchs
ms:assetid: 61abf78e-2543-4431-acc8-839e3c7a4548
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998569(v=EXCHG.150)
ms:contentKeyID: 50475805
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern des Standard-Offlineadressbuchs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Wenn Sie die Postfachserverrolle installieren, wird standardmäßig das webbasierte Standard-Offlineadressbuch (Offline Address Book, OAB) "Standard-Offlineadressbuch" erstellt. Sie können jedoch jedes beliebige OAB in Ihrer Exchange-Organisation als Standard-OAB festlegen. Dieses neue Standard-OAB wird allen neu erstellten Postfachdatenbanken zugeordnet. In einer Organisation kann es nur ein Standard-OAB geben. Wenn Sie das Standard-OAB löschen, wird von MicrosoftExchange nicht automatisch ein anderes OAB als Standard-OAB zugewiesen. Sie müssen manuell ein anderes OAB als Standard-OAB zuweisen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Ändern des Standard-OABs mithilfe der Shell

In diesem Beispiel wird das Offlineadressbuch "My OAB" als Standard-OAB festgelegt.

    Set-OfflineAddressBook -Identity "My OAB" -IsDefault $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OfflineAddressBook](https://technet.microsoft.com/de-de/library/aa996330\(v=exchg.150\)).

