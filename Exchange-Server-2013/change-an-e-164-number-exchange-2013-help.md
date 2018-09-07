---
title: 'Ändern Sie eine e. 164-Nummer: Exchange Online Help'
TOCTitle: Ändern Sie eine e. 164-Nummer
ms:assetid: 2a3da11b-bb9b-4d4d-9238-6a1a47ef63f2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335162(v=EXCHG.150)
ms:contentKeyID: 50554765
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern Sie eine e. 164-Nummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und ihn mit einem E.164-Wählplan verknüpfen, werden zwei EUM-Proxyadressen erstellt. Eine enthält die Durchwahlnummer des Benutzers, und die andere enthält die E.164-Nummer für den Benutzer. Die Durchwahlnummer wird verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Sie können die primäre E.164-Nummer, die beim Aktivieren des Benutzers für UM hinzugefügt wurde, oder eine sekundäre E.164-Nummer, die später zusammen mit der EUM-Proxyadresse für den Benutzer hinzugefügt wurde, ändern. Die primäre E.164-Nummer, die Sie beim Aktivieren des Benutzers für UM hinzugefügt haben, wird als primäre EUM-Proxyadresse aufgeführt. Weitere von Ihnen hinzugefügte sekundäre E.164-Nummern werden als sekundäre EUM-Proxyadressen aufgeführt. Wenn E.164-Nummern geändert wurden, können Anrufer eine Voicemail für den Benutzer an den neuen E.164-Nummern hinterlassen, die festgelegt wurden. Alle Sprachnachrichten werden an das Postfach des gleichen Benutzers zugestellt.

Sie können mit der Exchange-Verwaltungskonsole oder der Shell die primären und sekundären E.164-Nummern für einen Benutzer ändern. Sie können die Seite **E-Mail-Adresse** im Postfach des Benutzers verwenden, um eine primäre oder sekundäre E.164-Nummer zu ändern. Über die Seite **UM-Postfach** in der Exchange-Verwaltungskonsole können Sie jedoch keine primäre oder sekundäre E.164-Nummer ändern.

Sie können die primären und sekundären E.164-Nummern für einen Benutzer mit dem Cmdlet **Get-UMMailbox** oder dem Cmdlet **Get-Mailbox** in der Shell anzeigen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/voice-mail-enabled-user-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein E.164-UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers für UM aktiviert wurde und mit einem E.164-Wählplan verknüpft ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die E.164-Nummer, die dem UM-aktivierten Benutzer zugewiesen werden soll, gültig ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der primären oder einer sekundären E.164-Nummer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, für das Sie eine E.164-Nummer ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **Benutzerpostfach** unter **E-Mail-Adresse** die E.164-Nummer aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Die primäre E.164-Nummer ist in fett formatierten Buchstaben und Zahlen aufgeführt.

4.  Geben Sie auf der Seite **E-Mail-Adresse** im Feld **Adresse/Durchwahl** die neue E.164-Nummer für den Benutzer ein, und klicken Sie dann auf **OK**. Wenn Sie einen neuen UM-Wählplan auswählen müssen, können Sie auf **Durchsuchen** klicken.

5.  Klicken Sie auf **Speichern**.

## Ändern der primären oder einer sekundären E.164-Nummer mithilfe der Shell

In diesem Beispiel wird eine E.164-Nummer für den UM-aktivierten Benutzer Tony Smith geändert.


> [!NOTE]
> Bevor Sie eine E.164-Nummer mit der Shell ändern, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>, um die Position zu bestimmen. Die erste EUM-Proxyadresse ist die standardmäßige (primäre) E.164-Nummer, und sie ist in der Liste 0.



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(1)="eum:+14255550123;phone-context=MyE.164DialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

