---
title: Problembehandlung beim SiteMailbox-Integritätssatz
TOCTitle: Problembehandlung beim SiteMailbox-Integritätssatz
ms:assetid: ac00985c-c9a5-44bf-b152-4b99d8ae24ed
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.sitemailbox(v=EXCHG.150)
ms:contentKeyID: 53181871
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim SiteMailbox-Integritätssatz

 

_**Gilt für:**Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-11_

Mit dem SiteMailbox-Integritätssatz werden die Gesamtintegrität und Zugänglichkeit der Websitepostfächer in Ihrer Organisation überwacht.

Wenn Sie eine Warnung erhalten, dass Integritätsfehler in SiteMailbox vorliegen, weist dies darauf hin, dass die Inhalte eines Benutzerpostfachs in einem nicht synchronisierten Zustand sind.

## Erläuterung

Das SiteMailbox-Überwachungssystem empfängt passive Synchronisierungsergebnisse vom Hintergrundsynchronisierungsdienst. Dieses System verwendet keine Tests. Die passiven Synchronisierungsergebnisse werden nach jedem Synchronisierungsversuch in das SiteMailbox-Überwachungssystem geschrieben. Synchronisierungen werden auch ausgelöst, wenn die folgenden Ereignisse auftreten:

  - Benutzer greifen auf ihre Websitepostfächer zu, indem sie Outlook oder Outlook Web App verwenden

  - Sie führen den Befehl **Update-SiteMailbox** aus

  - Sie öffnen das Fenster "Outlook Web App-Optionen" und klicken dann auf der Seite **Synchronisierungsstatus** für das ausgewählte Websitepostfach auf die Schaltfläche **Synchronisierung starten**

Weitere Informationen zum Cmdlet "Update-SiteMailbox" finden Sie unter: [Update-SiteMailbox](https://technet.microsoft.com/de-de/library/jj218690\(v=exchg.150\))

Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Der Dienst für die Synchronisierungsüberwachung löst normalerweise einen Alarm aus, wenn es zu websiteweiten Synchronisierungsproblemen kommt. Schlägt nur die Synchronisierung eines einzelnen Websitepostfachs fehl, wird kein Alarm gesendet. Um die Ursache für einen den Schwellenwert überschreitenden Alarm für ein einzelnes Websitepostfach zu bestimmen, empfiehlt es sich, die Synchronisierungsprotokolldateien des Websitepostfachs zu überprüfen.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des SiteMailbox-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "SiteMailbox"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.

## Schritte zur Problembehandlung

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Uhrzeit und Datum des Auftretens der Warnung

  - Verwendeter Authentifizierungsmechanismus und Anmeldeinformationen

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen  
    
    **Hinweis**   Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt.

**Fehler bei der Hintergrundsynchronisierung**

Wenn der Hintergrundsynchronisierungsprozess fehlschlägt, erhalten Sie möglicherweise eine Warnung, die der folgenden ähnelt:

Fehler bei der Hintergrundsynchronisierung für das Websitepostfach. Mindestens 25 %: 41 Fehler von 87 Versuchen. Beispielsynchronisierungsergebnis:

\[Meldung: Der Remoteserver hat einen Fehler zurückgegeben: (401) Nicht autorisiert.\]\[Typ:System.Net.WebException\]

Diese Warnung wird ausgelöst, wenn ein konsistent hoher Prozentsatz von Synchronisierungsfehlern während der vorherigen vier Stunden aufgetreten ist. Zur Vermeidung falsch negativer Meldungen wird eine Warnung nur dann gesendet, wenn die folgenden Bedingungen während der vorherigen vier Stunden innerhalb eines 15-Minuten-Fensters erfüllt wurden:

  - Mindestens 20 Fehler treten innerhalb eines 15-Minuten-Fensters auf.

  - Der Prozentsatz von Fehlern im Vergleich zur Gesamtanzahl der Versuche überschreitet 25 % innerhalb eines 15-Minuten-Fensters.

Jedes Websitepostfach in Exchange ist mit einer SharePoint-Website verknüpft. Für jedes der Websitepostfächer auf einem vorgegebenen Exchange-Server, auf dem die Postfachrolle gehostet wird, synchronisiert der Server websitepostfachbezogene Informationen von SharePoint.

Zwei Arten von Synchronisierungen erfolgen während dieses Prozesses: Mitgliedschaftssynchronisierung und Dokumentensynchronisierung. Die Metadaten für diese Synchronisierungsprozesse stammen aus verschiedenen Webdiensten. Darüber hinaus kann ein vorgegebener Exchange-Server Websitepostfächer enthalten, die mit mehreren SharePoint-Servern oder -Farmen verknüpft sind. Deshalb kann die Warnung in Abhängigkeit von den folgenden Bedingungen von mehreren Postfachservern stammen:

1.  Art der Verteilung von aktiv verwendeten Websitepostfächern in der Organisation

2.  Die SharePoint-Server, mit denen die aktiv verwendeten Websitepostfächer verknüpft sind

3.  Ob der Postfachserver über ausreichendes Synchronisierungsvolumen zur Einhaltung der Alarmschwellenwerte verfügt

Um bei der Behebung dieses Problems zu helfen, kann das in der Warnung enthaltene Beispielsynchronisierungsergebnis herangezogen werden, um die Ursache des Fehlers zu bestimmen. Details zum Erfolg oder Fehlschlagen jedes Synchronisierungsversuchs werden im Ordner "*\<Installationsverzeichnis von exExchangeSvrNoVersion\>*Logging\\TeamMailbox" aufgezeichnet. Überprüfen Sie die jüngsten "Microsoft.Exchange.ServiceHost\_TeamMailboxSyncLog\*"-Dateien auf Fehler, indem Sie nach dem Begriff **failed** suchen. Für eine weiter gehende Problembehandlung können Sie auch die Cmdlets **Test-OAuthConnectivity**, **Test-SiteMailbox** und **Get-SiteMailboxDiagnostics** verwenden.

**Der MSExchangeServiceHost-Dienst wird nicht ausgeführt**

Wenn der MSExchangeServiceHost-Dienst nicht ausgeführt wird, erhalten Sie eine Warnung, die der folgenden ähnelt:

Der Dienst 'MSExchangeServiceHost' wird nach den Wiederherstellungsversuchen nicht ausgeführt. Der Dienst ist möglicherweise deaktiviert oder in einer Absturzschleife.

Überprüfen Sie zur Behebung dieses Problems, ob der MSExchangeServiceHost-Dienst auf dem Server ausgeführt wird, von dem die Warnung gesendet wurde. Wenn der Dienst ausgeführt wird, überprüfen Sie die Windows-Ereignisprotokolle auf Hinweise für die Ursache, warum der Dienst zuvor eventuell nicht ausgeführt wurde, beispielsweise manuelle Dienststeuerung oder wiederholte Abstürze des Diensts.

**Der MSExchangeServiceHost-Dienst ist abgestürzt**

Wenn der MSExchangeServiceHost-Dienst abstürzt, erhalten Sie eine Warnung, die der folgenden ähnelt:

Der MSExchangeServiceHost-Prozess ist mindestens 3-mal in den letzten 60 Minuten abgestürzt.  
Watson-Meldung:

\<*Meldung*\>

Überprüfen Sie zur Behebung dieses Problems das Windows-Anwendungsereignisprotokoll auf dem Server, von dem die Warnung für **4999** hinsichtlich des MSExchangeServiceHost-Diensts gesendet wurde. Der Text der Details kann Informationen zur Ursache des Problems enthalten.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

[Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

