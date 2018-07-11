---
title: 'Authentifizierungsmechanismen für Empfangsconnectors: Exchange 2013 Help'
TOCTitle: Authentifizierungsmechanismen für Empfangsconnectors
ms:assetid: 926424e1-83e3-4c4b-b2dd-bf814d81e877
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657472(v=EXCHG.150)
ms:contentKeyID: 50476187
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Authentifizierungsmechanismen für Empfangsconnectors

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_


Die Authentifizierungsmechanismen für einen Empfangsconnector sind folgende:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Authentifizierungsmechanismus</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Keine</p></td>
<td><p>Keine Authentifizierung.</p></td>
</tr>
<tr class="even">
<td><p>TLS</p></td>
<td><p>STARTTLS ankündigen. Setzt die Verfügbarkeit eines Serverzertifikats zur Bereitstellung von TLS voraus.</p></td>
</tr>
<tr class="odd">
<td><p>Integriert</p></td>
<td><p>NTLM und Kerberos (integrierte Windows-Authentifizierung).</p></td>
</tr>
<tr class="even">
<td><p>BasicAuth</p></td>
<td><p>Standardauthentifizierung. Setzt eine authentifizierte Anmeldung voraus.</p></td>
</tr>
<tr class="odd">
<td><p>BasicAuthRequireTLS</p></td>
<td><p>Standardauthentifizierung über TLS. Setzt ein Serverzertifikat voraus.</p></td>
</tr>
<tr class="even">
<td><p>ExchangeServer</p></td>
<td><p>Exchange Server-Authentifizierung (Generic Security Services Application Programming Interface (GSSAPI) und Mutual GSSAPI).</p></td>
</tr>
<tr class="odd">
<td><p>ExternalAuthoritative</p></td>
<td><p>Die Verbindung wird als extern gesichert betrachtet, da ein Exchange-externer Sicherheitsmechanismus verwendet wird. Bei der Verbindung kann es sich um eine IPsec-Zuordnung (Internet Protocol Security) oder ein virtuelles privates Netzwerk (VPN) handeln. Alternativ können die Server sich auch in einem vertrauenswürdigen, physisch gesteuerten Netzwerk befinden. Für die Authentifizierungsmethode <code>ExternalAuthoritative</code> ist die Berechtigungsgruppe <code>ExchangeServers</code> erforderlich. Diese Kombination aus Authentifizierungsmethode und Sicherheitsgruppe ermöglicht die Auflösung von anonymen Absender-E-Mail-Adressen für Nachrichten, die über diesen Connector empfangen werden.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen über den Empfangsconnector-Authentifizierungsmechanismus finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

