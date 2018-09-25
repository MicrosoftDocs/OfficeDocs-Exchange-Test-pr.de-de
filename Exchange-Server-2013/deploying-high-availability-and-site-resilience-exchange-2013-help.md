---
title: 'Bereitst. v. Hochverfüg. und Ausfallsich. von Standorten: Exchange 2013-Hilfe'
TOCTitle: Bereitstellen der hohen Verfügbarkeit und Ausfallsicherheit von Standorten
ms:assetid: 4c4e00a4-1f57-4fdb-b9b2-2779abf381a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638129(v=EXCHG.150)
ms:contentKeyID: 50475641
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Bereitstellen der hohen Verfügbarkeit und Ausfallsicherheit von Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Microsoft Exchange Server 2013 verwendet für die hohe Verfügbarkeit und die Ausfallsicherheit von Standorten das unter der Bezeichnung *Inkrementelle Bereitstellung* bekannte Konzept. Sie installieren einfach mindestens zwei Exchange 2013-Postfachserver als eigenständige Server und konfigurieren anschließend nach Bedarf und inkrementell die Funktionen für hohe Verfügbarkeit und Ausfallsicherheit für Standorte für die Postfachserver und -datenbanken.

## Übersicht über den Bereitstellungsvorgang

Der allgemeine Bereitstellungsvorgang von Exchange 2013 in einer Konfiguration mit hoher Verfügbarkeit und Ausfallsicherheit von Standorten ist im Grunde immer derselbe, auch wenn sich die tatsächlichen Schritte in den einzelnen Organisationen geringfügig unterscheiden. Nachdem Sie die notwendigen Planungs- und Entwicklungsaufgaben zum Erstellen und Bereitstellen einer Database Availability Group (DAG) ausgeführt und Postfachdatenbankkopien erstellt haben, gehen Sie wie folgt vor:

1.  Erstellen Sie eine DAG. Weitere Informationen finden Sie unter [Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md).

2.  Führen Sie ggf. eine provisorische Bereitstellung des Clusternamenobjekts (CNO) durch. Die provisorische Bereitstellung des Clusternamensobjekts ist erforderlich, wenn Sie eine DAG mit Postfachservern unter Windows Server 2012 bereitstellen. Wenn Sie eine DAG ohne Administratorzugriffspunkt mit Postfachservern unter Windows Server 2012 R2 bereitstellen, dann ist es nicht erforderlich, ein Clusternamensobjekt provisorisch bereitzustellen. Eine provisorische Bereitstellung ist auch in Umgebungen erforderlich, in denen die Computerkontoerstellung eingeschränkt ist oder Computerkonten in einem anderen Container als dem Standardcontainer für Computer erstellt werden. Weitere Informationen finden Sie unter [Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group](pre-stage-the-cluster-name-object-for-a-database-availability-group-exchange-2013-help.md).

3.  Fügen Sie der DAG mindestens zwei Postfachserver hinzu. Weitere Informationen finden Sie unter [Verwalten der Mitgliedschaft in DAGs](manage-database-availability-group-membership-exchange-2013-help.md).

4.  Konfigurieren Sie die Eigenschaften der DAG nach Bedarf:
    
    1.  Konfigurieren Sie optional Verschlüsselung und Komprimierung, Replikationsport, IP-Adressen und sonstige Eigenschaften für die DAG. Weitere Informationen finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md).
    
    2.  Aktivieren Sie den DAC-Modus (Datacenter Activation Coordination) für die DAG. Dies schützt die DAG vor Split Brain-Bedingungen auf Datenbankebene, wenn ein Datencenterswitchover durchgeführt und die Verwendung der integrierten Cmdlets zur DAG-Wiederherstellung aktiviert wurde. Weitere Informationen finden Sie unter [Datencenter-Aktivierungsmodus](datacenter-activation-coordination-mode-exchange-2013-help.md).

5.  Fügen Sie den Postfachservern in der DAG Postfachdatenbankkopien hinzu. Weitere Informationen finden Sie unter [Hinzufügen einer Kopie einer Postfachdatenbank](add-a-mailbox-database-copy-exchange-2013-help.md).

## Bereitstellungsbeispiel: DAG mit vier Mitgliedern in zwei Datencentern

In diesem Beispiel wird erläutert, wie ein Unternehmen (Contoso, Ltd.) eine DAG mit vier Mitgliedern, die sich über zwei physische Standorte erstreckt, konfiguriert und bereitstellt: Redmond, Washington und Portland, Oregon.

## Basisinfrastruktur

Jeder Standort verfügt über die Infrastrukturelemente, die zum Betrieb einer Messaginginfrastruktur auf Basis von Exchange 2013 erforderlich sind:

  - Verzeichnisdienste (Active Directory oder Active Directory-Domänendienste (Active Directory Domain Services, AD DS))

  - DNS-Namensauflösung (Domain Name System)

  - Mehrere Exchange 2013-Clientzugriffsserver

  - Mehrere Exchange 2013-Postfachserver

In der folgenden Abbildung wird die Contoso-Konfiguration dargestellt.

**Database Availability Group über zwei Standorte**

![Database Availability Group über zwei Standorte](images/Dd638129.1c326fd4-3c7b-4416-a63d-fbfdd0cc6b18(EXCHG.150).gif "Database Availability Group über zwei Standorte")

## Netzwerkkonfiguration

Wie aus der obigen Abbildung hervorgeht, beinhaltet die Lösung mehrere Subnetze und mehrere Netzwerke. Jeder Postfachserver in der DAG verfügt über zwei Netzwerkkarten in separaten Subnetzen. Bei jedem Postfachserver wird der eine Netzwerkadapter für das MAPI-Netzwerk (192.168.*x*.*x*) und der andere für das Replikationsnetzwerk (10.0.*x*.*x*) verwendet. Die Verbindung zu Active Directory, DNS-Diensten sowie sonstigen Exchange-Servern und -Clients wird nur über das MAPI-Netzwerk hergestellt. Der Adapter, der bei jedem Mitglied der DAG für das Replikationsnetzwerk verwendet wird, stellt nur die Verbindung zu den Replikationsnetzwerkadaptern der anderen Mitglieder bereit.

Die Einstellungen für die einzelnen Netzwerkadapter in jedem Knoten gehen aus der folgenden Tabelle hervor.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>IPv4-Adresse</th>
<th>Subnetzmaske</th>
<th>Standardgateway</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MBX1 (MAPI)</p></td>
<td><p>192.168.1.4</p></td>
<td><p>255.255.255.0</p></td>
<td><p>192.168.1.1</p></td>
</tr>
<tr class="even">
<td><p>MBX2 (MAPI)</p></td>
<td><p>192.168.1.5</p></td>
<td><p>255.255.255.0</p></td>
<td><p>192.168.1.1</p></td>
</tr>
<tr class="odd">
<td><p>MBX3 (MAPI)</p></td>
<td><p>192.168.2.4</p></td>
<td><p>255.255.255.0</p></td>
<td><p>192.168.2.1</p></td>
</tr>
<tr class="even">
<td><p>MBX4 (MAPI)</p></td>
<td><p>192.168.2.5</p></td>
<td><p>255.255.255.0</p></td>
<td><p>192.168.2.1</p></td>
</tr>
<tr class="odd">
<td><p>MBX1 (Replikation)</p></td>
<td><p>10.0.1.4</p></td>
<td><p>255.255.0.0</p></td>
<td><p>Keine</p></td>
</tr>
<tr class="even">
<td><p>MBX2 (Replikation)</p></td>
<td><p>10.0.1.5</p></td>
<td><p>255.255.0.0</p></td>
<td><p>Keine</p></td>
</tr>
<tr class="odd">
<td><p>MBX3 (Replikation)</p></td>
<td><p>10.0.2.4</p></td>
<td><p>255.255.0.0</p></td>
<td><p>Keine</p></td>
</tr>
<tr class="even">
<td><p>MBX4 (Replikation)</p></td>
<td><p>10.0.2.5</p></td>
<td><p>255.255.0.0</p></td>
<td><p>Keine</p></td>
</tr>
</tbody>
</table>


Wie aus der obigen Tabelle hervorgeht, werden bei den für die Replikationsnetzwerke verwendeten Adaptern keine Standardgateways verwendet. Für die Netzwerkverbindung zwischen den einzelnen Replikationsnetzwerkkarten verwendet Contoso ein dauerhaftes statisches Routing, das mithilfe des Tools "Netsh.exe" konfiguriert wird.

Für die Routingkonfiguration für die Replikationsnetzwerkkarte auf "MBX1" und "MBX2" wurde auf jedem Server der folgende Befehl ausgeführt.

```powershell
netsh interface ipv4 add route 10.0.2.0/24 <NetworkName> 10.0.1.254
```

Für die Routingkonfiguration für die Replikationsnetzwerkkarte auf "MBX3" und "MBX4" wurde auf jedem Server der folgende Befehl ausgeführt.

```powershell
netsh interface ipv4 add route 10.0.1.0/24 <NetworkName> 10.0.2.254
```

Außerdem wurden die folgenden weiteren Netzwerkeinstellungen konfiguriert:

  - Das Kontrollkästchen **Adressen dieser Verbindung in DNS registrieren** wurde bei den MAPI-Netzwerkadaptern aller DAG-Mitglieder aktiviert und bei allen Replikationsnetzwerkadaptern deaktiviert.

  - Für jeden MAPI-Netzwerkadapter aller DAG-Mitglieder wurde mindestens eine DNS-Serveradresse konfiguriert. Für die Replikationsnetzwerkadapter wurde keine Adresse konfiguriert. Zu Redundanzzwecken verwendet Contoso für die MAPI-Netzwerkadapter mehrere DNS-Serveradressen.

  - Die Windows-Firewall wird von Contoso nicht verwendet. Sie wurde auf den Servern deaktiviert.

Nach der Konfiguration der Netzwerkadapter kann Contoso jetzt eine DAG erstellen und ihr Postfachserver hinzufügen.

## Erstellen und Konfigurieren einer Database Availability Group (DAG)

Der Administrator hat sich für die Erstellung eines Windows PowerShell-Befehlszeilenskripts entschieden, mit dem mehrere Aufgaben ausgeführt werden:

  - Mithilfe des Cmdlets [New-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351107\(v=exchg.150\)) wird die DAG erstellt. Da "REDMOND" als primäres Datencenter betrachtet wird, hat sich Contoso für die Verwendung des Zeugenservers "CAS1" im gleichen Datencenter entschieden.

  - Mithilfe des Cmdlets [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) werden ein alternativer Zeugenserver und ein alternatives Zeugenverzeichnis vorkonfiguriert, die bei einem evtl. erforderlichen Datencenterswitchover zum Einsatz kommen.

  - Mithilfe des Cmdlets [Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd298049\(v=exchg.150\)) werden der DAG alle vier Postfachserver hinzugefügt.

  - Mithilfe des Cmdlets [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) wird die DAG für den DAC-Modus konfiguriert. Weitere Informationen zum DAC-Modus finden Sie unter [Datencenter-Aktivierungsmodus](datacenter-activation-coordination-mode-exchange-2013-help.md).

Die folgenden Befehle werden im Skript verwendet:

```powershell
    New-DatabaseAvailabilityGroup -Name DAG1 -WitnessServer CAS1 -WitnessDirectory C:\DAGWitness\DAG1.contoso.com -DatabaseAvailabilityGroupIPAddresses 192.168.1.8,192.168.2.8
```

Mit dem obigen Befehl wird die DAG "DAG1" erstellt. "CAS1" wird als Zeugenserver konfiguriert, und es wird ein spezielles Zeugenverzeichnis ("C:\\DAGWitness\\DAG1.contoso.com") festgelegt. Für die DAG werden zwei IP-Adressen (eine für jedes Subnetz im MAPI-Netzwerk) konfiguriert.

```powershell
    Set-DatabaseAvailabilityGroup -Identity DAG1 -AlternateWitnessDirectory C:\DAGWitness\DAG1.contoso.com -AlternateWitnessServer CAS4
```

Mit dem oben aufgeführten Befehl wird die DAG "DAG1" für die Verwendung eines alternativen Zeugenservers "CAS4" sowie eines alternativen Zeugenverzeichnisses auf "CAS4" konfiguriert, und zwar unter Verwendung des gleichen Pfads, der für "CAS1" konfiguriert wurde.


> [!NOTE]
> Es ist nicht unbedingt erforderlich, denselben Pfad zu verwenden; Contoso hat sich allerdings dafür entschieden, da die Konfiguration standardisiert werden sollte.


```powershell
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX3
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX2
    Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX4
```

Mit den obigen Befehlen wird der DAG jeweils ein Postfachserver hinzugefügt. Mit diesen Befehlen wird auch die Failoverclusteringkomponente von Windows auf jedem Postfachserver installiert (falls noch nicht geschehen), ein Failovercluster erstellt und jeder Postfachserver mit dem neu erstellten Cluster verbunden.

```powershell
Set-DatabaseAvailabilityGroup -Identity DAG1 -DatacenterActivationMode DagOnly
```

Mit dem obigen Befehl wird für die DAG der DAC-Modus aktiviert.

## Postfachdatenbanken und Postfachdatenbankkopien

Nachdem Contoso die DAG erstellt und ihr die Postfachserver hinzugefügt hat, wird die Erstellung der Postfachdatenbanken und Postfachdatenbankkopien vorbereitet. Damit die internen Kriterien für die Ausfallsicherheit erfüllt werden, plant Contoso, jede Postfachdatenbank mit drei unverzögerten Datenbankkopien und einer verzögerten Datenbankkopie zu konfigurieren. Für die verzögerte Kopie soll eine Protokollwiedergabeverzögerung von drei Tagen konfiguriert werden.

Mit dieser Konfiguration werden für jede Datenbank insgesamt vier Kopien (eine aktive, zwei unverzögerte passive und eine verzögerte passive Kopie) bereitgestellt. Contoso hat pro Server vier aktive Datenbanken vorgesehen. Mit den vier aktiven Datenbanken pro Server und den drei passiven Kopien pro Datenbank enthält die Contoso-Lösung insgesamt 16 Datenbankkopien.

Wie aus der folgenden Abbildung hervorgeht, hat sich Contoso hinsichtlich des Datenbanklayouts für einen ausgewogenen Ansatz entschieden.

**Datenbankkopien – Layout für Contoso, Ltd**

![Datenbankkopie – Layout für Contoso, Ltd](images/Dd638129.41d0c78e-ccaf-4b67-8bab-6fb344668ead(EXCHG.150).gif "Datenbankkopie – Layout für Contoso, Ltd")

Auf jedem Postfachserver befinden sich eine aktive Postfachdatenbankkopie, zwei unverzögerte passive Datenbankkopien und eine verzögerte passive Datenbankkopie. Die verzögerten Kopien der aktiven Postfachdatenbanken werden auf einem Postfachserver am anderen Standort gehostet.

Zum Erstellen dieser Konfiguration muss der Administrator mehrere Befehle ausführen.

Auf "MBX1":

```powershell
    Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX2
    Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX4
    Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX3 -ReplayLagTime 3.00:00:00 -SeedingPostponed
    Suspend-MailboxDatabaseCopy -Identity DB1\MBX3 -SuspendComment "Seed from MBX4" -Confirm:$False
    Update-MailboxDatabaseCopy -Identity DB1\MBX3 -SourceServer MBX4
    Suspend-MailboxDatabaseCopy -Identity DB1\MBX3 -ActivationOnly
```

Auf "MBX2":

```powershell
    Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX1
    Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX3
    Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX4 -ReplayLagTime 3.00:00:00 -SeedingPostponed
    Suspend-MailboxDatabaseCopy -Identity DB2\MBX4 -SuspendComment "Seed from MBX3" -Confirm:$False
    Update-MailboxDatabaseCopy -Identity DB2\MBX4 -SourceServer MBX3
    Suspend-MailboxDatabaseCopy -Identity DB2\MBX4 -ActivationOnly
```

Auf "MBX3":

```powershell
    Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX4
    Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX2
    Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX1 -ReplayLagTime 3.00:00:00 -SeedingPostponed
    Suspend-MailboxDatabaseCopy -Identity DB3\MBX1 -SuspendComment "Seed from MBX2" -Confirm:$False
    Update-MailboxDatabaseCopy -Identity DB3\MBX1 -SourceServer MBX2
    Suspend-MailboxDatabaseCopy -Identity DB3\MBX1 -ActivationOnly
```

Auf "MBX4":

```powershell
    Add-MailboxDatabaseCopy -Identity DB4 -MailboxServer MBX3
    Add-MailboxDatabaseCopy -Identity DB4 -MailboxServer MBX1
    Add-MailboxDatabaseCopy -Identity DB4 -MailboxServer MBX2 -ReplayLagTime 3.00:00:00 -SeedingPostponed
    Suspend-MailboxDatabaseCopy -Identity DB4\MBX2 -SuspendComment "Seed from MBX1" -Confirm:$False
    Update-MailboxDatabaseCopy -Identity DB4\MBX2 -SourceServer MBX1
    Suspend-MailboxDatabaseCopy -Identity DB4\MBX2 -ActivationOnly
```

Im obigen Beispiel wurde beim Cmdlet **Add-MailboxDatabaseCopy** der Parameter *ActivationPreference* nicht angegeben. Der Task inkrementiert automatisch bei jeder hinzugefügten Kopie die Aktivierungseinstellungsnummer. Die Originaldatenbank hat immer die Einstellungsnummer 1. Die erste mithilfe des Cmdlets **Add-MailboxDatabaseCopy** hinzugefügte Kopie erhält automatisch die Einstellungsnummer 2. Unter der Annahme, dass keine Kopien entfernt wurden, wird der nächsten hinzugefügten Kopie automatisch die Einstellungsnummer 3 zugeordnet usw. Daher hat in den obigen Beispielen die passive Kopie, die sich im selben Datencenter wie die aktive Kopie befindet, die Aktivierungseinstellungsnummer 2; die unverzögerte passive Kopie im Remotedatencenter hat die Aktivierungseinstellungsnummer 3 und die verzögerte passive Kopie im Remotedatencenter die Aktivierungseinstellungsnummer 4.

Obwohl es zwei Kopien von jeder aktiven Datenbank im WAN (Wide Area Network, Fernnetz) am anderen Standort gibt, erfolgte der Seedingvorgang nur einmal. Contoso nutzt nämlich die Möglichkeit von Exchange 2013, eine passive Datenbankkopie als Quelle für das Seeding zu verwenden. Mithilfe des Cmdlets [Add-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298105\(v=exchg.150\)) und des Parameters *SeedingPostponed* wird der Task daran gehindert, den Seedingvorgang für die neu erstellte Datenbankkopie automatisch auszuführen. Dann kann der Administrator die Kopie, für die kein Seeding erfolgt ist, anhalten und mithilfe des Cmdlets [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) und des Parameters *SourceServer* die lokale Kopie der Datenbank als Quelle für den Seedingvorgang angeben. Dadurch erfolgt der Seedingvorgang für die zweite Datenbankkopie, die jedem Standort hinzugefügt wird, lokal und nicht über das WAN.


> [!NOTE]
> Im obigen Beispiel erfolgt der Seedingvorgang für die unverzögerte Datenbankkopie über das WAN. Anschließend wird diese Kopie für das Seeding der verzögerten Kopie der Datenbank, die sich im selben Datencenter wie die unverzögerte Kopie befindet, verwendet.



Zum Schutz vor einer äußerst selten vorkommenden Beschädigung der Datenbanklogik, die katastrophale Folgen haben kann, hat Contoso eine passive Kopie jeder Postfachdatenbank als verzögerte Datenbankkopie konfiguriert. Daher konfiguriert der Administrator mithilfe des Cmdlets [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd351074\(v=exchg.150\)) und des Parameters *ActivationOnly* die verzögerten Kopien so, dass sie für eine Aktivierung gesperrt sind. Dadurch wird sichergestellt, dass die verzögerten Datenbankkopien bei einem Datenbank- oder Serverfailover nicht aktiviert werden.

## Überprüfen der Lösung

Nach Bereitstellung und Konfiguration der Lösung führt der Administrator mehrere Aufgaben aus, anhand denen er die Lösung auf ihre Funktionsfähigkeit überprüft, bevor Produktionspostfächer in die Datenbanken in der DAG verschoben werden. Die Lösung sollte anhand mehrerer Methoden, einschließlich Fehlersimulationen, getestet und überprüft werden. Zum Überprüfen der Lösung führt der Administrator verschiedene Aufgaben aus.

Der Administrator führt das Cmdlet [Test-ReplicationHealth](https://technet.microsoft.com/de-de/library/bb691314\(v=exchg.150\)) aus, um den allgemeinen Status der DAG zu überprüfen. Mit diesem Cmdlet werden Replikations- und Wiedergabestatus unter verschiedenen Aspekten überprüft und Informationen zu jedem Postfachserver und jeder Datenbankkopie in der DAG bereitgestellt.

Zum Überprüfen von Replikations- und Wiedergabeaktivität führt der Administrator das Cmdlet [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\)) aus. Dieses Cmdlet stellt Statusinformationen in Echtzeit zu einer bestimmten Postfachdatenbankkopie oder zu allen Postfachdatenbankkopien auf einem bestimmten Server bereit. Weitere Informationen zum Überwachen des Status replizierter Datenbanken in einer DAG finden Sie unter [Überwachen von Datenbankverfügbarkeitsgruppen](monitoring-database-availability-groups-exchange-2013-help.md).

Zum Überprüfen, ob Switchover erwartungsgemäß funktionieren, führt der Administrator mithilfe des Cmdlets [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)) eine Reihe von Datenbank- und Serverswitchovern durch. Nachdem diese Aufgaben erfolgreich durchgeführt wurden, verschiebt der Administrator mithilfe desselben Cmdlets die aktiven Datenbankkopien wieder an ihre ursprünglichen Speicherorte.

Zum Überprüfen des erwartungsgemäßen Verhaltens in verschiedenen Fehlerszenarien führt der Administrator mehrere Aufgaben aus, mit denen entweder Fehler simuliert oder tatsächlich verursacht werden. Der Administrator kann beispielsweise Folgendes tun:

  - "MBX1" vom Stromnetz trennen (Stecker ziehen), wodurch ein Serverfailover ausgelöst wird. Der Administrator kann dann überprüfen, ob "DB1" auf einem anderen Server (vorzugsweise "MBX2" gemäß den Aktivierungseinstellungsnummern) aktiviert wird.

  - Den MAPI-Netzwerkadapter auf "MBX2" vom Stromnetz trennen (Stecker ziehen), wodurch ein Serverfailover ausgelöst wird. Der Administrator kann dann überprüfen, ob "DB2" auf einem anderen Server (vorzugsweise "MBX1" gemäß den Aktivierungseinstellungsnummern) aktiviert wird.

  - Die von der aktiven Kopie von DB3 verwendete Festplatte offline schalten, wodurch ein Datenbankfailover ausgelöst wird. Der Administrator kann dann überprüfen, ob "DB3" auf einem anderen Server (vorzugsweise "MBX4" gemäß den Aktivierungseinstellungsnummern) aktiviert wird.

Je nach den geschäftlichen Anforderungen kann es noch weitere Fehlerszenarien geben, die in einer Organisation getestet werden. Nach der Simulation eines einzelnen Fehlers (z. B. Stecker ziehen) und der Überprüfung des Wiederherstellungsverhaltens der Lösung kann der Administrator die Lösung auf die ursprüngliche Konfiguration zurücksetzen. In einigen Fällen kann die Lösung auf mehrere gleichzeitige Fehler getestet werden. Letztlich gibt der Lösungsprüfplan vor, ob die Lösung nach jeder Fehlersimulation auf die ursprüngliche Konfiguration zurückgesetzt wird.

Außerdem kann der Administrator auch die Netzwerkverbindung zwischen den beiden Datencentern trennen und so den Ausfall eines Standorts simulieren. Ein Datencenterswitchover ist ein Prozess, der sehr viel mehr Überlegungen und Koordination verlangt; er wird jedoch empfohlen, wenn die bereitgestellte Lösung Ausfallsicherheit von Standorten für Messagingdienste und Daten bieten soll.

## Inbetriebnahme

Nachdem die Lösung bereitgestellt wurde, kann sie über die inkrementelle Bereitstellung erweitert werden. An diesem Punkt erfolgt auch hinsichtlich der Verwaltung der Lösung eine Umstellung auf die Betriebsprozesse, bei denen die folgenden Aufgaben ausgeführt werden:

  - Überwachen des Status der DAGs und Postfachdatenbankkopien. Weitere Informationen finden Sie unter [Überwachen von Datenbankverfügbarkeitsgruppen](monitoring-database-availability-groups-exchange-2013-help.md).

  - Führen Sie nach Bedarf Datenbankswitchover durch. Genaue Anweisungen zum Durchführen eines Datenbankswitchovers finden Sie unter [Aktivieren einer Kopie einer Postfachdatenbank](activate-a-mailbox-database-copy-exchange-2013-help.md).

Weitere Informationen zum Verwalten der Lösung finden Sie unter [Verwalten von hoher Verfügbarkeit und Ausfallsicherheit für Standorte](managing-high-availability-and-site-resilience-exchange-2013-help.md).

