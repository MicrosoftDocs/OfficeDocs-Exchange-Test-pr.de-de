---
title: 'Berechtigungen für Clients und mobile Geräte: Exchange 2013 Help'
TOCTitle: Berechtigungen für Clients und mobile Geräte
ms:assetid: 57eca42a-5a7f-4c65-89f0-7a84f2dbea19
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638131(v=EXCHG.150)
ms:contentKeyID: 50475733
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen für Clients und mobile Geräte

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-11-10_

Die zum Ausführen von Aufgaben für Clients und mobile Geräte erforderlichen Berechtigungen richten sich nach dem durchzuführenden Vorgang bzw. nach dem auszuführenden Cmdlet. Weitere Informationen zu Funktionen für Clients und mobile Geräte finden Sie unter [Clients und mobile Funktionen](clients-and-mobile-exchange-2013-help.md).

Führen Sie folgende Aktionen aus, um herauszufinden, welche Berechtigungen Sie zum Ausführen des Verfahrens bzw. des Cmdlets benötigen:

1.  Suchen Sie in der Tabelle unten nach der Funktion, die dem Verfahren oder dem Cmdlet, das Sie ausführen möchten, am ehesten entspricht.

2.  Betrachten Sie als Nächstes die für die Funktion erforderlichen Berechtigungen. Ihnen muss eine dieser Rollengruppen, eine entsprechende benutzerdefinierte Rollengruppe oder eine entsprechende Verwaltungsrolle zugewiesen sein. Sie können auch auf eine Rollengruppe klicken, um die zugehörigen Verwaltungsrollen anzuzeigen. Wenn für eine Funktion mehr als eine Rollengruppe aufgelistet wird, muss Ihnen lediglich eine der Rollengruppen zugewiesen sein, um diese Funktion nutzen zu können. Weitere Informationen zu Rollengruppen und Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

3.  Führen Sie jetzt das Cmdlet **Get-ManagementRoleAssignment** aus, um in den Ihnen zugewiesenen Rollengruppen oder Verwaltungsrollen nachzusehen, ob Sie über die zum Verwalten der Funktion erforderlichen Berechtigungen verfügen.
    

    > [!NOTE]
    > Ihnen muss die Verwaltungsrolle "Rollenverwaltung" zugewiesen sein, um das Cmdlet <STRONG>Get-ManagementRoleAssignment</STRONG> ausführen zu können. Wenn Sie nicht über die Berechtigungen zum Ausführen des Cmdlets <STRONG>Get-ManagementRoleAssignment</STRONG> verfügen, wenden Sie sich den Exchange-Administrator, um die Ihnen zugewiesenen Rollengruppen oder Verwaltungsgruppen zu erfahren.



Wenn Sie die Möglichkeit zum Verwalten einer Funktion an einen anderen Benutzer delegieren möchten, finden Sie weitere Informationen unter [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md).


> [!NOTE]
> Einige Funktionen erfordern u.&nbsp;U. lokale Administratorrechte für den Server, den Sie verwalten möchten. Um diese Funktionen zu verwalten, müssen Sie Mitglied der lokalen Administratorengruppe auf dem Server sein.



## Clientzugriffsserver – Berechtigungen

Für den Clientzugriffsserver können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Arrayeinstellungen für den Clientzugriffsserver</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für den Clientzugriffsserver</p></td>
<td><p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Einstellungen für den E-Mail-Kanal des Clientzugriffsdiensts</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Benutzereinstellungen für den Clientzugriff</p></td>
<td><p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Einstellungen für das virtuelle Verzeichnis für den Clientzugriff</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für den RPC-Clientzugriff</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="odd">
<td><p>Proxyeinstellungen für Pushbenachrichtigungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>OAuth-Authentifizierungsumleitungseinstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


## Exchange ActiveSync-Berechtigungen

Für Exchange ActiveSync können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange ActiveSync-Sperreinstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für Exchange ActiveSync-Postfachrichtlinien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Servereinstellungen für Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Benutzereinstellungen für Exchange ActiveSync</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für das virtuelle Exchange ActiveSync-Verzeichnis</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Einstellungen für Postfachrichtlinien für mobile Geräte</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Benutzereinstellungen für mobile Geräte</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für den AutoErmittlungsdienst

Für den AutoErmittlungsdienst können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Konfigurationseinstellungen des AutoErmittlungsdiensts</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Delegiertes Setup</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für die virtuellen Verzeichnisse für die AutoErmittlung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für den Verfügbarkeitsdienst

Für den Verfügbarkeitsdienst können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einstellungen des Adressraums für den Verfügbarkeitsdienst</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="even">
<td><p>Konfigurationseinstellungen für den Verfügbarkeitsdienst</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für die Clienteinschränkung

Für die Clienteinschränkung können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einstellungen für die Clienteinschränkung</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für Exchange-Webdienste

Für die virtuellen Verzeichnisse der Webdienste können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einstellungen für die virtuellen Verzeichnisse der Exchange-Webdienste</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Testen von Exchange-Webdiensten</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Testen von Outlook-Webdiensten</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für Outlook Anywhere

Für Outlook Anywhere können die folgenden Einstellungen konfiguriert und verwaltet werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Konfiguration von Outlook Anywhere (Aktivieren, Deaktivieren, Ändern, Anzeigen)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Delegiertes Setup</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
<tr class="even">
<td><p>RPC-über-HTTP-Proxy-Komponente</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="odd">
<td><p>Testen der Konnektivität von Outlook Anywhere</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für Outlook Web App

Mit den folgenden Funktionen können Sie Einstellungen von Outlook Web App anzeigen, die Sicherheit von Outlook Web App und den Benutzerzugriff auf die Anwendung steuern sowie die Konnektivität von Outlook Web App testen.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Grafikbearbeitung</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="even">
<td><p>IIS-Manager</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="odd">
<td><p>ISA Server 2006</p></td>
<td><p>ISA Server-Organisationsadministrator</p></td>
</tr>
<tr class="even">
<td><p>Outlook Web App-Postfachrichtlinien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Virtuelle Outlook Web App-Verzeichnisse</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Registrierungs-Editor</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="odd">
<td><p>S/MIME-Konfiguration</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Texteditor</p></td>
<td><p>Lokaler Serveradministrator</p></td>
</tr>
<tr class="odd">
<td><p>Anzeigen von Outlook Web App-Postfachrichtlinien</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Delegiertes Setup</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für POP3 und IMAP4

Für POP3 und IMAP4 können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IMAP4-Einstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="even">
<td><p>POP3-Einstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="odd">
<td><p>Testen von IMAP4-Einstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
<tr class="even">
<td><p>Testen von POP3-Einstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p>
<p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für virtuelle Windows PowerShell-Verzeichnisse

Für die Windows PowerShell können die folgenden Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Testen von Windows PowerShell</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Windows PowerShell-Einstellungen</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
</tr>
</tbody>
</table>


## Berechtigungen für Textnachrichten

Für Textnachrichten können die nachfolgend aufgeführten Einstellungen konfiguriert werden.

Benutzer, denen die Verwaltungsrollengruppe mit Leserechten zugewiesen ist, können die Konfiguration der Funktionen in der folgenden Tabelle anzeigen. Weitere Informationen finden Sie unter Organisationsverwaltung – nur Leserechte[Organisationsverwaltung mit Leserechten](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Erforderliche Berechtigungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Benachrichtigungseinstellungen für Textnachrichten</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für Textnachrichten</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
</tr>
<tr class="odd">
<td><p>Benutzereinstellungen für Textnachrichten</p></td>
<td><p><a href="mytextmessaging-role-exchange-2013-help.md">Rolle „MyTextMessaging“</a></p>
<p>Benutzer können Einstellungen für Textnachrichten im eigenen Postfach konfigurieren. Administratoren können die Einstellungen für Textnachrichten nicht in Postfächern anderer Benutzer konfigurieren.</p></td>
</tr>
</tbody>
</table>

