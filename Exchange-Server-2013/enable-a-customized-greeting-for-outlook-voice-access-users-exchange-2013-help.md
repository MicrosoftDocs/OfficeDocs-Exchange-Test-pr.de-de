---
title: 'Aktivieren einer benutzerdefinierten Begrüßung für Outlook Voice Access-Benutzer: Exchange 2013 Help'
TOCTitle: Aktivieren einer benutzerdefinierten Begrüßung für Outlook Voice Access-Benutzer
ms:assetid: abd418ec-2c65-4720-859d-c11a2698dc06
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124125(v=EXCHG.150)
ms:contentKeyID: 50554891
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren einer benutzerdefinierten Begrüßung für Outlook Voice Access-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Standardmäßig gehört zu jedem UM-Wählplan (Unified Messaging) eine WAV-Standarddatei mit der Begrüßung, die Anrufern wiedergegeben wird, einschließlich Outlook Voice Access-Benutzern, die eine konfigurierte Outlook Voice Access-Nummer anrufen. Sie können jedoch für die Begrüßung eine WAV- oder WMA-Datei erstellen und diese für den UM-Wählplan aktivieren.

Sie können beispielsweise diese Standardbegrüßung ändern und stattdessen eine firmenspezifische Ansage verwenden wie "Willkommen bei Outlook Voice Access der Woodgrove Bank." Hierzu zeichnen Sie die angepasste Begrüßung auf und speichern sie als WAV- oder WMA-Datei. Anschließend konfigurieren Sie den Wählplan so, dass die angepassten Begrüßung verwendet wird.

Weitere Informationen zu den Menüoptionen, die für Benutzer von Outlook Voice Access verfügbar sind, finden Sie in der Schnellreferenz zu Outlook Voice Access, die im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=272767) abgerufen werden kann.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren einer angepassten Begrüßung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Klicken Sie in **Outlook Voice Access** unter **Begrüßung** auf **Ändern** und anschließend auf **Durchsuchen**, um zur Begrüßungsdatei zu navigieren.
    

    > [!IMPORTANT]
    > Die Datei, die für die Begrüßung verwendet werden soll, muss eine WAV- oder WMA-Datei sein.



5.  Nachdem Sie die Datei bestimmt haben, klicken Sie auf **Öffnen** und anschließend auf **Speichern**.

## Aktivieren einer angepassten Begrüßung mithilfe der Shell

In diesem Beispiel wird eine Begrüßung aktiviert, bei der die Datei "C:\\UMPrompts\\welcome.wav" für die Wähleinstellungen `MyUMDialPlan` verwendet wird.

    Set-UMDialPlan -Identity MyUMDialPlan -WelcomeGreetingEnabled $true -WelcomeGreetingFilename c:\UMPrompts\welcome.wav

