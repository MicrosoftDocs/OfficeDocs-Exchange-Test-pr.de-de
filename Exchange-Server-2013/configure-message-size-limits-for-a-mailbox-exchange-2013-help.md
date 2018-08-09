---
title: 'Konfig. von Beschr. der Nachrichtengröße für Postfach: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von Beschränkungen der Nachrichtengröße für ein Postfach
ms:assetid: d1220685-14c0-4c4f-abb2-3920f3046212
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124708(v=EXCHG.150)
ms:contentKeyID: 50554913
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Beschränkungen der Nachrichtengröße für ein Postfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-12_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell für ein Benutzerpostfach Größenlimits für Nachrichten festlegen. Mithilfe dieser Limits wird die Größe von Nachrichten bestimmt, die ein Benutzer senden und empfangen darf. Wenn ein Postfach erstellt wird, gilt standardmäßig keine Größenbeschränkung für gesendete und empfangene Nachrichten.

Beachten Sie, dass es in einer Exchange-Organisation andere Einstellungen gibt, welche die maximale Größe von Nachrichten bestimmen, die ein Postfach senden und empfangen kann (z. B. die auf einem Postfachserver konfigurierte maximale Nachrichtengröße). Weitere Informationen zu Einschränkungen der Nachrichtengröße in Exchange, einschließlich der Typen von Größenlimits von Nachrichten, Geltungsbereich und Prioritätsreihenfolge, finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Benutzerpostfächer finden Sie unter [Verwalten von Benutzerpostfächern](manage-user-mailboxes-exchange-2013-help.md).


> [!NOTE]
> Sie können auch die Größe von Nachrichten bestimmen, die von E-Mail-Benutzern und freigegebenen Postfächern gesendet und empfangen werden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Größenlimits für Nachrichten mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Größenlimits für Nachrichten Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken Sie unter **Größeneinschränkungen für Nachrichten** auf **Details anzeigen**, um die folgenden Größenlimits für Nachrichten anzuzeigen und zu ändern:
    
      - **Gesendete Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer gesendete Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht sendet, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Benutzer zurückgesendet.
    
      - **Empfangene Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer empfangene Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht empfängt, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Absender zurückgesendet.

5.  Klicken Sie auf **OK** und dann auf **Speichern**, um die Änderungen zu speichern.

## Konfigurieren von Beschränkungen der Nachrichtengröße mithilfe der Shell

Bei diesem Beispiel wird für das Postfach von Debra Garcia die maximale Größe gesendeter Nachricht auf 25 MB und empfangener Nachrichten auf 35 MB festgelegt.

    Set-Mailbox "Debra Garcia" -MaxSendSize 25mb -MaxReceiveSize 35mb

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Konfiguration von Beschränkungen der Nachrichtengröße für ein Postfach zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Größenlimits für Nachrichten Sie überprüfen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken Sie unter **Größeneinschränkungen für Nachrichten** auf **Details anzeigen**, um die Größenlimits für Nachrichten zu überprüfen.

– oder –

Führen Sie folgenden Befehl in der Shell aus.

    Get-Mailbox <identity> | fl MaxSendSize,MaxReceiveSize

