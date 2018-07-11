---
title: 'Inhaltskonvertierung: Exchange 2013 Help'
TOCTitle: Inhaltskonvertierung
ms:assetid: bc367eb3-0306-4da9-9a84-4341caef77af
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232174(v=EXCHG.150)
ms:contentKeyID: 50476576
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Inhaltskonvertierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

*Inhaltskonvertierung* ist der Vorgang des richtigen Formatierens einer Nachricht für jeden Empfänger. Die Entscheidung, eine Inhaltskonvertierung für eine Nachricht durchzuführen, ist vom Ziel und Format der Nachricht abhängig, die verarbeitet wird. In Microsoft Exchange Server 2013 gibt es zwei verschiedene Arten der Inhaltskonvertierung:

  - **Nachrichtenkonvertierung für externe Empfänger**   Dieser Inhaltskonvertierungstyp schließt die TNEF-Konvertierungsoptionen (Transport Neutral Encapsulation Format) sowie Nachrichtencodierungsoptionen für externe Empfänger ein. Bei Nachrichten, die an Empfänger innerhalb der Exchange-Organisation gesendet werden, ist dieser Inhaltskonvertierungstyp nicht erforderlich. Dieser Inhaltskonvertierungstyp wird vom Kategorisierungsmodul im Transportdienst auf dem Postfachserver verarbeitet. Die Kategorisierung erfolgt für jede Nachricht, nachdem eine neu eingegangene Nachricht in die Übermittlungswarteschlange eingestellt wurde. Zusätzlich zur Empfänger- und Routingauflösung wird die Inhaltskonvertierung auf die Nachricht angewendet, bevor die Nachricht in eine Übermittlungswarteschlange eingestellt wird. Enthält eine einzelne Nachricht mehrere Empfänger, ermittelt das Kategorisierungsmodul die geeignete Codierung für jeden Nachrichtenempfänger. Die Ablaufverfolgung für die Inhaltskonvertierung erfasst keine Fehler der Inhaltskonvertierung, die beim Kategorisierungsmodul bei der Konvertierung von Nachrichten auftreten, die an externe Empfänger gesendet werden.

  - **MAPI-Konvertierung für interne Empfänger**   Dieser Inhaltskonvertierungstyp wird vom Postfachtransportdienst verarbeitet. Der Postfachtransportdienst befindet sich auf Postfachservern und dient zur Übermittlung von Nachrichten zwischen Postfachdatenbanken auf dem lokalen Server und dem Transportdienst auf Postfachservern. Genauer gesagt ist es der Postfachtransport-Übermittlungsdienst, der Nachrichten aus dem Postausgang des Absenders an den Transportdienst auf einem Postfachserver übermittelt. Der Postfachtransport-Zustellungsdienst übermittelt Nachrichten vom Transportdienst auf einem Postfachserver an den Posteingang des Empfängers. Der Postfachtransport-Übermittlungsdienst konvertiert alle ausgehenden Nachrichten aus MAPI, und der Postfachtransport-Zustellungsdienst konvertiert alle eingehenden Nachrichten nach MAPI. Die Ablaufverfolgung für die Inhaltskonvertierung erfasst MAPI-Konvertierungsfehler. Weitere Informationen finden Sie unter [Ablaufverfolgung für die Inhaltskonvertierung](content-conversion-tracing-exchange-2013-help.md).

In diesem Thema werden die Nachricht-Konvertierungsoptionen für externe Empfänger erläutert.

**Inhalt**

Exchange- und Outlook-Nachrichtenformate

Inhaltskonvertierungsoptionen für externe Empfänger

Grundlegendes zur Struktur von E-Mails

## Exchange- und Outlook-Nachrichtenformate

In der folgenden Liste werden die grundlegenden Nachrichtenformate beschrieben, die in Exchange und Outlook verfügbar sind:

  - **Nur-Text**   Eine Nur-Text-Nachricht verwendet ausschließlich US-ASCII-Text gemäß RFC 2822. Die Nachricht kann keine unterschiedlichen Schriftarten oder andere Textformatierungen enthalten. Folgende zwei Formate können für eine Nur-Text-Nachricht verwendet werden:
    
      - Die Nachrichtenkopfzeilen und der Nachrichtentext bestehen beide aus US-ASCII-Text. Anlagen müssen mithilfe von *Uuencode* codiert sein. Uuencode steht für Unix-to-Unix Encoding und definiert einen Codieralgorithmus zum Speichern von binären Anlagen im Text einer E-Mail unter Verwendung von US-ASCII-Textzeichen.
    
      - Die Nachricht wird mit dem **Content-Type**-Wert **text/plain** und dem **Content-Transfer-Encoding**-Wert **7bit** für die Textteile einer multipart-Nachricht (mehrteilig) MIME-codiert. Alle Nachrichtenanlagen werden mit Quoted-printable- oder Base64-Codierung codiert. Beim Erstellen und Senden einer Nur-Text-Nachricht in Outlook wird die Nachricht standardmäßig mit dem Content-Type-Wert "text/plain" MIME-codiert.

  - **HTML**   Eine HTML-Nachricht unterstützt Textformatierung, Hintergrundbilder, Tabellen, Aufzählungszeichen und andere grafische Elemente. Gemäß Definition muss eine HTML-formatierte Nachricht MIME-codiert sein, damit diese Formatierungselemente erhalten bleiben.

  - **Rich-Text**   RTF unterstützt die Textformatierung und andere grafische Elemente. RTF ist gleichbedeutend mit TNEF. TNEF und RTF können identisch verwendet werden. Das RTF-Nachrichtenformat unterscheidet sich grundlegend von dem in Microsoft Word verfügbaren RTF-Dokumentformat.
    
    Nur Outlook und einige wenige andere MAPI-E-Mail-Clients können RTF-Nachrichten auswerten.

  - **TNEF**   TNEF (Transport Neutral Encapsulation Format) ist ein Microsoft-spezifisches Format für das Kapseln von MAPI-Nachrichteneigenschaften. Eine TNEF-Nachricht enthält eine Nur-Text-Version der Nachricht sowie eine Anlage, die eine gepackte Version der formatierten Originalversion der Nachricht enthält. Üblicherweise trägt diese Anlage den Namen **Winmail.dat**. Die Anlage **Winmail.dat** enthält folgende Informationen:
    
      - Die formatierte Originalversion der Nachricht, wie z. B. Schriftarten, Textgrößen und Textfarben
    
      - OLE-Objekte, z. B. eingebettete Bilder oder eingebettete Microsoft Office-Dokumente
    
      - Spezielle Outlook-Funktionen, z. B. benutzerdefinierte Formulare, Abstimmungsschaltflächen oder Besprechungsanfragen
    
      - Reguläre Nachrichtenanlagen, die Bestandteil der Originalnachricht waren
    
    Die sich ergebende Nur-Text-Nachricht lässt sich in den folgenden Formaten darstellen:
    
      - Eine RFC 2822-kompatible Nachricht, bestehend ausschließlich aus US-ASCII-Text, mit einer mit Uuencode-codierten Anlage Winmail.dat
    
      - Eine MIME-codierte multipart-Nachricht (mehrteilig) mit einer Anlage Winmail.dat.
    
    Ein MAPI-kompatibler E-Mail-Client, der TNEF vollständig interpretieren kann, wie z. B. Outlook, verarbeitet die Anlage "Winmail.dat" und zeigt den ursprünglichen Nachrichteninhalt an, ohne je die Anlage "Winmail.dat" anzuzeigen. Ein E-Mail-Client, der TNEF nicht interpretieren kann, stellt eine TNEF-Nachricht möglicherweise auf eine der folgenden Arten dar:
    
      - Die Nur-Text-Version der Nachricht wird angezeigt, und die Nachricht enthält eine Anlage namens **Winmail.dat**, **Win.dat** oder mit einem anderen allgemeinen Namen wie **Att***nnnnn***.dat** oder **Att***nnnnn***.eml**, wobei der Platzhalter *nnnnn* eine Zufallszahl darstellt.
    
      - Die Nur-Text-Version der Nachricht wird angezeigt. Die TNEF-Anlage wird ignoriert oder entfernt. Das Ergebnis ist eine Nur-Text-Nachricht.
    
      - Messagingserver, die TNEF interpretieren können, können so konfiguriert werden, dass TNEF-Anlagen aus eingehenden Nachrichten entfernt werden. Das Ergebnis ist eine Nur-Text-Nachricht. Darüber hinaus können einige E-Mail-Clients wie Microsoft Outlook Express TNEF zwar möglicherweise nicht interpretieren, sind aber in der Lage, TNEF-Anlagen zu erkennen und zu ignorieren. Das Ergebnis ist eine Nur-Text-Nachricht.
    
    Es gibt Dienstprogramme von Drittanbietern, die bei der Konvertierung von **Winmail.dat**-Anlagen helfen können.
    
    TNEF wird von allen Versionen von Exchange seit Exchange Server, Version 5.5 interpretiert.

  - **Summary Transport Neutral Encapsulation Format (STNEF)**   STNEF ist äquivalent zu TNEF. STNEF-Nachrichten werden aber anders als TNEF-Nachrichten codiert. Insbesondere werden STNEF-Nachrichten immer MIME-codiert und haben immer einen **Content-Transfer-Encoding**-Wert von "Binary". Deshalb ist keine Nur-Text-Darstellung der Nachricht vorhanden, und im Text der Nachricht ist keine gesonderte Anlage **Winmail.dat** enthalten. Die gesamte Nachricht wird unter Verwendung von nur binären Daten dargestellt. Nachrichten, die den **Content-Transfer-Encoding**-Wert **Binary** aufweisen, können nur zwischen SMTP-Messagingservern übertragen werden, die die SMTP-Erweiterungen BINARYMIME und CHUNKING gemäß der Definition in RFC 3030 unterstützen und ankündigen. Die Nachrichten werden zwischen SMTP-Messagingservern immer unter Verwendung des BDAT-Befehls anstelle des Standardbefehls DATA übermittelt.
    
    STNEF wird von allen Versionen von Exchange seit Exchange 2000 interpretiert. STNEF wird automatisch für alle Nachrichten verwendet, die zwischen Exchange-Servern in der Organisation seit dem mit Exchange Server 2003 eingeführten einheitlichen Modus übertragen werden.
    
    Exchange sendet nie STNEF-Nachricht an externe Empfänger. Nur TNEF-Nachrichten können an Empfänger außerhalb der Exchange-Organisation gesendet werden.

Zurück zum Seitenanfang

## Inhaltskonvertierungsoptionen für externe Empfänger

Die Inhaltskonvertierungsoptionen, die in einer Exchange-Organisation für externe Empfänger festgelegt werden können, können in folgende Kategorien untergliedert werden:

  - **TNEF-Konvertierungsoptionen**   Diese Konvertierungsoptionen geben an, ob TNEF in Nachrichten, die die Exchange-Organisation verlassen, erhalten bleiben oder daraus entfernt werden soll.

  - **Nachrichtencodierungsoptionen**   Diese Optionen geben Nachrichtencodierungsoptionen an, wie z. B. MIME- oder Nicht-MIME-Zeichensätze, Nachrichtencodierung und Anlagenformate.

Diese Konvertierungs- und Codierungsoptionen sind voneinander unabhängig. So ist es beispielsweise für die MIME- oder Nur-Text-Codierungseinstellungen von Nachrichten ohne Belang, ob TNEF-Nachrichten die Exchange-Organisation verlassen dürfen.

Die Inhaltskonvertierung kann entsprechend der Beschreibung in der folgenden Liste auf unterschiedlichen Ebenen der Exchange-Organisation festgelegt werden:

  - **Remotedomäneneinstellungen**   Remotedomänen definieren die Einstellungen für Übertragungen von ausgehenden Nachrichten zwischen der Exchange-Organisation und externen Domänen. Auch wenn für bestimmte Domänen keine Remotedomäneneinträge erstellt werden, ist eine vordefinierte Remotedomäne namens **Standard** vorhanden, die auf alle Remoteadressräume (\*) angewendet wird.

  - **E-Mail-Benutzer- und E-Mail-Kontakteinstellungen**   E-Mail-Benutzer sind mit E-Mail-Kontakten vergleichbar – beide besitzen externe E-Mail-Adressen und enthalten Informationen über Personen außerhalb der Exchange-Organisation. Der Hauptunterschied besteht darin, dass E-Mail-Benutzer über Konten verfügen, mit denen sie sich bei der Active Directory-Domäne anmelden und auf Ressourcen in der Organisation zugreifen können.

  - **Outlook-Einstellungen**   In Outlook können Sie die in der folgenden Liste beschriebenen Nachrichtenformatierungs- und -codierungsoptionen festlegen:
    
      - **Nachrichtenformat**   Sie können das Standardnachrichtenformat für alle Nachrichten festlegen. Das Standardnachrichtenformat kann darüber hinaus beim Erstellen einer bestimmten Nachricht außer Kraft gesetzt werden.
    
      - **Internet-Nachrichtenformat**   Sie können steuern, ob TNEF-Nachrichten direkt an Remoteempfänger gesendet werden, oder ob sie zuerst in ein besser kompatibles Format konvertiert werden. Sie können außerdem verschiedene Nachrichtencodierungsoptionen für Nachrichten angeben, die an Remoteempfänger gesendet werden. Diese Einstellungen gelten nicht für Nachrichten, die an Empfänger in der Exchange-Organisation gesendet werden.
    
      - **Nachrichtenformat für Internet-Empfänger**   Sie können steuern, ob TNEF-Nachrichten direkt an bestimmte Empfänger gesendet werden, oder ob sie zuerst in ein besser kompatibles Format konvertiert werden. Die Konvertierungsoptionen können für bestimmte Kontakte im Ordner **Kontakte** festgelegt werden. Beim Erstellen einer Nachricht können Sie diese Konvertierungsoptionen dann für einen bestimmten Empfänger in den Feldern **An**, **Cc** oder **Bcc** außer Kraft setzen. Diese Konvertierungsoptionen sind für Empfänger innerhalb der Exchange-Organisation nicht verfügbar.
    
      - **Nachrichtencodierungsoptionen für Internet-Empfänger**   Sie können die MIME- oder Nur-Text-Codierungsoptionen für bestimmte Kontakte im Ordner **Kontakte** steuern. Beim Erstellen einer Nachricht können Sie die Konvertierungsoptionen dann für einen bestimmten Empfänger in den Feldern **An**, **Cc** oder **Bcc** außer Kraft setzen. Diese Konvertierungsoptionen sind für Empfänger innerhalb der Exchange-Organisation nicht verfügbar.
    
      - **Internationale Optionen**   Sie können die in Nachrichten verwendeten Zeichensätze steuern.

## TNEF-Konvertierungsoptionen

Sie können die TNEF-Konvertierungsoptionen auf folgenden Ebenen angeben:

  - Remotedomäneneinstellungen

  - E-Mail-Benutzer- und E-Mail-Kontakteinstellungen

  - Outlook-Einstellungen, einschließlich:
    
      - Nachrichtenformat
    
      - Internet-Nachrichtenformat
    
      - Nachrichtenformat für Internetempfänger

## Nachrichtencodierungsoptionen

Sie können die Nachrichtencodierungsoptionen auf folgenden Ebenen angeben:

  - Remotedomäneneinstellungen

  - E-Mail-Benutzer- und E-Mail-Kontakteinstellungen

  - Outlook-Einstellungen, einschließlich:
    
      - Nachrichtenformat
    
      - Internetnachricht
    
      - Nachrichtenformat für Internetempfänger
    
      - Nachrichtenzeichensatz-Codierungsoptionen

Ausführliche Informationen finden Sie unter [Nachrichtencodierungsoptionen](message-encoding-options-exchange-2013-help.md).

Zurück zum Seitenanfang

## Grundlegendes zur Struktur von E-Mails

Um die Inhaltskonvertierungsoptionen für externe Empfänger besser verstehen zu können, müssen Sie sich mit der Struktur von E-Mails vertraut machen. Die Grundlage einer SMTP-Nachricht bei der Erstellung und beim Senden von E-Mails bildet unformatierter 7-Bit-US-ASCII-Text. Eine SMTP-Standardnachricht besteht aus folgenden Elementen:

  - **Nachrichtenumschlag**   Der Nachrichtenumschlag ist in RFC 2821 definiert. Er enthält Informationen, die für die Übertragung und Zustellung der Nachricht erforderlich sind. Empfänger bekommen den Nachrichtenumschlag nicht angezeigt, da er vom Nachrichtenübermittlungsprozess generiert wird und nicht tatsächlicher Bestandteil des Nachrichteninhalts ist.

  - **Nachrichteninhalt**   Der Nachrichteninhalt ist in RFC 2822 definiert. Er besteht aus folgenden Elementen:
    
      - **Nachrichtenkopf**   Der Nachrichtenkopf ist eine Sammlung von Kopffeldern. Kopffelder bestehen aus einem Feldnamen, auf den ein Doppelpunkt (:) und dann ein Feldtext folgt. Abgeschlossen werden diese Felder durch eine Kombination aus Wagenrücklauf- und Zeilenvorschubzeichen (Carriage Return/Line Feed, CR/LF).
        
        Ein Feldname muss aus druckbaren US-ASCII-Textzeichen bestehen, mit Ausnahme des Doppelpunkts (:). Insbesondere ASCII-Zeichen mit Werten von 33 bis 57 sowie 59 bis 126 sind zulässig.
        
        Ein Feldtext kann aus beliebigen US-ASCII-Zeichen bestehen, mit Ausnahme des Wagenrücklaufzeichens (CR) und des Zeilenvorschubzeichens (LF). Ein Feldtext darf jedoch die Zeichenkombination CR/LF enthalten, wenn sie beim *Kopfzeilenumbruch* verwendet wird. Unter Kopfzeilenumbruch versteht man das Verteilen eines einzelnen Kopfzeilenfeldtexts auf mehrere Zeilen; eine Beschreibung des Verfahrens finden Sie in Abschnitt 2.2.3 von RFC 2822. Andere Anforderungen an die Feldtextsyntax werden in den Abschnitten 3 und 4 von RFC 2822 beschrieben.
    
      - **Nachrichtentext**   Der Nachrichtentext ist eine Sammlung von Zeilen aus US-ASCII-Textzeichen, die auf den Nachrichtenkopf folgen. Der Nachrichtenkopf und der Nachrichtentext sind durch eine Leerzeile getrennt, die durch die CR/LF-Zeichenkombination abgeschlossen wird. Der Nachrichtentext ist optional. Keine Textzeile im Nachrichtentext darf länger als 997 Zeichen sein. CR- und LF-Zeichen können nur zusammen verwendet werden, um das Ende einer Zeile anzuzeigen.

Wenn SMTP-Nachrichten Elemente enthalten, bei denen es sich nicht um unformatierten US-ASCII-Text handelt, muss die Nachricht codiert werden, um diese Elemente zu erhalten. Der MIME-Standard definiert eine Methode zum Codieren von Inhalten in Nachrichten, bei denen es sich nicht um Text handelt. MIME ermöglicht die Verwendung von Text in anderen Zeichensätzen, Anlagen ohne Text, mehrteiligen Nachrichtentexten und Kopffeldern in anderen Zeichensätzen. MIME ist in RFC 2045, RFC 2046, RFC 2047, RFC 2048 und RFC 2077 definiert. MIME definiert eine Sammlung von Kopffeldern, die zusätzliche Nachrichtenattribute angeben. In der folgenden Tabelle werden einige wichtige MIME-Kopfzeilenfelder beschrieben.

### Wichtige MIME-Kopfzeilenfelder

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Kopfzeilenfelds</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MIME-Version</p></td>
<td><p>1.0</p></td>
<td><p>Dieses Kopfzeilenfeld ist das erste MIME-Kopfzeilenfeld, das in einer Nachricht im MIME-Format vorkommt. Es folgt auf die anderen Standardkopfzeilenfelder gemäß RFC 2822, steht aber vor allen anderen MIME-Kopfzeilenfeldern. MIME-aktivierte E-Mail-Clients identifizieren anhand dieser Kopfzeilenfelder MIME-codierte Nachrichten. Fehlt dieses Kopfzeilenfeld, identifizieren MIME-aktivierte E-Mail-Clients die Nachricht als unformatierten Text.</p></td>
</tr>
<tr class="even">
<td><p>Content-Type</p></td>
<td><p>text/plain</p></td>
<td><p>Dieses Kopffeld identifiziert den Medientyp des Nachrichteninhalts, wie in RFC 2046 beschrieben. Ein Medientyp besteht aus einem Typ, einem Untertyp und mindestens einem optionalen Parameter, wie z. B. einem <em>charset=</em>-Parameter, der die MIME-Zeichencodierung definiert. Typen, die mit &quot;x-&quot; beginnen, sind keine Standardtypen. Untertypen, die mit &quot;vnd.&quot; beginnen, sind herstellerspezifisch. Die IANA (Internet Assigned Numbers Authority) pflegt eine Liste der registrierten Medientypen. Weitere Informationen finden Sie unter <a href="https://www.iana.org/assignments/media-types/">MIME Media Types</a>.</p>
<p>Der Medientyp <em>multipart</em> ermöglicht die Verwendung mehrerer Nachrichtenteile in derselben Nachricht, indem durch verschiedene Medientypen definierte Abschnitte verwendet werden. Mögliche Werte des Content-Type-Felds sind unter anderem <strong>text/plain</strong>, <strong>text/html</strong>, <strong>multipart/mixed</strong> und <strong>multipart/alternative</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Content-Transfer-Encoding</p></td>
<td><p>7bit</p></td>
<td><p>Dieses Kopfzeilenfeld kann folgende Informationen zu einer Nachricht beschreiben:</p>
<ul>
<li><p>Den Codieralgorithmus, mit dem alle im Nachrichtentext vorhandenen Nicht-US-ASCII-Text- oder Binärdaten transformiert werden.</p></li>
<li><p>Einen Indikator, der den aktuellen Zustand des Nachrichtentexts beschreibt.</p></li>
</ul>
<p>Eine MIME-Nachricht kann mehrere Werte des Kopffelds <strong>Content-Transfer-Encoding</strong> enthalten. Wenn das Kopffeld <strong>Content-Transfer-Encoding</strong> im Nachrichtenkopf vorkommt, gilt es für den gesamten Text der Nachricht. Wenn das Kopffeld <strong>Content-Transfer-Encoding</strong> in einem der Teile einer multipart-Nachricht (mehrteilig) vorkommt, gilt es nur für diesen Teil der Nachricht.</p>
<p>Bei Anwendung eines Codieralgorithmus auf die Nachrichtentextdaten werden diese in unformatierten US-ASCII-Text transformiert. Diese Transformation ermöglicht die Umleitung der Nachricht über ältere SMTP-Messagingservers, die nur Nachrichten in US-ASCII-Text unterstützen. Die Werte des Kopffelds <strong>Content-Transfer-Encoding</strong>, die anzeigen, dass ein Codieralgorithmus auf den Nachrichtentext angewendet wurde, sind folgende:</p>
<ul>
<li><p><strong>Quoted-printable</strong>   Dieser Codieralgorithmus verwendet druckbare US-ASCII-Zeichen zur Codierung der Nachrichtentextdaten. Besteht der ursprüngliche Nachrichtentext hauptsächlich aus US-ASCII-Text, erzeugt die Quoted-printable-Codierung relativ lesbare und kompakte Ergebnisse. Alle druckbaren US-ASCII-Textzeichen, mit Ausnahme des Gleichheitszeichens (=), können ohne Codierung dargestellt werden.</p></li>
<li><p><strong>Base64</strong>   Dieser Codieralgorithmus basiert in erster Linie auf dem PEM-Standard (Privacy-Enhanced Mail), der in RFC 1421 definiert ist. Die Base64-Codierung verwendet den 64-Zeichenalphabet-Codieralgorithmus sowie in PEM definierte Zeichen zum Auffüllen der Ausgabe, um die Nachrichtentextdaten zu codieren. Eine Base64-codierte Nachricht ist üblicherweise 33 % größer als die Ursprungsnachricht. Die Base64-Codierung erzeugt einen vorhersagbaren Zuwachs der Nachrichtengröße und eignet sich optimal für Binärdaten und Nicht-US-ASCII-Text.</p></li>
</ul>
<p>Normalerweise trifft man nur sehr selten innerhalb einer Nachricht auf verschiedene Codieralgorithmen.</p>
<p>Wenn kein Codieralgorithmus auf den Nachrichtentext angewendet wurde, zeig das Kopffeld <strong>Content-Transfer-Encoding</strong> nur den aktuellen Zustand der Nachrichtentextdaten an. Folgende Werte des Kopffelds <strong>Content-Transfer-Encoding</strong> zeigen an, dass kein Codieralgorithmus auf den Nachrichtentext angewendet wurde:</p>
<ul>
<li><p><strong>7bit</strong>   Dieser Wert zeigt an, dass die Nachrichtentextdaten bereits im RFC 2822-Format vorliegen. Hierbei müssen insbesondere die folgenden Bedingungen erfüllt sein:</p>
<ul>
<li><p>Keine Textzeile darf länger als 997 Zeichen sein.</p></li>
<li><p>Alle Zeichen müssen als US-ASCII-Text mit Zeichenwerten von 1 bis 127 vorliegen.</p></li>
<li><p>CR- und LF-Zeichen können nur zusammen verwendet werden, um das Ende einer Textzeile anzuzeigen.</p></li>
</ul>
<p>Der gesamte Nachrichtentext oder ein Teil des Nachrichtentexts bei einer multipart-Nachricht (mehrteilig) kann 7bit sein. Enthält die multipart-Nachricht andere Teile mit Binärdaten oder Nicht-US-ASCII-Text, müssen diese Teile der Nachricht mit einem der Algorithmen &quot;Quoted-printable&quot; oder &quot;Base64&quot; codiert sein.</p>
<p>Nachrichten mit 7bit-Texten können mithilfe des DATA-Standardbefehls zwischen SMTP-Messagingservern übermittelt werden.</p></li>
<li><p><strong>8bit</strong>   Dieser Wert zeigt an, dass die Nachrichtentextdaten Nicht-US-ASCII-Zeichen enthalten. Hierbei müssen insbesondere die folgenden Bedingungen erfüllt sein:</p>
<ul>
<li><p>Keine Textzeile darf länger als 998 Zeichen sein.</p></li>
<li><p>Mindestens ein Zeichen im Nachrichtentext hat einen Wert größer als 127.</p></li>
<li><p>Die Zeichen CR und LF können nur zusammen verwendet werden, um das Ende einer Textzeile anzuzeigen.</p></li>
</ul>
<p>Der gesamte Nachrichtentext oder ein Teil des Nachrichtentexts bei einer multipart-Nachricht (mehrteilig) kann &quot;8bit&quot; sein. Enthält die multipart-Nachricht andere Teile mit Binärdaten, müssen diese Teile der Nachricht mit einem der Algorithmen &quot;Quoted-printable&quot; oder &quot;Base64&quot; codiert sein.</p>
<p>Nachrichten mit 8bit-Texten können nur zwischen SMTP-Messagingservern übermittelt werden, die die 8BITMIME-SMTP-Erweiterung gemäß Definition in RFC 1652 unterstützen, z. B. Exchange 2000 Server oder neuere Versionen. Hierbei müssen insbesondere die folgenden Bedingungen erfüllt sein:</p>
<ul>
<li><p>Das 8BITMIME-Schlüsselwort muss in der EHLO-Antwort des Servers angekündigt werden.</p></li>
<li><p>Nachrichten werden weiterhin unter Verwendung des SMTP-Standardbefehls DATA übermittelt. Der Parameter <strong>BODY=8BITMIME</strong> muss aber am Ende des MAIL FROM-Befehls hinzugefügt werden.</p></li>
</ul></li>
<li><p><strong>Binary</strong>   Dieser Wert zeigt an, dass der Nachrichtentext Nicht-US-ASCII-Zeichen oder Binärdaten enthält. Dies heißt insbesondere, dass die folgenden Bedingungen erfüllt sind:</p>
<ul>
<li><p>Jede Zeichenfolge ist zulässig.</p></li>
<li><p>Es besteht keine Einschränkung der Zeilenlänge.</p></li>
<li><p>Binärnachrichtenelemente erfordern keine Codierung.</p></li>
</ul>
<p>Nachrichten mit Binärtexten können nur zwischen SMTP-Messagingservern übermittelt werden, die die BINARYMIME-SMTP-Erweiterung gemäß Definition in RFC 3030 unterstützen, z. B. Exchange 2000 Server oder neuere Versionen. Hierbei müssen insbesondere die folgenden Bedingungen erfüllt sein:</p>
<ul>
<li><p>Das BINARYMIME-Schlüsselwort muss in der EHLO-Antwort des Servers angekündigt werden.</p></li>
<li><p>Die SMTP-Erweiterung BINARYMIME kann nur zusammen mit der SMTP-Erweiterung CHUNKING verwendet werden. <em>Chunking</em> ermöglicht das Senden von großen Nachrichtentexten in mehreren kleineren Teilstücken (&quot;chunks&quot;). Chunking ist ebenfalls in RFC 3030 definiert. Das CHUNKING-Schlüsselwort muss ebenfalls in der EHLO-Antwort des Servers angekündigt werden.</p></li>
<li><p>Nachrichten werden unter Verwendung des BDAT-Befehls anstelle des Standardbefehls DATA übermittelt.</p></li>
<li><p>Wenn die Nachricht über einen Nachrichtentext verfügt, muss der Parameter <em>BODY=BINARYMIME</em> am Ende des MAIL FROM-Befehls hinzugefügt werden.</p></li>
</ul></li>
</ul>
<p>Die Werte &quot;7bit&quot;, &quot;8bit&quot; und &quot;Binary&quot; können nie gleichzeitig in derselben multipart-Nachricht vorkommen. Die Werte schließen sich gegenseitig aus. Die Werte &quot;Quoted-printable&quot; oder &quot;Base64&quot; können in einem 7bit- oder 8bit-multipart-Nachrichtentext (mehrteilig) vorkommen, aber nie in einem Binary-Nachrichtentext. Wenn ein multipart-Nachrichtentext (mehrteilig) verschiedene Teile enthält, die aus 7bit- und 8bit-Inhalten bestehen, wird die gesamte Nachricht als <strong>8bit</strong> klassifiziert. Wenn ein multipart-Nachrichtentext (mehrteilig) verschiedene Teile enthält, die aus 7bit-, 8bit- und Binary-Inhalten bestehen, wird die gesamte Nachricht als &quot;Binary&quot; klassifiziert.</p></td>
</tr>
<tr class="even">
<td><p>Content-Disposition</p></td>
<td><p>Attachment</p></td>
<td><p>Dieses Kopfzeilenfeld, das in RFC 2183 beschrieben ist, teilt einem MIME-aktivierten E-Mail-Client mit, wie eine angefügte Datei angezeigt werden soll. Die Werte dieses Felds können &quot;Inline&quot; oder &quot;Attachment&quot; sein. Wenn der Wert dieses Felds &quot;Inline&quot; ist, wird die Anlage innerhalb des Nachrichtentexts angezeigt. Ist der Wert dieses Felds <strong>Attachment</strong>, wird die angefügte Datei als reguläre Anlage vom Nachrichtentext getrennt angezeigt. Wenn der Wert &quot;Attachment&quot; ist, sind noch andere Parameter verfügbar, wie z. B. &quot;Filename&quot;, &quot;Creation-date&quot; und &quot;Size&quot;.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

