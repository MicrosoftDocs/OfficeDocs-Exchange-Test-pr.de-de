---
title: 'Clientzugriffsserver: Exchange 2013 Help'
TOCTitle: Clientzugriffsserver
ms:assetid: 87e206ab-7a7b-4b4f-be1a-5035713c74d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298114(v=EXCHG.150)
ms:contentKeyID: 50476103
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Clientzugriffsserver

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-07-02_

Bei Microsoft Exchange 2013 wurden größere Änderungen an der Architektur von Exchange-Serverrollen vorgenommen. Anstelle der fünf Serverrollen, die in Exchange 2010 und Exchange 2007 vorhanden waren, wurde die Anzahl von Serverrollen in Exchange 2013 auf drei verringert: die Serverrollen "Clientzugriff", "Postfach" und, mit Service Pack 1, die Serverrolle "Edge-Transport".


> [!NOTE]
> Exchange 2013 kann auch mit der Exchange&nbsp;2010-Edge-Transport-Serverrolle verwendet werden.



Der Exchange 2013-Postfachserver enthält viele der Serverkomponenten, die in Exchange 2010 zu finden sind: Clientzugriffsprotokolle, Transportdienste, Postfachdatenbanken und Unified Messaging-Dienste (der Clientzugriffsserver leitet SIP-Verkehr, der durch eingehende Anrufe generiert wird, an den Postfachserver um). Weitere Informationen zum Exchange 2013-Postfachserver finden Sie unter [Postfachserver](mailbox-server-exchange-2013-help.md).

Der Clientzugriffsserver stellt Authentifizierung, eingeschränkte Umleitung und Proxydienste bereit und bietet alle üblichen Clientzugriffsprotokolle: HTTP, POP, IMAP und SMTP. Der Clientzugriffsserver ist ein zustandsloser Thin-Server, auf dem kein Datenrendering durchgeführt wird. Auf einem Clientzugriffsserver werden keine Daten gespeichert oder in Warteschlangen gestellt. Weitere Informationen zur neuen Exchange 2013-Architektur finden Sie unter [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).


> [!WARNING]
> Clientzugriffsservers werden in Umkreisnetzwerken nicht unterstützt und müssen innerhalb Ihrer internen Active Directory-Umgebung bereitgestellt werden. Jeder Active Directory-Standort, der einen Postfachserver umfasst, muss auch einen Clientzugriffsserver aufweisen.



Aufgrund dieser Architekturänderungen gab es Änderungen in Bezug auf die Clientkonnektivität. Erstens wird RPC/TCP nicht mehr als Protokoll für den Direktzugriff unterstützt. Das bedeutet, dass Outlook-Konnektivität vollständig mithilfe von RPC über HTTPS (auch als Outlook Anywhere bezeichnet) oder bei Exchange 2013 SP1 und Outlook 2013 SP1 mit MAPI über HTTP erfolgen muss. Als Ergebnis dieser Änderungen muss sich der RPC-Clientzugriffsdienst nicht auf dem Clientzugriffsserver befinden. Außerdem sind für eine Lösung mit Ausfallsicherheit für Standorte weniger Namespaces erforderlich als in Exchange 2010, und es ist nicht mehr nötig, Affinitätseinstellungen für den RPC-Clientzugriffsdienst bereitzustellen. Außerdem stellen Outlook-Clients nicht länger eine Verbindung mit dem vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) eines Servers her, wie dies in allen vorherigen Versionen von Exchange der Fall war. Mithilfe der AutoErmittlung findet Outlook einen neuen Verbindungspunkt, der sich aus der Benutzerpostfach-GUID + @ + dem Domänenanteil der primären SMTP-Adresse des Benutzers zusammensetzt. Durch diese Änderung werden Benutzer wesentlich seltener mit der Meldung konfrontiert, dass der Administrator eine Änderung am Postfach vorgenommen hat. Nur Outlook 2007 und höhere Versionen werden mit Exchange 2013 unterstützt.

## Clientzugriffsserver-Funktionalität

Der Clientzugriffsserver in Exchange 2013 übernimmt gewissermaßen die Funktion einer Eingangstür, durch die alle Clientanforderungen eingelassen und an die richtige aktive Postfachdatenbank weitergeleitet werden. Der Clientzugriffsserver stellt Netzwerksicherheitsfunktionen wie SSL (Secure Sockets Layer) und Clientauthentifizierung bereit und verwaltet Clientverbindungen durch Umleitungs- und Proxyfunktionalität. Der Clientzugriffsserver authentifiziert Clientverbindungen und leitet eine Anforderung in den meisten Fällen an den Postfachserver, auf dem sich die derzeit aktive Kopie der Datenbank mit dem Benutzerpostfach befindet. In manchen Fällen kann der Clientzugriffsserver die Anforderung an einen passenderen Clientzugriffsserver weiterleiten, der sich entweder an einem anderen Standort befindet oder eine aktuellere Version von Exchange Server ausführt.

Der Clientzugriffsserver besitzt folgende Merkmale:

  - **Zustandsloser Server** In vorherigen Versionen von Exchange war für viele Clientzugriffsprotokolle Sitzungsaffinität erforderlich. Beispielsweise verlangte Outlook Web App, dass alle Anforderungen eines bestimmten Clients von einem bestimmten Clientzugriffsserver innerhalb eines Lastenausgleichsarrays von Clientzugriffsservern verarbeitet wurden. In Exchange 2013 ist der Clientzugriffsserver zustandslos. Mit anderen Worten: Da die gesamte Verarbeitung für das Postfach auf dem Postfachserver stattfindet, spielt es keine Rolle, welcher Clientzugriffsserver in einem Array von Clientzugriffsservern die einzelnen Clientanforderungen erhält. Diese Änderung an der Funktionalität hat zur Folge, dass auf Lastenausgleichsebene keine Sitzungsaffinität mehr erforderlich ist. Hierdurch können eingehende Verbindungen mit Clientzugriffsservern anhand einfacher Techniken ausgeglichen werden, die durch eine Lastenausgleichstechnologie wie DNS-Roundrobin bereitgestellt werden können. Außerdem können Hardware-Lastenausgleichsgeräte erheblich mehr gleichzeitige Verbindungen unterstützen.

  - **Verbindungspooling** Die Clientzugriffsserver verarbeiten die Clientauthentifizierung und senden die AuthN-Daten an den Postfachserver. Bei dem Konto, das von den Clientzugriffsservern für die Verbindung mit den Postfachservern verwendet wird, handelt es sich um ein privilegiertes Konto, das Mitglied der Gruppe "Exchange-Server" ist. Auf diese Weise können die Clientzugriffsserver Verbindungen mit den Postfachservern effektiv in Pools zusammenfassen. Ein Array mit Clientzugriffsservern kann Millionen Clientverbindungen aus dem Internet verarbeiten; es werden jedoch wesentlich weniger Verbindungen zur Umleitung der Anforderungen an die Postfachserver als in Vorgängerversionen von Exchange verwendet. Dies verbessert die Verarbeitungseffizienz und die End-to-End-Latenz.

## Verwaltungsaufgaben auf dem Clientzugriffsserver

In Exchange 2013 gibt es mehrere wichtige Aufgaben, die auf dem Clientzugriffsserver durchgeführt werden können. Die Verwaltung digitaler Zertifikate wird hauptsächlich auf dem Clientzugriffsserver durchgeführt, ebenso wie ein Teil der Clientprotokollverwaltung für Exchange ActiveSync, POP3 und IMAP4.

