---
title: 'Konfigurieren der E-Mail-Weiterleitung für ein Postfach: Exchange 2013 Help'
TOCTitle: Konfigurieren der E-Mail-Weiterleitung für ein Postfach
ms:assetid: c7a7afaf-577e-49d6-8cee-bb4c4a5d570b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351134(v=EXCHG.150)
ms:contentKeyID: 50554905
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der E-Mail-Weiterleitung für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Bei der E-Mail-Weiterleitung können Sie ein Postfach einrichten, sodass an dieses Postfach gesendete E-Mail-Nachrichten an das Postfach eines anderen Benutzers innerhalb oder außerhalb Ihrer Organisation weitergeleitet werden.


> [!IMPORTANT]
> Wenn Sie Office 365 für Business verwenden, sollten Sie in der <A href="https://go.microsoft.com/fwlink/p/?linkid=834774">Office 365-Verwaltungskonsole eine E-Mail-Weiterleitung konfigurieren: Konfigurieren einer E-Mail-Weiterleitung in Office 365</A>



Wenn Ihre Organisation eine lokale Exchange-Hybridumgebung verwendet, sollten Sie das lokale Exchange Admin Center (EAC) zum Erstellen und Verwalten von freigegebenen Postfächern verwenden.

## Konfigurieren der E-Mail-Weiterleitung mithilfe des Exchange-Verwaltungskonsole

Sie können im Exchange-Verwaltungskonsole (EAC) die E-Mail-Weiterleitung an einen einzelnen internen Empfänger, einen einzelnen externen Empfänger (mit einer E-Mail-Adresse) oder an mehrere Empfänger (mit einer Verteilergruppe) einrichten.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken oder tippen Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie die E-Mail-Weiterleitung konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Wählen Sie unter **E-Mail-FlussDetails anzeigen** aus, um die Einstellung für die Weiterleitung von E-Mail-Nachrichten anzuzeigen oder zu ändern.
    
    Auf dieser Seite können Sie die maximale Anzahl von Empfängern festlegen, an die der Benutzer eine Nachricht senden kann. Für lokale Exchange-Organisationen ist die Empfängeranzahl unbegrenzt. Für Exchange Online-Organisationen ist die Anzahl auf 500 Empfänger begrenzt.

5.  Aktivieren Sie das Kontrollkästchen **Weiterleitung aktivieren**, und klicken Sie dann auf **Durchsuchen**.

6.  Wählen Sie auf der Seite **Empfänger wählen** einen Benutzer aus, an den die E-Mail weitergeleitet werden soll. Aktivieren Sie das Kontrollkästchen **Nachricht an Weiterleitungsadresse und Postfach übermitteln**, wenn der Empfänger und die E-Mail-Adresse für die Weiterleitung Kopien der gesendeten E-Mails erhalten sollen. Klicken oder tippen Sie auf **OK** und anschließend auf **Speichern**.

Wie gehen Sie vor, wenn Sie E-Mails an eine E-Mail-Adresse außerhalb Ihrer Organisation weiterleiten möchten? Oder E-Mail-Nachrichten an mehrere Empfänger weiterleiten? Dies ist ebenfalls möglich.

  - **Externe Adressen**Erstellen Sie einen E-Mail-Kontakt, und wählen Sie dann in den vorhergehenden Schritten den E-Mail-Kontakt auf der Seite **Empfänger auswählen**. Möchten Sie wissen, wie Sie einen E-Mail-Kontakt erstellen? Weitere Informationen finden Sie hier: [Verwalten von E-Mail-Kontakten](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-mail-contacts).

  - **Mehrere Empfänger**Erstellen Sie eine Verteilergruppe, fügen Sie Empfänger zu dieser hinzu, und wählen Sie dann den E-Mail-Kontakt in den vorhergehenden Schritten auf der Seite **Empfänger auswählen**. Möchten Sie wissen, wie Sie einen E-Mail-Kontakt erstellen? Weitere Informationen finden Sie hier: [Erstellen und Verwalten von Verteilergruppen](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Konfiguration der E-Mail-Weiterleitung zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken oder tippen Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie die E-Mail-Weiterleitung konfiguriert haben, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken oder tippen Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken oder tippen Sie unter **Nachrichtenfluss** auf **Details anzeigen**, um die E-Mail-Weiterleitungseinstellungen anzuzeigen.

## Weitere Informationen

Dieses Thema ist für Administratoren bestimmt. Wenn Sie eigene E-Mail-Nachrichten an einen anderen Empfänger weiterleiten möchten, lesen Sie die folgenden Themen:

  - [Weiterleiten von E-Mails an ein anderes E-Mail-Konto](https://go.microsoft.com/fwlink/p/?linkid=510866)

  - [Verwalten von E-Mails mithilfe von Regeln](https://go.microsoft.com/fwlink/p/?linkid=510869)

Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

