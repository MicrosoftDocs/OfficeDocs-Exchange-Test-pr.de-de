---
title: 'Sichern und Wiederherstellen von Exchange-Daten mit Windows Server-Sicherung'
TOCTitle: Sichern und Wiederherstellen von Exchange-Daten mithilfe der Windows Server-Sicherung
ms:assetid: 0fac891a-5713-42b6-afd5-c91b2b88f966
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876851(v=EXCHG.150)
ms:contentKeyID: 50475089
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Sichern und Wiederherstellen von Exchange-Daten mithilfe der Windows Server-Sicherung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsofts [bevorzugte Architektur](https://blogs.technet.com/b/exchange/archive/2014/04/21/the-preferred-architecture.aspx) für Exchange Server 2013 nutzt Konzept der Exchange Native Data Protection. Exchange Native Data Protection nutzt die systemeigene Exchange Features zum Schutz Ihrer Postfachdaten, ohne die Verwendung von herkömmlichen Sicherungen. Aber wenn Sie Sicherungen erstellen möchten, umfasst Exchange Plug-In für Windows Server Sicherung (WSB), die Sie Exchange-fähige Volume Shadow Copy Service, VSS-basierten Sicherungen von Exchange Daten erstellen können. Damit Exchange-fähige Sicherungen werden können, müssen Sie das WSB-Feature installiert haben.

Das Plug-In, WSBExchange.exe, wird als Dienst namens Microsoft Exchange Server-Erweiterung für Windows Server-Sicherung (der Kurzname für diesen Dienst lautet WSBExchange) ausgeführt. Dieser Dienst wird automatisch auf allen Postfachservern installiert und für den manuellen Start konfiguriert. Mit dem Plug-In kann WSB die Exchange-bezogene VSS-Sicherungen erstellen.

Bevor Sie mit WSB Exchange-Daten sichern, sollten Sie sich mit den folgenden Funktionen und Optionen des Plug-Ins vertraut machen:

  - Sicherungen mit WSB erfolgen auf Volumeebene, und die einzige Möglichkeit zur Durchführung einer Sicherung oder Wiederherstellung auf Anwendungsebene ist, ein gesamtes Volume auszuwählen. Zum Sichern einer Datenbank und deren Protokolldatenstrom müssen Sie das komplette Volume mit der Datenbank und den Protokollen sichern, nicht nur die einzelnen Ordner. Es ist nicht möglich, Daten zu sichern, ohne auch das vollständige Volume mit den Daten zu sichern.

  - Die Sicherung muss lokal auf dem Server ausgeführt werden, der gesichert wird. Sie können das Plug-In nicht für VSS-Remotesicherungen verwenden. Eine Remoteverwaltung von WSB oder des Plug-Ins ist nicht möglich. Sie können jedoch über Remotedesktopdienste oder Terminaldienste Sicherungen remote verwalten.

  - Die Sicherung kann auf einem lokalen Laufwerk oder einer Remotenetzwerkfreigabe erstellt werden.

  - Es sollten nur vollständige Sicherungen vorgenommen werden. Nach erfolgreichem Abschluss einer vollständigen VSS-Sicherung von Volumes oder Ordnern mit einer Exchange-Datenbank wird das Protokoll abgeschnitten.

  - Wenn Sie Daten wiederherstellen, ist es möglich, nur Exchange-Daten wiederherzustellen. Diese Daten können am ursprünglichen oder einem anderen Speicherort wiederhergestellt werden. Wenn Sie die Daten am ursprünglichen Speicherort wiederherstellen, erfolgt die Wiederherstellung durch WSB und das Plug-In automatisch. Dazu gehört auch das Aufheben der Einbindung vorhandener Datenbanken und die Wiedergabe von Protokollen in die wiederhergestellte Datenbank.

  - Der Wiederherstellungsvorgang unterstützt die Exchange-Wiederherstellungsdatenbank (Recovery Database, RDB) nicht. Wenn Sie die RDB verwenden möchten, müssen Sie die Daten an einem anderen Speicherort wiederherstellen und die wiederhergestellten Daten dann manuell von diesem Speicherort in die RDB-Ordnerstruktur verschieben.

  - Wenn Sie Exchange-Daten wiederherstellen, müssen alle gesicherten Datenbanken zusammen wiederhergestellt werden. Sie können nicht eine einzelne Datenbank wiederherstellen.

  - Bare-Metal-Wiederherstellungen werden bei Verwendung von WSB unterstützt. Bei Exchange-Servern wird jedoch empfohlen, den Exchange-Server und dann die Daten wiederherzustellen. Wenn Sie eine Sicherungsanwendung eines Drittanbieters (d. h. keine Microsoft-Anwendung) verwenden, werden Bare-Metal-Wiederherstellungen von Exchange möglicherweise vom Anbieter Ihrer Backupanwendung unterstützt.

In der folgenden Tabelle wird die für Exchange 2013 mit WSB verfügbare Unterstützung von Sicherungs- und Wiederherstellungsoptionen beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wenn Sie...</th>
<th>Dann gilt Folgendes...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Den kompletten Server sichern...</p></td>
<td><p>Es wird eine VSS-Kopiesicherung durchgeführt, und die Transaktionsprotokolle für die Datenbanken auf dem Server werden nicht abgeschnitten.</p></td>
</tr>
<tr class="even">
<td><p>Eine benutzerdefinierte Sicherung durchführen und ein oder mehrere Volumes zum Sichern auswählen…</p></td>
<td><p>Es kann eine vollständige VSS-Sicherung ausgewählt werden, sodass die Transaktionsprotokolle auf die Datenbanken auf den ausgewählten Volumes nach Abschluss einer erfolgreichen Sicherung abgeschnitten werden können.</p></td>
</tr>
<tr class="odd">
<td><p>Eine benutzerdefinierte Sicherung durchführen und einen oder mehrere Ordner zum Sichern auswählen…</p></td>
<td><p>Eine vollständige VSS-Sicherung kann ausgewählt werden, und die Protokolldateien werden abgeschnitten. Die Wiederherstellung der Sicherung ist allerdings auf Dateiwiederherstellung beschränkt, da die Wiederherstellung auf Anwendungsebene nicht als Option zur Verfügung steht.</p></td>
</tr>
</tbody>
</table>


Ausführliche Schritte zur Sicherung von Exchange mit WSB finden Sie unter [Sichern von Exchange mithilfe der Windows Server-Sicherung](use-windows-server-backup-to-back-up-exchange-exchange-2013-help.md).

Genaue Anweisungen zum Wiederherstellen von Daten aus einer mit WSB erstellten Sicherung finden Sie unter [Verwenden der Windows Server-Sicherung zum Wiederherstellen einer Sicherung von Exchange](use-windows-server-backup-to-restore-a-backup-of-exchange-exchange-2013-help.md).

