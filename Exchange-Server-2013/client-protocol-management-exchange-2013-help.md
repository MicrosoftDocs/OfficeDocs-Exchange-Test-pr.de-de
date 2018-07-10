---
title: 'Clientprotokollverwaltung: Exchange 2013 Help'
TOCTitle: Clientprotokollverwaltung
ms:assetid: 89ba6d24-d1d3-46d5-a0ae-61f0d4c6df21
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657727(v=EXCHG.150)
ms:contentKeyID: 50476201
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Clientprotokollverwaltung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Clientprotokolle von Exchange ActiveSync, Outlook Web App, POP3, IMAP4, dem AutoErmittlungsdienst, den Exchange-Webdiensten und dem Verfügbarkeitsdienst werden in drei verschiedenen Bereichen verwaltet: in der Exchange-Verwaltungskonsole, in der Exchange-Verwaltungsshell und im Internetinformationsdienste-Manager (Internet Information Services, IIS). Die Einstellungen, die an den einzelnen Stellen verwaltet werden, unterscheiden sich je nach Clientprotokoll.

## Verwalten von Outlook Web App-Einstellungen

Die meisten Einstellungen, die sich darauf auswirken, welche Outlook Web App-Funktionen den Benutzern zur Verfügung stehen, können im virtuellen Outlook Web App-Verzeichnis eingestellt oder in einer Outlook Web App-Postfachrichtlinie konfiguriert werden. Mithilfe von Outlook Web App-Postfachrichtlinien können Sie definieren, welche Funktionen für einzelne Benutzer verfügbar sind. Postfachrichtlinieneinstellungen setzen die Einstellungen für virtuelle Verzeichnisse außer Kraft. Weitere Informationen zum Verwalten von Outlook Web App finden Sie unter [Outlook Web App](outlook-web-app-exchange-2013-help.md).

## Verwalten von Exchange ActiveSync-Einstellungen

In Exchange 2010 wurden alle Clientzugriffsprotokolle in einer einzigen Serverrolle implementiert und verwaltet, der Clientzugriffs-Serverrolle. Die Protokolle wurden in einer einzelnen Instanz von IIS verwaltet, es gab für jedes Clientprotokoll ein einziges virtuelles Verzeichnisobjekt in Active Directory, und es wurde ein einziger Satz von Cmdlets zum Konfigurieren des virtuellen Verzeichnisses verwendet.

In Exchange 2013 wird die Clientprotokollverwaltung für Exchange ActiveSync zwischen dem Clientzugriffsserver und dem Postfachserver aufgeteilt. Aufgrund dieser Architekturänderung können Sie verschiedene Verwaltungsaufgaben für virtuelle Verzeichnisse sowohl auf dem Clientzugriffsserver als auch auf dem Postfachserver ausführen. Wenn diese beiden Server nicht auf demselben physischen Computer installiert sind, ändern sich die mit den Cmdlets für virtuelle Verzeichnisse verwendeten Parameter basierend auf der Serverrolle, in der Sie sie ausführen.

Weitere Informationen zu den Architekturänderungen in Exchange 2013 finden Sie unter [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).

Auf das virtuelle Exchange ActiveSync-Verzeichnis können zwei Arten von Einstellungen angewendet werden:

  - Einstellungen für die Postfachsitzung

  - Einstellungen für den Server und das virtuelle Verzeichnis

Bei den Einstellungen für die Postfachsitzung handelt es sich um Benutzersitzungseinstellungen. Wenn ein Benutzer eine Verbindung mit einem Clientzugriffsserver herstellt, wird die Verbindung per Proxy an den Postfachserver weitergeleitet, der das Postfach des Benutzers enthält. Eine eindeutige ID des virtuellen Verzeichnisses ist der Proxyanforderung beigefügt. Der Postfachserver ruft anschließend die Einstellungen für das virtuelle Verzeichnis aus Active Directory ab und wendet sie auf die Sitzung an. Die Einstellungen für das virtuelle Verzeichnis werden auf dem Postfachserver zwischengespeichert, um die Leistung zu verbessern.

Wenn die Verbindung per Proxy an einen anderen Active Directory-Standort weitergeleitet wird, werden die Einstellungen für das virtuelle Verzeichnis von dem Clientzugriffsserver an demselben Standort geladen, an dem sich auch der Postfachserver befindet, und nicht von dem Clientzugriffsserver, an dem die Verbindung initiiert wurde.

In den folgenden Tabellen wird gezeigt, welche Einstellungen für virtuelle Verzeichnisse auf welchen Servern verwaltet werden können. Wenn Sie versuchen, eine bestimmte Einstellung auf einem Server zu verwalten, auf den sie nicht anwendbar ist, werden Sie in einer Fehlermeldung darauf hingewiesen, dass die betreffende Einstellung für den jeweiligen Server schreibgeschützt ist.

**Einstellungen für virtuelle Exchange ActiveSync-Verzeichnisse auf Clientzugriffsservern**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BadItemReportingEnabled</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>BasicAuthEnabled</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>ClientCertAuth</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>CompressionEnabled</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>ExternalAuthenticationMethods</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>ExternalURL</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>InternalAuthenticationMethods</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>InternalURL</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>MobileClientCertificateAuthorityURL</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>MobileClientCertificateProvisioningEnabled</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>MobileClientCertTemplateName</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>RemoteDocumentsActionForUnknownServers</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>RemoteDocumentsAllowedServers</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>RemoteDocumentsBlockedServers</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>RemoteDocumentsInternalDomainSuffixList</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>SendWatsonReport</p></td>
<td><p>Clientzugriff</p></td>
</tr>
</tbody>
</table>


**Einstellungen für virtuelle Exchange ActiveSync-Verzeichnisse auf Clientzugriffs- und Postfachservern**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ApplicationRoot</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>AppPoolID</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>MetabasePath</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>ProxySubVdir</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>VirtualDirectoryName</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>WebsiteName</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
</tbody>
</table>


## Verwalten von POP3- und IMAP4-Einstellungen

In Exchange 2013 wurde auch die Implementierung der POP3- und IMAP4-Protokolle zwischen den Clientzugriffs- und Postfachserverrollen aufgeteilt. Aufgrund der neuen Implementierung wird die POP3- und die IMAP4-Konnektivität jeweils von einem Dienst auf dem Clientzugriffsserver sowie von einem Dienst auf dem Postfachserver verwaltet. Die Namen der Dienste, die auf dem Clientzugriffsserver ausgeführt werden, stimmen mit den Namen aus Exchange 2010 überein: Microsoft Exchange-IMAP4-Dienst und Microsoft Exchange-POP3-Dienst. Die beiden neuen Dienste, die auf dem Postfachserver ausgeführt werden, heißen Microsoft Exchange-IMAP4-Back-End-Dienst und Microsoft Exchange-POP3-Back-End-Dienst.

Beachten Sie bei der Verwaltung der POP3- und der IMAP4-Konnektivität in Ihrer Organisation Folgendes:

  - Wenn Sie die Clientzugriffs-Serverrolle und die Postfachserverrolle auf demselben Computer ausführen, werden alle Änderungen an den POP3- oder IMAP4-Einstellungen automatisch auf den richtigen POP3- und IMAP4-Dienst angewendet.

  - Wenn Sie die Clientzugriffs-Serverrolle und die Postfachserverrolle auf verschiedenen Computern ausführen, müssen Sie die Einstellungen auf dem Computer verwalten, auf dem die zu ändernde Einstellung verwaltet wird.

Die folgenden Tabellen zeigen, welche POP-/IMAP-Einstellungen der jeweiligen Serverrolle zugeordnet sind.

**POP3- und IMAP4-Einstellungen auf dem Clientzugriffsserver**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AuthenticatedConnectionTimeout</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>Banner</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>ExternalConnectionSettings</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>InternalConnectionSettings</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>MaxCommandSize</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>MaxConnectionFromSingleIP</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>MaxConnections</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>MaxConnectionsPerUser</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="odd">
<td><p>PreAuthenticatedConnectionTimeout</p></td>
<td><p>Clientzugriff</p></td>
</tr>
<tr class="even">
<td><p>UnencryptedOrTLSBindings</p></td>
<td><p>Clientzugriff</p></td>
</tr>
</tbody>
</table>


**POP3- und IMAP4-Einstellungen auf dem Postfachserver**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CalendarItemRetrivalOption</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="even">
<td><p>EnableExactRFC822Size</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="odd">
<td><p>MessageRetrievalSortOrder</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="even">
<td><p>OWAServerURL</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="odd">
<td><p>ProxyTargetPort</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="even">
<td><p>ShowHiddenFoldersEnabled</p></td>
<td><p>Postfach</p></td>
</tr>
<tr class="odd">
<td><p>SuppressReadReceipt</p></td>
<td><p>Postfach</p></td>
</tr>
</tbody>
</table>


**POP3- und IMAP4-Einstellungen auf dem Clientzugriffs- und dem Postfachserver**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>X509CertificateName</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>EnforceCertificateErrors</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>LogFileLocation</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>LogFileRolloverSettings</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>LoginType</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>LogPerFileSizeQuota</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>ProtocolLogEnabled</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="even">
<td><p>Server</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
<tr class="odd">
<td><p>X509CertificateName</p></td>
<td><p>Clientzugriff und Postfach</p></td>
</tr>
</tbody>
</table>

