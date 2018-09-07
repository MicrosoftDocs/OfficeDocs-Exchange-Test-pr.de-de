---
title: 'Hierarchische Adressbücher: Exchange 2013 Help'
TOCTitle: Hierarchische Adressbücher
ms:assetid: a1d277a0-5437-40af-aade-e4730a0d1308
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff629379(v=EXCHG.150)
ms:contentKeyID: 50476372
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hierarchische Adressbücher

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-03-26_

Das hierarchische Adressbuch (HAB) ermöglicht es Endbenutzern, in ihrem Adressbuch über eine Organisationshierarchie nach Empfängern zu suchen. In der Regel sind die Benutzer auf die standardmäßige globale Adressliste und die dazugehörigen Empfängereigenschaften begrenzt, und die Struktur der globalen Adressliste gibt häufig die Hierarchie unter den Empfängern in Ihrer Organisation nicht wieder. Dadurch, dass ein hierarchisches Adressbuch entsprechend den besonderen geschäftlichen Strukturen Ihrer Organisation angepasst werden kann, können Sie den Benutzern eine effiziente Möglichkeit zum Auffinden interner Empfänger bieten.

## Verwenden hierarchischer Adressbücher

In einem hierarchischen Adressbuch wird Ihre Stammorganisation (z. B. Contoso, Ltd) als oberste Ebene verwendet. Unter dieser obersten Ebene können Sie mehrere untergeordnete Ebenen hinzufügen, um ein angepasstes hierarchisches Adressbuch zu erstellen, das gemäß Geschäftsbereich, Abteilung oder einer beliebigen anderen gewählten Organisationsebene segmentiert ist. Die folgende Abbildung veranschaulicht ein hierarchisches Adressbuch für Contoso, Ltd mit folgender Struktur:

  - Die oberste Ebene stellt die Stammorganisation Contoso, Ltd dar.

  - Die zweite Ebene enthält die Geschäftsbereiche von Contoso, Ltd: "Corporate Office", "Product Support Organization" und "Sales & Marketing Organization".

  - Die dritte Ebene enthält die Abteilungen im Geschäftsbereich "Corporate Office": "Human Resources", "Accounting Group" und "Administration Group".

**Beispiel eines hierarchischen Adressbuchs für Contoso, Ltd**

![Hierarchisches Adressbuch – Dialogfeld](images/Ff629379.d8cc782f-61cd-44c4-9c74-432ebea0c3db(EXCHG.150).gif "Hierarchisches Adressbuch – Dialogfeld")

Über den Parameter *SeniorityIndex* können Sie eine weitere hierarchische Strukturebene hinzufügen. Verwenden Sie beim Erstellen eines hierarchischen Adressbuchs den Parameter *SeniorityIndex* zum Einstufen einzelner Empfänger oder Gruppen nach ihrem Rang innerhalb der Organisationsebenen. Diese Rangfolge gibt die Reihenfolge an, in der diese Empfänger oder Gruppen in einem hierarchischen Adressbuch angezeigt werden. Im vorherigen Beispiel wird der Parameter *SeniorityIndex* für Empfänger im Geschäftsbereich "Corporate Office" beispielsweise wie folgt festgelegt:

  - `100` für David Hamilton

  - `50` für Rajesh M. Patel

  - `25` für Amy Alberts


> [!NOTE]
> Wenn der Parameter <EM>SeniorityIndex</EM> nicht festgelegt wird oder für zwei oder mehr Benutzer übereinstimmt, wird für die Sortierreihenfolge des hierarchischen Adressbuchs der Parameterwert von <EM>PhoneticDisplayName</EM> verwendet, um die Benutzer in aufsteigender alphabetischer Reihenfolge aufzulisten. Wird der Parameter <EM>PhoneticDisplayName</EM> nicht festgelegt, wird für die Sortierung des hierarchischen Adressbuchs standardmäßig der Wert des Parameters <EM>DisplayName</EM> verwendet, und die Benutzer werden in aufsteigender alphabetischer Reihenfolge aufgelistet.



## Konfigurieren hierarchischer Adressbücher

Detaillierte Anweisung zum Erstellen hierarchischer Adressbücher finden Sie im Thema [Aktivieren oder Deaktivieren von hierarchischen Adressbüchern](https://review.docs.microsoft.com/de-de/exchange/address-books/hierarchical-address-books/enable-or-disable-hierarchical-address-books). Die allgemeinen Schritte sind wie folgt:

1.  Erstellen Sie eine Verteilergruppe, die für die Stammorganisation (oberste Ebene) verwendet wird. Nach Wunsch können Sie eine in der Exchange-Gesamtstruktur vorhandene Organisationseinheit als Verteilergruppe verwenden.

2.  Erstellen Sie Verteilergruppen für die untergeordneten Ebenen, und kennzeichnen Sie sie als Mitglieder des hierarchischen Adressbuchs. Ändern Sie den Parameter *SeniorityIndex* dieser Gruppen, damit sie innerhalb der Stammorganisation in der ordnungsgemäßen hierarchischen Reihenfolge aufgelistet werden.

3.  Fügen Sie Organisationsmitglieder hinzu. Ändern Sie den Parameter *SeniorityIndex* der Mitglieder, damit sie innerhalb der untergeordneten Ebenen in der ordnungsgemäßen hierarchischen Reihenfolge aufgelistet werden.

4.  Zur Vereinfachung des Zugriffs können Sie den Parameter *PhoneticDisplayName* verwenden, der eine phonetische Aussprache des Parameters *DisplayName* angibt.

