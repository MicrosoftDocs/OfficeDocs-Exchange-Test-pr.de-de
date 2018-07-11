---
title: 'DNS-Abfragefehlerempfindlichkeit: Exchange 2013 Help'
TOCTitle: DNS-Abfragefehlerempfindlichkeit
ms:assetid: a3c3980c-20ca-4b54-a2e6-76d49af620b4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb676467(v=EXCHG.150)
ms:contentKeyID: 52062888
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DNS-Abfragefehlerempfindlichkeit

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-02_

Sie können in Microsoft Exchange Server 2013 die DNS-Abfrageempfindlichkeit anpassen, um beim Erkennen von DNS-Fehlern für die Zieldomäne eine etwas schnellere Nachrichtenzustellung zu erreichen. In Abhängigkeit von den DNS-Fehlern kann diese Anpassung unter Umständen jedoch zu Zustellungsfehlern führen.

## DNS-Abfragen und Remotenachrichtenzustellung

Der für die Zustellung von Nachrichten an externe Empfänger zuständige Exchange-Server muss einen Zielnachrichtenserver finden können, der E-Mail für die externen Empfänger zulässt. Je nach Ziel werden die Nachrichten in einer oder mehreren Remotezustellungswarteschlangen abgelegt, in denen sie auf die Zustellung an die Remoteempfänger warten. Weitere Informationen über Zustellungswarteschlangen finden Sie unter [Warteschlangen](queues-exchange-2013-help.md).

Der Exchange-Server fragt die konfigurierten externen DNS-Server ab, um die DNS-Datensätze zu finden, die für die Zustellung der Nachricht erforderlich sind. Die DNS-Server werden in der Reihenfolge abgefragt, in der sie aufgelistet sind. Wenn einer der DNS-Server nicht verfügbar ist, fährt die Abfrage mit dem nächsten DNS-Server in der Liste fort. Die DNS-Server werden nach den folgenden Informationen abgefragt:

  - **MX-Datensätze (Mail Exchange) für den Domänenteil des externen Empfängers**   Der MX-Datensatz enthält den vollqualifizierten Domänennamen (FQDN) des Messagingservers, der für die Annahme der Nachrichten für die Domäne zuständig ist und einen Präferenzwert für diesen Messagingserver. Ein niedrigerer Präferenzwert gibt einen bevorzugten Messagingserver an. Der Präferenzwert ist wichtig, wenn die Domäne mehr als einen MX-Datensatz aufweist. Die meisten Organisationen verwenden mehrere Messagingserver und mehrere MX-Datensätze mit unterschiedlichen Präferenzwerten, um die Fehlertoleranz zu optimieren.

  - **A-Datensätze (Adressdatensätze) für die Zielmessagingserver**   Jeder Messagingserver, der in einem MX-Datensatz verwendet wird, sollte einen entsprechenden A-Datensatz besitzen. Der A-Datensatz wird verwendet, um die IP-Adresse des Zielmessagingservers zu finden. Der abonnierte Edge-Transport-Server verwendet die IP-Adresse, um eine SMTP-Verbindung zum Zielmessagingserver zu öffnen. Obwohl es technisch möglich ist, den vollqualifizierten Namen (FQDN) eines kanonischen Namensdatensatzes (CNAME) in einem MX-Datensatz zu verwenden, verletzt diese Vorgehensweise RFC 974, RFC 1034, RFC 1912 und RFC 2181 und wird daher von den meisten Messagingservern nicht unterstützt.
    
    Die erforderliche Kombination von iterativen und rekursiven DNS-Abfragen, die mit einem DNS-Stammserver beginnen, wird zum Auflösen des vollqualifizierten Namens (FQDN) des Messagingservers, der sich im MX-Datensatz befindet, in eine IP-Adresse verwendet.

In Exchange 2013 besteht ein nicht konfigurierbarer DNS-Abfragegrenzwert von 5 Sekunden für die einzelnen DNS-Server sowie ein Grenzwert von einer Minute für die gesamte DNS-Abfrage.

## Potenzielle DNS-Probleme

Auch wenn die externen DNS-Einstellungen auf dem Exchange-Server ordnungsgemäß konfiguriert sind, können Probleme mit den DNS-Datensätzen für eine bestimmte Domäne oder mit einem der DNS-Server auftreten, die für die Suche nach dem autoritativen DNS-Server für eine bestimmte Domäne verwendet werden. Im Allgemeinen unterliegen diese Probleme nicht Ihrer Kontrolle und müssen von den Besitzern dieser DNS-Server behoben werden. Für diese DNS-bezogenen Fehler kann es eine oder mehrere der folgenden Ursachen geben:

  - Ungültige DNS-Datensätze für die Zieldomäne

  - Probleme mit der DNS-Serverauslastung

  - Probleme mit der DNS-Serverreplikation

Wenn in Exchange 2013 eine DNS-Abfrage zu Fehlern führt, fährt die Abfrage nur dann mit dem nächsten DNS-Server fort, wenn dieser DNS-Server für die aktuelle Abfrage noch keinen Fehler zurückgegeben hat.

Sie können die Empfindlichkeit für DNS-Abfragefehler durch Ändern der XML-Anwendungskonfigurationsdatei `%ExchangeInstallPath%bin\EdgeTransport.exe.config` ändern. Diese Datei ist dem Microsoft Exchange-Transportdienst zugeordnet. Änderungen, die Sie in dieser Datei speichern, werden nach einem Neustart des Microsoft Exchange-Transportdiensts angewendet. Wenn Sie diesen Dienst neu starten, wird die Nachrichtenübermittlung auf dem Server zeitweise unterbrochen. Die Empfindlichkeit für DNS-Abfragefehler wird vom Schlüssel *DnsFaultTolerance* in der Datei "EdgeTransport.exe.config" gesteuert. Dieser Schlüssel akzeptiert die folgenden Werte:

  - **Lenient**   Wenn die DNS-Abfrage eine Kombination aus gültigen und ungültigen MX-Datensätzen erkennt, fährt die DNS-Abfrage fort, bis der Grenzwert von einer Minute für die DNS-Abfrage erreicht wird. Die ungültigen MX-Datensätze werden verworfen, und der gültige MX-Datensatz mit dem niedrigsten Präferenzwert wird zum Zustellen der Nachricht an den Zielmessagingserver verwendet. Dies ist der Standardwert.

  - **Normal**   Wenn die DNS-Abfrage zuerst einen ungültigen MX-Datensatz erkennt, werden alle aufgelösten MX-Datensätze, deren Präferenzwert größer als oder gleich den ungültigen MX-Datensätzen ist, sofort verworfen. Der verbleibende MX-Datensatz mit dem niedrigsten Präferenzwert wird zum Zustellen der Nachricht an den Zielmessagingserver verwendet, ohne auf den Zeitablauf für die gesamte DNS-Abfrage zu warten. Obwohl dieses Verhalten zu einer schnelleren Nachrichtenübermittlung führen kann, ist ein potenzieller Nachteil dieses Verhaltens, dass die DNS-Abfrage möglicherweise keine gültigen MX-Datensätze besitzt, wenn die folgenden Bedingungen zutreffen:
    
      - Der ungültige MX-Datensatz ist der erste MX-Datensatz für die Zieldomäne.
    
      - Die gültigen MX-Datensätze besitzen denselben Präferenzwert wie die ungültigen MX-Datensätze.

Sowohl im Modus `Normal` als auch im Modus `Lenient` werden die Ergebnisse der DNS-Abfrage für einen ungültigen MX-Datensatz niemals zwischengespeichert. Bei der nächsten Ausführung einer DNS-Abfrage versucht diese die MX-Datensätze für die Zieldomäne aufzulösen.


> [!NOTE]
> Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z.&nbsp;B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.


