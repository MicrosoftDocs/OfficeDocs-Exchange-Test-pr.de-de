---
title: 'Hinzufügen einer Durchwahlnummer: Exchange Online Help'
TOCTitle: Hinzufügen einer Durchwahlnummer
ms:assetid: 1a73c9c8-cb50-4bd7-a101-dadd20e28031
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335124(v=EXCHG.150)
ms:contentKeyID: 50554813
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hinzufügen einer Durchwahlnummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Wenn Sie einen Benutzer für UM aktivieren und mit einem Telefondurchwahl-Wählplan verknüpfen, wird eine EUM-Proxyadresse für den Benutzer erstellt, die die Durchwahlnummer des Benutzers enthält. Sie müssen mindestens eine Durchwahlnummer für UM erstellen, damit Voicemail an das Postfach des Benutzers gesendet werden kann. Die Durchwahlnummer wird auch verwendet, wenn der Benutzer eine Outlook Voice Access-Nummer anruft.

Die primäre Durchwahlnummer, die Sie beim Aktivieren des Benutzers für UM hinzugefügt haben, wird als primäre EUM-Proxyadresse aufgeführt. Wenn die primäre Durchwahlnummer entfernt wurde, wird die erste von Ihnen hinzugefügte EUM-Proxyadresse, die die Durchwahlnummer des Benutzers enthält, zur primären EUM-Proxyadresse. Weitere von Ihnen hinzugefügte Durchwahlnummern werden als sekundäre EUM-Proxyadressen aufgeführt. Wenn zusätzliche sekundäre Durchwahlnummern hinzugefügt werden, können Anrufer an allen festgelegten Durchwahlnummern Voicemail für den Benutzer hinterlassen. Alle Sprachnachrichten werden an das Postfach des gleichen Benutzers zugestellt.

Sie können mit der Exchange-Verwaltungskonsole oder der Shell eine primäre oder eine sekundäre Durchwahlnummer für einen Benutzer hinzufügen. Sie können die Seite **E-Mail-Adresse** im Postfach des Benutzers in der Exchange-Verwaltungskonsole verwenden, um eine primäre oder sekundäre Durchwahlnummer hinzuzufügen. Über die Seite **UM-Postfach** in der Exchange-Verwaltungskonsole können Sie keine primäre Durchwahlnummer hinzufügen, Sie können über diese Seite aber sekundäre Durchwahlnummern hinzufügen.

Sie können die primären und sekundären Durchwahlnummern für einen Benutzer mit dem Cmdlet **Get-UMMailbox** oder dem Cmdlet **Get-Mailbox** in der Shell anzeigen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan für Telefondurchwahlnummern erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers für UM aktiviert wurde und mit einem Telefondurchwahl-Wählplan verknüpft ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass die Durchwahlnummer, die dem Benutzer zugewiesen wird, die richtige, im UM-Wählplan festgelegte Anzahl von Ziffern aufweist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Hinzufügen einer sekundären Durchwahlnummer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dem eine Durchwahlnummer hinzugefügt werden soll.

3.  Klicken Sie im Detailbereich **Telefon- und Sprachfunktionen** unter **Unified Messaging** auf **Details anzeigen**.

4.  Klicken Sie auf der Seite **UM-Postfach** auf **Andere Durchwahlen** und dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Klicken Sie auf der Seite **Andere Durchwahlen** neben **UM-Wählplan** auf **Durchsuchen**, und suchen Sie nach dem Wählplan für den Benutzer.

6.  Geben Sie auf der Seite **Andere Durchwahlen** im Feld **Durchwahlnummer** die Durchwahlnummer ein, und klicken Sie dann auf **OK**.

7.  Klicken Sie auf **Speichern**.

## Hinzufügen einer primären oder sekundären Durchwahlnummer mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dem Sie eine Durchwahlnummer hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Benutzerpostfach** unter **E-Mail-Adresse** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Neue E-Mail-Adresse** die Option **EUM** aus, und geben Sie im Feld **Adresse/Durchwahl** die Durchwahlnummer für den Benutzer ein.

5.  Klicken Sie auf der Seite **Neue E-Mail-Adresse** unter **Wählplan** auf **Durchsuchen**, um einen Telefondurchwahl-Wählplan auszuwählen, und klicken Sie dann auf **OK**.

6.  Klicken Sie auf **Speichern**.

## Hinzufügen einer Durchwahlnummer mithilfe der Shell

In diesem Beispiel wird die Durchwahlnummer 22222 für Tony Smith, einem UM-aktivierten Benutzer, hinzugefügt.


> [!NOTE]
> Bevor Sie eine Durchwahlnummer mit der Shell hinzufügen, müssen Sie die Position der EUM-Proxyadresse bestimmen, die Sie hinzufügen möchten. Verwenden Sie den Befehl <STRONG>$mbx.EmailAddresses</STRONG>, um die Position zu bestimmen. Die erste Proxyadresse in der Liste ist 0.



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses +="eum:22222;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

