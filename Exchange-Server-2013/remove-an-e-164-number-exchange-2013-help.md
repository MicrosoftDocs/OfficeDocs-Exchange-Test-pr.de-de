---
title: 'Entfernen einer e. 164-Nummer: Exchange Online Help'
TOCTitle: Entfernen einer e. 164-Nummer
ms:assetid: 17941918-7dc5-41a0-b540-09f2f907362b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ662759(v=EXCHG.150)
ms:contentKeyID: 50554783
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer e. 164-Nummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und ihn mit einem E.164-Wählplan verknüpfen, werden zwei EUM-Proxyadressen erstellt. Eine enthält die Durchwahlnummer des Benutzers, und die andere enthält die E.164-Nummer für den Benutzer. Die Durchwahlnummer wird verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Sie können die primäre E.164-Nummer, die beim Aktivieren des Benutzers für UM hinzugefügt wurde, oder eine sekundäre E.164-Nummer, die später zusammen mit der EUM-Proxyadresse für den Benutzer hinzugefügt wurde, entfernen. Die primäre E.164-Nummer, die Sie beim Aktivieren des Benutzers für UM hinzugefügt haben, wird als primäre EUM-Proxyadresse aufgeführt. Weitere von Ihnen hinzugefügte E.164-Nummern werden als sekundäre EUM-Proxyadressen aufgeführt. Wenn eine E.164-Nummer entfernt wird, können Anrufer über die entfernte E.164-Nummer keine Voicemail mehr für den Benutzer hinterlassen.

Wenn Sie die primäre E.164-Nummer entfernen, kann UM keine Voicemail mehr an das Postfach des Benutzers senden, und Mailboxansageregeln werden nicht verarbeitet. Nachdem Sie die primäre E.164-Nummer entfernt haben, wird die EUM-Proxyadresse für den Benutzer in der Exchange-Verwaltungskonsole im Postfach des Benutzers und in der Shell nach der Ausführung des Cmdlets **Get-Mailbox** als **Null** aufgeführt. Auch wenn Sie das Cmdlet **Get-UMMailbox** ausführen, sind die Parameter *Extensions*, *PhoneNumber* und *CallAnsweringRulesExtensions* leer oder Null.

Sie können mit der Exchange-Verwaltungskonsole oder der Shell eine primäre oder eine sekundäre E.164-Nummer für einen Benutzer entfernen. Sie können die Seite **E-Mail-Adresse** im Postfach des Benutzers in der Exchange-Verwaltungskonsole verwenden, um eine primäre oder sekundäre E.164-Nummer zu entfernen. Über die Seite **UM-Postfach** in der Exchange-Verwaltungskonsole können Sie keine primäre oder sekundäre E.164-Nummer entfernen.

Sie können die primären und sekundären E.164-Nummern für einen Benutzer mit dem Cmdlet **Get-UMMailbox** oder dem Cmdlet **Get-Mailbox** in der Shell anzeigen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit für Voicemail aktivierten Benutzern finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein E.164-UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers für UM aktiviert wurde und mit einem E.164-Wählplan verknüpft ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die primären und sekundären E.164-Nummern für den Benutzer konfiguriert sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen der primären oder einer sekundären E.164-Nummer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, aus dem Sie eine E.164-Nummer entfernen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **Benutzerpostfach** unter **E-Mail-Adresse** die E.164-Nummer aus, die Sie aus der Liste entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"). Die primäre EUM-Proxyadresse oder E.164-Nummer ist in fett formatierten Buchstaben und Zahlen aufgeführt.

4.  Klicken Sie auf **Speichern**.

## Entfernen der primären oder einer sekundären E.164-Nummer mithilfe der Shell

In diesem Beispiel wird die E.164-Nummer +14255551010 aus dem Postfach des UM-aktivierten Benutzers Tony Smith entfernt.


> [!NOTE]
> Bevor Sie eine E.164-Nummer mit der Shell entfernen, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>, um die Position zu bestimmen. Die erste EUM-Proxyadresse in der Liste ist 0.



    $mbx = Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(1) -="eum:+14255551010;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

