---
title: 'Konfigurieren von Get-QueueDigest: Exchange 2013 Help'
TOCTitle: Konfigurieren von Get-QueueDigest
ms:assetid: f730c520-4ba5-4a15-8846-132bff500bb8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn505733(v=EXCHG.150)
ms:contentKeyID: 59634176
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Get-QueueDigest

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Mit dem Cmdlet **Get-QueueDigest** können Sie Informationen zu manchen oder allen Warteschlangen in Ihrer Exchange-Organisation mit nur einem einzigen Befehl anzeigen.

Standardmäßig sind die vom Cmdlet **Get-QueueDigest** zurückgegebenen Ergebnisse zwischen ein und zwei Minuten alt. Diese Werte werden durch die folgenden Einstellungen gesteuert:

  - **QueueLoggingInterval-Schlüssel in EdgeTransport.exe.config**   Dieser Schlüssel gibt an, wie häufig Warteschlangendaten protokolliert werden, und steht für **Get-QueueDigest** zur Verfügung. Der Standardwert ist `00:01:00` (eine Minute). Geben Sie einen Wert als Zeitraum an: *hh:mm:ss*, wobei *h* = Stunden, *m* = Minuten und *s* = Sekunden angibt. Dieser Schlüssel ist standardmäßig nicht in der Datei "EdgeTransport.exe.config" vorhanden.

  - **QueueDiagnosticsAggregationInterval-Parameter von Set-TransportConfig**   Dieser Parameter gibt an, wie häufig Warteschlangendaten zwischen Postfachservern ausgetauscht werden. Der Standardwert ist `00:01:00` (eine Minute). Geben Sie einen Wert als Zeitraum an: *hh:mm:ss*, wobei *h* = Stunden, *m* = Minuten und *s* = Sekunden angibt.

Die Schlüsselsumme von **QueueLoggingInterval** und die Parameterwerte von *QueueDiagnosticsAggregationInterval* bestimmen das maximale Alter der von **Get-QueueDigest** zurückgegebenen Ergebnisse.

Außerdem gibt **Get-QueueDigest** Ergebnisse unterschiedlich basierend auf Typ und Status der Warteschlange zurück. Beispielsweise werden die folgenden Warteschlangen in den Ergebnissen angezeigt, solange sie mindestens eine Nachricht enthalten:

  - die Übermittlungswarteschlange, die Nicht-erreichbar-Warteschlange und die Warteschlange für nicht verarbeitbare Nachrichten (dauerhafte Warteschlange).

  - Zustellungswarteschlangen mit dem Status "Angehalten" (Warteschlangen, die von einem Administrator manuell angehalten wurden).

Standardmäßig werden Zustellungswarteschlangen mit dem Status "Aktiv", "Verbinden", "Bereit" und "Wiederholen" nur dann in den Ergebnissen zurückgegeben, wenn die Warteschlange mindestens 10 Nachrichten enthält. Dieser Wert wird über den Schlüssel **QueueLoggingThreshold** in der Datei "EdgeTransport.exe.config" gesteuert. Sie können einen kleineren oder größeren ganzzahligen Wert angeben. Dieser Schlüssel ist standardmäßig nicht in der Datei "EdgeTransport.exe.config" vorhanden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Informationen zu den benötigten Exchange-Berechtigungen für **Set-TransportConfig** in der Exchange-Verwaltungsshell finden Sie unter "Transportkonfiguration" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Exchange-Berechtigungen gelten nicht für Änderungen an der Datei "EdgeTransport.exe.config" und den Neustart des Microsoft Exchange-Transportdiensts. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - Änderungen, die Sie an der Datei "EdgeTransport.exe.config" vornehmen, werden nach einem Neustart des Microsoft Exchange-Transportdiensts angewendet. Wenn Sie diesen Dienst neu starten, wird die Nachrichtenübermittlung auf dem Server zeitweise unterbrochen.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config\&quot;-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config\&quot; auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Änderungen, die Sie mithilfe von **Set-TransportConfig** vornehmen, wirken sich auf alle Postfachserver in Ihrer Organisation aus. Änderungen, die Sie an der Datei "EdgeTransport.exe.config" vornehmen, betreffen nur den lokalen Postfachserver.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren von Get-QueueDigest

1.  Geben Sie in einem Eingabeaufforderungsfenster den folgenden Befehl ein, um die Datei "EdgeTransport.exe.config" in Notepad zu öffnen:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

2.  Fügen Sie im Abschnitt `<appSettings>` einen oder beide der folgenden Schlüssel hinzu.
    
        <add key="QueueLoggingThreshold" value="<integer>" />
        <add key="QueueLoggingInterval" value="<hh:mm:ss>" />
    
    Um beispielsweise den Wert von **QueueLoggingThreshold** auf 1 einzustellen und den Wert von **QueueLoggingInterval** auf 30 Sekunden, verwenden Sie die folgenden Angaben:
    
        <add key="QueueLoggingThreshold" value="1" />
        <add key="QueueLoggingInterval" value="00:00:30" />

3.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

4.  Starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:
    
        net stop MSExchangeTransport && net start MSExchangeTransport

5.  Um den Wert des Parameters *QueueDiagnosticsAggregationInterval* in der Exchange-Verwaltungsshell zu ändern, verwenden Sie folgende Syntax:
    
        Set-TransportConfig -QueueDiagnosticsAggregationInterval <hh:mm:ss>
    
    Führen Sie beispielsweise den folgenden Befehl aus, um den Wert auf 30 Sekunden zu ändern:
    
        Set-TransportConfig -QueueDiagnosticsAggregationInterval 00:00:30

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Sie **Get-QueueDigest** erfolgreich konfiguriert haben:

1.  Überprüfen Sie die Werte der Schlüssel **QueueLoggingThreshold** und **QueueLoggingInterval** in der Datei "EdgeTransport.exe.config". Wenn die Schlüssel nicht vorhanden sind, werden die Standardwerte verwendet.

2.  Überprüfen Sie den Wert des Parameters *QueueDiagnosticsAggregationInterval*, indem Sie den folgenden Befehl ausführen:
    
        Get-TransportConfig | Format-List *queue*

