---
title: 'Erstellen eines Offlineadressbuchs: Exchange 2013 Help'
TOCTitle: Erstellen eines Offlineadressbuchs
ms:assetid: b57bb4ce-5b6e-4702-a2f8-04bf3898a861
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124339(v=EXCHG.150)
ms:contentKeyID: 50476511
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.NewOabWizardForm.OabIntroductionWizardPage
ms.translationtype: HT
---

# Erstellen eines Offlineadressbuchs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-24_

Ein Offlineadressbuch (OAB) in Exchange Server 2013 ist eine heruntergeladene Kopie eines Adressbuchs, damit ein Outlook-Benutzer auf die darin enthaltenen Informationen zugreifen kann, während keine Verbindung mit dem Server besteht. Exchange-Administratoren können entscheiden, welche Adressbücher Benutzern zur Verfügung gestellt werden, die offline arbeiten, und sie können außerdem die Methode konfigurieren, mit der die Adressbücher verteilt werden (webbasierte Verteilung oder Verteilung in öffentlichen Ordnern).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Offlineadressbücher finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Offlineadressbuchs mit webbasierter Verteilung mithilfe der Verwaltungsshell

In diesem Beispiel wird ein Onlineadressbuch namens "OAB\_Contoso" erstellt, für das die webbasierte Verteilung für Clients mit Outlook 2007 oder höher verwendet wird, wozu das virtuelle Standardverzeichnis genutzt wird.

    New-OfflineAddressBook -Name "OAB_Contoso" -AddressLists "\Default Global Address List" -VirtualDirectories $Null -GlobalWebDistributionEnabled $True

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-OfflineAddressBook](https://technet.microsoft.com/de-de/library/bb123692\(v=exchg.150\)).

