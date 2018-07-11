---
title: 'Lastenausgleich: Exchange 2013 Help'
TOCTitle: Lastenausgleich
ms:assetid: f572c193-6f3a-400e-9085-a9d3e5e18c59
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898588(v=EXCHG.150)
ms:contentKeyID: 51409369
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Lastenausgleich

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Über den Lastenausgleich können Sie verwalten, welche Ihrer Server Datenverkehr empfangen. Mithilfe von Lastenausgleich können eingehende Clientverbindungen auf verschiedene Endpunkte (z. B. Clientzugriffsserver) verteilt werden, um sicherzustellen, dass die Last an jedem Endpunkt gleich ist. Außerdem kann Lastenausgleich beim Ausfall eines oder mehrerer Endpunkte Failoverredundanz gewährleisten. Durch Verwendung von Lastenausgleich mit Exchange Server 2013 können Sie sicherstellen, dass Benutzern der Exchange-Dienst bei einem Computerausfall weiterhin zur Verfügung steht. Darüber hinaus kann die Bereitstellung durch Lastenausgleich mehr Datenverkehr abwickeln, als von einem Server verarbeitet werden kann, und zwar unter Verwendung eines einzelnen Hostnamens für die Clients.

Der Lastenausgleich erfüllt zwei Hauptaufgaben. Er verringert die Auswirkungen des Ausfalls eines Clientzugriffsservers an einem der Active Directory-Standorte. Außerdem wird durch Lastenausgleich sichergestellt, dass die Last auf den einzelnen Clientzugriffsservern gleichmäßig verteilt ist.

Exchange 2013 umfasst außerdem die folgenden Lösungen für Switchover- und Failoverredundanz:

  - **Hohe Verfügbarkeit** Mithilfe von DAGs (Database Availability Groups) werden von Exchange 2013 mehrere synchronisierte Kopien von Postfächern auf verschiedenen Servern beibehalten. Auf diese Weise können Benutzer bei einem Ausfall einer Postfachdatenbank auf einem Server eine Verbindung zu einer synchronisierten Kopie der Datenbank auf einem anderen Server herstellen.

  - **Ausfallsicherheit von Standorten** Sie können zwei Active Directory-Standorte an getrennten geografischen Orten bereitstellen, die Postfachdaten zwischen beiden synchronisieren und die gesamte Last von einem der Standorte übernehmen lassen, falls der andere ausfällt.

  - **Onlinepostfachverschiebungen** Bei einer Onlinepostfachverschiebung können Benutzer während der Verschiebung auf ihre E-Mail-Konten zugreifen. Die Konten der Benutzer werden nur für einen kurzen Zeitraum gegen Ende des Vorgangs, d. h. bei der abschließenden Synchronisierung, gesperrt. Sie können die Verschiebung von Onlinepostfächern gesamtstrukturübergreifend oder innerhalb derselben Gesamtstruktur durchführen.

  - **Shadow-Redundanz**   Durch Shadow-Redundanz wird die Verfügbarkeit und Wiederherstellbarkeit von Nachrichten während der Übertragung geschützt. Mit der Shadow-Redundanz wird das Löschen einer Nachricht aus den Transportdatenbanken verzögert, bis der Transportserver sichergestellt hat, dass die jeweilige Nachricht vollständig an alle nächsten Hops zugestellt wurde. Wenn einer der nächsten Hops einen Fehler verursacht, bevor eine erfolgreiche Zustellung gemeldet wird, wird die Nachricht erneut zur Zustellung an diesen Hop gesendet.

## Architekturänderungen am Lastenausgleich für Exchange Server 2013

In Exchange Server 2010 wurden Clientverbindungen und Verarbeitung von der Clientzugriffs-Serverrolle übernommen. Dies erforderte Lastenausgleich für externe und interne Outlook-Verbindungen sowie Mobilgerät- und Drittclientverbindungen auf dem gesamten Clientzugriffsserver-Array einer Bereitstellung, um Fehlertoleranz und eine effiziente Auslastung von Servern zu erzielen. Für viele Exchange 2010-Clientzugriffsprotokolle wurde Affinität vorausgesetzt – eine Beziehung zwischen dem Client und einem bestimmten Clientzugriffsserver. Insbesondere für Outlook Web App, Exchange-Systemsteuerung, Exchange-Webdienste, Outlook Anywhere, Outlook-TCP/IP-MAPI-Verbindungen, Exchange ActiveSync, Exchange-Adressbuchdienst und Remote PowerShell wurde Client-zu-Client-Zugriffsserveraffinität vorausgesetzt oder genutzt. Exchange 2010 umfasste u. a. folgende Lastenausgleichsoptionen:

  - Windows-Netzwerklastenausgleich mit Quell-IP-Affinität

  - Hardwarelastenausgleich

Aufgrund der verschiedenen Anforderungen für Clientprotokolle in Exchange 2010 wurde die Verwendung einer Layer 7-Lastenausgleichslösung empfohlen. Mit Layer 7, das auch als "Lastenausgleich auf Anwendungsebene" bekannt ist, konnte von der Lastenausgleichslösung anhand komplexer Regeln ermittelt werden, wie die einzelnen beim System eingehenden Anforderungen auszugleichen waren, sofern der Lastenausgleichslogik die gesamte Kommunikation zwischen Client und Server zur Verfügung stand. Durch diese komplexen Regeln wurde sichergestellt, dass alle Anforderungen von einem bestimmten Client an denselben Clientzugriffsserver-Endpunkt übermittelt wurden. Wenn in Exchange 2010 für Protokolle, für die Affinität vorausgesetzt wurde, nicht alle Anforderungen von einem bestimmten Client an denselben Endpunkt übermittelt wurden, wirkte sich dies negativ auf die Benutzerfreundlichkeit aus. Weitere Informationen zu Lastenausgleichsoptionen in Exchange 2010 finden Sie unter [Grundlegendes zum Lastenausgleich in Exchange 2010](https://go.microsoft.com/fwlink/p/?linkid=196447).

In Exchange Server 2013 stehen zwei primäre Servertypen zur Verfügung: Clientzugriffsserver und Postfachserver. Die Clientzugriffsserver in Exchange 2013 fungieren als statuslose Lightweight-Proxyserver, über die Clients eine Verbindung zu Exchange 2013-Postfachservern herstellen können. Exchange 2013-Clientzugriffsserver bieten einen einheitlichen Namespace und Authentifizierung. Darüber hinaus bieten Exchange 2013-Clientzugriffsserver Folgendes:

  - Unterstützung von Proxy- und Umleitungslogik für Clientprotokolle.

  - Unterstützung der Verwendung von Layer 4-Lastenausgleich.

Mit Sitzungsaffinität und Layer 7-Lastenausgleich werden alle Anforderungen zwischen Client und Server gemäß den Anforderungen verschiedener Protokolle an denselben Endpunkt gesendet. Anforderungen werden in der Anwendungsschicht verteilt. Mit Layer 4-Lastenausgleich werden die Anforderungen in der Transportschicht verteilt. Anforderungen vom Client werden von der Lastenausgleichslösung basierend auf einer einzelnen IP-Adresse (manchmal auch "virtuelle IP-Adresse" oder "VIP" genannt) an eine Gruppe von Servern verteilt und dort abgearbeitet. Die Verbindung zwischen Client und Server muss hergestellt werden, bevor der Inhalt der Anforderung ermittelt wird, damit vom Lastenausgleichsmodul vorher ein Server zum Empfang der Anforderung ausgewählt wird. Die Auswahl des Zielservers kann auf verschiedene Weise erfolgen, z. B. mit "Roundrobin", wobei jede eingehende Verbindung zum nächsten Server in einer Ringliste wechselt, oder mit "Least Connections", wobei jede neue Verbindung vom Lastenausgleichsmodul an den Server mit den derzeit wenigsten aktiven Verbindungen gesendet wird. Da keine Sitzungsaffinität mehr vorausgesetzt wird, ist die Lastenausgleichsarchitektur flexibler, bietet mehr Auswahl und ist weniger kompliziert. Lastenausgleich ohne Sitzungsaffinität gibt Ihnen die Möglichkeit, die Kapazität und Auslastung des Lastenausgleichsmoduls zu erhöhen, da bei der Verarbeitung keine stärker beteiligten Affinitätsoptionen wie cookiegestützter Lastenausgleich oder SSL-Sitzungs-ID (Secure Sockets Layer) beibehalten werden müssen.

## Clientzugriffsserver-Arrays und Exchange-2013

In Exchange 2010 wurde das Konzept eines Clientzugriffsarrays eingeführt. Nach der Konfiguration eines Clientzugriffsarrays für einen Active Directory-Standort wurden alle Clientzugriffsserver an dem Standort automatisch zu Mitgliedern des Arrays. In aktuellen Builds von Exchange 2013 ist keine Konfiguration eines Clientzugriffsarrays erforderlich, da die Bereitstellung eines hoch verfügbaren Diensts mit Lastenausgleich wesentlich einfacher ist.

## Lastenausgleichslösungen

Die Verwendung von Hardwarelastenausgleich wird für Exchange 2013 weiterhin unterstützt. Informationen zu Hardwarelastenausgleichs-Lösungen, bei denen das Testen der jeweiligen Lösung mit Exchange 2010 abgeschlossen ist und die aller Wahrscheinlichkeit nach gut mit Exchange 2013 funktionieren, finden Sie unter [Bereitstellung von Lastenausgleich für Exchange Server 2010](https://go.microsoft.com/fwlink/p/?linkid=261834). Beachten Sie, dass diese Seite die komplexere Layer-7-Konfiguration des Hardware-Lastenausgleichsmoduls mit Exchange 2010 darstellt. Der Lastenausgleich für den Exchange 2013-Datenverkehr lässt sich anhand der weiter oben in diesem Abschnitt behandelten architekturspezifischen Änderungen deutlich vereinfachen. Statt Sitzungsaffinität für jedes der Exchange-Protokolle zu konfigurieren, können eingehende Verbindungen zu Exchange 2013-Clientzugriffsservern vom Lastenausgleichsmodul ohne weitere erforderliche Affinitätsverarbeitung an einen verfügbaren Server umgeleitet werden. Der Hardwarelastenausgleich spielt bei der Bereitstellung der hohen Verfügbarkeit des Exchange-Diensts weiterhin eine wichtige Rolle, da mit seiner Hilfe nicht mehr verfügbare Clientzugriffsserver erkannt und aus der Gruppe der Server, die für die Verarbeitung eingehender Verbindungen zuständig sind, entfernt werden können.

## Windows-Netzwerklastenausgleich

Der Windows-Netzwerklastenausgleich ist der gängigste Softwarelastenausgleich für Exchange-Server. Es gibt einige Einschränkungen bei der Bereitstellung des Windows-Netzwerklastenausgleichs mit Microsoft Exchange.

  - Sie können den Windows-Netzwerklastenausgleich nicht auf Exchange-Servern verwenden, auf denen auch Postfach-DAGs verwendet werden, da der Windows-Netzwerklastenausgleich nicht mit Windows-Failoverclustering kompatibel ist. Wenn Sie eine Exchange 2013-DAG verwenden und den Windows-Netzwerklastenausgleich verwenden möchten, müssen Clientzugriffs-Serverrolle und Postfachserverrolle auf separaten Servern ausgeführt werden.

  - Der Windows-Netzwerklastenausgleich erkennt keine Dienstausfälle. Der Windows-Netzwerklastenausgleich erkennt Dienstausfälle nur anhand der IP-Adresse. Wenn also ein bestimmter Webdienst wie Outlook Web App ausfällt, der Server jedoch noch funktioniert, erkennt der Windows-Netzwerklastenausgleich den Ausfall nicht und leitet Anforderungen auch weiterhin an diesen Clientzugriffsserver weiter. Ein Benutzereingriff ist erforderlich, um den von dem Ausfall betroffenen Clientzugriffsserver aus dem Lastenausgleichspool zu entfernen.

  - Die Verwendung des Windows-Netzwerklastenausgleichs kann zur Überflutung von Ports und damit zur Überlastung von Netzwerken führen.

  - Da der Windows-Netzwerklastenausgleich die Clientaffinität mithilfe der Quell-IP-Adresse durchführt, ist diese Lösung bei einem kleinen Quell-IP-Pool nicht effektiv. Dies kann der Fall sein, wenn der Quell-IP-Pool aus dem Subnetz eines Remotenetzwerks stammt oder Ihre Organisation die Netzwerkadressenübersetzung verwendet.

