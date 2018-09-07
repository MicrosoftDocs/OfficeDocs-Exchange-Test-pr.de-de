---
title: 'Erstellen einer Compliance-eDiscovery-Suche: Exchange 2013 Help'
TOCTitle: Erstellen einer Compliance-eDiscovery-Suche
ms:assetid: feedc0c9-4a44-4bb2-8520-cc29d66d4fc3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd353189(v=EXCHG.150)
ms:contentKeyID: 50477172
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Compliance-eDiscovery-Suche

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-01-17_


> [!NOTE]
> Wir haben den Stichtag (1. Juli 2017) für das Erstellen neuer In-Situ-eDiscovery-Suchen in Exchange Online (in Office 365 und eigenständigen Exchange Online-Plänen) verschoben. Im späteren Verlauf dieses Jahres oder Anfang des nächsten Jahres können Sie keine neuen Suchen mehr in Exchange Online erstellen. Um eDiscovery-Suchen zu erstellen, müssen Sie <A href="https://go.microsoft.com/fwlink/?linkid=847843">Inhaltssuche</A> im Office 365 Security &amp; Compliance Center verwenden. Nachdem die Erstellung neuer In-Situ-eDiscovery-Suchen eingestellt ist, können vorhandene In-Situ-eDiscovery-Suchen nach wie vor geändert werden, und das Erstellen neuer In-Situ-eDisvocery-Suchen in Exchange Server&nbsp;2013- und Exchange-Hybridbereitstellungen wird weiterhin unterstützt.



Mithilfe von [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md) können Sie den gesamten Postfachinhalt durchsuchen, einschließlich der gelöschten Objekte und der ursprünglichen Versionen geänderter Objekte für Benutzer, die im [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md) gespeichert sind.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Um eDiscovery-Suchen zu erstellen, benötigen Sie eine SMTP-Adresse in der Organisation, in der Sie die Suchen erstellen. In Exchange Online brauchen Sie also ein lizenziertes Exchange Online (Plan 2)-Postfach, um eDiscovery-Suchen zu erstellen. In einer Exchange-Hybridorganisation muss Ihr lokales Exchange-Postfach in Ihrer Office 365-Organisation ein entsprechendes E-Mail-Benutzerkonto aufweisen, damit Sie Exchange Online-Postfächer durchsuchen können. Wenn Sie sich mit einem Konto anmelden, das nur in Office 365 besteht, wie z. B. das Mandantenadministratorkonto, muss diesem Konto eine Exchange Online (Plan 2)-Lizenz zugewiesen werden.

  - Das Exchange 2013-Setup erstellt ein Discoverypostfach namens **Discoverysuchpostfach**, um Suchergebnisse zu kopieren. Das Postfach für die Discoverysuche wird standardmäßig in Exchange Online erstellt. Sie können zusätzliche Discoverypostfächer erstellen. Weitere Informationen finden Sie unter [Erstellen eines Discoverypostfachs](create-a-discovery-mailbox-exchange-2013-help.md).

  - Wenn Sie in eine Compliance-eDiscovery-Suche erstellen, werden die in den Suchergebnissen zurückgegebenen Ergebnisse nicht automatisch in ein Discoverypostfach kopiert. Nachdem Sie die Suche erstellt haben, können Sie die Suchergebnisse in der Exchange-Verwaltungskonsole schätzen, voranzeigen und in ein Discoverypostfach kopieren. Weitere Informationen finden Sie unter:
    
      - Estimate or preview search results(weiter unten in diesem Thema)
    
      - [Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach](copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen einer Compliance-eDiscovery-Suche mithilfe der Exchange-Verwaltungskonsole

Wie bereits erklärt, müssen Sie sich für das Erstellen einer eDiscovery-Suche bei einem Benutzerkonto anmelden, das in Ihrer Organisation über eine SMTP-Adresse verfügt.

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie auf der Seite **Name und Beschreibung** im **Compliance-eDiscovery und -Archiv**, einen Namen für die Suche ein, fügen Sie eine optionale Beschreibung hinzu, und klicken Sie dann auf **Weiter**.

4.  Wählen Sie auf der Seite **Postfächer** die zu durchsuchenden Postfächer aus. Sie können in alle Postfächern suchen oder bestimmte Postfächer auswählen, die durchsucht werden sollen. In Exchange Online können Sie auch Office 365-Gruppen als Inhaltsquelle für die Suche hinzufügen.
    

    > [!IMPORTANT]
    > Sie können die Option <STRONG>Alle Postfächer durchsuchen</STRONG> nicht verwenden, um alle Postfächer zu archivieren. Zum Erstellen eines Compliance-Archivs müssen Sie die Option <STRONG>Zu durchsuchende Postfächer angeben</STRONG> auswählen. Weitere Informationen finden Sie unter <A href="create-or-remove-an-in-place-hold-exchange-2013-help.md">Erstellen oder Entfernen eines Compliance-Archivs</A>.



5.  Füllen Sie auf der Seite **Suchabfrage** die folgenden Felder aus:
    
      - **Gesamten Postfachinhalt einschließen**   Wählen Sie diese Option, um den gesamten Inhalt der ausgewählten Postfächer in einem Archiv zu platzieren. Wenn Sie diese Option auswählen, können Sie keine weiteren Suchkriterien angeben.
    
      - **Anhand von Kriterien filtern**   Wählen Sie diese Option, um Suchkriterien wie zum Beispiel Stichwörter, Start- und Enddaten, Absender- und Empfängeradressen und Nachrichtentypen anzugeben.
        
        ![eDiscovery-Suchabfrage konfigurieren](images/Dd298021.a3626569-8700-421e-8b4e-7ec520b28272(EXCHG.150).png "eDiscovery-Suchabfrage konfigurieren")  
    

    > [!NOTE]
    > Die Felder <STRONG>Von:</STRONG> und <STRONG>An/Cc/Bcc:</STRONG> sind durch einen <STRONG>OR</STRONG>-Operator in der Suchabfrage verbunden, die beim Ausführen der Suche erstellt wird. Das bedeutet, dass eine Nachricht, die von einem der angegebenen Benutzer gesendet oder empfangen wird(und den anderen Suchkriterien entspricht), in den Suchergebnissen enthalten ist.<BR>Die Datumsangaben werden mit einem <STRONG>UND</STRONG>-Operator verbunden.



6.  Markieren Sie auf der Seite **Einstellungen für Compliance-Archiv** das Kontrollkästchen **Inhalt, der mit der Suchanfrage übereinstimmt, in ausgewählten Postfächern aufbewahren**, und wählen Sie dann eine der folgenden Optionen aus, um Objekte im Compliance-Archiv zu platzieren:
    
      - **Dauerhaft anhalten**   Wählen Sie diese Option, um die zurückgegebenen Elemente dauerhaft beizubehalten. Aufbewahrte Elemente werden solange beibehalten, bis Sie das Postfach aus der Suche entfernt oder die Suche entfernt haben.
    
      - **Anzahl von Tagen angeben, die Elemente in Relation zu ihrem Empfangsdatum in einem Archiv gespeichert werden sollen** Verwenden Sie diese Option, um Elemente für einen bestimmten Zeitraum beizubehalten. Diese Option können Sie beispielsweise verwenden, wenn es für Ihre Organisation erforderlich ist, dass alle Nachrichten mindestens sieben Jahre aufbewahrt werden. Sie können ein *zeitbasiertes* Compliance-Archiv zusammen mit einer Aufbewahrungsrichtlinie verwenden, damit sichergestellt ist, dass alle Elemente in sieben Jahren gelöscht werden.
        

        > [!IMPORTANT]
        > Wenn Postfächer oder Elemente aus rechtlichen Gründen in einem Compliance-Archiv platziert werden, empfiehlt es sich im Allgemeinen, die Elemente dauerhaft beizubehalten oder die Archivierung zu beenden, wenn der Fall oder die Untersuchung beendet ist.



7.  Klicken Sie auf **Fertig stellen**, um die Suche zu speichern und eine Schätzung der Gesamtgröße und -anzahl der Objekte anzuzeigen, die von der Suche auf der Grundlage der angegebenen Kriterien zurückgegeben werden. Schätzungen werden im Detailbereich angezeigt. Klicken Sie auf **Aktualisieren**![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)"), um die Informationen im Detailbereich zu aktualisieren.

Zurück zum Seitenanfang

## Erstellen einer Compliance-eDiscovery-Suche mithilfe der Shell

In diesem Beispiel wird die Compliance-eDiscovery-Suche mit dem Namen „Discovery-CaseId012“ nach Objekten mit den Schlüsselwörtern „Contoso“ und „ProjectA“ erstellt, die außerdem die folgenden Kriterien erfüllen:

  - Startdatum: 1/1/2009

  - Enddatum: 12/31/2011

  - Quellpostfach: DG-Finance

  - Zielpostfach: Discoverysuchpostfach

  - Nachrichtentypen: E-Mail

  - Einschließen von nicht durchsuchbaren Elementen in der Suchstatistik

  - Protokollstufe: Vollständig


> [!IMPORTANT]
> Wenn Sie für eine Compliance-eDiscovery-Suche keine zusätzlichen Parameter angeben, werden alle Objekte in den angegebenen Quellpostfächern in den Ergebnissen zurückgegeben. Wenn Sie nicht angeben, welche Postfächer durchsucht werden sollen, werden alle Postfächer auf den Exchange oder Exchange Online-Organisation durchsucht.



    New-MailboxSearch "Discovery-CaseId012" -StartDate "01/01/2009" -EndDate "12/31/2011" -SourceMailboxes "DG-Finance" -TargetMailbox "Discovery Search Mailbox" -SearchQuery '"Contoso" AND "Project A"' -MessageTypes Email -IncludeUnsearchableItems -LogLevel Full


> [!NOTE]
> Wenn Sie die Parameter <EM>StartDate</EM> und <EM>EndDate</EM> verwenden, müssen Sie das Datumsformat mm/tt/jjjj verwenden, selbst wenn Ihr PC für ein anderes Datumsformat, wie z. B. tt/mm/jjjj konfiguriert ist. Wenn Sie z. B. nach Nachrichten suchen, die zwischen dem 1. April 2013 und dem 1. Juli 2013 versandt wurden, geben Sie <STRONG>04/01/2013</STRONG> und <STRONG>07/01/2013</STRONG> als Start- und Enddatum ein.



In diesem Beispiel wird die Compliance-eDiscovery-Suche mit dem Namen „HRCase090116“ erstellt, die nach E-Mail-Nachrichten sucht, die von Alex Darrow and Sara Davis im Jahr 2015 gesendet wurden.

    New-MailboxSearch "HRCase090116" -StartDate "01/01/2015" -EndDate "12/31/2015" -SourceMailboxes  alexd,sarad -SearchQuery 'From:alexd@contoso.com AND To:sarad@contoso.com' -MessageTypes Email -TargetMailbox "Discovery Search Mailbox" -IncludeUnsearchableItems -LogLevel Full

Nachdem Sie mithilfe der Shell eine Compliance-eDiscovery-Suche erstellt haben, müssen Sie mithilfe des Cmdlets **Start-MailboxSearch** die Suche starten, um Nachrichten in das Discovery-Postfach zu kopieren, das im Parameter *TargetMailbox* angegeben ist. Weitere Informationen finden Sie unter [Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach](copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298064\(v=exchg.150\)).

Zurück zum Seitenanfang

## Verwenden des EAC zum Schätzen von Suchergebnissen oder zur Anzeige in einer Vorschau

Nach dem Erstellen einer Compliance-eDiscovery-Suche können Sie das EAC verwenden, um Suchergebnisse zu schätzen oder in einer Vorschau anzuzeigen. Wenn Sie mithilfe des Cmdlets **New-MailboxSearch** eine neue Suche erstellt haben, können Sie die Shell verwenden, um die Suche zu starten und eine Schätzung der Suchergebnisse zu erhalten. In Suchergebnissen zurückgegebene Nachrichten können nicht mithilfe der Shell vorangezeigt werden.

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-Discovery und -Archiv**.

2.  Wählen Sie in dieser Listenansicht die Compliance-eDiscovery-Suche aus, und führen Sie dann eine der folgenden Aktionen aus:
    
      - Kicken Sie auf **Suche**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") \> **Suchergebnisse schätzen**, um eine Schätzung der Gesamtgröße und -anzahl der Objekte, die von der Suche auf der Grundlage der angegebenen Kriterien zurückgegeben werden. Durch Auswahl dieser Option wird die Suche gestartet und eine Schätzung erstellt.
        
        Schätzungen der Suchergebnisse werden im Detailbereich angezeigt. Klicken Sie auf **Aktualisieren**![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)"), um die Informationen im Detailbereich zu aktualisieren.
    
      - Klicken Sie im Detailbereich auf **Vorschau auf Suchergebnisse anzeigen**, um eine Vorschau auf die Suchergebnisse anzuzeigen, nachdem die Suchabschätzung abgeschlossen ist. Wenn Sie diese Option auswählen, wird das Fenster **Vorschau der eDiscovery-Suche** geöffnet. Alle Nachrichten, die von den durchsuchten Postfächern zurückgegeben wurden, werden angezeigt.
        

        > [!NOTE]
        > Die Postfächer, die durchsucht wurden, werden im Fenster <STRONG>Vorschau der eDiscovery-Suche</STRONG> im rechten Bereich angezeigt. Für jedes Postfach wird außerdem die Anzahl der zurückgegebenen Elemente und die Gesamtgröße dieser Elemente angezeigt. Alle Elemente, die bei der Suche zurückgegeben wurden, werden im rechten Bereich angezeigt und können nach dem aktuellsten oder dem ältesten Datum sortiert werden. Die Elemente aller Postfächer können nicht im rechten Bereich angezeigt werden, wenn Sie ein Postfach im linken Bereich anklicken. Um die Elemente anzuzeigen, die von einem bestimmten Postfach zurückgegeben wurden, können Sie die Suchergebnisse kopieren und die Elemente im Discovery-Postfach anzeigen.

    
    ![Suchergebnisse schätzen oder in Vorschau anzeigen](images/Dd353189.57e0fc2d-71bf-42aa-aa4b-4a77148f2b43(EXCHG.150).gif "Suchergebnisse schätzen oder in Vorschau anzeigen")  

Zurück zum Seitenanfang

## Verwenden der Shell zur Schätzung der Suchergebnisse

Sie können den *EstimateOnly*-Switch verwenden, um eine Schätzung der Suchergebnisse zu erhalten, ohne die Ergebnisse in ein Discovery-Postfach zu kopieren. Sie müssen mit dem Cmdlet **Start-MailboxSearch** eine Suche vom Typ "Nur schätzen" ausführen. Anschließend können Sie mithilfe des Cmdlets **Get-MailboxSearch** die geschätzten Suchergebnisse abrufen.

Sie würden z. B. die folgenden Befehle ausführen, um eine neue eDiscovery-Suche zu erstellen und anschließend eine Schätzung der Suchergebnisse anzuzeigen:

```
    New-MailboxSearch "FY13 Q2 Financial Results" -StartDate "04/01/2013" -EndDate "06/30/2013" -SourceMailboxes "DG-Finance" -SearchQuery '"Financial" AND "Fabrikam"' -EstimateOnly -IncludeKeywordStatistics
```

```
    Start-MailboxSearch "FY13 Q2 Financial Results"
```

```
    Get-MailboxSearch "FY13 Q2 Financial Results"
```

Um die Informationen der geschätzten Suchergebnisse anzuzeigen können Sie den folgenden Befehl ausführen:

    Get-MailboxSearch "FY13 Q2 Financial Results" | FL Name,Status,LastRunBy,LastStartTime,LastEndTime,Sources,SearchQuery,ResultSizeEstimate,ResultNumberEstimate,Errors,KeywordHits

Zurück zum Seitenanfang

## Weitere Informationen zu eDiscovery-Suchen

  - Nachdem Sie eine neue eDiscovery-Suche erstellt haben, können Sie die Suchergebnisse in das Discovery-Postfach kopieren und die Ergebnisse als PST-Datei speichern. Weitere Informationen finden Sie unter:
    
      - [Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach](copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md)
    
      - [Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - Wenn Sie eine eDiscovery-Suchergebnisschätzung (mit Schlüsselwörtern in den Suchkriterien) durchgeführt haben, können Sie die Schlüsselwortstatistik anzeigen, indem Sie im Detailbereich für die ausgewählte Suche auf **Schlüsselwortstatistik anzeigen** klicken. Diese Statistik enthält detaillierte Informationen über die Anzahl der Elemente, die für jedes in der Suchanfrage verwendete Schlüsselwort zurückgegeben werden. Wenn allerdings mehr als 100 Quellpostfächer in die Suche einbezogen werden, wird beim Versuch, die Schlüsselwortstatistik anzuzeigen, eine Fehlermeldung zurückgegeben. Wenn Sie die Schlüsselwortstatistik anzeigen möchten, dürfen nicht mehr als 100 Postfächer in die Suche aufgenommen werden.

  - Wenn Sie **Get-MailboxSearch** in Exchange Online für den Abruf von Informationen über eine eDiscovery-Suche verwenden, müssen Sie den Namen einer Suche angeben, damit eine vollständige Liste der Sucheigenschaften zurückgegeben wird, wie z. B. `Get-MailboxSearch "Contoso Legal Case"`. Wenn Sie das Cmdlet **Get-MailboxSearch** ohne jegliche Parameter ausführen, werden die folgenden Eigenschaften nicht zurückgegeben:
    
      - SourceMailboxes
    
      - Quellen
    
      - SearchQuery
    
      - ResultsLink
    
      - PreviewResultsLink
    
      - Fehler
    
    Der Grund dafür ist, dass viele Ressourcen erforderlich sind, um diese Eigenschaften für alle eDiscovery-Suchvorgänge in Ihrer Organisation zurückzugeben.

Zurück zum Seitenanfang

