---
title: 'Edge-Transport-Server in Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Edge-Transport-Server in Hybridbereitstellungen
ms:assetid: 166b1490-5c56-40df-a17b-e8bb36224fd9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh134662(v=EXCHG.150)
ms:contentKeyID: 50477178
ms.date: 04/26/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Edge-Transport-Server in Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2018-04-16_

Die Edge-Transport-Serverrolle ist eine optionale Rolle, die in der Regel auf einem Computer im Umkreisnetzwerk der Exchange-Organisation bereitgestellt wird und darauf ausgelegt ist, die Angriffsfläche der Organisation auf ein Mindestmaß zu reduzieren. Die Edge-Transport-Serverrolle verarbeitet den gesamten Internetnachrichtenfluss, der SMTP-Relay- und Smarthost-Dienste für die internen lokalen Exchange-Server in Ihrer Organisation bereitstellt.

## Edge-Transport-Server in Exchange-basierten Organisationen mit Hybridbereitstellung

Exchange 2016-Organisationen, die Edge-Transport-Server verwenden möchten, können Edge-Transport-Server bereitstellen, auf denen die neueste Version von Exchange 2016 und neuer, Exchange 2013 oder Exchange 2010 ausgeführt wird. Sie sollten Edge-Transport-Server verwenden, wenn interne Exchange-Server nicht direkt für das Internet verfügbar sein sollen. Beim Bereitstellen eines Edge-Transport-Servers in einer Hybridbereitstellung stellt Exchange Online über den Exchange Online Protection-Dienst eine Verbindung zu Ihrem Edge-Transport-Server her, um Nachrichten zu senden. Anschließend sendet der Edge-Transport-Server die Nachrichten an den lokalen Exchange-Postfachserver, auf dem sich das Empfängerpostfach befindet.


> [!IMPORTANT]
> Platzieren Sie keine Server, Dienste oder Geräte, die SMTP-Datenverkehr verarbeiten oder ändern, zwischen Ihren lokalen Exchange-Servern und Office 365. Das Sichern der E-Mail-Übertragung zwischen Ihrer lokalen Exchange-Organisation und Office 365 hängt von Informationen ab, die in Nachrichten, die innerhalb der Organisation gesendet werden, enthalten sind. Firewalls, die SMTP-Datenverkehr über TCP-Port 25 ohne Änderung zulassen, werden unterstützt. Wenn ein Server, Dienst oder Gerät eine Nachricht verarbeitet, die zwischen der lokalen Exchange-Organisation und Office 365 gesendet wird, werden diese Informationen entfernt. Wenn dies der Fall ist, wird die Nachricht nicht mehr als organisationsintern eingestuft und unterliegt Antispamfiltern, Transport- und Journalregeln sowie andere Richtlinien, die möglicherweise nicht für die Nachricht gelten.




> [!IMPORTANT]
> Falls Sie über weitere Exchange-Edge-Transport-Server an anderen Standorten verfügen, die nicht für den Hybridtransport eingesetzt werden, müssen diese Server nicht aktualisiert werden, um eine Hybridbereitstellung zu unterstützen. Soll jedoch zukünftig EOP für die Verbindungsherstellung mit zusätzlichen Edge-Transport-Servern für den Hybridtransport verwendet werden, muss auf den Servern die neueste Version von Exchange 2016 und neuer, Exchange 2010 oder Exchange 2013 ausgeführt werden.



## Hinzufügen eines Edge-Transport-Servers zu einer Hybridbereitstellung

Die Bereitstellung eines Edge-Transport-Servers in Ihrer lokalen Organisation im Rahmen der Konfiguration einer Hybridbereitstellung ist optional. Während der Konfiguration der Hybridbereitstellung können Sie im Assistenten für die Hybridkonfiguration entweder einen oder mehrere interne lokale Exchange-Server auswählen oder festlegen, dass der Hybridtransport von E-Mails in der Exchange Online-Organisation über einen oder mehrere Edge-Transport-Server erfolgt.

Wenn Sie Ihrer Hybridbereitstellung einen Edge-Transport-Server hinzufügen, kommuniziert dieser im Auftrag des internen Exchange-Servers mit EOP. Der Edge-Transport-Server fungiert dabei als Relay zwischen den lokalen Exchange-Servern und EOP für ausgehende Nachrichten von der lokalen Organisation zur Exchange Online-Organisation. Ebenso dient der Edge-Transport-Server als Relay zwischen den internen Exchange-Servern für eingehende Nachrichten von der Exchange Online-Organisation zur lokalen Organisation. Die gesamte Verbindungssicherheit, die bisher von internen Exchange-Servern gesteuert wurde, wird nun durch den Edge-Transport-Server verwaltet. Für die Empfängersuche, die Konformitätsrichtlinien und sonstige Nachrichtenüberprüfungen bleiben weiterhin die internen Exchange-Server zuständig.

Wenn Sie Ihrer Hybridbereitstellung einen Edge-Transport-Server hinzufügen, ist es nicht erforderlich, Nachrichten, die zwischen lokalen Benutzern und Empfängern im Internet gesendet werden, über diesen weiterzuleiten. Nur Nachrichten, die zwischen der lokalen und der Exchange Online-Organisation gesendet werden, werden über den Edge-Transport-Server weitergeleitet.

## Nachrichtenfluss ohne Edge-Transport-Server

Die folgende Prozessbeschreibung und Abbildung veranschaulichen den Pfad von Nachrichten zwischen einer lokalen Organisation und Exchange Online, wenn kein Edge-Transport-Server bereitgestellt ist:

1.  Ausgehende Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden von einem Postfach auf einem internen Exchange-Server gesendet.

2.  Der Exchange-Server sendet die Nachricht direkt an EOP.

3.  EOP stellt die Nachricht an die Exchange Online-Organisation zu.

Nachrichten, die von der Exchange Online-Organisation an Empfänger in der lokalen Organisation gesendet werden, verwenden die umgekehrte Route.

**Nachrichtenfluss in einer Hybridbereitstellung ohne bereitgestellten Edge-Transport-Server**

![Hybrid-Nachrichtenfluss ohne Edge-Transport-Server](images/Hh134662.a95b4d1e-fd4a-4952-b891-22f84c9e71a3(EXCHG.150).png "Hybrid-Nachrichtenfluss ohne Edge-Transport-Server")

## Nachrichtenfluss mit Edge-Transport-Server

Die folgende Prozessbeschreibung veranschaulicht den Pfad von Nachrichten zwischen einer lokalen Organisation und Exchange Online bei Einsatz eines Edge-Transport-Servers. Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden vom internen Exchange-Server gesendet:

1.  Nachrichten von der lokalen Organisation an Empfänger in der Exchange Online-Organisation werden von einem Postfach auf einem internen Exchange-Server gesendet.

2.  Der Exchange-Server sendet die Nachricht an einen Edge-Transport-Server, auf dem eine unterstützte Version von Exchange ausgeführt wird.

3.  Der Edge-Transport-Server sendet die Nachricht an EOP.

4.  EOP stellt die Nachricht an die Exchange Online-Organisation zu.

Nachrichten, die von der Exchange Online-Organisation an Empfänger in der lokalen Organisation gesendet werden, verwenden die umgekehrte Route.

**Nachrichtenübermittlung in einer Hybridbereitstellung mit bereitgestelltem Edge-Transport-Server**

![Hybrid-Nachrichtenfluss mit Edge-Transport-Server](images/Hh134662.821fe099-56f5-4501-8e1a-e184ba07a653(EXCHG.150).png "Hybrid-Nachrichtenfluss mit Edge-Transport-Server")

