---
title: 'Ändern einer Durchwahlnummer: Exchange 2013 Help'
TOCTitle: Ändern einer Durchwahlnummer
ms:assetid: ff22b366-3bfb-4bf7-9f11-62fba48f1caf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232208(v=EXCHG.150)
ms:contentKeyID: 50554937
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern einer Durchwahlnummer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und mit einem Wählplan vom Typ "Telefondurchwahl" verknüpfen, wird für den Benutzer eine Exchange Unified Messaging-Proxyadresse (EUM) erstellt, die die Durchwahlnummer des Benutzers enthält. Sie müssen mindestens eine Durchwahlnummer für UM definieren, damit Voicemail an das Postfach des Benutzers gesendet werden kann. Die Durchwahlnummer wird auch verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Sie können die primäre Durchwahlnummer ändern, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde. Oder Sie können die sekundäre Durchwahlnummer, die später hinzugefügt wurde, zusammen mit den EUM-Proxyadressen des Benutzers entfernen. Die primäre Durchwahlnummer, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde, wird als primäre EUM-Proxyadresse aufgelistet. Weitere hinzugefügte sekundäre Durchwahlnummern werden als sekundäre EUM-Proxyadressen aufgelistet. Nachdem weitere Durchwahlnummern hinzugefügt wurden, können Anrufer Voicemail für den Benutzer an allen neu eingerichteten Durchwahlnummern hinterlassen. Alle Sprachnachrichten werden an dasselbe Postfach des Empfängers zugestellt.

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell eine primäre oder sekundäre Durchwahlnummer für einen Benutzer ändern. Sie können in der Exchange-Verwaltungskonsole auf der Seite **E-Mail-Adresse** des Postfachs des Benutzers eine primäre oder sekundäre Durchwahlnummer ändern. Auf der Seite **UM-Postfach** in der Exchange-Verwaltungskonsole können Sie zwar keine primäre, aber eine sekundäre Durchwahlnummer ändern. Wenn Sie eine sekundäre Durchwahlnummer ändern möchten, müssen Sie zunächst die vorhandene sekundäre Durchwahlnummer entfernen und anschließend die ordnungsgemäße sekundäre Durchwahlnummer für den Benutzer hinzufügen.

Sie können in der Shell die primäre oder sekundäre Durchwahlnummer eines Benutzers mithilfe der Cmdlets **Get-UMMailbox** und**Get-Mailbox** anzeigen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan für Telefondurchwahlen erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert und mit einem Wählplan vom Typ "Telefondurchwahl" verknüpft wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die Durchwahlnummer, die dem Benutzer zugewiesen ist, die ordnungsgemäße Anzahl von Stellen aufweist, die für den UM-Wählplan festgelegt ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der primären oder sekundären Durchwahlnummer über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, für das Sie eine Durchwahlnummer ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **E-Mail-Adresse** die Durchwahlnummer aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Die primäre Durchwahlnummer ist in fetten Buchstaben und Zahlen aufgelistet.

4.  Wählen Sie auf der Seite **E-Mail-Adresse** die Option **Adresse/Erweiterung** aus, und geben Sie die neue Durchwahlnummer für den Benutzer ein. Wenn Sie einen neuen UM-Wählplan auswählen müssen, klicken Sie auf **Durchsuchen**.

5.  Klicken Sie auf **Speichern**.

## Ändern der primären oder sekundären Durchwahlnummer über die Shell

In diesem Beispiel wird die Durchwahlnummer 22222 für den UM-aktivierten Benutzer Tony Smith geändert.


> [!NOTE]
> Bevor Sie eine Durchwahlnummer mithilfe der Shell ändern, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Um die Position zu bestimmen, verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>. Die erste EUM-Proxyadresse ist die standardmäßige (primäre) Durchwahlnummer, die mit 0 in der Liste angezeigt wird.



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(0)="eum:22222;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

