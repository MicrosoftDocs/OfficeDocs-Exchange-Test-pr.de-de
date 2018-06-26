---
title: 'Vorteile der Antispamfunktionen in Exchange Online Protection im Vergleich zu Exchange Server 2013: Exchange 2013 Help'
TOCTitle: Vorteile der Antispamfunktionen in Exchange Online Protection im Vergleich zu Exchange Server 2013
ms:assetid: 00e37a3c-3fbc-488f-bdad-d52a3c80fd72
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673032(v=EXCHG.150)
ms:contentKeyID: 50474928
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Vorteile der Antispamfunktionen in Exchange Online Protection im Vergleich zu Exchange Server 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-05-26_

Im Folgenden sind die Vorteile bei Verwendung des Exchange-Antispamschutzes in der Cloud (Microsoft Exchange Online oder Microsoft Exchange Online Protection) im Vergleich zu Microsoft Exchange Server 2013 aufgeführt. Microsoft Exchange Server 2013 verfügt über dieselben integrierten Antispamfunktionen wie Exchange Server 2010:

  - **Mehr Kontrolle und einfachere Konfiguration**   Administratoren können das webbasierte Exchange-Verwaltungskonsole (EAC) nutzen, um die Spamfiltereinstellungen gemäß den Anforderungen Ihrer Organisation anzupassen.Exchange Server 2013 verfügt nicht über eine Antispambenutzeroberfläche. Exchange Online verfügt über integrierte EOP-Antispamfunktionen

  - **Verbesserte Verbindungsfilterung**    In Exchange 2013 stehen die Listen zugelassener und blockierter IP-Adressen für die Verbindungsfilterung nur dann zur Verfügung, wenn Sie in Ihrem Umkreisnetzwerk einen Edge-Transport-Server installieren. Weitere Informationen finden Sie unter [Edge-Transport-Server](edge-transport-servers-exchange-2013-help.md). In der Cloud können Sie die Spamfilterung für von vertrauenswürdigen Absendern gesendete E-Mail-Nachrichten (aus verschiedenen Drittanbieterquellen zusammengestellt) überspringen und somit sicherstellen, dass diese Nachrichten nicht versehentlich als Spam markiert werden. Darüber hinaus verwendet der gehostete Filterdienst die Liste blockierter IP-Adressen von Microsoft sowie Listen anderer Anbieter, um eine verbesserte Filterung auf IP-Ebene zu ermöglichen.

  - **Verbesserte Inhaltsfilterung**   Sie können Ihre Inhaltsfilterrichtlinie problemlos für Folgendes konfigurieren:
    
      - Filtern von Nachrichten, die in bestimmten Sprachen verfasst wurden.
    
      - Filtern von Nachrichten aus bestimmten Ländern oder Regionen.
    
      - Markieren von Massen-E-Mails (z. B. Werbung und Marketing-E-Mails) als Spam.
    
      - Suchen nach Attributen in Nachrichten und Ergreifen von Maßnahmen, wenn die Nachricht einem bestimmten erweiterten Attribut für Spamoptionen entspricht. Wenn Sie sich Sorgen wegen Phishing machen, bieten einige dieser Optionen eine Kombination aus Sender ID- und SPF-Technologien, um eine Authentifizierung durchzuführen und sicherzustellen, dass Nachrichten nicht gefälscht wurden.
    
    Neben den obigen Inhaltsfilteroptionen, die in der Exchange-Verwaltungskonsole konfiguriert werden können, verwendet der gehostete Filterdienst zusätzliche URL-Listen, um verdächtige Nachrichten mit spezifischen URLs im Nachrichtentext zu blockieren.

  - **Schnellere Updates**   Spamupdates werden schneller innerhalb des Netzwerks verbreitet. In Exchange Server 2013 werden Updates zweimal pro Monat durchgeführt, der Dienst selbst wird jedoch mehrmals pro Stunde aktualisiert.

  - **Filterung für ausgehende E-Mails**  Die Filterung ausgehender Spamnachrichten ist immer aktiviert, wenn Sie den gehosteten Dienst für das Senden ausgehender E-Mails verwenden und dadurch Organisationen, die den Dienst nutzen, und ihre jeweiligen Empfänger schützen.

