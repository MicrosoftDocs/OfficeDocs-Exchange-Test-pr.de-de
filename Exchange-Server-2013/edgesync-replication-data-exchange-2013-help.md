---
title: 'EdgeSync-Replikationsdaten: Exchange 2013 Help'
TOCTitle: EdgeSync-Replikationsdaten
ms:assetid: c7dd137d-7ed4-4f16-9895-f354c449cf9b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232177(v=EXCHG.150)
ms:contentKeyID: 61180472
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# EdgeSync-Replikationsdaten

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Wenn Sie einen Edge-Transport-Server bereitstellen, hat er keinen Zugriff auf das Active Directory. Zum Ausführen der Empfängersuche und der Aggregation von Listen sicherer Empfänger und zum Implementieren von Domänensicherheit mithilfe von MTLS (Mutual Transport Layer Security) mit gegenseitiger Authentifizierung benötigt der Edge-Transport-Server Daten aus dem Active Directory. Diese Daten werden auf den Edge-Transport-Server mithilfe des EdgeSync-Vorgangs repliziert. Der Edge-Transport-Server speichert alle replizierten Informationen in Active Directory Lightweight Directory Services (AD LDS).

In diesem Abschnitt werden die auf dem Edge-Transport-Server vom Active Directory zum AD LDS replizierten Daten beschrieben, die auf einer Active Directory-Website abonniert werden. Weitere Informationen zu EdgeSync und Edge-Abonnements finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

Vier Datentypen werden an den AD LDS repliziert und vom Edge-Transport-Server verwendet:

Edge-Abonnementinformationen

Konfigurationsinformationen

Empfängerinformationen

Topologieinformationen

## Edge-Abonnementinformationen

Exchange 2013 erweitert die Schemas des Active Directory und AD LDS, um Attribute im Objekt **ms-Exch-ExchangeServer** bereitzustellen, die zur Darstellung der zum Steuern des EdgeSync-Synchronisationsprozesses erforderlichen Daten dienen. Diese Attribute stellen EdgeSync drei Funktionen zur Verfügung:

  - Sie stellen die automatische Bereitstellung und Wartung der Anmeldeinformationen bereit, die verwendet werden, um das Schützen der LDAP-Verbindung zwischen einem Postfachserver und einem abonnierten Edge-Transport-Server zu unterstützen.

  - Sie handeln den Sperr- und Freigabeprozess der Synchronisation aus, durch den sichergestellt wird, dass jeweils nur ein Server die Synchronisation mit einem einzelnen Edge-Transport-Server versucht. Weitere Informationen zum Sperr- und Freigabeprozess finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - Optimiert die EdgeSync-Synchronisierung, um einen Datensatz des aktuellen Synchronisierungsstatus zu verwalten. Durch das leichte Anzeigen des Synchronisierungsstatus kann eine übermäßige manuelle Synchronisierung vermieden werden.

In der folgenden Tabelle sind die Schemaerweiterungen aufgelistet, die für Edge-Abonnements spezifisch sind. Die den betreffenden Attributen zugeordneten Werte werden vom Edge-Abonnement und EdgeSync verwaltet; sie sind nicht dazu bestimmt, manuell bearbeitet zu werden.

### Schemaerweiterungen für Edge-Abonnements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Attributname</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ms-Exch-Server-EKPK-Public-Key</strong></p></td>
<td><p>Der aktuelle öffentlichen Schlüssel für das vom Server verwendete Zertifikat. Dieser Wert wird sowohl von Edge-Transport-Servern als auch von Postfachservern gespeichert. Der öffentliche Schlüssel wird zum Verschlüsseln der Anmeldeinformationen verwendet, die zur Authentifizierung des Servers während der LDAP- und SMTP-Kommunikation verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>ms-Exch-EdgeSync-Credential</strong></p></td>
<td><p>Die Liste der Anmeldeinformationen, die vom  -EdgeSync-Dienst zum Einrichten einer authentifizierten LDAP-Sitzung mit AD LDS verwendet werden. Auf Postfachservern enthält dieses Attribut nur die Anmeldeinformationen, die vom Postfachserver für die Authentifizierung bei den abonnierten Edge-Transport-Servern verwendet werden. Auf Edge-Transport-Servern enthält dieses Attribut die Anmeldeinformationen jedes Postfachservers auf der abonnierten Active Directory-Website, der am EdgeSync-Synchronisationsprozess teilnimmt. Dieses Attribut ist nur auf Postfachservern, auf denen der EdgeSync-Synchronisationsprozess ausgeführt wird, sowie auf abonnierten Edge-Transport-Servern vorhanden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ms-Exch-Edge-Sync-Lease</strong></p></td>
<td><p>Wird verwendet, um zwischen Postfachservern zu vermitteln, wenn mehr als ein Postfachserver versucht, auf den gleichen Edge-Transport-Server zu replizieren.</p></td>
</tr>
<tr class="even">
<td><p><strong>ms-Exch-Edge-Sync-Status</strong></p></td>
<td><p>Nur in AD LDS im Edge-Transport-Serverobjekt vorhanden. Dieses Attribut verfolgt den Replikationsstatus auf eine AD LDS-Instanz nach und enthält Informationen zur Replikation.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Konfigurationsinformationen

Wenn Sie einen Edge-Transport-Server für eine Organisation abonnieren, können Sie die Konfigurationsobjekte, die für einen Edge-Transport-Server üblich sind, und die Exchange-Organisation von innen verwalten. Die Änderungen werden dann mithilfe des  -EdgeSync-Diensts auf den Edge-Transport-Server repliziert. Dieser Prozess unterstützt Sie beim der Aufrechterhaltung einer konsistenten Konfiguration auf allen an der Nachrichtenverarbeitung beteiligten Servern.

Eine Teilmenge der Konfigurationsdaten für die Exchange-Organisation muss auch auf dem Edge-Transport-Server verwaltet werden. Während des EdgeSync-Synchronisierungsvorgangs werden die Konfigurationsdaten, die vom Edge-Transport-Server benötigt werden, in die Konfigurationspartition von AD LDS geschrieben. Zu den in die Konfigurationsdaten in AD LDS geschriebenen Daten gehören:

  - **Postfachserver**   Der vollqualifizierte Domänenname (FQDN) jedes Postfachservers auf der abonnierten Active Directory-Website wird dem lokalen AD LDS-Speicher auf dem Edge-Transport-Server zur Verfügung gestellt. Diese Informationen werden verwendet, um eine Liste der Smarthostserver für den eingehenden Sendeconnector abzuleiten.

  - **Akzeptierte Domänen**   Alle autorisierenden, internen und externen Relaydomänen, die für die Exchange-Organisationen konfiguriert sind, werden nach AD LDS geschrieben. Die Verfügbarkeit der akzeptierten Domänen für den Edge-Transport-Server ermöglicht der Exchange-Organisation, Domänenfilterung auszuführen und ungültigen SMTP-Verkehr so früh wie möglich in der Organisation zurückzuweisen. Weitere Informationen zu akzeptierten Domänen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

  - **Nachrichtenklassifikation**   Wenn Nachrichtenklassifikationen auf dem Edge-Transport-Server zur Verfügung stehen, können Transport-Agents und Inhaltskonvertierung auf Nachrichtenklassifikationen im Umkreisnetzwerk arbeiten. Der Anlagenfilter-Agent kann beispielsweise die Klassifizierung „Anlage entfernt“ anwenden, wenn er eine Anlage entfernt, Informationstext an einen Benutzer von Microsoft Outlook oder einen Outlook Web App-Benutzer senden, um dem Empfänger mitzuteilen, was passiert ist. Agents, die für die Verwendung durch Anwendungen von Drittanbietern entwickelt wurden, können Nachrichtenklassifikationen in ähnlicher Weise verwenden.

  - **Remotedomänen**   Alle Richtlinien für Remotedomänen, die für die Exchange-Organisation konfiguriert wurden, werden nach AD LDS geschrieben. Richtlinien für Remotedomänen steuern die Einstellungen für Abwesenheitsbenachrichtigungen und die Nachrichtenformateinstellungen für eine Remotedomäne. Weitere Informationen zu Remotedomänen finden Sie unter [Remotedomänen](remote-domains-exchange-2013-help.md).

  - **Sendeconnectors**   Standardmäßig werden die Sendeconnectors, die zum Aktivieren des End-to-End-Nachrichtenflusses zwischen der Exchange-Organisation und dem Internet erforderlich sind, automatisch durch das Erstellen eines Edge-Abonnements zum Zeitpunkt des Abonnierens des Edge-Transport-Servers erstellt. Alle ggf. vorhandenen Sendeconnectors auf dem Edge-Transport-Server werden gelöscht. Wenn Sie weitere Sendeconnectors konfigurieren möchten, konfigurieren Sie den Sendeconnector innerhalb der Exchange-Organisation und wählen Edge-Abonnement als Quellserver für den Connector aus. Weitere Informationen finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - **Interne SMTP-Server**   Der Wert für das Attribut *InternalSMTPServers* ist im **TransportConfig**-Objekt sowohl für die Exchange-Organisation als auch für den lokalen Edge-Transport-Server gespeichert. Während des EdgeSync-Synchronisierungsvorgangs wird der Wert, der im lokalen Edge-Transport-Serverobjekt gespeichert ist, mit dem Wert überschrieben, der in diesem Objekt für die Exchange-Organisation gespeichert ist. Dieses Attribut gibt eine Liste von internen SMTP-Server-IP-Adressen oder -IP-Adressbereichen an, die von der Sender ID- und der Verbindungsfilterung ignoriert werden sollen.

  - **Listen sicherer Domänen**   Die Attribute *TLSReceiveDomainSecureList* und *TLSSendDomainSecureList* sind sowohl für die Exchange-Organisation als auch für den lokalen Edge-Transport-Server im **TransportConfig**-Objekt gespeichert. Während des EdgeSync-Synchronisierungsvorgangs wird der Wert, der im lokalen Edge-Transport-Serverobjekt gespeichert ist, mit dem Wert überschrieben, der in diesem Objekt für die Exchange-Organisation gespeichert ist. In diesen Attributen ist die Liste der Remotedomänen angegeben, die für gegenseitige TLS-Authentifizierung konfiguriert ist.

Zurück zum Seitenanfang

## Empfängerinformationen

Die Empfängerinformationen, die nach AD LDS repliziert werden, enthalten nur eine Teilmenge der Empfängerattribute. Es werden nur die Daten repliziert, die der Edge-Transport-Server zum Ausführen bestimmter Antispamtasks benötigt. In AD LDS replizierte Empfängerinformationen umfassen:

  - **Empfänger   **Die Liste der Empfänger in der Exchange-Organisation wird nach AD LDS repliziert. Jeder Empfänger wird durch den zugewiesenen Active Directory-GUID identifiziert. Wenn Sie das Benutzerkonto eines Empfängers so konfigurieren, dass der Empfang von E-Mail-Nachrichten von außerhalb der Organisation verweigert wird, wird der betreffende Empfänger nicht nach AD LDS repliziert. Wenn Sie ein Postfach für einen Empfänger deaktivieren oder löschen, wird es nicht nach AD LDS repliziert.

  - **Proxyadressen**   Alle Proxyadressen, die jedem der Empfänger zugewiesen wurden, werden als gehashte Daten nach AD LDS repliziert. Hierbei handelt es sich um einen Einweghash, der SHA-256 verwendet (Secure Hash Algorithm). SHA-256 erzeugt einen 256-Bit-Nachrichtenhash der Originaldaten. Das Speichern von Proxyadressen als gehashte Daten trägt zum Schützen dieser Informationen im Fall einer Beschädigung des Edge-Transport-Servers oder von AD LDS bei. Proxyadressen werden referenziert, wenn der Edge-Transport-Server den Antispamtask Empfängersuche ausführt.

  - **Liste sicherer Absender, Liste blockierter Absender und Liste sicherer Empfänger**   Die Liste der sicheren Absender, der blockierten Absender und der sicheren Empfänger, die in der Outlook-Instanz jedes Empfängers definiert sind, werden aggregiert und nach AD LDS repliziert. Diese Einstellungen werden in dem Postfachspeicher gespeichert, in dem sich das Empfängerpostfach befindet. Die Sammlung von Listen sicherer Adressen eines -Benutzers enthält die zusammengefassten Daten aus den Listen sicherer Absender, sicherer Empfänger, blockierter Absender und externer Kontakte des betreffenden Benutzers. Die Verfügbarkeit der zusammengefassten Daten der sicheren Listen in AD LDS ermöglicht dem Edge-Transport-Server das Durchsuchen der Absender und verringert den betrieblichen Mehraufwand beim Filtern von E-Mail. Diese Informationen werden als gehashte Daten gesendet.
    

    > [!IMPORTANT]
    > Obwohl die Daten sicherer Empfänger in Outlook gespeichert werden und so in der AD&nbsp;LDS-Instanz auf dem Edge-Transport-Server in die Sammlung der Listen sicherer Absender aggregiert werden können, wird die Inhaltsfilterungsfunktion nicht für Daten sicherer Empfänger ausgeführt.



  - **Antispameinstellungen pro Empfänger**   Mithilfe des Cmdlets **Set-Mailbox** können Sie die Antispameinstellungen auf Empfängerbasis zuweisen, die von den organisationsweiten Antispameinstellungen abweichen. Wenn Sie Antispameinstellungen pro Empfänger konfigurieren, überschreiben diese Einstellungen die organisationsweiten Einstellungen. Durch Replizieren dieser Einstellungen nach AD LDS können die Einstellungen pro Empfänger berücksichtigt werden, bevor die Nachricht per Relay an die Exchange-Organisation weitergeleitet wird. Diese Informationen werden als gehashte Daten gesendet.

Zurück zum Seitenanfang

## Topologieinformationen

Die Topologieinformationen umfassen die Benachrichtigung der neu abonnierten Edge-Transport-Server oder der entfernten Edge-Abonnements. Diese Daten werden alle fünf Minuten aktualisiert.

Zurück zum Seitenanfang

