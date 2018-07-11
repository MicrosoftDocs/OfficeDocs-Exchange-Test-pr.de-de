---
title: Problembehandlung beim OWA.Protocol-Integritätssatz
TOCTitle: Problembehandlung beim OWA.Protocol-Integritätssatz
ms:assetid: fe172da8-65d3-43e0-ba62-d36a1b05fc11
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.owa.protocol(v=EXCHG.150)
ms:contentKeyID: 53181880
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim OWA.Protocol-Integritätssatz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem OWA.Protocol-Integritätssatz wird das Outlook Web App-Protokoll auf dem Postfachserver überwacht.

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im OWA.Protocol vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe von Outlook Web App hindert.

## Erläuterung

Der OWA-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>OwaSelfTestProbe</p></td>
<td><p>OWA.Protocol</p></td>
<td><p>Keine</p></td>
<td><p>OwaSelfTestMonitor</p></td>
</tr>
<tr class="even">
<td><p>OwaDeepTestProbe</p></td>
<td><p>OWA.Protocol</p></td>
<td><p>Active Directory</p>
<p>Informationsspeicher</p></td>
<td><p>OwaDeepTestMonitor</p></td>
</tr>
</tbody>
</table>


Der Test **OwaSelfTestProbe** sendet eine einzelne HTTP-Anforderung an folgende Adresse: https://localhost:444/owa/exhealth.check. Der Test bestätigt, dass der Anwendungspool reagiert, indem der Statuscode **200 OK** zurückgegeben wird. Für diesen Test besteht keine Abhängigkeit von einer anderen Exchange-Komponente.

Der Test **OwaDeepTestProbe** wird für jede Postfachdatenbank ausgeführt, indem Kopien auf dem aktuellen Server verwendet werden. Der Test bestimmt, ob eine vollständige Anmeldung beim Server durchgeführt werden kann. Hierzu wird die Art von Datenverkehr simuliert, die von einem Clientzugriffsserver auf diesem spezifischen Server generiert wird. Der Test ist bei der Authentifizierung von den Active Directory-Domänendiensten (AD DS) abhängig und beim Postfachzugriff vom Postfachspeicher. Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Bei diesem Test kann aus einer der folgenden häufigen Ursachen ein Fehler auftreten:

  - Der OWA-Anwendungspool, der auf dem überwachten Clientzugriffsserver gehostet wird, reagiert nicht, oder der Anwendungspool, der auf dem Postfachserver gehostet wird, reagiert nicht.

  - Der Clientzugriffs- oder Postfachserver hat Netzwerkprobleme und kann keine Verbindung mit dem anderen Server oder mit einem Domänencontroller herstellen.

  - Die Anmeldeinformationen des Überwachungskontos sind fehlerhaft.

  - Die Datenbank des Benutzers ist nicht eingebunden, oder dieses Postfach hat keinen Zugriff auf den Informationsspeicher.

  - Der Informationsspeicher reagiert nicht.

  - Die Domänencontroller reagieren nicht.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des OWA.Protocol-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "OWA.Protocol"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **OwaSelfTestMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **OwaSelfTestProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe OWA.Protocol\OwaSelfTestProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Art des Tests, der fehlgeschlagen ist (SelfTest oder DeepTest)

  - Uhrzeit und Datum des Auftretens der Warnung

  - Pfad zu dem Ordner, in dem Sie die vollständigen HTTP-Anforderungsablaufverfolgungen für den Test finden können
    
      
    Standardmäßig befinden sich die Ablaufverfolgungsdateien in den folgenden Ordnern:
    
      - SelfTestProbe: \<*ExchangeServer*\>\\Logging\\Monitoring\\OWA\\ProtocolProbe
    
      - DeepTestProbe: \<*ExchangeServer*\>\\Logging\\Monitoring\\OWA\\MailboxProbe

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen  
    
    **Hinweis**   Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt. Die Fehlerursache kann eine der folgenden sein:
    
      - **MissingKeyword**   Ein erwartetes Schlüsselwort wurde nicht in der Serverantwort gefunden. In diesem Fall enthält die Ausnahme die erwarteten Schlüsselwörter.
    
      - **NameResolution**   Die DNS-Auflösung kann einen angegebenen Servernamen nicht auflösen.
    
      - **NetworkConnection**   Der Test empfängt einen Netzwerkverbindungsfehler bei dem Versuch, eine Verbindung mit dem OWA-Anwendungspool auf dem Clientzugriffsserver herzustellen.
    
      - **UnexpectedHttpResponseCode**   Die Antwort hat einen unerwarteten HTTP-Code enthalten. Beispielsweise hat der Server einen HTTP-Code **503** zurückgegeben.
    
      - **RequestTimeout**   Die Antwort des Servers auf eine Clientanforderung hat zu lange gedauert.
    
      - **UnexpectedHttpResponseCode**   Die Antwort hat einen unerwarteten HTTP-Code zurückgegeben. Beispielsweise hat der Server einen HTTP-Code **503** zurückgegeben.
    
      - **ScenarioTimeout**   Der Test wurde erfolgreich fertig gestellt, hat hierfür aber länger als eine Minute benötigt. Dies weist in der Regel auf ein System hin, das überlastet ist.
    
      - **OwaErrorPage**   OWA hat eine Fehlerseite zurückgegeben. Der Name des Fehlers, von dem das Fehlschlagen verursacht wurde, findet sich normalerweise in der Ausnahmemeldung.
    
      - **OwaMailboxErrorPage**   OWA hat eine Fehlerseite zurückgegeben, die einen postfachspeicherbezogenen Fehler enthält. Dies weist normalerweise darauf hin, dass der Postfachspeicher nicht verfügbar ist oder dass die Einbindung von Postfächern aufgehoben wird.
    
    Die Ausnahmeablaufverfolgung enthält ein wichtiges Feld namens **FailingComponent**, in dem von dem Test der Versuch unternommen wird, den Fehler zu bestimmen und zu kategorisieren. Beispielsweise kann der Test einen der folgenden Werte zurückgeben:
    
      - **Postfach**   Der Test kann eine Verbindung mit OWA, aber nicht mit dem Postfachspeicher herstellen. In diesem Fall tritt beim Test ein Fehler auf, oder die Wartezeit des Postfachzugriffs führt zum Fehlschlagen des Tests, weshalb dieser einen **ScenarioTimeout**-Fehler generiert. Wenn diese Fehlerarten auftreten, sollten Sie die Integrität des Postfachservers überprüfen.
    
      - **Active Directory**   Der Test kann eine Verbindung mit OWA, aber nicht mit den AD DS herstellen. In diesem Fall schlägt der Test fehl, oder die Wartezeiten von AD DS-Aufrufen führen zu einem Timeout des Tests. Wenn diese Fehlerarten auftreten, sollten Sie die Integrität der Domänencontroller sowie die Netzwerkverbindungen zwischen den Clientzugriffs- und Postfachservern sowie den Domänencontrollern überprüfen.
    
      - **OWA**   Dies bedeutet normalerweise, dass ein Fehler in der OWA-Schicht aufgetreten ist. Wenn diese Fehlerarten auftreten, müssen Sie die Integrität des OWA-Prozesses auf den Clientzugriffs- und Postfachservern sowie die Netzwerkverbindungen überprüfen.
    
    Die Ausnahme enthält außerdem Informationen zur aktuellen HTTP-Anforderung und -Antwort, die vor dem Fehlschlagen des Tests empfangen wurde.  
      
    Der Eskalationstext enthält den Pfad zu den Testprotokollen, mit deren Hilfe Sie die vollständigen HTTP-Webanforderungen und -antworten überprüfen können, die zum Zeitpunkt des Fehlschlagens des Tests gesendet wurden. Diese Datei enthält nur Daten zu fehlgeschlagenen Tests, weil nur fehlgeschlagene Versuche protokolliert werden. Mithilfe dieser Informationen können Sie sich einen umfassenderen Überblick über die möglichen Ursachen für das Fehlschlagen des Tests verschaffen.

## OwaSelfTestProbe-Wiederherstellungsaktionen

Da dieser Test nur wenige Abhängigkeiten besitzt, treten Fehler normalerweise auf, wenn der OWA-Anwendungspoolprozess nicht reagiert.

Führen Sie zum Behandeln dieses Problems die folgenden Schritte aus:

1.  Klicken Sie im Nachrichtentext der E-Mail-Warnung auf die Ablaufverfolgungsprotokoll-URL des Tests, um zu überprüfen, ob neue Fehler auftreten.

2.  Erstellen Sie auf demselben Server, auf dem das Postfach eingebunden ist, ein Testbenutzerkonto. Versuchen Sie, sich anzumelden, um festzustellen, ob das Problem reproduziert werden kann.

3.  Überprüfen Sie den OWA-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Postfachserver betrifft. Weitere Informationen finden Sie unter [Problembehandlung beim OWA-Integritätssatz](troubleshooting-owa-health-set.md).

4.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu bestimmen, ob der Anwendungspool **MSExchangeOwaAppPool** auf dem Clientzugriffsserver ausgeführt wird.

5.  Überprüfen Sie im IIS-Manager, ob die Standardwebsite ausgeführt wird.

6.  Klicken Sie im IIS-Manager auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeOWAAppPool** neu, indem Sie in der Exchange-Verwaltungsshell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeOWAAppPool

7.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

8.  Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden oder den folgenden Befehl ausführen:
    
        Iisreset /noforce

9.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

10. Wenn das Problem weiterhin besteht, starten Sie den Server neu.

11. Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

12. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## OwaDeepTestProbe-Wiederherstellungsaktionen

1.  Um zu bestimmen, ob das Problem noch besteht, erstellen Sie auf demselben Server, auf dem das Postfach eingebunden ist, ein Testbenutzerkonto, und versuchen dann, sich bei OWA anzumelden. Melden Sie sich beispielsweise über folgende URL an: https://*\<Servername\>*/owa.

2.  Überprüfen Sie den OWA-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Postfachserver betrifft. Weitere Informationen finden Sie unter [Problembehandlung beim OWA-Integritätssatz](troubleshooting-owa-health-set.md).

3.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird, um zu bestimmen, ob der Anwendungspool **MSExchangeOwaAppPool** auf dem Clientzugriffsserver ausgeführt wird.

4.  Überprüfen Sie im IIS-Manager, ob die Standardwebsite ausgeführt wird.

5.  Suchen Sie die Postfachdatenbank für fehlgeschlagene Tests, und überprüfen Sie, ob die Postfachdatenbank auf dem Postfachserver aktiv und ob der Postfachspeicher fehlerfrei ist. Öffnen Sie zum Auffinden der GUID-Informationen der Fehlerdatenbank die Informationen der vollständigen Ausnahmeablaufverfolgung. Für jeden Fehler sollte ein Eintrag vorhanden sein, der folgendem Beispiel ähnelt:
    
    `Starting Owa probe with Target: https://localhost/owa/, Username:  HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com`

6.  Kopieren Sie die HealthMailbox-GUID, und führen Sie dann den folgenden Befehl in der Shell aus:
    
        Get-Mailbox -Monitoring -Identity <username>
    
    Führen Sie beispielsweise den folgenden Befehl aus:
    
        Get-Mailbox -Monitoring -Identity HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com
    
    Im zurückgegebenen Objekt können Sie den Namen der Benutzerdatenbank finden und bestimmen, wo sich die aktuell aktive Datenbank befindet.

7.  Klicken Sie im IIS-Manager auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeOWAAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeOWAAppPool

8.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

9.  Wenn das Problem weiterhin besteht, starten Sie den IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden oder den folgenden Befehl ausführen:
    
        Iisreset /noforce

10. Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

11. Wenn das Problem weiterhin besteht, starten Sie den Server neu.

12. Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

13. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Neuerungen in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150540\(v=exchg.150\))

[Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

