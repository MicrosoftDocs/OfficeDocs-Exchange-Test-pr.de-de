---
title: 'Empfängerfilter auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Empfängerfilter auf Edge-Transport-Servern
ms:assetid: 994eefd9-3903-41e6-a882-1e333d6d2d18
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123891(v=EXCHG.150)
ms:contentKeyID: 50476302
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Empfängerfilter auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-05-07_

Die Empfängerfilterung ist eine Antispamfunktion in Microsoft Exchange Server 2013, die den RCPT TO SMTP-Header verwendet, um zu bestimmen, welche Aktion ggf.auf eine eingehende Nachricht angewendet werden soll. Die Empfängerfilterung wird vom Empfängerfilter-Agent ausgeführt.

Der Empfängerfilter-Agent blockt Nachrichten entsprechend den Eigenschaften des beabsichtigten Empfängers in der Organisation. Der Empfängerfilter-Agent kann Ihnen dabei helfen, in folgenden Szenarios die Annahme von Nachrichten zu verhindern:

  - **Nicht vorhandene Empfänger**   Sie können die Zustellung an Empfänger verhindern, die nicht im Adressbuch der Organisation vorhanden sind. Möglicherweise möchten Sie die Zustellung an häufig missbrauchte Kontonamen wie **administrator&#64;contoso.com** oder **support&#64;contoso.com** unterbinden.

  - **Eingeschränkte Verteilerlisten**   Sie können die Zustellung von Internet Mail an Verteilerlisten verhindern, die nur von internen Benutzern verwendet werden sollten.

  - **Postfächer, die keine Nachrichten über das Internet empfangen dürfen sollen**   Sie können die Zustellung von Internet-E-Mails an ein bestimmtes Postfach bzw. an einen Alias verhindern, das/der normalerweise innerhalb der Organisation verwendet wird, z. B. **Helpdesk**.

Der Empfängerfilter-Agent verarbeitet Empfänger, die in einer der beiden folgenden Datenquellen gespeichert sind:

  - **Liste blockierter Empfänger**   Eine vom Administrator definierte Liste von Empfängern, die keine Nachrichten aus dem Internet empfangen sollen.

  - **Empfängersuche**   Fragt Active Directory ab, um zu prüfen, ob der Empfänger in der Organisation vorhanden ist. Auf einem Edge-Transport-Server wird für die Empfängersuche Zugriff auf Active Directory-Informationen benötigt, die EdgeSync der lokalen Instanz von Active Directory Lightweight Directory Services (AD LDS) bereitstellt.

Wenn der Empfängerfilter-Agent aktiviert wird, wird entsprechend der Eigenschaften des Empfängers mit eingehenden Nachrichten eine der folgenden Aktionen ausgeführt. Diese Empfänger werden durch die RCPT TO-Kopfzeile identifiziert.

  - Wenn die eingehende Nachricht einen Empfänger enthält, der in der Liste blockierter Empfänger steht, sendet der Server mit Exchange den SMTP-Sitzungsfehler `550 5.1.1 User unknown` an den Absenderserver.

  - Wenn die eingehende Nachricht einen Empfänger enthält, der keinem Empfänger in der Empfängersuche entspricht, sendet der Server mit Exchange den SMTP-Sitzungsfehler `550 5.1.1 User unknown` an den Absenderserver.

  - Wenn der Empfänger weder in der Liste blockierter Empfänger noch in der Empfängersuche zu finden ist, sendet der Server mit Exchange die SMTP-Antwort `250 2.1.5 Recipient OK` an den Absenderserver, und der nächste Antispam-Agent in der Reihe verarbeitet die Nachricht.

**Inhalt**

Configuring recipient lookup

Tarpitting functionality

Multiple namespaces

## Konfigurieren der Empfängersuche

Eins der effektivsten Verfahren zum Verringern von Spam besteht in der Überprüfung von Empfängern vor dem Akzeptieren eingehender Nachrichten aus dem Internet. Mit dem Cmdlet **Set-RecipientFilterConfig** der Exchange-Verwaltungsshell aktivieren Sie die Blockierung von Nachrichten, die an in der Exchange-Organisation nicht vorhandene Empfänger gesendet werden, sowie die Blockierung bestimmter Empfänger. Weitere Informationen finden Sie unter [Verwalten der Empfängerfilterung auf Edge-Transport-Servern](manage-recipient-filtering-on-edge-transport-servers-exchange-2013-help.md).

Wenn Sie in Ihrem Umkreisnetzwerk einen Edge-Transport-Server installiert haben, empfiehlt es sich, die AD LDS-Instanz, die auf dem Edge-Transport-Server ausgeführt wird, mit Active Directory zu synchronisieren. Standardmäßig wird AD LDS auf dem Edge-Transport-Server installiert und konfiguriert. Sie müssen jedoch AD LDS für die Kommunikation mit einem der Active Directory-Domäne beigetretenen globalen Katalogserver konfigurieren, indem Sie den Edge-Transport-Server für Ihr Organisation abonnieren. Weitere Informationen finden Sie unter [Verwenden eines Exchange 2010 oder 2007 Edge-Transport-Servers in Exchange 2013](use-an-exchange-2010-or-2007-edge-transport-server-in-exchange-2013-exchange-2013-help.md).

Zurück zum Seitenanfang

## Teergrubenfunktion (Tarpitting)

Die Empfängersuchfunktion ermöglicht einem Absenderserver die Überprüfung, ob eine E-Mail-Adresse gültig ist oder nicht. Wie bereits erwähnt, sendet der Server mit Exchange, wenn es sich bei dem Empfänger einer eingehenden Nachricht um einen bekannten Empfänger handelt, die SMTP-Antwort `250 2.1.5 Recipient OK` an den Absenderserver zurück. Diese Funktionalität bietet eine ideale Umgebung für einen Verzeichnisdiebstahl-Angriff.

Ein *Verzeichnisdiebstahl-Angriff* ist ein Versuch, gültige E-Mail-Adressen einer bestimmten Organisation zu sammeln, um diese Adressen einer Spamdatenbank hinzuzufügen. Da alle Erlöse aus Spam darauf beruhen, Personen dazu zu bringen, E-Mail-Nachrichten zu öffnen, sind Adressen, von denen bekannt ist, dass sie aktiv sind, eine Art Ware oder Rohstoff, für die/den bösartige Benutzer oder *Spammer* Geld bezahlen. Da das SMTP-Protokoll Rückmeldungen für bekannte und unbekannte Absender liefert, kann ein Spammer ein automatisiertes Programm schreiben, das allgemeine Namen oder Wörterbucheinträge verwendet, um E-Mail-Adressen für eine bestimmte Domäne zu konstruieren. Das Programm sammelt alle E-Mail-Adressen, die die SMTP-Antwort `250 2.1.5 Recipient OK` zurückgeben, und verwirft alle E-Mail-Adressen, die den SMTP-Sitzungsfehler `550 5.1.1 User unknown` zurückgeben. Der Spammer kann anschließend die gültigen E-Mail-Adressen verkaufen oder als Empfänger unerwünschter Nachrichten verwenden.

Zur Bekämpfung von Verzeichnisdiebstahl-Angriffen enthält Exchange 2013 eine Teergrubenfunktion (Tarpitting). Beim *Teergrubenverfahren* handelt es sich um eine Methode, bei der Serverantworten auf bestimmte SMTP-Kommunikationsmuster, die auf hohe Volumen von Spam oder anderen unerwünschten Nachrichten hindeuten, künstlich verzögert werden. Das Ziel des Teergrubenverfahrens ist es, den Kommunikationsprozess für solchen E-Mail-Verkehr zu verlangsamen, um die Kosten des Versendens von Spam für die Person oder Organisation, von der der Spam gesendet wird, zu erhöhen. Durch das Teergrubenverfahren werden Verzeichnisdiebstahl-Angriffe zu kostspielig, um sie effizient automatisieren zu können.

Wenn das Teergrubenverfahren nicht konfiguriert ist, gibt der Server mit Exchange sofort den SMTP-Sitzungsfehler `550 5.1.1 User unknown` an den Absender zurück, wenn ein Empfänger nicht in der Empfängersuche enthalten ist. Alternativ wartet SMTP bei konfigurierter Teergrubenfunktion eine festgelegte Anzahl von Sekunden, bevor der Fehler `550 5.1.1 User unknown` zurückgegeben wird. Diese Pause innerhalb der SMTP-Sitzung erschwert die Automatisierung eines Verzeichnisdiebstahl-Angriffs und erhöht die Kosten für den Spammer. Das Teergrubenverfahren ist für Empfangsconnectors standardmäßig auf 5 Sekunden festgelegt.

Zum Konfigurieren der Verzögerung, bevor SMTP den Fehler `550 5.1.1 User unknown` zurückgibt, legen Sie das Teergrubenintervall mit dem Parameter *TarpitInterval* des Cmdlets **Set-ReceiveConnector** fest. Die Syntax lautet:

```powershell
Set-ReceiveConnector <Receive Connector> -TarpitInterval <00:00:00 to 00:10:00>
```

Der Standardwert ist `00:00:05` oder 5 Sekunden. Der Name des Standardempfangsconnectors auf einem Edge-Transport-Server lautet `Default internal receive connector <server name>`.

Gehen Sie mit Umsicht vor, wenn Sie sich entscheiden, diesen Wert zu ändern. Ein übermäßig langes Intervall kann die normale Nachrichtenübermittlung unterbrechen, während ein zu kurzes Intervall möglicherweise nicht ausreichend effektiv beim Abwehren eines Verzeichnisdiebstahl-Angriffs ist. Wenn Sie das Teergrubenintervall ändern, nehmen Sie die Änderung in kleinen Schritten vor, und überprüfen Sie die Ergebnisse. Wenn ein Wert von 5 Sekunden beispielsweise nicht effektiv ist, ändern Sie das Intervall in 10 Sekunden.

Zurück zum Seitenanfang

## Mehrere Namespaces

Der Empfängerfilter-Agent führt Empfängersuchen nur für autoritative Domänen durch. Wenn Ihre Organisation Nachrichten im Auftrag einer anderen Domäne akzeptiert und weiterleitet, die als interne oder externe Relaydomäne konfiguriert ist, wendet der Empfängerfilter-Agent keine Empfängersuche auf die Empfänger in diesen Domänen an. Wenn der Empfänger allerdings in der Liste blockierter Empfänger angegeben ist, wird der Empfänger weiter vom Empfängerfilter-Agent blockiert.

Sie können auch akzeptierte Domänen lokal auf einem Edge-Transport-Server konfigurieren. Wenn die Domäne als interne oder externe Relaydomäne konfiguriert ist, führt der Empfängerfilter-Agent auf dem Edge-Transport-Server keine Empfängersuche in diesen Domänen durch.

Zurück zum Seitenanfang

