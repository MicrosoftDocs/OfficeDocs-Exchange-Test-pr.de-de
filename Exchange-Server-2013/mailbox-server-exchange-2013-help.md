---
title: 'Postfachserver: Exchange 2013 Help'
TOCTitle: Postfachserver
ms:assetid: 1aacc1c9-c81b-47d4-b222-ee73956cf968
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150491(v=EXCHG.150)
ms:contentKeyID: 50475120
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Postfachserver

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-19_

In Microsoft Exchange Server 2010 wurden sowohl Postfachdatenbanken als auch Datenbanken für öffentliche Ordner über die Postfachserverrolle gehostet. Zudem wurde über diese Serverrolle Speicherplatz für E-Mails bereitgestellt. In Exchange Server 2013 umfasst die Postfachserverrolle nun zusätzlich die Clientzugriffsprotokolle, den Transportdienst, Postfachdatenbanken und Unified Messaging-Komponenten.

In Exchange 2013 interagiert die Postfachserverrolle bei folgendem Vorgang direkt mit Active Directory, dem Clientzugriffsserver und Microsoft Outlook-Clients:

  - Der Postfachserver verwendet LDAP, um über Active Directory auf Konfigurationsinformationen des Empfängers, Servers und der Organisation zuzugreifen.

  - Der Clientzugriffsserver sendet Anforderungen von Clients an den Postfachserver und gibt Daten vom Postfachserver an die Clients zurück. Der Clientzugriffserver greift ebenfalls auf die Dateien des Offlineadressbuchs (OAB) auf dem Postfachserver unter Verwendung der NetBIOS-Dateiabfrage zu. Der Clientzugriffsserver sendet Nachrichten, Frei/Gebucht-Daten, Clientprofileinstellungen und Daten des Offlineadressbuchs vom Client an den Postfachserver bzw. vom Postfachserver an den Client.

  - Outlook-Clients innerhalb Ihrer Firewall greifen auf den Clientzugriffsserver zu, um Nachrichten zu senden und zu empfangen. Outlook-Clients außerhalb der Firewall können über Outlook Anywhere (unter Verwendung der RPC-über-HTTP-Proxykomponente) auf den Clientzugriffsserver zugreifen.

  - Der Zugriff auf Postfächer für öffentliche Ordner kann unabhängig davon, ob der Client sich außerhalb oder innerhalb der Firewall befindet, über die RPC-über-HTTP-Komponente erfolgen.

  - Der Nur-Administrator-Computer ruft Active Directory-Topologieinformationen vom Microsoft Exchange Active Directory-Topologiedienst ab. Er ruft ebenfalls Informationen zur Richtlinie für E-Mail-Adressen und zur Adressliste ab.

  - Der Clientzugriffsserver verwendet LDAP oder NSPI (Name Service Provider Interface), um den Active Directory-Server zu kontaktieren, und ruft Active Directory-Informationen der Benutzer ab.

**Postfach- und Clientzugriffsserver – Interaktion und Architektur**

![Clientzugriffs- und Postfachserverinteraktion](images/JJ150491.d14577bf-14f9-40fa-bd49-a92932eb003a(EXCHG.150).gif "Clientzugriffs- und Postfachserverinteraktion")

Weitere Einzelheiten finden Sie im Abschnitt "Exchange 2013-Architektur" in [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).

## Neue Postfachfunktionen

In der folgenden Liste finden Sie eine kurze Beschreibung einiger neuer und verbesserter Funktionen im Zusammenhang mit der Postfachserverrolle für Exchange 2013:

  - Weiterentwicklung der Database Availability Group (DAG) aus Exchange 2010:
    
      - Der Transaktionsprotokollcode wurde für ein schnelles Failover mit großer Prüfpunkttiefe für passive Datenbankkopien umgestaltet.
    
      - Zur Unterstützung einer verbesserten Standortausfallsicherheit können Server an verschiedenen Standorten platziert werden.

  - Jetzt werden einige Clientzugriffskomponenten, die Transportkomponenten und die Unified Messaging-Komponenten von Exchange 2013 gehostet.

  - Der Exchange-Informationsspeicher wurde basierend auf verwaltetem Code neu erstellt, um die Leistung durch eine zusätzliche Senkung der E/A-Last und höhere Zuverlässigkeit zu verbessern.

  - Jede Exchange 2013-Datenbank wird nun mit einem eigenen Prozess ausgeführt.

  - Die Infrastruktur für die Suche in mehreren Postfächern aus Exchange 2010 wurde durch eine intelligente Suche ersetzt.

## Sichern von Postfachservern

Standardmäßig ist die HTTP-, Microsoft Exchange ActiveSync-, POP3- und IMAP4-Kommunikation zwischen den Postfachservern und anderen Exchange-Serverrollen, Domänencontrollern und globalen Katalogservern verschlüsselt. Stellen Sie zusätzlich sicher, dass Ihre Postfachserver nicht für das Internet zugänglich sind.

## Weitere Informationen

[Unified Messaging](unified-messaging-exchange-2013-help.md)

[Nachrichtenübermittlung](mail-flow-exchange-2013-help.md)

[Hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-exchange-2013-help.md)

[Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md)

[Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md)

[Verwalten von Postfachdatenbanken in Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md)

[Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md)

[Empfänger](recipients-exchange-2013-help.md)

[Zusammenarbeit](collaboration-exchange-2013-help.md)

