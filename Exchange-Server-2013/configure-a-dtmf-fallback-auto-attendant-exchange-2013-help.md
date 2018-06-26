---
title: 'Konfigurieren Sie eine automatische DTMF-fallback-Telefonzentrale: Exchange Online Help'
TOCTitle: Konfigurieren Sie eine automatische DTMF-fallback-Telefonzentrale
ms:assetid: a82d85f7-de30-40db-8ee6-b091ac14da9d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232158(v=EXCHG.150)
ms:contentKeyID: 50476401
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie eine automatische DTMF-fallback-Telefonzentrale

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-30_

Sie können eine sprachaktivierte automatische UM-Telefonzentrale (Unified Messaging) konfigurieren, die über eine automatische DTMF-Fallback-Telefonzentrale (Dual Tone Multi-Frequency) verfügt. Eine automatische DTMF-Fallback-Telefonzentrale wird verwendet, wenn die sprachaktivierte automatische UM-Telefonzentrale die Spracheingaben des Anrufers nicht verstehen oder erkennen kann. Wenn eine automatische DTMF-Fallback-Telefonzentrale konfiguriert wurde, muss der Anrufer DTMF-Eingaben (auch als Tonwahleingaben bezeichnet) verwenden, um durch das Menüsystem der Telefonzentrale zu navigieren, den Namen eines Benutzers zu buchstabieren oder eine benutzerdefinierte Menüansage zu verwenden. Wenn keine automatische DTMF-Fallback-Telefonzentrale konfiguriert und die maximale Anzahl von Spracheingaben überschritten wurde, da das System den Anrufer nicht verstanden hat, antwortet das System mit folgender Ansage: "Leider kann ich Ihnen nicht helfen. Versuchen Sie es später noch einmal."

Eine automatische Telefonzentrale ist bei ihrer Erstellung standardmäßig nicht sprachaktiviert. Nachdem Sie die automatische Telefonzentrale sprachaktiviert haben, können die Anrufer nur Sprachbefehle und keine Tonwahleingaben verwenden, um durch das Menüsystem der automatischen Telefonzentrale zu navigieren. Obwohl es nicht erforderlich ist, wird empfohlen, dass Sie eine automatische DTMF-Fallback-Telefonzentrale für jede sprachaktivierte automatische Telefonzentrale konfigurieren, damit die Anrufer Tonwahleingaben verwenden können, falls die sprachaktivierte automatische Telefonzentrale die gesagten Worte nicht erkennt oder versteht. Außerdem wird empfohlen, dass Sie eine automatische DTMF-Fallback-Telefonzentrale nicht sprachaktivieren.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren einer sprachaktivierten automatischen Telefonzentrale zur Verwendung einer automatischen DTMF-Fallback-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, für die Sie eine automatische DTMF-Fallback-Telefonzentrale erstellen möchten. Klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Allgemein** das Kontrollkästchen neben **Verwenden Sie diese automatische Telefonzentrale, wenn Sprachbefehle nicht ordnungsgemäß funktionieren**, und klicken Sie anschließend auf **Durchsuchen**.

4.  Wählen Sie auf der Seite **Automatische UM-Telefonzentrale auswählen** die automatische Telefonzentrale aus, die Sie als automatische DTMF-Fallback-Telefonzentrale verwenden möchten, und klicken Sie anschließend auf **Speichern**.


> [!IMPORTANT]
> Zuerst muss die automatische Telefonzentrale sprachaktiviert werden, bevor Sie nach einer von Ihnen eingerichteten automatischen DTMF-Fallback-Telefonzentrale suchen können.



## Konfigurieren einer sprachaktivierten automatischen UM-Telefonzentrale zur Verwendung einer automatischen DTMF-Fallback-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird eine automatische UM-Telefonzentrale namens `MySpeechEnabledAA` zur Verwendung einer automatischen DTMF-Fallback-Telefonzentrale mit Namen `MyDTMFAA` konfiguriert.

    Set-UMAutoAttendant -Identity MySpeechEnabledAA -DTMFFallbackAutoAttendant MyDTMFAA

