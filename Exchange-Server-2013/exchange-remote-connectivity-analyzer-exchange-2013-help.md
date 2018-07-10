---
title: 'Exchange-Remoteverbindungsuntersuchung: Exchange 2013 Help'
TOCTitle: Exchange-Remoteverbindungsuntersuchung
ms:assetid: dd26698e-d00c-47f5-a7aa-c3894fe86c75
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff701693(v=EXCHG.150)
ms:contentKeyID: 50476883
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange-Remoteverbindungsuntersuchung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-09-22_

Mithilfe der MicrosoftExchange-Remoteverbindungsuntersuchung (ExRCA) kann die ordnungsgemäße Konfiguration der Konnektivität für Ihre Exchange-Server sichergestellt und eine Diagnose von Konnektivitätsproblemen durchgeführt werden. Bei Problemen kann dieses Tool Ihnen auch helfen, diese zu bestimmen und zu beheben. Auf der Website der Remoteverbindungsuntersuchung können Tests für MicrosoftExchange ActiveSync, Exchange-Webdienste, MicrosoftOutlook und Internet-E-Mail ausgeführt werden.

## Tests der Remoteverbindungsuntersuchung

Sie können mehrere Tests mithilfe von ExRCA ausführen. Die folgenden Tests können mit Exchange 2007 und höher verwendet werden.

  - Exchange ActiveSync

  - Exchange-Webdienste

  - Outlook

  - Internet-E-Mail

## Exchange ActiveSync-Tests

Folgende Tests für Exchange ActiveSync können ausgeführt werden:

  - **Exchange ActiveSync:**  Bei diesem Test werden die Schritte eines mobilen Geräts beim Herstellen einer Verbindung mit einem Exchange-Server unter Verwendung von Exchange ActiveSync simuliert.

  - **Exchange ActiveSync-AutoErmittlung:**  Bei diesem Test werden die Schritte überprüft, die ein Exchange ActiveSync-Gerät zum Abrufen von Einstellungen vom AutoErmittlungsdienst ausführt.

## Verbindungstests für die Exchange-Webdienste

Mit den Tests für die Exchange-Webdienste werden die Einstellungen für viele der Exchange-Webdienste überprüft. Sie können die folgenden Tests für Exchange-Webdienste ausführen:

  - **Synchronisierung, Benachrichtigung, Verfügbarkeit und automatische Antworten:**  Bei diesen Tests werden viele grundlegende Aufgaben der Exchange-Webdienste untersucht, um zu prüfen, ob sie wie gewünscht ausgeführt werden. Dies ist hilfreich für IT-Administratoren, die Probleme mit dem externen Zugriff über Entourage EWS oder andere Webdienstclients beheben möchten.

  - **Dienstkontozugriff (Entwickler):**  Der Test überprüft, ob ein Dienstkonto auf ein angegebenes Postfach zugreifen, Elemente in diesem Postfach erstellen und löschen und mittels Exchange-Identitätswechsels auf das Postfach zugreifen kann. Dieser Test ist hauptsächlich für Anwendungsentwickler gedacht, die die Fähigkeit des Zugriffs auf Postfächer mit alternativen Anmeldeinformationen testen möchten.

## Microsoft Office Outlook-Konnektivitätstests

Zum Überprüfen der Outlook-Konnektivität können Sie die folgenden Tests ausführen:

  - **Outlook Anywhere (RPC über HTTP):**  Der Test zeigt die Schritte, die Outlook zur Herstellen der Verbindung über Outlook Anywhere (RPC über HTTP) durchführt.

  - **Outlook-AutoErmittlung:**  Bei diesem Test werden die Schritte überprüft, die Outlook zum Abrufen von Einstellungen vom AutoErmittlungsdienst ausführt. Bei diesem Test wird keine wirkliche Verbindung mit einem Postfach hergestellt.

## Internet-E-Mail-Tests

Für Internet-E-Mail- können folgende Tests ausgeführt werden:

  - **Eingehende SMTP**-**E-Mail:**  Bei diesem Test werden die Schritte durchlaufen, die ein Internet-E-Mail-Server zum Senden eingehender SMTP-E-Mail an Ihre Domäne ausführt.

  - **Ausgehende SMTP-E-Mail:**  Bei diesem Test werden die IP-Adresseinstellungen für ausgehende Verbindungen für bestimmte Anforderungen überprüft. Dazu zählen Prüfungen von Reverse-DNS, Sender ID und RBL.

  - **POP-E-Mail:**  Bei diesem Test werden die Schritte durchlaufen, die ein E-Mail-Client zum Verbinden mit einem Postfach über POP3 ausführt.

  - **IMAP-E-Mail:**  Bei diesem Test werden die Schritte durchlaufen, die ein E-Mail-Client zum Verbinden mit einem Postfach über IMAP ausführt.

