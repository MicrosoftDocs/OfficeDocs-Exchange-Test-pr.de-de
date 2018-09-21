---
title: 'Konfig. der Eigenschaften von Postfachdatenbankkopien: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren der Eigenschaften von Postfachdatenbankkopien
ms:assetid: cf186561-ab2c-45c0-90f5-8d3ecfabeeac
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351151(v=EXCHG.150)
ms:contentKeyID: 50476758
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Eigenschaften von Postfachdatenbankkopien

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-01_

Jede Postfachdatenbankkopie verfügt über eigene Eigenschaften, die konfiguriert werden können. Dazu zählen gegebenenfalls die Dauer von Wiedergabeverzögerung und Abschneideverzögerung sowie die Aktivierungseinstellungsnummer. Weitere Informationen zu Wiedergabeverzögerung, Abschneideverzögerung und Aktivierungseinstellungsnummer finden Sie unter [Verwalten von Postfachdatenbankkopien](managing-mailbox-database-copies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankkopien" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Eigenschaften von Postfachdatenbankkopien mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Datenbank aus, das Sie konfigurieren möchten.

3.  Klicken Sie im Detailbereich unter **Datenbankkopien** für die gewünschte Datenbankkopie auf **Details anzeigen**. Anschließend können Sie Folgendes anzeigen oder konfigurieren:
    
      - **Datenbank**   Zeigt den Namen der ausgewählten Datenbank an.
    
      - **Postfachserver**   Zeigt den Namen des Postfachservers an, der die ausgewählte Datenbankkopie hostet.
    
      - **Inhaltsindexzustand**   Zeigt den aktuellen Zustand des Inhaltsindex für die ausgewählte Datenbankkopie an.
    
      - **Status**   Zeigt den aktuellen Status der ausgewählten Datenbankkopie an.
    
      - **Länge der Kopiewarteschlange**   Gibt die Anzahl der Protokolldateien an, die in die ausgewählte Datenbankkopie kopiert werden sollen. Dieses Feld ist nur für passive Datenbankkopien relevant.
    
      - **Länge der Wiedergabewarteschlange**   Gibt die Anzahl der Protokolldateien an, die in der ausgewählten Datenbankkopie wiedergegeben werden sollen. Dieses Feld ist nur für passive Datenbankkopien relevant.
    
      - **Fehlermeldungen**   Zeigt Fehlermeldungen für Datenbankkopien mit dem Status `Failed` oder `Failed and Suspended` an.
    
      - **Zeit des jüngsten verfügbaren Protokolls**   Zeigt den Datums- und Zeitstempel der zuletzt generierten Protokolldatei für die aktive Kopie der Datenbank. Dieses Feld ist nur für passive Datenbankkopien relevant. Bei aktiven (replizierten und eigenständigen) Datenbankkopien weist dieses Feld den Wert **nie** auf.
    
      - **Protokollzeit der letzten Überprüfung**   Zeigt den Datums- und Zeitstempel der letzten Protokolldatei, die vom Protokollinspektor für die ausgewählte Datenbankkopie überprüft wurde. Dieses Feld ist nur für passive Datenbankkopien relevant. Bei aktiven (replizierten und eigenständigen) Datenbankkopien weist dieses Feld den Wert **nie** auf.
    
      - **Zeit des letzten kopierten Protokolls**   Zeigt den Datums- und Zeitstempel der letzten Protokolldatei, die von der Protokollkopierfunktion für die ausgewählte Datenbankkopie kopiert wurde. Dieses Feld ist nur für passive Datenbankkopien relevant. Bei aktiven (replizierten und eigenständigen) Datenbankkopien weist dieses Feld den Wert **nie** auf.
    
      - **Zeit des letzten wiedergegebenen Protokolls**   Zeigt den Datums- und Zeitstempel der letzten Protokolldatei, die von der Protokollwiedergabe für die ausgewählte Datenbankkopie wiedergegeben wurde. Dieses Feld ist nur für passive Datenbankkopien relevant. Bei aktiven (replizierten und eigenständigen) Datenbankkopien weist dieses Feld den Wert **nie** auf.
    
      - **Aktivierungseinstellungsnummer**   Zeigt die Aktivierungseinstellungsnummer. Diese Nummer wird von Active Manager zur Auswahl der besten Kopie sowie zum Ausgleich der DAG durch Neuverteilung aktiver Postfachdatenbanken innerhalb der DAG mithilfe des Skripts **RedistributeActiveDatabases.ps1** verwendet. Der Wert für die Aktivierungspräferenz ist eine Zahl gleich oder größer 1, wobei 1 der ersten Präferenz entspricht. Die Nummer darf nicht größer sein als die Anzahl der Kopien der Postfachdatenbank.
    
      - **Wiedergabeverzögerung (in Tagen)**   Zeigt die Zeit, die der Microsoft Exchange-Informationsspeicherdienst warten soll, bevor Protokolldateien wiedergegeben werden, die vom Microsoft Exchange-Replikationsdienst in die passive Datenbankkopie kopiert wurden. Wenn Sie diesen Parameter auf einen Wert größer als 0 festlegen, wird eine verzögerte Datenbankkopie erstellt. Die Standardeinstellung für diesen Wert ist 0 Tage. Der maximal zulässige Wert für diese Einstellung ist 14 Tage. Der minimal zulässige Wert ist 0 Tage. Wenn Sie diesen Wert auf 0 festlegen, wird die Wiedergabeverzögerung deaktiviert.

## Konfigurieren der Eigenschaften von Postfachdatenbankkopien mithilfe der Shell

In diesem Beispiel wird eine Postfachdatenbankkopie mit der Aktivierungseinstellungsnummer 3 konfiguriert.

    Set-MailboxDatabaseCopy -Identity DB3\EX3 -ActivationPreference 3

In diesem Beispiel wird die auf Server1 gehostete Datenbankkopie DB1 mit einer Wiedergabe- und Abschneideverzögerungszeit von 1 Tag und der Aktivierungseinstellungsnummer 2 konfiguriert.

    Set-MailboxDatabaseCopy -Identity DB1\Server1 -ReplayLagTime 1.0:0:0 -TruncationLagTime 1.0:0:0 -ActivationPreference 2

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration einer Postfachdatenbankkopie zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Datenbanken**. Wählen Sie die geeignete Datenbank aus, und klicken Sie im Detailbereich auf **Details anzeigen**, um die Eigenschaften der Datenbankkopie anzuzeigen.

  - Führen Sie in der Shell den folgenden Befehl aus, um Konfigurationsinformationen zu einer Datenbankkopie anzuzeigen.
    
    ```powershell
Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List
```

## Weitere Informationen

[Set-MailboxDatabaseCopy](https://technet.microsoft.com/de-de/library/dd298104\(v=exchg.150\))

[Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\))

[Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\))

