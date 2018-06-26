---
title: 'Exchange Server Supportability Matrix: Exchange 2013 Help'
TOCTitle: Exchange Server Supportability Matrix
ms:assetid: dbac2d40-da8b-469f-a265-1d1f948fe446
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff728623(v=EXCHG.150)
ms:contentKeyID: 54652708
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange Server Supportability Matrix

 

_**Gilt für:**Exchange Server 2007, Exchange Server 2010, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2018-03-20_

Die Exchange Server-Unterstützbarkeitsmatrix stellt für Microsoft Exchange-Administratoren eine zentrale Quelle mit Informationen zur Unterstützung bereit, die für beliebige Konfigurationen oder eine erforderliche Komponente für unterstützte Versionen von Microsoft Exchange verfügbar ist.

## Veröffentlichungsmodell

In der folgenden Tabelle ist das Veröffentlichungsmodell für jede unterstützte Version von Exchange angegeben. Das Veröffentlichungsmodell ist durch ein x gekennzeichnet.

Für Exchange-Versionen vor Exchange 2013 ist jedes Updaterollup-Paket kumulativ hinsichtlich des Gesamtprodukts. Wenn Sie ein Updaterollup-Paket auf Exchange Server 2010 anwenden, wenden Sie daher alle Hotfixes an, die im betreffenden Updaterollup-Paket enthalten sind. Dies schließt alle Hotfixes ein, die in den einzelnen früheren Updaterolluppaketen enthalten waren. Wenn ein Update oder Hotfix für frühere Versionen von Exchange erstellt wird, ist mindestens eine der im Update oder Hotfix enthaltene Binärdateien kumulativ. Dies bedeutet, dass sie kumulativ hinsichtlich des Inhalts der Dateien sind. Im Hinblick auf das Exchange-Gesamtprodukt sind sie jedoch nicht kumulativ. Weitere Informationen finden Sie unter [Exchange 2010-Unterstützung](https://go.microsoft.com/fwlink/p/?linkid=298627).

Mit Exchange 2013 wurde eine neue Art der Übermittlung von Hotfixes und Service Packs eingeführt. Während Hotfixes und Updaterollups in früheren Versionen von Exchange nach Priorität veröffentlicht wurden, kommt in Exchange 2013 und neueren Versionen nun ein Modell der geplanten Übermittlung zur Anwendung. In diesem Modell werden alle drei Monate kumulative Updates veröffentlicht. Kumulative Updates (KU) für Exchange 2013 und neuer werden als vollständige Aktualisierung von dieser Version von Exchange veröffentlicht, ähnlich einem Produktupdate oder einer Service Pack-Version. Weitere Informationen zum neuen Unterstützungsmodell finden Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Serviceveröffentlichungsmodell</th>
<th>Exchange 2016</th>
<th>Exchange 2013</th>
<th>Exchange 2010</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kumulative Updates</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Updaterollups</p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Sicherheits-Hotfixes separat geliefert</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


## Support-Lebenszyklus

Weitere Informationen zum Supportlebenszyklus für eine bestimmte Version von Exchange oder die MicrosoftWindows-Server- oder Clientbetriebssysteme finden Sie auf der Seite [Microsoft Support Lifecycle](https://go.microsoft.com/fwlink/p/?linkid=55839). Weitere Informationen über den Microsoft-Supportlebenszyklus finden Sie unter [Microsoft Support Lifecycle-Richtlinie - Häufig gestellte Fragen (FAQ)](https://go.microsoft.com/fwlink/p/?linkid=158902).

## Exchange Server 2007 – Ende der Lebensdauer

Der Support für Exchange 2007 endete nach der [Microsoft Lifecycle-Richtlinie](https://go.microsoft.com/fwlink/p/?linkid=833210) am 11. April 2017. Zur Erinnerung: Nach diesem Datum werden keine neuen Sicherheitsupdates, Nicht-Sicherheitsupdates, kostenlose oder kostenpflichtige Supportunterstützung oder Onlineupdates von technischen Inhalten mehr bereitgestellt. Darüber hinaus werden aufgrund der immer schnelleren Übernahme von Office 365 und der wachsenden Nutzung der Cloud keine benutzerdefinierten Supportoptionen für Office-Produkte zur Verfügung stehen. Dazu gehören Exchange Server sowie die Office Suites, SharePoint Server, Office Communications Server, Lync Server, Skype for Business Server, Project Server und Visio. Angesichts des Supportendes für Exchange 2007 empfehlen wir unseren Kunden, ihre Migrations- und Upgradepläne abzuschließen. Wir empfehlen Kunden, die Bereitstellungsvorteile zu nutzen, die von Microsoft und Microsoft Certified Partners bereitgestellt werden, wie z. B. [Microsoft FastTrack](https://go.microsoft.com/fwlink/p/?linkid=238431) für Cloudmigrationen und [Software Assurance Planning Services](https://go.microsoft.com/fwlink/p/?linkid=833211) für lokale Upgrades.

## Unterstützte Betriebssysteme

In der folgenden Tabelle sind die Betriebssystemplattformen aufgeführt, auf denen jede Version von Exchange ausgeführt werden kann. Unterstützte Plattformen sind durch ein X gekennzeichnet.


> [!IMPORTANT]
> Versionen von Windows Server und Windows-Client, die nicht in der folgenden Tabelle aufgeführt werden, werden für die Verwendung mit einer Version oder einem Release von Exchange nicht unterstützt.




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
<th>Betriebssystemplattform</th>
<th>Exchange 2016 CU3 oder neuer</th>
<th>Exchange 2016 CU2 oder älter</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista SP2</p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X1</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 SP2</p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 R2 SP1</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows 7 SP1</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
</tr>
<tr class="odd">
<td><p>Windows 8</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
</tr>
<tr class="even">
<td><p>Windows 8.1</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Windows 10</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012 R2</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2016</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


1Nur für Exchange-Verwaltungstools

## Unterstützte Active Directory-Umgebungen

In der folgenden Tabelle sind die Active Directory-Umgebungen aufgeführt, mit denen jede Version von Exchange kommunizieren kann. Unterstützte Umgebungen sind durch ein X gekennzeichnet. Ein Active Directory-Server bezieht sich sowohl auf schreibbare globale Katalogserver als auch auf schreibbare Domänencontroller. Schreibgeschützte globale Katalogserver und Read-only-Domänencontroller werden nicht unterstützt.


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
<th>Betriebssystemumgebung</th>
<th>Exchange 2016 CU3 oder neuer</th>
<th>Exchange 2016 CU2 oder älter</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3 RU5 oder höher</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Server 2003 SP2, Active Directory-Server</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 SP2, Active Directory-Server</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 R2 SP1, Active Directory-Server</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012 Active Directory-Server</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012 R2 Active Directory-Server</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2016 Active Directory-Server</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>



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
<th>Gesamtstrukturfunktionsebene</th>
<th>Exchange 2016 CU3 oder neuer</th>
<th>Exchange 2016 CU2 oder älter</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3 RU5 oder höher</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Server 2003-Gesamtstrukturfunktionsebene</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008-Gesamtstrukturfunktionsebene</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 R2 SP1-Gesamtstrukturfunktionsebene</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012-Gesamtstrukturfunktionsebene</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012 R2-Gesamtstrukturfunktionsebene</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2016-Gesamtstrukturfunktionsebene</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Für die Verwendung mit der Premium-Version von Outlook Web App oder Outlook im Web unterstützte Webbrowser

Die folgende Tabelle enthält die für die Verwendung mit der Premium-Version von Outlook Web App oder Outlook im Web unterstützte Webbrowser. Unterstützte Browser sind mit einem „X“ gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Browser</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Edge</p></td>
<td><p>Aktuelle Version von Microsoft Edge</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer</p></td>
<td><p>Aktuelle oder unmittelbar vorhergehende Version von Internet Explorer</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 11</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 10</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 9</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 8</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 7</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Firefox</p></td>
<td><p>Aktuelle oder unmittelbar vorhergehende Version von Firefox</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="odd">
<td><p>Firefox 3.0.1 oder höher</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Firefox 12 oder höher</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Safari</p></td>
<td><p>Aktuelle Version von Safari</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="even">
<td><p>Safari 3,1 oder höher</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Safari 5.0 oder höher</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Chrome</p></td>
<td><p>Aktuelle Version von Chrome</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="odd">
<td><p>Chrome 3.0.195 oder höher</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Chrome 18 oder höher</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


## Für die Verwendung mit der Basisversion von Outlook Web App oder Outlook im Web unterstützte Webbrowser

Die folgende Tabelle enthält die für die Verwendung mit der Light-Version (Basic) von Outlook Web App oder Outlook im Web unterstützte Webbrowser. Unterstützte Browser sind mit einem „X“ gekennzeichnet.


> [!NOTE]
> Outlook Web App Basic (Outlook Web App Light) wird für die Verwendung in mobilen Browsern unterstützt. Wenn bei einem mobilen Browser jedoch Probleme beim Rendering oder der Authentifizierung auftreten, können Sie mithilfe von Outlook Web App Light im vollständigen Client eines unterstützten Browsers ermitteln, ob das Problem reproduziert werden kann. Testen Sie beispielsweise die Verwendung von Outlook Web App Light in Safari, Chrome oder Internet Explorer. Wenn das Problem nicht im vollständigen Client reproduziert werden kann, wird empfohlen, den Anbieter des mobilen Geräts zu kontaktieren. In diesen Fällen arbeiten wir dementsprechend mit dem Anbieter zusammen.




<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Browser</th>
<th>Exchange 2016</th>
<th>Exchange 2013</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Edge</p></td>
<td><p>Aktuelle Version von Microsoft Edge</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer</p></td>
<td><p>Aktuelle oder unmittelbar vorhergehende Version von Internet Explorer</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 11</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 10</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 9</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X<span></span></p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 8</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 7</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Safari</p></td>
<td><p>Aktuelle Version von Safari</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Firefox</p></td>
<td><p>Aktuelle oder unmittelbar vorhergehende Version von Firefox</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Chrome</p></td>
<td><p>Aktuelle Version von Chrome</p></td>
<td><p>k. A.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>Opera</p></td>
<td><p> </p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


## Für die Verwendung von S/MIME mit Outlook Web App oder Outlook im Web unterstützte Webbrowser

Die folgende Tabelle enthält die für die Verwendung von S/MIME mit Outlook Web App oder Outlook im Web unterstützte Webbrowser. Unterstützte Browser sind mit einem „X“ gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Browser</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Edge</p></td>
<td><p>Aktuelle Version von Microsoft Edge</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer</p></td>
<td><p>Aktuelle oder unmittelbar vorhergehende Version von Internet Explorer</p></td>
<td><p>k. A.</p></td>
<td><p>k. A.</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 11</p></td>
<td></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 10</p></td>
<td></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 9</p></td>
<td></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 8</p></td>
<td></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 7</p></td>
<td></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


## Clients

In der folgenden Tabelle sind die Postfachclients aufgeführt, die für die gemeinsame Verwendung mit jeder Version von Exchange unterstützt werden. Unterstützte Clients sind durch ein X gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p></p></td>
<td><p>X1</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2010</p></td>
<td><p>X4</p></td>
<td><p>X2</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2013</p></td>
<td><p>X4</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2016</p></td>
<td><p>X4</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Outlook für Mac für Office 365</p></td>
<td><p>X4</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Phone 7</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Phone 7.5</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Phone 8</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Windows Phone 8.1</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Mobile 10</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Entourage 2008 (EWS)</p></td>
<td><p>X3</p></td>
<td><p>X3</p></td>
<td><p>X3</p></td>
</tr>
</tbody>
</table>


1Erfordert Outlook 2007 Service Pack 3 und das neueste öffentliche Update.

2Erfordert Outlook 2010 Service Pack 1 und das neueste öffentliche Update.

3Nur EWS. DAV wird für Exchange 2010 nicht unterstützt.

4Mit dem neuesten Office Service Pack und neuesten öffentlichen Updates unterstützt.

## Tools

In der folgenden Tabelle sind die Versionen von Microsoft Exchange aufgeführt, die gemeinsam mit dem Microsoft Exchange-Tool für die organisationsübergreifende Replikation (Exscfg.exe; Exssrv.exe) verwendet werden können. Das Tool wird zum Replizieren der Informationen für Öffentliche Ordner (einschließlich Frei/Gebucht-Informationen) zwischen Exchange-Organisationen verwendet. Weitere Informationen finden Sie unter [Organisationsübergreifende Replikation in Microsoft Exchange Server](https://go.microsoft.com/fwlink/?linkid=22455). Unterstützte Versionen sind durch ein X gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Tool</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tool für die Replikation zwischen Organisationen</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


## Microsoft .NET Framework

Die folgende Tabelle gibt die Version von Microsoft.NET Framework an, die mit jeder Version von Exchange verwendet werden kann. Unterstützte Versionen sind durch ein X gekennzeichnet.


> [!IMPORTANT]
> <STRONG>Versionen von .NET Framework, die nicht in der folgenden Tabelle aufgeführt werden, werden in keiner Version und in keinem Release von Exchange unterstützt.</STRONG> Dies schließt kleinere und Patchreleases von .NET Framework ein.




> [!NOTE]
> Wenn Sie ein Upgrade von Exchange von einem nicht unterstützten KU auf das aktuelle KU durchführen und keine KUs dazwischen verfügbar sind, sollten Sie zunächst auf die neueste Version von .NET aktualisieren, die von Exchange unterstützt wird, und dann sofort ein Upgrade auf das aktuelle KU durchführen. Auch bei dieser Methode müssen Sie die Exchange-Server auf dem neuesten Stand halten und auf das neueste unterstützte KU aktualisieren.<BR>Microsoft erhebt keinen Anspruch, dass bei Verwendung dieser Methode kein Upgradefehler auftritt und Sie sich dann möglicherweise an den Support von Microsoft wenden müssen.




<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>.NET Framework</th>
<th>Exchange 2016 KU8</th>
<th>Exchange 2016 KU5–KU7</th>
<th>Exchange 2013 KU19</th>
<th>Exchange 2013 KU16–KU18</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.NET Framework 3.5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X1</p></td>
</tr>
<tr class="even">
<td><p>.NET Framework 3.5 SP1</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>.NET Framework 4.0</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X1,2</p></td>
</tr>
<tr class="even">
<td><p>.NET Framework 4.5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X1,2 </p></td>
</tr>
<tr class="odd">
<td><p>.NET Framework 4.6.2</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>.NET Framework 4.7.1</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


1Wenn Sie Windows Server 2012 verwenden, muss .NET Framework 3.5 installiert sein, bevor Sie Exchange 2010 SP3 verwenden können.

2Exchange 2010 verwendet nur die .NET.NET Framework 3.5 - und die .NET .NET Framework 3.5 SP1-Bibliotheken. Die .NET .NET Framework 4.5-Bibliotheken werden nicht verwendet, wenn sie auf dem Computer installiert sind. Die Installation einer Haupt- oder Nebenversion von .NET .NET Framework 4.5 (z. B. .NET .NET Framework 4.5.1, .NET .NET Framework 4.5.2 usw.) wird unterstützt, solange .NET .NET Framework 3.5 oder .NET .NET Framework 3.5 SP1 auch auf dem Computer installiert sind.

## Windows-Verwaltungsframework

In der folgenden Tabelle sind die Versionen des Windows Management Frameworks aufgeführt, welches die Windows PowerShell-Befehlszeilenschnittstelle enthält, die zusammen mit jeder Version von Exchange verwendet werden können. Unterstützte Versionen sind durch ein X gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows PowerShell</th>
<th>Exchange 2016</th>
<th>Exchange 2013</th>
<th>Exchange 2010</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows PowerShell 2.0</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Management Framework</p></td>
<td><p>Version von Windows Management Framework, die in die Windows Server-Version, auf der Sie Exchange installieren, integriert ist.</p></td>
<td><p>Version von Windows Management Framework, die in die Windows Server-Version, auf der Sie Exchange installieren, integriert ist.</p></td>
<td><p>Version von Windows Management Framework, die in die Windows Server-Version, auf der Sie Exchange installieren, integriert ist.1</p></td>
</tr>
</tbody>
</table>


1Windows Management Framework 3.0 und Windows Management Framework 4.0 kann zum Ausführen von betriebssystembezogenen Verwaltungsaufgaben auf einem Computer verwendet werden, auf dem Exchange 2010 SP3 RU5 oder höher ausgeführt wird. Exchange 2010-Cmdlets und Exchange 2010-Skripts erfordern jedoch Windows PowerShell 2.0. Die Verwendung von Exchange 2010-Cmdlets und -Skripts mit Windows Management Framework 3.0 oder Windows Management Framework 4.0 wird nicht unterstützt.

## Microsoft-Verwaltungskonsole

In der folgenden Tabelle sind die Versionen der Microsoft-Verwaltungskonsole aufgeführt, die gemeinsam mit jeder Version von Exchange verwendet werden können. Unterstützte Versionen sind durch ein X gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>MMC</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 oder höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MMC 3.0</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


## Windows Installer

Die folgende Tabelle gibt die Version von Windows Installer an, die mit jeder Version von Exchange verwendet werden kann. Unterstützte Versionen sind durch ein X gekennzeichnet.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows Installer</th>
<th>Exchange 2016</th>
<th>Exchange 2013 SP1 und höher</th>
<th>Exchange 2010 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Installer 4.5</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Windows Installer 5.0</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

