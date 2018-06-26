---
title: 'Rückstaufunktion: Exchange 2013 Help'
TOCTitle: Rückstaufunktion
ms:assetid: 03003544-e802-4988-9427-5fc4da64dcb8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201658(v=EXCHG.150)
ms:contentKeyID: 52062828
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Rückstaufunktion

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die Rückstaufunktion ist ein Feature des Microsoft Exchange-Transportdiensts zum Überwachen der Systemressourcen. Dieses Feature ist auf Microsoft Exchange 2013-Postfachservern und -Edge-Transport-Servern enthalten.

Exchange kann feststellen, wenn wichtige Ressourcen (beispielsweise verfügbarer Festplattenspeicher und Arbeitsspeicher) überlastet sind, und Maßnahmen einleiten, um die Nichtverfügbarkeit des Diensts zu verhindern. Der Rückstau verhindert die vollständige Überlastung von Systemressourcen, und der Exchange-Server versucht, die vorhandenen Nachrichten zu verarbeiten, bevor weitere Nachrichten angenommen werden. Wenn die Auslastung der Systemressource wieder auf einem normalen Niveau liegt, nimmt der Exchange-Server nach und nach den normalen Betrieb wieder auf und beginnt wieder mit der Annahme neuer Nachrichten.

Wenn in Exchange 2013 der Transportdienst auf einem Postfachserver oder einem Edge-Transport-Server unter starker Ressourcenbelastung steht, werden eingehende Verbindungen angenommen, eingehende Nachrichten über diese Verbindungen werden jedoch nur bei verminderter Geschwindigkeit akzeptiert oder zurückgewiesen. Wenn ein SMTP-Host versucht, eine Verbindung mit einem Exchange-Server herzustellen, dessen Ressourcen überlastet sind, wird die Verbindung erfolgreich hergestellt. Wenn der Host jedoch den Befehl **MAIL FROM** zum Übermitteln einer Nachricht ausgibt, verzögert der Transportdienst, je nach der überlasteten Ressource, die Bestätigung des Befehls **MAIL FROM** oder lehnt die Verbindung ab.

**Inhalt**

Überwachte Ressourcen

Vom Exchange-Transport unter Ressourcenüberlastung durchgeführte Maßnahmen

Rückstaukonfigurationsoptionen in der Datei "EdgeTransport.exe.config"

Rückstauprotokollierungsinformationen

## Überwachte Ressourcen

Die folgenden Systemressourcen werden als Teil der Rückstaufunktion überwacht:

  - Freier Speicherplatz auf der Festplatte, auf der die Nachrichtenwarteschlangendatenbank gespeichert ist.

  - Freier Speicherplatz auf der Festplatte, auf der die Transaktionsprotokolle der Nachrichtenwarteschlangendatenbank gespeichert sind.

  - Die Anzahl der nicht übergebenen Transaktionen der Nachrichtenwarteschlangendatenbank, die im Arbeitsspeicher vorhanden sind.

  - Der Arbeitsspeicher, der vom Prozess EdgeTransport.exe verwendet wird.

  - Der Arbeitsspeicher, der von allen anderen Prozessen verwendet wird.

  - Die Anzahl der Nachrichten in der Übermittlungswarteschlange.

Für jede überwachte Systemressource auf einem Postfachserver oder einem Edge-Transport-Server gelten die folgenden drei Ressourcenauslastungsstufen:

  - **Normal**   Die Ressource wird nicht übermäßig verwendet. Der Server nimmt neue Verbindungen und Nachrichten an.

  - **Mittel**   Die Ressource ist geringfügig überlastet. Die Rückstaufunktion wird in begrenztem Umfang auf den Server angewendet. E-Mail von Absendern in der autoritativen Domäne kann übermittelt werden. Je nach der spezifischen ausgelasteten Ressource verwendet der Server jedoch das Teergrubenverfahren, um die Serverantwort zu verzögern, oder weist eingehende **MAIL FROM**-Befehle von anderen Quellen zurück.

  - **Hoch**   Die Ressource ist hochgradig überlastet. Die Rückstaufunktion wird in vollem Umfang angewendet. Die gesamte Nachrichtenübermittlung wird eingestellt, und der Server weist alle neu eingehenden **MAIL FROM**-Befehle zurück.

In den folgenden Abschnitten wird erläutert, wie Exchange die Situation verarbeitet, wenn eine bestimmte Ressource überlastet ist.

## Freier Festplattenspeicher für die Nachrichtenwarteschlangendatenbank

Standardmäßig ist die Nachrichtenwarteschlangendatenbank unter %ExchangeInstallPath%TransportRoles\\data\\Queue gespeichert. Exchange überwacht die Ausnutzung des Festplattenspeichers für diesen Speicherort. Die hohe Stufe für die Auslastung der Festplatte wird mithilfe der folgenden Formel berechnet:

100 \* (*hard disk size* - *fixed constant*) / *hard drive size*

Der Wert für *fixed constant* beträgt 500 Megabyte (MB).

Das Ergebnis dieser Formel wird als ein Prozentsatz des gesamten verwendeten Speicherplatzes auf der Festplatte ausgedrückt. Die Ergebnisse der Formel werden immer auf die nächste ganze Zahl abgerundet. Standardmäßig liegt die Festplattenauslastung der mittleren Stufe 2 % unter der der hohen Stufe. Standardmäßig ist die normale Stufe der Auslastung der Festplatte 4 % geringer als die hohe Stufe.

Zurück zum Seitenanfang

## Freier Festplattenspeicher für die Transaktionsprotokolle der Nachrichtenwarteschlangendatenbank

Standardmäßig werden die Transaktionsprotokolle der Nachrichtenwarteschlangendatenbank unter %ExchangeInstallPath%TransportRoles\\data\\Queue gespeichert. Exchange überwacht die Ausnutzung des Festplattenspeichers für diesen Speicherort. Die Anwendungskonfigurationsdatei "%ExchangeInstallPath%Bin\\EdgeTransport.exe.config" enthält einen *DatabaseCheckPointDepthMax*-Schlüssel mit einem Standardwert von 384 MB. Dieser Schlüssel steuert die zulässige Gesamtgröße aller nicht übergebenen Transaktionsprotokolle, die auf dem Festplattenlaufwerk vorhanden sind. Dieser Schlüssel wird in der Formel verwendet, die die Auslastung des Festplattenlaufwerks berechnet.


> [!NOTE]
> Der Wert des Schlüssels <EM>DatabaseCheckPointDepthMax</EM> gilt für alle transportbezogenen ESE-Datenbanken (Extensible Storage Engine), die auf dem Postfachserver oder dem Edge-Transport-Server vorhanden sind. Dies schließt die Nachrichtenwarteschlangendatenbank und die IP-Filterdatenbank ein.



Standardmäßig wird die hohe Stufe der Festplattenauslastung mithilfe der folgenden Formel berechnet:

100 \* (*hard drive size* - Min(5 GB, 3\**DatabaseCheckPointDepthMax*)) / *hard drive size*

Die Ergebnisse der Formel werden immer auf die nächste ganze Zahl abgerundet. Standardmäßig liegt die Festplattenauslastung der mittleren Stufe 2 % unter der der hohen Stufe. Die normale Stufe der Auslastung der Festplatte ist 4 % geringer als die hohe Stufe.

Zurück zum Seitenanfang

## Anzahl der nicht übergebenen Transaktionen der Nachrichtenwarteschlangendatenbank im Arbeitsspeicher

Eine Liste der Änderungen, die an der Nachrichtenwarteschlangendatenbank vorgenommen werden, verbleibt im Speicher, bis diese Änderungen an ein Transaktionsprotokoll übergeben werden können. Anschließend wird die Liste an die Nachrichtenwarteschlangendatenbank selbst übergeben. Diese ausstehenden Transaktionen der Nachrichtenwarteschlangendatenbank, die im Arbeitsspeicher enthalten sind, werden als *Version-Buckets* bezeichnet. Die Anzahl der Version-Buckets kann aufgrund eines unerwartet hohen Aufkommens eingehender Nachrichten, aufgrund von Spamangriffen, Problemen mit der Integrität der Nachrichtenwarteschlangendatenbank oder der Leistung des Festplattenlaufwerks inakzeptabel hoch werden.

Wenn Exchange mit dem Empfang von Nachrichten beginnt, werden diese Nachrichten in Batches zusammengefasst und dann als Version-Buckets vorbereitet. Weist eine eingehende Nachricht eine große Anlage auf, kann sie in mehrere Batches unterteilt werden. Die verarbeiteten Batches werden als *Batchpunkte* bezeichnet. Die Anzahl der ausstehenden Batchpunkte kann die festgelegten Schwellenwerte überschreiten, insbesondere bei einem unerwartet hohen Aufkommen an eingehenden Nachrichten mit großen Anlagen.

Wenn Version-Buckets oder Batchpunkte überlastet sind, beginnt der Exchange-Server, eingehende Verbindungen einzuschränken, indem die Bestätigung für eingehende Nachrichten verzögert wird. Exchange schränkt die Rate des eingehenden Nachrichtenflusses durch das Teergrubenverfahren ein, bei dem eine Verzögerung in die **MAIL FROM**-Befehle eingeführt wird. Wenn die Ressourcenüberlastung anhält, erhöht Exchange stufenweise die Teergrubenverzögerung. Sobald die Ressourcenauslastung wieder auf einem normalen Niveau liegt, beginnt Exchange, die Bestätigungsverzögerung stufenweise zu verringern und zu einem normalen Betrieb zurückzukehren. Standardmäßig beginnt Exchange bei Ressourcenüberlastung mit einer Verzögerung von Nachrichtenbestätigungen um 10 Sekunden. Wenn die Ressourcenauslastung anhält, wird die Verzögerung in 5-Sekunden-Schritten auf bis zu 55 Sekunden verlängert.

Exchange speichert den Verlauf der Version-Bucket- und Batchpunkt-Ressourcenauslastung. Wenn die Ressourcenauslastung während einer bestimmten Anzahl von Abrufintervallen (Verlaufstiefe) nicht auf ein normales Niveau zurückgeht, beendet Exchange die Teergrubenverzögerung und beginnt mit dem Zurückweisen eingehender Nachrichten, bis die Ressourcenauslastung sich wieder auf einem normalen Niveau befindet. Standardmäßig liegen die Verlaufstiefen für Version-Buckets und Batchpunkte bei 10 bzw. 300 Abrufintervallen.

Zurück zum Seitenanfang

## Vom Prozess "EdgeTransport.exe" verwendeter Arbeitsspeicher

Standardmäßig wird die Stufe Hoch der Arbeitsspeicherauslastung durch den Prozess EdgeTransport.exe mithilfe der folgenden Formel berechnet:

75 % des gesamten physikalischen Arbeitsspeichers oder 1 Terabyte (der kleinere der beiden Werte)

Diese Berechnung enthält weder den virtuellen Arbeitsspeicher, der auf dem Festplattenlaufwerk in der Auslagerungsdatei vorhanden ist, noch den Arbeitsspeicher, der von anderen Prozessen verwendet wird. Das Ergebnis dieser Formel wird als Prozentsatz des gesamten Arbeitsspeichers ausgedrückt, der vom Prozess EdgeTransport.exe verwendet wird. Die Ergebnisse der Formel werden immer auf die nächste ganze Zahl abgerundet.

Standardmäßig wird die mittlere Stufe der Arbeitsspeicherauslastung durch die Datei EdgeTransport.exe als 73 % des gesamten physikalischen Arbeitsspeichers oder 2 % weniger als der Wert der hohen Stufe berechnet (dabei wird der kleinere der beiden Werte verwendet). Standardmäßig wird die normale Stufe der Arbeitsspeicherauslastung durch die Datei EdgeTransport.exe als 71 % des gesamten physikalischen Arbeitsspeichers oder 4 % weniger als der Wert der hohen Stufe berechnet (dabei wird der kleinere der beiden Werte verwendet).

Wenn die Speicherauslastung des Prozesses EdgeTransport.exe höher als der angegebene normale Wert ist, wird eine *Garbage Collection* erzwungen. Als Garbage Collection wird die Überprüfung des Speichers auf nicht verwendete Objekte bezeichnet. Der von nicht verwendeten Objekten belegte Arbeitsspeicher wird anschließend wieder freigegeben.

Exchange speichert den Verlauf der Arbeitsspeicherauslastung des Prozesses "EdgeTransport.exe". Wenn die Auslastung während einer bestimmten Anzahl von Abrufintervallen (Verlaufstiefe) nicht auf ein normales Niveau zurückgeht, beginnt Exchange mit dem Zurückweisen eingehender Nachrichten, bis die Ressourcenauslastung sich wieder auf einem normalen Niveau befindet. Standardmäßig beträgt die Verlaufstiefe für die Speicherauslastung von EdgeTransport.exe 30 Abrufintervalle.

Zurück zum Seitenanfang

## Von allen Prozessen verwendeter Arbeitsspeicher

Standardmäßig beträgt die hohe Stufe der Arbeitsspeicherauslastung durch alle Prozesse 94 % des gesamten physikalischen Arbeitsspeichers. Dieser Wert enthält nicht den virtuellen Arbeitsspeicher, der auf dem Festplattenlaufwerk in der Auslagerungsdatei vorhanden ist.

Wenn die angegebene Stufe der Arbeitsspeicherauslastung erreicht wird, tritt eine *Nachrichtenpausierung* auf. Als "Nachrichtenpausierung" wird der Vorgang des Entfernens nicht erforderlicher Elemente von Nachrichten in Warteschlangen bezeichnet, die im Arbeitsspeicher zwischengespeichert sind. Vollständige Nachrichten werden im Arbeitsspeicher aus Gründen der Leistungssteigerung gespeichert. Durch das Entfernen von MIME-Inhalten aus Nachrichten, die sich in Warteschlangen befinden, sinkt die Arbeitsspeicherauslastung. Allerdings entstehen längere Wartezeiten, da die Nachrichten direkt aus der Nachrichtenwarteschlangendatenbank gelesen werden. Standardmäßig ist die Nachrichtenpausierung aktiviert.

Zurück zum Seitenanfang

## Anzahl der Nachrichten in der Übermittlungswarteschlange

Die Übermittlungswarteschlange ist dem Transportdienst auf Exchange 2013-Postfachservern und auf Edge-Transport-Servern zugeordnet. Das Kategorisierungsmodul verarbeitet jede Nachricht in der Übermittlungswarteschlange. Diese Kategorisierung führt dazu, dass die Nachricht in eine Zustellungswarteschlange gestellt wird. Weitere Informationen finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md) und [Warteschlangen](queues-exchange-2013-help.md). Eine große Anzahl von Nachrichten in der Übermittlungswarteschlange weist darauf hin, dass das Kategorisierungsmodul Nachrichten nicht ordnungsgemäß verarbeiten kann.

Wenn die Übermittlungswarteschlange überlastet ist, beginnt der Exchange-Server, eingehende Verbindungen einzuschränken, indem die Bestätigung für eingehende Nachrichten verzögert wird. Exchange schränkt die Rate des eingehenden Nachrichtenflusses durch das Teergrubenverfahren ein, bei dem eine Verzögerung in die **MAIL FROM**-Befehle eingeführt wird. Wenn die Überlastung der Übermittlungswarteschlange anhält, erhöht Exchange stufenweise die Teergrubenverzögerung. Sobald die Auslastung der Übermittlungswarteschlange wieder auf einem normalen Niveau liegt, beginnt Exchange, die Bestätigungsverzögerung stufenweise zu verringern und zu einem normalen Betrieb zurückzukehren. Standardmäßig beginnt Exchange bei einer Überlastung der Übermittlungswarteschlange mit einer Verzögerung von Nachrichtenbestätigungen um 10 Sekunden. Wenn die Überlastung der Übermittlungswarteschlange anhält, wird die Verzögerung in 5-Sekunden-Schritten auf bis zu 55 Sekunden erhöht.

Exchange speichert den Auslastungsverlauf der Übermittlungswarteschlange. Wenn die Auslastung der Übermittlungswarteschlange während einer bestimmten Anzahl von Abrufintervallen (Verlaufstiefe) nicht auf ein normales Niveau zurückgeht, beendet Exchange die Teergrubenverzögerung und beginnt mit dem Zurückweisen eingehender Nachrichten, bis die Auslastung der Übermittlungswarteschlange sich wieder auf einem normalen Niveau befindet. Standardmäßig liegt die Verlaufstiefe für die Übermittlungswarteschlange bei 300 Abrufintervallen.

## Vom Exchange-Transport unter Ressourcenüberlastung durchgeführte Maßnahmen

In der folgenden Tabelle werden die Maßnahmen zusammengefasst, die der Exchange-Transport bei Überlastung einer bestimmten Ressource durchführt.

### Vom Postfach- und Edge-Transport-Server durchgeführte Rückstauaktionen als Reaktion auf eine Ressourcenüberlastung

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Überlastete Ressource</th>
<th>Auslastungsstufe</th>
<th>Ausgeführte Aktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Festplattenspeicher für Nachrichtenwarteschlangendatenbank</p></td>
<td><p>Mittel</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen der Nachrichtenübermittlung für PICKUP- und Wiedergabeverzeichnisse</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Festplattenspeicher für Nachrichtenwarteschlangendatenbank</p></td>
<td><p>Hoch</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Festplattenspeicher für Transaktionsprotokolle der Nachrichtenwarteschlangendatenbank</p></td>
<td><p>Medium</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Festplattenspeicher für Transaktionsprotokolle der Nachrichtenwarteschlangendatenbank</p></td>
<td><p>Hoch</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Version-Buckets</p></td>
<td><p>Medium</p></td>
<td><p>Starten oder Erhöhen der Teergrubenverzögerung für eingehende Nachrichten. Wenn die Auslastung für die gesamte Version-Bucket-Versionstiefe nicht auf ein normales Niveau zurückgeht, werden folgende Aktionen ausgeführt:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Version-Buckets</p></td>
<td><p>Hoch</p></td>
<td><p>Führen Sie die Teergrubenverzögerung für eingehende Nachrichten ein bzw. erhöhen Sie deren Wert. Wenn für die gesamte Verlaufstiefe des Version-Buckets kein normales Niveau erreicht wird, führen Sie die folgenden Maßnahmen durch:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Batchpunkt</p></td>
<td><p>Medium</p></td>
<td><p>Führen Sie die Teergrubenverzögerung für eingehende Nachrichten ein bzw. erhöhen Sie deren Wert. Wenn die Auslastung für die gesamte Batchpunkt-Versionstiefe nicht auf ein normales Niveau zurückgeht, werden folgende Aktionen ausgeführt:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Batchpunkt</p></td>
<td><p>Hoch</p></td>
<td><p>Führen Sie die Teergrubenverzögerung für eingehende Nachrichten ein bzw. erhöhen Sie deren Wert. Wenn für die gesamte Verlaufstiefe des Batchpunkts kein normales Niveau erreicht wird, führen Sie die folgenden Maßnahmen durch:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Vom Prozess EdgeTransport.exe verwendeter Arbeitsspeicher</p></td>
<td><p>Medium</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
<li><p>Erzwingen der Garbage Collection</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Vom Prozess &quot;EdgeTransport.exe&quot; verwendeter Arbeitsspeicher</p></td>
<td><p>Hoch</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Von allen Prozessen verwendeter Arbeitsspeicher</p></td>
<td><p>Medium</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
<li><p>Erzwingen der Garbage Collection</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Von allen Prozessen verwendeter Arbeitsspeicher</p></td>
<td><p>Hoch</p></td>
<td><ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
<li><p>Leeren des erweiterten DNS-Cache aus dem Arbeitsspeicher</p></li>
<li><p>Starten der Nachrichtenpausierung</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Anzahl der Nachrichten in der Übermittlungswarteschlange</p></td>
<td><p>Medium</p></td>
<td><p>Führen Sie die Teergrubenverzögerung für eingehende Nachrichten ein bzw. erhöhen Sie deren Wert. Wenn für die gesamte Verlaufstiefe der Übermittlungswarteschlange kein normales Niveau erreicht wird, führen Sie die folgenden Maßnahmen durch:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
<li><p>Erzwingen der Garbage Collection</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Anzahl der Nachrichten in der Übermittlungswarteschlange</p></td>
<td><p>Hoch</p></td>
<td><p>Führen Sie die Teergrubenverzögerung für eingehende Nachrichten ein bzw. erhöhen Sie deren Wert. Wenn für die gesamte Verlaufstiefe der Übermittlungswarteschlange kein normales Niveau erreicht wird, führen Sie die folgenden Maßnahmen durch:</p>
<ul>
<li><p>Ablehnen eingehender Nachrichten von anderen Exchange-Servern</p></li>
<li><p>Zurückweisen von Nachrichtenübermittlungen von Postfachdatenbanken durch den Postfachtransport-Übermittlungsdienst auf Postfachservern</p></li>
<li><p>Ablehnen eingehender Nachrichten von Nicht-Exchange-Servern</p></li>
<li><p>Ablehnen von Nachrichtenübermittlungen vom PICKUP- und Wiedergabeverzeichnis</p></li>
<li><p>Leeren des erweiterten DNS-Cache aus dem Arbeitsspeicher</p></li>
<li><p>Starten der Nachrichtenpausierung</p></li>
</ul></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Rückstaukonfigurationsoptionen in der Datei "EdgeTransport.exe.config"

Alle Konfigurationsoptionen für den Rückstau stehen in der XML-Anwendungskonfigurationsdatei "%ExchangeInstallPath%Bin\\EdgeTransport.exe.config" zur Verfügung.


> [!WARNING]
> Diese Einstellungen werden lediglich zur Referenz aufgeführt. Es wird dringend davon abgeraten, in der Datei EdgeTransport.exe.config Änderungen an den Rückstaueinstellungen vorzunehmen. Änderungen an den Rückstaueinstellungen können zu einer Leistungsbeeinträchtigung oder zu Datenverlust führen. Es wird empfohlen, die Ursachen für Rückstauereignisse zu ermitteln und diese nach Möglichkeit zu beseitigen.



### Konfigurationsoptionen für die Rückstaufunktion

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Schlüsselname</th>
<th>Standardwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>EnableResourceMonitoring</em></p></td>
<td><p>true</p></td>
</tr>
<tr class="even">
<td><p><em>ResourceMonitoringInterval</em></p></td>
<td><p><code>00:00:02</code> (2 Sekunden)</p></td>
</tr>
<tr class="odd">
<td><p><em>PercentageDatabaseDiskSpaceUsedHighThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass die Standardformel verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p><em>PercentageDatabaseDiskSpaceUsedMediumThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentageDatabaseDiskSpaceUsedHighThreshold</em> liegt.</p></td>
</tr>
<tr class="odd">
<td><p><em>PercentageDatabaseDiskSpaceUsedNormalThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentageDatabaseDiskSpaceUsedMediumThreshold</em> liegt.</p></td>
</tr>
<tr class="even">
<td><p><em>PercentageDatabaseLoggingDiskSpaceUsedHighThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass die Standardformel verwendet wird.</p></td>
</tr>
<tr class="odd">
<td><p><em>PercentageDatabaseLoggingDiskSpaceUsedMediumThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentageDatabaseLoggingDiskSpaceUsedHighThreshold</em> liegt.</p></td>
</tr>
<tr class="even">
<td><p><em>PercentageDatabaseLoggingDiskSpaceUsedNormalThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentageDatabaseLoggingDiskSpaceUsedMediumThreshold</em> liegt.</p></td>
</tr>
<tr class="odd">
<td><p><em>PercentagePrivateBytesUsedHighThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass die Standardberechnung verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p><em>PercentagePrivateBytesUsedMediumThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentagePrivateBytesUsedHighThreshold</em> liegt.</p></td>
</tr>
<tr class="odd">
<td><p><em>PercentagePrivateBytesUsedNormalThreshold</em></p></td>
<td><p>0. Dieser Wert zeigt an, dass der tatsächliche Wert 2 % unterhalb des Werts von <em>PercentagePrivateBytesUsedMediumThreshold</em> liegt.</p></td>
</tr>
<tr class="even">
<td><p><em>VersionBucketsHighThreshold</em></p></td>
<td><p>200</p></td>
</tr>
<tr class="odd">
<td><p><em>VersionBucketsMediumThreshold</em></p></td>
<td><p>120</p></td>
</tr>
<tr class="even">
<td><p><em>VersionBucketsNormalThreshold</em></p></td>
<td><p>80</p></td>
</tr>
<tr class="odd">
<td><p><em>VersionBucketsHistoryDepth</em></p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p><em>BatchPointHighThreshold</em></p></td>
<td><p>4000</p></td>
</tr>
<tr class="odd">
<td><p><em>BatchPointMediumThreshold</em></p></td>
<td><p>2000</p></td>
</tr>
<tr class="even">
<td><p><em>BatchPointNormalThreshold</em></p></td>
<td><p>1000</p></td>
</tr>
<tr class="odd">
<td><p><em>BatchPointHistoryDepth</em></p></td>
<td><p>300</p></td>
</tr>
<tr class="even">
<td><p><em>BatchPointUseCostForPressure</em></p></td>
<td><p>true</p></td>
</tr>
<tr class="odd">
<td><p><em>BatchPointBatchSize</em></p></td>
<td><p>40</p></td>
</tr>
<tr class="even">
<td><p><em>BatchPointBatchTimeout</em></p></td>
<td><p><code>00:00:00.100</code> (0,1 Sekunden)</p></td>
</tr>
<tr class="odd">
<td><p><em>BatchPointItemExpiryInterval</em></p></td>
<td><p><code>00:05:00</code> (5 Minuten)</p></td>
</tr>
<tr class="even">
<td><p><em>SMTPBaseThrottlingDelayInterval</em></p></td>
<td><p><code>00:00:00</code></p></td>
</tr>
<tr class="odd">
<td><p><em>SMTPMaxThrottlingDelayInterval</em></p></td>
<td><p><code>00:00:55</code> (55 Sekunden)</p></td>
</tr>
<tr class="even">
<td><p><em>SMTPStepThrottlingDelayInterval</em></p></td>
<td><p><code>00:00:05</code> (5 Sekunden)</p></td>
</tr>
<tr class="odd">
<td><p><em>SMTPStartThrottlingDelayInterval</em></p></td>
<td><p><code>00:00:10</code> (10 Sekunden)</p></td>
</tr>
<tr class="even">
<td><p><em>PercentagePhysicalMemoryUsedLimit</em></p></td>
<td><p>94</p></td>
</tr>
<tr class="odd">
<td><p><em>DehydrateMessagesUnderMemoryPressure</em></p></td>
<td><p>true</p></td>
</tr>
<tr class="even">
<td><p><em>PrivateBytesHistoryDepth</em></p></td>
<td><p>30</p></td>
</tr>
<tr class="odd">
<td><p><em>SubmissionQueueHighThreshold</em></p></td>
<td><p>10000</p></td>
</tr>
<tr class="even">
<td><p><em>SubmissionQueueMediumThreshold</em></p></td>
<td><p>4000</p></td>
</tr>
<tr class="odd">
<td><p><em>SubmissionQueueNormalThreshold</em></p></td>
<td><p>2000</p></td>
</tr>
<tr class="even">
<td><p><em>SubmissionQueueHistoryDepth</em></p></td>
<td><p>300</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Rückstauprotokollierungsinformationen

In der folgenden Liste werden die Ereignisprotokolleinträge beschrieben, die durch bestimmte Rückstauereignisse in Exchange generiert werden:

  - **Ereignisprotokolleintrag für einen Anstieg in einer beliebigen Ressourcenauslastungsstufe**
    
    Ereignistyp: Fehler
    
    Ereignisquelle: MSExchangeTransport
    
    Ereigniskategorie: Ressourcen-Manager
    
    Ereignis-ID: 15004
    
    Beschreibung: Die Ressourcenauslastungstufe wurde von *Previous Utilization Level* auf *Current Utilization Level* erhöht.

  - **Ereignisprotokolleintrag für einen Abfall in einer beliebigen Ressourcenauslastungsstufe**
    
    Ereignistyp: Information
    
    Ereignisquelle: MSExchangeTransport
    
    Ereigniskategorie: Ressourcen-Manager
    
    Ereignis-ID: 15005
    
    Beschreibung: Die Ressourcenauslastungstufe wurde von *Previous Utilization Level* auf *Current Utilization Level* abgesenkt.

  - **Ereignisprotokolleintrag für kritisch niedrigen verfügbaren Festplattenspeicherplatz**
    
    Ereignistyp: Fehler
    
    Ereignisquelle: MSExchangeTransport
    
    Ereigniskategorie: Ressourcen-Manager
    
    Ereignis-ID: 15006
    
    Beschreibung: Der Microsoft Exchange-Transportdienst weist Nachrichten zurück, weil der verfügbare Speicherplatz den konfigurierten Schwellenwert unterschritten hat. Ggf. sind Verwaltungsaktionen erforderlich, um Speicherplatz freizugeben, damit der Dienst seinen Betrieb fortsetzen kann.

  - **Ereignisprotokolleintrag für kritisch niedrigen verfügbaren Arbeitsspeicher**
    
    Ereignistyp: Fehler
    
    Ereignisquelle: MSExchangeTransport
    
    Ereigniskategorie: Ressourcen-Manager
    
    Ereignis-ID: 15007
    
    Beschreibung: Der Microsoft Exchange-Transportdienst weist Nachrichtenübermittlungen zurück, weil der Dienst auch weiterhin mehr Arbeitsspeicher als den konfigurierten Schwellenwert belegt. Möglicherweise ist ein Neustart dieses Diensts erforderlich, damit der normale Betrieb fortgesetzt werden kann.

Zurück zum Seitenanfang

