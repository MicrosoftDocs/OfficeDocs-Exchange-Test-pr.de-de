---
title: 'Exchange 2013-Leistungsindikatoren: Exchange 2013 Help'
TOCTitle: Exchange 2013-Leistungsindikatoren
ms:assetid: 9143dd77-7c30-4769-8de1-28c717cfa9e9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn904093(v=EXCHG.150)
ms:contentKeyID: 63910995
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exchange 2013-Leistungsindikatoren

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-02-06_

## Exchange 2013-Leistungsindikatoren

In den folgenden Abschnitten sind nützliche Leistungsindikatoren aufgeführt, die Sie bei der Problembehandlung von Leistungsproblemen in Exchange 2013 verwenden können.

## Leistungsindikatoren für Exchange-Domänencontrollerverbindungen

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu Leistungsindikatoren für die Exchange-Domänencontrollerkonnektivität aufgeführt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Leistungsindikator</th>
<th>Beschreibung</th>
<th>Schwellenwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MSExchange ADAccess-Domänencontroller(*)\LDAP-Lesedauer</p></td>
<td><p>Zeigt die Zeit in Millisekunden (ms) an, die benötigt wird, um eine LDAP-Leseanforderung an den angegebenen Domänencontroller zu senden und eine Antwort zu erhalten.</p></td>
<td><p>Dieser Wert sollte im Durchschnitt unter 50 ms liegen. Spitzen (Maximalwerte) sollten 100 ms nicht überschreiten.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange ADAccess-Domänencontroller(*)\LDAP-Suchdauer</p></td>
<td><p>Zeigt die Zeit in Millisekunden (ms) an, die benötigt wird, um eine LDAP-Suchanforderung zu senden und eine Antwort zu erhalten.</p></td>
<td><p>Dieser Wert sollte im Durchschnitt unter 50 ms liegen. Spitzen (Maximalwerte) sollten 100 ms nicht überschreiten.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange ADAccess-Prozesse(*)\LDAP-Lesedauer</p></td>
<td><p>Zeigt die Zeit in Millisekunden (ms) an, die benötigt wird, um eine LDAP-Leseanforderung an den angegebenen Domänencontroller zu senden und eine Antwort zu erhalten.</p></td>
<td><p>Dieser Wert sollte im Durchschnitt unter 50 ms liegen. Spitzen (Maximalwerte) sollten 100 ms nicht überschreiten.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange ADAccess-Prozesse(*)\LDAP-Suchdauer</p></td>
<td><p>Zeigt die Zeit in Millisekunden (ms) an, die benötigt wird, um eine LDAP-Suchanforderung zu senden und eine Antwort zu erhalten.</p></td>
<td><p>Dieser Wert sollte im Durchschnitt unter 50 ms liegen. Spitzen (Maximalwerte) sollten 100 ms nicht überschreiten.</p></td>
</tr>
</tbody>
</table>


## Indikatoren für Prozessoren und Prozesse

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu Prozessoren und Prozessleistungsindikatoren angezeigt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Leistungsindikator</th>
<th>Beschreibung</th>
<th>Schwellenwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Prozessor(_Total)\Prozessorzeit (%)</p></td>
<td><p>Zeigt den Prozentsatz des Zeitraums an, in dem der Prozessor Anwendungs- oder Betriebssystemprozesse ausführt. In dieser Zeit ist der Prozessor nicht im Leerlauf.</p></td>
<td><p>Sollte im Durchschnitt unter 75 % liegen.</p></td>
</tr>
<tr class="even">
<td><p>Prozessor(_Total)\Benutzerzeit (%)</p></td>
<td><p>Zeigt den Prozentsatz der Prozessorzeit an, die im Benutzermodus absolviert wird. Der Benutzermodus ist ein eingeschränkter Verarbeitungsmodus, der auf Anwendungen, Subsysteme der Umgebung und integrierte Subsysteme ausgelegt ist.</p></td>
<td><p>Sollte im Durchschnitt unter 75 % liegen.</p></td>
</tr>
<tr class="odd">
<td><p>Prozessor(_Total)\% privilegierte Zeit</p></td>
<td><p>Zeigt den Prozentsatz der Prozessorzeit an, die im privilegierten Modus absolviert wird. Der privilegierte Modus ist ein Verarbeitungsmodus, der auf Betriebssystemkomponenten und hardwaremanipulierende Treiber ausgelegt ist. Er ermöglicht den direkten Zugriff auf Hardware und den gesamten Arbeitsspeicher.</p></td>
<td><p>Sollte im Durchschnitt unter 75 % liegen.</p></td>
</tr>
<tr class="even">
<td><p>System\Prozessor-Warteschlangenlänge (alle Instanzen)</p></td>
<td><p>Gibt die Anzahl der Threads an, die von jedem Prozessor verarbeitet wird. Mithilfe der Prozessor-Warteschlangenlänge können Sie identifizieren, ob Prozessorkonflikte oder hohe CPU-Auslastung dadurch verursacht werden, dass die Prozessorkapazität für die Verarbeitung der zugewiesenen Arbeitslast nicht ausreichend ist. Die Prozessor-Warteschlangenlänge zeigt die Anzahl der Threads an, die in der Prozessorbereitschafts-Warteschlange verzögert sind und auf ihre Ausführung warten. Der aufgeführte Wert ist der zuletzt erfasste Wert zum Zeitpunkt der Messung.</p></td>
<td><p>Sollte nicht höher als 5 pro Prozessor sein.</p></td>
</tr>
<tr class="odd">
<td><p>Prozess(*)\Prozessorzeit (%)</p></td>
<td><p>Kann zum Identifizieren der jeweiligen Prozesse verwendet werden, die CPU-Zeit verbrauchen.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Indikatoren für den Arbeitsspeicher

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu Leistungsindikatoren für Speicher angezeigt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>Speicher\Verfügbare MB</p></td>
<td><p>Zeigt die Menge des physikalischen Arbeitsspeichers in MB an, der sofort für die Zuweisung zu einem Prozess bzw. für die Systemverwendung verfügbar ist. Ist gleich der Summe des Arbeitsspeichers, der Standby (zwischengespeichert)-, Frei- und Nullseitenlisten zugewiesen sind. Eine genaue Beschreibung des Speicher-Managers finden Sie unter MSDN (Microsoft Developer Network) oder im Windows Server 2003 Resource Kit unter &quot;Systemleistung und Problembehandlung&quot;.</p></td>
<td><p>Sollte über 5 % des gesamten Arbeitsspeichers bleiben.</p></td>
</tr>
<tr class="odd">
<td><p>Memory\% Committed Bytes In Use</p></td>
<td><p>Zeigt das Verhältnis von &quot;Arbeitsspeicher\Zugesicherte Bytes&quot; zu &quot;Arbeitsspeicher\Zusicherungslimit&quot; an. Zugesicherter Speicher ist belegter physikalischer Speicher, für den in der Auslagerungsdatei Speicherplatz reserviert wurde, damit er auf den Datenträger geschrieben werden kann. Das Zusicherungslimit wird durch die Größe der Auslagerungsdatei bestimmt. Wenn die Auslagerungsdatei vergrößert wird, wird das Zusicherungslimit erhöht und das Verhältnis reduziert. Dieser Indikator zeigt nur den aktuellen Prozentwert an, keinen Durchschnittswert.</p></td>
<td><p>Wenn dieser Wert mehr als 80 % ist, weist dies darauf hin, dass das System wahrscheinlich bei Überlastung mehr Arbeitsspeicher bereitstellt.</p></td>
</tr>
</tbody>
</table>


## Indikatoren für .NET Framework

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu .NET Framework-Leistungsindikatoren angezeigt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>.NET CLR-Speicher(*)\GC-Zeitdauer in Prozent</p></td>
<td><p>Zeigt an, wenn Garbage Collection aufgetreten ist. Wenn der Indikator den Schwellenwert überschreitet, weist dies darauf hin, dass die CPU eine Bereinigung durchführt und nicht effizient für Arbeitslasten verwendet wird. Durch Hinzufügen von Arbeitsspeicher auf dem Server kann diese Situation verbessert werden.</p></td>
<td><p>Sollte im Durchschnitt unter 10 % liegen.</p></td>
</tr>
<tr class="odd">
<td><p>.NET CLR-Ausnahmen(*)\Anzahl ausgelöster Ausnahmen/s</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde ausgelösten Ausnahmen an. Dazu gehören .NET Framework-Ausnahmen und nicht verwaltete Ausnahmen, die in .NET Framework-Ausnahmen konvertiert werden. So wird beispielsweise die Nullzeigerverweis-Ausnahme in nicht verwaltetem Code erneut im verwalteten Code als eine .NET Framework System.NullReferenceException ausgelöst. Dieser Indikator erfasst sowohl behandelte als auch nicht behandelte Ausnahmen.</p></td>
<td><p>Sollte niedriger als 5 % der Gesamtanforderungen pro Sekunde sein (Webserver(_Total)\Verbindungsversuche/s * 0,05).</p></td>
</tr>
<tr class="even">
<td><p>.NET CLR-Speicher(*)\Anzahl der Bytes in den Heaps</p></td>
<td><p>Zeigt die Summe aus vier anderen Indikatoren an: &quot;Heapgröße der Generation 0&quot;, &quot;Heapgröße der Generation 1&quot;, &quot;Heapgröße der Generation 2&quot; und die &quot;Objektheapgröße&quot;. Dieser Indikator zeigt den aktuell in den GC-Heaps zugeordneten Speicher in Byte an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Indikatoren für das Netzwerk

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu typischen Netzwerkleistungsindikatoren angezeigt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>Netzwerkschnittstelle(*)\Ausgehende Pakete, Fehler</p></td>
<td><p>Die Anzahl ausgehender Pakete, die aufgrund von Fehlern nicht übertragen werden konnten.</p></td>
<td><p>Muss immer 0 sein.</p></td>
</tr>
<tr class="odd">
<td><p>TCPv6\Verbindungsfehler</p></td>
<td><p>Zeigt die Anzahl der TCP-Verbindungen an, deren aktueller Zustand ESTABLISHED oder CLOSE-WAIT ist. Die Anzahl der TCP-Verbindungen, die erstellt werden können, wird von der Größe des nicht ausgelagerten Pools eingeschränkt. Wenn der nicht ausgelagerte Pool ausgeschöpft ist, können keine neuen Verbindungen erstellt werden.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>TCPv4\Zurückgesetzte Verbindungen</p></td>
<td><p>Zeigt an, wie oft TCP-Verbindungen direkt vom Zustand ESTABLISHED oder CLOSE-WAIT in CLOSED übergegangen sind.</p></td>
<td><p>Eine zunehmende Anzahl von Zurücksetzungsvorgängen oder eine konsistent steigende Rate von Zurücksetzungsvorgängen kann auf einen Bandbreitenengpass hinweisen.</p></td>
</tr>
<tr class="odd">
<td><p>TCPv6\Zurückgesetzte Verbindungen</p></td>
<td><p>Zeigt an, wie oft TCP-Verbindungen direkt vom Zustand ESTABLISHED oder CLOSE-WAIT in CLOSED übergegangen sind.</p></td>
<td><p>Eine zunehmende Anzahl von Zurücksetzungsvorgängen oder eine konsistent steigende Rate von Zurücksetzungsvorgängen kann auf einen Bandbreitenengpass hinweisen.</p></td>
</tr>
</tbody>
</table>


## Netlogon-Leistungsindikatoren

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu allgemeinen Leistungsindikatoren zur Überwachung von NTLM-Authentifizierungs- und MaxConcurrentAPI-Problemen aufgeführt. Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 2688798 [Leistungsoptimierung für die NTLM-Authentifizierung mithilfe der MaxConcurrentAPI-Einstellung](https://go.microsoft.com/fwlink/p/?linkid=389728).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>\Netlogon\Semaphore Waiters</p></td>
<td><p>Die Anzahl der Threads, die darauf waren, das Semaphorobjekt zu erhalten.</p></td>
<td><p>Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 2688798 <a href="https://go.microsoft.com/fwlink/p/?linkid=389728">Leistungsoptimierung für die NTLM-Authentifizierung mithilfe der MaxConcurrentAPI-Einstellung</a></p></td>
</tr>
<tr class="odd">
<td><p>\Netlogon\Semaphore Holders</p></td>
<td><p>Die Anzahl der Threads, die das Semaphorobjekt halten.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>\Netlogon\Semaphore Acquires</p></td>
<td><p>Wie oft das Semaphorobjekt über die Lebensdauer der Sicherheitskanalverbindung oder seit dem Systemstart für _Total abgerufen wurde.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>\Netlogon\Semaphore Timeouts</p></td>
<td><p>Die Gesamtanzahl der Fälle, in denen ein Thread ein Timeout erreicht hat, während er über die Lebensdauer der Sicherheitskanalverbindung oder seit dem Systemstart für _Total auf das Semaphorobjekt gewartet hat.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>\Netlogon\Average Semaphore Hold Time</p></td>
<td><p>Die durchschnittliche Zeit (in Sekunden), für die das Semaphorobjekt über das letzte Beispiel gehalten wird.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Indikatoren für Datenbanken

In der folgenden Tabelle werden Indikatoren für E/A-Wartezeitanforderungen aktiver Protokolle und ihre akzeptablen Schwellenwerte aufgeführt. Wenn diese Schwellenwerte überschritten werden, verschlechtert sich die Clientleistung. Es treten beispielsweise Verzögerungen bei der Nachrichtenzustellung und eine langsame Systemleistung auf.


> [!NOTE]
> Die Leitlinien für die normale Speicherlatenz in Exchange 2013 ähneln den Leitlinien für Exchange 2010. Zusätzliche Datenbankleistungsindikatoren finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=525622">Leistungsindikatoren für Postfachserver</A>.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Reads (Attached) Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Dauer pro Datenbanklesevorgang in Millisekunden (ms) an.</p></td>
<td><p>Sollte im Durchschnitt unter 20 ms liegen.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Writes (Attached) Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Dauer pro Datenbankschreibvorgang in Millisekunden (ms) an.</p></td>
<td><p>Sollte im Durchschnitt unter 50 ms liegen.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Log Writes Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Dauer pro Protokollschreibvorgang in Millisekunden (ms) an.</p></td>
<td><p>Sollte im Durchschnitt unter 10 ms liegen.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Reads (Recovery) Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Dauer pro passivem Datenbanklesevorgang in Millisekunden (ms) an.</p></td>
<td><p>Sollte im Durchschnitt unter 200 ms liegen.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Writes (Recovery) Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Dauer pro passivem Datenbankschreibvorgang in Millisekunden (ms) an.</p></td>
<td><p>Sollte unter der Wartezeit für Leseoperationen für dieselbe Instanz liegen, wie durch den Leistungsindikator MSExchange Database ==&gt; Instances(*)\I/O Database Reads (Recovery) Average Latency gemessen.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Reads (Attached)/sec</p></td>
<td><p>Zeigt die Anzahl der Datenbanklesevorgänge pro Sekunde für jede angebundene Datenbankinstanz an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Database Writes (Attached)/sec</p></td>
<td><p>Zeigt die Anzahl der Datenbankschreibvorgänge pro Sekunde für jede angebundene Datenbankinstanz an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange Database ==&gt; Instances(*)\I/O Log Writes/sec</p></td>
<td><p>Zeigt die Anzahl der Protokollschreibvorgänge pro Sekunde für jede Datenbankinstanz an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>MSExchange Active Manager(_total)\Database Mounted</p></td>
<td><p>Zeigt die Anzahl der aktiven Datenbankkopien auf dem Server an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## ASP.NET

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu ASP.NET-Leistungsindikatoren angezeigt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>ASP.NET\Anwendungsneustarts</p></td>
<td><p>Zeigt an, wie oft die Anwendung während der Lebensdauer des Webservers neu gestartet wurde.</p></td>
<td><p>Muss immer 0 sein.</p></td>
</tr>
<tr class="odd">
<td><p>ASP.NET\Workerprozess-Neustarts</p></td>
<td><p>Zeigt an, wie oft ein Workerprozess auf dem Computer neu gestartet wurde.</p></td>
<td><p>Muss immer 0 sein.</p></td>
</tr>
<tr class="even">
<td><p>ASP.NET\Wartezeit der Anforderung</p></td>
<td><p>Zeigt die Wartezeit der letzten Anforderung in der Warteschlange in Millisekunden an.</p></td>
<td><p>Muss immer 0 sein.</p></td>
</tr>
<tr class="odd">
<td><p>ASP.NET-Anwendungen(*)\Anforderungen in der Anwendungswarteschlange</p></td>
<td><p>Zeigt die Anzahl der Anforderungen in der Warteschlange der Anwendung an.</p></td>
<td><p>Muss immer 0 sein.</p></td>
</tr>
<tr class="even">
<td><p>ASP.NET Applications(*)\Requests Executing</p></td>
<td><p>Zeigt die Anzahl der derzeit ausgeführten Anforderungen an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>ASP.NET Applications(*)\Requests/Sec</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde ausgeführten Anforderungen an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Indikatoren für den RPC-Clientzugriff

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu Leistungsindikatoren für den RPC-Clientzugriff aufgeführt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>MSExchange RpcClientAccess\Durchschnittl. RPC-Wartezeit</p></td>
<td><p>Zeigt die durchschnittliche Wartezeit in Millisekunden (ms) für die letzten 1.024 Pakete an.</p></td>
<td><p>Sollte unter 250 ms liegen.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange RpcClientAccess\RPC-Anforderungen</p></td>
<td><p>Zeigt die Anzahl der Clientanforderungen an, die aktuell vom RPC-Clientzugriffsdienst verarbeitet werden.</p></td>
<td><p>Der Wert sollte nicht über 40 liegen.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange RpcClientAccess\Anzahl aktiver Benutzer</p></td>
<td><p>Zeigt die Anzahl der eindeutigen Benutzer an, die in den letzten 2 Minuten aktiv gewesen sind.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange RpcClientAccess\Verbindungsanzahl</p></td>
<td><p>Zeigt die Gesamtzahl der bestehenden Clientverbindungen an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>MSExchange RpcClientAccess\RPC-Vorgänge/Sek.</p></td>
<td><p>Zeigt die Rate der RPC-Vorgänge pro Sekunde an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange RpcClientAccess\Anzahl Benutzer</p></td>
<td><p>Zeigt die Anzahl der Benutzer an, die mit dem Dienst verbunden sind.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## HTTP-Proxy-Leistungsindikatoren

In den folgenden Tabellen sind Informationen zu HTTP-Proxy-Leistungsindikatoren angezeigt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
</tr>
<tr class="even">
<td><p>MSExchange HttpProxy(*)\MailboxServerLocator Average Latency</p></td>
<td><p>Zeigt die durchschnittliche Wartezeit (ms) von MailboxServerLocator-Webdienstaufrufen an.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange HttpProxy(*)\Average Authentication Latency</p></td>
<td><p>Zeigt die durchschnittliche Zeit für die Authentifizierung von CAS-Anforderungen über die letzten 200 Beispiele an.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange HttpProxy(*)\Average ClientAccess Server Processing Latency</p></td>
<td><p>Zeigt die durchschnittliche Wartezeit (ms) der CAS-Verarbeitungszeit (umfasst keine Zeit für die Proxyfunktion) über die letzten 200 Anforderungen an.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange HttpProxy(*)\Mailbox Server Proxy Failure Rate</p></td>
<td><p>Zeigt den Prozentsatz von konnektivitätsbezogenen Fehlern zwischen diesem Clientzugriffsserver und MBX-Servern über die letzten 200 Beispiele an.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange HttpProxy(*)\Outsanding Proxy Requests</p></td>
<td><p>Zeigt die Anzahl von gleichzeitigen ausstehenden Proxyanforderungen an.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange HttpProxy(*)\Proxy Requests/Sec</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Proxyanforderungen an.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange HttpProxy(*)\Requests/Sec</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Anforderungen an.</p></td>
</tr>
</tbody>
</table>


## Indikatoren für den Informationsspeicher

In den folgenden Tabellen sind die akzeptablen Schwellenwerte und Informationen zu Leistungsindikatoren für Informationsspeicher angezeigt.


> [!NOTE]
> Die Leitlinien für die normale Speicherlatenz in Exchange 2013 ähneln den Leitlinien für Exchange 2010. Zusätzliche Informationsspeicherindikatoren finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=525622">Leistungsindikatoren für Postfachserver</A>.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
<td><p>Schwellenwert</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeIS Store (*) \RPC Anfragen</p></td>
<td><p>Zeigt die Gesamtanzahl von RPC-Anforderungen an, die aktuell im Informationsspeicherprozess ausgeführt werden.</p></td>
<td><p>Sollte zu jeder Zeit unter 70 liegen.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeIS Client Type(*)\RPC Average Latency</p></td>
<td><p>Zeigt die Server-RPC-Wartezeit in Millisekunden (ms) als Durchschnitt der letzten 1.024 Pakete für ein bestimmtes Clientprotokoll an.</p></td>
<td><p>Sollte im Durchschnitt für jeden Client unter 50 ms liegen.</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeIS Store(*)\RPC Average Latency</p></td>
<td><p>Die durchschnittliche RPC-Wartezeit (ms) ist die durchschnittliche Wartezeit in Millisekunden von RPC-Anforderungen pro Datenbank. Der Durchschnitt wird aus allen RPCs seit dem Laden von exrpc32 berechnet.</p></td>
<td><p>Sollte jederzeit weniger als 50 Millisekunden betragen, mit Spitzen unter 100 ms.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeIS Store(*)\RPC Operations/sec</p></td>
<td><p>Zeigt die Anzahl der RPC-Vorgänge pro Sekunde für jede Datenbankinstanz an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeIS Client Type(*)\RPC Operations/sec</p></td>
<td><p>Zeigt die Anzahl der RPC-Vorgänge pro Sekunde für jede Clienttypverbindung an.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Indikatoren für Clientzugriffsserver

In den folgenden Tabellen sind Informationen zu Leistungsindikatoren für Clientverbindungen und IIS (Internetinformationsdienste)-Leistungsindikatoren aufgeführt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
</tr>
<tr class="even">
<td><p>MSExchange ActiveSync\Anforderungen/Sek.</p></td>
<td><p>Zeigt die Anzahl der HTTP-Anforderungen an, die pro Sekunde über ASP.NET vom Client empfangen wurden. Ermittelt die aktuelle Exchange ActiveSync-Anforderungsrate. Dient nur zur Ermittlung der aktuellen Benutzerlast.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange ActiveSync\Ausstehende Ping-Befehle</p></td>
<td><p>Zeigt die Anzahl der aktuell in der Warteschlange ausstehenden Ping-Befehle an.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange ActiveSync\Synchronisierungsbefehle/Sek.</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Synchronisierungsbefehle an. Clients verwenden diesen Befehl zum Synchronisieren von Elementen innerhalb eines Ordners.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange-Verfügbarkeitsdienst\Verfügbarkeitsanforderungen (Sek.)</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Anforderungen an. Die Anforderung kann nur für Frei/Gebucht-Informationen gelten oder Vorschläge enthalten. Eine Anforderung kann mehrere Postfächer enthalten. Ermittelt die Rate, mit der Verfügbarkeitsdienstanforderungen auftreten.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange OWA\Aktuelle eindeutige Benutzer</p></td>
<td><p>Zeigt die Anzahl der eindeutigen Benutzer an, die aktuell bei Outlook Web App angemeldet sind. Dieser Wert überwacht die Anzahl der aktiven Sitzungen eindeutiger Benutzer, sodass Benutzer nur aus diesem Indikator entfernt werden, nachdem sie sich abgemeldet haben oder ihre Sitzung einen Timeout hatte. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange OWA\Anforderungen/Sek.</p></td>
<td><p>Zeigt die Anzahl der Anforderungen, die pro Sekunde von Outlook Web App verarbeitet werden. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeAutodiscover\Anforderungen/Sek.</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Anforderungen des AutoErmittlungsdiensts an. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeWS\Anforderungen/Sek.</p></td>
<td><p>Zeigt die Anzahl der pro Sekunde verarbeiteten Anforderungen an. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="even">
<td><p>Webdienst(_Total)\Aktuelle Verbindungen</p></td>
<td><p>Zeigt die Anzahl der Verbindungen an, die zurzeit mit dem Webdienst hergestellt sind. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="odd">
<td><p>Web Service(Default Web Site)\Current Connections</p></td>
<td><p>Zeigt die aktuelle Anzahl der Verbindungen an, die zur Standardwebsite eingerichtet sind, was der Anzahl der Verbindungen entspricht, die auf der Front-End-CAS-Serverrolle eingehen. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="even">
<td><p>Webdienst(_Total)\Verbindungsversuche/s</p></td>
<td><p>Zeigt die Rate der Verbindungsversuche mit dem Webdienst pro Sekunde an. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
<tr class="odd">
<td><p>Webdienst(_Total)\Andere Anforderungsmethoden/s</p></td>
<td><p>Zeigt die Rate der HTTP-Anforderungen ohne die Methoden OPTIONS, GET, HEAD, POST, PUT, DELETE, TRACE, MOVE, COPY, MKCOL, PROPFIND, PROPPATCH, SEARCH, LOCK oder UNLOCK an. Ermittelt die aktuelle Benutzerlast.</p></td>
</tr>
</tbody>
</table>


## Leistungsindikatoren für die Verwaltung der Arbeitsauslastung

In den folgenden Tabellen sind Informationen zu Leistungsindikatoren für die Verwaltung der Exchange-Arbeitsauslastung aufgeführt. Die Überwachung dieser Leistungsindikatoren ist wichtig, da die Verwaltung der Arbeitsauslastung möglicherweise während Normalzeiten Aufgaben im Hintergrund ausführt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Leistungsindikator</p></td>
<td><p>Beschreibung</p></td>
</tr>
<tr class="even">
<td><p>MSExchange WorkloadManagement Workloads(*)\ActiveTasks</p></td>
<td><p>Zeigt die Anzahl der aktiven Aufgaben an, die derzeit im Hintergrund für die Verwaltung der Arbeitsauslastung ausgeführt werden.</p></td>
</tr>
<tr class="odd">
<td><p>MSExchange WorkloadManagement Workloads(*)\CompletedTasks</p></td>
<td><p>Zeigt die Anzahl der Aufgaben der Verwaltung der Arbeitsauslastung an, die abgeschlossen wurden.</p></td>
</tr>
<tr class="even">
<td><p>MSExchange WorkloadManagement Workloads(*)\QueuedTasks</p></td>
<td><p>Zeigt die Anzahl der Aufgaben der Verwaltung der Arbeitsauslastung an, die derzeit in einer Warteschlange auf die Verarbeitung warten.</p></td>
</tr>
</tbody>
</table>

