---
title: 'Empfangsconnectorberechtigungen: Exchange 2013 Help'
TOCTitle: Empfangsconnectorberechtigungen
ms:assetid: 31af7139-6823-411b-81b3-e42edd83ee6c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673053(v=EXCHG.150)
ms:contentKeyID: 50475279
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Empfangsconnectorberechtigungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

In der folgenden Tabelle werden verschiedene Berechtigungstypen und deren Beschreibungen aufgeführt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Empfangsconnectorberechtigung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ms-Exch-SMTP-Submit</p></td>
<td><p>Der Sitzung muss diese Berechtigung gewährt werden, oder es können keine Nachrichten an den Empfangsconnector übermittelt werden. Wenn eine Sitzung nicht über diese Berechtigung verfügt, schlagen die Befehle MAIL FROM und AUTH fehl.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-SMTP-Accept-Any-Recipient</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, Nachrichten über diesen Connector weiterzugeben. Wird diese Berechtigung nicht gewährt, akzeptiert der Connector nur Nachrichten an Empfänger in zugelassenen Domänen.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-SMTP-Accept-Any-Sender</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, die Spoofingprüfung der Absenderadresse zu umgehen.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-SMTP-Accept-Authoritative-Domain-Sender</p></td>
<td><p>Diese Berechtigung gestattet Sendern mit E-Mail-Adressen aus autoritativen Domänen, eine Sitzung zu diesem Empfangsconnector aufzubauen.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-SMTP-Accept-Authentication-Flag</p></td>
<td><p>Diese Berechtigung ermöglicht es Exchange 2003-Servern, Nachrichten von internen Absendern zu übermitteln. Exchange 2010 erkennt die Nachrichten als intern. Der Absender kann die Nachricht als vertrauenswürdig deklarieren. Nachrichten, die über anonyme Übermittlungen im Exchange-System eingehen, werden mit dieser Kennzeichnung durch die Exchange-Organisation mit dem Status &quot;nicht vertrauenswürdig&quot; weitergegeben.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Accept-Headers-Routing</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, eine Nachricht zu übermitteln, bei der alle empfangenen Kopfzeilen intakt sind. Wenn diese Berechtigung nicht erteilt wird, entfernt der Server alle empfangenen Kopfzeilen.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-Accept-Headers-Organization</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, eine Nachricht zu übermitteln, bei der alle Organisationskopfzeilen intakt sind. Organisationskopfzeilen beginnen alle mit <strong>X-MS-Exchange-Organization-</strong>. Wenn diese Berechtigung nicht erteilt wird, entfernt der empfangende Server alle Organisationskopfzeilen.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Accept-Headers-Forest</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, eine Nachricht zu übermitteln, bei der alle Gesamtstrukturkopfzeilen intakt sind. Gesamtstrukturkopfzeilen beginnen immer mit <strong>X-MS-Exchange-Forest-</strong>. Wenn diese Berechtigung nicht erteilt wird, entfernt der empfangende Server alle Gesamtstrukturkopfzeilen.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-Accept-Exch50</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, eine Nachricht zu übermitteln, die den Befehl XEXCH50 enthält. Dieser Befehl ist für die Interoperabilität mit Exchange 2003 erforderlich. Der Befehl XEXCH50 stellt Daten wie die SCL-Bewertung (Spam Confidence Level) einer Nachricht bereit.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Bypass-Message-Size-Limit</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, eine Nachricht zu übermitteln, die die für den Connector konfigurierte Nachrichtengrößenbeschränkung überschreitet.</p></td>
</tr>
<tr class="odd">
<td><p>Ms-Exch-Bypass-Anti-Spam</p></td>
<td><p>Mit dieser Berechtigung ist die Sitzung in der Lage, die Antispamfilterung zu umgehen.</p></td>
</tr>
</tbody>
</table>

