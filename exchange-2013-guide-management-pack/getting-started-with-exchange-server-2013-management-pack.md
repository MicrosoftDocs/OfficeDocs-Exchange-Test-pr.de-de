---
title: Erste Schritte mit Exchange Server 2013 Management Pack
TOCTitle: Erste Schritte mit Exchange Server 2013 Management Pack
ms:assetid: 72d1609f-ab32-44d8-aa40-b1de587442d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn195908(v=EXCHG.150)
ms:contentKeyID: 53181888
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erste Schritte mit Exchange Server 2013 Management Pack

 

_**Letztes Änderungsdatum des Themas:**  2013-04-08_

Das Exchange Server 2013 Management Pack fügt einen Container in den Bereich **Überwachung** der SCOM-Konsole ein. Wenn Sie den Exchange Server 2013-Container erweitern, sehen Sie dort lediglich drei Ansichten.

![Exchange 2013 Management Pack Container](images/Dn195908.253b4ec5-2103-4b0c-a22e-5ebd24d08600(EXCHG.150).png "Exchange 2013 Management Pack Container")

## "Aktive Warnungen": Gibt es Probleme mit Exchange?

Die Ansicht **Aktive Warnungen** führt alle ausgelösten und aktuell in Ihre Exchange-Organisation anstehenden Warnungen auf. Klicken Sie auf eine Warnung, um weitere Informationen zur Warnung im Detailbereich anzuzeigen. Diese Ansicht bietet Ihnen im Wesentlichen Ja/Nein-Antworten auf die Frage "Gibt es Probleme mit der Exchange-Bereitstellung?" Jede Warnung entspricht mindestens einem Problem für einen bestimmten Integritätssatz. Je nach dem spezifischen Problem kann auch mehr als eine Warnung ausgegeben werden.

## "Organisationsintegrität": Welche Auswirkungen gibt es?

Falls Sie eine Warnung in der Ansicht "Aktive Warnungen" sehen, sollten Sie zunächst in die Ansicht **Organisationsintegrität** gehen. Hier finden Sie erste Informationen zur allgemeinen Integrität Ihrer Organisation. Diese Ansicht sagt Ihnen, welche Komponente der Organisation betroffen ist, wie Active Directory-Standorte und Datenbankverfügbarkeitsgruppen.

![Zustand der Organisation](images/Dn195908.603c920b-7b88-4956-87d9-09d93fa6cba3(EXCHG.150).png "Zustand der Organisation")

## "Serverintegrität": Auf welchem Server müssen Probleme behoben werden?

Die Ansicht **Serverintegrität** liefert Details zu den einzelnen Servern in Ihrer Organisation. In dieser Ansicht können Sie die Integrität für jeden einzelnen Server sehen. Hier grenzen Sie ein Problem auf einen bestimmten Server ein.

![Zustand des Servers](images/Dn195908.c863be83-fc4b-4daf-a18b-27b1aae15b1d(EXCHG.150).png "Zustand des Servers")

## Überwachungskategorien

Während Sie die drei Ansichten im Exchange server 2013-Dashboard durchgegangen sind, haben Sie vielleicht festgestellt, dass sich neben der Spalte **Status** vier weitere Integritätsindikatoren befinden.

![Exchange Statusindikatoren](images/Dn195908.dd10ed0b-abe5-41aa-8d43-b4fb10133984(EXCHG.150).png "Exchange Statusindikatoren")

Jeder dieser Integritätsindikatoren liefert Ihnen einen Überblick über bestimmte Aspekte der Exchange-Bereitstellung.

  - **Kontaktpunkte für Kunden** Sie zeigen Ihnen, was Benutzern widerfährt. Hat dieser Indikator den Status "fehlerfrei", bedeutet dies, das Problem hat wahrscheinlich keine Auswirkungen auf Benutzer. Beispiel: Angenommen ein DAG-Mitglied hat Probleme, aber die Datenbank hatte ein erfolgreiches Failover. In diesem Fall sind die Indikatoren bei dieser speziellen DAG "fehlerhaft", aber der Indikator "Kontaktpunkte für Kunden" zeigt "fehlerfrei", da die Benutzer keine Dienstunterbrechung erleiden.

  - **Dienstkomponenten** Sie zeigen Ihnen den Status der mit der Komponente verknüpften Diensts an. Beispiel: Der Indikator "Dienstkomponente für OWA" zeigt an, ob der OWA-Dienst insgesamt fehlerfrei arbeitet.

  - **Serverressourcen** Sie zeigen Ihnen den Status physischer Ressourcen an, die den Betrieb eines Servers beeinträchtigen.

  - **Schlüsselabhängigkeiten** Sie zeigen Ihnen den Status externer Ressourcen an, von denen Exchange abhängig ist, wie Netzwerkkonnektivität, DNS oder Active Directory.

Die Ansichten in Exchange Server 2013 Management Pack bieten Ihnen einen einfach aufgebauten, aber sehr nützlichen und bequemen Überblick über die Integrität Ihrer Organisation. Die Ansichten sind so aufgebaut, dass Sie bei einer Warnung schnell zur Ursache des Problems finden. Erfahren Sie mehr über die Verwendung von Exchange Server 2013 Management Pack in Bezug auf Problemlösungen unter [Verwenden des Exchange Server 2013-Management Packs für die Problembehandlung](using-the-exchange-server-2013-management-pack-for-troubleshooting.md).

