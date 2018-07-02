---
title: 'Planen der Verwendung von Active Directory-Standorten für das E-Mail-Routing: Exchange 2013 Help'
TOCTitle: Planen der Verwendung von Active Directory-Standorten für das E-Mail-Routing
ms:assetid: 0f697cee-bcaa-4c69-b80c-7a2afd1817d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996299(v=EXCHG.150)
ms:contentKeyID: 52062833
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Planen der Verwendung von Active Directory-Standorten für das E-Mail-Routing

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-05-21_

Microsoft Exchange Server 2013 erkennt Active Directory-Standorte und Database Availability Groups (DAGs) als Routinggrenzen. Exchange 2013 verwendet jedoch noch immer die Active Directory-Standorttopologie, um festzulegen, wie Nachrichten zwischen Exchange-Servern in verschiedenen DAGs oder Standorten innerhalb der Organisation übermittelt werden. Weitere Informationen finden Sie unter [E-Mail-Routing](mail-routing-exchange-2013-help.md).

Der Transportdienst auf einem Postfachserver stellt den Nachrichtentransport innerhalb der Exchange-Organisation bereit. Beim Bereitstellen einer reinen Exchange 2013-Organisation oder beim Aufnehmen von Exchange 2013 in eine reine Exchange Server 2010-Organisation ist keine weitere Konfiguration erforderlich, um Routing in der Gesamtstruktur einzurichten.

**Inhalt**

Verwendung der Active Directory-Standortmitgliedschaft durch Exchange 2013

Ermitteln der Active Directory-Standortmitgliedschaft

Übersicht der IP-Standortverknüpfungen

Platzierung von Exchange 2013-Servern an Active Directory-Standorten

## Verwendung der Active Directory-Standortmitgliedschaft durch Exchange 2013

Exchange 2013 ist eine standortaktivierte Anwendung. Standortaktivierte Anwendungen können ihre eigene Active Directory-Standortmitgliedschaft und die Standortmitgliedschaft anderer Server durch Abfragen von Active Directory bestimmen. Exchange 2013 bestimmt darüber hinaus anhand der Standortmitgliedschaft, welche Domänencontroller und globalen Katalogserver für die Verarbeitung von Active Directory-Abfragen verwendet werden sollen. Wenn darüber hinaus ein Server mit Exchange die Active Directory-Standortmitgliedschaft eines anderen Exchange-Servers bestimmen muss, kann er über eine Active Directory-Abfrage den Standortnamen abrufen.

In Exchange 2013 ist der Microsoft Exchange Active Directory-Topologiedienst für das Aktualisieren des Standortattributs des Exchange-Serverobjekts zuständig. Da es sich bei der Active Directory-Standortmitgliedschaft um ein Attribut des Serverobjekts handelt, muss Exchange nicht DNS abfragen, um eine Serveradresse zu einem Subnetz aufzulösen, das einem Active Directory-Standort zugeordnet ist. Durch Stempeln des Active Directory-Standortattributs auf ein Exchange-Serverobjekt kann die Active Directory-Standortmitgliedschaft einem Server zugewiesen werden, der nicht Mitglied der Domäne ist, wie etwa einem abonnierten Edge-Transport-Server.

Die Exchange 2013-Server verwenden Informationen zur Active Directory-Standortmitgliedschaft in folgender Weise:

  - **E-Mail-Übermittlung**   Der Postfachtransport-Übermittlungsdienst auf einem Exchange 2013-Postfachserver verwendet Informationen zur Active Directory-Standortmitgliedschaft zum Ermitteln der übrigen Exchange 2013-Postfachserver, die sich an demselben Active Directory-Standort befinden. Wenn der Quellpostfachserver keiner DAG angehört oder wenn die DAG sich nicht über mehrere Active Directory-Standorte erstreckt, übermittelt der Postfachtransport-Übermittlungsdienst auf dem Quellpostfachserver Nachrichten für Routing und Transport an den Transportdienst auf einem Exchange 2013-Postfachserver an demselben Active Directory-Standort.

  - **E-Mail-Zustellung**   Der Transportdienst auf einem Exchange 2013-Postfachserver führt die Empfängerauflösung durch und fragt Active Directory ab, um eine E-Mail-Adresse einem Empfängerkonto zuzuordnen. Die Empfängerkontoinformationen beinhalten den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) der Postfachdatenbank des Benutzers. Der Transportdienst fragt Active Directory ab, um den Active Directory-Standort der Postfachdatenbank des Benutzers zu ermitteln. Wenn die Postfachdatenbank keiner DAG angehört, wird die Nachricht an den jeweiligen Postfachserver zugestellt. Andernfalls wird die Nachricht an einen anderen Postfachserver am Standort des Ziel-Postfachservers zur Zustellung weitergeleitet.

  - **Nachrichtenrouting**   Der Transportdienst auf Exchange 2013-Postfachservern ruft Informationen aus Active Directory ab, um zu ermitteln, wie E-Mail innerhalb der Organisation geroutet werden soll. Exchange 2013 ermittelt mithilfe des Konzepts der *Verteilergruppen*, wohin und wie Nachrichten zu routen sind. Abhängig vom Ziel kann die Nachricht an den Transportdienst oder den Postfachtransport-Zustellungsdienst auf einem Exchange 2013-Postfachserver oder an einen Hub-Transport-Server geroutet werden, auf dem eine frühere Exchange-Version ausgeführt wird. Weitere Informationen finden Sie unter [E-Mail-Routing](mail-routing-exchange-2013-help.md).

  - **Unified Messaging-Nachrichtenübermittlung**   Der Unified Messaging-Dienst auf Exchange 2013-Postfachservern verwendet Informationen zur Active Directory-Standortmitgliedschaft zum Auffinden der übrigen Postfachserver, die sich an demselben Active Directory-Standort befinden. Der Unified Messaging-Dienst übermittelt Nachrichten zum Routen an den Transportdienst auf einem Postfachserver innerhalb desselben Active Directory-Standorts. Der Transportdienstserver führt eine Empfängerauflösung durch und fragt Active Directory ab, um eine Telefonnummer, eine E.164-Nummer oder eine SIP-Adresse einem Empfängerkonto zuzuordnen. Wenn die Empfängerauflösung abgeschlossen ist, stellt der Transportdienst die Nachricht wie eine reguläre E-Mail-Nachricht dem Zielpostfach zu.

  - **Clientverbindungen mit einem Clientzugriffsserver**   Wenn der Clientzugriffsserver eine Benutzerverbindungsanforderung empfängt, fragt er Active Directory ab, um zu bestimmen, welcher Postfachserver das Postfach des Benutzers hostet. Der Clientzugriffsserver ruft anschließend die Active Directory-Standortmitgliedschaft des jeweiligen Postfachservers ab und leitet die Verbindung mittels Proxy an den Postfachserver weiter.

## Ermitteln der Active Directory-Standortmitgliedschaft

Active Directory-Clients treffen Annahmen über die Standortmitgliedschaft, indem sie ihre zugewiesene IP-Adresse einem Subnetz zuordnen, das in Active Directory-Standorten und -Diensten definiert und mit einem Active Directory-Standort verknüpft ist. Anschließend verwendet der Client diese Informationen, um zu bestimmen, welche Domänencontroller und globalen Katalogserver an dem betreffenden Standort vorhanden sind, und kommuniziert mit den entsprechenden Verzeichnisservern zum Zweck der Authentifizierung und Autorisierung. Exchange 2013 nutzt diese Beziehung, indem zum Abrufen von Informationen über Empfänger ebenfalls Verzeichnisserver bevorzugt werden, die sich am gleichen Standort wie der Exchange 2013-Server befinden.

Alle Computer, die demselben Active Directory-Standort angehören, werden als untereinander gut mit schnellen, zuverlässigen Netzwerkverbindungen verbunden angesehen. Standardmäßig besteht bei der ersten Bereitstellung einer Active Directory-Gesamtstruktur ein einzelner Standort mit dem Namen `Default-First-Site-Name`. Wenn vom Administrator keine anderen Standorte manuell konfiguriert werden, werden alle Server und Clientcomputer in der Gesamtstruktur als Mitglieder von `Default-First-Site-Name` angesehen.

Wenn mehr als ein Standort definiert ist, muss der Active Directory-Administrator die Subnetze definieren, die in der Organisation vorhanden sind, und diese den Active Directory-Standorten zuordnen.

Der Microsoft Exchange Active Directory-Topologiedienst überprüft das Standortmitgliedschaftsattribut auf dem Exchange-Serverobjekt beim Starten des Servers. Wenn das Standortattribut aktualisiert werden muss, stempelt der Microsoft Exchange Active Directory-Topologiedienst das Attribut mit dem neuen Wert. Der Microsoft Exchange Active Directory-Topologiedienst überprüft den Wert des Standortattributs alle 15 Minuten und aktualisiert den Wert, wenn sich die Standortmitgliedschaft geändert hat. Der Microsoft Exchange Active Directory-Topologiedienst verwendet den Netzwerkanmeldedienst, um die aktuelle Standortmitgliedschaft abzurufen. Der Netzwerkanmeldedienst aktualisiert die Standortmitgliedschaft alle fünf Minuten. Dies bedeutet, dass eine Wartezeit von bis zu 20 Minuten zwischen dem Zeitpunkt, an dem sich die Standortmitgliedschaft ändert, und dem Stempeln des neuen Werts im Standortattribut verstreichen kann.

## Übersicht der IP-Standortverknüpfungen

Beziehungen zwischen Active Directory-Standorten werden mithilfe von IP-Standortverknüpfungen definiert. Die IP-Standortverknüpfung besteht aus zwei oder mehr Active Directory-Standorten. Alle Active Directory-Standorte, die der Verknüpfung angehören, kommunizieren zu gleichen Kosten. Die Eigenschaften von IP-Standortverknüpfungen umfassen eine Kostenzuweisung, einen Zeitplan und ein Intervall. Die Zeitplan- und Intervalleigenschaften werden nur zum Bestimmen der Active Directory-Replikationshäufigkeit verwendet. Exchange 2013 verwendet die Kostenzuweisung, um die Route mit den geringsten Datenverkehrskosten zu bestimmen, wenn mehrere Pfade zum Ziel bestehen. Die Kosten der Route werden durch Aggregation der Kosten aller Standortverknüpfungen in einem Übertragungspfad bestimmt. Der Active Directory-Administrator weist einer Verknüpfung die Kosten basierend auf der relativen Netzwerkgeschwindigkeit und der verfügbaren Netzwerkbandbreite im Vergleich mit anderen verfügbaren Verbindungen zu.

Standardmäßig versucht der Transportdienst auf einem Postfachserver immer, eine direkte Verbindung zum Transportdienst oder zum Postfachtransport-Zustellungsdienst auf einem Postfachserver an einem anderen Active Directory-Standort herzustellen. Nachrichten werden beim Transport nicht per Relay über den Transportdienst auf allen Postfachservern im Pfad einer Standortverknüpfung umgeleitet. Postfachserver an dazwischen liegenden Active Directory-Standorten auf dem Routingpfad können jedoch in folgenden Szenarien Nachrichtenrelay ausführen:

  - Eine direkte Weiterleitung zwischen Postfachservern findet nicht statt, wenn ein Hubstandort auf dem Routingpfad mit den geringsten Kosten vorhanden ist. Sie können einen Active Directory-Standort als Hubstandort konfigurieren, sodass Nachrichten über den Hubstandort geleitet werden, bevor die Nachrichten per Relay an den Zielserver weitergeleitet werden. Hubstandorte werden weiter unten in diesem Thema behandelt.

  - Exchange 2013 verwendet den aus IP-Standortverknüpfungsinformationen abgeleiteten Routingpfad, wenn ein Fehler bei der Kommunikation mit dem Active Directory-Zielstandort auftritt. Wenn kein Postfachserver am Active Directory-Zielstandort antwortet, wird die Nachrichtenzustellung auf dem Routingpfad mit den geringsten Kosten aufgegeben, bis eine Verbindung mit einem Postfachserver an einem Active Directory-Standort auf dem Routingpfad hergestellt ist. Die Nachrichten werden an diesem Active Directory-Standort in die Warteschlange eingestellt, und die Warteschlange befindet sich in einem Wiederholungsstatus. Dieses Verhalten wird als *Warteschlangenbildung am Fehlerpunkt* bezeichnet.

  - In Exchange 2013-Organisationen ohne DAGs kann der Transportdienst auf einem Postfachserver außerdem die IP-Standortverknüpfungsinformationen verwenden, um das Routing von Nachrichten, die an mehrere Empfänger gesendet werden, zu optimieren. Der Postfachserver zögert die Verzweigung von Nachrichten hinaus, bis eine Gabelung in den Routingpfaden an die Empfänger erreicht wird. Die verzweigte Nachricht wird per Relay mithilfe eines Postfachservers an dem Active Directory-Standort, der in den einzelnen Routingpfaden die Gabelung darstellt, an das jeweilige Empfängerziel geleitet. Diese Funktionalität wird als *verzögerte Auffächerung* bezeichnet.

## Angeben von Hubstandorten

Sie können das Cmdlet **Set-AdSite** verwenden, um einen bestimmten Active Directory-Standort als Hubstandort zu konfigurieren. Wenn entlang des kostengünstigsten Routingpfads zwischen zwei Transportservern ein Hubstandort vorhanden ist, werden die Nachrichten zur Verarbeitung über den Hubstandort umgeleitet, bevor sie per Relay an den Zielserver weitergeleitet werden. Damit dieses Routingverhalten auch eintritt, muss der Hubstandort entlang des kostengünstigsten Routingpfads zwischen zwei Transportservern vorhanden sein. Diese Konfiguration sollte nur verwendet werden, wenn sie aufgrund der Netzwerktopologie erforderlich ist, etwa wenn Firewalls zwischen den Active Directory-Standorten vorhanden sind, die ein direktes Weiterleiten der SMTP-Kommunikation verhindern. Weitere Informationen finden Sie unter [Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory](configure-exchange-mail-routing-settings-in-active-directory-exchange-2013-help.md).

## Festlegen von Exchange-spezifischen Kosten für eine IP-Standortverknüpfung

Sie können das Cmdlet **Set-AdSiteLink** in der Exchange-Verwaltungsshell verwenden, um Exchange-spezifische Kosten für eine Active Directory-IP-Standortverknüpfung zu konfigurieren. Die Exchange-spezifischen Kosten sind ein gesondertes Attribut, das anstelle der von Active Directory zugewiesenen Kosten für die Ermittlung des Exchange-Routingpfads verwendet wird. Diese Konfiguration ist hilfreich, wenn die Kosten der Active Directory-IP-Standortverknüpfung nicht zu einer optimalen Exchange-Nachrichtenroutingtopologie führen. Weitere Informationen finden Sie unter [Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory](configure-exchange-mail-routing-settings-in-active-directory-exchange-2013-help.md).

## Festlegen von Nachrichtengrößenbeschränkungen für IP-Standortverknüpfungen

Standardmäßig wendet Exchange 2013 keine maximale Nachrichtengröße für Nachrichten an, die mittels Relay zwischen Postfachservern an verschiedenen Active Directory-Standorten weitergeleitet werden. Wenn Sie mit dem Cmdlet **Set-AdSiteLink** eine maximale Nachrichtengröße für eine Active Directory-IP-Standortverknüpfung konfigurieren, wird beim Routing ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) für alle Nachrichten generiert, deren Größe die für eine Active Directory-Standortverknüpfung auf dem kostengünstigsten Routingpfad konfigurierte, maximal zulässige Nachrichtengröße überschreitet. Diese Konfiguration ist hilfreich, um die Größe von Nachrichten zu beschränken, die über Verbindungen mit niedriger Bandbreite an Active Directory-Remotestandorte gesendet werden.

## Platzierung von Exchange 2013-Servern an Active Directory-Standorten

Damit das Nachrichtenrouting zwischen Exchange 2013-Servern ordnungsgemäß ausgeführt wird, müssen alle Exchange-Server, die in der Gesamtstruktur bereitgestellt werden, einem Active Directory-Standort angehören. Stellen Sie sicher, dass sich die zugewiesenen IP-Adressen in Subnetzen befinden, die den Active Directory-Standorten ordnungsgemäß zugeordnet sind.

Der erste Schritt beim Planen der Platzierung von Exchange 2013-Servern in der Active Directory-Standorttopologie besteht im Dokumentieren der aktuellen Topologie. Ihre Dokumentation soll die folgenden Punkte umfassen:

  - Standorte

  - Subnetze und ihre Standortzuordnung

  - IP-Standortverknüpfungen und ihre Mitgliedsstandorte

  - Kosten für IP-Standortverknüpfungen

  - Verzeichnisserver an den einzelnen Standorten

  - Physische Netzwerkverbindungen

  - Firewallstandorte

Nachdem Sie diese Objekte in Diagrammen erfasst haben, planen Sie die Platzierung von Exchange-Servern. Berücksichtigen Sie die folgenden Informationen bei der Entscheidung für die Platzierung von Servern:

  - Ein Postfachserver muss direkt mit einem globalen Katalogserver kommunizieren, um Active Directory-Suchen durchzuführen.

  - Es ist empfehlenswert, an jedem Active Directory-Standort mehrere Postfachserver bereitzustellen, um Lastenausgleich und Fehlertoleranz zur Verfügung zu stellen.

  - DAGs und Standortsicherheit

  - Der auf Postfachservern ausgeführte Unified Messaging-Dienst übermittelt Voicemailnachrichten an den auf Postfachservern befindlichen Transportdienst, damit diese an Postfächer zugestellt werden. Der Clientzugriffsserver, der den Unified Messaging-Dienst für die Anrufweiterleitung ausführt, kann sich an einem Hubstandort oder in der Nähe des IP- oder VoIP-Gateways (Voice over IP), der IP-Nebenstellenanlage (IP Private Branch eXchange, IP PBX), der SIP-fähigen Nebenstellenanlage oder der SBCs (Session Border Controller) befinden. Der Transportdienst auf einem Postfachserver, der dieselbe Standortmitgliedschaft besitzt wie der Clientzugriffsserver, empfängt Voicemailnachrichten für den Transport und leitet die Nachrichten an den Transportdienst auf anderen Postfachservern in der Organisation weiter.

  - Clientzugriffsserver stellen einen Verbindungspunkt mit der Exchange-Organisation für Benutzer zur Verfügung, die Remote auf Exchange zugreifen. Ein Clientzugriffsserver muss an jedem Active Directory-Standort bereitgestellt werden, der Postfachserver enthält.

Nachdem Sie die Exchange 2013-Serverplatzierung geplant haben, können Sie Bereiche identifizieren, in denen die Active Directory-Standorttopologie zur Verbesserung des Kommunikationsflusses geändert werden kann. Möglicherweise möchten Sie IP-Standortverknüpfungen und die Kosten von Standortverknüpfungen anpassen, um die E-Mail-Zustellung zu optimieren. Eine effiziente Active Directory-Topologie erfordert keine Änderungen zur Unterstützung von Exchange 2013

