---
title: Problembehandlung beim OWA-Integritätssatz
TOCTitle: Problembehandlung beim OWA-Integritätssatz
ms:assetid: eae9dbd7-2ce6-43ce-b9a1-b114fd0c3ab4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.owa(v=EXCHG.150)
ms:contentKeyID: 53181877
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim OWA-Integritätssatz

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit dem Outlook Web App-Integritätssatz (OWA) wird die Gesamtintegrität des Outlook Web App-Diensts überwacht.

Wenn Sie eine Warnung erhalten, dass Integritätsfehler in Outlook Web App vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe von Outlook Web App hindert.

## Erläuterung

Der Outlook Web App-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Test</th>
<th>Integritätssatz</th>
<th>Abhängigkeiten</th>
<th>Zugehörige Monitore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OwaCtpProbe</p></td>
<td><p>Outlook Web App</p></td>
<td><p>Active Directory</p>
<p>Informationsspeicher</p></td>
<td><p>OwaCtpMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Bei diesem Test kann aus mehreren Gründen ein Fehler auftreten. Im Folgenden finden Sie einige der häufigeren Ursachen:

  - Der Outlook Web App-Anwendungspool, der auf dem überwachten Clientzugriffsserver gehostet wird, reagiert nicht, oder der Anwendungspool, der auf dem Postfachserver gehostet wird, reagiert nicht.

  - Der Clientzugriffsserver hat Netzwerkprobleme und kann keine Verbindung mit dem Postfachserver oder dem Domänencontroller herstellen.

  - Die Anmeldeinformationen des Überwachungskontos sind fehlerhaft.

  - Die Datenbank des Benutzers ist nicht eingebunden, oder dieses Postfach hat keinen Zugriff auf den Informationsspeicher.

  - Der Informationsspeicher reagiert nicht.

  - Die Domänencontroller reagieren nicht.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung generiert wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des Outlook Web App-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "OWA"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Um beispielsweise einen Test zur Überwachung von Exchange ActiveSync auf *server1.contoso.com* zu erstellen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe -Identity ActiveSync.Protocol\ActiveSyncSelfTestProbe -Server server1.contoso.com
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## OwaCtpMonitor-Wiederherstellungsaktionen

Eine E-Mail-Warnung von einem Integritätssatz enthält die folgenden Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen  
    
    **Hinweis**   Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt. Beispielsweise enthält die Ausnahme Folgendes:
    
      - **MissingKeyword**   Ein erwartetes Schlüsselwort wurde nicht in der Serverantwort gefunden. In diesem Fall enthält die Ausnahme die erwarteten Schlüsselwörter.
    
      - **NameResolution**   Die DNS-Auflösung kann einen angegebenen Servernamen nicht auflösen.
    
      - **NetworkConnection**   Der Test empfängt einen Netzwerkverbindungsfehler bei dem Versuch, eine Verbindung mit dem OWA-Anwendungspool auf dem Clientzugriffsserver herzustellen.
    
      - **UnexpectedHttpResponseCode**   Antwort hatte einen unerwarteten HTTP-Code. Beispielsweise hat der Server einen HTTP-Code **503** zurückgegeben.
    
      - **RequestTimeout**   Die Antwort des Servers auf eine Clientanforderung hat zu lange gedauert.
    
      - **ScenarioTimeout**   Der Test wurde erfolgreich fertig gestellt, hat hierfür aber länger als eine Minute benötigt. Dies weist in der Regel auf ein System hin, das überlastet ist.
    
      - **OwaErrorPage**Outlook Web App hat eine Fehlerseite zurückgegeben. Der Name des Fehlers, von dem das Fehlschlagen verursacht wurde, findet sich normalerweise in der Ausnahmemeldung.
    
      - **OwaMailboxErrorPage**Outlook Web App hat eine Fehlerseite zurückgegeben, die einen postfachspeicherbezogenen Fehler enthält. Dies weist normalerweise darauf hin, dass der Postfachspeicher nicht verfügbar ist oder dass die Einbindung von Postfächern aufgehoben wird.
    
    Die Ausnahmeablaufverfolgung enthält ein wichtiges Feld namens **FailingComponent**. Der Test versucht, wie in dem folgenden Beispiel, den Fehler zu bestimmen:
    
      - **Mailbox**   Der Test kann eine Verbindung mit Outlook Web App, aber nicht mit dem Postfachspeicher herstellen. In diesem Fall tritt beim Test ein Fehler auf, oder die Wartezeit des Postfachzugriffs führt zum Fehlschlagen des Tests, weshalb dieser einen **ScenarioTimeout**-Fehler generiert. Wenn diese Fehlerarten auftreten, sollten Sie die Integrität des Postfachservers überprüfen.
    
      - **Active Directory**   Der Test kann eine Verbindung mit Outlook Web App, aber nicht mit Active Directory herstellen. In diesem Fall schlägt der Test fehl, oder die Wartezeiten von Active Directory-Aufrufen haben möglicherweise zu einem Timeout des Tests geführt. Wenn diese Fehlerarten auftreten, sollten Sie die Integrität der Domänencontroller sowie die Netzwerkverbindungen zwischen den Clientzugriffs- und Postfachservern sowie den Domänencontrollern überprüfen.
    
      - **Owa**   Dies bedeutet normalerweise, dass ein Fehler in der Outlook Web App-Schicht aufgetreten ist. Wenn diese Fehlerarten auftreten, müssen Sie die Integrität des Outlook Web App-Prozesses auf den Clientzugriffs- und Postfachservern sowie die Netzwerkverbindungen überprüfen.
    
    Die Ausnahme enthält außerdem Informationen zur aktuellen HTTP-Anforderung und -Antwort, die vor dem Fehlschlagen des Tests empfangen wurde. Der Eskalationstext enthält den Pfad zu Testprotokollen. Mithilfe dieser Informationen können Sie die vollständigen HTTP-Webanforderungen und -antworten bestimmen, die zum Zeitpunkt des Fehlschlagens des Tests gesendet wurden. Diese Datei enthält nur Daten zu fehlgeschlagenen Tests, weil nur fehlgeschlagene Versuche protokolliert werden. Mithilfe dieser Informationen können Sie sich einen umfassenderen Überblick über die möglichen Ursachen für das Fehlschlagen des Tests verschaffen.

  - Die Stärke des Abfalls der Verfügbarkeitsmetrik (x %).

  - Der vollständige Pfad zu dem Ordner, der die vollständigen HTTP-Anforderungsablaufverfolgungen für den Test enthält. Standardmäßig befinden sich diese Informationen im Ordner "*\<Exchange-Server\>*\\Logging\\Monitoring\\OWA\\ClientAccessProbe".

  - Uhrzeit und Datum des Auftretens der Warnung.

Führen Sie zum Behandeln dieses Problems die folgenden Schritte aus:

1.  Erstellen Sie ein Testbenutzerkonto, und melden Sie sich dann beim Clientzugriffsserver an, indem Sie das Testbenutzerkonto verwenden. Melden Sie sich beispielsweise über die URL "https://*\<Servername\>*/owa" an.
    
    Sollte dies fehlschlagen, testen Sie es mit einem anderen Clientzugriffsserver, um zu überprüfen, ob das Problem auf einem bestimmten Clientzugriffsserver auftritt und nicht auf dem Postfachserver.

2.  Überprüfen Sie die Netzwerkkonnektivität zwischen den Clientzugriffs- und Postfachservern. Verwenden Sie "ping.exe", um zu überprüfen, ob jeder Server antwortet.

3.  Überprüfen Sie den OWA.Protocol-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Postfachserver betrifft. Weitere Informationen finden Sie unter [Problembehandlung beim OWA.Protocol-Integritätssatz](troubleshooting-owa-protocol-health-set.md).

4.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu überprüfen, ob der Anwendungspool "MSExchangeOwaAppPool" auf dem Clientzugriffsserver ausgeführt wird.

5.  Überprüfen Sie im IIS-Manager, ob die Standardwebsite ausgeführt wird.

6.  Suchen Sie die Postfachdatenbank für fehlgeschlagene Tests, und überprüfen Sie, ob die Postfachdatenbank auf einem Postfachserver aktiv und ob der Postfachspeicher fehlerfrei ist. Öffnen Sie zum Auffinden der GUID-Informationen der Fehlerdatenbank die Informationen der vollständigen Ausnahmeablaufverfolgung. Für jeden Fehler sollte ein Eintrag vorhanden sein, der folgendem Beispiel ähnelt:
    
    OWA-Test mit Ziel beginnen: https://localhost/owa/, Benutzername: *HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com*

7.  Kopieren Sie die HealthMailbox-GUID, und führen Sie dann den folgenden Befehl in der Shell aus:
    
        Get-Mailbox -Monitoring -Identity <username>
    
    Führen Sie beispielsweise den folgenden Befehl aus:
    
        Get-Mailbox -Monitoring -Identity HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com
    
    Im zurückgegebenen Objekt können Sie den Namen der Benutzerdatenbank finden und bestimmen, wo sich die aktuell aktive Datenbank befindet.

8.  Wenn Sie die Umleitung zwischen Standorten konfiguriert haben, schlagen Tests eventuell fehl und generieren einen MissingKeyword-Fehler. Hierzu kommt es, weil Clientzugriffsserver-Tests standardmäßig mit Konten für jeden Ort ausgeführt werden, und auch, weil der Test nicht versucht, einen Clientzugriffsserver an einem anderen Standort zu testen, wenn dieser Umleitung verwendet. Stellen Sie zur Behebung dieses Problems sicher, dass die Server an jedem Standort in MonitoringGroups enthalten sind. Clientzugriffsserver in einer bestimmten Überwachungsgruppe werden nur zusammen mit Postfachservern aus derselben Gruppe getestet.
    
    Um die Überwachungsgruppen für Ihre Server zu bestimmen, führen Sie den folgenden Befehl aus:
    
        Get-ExchangeServer | ft MonitoringGroup
    
    Um die Überwachungsgruppe auf einem Server zu ändern, verwenden Sie den Parameter *MonitoringGroup* zusammen mit dem Cmdlet **Set-ExchangeServer**. Verwenden Sie beispielsweise Folgendes:
    
        Set-ExchangeServer -Identity "ServerName" -MonitoringGroup "Primary"

9.  Klicken Sie im IIS-Manager auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeOWAAppPool** neu, indem Sie in der Exchange-Verwaltungsshell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeOWAAppPool

10. Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

11. Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden oder den folgenden Befehl ausführen:
    
        Iisreset /noforce

12. Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

13. Wenn das Problem weiterhin besteht, starten Sie den Server neu.

14. Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

15. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

[Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

