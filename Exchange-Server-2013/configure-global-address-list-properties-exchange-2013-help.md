---
title: 'Konfigurieren der Eigenschaften von globalen Adresslisten: Exchange 2013 Help'
TOCTitle: Konfigurieren der Eigenschaften von globalen Adresslisten
ms:assetid: 5fd2c96f-fe93-4b5a-8495-70c450511a37
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232068(v=EXCHG.150)
ms:contentKeyID: 50475763
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Eigenschaften von globalen Adresslisten

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

In diesem Thema wird erläutert, wie Sie die Einstellungen einer globalen Adressliste (GAL) ändern.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Die Einstellungen der Standard-GAL können nicht bearbeitet werden.

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Konfigurieren von GAL-Eigenschaften

In diesem Beispiel wird der GAL mit der GUID 96d0c505-eba8-4103-ad4f-577a1bf4ad7b der neue Name "FourthCoffee" zugewiesen.

    Set-GlobalAddressList -Identity 96d0c505-eba8-4103-ad4f-577a1bf4ad7b -Name FourthCoffee


> [!NOTE]
> Wenn Sie Bedingungsmusterfilter-Eigenschaften verwenden, darf der Wert für den Parameter <EM>IncludedRecipients</EM> nicht leer sein.



In diesem Beispiel werden die Empfänger, die in der globalen Adressliste "Fourth Coffee" enthalten sind, in die geändert, deren Unternehmen auf "Fourth Coffee" gesetzt ist.

    Set-GlobalAddressList -Identity Fourth Coffee -RecipientFilter {Company -eq "Fourth Coffee"}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-GlobalAddressList](https://technet.microsoft.com/de-de/library/bb123877\(v=exchg.150\)).

