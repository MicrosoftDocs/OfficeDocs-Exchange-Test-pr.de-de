---
title: 'Grundlegendes zu exklusiven Bereichen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu exklusiven Bereichen
ms:assetid: 32492622-3b01-4e3b-8288-ed39525eea75
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638110(v=EXCHG.150)
ms:contentKeyID: 50475424
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu exklusiven Bereichen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

*Exklusive Bereiche* bezeichnen einen besonderen Typ von Verwaltungsbereich, der Verwaltungsrollenzuweisungen zugeordnet werden kann. Exklusive Bereiche sind für Situationen konzipiert, in denen Sie über Objekte mit hohen Sicherheitsanforderungen, z. B. ein Postfach des Geschäftsführers, verfügen und den Zugriff auf dieses Objekt streng kontrollieren möchten.

Eine Rollenzuweisung mit einem exklusiven Bereich wird als *exklusive Rollenzuweisung* bezeichnet.

Wenn Sie einen exklusiven Bereich erstellen, können nur diejenigen Benutzer, die diesem exklusiven Bereich oder einem äquivalenten Bereich zugewiesen sind, die Objekte für diesen Bereich ändern. Rollenempfänger, die nicht diesem exklusiven Bereich oder einem äquivalenten Bereich zugewiesen sind, können keine Objekte für diesen Bereich ändern – selbst dann nicht, wenn ihre eigenen Rollen über Bereiche verfügen, die die Objekte ansonsten einschließen würden. Exklusive Bereiche überschreiben andere reguläre Bereiche, die nicht exklusiv sind. Dieses Verhalten ähnelt einem Zugriffsverweigerungseintrag in einer Active Directory-Zugriffssteuerungsliste (Access Control List, ACL).

Ein *äquivalenter exklusiver Bereich* bezieht sich auf einen anderen exklusiven Bereich, der einige der Objekte des anderen exklusiven Bereichs umfasst. Die Bereiche müssen nicht den gleichen vollständigen Satz von Objekten umfassen. Beide Bereiche können die Änderung einiger oder aller enthaltenen Objekte zulassen.

## Erstellen exklusiver Bereiche

Exklusive Bereiche können wie andere explizite Bereiche erstellt werden. Sie können einen vordefinierten relativen Bereich, einen Empfangs-, Datenbank- oder Serverfilter oder eine Datenbank- oder Serverliste angeben. Im Gegensatz zu regulären Bereichen, die erst bei Zuordnung des Bereichs zu einer Verwaltungsrollenzuweisung in Kraft treten, findet der Aspekt der Zugriffsverweigerung für einen exklusiven Bereich sofort Anwendung. Dies bedeutet, dass die beim Erstellen eines exklusiven Bereichs in diesem Bereich enthaltenen Objekte sofort für den Benutzerzugriff gesperrt werden, bis die Rollenzuweisung erstellt wird.

Nach der Erstellung der Zuweisung gewährt der exklusive Bereich denjenigen Benutzern Zugriff, denen die Verwaltungsrolle sowie der Bereich zugewiesen wurde. Wenn ein äquivalenter exklusiver Bereich die gleichen Objekte umfasst, kann über eine diesem exklusiven Bereich zugeordnete Rollenzuweisung weiterhin auf die Objekte zugegriffen werden.

Weitere Informationen zu Verwaltungsbereichsfiltern finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md).


> [!IMPORTANT]
> Bei der Änderung von Verwaltungsrollenkomponenten, einschließlich exklusiver Bereiche, sollten die Replikationszeiten für Active Directory berücksichtigt werden.



Wenn Sie über Objekte verfügen, die in mehr als einem exklusiven Bereich enthalten sind, wird durch die Zuweisung zu einem beliebigen der exklusiven Bereich Zugriff auf die Objekte gewährt. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt Interaktion exklusiver und regulärer Bereiche.

Exklusive Bereiche steuern nur den expliziten Empfänger- oder Konfigurationsschreibbereich einer Rollenzuweisung. Der implizite Empfänger- oder Konfigurationslesebereich der einem Benutzer oder einer Gruppe zugewiesenen Rolle gilt weiterhin. Dies bedeutet, dass Folgendes zutrifft:

  - Benutzer, denen eine Rolle zugewiesen ist, können weiterhin Objekte anzeigen, die dem impliziten Lesebereich der Rolle entsprechen.

  - Benutzer mit anderen Rollen können Objekte in einem exklusiven Bereich möglicherweise anzeigen, wenn die Lesebereiche der anderen Rollen die Objekte einschließen. Die Objekte können jedoch nur von Benutzern geändert werden, deren Rolle dem exklusiven Bereich zugeordnet ist.

Exklusive Bereiche können nur mit administrativen oder Spezialrollen verwendet werden, eine Verwendung mit Endbenutzerrollen ist nicht möglich. Weitere Informationen zu Rollen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

## Interaktion exklusiver und regulärer Bereiche

Die Abbildung am Ende dieses Abschnitts verdeutlicht, wie exklusive Bereiche mit anderen exklusiven und mit regulären Bereichen interagieren. Den Benutzern in der Abbildung sind folgende Attribute zugeordnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Benutzer</th>
<th>Ort</th>
<th>Titel</th>
<th>Abteilung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Terry</p></td>
<td><p>Vancouver</p></td>
<td><p>Accountant</p></td>
<td><p>Accounting</p></td>
</tr>
<tr class="even">
<td><p>David</p></td>
<td><p>Vancouver</p></td>
<td><p>Writer</p></td>
<td><p>Marketing</p></td>
</tr>
<tr class="odd">
<td><p>Walter</p></td>
<td><p>Vancouver</p></td>
<td><p>Manager</p></td>
<td><p>Marketing</p></td>
</tr>
<tr class="even">
<td><p>Bob</p></td>
<td><p>Vancouver</p></td>
<td><p>CEO</p></td>
<td><p>Board</p></td>
</tr>
<tr class="odd">
<td><p>Christine</p></td>
<td><p>Vancouver</p></td>
<td><p>President</p></td>
<td><p>Board</p></td>
</tr>
<tr class="even">
<td><p>Fred</p></td>
<td><p>Vancouver</p></td>
<td><p>CFO</p></td>
<td><p>Executives</p></td>
</tr>
<tr class="odd">
<td><p>Martin</p></td>
<td><p>Vancouver</p></td>
<td><p>CIO</p></td>
<td><p>Executives</p></td>
</tr>
<tr class="even">
<td><p>Kim</p></td>
<td><p>Vancouver</p></td>
<td><p>Vice President, Operations</p></td>
<td><p>Executives</p></td>
</tr>
<tr class="odd">
<td><p>Jennifer</p></td>
<td><p>Vancouver</p></td>
<td><p>Vice President, Technology</p></td>
<td><p>Executives</p></td>
</tr>
</tbody>
</table>


Die folgenden drei Verwaltungsrollenzuweisungen in der Abbildung verwalten die Benutzer in der vorstehenden Tabelle. Jede Verwaltungsrollenzuweisung verfügt über einen zugeordneten Bereich, von denen einige exklusive Bereiche sind.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Rollenzuweisung</th>
<th>Bereichsfilter</th>
<th>Exklusiv oder regulär</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Empfängeradministratoren</p></td>
<td><p>Ort = Vancouver</p></td>
<td><p>Regulär</p></td>
</tr>
<tr class="even">
<td><p>VIP-Administratoren</p></td>
<td><p>Titel = CEO oder CFO oder CIO oder President</p></td>
<td><p>Exklusiv</p></td>
</tr>
<tr class="odd">
<td><p>Führungskräfte-Administratoren</p></td>
<td><p>Abteilung = Executives</p></td>
<td><p>Exklusiv</p></td>
</tr>
</tbody>
</table>


Die Rollenzuweisung "Empfängeradministratoren" weist einen Bereich auf, der alle Benutzer umfasst, da sich alle Benutzer in Vancouver befinden. Ohne exklusive Bereiche würde dies bedeuten, dass mit der Rollenzuweisung "Empfängeradministratoren" alle Benutzer verwaltet werden können. Diese Organisation hat jedoch zwei exklusive Bereiche erstellt: "VIP-Administratoren" und "Führungskräfte-Administratoren". Diese exklusiven Bereiche schränken ein, wer die Benutzer verwalten kann, die mit dem jeweiligen Bereichsfilter übereinstimmen. Die Rollenzuweisung "VIP-Administratoren" ist mit einem Bereichsfilter versehen, der alle Benutzer mit den Titeln "CEO", "CFO", "CIO" oder "President" umfasst. Die Rollenzuweisung "Führungskräfte-Administratoren" ist mit einem Bereichsfilter versehen, der alle Benutzer in der Abteilung "Executives" umfasst.

Die Auswertung der regulären und exklusiven Bereiche führt zu dem folgenden Ergebnis:

  - Mit der Rollenzuweisung "Empfängeradministratoren" können die Benutzer Terry, David und Walter verwaltet werden. Anhand dieser Rollenzuweisung können keine weiteren Benutzer verwaltet werden, da diese mit den exklusiven Bereichsfiltern der Rollenzuweisungen "VIP-Administratoren" und "Führungskräfte-Administratoren" übereinstimmen.

  - Mit der Rollenzuweisung "VIP-Administratoren" können die Benutzer Bob, Christine, Fred und Martin verwaltet werden. Die Ursache ist, dass der exklusive Bereichsfilter, der dieser Rollenzuweisung zugeordnet ist, mit den Attributen dieser Objekte übereinstimmt. Mit dieser Rollenzuweisung können die Benutzer Kim und Jennifer nicht verwaltet werden, da ihre Attribute nicht mit dem exklusiven Bereich übereinstimmen.

  - Mit der Rollenzuweisung "Führungskräfte-Administratoren" können die Benutzer Kim, Jennifer, Fred und Martin verwaltet werden. Die Ursache ist, dass der exklusive Bereichsfilter, der dieser Rollenzuweisung zugeordnet ist, mit den Attributen dieser Objekte übereinstimmt. Mit dieser Rollenzuweisung können die Benutzer Bob und Christine nicht verwaltet werden, da ihre Attribute nicht mit dem exklusiven Bereich übereinstimmen.

Beachten Sie, dass Fred und Martin durch beide exklusiven Bereiche zugänglich sind. Die Ursache ist, dass die Attribute dieser Benutzer mit beiden exklusiven Filtern übereinstimmen.

**Interaktion zwischen exklusiven und regulären Bereichen**

![Interaktion exklusiver und regulärer Bereiche](images/Dd638110.0aa26d1d-1fa6-44d8-802d-83d75cd2624c(EXCHG.150).jpg "Interaktion exklusiver und regulärer Bereiche")

Weitere Informationen zu Verwaltungsbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

