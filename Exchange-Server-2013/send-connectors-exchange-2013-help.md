---
title: 'Sendeconnectors: Exchange 2013 Help'
TOCTitle: Sendeconnectors
ms:assetid: 6aa19a12-c7b2-4eac-a8dc-9a4d26919ac5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998662(v=EXCHG.150)
ms:contentKeyID: 50475900
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Sendeconnectors

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-15_

In Microsoft Exchange Server 2013 steuert ein Sendeconnector die Übermittlung von ausgehenden Nachrichten an den empfangenden Server. Dieser wird auf Postfachservern konfiguriert, auf denen der Transportdienst ausgeführt wird. In den meisten Fällen wird ein Sendeconnector so konfiguriert, dass ausgehende E-Mails an einen Smarthost oder unter Verwendung von DNS direkt an einen Empfänger gesendet werden.

Exchange 2013-Postfachserver, auf denen der Transportdienst ausgeführt wird, erfordern Sendeconnectors, um Nachrichten an den nächsten Hop auf dem Weg zum Ziel zu übertragen. Auf Postfachservern erstellte Sendeconnectors werden in Active Directory gespeichert und stehen für alle Postfachserver in der Organisation zur Verfügung, auf denen der Transportdienst ausgeführt wird.


> [!IMPORTANT]
> Wenn Sie Exchange 2013 bereitstellen, können ausgehende Nachrichten erst übermittelt werden, wenn Sie einen Sendeconnector zum Routen ausgehender Mails an das Internet konfiguriert haben. Weitere Informationen finden Sie unter <A href="create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md">Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden</A>.



## Auswählen des Typs für einen Sendeconnector

Üblicherweise erstellen Sie einen Sendeconnector im Abschnitt **Nachrichtenfluss** der Exchange-Verwaltungskonsole. Wenn Sie einen neuen Sendeconnector erstellen, wählen Sie einen verfügbaren **Typ** aus, der Ihrem Verbindungsszenario entspricht. Der Typ legt fest, welche Standardberechtigungen für den Connector zugewiesen werden, und erteilt vertrauenswürdigen Sicherheitsprinzipalen diese Berechtigungen. Sicherheitsprinzipale beinhalten Benutzer, Computer und Sicherheitsgruppen.

Folgende Verfahren erläutern die Auswahl von bestimmten **Typen**: [Erstellen eines Sendeconnectors, um ausgehende E-Mails über einen Smarthost weiterzuleiten](create-a-send-connector-to-route-outbound-email-through-a-smart-host-exchange-2013-help.md) und [Erstellen eines Sendeconnectors nach Aktivierung von Transport Layer Security (TLS), um E-Mails an Partner zu senden](create-a-send-connector-to-send-email-to-a-partner-with-transport-layer-security-tls-applied-exchange-2013-help.md).

Wenn Sie lieber die Exchange-Verwaltungsshell als die Exchange-Verwaltungskonsole verwenden möchten, können Sie mithilfe des Cmdlets [New-SendConnector](https://technet.microsoft.com/de-de/library/aa998936\(v=exchg.150\)) einen Sendeconnector erstellen und einen Typ angeben.

## Neue Sendeconnectorfunktionen in Exchange 2013

Durch die Beziehung zwischen dem Front-End-Transport-Dienst auf Clientzugriffsservern und dem Transportdienst auf Postfachservern in Exchange 2013 geht auch ein neues Verhalten für Sendeconnectors einher. Sie können mithilfe des Parameters *FrontEndProxyEnabled* im Cmdlet [Set-SendConnector](https://technet.microsoft.com/de-de/library/aa998294\(v=exchg.150\)) einen Sendeconnector im Transportdienst eines Postfachservers so einrichten, dass ausgehende E-Mails über einen Front-End-Transport-Server am lokalen Active Directory-Standort geroutet werden. Auf diese Weise werden die Verfahren zum Routen von E-Mails aus dem Transportdienst konsolidiert. Unter [E-Mail-Routing](mail-routing-exchange-2013-help.md) finden Sie weitere Informationen zu Transportdiensten, Routingverhalten und Zielen in Exchange 2013. [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md) bietet eine Übersicht über die Transportpipeline und Beschreibungen jedes Transportdiensts.

Der Parameter *IsCoexistenceConnector* wird nicht mehr unterstützt. Wenn Sie eine Hybridumgebung konfigurieren möchten, in der die Postfächer zum Teil lokal und zum Teil in der Cloud gehostet werden, empfiehlt sich in den meisten Fällen die Verwendung des Assistenten für die Hybridkonfiguration.

*LinkedReceiveConnector* wird nicht mehr unterstützt. Dieser Parameter wurde zum Erstellen von Connectors verwendet, die beispielsweise Nachrichten an den Antispamdienst eines Drittanbieters routen konnten. Nun werden E-Mails an den Antispamdienst in den meisten Fällen unter Verwendung des MX-Eintrags geroutet, und verknüpfte Connectors sind nicht erforderlich.

Die standardmäßige maximale Nachrichtengröße, die durch den Parameter *MaxMessageSize* angegeben wird, wurde von 10 MB auf 25 MB erhöht. Unter [Set-SendConnector](https://technet.microsoft.com/de-de/library/aa998294\(v=exchg.150\)) finden Sie weitere Informationen zum Festlegen von Parametern für einen Sendeconnector.

*TlsCertificateName* wurde hinzugefügt. Er wird zum Authentifizieren des lokalen Zertifikats für ausgehende Verbindungen und zum Minimieren des Risikos betrügerischer Zertifikate verwendet.

