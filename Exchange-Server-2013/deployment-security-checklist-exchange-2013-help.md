---
title: 'Prüfliste für Bereitstellungssicherheit: Exchange 2013 Help'
TOCTitle: Prüfliste für Bereitstellungssicherheit
ms:assetid: 0cbfad59-f503-48a0-8184-6ca999d89e61
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996026(v=EXCHG.150)
ms:contentKeyID: 50475004
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Prüfliste für Bereitstellungssicherheit

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft Exchange Server 2013-Funktionen wurden entwickelt, um die Sicherheit der Messagingumgebung zu verbessern. Im Allgemeinen sind für Exchange 2013 die folgenden Bedingungen erfüllt:

  - Konten, die von Exchange 2013 verwendet werden, weisen die minimal für die Ausführung der erforderlichen Aufgabensätze erforderlichen Rechte auf.

  - Standardmäßig werden Dienste nur gestartet, wenn sie benötigt werden.

  - Die ACL-Rechte (Access Control List, Zugriffssteuerungsliste) für Exchange-Objekte sind minimiert.

  - Administratorrechte werden entsprechend dem Umfang der Änderungen am Objekt festgelegt, die für eine bestimmte Änderung erforderlich sind.

  - Alle internen, standardmäßigen Nachrichtenpfade sind standardmäßig verschlüsselt.

In diesem Thema werden einige empfehlenswerte Schritte aufgelistet, die Sie ausführen können, um die Nachrichtenumgebung vor dem Installieren von Microsoft Exchange besser zu schützen. Bei jeder Installation einer neuen Exchange-Serverrolle sollte diese Checkliste durchgegangen werden.

Führen Sie die folgenden Verfahren durch, bevor Sie Exchange 2013 installieren.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verfahren</th>
<th>Erledigt?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Führen Sie <a href="https://go.microsoft.com/fwlink/p/?linkid=54836">Microsoft Update</a> aus.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Führen Sie das Microsoft Windows Tool zum Entfernen bösartiger Software aus. Das Tool zum Entfernen bösartiger Software ist in Microsoft-Update enthalten. Weitere Informationen zum Tool finden Sie unter <a href="http://go.microsoft.com/fwlink/p/?linkid=73452">Tool zum Entfernen bösartiger Software</a>.</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Führen Sie den <a href="https://go.microsoft.com/fwlink/p/?linkid=16526">Microsoft Baseline Security Analyzer</a> aus.</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

