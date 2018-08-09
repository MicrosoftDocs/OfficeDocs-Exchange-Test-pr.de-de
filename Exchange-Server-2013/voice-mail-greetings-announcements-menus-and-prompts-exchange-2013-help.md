---
title: 'Begrüß., Infoansagen, Menüs und Menüansagen f. Voicemail: Exchange 2013-Hilfe'
TOCTitle: Begrüßungen, Informationsansagen, Menüs und Menüansagen für Voicemail
ms:assetid: df61105d-c9d8-452c-b028-50cbda47aecf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124902(v=EXCHG.150)
ms:contentKeyID: 54652710
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Begrüßungen, Informationsansagen, Menüs und Menüansagen für Voicemail

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Wenn Sie Unified Messaging (UM) installieren, wird eine allgemeine Sammlung von Standardaudiodateien installiert, die für das Voicemailsystem und für Menüansagen, Begrüßungen und Informationsansagen verwendet wird. Zwar ist es möglich, eine vollständig funktionsfähige automatische UM-Telefonzentrale oder einen Wählplan zu erstellen, die bzw. der nur die Standardtelefonansagen verwendet, sind diese Ansagen für viele Unternehmen zu allgemein, als dass sie als Schnittstelle zur Öffentlichkeit eingesetzt werden könnten. In diesem Thema werden die System- und Menüansagen, Begrüßungen und Informationsansagen behandelt, die von UM-Wählplänen und automatischen Telefonzentralen verwendet werden, sowie deren Verwendung beim Zugriff auf das Voicemailsystem durch Anrufer.

**Inhalt**

Übersicht über Telefonansagen und Begrüßungen

Systemansagen

Begrüßungen und Ansagen für UM-Wählpläne

Begrüßungen, Ansagen und Menüansagen für automatische UM-Telefonzentralen

Anpassen von Begrüßungen, Informationsansagen und Menüansagen sowie Navigationsmenüs

## Übersicht über Telefonansagen und Begrüßungen

Nach dem Installieren von Unified Messaging werden Audiodateien für UM-Wähleinstellungen und automatische Telefonzentralen auf den Postfachserver kopiert. Standardmäßig kopiert das Installationsprogramm die Audiodateien in den Ordner Programme\\Microsoft\\Exchange Server\\V15\\Unified Messaging\\Prompts*\\\<Sprache\>*. Wenn Sie die englische Version (USA) installiert haben, wird während der Installation ein Ordner namens \\en erstellt, in dem die englischen Versionen der Systemansagen gespeichert werden. Diese Systemansagen werden vom Postfachserver für Anrufer wiedergegeben, damit diese Begrüßungen, Menüansagen und Informationsansagen hören können, und damit Anrufer durch die UM-Menüs navigieren können.

Diese Systemaudiodateien oder Ansagen sollten niemals ersetzt werden. UM ermöglicht jedoch das Anpassen der Begrüßungen, Hauptmenü- und Informationsansagen der UM-Wähleinstellungen und der automatischen Telefonzentrale.

Die folgende Tabelle zeigt eine Übersicht über die für UM-Wähleinstellungen verwendeten Ansagen und Begrüßungen.

### Telefonansagen für UM-Wähleinstellungen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Telefonansagen und Begrüßungen</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Systemansagen</p></td>
<td><p>Dürfen nicht geändert werden.</p></td>
</tr>
<tr class="even">
<td><p>Begrüßung</p></td>
<td><p>Die Standardbegrüßung ist eine Systemansage, die standardmäßig wiedergegeben wird. Sie können jedoch eine von Ihnen erstellte benutzerdefinierte Begrüßungsdatei verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>Informationsansage</p></td>
<td><p>Informationsansagen sind standardmäßig deaktiviert. Wenn Sie eine Informationsansage aktivieren, müssen Sie eine benutzerdefinierte Begrüßungsdatei angeben.</p></td>
</tr>
</tbody>
</table>


Die folgende Tabelle zeigt eine Übersicht über die für automatische UM-Telefonzentralen verwendeten Ansagen und Begrüßungen.

### Telefonansagen für automatische UM-Telefonzentralen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Telefonansagen und Begrüßungen</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Systemansagen</p></td>
<td><p>Dürfen nicht geändert werden.</p></td>
</tr>
<tr class="even">
<td><p>Menüansagen während der Geschäftszeit</p></td>
<td><p>Menüansagen während der Geschäftszeit sind standardmäßig aktiviert, und es wird eine Systemansage wiedergegeben. Sie können jedoch eine von Ihnen erstellte benutzerdefinierte Begrüßungsdatei verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>Menüansagen außerhalb der Geschäftszeit</p></td>
<td><p>Menüansagen außerhalb der Geschäftszeit sind standardmäßig aktiviert, und es wird eine Systemansage wiedergegeben. Sie können jedoch eine von Ihnen erstellte benutzerdefinierte Begrüßungsdatei verwenden.</p></td>
</tr>
<tr class="even">
<td><p>Begrüßung während der Geschäftszeit</p></td>
<td><p>Die Begrüßung während der Geschäftszeit ist standardmäßig aktiviert, und es wird eine Systemansage wiedergegeben. Sie können jedoch eine von Ihnen erstellte benutzerdefinierte Begrüßungsdatei verwenden. Diese wird auch als Willkommensansage bezeichnet.</p></td>
</tr>
<tr class="odd">
<td><p>Begrüßung außerhalb der Geschäftszeit</p></td>
<td><p>Die Begrüßung außerhalb der Geschäftszeit ist standardmäßig aktiviert, und es wird eine Systemansage wiedergegeben. Sie können jedoch eine von Ihnen erstellte benutzerdefinierte Begrüßungsdatei verwenden. Diese wird auch als Willkommensansage bezeichnet.</p></td>
</tr>
<tr class="even">
<td><p>Informationsansage</p></td>
<td><p>Informationsansagen sind standardmäßig deaktiviert. Wenn Sie eine Informationsansage aktivieren, müssen Sie eine benutzerdefinierte Begrüßungsdatei angeben.</p></td>
</tr>
</tbody>
</table>



> [!WARNING]
> Das Ändern der installierten Systemansagen wird nicht unterstützt.



Übersicht über Telefonansagen und Begrüßungen

## Systemansagen

Unified Messaging wird mit einer Sammlung von Standardtelefonansagen für die Verwendung mit Outlook Voice Access, Wähleinstellungen und automatischen Telefonzentralen installiert. Auf einem Postfachserver werden für jede Sprache Hunderte von Systemansagen installiert. Der Postfachserver gibt die Audiodateien für diese Systemansagen für Anrufer wieder, wenn diese auf das Voicemailsystem zugreifen. Im Folgenden sind Beispiele für diese Systemansagen aufgeführt:

  - "Geben Sie Ihre PIN ein".

  - "Wenn Sie auf Ihr Postfach zugreifen möchten, geben Sie Ihre Durchwahl ein".

  - "Zum Kontaktieren einer Person drücken Sie die Raute-Taste".

  - "Buchstabieren Sie den Namen der Person, mit der eine Verbindung hergestellt werden soll. Beginnen Sie dabei mit dem Nachnamen".

  - "Wenn Sie mit einer bestimmten Person sprechen möchten, nennen Sie den Namen".


> [!WARNING]
> Das Ändern der installierten Systemansagen wird nicht unterstützt.




> [!NOTE]
> Wenn der Unified Messaging-Dienst auf dem Postfachserver gestartet wird, überprüft er, ob alle Systemansagen verfügbar sind. Wenn eine Systemansage nicht gefunden werden kann, gibt Unified Messaging eine Fehlermeldung aus. Um den zurückgegebenen Fehler zu beheben, suchen Sie das Ereignis mithilfe der Ereignisanzeige, und kopieren Sie die Datei, die im Fenster <STRONG>Ereigniseigenschaften</STRONG> aufgelistet wird, von der -Installations-DVD in den entsprechenden Ordner auf dem Postfachserver.



## Begrüßungen und Ansagen für UM-Wählpläne

Nachdem Sie den Postfachserver installiert und einen UM-Wählplan erstellt haben, besteht die Option, die Audiodateien für die Standardsystemansagen zu verwenden, die während der Installation erstellt wurden, oder angepasste Audiodateien zu erstellen, die mit UM-Wählplänen verwendet werden können.

UM-Wähleinstellungen verfügen über eine Begrüßung sowie eine optionale Informationsansage, die Sie ändern können. Diese Begrüßung wird verwendet, wenn Outlook Voice Access-Benutzer oder andere Anrufer die Zugriffsnummer des Teilnehmers wählen. Die Anrufer hören eine Standardbegrüßung "Willkommen. Sie sind mit Microsoft Exchange verbunden". Sie können diese Standardbegrüßung ändern und stattdessen eine firmenspezifische Ansage verwenden. Beispiel: "Willkommen bei Outlook Voice Access der Woodgrove Bank." Wenn Sie diese Begrüßung anpassen, müssen Sie zuerst eine entsprechende Begrüßung aufzeichnen, diese als WAV-Datei speichern und dann die Wähleinstellungen so konfigurieren, dass diese benutzerdefinierte Begrüßung verwendet wird.

Bei Unified Messaging kann im Anschluss an die Begrüßung eine Informationsansage wiedergegeben werden. Standardmäßig ist keine Informationsansage konfiguriert. Sie können jedoch eine Informationsansage für Anrufer zur Verfügung stellen. Sie können die Informationsansage für allgemeine Ankündigungen verwenden, die sich häufiger ändern als die Begrüßung, oder für Ankündigungen, die zur Einhaltung von Unternehmensrichtlinien erforderlich sind. Wenn Anrufer unbedingt die gesamte Informationsansage abhören sollen, kann diese als nicht unterbrechbar konfiguriert werden. In diesem Fall kann ein Anrufer die Informationsansage nicht durch Drücken einer Taste oder Sprechen eines Befehls abbrechen.

In der folgenden Tabelle werden die Begrüßungen und Informationsansagen für UM-Wähleinstellungen beschrieben.

### Begrüßungen und Informationsansagen für UM-Wählpläne

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Begrüßung</th>
<th>Standardbeispiel</th>
<th>Angepasstes Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Begrüßung</p></td>
<td><p>&quot;Willkommen. Sie sind mit Microsoft Exchange verbunden&quot;.</p></td>
<td><p>&quot;Willkommen bei Outlook Voice Access der Woodgrove Bank&quot;.</p></td>
</tr>
<tr class="even">
<td><p>Informationsansage</p></td>
<td><p>Standardmäßig ist keine Informationsansage konfiguriert.</p></td>
<td><p>&quot;Durch das Verwenden dieses Systems erklären Sie sich einverstanden, alle Unternehmensrichtlinien zu befolgen, wenn Sie auf dieses System zugreifen&quot;.</p></td>
</tr>
</tbody>
</table>


Wenn Sie Begrüßungen und Ansagen anpassen und konfigurieren, stellen Sie sicher, dass die Spracheinstellung, die für die UM-Wähleinstellungen konfiguriert ist, der Spracheinstellung der von Ihnen erstellten benutzerdefinierten Telefonansagen entspricht. Wenn dies nicht der Fall ist, hört ein Anrufer ggf. eine Nachricht oder Begrüßung in einer Sprache und eine andere Nachricht oder Begrüßung in einer anderen Sprache.

Übersicht über Telefonansagen und Begrüßungen

## Begrüßungen, Ansagen und Menüansagen für automatische UM-Telefonzentralen

Ebenso wie UM-Wähleinstellungen verfügen auch automatische UM-Telefonzentralen über eine Begrüßung, eine optionale Informationsansage und eine optionale benutzerdefinierte Menüansage. Sie können verschiedene Versionen der Begrüßung und Menüansage für Zeitspannen innerhalb bzw. außerhalb der Geschäftszeiten konfigurieren. Alle diese Ansagen können geändert werden.

Die Begrüßung ist das Erste, was ein Anrufer hört, wenn eine automatische UM-Telefonzentrale seinen Anruf beantwortet. In der Standardeinstellung lautet diese Ansage "Willkommen bei der automatischen Telefonzentrale von Microsoft Exchange". Die für den Anruf wiedergegebene Audiodatei ist die Standardsystemansage für die automatische UM-Telefonzentrale. Sie können jedoch eine alternative, auf Ihre Organisation abgestimmte Begrüßung verwenden, wie zum Beispiel "Danke für Ihren Anruf bei der Woodgrove Bank". Um diese Begrüßung anzupassen, müssen Sie zuerst eine benutzerdefinierte Begrüßung aufzeichnen, diese als WAV-Datei speichern und dann die automatische Telefonzentrale so konfigurieren, dass diese benutzerdefinierte Begrüßung verwendet wird. Ebenso wie Begrüßungen können Sie auch die Menüansagen anpassen.

Bei Unified Messaging kann zudem im Anschluss an die Begrüßung innerhalb oder außerhalb der Geschäftszeit eine Informationsansage wiedergegeben werden. Standardmäßig ist keine Informationsansage konfiguriert. Sie können Anrufern jedoch eine solche zur Verfügung stellen. Die Informationsansage kann die Geschäftszeiten der Organisation wiedergeben. Beispiel "Unsere Geschäftszeiten sind Montag bis Freitag von 08:00 Uhr bis 17:30 Uhr und Samstag von 8:30 Uhr bis 13:00 Uhr". Die Informationsansage kann ebenfalls Informationen enthalten, die für die Einhaltung von Organisationsrichtlinien erforderlich sind, wie zum Beispiel "Anrufe können zu Schulungszwecken überwacht werden". Wenn Anrufer unbedingt die gesamte Informationsansage abhören sollen, kann diese als nicht unterbrechbar konfiguriert werden. In diesem Fall kann der Anrufer die Informationsansage nicht durch Drücken einer Taste oder Sprechen eines Befehls abbrechen.

In der folgenden Tabelle werden die Begrüßungen und Informationsansagen für automatische UM-Telefonzentralen beschrieben.

### Begrüßungen, Informationsansagen und Menüansagen für automatische UM-Telefonzentralen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Begrüßung</th>
<th>Standardbeispiel</th>
<th>Angepasstes Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Begrüßung während der Geschäftszeit</p></td>
<td><p>&quot;Willkommen bei der automatischen Telefonzentrale von Microsoft Exchange&quot;.</p></td>
<td><p>&quot;Danke für Ihren Anruf bei der Woodgrove Bank&quot;.</p></td>
</tr>
<tr class="even">
<td><p>Begrüßung außerhalb der Geschäftszeit</p></td>
<td><p>Es wird keine Begrüßung außerhalb der Geschäftszeit wiedergegeben, bevor Sie Geschäftszeiten für die automatische Telefonzentrale konfigurieren. Die Begrüßung innerhalb der Geschäftszeit wird jedoch jederzeit für Anrufer wiedergegeben.</p></td>
<td><p>&quot;Sie rufen die Woodgrove Bank außerhalb der Geschäftszeit an. Unsere Geschäftszeiten sind Montag und Freitag zwischen 8:00 Uhr und 17:00 Uhr.&quot;</p></td>
</tr>
<tr class="odd">
<td><p>Informationsansage</p></td>
<td><p>Standardmäßig sind keine Informationsansagen konfiguriert.</p></td>
<td><p>&quot;Anrufe können zu Schulungszwecken überwacht werden&quot;.</p></td>
</tr>
<tr class="even">
<td><p>Hauptmenüansage während der Geschäftszeit</p></td>
<td><p>Es wird keine Standardmenüansage während der Geschäftszeit wiedergegeben, bevor Sie Tastenzuordnungen für die automatische Telefonzentrale konfigurieren.</p></td>
<td><p>&quot;Wenn Sie technischen Support benötigen, drücken oder sagen Sie 1. Wenn Sie mit Unternehmensstandorten oder der Unternehmensverwaltung verbunden werden möchten, drücken oder sagen Sie 2. Wenn Sie mit dem Vertrieb verbunden werden möchten, drücken oder sagen Sie 3&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>Hauptmenüansage außerhalb der Geschäftszeit</p></td>
<td><p>Es wird keine Standardmenüansage außerhalb der Geschäftszeit wiedergegeben, bevor Sie Tastenzuordnungen und die Geschäftszeiten für die automatische Telefonzentrale konfigurieren.</p></td>
<td><p>&quot;Wir freuen uns sehr über Ihren Anruf. Sie rufen die Woodgrove Bank jedoch außerhalb der Geschäftszeit an. Wenn Sie eine Nachricht hinterlassen möchten, drücken oder sagen Sie 1. Wir rufen Sie so schnell wie möglich zurück&quot;.</p></td>
</tr>
</tbody>
</table>


Stellen Sie ebenso wie bei UM-Wähleinstellungen sicher, dass die für die automatische UM-Telefonzentrale konfigurierte Spracheinstellung der Sprache der von Ihnen erstellten benutzerdefinierten Begrüßungen entspricht und auf die gleiche Sprache wie die UM-Wähleinstellungen festgelegt ist. Wenn dies nicht der Fall ist, hört ein Anrufer ggf. eine Nachricht oder Begrüßung in einer Sprache und eine andere Nachricht oder Begrüßung in einer anderen Sprache.

Übersicht über Telefonansagen und Begrüßungen

## Anpassen von Begrüßungen, Informationsansagen und Menüansagen sowie Navigationsmenüs

Auch wenn Systemansagen nicht ersetzt oder geändert werden dürfen, möchten Sie möglicherweise die Begrüßungen, Informationsansagen, Menüansagen und Navigationsmenüs anpassen, die mit UM-Wähleinstellungen und automatischen Telefonzentralen verwendet werden. Nach der Installation können Sie die UM-Wählpläne und automatischen UM-Telefonzentralen für die Verwendung von benutzerdefinierten Audiodateien (WAV oder WMA) konfigurieren. Vor der Aktivierung von benutzerdefinierten Sprachansagen für Anrufer müssen Sie die folgenden Schritte ausführen:

1.  Zeichnen Sie die benutzerdefinierten Begrüßungen, Informationsansagen und Menüansagen auf, und speichern Sie sie als WAV-Dateien. Der lineare PCM-Audiocodec (16 Bit/Sample) mit 8 KHz ist zum Codieren der WAV-Dateien erforderlich. Wenn Sie nicht dieses spezifische Format für die WAV-Dateien verwenden, wird ein Fehler generiert, der besagt, dass die Quelldatei ein nicht unterstütztes Format aufweist. Obwohl ein Fehler generiert wird, wird er nicht in der Ereignisanzeige angezeigt.

2.  Konfigurieren des UM-Wahlplans oder der automatischen Telefonzentrale für die Verwendung von benutzerdefinierten Begrüßungen, Informationsansagen und Menüansagen.

Wenn Sie eine automatische UM-Telefonzentrale erstellen, sind die Begrüßungen und Ansagen innerhalb und außerhalb der Geschäftszeiten nicht konfiguriert, und es sind keine Tastenzuordnungen für Ansagen für das Hauptmenü innerhalb und außerhalb der Geschäftszeiten definiert. Um benutzerdefinierte Begrüßungen und Ansagen für eine automatische Telefonzentrale korrekt zu konfigurieren, müssen Sie folgende Schritte ausführen:

  - Konfigurieren der Zeiten während und außerhalb der Geschäftszeiten auf der Seite **Geschäftszeiten**.

  - Erstellen der Begrüßungsaudiodateien (WAV oder WMA), die für die Begrüßungsansagen während der Geschäftszeiten bzw. außerhalb der Geschäftszeiten verwendet werden.

  - Konfigurieren der Begrüßungsansagen während und außerhalb der Geschäftszeiten auf der Seite **Begrüßungen**.

  - Erstellen der Begrüßungsdateien, die für die Begrüßungsansagen für das Hauptmenü während und außerhalb der Geschäftszeiten verwendet werden.

  - Konfigurieren der Begrüßungsansagen für das Hauptmenü während und außerhalb der Geschäftszeiten auf der Seite **Begrüßungen**.

  - Aktivieren und Konfigurieren der Menünavigation während und außerhalb der Geschäftszeiten auf der Seite **Menünavigation**.

Übersicht über Telefonansagen und Begrüßungen

