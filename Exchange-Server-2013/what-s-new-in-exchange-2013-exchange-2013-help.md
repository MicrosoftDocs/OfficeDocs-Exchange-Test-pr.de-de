---
title: 'Neuerungen in Exchange 2013: Exchange 2013 Help'
TOCTitle: Neuerungen in Exchange 2013
ms:assetid: 97501135-2149-4590-8373-98e638ac8eb1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150540(v=EXCHG.150)
ms:contentKeyID: 50476274
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Neuerungen in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Informieren Sie sich über die neuesten Funktionen in Exchange 2013.

Microsoft Exchange Server 2013 erweitert die Exchange Server-Produktlinie um eine umfangreiche Sammlung neuer Technologien, Funktionen und Dienste. Ziel ist es, Benutzer und Organisationen bei der Änderung ihrer Arbeitsgewohnheiten zu unterstützen, deren Schwerpunkt sich von auf der Kommunikation weiter auf die Zusammenarbeit verlagert. Zugleich hilft Exchange Server 2013, die Gesamtbetriebskosten zu senken – ob bei einer lokalen Bereitstellung von Exchange 2013 oder einer Bereitstellung Ihrer Postfächer in der Cloud. Neue Features und Funktionen in Exchange 2013 wurden für die folgenden Zwecke konzipiert:

  - **Unterstützen einer Mitarbeiterschaft mehrerer Generationen**   Ein soziales Miteinander und das schnelle Finden von Personen sind für Benutzer wichtig. Die Funktion *Intelligente Suche* wertet das Kommunikations- und Zusammenarbeitsverhalten aus, um Suchergebnisse im Exchange zu verbessern und mit Prioritäten zu versehen. Mithilfe von Exchange 2013 können Benutzer außerdem Kontakte aus mehreren Quellen zusammenführen, um eine einzelne Sicht auf eine Person zu schaffen, für die aus mehreren Stellen abgerufene Kontaktinformationen miteinander verknüpft werden.

  - **Neue optimierte Oberfläche**   Microsoft Outlook 2013 und Microsoft Outlook Web App haben eine neue aktualisierte Benutzeroberfläche. Outlook Web App bietet eine verbesserte Benutzeroberfläche, die auch die Verwendung von Touchscreens unterstützt, wodurch die Nutzung von Exchange auf mobilen Geräten optimiert wird.

  - **Integration mit SharePoint und Lync**   Exchange 2013 bietet mithilfe von Websitepostfächern und Compliance-eDiscovery eine bessere Integration mit Microsoft SharePoint 2013 und Microsoft Lync 2013. Zusammen bieten diese Produkte eine breite Palette an Features, die Szenarien wie Unternehmens-eDiscovery und Zusammenarbeit mit Websitepostfächern ermöglichen.

  - **Hilfe bei der Erfüllung wachsender Anforderungen hinsichtlich Compliance**   Compliance und eDiscovery stellen für viele Organisationen eine Herausforderung dar. Exchange 2013 hilft Ihnen nicht nur beim Suchen und Finden von Daten in Exchange, sondern in der gesamten Organisation. Dank verbesserter Such- und Indexfunktionen können Sie Exchange 2013, Lync 2013, SharePoint 2013 und Windows-Dateiserver durchsuchen. Mit den Funktionen zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) können Organisationen auch verhindern, dass Benutzer versehentlich vertrauliche Informationen an nicht autorisierte Personen senden. DLP ermöglicht Ihnen das Bestimmen, Überwachen und Schützen vertraulicher Daten mittels einer eingehenden Inhaltsanalyse.

  - **Bereitstellung einer ausfallsicheren Lösung**   Exchange 2013 baut auf der Architektur von Exchange Server 2010 auf und wurde hinsichtlich Einfachheit für Skalierung, Hardwarenutzung und Fehlerisolierung neu gestaltet.

Informationen zu den an Exchange Server 2013 seit der RTM-Version (Release to Manufacturing) erfolgten Änderungen finden Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md).

In den folgenden Themen finden Sie weitere Informationen zu den Neuerungen in Exchange 2013:

Exchange-Verwaltungskonsole

Exchange 2013-Architektur

Setup

Messagingrichtlinie und -kompatibilität

Schutz vor Schadsoftware

Nachrichtenübermittlung

Empfänger

Freigabe und Zusammenarbeit

Integration in SharePoint und Lync

Clients und mobile Funktionen

Unified Messaging

Batchverschiebungen von Postfächern

[Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md)

Verwaltung von Exchange-Arbeitsauslastungen


> [!NOTE]
> Weitere Informationen zu Funktionen in Vorgängerversionen von Exchange, die in Exchange Server&nbsp;2013 entfernt, eingestellt oder ersetzt wurden, finden Sie unter <A href="what-s-discontinued-in-exchange-2013-exchange-2013-help.md">In Exchange 2013 nicht mehr unterstützte Funktionen</A>. Darüber hinaus sind die <A href="release-notes-for-exchange-2013-exchange-2013-help.md">Versionshinweise zu Exchange&nbsp;2013</A> für Sie möglicherweise interessant.



## Exchange-Verwaltungskonsole

Exchange 2013 bietet eine zentrale vereinheitlichte und benutzerfreundliche Verwaltungskonsole, die für die Verwaltung von lokalen, Online- und Hybridbereitstellungen optimiert wurde. Die *Exchange-Verwaltungskonsole* in Exchange 2013 ersetzt die Exchange 2010-Verwaltungskonsole und die Exchange-Systemsteuerung (ECP). ("ECP" ist aber immer noch der Name des virtuellen Verzeichnisses, das von der Exchange-Verwaltungskonsole verwendet wird.) Zu den Funktionen der Exchange-Verwaltungskonsole zählen u. a.:

  - **Listenansicht**   Die Listenansicht der Exchange-Verwaltungskonsole weist wesentliche Einschränkungen der Exchange-Systemsteuerung nicht mehr auf. In der Exchange-Systemsteuerung konnten nur bis zu 500 Objekte angezeigt werden, und um Objekte anzuzeigen, die im Detailbereich nicht aufgeführt wurden, mussten Sie mithilfe von Such- und Filterfunktionen nach diesen Objekten suchen. In Exchange 2013 können in der Listenansicht der Exchange-Verwaltungskonsole gut 20.000 Objekte angezeigt werden. Nachdem die Exchange-Verwaltungskonsole die Ergebnisse zurückgegeben hat, führt der dazugehörige Client die Such- und Sortiervorgänge aus, wodurch im Vergleich zur Exchange-Systemsteuerung in Exchange 2010 deutliche Leistungsverbesserungen zu verzeichnen sind. Darüber hinaus können Sie die Ergebnisse seitenweise anzeigen. Sie können auch die Seitengröße konfigurieren und Daten in eine CSV-Datei exportieren.

  - **Hinzufügen/Entfernen von Spalten in der Empfängerlistenansicht**   Sie können festlegen, welche Spalten angezeigt werden sollen, und mithilfe lokaler Cookies können Sie Ihre benutzerdefinierten Listenansichten, über die Sie auf die Exchange-Verwaltungskonsole zugreifen, computerbezogen speichern.

  - **Absichern des virtuellen Verzeichnisses der Exchange-Systemsteuerung**   Sie können den Zugriff über das Internet und Intranets innerhalb des virtuellen IIS-Verzeichnisses der Exchange-Systemsteuerung partitionieren, um Verwaltungsfunktionen zuzulassen oder zu sperren. Mit dieser Funktion können Sie den Zugriff für Benutzer zulassen oder verweigern, die von außerhalb Ihrer Organisationsumgebung über das Internet auf die Exchange-Verwaltungskonsole zugreifen möchten. Gleichzeitig können Sie den Zugriff auf die Outlook Web App-Optionen eines Endbenutzers weiterhin zulassen.

  - **Verwaltung öffentlicher Ordnern**   In Exchange 2010 und Exchange 2007 wurden öffentliche Ordner über die Verwaltungskonsole für öffentliche Ordner verwaltet. Öffentliche Ordner befinden sich nun in der Exchange-Verwaltungskonsole, und Sie benötigen kein separates Tool mehr für deren Verwaltung.

  - **Benachrichtigungen**   In Exchange 2013 weist die Exchange-Verwaltungskonsole eine Benachrichtigungsanzeige auf, sodass Sie den Status lang dauernder Prozesse anzeigen können und, falls gewünscht, per E-Mail darüber benachrichtigt werden, sobald ein Prozess abgeschlossen ist.

  - **Benutzereditor für die rollenbasierte Zugriffssteuerung**   In Exchange 2010 konnte der Benutzereditor für die rollenbasierte Zugriffssteuerung in der Exchange Toolbox verwendet werden, um Benutzer zu Verwaltungsrollengruppen hinzuzufügen. In Exchange 2013 ist die Funktionalität des Benutzereditors für die rollenbasierte Zugriffssteuerung nun in die Exchange-Verwaltungskonsole integriert, sodass kein separates Tool zur Verwaltung der rollenbasierten Zugriffssteuerung erforderlich ist.

  - **Unified Messaging-Tools**   In Exchange 2010 konnten die Anrufstatistik und die Benutzeranrufprotokolle verwendet werden, um UM-Statistiken und -Informationen zu bestimmten Anrufen für einen UM-aktivierten Benutzer abzurufen. In Exchange 2013 sind die Anrufstatistik und die Benutzeranrufprotokolle nun in die Exchange-Verwaltungskonsole integriert, sodass kein separates Tool erforderlich ist, um diese Informationen zu verwalten.

  - **Verbesserungen für Gruppen**   In der Exchange-Verwaltungskonsole können nun im Fenster **Gruppen**, **Mitglieder auswählen** bis zu 10.000 Empfänger angezeigt werden. Standardmäßig werden bis zu 500 Empfänger zurückgegeben, wenn Sie das Fenster **Mitglieder auswählen** öffnen. Durch Klicken auf **Alle Ergebnisse abrufen** unter der Empfängerliste können Sie jedoch bis zu 10.000 Empfänger auflisten. Unterstützt wird nun auch das Durchsuchen von mehr als 500 Empfängern mithilfe der Bildlaufleiste. Außerdem bieten wir optimierte Suchfunktionen, mit deren Hilfe Sie die in der Empfängerliste enthaltenen Empfänger filtern können. Sie können filtern nach:
    
      - Ort
    
      - Firma
    
      - Land/Region
    
      - Abteilung
    
      - Büro
    
      - Titel

Weitere Informationen finden Sie unter [Exchange Admin Center in Exchange 2013](exchange-admin-center-in-exchange-2013-exchange-2013-help.md).

## Exchange 2013-Architektur

Vorgängerversionen von Exchange wurden gemäß der technischen Möglichkeiten zur jeweiligen Zeit entwickelt und optimiert. Während der Entwicklung von Exchange 2007 war beispielsweise die CPU-Leistung eine der wesentlichsten Einschränkungen. Zum Umgehen dieser Einschränkung wurde Exchange 2007 in verschiedene Serverrollen aufgeteilt, die eine horizontale Skalierung durch Servertrennung ermöglichten. Jedoch waren die Serverfunktionen in Exchange 2007 und Exchange 2010 eng gekoppelt. Die enge Kopplung der Rollen hatte mehrere Nachteile, z. B. Versionsabhängigkeit, geografische Affinität (alle Rollen muss sich an einem bestimmten Standort befinden), Sitzungsaffinität (ein teurer hardwaregestützter Layer 7-Lastenausgleich war erforderlich) und Namespacekomplexität.

Mittlerweile ist CPU-Leistung viel günstiger zu haben und kein einschränkender Faktor mehr. Nach dem Überwinden dieser Einschränkung war das primäre Entwicklungsziel für Exchange 2013 die Einfachheit von Skalierung, Hardwarenutzung und Fehlerisolierung. Für Exchange 2013 wurde die Anzahl der Serverrollen auf drei reduziert: Clientzugriff, Postfach und Edge-Transport.

Der Postfachserver umfasst alle traditionellen Serverkomponenten aus Exchange 2010: Clientzugriffsprotokolle, Transportdienst, Postfachdatenbanken und Unified Messaging. Der Postfachserver verarbeitet alle Vorgänge für die aktiven Postfächer auf diesem Server. Der Clientzugriffsserver bietet eine Authentifizierung, begrenzte Umleitung und Proxydienste. Der Clientzugriffsserver führt kein Datenrendering durch. Der Clientzugriffsserver ist ein zustandsloser Thin Server. Auf einem Clientzugriffsserver werden keine Daten gespeichert oder in Warteschlangen gestellt. Der Clientzugriffsserver bietet alle üblichen Clientzugriffsprotokolle: HTTP, POP und IMAP und SMTP.

Bei dieser neuen Architektur sind der Clientzugriffs- und der Postfachserver nur noch "lose gekoppelt". Verarbeitungsvorgänge und Aktivitäten für ein bestimmtes Postfach erfolgen auf dem Postfachserver, der die aktive Datenbankkopie hostet, in der sich das Postfach befindet. Alle Datenrender- und -transformationsvorgänge erfolgen lokal für die aktive Datenbankkopie, sodass Bedenken hinsichtlich der Versionskompatibilität zwischen Clientzugriffs- und Postfachserver aus dem Weg geräumt werden.

Mit Exchange 2013 Service Pack 1 haben wir erneut die Edge-Transport-Serverrolle eingeführt. Die Edge-Transport-Serverrolle wird normalerweise in Ihrem Umkreisnetzwerk außerhalb der internen Active Directory-Gesamtstruktur bereitgestellt und wurde entwickelt, um die Angriffsfläche Ihrer Exchange-Bereitstellung zu minimieren. Durch die Verarbeitung des gesamten E-Mail-Flusses in das Internet werden außerdem weitere Nachrichtenschutz- und Sicherheitsebenen gegen Viren und Spam hinzugefügt, und es können Transportregeln zum Steuern des Nachrichtenflusses angewendet werden. Weitere Informationen zur Serverrolle **Edge-Transport** finden Sie unter [Edge-Transport-Server](edge-transport-servers-exchange-2013-help.md).

Die Exchange 2013-Architektur bietet die folgenden Vorzüge:

  - **Flexibilität beim Versionsupgrade**   Keine starren Upgradeanforderungen mehr. Ein Upgrade eines Clientzugriffsservers kann unabhängig und in beliebiger Reihenfolge in Relation zum Postfachserver stattfinden.

  - **Sitzungsindifferenz**   Bei Exchange 2010 war für mehrere Protokolle Sitzungsaffinität zur Clientzugriffsserver-Rolle erforderlich. In Exchange 2013 befinden sich die Clientzugriffs- und Postfachkomponenten auf demselben Postfachserver. Da der Clientzugriffsserver alle Verbindungen eines Benutzers per Proxy an einen bestimmten Postfachserver weiterleitet, ist auf den Clientzugriffsservern keine Sitzungsaffinität erforderlich. Dadurch kann für eingehende Verbindungen für Clientzugriffsserver ein Lastenausgleich mithilfe von Methoden wie "Geringste Anzahl von Verbindungen" oder "Round-Robin" erfolgen.

  - **Einfachheit der Bereitstellung**   Bei einem Exchange 2010-Entwurf für ausfallsichere Standorte benötigten Sie bis zu acht verschiedene Namespaces: zwei Internet Protocol-Namespaces, zwei für Outlook Web App-Fallback, einen für die AutoErmittlung, zwei für den RPC-Clientzugriff und einen für SMTP. Für ein Upgrade von Exchange 2003 oder Exchange 2007 war zudem ein Legacynamespace erforderlich. Bei Exchange 2013 sinkt die Mindestanzahl von Namespaces auf zwei. Bei einer Koexistenzlösung mit Exchange 2007 müssen Sie dennoch einen Legacyhostnamen erstellen. Doch bei einer Koexistenzlösung mit Exchange 2010 oder Installation einer neuen Exchange 2013-Organisation benötigen Sie nur zwei Namespaces: einen für Clientprotokolle und einen für die AutoErmittlung. Möglicherweise benötigen Sie auch einen SMTP-Namespace.

Aufgrund dieser Architekturänderungen gab es Änderungen in Bezug auf die Clientkonnektivität. Erstens wird RPC nicht länger als Protokoll für den Direktzugriff unterstützt. Dies bedeutet, dass sämtliche Outlook-Verbindungen mithilfe von RPC über HTTP (auch als Outlook Anywhere bekannt) erfolgen müssen. Auf den ersten Blick scheint dies eine Einschränkung zu sein, doch tatsächlich ergeben sich einige zusätzliche Vorteile. Der offenkundigste Vorteil ist, dass der RPC-Clientzugriffsdienst sich nicht auf dem Clientzugriffsserver befinden muss. Dies resultiert zu einer Verringerung um zwei Namespaces, die normalerweise für eine ausfallsichere Lösung für Standorte erforderlich wären. Darüber hinaus muss keine Affinität mehr für den RPC-Clientzugriffsdienst bereitgestellt werden.

Zweitens greifen Outlook-Clients nicht mehr wie in allen Vorversionen von Exchange auf den vollqualifizierten Domänennamen (FQDN) eines Servers zu. Outlook verwendet die AutoErmittung zum Erstellen eines neuen Verbindungspunkts, der aus einer Postfach-GUID, dem Symbol "@" und dem Domänenteil der primären SMTP-Adresse des Benutzers besteht. Diese einfache Änderung führt zu einer fast vollständigen Einstellung der unwillkommenen Nachricht "Ihr Administrator hat eine Änderung an Ihrem Postfach vorgenommen. Bitte starten Sie neu." Nur Outlook 2007 und höhere Versionen werden von Exchange 2013 unterstützt.

Das Modell für Hochverfügbarkeit der Postfachkomponente hat sich seit Exchange 2010 nicht wesentlich geändert. Die Einheit für Hochverfügbarkeit ist weiter die Database Availability Group (DAG). Für die DAG wird immer noch Windows Server-Failoverclustering verwendet. Für die fortlaufende Replikation werden weiter sowohl die Dateimodus- als auch die Blockmodusreplikation unterstützt. Jedoch gibt es einige Verbesserungen. Failoverzeiten wurden verkürzt, und zwar als Ergebnis von verbessertem Transaktionsprotokollcode und umfassender Überprüfungen der passiven Datenbanken. Der Exchange-Speicherdienst wurde in verwaltetem Code neu geschrieben (siehe den Abschnitt "Verwalteter Speicher" weiter unten in diesem Kapitel). Jede Datenbank wird nun in einem eigenen Prozess ausgeführt, was die Isolierung von Speicherproblemen auf eine einzelne Datenbank ermöglicht.

## Verwalteter Speicher

In Exchange 2013 ist *Verwalteter Speicher* der Name der neu gestalteten Informationsspeicherprozesse ("Microsoft.Exchange.Store.Service.exe" und "Microsoft.Exchange.Store.Worker.exe"). Der neue verwaltete Speicher ist in C\# geschrieben und eng in den Microsoft Exchange-Replikationsdienst (MSExchangeRepl.exe) integriert, um eine verbesserte Resilienz und damit eine höhere Verfügbarkeit bereitzustellen. Darüber hinaus ermöglicht die Architektur des verwalteten Speichers eine präzisere Verwaltung der Ressourcennutzung und schnellere Ursachenanalyse durch eine verbesserte Diagnose.

Der verwaltete Speicher arbeitet mit dem Microsoft Exchange-Replikationsdienst bei der Verwaltung von Postfachdatenbanken zusammen, für die weiterhin ESE (Extensible Storage Engine) als Datenbankmodul verwendet wird. Exchange 2013 weist wesentliche Änderungen am Schema von Postfachdatenbanken auf, die im Vergleich zu früheren Exchange-Versionen viele Optimierungen bieten. Zusätzlich zu diesen Änderungen ist der Microsoft Exchange-Replikationsdienst für die Verfügbarkeit sämtlicher Dienste für Postfachserver zuständig. Aufgrund der Architekturänderungen sind ein schnelleres Datenbankfailover und ein besserer Umgang mit dem Ausfall physischer Datenträger möglich.

Der verwaltete Speicher ist außerdem mit dem Search Foundation-Suchmodul integriert (das auch von SharePoint 2013 verwendet wird), um im Vergleich zur Microsoft-Suche in früheren Versionen von Exchange zuverlässigere Indizierungs- und Suchfunktionen zu bieten.

Weitere Informationen finden Sie unter [Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md).

## Zertifikatverwaltung

Das Verwalten digitaler Zertifikate ist eine der wichtigsten Aufgaben in Bezug auf Sicherheit in Ihrer Exchange-Organisation. Die Sicherstellung, dass Zertifikate ordnungsgemäß konfiguriert sind, ist der Schlüssel zu einer sicheren Messaginginfrastruktur für das Unternehmen. In Exchange 2010 war die Exchange-Verwaltungskonsole das Hauptinstrument zum Verwalten von Zertifikaten. In Exchange 2013 erfolgt die Zertifikatverwaltung auch mithilfe der neu gestalteten Exchange 2013-Verwaltungskonsole für Administratoren.

Die Vorgaben für Exchange 2013 in Bezug auf Zertifikate waren schwerpunktmäßig die Minimierung der Anzahl von Zertifikaten, die ein Administrator verwalten muss, und der Interaktion des Administrators mit Zertifikaten sowie das Ermöglichen einer zentralen Zertifikatverwaltung. Aus den Änderungen bei der Zertifikatverwaltung ergeben sich die folgenden Vorteile:

  - Die Zertifikatverwaltung kann auf dem Clientzugriffs- oder Postfachserver erfolgen. Für den Postfachserver ist standardmäßig ein selbstsigniertes Zertifikat installiert. Der Clientzugriffsserver vertraut dem selbstsignierten Zertifikat auf dem Exchange 2013-Postfachserver automatisch, weshalb Clients keine Warnungen zu einem selbstsignierten Zertifikat erhalten, dem nicht vertraut wird. Voraussetzung ist allerdings, dass der Exchange 2013-Clientzugriffsserver über ein nicht selbstsigniertes Zertifikat von entweder einer Windows-Zertifizierungsstelle oder einem vertrauenswürdigen Drittanbieter verfügt.

  - In früheren Exchange-Versionen war es schwierig zu erkennen, wann sich ein digitales Zertifikat dem Ablauf näherte. In Exchange 2013 zeigt das Benachrichtigungscenter Warnungen an, wenn ein auf einem Server mit Exchange 2013 gespeichertes Zertifikat vor dem Ablauf steht. Administratoren können diese Benachrichtigungen wahlweise auch per E-Mail erhalten.

Weitere Informationen finden Sie unter [Digitale Zertifikate und SSL](digital-certificates-and-ssl-exchange-2013-help.md).

## Setup

Setup wurde komplett neu gestaltet, sodass das Installieren von Exchange 2013 und Sicherstellen, dass Sie über die neuesten Produktrollups und Sicherheitsfixes verfügen, nun einfacher als je zuvor ist. Hier einige der Verbesserungen, die wir vorgenommen haben:

  - **Setup greift stets auf aktuelle Informationen zu**   Wenn Sie den Setup-Assistenten ausführen, können Sie die neuesten Produktrollups, Sicherheitsfixes und Sprachpakete herunterladen und nutzen. Über diese Option werden nicht nur die Dateien aktualisiert, die zum Ausführen von Exchange dienen, sondern Setup selbst kann aktualisiert werden. Auf diese Weise können wir Setup im Anschluss an die Produktveröffentlichung weiter verbessern und Überprüfungen der Bereitschaft aktualisieren, sobald Anforderungen aktualisiert oder geändert werden.
    
    Wenn Sie den unbeaufsichtigten Setupmodus verwenden, können Updates nicht automatisch heruntergeladen werden. Sie können dennoch weiter in den Genuss der Ausführung der neuesten Version von Setup kommen, indem Sie die neuesten Updates vorher herunterladen und den Parameter `/UpdatesDir: <path>` angeben, damit Setup sich vor Beginn des Installationsvorgangs selbst aktualisiert.

  - **Verbesserte Überprüfungen der Bereitschaft**   Überprüfungen der Bereitschaft stellen sicher, dass Ihr Computer und Ihre Organisation für Exchange 2013 bereit sind. Nachdem Sie Setup die benötigten Informationen zu Ihrer Installation bereitgestellt haben, werden die Überprüfungen der Bereitschaft vor Beginn der Installation ausgeführt. Das neue Modul für Überprüfungen der Bereitschaft durchläuft nun sämtliche Überprüfungen, bevor Ihnen gemeldet wird, welche Aktionen Sie durchführen müssen, damit Setup fortgesetzt werden kann. Dieser Vorgang erfolgt so schnell wie nie zuvor. Wie bei Vorgängerversionen von Exchange können Sie Setup auffordern, die hierfür benötigten Windows-Funktionen zu installieren, damit Sie dies nicht manuell ausführen müssen.

  - **Vereinfachter und moderner Assistent**   Wir haben sämtliche Schritte im Setup-Assistenten entfernt, die für die Installation von Exchange nicht unbedingt erforderlich sind. Übrig geblieben ist ein einfach zu durchlaufender Assistent, der Sie nacheinander durch alle Schritte des Installationsprozesses begleitet.

Weitere Informationen finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

## Messagingrichtlinie und -kompatibilität

Es gibt zwei neue Nachrichtenrichtlinien- und Kompatibilitätsfeatures in Exchange 2013: Verhinderung von Datenverlust und Microsoft Rights Management-Verbindungsdienst

DLP-Funktionen zur *Verhinderung von Datenverlust* helfen Ihnen dabei, Ihre vertraulichen Daten zu schützen und Benutzer über interne Richtlinien und Vorschriften zu informieren. Mit DLP können Sie in Ihrer Organisation verhindern, dass Benutzer versehentlich vertrauliche Informationen an nicht autorisierte Personen senden. DLP ermöglicht Ihnen das Bestimmen, Überwachen und Schützen vertraulicher Daten mittels einer eingehenden Inhaltsanalyse.Exchange 2013 bietet vordefinierte DLP-Richtlinien basierend auf diversen Bestimmungen wie beispielsweise PII (persönlich identifizierbare Informationen) und PCI-DSS (Payment Card Industry Data Security Standard) und kann erweitert werden, um weitere für Ihr Unternehmen wichtige Richtlinien zu unterstützen. Darüber hinaus ermöglicht die neue Funktion der Richtlinientipps in Outlook 2013 Ihnen, Ihre Benutzer über mögliche Richtlinienverletzungen zu informieren, bevor vertrauliche Daten gesendet werden.

Der Microsoft Rights Management-Verbindungsdienst (RMS-Verbindungsdienst) ist eine optionale Anwendung, die den Datenschutz für Ihren Exchange 2013-Server mithilfe von cloudbasierten Rechteverwaltungsdiensten (Microsoft Rights Management-Diensten) verbessert. Nachdem Sie den RMS-Verbindungsdienst installiert haben, bietet er kontinuierlichen Datenschutz während der gesamten Lebensspanne der Informationen. Da diese Dienste anpassbar sind, können Sie das gewünschte Sicherheitsniveau festlegen. Sie können beispielsweise den E-Mail-Nachrichtenzugriff auf bestimmte Benutzer beschränken oder für bestimmte Nachrichten nur Leserechte festlegen.

Hier erfahren Sie mehr über diese Funktionen:

[Verhinderung von Datenverlust](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)

[Rights Management-Verbindungsdienst](https://go.microsoft.com/fwlink/p/?linkid=330432)

## Compliance-Archivierung, Aufbewahrung und eDiscovery

Exchange 2013 bietet die folgenden Verbesserungen für Compliance-Archivierung, Aufbewahrung und eDiscovery, damit Ihre Organisation ihre Anforderungen an die Richtlinientreue besser erfüllen kann:

  - **Compliance-Archiv**   Ein neues einheitliches Archivmodell, mit dessen Hilfe Sie gesetzliche Archivierungsvorschriften in den folgenden Szenarien erfüllen können:
    
      - Aufbewahren der Ergebnisse der Abfrage (abfragebasierte Aufbewahrung), wodurch eine bereichsbasierte Unveränderbarkeit postfachübergreifend ermöglicht wird.
    
      - Definieren einer zeitbasierten Aufbewahrung (Sie können beispielsweise alle Elemente in einem Postfach sieben Jahre aufbewahren. Für dieses Szenario mussten in Exchange 2010 die Funktionen "Wiederherstellung einzelner Elemente/Aufbewahrungszeit für gelöschte Elemente" verwendet werden).
    
      - Dauerhaftes Platzieren eines Postfachs in einem Archiv (ähnlich dem Beweissicherungsverfahren in Exchange 2010).
    
      - Platzieren eines Benutzerpostfachs in mehreren Archiven, um die Anforderungen verschiedener Untersuchungen zu erfüllen.

  - **Compliance-eDiscovery**   Compliance-eDiscovery ermöglicht autorisierten Benutzern das Durchsuchen von Postfachdaten in sämtlichen Postfächern und Compliance-Archiven einer Exchange 2013-Organisation und das Kopieren von Nachrichten zur Überprüfung in ein Discoverypostfach. In Exchange 2013 wurde Compliance-eDiscovery verbessert, um zuständigen Mitarbeitern effizientere Such- und Archivierungsvorgänge zu ermöglichen. Diese Verbesserungen umfassen:
    
      - Über eine **Sammelsuche** können Daten in mehreren Datenspeichern durchsucht und beibehalten werden. In Exchange 2013 können Sie Compliance-eDiscovery-Suchen übergreifend in Exchange, SharePoint 2013 und Lync 2013 durchführen. Im eDiscovery Center in SharePoint 2013 können Sie Compliance-eDiscovery-Such- und Archivierungsvorgänge durchführen.
    
      - Ein **abfragebasiertes Compliance-Archiv** ermöglicht das Speichern der Ergebnisse der Abfrage, wodurch eine bereichsbasierte Unveränderbarkeit postfachübergreifend ermöglicht wird.
    
      - **Export von Suchergebnissen** Discoverymanager können über die SharePoint 2013-eDiscovery-Konsole Postfachinhalte in eine PST-Datei exportieren. Cmdlets für das Anfordern des Exports von Postfächern sind nicht mehr erforderlich, um ein Postfach in eine PST-Datei zu exportieren.
    
      - **Schlüsselwortstatistik**   Suchstatistiken werden suchbegriffsbezogen bereitgestellt. Dadurch kann ein Discoverymanager schnell intelligente Entscheidungen zur weiteren Optimierung der Suchabfrage treffen, um bessere Ergebnisse zu erzielen. eDiscovery-Suchergebnisse werden nach Relevanz sortiert.
    
      - **KQL-Syntax**   Discoverymanager können in Suchabfragen KQL-Syntax (Keyword Query Language) verwenden. KQL ähnelt AQS (Advanced Query Syntax), die für Discoverysuchvorgänge in Exchange 2010 verwendet wurde.
    
      - **Assistent für Compliance-eDiscovery und -Archiv**   Discoverymanager können mit diesem neuen Assistenten Compliance-eDiscovery- und -Archiv-Vorgänge durchführen.
        

        > [!NOTE]
        > Wenn SharePoint 2013 nicht verfügbar ist, steht in der Exchange-Verwaltungskonsole eine eingeschränkte eDiscovery-Funktionalität zur Verfügung.



  - **Durchsuchen aller primären und Archivpostfächer in Outlook Web App**   Benutzer können in Outlook Web App alle ihre primären und Archivpostfächer durchsuchen. Zwei getrennte Suchvorgänge sind nicht mehr notwendig.

  - **Archivieren von Lync-Inhalten**   Exchange 2013 unterstützt die Archivierung von Lync 2013-Inhalten in einem Benutzerpostfach. Sie können mithilfe der Funktion "Compliance-Archiv" Lync-Inhalte in Archivpostfächern platzieren und mit der Funktion "Compliance-eDiscovery" in Exchange archivierte Lync-Inhalte durchsuchen.

  - **Aufbewahrungsrichtlinien**  Mithilfe von Aufbewahrungsrichtlinien kann Ihre Organisation Risiken im Zusammenhang mit E-Mail und anderen Kommunikationsmitteln verringern und E-Mail-Aufbewahrungsanforderungen erfüllen. Die Aufbewahrungsrichtlinien wurden in folgenden Bereichen verbessert:
    
      - **Unterstützung von Aufbewahrungstags für "Kalender" und "Aufgaben"**   Sie können Aufbewahrungsrichtlinientags für die Standardordner "Kalender" und "Aufgaben" erstellen, damit Elemente in diesen Ordnern ablaufen. Elemente in diesen Ordnern werden außerdem basierend auf den für das Postfach geltenden Archivrichtlinieneinstellungen in das Archiv des Benutzers verschoben.
    
      - **Optimierte Fähigkeit zur Aufbewahrung von Elementen für einen angegebenen Zeitraum**   Sie können mithilfe einer Aufbewahrungsrichtlinie und eines zeitbasierten Compliance-Archivs die Aufbewahrung von Elementen für einen festgelegten Zeitraum erzwingen.

Weitere Informationen finden Sie unter [Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md).

## Transportregeln

Transportregeln in Exchange Server 2013 sind eine Weiterentwicklung der in Exchange Server 2010 verfügbaren Funktionen. Es sind jedoch einige Verbesserungen an den Transportregeln in Exchange 2013 erfolgt. Die wichtigste Änderung ist die Unterstützung der Verhinderung von Datenverlust (Data Loss Prevention, DLP). Ferner sind neue Prädikate und Aktionen sowie eine verbesserte Überwachung verfügbar und einige Architekturänderungen erfolgt.

Ausführliche Informationen finden Sie unter [Neuerungen bei Transportregeln](what-s-new-for-transport-rules-exchange-2013-help.md).

## Verwaltung von Informationsrechten

Information Rights Management (IRM) ist kompatibel mit dem Kryptografiemodus 2, einem AD RMS-Kryptografiemodus (Active Directory Rights Management), der eine stärkere Verschlüsselung unterstützt und Ihnen die Verwendung von 2048-Bit-Schlüsseln für RSA und 256-Bit-Schlüsseln für SHA-1 ermöglicht. Darüber hinaus ermöglicht der Kryptografiemodus 2 die Verwendung des SHA-2-Hashalgorithmus. Weitere Informationen zu Kryptografiemodi in AD RMS finden Sie unter [AD RMS-Kryptografiemodi](https://go.microsoft.com/fwlink/p/?linkid=263219).

## Überwachung

Exchange 2013 bietet die folgenden Verbesserungen an der Überwachung:

  - **Überwachungsberichte**   Die Exchange-Verwaltungskonsole bietet Überwachungsfunktionen, sodass Sie Berichte erstellen oder Einträge aus dem Postfachüberwachungsprotokoll oder Administratorüberwachungsprotokoll exportieren können. Im Postfachüberwachungsprotokoll werden alle Postfachzugriffe erfasst, die von Personen vorgenommen werden, bei denen es sich nicht um den Besitzer des Postfachs handelt. Dadurch können Sie ermitteln, wer auf ein Postfach zugegriffen hat und welche Aktionen ausgeführt wurden. Im Administratorüberwachungsprotokoll werden (auf der Grundlage eines Exchange Verwaltungsshell-Cmdlets) alle Aktionen aufgezeichnet, die von einem Administrator ausgeführt wurden. Diese Informationen können Sie zum Behandeln von Konfigurationsproblemen sowie zum Ermitteln der Ursache von Sicherheits- oder Richtlinientreueproblemen heranziehen. Weitere Informationen finden Sie unter [Exchange-Überwachungsberichte](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

  - **Anzeigen des Administratorüberwachungsprotokolls**   Anstatt das Administratorüberwachungsprotokoll zu exportieren, dessen Empfang in einer E-Mail-Nachricht bis zu 24 Stunden dauern kann, können Sie Einträge im Administratorüberwachungsprotokoll in der Exchange-Verwaltungskonsole anzeigen. Wählen Sie **Verwaltung der Richtlinientreue** \> **Überwachung** aus, und klicken Sie anschließend auf **Administratorüberwachungsprotokoll anzeigen**. Es können bis zu 1.000 Einträge auf mehreren Seiten angezeigt werden. Um die Suche einzuschränken, können Sie einen Datumsbereich angeben. Weitere Informationen finden Sie unter [Anzeigen des Administratorüberwachungsprotokolls](view-the-administrator-audit-log-exchange-2013-help.md).

## Schutz vor Schadsoftware

Die integrierten Filterfunktionen für Schadsoftware in Exchange 2013 dienen zum Schutz Ihres Netzwerks vor Schadsoftware, die durch E-Mail-Nachrichten übertragen wird. Alle von Ihrem Server mit Exchange gesendeten und empfangenen Nachrichten werden auf Schadsoftware (Viren und Spyware) überprüft. Sobald Schadsoftware erkannt wird, wird die Nachricht gelöscht. Wenn eine infizierte Nachricht gelöscht und nicht übermittelt wird, können auch Benachrichtigungen an Absender oder Administratoren gesendet werden. Sie können auch infizierte Anlagen durch entweder Standard- oder benutzerdefinierte Nachrichten ersetzen, die die Empfänger über erkannte Schadsoftware informieren.

Weitere Informationen zum Schutz vor Schadsoftware finden Sie unter [Antischadsoftwareschutz](anti-malware-protection-exchange-2013-help.md).

## Nachrichtenübermittlung

Exchange 2013 weist wesentliche Änderungen hinsichtlich der Übermittlung von Nachrichten durch eine Organisation und ihrer Verarbeitung auf. Es folgt eine kurze Übersicht der Änderungen:

  - **Transportpipeline**   An der Transportpipeline in Exchange 2013 sind nun mehrere Dienste beteiligt: der Front-End-Transport-Dienst auf Clientzugriffsservern, der Transportdienst auf Postfachservern und der Postfachtransportdienst auf Postfachservern. Weitere Informationen finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).

  - **Routing**   Beim Routing von E-Mail in Exchange 2013 werden DAG-Grenzen und Active Directory-Standortgrenzen erkannt. Darüber hinaus wurde das E-Mail-Routing so verbessert, dass Nachrichten für interne Empfänger direkter in Warteschlangen abgelegt werden. Weitere Informationen finden Sie unter [E-Mail-Routing](mail-routing-exchange-2013-help.md).

  - **Connectors**   Die standardmäßige maximale Nachrichtengröße für einen Sende- oder Empfangsconnector gemäß dem Parameter *MaxMessageSize* wurde von 10 MB auf 25 MB erhöht. Weitere Informationen zum Festlegen von Parametern für einen Connector finden Sie unter [Set-SendConnector](https://technet.microsoft.com/de-de/library/aa998294\(v=exchg.150\)) und [Set-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125140\(v=exchg.150\)).
    
    Sie können mithilfe des Parameters *FrontEndProxyEnabled* des Cmdlets **Set-SendConnector** einen Sendeconnector im Transportdienst eines Postfachservers auf das Routing von ausgehender E-Mail durch einen Front-End-Transportserver am lokalen Active Directory-Standort festlegen. Dadurch können Sie bestimmen, wie das Routing von E-Mail durch den Transportdienst erfolgt.

  - **Edge-Transport**   Sie können optional einen Edge-Transport-Server in Ihrem Umkreisnetzwerk installieren, um die Angriffsfläche zu verkleinern und Nachrichtenschutz und -sicherheit zu bieten. Weitere Informationen finden Sie unter [Edge-Transport-Server](edge-transport-servers-exchange-2013-help.md).

## Empfänger

In diesem Abschnitt werden die Verbesserungen bei der Verwaltung von Empfängern in Exchange 2013 beschrieben:

  - **Gruppenbenennungsrichtlinie**   Administratoren können nun in der Exchange-Verwaltungskonsole eine *Gruppenbenennungsrichtlinie* erstellen, mit deren Hilfe Sie die Namen von Verteilergruppen standardisieren und verwalten können, die von Benutzern in Ihrer Organisation erstellt werden. Sie können festlegen, dass dem Namen der Verteilergruppe bei der Erstellung ein bestimmtes Präfix und Suffix hinzugefügt werden muss, und Sie können die Verwendung bestimmter Wörter unterbinden. Dadurch können Sie die Verwendung ungeeigneter Wörter in Gruppennamen eindämmen.
    
    Weitere Informationen finden Sie unter [Erstellen einer Benennungsrichtlinie für Verteilergruppen](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

  - **Nachrichtenverfolgung**   Administratoren können in der Exchange-Verwaltungskonsole auch Zustellungsoptionen für E-Mail-Nachrichten nachverfolgen, die von Benutzern in Ihrer Organisation gesendet oder empfangen werden. Sie wählen nur ein Postfach aus und suchen dann nach Nachrichten, die an einen anderen Benutzer gesendet oder von diesem empfangen wurden. Sie können die Suche eingrenzen, indem Sie in der Betreffzeile nach bestimmten Wörtern suchen. Im sich ergebenden Zustellungsbericht wird eine Nachricht während des Zustellungsprozesses nachverfolgt und angegeben, ob die Nachricht erfolgreich zugestellt wurde, ob die Zustellung noch aussteht oder ob sie nicht zugestellt wurde.
    
    Weitere Informationen finden Sie unter [Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md).

## Freigabe und Zusammenarbeit

In diesem Abschnitt werden die Verbesserungen bei Freigabe und Zusammenarbeit in Exchange 2013 beschrieben.

  - **Öffentliche Ordner**   Öffentliche Ordner kommen nun in den Genuss der vorhandenen Hochverfügbarkeits- und Speichertechnologien des Postfachspeichers. Die Architektur für öffentliche Ordner verwendet speziell entworfene Postfächer, um sowohl die Hierarchie als auch die Inhalte öffentlicher Ordner zu speichern. Dieser neue Entwurf bedeutet auch, dass es keine Öffentliche Ordner-Datenbank mehr gibt. Für die Replikation öffentlicher Ordner wird jetzt das Modell der fortlaufenden Replikation eingesetzt. Hochverfügbarkeit für die Hierarchie- und Inhaltspostfächer wird von der DAG bereitgestellt. Durch diesen Entwurf erfolgt ein Wechsel weg von einem Multimaster- hin zu einem Einzelmasterreplikationsmodell.
    
    Outlook Web App-Benutzer in Ihrer Organisation haben jetzt die Möglichkeit, öffentliche Ordner zu ihren Favoriten hinzuzufügen oder aus ihren Favoriten zu entfernen. Zuvor konnte dies nur in Outlook durchgeführt werden.
    
    Weitere Informationen finden Sie unter [Öffentliche Ordner](public-folders-exchange-2013-help.md).

  - **Websitepostfächer**   E-Mails und Dokumente werden herkömmlicherweise in zwei voneinander getrennten Datenrepositorys gespeichert. Die meisten Teams verwenden bei der Zusammenarbeit normalerweise beide Medien. Die Herausforderung liegt darin, dass auf E-Mails und Dokumente mit unterschiedlichen Clients zugegriffen wird. Dies reduziert üblicherweise sowohl die Benutzerfreundlichkeit als auch die Benutzerproduktivität.
    
    Das *Websitepostfach* ist ein neues Konzept in Exchange 2013, mit dem diese Probleme gelöst werden sollen. Websitepostfächer verbessern die Zusammenarbeit und Benutzerproduktivität, indem sie den Zugriff auf SharePoint-Websitedokumente und E-Mail-Nachrichten in Outlook 2013 über die gleiche Clientbenutzeroberfläche ermöglichen. Ein Websitepostfach besteht funktional aus der Mitgliedschaft in einer SharePoint-Website (Besitzer und Mitglieder), gemeinsam genutztem Speicher in einem Exchange-Postfach für E-Mail-Nachrichten und einer SharePoint-Website für Dokumente sowie einer Verwaltungsoberfläche für Bereitstellungs- und Lebenszyklusanforderungen.
    
    Weitere Informationen finden Sie unter [Websitepostfächer](site-mailboxes-exchange-2013-help.md).

  - **Freigegebene Postfächer**   In Vorgängerversionen von Exchange mussten zum Erstellen eines freigegebenen Postfachs mehrere Schritte ausgeführt werden, wobei Stellvertretungsberechtigungen über die Exchange-Verwaltungsshell festgelegt wurden. In Exchange 2013 können Sie nun in der Exchange-Verwaltungskonsole ein freigegebenes Postfach erstellen. Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Freigegebene Postfächer**, um ein freigegebenes Postfach zu erstellen. Ein freigegebenes Postfach ist nun ein Empfängertyp, weshalb Sie auf der Benutzeroberfläche oder über die Shell ganz einfach nach freigegebenen Postfächern suchen können.
    
    Weitere Informationen finden Sie unter [Freigegebene Postfächer](shared-mailboxes-exchange-2013-help.md).

## Integration in SharePoint und Lync

Exchange 2013 bietet eine bessere Integration mit SharePoint 2013 und Lync 2013. Vorteile dieser verbesserten Integration sind u. a.:

  - Exchange 2013 ist mit SharePoint 2013 integriert, damit Benutzer mithilfe von Websitepostfächern effektiver zusammenarbeiten können.

  - Lync Server 2013 ermöglicht die Archivierung von Inhalten in Exchange 2013 und Nutzung von Exchange 2013 als Kontaktspeicher.

  - Discoverymanager können Compliance-eDiscovery- und Compliance-Archiv-Suchvorgänge auf sämtliche Daten in SharePoint 2013, Exchange 2013 und Lync 2013 anwenden.

  - Die Oauth-Authentifizierung ermöglicht Anwendungen von Partnern die Authentifizierung als Dienst oder bei Bedarf das Annehmen der Identität von Benutzern.

Weitere Informationen finden Sie unter [Integration in SharePoint und Lync](integration-with-sharepoint-and-lync-exchange-2013-help.md).

## Clients und mobile Funktionen

Die Outlook Web App-Benutzeroberfläche ist neu und für Tablets und Smartphones sowie für Desktop- und Laptopcomputer optimiert. Zu den neuen Funktionen gehören Apps für Outlook, die Benutzern und Administratoren die Erweiterung der Funktionsmöglichkeiten von Outlook Web App erlauben: die Verknüpfung von Kontakten, die Möglichkeit für Benutzer, Kontakte aus ihre LinkedIn-Konten hinzuzufügen, und Aktualisierungen des Aussehens und der Funktionen des Kalenders.

Weitere Informationen finden Sie unter [Neuerungen bei Outlook Web App in Exchange 2013](what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md).

## Unified Messaging

Unified Messaging in Exchange 2013 bietet im Wesentlichen dieselben Voicemailfunktionen wie Exchange 2010. Diese vorhandenen Funktionen wurden jedoch durch einige neue und weiterentwickelte Funktionen ergänzt. Wichtiger ist der Hinweis, dass Architekturänderungen an Exchange 2013 Unified Messaging zu Komponenten, Diensten und Funktionalität geführt haben, die von der Unified Messaging-Serverrolle in Exchange 2010 geboten wurden und nun in Exchange 2013 auf die Clientzugriffs- und Postfachserverrolle aufgeteilt sind.

Weitere Informationen finden Sie unter [Neues in Exchange 2013 Unified Messaging](what-s-new-for-unified-messaging-in-exchange-2013-exchange-2013-help.md).

## Batchverschiebungen von Postfächern

In Exchange 2013 wurde das Konzept von Batchverschiebungen eingeführt. Die neue Verschiebungsarchitektur basiert auf der des Postfachreplikationsdiensts und bietet verbesserte Verwaltungsfunktionen. Die neue Architektur für Batchverschiebungen weist die folgenden Verbesserungen auf:

  - Möglichkeit, mehrere Postfächer in großen Batches zu verschieben.

  - E-Mail-Benachrichtigung bei Verschiebung mit Berichterstellung.

  - Automatische Wiederholung und automatische Priorisierung von Verschiebungen.

  - Primäre und persönliche Archivpostfächer können zusammen oder einzeln verschoben werden.

  - Option zum manuellen Abschließen der Verschiebungsanforderung, sodass Sie eine Verschiebung überprüfen können, ehe Sie sie abschließen.

  - Regelmäßige inkrementelle Synchronisierungen zum Migrieren der Änderungen.

Weitere Informationen finden Sie unter [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).

## Hohe Verfügbarkeit und Ausfallsicherheit von Standorten

Exchange 2013 verwendet DAGs, Postfachdatenbankkopien und weitere Funktionen, wie z. B. die Wiederherstellung einzelner Elemente, Aufbewahrungsrichtlinien und verzögerte Datenbankkopien, um Hochverfügbarkeit, Ausfallsicherheit für Standorte und einen systemeigenen Exchange-Datenschutz bereitzustellen. Sowohl die Hochverfügbarkeitsplattform als auch der Exchange-Informationsspeicher und das ESE-Modul (Extensible Storage Engine) wurden erweitert und bieten mehr Verfügbarkeit, eine vereinfachte Verwaltung und die Möglichkeit zur Kosteneinsparung. Diese Verbesserungen umfassen:

  - **Verwaltete Verfügbarkeit**   Bei der verwalteten Verfügbarkeit werden eine interne Überwachung und wiederherstellungsorientierte Funktionen eng miteinander verzahnt, um Ausfälle zu vermeiden, Dienste proaktiv wiederherzustellen, ein Serverfailover automatisch einzuleiten oder den Administrator zu benachrichtigen, damit dieser entsprechende Maßnahmen ergreift. Der Schwerpunkt liegt eher auf der Überwachung und Verbesserung des Endbenutzererlebnisses als darauf, nur den Betrieb von Servern und Komponenten sicherzustellen, damit die Dienste ohne Unterbrechung verfügbar sind.

  - **Verwalteter Speicher**   Als verwalteter Speicher werden die neu gestalteten Informationsspeicherprozesse in Exchange 2013 bezeichnet. Der neue verwaltete Speicher ist in C\# geschrieben und eng in den Microsoft Exchange-Replikationsdienst (MSExchangeRepl.exe) integriert, um eine verbesserte Resilienz und damit eine höhere Verfügbarkeit bereitzustellen.

  - **Unterstützung für mehrere Datenbanken pro Datenträger**   Exchange 2013 bietet Verbesserungen, die Ihnen die Unterstützung mehrerer Datenbanken (eine Kombination aus aktiven und passiven Kopien) auf demselben Datenträger ermöglichen, wodurch größere Datenträger in Bezug auf Kapazität und E/A pro Sekunde effizienter genutzt werden können.

  - **Automatisches erneutes Seeding**   Ermöglicht das schnelle Wiederherstellen von Datenbankredundanz nach einem Datenträgerausfall. Wenn ein Datenträger ausfällt, wird die auf diesem Datenträger gespeicherte Datenbankkopie aus der aktiven Datenbankkopie auf einen Ersatzdatenträger auf demselben Server kopiert. Wenn mehrere Datenbankkopien auf dem fehlerhaften Datenträger gespeichert waren, kann für diese automatisch ein erneutes Seeding auf einem Ersatzdatenträger ausgeführt werden. Damit kann das erneute Seeding schneller ausgeführt werden, da die aktiven Datenbanken sich wahrscheinlich auf mehreren Servern befinden und die Daten parallel kopiert werden können.

  - **Automatische Wiederherstellung nach Speicherfehlern**   Eine Weiterentwicklung der in Exchange 2010 eingeführten Funktion, die es dem System erlaubt, nach Ausfällen mit Auswirkung auf Resilienz oder Redundanz eine automatische Wiederherstellung durchzuführen. Zusätzlich zur Fehlerprüfung von Exchange 2010 bietet Exchange 2013 weitere Wiederherstellungsfunktionen bei langen E/A-Zeiten, übermäßige Speicherbelegungen durch "MSExchangeRepl.exe" und für gravierende Fälle, bei denen das System sich in einem so schlechten Zustand befindet, dass keine Threads geplant werden können.

  - **Verbesserungen in Bezug auf verzögerte Kopien**   Verzögerte Kopien können sich mithilfe der automatischen Protokollwiedergabe jetzt bis zu einem gewissen Grad selbst verwalten. Verzögerte Kopien geben in verschiedenen Situationen automatisch Protokolldateien wieder, wie z. B. beim Wiederherstellen einzelner Seite und in Szenarien mit wenig Speicherplatz. Wenn das System ermittelt, dass für eine verzögerte Kopie ein Seitenpatching erforderlich ist, werden die Protokolle automatisch in die verzögerte Kopie wiedergegeben, um das Seitenpatching auszuführen. Verzögerte Kopien rufen die automatische Wiedergabefunktion auch auf, wenn ein Schwellenwert bezüglich zu wenig Speicherplatz erreicht wird und wenn die verzögerte Kopie während eines bestimmten Zeitraums die einzige verfügbare Kopie ist. Darüber hinaus nutzen verzögerte Kopien die Funktion "Sicherheitsnetz", mit der die Wiederherstellung oder Aktivierung wesentlich vereinfacht wird. *Sicherheitsnetz* ist der Name einer verbesserten Funktionalität in Exchange 2013, die auf dem Transportdumpster von Exchange 2010 basiert.

  - **Verbesserte Warnung zu einzelnen Kopien**   Die in Exchange 2010 eingeführte Warnung zu einzelnen Kopien wird nicht länger als separat geplantes Skript zur Verfügung gestellt. Es wurde in die Systemkomponenten für verwaltete Verfügbarkeit integriert und ist jetzt eine systemeigene Funktion von Exchange.

  - **Automatische Konfiguration von DAG-Netzwerken**   DAG-Netzwerke können basierend auf Konfigurationseinstellungen automatisch vom System konfiguriert werden. DAGs bieten nicht nur manuelle Konfigurationsoptionen, sondern können auch zwischen MAPI- und Replikationsnetzwerken unterscheiden und DAG-Netzwerke automatisch konfigurieren.

Weitere Informationen zu diesen beiden Funktionen finden Sie unter [Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md) und [Änderungen bei hoher Verfügbarkeit und Ausfallsicherheit im Vergleich zu früheren Versionen](changes-to-high-availability-and-site-resilience-over-previous-versions-exchange-2013-help.md)

## Verwaltung von Exchange-Arbeitsauslastungen

Bei Exchange-Arbeitsauslastungen handelt es sich um Exchange-Serverfunktionen, -protokolle oder -dienste, die explizit zum Zweck der Exchange-Systemressourcenverwaltung definiert wurden. Jede Exchange-Arbeitsauslastung nutzt Systemressourcen (z. B. CPU, Postfachdatenbankvorgänge oder Active Directory-Anforderungen), um Benutzeranforderungen oder Hintergrundaufgaben auszuführen. Beispiele für Exchange-Arbeitsauslastungen sind Outlook Web App, Exchange ActiveSync, Postfachmigrationen und der Postfach-Assistenten.

Es gibt zwei Möglichkeiten zum Verwalten von Exchange-Arbeitsauslastungen in Exchange 2013:

  - **Überwachen des Status bestimmter Systemressourcen**   Die Verwaltung von Arbeitsauslastungen basierend auf dem Status bestimmter Systemressourcen ist neu in Exchange 2013.

  - **Steuern der Nutzung von Ressourcen durch einzelne Benutzer**   Das Steuern der Nutzung von Ressourcen durch einzelne Benutzer war in Exchange 2010 möglich (und wurde als Benutzereinschränkung bezeichnet). Diese Funktionalität wurde für Exchange 2013 erweitert.

Weitere Informationen zu diesen Funktionen finden Sie unter [Verwaltung von Exchange-Arbeitsauslastungen](exchange-workload-management-exchange-2013-help.md).

