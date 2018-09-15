---
title: 'Aktivieren o. Deaktivieren des IMAP4-Zugriffs für Ben.: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren des IMAP4-Zugriffs für einen Benutzer
ms:assetid: a685fae4-b6f1-42fe-8bdc-5f99f9617799
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb676481(v=EXCHG.150)
ms:contentKeyID: 50476369
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren des IMAP4-Zugriffs für einen Benutzer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-01-18_

Sie können IMAP4 für einen Benutzer aktivieren oder deaktivieren.


> [!NOTE]
> Nachdem Sie IMAP4 für einen Benutzer aktiviert oder deaktiviert haben, müssen Sie den IMAP4-Dienst und den IMAP4-Back-End-Dienst von Microsoft Exchange neu starten. Weitere Informationen zum Neustarten des IMAP4-Diensts finden Sie unter <A href="start-and-stop-the-imap4-services-exchange-2013-help.md">Starten und Stoppen der IMAP4-Dienste</A>.



Weitere Informationen zum Verwalten von Benutzerpostfächern finden Sie unter [Verwalten von Benutzerpostfächern](https://technet.microsoft.com/de-de/library/Bb123809(v=EXCHG.150)).

Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren von IMAP4 für einen Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Wählen Sie im Ergebnisbereich den Benutzer aus, für den Sie IMAP4 aktivieren oder deaktivieren möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie im Dialogfeld **Benutzerpostfach** in die Konsolenstruktur und dann auf **Postfachfeatures**.
    
    Gehen Sie im Ergebnisbereich unter **E-Mail-Konnektivität** wie folgt vor:
    
      - Klicken Sie zum Deaktivieren von IMAP4 für den Benutzer unterhalb von **IMAP4: Aktiviert** auf **Deaktivieren**.
    
      - Klicken Sie zum Aktivieren von IMAP4 für den Benutzer unterhalb von **IMAP4: Deaktiviert** auf **Aktivieren**.

4.  Klicken Sie auf **Speichern**.

## Aktivieren oder Deaktivieren von IMAP4 für ein Benutzerpostfach mithilfe der Shell

Im folgenden Beispiel wird IMAP4 für den Benutzer John Smith aktiviert.

    Set-CASMailbox -Identity "John Smith" -IMAPEnabled $true

In diesem Beispiel wird IMAP4 für den Benutzer John Smith deaktiviert.

    Set-CASMailbox -Identity "John Smith" -IMAPEnabled $false

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Wählen Sie im Ergebnisbereich den Benutzer aus, für den Sie IMAP4 aktivieren oder deaktivieren möchten, und klicken Sie auf **Bearbeiten**.

3.  Klicken Sie im Dialogfeld **Benutzerpostfach** in die Konsolenstruktur und dann auf **Postfachfeatures**.
    
    Sehen Sie im Ergebnisbereich unter **E-Mail-Konnektivität** nach.
    
      - Wenn IMAP4 für den Benutzer aktiviert ist, sehen Sie die Einstellung **IMAP4: Aktiviert**.
    
      - Wenn IMAP4 für den Benutzer nicht aktiviert ist, sehen Sie die Einstellung **IMAP4: Deaktiviert**.

4.  Klicken Sie auf **Speichern**.

