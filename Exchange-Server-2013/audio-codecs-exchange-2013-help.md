---
title: 'Audiocodecs: Exchange 2013 Help'
TOCTitle: Audiocodecs
ms:assetid: 6c39d65c-c2d3-4128-aae9-8596602819c3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998670(v=EXCHG.150)
ms:contentKeyID: 54652691
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Audiocodecs

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Unified Messaging (UM) wird ein Audiocodec zum Speichern von Voicemailnachrichten verwendet. Ein weiterer Codec wird zwischen einem VoIP-Gateway oder einer IP-Festnetztelefonanlage (IP Private Branch eXchange) und dem Postfachserver, der den Microsoft Exchange Unified Messaging-Dienst ausführt, beziehungsweise dem Clientzugriffsserver, der den Microsoft Exchange Unified Messaging Call Router-Dienst ausführt, verwendet. Unified Messaging kann Sprachnachrichten mithilfe der folgenden vier Audiocodecs erstellen und speichern:

  - MP3 (Standardeinstellung)

  - Windows Media Audio (WMA)

  - Group System Mobile (GSM) 06.10

  - G.711 Pulse Code Modulation (PCM) Linear


> [!WARNING]
> Die VoIP-Codecs G.711 (PCMA und PCMU) und G.723.1 werden zwischen einem VoIP-Gateway und den Clientzugriffs- und Postfachservern eingesetzt.



Ein Teil der Planung Ihres Unified Messaging-Systems besteht in der Auswahl des Audiocodecs, der für die Anforderungen Ihres Unternehmens geeignet ist. In diesem Thema werden die Audiocodecs beschrieben, die von Unified Messaging verwendet werden können. Außerdem finden Sie hier Hilfe zur Planung Ihrer UM-Bereitstellung.

## Codecs

Der Ausdruck *Codec* ist eine Kombination aus "Coding" (Codieren) und "Decoding" (Decodieren) und bezieht sich auf digitale Audiodaten. Ein Codec ist ein Programm zum Transformieren von digitalen Daten in ein Audiodatei- oder Audiostreamingformat. Codecs werden zum Konvertieren eines analogen Sprachsignals in eine digitale Version des Sprachsignals verwendet. Codecs können hinsichtlich der Soundqualität, der für ihre Nutzung erforderlichen Bandbreite und den Systemanforderungen, die für die Verschlüsselung benötigt werden, unterschiedlich sein.

In Unified Messaging werden zwei Typen von Codecs verwendet:

  - Der Codec wird zwischen einem VoIP-Gateway, einer IP-Festnetztelefonanlage oder einer SIP-aktivierten PBX-Anlage und den Clientzugriffs- und Postfachservern bzw. zwischen einer PBX-Anlage und einem VoIP-Gateway eingesetzt.

  - Mit dem Codec werden Sprachnachrichten für Benutzer codiert und gespeichert.

Beim Telefonieren mit einem gewöhnlichen Telefon über das herkömmliche öffentliche Telefonnetz wird das Sprachsignal in einem analogen Format über die Telefonleitung übertragen. Mit Voice over IP (VoIP) muss das Sprachsignal in digitale Signale umgewandelt werden. Dieser Umwandlungsprozess wird als Verschlüsselung bezeichnet. Die Verschlüsselung erfolgt über einen Codec. Nachdem das digitalisierte Sprachsignal sein Ziel erreicht hat, muss es wieder in das ursprüngliche analoge Format umgewandelt werden, damit die Person am anderen Ende der Leitung den Anrufer hören und verstehen kann.

## VoIP-Codec

In UM können drei unterschiedliche Codectypen zwischen VoIP-Gateways oder IP-Festnetztelefonanlage und den Clientzugriffs- und Postfachservern eingesetzt werden.

  - G.711 µ-law

  - G.711 A-law

  - G.723.1

G.711 ist ein Standard, der für den Einsatz mit Audiocodecs entwickelt wurde. Im Standard G.711 sind zwei Haupt-Algorithmen definiert: Der Algorithmus µ-law wird in Nordamerika und Japan verwendet, der Algorithmus A-law dagegen in Europa und anderen Ländern. Der G.723.1-Audiocodec wird hauptsächlich in VoIP-Anwendungen eingesetzt und erfordert eine entsprechende Lizenz. G.723.1 ist ein Codectyp für hohe Qualität bei hoher Komprimierung.

Ein Clientzugriffs- oder Postfachserver und ein unterstütztes VoIP-Gateway oder eine IP-Festnetztelefonanlage können den G.711- und den G.7230.1-Codec anbieten. Standardmäßig wird als primärer Codec G.723.1 verwendet. Wenn Sie zwischen den Clientzugriffs- und Postfachservern und dem VoIP-Gateway oder der IP-Festnetztelefonanlage einen anderen Codec als G.723.1 verwenden möchten, empfiehlt es sich, die Konfiguration des VoIP-Gateways oder der IP-Festnetztelefonanlage zu ändern. In der folgenden Tabelle werden einige allgemeine VoIP-Codecs zusammengefasst.

### VoIP-Codec

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>VoIP-Codec</th>
<th>Bandbreite (Kbit/s)</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>G.711</p></td>
<td><p>64</p></td>
<td><p>Dieser Codec erfordert eine sehr geringe Prozessorleistung. Er benötigt mindestens 128 KBits/s für die bidirektionale Kommunikation.</p></td>
</tr>
<tr class="even">
<td><p>G.723.1</p></td>
<td><p>5.3/6.3</p></td>
<td><p>Dieser Codec bietet hohe Komprimierung bei hoher Audioqualität. Er erfordert eine höhere Prozessorleistung als der G.711-Codec. Der G.723.1-Codec benötigt, allerdings zu Lasten der Audioqualität, eine geringere Bandbreite.</p></td>
</tr>
</tbody>
</table>


## Codec für UM-Sprachnachrichtenspeicher

Unified Messaging-Wähleinstellungen sind integraler Bestandteil des Unified Messaging-Betriebs. Beim Erstellen von UM-Wähleinstellungen wird standardmäßig der MP3-Audiocodec verwendet, um Sprachnachrichten zu erstellen und zu speichern. Nachdem Sie die UM-Wähleinstellungen erstellt haben, können Sie diese jedoch so konfigurieren, dass sie WMA, GSM 06.10- oder G.711 PCM Linear-Audiocodecs verwenden.

Jeder Audiocodec hat Vor- und Nachteile. Der MP3-Audiocodec wurde aufgrund seiner Soundqualität und Komprimiereigenschaften als Standardaudiocodec ausgewählt. Die GSM 06.10- und G.711 PCM Linear-Audiocodecs wurden aufgrund ihrer Fähigkeit, andere Messagingsystemtypen zu unterstützen, als Optionen aufgenommen.

Bei der Planung von Unified Messaging sind die Größe und relative Qualität der Audiodatei für Sprachnachrichten zu berücksichtigen. Generell gilt der Grundsatz, je höher die Bitrate einer Audiodatei, desto höher die Qualität. Außerdem ist zu überlegen, ob die Audiodatei komprimiert werden soll. In der folgenden Tabelle sind Bitrate (bit/s) sowie Komprimierungseigenschaften der einzelnen in UM verwendeten Codecs aufgeführt.

### Standardcodecs für UM-Sprachnachrichtenspeicher

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Codec für Sprachnachrichtenspeicher</th>
<th>Bit</th>
<th>Komprimierte Datei?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MP3</p></td>
<td><p>16 Bit</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>WMA</p></td>
<td><p>16 Bit</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>G.711 PCM</p></td>
<td><p>16 Bit</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>GSM 06.10</p></td>
<td><p>8 Bit</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


In UM hängt der für eine Sprachnachricht erstellte Dateityp vom Audiocodec ab, der zum Erstellen der Sprachnachricht-Audiodatei verwendet wurde. Der MP3-Audiocodec erstellt MP3-Audiodateien, der WMA-Audiocodec erstellt .WMA-Audiodateien und die GSM 06.10- und G.711 PCM Linear-Audiocodecs erstellen .WAV-Audiodateien. Diese Typen von Audiodateien werden zusammen mit der E-Mail-Nachricht an den Empfänger der Sprachnachricht gesendet.

Das Codieren und Decodieren von digitalen Daten beinhaltet häufig, allerdings nicht immer, eine Komprimierung oder Dekomprimierung. Die Audiokomprimierung ist eine Form der Datenkomprimierung, bei der die Größe von Audiodateien reduziert wird. Der vom Audiocodec benutzte Audiokomprimierungsalgorithmus komprimiert WMA- oder WAV-Audiodateien. In Unified Messaging hängt der verwendete Audiokomprimierungsalgorithmus von dem Audiocodectyp ab, der in den UM-Wähleinstellungseigenschaften ausgewählt wird. Nachdem die Audiodatei erstellt und komprimiert wurde, wird sie der Sprachnachricht als Anlage hinzugefügt.

Manchmal gehen bei der Komprimierung und Dekomprimierung Informationen der digitalen Daten verloren. Je höher der für die Audiodatei gewählte Komprimierungsgrad, desto größer der Verlust an Informationen während der Konvertierung. Es wird jedoch weniger Speicherplatz verwendet, da die Größe der Audiodatei verringert wird. Umgekehrt gilt, je niedriger der Komprimierungsgrad, desto geringer der Verlust an Informationen. Aufgrund der Größe der einzelnen Audiodateien wird jedoch mehr Speicherplatz benötigt.

RTAudio-Breitband bzw. HiFi-Audio zum Aufzeichnen von Sprachnachrichten wird ebenfalls als Audiocodec unterstützt. HiFi-Audio mit RTAudio ist aber erst verfügbar, nachdem Sie Unified Messaging mit [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=202010) integriert haben. Zur Aktivierung von RTAudio als Übermittlungscodec entweder im Schmal- oder Breitbandmodus müssen die UM-Wähleinstellungen als SIP-URI-Typ (Session Initiation-Protokoll) konfiguriert und der Mailboxansagecodec in den Wähleinstellungen auf MP3 oder WMA festgelegt werden, um Breitbandaudio (16 kHz) zu ermöglichen.


> [!IMPORTANT]
> RTAudio steht in Umgebungen ohne Lync Server nicht zur Verfügung. Das liegt daran, dass der Wählplan in Umgebungen ohne integrierten Lync Server für Telefondurchwahlnummer oder E.164 und nicht für SIP URI konfiguriert wird.



Für jeden eingehenden Anruf gibt es zwei Medienstreams: eingehend an einen Clientzugriffsserver und ausgehend von einem Postfachserver. Wenn der Wähleinstellungstyp auf SIP URI und der Mailboxansagecodec in den Wähleinstellungen auf MP3 oder WMA gesetzt ist, wählt ein Clientzugriffsserver den RTAudio-VoIP-Codec für den eingehenden Medienstream aus. Bei erfolgreicher Aushandlung wird der RTAudio-Codec des eingehenden Streams für die Mailboxansage oder für Anrufe verwendet, die aus einem Lync-Client oder -Server stammen.


> [!NOTE]
> Anrufe, die mithilfe der Funktion "Wiedergabe über Telefon" abgesetzt werden, verwenden den RTAudio-Codec nicht. Der eingehende Stream für Anrufe, die mithilfe dieser Funktion abgesetzt werden, verwendet den G.711- oder G.723.1-Codec.



Bei Verwendung des RTAudio-Codecs wird die jeweilige Sprachnachricht in HiFi-Qualität aufgezeichnet und als Audiodatei mit einer .MP3- oder .WMA-Erweiterung, je nach Konfiguration des Wählplans, gespeichert. Die Wiedergabe dieser Sprachnachricht für den Benutzer erfolgt in Outlook oder Outlook Web App in HiFi-Audioqualität. Bei erfolgreicher Aushandlung wird entweder der G.711- oder der G.723.1-Codec verwendet. Sowohl beim G.711- als auch beim G.723.1-Codec handelt es sich um schmalbandige Codecs. Wenn diese als VoIP-Codecs verwendet werden, wird die Sprachnachricht als schmalbandige Audiodatei mit einer .MP3- oder .WMA-Erweiterung aufgezeichnet und gespeichert.

Der ausgehende Medienstrom wird immer unter Verwendung des G.711- oder des G.723.1-Codecs ausgehandelt. Anrufer hören daher immer eine schmalbandige Wiedergabe über das Telefon. Dies gilt auch für Szenarien, in denen ein Anruf mit Microsoft Lync Server 2010 oder höher getätigt wird.

Das von den Postfachservern zum Speichern der Audiodaten in Sprachnachrichten verwendete Audioformat und der Audiocodec hängen nicht nur vom Audiocodec ab, der für die Wähleinstellungen konfiguriert ist, sondern auch von der Bitrate der Audiodaten, die vom UM mit einem SIP-Peer ausgehandelt werden. Falls Sie in Ihrer Umgebung Lync Server- oder SIP-Endpunkte integriert haben, verhandelt der Postfachserver auch den Audiocodec, der mit SIP-Peers verwendet wird. Wenn z. B. Breitband-RTAudio als Übermittlungscodec ausgehandelt wird, verwendet ein Postfachserver in Abhängigkeit von den Wähleinstellungen entweder das MP3- oder WMA 9.2-Format (32 KBit/s) zum Erstellen von Sprachnachrichten. In der folgenden Tabelle wird die Beziehung zwischen dem zum Speichern der Sprachnachrichten verwendeten Audiocodec und dem für VoIP oder Übermittlungen verwendeten Audiocodec veranschaulicht.

### Beziehung zwischen Speicheraudiocodec und VoIP- oder Übermittlungsaudiocodec

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>In UM-Wähleinstellungen konfigurierter Audiocodec</th>
<th>VoIP- oder Übermittlungscodec (Schmalband) – G.723, G.711 oder RTAudio (8 kHz)</th>
<th>VoIP- oder Übermittlungscodec (Breitband) – RTAudio (16 kHz)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>G.711</p></td>
<td><p>G.711</p></td>
<td><p>Nicht zutreffend. Die Breitbandaudiodaten werden nicht von einem Clientzugriffs- oder Postfachserver ausgehandelt, wenn G.711 für die Wähleinstellungen festgelegt ist.</p></td>
</tr>
<tr class="even">
<td><p>WMA</p></td>
<td><p>WMA 9-Voice</p></td>
<td><p>WMA 9.2</p></td>
</tr>
<tr class="odd">
<td><p>GSM</p></td>
<td><p>GSM 6.10</p></td>
<td><p>Nicht zutreffend. Die Breitbandaudiodaten werden nicht von einem Clientzugriffs- oder Postfachserver ausgehandelt, wenn GSM für die Wähleinstellungen festgelegt ist.</p></td>
</tr>
<tr class="even">
<td><p>MP3</p></td>
<td><p>MP3 (16 KBit/s)</p></td>
<td><p>MP3 (32 KBit/s)</p></td>
</tr>
</tbody>
</table>


Codecs

## UM-Nachrichtengröße

Sie können Unified Messaging so konfigurieren, dass einer der vier folgenden Audiocodecs zum Erstellen von Sprachnachrichten verwendet wird: MP3, WMA, GSM 06.10 oder G.711 PCM Linear. Standardmäßig ist das MP3-Format ausgewählt.

Der WMA-Audiocodec wird immer im Windows Media-Format gespeichert. Die Anlage ist eine Datei mit der Erweiterung "WMA". Mit den GSM- oder G.711 PCM Linear-Audiocodecs codierte Audiodateien werden immer im RIFF/WAV-Format gespeichert. Die Anlage ist eine Datei mit der Erweiterung "WAV".

Die Größe der Unified Messaging-Sprachnachrichten hängt von der Größe der Anlage ab, die die Sprachdaten enthält. Umgekehrt ist die Größe der Anlage von folgenden Faktoren abhängig:

  - Dauer der Voicemailaufzeichnung

  - Verwendeter Audiocodec

  - Speicherformat der Audiodatei

In der folgenden Abbildung wird gezeigt, wie bei den drei in UM verwendbaren Audiocodecs die Größe der Audiodatei von der Dauer der Voicemailaufzeichnung abhängt.


> [!NOTE]
> In dieser Abbildung beträgt die durchschnittliche Länge einer als Anrufannahme verwendeten Sprachnachricht ca. 30&nbsp;Sekunden.



**Größe der Audiodatei**

![UM\_Message\_Sizing](images/Aa998670.76ca4891-450f-4ffd-9493-aac8d0d23a5d(EXCHG.150).gif "UM_Message_Sizing")

## MP3

Das MP3-Format ist standardmäßig ausgewählt. Es ist das Standard-Audiodateiformat für Voicemailnachrichten. Das MP3-Format ist ein gängiges Audiodateiformat, das zum weitreichenden Verkleinern der Audiodatei dient und auf MP3-Playern und anderen Audiogeräten weite Verbreitung gefunden hat. MP3 ist ein plattformübergreifender Audiocodectyp, der mit vielen Mobiltelefonen und -geräten sowie verschiedenen Computerbetriebssystemen kompatibel ist.

## WMA

WMA ist von den drei Codec-Arten der Audiocodec mit der höchsten Komprimierung. Die Kompression beträgt etwa 11.000 Byte pro 10 Sekunden Audio. Das WMA-Dateiformat hat jedoch einen wesentlich größeren Kopfzeilenbereich als das WAV-Dateiformat. Der Kopfbereich der WMA-Datei umfasst ca. 7 KB, der der WAV-Datei hingegen weniger als 100 Byte. Obwohl WMA-Audioaufzeichnungen länger als 15 Sekunden sind, sind sie kleiner als GSM-Audioaufzeichnungen. Verwenden Sie deshalb den WMA-Audiocodec, wenn Sie die Audiodateien benötigen, die besonders klein sind und zugleich die höchste Qualität bieten.


> [!NOTE]
> Wenn Sie Pushbenachrichtigungen aus Ihrer lokalen Bereitstellung für OWA for Devices verwenden, ist das WMA-Format nicht zulässig. OWA for Devices unterstützt nur das Dateiformat MP3.



## G.711 PCM Linear

Der G.711 PCM Linear-Audiocodec erstellt WAV-Audiodateien, die nicht komprimiert sind. Daher belegen WAV-Audiodateien des G.711 PCM Linear-Codectyps verglichen mit den GSM- und WMA-Audiocodecs unabhängig von der Dauer den meisten Speicherplatz. G.711 PCM Linear-WAV-Audiodateien belegen pro 10 Sekunden Audio etwas über 160.000 Byte. Unter den drei von Unified Messaging verwendeten Audiocodecs bieten G.711 PCM Linear-WAV-Audiodateien die höchste Audioqualität. Die Qualität vergleichbarer Audiodateien, die mit WMA- und GSM-Audiocodecs erstellt wurden, ist für die meisten Benutzer, die Sprachnachrichten abrufen, jedoch durchaus ausreichend.

## GSM

Der GSM-Audiocodec erstellt WAV-Audiodateien, die komprimiert sind. GSM-WAV-Audiodateien belegen pro 10 Sekunden Audio etwas über 16.000 Byte. Von GSM erstellte Audiodateien sind jedoch größer als Audiodateien, die vom WMA-Audiocodec erstellt werden. Deshalb ist dies möglicherweise nicht die beste Wahl, wenn Sie Qualität und Größe der Sprachnachricht berücksichtigen müssen.

Codecs

