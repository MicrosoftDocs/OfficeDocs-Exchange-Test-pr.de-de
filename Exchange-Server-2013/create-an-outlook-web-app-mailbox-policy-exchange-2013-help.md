---
title: 'Erstellen einer Outlook Web App-Postfachrichtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer Outlook Web App-Postfachrichtlinie
ms:assetid: 347207fa-cfb7-40a6-b19a-831dcdb54ad5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335191(v=EXCHG.150)
ms:contentKeyID: 50475444
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Outlook Web App-Postfachrichtlinie

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-05-30_

Sie können eine Outlook Web App-Postfachrichtlinie erstellen, um eine Reihe allgemeiner Richtlinieneinstellungen anzuwenden. Outlook Web App-Postfachrichtlinien sind beim Anwenden und Standardisieren von Einstellungen, z. B. Anlageneinstellungen, für bestimmte Benutzergruppen hilfreich.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie dieses Cmdlet ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. In diesem Thema sind zwar alle Parameter für das Cmdlet aufgeführt, aber Sie verfügen möglicherweise nicht über Zugriff auf einige Parameter, falls diese nicht in den Ihnen zugewiesenen Berechtigungen enthalten sind. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Web App-Postfachrichtlinien" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer Outlook Web App-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**.

2.  Klicken Sie auf die Schaltfläche **Neu**.

3.  
    
    Geben Sie einen Namen für die Richtlinie ein.

4.  
    
    Verwenden Sie die Kontrollkästchen, um Funktionen zu aktivieren oder zu deaktivieren. Standardmäßig werden die gängigsten Funktionen angezeigt. Klicken Sie auf **Weitere Optionen**, um alle Funktionen anzuzeigen, die aktiviert oder deaktiviert werden können.
    

    > [!NOTE]
    > Einstellungen für Outlook Web App-Postfachrichtlinien haben Vorrang vor Einstellungen für virtuelle Outlook Web App-Verzeichnisse. Sie können Segmentierungseinstellungen für einzelne Benutzer mithilfe des Cmdlets <STRONG>Set-CASMailbox</STRONG> in der Shell ändern.



5.  Klicken Sie auf **Speichern**, um die Richtlinie zu speichern.

## Erstellen einer Outlook Web App-Postfachrichtlinie mit der Verwaltungsshell

In diesem Beispiel wird eine Outlook Web App-Postfachrichtlinie namens `Policy1` erstellt.

  - Führen Sie in der Shell den folgenden Befehl aus.
    
        New-OwaMailboxPolicy -Name Policy1

Weitere Informationen zu Syntax und Parametern finden Sie unter [New-OwaMailboxPolicy](https://technet.microsoft.com/de-de/library/dd351067\(v=exchg.150\)). Informationen zur Verwendung der Shell zum Konfigurieren einer Outlook Web App-Postfachrichtlinie finden Sie unter [Set-OwaMailboxPolicy](https://technet.microsoft.com/de-de/library/dd297989\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

So stellen Sie sicher, dass Sie eine Outlook Web App-Postfachrichtlinie erfolgreich erstellt haben:

  - Klicken Sie in der Exchange-Verwaltungskonsole auf **Berechtigungen** \> **Outlook Web App-Richtlinien**, und suchen Sie nach der neuen Postfachrichtlinie.

