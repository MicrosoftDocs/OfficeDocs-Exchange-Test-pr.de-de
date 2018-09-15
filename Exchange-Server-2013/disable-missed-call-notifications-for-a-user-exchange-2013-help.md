---
title: 'Deaktiv. von Benachricht. über verp. Anrufe für Benutzer: Exchange 2013-Hilfe'
TOCTitle: Deaktivieren von Benachrichtigungen über verpasste Anrufe für einen Benutzer
ms:assetid: e54937d5-3074-454f-b561-e601fecfc6ad
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673570(v=EXCHG.150)
ms:contentKeyID: 52062785
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren von Benachrichtigungen über verpasste Anrufe für einen Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-09_

Sie können über die Shell oder Exchange-Verwaltungskonsole Benachrichtigungen über verpasste Anrufe für eine Unified Messaging-Postfachrichtlinie (UM) aktivieren oder deaktivieren. Bei einer Benachrichtigung über verpasste Anrufe handelt es sich um eine E-Mail, die an einen Benutzer gesendet wird, wenn der Benutzer einen eingehenden Anruf nicht annimmt und der Anrufer keine Sprachnachricht hinterlässt. Dies ist jedoch nicht die E-Mail-Nachricht, die die für einen Benutzer hinterlassene Sprachnachricht enthält.

Wenn Sie Benachrichtigungen über verpasste Anrufe für eine UM-Postfachrichtlinie deaktivieren, erhalten sämtliche der einer UM-Postfachrichtlinie zugeordneten Benutzer keine E-Mail-Nachricht, wenn Sie einen eingehenden Anruf nicht beantworten und der Anrufer keine Sprachnachricht hinterlässt. Standardmäßig sind Benachrichtigungen über verpasste Anrufe für alle UM-Postfachrichtlinien aktiviert, die erstellt werden. Wenn Sie einen UM-Wählplan erstellen, wird zudem standardmäßig eine UM-Postfachrichtlinie erstellt.


> [!NOTE]
> Wenn Sie Unified Messaging und Microsoft Lync Server integrieren, stehen Benachrichtigungen über verpasste Anrufe Benutzern nicht zur Verfügung, die über ein Postfach auf einem Exchange&nbsp;2007- oder Exchange&nbsp;2010-Postfachserver verfügen, wenn ein Benutzer sich abmeldet, bevor der Anruf an einen Postfachserver gesendet wurde, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [Verwalten einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Aa998829(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von Benachrichtigungen über verpasste Anrufe für eine UM-Telefonrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie auf der Seite **UM-Postfachrichtlinie** \> **Allgemein** das Kontrollkästchen neben **Benachrichtigungen über verpasste Anrufe zulassen**.

4.  Klicken Sie auf **Speichern**.

## Deaktivieren von Benachrichtigungen über verpasste Anrufe für eine UM-Telefonrichtlinie mithilfe der Shell

In diesem Beispiel werden Benachrichtigungen über verpasste Anrufe für eine UM-Postfachrichtlinie mit dem Namen `MyUMMailboxPolicy` deaktiviert.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowMissedCallNotifications $false

