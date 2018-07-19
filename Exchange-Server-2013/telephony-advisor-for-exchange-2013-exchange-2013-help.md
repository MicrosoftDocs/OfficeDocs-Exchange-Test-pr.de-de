---
title: 'Telefonieratgeber für Exchange 2013: Exchange Online Help'
TOCTitle: Telefonieratgeber für Exchange 2013
ms:assetid: e9f760f2-5901-4ed2-95a5-724555cc700e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364753(v=EXCHG.150)
ms:contentKeyID: 50554936
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Telefonieratgeber für Exchange 2013

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-07-25_

Unified Messaging (UM) erfordert die Integration von Microsoft Exchange mit dem vorhandenen Telefoniesystem Ihrer Organisation. Für eine erfolgreiche Bereitstellung und die Durchführung der richtigen Planungsschritte für die Bereitstellung von Unified Messaging ist eine sorgfältige Analyse Ihrer vorhandenen Telefonieinfrastruktur erforderlich.

Für Exchange-Administratoren, die wenig oder gar keine Erfahrung mit einem Telefonienetzwerk haben, kann die Planungsphase eine große Herausforderung darstellen. Informationen zur Bewältigung dieser Herausforderung finden Sie weiter unten in diesem Thema unter Resources to Help with Your UM Deployment.

Um die für Unified Messaging unterstützten VoIP-Gateways anzuzeigen, um festzustellen, ob Ihre Nebenstellenanlage die Verwendung eines bestimmten VoIP-Gatewaymodells oder -herstellers unterstützt, um zu ermitteln, ob Ihre IP-Nebenstellenanlage die Verwendung einer direkten SIP-Verbindung unterstützt, oder um die unterstützten Session Border Controller (SBCs) für Exchange Online UM anzuzeigen, klicken Sie auf einen der folgenden Links:

  - Supported VoIP gateways

  - Supported PBXs when using an AudioCodes VoIP gateway

  - Supported PBXs when using a dialogic VoIP gateway
    
      - PBXs supported when using a DMG1000 series Media Gateway
    
      - PBXs supported when using a DMG 2000 series Media Gateway
    
      - PBXs supported when using a DMG3000 series Media Gateway

  - Supported IP PBXs

  - Supported IP PBXs when using SIP media gateways

  - Exchange Unified Messaging, Office Communications Server 2007 R2, and Microsoft Lync Server

## Hilferessourcen für die UM-Bereitstellung

Das Erstellen von Richtlinien für die Bereitstellung von Telefonienetzwerken stellt eine Herausforderung dar. Da diese Netzwerke VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen mit unterschiedlichen Konfigurationseinstellungen und Anforderungen oder unterschiedlicher Firmware umfassen können, sind große Unterschiede möglich. Es sind jedoch zahlreiche Ressourcen verfügbar, die Ihnen bei einer erfolgreichen Bereitstellung von Unified Messaging behilflich sein können:

  - **Unified Messaging-Spezialisten**   UM-Spezialisten sind Systemintegratoren, die eine technische Schulung zu Exchange Unified Messaging absolviert haben, die vom Exchange-Technikteam durchgeführt wurde. Um einen problemlosen Übergang von Legacy-Voicemailsystemen zu Unified Messaging zu gewährleisten, empfiehlt Microsoft allen Kunden, sich an einen UM-Spezialisten zu wenden. Kontaktinformationen finden Sie unter [Microsoft Exchange Server 2013 Unified Messaging (UM) Specialists](https://go.microsoft.com/fwlink/p/?linkid=262708) oder [Microsoft Pinpoint for Unified Messaging](https://go.microsoft.com/fwlink/p/?linkid=261951).

  - **Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen**   Diese Konfigurationshinweise enthalten Einstellungen und andere nützliche Informationen für die Konfiguration von VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen für die Kommunikation mit Unified Messaging-Servern in Ihrem Netzwerk. Weitere Informationen finden Sie unter [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md).

  - **Konfigurationshinweise für unterstützte SBCs (Session Border Controllers)**   In diesen Konfigurationshinweisen finden Sie Einstellungen und weitere Informationen, die bei der Konfiguration von SBCs (Session Border Controllers) für die Kommunikation mit Unified Messaging-Servern in Hybrid- und Exchange Online-UM-Bereitstellungen hilfreich sein können. Weitere Informationen finden Sie unter [Konfigurationshinweise für unterstützte Session Border Controller](configuration-notes-for-supported-session-border-controllers-exchange-2013-help.md).
    

    > [!NOTE]
    > Exchange Online UM Unterstützung für Drittanbieter-Nebenstellenanlage Systeme über direkte Verbindungen von Kunden betrieben SBCs werden im Juli 2018 beendet. Finden Sie in der Exchange-Teamblog <A href="https://blogs.technet.microsoft.com/exchange/2017/07/18/discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/">die Einstellung der Unterstützung für Session Border Controller in Exchange Online unified messaging</A> Weitere Informationen.



Bevor Sie einen Unified Messaging-Spezialisten engagieren, sollten Sie in der Lage sein, die wichtigsten Fragen zu beantworten, die dieser Ihnen stellen wird. Wenn Sie die Antworten auf die folgenden Fragen kennen, wird dies die Produktivität Ihrer Unterhaltung mit dem UM-Spezialisten steigern.

  - Wie viele Telefon- bzw. Voicemailbenutzer befinden sich bereits in Ihrer Organisation?

  - Für wie viele Benutzer möchten Sie Unified Messaging bereitstellen?

  - Welche Nebenstellenanlagen (PBX) sollen für die Integration mit Unified Messaging verwendet werden?

  - Über wie viele PBX-Anlagen verfügt Ihre Organisation? Geben Sie hierbei auch die Anbieter, Typenbezeichnungen (leitungsvermittelt oder IP-basiert), Modellbezeichnungen und Firmwareversionen an.

  - Sind die PBX-Anlagen vernetzt, und sind sie zentralisiert, oder befinden sie sich an mehreren Orten?

  - Welche Voicemailsysteme werden zurzeit in Ihrer Organisation verwendet? Geben Sie hierbei auch die Anbieter, Typenbezeichnungen, Modellbezeichnungen und Firmwareversionen an.

  - Wie sind die Voicemailsysteme in Ihre PBX-Anlagen integriert (Analog, T1/E1, PRI, Digital Set Emulation, VoIP oder anders)?

  - Verwenden Sie zurzeit Sprachnetzwerke?

  - Welche Typen von Faxsystemen werden in Ihrer Organisation verwendet, und unterstützen die Faxsysteme eingehendes Faxrouting an Exchange?

  - Verwendet Ihre Organisation automatische Telefonzentralen?

  - Benötigen Sie Unterstützung für reine Telefonbenutzer, d. h. Benutzer die keinen E-Mail-Zugriff haben?

## Unterstützte VoIP-Gateways

Für die Integration von Unified Messaging mit Nebenstellenanlagen ist der Einsatz von mindestens einem VoIP-Gateway erforderlich, um die von TDM-basierten Nebenstellenanlagen verwendeten leitungsvermittelten Protokolle in IP-basierte, paketvermittelte Protokolle zu übersetzen, die von Unified Messaging verwendet werden. Es wurden Anbieter mit mehreren Modellen von VoIP-Gateways getestet, die für Unified Messaging unterstützt werden.

Das Testen der Interoperabilität von Unified Messaging mit VoIP-Gateways, IP-Nebenstellenanlagen und SBCs wurde in das Microsoft Unified Communications Open Interoperability Program integriert. Weitere Informationen hierzu finden Sie unter [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkid=140722).

Das Qualifizierungsprogramm für IP-Gateways, IP-Nebenstellenanlagen und erweiterte VoIP-Gateways gemäß dem [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkid=140722) gewährleistet Kunden eine nahtlose Setup- und Unterstützungserfahrung, wenn sie qualifizierte VoIP-Telefoniegateways und IP-Nebenstellenanlagen mit Microsoft Unified Communications-Software verwenden. Nur Produkte, die strenge und umfassende Testanforderungen erfüllen und die Spezifikationen und Testpläne einhalten, erhalten die Qualifizierung.

Einzelheiten zum Konfigurieren von unterstützten VoIP-Gateways, IP-Nebenstellenanlagen, Nebenstellenanlagen und SBCs finden Sie in den folgenden Ressourcen:

  - [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md)

  - [Konfigurationshinweise für unterstützte Session Border Controller](configuration-notes-for-supported-session-border-controllers-exchange-2013-help.md)

Interoperabilität wurde für die folgenden Anbieter von VoIP-Gateways bestätigt:

  - AudioCodes

  - Dialogic

  - In der folgenden Tabelle sind der VoIP-Gatewayanbieter, das IP-Gatewaymodell und die von jedem Modell unterstützten Protokolle aufgeführt.

### Unterstützte VoIP-Gateways für Unified Messaging

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Anbieter</th>
<th>Modell</th>
<th>Unterstützte Protokolle</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioCodes</p></td>
<td><p>MediaPack 114/8 FXO</p></td>
<td><ul>
<li><p>Analog mit In-Band oder DTMF</p></li>
<li><p>Analog mit SMDI</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><ul>
<li><p>Analog mit In-Band oder DTMF</p></li>
<li><p>Analog mit SMDI</p></li>
<li><p>BRI Q.SIG</p></li>
<li><p>T1/E1 Q.SIG</p></li>
<li><p>IP-zu-IP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><ul>
<li><p>T1/E1 CAS</p></li>
<li><p>T1/E1 Q.SIG</p></li>
<li><p>IP-zu-IP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Dialogic</p></td>
<td><p>DMG1000PBXDNIW</p></td>
<td><p>Digital Set Emulation</p></td>
</tr>
<tr class="odd">
<td><p>Dialogic</p></td>
<td><p>DMG1000LSW</p></td>
<td><ul>
<li><p>Analog mit In-Band oder DTMF</p></li>
<li><p>Analog mit SMDI</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Dialogic</p></td>
<td><p>DMG2000</p></td>
<td><ul>
<li><p>T1 CAS</p></li>
<li><p>T1/E1 Q.SIG</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><ul>
<li><p>BRI Q.SIG</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>NET</p></td>
<td><p>VX1200</p></td>
<td><ul>
<li><p>T1 Q.SIG</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Sonus</p></td>
<td><p>SBC 1000/2000 2.2.1 oder höher</p></td>
<td><ul>
<li><p>TDM-Signal (ISDN): AT&amp;T 4ESS/5ESS, Nortel DMS- 100, Euro ISDN (ETSI 300-102), QSIG, NTT InsNet (Japan), ANSI National ISDN-2 (NI-2)</p></li>
<li><p>TDM-Signal (CAS): T1 CAS (E&amp;M, Loop-Start); E1 CAS (R2)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Quintum</p></td>
<td><p>Tenor DX-Reihe</p></td>
<td><ul>
<li><p>T1 Q.SIG</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Unterstützte Nebenstellenanlagen bei Verwendung eines VoIP-Gateways von AudioCodes

In der folgenden Tabelle sind die Nebenstellenanlagen aufgeführt, die für die Verwendung mit VoIP-Gateways von AudioCodes unterstützt werden, einschließlich der Modelle MediaPack-114 FXO, MediaPack-118 FXO und Mediant 2000.

### Mit einem VoIP-Gateway von AudioCodes unterstützte Nebenstellenanlagen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>AudioCodes-Modell &quot;x&quot; – nach Bedarf durch 4 oder 8 ersetzen &quot;y&quot;- nach Bedarf durch 1, 2, 4, 8 oder 16 ersetzen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Alcatel</p></td>
<td><p>OmniPCX 4400</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Aastra</p></td>
<td><p>M1000, M2000</p></td>
<td><ul>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Definity G3</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Magix/Merlin</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>S8300</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>S8700</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>IP Office</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Cisco</p></td>
<td><p>CallManager 4.x</p></td>
<td><ul>
<li><p>Mediant1000/IP-zu-IP</p></li>
<li><p>Mediant2000/IP-zu-IP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>NEC</p></td>
<td><p>Electra Elite</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>NEAX2400</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP/RS232</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>NeXspan</p></td>
<td><p>S</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>Communication Server-1000M, 1000S, 1000E</p></td>
<td><ul>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Meridian 11c, 51c, 61c, 81c</p></td>
<td><ul>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Panasonic</p></td>
<td><p>KX-TES824, KX-TEA308</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Panasonic</p></td>
<td><p>KX-TDA30, KX-TDA100, KX-TDA200, KX-TDA600</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Shortel</p></td>
<td><p>IP-Telefoniesystem</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 150E</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 3550</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Tadiran Telecom</p></td>
<td><p>Coral Flexicom, Coral IPX</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Unterstützte Nebenstellenanlagen bei Verwendung eines VoIP-Gateways von Dialogic

Jedes VoIP-Gatewaymodell von Dialogic unterstützt verschiedene Nebenstellenanlagen. In den folgenden Tabellen sind die Hersteller und das Modell von Nebenstellenanlagen sowie das jeweils verwendbare VoIP-Gateway von Dialogic aufgeführt. Jedes VoIP-Gateway verwendet unterschiedliche Signalmethoden, -dichten und -protokolle.

## Unterstützte Nebenstellenanlagen bei Verwendung eines Mediengateways der DMG1000-Serie

In der folgenden Tabelle werden die PBX-Anlagen aufgeführt, die mit dem Mediengateway mit niedriger Dichte von Dialogic (DMG1000) unterstützt werden. Wenn aber ein analoger DMG1000 verwendet wird, ist ergänzende Signalgebung (RS232 SMDI, MD110, MCI-Protokolle oder In-Band-DTMF-Signalgebung) erforderlich.

### Für die Verwendung mit VoIP-Gateways der Dialogic DMG1000-Serie mit niedriger Dichte unterstützte Nebenstellenanlagen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>DMG-Modell und zusätzliche Signalgebung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra</p></td>
<td><p>Aastra MD110 (früher Ericsson MD110)</p></td>
<td><p>DMG1008LSW</p>
<p>Analogverbindung unter Verwendung des MD110 RS232-Protokolls</p></td>
</tr>
<tr class="even">
<td><p>Alcatel</p></td>
<td><p>Omni PCX 4400</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Definity G3 S8100, S8300, S8700 und S8710 (Communications Mgr SW V2.0 oder höher)</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Intercom</p></td>
<td><p></p></td>
<td><p>DMG1008LSW</p>
<p>Analogverbindung unter Verwendung des seriellen SMDI-Protokolls</p></td>
</tr>
<tr class="odd">
<td><p>Mitel</p></td>
<td><p>SX-200D, SX-200 Light, SX-2000 Light, SX-2000 S, SX-2000 VS, SX-200 ICP</p></td>
<td><p>DMG1008MTLDNIW</p></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>2000, 2400, 2400 IPX</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Meridian 1 - Option 11, 21, 21A, 51, 61, 71 und 81</p>
<p>Meridian SL1 - Generic X11, Version 15 oder höher</p>
<p>Nortel Communication Server - 1000M, 1000S, 1000E mit V3.0 oder höher</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>SL 100</p></td>
<td><p>DMG1008LSW</p>
<p>Analogverbindung unter Verwendung des seriellen SMDI-Protokolls</p></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 300E CS</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiCom 300E (Europa)</p></td>
<td><p>DMG1008LSW</p>
<p>Analogverbindung unter Verwendung der In-Band-DTMF-Signalgebung</p></td>
</tr>
<tr class="odd">
<td><p>Siemens/ROLM</p></td>
<td><p>8000 (SW-Version 80003 oder höher)<br />
9000 (alle Versionen)</p>
<p>9751 (alle Versionen von SW-Version 9005)</p>
<p>9751 (SW-Version 9006.4 oder höher)</p></td>
<td><p>DMG1008RLMDNIW</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="odd">
<td><p>Toshiba</p></td>
<td><p>CTX (SW-Version AR1ME021.00)</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="even">
<td><p>Sonstige</p></td>
<td><p>Verschiedene</p></td>
<td><p>DMG1008LSW</p>
<p>Analogverbindung unter Verwendung von entweder In-Band-DTMF oder SMDI</p></td>
</tr>
</tbody>
</table>


## Unterstützte Nebenstellenanlagen bei Verwendung eines Mediengateways der DMG2000-Serie

In der folgenden Tabelle werden die PBX-Anlagen aufgeführt, die mit dem T1/E1-Mediengateway von Dialogic (DMG2000) unterstützt werden. Das DMG2000-Gateway, das es in den Dichteausführungen Single-Span (DMG2030DTIQ), Dual-Span (DMG2060DTIQ) und Quad-Span (DMG2120DTIQ) gibt, unterstützt folgende Protokolle:

  - T1 CAS

  - T1 Q.SIG

  - E1 Q.SIG

  - T1 NI-2

  - T1 5ESS

  - T1 DMS100

Wenn CAS-Signalgebung (Channel Associated Signaling) verwendet wird, ist ergänzende Signalgebung (RS232 SMDI, MD110, MCI-Protokolle oder In-Band-DTMF-Signalgebung) erforderlich. Wenn Q.SIG-Signalgebung verwendet wird, muss die Nebenstellenanlage die Ergänzungsdienste unterstützen, die mit Informationen über den anrufenden und angerufenen Teilnehmer in Verbindung stehen, sowie die Anrufvermittlungsfunktionen, die für Unified Messaging erforderlich sind.

### Mit dem DMG2000-Mediengateway unterstützte PBX-Anlagen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>Erforderliche Softwareversion</th>
<th>Protokoll und zusätzliche Signalgebung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Alcatel</p></td>
<td><p>Omni PCX 4400</p></td>
<td><p>Version 3.2.712.5</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Definity G3</p></td>
<td><p>Version 3 oder höher</p></td>
<td><p>T1 CAS</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>S8500</p></td>
<td><p>Manager SW V2.0 oder höher</p></td>
<td><p>T1 CAS</p>
<p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Ericsson</p></td>
<td><p>MD110</p></td>
<td><p>Version MX1 TSW R2A (BC13)</p></td>
<td><p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Intercom</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>CAS (mit seriellem SMDI-Protokoll)</p></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>2400 IMX</p></td>
<td><p>Release 5200 Dez. 92 1b oder nachfolgende Versionen</p></td>
<td><p>CAS (mit seriellem MCI-Protokoll)</p></td>
</tr>
<tr class="odd">
<td><p>NEC</p></td>
<td><p>2400 IPX</p></td>
<td><p>R17 Version 03.46.001</p></td>
<td><p>T1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>Meridian 1 - Option 11</p></td>
<td><p>Release 15 oder nachfolgende Versionen und Optionen 19 und 46 sind erforderlich</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Communication Server 1000</p></td>
<td><p>Version 2121, Release 4</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiCom 300E CS</p></td>
<td><p>Version 9006.4 oder höher (Hinweis: Nur nordamerikanische Software)</p></td>
<td><p>T1 CAS</p></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>V2 SMR 9 SMPO</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Mitel</p></td>
<td><p>SX-2000 S, SX-2000 VS</p></td>
<td><p>LW 34</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Mitel</p></td>
<td><p>3300</p></td>
<td><p>Version 5.1.4.8</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
</tbody>
</table>


## Unterstützte Nebenstellenanlagen bei Verwendung eines Mediengateways der DMG4008BRI-Serie

Die Mediengateways der DMG4000-Serie bieten mehrere TDM-Schnittstellenoptionen. DMG4008BRI unterstützt 4-Port/8-Kanaldichten und unterstützt die folgenden Protokolle:

  - ISDN BRI Q.SIG

  - ETSI-DSS1 (Euro ISDN)

  - NET 3 (Belgien)

  - VN3 (Frankreich)

  - 1TR6 (Deutschland)

  - INS-64 (Japan)

  - 5ESS Custom (Nordamerika - AT\&T)

  - National ISDN (NI1 - Nordamerika)

In der folgenden Tabelle werden die PBX-Anlagen aufgeführt, die für die Verwendung mit einem Mediengateway der Dialogic 4000-Serie (DMG4008) unterstützt werden.

### Unterstützte PBX-Anlagen bei Verwendung eines Mediengateways der DMG4008BR-Serie

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>Erforderliche Softwareversion</th>
<th>Protokoll und zusätzliche Signalgebung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 300</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI-Q.SIG (ECMAV2)</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>S.0 B4400</p></td>
<td><p>BRI-Q.SIG (ECMAV2)</p></td>
</tr>
</tbody>
</table>


## Unterstützte IP-PBX-Anlagen

IP-Nebenstellenanlagen werden ebenfalls von Unified Messaging unterstützt. In der folgenden Tabelle werden die IP-Nebenstellenanlagen aufgeführt, die für die Verwendung einer direkten SIP-Verbindung mit Unified Messaging unterstützt werden.

### Für die Verwendung einer direkten SIP-Verbindung unterstützte IP-Nebenstellenanlagen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>Erforderliche Softwareversion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra</p></td>
<td><p>MX-ONE</p></td>
<td><p>4.0</p></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Aura</p></td>
<td><p>5.2.1 mit Servicepack 5 (SP5)</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Communication Server 2100</p></td>
<td><p>CS2100 SE13</p></td>
</tr>
<tr class="even">
<td><p>Cisco</p></td>
<td><p>Call Manager, Unified Communications Manager</p></td>
<td><p>5.1, 6.x, 7.0 and8.0</p></td>
</tr>
</tbody>
</table>


## Für die Verwendung von SIP-Mediengateways unterstützte IP-Nebenstellenanlagen

IP-Nebenstellenanlagen, die SIP-Mediengateways verwenden, werden ebenfalls von Unified Messaging unterstützt. In der folgenden Tabelle sind die IP-Nebenstellenanlagen aufgeführt, die für die Verwendung von IP-zu-IP-Funktionen von SIP-Mediengateways zum Herstellen einer Verbindung mit Unified Messaging unterstützt werden.

### Für die Verwendung von SIP-Mediengateways unterstützte IP-Nebenstellenanlagen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>PBX-Hersteller</th>
<th>PBX-Modell/-Typ</th>
<th>SIP-Gatewaymodell</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cisco</p></td>
<td><p>Call Manager 4.x</p></td>
<td><p>AudioCodes Mediant 1000/2000 (IP-zu-IP-fähig)</p></td>
</tr>
</tbody>
</table>


## Exchange Unified Messaging, Office Communications Server 2007 R2 und Microsoft Lync Server

Bei lokalen und Hybridbereitstellungen kann Exchange Unified Messaging zusammen mit Microsoft Office Communications Server 2007 R2, Microsoft Lync Server 2010 oder Lync Server 2013 bereitgestellt werden, um Benutzern in Ihrer Organisation Sprachnachrichten, Chatfunktionen, erweiterte Anwesenheitsinformationen, Audio-/Videokonferenzen sowie integrierte E-Mail- und Messagingfunktionen zur Verfügung zu stellen. Weitere Informationen finden Sie unter:

  - [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md)

  - [Microsoft Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=202010)

Weitere Informationen zum Microsoft Unified Communications Open Interoperability Program für Unternehmenstelefonieinfrastrukturen, einschließlich einer Auflistung der qualifizierten SIP-Festnetzgateways und IP-Nebenstellenanlagen sowie einer Beschreibung des Prozesses zur Teilnahme an diesem Programm für Telefonieinfrastrukturanbieter finden Sie unter [Microsoft Unified Communications Open Interoperability Program](https://go.microsoft.com/fwlink/p/?linkid=132071).

