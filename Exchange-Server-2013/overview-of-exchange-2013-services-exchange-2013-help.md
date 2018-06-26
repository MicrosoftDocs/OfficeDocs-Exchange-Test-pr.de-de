---
title: 'Überblick über Exchange 2013-Dienste: Exchange 2013 Help'
TOCTitle: Überblick über Exchange 2013-Dienste
ms:assetid: 2ed45d18-2ff3-4099-b841-050eb16a416b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423542(v=EXCHG.150)
ms:contentKeyID: 74479258
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Überblick über Exchange 2013-Dienste

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-10-20_

Während der Installation von Exchange Server 2013 führt Setup eine Reihe von Tasks aus, von denen neue Dienste Microsoft Windows installiert werden. Ein Dienst ist ein Hintergrundprozess, der vom Dienststeuerungs-Manager in Windows während des Starts des Servers gestartet werden kann. Dienste sind ausführbare Dateien, die unabhängig und ohne administratives Eingreifen arbeiten. Ein Dienst kann im GUI- oder im Konsolenmodus ausgeführt werden.

Alle vorherigen Versionen von Exchange beinhalten Komponenten, die als Dienste implementiert sind. Jede Exchange-Serverrolle beinhaltet Dienste, die Bestandteil der Serverrolle sind oder von dieser benötigt werden, um ihre Funktionen auszuführen. Beachten Sie, dass einige Dienste erst aktiv werden, wenn bestimmte Funktionen verwendet werden.

In den Abschnitten in diesem Thema werden die unterschiedlichen Dienste beschrieben, die von Exchange 2013 auf Postfachservern, Clientzugriffsservern und Edge-Transport-Servern installiert werden. Bei Diensten, die als optional gekennzeichnet sind, können Sie den Dienst deaktivieren, wenn Sie feststellen, dass Ihre Organisation die von dem Dienst bereitgestellte Funktionalität nicht benötigt.

## Exchange-Dienste auf Exchange 2013-Postfachservern

In der folgenden Tabelle sind die Exchange-Dienste beschrieben, die auf Postfachservern installiert sind.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Dienstname</th>
<th>Dienstkurzname</th>
<th>Beschreibung und Abhängigkeiten</th>
<th>Standardstarttyp</th>
<th>Sicherheitskontext</th>
<th>Abhängigkeiten</th>
<th>Erforderlich oder optional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>MSExchangeADTopology</p></td>
<td><p>Stellt Exchange-Diensten Active Directory-Topologieinformationen bereit. Wenn dieser Dienst beendet wird, können die meisten Exchange-Dienste nicht starten.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Net. TCP-Portfreigabedienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Antispamupdate</p></td>
<td><p>MSExchangeAntispamUpdate</p></td>
<td><p>Stellt Exchange SmartScreen-Spamdefinitionsaktualisierungen bereit.</p>

> [!NOTE]
> Am 1. November 2016 hat Microsoft die Generierung von Spamdefinitionsupdates für die SmartScreen-Filter in Exchange und Outlook eingestellt. Die vorhandenen SmartScreen-Spamdefinitionen bleiben bestehen, ihre Effektivität wird aber im Laufe der Zeit wahrscheinlich abnehmen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=835894">Deprecating support for SmartScreen in Outlook and Exchange</A>.


</td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-DAG-Verwaltung</p></td>
<td><p>MSExchangeDagMgmt</p></td>
<td><p>Stellt eine Speicher- und Datenbanklayoutverwaltung für Postfachserver in Database Availability Groups (DAGs) bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p>
<p>Net. TCP-Portfreigabedienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Diagnose</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Stellt einen Agent bereit, der die Exchange-Serverintegrität überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Keine</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange EdgeSync</p></td>
<td><p>MSExchangeEdgeSync</p></td>
<td><p>Repliziert Konfigurations- und Empfängerdaten zwischen dem Postfachserver und UNRESOLVED_TOKEN_VAL(exADLDS_1st) (AD LDS) auf abonnierten Edge-Transport-Servern über einen sicheren LDAP-Kanal.</p>
<p>Wenn Sie nicht abonnierte Edge-Transport-Server verfügen, können Sie diesen Dienst deaktivieren.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Integritäts-Manager</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Teil der verwalteten Verfügbarkeit, der die Integrität von Schlüsselkomponenten auf dem Exchange-Server überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Windows-Ereignisprotokoll</p>
<p>Windows Windows-Verwaltungsinstrumentation</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange IMAP4-Back-End</p></td>
<td><p>MSExchangeIMAP4BE</p></td>
<td><p>Empfängt Clientverbindungen über Proxy vom IMAP4-Dienst auf Clientzugriffsservern. Standardmäßig wird dieser Dienst nicht ausgeführt, IMAP4-Clients können daher erst eine Verbindung zum Exchange-Server herstellen, nachdem der Dienst gestartet wurde.</p>
<p>Wenn Sie nicht über IMAP4-Clients verfügen, können Sie diesen Dienst deaktivieren.</p></td>
<td><p>Manuell</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Informationsspeicher</p></td>
<td><p>MSExchangeIS</p></td>
<td><p>Verwaltet die Postfachdatenbanken auf dem Server. Wenn dieser Dienst beendet wird, sind die Postfachdatenbanken auf dem Server nicht verfügbar.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p>
<p>Remoteprozeduraufruf (Remote Procedure Call, RPC)</p>
<p>Server</p>
<p>Windows-Ereignisprotokoll</p>
<p>Arbeitsstation</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Postfach-Assistenten</p></td>
<td><p>MSExchangeMailboxAssistants</p></td>
<td><p>Führt die Hintergrundverarbeitung von Postfächern in Postfachservern auf dem Server aus.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Postfachreplikation</p></td>
<td><p>MSExchangeMailboxReplication</p></td>
<td><p>Verarbeitet Postfachverschiebungen und Verschiebungsanforderungen.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p>
<p>Net. TCP-Portfreigabedienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Postfachtransportbereitstellung</p></td>
<td><p>MSExchangeDelivery</p></td>
<td><p>Empfängt SMTP-Nachrichten vom Microsoft Exchange-Transport-Dienst (auf den lokalen oder Remotepostfachservern) und übermittelt diese mithilfe von RPC an eine lokale Postfachdatenbank.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft ExchangePostfachtransport-Übermittlung</p></td>
<td><p>MSExchangeSubmission</p></td>
<td><p>Empfängt RPC-Nachrichten von einer lokalen Postfachdatenbank und übermittelt diese über SMTP an den Microsoft Exchange Transport-Dienst (auf den lokalen oder Remotepostfachservern).</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange POP3-Back-End</p></td>
<td><p>MSExchangePOP3BE</p></td>
<td><p>Empfängt Clientverbindungen über Proxy vom POP3-Dienst auf Clientzugriffsservern. Standardmäßig wird dieser Dienst nicht ausgeführt, POP3-Clients können daher erst eine Verbindung zum Exchange-Server herstellen, nachdem der Dienst gestartet wurde.</p></td>
<td><p>Manuell</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Replikationsdienst</p></td>
<td><p>MSExchangeRepl</p></td>
<td><p>Stellt Replikationsfunktionen für Postfachdatenbanken in einer Database Availability Group (DAG) bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-RPC-Clientzugriff</p></td>
<td><p>MSExchangeRPC</p></td>
<td><p>Verwaltet Client-RPC-Verbindungen für Exchange.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Suche</p></td>
<td><p>MSExchangeFastSearch</p></td>
<td><p>Stellt die Indizierung von Postfachinhalten bereit, wodurch die Leistung der Inhaltssuche verbessert wird.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Suchhostcontroller</p></td>
<td><p>HostControllerService</p></td>
<td><p>Stellt Bereitstellungs- und Verwaltungsdienste für Anwendungen auf dem lokalen Exchange-Server bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>HTTP-Dienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange Server-Erweiterung für Windows Server-Sicherung</p></td>
<td><p>WSBExchange</p></td>
<td><p>Aktiviert die Windows Server-Sicherung zum Sichern und Wiederherstellen von Exchange-Serverdaten.</p></td>
<td><p>Manuell</p></td>
<td><p>Lokales System</p></td>
<td><p>Keine</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Diensthost</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Stellt einen Diensthost für Exchange-Komponenten bereit, die nicht über eigene Dienste verfügen.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Einschränkung</p></td>
<td><p>MSExchangeThrottling</p></td>
<td><p>Ermöglicht die Verwaltung der Benutzerarbeitslast, durch die die Rate von Benutzeraktionen (bisher als Benutzereinschränkung bezeichnet) eingeschränkt wird.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Transport</p></td>
<td><p>MSExchangeTransport</p></td>
<td><p>Stellt den SMTP-Serverstapel und -Transportstapel bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p>
<p>Microsoft-Filterverwaltungsdienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Transportprotokollsuche</p></td>
<td><p>MSExchangeTransportLogSearch</p></td>
<td><p>Stellt Remotesuchfunktionen für Transportprotokolldateien zur Verfügung (z. B. Nachrichtenverfolgung).</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange Unified Messaging</p></td>
<td><p>MSExchangeUM</p></td>
<td><p>Stellt Unified Messaging (UM)-Funktionen bereit: Ermöglicht, dass Sprach- und Faxnachrichten in Exchange gespeichert werden und bietet Benutzern Zugriff auf E-Mail, Voicemail, Kalender, Kontakte oder eine automatische Telefonzentrale. Wenn dieser Dienst beendet wird, ist Unified Messaging nicht verfügbar.</p>
<p>Wenn Sie UM nicht verwenden, können Sie diesen Dienst deaktivieren.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>CNG-Schlüsselisolation</p>
<p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
</tbody>
</table>


## Exchange-Dienste auf Exchange 2013-Clientzugriffsservern

In der folgenden Tabelle sind die Exchange-Dienste beschrieben, die auf Clientzugriffsservern installiert sind.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Dienstname</th>
<th>Dienstkurzname</th>
<th>Beschreibung und Abhängigkeiten</th>
<th>Standardstarttyp</th>
<th>Sicherheitskontext</th>
<th>Abhängigkeiten</th>
<th>Erforderlich oder optional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>MSExchangeADTopology</p></td>
<td><p>Stellt Exchange-Diensten Active Directory-Topologieinformationen bereit. Wenn dieser Dienst beendet wird, können die meisten Exchange-Dienste nicht starten.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Net. TCP-Portfreigabedienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Diagnose</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Stellt einen Agent bereit, der die Exchange-Serverintegrität überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Keine</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange Front-End-Transport</p></td>
<td><p>MSExchangeFrontEndTransport</p></td>
<td><p>SMTP-Verbindungen erfolgen über Proxy von externen Hosts an den Microsoft Exchange-Transport-Dienst auf Postfachservern.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Integritäts-Manager</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Teil der verwalteten Verfügbarkeit, der die Integrität von Schlüsselkomponenten auf dem Exchange-Server überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Windows-Ereignisprotokoll</p>
<p>Windows Windows-Verwaltungsinstrumentation</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange IMAP4</p></td>
<td><p>MSExchangeIMAP4</p></td>
<td><p>IMAP4-Clientverbindungen erfolgen über Proxy zu dem IMAP4-Dienst auf Postfachservern. Standardmäßig wird dieser Dienst nicht ausgeführt, IMAP4-Clients können daher erst eine Verbindung zum Exchange-Server herstellen, nachdem der Dienst gestartet wurde.</p>
<p>Wenn Sie nicht über IMAP4-Clients verfügen, können Sie diesen Dienst deaktivieren.</p></td>
<td><p>Manuell</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange POP3</p></td>
<td><p>MSExchangePOP3</p></td>
<td><p>POP3-Clientverbindungen erfolgen über Proxy zu dem IMAP4-Dienst auf Postfachservern. Standardmäßig wird dieser Dienst nicht ausgeführt, POP3-Clients können daher erst eine Verbindung zum Exchange-Server herstellen, nachdem der Dienst gestartet wurde.</p></td>
<td><p>Manuell</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Suchhostcontroller</p></td>
<td><p>HostControllerService</p></td>
<td><p>Stellt Bereitstellungs- und Verwaltungsdienste für Anwendungen auf dem lokalen Exchange-Server bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>HTTP-Dienst</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Diensthost</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Stellt einen Diensthost für Exchange-Komponenten bereit, die nicht über eigene Dienste verfügen.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange Unified Messaging-Anrufweiterleitung</p></td>
<td><p>MSExchangeUMCR</p></td>
<td><p>Leitet UM-Clientverbindungen zum Unified Messaging-Dienst auf Postfachservern um.</p>
<p>Wenn Sie UM nicht verwenden, können Sie diesen Dienst deaktivieren.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>CNG-Schlüsselisolation</p>
<p>Microsoft ExchangeActive Directory-Topologie</p></td>
<td><p>Optional</p></td>
</tr>
</tbody>
</table>


## Exchange-Dienste auf Exchange 2013-Edge-Transport-Servern

In der folgenden Tabelle sind die Exchange-Dienste beschrieben, die auf Edge-Transport-Servern installiert sind.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Dienstname</th>
<th>Dienstkurzname</th>
<th>Beschreibung</th>
<th>Standardstarttyp</th>
<th>Sicherheitskontext</th>
<th>Abhängigkeiten</th>
<th>Erforderlich oder optional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>ADAM_MSExchange</p></td>
<td><p>Speichert Konfigurationsdaten und Empfängerdaten auf dem Edge-Transport-Server. Dieser Dienst stellt die benannte Instanz von UNRESOLVED_TOKEN_VAL(exADLDS_1st) (AD LS) dar, die vom Exchange- Setup automatisch erstellt wird.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>COM + Event-System</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Antispamupdate</p></td>
<td><p>MSExchangeAntispamUpdate</p></td>
<td><p>Stellt Exchange SmartScreen-Spamdefinitionsaktualisierungen bereit.</p>

> [!NOTE]
> Am 1. November 2016 hat Microsoft die Generierung von Spamdefinitionsupdates für die SmartScreen-Filter in Exchange und Outlook eingestellt. Die vorhandenen SmartScreen-Spamdefinitionen bleiben bestehen, ihre Effektivität wird aber im Laufe der Zeit wahrscheinlich abnehmen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=835894">Deprecating support for SmartScreen in Outlook and Exchange</A>.


</td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Anmeldeinformationsdienst</p></td>
<td><p>MSExchangeEdgeCredential</p></td>
<td><p>Überwacht Änderungen an Anmeldeinformationen in UNRESOLVED_TOKEN_VAL(exADLDS_1st) (AD LDS) und installiert die Änderungen auf dem Edge-Transport-Server.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Diagnose</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Stellt einen Agent bereit, der die Exchange-Serverintegrität überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Keine</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Integritäts-Manager</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Teil der verwalteten Verfügbarkeit, der die Integrität von Schlüsselkomponenten auf dem Exchange-Server überwacht.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Windows-Ereignisprotokoll</p>
<p>Windows-Verwaltungsinstrumentation</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Diensthost</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Stellt einen Diensthost für Exchange-Komponenten bereit, die nicht über eigene Dienste verfügen.</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Transport</p></td>
<td><p>MSExchangeTransport</p></td>
<td><p>Stellt den SMTP-Serverstapel und -Transportstapel bereit.</p></td>
<td><p>Automatisch</p></td>
<td><p>Netzwerkdienst</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Erforderlich</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange-Transportprotokollsuche</p></td>
<td><p>MSExchangeTransportLogSearch</p></td>
<td><p>Stellt Remotesuchfunktionen für Transportprotokolldateien zur Verfügung (z. B. Nachrichtenverfolgung).</p></td>
<td><p>Automatisch</p></td>
<td><p>Lokales System</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Optional</p></td>
</tr>
</tbody>
</table>

