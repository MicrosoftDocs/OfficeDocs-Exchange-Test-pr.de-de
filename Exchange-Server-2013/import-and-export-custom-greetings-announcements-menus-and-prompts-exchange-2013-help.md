---
title: 'Importieren und Exportieren ang. Begrüß., Infoansagen, Menüs und Menüansagen'
TOCTitle: Importieren und Exportieren angepasster Begrüßungen, Informationsansagen, Menüs und Menüansagen
ms:assetid: e82da5d5-625f-4d8b-8d31-ac45513aacfd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee681667(v=EXCHG.150)
ms:contentKeyID: 54652711
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Importieren und Exportieren angepasster Begrüßungen, Informationsansagen, Menüs und Menüansagen

 

_**Gilt für:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Audiodateien, die Sie aufgezeichnet haben, importieren und exportieren, um sie für UM-Wählpläne und automatische Telefonzentralen zu verwenden. Sie möchten beispielsweise vielleicht eine Kopie einer Audiodatei exportieren und speichern, wenn Sie ein Upgrade von einer früheren Version von Exchange durchführen. Es kann auch sein, dass Sie eine Kopie einer aufgezeichneten Telefonansage importieren müssen, bevor Sie einen Wählplan oder eine automatische Telefonzentrale konfigurieren.

Die Audiodateien werden zu folgenden Zwecken verwendet:

  - In UM-Wählplänen werden Audiodateien für angepasste Begrüßungen und Informationsansagen verwendet. Sie werden wiedergegeben, wenn sich Outlook Voice Access-Benutzer über eine Outlook Voice Access-Nummer einwählen.

  - In automatischen UM-Telefonzentralen werden Audiodateien für angepasste Begrüßungen, Informationsansagen, Menüansagen und Navigationsmenüs während und außerhalb der Geschäftszeiten verwendet. Sie werden wiedergegeben, wenn Anrufer bei einer automatischen UM-Telefonzentrale anrufen.

Die folgenden Audiodateiformate werden für angepasste Begrüßungen, Informationsansagen, Menüs und Menüansagen unterstützt:

  - Mit Windows Media Audio 9.2 (96 KBit/s, 44 kHz, Stereo 1-Pass CBR - Windows Sound Recorder) und

  - Windows Media Audio Voice 9 (8 KBit/s, 8 kHz, Mono) codierte WMA-Dateien und WAV-Dateien, die mit dem Audiocodec für Linear PCM (16 Bits/Sample; 8 kHz) codiert wurden.

Sie importieren die Audiodateien, die von UM-Wählplänen und automatischen Telefonzentralen verwendet werden, in das Systempostfach mit dem Namen {e0dc1c29-89c3-4034-b678-e6c29d823ed9} und exportieren die Audiodateien von diesem Systempostfach. Die Audiodateien können mithilfe der Cmdlets **Import-UMPrompt** und **Export-UMPrompt** importiert und exportiert werden.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wählpläne" und "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Importieren von benutzerdefinierten Begrüßungen, Informationsansagen, Menüs und Menüansagen für UM-Wählpläne und automatische Telefonzentralen mithilfe der Shell

In diesem Beispiel wird die Begrüßungsdatei "welcomegreeting.wav" aus "D:\\UMPrompts" in den UM-Wählplan `MyUMDialPlan` importiert.

    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMDialPlan MyUMDialPlan -PromptFileName "welcomegreeting.wav" -PromptFileData $c

In diesem Beispiel wird die Begrüßungsdatei "welcomegreeting.wav" aus "D:\\UMPrompts" in die automatische UM-Telefonzentrale `MyUMAutoAttendant` importiert.

    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMAutoAttendant MyUMAutoAttendant -PromptFileName "welcomegreeting.wav" -PromptFileData $c

## Exportieren von benutzerdefinierten Begrüßungen, Informationsansagen, Menüs und Menüansagen aus UM-Wählplänen und automatischen Telefonzentralen mithilfe der Shell

In diesem Beispiel wird die Begrüßung für den UM-Wählplan `MyUMDialPlan` exportiert, und die Datei wird unter dem Namen "welcomegreeting.wav" gespeichert.

    $prompt = Export-UMPrompt -PromptFileName "customgreeting.wav�? -UMDialPlan MyUMDialPlan
    set-content -Path "d:\DialPlanPrompts\welcomegreeting.wav" -Value $prompt.AudioData -Encoding Byte

In diesem Beispiel wird die Begrüßung während der Geschäftszeit exportiert, die für die automatische UM-Telefonzentrale `MYUMAutoAttendant` verwendet wird, und die Datei wird unter dem Namen "BusinessHoursWelcomeGreeting.wav" gespeichert.

    $prompt = Export-UMPrompt -BusinessHoursWelcomeGreeting -UMAutoAttendant MyUMAutoAttendant
    set-content -Path "d:\UMPrompts\BusinessHoursWelcomeGreeting.wav" -Value $prompt.AudioData -Encoding Byte

