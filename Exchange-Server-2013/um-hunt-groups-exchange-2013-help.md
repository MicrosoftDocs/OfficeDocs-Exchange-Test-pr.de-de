---
title: 'UM-Sammelanschlüsse: Exchange 2013 Help'
TOCTitle: UM-Sammelanschlüsse
ms:assetid: 026129a1-b0b5-410a-bed6-2d49f85205b3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995918(v=EXCHG.150)
ms:contentKeyID: 50554809
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-Sammelanschlüsse

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-18_

Ein telefonischer Sammelanschluss bietet eine Möglichkeit, Telefonanrufe einer einzelnen Nummer an mehrere Durchwahlen oder Telefonnummern zu verteilen. In Unified Messaging (UM) ist ein UM-Sammelanschluss die logische Abbildung eines telefonischen Sammelanschlusses und dient zum Verbinden eines UM-IP-Gateways mit einem UM-Wählplan.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Unified Messaging-Sammelanschlüssen gibt? Weitere Informationen finden Sie unter [Um-Sammelanschlüsse Gruppieren von Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-hunt-group-procedures).

**Inhalt**

Was ist ein Sammelanschluss?

Was ist eine Pilotnummer?

Was ist ein UM-Sammelanschluss?

## Was ist ein Sammelanschluss?

Der Begriff *Sammelanschluss* dient der Bezeichnung einer Gruppe von Durchwahlnummern von Nebenstellenanlagen bzw. IP-Nebenstellenanlagen, die von Benutzern gemeinsam verwendet werden. Sammelanschlüsse werden für das effiziente Verteilen der eingehenden und ausgehenden Anrufe einer bestimmten Unternehmenseinheit verwendet. Das Erstellen und Definieren eines Sammelanschlusses verringert die Wahrscheinlichkeit, dass der Anrufer bei einem eingehenden Anruf ein Besetztzeichen hört, wenn sein Anruf empfangen wird.

Sammelanschlüsse dienen zum Bestimmen offener Leitungen, Durchwahlen oder Kanäle, wenn ein Anruf eingeht. Anrufe werden an die nächste verfügbare Leitung weitergeleitet, wenn die Haupttelefonleitung besetzt ist oder der Anruf nicht entgegengenommen wird. Der Anrufer erhält ein Besetztzeichen oder wird an Voicemail weitergeleitet, wenn keine Durchwahlen in der Gruppe verfügbar sind. Eine Nebenstellenanlage- oder IP-Nebenstellenanlage kann z. B. so konfiguriert sein, dass sie 10 Durchwahlnummern für die Vertriebsabteilung besitzt. Diese 10 Vertriebsdurchwahlnummern würden als ein Sammelanschluss konfiguriert.

Zu den Einstellungen eines einfachen Sammelanschlusses gehören Name, Durchwahlnummer, Liste verfügbarer Mitglieder und Auswahlmethode für den Sammelanschluss. Die Methode zur Auswahl des Sammelanschlusses bestimmt die Reihenfolge, in der eingehende Anrufe an die Mitglieder des Sammelanschlusses weitergeleitet werden.

Es gibt mehrere Algorithmen oder Methoden, gemäß denen eine Nebenstellenanlage bzw. IP-Nebenstellenanlage geöffnete Leitungen, Durchwahlen oder Kanäle bestimmen können. Dabei handelt es sich um folgende Verfahren:

  - **Gruppenweise Nummernwahl oder alle Durchwahlen anrufen**   Wenn ein eingehender Anruf von der Durchwahlnummer des Sammelanschlusses empfangen wird, bringt die Nebenstellenanlage bzw. IP-Nebenstellenanlage alle Durchwahlnummer des Sammelanschlusses zum Klingeln.

  - **Mit der niedrigsten Nummer beginnen oder lineare Suche**   Dies ist die Standardeinstellungen bei den meisten Nebenstellenanlagen bzw. IP-Nebenstellenanlagen. Bei dieser Methode werden Anrufe in sequenzieller Reihenfolge an die erste freie Leitung beginnend mit der ersten Leitung in der Gruppe weitergeleitet. Diese Konfiguration ist am häufigsten bei Multiplex-Telefonen in Kleinunternehmen anzutreffen.

  - **Roundrobin oder Umlaufsuche**   Bei dieser Methode werden Anrufe an die erste freie Leitung weitergeleitet beginnend mit der Leitung nach derjenigen, die den letzten Anruf abgewickelt hat. Wenn bei Verteilung von Anrufen mit dieser Methode ein Anruf an Leitung 1 übermittelt wird, geht der nächste Anruf an Leitung 2, der nächste an Leitung 3 usw. Dieser Prozess wird fortgesetzt, auch wenn eine der vorherigen Leitungen frei wird. Wenn das Ende des Sammelanschlusses erreicht ist, beginnt die Suche wieder bei der ersten Leitung. Leitungen werden nur übersprungen, wenn sie noch durch einen früheren Anruf besetzt sind. Durch das Roundrobin-Verfahren werden Anrufe gleichmäßig verteilt, wodurch die Wahrscheinlichkeit einer größeren Dienstunterbrechung minimiert wird.

  - **Am längsten im Leerlauf oder gleichförmige Verteilung**   Bei dieser Methode wird der Anruf an die erste freie Leitung in der Gruppe weitergeleitet, die am längsten im Leerlauf ist. Bei dieser Methode wird die Dauer berücksichtigt, die die Person, die den Anruf angenommen hat, beschäftigt war, und nicht, ob die Leitung verfügbar ist. Diese Methode wird zumeist in großen Callcentern befolgt, in denen eingehende Anrufe von Mitarbeitern beantwortet und die Arbeitslast gleichmäßig auf die Gruppe der Durchwahlen verteilt wird.

Sie können einen oder mehrere Sammelanschlüsse konfigurieren. Jeder Sammelanschluss muss mindestens zwei Leitungen aufweisen. Wenn eine Nummer bereits zu einem Sammelanschluss gehört, steht sie für den anderen nicht zur Verfügung.

Es folgen Beispiele einfacher telefonischer Sammelanschlüsse und ihrer Funktionsweise.

**Beispiel 1**

Die Durchwahl 300 (Pilotnummer) ist so programmiert, dass bei einem eingehenden Anruf erst die Durchwahl 301, dann 302, dann 303, dann 304 angerufen wird.

1.  Durchwahl 301 ist besetzt.

2.  Durchwahl 302 klingelt und wird nicht beantwortet.

3.  Durchwahl 303 beantwortet den Anruf.

4.  Durchwahl 304 ist frei und wartet auf einen eingehenden Anruf.

**Beispiel 2**

Die Durchwahl 1000 (Pilotnummer) ist so programmiert, dass bei einem eingehenden Anruf alle Durchwahlen von 2000 bis 2003 gleichzeitig klingeln:

1.  Durchwahl 2000 ist frei.

2.  Durchwahl 2001 ist frei.

3.  Durchwahl 2002 ist frei.

4.  Durchwahl 2003 beantwortet den Anruf.

Was ist ein Sammelanschluss?

## Was ist eine Pilotnummer?

In einem Telefonienetzwerk kann eine Nebenstellenanlage oder IP-Nebenstellenanlage so konfiguriert werden, dass sie eine mehrere Sammelanschlussgruppen hat. Jeder Sammelanschluss, der für eine Nebenstellenanlage oder IP-Nebenstellenanlage erstellt wird, muss eine zugehörige *Pilotnummer* aufweisen. Wenn eine Pilotnummer verwendet wird, werden Besetztzeichen vermieden und eingehende Anrufe an die Durchwahlen weitergeleitet, die verfügbar sind. Die Nebenstellenanlage oder IP-Nebenstellenanlage verwendet die Pilotnummer, um den Sammelanschluss und die Telefondurchwahlnummer zu ermitteln, an der der eingehende Anruf empfangen wurde, und die Durchwahlen zu bestimmen, die dem Sammelanschluss zugewiesen sind. Ohne eine definierte Pilotnummer kann die Nebenstellenanlage- oder IP-Nebenstellenanlage nicht ermitteln, wo der eingehende Anruf empfangen wurde.

Eine Pilotnummer ist die Adresse, Durchwahl oder Position des Sammelanschlusses in der Nebenstellenanlage oder IP-Nebenstellenanlage. Sie wird im Allgemeinen als leere Durchwahlnummer oder Durchwahlnummer eines aus mehreren Durchwahlnummern bestehenden Sammelanschlusses definiert, die keiner Person bzw. keinem Telefon zugeordnet ist. Angenommen, Sie konfigurieren einen Sammelanschluss in einer Nebenstellenanlage oder IP-Nebenstellenanlage so, dass die Durchwahlnummern 4100, 4101, 4102, 4103, 4104 und 4105 enthalten sind. Die Pilotnummer für den Sammelanschluss wird als Durchwahl 4100 konfiguriert. Wenn ein Anruf für die Durchwahl 4100 eingeht, sucht die Nebenstellenanlage oder IP-Nebenstellenanlage nach der nächsten verfügbaren Durchwahlnummer, um so zu ermitteln, wohin der Anruf weitergeleitet werden soll. In diesem Beispiel untersucht die Nebenstellenanlage oder IP-Nebenstellenanlage mithilfe eines programmierten Suchalgorithmus die Durchwahlnummern 4101, 4102, 4103, 4104 und 4105.

Wenn eine Pilotnummer verwendet wird, werden Besetztzeichen vermieden und eingehende Anrufe an die Durchwahlnummern weitergeleitet, die verfügbar sind. In Unified Messaging wird die Pilotnummer der Nebenstellenanlage oder IP-Nebenstellenanlage als Ziel verwendet. Wenn keine der Durchwahlnummern des Sammelanschlusses einen eingehenden Anruf beantwortet, wird der Anruf an einem Postfachserver weitergeleitet, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird.

Was ist ein Sammelanschluss?

## Was ist ein UM-Sammelanschluss?

Unified Messaging-Sammelanschlüsse sind für den Betrieb des Unified Messaging-Systems wichtig. Der UM-Sammelanschluss ist eine logische Darstellung eines vorhandenen Sammelanschlusses einer Nebenstellenanlage oder IP-Nebenstellenanlage. Seit Zweck ist die Verbindung eines UM-IP-Gateways mit einem UM-Wählplan. Mithilfe eines einzelnen UM-Sammelanschlusses können mehrere UM-IP-Gateways mit einem UM-Wählplan verbunden werden. Wenn Sie ein UM-IP-Gateway erstellen und mit einem UM-Wählplan verknüpfen, wird standardmäßig ein UM-Sammelanschluss erstellt. Sie können außerdem weitere Sammelanschlüsse erstellen. Sie müssen mindestens einen UM-Sammelanschluss erstellen.

UM-Sammelanschlüsse werden zum Ermitteln des Sammelanschlusses der Nebenstellenanlage oder IP-Nebenstellenanlage verwendet, von dem der eingehende Anruf empfangen wurde. Eine für einen Sammelanschluss in der Nebenstellenanlage oder IP-Nebenstellenanlage definierte Pilotnummer muss auch innerhalb des UM-Sammelanschlusses definiert werden. Die Pilotnummer wird zum Zuordnen der Informationen verwendet, die für eingehende Anrufe über die SIP-Signalnachrichteninformationen (Session Initiation Protocol) zu der Sprachnachricht bereitgestellt werden. Anhand der Pilotnummer können Exchange-Server den Anruf zusammen mit dem richtigen Wählplan interpretieren, damit der Anruf ordnungsgemäß weitergeleitet werden kann. Wenn kein Sammelanschluss vorhanden ist, können Exchange-Server den Ort des eingehenden Anrufs nicht ermitteln. Wenn Exchange-Server den Ort eingehender Anrufe feststellen, können sie die Anrufheaderinformationen übernehmen, die vom VoIP-Gateway, von der IP-Nebenstellenanlage oder der SIP-fähigen Nebenstellenanlage übermittelt werden. Es ist außerordentlich wichtig, die UM-Sammelanschlüsse ordnungsgemäß zu konfigurieren, weil eingehende Anrufe, die der für den UM-Sammelanschluss definierten Pilotnummer nicht eindeutig entsprechen, nicht beantwortet werden und die Weiterleitung eingehender Anrufe nicht funktioniert.

Wenn Sie in lokalen und Hybridbereitstellungen einen UM-Sammelanschluss erstellen, ermöglichen Sie allen Clientzugriffs- und Postfachservern die Kommunikation mit einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einer SIP-fähigen Nebenstellenanlage – unabhängig davon, ob sie einem UM-Wählplan hinzugefügt wurden. Dies liegt daran, dass alle Clientzugriffs- und Postfachserver eingehende Anrufe für alle Wählpläne beantworten anstatt für einen bestimmten UM-Wählplan (wie der UM-Server in Vorgängerversionen von Exchange). Wenn Sie den UM-Sammelanschluss löschen, kann das dazugehörige UM-IP-Gateway keine von einem VoIP-Gateway, einer IP-Nebenstellenanlage oder SIP-fähigen Nebenstellenanlage eingehenden Anrufe beantworten oder ausgehende Anrufe über das VoIP-Gateway, die IP-Nebenstellenanlage oder SIP-fähige Nebenstellenanlage mithilfe der angegebenen Pilotnummer ausführen.

Wenn Sie in lokalen und Hybridbereitstellungen jedoch UM in Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren, müssen Sie alle Clientzugriffs- und Postfachserver allen SIP-URI-Wählplänen hinzufügen, die für die Arbeit mit Communications Server 2007 R2 oder Lync Server erstellt wurden. Dadurch können Anrufweiterleitung und Outdialing ordnungsgemäß funktionieren.

Weitere Informationen zu UM-IP-Gateways finden Sie unter [UM-IP-Gateways](um-ip-gateways-exchange-2013-help.md).

