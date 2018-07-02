---
title: 'Erstellen oder Entfernen eines Compliance-Archivs: Exchange 2013 Help'
TOCTitle: Erstellen oder Entfernen eines Compliance-Archivs
ms:assetid: 9d5d8d37-a053-4830-9cb1-6e1ede25e963
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979797(v=EXCHG.150)
ms:contentKeyID: 50476347
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen oder Entfernen eines Compliance-Archivs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-01-18_


> [!NOTE]
> Wir haben den Stichtag (1. Juli 2017) für das Erstellen neuer In-Situ-Speicher in Exchange Online (in Office 365 und eigenständigen Exchange Online-Plänen) verschoben. Im späteren Verlauf dieses Jahres oder Anfang des nächsten Jahres können Sie keine neuen In-Situ-Speicher mehr in Exchange Online erstellen. Als Alternative zur Verwendung von In-Situ-Speichern können Sie <A href="https://go.microsoft.com/fwlink/?linkid=780738">eDiscovery-Fälle</A> oder <A href="https://go.microsoft.com/fwlink/?linkid=827811">Aufbewahrungsrichtlinien</A> im Office 365-Sicherheit &amp; Compliance Center verwenden. Sobald die Erstellung neuer In-Situ-Speicher eingestellt ist, können vorhandene In-Situ-Speicher weiterhin geändert werden, und das Erstellen neuer In-Situ-Speicher in Exchange Server&nbsp;2013- und Exchange-Hybridbereitstellungen wird weiterhin unterstützt. Und Sie können weiterhin Postfächer im Beweissicherungsverfahren platzieren.



Bei einem Compliance-Archiv bleiben sämtliche Postfachinhalte einschließlich gelöschter Elemente und Originalversionen geänderter Elemente erhalten. Alle diese Postfachelemente werden bei einer [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)-Suche zurückgegeben. Wenn Sie für das Postfach eines Benutzers das Compliance-Archiv aktivieren, wird auch der Inhalt im zugehörigen Archivpostfach (falls aktiviert) archiviert und in einer eDiscovery-Suche zurückgegeben.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-Archiv" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Um ein Exchange Online-Postfach anzuhalten, muss ihm eine Exchange Online-Lizenz zugewiesen sein (Tarif 2). Wenn einem Postfach eine Exchange Online-Lizenz (Tarif 1) zugewiesen ist, müssen Sie ihm eine separate Exchange Online-Archivierungslizenz zuweisen, um es anzuhalten.

  - Je nach Ihrer Active Directory-Topologie und Replikationswartezeit kann es bis zu einer Stunde dauern, bis ein Compliance-Archiv fertig gestellt ist.

  - Wie bereits erwähnt, wird der Inhalt im Archivpostfach des Benutzers auch ausgesetzt, wenn Sie für das Postfach eines Benutzers ein In-Situ-Archiv festlegen. Wenn Sie einen In-Situ-Speicher für ein lokales primäres Postfach in einer Exchange-Hybridbereitstellung festlegen, wird auch das cloudbasierte Archivpostfach (sofern aktiviert) ausgesetzt.

  - Wenn ein Benutzer in mehreren In-Situ-Speichern platziert wird, werden die Suchabfragen von einem abfragebasierten Archiv kombiniert (mit **OR**-Operatoren). In diesem Fall beträgt die maximale Anzahl von Stichwörtern in allen abfragebasierten Archiven für ein Postfach 500. Bei mehr als 500 Stichwörtern werden sämtliche Inhalte des Postfachs archiviert (nicht bloß die Inhalte, die mit den Suchkriterien übereinstimmen). Alle Inhalte werden archiviert, bis die Gesamtzahl von Stichwörtern auf 500 oder weniger verringert wird.

  - In Exchange Online wird das Kontingent für den Ordner "Wiederherstellbare Elemente" automatisch auf 100 GB erhöht, wenn Sie ein Postfach ins Compliance-Archiv platzieren. Die Standardgröße des Ordners "Wiederherstellbare Elemente" beträgt 30 GB.

  - In Exchange Online können Sie auch ein Compliance-Archiv in Office 365-Gruppen platzieren. Wenn Sie eine Office 365-Gruppe archivieren, wird das Gruppenpostfach archiviert; die Postfächer der Gruppenmitglieder werden nicht archiviert. Informationen zu Office 365-Gruppen finden Sie unter [Weitere Informationen zu Office 365-Gruppen](https://go.microsoft.com/fwlink/p/?linkid=724066).

## Erstellen eines Compliance-Archivs

**Erstellen eines Compliance-Archivs über die Exchange-Verwaltungskonsole**

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie im Abschnitt **Compliance-eDiscovery und Compliance-Archiv** auf der Seite **Name und Beschreibung** einen Namen für die Suche und optional eine Beschreibung ein, und klicken Sie dann auf **Weiter**.

4.  Wählen Sie auf der Seite **Postfächer und Öffentliche Ordner** die Inhaltsspeicherorte aus, die Sie im Archiv platzieren möchten, und klicken Sie dann auf **Weiter**.
    
    ![Wählen Sie Inhaltsspeicherorte aus, die im Haltebereich platziert werden sollen.](images/Dd979797.bbe76c50-a93b-4e5e-acd2-78e0d747ea19(EXCHG.150).png "Wählen Sie Inhaltsspeicherorte aus, die im Haltebereich platziert werden sollen.")  
    
    1.  **Alle Postfächer durchsuchen**   Beim Erstellen eines In-Situ-Speichers können Sie diese Option nicht auswählen. Sie können diese Option für In-Situ-eDiscovery-Suchvorgänge verwenden, aber zum Erstellen eines In-Situ-Speichers müssen Sie die bestimmten Postfächer auswählen, die Sie im Archiv platzieren möchten.
    
    2.  **Keine Postfächer durchsuchen**   Wählen Sie diese Option aus, wenn Sie ausschließlich für öffentliche Ordner einen In-Situ-Speicher erstellen.
    
    3.  **Zu durchsuchende Postfächer angeben**   Wählen Sie diese Option aus, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Postfächer oder Verteilergruppen auszuwählen, die Sie im Archiv platzieren möchten. In Exchange Online können Sie auch Office 365-Gruppen auswählen, die im Archiv platziert werden sollen.
    
    4.  **Alle öffentlichen Ordner durchsuchen**In Exchange Online können Sie dieses Kontrollkästchen aktivieren, um alle öffentlichen Ordner in Ihrer Organisation im Archiv zu platzieren. Wie zuvor beschrieben, müssen Sie zum Erstellen eines In-Situ-Speichers nur für öffentlichen Ordner die Option **Keine Postfächer durchsuchen** auswählen.

5.  Füllen Sie auf der Seite **Suchabfrage** die folgenden Felder aus, und klicken Sie anschließend auf **Weiter**:
    
      - **Gesamten Postfachinhalt einschließen**   Klicken Sie auf diese Schaltfläche, um den gesamten Inhalt der ausgewählten Postfächer in einem Archiv zu platzieren.
    
      - **Anhand von Kriterien filtern**   Klicken Sie auf diese Schaltfläche, um Suchkriterien wie zum Beispiel Schlüsselwörter, Start- und Endtermine, Absender- und Empfängeradressen und Nachrichtentypen anzugeben. Beim Erstellen eines abfragebasierten Archivs werden nur Elemente gespeichert, die mit den Suchkriterien übereinstimmen.
        

        > [!TIP]
        > Wenn Sie öffentliche Ordner im In-Situ-Speicher platzieren, werden E-Mail-Nachrichten im Zusammenhang mit dem Hierarchiesynchronisierungsprozess für öffentliche Ordner ebenfalls gespeichert. Auf diese Weise können Tausende von E-Mail-Elementen im Zusammenhang mit der Hierarchiesynchronisierung gespeichert werden. Diese Nachrichten können das Speicherkontingent für den Ordner „Wiederherstellbare Elemente“ für Postfächer für Öffentlicher Ordner auffüllen. Um dies zu verhindern, können Sie einen abfragebaiserten In-Situ-Speicher erstellen und das folgende <CODE>property:value</CODE>-Paar zur Suchabfrage hinzufügen:<BR><CODE>NOT(subject:HierarchySync*)</CODE><BR>Das Ergebnis ist, dass alle Nachrichten (im Zusammenhang mit der Synchronisierung der Hierarchie der öffentlichen Ordner), die den Ausdruck“HierarchySync“ in der Betreffzeile aufweisen, nicht im Archiv platziert werden.



6.  Aktivieren Sie auf der Seite **Einstellungen für Compliance-Archive** das Kontrollkästchen **Inhalt, der mit der Suchanfrage übereinstimmt, in ausgewählten Postfächern aufbewahren**, und wählen Sie eine der folgenden Optionen:
    
      - **Dauerhaft aufbewahren**   Klicken Sie auf diese Schaltfläche, um die zurückgegebenen Elemente dauerhaft in einem Archiv zu platzieren. Aufbewahrte Elemente werden solange beibehalten, bis Sie das Postfach aus der Suche entfernt oder die Suche entfernt haben.
    
      - **Anzahl von Tagen angeben, die Elemente in Bezug auf ihr Empfangsdatum aufbewahrt werden** Klicken Sie auf diese Schaltfläche, um Elemente für einen bestimmten Zeitraum aufzubewahren. Diese Option können Sie beispielsweise verwenden, wenn es für Ihre Organisation erforderlich ist, dass alle Nachrichten mindestens sieben Jahre aufbewahrt werden. Sie können ein *zeitbasiertes* Compliance-Archiv zusammen mit einer Aufbewahrungsrichtlinie verwenden, damit sichergestellt ist, dass alle Elemente in sieben Jahren gelöscht werden. Weitere Informationen zu Aufbewahrungsrichtlinien finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md).

**Erstellen eines Compliance-Archivs über die Shell**

Bei diesem Beispiel wird das Compliance-Archiv "Hold-CaseId012" erstellt und das Postfach "joe@contoso.com" im Archiv platziert.


> [!IMPORTANT]
> Wenn Sie keine weiteren Suchparameter für ein Compliance-Archiv angeben, werden alle Elemente in den Quellpostfächern im Archiv platziert. Wenn Sie den Parameter <EM>ItemHoldPeriod</EM> nicht angeben, werden Elemente unbegrenzt lange im Archiv platziert oder bis das Postfach entweder aus dem Archiv entfernt oder das Archiv gelöscht wird.



    New-MailboxSearch "Hold-CaseId012"-SourceMailboxes "joe@contoso.com" -InPlaceHoldEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298064\(v=exchg.150\)).

**Woher wissen Sie, dass dieses Verfahren erfolgreich war?**

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines Compliance-Archivs zu überprüfen:

  - Überprüfen Sie in der Exchange-Verwaltungskonsole, ob das Compliance-Archiv in der Listenansicht der Registerkarte **Compliance-eDiscovery und -Archiv** aufgeführt wird.

  - Rufen Sie mit dem Cmdlet **Get-MailboxSearch** die Postfachsuche ab, und überprüfen Sie die Suchparameter. Ein Beispiel für das Abrufen einer Postfachsuche finden Sie in den Beispielen unter [Get-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351021\(v=exchg.150\)).

Zurück zum Seitenanfang

## Entfernen eines Compliance-Archivs


> [!IMPORTANT]
> In Exchange 2013 können Postfachsuchvorgänge für die Compliance-eDiscovery und das Compliance-Archiv verwendet werden. Sie können keine Postfachsuche entfernen, die für ein Compliance-Archiv verwendet wird. Sie müssen zunächst das Compliance-Archiv deaktivieren, indem Sie das Kontrollkästchen <STRONG>Inhalt, der mit der Suchanfrage übereinstimmt, in ausgewählten Postfächern aufbewahren</STRONG> auf der Seite <STRONG>Einstellungen für Compliance-Archiv</STRONG> deaktivieren oder in der Shell den Parameter <EM>InPlaceHoldEnabled</EM> auf <CODE>$false</CODE> festlegen. Sie können ein Postfach auch über den in einer Suche angegebenen Parameter <EM>SourceMailboxes</EM> entfernen.



**Entfernen eines Compliance-Archivs über die Exchange-Verwaltungskonsole**

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Wählen Sie in der Listenansicht das Compliance-Archiv aus, das Sie entfernen möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie in den Eigenschaften von **Compliance-eDiscovery und -Archiv** auf der Seite **Compliance-Archiv** das Kontrollkästchen **Inhalt, der mit der Suchanfrage übereinstimmt, in ausgewählten Postfächern aufbewahren**, und klicken Sie dann auf **Speichern**.

4.  Wählen Sie in der Listenansicht nochmals das Compliance-Archiv aus, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

5.  Klicken Sie in der Warnung auf **Ja**, um die Suche zu entfernen.

**Entfernen eines Compliance-Archivs über die Shell**

Bei diesem Beispiel wird zunächst das Compliance-Archiv "Hold-CaseId012" deaktiviert und anschließend die Postfachsuche entfernt.

    Set-MailboxSearch "Hold-CaseId012"  -InPlaceHoldEnabled $false
    Remove-MailboxSearch "Hold-CaseId012"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxSearch](https://technet.microsoft.com/de-de/library/dd335145\(v=exchg.150\)).

**Woher wissen Sie, dass dieses Verfahren erfolgreich war?**

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Entfernung eines Compliance-Archivs zu überprüfen:

  - Überprüfen Sie in der Exchange-Verwaltungskonsole, ob das Compliance-Archiv in der Listenansicht der Registerkarte **Compliance-eDiscovery & -Archiv** nicht mehr aufgeführt wird.

  - Rufen Sie mit dem Cmdlet **Get-MailboxSearch**alle Postfachsuchvorgänge ab, und vergewissern Sie sich, dass die Suche, die Sie entfernt haben, nicht mehr aufgeführt ist. Ein Beispiel für das Abrufen einer Postfachsuche finden Sie in den Beispielen unter [Get-MailboxSearch](https://technet.microsoft.com/de-de/library/dd351021\(v=exchg.150\)).

Zurück zum Seitenanfang

