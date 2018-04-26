---
title: Problembehandlung beim FIPS-Integritätssatz
TOCTitle: Problembehandlung beim FIPS-Integritätssatz
ms:assetid: 96e1b096-9cb5-426f-a84e-50d5599e4bbb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.fips(v=EXCHG.150)
ms:contentKeyID: 54651554
ms.date: 10/08/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim FIPS-Integritätssatz

 

_**Gilt für:**Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Der **FIPS**-Integritätssatz überwacht die Gesamtintegrität der FIPS-Einstellungen (Federal Information Processing Standards, Bundesstandard für Informationsverarbeitung) auf Exchange-Servern. Weitere Informationen über FIPS 140 finden Sie im Thema zur [FIPS 140-Überprüfung](http://go.microsoft.com/fwlink/p/?linkid=521913).

Wenn eine Warnung angezeigt wird, die darauf hindeutet, dass der **FIPS**-Integritätssatz eine fehlerhafte Integrität aufweist, deutet dies auf einen Fehler hin, der Ihren Exchange-Server möglicherweise daran hindert, FIPS 140-konforme Komponenten und Prozesse zu verwenden.

## Erläuterung

Der **FIPS**-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


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
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>CrashEvent.scanningprocess</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>MaintenanceFailureMonitor.FIPS</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>MaintenanceTimeoutMonitor.FIPS</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>PrivateWorkingSetWarning.scanningprocess</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>PrivateWorkingSetError.scanningprocess</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>ProcessProcessorTimeWarning.scanningprocess</p></td>
</tr>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>FIPS</p></td>
<td><p>ProcessProcessorTimeError.scanningprocess</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im **FIPS**-Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die im folgenden Abschnitt beschrieben sind.

## Überprüfen des Problems

1.  Identifizieren Sie den Namen des Integritätssatzes sowie den Servernamen, die in der Warnung angegeben sind.

2.  Die Nachrichtendetails enthalten Informationen zur genauen Ursache für die Warnung. In den meisten Fällen bieten die Nachrichtendetails ausreichende Problembehandlungsinformationen, um die Fehlerursache zu identifizieren. Wenn die Nachrichtendetails nicht klar sind, gehen Sie wie folgt vor:
    
    1.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus, um die Details des Integritätssatzes abzurufen, von dem die Warnung ausgelöst wurde:
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Führen Sie den folgenden Befehl aus, um beispielsweise die Details des **FIPS**-Integritätssatzes zu "server1.contoso.com" abzurufen:
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "FIPS"}
    
    2.  Überprüfen Sie die Ausgabe des Befehls, um zu bestimmen, von welchem Monitor der Fehler gemeldet wurde. Der Wert **AlertValue** des Monitors, von dem die Warnung ausgegeben wurde, lautet **Unhealthy**.

