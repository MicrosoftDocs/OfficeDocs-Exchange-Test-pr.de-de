---
title: Problembehandlung beim ActiveSync-Integritätssatz
TOCTitle: Problembehandlung beim ActiveSync-Integritätssatz
ms:assetid: 8a0b8b26-b4ef-41b8-8f71-8271c1735a69
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.activesync(v=EXCHG.150)
ms:contentKeyID: 53181865
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim ActiveSync-Integritätssatz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit dem Exchange ActiveSync-Integritätssatz wird die Gesamtintegrität des ActiveSync-Diensts für mobile Clients in Ihrer Organisation überwacht. Der ActiveSync-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

[Problembehandlung beim ActiveSync.Protocol-Integritätssatz](troubleshooting-activesync-protocol-health-set.md)

[Problembehandlung beim ActiveSync.Proxy-Integritätssatz](troubleshooting-activesync-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im ActiveSync-Integritätssatz vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe von ActiveSync hindert.

## Erläuterung

Der ActiveSync-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>ActiveSyncCTPProbe</p></td>
<td><p>ActiveSync</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Postfachserverauthentifizierung</p>
<p>Informationsspeicher</p>
<p>Hochverfügbarkeit</p>
<p>Netzwerk</p></td>
<td><p>ActiveSyncCTPMonitor (ActiveSync-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>ActiveSyncProxyTestProbe</p></td>
<td><p>ActiveSync.Proxy</p></td>
<td><p>-</p></td>
<td><p>ActiveSyncProxyTestMonitor (ActiveSync.Proxy-Integritätssatz)</p></td>
</tr>
<tr class="odd">
<td><p>ActiveSyncDeepTestProbe</p></td>
<td><p>ActiveSync.Protocol</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Informationsspeicher</p>
<p>Hochverfügbarkeit</p></td>
<td><p>ActiveSyncDeepTestMonitor (ActiveSync-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>ActiveSyncSelfTestProbe</p></td>
<td><p>ActiveSync.Protocol</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p></td>
<td><p>ActiveSyncSelfTestMonitor (ActiveSync.Protocol-Integritätssatz)</p>
<p>RequestsQueuedGt500Monitor (ActiveSync-Integritätssatz)</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im ActiveSync-Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Problems

1.  Identifizieren Sie den Namen des Integritätssatzes sowie den Servernamen, die in der Warnung angegeben sind.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des ActiveSync-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "ActiveSync"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet **Unhealthy**.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **ActiveSyncCTPMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **ActiveSyncCTPProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe ActiveSync\ActiveSyncCTPProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Abschnitt "Ergebnis" des Tests. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## ActiveSyncDeepTestMonitor- und ActiveSyncSelfTestMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Postfachservern ausgegeben. Führen Sie zum Ausführen von Wiederherstellungsaktionen die folgenden Schritte aus:

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird. Klicken Sie auf **Anwendungspools**, und starten Sie den ActiveSync-Anwendungspool mit dem Namen **MSExchangeSyncAppPool** neu.

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn das Problem weiterhin besteht, starten Sie den gesamten IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

4.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

5.  Wenn das Problem weiterhin besteht, starten Sie den Server neu. Führen Sie hierzu zuerst ein Failover der Datenbanken durch, die auf dem Server gehostet sind, indem Sie den folgenden Befehl verwenden:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $true
    
    In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.

6.  Als Nächstes überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
    
        Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status

7.  Wenn die Ausgabe des Befehls in Schritt 6 keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu. Werden in der Ausgabe noch aktive Kopien angezeigt, führen Sie die Schritte 5 und 6 erneut aus.

8.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

9.  Ist der Test erfolgreich, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

10. Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## ActiveSyncCTPMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffsservern ausgegeben.

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird. Klicken Sie auf **Anwendungspools**, und verwenden Sie den ActiveSync-Anwendungspool mit dem Namen **MSExchangeSyncAppPool** wieder.

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn das Problem weiterhin besteht, starten Sie den gesamten IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

4.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

5.  Wenn das Problem weiterhin besteht, müssen Sie den Integritätsstatus auf dem entsprechenden Postfachserver überprüfen. Der Name des Postfachservers ist der `_Mbx:`-Wert, der in der Fehlermeldung angegeben ist.
    
    1.  Führen Sie den folgenden Befehl für den entsprechenden Postfachserver aus. Führen Sie beispielsweise den folgenden Befehl für einen Postfachserver namens "mailbox1.contoso.com" aus:
        
            Get-ServerHealth mailbox1.contoso.com | ?{$_.HealtSetName -like "ActiveSync*"}
    
    2.  Wenn für in der Befehlsausgabe aufgeführte Monitore Integritätsfehler gemeldet sind, müssen Sie zuerst diese Monitore behandeln. Führen Sie hierzu die Schritte zur Problembehandlung aus, die im Abschnitt ActiveSyncDeepTestMonitor- und ActiveSyncSelfTestMonitor-Wiederherstellungsaktionen beschrieben sind.

6.  Wenn alle Monitore auf dem Postfachserver fehlerfrei sind, starten Sie den Clientzugriffsserver neu.

7.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Problems in Schritt 2c gezeigt, erneut aus.

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## RequestsQueuedGt500Monitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffsservern ausgegeben.

1.  Starten Sie den IIS-Manager, und stellen Sie eine Verbindung mit dem Server her, von dem das Problem gemeldet wird. Klicken Sie auf **Anwendungspools**, und verwenden Sie den ActiveSync-Anwendungspool mit dem Namen **MSExchangeSyncAppPool** wieder.

2.  Warten Sie 10 Minuten, um zu sehen, ob der Monitor fehlerfrei bleibt. Führen Sie nach 10 Minuten den folgenden Befehl für den entsprechenden Server aus. Führen Sie beispielsweise den folgenden Befehl für "server1.contoso.com" aus:
    
        Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -like "ActiveSync*"}

3.  Wenn das Problem weiterhin besteht, starten Sie den gesamten IIS-Dienst neu, indem Sie das Hilfsprogramm "IISReset" verwenden.

4.  Warten Sie 10 Minuten, und führen Sie dann den in Schritt 2 gezeigten Befehl erneut aus, um zu überprüfen, ob der Monitor fehlerfrei bleibt.

5.  Wenn das Problem weiterhin besteht, starten Sie den Server neu. Ist der Server ein Clientzugriffsserver, brauchen Sie den Server nur neu zu starten. Ist der Server ein Postfachserver, gehen Sie wie folgt vor:
    
    1.  Führen Sie ein Failover der Datenbanken durch, die auf dem Server gehostet sind. Führen Sie dazu den folgenden Befehl aus:
        
            Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $true
        
        **Hinweis**   In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.
    
    2.  Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
        
            Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status
        
        Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu.

6.  Warten Sie nach dem Neustart des Servers 10 Minuten, und führen Sie dann den in Schritt 2 gezeigten Befehl erneut aus, um zu bestimmen, ob der Monitor fehlerfrei bleibt.

7.  Bleibt der Monitor fehlerfrei, und handelt es sich um einen Postfachserver, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Exchange ActiveSync](https://technet.microsoft.com/de-de/library/aa998357\(v=exchg.150\))

[Mobile Geräte](https://technet.microsoft.com/de-de/library/bb232129\(v=exchg.150\))

[Verwaltungstasks für virtuelle Exchange ActiveSync-Verzeichnisse](https://technet.microsoft.com/de-de/library/bb125170\(v=exchg.150\))

