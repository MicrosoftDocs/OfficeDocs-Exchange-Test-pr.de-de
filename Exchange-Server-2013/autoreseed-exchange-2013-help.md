---
title: 'AutoReseed: Exchange 2013 Help'
TOCTitle: AutoReseed
ms:assetid: 61f9a8be-070e-4c62-b505-52644fcff0c5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn789209(v=EXCHG.150)
ms:contentKeyID: 62523866
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# AutoReseed

 

_**Gilt für:** Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Das automatische erneute Seeding, auch AutoReseed genannt, ist ein Feature zur Ersetzung der Aufgaben, die – als Reaktion auf einen Datenträgerfehler, eine Datenbankbeschädigung oder andere Probleme, die ein erneutes Seeding einer Datenbankkopie erforderlich machen – normalerweise von einem Administrator ausgeführt werden. Die AutoReseed-Funktion ist für die automatische Wiederherstellung der Datenbankredundanz nach einem Datenträgerfehler konzipiert. Hierbei wird auf Ersatzdatenträger zurückgegriffen, die im System bereitgestellt wurden.

## Überblick über AutoReseed

In einer AutoReseed-Konfiguration (mit automatischem erneuten Seeding) wird eine standardisierte Speicherstruktur verwendet, und der Administrator bestimmt den Startpunkt. Die AutoReseed-Funktion sorgt nach dem Ausfall eines Datenträgers für eine schnellstmögliche Wiederherstellung der Redundanz. Hierbei werden Sätze aus Volumes (Ersatzvolumes eingeschlossen) und Datenbanken mithilfe von Bereitstellungspunkten vorab zugeordnet. Bei Auftreten eines Datenträgerfehlers, durch den der Datenträger nicht länger für das Betriebssystem zur Verfügung steht oder nicht mehr beschreibbar ist, wird ein Ersatzvolume durch das System zugewiesen, und für die betroffenen Datenbanken wird automatisch ein erneutes Seeding durchgeführt.

1.  Der Microsoft Exchange-Replikationsdienst prüft regelmäßig auf Kopien mit dem Status "FailedAndSuspended". Wenn sich alle in einem Volume für AutoReseed konfigurierten Datenbankkopien 15 Minuten lang im Status "FailedAndSuspended" befinden, wird der AutoReseed-Workflow initiiert.

2.  AutoReseed versucht dreimal, die fehlgeschlagenen und angehaltenen Kopien wiederaufzunehmen – mit einer Pause von jeweils 5 Minuten zwischen zwei Versuchen. Manchmal bleibt eine Datenbankkopie, die nach dem Status FailedandSuspended wiederaufgenommen wurde, im Status "Fehlgeschlagen". Dies kann aus einer Vielzahl von Gründen geschehen. Deshalb hat dieser Schritt den Zweck, mit diesen Fällen umzugehen. AutoReseed hält eine Datenbankkopie, die 10 Minuten lang den Status "Fehlgeschlagen" hat, an, um den Workflow am Laufen zu halten. Wenn die Anhalte- und Wiederaufnahmeaktion nicht zu einer fehlerfreien Datenbankkopie führt, wird der Workflow fortgesetzt.

3.  Wenn eine Kopie mit diesem Status gefunden wird, werden einige Vorbedingungsprüfungen ausgeführt. Es wird z. B. geprüft, ob ein Ersatzdatenträger vorhanden ist, ob die Datenbank und ihre Protokolldateien auf demselben Volume konfiguriert sind und ob sie sich an den entsprechenden Speicherorten befinden, die die erforderlichen Namenskonventionen erfüllen.

4.  Wenn die erforderlichen Prüfungen erfolgreich waren, weist die Funktion für Speicherplatzfreigabe im Microsoft Exchange-Replikationsdienst einen Ersatzdatenträger zu, ordnet diesen neu zu und formatiert ihn entsprechend den Zeitvorgaben in der Tabelle unten. AutoReseed versucht bis zu fünf Mal, ein Ersatzvolume zuzuordnen, mit einer jeweils einstündigen Pause zwischen den einzelnen Versuchen.

5.  Wenn ein Ersatzvolume zugewiesen wurde, führt AutoReseed eine InPlaceSeed-Operation mithilfe der Seeding-Option durch. Für alle Datenbanken, die sich auf dem betroffenen Datenträger befanden, wird mithilfe der aktiven Kopie der Datenbank als Seeding-Quelle ein erneutes Seeding ausgeführt.

6.  Nach Abschluss des Seeding-Vorgangs überprüft der Microsoft Exchange-Replikationsdienst, ob die neu eingespielte Kopie sich in einem fehlerfreien Zustand befindet.

Sobald alle Versuche ausgeschöpft sind, wird der Workflow beendet. Wenn sich die Datenbankkopie nach 3 Tagen immer noch im Status FailedandSuspended befindet, wird der Workflow-Status zurückgesetzt und erneut mit Schritt 1 begonnen. Dieses Rücksetz- und Wiederaufnahme-Verhalten ist hilfreich (und beabsichtigt), da es ein paar Tage dauern kann, einen fehlerhaften Datenträger, Controller usw. zu ersetzen.

Wenn es sich bei dem Fehler um einen Datenträgerausfall handelt, ist an diesem Punkt das manuelle Eingreifen eines Bedieners oder Administrators erforderlich, um den ausgefallenen Datenträger zu entfernen und zu ersetzen und den Ersatzdatenträger neu als Ersatzdatenträger zu konfigurieren.

Die AutoReseed-Konfiguration wird über drei Eigenschaften der DAG konfiguriert. Zwei der Eigenschaften beziehen sich auf die zwei in Verwendung befindlichen Bereitstellungspunkte. Exchange 2013 nutzt die Tatsache, dass Windows Server mehrere Bereitstellungspunkte pro Volume unterstützt. Die Eigenschaft *AutoDagVolumesRootFolderPath* bezieht sich auf den Bereitstellungspunkt, der alle verfügbaren Volumes enthält. Hierzu zählen Volumes, die Datenbanken hosten, sowie Ersatzvolumes. Die Eigenschaft *AutoDagDatabasesRootFolderPath* bezieht sich auf den Bereitstellungspunkt, der die Datenbanken umfasst. Eine dritte DAG-Eigenschaft, *AutoDagDatabaseCopiesPerVolume*, wird zum Konfigurieren der Anzahl von Datenbankkopien pro Volume verwendet.

Die nachstehende Abbildung zeigt eine AutoReseed-Beispielkonfiguration.

**Beispielkonfiguration für AutoReseed**

![Beispielkonfiguration für automatisches erneutes Seeding](images/Dn789209.e3af7306-f5b4-4ec4-9ccf-222ec452699b(EXCHG.150).gif "Beispielkonfiguration für automatisches erneutes Seeding")

In diesem Beispiel sind drei Volumes vorhanden, von denen zwei Datenbanken (VOL1 und VOL2) enthalten und es sich bei dem dritten um ein leeres, formatiertes Ersatzvolume (VOL3) handelt.

So konfigurieren Sie die AutoReseed-Funktion:

1.  Alle drei Volumes werden über einen einzelnen Bereitstellungspunkt bereitgestellt. In diesem Beispiel wird der Bereitstellungspunkt "C:\\ExchVols" verwendet. Dieser steht für das Verzeichnis zum Speicherabruf für Exchange-Datenbanken.

2.  Das Stammverzeichnis der Postfachdatenbanken wird als ein weiterer Bereitstellungspunkt konfiguriert. In diesem Beispiel wird der Bereitstellungspunkt "C:\\ExchDBs" verwendet. Im nächsten Schritt wird eine Verzeichnisstruktur erstellt, die ein übergeordnetes Verzeichnis für jede Datenbank aufweist. Zu jedem übergeordneten Verzeichnis werden zwei Unterverzeichnisse erstellt: ein Verzeichnis für die Datenbankdatei und ein Verzeichnis für die Protokolldateien.

3.  Die Datenbanken werden erstellt. Das obige Beispiel zeigt ein einfaches Design mit einer einzelnen Datenbank pro Volume. Auf "VOL1" gibt es somit drei Verzeichnisse: ein übergeordnetes Verzeichnis und zwei Unterverzeichnisse (ein Verzeichnis für die MDB1-Datenbankdatei und ein Verzeichnis für die zugehörigen Protokolle). Obwohl nicht in der Abbildung dargestellt, würde auch "VOL2" drei Verzeichnisse enthalten: das übergeordnete Verzeichnis und darunter das Verzeichnis für die MDB2-Datenbankdatei sowie das Verzeichnis für die zugehörigen Protokolldateien.

In dieser Konfiguration wird bei Ausfall von MDB1 oder MDB2 für eine Kopie der ausgefallenen Datenbank automatisch ein erneutes Seeding auf "VOL3" ausgeführt.

## Disk Reclaimer

Die AutoReseed-Komponente, die Ersatzdatenträger zuweist und formatiert, wird als *Disk Reclaimer* bezeichnet. Die Disk Reclaimer-Komponente formatiert Ersatzdatenträger automatisch in Vorbereitung für automatisches erneutes Seeding in unterschiedlichen Intervallen, je nach Zustand der Festplatte. Damit die Disk Reclaimer-Funktion einen Datenträger formatiert, müssen bestimmten Bedingungen erfüllt sein:

  - Die Disk Reclaimer-Funktion muss aktiviert sein. Sie ist standardmäßig aktiviert, kann aber mit [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) deaktiviert werden.

  - Das Volume muss einen Bereitstellungspunkt im Stammvolumepfad haben (standardmäßig "C:\\ExchangeVolumes").

  - Das Volume darf keine Bereitstellungspunkte im Datenbankvolumepfad haben (standardmäßig "C:\\ExchangeDatabases").

  - Wenn das Volume Dateien enthält, darf 24 Stunden lang keine der Dateien verwendet werden.

Zusätzlich zu den obigen Bedingungen versucht die Disk Reclaimer-Funktion nur einmal am Tag, ein bestimmtes Volume zu formatieren. In der folgenden Tabelle ist das Formatierungsverhalten der Disk Reclaimer-Funktion beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Status des Datenträgers und der Datenbankkopien</th>
<th>Formatierungsintervall</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Datenträger ist unformatiert oder formatiert, aber leer, oder formatiert, aber enthält Dateien, die seit 24 Stunden nicht verwendet wurden, und am lokalen Active Directory-Standort sind fehlerfreie aktive Datenbankkopien vorhanden, die als eine Seeding-Quelle verwendet werden können.</p></td>
<td><p>1 Tag</p></td>
</tr>
<tr class="even">
<td><p>Datenträger ist unformatiert oder formatiert, aber leer, oder formatiert, aber enthält Dateien, die seit 24 Stunden nicht verwendet wurden, aber am lokalen Active Directory-Standort sind keine fehlerfreien aktiven Datenbankkopien vorhanden, die als eine Seeding-Quelle verwendet werden können.</p></td>
<td><p>2 Tage</p></td>
</tr>
<tr class="odd">
<td><p>Datenträger ist unformatiert oder formatiert, aber leer, oder formatiert, aber enthält Dateien, die seit 24 Stunden nicht verwendet wurden, und am lokalen Active Directory-Standort sind fehlerfreie aktive Datenbankkopien vorhanden, die als eine Seeding-Quelle verwendet werden können. Allerdings sind außerhalb der Datenbankdatei (EDB-Datei) und Protokolldateien unbekannte Dateien vorhanden.</p></td>
<td><p>2 Wochen</p></td>
</tr>
<tr class="even">
<td><p>Datenträger ist unformatiert oder formatiert, aber leer, oder formatiert, aber enthält Dateien, die seit 24 Stunden nicht verwendet wurden, und am lokalen Active Directory-Standort sind fehlerfreie aktive Datenbankkopien vorhanden, die als eine Seeding-Quelle verwendet werden können. Allerdings sind eine oder mehrere Datenbankdateien (EDB-Dateien) für Datenbanken vorhanden, die sich nicht in Active Directory befinden.</p></td>
<td><p>2 Wochen</p></td>
</tr>
</tbody>
</table>

