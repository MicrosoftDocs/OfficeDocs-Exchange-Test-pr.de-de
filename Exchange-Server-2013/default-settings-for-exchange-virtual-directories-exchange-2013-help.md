---
title: 'Standardeinstellungen für virtuelle Exchange-Verzeichnisse: Exchange 2013 Help'
TOCTitle: Standardeinstellungen für virtuelle Exchange-Verzeichnisse
ms:assetid: d2d89ce6-4721-4737-a325-fba5ad9422e0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg247612(v=EXCHG.150)
ms:contentKeyID: 52062906
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Standardeinstellungen für virtuelle Exchange-Verzeichnisse

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Exchange Server 2013 konfiguriert bei der Installation automatisch mehrere virtuelle IIS-Verzeichnisse (Internet Information Services). In diesem Thema finden Sie Informationen zu den Standardeinstellungen für die IIS-Authentifizierung und SSL (Secure Sockets Layer) für die Clientzugriffs- und Postfachserver.

## Clientzugriffsserver

In der folgenden Tabelle sind die Standardeinstellungen für einen eigenständigen Exchange 2013-Clientzugriffsserver aufgeführt.

### Standardeinstellungen für IIS-Authentifizierung und SSL auf einem Clientzugriffsserver

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Virtuelles Verzeichnis</th>
<th>Authentifizierungsmethode</th>
<th>SSL-Einstellungen</th>
<th>Verwaltungsmethode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standardwebseite</p></td>
<td><ul>
<li><p>Anonym</p></li>
</ul></td>
<td><ul>
<li><p>Erforderlich</p></li>
</ul></td>
<td><p>IIS-Verwaltungskonsole</p></td>
</tr>
<tr class="even">
<td><p>aspnet_client</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>IIS-Verwaltungskonsole</p></td>
</tr>
<tr class="odd">
<td><p>AutoErmittlung</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
<li><p>Standardauthentifizierung</p></li>
<li><p>Windows-Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Exchange-Verwaltungsshell (Shell)</p></td>
</tr>
<tr class="even">
<td><p>ecp</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
<li><p>Standardauthentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Exchange-Verwaltungskonsole oder -Shell</p></td>
</tr>
<tr class="odd">
<td><p>EWS</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
<li><p>Windows-Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Shell</p></td>
</tr>
<tr class="even">
<td><p>Microsoft-Server-ActiveSync</p></td>
<td><ul>
<li><p>Standardauthentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Exchange-Verwaltungskonsole oder Shell</p></td>
</tr>
<tr class="odd">
<td><p>OAB</p></td>
<td><ul>
<li><p>Windows-Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>Nicht erforderlich</p></li>
</ul></td>
<td><p>Exchange-Verwaltungskonsole oder Shell</p></td>
</tr>
<tr class="even">
<td><p>owa</p></td>
<td><ul>
<li><p>Standardauthentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Exchange-Verwaltungskonsole oder Shell</p></td>
</tr>
<tr class="odd">
<td><p>PowerShell</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>Nicht erforderlich</p></li>
</ul></td>
<td><p>Shell</p></td>
</tr>
<tr class="even">
<td><p>Rpc</p></td>
<td><ul>
<li><p>Standardauthentifizierung</p></li>
<li><p>Windows-Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Shell</p></td>
</tr>
<tr class="odd">
<td><p>RpcWithCert</p></td>
<td><p>Standardmäßig sind alle Authentifizierungsmethoden deaktiviert.</p></td>
<td><ul>
<li><p>Erforderlich</p></li>
</ul></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


## Postfachserver

In der folgenden Tabelle sind die Standardeinstellungen für einen eigenständigen Exchange 2013-Postfachserver aufgeführt.

### Standardeinstellungen für IIS-Authentifizierung und SSL auf einem Postfachserver

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Virtuelles Verzeichnis</th>
<th>Authentifizierungsmethode</th>
<th>SSL-Einstellungen</th>
<th>Verwaltungsmethode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standardwebseite</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>SSL erforderlich</p></li>
<li><p>128-Bit-Verschlüsselung erforderlich</p></li>
</ul></td>
<td><p>Dieses virtuelle Verzeichnis kann nicht vom Benutzer konfiguriert werden.</p></td>
</tr>
<tr class="even">
<td><p>PowerShell</p></td>
<td><ul>
<li><p>Anonyme Authentifizierung</p></li>
</ul></td>
<td><ul>
<li><p>Nicht erforderlich</p></li>
</ul></td>
<td><p>Shell</p></td>
</tr>
</tbody>
</table>

