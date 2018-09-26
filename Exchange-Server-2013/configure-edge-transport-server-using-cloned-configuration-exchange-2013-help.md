---
title: 'Konfig. der Edge-Transport-Server mit geklonter Konfig.: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren der Edge-Transport-Server mithilfe geklonter Konfiguration
ms:assetid: 0bbc83e3-e5e8-4480-a8a6-15f035360856
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996008(v=EXCHG.150)
ms:contentKeyID: 61180463
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Edge-Transport-Server mithilfe geklonter Konfiguration

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-13_

Sie können die vorhandenen Exchange Management Shell-Skripts (zu finden unter %ExchangeInstallPath%Scripts) verwenden, um die Konfiguration eines Edge-Transport-Servers zu duplizieren. Dieser Vorgang wird als *geklonte Konfiguration* bezeichnet. *Geklonte Konfiguration* bedeutet, neue Edge-Transport-Server basierend auf den Konfigurationsinformationen eines zuvor konfigurierten Quellservers bereitzustellen. Die Konfigurationsinformationen des zuvor konfigurierten Quellservers werden kopiert und in eine XML-Datei exportiert, die dann auf den Zielserver importiert wird. Einen Überblick über diesen Vorgang finden Sie unter [Geklonte Edge-Transport-Server-Konfiguration](edge-transport-server-cloned-configuration-exchange-2013-help.md).

Die Konfigurationsinformationen des Edge-Transport-Servers werden in Active Lightweight Directory Services (AD LDS) gespeichert und nicht zwischen mehreren Edge-Transport-Servern repliziert. Mit einer geklonten Konfiguration können Sie sicherstellen, dass jeder in Ihrem Umkreisnetzwerk eingesetzte Edge-Transport-Server dieselbe Konfiguration verwendet.

Zwei Shellskripts führen geklonte Konfigurationsaufgaben durch:

  - **ExportEdgeConfig.ps1**   Dieses Skript exportiert alle vom Benutzer konfigurierten Einstellungen und Daten von einem Edge-Transport-Server und speichert die Daten in einer XML-Datei.

  - **ImportEdgeConfig.ps1**   Während der Konfigurationsüberprüfung überprüft das Skript "ImportEdgeConfig.ps1" die exportierte XML-Datei daraufhin, ob serverspezifische Exporteinstellungen für den Zielserver gelten. Wenn Einstellungen geändert werden müssen, schreibt das Skript die ungültigen Einstellungen in eine Antwortdatei, die Sie so ändern können, dass die Zielserverinformationen angegeben werden, die während der Importphase der Konfiguration verwendet werden. Während der Importphase der Konfiguration importiert das Skript alle benutzerkonfigurierten Einstellungen und Daten, die in der XML-Zwischendatei gespeichert sind, die vom Skript ExportEdgeConfig.ps1 erstellt wurde.

Diese Skripts befinden sich im Ordner % ExchangeInstallPath%Scripts.

## Bevor Sie beginnen

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - In einer geklonten Konfiguration werden nicht die Edge-Abonnementeinstellungen eines Servers dupliziert. EdgeSync-Zertifikate werden nicht geklont. Sie müssen den EdgeSync-Vorgang separat für jeden Edge-Transport-Server durchführen. EdgeSync überschreibt alle Einstellungen, die sowohl in den geklonten Konfigurationsinformationen als auch in den EdgeSync-Replikationsinformationen enthalten sind.

  - Wenn Sendeconnectors für die Verwendung von Anmeldeinformationen konfiguriert sind, wird das Kennwort als verschlüsselte Zeichenfolge in die XML-Zwischendatei geschrieben. Sie können den Parameter *-key* zusammen mit den Skripts "ImportEdgeConfig.ps1" und "ExportEdgeConfig.ps1" zum Angeben der 32 Byte langen Zeichenfolge verwenden, die zur Kennwortver- und -entschlüsselung verwendet werden soll. Wenn der Parameter *-key* nicht verwendet wird, wird ein Standardverschlüsselungsschlüssel verwendet.

  - Die Shell kann nur für diesen Vorgang verwendet werden.Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Exportieren Sie die Quellserver-Konfigurationsdaten in eine Datei auf dem Quellserver.

1.  Kopieren Sie das Skript "ExportEdgeConfig.ps1" in den Stammordner Ihres Benutzerprofils auf dem Quellserver.

2.  Verwenden Sie die folgende Syntax, um die Quellserver-Konfigurationsdaten in eine Datei auf dem Quellserver zu exportieren.
    
    ```powershell
    ./ExportEdgeConfig.ps1 -CloneConfigData:"<configuration file>"
    ```
    
    Wenn Sie z. B. die Quellserver-Konfigurationsdaten in die Datei C:\\CloneConfigData.xml exportieren möchten, führen Sie den folgenden Befehl aus.
    
    ```powershell
        ./ExportEdgeConfig.ps1 -CloneConfigData:"C:\CloneConfigData.xml"
    ```
    
## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Der Export der Konfigurationsdaten in eine Datei war erfolgreich, wenn die Bestätigungsmeldung "Edge-Konfigurationsdaten wurden erfolgreich exportiert nach: \<Pfad der Ausgabedatei\>" angezeigt wird.

## Schritt 2: Überprüfen Sie die Konfigurationsdatei, und erstellen Sie eine Antwortdatei auf dem Zielserver.

1.  Kopieren Sie die Quellserver-Konfigurationsdatei, die Sie im vorhergehenden Schritt exportiert haben, auf den Edge-Transport-Server.

2.  Kopieren Sie das Skript "ImportEdgeConfig.ps1" in den Stammordner Ihres Benutzerprofils auf dem Zielserver.

3.  Verwenden Sie die folgende Syntax, um die Konfigurationsdatei zu überprüfen und mithilfe der Ergebnisse eine Antwortdatei auf dem Zielserver zu erstellen.
    
    ```powershell
        ./ImportEdgeConfig.ps1 -CloneConfigData:"<configuration file>" -IsImport $false -CloneConfigAnswer:"<answer file>"
    ```
    
    Wenn Sie z. B. die Konfigurationsdatei C:\\CloneConfigData.xml überprüfen und die Antwortdatei C:\\CloneConfigAnswer.xml erstellen möchten, führen Sie den folgenden Befehl aus.
    
    ```powershell
        ./ImportEdgeConfig.ps1 -CloneConfigData:"C:\CloneConfigData.xml" -IsImport $false -CloneConfigAnswer:"C:\CloneConfigAnswer.xml"
    ```
    
4.  Öffnen Sie die Antwortdatei, und ändern Sie ggf. alle Einstellungen, die für den Zielserver ungültig sind. Wenn keine Änderungen erforderlich sind, weist die Antwortdatei keine Einträge auf. Speichern Sie Ihre Änderungen.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Die Überprüfung der Konfigurationsdatei und die Erstellung einer Antwortdatei waren erfolgreich, wenn die Bestätigungsmeldung "Die Antwortdatei wurde erfolgreich erstellt" angezeigt wird.

## Schritt 3 – Import der Konfigurationsdatei auf dem Zielserver

Verwenden Sie die folgende Syntax, um die Konfigurationsdatei auf dem Zielserver zu importieren.

```powershell
    ./ImportEdgeConfig.ps1 -CloneConfigData:"<Configuration file>" -IsImport $true -CloneConfigAnswer:"<answer file>"
```

Wenn Sie z. B. die Konfigurationsdatei C:\\CloneConfigData.xml importieren und dafür die Antwortdatei C:\\CloneConfigAnswer.xml verwenden möchten, führen Sie den folgenden Befehl aus.

```powershell
    ./ImportEdgeConfig.ps1 -CloneConfigData:"C:\CloneConfigData.xml" -IsImport $true -CloneConfigAnswer:"C:\CloneConfigAnswer.xml"
```

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Der Import der Konfigurationsdatei auf dem Zielserver war erfolgreich, wenn die Bestätigungsmeldung "Der Import der Edge-Konfigurationsinformationen war erfolgreich" angezeigt wird.

