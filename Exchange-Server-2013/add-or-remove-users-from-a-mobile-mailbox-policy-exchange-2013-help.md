---
title: 'Hinzufügen oder Entfernen von Benutzern zu bzw. aus einer Postfachrichtlinie für mobile Geräte: Exchange 2013 Help'
TOCTitle: Hinzufügen oder Entfernen von Benutzern zu bzw. aus einer Postfachrichtlinie für mobile Geräte
ms:assetid: 4ca8e395-c074-4165-b788-16fae3e2ccab
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997929(v=EXCHG.150)
ms:contentKeyID: 50475596
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen oder Entfernen von Benutzern zu bzw. aus einer Postfachrichtlinie für mobile Geräte

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-16_

Mit einer Postfachrichtlinie für mobile Geräte können Sie allgemeine Sicherheitseinstellungen und Einstellungen für mobile Geräte auf eine Gruppe von Benutzern anwenden. Sie können mehrere Postfachrichtlinien für mobile Geräte erstellen.


> [!WARNING]
> Wenn Sie Microsoft Exchange Server&nbsp;2013 installieren, wird eine standardmäßige Postfachrichtlinie für mobile Geräte erstellt, und alle Benutzer werden automatisch dieser Richtlinie zugewiesen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Postfachrichtlinien für mobile Geräte finden Sie unter [Postfachrichtlinien für mobile Geräte](mobile-device-mailbox-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachrichtlinien für mobile Geräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Im Abschnitt **Mobil** \> **Postfachrichtlinien für mobile Geräte** in der Exchange-Verwaltungskonsole muss eine Postfachrichtlinie für mobile Geräte verfügbar sein.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern einer Postfachrichtlinie für mobile Geräte für einen Benutzer

Sie können mithilfe der Exchange-Verwaltungskonsole oder der Shell die Postfachrichtlinie für mobile Geräte für einen Benutzer ändern.

## Ändern der Postfachrichtlinie für mobile Geräte für einen Benutzer mithilfe der Exchange-Verwaltungskonsole

Sie ändern die Postfachrichtlinie für mobile Geräte für einen einzelnen Benutzer mithilfe der Exchange-Verwaltungskonsole.

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Eigenschaften** \> **Postfächer**, und wählen Sie ein Postfach aus.

2.  Führen Sie im Detailbereich einen Bildlauf bis **Telefon- und Sprachfunktionen** durch, und wählen Sie **Details anzeigen**, um den Bildschirm **Details des mobilen Geräts** anzuzeigen.

3.  Die aktuell zugewiesene Postfachrichtlinie für mobile Geräte wird angezeigt. Klicken Sie auf **Durchsuchen**, um die Postfachrichtlinie für mobile Geräte zu ändern.

4.  Wählen Sie in der Liste die geeignete Postfachrichtlinie für mobile Geräte aus, klicken Sie auf **OK**, und klicken Sie dann auf **Speichern**.

## Hinzufügen eines Benutzers zu einer Postfachrichtlinie für mobile Geräte mithilfe der Shell

Sie können die Postfachrichtlinie für mobile Geräte für einen einzelnen Benutzer ändern, indem Sie das Cmdlet **Get-CASMailbox** in der Shell verwenden.

1.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-CASMailbox -Identity tony@contoso.com -ActiveSyncMailboxPolicy "Sales" 

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um zu überprüfen, ob Sie die Postfachrichtlinie für mobile Geräte eines Benutzers erfolgreich geändert haben:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**, und wählen Sie einen Empfänger aus. Führen Sie im Detailbereich einen Bildlauf bis **Telefon- und Sprachfunktionen** durch, und klicken Sie auf **Details anzeigen**.

2.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-CASMailbox -Identity tony@contoso.com 

## Ändern der Postfachrichtlinie für mobile Geräte für mehrere Benutzer in einem Arbeitsschritt

Wenn Sie die Postfachrichtlinie für mobile Geräte für mehrere Benutzer gleichzeitig ändern möchten, können Sie die Funktion zur Massenbearbeitung in der Exchange-Verwaltungskonsole verwenden oder die Postfachrichtlinie für mobile Geräte mithilfe der Shell für einen gefilterten Satz an Benutzern ändern.

## Ändern der Postfachrichtlinie für mobile Geräte für mehrere Benutzer mithilfe der Funktion zur Massenbearbeitung in der Exchange-Verwaltungskonsole

Sie können die Postfachrichtlinie für mobile Geräte für mehrere Benutzer gleichzeitig aktualisieren, indem Sie die Funktion zur Massenbearbeitung einsetzen.

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**.

2.  Wählen Sie mehrere Benutzer aus.

3.  Führen Sie im Detailbereich einen Bildlauf bis **Exchange ActiveSync** durch, und klicken Sie auf **Richtlinie aktualisieren**.

4.  Klicken Sie auf **Durchsuchen**, um eine Postfachrichtlinie für mobile Geräte auszuwählen.

5.  Klicken Sie auf **OK** und anschließend auf **Speichern**.

## Ändern der Postfachrichtlinie für mobile Geräte für einen gefilterten Satz an Benutzern mithilfe der Shell

Sie können mithilfe der Shell die Postfachrichtlinie für mobile Geräte für einen gefilterten Satz an Benutzern ändern. Sie können Benutzer basierend auf einer Vielzahl von Attributen filtern.

1.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-Mailbox | where { $_.CustomAttribute1 -match "Manager"
         } | Set-CASMailbox -activesyncmailboxpolicy(Get-ActiveSyncMailboxPolicy "Contoso").Identity
    

    > [!NOTE]
    > Sie können jede beliebige Eigenschaft für das <STRONG>Get-Mailbox</STRONG>-Objekt durch <CODE>CustomAttribute1</CODE> ersetzen. Geben Sie Folgendes ein, um die vollständige Liste anzuzeigen: <CODE>Get-Mailbox username |fl</CODE>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um zu überprüfen, ob Sie die Postfachrichtlinie für mobile Geräte eines Benutzers erfolgreich geändert haben:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**, und wählen Sie einen Empfänger aus. Führen Sie im Detailbereich einen Bildlauf bis **Telefon- und Sprachfunktionen** durch, und klicken Sie auf **Details anzeigen**.

2.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-CASMailbox -Identity tony@contoso.com

