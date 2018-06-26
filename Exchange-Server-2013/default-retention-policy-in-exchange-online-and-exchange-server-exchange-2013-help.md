---
title: 'Standardaufbewahrungsrichtlinie in Exchange Online und Exchange Server: Exchange 2013 Help'
TOCTitle: Standardaufbewahrungsrichtlinie
ms:assetid: bcf31b2d-463b-4623-b488-c8ac40f14f62
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn775046(v=EXCHG.150)
ms:contentKeyID: 62625970
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Standardaufbewahrungsrichtlinie in Exchange Online und Exchange Server

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Exchange erstellt die Aufbewahrungsrichtlinie "MRM-Standardrichtlinie" in Exchange Online und der lokalen Exchange-Organisation. Die Richtlinie wird automatisch auf neue Benutzer in Exchange Online angewendet. In lokalen Organisationen wird die Richtlinie angewendet, wenn Sie ein Archiv für das Postfach erstellen. Sie können die auf einen Benutzer angewendete Aufbewahrungsrichtlinie jederzeit ändern.

Sie können Tags modifizieren, die in der MRM-Standardrichtlinie enthalten sind, z. B., indem Sie die Verfallszeit für die Aufbewahrung oder die Aufbewahrungsaktionen ändern, ein Tag deaktivieren oder die Richtlinie ändern, indem Sie Tags zu ihr hinzufügen oder aus ihr entfernen. Die aktualisierte Richtlinie wird ab der nächsten Verarbeitung von Postfächern durch den Assistenten für verwaltete Ordner auf die Postfächer angewendet.

## Mit der MRM-Standardrichtlinie verknüpfte Aufbewahrungstags

In der folgenden Tabelle sind die Standardaufbewahrungstags aufgeführt, die mit der MRM-Standardrichtlinie verknüpft sind.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Aufbewahrungszeitraum (Tage)</th>
<th>Aufbewahrungsaktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standard, 2 Jahre, in Archiv verschieben</p></td>
<td><p>Standardrichtlinientag</p></td>
<td><p>730</p></td>
<td><p>In Archiv verschieben</p></td>
</tr>
<tr class="even">
<td><p>Wiederherstellbare Elemente, 14 Tage, in Archiv verschieben</p></td>
<td><p>Ordner &quot;Wiederherstellbare Elemente&quot;</p></td>
<td><p>14</p></td>
<td><p>In Archiv verschieben</p></td>
</tr>
<tr class="odd">
<td><p>Persönlich, 1 Jahre, in Archiv verschieben</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>365</p></td>
<td><p>In Archiv verschieben</p></td>
</tr>
<tr class="even">
<td><p>Persönlich, 5 Jahre, in Archiv verschieben</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>1,825</p></td>
<td><p>In Archiv verschieben</p></td>
</tr>
<tr class="odd">
<td><p>Persönlich, nie in Archiv verschieben</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>In Archiv verschieben</p></td>
</tr>
<tr class="even">
<td><p>1 Woche, löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>7</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="odd">
<td><p>1 Monat, löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>30</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="even">
<td><p>6 Monate, löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>180</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="odd">
<td><p>1 Jahr, löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>365</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="even">
<td><p>5 Jahre, löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>1,825</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="odd">
<td><p>Nie löschen</p></td>
<td><p>Persönliches Tag</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
</tbody>
</table>


## Möglichkeiten der MRM-Standardrichtlinie


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Möglichkeit ...</th>
<th>In Exchange Online ...</th>
<th>In Exchange Server ...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Automatisches Anwender der MRM-Standardrichtlinie auf neue Benutzer</p></td>
<td><p>Ja, standardmäßig angewendet. Es ist keine Aktion erforderlich.</p></td>
<td><p>Ja, standardmäßig angewendet, wenn Sie auch ein Archiv für den neuen Benutzer erstellen.</p>
<p>Wenn Sie später ein Archiv für den Benutzer erstellen, wird die Richtlinie nur dann automatisch angewendet, wenn der Benutzer keine vorhandene Aufbewahrungsrichtlinie hat.</p></td>
</tr>
<tr class="even">
<td><p>Ändern des Aufbewahrungsalters oder der Aufbewahrungsaktion eines Aufbewahrungstags, das mit der Richtlinie verknüpft ist</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Deaktivieren eines Aufbewahrungstags, das mit der Richtlinie verknüpft ist</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Hinzufügen eines Aufbewahrungstag zur Richtlinie</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Entfernen eines Aufbewahrungstags aus der Richtlinie</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Festlegen einer anderen Richtlinie als Standardaufbewahrungsrichtlinie, die automatisch auf neue Benutzer angewendet wird</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

  - Ein Aufbewahrungstag kann mit mehr als einer Aufbewahrungsrichtlinie verknüpft werden. Weitere Informationen zum Verwalten von [Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md) finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

  - Die MRM-Standardrichtlinie enthält kein Standardrichtlinientag, um Elemente (sie enthält jedoch persönliche Tags mit der Aufbewahrungsaktion zum Löschen, die Benutzer auf ihre Postfachelemente anwenden können) automatisch zu löschen. Wenn Sie Elemente nach einer bestimmten Zeit automatisch löschen möchten, können Sie ein Standardrichtlinientag mit der erforderlichen Löschaktion erstellen und es der Richtlinie hinzufügen. Ausführliche Informationen finden Sie unter [Erstellen einer Aufbewahrungsrichtlinie](create-a-retention-policy-exchange-2013-help.md) und [Hinzufügen von Aufbewahrungstags zu oder Entfernen von Aufbewahrungstags aus einer Aufbewahrungsrichtlinie](add-retention-tags-to-or-remove-retention-tags-from-a-retention-policy-exchange-2013-help.md).

  - Aufbewahrungsrichtlinien werden auf die Postfachbenutzer angewendet. Für das Postfach und das Archiv des Benutzers gilt dieselbe Richtlinie.

