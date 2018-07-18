---
title: 'Outlook Anywhere: Exchange 2013 Help'
TOCTitle: Outlook Anywhere
ms:assetid: 9026d461-ec6a-4ef5-ba9d-de33030858f3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123741(v=EXCHG.150)
ms:contentKeyID: 50476158
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Outlook Anywhere

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In Microsoft Exchange Server 2013 ermöglicht es die Outlook Anywhere-Funktion, die früher als "RPC-über-HTTP" bekannt war, dass Clients, die MicrosoftOutlook 2013, Outlook 2010 oder Outlook 2007 verwenden, von außerhalb des Unternehmensnetzwerks oder über das Internet mithilfe derWindows-Netzwerkkomponente "RPC-über-HTTP" eine Verbindung zu ihren Exchange-Servern herstellen können. In diesem Thema wird das Feature Outlook Anywhere beschrieben, und die Vorteile der Verwendung von Outlook Anywhere werden aufgelistet.

**Inhalt**

Outlook Anywhere und Exchange 2013

Vorteile der Verwendung von Outlook Anywhere

Bereitstellen von Outlook Anywhere

Verwalten von Outlook Anywhere

Outlook Anywhere – Koexistenz

Testen der Outlook Anywhere-Konnektivität

## Outlook Anywhere und Exchange 2013

Die Windows-Proxykomponente "RPC-über-HTTP", die von Outlook Anywhere-Clients zum Herstellen von Verbindungen verwendet wird, schließt RPCs (Remote Procedure Calls, Remoteprozeduraufrufe) in eine HTTP-Schicht ein. Dadurch kann der Datenverkehr Netzwerkfirewalls passieren, ohne dass RPC-Ports geöffnet sein müssen. In Exchange 2013 ist diese Funktion standardmäßig aktiviert, weil Exchange 2013 keine direkte RPC-Verbindung zulässt.

## Vorteile der Verwendung von Outlook Anywhere

Outlook Anywhere bietet Clients, die Outlook 2013, Outlook 2010 oder Outlook 2007 für den Zugriff auf Ihre Exchange-Messaginginfrastruktur verwenden, die folgenden Vorteile:

  - Benutzer verfügen über den Remotezugriff auf Exchange-Server über das Internet.

  - Sie können dieselbe URL und denselben Namespace wie für Outlook Web App und MicrosoftExchange ActiveSync verwenden.

  - Sie können dasselbe SSL-Serverzertifikat (Secure Sockets Layer) wie für Outlook Web App und Exchange ActiveSync verwenden.

  - Nicht authentifizierte Anforderungen von Outlook können nicht auf Exchange-Server zugreifen.

  - Sie müssen für den Zugriff auf Exchange-Server über das Internet keine VPN-Verbindung (Virtual Private Network, virtuelles privates Netzwerk) verwenden.

  - Wenn Sie bereits Outlook Web App mit SSL oder Exchange ActiveSync mit SSL verwenden, müssen Sie keine weiteren Ports für das Internet öffnen.

  - Sie können die End-to-End-Clientkonnektivität für Outlook Anywhere und TCP-basierte Verbindungen mithilfe des Cmdlets **Test-OutlookConnectivity** testen.

## Bereitstellen von Outlook Anywhere

In Exchange 2013 ist Outlook Anywhere standardmäßig aktiviert, weil die gesamte Outlook-Konnektivität über Outlook Anywhere bereitgestellt wird. Die einzige Aufgabe, die Sie nach der Bereitstellung ausführen müssen, um Outlook Anywhere erfolgreich verwenden zu können, ist die Installation eines gültigen SSL-Zertifikats auf Ihrem Clientzugriffsserver. Postfachserver in Ihrer Organisation benötigen nur das standardmäßige selbstsignierte SSL-Zertifikat.

## Verwalten von Outlook Anywhere

Outlook Anywhere kann mithilfe der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell verwaltet werden.

## Outlook Anywhere – Koexistenz

Wenn Sie vorhaben, Exchange 2013 in einem Koexistenzszenario mit früheren Versionen von Exchange Server zu installieren, sind in Ihrer Organisation ggf. noch Outlook 2003-Clients vorhanden. Outlook 2003 ist kein unterstützter Client für Exchange 2013.

Bevor Sie Ihren Namespace nach Exchange 2013 verschieben, müssen Sie sicherstellen, dass alle Outlook-Clients einem Upgrade auf die unterstützte Mindestversion unterzogen wurden. Outlook 2007 oder höher ist für eine Outlook Anywhere-Verbindung mit Exchange 2013 erforderlich, selbst wenn sich das Zielpostfach weiter in Exchange 2007 oder Exchange 2010 befindet.

Wenn Sie derzeit Outlook Anywhere in Ihrer Exchange 2007- oder Exchange 2010-Umgebung verwenden, müssen Sie Outlook Anywhere auf allen Exchange 2007-/2010-Clientzugriffsservern in Ihrer Organisation aktivieren und konfigurieren, damit Ihr Exchange 2013-Clientzugriffsserver Verbindungen an die Exchange 2007-/2010-Server weiterleiten kann. Wenn Sie derzeit jedoch nicht Outlook Anywhere in Ihrer Exchange 2007- oder Exchange 2010-Umgebung verwenden und Sie die Verwendung auch nicht beginnen möchten, müssen Sie Outlook Anywhere nicht in der Legacyumgebung aktivieren. Anweisungen zum Aktivieren von Outlook Anywhere für Clientzugriffsserver, die auf Exchange 2007-Servern ausgeführt werden, finden Sie unter[Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=510497).. Anweisungen zum Aktivieren von Outlook Anywhere für Clientzugriffsserver, die auf Exchange 2010-Servern ausgeführt werden, finden Sie unter [Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=510502).

Stellen Sie sicher, dass Sie beim Aktivieren von Outlook Anywhere für den Clientzugriffsserver für die IIS-Authentifizierung NTLM auswählen.

Konfigurieren Sie abschließend den externen Hostnamen für Outlook Anywhere, sodass er auf den Hostnamen für Exchange 2013 Outlook Anywhere verweist. Anweisungen für Exchange Server 2007 finden Sie unter [Konfigurieren eines externen Hostnamens für Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=510530). Anweisungen für Exchange Server 2010 finden Sie unter [Konfigurieren eines externen Hostnamens für Outlook Anywhere](https://go.microsoft.com/fwlink/p/?linkid=510531).

## Testen der Outlook Anywhere-Konnektivität

Sie können die End-to-End-Konnektivität eines Outlook-Clients testen, indem Sie einen der folgenden Schritte ausführen:

  - Führen Sie das Cmdlet **Test-OutlookConnectivity** aus. Das Cmdlet testet auf Outlook Anywhere-Verbindungen (RPC-über-HTTP). Führt die Durchführung des Cmdlet-Tests zu einem Fehler, wird der fehlerhafte Schritt in der Ausgabe aufgeführt. Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Test-OutlookConnectivity](https://technet.microsoft.com/de-de/library/dd638082\(v=exchg.150\)).

  - Führen Sie den Outlook Anywhere-Verbindungstest mithilfe der Exchange-Remoteverbindungsuntersuchung (Exchange Remote Connectivity Analyzer, ExRCA) aus. Wenn Sie diesen Test ausführen, erhalten Sie eine ausführliche Zusammenfassung, in der angegeben ist, wo der Fehler im Test aufgetreten ist und mit welchen Schritten Sie die Probleme lösen können. Weitere Informationen finden Sie unter [Exchange-Remoteverbindungsuntersuchung](exchange-remote-connectivity-analyzer-exchange-2013-help.md).

Beide Tests versuchen, sich über Outlook Anywhere anzumelden, nachdem sie die Servereinstellungen vom AutoErmittlungsdienst abgerufen haben. Die End-to-End-Überprüfung umfasst Folgendes:

  - Testen der AutoErmittlungskonnektivität

  - Überprüfen von DNS

  - Überprüfen von Zertifikaten (ob der Zertifikatsname mit der Website übereinstimmt, das Zertifikat abgelaufen oder vertrauenswürdig ist)

  - Überprüfen, ob die Firewall ordnungsgemäß eingerichtet ist (ExRCA überprüft die Gesamteinrichtung der Firewall. Das Cmdlet prüft die Windows-Firewallkonfiguration.)

  - Bestätigen der Clientkonnektivität durch Anmelden am Benutzerpostfach

