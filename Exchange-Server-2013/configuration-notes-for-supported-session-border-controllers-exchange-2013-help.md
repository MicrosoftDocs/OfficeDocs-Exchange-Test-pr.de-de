---
title: 'Konfigurationshinweise für unterstützte Session Border Controller'
TOCTitle: Konfigurationshinweise für unterstützte Session Border Controller
ms:assetid: d161f94a-a243-4294-93b3-2bf1dc17b59f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673565(v=EXCHG.150)
ms:contentKeyID: 50554914
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurationshinweise für unterstützte Session Border Controller

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-07-25_

Session Border Controller (SBCs) ermöglichen das Verbinden Ihres lokalen Telefonienetzwerks mit einem Microsoft-Datencenter über eine dedizierte öffentliche WAN-Verbindung. Ein SBC befindet sich am Rand Ihres lokalen IP-Netzwerks und verbindet sich mit einem zweiten SBC in einem Microsoft-Datencenter.

Für SBCs müssen digitale Zertifikate verwendet werden, um den gesamten Datenverkehr zwischen der lokalen Organisation und dem Microsoft-Datencenter zu verschlüsseln. Sie müssen ein digitales Zertifikat für das Netzwerkrandelement (z. B. Session Border Controller) beziehen, das Sie für die Kommunikation mit Hybrid- und Onlinebereitstellungen von Exchange verwenden. Digitale Zertifikate stellten eine Vertrauensstellung zwischen der lokalen Organisation und dem Microsoft-Datencenter her und ermöglichen gegenseitige Transport Layer Security (Mutual TLS oder MTLS). Nachdem diese Vertrauensstellung hergestellt wurde, tauschen die Netzwerkrandelemente in der lokalen Organisation und im Microsoft-Datencenter Sitzungsschlüssel aus, die dann zum Verschlüsseln des nachfolgenden Datenverkehrs verwendet werden.

Bei Hybrid- oder Onlinebereitstellungen stellt das UM-IP-Gateway einen SBC dar. Der allgemeine Antragstellername im Zertifikat muss mit dem FQDN-Wert im Adressfeld des UM-IP-Gateways übereinstimmen, das Sie erstellen. Wenn Sie beispielsweise die FQDN-Adresse "sbcexternal.contoso.com" für Ihr UM-IP-Gateway angeben, stellen Sie sicher, dass der Antragstellername und der alternative Antragstellername im Zertifikat denselben Wert enthalten: sbcexternal.contoso.com. Beim verwendeten Namen wird Groß-/Kleinschreibung unterschieden, sodass Sie sich vergewissern müssen, dass die Schreibung von Zertifikat und UM-IP-Gateway identisch ist. Wenn Sie einen Acme Packet SBC verwenden und der allgemeine Name nicht mit dem FQDN des UM-IP-Gateways übereinstimmt, wird der Aufruf mit dem Fehler 403 zurückgewiesen.


> [!NOTE]
> Da SBCs sich am Rand des Netzwerks befinden, fungieren sie außerdem als Firewall. Wenn Sie einen SBC hinter der Firewall Ihrer Organisation einrichten, kann er Konfigurationsprobleme verursachen. Zudem wird er für die Verbindung zu Office 365 nicht unterstützt.



## Unterstützte Session Border Controller

Die folgenden SBCs wurden erfolgreich auf Interoperabilität mit Hybrid- und Onlinebereitstellungen von Exchange getestet. Beachten Sie, dass die Funktionen und Kompatibilitäten von SBCs variieren können. Auch deren Einrichtung kann abhängig von anderen Geräten in Ihrem Netzwerk anders sein. Wenden Sie sich an den SBC-Hersteller, um herauszufinden, ob es spezielle Konfigurationshinweise für Unified Messaging in einer Hybrid- und Onlinebereitstellung gibt.


> [!NOTE]
> Exchange Online UM Unterstützung für Drittanbieter-Nebenstellenanlage Systeme über direkte Verbindungen von Kunden betrieben SBCs werden im Juli 2018 beendet. Finden Sie in der Exchange-Teamblog <A href="https://blogs.technet.microsoft.com/exchange/2017/07/18/discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/">die Einstellung der Unterstützung für Session Border Controller in Exchange Online unified messaging</A> Weitere Informationen.




<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Anbieter</strong></p></td>
<td><p><strong>Modell</strong></p></td>
<td><p><strong>Konfigurationshinweise</strong></p></td>
<td><p><strong>Anmerkungen</strong></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.acmepacket.com">Acme Packet</a></p></td>
<td><p>Net-Net 3820 oder 4500</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>Dedizierter SBC</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://www.audiocodes.com">AudioCodes</a></p></td>
<td><p>Mediant 1000 MSBG</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>Dedizierter SBC</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.audiocodes.com">AudioCodes</a></p></td>
<td><p>Mediant 1000 MSBG</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>SBC und IP-Gateway</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://www.cisco.com/c/dam/en/us/solutions/collateral/enterprise-networks/unified-access/cube-asr-release-10-0.pdf">Cisco</a></p></td>
<td><p>ASR 1000</p>

> [!NOTE]
> IOS 15.4(3)S3 oder höher muss installiert sein.


</td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>Dedizierter SBC</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.ingate.com/">Ingate</a></p></td>
<td><p>SIParator</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>Dedizierter SBC</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.net.com">NET</a></p></td>
<td><p>VX1200 &amp; VX1800</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>SBC-Option für ein VoIP-Gatewayprodukt</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.sonus.net/">Sonus</a></p></td>
<td><p>SBC 1000/2000 2.2.1 oder höher</p></td>
<td><p><strong>Wenden Sie sich in Bezug auf aktuelle Anweisungen und hinsichtlich der Einrichtung des Geräts an den Hardwarehersteller.</strong></p></td>
<td><p>Dedizierter SBC</p></td>
</tr>
</tbody>
</table>

