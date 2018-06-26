---
title: 'Voicemail-Vorschau Erweiterungen: Exchange 2013 Help'
TOCTitle: Voicemail-Vorschau Erweiterungen
ms:assetid: 1fcccec1-4edc-40b8-948c-111647d7d770
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150501(v=EXCHG.150)
ms:contentKeyID: 50475196
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Voicemail-Vorschau Erweiterungen

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-07-05_

Die Voicemailvorschau ist eine Funktion, die Benutzer unter Verwendung von Microsoft Exchange Server 2010 oder Exchange Server 2013 Unified Messaging (UM) nutzen können, wenn sie Voicemailnachrichten empfangen. Die Voicemailvorschau erweitert die UM-Voicemailfunktion, indem eine Textversion der Audioaufzeichnungen bereitgestellt wird. Der Voicemailtext wird in einer E-Mail innerhalb von Microsoft Office Outlook Web App, Outlook 2010 und anderen E-Mail-Programmen angezeigt.

## Verbesserungen bei der Voicemailvorschau

In Exchange 2013 bietet Unified Messaging verschiedene Erweiterungen der Benutzeroberfläche für Outlook Web App- und Outlook-Clients sowie eine verbesserte Zuverlässigkeit und Genauigkeit für die Voicemailvorschau. Darüber hinaus sind über Microsoft Speech Platform (Version 11.0) und Unified Communications Managed API (UCMA) 4.0 Erweiterungen bei den sprachbezogenen Diensten verfügbar, um die Grammatikgenerierung und die Sprachunterstützung zu verbessern.

Die Voicemailvorschau wurde in der Unified Messaging-Komponente von Exchange 2010 eingeführt. Für die Voicemailvorschau wird die automatische Spracherkennung verwendet, um eine Textversion einer Voicemailaudiodatei zu einer Sprachnachricht hinzuzufügen. Die automatische Spracherkennung ist nicht immer exakt, insbesondere wenn sie für die Aufzeichnung von Ton mit unbekannten Stimmen und Geräuschen über ein Telefon verwendet wird.

Einige Organisationen benötigen konstant fehlerfreie (oder fast fehlerfreie) Transkriptionen von Voicemailnachrichten für einige – wenn nicht alle – Benutzer. Das Voicemailvorschau-Partnerprogramm unterstützt diese Organisationen bei der Erfüllung dieser Anforderungen. Das Voicemailvorschau-Partnerprogramm wurde für Exchange 2010 entworfen, um die Ergebnisse der Voicemailvorschau zu verbessern, wurde aufgrund des Overheads und der Kosten jedoch nicht von Exchange 2010-Kunden verwendet. Um diese Probleme zu lösen, wurde die Voicemailvorschau in Exchange 2013 wie folgt verbessert:

  - **Verbesserte Audionormalisierung**   Bei der Audionormalisierung wird die Amplitude eines Audiosignals einheitlich erhöht (oder gesenkt), sodass die resultierende maximale Amplitude einem angegebenen Ziel oder dem Normalwert entspricht. Unified Messaging normalisiert die Audioaufzeichnung, bevor sie komprimiert und an den Benutzer gesendet wird.

  - **Verbesserte Spracherkennung**   Durch die Erfassung von Voicemailnachrichten (sofern der Exchange-Kunde der Freigabe dieser Informationen zustimmt) können die Ergebnisse der Voicemailvorschau verwendet werden, um dem Sprachmodul Wörter und Ausdrücke hinzuzufügen. Zu diesem Zweck wird der Parameter *VoiceMailAnalysisEnabled* des Cmdlets **Set-UMMailbox** auf `$true` oder der Parameter *AllowVoiceMailAnalysis* des Cmdlets **Set-UMMailboxPolicy** auf `$true` gesetzt. Darüber hinaus werden Informationen aus E-Mail-Threads, die von einem Benutzer über Outlook Voice Access erstellt wurden, in Exchange 2013 Unified Messaging effizienter verwendet. Dies umfasst Informationen (Land, Ort, Unternehmen) zum Teilnehmer (Active Directory- oder persönlicher Kontakt), sowie die Telefonnummer des Outlook Voice Access-Benutzers.

  - **Zuverlässigkeit der Voicemailvorschau**   Der Zuverlässigkeitswert gibt die von Unified Messaging zugewiesene Nummer an, die direkt mit der allgemeinen Genauigkeit der Transkription in Zusammenhang steht. Die von Unified Messaging verwendeten Berechnungen der Zuverlässigkeit wurden angepasst, um präzisere Ergebnisse zu liefern und der tatsächlichen Genauigkeit einer transkribierten Nachricht zu entsprechen.

  - **Filterung**   Anstößige Wörter werden ermittelt und herausgefiltert, und die Ergebnisse werden zwischengespeichert und im Postfach des Benutzers gespeichert.

  - **Ausblenden der Textvorschau**   Wenn der Zuverlässigkeitswert einer Voicemailvorschau einen bestimmten Schwellenwert unterschreitet, wird der Text der Voicemailvorschau ausgeblendet. Wenn der Text ausgeblendet wird, wird in der Sprachnachricht ein Hinweis eingefügt, der besagt, dass die Zuverlässigkeit der Voicemailvorschau zu gering war und die Ergebnisse nicht angezeigt werden.

  - **Transkriptionsleistung**   Die Voicemailvorschau ist ein CPU-intensiver Vorgang, der etwa zweimal so viel Zeit in Anspruch nimmt wie die Verarbeitung einer Audiodatei. Wenn die Generierung des Texts für die Voicemailvorschau zu viel Zeit in Anspruch nimmt, wird die Verarbeitung der Vorschau durch die CPU-Drosselung angehalten. In Exchange 2010 wurden Sprachnachrichten mit einer Dauer von mehr als 75 Sekunden nicht von der Unified Messaging-Komponente transkribiert. In Exchange 2013 wird die vollständige Sprachnachricht transkribiert, der Text für die Nachricht wird jedoch nicht hinzugefügt, wenn die Dauer von 75 Sekunden überschritten wird.

  - **Farbschemas**   Da die Farben, die zum Unterscheiden zwischen den verschiedenen Zuverlässigkeitsstufen bei einer Voicemailvorschau verwendet wurden, zu Verwirrung geführt haben, wurde das Farbschema in Exchange 2013 für Outlook Web App und Outlook entfernt.

