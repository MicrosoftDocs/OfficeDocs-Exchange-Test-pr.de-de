---
title: 'Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen: Exchange 2013 Help'
TOCTitle: Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen
ms:assetid: 1583674f-5a57-45fd-8125-087d1624e686
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee681657(v=EXCHG.150)
ms:contentKeyID: 50554782
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Auf dieser Seite finden Sie Links zu Konfigurationshinweisen, die von Microsoft oder einem Partner für VoIP-Gateways erstellt und getestet wurden. Wenn Microsoft oder ein Partner Unified Messaging mit einem neuen VoIP-Gateway und einer Konfiguration aus Nebenstellenanlage oder IP-Nebenstellenanlage bereitstellt, werden die Voraussetzungen und Konfigurationseinstellungen dokumentiert. Diese Informationen werden zum Erstellen von Konfigurationshinweisen verwendet.

Jeder Konfigurationshinweis für Nebenstellenanlagen enthält Informationen darüber, wie Unified Messaging mit einer bestimmten Telefoniekonfiguration bereitgestellt wird, einschließlich Hersteller, Modell und Firmwareversion für die VoIP-Gateways, IP-Nebenstellenanlagen oder Nebenstellenanlagen. Darüber hinaus enthält jeder Konfigurationshinweis für PBX-Anlagen weitere Informationen, z. B.:

  - Beteiligte Autoren des Konfigurationshinweises.

  - Detaillierte Voraussetzungen, einschließlich der folgenden:
    
      - Funktionen, die in der PBX-Anlage aktiviert bzw. deaktiviert werden müssen.
    
      - Spezielle Hardware, die installiert werden muss.
    
      - Ob ein VoIP-Gateway erforderlich ist.
    
      - Funktionen, über die das VoIP-Gateway verfügen muss, falls eines erforderlich ist.
    
      - Spezielle Verkabelungs-/Anschlussanforderungen zwischen IP-Gateway und PBX-Anlage.
    
      - Eine Liste der Unified Messaging-Funktionen, die mit einer vorgegebenen Telefoniekonfiguration möglicherweise nicht verfügbar sind.

Weitere Informationen zum Microsoft Unified Communications Open Interoperability Program für Telefonieinfrastrukturen in Unternehmen, einschließlich einer Liste qualifizierter SIP-PSTN-Gateways und IP-Nebenstellenanlagen, sowie zum Registrierungsprozess für Telefonieinfrastrukturanbieter, die an diesem Programm teilnehmen möchten, finden Sie unter [Microsoft Unified Communications Open Interoperability Program](https://go.microsoft.com/fwlink/p/?linkid=132071).

## Konfigurationshinweise für VoIP-Gateways, IP-PBX- und PBX-Anlagen

Microsoft arbeitet mit den Partnern für VoIP-Gateways AudioCodes und Dialogic zusammen, um die Liste von getesteten Nebenstellenanlagen zu erweitern. Da zurzeit zahlreiche Kombinationen von Telefoniekomponenten getestet werden, wird dieses Thema regelmäßig aktualisiert. Überprüfen Sie wiederholt diese Seite, wenn Sie den erforderlichen Konfigurationshinweis für Ihre Bereitstellung nicht finden können.

Folgende Konfigurationshinweise sind verfügbar:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Aastra</p></li>
<li><p>Alcatel</p></li>
<li><p>Avaya</p></li>
<li><p>Cisco</p></li>
<li><p>Inter-Tel</p></li>
<li><p>Intecom</p></li>
<li><p>Mitel</p></li>
<li><p>NEC</p></li>
</ul></td>
<td><ul>
<li><p>NeXspan</p></li>
<li><p>Nortel</p></li>
<li><p>Panasonic</p></li>
<li><p>Rolm</p></li>
<li><p>ShoreTel</p></li>
<li><p>Siemens</p></li>
<li><p>Sonus</p></li>
<li><p>Tadiran</p></li>
<li><p>Toshiba</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Aastra


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra MD110 (früher Ericsson MD110)</p></td>
<td><p>MX1 TSW R2A (alternative Bezeichnung: BC13)</p></td>
<td><p>Analog – Seriell MD110</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Aastra MD110 (früher Ericsson MD110)</p></td>
<td><p>MX1 TSW R2A (alternative Bezeichnung: BC13)</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Aastra MX-ONE</p></td>
<td><p>4.0</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Aastra</p></td>
<td><p><a href="http://www.aastra.com/cps/rde/aareddownload?file_id=4384-14746-_p06_xml%26dsproject=aastra%26mtype=pdf">Download</a></p></td>
</tr>
</tbody>
</table>


## Alcatel


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OmniPCX 4400</p></td>
<td><p>R4.2-d2.304-4-h-il-c6s2</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Avaya


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aura</p></td>
<td><p>Communication Manager 5.2.1 mit SP 5</p>
<p>Session Manager 5.2.</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Avaya</p></td>
<td><p><a href="https://support.avaya.com/downloads/">Download</a></p></td>
</tr>
<tr class="even">
<td><p>CS 2100</p></td>
<td><p>CS 2100 SE13</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Avaya</p></td>
<td><p><a href="https://support.avaya.com/css/p8/documents/100149819">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R009i.05.122.4</p></td>
<td><p>Digital Set Emulation (DNI7434)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Merlin Magix</p></td>
<td><p>Version 1.5 v.6.0</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>S8300</p></td>
<td><p>G3xV11 Communication Manager 1.3</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>S8300</p></td>
<td><p>R013x.01.2.632.1</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>S8300</p></td>
<td><p>R013x.01.2.632.1</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>S8700</p></td>
<td><p>R011x.02.0.110.4</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Cisco


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cisco Call Manager 4.x</p></td>
<td><p>4.x</p></td>
<td><p>IP-zu-IP</p></td>
<td><p>AudioCodes</p></td>
<td><p>AudioCodes</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Cisco Call Manager 5.1</p></td>
<td><p>5.1.0.9921-12</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Microsoft</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=225083">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Cisco Unified Communications Manager 6.0 und 6.1</p></td>
<td><p>6.x</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Microsoft</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=225083">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Cisco Unified Communications Manager 7.0</p></td>
<td><p>7.0.2.20000-5</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Microsoft</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=196361">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Cisco Unified Communications Manager 8.0</p></td>
<td><p>8.0.3.20000-5</p></td>
<td><p>Direkte SIP-Verbindung</p></td>
<td><p>K.A.</p></td>
<td><p>K.A.</p></td>
<td><p>Microsoft</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=213007">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Inter-Tel


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5000</p></td>
<td><p>Inter-Tel 5000 v2.1</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Axxess</p></td>
<td><p>Axxess V9.0</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Intecom


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PointSpan M6880</p></td>
<td><p>40PS3.5.K.2</p></td>
<td><p>T1 CAS - SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Mitel


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>3300</p></td>
<td><p>5.1.4.8</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>3300</p></td>
<td><p>5.1.4.8</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>SX2000</p></td>
<td><p>5.0.24</p></td>
<td><p>Digital Set Emulation (DNISS430)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008MTLDNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>3300</p></td>
<td><p>7</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## NEC


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Electra Elite 192</p></td>
<td><p>SP034V4.5</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IMX</p></td>
<td><p>Version 7400</p></td>
<td><p>T1 CAS - Seriell MCI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>NEAX2400IMX &amp; IPX</p></td>
<td><p>Version 7400</p></td>
<td><p>Digital Set Emulation (DNIDtermIII)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IPX</p></td>
<td><p>Ver. R18.06.24.000</p></td>
<td><p>T1 CAS – Seriell MCI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>NEAX2400IPX</p></td>
<td><p>Ver. R18.06.24.000</p></td>
<td><p>Analog – Seriell MCI</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IPX</p></td>
<td><p>Ver.17 Rel.03.46.001</p></td>
<td><p>T1 Q.SIG – Seriell MCI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## NeXspan


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>L</p></td>
<td><p>RMS1 Version R1.3 E1TA</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Nortel


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CS1000</p></td>
<td><p>3.0 &amp; 4.5</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Meridian 81C</p></td>
<td><p>4.5</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Meridian 81C</p></td>
<td><p>4.5</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Option11c</p></td>
<td><p>Version 25</p></td>
<td><p>Digital Set Emulation (DNI2616)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Option11c</p></td>
<td><p>Version 25</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Option11c</p></td>
<td><p>Version 25</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>CS-1000M (Nachfolger)</p></td>
<td><p>Version 25.40</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Panasonic


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>KX-TDA200</p></td>
<td><p>001-001</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>KX-TDA200</p></td>
<td><p>3</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>KX-TES824</p></td>
<td><p>2.0.2</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Rolm


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>9751</p></td>
<td><p>9005</p></td>
<td><p>Digital Set Emulation (DNIRP400)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008RLMDNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## ShoreTel


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IP-Telefoniesystem</p></td>
<td><p>6.1</p></td>
<td><p>Analog – SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>IP-Telefoniesystem</p></td>
<td><p>7.5</p></td>
<td><p>Analog – SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Siemens


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HiCom 150E</p></td>
<td><p>Vers. 2.2</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>HiCom 300</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI QSIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>HiCom 300</p></td>
<td><p>9006.4SMR3</p></td>
<td><p>Digital Set Emulation (DNIOptiset)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>HiCom 300</p></td>
<td><p>9006.4SMR3</p></td>
<td><p>T1 CAS – In-Band-DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 3550</p></td>
<td><p>Vers. 3</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Ver 3.0 SMR5 SMP4</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 4000</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI QSIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Ver 3.0 SMR5 SMP4</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 4000</p></td>
<td><p>Version 2.0 SMR9 SMP0</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Version 2.0 SMR9 SMP0</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Sonus


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>VoIP-Gatewaymodell</th>
<th>VoIP-Gatewaysoftwareversion</th>
<th>Unterstützte Protokolle</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SBC 1000/2000</p></td>
<td><p>2.2.1 oder höher</p></td>
<td><ul>
<li><p>TDM-Signal (ISDN): AT&amp;T 4ESS/5ESS, Nortel DMS- 100, Euro ISDN (ETSI 300-102), QSIG, NTT InsNet (Japan), ANSI National ISDN-2 (NI-2)</p></li>
<li><p>TDM-Signal (CAS): T1 CAS (E&amp;M, Loop-Start); E1 CAS (R2)</p></li>
</ul></td>
<td><p>Sonus</p></td>
<td><p><a href="http://www.sonus.net/sites/default/files/sonussbc1k2kconfigo365.pdf">Download</a></p></td>
</tr>
</tbody>
</table>


## Tadiran


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP 11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>BRI QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant</p>
<p>1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>BRI QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 CAS – In-Band-DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant</p>
<p>1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Herunterladen</a></p></td>
</tr>
</tbody>
</table>


## Toshiba


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
<th>PBX-Modell</th>
<th>PBX-Softwareversion</th>
<th>Protokoll</th>
<th>Gatewayanbieter</th>
<th>Gatewaymodell</th>
<th>Konfigurationsautor</th>
<th>Konfigurationsdateidownload</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CTX</p></td>
<td><p>AR1ME021.00</p></td>
<td><p>Analog – SMDI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
<tr class="even">
<td><p>CTX</p></td>
<td><p>AR1ME021.00</p></td>
<td><p>Analog – In-Band-DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Herunterladen</a></p></td>
</tr>
</tbody>
</table>

