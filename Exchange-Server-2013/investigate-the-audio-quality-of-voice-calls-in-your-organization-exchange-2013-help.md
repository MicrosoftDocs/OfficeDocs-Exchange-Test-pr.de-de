---
title: 'Überprüfen Sie die Audioqualität VoIP-Anrufe in Ihrer Organisation: Exchange Online Help'
TOCTitle: Überprüfen Sie die Audioqualität VoIP-Anrufe in Ihrer Organisation
ms:assetid: 8a87694b-1678-4a01-859f-5ad3b2c73db5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659069(v=EXCHG.150)
ms:contentKeyID: 50554870
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Überprüfen Sie die Audioqualität VoIP-Anrufe in Ihrer Organisation

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-21_

Sollten in der Organisation Probleme mit der Audioqualität von UM-Anrufen und Voicemailnachrichten auftreten, verwenden Sie den Bericht Anrufstatistik, um die Ursache der Probleme zu ermitteln.


> [!NOTE]
> Die Audioqualität eines Anrufs kann durch Faktoren beeinträchtigt werden, die nicht in den Berichten behandelt werden. Liegt auf Ihren Exchange-Servern beispielsweise eine hohe Arbeitsspeicher- oder CPU-Auslastung vor, melden die Benutzer unter Umständen eine schlechte Anrufqualität, obwohl die Audioqualität den Berichten zufolge ausgezeichnet ist.



Weitere Aufgaben im Zusammenhang mit Anrufstatistiken finden Sie unter [UM Berichte Prozeduren](um-reports-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Cmdlets für UM-Anrufdaten und Zusammenfassungsberichte" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Abrufen von Statistiken zur Audioqualität in Ihrer Organisation mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Anrufstatistik**.

2.  Wählen Sie die Anrufstatistik aus, die in den Bericht eingeschlossen werden soll. Der Bericht wird automatisch aktualisiert, wenn Sie beliebige der folgenden Optionen auswählen:
    
      - **Anzeigen **  Wählen Sie den Typ der Anrufstatistik für die Anzeige aus:
        
          - **Täglich (90 Tage) **  Wählen Sie diese Option aus, um Details zu den Anrufen in den vergangenen 90 Tagen anzuzeigen.
        
          - **Monatlich (12 Monate)**   Wählen Sie diese Option aus, um eine Zusammenfassung der Anrufe in den vergangenen 12 Monaten anzuzeigen.
        
          - **Alle**   Wählen Sie diese Option aus, um kombinierte Statistiken für alle Anrufe anzuzeigen, die seit dem Beginn der Behandlung von Anrufen durch UM empfangen wurden.
    
      - **UM-Wählplan**   Wenn Sie die Daten im Bericht auf Anrufe in einem bestimmten UM-Wählplan beschränken möchten, wählen Sie diesen Wählplan aus.
    
      - **UM-IP-Gateway**   Wenn Sie die Daten im Bericht auf Anrufe eines bestimmten UM-IP-Gateways einschränken möchten, wählen Sie dieses UM-IP-Gateway aus. Wenn Sie zuerst einen UM-Wählplan auswählen, sind in der Liste nur die dem ausgewählten UM-Wählplan zugeordneten UM-IP-Gateways verfügbar.

3.  Wenn Sie für eine Zeile des Berichts ausführlichere Informationen zur Audioqualität anzeigen möchten, markieren Sie die Zeile, und klicken Sie auf **Details zur Audioqualität**. Die folgenden Informationen sind verfügbar:
    
      - **DATUM UND UHRZEIT**   Die Zeit (im UTC-Format), zu der die Anrufstatistik erfasst wurde.
    
      - **UM-WÄHLPLAN**   Der Wählplan für die in der Statistik enthaltenen Anrufe.
    
      - **UM-IP-GATEWAY**   Das UM-IP-Gateway, von dem die in der Statistik enthaltenen Anrufe angenommen wurden.
    
      - **NMOS**   Das NMOS-Ergebnis (Network Mean Opinion Score) des Anrufs. Das NMOS-Ergebnis gibt an, wie gut die Audioqualität des Anrufs auf einer Skala von 1 bis 5 war, wobei 5 "ausgezeichnet" ist.
        

        > [!NOTE]
        > Das bestmögliche NMOS-Ergebnis eines Anrufs hängt vom verwendeten Audio-Codec ab. Das NMOS-Ergebnis steht ggf. für Anrufe, die kürzer als 10&nbsp;Sekunden sind, nicht zur Verfügung.

    
      - **NMOS-HERABSTUFUNG**   Der Wert für die Herabstufung der Audioqualität des NMOS-Ergebnisses im Vergleich zum bestmöglichen Wert für den verwendeten Audiocodec. Wenn der NMOS-Herabstufungswert für einen Anruf z. B. 1,2 war, und das gemeldete NMOS-Ergebnis für den Anruf 3,3, ist das maximale NMOS-Ergebnis für diesen Anruf 4,5 (1,2 + 3,3).
    
      - **JITTER**   Die durchschnittliche Variation beim Eingang von Datenpaketen für den Anruf.
    
      - **PAKETVERLUST**   Der durchschnittliche Prozentsatz verloren gegangener Pakete für den ausgewählten Anruf. Der Paketverlust gibt Aufschluss über die Zuverlässigkeit der Verbindung.
    
      - **ROUNDTRIP**   Das durchschnittliche Roundtrip-Ergebnis in Millisekunden für den Audioteil des ausgewählten Anrufs. Das Roundtripergebnis gibt Aufschluss über die Latenz der Verbindung.
    
      - **BURSTVERLUSTDAUER**   Die durchschnittliche Dauer des Paketverlusts während Verlustbursts für den ausgewählten Anruf.
    
      - **ANZAHL DER BEISPIELE**   Die Anzahl der Anrufe, für die ein Sampling ausgeführt wurde, um die Durchschnittswerte zu berechnen.

4.  Eine ausführliche Audioqualitätsmetrik zu bestimmten Anrufen finden Sie unter [Durchführen einer Überprüfung der Audioqualität von Sprachanrufen für Benutzer](investigate-the-audio-quality-of-voice-calls-for-a-user-exchange-2013-help.md).

