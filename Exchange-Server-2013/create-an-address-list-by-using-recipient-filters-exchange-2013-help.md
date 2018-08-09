---
title: 'Erstellen e. Adressliste mithilfe von Empfängerfiltern: Exchange 2013-Hilfe'
TOCTitle: Erstellen einer Adressliste mithilfe von Empfängerfiltern
ms:assetid: 8eabea64-97c6-40af-b61c-9b6a125cbdf1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123718(v=EXCHG.150)
ms:contentKeyID: 50476230
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Adressliste mithilfe von Empfängerfiltern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

In diesem Thema wird das Erstellen einer Adressliste mithilfe von Empfängerfiltern erläutert. Weitere Informationen zu Adresslisten finden Sie unter [Adresslisten](address-lists-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe\&quot; im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Wenn der Parameter *RecipientFilter* zum Erstellen eines benutzerdefinierten Filters verwendet werden soll, müssen Sie eine Zeichenfolge für den Filter angeben. Die Shell verwendet OPATH für die Filtersyntax. OPATH ist eine Abfragesprache, mit der Objektdatenquellen abgefragt werden können.

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Erstellen einer Adressliste mithilfe von Empfängerfiltern

In diesem Beispiel wird eine Adressliste aller Benutzer mit Exchange-Postfächern erstellt, die in Washington oder Oregon wohnen.

    New-AddressList -Name "Pacific Northwest Mailboxes" -RecipientFilter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}

In diesem Beispiel wird eine Adressliste für alle Benutzer mit Exchange-Postfächern erstellt, bei denen `AgencyB` als Wert für den Parameter *CustomAttribute15* festgelegt ist.

    New-AddressList -Name "AgencyB" -RecipientFilter {(RecipientType -eq 'UserMailbox') -and (CustomAttribute15 -like *AgencyB*)}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-AddressList](https://technet.microsoft.com/de-de/library/aa996912\(v=exchg.150\)).

