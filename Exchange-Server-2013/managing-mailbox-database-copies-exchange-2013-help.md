---
title: 'Verwalten von Postfachdatenbankkopien: Exchange 2013 Help'
TOCTitle: Verwalten von Postfachdatenbankkopien
ms:assetid: 28cedf1d-365a-4e36-b2ba-6bf81af8684f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335158(v=EXCHG.150)
ms:contentKeyID: 50475380
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Postfachdatenbankkopien

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-08-26_

Nachdem eine Database Availability Group (DAG) erstellt, konfiguriert und mit den Mitgliedern eines Postfachservers gefüllt wurde, können Sie die Exchange-Verwaltungskonsole oder die Exchange-Verwaltungsshell verwenden, um auf flexible und präzise Weise Kopien einer Postfachdatenbank hinzuzufügen.

## Verwalten von Datenbankkopien

Nachdem mehrere Kopien einer Datenbank erstellt wurden, können Sie die Exchange-Verwaltungskonsole oder die Shell verwenden, um die Integrität und den Status der einzelnen Kopien zu überwachen und andere Verwaltungsaufgaben im Zusammenhang mit Datenbankkopien auszuführen. Einige der Verwaltungsaufgaben, die Sie möglicherweise ausführen müssen, umfassen das Anhalten oder Fortsetzen einer Datenbankkopie, das Seeding einer Datenbankkopie, das Überwachen von Datenbankkopien, das Konfigurieren der Einstellungen von Datenbankkopien und das Entfernen einer Datenbankkopie.

## Anhalten und Fortsetzen von Datenbankkopien

Es gibt verschiedene Gründe, z. B. das Ausführen geplanter Wartungsmaßnahmen, die das Anhalten und Fortsetzen der fortlaufenden Replikationsaktivität für eine Datenbankkopie erforderlich machen können. Außerdem erfordern einige Verwaltungsaufgaben, z. B. das Seeding, dass Sie zuerst eine Datenbankkopie anhalten. Es wird empfohlen, dass alle Replikationsaktivitäten angehalten werden, wenn der Pfad der Datenbank oder ihrer Protokolldateien geändert wird. Sie können die Aktivität einer Datenbankkopie mithilfe der Exchange-Verwaltungskonsole oder über die Cmdlets **Suspend-MailboxDatabaseCopy** und **Resume-MailboxDatabaseCopy** in der Shell anhalten und fortsetzen. Genaue Anweisungen zum Anhalten oder Fortsetzen der fortlaufenden Replikationsaktivität für eine Datenbankkopie finden Sie unter [Anhalten oder Fortsetzen der Kopie einer Postfachdatenbank](suspend-or-resume-a-mailbox-database-copy-exchange-2013-help.md).

## Seeding von Datenbankkopien

Das *Seeding*, das auch als *Aktualisieren* bezeichnet wird, ist der Prozess, bei dem eine Datenbank (entweder eine leere Datenbank oder eine Kopie einer Produktionsdatenbank) am Speicherort der Zielkopie auf einem anderen Postfachserver in derselben DAG wie die aktive Datenbank hinzugefügt wird. Dies wird die Basisdatenbank für die von diesem Server verwaltete Kopie.

Abhängig von der Situation kann das Seeding ein automatischer Prozess oder ein vom Administrator eingeleiteter, manueller Prozess sein. Wenn eine Datenbankkopie hinzugefügt wird, erfolgt automatisch das Seeding der Kopie, sofern der Zielserver und sein Speicher ordnungsgemäß konfiguriert sind. Wenn Sie das Seeding einer Datenbankkopie manuell ausführen und kein automatisches Seeding beim Erstellen der Kopie möchten, können Sie den Parameter *SeedingPostponed* beim Ausführen des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) verwenden.

Für Datenbankkopien ist nach dem anfänglichen Seeding selten ein erneutes Seeding erforderlich. Wenn jedoch ein erneutes Seeding erforderlich ist oder Sie das Seeding für eine Datenbankkopie manuell ausführen möchten, anstatt dies automatisch vom System übernehmen zu lassen, dann können diese Aufgaben mithilfe des Assistenten zum Aktualisieren von Postfachdatenbankkopien in der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) in der Shell ausgeführt werden. Vor dem Seeding einer Datenbankkopie müssen Sie zunächst die Postfachdatenbankkopie anhalten. Ausführliche Anweisungen zum Seeding einer Datenbankkopie finden Sie unter [Aktualisieren einer Postfachdatenbankkopie](update-a-mailbox-database-copy-exchange-2013-help.md).

Nachdem das manuelle Seeding abgeschlossen ist, wird die Replikation für die Postfachdatenbankkopie, für die das Seeding durchgeführt wurde, automatisch fortgesetzt. Wenn die Replikation nicht automatisch fortgesetzt werden soll, können Sie den Parameter *ManualResume* beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) verwenden.

## Auswählen der Seedingziele

Wenn Sie einen Seedingvorgang ausführen, können Sie das Seeding für die Postfachdatenbankkopie, für den Inhaltsindexkatalog der Postfachdatenbankkopie oder sowohl für die Datenbankkopie als auch für die Inhaltsindex-Katalogkopie auswählen.

Das Standardverhalten des Assistenten zum Aktualisieren von Postfachdatenbankkopien und des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) ist es, das Seeding sowohl für die Postfachdatenbankkopie als auch für die Inhaltsindex-Katalogkopie auszuführen. Damit das Seeding nur für die Postfachdatenbankkopie und nicht für den Inhaltsindexkatalog ausgeführt wird, verwenden Sie den Parameter *DatabaseOnly* beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)). Damit das Seeding nur für den Inhaltsindexkatalog ausgeführt wird, verwenden Sie den Parameter *CatalogOnly* beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)).

## Auswählen der Seedingquelle

Jede fehlerfreie Datenbankkopie kann als Seedingquelle für eine zusätzliche Kopie dieser Datenbank verwendet werden. Dies ist v. a. hilfreich, wenn Sie eine DAG besitzen, die sich über mehrere physische Standorte erstreckt. Stellen Sie sich z. B. eine Bereitstellung einer DAG mit vier Mitgliedern vor, bei der sich zwei Mitglieder (MBX1 und MBX2) in Portland, Oregon, befinden, während sich die anderen beiden Mitglieder (MBX3 und MBX4) in New York, New York, befinden. Auf MBX1 ist eine Postfachdatenbank mit der Bezeichnung DB1 aktiv, und es befinden sich passive Kopien von DB1 auf MBX2 und MBX3. Beim Hinzufügen einer Kopie von DB1 zu MBX4 können Sie die Kopie auf MBX3 als Quelle für das Seeding verwenden. Dabei wird das Seeding über die WAN-Verbindung (Wide Area Network) zwischen Portland und New York vermieden.

Sie würden wie folgt vorgehen, wenn Sie beim Hinzufügen einer neuen Datenbankkopie eine bestimmte Kopie als Quelle für das Seeding verwenden:

  - Verwenden Sie den Parameter *SeedingPostponed* beim Ausführen des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)), um die Datenbankkopie hinzuzufügen. Wenn der Parameter *SeedingPostponed* nicht verwendet wird, erfolgt das explizite Seeding der Datenbankkopie mithilfe der aktiven Kopie der Datenbank als Quelle.

  - Sie können den Quellserver, der im Assistenten zum Aktualisieren von Postfachdatenbankkopien verwendet werden soll, in der Exchange-Verwaltungskonsole angeben oder beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) den Parameter *SourceServer* verwenden, um den gewünschten Quellserver für das Seeding anzugeben. Im vorherigen Beispiel würden Sie "MBX3" als Quellserver angeben. Wenn der Parameter *SourceServer* nicht verwendet wird, erfolgt das explizite Seeding der Datenbankkopie basierend auf der aktiven Kopie der Datenbank.

## Seeding und Netzwerke

Zusätzlich zum Auswählen eines bestimmten Quellservers für das Seeding einer Postfachdatenbankkopie können Sie über die Shell auch angeben, welche DAG-Netzwerke zu verwenden sind. Außerdem können Sie die Einstellungen für die Komprimierung und Verschlüsselung des DAG-Netzwerks während des Seedingvorgangs optional außer Kraft setzen.


> [!NOTE]
> Das Seeding des Inhaltsindexkatalogs ist nur über ein MAPI-Netzwerk möglich. Das gleiche gilt auch bei Verwendung des <CODE>-Network</CODE>-Parameters im Update-MailboxDatabaseCopy-Cmdlet.



Wenn Sie die für das Seeding zu verwendenden Netzwerke angeben, verwenden Sie den Parameter *Network* beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)), und geben Sie die zu verwendenden DAG-Netzwerke an. Wenn Sie den Parameter *Network* nicht verwenden, verwendet das System das folgende Standardverhalten zum Ausführen eines Netzwerks, das für den Seedingvorgang verwendet wird:

  - Wenn sich Quell- und Zielserver in demselben Subnetz befinden und ein Replikationsnetzwerk konfiguriert wurde, das dieses Subnetz einbezieht, dann wird das Replikationsnetzwerk verwendet.

  - Wenn sich Quell- und Zielserver in unterschiedlichen Subnetzen befinden, dann wird das Clientnetzwerk (MAPI) für das Seeding verwendet, auch wenn ein Replikationsnetzwerk konfiguriert wurde, das diese Subnetze einbezieht.

  - Wenn sich Quell- und Zielserver in verschiedenen Datencentern befinden, wird das Clientnetzwerk (MAPI) für das Seeding verwendet.

Auf der Ebene der DAG sind DAG-Netzwerke für die Verschlüsselung und Komprimierung konfiguriert. Die Standardeinstellungen geben an, dass die Verschlüsselung und Komprimierung nur für die Kommunikation in unterschiedlichen Subnetzen verwendet wird. Wenn sich Quelle und Ziel in unterschiedlichen Subnetzen befinden und die DAG mit den Standardwerten für *NetworkCompression* und *NetworkEncryption* konfiguriert ist, dann können Sie diese Werte mithilfe der Parameter *NetworkCompressionOverride* und *NetworkEncryptionOverride* beim Ausführen des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) entsprechend außer Kraft setzen.

## Seedingprozess

Wenn Sie einen Seedingprozess mithilfe des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) oder [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) starten, werden die folgenden Tasks ausgeführt:

1.  Es werden Datenbankeigenschaften aus Active Directory gelesen, um die angegebene Datenbank und die Server zu überprüfen. Außerdem wird überprüft, dass die Quell- und Zielserver Exchange 2013 ausführen, dass beide Mitglieder derselben DAG sind und dass die angegebene Datenbank keine Wiederherstellungsdatenbank ist. Die Dateipfade der Datenbank werden ebenfalls gelesen.

2.  Vom Microsoft Exchange-Replikationsdienst auf dem Zielserver werden Vorbereitungen für Prüfungen zum erneuten Seeding getroffen.

3.  Der Microsoft Exchange-Replikationsdienst auf dem Zielserver prüft das Vorhandensein von Datenbank- und Transaktionsprotokolldateien in den Dateiverzeichnissen, die von den Active Directory-Prüfungen in Schritt 1 gelesen werden.

4.  Der Microsoft Exchange-Replikationsdienst gibt die Statusinformationen vom Zielserver an die Verwaltungsschnittstelle zurück, von der aus das Cmdlet ausgeführt wurde.

5.  Wenn alle einleitenden Prüfungen bestanden wurden, werden Sie zur Bestätigung des Vorgangs aufgefordert, bevor dieser fortgesetzt wird. Wenn Sie den Vorgang bestätigen, wird der Prozess fortgesetzt. Wenn während der einleitenden Prüfungen ein Fehler auftritt, wird der Fehler gemeldet, und der Vorgang schlägt fehl.

6.  Der Seedingvorgang wird vom Microsoft Exchange-Replikationsdienst auf dem Zielserver gestartet.

7.  Der Microsoft Exchange-Replikationsdienst hält die Datenbankreplikation für die aktive Datenbankkopie an.

8.  Die Statusinformationen für die Datenbank werden vom Microsoft Exchange-Replikationsdienst aktualisiert, um den Status für das Seeding anzugeben.

9.  Wenn der Zielserver nicht bereits über die Verzeichnisse für die Zieldatenbank und die Protokolldateien verfügt, dann werden diese erstellt.

10. Vom Microsoft Exchange-Replikationsdienst auf dem Zielserver wird eine Anforderung für das Seeding der Datenbank an den Microsoft Exchange-Replikationsdienst auf dem Quellserver mithilfe von TCP übergeben. Diese Anforderung und die nachfolgende Kommunikation für das Seeding der Datenbank erfolgen in einem DAG-Netzwerk, das als Replikationsnetzwerk konfiguriert wurde.

11. Der Microsoft Exchange-Replikationsdienst auf dem Quellserver startet eine ESE-Streamingsicherung (Extensible Storage Engine) über die Schnittstelle des Microsoft Exchange-Informationsspeicherdiensts.

12. Der Microsoft Exchange-Informationsspeicherdienst sendet die Datenbankdaten als Stream an den Microsoft Exchange-Replikationsdienst.

13. Die Datenbankdaten werden vom Microsoft Exchange-Replikationsdienst des Quellservers zum Microsoft Exchange-Replikationsdienst das Zielservers verschoben.

14. Der Microsoft Exchange-Replikationsdienst auf dem Zielserver schreibt die Datenbankkopie in ein temporäres Verzeichnis, das sich im Hauptdatenbankverzeichnis *temp-seeding* befindet.

15. Die Streamingsicherung auf dem Quellserver endet, wenn das Ende der Datenbank erreicht wurde.

16. Der Schreibvorgang auf dem Zielserver wird abgeschlossen, und die Datenbank wird aus dem Verzeichnis "temp-seeding" an den endgültigen Speicherort verschoben. Das Verzeichnis "temp-seeding" wird gelöscht.

17. Auf dem Zielserver leitet der Microsoft Exchange-Replikationsdienst eine Anforderung mittels Proxyweiterleitung an den Microsoft Exchange-Suchdienst weiter, um den Inhaltsindexkatalog für die Datenbankkopie einzubinden, sofern dieser vorhanden ist. Wenn veraltete Katalogdateien einer früheren Instanz der Datenbankkopie vorhanden sind, schlägt der Einbindungsvorgang fehl, sodass der Katalog vom Quellserver repliziert werden muss. Wenn der Katalog nicht in einer neuen Instanz der Datenbankkopie auf dem Zielserver vorhanden ist, ist entsprechend eine Kopie des Katalogs erforderlich. Der Microsoft Exchange-Replikationsdienst weist den Microsoft Exchange-Suchdienst an, die Indizierung für die Datenbankkopie anzuhalten, während ein neuer Katalog von der Quelle kopiert wird.

18. Der Microsoft Exchange-Replikationsdienst auf dem Zielserver sendet eine Anforderung zum Seeding des Katalogs an den Microsoft Exchange-Replikationsdienst auf dem Quellserver.

19. Auf dem Quellserver fordert der Microsoft Exchange-Replikationsdienst die Verzeichnisinformationen vom Microsoft Exchange-Suchdienst sowie das Anhalten der Indizierung an.

20. Der Microsoft Exchange-Suchdienst auf dem Quellserver gibt die Verzeichnisinformationen des Suchkatalogs an den Microsoft Exchange-Replikationsdienst zurück.

21. Der Microsoft Exchange-Replikationsdienst auf dem Quellserver liest die Katalogdateien aus dem Verzeichnis.

22. Der Microsoft Exchange-Replikationsdienst auf dem Quellserver verschiebt die Katalogdaten mithilfe einer Verbindung über das Replikationsnetzwerk zum Microsoft Exchange-Replikationsdienst auf dem Zielserver. Nachdem der Lesevorgang abgeschlossen ist, sendet der Microsoft Exchange-Replikationsdienst eine Anforderung an den Microsoft Exchange-Suchdienst, um die Indizierung der Quelldatenbank fortzusetzen.

23. Wenn sich im Verzeichnis auf dem Zielserver vorhandene Katalogdateien befinden, werden diesem vom Microsoft Exchange-Replikationsdienst auf dem Zielserver gelöscht.

24. Der Microsoft Exchange-Replikationsdienst auf dem Zielserver schreibt die Katalogdateien in das temporäre Verzeichnis *CiSeed.Temp*, bis die Daten vollständig übertragen wurden.

25. Der Microsoft Exchange-Replikationsdienst verschiebt die vollständigen Katalogdaten an ihren endgültigen Speicherort.

26. Der Microsoft Exchange-Replikationsdienst auf dem Zielserver fährt mit der Suchindizierung für die Zieldatenbank fort.

27. Der Microsoft Exchange-Replikationsdienst auf dem Zielserver gibt einen Fertigstellungsstatus zurück.

28. Das letzte Ergebnis des Vorgangs wird an die Verwaltungsschnittstelle übergeben, von der aus das Cmdlet aufgerufen wurde.

## Konfigurieren von Datenbankkopien

Nachdem eine Datenbankkopie erstellt wurde, können Sie ihre Konfigurationseinstellungen bei Bedarf anzeigen und ändern. Sie können einige Konfigurationsinformationen für eine Datenbankkopie in der Exchange-Verwaltungskonsole auf der Seite **Eigenschaften** anzeigen. Sie können auch die Cmdlets [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)) und [Set-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298104\(v=exchg.150\)) in der Shell verwenden und damit die Einstellungen der Datenbankkopie anzeigen und konfigurieren, z. B. die Wiedergabeverzögerung, die Abschneideverzögerung und die Aktivierungseinstellungsreihenfolge. Genaue Anweisungen zum Anzeigen und Konfigurieren der Einstellungen von Datenbankkopien finden Sie unter [Konfigurieren der Eigenschaften von Postfachdatenbankkopien](configure-mailbox-database-copy-properties-exchange-2013-help.md).

## Verwenden von Optionen für die Wiedergabe- und Abschneideverzögerung

Postfachdatenbankkopien unterstützen die Verwendung von *Wiedergabeverzögerungen* und *Abschneideverzögerungen*, die jeweils innerhalb von Minuten konfiguriert werden können. Durch das Festlegen einer Wiedergabeverzögerung können Sie bei einer Datenbankkopie zu einem bestimmten Zeitpunkt zurückkehren. Durch das Festlegen einer Abschneideverzögerung können Sie anhand der Protokolle für eine passive Datenbankkopie die verlorenen Protokolldateien für die aktive Datenbankkopie wiederherstellen. Da beide Features zu einer temporären Ansammlung an Protokolldateien führen, beeinflussen beide den Speicherentwurf.

## Wiedergabeverzögerung

Die Wiedergabeverzögerung ist eine Eigenschaft einer Postfachdatenbankkopie, die die Dauer (in Minuten) angibt, die die Protokollwiedergabe für die Datenbankkopie verzögert wird. Der Zeitgeber für die Wiedergabeverzögerung startet, wenn eine Protokolldatei für die passive Kopie repliziert und erfolgreich überprüft wurde. Durch die Verzögerung der Wiedergabe von Protokollen für die Datenbankkopie haben Sie die Möglichkeit, die Datenbank zu einem bestimmten Zeitpunkt in der Vergangenheit wiederherzustellen. Eine Postfachdatenbankkopie mit einer Wiedergabeverzögerung von mehr als 0 wird als *verzögerte Postfachdatenbankkopie* oder einfach als *verzögerte Kopie* bezeichnet.

Eine Strategie, in der die Datenbankkopie und die Funktionen für das Beweissicherungsverfahren in Exchange 2013 verwendet werden, kann vor einer Vielzahl von Fehlern schützen, die gewöhnlich zu Datenverlusten führen würden. Diese Funktionen können jedoch bei logischen Beschädigungen, die zwar sehr selten sind, jedoch möglicherweise zu Datenverlusten führen, keinen Schutz vor einem Datenverlust bieten. Verzögerte Kopien sind dazu gedacht, Datenverluste bei logischen Beschädigungen zu vermeiden. Im Allgemeinen gibt es zwei Arten von logischen Beschädigungen:

  - **Logische Beschädigung der Datenbank**   Die Prüfsumme der Datenbankseiten stimmt überein, doch die Daten auf den Seiten sind logisch gesehen falsch. Dies kann vorkommen, wenn ESE versucht, eine Datenbankseite zu schreiben, und die Daten entweder niemals auf den Datenträger geschrieben wurden oder sie sich am falschen Speicherort befinden, auch wenn vom Betriebssystem eine Nachricht zur erfolgreichen Ausführung zurückgegeben wurde. Dies wird als *verlorene Leerung* bezeichnet. Damit bei verlorenen Leerungen keine Daten verloren gehen, bezieht ESE einen Mechanismus zur Erkennung verlorener Leerungen zusammen mit einer Funktion zum Patchen von Seiten (Einzelseitenwiederherstellung) in die Datenbank ein.

  - **Logische Beschädigung des Speichers**   Es werden Daten auf eine Weise hinzugefügt, gelöscht oder geändert, die der Benutzer nicht erwartet. Diese Fälle werden im Allgemeinen durch Anwendungen von Drittanbietern verursacht. Es handelt sich im Allgemeinen nur insofern um eine Beschädigung, als der Benutzer sie als Beschädigung betrachtet. Der Exchange-Speicher betrachtet die Transaktion, die zur logischen Beschädigung geführt hat, als eine Folge gültiger MAPI-Operationen. Die Funktion für Beweissicherungsverfahren in Exchange 2013 bietet Schutz gegen logische Beschädigungen des Speichers, indem verhindert wird, dass Inhalte von einem Benutzer oder einer Anwendung dauerhaft gelöscht werden. Es gibt jedoch auch Szenarien, in denen ein Benutzerpostfach so beschädigt wird, dass es einfacher ist, die Datenbank zu einem Zeitpunkt vor der Beschädigung wiederherzustellen, um dann das Benutzerpostfach zu exportieren, damit nicht beschädigte Daten abgerufen werden können.

Durch die Kombination aus Datenbankkopien, Aufbewahrungsrichtlinien und ESE-Wiederherstellungen einzelner Seiten verbleibt nur die seltene, jedoch katastrophale logische Beschädigung des Speichers. Ihre Entscheidung, ob Sie eine Datenbankkopie mit Wiedergabeverzögerung (eine verzögerte Kopie) verwenden, hängt davon ab, welche Anwendungen von Drittanbietern Sie einsetzen und welche Erfahrungen Ihre Organisation mit logischen Beschädigungen des Speichers gemacht hat.

Verzögerte Kopien können sich in Exchange 2013 bis zu einem gewissen Grad selbst verwalten, wenn Sie in bestimmten Szenarien eine automatische Protokollwiedergabe auslösen:

  - Wenn ein Schwellenwert für zu wenig Speicherplatz erreicht wird

  - Wenn die verzögerte Kopie eine physische Beschädigung aufweist und ein Seitenpatching erforderlich ist

  - Wenn für mehr als 24 Stunden weniger als drei fehlerfreie Kopien (nur aktiv oder passiv; verzögerte Datenbankkopien werden nicht gezählt) zur Verfügung stehen

Das Seitenpatching kann über die automatische Wiedergabefunktion für verzögerte Kopien genutzt werden. Wenn das System ermittelt, dass für eine verzögerte Kopie ein Seitenpatching erforderlich ist, werden die Protokolle automatisch in die verzögerte Kopie wiedergegeben, um das Seitenpatching auszuführen. Verzögerte Kopien rufen die automatische Wiedergabefunktion auch auf, wenn ein Schwellenwert bezüglich zu wenig Speicherplatz erreicht wird und wenn die verzögerte Kopie während eines bestimmten Zeitraums die einzige verfügbare Kopie ist.

Die Wiedergabe für verzögerte Kopien ist standardmäßig deaktiviert und kann durch Ausführung des folgenden Befehls aktiviert werden:

    Set-DatabaseAvailabilityGroup <DAGName> -ReplayLagManagerEnabled $true

Nach der Aktivierung wird eine Wiedergabe durchgeführt, wenn weniger als drei Kopien zur Verfügung stehen. Sie können den Standardwert 3 ändern, indem Sie den folgenden DWORD-Registrierungswert bearbeiten.

**HKLM\\Software\\Microsoft\\ExchangeServer\\v15\\Replay\\Parameters\\ReplayLagManagerNumAvailableCopies**

Sie müssen den folgenden Registrierungswert konfigurieren, um die Wiedergabe bei Erreichen von Schwellenwerten in Bezug auf zu wenig Speicherplatz zu aktivieren:

**HKLM\\Software\\Microsoft\\ExchangeServer\\v15\\Replay\\Parameters\\ReplayLagLowSpacePlaydownThresholdInMB**

Starten Sie nach der Konfiguration einer dieser Registrierungseinstellungen den Microsoft Exchange DAG-Verwaltungsdienst neu, damit die Änderungen übernommen werden.

Beispiel: Angenommen, eine Umgebung weist eine Datenbank mit 4 Kopien auf (3 hoch verfügbare Kopien und 1 verzögerte Kopie), und für ReplayLagManagerNumAvailableCopies wird die Standardeinstellung verwendet. Wenn eine nicht verzögerte Kopie aus irgendeinem Grund nicht verwendet werden kann (z. B. weil sie angehalten wurde), gibt die verzögerte Kopie ihre Protokolldateien automatisch in 24 Stunden wieder.

Wenn Sie verzögerte Kopien verwenden, ohne den `ReplayLagManagerEnabled`-Parameter zu aktivieren, beachten Sie die folgenden Konsequenzen:

  - Die Wiedergabeverzögerung ist ein vom Administrator konfigurierter Wert, der standardmäßig deaktiviert ist.

  - Die Einstellung für die Wiedergabeverzögerung besitzt eine Standardeinstellung von 0 Tagen sowie eine maximale Einstellung von 14 Tagen.

  - Verzögerte Kopien werden nicht als hochverfügbare Kopien betrachtet. Stattdessen wurden sie zur Notfallwiederherstellung entworfen, um vor logischen Beschädigungen des Speichers zu schützen.

  - Je größer die festgelegte Wiedergabeverzögerung, desto länger ist der Datenbankwiederherstellungsprozess. Je nach der Anzahl der Protokolldateien, die während der Wiederherstellung wiedergegeben werden müssen, und nach der Geschwindigkeit, mit der Ihre Hardware diese wiedergeben kann, sind möglicherweise einige Stunden oder mehr für die Wiederherstellung einer Datenbank erforderlich.

  - Es wird empfohlen, dass Sie ermitteln, ob verzögerte Kopien für ihre Gesamtstrategie zur Wiederherstellung entscheidend sind. Wenn deren Verwendung für ihre Strategie entscheidend ist, wird empfohlen, mehrere verzögerte Kopien zu verwenden. Sie können auch RAID (Redundant Array of Independent Disks) verwenden, um eine einzelne verzögerte Kopie zu schützen, wenn Sie nicht über mehrere verzögerte Kopien verfügen. Falls Sie einen Datenträger verlieren oder eine Beschädigung auftritt, verlieren Sie nicht Ihren verzögerten Zeitpunkt in der Vergangenheit.

  - Verzögerte Kopien können nicht mit der ESE-Funktion zur Wiederherstellung einzelner Seiten gepatcht werden. Wenn bei einer verzögerten Kopie die Beschädigung einer Datenbankseite auftritt (z. B. der Fehler -1018), dann muss für diese Kopie das erneute Seeding ausgeführt werden (wodurch der verzögerte Aspekt der Kopie verloren geht).

Das Aktivieren und Wiederherstellen einer verzögerten Postfachdatenbankkopie ist ein einfacher Vorgang, wenn die Datenbank alle Protokolldateien wiedergeben und die Datenbankkopie auf den aktuellen Stand gebracht werden soll. Wenn Sie die Protokolldateien nur bis zu einem bestimmten Zeitpunkt wiedergeben möchten, ist der Vorgang komplizierter, da Sie die Protokolldateien manuell bearbeiten und das Tool "Eseutil" (Exchange Server Database Utilities) ausführen müssen.

Genaue Anweisungen zum Aktivieren einer verzögerten Kopie einer Postfachdatenbank finden Sie unter [Aktivieren einer verzögerten Kopie einer Postfachdatenbank](activate-a-lagged-mailbox-database-copy-exchange-2013-help.md).

## Abschneideverzögerung

Die Abschneideverzögerung ist eine Eigenschaft einer Postfachdatenbankkopie, die die Dauer (in Minuten) angibt, die das Löschen des Protokolls für die Datenbankkopie verzögert wird. Der Zeitgeber für die Abschneideverzögerung startet, wenn eine Protokolldatei für die passive Kopie repliziert, erfolgreich überprüft und erfolgreich in der Kopie der Datenbank wiedergegeben wurde. Durch die Verzögerung beim Abschneiden von Protokolldateien von der Datenbankkopie haben Sie die Möglichkeit, eine Wiederherstellung nach Fehlern durchzuführen, die die Protokolldateien für die aktive Kopie der Datenbank betreffen.

## Datenbankkopien und Abschneiden der Protokolldateien

Das Abschneiden der Protokolldateien funktioniert in Exchange 2013 auf die gleiche Weise wie in Exchange 2010. Das Abschneideverhalten wird durch die Einstellungen für die Wiedergabe- und Abschneideverzögerung der Kopie bestimmt.

Die folgenden Kriterien müssen für das Abschneiden der Protokolldatei einer Datenbankkopie erfüllt sein, wenn die die Standardwerte (0 = deaktiviert) der Verzögerungseinstellungen beibehalten werden:

  - Die Protokolldatei muss erfolgreich gesichert worden sein, oder die Umlaufprotokollierung muss aktiviert sein.

  - Die Protokolldatei muss sich unterhalb des Prüfpunkts (die für die Wiederherstellung erforderliche minimale Protokolldatei) für die Datenbank befinden.

  - Alle anderen verzögerten Kopien müssen die Protokolldatei geprüft haben.

  - Alle anderen Kopien (nicht verzögerte Kopien) müssen die Protokolldatei wiedergegeben haben.

Die folgenden Kriterien müssen erfüllt sein, damit das Abschneiden für eine verzögerte Datenbankkopie erfolgt:

  - Die Protokolldatei muss sich unterhalb des Prüfpunkts für die Datenbank befinden.

  - Die Protokolldatei muss älter sein als "ReplayLagTime" + "TruncationLagTime".

  - Die Protokolldatei muss für die aktive Kopie abgeschnitten worden sein.

Das Abschneiden von Protokollen in Exchange 2013 tritt bei der aktiven Postfachdatenbankkopie nicht auf, wenn eine oder mehrere passive Kopien angehalten werden. Wenn geplante Wartungsaktivitäten einen längeren Zeitraum (z. B. mehrere Tage) in Anspruch nehmen, kann eine beträchtliche Menge von Protokolldateien erstellt werden. Damit das Protokolllaufwerk nicht durch Transaktionsprotokolle überfüllt wird, können Sie die betroffene passive Datenbankkopie entfernen, anstatt sie anzuhalten. Nach Abschluss der geplanten Wartung können Sie die passive Datenbankkopie wieder hinzufügen.

Exchange 2013 Service Pack 1 (SP1) führt eine neue Funktion namens *loose truncation* (ungenau Abschneiden), die standardmäßig deaktiviert ist. Während des Normalbetriebs verwaltet jede Datenbankkopie Protokolle, die an die anderen Datenbankkopien gesendet werden müssen, bis alle Kopien der Datenbank die Wiedergabe (passive Kopien) oder den Empfang (verzögerte Kopien) der Protokolldateien bestätigen. Dies ist das Standardverhalten für das Abschneiden der Protokolle. Wenn eine Datenbankkopie aus irgendeinem Grund offline geht, sammeln sich die Protokolldateien auf den Datenträgern an, die von anderen Kopien der Datenbank verwendet werden. Wenn die betreffende Datenbankkopie über einen längeren Zeitraum hinweg offline bleibt, kann dies dazu führen, dass die anderen Datenbankkopie nicht mehr über ausreichend Speicherplatz verfügen.

Wenn ungenaues Abschneiden aktiviert ist, unterscheidet sich das Abschneideverhalten. Jede Datenbankkopie verfolgt ihren eigenen freien Speicherplatz und wendet ungenaues Abschneiden an, wenn der freie Speicherplatz zur Neige geht. Für die aktive Kopie wird der älteste Nachzügler (die passive Datenkkopie, die in der Protokollwiedergabe am weitesten zurückliegt) ignoriert und beim Abschneiden werden die ältesten verbleibenden passiven Kopien respektiert. Die aktive Datenbankkopie ist dort, wo das globale Abschneiden berechnet wird. Die passiven Kopien versuchen, die in der aktiven Kopie getroffene Abschneideentscheidung zu respektieren. Unabhängig von der vermeintlichen Mindestanzahl der zu schützenden Kopien ignoriert Exchange nur die ältesten bekannten Nachzügler zum Zeitpunkt des Abschneidens. Für eine passive Kopie werden die Protokolldateien unabhängig davon mit den unten beschriebenen Parametern abgeschnitten, wenn es zu wenig Speicherplatz gibt.

Wenn die Offllinedatenbank wieder online geht, fehlen hier die Protokolldateien, die von den anderen fehlerfreien gelöscht werden, und daher erhält diese Datenbankkopie den Status FailedAndSuspended. In diesem Fall wird AutoReseed konfiguriert, und für die betreffende Kopie wird automatisch ein erneutes Seeding durchgeführt. Wenn AutoReseed nicht konfiguriert ist, muss der Administrator manuell ein erneutes Seeding für die Datenbankkopie durchführen.

Die erforderliche Anzahl von fehlerfreien Kopien, der Schwellenwert für freien Festplattenspeicher und die Anzahl der zu speichernden Protokolle sind konfigurierbare Parameter. Standardmäßig beträgt der Schwellenwert für freien Festplattenspeicher 204.800 MB (200 GB), und die Anzahl der zu speichernden Protokolle beträgt 100.000 (100 GB) für passive Kopien sowie 100.000 (100 GB) für aktive Kopien.

Zum Aktivieren der Funktion zum ungenauen Abschneiden und Konfigurieren der zugehörigen Parameter muss die Windows-Registrierung auf jedem DAG-Mitglied bearbeitet werden. Es gibt drei Registrierungswerte, die konfiguriert werden können und alle unter "HKLM\\Software\\Microsoft\\ExchangeServer\\v15\\BackupInformation" gespeichert werden. Der Schlüssel "BackupInformation" mit den folgenden DWORD-Werten ist standardmäßig nicht vorhanden, sondern muss manuell erstellt werden. Die DWORD-Registierungswerte unter "BackupInformation" werden in der folgenden Tabelle beschrieben:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Registrierungswert</th>
<th>Beschreibung</th>
<th>Standardwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LooseTruncation_MinCopiesToProtect</p></td>
<td><p>Dieser Schlüssel dient zur Aktivierung des ungenauen Abschneidens. Er steht für die Anzahl der passiven Kopien, die vor dem ungenauen Abschneiden auf der aktiven Kopie einer Datenbank geschützt werden sollen. Durch Festlegen dieses Schlüsselwerts auf 0 wird das ungenaue Abschneiden deaktiviert.</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>LooseTruncation_MinDiskFreeSpaceThresholdInMB</p></td>
<td><p>Schwellenwert für verfügbaren Festplattenspeicher (in MB) zum Auslösen der Funktion zum ungenauen Abschneiden. Wenn weniger freier Festplattenspeicher vorhanden ist, als hier angegeben, wird die Funktion zum ungenauen Abschneiden aktiviert.</p></td>
<td><p>Falls dieser Registrierungswert nicht konfiguriert ist, wird der Standardwert von 200 GB für das ungenaue Abschneiden verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>LooseTruncation_MinLogsToProtect</p></td>
<td><p>Die minimale Anzahl von Protokolldateien, die für fehlerfreie Kopien, deren Protokolle abgeschnitten werden, aufbewahrt werden sollen. Wenn dieser Registrierungswert konfiguriert ist, gilt der konfigurierte Wert sowohl für aktive als auch für passive Kopien.</p></td>
<td><p>Falls dieser Registrierungswert nicht konfiguriert ist, wird der Standardwert von 100.000 für passive Datenbankkopien und 100.000 für aktive Datenbankkopien verwendet.</p></td>
</tr>
</tbody>
</table>


Beachten Sie bei der Verwendung des Registrierungswerts "LooseTruncation\_MinLogsToProtect", dass das Verhalten für aktive und passive Datenbankkopien unterschiedlich ist. In der aktiven Datenbankkopie ist dies die Anzahl der Zusatzprotokolle, die vor denen beibehalten werden, die von den geschützten passiven Kopien benötigt werden, sowie dem erforderlichen Bereich der aktiven Kopie. In der passiven Datenbankkopie ist dies die Anzahl der Protokolle, die vom letzten verfügbaren Protokoll verwaltet wird. Ein Zehntel dieser Anzahl wird außerdem verwendet, um Protokolle vor dem erforderlichen Bereich dieser passiven Kopie zu verwalten. Die beiden Grenzwerte sollen sicherstellen, dass verzögerte Datenbankkopien nicht zuviel Platz wegnehmen, da ihr erforderlicher Bereich in der Regel sehr groß ist.

## Datenbankaktivierungsrichtlinie

Es gibt Szenarien, in denen Sie möglicherweise eine Postfachdatenbankkopie erstellen und das System daran hindern möchten, diese Kopie bei einem Fehler automatisch zu aktivieren. Beispiel:

  - Wenn Sie eine oder mehrere Postfachdatenbankkopien in einem alternativen Datencenter oder in einem Ersatzdatencenter bereitstellen.

  - Wenn Sie eine Datenbankkopie als verzögerte Kopie für Wiederherstellungszwecke konfigurieren.

  - Wenn Sie die Wartung oder Aktualisierung eines Servers durchführen.

In jedem der vorangehenden Szenarien verfügen Sie über Datenbankkopien, die nicht automatisch vom System aktiviert werden sollen. Damit das System am automatischen Aktivieren einer Postfachdatenbankkopie gehindert wird, können Sie die Kopie so konfigurieren, dass sie für die Aktivierung blockiert (angehalten) ist. Dadurch kann das System die Aktualität der Datenbank mithilfe von Protokollversand und -wiederherstellung aufrecht erhalten, doch es wird daran gehindert, die Kopie automatisch zu aktivieren und zu verwenden. Für die Aktivierung blockierte Kopien müssen von einem Administrator manuell aktiviert werden. Sie können die Richtlinie für die Datenbankaktivierung für einen vollständigen Server mithilfe des Cmdlets [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)) oder eine einzelne Datenbankkopie mithilfe des Cmdlets [Set-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298104\(v=exchg.150\)) konfigurieren, um den Parameter *DatabaseCopyAutoActivationPolicy* auf "Blocked" festzulegen.

Weitere Informationen zum Konfigurieren der Richtlinie für die Datenbankaktivierung finden Sie unter [Konfigurieren der Aktivierungsrichtlinie für die Kopie einer Postfachdatenbank](configure-activation-policy-for-a-mailbox-database-copy-exchange-2013-help.md).

## Auswirkungen von Postfachverschiebungen auf die fortlaufende Replikation

Bei einer Postfachdatenbank mit hoher Auslastung und hoher Protokollgenerierungsrate besteht ein größeres Risiko von Datenverlust, wenn die Replikation in die passiven Datenbankkopien nicht mit der Protokollgenerierung Schritt halten kann. Ein Szenario, in dem eine hohe Protokollgenerierungsrate auftreten kann, sind Postfachverschiebungen. Exchange 2013 umfasst eine Datengarantie-API, die von Diensten wie dem Microsoft Exchange-Postfachreplikationsdienst verwendet wird, um die Integrität der Architektur der Datenbankkopien basierend auf dem Wert des Parameters *DataMoveReplicationConstraint* zu überprüfen, der vom System oder einem Administrator festgelegt wurde. Diese Datengarantie-API kann für folgende Aufgaben verwendet werden:

  - **Überprüfen der Replikationsintegrität**   Bei dieser Aufgabe wird überprüft, ob die erforderliche Anzahl von Datenbankkopien verfügbar ist.

  - **Überprüfen von Replikationslöschvorgängen**   Bei dieser Aufgabe wird überprüft, ob die erforderlichen Protokolldateien für die erforderliche Anzahl von Datenbankkopien wiedergegeben wurden.

Bei der Ausführung gibt die API die folgenden Statusinformationen für die aufrufende Anwendung zurück:

  - **Retry**   Dieser Status zeigt an, dass vorübergehende Fehler vorliegen und eine Bedingung nicht für die Datenbank überprüft werden kann.

  - **Satisfied**   Dieser Status zeigt an, dass die Datenbank die erforderlichen Bedingungen erfüllt oder nicht repliziert wird.

  - **NotSatisfied**   Dieser Status zeigt an, dass die Datenbank die erforderlichen Bedingungen nicht erfüllt. Darüber hinaus wird für die aufrufende Anwendung angegeben, weshalb die Antwort **NotSatisfied** zurückgegeben wurde.

Der Wert des Parameters *DataMoveReplicationConstraint* für die Postfachdatenbank gibt an, wie viele Datenbankkopien im Rahmen der Anforderung ausgewertet werden sollen. Mögliche Werte des Parameters *DataMoveReplicationConstraint*:

  - `None`   Beim Erstellen einer Postfachdatenbank wird standardmäßig dieser Wert festgelegt. Bei Festlegung dieses Werts werden die Bedingungen der Datengarantie-API ignoriert. Diese Einstellung sollte nur für Postfachdatenbanken verwendet werden, die nicht repliziert werden.

  - `SecondCopy`   Dies ist der Standardwert, wenn Sie eine zweite Kopie einer Postfachdatenbank hinzufügen. Bei Festlegung dieses Werts muss mindestens eine passive Datenbankkopie die Bedingungen der Datengarantie-API erfüllen.

  - `SecondDatacenter`   Bei Festlegung dieses Werts muss mindestens eine passive Datenbankkopie an einem anderen Active Directory-Standort die Bedingungen der Datengarantie-API erfüllen.

  - `AllDatacenters`   Bei Festlegung dieses Werts muss mindestens eine passive Datenbankkopie an jedem Active Directory-Standort die Bedingungen der Datengarantie-API erfüllen.

  - `AllCopies`   Bei Festlegung dieses Werts müssen alle Kopien der Postfachdatenbank die Bedingungen der Datengarantie-API erfüllen.

**Überprüfen der Replikationsintegrität**

Wenn die Datengarantie-API ausgeführt wird, um die Integrität der Infrastruktur der Datenbankkopien auszuwerten, werden verschiedene Elemente ausgewertet.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert des Parameters <em>DataMoveReplicationConstraint</em></th>
<th>Anforderung für eine Datenbank</th>
<th>Bedingungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>SecondCopy</code></p></td>
<td><p>Mindestens eine passive Datenbankkopie für eine replizierte Datenbank muss die Bedingungen in der nächsten Spalte erfüllen.</p></td>
<td><p>Die passive Datenbank muss folgende Bedingungen erfüllen:</p>
<ul>
<li><p>Fehlerfreier Status.</p></li>
<li><p>Wiedergabewarteschlange mit einer Dauer von 10 Minuten des Wiedergabeverzögerungszeitraums.</p></li>
<li><p>Länge der Kopiewarteschlange von weniger als 10 Protokollen.</p></li>
<li><p>Durchschnittliche Länge der Kopiewarteschlange von weniger als 10 Protokollen. Die durchschnittliche Länge der Kopiewarteschlange wird basierend auf der Anzahl von Abfragen des Datenbankstatus durch die Anwendung berechnet.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>SecondDatacenter</code></p></td>
<td><p>Mindestens eine passive Datenbankkopie an einem anderen Active Directory-Standort muss die Bedingungen in der nächsten Spalte erfüllen.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><code>AllDatacenters</code></p></td>
<td><p>Die aktive Kopie muss eingebunden sein, und eine passive Kopie an jedem Active Directory-Standort muss die Bedingungen in der nächsten Spalte erfüllen.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><code>AllCopies</code></p></td>
<td><p>Die aktive Kopie muss eingebunden sein, und alle passiven Datenbankkopien müssen die Bedingungen in der nächsten Spalte erfüllen.</p></td>
<td></td>
</tr>
</tbody>
</table>


**Überprüfen von Replikationslöschvorgängen**

Mithilfe der Datengarantie-API kann zudem überprüft werden, ob die erforderlichen Transaktionsprotokolle von der erforderlichen Anzahl von Datenbankkopien wiedergegeben wurden. Zu diesem Zweck wird der Zeitstempel des letzten wiedergegebenen Protokolls mit dem Commitzeitstempel des aufrufenden Diensts verglichen (in den meisten Fällen ist dies der Zeitstempel der letzten Protokolldatei mit den erforderlichen Daten). Dabei werden fünf Sekunden hinzugerechnet, um Zeitabweichungen oder Schwankungen bei der Systemzeit Rechnung zu tragen. Wenn der Wiedergabezeitstempel größer ist als der Commitzeitstempel, gilt die Bedingung des Parameters *DataMoveReplicationConstraint* als erfüllt. Wenn der Wiedergabezeitstempel kleiner ist als der Commitzeitstempel, gilt die Bedingung des Parameters *DataMoveReplicationConstraint* als nicht erfüllt.

Bevor Sie eine große Anzahl von Postfächern in bzw. aus Replikationsdatenbanken innerhalb einer DAG verschieben, sollten Sie den Parameter *DataMoveReplicationConstraint* wie folgt für jede Postfachdatenbank konfigurieren:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Bereitstellung</th>
<th>Legen Sie &quot;DataMoveReplicationConstraint&quot; auf folgenden Wert fest:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Postfachdatenbanken, die keine Datenbankkopien aufweisen</p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p>Eine DAG an einem einzigen Active Directory-Standort</p></td>
<td><p><code>SecondCopy</code></p></td>
</tr>
<tr class="odd">
<td><p>Eine DAG, die sich über mehrere Datencenter erstreckt, unter Verwendung eines verteilten Active Directory-Standorts</p></td>
<td><p><code>SecondCopy</code></p></td>
</tr>
<tr class="even">
<td><p>Eine DAG, die sich über zwei Active Directory-Standorte erstreckt, sowie Datenbankkopien mit hoher Verfügbarkeit an jedem Standort</p></td>
<td><p><code>SecondDatacenter</code></p></td>
</tr>
<tr class="odd">
<td><p>Eine DAG, die sich über zwei Active Directory-Standorte erstreckt, sowie ausschließlich verzögerte Datenbankkopien am zweiten Standort</p></td>
<td><p><code>SecondCopy</code></p>
<p>Der Grund dafür ist, dass die Datengarantie-API einen Commit der Daten erst garantiert, wenn die Protokolldatei in die Datenbankkopie wiedergegeben wird. Außerdem tritt aufgrund der Verzögerung mit dieser Einschränkung bei der Verschiebungsanforderung ein Fehler auf, sofern der Wert der verzögerten Datenbankkopie &quot;ReplayLagTime&quot; nicht auf weniger als 30 Minuten festgelegt wird.</p></td>
</tr>
<tr class="even">
<td><p>Eine DAG, die sich über mindestens drei Active Directory-Standorte erstreckt, sowie Datenbankkopien mit hoher Verfügbarkeit an jedem Standort</p></td>
<td><p><code>AllDatacenters</code></p></td>
</tr>
</tbody>
</table>


## Ausgleichen von Datenbankkopien

Aufgrund der inhärenten Merkmale von DAGs werden die Hosts von aktiven Postfachdatenbankkopien durch Datenbankswitchover und -failover mehrfach während der Lebensdauer der DAG geändert. Dadurch kann die Verteilung der aktiven Postfachdatenbankkopien der DAGs aus dem Gleichgewicht geraten. Die folgende Tabelle zeigt als Beispiel eine DAG mit vier Datenbanken und vier Kopien jeder Datenbank (insgesamt 16 Datenbanken auf jedem Server) sowie einer unausgeglichenen Verteilung aktiver Datenbankkopien.

### DAG mit unausgeglichener Verteilung aktiver Kopien

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Server</th>
<th>Anzahl von aktiven Datenbanken</th>
<th>Anzahl von passiven Datenbanken</th>
<th>Anzahl von eingebundenen Datenbanken</th>
<th>Anzahl von nicht eingebundenen Datenbanken</th>
<th>Anzahl von Datenbanken mit diesen Einstellungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EX1</p></td>
<td><p>5</p></td>
<td><p>11</p></td>
<td><p>5</p></td>
<td><p>0</p></td>
<td><p>4, 4, 3, 5</p></td>
</tr>
<tr class="even">
<td><p>EX2</p></td>
<td><p>1</p></td>
<td><p>15</p></td>
<td><p>1</p></td>
<td><p>0</p></td>
<td><p>1, 8, 6, 1</p></td>
</tr>
<tr class="odd">
<td><p>EX3</p></td>
<td><p>12</p></td>
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>0</p></td>
<td><p>13, 2, 1, 0</p></td>
</tr>
<tr class="even">
<td><p>EX4</p></td>
<td><p>1</p></td>
<td><p>15</p></td>
<td><p>1</p></td>
<td><p>0</p></td>
<td><p>1, 1, 5, 9</p></td>
</tr>
</tbody>
</table>


Im vorausgehenden Beispiel sind vier Kopien jeder Datenbank vorhanden, daher gibt es nur vier mögliche Werte für die Aktivierungseinstellungen (1, 2, 3 oder 4). Die Spalte **Anzahl von Datenbanken mit diesen Einstellungen** zeigt die Anzahl von Datenbanken mit diesen Werten. Auf EX3 gibt es beispielsweise 13 Datenbankkopien mit der Aktivierungseinstellung 1, zwei Kopien mit der Aktivierungseinstellung 2, eine Kopie mit der Aktivierungseinstellung 3 und keine Kopie mit der Aktivierungseinstellung 4.

Diese DAG ist also weder hinsichtlich der Anzahl von aktiven Datenbanken, die von jedem DAG-Mitglied gehostet werden, der Anzahl von passiven Datenbanken, die von jedem DAG-Mitglied gehostet werden, oder der Anzahl von Aktivierungseinstellungen der gehosteten Datenbanken ausgeglichen.

Sie können das Skript "RedistributeActiveDatabases.ps1" verwenden, um die aktiven Datenbankkopien innerhalb einer DAG auszugleichen. Das Skript verschiebt Datenbanken zwischen ihren Kopien, um die Anzahl von eingebundenen Datenbanken auf jedem Server in einer DAG auszugleichen. Falls erforderlich, versucht das Skript auch einen Ausgleich aktiver Datenbanken an den Standorten durchzuführen.

Das Skript stellt zwei Optionen zum Ausgleich aktiver Datenbankkopien in einer DAG bereit:

  - **BalanceDbsByActivationPreference**   Wenn diese Option aktiviert wurde, versucht das Skript, die Datenbanken auf die bevorzugte Kopie zu verschieben (basierend auf der Aktivierungseinstellung), ohne dabei den Active Directory-Standort zu berücksichtigen.

  - **BalanceDbsBySiteAndActivationPreference**   Wenn diese Option aktiviert wurde, versucht das Skript, die Datenbanken auf die bevorzugte Kopie zu verschieben und einen Ausgleich der aktiven Datenbanken innerhalb jedes Active Directory-Standorts zu erreichen.

Nach Ausführen des Skripts mit der ersten Option wird die vorher unausgeglichene DAG ausgeglichen, wie in der folgenden Tabelle gezeigt.

### DAG mit ausgeglichener Verteilung aktiver Kopien

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>server</th>
<th>Anzahl von aktiven Datenbanken</th>
<th>Anzahl von passiven Datenbanken</th>
<th>Anzahl von eingebundenen Datenbanken</th>
<th>Anzahl von nicht eingebundenen Datenbanken</th>
<th>Anzahl von Datenbanken mit diesen Einstellungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EX1</p></td>
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>4</p></td>
<td><p>0</p></td>
<td><p>4, 4, 4, 4</p></td>
</tr>
<tr class="even">
<td><p>EX2</p></td>
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>4</p></td>
<td><p>0</p></td>
<td><p>4, 4, 4, 4</p></td>
</tr>
<tr class="odd">
<td><p>EX3</p></td>
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>4</p></td>
<td><p>0</p></td>
<td><p>4, 4, 4, 4</p></td>
</tr>
<tr class="even">
<td><p>EX4</p></td>
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>4</p></td>
<td><p>0</p></td>
<td><p>4, 4, 4, 4</p></td>
</tr>
</tbody>
</table>


Wie in der vorherigen Tabelle gezeigt, ist diese DAG jetzt bezüglich der Anzahl aktiver und passiver Datenbanken auf jedem Server und der Aktivierungseinstellungen auf den Servern ausgeglichen.

In der folgenden Tabelle sind die verfügbaren Parameter für das Skript "RedistributeActiveDatabases.ps1" aufgeführt.

### Skriptparameter "RedistributeActiveDatabases.ps1"

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>DagName</em></p></td>
<td><p>Gibt den Namen der DAG an, die Sie wieder ausgleichen möchten. Wird dieser Parameter ausgelassen, wird die DAG verwendet, der der lokale Server angehört.</p></td>
</tr>
<tr class="even">
<td><p><em>BalanceDbsByActivationPreference</em></p></td>
<td><p>Gibt an, dass das Skript Datenbanken auf die bevorzugte Kopie verschieben soll, ohne dabei den Active Directory-Standort zu berücksichtigen.</p></td>
</tr>
<tr class="odd">
<td><p><em>BalanceDbsBySiteAndActivationPreference</em></p></td>
<td><p>Gibt an, dass das Skript die aktiven Datenbanken auf die bevorzugte Kopie verschieben und gleichzeitig einen Ausgleich der aktiven Datenbanken innerhalb jedes Active Directory-Standorts erreichen soll.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowFinalDatabaseDistribution</em></p></td>
<td><p>Gibt an, dass ein Bericht zu aktuellen Datenbankverteilung nach abgeschlossener Neuverteilung angezeigt werden soll.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowedDeviationFromMeanPercentage</em></p></td>
<td><p>Gibt die zugelassene Abweichung der Anzahl von aktiven Datenbanken an Standorten als Prozentsatz an. Der Standardwert beträgt 20 %. Wenn beispielsweise 99 Datenbanken auf drei Standorte verteilt werden sollen, entspräche die ideale Verteilung 33 Datenbanken pro Standort. Wenn die zugelassene Abweichung 20 % beträgt, versucht das Skript, die Datenbanken so auszugleichen, dass deren Anzahl an jedem Standort nicht um mehr als 10 % überschritten bzw. unterschritten wird. 10 % von 33 ist 3,3, aufgerundet 4. Daher versucht das Skript zwischen 29 und 37 Datenbanken pro Standort einzurichten.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowDatabaseCurrentActives</em></p></td>
<td><p>Gibt an, dass das Skript einen Bericht für jede Datenbank erstellt, in dem beschrieben wird, wie die Datenbank verschoben wurde und ob sie jetzt auf der bevorzugten Kopie aktiv ist.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShowDatabaseDistributionByServer</em></p></td>
<td><p>Gibt an, dass das Skript einen Bericht zu jedem Server mit der zugehörigen Datenbankverteilung erstellt.</p></td>
</tr>
<tr class="even">
<td><p><em>RunOnlyOnPAM</em></p></td>
<td><p>Gibt an, dass das Skript nur auf dem DAG-Mitglied mit der Rolle &quot;Primary Active Manager&quot; (PAM) ausgeführt wird. Das Skript überprüft, ob es von einem PAM ausgeführt wird. Wenn es nicht von einem PAM ausgeführt wird, wird das Skript beendet.</p></td>
</tr>
<tr class="odd">
<td><p><em>LogEvents</em></p></td>
<td><p>Gibt an, dass das Skript ein Ereignis (MsExchangeRepl-Ereignis &quot;4115&quot;) protokolliert, das eine Zusammenfassung der Aktionen enthält.</p></td>
</tr>
<tr class="even">
<td><p><em>IncludeNonReplicatedDatabases</em></p></td>
<td><p>Gibt an, dass das Skript bei der Bestimmung der Neuverteilung aktiver Datenbanken nicht replizierte Datenbanken (Datenbanken ohne Kopien) umfassen soll. Obwohl nicht replizierte Datenbanken nicht verschoben werden können, beeinflussen sie möglicherweise die Verteilung replizierter Datenbanken.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Die Option &quot;Confirm&quot; kann zum Unterdrücken der Bestätigungsaufforderung verwendet werden, die standardmäßig angezeigt wird, wenn dieses Skript ausgeführt wird. Verwenden Sie zum Unterdrücken dieser Bestätigungsaufforderung die folgende Syntax: -Confirm:$False. Sie müssen einen Doppelpunkt ( : ) in die Syntax einfügen.</p></td>
</tr>
</tbody>
</table>


## RedistributeActiveDatabases.ps1 – Beispiele

In diesem Beispiel wird die aktuelle Datenbankverteilung für eine DAG, einschließlich der Anzahl von Datenbanken mit diesen Einstellungen, veranschaulicht.

    RedistributeActiveDatabases.ps1 -DagName DAG1 -ShowDatabaseDistributionByServer | Format-Table

In diesem Beispiel werden die aktiven Postfachdatenbankkopien in einer DAG mithilfe von Aktivierungseinstellungen neu verteilt und ausgeglichen, ohne dass eine Eingabe erforderlich ist.

    RedistributeActiveDatabases.ps1 -DagName DAG1 -BalanceDbsByActivationPreference -Confirm:$False

In diesem Beispiel werden die aktiven Postfachdatenbankkopien in der DAG mithilfe von Aktivierungseinstellungen neu verteilt und ausgeglichen. Außerdem wird eine Zusammenfassung der Verteilung erstellt.

    RedistributeActiveDatabases.ps1 -DagName DAG1 -BalanceDbsByActivationPreference -ShowFinalDatabaseDistribution

## Überwachen von Datenbankkopien

Eine Datenbankkopie stellt Ihre erste Verteidigungsmaßnahme dar, wenn ein Fehler auftritt, der sich auf die aktive Kopie einer Datenbank auswirkt. Es ist daher äußerst wichtig, den Zustand und Status von Datenbankkopien zu überwachen, damit sichergestellt ist, dass sie bei Bedarf verfügbar sind. Sie können verschiedene Informationen, u. a. die Länge der Kopiewarteschlange, die Länge der Wiedergabewarteschlange, Statusinformationen sowie Informationen zum Zustand des Inhaltsindex anzeigen, indem Sie die Details einer Datenbankkopie in der Exchange-Verwaltungskonsole überprüfen. Sie können auch das Cmdlet **Get-MailboxDatabaseCopyStatus** in der Shell verwenden, um eine Vielzahl von Statusinformationen für eine Datenbankkopie anzuzeigen.

Weitere Informationen zum Überwachen von Datenbankkopien finden Sie unter [Überwachen von Datenbankverfügbarkeitsgruppen](monitoring-database-availability-groups-exchange-2013-help.md).

## Entfernen einer Datenbankkopie

Eine Datenbankkopie kann jederzeit mithilfe der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **Remove-MailboxDatabaseCopy** in der Shell entfernt werden. Nachdem Sie eine Datenbankkopie entfernt haben, müssen Sie manuell alle Datenbank- und Transaktionsprotokolldateien von dem Server entfernen, von dem die Datenbankkopie entfernt wurde. Genaue Anweisungen zum Entfernen einer Datenbankkopie finden Sie unter [Entfernen einer Postfachdatenbankkopie](remove-a-mailbox-database-copy-exchange-2013-help.md).

## Datenbankswitchover

Der Postfachserver, der die aktive Kopie einer Datenbank hostet, wird als Postfachdatenbankmaster bezeichnet. Die Aktivierung einer passiven Datenbankkopie ändert den Postfachdatenbankmaster für die Datenbank und macht aus der passiven Kopie eine neue, aktive Kopie. Dieser Prozess wird als Datenbankswitchover bezeichnet. Bei einem Datenbankswitchover wird die Einbindung einer aktiven Kopie einer Datenbank auf einem Postfachserver aufgehoben und eine passive Kopie dieser Datenbank als neue aktive Postfachdatenbank auf einem anderen Postfachserver eingebunden. Wenn Sie einen Switchover ausführen, können Sie die Wahleinstellung für die Datenbankeinbindung für den neuen Postfachdatenbankmaster optional außer Kraft setzen.

Sie können schnell erkennen, welcher Postfachserver der aktuelle Postfachdatenbankmaster ist, indem Sie die rechte Spalte auf der Registerkarte **Datenbankkopien** in der Exchange-Verwaltungskonsole überprüfen. Ein Switchover kann über den Link **Aktivieren** in der Exchange-Verwaltungskonsole oder über das Cmdlet **Move-ActiveMailboxDatabase** in der Shell ausgeführt werden.

Es gibt verschiedene interne Prüfungen, die ausgeführt werden, bevor eine passive Kopie aktiviert wird:

  - Der Status der Datenbankkopie wird überprüft. Wenn die Datenbankkopie einen fehlerhaften Status aufweist, wird der Switchover blockiert. Sie können dieses Verhalten außer Kraft setzen und die Systemdiagnose mithilfe des Parameters *SkipHealthChecks* des Cmdlets **Move-ActiveMailboxDatabase** umgehen. Mithilfe dieses Parameters können Sie die aktive Kopie in eine Datenbankkopie mit einem fehlerhaften Status verschieben.

  - Für die aktive Datenbankkopie wird überprüft, ob sie gegenwärtig eine Seedingquelle für passive Kopien der Datenbank ist. Wenn die aktive Kopie gegenwärtig als Seedingquelle verwendet wird, wird der Switchovervorgang blockiert. Sie können dieses Verhalten außer Kraft setzen und die Überprüfung der Seedingquelle mithilfe des Parameters *SkipActiveCopyChecks* des Cmdlets **Move-ActiveMailboxDatabase** umgehen. Dieser Parameter ermöglicht das Verschieben einer aktiven Kopie, die als Seedingquelle verwendet wird. Bei Verwendung dieses Parameters wird der Seedingvorgang abgebrochen und als nicht erfolgreich eingestuft.

  - Die Länge der Kopie- und Wiedergabewarteschlange für die Datenbankkopie wird überprüft, um sicherzustellen, dass ihre Werte den konfigurierten Kriterien entsprechen. Die Datenbankkopie wird auch überprüft, damit sichergestellt ist, dass sie momentan nicht als Seedingquelle verwendet wird. Wenn die Werte für die Warteschlangenlänge nicht den konfigurierten Kriterien entsprechen oder die Datenbank derzeit als Seedingquelle verwendet wird, wird der Switchover blockiert. Sie können dieses Verhalten außer Kraft setzen und diese Prüfungen mithilfe des Parameters *SkipLagChecks* des Cmdlets **Move-ActiveMailboxDatabase** umgehen. Dieser Parameter ermöglicht es, dass eine Kopie aktiviert wird, die über nicht den Kriterien entsprechende Wiedergabe- und Kopiewarteschlangen verfügt.

  - Der Status des Suchkatalogs (Inhaltsindex) für die Datenbankkopie wird überprüft. Wenn der Suchkatalog nicht auf dem neuesten Stand ist, sich in einem fehlerhaften Zustand befindet oder beschädigt ist, wird der Switchover blockiert. Sie können dieses Verhalten außer Kraft setzen und die Überprüfung des Suchkatalogs mithilfe des Parameters *SkipClientExperienceChecks* des Cmdlets **Move-ActiveMailboxDatabase** umgehen. Dieser Parameter führt dazu, dass diese Suche die Systemdiagnose für den Katalog überspringt. Wenn sich der Suchkatalog für die von Ihnen zu aktivierende Datenbankkopie in einem fehlerhaften oder nicht zu verwendenden Zustand befindet und Sie diesen Parameter zum Überspringen der Systemdiagnose für den Katalog verwenden und dann die Datenbankkopie aktivieren, müssen Sie den Suchkatalog erneut durchforsten oder das Seeding für den Katalog erneut ausführen.

Wenn Sie einen Datenbankswitchover ausführen, haben Sie auch die Möglichkeit, die Wahleinstellungen für die Einbindung außer Kraft zu setzen, die für den Server konfiguriert wurden, der den Host für die zu aktivierende passive Datenbankkopie darstellt. Der Parameter *MountDialOverride* des Cmdlets **Move-ActiveMailboxDatabase** weist den Zielserver an, die eigenen Wahleinstellungen für die Einbindung außer Kraft zu setzen und die vom Parameter *MountDialOverride* angegebenen Einstellungen zu verwenden.

Genaue Anweisungen zum Ausführen eines Switchovers für eine Datenbankkopie finden Sie unter [Aktivieren einer Kopie einer Postfachdatenbank](activate-a-mailbox-database-copy-exchange-2013-help.md).

