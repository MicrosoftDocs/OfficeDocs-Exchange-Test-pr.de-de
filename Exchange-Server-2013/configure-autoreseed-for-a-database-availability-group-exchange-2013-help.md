---
title: 'Konfigurieren von AutoReseed für eine Database Availability Group: Exchange 2013 Help'
TOCTitle: Konfigurieren von AutoReseed für eine Database Availability Group
ms:assetid: 4a8bd779-b52a-40ed-8040-4d76eabeb41e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ619303(v=EXCHG.150)
ms:contentKeyID: 50475619
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von AutoReseed für eine Database Availability Group

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-04-15_

AutoReseed ist eine Funktion für die schnelle Wiederherstellung der Datenbankredundanz nach einem Datenträgerausfall. Wenn ein Datenträger ausfällt, wird für die auf diesem Datenträger gespeicherten Datenbankkopien automatisch ein erneutes Seeding auf einen vorkonfigurierten Ersatzdatenträger auf dem Postfachserver durchgeführt. Sie können die Schritte in diesem Thema ausführen, um die AutoReseed-Funktion für eine Database Availability Group (DAG) zu konfigurieren.


> [!WARNING]
> Das AutoReseed-Feature führt keine erforderlichen Konfigurationsaufgaben für Sie durch. Die ordnungsgemäße Installation der Datenträger, das Hinzufügen von Ersatzdatenträgern zum System, das Austauschen fehlerhafter Datenträger sowie die Formatierung neuer Datenträger muss manuell durch einen Administrator ausgeführt werden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf DAGs finden Sie unter [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Database Availability Groups" im Thema [Berechtigungen für hohe Verfügbarkeit und Ausfallsicherheit von Standorten](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Eine einzelne logische Datenträgerpartition pro physischem Datenträger muss verwendet werden.

  - Es muss die in den nachstehenden Schritten beschriebene spezifische Datenbank- und Protokollordnerstruktur verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Konfigurieren von Stammpfaden für Datenbanken und Volumes

Der erste Schritt umfasst das Konfigurieren der Stammverzeichnisse für die Datenbanken (*AutoDagDatabasesRootFolderPath*) und Volumes (*AutoDagVolumesRootFolderPath*), die von der DAG verwendet werden. Die Standardverzeichnisse lauten "C:\\ExchangeDatabases" und "C:\\ExchangeVolumes". Sie können diesen Schritt auslassen, wenn Sie die Standardpfade verwenden.

In diesem Beispiel wird die Konfiguration des Stammpfads für die Datenbanken veranschaulicht.

    Set-DatabaseAvailabilityGroup DAG1 -AutoDagDatabasesRootFolderPath "C:\ExchDbs"

In diesem Beispiel wird die Konfiguration des Stammpfads für die Speichervolumes veranschaulicht.

    Set-DatabaseAvailabilityGroup DAG1 -AutoDagVolumesRootFolderPath "C:\ExchVols"

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Konfiguration der Stammpfade für Datenbanken und Volumes zu überprüfen:

    Get-DatabaseAvailabilityGroup DAG1 | Format-List *auto*

Die Ausgabe von *AutoDagDatabasesRootFolderPath* und *AutoDagVolumesRootFolderPath* sollte die konfigurierten Pfade zeigen.

## Schritt 2: Konfigurieren der Anzahl von Datenbanken pro Volume

Als Nächstes konfigurieren Sie die Anzahl von Datenbanken pro Volume (*AutoDagDatabaseCopiesPerVolume*) für die DAG.

In diesem Beispiel wird veranschaulicht, wie Sie diese AutoReseed-Einstellung für eine DAG festlegen, die mit 4 Datenbanken pro Volume konfiguriert ist.

    Set-DatabaseAvailabilityGroup DAG1 -AutoDagDatabaseCopiesPerVolume 4

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Konfiguration der Anzahl von Datenbanken pro Volume zu überprüfen:

    Get-DatabaseAvailabilityGroup DAG1 | Format-List *auto*

Die Ausgabe für *AutoDagDatabaseCopiesPerVolume* sollte den konfigurierten Wert zeigen.

## Schritt 3: Erstellen der Stammverzeichnisse für Datenbanken und Volumes

Als Nächstes erstellen Sie die Verzeichnisse, die den in Schritt 1 konfigurierten Stammverzeichnissen entsprechen. Im folgenden Beispiel wird gezeigt, wie Sie die Standardverzeichnisse mithilfe der Eingabeaufforderung erstellen.

    md C:\ExchangeDatabases
    md C:\ExchangeVolumes

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Konfiguration der Stammverzeichnisse für Datenbanken und Volumes zu überprüfen:

    Dir C:\

Die erstellten Verzeichnisse werden in der Ausgabeliste angezeigt.

## Schritt 4: Bereitstellen der Volumeordner

Stellen Sie jedes Volume, das für Datenbanken eingesetzt wird (Ersatzvolumes eingeschlossen), mithilfe der Windows-Datenträgerverwaltung (diskmgmt.msc) in einem bereitgestellten Ordner unter "C:\\ExchangeVolumes\\" bereit. Wenn beispielsweise 2 Volumes mit Datenbanken und 1 Ersatzvolume vorliegen, müssen Sie die Volumes in den folgenden bereitgestellten Ordnern bereitstellen:

  - C:\\ExchangeVolumes\\Volume1

  - C:\\ExchangeVolumes\\Volume2

  - C:\\ExchangeVolumes\\Volume3

Als Namen für die bereitgestellten Ordner kann jeder beliebige Name verwendet werden, vorausgesetzt, die Ordner werden unter dem Pfad des Stammdatenträgers bereitgestellt.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Bereitstellung der Volumeordner zu überprüfen:

    Dir C:\

Die bereitgestellten Volumes sollten in der Ausgabeliste angezeigt werden.

## Schritt 5: Erstellen der Datenbankordner

Im nächsten Schritt erstellen Sie die Datenbankverzeichnisse unterhalb des Stammpfads "C:\\ExchangeDatabases". Mit diesem Beispiel wird veranschaulicht, wie in jedem Datenträger Verzeichnisse für eine Speicherkonfiguration mit vier Datenbanken erstellt werden können.

```
    md c:\ExchangeDatabases\db001
```

```
    md c:\ExchangeDatabases\db002
```

```
    md c:\ExchangeDatabases\db003
```

```
    md c:\ExchangeDatabases\db004
```

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Bereitstellung der Datenbankordner zu überprüfen:

    Dir C:\ExchangeDatabases

Die erstellten Verzeichnisse werden in der Ausgabeliste angezeigt.

## Schritt 6: Erstellen von Bereitstellungspunkten für die Datenbanken

Erstellen Sie die Bereitstellungspunkte für jede Datenbank, und verknüpften Sie den Bereitstellungspunkt mit dem richtigen Volume. Beispielsweise sollte sich der bereitgestellte Ordner für "db001" im Verzeichnis "C:\\ExchangeDatabases\\db001" befinden. Sie können zur Ausführung dieser Aufgabe "diskmgmt.msc" oder "mountvol.exe" verwenden. In diesem Beispiel wird veranschaulicht, wie "db001" mithilfe von "mountvol.exe" in "C:\\ExchangeDatabases\\db001" bereitgestellt wird.

    Mountvol.exe c:\ExchangeDatabases\db001 \\?\Volume (GUID)

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Erstellung der Bereitstellungspunkte für die Datenbank zu überprüfen:

    Mountvol.exe C:\ExchangeDatabases\db001 /L

Das bereitgestellte Volume sollte in der Liste der Bereitstellungspunkte angezeigt werden.

## Schritt 7: Erstellen der Datenbankverzeichnisstruktur

Als Nächstes erstellen Sie zwei Verzeichnisse unterhalb der in Schritt 5 erstellten Ordner: einen Ordner für jede Datenbank und einen Ordner für den Protokolldatenstrom jeder Datenbank, der auf demselben Volume gespeichert wird. Sie müssen das folgende Format für Ihre Verzeichnisstruktur verwenden:

C:\\\< *Datenbankordnername*\>\\*Datenbankname*\\\<*Datenbankname*\>.db

C:\\\< *Datenbankordnername*\>\\*Datenbankname*\\\<*Datenbankname*\>.db

In diesem Beispiel wird gezeigt, wie Sie Verzeichnisse für 4 Datenbanken erstellen, die auf Volume 1 gespeichert werden:

```
    md c:\ExchangeDatabases\db001\db001.db
```

```
    md c:\ExchangeDatabases\db001\db001.log
```

```
    md c:\ExchangeDatabases\db002\db002.db
```

```
    md c:\ExchangeDatabases\db002\db002.log
```

```
    md c:\ExchangeDatabases\db003\db003.db
```

```
    md c:\ExchangeDatabases\db003\db003.log
```

```
    md c:\ExchangeDatabases\db004\db004.db
```

```
    md c:\ExchangeDatabases\db004\db004.log
```

Führen Sie die obigen Befehle für die Datenbanken auf jedem Volume aus.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Erstellung der Datenbankverzeichnisstruktur zu überprüfen:

    Dir C:\ExchangeDatabases /s

Die erstellten Verzeichnisse werden in der Ausgabeliste angezeigt.

## Schritt 8: Erstellen von Datenbanken

Erstellen Sie Datenbanken mit Protokoll- und Datenbankpfaden, die mit den entsprechenden Ordnern konfiguriert sind. In diesem Beispiel wird gezeigt, wie Sie eine Datenbank erstellen, die im neu erstellten Verzeichnis und in der Bereitstellungspunktstruktur gespeichert wird.

    New-MailboxDatabase -Name db001 -Server MBX1 -LogFolderPath C:\ExchangeDatabases\db001\db001.log -EdbFilePath C:\ExchangeDatabases\db001\db001.db\db001.edb

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um die erfolgreiche Erstellung der Datenbanken im entsprechenden Ordner zu überprüfen:

    Get-MailboxDatabase db001 | Format List *path*

Die zurückgegebenen Datenbankeigenschaften sollten anzeigen, dass Datenbankdatei und -protokolldateien in den obigen Ordnern gespeichert werden.

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration der AutoReseed-Funktion für eine DAG zu überprüfen:

1.  Führen Sie den folgenden Befehl aus, um die ordnungsgemäße Konfiguration der DAG zu überprüfen:
    
        Get-DatabaseAvailabilityGroup DAG1 | Format-List *auto*

2.  Führen Sie den folgenden Befehl aus, um die ordnungsgemäße Konfiguration der Verzeichnisstruktur zu überprüfen (nachfolgend werden die Standardpfade angezeigt; ersetzen Sie die Pfade ggf. durch die von Ihnen verwendeten Pfade):
    
```
	Dir c:\ExchangeDatabases /s
```

```
	Dir c:\ExchangeVolumes /s
```

