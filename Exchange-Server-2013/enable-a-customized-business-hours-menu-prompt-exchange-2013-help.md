---
title: 'Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Menü Aufforderung: Exchange Online Help'
TOCTitle: Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Menü Aufforderung
ms:assetid: 89053e84-3490-4dc6-ade3-9b6c5dbf4020
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232116(v=EXCHG.150)
ms:contentKeyID: 50554854
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Menü Aufforderung

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-19_

Sie können die Menüansage anpassen, die von einer automatischen Unified Messaging-Telefonzentrale (UM) während der Geschäftszeit verwendet werden soll. Nachdem Sie eine automatische UM-Telefonzentrale erstellt haben, wird eine Systemansage ("Willkommen bei Unified Messaging") als Menüansage verwendet, die Anrufer hören, nachdem die Begrüßung mit den Geschäftszeiten wiedergegeben wurde. Auch wenn Systemansagen nicht ersetzt oder geändert werden dürfen, können Sie die Begrüßungen und Menüansagen anpassen, die mit automatischen UM-Telefonzentralen verwendet werden. Nachdem Sie eine angepasste Audiodatei für die Menüansage für die Geschäftszeiten erstellt haben, müssen Sie für die automatische UM-Telefonzentrale Menünavigationseinträge für die Geschäftszeiten aktivieren.

Wenn Sie den Namen der Organisation oder des Unternehmens in die Standardsystemansage aufnehmen möchten, können Sie den Namen in das Feld **Firmenname** der automatischen UM-Telefonzentrale eingeben. Weitere Informationen finden Sie unter [Geben Sie einen Namen für die business](enter-a-business-name-exchange-2013-help.md).


> [!IMPORTANT]
> Sie müssen die Geschäftszeiten in der automatischen Telefonzentrale konfigurieren. Weitere Informationen finden Sie unter <A href="configure-business-hours-exchange-2013-help.md">Konfigurieren von Geschäftszeiten</A>.



Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Erstellen Sie eine WAV- oder WMA-Datei, die für die Menüansage verwendet werden soll.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren einer angepassten Menüansage während der Geschäftszeit mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie die Menüansage während der Geschäftszeit festlegen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Menünavigation** unter **Menünavigation während der Geschäftszeit** auf **Ändern**, und klicken Sie dann auf **Durchsuchen**, um die angepasste Datei mit der Menüansage während der Geschäftszeit zu bestimmen.
    

    > [!IMPORTANT]
    > Die Datei, die für die Menüansage verwendet werden soll, muss eine WAV- oder WMA-Datei sein.



4.  Nachdem Sie die Datei bestimmt haben, klicken Sie auf **Öffnen** und anschließend auf **Speichern**.

## Aktivieren einer angepassten Menüansage während der Geschäftszeit mithilfe der Shell

In diesem Beispiel wird eine Ansage für das Hauptmenü während der Geschäftszeit aktiviert und eine angepasste Ansage namens `businesshoursprompts.wav` für die automatische UM-Telefonzentrale `MyUMAutoAttendant` verwendet.

    Command Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursMainMenuCustomPromptEnabled $true -BusinessHoursMainMenuCustomPromptFilename BusinessHoursPrompts.wav

In diesem Beispiel wird eine automatische UM-Telefonzentrale mit dem Namen `MyUMAutoAttendant` konfiguriert, deren Geschäftszeiten auf 10:45 bis 13:15 (Sonntag), 09:00 bis 17:00 (Montag) und 09:00 bis 16:30 (Samstag) festgelegt und Feiertage mit den entsprechenden Begrüßungen "`New Year`" am 02.01.13 und "`Building Closed for Construction`" vom 24. bis zum 28.04.13 konfiguriert sind.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30 -HolidaySchedule "New Year,newyrgrt.wav,1/2/2013","Building Closed for Construction,construction.wav,4/24/2013,4/28/2013"

In diesem Beispiel werden eine automatische UM-Telefonzentrale namens `MyAutoAttendant` und Navigationsmenüs während der Geschäftszeiten so konfiguriert, dass Anrufer beim Drücken der Taste "1" an eine andere automatische UM-Telefonzentrale namens `SalesAutoAttendant` weitergeleitet werden. Wenn Anrufer die Taste "2" drücken, werden sie an die Durchwahlnummer 12345 für den `Support` weitergeleitet. Beim Drücken der Taste "3" werden sie an eine andere automatische Telefonzentrale weitergeleitet, die eine Audiodatei wiedergibt.

    Set-UMAutoAttendant -Identity MyAutoAttendant - BusinessHoursKeyMappingEnabled $true -BusinessHoursKeyMapping "1,Sales,,SalesAutoAttendant","2,Support,12345","3,Directions,,,directions.wav"

