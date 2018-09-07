---
title: 'Aktiv. ang. Begrüßung außerhalb d. Geschäftszeiten: Exchange 2013-Hilfe'
TOCTitle: Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Begrüßung
ms:assetid: d4743805-bab0-4735-a1e0-2cea4e088e8c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232183(v=EXCHG.150)
ms:contentKeyID: 50554918
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Begrüßung

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-30_

Sie können für eine automatische Unified Messaging-Telefonzentrale (Unified Messaging) eine benutzerdefinierte Begrüßung außerhalb der Geschäftszeit aktivieren. Wenn eine automatische UM-Telefonzentrale außerhalb der Geschäftszeit einen Anruf beantwortet, hört der Anrufer als Erstes die Begrüßung. Sie können die Begrüßung nach Wunsch anpassen.

Unified Messaging bietet eine Standardsystemansage zur Verwendung außerhalb der Geschäftszeit. Sie müssen diese Standardsystemansage zwar weder ersetzen noch ändern, dennoch möchten Sie möglicherweise eine angepasste Begrüßung bereitstellen. Sie können eine benutzerdefinierte Ansage im WAV- oder WMA-Dateiformat erstellen, die verwendet wird, wenn Anrufer außerhalb der Geschäftszeiten bei einer automatischen UM-Telefonzentrale anrufen. Diese kann beispielsweise wie folgt lauten: "Hallo, hier ist die Woodgrove Bank. Leider rufen Sie außerhalb unserer Geschäftszeiten an."

Wenn Sie den Namen der Organisation oder des Unternehmens in die Standardansage aufnehmen möchten, können Sie den Namen in das Feld **Firmenname** der automatischen UM-Telefonzentrale eingeben. Weitere Informationen finden Sie unter [Geben Sie einen Namen für die business](enter-a-business-name-exchange-2013-help.md).

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Erstellen Sie eine WAV- oder WMA-Datei, die für die Begrüßung verwendet werden soll.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren einer angepassten Begrüßung außerhalb der Geschäftszeit mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie die Begrüßung außerhalb der Geschäftszeit festlegen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Begrüßungen** unter **Begrüßung außerhalb der Geschäftszeit** auf **Ändern**, und klicken Sie dann auf **Durchsuchen**, um die benutzerdefinierte Datei mit der Begrüßung außerhalb der Geschäftszeit zu bestimmen, die Sie vor Beginn dieses Schritts erstellt haben.
    

    > [!IMPORTANT]
    > Die Datei, die für die Begrüßung verwendet werden soll, muss eine WAV- oder WMA-Datei sein.



4.  Nachdem Sie die Datei bestimmt haben, klicken Sie auf **Öffnen** und anschließend auf **Speichern**.

## Aktivieren einer angepassten Begrüßung außerhalb der Geschäftszeit mithilfe der Shell

In diesem Beispiel wird die Begrüßung außerhalb der Geschäftszeit aktiviert, bei der eine benutzerdefinierte Begrüßung namens `GreetingFile.wav` für die automatische UM-Telefonzentrale `MyUMAutoAttendant` verwendet wird.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -AfterHoursWelcomeGreetingEnabled $true -AfterHoursWelcomeGreetingFilename GreetingFile.wav

In diesem Beispiel wird eine automatische UM-Telefonzentrale mit dem Namen `MyUMAutoAttendant` konfiguriert, deren Geschäftszeiten auf 10:45 bis 13:15 (Sonntag), 09:00 bis 17:00 (Montag) und 09:00 bis 16:30 (Samstag) festgelegt und Feiertage mit den entsprechenden Begrüßungen "`New Year`" am 02.01.13 und "`Building Closed for Construction`" vom 24. bis zum 28.04.13 konfiguriert sind.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30 -HolidaySchedule "New Year,newyrgrt.wav,1/2/2013","Building Closed for Construction,construction.wav,4/24/2013,4/28/2013"

In diesem Beispiel werden eine automatische UM-Telefonzentrale namens `MyAutoAttendant` und Tastenzuordnungen für die Begrüßung außerhalb der Geschäftszeit so konfiguriert, dass Anrufer beim Drücken der Taste "1" an eine andere automatische UM-Telefonzentrale namens `SalesAutoAttendant` weitergeleitet werden. Wenn Anrufer die Taste "2" drücken, werden sie an die Durchwahlnummer 12345 für den `Support` weitergeleitet. Beim Drücken der Taste "3" werden sie an eine andere automatische Telefonzentrale weitergeleitet, die eine Audiodatei wiedergibt.

    Set-UMAutoAttendant -Identity MyAutoAttendant - BusinessHoursKeyMappingEnabled $true -BusinessHoursKeyMapping "1,Sales,,SalesAutoAttendant","2,Support,12345","3,Directions,,,directions.wav"

