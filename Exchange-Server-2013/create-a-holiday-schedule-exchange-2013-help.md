---
title: 'Erstellen eines Feiertagszeitplans: Exchange Online Help'
TOCTitle: Erstellen eines Feiertagszeitplans
ms:assetid: 0c5c51e4-5b51-451b-ab93-2cebf644dc96
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266921(v=EXCHG.150)
ms:contentKeyID: 50475063
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen eines Feiertagszeitplans

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-19_

Sie können die Datums- und Zeitangaben definieren, zu denen Ihre Organisation an Feiertagen oder zu anderen Gelegenheiten geschlossen ist. Innerhalb der von Ihnen festgelegten Start- und Enddatumsangaben erreichen Anrufer die automatische Unified Messaging (UM)-Telefonzentrale und hören die entsprechende Feiertagsansage, die Sie beim Konfigurieren des Feiertagszeitplans angeben. Nach der von Ihnen angegebenen Feiertagsansage werden die Begrüßungen und Menüansagen außerhalb der Geschäftszeiten zur Information für den Anrufer wiedergegeben.

Sie können auch einen Feiertagszeitplan innerhalb eines vorhandenen Feiertagszeitplans erstellen. Wenn Sie mehrere Feiertagszeitpläne erstellen, erlaubt Unified Messaging die Überschneidung von geplanten Feiertagszeiten. Sie können z. B. einen Feiertagszeitplan vom 15. bis zum 31. Dezember erstellen, weil Ihre Organisation wegen Bauarbeiten geschlossen ist, und Sie können einen weiteren Feiertagszeitplan vom 24. bis zum 26. Dezember definieren. Wenn Anrufer zwischen dem 15. und 23. Dezember und zwischen dem 27. und 31. Dezember die automatische Telefonzentrale anrufen, hören Sie die Feiertagsbegrüßung, die Sie für diesen Zeitraum angegeben haben. Beispiel: "Das Unternehmen ist zurzeit aufgrund von Baumaßnahmen geschlossen." Wenn Anrufer zwischen dem 24. und 26. Dezember anrufen, hören Sie eine andere Feiertagsbegrüßung, z. B. "Wir haben zurzeit aufgrund der Weihnachtsfeiertage geschlossen."

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Angeben eines Feiertagszeitplans für eine automatische UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie den Feiertagszeitplan festlegen möchten. Klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Geschäftszeiten** unter **Feiertagszeitplan** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Konfigurieren Sie auf der Seite **Neuer Feiertag** Folgendes:
    
      - **Name**   Geben Sie einen Namen für den Feiertagszeitplan ein.
    
      - **Ansage für Feiertage**   Navigieren Sie zur WAV-Datei, die als Begrüßung verwendet werden soll. Dieses Feld ist erforderlich.
    
      - **Startdatum**   Verwenden Sie diese Liste, um das Datum auszuwählen, an dem die Feiertage beginnen sollen. Der Feiertagszeitplan wird zu dem in der Liste angegebenen Datum um Mitternacht wirksam.
    
      - **Enddatum**   Verwenden Sie diese Liste, um das Datum auszuwählen, an dem die Feiertage enden sollen. Der Feiertagszeitplan endet an dem in dieser Liste angegebenen Datum um 23:59 Uhr.

5.  Nachdem Sie den Feiertagszeitplan konfiguriert haben, klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Shell zum Angeben eines Feiertagszeitplans für eine automatische UM-Telefonzentrale

In diesem Beispiel wird eine automatische UM-Telefonzentrale mit dem Namen `MyUMAutoAttendant` konfiguriert, deren Geschäftszeiten auf 10:45 bis 13:15 Uhr (Sonntag), 09:00 bis 17:00 Uhr (Montag) und 09:00 bis 16:30 Uhr (Samstag) festgelegt und Feiertage mit den entsprechenden Begrüßungen "New Year" am 2. Januar 2013 und "Building Closed for Construction" vom 24. bis zum 28. April 2013 konfiguriert sind.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30 -HolidaySchedule "New Year,newyrgrt.wav,1/2/2013","Building Closed for Construction,construction.wav,4/24/2013,4/28/2013"

