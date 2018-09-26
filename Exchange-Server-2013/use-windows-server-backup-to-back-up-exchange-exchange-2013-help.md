---
title: 'Sichern von Exchange mithilfe der Windows Server-Sicherung: Exchange 2013 Help'
TOCTitle: Sichern von Exchange mithilfe der Windows Server-Sicherung
ms:assetid: 188a8291-0a41-4ca2-b6d2-94242e2b1ffc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876854(v=EXCHG.150)
ms:contentKeyID: 50475176
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Sichern von Exchange mithilfe der Windows Server-Sicherung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-18_

Mithilfe der Windows Server-Sicherung können Sie Exchange-Datenbanken sichern und wiederherstellen. Exchange enthält ein Plug-In für die Windows Server-Sicherung, mit der Sie VSS-basierte Sicherungen (Volume Shadow Copy Service, Volumenschattenkopie-Dienst) von Exchange-Daten erstellen können.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute, zuzüglich der erforderlichen Zeit für das Sichern der Daten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Windows Server-Sicherungsfunktion muss auf dem lokalen Computer installiert sein.

  - Während der Sicherung wird eine Konsistenzprüfung der Exchange-Datendateien ausgeführt, um sicherzustellen, dass sich die Dateien in einem funktionierenden Zustand befinden und für die Wiederherstellung verwendet werden können. Wenn die Konsistenzprüfung erfolgreich ausgeführt werden kann, sind die Exchange-Daten für die Wiederherstellung aus dieser Sicherung verfügbar. Wenn bei der Konsistenzprüfung ein Fehler auftritt, stehen die Exchange-Daten für die Wiederherstellung nicht zur Verfügung. Die Windows Server-Sicherung führt die Konsistenzprüfung für die Momentaufnahme aus, die für die Sicherung erstellt wurde. Das bedeutet, dass die Konsistenz der Sicherung bekannt ist, bevor Dateien aus der Momentaufnahme auf den Sicherungsdatenträger kopiert werden, und dass der Benutzer über die Ergebnisse der Konsistenzprüfung informiert wird.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Sichern von Exchange mithilfe der Windows Server-Sicherung

1.  Starten Sie die Windows Server-Sicherung.

2.  Wählen Sie **Lokale Sicherung** aus.

3.  Klicken Sie im Aktionsbereich auf **Einmalsicherung…**, um den Einmalsicherungsassistenten zu starten.

4.  Wählen Sie auf der Seite **Sicherungsoptionen** die Option **Unterschiedliche Optionen** aus, und klicken Sie dann auf **Weiter**.

5.  Wählen Sie auf der Seite **Sicherungskonfiguration auswählen** die Option **Benutzerdefiniert** aus, und klicken Sie auf **Weiter**.

6.  Klicken Sie auf der Seite **Sicherungselemente auswählen** auf **Elemente hinzufügen**, um das/die zu sicherende(n) Volume(s) auszuwählen, und klicken Sie dann auf **OK**.
    

    > [!NOTE]
    > Wählen Sie Volumes und nicht einzelne Ordner aus. Die einzige Möglichkeit zur Durchführung einer Sicherung oder Wiederherstellung auf Anwendungsebene ist, ein gesamtes Volume auszuwählen.



7.  Klicken Sie auf **Erweiterte Einstellungen**. Klicken Sie auf der Registerkarte **Ausschlüsse** auf **Ausschluss hinzufügen**, um Dateien oder Dateitypen hinzuzufügen, die Sie von der Sicherung ausschließen möchten.
    

    > [!NOTE]
    > Standardmäßig sind in der Sicherung die Volumes enthalten, auf denen sich Betriebssystemkomponenten oder Anwendungen befinden. Sie können von der Sicherung nicht ausgeschlossen werden.



8.  Wählen Sie auf der Registerkarte **VSS-EinstellungenVollständige VSS-Sicherung** aus, und klicken Sie dann auf **OK** und **Weiter**.

9.  Wählen Sie auf der Seite **Zieltyp angeben** den Ort aus, an dem die Sicherung gespeichert werden soll, und klicken Sie dann auf **Weiter**.
    
      - Wenn Sie **Lokale Laufwerke** auswählen, wird die Seite **Sicherungsziel auswählen** angezeigt. Wählen Sie in der Dropdownliste **Sicherungsziel** eine Option aus, und klicken Sie dann auf **Weiter**.
    
      - Wenn Sie **Freigegebener Remoteordner** auswählen, wird die Seite **Remoteordner angeben** angezeigt. Geben Sie einen UNC-Pfad für die Sicherungsdateien an, und konfigurieren Sie Einstellungen für die Zugriffssteuerung. Wählen Sie **Nicht vererben**, wenn der Zugriff auf die Sicherung auf ein bestimmtes Konto beschränkt werden soll. Geben Sie einen Benutzernamen und ein Kennwort für ein Konto an, das über Schreibberechtigungen auf dem Computer verfügt, auf dem der Remoteordner gehostet wird, und klicken Sie dann auf **OK**. Wählen Sie alternativ **Vererben** aus, wenn alle Benutzer mit Zugriff auf den Remoteordner auf die Sicherung zugreifen können sollen. Klicken Sie auf **Weiter**.

10. Überprüfen Sie die Sicherungseinstellungen auf der Seite **Bestätigung**, und klicken Sie dann auf **Sichern**.

11. Auf der Seite **Sicherungsprozess** werden der Status und der Fortschritt der Sicherung angezeigt.

12. Klicken Sie auf **Schließen**, um die Seite **Sicherungsfortschritt** jederzeit zu beenden. Laufende Sicherungen werden im Hintergrund fortgesetzt.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Sicherung der Daten zu überprüfen:

  - Auf dem Server, auf dem die Windows Server-Sicherung ausgeführt wurde, wird der letzte Sicherungsstatus, der "Erfolgreich" lauten sollte, angezeigt. Sie können auch durch Anzeigen der Windows Server-Sicherungsprotokolle überprüfen, ob die Sicherung erfolgreich abgeschlossen wurde.

  - Öffnen Sie die Ereignisanzeige, und überprüfen Sie, ob im Anwendungsereignisprotokoll ein Sicherungsabschlussereignis protokolliert wurde.

  - Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um zu überprüfen, ob alle Datenbanken auf dem/n ausgewählten Volume(s) erfolgreich gesichert wurden:
    
    ```powershell
        Get-MailboxDatabase -Server <ServerName> -Status | fl Name,*FullBackup
    ```
    
    Die Eigenschaften *SnapshotLastFullBackup* und *LastFullBackup* der Datenbank geben an, wann die letzte erfolgreiche Sicherung durchgeführt wurde, und ob es sich um eine vollständige VSS-Sicherung handelte.

