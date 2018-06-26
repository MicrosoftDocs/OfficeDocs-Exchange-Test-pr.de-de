---
title: 'Erstellen einer Postfachüberwachungsprotokoll-Suche: Exchange 2013 Help'
TOCTitle: Erstellen einer Postfachüberwachungsprotokoll-Suche
ms:assetid: 48ba22cf-b1f2-4dbc-98fc-fed22d97db14
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff461929(v=EXCHG.150)
ms:contentKeyID: 50475560
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Postfachüberwachungsprotokoll-Suche

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-11_

Sie können eine Postfachüberwachungsprotokoll-Suche erstellen, um ein oder mehrere Postfächer asynchron zu durchsuchen und die Suchergebnisse als XML-Datei per E-Mail an angegebene Adressen zu senden.

Wenn Sie Postfachüberwachungsprotokolle für ein einzelnes Postfach durchsuchen und die Ergebnisse in der Shell anzeigen möchten, finden Sie weitere Informationen unter [Durchsuchen des Überwachungsprotokolls für ein Postfach](search-the-mailbox-audit-log-for-a-mailbox-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Postfachüberwachungsprotokollierung finden Sie unter [Verfahren der Postfachüberwachungsprotokollierung](mailbox-audit-logging-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Standardmäßig ist die Postfachüberwachungsprotokollierung für alle Postfächer deaktiviert. Sie müssen für jedes zu überwachende Postfach die Überwachungsprotokollierung aktivieren und die zu überwachenden Aktionen von Postfachbesitzern, Stellvertretungen oder Administratoren angeben. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach](enable-or-disable-mailbox-audit-logging-for-a-mailbox-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Durchsuchen von Postfachüberwachungsprotokollen nach Besitzerzugriffen verwendet werden. Der Überwachungsabschnitt in der Exchange-Verwaltungskonsole umfasst Berichte zu Nicht-Besitzer-Zugriffen und ermöglicht es außerdem, nach Nicht-Besitzer-Zugriffsereignissen zu suchen und diese zu exportieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Postfachüberwachungsprotokoll-Suche mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Überwachung**.

2.  Wählen Sie in der Listenansicht **Postfachüberwachungsprotokolle exportieren** aus.

3.  Füllen Sie im Bereich **Postfachüberwachungsprotokolle exportieren** die folgenden Felder aus, und klicken Sie dann auf **Exportieren**:
    
      - **Startdatum**
    
      - **Enddatum**
    
      - **Diese Postfächer durchsuchen oder Feld leerlassen, um alle Postfächer zu finden, auf die von Nicht-Besitzern zugegriffen wurde**
        

        > [!WARNING]
        > In Abhängigkeit von der Anzahl von Postfächern in Ihrer Organisation und der Menge an Postfachüberwachungsprotokoll-Daten in jedem Postfach kann die Suche in allen Postfächern sehr viel Zeit in Anspruch nehmen.

    
      - **Suchen nach Zugriff durch**
        
        Wählen Sie aus den folgenden Arten von Zugriffsereignissen aus, nach denen gesucht werden soll:
        
          - **Alle Nicht-Besitzer**
        
          - **Externe Benutzer**
        
          - **Administratoren und delegierte Benutzer**
        
          - **Administratoren**
    
      - **Überwachungsbericht senden an**

## Verwenden der Shell zum Erstellen einer Postfachüberwachungsprotokoll-Suche

Ein Beispiel zur Verwendung der Shell zum Erstellen einer Postfachüberwachungsprotokoll-Suche finden Sie im Abschnitt [Example 1](https://technet.microsoft.com/de-de/95365cab-bbb2-4a64-8e8f-1c89fa9e0352\(exchg.150\)#example1) in **New-MailboxAuditLogSearch**.

