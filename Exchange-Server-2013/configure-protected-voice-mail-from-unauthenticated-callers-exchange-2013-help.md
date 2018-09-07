---
title: 'Konfigurieren geschützter Voicemail von nicht authentifizierten Anrufern'
TOCTitle: Konfigurieren geschützter Voicemail von nicht authentifizierten Anrufern
ms:assetid: 106bfa0a-a0fa-4a1b-bd59-4b6df1d0d61d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335098(v=EXCHG.150)
ms:contentKeyID: 52062665
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren geschützter Voicemail von nicht authentifizierten Anrufern

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können Unified Messaging für die Annahme eines eingehenden Anrufs konfigurieren und anschließend festlegen, ob Voicemailnachrichten durch Verschlüsselung geschützt werden. Eine geschützte Voicemailnachricht bedeutet Folgendes:

  - Die Nachricht wird in Microsoft Outlook und in Outlook Web App als Privat gekennzeichnet.

  - Die Sprachnachricht kann nur durch den vorgesehenen Empfänger geöffnet werden.

  - Der Empfänger kann die Sprachnachricht beantworten, er kann sie aber nicht an einen Benutzer weiterleiten, der in der ursprünglichen Sprachnachricht nicht enthalten war.

Diese Einstellung gilt für Sprachnachrichten, die an UM-aktivierte Benutzer gesendet werden, wenn diese ein Gespräch nicht entgegennehmen. Diese Einstellung gilt auch für direkt an UM-aktivierte Benutzer gesendete Sprachnachrichten, wenn der Anrufer eine automatische UM-Telefonzentrale verwendet.

Weitere Verwaltungsaufgaben im Zusammenhang mit Verfahren zum Schutz von Voicemail finden Sie unter [Geschützte Voicemail-Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/protected-voice-mail-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von vor nicht authentifizierten Anrufern geschützter Voicemail mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Postfachrichtlinie** \> **Geschützte Voicemail** unter **Sprachnachrichten vor nicht authentifizierten Anrufern schützen** eine der folgenden Optionen aus:
    
      - **Keine**   Verwenden Sie diese Einstellung, wenn an UM-aktivierte Benutzer gesendete Sprachnachrichten nicht geschützt werden sollen.
    
      - **Privat** Verwenden Sie diese Einstellung, wenn Unified Messaging nur Sprachnachrichten schützen soll, die vom Anrufer als privat gekennzeichnet wurden.
    
      - **Alle** Verwenden Sie diese Einstellung, wenn Unified Messaging alle Sprachnachrichten einschließlich der nicht als privat gekennzeichneten Nachrichten schützen soll.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren geschützter Voicemail von nicht authentifizierten Anrufern

In diesem Beispiel werden alle Sprachnachrichten von allen nicht authentifizierten Anrufern in der UM-Postfachrichtlinie `MyUMMailboxPolicy` geschützt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -ProtectUnauthenticatedVoiceMail -All

