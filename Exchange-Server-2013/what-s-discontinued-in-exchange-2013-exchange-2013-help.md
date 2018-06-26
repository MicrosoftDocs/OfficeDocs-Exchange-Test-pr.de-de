---
title: 'In Exchange 2013 nicht mehr unterstützte Funktionen: Exchange 2013 Help'
TOCTitle: In Exchange 2013 nicht mehr unterstützte Funktionen
ms:assetid: 0ac0001c-b314-4108-b895-d9c0e271b489
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ619283(v=EXCHG.150)
ms:contentKeyID: 50474997
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# In Exchange 2013 nicht mehr unterstützte Funktionen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In diesem Thema werden die Komponenten, Features oder Funktionen erläutert, die in Microsoft Exchange Server 2013 entfernt, eingestellt oder ersetzt wurden.


> [!NOTE]
> Die folgenden Themen könnten Sie ebenfalls interessieren: 
> <UL>
> <LI>
> <P><A href="what-s-new-in-exchange-2013-exchange-2013-help.md">Neuerungen in Exchange&nbsp;2013</A>&nbsp;&nbsp;&nbsp;Informationen zu neuen Funktionen in Exchange Server&nbsp;2013.</P>
> <LI>
> <P><A href="https://go.microsoft.com/fwlink/p/?linkid=267479">Entwickler-Roadmap für Exchange 2013</A>&nbsp;&nbsp;&nbsp;&nbsp;Im Abschnitt zu den aus Exchange entfernten Entwicklungstechnologien finden Sie Informationen zu den APIs und Entwicklungsfunktionen, die in Exchange 2013 nicht länger verfügbar sind.</P></LI></UL>



## Exchange 2010-Funktionen, die in Exchange 2013 nicht mehr unterstützt werden

In diesem Abschnitt sind die Exchange Server 2010-Funktionen aufgeführt, die in Exchange 2013 nicht länger verfügbar sind.

## Architektur


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hub-Transport-Serverrolle</p></td>
<td><p>Die Hub-Transport-Serverrolle wurde durch Transportdienste ersetzt, die auf den Serverrollen &quot;Postfach&quot; und &quot;Clientzugriff&quot; ausgeführt werden. Die Serverrolle &quot;Postfach&quot; beinhaltet die Dienste Microsoft Exchange Transport, Microsoft Exchange Mailbox Transport Delivery und Microsoft Exchange Mailbox Transport Submission. Die Serverrolle &quot;Clientzugriff&quot; beinhaltet den Microsoft Exchange Frontend Transport-Dienst. Weitere Informationen finden Sie unter <a href="mail-flow-exchange-2013-help.md">Nachrichtenübermittlung</a>.</p></td>
</tr>
<tr class="even">
<td><p>Unified Messaging-Serverrolle</p></td>
<td><p>Die Serverrolle &quot;Unified Messaging&quot; wurde durch Unified Messaging-Dienste ersetzt, die auf den Serverrollen &quot;Postfach&quot; und &quot;Clientzugriff&quot; ausgeführt werden. Die Serverrolle &quot;Postfach&quot; beinhaltet den Microsoft Exchange Unified Messaging-Dienst, und die Serverrolle &quot;Clientzugriff&quot; beinhaltet den Exchange Unified Messaging Call Router-Dienst. Weitere Informationen finden Sie unter <a href="voice-architecture-changes-exchange-2013-help.md">Änderungen an der Spracharchitektur</a>.</p></td>
</tr>
</tbody>
</table>


## Verwaltungsschnittstellen


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Verwaltungskonsole und Exchange-Systemsteuerung</p></td>
<td><p>Die Exchange-Verwaltungskonsole und die Exchange-Systemsteuerung wurden durch das Exchange Admin Center (EAC) ersetzt. EAC verwendet das gleiche virtuelle Verzeichnis (/ecp) wie die Exchange-Systemsteuerung. Weitere Informationen finden Sie unter <a href="exchange-admin-center-in-exchange-2013-exchange-2013-help.md">Exchange Admin Center in Exchange 2013</a>.</p></td>
</tr>
</tbody>
</table>


## Clientzugriff


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2003 wird nicht unterstützt</p></td>
<td><p>Zum Herstellen einer Verbindung zwischen Microsoft Outlook und Exchange 2013 muss der AutoErmittlungsdienst verwendet werden. Microsoft Outlook 2003 unterstützt die Verwendung des AutoErmittlungsdiensts jedoch nicht.</p></td>
</tr>
<tr class="even">
<td><p>RPC/TCP-Zugriff für Outlook-Clients</p></td>
<td><p>In Exchange 2013 können Microsoft Outlook-Clients mithilfe von Outlook Anywhere (RPC/HTTP) oder MAPI über HTTP in Exchange 2013 Service Pack 1 und Outlook 2013 Service Pack 1 und höher eine Verbindung herstellen. Wenn Sie in Ihrer Organisation Outlook-Clients haben, müssen Sie Outlook Anywhere und/oder MAPI über HTTP verwenden. Weitere Informationen finden Sie unter <a href="outlook-anywhere-exchange-2013-help.md">Outlook Anywhere</a> und <a href="mapi-over-http-exchange-2013-help.md">MAPI über HTTP</a>.</p></td>
</tr>
</tbody>
</table>


## Outlook Web App und Outlook


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rechtschreibprüfung</p></td>
<td><p>In Outlook Web App sind keine Rechtschreibprüfungsdienste mehr enthalten. Stattdessen werden die Funktionen für Rechtschreibprüfung in Ihren Webbrowsern verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Anpassbare Filter</p></td>
<td><p>Outlook Web App verfügt über keine anpassbaren gefilterten Ansichten mehr und unterstützt das Speichern gefilterter Ansichten in den Favoriten nicht mehr. Anpassbare Filter wurden durch feste Filter ersetzt, die für die Anzeige aller Nachrichten, ungelesenen Nachrichten, an den Benutzer gesendeten Nachrichten oder markierten Nachrichten verwendet werden können.</p></td>
</tr>
<tr class="odd">
<td><p>Nachrichtenflags</p></td>
<td><p>In Outlook Web App kann bei einem Nachrichtenkennzeichen kein benutzerdefiniertes Datum festgelegt werden. Sie können Outlook zum Konfigurieren benutzerdefinierter Daten verwenden.</p></td>
</tr>
<tr class="even">
<td><p>Chatkontaktliste</p>
<p></p></td>
<td><p>Die Chatkontaktliste, die in der Ordnerliste in Outlook Web App für Exchange 2010 angezeigt wurde, ist nicht mehr verfügbar.</p></td>
</tr>
<tr class="odd">
<td><p>Suchordner</p></td>
<td><p>Benutzer können Suchordner derzeit nicht in Outlook Web App verwenden.</p></td>
</tr>
</tbody>
</table>


## Nachrichtenübermittlung


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verknüpfte Connectors</p></td>
<td><p>Sendeconnectors können nicht länger mit Empfangsconnectors verknüpft werden. Der Parameter <em>LinkedReceiveConnector</em> wurde aus <a href="https://technet.microsoft.com/de-de/library/aa998936(v=exchg.150)">New-SendConnector</a> und <a href="https://technet.microsoft.com/de-de/library/aa998294(v=exchg.150)">Set-SendConnector</a> entfernt.</p></td>
</tr>
</tbody>
</table>


## Antispam- und Antischadsoftwareoptionen


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verwalten von Antispam-Agents in der Exchange-Verwaltungskonsole</p></td>
<td><p>Wenn in Exchange 2010 Antispam-Agents auf einem Hub-Transport-Server aktiviert wurden, konnten die Antispam-Agents in der Exchange-Verwaltungskonsole verwaltet werden. Wenn Sie in Exchange 2013 auf einem Postfachserver Antispam-Agenten aktivieren, können Sie die Agenten nicht über das EAC verwalten. Sie müssen die Shell verwenden. Informationen dazu, wie Sie Antispam-Agents auf einem Postfachserver aktivieren, finden Sie unter <a href="enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md">Aktivieren der Antispamfunktionen auf einem Postfachserver</a>.</p></td>
</tr>
<tr class="even">
<td><p>Verbindungsfilter-Agent auf Hub-Transport-Servern</p></td>
<td><p>Bei Aktivierung der Antispam-Agents auf einem Hub-Transport-Server in Exchange 2010 war der Anlagenfilter-Agent der einzige Antispam-Agent, der nicht verfügbar war. Wenn Sie die Antispam-Agents in Exchange 2013 auf einem Postfachserver aktivieren, sind weder der Anlagenfilter-Agent noch der Verbindungsfilter-Agent verfügbar. Der Verbindungsfilter-Agent stellt IP-Zulassungslisten und IP-Sperrlisten bereit. Informationen dazu, wie Sie Antispam-Agents auf einem Postfachserver aktivieren, finden Sie unter <a href="enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md">Aktivieren der Antispamfunktionen auf einem Postfachserver</a>.</p>

> [!NOTE]
> Die Antispam-Agents auf einem Exchange 2013-Clientzugriffsserver können Sie nicht aktivieren. Daher besteht die einzige Möglichkeit zum Erhalt des Verbindungsfilter-Agents in der Installation eines Edge-Transport-Servers im Umgebungsnetzwerk. Weitere Informationen finden Sie unter <A href="edge-transport-servers-exchange-2013-help.md">Edge-Transport-Server</A>.


</td>
</tr>
</tbody>
</table>


## Messagingrichtlinie und -kompatibilität


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verwaltete Ordner</p></td>
<td><p>In Exchange 2010 werden zur Verwaltung der Nachrichtenaufbewahrung (Messaging Retention Management, MRM) verwaltete Ordner verwendet. Verwaltete Ordner werden in Exchange 2013 nicht unterstützt. Sie müssen Aufbewahrungsrichtlinien für MRM verwenden.</p>

> [!NOTE]
> Cmdlets für verwaltete Ordner sind weiterhin verfügbar. Sie können verwaltete Ordner, Einstellungen für verwaltete Inhalte und Postfachrichtlinien für verwaltete Ordner erstellen sowie eine Postfachrichtlinie für verwaltete Ordner auf einen Benutzer anwenden, aber der MRM-Assistent überspringt die Verarbeitung von Postfächern, auf die eine Postfachrichtlinie für verwaltete Ordner angewendet wurde.


</td>
</tr>
<tr class="even">
<td><p>Assistent zum Portieren von verwalteten Ordnern</p></td>
<td><p>In Exchange 2010 wird der Assistent zum Portieren von verwalteten Ordnern verwendet, um basierend auf den Einstellungen für verwaltete Ordner und Inhalte Aufbewahrungstags zu erstellen. In Exchange 2013 ist diese Funktionalität nicht in der Exchange-Verwaltungskonsole enthalten. Sie können das Cmdlet <strong>New-RetentionPolicyTag</strong> mit dem Parameter <em>ManagedFolderToUpgrade</em> verwenden, um basierend auf einem verwalteten Ordner ein Aufbewahrungstag zu erstellen.</p></td>
</tr>
</tbody>
</table>


## Unified Messaging und Voicemail


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verzeichnissuchen mithilfe automatischer Spracherkennung</p></td>
<td><p>In Exchange 2010 können Outlook Voice Access-Benutzer die Spracheingabe über die automatische Spracherkennung verwenden, um im Verzeichnis nach Benutzern zu suchen. Spracheingaben können auch in Outlook Voice Access zur Navigation durch Menüs, Nachrichten und andere Optionen eingesetzt werden. Allerdings müssen selbst Outlook Voice Access-Benutzer mit Sprachaktivierung die Telefontastatur verwenden, um ihre PIN einzugeben und durch die persönlichen Einstellungen zu navigieren.</p>
<p>In Exchange 2013 können authentifizierte und nicht authentifizierte Outlook Voice Access-Benutzer nicht per Spracheingabe oder automatischer Spracherkennung in beliebiger Sprache nach Benutzern im Verzeichnis suchen. Allerdings können Anrufer, die bei einer automatischen Telefonzentrale anrufen, per Spracheingabe in mehreren Sprachen durch die Menüs der automatischen Telefonzentrale navigieren und nach Benutzern im Verzeichnis suchen.</p></td>
</tr>
</tbody>
</table>


## Tools


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Best Practice Analyzer</p></td>
<td><p>In Exchange 2010 wurde Ihre Exchange-Bereitstellung vom Exchange Best Practice Analyzer analysiert, und es wurde überprüft, ob die Konfiguration bewährten Methoden von Microsoft entsprach. In Exchange 2013 wurde der Exchange Best Practice Analyzer durch den <a href="https://go.microsoft.com/fwlink/p/?linkid=391077">Office 365 Best Practices Analyzer für Exchange Server 2013</a> ersetzt.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenfluss-Problembehandlung</p></td>
<td><p>In Exchange 2010 war die Nachrichtenfluss-Problembehandlung hilfreich, um häufige Probleme mit dem Nachrichtenfluss zu behandeln. In Exchange 2013 wurde die Nachrichtenfluss-Problembehandlung eingestellt. In Exchange 2013 können Sie nun die Nachrichtenverfolgungsfunktion in der Exchange-Verwaltungskonsole nutzen. Weitere Informationen finden Sie unter <a href="track-messages-with-delivery-reports-exchange-2013-help.md">Nachverfolgen von Nachrichten mit Zustellungsberichten</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Systemmonitor</p></td>
<td><p>In Exchange 2010 war der Systemmonitor in der Exchange Toolbox enthalten, um Informationen zur Leistung des Messagingsystems erfassen zu können. Der Systemmonitor wird im Allgemeinen zum Anzeigen von Schlüsselparametern bei der Problembehebung von Leistungsproblemen verwendet. In Exchange 2013 wurde der Systemmonitor aus der Toolbox herausgenommen. Sie finden den Systemmonitor weiterhin unter <strong>Veraltung</strong> in Windows Server 2008.</p></td>
</tr>
<tr class="even">
<td><p>Leistungsproblembehandlung</p></td>
<td><p>In Exchange 2013 wurde die Leistungsproblembehandlung eingestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Routingprotokollanzeige</p></td>
<td><p>In Exchange 2013 wurde die Routingprotokollanzeige eingestellt.</p></td>
</tr>
</tbody>
</table>


## Postfachdatenbankkopien


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Update-MailboxDatabaseCopy</p></li>
<li><p>Assistent zum Aktualisieren einer Postfachdatenbankkopie</p></li>
</ul></td>
<td><p>Das Seeding des Inhaltsindexkatalogs über das Replikationsnetzwerk ist nicht mehr möglich. Es kann nur über ein MAPI-Netzwerk ausgeführt werden. Das gleiche gilt auch bei Verwendung des <code>-Network</code>-Parameters im Update-MailboxDatabaseCopy-Cmdlet.</p></td>
</tr>
</tbody>
</table>


## Exchange 2007-Funktionen, die in Exchange 2013 nicht mehr unterstützt werden

In diesem Abschnitt sind die Exchange Server 2007-Funktionen aufgeführt, die in Exchange 2013 nicht länger verfügbar sind.

## APIs und Entwicklung


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange WebDAV</p></td>
<td><p>Verwenden Sie die <a href="https://go.microsoft.com/fwlink/p/?linkid=167197">Exchange-Webdienste</a> oder die <a href="https://go.microsoft.com/fwlink/p/?linkid=157179">verwaltete EWS-API</a>. Alternativ können Sie einen Exchange 2007-Server für Postfächer verwalten, die von Anwendungen unter Verwendung von WebDAV verwaltet werden. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=169474">Migrieren von WebDAV</a>.</p></td>
</tr>
</tbody>
</table>


## Architektur


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Speichergruppen</p></td>
<td><p>Exchange 2013 verwendet keine Speichergruppen mehr. Stattdessen verwalten Sie einfach Postfachdatenbanken. Weitere Informationen finden Sie unter <a href="manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md">Verwalten von Postfachdatenbanken in Exchange 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Streamingsicherungs-APIs von Extensible Storage Engine (ESE)</p></td>
<td><p>Exchange 2013 unterstützt nur Exchange-fähige, auf dem Volumeschattenkopie-Dienst (Volume Shadow Copy Service, VSS) basierende Sicherungen. Exchange 2013 enthält kein Plug-In für Windows-Serversicherung, mit dem Sie Daten sichern und wiederherstellen können. Informationen finden Sie unter <a href="backup-restore-and-disaster-recovery-exchange-2013-help.md">Sicherung, Wiederherstellung und Notfallwiederherstellung</a>.</p></td>
</tr>
<tr class="odd">
<td><p>UDP-Benachrichtigungen (User Datagram-Protokoll)</p></td>
<td><p>Die Unterstützung für UDP-Benachrichtigungen (User Datagram Protocol) wurde aus Exchange 2013 entfernt. Dies beeinträchtigt das Benutzererlebnis, wenn Outlook 2003-Clients eine Verbindung mit ihren Postfächern auf einem Exchange 2013-Server herstellen. Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 2009942, <a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2009942">Das Aktualisieren von Ordnern dauert sehr lange, wenn ein Exchange Server 2010-Benutzer Outlook 2003 im Onlinemodus verwendet</a>.</p></td>
</tr>
</tbody>
</table>


## Hohe Verfügbarkeit


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fortlaufende Clusterreplikation (CCR, Cluster Continuous Replication)</p></td>
<td><p>Exchange 2013 verwendet Database Availability Groups (DAGs) und Postfachdatenbankkopien. Informationen finden Sie unter <a href="high-availability-and-site-resilience-exchange-2013-help.md">Hohe Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
<tr class="even">
<td><p>Fortlaufende lokale Replikation (LCR, Local Continuous Replication)</p></td>
<td><p>Exchange 2013 verwendet DAGs und Postfachdatenbankkopien. Informationen finden Sie unter <a href="high-availability-and-site-resilience-exchange-2013-help.md">Hohe Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Fortlaufende Standbyreplikation (SCR, Standby Continuous Replication)</p></td>
<td><p>Exchange 2013 verwendet DAGs und Postfachdatenbankkopien. Informationen finden Sie unter <a href="high-availability-and-site-resilience-exchange-2013-help.md">Hohe Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
<tr class="even">
<td><p>Einzelkopiecluster (SCC, Single Copy Cluster)</p></td>
<td><p>Exchange 2013 verwendet DAGs und Postfachdatenbankkopien. Informationen finden Sie unter <a href="high-availability-and-site-resilience-exchange-2013-help.md">Hohe Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Setup /recoverCMS</p></td>
<td><p>Exchange 2013 verwendet &quot;Setup /m:recoverServer&quot;. Informationen finden Sie unter <a href="recover-an-exchange-server-exchange-2013-help.md">Wiederherstellen eines Exchange-Servers</a>.</p></td>
</tr>
<tr class="even">
<td><p>Postfachclusterserver</p></td>
<td><p>Exchange 2013 verwendet DAGs und Postfachdatenbankkopien. Informationen finden Sie unter <a href="high-availability-and-site-resilience-exchange-2013-help.md">Hohe Verfügbarkeit und Ausfallsicherheit von Standorten</a>.</p></td>
</tr>
</tbody>
</table>


## Clientzugriff


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientauthentifizierung mithilfe der integrierten Windows-Authentifizierung (NTLM) für POP3- und IMAP4-Benutzer</p></td>
<td><p>NTLM wird in Exchange 2013 nicht für POP3- oder IMAP4-Clientverbindungen unterstützt. Bei Verbindungen von POP3- oder IMAP4-Clientprogrammen über NTLM treten Fehler auf. Wenn Sie die RTM-Version von Exchange 2013 ausführen, ist die Verwendung von Nur-Text-Authentifizierung mit SSL die empfohlene Alternative zu NTLM.</p>
<p>Bei Verwendung von Exchange 2013 muss ein Exchange 2007-Server in Ihrer Exchange 2013-Organisation beibehalten werden, um NTLM nutzen zu können.</p></td>
</tr>
</tbody>
</table>


## Outlook Web App und Outlook


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dokumentzugriff</p></td>
<td><p>Outlook Web App kann nicht für den Zugriff auf Microsoft SharePoint-Dokumentbibliotheken und Windows-Dateifreigaben verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenflags</p></td>
<td><p>In Outlook Web App 2013 gibt es keine Möglichkeit, ein benutzerdefiniertes Datum für ein Nachrichten-Flag festzulegen. Zum Festlegen benutzerdefinierter Daten können Sie Outlook verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>Rechtschreibprüfung</p></td>
<td><p>Outlook Web App verwendet die Funktionen für Rechtschreibprüfung in Ihrem Webbrowser.</p></td>
</tr>
<tr class="even">
<td><p>Suchordner</p></td>
<td><p>Benutzer können Suchordner derzeit nicht in Outlook Web App verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>Maximale Anzahl zwischengespeicherter Ansichten</p></td>
<td><p>In Exchange 2007 wurde die Änderung der maximalen Anzahl zwischengespeicherter Ansichten pro Datenbankparameter (msExchMaxCachedViews) für Outlook-Clients unterstützt. In Exchange 2013 wird dieser Parameter nicht mehr verwendet.</p></td>
</tr>
</tbody>
</table>


## Funktionen in Bezug auf Empfänger


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cmdlets <strong>Export-Mailbox</strong> und <strong>Import-Mailbox</strong></p></td>
<td><p>Verwenden Sie in Exchange 2013 Export- oder Importanforderungen. Weitere Informationen finden Sie unter <a href="mailbox-import-and-export-requests-exchange-2013-help.md">Import- und Exportanforderungen für Postfächer</a>.</p></td>
</tr>
<tr class="even">
<td><p>Cmdlet-Satz <strong>Move-Mailbox</strong></p></td>
<td><p>Verwenden Sie in Exchange 2013 Verschiebungsanforderungen, um Postfächer zu verschieben. Informationen finden Sie unter <a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Postfachverschiebungen in Exchange 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>ISInteg</p></td>
<td><p>Verwenden Sie in Exchange 2013 das Cmdlet <a href="https://technet.microsoft.com/de-de/library/ff625226(v=exchg.150)">New-MailboxRepairRequest</a>.</p></td>
</tr>
</tbody>
</table>


## Messagingrichtlinie und -kompatibilität


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verwaltete Ordner</p></td>
<td><p>In Exchange 2007 werden zur Verwaltung der Nachrichtenaufbewahrung (Messaging Retention Management, MRM) verwaltete Ordner verwendet. Verwaltete Ordner werden in Exchange 2013 nicht unterstützt. Sie müssen Aufbewahrungsrichtlinien für MRM verwenden.</p>

> [!NOTE]
> Cmdlets für verwaltete Ordner sind weiterhin verfügbar. Sie können verwaltete Ordner, Einstellungen für verwaltete Inhalte und Postfachrichtlinien für verwaltete Ordner erstellen sowie eine Postfachrichtlinie für verwaltete Ordner auf einen Benutzer anwenden, aber der MRM-Assistent überspringt die Verarbeitung von Postfächern, auf die eine Postfachrichtlinie für verwaltete Ordner angewendet wurde.


</td>
</tr>
</tbody>
</table>


## Unified Messaging und Voicemail


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Kommentare und Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verzeichnissuchen mithilfe automatischer Spracherkennung für Outlook Voice Access</p></td>
<td><p>In Exchange 2007 können Outlook Voice Access-Benutzer die Spracheingabe über die automatische Spracherkennung in Englisch (USA) – (en-US) verwenden, um im Verzeichnis nach Benutzern zu suchen. Spracheingaben können auch in Outlook Voice Access zur Navigation durch Menüs, Nachrichten und andere Optionen eingesetzt werden. Allerdings müssen selbst Outlook Voice Access-Benutzer mit Sprachaktivierung die Telefontastatur verwenden, um ihre PIN einzugeben und durch die persönlichen Einstellungen zu navigieren.</p>
<p>In Exchange 2013 können authentifizierte und nicht authentifizierte Outlook Voice Access-Benutzer nicht per Spracheingabe oder automatischer Spracherkennung in beliebiger Sprache nach Benutzern im Verzeichnis suchen. Allerdings können Anrufer, die bei einer automatischen Telefonzentrale anrufen, per Spracheingabe in mehreren Sprachen durch die Menüs der automatischen Telefonzentrale navigieren und nach Benutzern im Verzeichnis suchen.</p></td>
</tr>
</tbody>
</table>

