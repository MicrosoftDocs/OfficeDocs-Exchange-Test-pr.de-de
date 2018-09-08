---
title: 'Hinzufügen v. Text der gesendeten E-Mail, wenn eine PIN zurückgesetzt wurde'
TOCTitle: Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn ein Zurücksetzen PIN-Nummer ist text
ms:assetid: f7a4d775-a588-412f-ac2c-11ab1a5c67eb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201750(v=EXCHG.150)
ms:contentKeyID: 51409367
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Enthalten Sie mit der e-Mail-Nachricht gesendet, wenn ein Zurücksetzen PIN-Nummer ist text

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können zusätzlichen Text in die E-Mail-Nachricht aufnehmen, die Benutzer erhalten, wenn ihre UM (Unified Messaging)- oder Voicemail-PIN zurückgesetzt wird. Geben Sie dazu in einer UM-Postfachrichtlinie in das Feld **Wenn die Outlook Voice Access-PIN eines Benutzers zurückgesetzt wird** benutzerdefinierten Text ein. Der benutzerdefinierte Text kann z. B. sicherheitsrelevante Informationen für UM-aktivierte Benutzer enthalten.

Eine für Outlook Voice Access verwendete PIN wird vom Unified Messaging- oder Voicemailsystem standardmäßig nach 5 fehlgeschlagenen Anmeldeversuchen zurückgesetzt. Benutzer können ihre PINs auch über die UM-Funktionen in Outlook Web App bzw. Outlook 2010 oder höher oder von einem Telefon aus über Outlook Voice Access zurücksetzen.


> [!NOTE]
> Die Texteingabe in das Feld ist auf 512 Zeichen beschränkt und kann einfachen HTML-Text umfassen.



Weitere Aufgaben im Zusammenhang mit der Sicherheit von Outlook Voice Access-PINs finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Hinzufügen von Text zur E-Mail-Nachricht, die Benutzer erhalten, wenn ihre PIN zurückgesetzt wird, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Nachrichtentext** in das Textfeld für **Wenn die Outlook Voice Access-PIN eines Benutzers zurückgesetzt wird** den Text ein, der in die E-Mail aufgenommen werden soll, die Benutzern beim Zurücksetzen ihrer PIN zugesendet wird.

4.  Klicken Sie auf **Speichern**.

## Hinzufügen von Text zur E-Mail-Nachricht, die Benutzer erhalten, wenn ihre PIN zurückgesetzt wird, mithilfe der Shell

In diesem Beispiel wird der E-Mail, die den Benutzern, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, beim Zurücksetzen ihrer PIN zugesendet wird, der Text "Do not share your PIN with other users. Doing so may result in disciplinary action" hinzugefügt.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -ResetPINText "Do not share your PIN with other users. Doing so may result in disciplinary action."

