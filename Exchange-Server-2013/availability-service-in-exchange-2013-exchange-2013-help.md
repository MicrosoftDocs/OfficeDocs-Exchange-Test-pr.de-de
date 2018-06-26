---
title: 'Verfügbarkeitsdienst in Exchange 2013: Exchange 2013 Help'
TOCTitle: Verfügbarkeitsdienst in Exchange 2013
ms:assetid: 9722dea2-2bf8-437c-85c0-3ab65b8a07b9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232134(v=EXCHG.150)
ms:contentKeyID: 52062899
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verfügbarkeitsdienst in Exchange 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Exchange 2013-Verfügbarkeitsdienst wird verwendet, um Microsoft Outlook- und Outlook Web App-Clients Frei/Gebucht-Informationen zur Verfügung zu stellen. Der Verfügbarkeitsdienst verbessert die Benutzererfahrung der Information-Worker bei Kalenderfunktionen und bei der Besprechungsplanung, indem sichere, konsistente und aktuelle Frei/Gebucht-Informationen zur Verfügung gestellt werden.

Outlook und Outlook Web App verwenden den Verfügbarkeitsdienst zur Durchführung der folgenden Aufgaben:

  - Abrufen aktueller Frei/Gebucht-Informationen für Exchange 2013-Postfächer

  - Abrufen aktueller Frei/Gebucht-Informationen aus anderen Exchange 2013-Organisationen

  - Abrufen veröffentlichter Frei/Gebucht-Informationen aus öffentlichen Ordnern für Postfächer auf Servern mit vorherigen Versionen von Exchange

  - Anzeigen der Geschäftszeiten des Teilnehmers

  - Anzeigen von Vorschlägen zum Besprechungstermin

**Inhalt**

Übersicht über den Verfügbarkeitsdienst

Informationen zum Status "Abwesend"

Verfügbarkeitsdienst-API

Netzwerklastenausgleich des Verfügbarkeitsdiensts

Methoden zum Abrufen von Frei/Gebucht-Informationen

## Übersicht über den Verfügbarkeitsdienst

Der Verfügbarkeitsdienst ruft für Benutzer mit Exchange 2013, Exchange 2010 und Exchange 2007 Frei/Gebucht-Informationen direkt aus dem Zielpostfach ab und kann so konfiguriert werden, dass Frei/Gebucht-Informationen für Benutzer von Vorgängerversionen von Exchange abgerufen werden. Für Topologien mit Exchange 2007-, Exchange 2010- oder Exchange 2013-Postfächern, in denen alle Clients Outlook 2007 oder höher ausführen, wird der Verfügbarkeitsdienst zum Abrufen der Frei/Gebucht-Informationen verwendet.

Outlook verwendet den Exchange-AutoErmittlungsdienst zum Abrufen der URL des Verfügbarkeitsdiensts. Weitere Informationen zum AutoErmittlungsdienst finden Sie unter [AutoErmittlungsdienst](autodiscover-service-for-exchange-2013.md).

Sie können den Verfügbarkeitsdienst über die Exchange-Verwaltungsshell konfigurieren. Die Exchange-Verwaltungskonsole kann nicht zum Konfigurieren des Verfügbarkeitsdiensts verwendet werden.

## Informationen zum Status "Abwesend"

Der Verfügbarkeitsdienst bietet auch den Zugriff auf automatische Antwortnachrichten, die von Benutzern gesendet werden, wenn sie abwesend oder für einen längeren Zeitraum unterwegs sind.

Information-Worker verwenden die Funktion "Automatische Antworten" (früher als Abwesenheitsfunktion bekannt) in Outlook und Outlook Web App, um andere Benutzer darüber zu informieren, dass sie zurzeit keine E-Mail-Nachrichten beantworten können. Mithilfe dieser Funktion können automatische Antworten sowohl für Information-Worker als auch für Administratoren einfacher eingerichtet und verwaltet werden.

## Verfügbarkeitsdienst-API

Der Verfügbarkeitsdienst ist Teil der Exchange 2013-Programmierschnittstelle. Er steht als Webdienst zur Verfügung, mit dem Entwickler Drittanbietertools für Integrationszwecke entwickeln können.

## Netzwerklastenausgleich des Verfügbarkeitsdiensts

Mithilfe des Netzwerklastenausgleichs auf Ihren Clientzugriffsservern, die den Verfügbarkeitsdienst ausführen, können Sie die Leistung und Zuverlässigkeit für Ihre Benutzer steigern, die auf Frei/Gebucht-Informationen angewiesen sind. Outlook erkennt die URL des Verfügbarkeitsdiensts mithilfe des AutoErmittlungsdiensts. Damit Sie den Netzwerklastenausgleich zusammen mit dem Verfügbarkeitsdienst verwenden können, müssen Sie Änderungen an der Konfiguration vornehmen.

Die interne URL wird vom Intranet aus und die externe URL vom Internet aus verwendet. Wenn Sie die gleiche URL sowohl für den internen als auch für den externen Datenverkehr verwenden möchten, müssen Sie sicherstellen, dass das DNS (Domain Name System) für die Weiterleitung des internen Datenverkehrs direkt zur internen URL ordnungsgemäß konfiguriert ist. Vergewissern Sie sich außerdem, dass auf die URL sowohl intern als auch extern ordnungsgemäß zugegriffen werden kann. Für das ordnungsgemäße Funktionieren des AutoErmittlungs- und Verfügbarkeitsdiensts muss DNS so konfiguriert werden, dass "mail.\<*Domänenname*\>.com" und "autodiscover.mail.\<*Domänenname*\>.com" auf Ihre Lastenausgleichslösung verweisen, wobei \<*Domänenname*\> den Namen Ihrer Domäne angibt.


> [!NOTE]
> Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=45959">Netzwerklastenausgleich – Technische Referenz</A> und <A href="https://go.microsoft.com/fwlink/p/?linkid=49315">Cluster für den Netzwerklastenausgleich</A>. Sie können auch nach Websites von Drittanbietern suchen, die Software für den Netzwerklastenausgleich anbieten.



## Methoden zum Abrufen von Frei/Gebucht-Informationen

In den folgenden Tabellen sind die verschiedenen Methoden zum Abrufen der Frei/Gebucht-Informationen aus unterschiedlichen Topologien mit einer einzelnen Gesamtstruktur aufgeführt.


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
<th>Frei/Gebucht-Informationen abrufendes Postfach ist aktiv</th>
<th>Zielpostfach ist aktiv</th>
<th>Frei/Gebucht-Abrufmethode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013</p></td>
<td><p>Exchange 2013, Exchange 2010 oder Exchange 2007</p></td>
<td><p>Exchange 2013, Exchange 2010 oder Exchange 2007</p></td>
<td><p>Der Verfügbarkeitsdienst liest die Frei/Gebucht-Informationen aus dem Zielpostfach.</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2007</p></td>
<td><p>Exchange 2013, Exchange 2010 oder Exchange 2007</p></td>
<td><p>Exchange 2010 oder Exchange 2007</p></td>
<td><p>Der Verfügbarkeitsdienst liest die Frei/Gebucht-Informationen aus dem Zielpostfach.</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p>Exchange 2010 oder Exchange 2007</p></td>
<td><p>Exchange 2003</p></td>
<td><p>Der Verfügbarkeitsdienst stellt HTTP-Verbindungen zum virtuellen Verzeichnis <strong>/public</strong> des Exchange 2003-Postfachs her.</p></td>
</tr>
<tr class="even">
<td><p>Outlook Web App</p></td>
<td><p>Exchange 2013, Exchange 2010 oder Exchange 2007</p></td>
<td><p>Exchange 2013, Exchange 2010 oder Exchange 2007</p></td>
<td><p>Outlook Web App in Exchange 2010 oder Outlook Web Access in Exchange 2007 rufen die Verfügbarkeitsdienst-API auf, die die Frei/Gebucht-Informationen aus dem Zielpostfach liest.</p></td>
</tr>
</tbody>
</table>

