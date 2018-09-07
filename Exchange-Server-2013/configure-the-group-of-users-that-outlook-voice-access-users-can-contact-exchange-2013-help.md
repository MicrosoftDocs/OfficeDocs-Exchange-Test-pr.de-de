---
title: 'Konfig. d. Gruppe, die Outlook Voice Access-Benutzer kontaktieren können'
TOCTitle: Konfigurieren Sie die Gruppe von Benutzern, die Outlook Voice Access-Benutzer wenden können
ms:assetid: a8dc0f9e-dc86-4128-af63-d4e550aed5bb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423551(v=EXCHG.150)
ms:contentKeyID: 50476406
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die Gruppe von Benutzern, die Outlook Voice Access-Benutzer wenden können

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-09_

Sie können angeben, welche Benutzer weitergeleitete Anrufe oder Voicemailnachrichten von Outlook Voice Access-Benutzern empfangen können. Standardmäßig ist die Option **Nur in diesem Wählplan** aktiviert. Sie können diese Einstellung ändern, um Outlook Voice Access-Benutzern die Weiterleitung von Anrufen oder das Senden von Sprachnachrichten an Benutzer, die sich in der gesamten Organisation befinden, an eine automatische UM-Telefonzentrale oder an eine bestimmte Durchwahlnummer zu ermöglichen.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Mit der Exchange-Verwaltungskonsole die Gruppe der Benutzer konfigurieren, mit denen Voice Access-Benutzer verbunden werden können

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Wählen Sie in **Weiterleitung und Suche** unter **Anrufer dürfen Benutzer nach Name oder Alias suchen** eine der folgenden Optionen aus:
    
      - **Nur in diesem Wählplan**   Mithilfe dieser Option können Sie Outlook Voice Access-Benutzern, die sich über eine Outlook Voice Access-Nummer einwählen, die Suche nach und die Kontaktaufnahme mit Benutzern gestatten, die sich im gleichen Wählplan befinden.
    
      - **In der gesamten Organisation**   Mithilfe dieser Option können Sie Outlook Voice Access-Benutzern, die sich über eine Outlook Voice Access-Nummer einwählen, die Suche nach und die Kontaktaufnahme mit jeder Person in der gesamten Organisation gestatten. Hierzu gehören alle postfachaktivierten Benutzer.
    
      - **Nur in dieser automatischen Telefonzentrale**   Mithilfe dieser Option können Sie Outlook Voice Access-Benutzern, die sich über eine Outlook Voice Access-Nummer einwählen, gestatten, eine Verbindung mit einer bestimmten automatischen Telefonzentrale herzustellen. Sie müssen die automatische Telefonzentrale erst erstellen, bevor Sie sie an dieser Stelle angeben können. Auf diese Weise können Outlook Voice Access-Benutzer an eine andere automatische Telefonzentrale weitergeleitet werden. Die von Ihnen hier ausgewählte automatische Telefonzentrale kann sprachaktiviert oder nicht sprachaktiviert sein.
    
      - **Nur für diese Durchwahl**   Verwenden Sie diese Option, um es Outlook Voice Access-Benutzern zu ermöglichen, eine Verbindung mit einer von Ihnen angegebenen Durchwahl herzustellen. Für die Durchwahl dürfen nur Ziffern verwendet werden. Die Anzahl der in diesem Feld definierten Ziffern muss der Anzahl von Ziffern in den Durchwahlnummern entsprechen, die in den UM-Wähleinstellungen konfiguriert sind.

5.  Klicken Sie auf **Speichern**.

## Mit der Shell die Gruppe der Benutzer konfigurieren, mit denen Voice Access-Benutzer verbunden werden können

In diesem Beispiel wird die Gruppe der Benutzer, mit denen Outlook Voice Access-Benutzer verbunden werden können, in einem UM-Wählplan namens `MyUMDialPlan` auf die gesamte Organisation festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -ContactScope 'GlobalAddressList' -UMAutoAttendant $null -AllowDialPlanSubscribers $false -AllowExtensions $false

In diesem Beispiel wird die Gruppe der Benutzer, mit denen Outlook Voice Access-Benutzer verbunden werden können, in einem UM-Wählplan namens `MyUMDialPlan` auf den `DialPlan` festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -ContactScope DialPlan -AllowDialPlanSubscribers $false -AllowExtensions $false

