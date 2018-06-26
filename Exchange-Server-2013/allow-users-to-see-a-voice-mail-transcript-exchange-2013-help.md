---
title: 'Zulassen der Anzeige von Voicemailtranskriptionen für Benutzer: Exchange 2013 Help'
TOCTitle: Zulassen der Anzeige von Voicemailtranskriptionen für Benutzer
ms:assetid: c5192e05-905c-440f-beec-1f697edc15b3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff629381(v=EXCHG.150)
ms:contentKeyID: 51409344
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zulassen der Anzeige von Voicemailtranskriptionen für Benutzer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Die Voicemailvorschau ist eine Funktion, die Benutzer beim Empfang ihrer Voicemailnachrichten von Unified Messaging (UM) nutzen können. Die Voicemailvorschau erweitert die vorhandene UM-Voicemailfunktion, indem eine Textversion der Audioaufzeichnungen bereitgestellt wird. Der Voicemailtext wird in E-Mail-Nachrichten innerhalb von MicrosoftOutlook Web App, Outlook 2010 und höheren Versionen sowie anderen unterstützten E-Mail-Programmen angezeigt. Weitere Informationen finden Sie unter [Microsoft-Sprachtechnologien](http://go.microsoft.com/fwlink/p/?linkid=187348).

## Müssen Benutzer ein bestimmtes E-Mail-Programm verwenden?

Nein. Die Voicemailvorschau ist im Nachrichtentext eines beliebigen E-Mail-Programms (einschließlich mobiler Programme) enthalten. Wenngleich Benutzer andere E-Mail-Programme für den Empfang von Sprachnachrichten verwenden können, bieten Outlook und Outlook Web App das beste Benutzererlebnis. Wenn der Benutzer z. B. in Outlook 2010 und höheren Versionen im Voicemailvorschautext auf ein bestimmtes Wort klickt, beginnt die Wiedergabe der Sprachnachricht bei diesem Wort. Dies ist nützlich, um einen bestimmten Teil einer Sprachnachricht wiederzugeben.

## Können Benutzer nach bestimmten Voicemailnachrichten suchen?

Ja. Wörter und Sätze im Voicemailvorschautext werden automatisch indiziert, sodass Sprachnachrichten in den Suchergebnissen enthalten sind. In Outlook 2010 und höheren Versionen oder in Outlook Web App können Benutzer über das Feld **Audionotizen** ferner Text zu einer Sprachnachricht hinzufügen. Diese Notizen werden bei Suchvorgängen ebenso berücksichtigt, um das Auffinden einer Nachricht zu vereinfachen.

## Weshalb lautet der Name der Funktion "Voicemailvorschau"?

Es ist wichtig, bei den Benutzern keine falschen Erwartungen zu wecken. Bei der Voicemailvorschau stimmt der Text nicht unbedingt exakt mit der Sprachnachricht des Anrufers überein. Tatsächlich weicht der Text üblicherweise etwas ab. Wenn der Name "Transkription" lauten würde, ließe dies ein besseres Ergebnis vermuten, als im Allgemeinen erreicht werden kann. Der Begriff "Vorschau" weist jedoch darauf hin, dass der Leser einen ersten Einblick in den Inhalt der Sprachnachricht erhält, was der tatsächlichen Funktion eher entspricht.

## Wodurch wird die Zuverlässigkeit des Voicemailvorschautexts erhöht oder verringert?

Die Zuverlässigkeit des Voicemailvorschautexts hängt von einer Vielzahl von Faktoren ab, die manchmal nicht beeinflusst werden können. Die folgenden Faktoren können jedoch dazu beitragen, die Zuverlässigkeit des Voicemailvorschautexts zu erhöhen:

  - Der Anrufer hinterlässt eine einfache Sprachnachricht, die keine Umgangssprache, technischen Fachwörter oder ungewöhnlichen Wörter und Sätze enthält.

  - Der Anrufer spricht eine Sprache, die problemlos vom Voicemailsystem erkannt und übersetzt werden kann. Im Allgemeinen wird die Zuverlässigkeit der Vorschau erhöht, wenn die Anrufer beim Hinterlassen von Sprachnachrichten nicht zu schnell oder zu leise und ohne starken Dialekt sprechen.

  - Die Sprachnachricht enthält keine Hintergrundgeräusche, Echos oder Tonaussetzer.

## Welche Sprachen können mit der Voicemailvorschau verwendet werden?

Voicemailvorschautext ist in den folgenden Sprachen verfügbar:

  - Englisch (USA) (en-US)

  - Englisch (Kanada) (en-CA)

  - Französisch (Frankreich) (fr-FR)

  - Italienisch (it-IT)

  - Polnisch (pl-PL)

  - Portugiesisch (Portugal) (pt-PT)

  - Spanisch (Spanien) (es-ES)

Wenn Sie über eine lokale oder Hybridbereitstellung von UM verfügen, können die UM-Sprachpakete aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=266542) heruntergeladen werden.

Bei einer lokalen oder Hybridbereitstellung können nach der Installation eines UM-Sprachpakets die Wählpläne und automatischen Telefonzentralen für die gewählte Sprache konfiguriert werden. Bei der Online-Version müssen Sie keine Sprachpakete installieren. Viele Unternehmen verfügen über nur einen UM-Wählplan. Es wird versucht, eine Voicemailvorschau in der Standardsprache des Wählplans zu erstellen. Die Standardsprache muss die Voicemailvorschau jedoch unterstützen. Ein UM-Wählplan kann lediglich zum Erstellen von Voicemailvorschauen in jeweils einer Sprache konfiguriert werden.

Um Unified Messaging für die Bereitstellung von Voicemailvorschauen in einer anderen Sprache als Englisch (USA) zu konfigurieren, führen Sie die folgenden Schritte aus:

1.  Stellen Sie sicher, dass die Voicemailvorschau in der gewünschten Sprache unterstützt wird.

2.  Laden Sie bei einer lokalen oder Hybridbereitstellung das gewünschte UM-Sprachpaket herunter, und installieren Sie es. Durch das Herunterladen und Installieren des Sprachpakets wird die Standardsprache des Wählplans nicht konfiguriert.

3.  Konfigurieren Sie für den Wählplan die Sprache, die für die Voicemailvorschau verwendet wird. Weitere Informationen finden Sie unter [Festlegen der Standardsprache für einen Wählplan](set-the-default-language-on-a-dial-plan-exchange-2013-help.md).

Wie Voicemailvorschautext in den unterstützen Sprachen angezeigt wird, hängt vom Typ der gesendeten Sprachnachricht ab. Es gibt zwei Typen:

  - **Sprachnachrichten, die bei nicht beantworteten Anrufen aufgezeichnet werden**
    
    Bei diesen Nachrichten wird die für die Voicemailvorschau verwendete Sprache anhand der Sprache des Anrufers und basierend darauf bestimmt, ob die Sprache unterstützt wird. Wenn der Anrufer z. B. eine Sprachnachricht auf Italienisch hinterlässt, wird der Voicemailvorschautext auf Italienisch angezeigt, wenn diese Sprache für den Wählplan konfiguriert wurde. Wenn der Anrufer jedoch eine Nachricht auf Japanisch hinterlässt, umfasst die Nachricht keinen Voicemailvorschautext, da diese Sprache nicht verfügbar ist.

  - **Von einem Outlook Voice Access-Benutzer gesendete Sprachnachrichten**
    
    Bei Nachrichten, die von einem Outlook Voice Access-Benutzer gesendet werden, wird die Sprache der Voicemailvorschau vom Voicemailadministrator bestimmt. Für den Text der Voicemailvorschau wird die Sprache des Voicemailsystems verwendet. Wenn jedoch ein Anrufer, der keine von der Voicemailvorschau unterstützte Sprache spricht, Outlook Voice Access zum Hinterlassen einer Nachricht verwendet, enthält die Nachricht keinen Voicemailvorschautext. Weitere Informationen zu Outlook Voice Access finden Sie unter [Einrichten von Outlook Voice Access](setting-up-outlook-voice-access-exchange-2013-help.md).

## Erkennt UM, wenn eine Voicemailvorschau ungenau ist?

Der Zuverlässigkeitswert wird für jede Voicemailvorschau bestimmt, die in einer Sprachnachricht enthalten ist. Das Voicemailsystem misst, inwieweit der Ton in der Aufzeichnung den Wörtern, Zahlen und Ausdrücke entspricht. Wenn Entsprechungen mühelos gefunden werden, ist der Zuverlässigkeitswert hoch. Ein hoher Zuverlässigkeitswert weist üblicherweise auf eine hohe Genauigkeit der Vorschau hin.

Wenn der Zuverlässigkeitswert unter einem bestimmten Wert liegt, wird über dem Text der Voicemailvorschau der Satz **Voicemailvorschau (geringe Zuverlässigkeit)** angezeigt. Bei einem geringen Zuverlässigkeitswert ist es wahrscheinlich, dass der Voicemailvorschautext ungenau ist.

Unified Messaging verwendet zum Berechnen der Vorschauzuverlässigkeit die automatische Spracherkennung. Es kann jedoch nicht ermittelt werden, welche Wörter richtig und welche falsch wiedergegeben werden.

UM versucht jedoch, die Zuverlässigkeit der Voicemailvorschau weiter zu verbessern. Es wird beispielsweise versucht, die Telefonnummer des Anrufers (falls bereitgestellt) mit den persönlichen Kontakten des Benutzers und dem Adressbuch Ihrer Organisation sowie Kontakten in sozialen Netzwerken abzugleichen. Wenn UM eine Übereinstimmung ermittelt, werden bei der automatischen Spracherkennung für die Sprachaufzeichnung der Name des Anrufers sowie die Standardlisten mit Namen und Wörtern aufgenommen.

## Kann die Voicemailvorschau verwendet werden, wenn sie nicht absolut zuverlässig ist?

Das Benutzererlebnis bei der Voicemailvorschau wird verbessert, wenn die Benutzer nicht versuchen, die Vorschau Wort für Wort zu lesen. Stattdessen sollten sie nach Namen, Telefonnummern und Hinweisen wie "Rückruf" oder "Möchte mit Ihnen sprechen" suchen, anhand derer sich der Grund des Anrufs ermitteln lässt.

Der Zweck der Voicemailvorschau ist nicht die präzise Wiedergabe des Nachrichteninhalts, sondern die Funktion soll lediglich dazu beitragen, u. a. die folgenden Fragen zu beantworten:

  - Bezieht sich diese Sprachnachricht auf meine Arbeit?

  - Ist diese Sprachnachricht wichtig für mich?

  - Hat der Anrufer eine Telefonnummer hinterlassen? Unterscheidet sich diese Nummer von den Telefonnummern in meiner Liste?

  - Betrachtet der Anrufer diese Sprachnachricht als dringend?

  - Muss ich ein Meeting verlassen, um den Anrufer zurückzurufen?

  - Ich habe einen Anruf zur Bestätigung einer Anfrage erwartet. Handelt es sich um diesen Anruf?

## Kann die Voicemailvorschau aktiviert oder deaktiviert werden?

Ja. Bei aktivierter Voicemailvorschau können Benutzer die Funktion über Outlook 2010 oder eine höhere Version oder Outlook Web App aktivieren oder deaktivieren. Die Sprache des Wählplans muss die Voicemailvorschau jedoch unterstützen, und das entsprechende UM-Sprachpaket muss installiert sein.

Wenngleich bei Verwendung von Outlook 2010 oder einer höheren Version und Outlook Web App dieselben Einstellungen für die Voicemailvorschau verwendet werden, wird unterschiedlich auf diese Einstellungen zugegriffen:

**Outlook Web App**

In Outlook Web App klicken Benutzer auf **Einstellungen** \> **Telefon** \> **Voicemail**, um auf die Einstellungen für die Voicemailvorschau zuzugreifen. Auf der Seite **Voicemail** stehen die Einstellungen unter **Voicemailvorschau** zur Verfügung.

Standardmäßig sind beide Voicemailvorschauoptionen verfügbar, wenn ein Benutzer für Unified Messaging aktiviert ist. Wenn der UM-Wählplan für die Verwendung eines UM-Sprachpakets mit Unterstützung der Voicemailvorschau konfiguriert sind, erstellt Unified Messaging in den folgenden Fällen eine Voicemailvorschau für die Benutzer:

  - Ein Anrufer hinterlässt eine Voicemailnachricht, weil sein Anruf nicht entgegengenommen wird.

  - Ein UM-aktivierter Benutzer meldet sich an Outlook Voice Access an und zeichnet eine Sprachnachricht für einen oder mehrere Empfänger auf.

Wenn ein Anrufer eine Sprachnachricht hinterlässt und die Option **Vorschautext in Sprachnachrichten einschließen, die ich erhalte** aktiviert ist, erstellt Unified Messaging eine Voicemailvorschau in der E-Mail-Nachricht, fügt die Audiodatei an und sendet die Nachricht an das Postfach des Empfängers. Sie können diese Option deaktivieren, wenn die für den Wählplan konfigurierte Sprache die Voicemailvorschau nicht unterstützt und Sie keine Voicemailvorschauen in Voicemailnachrichten aufnehmen möchten.

Wenn sich Benutzer an Outlook Voice Access anmelden und eine Sprachnachricht an einen anderen Benutzer senden, können Sie das Kontrollkästchen **Vorschautext in Sprachnachrichten einschließen, die ich mit Outlook Voice Access sende** deaktivieren. Dies bietet sich beispielsweise an, wenn Sprachnachrichten in einer Sprache gesendet werden, die von der Voicemailvorschau nicht unterstützt wird, oder sie die Voicemailvorschau nicht in die Sprachnachricht einschließen möchten, da diese zu lang ist.

