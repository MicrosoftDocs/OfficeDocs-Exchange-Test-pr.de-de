---
title: 'Konfigurieren der Zeitzone: Exchange 2013 Help'
TOCTitle: Konfigurieren der Zeitzone
ms:assetid: 30d769e1-3657-4622-bc9a-643c63cf46d9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997162(v=EXCHG.150)
ms:contentKeyID: 50554785
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Zeitzone

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-17_

Standardmäßig verwendet die automatische Unified Messaging-Telefonzentrale (UM) die Zeitzone des Postfachservers, auf dem sie erstellt wurde. Es gibt jedoch Situationen, in denen die Zeitzone für die automatische UM-Telefonzentrale in eine andere Zeitzone geändert werden muss. Wenn Sie beispielsweise über zwei UM-Wählpläne verfügen und jeder Wählplan für eine andere Zeitzone steht, müssen Sie eine automatische UM-Telefonzentrale so konfigurieren, dass sie die gleiche Zeitzone wie der Postfachserver aufweist. Die andere automatische UM-Telefonzentrale muss eine vom Postfachserver abweichende Zeitzone haben.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Zeitzone mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, für die Sie die Zeitzone festlegen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Geschäftszeiten**, und wählen Sie dann unter **Zeitzone** die Zeitzone aus der Dropdownliste aus.

4.  Klicken Sie zum Speichern Ihrer Änderungen auf **OK** und dann auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der Zeitzone

In diesem Beispiel wird die Zeitzone für eine automatische UM-Telefonzentrale `MyUMAutoAttendant` auf "Pazifik" festgelegt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -TimeZoneName Pacific

