---
title: 'Ändern einer Compliance-eDiscovery-Suche: Exchange Online Help'
TOCTitle: Ändern einer Compliance-eDiscovery-Suche
ms:assetid: 3162743c-cc12-4997-91e0-bcbfea8bcb17
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335182(v=EXCHG.150)
ms:contentKeyID: 50475416
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern einer Compliance-eDiscovery-Suche

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-08-27_

Nachdem Sie eine Compliance-eDiscovery-Suche erstellt haben, können Sie diese modifizieren, um die Suchparameter zu ändern. Sie können z. B. die zu durchsuchenden Postfächer, Datenbereiche, Schlüsselwörter und Protokollierungsoptionen ändern oder ein anderes Discoverypostfach zum Speichern der Suchergebnisse angeben. Alle Ä̈nderungen, die Sie an den Sucheigenschaften vornehmen, werden angewendet, wenn Sie die Suche erneut starten.


> [!WARNING]
> Wenn eine Compliance-eDiscovery-Suche ausgeführt wird, müssen Sie diese beenden, bevor Sie Änderungen vornehmen können. Wenn Sie die Suche erneut starten, werden die Ergebnisse der letzten Ausführung der Suche aus dem Discoverypostfach entfernt. Die Protokolle der vorherigen Suchen werden jedoch gespeichert.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2-5 Minuten.

  - Eine Compliance-eDiscovery-Suche wurde erstellt und wird nicht ausgeführt.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Ändern einer Compliance-eDiscovery-Suche mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Wählen Sie in der Listenansicht die Compliance-eDiscovery-Suche aus, die Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Unter **Compliance-eDiscovery und -Archiv** können Sie die folgenden Einstellungen ändern:
    
      - Ändern Sie auf der Seite **Name** den Namen für die Suche und die optionale Beschreibung.
    
      - Ändern Sie auf der Seite **Postfach** die Postfächer, die durchsucht werden sollen. Sie können in alle Postfächern suchen oder bestimmte Postfächer auswählen, die durchsucht werden sollen.
        

        > [!IMPORTANT]
        > Sie können die Option <STRONG>Alle Postfächer durchsuchen</STRONG> nicht verwenden, um alle Postfächer auf Exchange 2013-Postfachservern in einem Archiv zu platzieren. Zum Erstellen eines Compliance-Archivs müssen Sie die Option <STRONG>Zu durchsuchende Postfächer angeben</STRONG> auswählen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/create-or-remove-in-place-holds">Erstellen oder Entfernen eines Compliance-Archivs</A>.

    
      - Ändern Sie auf der Seite **Suchabfrage** die folgenden Felder:
        
          - **Gesamten Postfachinhalt einschließen**   Wählen Sie diese Option, um den gesamten Inhalt der ausgewählten Postfächer in einem Archiv zu platzieren.
        
          - **Anhand von Kriterien filtern**   Wählen Sie diese Option, um Suchkriterien wie zum Beispiel Schlüsselwörter, Start- und Enddaten, Absender- und Empfängeradressen und Nachrichtentypen anzugeben.
    
      - Aktivieren Sie auf der Seite **Compliance-Archiv** das Kontrollkästchen **Inhalt, der mit der Suchanfrage übereinstimmt, in ausgewählten Postfächern aufbewahren**, und wählen Sie eine der folgenden Optionen, um Elemente in einem Compliance-Archiv zu platzieren:
        
          - **Dauerhaft anhalten**   Wählen Sie diese Option, um die zurückgegebenen Elemente dauerhaft beizubehalten. Aufbewahrte Elemente werden solange beibehalten, bis Sie das Postfach aus der Suche entfernt oder die Suche entfernt haben.
        
          - **Anzahl von Tagen angeben, die Elemente in Relation zu ihrem Empfangsdatum in einem Archiv gespeichert werden sollen** Verwenden Sie diese Option, um Elemente für einen bestimmten Zeitraum beizubehalten. Diese Option können Sie beispielsweise verwenden, wenn es für Ihre Organisation erforderlich ist, dass alle Nachrichten mindestens sieben Jahre aufbewahrt werden. Sie können ein *zeitbasiertes* Compliance-Archiv zusammen mit einer Aufbewahrungsrichtlinie verwenden, damit sichergestellt ist, dass alle Elemente in sieben Jahren gelöscht werden.
            

            > [!IMPORTANT]
            > Wenn Postfächer oder Elemente aus rechtlichen Gründen in einem Compliance-Archiv platziert werden, empfiehlt es sich im Allgemeinen, die Elemente dauerhaft beizubehalten oder die Archivierung zu beenden, wenn der Fall oder die Untersuchung beendet ist.



4.  Klicken Sie auf **Speichern**.

## Ändern einer Compliance-eDiscovery-Suche mithilfe der Shell

In diesem Beispiel wird die Compliance-eDiscovery-Suche "Search-Project Contoso" geändert, um Postfächer zu durchsuchen, die Mitgliedern der Verteilergruppe "DG-ProjectManagers" gehören.

    Set-MailboxSearch -Identity "Search-Project Contoso" -SourceMailboxes "DG-ProjectManagers"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Änderung einer Compliance-eDiscovery-Suche zu überprüfen:

  - Verwenden Sie die Exchange-Verwaltungskonsole, um die Eigenschaften der Suche zu überprüfen.

  - Verwenden Sie die Shell, um über das Cmdlet **Get-MailboxSearch** die Eigenschaften der Suche zu überprüfen. Beispiele zur Überprüfung der Eigenschaften einer Postfachsuche finden Sie im Abschnitt "Beispiele" in [Get-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351021\(v=exchg.150\)).


> [!NOTE]
> Wenn Sie <STRONG>Get-MailboxSearch</STRONG> in Exchange Online für den Abruf von Informationen über eine eDiscovery-Suche verwenden, müssen Sie den Namen einer Suche angeben, damit eine vollständige Liste der Sucheigenschaften zurückgegeben wird, wie z.&nbsp;B. <CODE>Get-MailboxSearch "Contoso Legal Case"</CODE>. Wenn Sie das Cmdlet <STRONG>Get-MailboxSearch</STRONG> ohne jegliche Parameter ausführen, werden die folgenden Eigenschaften nicht zurückgegeben: 
> <UL>
> <LI>
> <P>SourceMailboxes</P>
> <LI>
> <P>Quellen</P>
> <LI>
> <P>SearchQuery</P>
> <LI>
> <P>ResultsLink</P>
> <LI>
> <P>PreviewResultsLink</P>
> <LI>
> <P>Fehler</P></LI></UL>Der Grund dafür ist, dass viele Ressourcen erforderlich sind, um diese Eigenschaften für alle eDiscovery-Suchvorgänge in Ihrer Organisation zurückzugeben.


