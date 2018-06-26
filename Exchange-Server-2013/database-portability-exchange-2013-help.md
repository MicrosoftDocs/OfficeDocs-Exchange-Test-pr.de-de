---
title: 'Datenbankportabilität: Exchange 2013 Help'
TOCTitle: Datenbankportabilität
ms:assetid: 387b727a-ce51-4910-b5c4-613c693fa5bd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876873(v=EXCHG.150)
ms:contentKeyID: 51409280
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Datenbankportabilität

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-01-30_

Die Datenbankportabilität ist eine Funktion, mit der eine Microsoft Exchange Server 2013-Postfachdatenbank auf einen beliebigen anderen Postfachserver in derselben Organisation verschoben oder dort eingebunden werden kann, auf dem Exchange 2013 mit Datenbanken derselben Datenbankschemaversion ausgeführt wird. Postfachdatenbanken aus früheren Versionen von Exchange können nicht auf einen Postfachserver verschoben werden, der Exchange 2013 ausführt. Mithilfe der Datenbankportabilität wird die Zuverlässigkeit verbessert, indem auf verschiedene fehleranfällige manuelle Schritte bei den Wiederherstellungsprozessen verzichtet werden kann. Darüber hinaus verringert die Datenbankportabilität die Gesamtwiederherstellungsdauer für verschiedene Fehlerszenarien.

Wenn Datenbankportabilität zur Wiederherstellung einer Postfachdatenbank verwendet wird, müssen die Version des Betriebssystems und die Exchange Server-Version auf den Quell- und Ziel-Exchange-Servern übereinstimmen. Beispiel: Wenn eine Exchange 2013-Postfachdatenbank auf einem Server unter Windows Server 2012 bereitgestellt wurde, funktioniert Datenbankportabilität nur, wenn die Datenbank auch zu einem Server unter Windows Server 2012 und Exchange 2013 migriert wird.

Weitere Informationen über die Durchführung einer Datenbankwiederherstellung unter Verwendung der Funktion für die Datenbankportabilität finden Sie unter [Verschieben einer Postfachdatenbank mithilfe der Datenbankportabilität](move-a-mailbox-database-using-database-portability-exchange-2013-help.md).

