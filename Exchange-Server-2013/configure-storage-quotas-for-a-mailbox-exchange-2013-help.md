---
title: 'Konfigurieren von Speicherkontingenten für ein Postfach: Exchange 2013 Help'
TOCTitle: Konfigurieren von Speicherkontingenten für ein Postfach
ms:assetid: 5f5fe292-c80e-4a0b-b3e6-e193ea5171d0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998353(v=EXCHG.150)
ms:contentKeyID: 50554837
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Speicherkontingenten für ein Postfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-07_

**Zusammenfassung:**  Verwenden Sie die Exchange-Verwaltungskonsole oder die Shell, um Speicherkontingente für bestimmte Postfächer festzulegen.

Speicherkontingente ermöglichen es Ihnen, die Größe von Postfächern zu steuern und das Wachstum von Postfachdatenbanken zu verwalten. Wenn die Postfachgröße eine angegebene Kontingentgrenze erreicht oder überschreitet, sendet Exchange eine beschreibende Benachrichtigung an den Postfachbesitzer.


> [!NOTE]
> Speicherkontingente für die Größe eines bestimmten Postfachs anwenden, entsprechend der Definitionen durch die Eigenschaft <CODE>TotalItemSize</CODE> bei der Ausführung des Cmdlets <CODE>Get-MailboxStatistics</CODE>. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb124612(v=exchg.150)">Get-MailboxStatistics</A>.



Speicherkontingente werden typischerweise pro Datenbank konfiguriert. Das bedeutet, dass die für eine Postfachdatenbank konfigurierten Kontingente für alle Postfächer in der betreffenden Datenbank gelten. Weitere Informationen zum Verwalten von Postfacheinstellungen pro Datenbank finden Sie unter [Verwalten von Postfachdatenbanken in Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

In diesem Thema wird beschrieben, wie Sie die Speichereinstellungen für ein bestimmtes Postfach anpassen, anstatt die Speichereinstellungen der Postfachdatenbank zu verwenden. Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Benutzerpostfächer finden Sie unter [Verwalten von Benutzerpostfächern](https://technet.microsoft.com/de-de/library/Bb123809(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Speicherkontingenten für ein Postfach mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Speicherkontingente Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite für die Postfacheinstellungen auf **Postfachnutzung**, und klicken Sie dann auf **Weitere Optionen**.

4.  Klicken Sie auf **Die Einstellungen für dieses Postfach anpassen**, und konfigurieren Sie dann die folgenden Felder. Der Wertebereich für alle Einstellungen für Speicherkontingente liegt zwischen 0 und 2047 GB.
    
      - **Warnmeldung senden ab (GB)**   In diesem Feld wird der maximale Speichergrenzwert angezeigt, der erreicht werden muss, damit eine Warnung an den Benutzer ausgegeben wird. Wenn die Größe des Postfachs den angegebenen Wert erreicht oder übersteigt, sendet Exchange eine Warnmeldung an den Benutzer.
        

        > [!IMPORTANT]
        > Die dem Kontingent <STRONG>Warnmeldung senden</STRONG> zugeordnete Nachricht wird erst an den Benutzer gesendet, wenn der Wert für diese Einstellung mehr als 50 % des im Kontingent <STRONG>Senden verbieten</STRONG> angegebenen Werts ausmacht. Wenn Sie beispielsweise das Kontingent <STRONG>Senden verbieten</STRONG> auf 8 MB festlegen, müssen Sie das Kontingent <STRONG>Warnmeldung senden</STRONG> auf mindestens 4 MB einstellen. Andernfalls wird die Meldung des Kontingents <STRONG>Warnmeldung senden</STRONG> nicht gesendet.

    
      - **Senden verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sendeverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und zeigt eine Fehlermeldung mit weiteren Informationen an.
    
      - **Senden/Empfangen verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sende- und Empfangsverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und stellt keine neuen Nachrichten mehr an das Postfach zu. Alle an das Postfach gesendeten Nachrichten werden zusammen mit einer Fehlermeldung und weiteren Informationen an den Absender zurückgeschickt.

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Verwenden der Shell zum Konfigurieren von Speicherkontingenten für ein Postfach

In diesem Beispiel werden die Grenzwerte für Warnungen, Sendeverbote sowie Sende- und Empfangskontingente für das Postfach von Joe Healy auf 24,5 GB, 24,75 GB bzw. 25 GB festgelegt.


> [!NOTE]
> Damit sichergestellt ist, dass die benutzerdefinierten Einstellungen für das Postfach anstelle der Standardeinstellungen der Postfachdatenbank verwendet werden, müssen Sie den Parameter <EM>UseDatabaseQuotaDefaults</EM> auf <CODE>$false</CODE> festlegen.



    Set-Mailbox -Identity "Joe Healy" -IssueWarningQuota 24.5gb -ProhibitSendQuota 24.75gb -ProhibitSendReceiveQuota 25gb -UseDatabaseQuotaDefaults $false

In diesem Beispiel werden die Grenzwerte für Warnungen, Sendeverbote sowie Sende- und Empfangskontingente für das Postfach von Ayla Kol auf 900 MB, 950 MB bzw. 1 GB festgelegt, und das Postfach wird zur Verwendung der benutzerdefinierten Einstellungen konfiguriert.

    Set-Mailbox -Identity "Ayla Kol" -IssueWarningQuota 900mb -ProhibitSendQuota 950mb -ProhibitSendReceiveQuota 1gb -UseDatabaseQuotaDefaults $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Speicherkontingente für ein Postfach zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Speicherkontingente Sie überprüfen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite für die Postfacheinstellungen auf **Postfachnutzung**, und klicken Sie dann auf **Weitere Optionen**.

4.  Überprüfen Sie, ob **Die Einstellungen für dieses Postfach anpassen** ausgewählt ist.

5.  Überprüfen Sie die Kontingenteinstellungen.

Oder

Führen Sie folgenden Befehl in der Shell aus.

    Get-Mailbox <identity> | fl IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults

