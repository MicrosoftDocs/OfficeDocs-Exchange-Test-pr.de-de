---
title: 'Wiederherstellungsdatenbanken: Exchange 2013 Help'
TOCTitle: Wiederherstellungsdatenbanken
ms:assetid: f3c6fd0b-2e25-442e-a0fc-46f663130c3e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876954(v=EXCHG.150)
ms:contentKeyID: 50477077
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Wiederherstellungsdatenbanken

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-11-02_

Eine Wiederherstellungsdatenbank ist eine spezielle Art von Postfachdatenbank, mit der Sie eine wiederhergestellte Postfachdatenbank einbinden und im Rahmen einer Wiederherstellung Daten aus der wiederhergestellten Datenbank extrahieren können. Mithilfe des Cmdlets [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)) können Sie Daten aus einer Wiederherstellungsdatenbank extrahieren. Anschließend können die Daten in einen Ordner exportiert oder mit einem vorhandenen Postfach zusammengeführt werden. Durch Wiederherstellungsdatenbanken können Sie Daten aus einer Sicherung oder Kopie einer Datenbank wiederherstellen, ohne den Benutzerzugriff auf aktuelle Daten zu beeinträchtigen.

Microsoft Exchange Server 2013 unterstützt die Möglichkeit, Daten direkt in einer Wiederherstellungsdatenbank wiederherzustellen. Das Einbinden der wiederhergestellten Daten in Form einer Wiederherstellungsdatenbank ermöglicht es dem Administrator, einzelne Postfächer oder einzelne Elemente in einem Postfach wiederherzustellen. Es gibt zwei Möglichkeiten, um Daten in einer Wiederherstellungsdatenbank wiederherzustellen:

  - Wenn eine Wiederherstellungsdatenbank bereits vorhanden ist, kann die Anwendung die Einbindung der Datenbank aufheben, die Daten in den Wiederherstellungsdatenbank- und Protokolldateien wiederherstellen und die Datenbank anschließend erneut einbinden.

  - Die Datenbank- und Protokolldateien können in einem beliebigen Speicherort wiederhergestellt werden. Exchange analysiert die wiederhergestellten Daten und spielt die Transaktionsprotokolle erneut ab, um die Datenbanken zu aktualisieren. Anschließend kann eine Wiederherstellungsdatenbank so konfiguriert werden, dass sie auf die bereits wiederhergestellten Datenbankdateien verweist.

## Unterschied zwischen einer Postfachdatenbank und einer Wiederherstellungsdatenbank

Wiederherstellungsdatenbanken unterscheiden sich von Standard-Postfachdatenbanken in mehrerlei Hinsicht:

  - Eine Wiederherstellungsdatenbank wird mithilfe der Exchange-Verwaltungsshell erstellt.

  - E-Mail kann nicht in oder aus einer Wiederherstellungsdatenbank gesendet werden. Der gesamte Clientprotokollzugriff auf eine Wiederherstellungsdatenbank (einschließlich SMTP, POP3 und IMAP4) ist blockiert. Dieses Konzept verhindert die Verwendung einer Wiederherstellungsdatenbank, um E-Mail in das Messagingsystem einzufügen oder daraus zu entfernen.

  - Der Client-MAPI-Zugriff über Microsoft Office Outlook oder Outlook Web App ist blockiert. MAPI-Zugriff wird für eine Wiederherstellungsdatenbank unterstützt, jedoch nur durch Wiederherstellungstools und Anwendungen. Sowohl die Postfach-GUID als auch die Datenbank-GUID muss angegeben werden, wenn MAPI für die Anmeldung bei einem Postfach in einer Wiederherstellungsdatenbank verwendet wird.

  - Postfächer in einer Wiederherstellungsdatenbank können nicht mit Benutzerkonten verbunden werden. Um einem Benutzer den Zugriff auf die Daten in einem Postfach in einer Wiederherstellungsdatenbank zu ermöglichen, muss das Postfach mit einem vorhandenen Postfach zusammengeführt oder in einen Ordner exportiert werden.

  - System- und Postfachverwaltungsrichtlinien werden nicht angewendet. Dieses Konzept verhindert, dass Elemente in einer Wiederherstellungsdatenbank während des Wiederherstellungsprozesses vom System gelöscht werden.

  - Eine Onlinewartung wird für Wiederherstellungsdatenbanken nicht durchgeführt.

  - Für Wiederherstellungsdatenbanken kann die Umlaufprotokollierung nicht aktiviert werden.

  - Es kann immer nur eine Wiederherstellungsdatenbank auf einem Postfachserver eingebunden sein. Die Verwendung einer Wiederherstellungsdatenbank wird bei der Datenbankbegrenzung pro Postfachserver nicht eingerechnet.

  - Sie können keine Postfachdatenbankkopien einer Wiederherstellungsdatenbank erstellen.

  - Eine Wiederherstellungsdatenbank kann als Ziel für Wiederherstellungsvorgänge, jedoch nicht für Sicherungsvorgänge verwendet werden.

  - Eine wiederhergestellte Datenbank, die als Wiederherstellungsdatenbank eingebunden wird, ist in keiner Weise an das ursprüngliche Postfach gebunden.

## Verwenden einer Wiederherstellungsdatenbank

Bevor Sie eine Wiederherstellungsdatenbank verwenden können, müssen bestimmte Anforderungen erfüllt sein. Eine Wiederherstellungsdatenbank kann nur für Exchange 2013-Postfachdatenbanken verwendet werden. Postfachdatenbanken aus früheren Versionen von Exchange werden nicht unterstützt. Außerdem muss sich das Zielpostfach, das zur Datenzusammenführung und -extraktion verwendet wird, in derselben Active Directory-Gesamtstruktur befinden wie die in der Wiederherstellungsdatenbank eingebundene Datenbank.

Eine Wiederherstellungsdatenbank kann zum Wiederherstellen von Daten in verschiedenen Situationen eingesetzt werden. Hierzu gehören:

  - **Dial-Tone-Wiederherstellung auf demselben Server**   Sie können eine Wiederherstellung aus einer Wiederherstellungsdatenbank im Rahmen eines Dial-Tone-Wiederherstellungsvorgangs durchführen, nachdem die ursprüngliche Datenbank aus einer Sicherung wiederhergestellt wurde.

  - **Dial-Tone-Wiederherstellung auf einem anderen Server**   Sie können einen anderen Server zum Hosten der Dial-Tone-Datenbank verwenden und später Daten aus einer Wiederherstellungsdatenbank wiederherstellen, nachdem die ursprüngliche Datenbank aus einer Sicherung wiederhergestellt wurde.

  - **Postfachwiederherstellung**   Sie können ein einzelnes Postfach aus einer Sicherung wiederherstellen, wenn die Aufbewahrungszeit für das gelöschte Postfach abgelaufen ist. Anschließend extrahieren Sie Daten aus dem wiederhergestellten Postfach und kopieren sie in einen Zielordner oder führen sie mit einem anderen Postfach zusammen.

  - **Wiederherstellung bestimmter Elemente**   Sie können eine Wiederherstellung von Sicherungsdaten durchführen, die gelöscht oder aus einem Postfach entfernt wurden.


> [!NOTE]
> Ordner-Zugriffssteuerungslisten (Access Control Lists, ACLs) bleiben beim Wiederherstellen von Inhalten in einem aktiven Postfach nicht erhalten. Da der Wiederherstellungsvorgang normalerweise die Wiederherstellung von Postfachdaten und das Zusammenführen des Inhalts mit der ursprünglichen Datenbank umfasst, sollte das Wiederherstellen oder Kopieren von Zugriffssteuerungslisten nicht erforderlich sein.



Eine Wiederherstellungsdatenbank ist für die Wiederherstellung von Postfachdatenbanken unter den folgenden Bedingungen und in folgenden Szenarios ausgelegt:

  - Die logischen Informationen über die ursprüngliche Datenbank und die in der Datenbank enthaltenen Postfächer sind intakt und unverändert in Active Directory enthalten.

  - Sie müssen ein einzelnes Postfach oder eine einzige Datenbank wiederherstellen. Folgende Wiederherstellungsszenarios werden berücksichtigt:
    
      - Wiederherstellen und Reparieren einer Datenbank während der Verwendung einer Dial-Tone-Datenbank mit dem Ziel, die beiden Datenbanken zusammenzuführen.
    
      - Wiederherstellen einer Datenbank auf einem anderem Server als dem ursprünglichen Server dieser Datenbank. Bei Bedarf können die wiederhergestellten Daten wieder auf dem ursprünglichen Server zusammengeführt werden.
    
      - Wiederherstellen von Elementen, die Benutzer zuvor aus ihrem Postfach gelöscht haben, nach Ablauf der Aufbewahrungszeit für gelöschte Elemente.

Wiederherstellungsdatenbanken sind im Allgemeinen nicht für Szenarien geeignet, in denen Sie vollständige Server oder mehrere Datenbanken wiederherstellen müssen, oder wenn in einer Notfallsituation Ihre Active Directory-Topologie geändert oder neu erstellt werden muss.

Weitere Informationen zum Erstellen einer Wiederherstellungsdatenbank finden Sie unter [Erstellen einer Wiederherstellungsdatenbank](create-a-recovery-database-exchange-2013-help.md). Weitere Informationen zum Verwenden einer Wiederherstellungsdatenbank finden Sie unter [Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank](restore-data-using-a-recovery-database-exchange-2013-help.md).

