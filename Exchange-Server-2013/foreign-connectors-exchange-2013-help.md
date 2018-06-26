---
title: 'Fremde Connectors: Exchange 2013 Help'
TOCTitle: Fremde Connectors
ms:assetid: 21c6a7a9-f4d2-4359-9ac9-930701b63a4e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996779(v=EXCHG.150)
ms:contentKeyID: 50475338
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Fremde Connectors

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-25_

Ein fremder Connector übermittelt Nachrichten an einen Server oder ein fremdes System, der bzw. das als primären Transportmechanismus nicht SMTP verwendet. Ein Beispiel ist ein Faxgatewayserver. Ein fremder Connector verwendet ein lokales oder freigegebenes Ablageverzeichnis, um ausgehende Nachrichten mittels Dateiübertragung an das fremde System zu übermitteln. Fremde Connectors werden im Transportdienst eines Microsoft Exchange Server 2013-Postfachservers erstellt.

Fremde Gatewayserver können Nachrichten unter Verwendung des PICKUP- oder Wiedergabeverzeichnisses an die Exchange 2013-Organisation senden. Diese Verzeichnisse befinden sich im Transportdienst eines Postfachservers. Ordnungsgemäß formatierte E-Mails, die Sie in diese beiden Verzeichnisse kopieren, werden zur Zustellung an ein Exchange-Postfach übermittelt.


> [!TIP]
> Wenn ausgehende Nachrichten an ein Nicht-SMTP-System gesendet werden müssen, empfehlen sich üblicherweise Zustellungs-Agent-Connectors, weil Nachrichten in einer Warteschlange verwaltet werden können, sie nicht in das Dateisystem geschrieben werden müssen, und weil es weitere Vorteile gibt. Im Thema <A href="delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md">Zustellungs-Agents und Zustellungs-Agent-Connectors</A> finden Sie weitere Informationen.



## Weitere Informationen

[Erstellen eines fremden Connectors zum Übermitteln von Nachrichten an ein Nicht-SMTP-Faxgateway](create-a-foreign-connector-to-deliver-messages-to-a-non-smtp-fax-gateway-exchange-2013-help.md)

[Zustellungs-Agents und Zustellungs-Agent-Connectors](delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md)

[New-ForeignConnector](https://technet.microsoft.com/de-de/library/aa996310\(v=exchg.150\))

[Set-ForeignConnector](https://technet.microsoft.com/de-de/library/bb123789\(v=exchg.150\))

