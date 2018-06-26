---
title: 'Anzeige für wartende Nachrichten zulassen: Exchange 2013 Help'
TOCTitle: Anzeige für wartende Nachrichten zulassen
ms:assetid: 57fb439e-8208-499f-a20b-814677843a8c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298001(v=EXCHG.150)
ms:contentKeyID: 54652686
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeige für wartende Nachrichten zulassen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

MWI (Message Waiting Indicator) ist eine Funktion, die sich bei den meisten Voicemail-Legacysystemen findet. Benutzer erfahren so, ob sie neue oder nicht abgehörte Sprachnachrichten haben. In der Regel wird dabei durch eine Leuchtanzeige am Telefon eines Benutzers signalisiert, dass eine neue oder nicht abgehörte Sprachnachricht vorliegt.

**Inhalt**

Übersicht

Rolle des Postfachservers in MWI

MWI-spezifische SIP NOTIFY-Nachrichten

MWI-Ausfallsicherheit

MWI-Verwaltung

SMS-Benachrichtigungen für Voicemailnachrichten und verpasste Anrufe

## Übersicht

MWI-Benachrichtigungen können Mechanismen enthalten, die das Vorhandensein neuer oder nicht abgehörter Sprachnachrichten anzeigen. Die Nachricht kann in einer neuen oder als ungelesen markierten E-Mail-Nachricht eingebettet sein. Die MWI-Benachrichtigung kann in einer der folgenden Formen auftreten:

  - Eine von Microsoft Outlook oder Outlook Web App aus gesehen neue Sprachnachricht.

  - Ein an ein Mobiltelefon gesendeter Text bzw. eine SMS (Short Messaging Service), wobei das Mobiltelefon für den Empfang von Textnachrichten konfiguriert ist.

  - Ein aus Exchange Unified Messaging (UM) ausgehender Anruf.

  - Ein optische Anzeige auf einem Telefon.

  - Besonderer Klingelton

  - Symbole oder Schaltflächen im Telefondisplay

  - Hervorgehobene Signalisierung in einer Softwareanwendung

Die Sprachnachricht eines Benutzers wird in UM in dessen Postfach gespeichert. Der Zugriff kann über ein Telefon mit Outlook Voice Access, über einen Desktop-Computer oder einen Laptop mit Outlook oder Outlook Web App sowie Mobiltelefonclients erfolgen. Wenn ein Benutzer eine neue Sprachnachricht empfängt, wird diese in seinem Voicemailsuchordner angezeigt. Wenn er mit Outlook oder Outlook Web App auf die Sprachnachricht zugreift, wird die Sprachnachricht um eine E-Mail-Nachricht ergänzt.

Bei der Bereitstellung von früheren UM-Versionen in einer Organisation wurde MWI entweder in einer herkömmlichen VoIP-Gatewayumgebung oder in einer IP-PBX-Umgebung durch eine Drittanbieterlösung oder -anwendung unterstützt, oder er war Teil des Exchange UM In Exchange 2010 oder höher wird MWI auch dann unterstützt, wenn UM mit Microsoft Lync Server bereitgestellt wurde. Der MWI-Benachrichtigungsmechanismus von Lync Server hängt vom Typ des VoIP-basierten Telefons ab, das der Enterprise-VoIP- und UM-aktivierte Benutzer verwendet. Dieser Mechanismus kann sich an folgenden Stellen befinden:

  - Auf einem Telefon

  - Auf einem Telefondisplay

  - Auf einer Wähltaste

MWI ist standardmäßig für alle Benutzer eingeschaltet, die UM-aktiviert sind. Er wird über Einstellungen in einer UM-Postfachrichtlinie oder in UM-IP-Gateways gesteuert, die erstellt und mit einem UM-Wählplan verknüpft wurden. MWI kann auch zusammen mit geschützten Sprachnachrichten verwendet werden.

Für eine Implementierung von MWI in einer herkömmlichen Telefonieumgebung mit VoIP-Gateways, IP-Festnetztelefonanlagen oder SIP-fähigen PBX-Anlagen sendet ein Postfachserver, der den Microsoft Exchange Unified Messaging-Dienst ausführt, eine MWI-SIP-NOTIFY-Benachrichtigung an einen *SIP-Peer*, der entweder eine IP-Festnetztelefonanlage, ein VoIP-Gateway mit Legacy-PBX-Anlage, eine SIP-fähige PBX-Anlage oder, falls Lync Server bereitgestellt, ein Lync-Server ist. In der IP-Festnetztelefonanlage oder PBX-Anlage leuchtet die optische Anzeige auf dem Desktoptelefon, um dem Benutzer eine neue oder nicht abgehörte Nachricht zu melden.

Benutzer haben zwei Möglichkeiten, Sprachnachrichten zu hinterlassen: über die Mailboxansage und Outlook Voice Access. Über die Mailboxansagefunktion beantwortet ein Postfachserver eingehende Anrufe, und der Anrufer kann eine Sprachnachricht für einen Benutzer hinterlassen. Bei Outlook Voice Access kann der Anrufer eine Outlook Voice Access-Nummer anrufen und über das Menüsystem eine Sprachnachricht für einen UM-aktivierten Benutzer hinterlassen.

Übersicht

## Rolle des Postfachservers in MWI

Ruft ein Anrufer einen UM-aktivierten Benutzer an, und der Benutzer antwortet nicht auf den Anruf, erhält der auf einem Postfachserver gehostete Microsoft Exchange Unified Messaging-Dienst eine MWI-Statusänderungsinformation. In einer SIP NOTIFY-Nachricht sendet dieser Dienst eine Benachrichtigungsänderungsanfrage an ein VoIP-Gateway, eine IP-Festnetztelefonanlage, eine PBX-Anlage oder SIP-fähige PBX-Anlage. Die Benachrichtigungsänderung enthält die folgenden Informationen:

  - MWI (Message Waiting Indicator) aktiviert (Ja oder Nein)

  - Anzahl der neuen/als nicht abgehört markierten Sprachnachrichten.

  - Anzahl der alten/als abgehört markierten Sprachnachrichten.

  - Anzahl der neuen/als nicht abgehört markierten Sprachnachrichten mit hoher Wichtigkeit.

  - Anzahl der alten/als abgehört markierten Sprachnachrichten mit hoher Wichtigkeit.

  - Die primäre Durchwahl im primären Satz UM-Wähleinstellungen

  - Die IP-Adresse oder der vollqualifizierte Domänenname (FQDN) des SIP-Peers, der für SIP NOTIFY-Nachrichten verwendet werden soll.

  - Der Sicherheitstyp des Satzes UM-Wähleinstellungen ("Ungesichert", "SIP-gesichert" oder "Gesichert"). Anhand dieser Informationen wird ermittelt, ob der Verbindungstyp zum VoIP-Gateway oder zur IP-Festnetztelefonanlage "SIP über TCP" oder "SIP über TLS" ist. Transport Layer Security (TLS) wird für MWI SIP NOTIFY unterstützt.

Ein Postfachserver ermittelt anhand der Umleitungsinformationen in der Kopfzeile des eingehenden Anrufs die Durchwahl oder Telefonnummer des UM-aktivierten Benutzers. Wurde die Durchwahl oder Telefonnummer ermittelt, sendet der Postfachserver die Anfrage an den SIP-Peer. Der SIP-Peer ändert dann den MWI-Status und schaltet die Benachrichtigung auf dem Telefon des Benutzers ein.


> [!NOTE]
> Obwohl PBX-Anlagen nur in den seltensten Fällen ausfallen, wird der MWI-Status für jedes Postfach automatisch von UM aktualisiert, das heißt, mindestens alle 12&nbsp;Stunden. Eine Aktualisierung kann nicht erzwungen werden, aber wenn die PBX- oder IP-Festnetztelefonanlage ausgeschaltet ist und alle optischen MWI-Anzeigen erlöschen, werden alle LEDs innerhalb von sechs Stunden wieder in den richtigen Status zurückgesetzt.



Übersicht

## MWI-spezifische SIP NOTIFY-Nachrichten

Bei MWI-Benachrichtigungen werden für die Kommunikation mit SIP-Peers SIP NOTIFY-Nachrichten verwendet. Die MWI-Statusänderungsinformationen sind in der SIP NOTIFY-Nachricht enthalten und geben an, ob MWI-Benachrichtigungen an die Benutzer gesendet werden. Bei jeder Änderung des MWI-Status sendet der Postfach-Assistentendienst diese Informationen an den Microsoft Exchange Unified Messaging-Dienst, der auf einem Postfachserver ausgeführt wird. Nachdem der UM-Dienst diese Informationen empfangen hat, analysiert er die Nachricht, um den SIP-Zielpeer und die MWI-Statusänderungsinformationen zu ermitteln. Anschließend wird eine SIP NOTIFY-Nachricht mit den MWI-Statusänderungsinformationen im Textkörper erstellt und an den SIP-Peer gesendet.

MWI basiert auf RFC 3842. RFC 3842 besagt, dass für MWI-Benachrichtigungen SIP-Ereignisbenachrichtigungen verwendet werden müssen. MWI basiert auf dem SIP-Modell und wird über die Endpunkte in einem Unified Messaging-System gesteuert. SIP-Endpunkte, auch SIP-Peers genannt, die MWI-Informationen erhalten, müssen eine SIP SUBSCRIBE-Nachricht an den Unified Messaging-Dienst senden. Der Dienst antwortet mit einer NOTIFY-Nachricht, die besagt, dass das Abonnement angenommen wurde. Alle MWI-Statusänderungsinformationen werden vom Unified Messaging-System über NOTIFY-Nachrichten, die in das zuvor erstellte Abonnement eingebettet sind, an einen SIP-Endpunkt weitergeleitet. Die genaue Syntax der SIP NOTIFY-Nachricht an den SIP-Peer basiert auf dem in RFC 3842 beschriebenen Format.

Wenn der Unified Messaging-Dienst, der auf einem Postfachserver ausgeführt wird, eine MWI NOTIFY-Nachricht an den SIP-Peer sendet, wird die Ereigniskopfzeile auf "message-summary" eingestellt, was bedeutet, dass es sich um eine MWI-bezogene NOTIFY-Nachricht handelt. Im Kopfzeilenfeld "To" ist der SIP-Endpunkt angegeben, für den der MWI-Dienst bereitzustellen ist. Die Kopfzeile "Subscription-State" muss auf "terminated" und nicht auf "active" eingestellt sein. Die folgenden Aktionen geschehen als Antwort auf die SIP NOTIFY-Nachricht:

1.  Der SIP-Peer leitet diese Informationen mithilfe eines leitungsvermittelten Protokolls (z. B. SMDI) an die PBX-Anlage weiter.

2.  Die PBX-Anlage sendet über ein leitungsvermitteltes Protokoll eine Erfolgsnachricht.

3.  Der SIP-Peer antwortet mit einer der folgenden Nachrichten: 200 OK (Erfolg) oder 480 (vorübergehend nicht verfügbar). Ein Postfachserver kann diese beiden Antworten und weitere Fehlermeldungen verarbeiten.

## MWI in einer herkömmlichen Telefonieumgebung

In einer herkömmlichen Telefonieumgebung erhält die PBX-Anlage oder die IP-Festnetztelefonanlage oder eine SIP-aktivierte PBX-Anlage einen eingehenden Anruf und sendet ihn weiter an das VoIP-Gateway. Mithilfe des Postfachservers und des Postfach-Assistenten wird der MWI-Status für den UM-aktivierten Benutzer ermittelt. Sie sind für die Zustellung der SIP-Benachrichtigung an das VoIP-Gateway und die Legacy-PBX-Anlage, die IP-Festnetztelefonanlage, die PBX-Anlage oder die SIP-aktivierte PBX-Anlage zuständig.

In einer herkömmlichen Telefonieumgebung stellen sich Anruffluss und MWI-Benachrichtigung folgendermaßen dar:

1.  Der eingehende Anruf wird von der Legacy-PBX-Anlage empfangen, an das VoIP-Gateway, eine IP-Festnetztelefonanlage oder eine SIP-aktivierte PBX-Anlage weitergeleitet und von dort an die Durchwahlnummer des UM-aktivierten Benutzer weitergeleitet. Der Benutzer meldet sich nicht, und der Anrufer wird aufgefordert, eine Sprachnachricht zu hinterlassen.

2.  Das VoIP-Gateway oder die IP-Festnetztelefonanlage sendet den Anruf an einen Postfachserver mit Microsoft Exchange Unified Messaging-Dienst.

3.  Der Postfachserver ermittelt anhand einer LDAP-Abfrage die Informationen des UM-aktivierten Benutzers (z. B. Durchwahl und individuelle Begrüßung). Die Begrüßung des UM-aktivierten Benutzers wird wiedergegeben.

4.  Die vom UM-Dienst erstellte Sprachnachricht wird an den Microsoft Exchange Transport-Dienst auf demselben Postfachserver weitergegeben.

5.  Der Transportdienst auf dem Postfachserver sendet die Sprachnachricht an den Postfachserver, auf dem das Postfach des Benutzers liegt. Beim Postfach-Assistent geht ein MAPI-Ereignis für eine neue Sprachnachricht ein.

6.  Der Postfach-Assistent ermittelt anhand der UM-Wähleinstellungen und der UM-Postfachrichtlinie, ob an den UM-aktivierten Benutzer MWI-Benachrichtigungen zu senden sind. Der Postfach-Assistent fragt alle Postfachserver ab, die mit den UM-Wähleinstellungen für den UM-aktivierten Benutzer verknüpft sind. Der Postfach-Assistent versucht dann, das RPC-Ereignis an den ersten zurückgegebenen Postfachserver zu senden. Treten Fehler auf, setzt er den Versuch beim nächsten Server fort. Die Versuche werden 5 Minuten lang fortgesetzt bzw. so lange, bis Verbindungsversuche zu allen Postfachservern durchgeführt wurden. Schlagen alle RPC-Aufrufe fehl, protokolliert der Postfach-Assistent den Fehler in der Ereignisanzeige. Der Postfachserver fragt alle UM-IP-Gateways ab, die mit den UM-Wähleinstellungen für das Postfach des UM-aktivierten Benutzers verknüpft sind.

7.  Der UM-Server sendet eine SIP NOTIFY-Nachricht an das erste VoIP-Gateway oder die erste IP-Festnetztelefonanlage, das bzw. die bei der Abfrage zurückgegeben wird. Treten Fehler auf, wählt der UM-Server das nächste VoIP-Gateway bzw. IP-Festnetztelefonanlage aus. Der Postfachserver sucht weitere fünf Minuten nach einem VoIP-Gateway bzw. IP-Festnetztelefonanlage. Schlagen alle Verbindungsversuche zu einem VoIP-Gateway oder einer IP-Festnetztelefonanlage fehl, protokolliert der Postfachserver einen Fehler. Wurde ein VoIP-Gateway bzw. IP-Festnetztelefonanlage erfolgreich ermittelt, sendet das VoIP-Gateway die Benachrichtigung an die PBX-Anlage, die ihrerseits eine Benachrichtigung über das MWI-Ereignis an das Telefon des Benutzers sendet und dort die Leuchtanzeige aktiviert. Wenn Sie eine IP-Festnetztelefonanlage haben, wird die MWI-Benachrichtigung von dieser IP-Anlage verarbeitet, und die LED auf dem Telefon des Benutzers leuchtet auf. Weitere MWI-Benachrichtigungsmechanismen finden Sie im Übersichtsabschnitt aufgelistet. Die Art der Benachrichtigung hängt vom PBX- oder IP-Hardwareanbieter ab und ob Lync Server verwendet wird. Sie hängt ebenfalls vom Telefontyp (analog oder digital) ab und ob VoIP verwendet wird.

Übersicht

## MWI in einer Lync Server-Umgebung

In einer Telefonieumgebung mit Lync Server kann ein eingehender Anruf von einem externen Telefon an den Vermittlungsserver, von einem Lync-Client oder von einem UC-fähigen Telefon (Unified Communications) oder anderen VoIP-basierten Telefon gesendet werden. Nach dem Eingang des Anrufs wird dieser an den Lync Server-Front-End-Serverpool gesendet. Mithilfe des Postfachservers und des Postfach-Assistenten wird der MWI-Status für den UM-aktivierten Benutzer ermittelt, und diese Benachrichtigung wird an den (analogen oder digitalen) Lync-Client oder das UC-fähige oder VoIP-basierte Telefon gesendet.

In einer Telefonieumgebung mit Lync Server stellen sich Anruffluss und MWI-Benachrichtigung folgendermaßen dar:

1.  Der Anruf geht wie folgt ein:
    
      - Ein Telefon außerhalb der Organisation (an einen Vermittlungsserver gesendet)
    
      - Ein Lync-basierter Client
    
      - Ein UC-aktiviertes oder ein anderes VoIP-basiertes Telefon

2.  Der eingehende Anruf wird vom Lync Server-Front-End-Serverpool entgegengenommen und an das Telefon oder den SIP-Endpunkt des UM-aktivierten Benutzers gesendet. Der Benutzer meldet sich nicht, und der Anrufer wird aufgefordert, eine Sprachnachricht zu hinterlassen.

3.  Der Lync Server-Front-End-Serverpool leitet den Anruf an einen Postfachserver innerhalb des lokalen Netzwerks bis zum Postfach des Benutzers weiter.

4.  Der Postfachserver ermittelt anhand einer LDAP-Abfrage die Informationen des UM-aktivierten Benutzers (z. B. Durchwahl und benutzerdefinierte Begrüßung). Die Begrüßung wird wiedergegeben, und der Anrufer wird aufgefordert, eine Sprachnachricht zu hinterlassen.

5.  Die vom UM-Dienst erstellte Sprachnachricht wird an den Transportdienst auf demselben Postfachserver am selben Standort weitergegeben.

6.  Der Transportdienst sendet die Sprachnachricht an den Postfachserver, auf dem das Postfach des Benutzers liegt. Beim Postfach-Assistent geht ein MAPI-Ereignis für eine neue Sprachnachricht ein.

7.  Der Postfach-Assistent entscheidet anhand der UM-Wähleinstellungen und der UM-Postfachrichtlinie, ob an den Benutzer MWI-Benachrichtigungen zu senden sind. Der Postfach-Assistent fragt alle Postfachserver ab, die mit den UM-Wähleinstellungen für den Benutzer verknüpft sind. Der Postfach-Assistent versucht dann, das RPC-Ereignis an den ersten zurückgegebenen Postfachserver zu senden. Treten bei diesem Versuch Fehler auf, setzt der Postfach-Assistent seine Versuche beim nächsten Server fort. Die Suche nach einem Postfachserver wird fünf Minuten lang fortgesetzt bzw. so lange, bis Verbindungsversuche zu allen Servern durchgeführt wurden. Schlagen alle RPC-Aufrufe fehl, protokolliert der Postfach-Assistent einen Fehler in der Ereignisanzeige. Der Postfachserver fragt Active Directory nach allen UM-IP-Gateways ab, die mit den UM-Wähleinstellungen für das Postfach des UM-aktivierten Benutzers verknüpft sind.

8.  Der UM-Server sendet eine SIP NOTIFY-Nachricht an das erste VoIP-Gateway oder die erste IP-Festnetztelefonanlage, das bzw. die bei der Abfrage zurückgegeben wird. Treten Fehler auf, wählt der UM-Server das nächste VoIP-Gateway bzw. IP-Festnetztelefonanlage aus. Der Postfachserver sucht weitere fünf Minuten nach einem VoIP-Gateway bzw. IP-Festnetztelefonanlage. Schlagen alle Verbindungsversuche zu einem VoIP-Gateway oder einer IP-Festnetztelefonanlage fehl, protokolliert der Postfachserver einen Fehler. Ist der Verbindungsversuch erfolgreich, sendet das VoIP-Gateway bzw. die IP-Festnetztelefonanlage die Benachrichtigung an den Lync Server-Front-End-Serverpool, der seinerseits eine Benachrichtigung über das MWI-Ereignis an das Telefon des Benutzers oder einen Lync-Client sendet.

Übersicht

## MWI-Ausfallsicherheit

Wenn Sie Postfach- und Clientzugriffsserver, UM-Wählpläne und UM-IP-Gateways bereitstellen und MWI für UM-aktivierte Benutzer verwenden, ist es zugunsten von Fehlertoleranz und Ausfallsicherheit empfehlenswert, mehrere Postfach- und Clientzugriffsserver und auch mehrere VoIP-Gateways und IP-Festnetztelefonanlagen bereitzustellen. Dieses Vorgehen führt auch zu mehr MWI-Ausfallsicherheit, da es mehrere Wege für das Senden der MWI-Benachrichtigungen bereitstellt, wie es im vorhergehenden Abschnitt beschrieben wurde.

Zur Realisierung von Fehlertoleranz für MWI in Unified Messaging muss Folgendes erstellt und konfiguriert werden:

  - Mindestens ein Satz Wähleinstellungen, der mit dem UM-aktivierten Benutzer verknüpft ist, der MWI-Benachrichtigungen empfängt.

  - Mindestens eine UM-Postfachrichtlinie, die mit dem UM-aktivierten Benutzer verknüpft ist, der MWI-Benachrichtigungen empfängt.

  - Mindestens ein UM-IP-Gateway, das dem Satz UM-Wähleinstellungen verknüpft ist, der mit dem UM-aktivierten Benutzer verknüpft ist, der MWI-Benachrichtigungen empfängt.

  - Wenn Sie Lync Server verwenden, müssen alle Clientzugriffs- und Postfachserver zum UM-SIP-URI-Wählplan hinzugefügt werden, der mit dem UM-aktivierten Benutzer verknüpft ist, der wiederum die MWI-Benachrichtigungen erhält.

## MWI-Verwaltung

Für die Verwaltung von MWI können Einstellungen für zwei UM-Komponenten konfiguriert werden: UM-Postfachrichtlinien und UM-IP-Gateways. Bei beiden UM-Objekten kann mithilfe des Cmdlets **Set-UMMailboxPolicy** bzw. **Set-UMIPgateway** MWI in der Exchange-Verwaltungsshell aktiviert oder deaktiviert werden. Sie können die Einstellungen auch über das Exchange Admin Center (EAC) konfigurieren. Der Status der MWI-Benachrichtigung kann mithilfe des Cmdlets **Get-UMMailboxPolicy** bzw. **Get-UMIPgateway** oder in der Shell oder dem EAC angezeigt werden.

## UM-Postfachrichtlinien und MWI

Sie erstellen eine UM-Postfachrichtlinie, um eine allgemeine Zusammenstellung von UM-Richtlinien und -Einstellungen auf eine Gruppe von UM-aktivierten Postfächern anzuwenden. Mithilfe einer UM-Postfachrichtlinie können Sie beispielsweise PIN-Richtlinieneinstellungen, Wähleinschränkungen und MWI-Benachrichtigungen anwenden. Wird MWI für eine UM-Postfachrichtlinie aktiviert oder deaktiviert, werden auch alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, aktiviert bzw. deaktiviert. Die MWI-Einstellung gilt für eine Teilmenge der Benutzer, die mit einem UM-Wählplan verknüpft sind. Weitere Informationen zu UM-Postfachrichtlinien und zum Aktivieren bzw. Deaktivieren von MWI für eine UM-aktivierte Benutzergruppe finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

Sie können das EAC oder das Cmdlet **Set-UMMailboxPolicy** in der Shell verwenden, um die MWI-Einstellung zu konfigurieren, wie es in der folgenden Tabelle dargestellt ist.

### MWI-Einstellung für eine UM-Postfachrichtlinie

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Shell-Parameter</th>
<th>Einstellung im Exchange Admin Center verfügbar?</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AllowMessageWaitingIndicator</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>AllowMessageWaitingIndicator</em> gibt an, ob Benutzer, die mit der UM-Postfachrichtlinie verknüpft sind, beim Eingang neuer Sprachnachrichten Benachrichtigungen empfangen können. Der Standardwert ist <code>$true</code>.</p>
<p>Durch das Aktivieren dieser Einstellung werden den Benutzern, die mit einer UM-Postfachrichtlinie verknüpft sind, bei Anrufen über ein UM-IP-Gateway MWI-Benachrichtigungen gesendet. Mit dieser Einstellung kann das UM-IP-Gateway SIP NOTIFY-Nachrichten senden und empfangen, die an Telefone oder SIP-Endpunkte UM-aktivierter Benutzer gingen.</p>
<p></p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Verwalten von MWI-Einstellungen in einer UM-Postfachrichtlinie finden Sie in den folgenden Themen:

  - [Verwalten einer UM-Postfachrichtlinie](manage-a-um-mailbox-policy-exchange-2013-help.md)

  - [Aktivieren der MWI-Funktion (Message Waiting Indicator) für Benutzer](enable-message-waiting-indicator-mwi-for-users-exchange-2013-help.md)

  - [Deaktivieren der Nachricht wartet Indicator (MWI) für Benutzer](disable-message-waiting-indicator-mwi-for-users-exchange-2013-help.md)

  - [Set-UMMailboxPolicy](https://technet.microsoft.com/de-de/library/bb124903\(v=exchg.150\))

## UM-IP-Gateways und MWI

Wird MWI für ein UM-IP-Gateway deaktiviert, wird MWI für alle Benutzer deaktiviert, die eine Verbindung zu dem VoIP-Gateway oder der IP-Festnetztelefonanlage herstellen, das bzw. die als UM-IP-Gateway definiert ist. Wenn Sie MWI auf einem einzigen UM-IP-Gateway, das mit einem UM-Wählplan verknüpft ist, deaktivieren, werden möglicherweise MWI-Benachrichtigungen für alle UM-aktivierten Benutzer, die mit einem oder mehreren UM-Wählplänen bzw. einer oder mehreren UM-Postfachrichtlinien verknüpft sind, deaktiviert. Weitere Informationen zu UM-Postfachrichtlinien und zum Aktivieren bzw. Deaktivieren von MWI für eine UM-aktivierte Benutzergruppe finden Sie unter [Verwalten einer UM-Postfachrichtlinie](manage-a-um-mailbox-policy-exchange-2013-help.md).

Sie können das EAC oder das Cmdlet **Set-UMMailboxPolicy** in der Shell verwenden, um die MWI-Einstellung zu konfigurieren, wie es in der folgenden Tabelle dargestellt ist.

### MWI-Einstellung für ein UM-IP-Gateway

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Shell-Parameter</th>
<th>Einstellung im Exchange Admin Center verfügbar?</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>MessageWaitingIndicatorAllowed</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>MessageWaitingIndicatorAllowed</em> gibt an, ob das UM-IP-Gateway für das Senden von SIP-NOTIFY-Nachrichten an Benutzer, die einem Satz UM-Wähleinstellungen zugeordnet sind, aktiviert werden soll. Der Standardwert ist <code>$true</code>.</p>
<p>Wird diese Einstellung aktiviert, können für die vom UM-IP-Gateway empfangenen Anrufe Voicemailbenachrichtigungen an die Benutzer gesendet werden. Mit dieser Einstellung kann das UM-IP-Gateway MWI-Benachrichtigungen an UM-aktivierte Benutzer senden.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Verwalten von MWI-Einstellungen finden Sie in den folgenden Themen:

  - [Verwalten eines UM-IP-Gateways](manage-a-um-ip-gateway-exchange-2013-help.md)

  - [MWI (Message Waiting Indicator) für ein UM-IP-Gateway unterstützen](allow-message-waiting-indicator-mwi-on-a-um-ip-gateway-exchange-2013-help.md)

  - [Verhindern von MWI an einem UM-IP-Gateway](prevent-message-waiting-indicator-mwi-on-a-um-ip-gateway-exchange-2013-help.md)

  - [Set-UMIPGateway](https://technet.microsoft.com/de-de/library/aa996577\(v=exchg.150\))

Übersicht

## SMS-Benachrichtigungen für Voicemailnachrichten und verpasste Anrufe

Wie bereits früher erwähnt, ist eine MWI-Benachrichtigung jeder Mechanismus, der das Vorhandensein einer neuen Voicemailnachricht anzeigt. Zusätzlich zu den bereits genannten Mechanismen kann der Benutzer benachrichtigt werden, dass eine Sprachnachricht als Textnachricht, oder auch SMS (Short Message Service) genannt, ansteht. Dies ist eine andere Art der MWI-Benachrichtigung über neue Sprachnachrichten als die herkömmliche optische Anzeige oder andere Mechanismen.

Eine Textnachricht wird auf das Mobiltelefon des Benutzers gesendet, wenn ein Anrufer eine neue Sprachnachricht hinterlässt. Der Benutzer kann auch eine Textnachricht erhalten, die ihm sagt, wenn er einen Anruf verpasst hat und keine Sprachnachricht hinterlassen wurde. Die Benachrichtigung über einen verpassten Anruf per Textnachricht kann dem Benutzer zusammen mit der neuen Voicemailbenachrichtigung gesendet werden.


> [!NOTE]
> Die Textnachricht, die an den Benutzer gesendet wird, enthält eine Vorschau der Sprachnachricht.



Die Benachrichtigungen per Textnachricht verwenden andere Einstellungen als die MWI-Einstellungen auf dem UM-IP-Gateway oder als die UM-Postfachrichtlinie. Benachrichtigungen über neue Sprachnachrichten und verpasste Anrufe per Textnachricht werden in den UM-Postfachrichtlinien und UM-Postfächern konfiguriert. Sie können Benachrichtigungen per Textnachricht über die Cmdlets **Set-UMMailboxPolicy** und **Set-UMMailbox** in der Shell aktivieren bzw. deaktivieren. Mithilfe des Cmdlets **Get-UMMailboxPolicy** bzw. **Get-UMMailbox** kann der Status von Benachrichtigungen per Textnachricht angezeigt werden. Im EAC können Sie keine solchen Benachrichtigungen konfigurieren.

In der folgenden Tabelle sehen Sie die Parameter für ein UM-Postfach, das für einen Benutzer so konfiguriert werden muss, dass er Textnachrichten bezüglich anstehender Sprachnachrichten und verpasster Anrufe erhält.

### Einstellung der Benachrichtigungen per Textnachricht im Benutzerpostfach

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>UMSMSNotificationOption</em></p></td>
<td><p>Nein</p></td>
<td><p>Der Parameter <em>UMSMSNotificationOption</em> gibt an, ob ein UM-aktivierter Benutzer nur für Sprachnachrichten oder für Sprachnachrichten und verpasste Anrufe per SMS bzw. Textnachricht benachrichtigt wird oder ob er keine Benachrichtigungen erhält. Die Werte für diesen Parameter sind: <code>VoiceMail</code>, <code>VoiceMailAndMissedCalls</code> und <code>None</code>. Der Standardwert ist <code>None</code>.</p>
<p></p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Verwalten von Einstellungen von Benachrichtigungen per Textnachricht im Benutzerpostfach finden Sie in den folgenden Themen:

  - [Verwalten von Voicemail-Einstellungen für einen Benutzer](manage-voice-mail-settings-for-a-user-exchange-2013-help.md)

  - [Set-UMMailbox](https://technet.microsoft.com/de-de/library/bb124893\(v=exchg.150\))

In der folgenden Tabelle sehen Sie die Parameter für eine UM-Postfachrichtlinie, die für einen Benutzer so konfiguriert werden muss, dass er Textnachrichten bezüglich anstehender Sprachnachrichten und verpasster Anrufe erhält.

### Einstellung von Benachrichtigungen über Sprachnachrichten und verpasste Anrufe per Textnachricht in einer UM-Postfachrichtlinie

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Shell-Parameter</th>
<th>Einstellung im Exchange Admin Center verfügbar?</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AllowSMSNotification</em></p></td>
<td><p>Nein</p></td>
<td><p>Der Parameter <em>AllowSMSNotification</em> gibt an, ob UM-aktivierte Benutzer, deren Postfächer der UM-Postfachrichtlinie verknüpft sind, an ihre Mobiltelefone gesendete Benachrichtigungen per Textnachricht erhalten dürfen. Wenn dieser Parameter auf <code>$true</code> gesetzt ist, sollte auch der Parameter <em>UMSMSNotificationOption</em> mithilfe des Cmdlets <strong>Set-UMMailbox</strong> für den UM-aktivierten Benutzer auf <code>voicemail</code> oder <code>VoiceMailAndMissedCalls</code> eingestellt werden. Der Standardwert ist <code>$true</code>.</p>
<p></p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Verwalten von Einstellungen für Benachrichtigungen per Textnachricht finden Sie in den folgenden Themen:

  - [Verwalten einer UM-Postfachrichtlinie](manage-a-um-mailbox-policy-exchange-2013-help.md)

  - [Set-UMMailboxPolicy](https://technet.microsoft.com/de-de/library/bb124903\(v=exchg.150\))

Damit die Benachrichtigungen über Sprachnachrichten und verpasste Anrufe per Textnachricht ordnungsgemäß aufgeführt werden, müssen Sie wie folgt vorgehen:

1.  Verwenden Sie entweder das EAC oder die Shell, um UM für den Benutzer zu aktivieren und ihn mit der entsprechenden UM-Postfachrichtlinie zu verknüpfen.

2.  Prüfen Sie in der mit dem Benutzer verknüpften UM-Postfachrichtlinie, dass der Parameter *AllowSMSNotification* auf `$true` gesetzt ist. Führen Sie folgenden Befehl aus, um den Parameter auf `$true` zu setzen: `Set-UMMailboxPolicy -id MyUMMailboxPolicy - AllowSMSNotification $true`.

3.  Aktivieren Sie im Benutzerpostfach die Benachrichtigungen per Textnachricht, indem Sie den Parameter *UMSMSNotificationOption* auf `VoiceMailAndMissedCalls` oder `VoiceMail` setzen.

4.  Da die Standardeinstellung `None` lautet, müssen Sie den folgenden Befehl aus der Shell heraus ausführen und die Option für eine Benachrichtigung per Textnachricht entweder auf `VoiceMailAndMissedCalls` oder `VoiceMail` setzen. Beispiel: `Set-UMMailbox- -id MyUMMailbox -UMSMSNotificationOption VoiceMailAndMissedCalls`.
    

    > [!IMPORTANT]
    > Der Parameter <EM>AllowSMSNotification</EM> in der UM-Postfachrichtlinie und der Parameter <EM>UMSMSNotificationOption</EM> im Benutzerpostfach müssen beide auf <CODE>$true</CODE> gesetzt werden, damit SMS-Benachrichtigungen funktionieren.



Zusätzlich zur Konfiguration der UM-Postfachrichtlinie und des Benutzerpostfachs, damit Benachrichtigungen für neue Sprachnachrichten und verpasste Anrufe per Textnachricht erfolgen, muss der Benutzer solche Benachrichtigungen aktivieren und konfigurieren, wenn er sich bei Outlook Web App anmeldet. Er muss solche Benachrichtigungen wie folgt einrichten und konfigurieren:

1.  Bei Outlook Web App anmelden und zu **Optionen** \> **Telefon** \> **Voicemail** navigieren.

2.  Auf der Seite **Voicemail** unter **Benachrichtigungen** auf **Benachrichtigungen einrichten** klicken.

3.  Auf der Seite **Textnachrichten** auf **Benachrichtigungen aktivieren** klicken.
    

    > [!WARNING]
    > Nicht auf <STRONG>Voicemailbenachrichtigungen</STRONG> klicken, andernfalls wird der Benutzer zur Seite <STRONG>Voicemail</STRONG> zurückgeführt.



4.  Auf der Seite **Textnachrichten** unter **Gebietsschema** in der Dropdownliste nach dem Gebietsschema oder dem Standort des Textnachrichten-Mobilfunkanbieters suchen.

5.  Auf der Seite **Textnachrichten** unter **Mobilfunkanbieter** in der Dropdownliste nach dem Textnachrichten-Mobilfunkanbieter suchen und auf **Weiter** klicken.

6.  Auf der Seite **Textnachrichten** im Feld **Geben Sie Ihre Telefonnummer ein, und klicken Sie auf "Weiter".** die Mobiltelefonnummer für die Benachrichtigungen eingeben und auf **Weiter** klicken. Eine sechsstellige Kennung wird an das Mobiltelefon gesendet. Falls der Benutzer den Kenncode nicht erhält, muss er auf **Keine Kennung empfangen, muss erneut gesendet werden...** klicken.

7.  Kenncode in das Feld **Kennung** eingeben und auf **Fertig stellen** klicken

8.  Nachdem der Benutzer die Benachrichtigungen per Textnachricht aktiviert hat, kann er auf der Seite **Textnachrichten** auf **Voicemailbenachrichtigungen einrichten...** klicken. Der Benutzer wird zurück zur Voicemailseite geführt, wo er im Bereich **Benachrichtigungen** einen Bildlauf nach unten durchführen und die Benachrichtigungsoptionen für verpasste Anrufe und Sprachnachrichten einrichten kann.

Übersicht

