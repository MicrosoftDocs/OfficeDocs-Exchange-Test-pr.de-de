---
title: 'Ablaufverfolgung für die Inhaltskonvertierung: Exchange 2013 Help'
TOCTitle: Ablaufverfolgung für die Inhaltskonvertierung
ms:assetid: eb9c7df2-9093-49f9-aa4f-044909bd2225
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb397226(v=EXCHG.150)
ms:contentKeyID: 50476994
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ablaufverfolgung für die Inhaltskonvertierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-25_

Die Ablaufverfolgung für die Inhaltskonvertierung erfasst Fehler der MAPI-Inhaltskonvertierung, die vom Postfachtransportdienst für eingehende und ausgehende Nachrichten auf einem Microsoft Exchange Server 2013-Postfachserver ausgeführt wird.

Der Postfachtransportdienst auf einem Postfachserver ist für die Inhaltskonvertierung von Nachrichten zuständig, die an und von Postfachempfänger(n) gesendet werden. Genauer gesagt konvertiert der Dienst für die Postfachtransportübermittlung ausgehende Nachrichten von Postfachbenutzern von MAPI nach MIME. Der Dienst für die Postfachtransportzustellung konvertiert eingehende Nachrichten für Postfachbenutzer von MIME nach MAPI. Die Ablaufverfolgung für die Inhaltskonvertierung ist für die Erfassung dieser MAPI-Konvertierungsfehler zuständig.

Das Kategorisierungsmodul im Transportdienst auf einem Postfachserver ist für die Inhaltskonvertierung aller Nachrichten zuständig, die an externe Empfänger gesendet werden. Die Ablaufverfolgung für die Inhaltskonvertierung erfasst keine Fehler der Inhaltskonvertierung, die vom Kategorisierungsmodul im Transportdienst bei der Konvertierung von Nachrichten erkannt werden, die an externe Empfänger gesendet werden.

**Inhalt**

Konfigurieren der Ablaufverfolgung für die Inhaltskonvertierung

Arbeitsweise der Ablaufverfolgung für die Inhaltskonvertierung

Überlegungen zur Ablaufverfolgung für die Inhaltskonvertierung

## Konfigurieren der Ablaufverfolgung für die Inhaltskonvertierung

Die Ablaufverfolgung der Inhaltskonvertierung wird durch die folgenden Parameter in den Cmdlets **Set-TransportService** und **Set-MailboxTransportService** in der Exchange-Verwaltungsshell gesteuert:

  - *ContentConversionTracingEnabled*   Über diesen Parameter wird die Ablaufverfolgung der Inhaltskonvertierung im Transportdienst auf dem Postfachserver oder im Postfachtransportdienst auf dem Postfachserver aktiviert oder deaktiviert. Gültige Werte für diesen Parameter sind `$true` und `$false`. Der Standardwert ist `$false`. Wenn Ihre Exchange-Organisation mehrere Postfachserver enthält, müssen Sie die Ablaufverfolgung der Inhaltskonvertierung auf jedem Postfachserver aktivieren.

  - *PipelineTracingPath*   Zwar ist dieser Parameter der Pipelineablaufverfolgung zugeordnet, er gibt jedoch außerdem den Stammspeicherort der Ablaufverfolgungsdateien für die Inhaltskonvertierung an. Der Standardspeicherort im Transportdienst ist `%ExchangeInstallPath%TransportRoles\Logs\Hub\PipelineTracing`. Der Standardspeicherort im Postfachtransportdienst ist `%ExchangeInstallPath%TransportRoles\Logs\Mailbox\PipelineTracing`. Bei dem Pfad muss es sich um einen lokalen Pfad auf dem Exchange-Computer handeln.

Die Inhaltskonvertierung erstellt einen Ordner mit dem Namen `ContentConversionTracing` in dem Pfad, der im Parameter *PipelineTracingPath* angegeben wird. Innerhalb des Ordners `ContentConversionTracing` erstellt die Inhaltskonvertierung zwei Unterordner: `InboundFailures` und `OutboundFailures`. Der Ordner `InboundFailures` enthält die Informationen aus Fehlern der Inhaltskonvertierung für eingehende Nachrichten. Der Ordner `OutboundFailures` enthält die Informationen aus Fehlern der Inhaltskonvertierung für ausgehende Nachrichten.

Die maximale Größe für alle Dateien im Ordner `InboundFailures` oder `OutboundFailures` beträgt 128 MB. Die Ablaufverfolgung der Inhaltkonvertierung verwendet keine Umlaufprotokollierung, um alte Dateien abhängig von ihrem Alter oder ihrer Größe zu entfernen. Sobald die maximale Größe für einen Ordner erreicht wird, beendet die Ablaufverfolgung der Inhaltskonvertierung das Schreiben von Informationen in den Ordner. Wenn Sie sicherstellen möchten, dass die Grenzwerte für die maximale Ordnergröße nicht überschritten werden, können Sie einen geplanten Task erstellen, der die Ablaufverfolgungsdateien der Inhaltskonvertierung regelmäßig an einen anderen Speicherort verschiebt.

Diese Berechtigungen sind für die in der Ablaufverfolgung für die Inhaltskonvertierung verwendeten Ordner und Unterordner erforderlich:

  - Administratoren: Vollzugriff

  - Netzwerkdienst: Vollzugriff

  - System: Vollzugriff


> [!WARNING]
> Die Ablaufverfolgung der Inhaltskonvertierung kopiert die gesamten Inhalte von E-Mail-Nachrichten. Um die unerwünschte Preisgabe vertraulicher Informationen zu vermeiden, müssen Sie für den Speicherort der Ablaufverfolgungsdateien der Inhaltskonvertierung geeignete Sicherheitsberechtigungen festlegen.



Zurück zum Seitenanfang

## Arbeitsweise der Ablaufverfolgung für die Inhaltskonvertierung

Wenn bei der Inhaltskonvertierung einer eingehenden Nachricht ein Fehler auftritt, wird eine Benachrichtigung über den Zustellungsstatus (Delivery Status Notification, DSN) mit dem Statuscode 5.6.0 an den Absender der Nachricht gesendet. Wenn die Ablaufverfolgung der Inhaltskonvertierung aktiviert ist, werden die Fehlerinformationen zu dem Zeitpunkt erfasst, zu dem die 5.6.0-DSN-Nachricht erstellt wird. Für jeden Fehler der Inhaltskonvertierung werden zwei separate Dateien erstellt.

Für einen Fehler bei der Inhaltskonvertierung, der beim Konvertieren einer eingehenden Nachricht von MIME nach MAPI auftritt, werden die zwei folgenden Dateien im Ordner **InboundFailures** erstellt:

  - **\<GUID\>.eml**   Diese Datei enthält die fehlgeschlagene Nachricht im Textformat.

  - **\<GUID\>.txt**   Diese Datei enthält die Ausnahmebeschreibung, die Konvertierungsergebnisse, die Konvertierungsoptionen und die Grenzwerte der Nachrichtengröße, die vom Postfachtransportdienst auf alle Nachrichten angewendet werden.

Für einen Fehler bei der Inhaltskonvertierung, der beim Konvertieren einer ausgehenden Nachricht von MAPI nach MIME auftritt, werden die zwei folgenden Dateien im Ordner **OutboundFailures** erstellt:

  - **\<GUID\>.msg**   Diese Datei enthält die fehlerhafte Nachricht im Microsoft Outlook-Nachrichtenformat.

  - **\<GUID\>.txt**   Diese Datei enthält die Ausnahmebeschreibung, die Konvertierungsergebnisse, die Konvertierungsoptionen und die Grenzwerte der Nachrichtengröße, die vom Informationsspeichertreiber auf alle Nachrichten angewendet werden.

Der Platzhalter \<*GUID*\> ist für beide Dateinamen gleich. Durch jeden Fehler bei der Inhaltskonvertierung wird eine andere GUID erstellt, die in den Dateinamen der entsprechenden Nachrichten- und Textdateien verwendet wird. Ein Beispiel für eine GUID, die in den Dateinamen verwendet wird, ist `038b930e-61fd-4bfd-b9b4-0374c18b73f7`.

Zurück zum Seitenanfang

## Überlegungen zur Ablaufverfolgung für die Inhaltskonvertierung

Für eine proaktive Überwachung kann die Ablaufverfolgung der Inhaltskonvertierung aktiviert bleiben. Die Ablaufverfolgung für die Inhaltskonvertierung kann jedoch auch aktiviert werden, um eine Problembehebung für ein bestimmtes Fehlerereignis durchzuführen. In der Regel können Fehler bei der Konvertierung eingehender Inhalte reproduziert werden, indem der Empfänger der 5.6.0-DSN-Nachricht zum erneuten Senden der Originalnachricht aufgefordert wird.

Fehler bei der Inhaltskonvertierung eingehender Nachrichten stellen den häufigsten Fall dar. Dies sind einige der Gründe für Konvertierungsfehler bei eingehenden Inhalten:

  - **Verletzungen der Grenzwerte für die Nachrichtengröße**   Diese Grenzwerte für die Nachrichtengröße werden vom Postfachtransportdienst angewendet, um die Abwehr von DoS-Angriffen (Denial of Service) zu unterstützen. Diese Nachrichtengrenzwerte sind in der Datei \<*GUID*\>.txt aufgelistet. Zu diesen Nachrichtengrenzwerten gehören die folgenden:
    
      - **MaxMimeTextHeaderLength**   Dieser Grenzwert gibt die maximale Anzahl der Textzeichen an, die in einer MIME-Kopfzeile verwendet werden können. Der Wert lautet 2000.
    
      - **MaxMimeSubjectLength**   Dieser Grenzwert gibt die maximale Anzahl der Textzeichen an, die in der Betreffzeile verwendet werden können. Der Wert lautet 255.
    
      - **MSize**   Dieser Grenzwert gibt die maximale Nachrichtengröße an. Der Wert lautet 2147483647 Byte.
    
      - **MaxMimeRecipients**   Dieser Grenzwert gibt die Gesamtzahl der Empfänger an, die in den Feldern **An**, **Cc** und **Bcc** aufgeführt werden können. Der Wert lautet 12288.
    
      - **MaxRecipientPropertyLength**   Dieser Grenzwert gibt die maximale Anzahl der Textzeichen an, die in einer Empfängerbeschreibung verwendet werden können. Der Wert lautet 1000.
    
      - **MaxBodyPartsTotal**   Dieser Grenzwert gibt die maximale Anzahl der Nachrichtenteile an, die in einer MIME-Multipart-Nachricht verwendet werden können. Der Wert lautet 250.
    
      - **MaxEmbeddedMessageDepth**   Dieser Grenzwert gibt die maximale Anzahl der weitergeleiteten Nachrichten an, die in einer Nachricht enthalten sein können. Der Wert lautet 30.
    
    Weitere Informationen zu konfigurierbaren Grenzwerten für die Nachrichtengröße, die im Transportdienst auf Postfachservern oder auf Edge-Transport-Servern verwendet werden, finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

  - **Fehler beim Konvertieren einer eingehenden iCalendar-Nachricht in eine Besprechungsanforderung**   RFC 2445 definiert iCalendar als einen Standard für den Austausch von Kalenderdaten. Die folgenden spezifischen Ursachen für Konvertierungsfehler treten auf:
    
      - Falsche Verwendung von iCalendar vom sendenden Agent.
    
      - Strukturen von iCalendar, die vom Outlook- oder Exchange-Kalenderschema nicht unterstützt werden können.
    
    Konvertierungsfehler von iCalendar führen nicht dazu, dass der Absender eine 5.6.0-DSN-Nachricht erhält. Stattdessen wird die Nachricht mit einer angehängten **ICS**-Datei übermittelt, die den Text der iCalendar-Nachricht enthält.

  - **Durch falsch formatierte MIME-Nachrichten verursachte Fehler**   Unaufgefordert gesendete Werbe-E-Mails oder Spamnachrichten können Formatierungsfehler im Nachrichtenkopf aufweisen, wie etwa nicht geschlossene Anführungszeichen in Empfängerbeschreibungen. Eine viel kleinere Anzahl von Fehlern, die durch MIME-Formatierungsfehler verursacht werden, wird als Bug angesehen.

Fehler bei der Inhaltskonvertierung von ausgehenden Nachrichten sind viel seltener als Fehler im Eingang. Fehler in ausgehenden Nachrichten werden normalerweise durch Codefehler in Exchange oder beschädigte Nachrichteninhalte verursacht.

Zurück zum Seitenanfang

