---
title: 'Postfachdatenbankkopien: Exchange 2013 Help'
TOCTitle: Postfachdatenbankkopien
ms:assetid: ce748bca-3e24-493b-b9e6-153157bffd6a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979802(v=EXCHG.150)
ms:contentKeyID: 50476746
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Postfachdatenbankkopien

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

In Microsoft Exchange Server 2013 wird das Konzept der Datenbankmobilität genutzt, bei dem es sich um von Exchange verwaltete Failover auf Datenbankebene handelt. Im Rahmen der Datenbankmobilität werden Datenbanken von Servern getrennt, die Unterstützung für bis zu 16 Kopien einer einzelnen Datenbank hinzugefügt und eine einheitliche Vorgehensweise beim Hinzufügen von Datenbankkopien zu einer Datenbank bereitgestellt.

## Wichtige Merkmale

Wichtige Merkmale von Postfachdatenbankkopien sind u. a.:

  - Bis zu 16 Kopien einer Exchange 2013-Postfachdatenbank können auf mehreren Postfachservern erstellt werden, vorausgesetzt, die Server sind in einer Database Availability Group (DAG) enthalten, die eine Begrenzung für die fortlaufende Replikation darstellt. Exchange 2013-Postfachdatenbanken können nur auf andere Exchange 2013-Postfachserver in einer DAG repliziert werden. Sie können eine Datenbank weder außerhalb einer DAG noch eine Exchange 2013-Postfachdatenbank auf einen Server mit Exchange 2010 oder früher replizieren. Weitere Informationen zu Datenbankverfügbarkeitsgruppen finden Sie unter [Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md).

  - Alle Postfachserver in einer Datenbankverfügbarkeitsgruppe müssen in derselben Active Directory-Domäne enthalten sein.

  - Postfachdatenbankkopien unterstützen die Konzepte der Wiedergabeverzögerung und der Abschneideverzögerung. Angemessene Planung ist erforderlich, bevor diese Features aktiviert werden.

  - Alle Datenbankkopien können mithilfe einer Exchange unterstützenden, auf dem Volumenschattenkopie-Dienst basierenden Sicherungsanwendung gesichert werden.

  - Datenbankkopien können nur auf Postfachservern erstellt werden, die nicht als Host der aktiven Kopie einer Datenbank dienen. Es ist nicht möglich, zwei Kopien derselben Datenbank auf demselben Server zu erstellen.

  - Alle Kopien einer Datenbank verwenden auf allen Servern, die eine Kopie aufweisen, denselben Pfad. Die Datenbank- und Protokolldateipfade einer Datenbankkopie auf den einzelnen Postfachservern dürfen nicht in Konflikt mit anderen Datenbankpfaden stehen.

  - Datenbankkopien können an denselben oder unterschiedlichen Active Directory-Standorten bzw. im selben oder unterschiedlichen Netzwerksubnetzen erstellt werden.

  - Datenbankkopien werden zwischen Postfachservern mit einer Roundtrip-Netzwerklatenz von mehr als 500 Millisekunden (ms) nicht unterstützt.

## Postfachdatenbankkopien

Sie können jederzeit eine Postfachdatenbankkopie erstellen. Postfachdatenbankkopien können zwischen Postfachservern flexibel und abgestuft verteilt werden.

Sie können mithilfe des Assistenten **Postfachdatenbankkopie hinzufügen** in der Exchange-Verwaltungskonsole oder des Cmdlets **Add-MailboxDatabaseCopy** in der Exchange-Verwaltungsshell eine Postfachdatenbankkopie erstellen.

Wenn Sie eine Postfachdatenbankkopie erstellen, geben Sie die folgenden Parameter an:

  - *Identity*   Dieser Parameter gibt den Namen der Datenbank an, die kopiert wird. Datenbanknamen müssen innerhalb der Exchange-Organisation eindeutig sein.

  - *MailboxServer*   Dieser Parameter gibt den Namen des Postfachservers an, der die Datenbankkopie hostet. Dieser Server muss Mitglied derselben Datenbankverfügbarkeitsgruppe sein und darf nicht bereits als Host einer Kopie der Datenbank dienen.

Sie können optional Folgendes angeben:

  - *ActivationPreference*   Dieser Parameter gibt die Aktivierungseinstellungsnummer an, die Active Manager im Rahmen des Prozesses der Auswahl der bestmöglichen Kopie verwendet. Der Parameter dient auch zur erneuten Verteilung aktiver Postfachdatenbanken in der DAG, falls das Skript **RedistributeActiveDatabases.ps1** verwendet wird. Der Wert der Aktivierungseinstellung ist eine Zahl größer gleich 1, wobei 1 in der Reihenfolge zuerst kommt. Die Positionsnummer darf nicht größer als die Anzahl der Postfachdatenbankkopien sein.

  - *ReplayLagTime *   Mit diesem Parameter wird der Zeitraum angegeben, den der Exchange-Replikationsdienst abwarten soll, bevor mit der Wiedergabe von Protokolldateien begonnen wird, die in die Datenbankkopie kopiert wurden. Das Format für diesen Parameter ist (Tage.Stunden:Minuten:Sekunden). Die Standardeinstellung für diesen Wert ist 0 Sekunden. Die maximal zulässige Einstellung für diesen Wert ist 14 Tage. Die zulässige Mindesteinstellung ist 0 Sekunden. Bei Festlegung auf 0 wird die Protokollwiedergabeverzögerung deaktiviert.

  - *TruncationLagTime*   Mit diesem Parameter wird der Zeitraum angegeben, den der Exchange-Replikationsdienst abwarten soll, bevor Protokolldateien abgeschnitten werden, die in eine Kopie der Datenbank wiedergegeben wurden. Der Zeitraum beginnt nach der erfolgreichen Wiedergabe des Protokolls in die Kopie der Datenbank. Das Format für diesen Parameter ist (Tage.Stunden:Minuten:Sekunden). Die Standardeinstellung für diesen Wert ist 0 Sekunden. Die maximal zulässige Einstellung für diesen Wert ist 14 Tage. Die zulässige Mindesteinstellung ist 0 Sekunden. Bei Festlegung auf 0 wird die Protokollabschneideverzögerung deaktiviert.

  - *SeedingPostponed*   Mit diesem Parameter wird angegeben, dass der Task nicht automatisch ein Seeding für die Datenbankkopie auf dem angegebenen Postfachserver durchführen soll. Diese Option wird in der Regel verwendet, wenn Sie für eine neue Postfachdatenbankkopie mithilfe einer vorhandenen Kopie der Datenbank ein Seeding durchführen möchten (z. B. durch Hinzufügen einer zweiten Kopie einer bestimmten Datenbank zu einem Remotestandort). Bei Verwenden dieses Parameters müssen Sie mit dem Cmdlet [Update-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd335201\(v=exchg.150\)) manuell ein Seeding für die Datenbank ausführen.

Weitere Informationen zum Erstellen, Verwenden und Verwalten von Postfachdatenbankkopien finden Sie unter [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

