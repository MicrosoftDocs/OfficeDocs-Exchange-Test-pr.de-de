---
title: 'Konfigurieren Sie die sekundäre Methode für Outlook Voice Access-Benutzer suchen: Exchange Online Help'
TOCTitle: Konfigurieren Sie die sekundäre Methode für Outlook Voice Access-Benutzer suchen
ms:assetid: 5cd4e0a0-d023-45a1-aa3c-b8dea6ec6d72
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998311(v=EXCHG.150)
ms:contentKeyID: 52062706
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die sekundäre Methode für Outlook Voice Access-Benutzer suchen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Bei der Erstellung eines Wählplans können Sie die primäre und die sekundäre *Wahlmethode nach Namen* oder Möglichkeiten konfigurieren, mit denen Anrufer nach Namen suchen können. Mithilfe dieser Methoden für die Wahl nach Namen können Anrufer Namen nachschlagen, um einen Benutzer zu ermitteln und zu kontaktieren, wenn sie eine Outlook Voice Access-Nummer oder eine automatische UM-Telefonzentrale anrufen, die dem Wählplan zugeordnet ist. Anrufer können Tonwahleingaben für die Suche nach einem UM-aktivierten Benutzer verwenden.


> [!NOTE]
> Wenn <STRONG>Keine</STRONG> als sekundäre Methode für die Suche nach Namen ausgewählt ist, steht Anrufern beim Suchen nach Benutzern nur die primäre Methode für die Namenssuche zur Verfügung. Wenn Sie sowohl die primäre als auch die sekundäre Methode für die Namenssuche konfigurieren, können Anrufer beide Methoden nutzen.



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der sekundären Methode für die Wahl nach Namen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Verwenden Sie im Abschnitt **Einstellungen** unter **Sekundäre Methode für Namenssuche** die Dropdownliste, um die gewünschte Option auszuwählen:
    
      - **Nachname Vorname** (Standardeinstellung)
    
      - **Vorname Nachname**
    
      - **SMTP-Adresse**
    
      - **Keine**

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell, um die sekundäre Methode für die Wahl nach Namen zu ändern

In diesem Beispiel wird die sekundäre Methode für die Wahl nach Namen auf `FirstLast` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seinen Vornamen und dann über den Nachnamen suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary FirstLast

In diesem Beispiel wird die sekundäre Methode für die Wahl nach Namen auf `LastFirst` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seinen Nachnamen und dann über den Vornamen suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary LastFirst 

In diesem Beispiel wird die sekundäre Methode für die Wahl nach Namen auf `SMTP address` festgelegt. Dadurch können Anrufer, die die Outlook Voice Access-Nummer oder eine mit der Wähleinstellung verbundene UM-Telefonzentrale anrufen, nach einem UM-aktivierten Benutzer über seine SMTP-Adresse suchen.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary SMTPAddress 

In diesem Beispiel wird `None` als sekundäre Methode und `SMTP address` als primäre Methode für die Wahl nach Namen festgelegt. Dies bewirkt, dass Anrufer, die die Outlook Voice Access-Nummer oder eine dem Satz Wähleinstellungen zugeordnete automatische UM-Telefonzentrale anrufen, nur anhand der SMTP-Adresse nach einem UM-aktivierten Benutzer suchen können.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary SMTPAddress -DialByNameSecondary None

