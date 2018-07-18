---
title: 'Durchführen einer Überprüfung der Audioqualität von Sprachanrufen für Benutzer: Exchange Online Help'
TOCTitle: Durchführen einer Überprüfung der Audioqualität von Sprachanrufen für Benutzer
ms:assetid: 0c945886-3cfa-423e-9b46-0d6b1584a145
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659059(v=EXCHG.150)
ms:contentKeyID: 50554775
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Durchführen einer Überprüfung der Audioqualität von Sprachanrufen für Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Werden von einem Benutzer Probleme mit der Audioqualität der UM-Anrufe (Unified Messaging) gemeldet, können Sie den Bericht für Benutzeranrufprotokolle verwenden, um die Ursache der Probleme zu klären.


> [!NOTE]
> Die Audioqualität eines Anrufs kann durch Faktoren beeinträchtigt werden, die nicht in den Berichten behandelt werden. Liegt auf Ihren Exchange-Servern beispielsweise eine hohe Arbeitsspeicher- oder CPU-Auslastung vor, melden die Benutzer unter Umständen eine schlechte Anrufqualität, obwohl die Audioqualität den Berichten zufolge ausgezeichnet ist.



Informationen zu weiteren Aufgaben im Zusammenhang mit UM-Berichten finden Sie unter [UM Berichte Prozeduren](um-reports-procedures-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Cmdlets für UM-Anrufdaten und Zusammenfassungsberichte" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Abrufen von Anrufprotokollen für einen UM-aktivierten Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Benutzeraufrufprotokolle**.

2.  Klicken Sie auf **Benutzer auswählen**, und wählen Sie den Benutzer aus, für den Sie Daten abrufen möchten.

3.  Wenn Sie für eine Zeile des Berichts ausführlichere Informationen zur Audioqualität anzeigen möchten, markieren Sie die Zeile, und klicken Sie auf **Details zur Audioqualität**. Die folgenden Informationen sind verfügbar:
    
      - **DATUM UND UHRZEIT**   Das Datum und die Uhrzeit des Anrufs in der Zeitzone, die der ausgewählte Benutzer in Outlook Web App festgelegt hat.
    
      - **BENUTZER**   Der ausgewählte Benutzer.
    
      - **UM-WÄHLPLAN**   Der Wählplan für den Anruf.
    
      - **UM-IP-GATEWAY**   Das UM-IP-Gateway, das für den Aufruf verwendet wurde.
    
      - **AUDIOCODEC**   Der während des Anrufs verwendete Audiocodec.
    
      - **NMOS**   Der NMOS-Wert (Network Mean Opinion Score) für den Anruf. Der NMOS-Wert gibt an, wie gut die Audioqualität des Anrufs auf einer Skala von 1 bis 5 war, wobei 5 "ausgezeichnet" ist.
        

        > [!NOTE]
        > Der maximal mögliche NMOS-Wert für einen Anruf hängt vom verwendeten Audiocodec ab. Für sehr kurze Anrufe von weniger als 10&nbsp;Sekunden ist möglicherweise kein NMOS-Wert verfügbar.

    
      - **NMOS-HERABSTUFUNG**   Der Wert für die NMOS-Herabstufung der Audioqualität im Vergleich zum bestmöglichen Wert für den verwendeten Audiocodec. Wenn der NMOS-Herabstufungswert für einen Anruf z. B. 1,2 war, und der gemeldete NMOS-Wert für den Anruf war 3,3, dann ist der maximale NMOS-Wert für diesen Anruf 4,5 (1,2 + 3,3).
    
      - **JITTER**   Die durchschnittliche Variation beim Eingang von Datenpaketen für den Anruf.
    
      - **PAKETVERLUST**   Der durchschnittliche Prozentsatz verloren gegangener Pakete für den ausgewählten Anruf. Der Paketverlust gibt Aufschluss über die Zuverlässigkeit der Verbindung.
    
      - **ROUNDTRIP**   Das durchschnittliche Roundtripergebnis in Millisekunden für den Audioteil des ausgewählten Anrufs. Das Roundtripergebnis gibt Aufschluss über die Latenz der Verbindung.
    
      - **BURSTVERLUSTDAUER**   Die durchschnittliche Dauer des Paketverlusts während Verlustbursts für den ausgewählten Anruf.

