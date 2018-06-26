---
title: 'Serverstatus und -leistung: Exchange 2013 Help'
TOCTitle: Serverstatus und -leistung
ms:assetid: 9d1fdec8-8273-4c71-88f1-b4edfd542c4f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150551(v=EXCHG.150)
ms:contentKeyID: 50476337
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Serverstatus und -leistung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Um eine hoch leistungsfähige Messaginginfrastruktur entwerfen und verwalten zu können, ist ein Verständnis der Bereiche Serverstatus und -leistung entscheidend. Microsoft Exchange Server 2013 bietet Verbesserungen in diesen beiden Bereichen.

Suchen Sie eine Liste aller Themen zu Serverstatus und -leistung? Weitere Informationen finden Sie unter Dokumentation zu Serverstatus und -leistung.

## Verwaltete Verfügbarkeit

In Exchange 2013 wurde das Konzept der *verwalteten Verfügbarkeit* eingeführt. Verwaltete Verfügbarkeit wird auf allen Servern mit Exchange 2013 geboten. Das Konzept umfasst die beiden Prozesse "Exchange-Integritätsdienst" (MSExchangeHMHost.exe) und "Exchange-Integritäts-Manager-Arbeitsprozess" (MSExchangeHMWorker.exe) sowie die folgenden asynchronen Komponenten:

  - **Testmodul**   Das *Testmodul* nimmt Messungen auf dem Server vor.

  - **Überwachungstestmodul**   Das *Überwachungstestmodul* speichert die Geschäftslogik dazu, was einen fehlerfreien Status ausmacht. Das Modul funktioniert wie ein Mustererkennungsmodul, das nach Mustern und Messwerten sucht, die von einem fehlerfreien Status abweichen. Es bestimmt anschließend, ob eine Komponente oder Funktion fehlerhaft ist.

  - **Respondermodul**   Wenn das *Respondermodul* über eine fehlerhafte Komponente informiert wird, ist dessen erste Aktion der Versuch, die Komponente wiederherzustellen. Die verwaltete Verfügbarkeit ermöglicht mehrstufige Wiederherstellungsaktionen. Der erste Versuch kann der Neustart des Anwendungspools sein, der zweite Versuch der Neustart des entsprechenden Diensts und der dritte Versuch der Neustart des Servers sein. Als letzter Versuch wird der Server ggf. offline geschaltet, um keinen weiteren Datenverkehr mehr zu akzeptieren. Wenn alle diese Aktionen keinen Erfolg haben, wird eine Warnung an das Helpdesk gesendet.

Weitere Informationen zur verwalteten Verfügbarkeit finden Sie unter [Verwaltete Verfügbarkeit](managed-availability-exchange-2013-help.md).

## Verwaltung von Arbeitsauslastungen

Exchange 2013 bietet die folgenden Komponenten zur Verwaltung von Arbeitsauslastungen:

  - *Verwaltung von Benutzerarbeitsauslastungen* ist der neue Name der Benutzereinschränkungsfunktionen von Exchange Server 2010. Sie können diese Einstellung an die Anforderungen Ihrer Umgebung anpassen.

  - Die *Verwaltung von Systemarbeitsauslastungen* ist neu in Exchange 2013 und wird verwendet, um den Status der wichtigsten Serverressourcen zu überwachen und bestimmte Arbeitsauslastungen von Exchange automatisch zu drosseln. Diese Einstellungen sollten nur unter Anleitung des Microsoft-Kundendiensts und -Supports angepasst werden.

Weitere Informationen finden Sie unter [Verwaltung von Exchange-Arbeitsauslastungen](exchange-workload-management-exchange-2013-help.md).

## Dokumentation zu Serverstatus und -leistung

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zu Serverstatus und -leistung in Exchange 2013 sowie zu deren Verwaltung finden.


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
<td><p><a href="exchange-workload-management-exchange-2013-help.md">Verwaltung von Exchange-Arbeitsauslastungen</a></p></td>
<td><p>Erfahren Sie, wie Sie Arbeitsauslastungen verwalten können, indem Sie festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden</p></td>
</tr>
<tr class="even">
<td><p><a href="managed-availability-exchange-2013-help.md">Verwaltete Verfügbarkeit</a></p></td>
<td><p>Erfahren Sie mehr über die in Exchange 2013 integrierten Ressourcenüberwachungs- und Wiederherstellungsaktionen.</p></td>
</tr>
</tbody>
</table>

