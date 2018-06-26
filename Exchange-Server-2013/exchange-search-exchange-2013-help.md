---
title: 'Exchange-Suche: Exchange 2013 Help'
TOCTitle: Exchange-Suche
ms:assetid: 967e2a13-4e54-486a-ac22-08768674abbb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232132(v=EXCHG.150)
ms:contentKeyID: 52062898
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange-Suche

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-09-17_

Angesichts immer größer werdender Postfächer und Datenmengen, die in Postfächern in Form von Nachrichten und Anlagen gespeichert werden, ist es für Benutzer entscheidend, dass sie in der Lage sind, die erforderlichen Nachrichten schnell zu suchen und zu finden. Die [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md) hilft Ihnen, die Verwendung von PST-Dateien zu verringern oder einzustellen, indem alte Elemente oder Elemente, auf die selten zugegriffen wird, in das Archiv verschoben werden. Dies führt dazu, dass ein Benutzer mehr Postfachdaten speichert. Außerdem wird dadurch die Suche über die primären und Archivpostfächer des Benutzers zu einem wichtigen Produktivitätstool. Die [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md) ermöglicht autorisierten Benutzern das Durchsuchen von Inhalten in Postfächern in sowohl lokalen als auch cloudbasierten Exchange-Organisationen, um eDiscovery-Anforderungen erfüllen und Überprüfungen von Vorschriften sowie interne Untersuchungen durchführen zu können. Für die Compliance-eDiscovery-Suche werden auch die von der Exchange-Suche erstellten Inhaltsindizes verwendet.

Die Exchange-Suche unterscheidet sich von der in Exchange Server 2003 verfügbaren Volltextindizierung. Es wurden hinsichtlich Leistung, Inhaltsindizierung und Suche Verbesserungen vorgenommen. Neue Elemente werden in der Transportpipeline nahezu unverzüglich nach ihrer Erstellung oder der Zustellung an das Postfach indiziert, wodurch Benutzer Postfachdaten schnell, konstant und zuverlässiger durchsuchen können. Die Inhaltsindizierung ist standardmäßig aktiviert, und es ist kein einleitendes Setup und keine Konfiguration erforderlich.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit der Exchange-Suche gibt? Weitere Informationen finden Sie unter [Exchange-Suchverfahren](exchange-search-procedures-exchange-2013-help.md).

## Neue Funktionen

In Exchange 2013 weist die Exchange-Suche die folgenden Änderungen auf:

  - Das zugrunde liegende Inhaltsindizierungsmodul wurde durch Microsoft Search Foundation ersetzt. Diese Lösung bietet Leistungs- und Funktionsverbesserungen und dient als gemeinsames zugrunde liegendes Inhaltsindizierungsmodul in Exchange und SharePoint. Die Verschlüsselungsschnittstelle bleibt jedoch identisch.

  - Search Foundation verarbeitet standardmäßig die gängigsten Dateiformate in E-Mail-Anlagen. Sie müssen für die Exchange-Suche keine Microsoft Office Filter Packs mehr installieren. Unter [Von der Exchange-Suche indizierte Dateiformate](file-formats-indexed-by-exchange-search-exchange-2013-help.md) finden Sie eine Liste der von der Exchange-Suche verarbeiteten Dateiformate.
    
    Durch Installieren von IFilters können Sie wie in Exchange 2010 weitere Dateiformate hinzufügen.

  - Die Inhaltsindizierung ist effizienter, da Nachrichten nun in der Transportpipeline verarbeitet werden. Das Ergebnis ist, dass an mehrere Empfänger oder Verteilergruppen adressierte Nachrichten nur einmal verarbeitet werden. An die Nachricht werden Anmerkungsdaten angefügt, die die Inhaltsindizierung wesentlich beschleunigen und weniger Ressourcen benötigen.

