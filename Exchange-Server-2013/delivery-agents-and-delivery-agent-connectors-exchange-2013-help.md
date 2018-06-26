---
title: 'Zustellungs-Agents und Zustellungs-Agent-Connectors: Exchange 2013 Help'
TOCTitle: Zustellungs-Agents und Zustellungs-Agent-Connectors
ms:assetid: 38c942ee-b59d-47ec-87eb-bebad441ada5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638118(v=EXCHG.150)
ms:contentKeyID: 50475327
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zustellungs-Agents und Zustellungs-Agent-Connectors

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Ein Zustellungs-Agent kann Nachrichten aus Ihrer SMTP-Exchange-Serverumgebung an ein System zustellen, in dem das SMTP-Protokoll nicht verwendet wird. Jeder Zustellungs-Agent ist einem Zustellungs-Agent-Connector zugeordnet, der an den Zustellungs-Agent weitergeleitete Nachrichten für die Verarbeitung und Zustellung an das Nicht-SMTP-Gerät oder -System in eine Warteschlange einreiht.


> [!TIP]
> Während die Architektur mit fremden Connectors in Microsoft Exchange 2013 erhalten bleibt, empfiehlt es sich, Nachrichten nach Möglichkeit mit Zustellungs-Agents an Nicht-SMTP-Systeme weiterzuleiten. Die wichtigsten Gründe hierfür sind, dass Sie die Warteschlangenverwaltung für Nachrichten einsetzen können, dass keine Dateiübertragung an ein Ablageverzeichnis verwaltet werden muss, und dass die Nachrichtenzustellung überprüft werden kann.



**Inhalt**

Funktion und Vorteile von Zustellungs-Agents

Hinzufügen von Zustellungs-Agents zu Ihrer Organisation

Zustellungs-Agent-Connectors

Standardmäßiger Zustellungs-Agent-Connector für Textnachrichten

## Funktion und Vorteile von Zustellungs-Agents

Ein Zustellungs-Agent ist eine im Transportdienst eines Postfachservers installierte Komponente, die folgende Aufgaben ausführen kann:

  - Herstellen einer Verbindung an das fremde System für die Nachrichtenzustellung.

  - Abrufen von Nachrichten aus den Warteschlangen auf den Postfachservern.

  - Zustellen von Nachrichten an das fremde System.

  - Bereitstellen einer Bestätigung für jede erfolgreiche Nachrichtenzustellung.

Während die Architektur mit fremden Connectors in Microsoft Exchange Server 2013 erhalten bleibt, empfiehlt es sich, Nachrichten nach Möglichkeit mit Zustellungs-Agents an Nicht-SMTP-Systeme weiterzuleiten. Zustellungs-Agents bieten die folgenden Vorteile:

  - Sie ermöglichen eine Warteschlangenverwaltung von Nachrichten, die an fremde Systeme weitergeleitet werden.

  - Da die Nachrichten nicht länger in das Dateisystem geschrieben und daraus gelesen werden müssen, wird die Leistung bei der Nachrichtenzustellung verbessert.

  - Sie bieten Zugriff auf Nachrichteneigenschaften mit umfassenden Ereignissen für Agent-Entwickler.

  - Die Entwicklungszeit eines Zustellungs-Agents ist kürzer als die Implementierung eines fremden Connectors, da der Zustellungs-Agent die Nachrichtendarstellungs- und -verwaltungsfunktionen von Exchange verwenden kann.

  - Sie kontrollieren nicht lediglich, ob die Nachrichten in das Ablageverzeichnis geschrieben wurden, sondern können prüfen, ob die Nachrichten an das fremde System zugestellt wurden.

  - Die Verwendung von Zustellungs-Agent-Connectors ermöglicht eine SLA-Analyse (Service Level Agreement, Vereinbarung zum Servicelevel), da es möglich ist, die Latenz bei der Nachrichtenzustellung an das fremde System zu verfolgen.

## Hinzufügen von Zustellungs-Agents zu Ihrer Organisation

Zur Verwendung eines Zustellungs-Agents in Ihrer Organisation müssen Sie folgende Schritte durchführen:

1.  Erwerben Sie den Zustellungs-Agent. In der Regel werden Zustellungs-Agents von Drittanbietern geschrieben. Zum Lieferumfang von Exchange 2013 gehört standardmäßig ein Zustellungs-Agent-Connector: der Zustellungs-Agent-Connector für Textnachrichten.

2.  Installieren Sie den Zustellungs-Agent im Transportdienst auf den Postfachservern, die als Quellserver für die Zustellungs-Agent-Connectors dienen.

3.  Erstellen Sie einen Zustellungs-Agent-Connector für das spezifische Protokoll.

Nach Abschluss all dieser Schritte werden Nachrichten an fremde Systeme über die Zustellungs-Agent-Connectors geleitet und vom Zustellungs-Agent verarbeitet.

Unter [Microsoft.Exchange.Data.Transport.Delivery Namespace](https://go.microsoft.com/fwlink/?linkid=262690) finden Sie weitere Informationen zum Entwickeln eines Zustellungs-Agents.

## Zustellungs-Agent-Connectors

Ein Zustellungs-Agent-Connector in Exchange 2013 ähnelt dem in Exchange 2010 eingeführten Zustellungs-Agent-Connector. Er leitet Nachrichten weiter, die an fremde Systeme ohne SMTP-Protokoll gerichtet sind. Wenn eine Nachricht an den Zustellungs-Agent-Connector weitergeleitet wird, führt der zugeordnete Zustellungs-Agent die Inhaltskonvertierung und die Nachrichtenzustellung durch. In der Regel werden Zustellungs-Agents von einem Drittanbieter erstellt und sind für die Zusammenarbeit mit einem Zustellungs-Agent-Connector in Ihrer Organisation konfiguriert.

Es ist nicht möglich, einen Zustellungs-Agent-Connector in der Exchange-Verwaltungskonsole zu erstellen. Stattdessen erstellen Sie einen Zustellungs-Agent-Connector in der Exchange-Verwaltungsshell. Sie verwenden hierzu das Cmdlet [New-DeliveryAgentConnector](https://technet.microsoft.com/de-de/library/dd351063\(v=exchg.150\)) und bearbeiten die Eigenschaften des Zustellungs-Agent-Connectors mit [Set-DeliveryAgentConnector](https://technet.microsoft.com/de-de/library/dd351159\(v=exchg.150\)). Sie können einen oder mehrere Hostpostfachserver für den Connector angeben, indem Sie den optionalen Parameter *SourceTransportServers* verwenden.

## Standardmäßiger Zustellungs-Agent-Connector für Textnachrichten

Sie können den Zustellungs-Agent-Connector für Textnachrichten zum Weiterleiten von Nachrichten an mobile Geräte verwenden. Führen Sie auf dem Exchange-Server `Get-DeliveryAgentConnector | fl` aus, um den Connector und alle zugehörigen Parameter anzuzeigen. Beachten Sie, dass *DeliveryProtocol* auf `MOBILE` festgelegt ist.

