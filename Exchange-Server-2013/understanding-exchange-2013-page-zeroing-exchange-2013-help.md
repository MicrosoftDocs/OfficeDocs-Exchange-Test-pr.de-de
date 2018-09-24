---
title: 'Grundlegendes z. unwiderr. Löschen in Exchange 2013: Exchange 2013-Hilfe'
TOCTitle: Grundlegendes zum unwiderruflichen Löschen in Exchange 2013
ms:assetid: 0ca7b188-efbc-4c0d-bcfe-5138cffc803c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg549096(v=EXCHG.150)
ms:contentKeyID: 61621798
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zum unwiderruflichen Löschen in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

## Unwiderrufliches Löschen in Exchange 2013

*Unwiderrufliches Löschen* ist ein Sicherheitsmechanismus, bei dem entweder Nullen oder ein binäres Muster über gelöschte Daten geschrieben werden, sodass ein Wiederherstellen der gelöschten Daten viel schwieriger wird. In Exchange Server 2013 werden für eine ESE-Datenbank *Seiten* als Speichereinheit verwendet, und infolgedessen wird *unwiderrufliches Löschen* implementiert. Unwiderrufliches Löschen ist standardmäßig aktiviert und kann nicht deaktiviert werden. Vorgänge zu unwiderruflichem Löschen werden im Transaktionsprotokoll festgehalten, sodass unwiderrufliches Löschen für alle Kopien einer Datenbank auf die gleiche Weise ausgeführt wird. Das unwiderrufliche Löschen einer Seite in einer aktiven Datenbank bewirkt daher, dass die Seite in einer passiven Kopie der Datenbank unwiderruflich gelöscht wird.


> [!NOTE]
> Es gibt kein Verfahren für Extensible Storage Engine (ESE), die Wiederverwendung von unwiderruflich gelöschten Seiten gegenüber dem Zuordnen von neuem Speicher zu priorisieren. Für Tabellen, denen aufeinanderfolgende Speicherbereiche zugeordnet sind, werden fragmentierte oder unwiderruflich gelöschte Seiten absichtlich zugunsten von neuen oder freien aufeinanderfolgenden Seiten übersprungen. Mit diesem Ansatz werden Datenbank-IOPS verringert.



In Exchange 2013 werden durch das unwiderrufliche Löschen die Leistungsbeeinträchtigungen bei Servern verringert, wenn diese Funktionen zum unwiderruflichen Löschen ausführen. Dazu gehört Folgendes:

  - **Optimierte Speicher- und Netzwerkkapazität**   ESE schreibt einen unwiderruflich gelöschten Eintrag in die Transaktionsprotokolldatei, statt das gesamte Bild der Seite zu protokollieren. Dieser Ansatz bewirkt, dass weniger E/A-Protokollschreibvorgänge erforderlich sind und dass weniger Bandbreite für das Übertragen von Protokolldateien erforderlich ist.

  - **Optimierte Datenbankdatenträger-E/A**   In Exchange 2010 und früheren Versionen wird unwiderrufliches Löschen nur während einer Sicherung oder einer geplanten Wartung ausgeführt, und es bedingt erhebliche Datenbankdatenträger-E/A. In Exchange 2010 SP1 und höher (einschließlich Exchange 2013) wird unwiderrufliches Löschen standardmäßig vorgenommen und hauptsächlich zur Transaktionszeit ausgeführt. In den meisten Fällen wird unwiderrufliches Löschen unmittelbar nach dem endgültigen Löschen ausgeführt. Diese Vorgehensweise ermöglicht der Datenbank, die von ESE unterstützte Prüfpunkttiefe zu nutzen. Dadurch wird sichergestellt, dass modifizierte Seiten für einen bestimmte Zeit im Datenbankcache verbleiben, sodass weitere Seitenaktualisierungen, die zeitnah auftreten, keine zusätzlichen Datenbank-E/A-Schreibvorgänge verursachen. Aufgrund dieser Vorgehensweise hat unwiderrufliches Löschen keine wesentlichen Auswirkungen auf Datenbank-E/A. Dies ist der Grund, warum unwiderrufliches Löschen standardmäßig aktiviert ist.

## Implementierung von unwiderruflichem Löschen in der ESE-Datenbank

Unwiderrufliches Löschen bewirkt, dass ein endgültig gelöschter Datensatz mit einem binären Muster überschrieben wird. Das jeweilige Muster für unwiderrufliches Löschen gehört speziell zu einem ESE-Vorgang und ist bei Laufzeitvorgängen und Wartungsvorgängen unterschiedlich. In der folgenden Tabelle sind die Füllmuster zusammengestellt, die für die speziellen Laufzeitvorgänge verwendet werden.

### Füllmuster für unwiderrufliches Löschen während der ESE-Laufzeit

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ESE-Laufzeitvorgang</th>
<th>Füllmuster</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ersetzen</p></td>
<td><p>R</p></td>
</tr>
<tr class="even">
<td><p>Datensatz/Long-Wert löschen</p></td>
<td><p>D</p></td>
</tr>
<tr class="odd">
<td><p>Freigegebener Seitenspeicherplatz</p></td>
<td><p>H</p></td>
</tr>
</tbody>
</table>


In der folgenden Tabelle sind die Füllmuster zusammengestellt, die den speziellen Vorgängen entsprechen, die bei der Hintergrundwartung einer ESE-Datenbank ausgeführt werden.

### Füllmuster für unwiderrufliches Löschen während der Hintergrundwartung einer ESE-Datenbank

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hintergrundwartungsvorgang für ESE-Datenbank</th>
<th>Füllmuster</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Datensatz löschen</p></td>
<td><p>D</p></td>
</tr>
<tr class="even">
<td><p>Long-Wert löschen</p></td>
<td><p>L</p></td>
</tr>
<tr class="odd">
<td><p>Freigegebener Seitenspeicherplatz einer teilweise verwendeten Seite</p></td>
<td><p>Z</p></td>
</tr>
<tr class="even">
<td><p>Freigegebener Seitenspeicherplatz einer nicht verwendeten Seite</p></td>
<td><p>U</p></td>
</tr>
</tbody>
</table>


## Hintergrundwartung einer Datenbank

Die Hintergrundwartung einer Datenbank ist ein Vorgang, bei dem jede Datenbank ständig im Hintergrund überprüft und bezüglich Prüfsummen überwacht wird. Die Hauptfunktion der Wartung besteht darin, die Prüfsummen der Datenbankseiten zu überwachen. Sie führt jedoch auch die Bereinigung von Speicherplatz und das unwiderrufliche Löschen von Datensätzen und Seiten durch, die aufgrund eines Absturzes nicht unwiderruflich gelöscht wurden. Bei der Hintergrundwartung einer Datenbank werden ungefähr 1 MB pro Sekunde und Datenbank verarbeitet. Wenn rechtzeitiges unwiderrufliches Löschen Priorität haben soll, können Sie die Datenbank verkleinern, damit sichergestellt ist, dass unwiderrufliches Löschen für das Wiederherstellen nach einem Absturz in einer kürzeren Zeitspanne erfolgt (z. B. 24 Stunden).

Die Hintergrundwartung einer Datenbank ist ein kontinuierlicher Vorgang, weshalb weder dessen Start noch dessen Abschluss ein Ereignis zugeordnet ist. Sie können den Fortschritt der Hintergrundwartung einer Datenbank nachverfolgen, indem Sie den Wert eines Leistungsindikators ablesen:

  - MSExchange-Datenbank -\> Instanzen -\> Datenbankwartung: Dauer seit letzter

Dieser Leistungsindikator gibt an, wie viele Sekunden vergangen sind, seit die letzte Wartung für die jeweilige Datenbank abgeschlossen wurde.

## Unwiderrufliches Löschen in einer ESE-Datenbank

In der folgenden Tabelle ist für verschiedene Datenbanklöschszenarien erläutert, wann Funktionen zum unwiderruflichen Löschen ausgeführt werden.

### ESE-Datenbankwartung im Hintergrund

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Datenbanklöschszenario</th>
<th>ESE-Vorgang und -Zeitrahmen für unwiderrufliches Löschen von Datenbankdaten</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Szenario 1: Wiederherstellung einzelner Elemente ist deaktiviert, und der Benutzer löscht ein Element aus dem Ordner &quot;Wiederherstellbare Elemente&quot;.</p></li>
<li><p>Szenario 2: Wiederherstellung einzelner Elemente ist deaktiviert, und für &quot;Wiederherstellbare Elemente&quot; ist die Einstellung &quot;Aufbewahrungszeitraum&quot;auf 0 festgelegt.</p></li>
<li><p>Szenario 3: Wiederherstellung einzelner Elemente ist aktiviert, und das Element läuft entsprechend dem Aufbewahrungszeitraum für gelöschte Elemente ab.</p></li>
</ul></td>
<td><p>Ein asynchroner Thread schreibt ein binäres Muster über die gelöschten Daten. Diese Aktion wird innerhalb von Millisekunden nach dem Datensatzlöschvorgang ausgeführt. Wenn der Informationsspeicherprozess abstürzt, während das asynchrone unwiderrufliche Löschen noch nicht erledigt ist (oder das Bereinigen des Versionsspeichers wegen dessen Vergrößerung abgebrochen wurde), wird das unwiderrufliche Löschen ausgeführt, wenn die Hintergrundwartung der Datenbank diesen Abschnitt der Datenbank verarbeitet.</p></td>
</tr>
<tr class="even">
<td><p>Szenario für Ansicht: Ablauf von Elementen aus einer Outlook-/Outlook Web App-Ordneransicht (beispielsweise Unterhaltungsansicht)</p></td>
<td><p>Unwiderrufliches Löschen von Daten wird ausgeführt, wenn die Hintergrundwartung der Datenbank diesen Abschnitt der Datenbank verarbeitet.</p></td>
</tr>
<tr class="odd">
<td><p>Szenario für das Verschieben/Löschen eines Postfachs: Quellpostfach gelöscht (Ablauf des aus dem Dumpster gelöschten Postfachs)</p></td>
<td><p>Unwiderrufliches Löschen von Daten wird ausgeführt, wenn die Hintergrundwartung der Datenbank diesen Abschnitt der Datenbank verarbeitet.</p></td>
</tr>
</tbody>
</table>


## Überwachen des Verhaltens von unwiderruflichem Löschen

Sie können die Funktionalität von unwiderruflichem Löschen mit den folgenden beiden ESE-Leistungsindikatoren messen und überwachen:

  - MSExchange-Datenbank -\> Datenbankwartung: Unwiderruflich gelöschte Seiten: Gibt an, wie viele Seiten durch das Datenbankmodul unwiderruflich gelöscht wurden, seit der Leistungsindikator das letzte Mal aufgerufen wurde.

  - MSExchange-Datenbank -\> Datenbankwartung: Unwiderruflich gelöschte Seiten/Sek: Gibt die Rate an, mit der die Seiten unwiderruflich gelöscht werden.


> [!NOTE]
> Informationen zum Aktivieren dieser Leistungsindikatoren finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=101194">Aktivieren der erweiterten ESE-Leistungsindikatoren</A>.



Unwiderrufliches Löschen ist eine Datenbankwartungsfunktion. Daher enthalten diese Leistungsindikatoren Leistungsinformationen sowohl hinsichtlich des unwiderruflichen Löschens für Laufzeittransaktionen als auch hinsichtlich des unwiderruflichen Löschens wegen der Hintergrundwartung der Datenbank.

## Postfachdatentypen ohne unwiderrufliches Löschen

Für die folgenden Postfachdatentypen gibt es keine Regelungen für unwiderrufliches Löschen:

  - Transaktionsprotokolle einer Postfachdatenbank (LOG)
    
    Wenn Transaktionsprotokolle gelöscht werden (wegen Abschneidens durch Sicherung oder Umlaufprotokollierung), gibt es keinen Vorgang, mit dem die Blöcke im NTFS-Dateisystem, in dem die gelöschten Protokolldateien gesichert sind, unwiderruflich gelöscht werden können. Es ist sehr wahrscheinlich, dass NTFS den freien Speicherplatz schnell für neu erstellte Protokolle wiederverwendet, es gibt aber keine Garantie dafür.

  - Inhaltsindex-Katalogdateien
    
    Exchange 2013 verwendet Search Foundation für die Suchindizierungsfunktion. Der Suchindexkatalog besteht aus mehreren Dutzend Dateien, die auf demselben Volume gespeichert sind wie die Postfachdatenbankdatei. Wenn eine Nachricht endgültig aus der Postfachdatenbank gelöscht wird, wird der zugehörige Inhalt im Suchkatalog nicht sofort gelöscht. Das Löschen des Inhalts erfolgt, wenn Search Foundation eine Shadow- bzw. Hauptzusammenführung vieler kleiner Katalogdateien zu einer einzigen größeren Datei ausführt. Nach Abschluss der Hauptzusammenführung werden die kleineren Katalogdateien gelöscht. Es gibt keinen Vorgang zum unwiderruflichen Löschen der Blöcke, in denen die gelöschten Katalogdateien gespeichert waren.

