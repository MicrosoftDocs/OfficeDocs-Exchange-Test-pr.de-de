---
title: Problembehandlung beim IMAP-Integritätssatz
TOCTitle: Problembehandlung beim IMAP-Integritätssatz
ms:assetid: 2a06e671-4cc2-4ce5-bf53-6243ea140f20
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.imap(v=EXCHG.150)
ms:contentKeyID: 53181855
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim IMAP-Integritätssatz

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Mit dem IMAP-Integritätssatz wird die Verfügbarkeit der IMAP4-Proxyinfrastruktur auf dem Clientzugriffsserver überwacht. Der IMAP-Integritätssatz steht in enger Beziehung mit den folgenden Integritätssätzen:

[Problembehandlung beim IMAP.Protocol-Integritätssatz](troubleshooting-imap-protocol-health-set.md)

[Problembehandlung beim IMAP.Proxy-Integritätssatz](troubleshooting-imap-proxy-health-set.md)

Wenn Sie eine Warnung erhalten, dass Integritätsfehler im IMAP vorliegen, weist dies auf ein Problem hin, das Ihre Benutzer eventuell am Zugriff auf ihre Postfächer mithilfe von IMAP hindert.

## Erläuterung

Der IMAP4-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>ImapCTPProbe</p></td>
<td><p>IMAP</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Postfachserverauthentifizierung</p>
<p>Hochverfügbarkeit</p>
<p>Netzwerk</p></td>
<td><p>ImapCTPMonitor (IMAP-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>ImapProxyTestProbe</p></td>
<td><p>IMAP.Proxy</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p></td>
<td><p>ImapProxyTestMonitor (IMAP.Proxy-Integritätssatz)</p></td>
</tr>
<tr class="odd">
<td><p>ImapDeepTestProbe</p></td>
<td><p>IMAP.Protocol</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p>
<p>Informationsspeicher</p>
<p>Hochverfügbarkeit</p></td>
<td><p>IMAP.Protocol (IMAP.Protocol-Integritätssatz)</p></td>
</tr>
<tr class="even">
<td><p>ImapSelfTestProbe</p></td>
<td><p>IMAP.Protocol</p></td>
<td><p>Active Directory</p>
<p>Authentifizierung</p></td>
<td><p>IMAP.Protocol (IMAP.Protocol-Integritätssatz)</p>
<p>AverageCommandProcessingTimeGt60sMonitor (IMAP-Integritätssatz)</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Überprüfen des Vorhandenseins des Problems

1.  Identifizieren des Namens des Integritätssatzes sowie des Servernamens in der Warnung.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Um beispielsweise die Details des IMAP-Integritätssatzes zu "server1.contoso.com" abzurufen, führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -like "IMAP*"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet `Unhealthy`.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt Erläuterung ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Nehmen wir beispielsweise **ImapCTPMonitor** als fehlgeschlagenen Monitor an. Der diesem Monitor zugeordnete Test ist **ImapCTPProbe**. Um diesen Test auf "server1.contoso.com" auszuführen, führen Sie den folgenden Befehl aus:
        
            Invoke-MonitoringProbe IMAP\ImapCTPProbe -Server server1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Wert von **Ergebnis** für den Test. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht. Andernfalls finden Sie Informationen in den Schritten zur Wiederherstellung, die in den folgenden Abschnitten beschrieben sind.

## ImapTestDeepMonitor- und ImapSelfTestMonitor-Wiederherstellungsaktionen

1.  Starten Sie den Exchange-IMAP4-Dienst auf dem Back-End-Server neu. Weitere Informationen zum Beenden und Starten des IMAP4-Diensts finden Sie unter [Starten und Stoppen der IMAP4-Dienste](https://technet.microsoft.com/de-de/library/bb124022\(v=exchg.150\)).

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn das Problem weiterhin besteht, müssen Sie ein Failover der Datenbanken ausführen, die auf dem Postfachserver gehostet werden, indem Sie den folgenden Befehl verwenden:
    
        Set-MailboxServer -Identity <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $true

4.  Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
    
        Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status
    
    Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu.

5.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

6.  Ist der Test erfolgreich, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

7.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## ImapCTPMonitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffsservern ausgegeben.

1.  Starten Sie den Exchange-IMAP4-Dienst auf dem Back-End-Server neu. Weitere Informationen zum Beenden und Starten des IMAP4-Diensts finden Sie unter [Starten und Stoppen der IMAP4-Dienste](https://technet.microsoft.com/de-de/library/bb124022\(v=exchg.150\))

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn das Problem weiterhin besteht, müssen Sie die IMAP-Protokollprotokollierung aktivieren, um die Behebung des Problems zu unterstützen. Führen Sie zu diesem Zweck die folgenden Schritte aus:
    
    1.  Führen Sie in der Windows PowerShell den folgenden Befehl aus:
        
            Set-ImapSettings -server <CAS server name> -ProtocolLoggingEnabled $true
    
    2.  Starten Sie den Exchange-IMAP4-Dienst auf dem Back-End-Server neu. Weitere Informationen zum Beenden und Starten des IMAP4-Diensts finden Sie unter [Starten und Stoppen der IMAP4-Dienste](https://technet.microsoft.com/de-de/library/bb124022\(v=exchg.150\))
    
    3.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.
    
    4.  Führen Sie den folgenden Befehl aus, und bestimmen Sie dann den Speicherort der Protokolldatei. Führen Sie dazu den folgenden Befehl aus:
        
            Get-ImapSettings -server <CAS server name>
    
    5.  Bestimmen Sie das Postfach, für das dieser Befehl ausgeführt wird. Der Name des Postfachservers ist der `_Mbx:`-Wert, der in der Fehlermeldung angegeben ist.
    
    6.  Führen Sie den folgenden Befehl aus:
        
            Get-ServerHealth mailbox1.contoso.com | ?{$_.HealtSetName -like "IMAP*"}
        
        **Hinweis**   In diesem Befehl ist *mailbox1.contoso.com* durch Ihren tatsächlichen Postfachservernamen zu ersetzen.
    
    7.  Wenn für in der Befehlsausgabe aufgeführte Monitore Integritätsfehler gemeldet sind, müssen Sie zuerst diese Monitore behandeln. Führen Sie die Schritte zur Problembehandlung aus, die im Abschnitt ImapTestDeepMonitor- und ImapSelfTestMonitor-Wiederherstellungsaktionen beschrieben sind.

4.  Wenn der Postfachserver als fehlerfrei gemeldet wird, starten Sie den Clientzugriffsserver neu.

5.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

6.  Deaktivieren Sie die Protokollprotokollierung. Führen Sie dazu den folgenden Windows PowerShell-Befehl aus:
    
        Set-ImapSettings -server <CAS server name> -ProtocolLoggingEnabled $false

7.  Starten Sie den IMAP4-Dienst neu.

8.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## ImapProxyTestMonitor-Wiederherstellungsaktionen

1.  Starten Sie den IMAP4-Dienst neu.

2.  Führen Sie den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

3.  Wenn der Test weiterhin fehlschlägt, starten Sie den Clientzugriffsserver neu.

4.  Führen Sie nach dem Neustart des Servers den zugeordneten Test, wie im Abschnitt Überprüfen des Vorhandenseins des Problems in Schritt 2c gezeigt, erneut aus.

5.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## AverageCommandProcessingTimeGt60sMonitor- und RequestsQueuedGt500Monitor-Wiederherstellungsaktionen

Diese Monitorwarnung wird typischerweise auf Clientzugriffs- und Postfachservern ausgegeben.

1.  Starten Sie den Exchange-IMAP4-Dienst auf dem Back-End-Server oder dem Clientzugriffsserver neu. Weitere Informationen zum Beenden und Starten des IMAP4-Diensts finden Sie unter [Starten und Stoppen der IMAP4-Dienste](https://technet.microsoft.com/de-de/library/bb124022\(v=exchg.150\))

2.  Warten Sie 10 Minuten, um zu sehen, ob der Monitor fehlerfrei bleibt. Führen Sie nach 10 Minuten den folgenden Befehl aus:
    
        Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -like "IMAP*"}
    
    **Hinweis**   In diesem Befehl ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.

3.  Warten Sie 10 Minuten, und führen Sie dann den in Schritt 2 gezeigten Befehl erneut aus, um zu überprüfen, ob der Monitor fehlerfrei bleibt.

4.  Wenn das Problem weiterhin besteht, müssen Sie den Server neu starten. Ist der Server ein Clientzugriffsserver, brauchen Sie den Server nur neu zu starten. Ist der Server ein Postfachserver, gehen Sie wie folgt vor:
    
    1.  Führen Sie ein Failover der Datenbanken durch, die auf dem Server gehostet sind. Führen Sie dazu den folgenden Befehl aus:
        
            Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $true
        
        **Hinweis**   In diesem und allen folgenden Codebeispielen ist *server1.contoso.com* durch Ihren tatsächlichen Servernamen zu ersetzen.
    
    2.  Überprüfen Sie, ob alle Datenbanken von dem Server, der das Problem meldet, verschoben wurden. Führen Sie dazu den folgenden Befehl aus:
        
            Get-MailboxDatabaseCopyStatus -Server server1.contoso.com | Group Status
        
        Wenn die Ausgabe des Befehls keine aktiven Kopien mehr auf dem Server anzeigt, starten Sie den Server neu.

5.  Warten Sie nach dem Neustart des Servers 10 Minuten, und führen Sie dann den in Schritt 2 gezeigten Befehl erneut aus, um zu bestimmen, ob der Monitor fehlerfrei bleibt.

6.  Bleibt der Monitor fehlerfrei, und handelt es sich um einen Postfachserver, führen Sie ein Failover der Datenbanken durch, indem Sie den folgenden Befehl ausführen:
    
        Set-MailboxServer server1.contoso.com -DatabaseCopyActivationDisabledAndMoveNow $false

7.  Tritt weiterhin ein Fehler bei diesem Test auf, benötigen Sie eventuell Unterstützung zur Behebung dieses Problems. Wenden Sie sich zur Lösung des Problems an einen Microsoft-Supportspezialisten. Sie können Kontakt zu einem Microsoft-Supportspezialisten aufnehmen, indem Sie das [Exchange Server Solution Center](http://go.microsoft.com/fwlink/p/?linkid=180809) besuchen. Klicken Sie im Navigationsbereich auf **Optionen für Support und Ressourcen**, und verwenden Sie eine der Optionen zum **Anfordern von technischen Support**, um Kontakt mit einem Microsoft-Supportspezialisten aufzunehmen. Da es in Ihrer Organisation ein bestimmtes Verfahren für den direkten Kontakt mit dem Microsoft-Produktsupport geben kann, sollten Sie zuerst die Richtlinien Ihrer Organisation prüfen.

## Weitere Informationen

[POP3 und IMAP4](https://technet.microsoft.com/de-de/library/jj657728\(v=exchg.150\))

[Aktivieren von IMAP4 in Exchange 2013](https://technet.microsoft.com/de-de/library/bb124489\(v=exchg.150\))

[Test-ImapConnectivity](https://technet.microsoft.com/de-de/library/bb738126\(v=exchg.150\))

