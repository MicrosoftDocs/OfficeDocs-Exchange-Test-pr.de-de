---
title: 'Aktiv. oder Deaktiv. v. Exchange ActiveSync für Postfach: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren von Exchange ActiveSync für ein Postfach
ms:assetid: dcf7c05b-b1b9-4b0f-800d-fec9f2ddc9e4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124809(v=EXCHG.150)
ms:contentKeyID: 50554926
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von Exchange ActiveSync für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-13_

Über die Exchange-Verwaltungskonsole oder Shell können Sie Microsoft Exchange ActiveSync für ein Benutzerpostfach aktivieren oder deaktivieren. Exchange ActiveSync ist ein Clientprotokoll, über das Benutzer ein Mobilgerät mit ihrem Exchange-Postfach synchronisieren können. Exchange ActiveSync wird standardmäßig aktiviert, wenn ein Benutzerpostfach erstellt wird. Weitere Informationen finden Sie unter [Exchange ActiveSync](exchange-activesync-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange Active Sync-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren oder Deaktivieren von Exchange ActiveSync

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie Exchange ActiveSync aktivieren oder deaktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Führen Sie unter **Mobilgeräte** einen der folgenden Schritte aus:
    
      - Klicken Sie zum Deaktivieren von Exchange ActiveSync auf **Exchange ActiveSync deaktivieren**.
        
        Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie Exchange ActiveSync wirklich deaktivieren möchten. Klicken Sie auf **Ja**.
    
      - Klicken Sie zum Aktivieren von Exchange ActiveSync auf **Exchange ActiveSync aktivieren**.

5.  Klicken Sie auf **Speichern**, um die Änderung zu speichern.


> [!NOTE]
> Sie können Exchange ActiveSync für mehrere Benutzerpostfächer mithilfe der Massenbearbeitungsfunktion der Exchange-Verwaltungskonsole aktivieren oder deaktivieren. Weitere Informationen finden Sie im Abschnitt "Massenbearbeitung von Benutzerpostfächern" unter <A href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes">Verwalten von Benutzerpostfächern</A>.



## Verwenden der Shell zum Aktivieren oder Deaktivieren von Exchange ActiveSync

In diesem Beispiel wird Exchange ActiveSync für das Postfach von Yan Li deaktiviert.

    Set-CASMailbox -Identity "Yan Li" -ActiveSyncEnabled $false

In diesem Beispiel wird Exchange ActiveSync für das Postfach von Elly Nkya aktiviert.

    Set-CASMailbox -Identity Ellyn@contoso.com -ActiveSyncEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Aktivierung bzw. Deaktivierung von Exchange ActiveSync für ein Benutzerpostfach zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Klicken Sie auf das Postfach und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

  - Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

  - Überprüfen Sie unter **Mobilgeräte**, ob Exchange ActiveSync aktiviert oder deaktiviert ist.

– oder –

  - Führen Sie folgenden Befehl in der Shell aus.
    
        Get-CASMailbox <identity>
    
    Ist Exchange ActiveSync aktiviert, lautet der Wert der *ActiveSyncEnabled*-Eigenschaft `True`. Ist Exchange ActiveSync deaktiviert, lautet der Wert `False`.

