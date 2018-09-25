---
title: 'Verwenden von Telnet zum Testen der SMTP-Kommunikation: Exchange 2013 Help'
TOCTitle: Verwenden von Telnet zum Testen der SMTP-Kommunikation
ms:assetid: 8a5f6715-baa4-48dd-8600-02c6b3d1aa9d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123686(v=EXCHG.150)
ms:contentKeyID: 52062876
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden von Telnet zum Testen der SMTP-Kommunikation

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird erläutert, wie Sie Telnet zum Testen der SMTP-Kommunikation (Simple Mail Transfer Protocol) zwischen Messagingservern verwenden können. Standardmäßig überwacht SMTP Port 25. Wenn Sie Telnet für Port 25 verwenden, können Sie die SMTP-Befehle, die zum Herstellen einer Verbindung mit einem SMTP-Server und zum Senden einer Nachricht verwendet werden, genau so eingeben, als handele es sich bei Ihrer Telnet-Sitzung um einen SMTP-Messagingserver. Sie können den Erfolg oder Fehler jedes Schritts im Verbindungs- und Nachrichtenübermittlungsprozess erkennen.

Es folgen die die Szenarien, in denen Sie ggf. Telnet zum Testen der SMTP-Kommunikation mit den Transportservern verwenden können, die in Ihrer Microsoft Exchange-Organisation vorhanden sind:

  - Stellen Sie von einem Host aus, der sich außerhalb des Umkreisnetzwerks befindet, eine Verbindung mit dem Internet verbundenen Exchange-Server Ihrer Organisation her, und senden Sie eine Testnachricht.

  - Stellen Sie vom mit dem Internet verbundenen Exchange-Server Ihrer Organisation aus eine Verbindung mit einem Remotemessagingserver her, und senden Sie eine Testnachricht.

Das in diesem Abschnitt beschriebene Verfahren zeigt, wie Sie den Telnet-Client verwenden können, eine in Microsoft Windows eingeschlossene Komponente. Telnet-Clients von Drittanbietern erfordern möglicherweise eine andere Syntax als die Telnet-Komponente von Windows.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren erfolgen im Betriebssystem des Exchange Server-Computers oder eines Clientcomputers.

  - Die Verfahren in diesem Thema eignen sich am besten für ein- und ausgehende Verbindungen mit Servern, die mit dem Internet verbunden sind, und anonyme Verbindungen zulassen. Die Nachrichtenübertragung zwischen internen Exchange-Servern wird verschlüsselt und authentifiziert. Um über Telnet eine Verbindung mit dem Hub-Transport-Dienst auf einem Postfachserver herzustellen, müssen Sie einen Emfangsconnector erstellen, der für den Empfang von Nachrichten den anonymen Zugriff oder die Standardauthentifzierung zulässt. Wenn der Connector die Standardauthentifizierung zulässt, benötigen Sie ein Hilfsprogramm zum Umwandeln der Textzeichenfolgen des Benutzernamens und Kennworts in das Base64-Format. Da der Benutzername und das Kennwort unverschlüsselt gesendet werden, wenn die Standardauthentifizierung verwendet wird, wird die Standardauthentifizierung ohne Verschlüsselung nicht empfohlen.

  - Wenn Sie eine Verbindung mit einem Remotemessagingserver herstellen, erwägen Sie die Ausführung der Verfahren in diesem Thema auf Ihrem mit dem Internet verbundenen Exchange-Server. Dies vermeidet die Ablehnung der Testnachricht durch Remotemessagingserver, die so konfiguriert sind, dass die Quell-IP-Adresse, der entsprechende DNS-Domänenname (Domain Name System) und die Reverse-Lookup-IP-Adresse jedes Internet-Hosts überprüft werden, der versucht, eine Nachricht an den Server zu senden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Installieren des Telnet-Clients unter Windows

Bei den meisten Client- und Serverversionen der Microsoft Windows-Betriebssysteme ist der Telnet-Client nicht standardmäßig installiert. Installationsanweisungen finden Sie unter [Installieren des Telnet-Clients](https://go.microsoft.com/fwlink/p/?linkid=179054).

## Schritt 2: Verwenden von Nslookup zum Bestimmen des FQDN oder der IP-Adresse im MX-Eintrag des SMTP-Remoteservers

Um mithilfe von Telnet an Port 25 eine Verbindung mit einem SMTP-Zielserver herzustellen, müssen Sie den vollqualifizierten Domänennamen (FQDN) oder die IP-Adresse des SMTP-Servers verwenden. Wenn Sie den FQDN oder die IP-Adresse nicht kennen, besteht die einfachste Methode zum Abrufen dieser Informationen im Verwenden des Befehlszeilentools Nslookup, um den MX-Datensatz für die Zieldomäne zu suchen.

1.  Geben Sie an der Eingabeaufforderung **nslookup** ein, und drücken Sie die EINGABETASTE. Dieser Befehl öffnet die Nslookup-Sitzung.

2.  Geben Sie **set type=mx** ein, und drücken Sie die EINGABETASTE.

3.  Geben Sie **set timeout=20** ein, und drücken Sie die EINGABETASTE. Standardmäßig weisen Windows DNS-Server einen Timeoutgrenzwert von 15 Sekunden für rekursive DNS-Abfragen auf.

4.  Geben Sie den Namen der Domäne ein, für die Sie den MX-Datensatz suchen möchten. Um den MX-Datensatz für die Domäne "fabrikam.com" zu suchen, geben Sie beispielsweise **fabrikam.com.** ein und drücken dann die EINGABETASTE.
    

    > [!NOTE]
    > Der nachgestellte Punkt (<STRONG>.</STRONG>) zeigt einen FQDN an. Durch den nachgestellten Punkt wird verhindert, dass DNS-Standardsuffixe, die ggf. für Ihr Netzwerk konfiguriert sind, dem Domänennamen unbeabsichtigt hinzugefügt werden.

    
    Die Ausgabe des Befehls ähnelt der folgenden Ausgabe:
    
    ```powershell
        fabrikam.com mx preference=10, mail exchanger = mail1.fabrikam.com
        fabrikam.com mx preference=20, mail exchanger = mail2.fabrikam.com
        mail1.fabrikam.com internet address = 192.168.1.10
        mail2 fabrikam.com internet address = 192.168.1.20
    ```
    
    Sie können jeden beliebigen Hostnamen oder jede beliebige IP-Adresse verwenden, der bzw. die den MX-Datensätzen als SMTP-Zielserver zugeordnet ist. Ein niedrigerer Präferenzwert gibt einen bevorzugten SMTP-Server an. Sie können mehrere MX-Datensätze und unterschiedliche Präferenzwerte für Lastenausgleich und Fehlertoleranz verwenden.

5.  Wenn Sie bereit sind, die Nslookup-Sitzung zu beenden, geben Sie **exit** ein und drücken dann die EINGABETASTE.


> [!NOTE]
> Firewall- oder Internetproxyeinschränkungen, die für das interne Netzwerk Ihrer Organisation gelten, verhindern ggf. die Verwendung des Tools Nslookup zum Abfragen öffentlicher DNS-Server im Internet.



## Schritt 3: Verwenden von Telnet an Port 25 zum Testen der SMTP-Kommunikation

In diesem Beispiel werden folgende Werte verwendet:

  - **SMTP-Zielserver**   mail1.fabrikam.com

  - **Quelldomäne**   contoso.com

  - **E-Mail-Adresse des Absenders**   chris@contoso.com

  - **E-Mail-Adresse des Empfängers**   kate@fabrikam.com

  - **Nachrichtenbetreff**   Test von Contoso

  - **Nachrichtentext**   Dies ist eine Testnachricht


> [!NOTE]
> <UL>
> <LI>
> <P>Bei den Befehlen im Telnet-Client wird nicht zwischen Groß- und Kleinschreibung unterschieden. Die SMTP-Befehlsverben wurden aus Gründen der Klarheit als Großbuchstaben formatiert.</P>
> <LI>
> <P>Sie können die Rücktaste nicht verwenden, nachdem Sie in der Telnet-Sitzung eine Verbindung mit dem SMTP-Zielserver hergestellt haben. Wenn Ihnen beim Eingeben eines SMTP-Befehls ein Fehler unterläuft, müssen Sie die EINGABETASTE drücken und den Befehl dann erneut eingeben. SMTP-Befehle, die nicht erkannt werden, oder Syntaxfehler führen zu eine Fehlermeldung, die der folgenden Fehlermeldung ähnelt:</P><PRE><CODE>500 5.3.3 Unrecognized command</CODE></PRE></LI></UL>



1.  Geben Sie an der Eingabeaufforderung **telnet** ein, und drücken Sie die EINGABETASTE. Dieser Befehl öffnet die Telnet-Sitzung.

2.  Geben Sie **set localecho** ein, und drücken Sie die EINGABETASTE. Mit diesem optionalen Befehl können Sie die Zeichen anzeigen, die Sie eingeben. Dieses Einstellung ist für einige SMTP-Server möglicherweise erforderlich.

3.  Geben Sie **set logfile***\<Dateiname\>* ein. Dieser optionale Befehl aktiviert die Protokollierung der Telnet-Sitzung in der angegebenen Protokolldatei. Wenn Sie nur einen Dateinamen angeben, ist der Speicherort der Protokolldatei das aktuelle Arbeitsverzeichnis. Wenn Sie einen Pfad und einen Dateinamen angeben, muss der Pfad ein lokaler Computerpfad sein. Der von Ihnen angegebene Pfad und der Dateiname müssen im Microsoft DOS 8.3-Format eingegeben werden. Der angegebene Pfad muss bereits vorhanden sein. Wenn Sie eine noch nicht vorhandene Protokolldatei angeben, wird diese für Sie erstellt.

4.  Geben Sie **open mail1.fabrikam.com 25** ein, und drücken Sie die EINGABETASTE.

5.  Geben Sie **EHLO contoso.com** ein, und drücken Sie die EINGABETASTE.

6.  Geben Sie **MAIL FROM:chris@contoso.com** ein, und drücken Sie die EINGABETASTE.

7.  Geben Sie **RCPT TO:kate@fabrikam.com NOTIFY=success,failure** ein, und drücken Sie die EINGABETASTE. Der optionale NOTIFY-Befehl definiert die jeweiligen Benachrichtigungen über den Zustellungsstatus, die der SMTP-Zielserver dem Absender zur Verfügung stellen muss. DSN-Nachrichten werden in RFC 1891 definiert. In diesem Fall fordern Sie eine DSN-Nachricht für eine erfolgreiche Nachrichtenzustellung bzw. eine Nachrichtenzustellung mit Fehler an.

8.  Geben Sie **DATA** ein, und drücken Sie die EINGABETASTE. Sie erhalten die folgende oder eine ähnliche Antwort:
    
    ```powershell
    354 Start mail input; end with <CLRF>.<CLRF>
    ```

9.  Geben Sie **Betreff: Test von Contoso** ein, und drücken Sie die EINGABETASTE.

10. Drücken Sie die EINGABETASTE. RFC 2822 erfordert eine Leerzeile zwischen dem `Subject:`-Kopfzeilenfeld und dem Nachrichtentext.

11. Geben Sie **Dies ist eine Textnachricht.** ein, und drücken Sie dann die EINGABETASTE.

12. Drücken Sie die EINGABETASTE, geben Sie einen Punkt (**.**) ein, und drücken Sie dann die EINGABETASTE. Sie erhalten die folgende oder eine ähnliche Antwort:
    
    ```powershell
    250 2.6.0 <GUID> Queued mail for delivery
    ```

13. Um die Verbindung mit dem SMTP-Zielserver zu trennen, geben Sie **QUIT** ein, und drücken Sie dann die EINGABETASTE. Sie erhalten die folgende oder eine ähnliche Antwort:
    
    ```powershell
    221 2.0.0 Service closing transmission channel
    ```

14. Um Ihre Telnet-Sitzung zu schließen, geben Sie **quit** ein und drücken dann die EINGABETASTE.

## Schritt 4: Auswerten der Ergebnisse der Telnet-Sitzung

In diesem Abschnitt werden Informationen zu Antworten zur Verfügung gestellt, die auf die im vorigen Beispiel verwendeten Befehle gegeben werden können.

  - Öffnen von "mail1.fabrikam.com 25"

  - EHLO contoso.com

  - MAIL FROM:chris@contoso.com

  - RCPT TO:kate@fabrikam.com NOTIFY=success,failure
    

    > [!NOTE]
    > Die dreistelligen SMTP-Antwortcodes, die in RFC&nbsp;2821 definiert sind, sind für alle SMTP-Messagingserver gleich. Die Textbeschreibungen können für einige SMTP-Messagingserver geringfügig abweichen.



## Öffnen von "mail1.fabrikam.com 25"

**Erfolgreiche Antwort**   `220 mail1.fabrikam.com Microsoft ESMTP MAIL Service ready at <day-date-time>`

**Fehlerantwort**   `Connecting to mail1.fabrikam.com...Could not open connection to the host, on port 25: Connect failed`

**Mögliche Fehlerursachen**

  - Der SMTP-Zieldienst ist nicht verfügbar.

  - Für die Zielfirewall gelten Einschränkungen.

  - Für die Quellfirewall gelten Einschränkungen.

  - Es wurde ein falscher FQDN oder eine falsche IP-Adresse für den SMTP-Zielserver angegeben.

  - Es wurde eine falsche Portnummer angegeben.

## EHLO contoso.com

**Erfolgreiche Antwort**   `250 mail1.fabrikam.com Hello [<sourceIPaddress>]`

**Fehlerantwort**   `501 5.5.4 Invalid domain name`

**Mögliche Fehlerursachen**   Der Domänenname enthält ungültige Zeichen. Es können auch Verbindungseinschränkungen für den SMTP-Zielserver gelten.


> [!NOTE]
> EHLO ist das ESMTP-Verb (Extended Simple Message Transfer Protocol), das in RFC&nbsp;2821 definiert ist. ESMTP-Server können ihre Funktionen während der anfänglichen Verbindung ankündigen. Diese Funktionen umfassen ihre maximal akzeptierte Nachrichtengröße sowie die unterstützten Authentifizierungsmethoden. HELO ist das ältere SMTP-Verb, das in RFC&nbsp;821 definiert ist. Die meisten SMTP-Messagingserver unterstützen ESMTP und EHLO.



## MAIL FROM:chris@contoso.com

**Erfolgreiche Antwort**   `250 2.1.0 Sender OK`

**Fehlerantwort**   `550 5.1.7 Invalid address`

**Mögliche Fehlerursachen**   Die E-Mail-Adresse des Absenders enthält einen Syntaxfehler.

**Fehlerantwort**   `530 5.7.1 Client was not authenticated`

**Mögliche Fehlerursachen**   Der Zielserver akzeptiert keine anonymen Nachrichtenübermittlungen. Sie erhalten diesen Fehler, wenn Sie mit Telnet versuchen, eine Nachricht direkt an einen Hub-Transport-Server zu übermitteln.

## RCPT TO:kate@fabrikam.com NOTIFY=success,failure

**Erfolgreiche Antwort**   `250 2.1.5 Recipient OK`

**Fehlerantwort**   `550 5.1.1 User unknown`

**Mögliche Fehlerursachen**   Der angegebene Empfänger ist in der Organisation nicht vorhanden.

