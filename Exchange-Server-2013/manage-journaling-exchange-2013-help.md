---
title: 'Verwalten des Journalings: Exchange 2013 Help'
TOCTitle: Verwalten des Journalings
ms:assetid: d517f27e-f80a-4a06-988c-cbbf981c701d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ651670(v=EXCHG.150)
ms:contentKeyID: 50476798
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten des Journalings

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe der Aufzeichnung eingehender und ausgehender E-Mail-Kommunikation in Journalen kann Ihre Organisation rechtlichen, regulatorischen und organisatorischen Auflagen genügen. In diesem Artikel wird die Ausführung grundlegender Aufgaben im Zusammenhang mit der Verwaltung des Journalings in Exchange 2013 und Exchange Online erläutert.

Das Standardjournaling wird für eine Postfachdatenbank konfiguriert. Dadurch kann der Journaling-Agent alle Nachrichten, die an Postfächer und von Postfächern in einer bestimmten Postfachdatenbank gesendet werden, erfassen. Sie können auch das Premiumjournaling verwenden. Dadurch kann der Journaling-Agent mithilfe von Journalregeln das Journaling differenzierter anwenden. Statt alle Postfächer in einer Postfachdatenbank in einem Journal zu erfassen, können Sie Journalregeln entsprechend den Anforderungen Ihrer Organisation erstellen, um das Journaling auf einzelne Empfänger oder Mitglieder von Verteilergruppen anzuwenden. Zur Verwendung das Premiumjournalings benötigen Sie eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL).

Weitere Informationen zu Journalen finden Sie unter [Journale](journaling-exchange-2013-help.md).

**Inhalt**

Erstellen einer Journalregel

Anzeigen oder Ändern einer Journalregel

Aktivieren oder Deaktivieren einer Journalregel

Entfernen einer Journalregel

Aktivieren oder Deaktivieren des Journalings pro Postfachdatenbank

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Journale" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Es wurde ein Journalpostfach erstellt, oder ein vorhandenes Postfach ist zur Verwendung als Journalpostfach verfügbar. Sie können ein Exchange Online-Postfach nicht als ein Journalpostfach festlegen. Sie können Journalberichte an ein lokales Archivierungssystem oder den Archivierungsdienst eines Drittanbieters senden. In einer Hybridbereitstellung, in der sich Postfächer sowohl auf lokalen Servern als auch in Exchange Online befinden, können Sie ein lokales Postfach als Journalpostfach für Ihre lokalen und Exchange Online-Postfächer festlegen.
    

    > [!IMPORTANT]
    > Wenn Sie in Exchange Online eine Journalregel konfiguriert haben, durch die Journalberichte an ein Journalingpostfach gesendet werden, das nicht vorhanden ist oder ein ungültiges Ziel darstellt, bleibt der Journalbericht in der Transportwarteschlange auf Microsoft-Rechenzentrumsservern. Wenn dies der Fall ist, wenden sich Microsoft-Rechenzentrumsmitarbeiter an Ihre Organisation und bitten Sie, das Problem zu beheben, damit die Journalberichte an ein Journalingpostfach übermittelt werden können. Wenn Sie das Problem nicht innerhalb von zwei Tagen ab der Kontaktaufnahme lösen, wird die problematische Journalregel von Microsoft deaktiviert.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>. Wenn Sie Probleme mit dem <STRONG>JournalingReportDNRTo</STRONG>-Postfach haben, finden Sie weitere Informationen unter <A href="https://go.microsoft.com/fwlink/p/?linkid=331674">Transport- und Postfachregeln in Exchange Online funktionieren nicht wie erwartet</A>.



## Erstellen einer Journalregel

## Erstellen einer Journalregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Journalregeln**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Feld **Journalregel** einen Namen für die Journalregel ein, und füllen Sie dann folgende Felder aus:
    
      - **Beim Senden der Nachricht an oder Empfangen der Nachricht von**   Geben Sie den Empfänger an, für den die Regel gilt. Sie können einen bestimmten Empfänger auswählen oder die Regel auf alle Nachrichten anwenden.
    
      - **Folgende Nachrichten im Journal erfassen**   Geben Sie den Bereich der Journalregel an. Sie können nur die internen Nachricht im Journal erfassen, nur die externen Nachrichten oder unabhängig vom Ursprung oder Ziel alle Nachrichten.
    
      - **Journalberichte senden an**   Geben Sie die Adresse des Journalingpostfachs ein, das alle Journalberichte empfängt.
        

        > [!NOTE]
        > Sie können auch den Anzeigenamen oder Alias für einen E-Mail-Benutzer oder eine E-Mail-Kontakt als Journalpostfach eingeben. In diesem Fall werden Journalberichte an die externe E-Mail-Adresse des E-Mail-Benutzers oder E-Mail-Kontakts gesendet. Die externe E-Mail-Adresse eines E-Mail-Benutzers oder E-Mail-Kontakts kann aber, wie zuvor beschrieben, nicht als Exchange Online-Postfach verwendet werden.



3.  Klicken Sie auf **Speichern**, um die Journalregel zu erstellen.

## Erstellen einer Journalregel mit der Verwaltungsshell

In diesem Beispiel wird die Journalregel "Discovery Journal Recipients" erstellt, mit der auf alle Nachrichten, die von dem Benutzer "user1@contoso.com" gesendet und empfangen werden, die Journalfunktion angewendet wird.

    New-JournalRule -Name "Discovery Journal Recipients" -Recipient user1@contoso.com -JournalEmailAddress "Journal Mailbox" -Scope Global -Enabled $True

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie die Journalregel erfolgreich erstellt haben:

  - Überprüfen Sie in der Exchange-Verwaltungskonsole, ob die neue Journalregel, die Sie erstellt haben, auf der Registerkarte **Journalregeln** aufgeführt wird.

  - Überprüfen Sie mithilfe der Shell durch Ausführen des folgenden Befehls, ob die neue Journalregel vorhanden ist (im Beispiel unten wird überprüft, ob die im Shell-Beispiel oben erstellte Regel vorhanden ist):
    
        Get-JournalRule "Discovery Journal Recipients"

Zurück zum Seitenanfang

## Anzeigen oder Ändern einer Journalregel

## Anzeigen oder Ändern einer Journalregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Journalregeln**.

2.  In der Listenansicht werden alle Journalregeln in Ihrer Organisation angezeigt.

3.  Doppelklicken Sie auf die Regel, die Sie anzeigen oder ändern möchten.

4.  Ändern Sie in **Journalregel** die gewünschten Einstellungen. Weitere Informationen zu den Einstellungen in diesem Dialogfeld finden Sie an früherer Stelle in diesem Thema unter Erstellen einer Journalregel mithilfe der Exchange-Verwaltungskonsole.

## Anzeigen oder Ändern einer Journalregel mithilfe der Shell

In diesem Beispiel wird eine Übersichtsliste aller Journalregeln in der Exchange-Organisation angezeigt:

    Get-JournalRule

In diesem Beispiel die Journalregel "Brokerage" abgerufen und die Ausgabe über Pipes an das Cmdlet **Format-List** übergeben, um alle Parameter der Regel in einem Listenformat anzuzeigen:

    Get-JournalRule "Brokerage Journal Rule" | Format-List

Wenn Sie die Eigenschaften einer bestimmten Regel ändern möchten, müssen Sie das Cmdlet [Set-JournalRule](https://technet.microsoft.com/de-de/library/bb125010\(v=exchg.150\)) verwenden. In diesem Beispiel wird der Name der Journalregel `JR-Sales` in `TraderVault` geändert. Die folgenden Regeleinstellungen werden ebenfalls geändert:

  - Empfänger

  - JournalEmailAddress

  - Umfang

<!-- end list -->

    Set-JournalRule JR-Sales -Name TraderVault -Recipient traders@woodgrovebank.com -JournalEmailAddress tradervault@woodgrovebank.com -Scope Internal

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie eine Journalregel erfolgreich geändert haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Journalregeln**. Doppelklicken Sie auf die Regel, die Sie geändert haben, und überprüfen Sie, ob die Änderungen gespeichert wurden.

  - Überprüfen Sie mithilfe der Shell durch Ausführen des folgenden Befehls, ob Sie die Journalregel erfolgreich geändert haben. Dieser Befehl listet die von Ihnen geänderten Eigenschaften und den Namen der Regel auf (im Beispiel unten wird die im Shell-Beispiel oben geänderte Regel überprüft):
    
        Get-TransportRule "TraderVault" | Format-List Name,Recipient,JournalEmailAddress,Scope

Zurück zum Seitenanfang

## Aktivieren oder Deaktivieren einer Journalregel


> [!IMPORTANT]
> Wenn Sie eine Journalregel deaktivieren, wendet der Journaling-Agent die Journalfunktion nicht mehr auf Nachrichten an, für die die Regel gilt. Während eine Journalregel deaktiviert ist, werden die Nachrichten, auf die normalerweise die Journalfunktion angewendet würde, nicht im Journal erfasst. Stellen Sie sicher, dass durch das Deaktivieren einer Journalregel keine gesetzlichen Bestimmungen oder die Anforderungen bezüglich der Richtlinientreue in Ihrer Organisation verletzt werden.



## Aktivieren oder Deaktivieren einer Journalregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Journalregeln**.

2.  Aktivieren Sie in der Listenansicht in der Spalte **Ein** neben dem Namen der Regel das Kontrollkästchen, um die Regel zu aktivieren, oder deaktivieren Sie es, um die Regel zu deaktivieren.

## Aktivieren oder Deaktivieren einer Journalregel mithilfe der Shell

In diesem Beispiel wird die Regel "Contoso" aktiviert.

    Enable-JournalRule "Contoso Journal Rule"

In diesem Beispiel wird die Regel "Contoso" deaktiviert.

    Disable-JournalRule "Contoso Journal Rule"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie eine Journalregel erfolgreich aktiviert oder deaktiviert haben:

  - Zeigen Sie in der Exchange-Verwaltungskonsole die Liste der Journalregeln an, und überprüfen Sie den Status des Kontrollkästchens in der Spalte **Ein**.

  - Führen Sie in der Shell folgenden Befehl aus, um eine Liste aller Journalregeln in Ihrer Organisation einschließlich Status zurückzugeben:
    
        Get-JournalRule | Format-Table Name,Enabled

Zurück zum Seitenanfang

## Entfernen einer Journalregel

## Entfernen einer Journalregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Journalregeln**.

2.  Wählen Sie in der Listeansicht die Regel aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Verwenden der Shell zum Entfernen einer Journalregel

In diesem Beispiel wird die Regel "Brokerage Journal Rule" entfernt.

    Remove-JournalRule "Brokerage Journal Rule"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie die Journalregel erfolgreich entfernt haben:

  - Überprüfen Sie in der Exchange-Verwaltungskonsole, ob die Regel, die Sie entfernt haben, nicht mehr auf der Registerkarte **Journalregeln** aufgeführt wird.

  - Führen Sie in der Shell folgenden Befehl aus, um zu überprüfen, ob die Regel, die Sie entfernt haben, nicht mehr aufgeführt wird:
    
        Get-JournalRule

Zurück zum Seitenanfang

## Aktivieren oder Deaktivieren des Journalings pro Postfachdatenbank


> [!WARNING]
> Die Deaktivierung der Journalerstellung für Nachrichten einer Postfachdatenbank kann dazu führen, dass Ihre Organisation die geltenden Richtlinien zur Aufbewahrung von Nachrichten nicht mehr einhält. Wenn Sie die Journalerstellung für Nachrichten einer Postfachdatenbank deaktivieren, werden keine Journalbelege mehr für Nachrichten gesendet, die von Postfächern in der Postfachdatenbank gesendet oder empfangen werden.



## Aktivieren oder Deaktivieren des Journalings pro Postfachdatenbank mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Doppelklicken Sie in der Listenansicht auf die Postfachdatenbank, für die Sie das Journaling aktivieren möchten.

3.  Klicken Sie auf **Wartung**, und klicken Sie dann neben dem Feld **Journalempfänger** auf **Durchsuchen**, um das Journalingpostfach auszuwählen. Durch Angabe eines Journalempfängers wird das Journaling für die Datenbank aktiviert.
    
    Zum Deaktivieren des Journalings entfernen Sie den Journalempfänger durch Klicken auf **X entfernen**.

## Aktivieren oder Deaktivieren des Journalings pro Postfachdatenbank mithilfe der Shell

In diesem Beispiel wird das Journaling für die Postfachdatenbank "Sales Database" aktiviert, und das Journalpostfach "Sales Database" wird als Journalempfänger festgelegt.

    Set-MailboxDatabase "Sales Database" -JournalRecipient "Sales Database Journal Mailbox"

In diesem Beispiel wird die Journalerstellung pro Postfachdatenbank für die Postfachdatenbank "Sales Database" deaktiviert.

    Set-MailboxDatabase "Sales Database" -JournalRecipient $Null

In diesem Beispiel wird die Journalerstellung pro Postfachdatenbank für alle Postfachdatenbanken in der Exchange-Organisation deaktiviert. Das Cmdlet [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)) wird verwendet, um alle Postfachdatenbanken in der Exchange-Organisation abzurufen. Die Ergebnisse des Cmdlets werden mittels Pipelining an das Cmdlet [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)) geleitet.

    Get-MailboxDatabase | Set-MailboxDatabase -JournalRecipient $Null

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie das Journaling pro Postfachdatenbank erfolgreich aktiviert oder deaktiviert haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Doppelklicken Sie auf die Datenbank, die Sie überprüfen möchten, und wählen Sie dann die Registerkarte **Wartung** aus.

3.  Wenn der richtige Journalempfänger im Feld **Journalempfänger** aufgeführt ist, haben Sie das Journaling für die Postfachdatenbank erfolgreich aktiviert. Wenn kein Journalempfänger aufgeführt ist, ist das Journaling für die Datenbank deaktiviert.

<!-- end list -->

  - Führen Sie in der Shell folgenden Befehl aus, um eine Liste aller Postfachdatenbanken in Ihrer Organisation mit den diesen zugeordneten Journalempfängern zurückzugeben. Das Journaling ist für Datenbanken aktiviert, für die ein Journalempfänger aufgeführt ist, für eine Datenbank ohne Journalempfänger ist sie deaktiviert.
    
        Get-MailboxDatabase | Format-Table Name,JournalRecipient

Zurück zum Seitenanfang

## Weitere Informationen

[Journale](journaling-exchange-2013-help.md)

[Deaktivieren oder Aktivieren der Journalfunktion für Voicemail und Benachrichtigungen über verpasste Anrufe](disable-or-enable-journaling-of-voice-mail-and-missed-call-notifications-exchange-2013-help.md)

[New-JournalRule](https://technet.microsoft.com/de-de/library/bb125242\(v=exchg.150\))

[Get-JournalRule](https://technet.microsoft.com/de-de/library/aa998866\(v=exchg.150\))

[Set-JournalRule](https://technet.microsoft.com/de-de/library/bb125010\(v=exchg.150\))

[Enable-JournalRule](https://technet.microsoft.com/de-de/library/bb123902\(v=exchg.150\))

[Disable-JournalRule](https://technet.microsoft.com/de-de/library/aa995925\(v=exchg.150\))

[Remove-JournalRule](https://technet.microsoft.com/de-de/library/bb123489\(v=exchg.150\))

[Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\))

