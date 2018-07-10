---
title: 'Transportweiterleitung in Exchange-Hybrid-Bereitstellungen: Exchange 2013 Help'
TOCTitle: Transportweiterleitung in Exchange-Hybrid-Bereitstellungen
ms:assetid: 36c2cea3-2e2f-40ac-88bd-7e1b6bd27828
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659050(v=EXCHG.150)
ms:contentKeyID: 50477180
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportweiterleitung in Exchange-Hybrid-Bereitstellungen

 

_<strong>Gilt für:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-07-29_

In diesem Thema werden die verschiedenen Weiterleitungsoptionen für eingehende Nachrichten aus dem Internet und ausgehende Nachrichten ins Internet erläutert.


> [!IMPORTANT]
> Platzieren Sie keine Server, Dienste oder Geräte, die SMTP-Datenverkehr verarbeiten oder ändern, zwischen Ihren lokalen Exchange-Servern und Office 365. Das Sichern der E-Mail-Übertragung zwischen Ihrer lokalen Exchange-Organisation und Office 365 hängt von Informationen ab, die in Nachrichten, die innerhalb der Organisation gesendet werden, enthalten sind. Firewalls, die SMTP-Datenverkehr über TCP-Port 25 ohne Änderung zulassen, werden unterstützt. Wenn ein Server, Dienst oder Gerät eine Nachricht verarbeitet, die zwischen der lokalen Exchange-Organisation und Office 365 gesendet wird, werden diese Informationen entfernt. Wenn dies der Fall ist, wird die Nachricht nicht mehr als organisationsintern eingestuft und unterliegt Antispamfiltern, Transport- und Journalregeln sowie andere Richtlinien, die möglicherweise nicht für die Nachricht gelten.




> [!NOTE]
> Die Beispiele in diesem Thema enthalten nicht das Hinzufügen von Edge-Transport-Servern zu der Hybridbereitstellung. Die Nachrichtenrouten zwischen der lokalen Organisation, der Exchange Online-Organisation und dem Internet ändern sich durch das Hinzufügen eines Edge-Transport-Servers nicht. Die Weiterleitung ändert sich nur innerhalb der lokalen Organisation. Weitere Informationen zum Hinzufügen von Edge-Transport-Servern zu einer Hybridbereitstellung finden Sie unter <A href="edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md">Edge-Transport-Server in Hybridbereitstellungen</A>.



## Eingehende Nachrichten aus dem Internet

Während der Planung und Konfiguration der Hybridbereitstellung müssen Sie entscheiden, ob alle Nachrichten von Absendern im Internet über die Exchange Online-Organisation oder über die lokale Organisation weitergeleitet werden sollen. Alle Nachrichten von Absendern im Internet werden zunächst an die von Ihnen ausgewählte Organisation zugestellt und dann abhängig vom Speicherort des Postfachs des Empfängers weitergeleitet. Ob Sie entscheiden, dass Nachrichten über die Exchange Online-Organisation oder die lokale Organisation weitergeleitet werden, hängt von verschiedenen Faktoren ab, u. a. davon, ob Richtlinien zur Kompatibilität auf alle Nachrichten, die an beide Organisationen gesendet werden, angewendet werden sollen, wie viele Postfächer sich in jeder Organisation befinden usw.

Der Pfad von Nachrichten, die an Empfänger in Ihrer lokalen Organisation und der Exchange Online-Organisation gesendet werden, hängt davon ab, wie Sie den MX-Eintrag in Ihrer Hybridbereitstellung konfigurieren. Es wird empfohlen, dass der MX-Eintrag auf Exchange Online Protection (EOP) in Office 365 verweist, da diese Konfiguration die genaueste Spamfilterung bietet. Der Assistent für die Hybridkonfiguration konfiguriert nicht die Weiterleitung von eingehenden Internet-Nachrichten für die lokale oder die Exchange Online-Organisation. Wenn Sie die Zustellung der eingehenden Internet-E-Mails ändern möchten, müssen Sie den MX-Eintrag manuell konfigurieren.

  - **Falls Sie den MX-Eintrag so ändern, dass er auf den EOP-Dienst (Exchange Online Protection) in Office 365 verweist** Dies ist die empfohlene Konfiguration für Hybridbereitstellungen. Alle Nachrichten an Empfänger in den Organisationen werden zunächst über Ihre Exchange Online-Organisation weitergeleitet. Eine an einen Empfänger in der lokalen Organisation adressierte Nachricht wird zunächst über die Exchange Online-Organisation weitergeleitet und dann an den Empfänger in der lokalen Organisation zugestellt. Diese Route wird auch empfohlen, wenn in der Exchange Online-Organisation mehr Empfänger vorhanden sind als in der lokalen Organisation. Diese Konfigurationsoption ist erforderlich, damit Exchange Online Protection Nachrichten auf Spam prüfen und danach filtern kann.

  - **Falls Sie den MX-Eintrag auf Ihre lokale Organisation ausgerichtet lassen:**    Alle Nachrichten an Empfänger in den Organisationen werden zunächst über Ihre lokale Organisation weitergeleitet. Eine an einen Empfänger in Exchange Online adressierte Nachricht wird zunächst über die lokale Organisation weitergeleitet und dann an den Empfänger in Exchange Online zugestellt. Diese Route kann für Organisationen mit Richtlinien zur Kompatibilität hilfreich sein, denen zufolge an eine und von einer Organisation gesendete Nachrichten von einer Lösung zur Journalerstellung geprüft werden müssen. Wenn Sie diese Option wählen, kann Exchange Online Protection Nachrichten nicht effektiv auf Spam prüfen und nicht nach diesen filtern.

Weitere Informationen finden Sie unter [Bewährte Methoden für die Nachrichtenübermittlung für Exchange Online und Office 365 (Übersicht)](https://technet.microsoft.com/de-de/library/jj937232\(v=exchg.150\)).

Lesen Sie den folgendem Abschnitt, in dem gegenübergestellt wird, wie Sie die Weiterleitung von Empfängern aus dem Internet gesendeten Nachrichten an lokale und Exchange Online-Empfänger planen. In jedem Abschnitt kann der „lokale Exchange-Server“ entweder ein Exchange 2013-Clientzugriffsserver oder ein Exchange 2016-Postfachserver sein.

## Weiterleiten von eingehenden Internet-Nachrichten über die Exchange Online-Organisation

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad von eingehenden Nachrichten in einer Hybridbereitstellung, wenn Sie den MX-Eintrag so ändern, dass er auf den EOP-Dienst in der Office 365-Organisation verweist. Der Nachrichtenpfad hängt davon ab, ob Sie den zentralen E-Mail-Transport aktivieren.


> [!IMPORTANT]
> Möglicherweise müssen Sie für jedes lokale Postfach, das Nachrichten empfängt, die zuerst an EOP zugestellt und dann über die Exchange Online-Organisation weitergeleitet werden, EOP-Lizenzen erwerben. Weitere Informationen erhalten Sie bei Ihrem Microsoft-Händler.



Wenn der zentrale E-Mail-Transport **deaktiviert** ist (Standardkonfiguration), werden eingehende Internet-Nachrichten in einer Hybridbereitstellung folgendermaßen weitergeleitet:

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger „julie@contoso.com“ und „david@contoso.com“ gesendet. Julies Postfach befindet sich auf einem Exchange-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf EOP verweist, wird die Nachricht an EOP zugestellt.

3.  EOP leitet die Nachrichten für beide Empfänger an Exchange Online weiter.

4.  Exchange Online prüft die Nachrichten auf Viren und sucht nach jedem Empfänger. Die Suche ergibt, dass sich Julies Postfach in der lokalen Organisation befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet.

5.  Exchange Online teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an Davids Postfach zugestellt.

6.  Die zweite Kopie wird von Exchange Online zurück an EOP gesendet.

7.  EOP sendet die Nachricht an einen lokalen Exchange-Server in der lokalen Organisation.

8.  Ein Exchange sendet die Nachricht an den Exchange-Postfachserver, von wo sie an das Postfach von Julie zugestellt wird.

**Weiterleiten von Nachrichten über die Exchange Online-Organisation an die lokale und die Exchange Online-Organisation bei deaktiviertem zentralen E-Mail-Transport (Standardkonfiguration)**

![Zentral eingehend zu EXO](images/JJ659050.f98341e0-088d-49f0-bf8e-09f35255bf9e(EXCHG.150).png "Zentral eingehend zu EXO")

Wenn der zentrale E-Mail-Transport **aktiviert** ist, werden eingehende Internet-Nachrichten in einer Hybridbereitstellung folgendermaßen weitergeleitet:

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger „julie@contoso.com“ und „david@contoso.com“ gesendet. Julies Postfach befindet sich auf einem Exchange-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf EOP verweist, wird die Nachricht an EOP zugestellt und auf Viren geprüft.

3.  Da der zentrale E-Mail-Transport aktiviert ist, leitet EOP die Nachrichten für beide Empfänger an einen lokalen Exchange-Server weiter.

4.  Der lokale Exchange-Server führt eine Suche nach den Empfängern aus. Die Suche ergibt, dass sich Julies Postfach in der lokalen Organisation befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet.

5.  Der lokale Exchange-Server teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an Julies Postfach auf dem lokalen Exchange-Postfachserver gesendet.

6.  Die zweite Kopie wird vom lokalen Exchange-Server zurück an EOP gesendet.

7.  EOP sendet die Nachricht an Exchange Online.

8.  Exchange stellt die Nachricht an Davids Postfach zu.

**Weiterleiten von Nachrichten über die Exchange Online-Organisation an die lokale und die Exchange Online-Organisation bei aktiviertem zentralen E-Mail-Transport**

![Eingehendes EXO, zentral aktiviert](images/JJ659050.062422d5-9cb6-42c2-9ec0-31962cd7ada6(EXCHG.150).png "Eingehendes EXO, zentral aktiviert")

## Weiterleiten von eingehenden Internet-Nachrichten über Ihre lokale Organisation

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad von eingehenden Internet-Nachrichten in einer Hybridbereitstellung, wenn Sie den MX-Eintrag auf Ihre lokale Organisation ausgerichtet lassen.

1.  Eine eingehende Nachricht wurde von einem Internetabsender an die Empfänger „julie@contoso.com“ und „david@contoso.com“ gesendet. Julies Postfach befindet sich auf einem Exchange-Postfachserver in der lokalen Organisation. Davids Postfach befindet sich in Exchange Online.

2.  Da beide Empfänger eine "contoso.com"-E-Mail-Adresse haben und der MX-Eintrag für "contoso.com" auf die lokale Organisation verweist, wird die Nachricht an einen lokalen Exchange-Server zugestellt.

3.  Der lokale Exchange-Server sucht unter Verwendung des lokalen globalen Katalogservers nach den einzelnen Empfängern. Über die Suche im globalen Katalog ermittelt der Hub-Transport-Server, dass sich Julies Postfach auf dem lokalen Exchange-Postfachserver befindet, während sich Davids Postfach in der Exchange Online-Organisation befindet und die Hybridroutingadresse „david@contoso.mail.onmicrosoft.com“ aufweist.

4.  Der lokale Exchange-Server teilt die Nachricht in zwei Kopien auf. Eine Kopie der Nachricht wird an den lokalen Exchange-Postfachserver gesendet, wo sie an das Postfach von Julie zugestellt wird.

5.  Die zweite Kopie der Nachricht wird vom lokalen Exchange-Server mithilfe eines für die Verwendung von TLS konfigurierten Sendeconnectors an den EOP-Dienst gesendet, der die Nachrichten empfängt, die an die Exchange Online-Organisation gesendet werden.

6.  EOP sendet die Nachricht an die Exchange Online-Organisation, wo sie auf Viren geprüft und an Davids Postfach zugestellt wird.

**Weiterleiten von Nachrichten über die lokale Organisation für die lokale und die Exchange Online-Organisation**

![Zentral eingehende E-Mail, lokal](images/JJ659050.a246a1e2-7593-4d13-9426-73622a545c9a(EXCHG.150).png "Zentral eingehende E-Mail, lokal")

## Ausgehende Nachrichten ins Internet

Sie können nicht nur festlegen, wie eingehende Nachrichten weitergeleitet werden, die an Empfänger in Ihrer Organisation adressiert sind, sondern auch angeben, wie ausgehende Nachrichten weitergeleitet werden, die von Exchange Online-Empfängern gesendet wurden. Wenn Sie den Assistenten für die Hybridkonfiguration ausführen, können Sie zwischen zwei Optionen wählen:

  - **Zentralen E-Mail-Transport nicht aktivieren**   Diese Option ist im Assistenten für die Hybridkonfiguration standardmäßig ausgewählt und leitet ausgehende Nachrichten aus der Exchange Online-Organisation direkt ins Internet weiter. Verwenden Sie diese Option, wenn es nicht erforderlich ist, lokale Richtlinien zur Kompatibilität oder sonstige Verarbeitungsregeln auf Nachrichten anzuwenden, die von Empfängern in der Exchange Online-Organisation gesendet werden.

  - **Zentralen E-Mail-Transport aktivieren**   Bei Auswahl dieser Option werden ausgehende Nachrichten, die aus der Exchange Online-Organisation gesendet werden, über Ihre lokale Organisation weitergeleitet. Mit Ausnahme von Nachrichten, die an andere Empfänger in derselben Exchange Online-Organisation gesendet wurden, werden alle Nachrichten, die von Empfängern in der Exchange Online-Organisation gesendet wurden, über die lokale Organisation gesendet. Dadurch wird es Ihnen ermöglicht, Kompatibilitätsregeln auf diese Nachrichten sowie andere Prozesse oder Anforderungen anzuwenden, die auf alle Empfänger angewendet werden müssen, unabhängig davon, ob diese zur Exchange Online- oder zur lokalen Organisation gehören.
    

    > [!NOTE]
    > Der zentrale E-Mail-Transport wird nur für Organisationen empfohlen, die aufgrund der Richtlinientreue spezielle Transportanforderungen haben. Für typische Exchange-Organisationen empfiehlt es sich, den zentralen E-Mail-Transport nicht zu aktivieren.



Von lokalen Empfängern gesendete Nachrichten werden immer direkt über DNS an Empfänger im Internet gesendet, unabhängig davon, welche der oben genannten Optionen Sie im Assistenten für die Hybridkonfiguration auswählen.

Die folgenden Schritte und die Abbildung veranschaulichen den Pfad ausgehender Nachrichten für Nachrichten, die von lokalen Empfängern gesendet werden.

1.  Julie, die über ein Postfach auf dem lokalen Exchange-Postfachserver verfügt, sendet über das Internet eine Nachricht an den externen Empfänger „erin@cpandl.com“.

2.  Der Exchange-Server schlägt den MX-Eintrag für „cpandl.com“ nach und sendet die Nachricht an die „cpandl.com“-Postfachserver, die sich im Internet befinden.

**Nachrichten von lokalen Absendern an Empfänger im Internet**

![Ausgehende E-Mail von lokal](images/JJ659050.71f287d6-b814-4820-a0dc-575f17d13894(EXCHG.150).png "Ausgehende E-Mail von lokal")

Lesen Sie den folgendem Abschnitt, in dem gegenübergestellt wird, wie Sie die Weiterleitung aller von Empfängern in der Exchange Online-Organisation gesendeten Nachrichten an Empfänger im Internet planen.

## Zustellen von Internet-Nachrichten aus Exchange Online mithilfe von DNS (zentraler E-Mail-Transport deaktiviert)

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad für ausgehende Nachrichten, die von Exchange Online-Empfängern an Empfänger im Internet gesendet werden, wenn die Option **Zentralen E-Mail-Transport aktivieren** im Assistenten für die Hybridkonfiguration nicht ausgewählt ist (Standardkonfiguration).

1.  David, der über ein Postfach in der Exchange Online-Organisation verfügt, sendet über das Internet eine Nachricht an den externen Empfänger "erin@cpandl.com".

2.  Exchange Online prüft die Nachricht auf Viren und sendet sie an das EOP-Unternehmen für Exchange.

3.  EOP schlägt den MX-Eintrag für "cpandl.com" nach und sendet die Nachricht an die "cpandl.com"-Postfachserver im Internet.

**Direkte Weiterleitung von E-Mails von Exchange Online-Absendern ins Internet bei deaktiviertem zentralen E-Mail-Transport (Standardkonfiguration)**

![EXO direkt ausgehende E-Mail](images/JJ659050.fe1c4241-0d6e-47bf-b61d-5af732d2dbbc(EXCHG.150).png "EXO direkt ausgehende E-Mail")

## Weiterleiten von Nachrichten aus Exchange Online ins Internet über die lokale Organisation (zentraler E-Mail-Transport aktiviert)

Die folgende Beschreibung und Abbildung veranschaulichen den Pfad für ausgehende Nachrichten, die von Exchange Online-Empfängern an Empfänger im Internet gesendet werden, wenn die Option **Zentralen E-Mail-Transport aktivieren** im Assistenten für die Hybridkonfiguration ausgewählt wird.

1.  David, der über ein Postfach in der Exchange Online-Organisation verfügt, sendet über das Internet eine Nachricht an den externen Empfänger "erin@cpandl.com".

2.  Exchange Online prüft die Nachricht auf Viren und sendet sie an EOP.

3.  Da EOP so konfiguriert ist, dass alle ins Internet gehenden Nachrichten an einen lokalen Server gesendet werden, wird die Nachricht an einen lokalen Exchange-Server weitergeleitet. Die Nachricht wird mit TLS gesendet.

4.  Der lokale Exchange-Server führt an Davids Nachricht sämtliche Konformitäts-, Virenschutz- und sonstigen Prozesse aus, die vom Administrator konfiguriert wurden.

5.  Der lokale Exchange-Server schlägt den MX-Eintrag für „cpandl.com“ nach und sendet die Nachricht an die „cpandl.com“-Postfachserver, die sich im Internet befinden.

**Weiterleitung von E-Mails von Exchange Online-Absendern über die lokale Organisation bei aktiviertem zentralen E-Mail-Transport**

![Ausgehende EXO-Mail über lokal](images/JJ659050.7ea9ffee-944b-45ae-ba4d-c3484100399b(EXCHG.150).png "Ausgehende EXO-Mail über lokal")

