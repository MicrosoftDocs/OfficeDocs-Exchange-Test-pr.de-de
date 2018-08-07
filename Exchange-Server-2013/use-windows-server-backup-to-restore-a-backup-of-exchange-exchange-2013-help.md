---
title: 'Wiederher. v. Exchange-Sicher. m. Windows Server-Sicher.: Exchange 2013-Hilfe'
TOCTitle: Verwenden der Windows Server-Sicherung zum Wiederherstellen einer Sicherung von Exchange
ms:assetid: 2d0f31dc-eb32-451a-8852-591269026506
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876864(v=EXCHG.150)
ms:contentKeyID: 50475396
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwenden der Windows Server-Sicherung zum Wiederherstellen einer Sicherung von Exchange

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-18_

Mithilfe der Windows Server-Sicherung können Sie Exchange-Datenbanken sichern und wiederherstellen. Exchange enthält ein Plug-In für die Windows Server-Sicherung, mit der Sie VSS-basierte Sicherungen (Volume Shadow Copy Service, Volumenschattenkopie-Dienst) von Exchange-Daten erstellen und wiederherstellen können. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Exchange-Daten mithilfe der Windows Server-Sicherung](using-windows-server-backup-to-back-up-and-restore-exchange-data-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute, zuzüglich der erforderlichen Zeit zur Wiederherstellung der Daten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Windows Server-Sicherungsfunktion muss auf dem lokalen Computer installiert sein.

  - Wenn eine Datenbank an ihrem ursprünglichen Speicherort wiederhergestellt wird, kann die Datenbank im Status "Dirty Shutdown" verbleiben und vom System eingebunden werden. Bei der Wiederherstellung an einem alternativen Speicherort (z. B. in Vorbereitung der Verwendung einer Wiederherstellungsdatenbank) muss die Datenbank mithilfe der Datenbankdienstprogramme für Exchange Server (Eseutil.exe) manuell in den Status "Clean Shutdown" versetzt werden.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Windows Server-Sicherung zum Wiederherstellen einer Sicherung von Exchange

1.  Starten Sie die Windows Server-Sicherung.

2.  Wählen Sie **Lokale Sicherung** aus.

3.  Klicken Sie im Aktionsbereich auf **Wiederherstellen…**, um den Wiederherstellungsassistenten zu starten.

4.  Führen Sie auf der Seite **Erste Schritte** einen der folgenden Schritte aus:
    
      - Wenn die wiederherzustellenden Daten auf dem lokalen Server gesichert wurden, wählen Sie **Dieser Server (ServerName)** aus, und klicken Sie dann auf **Weiter**.
    
      - Wenn die wiederherzustellenden Daten von einem anderen Server stammen, oder wenn sich die wiederherzustellende Sicherung auf einem anderen Computer befindet, wählen Sie **Anderer Server** aus, und klicken Sie dann auf **Weiter**. Wählen Sie auf der Seite **Speicherorttyp angeben** den Eintrag **Lokale Datenträger** oder **Freigegebener Remoteordner** aus, und klicken Sie dann auf **Weiter**. Bei Auswahl von **Lokale Datenträger** wählen Sie auf der Seite **Speicherort für die Sicherung auswählen** den Datenträger aus, der die Sicherung enthält, und klicken Sie dann auf **Weiter**. Bei Auswahl von **Freigegebener Remoteordner** geben Sie den UNC-Pfad für die Sicherungsdaten auf der Seite **Remoteordner angeben** ein, und klicken Sie dann auf **Weiter**.

5.  Wählen Sie auf der Seite **Sicherungsdatum auswählen** das Datum und die Uhrzeit der wiederherzustellenden Sicherung aus, und klicken Sie dann auf **Weiter**.

6.  Wählen Sie auf der Seite **Wiederherstellungstyp auswählen** die Option **Anwendungen** aus, und klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Wenn <STRONG>Anwendungen</STRONG> nicht zur Auswahl steht, bedeutet dies, dass es sich bei der zur Wiederherstellung ausgewählten Sicherung um eine Sicherung auf Ordnerebene und nicht um eine Sicherung auf Volumeebene handelte. Sie müssen Sicherungen auf der Volumeebene durchführen, wenn Sie Exchange-Daten mit Windows Server Backup sichern.



7.  Überprüfen Sie, ob auf der Seite **Anwendung auswählen** im Feld **Anwendungen**Exchange ausgewählt ist. Klicken Sie auf **Details anzeigen**, um die Anwendungskomponenten der Sicherungen anzuzeigen. Wenn es sich bei der von Ihnen wiederherzustellenden Sicherung um die aktuellste Version handelt, wird das Kontrollkästchen **Keine Rollforward-Wiederherstellung der Anwendungsdatenbanken ausführen** angezeigt. Aktivieren Sie dieses Kontrollkästchen, wenn Sie die Rollforward-Wiederherstellung der Datenbank durch die Windows Server-Sicherung verhindern möchten, indem alle nicht übergebenen Transaktionsprotokolle übergeben werden. Klicken Sie auf **Weiter**.

8.  Geben Sie auf der Seite **Wiederherstellungsoptionen auswählen** an, wo die Daten wiederhergestellt werden sollen, und klicken Sie dann auf **Weiter**:
    
      - Wählen Sie **Am ursprünglichen Speicherort wiederherstellen** aus, wenn gesicherte Daten direkt am ursprünglichen Speicherort wiederhergestellt werden sollen. Wenn Sie diese Option verwenden, können Sie nicht auswählen, welche Datenbanken wiederhergestellt werden. Alle gesicherten Datenbanken auf dem Volume werden an ihrem ursprünglichen Speicherort wiederhergestellt.
    
      - Wählen Sie **An einem anderen Speicherort wiederherstellen** aus, wenn Sie einzelne Datenbanken und deren Dateien an einem angegebenen Speicherort wiederherstellen möchten. Klicken Sie auf **Durchsuchen**, um den alternativen Speicherort anzugeben. Wenn Sie diese Option auswählen, können Sie festlegen, welche Datenbanken wiederhergestellt werden. Nachdem die Datendateien wiederhergestellt wurden, können sie mit [Datenbankportabilität](database-portability-exchange-2013-help.md) in eine Wiederherstellungsdatenbank verschoben, manuell zurück an ihren ursprünglichen Speicherort verschoben oder an anderer Stelle in der Exchange-Organisation bereitgestellt werden. Wenn Sie eine Datenbank an einem alternativen Speicherort wiederherstellen, weist die wiederhergestellte Datenbank den Status "Dirty Shutdown" auf. Nach Abschluss des Wiederherstellungsvorgangs müssen Sie die Datenbank mit Eseutil.exe manuell in den Status "Clean Shutdown" versetzen.

9.  Überprüfen Sie auf der Seite **Bestätigung** die Wiederherstellungseinstellungen, und klicken Sie dann auf **Wiederherstellen**.

10. Auf der Seite **Wiederherstellungsstatus** können Sie den Status und Fortschritt der Wiederherstellung anzeigen.

11. Klicken Sie auf **Schließen**, wenn die Wiederherstellung abgeschlossen ist.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Auf der Seite **Wiederherstellungsstatus** wird angegeben, ob der Wiederherstellungsprozess erfolgreich abgeschlossen wurde. Gehen Sie folgendermaßen vor, um zusätzlich zu überprüfen, ob die Daten erfolgreich wiederhergestellt wurden:

  - Prüfen Sie das Zielverzeichnis der Wiederherstellung, und vergewissern Sie sich, dass die wiederhergestellten Daten vorhanden sind.

  - Überprüfen Sie anhand der Sicherungsprotokolle, ob der Auftrag auf dem Server, auf dem die Windows Server-Sicherung ausgeführt wurde, erfolgreich abgeschlossen wurde.

  - Öffnen Sie die Ereignisanzeige, und überprüfen Sie, ob im Anwendungsereignisprotokoll ein Wiederherstellungsabschlussereignis protokolliert wurde.

