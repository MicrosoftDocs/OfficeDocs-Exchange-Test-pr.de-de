---
title: 'Überprüfen der Voicemailanrufe in der Organisation: Exchange 2013-Hilfe'
TOCTitle: Überprüfen Sie die e-Mail-Sprachanrufe in Ihrer Organisation
ms:assetid: f6fdbe17-d1d2-442a-aa13-06b908d9c33a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659073(v=EXCHG.150)
ms:contentKeyID: 50554944
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Überprüfen Sie die e-Mail-Sprachanrufe in Ihrer Organisation

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Mithilfe des Berichts "Anrufstatistik" können Sie Informationen zu Typ und Status von eingehenden Anrufen anzeigen, die von den Exchange-Servern in Ihrer Organisation verarbeitet wurden. Der Bericht enthält statistische Informationen zu den Anrufen, die an UM weitergeleitet oder von UM für die Organisation erfasst wurden. Anhand dieser Informationen können Sie für die Kapazitätsplanung, Überwachung und Behandlung von UM-Verfügbarkeits- und Audioqualitätsproblemen sowie nicht erfolgreicher Anrufe die Nutzung nachverfolgen.

In diesem Thema werden diese Fragen beantwortet:

  - How do I get call statistics for UM?

  - How do I interpret UM call statistics?

Informationen zu weiteren Aufgaben im Zusammenhang mit UM-Berichten finden Sie unter [UM Berichte Prozeduren](um-reports-procedures-exchange-2013-help.md).

## Wie rufe ich Anrufstatistiken für UM ab?

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Unified Messaging** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Anrufstatistik**.

2.  Wählen Sie die Informationen aus, die in den Bericht eingeschlossen werden soll. Der Bericht wird automatisch aktualisiert, wenn Sie eine der folgenden Optionen auswählen:
    
      - **Anzeigen**   Wählen Sie den Typ der Anrufstatistik für die Anzeige aus:
        
          - **Täglich (90 Tage)**   Wählen Sie diese Option aus, um Details zu den Anrufen in den vergangenen 90 Tagen anzuzeigen.
        
          - **Monatlich (12 Monate)**   Wählen Sie diese Option aus, um eine Zusammenfassung der Anrufe in den vergangenen 12 Monaten anzuzeigen.
        
          - **Alle**   Wählen Sie diese Option aus, um kombinierte Statistiken für alle Anrufe anzuzeigen, die seit dem Beginn der Behandlung von Anrufen durch UM empfangen wurden.
    
      - **UM-Wählplan**   Wenn Sie die Daten im Bericht auf Anrufe in einem bestimmten UM-Wählplan beschränken möchten, wählen Sie diesen Wählplan aus.
    
      - **UM-IP-Gateway**   Wenn Sie die Daten im Bericht auf Anrufe eines bestimmten UM-IP-Gateways einschränken möchten, wählen Sie dieses Gateway aus. Wenn Sie zuerst einen UM-Wählplan auswählen, sind in der Liste nur die dem ausgewählten UM-Wählplan zugeordneten UM-IP-Gateways verfügbar.

3.  Wenn Sie für eine Zeile des Berichts ausführlichere Informationen zur Audioqualität anzeigen möchten, markieren Sie die Zeile, und klicken Sie auf **Details zur Audioqualität**. Weitere Informationen zum Interpretieren der Audioqualität finden Sie unter [Überprüfen Sie die Audioqualität VoIP-Anrufe in Ihrer Organisation](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/run-voice-mail-call-reports/audio-quality-of-voice-calls-in-organization).

4.  Wenn Sie den Bericht in die Zwischenablage kopieren möchten, klicken Sie auf **Kopieren**.

5.  Für tägliche Berichte können Sie Details für einen bestimmten Tag in eine CSV-Datei exportieren.
    
    1.  Wählen Sie den Tag aus, und klicken Sie auf **Tag exportieren**.
    
    2.  Klicken Sie in der Bestätigung für den Dateidownload auf **Öffnen** oder **Speichern**.
    
    Die exportierte Datei erhält den Namen "um\_cdr\_*JJJJ-MM-TT*.csv", wobei *JJJJ-MM-TT* das Jahr, der Monat und der Tag der Berichtsausführung sind. Weitere Informationen finden Sie unter [Interpretieren von Voice Mail-anrufdatensätze](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/run-voice-mail-call-reports/interpret-voice-mail-call-records).
    

    > [!NOTE]
    > Auf der Berichtsseite können Sie eine Microsoft Excel-Vorlage herunterladen, mit der Sie die CSV-Datei für einen bestimmten Tag importieren können.



Zurück zum Seitenanfang

## Wie werte ich UM-Anrufstatistiken aus?

Der Bericht für die UM-Anrufstatistik enthält die folgenden Informationen:

  - **DATUM**   Das UTC-Datum für die Anrufdaten. Das Datumsformat hängt vom gewählten Typ des Berichts und den Gebietsschemaeinstellungen ab. Sie können unter folgenden Optionen wählen:
    
      - **---**   Alle Anrufe werden angezeigt.
    
      - **MMM/JJ**   Der Monat der Anrufe. Beispielsweise Jan/13.
    
      - **TT/MM/JJ**   Der Tag der Anrufe. Beispiel: 23/06/13.

  - **GESAMT**   Die Gesamtanzahl der Anrufe für die ausgewählten UM-Wähleinstellungen oder das UM-IP-Gateway für dieses Datum.

  - **SPRACHNACHRICHT**   Der Prozentsatz eingehender Anrufe, die von UM im Namen von Benutzern angenommen wurden und bei denen Anrufer eine Sprachnachricht hinterlassen haben.

  - **VERPASST**    Der Prozentsatz eingehender Anrufe, die von UM im Namen von Benutzern angenommen wurden und bei denen Anrufer keine Sprachnachricht hinterlassen haben, sodass eine Benachrichtigung über einen verpassten Anruf erstellt wurde.

  - **OUTLOOK VOICE ACCESS**   Der Prozentsatz von eingehenden Anrufen, bei denen sich Benutzer in UM angemeldet haben (und authentifiziert wurden), um auf ihre E-Mails, Kalender und Sprachnachrichten zuzugreifen.

  - **AUSGEHEND**   Der Prozentsatz von Anrufen, die von UM im Namen von authentifizierten oder nicht authentifizierten Benutzern getätigt oder übertragen wurden. Diese Statistik enthält die Anruftypen für die Benutzersuche, die Wiedergabe über das Telefon und die Wiedergabe von Begrüßungen über das Telefon.

  - **AUTOMATISCHE TELEFONZENTRALE**   Der Prozentsatz von eingehenden Anrufen, die von automatischen UM-Telefonzentralen angenommen wurden.

  - **FAX**   Der Prozentsatz eingehender Anrufe, die an einen Faxpartner umgeleitet wurden.

  - **ANDERE**   Der Prozentsatz anderer eingehender oder getätigter Anrufe, die in keine der oben genannten Kategorien fallen. Diese Anrufe enthalten Anrufe von Outlook Voice Access-Nummern, bei denen sich die Benutzer nicht angemeldet haben und nicht authentifiziert wurden.

  - **MISSLUNGEN ODER ABGELEHNT**   Der Prozentsatz der Anrufe, bei denen Fehler aufgetreten sind oder die von UM abgelehnt wurden. Beachten Sie, dass Anrufe, bei denen Fehler aufgetreten sind, nicht doppelt gezählt werden. Wenn z. B. bei einem Anruf bei Outlook Voice Access ein Fehler auftritt, wird dieser nur als fehlerhafter Anruf betrachtet und nicht auch als Outlook Voice Access-Anruf.

  - **AUDIOQUALITÄT**   Eine grafische Darstellung der gesamten Audioqualität für den ausgewählten Zeitraum für die Organisation.

Zurück zum Seitenanfang

## Weitere Informationen

[Überprüfen Sie die Audioqualität VoIP-Anrufe in Ihrer Organisation](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/run-voice-mail-call-reports/audio-quality-of-voice-calls-in-organization)

[Interpretieren von Voice Mail-anrufdatensätze](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/run-voice-mail-call-reports/interpret-voice-mail-call-records)

