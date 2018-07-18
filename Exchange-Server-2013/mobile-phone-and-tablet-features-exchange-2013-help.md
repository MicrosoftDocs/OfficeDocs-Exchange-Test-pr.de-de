---
title: 'Mobiltelefon- und Tabletfunktionen: Exchange 2013 Help'
TOCTitle: Mobiltelefon- und Tabletfunktionen
ms:assetid: ad54d9e6-7a1c-4fb0-b5a9-0b042b98ada3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232162(v=EXCHG.150)
ms:contentKeyID: 50554893
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Mobiltelefon- und Tabletfunktionen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Benutzer können über Microsoft Exchange ActiveSync auf Mobiltelefonen, Tablets und anderen tragbaren Geräten auf ihre E-Mail-, Kalender-, Kontakt- und Aufgabeninformationen zugreifen. Sie können mithilfe von ActiveSync auch ihre Signatur und automatische Antworten einrichten. Eine Vielzahl von Mobiltelefonen und -geräten unterstützt Exchange ActiveSync.


> [!NOTE]
> Wir beziehen uns zwar auf Geräte, die als Mobiltelefone auf Exchange Server&nbsp;2013 zugreifen, es gibt jedoch auch viele Geräte, die auf Exchange 2013 zugreifen können, aber nicht über die Funktionalität eines Mobiltelefons verfügen. In dieser Dokumentation wird der Begriff "Mobiltelefon" auch für diese Geräte verwendet.



## Mit Exchange ActiveSync kompatible Geräte

Benutzer können die von Exchange ActiveSync gebotenen umfassenden Funktionen nutzen, indem sie Mobiltelefone auswählen, die mit Exchange ActiveSync kompatibel sind. Diese Mobiltelefone sind bei vielen Herstellern und Telefongesellschaften erhältlich. Weitere Informationen hierzu finden Sie in der Dokumentation zum jeweiligen Mobiltelefon.

Die folgenden Mobiltelefone sind mit Microsoft Exchange kompatibel:

  - **Apple** Apple iPhone, iPod Touch und iPad unterstützen Exchange ActiveSync.

  - **Windows Phone**   Exchange ActiveSync wird von Windows Phone 8, Windows Phone 7 und früheren Versionen unterstützt.

  - **Android**   Viele Mobiltelefone und Tablets mit Android-Betriebssystem unterstützen Exchange ActiveSync. Diese mobilen Geräte unterstützen jedoch ggf. nicht alle verfügbaren Postfachrichtlinien für mobile Geräte. Weitere Informationen finden Sie unter [Postfachrichtlinien für mobile Geräte](mobile-device-mailbox-policies-exchange-2013-help.md).

## Windows Phone-Softwarefunktionen

Mobiltelefone mit einer Version der Windows Phone-Software als Betriebssystem bieten für die Synchronisierung mit Exchange 2013 den größten Funktionsumfang. In der folgenden Tabelle sind die Postfachrichtlinien für mobile Geräte aufgeführt, die für Windows Phone 8 und Windows Phone 7 verfügbar sind.

### Funktionen von Windows Phone 7 und 8

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Betriebssystem</th>
<th>Funktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Phone 8</p></td>
<td><p>Windows Phone 8 unterstützt die folgenden Postfachrichtlinien für mobile Geräte:</p>
<ul>
<li><p>Einfaches Kennwort zulassen</p></li>
<li><p>Alphanumerisches Kennwort erforderlich</p></li>
<li><p>Gerätekennwort aktiviert</p></li>
<li><p>Ablauf des Gerätekennworts</p></li>
<li><p>IRM aktiviert</p></li>
<li><p>Maximale Anzahl fehlerhafter Eingaben des Gerätekennworts</p></li>
<li><p>Zeitsperre für maximale Geräteinaktivität</p></li>
<li><p>Mindestanzahl komplexer Zeichen im Gerätekennwort</p></li>
<li><p>Minimale Gerätekennwortlänge</p></li>
<li><p>Geräteverschlüsselung anfordern</p></li>
<li><p>Remotezurücksetzung</p></li>
</ul>

> [!WARNING]
> Wenn Ihre Organisation andere Einstellungen für die Postfachrichtlinien von Mobilgeräten verwendet, müssen Sie die Richtlinie <STRONG>Nicht bereitstellbare Geräte zulassen</STRONG> auf "true" fest. Dies kann Auswirkungen auf die Sicherheit Ihrer Organisation haben, da anderen Mobiltelefonen und -geräten, die nicht alle Anforderungen Ihrer Richtlinieneinstellungen für Mobilgeräte erfüllen, die Synchronisierung erlaubt wird. Weitere Informationen finden Sie unter <A href="mobile-device-mailbox-policies-exchange-2013-help.md">Postfachrichtlinien für mobile Geräte</A>.


</td>
</tr>
<tr class="even">
<td><p>Windows Phone 7</p></td>
<td><p>Mobiltelefone mit Windows Phone 7 unterstützen die Einstellungen von Exchange ActiveSync-Postfachrichtlinien nur teilweise.</p>
<ul>
<li><p>Kennwort erforderlich</p></li>
<li><p>Minimale Kennwortlänge</p></li>
<li><p>Zeitsperre für maximale Inaktivität</p></li>
<li><p>Maximale Anzahl fehlerhafter Eingaben des Gerätekennworts</p></li>
<li><p>Einfaches Kennwort zulassen</p></li>
<li><p>Kennwortablauf</p></li>
<li><p>Kennwortverlauf</p></li>
<li><p>Wechselmedien deaktivieren</p></li>
<li><p>IrDA deaktivieren</p></li>
<li><p>Desktopsynchronisierung deaktivieren</p></li>
<li><p>Remotedesktop blockieren</p></li>
<li><p>Gemeinsame Nutzung der Internetverbindung blockieren</p></li>
</ul></td>
</tr>
</tbody>
</table>

