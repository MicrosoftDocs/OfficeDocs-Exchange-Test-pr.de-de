---
title: 'Hinzufügen v. Text der gesendeten E-Mail, wenn Faxnachricht empfangen wird'
TOCTitle: Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn eine Faxnachricht empfangen wird text
ms:assetid: 48244e58-b7d6-4f0e-bbae-d22bf0fc11ff
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201684(v=EXCHG.150)
ms:contentKeyID: 51409283
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn eine Faxnachricht empfangen wird text

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können zusätzlichen Text in die zu sendende E-Mail einschließen, wenn eine Faxnachricht von einem Benutzer empfangen wird, der für UM-Voicemail (Unified Messaging) und auch für den Faxempfang aktiviert ist, und wenn die UM-Postfachrichtlinie ordnungsgemäß für die Verwendung eines Faxpartneranbieters konfiguriert wurde. Standardmäßig gibt der Text, der verwendet wird, wenn ein UM-aktivierter Benutzer eine Faxnachricht empfängt, nur an, dass der Benutzer eine Faxnachricht empfangen hat. Sie können jedoch auch eine benutzerdefinierte Nachricht erstellen, indem Sie für eine UM-Postfachrichtlinie Text im Textfeld **Wenn ein Benutzer eine Faxnachricht empfängt** hinzufügen. Dieser Text kann z. B. Informationen zu Systemsicherheitsrichtlinien enthalten und das ordnungsgemäße Verfahren für den Umgang mit Faxnachrichten in Ihrer Organisation beschreiben. Nachdem Sie den Text hinzugefügt haben, wird er in jede E-Mail eingefügt, die gesendet wird, wenn UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, eine Faxnachricht empfangen.


> [!NOTE]
> Der benutzerdefinierte Text, der mit einer Faxnachricht gesendet wird, darf maximal 512 Zeichen lang sein und kann einfachen HTML-Text enthalten.



Weitere Informationen zu Fax Partner finden Sie unter [Microsoft Hindernissen bei für Fax Partner](https://go.microsoft.com/fwlink/?linkid=190238).

Weitere Verwaltungsaufgaben im Zusammenhang mit Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern des in eine Faxnachricht eingebundenen Texts mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Nachrichtentext** im Textfeld für **Wenn ein Benutzer für Unified Messaging aktiviert ist** den Text ein, der in der E-Mail enthalten sein soll, die beim Erhalt einer Faxnachricht im Postfach von Benutzern gesendet wird.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell, um den in eine Faxnachricht eingebundenen Text zu ändern

In diesem Beispiel wird es UM-aktivierten Benutzern, denen eine UM-Postfachrichtlinie zugeordnet ist, ermöglicht, weitere Anweisungen zum Öffnen von Faxnachrichten zu erhalten, die in ihrem Postfach eingehen.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -FaxMessageText "To open this fax message, double-click the file attachment."

