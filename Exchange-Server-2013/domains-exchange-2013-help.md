---
title: 'Domänen: Exchange 2013 Help'
TOCTitle: Domänen
ms:assetid: 11748c2d-2e32-43a4-b77d-e0c17db6200b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673041(v=EXCHG.150)
ms:contentKeyID: 50475127
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Domänen

 

_**Gilt für:** Exchange Server 2013, Office 365_

_**Letztes Änderungsdatum des Themas:** 2012-10-11_

Domänen stehen für SMTP-Namespaces, für die E-Mail-Verzeichnisse und -Postfächer eingerichtet sind. Indem Sie die Domänen konfigurieren, die mit Ihrer Microsoft Exchange Server 2013-Organisation interagieren, können Sie festlegen, wie ausgehende und eingehende E-Mails für verschiedene Domänen von Exchange verarbeitet werden.

## Akzeptierte Domänen

Eine akzeptierte Domäne ist jeder SMTP-Namespace, für den eine Exchange-Organisation E-Mail sendet oder empfängt. Akzeptierte Domänen enthalten die Domänen, für die die Exchange-Organisation autoritativ ist, sowie interne und externe Relaydomänen. Eine Exchange-Organisation ist autoritativ, wenn sie die Nachrichtenübermittlung für Empfänger in der akzeptierten Domäne ausführt. Akzeptierte Domänen umfassen darüber hinaus Domänen, für die die Exchange-Organisation E-Mails empfängt und dann an einen E-Mail-Server außerhalb der Organisation weiterleitet.

Weitere Informationen zu akzeptierten Domänen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

## Remotedomänen

In Exchange 2013 können Sie Remotedomäneneinträge erstellen, um die Einstellungen für die Nachrichtenübermittlung zwischen Ihrer Exchange-Organisation und Domänen außerhalb Ihrer Organisation festzulegen. Durch das Erstellen eines Remotedomäneneintrags steuern Sie die Nachrichtentypen, die an diese Domäne gesendet werden. Sie können zudem auch Nachrichtenformatrichtlinien anwenden und zulässige Zeichensätze für Nachrichten angeben, die von Benutzer Ihrer Organisation an die Remotedomäne gesendet werden.

Bei den Einstellungen für Remotedomänen handelt es sich um globale Konfigurationseinstellungen für die Exchange-Organisation. Die Remotedomäneneinstellungen werden während der Kategorisierung auf Nachrichten angewendet. Bei der Empfängerauflösung wird die Empfängerdomäne mit den konfigurierten Remotedomänen verglichen. Wenn durch die Konfiguration einer Remotedomäne verhindert wird, dass ein bestimmter Nachrichtentyp an Empfänger in dieser Domäne gesendet werden kann, wird die Nachricht gelöscht. Wenn Sie für die Remotedomäne ein bestimmtes Nachrichtenformat festlegen, werden Nachrichtenkopfzeile und -inhalt geändert. Die Einstellungen gelten für alle Nachrichten, die von der Exchange-Organisation verarbeitet werden.

Weitere Informationen zu Remotedomänen finden Sie unter [Remotedomänen](remote-domains-exchange-2013-help.md).

