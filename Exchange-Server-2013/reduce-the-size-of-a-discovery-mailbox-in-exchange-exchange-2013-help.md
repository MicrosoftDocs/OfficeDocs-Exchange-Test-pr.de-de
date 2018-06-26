---
title: 'Verkleinern eines Discoverypostfachs in Exchange: Exchange 2013 Help'
TOCTitle: Verkleinern eines Discoverypostfachs in Exchange
ms:assetid: fa762d14-f942-4728-8813-887d11441a68
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn750895(v=EXCHG.150)
ms:contentKeyID: 62371360
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verkleinern eines Discoverypostfachs in Exchange

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Haben Sie ein Discoverypostfach, das die Größenbeschränkung von 50 GB überschritten hat? Sie können dieses Problem beheben, indem Sie neue Discoverypostfächer erstellen und die Suchergebnisse aus dem großen Discoverypostfach in die neuen Postfächer kopieren.

## Aus welchen Gründen kann dies erforderlich sein?

In Exchange Server 2013 und Exchange Online beträgt die maximale Größe für Discoverypostfächer, die zum Speichern von Compliance-eDiscovery-Suchergebnissen verwendet werden, 50 GB. Vor der aktuellen Größenbeschränkung konnten Sie das Speicherkontingent auf mehr als 50 GB erhöhen und hatten dann Discoverypostfächer, die wesentlich größer als 50 GB waren. Über 50 GB große Discoverypostfächer bringen die folgenden drei Probleme mit sich:

  - Sie werden nicht unterstützt.

  - Sie können nicht zu Office 365 migriert werden.

  - Wenn es sich um Discoverypostfächer in Exchange Server 2010 handelt, kann kein Upgrade auf Exchange Server 2013 durchgeführt werden.

## Der Prozess auf einen Blick

Hier ist eine kurze Übersicht über die erforderlichen Schritte für das Verkleinern eines Discoverypostfachs, das die Größenbeschränkung von 50 GB überschritten hat:

1.  Schritt 1: Erstellen von Discoverypostfächern zusätzliche Discoverypostfächer, um die Suchergebnisse an diese zu verteilen.

2.  Schritt 2: Kopieren der Suchergebnisse an ein Discoverypostfach die Suchergebnisse vom vorhandenen Discoverypostfach zu einem oder mehreren der neuen Discoverypostfächer.

3.  Schritt 3: Löschen von eDiscovery-Suchen eDiscovery-Suchen aus dem ursprünglichen Discoverypostfach, um es zu verkleinern.

Mit der hier dargestellten Strategie werden die Suchergebnisse aus dem ursprünglichen Discoverypostfach in separate eDiscovery-Suchvorgänge gruppiert, die auf Datumsbereichen basieren. Auf diese Weise können Sie schnell viele Suchergebnisse in ein neues Discoverypostfach kopieren. Die folgende Grafik veranschaulicht diesen Ansatz.

![Verkleinern eines Discoverypostfachs](images/Dn750895.4400df18-c7ed-4c62-b304-f9060ffbdba5(EXCHG.150).gif "Verkleinern eines Discoverypostfachs")

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: Die benötigte Zeit ist je nach Anzahl und Größe der Suchergebnisse, die an verschiedene Discoverypostfächer kopiert werden, unterschiedlich.

  - Führen Sie den folgenden Befehl aus, um die Größe der Discoverypostfächer in Ihrer Organisation festzulegen.
    
        Get-Mailbox -RecipientTypeDetails DiscoveryMailbox | Get-MailboxStatistics | FL DisplayName,TotalItemSize

  - Legen Sie fest, ob Sie einige oder alle Suchergebnisse aus dem Discoverypostfach behalten müssen, das die Größenbeschränkung von 50 GB überschritten hat. Befolgen Sie die Schritte in diesem Thema, um Suchergebnisse beizubehalten, indem Sie sie an ein anderes Discoverypostfach kopieren. Wenn Sie die Ergebnisse einer bestimmten eDiscovery-Suche nicht beibehalten müssen, können Sie die Suche löschen, wie in Schritt 3 erklärt. Durch das Löschen einer Suche werden die Suchergebnisse aus dem Discoverypostfach gelöscht.

  - Wenn Sie keine der Suchergebnisse aus einem Discoverypostfach benötigen, das die Größenbeschränkung von 50 GB überschritten hat, können Sie es löschen. Wenn es sich um das Standarddiscoverypostfach handelt, das bei der Bereitstellung Ihrer Exchange-Organisation erstellt wurde, können Sie das Postfach erneut erstellen. Weitere Informationen finden Sie unter [Löschen und Neuerstellen des Standarddiscoverypostfachs in Exchange](delete-and-re-create-the-default-discovery-mailbox-in-exchange-exchange-2013-help.md).

  - Bei aktuellen Rechtsstreitigkeiten sollten Sie die Ergebnisse ausgewählter eDiscovery-Suchvorgänge in PST-Dateien exportieren. Damit bleiben die Ergebnisse aus einer bestimmten Suche intakt. Zusätzlich zu den PST-Dateien mit den Suchergebnissen wird auch ein Suchergebnisprotokoll (im CSV-Dateiformat) exportiert, das einen Eintrag für jede in den Suchergebnissen zurückgegebene Nachricht enthält. Jeder Eintrag in dieser Datei identifiziert das Quellpostfach, in dem sich die Nachricht befindet. Weitere Informationen finden Sie unter [Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](export-ediscovery-search-results-to-a-pst-file-exchange-2013-help.md).
    
    Nachdem Sie die Suchergebnisse in PST-Dateien exportiert haben, müssen Sie Outlook verwenden, um sie bei Bedarf in ein neues Discoverypostfach zu importieren.

## Schritt 1: Erstellen von Discoverypostfächern

Der erste Schritt besteht darin, zusätzliche Discoverypostfächer zu erstellen, damit Sie die Suchergebnisse aus dem Discoverypostfach kopieren können, das die Größenbeschränkung überschritten hat. Legen Sie basierend auf der Größenbeschränkung für Discoverypostfächer von 50 GB fest, wie viele zusätzliche Discoverypostfächer Sie benötigen, und installieren Sie diese. Dann müssen Sie Benutzern oder Gruppen die erforderlichen Berechtigungen zum Öffnen dieser neuen Discoverypostfächer zuweisen.

1.  Führen Sie den folgenden Befehl aus, um ein neues Discoverypostfach zu erstellen.
    
        New-Mailbox -Name <discovery mailbox name> -Discovery

2.  Führen Sie den folgenden Befehl aus, um einem Benutzer oder einer Gruppe Berechtigungen zum Öffnen des Discoverypostfachs und zum Anzeigen der Suchergebnisse zuzuweisen:
    
        Add-MailboxPermission <discovery mailbox name> -User <name of user or group> -AccessRights FullAccess -InheritanceType all

## Schritt 2: Kopieren der Suchergebnisse an ein Discoverypostfach

Der nächste Schritt besteht darin, die Suchergebnisse aus dem vorhandenen Discoverypostfach mit dem Cmdlet **New-MailboxSearch** an ein neues Discoverypostfach zu kopieren, das Sie im vorherigen Schritt erstellt haben. Bei diesem Verfahren werden die Parameter *StartDate* und *EndDate* verwendet, um die Suchergebnisse in Batches aufzuteilen, die nicht größer als 50 GB sind. Dafür sind möglicherweise einige Testläufe (durch Abschätzen der Suchergebnisse) erforderlich, um die Größe der Suchergebnisse entsprechend festzulegen.

1.  Führen Sie den folgenden Befehl aus, um eine neue eDiscovery-Suche zu erstellen.
    
        New-MailboxSearch -Name "Search results from 2010" -SourceMailboxes "Discovery Search Mailbox" -StartDate "01/01/2010" -EndDate "12/31/2010" -TargetMailbox "Discovery Mailbox Backup 01" -EstimateOnly -StatusMailRecipients admin@contoso.com
    
    In diesem Beispiel werden die folgenden Parameter verwendet:
    
      - *Name*   Mit diesem Parameter wird der Name der neuen eDiscovery-Suche angegeben. Da die Suche nach Sende- und Empfangsdatum eingeteilt wird, ist es sinnvoll, den Datumsbereich in den Namen der Suche einzuschließen.
    
      - *SourceMailboxes*   Mit diesem Parameter wird das Standarddiscoverypostfach angegeben. Sie können außerdem den Namen eines anderen Discoverypostfachs angeben, das die Größenbeschränkung überschritten hat.
    
      - *StartDate* und *EndDate*   Mit diesen Parametern wird der Datumsbereich der Suchergebnisse im Standarddiscoverypostfach zum Einschließen in die Suchergebnisse angegeben.
        

        > [!NOTE]
        > Verwenden Sie für das Datum selbst dann das kurze Datumsformat mm/tt/jjjj, wenn bei den regionalen Einstellungen auf dem lokalen Computer ein anderes Format konfiguriert ist, z.&nbsp;B. tt.mm.jjjj. Verwenden Sie beispielsweise <STRONG>03/01/2014</STRONG>, um den 1. März 2014 anzugeben.

    
      - *TargetMailbox*   Mit diesem Parameter wird angegeben, dass die Suchergebnisse in das Discoverypostfach mit dem Namen "Discovery Mailbox Backup 01" kopiert werden sollen.
    
      - *EstimateOnly*   Mit diesem Switch wird angegeben, dass nur eine Schätzung der zurückgegebenen Elemente bereitgestellt wird, wenn die Suche gestartet wird. Wenn Sie diesen Switch nicht einfügen, werden Nachrichten an das Zielpostfach kopiert, wenn die Suche gestartet wird. Mit diesem Switch können Sie die Datumsbereiche bei Bedarf anpassen, um die Anzahl der Suchergebnisse zu vergrößern oder zu verkleinern.
    
      - *StatusMailRecipients*   Mit diesem Parameter wird angegeben, dass die Statusmeldung an den angegebenen Empfänger gesendet werden sollte.

2.  Nachdem die Suche erstellt ist, starten Sie sie über die Shell oder das Exchange Admin Center (EAC).
    
      - **Verwenden der Shell:** Führen Sie den folgenden Befehl aus, um die im vorherigen Schritt erstellte Suche zu starten. Da der Switch *EstimateOnly* bei der Erstellung der Suche eingeschlossen wurde, werden die Suchergebnisse nicht an das Zieldiscoverypostfach kopiert.
        
            Start-MailboxSearch "Search results from 2010"
    
      - **Verwenden des EAC:** Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**. Wählen Sie die im vorherigen Schritt erstellte Suche aus, klicken Sie auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)"), und klicken Sie dann auf **Suchergebnisse schätzen**.

3.  Passen Sie bei Bedarf den Datumsbereich an, um die Menge der zurückgegebenen Suchergebnisse zu vergrößern oder zu verkleinern. Wenn Sie den Datumsbereich ändern, führen Sie die Suche erneut aus, um eine neue Schätzung der Ergebnisse zu erhalten. Ziehen Sie eine Änderung des Namens für die Suche in Betracht, um den neuen Datumsbereich darzustellen.

4.  Wenn Sie das Testen der Suche abgeschlossen haben, kopieren Sie die Suchergebnisse über die Shell oder das EAC an das Zieldiscoverypostfach.
    
      - **Verwenden der Shell:** Führen Sie die folgenden Befehle aus, um die Suchergebnisse zu kopieren. Sie müssen den Switch *EstimateOnly* entfernen, bevor Sie die Suchergebnisse kopieren können.
        
            Set-MailboxSearch "Search results from 2010" -EstimateOnly $false
        
            Start-MailboxSearch "Search results from 2010"
    
      - **Verwenden des EAC:** Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**. Wählen Sie die Suche aus, klicken Sie auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)"), und klicken Sie dann auf **Suchergebnisse kopieren**.
    
    Weitere Informationen finden Sie unter [Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach](copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md).

5.  Wiederholen Sie die Schritte 1 bis 4, um neue Suchen für weitere Datumsbereiche zu erstellen. Schließen Sie den Datumsbereich in den Namen der neuen Suchvorgänge ein, um den Bereich der Ergebnisse anzugeben. Verwenden Sie verschiedene Discoverypostfächer als Zielpostfach, um sicherzustellen, dass keins der Discoverypostfächer die Größenbeschränkung von 50 GB überschreitet.

## Schritt 3: Löschen von eDiscovery-Suchen

Nachdem Sie die Suchergebnisse aus dem ursprünglichen Discoverypostfach an ein anderes Discoverypostfach kopiert haben, können Sie die ursprünglichen eDiscovery-Suchen löschen. Durch das Löschen einer eDiscovery-Suche werden die Suchergebnisse aus dem Discoverypostfach gelöscht, in dem diese Suchergebnisse gespeichert werden.

Bevor Sie eine Suche löschen, können Sie den folgenden Befehl ausführen, um die Größe der Suchergebnisse, die an ein neues Discoverypostfach kopiert wurden, für alle Suchvorgänge in Ihrer Organisation zu ermitteln.

    Get-MailboxSearch | FL Name,TargetMailbox,ResultSizeCopied

Sie können zum Löschen einer eDiscovery-Suche die Shell oder das EAC verwenden.

  - **Verwenden der Shell:** Führen Sie den folgenden Befehl aus.
    
        Remove-MailboxSearch -Identity <name of search>

  - **Verwenden des EAC:** Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**. Wählen Sie die Suche aus, die Sie löschen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nachdem Sie die eDiscovery-Suchen gelöscht haben, um die Ergebnisse aus dem Discoverypostfach zu löschen, in dem sie gespeichert waren, führen Sie den folgenden Befehl aus, um die Größe eines ausgewählten Discoverypostfachs anzuzeigen.

    Get-Mailbox <name of discovery mailbox> | Get-MailboxStatistics | FL TotalItemSize

