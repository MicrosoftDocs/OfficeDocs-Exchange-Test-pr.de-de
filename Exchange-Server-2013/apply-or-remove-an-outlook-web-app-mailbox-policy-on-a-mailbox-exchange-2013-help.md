---
title: 'Anwenden oder Entfernen einer Outlook Web App-Postfachrichtlinie auf ein Postfach bzw. von einem Postfach: Exchange 2013 Help'
TOCTitle: Anwenden oder Entfernen einer Outlook Web App-Postfachrichtlinie auf ein Postfach bzw. von einem Postfach
ms:assetid: 51d8e269-b0d5-4bc7-9b3d-0460871e54fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876884(v=EXCHG.150)
ms:contentKeyID: 50475649
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anwenden oder Entfernen einer Outlook Web App-Postfachrichtlinie auf ein Postfach bzw. von einem Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

Mithilfe der Exchange-Verwaltungskonsole oder der Shell können Sie eine Outlook Web App-Postfachrichtlinie auf Postfächer anwenden oder von diesen entfernen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Web App-Postfachrichtlinien" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anwenden einer Outlook Web App-Postfachrichtlinie

## Anwenden einer Outlook Web App-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**.

2.  Wählen Sie im Arbeitsbereich per Mausklick das Postfach aus, auf das Sie eine Outlook Web App-Postfachrichtlinie anwenden möchten. Sie können auch mehrere Postfächer auswählen.

3.  **Wenn Sie ein Postfach ausgewählt haben:** 
    
    1.  Führen Sie einen Bildlauf bis **E-Mail-Konnektivität** durch, und klicken Sie auf **Details anzeigen**.
    
    2.  Klicken Sie auf **Durchsuchen**, um die verfügbaren Postfachrichtlinien anzuzeigen und eine auszuwählen.
    
    3.  Klicken Sie auf **Speichern**, um die ausgewählte Richtlinie dem ausgewählten Postfach zuzuweisen.
    
    **Wenn Sie mehr als ein Postfach ausgewählt haben:** 
    
    1.  Führen Sie im Detailbereich einen Bildlauf bis **Outlook Web App** durch, und klicken Sie auf **Richtlinie zuweisen**.
    
    2.  Klicken Sie auf **Durchsuchen**, um die verfügbaren Postfachrichtlinien anzuzeigen und eine auszuwählen.
    
    3.  Klicken Sie auf **Speichern**, um die ausgewählte Richtlinine den ausgewählten Postfächern zuzuweisen.

## Verwenden der Shell zum Anwenden einer Outlook Web App-Postfachrichtlinie auf ein vorhandenes Postfach

In diesem Beispiel wird die Outlook Web App-Postfachrichtlinie "Calendar" auf das Postfach des Benutzers "thorsten@contoso.com" angewendet.

    Set-CASMailbox -Identity tony@contoso.com -OwaMailboxPolicy:Calendar

Weitere Informationen zur Syntax und zu den Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Entfernen einer Outlook Web App-Postfachrichtlinie

## Entfernen einer Outlook Web App-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**.

2.  Wählen Sie im Arbeitsbereich per Mausklick das Postfach aus, für das Sie eine Outlook Web App-Postfachrichtlinie entfernen möchten.

3.  Führen Sie einen Bildlauf bis **E-Mail-Konnektivität** durch, und klicken Sie auf **Details anzeigen**.
    
    Wenn eine Postfachrichtlinie zugewiesen wurde, klicken Sie auf **Löschen**, um sie aus dem Postfach zu entfernen.

4.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Verwenden der Shell zum Entfernen einer Outlook Web App-Postfachrichtlinie von einem vorhandenen Postfach.

In diesem Beispiel wird die Outlook Web App-Postfachrichtlinie vom Postfach des Benutzers "thorsten@contoso.com" entfernt.

    Set-CASMailbox -Identity tony@contoso.com -OwaMailboxPolicy:$null

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

