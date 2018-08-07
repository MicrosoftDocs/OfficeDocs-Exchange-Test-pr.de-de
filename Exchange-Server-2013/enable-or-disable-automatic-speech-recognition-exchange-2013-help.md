---
title: 'Aktivieren oder Deaktivieren der autom. Spracherkennung: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren der automatischen Spracherkennung
ms:assetid: 92b3b679-b503-4068-8e88-25ec0f4537ab
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232128(v=EXCHG.150)
ms:contentKeyID: 52062741
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der automatischen Spracherkennung

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-12_

Sie können die automatische Unified Messaging-Telefonzentrale (UM) für die automatische Spracherkennung aktivieren. Durch die Sprachaktivierung einer automatischen UM-Telefonanlage können Benutzer verbal auf die Ansagen der automatischen Telefonzentrale antworten bzw. durch das Menüsystem der automatischen Telefonzentrale navigieren. Eine automatische Telefonzentrale ist bei ihrer Erstellung standardmäßig nicht sprachaktiviert. Nachdem Sie die automatische Telefonzentrale sprachaktiviert haben, können die Anrufer nur Sprachbefehle und keine Tonwahleingaben verwenden, um durch das Menüsystem der automatischen Telefonzentrale zu navigieren.

Diese Vorgehensweise ist zwar nicht erforderlich, es wird jedoch empfohlen, eine automatische DTMF-Fallback-Telefonzentrale (Dual Tone Multi-Frequency) für jede sprachaktivierte automatische Telefonzentrale zu erstellen, damit Anrufer Tonwahleingaben verwenden können, wenn die sprachaktivierte automatische Telefonzentrale die von ihnen gesprochenen Wörter nicht erkennt oder versteht. Wenn eine automatische DTMF-Fallback-Telefonzentrale konfiguriert ist, können Benutzer die DTMF-Eingabe (auch als Tonwahleingabe bezeichnet) verwenden, um durch das Menüsystem der automatischen Telefonzentrale zu navigieren, den Namen eines Benutzers zu buchstabieren oder eine benutzerdefinierte Menüansage zu verwenden. Es wird empfohlen, die Spracherkennung für automatische DTMF-Fallback-Telefonzentralen nicht zu aktivieren.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren der Spracherkennung einer automatischen UM-Telefonzentrale

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie für die Spracherkennung aktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Allgemein** das Kontrollkästchen **Automatische Telefonzentrale zum Beantworten von Sprachbefehlen festlegen**, um die Spracherkennung zu aktivieren. Deaktivieren Sie dieses Kontrollkästchen, um die automatische Spracherkennung zu deaktivieren.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Aktivieren der Spracherkennung einer automatischen UM-Telefonzentrale

In diesem Beispiel wird die automatische Spracherkennung für die automatische UM-Telefonzentrale `MySpeechEnabled AA` aktiviert.

    Set-UMAutoAttendant -Identity MySpeechEnabledAA -SpeechEnabled $true

