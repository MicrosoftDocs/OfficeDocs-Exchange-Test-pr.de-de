---
title: 'Erstellen einer Mailboxansageregel: Exchange Online Help'
TOCTitle: Erstellen einer Mailboxansageregel
ms:assetid: 0976f8f2-3449-44f1-b0d1-20c91622e827
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898495(v=EXCHG.150)
ms:contentKeyID: 51409264
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Mailboxansageregel

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Mit der Shellkönnen Sie eine oder mehr Mailboxansageregeln für einen Benutzer erstellen. Sie können auch mit dem Cmdlet **New-UMCallAnsweringRule** in einem Exchange-Verwaltungsshellskript Mailboxansageregeln für mehrere Benutzer erstellen.

Mailboxansageregeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails. Wenn ein Benutzer für Unified Messaging (UM) aktiviert ist, werden standardmäßig keine Mailboxansageregeln konfiguriert. Dennoch werden eingehende Anrufe vom Voicemailsystem beantwortet, und Anrufer werden aufgefordert, eine Sprachnachricht zu hinterlassen.


> [!NOTE]
> Für Unified Messaging (UM) aktivierte Benutzer können sich bei Outlook Web App anmelden, um Mailboxansageregeln zu erstellen, zu verwalten und zu entfernen.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Mailboxansageregeln finden Sie unter [Weiterleiten von Anrufen Prozeduren](forwarding-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Mailboxansageregeln" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Genaue Anweisungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Die Shell kann nur für diesen Vorgang verwendet werden. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)). Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Erstellen einer Mailboxansageregel

In diesem Beispiel wird die Mailboxansageregel `MyCallAnsweringRule` im Postfach für "Tony Smith" mit einer Priorität von 2 erstellt.

    New-UMCallAnsweringRule -Name MyCallAnsweringRule -Priority 2 -Mailbox tonysmith

In diesem Beispiel wird die Mailboxansageregel `MyCallAnsweringRule` im Postfach für "Tony Smith" erstellt, und folgende Aktionen werden durchgeführt:

  - Die Mailboxansageregel wird auf zwei Anrufer-IDs festgelegt.

  - Die Priorität der Mailboxansageregel wird auf 2 festgelegt.

  - Die Mailboxansageregel wird so festgelegt, dass Anrufer die Ansage unterbrechen können.

<!-- end list -->

    New-UMCallAnsweringRule -Name MyCallAnsweringRule -CallerIds "1,4255550100,,","1,4255550123,," -Priority 2 -CallersCanInterruptGreeting $true -Mailbox tonysmith

In diesem Beispiel wird die Mailboxansageregel `MyCallAnsweringRule` im Postfach für "Tony Smith" erstellt, und folgende Aktionen werden durchgeführt:

  -  Die Priorität der Mailboxansageregel wird auf 2 festgelegt.

  -  Für die Mailboxansageregel werden Tastenzuordnungen erstellt.

  -  Wenn der Anrufer die Voicemail des Benutzers erreicht und der Status des Benutzers auf "Gebucht" gesetzt ist, hat der Anrufer folgende Möglichkeiten:
    
      - Er drückt die Taste 1 und wird an den Empfang mit der Durchwahl 45678 weitergeleitet.
    
      - Er drückt die Taste 2, sodass in dringenden Fällen die Suchfunktion verwendet und zuerst die Durchwahl 23456 und anschließend 45671 angerufen wird.

<!-- end list -->

    New-UMCallAnsweringRule -Name MyCallAnsweringRule -Priority 2 -Mailbox tonysmith -ScheduleStatus 0x4 - -KeyMappings "1,1,Receptionist,,,,,45678,","5,2,Urgent Issues,23456,23,45671,50,,"

