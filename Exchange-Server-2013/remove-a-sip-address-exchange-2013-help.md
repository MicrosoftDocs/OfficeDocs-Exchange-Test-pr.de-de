---
title: 'Entfernen einer SIP-Adresse: Exchange 2013 Help'
TOCTitle: Entfernen einer SIP-Adresse
ms:assetid: eaaff0b0-7d85-4845-a7b8-ac22b42bc415
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ662761(v=EXCHG.150)
ms:contentKeyID: 50554935
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer SIP-Adresse

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und ihn einem SIP-URI-Wählplan zuweisen, werden zwei Exchange Unified Messaging-Proxyadressen (EUM) erstellt. Eine enthält die Durchwahlnummer des Benutzers, die andere seine SIP-Adresse. Die Durchwahlnummer wird verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

SIP-URI-Wählpläne und SIP-Adressen werden verwendet, wenn Sie UM und Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren. Die SIP-Adresse wird von Communications Server oder Lync Server zum Weiterleiten eingehender Anrufe und zum Senden von Voicemail an den Benutzer verwendet. Die von UM verwendete SIP-Adresse ist standardmäßig die von Communications Server oder Lync Server verwendete SIP-Adresse.

Sie können die primäre SIP-Adresse entfernen, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde. Oder Sie können die sekundäre SIP-Adresse, die später hinzugefügt wurde, zusammen mit den EUM-Proxyadressen des Benutzers entfernen. Die primäre SIP-Adresse, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde, wird als primäre EUM-Proxyadresse aufgelistet. Weitere hinzugefügte SIP-Adressen werden als sekundäre EUM-Proxyadressen aufgelistet. Wenn eine SIP-Adresse entfernt wird, können Anrufer keine Voicemail mehr für den Benutzer an der SIP-Adresse hinterlassen, die entfernt wurde, auch wenn der Benutzer mit der SIP-Adresse angemeldet ist, die dem Benutzer Communications Server oder Lync Server zugewiesen wurde.

Wenn Sie die primäre Communications Server oder Lync Server entfernen, kann UM keine Voicemail an das Postfach des Benutzers senden, und Mailboxansageregeln werden nicht verarbeitet. Nachdem die primäre SIP-Adresse entfernt wurde, wird die EUM-Proxyadresse des Benutzers für das Postfach des Benutzers in der Exchange-Verwaltungskonsole und beim Ausführen des Cmdlets **Get-Mailbox** in der Shell als **Null** aufgeführt. Auch wenn Sie das Cmdlet **Get-UMMailbox** ausführen, werden die Parameter *Extensions*, *PhoneNumber* und *CallAnsweringRulesExtensions* leer oder als Null angezeigt.

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell eine primäre oder sekundäre SIP-Adresse entfernen. Sie können in der Exchange-Verwaltungskonsole auf der Seite **E-Mail-Adresse** des Postfachs des Benutzers eine primäre oder sekundäre SIP-Adresse entfernen. Sie können auf der Seite **UM-Postfach** der Exchange-Verwaltungskonsole keine primäre oder sekundäre SIP-Adresse entfernen.

Sie können in der Shell die primäre oder sekundäre SIP-Adresse eines Benutzers mithilfe der Cmdlets **Get-UMMailbox** und**Get-Mailbox** anzeigen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert und mit einem Wählplan vom Typ "SIP-URI" verknüpft wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die primäre oder sekundäre SIP-Adresse für den Benutzer konfiguriert sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen der primären oder sekundären SIP-Adresse mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, aus dem Sie eine SIP-Adresse entfernen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **E-Mail-Adresse** die SIP-Adresse aus, die Sie aus der Liste entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"). Die primäre EUM-Proxyadresse bzw. SIP-Adresse ist in fetten Buchstaben und Zahlen aufgelistet.

4.  Klicken Sie auf **Speichern**.

## Entfernen der primären oder sekundären SIP-Adresse mithilfe der Shell

In diesem Beispiel wird die SIP-Adresse "tsmith@contoso" aus dem Postfach des UM-aktivierten Benutzers Tony Smith entfernt.


> [!NOTE]
> Bevor Sie eine SIP-Adresse mithilfe der Shell entfernen, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Um die Position zu bestimmen, verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>. Die erste EUM-Proxyadresse in der Liste ist 0.



    $mbx = Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(1) -="eum:tsmith@contoso.com;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

