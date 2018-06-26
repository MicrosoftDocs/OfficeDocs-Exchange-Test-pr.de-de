---
title: 'Antivirensoftware im Betriebssystem auf Exchange-Servern: Exchange 2013 Help'
TOCTitle: Antivirensoftware im Betriebssystem auf Exchange-Servern
ms:assetid: 7cef6017-7a55-41f3-a636-1ca4fce575b1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb332342(v=EXCHG.150)
ms:contentKeyID: 50476041
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Antivirensoftware im Betriebssystem auf Exchange-Servern

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-07-22_

In diesem Thema werden die Auswirkungen von Antivirenprogrammen auf Dateiebene auf Computern beschrieben, auf denen Microsoft Exchange Server 2013 ausgeführt wird. Wenn Sie die in diesem Thema beschriebenen Empfehlungen implementieren, können Sie die Sicherheit und den Status Ihrer Exchange-Organisation optimieren.

Scanner auf Dateiebene werden häufig verwendet. Wenn sie jedoch nicht ordnungsgemäß konfiguriert sind, können sie Probleme in Exchange 2013 verursachen. Zwei Typen von Scannern auf Dateiebene werden unterschieden:

  - *Speicherresidente Scans auf Dateiebene* beziehen sich auf Antivirensoftware auf Dateiebene, die immer im Arbeitsspeicher geladen ist. Sie überprüft alle Dateien, die auf der Festplatte und im Arbeitsspeicher verwendet werden.

  - *Scans auf Dateiebene bei Bedarf* bezieht sich auf Antivirussoftware auf Dateiebene, die Sie so konfigurieren können, dass Dateien auf der Festplatte manuell oder nach einem festgelegten Zeitplan gescannt werden. Einige Versionen von Antivirussoftware starten den Scan bei Bedarf automatisch, nachdem die Virensignaturen aktualisiert wurden, damit sichergestellt ist, dass alle Dateien mit den aktuellsten Signaturen gescannt wurden.

Die folgenden Probleme können auftreten, wenn Sie Antivirenprogramme auf Dateiebene zusammen mit Exchange 2013 verwenden:

  - Scanner auf Dateiebene können eine Datei scannen, wenn sie verwendet wird, oder sie können in einem geplanten Intervall aufgerufen werden. Dieser Vorgang kann bewirken, dass die Scanner ein Exchange-Protokoll oder eine Datenbankdatei sperren oder isolieren, während Exchange 2013 versucht, die Datei zu verwenden. Dieses Verhalten kann einen schwerwiegenden Fehler in Exchange 2013 sowie -1018-Ereignisprotokollfehler verursachen.

  - Scanner auf Dateiebene bieten keinen Schutz vor E-Mail-Viren wie etwa dem Storm-Wurm. Der Storm-Wurm ist ein Beispiel für ein Trojanisches Pferd (Backdoor-Virus), das sich selbst über E-Mail-Nachrichten verbreitet hat. Der Wurm hat den infizierten Computer an ein Botnet angeschlossen, wobei der Computer in regelmäßigen Abständen zum massenhaften Senden von Spam-E-Mails verwendet wurde.

## Empfehlungen für die Verwendung von Scans auf Dateiebene mit Exchange 2013

Wenn Sie Antivirenprogramme auf Dateiebene auf Exchange 2013-Servern bereitstellen, vergewissern Sie sich, dass die entsprechenden Ausschlüsse, z. B. Ausschlüsse für Verzeichnisse, Prozesse und Dateinamenerweiterungen, sowohl für die speicherresidente als auch für die Prüfung auf Dateiebene eingerichtet wurden. In diesem Abschnitt werden empfohlene Ausschlüsse für Verzeichnisse, Prozesse und Dateinamenerweiterungen beschrieben.

**Inhalt**

Verzeichnisausschlüsse

Prozessausschlüsse

Ausschlüsse für Dateinamenerweiterungen

## Verzeichnisausschlüsse

Sie müssen bestimmte Verzeichnisse für jeden Exchange-Server bzw. ausschließen, für den Sie einen Antivirenscanner auf Dateiebene ausführen. In diesem Abschnitt werden die Verzeichnisse beschrieben, die Sie von Scans auf Dateiebene ausschließen sollten.

  - **Postfachserver**
    
      - **Postfachdatenbanken**
        
          - Exchange-Datenbanken, Prüfpunktdateien und Protokolldateien. Diese Dateien werden standardmäßig in Unterordnern des Ordners "%ExchangeInstallPath%Mailbox" gespeichert. Möchten Sie den Speicherort einer Postfachdatenbank, eines Transaktionsprotokolls und einer Prüfpunktdatei bestimmen, führen Sie den folgenden Befehl aus: `Get-MailboxDatabase -Server <servername>| Format-List *path*`
        
          - Datenbankinhaltsindizes. In der Standardeinstellung befinden sich diese im gleichen Ordner wie die Datenbankdatei.
        
          - GroupMetrics-Dateien. Standardmäßig befinden sich diese Dateien im Ordner "%ExchangeInstallPath%GroupMetrics".
        
          - Allgemeine Protokolldateien, z. B. Protokolldateien für die Nachrichtenverfolgung und Kalenderreparatur. Standardmäßig befinden sich diese Dateien in Unterordnern der Ordner "%ExchangeInstallPath%TransportRoles\\Logs" und "%ExchangeInstallPath%Logging". Führen Sie folgenden Befehl in der Exchange-Verwaltungsshell aus, um die verwendeten Protokollpfade zu bestimmen: `Get-MailboxServer <servername> | Format-List *path*`
        
          - Offlineadressbuch-Dateien. Standardmäßig befinden sich diese Dateien in Unterordnern des Ordners "%ExchangeInstallPath%ClientAccess\\OAB".
        
          - IIS-Systemdateien im Ordner "%SystemRoot%\\System32\\Inetsrv".
        
          - Der temporäre Ordner der Postfachdatenbank: %ExchangeInstallPath%Mailbox\\MDBTEMP
    
      - **Mitglieder von Database Availability Groups**
        
          - Alle Elemente der Liste **Postfachdatenbanken** und die Clusterquorumdatenbank unter "%Windir%\\Cluster".
        
          - Die Zeugenverzeichnisdateien. Diese Dateien sind auf einem anderen Server in der Umgebung gespeichert, typischerweise auf einem Clientzugriffsserver, der nicht auf dem gleichen Computer installiert ist wie ein Postfachserver. Die Dateien des Zeugenverzeichnisses befinden sich standardmäßig in "%SystemDrive%:\\DAGFileShareWitnesses\\\<DAGFQDN\>".
    
      - **Transportdienst**
        
          - Protokolldateien, z. B. für Nachrichtenverfolgung und Verbindungsprotokolle. Standardmäßig befinden sich diese Dateien in Unterordnern des Ordners "%ExchangeInstallPath%TransportRoles\\Logs". Führen Sie folgenden Befehl in der Exchange-Verwaltungsshell aus, um die verwendeten Protokollpfade zu bestimmen: `Get-TransportService <servername> | Format-List *logpath*,*tracingpath*`
        
          - Nachrichtenverzeichnisordner PICKUP und REPLAY. Standardmäßig befinden sich diese Ordner im Ordner "%ExchangeInstallPath%TransportRoles". Führen Sie folgenden Befehl in der Exchange-Verwaltungsshell aus, um die verwendeten Pfade zu bestimmen: `Get-TransportService <servername>| Format-List *dir*path*`
        
          - Die Warteschlangendatenbanken, Prüfpunkte und Protokolldateien. Standardmäßig befinden sich diese im Ordner "%ExchangeInstallPath%TransportRoles\\Data\\Queue".
        
          - Die Absenderzuverlässigkeitsdatenbank, Prüfpunkte und Protokolldateien. Standardmäßig befinden sich diese im Ordner "%ExchangeInstallPath%TransportRoles\\Data\\SenderReputation".
        
          - Die temporären Ordner, die zum Durchführen von Konvertierungen verwendet werden:
            
              - Standardmäßig werden Inhaltskonvertierungen im "%TMP%"-Ordner des Exchange-Servers ausgeführt.
            
              - Standardmäßig werden Umwandlungen vom RTF-Format in das MIME/HTML-Format im Ordner "%ExchangeInstallPath%Working\\OleConverter" durchgeführt.
        
          - Die Komponenten zum Scannen von Inhalten wird vom Schadsoftware-Agent und den Funktionen zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) genutzt. Standardmäßig befinden sich diese Dateien im Ordner "%ExchangeInstallPath%FIP-FS".
    
      - **Postfachtransportdienst**
        
          - Protokolldateien, z. B. Verbindungsprotokolle. Standardmäßig befinden sich diese Dateien in Unterordnern des Ordners "%ExchangeInstallPath%TransportRoles\\Logs\\Mailbox". Führen Sie folgenden Befehl in der Exchange-Verwaltungsshell aus, um die verwendeten Protokollpfade zu bestimmen: `Get-MailboxTransportService <servername> | Format-List *logpath*`
    
      - **Unified Messaging**
        
          - Die Grammatikdateien für unterschiedliche Gebietsschemas, z. B. "de-DE" oder "es-ES". Standardmäßig werden diese in den Unterordnern des Ordners "%ExchangeInstallPath%UnifiedMessaging\\grammars" gespeichert.
        
          - Die Dateien für Ansagen, Begrüßungen und Informationsmeldungen. Standardmäßig werden diese in den Unterordnern des Ordners "%ExchangeInstallPath%UnifiedMessaging\\Prompts" gespeichert
        
          - Die Voicemaildateien, die vorübergehend im Ordner "%ExchangeInstallPath%UnifiedMessaging\\voicemail" gespeichert sind.
        
          - Die durch Unified Messaging generierten temporären Dateien. Standardmäßig werden diese im Ordner "%ExchangeInstallPath%UnifiedMessaging\\temp" gespeichert.
    
      - **Setup**
        
          - Temporäre Dateien für Exchange Server-Setup. Diese Dateien befinden sich normalerweise unter %SystemRoot%\\Temp\\ExchangeSetup.
    
      - **Exchange-Suchdienst**
        
          - Temporäre Dateien, die vom Exchange-Suchdienst und Microsoft Filter Pack verwendet werden, um die Konvertierung in einer Sandkastenumgebung durchzuführen. Diese Dateien befinden sich unter %SystemRoot%\\Temp\\OICE\_*\<GUID\>*\\.

<!-- end list -->

  - **Clientzugriffsserver**
    
      - **Webkomponenten**
        
          - Für IIS 7.0 (Internet Information Services, Internetinformationsdienste) verwendende Server der Komprimierungsordner, der mit Microsoft Outlook Web App verwendet wird. Der Komprimierungsordner für IIS 7.0 befindet sich standardmäßig unter "%SystemDrive%\\inetpub\\temp\\IIS Temporary Compressed Files".
        
          - IIS-Systemdateien im Ordner "%SystemRoot%\\System32\\Inetsrv"
        
          - Inetpub\\logs\\logfiles\\w3svc
        
          - Unterordner unter „%SystemRoot%\\Microsoft.NET\\Framework64\\v4.0.30319\\Temporary ASP.NET Files“
    
      - **POP3- und IMAP4-Protokollierung**
        
          - POP3-Ordner: %ExchangeInstallPath%Logging\\POP3
        
          - IMAP4-Ordner: %ExchangeInstallPath%Logging\\IMAP4
    
      - **Front-End-Transport-Dienst**
        
          - Protokolldateien, z. B. Verbindungsprotokolle und Protokolle. Standardmäßig befinden sich diese Dateien in Unterordnern des Ordners "%ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd". Führen Sie folgenden Befehl in der Exchange-Verwaltungsshell aus, um die verwendeten Protokollpfade zu bestimmen: `Get-FrontEndTransportService <servername> | Format-List *logpath*`
    
      - **Setup**
        
          - Temporäre Dateien für Exchange Server-Setup. Diese Dateien befinden sich normalerweise unter % SystemRoot%\\Temp\\ExchangeSetup.

Empfehlungen für die Verwendung von Scans auf Dateiebene mit Exchange 2013

## Prozessausschlüsse

Zahlreiche Antivirenprogramme auf Dateiebene unterstützen die Prüfung von Prozessen, die sich negativ auf Microsoft Exchange auswirken können, wenn die falschen Prozesse überprüft werden. Aus diesem Grund sollten Sie die folgenden Prozesse aus Scanvorgängen auf Dateiebene ausschließen.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Prozess</th>
<th>Pfad</th>
<th>Kommentare</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dsamain.exe</p></td>
<td><p>%SystemRoot%\System32</p></td>
<td><p>Active Directory Lightweight Directory Services (AD LDS) auf abonnierten Edge-Transport-Servern.</p></td>
<td><p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>EdgeTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Arbeitsprozess des Microsoft Exchange-Transportdiensts</p></td>
<td><p>Postfachserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>fms.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Komponente zum Scannen von Inhalten, die vom Schadsoftware-Agenten und von DLP verwendet wird.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>hostcontrollerservice.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\HostController</p></td>
<td><p>Microsoft Exchange-Suchhost-Controllerdienst (HostControllerService)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p></td>
</tr>
<tr class="odd">
<td><p>inetinfo.exe</p></td>
<td><p>%SystemRoot%\System32\inetsrv</p></td>
<td><p>Internetinformationsdienste (IIS)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.AntispamUpdateSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Antispamupdatesdienst (MSExchangeAntispamUpdate)</p></td>
<td><p>Postfachserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.ContentFilter.Wrapper.exe</p></td>
<td><p>%ExchangeInstallPath%TransportRoles\agents\Hygiene</p></td>
<td><p>Inhaltsfilter-Agent</p></td>
<td><p>Postfachserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Diagnostics.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Diagnosedienst (MSExchangeDiagnostics)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Directory.TopologyService.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange Active Directory-Topologiedienst (MSExchangeADTopology)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.EdgeCredentialSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Anmeldeinformationsdienst (MSExchangeEdgeCredential)</p></td>
<td><p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.EdgeSyncSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-EdgeSync-Dienst (MSExchangeEdgeSync)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Imap4.exe</p></td>
<td><p>ExchangeInstallPath%FrontEnd\PopImap</p></td>
<td><p>Microsoft Exchange IMAP4-Dienst (MSExchangeImap4)</p></td>
<td><p>Clientzugriffsserver</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Imap4service.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\PopImap</p></td>
<td><p>Microsoft Exchange IMAP4-Back-End-Dienst (MSExchangeIMAP4BE)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Pop3.exe</p></td>
<td><p>%ExchangeInstallPath%FrontEnd\PopImap</p></td>
<td><p>Microsoft Exchange POP3-Dienst (MSExchangePop3)</p></td>
<td><p>Clientzugriffsserver</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Pop3service.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\PopImap</p></td>
<td><p>Microsoft Exchange POP3-Back-End-Dienst (MSExchangePOP3BE)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.ProtectedServiceHost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Dienst für den Diensthost (MSExchangeServiceHost)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.RPCClientAccess.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-RPC-Clientzugriffsdienst (MSExchangeRPC)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Search.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Suchdienst (MSExchangeFastSearch)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Servicehost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Dienst für den Diensthost (MSExchangeServiceHost)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Store.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Informationsspeicher (MSExchangeIS)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Store.Worker.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Arbeitsprozess des Microsoft Exchange-Informationsspeicherdiensts</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.UM.CallRouter.exe</p></td>
<td><p>%ExchangeInstallPath%FrontEnd\CallRouter</p></td>
<td><p>Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung (MSExchangeUMCR)</p></td>
<td><p>Clientzugriffsserver</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeDagMgmt.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange DAG-Verwaltungsdienst (MSExchangeDagMgmt)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeDelivery.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Postfachtransport-Zustellungsdienst (MSExchangeDelivery)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeFrontendTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Frontend-Transportdienst (MSExchangeFrontEndTransport)</p></td>
<td><p>Clientzugriffsserver</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeHMHost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Integritätsdienst (MSExchangeHM)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeHMWorker.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Arbeitsprozess des Microsoft Exchange-Integritätsdiensts</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeMailboxAssistants.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Postfach-Assistentendienst (MSExchangeMailboxAssistants)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeMailboxReplication.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Postfachreplikationsdienst (MSExchangeMailboxReplication)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeMigrationWorkflow.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Migrationsworkflowdienst (MSExchangeMigrationWorkflow)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeRepl.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Replikationsdienst (MSExchangeRepl)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeSubmission.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Postfachtransport-Übermittlungsdienst (MSExchangeDelivery)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Transportdienst (MSExchangeTransport)</p></td>
<td><p>Postfachserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeTransportLogSearch.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Transportprotokoll-Suchdienst (MSExchangeTransportLogSearch)</p></td>
<td><p>Postfachserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeThrottling.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange-Einschränkungsdienst (MSExchangeThrottling)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>Noderunner.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\Runtime\1.0</p></td>
<td><p>Microsoft Exchange-Suchdienst (MSExchangeFastSearch)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>OleConverter.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Wandelt Nachrichten im RTF-Format für externe Empfänger in das MIME/HTML-Format um.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>ParserServer.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\ParserServer</p></td>
<td><p>Microsoft Exchange-Suchdienst (MSExchangeFastSearch)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>Powershell.exe</p></td>
<td><p>C:\Windows\System32\WindowsPowerShell\v1.0</p></td>
<td><p>Exchange-Verwaltungsshell</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p>
<p>Edge-Transport-Server</p></td>
</tr>
<tr class="even">
<td><p>ScanEngineTest.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Komponente zum Scannen von Inhalten, die vom Schadsoftware-Agenten und von DLP verwendet wird.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>ScanningProcess.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Komponente zum Scannen von Inhalten, die vom Schadsoftware-Agenten und von DLP verwendet wird.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>TranscodingService.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\Owa\Bin\DocumentViewing</p></td>
<td><p>WebReady Document Viewing in Outlook Web App.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>UmService.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Microsoft Exchange Unified Messaging-Dienst (MSExchangeUM)</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>UmWorkerProcess.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Arbeitsprozess des Microsoft Exchange Unified Messaging-Diensts</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="odd">
<td><p>UpdateService.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Komponente zum Scannen von Inhalten, die vom Schadsoftware-Agenten und von DLP verwendet wird.</p></td>
<td><p>Postfachserver</p></td>
</tr>
<tr class="even">
<td><p>W3wp.exe</p></td>
<td><p>%SystemRoot%\System32\inetsrv</p></td>
<td><p>Internetinformationsdienste (IIS)</p></td>
<td><p>Postfachserver</p>
<p>Clientzugriffsserver</p></td>
</tr>
</tbody>
</table>


Empfehlungen für die Verwendung von Scans auf Dateiebene mit Exchange 2013

## Ausschlüsse für Dateinamenerweiterungen

Sie sollten neben bestimmten Verzeichnissen und Prozessen auch die folgenden Exchange-spezifischen Dateinamenerweiterungen für den Fall ausschließen, dass ein Fehler bei den Verzeichnisausschlüssen auftritt oder Dateien aus ihren Standardspeicherorten verschoben werden.

  - Anwendungsbezogene Erweiterungen:
    
      - .config
    
      - .dia
    
      - .wsb

<!-- end list -->

  - Datenbankbezogene Erweiterungen:
    
      - .chk
    
      - .edb
    
      - .jrs
    
      - .jsl
    
      - .log
    
      - .que

<!-- end list -->

  - Erweiterungen, die sich auf das Offlineadressbuch beziehen:
    
      - .lzx

<!-- end list -->

  - Inhaltsindexbezogene Erweiterungen:
    
      - .ci
    
      - .dir
    
      - .wid
    
      - .000
    
      - .001
    
      - .002

<!-- end list -->

  - Unified Messaging-bezogene Erweiterungen:
    
      - .cfg
    
      - .grxml

<!-- end list -->

  - Gruppenmetrikbezogene Erweiterungen:
    
      - .dsc
    
      - .txt

Empfehlungen für die Verwendung von Scans auf Dateiebene mit Exchange 2013

