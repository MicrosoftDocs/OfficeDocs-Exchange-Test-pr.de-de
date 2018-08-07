---
title: 'Anzeigen oder Konfig. d. Eigensch. von Outlook Web App-Postfachrichtlinien'
TOCTitle: Anzeigen oder Konfigurieren der Eigenschaften von Outlook Web App-Postfachrichtlinien
ms:assetid: be012ffe-8fdb-4fb7-aebd-78b3a55593fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351097(v=EXCHG.150)
ms:contentKeyID: 50476598
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen oder Konfigurieren der Eigenschaften von Outlook Web App-Postfachrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-04-13_

Nach Erstellen einer Outlook Web App-Postfachrichtlinie können Sie verschiedene Optionen konfigurieren, um die Funktionen zu steuern, die Benutzern in Outlook Web App zur Verfügung stehen sollen. Sie können beispielsweise Posteingangsregeln aktivieren oder deaktivieren oder eine Liste mit zulässigen Dateitypen für Anlagen erstellen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Web App-Postfachrichtlinien" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen oder Konfigurieren von Outlook Web App-Postfachrichtlinien mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**.

2.  Klicken Sie im Ergebnisbereich auf die Postfachrichtlinie, die Sie anzeigen oder konfigurieren möchten.

3.  Klicken Sie auf die Schaltfläche **Bearbeiten**.

4.  Auf der Registerkarte **Allgemein** können Sie den Namen der Richtlinie anzeigen und ändern.

5.  Verwenden Sie die Kontrollkästchen auf der Registerkarte **Features**, um Features zu aktivieren oder zu deaktivieren. Standardmäßig werden die gängigsten Funktionen angezeigt. Klicken Sie auf **Weitere Optionen**, um alle Funktionen anzuzeigen, die aktiviert oder deaktiviert werden können.
    

    > [!NOTE]
    > Einstellungen für Outlook Web App-Postfachrichtlinien haben Vorrang vor Einstellungen für virtuelle Outlook Web App-Verzeichnisse. Sie können Segmentierungseinstellungen für einzelne Benutzer mithilfe des Cmdlets <STRONG>Set-CASMailbox</STRONG> in der Shell ändern.



6.  Verwenden Sie die Kontrollkästchen **Direkter Dateizugriff** auf der Registerkarte **Dateizugriff**, um die Optionen für den Zugriff und die Anzeige von Dateien für die Benutzer zu konfigurieren. Mit der Dateizugriffsoption kann ein Benutzer alle an eine E-Mail-Nachricht angehängten Dateien öffnen oder anzeigen.
    
    Der Dateizugriff kann basierend darauf gesteuert werden, ob sich ein Benutzer bei einem öffentlichen oder privaten Computer angemeldet hat. Die Benutzeroption zur Auswahl des privaten oder öffentlichen Computerzugriffs steht nur zur Verfügung, wenn Sie mit der formularbasierten Authentifizierung arbeiten. Bei allen weiteren Formen der Authentifizierung wird von einem Zugriff auf einen privaten Computer ausgegangen.

7.  Verwenden Sie auf der Registerkarte **Offlinezugriff** die Optionsfelder, um die Verfügbarkeit des Offlinezugriffs zu konfigurieren.

8.  Klicken Sie auf **Speichern**, um die Richtlinie zu aktualisieren.

## Anzeigen und Konfigurieren von Outlook Web App-Postfachrichtlinien mithilfe der Shell

In diesem Beispiel wird der Kalenderzugriff in der Standardpostfachrichtlinie geändert.

    Set-OwaMailboxPolicy -Identity Default -CalendarEnabled $true

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-OwaMailboxPolicy](https://technet.microsoft.com/de-de/library/dd297989\(v=exchg.150\)).

## Anzeigen von Outlook Web App-Postfachrichtlinien mithilfe der Shell

In diesem Beispiel werden die Eigenschaften der Outlook Web App-Postfachrichtlinie `Executives` in der Organisation `Fabrikam` abgerufen.

    Get-OwaMailboxPolicy -Identity Fabrikam\Executives

Weitere Informationen zu Syntax und Parametern finden Sie unter [Get-OwaMailboxPolicy](https://technet.microsoft.com/de-de/library/dd351095\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass Sie eine Outlook Web App-Postfachrichtlinie erfolgreich bearbeitet haben:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**, und wählen Sie dann eine bestimmte Outlook Web App-Postfachrichtlinie aus.

2.  Klicken Sie auf die Schaltfläche **Bearbeiten**, um die Eigenschaften der Postfachrichtlinie anzuzeigen.

3.  Klicken Sie auf **Speichern** oder **Abbrechen**, um die Eigenschaftenseite zu schließen.

