---
title: 'Transportweiterleitung in Exchange 2013-/Exchange 2007-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Transportweiterleitung in Exchange 2013-/Exchange 2007-Hybridbereitstellungen
ms:assetid: 75cb6e05-82f1-424c-8c13-4b472569a419
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn151303(v=EXCHG.150)
ms:contentKeyID: 54651528
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportweiterleitung in Exchange 2013-/Exchange 2007-Hybridbereitstellungen

 

_**Gilt für:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-07-29_

In diesem Thema werden die verschiedenen Weiterleitungsoptionen für eingehende Nachrichten aus dem Internet und ausgehende Nachrichten ins Internet erläutert.


> [!IMPORTANT]
> Platzieren Sie keine Server, Dienste oder Geräte, die SMTP-Datenverkehr verarbeiten oder ändern, zwischen Ihren lokalen Exchange-Servern und Office 365. Das Sichern der E-Mail-Übertragung zwischen Ihrer lokalen Exchange-Organisation und Office 365 hängt von Informationen ab, die in Nachrichten, die innerhalb der Organisation gesendet werden, enthalten sind. Firewalls, die SMTP-Datenverkehr über TCP-Port 25 ohne Änderung zulassen, werden unterstützt. Wenn ein Server, Dienst oder Gerät eine Nachricht verarbeitet, die zwischen der lokalen Exchange-Organisation und Office 365 gesendet wird, werden diese Informationen entfernt. Wenn dies der Fall ist, wird die Nachricht nicht mehr als organisationsintern eingestuft und unterliegt Antispamfiltern, Transport- und Journalregeln sowie andere Richtlinien, die möglicherweise nicht für die Nachricht gelten.




> [!NOTE]
> Die Beispiele in diesem Thema enthalten nicht das Hinzufügen von Edge-Transport-Servern zu der Hybridbereitstellung. Die Nachrichtenrouten zwischen der lokalen Organisation, der Exchange Online-Organisation und dem Internet ändern sich durch das Hinzufügen eines Edge-Transport-Servers nicht. Die Weiterleitung ändert sich nur innerhalb der lokalen Organisation. Weitere Informationen zum Hinzufügen von Edge-Transport-Servern zu einer Hybridbereitstellung finden Sie unter <A href="edge-transport-servers-in-exchange-2013-exchange-2007-hybrid-deployments-exchange-2013-help.md">Edge-Transport-Server in Exchange 2013/Exchange 2007-Hybrid-Bereitstellungen</A>.



## Eingehende Nachrichten aus dem Internet

Während der Planung und Konfiguration der Hybridbereitstellung müssen Sie entscheiden, ob alle Nachrichten von Absendern im Internet über die Exchange Online-Organisation oder über die lokale Organisation weitergeleitet werden sollen. Alle Nachrichten von Absendern im Internet werden zunächst an die von Ihnen ausgewählte Organisation zugestellt und dann abhängig vom Speicherort des Postfachs des Empfängers weitergeleitet. Ob Sie entscheiden, dass Nachrichten über die Exchange Online-Organisation oder die lokale Organisation weitergeleitet werden, hängt von verschiedenen Faktoren ab, u. a. davon, ob Richtlinien zur Kompatibilität auf alle Nachrichten, die an beide Organisationen gesendet werden, angewendet werden sollen, wie viele Postfächer sich in jeder Organisation befinden usw.

Der Pfad von Nachrichten, die an Empfänger in Ihrer lokalen Organisation und der Exchange Online-Organisation gesendet werden, hängt davon ab, wie Sie den MX-Eintrag in Ihrer Hybridbereitstellung konfigurieren. Es wird empfohlen, dass der MX-Eintrag auf Exchange Online Protection (EOP) in Office 365 verweist, da diese Konfiguration die genaueste Spamfilterung bietet. Der Assistent für die Hybridkonfiguration konfiguriert nicht die Weiterleitung von eingehenden Internet-Nachrichten für die lokale oder die Exchange Online-Organisation. Wenn Sie die Zustellung der eingehenden Internet-E-Mails ändern möchten, müssen Sie den MX-Eintrag manuell konfigurieren.

  - **Falls Sie den MX-Eintrag so ändern, dass er auf den EOP-Dienst (Exchange Online Protection) in Office 365 verweist: **  Dies ist die empfohlene Konfiguration für Hybridbereitstellungen. Alle Nachrichten an Empfänger in den Organisationen werden zunächst über Ihre Exchange Online-Organisation weitergeleitet. Eine an einen Empfänger in der lokalen Organisation adressierte Nachricht wird zunächst über die Exchange Online-Organisation weitergeleitet und dann an den Empfänger in der lokalen Organisation zugestellt. Diese Route wird auch empfohlen, wenn in der Exchange Online-Organisation mehr Empfänger vorhanden sind als in der lokalen Organisation und wenn Nachrichten von EOP gefiltert werden sollen. Diese Konfigurationsoption ist erforderlich, damit Exchange Online Protection Nachrichten auf Spam prüfen und danach filtern kann.

  - **Falls Sie den MX-Eintrag auf Ihre lokale Organisation ausgerichtet lassen: **   Alle Nachrichten an Empfänger in den Organisationen werden zunächst über Ihre lokale Organisation weitergeleitet. Eine an einen Empfänger in Exchange Online adressierte Nachricht wird zunächst über die lokale Organisation weitergeleitet und dann an den Empfänger in Exchange Online zugestellt. Diese Route kann für Organisationen mit Richtlinien zur Kompatibilität hilfreich sein, denen zufolge an eine und von einer Organisation gesendete Nachrichten von einer Lösung zur Journalerstellung geprüft werden müssen. Wenn Sie diese Option wählen, kann Exchange Online Protection Nachrichten nicht effektiv auf Spam prüfen und nicht nach diesen filtern.

Weitere Informationen finden Sie unter [Bewährte Methoden für die Nachrichtenübermittlung für Exchange Online und Office 365 (Übersicht)](https://technet.microsoft.com/de-de/library/jj937232\(v=exchg.150\)).

Lesen Sie den folgendem Abschnitt, in dem gegenübergestellt wird, wie Sie die Weiterleitung von Empfängern aus dem Internet gesendeten Nachrichten an lokale und Exchange Online-Empfänger planen.

## Weiterleiten von eingehenden Internet-Nachrichten über die Exchange Online-Organisation

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad von eingehenden Nachrichten in einer Hybridbereitstellung, wenn Sie den MX-Eintrag so ändern, dass er auf den EOP-Dienst in der Office 365-Organisation verweist. Der Nachrichtenpfad hängt davon ab, ob Sie den zentralen E-Mail-Transport aktivieren.


> [!IMPORTANT]
> Möglicherweise müssen Sie für jedes lokale Postfach, das Nachrichten empfängt, die zuerst an EOP zugestellt und dann über die Exchange Online-Organisation weitergeleitet werden, EOP-Lizenzen erwerben. Weitere Informationen erhalten Sie bei Ihrem Microsoft-Händler.



Wenn der zentrale E-Mail-Transport *deaktiviert* ist (Standardkonfiguration), werden eingehende Internet-Nachrichten in einer Hybridbereitstellung folgendermaßen weitergeleitet:

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger "chris@contoso.com" und "david@contoso.com" gesendet. Chris' Postfach befindet sich auf einem Exchange 2007-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf EOP verweist, wird die Nachricht an EOP zugestellt.

3.  EOP leitet die Nachrichten für beide Empfänger an Exchange Online weiter.

4.  Exchange Online prüft die Nachrichten auf Viren und sucht nach jedem Empfänger. Die Suche ergibt, dass sich Chris' Postfach in der lokalen Organisation befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet.

5.  Exchange Online teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an Davids Postfach zugestellt.

6.  Die zweite Kopie wird von Exchange Online zurück an EOP gesendet.

7.  EOP sendet die Nachricht an die Exchange 2013-Clientzugriffsserver in der lokalen Organisation.

8.  Der Exchange 2013-Clientzugriffsserver sendet die Nachricht über den Routinggruppenconnector, der zwischen dem Exchange 2013-Server und dem Exchange 2007-Server konfiguriert ist, an den Exchange 2007-Postfachserver. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

**Weiterleiten von Nachrichten über die Exchange Online-Organisation an die lokale und die Exchange Online-Organisation bei deaktiviertem zentralen E-Mail-Transport (Standardkonfiguration)**

![Eingehend über Exchange Online ohne zentralisiert](images/Dn151303.725126f3-715e-4be6-bb80-c3a9130ddf3d(EXCHG.150).png "Eingehend über Exchange Online ohne zentralisiert")

Wenn der zentrale E-Mail-Transport *aktiviert* ist, werden eingehende Internet-Nachrichten in einer Hybridbereitstellung folgendermaßen weitergeleitet:

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger "chris@contoso.com" und "david@contoso.com" gesendet. Chris' Postfach befindet sich auf einem Exchange 2007-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf EOP verweist, wird die Nachricht an EOP zugestellt und auf Viren geprüft.

3.  Da der zentrale E-Mail-Transport aktiviert ist, leitet EOP die Nachrichten für beide Empfänger an den lokalen Exchange 2013-Clientzugriffsserver weiter.

4.  Der Exchange 2013-Server führt eine Suche nach den Empfängern aus. Die Suche ergibt, dass sich Chris' Postfach in der lokalen Organisation befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet.

5.  Der Exchange 2013-Server teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an Chris' Postfach auf dem lokalen Exchange 2007-Postfachserver zugestellt.

6.  Die zweite Kopie wird vom Exchange 2013-Server zurück an EOP gesendet.

7.  EOP sendet die Nachricht an Exchange Online.

8.  Exchange stellt die Nachricht an Davids Postfach zu. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

**Weiterleiten von Nachrichten über die Exchange Online-Organisation an die lokale und die Exchange Online-Organisation bei aktiviertem zentralen E-Mail-Transport**

![Eingehend über Exchange Online mit zentralisiert](images/Dn151303.1e0c7f81-2db3-4bf2-84a5-ca59d4e9d5ef(EXCHG.150).png "Eingehend über Exchange Online mit zentralisiert")

## Weiterleiten von eingehenden Internet-Nachrichten über Ihre lokale Organisation

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad von eingehenden Internet-Nachrichten in einer Hybridbereitstellung, wenn Sie den MX-Eintrag auf Ihre lokale Organisation ausgerichtet lassen.

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger "chris@contoso.com" und "david@contoso.com" gesendet. Chris' Postfach befindet sich auf einem Exchange 2007-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf die lokale Organisation verweist, wird die Nachricht an einen Exchange 2007-Hub-Transport-Server zugestellt.

3.  Der Exchange 2007-Postfachserver sucht unter Verwendung des lokalen globalen Katalogservers nach den einzelnen Empfängern. Über die Suche im globalen Katalog ermittelt der Hub-Transport-Server, dass sich Chris' Postfach auf dem Exchange 2007-Postfachserver befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet und die Hybridroutingadresse "david@contoso.mail.onmicrosoft.com" aufweist.

4.  Der Exchange 2007-Postfachserver teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an Chris' Postfach zugestellt.

5.  Die zweite Kopie der Nachricht wird über den Routinggruppenconnector gesendet, der zwischen dem Exchange 2013-Server und dem Exchange 2007-Server konfiguriert ist.

6.  Der Exchange 2013-Postfachserver sendet die Nachricht über einen Sendeconnector, der für die Verwendung von TLS konfiguriert ist, an EOP. EOP erhält Nachrichten, die an die Exchange Online-Organisation gesendet werden.

7.  EOP sendet die Nachricht an die Exchange Online-Organisation, wo sie auf Viren und Spam geprüft und an Davids Postfach zugestellt wird. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

**Weiterleiten von Nachrichten über die lokale Organisation für die lokale und die Exchange Online-Organisation**

![Eingehender Nachrichtenfluss über lokale Organisation](images/Dn151303.1c255e61-6373-4a99-ac9d-0ed4bd4f12dc(EXCHG.150).png "Eingehender Nachrichtenfluss über lokale Organisation")

## Ausgehende Nachrichten ins Internet

Sie können nicht nur festlegen, wie eingehende Nachrichten weitergeleitet werden, die an Empfänger in Ihrer Organisation adressiert sind, sondern auch angeben, wie ausgehende Nachrichten weitergeleitet werden, die von Exchange Online-Empfängern gesendet wurden. Wenn Sie den Assistenten für die Hybridkonfiguration ausführen, können Sie zwischen zwei Optionen wählen:

  - **Zentralen E-Mail-Transport nicht aktivieren**   Diese Option ist im Assistenten für die Hybridkonfiguration standardmäßig ausgewählt und leitet ausgehende Nachrichten aus der Exchange Online-Organisation direkt ins Internet weiter. Verwenden Sie diese Option, wenn es nicht erforderlich ist, lokale Richtlinien zur Kompatibilität oder sonstige Verarbeitungsregeln auf Nachrichten anzuwenden, die von Empfängern in der Exchange Online-Organisation gesendet werden.

  - **Zentralen E-Mail-Transport aktivieren**   Bei Auswahl dieser Option werden ausgehende Nachrichten, die aus der Exchange Online-Organisation gesendet werden, über Ihre lokale Organisation weitergeleitet. Mit Ausnahme von Nachrichten, die an andere Empfänger in derselben Exchange Online-Organisation gesendet wurden, werden alle ausgehenden Nachrichten, die von Empfängern in der Exchange Online-Organisation gesendet wurden, über die lokale Organisation gesendet. Dadurch wird es Ihnen ermöglicht, Kompatibilitätsregeln auf diese Nachrichten sowie andere Prozesse oder Anforderungen anzuwenden, die auf alle Empfänger angewendet werden müssen, unabhängig davon, ob diese zur Exchange Online- oder zur lokalen Organisation gehören.
    

    > [!NOTE]
    > Der zentrale E-Mail-Transport wird nur für Organisationen empfohlen, die aufgrund der Richtlinientreue spezielle Transportanforderungen haben. Für typische Exchange-Organisationen empfiehlt es sich, den zentralen E-Mail-Transport nicht zu aktivieren.



Von lokalen Empfängern gesendete Nachrichten werden immer direkt über DNS an Empfänger im Internet gesendet, unabhängig davon, welche der oben genannten Optionen Sie im Assistenten für die Hybridkonfiguration auswählen.

Die folgenden Schritte und die Abbildung veranschaulichen den Pfad ausgehender Nachrichten für Nachrichten, die von lokalen Empfängern gesendet werden.

1.  Chris, der über ein Postfach auf dem lokalen Exchange 2007-Postfachserver verfügt, sendet über das Internet eine Nachricht an den externen Empfänger "erin@cpandl.com".

2.  Der Exchange 2007-Postfachserver sendet die Nachricht an den Exchange 2007-Hub-Transport-Server.

3.  Der Exchange 2007-Hub-Transport-Server schlägt den MX-Eintrag für "cpandl.com" nach und sendet die Nachricht an die "cpandl.com"-Postfachserver, die sich im Internet befinden.

**Nachrichten von lokalen Absendern an Empfänger im Internet**

![Ausgehendes Routing aus nur lokal](images/Dn151303.ad3beba1-0330-473f-9f7c-cec53995d055(EXCHG.150).png "Ausgehendes Routing aus nur lokal")

Lesen Sie den folgendem Abschnitt, in dem gegenübergestellt wird, wie Sie die Weiterleitung aller von Empfängern in der Exchange Online-Organisation gesendeten Nachrichten an Empfänger im Internet planen.

## Zustellen von Internet-Nachrichten aus Exchange Online mithilfe von DNS (zentraler E-Mail-Transport deaktiviert)

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad für ausgehende Nachrichten, die von Exchange Online-Empfängern an Empfänger im Internet gesendet werden, wenn die Option **Zentralen E-Mail-Transport aktivieren** im Assistenten für die Hybridkonfiguration nicht ausgewählt ist (Standardkonfiguration).

1.  David, der über ein Postfach in der Exchange Online-Organisation verfügt, sendet über das Internet eine Nachricht an den externen Empfänger "erin@cpandl.com".

2.  Exchange Online prüft die Nachricht auf Viren und sendet sie an den Exchange-EOP-Dienst.

3.  EOP schlägt den MX-Eintrag für "cpandl.com" nach und sendet die Nachricht an die "cpandl.com"-Postfachserver im Internet.

**Direkte Weiterleitung von E-Mails von Exchange Online-Absendern ins Internet bei deaktiviertem zentralen E-Mail-Transport (Standardkonfiguration)**

![Ausgehendes Routing direkt von Exchange Online](images/Dn151303.05f002e6-c5c9-47f0-962c-f3bba824e28f(EXCHG.150).png "Ausgehendes Routing direkt von Exchange Online")

## Weiterleiten von Nachrichten aus Exchange Online ins Internet über die lokale Organisation (zentraler E-Mail-Transport aktiviert)

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad für ausgehende Nachrichten, die von Exchange Online-Empfängern an Empfänger im Internet gesendet werden, wenn die Option **Zentralen E-Mail-Transport aktivieren** im Assistenten für die Hybridkonfiguration ausgewählt wird.

1.  David, der über ein Postfach in der Exchange Online-Organisation verfügt, sendet über das Internet eine Nachricht an den externen Empfänger "erin@cpandl.com".

2.  Exchange Online prüft die Nachricht auf Viren und sendet sie an EOP.

3.  Da EOP so konfiguriert ist, dass alle ins Internet gehenden Nachrichten an einen lokalen Server gesendet werden, wird die Nachricht an einen Exchange 2013-Clientzugriffsserver weitergeleitet. Die Nachricht wird mit TLS gesendet.

4.  Der Exchange 2013-Clientzugriffsserver führt an Davids Nachricht sämtliche Konformitäts-, Virenschutz- und sonstigen Prozesse aus, die vom Administrator konfiguriert wurden.

5.  Der Exchange 2013 Clientzugriffsserver leitet die Nachricht an den Exchange 2007-Hub-Transport-Server weiter. In diesem Beispiel sind die Clientzugriffsrolle und die Postfachserverrolle auf dem gleichen Exchange 2013-Server installiert.

6.  Der Exchange 2007-Hub-Transport-Server schlägt den MX-Eintrag für "cpandl.com" nach und sendet die Nachricht an die "cpandl.com"-Postfachserver, die sich im Internet befinden.

**Weiterleitung von E-Mails von Exchange Online-Absendern über die lokale Organisation bei aktiviertem zentralen E-Mail-Transport**

![Ausgehend aus Exchange Online über lokal](images/Dn151303.fe2f0e69-0779-4d96-b020-34a2015f61f2(EXCHG.150).png "Ausgehend aus Exchange Online über lokal")

