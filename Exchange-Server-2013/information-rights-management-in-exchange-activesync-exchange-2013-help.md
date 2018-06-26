---
title: 'Verwaltung von Informationsrechten in Exchange ActiveSync: Exchange 2013 Help'
TOCTitle: Verwaltung von Informationsrechten in Exchange ActiveSync
ms:assetid: ebf04460-4d61-4b00-86b9-85ec1dbbd6a1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff657743(v=EXCHG.150)
ms:contentKeyID: 50476995
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwaltung von Informationsrechten in Exchange ActiveSync

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Information-Worker verwenden zum Austausch vertraulicher Informationen häufig E-Mail-Nachrichten. Zur besseren Sicherung dieser Informationen können Organisationen die Verwaltung von Informationsrechten (Information Rights Management, IRM) verwenden und Nachrichteninhalte dauerhaft schützen. Da mobile Geräte immer häufiger für den Zugriff auf E-Mail verwendet werden, ist es wichtig, dass die Benutzer mobiler Geräte durch IRM geschützte Inhalte erstellen und nutzen können.

**Inhalt**

Mobiler IRM-Schutz in Exchange 2013

Anforderungen

Sicherheit

Aktivieren von IRM in Exchange ActiveSync

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit IRM gibt? Informationen hierzu finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Mobiler IRM-Schutz in Exchange 2013

In Exchange 2013 können Benutzer mit IRM in Microsoft Exchange ActiveSync auf allen unterstützten Exchange ActiveSync-Geräten auf umfassende IRM-Funktionen zugreifen, ohne AD RMS-Berechtigungen konfigurieren oder das Gerät mit einem Computer verbinden und für IRM aktivieren zu müssen. Zudem muss auf dem mobilen Gerät nicht Windows ausgeführt werden. Exchange ActiveSync ist von Microsoft für Hersteller mobiler Geräte, OEMs (Original Equipment Manufacturer) und andere lizenziert. Für eine Liste aktueller Exchange ActiveSync-Lizenznehmer erweitern Sie den Abschnitt „Exchange ActiveSync-Protokoll“ auf der Seite [Microsoft-Technologielizenzierung](https://go.microsoft.com/fwlink/p/?linkid=198562).

IRM in Exchange ActiveSync bietet Benutzern mobiler Geräte folgende Möglichkeiten:

  - Erstellen von IRM-geschützten Nachrichten.

  - Lesen von IRM-geschützten Nachrichten.

  - Antworten und Weiterleiten von IRM-geschützten Nachrichten.

Mobiler IRM-Schutz in Exchange 2013

## Anforderungen

Dabei gelten folgenden Anforderungen:

  - Auf den Clientzugriffsservern in der Organisation muss Exchange 2010 SP1 oder höher ausgeführt werden.

  - In der Organisation muss ein AD RMS-Server bereitgestellt werden.

  - IRM muss für interne Nachrichten aktiviert sein. Dies ist eine Voraussetzung für alle IRM-Features in Exchange 2010. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren von IRM für interne Nachrichten](enable-or-disable-irm-for-internal-messages-exchange-2013-help.md).

  - IRM muss in der Exchange ActiveSync-Postfachrichtlinie aktiviert sein. Sie können IRM mithilfe unterschiedlicher Exchange ActiveSync-Postfachrichtlinien für verschiedene Benutzergruppen aktivieren oder deaktivieren.

  - Geräte, die das Exchange ActiveSync-Protokoll in der Version 14.1 unterstützen, einschließlich Mobiltelefone unter Windows, können IRM in Exchange ActiveSync unterstützen. Die mobile E-Mail-Anwendung des Geräts muss das Tag "RightsManagementInformation" unterstützen, das in Exchange ActiveSync, Version 14.1, definiert ist.

Mobiler IRM-Schutz in Exchange 2013

## Sicherheit

Wenn Sie IRM in Exchange ActiveSync aktivieren, entschlüsselt der Clientzugriffsserver IRM-geschützte Nachrichten vor der Bereitstellung der Nachrichten für den Zugriff durch das unterstützte mobile Gerät. Bei der Synchronisierung befinden sich IRM-geschützte Nachrichten im unverschlüsselten Format auf dem mobilen Gerät. Der IRM-Schutz wird durch die IRM-fähige E-Mail-Clientanwendung auf dem mobilen Gerät erzwungen.

IRM in Exchange ActiveSync entschlüsselt keine IRM-geschützten Anlagen auf dem Clientzugriffsserver. Der Zugriff auf IRM-geschützte Dateien wird durch die Anwendung erzwungen, die zum Erstellen oder Anzeigen der Datei verwendet wird. Auf einem Windows-Mobiltelefon wird der IRM-Schutz für Microsoft Office-Dateien beispielsweise durch [Microsoft Office Mobile](https://go.microsoft.com/fwlink/p/?linkid=205121) erzwungen. Für den Zugriff auf Office-Dateien mit IRM-Schutz müssen Benutzer das Gerät mit einem Computer verbinden und Office Mobile auf dem RMS-Server aktivieren.

Bei der Aktivierung von IRM in Exchange ActiveSync sollten Sie die in der folgenden Tabelle angezeigten Exchange ActiveSync-Richtlinieneinstellungen verwenden, um die Sicherheit mobiler Geräte zu gewährleisten.

### Exchange ActiveSync-Richtlinieneinstellungen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Mithilfe des Exchange ActiveSync-Assistenten für neue Postfachrichtlinien konfigurieren</th>
<th>Mithilfe des Cmdlets &quot;New-ActiveSyncMailboxPolicy&quot; konfigurieren</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Eingeben eines Kennworts für den Zugriff auf das mobile Gerät durch den Benutzer anfordern.</p></td>
<td><p>Aktivieren Sie das Kontrollkästchen <strong>Kennwort anfordern</strong>.</p></td>
<td><p>Legen Sie den Parameter <em>DevicePasswordEnabled</em> auf <code>$true</code> fest.</p></td>
</tr>
<tr class="even">
<td><p>Verschlüsselung für das mobile Gerät aktivieren.</p></td>
<td><p>Aktivieren Sie das Kontrollkästchen <strong>Kennwort anfordern</strong>, und aktivieren Sie dann das Kontrollkästchen <strong>Verschlüsselung auf dem Gerät anfordern</strong>.</p></td>
<td><p>Legen Sie den Parameter <em>RequireDeviceEncryption</em> auf <code>$true</code> fest.</p>

> [!IMPORTANT]
> Wenn Sie den Parameter <EM>RequireDeviceEncryption</EM> auf <CODE>$true</CODE> festlegen, können mobile Geräte, die keine Geräteverschlüsselung unterstützen, keine Verbindung herstellen.


</td>
</tr>
<tr class="odd">
<td><p>Synchronisierung nicht bereitstellbarer mobiler Geräte mit dem Exchange-Server nicht zulassen.</p></td>
<td><p>Deaktivieren Sie das Kontrollkästchen <strong>Nicht bereitstellbare Geräte zulassen</strong>.</p></td>
<td><p>Legen Sie den Parameter <em>AllowNonProvisionableDevices</em> auf <code>$false</code> fest.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen finden Sie unter [Postfachrichtlinien für mobile Geräte](mobile-device-mailbox-policies-exchange-2013-help.md).

Mobiler IRM-Schutz in Exchange 2013

## Aktivieren von IRM in Exchange ActiveSync

Gehen Sie wie folgt vor, um IRM in Exchange ActiveSync zu aktivieren:

1.  Fügen Sie das Verbundpostfach (ein von Exchange 2013- und Exchange 2010-Setup erstelltes Systempostfach) der Benutzergruppe mit Administratorrechten in AD RMS hinzu. Dies ermöglicht Exchange 2013- und Exchange 2010-Servern den Zugriff auf IRM-geschützte Nachrichten. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

2.  Verwenden Sie das Cmdlet [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) in der Exchange-Verwaltungsshell, um IRM auf dem Clientzugriffsserver zu aktivieren. Dies aktiviert IRM in Exchange ActiveSync und IRM in Microsoft OfficeOutlook Web App für Ihre Organisation. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern](enable-or-disable-information-rights-management-on-client-access-servers-exchange-2013-help.md).

Mobiler IRM-Schutz in Exchange 2013

