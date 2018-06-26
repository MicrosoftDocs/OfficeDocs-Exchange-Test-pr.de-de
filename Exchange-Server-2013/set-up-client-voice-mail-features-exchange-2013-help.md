---
title: 'Einrichten von Client-Voicemailfunktionen: Exchange 2013 Help'
TOCTitle: Einrichten von Client-Voicemailfunktionen
ms:assetid: 5e661cfd-d34e-4caa-91a5-967bbecb75eb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673529(v=EXCHG.150)
ms:contentKeyID: 50554825
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Einrichten von Client-Voicemailfunktionen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-20_

In diesem Thema werden die Clientfeatures beschrieben, die Exchange Unified Messaging-aktivierten Benutzern den Zugriff auf ihre E-Mails und Voicemailnachrichten in ihrem Postfach ermöglichen. Mithilfe dieser Features können Sie den Benutzern einen vereinfachten Voicemail- und E-Mail-Zugriff und eine bessere Benutzerfreundlichkeit bieten.

**Inhalt**

Voice mail client support

Outlook Voice Access

Forwarding calls

Voice Mail Preview

Receiving faxes

## Voicemailclient-Unterstützung

**Exchange ActiveSync-Clients**   Mithilfe des Microsoft Exchange ActiveSync-Protokolls wird eine Verbindung von mobilen Clients, z. B. Clients auf internetfähigen mobilen Geräten, mit einem Exchange-Postfach hergestellt. Benutzer können mithilfe von mobilen Geräten auf ihr Postfach zugreifen und E-Mails abrufen, Kalender- und Kontaktinformationen anzeigen und ändern sowie ihre Voicemailnachrichten abhören. Sie können außerdem ihre E-Mails, Voicemailnachrichten, Kalenderelemente und Kontaktinformationen mit anderen Geräten synchronisieren.

**Outlook-Integration**   Mithilfe von Microsoft Outlook können Benutzer auf ihr Exchange-Postfach zugreifen und E-Mails in ihrem Postfach anzeigen, Kalenderinformationen anzeigen und ändern sowie Sprachnachrichten mithilfe von Microsoft Windows Media Player abhören, der in die E-Mails eingebettet ist. Durch Verwendung eines unterstützten E-Mail-Clients stehen den Benutzern zusätzliche Features zur Verfügung, z. B. die Funktion für die Wiedergabe über Telefon.

**Outlook Web App-Integration**   Microsoft Outlook Web App bietet Benutzern eine Reihe von UM-Schnittstellen und -Tools, die mit einem vollständig ausgestatteten E-Mail-Client wie Outlook vergleichbar sind. Mit Outlook Web App können Benutzer über einen kompatiblen Webbrowser auf ihr Exchange-Postfach zugreifen. Wie in Outlook ist auch in Outlook Web App Windows Media Player verfügbar – eingebettet in die E-Mails, sodass die Benutzer Sprachnachrichten abhören und auf andere Features zugreifen können, z. B. das Feature für die Wiedergabe über Telefon.

## Outlook Voice Access

In Exchange Unified Messaging kann ein UM-aktivierter Benutzer zum Zugriff auf sein Postfach eine interne oder externe Telefonnummer anrufen (die im UM-Wählplan konfiguriert ist) und das Outlook Voice Access-Menüsystem verwenden. Mithilfe des Menüs können UM-aktivierte Benutzer E-Mails lesen, Sprachnachrichten abhören, mit ihrem Outlook-Kalender arbeiten, auf ihre persönlichen Kontakte zugreifen und Aufgaben ausführen, beispielsweise das Konfigurieren ihrer Outlook Voice Access-PIN oder das Aufzeichnen von Voicemails. Weitere Informationen finden Sie unter [Einrichten von Outlook Voice Access](setting-up-outlook-voice-access-exchange-2013-help.md).

## Weiterleiten von Anrufen

Ein UM-aktivierter Benutzer kann Mailboxansageregeln mithilfe von Outlook oder Outlook Web App erstellen oder konfigurieren. Mithilfe von Mailboxansageregeln können Benutzer steuern, wie eingehende Anrufe behandelt werden. Diese Regeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails, und sie werden wie andere Spracheinstellungen im Postfach des Benutzers gespeichert. Für jedes UM-aktivierte Postfach können bis zu neun Mailboxansageregeln eingerichtet werden. Diese Regeln gelten unabhängig von den Posteingangsregeln und schmälern nicht das Kontingent der Posteingangsregeln. Weitere Informationen finden Sie unter [Zulassen, dass Voice Mailbenutzer Anrufe weitergeleitet werden sollen](allow-voice-mail-users-to-forward-calls-exchange-2013-help.md).

## Voicemailvorschau

Die Voicemailvorschau ist ein Feature, das Benutzer beim Empfang ihrer Voicemailnachrichten vom UM-Voicemailsystem nutzen können. Die Voicemailvorschau erweitert die Voicemailfunktion, indem eine Textversion der Audioaufzeichnungen bereitgestellt wird. Weitere Informationen finden Sie unter [Zulassen der Anzeige von Voicemailtranskriptionen für Benutzer](allow-users-to-see-a-voice-mail-transcript-exchange-2013-help.md).

## Faxempfang

UM leitet eingehende Faxanrufe für einen UM-aktivierten Benutzer an eine dafür vorgesehene Faxpartnerlösung weiter, die dann die Faxverbindung mit dem Faxabsender aufbaut und die Nachricht für den Benutzer empfängt. Damit UM-aktivierte Benutzer Faxnachrichten in ihrem Postfach empfangen können, müssen Sie wie folgt vorgehen:

  - Aktivieren Sie eingehende Faxe für den UM-Wählplan, der mit den Benutzern verknüpft ist, indem Sie den Parameter *FaxEnabled* auf `$true` festlegen.

  - Aktivieren Sie eingehende Faxe für den UM-Wählplan, der mit den Benutzern verknüpft ist, indem Sie den Parameter *Allowfax* auf `$true` festlegen.

  - Aktivieren Sie eingehende Faxe für die Benutzer, indem Sie den Parameter *FaxEnabled* auf `$true` festlegen.

  - Legen Sie den Partnerfaxserver-URI fest, um eingehende Faxe zuzulassen.

  - Konfigurieren Sie die Authentifizierung zwischen dem Postfachserver und dem Server des Faxpartners.

