---
title: 'Warteschlangenanzeige: Exchange 2013 Help'
TOCTitle: Warteschlangenanzeige
ms:assetid: db892f88-5c13-4607-a38c-8845b35ab8b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124789(v=EXCHG.150)
ms:contentKeyID: 50476881
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Warteschlangenanzeige

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-09-25_

Die Warteschlangenanzeige ist ein Microsoft Management Console-Snap-In, das auf einem Postfachserver oder auf dem Edge-Transport-Server installiert wird. Die Warteschlangenanzeige befindet sich in der Exchange Toolbox-Konsole im Abschnitt **Nachrichtenflusstools**. Mit diesem Tool können Sie Informationen zu Warteschlangen auf einem Transportserver und zu den in diesen Warteschlangen vorhandenen Nachrichten anzeigen sowie Verwaltungsaktionen für Warteschlangen und E-Mail-Elemente ausführen. Die Warteschlangenanzeige ist für die Problembehebung bei der Nachrichtenübermittlung und das Identifizieren von Spam nützlich.

Wenn Sie die Warteschlangenanzeige zum Verwalten von Warteschlangen verwenden, beachten Sie Folgendes:

  - Sie müssen eine Verbindung mit einem Transportserver herstellen. Standardmäßig öffnet die Warteschlangenanzeige die Warteschlangendatenbank auf dem Server, auf dem Sie die Warteschlangenanzeige geöffnet haben. Sie können aber auch eine Verbindung mit anderen Servern herstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Server in der Warteschlangenanzeige](connect-to-a-server-in-queue-viewer-exchange-2013-help.md).

  - Die Liste der Warteschlangen und Nachrichten kann, je nach aktuellem E-Mail-Fluss, umfangreich sein und ändert sich, wenn Nachrichten beim Server ein- und ausgehen. Sie können die Optionen für die Warteschlangenanzeige konfigurieren, um das Aktualisierungsintervall für die Liste der Warteschlangen und Nachrichten sowie die Anzahl der auf jeder Seite angezeigten Elemente zu steuern. Weitere Informationen finden Sie unter [Festlegen der Optionen für die Warteschlangenanzeige](set-queue-viewer-options-exchange-2013-help.md).

  - Sie können einen Filter erstellen, um die bestimmte Menge von Warteschlangen oder Nachrichten anzuzeigen, die Sie überwachen möchten. Nachdem Sie die zu überwachenden Warteschlangen und Nachrichten ermittelt haben, können Sie die Eigenschafteninformationen für diese Warteschlangen und Nachrichten anzeigen. Diese Informationen sind bei der Behebung von Ursachen von Problemen des E-Mail-Flusses nützlich. Weitere Informationen finden Sie unter [Warteschlangenfilter](queue-filters-exchange-2013-help.md) und [Nachrichtenfilter](message-filters-exchange-2013-help.md).

  - Über den Link **Liste exportieren** im Aktionsbereich können Sie die Liste der Warteschlangen oder eine Liste von Nachrichten exportieren. Weitere Informationen finden Sie unter [Exportieren von Listen aus der Warteschlangenanzeige](export-lists-from-queue-viewer-exchange-2013-help.md).

