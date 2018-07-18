---
title: 'Edge-Transport-Server: Exchange 2013 Help'
TOCTitle: Edge-Transport-Server
ms:assetid: cfff9f59-afac-447c-8297-afcebe49a52d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124701(v=EXCHG.150)
ms:contentKeyID: 61180475
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Edge-Transport-Server

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-09-29_

Edge-Transport-Server halten die Angriffsfläche so klein wie möglich, indem der gesamte Internetnachrichtenfluss verarbeitet wird, der SMTP-Relay- (Simple Mail Transfer Protocol) und Smarthost-Dienste für Ihre Exchange-Organisation bereitstellt. Auf dem Edge-Transport-Server ausgeführte Agents bieten weitere Stufen von Nachrichtenschutz und -sicherheit. Diese Agents bieten Schutz vor Spam und wenden Transportregeln zum Steuern des Nachrichtenflusses an.

Da der Edge-Transport-Server im Umkreisnetzwerk installiert wird, ist er niemals Bestandteil der internen Active Directory-Gesamtstruktur Ihrer Organisation und hat keinen Zugriff auf Active Directory-Informationen. Der Edge-Transport-Server benötigt allerdings Daten, die in Active Directory gespeichert sind, beispielsweise Connectordaten für den Nachrichtenfluss und Empfängerdaten, um Antispam-Empfängersuchen durchzuführen. Mithilfe des Microsoft Exchange EdgeSync-Diensts (EdgeSync) werden diese Daten mit dem Edge-Transport-Server synchronisiert. Bei EdgeSync handelt es sich um eine Sammlung von Prozessen, die auf einem Exchange 2013-Postfachserver ausgeführt werden, um die unidirektionale Replikation von Empfänger- und Konfigurationsinformationen aus Active Directory in die Active Directory Lightweight Directory Services (AD LDS)-Instanz auf dem Edge-Transport-Server einzurichten. EdgeSync kopiert nur die Informationen, die erforderlich sind, damit der Edge-Transport-Server Antispam- und Konfigurationsaufgaben ausführen kann und die End-to-End-Nachrichtenübermittlung aktiviert wird. EdgeSync führt geplante Updates aus, damit die Informationen in AD LDS aktuell bleiben.

Sie können im Umkreisnetzwerk mehrere Edge-Transport-Server installieren. Die Bereitstellung mehrerer Edge-Transport-Server bietet Redundanz- und Failoverfunktionen für die eingehende Nachrichtenübermittlung. Sie können einen Lastenausgleich des SMTP-Datenverkehrs in Ihre Organisation zwischen Edge-Transport-Servern durchführen, indem Sie mehr als einen MX-Datensatz mit der gleichen Priorität für Ihre E-Mail-Domäne definieren. Sie können eine Konsistenz bei der Konfiguration zwischen mehreren Edge-Transport-Servern erreichen, indem Sie geklonte Konfigurationsskripts verwenden.

Mit der Serverrolle "Edge-Transport" können Sie die folgenden Nachrichtenverarbeitungsszenarien erledigen.

## Internetnachrichtenübermittlung

Edge-Transport-Server akzeptieren Nachrichten, die über das Internet in die Exchange-Organisation gelangen. Nachdem die Nachrichten vom Edge-Transport-Server verarbeitet wurden, werden sie abhängig von der Konfiguration Ihrer internen Exchange-Server an die nächste Position weitergeleitet:

  - Wenn der Clientzugriffsserver und der Postfachserver auf getrennten Computern installiert sind, werden die Nachrichten an den Transportdienst auf dem Postfachserver weitergeleitet. Der Clientzugriffsserver wird bei der Übermittlung eingehender SMTP-Nachrichten umgangen.

  - Wenn der Clientzugriffsserver und der Postfachserver auf dem gleichen Computer installiert sind, werden die Nachrichten an den Front-End-Transport-Dienst auf dem Clientzugriffsserver und anschließend an den Transportdienst auf dem Postfachserver weitergeleitet.

Alle von innerhalb der Organisation an das Internet gesendeten Nachrichten werden zu den Edge-Transport-Servern geleitet, nachdem die Nachrichten vom Transportdienst auf dem Postfachserver verarbeitet wurden. Sie können den Edge-Transport-Server für die Verwendung von DNS zum Auflösen von MX-Ressourceneinträgen für externe SMTP-Domänen konfigurieren, oder Sie können den Edge-Transport-Server zum Weiterleiten von Nachrichten an einen Smarthost für die DNS-Auflösung konfigurieren.

## Antispamschutz

In Exchange 2013 bieten die Antispam- und Antivirenfunktionen Dienste zum Schutz vor unerwünschten kommerziellen E-Mails (Spam) im Umkreisnetzwerk.

Spammer verwenden eine Vielzahl von Techniken, um Spam in Ihre Organisation zu senden. Edge-Transport-Server verhindern, dass Benutzer jemals Spam erhalten. Dazu wird eine Reihe von Agents bereitgestellt, die zusammenarbeiten, um verschiedene Stufen der Spamfilterung und des Schutzes zu bieten. Das Einrichten von Teergruppenintervallen für Connectors gestaltet E-Mail-Abfangversuche ineffektiv.

## Edge-Transportregeln

Edge-Transportregeln werden zum Steuern des Nachrichtenflusses verwendet, der aus dem Internet empfangen oder an das Internet gesendet wird. Die Edge-Transportregeln werden auf jedem einzelnen Edge-Transport-Server konfiguriert und helfen dabei, die Ressourcen und Daten des Unternehmensnetzwerks zu schützen, indem Aktionen auf Nachrichten angewendet werden, die bestimmte Bedingungen erfüllen. Bedingungen für Edge-Transportregeln basieren auf Daten, wie z. B. speziellen Wörtern oder Textmustern im Nachrichtenbetreff oder -text, in den Kopfzeilen oder in der Absenderadresse (Von), der SCL-Bewertung (Spam Confidence Level) oder dem Anlagentyp. Aktionen bestimmen, wie die Nachricht verarbeitet wird, wenn eine bestimmte Bedingung erfüllt (true) ist. Zu den möglichen Aktionen gehören das Isolieren einer Nachricht, das Verwerfen oder Zurückweisen einer Nachricht, das Hinzufügen zusätzlicher Empfänger oder das Protokollieren eines Ereignisses. Durch optionale Ausnahmen werden bestimmte Nachrichten davon ausgenommen, dass eine Aktion auf sie angewendet wird.

## Umschreiben von Adressen

Das erneute Schreiben von Adressen ermöglicht ein einheitliches Erscheinungsbild der E-Mail-Adressen gegenüber externen Empfängern. Sie konfigurieren das Umschreiben von Adressen auf Edge-Transport-Servern, um die SMTP-Adressen von eingehenden und ausgehenden Nachrichten zu ändern. Das erneute Schreiben von Adressen ist für neu zusammengeführte Organisationen besonders nützlich, da sie gegenüber externen Empfängern ein einheitliches Erscheinungsbild der E-Mail-Adressen präsentieren möchten.

Weitere Informationen zum erneuten Schreiben von Adressen finden Sie unter [Adressumschreibung auf Edge-Transport-Servern](address-rewriting-on-edge-transport-servers-exchange-2013-help.md).

