---
title: 'Leistungsempfehlungen für Exchange Server 2013: Exchange 2013 Help'
TOCTitle: Leistungsempfehlungen für Exchange Server 2013
ms:assetid: 6d0aea68-10d5-4a18-b632-a814ce3daa43
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn879084(v=EXCHG.150)
ms:contentKeyID: 63913011
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Leistungsempfehlungen für Exchange Server 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Exchange Server 2013-Leistungsoptimierung und -Problembehandlung sind am effektivsten, wenn Ihre Umgebung ordnungsgemäß dimensioniert und geplant wurde. Obwohl Exchange 2013 darauf ausgelegt ist, die zugrunde liegende Ressourceninfrastruktur zu vereinfachen, kann dennoch eine große Menge an Systemressourcen belegt werden, z. B. Arbeitsspeicher, Speicherkapazität und CPU-Kapazität.

Die Artikel in diesem Abschnitt wurden vom Exchange-Leistungsteam geschrieben. Sie enthalten Fachwissen der Exchange-Produktgruppe sowie bewährte Methoden, die aus Supportanfragen von Kunden ermittelt wurden. Diese Artikel sollen Sie dabei unterstützen, die Auswirkungen der in Exchange 2013 eingeführten Änderungen und die Bedeutung einer ordnungsgemäßen Dimensionierung Ihrer Exchange 2013-Infrastruktur zu verstehen. Wir haben außerdem empfohlene Optimierungen und Anleitungen zum Erkennen von Leistungsproblemen eingefügt.

## Architekturänderungen in Exchange 2013 und anderen Ressourcen

Die Änderungen an der Architektur von Exchange 2013 sind bereits auf TechNet und im [Exchange-Teamblog](https://go.microsoft.com/fwlink/p/?linkid=35786) dokumentiert. Wir werden zuerst einige allgemeine Änderungen darstellen, die Sie berücksichtigen sollten, um Leistungseinbußen und die Dimensionierung besser zu verstehen. Weiter unten finden Sie dann eine Liste empfohlener Referenzen, die weitere Zusammenhänge und Hintergründe für diese wichtigen Bereiche bieten.


> [!NOTE]
> Anweisen zur Leistungsoptimierung bei der Bereitstellung von Exchange Server 2013 in einer virtualisierten Umgebung finden Sie unter <A href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013-Virtualisierung</A>.



In Exchange 2013 ist die Clientzugriffs-Serverrolle ein zustandsloser Proxyserver. Jetzt besteht die primäre Verantwortung der Clientzugriffs-Serverrolle darin, eingehende Anforderungen zu authentifizieren und dann jede Anforderung an den entsprechenden Postfachserver weiterzuleiten, auf dem die aktive Kopie des Benutzerpostfachs gehostet ist. Dies bedeutet, dass es ist nicht mehr erforderlich ist, die Affinität zwischen dem Clientzugriffsserver und dem Lastenausgleich für bestimmte Protokolle zu konfigurieren.

Eine weitere wichtige Änderung in Exchange 2013 betrifft den Informationsspeicher. Der Informationsspeicher besteht jetzt aus zwei Arten von Prozessen: dem Host- und dem Arbeitsprozess. Jede Datenbankinstanz ist einem eigenen Microsoft.Exchange.Store.Worker.exe-Prozess zugeordnet. Dies ermöglicht eine bessere Isolierung von Datenbankproblemen und kann die Leistungsauswirkungen eines Datenbankproblems auf nur diese eine Arbeitsinstanz für diese Datenbank reduzieren.

Der Microsoft Exchange-Replikationsdienst ist für alle Hochverfügbarkeitsdienste im Zusammenhang mit der Postfachserverrolle verantwortlich. Dieser Replikationsdienst hostet die Active Manager-Komponente, die für die Überwachung von Fehlern und Korrekturmaßnahmen zuständig ist.

Ein großartiger Beitrag zu Änderungen an der Architektur, einschließlich der Auswirkungen einer erneuten Dimensionierung einer Exchange 2013-Umgebung aus früheren Versionen, finden Sie unter [Architektur der Exchange 2013-Serverrolle](https://go.microsoft.com/fwlink/p/?linkid=523735).

Weitere Informationen zu Änderungen an der Exchange 2013-Architektur und Hintergrundinformationen zu anderen relevanten Bereichen finden Sie in den folgenden Dokumenten:

[Exchange Server 2013-Architektur](https://go.microsoft.com/fwlink/p/?linkid=523769)

[Richtige Planung: Szenarien für die Exchange Server 2013-Dimensionierung](https://go.microsoft.com/fwlink/p/?linkid=523773)

[Überwachen und Optimieren der Microsoft Exchange Server 2013-Leistung](https://go.microsoft.com/fwlink/p/?linkid=523774)

[Implementieren von Exchange Server 2013: (01) Upgrade und Bereitstellung von Exchange Server 2013](https://go.microsoft.com/fwlink/p/?linkid=523775)

[Implementieren von Exchange Server 2013: (02) Richtige Planung: Exchange Server 2013-Dimensionierung](https://go.microsoft.com/fwlink/p/?linkid=523776)

[Implementieren von Exchange Server 2013: (03) Bewährte Methoden für die Exchange Server 2013-Virtualisierung](https://go.microsoft.com/fwlink/p/?linkid=523777)

[Implementieren von Exchange Server 2013: (04) Architektur von Exchange: Hohe Verfügbarkeit und Ausfallsicherheit für Standorte](https://go.microsoft.com/fwlink/p/?linkid=523779)

[Implementieren von Exchange Server 2013: (05) Outlook-Konnektivität](https://go.microsoft.com/fwlink/p/?linkid=523781)

[Die bevorzugte Architektur](https://go.microsoft.com/fwlink/p/?linkid=523782)

[Exchange 2013-Clientzugriffs-Serverrolle](https://go.microsoft.com/fwlink/p/?linkid=386373)

[Bewährte Methoden für die Exchange Server 2013-Virtualisierung](https://go.microsoft.com/fwlink/p/?linkid=523783)

[Lastenausgleich](load-balancing-exchange-2013-help.md)

[Exchange Server-Updates: Buildnummern und Veröffentlichungstermine](https://technet.microsoft.com/de-de/library/hh135098\(v=exchg.150\))

[Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md)

[Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md)

[ASP.NET-Threadverwendung in IIS 7.5 IIS 7.0 und IIS 6.0](https://go.microsoft.com/fwlink/p/?linkid=169626)

