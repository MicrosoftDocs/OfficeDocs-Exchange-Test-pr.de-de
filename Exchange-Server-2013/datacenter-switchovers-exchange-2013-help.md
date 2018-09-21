---
title: 'Datencenterswitchover: Exchange 2013 Help'
TOCTitle: Datencenterswitchover
ms:assetid: ac208c12-04d0-4809-bacd-72478ff14983
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351049(v=EXCHG.150)
ms:contentKeyID: 62523869
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Datencenterswitchover

 

_**Gilt für:** Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2016-03-17_

In einer Konfiguration mit Ausfallsicherheit für Standorte kann in einer DAG in Reaktion auf einen Ausfall auf Standortebene eine automatische Wiederherstellung erfolgen, sodass das Messaging-System weiterhin funktioniert. Für diese Konfiguration sind mindestens drei Standorte erforderlich, da dafür DAG-Mitglieder an zwei Standorten und der Zeugenserver der DAG an einem dritten Standort bereitgestellt werden müssen.

Wenn Sie keine drei Standorte zur Verfügung haben, oder diese zur Verfügung haben, aber Wiederherstellungsaktionen auf Rechenzentrumsebene steuern möchten, können Sie eine DAG für den Fall eines Ausfalls auf Standortebene für manuelle Wiederherstellung konfigurieren. In diesem Fall würden Sie einen Prozess mit der Bezeichung *Datencenterswitchover* durchführen. Wie bei vielen Szenarien der Notfallwiederherstellung kann eine vorherige Planung und Vorbereitung eines Datencenterswitchovers den Wiederherstellungsvorgang vereinfachen und die Dauer des Ausfalls verringern.

Zwischen der Entscheidung, ein zweites Datencenter zu aktivieren, und dem Ausführen eines Datencenterswitchovers liegen vier grundlegende Schritte:

1.  **Beenden eines teilweise aktiven Datencenters**   Dieser Schritt umfasst das Beenden von Exchange-Diensten im primären Datencenter, falls diese noch ausgeführt werden. Dies ist vor allem für die Postfachserverrolle wichtig, da diese ein Aktiv/Passiv-Modell für hohe Verfügbarkeit verwendet. Wenn Dienste in einem teilweise ausgefallenen Datencenter nicht angehalten werden, wirken sich die Probleme dieses Datencenters bei einem Switchover zurück zum primären Datencenter möglicherweise negativ auf die Dienste aus.
    

    > [!IMPORTANT]
    > Wenn die Zuverlässigkeit eines Netzwerks oder einer Active Directory-Infrastruktur durch den Ausfall des primären Datencenters beeinträchtigt wurde,&nbsp;wird empfohlen, alle Messagingdienste zu deaktivieren, bis diese Abhängigkeiten wieder fehlerfrei ausgeführt werden können.



2.  **Überprüfen und Bestätigen der Voraussetzungen für das zweite Datencenter**   Dieser Schritt kann zeitgleich mit Schritt 1 ausgeführt werden, da das Überprüfen der Integrität der Infrastrukturabhängigkeiten im zweiten Datencenter größtenteils unabhängig von den Diensten im ersten Datencenter ist. Jede Organisation wendet in der Regel eine eigene Methode für die Ausführung dieses Schritts an. So können Sie beispielsweise die von einer Anwendung zur Infrastrukturüberwachung erfassten und gefilterten Integritätsinformationen prüfen oder ein speziell in Ihrer Organisationsstruktur genutztes Tool verwenden. Dies ist ein wichtiger Schritt, da das Aktivieren eines zweiten Datencenters in einer fehlerhaften oder instabilen Infrastruktur mit hoher Wahrscheinlichkeit nur unbefriedigende Ergebnisse liefert.

3.  **Aktivieren der Postfachserver**   Mit diesem Schritt beginnt das Aktivieren des zweiten Datencenters. Dieser Schritt kann zeitgleich mit Schritt 4 ausgeführt werden, da die Microsoft Exchange-Dienste Datenbankausfälle und -wiederherstellungen verarbeiten können. Das Aktivieren der Postfachserver umfasst das Kennzeichnen der ausgefallenen Server im primären Datencenter als nicht verfügbar sowie das anschließende Aktivieren der Server im zweiten Datencenter. Der Aktivierungsprozess für Postfachserver hängt davon ab, ob sich die Database Availability Group (DAG) im Aktivierungsmodus der Datenbank befindet. Weitere Informationen zum Aktivierungsmodus der Datenbank finden Sie unter [Datencenter-Aktivierungsmodus](datacenter-activation-coordination-mode-exchange-2013-help.md).
    
    Wenn sich die DAG im Aktivierungsmodus der Datenbank befindet, können Sie die Cmdlets für die Ausfallsicherheit von Standorten in Exchange verwenden, um teilweise ausgefallene Datencenter zu beenden (falls erforderlich) und die Postfachserver zu aktivieren. Im Aktivierungsmodus der Datenbank wird dieser Schritt z. B. mithilfe des Cmdlets [Stop-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd335133\(v=exchg.150\)) ausgeführt. In einigen Fällen müssen die Server zweimal als nicht verfügbar gekennzeichnet werden (einmal pro Datencenter). Im Anschluss wird das Cmdlet [Restore-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351169\(v=exchg.150\)) ausgeführt, um die verbleibenden Mitglieder der DAG im zweiten Datencenter wiederherzustellen. Dabei werden nur jene DAG-Mitglieder beibehalten, die noch funktionsbereit sind, und das Quorum wird so wiederhergestellt. Befindet sich die Database Availability Group nicht im Aktivierungsmodus der Datenbank, müssen die Postfachserver mithilfe von Windows-Failovercluster aktiviert werden. Nach Abschluss dieser Vorgänge können die zuvor im zweiten Datencenter passiven Datenbankkopien aktiviert und eingebunden werden. Zu diesem Zeitpunkt ist die Wiederherstellung des Postfachservers abgeschlossen.

4.  **Aktivieren der Clientzugriffsserver**   Dazu zählt das Implementieren aller erforderlichen DNS-Updates mithilfe der URL-Zuordnungsinformationen und der DNS-Änderungsmethode (Domain Name System). Die Zuordnungsinformationen beschreiben, welche DNS-Änderungen vorgenommen werden sollen. Der Zeitraum für das Fertigstellen der Updates hängt von der verwendeten Methode und den Einstellungen für die Gültigkeitsdauer (Time to Live, TTL) im DNS-Datensatz ab (und davon, ob bei der Bereitstellung der Infrastruktur die TTL berücksichtigt wurde).

Benutzer sollten im Regelfall im Anschluss an Schritt 3 oder 4 Zugriff auf die Messagingdienste haben. Die Schritte 3 und 4 werden weiter unten in diesem Thema ausführlich beschrieben.

**Inhalt**

Beenden eines teilweise ausgefallenen Datencenters

Aktivieren von Postfachservern

Aktivieren von Clientzugriffsservern

Wiederherstellen von Diensten im primären Datencenter

Wiederherstellen der Ausfallsicherheit

## Beenden eines teilweise ausgefallenen Datencenters

Im ausgefallenen Datencenter noch ausgeführte Mitglieder einer Database Availability Group müssen beendet werden.

Wenn sich die Database Availability Group im Aktivierungsmodus der Datenbank befindet, müssen folgende Aktionen ausgeführt werden, um noch ausgeführte Mitglieder einer DAG im primären Datencenter zu beenden:

1.  Die DAG-Mitglieder im primären Datencenter müssen als beendet gekennzeichnet werden. *Beendet* ist ein Status von Active Manager, der die Bereitstellung von Datenbanken verhindert. Dieser Active Manager-Status kann auf jedem Server innerhalb des ausgefallenen Datencenters mithilfe des Cmdlets [Stop-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd335133\(v=exchg.150\)) festgelegt werden. Über den Parameter *ActiveDirectorySite* dieses Cmdlets können alle Server im primären Datencenter mithilfe eines einzelnen Befehls als beendet gekennzeichnet werden. Dieser Schritt kann je nach Art des Ausfalls möglicherweise nicht ausgeführt werden. Er sollte jedoch ausgeführt werden, wenn der Status des Datencenters dies zulässt. Das Cmdlet **Stop-DatabaseAvailabilityGroup** muss auf allen Servern im primären Datencenter ausgeführt werden. Falls der Postfachserver nicht verfügbar, Active Directory jedoch im primären Datencenter funktionsbereit ist, muss der Befehl **Stop-DatabaseAvailabilityGroup** mit dem Parameter *ConfigurationOnly* auf allen Servern mit diesem Status im primären Datencenter ausgeführt werden, oder der Postfachserver muss deaktiviert werden. Wenn weder die Postfachserver im ausgefallenen Datencenter deaktiviert werden noch der Befehl **Stop-DatabaseAvailabilityGroup** auf den Servern erfolgreich ausgeführt wird, kann es zu einem datencenterübergreifenden Split Brain-Syndrom kommen. Sie müssen Computer u. U. einzeln mithilfe von Geräten zur Energieverwaltung ausschalten, um diese Anforderung zu erfüllen.

2.  Das zweite Datencenter muss nun aktualisiert werden, um anzuzeigen, welche Server des primären Datencenters beendet wurden. Dies geschieht durch Ausführen desselben Befehls **Stop-DatabaseAvailabilityGroup** mit dem Parameter *ConfigurationOnly* unter Verwendung desselben Parameters *ActiveDirectorySite* und unter Angabe des Namens des Active Directory-Standorts im ausgefallenen primären Datencenter. Zweck dieses Schritts ist das Benachrichtigen der Server im zweiten Datencenter hinsichtlich der Postfachserver, die beim Wiederherstellen des Diensts verwendet werden können.

Wenn sich die Database Availability Group nicht im Aktivierungsmodus der Datenbank befindet, müssen folgende Aktionen ausgeführt werden, um noch ausgeführte Mitglieder einer Database Availability Group im primären Datencenter zu beenden:

1.  Für DAG-Mitglieder im primären Datencenter muss das Entfernen aus dem zugrunde liegenden Cluster der Database Availability Group erzwungen werden, indem für jedes Mitglied die folgenden Befehle ausgeführt werden:
    
    ```powershell
net stop clussvc
```
        cluster <DAGName> node <DAGMemberName> /forcecleanup

2.  Die Mitglieder der Database Availability Group im zweiten Datencenter müssen nun neu gestartet und anschließend zum Abschließen des Entfernungsprozesses aus dem zweiten Datencenter verwendet werden. Halten Sie den Clusterdienst für jedes Mitglied der Database Availability Group im zweiten Datencenter an, indem Sie für jedes Mitglied den folgenden Befehl ausführen:
    
    ```powershell
net stop clussvc
```

3.  Erzwingen Sie auf einem DAG-Mitglied im zweiten Datencenter mithilfe des folgenden Befehls einen Quorumstart des Clusterdiensts:
    
    ```powershell
net start clussvc /forcequorum
```

4.  Öffnen Sie die das Tool für die Failoverclusterverwaltung, und stellen Sie die Verbindung mit dem zugrunde liegenden Cluster der Database Availability Group her. Erweitern Sie den Clusterknoten, und erweitern Sie dann **Knoten**. Klicken Sie mit der rechten Maustaste auf jeden Knoten im primären Datencenter, wählen Sie **Weitere Aktionen**, und wählen Sie dann **Zwangslöschen**. Schließen Sie nach dem Entfernen der DAG-Mitglieder im primären Datencenter die Tools zur Failoverclusterverwaltung.

Zurück zum Seitenanfang

## Aktivieren von Postfachservern

Die erforderlichen Schritte zum Aktivieren von Postfachservern während eines Datencenterswitchovers hängen ebenfalls davon ab, ob sich die Database Availability Group im Aktivierungsmodus der Datenbank befindet. Vor der Aktivierung von DAG-Mitgliedern im zweiten Datencenter sollten Sie überprüfen, ob die Infrastrukturdienste im zweiten Datencenter für die Aktivierung des Messagingdiensts bereit sind.

Wenn sich die Database Availability Group im Aktivierungsmodus der Datenbank befindet, müssen die folgenden Schritte ausgeführt werden, um die Aktivierung von Postfachservern im zweiten Datencenter abzuschließen:

1.  Der Clusterdienst muss auf jedem DAG-Mitglied im zweiten Datencenter beendet werden. Verwenden Sie das Cmdlet **Stop-Service**, um den Dienst zu beenden (z. B. `Stop-Service ClusSvc`), oder führen Sie `net stop clussvc` an einer Eingabeaufforderung mit erhöhten Rechten aus.

2.  Die Postfachserver im Standbydatencenter werden dann mithilfe des Cmdlets [Restore-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351169\(v=exchg.150\)) aktiviert. Der Active Directory-Standort des Standbydatencenters wird an das Cmdlet **Restore-DatabaseAvailabilityGroup** weitergeleitet, damit die für die Wiederherstellung des Diensts zu verwendenden Server identifiziert und die Datenverfügbarkeitsgruppe zur Verwendung eines alternativen Zeugenservers konfiguriert werden. Wenn zuvor kein alternativer Zeugenserver konfiguriert wurde, können Sie einen solchen konfigurieren, indem Sie die Parameter *AlternateWitnessServer* und *AlternateWitnessDirectory* des Cmdlets [Restore-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd351169\(v=exchg.150\)) verwenden. Wird dieser Befehl erfolgreich ausgeführt, berücksichtigen die Quorumkriterien nur noch die Server im Ersatzdatencenter. Wenn in diesem Datencenter eine gerade Anzahl von Servern vorhanden ist, verwendet die DAG den alternativen Zeugenserver, der in der Einstellung für das DAG-Objekt angegeben ist.

3.  Die Datenbanken können nun aktiviert werden. Abhängig von der in der Organisation verwendeten Konfiguration geschieht dies möglicherweise nicht automatisch. Wenn in den Einstellungen der Server im Ersatzdatencenter die Aktivierung blockiert ist, führt das System kein automatisches Failover vom primären Datencenter zum Ersatzdatencenter einer beliebigen Datenbank aus. Falls für keine der Datenbankkopien im Ersatzdatencenter Failovereinschränkungen vorhanden sind, aktiviert das System Kopien im zweiten Datencenter, in der Annahme, dass diese sich in einem fehlerfreien Zustand befinden. Wenn die Aktivierung in den Datenbankeinstellungen blockiert ist, die explizit das Ausführen einer manuellen Aktion erfordern, gibt es zwei Möglichkeiten:
    
    1.  Deaktivieren Sie die Einstellung, die die Aktivierung blockiert. Dadurch kehrt das System zu seinem Standardverhalten zurück, d. h., es aktiviert jede verfügbare Kopie.
    
    2.  Lassen Sie die Einstellungen unverändert, und verwenden Sie das Cmdlet [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)), um die Datenbankaktivierung im zweiten Datencenter abzuschließen. Wenn die Aktivierung in den Einstellungen blockiert ist, müssen Sie das Ziel des Verschiebevorgangs explizit angeben, um diesen Schritt mithilfe des Cmdlets **Move-ActiveMailboxDatabase** abzuschließen.

4.  Im letzten Schritt werden alle während der einzelnen Tasks ausgegebenen Fehler und Warnmeldungen geprüft. Alle angezeigten Warnungen sollten nachverfolgt und korrigiert werden. Das Taskdesignmodell für diese Befehle sieht vor, dass nur dann Fehler ausgegeben werden, wenn die vorgesehenen Mindestziele nicht erreicht werden. Beispielsweise gibt das Cmdlet **Restore-DatabaseAvailabilityGroup** einen Fehler aus, wenn das Quorum der DAG nicht soweit reduziert werden kann, dass ein Server im zweiten Datencenter zur Bereitstellungen von Diensten neu gestartet werden kann, ohne einen Quorumausfall zu verursachen. Jede Taskausgabe wird auch zur Identifizierung von Problemen genutzt, die einen Administratoreingriff erfordern. Es wird dringend empfohlen, alle Taskausgaben zu speichern und auf möglicherweise erforderliche Aktionen zu prüfen.

Wenn sich die Database Availability Group nicht im Aktivierungsmodus der Datenbank befindet, müssen die folgenden Schritte ausgeführt werden, um die Aktivierung von Postfachservern im zweiten Datencenter abzuschließen:

1.  Das Quorum muss basierend auf der Anzahl von DAG-Mitgliedern im zweiten Datencenter geändert werden.
    
    1.  Wenn eine ungerade Anzahl von DAG-Mitgliedern vorhanden ist, ändern Sie das DAG-Modell mithilfe des folgenden Befehls von einem Quorum des Typs Knoten- und Dateifreigabemehrheit in ein Knotenmehrheitsquorum:
        
        ```powershell
cluster <DAGName> /quorum /nodemajority
```
    
    2.  Wenn eine gerade Anzahl von DAG-Mitgliedern vorhanden ist, konfigurieren Sie den Zeugenserver und das Verzeichnis neu, indem Sie in der Exchange-Verwaltungsshell den folgenden Befehl ausführen:
        
        ```powershell
Set-DatabaseAvailabilityGroup <DAGName> -WitnessServer <ServerName>
```

2.  Starten Sie den Clusterdienst für alle verbleibenden DAG-Mitglieder im zweiten Datencenter mithilfe des folgenden Befehls:
    
    ```powershell
net start clussvc
```

3.  Führen Sie zum Aktivieren der Postfachdatenbanken in der Database Availability Group einen Serverswitchover aus, indem Sie für jedes DAG-Mitglied den folgenden Befehl ausführen:
    
        Move-ActiveMailboxDatabase -Server <DAGMemberinPrimarySite> -ActivateOnServer <DAGMemberinSecondSite>

4.  Binden Sie die Postfachdatenbanken für jedes DAG-Mitglied im zweiten Standort über den folgenden Befehl ein:
    
    ```powershell
Get-MailboxDatabase <DAGMemberinSecondSite> | Mount-Database
```

Zurück zum Seitenanfang

## Aktivieren von Clientzugriffsservern

Clients verbinden sich mit Dienstendpunkten (beispielsweise Outlook Web App, AutoErmittlung, Exchange ActiveSync, Outlook Anywhere, POP3, IMAP4 und das RPC-Clientzugriffsarray), um auf Exchange-Dienste und -Daten zuzugreifen. Aus diesem Grund muss bei der Aktivierung des Clientzugriffsservers die Zuordnung der DNS-Einträge für diese Dienstendpunkte von den IP-Adressen im primären Datencenter in die IP-Adressen im zweiten Datencenter geändert werden, die als neue Dienstendpunkte fungieren. Je nach DNS-Konfiguration können sich die zu ändernden DNS-Einträge in derselben oder in unterschiedlichen DNS-Zonen befinden.

## Aktivieren von Clientzugriffsservern

Clients stellen dann auf zweierlei Art automatisch eine Verbindung mit den neuen Dienstendpunkten her:

  - Clients versuchen in regelmäßigen Abständen, eine Verbindung herzustellen, und sollten automatisch verbunden werden, nachdem die Gültigkeitsdauer für den ursprünglichen DNS-Eintrag abgelaufen ist und der Eintrag aus dem DNS-Cache des Clients entfernt wurde. Benutzer können einen DNS-Cache auch manuell löschen, indem sie den Befehl `ipconfig /flushdns` über die Eingabeaufforderung ausführen.

  - Clients führen beim Starten und Neustarten einen DNS-Suchvorgang aus und erhalten die neue IP-Adresse für den Dienstendpunkt, der ein Clientzugriffsserver oder Clientzugriffsserver-Array im zweiten Datencenter ist.

Wenn alle entsprechenden Konfigurationsänderungen durchgeführt wurden, um die Dienste im zweiten Datencenter so zu definieren und konfigurieren, dass sie wie im primären Datencenter ausgeführt werden, und wenn die eingerichtete DNS-Konfiguration korrekt ist, dann sollten keine weiteren Änderungen für die Aktivierung von Clientzugriffsservern erforderlich sein.

## Aktivieren von Transportdiensten

Clients und sonstige Server, die Nachrichten übermitteln, identifizieren diese Server in der Regel mithilfe von DNS. Das Aktivieren von Transportdiensten im zweiten Datencenter umfasst das Ändern von DNS-Datensätzen in einer Weise, dass diese auf die IP-Adressen der Postfachserver im zweiten Datencenter verweisen. Clients und weitere sendende Server stellen dann auf zweierlei Art automatisch eine Verbindung mit den Servern im zweiten Datencenter her:

  - Clients versuchen in regelmäßigen Abständen, eine Verbindung herzustellen, und sollten automatisch verbunden werden, nachdem die Gültigkeitsdauer für den ursprünglichen DNS-Eintrag abgelaufen ist und der Eintrag aus dem DNS-Cache des Clients entfernt wurde. Benutzer können einen DNS-Cache auch manuell löschen, indem sie den Befehl `ipconfig /flushdns` über die Eingabeaufforderung ausführen.

  - Clients führen beim Starten und Neustarten einen DNS-Suchvorgang aus und erhalten die neue IP-Adresse für den SMTP-Endpunkt (Simple Mail Transfer Protocol), der ein Postfachserver im zweiten Datencenter ist.

Wenn alle entsprechenden Konfigurationsänderungen durchgeführt wurden, um die Dienste im zweiten Datencenter so zu definieren und konfigurieren, dass sie wie im primären Datencenter ausgeführt werden, und wenn die eingerichtete DNS-Konfiguration korrekt ist, dann sollten keine weiteren Änderungen für die Aktivierung von Transportdiensten erforderlich sein.

## Aktivieren von Unified Messaging-Diensten

UM-Dienste (Unified Messaging) stellen eine Verbindung mit dem PBX-System und den Telefonleitungen einer Organisation her. Die logische Verbindung zwischen dem PBX-System und dem Unified Messaging-Dienst wird über ein IP-Gateway bereitgestellt. IP-Gateways bieten Funktionen für hohe Verfügbarkeit und können bei Auftreten eines Fehlers zwischen mehreren Unified Messaging-Diensten wechseln.

Wenn es Unified Messaging-Dienste im zweiten Datencenter gibt, die aufgrund ihrer Bestimmung für die Ausfallsicherheitslösung einen deaktivierten Status aufwiesen, können diese mithilfe des Cmdlets [Enable-UMService](https://technet.microsoft.com/de-de/library/jj552411\(v=exchg.150\)) aktiviert werden (z. B. `Enable-UMService EX4`).

Wenn die IP-Gateways mithilfe von DNS-Servern Unified Messaging-Dienste zugeordnet sind, müssen beim Aktivieren von Unified Messaging-Diensten DNS-Datensätze so geändert werden, dass diese auf die neuen IP-Adressen verweisen, die für die Unified Messaging-Dienst im zweiten Datencenter konfiguriert werden. Wenn alle entsprechenden Konfigurationsänderungen durchgeführt wurden, um die Dienste im zweiten Datencenter so zu definieren und konfigurieren, dass sie wie im primären Datencenter ausgeführt werden, und wenn die eingerichtete DNS-Konfiguration korrekt ist, dann sollten keine weiteren Änderungen für die Aktivierung von Unified Messaging-Diensten erforderlich sein.

Wenn das aktive IP-Gateway die Verwendung von DNS-Namen zum Auflösen der Unified Messaging-Dienste nicht unterstützt, sind zusätzliche manuelle Konfigurationsschritte erforderlich, damit das IP-Gateway auf die IP-Adressen der Unified Messaging-Dienste im zweiten Datencenter verweist.

## Aktivieren von Edge-Transport-Servern

Die Schritte zum Aktivieren der Edge-Transport-Serverrolle variieren in Abhängigkeit von der jeweiligen Konfiguration. Edge-Transport-Server in zwei Datencentern können entweder in einer Aktiv/Passiv- oder einer Aktiv/Aktiv-Konfiguration konfiguriert werden. In einer Aktiv/Passiv-Konfiguration befindet sich der Edge-Transport-Server im zweiten Datencenter bis zur Aktivierung des zweiten Datencenters im Leerlauf. In einer Aktiv/Aktiv-Konfiguration stellen Edge-Transport-Server in beiden Datencentern jederzeit Mail zu.

In einer Aktiv/Aktiv-Konfiguration sind keine zusätzlichen Schritte zur Aktivierung der Edge-Transport-Server des zweiten Datencenters erforderlich, da diese bereits ausgeführt werden. In einer Aktiv/Passiv-Konfiguration muss der DNS MX-Ressourcendatensatz (Mail-Exchanger) für jede SMTP-Domäne als Bestandteil des Switchovers vom primären Datencenter zum Ersatzdatencenter aktualisiert werden. Die Aktiv/Aktiv-Konfiguration stellt zwar eine einfache Lösung für den Switchover eines Datencenters bereit, ihr Nachteil ist jedoch die erforderliche sorgfältige Überwachung der Auslastung. Durch diese soll sichergestellt werden, dass die Edge-Transport-Server im zweiten Datencenter nach dem Switchover über ausreichend Kapazität für die erhöhte Auslastung verfügen, die das Ergebnis der nicht verfügbaren Edge-Transport-Server im primären Datencenter ist.

Selbst bei einer Aktiv/Aktiv-Konfiguration ist es ratsam, die MX-Ressourcendatensätze für die Edge-Transport-Server während eines Datencenterswitchovers zu aktualisieren. Wenn der MX-Ressourcendatensatz für das ausgefallene Datencenter weiterhin auf das ausgefallene Datencenter verweist, könnte dieses bei der Wiederherstellung versuchen, eine Verbindung mit den zugeordneten Edge-Transport-Servern herzustellen. Dieser Fall kann eintreten, während Edge-Transport-Dienste instabil sind (z. B. weil die abhängigen Dienste im Datencenter wiederhergestellt werden).

Wenn die DNS-Datensätze der Kontrolle der Organisation unterliegen, muss beim Aktivieren der Edge-Transport-Server der MX-Ressourcendatensatz für jede SMTP-Domäne aktualisiert werden, die von dem Server gehostet wird.


> [!NOTE]
> Wenn der von Ihrer Organisation verwendete MX-Ressourcendatensatz nicht von einem der Kontrolle Ihrer Organisation unterliegenden DNS-Server gehostet wird, können Sie möglicherweise auf einen CNAME-Datensatz im MX-Ressourcendatensatz verweisen und dabei einen der Kontrolle Ihrer Organisation unterliegenden CNAME-Datensatz verwenden, der dann aktualisiert werden kann.



DNS-Updates lassen eingehenden Datenverkehr zu, und der ausgehende Datenverkehr wird über die Aktivierung von Postfachdatenbanken an einem Standort verwaltet, der über funktionsfähige Edge-Transport-Server verfügt:

  - Wenn eingehende SMTP-Verbindungen mithilfe der aktualisierten Informationen zur Namensauflösung initiiert werden, stellen SMTP-Clients eine Verbindung mit den Edge-Transport-Servern im zweiten Datencenter her. Der Datenverkehr wird von den Edge-Transport-Servern entsprechend weitergeleitet, und es sind keine weiteren Änderungen erforderlich.

  - Wenn ausgehende SMTP-Verbindungen initiiert werden, werden Verbindungsversuche mit dem lokal verfügbaren Edge-Transport-Server gestartet. Diese Nachrichten werden je nach Status des empfangenden Servers in der Warteschlange platziert oder sofort gesendet.

Zurück zum Seitenanfang

## Wiederherstellen von Diensten im primären Datencenter

Im Allgemeinen sind Datencenterausfälle entweder temporär oder permanent. Bei einem permanenten Ausfall, z. B. einem Ereignis, das zu einer unwiderruflichen Zerstörung eines primären Datencenters geführt hat, sind die Chancen gering, dass das primäre Datencenter wieder aktiviert werden kann. Bei einem temporären Ausfall dagegen, z. B. einem längerfristigen Stromausfall oder weitreichenden, jedoch reparablen Schäden, ist die Möglichkeit einer vollständigen Wiederherstellung gegeben.

Der Prozess der Dienstwiederherstellung eines zuvor ausgefallenen Datencenters wird auch als *Switchback* bezeichnet. Die Schritte zur Ausführung eines Datencenterswitchbacks entsprechen den Schritten zur Ausführung eines Datencenterswitchovers. Ein bedeutender Unterschied besteht darin, dass Datencenterswitchbacks geplant sind und die Dauer des Ausfalls häufig deutlich kürzer ist.

Es ist wichtig, dass ein Switchback erst dann ausgeführt wird, wenn die Infrastrukturabhängigkeiten für Exchange reaktiviert wurden, stabil ausgeführt werden und überprüft wurden. Wenn diese Abhängigkeiten nicht verfügbar oder nicht fehlerfrei sind, ist die Wahrscheinlichkeit groß, dass der Switchbackprozess zu einem längeren Ausfall als notwendig führt, und es kann sein, dass der gesamte Vorgang fehlschlägt.

## Switchback der Postfachserverrolle

Die Postfachserverrolle sollte die erste Rolle sein, für die ein Switchback zum primären Datencenter ausgeführt wird. Die folgenden Schritte erläutern ausführlich den Switchbackprozess der Postfachserverrolle:

1.  Als Teil des Datencenterswitchovers wurden die Postfachserver im primären Datencenter beendet. Wenn die Umgebung (z. B. primäres Datencenter, Exchange-Abhängigkeiten und WAN-Konnektivität (Wide Area Network, Fernnetz)) bereitsteht, besteht der erste Schritt darin, die Postfachserver im wiederhergestellten primären Datencenter zu starten und in die Database Availability Group zu integrieren. Die für diesen Schritt erforderlichen Aktionen hängen davon ab, ob sich die Database Availability Group im Aktivierungsmodus der Datenbank befindet oder nicht.
    
    1.  Wenn sich die Database Availability Group im Aktivierungsmodus der Datenbank befindet, können Sie die DAG-Mitglieder am primären Standort mithilfe des Cmdlets [Start-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd335076\(v=exchg.150\)) erneut einbinden. Um sicherzustellen, dass das geeignete Quorummodell von der Database Availability Group verwendet wird, müssen Sie anschließend das Cmdlet [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) für die Database Availability Group ausführen, ohne hierbei Parameter anzugeben.
    
    2.  Wenn sich die Database Availability Group nicht im Aktivierungsmodus der Datenbank befindet, können Sie die DAG-Mitglieder mithilfe des Cmdlets [Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd298049\(v=exchg.150\)) erneut einbinden.

2.  Nach der Integration der Postfachserver im primären Datencenter in die Database Availability Group wird die Synchronisierung der Datenbankkopien gestartet; dies kann einige Zeit dauern. In Abhängigkeit von der Art und Länge des Ausfalls und den vom Administrator während des Ausfalls getroffenen Maßnahmen kann ein erneutes Seeding der Datenbankkopien erforderlich sein. Wenn z. B. während des Ausfalls die Datenbankkopien aus dem ausgefallenen primären Datencenter entfernt wurden, um das Abschneiden der Protokolldateien für die noch aktiven Kopien im zweiten Datencenter zuzulassen, ist ein erneutes Seeding erforderlich. Jede Datenbank kann ab diesem Zeitpunkt einzeln fortgesetzt werden. Wenn eine replizierte Datenbankkopie im primären Datencenter fehlerfrei läuft, kann der nächste Schritt ausgeführt werden.
    

    > [!NOTE]
    > Für diesen Vorgang ist kein gleichzeitiges Verschieben aller Datenbanken erforderlich. Es wird empfohlen, die Mehrzahl der Organisationsdatenbanken zeitgleich zu verschieben. Einige Datenbanken verbleiben jedoch zunächst im zweiten Datencenter, falls Probleme mit den Datenbankkopien im primären Datencenter auftreten.



3.  Sobald die meisten Datenbanken im primären Datencenter fehlerfrei ausgeführt werden, kann der durch das Switchback bedingte Ausfall geplant werden. Tritt der geplante Zeitpunkt ein, müssen die folgenden Schritte ausgeführt werden:
    
    1.  Während des Datencenterswitchovers wurde die DAG so konfiguriert, dass sie auf einen alternativen Zeugenserver zugreift. Die DAG muss erneut konfiguriert werden, damit sie einen Zeugenserver im primären Datencenter verwendet. Wenn Sie denselben Zeugenserver und dasselbe Zeugenverzeichnis verwenden, der bzw. das bereits vor dem Ausfall des primären Datencenters verwendet wurde, können Sie den Befehl `Set-DatabaseAvailabilityGroup -Identity DAGName` ausführen. Wenn Sie einen Zeugenserver oder ein Zeugenverzeichnis verwenden möchten, das sich vom ursprünglichen Zeugenserver und -verzeichnis unterscheidet, verwenden Sie den Befehl [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)), um die Parameter für Zeugenserver und Zeugenverzeichnis mit den geeigneten Werten zu konfigurieren.
    
    2.  Die Einbindung der im primären Datencenter reaktivierten Datenbanken muss im zweiten Datencenter aufgehoben werden. Mithilfe des Cmdlets [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\)) können Sie die Einbindung der Datenbanken aufheben.
    
    3.  Nachdem die Einbindung der Datenbanken aufgehoben wurde, müssen die URLs der Clientzugriffsserver vom zweiten in das primäre Datencenter geändert werden. Die geschieht durch das Ändern des DNS-Datensatzes, sodass die URLs auf den Clientzugriffsserver oder das Clientzugriffsserver-Array im primären Datencenter verweisen. Das System verhält sich so, als ob ein Datenbankfailover für jede verschobene Datenbank aufgetreten ist.
        

        > [!IMPORTANT]
        > Führen Sie den nächsten Schritt erst aus, wenn die URLs des Clientzugriffsservers geändert wurden und die DNS-Gültigkeitsdauer abgelaufen ist bzw. die DNS-Cacheeinträge entfernt wurden. Wenn die Datenbanken im primären Datencenter vor dem Ändern der Clientzugriffsserver-URLs in das primäre Datencenter aktiviert werden, ist die Konfiguration nicht gültig (z. B. eine eingebundene Datenbank, die über keine Clientzugriffsserver am Active Directory-Standort verfügt).

    
    4.  Da sich jede Datenbank im primären Datencenter in einem fehlerfreien Zustand befindet, kann sie im primären Datencenter durch das Ausführen von Datenbankswitchovern aktiviert werden. Verwenden Sie dazu das Cmdlet [Move-ActiveMailboxDatabase](https://technet.microsoft.com/de-de/library/dd298068\(v=exchg.150\)) für jede zu aktivierende Datenbank.
    
    5.  Nach dem Verschieben der Datenbanken in das primäre Datencenter können diese mithilfe des Cmdlets [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\)) eingebunden werden.

Wenn mindestens eine Datenbank aktiv ist und im primären Datencenter bereitgestellt wird, kann der Switchbackvorgang für die weiteren Serverrollen ausgeführt werden.

## Clientzugriffsserver-Switchback

Als Teil des Switchovers wurden die von Clients, sonstigen Servern und IP-Gateways für das Auflösen der Dienstendpunkte für Clientzugriffs-, Transport- und Unified Messaging-Dienste verwendeten internen und externen DNS-Datensätze so geändert, dass sie auf die entsprechenden Endpunkte im zweiten Datencenter verweisen. Der Switchbackvorgang für die weiteren Serverrollen umfasst das Ändern dieser Datensätze dahin gehend, dass diese auf die wiederhergestellten Dienstendpunkte im primären Datencenter verweisen.

Ebenso wie bei den DNS-Änderungen, die während des Switchovers zum zweiten Datencenter vorgenommen wurden, versuchen Clients, Server und IP-Gateways weiterhin, eine Verbindung herzustellen. Diese Verbindung sollte automatisch bestehen, sobald die Gültigkeitsdauer des ursprünglichen DNS-Eintrags abgelaufen ist und sobald der Eintrag aus dem DNS-Cache entfernt wurde.

Zurück zum Seitenanfang

## Wiederherstellen der Ausfallsicherheit

Nach dem erfolgreichen Switchback zum primären Datencenter können Sie dessen Ausfallsicherheit wiederherstellen, indem Sie die Integrität und den Status jeder Postfachdatenbankkopie im zweiten Datencenter überprüfen. Wenn Datenbankkopien im zweiten Datencenter ursprünglich nicht aktiviert werden konnten, können Sie diese Einstellungen nun wieder konfigurieren.

Zurück zum Seitenanfang

