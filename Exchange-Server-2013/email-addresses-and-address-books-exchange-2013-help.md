---
title: 'E-Mail-Adressen und Adressbücher: Exchange 2013 Help'
TOCTitle: E-Mail-Adressen und Adressbücher
ms:assetid: b97d0f68-691a-42af-9a6c-4dcc37b28a42
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657488(v=EXCHG.150)
ms:contentKeyID: 50476558
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# E-Mail-Adressen und Adressbücher

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Empfänger (wozu Benutzer, Ressourcen, Kontakte und Gruppen gehören) sind alle E-Mail-aktivierten Objekte in Active Directory, an die Microsoft Exchange Nachrichten senden oder weiterleiten kann. Ein Empfänger muss über eine E-Mail-Adresse verfügen, um E-Mails senden oder empfangen zu können. Adressbücher sind die Informationsquellen, über die Benutzer einander finden können, um sich E-Mails zu senden. Es gibt viele verschiedene Methoden für den Aufbau von Adressbüchern. Ausführliche Beschreibungen zu den Adressbuchfeatures in Exchange Server 2013 finden Sie unter Wichtige Terminologie.

## Wichtige Terminologie

Die folgenden Begriffe definieren die Kernkomponenten von E-Mail-Adressen und Adressbüchern in Exchange 2013.

  - **Adressbuchrichtlinien**  
    Adressbuchrichtlinien ermöglichen Ihnen die Einteilung von Benutzern in bestimmte Gruppen, um benutzerdefinierte Ansichten der globalen Adressliste Ihrer Organisation bereitzustellen. Bei der Erstellung einer ABP weisen Sie der Richtlinie eine globale Adressliste (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine oder mehrere Adresslisten zu. Anschließend können Sie die ABP Postfachbenutzern zuweisen und diesen den Zugriff auf eine benutzerdefinierte GAL in Outlook und Outlook Web App bereitstellen. Das Ziel besteht darin, einen einfacheren Mechanismus zum Durchführen der GAL-Segmentierung für lokale Organisationen bereitzustellen, die mehrere GALs benötigen.

<!-- end list -->

  - **Adresslisten**  
    Eine Adressliste ist eine Teilmenge einer globalen Adressliste (GAL). Jede Adressliste ist eine Zusammenstellung aus mindestens einem Typ von E-Mail-aktivierten Empfängern (beispielsweise Benutzer, Kontakte, Gruppen, öffentliche Ordner, Konferenz- und andere Ressourcen). Sie können Adresslisten zum Strukturieren von Empfängern und Ressourcen verwenden und auf diese Weise Benutzern das Auffinden gewünschter Empfänger und Ressourcen vereinfachen. Adresslisten werden dynamisch aktualisiert. Beim Hinzufügen neuer Benutzer zur Organisation werden diese daher automatisch allen entsprechenden Adresslisten hinzugefügt.

<!-- end list -->

  - **E-Mail-Adressrichtlinien**  
    E-Mail-Adressrichtlinien generieren die primären und sekundären E-Mail-Adressen für Ihre Empfänger, damit diese E-Mails empfangen und senden können. Standardmäßig enthält Exchange eine E-Mail-Adressrichtlinie für jeden E-Mail-aktivierten Benutzer.

<!-- end list -->

  - **Hierarchische Adressbücher**  
    Das hierarchische Adressbuch (HAB) ermöglicht es Endbenutzern, in ihrem Adressbuch über eine Organisationshierarchie, wie eine Rang- oder Führungsstruktur, nach Empfängern zu suchen. In der Regel sind die Benutzer auf die standardmäßige globale Adressliste und die zugehörigen Empfängereigenschaften begrenzt, und die Struktur der globalen Adressliste gibt häufig die Hierarchie unter den Empfängern in Ihrer Organisation nicht korrekt wieder. Dadurch, dass ein hierarchisches Adressbuch entsprechend den besonderen geschäftlichen Strukturen Ihrer Organisation angepasst werden kann, können Sie den Benutzern eine effiziente Möglichkeit zum Auffinden interner Empfänger bieten.

<!-- end list -->

  - **Offlineadressbücher**  
    Ein Offlineadressbuch (OAB) ist eine Kopie einer Sammlung von Adressbüchern, die heruntergeladen wurde, damit ein Microsoft Outlook-Benutzer auf die darin enthaltenen Informationen zugreifen kann, wenn keine Verbindung mit dem Server besteht.

## E-Mail-Adressen- und Adressbuchdokumentation

Die folgende Tabelle enthält Links zu Themen mit Informationen zur Verwaltung von E-Mail-Adressen und Adressbüchern in Exchange 2013.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/address-books/address-lists/address-lists">Adresslisten</a></p></td>
<td><p>Hier finden Sie Informationen zu Adresslisten und globalen Adresslisten zum Strukturieren von Empfängern, sodass Endbenutzer einfachen Zugang haben.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/address-books/address-book-policies/address-book-policies">Adressbuchrichtlinien</a></p></td>
<td><p>Hier finden Sie Informationen darüber, wie Sie Adresslisten und globale Adresslisten in getrennte virtuelle Organisationen aufteilen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="details-templates-exchange-2013-help.md">Detailvorlagen</a></p></td>
<td><p>Hier finden Sie Informationen zum Anpassen der Adresskarten in Outlook.</p></td>
</tr>
<tr class="even">
<td><p><a href="email-address-policies-exchange-2013-help.md">E-Mail-Adressrichtlinien</a></p></td>
<td><p>Hier finden Sie Informationen, wie mithilfe von Proxy-E-Mail-Adressen Empfänger einfacher auffindbar sind.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/address-books/hierarchical-address-books/hierarchical-address-books">Hierarchische Adressbücher</a></p></td>
<td><p>Hier finden Sie Informationen, wie Sie die globale Adressliste und Adresslisten so anpassen können, dass sie der speziellen Geschäftsstruktur Ihrer Organisation entsprechen.</p></td>
</tr>
<tr class="even">
<td><p><a href="offline-address-books-exchange-2013-help.md">Offlineadressbücher</a></p></td>
<td><p>Hier finden Sie Informationen, wie Sie für Benutzer den Offlinezugriff auf Adresslisten Ihrer Organisation ermöglichen.</p></td>
</tr>
</tbody>
</table>

