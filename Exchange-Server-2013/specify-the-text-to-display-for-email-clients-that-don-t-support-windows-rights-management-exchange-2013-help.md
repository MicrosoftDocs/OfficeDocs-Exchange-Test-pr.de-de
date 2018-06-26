---
title: 'Geben Sie den Text, der für e-Mail-Clients angezeigt, die Windows Rights Management nicht unterstützen: Exchange Online Help'
TOCTitle: Geben Sie den Text, der für e-Mail-Clients angezeigt, die Windows Rights Management nicht unterstützen
ms:assetid: a9b2238a-b534-469c-a0c3-2768bc3d005b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423552(v=EXCHG.150)
ms:contentKeyID: 52062767
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Geben Sie den Text, der für e-Mail-Clients angezeigt, die Windows Rights Management nicht unterstützen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Sie können den an Benutzer gesendeten Text angeben, wenn dieser eine geschützte Sprachnachricht empfängt, ihr E-Mail-Client aber die Verwaltung von Informationsrechten (IRM) oder Windows-Rechteverwaltung nicht unterstützt.

Der Zugriff auf geschützte Voicemail kann nur über E-Mail-Clients erfolgen, die die Windows-Rechteverwaltung unterstützen, oder wenn ein UM-aktivierter Benutzer mit Outlook Voice Access auf eine geschützte Sprachnachricht zugreift.

Geschützte Voicemail ist verschlüsselt. Wenn eine Sprachnachricht geschützt ist, gilt Folgendes:

  - Die Nachricht wird in Microsoft Outlook und Outlook Web App als **Privat** gekennzeichnet.

  - Die Sprachnachricht kann nur vom vorgesehenen Empfänger geöffnet werden.

  - Der Empfänger hat zwar die Möglichkeit, auf die Sprachnachricht zu antworten, er kann sie jedoch nicht an Benutzer weiterleiten, die nicht als Empfänger in der ursprünglichen Sprachnachricht enthalten waren.

Beim Senden einer geschützten Sprachnachricht an einen Benutzer, dessen E-Mail-Client keine Windows-Rechteverwaltung unterstützt und der nicht mit Outlook Voice Access auf die Nachricht zugreift, wird eine E-Mail-Nachricht mit dem von Ihnen angegebenen Text an diesen Benutzer gesendet. Dieser Text sollte Anweisungen zu den Schritten enthalten, die der angerufene Teilnehmer ausführen muss, um die geschützte Sprachnachricht empfangen zu können.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Verfahren für geschützte Voicemail finden Sie unter [Geschützte Voicemail-Prozeduren](protected-voice-mail-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Angeben des anzuzeigenden Texts für E-Mail-Clients, die keine Windows-Rechteverwaltung unterstützen

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Geschützte Voicemail** unter **Nachricht, die an Benutzer gesendet werden soll, die keine Unterstützung durch Windows-Rechteverwaltung haben** den Meldungstext in das Textfeld ein.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Angeben des anzuzeigenden Texts für E-Mail-Clients, die keine Windows-Rechteverwaltung unterstützen

In diesem Beispiel wird der Text angegeben, der den der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordneten Benutzern angezeigt wird, deren E-Mail-Clients keine Windows-Rechteverwaltung unterstützen.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -ProtectedVoiceMailText "Your email client software does not support Protected Voice Mail. Please contact the Help Desk."

