---
title: Problembehandlung beim Autodiscover-Integritätssatz
TOCTitle: Problembehandlung beim Autodiscover-Integritätssatz
ms:assetid: bc933621-df73-4d1d-bdef-825b98be8e09
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.autodiscover(v=EXCHG.150)
ms:contentKeyID: 53181872
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim Autodiscover-Integritätssatz

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit dem Autodiscover-Integritätssatz wird die Gesamtintegrität des AutoErmittlungsdiensts für Clients überwacht.

Wenn Sie eine Warnung erhalten, dass Autodiscover-Integritätsfehler vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe des AutoErmittlungsprozesses hindert.

## Erläuterung

Der AutoErmittlungsdienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>AutodiscoverCtpProbe</p></td>
<td><p>AutoErmittlung</p></td>
<td><p>Active Directory</p></td>
<td><p>AutodiscoverCtpMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Häufige Probleme

Bei diesem Test kann aus einer der folgenden häufigen Ursachen ein Fehler auftreten:

  - Der AutoErmittlungs-Anwendungspool (MSExchangeAutodiscoverAppPool), der auf dem überwachten Clientzugriffsserver gehostet wird, reagiert nicht. Oder der AutoErmittlungs-Anwendungspool, der auf mindestens einem Postfachserver gehostet wird, reagiert nicht.

  - Der Clientzugriffsserver hat Netzwerkprobleme und kann keine Verbindung mit dem Postfachserver oder dem Domänencontroller herstellen.

  - Die Anmeldeinformationen des Überwachungskontos sind fehlerhaft.

  - Die Domänencontroller reagieren nicht.

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des Autodiscover-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "Autodiscover"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **AutodiscoverCtpMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **AutodiscoverCtpProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe Autodiscover\AutodiscoverCtpProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## AutodiscoverCtpMonitor-Wiederherstellungsaktionen

Wenn Sie eine Warnung von einem Integritätssatz erhalten, enthält die E-Mail folgende Informationen:

  - Name des Servers, von dem die Warnung gesendet wurde

  - Name des Postfachservers, der von dem Test überwacht wurde

  - Uhrzeit und Datum des Auftretens der Warnung

  - Verwendeter Authentifizierungsmechanismus und Anmeldeinformationen

  - Vollständige Ausnahmeablaufverfolgung des letzten Fehlers, einschließlich Diagnosedaten und spezifischer HTTP-Headerinformationen

Die in der vollständigen Ausnahmeablaufverfolgung enthaltenen Informationen können bei der Behandlung des Problems hilfreich sein. Die von dem Test generierte Ausnahme enthält eine Fehlerursache, die den Grund für das Fehlschlagen des Tests beschreibt. Beispielsweise kann die Fehlerursache eine der folgenden sein:

  - **X-FEServer**   Gibt an, auf welchem Clientzugriffsserver der Test ausgeführt wurde

  - **X-CalculatedBETarget**   Gibt den Postfachserver an, an den die Anforderung weitergeleitet wird

  - **X-DiagInfo**   Gibt den Postfachserver an, der die Anforderung empfangen hat

Führen Sie zum Behandeln dieses Problems die folgenden Schritte aus:

1.  Überprüfen Sie die Protokolle auf den Clientzugriffs- und Postfachservern. Standardmäßig befinden sich die Protokolle auf dem jeweiligen Clientzugriffsserver im Ordner "***\<Installationsverzeichnis des Exchange-Servers\>*\\Logging\\HttpProxy\\Autodiscover**". Standardmäßig befinden sich die Protokolldateien auf dem Postfachserver im Ordner "***\<Installationsverzeichnis des Exchange-Servers\>*\\Logging\\Autodiscover**".

2.  Erstellen Sie ein Testbenutzerkonto, und melden Sie sich dann beim Clientzugriffsserver an, indem Sie das Testbenutzerkonto verwenden. Melden Sie sich beispielsweise über folgende URL an: https://*\<Servername\>*/autodiscover/autodiscover.xml.
    
    Wenn der Name des Testbenutzerkontos akzeptiert wird, kann der Postfachserver, auf dem das überwachte Postfach gehostet wird, von einem Problem betroffen sein.
    
    Versuchen Sie, die vorherigen Schritte zu wiederholen, indem Sie ein Testkonto auf dem Postfachserver verwenden. Sollte dieser Versuch fehlschlagen, versuchen Sie, den Test mit einem anderen Clientzugriffsserver erneut auszuführen, um zu überprüfen, ob das Problem auf einem bestimmten Clientzugriffsserver auftritt und nicht auf dem Postfachserver.

3.  Überprüfen Sie die Netzwerkkonnektivität zwischen den Clientzugriffs- und Postfachservern. Verwenden Sie "ping.exe", um zu überprüfen, ob jeder Server antwortet.

4.  Überprüfen Sie den Autodiscover.Proxy-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das einen bestimmten Postfachserver betrifft. Weitere Informationen finden Sie unter [Problembehandlung beim Autodiscover.Proxy-Integritätssatz](troubleshooting-autodiscover-proxy-health-set.md).

5.  Überprüfen Sie den Autodiscover.Protocol-Integritätssatz auf Warnungen, die auf ein Problem hinweisen können, das bestimmte Postfachserver betrifft. Weitere Informationen finden Sie unter [Problembehandlung beim Autodiscover.Protocol-Integritätssatz](troubleshooting-autodiscover-protocol-health-set.md).

6.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird. Überprüfen Sie, ob der Anwendungspool **MSExchangeAutodiscoverAppPool** sowohl auf dem Clientzugriffsserver als auch auf den Postfachservern ausgeführt wird.

7.  Klicken Sie im IIS-Manager auf **Anwendungspools**, und starten Sie den Anwendungspool **MSExchangeAutodiscoverAppPool** neu, indem Sie in der Shell den folgenden Befehl ausführen:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeAutodiscoverAppPool

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

