---
title: 'Entfernen eines Offlineadressbuchs: Exchange 2013 Help'
TOCTitle: Entfernen eines Offlineadressbuchs
ms:assetid: d69f1e8a-b3cb-4739-90cd-85ea450d06f3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124744(v=EXCHG.150)
ms:contentKeyID: 50476818
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen eines Offlineadressbuchs

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-12-16_

In diesem Thema wird erläutert, wie ein Offlineadressbuch (OAB) entfernt wird.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Offlineadressbücher finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Nach dem Entfernen eines Offlineadressbuchs, das einem Benutzer oder einer Postfachdatenbank zugeordnet ist, lädt der Empfänger das standardmäßige Offlineadressbuch herunter, bis Sie dem jeweiligen Benutzer ein neues Offlineadressbuch zuweisen. Wenn Sie jedoch das standardmäßige Offlineadressbuch entfernen, müssen Sie ein anderes Offlineadressbuch als standardmäßiges Offlineadressbuch zuweisen. Anweisungen zum Ändern des standardmäßigen Offlineadressbuchs finden Sie unter [Ändern des Standard-Offlineadressbuchs](change-the-default-offline-address-book-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Entfernen eines Offlineadressbuchs mithilfe der Shell

In diesem Beispiel wird das Offlineadressbuch "My OAB" entfernt.

    Remove-OfflineAddressBook -Identity "My OAB"

Geben Sie **Y** ein, um das Entfernen des Offlineadressbuchs zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-OfflineAddressBook](https://technet.microsoft.com/de-de/library/bb123594\(v=exchg.150\)).

