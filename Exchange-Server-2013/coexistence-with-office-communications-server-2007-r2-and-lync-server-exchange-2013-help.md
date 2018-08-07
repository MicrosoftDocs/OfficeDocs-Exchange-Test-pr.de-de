---
title: 'Koexistenz mit Office Communications Server 2007 R2 und Lync Server'
TOCTitle: Koexistenz mit Office Communications Server 2007 R2 und Lync Server
ms:assetid: f12d65c7-0b2c-46a1-a14a-802a76296fa1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ851069(v=EXCHG.150)
ms:contentKeyID: 50554932
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Koexistenz mit Office Communications Server 2007 R2 und Lync Server

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Communications Server 2007 R2 und Lync Server bieten Benutzern zahlreichen Funktionen wie Chat (auch mit mehreren Teilnehmern), Anwesenheitsinformationen und Voicemailfunktionalität, die mit Exchange Unified Messaging (UM) integriert werden können. Bei Bereitstellungen mit integriertem Lync Server 2010 oder 2013 können Benutzer, die für Enterprise-VoIP aktiviert sind, über Lync Server-Komponenten auf ihre Voicemail zugreifen.

Wenn Sie UM mit früheren Versionen von Office Communications Server oder Lync Server integrieren, stehen nicht alle Funktionen zur Verfügung. Damit Benutzer in den Genuss der neuen weiterentwickelten Funktionen wie hochauflösende Fotos, einheitlicher Kontaktspeicher und Integration mit der Lync-Archivierung kommen können, benötigen sie Benutzerkonten für Lync Server 2013 und Exchange Server 2013 sowie die neueste Version der Lync 2013-Clientsoftware. Der einheitliche Kontaktspeicher steht beispielsweise Benutzern nicht zur Verfügung, die in Lync Server 2010 für Enterprise-VoIP aktiviert sind. Außerdem können hochauflösende Fotos nicht in Lync 2010 angezeigt werden.

Wenn Sie Exchange UM mit Office Communications Server 2007 R2 oder Lync Server 2010 integrieren, müssen Sie ggf. weitere Hotfixes, Rollup- und kumulative Updates sowie Service Packs auf den Servern mit Office Communications Server 2007 R2 oder Lync 2010 installieren, die in Ihrer Organisation bereitgestellt sind. Die zu installierenden Komponenten hängen von Ihrer Bereitstellungstopologie und den Produktversionen ab, die mit Exchange UM integriert werden.

## Hotfixes, Rollup- und kumulative Updates sowie Service Packs

Die folgende Tabelle enthält die Korrekturen, die für jede Version der Produkte für eine Integration mit UM erforderlich sind.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>Office Communications Server 2007 R2, kumulatives Update 10 oder höher.</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010</p></td>
<td><p>Lync Server 2010, kumulatives Update 3 oder höher.</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013</p></td>
<td><p>Keine Updates erforderlich.</p></td>
</tr>
</tbody>
</table>

