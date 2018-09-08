---
title: 'Hinzufügen von Text d. gesendeten E-Mail, wenn Sprachnachricht empfangen wird'
TOCTitle: Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn eine VoIP-Nachricht empfangen wird text
ms:assetid: b2eec29c-e5eb-4263-80d8-0b9813dd56dc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201718(v=EXCHG.150)
ms:contentKeyID: 51409329
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn eine VoIP-Nachricht empfangen wird text

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-16_

Sie können zur E-Mail-Nachricht, die beim Empfang einer Voicemailnachricht durch für Unified Messaging (UM) aktivierte Benutzer gesendet wird, zusätzlichen Text hinzufügen. Standardmäßig gibt der E-Mail-Nachrichtentext beim Empfang einer Sprachnachricht nur an, dass der Benutzer eine Sprachnachricht empfangen hat. Sie können jedoch auch eine benutzerdefinierte Nachricht durch Hinzufügen von Text im Textfeld **Wenn ein Benutzer eine Sprachnachricht empfängt** für eine UM-Postfachrichtlinie erstellen. Dieser Text kann z. B. Informationen zu Systemsicherheitsrichtlinien enthalten und das ordnungsgemäße Verfahren für den Umgang mit Sprachnachrichten in Ihrer Organisation beschreiben. Nachdem Sie den Text hinzugefügt haben, wird dieser jeder E-Mail-Nachricht hinzugefügt, die gesendet wird, wenn der UM-Postfachrichtlinie zugeordnete UM-aktivierte Benutzer eine Sprachnachricht empfangen.


> [!NOTE]
> Der benutzerdefinierte Text, der eine Sprachnachricht begleitet, darf maximal 512 Zeichen lang sein und kann einfachen HTML-Text enthalten.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://technet.microsoft.com/de-de/library/JJ851061(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern des E-Mail-Nachrichtentexts beim Empfang einer Sprachnachricht mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Nachrichtentext** in das Textfeld **Wenn ein Benutzer eine Sprachnachricht empfängt** den Text der E-Mail-Nachricht ein, die gesendet wird, wenn Benutzer eine Sprachnachricht empfangen.

4.  Klicken Sie auf **Speichern**.

## Ändern des E-Mail-Nachrichtentexts beim Empfang einer Sprachnachricht mithilfe der Shell

In diesem Beispiel wird der zusätzliche Text "Do not forward voice messages to users outside this organization" in E-Mail-Nachrichten hinzugefügt, die beim Empfang von Sprachnachrichten an Benutzer gesendet werden, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailText "Do not forward voice messages to users outside this organization."

