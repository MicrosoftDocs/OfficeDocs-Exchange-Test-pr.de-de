---
title: 'Absenderzuverlässigkeit und der Protokollanalyse-Agent: Exchange 2013 Help'
TOCTitle: Absenderzuverlässigkeit und der Protokollanalyse-Agent
ms:assetid: c4c34235-d545-41e7-ac2f-1dd43aaa3708
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124512(v=EXCHG.150)
ms:contentKeyID: 50476689
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Absenderzuverlässigkeit und der Protokollanalyse-Agent

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

Die Absenderzuverlässigkeit ist Teil der Exchange-Antispamfunktion, die Nachrichten anhand zahlreicher Eigenschaften des Absenders blockiert. Die Absenderzuverlässigkeit verwendet gespeicherte Daten über den Absender, um die Aktion zu bestimmen, die ggf. für eine eingehende Nachricht ausgeführt werden soll. Der Protokollanalyse-Agent ist der zugrunde liegende Agent für die Funktion der Absenderzuverlässigkeit.

Beim Konfigurieren von Antispam-Agents auf einem Exchange-Server bearbeitet der Agent Nachrichten kumulativ, um die Anzahl der unerwünschten Nachrichten zu verringern, die in die Organisation gelangen.

**Inhalt**

Calculation of the sender reputation level

Use of the SRL

Enabling and configuring the detection of open proxy servers

Setting the SRL block threshold

## Berechnung des Absenderzuverlässigkeitsgrads

Aus folgender Statistik wird ein Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) berechnet:

  - **HELO/EHLO-Analyse**   Zweck der SMTP-Befehle HELO und EHLO ist es, dem empfangenden SMTP-Server den Domänennamen, beispielsweise Contoso.com, oder die IP-Adresse des sendenden SMTP-Servers bereitzustellen. Böswillige Benutzer und *Spammer* fälschen die HELO/EHLO-Anweisung häufig auf verschieden Arten. Beispielsweise geben sie eine IP-Adresse ein, die nicht der IP-Adresse entspricht, über welche die Verbindung tatsächlich hergestellt wurde. Spammer fügen auch Domänen in die HELO-Anweisung ein, von denen bekannt ist, dass sie von dem empfangenden Server lokal unterstützt werden, in dem Versuch der Vortäuschung, dass sich die Domänen innerhalb der Organisation befinden. In anderen Fällen ändern Spammer die Domäne, die in der HELO-Anweisung übergeben wird. Rechtmäßige Benutzer mögen zwar auch verschiedene Sätze von Domänen in ihren HELO-Anweisungen verwenden, doch sind diese normalerweise relativ konstant.
    
    Daher kann die Analyse der HELO/EHLO-Anweisung auf Absenderbasis darauf hinweisen, dass es sich bei dem Absender wahrscheinlich um einen Spammer handelt. Ein Absender, der beispielsweise innerhalb eines bestimmten Zeitraums viele verschiedene, aber eindeutige HELO/EHLO-Anweisungen bereitstellt, ist mit höherer Wahrscheinlichkeit ein Spammer. Absender, die kontinuierlich eine IP-Adresse in der HELO-Anweisung übermitteln, die nicht der IP-Absenderadresse wie vom Verbindungsfilter-Agent ermittelt entsprechen, sind ebenfalls mit höherer Wahrscheinlichkeit Spammer. Remoteabsender, die kontinuierlich einen lokalen Domänennamen in der HELO-Anweisung übermitteln, der sich in der gleichen Organisation wie der Exchange-Server befindet, sind ebenfalls mit höherer Wahrscheinlichkeit Spammer.

  - **Reverse-DNS-Lookup**   Die Absenderzuverlässigkeit überprüft auch, ob die Ursprungs-IP-Adresse, von der der Absender die Nachricht übermittelt hat, dem registrierten Domänennamen entspricht, der vom Absender mit dem SMTP-Befehl HELO oder EHLO übermittelt wird.
    
    Die Absenderzuverlässigkeit führt eine Reverse-DNS-Abfrage aus, indem die Ursprungs-IP-Adresse an DNS übermittelt wird. Das von DNS zurückgegebene Ergebnis ist der Domänenname, der für diese IP-Adresse von der zuständigen Stelle für die Vergabe von Domänennamen registriert wurde. Die Absenderzuverlässigkeit vergleicht den von DNS zurückgegebenen Domänennamen mit dem Domänennamen, der vom Absender mit dem SMTP-Befehl HELO/EHLO übermittelt wurde. Wenn sich die Domänennamen nicht entsprechen, ist der Absender wahrscheinlich ein Spammer, und der Wert der SRL-Gesamtbewertung für diesen Absender wird erhöht.
    
    Der Sender ID-Agent führt einen ähnlichen Task aus, aber sein Erfolg hängt von rechtmäßigen Absendern ab, die ihre DNS-Infrastruktur aktualisieren, um alle E-Mail sendenden SMTP-Server in deren Organisation zu identifizieren. Mit einem Reverse-DNS-Lookup können Sie bei der Identifizierung potenzieller Spammer helfen.

  - **Analyse von SCL-Bewertungen für Nachrichten eines bestimmten Absenders**   Wenn der Inhaltsfilter-Agent eine Nachricht verarbeitet, weist er dieser eine SCL-Bewertung (Spam Confidence Level) zu. Die SCL-Bewertung ist eine Zahl von 0 bis 9. Eine höhere SCL-Bewertung zeigt an, dass es sich bei einer Nachricht mit größerer Wahrscheinlichkeit um Spam handelt. Die Daten über jeden Absender und die SCL-Bewertungen ihrer Nachrichten sind beständig verfügbar für die Analyse durch die Absenderzuverlässigkeit. Die Absenderzuverlässigkeit berechnet die Statistik für einen Absender aus dem Verhältnis aller Nachrichten dieses Absenders mit einer niedrigen SCL-Bewertung in der Vergangenheit und allen Nachrichten dieses Absenders mit einer hohen SCL-Bewertung in der Vergangenheit. Zusätzlich fließt die Anzahl der Nachrichten mit einer hohen SCL-Bewertung, die der Absender innerhalb des letzten Tags versendet hat, in die SRL-Gesamtbewertung ein.

  - **Open Proxy-Test für Absender**   Ein *offener Proxy* ist ein Proxyserver, der ortsunabhängig alle Verbindungsanforderungen akzeptiert und den Datenverkehr so weiterleitet, als ob er von den lokalen Hosts stammte. Proxyserver leiten TCP-Verkehr durch Firewallhosts weiter, um Benutzeranwendungen einen transparenten Zugriff hinter die Firewall zu gestatten. Da Proxyprotokolle schlank und von Benutzeranwendungsprotokollen unabhängig sind, können Proxys von vielen verschiedenen Diensten verwendet werden. Proxys können auch zur gemeinsamen Nutzung einer Internetverbindung durch mehrere Hosts verwendet werden. Proxys werden normalerweise so eingerichtet, dass nur vertrauenswürdige Hosts innerhalb der Firewall den jeweiligen Proxy passieren dürfen. Ein rechtmäßiger Absender kann aufgrund einer unabsichtlichen Fehlkonfiguration oder aufgrund von Schadsoftware auch ein offener Proxy sein.
    
    Offene Proxys bieten böswilligen Benutzern eine ideale Möglichkeit, um ihre wahre Identität zu verbergen sowie um DoS-Angriffe (Denial of Service) zu starten oder um Spam zu senden. Da Proxyserver zunehmend als standardmäßig offen konfiguriert werden, treten offene Proxys immer häufiger auf. Darüber hinaus können böswillige Benutzer mehrere offene Proxys verwenden, um die Ursprungs-IP-Adresse des Absenders zu verschleiern.
    
    Wenn die Absenderzuverlässigkeit einen Open Proxy-Test durchführt, wird eine SMTP-Anforderung formatiert, um von dem offenen Proxyserver aus eine Verbindung zurück zum Exchange-Server herzustellen. Wenn eine SMTP-Anforderung von dem Proxyserver empfangen wird, überprüft die Absenderzuverlässigkeit, ob es sich bei dem Proxyserver um einen offenen Proxy handelt, und aktualisiert die Open Proxy-Teststatistik dieses Absenders entsprechend.

Die Absenderzuverlässigkeit wägt die jede einzelne Statistik ab und berechnet einen Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) für jeden Absender. Der Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) ist eine Zahl zwischen 0 und 9 zur Vorhersage der Wahrscheinlichkeit, dass ein bestimmter Absender ein Versender von Spam oder in anderer Weise böswilliger Benutzer ist. Ein Wert von 0 gibt an, dass es sich bei dem Absender wahrscheinlich nicht um einen Spammer handelt; ein Wert von 9 gibt an, dass es sich bei dem Absender wahrscheinlich um einen Spammer handelt.

Sie können einen Sperrschwellenwert zwischen 0 und 9 konfigurieren, ab dem die Absenderzuverlässigkeit eine Anforderung an den Absenderfilter-Agent ausgibt, wodurch der Absender am Senden einer Nachricht in die Organisation gehindert wird. Wenn ein Absender geblockt wird, wird er der Liste der geblockten Absender für einen konfigurierbaren Zeitraum hinzugefügt. Die Art der Verarbeitung von geblockten Nachrichten hängt von der Konfiguration des Absenderfilter-Agents ab. Folgende Aktionen stehen für die Verarbeitung geblockter Nachrichten zur Wahl:

  - Ablehnen

  - Löschen und archivieren

  - Akzeptieren und als geblockten Absender kennzeichnen

Wenn ein Absender in die IP-Sperrliste oder den IP-Zuverlässigkeitsdienst von Microsoft aufgenommen wurde, gibt die Absenderzuverlässigkeit eine sofortige Anforderung an den Absenderfilter-Agent aus, um den Absender zu blockieren. Um von dieser Funktionalität profitieren zu können, müssen Sie die automatischen Antispamupdates von Microsoft Exchange aktivieren und konfigurieren.

Für Absender, die nicht analysiert wurden, legt die Absenderzuverlässigkeit standardmäßig eine Bewertung von 0 fest. Nachdem ein Absender mindestens 20 Nachrichten gesendet hat, berechnet die Absenderzuverlässigkeit auf Grundlage der zuvor in diesem Thema beschriebenen Statistik eine SRL-Bewertung.‏

Zurück zum Seitenanfang

## Verwenden eines Absenderzuverlässigkeitsgrads (Sender Reputation Level, SRL)

Die Absenderzuverlässigkeit führt in zwei Phasen der SMTP-Sitzung Aktionen für Nachrichten aus:

  - **SMTP-Befehl "MAIL FROM"**   Die Absenderzuverlässigkeit führt nur dann Aktionen für eine Nachricht aus, wenn diese vom Verbindungsfilter-Agent, vom Absenderfilter-Agent, vom Empfängerfilter-Agent oder vom Sender ID-Agent blockiert oder anderweitig verarbeitet wurde. In diesem Fall ruft die Absenderzuverlässigkeit die aktuelle SRL-Bewertung des Absenders aus dessen Absenderprofil ab, das auf dem Exchange-Server gespeichert wird. Nach dem Abrufen und Auswerten dieser Bewertung gibt die Konfiguration des Exchange-Servers das Verhalten vor, das aufgrund des Sperrschwellenwerts bei der jeweiligen Verbindung auftritt.

  - **Nach dem SMTP-Befehl "end of data"**   Der SMTP-Befehl "end of data" (**EOD**) wird ausgeführt, nachdem alle tatsächlichen Nachrichtendaten gesendet wurden. Zu diesem Zeitpunkt der SMTP-Sitzung wurde die Nachricht bereits von zahlreichen Antispam-Agents verarbeitet. Als Begleiteffekt der Antispamverarbeitung wird die Statistik, die Absenderzuverlässigkeit benötigt, aktualisiert. Deshalb verfügt die Absenderzuverlässigkeit über die Daten, die zum Berechnen oder Neuberechnen einer SRL-Bewertung für den Absender notwendig sind.

Weitere Informationen finden Sie unter [Verwalten der Absenderzuverlässigkeit](manage-sender-reputation-exchange-2013-help.md).

Zurück zum Seitenanfang

## Aktivieren und Konfigurieren der Erkennung von offenen Proxyservern

Die Absenderzuverlässigkeit wertet zur Berechnung der SRL-Bewertung mehrere Absendermerkmale aus. Zu den Eigenschaften, die die Absenderzuverlässigkeit auswertet, zählen die Ergebnisse eines Tests auf offene Proxyserver. Häufig leiten Versender von Spam Nachrichten über offene Proxyserver im Internet. Durch das Weiterleiten von Spam über offene Proxyserver können Versender von Spam Nachrichten senden, die von einem anderen als ihrem eigenen Server zu stammen scheinen.

Wenn die Absenderzuverlässigkeit einen SRL-Wert berechnet, versucht sie, mithilfe einer Vielzahl gängiger Proxyprotokolle, wie etwa SOCKS4, SOCKS5, HTTP, Telnet, Cisco oder Wingate, eine Verbindung mit der Absender-IP-Adresse herzustellen. Die Absenderzuverlässigkeit formatiert eine protokollspezifische Anforderung, um über den offenen Proxyserver mithilfe einer SMTP-Anforderung eine Verbindung mit dem Edge-Transport-Server herzustellen. Wenn eine SMTP-Anforderung von dem Proxyserver empfangen wird, überprüft die Absenderzuverlässigkeit, ob es sich bei dem Proxyserver um einen offenen Proxyserver handelt, und passt die SRL-Bewertung diesem Ergebnis entsprechend an. Die Erkennung offener Proxyserver ist für die Absenderzuverlässigkeit standardmäßig aktiviert.

Weitere Informationen zum Aktivieren und Konfigurieren der Erkennung von offenen Proxyservern finden Sie unter [Verwalten der Absenderzuverlässigkeit](manage-sender-reputation-exchange-2013-help.md).

Zurück zum Seitenanfang

## Festlegen des SRL-Sperrschwellenwerts

Der Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) ist eine Zahl zwischen 0 und 9 zur Vorhersage der Wahrscheinlichkeit, dass ein bestimmter Absender ein Versender von Spam oder in anderer Weise böswilliger Benutzer ist. Sie müssen einen Schwellenwert für die Absendersperrung durch SRL festlegen. Dieser SRL-Sperrschwellenwert definiert den SRL-Wert, der überschritten werden muss, damit die Absenderzuverlässigkeit einen Absender blockiert. Standardmäßig ist der SRL-Wert auf 7 festgelegt. Sie sollten die Wirksamkeit des Agents bei Verwendung der Standardeinstellung überwachen. Es kann möglich sein, dass der SRL-Wert angepasst werden muss, um die Anforderungen Ihrer Organisation zu erfüllen. Wenn Sie andere Antispam-Agents auf aggressive Werte festlegen, können Sie möglicherweise einen höheren SRL-Schwellenwert für die Absenderzuverlässigkeit festlegen als bei weniger aggressiven Werten für die anderen Antispam-Agents. Weitere Informationen zum Anpassen von Antispamkonfigurationen für ein effektives Zusammenwirken, um Spam zu verringern, finden Sie unter [Antispamschutz](anti-spam-protection-exchange-2013-help.md).

Wenn der SRL-Sperrschwellenwert für einen bestimmten Absender überschritten wird, fügt die Absenderzuverlässigkeit den Absender auf dem Edge-Transport-Server der IP-Sperrliste im Verbindungsfilter-Agent hinzu. Manchmal senden Versender von Spam Batches von Spamnachrichten über einen einzelnen Absender. In diesem Szenario wird der Absender für einen konfigurierbaren Zeitraum zur Absendersperrliste hinzugefügt, wenn die Absenderzuverlässigkeit einen SRL-Wert berechnet, der den SRL-Sperrschwellenwert überschreitet. Die standardmäßige Dauer ist 24 Stunden. Nach 24 Stunden wird der Absender aus der Absendersperrliste entfernt und kann erneut Nachrichten senden.

Wenn ein Absender zur IP-Sperrliste hinzugefügt wird, löscht die Absenderzuverlässigkeit das Profil für den Absender. Die Absenderzuverlässigkeit löscht das vorhandene Profil des blockierten Absenders, da dieses angibt, dass der SRL-Wert des Absenders den SRL-Sperrschwellenwert überschreitet. Dies würde dazu führen, dass der blockierte Absender erneut zur IP-Sperrliste hinzugefügt würde, sobald der Sperrzeitraum für den Absender abgelaufen wäre.

Weitere Informationen finden Sie unter [Verwalten der Absenderzuverlässigkeit](manage-sender-reputation-exchange-2013-help.md).

Zurück zum Seitenanfang

