---
title: 'IIS-Protokolle und Log Parser Studio-Berichte: Exchange 2013 Help'
TOCTitle: IIS-Protokolle und Log Parser Studio-Berichte
ms:assetid: 01fa67d4-dc02-4c5f-93af-6da7b97d282f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn904092(v=EXCHG.150)
ms:contentKeyID: 63910990
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# IIS-Protokolle und Log Parser Studio-Berichte

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

## Analysieren von Log Parser Studio-Berichten

Log Parser Studio ist ein Dienstprogramm, mit dem Sie Berichte aus verschiedenen Arten von Protokolldateien durchsuchen und erstellen können, einschließlich Protokolldateien für die Internetinformationsdienste (IIS). Das Programm baut auf Log Parser 2.2 auf und verfügt über eine vollständige Benutzeroberfläche für die einfache Erstellung und Verwaltung von verwandten SQL-Abfragen.

[Laden Sie Log Parser Studio herunter](https://go.microsoft.com/fwlink/p/?linkid=524244), und sehen Sie sich dann den Blogbeitrag [Erste Schritte mit Log Parser Studio](https://go.microsoft.com/fwlink/p/?linkid=524243) an.

Denken Sie daran, dass in Exchange 2013 der gesamte Datenverkehr über IIS läuft. Das bedeutet, dass das Analysieren von IIS-Protokollen die beste Möglichkeit ist, einen vollständigen Überblick über die Anzahl der Verbindungen, die auf einem Server eingehen, über protokollspezifische Informationen zu den Verbindungen und über die Benutzer zu erhalten, die die Leistung am meisten beeinträchtigen. Mehr als zwanzig neue Berichte wurden für Log Parser Studio entwickelt, um Exchange 2013-Leistungsprobleme zu behandeln.

## Log Parser Studio-Berichterstellung für Exchange 2013-Leistungsprobleme

Um einen umfassenden Einblick in die Gesamtlast in Ihrer Exchange 2013-Umgebung zu erhalten, verwenden Sie die folgende Berichterstellung, und vergleichen Sie die Zahlen für jeden Server.

Eine ZIP-Datei mit den hier aufgeführten Log Parser Studio-Berichten und weitere Berichte im Zusammenhang mit der Problembehandlung können [hier heruntergeladen werden](https://go.microsoft.com/fwlink/p/?linkid=524245).

  - **IIS: Requests Per Hour**. Feed in IIS-Protokollen von der Standardwebsite (W3SVC1-Verzeichnis) oder der Back-End-Website (W3SVC2-Verzeichnis), aber nicht von beiden gleichzeitig.

  - **ACTIVESYNC\_WP: Clients by percent**. Berechnet alle ActiveSync-Anforderungen, aufgeschlüsselt nach Benutzer-Agent und Prozentsatz der einzelnen Clients in Bezug auf die Gesamtanzahl der Anforderungen.

  - **ACTIVESYNC\_WP: Requests per hour (CSV)**. Listet die ActiveSync-Anforderungen pro Stunde auf und sendet die Ergebnisse an eine CSV-Datei.

  - **ACTIVESYNC\_WP: Requests per user (CSV)**. Listet die ActiveSync-Anforderungen pro Benutzer auf und sendet die Ergebnisse an eine CSV-Datei.

  - **ACTIVESYNC\_WP: Requests per user (Top 10k)**. Listet die ActiveSync-Anforderungen pro Benutzer für die 10.000 häufigsten Benutzer auf.

  - **ACTIVESYNC\_WP: Top Talkers (CSV)**. Listet die häufigsten ActiveSync-Clients in absteigender Reihenfolge der Anforderungsanzahl auf und sendet das Ergebnis an eine CSV-Datei.

  - **EWS\_WP: Clients by percent**. Berechnet alle EWS-Anforderungen, aufgeschlüsselt nach Benutzer-Agent und Prozentsatz der einzelnen Clients in Bezug auf die Gesamtanzahl der Anforderungen.

  - **EWS\_WP: Requests per hour (CSV)**. Listet die Gesamtanzahl der EWS-Anforderungen pro Stunde auf.

  - **EWS\_WP: Requests per user (CSV)**. Listet die EWS-Anforderungen pro Benutzer auf und sendet die Ergebnisse an eine CSV-Datei.

  - **EWS\_WP: Requests per user (Top 10k)**. Listet die EWS-Anforderungen pro Benutzer für die 10.000 häufigsten Benutzer auf.

  - **EWS\_WP: Top Talkers (CSV)**. Listet die häufigsten EWS-Clients in absteigender Reihenfolge der Anforderungsanzahl auf.

  - **OLA\_WP: Errors, per user, per hour, per day**. Outlook Anywhere-Benutzer nach Anzahl der Anforderungen.

  - **OLA\_WP: Requests per hour**. Listet die Outlook Anywhere-Anforderungen pro Stunde auf.

  - **OLA\_WP: Requests per hour, per user**. Listet die Outlook Anywhere-Anforderungen pro Stunde und Benutzer auf.

  - **OLA\_WP: Requests per user (CSV)**. Listet die Outlook Anywhere-Anforderungen pro Benutzer auf.

  - **OLA\_WP: Requests per user (Top 10k)**. Listet die Outlook Anywhere-Anforderungen pro Benutzer für die 10.000 häufigsten Benutzer auf.

  - **OLA\_WP: Top Talkers**. Listet die häufigsten Outlook Anywhere-Clients in absteigender Reihenfolge der Anforderungsanzahl auf.

  - **OWA\_WP: Clients by percent**. Berechnet alle OWA-Anforderungen, aufgeschlüsselt nach Benutzer-Agent und Prozentsatz der einzelnen Clients in Bezug auf die Gesamtanzahl der Anforderungen.

  - **OWA\_WP: Requests per hour (CSV)**. Listet die OWA-Anforderungen pro Stunde auf und sendet die Ergebnisse an eine CSV-Datei.

  - **OWA\_WP: Requests per user (CSV)**. Listet die OWA-Anforderungen pro Benutzer auf und sendet die Ergebnisse an eine CSV-Datei.

  - **OWA\_WP: Requests per user (Top 10k)**. Listet die OWA-Anforderungen pro Benutzer für die 10.000 häufigsten Benutzer auf.

  - **OWA\_WP: Top Talkers (CSV)**. Listet die häufigsten OWA-Clients in absteigender Reihenfolge der Anforderungsanzahl auf und sendet das Ergebnis an eine CSV-Datei.

