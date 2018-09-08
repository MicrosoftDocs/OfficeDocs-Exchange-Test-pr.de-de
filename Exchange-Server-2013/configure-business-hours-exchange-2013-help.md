---
title: 'Konfigurieren von Geschäftszeiten: Exchange Online Help'
TOCTitle: Konfigurieren von Geschäftszeiten
ms:assetid: 96b4be99-af94-4fa4-959a-48413387a044
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232133(v=EXCHG.150)
ms:contentKeyID: 50476291
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Geschäftszeiten

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-19_

Bei der Konfiguration der Geschäftszeiten für eine automatische Unified Messaging (UM)-Telefonzentrale definieren Sie die Zeit, in der Ihre Organisation täglich zu erreichen ist, sowie die Begrüßung während der Geschäftszeiten und die Menüansagen, die Anrufer hören, wenn sie eine in der automatischen Telefonzentrale konfigurierte Durchwahlnummer anwählen. Wenn ein Anrufer die automatische Telefonzentrale während der Stunden erreicht, die außerhalb der von Ihnen definierten Geschäftszeiten liegen, hört der Anrufer die Ansagen und Begrüßungen, die außerhalb der Geschäftszeiten wiedergegeben werden.

In der Exchange-Verwaltungskonsole stehen einige Zeitplanoptionen zur Verfügung. Die Geschäftszeiten der meisten Unternehmen sind Montag bis Freitag zwischen 8:00 Uhr und 17:00 Uhr. In einigen Fällen entsprechen die Standardoptionen vielleicht nicht Ihren Anforderungen und Sie müssen den Zeitplan anpassen. Wenn Ihre Geschäftszeiten von den vom System definierten Zeitplänen abweichen, können Sie einen angepassten Zeitplan für die automatische Telefonzentrale definieren.

Standardmäßig gibt die automatische UM-Telefonzentrale zu jeder Tageszeit bei einem Anruf die Ansagen und Begrüßungen für die Geschäftszeiten wieder.


> [!NOTE]
> Wenn Sie den Zeitplan für die Zeiten während und außerhalb der Geschäftszeiten für eine automatische UM-Telefonzentrale festlegen, vergewissern Sie sich, dass die Zeitzone ordnungsgemäß konfiguriert ist.



Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Festlegen der Geschäftszeiten für eine automatische UM-Telefonzentrale

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie die Geschäftszeiten festlegen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Geschäftszeiten** unter **Geschäftszeiten** auf **Geschäftszeiten konfigurieren**.

4.  Wählen Sie auf der Seite **Geschäftszeiten konfigurieren** die Stunden aus, die für die einzelnen Wochentage als Geschäftszeiten gelten sollen.

5.  Klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Shell zum Festlegen der Geschäftszeiten für eine automatische UM-Telefonzentrale

In diesem Beispiel werden die Geschäftszeiten für eine automatische UM-Telefonzentrale mit dem Namen `MyUMAutoAttendant` festgelegt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30

