---
title: 'Aktiv. o. Deakt. von Outlook Web App für Postfach: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren von Outlook Web App für ein Postfach
ms:assetid: abc19646-6211-4f18-a060-e347452dcc53
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124124(v=EXCHG.150)
ms:contentKeyID: 50554892
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von Outlook Web App für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell Outlook Web App für ein Benutzerpostfach aktivieren oder deaktivieren. Sofern Outlook Web App aktiviert ist, kann ein Benutzer über Outlook Web App E-Mail senden und empfangen. Wenn Outlook Web App deaktiviert ist, empfängt das Postfach weiter E-Mail-Nachrichten. Ein Benutzer hat Zugriff darauf, um E-Mail mithilfe eines MAPI-Clients wie Microsoft Outlook oder eines POP- oder IMAP-E-Mail-Clients zu senden und zu empfangen. Voraussetzung ist, dass das Postfach für den Zugriff durch diese Clients aktiviert ist.


> [!NOTE]
> Unterstützung für Outlook Web App sowie MAPI-, POP3- und IMAP4-E-Mail-Clients ist standardmäßig aktiviert, wenn ein Benutzerpostfach erstellt wird.



Informationen zu weiteren Verwaltungsaufgaben in Bezug die Verwaltung des E-Mail-Clientzugriffs auf ein Postfach finden Sie in den folgenden Themen:

  - [Aktivieren oder Deaktivieren von MAPI für ein Postfach](https://technet.microsoft.com/de-de/library/Bb124497(v=EXCHG.150))

  - [Aktivieren oder Deaktivieren des IMAP4-Zugriffs für einen Benutzer](enable-or-disable-imap4-access-for-a-user-exchange-2013-help.md)

  - [Aktivieren oder Deaktivieren des POP3-Zugriffs für einen Benutzer](enable-or-disable-pop3-access-for-a-user-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benutzereinstellungen für den Clientzugriff" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren von Outlook Web App mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie Outlook Web App aktivieren oder deaktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Führen Sie unter **E-Mail-Konnektivität** einen der folgenden Schritte aus:
    
      - Klicken Sie zum Deaktivieren von Outlook Web App unter **Outlook Web App: Aktiviert** auf **Deaktivieren**.
        
        Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie Outlook Web App wirklich deaktivieren möchten. Klicken Sie auf **Ja**.
    
      - Klicken Sie zum Aktivieren von Outlook Web App unter **Outlook Web App: Deaktiviert** auf **Aktivieren**.

5.  Klicken Sie auf **Speichern**, um die Änderung zu speichern.


> [!NOTE]
> Sie können Outlook Web App für mehrere Benutzerpostfächer mithilfe der Massenbearbeitungsfunktion der Exchange-Verwaltungskonsole aktivieren oder deaktivieren. Weitere Informationen finden Sie im Abschnitt "Massenbearbeitung von Benutzerpostfächern" unter <A href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes">Verwalten von Benutzerpostfächern</A>.



## Aktivieren oder Deaktivieren von Outlook Web App mithilfe der Shell

In diesem Beispiel wird Outlook Web App für das Postfach von Yan Li deaktiviert.

    Set-CASMailbox -Identity "Yan Li" -OWAEnabled $false

In diesem Beispiel wird Outlook Web App für das Postfach von Elly Nkya aktiviert.

    Set-CASMailbox -Identity Ellyn@contoso.com -OWAEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Aktivierung bzw. Deaktivierung von Outlook Web App für ein Benutzerpostfach zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Klicken Sie auf das Postfach und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

  - Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

  - Überprüfen Sie unter **E-Mail-Konnektivität**, ob Outlook Web App aktiviert oder deaktiviert ist.

– oder –

  - Führen Sie folgenden Befehl in der Shell aus.
    
        Get-CASMailbox <identity>
    
    Ist Outlook Web App aktiviert, lautet der Wert der *OWAEnabled*-Eigenschaft `True`. Ist Outlook Web App deaktiviert, lautet der Wert `False`.

