---
title: 'Überprüfen der E-Mail-Sprachanrufe für Benutzer: Exchange 2013-Hilfe'
TOCTitle: Überprüfen Sie die e-Mail-Sprachanrufe für einen Benutzer
ms:assetid: 95768fe3-3ae2-43bd-9cbf-18c3b85c4592
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659070(v=EXCHG.150)
ms:contentKeyID: 50554861
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Überprüfen Sie die e-Mail-Sprachanrufe für einen Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Mithilfe von Benutzeranrufprotokollen können die folgenden Informationen zu bestimmten UM-Benutzern (Unified Messaging) angezeigt werden:

  - Details zu den UM-Anrufen für einen Benutzer innerhalb der letzten 90 Tage.

  - Audioqualität der einzelnen Anrufe. Die Audioqualitätsmetrik ist unter Umständen nicht für alle Anrufe verfügbar, da die Metrik von mehreren Faktoren (wie Art und die Dauer des Anrufs) abhängt.

Informationen zu weiteren Aufgaben im Zusammenhang mit UM-Berichten finden Sie unter [UM Berichte Prozeduren](um-reports-procedures-exchange-2013-help.md).

## Wie rufe ich Anrufprotokolle für einen UM-aktivierten Benutzer ab?

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Benutzeranrufprotokolle**.

2.  Klicken Sie auf **Benutzer auswählen**, und wählen Sie den Benutzer aus, für den Sie Daten abrufen möchten.

3.  Wenn Sie für eine Zeile des Berichts ausführlichere Informationen zur Audioqualität anzeigen möchten, markieren Sie die Zeile, und klicken Sie auf **Details zur Audioqualität**. Weitere Informationen zum Interpretieren der Audioqualität finden Sie unter [Durchführen einer Überprüfung der Audioqualität von Sprachanrufen für Benutzer](investigate-the-audio-quality-of-voice-calls-for-a-user-exchange-2013-help.md).

4.  Wenn Sie den Bericht in die Zwischenablage kopieren möchten, klicken Sie auf **Alle Zeilen in die Zwischenablage kopieren**.

## Wie interpretiere ich das UM-Benutzeranrufprotokoll?

Das Benutzeranrufprotokoll enthält zu jedem Anruf folgende Informationen:

  - **DATUM UND UHRZEIT:**    Das Datum und die Uhrzeit des Anrufs in der Zeitzone, die der ausgewählte Benutzer in Microsoft Outlook Web App festgelegt hat.

  - **DAUER**   Die Dauer des Anrufs in Minuten (MM) und Sekunden (SS) im folgenden Format: MM:SS.

  - **ANRUFTYP**   Der Typ des Anrufs:
    
      - **Mailboxansage:**    Der Anruf wurde nicht angenommen und an die Postfachserver weitergeleitet, und der Anrufer hat eine Sprachnachricht hinterlassen.
    
      - **Mailboxansage: Verpasste Anrufe**   Der Anruf wurde nicht angenommen und wurde an die Postfachserver weitergeleitet, und der Anrufer hat keine Sprachnachricht hinterlassen.
    
      - **Teilnehmerzugriff**   Eine Teilnehmerzugriffsnummer aufgerufen. Der Anrufer hat sich angemeldet und wurde für UM über seine Durchwahl und sein Kennwort für den Zugriff auf E-Mail-Nachrichten, Kalender und Sprachnachrichten über das Telefon authentifiziert.
    
      - **Automatische Telefonzentrale**   Der Anruf wurde von einer automatischen UM-Telefonzentrale angenommen. Diese Anrufe sind in der Regel Anrufe, bei denen der Anrufer die Haupttelefonnummer der Organisation gewählt hat.
    
      - **Fax**   Ein Anruf, bei dem ein Faxsignal erkannt wurde. Wenn Sie Faxpartner konfiguriert haben, wurde dieser Anruf an den Partner gesendet.
    
      - **Wiedergabe über Telefon**   Ein Anruf, der von UM durchgeführt wurde, weil der Benutzer in Microsoft Outlook Web App oder Outlook in einer Sprachnachricht auf die Schaltfläche "Wiedergabe über Telefon" geklickt hat.
    
      - **Mich suchen**   Ein ausgehender Anruf, der aufgrund einer Regel vom Typ "Mich suchen" in einer Mailboxansageregel von UM durchgeführt wurde.
    
      - **Nicht authentifizierte Pilotnummer**   Ein Anruf ist an die Outlook Voice Access-Nummer erfolgt. Der Aufrufer hat sich nicht angemeldet und wurde nicht authentifiziert.
    
      - **Begrüßungsaufzeichnung**   Ein Anruf, der von UM durchgeführt wurde, um persönliche Ansagen für einen Benutzer aufzuzeichnen.
    
      - **Keine**   Ein Anruf, dessen Typ nicht definiert wurde, ist erfolgt.

  - **ANGERUFENE NUMMER**   Die Telefonnummer oder SIP-Adresse des Anrufers.

  - **ANRUFENDE NUMMER**   Die Telefonnummer oder SIP-Adresse (für Benutzer in SIP-Wählplänen wie beispielsweise Benutzer von Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server) des gewünschten Anrufempfängers.

  - **UM-IP-GATEWAY**   Das UM-IP-Gateway, von dem der Anruf angenommen wurde.

  - **AUDIOQUALITÄT**   Die allgemeine Audioqualität des Anrufs. Wählen Sie zum Erhalten ausführlicherer Informationen zur Audioqualität die gewünschte Zeile aus, und klicken Sie auf **Details zur Audioqualität**.

