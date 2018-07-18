---
title: 'Anzeigen des Administratorüberwachungsprotokolls: Exchange Online Help'
TOCTitle: Anzeigen des Administratorüberwachungsprotokolls
ms:assetid: 5c62072a-556d-4fea-9973-d668c6b9fd57
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn342832(v=EXCHG.150)
ms:contentKeyID: 56269038
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen des Administratorüberwachungsprotokolls

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-05-03_

In Microsoft Exchange Online Protection (EOP), Microsoft Exchange Online und Microsoft Exchange 2013 können Sie im Exchange-Verwaltungskonsole (EAC) Einträge im *Administratorüberwachungsprotokoll* suchen und anzeigen. Im Administratorüberwachungsprotokoll werden bestimmte Aktionen aufgezeichnet, die basierend auf dem jeweiligen Exchange-Verwaltungsshell-Cmdlet von Administratoren und Benutzern mit Administratorrechten ausgeführt werden. In Einträgen im Administratorüberwachungsprotokoll finden Sie Informationen dazu, welches Cmdlet ausgeführt wurde, welche Parameter verwendet wurden, wer das Cmdlet ausgeführt hat und welche Objekte betroffen sind.


> [!NOTE]
> <UL>
> <LI>
> <P>Die Administratorüberwachungsprotokollierung ist standardmäßig aktiviert.</P>
> <LI>
> <P>Im Administratorüberwachungsprotokoll werden keine Aktionen aufgezeichnet, die auf einem Exchange-Verwaltungsshell-Cmdlet basieren, das mit dem Verb <STRONG>Get</STRONG>, <STRONG>Search</STRONG> oder <STRONG>Test</STRONG> beginnt.</P>
> <LI>
> <P>Die Überwachungsprotokolleinträge werden 90&nbsp;Tage lang aufbewahrt. Wenn ein Eintrag älter als 90 Tage ist, wird er gelöscht.</P></LI></UL>



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berichte anzeigen" im Thema [Feature permissions in EOP](https://technet.microsoft.com/de-de/library/jj723125\(v=exchg.150\)).

  - Wie bereits erwähnt, ist die Administratorüberwachungsprotokollierung standardmäßig aktiviert. Führen Sie zur Sicherstellung, dass die Administratorüberwachungsprotokollierung aktiviert wurde, folgenden Befehl aus:
    
        Get-AdminAuditLogConfig | FL AdminAuditLogEnabled
    
    In Exchange 2013 können Sie die Administratorüberwachungsprotokollierung aktivieren, wenn sie deaktiviert ist, indem Sie den folgenden Befehl ausführen.
    
        Set-AdminAuditLogConfig -AdminAuditLogEnabled $True
    
    In Exchange Online Protection und Exchange Online ist die Administratorüberwachungsprotokollierung immer aktiviert und kann nicht deaktiviert werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Anzeigen des Administratorüberwachungsprotokolls mithilfe der Exchange-Verwaltungskonsole

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Verwaltung der Compliance** \> **Überwachung** aus, und klicken Sie anschließend auf **Administratorüberwachungsprotokoll-Bericht ausführen**.

2.  Legen Sie **Startdatum** und **Enddatum** fest, und klicken Sie dann auf **Suchen**. Sämtliche Konfigurationsänderungen, die im angegebenen Zeitraum erfolgt sind, werden angezeigt und können anhand der folgenden Informationen sortiert werden:
    
      - **Datum**   Datum und Uhrzeit der Konfigurationsänderung. Datum und Uhrzeit werden im UTC-Format (Coordinated Universal Time, koordinierte Weltzeit) gespeichert.
    
      - **Cmdlet**   Name des Cmdlets, mit dem die Konfigurationsänderung erfolgt ist.
    
      - **Benutzer**   Name des Benutzerkontos des Benutzers, der die Konfigurationsänderung vorgenommen hat.
    
    Es können bis zu 5000 Einträge auf mehreren Seiten angezeigt werden. Geben Sie einen kürzeren Datumsbereich ein, wenn Sie Ihre Ergebnisse eingrenzen möchten. Wenn Sie ein einzelnes Suchergebnis auswählen, werden im Detailbereich die folgenden weiteren Informationen angezeigt:
    
      - **Geändertes Objekt**   Der Name des Objekts, das vom Cmdlet geändert wurde.
    
      - **Parameter (Parameter:Wert)**   Die verwendeten Cmdlet-Parameter und mit dem Parameter angegebener beliebiger Wert.

3.  Wenn Sie einen bestimmten Überwachungsprotokolleintrag drucken möchten, klicken Sie im Detailbereich auf die Schaltfläche **Drucken**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie einen Administrator-Überwachungsprotokollbericht erfolgreich ausgeführt haben, werden im angegebenen Datumsbereich erfolgte Konfigurationsänderungen im Suchergebnisbereich angezeigt. Wenn keine Ergebnisse vorhanden sind, ändern Sie den Datumsbereich, und führen Sie den Bericht erneut aus.


> [!NOTE]
> Wenn eine Änderung in Ihrer Organisation erfolgt, kann es bis zu 15&nbsp;Minuten dauern, bis diese in den Suchergebnissen des Überwachungsprotokolls angezeigt wird. Wenn eine Änderung nicht im Administratorüberwachungsprotokoll aufgeführt wird, warten Sie einige Minuten, und führen Sie dann die Suche erneut aus.


