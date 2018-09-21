---
title: 'PICKUP-Verzeichnis und Wiedergabeverzeichnis: Exchange 2013 Help'
TOCTitle: PICKUP-Verzeichnis und Wiedergabeverzeichnis
ms:assetid: ae191700-953f-411c-906f-dc90feec3d5a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124230(v=EXCHG.150)
ms:contentKeyID: 50476471
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# PICKUP-Verzeichnis und Wiedergabeverzeichnis

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das PICKUP-Verzeichnis und das Wiedergabeverzeichnis sind standardmäßig auf jedem Microsoft Exchange Server 2013-Postfachserver oder Edge-Transport-Server vorhanden. Ordnungsgemäß formatierte E-Mails, die in das PICKUP- oder Wiedergabeverzeichnis kopiert werden, werden zur Zustellung übermittelt. Das PICKUP-Verzeichnis wird von Administratoren zum Testen der Nachrichtenübermittlung oder von Anwendungen verwendet, die ihre eigenen Nachrichten erstellen und senden müssen. Das Wiedergabeverzeichnis empfängt Nachrichten von fremden Gatewayservern und kann dazu verwendet, Nachrichten erneut zu übermitteln, die von Administratoren aus den Warteschlangen von Exchange-Servern exportiert werden.

**Inhalt**

Aufbau einer E-Mail-Datei

Verarbeitung von Nachrichten im PICKUP- und im Wiedergabeverzeichnis

Voraussetzungen für eine Nachrichtendatei im PICKUP-Verzeichnis

Nachrichtenkopfänderungen im PICKUP-Verzeichnis

Voraussetzungen für eine Nachrichtendatei im Wiedergabeverzeichnis

Nachrichtenkopfänderungen im Wiedergabeverzeichnis

Fehler beim Verarbeiten von Nachrichten im PICKUP- und Wiedergabeverzeichnis

Sicherheitsüberlegungen für das PICKUP- und das Wiedergabeverzeichnis

Berechtigungen für das PICKUP- und das Wiedergabeverzeichnis

## Aufbau einer E-Mail-Datei

Eine standardmäßige SMTP-E-Mail besteht aus einem *Nachrichten-Envelope* und dem Nachrichteninhalt. Der Nachrichten-Envelope enthält Informationen, die für die Übermittlung und Zustellung der Nachricht erforderlich sind. Der Nachrichteninhalt enthält Nachrichtenkopffelder (zusammenfassend als *Nachrichtenkopf* bezeichnet) sowie den Nachrichtentext. Der Nachrichten-Envelope wird in RFC 2821 und der Nachrichtenkopf in RFC 2822 beschrieben.

Wenn ein Absender eine E-Mail verfasst und zur Zustellung übermittelt, enthält die Nachricht die grundlegenden Informationen, die erforderlich sind, um die SMTP-Standards zu erfüllen. Hierzu gehören beispielsweise ein Absender, ein Empfänger, Datum und Uhrzeit der Erstellung der Nachricht sowie optional eine Betreffzeile und ein Nachrichtentext. Diese Informationen sind in der Nachricht selbst und laut Definition im Nachrichtenkopf enthalten.

Der Messagingserver des Absenders generiert aus den Absender- und Empfängerinformationen des Nachrichtenkopfes einen Nachrichten-Envelope für die Nachricht und übermittelt diese dann an das Internet zur Zustellung an den Messagingserver des Empfängers. Empfänger bekommen den Nachrichten-Envelope nicht angezeigt, da er vom Nachrichtenübermittlungsprozess generiert wird und nicht tatsächlicher Bestandteil der Nachricht ist.

Jeder Server, der an der Übermittlung der Nachricht beteiligt ist, kann Nachrichtenkopffelder in die Nachricht einfügen, die mit der Funktion des Servers bei der Zustellung der Nachricht oder anderer anwendungsspezifischer Nachrichtenkopffelder in die Nachricht in Zusammenhang stehen. Wenn der Empfänger die Nachricht mit einem E-Mail-Client öffnet, zeigt dieser einige der relevanteren Informationen aus dem Nachrichtenkopf an, beispielsweise den Absender, die Empfänger und den Betreff zusammen mit dem Nachrichtentext.

Zurück zum Seitenanfang

## Verarbeitung von Nachrichten im PICKUP- und im Wiedergabeverzeichnis

In Exchange 2013 lautet der Standardpfad des PICKUP-Verzeichnisses `%ExchangeInstallPath%TransportRoles\Pickup`. Der Standardpfad des Wiedergabeverzeichnisses lautet `%ExchangeInstallPath%TransportRoles\Replay`. Eine ordnungsgemäß formatierte EML-Nachrichtendatei, die in das PICKUP- oder Wiedergabeverzeichnis kopiert wurde, wird anhand der folgenden Schritte für die Übermittlung verarbeitet:

1.  Das PICKUP- und das Wiedergabeverzeichnis werden alle fünf Sekunden auf neue Nachrichtendateien überprüft. Dieses Abfrageintervall kann nicht geändert werden. Die Rate der Nachrichtendateiverarbeitung kann mithilfe des Parameters *PickupDirectoryMaxMessagesPerMinute* des Cmdlets **Set-TransportService** angepasst werden. Dieser Parameter wirkt sich auf das PICKUP-Verzeichnis und das Wiedergabeverzeichnis aus. Der Standardwert beträgt 100 Nachrichten pro Minute. Dateien, die nicht geöffnet werden können, verbleiben im PICKUP-Verzeichnis und werden beim nächsten Abfrageintervall erneut ausgewertet.

2.  Es wird auf Beschränkungen geprüft, die für Nachrichtendateien im PICKUP-Verzeichnis gelten, z. B. die maximale Kopfzeilengröße und die maximale Anzahl von Empfängern. Standardmäßig beträgt die maximale Kopfzeilengröße 64 KB, und die maximale Empfängeranzahl ist auf 100 festgelegt. Sie können diese Grenzwerte mithilfe des Cmdlets **Set-TransportService** ändern. Diese Einstellungen betreffen nur das PICKUP-Verzeichnis.

3.  Die Datei wird von *\<Dateiname\>*.eml in *\<Dateiname\>*.tmp umbenannt. Wenn die Datei *\<Dateiname\>*.tmp bereits vorhanden ist, wird die Datei in *\<Dateiname\>\<DatumUhrzeit\>*.tmp umbenannt. Schlägt das Umbenennen der Datei fehl, wird ein Fehler im Ereignisprotokoll generiert, und der PICKUP-Prozess geht zur nächsten Datei über.

4.  Nachdem die TMP-Datei erfolgreich in eine E-Mail konvertiert wurde, wird ein **delete on close**-Befehl an die TMP-Datei ausgegeben. Die TMP-Datei scheint im PICKUP-Verzeichnis zu verbleiben, kann aber nicht geöffnet werden.

5.  Nachdem die Nachricht erfolgreich zur Zustellung in die Warteschlange eingereiht wurde, wird ein **close**-Befehl ausgegeben, und die TMP-Datei wird aus dem PICKUP-Verzeichnis gelöscht. Schlägt der Löschvorgang fehl, wird ein Fehler im Ereignisprotokoll generiert. Wird der Microsoft Exchange-Transportdienst neu gestartet, während sich noch TMP-Dateien im PICKUP-Verzeichnis befinden, werden alle TMP-Dateien in EML-Dateien umbenannt und erneut verarbeitet. Dadurch kann es zu doppelten Nachrichtenübertragungen kommen.

Zurück zum Seitenanfang

## Voraussetzungen für eine Nachrichtendatei im PICKUP-Verzeichnis

Eine Nachrichtendatei, die in das PICKUP-Verzeichnis kopiert wird, muss die folgenden Voraussetzungen erfüllen, damit eine erfolgreiche Zustellung gewährleistet ist:

  - Die Nachrichtendatei muss eine Textdatei sein, die dem grundlegenden SMTP-Nachrichtenformat entspricht. Felder und Inhalt von MIME-Nachrichtenköpfen werden nicht unterstützt.

  - Die Nachrichtendatei muss die Dateinamenerweiterung .eml aufweisen.

  - Im Nachrichtenkopf muss mindestens eine E-Mail-Adresse in den Nachrichtenkopffeldern `Sender` oder `From` angegeben sein. Wenn nur eine E-Mail-Adresse in den Feldern `Sender` und `From` vorhanden ist, wird die E-Mail-Adresse im Feld `From` als Verfasser der Nachricht im Nachrichten-Envelope verwendet.

  - Es darf nur eine E-Mail-Adresse im Feld `Sender` vorhanden sein. Mehrere E-Mail-Adressen sind nicht zulässig. Das Feld `Sender` ist optional, wenn es im Feld `From` nur eine E-Mail-Adresse gibt.

  - Im Feld `From` sind mehrere E-Mail-Adressen zulässig, aber es muss auch eine einzelne E-Mail-Adresse im Feld `Sender` vorhanden sein. Die Adresse im Feld `Sender` wird dann als Verfasser der Nachricht im Nachrichten-Envelope verwendet.

  - Es muss mindestens eine E-Mail-Adresse im Feld `To`, `Cc` oder `Bcc` vorhanden sein.

  - Nachrichtenkopf und Nachrichtentext müssen durch eine Leerzeile getrennt sein.

Dieses Beispiel zeigt eine Nur-Text-Nachricht, die eine akzeptable Formatierung für das PICKUP-Verzeichnis verwendet.

    To: mary@contoso.com
    From: bob@fabrikam.com
    Subject: Message subject
    
    This is the body of the message.

In Nachrichtendateien des PICKUP-Verzeichnisses werden auch MIME-Inhalte unterstützt. MIME definiert eine breite Palette von Nachrichteninhalten, wozu auch Sprachen gehören, die nicht als 7-Bit-ASCII-Text darstellbar sind, sowie HTML und andere Multimediainhalte. Eine vollständige Beschreibung von MIME und den für diesen Standard geltenden Voraussetzungen würde den Rahmen dieses Themas jedoch sprengen. Dieses Beispiel zeigt eine einfache MIME-Nachricht, die eine akzeptable Formatierung für das PICKUP-Verzeichnis verwendet.

    To: mary@contoso.com
    From: bob@fabrikam.com
    Subject: Message subject
    MIME-Version: 1.0
    Content-Type: text/html; charset="iso-8859-1"
    Content-Transfer-Encoding: 7bit
    
    <HTML><BODY>
    <TABLE>
    <TR><TD>cell 1</TD><TD>cell 2</TD></TR>
    <TR><TD>cell 3</TD><TD>cell 4</TD></TR>
    </TABLE>

    </BODY></HTML>

Zurück zum Seitenanfang

## Nachrichtenkopfänderungen im PICKUP-Verzeichnis

Das PICKUP-Verzeichnis entfernt die folgenden Felder aus dem Nachrichtenkopf:

  - `Received`

  - `Resent-*`

  - `Bcc`
    

    > [!NOTE]
    > Alle E-Mail-Adressen, die im Nachrichtenkopf in den optionalen <CODE>Bcc</CODE>-Nachrichtenkopffeldern enthalten sind, werden ordnungsgemäß verarbeitet. Nachdem die <CODE>Bcc</CODE>-Empfänger in unsichtbare Nachrichten-Envelopeempfänger übertragen wurden, werden sie aus dem Nachrichtenkopf entfernt, um ihre Identität zu schützen. Wenn eine Nachricht nur <CODE>Bcc</CODE>-Empfänger enthält, wird der Wert von <STRONG>Undisclosed Recipients</STRONG> dem Feld <CODE>To</CODE> im Nachrichtenkopf hinzugefügt.



Im PICKUP-Verzeichnis wird einer Nachricht das eigene `Received`-Kopfzeilenfeld im Rahmen des Nachrichtenübermittlungsprozesses hinzugefügt. Das `Received`-Nachrichtenkopffeld wird im folgenden Format angewendet

    Received: from localhost by Pickup with Microsoft SMTP Server id <ExchangeServerVersion><datetime>

Das PICKUP-Verzeichnis ändert die folgenden Nachrichtenkopffelder, falls diese fehlen oder fehlerhaft sind:

  - **Message-Id**   Wenn das Feld `Message-Id` fehlt oder leer ist, fügt das PICKUP-Verzeichnis ein Message-ID-Feld im Format *\<GUID\>*@*\<Standarddomaene\>* hinzu.

  - **Date**   Wenn das Feld `Date` fehlt oder fehlerhaft ist, wird der Zeitpunkt (Datum und Uhrzeit) hinzugefügt, zu dem die Nachricht im PICKUP-Verzeichnis verarbeitet wurde.

Zurück zum Seitenanfang

## Voraussetzungen für eine Nachrichtendatei im Wiedergabeverzeichnis

Das Wiedergabeverzeichnis wird für die erneute Übermittlung exportierter Exchange-Nachrichten sowie zum Empfangen von Nachrichten von fremden Gatewayservern verwendet. Diese Nachrichten sind bereits für das Wiedergabeverzeichnis formatiert. Es besteht selten bzw. keine Notwendigkeit, dass ein Administrator oder eine andere Anwendung mithilfe des Wiedergabeverzeichnisses neue Nachrichtendateien erstellt und übermittelt. Zum Erstellen und Übermitteln neuer Nachrichtendateien muss das PICKUP-Verzeichnis verwendet werden.

Bei den Nachrichten im Wiedergabeverzeichnis werden in hohem Maße *X-Header* verwendet. X-Header sind benutzerdefinierte, inoffizielle Nachrichtenkopffelder, die im Nachrichtenkopf vorhanden sind. X-Header werden in RFC 2822 nicht speziell erwähnt, die Verwendung eines nicht definierten Nachrichtenkopffelds, das mit "X-" beginnt, ist jedoch mittlerweile ein anerkannter Weg, um einer Nachricht inoffizielle Nachrichtenkopffelder hinzuzufügen. Die Exchange-spezifischen X-Header, die in Nachrichtendateien im Wiedergabeverzeichnis verwendet werden, können Zustellinformationen festlegen, die normalerweise im Nachrichten-Envelope vorhanden sind. Dieses Feature ist erforderlich, um ursprüngliche Nachrichteninformationen zu erhalten, wenn Sie das Wiedergabeverzeichnis zum Verarbeiten von Nachrichten verwenden, die von einem anderen Exchange-Server exportiert wurden.

Eine Nachrichtendatei, die in das Wiedergabeverzeichnis kopiert wird, muss die folgenden Voraussetzungen erfüllen, damit eine erfolgreiche Zustellung gewährleistet ist:

  - Die Nachrichtendatei muss eine Textdatei sein, die dem grundlegenden SMTP-Nachrichtenformat entspricht. Felder und Inhalt von MIME-Nachrichtenköpfen werden nicht unterstützt.

  - Die Nachrichtendatei muss die Dateinamenerweiterung .eml aufweisen.

  - X-Kopfzeilen müssen vor allen anderen regulären Kopfzeilenfeldern stehen.

  - Der Nachrichtentext muss durch eine Leerzeile von den Kopfzeilenfeldern getrennt sein.

Die in der folgenden Liste beschriebenen X-Header sind für Nachrichten im Wiedergabeverzeichnis erforderlich:

  - **X-Sender**   Diese X-Kopfzeile ersetzt die Anforderung eines `From`-Nachrichtenkopffelds in einer typischen SMTP-Nachricht. Es muss ein `X-Sender`-Feld vorhanden sein, das eine E-Mail-Adresse enthält. Das Wiedergabeverzeichnis ignoriert ein eventuell vorhandenes `From`-Nachrichtenkopffeld, obwohl der Wert des `From`-Nachrichtenkopffelds im E-Mail-Client des Empfängers als Absender der Nachricht angezeigt wird. Normalerweise sind noch andere Parameter im `X-Sender`-Feld vorhanden, wie im folgenden Beispiel dargestellt.
    
    ```powershell
X-Sender: <bob@fabrikam.com> BODY=7bit RET=HDRS ENVID=12345ABCD auth=<someAuth>
```
    

    > [!NOTE]
    > Diese Parameter sind Nachrichten-Envelopewerte, die normalerweise vom sendenden Server generiert werden. Möglicherweise finden Sie in exportierten Nachrichtendateien Parameter vor, die diesen ähnlich sind.<BR><CODE>RET</CODE> gibt an, ob die gesamte Nachricht oder nur die Kopfzeilen an den Absender zurückgegeben werden sollen, wenn die Nachricht nicht zugestellt werden kann. <CODE>RET</CODE> kann den Wert <CODE>HDRS</CODE> oder <CODE>FULL</CODE> aufweisen. <CODE>ENVID</CODE> ist ein Nachrichten-Envelopebezeichner. <CODE>BODY</CODE> gibt die Textcodierung der Nachricht an. <CODE>auth</CODE> gibt dem Messagingserver einen Authentifizierungsmechanismus an, wie in RFC 2554 beschrieben.



  - **X-Receiver**   Diese X-Kopfzeile ersetzt die Anforderung eines `To`-Nachrichtenkopffelds in einer typischen SMTP-Nachricht. Mindestens ein `X-Receiver`-Feld, das eine E-Mail-Adresse enthält, muss vorhanden sein. Für mehrere Empfänger sind mehrere `X-Receiver`-Kopfzeilenfelder zulässig. Das Wiedergabeverzeichnis ignoriert eventuell vorhandene `To`-Nachrichtenkopffelder, obwohl die Werte der `To`-Nachrichtenkopffelder im E-Mail-Client des Empfängers als Empfänger der Nachricht angezeigt werden. Wie im folgenden Beispiel dargestellt, können weitere Parameter in den `X-Receiver`-Feldern vorhanden sein.
    
    ```powershell
X-Receiver: <mary@contoso.com> NOTIFY=NEVER ORcpt=mary@contoso.com
```
    

    > [!NOTE]
    > Diese Parameter sind Nachrichten-Envelopewerte, die normalerweise vom sendenden Server generiert werden. Möglicherweise finden Sie in exportierten Nachrichtendateien Parameter vor, die diesen ähnlich sind. Diese Parameter stehen in Zusammenhang mit DSN-Nachrichten (Delivery Status Notification, Benachrichtigung über den Übermittlungsstatus), wie in RFC&nbsp;1891 beschrieben.<BR><CODE>NOTIFY</CODE> kann den Wert <CODE>NEVER</CODE>, <CODE>DELAY</CODE> oder <CODE>FAILURE</CODE> aufweisen. <CODE>ORcpt</CODE> behält den ursprünglichen Empfänger der Nachricht bei.



Die in der folgenden Liste beschriebenen X-Header sind für Nachrichtendateien im Wiedergabeverzeichnis optional:

  - **X-CreatedBy**   Dieses Feld wird für Firewallfunktionen verwendet. Wenn diese X-Kopfzeile vorhanden ist, darf sie nicht leer sein. Ist das Feld `X-CreatedBy` nicht vorhanden, wird es mit dem Wert **Unspecified** hinzugefügt. Normalerweise hat dieses Feld den Wert **MSExchange15**, es kann jedoch auch den für einen Sendeconnector festgelegten Nicht-SMTP-Adressraumtyp enthalten, beispielsweise **Notes**.

  - **X-EndOfInjectedXHeaders**   Größe in Bytes für alle vorhandenen X-Header. Diese X-Kopfzeile kann zum Markieren der letzten X-Kopfzeile vor Beginn der regulären Nachrichtenkopffelder verwendet werden.

  - **X-ExtendedMessageProps**   Erweiterte Nachrichteneigenschaften für die Nachricht.

  - **X-HeloDomain**   Die während der anfänglichen SMTP-Protokollverhandlung vorgelegte HELO/EHLO-Domänenzeichenfolge.

  - **X-Source**   Wird von der Warteschlangenanzeige unterhalb der Spalte **MessageSourceName** verwendet. Wenn der Wert dieser X-Kopfzeile nicht angegeben ist, wird der Wert **Replay** verwendet. Andere mögliche Werte für diese X-Kopfzeile sind **Smtp Receive Connector** und **Smtp Send Connector**.

  - **X-SourceIPAddress**   Die IP-Adresse des sendenden Servers. Wenn keine IP-Adresse angegeben ist, lautet der Wert dieses Felds `0.0.0.0`.

Dieses Beispiel zeigt eine Nur-Text-Nachricht, die eine akzeptable Formatierung für das Wiedergabeverzeichnis verwendet.

```powershell
X-Receiver: <mary@contoso.com> NOTIFY=NEVER ORcpt=mary@contoso.com
```
    X-Sender: <bob@fabrikam.com> BODY=7bit ENVID=12345AB auth=<someAuth>
    Subject: Optional message subject
    
    This is the body of the message.

In Nachrichtendateien des Wiedergabeverzeichnisses werden auch MIME-Inhalte unterstützt. MIME definiert eine breite Palette von Nachrichteninhalten, wozu auch Sprachen gehören, die nicht als 7-Bit-ASCII-Text darstellbar sind, sowie HTML und andere Multimediainhalte. Eine vollständige Beschreibung von MIME und den für diesen Standard geltenden Voraussetzungen würde den Rahmen dieses Themas jedoch sprengen. Dieses Beispiel zeigt eine einfache MIME-Nachricht, die eine akzeptable Formatierung für das Wiedergabeverzeichnis verwendet.

```powershell
X-Receiver: <mary@contoso.com> NOTIFY=NEVER ORcpt=mary@contoso.com
```
    X-Sender: <bob@fabrikam.com> BODY=7bit ENVID=12345ABCD auth=<someAuth>
    To: mary@contoso.com
    From: bob@fabrikam.com
    Subject: Optional message subject
    MIME-Version: 1.0
    Content-Type: text/html; charset="iso-8859-1"
    Content-Transfer-Encoding: 7bit
    
    <HTML><BODY>
    <TABLE>
    <TR><TD>cell 1</TD><TD>cell 2</TD></TR>
    <TR><TD>cell 3</TD><TD>cell 4</TD></TR>
    </TABLE>

    </BODY></HTML>

Zurück zum Seitenanfang

## Nachrichtenkopfänderungen im Wiedergabeverzeichnis

Im Wiedergabeverzeichnis wird das `Bcc`-Nachrichten-Kopfzeilenfeld aus der Nachrichtendatei gelöscht.

Im Wiedergabeverzeichnis wird einer Nachricht das eigene `Received`-Nachrichten-Kopfzeilenfeld im Rahmen des Nachrichtenübermittlungsprozesses hinzugefügt. Das Received-Nachrichtenkopffeld wird im folgenden Format angewendet.

    Received: from <ReceivingServerName> by Replay with <ExchangeServerVersion><DateTime>

Im Wiedergabeverzeichnis werden die folgenden Nachrichtenkopffelder im Nachrichtenkopf geändert:

  - **Message-ID**   Wenn dieses Nachrichtenkopffeld fehlt oder leer ist, fügt das Wiedergabeverzeichnis ein entsprechendes Feld im Format *\<GUID\>*@*\<Standarddomaene\>* hinzu.

  - **Date**   Wenn dieses Nachrichtenkopffeld fehlt oder leer ist, fügt das Wiedergabeverzeichnis ein entsprechendes Feld mit Datum und Uhrzeit der Nachrichtenverarbeitung durch das Wiedergabeverzeichnis hinzu.

Zurück zum Seitenanfang

## Fehler beim Verarbeiten von Nachrichten im PICKUP- und Wiedergabeverzeichnis

Eine in das PICKUP- oder Wiedergabeverzeichnis kopierte Nachrichtendatei wird möglicherweise nicht erfolgreich für die Zustellung in die Warteschlange eingereiht. Die folgenden Kategorien für Nachrichtenübermittlungsfehler können auftreten:

  - **Zustellungsfehler**   Eine ordnungsgemäß formatierte Nachrichtendatei mit einem gültigen Absender, die nicht erfolgreich für die Zustellung übermittelt werden kann, generiert einen Unzustellbarkeitsbericht. Fehlerhafte Inhalte oder eine Verletzung der Nachrichteneinschränkungen für das PICKUP-Verzeichnis können ebenfalls dazu führen, dass ein Unzustellbarkeitsbericht generiert wird. Wenn während der Verarbeitung der Nachricht ein Unzustellbarkeitsbericht generiert wird, wird die ursprüngliche Nachrichtendatei an die Nachricht des Unzustellbarkeitsberichts angefügt und die Nachrichtendatei aus dem PICKUP-Verzeichnis oder Wiedergabeverzeichnis gelöscht.
    

    > [!NOTE]
    > Eine ordnungsgemäß formatierte Nachricht, die in die Transportpipeline übermittelt wurde, kann später einen Zustellungsfehler aufweisen und mit einem Unzustellbarkeitsbericht an den Absender zurückgesendet werden. Diese Art von Fehler kann durch Übertragungsprobleme hervorgerufen werden, die nichts mit dem PICKUP- oder Wiedergabeverzeichnis zu tun haben, etwa Messagingserverfehler oder Routingfehler im Zustellungspfad der Nachricht.



  - **BadMail**   Eine als *BadMail* klassifizierte Nachricht weist schwerwiegende Probleme auf, die eine Übermittlung für die Zustellung durch das PICKUP- oder Wiedergabeverzeichnis verhindern. Die zweite Bedingung, die zu einer Badmail führt, liegt vor, wenn die Nachricht richtig formatiert ist, jedoch ein ungültiger Empfänger vorliegt und kein Unzustellbarkeitsbericht an den Absender gesendet werden kann, da der Absender ungültig ist.
    
    Nachrichtendateien, die als BadMail eingestuft sind, verbleiben im PICKUP- oder Wiedergabeverzeichnis und werden von "*\<Dateiname\>*.eml" in "*\<Dateiname\>*.bad" umbenannt. Wenn die Datei *\<Dateiname\>*.bad bereits vorhanden ist, wird die Datei in *\<Dateiname*\<DatumUhrzeit\>\<.bad umbenannt. Sind im PICKUP- oder Wiedergabeverzeichnis BadMailnachrichten vorhanden, wird ein Fehler im Ereignisprotokoll generiert, aber dieselben BadMailnachrichten generieren keine wiederholten Fehler im Ereignisprotokoll.
    

    > [!NOTE]
    > Erstellen und Speichern Sie Nachrichtendateien immer an einem anderen Ort, bevor Sie diese zur Zustellung in das PICKUP-Verzeichnis kopieren. Das PICKUP-Verzeichnis wird alle fünf Sekunden auf neue Nachrichten überprüft. Wenn Sie daher versuchen, die Nachrichtendateien im PICKUP-Verzeichnis selbst zu erstellen und zu speichern, versucht das PICKUP-Verzeichnis vielleicht, die Nachrichtendateien zu verarbeiten, bevor Sie mit dem Verfassen fertig sind.



Zurück zum Seitenanfang

## Sicherheitsüberlegungen für das PICKUP- und das Wiedergabeverzeichnis

In der folgenden Liste werden Sicherheitsrisiken für das PICKUP- und Wiedergabeverzeichnis beschrieben:

  - Alle Sicherheitsüberprüfungen, die für einen Empfangsconnector konfiguriert sind, beispielsweise Antispam-, Antischadsoftware-, Absenderfilterungs- oder Empfängerfilterungsaktionen, werden nicht für Nachrichten ausgeführt, die über das PICKUP- oder das Wiedergabeverzeichnis übermittelt werden.

  - Ein gefährdetes PICKUP- oder Wiedergabeverzeichnis kann als offenes Relay fungieren. Dies ermöglicht die erneute Übermittlung von Nachrichten bzw. deren *Relay* unter Verwendung eines anderen Servers, um die wahre Quelle der Nachrichten zu verschleiern.

In der folgenden Liste werden zusätzliche Sicherheitsrisiken für das Wiedergabeverzeichnis beschrieben:

  - Die vom Wiedergabeverzeichnis verwendeten X-Header lassen die manuelle Erstellung des Nachrichten-Envelopes zu. Die in den `X-Sender`- und `X-Receiver`-Feldern enthaltenen Informationen können vollständig von den `To`- oder `From`-Nachrichtenkopffeldern abweichen, die von E-Mail-Clients angezeigt werden. Ein solcher Identitätswechsel eines Absenders und einer Domäne wird häufig als *Spoofing* bezeichnet. Eine *Spoof-E-Mail* ist eine E-Mail, die eine Absenderadresse hat, die so geändert wurde, dass sie von einem anderen Absender als dem tatsächlichen Absender der Nachricht zu stammen scheint.

  - Wenn das `X-CreatedBy`-Feld den Wert **MSExchange15** hat, wird das Ziel als vertrauenswürdig eingestuft, und die Kopfzeilenfirewall wird nicht angewendet. Die *Kopfzeilenfirewall* ist ein Verfahren für Exchange, die X-Header in Nachrichten zu erhalten, die zwischen vertrauenswürdigen Exchange-Servern übermittelt werden, oder potenziell verräterische X-Header aus Nachrichten zu entfernen, die an nicht vertrauenswürdige Ziele außerhalb der Exchange-Organisation übermittelt werden. Mithilfe dieser X-Header können Exchange-Informationen wie SCL-Bewertung (Spam Confidence Level), Nachrichtensignierung oder Verschlüsselung zwischen autorisierten Exchange-Servern freigegeben werden. Die Offenlegung solcher Informationen gegenüber nicht autorisierten Quellen kann ein potenzielles Sicherheitsrisiko darstellen. Weitere Informationen zur Kopfzeilenfirewall finden Sie unter [Grundlegendes zur Kopfzeilenfirewall](https://go.microsoft.com/fwlink/?linkid=268394).

Auf das Wiedergabeverzeichnis sollten wegen der damit einhergehenden zusätzlichen Sicherheitsrisiken stärkere Sicherheitsmaßnahmen angewendet werden. Benutzern oder Anwendungen, die Nachrichten generieren und übermitteln müssen, kann der Zugriff auf das PICKUP-Verzeichnis gewährt werden, aber es sollte kein Zugriff auf das Wiedergabeverzeichnis erteilt werden.

Sowohl das PICKUP-Verzeichnis als auch das Wiedergabeverzeichnis sind auf allen Postfachservern und Edge-Transport-Servern standardmäßig aktiviert. Wenn das PICKUP-Verzeichnis oder das Wiedergabeverzeichnis auf einem bestimmten Postfachserver oder Edge-Transport-Server in Ihrer Organisation nicht erforderlich ist, können Sie es auf diesem Server deaktivieren, indem Sie den Pfad des PICKUP- oder des Wiedergabeverzeichnisses auf den Wert `$null` festlegen. Weitere Informationen finden Sie unter [Konfigurieren des PICKUP-Verzeichnisses und des Wiedergabeverzeichnisses](configure-the-pickup-directory-and-the-replay-directory-exchange-2013-help.md).

Zurück zum Seitenanfang

## Berechtigungen für das PICKUP- und das Wiedergabeverzeichnis

Die folgenden Berechtigungen sind für das PICKUP- und Wiedergabeverzeichnis erforderlich:

  - Administrator: Vollzugriff

  - System: Vollzugriff

  - Netzwerkdienst: Lesen, Schreiben und Löschen von Unterordnern und Dateien

Der Microsoft Exchange-Transportdienst verwendet standardmäßig die Sicherheitsanmeldeinformationen des Netzwerkdienst-Benutzerkontos, um den Speicherort und die Berechtigungen des PICKUP- und des Wiedergabeverzeichnisses zu verwalten. Das Netzwerkdienstkonto benötigt diese Berechtigungen für das PICKUP-Verzeichnis, damit EML-Dateien geöffnet, in TMP umbenannt und gelöscht bzw. in BAD umbenannt werden können, wenn die Nachricht als Badmail klassifiziert wurde.

Der Speicherort dieser Verzeichnisse kann mithilfe der Parameter *PickupDirectoryPath* und *ReplayDirectoryPath* des Cmdlets **Set-TransportService** verschoben werden. Das erfolgreiche Ändern des Speicherorts für das PICKUP-Verzeichnis hängt von den Rechten ab, die dem Netzwerkdienstkonto an den neuen Verzeichnispositionen gewährt werden, und davon, ob die neuen Verzeichnisse bereits vorhanden sind. Wenn das Verzeichnis noch nicht vorhanden ist und das Netzwerkdienstkonto über die notwendigen Rechte zum Erstellen von Ordnern und Anwenden von Berechtigungen am neuen Speicherort verfügt, wird das neue Verzeichnis erstellt und die korrekten Berechtigungen darauf angewendet. Wenn das neue Verzeichnis bereits vorhanden ist, werden die vorhandenen Ordnerberechtigungen nicht überprüft. Wenn Sie einen Verzeichnisspeicherort über den Parameter *PickupDirectoryPath* oder *ReplayDirectoryPath* des Cmdlets **Set-TransportService** verschieben, sollten Sie sich immer vergewissern, dass das neue Verzeichnis vorhanden und mit den richtigen Berechtigungen konfiguriert ist.

Zurück zum Seitenanfang

