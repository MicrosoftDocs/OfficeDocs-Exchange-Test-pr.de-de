---
title: 'Interpretieren von Voice Mail-anrufdatensätze: Exchange Online Help'
TOCTitle: Interpretieren von Voice Mail-anrufdatensätze
ms:assetid: 368d9c58-61a2-43d5-8189-d3469a9e2a8d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659061(v=EXCHG.150)
ms:contentKeyID: 50554769
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Interpretieren von Voice Mail-anrufdatensätze

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Um ausführliche Informationen zu Anrufen anzuzeigen, die an einem bestimmten Tag von den Exchange-Servern behandelt wurden, exportieren Sie die Anrufdaten für diesen Tag aus dem Anrufstatistikbericht. Tägliche Anrufdaten, die für die vergangenen 90 Tage verfügbar sind, helfen Ihnen beim Diagnostizieren von Problemen mit der Audioqualität oder abgelehnten Anrufen und stellen Informationen für Überwachungen oder Berichte zu Exchange-Servern in der Organisation bereit.

Informationen zu weiteren Aufgaben im Zusammenhang mit UM-Berichten finden Sie unter [UM Berichte Prozeduren](um-reports-procedures-exchange-2013-help.md).

## Exportieren täglicher UM-Anrufdatensätze mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Anrufstatistiken**.

2.  Klicken Sie unter **Anzeigen** auf **Täglich (90 Tage)**, und wählen Sie dann den UM-Wählplan oder das UM-IP-Gateway oder ggf. beides aus. Der Bericht wird automatisch aktualisiert, wenn Sie Optionen auswählen.

3.  Wählen Sie den Tag aus, für den Sie Anrufdatensätze exportieren möchten, und klicken Sie auf **Tag exportieren**.

4.  Klicken Sie im Bestätigungsfeld für den Dateidownload auf **Öffnen** oder **Speichern**.
    
    Die exportierte Datei erhält den Namen "um\_cdr\_*JJJJ-MM-TT*.csv", wobei *JJJJ-MM-TT* das Jahr, der Monat und der Tag der Berichtsausführung sind.
    

    > [!NOTE]
    > Auf der Berichtsseite können Sie eine Microsoft Excel-Vorlage herunterladen, mit der Sie die CSV-Datei für einen bestimmten Tag importieren können.



5.  Verwenden Sie eine Anwendung wie Excel, um die CSV-Datei zu verarbeiten und eigene benutzerdefinierte Berichte zu erstellen.

## Interpretieren von UM-Anrufdaten

Die exportierten UM-Anrufdaten enthalten die folgenden detaillierten Informationen zu jedem Anruf, der an diesem Tag von UM behandelt wurde.


> [!NOTE]
> Im Anrufstatistikbericht werden die Tage in der UTC-Zeit angezeigt.



  - **CallStartTime   **Das Datum und die Uhrzeit der Verarbeitung des Anrufs durch UM (UTC-Zeit). Die UTC-Zeit und das Datum werden im folgenden Format dargestellt: *JJJJ-MM-TT hh:mm:SSZ*, wobei Folgendes gilt: *JJJJ* = Jahr, *MM* = Monat, *TT* = Tag, *hh* = Stunde (im 24-Stunden-Format), *mm* = Minuten, ss = Sekunden. Z steht für Zulu, eine andere Bezeichnung für UTC (wie +*hh*:*mm* oder -*hh*:*mm* zur Angabe einer Zeitverschiebung von der UTC-Zeit). Da alle Anrufzeiten in diesem Bericht in UTC-Zeit angegeben sind, wird immer Z verwendet.
    
    Für einen Anruf am 23.06.13 um 14:23 Uhr wird die Anrufstartzeit z. B. als 23.06.2013 14:23:11Z angezeigt.

  - **Anruftyp   **Der Typ des Anrufs:
    
      - **Mailboxansage: Sprachnachrichten**   Der Anruf wurde nicht angenommen und wurde an die Exchange-Server weitergeleitet, und der Anrufer hat eine Sprachnachricht hinterlassen.
    
      - **Mailboxansage: Verpasste Anrufe**   Der Anruf wurde nicht angenommen und wurde an die Exchange-Server weitergeleitet, und der Anrufer hat keine Sprachnachricht hinterlassen.
    
      - **Subscriber Access**   Ein Anruf wurde für die Teilnehmerzugriffsnummer getätigt. Der Anrufer hat sich angemeldet und wurde bei UM mit der Durchwahl und dem Kennwort authentifiziert, um über das Telefon auf E-Mails, Kalender und Sprachnachrichten zuzugreifen.
    
      - **Auto Attendant**   Der Anruf wurde von einer automatischen UM-Telefonzentrale angenommen. Diese Anrufe sind in der Regel Anrufe, bei denen der Anrufer die Haupttelefonnummer der Organisation gewählt hat.
    
      - **Fax**   Ein Anruf wurde angenommen, bei dem ein FAX-Ton erkannt wurde. Wenn Sie Faxpartner konfiguriert haben, wird dieser Anruf an den Faxpartner gesendet.
    
      - **Wiedergabe über Telefon**   Ein Anruf wurde von UM durchgeführt, weil der Benutzer in Microsoft Outlook Web App oder Outlook in einer Sprachnachricht auf die Schaltfläche "Wiedergabe über Telefon" geklickt hat.
    
      - **Find Me**   Ein ausgehender Anruf wurde aufgrund einer Regel "Mich suchen" in einer Mailboxansageregel von UM durchgeführt.
    
      - **Unauthenticated Pilot Number**   Ein Anruf wurde für die Outlook Voice Access-Nummer durchgeführt. Der Aufrufer hat sich nicht angemeldet, und er wurde nicht authentifiziert.
    
      - **Greetings Recording**   Ein Anruf wurde von UM durchgeführt, um persönliche Ansagen für einen Benutzer aufzuzeichnen.
    
      - **None**   Ein Anruf wurde durchgeführt, dessen Typ nicht definiert wurde.

  - **CallIdentity**   Die vom UM-IP-Gateway bereitgestellte SIP-Anrufidentität.

  - **ParentCallIdentity**   Die SIP-Sitzungsidentität der Sitzung, aus der dieser Anruf stammt. Dieses Feld wird genutzt, wenn das Feature für Mailboxansageregeln "Mich suchen" oder Anrufe der Anrufweiterleitung verwendet werden, einschließlich der Anrufweiterleitung zwischen automatischen UM-Telefonzentralen.

  - **UMServerName**   Der Name des Postfachservers, von dem der Anruf verarbeitet wurde (sofern vorhanden). Diese Informationen werden nur bereitgestellt, wenn Sie über einen lokalen Postfachserver verfügen.

  - **DialPlanName**   Der UM-Wählplan, mit dem der Anruf verarbeitet wurde.

  - **Call Duration**   Die gesamte Dauer des Anrufs.

  - **IPGatewayAddress**   Der vollqualifizierte Domänenname (Fully Qualified Domain Name, FQDN) des IP-Gateways, das den Anruf verarbeitet hat.

  - **CalledPhoneNumber**   Die Telefonnummer oder SIP-Adresse des gewünschten Anrufempfängers (für Benutzer in SIP-Wählplänen mit Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server).

  - **CallerPhoneNumber**   Die Telefonnummer oder SIP-Adresse des Anrufers.

  - **OfferResult**   Der Status des Anrufs:
    
      - **Antwort**   UM hat einen Anruf erfolgreich angenommen oder durchgeführt. Der Anruf wurde nicht weiter- oder umgeleitet. Zu diesen Anrufen zählen abgeschlossene Anrufe bei Outlook Voice Access, "Wiedergabe über Telefon" oder automatischen UM-Telefonzentralen und Anrufe, die von UM behandelt wurden, weil der Anruf unter der angerufenen Durchwahl nicht angenommen wurde.
    
      - **Fehler**   UM hat einen Anruf angenommen oder durchgeführt, dabei ist jedoch ein Fehler aufgetreten. Zu diesen Anrufen zählen Anrufe, bei denen die angerufene Nummer oder Adresse besetzt, nicht verfügbar oder nicht vorhanden war, der Anrufer aufgelegt hat, bevor der Anruf durchgestellt wurde, der UM-Wählplan oder die UM-Postfachrichtlinieneinstellungen den Anruf verhindert haben oder das VoIP-Gateway oder die IP-Nebenstellenanlage im Telefonsystem nicht erreicht werden konnte.
    
      - **Abgelehnt**   Der Anruf wurde von UM abgelehnt. Dies ist normalerweise auf einen Konfigurationsfehler zurückzuführen. Zu diesen Anrufen zählen Anrufe, bei denen das UM-IP-Gateway keinem UM-Wählplan zugeordnet ist oder Inkompatibilitätsprobleme vorliegen.
    
      - **Redirected**   Der Anruf wurde von UM angenommen, aber an einen anderen Postfachserver umgeleitet. Zu diesen Anrufen zählen Anrufe, bei denen der Anrufer das UM-Menü verwendet hat, um einen Kontakt im Verzeichnis oder in den persönlichen Kontakten anzurufen, oder bei denen der Anrufer eine Outlook Voice Access-Nummer über eine Telefonnummer angerufen hat, die nicht mit dem Postfach des Benutzers verknüpft ist. In diesen Fällen leitet UM den Anruf an den Exchange-Server weiter, der mit dem Konto dieses Benutzers verbunden ist.
    
      - **Keine**   Der Anrufstatus ist unbekannt.

  - **DropCallReason**   Der Grund, aus dem der Anruf getrennt wurde, sofern UM den Grund ermitteln konnte. Wenn der Anrufer aufgelegt hat, wird z. B. "Auflegen" angezeigt.

  - **ReasonForCall**   Wie der Anruf verbunden wurde:
    
      - **Direct**   Der Anrufer hat die angerufene Nummer direkt gewählt.
    
      - **DivertForward**   Der Anrufer hat eine Nummer gewählt, und die angerufene Person hat den Anruf an UM-Voicemail umgeleitet.
    
      - **DivertBusy**   Der Anrufer hat eine Nummer gewählt, und das Telefon war besetzt, sodass der Anruf an UM-Voicemail umgeleitet wurde.
    
      - **DivertNoAnswer **  Der Anrufer hat eine Nummer gewählt, und die angerufene Person hat den Anruf nicht angenommen, sodass der Anruf an UM-Voicemail umgeleitet wurde.
    
      - **Outbound**   Der Anruf wurde von UM durchgeführt, beispielsweise um eine Sprachnachricht mit "Wiedergabe über Telefon" wiederzugeben.
    
      - **None**   Es wurde kein Grund für den Anruf gemeldet.

  - **DialedString**   Die Adresse oder Telefonnummer der Person, an die dieser Anruf übergeben oder weitergeleitet wurde. Dieser Wert ist auch die Adresse oder Telefonnummer, die für "Wiedergabe über Telefon" angerufen wird.

  - **CallerMailboxAlias**   Der Postfachalias (der Teil der E-Mail-Adresse vor dem @-Zeichen) des Anrufers. Dieser Wert ist nur verfügbar, wenn sich der Anrufer bei Outlook Voice Access angemeldet hat.

  - **CallerMailboxAlias**   Der Postfachalias des gewünschten Empfängers des Anrufs, wenn dieser ein UM-aktivierter Benutzer ist.

  - **Auto Attendant Name**   Der Name der automatischen Telefonzentrale für diesen Anruf.

  - **NMOS Score**   Der NMOS-Wert (Network Mean Opinion Score) für den Anruf. Der NMOS-Wert gibt an, wie gut die Audioqualität des Anrufs auf einer Skala von 1 bis 5 war, wobei 5 "ausgezeichnet" ist.
    

    > [!NOTE]
    > <STRONG>Note</STRONG>&nbsp;&nbsp;&nbsp;Der maximal mögliche NMOS-Wert für einen Anruf hängt vom verwendeten Audiocodec ab. Für sehr kurze Anrufe von weniger als 10&nbsp;Sekunden ist möglicherweise kein NMOS-Wert verfügbar.



  - **NMOSDegradation**   Der Wert für die Herabstufung der Audioqualität des NMOS-Werts im Vergleich zum bestmöglichen Wert für den verwendeten Audiocodec. Wenn der NMOS-Herabstufungswert für einen Anruf z. B. 1,2 war, und der gemeldete NMOS-Wert für den Anruf war 3,3, dann ist der maximale NMOS-Wert für diesen Anruf 4,5 (1,2 + 3,3).

  - **NMOSDegradation Jitter**   Die gesamte NMOS-Herabstufung aufgrund von Jitter.

  - **NMOSDegradation PacketLoss**   Die gesamte NMOS-Herabstufung aufgrund von Paketverlusten.

  - **Jitter   **Die durchschnittliche Variation beim Eingang von Datenpaketen für den Anruf.

  - **PacketLoss   **Der durchschnittliche Prozentsatz des Datenpaketverlusts für den ausgewählten Anruf. Der Paketverlust gibt Aufschluss über die Zuverlässigkeit der Verbindung.

  - **Round Trip**   Der durchschnittliche Roundtrip in Millisekunden für den Audioteil des ausgewählten Anrufs. Das Roundtripergebnis gibt Aufschluss über die Latenz der Verbindung.

  - **BurstDensity   **Der Prozentsatz von Paketen, die innerhalb eines Burstzeitraums (hohe Verlustrate) verloren gegangen sind und verworfen wurden.

  - **Burstlückendauer   **Die durchschnittliche Dauer des Paketverlusts während Verlustbursts für den ausgewählten Anruf.

  - **Audiocodec   **Der während des Anrufs verwendete Audiocodec.

