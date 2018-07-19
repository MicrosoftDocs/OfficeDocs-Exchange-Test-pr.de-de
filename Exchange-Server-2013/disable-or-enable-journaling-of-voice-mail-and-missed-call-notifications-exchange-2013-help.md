---
title: 'Deaktivieren oder Aktivieren der Journalfunktion für Voicemail und Benachrichtigungen über verpasste Anrufe: Exchange 2013 Help'
TOCTitle: Deaktivieren oder Aktivieren der Journalfunktion für Voicemail und Benachrichtigungen über verpasste Anrufe
ms:assetid: 5164a92e-69e6-4339-b80c-0cfbf0dc0198
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201690(v=EXCHG.150)
ms:contentKeyID: 50475642
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren oder Aktivieren der Journalfunktion für Voicemail und Benachrichtigungen über verpasste Anrufe

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

In Microsoft Exchange Server 2013 werden Voicemails und Benachrichtigungen über verpasste Anrufe, die vom Unified Messaging-Dienst generiert werden, in das Journal einbezogen, wenn Sie eine Journalregel zum Erfassen von E-Mails erstellen, die an Empfänger oder von Absendern in einer Exchange-Organisation gesendet werden. Verwenden Sie die Verfahren in diesem Thema, um diese Funktion für Ihre gesamte Organisation zu aktivieren oder zu deaktivieren.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit der Journalfunktion gibt? Weitere Informationen finden Sie hier: [Verwalten des Journalings](manage-journaling-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Journale" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktivieren oder Deaktivieren der Journalfunktion für Voicemails und Benachrichtigungen über verpasste Anrufe mithilfe der Shell

In diesem Beispiel wird die Journalfunktion für Voicemails und Benachrichtigungen über verpasste Anrufe deaktiviert, indem der Parameter *VoicemailJournalingEnabled* auf `$false` festgelegt wird.

    Set-TransportConfig -VoicemailJournalingEnabled $false

In diesem Beispiel wird die Journalfunktion für Voicemails und Benachrichtigungen über verpasste Anrufe aktiviert, indem derselbe Parameter auf `$true` festgelegt wird.

    Set-TransportConfig -VoicemailJournalingEnabled $true

Ausführliche Informationen zur Syntax und zu den Parametern finden Sie unter [Set-TransportConfig](https://technet.microsoft.com/de-de/library/bb124151\(v=exchg.150\)).

## Weitere Informationen

[Journale](journaling-exchange-2013-help.md)

[Verwalten des Journalings](manage-journaling-exchange-2013-help.md)

