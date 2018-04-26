---
title: Problembehandlung beim POP-Integritätssatz
TOCTitle: Problembehandlung beim POP-Integritätssatz
ms:assetid: 6114e9fe-d037-4cb9-a643-933eb5fabc45
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.pop(v=EXCHG.150)
ms:contentKeyID: 53181862
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim POP-Integritätssatz

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit dem POP-Integritätssatz werden die Gesamtintegrität und Verfügbarkeit des Microsoft Exchange-POP3-Diensts sowie die POP3-Clientkonnektivität überwacht. Der POP-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

  - [Problembehandlung beim POP.Protocol-Integritätssatz](troubleshooting-pop-protocol-health-set.md)

  - [Problembehandlung beim POP.Proxy-Integritätssatz](troubleshooting-pop-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im POP-Dienst vorliegen, weist dies auf ein Problem hin, das Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe von POP3 in der Exchange-Umgebung hindert.

## Erläuterung

Der POP-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>PopCTPProbe</p></td>
<td><p>POP</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Postfachserverauthentifizierung</p>
<p>Informationsspeicher</p>
<p>Hochverfügbarkeit</p>
<p>Netzwerk</p></td>
<td><p>PopCTPMonitor (POP-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>PopProxyTestProbe</p></td>
<td><p>POP.Proxy</p></td>
<td><p>Keine</p></td>
<td><p>PopProxyTestMonitor (POP.Proxy-Integritätssatz)</p></td>
</tr>
<tr class="odd">
<td><p>PopDeepTestProbe</p></td>
<td><p>POP.Protocol</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Informationsspeicher</p>
<p>Hochverfügbarkeit</p></td>
<td><p>PopDeepTestMonitor (POP.Protocol-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>PopSelfTestProbe</p></td>
<td><p>POP.Protocol</p></td>
<td><p>Keine</p></td>
<td><p>PopSelfTestMonitor (POP.Protocol-Integritätssatz)</p>
<p>AverageCommandProcessingTimeGt60sMonitor (POP-Integritätssatz)</p></td>
</tr>
</tbody>
</table>


## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des POP-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "POP"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **PopCTPMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **PopCTPProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe POP\PopCTPProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## PopTestDeepMonitor- und PopSelfTestMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Postfachservern ausgegeben.

1.  Starten Sie den POP3-Back-End-Dienst neu. Weitere Informationen finden Sie unter [Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\)).

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn der Test weiterhin fehlschlägt, führen Sie ein Failover der Datenbanken durch, die auf dem Postfachserver gehostet sind, indem Sie den folgenden Befehl verwenden:
    
        Set-MailboxServer -Identity <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $true

4.  Nachdem alle Datenbanken vom Postfachserver entfernt wurden, müssen Sie überprüfen, ob die Datenbanken erfolgreich verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
    
        Get-MailboxDatabaseCopyStatus -Server <ServerName> | group status

5.  Stellen Sie sicher, dass der Server keine aktiven Kopien der Datenbank mehr hostet. Starten Sie dann den Server neu.

6.  Führen Sie nach dem erfolgreichen Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

7.  Ist der Test erfolgreich, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer -Identity <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $false

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## POPCTPMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffsservern ausgegeben.

1.  Starten Sie den POP3-Dienst auf den Servern, auf denen die Clientzugriffs-Serverrolle ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\)).

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn das Problem weiterhin besteht, führen Sie die folgenden Befehle in der Windows PowerShell aus:
    
    1.  ``` 
        Set-PopSettings -server <CAS server name> -ProtocolLoggingEnabled $true
        ```
    
    2.  Starten Sie den POP3-Dienst auf den Servern, auf denen die Clientzugriffs-Serverrolle ausgeführt wird.
    
    3.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.
    
    4.  Führen Sie den folgenden Befehl aus, und suchen Sie dann den Speicherort der Protokolldatei:
        
            Get-PopSettings -server <CAS server name>
    
    5.  Führen Sie den folgenden Befehl aus, um zu bestimmen, für welches Postfach dieser Befehl ausgeführt wird, indem Sie die Zeitstempel mit dem Test vergleichen:
        
            Get-ServerHealth <mailbox server name> | ?{ $_.HealthSetName -like "POP*"}
    
    6.  Wenn für diese Server Integritätsfehler gemeldet werden, führen Sie die Schritte aus, die im Abschnitt PopTestDeepMonitor- und PopSelfTestMonitor-Wiederherstellungsaktionen aufgelistet sind.

4.  Wenn der Postfachserver als fehlerfrei gemeldet wird, starten Sie den Clientzugriffsserver neu.

5.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c beschrieben, erneut aus.

6.  Deaktivieren Sie die Protokollprotokollierung, indem Sie den folgenden Befehl ausführen:
    
        Set-PopSettings -server <CAS server name> -ProtocolLoggingEnabled $false

7.  Starten Sie den POP3-Dienst auf den Servern, auf denen die Clientzugriffs-Serverrolle ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\)).

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## PopProxyTestMonitor-Wiederherstellungsaktionen

1.  Starten Sie den POP3-Dienst auf den Servern, auf denen die Clientzugriffs-Serverrolle ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\)).

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn der Test weiterhin fehlschlägt, starten Sie den Clientzugriffsserver neu.

4.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c beschrieben, erneut aus.

5.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## AverageCommandProcessingTimeGt60sMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffs- und Postfachservern ausgegeben.

1.  Starten Sie den POP3-Dienst auf dem Clientzugriffs- oder Postfachserver neu. Weitere Informationen finden Sie unter [Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\)).

2.  Warten Sie 10 Minuten, um zu sehen, ob der Monitor fehlerfrei bleibt. Führen Sie nach 10 Minuten den folgenden Befehl aus (im Beispiel wird "server1.contoso.com" verwendet).
    
        Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -like "POP*"}

3.  Wenn das Problem weiterhin besteht, müssen Sie den Server neu starten. Ist der Server ein Clientzugriffsserver, brauchen Sie den Server nur neu zu starten. Ist der Server ein Postfachserver, müssen Sie ein Failover der Datenbank durchführen und die Ergebnisse überprüfen. Führen Sie zu diesem Zweck die folgenden Schritte aus:
    
    1.  Führen Sie ein Failover der Datenbanken durch, die auf dem Server gehostet sind, indem Sie den folgenden Befehl verwenden:
        
            Set-MailboxServer -Identity <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $true
        
        **Hinweis**   In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.
    
    2.  Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
        
            Get-MailboxDatabaseCopyStatus -Server <ServerName> | group status
        
        Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu.

4.  Warten Sie nach dem Neustart des Servers 10 Minuten, und führen Sie dann den in Schritt 2 gezeigten Befehl erneut aus, um zu bestimmen, ob der Monitor fehlerfrei bleibt.

5.  Ist der Monitor fehlerfrei, und handelt es sich um einen Postfachserver, führen Sie ein Failover der Datenbanken zurück auf den Postfachserver durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer -Identity <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $false

6.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[Starten und Beenden des POP3-Diensts](https://technet.microsoft.com/de-de/library/aa997475\(v=exchg.150\))

[Test-PopConnectivity](https://technet.microsoft.com/de-de/library/bb738143\(v=exchg.150\))

