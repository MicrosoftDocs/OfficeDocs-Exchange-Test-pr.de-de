---
title: 'Erstellen einer globalen Adressliste: Exchange 2013 Help'
TOCTitle: Erstellen einer globalen Adressliste
ms:assetid: 59e4955a-8999-4d17-be9f-23a41a23b929
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232063(v=EXCHG.150)
ms:contentKeyID: 50475714
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer globalen Adressliste

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Eine globale Adressliste ist ein Verzeichnis, das Einträge für alle Gruppen, Benutzer und Kontakte in der Microsoft Exchange-Implementierung einer Organisation enthält. Wenn in Ihrer Organisation Adressbuchrichtlinien verwendet werden, möchten Sie vielleicht zusätzliche globale Adresslisten (GALs) erstellen. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer GAL unter Verwendung von Bedingungsfiltereigenschaften mithilfe der Shell

In diesem Beispiel wird eine globale Adressliste namens "GAL\_Contoso" für Empfänger erstellt, die Postfachbenutzer sind und als deren Unternehmen "Contoso" aufgeführt ist.

    New-GlobalAddressList -Name "GAL_Contoso" -IncludedRecipients MailboxUsers -ConditionalCompany Contoso


> [!NOTE]
> Wenn Sie Bedingungsmusterfilter-Eigenschaften verwenden, darf der Parameter <EM>IncludedRecipients</EM> nicht leer sein.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-GlobalAddressList](https://technet.microsoft.com/de-de/library/bb123785\(v=exchg.150\)).

## Erstellen einer GAL unter Verwendung eines Empfängerfilters mithilfe der Shell

In diesem Beispiel wird eine globale Adressliste namens "GAL\_AgencyA" für Empfänger erstellt, bei denen der Parameter *CustomAttribute15* den Wert `AgencyA` aufweist.

    New-GlobalAddressList -Name "GAL_AgencyA" -RecipientFilter {CustomAttribute15 -like "AgencyA"}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-GlobalAddressList](https://technet.microsoft.com/de-de/library/bb123785\(v=exchg.150\)).

