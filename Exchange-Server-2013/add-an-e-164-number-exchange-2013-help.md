---
title: 'Hinzufügen einer E.164-Nummer: Exchange Online Help'
TOCTitle: Hinzufügen einer E.164-Nummer
ms:assetid: fab86207-be03-40ef-9fea-045a50f3d122
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ662762(v=EXCHG.150)
ms:contentKeyID: 50554945
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hinzufügen einer E.164-Nummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und ihn einem E.164-Wählplan zuweisen, werden zwei Exchange Unified Messaging-Proxyadressen (EUM) erstellt. Eine enthält die Durchwahlnummer des Benutzers, die andere seine E.164-Adresse. Die Durchwahlnummer wird verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Die primäre E.164-Nummer, die hinzugefügt wurde, als der Benutzer für UM aktiviert wurde, wird als primäre EUM-Proxyadresse aufgelistet. Nachdem die primäre E.164-Nummer entfernt wurde, wird die erste EUM-Proxyadresse, die Sie hinzufügen und die E.164-Nummer des Benutzers enthält, als primäre EUM-Proxyadresse aufgelistet. Weitere hinzugefügte E.164-Nummern werden als sekundäre EUM-Proxyadressen aufgelistet. Nachdem weitere E.164-Nummern hinzugefügt wurden, können Anrufer Voicemail für den Benutzer an allen eingerichteten E.164-Nummern hinterlassen. Alle Sprachnachrichten werden an dasselbe Postfach des Empfängers zugestellt.

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell eine primäre oder sekundäre E.164-Nummer für einen Benutzer hinzufügen. Sie können auf der Seite **E-Mail-Adresse** des Postfachs des Benutzers in der Exchange-Verwaltungskonsole eine primäre oder sekundäre E.164-Nummer hinzufügen. Sie können auf der Seite **UM-Postfach** der Exchange-Verwaltungskonsole keine primäre oder sekundäre E.164-Nummer hinzufügen.

Sie können in der Shell die primäre oder sekundäre E.164-Nummer eines Benutzers mithilfe der Cmdlets **Get-UMMailbox** und**Get-Mailbox** anzeigen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass E.164-UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert und mit einem Wählplan vom Typ "E.164" verknüpft wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die E.164-Nummer, die dem Benutzer zugewiesen ist, gültig und ordnungsgemäß formatiert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Hinzufügen einer primären oder sekundären E.164-Nummer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dem Sie eine E.164-Nummer hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Postfach** unter **E-Mail-Adresse** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Neue E-Mail-Adresse** die Option **EUM** aus, und geben Sie in das Feld **Adresse/Durchwahl** die neue E.164-Nummer für den Benutzer ein.

5.  Klicken Sie auf der Seite **Neue E-Mail-Adresse** unter **Wählplan** auf **Durchsuchen**, um den E.164-Wählplan auszuwählen. Klicken Sie anschließend auf **OK**.

6.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Hinzufügen einer E.164-Nummer

In diesem Beispiel wird eine E.164-Nummer für Tony Smith, einen UM-aktivierten Benutzer, hinzugefügt.


> [!NOTE]
> Bevor Sie eine E.164-Nummer mithilfe der Shell entfernen, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie ändern möchten. Diese Position können Sie mit dem Befehl <STRONG>$mbx.EmailAddresses</STRONG> bestimmen. Die erste Proxyadresse in der Liste ist 0.



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(2)="eum:+14255550123;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

