---
title: 'UM-Sprachen, -Telefonansagen und -Begrüßungen: Exchange 2013 Help'
TOCTitle: UM-Sprachen, -Telefonansagen und -Begrüßungen
ms:assetid: d48df962-9669-420b-838f-44bfe1012e2f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124728(v=EXCHG.150)
ms:contentKeyID: 50476799
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-Sprachen, -Telefonansagen und -Begrüßungen

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können Sprachpakete installieren und konfigurieren, um mehrere Sprachen in UM-Umgebungen (Unified Messaging) zu unterstützen.

UM-Sprachpakete ermöglichen Anrufern und Outlook Voice Access-Benutzern die Interaktion mit dem Voicemailsystem in mehreren Sprachen. Nachdem Sie eine zusätzliche Sprache auf einem Postfachserver installiert haben, können Anrufer und Outlook Voice Access-Benutzer E-Mail-Nachrichten in dieser Sprache wiedergeben und mit dem Voicemailsystem in dieser Sprache interagieren.

Einige Schlüsselkomponenten verwenden UM-Sprachpakete, um Benutzern und Anrufern die effektive Interaktion mit Unified Messaging in mehreren Sprachen zu ermöglichen. Jedes UM-Sprachpaket umfasst ein TTS-Modul (Text-zu-Sprache), vorab aufgezeichnete Telefonansagen sowie Support für die automatische Spracherkennung (Automatic Speech Recognition, ASR) und Voicemailvorschau für eine bestimmte Sprache. In diesem Thema werden die UM-Sprachpakete sowie die UM-Komponenten, die diese UM-Sprachpakete verwenden, erläutert. Außerdem wird beschrieben, wie die UM-Sprachpakete nach ihrer Installation zum Konfigurieren von UM-Wählplänen und automatischen UM-Telefonzentralen für die Verwendung anderer Sprachen eingesetzt werden können.

Exchange Unified Messaging-Sprachpakete sind versionsspezifisch und plattformspezifisch. Seit Exchange Server 2007 hat es mehrere Veröffentlichungen von UM-Sprachpaketen gegeben, u. a. die RTM-Version von Exchange 2007, Exchange 2007 SP1, SP2 und SP3, die RTM-Version von Exchange Server 2010, Exchange 2010 SP1 und SP2 und Exchange 2013. Für einige dieser Versionen sind sowohl 32-Bit- als auch 64-Bit-Downloads verfügbar, während für andere Versionen ausschließlich 64-Bit-Downloads zur Verfügung stehen.

Sie müssen auf einem Postfachserver unbedingt die richtige Version und Plattform der UM-Sprachpakete installieren. Installieren Sie keine UM-Sprachpakete auf einem Postfachserver, auf dem eine frühere Version von Exchange ausgeführt wird oder der für eine 32-Bit-Plattform konzipiert ist.

**Inhalt**

Übersicht über die UM-Sprachpakete

UM-Sprachkomponenten und -features

Voicemailvorschau

Unified Messaging-Sprachen

Unified Messaging-Sprachpakete

UM-Wählplansprachen

Sprachen der automatischen UM-Telefonzentrale

Auswahl der Clientsprache

## Übersicht über die UM-Sprachpakete

Durch die Installation von Unified Messaging-Sprachpaketen können die Telefonansagen eines Postfachservers in zusätzlichen Sprachen wiedergegeben werden, und der Server kann weitere Sprachen erkennen, wenn Anrufer die automatische Spracherkennung nutzen oder Sprachnachrichten transkribiert werden. UM-Sprachpakete enthalten Folgendes:

  - Vorab aufgezeichnete Ansagen in der Sprache des UM-Sprachpakets. Beispiel: "Bitte hinterlassen Sie Ihre Nachricht nach dem Signalton. Legen Sie anschließend auf, oder drücken Sie für weitere Optionen die Raute-Taste."

  - Grammatikdateien in der Sprache des UM-Sprachpakets, die von einem Postfachserver für die Suche nach bestimmten Benutzernamen innerhalb des Verzeichnisses verwendet werden.

  - TTS-Übersetzung (Text-zu-Sprache), sodass Inhalte (E-Mails, Kalender- oder Kontaktinformationen usw.) für die Anrufer in der Sprache des UM-Sprachpakets wiedergegeben werden können.

  - Support für die automatische Spracherkennung, sodass Anrufer über die Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI) in der Sprache des UM-Sprachpakets mit dem UM-System interagieren können.

  - Support für die Voicemailvorschau, sodass Benutzer Voicemailnachrichten über einen unterstützten E-Mail-Client wie Outlook oder Outlook Web App transkribiert in einer bestimmten Sprache lesen können.

UM-Sprachpakete enthalten vorab aufgezeichnete Telefonansagen, Support für TTS-Konvertierung für eine bestimmte Sprache und in einigen Fällen Support für die automatische Spracherkennung. In mehrsprachigen Umgebungen müssen Sie ggf. zusätzliche UM-Sprachpakete installieren, da einige Anrufer es vorziehen, Telefonansagen in einer anderen Sprache zu hören, oder E-Mails in mehreren Sprachen empfangen. Da das TTS-Konvertierungssystem basierend auf dem zu lesenden Nachrichtentext angewiesen werden muss, welche Sprache ausgewählt werden soll, müssen Sie mehrere UM-Sprachpakete installieren, damit der Postfachserver eine E-Mail mit mehreren Sprachen lesen kann. Wenn das Unified Messaging-Sprachpaket nicht installiert wurde, klingt der Inhalt der E-Mail bei der Wiedergabe für den Benutzer unlogisch und wirr. Durch das Installieren des entsprechenden Sprachpakets kann das TTS-Modul E-Mails und Kalenderelemente in der richtigen Sprache für den Outlook Voice Access-Benutzer wiedergeben. Außerdem werden die sprachspezifischen vorab aufgezeichneten Telefonansagen für Unified Messaging bereitgestellt. In einigen Fällen bieten die Sprachpakete auch Unterstützung für die automatische Spracherkennung.


> [!NOTE]
> Das TTS-Modul konvertiert Text in Sprache, jedoch nicht Sprache in Text. Ein UM-aktivierter Benutzer kann eine E-Mail mit angefügter Sprachdatei an einen anderen Benutzer senden. Jedoch können sie keine textbasierte E-Mail erstellen und an einen anderen Benutzer senden.



Wenn Sie ein Sprachpaket installieren, geht das Installationsprogramm folgendermaßen vor:

1.  Die zum Konfigurieren von UM-Wähleinstellungen und automatischen Telefonzentralen verwendeten Sprachansagen werden kopiert.

2.  Das TTS-Modul wird für das Wiedergeben von Nachrichten aktiviert, wenn ein Outlook Voice Access-Benutzer auf seinen Posteingang zugreift.

3.  Die automatische Spracherkennung wird für sprachaktivierte UM-Wähleinstellungen und automatische Telefonzentralen für die installierte Sprache aktiviert.

4.  Die Voicemailvorschau wird für Clients in anderen Sprachen aktiviert.

Nach dem Herunterladen eines UM-Sprachpakets von [Exchange Server 2013 UM Language Packs – Deutsch](https://go.microsoft.com/fwlink/p/?linkid=266542) kann dieses über den Befehl **Setup.exe** oder über das Installationsprogramm "*\<UMLanguagePack\>*.exe" installiert werden. Zum Entfernen eines UM-Sprachpakets müssen Sie jedoch den Befehl "Setup.exe" verwenden. Es gibt kein Cmdlet in der Exchange-Verwaltungsshell, mit dem Sprachen zu einem Postfachserver hinzugefügt oder von diesem entfernt werden können. Weitere Informationen zum Installieren eines UM-Sprachpakets finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md). Weitere Informationen zum Entfernen eines UM-Sprachpakets finden Sie unter [Entfernen eines UM-Sprachpakets](remove-a-um-language-pack-exchange-2013-help.md).


> [!NOTE]
> Bei der Installation eines Postfachservers wird standardmäßig das Sprachpaket für US-amerikanisches Englisch (en-US) installiert. Eine Entfernung ist nur möglich, indem Sie den Postfachserver vom Computer entfernen.



Zurück zum Seitenanfang

In der folgenden Tabelle sind die gegenwärtig verfügbaren Unified Messaging-Sprachpakete aufgelistet. Darüber hinaus wird der Name der Installationsdatei für die einzelnen UM-Sprachpakete sowie die Kultur-ID für die UM-Sprache genannt.

### Installationsdateinamen und Kultur-IDs für UM-Sprachpakete

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Sprache</th>
<th>Land/Region</th>
<th>Kultur-ID</th>
<th>Installationsdateiname</th>
<th>Verfügbarkeit</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Katalanisch</p></td>
<td><p>Spanien</p></td>
<td><p>ca-ES</p></td>
<td><p>UMLanguagePack.ca-ES</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Chinesisch (Hongkong)</p></td>
<td><p>China</p></td>
<td><p>zh-HK</p></td>
<td><p>UMLanguagePack.zh-HK</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Chinesisch (vereinfacht)</p></td>
<td><p>China</p></td>
<td><p>zh-CHS</p></td>
<td><p>UMLanguagePack.zh-CN</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Chinesisch (traditionell)</p></td>
<td><p>Taiwan</p></td>
<td><p>zh-TW</p></td>
<td><p>UMLanguagePack.zh-TW</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Dänisch</p></td>
<td><p>Dänemark</p></td>
<td><p>da-DK</p></td>
<td><p>UMLanguagePack.da-DK</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Niederländisch</p></td>
<td><p>Niederlande</p></td>
<td><p>nl-NL</p></td>
<td><p>UMLanguagePack.nl-NL</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Australien</p></td>
<td><p>en-AU</p></td>
<td><p>UMLanguagePack.en-AU</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Englisch</p></td>
<td><p>Kanada</p></td>
<td><p>en-CA</p></td>
<td><p>UMLanguagePack.en-CA</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Indien</p></td>
<td><p>en-IN</p></td>
<td><p>UMLanguagePack.en-IN</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Englisch</p></td>
<td><p>Vereinigtes Königreich</p></td>
<td><p>en-GB</p></td>
<td><p>UMLanguagePack.en-GB</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Vereinigte Staaten</p></td>
<td><p>en-US</p></td>
<td><p>Bei der Installation eines Postfachservers enthalten</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Finnisch</p></td>
<td><p>Finnland</p></td>
<td><p>fi-Fl</p></td>
<td><p>UMLanguagePack.fi-Fl</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Französisch</p></td>
<td><p>Kanada</p></td>
<td><p>fr-CA</p></td>
<td><p>UMLanguagePack.fr-CA</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Französisch</p></td>
<td><p>Frankreich</p></td>
<td><p>fr-FR</p></td>
<td><p>UMLanguagePack.fr-FR</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Deutsch</p></td>
<td><p>Deutschland</p></td>
<td><p>de-DE</p></td>
<td><p>UMLanguagePack.de-DE</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Italienisch</p></td>
<td><p>Italien</p></td>
<td><p>it-IT</p></td>
<td><p>UMLanguagePack.it-IT</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Japanisch</p></td>
<td><p>Japan</p></td>
<td><p>ja-JP</p></td>
<td><p>UMLanguagePack.ja-JP</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Korea</p></td>
<td><p>Koreanisch</p></td>
<td><p>ko-KR</p></td>
<td><p>UMLanguagePack.ko-KR</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Norwegisch (Bokmal)</p></td>
<td><p>Norwegen</p></td>
<td><p>nb-NO</p></td>
<td><p>UMLanguagePack.nb-NO</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Polnisch</p></td>
<td><p>Polen</p></td>
<td><p>pl-PL</p></td>
<td><p>UMLanguagePack.pl-PL</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Portugiesisch</p></td>
<td><p>Brasilien</p></td>
<td><p>pt-BR</p></td>
<td><p>UMLanguagePack.pt-BR</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Portugiesisch</p></td>
<td><p>Portugal</p></td>
<td><p>pt-PT</p></td>
<td><p>UMLanguagePack.pt-PT</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Russisch</p></td>
<td><p>Russische Föderation</p></td>
<td><p>ru-RU</p></td>
<td><p>UMLanguagePack.ru-RU</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Spanisch</p></td>
<td><p>Spanien</p></td>
<td><p>es-ES</p></td>
<td><p>UMLanguagePack.es-ES</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="odd">
<td><p>Spanisch</p></td>
<td><p>Mexiko</p></td>
<td><p>es-MX</p></td>
<td><p>UMLanguagePack.es-MX</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
<tr class="even">
<td><p>Schwedisch</p></td>
<td><p>Schweden</p></td>
<td><p>sv-SE</p></td>
<td><p>UMLanguagePack.sv-SE</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=266542">Download verfügbar</a></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## UM-Sprachkomponenten und -features

Einige Schlüsselkomponenten und -features in Unified Messaging ermöglichen Benutzern und Anrufern die Interaktion mit einem mehrsprachigen Voicemailsystem. Damit diese Komponenten und Features ordnungsgemäß funktionieren und Anrufer in die Lage versetzen, mit dem System in mehreren Sprachen zu interagieren, müssen die UM-Sprachpakete ordnungsgemäß auf einem Postfachserver installiert werden.

## Vorab aufgezeichnete Telefonansagen

Die Postfachserverrolle umfasst mehrere Audiodateien mit Standardtelefonansagen. Diese Audiodateien umfassen die Aufzeichnungen für Outlook Voice Access-Menüs, Voicemailansagen und von Exchange Unified Messaging verwendete Nummern. Die Audiodateien werden von einem Postfachserver für eingehende interne und externe Anrufer wiedergegeben. Viele dieser Audiodateien sind Standardtelefonansagen, die Benutzern der Benutzerschnittstelle für Telefoneingabe (Telephony User Interface, TUI) und Benutzern von Outlook Voice Access die Informationen zur Verfügung stellen, die sie für die Navigation in der Benutzerschnittstelle für Telefoneingabe und der Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI) benötigen. Die Ansagen befinden sich unter \<*Programme*\>\\Microsoft\\Exchange Server\\V15\\UnifiedMessaging\\Prompts\\\<Sprache\>. Die vom Postfachserver verwendeten Telefonansagen zur Unterstützung von Benutzern bei der Navigation durch die Menüs sollten nicht ersetzt oder geändert werden.

Wenn ein weiteres UM-Sprachpaket installiert wird, werden die vorab aufgezeichneten Ansagen für die betreffende Sprache ebenfalls installiert. Nachdem ein UM-Sprachpaket installiert wurde, können die vorab aufgezeichneten Ansagen für die betreffende Sprache von UM-Wähleinstellungen und automatischen Telefonzentralen verwendet werden.

## TTS-Sprachen

Unified Messaging verwendet ein TTS-Modul (Text-zu-Sprache). Die TTS-Funktionen werden vom Microsoft Speech Server-Dienst bereitgestellt. Das TTS-Modul liest und konvertiert geschriebenen Text in hörbare Ausgaben, die vom Anrufer angehört werden können. Das TTS-Modul liest und konvertiert die folgenden Elemente im Postfach eines Benutzers:

  - Nachrichtentext von E-Mails und Voicemailnachrichten, Betreffangaben und Namen

  - Nachrichtentext von Kalenderelementen, Betreffangaben, Orte und Namen

  - Namen persönlicher Kontakte

  - Standardmäßige Voicemailansagen eines Benutzers


> [!NOTE]
> Nachdem ein Benutzer personalisierte Voicemailansagen aufgezeichnet hat, wird die TTS-Version der Voicemailansagen nicht mehr verwendet.



## Automatische Spracherkennung (Automatic Speech Recognition, ASR)

Es ist nicht nur Support für TTS, sondern auch für ASR in Unified Messaging enthalten. Die ASR-Funktionen werden vom Microsoft Speech Server-Dienst bereitgestellt. ASR ermöglicht es Anrufern, mithilfe von Sprachbefehlen durch die Menüs zu navigieren und mit Elementen aus ihren jeweiligen Postfächern zu interagieren, z. B. mit Nachrichten, den persönlichen Kontakten und dem Kalender. Sämtliche Sprachpakete bieten Unterstützung für die automatische Spracherkennung.

Zurück zum Seitenanfang

## Voicemailvorschau

UM-Sprachpakete bieten außerdem Support für die Voicemailvorschau, mit der die Benutzer ihre Sprachnachrichten schnell auswählen können, indem sie ihre Transkriptionen in einem unterstützen E-Mail-Client wie Outlook oder Outlook Web App lesen.

Wenn ein Anrufer eine Sprachnachricht für einen UM-aktivierten Benutzer hinterlässt, werden die Sprachnachrichtdatei und eine Transkription der Sprachnachricht im Nachrichtentext der Sprachnachricht platziert, die an das Postfach des Benutzers gesendet wird.

Alle UM-Sprachpakete sind einzelne Dateien, die heruntergeladen werden können. Diese Sprachpakete umfassen vorab aufgezeichnete Ansagen, Grammatikdateien, die TTS-Übersetzung (Text-to-Speech, Text-zu-Sprache) und automatische Spracherkennung. Doch nicht alle UM-Sprachpakete unterstützen die Voicemailvorschau.

Die folgenden UM-Sprachpakete unterstützen alle Komponenten und Funktionen, einschließlich der Voicemailvorschau:

  - Englisch (USA) - (en-US)

  - Englisch (Kanada) (en-CA)

  - Französisch (Frankreich) - (fr-FR)

  - Italienisch - (it-IT)

  - Polnisch (pl-PL)

  - Portugiesisch (Portugal) (pt-PT)

  - Spanisch (Spanien) (es-ES)

Nach der Installation des Postfachservers sendet der Server standardmäßig eine Voicemailvorschau an UM-aktivierte Benutzer, wenn ein unterstütztes UM-Sprachpaket installiert ist.

Manche Unified Messaging-Voicemailvorschau-Partner bieten erweiterten Support für die Transkription der Voicemailvorschau. Diese Partner beschäftigen Mitarbeiter für die Korrektur von Voicemail-Transkriptionen, die mithilfe von ASR erstellt wurden. Jeder Voicemailvorschau-Partner muss bestimmte Anforderungen erfüllen, um für die Zusammenarbeit mit Unified Messaging zertifiziert zu werden.

Wenn Sie feststellen, dass die an Ihre Benutzer gesendete Voicemailvorschau nicht präzise genug ist, können Sie sich an einen der zertifizierten Voicemailvorschau-Partner wenden, die auf der Seite [Microsoft Pinpoint für Unified Messaging](https://go.microsoft.com/fwlink/p/?linkid=261951) aufgeführt sind, und sich gegen zusätzliche Kosten bei diesen anmelden.

Die UM-Sprachpakete können aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=266542) heruntergeladen werden. Weitere Informationen finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md).

## Unified Messaging-Sprachen

Damit Anrufer die mehrsprachigen Funktionen von Unified Messaging verwenden können, müssen Sie zuerst ein UM-Sprachpaket installieren. Anschließend können Sie andere UM-Komponenten konfigurieren.

  - Installieren Sie das UM-Sprachpaket auf den Postfachservern in Ihrer Organisation.

  - Falls erforderlich, konfigurieren Sie die Standardsprache für einen Satz mit UM-Wähleinstellungen. Auf diese Weise können Outlook Voice Access-Benutzer, die den UM-Wähleinstellungen zugeordnet sind, beim Zugriff auf ihr Postfach die neue Sprache verwenden. Die Benutzer können jedoch auch weiterhin ihre Spracheinstellung in den Outlook Web App-Optionen konfigurieren.

  - Wenn Sie für automatische Telefonzentralen mehrere Sprachen aktivieren müssen, konfigurieren Sie die Spracheinstellung für eine automatische UM-Telefonzentrale. Standardmäßig verwendet eine automatische UM-Telefonzentrale die Sprache der UM-Wähleinstellungen. Sie können diese Einstellung jedoch ändern und es nicht authentifizierten Anrufern ermöglichen, eine Verbindung mit Ihrer Organisation herzustellen und in der für die automatische UM-Telefonzentrale angegebenen Sprache durch deren Menüs zu navigieren.

## Unified Messaging-Sprachpakete

Sie installieren ein UM-Sprachpaket mithilfe von "Setup.exe" auf einem Postfachserver. Nach der Installation des neuen Sprachpakets wird die dem Sprachpaket zugeordnete Sprache der Liste der verfügbaren Sprachen hinzugefügt. Sie können die Sprachen, die installiert wurden, mithilfe des Cmdlets [Get-UMService](https://technet.microsoft.com/de-de/library/jj552407\(v=exchg.150\)) in der Exchange-Verwaltungsshell anzeigen.

Bei der Installation des UM-Sprachpakets werden die vom TTS-Modul verwendeten Dateien und die vorab aufgezeichneten Telefonansagen für die ausgewählte Sprache kopiert und für Benutzer zur Verfügung gestellt, die eine Verbindung mit dem Voicemailsystem herstellen. Die  UM-Sprachpakete können aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=266542) heruntergeladen werden. Weitere Informationen finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md).

## UM-Wählplansprachen

Jeder Satz mit UM-Wähleinstellungen, der erstellt wird, enthält eine Standardspracheinstellung. Die Spracheinstellung für den UM-Wählplan ist erforderlich, da Unified Messaging möglicherweise die TTS-Konvertierung verwenden oder eine Standardtelefonansage für Outlook Voice Access-Benutzer wiedergeben muss, wenn diese auf ihr Postfach zugreifen. Sie müssen eine Standardsprache für die Wähleinstellungen auswählen.

Bei der anfänglichen Installation von Exchange ist US-amerikanisches Englisch die Standardsprache und die einzige verfügbare Sprachoption für Ihren Wählplan. Nachdem Sie ein UM-Sprachpaket auf einem Postfachserver installiert haben, wird die dem Sprachpaket zugeordnete Sprache als verfügbare Option aufgelistet, wenn Sie die Standardsprache für den Wählplan konfigurieren.

Die Standardsprache ist für Anrufer wichtig. Wenn ein Outlook Voice Access-Benutzer das Voicemailsystem anruft, basiert die verwendete Sprache auf der Spracheinstellung in Outlook Web App, die festgelegt wurde, als sich der Benutzer erstmals bei seinem Postfach angemeldet hat. Unified Messaging vergleicht die in Outlook Web App festgelegte Sprache mit der Liste der verfügbaren Sprachen für den Wählplan, dem der Benutzer zugeordnet ist. Wenn keine passende Entsprechung gefunden wird, wird der UM-Wählplan in der Standardsprache verwendet. Wenn Sie z. B. einen Satz mit Wähleinstellungen verwenden, der ausschließlich Benutzer aus Frankreich enthält, können Sie die Standardspracheinstellung für die Wähleinstellungen in Französisch ändern.

## Sprachen der automatischen UM-Telefonzentrale

Da automatische UM-Telefonzentralen bei der Erstellung einem UM-Wählplan zugeordnet werden, wird standardmäßig die Standardspracheinstellung des zugehörigen UM-Wählplans verwendet. Diese Einstellung kann jedoch geändert werden, nachdem die automatische UM-Telefonzentrale erstellt wurde.

Die Spracheinstellung der automatischen UM-Telefonzentrale ist erforderlich, da Unified Messaging ggf. die TTS-Konvertierung verwenden oder eine Standardtelefonansage für einen Anrufer wiedergeben muss. Unified Messaging überprüft nicht, ob die Sprache benutzerdefinierter Ansagen für die automatische Telefonzentrale mit der Spracheinstellung der automatische Telefonzentrale übereinstimmt. Als bewährte Methode sollten Sie jedoch sicherstellen, dass die Spracheinstellung der automatischen Telefonzentrale mit der Sprache der benutzerdefinierten Ansagen übereinstimmt. Anderenfalls wechselt das System bei der Wiedergabe einer Nachricht oder Ansage möglicherweise von einer Sprache in eine andere.

Die Möglichkeit, die Spracheinstellung der automatischen Telefonzentrale zu ändern, ist ebenfalls hilfreich, wenn Sie mehrere verschiedene sprachspezifisch automatische Telefonzentralen für Anrufer benötigen.

## Auswahl der Clientsprache

UM-Sprachpakete ermöglichen Anrufern und Outlook Voice Access-Benutzern die Interaktion mit dem Unified Messaging-System in mehreren Sprachen. Nach der Installation zusätzlicher Sprachpakete auf einem Postfachserver sind Anrufer und Outlook Voice Access-Benutzer in der Lage, E-Mails in dieser Sprache wiederzugeben und mit dem Voicemailsystem in dieser Sprache zu interagieren. Outlook Web App-Benutzer und Benutzer von Outlook 2010 oder einer höheren Version können die Transkription der Sprachnachricht mithilfe der Voicemailvorschau in einer bestimmten Sprache anzeigen.

Um eine bestimmte Sprache zu unterstützen, muss ein UM-Clientsprachpaket für diese Sprache auf jedem Postfachserver installiert werden.

In einigen Fällen kann eine Clientfallbacksprache verwendet werden, wenn das UM-Sprachpaket für eine bestimmte Sprache nicht installiert wurde und nicht verfügbar ist. Fallbacksprachen für UM-Clients sind nur für einige Sprachen verfügbar. Wenn für eine bestimmte Sprache kein UM-Sprachpaket installiert und keine Fallbacksprache verfügbar ist, wird en-US (US-Englisch) verwendet.

Die folgende Tabelle zeigt eine Liste mit Clientsprachen und den entsprechenden Fallbacksprachen, die verwendet werden, wenn ein bestimmtes UM-Sprachpaket nicht auf einem Postfachserver installiert wurde.

### Clientfallbacksprachen für UM

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Sprache</th>
<th>Land/Region</th>
<th>Kultur-ID</th>
<th>Erste Sprachauswahl, sofern installiert</th>
<th>Zweite Sprachauswahl, sofern installiert</th>
<th>Dritte Sprachauswahl, sofern installiert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Katalanisch</p></td>
<td><p>Spanien</p></td>
<td><p>ca-ES</p></td>
<td><p>ca-ES</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Chinesisch (Hongkong)</p></td>
<td><p>China</p></td>
<td><p>zh-HK</p></td>
<td><p>zh-HK</p></td>
<td><p>zh-CN</p></td>
<td><p>zh-TW</p></td>
</tr>
<tr class="odd">
<td><p>Chinesisch (vereinfacht)</p></td>
<td><p>China</p></td>
<td><p>zh-CN</p></td>
<td><p>zh-CN</p></td>
<td><p>zh-HK</p></td>
<td><p>zh-TW</p></td>
</tr>
<tr class="even">
<td><p>Chinesisch (traditionell)</p></td>
<td><p>Taiwan</p></td>
<td><p>zh-TW</p></td>
<td><p>zh-TW</p></td>
<td><p>zh-HK</p></td>
<td><p>zh-CN</p></td>
</tr>
<tr class="odd">
<td><p>Dänisch</p></td>
<td><p>Dänemark</p></td>
<td><p>da-DK</p></td>
<td><p>da-DK</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Niederländisch</p></td>
<td><p>Niederlande</p></td>
<td><p>nl-NL</p></td>
<td><p>nl-NL</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Australien</p></td>
<td><p>en-AU</p></td>
<td><p>en-AU</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Englisch</p></td>
<td><p>Kanada</p></td>
<td><p>en-CA</p></td>
<td><p>en-CA</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Indien</p></td>
<td><p>en-IN</p></td>
<td><p>en-IN</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Englisch</p></td>
<td><p>Vereinigtes Königreich</p></td>
<td><p>en-GB</p></td>
<td><p>en-GB</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Englisch</p></td>
<td><p>Vereinigte Staaten</p></td>
<td><p>en-US</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Finnisch</p></td>
<td><p>Finnland</p></td>
<td><p>fi-FL</p></td>
<td><p>fi-FL</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Französisch</p></td>
<td><p>Kanada</p></td>
<td><p>fr-CA</p></td>
<td><p>fr-CA</p></td>
<td><p>fr-FR</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="even">
<td><p>Französisch</p></td>
<td><p>Frankreich</p></td>
<td><p>fr-FR</p></td>
<td><p>fr-FR</p></td>
<td><p>fr-CA</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="odd">
<td><p>Deutsch</p></td>
<td><p>Deutschland</p></td>
<td><p>de-DE</p></td>
<td><p>de-DE</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Italienisch</p></td>
<td><p>Italien</p></td>
<td><p>it-IT</p></td>
<td><p>it-IT</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Japanisch</p></td>
<td><p>Japan</p></td>
<td><p>ja-JP</p></td>
<td><p>ja-JP</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Koreanisch</p></td>
<td><p>Korea</p></td>
<td><p>ko-KR</p></td>
<td><p>ko-KR</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Norwegisch (Bokmal)</p></td>
<td><p>Norwegen</p></td>
<td><p>nb-NO</p></td>
<td><p>nb-NO</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Polnisch</p></td>
<td><p>Polen</p></td>
<td><p>pl-PL</p></td>
<td><p>pl-PL</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Portugiesisch</p></td>
<td><p>Brasilien</p></td>
<td><p>pt-BR</p></td>
<td><p>pt-BR</p></td>
<td><p>pt-PT</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="even">
<td><p>Portugiesisch</p></td>
<td><p>Portugal</p></td>
<td><p>pt-PT</p></td>
<td><p>pt-PT</p></td>
<td><p>pt-BR</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="odd">
<td><p>Russisch</p></td>
<td><p>Russische Föderation</p></td>
<td><p>ru-RU</p></td>
<td><p>ru-RU</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Spanisch</p></td>
<td><p>Spanien</p></td>
<td><p>es-ES</p></td>
<td><p>es-ES</p></td>
<td><p>es-MX</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="odd">
<td><p>Spanisch</p></td>
<td><p>Mexiko</p></td>
<td><p>es-MX</p></td>
<td><p>es-MX</p></td>
<td><p>es-ES</p></td>
<td><p>en-US</p></td>
</tr>
<tr class="even">
<td><p>Schwedisch</p></td>
<td><p>Schweden</p></td>
<td><p>sv-SE</p></td>
<td><p>sv-SE</p></td>
<td><p>en-US</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

