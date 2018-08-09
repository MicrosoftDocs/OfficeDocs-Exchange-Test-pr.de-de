---
title: 'Bereitst. v. Exchange 2013 UM u. Lync-Server (Übersicht): Exchange 2013-Hilfe'
TOCTitle: Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)
ms:assetid: 96fcb0dd-79ee-4e55-9e59-3ee7fbe3c4a1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb676409(v=EXCHG.150)
ms:contentKeyID: 50476292
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Unified Messaging (UM) und Microsoft Lync Server können zusammen bereitgestellt werden, um Benutzern in der Organisation Voicemessaging, Instant Messaging, erweiterte Anwesenheitsfunktionen, Audio-/Videokonferenzen sowie integrierte E-Mail- und Messagingfunktionen bereitzustellen. Unified Messaging wird verwendet, um Funktionen wie Mailboxansage für Voicemail, Outlook Voice Access und automatische Telefonzentrale bereitzustellen. Microsoft Lync Server bietet weitere, erweiterte Funktionen in Enterprise-VoIP, wie Instant Messaging, Konferenzen sowie ein- und ausgehende Anrufe. In diesem Thema wird erläutert, wie Sie Unified Messaging und Microsoft Lync Server für die Unterstützung dieser Funktionen konfigurieren.


> [!TIP]
> Microsoft Office Communications&nbsp;Server 2007&nbsp;R2 kann ebenfalls zusammen mit Unified Messaging bereitgestellt werden. In diesem Thema steht "Microsoft Lync Server" für Microsoft Lync Server&nbsp;2010 oder Microsoft Lync Server&nbsp;2013.



Benötigen Sie weitere Informationen zu Microsoft Lync Server? Siehe [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752).

**Inhalt**

Bereitstellen von Exchange UM und Lync-Server (Übersicht)

Empfehlungen für die Zertifikatkonfiguration

Bereitstellungsschritte

Weitere Informationen

## Bereitstellen von Exchange UM und Lync-Server (Übersicht)

Unified Messaging kombiniert Voicemessaging und E-Mail-Messaging zu einer einzelnen Messaginginfrastruktur. Microsoft Lync Server Enterprise Voice nutzt die UM-Infrastruktur, um Voicemail, Outlook Voice Access, Anrufbenachrichtigungen und automatische Telefonzentralen bereitzustellen.

Die folgende Liste zeigt die vereinfachten Bereitstellungsschritte für UM und Lync Server. Einzelheiten zu den einzelnen Schritten sind weiter unten in diesem Thema enthalten.

1.  Installieren Sie Microsoft Lync Server in der Topologie, in der die Clientzugriffsserver mit dem Microsoft Exchange Unified Messaging-Anrufrouterdienst und die Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst installiert werden sollen. Stellen Sie sicher, dass mindestens ein Lync-Pool erstellt wird.

2.  Installieren Sie ein gültiges Zertifikat, das von einer privaten oder öffentlichen Zertifizierungsstelle ausgegeben wurde und für das in Lync Server eine Vertrauensstellung vorhanden ist.

3.  Installieren Sie die Clientzugriffsserver und Postfachserver. Überprüfen Sie die Installation.

4.  Installieren Sie ein gültiges Zertifikat, das von derselben Zertifizierungsstelle signiert ist wie das auf den Lync-Servern installierte Zertifikat.

5.  Erstellen und konfigurieren Sie einen URI-Wählplan für Session Initiation Protocol (SIP).

6.  Fügen Sie dem SIP-URI-Wählplan alle Clientzugriffsserver und Postfachserver hinzu. Wenn Sie über mehrere SIP-URI-Wählpläne verfügen, müssen Sie allen SIP-URI-Wählplänen alle Clientzugriffsserver und Postfachserver hinzufügen.

7.  Führen Sie das Skript "ExchUcUtil.ps1" aus dem Ordner "\<Exchange-Installationsordner\>\\Exchange Server\\Script" auf einem Postfachserver aus.
    

    > [!IMPORTANT]
    > Das Skript "ExchUcUtil.ps1" erstellt ein oder mehrere UM-IP-Gateways für die Lync-Integration. Sie müssen ausgehende Anrufe für alle UM-IP-Gateways deaktivieren, außer dem einen Gateway, das durch das Skript erstellt wurde. Dazu gehört auch das Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways, die vor dem Ausführen des Skripts erstellt wurden. Informationen zum Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways finden Sie unter <A href="disable-outgoing-calls-on-um-ip-gateways-exchange-2013-help.md">Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways</A>.



8.  Führen Sie **OcsUmUtil.exe** aus dem Ordner "%CommonProgramFiles%\\Microsoft Lync Server 2013\\Support" auf einem Lync-Server aus.

9.  Stellen Sie den Vermittlungsserver und die Mediengateways bereit.

10. Installieren Sie auf dem Vermittlungsserver ein gültiges Zertifikat, das von derselben Zertifizierungsstelle signiert ist wie das auf den Lync-Servern installierte Zertifikat.

11. Aktivieren Sie Ihre Benutzer für UM und Enterprise-VoIP.

## Empfehlungen für die Zertifikatkonfiguration

Sie müssen über ein Zertifikat verfügen, für das auf den Computern mit Exchange und den Computern mit Lync Server eine Vertrauensstellung vorhanden ist. Befolgen Sie in einer Umgebung mit Lync Server und Unified Messaging die folgenden Richtlinien für die Bereitstellung eines vertrauenswürdigen Zertifikats:

  - Importieren Sie auf den Lync-Servern, Clientzugriffsservern, Postfachservern, dem Vermittlungsserver und den Mediengateway ein gültiges Zertifikat, das von einer privaten oder öffentlichen Zertifizierungsstelle signiert ist. Hierbei sollte es sich um ein vertrauenswürdiges Zertifikat eines kommerziellen Drittanbieters oder ein Zertifikat der Public Key-Infrastruktur (PKI) handeln.

  - Die Komplexität wird verringert, wenn Sie dasselbe derartige Zertifikat auf jeden Exchange-Server importieren. Installieren Sie dieses vertrauenswürdige Zertifikat auf jedem Microsoft Lync-Server und Vermittlungsserver. Dies verringert die Komplexität der Zertifikatbereitstellung und den Verwaltungsaufwand im Zusammenhang mit der Bereitstellung von Zertifikaten. Achten Sie darauf, dass Sie ein vertrauenswürdiges Zertifikat beziehen, das alternative Antragstellernamen (Subject Alternative Name, SAN) unterstützt.
    
    Wenn Sie Transport Layer Security (TLS) mit UM bereitstellen, müssen die auf dem Clientzugriffsserver und dem Postfachserver verwendeten Zertifikate den vollqualifizierten Domänennamen (FQDN) des lokalen Computers im Antragstellernamen des Zertifikats enthalten. Verwenden Sie als Problemumgehung ein öffentliches Zertifikat, und importieren Sie es auf allen Clientzugriffsservern und Postfachservern, VoIP-Gateways, IP-Nebenstellenanlagen und Lync-Servern.
    
    Wenn Ihre Bereitstellung VoIP-Gateways oder IP-Nebenstellenanlagen einschließt und Sie einen SIP-gesicherten oder gesicherten Wählplan verwenden, ist ein vertrauenswürdiges Zertifikat zwischen den Clientzugriffs- und Postfachservern und den VoIP-Gateways oder IP-Nebenstellenanlagen erforderlich. Ein vertrauenswürdiges Zertifikat ist außerdem erforderlich, wenn eine direkte SIP-Verbindung verwendet wird. Wenn Sie einen SIP-gesicherten oder gesicherten Wählplan verwenden, können Sie dasselbe vertrauenswürdige Zertifikat für Ihre Lync- und Exchange-Server verwenden wie für Ihre VoIP-Gateways oder IP-Nebenstellenanlagen.

  - Wenn Exchange-Clientzugriffs- und Postfachserver eine Verbindung mit Microsoft Lync-Servern oder mit SIP-Gateways oder Nebenstellenanlagen (Private Branch eXchange, PBX) von Drittanbietern herstellen, müssen Sie zum Einrichten geschützter Sitzungen ein gültiges Zertifikat verwenden, das von einer internen oder öffentlichen externen Zertifizierungsstelle signiert wurde. Sie können ein einzelnes Zertifikat auf allen Clientzugriffs- und Postfachservern verwenden, sofern in der SAN-Liste des Zertifikats die FQDNs aller Clientzugriffs- und Postfachserver enthalten sind. Alternativ können Sie für jeden Clientzugriffs- und Postfachserver ein anderes Zertifikat generieren, bei dem der FQDN des lokalen Computers sich im allgemeinen Namen (Common Name, CN) des Antragstellers oder in der SAN-Liste für das Zertifikat dieses Servers befindet. Exchange UM unterstützt keine Platzhalterzertifikate mit Microsoft Lync Server.
    
    Damit Lync Server und Exchange zusammenarbeiten können, ist ein Antragstellername erforderlich, der kein Platzhalter ist. UM und Lync Server verwenden den Antragstellernamen, um die Vertrauensstellung als SIP-Peers anzuzeigen. Lync Server benötigt auch in einigen Call-Routing-Szenarien einen Antragstellernamen, der kein Platzhalter ist. Der FQDN muss als Wert für "Ausgestellt für" verwendet werden.
    
    Für Exchange UM wird als Zertifikatname kein Platzhalter unterstützt. Sie können jedoch einen Platzhalter im SAN verwenden.

Die folgende Tabelle zeigt die Zertifikatanforderungen für das Installieren und Konfigurieren von Zertifikaten für Exchange UM.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topologie</th>
<th>Zertifikatkonfiguration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriffsserver und Postfachserver auf demselben Server (ohne Lync 2010 und 2013; Nicht-SIP-Wählpläne)</p></td>
<td><p>Ein Zertifikat ist zwischen Clientzugriffsservern und Postfachservern erforderlich. Hierbei handelt es sich um dasselbe Zertifikat, wie zwischen dem Clientzugriffsserver und Postfachserver und dem VoIP-Gateway, der IP-Nebenstellenanlage oder dem SBC verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriffsserver und Postfachserver auf verschiedenen Servern (ohne Lync 2010 und 2013; Nicht-SIP-Wählpläne)</p></td>
<td><p>Es ist ein Zertifikat erforderlich. Das Zertifikat muss auf dem Clientzugriffsserver und dem Postfachserver übereinstimmen. Außerdem ist ein Zertifikat zwischen dem Clientzugriffsserver und Postfachserver und dem VoIP-Gateway, der IP-Nebenstellenanlage oder dem SBC erforderlich. Hierbei kann es sich um dasselbe Zertifikat handeln, wie zwischen dem Clientzugriffsserver und Postfachserver verwendet wird, oder um ein anderes. Für Clientzugriffs- und Postfachserver können Sie das Cmdlet <strong>Create-ExchangeCertificate</strong> auf einem der beiden Server ausführen.</p></td>
</tr>
<tr class="odd">
<td><p>Clientzugriffsserver und Postfachserver auf demselben Server (mit Lync 2010 oder 2013 und SIP-Wählplänen)</p></td>
<td><p>Es ist ein Zertifikat erforderlich. Der Clientzugriffs- und der Postfachserver müssen über dasselbe Stammzertifikat verfügen wie die Lync 2010- oder Lync 2013-Server.</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriffsserver und Postfachserver auf unterschiedlichen Servern (mit Lync 2010 oder 2013 und SIP-Wählplänen)</p></td>
<td><p>Es ist ein Zertifikat erforderlich. Der Clientzugriffs- und der Postfachserver müssen über dasselbe Stammzertifikat verfügen wie die Lync 2010- oder Lync 2013-Server.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Bereitstellungsschritte

Nach dem Installieren der erforderlichen Server in Ihrer Organisation müssen Sie eine empfohlene Abfolge von Schritten in Ihren Exchange Unified Messaging- und Lync Server-Bereitstellungen durchführen, um Enterprise-VoIP für Benutzer korrekt bereitzustellen.

Weitere Informationen zu Microsoft Lync Server finden Sie unter [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752).

Sie müssen die folgenden Schritte durchführen, um Unified Messaging für die Zusammenarbeit mit den Enterprise-VoIP-Funktionen in Lync Server zu konfigurieren:

1.  Erstellen Sie einen oder mehrere SIP-URI-Wählpläne von Unified Messaging, die jeweils einem entsprechenden Lync Server-Standortprofil zugeordnet sind. Ein Enterprise-VoIP-Standortprofil muss für jeden Satz Exchange UM-Wähleinstellungen erstellt werden. Sie können mit dem Cmdlet **Get-UMDialPlan** den FQDN eines SIP-URI-Wählplans abrufen. Weitere Informationen zum Erstellen von SIP-URI-Wähleinstellungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Wenn Sie Exchange UM und Lync Server integrieren, ist es im Allgemeinen unnötig, Wählregeln oder Wählregelgruppen in Exchange UM zu konfigurieren. Lync Server ist dazu entworfen, das Anrufrouting und die Nummernübersetzung für Benutzer in Ihrer Organisation durchzuführen, und übernimmt diese Aufgaben auch, wenn Unified Messaging Anrufe im Namen von Benutzern tätigt.



2.  Installieren Sie auf dem Clientzugriffs- und Postfachserver ein gültiges Zertifikat, das von einer privaten oder öffentlichen Zertifizierungsstelle signiert wurde. Dies ist die derselben Zertifizierungsstelle, die auf den Lync-Servern verwendet wurde.

3.  Verschlüsseln Sie den VoIP-Datenverkehr (Voice over IP), indem Sie die SIP-URI-Wähleinstellungen als "SIP-gesichert" oder "Gesichert" konfigurieren.
    

    > [!WARNING]
    > Wenn Sie als Sicherheitseinstellung "SIP-gesichert" festlegen, um die Verschlüsselung ausschließlich für den SIP-Datenverkehr erforderlich zu machen, ist diese Einstellung für einen Wählplan unzureichend, wenn der Front-End-Pool so konfiguriert ist, dass er die Verschlüsselung erfordert (dies bedeutet, dass der Pool die Verschlüsselung von SIP- und RTP-Datenverkehr erfordert). Wenn die Sicherheitseinstellungen für den Wählplan und den Pool nicht kompatibel sind, schlagen alle Exchange UM-Aufrufe vom Front-End-Pool fehl; dabei wird die Fehlermeldung "Inkompatible Sicherheitseinstellung" ausgegeben.

    
    Obwohl es möglich ist, einen UM-Wählplan als "SIP-gesichert" oder "Gesichert" zu konfigurieren, wird empfohlen, den Wählplan als "Gesichert" zu konfigurieren, damit Lync Phone Edition-Geräte korrekt funktionieren. Dies wird aufgrund der Standardeinstellungen für die Verschlüsselungsebene empfohlen, die in Lync Server konfiguriert sind. Ein Lync Phone Edition-Gerät funktioniert nur, wenn die Verschlüsselungseinstellungen so konfiguriert sind wie in der folgenden Tabelle gezeigt. Diese Tabelle stellt die Beziehung zwischen den Verschlüsselungseinstellungen für Lync Server und für UM-Wählpläne dar.
    
    **Verschlüsselungseinstellungen für Lync Phone Edition**
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Lync Server</th>
    <th>UM-Wähleinstellungen</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Verschlüsselung erforderlich (Standard)</p></td>
    <td><p>Gesichert</p></td>
    </tr>
    <tr class="even">
    <td><p>Verschlüsselung optional</p></td>
    <td><p>SIP-gesichert/Gesichert</p></td>
    </tr>
    <tr class="odd">
    <td><p>Keine Verschlüsselung</p></td>
    <td><p>SIP-gesichert</p></td>
    </tr>
    </tbody>
    </table>


4.  Fügen Sie dem SIP-Wählplan alle Clientzugriffsserver und Postfachserver hinzu. Damit der Server eingehende Anrufe beantworten kann, müssen Sie alle Exchange-Server zu einem Wählplan hinzufügen, wenn sie Anrufe von Lync Server beantworten sollen.

5.  Legen Sie den Startmodus und den TLS-Überwachungsport für die Clientzugriffsserver und Postfachserver, die dem SIP-URI-Wählplan hinzugefügt werden, auf "Dual" fest, und starten Sie dann den MicrosoftExchange Unified Messaging-Dienst auf jedem Postfachserver und den MicrosoftExchange Unified Messaging-Anrufrouterdienst auf jedem Clientzugriffsserver neu.

6.  Erstellen und konfigurieren Sie eine automatische UM-Telefonzentrale. Weitere Informationen finden Sie unter [Einrichten einer automatischen UM-Telefonzentrale](set-up-a-um-auto-attendant-exchange-2013-help.md).

7.  Erstellen Sie beim Aktivieren von Benutzern für Voicemail eine SIP-Adresse für die Benutzer, die Enterprise-VoIP verwenden werden. In den meisten Fällen ist dies die SIP-Adresse, die auch verwendet wird, wenn ein Benutzer für Enterprise-VoIP aktiviert wird. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Benutzer, die SIP-URI-Wähleinstellungen zugeordnet sind, können keine eingehenden Faxnachrichten empfangen. Der Grund ist, dass eingehende Sprach- und Faxanrufe über einen Vermittlungsserver weitergeleitet werden und dass hierbei die Faxfunktion nicht unterstützt wird.



8.  Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie das Skript "exchucutil.ps1" aus, das sich im Ordner "%ProgramFiles%\\Microsoft\\Exchange Server\\V15\\Scripts" befindet. Das Skript "exchucutil.ps1" führt Folgendes aus:
    
      - Es erteilt Lync Server die Berechtigung zum Lesen von Exchange UM Active Directory-Komponenten, insbesondere dem in der vorigen Aufgabe erstellten SIP-URI-Wählplan. Weitere Informationen zum Konfigurieren von Berechtigungen in Active Directory finden Sie unter [Anwenden von Berechtigungen mithilfe von ADSI-Bearbeitung](https://go.microsoft.com/fwlink/p/?linkid=82751).
    
      - Es erstellt einen UM-IP-Gateway für jeden Lync Server-Pool oder für jeden Server, auf dem Lync Server Standard Edition als Host für Enterprise-VoIP-aktivierte Benutzer ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).
    
      - Es erstellt einen Exchange UM-Sammelanschluss für jedes UM-IP-Gateway. Dabei wird die Pilot-ID des Sammelanschlusses als Name des Wählplans verwendet, der dem entsprechenden UM-IP-Gateway zugeordnet ist. Für den Sammelanschluss muss der UM-IP-Wählplan angegeben werden, der mit dem UM-IP-Gateway verwendet wird.

9.  Es aktiviert Benutzer für Voicemail. Stellen Sie dabei sicher, dass Sie eine gültige SIP-Adresse für den Benutzer eingeben und ihn mit einem SIP-Wählplan verknüpfen. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

Führen Sie außerdem die folgenden Aufgaben aus, um Lync Server für die Verwendung mit Exchange UM zu konfigurieren:

  - Erstellen Sie Standortprofile oder Lync-Wählpläne. Der Name des Standortprofils muss nicht dem vollständig qualifizierten Domänennamen der jeweiligen UM-Wählpläne entsprechen.

  - Weisen Sie die Standortprofile den Lync Server-Pools zu.

  - Stellen Sie Mediengateways oder Vermittlungsserver bereit, und konfigurieren Sie diese. Außerdem müssen Sie ein Zertifikat von der vertrauenswürdigen Zertifizierungsstelle importieren, die auch für die Zertifikate der Clientzugriffs- und Postfachserver sowie für Lync Server verwendet wurde.

  - Definieren Sie die Telefonverwendung. Erstellen Sie VoIP-Richtlinien und Routen für ausgehende Anrufe, und weisen Sie sie zu.

  - Konfigurieren Sie die Benutzer für Enterprise-VoIP, und fügen Sie eine TEL-URI sowie eine SIP-ID hinzu.

  - Führen Sie die Datei **ocsumutil.exe** aus, die die Kontaktobjekte für Outlook Voice Access und für die automatischen Telefonzentralen erstellt.
    

    > [!NOTE]
    > Bei der Installation von Lync Server wird Active Directory das Attribut <STRONG>msRTC-SIPLine</STRONG> hinzugefügt. Wenn Lync Server nicht in der Umgebung installiert ist, wird dieses Attribut Active Directory&nbsp;nicht hinzugefügt, und die wählplanübergreifende Namensauflösung der Anrufer-ID in Szenarien mit einzelner Gesamtstruktur und in gesamtstrukturübergreifenden Szenarien funktioniert nicht einwandfrei, sofern Sie keine Unified Messaging-Proxyadressen für Benutzer konfigurieren, die nicht UM-aktiviert sind.



Nach Abschluss der Konfiguration von Lync Server und den Unified Messaging-Servern müssen Sie den Benutzer zur Verwendung von Lync Server aktivieren und Lync auf dem Clientcomputer des Benutzers installieren.


> [!IMPORTANT]
> Wenn Sie Unified Messaging und Lync Server integrieren, stehen Benachrichtigungen über verpasste Anrufe nicht für Benutzer zur Verfügung, die über ein Postfach auf einem Exchange&nbsp;2007- oder Exchange&nbsp;2010-Postfachserver verfügen. Es wird eine Benachrichtigung über einen verpassten Anruf generiert, wenn ein Benutzer sich abmeldet, bevor der Anruf an einen Postfachserver gesendet wurde.



Zurück zum Seitenanfang

## Weitere Informationen

Weitere Informationen zum Durchführen der für Microsoft Lync Server erforderlichen Aufgaben finden Sie unter [Microsoft Lync Server](https://go.microsoft.com/fwlink/p/?linkid=265752).

