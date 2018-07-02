---
title: 'Speichern von Bcc-Empfängern und Empfängern aus erweiterten Verteilergruppen für eDiscovery: Exchange Online Help'
TOCTitle: Speichern von Bcc-Empfängern und Empfängern aus erweiterten Verteilergruppen für eDiscovery
ms:assetid: eb8ddf15-0080-457e-9d83-e73e193da334
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn770225(v=EXCHG.150)
ms:contentKeyID: 62516878
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Speichern von Bcc-Empfängern und Empfängern aus erweiterten Verteilergruppen für eDiscovery

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Office 365 Enterprise_

_**Letztes Änderungsdatum des Themas:** 2017-06-19_

Mit dem Compliance-Archiv, dem Beweissicherungsverfahren und [Office 365-Aufbewahrungsrichtlinien](http://go.microsoft.com/fwlink/?linkid=827811) (erstellt in Office 365 Security & Compliance Center) können Sie Postfachinhalte speichern, um rechtliche Vorschriften einzuhalten und eDiscovery-Anforderungen zu erfüllen. Informationen über Empfänger, die direkt in den Feldern "An" und "Cc" einer Nachricht adressiert werden, sind standardmäßig in allen Nachrichten enthalten, aber in Ihrer Organisation kann es erforderlich sein, nach detaillierten Informationen über alle Empfänger einer Nachricht zu suchen und sie zu reproduzieren. Dazu gehört Folgendes:

  - **Empfänger, die im Feld "Bcc" einer Nachricht adressiert werden:**  Bcc-Empfänger werden in der Nachricht im Postfach des Absenders gespeichert, aber sind nicht in den Kopfzeilen der Nachricht enthalten, die an die Empfänger gesendet wird.

  - **Empfänger in erweiterten Verteilergruppen:**  Empfänger, die die Nachricht erhalten, weil sie Mitglieder einer Verteilergruppe sind, an die die Nachricht adressiert war, entweder im Feld "An", "CC", oder "Bcc".

Exchange Online und Exchange Server 2013 (kumulatives Update 7 und höher) behalten Informationen zu Bcc-Empfängern und Empfängern in erweiterten Verteilergruppen bei. Sie können mithilfe einer Compliance-eDiscovery-Suche in der Exchange-Verwaltungskonsole oder einer Inhaltssuche in der Security & Compliance Center nach diesen Informationen suchen.

## Wie Bcc-Empfänger und Empfänger in erweiterten Verteilergruppen beibehalten werden

Wie schon zuvor erwähnt werden Informationen über Bcc-Empfänger mit der Nachricht im Postfach des Absenders gespeichert. Diese Informationen werden indiziert und stehen dann in eDiscovery und im Archiv zur Verfügung.

Informationen über Empfänger in erweiterten Verteilergruppen werden mit der Nachricht gespeichert, nachdem Sie ein Postfach in das Compliance-Archiv verschoben oder einem Beweissicherungsverfahren unterzogen haben. In Office 365 werden diese Informationen auch gespeichert, wenn eine Office 365-Aufbewahrungsrichtlinie auf ein Postfach angewendet wird. Die Mitgliedschaft in einer Verteilergruppe wird zu dem Zeitpunkt festgelegt, zu dem die Nachricht gesendet wird. Die mit der Nachricht gespeicherte erweiterte Empfängerliste ist nicht von Änderungen an der Mitgliedschaft betroffen, die nach dem Senden der Nachricht erfolgen.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Informationen über...</th>
<th>Werden gespeichert in...</th>
<th>Werden standardmäßig gespeichert...</th>
<th>Sind zugänglich für…</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Felder &quot;An&quot; und &quot;Cc&quot;</p></td>
<td><p>Nachrichteneigenschaften in den Postfächer des Absenders und der Empfänger</p></td>
<td><p>Ja</p></td>
<td><p>Absender, Empfänger und Compliance Officers</p></td>
</tr>
<tr class="even">
<td><p>Bcc-Empfänger</p></td>
<td><p>Nachrichteneigenschaft im Postfach des Absenders</p></td>
<td><p>Ja</p></td>
<td><p>Absender, Empfänger und Compliance Officers</p></td>
</tr>
<tr class="odd">
<td><p>Empfänger in erweiterten Verteilergruppen</p></td>
<td><p>Nachrichteneigenschaften im Postfach des Absenders</p></td>
<td><p>Keine. Die Informationen über die Empfänger in erweiterten Verteilergruppen werden gespeichert, nachdem ein Postfach in einem In-Situ-Speicher platziert oder ein Beweissicherungsverfahren für das Postfach aktiviert oder einer Office 365-Aufbewahrungsrichtlinie zugewiesen worden ist.</p></td>
<td><p>Compliance Officers</p></td>
</tr>
</tbody>
</table>


## Suche nach an Bcc-Empfänger oder an Empfänger in erweiterten Verteilergruppen gesendeten Nachrichten

Bei der Suche nach Nachrichten an einen bestimmten Empfänger enthalten eDiscovery-Suchergebnisse nun auch Nachrichten an Verteilergruppen, deren Mitglied der Empfänger ist. In der folgenden Tabelle werden die Szenarien gezeigt, in denen an Bcc-Empfänger oder an Empfänger in erweiterten Verteilergruppen gesendete Nachrichten in eDiscovery-Suchen zurückgegeben werden.

Szenario 1: John ist ein Mitglied der Verteilergruppe Vertrieb USA. Diese Tabelle zeigt die eDiscovery-Suchergebnisse, die zurückgegeben werden, wenn Bob eine Nachricht direkt oder (über eine Verteilergruppe) indirekt an John sendet.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Wenn Sie in Bobs Postfach nach gesendeten Nachrichten suchen...</th>
<th>Und die Nachricht gesendet wird mit...</th>
<th>Enthalten die Ergebnisse die Nachricht...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>An:John</p></td>
<td><p>John in &quot;An&quot;</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>An:John</p></td>
<td><p>Vertrieb USA in &quot;An&quot;</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>An:Vertrieb USA</p></td>
<td><p>Vertrieb USA in &quot;An&quot;</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Cc:John</p></td>
<td><p>John auf CC</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Cc:John</p></td>
<td><p>Vertrieb USA auf CC</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Cc:Vertrieb USA</p></td>
<td><p>Vertrieb USA auf CC</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


Szenario 2: Bob sendet eine E-Mail an John (An/Cc) und Jack (direkt über BCC oder indirekt über eine Verteilergruppe). Die folgende Tabelle zeigt eDiscovery-Suchergebnisse.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Bei der Suche...</th>
<th>Nach gesendeten Nachrichten...</th>
<th>Enthalten die Ergebnisse die Nachricht...</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Bobs Postfach</p></td>
<td><p>An/Cc:John</p></td>
<td><p>Ja</p></td>
<td><p>Gibt an, dass Jack auf Bcc stand</p></td>
</tr>
<tr class="even">
<td><p>Bobs Postfach</p></td>
<td><p>Bcc:Jack</p></td>
<td><p>Ja</p></td>
<td><p>Gibt an, dass Jack auf Bcc stand</p></td>
</tr>
<tr class="odd">
<td><p>Bobs Postfach</p></td>
<td><p>Bcc:Jack (über Verteilergruppe)</p></td>
<td><p>Ja</p></td>
<td><p>Liste der Mitglieder der Verteilergruppe auf Bcc, beim Senden der Nachricht erweitert, in der eDiscovery-Suchvorschau, im Export und in Protokollen sichtbar.</p></td>
</tr>
<tr class="even">
<td><p>Johns Postfach</p></td>
<td><p>An/Cc:John</p></td>
<td><p>Ja</p></td>
<td><p>Keine Hinweise auf Bcc-Empfänger.</p></td>
</tr>
<tr class="odd">
<td><p>Johns Postfach</p></td>
<td><p>Bcc:Jack (direkt oder über Verteilergruppe)</p></td>
<td><p>Nein</p></td>
<td><p>Bcc-Informationen werden nicht in der an die Empfänger gesendeten Nachricht gespeichert. Sie müssen das Postfach des Absenders durchsuchen.</p></td>
</tr>
<tr class="even">
<td><p>Jacks Postfach</p></td>
<td><p>An/Cc:John (direkt oder über Verteilergruppe)</p></td>
<td><p>Ja</p></td>
<td><p>An/Cc-Informationen sind in der an alle Empfänger gesendeten Nachricht enthalten.</p></td>
</tr>
<tr class="odd">
<td><p>Jacks Postfach</p></td>
<td><p>Bcc:Jack (direkt oder über Verteilergruppe)</p></td>
<td><p>Nein</p></td>
<td><p>Bcc-Informationen werden nicht in der an die Empfänger gesendeten Nachricht gespeichert. Sie müssen das Postfach des Absenders durchsuchen.</p></td>
</tr>
</tbody>
</table>


## Häufig gestellte Fragen

**F. Wann und wo werden die Bcc-Empfänger-Informationen gespeichert?**  
A. Informationen über einen Bcc-Empfänger werden standardmäßig in der ursprünglichen Nachricht im Postfach des Absenders gespeichert. Wenn der Bcc-Empfänger eine Verteilergruppe ist, wird die Mitgliedschaft in der Verteilergruppe nur erweitert, wenn das Postfach des Absenders archiviert oder einer Office 365-Aufbewahrungsrichtlinie zugewiesen wird.

**F. Wann und wo wird die Liste der Empfänger in erweiterten Verteilergruppen gespeichert?**  
A. Die Mitgliedschaft in einer Verteilergruppe wird zu dem Zeitpunkt erweitert, zu dem die Nachricht gesendet wird. Die Liste der Mitglieder erweiterter Verteilergruppen wird in der ursprünglichen Nachricht im Postfach des Absenders gespeichert. Für das Postfach des Absenders muss das Compliance-Archiv oder die Beweissicherung aktiviert oder eine Office 365-Aufbewahrungsrichtlinie zugewiesen worden sein.

**F. Können die unter An/Cc aufgeführten Empfänger sehen, welche Empfänger auf Bcc stehen?**  
A. Nein. Diese Informationen sind nicht in den Nachrichtenkopfzeilen enthalten und nicht für die Empfänger unter An/Cc sichtbar. Der Absender kann das Bcc-Feld in der ursprünglichen Nachricht sehen, die in seinem Postfach gespeichert wird. Compliance Officers können diese Informationen sehen, wenn Sie das Postfach des Absenders durchsuchen.

**F. Wie kann ich sicherstellen, dass Empfänger in erweiterten Verteilergruppen immer gespeichert werden?**  
A. Wenn Sie sicherstellen möchten, dass Mitglieder erweiterter Verteilergruppen immer mit einer Nachricht gespeichert werden, [Platzieren aller Postfächer im Archiv](place-all-mailboxes-on-hold-exchange-2013-help.md). Oder Sie erstellen eine organisationsweite Office 365-Aufbewahrungsrichtlinie.

**F. Welche Arten von Gruppen werden unterstützt?**  
A. Verteilergruppen, E-Mail-aktivierte Sicherheitsgruppen und dynamische Verteilergruppen werden unterstützt.

**F. Ist die Anzahl der Empfänger in Verteilergruppen, die erweitert und in der Nachricht gespeichert werden können, begrenzt?**  
A. Bis zu 10.000 Mitglieder einer Verteilergruppe werden gespeichert.

**F. Werden geschachtelte Verteilergruppen unterstützt?**  
A. Ja, 25 Ebenen von geschachtelten Verteilergruppen werden erweitert.

**F. Wo sind die Informationen über Bcc-Empfänger und Empfänger in erweiterten Verteilergruppen sichtbar?**  
A. Die Informationen über Bcc-Empfänger und Empfänger in erweiterten Verteilergruppen sind für Compliance Officers sichtbar, wenn sie eine eDiscovery-Suche durchführen. Bcc-Empfänger und Empfänger in erweiterten Verteilergruppen sind in den Suchergebnissen, die in ein Discoverypostfach kopiert oder in eine PST-Datei exportiert werden, sowie im eDiscovery-Protokoll enthalten, das Teil der Suchergebnisse ist. Die Informationen über Bcc-Empfänger sind auch in der Suchvorschau verfügbar.

**F. Was passiert, wenn ein Mitglied einer Verteilergruppe aus der globalen Adressliste (GAL) Ihrer Organisation ausgeblendet ist?**  
A. Dies hat keine Auswirkungen. Wenn Empfänger aus der globalen Adressliste ausgeblendet sind, sind sie weiterhin in der Liste der Empfänger für die erweiterte Verteilergruppe enthalten.

