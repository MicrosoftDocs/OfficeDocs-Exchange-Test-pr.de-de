---
title: 'Aktivieren von Voicemailanmeldungen ohne PIN: Exchange 2013 Help'
TOCTitle: Aktivieren von Voicemailanmeldungen ohne PIN
ms:assetid: 54133753-317c-42ef-9b0d-ca9f2d2d6bd7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg602127(v=EXCHG.150)
ms:contentKeyID: 54652685
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren von Voicemailanmeldungen ohne PIN

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Sie können Unified Messaging (UM) so einrichten, dass die Benutzer sich ohne Verwendung einer PIN bei ihrer Voicemail anmelden können. Standardmäßig werden Outlook Voice Access-Benutzer aufgefordert, eine PIN einzugeben, um sich bei ihrem Postfach anzumelden und auf ihre Voicemail, E-Mail, Kalender, persönlichen Kontakte, das Verzeichnis sowie persönliche Optionen zuzugreifen.


> [!WARNING]
> Mit der Aktivierung von Anmeldungen ohne PIN-Eingabe für einzelne Benutzer oder Benutzergruppen, die für Voicemail aktiviert sind, sinkt die Sicherheitsstufe für Voicemail und wird ein Sicherheitsrisiko für Ihre Organisation eingeführt.



Um Anmeldungen ohne PIN zu ermöglichen, müssen Sie den Parameter *AllowPinlessVoiceMailAccess* für die UM-Postfachrichtlinie auf `$true` und den Parameter *PinlessAccessToVoiceMailEnabled* für das UM-Postfach ebenfalls auf `$true` festlegen. Standardmäßig sind beide Parameter auf `$false` festgelegt. Dies bedeutet, dass ein Outlook Voice Access-Benutzer beim Zugriff auf Voicemail die PIN eingeben muss.

Indem Sie beide Parameter auf `$true` festlegen, können Sie Voicemailanmeldungen ohne PIN für eine große Gruppe von Benutzern ermöglichen, die einem UM-Postfach zugeordnet sind, sowie Anmeldungen ohne PIN für ein einzelnes UM-Postfach oder eine Teilmenge der UM-Postfächer ermöglichen. Auch wenn Sie Voicemailanmeldungen ohne PIN für eine Gruppe UM-aktivierter Benutzer oder einen einzelnen UM-aktivierten Benutzer ermöglichen, wird beim Zugriff auf E-Mail, Kalender, persönliche Kontakte, das Verzeichnis oder persönliche Optionen zur Eingabe der PIN aufgefordert.

Um für einen Benutzer Voicemailanmeldungen ohne PIN zu ermöglichen, müssen die folgenden Bedingungen erfüllt sein:

  - Sie müssen das folgende Cmdlet für die UM-Postfachrichtlinie ausgeführt haben: `Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowPinlessVoiceMailAccess $true`

  - Sie müssen das folgende Cmdlet für das Postfach des UM-aktivierten Benutzers ausgeführt haben: `Set-UMMailbox -id tonys@contoso.com -PinlessAccessToVoiceMailEnabled $true`

  - Der UM-aktivierte Benutzer ist der UM-Postfachrichtlinie zugeordnet, für die Sie Anmeldungen ohne PIN ermöglicht haben.

  - Der UM-aktivierte Benutzer wählt sich über eine zugewiesene Telefonnummer bei Outlook Voice Access ein.

  - Die Shell kann nur für diesen Vorgang verwendet werden. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)). Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

Informationen zu weiteren Aufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

Weitere Informationen zu Aufgaben im Zusammenhang mit UM-Postfächern finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Genaue Anweisungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Bestätigen Sie vor der Durchführung dieser Schritte, dass der Benutzer beziehungsweise die Benutzer für UM und Voicemail aktiviert wurden. Genaue Anweisungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

## Was möchten Sie machen?

## Ermöglichen des Zugriffs auf Voicemail ohne PIN für UM-aktivierte Benutzer mit einer UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wir der Voicemailzugriff ohne PIN für eine UM-Postfachrichtlinie mit dem Namen `MyUMMailboxPolicy` für Benutzer ermöglicht, die der Postfachrichtlinie zugeordnet sind und die sich bei Outlook Voice Access einwählen.

    Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowPinlessVoiceMailAccess $true

## Ermöglichen des Zugriffs auf Voicemail ohne PIN für das Postfach eines UM-aktivierten Benutzers mithilfe der Shell

In diesem Beispiel wird der Voicemailzugriff ohne PIN für den Benutzer ermöglicht, der sich bei Outlook Voice Access einwählt, um das Postfach mit dem Namen `tonys@contoso.com` zu erreichen.

    Set-UMMailbox -id tonys@contoso.com -PinlessAccessToVoiceMailEnabled $true

