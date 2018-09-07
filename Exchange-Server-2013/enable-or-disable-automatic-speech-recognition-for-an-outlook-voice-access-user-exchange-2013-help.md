---
title: 'Aktiv. O. Deaktiv. d. autom. Spracherkennung für Outlook Voice Access-Benutzer'
TOCTitle: Aktivieren oder Deaktivieren der automatischen Spracherkennung für einen Outlook Voice Access-Benutzer
ms:assetid: 58f41016-e725-432b-953e-415d61e0664c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232062(v=EXCHG.150)
ms:contentKeyID: 50554833
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der automatischen Spracherkennung für einen Outlook Voice Access-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können die automatische Spracherkennung (Automatic Speech Recognition, ASR) für einen Benutzer konfigurieren, der für Unified Messaging und Voicemail aktiviert wurde. Wenn ASR für das Postfach eines Outlook Voice Access-Benutzers aktiviert ist, kann der Benutzer mithilfe von Sprachbefehlen durch die Postfachmenüs navigieren. Die automatische Spracherkennung ist standardmäßig aktiviert. Wenn ASR deaktiviert ist, muss der Benutzer DTMF-Eingaben (Dual Tone Multi-Frequency), auch Tonwahl genannt, verwenden, um durch die Menüs zu navigieren.


> [!NOTE]
> Dieses Feature kann nicht mithilfe der Exchange-Verwaltungskonsole konfiguriert werden. Sie müssen die Shell verwenden, um die automatische Spracherkennung für einen Voicemailbenutzer zu aktivieren oder zu deaktivieren.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM- oder Voicemailbenutzer finden Sie unter [Verwalten von Voicemail-Einstellungen für einen Benutzer](manage-voice-mail-settings-for-a-user-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Aktivieren oder Deaktivieren der automatischen Spracherkennung für einen UM-aktivierten Benutzer mithilfe der Shell

In diesem Beispiel wird die automatische Spracherkennung für den UM-aktivierten Benutzer `tonysmith` aktiviert.

    Set-UMMailbox -Identity tonysmith@contoso.com -AutomaticSpeechRecognitionEnabled $true

In diesem Beispiel wird die automatische Spracherkennung für den UM-aktivierten Benutzer `tonysmith` deaktiviert.

    Set-UMMailbox -Identity tonysmith@contoso.com -AutomaticSpeechRecognitionEnabled $false

