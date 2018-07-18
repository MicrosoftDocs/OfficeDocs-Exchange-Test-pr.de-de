---
title: 'Switchover und Failover: Exchange 2013 Help'
TOCTitle: Switchover und Failover
ms:assetid: 75388645-cae1-402e-bf02-c4949d3e2c31
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298067(v=EXCHG.150)
ms:contentKeyID: 62523868
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Switchover und Failover

 

_**Gilt für:** Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2015-12-02_

Switchover und Failover sind die beiden Arten von Ausfällen in Microsoft Exchange Server 2013:

  - Ein *Switchover* ist ein geplanter Ausfall einer Datenbank oder eines Servers, der explizit von einem Cmdlet oder dem verwalteten Verfügbarkeitssystem in Exchange 2013 initiiert wird. Switchover erfolgen im Allgemeinen im Rahmen der Vorbereitung auf die Durchführung eines Wartungsvorgangs. Für einen Switchover muss die aktive Kopie der Postfachdatenbank auf einen anderen Server in der Database Availability Group (DAG) verschoben werden. Wenn während eines Switchovers kein fehlerfreies Ziel gefunden wird, erhalten Administratoren eine Fehlermeldung, und die Postfachdatenbank wird weiterhin bereitgestellt oder eingebunden.

  - Als *Failover* werden unerwartete Ereignisse bezeichnet, aufgrund derer Dienste, Daten oder beides nicht zur Verfügung stehen. Bei einem Failover erfolgt eine automatische Wiederherstellung des Systems nach dem Ausfall, indem eine passive Kopie der Postfachdatenbank zur aktiven Kopie gemacht wird. Wenn während eines Failovers kein fehlerfreies Ziel gefunden wird, wird die Bereitstellung der Postfachdatenbank aufgehoben.

Exchange 2013 wurde speziell für die Verarbeitung von Switchover- und Failoversituationen entwickelt.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit der hohen Verfügbarkeit und der Standortflexibilität gibt? Informationen hierzu finden Sie unter [Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte](managing-high-availability-and-site-resilience-exchange-2013-help.md).

## Switchover

Es gibt drei Arten von Switchovervorgängen in Exchange 2013:

  - Datenbankswitchover

  - Serverswitchover

  - Datencenterswitchover

## Datenbankswitchover

Ein *Datenbankswitchover* ist der Vorgang, bei dem für eine einzelne aktive Datenbank auf eine andere Datenbankkopie (eine passive Kopie) gewechselt wird, wobei diese andere Datenbankkopie zur neuen aktiven Datenbankkopie wird. Datenbankswitchover können sowohl innerhalb eines Datencenters als auch zwischen Datencentern auftreten. Ein Datenbankswitchover kann mithilfe des Exchange Admin Center (EAC) oder der Shell durchgeführt werden. Unabhängig davon, welche Schnittstelle verwendet wird, läuft der Switchovervorgang folgendermaßen ab:

1.  Der Administrator initiiert einen Datenbankswitchover, um die aktuell aktive Kopie der Postfachdatenbank auf einen anderen Server zu verschieben.

2.  Der für den Task verwendete Client sendet einen Remoteprozeduraufruf (RPC) an den Microsoft Exchange-Replikationsdienst auf einem DAG-Mitglied.

3.  Wenn das DAG-Mitglied nicht die Rolle "Primary Active Manager" innehat, übergibt das DAG-Mitglied den Task an den Server mit der PAM-Rolle.

4.  Der Task sendet einen Remoteprozeduraufruf an den Microsoft Exchange-Replikationsdienst auf dem Server mit der PAM-Rolle.

5.  Der PAM liest und aktualisiert die Informationen zu Datenbankpfaden, die in der Clusterdatenbank für die DAG gespeichert sind.

6.  Der PAM kontaktiert den Microsoft Exchange-Replikationsdienst auf dem DAG-Mitglied, dessen passive Kopie als neue aktive Kopie der Postfachdatenbank aktiviert wird.

7.  Der Microsoft Exchange-Replikationsdienst auf dem Zielserver fragt die Microsoft Exchange-Replikationsdienste auf allen anderen DAG-Mitgliedern ab, um die beste Protokollquelle für die Datenbankkopie zu bestimmen.

8.  Die Einbindung der Datenbank wird vom aktuellen Server entfernt, und der Microsoft Exchange-Replikationsdienst auf dem Zielserver kopiert die verbleibenden Protokolle auf den Zielserver.

9.  Der Microsoft Exchange-Replikationsdienst auf dem Zielserver fordert eine Datenbankeinbindung an.

10. Der Microsoft Exchange-Informationsspeicherdienst auf dem Zielserver gibt die Protokolldateien wieder und bindet die Datenbank ein.

11. Alle etwaigen Fehlercodes werden an den Microsoft Exchange-Replikationsdienst auf dem Zielserver zurückgegeben.

12. Der PAM aktualisiert die Statusinformationen für Datenbankkopien in der Clusterdatenbank für die DAG.

13. Alle etwaigen Fehlercodes werden vom Microsoft Exchange-Replikationsdienst auf dem Zielserver an den Microsoft Exchange-Replikationsdienst auf dem PAM zurückgegeben.

14. Der Microsoft Exchange-Replikationsdienst auf dem PAM gibt alle etwaigen Fehler an die Verwaltungsschnittstelle zurück, über die der Task aufgerufen wurde.

15. Die Remote-PowerShell gibt die Ergebnisse des Vorgangs an die aufrufende Verwaltungsschnittstelle zurück.

Genaue Anweisungen zum Durchführen eines Datenbankswitchovers finden Sie unter [Aktivieren einer Kopie einer Postfachdatenbank](activate-a-mailbox-database-copy-exchange-2013-help.md).

## Serverswitchover

Ein Serverswitchover ist der Vorgang, bei dem alle aktiven Datenbanken auf einem DAG-Mitglied auf mindestens einem anderen DAG-Mitglied aktiviert werden. Wie ein Datenbankswitchover kann ein Serverswitchover innerhalb eines Datencenters und zwischen Datencentern auftreten, und er kann mithilfe des EAC oder der Shell initiiert werden. Unabhängig davon, welche Schnittstelle verwendet wird, läuft der Serverswitchover-Vorgang folgendermaßen ab:

1.  Der Administrator initiiert einen Serverswitchover, um alle aktuell aktiven Kopien von Postfachdatenbanken auf mindestens einen anderen Server zu verschieben.

2.  Der Task führt für jede aktive Datenbank auf dem aktuellen Server die Schritte aus, die weiter oben in diesem Thema für Datenbankswitchover beschrieben wurden (Schritte 2 bis 4) .

3.  Der PAM liest und aktualisiert die Informationen zu Datenbankpfaden, die in der Clusterdatenbank für die DAG gespeichert sind.

4.  Der PAM kontaktiert den Microsoft Exchange-Replikationsdienst auf jedem DAG-Mitglied, auf dem eine passive Kopie aktiviert wird.

5.  Der Microsoft Exchange-Replikationsdienst auf den Zielservern fragt die Microsoft Exchange-Replikationsdienste auf allen anderen DAG-Mitgliedern ab, um die beste Protokollquelle für die Datenbankkopie zu bestimmen.

6.  Die Einbindung der Datenbank wird vom aktuellen Server entfernt, und der Microsoft Exchange-Replikationsdienst auf jedem Zielserver kopiert die verbleibenden Protokolle auf den Zielserver.

7.  Der Microsoft Exchange-Replikationsdienst auf jedem Zielserver fordert eine Datenbankeinbindung an.

8.  Der Microsoft Exchange-Informationsspeicherdienst auf jedem Zielserver gibt die Protokolldateien wieder und bindet die Datenbank ein.

9.  Alle etwaigen Fehlercodes werden an den Microsoft Exchange-Replikationsdienst auf dem Zielserver zurückgegeben.

10. Der PAM aktualisiert die Statusinformationen für Datenbankkopien in der Clusterdatenbank für die DAG.

11. Alle etwaigen Fehlercodes werden vom Microsoft Exchange-Replikationsdienst auf dem Zielserver an den Microsoft Exchange-Replikationsdienst auf dem PAM zurückgegeben.

12. Der Microsoft Exchange-Replikationsdienst auf dem PAM gibt alle etwaigen Fehler an die Verwaltungsschnittstelle zurück, über die der Task aufgerufen wurde.

13. Die Remote-PowerShell gibt die Ergebnisse des Vorgangs an die aufrufende Verwaltungsschnittstelle zurück.

Genaue Anweisungen zum Durchführen eines Serverswitchovers finden Sie unter [Ausführen eines Serverswitchovers](perform-a-server-switchover-exchange-2013-help.md).

## Datencenterswitchover

In einer Konfiguration mit Ausfallsicherheit für Standorte kann in einer DAG in Reaktion auf einen Ausfall auf Standortebene eine automatische Wiederherstellung erfolgen, sodass das Messaging-System weiterhin funktioniert. Für diese Konfiguration sind mindestens drei Standorte erforderlich, da dafür DAG-Mitglieder an zwei Standoirten und der Zeugenserver der DAG an einem dritten Standort bereitgestellt werden müssen.

Wenn Sie keine drei Standorte zur Verfügung haben, oder diese zur Verfügung haben, aber Wiederherstellungsaktionen auf Rechenzentrumsebene steuern möchten, können Sie eine DAG für den Fall eines Ausfalls auf Standortebene für manuelle Wiederherstellung konfigurieren. In diesem Fall würden Sie einen Prozess mit der Bezeichung *Datencenterswitchover* durchführen. Wie bei vielen Szenarien der Notfallwiederherstellung kann eine vorherige Planung und Vorbereitung eines Datencenterswitchovers den Wiederherstellungsvorgang vereinfachen und die Dauer des Ausfalls verringern.

Aufgrund der zahlreichen Architekturänderungen in Exchange 2013, einschließlich der Konsolidierung von Serverrollen, ist die Durchführung eines Datencenterswitchovers in Exchange 2013 um einiges einfacher als in Exchange 2010. Ausführliche Schritte zur Durchführung eines Datencenterswitchovers finden Sie unter [Datencenterswitchover](datacenter-switchovers-exchange-2013-help.md).

## Failover

Ein Failover ist ein automatischer Aktivierungsvorgang, der auf Datenbank-, Server- oder Datencenterebene auftreten kann. Failover treten als Reaktion auf einen Ausfall auf, der sich auf eine einzelne Datenbank (wie z. B. einen isolierten Speicherverlust), auf einen gesamten Server (wie z. B. einen Ausfall der Hauptplatine oder einen Stromausfall) oder auf einen gesamten Standort (wie z. B. den Verlust aller DAG-Mitglieder an einem Standort) auswirkt.

DAGs und Kopien von Postfachdatenbanken stellen vollständige Redundanz und schnelle Wiederherstellung der Daten und Dienste bereit, die den Zugriff auf die Daten bereitstellen. In der folgenden Tabelle werden die erwarteten Wiederherstellungsaktionen für verschiedene Ausfälle aufgeführt. Einige Ausfälle erfordern, dass der Administrator die Wiederherstellung startet. Andere Ausfälle werden automatisch vom System behandelt.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Automatische Aktivierung</th>
<th>Automatische Reparaturaktion</th>
<th>Zustand während der Reparatur: Aktiv</th>
<th>Zustand während der Reparatur: Passiv</th>
<th>Reparaturaktionen</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Soft-Datenbankausfall von Extensible Storage Engine (ESE): Die Laufwerke, auf denen die Datenbank gespeichert ist, geben bei einigen Lesevorgängen Fehler zurück (beispielsweise Fehler -1018).</p></td>
<td><p>Kurze Ausfallzeit möglich.</p>
<p>Automatischer Failover möglich.</p></td>
<td><p>Automatische Patchen einer defekten Seite.</p></td>
<td><p>Manueller Switchover, automatischer Failover oder Onlinereparatur.</p></td>
<td><p>Fehler</p></td>
<td><p>Neuerstellung des RAID-Systems, Reparatur von Datenbank und Datenbankkopien, Wiederherstellung und Patchen von Seiten oder Patchen von Seiten von einer Kopie.</p></td>
<td><p>Möglicherweise sind weitere Soft-Ausfallcodes für Datenbanken vorhanden.</p>
<p>Schließt keine Ausfälle von Blöcken des NTFS-Dateisystems ein.</p>
<p>Wenn ein Failover oder Switchover durchgeführt wird, wird der Hostserver aktualisiert.</p></td>
</tr>
<tr class="even">
<td><p>&quot;<em>Semi-Soft</em>&quot;-Datenbankausfall von ESE: Die Laufwerke, auf denen die Datenbank gespeichert ist, geben für einige Schreibvorgänge Fehler zurück.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Automatische Neuerstellung des Volumes bzw. Datenträgers nach einer möglichen Laufwerkersetzung.</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Eine RAID-Neuerstellung löst möglicherweise das Problem.</p>
<p>Kopieren und Reparieren, Ausführen der Wiederherstellung oder Neuerstellung von Volume/Datenträger nach möglicher Ersetzung.</p></td>
<td><p>Ein Semi-Soft-Schreibzugriffsfehler bei ESE bedeutet, dass einige Schreibvorgänge erfolgreich sind.</p>
<p>Schließt keine Ausfälle von Blöcken des NTFS-Dateisystems ein.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;Semi-Soft&quot;-Protokollausfall von ESE: Die Laufwerke, auf denen die Protokolldaten gespeichert sind, geben für einige Lese- oder Schreibvorgänge Fehler ohne entsprechende Wiederherstellung zurück.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Automatische Neuerstellung des Volumes bzw. Datenträgers nach einer möglichen Laufwerkersetzung.</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Eine RAID-Neuerstellung löst möglicherweise das Problem.</p>
<p>Kopieren und Reparieren, Ausführen der Wiederherstellung oder Neuerstellung von Volume/Datenträger nach möglicher Ersetzung.</p></td>
<td><p>Ein Semi-Soft-Lese-/Schreibzugriffsfehler bei ESE bedeutet, dass einige Lese-/Schreibvorgänge erfolgreich sind.</p>
<p>Wenn die Datenbank ausfällt, tritt die automatisierte Wiederherstellung auf, bevor die Verarbeitung der Protokolldatenwiederherstellung gestartet wird.</p></td>
</tr>
<tr class="even">
<td><p>ESE-Softwarefehler oder Ressourcenauslastung: Ein Fehler, bei dem ESE die Instanz terminiert (z. B. Ereignis-ID 1022, Prüfpunkttiefe zu groß).</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Behebung des zugrunde liegenden Ressourcenproblems.</p></td>
<td><p>Dieser Ausfall kann der sichtbare Fehler anderer Fälle sein.</p></td>
</tr>
<tr class="odd">
<td><p>Ausfälle von NTFS-Blöcken: Auf den Laufwerken, auf denen die Datenbank oder die Protokolle gespeichert sind, tritt ein Lese- oder Schreibfehler für eine NTFS-Kontrollstruktur auf.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Vollständige Neuerstellung des Volumes nach einer möglichen Laufwerkersetzung.</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Eine RAID-Neuerstellung löst möglicherweise das Problem. NTFS-Dienstprogramme lösen möglicherweise die NTFS-Probleme. Eine Exchange-Wiederherstellung kann erforderlich sein.</p></td>
<td><p>Dies ist wahrscheinlicher, wenn RAID nicht verwendet wird. Wenn dies Auswirkungen auf das aktive Protokollvolume hat, gehen einige aktuelle Protokolldateien verloren.</p>
<p>Schließt keine Fehler ein, die von NTFS oder dem zugrunde liegenden Software- oder Hardwarestack automatisch korrigiert werden.</p></td>
</tr>
<tr class="even">
<td><p>Ausfall des Datenbank- oder Protokolllaufwerks: Ein Laufwerk, auf dem Datenbank oder Protokolle gespeichert sind, ist vollständig ausgefallen, und es kann nicht darauf zugegriffen werden.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Das Laufwerk wird neu formatiert oder ersetzt, gefolgt von einer vollständigen Neuerstellung des Volumes.</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Laufwerkersetzung, gefolgt von möglicher RAID-Neuerstellung.</p>
<p>Laufwerkersetzung, gefolgt von vollständiger Neuerstellung des Volumes.</p>
<p>Vollständige Neuerstellung des Volumes.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Ausfall des Datenbank- oder Protokolldateivolumes: Das Volume fällt aufgrund von Volumeproblemen bei NTFS oder auf niedrigerer Ebene aus.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Laufwerk neu formatiert oder ersetzt.</p></td>
<td><p>Die Einbindung wird aufgehoben, wenn keine Wiederherstellung möglich ist.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Laufwerkersetzung, gefolgt von möglicher RAID-Neuerstellung.</p>
<p>Laufwerkersetzung, gefolgt von vollständiger Neuerstellung des Volumes.</p>
<p>Vollständige Neuerstellung des Volumes.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Nicht genügend Speicherplatz auf dem Datenbank- oder Protokollvolume: Das NTFS-Dateisystem mit den Datenbank- oder Protokolldateien hat nicht genügend Speicherplatz.</p></td>
<td><p>Automatischer Failover, wenn die andere Kopie keinen ähnlichen Status aufweist.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Vollständige oder inkrementelle Sicherungen ausführen, Protokolle manuell löschen, Zeit vergehen lassen, Datenbankkopie fortsetzen oder ausgefallene Datenbankkopie reparieren.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Administrator hebt die Einbindung der falschen Datenbank auf.</p></td>
<td><p>Wenn der Administrator den automatischen Failover nicht gesperrt hat, tritt ein kurzer Ausfall auf.</p>
<p>Wenn der automatische Failover verhindert wird, tritt bis zur Einbindung der Datenbank ein Ausfall auf.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Administrator korrigiert den Fehler.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Administrator hält die falsche Datenbankkopie an.</p></td>
<td><p>Je nach Konfiguration und betroffener Kopie ist möglicherweise keine automatische Wiederherstellung möglich.</p></td>
<td><p>Keine.</p></td>
<td><p>Nicht anwendbar.</p></td>
<td><p>Angehalten</p></td>
<td><p>Administrator korrigiert den Fehler.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Administrator hebt die Einbindung einer Datenbank für Speicherung, NTFS oder Volumewartung auf.</p></td>
<td><p>Wenn der Administrator den automatischen Failover nicht gesperrt hat, tritt ein kurzer Ausfall auf.</p>
<p>Wenn der automatische Failover gesperrt ist, tritt ein Ausfall auf, bis der Administrator die Aufgabe abschließt.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Administrator schließt die Aufgabe ab.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Administrator hält eine Datenbankkopie für Speicher-, NTFS oder Volumewartung an.</p></td>
<td><p>Je nach Konfiguration und betroffener Kopie ist möglicherweise keine automatische Wiederherstellung möglich.</p></td>
<td><p>Keine.</p></td>
<td><p>Nicht anwendbar.</p></td>
<td><p>Suspended</p></td>
<td><p>Administrator schließt die Aktionen ab.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Administrator hebt die Einbindung einer Datenbank für die Offline-Datenbankwartung auf.</p></td>
<td><p>Ausfall bis Abschluss der Reparatur.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Suspended</p></td>
<td><p>Administrator schließt die Aktionen ab.</p></td>
<td><p>Aktive und passive Datenbankkopien weichen voneinander ab.</p>
<p>Administrator muss Kopien anhalten.</p></td>
</tr>
<tr class="even">
<td><p>Ausfall des Storage Area Network (SAN), Datenträger oder Speichercontrollers.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebig</p></td>
<td><p>Hardware reparieren.</p></td>
<td><p>Eine passive Datenbankkopie weist den Status auf, der zum Zeitpunkt des Systemausfalls vorhanden war.</p></td>
</tr>
<tr class="odd">
<td><p>Serverhardwarewartung.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover (außer wenn vom Administrator blockiert).</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Aktionen abschließen.</p></td>
<td><p>Eine passive Datenbankkopie weist den Status auf, der zum Zeitpunkt des Herunterfahrens des Systems vorhanden war.</p></td>
</tr>
<tr class="even">
<td><p>Serversoftwarewartung.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover (außer wenn vom Administrator blockiert).</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Aktionen abschließen.</p></td>
<td><p>Eine passive Datenbankkopie weist den Status auf, der zum Zeitpunkt des Herunterfahrens des Systems vorhanden war.</p></td>
</tr>
<tr class="odd">
<td><p>Der Microsoft Exchange-Informationsspeicherdienst wurde durch einen Administrator beendet oder angehalten.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Starten Sie den Microsoft Exchange-Informationsspeicherdienst neu.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Informationsspeicherdienst schlägt fehl; Betriebssystem wird noch ausgeführt.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Dienststeuerungs-Manager startet den Microsoft Exchange-Informationsspeicherdienst neu.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Microsoft Exchange-Informationsspeicherdienst manuell oder automatisch neu starten.</p></td>
<td><p>Eine passive Datenbankkopie weist den Status auf, der zum Ausfallzeitpunkt des Microsoft Exchange-Informationsspeichers vorhanden war.</p></td>
</tr>
<tr class="odd">
<td><p>Teilweiser Ausfall des Microsoft Exchange-Informationsspeicherdiensts. Ein Teil des Exchange-Speichers arbeitet nicht mehr, aber er wird nicht als vollständig ausgefallen identifiziert.</p></td>
<td><p>Mögliche kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Eingebunden und teilweise funktionsfähig.</p></td>
<td><p>Beliebig, aber möglicherweise nur teilweise funktionsfähig</p></td>
<td><p>Starten Sie Server, Betriebssystem oder Microsoft Exchange-Informationsspeicherdienst neu.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Serverausfall: Der Server fällt aus einem der folgenden Gründe aus:</p>
<ul>
<li><p>Vollständiger Stromausfall</p></li>
<li><p>Ausfall des Prozessorchips, der Hauptplatine oder der Rückwandplatine ohne Wiederherstellung</p></li>
<li><p>Betriebssystem-Abbruchfehler</p></li>
<li><p>Das Betriebssystem reagiert nicht mehr.</p></li>
<li><p>Vollständiger Kommunikationsausfall</p></li>
</ul></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Computer neu starten.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Strom wieder bereitstellen, Betriebssystemeinstellungen ändern, Hardwareeinstellungen ändern, Hardware ersetzen, Betriebssystem neu starten, Betriebssystem warten, Hardware warten oder Kommunikationsprobleme beheben.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Quorumausfall bei DAG.</p></td>
<td><p>Ausfall bis Abschluss der Reparatur.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Fehlerhaftes Quorum reparieren, neues Quorum zuweisen oder das Netzwerk wiederherstellen, das den Quorumausfall verursacht.</p></td>
<td><p>Eine passive Datenbankkopie weist den Status auf, der zum Zeitpunkt des Systemausfalls vorhanden war.</p></td>
</tr>
<tr class="even">
<td><p>MAPI-Kommunikationsausfall im Netzwerk: Der Server ist nicht mehr im MAPI-Netzwerk verfügbar.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover; muss verlustfrei sein.</p></td>
<td><p>Keine. Kommunikation wird weiterhin versucht.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Beheben des Kommunikationsproblems durch Korrigieren von Hardware- oder Softwareproblemen.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Replikations-Kommunikationsausfall im Netzwerk: Der Server kann Takt, Protokollkopien oder Seed über das ausgefallene Replikationsnetzwerk nicht empfangen.</p></td>
<td><p>Möglicherweise kurzer Ausfall beim Kopieren oder Seeding, während die Arbeitsauslastung in ein anderes Netzwerk gewechselt wird.</p></td>
<td><p>Keine. Kommunikation wird weiterhin versucht.</p></td>
<td><p>Keine.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Beheben des Kommunikationsproblems durch Korrigieren von Hardware- oder Softwareproblemen.</p></td>
<td><p>Flexibilität durch Ausfall beeinträchtigt.</p></td>
</tr>
<tr class="even">
<td><p>Mehrfacher Netzwerk-Kommunikationsausfall: Der Server kann keine Takte, Protokollkopien oder Seeds über mehrere Netzwerke empfangen.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover; muss verlustfrei sein.</p></td>
<td><p>Keine. Kommunikation wird weiterhin versucht.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Beheben des Kommunikationsproblems durch Korrigieren von Hardware- oder Softwareproblemen.</p></td>
<td><p>Mindestens ein Netzwerk ist weiterhin funktionsfähig.</p></td>
</tr>
<tr class="odd">
<td><p>Partieller Ausfall mindestens eines Netzwerks: Hohe Fehlerraten bei Netzwerken.</p></td>
<td><p>Fehler nicht erkannt; keine Aktion.</p></td>
<td><p>Keine.</p></td>
<td><p>Eingebunden, aber mögliche Leistungsprobleme.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Beheben des Kommunikationsproblems durch Korrigieren von Hardware- oder Softwareproblemen.</p></td>
<td><p>Höhere Fehlerraten im Netzwerk als normal.</p></td>
</tr>
<tr class="even">
<td><p>Nicht erkanntes Hängen des Betriebssystems: Betriebssystem reagiert nicht mehr, aber dies wird nicht durch Überwachung oder Clustering erkannt.</p></td>
<td><p>Keine.</p></td>
<td><p>Keine.</p></td>
<td><p>Beliebig.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Nicht mehr reagierende Ressourcen neu starten oder beenden.</p></td>
<td><p>Hängen wird nicht erkannt; daher wird keine Aktion ausgeführt.</p>
<p>Einige Funktionen sind möglicherweise betriebsbereit.</p></td>
</tr>
<tr class="odd">
<td><p>Ausfall eines Betriebssystemlaufwerks.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Laufwerk ersetzen und Server neu erstellen oder Volume mit RAID neu erstellen.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Nicht genügend Speicherplatz auf dem Betriebssystemlaufwerk.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Manuell Speicherplatz auf dem Volume freigeben.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Volume- oder Laufwerkfehler bei Laufwerk mit Exchange-Binärdateien.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Laufwerk ersetzen und Anwendung neu installieren oder Volume mit RAID neu erstellen.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="even">
<td><p>Nicht genügend Speicherplatz auf Laufwerk mit Exchange-Binärdateien.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Beliebiger Wert</p></td>
<td><p>Manuell Speicherplatz auf dem Volume freigeben.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
<tr class="odd">
<td><p>Ungültiges neues Protokoll erkannt: Die Protokollsequenz wird durch eine vorhandene Datei unterbrochen.</p></td>
<td><p>Kurze Ausfallzeit während automatischem Failover, sofern das Problem nicht auch andere Kopien betrifft.</p></td>
<td><p>Keine.</p></td>
<td><p>Einbindung aufgehoben.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Störende Protokolle nach Ermittlung der Ursache entfernen.</p></td>
<td><p>Störende Protokolle sollten nicht repliziert werden.</p></td>
</tr>
<tr class="even">
<td><p>Fortlaufende Replikation erkennt ungültige Protokoll: Wiedergabe erkennt ungeeignetes Protokoll beim Kopieren oder Wiedergeben.</p></td>
<td><p>Nicht anwendbar.</p></td>
<td><p>Protokoll verwerfen.</p></td>
<td><p>Nicht anwendbar.</p></td>
<td><p>Fehlgeschlagen</p></td>
<td><p>Ungültiges Protokoll verwerfen; störenden Protokollstream verschieben.</p></td>
<td><p>Nicht anwendbar.</p></td>
</tr>
</tbody>
</table>


## Datenbankfailover

Ein Datenbankfailover tritt auf, wenn eine aktive Datenbankkopie nicht mehr aktiv bleiben kann. Die folgenden Aktionen treten bei einem Datenbankfailover auf:

1.  Der Datenbankausfall wird durch den Microsoft Exchange-Informationsspeicherdienst erkannt.

2.  Der Microsoft Exchange-Informationsspeicherdienst schreibt Ausfallereignisse in das Windows Vista-Ereignisprotokoll (Codename: Crimson).

3.  Der Active Manager auf dem Server, der die ausgefallene Datenbank enthält, erkennt die Ausfallereignisse.

4.  Der Active Manager fordert den Datenbankkopiestatus von den anderen Servern an, die eine Kopie der Datenbank enthalten.

5.  Die anderen Server geben den angeforderten Datenbankkopiestatus an den anfordernden Active Manager zurück.

6.  Der PAM initiiert eine Verschiebung der aktiven Datenbank auf einen anderen Server in der DAG mithilfe eines Algorithmus zum Auswählen der besten Kopie.

7.  Der PAM aktualisiert den Datenbankeinbindungspfad in der Clusterdatenbank so, dass er auf den ausgewählten Server verweist.

8.  Der PAM sendet eine Anforderung, Datenbankmaster zu werden, an den Active Manager auf dem ausgewählten Server.

9.  Der Active Manager auf dem ausgewählten Server fordert an, dass der Microsoft Exchange-Replikationsdienst die letzten Protokolle vom vorigen Server kopiert und die Datenbank als einbindbar kennzeichnet.

10. Der Microsoft Exchange-Replikationsdienst kopiert die Protokolle von dem Server, der zuvor über eine aktive Kopie der Datenbank verfügte.

11. Der Active Manager liest die maximale Protokollgenerierungsnummer aus der Clusterdatenbank.

12. Der Microsoft Exchange-Informationsspeicherdienst bindet die neue Kopie der aktiven Datenbank ein.

## Serverfailover

Ein Serverfailover tritt auf, wenn das DAG-Mitglied das MAPI-Netzwerk nicht mehr bedienen kann oder wenn der Clusterdienst auf einem DAG-Mitglied die übrigen DAG-Mitglieder nicht mehr kontaktieren kann. Folgendes tritt im Rahmen eines Serverfailovers auf:

1.  Der Clusterdienst auf dem PAM sendet eine Benachrichtigung über eine der beiden folgenden Bedingungen an den PAM:
    
    1.  **Knoten ausgefallen**   Der Server ist erreichbar, aber kann nicht an DAG-Vorgängen teilnehmen.
    
    2.  **MAPI-Netzwerk ausgefallen**   Der Server kann nicht über das MAPI-Netzwerk kontaktiert werden und kann daher nicht an DAG-Vorgängen teilnehmen.

2.  Wenn der Server erreichbar ist, kontaktiert der PAM den Active Manager auf dem betroffenen Server und fordert die sofortige Aufhebung der Einbindung aller Datenbanken an.

3.  Für jede betroffene Datenbankkopie wird Folgendes ausgeführt:
    
    1.  Der PAM fordert den Status der Datenbankkopie von allen Servern in der DAG an.
    
    2.  Der PAM empfängt eine Antwort von allen erreichbaren und aktiven DAG-Elementen.
    
    3.  Der PAM bestimmt unter den antwortenden Servern die beste Protokollquelle, indem er von jedem die aktuelle Protokollgenerierungsnummer abfragt.
    
    4.  Jeder der Server antwortet mit der Protokollgenerierungsnummer.

4.  Der PAM ruft den aktuellen Suchindex-Katalogstatus aus der Clusterdatenbank ab.

5.  Basierend auf der Protokollgenerierungsnummer und dem Katalogstatus jeder Datenbankkopie wählt der PAM die besten Kopien für die Aktivierung aus.

6.  Der PAM aktualisiert den Einbindungspfad der Datenbank in der Clusterdatenbank.

7.  Der PAM initiiert den Datenbankfailover durch Kommunikation mit dem Active Manager auf mindestens einem anderen Server.

8.  Der Active Manager auf dem ausgewählten Server fordert an, dass der Microsoft Exchange-Replikationsdienst die letzten Protokolle vom vorigen Server kopiert und die Datenbank als einbindbar kennzeichnet.

9.  Wenn die Datenbank einbindbar ist, bindet der Active Manager auf den Servern die Datenbanken ein.

Weitere Informationen zum Auswahlvorgang der besten Kopie durch den Active Manager finden Sie unter [Active Manager](active-manager-exchange-2013-help.md).

## Datencenterfailover

In Exchange 2013 wurden wesentliche Änderungen vorgenommen, die auf die Herausforderungen bei einer Konfiguration für die Ausfallsicherheit von Exchange 2010-Standorten abzielen. Durch die Vereinfachung von Namespaces, die Konsolidierung von Serverrollen, die Trennung von Clientzugriffsserver- und DAG-Wiederherstellung (in Exchange 2013 muss der Namespace nicht mit der DAG verschoben werden) und die Änderungen rund um den Lastenausgleich bietet Exchange 2013 neue Optionen für die Ausfallsicherheit von Standorten. Dazu zählt die Möglichkeit, einen einzelnen globalen Namespace zu verwenden. Wenn Sie mehr als zwei Standorte haben, an denen Messaging-Dienstkomponenten bereitgestellt werden sollen, bietet Exchange 2013 zusätzlich die Möglichkeit, den Messaging-Dienst bei Fehlern, die in Exchange 2010 manuelles Eingreifen erforderten, für automatisches Failover zu konfigurieren.

Die Konfiguration der Ausfallsicherheit von Standorten wurde in Exchange 2013 vereinfacht. Exchange nutzt die integrierte Fehlertoleranz des Namespace über mehrere IP-Adressen, Lastenausgleich (und, sofern erforderlich, die Fähigkeit zur Inbetriebnahme und Außerbetriebnahme von Servern). Eine der wichtigsten Änderungen in Exchange 2013 ist, dass die Möglichkeit von Clients zum Zwischenspeichern mehrerer IP-Adressen genutzt wird, die von einem DNS-Server als Antwort auf eine Namensauflösungsanforderung zurückgegeben werden. Die Tatsache, dass der Client mehrere IP-Adressen zwischenspeichern kann (was fast alle HTTP-Clients können, und da fast alle Clientzugriffsprotokolle in Exchange 2013 HTTP-basiert sind (Outlook, Outlook Anywhere, EAS, EWS, OWA, EAC, RPS usw.), können alle unterstützten HTTP-Clients mehrere IP-Adressen verwenden), ermöglicht ein Failover auf Clientseite. Sie können DNS so konfigurieren, dass einem Client während der Namensauflösung mehrere IP-Adressen übergeben werden. Der Client fragt "mail.contoso.com" an und erhält beispielsweise zwei oder vier IP-Adressen. Viele der an den Client zurückgegebenen IP-Adressen können jedoch zuverlässig verwenden werden. Dies verbessert den Clientbetrieb, da der Client bei einem Ausfall einer der IP-Adressen weitere Adressen zur Verbindungsherstellung zur Verfügung stehen. Wenn beim Versuch einer Verbindungsherstellung durch den Client ein Fehler auftritt, wartet der Client für etwa 20 Sekunden und versucht es dann mit der nächsten Adresse in der Liste. Wenn Sie die Verbindung zu Ihrem primären CAS-Array verlieren und Sie eine zweite veröffentliche IP-Adresse für ein zweites CAS-Array haben, erfolgt die Wiederherstellung für die Clients automatisch (und in ca. 21 Sekunden).

Moderne HTTP-Clients (Betriebssysteme und Webbrowser, die höchstens zehn Jahre alt sind) arbeiten mit dieser Redundanz einfach automatisch. Der HTTP-Stack kann mehrere IP-Adressen für einen FQDN akzeptieren, und wenn die erste IP-Adresse dauerhaft ausfällt (d. h. eine Verbindung nicht möglich ist), wird die nächste IP-Adresse in der Liste verwendet. Bei einem temporären Fehler (Verbindungsverlust nach dem Einrichten einer Sitzung, beispielsweise aufgrund eines zeitweiligen Fehlers im Dienst, bei dem ein Gerät Pakete verliert und außer Betrieb genommen werden muss), muss der Benutzer möglicherweise den Browser aktualisieren.

Mit der richtigen Konfiguration kann ein Failover auf Clientebene stattfinden, und Clients werden automatisch an ein zweites Datencenter umgeleitet, das über funktionierende Clientzugriffsserver verfügt. Diese Clientzugriffsserver leiten die Kommunikation zurück an den Benutzerpostfachserver, der vom Ausfall nicht betroffen ist (da Sie kein Switchover durchgeführt haben). Statt daran zu arbeiten, den Dienst wiederherzustellen, stellt der Dienst sich selbst wieder her, und Sie können sich auf die Behebung des Hauptproblems kümmern (z. B. um den Austausch eines Lastenausgleichmoduls).

Da ein Failover des Namespace zwischen Datencentern möglich ist, wird zum Erreichen eines Datencenterfailovers lediglich ein Mechanismus für ein datencenterübergreifendes Failover der Postfachrolle benötigt. Für ein automatisches Failover der DAG benötigen Sie lediglich eine Lösung, bei der die DAG gleichmäßig auf zwei Datencenter aufgeteilt ist. Anschließend platzieren Sie den Zeugenserver an einem dritten Standort, sodass er von DAG-Mitgliedern beider Datencenter vermittelt werden kann – unabhängig vom Status des Netzwerks zwischen den Datencentern, die die DAG-Mitglieder enthalten. Wichtig ist, dass der dritte Standort von Netzwerkfehlern isoliert ist, die sich auf die Standorte mit den DAG-Mitgliedern auswirken.

Wenn Sie nur zwei Rechenzentren haben und automatisches Failover konfigurieren möchten, können Sie Microsoft Azure als dritten Standort nutzen. Sie müssen ein virtuelles Azure-Netzwerk erstellen und dieses über ein Multipunkt-VPN mit Ihren zwei Rechenzentren verbinden. Dann können Sie den Zeugenserver auf einen virtuellen Microsoft Azure-Computer platzieren. Weitere Informationen finden Sie unter [Verwenden einer Microsoft Azure-VM als DAG-Zeugenserver](using-a-microsoft-azure-vm-as-a-dag-witness-server-exchange-2013-help.md).

