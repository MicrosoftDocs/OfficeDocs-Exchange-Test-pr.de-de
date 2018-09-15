---
title: 'Entfernen einer Durchwahlnummer: Exchange Online Help'
TOCTitle: Entfernen einer Durchwahlnummer
ms:assetid: c2b896cf-21f7-4453-a4e6-b23d236a6dd3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351124(v=EXCHG.150)
ms:contentKeyID: 50554921
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen einer Durchwahlnummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-07-21_

Wenn Sie einen Benutzer für UM aktivieren und mit einem Wählplan vom Typ "Telefondurchwahl" verknüpfen, wird für den Benutzer eine Exchange Unified Messaging-Proxyadresse (EUM) erstellt, die die Durchwahlnummer des Benutzers enthält. Sie müssen mindestens eine Durchwahlnummer für UM definieren, damit Voicemail an das Postfach des Benutzers gesendet werden kann. Die Durchwahlnummer wird auch verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Sie können die primäre Durchwahlnummer entfernen, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde. Oder Sie können die sekundäre Durchwahlnummer, die später hinzugefügt wurde, zusammen mit den EUM-Proxyadressen des Benutzers entfernen. Die primäre Durchwahlnummer, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde, wird als primäre EUM-Proxyadresse aufgelistet. Weitere hinzugefügte Durchwahlnummern werden als sekundäre EUM-Proxyadressen aufgelistet. Nach dem Entfernen einer Durchwahlnummer können Anrufer keine Voicemail mehr für den Benutzer an dieser Durchwahlnummern hinterlassen.

Wenn Sie die primäre Durchwahlnummer entfernen, kann UM keine Voicemail an das Postfach des Benutzers senden, und Mailboxansageregeln werden nicht verarbeitet. Nachdem die primäre Durchwahlnummer entfernt wurde, wird die EUM-Proxyadresse des Benutzers für das Postfach des Benutzers in der Exchange-Verwaltungskonsole und beim Ausführen des Cmdlets **Get-Mailbox** in der Shell als **Null** aufgeführt. Auch wenn Sie das Cmdlet **Get-UMMailbox** ausführen, werden die Parameter *Extensions*, *PhoneNumber* und *CallAnsweringRulesExtensions* leer oder als Null angezeigt.

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell eine primäre oder sekundäre Durchwahlnummer entfernen. Sie können in der Exchange-Verwaltungskonsole auf der Seite **E-Mail-Adresse** des Postfachs des Benutzers eine primäre oder sekundäre Durchwahlnummer entfernen. Auf der Seite **UM-Postfach** der Exchange-Verwaltungskonsole können Sie zwar keine primäre, aber eine sekundäre Durchwahlnummer entfernen.

Sie können in der Shell die primäre oder sekundäre Durchwahlnummer eines Benutzers mithilfe der Cmdlets **Get-UMMailbox** und**Get-Mailbox** anzeigen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert und mit einem Wählplan vom Typ "Telefondurchwahl" verknüpft wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die primäre oder sekundäre Durchwahlnummer für den Benutzer konfiguriert sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Entfernen der primären oder sekundären Durchwahlnummer über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, aus dem Sie eine Durchwahlnummer entfernen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **E-Mail-Adresse** die Durchwahlnummer aus, die Sie aus der Liste entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"). Die primäre EUM-Proxyadresse bzw. Durchwahlnummer ist in fetten Buchstaben und Zahlen aufgelistet.

4.  Klicken Sie auf **Speichern**.

## Entfernen einer sekundären Durchwahlnummer über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, aus dessen Postfach eine Durchwahlnummer entfernt werden soll.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** \> **Unified Messaging** auf **Details anzeigen**.

4.  Wählen Sie auf der Seite **Andere Durchwahlen** im Feld **Durchwahlnummer** die Durchwahlnummer aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

5.  Klicken Sie auf **Speichern**.

## Entfernen einer Durchwahlnummer mithilfe der Shell

In diesem Beispiel wird die Durchwahlnummer 12345 aus dem Postfach des UM-aktivierten Benutzers Tony Smith entfernt.


> [!NOTE]
> Bevor Sie eine Durchwahlnummer mithilfe der Shell entfernen, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Um die Position zu bestimmen, verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>. Die erste EUM-Proxyadresse in der Liste ist 0.



    $mbx = Get-Mailbox tony.smith
    $mbx.EmailAddresses.remove("eum:22222;phone-context=MyDialPlan.contoso.com") 
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

