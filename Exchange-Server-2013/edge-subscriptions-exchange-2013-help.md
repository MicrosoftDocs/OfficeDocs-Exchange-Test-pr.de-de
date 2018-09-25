---
title: 'Edge-Abonnements: Exchange 2013 Help'
TOCTitle: Edge-Abonnements
ms:assetid: 3addd71a-4165-401f-a009-002bcd8baba6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997438(v=EXCHG.150)
ms:contentKeyID: 61180467
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Edge-Abonnements

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Der Edge-Transport-Server reduziert die Angriffsfläche auf ein Mindestmaß. Er verarbeitet die gesamte Internetnachrichtenübermittlung und stellt SMTP-Relay- und Smarthostdienste für die Exchange-Organisation bereit. Weitere Stufen von Nachrichtenschutz und -sicherheit werden von einer Reihe von Agents bereitgestellt, die auf dem Edge-Transport-Server im Umkreisnetzwerk Ihrer Organisation ausgeführt werden. Diese Agents unterstützen die Funktionen, die Schutz vor Viren und Spam bereitstellen und Transportregeln zum Steuern des Nachrichtenflusses anwenden.

Edge-Abonnements werden verwendet, um die Active Directory Lightweight-Verzeichnisdienstinstanz (AD LDS) auf dem Edge-Transport-Server mit Daten des Active Directory-Verzeichnisdiensts zu füllen. Das Erstellen eines Edge-Abonnements ist zwar optional, wenn ein Edge-Transport-Server die Exchange-Organisation abonniert, wird jedoch die Verwaltung vereinfacht, und die Antispamfeatures werden optimiert. Sie müssen ein Edge-Abonnement erstellen, wenn Sie planen, die Empfängersuche oder die Aggregation von Listen sicherer Adressen zu verwenden bzw. die SMTP-Kommunikation mit Partnerdomänen mithilfe vom MTLS (Mutual Transport Layer Security) zu sichern.

**Inhalt**

Edge-Abonnementprozess

Microsoft Exchange EdgeSync-Dienst

Verwalten von Edge-Abonnements

## Edge-Abonnementprozess

Der Edge-Transport-Server hat keinen direkten Zugriff auf Active Directory. Die Konfiguration und die Empfängerinformationen, die der Edge-Transport-Server zum Verarbeiten von Nachrichten verwendet, sind lokal in AD LDS gespeichert. Beim Erstellen eines Edge-Abonnements wird die sichere und automatische Replikation von Informationen aus Active Directory nach AD LDS eingerichtet. Der Edge-Abonnementprozess stellt die Anmeldeinformationen bereit, die zum Herstellen einer sicheren LDAP-Verbindung zwischen Exchange 2013-Postfachservern und einem abonnierten Edge-Transport-Server erforderlich sind. Der Microsoft Exchange EdgeSync-Dienst (EdgeSync), der auf Postfachservern läuft, führt regelmäßig eine unidirektionale Synchronisierung durch, um aktuelle Daten nach AD LDS zu übertragen. Dies verringert die erforderliche Verwaltung im Umkreisnetzwerk, indem Sie den Postfachserver konfigurieren und anschließend diese Informationen mit dem Edge-Transport-Server synchronisieren.

Sie richten ein Abonnement für einen Edge-Transport-Server bei einem Active Directory-Standort ein, der die Postfachserver enthält, die für das Übertragen der Nachrichten von und zu den Edge-Transport-Servern verantwortlich sind. Der Edge-Abonnementprozess erstellt eine Mitgliedschaft beim Active Directory-Standort für den Edge-Transport-Server. Durch die Standortmitgliedschaft können die Postfachserver in der Exchange-Organisation Nachrichten mittels Relay an den Edge-Transport-Server für die Zustellung im Internet weiterleiten, ohne dass explizite Sendeconnectors konfiguriert werden müssen.

Ein oder mehrere Edge-Transport-Server können ein Abonnement für einen einzelnen Active Directory-Standort haben. Ein Edge-Transport-Server kann jedoch nur einen einzigen Active Directory-Standort abonnieren. Wenn Sie mehrere Edge-Transport-Server bereitstellen, kann jeder dieser Server einen anderen Active Directory-Standort abonnieren. Jeder Edge-Transport-Server erfordert ein einzelnes Edge-Abonnement.

Führen Sie die folgenden Schritte aus, um einen Edge-Transport-Server bereitzustellen und einen Active Directory-Standort für diesen zu abonnieren:

1.  Installieren Sie die Edge-Transport-Serverrolle.

2.  Vergewissern Sie sich, dass die Postfachserver und der Edge-Transport-Server sich gegenseitig mithilfe von DNS-Namenauflösung erkennen können.

3.  Konfigurieren Sie auf dem Postfachserver die Objekte und Einstellungen, die auf den Edge-Transport-Server repliziert werden sollen.

4.  Erstellen und exportieren Sie auf dem Edge-Transport-Server eine Edge-Abonnementdatei.

5.  Kopieren Sie die Edge-Abonnementdatei auf einen Postfachserver oder eine Dateifreigabe, auf die vom Active Directory-Standort, der die Postfachserver enthält, zugegriffen werden kann.

6.  Importieren Sie die Edge-Abonnementdatei an den Active Directory-Standort.

## Was geschieht, wenn Sie ein neues Edge-Abonnement erstellen?

Wenn Sie eine Edge-Abonnementdatei erstellen (durch Ausführen des Cmdlets **New-EdgeSubscription** auf dem Edge-Transport-Server), werden die folgenden Aktionen durchgeführt:

  - Ein AD LDS-Konto wird als ESBRA-Konto (EdgeSync Bootstrap Replication Account) erstellt. Diese ESBRA-Anmeldeinformationen werden für die Authentifizierung der ersten EdgeSync-Verbindung mit dem Edge-Transport-Server verwendet. Das Konto ist so konfiguriert, dass es 24 Stunden nach seiner Erstellung abläuft. Deshalb müssen Sie die sechs Schritte des Abonnementprozesses, die im vorhergehenden Abschnitt beschrieben wurden, innerhalb von 24 Stunden ausführen. Wenn das ESBRA-Konto abläuft, bevor der Edge-Abonnementprozess abgeschlossen ist, müssen Sie das Cmdlet **New-EdgeSubscription** erneut ausführen, um eine neue Edge-Abonnementdatei zu erstellen.

  - Die ESBRA-Anmeldeinformationen werden aus AD LDS abgerufen und in die Edge-Abonnementdatei geschrieben. Der öffentliche Schlüssel für das selbstsignierte Zertifikat des Edge-Transport-Servers wird ebenfalls in die Edge-Abonnementdatei exportiert. Die in die Edge-Abonnementdatei geschriebenen Anmeldeinformationen sind für den Server spezifisch, von dem die Datei exportiert wird.

  - Alle ggf. zuvor erstellten Konfigurationsobjekte auf dem Edge-Transport-Server, die nun aus Active Directory nach AD LDS repliziert werden, werden aus AD LDS gelöscht, und die Cmdlets der Exchange-Verwaltungsshell, die zum Konfigurieren dieser Objekte verwendet wurden, werden deaktiviert. Sie können jedoch die **Get-\***-Cmdlets, mit denen Sie diese Objekte anzeigen können, auch weiterhin verwenden. Wenn Sie das Cmdlet **New-EdgeSubscription** verwenden, werden folgende Cmdlets auf dem Edge-Transport-Server deaktiviert:
    
      - **Set-SendConnector**
    
      - **New-SendConnector**
    
      - **Remove-SendConnector**
    
      - **New-AcceptedDomain**
    
      - **Set-AcceptedDomain**
    
      - **Remove-AcceptedDomain**
    
      - **New-MessageClassification**
    
      - **Set-MessageClassification**
    
      - **Remove-MessageClassification**
    
      - **New-RemoteDomain**
    
      - **Set-RemoteDomain**
    
      - **Remove-RemoteDomain**

Wenn Sie die Edge-Abonnementdatei auf dem Postfachserver importieren, indem Sie das Cmdlet **New-EdgeSubscription** auf dem Edge-Transport-Server ausführen, passiert Folgendes:

  - Das Edge-Abonnement wird erstellt und bindet den Edge-Transport-Server in eine Exchange-Organisation ein. EdgeSync gibt die Konfigurationsdaten an diesen Edge-Transport-Server weiter und erstellt so ein Edge-Konfigurationsobjekt in Active Directory.

  - Jeder Postfachserver am Active Directory-Standort empfängt eine Benachrichtigung von Active Directory, dass ein neuer Edge-Transport-Server abonniert wurde. Der Postfachserver ruft die ESBRA-Informationen aus der Edge-Abonnementdatei ab. Der Postfachserver verschlüsselt dann die ESBRA-Informationen mithilfe des öffentlichen Schlüssels des selbstsignierten Zertifikats des Edge-Transport-Servers. Die verschlüsselten Anmeldeinformationen werden anschließend in das Edge-Konfigurationsobjekt geschrieben.

  - Jeder Postfachserver verschlüsselt außerdem die ESRA-Informationen mithilfe seines eigenen öffentlichen Schlüssels und speichert die Anmeldeinformationen dann in seinem eigenen Konfigurationsobjekt.

  - EdgeSync-Replikationskonten (EdgeSync Replication Accounts, ESRA) werden in Active Directory für jedes Paar aus Edge-Transport-Postfachservern erstellt. Jeder Postfachserver speichert seine ESRA-Anmeldeinformationen als ein Attribut des Postfachserver-Konfigurationsobjekts.

  - Sendeconnectors werden automatisch für Weiterleiten von Nachrichten mittels Relay erstellt, die vom Edge-Transport-Server in das Internet ausgehen bzw. vom Edge-Transport-Server in die Exchange-Organisation eingehen.

  - Der Microsoft Exchange EdgeSync-Dienst, der auf Postfachservern ausgeführt wird, verwendet die ESBRA-Anmeldeinformationen, um eine sichere LDAP-Verbindung zwischen einem Postfachserver und dem Edge-Transport-Server herzustellen und die anfängliche Replikation der Daten auszuführen. Die folgenden Daten werden nach AD LDS repliziert:
    
      - Topologiedaten
    
      - Konfigurationsdaten
    
      - Empfängerdaten
    
      - ESRA-Anmeldeinformationen

  - Der Microsoft Exchange-Anmeldeinformationsdienst, der auf dem Edge-Transport-Server ausgeführt wird, installiert die ESRA-Anmeldeinformationen. Diese Anmeldeinformationen werden zum Authentifizieren und Sichern späterer Synchronisierungssitzungen verwendet.

  - Der Zeitplan für die EdgeSync-Synchronisierung wird eingerichtet.

Der Microsoft Exchange EdgeSync-Dienst, der auf den Postfachservern am abonnierten Active Directory-Standort ausgeführt wird, führt dann regelmäßig eine unidirektionale Replikation von Daten aus Active Directory zu AD LDS durch. Sie können auch das Cmdlet **Start-EdgeSynchronization** verwenden, um den Zeitplan für die EdgeSync-Synchronisierung außer Kraft zu setzen und mit der Synchronisierung sofort zu beginnen.

Weitere Informationen zu ESRA-Konten und deren Verwendung zum Sichern des EdgeSync-Synchronisierungsprozesses finden Sie unter [Edge-Abonnementanmeldeinformationen](edge-subscription-credentials-exchange-2013-help.md).

In diesem Beispiel wird ein Abonnement des Edge-Transport-Servers mit dem angegebenen Standort hergestellt. Gleichzeitig werden automatisch der Internet-Sendeconnector und der Sendeconnector vom Edge-Transport-Server zu den Postfachservern erstellt.

```powershell
    New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "C:\EdgeSubscriptionInfo.xml" -Encoding Byte -ReadCount 0)) -CreateInternetSendConnector $true -CreateInboundSendConnector $true -Site "Default-First-Site-Name" 
```


> [!NOTE]
> Die Standardwerte der Parameter <EM>CreateInternetSendConnector</EM> und <EM>CreateInboundSendConnector</EM> sind beide <CODE>$true</CODE>. Die Parameter werden hier nur zu Demonstrationszwecken gezeigt.



In diesem Beispiel wird eine Edge-Abonnementdatei exportiert.

```powershell
    New-EdgeSubscription -FileName "C:\EdgeSubscriptionInfo.xml"
```


> [!NOTE]
> Wenn Sie das Cmdlet <STRONG>New-EdgeSubscription</STRONG> auf dem Edge-Transport-Server ausführen, wird eine Eingabeaufforderung angezeigt, in der Sie die zu deaktivierenden Befehle und die Konfiguration, die auf dem Edge-Transport-Server überschrieben wird, bestätigen müssen. Um diese Bestätigung zu umgehen, müssen Sie den Parameter <EM>Force</EM> verwenden. Dieser Parameter ist hilfreich, wenn Sie ein Skript für das Cmdlet <STRONG>New-EdgeSubscription</STRONG> erstellen. Der Parameter <EM>Force</EM> wird auch zum Überschreiben einer vorhandenen Datei verwendet, die den gleichen Namen hat wie die Datei, die Sie zum erneuten Abonnieren eines Edge-Transport-Servers erstellen.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-EdgeSubscription](https://technet.microsoft.com/de-de/library/bb123800\(v=exchg.150\)).

## Beim Edge-Abonnementprozess erstellte Sendeconnectors

Wenn Sie den empfohlenen Edge-Abonnementprozess durch Importieren der Edge-Abonnementdatei auf einen Postfachserver abschließen, werden standardmäßig die Sendeconnectors, die für die Aktivierung der End-to-End-Nachrichtenübermittlung zwischen dem Internet und der Exchange-Organisation erforderlich sind, automatisch erstellt. Alle ggf. vorhandenen Sendeconnectors auf dem Edge-Transport-Server werden gelöscht. Sie können die automatische Erstellung von Sendeconnectors unter Umständen auch unterdrücken und Sendeconnectors manuell konfigurieren. Weitere Informationen zum manuellen Konfigurieren von Sendeconnectors finden Sie unter [Manuelles Konfigurieren der Edge-Transport-Server-Nachrichtenübermittlung](manually-configure-edge-transport-server-mail-flow-exchange-2013-help.md) und [Konfigurieren der Internetnachrichtenflusses über einen Edge-Transport-Server ohne Verwendung von EdgeSync](configure-internet-mail-flow-through-an-edge-transport-server-without-using-edgesync-exchange-2013-help.md).

Der Edge-Abonnementprozess stellt die folgenden Sendeconnectors bereit:

  - Einen Sendeconnector, der für das Weiterleiten von E-Mail-Nachrichten aus der Exchange-Organisation in das Internet konfiguriert ist.

  - Einen Sendeconnector, der für das Weiterleiten von E-Mail-Nachrichten vom Edge-Transport-Server in die Exchange-Organisation konfiguriert ist.

Durch Abonnieren eines Edge-Transport-Servers bei der Exchange-Organisation können außerdem Postfachserver am abonnierten Active Directory-Standort die organisationsinternen Sendeconnectors für das Weiterleiten von Nachrichten auf diesen Edge-Transport-Server verwenden.

## Automatisches Erstellen eines eingehenden Sendeconnectors zum Empfang von Nachrichten aus dem Internet

Wenn Sie das Cmdlet **New-EdgeSubscription** auf dem Postfachserver ausführen, wird der Parameter *CreateInboundSendConnector* des eingehenden Sendeconnectors auf den Wert `$true` festgelegt. Auf diese Weise wird der benötigte Sendeconnector zum Senden von Nachrichten an die Exchange-Organisation erstellt. Die folgende Tabelle zeigt die Konfiguration dieses Sendeconnectors.

### Konfiguration des automatisch erstellten Sendeconnectors für eingehende Nachrichten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>EdgeSync - Eingehend an &lt;<em>Standortname</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p><em>AddressSpaces</em></p></td>
<td><p><code>SMTP:--;1</code></p>
<p>Der Wert <code>--</code> im Adressraum stellt die autorisierenden und internen Relay-akzeptierten Domänen für die Exchange-Organisation dar. Alle Nachrichten, die der Edge-Transport-Server für diese akzeptierten Domänen empfängt, werden an diesen Sendeconnector weitergeleitet und dann mittels Relay an die Smarthosts weitergeleitet.</p></td>
</tr>
<tr class="odd">
<td><p><em>SourceTransportServers</em></p></td>
<td><p>&lt;<em>Edge-Abonnementname</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p><em>DNSRoutingEnabled</em></p></td>
<td><p>False</p></td>
</tr>
<tr class="even">
<td><p><em>SmartHosts</em></p></td>
<td><p><code>--</code></p>
<p>Der Wert <code>--</code> in der Liste der Smarthosts stellt alle Postfachserver am abonnierten Active Directory-Standort dar. Alle Postfachserver, die Sie zum abonnierten Active Directory-Standort hinzufügen, nachdem Sie das Edge-Abonnement eingerichtet haben, nehmen nicht am Edge-Synchronisierungsprozess teil. Sie werden jedoch automatisch der Liste der Smarthosts für den automatisch erstellten Sendeconnector für eingehende Nachrichten hinzugefügt. Wenn sich mehrere Postfachserver am abonnierten Active Directory-Standort befinden, findet für eingehende Verbindungen Lastenausgleich zwischen den Smarthosts statt.</p></td>
</tr>
</tbody>
</table>


Sie können den Adressraum oder die Liste der Smarthosts für den automatisch erstellten eingehenden Sendeconnector nicht ändern. Sie können jedoch den Parameter *CreateInboundSendConnector* auf den Wert `$false` setzen, wenn Sie ein Edge-Abonnement erstellen. Auf diese Weise können Sie einen Sendeconnector vom Edge-Transport-Server zur Exchange-Organisation manuell konfigurieren.

## Automatisches Erstellen eines ausgehenden Sendeconnectors zum Senden von Nachrichten an das Internet

Wenn Sie das Cmdlet **New-EdgeSubscription** auf dem Postfachserver ausführen, wird der Parameter *CreateInternetSendConnector* des ausgehenden Sendeconnectors auf den Wert `$true` festgelegt. Auf diese Weise wird der benötigte Sendeconnector zum Senden von Nachrichten an das Internet erstellt. Die folgende Tabelle zeigt die Standardkonfiguration dieses Sendeconnectors.

### Konfiguration des automatisch erstellten Internetsendeconnectors

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>EdgeSync - &lt;<em>Standortname</em>&gt; an Internet</p></td>
</tr>
<tr class="even">
<td><p><em>AddressSpaces</em></p></td>
<td><p><code>SMTP:*;100</code></p></td>
</tr>
<tr class="odd">
<td><p><em>SourceTransportServers</em></p></td>
<td><p>&lt;<em>Edge-Abonnementname</em>&gt;</p>

> [!NOTE]
> Der Name des Edge-Abonnements ist mit dem Namen des abonnierenden Edge-Transport-Servers identisch.


</td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p><em>DNSRoutingEnabled</em></p></td>
<td><p>True</p></td>
</tr>
<tr class="even">
<td><p><em>DomainSecureEnabled</em></p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


Wenn mehrere Edge-Transport-Server den gleichen Active Directory-Standort abonniert haben, werden keine zusätzlichen Sendeconnectors in das Internet erstellt. In diesem Fall werden alle Edge-Abonnements dem gleichen Sendeconnector als Quellserver hinzugefügt. Dies bewirkt einen Lastenausgleich für ausgehende Verbindungen in das Internet zwischen den abonnierten Edge-Transport-Servern.

Der ausgehende Sendeconnector ist für das Senden von E-Mail-Nachrichten von der Exchange-Organisation an alle Remote-SMTP-Domänen konfiguriert, mithilfe von DNS-Routing zum Auflösen von Domänennamen in MX-Datensätze. Ausführliche Informationen zum manuellen Konfigurieren einer Connectorkonfiguration finden Sie unter [Manuelles Konfigurieren der Edge-Transport-Server-Nachrichtenübermittlung](manually-configure-edge-transport-server-mail-flow-exchange-2013-help.md).

## Microsoft Exchange EdgeSync-Dienst

Nachdem Sie einen Active Directory-Standort für einen Edge-Transport-Server abonnieren, repliziert EdgeSync die Konfigurations- und Empfängerdaten an die Edge-Transport-Server. Der Dienst repliziert die folgenden Daten von Active Directory nach AD LDS:

  - Sendeconnectorkonfiguration

  - Akzeptierte Domänen

  - Remotedomänen

  - Nachrichtenklassifikationen

  - Listen sicherer Absender

  - Listen blockierter Absender

  - Empfänger

  - Liste der Absender- und Empfängerdomänen, die bei der sicheren Domänenkommunikation mit Partnern verwendet werden

  - Liste der SMTP-Server, die in der Transportkonfiguration Ihrer Organisation als intern aufgelistet sind

  - Liste der Postfachserver am abonnierten Active Directory-Standort

Ausführliche Informationen zu den nach AD LDS replizierten Daten und ihre Verwendung finden Sie unter [EdgeSync-Replikationsdaten](edgesync-replication-data-exchange-2013-help.md).

EdgeSync verwendet einen gegenseitig authentifizierten und autorisierten LDAP-Kanal zum Übertragen von Daten vom Postfachserver zum Edge-Transport-Server.

Um Daten nach AD LDS zu replizieren, geht der Postfachserver eine Bindung mit einem globalen Katalogserver ein, um aktualisierte Daten abzurufen. EdgeSync leitet eine sichere LDAP-Sitzung zwischen einem Postfachserver und dem abonnierten Edge-Transport-Server über den nicht standardmäßigen TCP-Port 50636 ein.

Wenn Sie erstmals einen Active Directory-Standort für den Edge-Transport-Server abonnieren, füllt die anfängliche Replikation AD LDS mit Daten aus Active Directory auf. Dies kann abhängig von der Menge der Daten im Verzeichnisdienst fünf Minuten oder länger dauern. Nach der anfänglichen Replikation synchronisiert EdgeSync nur noch neue oder geänderte Objekte und entfernt gelöschte Objekte.

## Synchronisationszeitplan

Verschiedene Typen von Daten werden mit verschiedenen Zeitplänen synchronisiert. Der Zeitplan für die EdgeSync-Synchronisierung gibt das maximale Zeitintervall zwischen EdgeSync-Synchronisierungen an. Die EdgeSync-Synchronisierung tritt in den folgenden Intervallen auf:

  - Konfigurationsdaten: 3 Minuten.

  - Empfängerdaten: 5 Minuten.

  - Topologiedaten: 5 Minuten

Sie können diese Intervalle mithilfe des Cmdlets **Set-EdgeSyncServiceConfig** ändern. Wenn Sie das Cmdlet **Start-EdgeSynchronization** auf dem Postfachserver verwenden, um die Synchronisierung des Edge-Abonnements zu erzwingen, wird der Zeitgeber für den nächsten Zeitpunkt der geplanten EdgeSync-Synchronisierung außer Kraft gesetzt und EdgeSync sofort gestartet.

## Auswahl der Postfachserver

Jeder abonnierte Edge-Transport-Server ist einem bestimmten Active Directory-Standort zugeordnet. Wenn mehrere Postfachserver am Standort vorhanden sind, kann jeder von ihnen Daten auf die abonnierten Edge-Transport-Server replizieren. Um bei der Synchronisation Konflikte unter den Postfachservern zu vermeiden, findet die Auswahl des bevorzugten Postfachservers wie folgt statt:

1.  Der erste Postfachserver am Active Directory-Standort, der einen Topologiescan durchführt und das neue Edge-Abonnement erkennt, führt die anfängliche Replikation durch. Da diese Erkennung auf dem Zeitpunkt des Topologiescans basiert, kann jeder Postfachserver am Standort die anfängliche Replikation durchführen.

2.  Der Postfachserver, der die Anfangsreplikation ausführt, richtet eine EdgeSync-Leaseoption ein und setzt eine Sperre für das Edge-Abonnement. Die Leaseoption legt den betreffenden Postfachserver als den bevorzugten Server zum Bereitstellen von Synchronisationsdiensten für den Edge-Transport-Server fest. Die Sperre verhindert, dass der EdgeSync-Dienst auf einem anderen Postfachserver die Leaseoption übernimmt.

3.  Die EdgeSync-Leaseoption hat für eine Stunde Bestand. Während dieser Stunde kann kein anderer EdgeSync-Dienst die Option übernehmen, es sei denn, es findet vor dem Ablauf der Stunde eine manuelle Synchronisation statt. Wenn der bevorzugte Postfachserver nicht verfügbar ist, um den EdgeSync-Dienst beim Ausführen der manuellen Synchronisation bereitzustellen, wird die Sperre nach einer Wartezeit von fünf Minuten aufgehoben, und ein anderer EdgeSync-Dienst kann die Leaseoption übernehmen und die Synchronisation ausführen.

4.  Wenn keine manuelle Synchronisation ausgeführt wird, findet die Synchronisation basierend auf dem EdgeSync-Synchronisationszeitplan statt. Wenn der bevorzugte Server beim Ausführen der planmäßigen Synchronisation nicht verfügbar ist, wird die Sperre nach einer Wartezeit von fünf Minuten freigegeben, und ein anderer EdgeSync-Dienst kann die Leaseoption übernehmen und die Synchronisation ausführen.

Diese Sperr- und Leasemethode verhindert, dass mehr als eine EdgeSync-Instanz Daten zur gleichen Zeit auf den gleichen Edge-Transport-Server schreibt.


> [!NOTE]
> Falls Sie außerdem Exchange 2010- oder Exchange 2007-Postfachserver am abonnierten Active Directory-Standort haben, erhalten Exchange 2013-Postfachserver immer Vorrang und führen die Replikation aus.




> [!NOTE]
> Wenn ein Edge-Transport-Server einen Active Directory-Standort abonniert hat, können alle Postfachserver, die an diesem Active Directory-Standort installiert sind, am EdgeSync-Synchronisationsprozess teilnehmen. Wird einer dieser Server entfernt, führt der EdgeSync-Dienst, der auf den verbleibenden Postfachservern ausgeführt wird, den Datensynchronisierungsvorgang fort. Wenn Sie jedoch später neue Postfachserver am Active Directory-Standort installieren, nehmen diese nicht automatisch am EdgeSync-Synchronisationsprozess teil. Falls Sie diese neuen Postfachserver zur Teilnahme am EdgeSync-Synchronisationsprozess aktivieren möchten, müssen Sie das Abonnement des Edge-Transport-Servers erneuern.



In der folgenden Tabelle sind die EdgeSync-Eigenschaften aufgelistet, die sich auf die Sperr- und Leaseprozesse beziehen. Sie können das Cmdlet **Set-EdgeSyncServiceConfig** verwenden, um diese Eigenschaften zu konfigurieren.

### EdgeSync-Leaseeigenschaften

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>LockDuration</em></p></td>
<td><p><code>00:05:00</code> (5 Minuten)</p></td>
<td><p>Diese Einstellung bestimmt, für wie lange Zeit ein bestimmter EdgeSync-Dienst eine Sperre erwerben kann. Wenn der EdgeSync-Dienst auf dem Postfachserver, der diese Sperre enthält, nicht reagiert, dauert es fünf Minuten, bis der EdgeSync-Dienst auf einem anderen Postfachserver die Lease übernimmt. Durch Erzwingen der sofortigen EdgeSync-Synchronisation wird diese Einstellung nicht außer Kraft gesetzt.</p></td>
</tr>
<tr class="even">
<td><p><em>OptionDuration</em></p></td>
<td><p><code>01:00:00</code> (1 Stunde)</p></td>
<td><p>Diese Einstellung bestimmt, für wie lange ein EdgeSync-Dienst eine Leaseoption auf einem Edge-Transport-Server deklarieren kann. Wenn der EdgeSync-Dienst, der die Lease hält, nicht verfügbar ist und während des Optionszeitraums auch keinen Neustart durchführt, übernimmt kein anderer Exchange EdgeSync-Dienst die Leaseoption, bis die EdgeSync-Synchronisation erzwungen wird.</p></td>
</tr>
<tr class="odd">
<td><p><em>LockRenewalDuration</em></p></td>
<td><p><code>00:01:00</code> (1 Minute)</p></td>
<td><p>Diese Einstellung bestimmt, wie häufig das Sperrfeld aktualisiert wird, wenn ein EdgeSync-Dienst eine Sperre auf einem Edge-Transport-Server erworben hat.</p></td>
</tr>
</tbody>
</table>


## Vorbereiten der Ausführung des EdgeSync-Dienstes

Bevor Sie ein Abonnement für den Edge-Transport-Server bei Ihrer Exchange-Organisation einrichten können, müssen Sie sicherstellen, dass die Infrastruktur und die Postfachserver für den EdgeSync-Dienst vorbereitet sind. Zur Vorbereitung der EdgeSync-Synchronisierung gehen Sie wie folgt vor:

  - Stellen Sie sicher, dass die Firewall des Umkreisnetzwerks, die den Edge-Transport-Server von der Exchange-Organisation trennt, so konfiguriert ist, dass die Kommunikation über die richtigen Ports möglich ist. Der Edge-Transport-Server verwendet nicht standardmäßige LDAP-Ports. Falls Ihre Umgebung bestimmte Ports erfordert, können Sie das im Lieferumfang von Exchange enthaltene Skript "ConfigureAdam.ps1" verwenden, um die von AD LDS verwendeten Ports zu ändern. Weitere Informationen finden Sie unter [Ändern der AD LDS-Konfiguration](modify-ad-lds-configuration-exchange-2013-help.md). Ändern Sie die Ports, bevor Sie das Edge-Abonnement erstellen. Wenn Sie die Ports ändern, nachdem Sie das Edge-Abonnement erstellt haben, müssen Sie das Abonnement entfernen und dann ein neues Edge-Abonnement erstellen. Standardmäßig werden die folgenden LDAP-Ports für den Zugriff auf AD LDS verwendet:
    
      - **LDAP**   Anschluss 50389/TCP wird lokal zum Binden an die AD LDS-Instanz verwendet. Dieser Port muss auf der Firewall des Umkreisnetzwerks nicht geöffnet sein.
    
      - **Sicheres LDAP**   Anschluss 50636/TCP wird für die Verzeichnissynchronisierung von Postfachservern auf AD LDS verwendet. Dieser Port muss für eine erfolgreiche EdgeSync-Synchronisierung auf der Firewall offen sein.

  - Vergewissern Sie sich, dass die gegenseitige Auflösung des DNS-Hostnamens zwischen dem Edge-Transport-Server und den Postfachservern erfolgreich ist.

  - Lizenzieren Sie den Edge-Transport-Server. Die Lizenzierungsinformationen für den Edge-Transport-Server werden erfasst, nachdem das Edge-Abonnement erstellt wurde. Abonnierte Edge-Transport-Server müssen bei der Exchange-Organisation ein Abonnement erhalten, nachdem der Lizenzschlüssel auf dem Edge-Transport-Server angewendet wurde. Wird der Lizenzschlüssel auf dem Edge-Transport-Server angewendet, nach das Edge-Abonnementverfahren durchgeführt wurde, werden die Lizenzierungsinformationen in der Exchange-Organisation nicht aktualisiert, und Sie müssen den Edge-Transport-Server erneut abonnieren.

  - Konfigurieren Sie die folgenden Einstellungen für die Übermittlung an den Edge-Transport-Server:
    
      - **Interne SMTP-Server**   Verwenden Sie den Parameter *InternalSMTPServers* des Cmdlets **Set-TransportConfig**, um eine Liste von IP-Adressen oder IP-Adressbereichen des internen SMTP-Servers anzugeben, die von den Sender ID- und Verbindungsfilter-Agents auf dem Edge-Transport-Server ignoriert werden.
    
      - **Akzeptierte Domänen**   Konfigurieren Sie alle autoritativen Domänen, internen Relaydomänen und externen Relaydomänen.
    
      - **Remotedomänen**   Konfigurieren Sie die Remotedomäneneinstellungen.

Zurück zum Seitenanfang

## Verwalten von Edge-Abonnements

Schrittweise Anweisungen zu Verwaltungsaufgaben für Edge-Abonnements finden Sie unter [Verwaltung von Edge-Abonnements](manage-edge-subscriptions-exchange-2013-help.md).

