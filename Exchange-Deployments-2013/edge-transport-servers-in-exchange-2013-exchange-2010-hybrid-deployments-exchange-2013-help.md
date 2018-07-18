---
title: 'Edge-Transport-Server in Exchange 2013/Exchange 2010-Hybrid-Bereitstellungen: Exchange 2013 Help'
TOCTitle: Edge-Transport-Server in Exchange 2013/Exchange 2010-Hybrid-Bereitstellungen
ms:assetid: 924f895e-5987-48d0-b113-9d26dcbcdae0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn393965(v=EXCHG.150)
ms:contentKeyID: 59634186
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Edge-Transport-Server in Exchange 2013/Exchange 2010-Hybrid-Bereitstellungen

Dieses Thema ist in Bearbeitung.  

_<strong>Gilt für:</strong>Exchange Online, Exchange Server, Exchange Server 2013_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

Mit Microsoft Exchange bereitgestellte Edge-Transport-Server werden im lokalen Umkreisnetzwerk Ihrer Organisation bereitgestellt. Sie sind keine der Domäne beigetretenen Computer, die den internetseitigen Nachrichtenfluss verarbeiten und als SMTP-Relay und Smarthost für Exchange-Server im internen Netzwerk fungieren.

Exchange 2013 Organisationen, die Edge-Transport-Server verwenden möchten, haben die Möglichkeit, Exchange Server 2013-Edge-Transfer-Server oder Exchange 2010-Edge-Transport-Server mit Service Pack 3 (SP3) für Exchange 2010 bereitzustellen. Verwenden Sie Edge-Transport-Server, wenn Sie den internen Exchange 2013-Clientzugriff oder Postfach-Server nicht direkt mit dem Internet verbinden möchten.

Weitere Informationen zur Exchange 2013-Edge-Transport-Serverrolle finden Sie unter [Edge-Transport-Server](https://technet.microsoft.com/de-de/library/bb124701\(v=exchg.150\)).

Weitere Informationen zur Edge-Transport-Serverrolle für Exchange 2010 finden Sie unter [Übersicht über die Edge-Transport-Serverrolle](http://go.microsoft.com/fwlink/p/?linkid=183473).

## Exchange 2013-Edge-Transport-Server in Exchange 2013-basierten Organisationen mit Hybrid-Bereitstellung

Wenn in einer Hybridbereitstellung Nachrichten zwischen lokalen und Exchange Online-Organisationen weitergeleitet werden, muss der Microsoft EOP-Dienst (Exchange Online Protection) im Auftrag von Exchange Online direkt mit den Edge-Transport-Servern mit Exchange 2013 oder Exchange 2010 SP3 verbunden werden.


> [!IMPORTANT]
> Falls Sie über weitere Exchange 2010-Edge-Transport-Server an anderen Standorten verfügen, die nicht für den Hybridtransport eingesetzt werden, müssen diese Server nicht auf Exchange 2010 SP3 aktualisiert werden. Soll jedoch zukünftig EOP für die Verbindungsherstellung mit zusätzlichen Edge-Transport-Servern für den Hybridtransport verwendet werden, muss für diese Server ein Upgrade auf Exchange 2010 SP3 oder Exchange 2013-Edge-Transport-Server durchgeführt werden.



## Hinzufügen eines Edge-Transport-Servers zu einer Hybridbereitstellung

Die Bereitstellung eines Edge-Transport-Servers in Ihrer lokalen Organisation im Rahmen der Konfiguration einer Hybridbereitstellung ist optional. Während der Konfiguration der Hybridbereitstellung können Sie im Assistenten für die Hybridkonfiguration entweder einen oder mehrere Clientzugriffsserver und Postfachserver für den Hybridtransport von E-Mails auswählen oder festlegen, dass der Hybridtransport von E-Mails in der Exchange Online-Organisation über einen oder mehrere Edge-Transport-Server erfolgt.

Wenn Sie Ihrer Hybridbereitstellung einen Edge-Transport-Server hinzufügen, kommuniziert dieser im Auftrag der internen Exchange 2013-Clientzugriffsservers und Postfachserver mit EOP. Der Edge-Transport-Server fungiert dabei als Relay zwischen dem lokalen Postfachserver und EOP für ausgehende Nachrichten von der lokalen Organisation zu Exchange Online. Ebenso dient der Edge-Transport-Server als Relay zwischen dem lokalen Clientzugriffsserver und EOP für eingehende Nachrichten von der Exchange Online-Organisation zur lokalen Organisation. Die gesamte Verbindungssicherheit, die bisher vom Clientzugriffsserver gesteuert wurde, wird nun durch den Edge-Transport-Server verwaltet. Für die Empfängersuche, die Konformitätsrichtlinien und sonstige Nachrichtenüberprüfungen bleibt weiterhin der Clientzugriffsserver zuständig.

## Nachrichtenfluss ohne Edge-Transport-Server

Die folgende Prozessbeschreibung und Abbildung veranschaulichen den Pfad von Nachrichten zwischen einer lokalen Organisation und Exchange Online, wenn kein Edge-Transport-Server bereitgestellt ist:

1.  Ausgehende Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden von einem Exchange 2010-Postfachserver an einen Exchange 2010-Hub-Transport-Server gesendet.

2.  Der Exchange 2010-Hub-Transport-Server sendet die Nachricht an den Exchange 2013-Postfachserver.

3.  Der Exchange 2013-Postfachserver sendet die Nachricht direkt an das EOP-Unternehmen für Exchange Online.

4.  EOP stellt die Nachricht an die Exchange Online-Organisation zu. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

Nachrichten, die von der Exchange Online-Organisation an Empfänger in der lokalen Organisation gesendet werden, verwenden die umgekehrte Route.

**Nachrichtenfluss in einer Hybridbereitstellung ohne bereitgestellten Edge-Transport-Server**

![Lokal ohne Edge-Transport-Server](images/Dn393965.37bbe430-b157-4f52-83da-6d44f4459425(EXCHG.150).png "Lokal ohne Edge-Transport-Server")

## Nachrichtenfluss mit Edge-Transport-Server

Die folgende Prozessbeschreibung veranschaulicht den Pfad von Nachrichten zwischen einer lokalen Organisation und Exchange Online bei Vorhandensein eines Edge-Transport-Servers. Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden vom Exchange 2010-Postfachserver gesendet:

1.  Ausgehende Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden von einem Exchange 2010-Postfachserver an einen Exchange 2010-Hub-Transport-Server gesendet.

2.  Der Exchange 2010-Hub-Transport-Server sendet die Nachricht an den Exchange 2013-Postfachserver.

3.  Der Exchange 2013-Postfachserver sendet die Nachricht an einen Exchange 2013 oder Exchange 2010 SP3-Edge-Transport-Server.

4.  Der Edge-Transport-Server sendet die Nachricht wiederum an das Exchange Online EOP-Unternehmen.

5.  EOP stellt die Nachricht an die Exchange Online-Organisation zu. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

Nachrichten, die von der Exchange Online-Organisation an Empfänger in der lokalen Organisation gesendet werden, verwenden die umgekehrte Route.

**Nachrichtenfluss in einer Hybrid-Bereitstellung mit bereitgestelltem Exchange 2013 oder 2010 SP3-Edge-Transport-Server**

![Lokal mit Edge-Transport-Server](images/Dn393965.f1039133-249b-401d-bd39-3672442a06c9(EXCHG.150).png "Lokal mit Edge-Transport-Server")

