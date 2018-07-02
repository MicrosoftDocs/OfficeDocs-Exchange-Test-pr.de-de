---
title: 'Informationen zum Exchange UM-Problembehandlungstool: Exchange 2013 Help'
TOCTitle: Informationen zum Exchange UM-Problembehandlungstool
ms:assetid: cc11bf5e-2c87-4495-b2ad-3e9a6bc81dbc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg584301(v=EXCHG.150)
ms:contentKeyID: 56271573
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Informationen zum Exchange UM-Problembehandlungstool

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das Microsoft Exchange 2010 UM-Problembehandlungstool (Unified Messaging Troubleshooting Tool) ist ein Cmdlet für die Exchange-Verwaltungsshell und hat den Namen **Test-ExchangeUMCallFlow**. Mit diesem Tool können Sie eine Reihe von Diagnosetests für Unified Messaging (UM) in Ihrer Organisation ausführen. Schlägt einer der Tests fehl, meldet das Tool den Grund für den Fehler sowie mögliche Lösungen zum Beheben des Problems. Sie können das UM-Problembehandlungstool nur auf Exchange 2010 oder Servern neuerer Versionen verwenden.

Mit dem UM-Problembehandlungstool kann getestet werden, ob Voicemail sowohl in lokalen als auch in standortübergreifenden Bereitstellungen ordnungsgemäß funktioniert. Sie können dieses Tool in UM-Bereitstellungen nutzen, die Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server 2010 umfassen, oder in UM-Bereitstellungen, die VoIP-Gateways, IP/PBX-Anlagen oder Session Border Controller (SBCs) umfassen.


> [!NOTE]
> Das UM-Problembehandlungstool wird zum Testen und zur Problembehandlung verwendet. Zusätzlich sollte das Cmdlet <STRONG>Test-UMConnectivity</STRONG> für Überwachungsaufgaben verwendet werden. Das Cmdlet <STRONG>Test-UMConnectivity</STRONG> wird mit SCOM-Management Packs (System Center Operations Manager) verwendet, mit denen Exchange 2010 UM-Server oder Exchange 2013-Clientzugriffsserver und -Postfachserver sowie die Telefoniekomponenten überwacht werden. Das Cmdlet <STRONG>Test-UMConnectivity</STRONG> führt lokale SIP-Tests und lokale Anmeldetests für Postfächer aus und kann als SCOM-Task ausgeführt werden.



Das UM-Problembehandlungstool können Sie über folgende Seite herunterladen: [Unified Messaging-Problembehandlungstool](https://go.microsoft.com/fwlink/p/?linkid=182625).

**Inhalt**

Übersicht

Architektur der UM-Problembehandlung

VoIP-Gateways und IP-PBX-Bereitstellungen

Office Communications Server 2007 R2- und Microsoft Lync Server-Bereitstellungen

Installieren des UM-Problembehandlungstools

Cmdlet-Parameter

## Übersicht

Das UM-Problembehandlungstool vereinfacht das Testen und die Problembehandlung in UM-Bereitstellungen. Wenn das UM-Problembehandlungstool ausgeführt wird, generiert es automatisch eine Reihe von Ablaufverfolgungsdateien, die im Ordner "C:\\Benutzer\\%UserProfile%\\AppData\\Roaming\\Microsoft Exchange 2010 UM Troubleshooting" gespeichert werden. Das Tool generiert die folgenden Ablaufverfolgungsdateien:

  - **UMTool\_Collaboration**   Beinhaltet RTC-Stapelüberwachungen

  - **UMTool\_DiagnosticLog**   Listet alle Tests, die ausgeführt wurden, sowie deren Ergebnisse auf

  - **UMTool\_S4**   Beinhaltet die Stapelüberwachungen für S4-Signalisierung

  - **UMTool\_SIPMessageLogs**   Beinhaltet die vollständigen SIP-Überwachungen für den Testaufruf, der ausgeführt wird

Das UM-Problembehandlungstool stellt direkt eine Verbindung mit einem lokalen Session Border Controller (SBC), sofern ein solcher existiert, oder mit einem SBC in einem Datencenter her und emuliert einen eingehenden Anruf so, als käme dieser von einer PBX-Anlage über ein VoIP-Gateway oder eine IP-PBX-Anlage. Mit dem UM-Problembehandlungstool kann Folgendes diagnostiziert werden:

  - Fehlerhafte Einstellungen in lokalen oder standortübergreifenden UM-Bereitstellungen, in denen Office Communications Server 2007 R2 oder Microsoft Lync Server bereitgestellt wird

  - Fehlerhafte Einstellungen in lokaler oder standortübergreifender Telephonieausrüstung, die VoIP-Gateways und PBX-Anlagen oder IP-PBX-Anlagen umfasst

  - Probleme mit DNS (Domain Name System)

  - Zertifikatprobleme, wenn SIP-gesicherte oder gesicherte UM-Wähleinstellungen verwendet werden

  - Signalisierungs- und Medienprobleme für DTMF (auch als Tonwahl bezeichnet) und Audio

Wenn das UM-Problembehandlungstool einen Fehler in der Konfiguration erkennt, meldet es den Grund für den Fehler sowie die möglichen Lösungen für die erkannten Probleme. Wird das UM-Problembehandlungstool in einer lokalen Bereitstellung verwendet, kann es folgende Fehler melden:

  - Die maximal zulässige Anzahl von Anrufen (Anruflimit) wurde erreicht.

  - Der Benutzer ist nicht für Unified Messaging aktiviert.

  - Die Informationen zu dem UM-IP-Gateway, den UM-Wähleinstellungen oder dem UM-Sammelanschluss wurden nicht gefunden.

  - Der Sicherheitstyp passt nicht zu den UM-Wähleinstellungen.

  - Es sind keine Arbeitsprozesse verfügbar, die den Anruf verarbeiten können.

  - Der UM-Dienst oder UM-Anrufroutingdienst wird beendet.

  - Die Active Directory-Gesamtstruktur wurde nicht gefunden.

  - Es ist kein Speicherplatz verfügbar.

  - In der Anforderung wurden unzulässige SIP-Kopfzeilen verwendet.

  - Es wurde ein Office Communications Server 2007 R2-Server oder ein Server mit Lync Server angerufen.

  - Das UM-IP-Gateway ist deaktiviert.

  - Der URI für den Benutzer, der angerufen wird, ist ungültig.

Wird das UM-Problembehandlungstool in einer standortübergreifenden Bereitstellung verwendet, kann es folgende Fehler melden:

  - Der Benutzer ist nicht für Unified Messaging aktiviert.

  - Das UM-IP-Gateway ist deaktiviert.

  - Der URI für den Benutzer ist ungültig.

  - Der Sicherheitstyp passt nicht zu den UM-Wähleinstellungen.

  - In der Anforderung wurden unzulässige SIP-Kopfzeilen verwendet.

  - Die Informationen zu dem UM-IP-Gateway, den UM-Wähleinstellungen oder dem UM-Sammelanschluss wurden nicht gefunden.

Das UM-Problembehandlungstool sendet 15 Sekunden lang eine Beispiel-WAV-Datei. Nachdem die Audiodatei und der RTP-Audiodatenstrom gesendet und wiedergegeben wurden, meldet das Tool Metriken für die allgemeine Audioqualität, mit denen Probleme bei der Audioqualität im Zusammenhang mit der Netzwerkkonnektivität diagnostiziert werden können, z. B. Jitter und durchschnittlicher Paketverlust. Ein entsprechender Bericht beinhaltet die Qualität der Mediendatenströme zu und von einem UM-Server und enthält folgende Informationen:

  - Netzwerk-Mean Opinion Score (NMOS)

  - Codec

  - Wartezeit in Millisekunden (ms)

  - Jitter in Millisekunden (ms)

  - % des Paketverlusts

  - Die NMOS-Klassifizierung und -Bewertung, anhand der die Audioqualität ermittelt wird, ist wie folgt festgelegt:
    
      - NMOS kleiner als 2 = Schlecht
    
      - NMOS größer als 2, aber kleiner als 3 = Durchschnitt
    
      - NMOS größer als 3, aber kleiner als 4 = Gut
    
      - NMOS größer als 4, aber kleiner als 5 = Hervorragend

Das UM-Problembehandlungstool unterstützt das Testen von UM-Wähleinstellungen, für die gesicherte, SIP-gesicherte und ungesicherte Anrufe verwendet werden. Wenn Sie "Gesichert" oder "SIP-gesichert" auswählen, wird der Fingerabdruck des verwendeten Zertifikats geprüft, um zu ermitteln, ob das Zertifikat abgelaufen ist, und um den Typ des Zertifikats zu ermitteln, das für TLS-Datenübertragungen (Transport Layer Security) verwendet wird. Das Zertifikat wird dazu verwendet, die Identität des Remotecomputers ordnungsgemäß zu bestimmen und sicherzustellen. Wenn der Modus "Gesichert" oder "SIP-gesichert" ausgewählt ist, prüft das UM-Problembehandlungstool, ob Folgendes zutrifft:

  - Das lokale Zertifikat wurde im lokalen Computerspeicher gefunden.

  - Dem verwendeten Zertifikat wird vertraut.

  - Der im Zertifikat angegebene Zielname ist gültig.

  - Das Zertifikat ist abgelaufen.

  - Der Remotecomputer vertraut dem Zertifikat.

  - Das Zertifikat wurde widerrufen.

  - Das Zertifikat hat nicht die erforderliche erweiterte Schlüsselverwendung.

Das UM-Problembehandlungstool kann abhängig davon, ob Office Communications Server 2007 R2 oder Lync Server bereitgestellt wird oder ob VoIP-Gateways und PBX- oder IP-PBX-Anlagen mit Unified Messaging-Server verwendet werden, im Gateway- oder im SIPClient-Modus ausgeführt werden. Wird der Gateway- oder der SIPClient-Modus verwendet, unterstützt das UM-Problembehandlungstool die folgenden Formate für das Führen von Anrufen. Welches Format verwendet wird, hängt vom URI-Typ der UM-Wähleinstellungen ab:

  - Telefondurchwahl   0231-5551010

  - E.164-Telefonnummern   +49 (231) 5551010

  - SIP-Adressen   tonysmith@contoso.com

Wenn der SIPClient-Modus verwendet wird, tätigt das UM-Problembehandlungstool einen Sprachmemoanruf. Dies ist ein Anruf, bei dem weder ein Telefon noch ein Unified Communications-Endpunkt (UC) klingelt. Stattdessen wird der Anruf direkt an Voicemail gesendet. Wenn das UM-Problembehandlungstool im SIPClient-Modus ausgeführt wird, ermittelt es Folgendes:

  - Den Zielbenutzer, der angerufen wird.

  - Wurde die Verbindung für den SIP-Anruf erfolgreich hergestellt?

  - Wurde der SIP-Anruf von einem Exchange 2010 Unified Messaging-Server oder Exchange 2013-Postfachserver angenommen?

  - Wurde die richtige DTMF-Folge empfangen?

  - Wurde die WAV-Diagnosedatei gesendet und von einem Exchange 2010 UM-Server oder Exchange 2013-Postfachserver empfangen?

  - Die Metriken, die verwendet wurden, als der Medien- oder Audioqualitätsdatenstrom empfangen wurde.

Das UM-Problembehandlungstool emuliert eingehende Anrufe und führt eine Reihe von Diagnosetests aus, mit denen lokale Administratoren sowie Mandantenadministratoren den Anruffluss für eine Anrufbeantwortung testen und Konfigurationsfehler aufspüren können. Das UM-Problembehandlungstool kann zwar für Anrufbeantwortungsszenarien verwendet werden, aber nicht für die folgenden Arten von Anrufen:

  - Outlook Voice Access-Anrufe, so auch Anrufe, in denen auf Voicemail, E-Mail, Kalender, das Verzeichnis, persönliche Kontakte oder persönliche Optionen zugegriffen wird

  - Automatische UM-Telefonzentralen

  - Wiedergabe über Telefon

  - Mailboxansageregeln

  - Faxanrufe

  - Ansagenbereitstellung

Übersicht

## Architektur der UM-Problembehandlung

Mit dem UM-Problembehandlungstool können Sie Konfigurationsprobleme in einer standortübergreifenden Bereitstellung diagnostizieren und beheben, außerdem können Sie das Tool in lokalen Unified Messaging-Bereitstellungen verwenden. In einer standortübergreifenden Bereitstellung prüft das Tool auch zugehörige SBC-Konfigurationen (Session Border Controller). Der Administrator kann alle Unified Messaging-Komponenten testen, die von Unified Messaging verwendet werden, so auch die SBCs.

## VoIP-Gateways und IP-PBX-Bereitstellungen

Im folgenden Beispiel wird der Gateway-Modus verwendet, um den Anruffluss in einer Umgebung ohne Office Communications Server 2007 R2 oder Lync Server zu testen. In diesem Beispiel werden die Telefonieausrüstung (VoIP-Gateways, PBX- und IP-PBX-Anlagen) sowie die Unified Messaging-Komponenten getestet. In dem Beispiel wird der VoIP-Sicherheitsmodus (Voice over IP) auf "Ungesichert" festgelegt, wird die IP-Adresse 10.1.1.1 als nächster Hop festgelegt und wird eine Durchwahlnummer in die Umleitungsinformationen eingefügt.

    Test-ExchangeUMCallFlow -Mode Gateway -VoIPSecurity Unsecured -NextHop 10.1.1.1 -Diversion 12345

Übersicht

## Office Communications Server 2007 R2- und Microsoft Lync Server-Bereitstellungen

Wenn der SIPClient-Modus verwendet wird, kann das UM-Problembehandlungstool in lokalen oder standortübergreifenden Bereitstellungen verwendet werden, die Office Communications Server 2007 R2 oder Microsoft Lync Server umfassen. Im folgenden Beispiel wird der SIPClient-Modus verwendet, und es wird der Anruffluss mit gesicherten UM-Wähleinstellungen in einer Umgebung getestet, die Server mit Office Communications Server 2007 R2 oder mit Lync Server enthält. Wenn Sie das UM-Problembehandlungstool ausführen, verwendet es standardmäßig die Anmeldeinformationen des Benutzers, der momentan beim Computer angemeldet ist. Wenn Sie das folgende Beispiel ausführen, werden Sie zur Eingabe der Anmeldeinformationen aufgefordert, die Sie für das Ausführen des UM-Problembehandlungstools verwenden möchten. Weitere Informationen finden Sie unter [Festlegen der Anmeldeinformationen zur Verwendung mit dem Exchange UM-Problembehandlungstool](set-the-credentials-to-use-with-the-exchange-um-troubleshooting-tool-exchange-2013-help.md).

    Test-ExchangeUMCallFlow -Mode SIPClient -VoIPSecurity Secured -CallingParty tony@contoso.com -CalledParty david@contoso.com -Credential $get

## Installieren des UM-Problembehandlungstools

Das UM-Problembehandlungstool kann auf einem lokalen Unified Messaging-Server oder auf einem anderen 64-Bit-Computer unter folgendem Betriebssystem installiert werden:

  - Betriebssystem Windows 7 oder Windows 8

  - Windows Server 2008 oder Windows Server 2008 R2

  - Das Windows Server 2012- oder Windows Server 2012 R2-Betriebssystem

Wenn Sie das UM-Problembehandlungstool unter einer 64-Bit-Version von Windows 7 oder Windows 8 oder unter der 64-Bit-Edition von Windows Server 2008 verwenden möchten, können Sie das UM-Problembehandlungstool erst installieren, nachdem Sie die folgenden Komponenten installiert haben:

  - Microsoft .NET Framework 3.5 Service Pack 1 (SP1). Informationen finden Sie unter [Microsoft .NET Framework 3.5 Service Pack 1](https://go.microsoft.com/fwlink/p/?linkid=152380).
    

    > [!NOTE]
    > Wenn das Tool auf einem Computer unter Windows Vista oder Windows Server 2008 ausgeführt werden soll, finden Sie entsprechende Informationen unter <A href="https://go.microsoft.com/fwlink/p/?linkid=178998">Update der Microsoft .NET Framework 3.5-Familie für Windows Vista x64 und Windows Server 2008 x64</A>.



  - Windows-Remoteverwaltung (WinRM) 2.0 und Windows PowerShell V2 (Windows6.0-KB968930.msu).   Informationen finden Sie im Microsoft Knowledge Base-Artikel 968930, [Windows-Verwaltungsframework-Kernpaket (Windows PowerShell 2.0 und WinRM 2.0)](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=968930).

  - Microsoft Unified Communications Managed API 2.0 Core Runtime (UcmaRuntimeWebDownloadX64.msi). Informationen finden Sie unter [Unified Communications Managed API 2.0, Core Runtime (64-Bit)](https://go.microsoft.com/fwlink/p/?linkid=198175).

Das UM-Problembehandlungstool (Cmdlet **Test-ExchangeUMCallFlow**) befindet sich weder auf der Exchange 2010 SP1-DVD noch in den Downloaddateien, die nur Exchange 2010 beinhalten, noch auf den Exchange 2013-Installationsmedien. Sie können das UM-Problembehandlungstool aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=182625) herunterladen.

Weitere Informationen finden Sie unter [Installieren des Exchange UM-Problembehandlungstools](install-the-exchange-um-troubleshooting-tool-exchange-2013-help.md).

Übersicht

## Cmdlet-Parameter

In der folgenden Tabelle sind die Parameter, die Sie mit dem Cmdlet **Test-ExchangeUMCallFlow** verwenden können, sowie Beschreibungen dieser Parameter aufgelistet. Außerdem können Sie in der Shell den Befehl `Get-help Test-ExchangeUMCallFlow -detailed` verwenden, um zu jedem Parameter, der mit dem Cmdlet **Test-ExchangeUMCallFlow** verwendet werden kann, ausführliche Informationen sowie Verwendungsbeispiele abzurufen.

### Parameter

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>CalledParty</em></p></td>
<td><p>Im Parameter <em>CalledParty</em> wird der SIP-URI des Office Communications Server 2007 R2- oder Lync Server-Benutzers angegeben, für den Enterprise-VoIP aktiviert wurde. Dies ist der Benutzer, an den das Cmdlet <strong>Test-ExchangeUMCallFlow</strong> den Sprachanruf richtet. Beispiel: <code>-CalledParty tonysmith@contoso.com</code>. Verwenden Sie diesen Parameter, wenn Sie das Tool im SIPClient-Modus ausführen.</p></td>
</tr>
<tr class="even">
<td><p><em>CallingParty</em></p></td>
<td><p>Im Parameter <em>CallingParty</em> wird der SIP-URI des Office Communications Server 2007 R2- oder Lync Server-Benutzers angegeben, für den Enterprise-VoIP aktiviert wurde. Dies ist der Benutzer, der den eingehenden Anruf tätigt. Beispiel: <code>-CallingParty tonysmith@contoso.com</code>. Verwenden Sie diesen Parameter, wenn Sie das Tool im SIPClient-Modus ausführen.</p></td>
</tr>
<tr class="odd">
<td><p><em>Diversion</em></p></td>
<td><p>Im Parameter <em>Diversion</em> wird die Zeichenfolge angegeben, die als Umleitungsinformationen für den eingehenden Anruf gesendet werden soll. Dies kann in Form einer &quot;Diversion&quot;- oder &quot;History-Info&quot;-Kopfzeile erfolgen. Die Umleitungsinformationen, die im eingehenden Anruf enthalten sind, können aus einer Durchwahl bestehen oder weitere Umleitungsinformationen enthalten.</p>
<p>Wenn Sie die Umleitungsinformationen als &quot;History-Info&quot;-Kopfzeile angeben, müssen Sie Folgendes überprüfen:</p>
<ul>
<li><p>Es sind mindestens zwei verschiedene Einträge mit unterschiedlichen Benutzerangaben vorhanden.</p></li>
<li><p>Der letzte Eintrag enthält die Pilotnummer der UM-Wähleinstellungen des Benutzers.</p></li>
<li><p>Der vorletzte Eintrag enthält die Durchwahlnummer des UM-aktivierten Benutzers. Dieser Eintrag muss außerdem den geeigneten Text für den Grund (Reason) enthalten. Der Text muss ordnungsgemäße Escapezeichen gemäß den Escaperegeln für Standard-URL-Parameter enthalten.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><em>Mode</em></p></td>
<td><p>Der Parameter <em>Mode</em> gibt an, ob der Modus für VoIP-Gateway, IP-PBX-Anlage oder für Office Communications Server 2007 R2 oder Lync Server verwendet werden soll. Sie können den Gateway-Modus angeben, wenn Ihre UM-Bereitstellung VoIP-Gateways oder IP-PBX-Anlagen einschließt, oder den SIPClient-Modus, wenn Ihre UM-Bereitstellung Office Communications Server 2007 R2 oder Lync Server einschließt.</p></td>
</tr>
<tr class="odd">
<td><p><em>NextHop</em></p></td>
<td><p>Der Parameter <em>NextHop</em> gibt die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des nächsten Hops an und kann außerdem den TCP-Port für den nächsten Hop einschließen, mit dem das Cmdlet <strong>Test-ExchangeUMCallFlow</strong> beim Emulieren des VoIP-Gateways oder der IP-PBX-Anlage eine Verbindung herstellen muss. Wenn Sie den TCP-Port einschließen, müssen Sie Port 5060 für den Modus &quot;Ungesichert&quot; oder Port 5061 für den Modus &quot;SIP-gesichert&quot; angeben. Beispiel: <code>gateway.contoso.com:5061</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>CertificateThumbprint</em></p></td>
<td><p>Der Parameter <em>CertificateThumbprint</em> gibt den Fingerabdruck des Zertifikats an, das für TLS (Transport Layer Security) verwendet wird. Dieser Abdruck ist erforderlich, wenn für die UM-Wähleinstellungen der Modus &quot;SIP-gesichert&quot; oder &quot;Gesichert&quot; konfiguriert ist. Dieser Zertifikatfingerabdruck gehört zu dem Zertifikat, das vom VoIP-Gateway, von der IP-PBX-Anlage oder vom SBC exportiert wurde. Außerdem muss der Computer, auf dem das UM-Problembehandlungstool installiert ist und der zum Testen des Anrufflusses verwendet wird, dem von der Zertifizierungsstelle ausgegebene Zertifikat für den nächsten Hop vertrauen.</p></td>
</tr>
<tr class="odd">
<td><p><em>Credential</em></p></td>
<td><p>Der Parameter <em>Credential</em> gibt die Anmeldeinformationen für die Ausführung des Cmdlets an.</p></td>
</tr>
<tr class="even">
<td><p><em>HuntGroup</em></p></td>
<td><p>Der Parameter <em>HuntGroup</em> gibt den UM-Sammelanschluss an, der dem emulierten VoIP-Gateway zugeordnet ist. Dies ist im Allgemeinen eine Durchwahlnummer. Verwenden Sie diesen Parameter, wenn Sie das Tool im Gateway-Modus ausführen.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoIPSecurity</em></p></td>
<td><p>Der Parameter <em>VoIPSecurity</em> gibt den Sicherheitsmodus an, wenn das Cmdlet im Gateway-Modus verwendet wird. Sie können einen der folgenden VoIP-Sicherheitsmodi verwenden:</p>
<ul>
<li><p>Gesichert (TLS/SRTP)</p></li>
<li><p>Ungesichert (TCP/RTP) (Standard)</p></li>
<li><p>SIP-gesichert (TLS/RTP)</p></li>
</ul></td>
</tr>
</tbody>
</table>


Übersicht

