---
title: Problembehandlung beim MailboxTransport-Integritätssatz
TOCTitle: Problembehandlung beim MailboxTransport-Integritätssatz
ms:assetid: 02bfa4cf-6929-437e-bae5-079ea1b92373
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.mailboxtransport(v=EXCHG.150)
ms:contentKeyID: 54651531
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim MailboxTransport-Integritätssatz

 

_**Gilt für:** Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Der Integritätssatz **MailboxTransport** überwacht die Gesamtintegrität der Postfachtransportübergabe- und Postfachtransportzustellungs-Dienste auf Postfachservern. Diese Dienste sind für das Senden zu und aus Postfachdatenbanken verantwortlich. Weitere Informationen finden Sie unter [Nachrichtenübermittlung](https://technet.microsoft.com/de-de/library/aa996349\(v=exchg.150\)).

Wenn eine Warnung angezeigt wird, die darauf hinweist, dass der Integritätssatz **MailboxTransport** eine fehlerhafte Integrität aufweist, deutet dies auf ein Problem hin, die Ihre E-Mail möglicherweise daran hindert, von Postfachdatenbanken gesendet oder empfangen zu werden.

## Erläuterung

Der **MailboxTransport**-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Test</th>
<th>Integritätssatz</th>
<th>Zugehörige Monitore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MailboxDeliveryAvailability</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryAvailabilityMonitor</p></td>
</tr>
<tr class="even">
<td><p>MailboxDeliveryAvailabilityAggregationProbe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryAvailabilityAggregationMonitor</p></td>
</tr>
<tr class="odd">
<td><p>MailboxDeliveryInstanceAvailabilityProbe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryInstanceAvailabilityMonitor</p></td>
</tr>
<tr class="even">
<td><p>MailboxTransportDeliveryServiceRunning</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportDeliveryServiceRunningMonitor</p></td>
</tr>
<tr class="odd">
<td><p>MailboxTransportSubmissionServiceRunning</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportSubmissionServiceRunningMonitor</p></td>
</tr>
<tr class="even">
<td><p>Mapi.Submit.Probe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>Mapi.Submit.Monitor</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>CrashEvent.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>CrashEvent.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>DeliveryBackpressureSustainedTimeMonitor</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>DeliveryInterceptorStoreDriverAgentPctPermFailedMonitor</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportUserQuarantineMonitor</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MBTSubmissionInterceptorSubmissionAgentMonitor</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MSExchangeAsstAvgEventProcessingTimeSubmissionMonitor50</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MSExchangeAsstAvgEventProcessingTimeSubmissionMonitor70</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetError.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetError.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetWarning.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetWarning.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeError.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeError.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeWarning.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeWarning.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>SubmissionBackpressureSustainedTimeMonitor</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>SubmissionInterceptorSubmissionAgentPctPermFailedMonitor</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>TransportDeliveryFailuresDeliveryStoreDriver560Monitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im **MailboxTransport**-Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die im folgenden Abschnitt beschrieben sind.

## Überprüfen des Problems

1.  Identifizieren Sie den Namen des Integritätssatzes sowie den Servernamen, die in der Warnung angegeben sind.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Führen Sie den folgenden Befehl aus, um beispielsweise **MailboxTransport**-Integritätssatzdetails über "mailbox1.contoso.com" zu erhalten:
        
            Get-ServerHealth mailbox1.contoso.com | ?{$_.HealthSetName -eq "MailboxTransport"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet **Unhealthy**.
    
    3.  Führen Sie den Test erneut aus, der dem Monitor zugeordnet ist, der sich in einem fehlerhaften Zustand befindet. Den zugeordneten Test können Sie mithilfe der Tabelle im Abschnitt [Erläuterung](troubleshooting-activesync-health-set.md) ermitteln. Führen Sie dazu den folgenden Befehl aus:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Angenommen, **MailboxDeliveryAvailabilityMonitor** ist der fehlerhafte Monitor. Der diesem Monitor zugeordnete Test ist **MailboxDeliveryAvailability**. Führen Sie den folgenden Befehl aus, um diesen Test auf "mailbox1.contoso.com" auszuführen:
        
            Invoke-MonitoringProbe MailboxTransport\MailboxDeliveryAvailabilityMonitor -Server mailbox1.contoso.com | Format-List
    
    4.  Überprüfen Sie in der Ausgabe des Befehls den Abschnitt "Ergebnis" des Tests. Wenn der Wert **Erfolgreich** ist, hat es sich bei dem Problem um einen vorübergehenden Fehler gehandelt, der nicht mehr besteht.

