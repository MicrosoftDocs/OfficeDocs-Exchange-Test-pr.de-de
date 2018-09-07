---
title: 'Legen Sie die PIN-Mindestlänge für Voicemail: Exchange Online Help'
TOCTitle: Legen Sie die PIN-Mindestlänge für Voicemail
ms:assetid: b2ecab54-42e6-45af-8322-615cc1f68dd9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124271(v=EXCHG.150)
ms:contentKeyID: 50554903
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die PIN-Mindestlänge für Voicemail

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können die minimale PIN-Länge für Ihre Outlook Voice Access-Benutzer konfigurieren, die für Unified Messaging (UM) aktiviert sind. Die PIN-Einstellungen, die Sie für eine UM-Postfachrichtlinie konfigurieren, gelten für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.

Mithilfe von Outlook Voice Access können UM-aktivierte Benutzer auf die Voicemail-, E-Mail-, Kalender- und persönlichen Kontaktinformationen in ihrem Postfach zugreifen. Bevor sie auf ihr Postfach zugreifen können, müssen sie jedoch eine PIN eingeben, damit sie vom Voicemailsystem authentifiziert werden können.


> [!NOTE]
> Wenn Sie die minimale PIN-Länge ändern, werden vorhandene Outlook Voice Access-Benutzer aufgefordert, eine neue PIN mit der neuen Mindestanzahl von Stellen einzugeben, bevor sie fortfahren können. Der Standardwert ist 6.



Informationen zu weiteren Aufgaben im Zusammenhang mit der Outlook Voice Access-PIN-Sicherheit finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der minimalen PIN-Länge für Outlook Voice Access mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **PIN-Richtlinien**, und geben Sie neben **PIN-Mindestlänge** einen Wert von 4 bis 24 ein.

5.  Klicken Sie auf **Speichern**.

## Konfigurieren der minimalen PIN-Länge für Outlook Voice Access mithilfe der Shell

In diesem Beispiel wird die minimale PIN-Länge für Outlook Voice Access-aktivierte Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, auf 8 Stellen festgelegt.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -MinPINLength 8

In diesem Beispiel wird die minimale PIN-Länge auf 8 Stellen sowie die Anzahl von fehlgeschlagenen Anmeldeversuchen festgelegt, bevor die PIN des Benutzers auf 3 zurückgesetzt wird. Diese Einstellungen gelten für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3 -MinPINLength 8

