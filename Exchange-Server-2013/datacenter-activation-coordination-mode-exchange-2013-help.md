---
title: 'Datencenter-Aktivierungsmodus: Exchange 2013 Help'
TOCTitle: Datencenter-Aktivierungsmodus
ms:assetid: 57e4bf22-eeae-42a5-beb3-d68d06489592
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979790(v=EXCHG.150)
ms:contentKeyID: 50475729
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Datencenter-Aktivierungsmodus

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-07-14_

Der DAC-Modus (Datacenter Activation Coordination) ist eine Eigenschaft für eine Datenbankverfügbarkeitsgruppe (DAG, Database Availability Group). Der DAC-Modus ist standardmäßig deaktiviert, sollte jedoch für alle DAGs mit mindestens zwei Mitgliedern aktiviert werden, die die fortlaufende Replikation verwenden. Der DAC-Modus sollte für DAGs, die einen Replikationsmodus von Drittanbietern verwenden, nur aktiviert werden, wenn der Drittanbieter dies ausdrücklich autorisiert hat.

Der DAC-Modus wird verwendet, um die Datenbankbereitstellung beim Startverhalten einer DAG zu steuern. Diese Steuerung hat den Sinn, das Auftreten des Split Brain-Syndroms zu verhindern, das während eines Datencenterswitchbacks auf Datenbankebene auftritt. Split Brain, auch als Split Brain-Syndrom bekannt, ist ein Zustand, der dazu führt, dass eine Datenbankkopie als aktive Kopie von zwei Mitgliedern derselben DAG bereitgestellt wird, die nicht miteinander kommunizieren können. Split Brain wird mithilfe des DAC-Modus verhindert, da der DAC-Modus erfordert, dass DAG-Mitglieder Berechtigungen zur Bereitstellung von Datenbanken besitzen müssen, bevor sie bereitgestellt werden können.

Beispiel: In einem Szenario umfasst das primäre Datencenter zwei Mitglieder der DAG und den Zeugenserver, ein sekundäres Datencenter die beiden anderen Mitglieder. In diesem Szenario befindet sich die DAG nicht im DAC-Modus. Wenn im primären Datencenter der Strom ausfällt, aktivieren Sie die DAG im zweiten Datencenter. Nach einiger Zeit ist die Stromversorgung des primären Datencenters wiederhergestellt, und die DAG-Elemente im primären Datencenter, die das Quorum vor dem Stromausfall hatten, starten und stellen ihre Datenbanken bereit. Da das primäre Datencenter ohne Netzwerkkonnektivität zum zweiten Datencenter wiederhergestellt wurde und da sich die DAG nicht im DAC-Modus befunden hat, wurde die aktive Datenbank in der DAG vom Split Brain-Syndrom befallen.

## Funktionsweise des DAC-Modus (Datacenter Activation Coordination)

Der DAC-Modus verhindert über das Protokoll DACP (Datacenter Activation Coordination Protocol) das Auftreten von Split Brain-Szenarien. Wenn der DAC-Modus aktiviert wird, stellen DAG-Mitglieder nicht automatisch Datenbanken bereit, selbst wenn Sie das Quorum haben. Stattdessen wird anhand von DACP der aktuelle Status der DAG ermittelt und festgestellt, ob Active Manager versuchen soll, die Datenbanken einzubinden.

Sie können sich den DAC-Modus wie ein Quorum zum Einbinden von Datenbanken auf Anwendungsebene vorstellen. Um Sinn und Zweck von DACP und dessen Funktionsweise zu verstehen, müssen Sie das Szenario kennen, für das dieses Protokoll hauptsächlich vorgesehen ist. Stellen Sie sich ein Szenario mit zwei Datencentern vor. Nehmen Sie an, dass im primären Datencenter die Stromversorgung vollständig ausfällt. Bei diesem Ereignis fallen alle Server und das WAN aus, und das Unternehmen entscheidet sich für eine Aktivierung des Standby-Datencenters. Bei nahezu allen Wiederherstellungsszenarien (wenn die Stromversorgung im primären Datencenter wiederhergestellt wird) wird die WAN-Konnektivität in der Regel nicht sofort gleichzeitig wiederhergestellt. Das bedeutet, dass die Mitglieder der DAG im primären Datencenter wieder hochgefahren werden, aber nicht mit den Mitgliedern der DAG im aktivierten Standby-Datencenter kommunizieren können. Das primäre Datencenter sollte stets das Quorum der DAG (die Mehrzahl der Wähler) haben. Das heißt, dass die Mitglieder der DAG im primären Datencenter eine Mehrheit bilden und daher das Quorum haben, wenn die Stromversorgung wiederhergestellt wird, auch wenn keine WAN-Konnektivität zu den Mitgliedern der DAG im Standby-Datencenter besteht. Das stellt jedoch ein Problem dar. Aufgrund des Quorums können die Server ihre Datenbanken einbinden, was wiederum zu Abweichungen von den tatsächlich aktiven Datenbanken führt, die aktuell im aktivierten Standby-Datencenter eingebunden sind.

Für dieses Problem wurde DACP entwickelt. Der Active Manager speichert ein Bit (0 oder 1) im Arbeitsspeicher, das der DAG mitteilt, ob sie lokale Datenbanken, die auf dem Server als aktiv zugewiesen sind, einbinden darf. Wenn eine DAG im DAC-Modus läuft, wird das Bit immer dann, wenn Active Manager startet, auf 0 gesetzt, was bedeutet, dass es nicht erlaubt ist, Datenbanken bereitzustellen. Aufgrund des DAC-Modus muss der Server versuchen, mit allen bekannten Mitgliedern der DAG zu kommunizieren, um von einem anderen Mitglied der DAG eine Antwort auf die Frage zu erhalten, ob er die ihm als aktiv zugewiesenen lokalen Datenbanken einbinden darf. Die Antwort erfolgt in Form der Biteinstellung für andere Active Manager in der DAG. Wenn ein anderer Server antwortet, dass sein Bit auf 1 gesetzt ist, bedeutet dies, dass die Server Datenbanken einbinden dürfen. Daher wird auf dem Server, der gestartet wird, das Bit auf 1 gesetzt, und die Datenbanken werden eingebunden.

Bei der Wiederherstellung eines primären Datencenters nach einem Stromausfall, bei dem zwar die Server, jedoch noch nicht die WAN-Konnektivität wiederhergestellt wurde, ist bei allen Mitgliedern der DAG im primären Datencenter der DACP-Bitwert auf 0 gesetzt. Folglich bindet keiner der neu gestarteten Server im wiederhergestellten primären Datencenter Datenbanken ein, da keiner dieser Server mit einem Mitglied der DAG kommunizieren kann, das im DACP einen Bitwert von 1 aufweist.

## DAC-Modus für DAGs mit zwei Mitgliedern

DAGs mit zwei Mitgliedern unterliegen automatisch Einschränkungen, die einen vollständigen Schutz vor dem Split Brain-Syndrom auf Anwendungsebene durch das DACP-Bit allein verhindern. Bei DAGs mit nur zwei Mitgliedern wird beim Datacenter-Aktivierungsmodus außerdem anhand des Startzeitpunkts des DAG-Zeugenservers ermittelt, ob beim Start Datenbanken eingebunden werden können. Der Startzeitpunkt des Zeugenservers wird mit dem Zeitpunkt verglichen, an dem das DACP-Bit auf 1 gesetzt wurde.

  - Wenn der Zeitpunkt, an dem das DACP-Bit gesetzt wurde, vor dem Startzeitpunkt des Zeugenservers liegt, geht das System davon aus, dass das DAG-Mitglied und der Zeugenserver zur gleichen Zeit neu gestartet wurden (möglicherweise aufgrund eines Stromausfalls im primären Datencenter), und dem DAG-Mitglied wird nicht gestattet, Datenbanken einzubinden.

  - Wenn das DACP-Bit zu einem späteren Zeitpunkt als dem Startzeitpunkt des Zeugenservers gesetzt wurde, geht das System davon aus, dass das DAG-Mitglied aus einem anderen Grund neu gestartet wurde (möglicherweise ein geplanter Ausfall zu Wartungszwecken oder ein isolierter System- oder Stromausfall ausschließlich beim DAG-Mitglied), und das DAG-Mitglied darf Datenbanken einbinden.


> [!IMPORTANT]
> Da anhand des Startzeitpunkts des Zeugenservers ermittelt wird, ob ein DAG-Mitglied seine aktiven Datenbanken beim Start einbinden darf, sollten Sie den Zeugenserver und das einzige DAG-Mitglied nie zur gleichen Zeit neu starten, Das DAG-Mitglied bleibt dadurch möglicherweise in einem Zustand, in dem beim Start keine Datenbanken eingebunden werden können. In einem solchen Fall müssen Sie für die DAG das Cmdlet <A href="https://technet.microsoft.com/de-de/library/dd351169(v=exchg.150)">Restore-DatabaseAvailabilityGroup</A> ausführen. Dadurch wird das DACP-Bit zurückgesetzt und dem DAG-Mitglied das Einbinden von Datenbanken gestattet.



## Weitere Vorteile des DAC-Modus

Der DAC-Modus verhindert nicht nur das Split Brain-Syndrom auf Anwendungsebene, sondern aktiviert auch die Verwendung der integrierten Cmdlets für die Ausfallsicherheit von Standorten, die für Datencenterswitchover verwendet werden. Hierzu gehören folgende:

  - [Stop-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd335133\(v=exchg.150\))

  - [Restore-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351169\(v=exchg.150\))

  - [Start-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd335076\(v=exchg.150\))

Bei Datencenterswitchovern für DAGs, die sich nicht im DAC-Modus befinden, muss eine Kombination von Exchange-Tools und Clustermanagementtools verwendet werden. Weitere Informationen finden Sie unter [Datencenterswitchover](datacenter-switchovers-exchange-2013-help.md).

## Aktivieren des DAC-Modus

Der DAC-Modus kann nur mithilfe der Exchange-Verwaltungsshell aktiviert werden. Zum Aktivieren des DAC-Modus wird speziell das Cmdlet [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) verwendet (siehe Abbildung).

    Set-DatabaseAvailabilityGroup -Identity DAG2 -DatacenterActivationMode DagOnly

Im vorherigen Beispiel wurde die DAG "DAG2" für den DAC-Modus aktiviert.

Weitere Informationen zum DAC-Modus finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md) und [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)).

