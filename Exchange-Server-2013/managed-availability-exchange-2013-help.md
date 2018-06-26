---
title: 'Verwaltete Verfügbarkeit: Exchange 2013 Help'
TOCTitle: Verwaltete Verfügbarkeit
ms:assetid: ceb99e6f-6dca-446d-abfb-3e6fc6a72704
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn482056(v=EXCHG.150)
ms:contentKeyID: 59889669
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwaltete Verfügbarkeit

 

_**Gilt für:**Exchange Online, Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:**2017-03-29_

Die Hauptaufgabe der Administratoren eines Messagingsystems besteht darin, Benutzern eine reibungslose E-Mail-Erfahrung zu ermöglichen. Um die Verfügbarkeit und Zuverlässigkeit einer Microsoft Exchange Server 2013-Organisation sicherzustellen, müssen sämtliche Aspekte des Systems aktiv überwacht und erkannte Probleme schnell gelöst werden. In früheren Versionen von Exchange erforderte die Überwachung wichtiger Systemkomponenten in der Regel eine externe Anwendung, wie Microsoft System Center 2012 Operations Manager, um Daten zu sammeln und Wiederherstellungsaktionen für durch die Datenanalyse erkannte Probleme bereitzustellen. Exchange 2010 und frühere Versionen enthielten Statusmanifeste und Korrelationsmodule in Form von Verwaltungspaketen. Mithilfe dieser Komponenten wurde von Operations Manager entschieden, ob sich eine bestimmte Komponente in einem fehlerhaften oder fehlerfreien Zustand befindet. Darüber hinaus wurden von Operations Manager mithilfe der integrierten Diagnose-Cmdlets von Exchange 2010 synthetische Transaktionen für verschiedene Systemaspekte ausgeführt.

In Exchange 2013 wird ein neuer Ansatz für die systemeigene Überwachung und Aufrechterhaltung der Endbenutzerumgebung verfolgt. Dabei wird ein Feature namens *verwaltete Verfügbarkeit* verwendet, das integrierte Überwachungs- und Wiederherstellungsaktionen bietet.

## Verwaltete Verfügbarkeit

Bei der verwalteten Verfügbarkeit, auch als *aktive Überwachung* oder *lokale aktive Überwachung* bezeichnet, handelt es sich um die Integration integrierter Überwachungs- und Wiederherstellungsaktionen in die integrierte, hochverfügbare Plattform von Exchange. Sie ist dafür vorgesehen, vom System erkannte Probleme sofort zu ermitteln und zu beheben. Im Gegensatz zu früheren externen Überwachungslösungen und -techniken für Exchange versucht die verwaltete Verfügbarkeit nicht, die eigentliche Ursache eines Problems zu ermitteln oder zu kommunizieren. Sie konzentriert sich stattdessen auf Wiederherstellungsaspekte, die drei zentrale Benutzerfragen adressieren:

  - **Verfügbarkeit**   Können Benutzer auf den Dienst zugreifen?

  - **Latenz**   Welchen Eindruck haben Benutzer?

  - **Fehler**   Können Benutzer ihre Vorstellungen umsetzen?

Die Serverrollenkonsolidierung und andere Architekturänderungen in Exchange 2013 machen einen neuen Ansatz für die Überwachungsmethoden und das Integritätsmodell aus früheren Versionen von Exchange erforderlich. Die verwaltete Verfügbarkeit soll diesen Änderungen durch eine systemeigene Integritätsüberwachungs- und Wiederherstellungslösung Rechnung tragen. Sie geht von der Überwachung einzelner, separater Systemkomponenten über zu einer umfassenden Überwachung der Benutzerfreundlichkeit und schützt diese mithilfe wiederherstellungsorientierter Aktionen.

Die verwaltete Verfügbarkeit ist ein interner Prozess, der auf jedem Exchange 2013-Server ausgeführt wird. Dabei werden in jeder Sekunde Hunderte von Integritätsmetriken abgerufen. Wenn Fehler erkannt werden, können diese meist automatisch behoben werden. Es wird jedoch auch immer Probleme geben, die von der verwalteten Verfügbarkeit nicht direkt gelöst werden können. In diesen Fällen wird das Problem durch Ereignisprotokollierung an einen Administrator weitergeleitet.

Die verwaltete Verfügbarkeit wird in Form von zwei Diensten implementiert:

  - **Exchange-Integritätsdienst (MSExchangeHMHost.exe)**   Dies ist ein Controllerprozess, der zur Verwaltung von Arbeitsprozessen verwendet wird. Mit diesem Prozess wird der Arbeitsprozess nach Bedarf erstellt, ausgeführt, gestartet und angehalten. Dieser Prozess wird auch zur Wiederherstellung des Arbeitsprozesses verwendet, falls dieser ausfällt. So soll verhindert werden, dass der Arbeitsprozess zu einer einzelnen Fehlerquelle wird.

  - **Exchange-Integritäts-Manager-Arbeitsprozess (MSExchangeHMWorker.exe)**   Dies ist der Arbeitsprozess, der für die Ausführung der Laufzeittasks im Framework für die verwaltete Verfügbarkeit zuständig ist.

Bei der verwalteten Verfügbarkeit wird ein beständiger Speicher verwendet, um die zugehörigen Funktionen auszuführen:

  - In den XML-Dateien im Ordner "\\bin\\Monitoring\\config" werden Konfigurationseinstellungen für einige der Test- und Überwachungsarbeitsaufgaben gespeichert.

  - Active Directory wird zum Speichern globaler Außerkraftsetzungen verwendet.

  - Die Windows-Registrierung wird zum Speichern von Laufzeitdaten, wie z. B. Lesezeichen, und lokalen (serverspezifischen) Außerkraftsetzungen verwendet.

  - Die Windows-Crimson-Kanal-Ereignisprotokollinfrastruktur wird zum Speichern der Arbeitselementergebnisse verwendet.

  - Integritätspostfächer werden für Prüfaktivitäten verwendet. In jeder Postfachdatenbank auf dem Server werden mehrere Integritätspostfächer erstellt.

Wie in der folgenden Abbildung veranschaulicht, umfasst die verwaltete Verfügbarkeit drei zentrale asynchrone Komponenten, die permanent aktiv sind.

**Komponenten der verwalteten Verfügbarkeit**

![Verwaltete Verfügbarkeit in Exchange Server 2013](images/Dn482056.7a54dcb5-1e28-4bd4-87e6-0d496b4ab796(EXCHG.150).gif "Verwaltete Verfügbarkeit in Exchange Server 2013")

Die erste Komponente wird *Testmodul* genannt. Testmodule sind für die Durchführung von Messungen auf dem Server und für das Sammeln von Daten verantwortlich. Die Ergebnisse dieser Messungen fließen in die zweite Komponente ein, den *Monitor*. Der Monitor umfasst die vollständige, vom System verwendete Geschäftslogik zur Definition des fehlerfreien Zustands von gesammelten Daten. Ähnlich wie bei einem Modul zur Mustererkennung achtet der Monitor auf die zahlreichen verschiedenen Muster aller gesammelten Messungen. Anschließend wird entschieden, ob eine Komponente als fehlerfrei betrachtet wird. Schließlich gibt es noch *Antwortdienste*, die für Wiederherstellungs- und Weiterleitungsaktionen verantwortlich sind. Wenn eine Komponente fehlerhaft ist, besteht die erste Aktion in dem Versuch, diese Komponente wiederherzustellen. Dies kann mehrstufige Wiederherstellungsaktionen umfassen. Der erste Versuch kann z. B. darin bestehen, dass der Anwendungspool neu gestartet wird, während der zweite Versuch den Neustart des Diensts und der dritte Versuch den Neustart des Servers umfasst. Ein nachfolgender Versuch könnte darin bestehen, den Server offline zu nehmen, damit kein Datenverkehr mehr angenommen wird. Wenn die Wiederherstellungsaktionen keinen Erfolg zeigen, eskaliert das System das Problem per Ereignisprotokollbenachrichtigung an einen Benutzer.

Es existieren drei wesentliche Testtypen: wiederkehrende Tests, Benachrichtigungen und Prüfungen. Wiederkehrende Tests sind synthetische Transaktionen, die vom System zum Testen der umfassenden Benutzerfreundlichkeit ausgeführt werden. Prüfungen stellen die Infrastruktur dar, die die Leistungsdaten erfasst, einschließlich Benutzerdatenverkehr und der Gewichtung der erfassten Daten anhand von Schwellenwerten, die festgelegt werden, um Benutzerfehlerspitzen zu ermitteln. Dadurch kann die Prüfinfrastruktur ermitteln, wann bei den Benutzern Probleme auftreten. Mithilfe der Benachrichtigungslogik kann das System schließlich auf Grundlage eines kritischen Ereignisses Sofortmaßnahmen ergreifen, ohne auf die Ergebnisse der über den Test erfassten Daten warten zu müssen. Hierbei handelt es sich in der Regel um Ausnahmen oder Bedingungen, die ohne große Stichprobe ermittelt und erkannt werden können.

Wiederkehrende Tests werden alle paar Minuten durchgeführt und dienen zur Überprüfung einzelner Aspekte der Dienstintegrität. In diesen Tests kann über Exchange ActiveSync eine E-Mail an ein Überwachungspostfach gesendet werden, sie können zur Verbindung mit einem RPC-Endpunkt dienen, oder sie können die Konnektivität für Client-Zugriffe auf die Mailbox prüfen.

Alle Tests werden beim Start des Integritätsdienstes im Crimson-Kanal Microsoft.Exchange.ActiveMonitoring\\ProbeDefinition definiert. Jede Testdefinition hat mehrere Eigenschaften. Die relevantesten davon sind folgende:

  - **Name** Der Name des Tests, der mit einer *SampleMask* des Testmonitors beginnt.

  - **TypeName** Der Codeobjekttyp des Tests, der die Testlogik enthält.

  - **ServiceName** Der Name des Integritätssatzes, der den Test enthält.

  - **TargetResource** Das Objekt, das durch den Test überprüft wird. Dieses wird an den Namen des Tests angehängt, wenn dieser ausgeführt wird, und wird dann zu einem Bestandteil des *ResultName*.

  - **RecurrenceIntervalSeconds** Häufigkeit, in der der Test ausgeführt wird.

  - **TimeoutSeconds** Zeit, die der Test wartet, bevor er als fehlgeschlagen gilt.

Es gibt Hunderte von wiederkehrenden Tests. Viele dieser Tests sind datenbankbezogen. Wenn also die Anzahl der Datenbanken sich erhöht, gibt es auch immer mehr Tests, Die meisten dieser Tests werden im Code definiert und sind deshalb nicht direkt erkennbar.

Ein wiederkehrender Test wird auf folgender Grundlage durchgeführt: Er wird alle *RecurrenceIntervalSeconds* neu gestartet und prüft einige Aspekte der Dienstintegrität. Wenn die betreffende Komponente intakt ist, ist der Test bestanden, und es wird ein Informationsereignis mit dem *ResultType* 3 an den Kanal Microsoft.Exchange.ActiveMonitoring\\ProbeResult gesendet. Wenn die Prüfung fehlschlägt oder eine Zeitüberschreitung auftritt, wird ein Fehlerereignis an denselben Kanal gesendet. Der *ResultType* 4 bedeutet, dass der Test fehlgeschlagen ist, und das *ResultType* 1 zeigt eine Zeitüberschreitung an. Viele Tests werden nach einer Zeitüberschreitung so oft erneut ausgeführt, wie in der Eigenschaft *MaxRetryAttempts* definiert ist.


> [!NOTE]
> <STRONG>Hinweis</STRONG> Der Crimson-Kanal ProbeResult kann mit Hunderten von Tests, die alle paar Minuten laufen, sowie mit der Protokollierung der entsprechenden Ereignisse sehr beschäftigt sein, so dass sich eine deutliche Auswirkung auf die Leistung Ihres Exchange-Servers ergeben kann, wenn Sie in einer Produktumgebung umfassende Abfragen der Ereignisprotokolle durchführen.



Benachrichtigungen sind Tests, die nicht durch das Framework des Integritätsdiensts, sondern durch andere Dienste auf dem Server durchgeführt werden. Diese Dienste führen ihre eigene Überwachung durch und stellen ihre Daten im Framework für verwaltete Verfügbarkeit bereit, indem Sie die Testergebnisse direkt in dieses schreiben. Sie können diese Tests im Kanal ProbeDefinition nicht sehen, da dieser Kanal nur die Tests beschreibt, die vom Framework für verwaltete Verfügbarkeit ausgeführt werden. Der Monitor ServerOneCopyMonitor wird z.B. nur durch Testergebnisse ausgelöst, die vom Dienst MSExchangeDAGMgmt geschrieben werden. Dieser Dienst führt seine eigene Überwachung durch, ermittelt, ob ein Problem vorliegt, und protokolliert das Testergebnis. Die meisten Benachrichtigungstests verfügen über die Kapazität, sowohl rote Ereignisse, die auf eine Fehlerhaftigkeit des Monitors hinweisen, als auch grüne Ereignisse anzuzeigen, mit denen der betreffende Monitorfehler behoben wird.

Prüfungen sind Tests, bei denen Ereignisse nur protokolliert werden, wenn der Leistungsindikator einen bestimmten Schwellenwert über- oder unterschreitet. Diese sind ein wirklich spezieller Fall von Benachrichtigungstest, da ein Dienst die Leistungsindikatoren auf dem Server überwacht und Ereignisse in den Kanal ProbeResult protokolliert, wenn der konfigurierte Schwellenwert erreicht wird.

Um den Indikator und den Schwellenwert zu finden, der als fehlerhaft betrachtet wird, können Sie für diese Prüfung auf den Monitor schauen. Monitoren der Art *Microsoft.Office.Datacenter.ActiveMonitoring.OverallConsecutiveSampleValueAboveThresholdMonitor* oder *Microsoft.Office.Datacenter.ActiveMonitoring.OverallConsecutiveSampleValueBelowThresholdMonitor* bedeuten, dass der angezeigte Test ein Prüfungstest ist

Monitore fragen die von Tests erfassten Daten ab, um zu ermitteln, ob auf Basis eines vordefinierten Regelsatzes Maßnahmen ergriffen werden müssen. In Abhängigkeit von der Regel oder der Art des Problems kann ein Monitor entweder einen Responder initiieren oder das Problem über einen Ereignisprotokolleintrag an eine Person weiterleiten. Monitore legen außerdem fest, wie lange ein Responder nach einem Fehler ausgeführt und welcher Workflow der Wiederherstellungsmaßnahme verwendet wird. Monitore können verschiedene Zustände aufweisen. Aus Sicht des Systemstatus verfügen Monitore über zwei Zustände:

  - **Fehlerfrei**   Der Monitor arbeitet ordnungsgemäß, und alle erfassten Metriken befinden sich innerhalb der normalen Betriebsparameter

  - **Fehlerhaft**   Der Monitor ist nicht fehlerfrei und hat entweder die Wiederherstellung über einen Responder eingeleitet oder einen Administrator benachrichtigt (Eskalation).

Aus Administratorsicht verfügen Monitore über weitere Zustände, die in der Shell angezeigt werden:

  - **Beeinträchtigt**   Wenn sich ein Monitor für 0 bis 60 Sekunden im Zustand "Fehlerhaft" befindet, wird er als "Beeinträchtigt" betrachtet. Wenn sich der Monitor für mehr als 60 Sekunden im Zustand "Fehlerhaft" befindet, wird er als "Fehlerhaft" betrachtet.

  - **Deaktiviert**   Der Monitor wurde explizit von einem Administrator deaktiviert.

  - **Nicht verfügbar**   Der Microsoft Exchange-Integritätsdienst fragt den Zustand der einzelnen Monitore regelmäßig ab. Wenn er auf die Abfrage keine Antwort erhält, ändert sich der Zustand des Monitors in "Nicht verfügbar".

  - **Reparatur**   Dieser Status wird von einem Administrator festgelegt, um dem System anzuzeigen, dass Reparaturmaßnahmen von einer Person ausgeführt werden. Auf diese Weise können das System und die Person sonstige Fehler erkennen, die möglicherweise während der Ausführung der Reparaturmaßnahme auftreten (z. B. das erneute Seeding für eine Datenbankkopie).

Für jeden Monitor ist eine *SampleMask*-Eigenschaft definiert. Während seiner Ausführung sucht der Monitor nach Ereignissen im Kanal ProbeResult mit einem *ResultName*, der der *SampleMask* des Monitors entspricht. Diese Ereignisse können aus wiederkehrenden Tests, Benachrichtigungen oder Prüfungen stammen. Wenn die Schwellenwerte des Monitors erreicht werden, wird Fehlerhaftigkeit festgestellt. Aus der Perspektive des Monitors sind die Testtypen gleich, da sie alle Protokolle in den Kanal ProbeResult schreiben.

Bitte beachten Sie, dass das Fehlschlagen nur eines Tests nicht notwendigerweise bedeutet, dass mit dem Server etwas nicht in Ordnung ist. Die Monitore sind dafür entwickelt worden, echte Probleme, die dringenden behoben werden müssen, korrekt zu identifizieren. Aus diesem Grund haben viele Monitore Schwellenwerte für mehrere Testfehlschläge, bevor Fehlerhaftigkeit festgestellt wird. Aber dennoch können viele dieser Probleme automatisch durch Antwortsender behoben werden, sodass der Crimson-Kanal Microsoft.Exchange.ManagedAvailability\\Monitoring der beste Platz für die Suche nach Problemen ist, die eine manuelle Behebung erfordern. Dazu gehört auch der letzte Testfehler.

Wie der Name besagt, führen Responder eine bestimmte Art von Reaktion auf eine von einem Monitor generierte Warnung aus. Responder nehmen unterschiedliche Wiederherstellungsaktionen vor, vom Wiederherstellen eines Anwendungspools bis hin zum Neustarten eines Servers. Es gibt verschiedene Arten von Respondern:

  - **Neustart-Responder** beendet einen Dienst und startet ihn neu

  - **Anwendungspool-Neustart-Responder** beendet einen Anwendungspool in den Internetinformationsdiensten (IIS) und startet ihn neu

  - **Failover-Responder** initiiert ein Datenbank- oder Serverfailover

  - **Fehlerprüfungs-Responder** initiiert eine Fehlerprüfung des Servers und verursacht dadurch einen Neustart des Servers

  - **Offline-Responder** setzt ein Protokoll auf einem Server außer Betrieb (weist Clientanforderungen zurück)

  - **Online-Responder** versetzt ein Protokoll auf einem Server wieder in den Produktionsmodus (akzeptiert Clientanforderungen)

  - **Eskalations-Responder** eskaliert das Problem durch Ereignisprotokollierung an einen Administrator

Zusätzlich zu den aufgeführten Respondern verfügen einige Komponenten über eigene, spezialisierte Responder.

Alle Responder umfassen ein Einschränkungsverhalten, das einen integrierten Sequenzierungsmechanismus für Responderaktionen bereitstellt. Durch dieses Einschränkungsverhalten soll verhindert werden, dass das System aufgrund von Wiederherstellungsaktionen des Responders beschädigt oder beeinträchtigt wird. Alle Responder werden in irgendeiner Weise eingeschränkt. Wenn eine Einschränkung auftritt, kann die Wiederherstellungsaktion des Responders je nach Aktion entweder übersprungen oder verzögert werden. Beispielsweise wird bei einer Einschränkung des Fehlerprüfungs-Responders die Aktion übersprungen und nicht verzögert.

## Integritätssätze

Bezüglich der Berichterstellung umfasst die verwaltete Verfügbarkeit zwei Ansichten der Integrität: eine interne und eine externe. Für die interne Ansicht werden *Integritätssätze* verwendet. Jede Komponente in Exchange 2013 (z. B. Outlook Web App, Exchange ActiveSync, Informationsspeicherdienst, Inhaltsindizierung, Transportdienste usw.) wird mithilfe von Tests, Monitoren und Respondern durch die verwaltete Verfügbarkeit überwacht. Eine Gruppe von Tests, Monitoren und Respondern für eine bestimmte Komponente wird als *Integritätssatz* bezeichnet. Ein Integritätssatz besteht aus einer Gruppe von Tests, Monitoren und Respondern, die bestimmen, ob die Komponente fehlerfrei arbeitet. Der aktuelle Status eines Integritätssatzes (d. h. fehlerfrei oder fehlerhaft) wird anhand des Status der Monitore des Integritätssatzes bestimmt. Sind alle Monitore eines Integritätssatzes fehlerfrei, befindet sich der Integritätssatz in einem fehlerfreien Zustand. Ist einer der Monitore nicht im fehlerfreien Zustand, wird der Zustand des Integritätssatzes durch den am meisten fehlerhaften Monitor bestimmt.

Detaillierte Anweisungen zum Anzeigen des Status der Serverintegrität oder des Integritätssatzes finden Sie unter [Verwalten von Integritätssätzen und Serverintegrität](manage-health-sets-and-server-health-exchange-2013-help.md).

## Integritätsgruppen

Die externe Ansicht der verwalteten Verfügbarkeit besteht aus *Integritätsgruppen*. Integritätsgruppen sind für System Center Operations Manager 2007 R2 und System Center Operations Manager 2012 verfügbar.

Es gibt vier primäre Integritätsgruppen:

  - **Kontaktpunkte für Kunden** Komponenten, die sich auf Echtzeit-Benutzerinteraktionen auswirken, wie Protokolle oder der Informationsspeicher

  - **Dienstkomponenten** Komponenten ohne direkte Echtzeit-Benutzerinteraktionen, wie z. B. der Microsoft Exchange-Postfachreplikationsdienst oder der Offlineadressbuch-Generierungsprozess (OABGen)

  - **Serverkomponenten** Die physischen Ressourcen des Servers, wie Speicherplatz, Arbeitsspeicher und Netzwerk

  - **Abhängigkeitsverfügbarkeit** Die Fähigkeit des Servers, auf erforderliche Abhängigkeiten, wie z. B. Active Directory, DNS usw., zuzugreifen

Wenn das Exchange Management Pack installiert ist, fungiert System Center Operations Manager (SCOM) als einen Gesundheitsportal zum Anzeigen von Informationen im Zusammenhang mit der Exchange-Umgebung. Das Dashboard SCOM umfasst drei Ansichten von Exchange Serverintegrität:

  - **Aktive Warnungen** Eskalations-Responder schreiben Ereignisse in das Windows-Ereignisprotokoll, die vom Monitor in SCOM verwendet werden. Diese werden als Warnungen in der Ansicht "Aktive Warnungen" angezeigt.

  - **Organisationsintegrität** In dieser Ansicht wird eine Rollupzusammenfassung des Gesamtzustands der Exchange-Organisationsintegrität angezeigt. Diese Rollups enthalten Anzeigen der Integrität für einzelne Datenbank-Verfügbarkeitsgruppen und für bestimmte Active Directory-Standorte.

  - **Serverintegrität** In dieser Ansicht werden verwandte Integritätssätze zu Integritätsgruppen kombiniert und zusammengefasst.

## Außerkraftsetzungen

Außerkraftsetzungen ermöglichen es einem Administrator, einige Aspekte der Tests, Monitore und Responder für die verwaltete Verfügbarkeit zu konfigurieren. Mit Außerkraftsetzungen können einige der von der verwalteten Verfügbarkeit verwendeten Schwellenwerte angepasst werden. Zudem können hiermit Notfallaktionen für unerwartete Ereignisse aktiviert werden, die andere Konfigurationseinstellungen als die Standardvorgaben erfordern.

Außerkraftsetzungen können auf einem einzelnen Server erstellt und angewendet werden (dies wird als *Serveraußerkraftsetzung* bezeichnet), oder sie können auf eine Gruppe von Servern angewendet werden (dies wird als *globale Außerkraftsetzung* bezeichnet). Konfigurationsdaten für Serveraußerkraftsetzungen werden in der Windows-Registrierung auf dem Server gespeichert, auf dem die Außerkraftsetzung angewendet wird. Konfigurationsdaten für globale Außerkraftsetzungen werden in Active Directory gespeichert.

Außerkraftsetzungen können für eine unendliche oder für eine beschränkte Dauer konfiguriert werden. Zudem können globale Außerkraftsetzungen für die Anwendung auf allen Servern oder nur auf Servern mit einer bestimmten Version von Exchange konfiguriert werden.

Wenn Sie eine Außerkraftsetzung konfigurieren, wird sie nicht sofort wirksam. Der Microsoft Exchange-Integritätsdienst nimmt alle 10 Minuten eine Prüfung auf aktualisierte Konfigurationsdaten vor. Darüber hinaus sind globale Außerkraftsetzungen von der Replikationslatenz von Active Directory abhängig.

Detaillierte Anweisungen zum Anzeigen oder Konfigurieren von globalen oder serverspezifischen Außerkraftsetzungen finden Sie unter [Konfigurieren von Überschreibungen für die verwaltete Verfügbarkeit](configure-managed-availability-overrides-exchange-2013-help.md).

## Verwaltungsaufgaben und Verwaltungs-Cmdlets

In der Regel haben Administratoren drei wesentliche Betriebsaufgaben bezüglich der verwalteten Verfügbarkeit auszuführen:

  - Extrahieren oder Anzeigen der Systemintegrität

  - Anzeigen von Integritätssätzen und Details zu Tests, Monitoren und Respondern

  - Verwalten von Außerkraftsetzungen

Die beiden wichtigsten Verwaltungstools für die verwaltete Verfügbarkeit sind das Windows-Ereignisprotokoll und die Shell. Die verwaltete Verfügbarkeit protokolliert umfangreiche Informationen in den Exchange-Crimson-Kanal-Ereignisprotokollen "ActiveMonitoring" und "ManagedAvailability". Beispiele dafür sind:

  - Test-, Monitor- und Responderdefinitionen, die in den jeweiligen Ereignisprotokollen "\*Definition" aufgezeichnet werden.

  - Test-, Monitor- und Responderergebnisse, die in den jeweiligen Ereignisprotokollen "\*Results" aufgezeichnet werden.

  - Details zu Responder-Wiederherstellungsaktionen, z. B. wann die Wiederherstellungsaktion gestartet und als abgeschlossen betrachtet wird (erfolgreich oder nicht), die im Ereignisprotokoll "RecoveryActionResults" aufgezeichnet werden.

Für die verwaltete Verfügbarkeit stehen 12 Cmdlets zur Verfügung, die in der folgenden Tabelle beschrieben werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218703(v=exchg.150)">Get-ServerHealth</a></p></td>
<td><p>Dient zum Abruf unverarbeiteter Serverintegritätsinformationen, z. B. von Integritätssätzen und deren aktuellem Zustand (fehlerfrei oder fehlerhaft), Integritätssatzmonitoren, Serverkomponenten, Zielressourcen für Tests, Zeitstempeln im Zusammenhang mit Start- bzw. Endzeiten von Tests und Monitoren sowie Zustandsübergangszeiten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218724(v=exchg.150)">Get-HealthReport</a></p></td>
<td><p>Dient zum Abruf einer zusammenfassenden Integritätsansicht mit Integritätssätzen und deren aktuellem Status.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218668(v=exchg.150)">Get-MonitoringItemIdentity</a></p></td>
<td><p>Dient zum Anzeigen der Tests, Monitore und Responder für einen bestimmten Integritätssatz.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218642(v=exchg.150)">Get-MonitoringItemHelp</a></p></td>
<td><p>Dient zum Anzeigen von Beschreibungen einiger Eigenschaften von Tests, Monitoren und Respondern.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218628(v=exchg.150)">Add-ServerMonitoringOverride</a></p></td>
<td><p>Dient zum Erstellen einer lokalen, serverspezifischen Außerkraftsetzung eines Tests, Monitors oder Responders.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218664(v=exchg.150)">Get-ServerMonitoringOverride</a></p></td>
<td><p>Dient zum Anzeigen einer Liste lokaler Außerkraftsetzungen auf dem angegebenen Server.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/dn482411(v=exchg.150)">Remove-ServerMonitoringOverride</a></p></td>
<td><p>Dient zum Entfernen einer lokalen Außerkraftsetzung von einem bestimmten Server.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218683(v=exchg.150)">Add-GlobalMonitoringOverride</a></p></td>
<td><p>Dient zum Erstellen einer globalen Außerkraftsetzung für eine Gruppe von Servern.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218627(v=exchg.150)">Get-GlobalMonitoringOverride</a></p></td>
<td><p>Dient zum Anzeigen einer Liste globaler Außerkraftsetzungen in der Organisation.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218675(v=exchg.150)">Remove-GlobalMonitoringOverride</a></p></td>
<td><p>Dient zum Entfernen einer globalen Außerkraftsetzung.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218699(v=exchg.150)">Set-ServerComponentState</a></p></td>
<td><p>Dient zum Konfigurieren des Status einer oder mehrerer Komponenten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/de-de/library/jj218713(v=exchg.150)">Get-ServerComponentState</a></p></td>
<td><p>Dient zum Anzeigen des Status einer oder mehrerer Komponenten.</p></td>
</tr>
</tbody>
</table>

