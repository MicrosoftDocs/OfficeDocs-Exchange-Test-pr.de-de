---
title: 'Festlegen der Anzahl von Anmeldefehlern vor Zurücksetzung der Voicemail-PIN'
TOCTitle: Festlegen Sie die Anzahl der Anmeldung Fehler vor einer Voicemail, die PIN zurücksetzen,
ms:assetid: 4de38499-0a6f-4f00-8697-eeff805d7266
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997939(v=EXCHG.150)
ms:contentKeyID: 50554817
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen Sie die Anzahl der Anmeldung Fehler vor einer Voicemail, die PIN zurücksetzen,

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können konfigurieren, welche Anzahl von Anmeldefehlern vor dem Zurücksetzen der PIN für einen Outlook Voice Access-Benutzer zulässig ist. Die möglichen Werte liegen in einem Bereich von 1 bis 998, der Standardwert ist 5. Die maximal zulässige Anzahl von fehlerhaften Anmeldeversuchen vor dem Zurücksetzen eines Postfachs wird in einer UM-Postfachrichtlinie konfiguriert und gilt für alle Outlook Voice Access-Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.


> [!NOTE]
> Sie erhöhen die Sicherheit, indem Sie die Einstellung <STRONG>Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN</STRONG> mit einem kleineren Wert als 5 konfigurieren. Sie verringern die Sicherheit, wenn Sie diese Einstellung mit einem größeren Wert als 5 konfigurieren.



Informationen zu weiteren Aufgaben im Zusammenhang mit der Sicherheit der Outlook Voice Access-PIN finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Anzahl von Anmeldefehlern, bevor eine PIN zurückgesetzt wird, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **PIN-Richtlinien** und dann auf **Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN:** , und geben Sie einen Wert zwischen 0 und 999 ein.

5.  Klicken Sie auf **Speichern**.

## Konfigurieren der Anzahl von Anmeldefehlern, bevor eine PIN zurückgesetzt wird, mithilfe der Shell

In diesem Beispiel wird für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, die Anzahl von zulässigen Anmeldefehlern vor dem Zurücksetzen der PIN auf 3 festgelegt.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3

In diesem Beispiel wird die Anzahl von Anmeldefehlern vor dem Zurücksetzen der PIN des Benutzers auf 3 festgelegt. Die maximale Anzahl von Anmeldeversuchen wird auf 5 begrenzt, und die minimale PIN-Länge für UM-aktivierte Benutzer, die einer UM-Postfachrichtlinie mit der Bezeichnung `MyUMMailboxPolicy` zugewiesen sind, beträgt 9 Zeichen.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3 -MaxLogonAttempts 5 -MinPINLength 9

