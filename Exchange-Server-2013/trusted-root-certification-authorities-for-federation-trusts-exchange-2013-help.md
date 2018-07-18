---
title: 'Vertrauenswürdige Stammzertifizierungsstellen für Verbundvertrauensstellungen: Exchange 2013 Help'
TOCTitle: Vertrauenswürdige Stammzertifizierungsstellen für Verbundvertrauensstellungen
ms:assetid: d4224bf5-69b3-484c-8a70-4f230d3dbdd9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee332350(v=EXCHG.150)
ms:contentKeyID: 50476792
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Vertrauenswürdige Stammzertifizierungsstellen für Verbundvertrauensstellungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-07-26_

Um eine Verbundvertrauensstellung zwischen Ihrer Microsoft Exchange Server 2013-Organisation und dem [Azure Active Directory-Authentifizierungssystem](https://go.microsoft.com/fwlink/p/?linkid=135986) zu erstellen, muss auf dem zum Erstellen der Vertrauensstellung verwendeten Exchange-Server ein digitales Zertifikat installiert sein. Es empfiehlt sich dringend, ein selbstsigniertes Zertifikat zu verwenden. Beim Verwenden des Assistenten **Verbundvertrauensstellung aktivieren** in der Exchange-Verwaltungskonsole (EAC) wird automatisch ein selbstsigniertes Zertifikat erstellt und installiert.

Wenn Sie das empfohlene selbstsignierte Zertifikat nicht verwenden möchten, sollten Sie ein X.509 SSL-Zertifikat (Secure Sockets Layer) von einer Zertifizierungsstelle anfordern und installieren, die Microsoft als vertrauenswürdig einstuft. Wenngleich von anderen Zertifizierungsstellen ausgestellte Zertifikate zum Erstellen einer Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem verwendet werden können, wurden diese Zertifikate bisher nicht von Microsoft zertifiziert.

In der folgenden Tabelle werden die von Microsoft gegenwärtig als vertrauenswürdig eingestuften Zertifizierungsstellen aufgeführt. Diese Zertifizierungsstellen wurden für die Verwendung mit Exchange 2013 getestet.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Anzeigename der Zertifizierungsstelle</th>
<th>Ausgestellt von</th>
<th>Beabsichtigte Zwecke</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Autoridade Certificadora Raiz Brasileira</p></td>
<td><p>Autoridade Certificadora Raiz Brasileira</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Comodo</p></td>
<td><p>Comodo Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>CyberTrust</p></td>
<td><p>Baltimore CyberTrust Root-Zertifizierungsstelle</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Digicert</p></td>
<td><p>Digicert Global Root Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>Digicert High Assurance EV</p></td>
<td><p>Digicert Global Root Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Entrust</p></td>
<td><p>Entrust.net Secure Server Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>Entrust (2048)</p></td>
<td><p>Entrust.net Secure Server Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Equifax</p></td>
<td><p>Equifax Secure Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>GlobalSign</p></td>
<td><p>GlobalSign Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Go Daddy</p></td>
<td><p>Go Daddy Class 2 Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>Network Solutions</p></td>
<td><p>Network Solutions Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>PositiveSSL</p></td>
<td><p>Comodo Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>SECOM</p></td>
<td><p>SECOM Trust Systems-Zertifizierungsstelle</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>UTN-UserFirst-Hardware</p></td>
<td><p>Comodo Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>VeriSign</p></td>
<td><p>Class 3 Public Primary Certification Authority</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>VeriSign</p></td>
<td><p>VeriSign Trust Network</p></td>
<td><p>Serverauthentifizierung, Clientauthentifizierung</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Zertifikatanforderungen für den Verbund finden Sie unter [Verbund](federation-exchange-2013-help.md).

