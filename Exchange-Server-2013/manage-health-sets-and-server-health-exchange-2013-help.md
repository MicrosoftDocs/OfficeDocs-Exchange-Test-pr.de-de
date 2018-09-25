---
title: 'Verwalten von Integritätssätzen und Serverintegrität: Exchange 2013 Help'
TOCTitle: Verwalten von Integritätssätzen und Serverintegrität
ms:assetid: a4f84312-6cfa-4f17-9707-676aadab1143
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn482054(v=EXCHG.150)
ms:contentKeyID: 59889667
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Integritätssätzen und Serverintegrität

 

_**Gilt für:** Exchange Online, Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2013-12-02_

Mithilfe der integrierten Cmdlets für die Integritätsberichterstellung können Sie verschiedene Aufgaben im Zusammenhang mit verwalteter Verfügbarkeit ausführen wie z. B.:

  - Anzeigen der Integrität eines Servers oder einer Gruppe von Servern

  - Anzeigen einer Liste von Integritätssätzen

  - Anzeigen einer Liste von Tests, Monitoren und Antwortdiensten im Zusammenhang mit einem bestimmten Integritätssatz

  - Anzeigen einer Liste von Monitoren und ihrer aktuellen Integrität

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen der Serverintegrität

Über die Verwaltungsshell können Sie eine Übersicht der Integrität eines Servers abrufen, auf dem Exchange 2013 ausgeführt wird.

## Verwenden der Shell zum Anzeigen der Serverintegrität

Führen Sie einen der folgenden Befehle aus, um die Integritätssätze und Integritätsinformationen zu einem Server anzuzeigen, auf dem Exchange 2013 ausgeführt wird.


```powershell
Get-HealthReport -Identity <ServerName>
```

```powershell
    Get-ServerHealth -Identity <ServerName> | Format-Table Server,CurrentHealthSetState,Name,HealthSetName,AlertValue,HealthGroupName -Auto
```

Führen Sie einen der folgenden Befehle aus, um die Integritätssätze zu einem Server oder einer Database Availability Group anzuzeigen, auf dem/in der Exchange 2013 ausgeführt wird.


```powershell
Get-ExchangeServer | Get-HealthReport -RollupGroup
```

```powershell
Get-ExchangeServer | Get-HealthReport -RollupGroup -HealthSetName <HealthSet>
```

```powershell
    (Get-DatabaseAvailabiltyGroup <DAGName>).Servers | Get-HealthReport -RollupGroup
```

## Anzeigen einer Liste von Integritätssätzen

Ein Integritätssatz ist eine Gruppe von Monitoren, Tests und Antwortdiensten für eine Komponente, der bestimmt, ob die Komponente fehlerfrei oder fehlerhaft ist. Über die Verwaltungsshell können Sie die Liste der Integritätssätze auf einem Server mit ausgeführtem Exchange 2013 anzeigen.

## Anzeigen der Liste der Integritätssätze mithilfe der Verwaltungsshell

Führen Sie den folgenden Befehl aus, um die Integritätssätze auf einem Server mit ausgeführtem Exchange 2013 anzuzeigen.

```powershell
Get-HealthReport -Server <ServerName>
```

## Anzeigen der Tests, Monitore und Antwortdienste eines Integritätssatzes

Ein Integritätssatz ist eine Gruppe von Monitoren, Tests und Antwortdiensten für eine Komponente, der bestimmt, ob die Komponente fehlerfrei oder fehlerhaft ist. Über die Verwaltungsshell können Sie die Liste der zu einem Integritätssatz gehörigen Monitore, Tests und Antwortdienste auf einem Server mit ausgeführtem Exchange 2013 anzeigen.

## Anzeigen der Tests, Monitore und Antwortdienste eines Integritätssatzes mithilfe der Verwaltungsshell

Führen Sie den folgenden Befehl aus, um die zu einem Integritätssatz gehörigen Monitore, Tests und Antwortdienste auf einem Server mit ausgeführtem Exchange 2013 anzeigen.

```powershell
    Get-MonitoringItemIdentity -Server <ServerName> -Identity <HealthSetName> | Format-Table Identity,ItemType,Name -Auto
```

## Anzeigen einer Liste von Monitoren und ihrer aktuellen Integrität

Die Integrität eines Monitors wird mithilfe der "schlechtesten" Monitore im Integritätssatz gemeldet. Sie können die Details eines Integritätssatzes anzeigen, um zu prüfen, welche Monitore fehlerhaft und welche fehlerfrei sind.

## Anzeigen einer Liste der Monitore und ihrer aktuellen Integrität über die Verwaltungsshell

Führen Sie den folgenden Befehl aus, um die Liste der Monitore und ihrer aktuellen Integrität auf einem Server mit ausgeführtem Exchange 2013 anzeigen.

```powershell
    Get-ServerHealth -HealthSet <HealthSetName> -Server <ServerName> | Format-Table Name, AlertValue -Auto
```
