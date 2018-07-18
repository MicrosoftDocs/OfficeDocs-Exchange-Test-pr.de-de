---
title: 'Ausführen einer Remotezurücksetzung auf einem Mobiltelefon: Exchange 2013 Help'
TOCTitle: Ausführen einer Remotezurücksetzung auf einem Mobiltelefon
ms:assetid: 67ba838e-031d-4a98-b277-170683b6f520
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998614(v=EXCHG.150)
ms:contentKeyID: 52062717
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ausführen einer Remotezurücksetzung auf einem Mobiltelefon

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-06_

Ihre Benutzer tragen vertrauliche Unternehmensinformationen jeden Tag mit sich herum. Wenn einer von ihnen sein Mobiltelefon verliert, können Ihre Daten in die Hände einer anderen Person gelangen. Sollte einer Ihrer Benutzer sein Mobiltelefon verlieren, können Sie mithilfe der Exchange-Verwaltungskonsole oder Exchange-Verwaltungsshell sämtliche Unternehmens- und Benutzerdaten vom Mobiltelefon löschen, was als Zurücksetzen bezeichnet wird.


> [!NOTE]
> Außerdem erfahren Sie in diesem Thema, wie Sie eine Remotezurücksetzung eines Mobiltelefons mit MicrosoftOutlook Web App&nbsp;ausführen können. Der Benutzer muss bei Outlook Web App angemeldet sein, um eine Remotezurücksetzung ausführen zu können.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Mobilgeräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Bei diesem Verfahren werden alle Daten auf dem Mobiltelefon einschließlich installierter Anwendungen, Fotos und persönlicher Daten gelöscht.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zurücksetzen des Telefons eines Benutzers über das Exchange Admin Center

Sie können über das EAC das Telefon eines Benutzers zurücksetzen oder eine noch nicht abgeschlossene Remotezurücksetzung abbrechen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie den Benutzer und unter **Mobilgeräte** den Befehl **Details anzeigen** aus.

3.  Wählen Sie auf der Seite **Details des mobilen Geräts** das verloren gegangene Mobilgerät aus, und klicken Sie auf **Daten zurücksetzen**.

4.  Klicken Sie auf **Speichern**.

## Zurücksetzen des Telefons eines Benutzers über die Shell

Verwenden Sie zum Zurücksetzen des Telefons eines Benutzers über die Shell das Cmdlet **Clear-MobileDevice**.

Über den folgenden Befehl wird das Gerät mit der Bezeichnung "WM\_TonySmith" zurückgesetzt und eine Bestätigungsnachricht an "admin@contoso.com" gesendet.

    Clear-MobileDevice -Identity WM_TonySmith -NotificationEmailAddresses "admin@contoso.com"

## Zurücksetzen des Telefons eines Benutzers über Outlook Web App

Die Benutzer können ihre eigenen Telefone mit Outlook Web App zurücksetzen.

1.  Klicken Sie in Outlook Web App auf **Einstellungen \> Telefon \> Mobile Geräte**.

2.  Wählen Sie das Mobiltelefon aus.

3.  Klicken oder tippen Sie auf das Symbol **Gerät zurücksetzen**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Es gibt mehrere Möglichkeiten zum Überprüfen, ob das Remotezurücksetzen erfolgt ist.

  - Führen Sie das Cmdlet **Clear-MobileDevice** mit dem Parameter *–NotificationEmailAddresses* aus. Nach Abschluss des Remotezurücksetzens wird eine Nachricht an die angegebene E-Mail-Adresse gesendet.

  - Überprüfen Sie in der Exchange-Verwaltungskonsole den Status des mobilen Geräts. Der Status ändert sich von **Zurücksetzen steht aus** in **Remotegerätezurücksetzung war erfolgreich**.

  - Überprüfen Sie in Outlook Web App den Status des mobilen Geräts. Der Status ändert sich von **Zurücksetzen steht aus** in **Remotegerätezurücksetzung war erfolgreich**.

