---
title: 'Konfig. von Voicemail aus authentifizierter Anrufer: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von Voicemail aus authentifizierter Anrufer
ms:assetid: f69e94a7-9768-4445-9ded-e78d732bd623
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423560(v=EXCHG.150)
ms:contentKeyID: 52062796
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Voicemail aus authentifizierter Anrufer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können Unified Messaging dazu konfigurieren, eingehende Anrufe entgegenzunehmen, und dann festlegen, ob Voicemailnachrichten durch Verschlüsselung geschützt werden sollen. Wenn eine Sprachnachricht geschützt ist, gilt Folgendes:

  - Die Nachricht wird in Microsoft Outlook und Outlook Web App als "Privat" gekennzeichnet.

  - Die Sprachnachricht kann nur durch den vorgesehenen Empfänger geöffnet werden.

  - Der Empfänger kann auf die Sprachnachricht antworten, sie jedoch nicht an einen Empfänger weiterleiten, der nicht in der ursprünglichen Sprachnachricht enthalten war.

Diese Einstellung gilt für Sprachnachrichten, die an UM-aktivierte Benutzer gesendet werden, wenn diese ein Gespräch nicht entgegennehmen. Diese Einstellung gilt auch, wenn Anrufer sich über Outlook Voice Access bei ihrem Postfach anmelden und anschließend eine Sprachnachricht erstellen und senden.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Verfahren für geschützte Voicemail finden Sie unter [Geschützte Voicemail-Prozeduren](https://technet.microsoft.com/de-de/library/JJ938013(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von geschützten Voicemails von authentifizierten Anrufern mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **UM-Postfachrichtlinie** \> **Geschützte Voicemail** unter **Sprachnachricht von authentifizierten Anrufern schützen** eine der folgenden Optionen:
    
      - **Keine**   Verwenden Sie diese Einstellung, wenn an UM-aktivierte Benutzer gesendete Sprachnachrichten nicht geschützt werden sollen.
    
      - **Privat**   Verwenden Sie diese Einstellung, wenn nur Sprachnachrichten von Unified Messaging geschützt werden sollen, die vom Anrufer als privat gekennzeichnet wurden.
    
      - **Alle**   Verwenden Sie diese Einstellung, wenn alle Sprachnachrichten einschließlich der nicht als privat gekennzeichneten Nachrichten von Unified Messaging geschützt werden sollen.

4.  Klicken Sie auf **Speichern**.

## Konfigurieren von geschützten Voicemails von authentifizierten Anrufern mithilfe der Shell

In diesem Beispiel werden Sprachnachrichten von allen authentifizierten Anrufern für die UM-Postfachrichtlinie `MyUMMailboxPolicy` geschützt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy ProtectAuthenticatedVoiceMail -All

