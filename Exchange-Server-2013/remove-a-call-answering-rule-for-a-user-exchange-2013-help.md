---
title: 'Entfernen einer Mailboxansageregel für einen Benutzer: Exchange Online Help'
TOCTitle: Entfernen einer Mailboxansageregel für einen Benutzer
ms:assetid: 1da3c5bc-7227-4b37-96f6-67ceefc084d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898497(v=EXCHG.150)
ms:contentKeyID: 51409278
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer Mailboxansageregel für einen Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Mit der Shell können Sie eine oder mehr Mailboxansageregeln für einen Benutzer entfernen. Sie können auch mit dem Cmdlet **Remove-UMCallAnsweringRule** in einem Exchange-Verwaltungsshellskript eine oder mehrere Mailboxansageregeln für mehrere Benutzer entfernen.

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



## Verwenden der Shell zum Entfernen einer Mailboxansageregel

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` vom Postfach eines Benutzers entfernt. Das Postfach des Benutzers ist das Postfach des Benutzers, der das Cmdlet ausführt.

    Remove-UMCallAnsweringRule -Identity MyUMCallAnsweringRule

In diesem Beispiel wird die Mailboxansageregel `MyUMCallAnsweringRule` vom Postfach von "Tony Smith" entfernt.

    Remove-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith

