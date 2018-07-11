---
title: 'Hohe Verfügbarkeit des Transports: Exchange 2013 Help'
TOCTitle: Hohe Verfügbarkeit des Transports
ms:assetid: e9ec6d05-f441-4cca-8592-8f7469948299
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657506(v=EXCHG.150)
ms:contentKeyID: 50476980
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hohe Verfügbarkeit des Transports

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-15_

In Microsoft Exchange Server 2013 ist die hohe Verfügbarkeit des Transports dafür zuständig, redundante Kopien von Nachrichten vor und nach dem erfolgreichen Zustellen von Nachrichten beizubehalten. Exchange 2013 optimiert die Features für die hohe Verfügbarkeit des Transports, die in Exchange Server 2010 eingeführt wurden, z. B. die Shadow-Redundanz und der Transportdumpster, die sicherzustellen, dass beim Transport keine Nachrichten verloren gehen.

Hier folgt eine Übersicht über die wesentlichen Verbesserungen an der hohen Verfügbarkeit des Transports in Exchange 2013:

  - Die Shadow-Redundanz erstellt eine redundante Kopie der Nachricht auf einem anderen Server, bevor die Nachricht angenommen oder bestätigt wird. Die Unterstützung bzw. die fehlende Unterstützung des sendenden Servers für die Shadow-Redundanz ist dabei irrelevant.

  - Die Shadow-Redundanz erkennt sowohl Database Availability Groups (DAGs) als auch Active Directory-Standorte als Grenzen für die hohe Verfügbarkeit des Transports. Dadurch wird die Anzahl der Server verringert, die redundante Kopien von Nachrichten aufnehmen können. Zusätzlich wird der überflüssige Wartungsdatenverkehr für redundante Nachrichten zwischen Database Availability Groups oder Active Directory-Standorten beseitigt.
    
    Weitere Informationen finden Sie unter [Shadow-Redundanz](shadow-redundancy-exchange-2013-help.md).

  - Der Transportdumpster wurde verbessert und wird jetzt als *Sicherheitsnetz* bezeichnet. Das Sicherheitsnetz speichert Nachrichten, die erfolgreich vom Transportdienst verarbeitet wurden, auf Postfachservern. Das Sicherheitsnetz funktioniert am besten bei Postfachservern in einer Database Availability Group, aber auch für mehrere Postfachserver an demselben Active Directory-Standort, die nicht zu einer DAG gehören.

  - Das Sicherheitsnetz selbst ist nun auf einem anderen Server redundant verfügbar. Das ist wichtig, um eine einzelne Fehlerquelle in Exchange 2013 zu vermeiden, da sich sowohl der Transportdienst als auch die Postfachdatenbanken auf dem Postfachserver befinden.
    
    Weitere Informationen finden Sie unter [Sicherheitsnetz](safety-net-exchange-2013-help.md).

Das folgende Diagramm bietet eine allgemeine Übersicht über die Funktionsweise der hohen Verfügbarkeit des Transports in Exchange 2013.

![Übersicht über die hohe Verfügbarkeit des Transports](images/JJ657506.88f2284d-8afe-4c8f-94a6-cd4c097a55d8(EXCHG.150).gif "Übersicht über die hohe Verfügbarkeit des Transports")

1.  Ein Exchange 2013-Postfachserver namens "Mailbox01" empfängt eine Nachricht von einem SMTP-Server, der sich außerhalb der Grenze der hohen Verfügbarkeit des Transports befindet. Die *Grenze der hohen Verfügbarkeit des Transports* ist eine Database Availability Group oder ein Active Directory-Standort in DAG-freien Umgebungen. Die Nachricht kann von einem SMTP-Server eines Drittanbieters, von einem Internet-SMTP-Server mit Proxyverbindung über einen Clientzugriffsserver oder von einem anderen Exchange 2013-Server stammen.

2.  Bevor der Empfang der Nachricht bestätigt wird, initiiert "Mailbox01" eine neue SMTP-Sitzung mit einem anderen Exchange 2013-Postfachserver namens "Mailbox03", der sich innerhalb der Grenze der hohen Verfügbarkeit des Transports befindet. Der Postfachserver "Mailbox03" erstellt dann eine Schattenkopie der Nachricht. In DAG-Umgebungen wird ein Shadow-Server an einem Active Directory-Remotestandort bevorzugt. "Mailbox01" ist der primäre Server, der die primäre Nachricht enthält, und "Mailbox03" ist der Shadow-Server mit der Shadow-Nachricht.

3.  Der Transportdienst auf "Mailbox01" verarbeitet die primäre Nachricht.
    
    1.  In diesem Beispiel befindet sich das Postfach des Empfängers auf "Mailbox01", daher übermittelt der Transportdienst die Nachricht an den lokalen Postfachtransportdienst.
    
    2.  Der Postfachtransportdienst stellt die Nachricht an die lokale Postfachdatenbank zu.
    
    3.  "Mailbox01" stellt für "Mailbox03" einen Löschstatus in die Warteschlange, der auf die erfolgreiche Verarbeitung der primären Nachricht hinweist. "Mailbox01" verschiebt dann eine Kopie der primären Nachricht in das lokale primäre Sicherheitsnetz. Beachten Sie, dass die Nachricht zwischen Warteschlangen innerhalb derselben Warteschlangendatenbank verschoben wird.

4.  "Mailbox03" fragt bei "Mailbox01" regelmäßig den Löschstatus der primären Nachricht an.

5.  Wenn "Mailbox03" ermittelt, dass "Mailbox01" die primäre Nachricht erfolgreich verarbeitet hat, dann verschiebt "Mailbox03" die Shadow-Nachricht in das lokale Shadow-Sicherheitsnetz. Beachten Sie, dass die Nachricht zwischen Warteschlangen innerhalb derselben Warteschlangendatenbank verschoben wird.

Die Nachricht bleibt im primären Sicherheitsnetz und im Shadow-Sicherheitsnetz erhalten, bis die Nachricht auf der Grundlage eines konfigurierbaren Timeoutwerts abläuft. Wenn vor dem Ablauf der Nachricht ein Postfachdatenbank-Failover auftritt, wird die Nachricht vom primären Sicherheitsnetz auf "Mailbox01" erneut übermittelt. Wenn "Mailbox01" nicht verfügbar ist, übernimmt das Shadow-Sicherheitsnetz auf "Mailbox03" die Aufgabe und übermittelt die Nachricht erneut.

## Nachrichtenredundanz im Front-End-Transport-Dienst auf Clientzugriffsservern

Ein Clientzugriffsserver besitzt keine Nachrichtenwarteschlangen. Es handelt sich um einen zustandslosen Proxyserver, der den Front-End-Transport-Dienst dazu verwendet, eingehende SMTP-Verbindungen anzunehmen und diese an den Transportdienst auf einem Postfachserver weiterzuleiten. Der Front-End-Transport-Dienst hält die SMTP-Sitzung mit dem sendenden Server geöffnet, während die primäre Nachricht an den Transportdienst auf einem Postfachserver übermittelt und eine Schattenkopie der Nachricht vom Transportdienst auf einem anderen Postfachserver innerhalb der Grenze der hohen Verfügbarkeit des Transports erstellt wird. Erst nachdem sowohl die primäre als auch die Shadow-Nachricht erfolgreich erstellt wurden, wird der SMTP-Befehl für das Datenende über den Clientzugriffsserver zurück an den sendenden SMTP-Server gesendet.

