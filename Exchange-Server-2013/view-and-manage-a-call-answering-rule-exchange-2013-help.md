---
title: 'Anzeigen und Verwalten einer Mailboxansageregel: Exchange Online Help'
TOCTitle: Anzeigen und Verwalten einer Mailboxansageregel
ms:assetid: de6d9fa1-7878-49a9-bddb-e3317d94f4d8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn140251(v=EXCHG.150)
ms:contentKeyID: 54651515
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen und Verwalten einer Mailboxansageregel

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Shell verwenden, um eine oder mehrere Mailboxansageregeln für einen Benutzer anzuzeigen oder zu konfigurieren. Sie können auch die Cmdlets **Get-UMCallAnsweringRule** oder **Set-UMCallAnsweringRule** in einem Exchange-Verwaltungsshellskript verwenden, um Mailboxansageregeln für mehrere Benutzer anzuzeigen oder zu verwalten.

Mailboxansageregeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails. Wenn ein Benutzer für Unified Messaging (UM) aktiviert ist, werden standardmäßig keine Mailboxansageregeln konfiguriert. Eingehende Anrufe werden vom Mailsystem beantwortet, und Anrufer werden aufgefordert, eine Sprachnachricht zu hinterlassen.


> [!IMPORTANT]
> Benutzer, die UM-aktiviert sind, können sich bei Outlook Web App anmelden, um Mailboxansageregeln zu erstellen, zu verwalten und zu entfernen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Mailboxansageregeln finden Sie unter [Weiterleiten von Anrufen Prozeduren](forwarding-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Mailboxansageregeln" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Die Shell kann nur für diesen Vorgang verwendet werden. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)). Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen einer Mailboxansageregel mithilfe der Shell

Sie können die Eigenschaften für eine einzelne Mailboxansageregel oder für eine Liste von Mailboxansageregeln in einem UM-aktivierten Benutzerpostfach abrufen.

In diesem Beispiel wird eine formatierte Liste aller Mailboxansageregeln im UM-aktivierten Postfach eines Benutzers zurückgegeben.

    Get-UMCallAnsweringRule-Mailbox tonysmith | Format-List

Dieses Beispiel zeigt die Eigenschaften der Mailboxansageregel `MyUMCallAnsweringRule` an.

    Get-UMCallAnsweringRule -Identity MyUMCallAnsweringRule

## Konfigurieren einer Mailboxansageregel mithilfe der Shell

Sie können eine Mailboxansageregel konfigurieren oder ändern, die im Postfach eines Benutzers gespeichert ist. Sie können folgende Bedingungen festlegen:

  - Von wem der eingehende Anruf stammt

  - Tageszeit

  - Frei/Gebucht-Kalenderstatus

  - Ob automatische Antworten für E-Mail aktiviert sind

Sie können außerdem folgende Aktionen angeben:

  - Mich anrufen

  - Anrufer an eine andere Person übergeben

  - Eine Sprachnachricht hinterlassen

In diesem Beispiel wird in der Mailboxansageregel `MyCallAnsweringRule`, die im Postfach für Tony Smith vorliegt, die Priorität auf 2 gesetzt.

    Set-UMCallAnsweringRule -Mailbox tonysmith -Name MyCallAnsweringRule -Priority 2

In diesem Beispiel werden die folgenden Aktionen in der Mailboxansageregel `MyCallAnsweringRule` im Postfach für Tony Smith durchgeführt:

  - Die Mailboxansageregel wird auf zwei Anrufer-IDs festgelegt.

  - Die Priorität der Mailboxansageregel wird auf 2 festgelegt.

  - Die Mailboxansageregel wird so festgelegt, dass Anrufer die Ansage unterbrechen können.

<!-- end list -->

    Set-UMCallAnsweringRule -Name MyCallAnsweringRule -CallerIds "1,4255550100,,","1,4255550123,," -Priority 2 -CallersCanInterruptGreeting $true -Mailbox tonysmith

In diesem Beispiel wird in der Mailboxansageregel `MyCallAnsweringRule` im Postfach für Tony Smith der Frei-/Gebucht-Status auf "Abwesend" geändert und eine Priorität von 2 festlegt.

    Set-UMCallAnsweringRule -Name MyCallAnsweringRule -Priority 2 -Mailbox tonysmith@contoso.com -ScheduleStatus 0x8

