---
title: 'Konfigurieren d. primären Meth. für Suche der Outlook Voice Access-Benutzer'
TOCTitle: Konfigurieren Sie die primäre Methode für Outlook Voice Access-Benutzer suchen
ms:assetid: 3d93a037-5820-41d3-9206-69f534414daf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997563(v=EXCHG.150)
ms:contentKeyID: 50475435
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die primäre Methode für Outlook Voice Access-Benutzer suchen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Beim Erstellen eines Unified Messaging-Wählplans (UM) können Sie die primäre und sekundäre Methode konfigurieren, mit der Anrufer nach Namen suchen können, um einen Benutzer zu ermitteln, wenn sie eine Outlook Voice Access-Nummer oder die Nummer einer automatischen UM-Telefonzentrale anrufen, die dem Wählplan zugeordnet ist. Anrufer können Tonwahleingaben für die Suche nach einem UM-aktivierten Benutzer verwenden.


> [!NOTE]
> <STRONG>Keine</STRONG> ist keine verfügbare Option für die primäre Methode zur Namenssuche. Wenn als sekundäre Methode für die Namenssuche <STRONG>Keine</STRONG> ausgewählt ist, steht Anrufern nur die primäre Methode zur Verfügung. Wenn Sie sowohl die primäre als auch die sekundäre Methode für die Namenssuche konfigurieren, können Anrufer beide Methoden nutzen.



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der primären Methode für die Wahl nach Namen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Verwenden Sie im Abschnitt **Einstellungen** unterhalb von **Primäre Methode für Namenssuche** die Dropdownliste, um die gewünschte Option auszuwählen:
    
      - **Nachname Vorname** (Standardeinstellung)
    
      - **Vorname Nachname**
    
      - **SMTP-Adresse**

5.  Klicken Sie auf **Speichern**.

## Ändern der primären Methode für die Wahl nach Namen mithilfe der Shell

In diesem Beispiel wird die primäre Methode für die Wahl nach Namen auf `FirstLast` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seinen Vornamen und dann über den Nachnamen suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary FirstLast

In diesem Beispiel wird die primäre Methode für die Wahl nach Namen auf `LastFirst` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seinen Nachnamen und dann über den Vornamen suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary LastFirst 

In diesem Beispiel wird die primäre Methode für die Wahl nach Namen auf `SMTP address` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seine SMTP-Adresse suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary SMTPAddress

