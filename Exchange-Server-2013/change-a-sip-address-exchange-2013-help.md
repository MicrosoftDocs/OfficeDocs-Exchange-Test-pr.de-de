---
title: 'Ändern einer SIP-Adresse: Exchange 2013 Help'
TOCTitle: Ändern einer SIP-Adresse
ms:assetid: 33f4f464-9baa-48af-bf5e-a0d55bb45f60
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335189(v=EXCHG.150)
ms:contentKeyID: 50554787
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern einer SIP-Adresse

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und ihn mit einem SIP-URI-Wählplan verknüpfen, werden zwei EUM-Proxyadressen erstellt. Eine enthält die Durchwahlnummer des Benutzers, und die andere enthält die SIP-Adresse für den Benutzer. Die Durchwahlnummer wird verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

SIP-URI-Wählpläne und SIP-Adressen werden verwendet, wenn Sie UM und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren. Die SIP-Adresse wird von Communications Server oder Lync Server verwendet, um eingehende Anrufe weiterzuleiten und Voicemail an den Benutzer zu senden. Standardmäßig ist die von UM verwendete SIP-Adresse die SIP-Adresse, die von Communications Server oder Lync Server verwendet wird.

Sie können die primäre SIP-Adresse, die beim Aktivieren des Benutzers für UM hinzugefügt wurde, oder eine sekundäre SIP-Adresse, die später zusammen mit der EUM-Proxyadresse für den Benutzer hinzugefügt wurde, ändern. Die primäre SIP-Adresse, die Sie beim Aktivieren des Benutzers für UM hinzugefügt haben, wird als primäre EUM-Proxyadresse aufgeführt. Weitere von Ihnen hinzugefügte sekundäre SIP-Adressen werden als sekundäre EUM-Proxyadressen aufgeführt. Wenn sekundäre SIP-Adressen geändert werden, können Anrufer an allen SIP-Endpunkten, bei denen der Benutzer angemeldet ist, über die neuen SIP-Adressen eine Voicemail für den Benutzer hinterlassen. Alle Sprachnachrichten werden an das Postfach des gleichen Benutzers zugestellt.

Sie können eine primäre oder sekundäre SIP-Adresse mit der Exchange-Verwaltungskonsole oder der Shell ändern. Sie können die Seite **E-Mail-Adresse** im Postfach des Benutzers in der Exchange-Verwaltungskonsole verwenden, um eine primäre oder sekundäre SIP-Adresse zu ändern. Über die Seite **UM-Postfach** in der Exchange-Verwaltungskonsole können Sie keine primäre oder sekundäre SIP-Adresse ändern.

Sie können die primären und sekundären SIP-Adressen für einen Benutzer mit dem Cmdlet **Get-UMMailbox** oder dem Cmdlet **Get-Mailbox** in der Shell anzeigen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein SIP-URI-UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der vorhandene Benutzer für UM aktiviert wurde und mit einem SIP-URI-Wählplan verknüpft ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die SIP-Adresse, die dem Benutzer zugewiesen werden soll, gültig und richtig formatiert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der primären oder einer sekundären SIP-Adresse mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, für das Sie eine SIP-Adresse ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **Benutzerpostfach** unter **E-Mail-Adresse** die SIP-Adresse aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Die primäre SIP-Adresse ist in fett formatierten Buchstaben und Zahlen aufgeführt.

4.  Geben Sie auf der Seite **E-Mail-Adresse** im Feld **Adresse/Durchwahl** die neue SIP-Adresse für den Benutzer ein, und klicken Sie dann auf **OK**. Wenn Sie einen neuen UM-Wählplan auswählen müssen, können Sie auf **Durchsuchen** klicken.

5.  Klicken Sie auf **Speichern**.

## Ändern der primären oder einer sekundären SIP-Adresse mithilfe der Shell

In diesem Beispiel wird eine SIP-Adresse für Tony Smith geändert.


> [!NOTE]
> Bevor Sie eine SIP-Adresse mit der Shell ändern, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>, um die Position zu bestimmen. Die erste EUM-Proxyadresse ist die standardmäßige (primäre) SIP-Adresse, und sie ist in der Liste 0.



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(1)="eum:tsmith@contoso.com;phone-context=MySIPDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

