---
title: 'Verwalten von Postfachdatenbanken in Exchange 2013: Exchange 2013 Help'
TOCTitle: Verwalten von Postfachdatenbanken in Exchange 2013
ms:assetid: ead4a96b-1717-435b-bcfc-9901ac4e3b58
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150580(v=EXCHG.150)
ms:contentKeyID: 50477011
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Postfachdatenbanken in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-04-29_

Eine Postfachdatenbank ist eine Granularitätseinheit, in der Postfächer erstellt und gespeichert werden. Eine Postfachdatenbank wird als Exchange-Datenbankdatei (EDB-Datei) gespeichert. In Microsoft Exchange Server 2013 weist jede Postfachdatenbank eigene, konfigurierbare Eigenschaften auf.

In diesem Thema wird die Ausführung von Konfigurationsaufgaben im Zusammenhang mit der Verwaltung Ihrer Postfachdatenbanken in Microsoft Exchange Server 2013 erläutert.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbanken" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Postfachdatenbank

## Erstellen einer Postfachdatenbank mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server**.

2.  Wählen Sie **Datenbanken** aus, und klicken Sie dann auf das Symbol **+**, um eine Datenbank zu erstellen.

3.  Verwenden Sie den Assistenten zur Erstellung neuer Datenbanken, um Ihre Datenbank zu erstellen.

## Erstellen einer Postfachdatenbank mithilfe der Shell

Ein Beispiel für das Erstellen einer Postfachdatenbank finden Sie in Beispiel 1 unter [New-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997976\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Datenbank erfolgreich erstellt wurde:

  - Überprüfen Sie in der Exchange-Verwaltungskonsole, ob die Postfachdatenbank, die Sie erstellt haben, auf der Seite **Datenbanken** aufgeführt wird.

  - Überprüfen Sie in der Shell, ob die Datenbank auf dem Server "Mailbox01" erstellt wurde, indem Sie den folgenden Befehl ausführen.
    
    ```powershell
Get-MailboxDatabase -Server "Mailbox01"
```

## Abrufen der Eigenschaften der Postfachdatenbank

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)).

## Abrufen der Eigenschaften der Postfachdatenbank mithilfe der Shell

Ein Beispiel für das Abrufen der Eigenschaften der Postfachdatenbank finden Sie in Beispiel 2 unter [New-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997976\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um das erfolgreiche Abrufen Ihrer Postfachdatenbankinformationen zu überprüfen:

Überprüfen Sie in der Shell, dass alle Postfachdatenbankinformationen ordnungsgemäß dargestellt werden.

## Festlegen der Eigenschaften der Postfachdatenbank

## Festlegen der Eigenschaften der Postfachdatenbank mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server**.

2.  Wählen Sie **Datenbanken** aus, und klicken Sie dann auf die zu konfigurierende Postfachdatenbank.

3.  Klicken Sie auf **Bearbeiten** ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Attribute einer Postfachdatenbank zu konfigurieren.

4.      
    Auf der Registerkarte **Allgemein** können Sie den Status der Postfachdatenbank anzeigen, einschließlich des Pfads zur Postfachdatenbank, der letzten Sicherung und des Status der Postfachdatenbank:
    
      - **Datenbankpfad**   In diesem schreibgeschützten Feld wird der vollständige Pfad zur Exchange 2013-Datenbankdatei (EDB) für die ausgewählte Postfachdatenbank angezeigt. Zum Anzeigen des gesamten Pfads müssen Sie möglicherweise auf den Pfad klicken und die NACH-RECHTS-TASTE drücken. Sie können in diesem Feld nicht den Pfad ändern. Verwenden Sie zum Ändern des Speicherorts der Datenbankdateien das Cmdlet [Move-DatabasePath](https://technet.microsoft.com/de-de/library/bb124742\(v=exchg.150\)).
    
      - **Letzte vollständige Sicherung**   In diesem schreibgeschützten Feld werden das Datum und die Uhrzeit der letzten vollständigen Sicherung der Postfachdatenbank angezeigt.
    
      - **Letzte inkrementelle Sicherung**   In diesem schreibgeschützten Feld werden das Datum und die Uhrzeit der letzten inkrementellen Sicherung der Postfachdatenbank angezeigt.
    
      - **Status**   In diesem schreibgeschützten Feld wird angezeigt, ob die Postfachdatenbank eingebunden oder nicht eingebunden ist.
    
      - **Eingebunden auf Server**   In diesem schreibgeschützten Feld wird angezeigt, auf welchem Server die Datenbank eingebunden ist.
    
      - **Master**   Dieses schreibgeschützte Feld zeigt den Masterserver für die Postfachdatenbank an. Der Postfachserver, der die aktive Kopie einer Datenbank hostet, wird als Postfachdatenbankmaster bezeichnet.
    
      - **Mastertyp**   Dieses schreibgeschützte Feld zeigt den Typ des Postfachdatenbankmasters an.
    
      - **Geändert**   Dieses schreibgeschützte Feld zeigt das Datum und die Uhrzeit der letzten Änderung der Datenbank an.
    
      - **Server, die eine Kopie dieser Datenbank hosten**   In diesem schreibgeschützten Feld werden die weiteren Server angezeigt, die über eine Kopie dieser Datenbank verfügen.

5.  Auf der Registerkarte **Wartung** können Sie Einstellungen für die Postfachdatenbank konfigurieren. Sie können einen Journalempfänger angeben, einen Wartungszeitplan festlegen und die Datenbank beim Start bereitstellen:
    
      - **Journalempfänger**   Klicken Sie auf **Durchsuchen**, um einen Empfänger anzugeben, für den das Journaling in dieser Postfachdatenbank aktiviert wird. Entfernen Sie den aufgeführten Empfänger, um das Journaling zu deaktivieren.
    
      - **Wartungszeitplan** Verwenden Sie diese Liste, um einen der voreingestellten Wartungszeitpläne auszuwählen. Sie können auch einen benutzerdefinierten Zeitplan konfigurieren. Um einen benutzerdefinierten Zeitplan zu erstellen, klicken Sie auf **Anpassen**.
    
      - **Hintergrundwartung für Datenbank aktivieren (24 x 7 ESE-Scannen)**   Aktivieren Sie dieses Kontrollkästchen, um einen Onlinescan der Datenbank zu aktivieren, der kontinuierlich im Hintergrund ausgeführt wird. Bei einem Onlinescan der Datenbank wird eine Prüfsummenberechnung für die Datenbank durchgeführt. Außerdem prüft Exchange auf verlorenen Speicherplatz in der Datenbank, der wiederhergestellt wird. Wenn Sie dieses Kontrollkästchen aktivieren, überprüft Exchange die Datenbank höchstens einmal pro Tag und gibt ein Warnereignis aus, wenn der Datenbankscan innerhalb von sieben Tagen nicht abgeschlossen werden kann.
    
      - **Diese Datenbank beim Start nicht bereitstellen**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Exchange diese Postfachdatenbank beim Start bereitstellt.
    
      - **Diese Datenbank kann bei einer Wiederherstellung überschrieben werden**    Aktivieren Sie dieses Kontrollkästchen, um zuzulassen, dass die Postfachdatenbank während eines Wiederherstellungsvorgangs überschrieben wird.
    
      - **Umlaufprotokollierung aktivieren**   Aktivieren Sie dieses Kontrollkästchen, um die Umlaufprotokollierung zu aktivieren.

6.  Verwenden Sie die Registerkarte **Grenzwerte** zur Angabe der Speichergrenzwerte, der Zeitspanne zwischen Warnmeldungen sowie der Löscheinstellungen für eine Postfachdatenbank:
    
      - **Warnmeldung senden ab (GB)**   Aktivieren Sie dieses Kontrollkästchen, um Postfachbenutzer automatisch zu warnen, wenn ihr Postfach die Speichergrenze erreicht. Aktivieren Sie dieses Kontrollkästchen zum Festlegen der Speichergrenze, und geben Sie dann in Gigabyte (GB) an, wie viel Inhalt in der Datenbank gespeichert werden kann, bevor der Postfachbenutzer eine Warnmeldung erhält. Sie können einen Wert zwischen 0 und 2.097.151 MB (2,0 TB) eingeben.
    
      - **Senden verbieten ab (GB)**   Aktivieren Sie dieses Kontrollkästchen, um Benutzer daran zu hindern, nach dem Erreichen der für das Postfach festgelegten Speichergrenze neue E-Mail-Nachrichten zu senden. Aktivieren Sie dieses Kontrollkästchen zum Festlegen der Speichergrenze, und geben Sie dann die Größe des Postfachs in GB ein, ab der Sie das Senden von neuen E-Mail-Nachrichten verbieten und den Benutzer benachrichtigen möchten. Sie können einen Wert zwischen 0 und 2.097.151 MB (2,0 TB) eingeben.
    
      - **Senden und Empfangen verbieten ab (GB)**   Aktivieren Sie dieses Kontrollkästchen, um Benutzer daran zu hindern, nach dem Erreichen der für das Postfach festgelegten Speichergrenze E-Mail-Nachrichten zu senden und zu empfangen. Aktivieren Sie dieses Kontrollkästchen zum Festlegen der Speichergrenze, und geben Sie dann die Größe des Postfachs in GB ein, ab der Sie das Senden und Empfangen von E-Mail-Nachrichten verbieten und den Benutzer benachrichtigen möchten. Sie können einen Wert zwischen 0 und 2.097.151 MB (2,0 TB) eingeben.
    
      - **Gelöschte Element aufbewahren für (Tage)**   Aktivieren Sie dieses Kontrollkästchen, um die Anzahl von Tagen festzulegen, für die gelöschte Elemente in einem Postfach aufbewahrt werden. Sie können einen Wert zwischen 0 und 24.855 Tagen eingeben.
    
      - **Gelöschte Postfächer aufbewahren (Tage)**   Aktivieren Sie dieses Kontrollkästchen, um die Anzahl von Tagen fest, für die gelöschte Postfächer aufbewahrt werden. Sie können einen Wert zwischen 0 und 24.855 Tagen eingeben.
    
      - **Elemente nicht endgültig löschen, bevor eine Sicherung der Datenbank erstellt wurde**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Postfächer und E-Mail-Nachrichten gelöscht werden, bevor die Postfachdatenbank gesichert wurde.

7.  Auf der Registerkarte **Clienteinstellungen** können Sie das Offlineadressbuch (OAB) für das Postfach auswählen:
    
      - **Offlineadressbuch**   Klicken Sie zum Auswählen eines Offlineadressbuchs auf **Durchsuchen**, und wählen Sie dann das Offlineadressbuch aus.

## Festlegen von Eigenschaften der Postfachdatenbank mithilfe der Shell

Ein Beispiel dazu, wie Sie die Eigenschaften der Postfachdatenbank festlegen können, finden Sie in Beispiel 1 in [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die Attribute erfolgreich festgelegt haben:

  - Überprüfen Sie, ob Ihre Änderungen in der Exchange-Verwaltungskonsole gespeichert wurden.

  - Führen Sie in der Shell folgenden Befehl aus, um Eigenschaften der Postfachdatenbank abzurufen.
    
    ```powershell
Get-MailboxDatabase -Identity MailboxDatabase01 -Status | Format-List
```

## Verschieben eines Postfachdatenbankpfads

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Move-DatabasePath](https://technet.microsoft.com/de-de/library/bb124742\(v=exchg.150\)).

## Verschieben eines Postfachdatenbankpfads mithilfe der Shell

Ein Beispiel dazu, wie Sie die Eigenschaften der Postfachdatenbank festlegen können, finden Sie in Beispiel 1 in [Move-DatabasePath](https://technet.microsoft.com/de-de/library/bb124742\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie den Datenbankpfad erfolgreich verschoben haben:

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Server** \> **Datenbanken**, und klicken Sie auf das entsprechende Postfach, um es auszuwählen.

2.  Klicken Sie auf das Symbol mit dem **Stift**, und überprüfen Sie, dass der Datenbankpfad ordnungsgemäß angegeben ist.

## Einbinden einer Postfachdatenbank

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\)).

## Einbinden einer Postfachdatenbank mithilfe der Shell

Ein Beispiel für das Einbinden einer Postfachdatenbank finden Sie in Beispiel 1 in [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die Postfachdatenbank erfolgreich eingebunden haben.

  - Führen Sie in der Shell folgenden Befehl aus, um Eigenschaften der Postfachdatenbank für alle Postfachdatenbanken abzurufen.
    
    ```powershell
Get-MailboxDatabase -IncludePreExchange2013
```

## Aufheben der Einbindung einer Postfachdatenbank

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\)).

## Aufheben der Einbindung einer Postfachdatenbank mithilfe der Shell

Ein Beispiel für das Aufheben der Einbindung einer Postfachdatenbank finden Sie in Beispiel 1 in [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die Einbindung der Datenbank erfolgreich aufgehoben haben:

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Server** \> **Datenbanken**, und klicken Sie auf das entsprechende Postfach, um es auszuwählen.

2.  Klicken Sie auf das Symbol mit dem **Stift**, und überprüfen Sie, ob der Datenbankstatus dem Wert **Einbindung aufgehoben** entspricht.

## Entfernen einer Postfachdatenbank

## Entfernen einer Postfachdatenbank mithilfe der Exchange-Verwaltungskonsole

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Server** \> **Datenbanken**, und klicken Sie auf das entsprechende Postfach, um es auszuwählen.

2.  Klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"), um die Postfachdatenbank zu entfernen.

## Entfernen einer Postfachdatenbank mithilfe der Shell

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997931\(v=exchg.150\)).

1.  Führen Sie den folgenden Befehl zum Entfernen der Postfachdatenbank "MyDatabase" aus.
    
    ```powershell
Remove-MailboxDatabase -Identity "MyDatabase"
```

2.  Wenn Sie aufgefordert werden, diese Aktion zu bestätigen, geben Sie **Y** ein.

3.  Wenn das Dialogfeld mit dem Inhalt angezeigt wird, dass die Datenbank erfolgreich entfernt wurde, notieren Sie sich den Speicherort der Exchange 2013-Datenbank (EDB-Datei). Wenn Sie diese Datei von der Festplatte entfernen möchten, muss sie manuell entfernt werden.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die Postfachdatenbank erfolgreich entfernt haben:

  - Wählen Sie in der Exchange-Verwaltungskonsole **Server** \> **Datenbanken** aus.

  - Überprüfen Sie, ob die Postfachdatenbank entfernt wurde.

