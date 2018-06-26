---
title: 'Antispamschutz: Exchange 2013 Help'
TOCTitle: Antispamschutz
ms:assetid: 6af88a08-687d-40b1-8b22-80704184403d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218660(v=EXCHG.150)
ms:contentKeyID: 50475924
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Antispamschutz

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-06_

*Spammer* oder böswillige Absender verwenden eine Vielzahl von Techniken, um ungewünschte E-Mails an Ihre Organisation zu senden. Kein einzelnes Tool und kein einzelner Vorgang kann Spam vollständig beseitigen. Daher bietet Microsoft Exchange Server 2013 einen mehrschichtigen, diversifizierten und facettenreichen Ansatz zur Verringerung dieser unerwünschten Nachrichten. Exchange verwendet Transport-Agents, um Antispamschutz bereitzustellen, und die integrierten Agents in Exchange 2013 wurden weitgehend unverändert aus Microsoft Exchange Server 2010 übernommen.

Wenn Sie Microsoft Exchange Online Protection (EOP) erwerben, stehen Ihnen weitere Antispamfunktionen und eine einfachere Verwaltung zur Verfügung. Einen Vergleich zwischen EOP und Exchange 2013-Eigenschaften finden Sie unter [Vorteile der Antispamfunktionen in Exchange Online Protection im Vergleich zu Exchange Server 2013](benefits-of-anti-spam-features-in-exchange-online-protection-over-exchange-server-2013-exchange-2013-help.md). Weitere Informationen über den Antispamschutz von Office 365 finden Sie im Thema über den [Office 365-E-Mail-Antispamschutz](https://support.office.com/de-de/article/office-365-email-anti-spam-protection-6a601501-a6a8-4559-b2e7-56b59c96a586?ui=en-us%26rs=en-us%26ad=us).

Weitere Informationen zu den integrierten Antischadsoftwarefunktionen in Exchange 2013 finden Sie unter [Antischadsoftwareschutz](anti-malware-protection-exchange-2013-help.md).

**Inhalt**

Antispam-Agents auf Postfachservern

Antispam-Agents auf Edge-Transport-Servern

Antispamstempel

Strategie für ein Antispamkonzept

## Antispam-Agents auf Postfachservern

Typischerweise werden Antispam-Agents auf einem Postfachserver nur dann aktiviert, wenn Ihre Exchange-Organisation nicht über einen Edge-Transport-Server verfügt oder eingehende Nachrichten nicht im Vorfeld nach Spam filtert. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

Wie allen Transport-Agents ist jedem Antispam-Agent ein Prioritätswert zugewiesen. Je niedriger der Wert ist, desto höher ist die Priorität: ein Antispam-Agent mit Priorität 1 wird also vor einem Agent mit Priorität 9 eine Aktion für eine Nachricht ausführen. Das SMTP-Ereignis, für das der Antispam-Agent registriert ist, spielt jedoch auch eine große Rolle, um die Reihenfolge zu bestimmen, in der Antispam-Agents Aktionen für Nachrichten ausführen. Ein Antispam-Agent mit niedriger Priorität, der für ein früher in der Transportpipeline eintretendes SMTP-Ereignis registriert ist, führt eine Aktion für eine Nachricht aus, bevor ein Antispam-Agent mit hoher Priorität, der für ein später in der Transportpipeline eintretendes SMTP-Ereignis registriert ist, eine Aktion ausführen kann.

Basierend auf dem Standardprioritätswert des Antispam-Agents und dem SMTP-Ereignis in der Transportpipeline, für das der Antispam-Agent registriert ist, beschreibt die folgende Liste die Agents und die Standardreihenfolge, in der sie auf Nachrichten auf einem Postfachserver angewendet werden:

1.  **Absenderfilter-Agent**   Die Absenderfilterung vergleicht den Absender im SMTP-Befehl MAIL FROM: mit einer vom Administrator definierten Liste der Absender oder Absenderdomänen, die keine Nachrichten an die Organisation senden dürfen, um die Aktion zu bestimmen, die ggf. für die eingehende Nachricht ausgeführt werden soll. Weitere Informationen finden Sie unter [Absenderfilterung](sender-filtering-exchange-2013-help.md).

2.  **Sender ID-Agent**   Sender ID verwendet die IP-Adresse des sendenden Servers und die PRA (Purported Responsible Address) des Absenders zum Bestimmen, ob der Absender ggf. gefälscht ist. Weitere Informationen finden Sie unter [Absender-ID](sender-id-exchange-2013-help.md).

3.  **Inhaltsfilter-Agent** Die Inhaltsfilterung bewertet den Inhalt einer Nachricht. Weitere Informationen finden Sie unter [Inhaltsfilterung](content-filtering-exchange-2013-help.md).
    
    Das Spam-Quarantänepostfach ist eine Funktion des Inhaltsfilter-Agents, die das Risiko verringert, legitime Nachrichten zu verlieren, die fälschlicherweise als Spam klassifiziert wurden. Die Spamquarantäne stellt einen temporären Speicherort für Nachrichten bereit, die als Spam erkannt wurden und nicht an ein Benutzerpostfach in der Organisation gesendet werden sollen. Weitere Informationen finden Sie unter [Quarantänepostfach für Spam](spam-quarantine-exchange-2013-help.md).
    
    Die Inhaltsfilterung arbeitet auch mit der Funktion "Aggregation von Listen sicherer Adressen" zusammen. Die Aggregation von Listen sicherer Adressen erfasst Daten aus den sicheren Listen zur Abwehr von Spam, die Microsoft Outlook- und Outlook Web App-Benutzer konfigurieren, und stellt diese Daten dem Inhaltsfilter-Agent zur Verfügung. Weitere Informationen finden Sie unter [Aggregation von Listen sicherer Adressen](safelist-aggregation-exchange-2013-help.md).

4.  **Protokollanalyse-Agent**   Der Protokollanalyse-Agent ist der zugrunde liegende Agent, der die Absenderzuverlässigkeitsfunktion implementiert. Die Absenderzuverlässigkeit stützt sich auf bestehende Daten zur IP-Adresse des sendenden Servers, um die Aktion zu bestimmen, die ggf. für eine eingehende Nachricht ausgeführt werden soll. Ein Absenderzuverlässigkeitsgrad wird für mehrere Absendermerkmale berechnet, die aus der Nachrichtenanalyse und externen Tests abgeleitet werden. Weitere Informationen finden Sie unter [Absenderzuverlässigkeit und der Protokollanalyse-Agent](sender-reputation-and-the-protocol-analysis-agent-exchange-2013-help.md).

Zurück zum Seitenanfang

## Antispam-Agents auf Edge-Transport-Servern

Wenn in Ihrer Organisation ein Edge-Transport-Server im Umkreisnetzwerk installiert ist, werden alle Antispam-Agents, die auf einem Postfachserver verfügbar sind, standardmäßig auf dem Edge-Transport-Server installiert und aktiviert. Folgende Antispam-Agents sind jedoch nur auf einem Edge-Transport-Server verfügbar:

  - **Verbindungsfilter-Agent**   Die Verbindungsfilterung untersucht die IP-Adresse des Remoteservers, der Nachrichten zu senden versucht, um die Aktion zu bestimmen, die ggf. für eine eingehende Nachricht ausgeführt werden soll. Die Verbindungsfilterung verwendet eine Liste blockierter IP-Adressen, Liste zugelassener IP-Adressen, einen Anbieterdienst für blockierte IP-Adressen und einen Anbieterdienst für zugelassene IP-Adressen, um zu bestimmen, ob die Verbindungs-IP geblockt oder zugelassen werden sollte. Weitere Informationen finden Sie unter [Verbindungsfilterung auf Edge-Transport-Servern](connection-filtering-on-edge-transport-servers-exchange-2013-help.md).

  - **Empfängerfilter-Agent**   Die Empfängerfilterung vergleicht die Nachrichtenempfänger im SMTP-Befehl RCPT TO: mit einer vom Administrator definierten Empfängersperrliste. Wird dabei eine Übereinstimmung gefunden, darf die Nachricht nicht in die Organisation gelangen. Der Empfängerfilter vergleicht außerdem Empfänger in eingehenden Nachrichten mit dem lokalen Empfängerverzeichnis um zu bestimmen, ob die Nachricht an gültige Empfänger adressiert ist. Wenn eine Nachricht nicht an gültige Empfänger gerichtet ist, wird sie zurückgewiesen. Weitere Informationen finden Sie unter [Empfängerfilter auf Edge-Transport-Servern](recipient-filtering-on-edge-transport-servers-exchange-2013-help.md).
    

    > [!NOTE]
    > Obwohl der Empfängerfilter-Agent auf Postfachservern verfügbar ist, sollten Sie ihn nicht konfigurieren. Wenn ein Empfängerfilter auf einem Postfachserver einen ungültigen oder gesperrten Empfänger in einer Nachricht entdeckt, die andere gültige Empfänger enthält, wird die Nachricht zurückgewiesen. Wenn Sie die Anti-Spam-Agents auf einem Postfachserver installieren, wird der Empfängerfilter-Agent standardmäßig aktiviert. Er wird aber nicht zum Sperren von Empfängern konfiguriert.



  - **Anlagenfilter-Agent**   Die Anlagenfilterung blockiert Nachrichten auf Grundlage des Dateinamens der Anlage, der Dateinamenerweiterung oder des MIME-Inhaltstyps der Datei. Sie können die Anlagenfilterung so konfigurieren, dass Nachrichten und ihre Anlagen blockiert werden, die Anlage entfernt und die Nachricht zugestellt oder die Nachricht samt Anlage ohne Benachrichtigung gelöscht wird. Weitere Informationen finden Sie unter [Anlagenfilterung auf Edge-Transport-Servern](attachment-filtering-on-edge-transport-servers-exchange-2013-help.md).

Basierend auf dem Standardprioritätswert des Antispam-Agents und dem SMTP-Ereignis in der Transportpipeline, für das der Antispam-Agent registriert ist, werden die Antispam-Agents auf einem Edge-Transport-Server standardmäßig in dieser Reihenfolge angewendet:

1.  Verbindungsfilter-Agent

2.  Absenderfilter-Agent

3.  Empfängerfilter-Agent

4.  Sender ID-Agent

5.  Inhaltsfilter-Agent

6.  Protokollanalyse-Agent für die Absenderzuverlässigkeit

7.  Anlagenfilter-Agent

Zurück zum Seitenanfang

## Antispamstempel

Antispamstempel helfen Ihnen bei der Diagnose spambezogener Probleme, indem Diagnosemetadaten oder Stempel (z. B. absenderspezifische Informationen, Ergebnisse der Poststempelüberprüfung und Ergebnisse der Inhaltsfilterung) auf Nachrichten angewendet werden, während sie die Antispamfunktionen passieren, die aus dem Internet eingehende Nachrichten filtern. Weitere Informationen finden Sie unter [Antispamstempel](anti-spam-stamps-exchange-2013-help.md).

Zurück zum Seitenanfang

## Strategie für ein Antispamkonzept

Ihre Strategie für das Konfigurieren der Antispamfunktionen und das Einrichten des Aggressivitätsgrads der Einstellungen für den Antispam-Agent erfordern sorgfältige Planung und Berechnung. Wenn Sie alle Antispamfilter auf die aggressivste Stufe festlegen und alle Antispamfunktionen so konfigurieren, dass alle verdächtigen Nachrichten abgelehnt werden, wird die Wahrscheinlichkeit erhöht, dass auch Nachrichten abgelehnt werden, die kein Spam sind. Andererseits tritt möglicherweise keine Verringerung des Spamvolumens ein, das in Ihre Organisation gelangt, wenn Sie die Antispamfunktionen nicht ausreichend aggressiv und den SCL-Schwellenwert (Spam Confidence Level) zu hoch festlegen.

Es ist eine bewährte Methode, eine Nachricht abzulehnen, wenn Exchange über den Verbindungsfilter-Agent, den Empfängerfilter-Agent oder den Absenderfilter-Agent diese als verdächtige Nachricht erkennt. Dieser Ansatz ist besser als das Isolieren solcher Nachrichten oder das Zuweisen von Metadaten, wie zum Beispiel Antispamstempel, zu solchen Nachrichten. Der Verbindungsfilter-Agent und der Empfängerfilter-Agent blockieren automatisch Nachrichten, die vom jeweiligen Filter identifiziert werden. Der Absenderfilter-Agent kann konfiguriert werden.

Diese bewährte Methode wird empfohlen, da die zugrunde liegende SCL-Bewertung im Verbindungsfilter, Empfängerfilter oder Absenderfilter relativ hoch ist. Wenn der Administrator bestimmte Absender konfiguriert hat, die immer blockiert werden, besteht bei der Absenderfilterung kein Grund, die Absenderfilterdaten solchen Nachrichten zuzuweisen und mit ihrer Verarbeitung fortzufahren. In den meisten Organisationen sollten blockierte Nachrichten abgelehnt werden. (Sie hätten die Absender nicht in die Liste blockierter Absender aufgenommen, wenn deren Nachrichten nicht abgelehnt werden sollten.)

Die gleiche Logik gilt für Echtzeit-Sperrlistendienste und Absenderfilter, obwohl der zugrunde liegende Vertrauensgrad nicht so hoch wie bei der IP-Sperrliste ist. Sie sollten beachten, dass im weiteren Verlauf der Nachrichtenübermittlung die Wahrscheinlichkeit für falsch positive Befunde steigt, weil die Antispamfunktionen eine größere Anzahl von Variablen auswerten. Sie werden ggf. feststellen, dass Sie durch aggressiveres Konfigurieren der ersten Antispamfunktionen in der Antispamkette das Spamvolumen verringern. Dadurch sparen Sie Verarbeitungs-, Bandbreiten- und Datenträgerressourcen, sodass eine höhere Anzahl von verdächtigen Nachrichten untersucht werden kann.

Schließlich müssen Sie die Überwachung der Gesamteffektivität der Antispamfunktionen planen. Mit sorgfältiger Überwachung können Sie die Antispamfunktionen fortlaufend anpassen, damit sie für Ihre Umgebung gut zusammen arbeiten. Bei diesem Ansatz sollten Sie zu Beginn nur eine weitgehend nicht aggressive Konfiguration der Antispamfunktionen vorsehen. Durch diese Vorgehensweise können Sie die Anzahl falsch positiver Befunde so gering wie möglich halten. Während Sie die Antispamfunktionen überwachen und anpassen, können Sie aggressiver gegen die Art von Spam und die Spamangriffe vorgehen, der bzw. denen Ihre Organisation ausgesetzt ist.

Zurück zum Seitenanfang

## Siehe auch


[Office 365 Email Anti-Spam Protection](https://support.office.com/de-de/article/office-365-email-anti-spam-protection-6a601501-a6a8-4559-b2e7-56b59c96a586?ui=en-us%26rs=en-us%26ad=us)

