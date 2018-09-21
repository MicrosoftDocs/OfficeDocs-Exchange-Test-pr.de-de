---
title: 'Aktiv. u. Konfig. v. Warteschlangen nach Priorität: Exchange 2013-Hilfe'
TOCTitle: Aktivieren und Konfigurieren von Warteschlangen nach Priorität
ms:assetid: 1975d85d-2f1d-4852-8d19-e74ba4ba3853
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ891104(v=EXCHG.150)
ms:contentKeyID: 51409272
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren und Konfigurieren von Warteschlangen nach Priorität

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

*Prioritätswarteschlange* ist ein Feature von Microsoft Exchange Server 2013, mit dem die Nachrichtenpriorität, die vom Absender in Microsoft Outlook oder Outlook Web Access konfiguriert wird, die Verarbeitung der Nachrichten durch den Transportdienst auf dem Postfachserver beeinflussen kann. Bei aktivierter Prioritätswarteschlange werden Nachrichten mit hoher Priorität vor Nachrichten mit normaler Priorität und Nachrichten mit normaler Priorität vor Nachrichten mit niedriger Priorität an das jeweilige Ziel übermittelt. Weitere Informationen finden Sie unter [Prioritätswarteschlangen](priority-queuing-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - Änderungen, die Sie an der Anwendungskonfigurationsdatei "EdgeTransport.exe.config" vornehmen, werden nach einem Neustart des Microsoft Exchange-Transportdiensts angewendet.

  - Wenn Sie den Microsoft Exchange-Transportdienst neu starten, wird der E-Mail-Fluss auf dem Server zeitweise unterbrochen.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config\&quot;-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config\&quot; auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktivieren und Konfigurieren der Prioritätswarteschlange in der Datei "EdgeTransport.exe.config" mithilfe der Eingabeaufforderung

1.  Führen Sie an einer Eingabeaufforderung folgenden Befehl aus, um die Anwendungskonfigurationsdatei "EdgeTransport.exe.config" im Editor zu öffnen:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

2.  Suchen Sie im Abschnitt `<appSettings>` die folgenden Schlüssel.
    
        <add key="PriorityQueuingEnabled" value="false" />
        <add key="MaxPerDomainHighPriorityConnections" value="3" />
        <add key="MaxPerDomainNormalPriorityConnections" value="15" />
        <add key="MaxPerDomainLowPriorityConnections" value="2" />
        <add key="HighPriorityMessageExpirationTimeout" value="8:00:00" />
        <add key="NormalPriorityMessageExpirationTimeout" value="2.00:00:00" />
        <add key="LowPriorityMessageExpirationTimeout" value="2.00:00:00" />
        <add key="HighPriorityDelayNotificationTimeout" value="00:30:00" />
        <add key="NormalPriorityDelayNotificationTimeout" value="4:00:00" />
        <add key="LowPriorityDelayNotificationTimeout" value="8:00:00" />
        <add key="MaxHighPriorityMessageSize" value="250KB" />
    
    Verwenden Sie zum Aktivieren der Prioritätswarteschlange im Transportdienst auf dem Postfachserver den folgenden Wert:
    
    ```command line
<add key="PriorityQueuingEnabled" value="true" />
```
    
    Konfigurieren Sie die übrigen Werte für Prioritätswarteschlangen, oder behalten Sie die Standardwerte bei.

3.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

4.  Starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:
    
        net stop MSExchangeTransport && net start MSExchangeTransport

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Prioritätswarteschlange erfolgreich aktiviert und konfiguriert wurde:

1.  Stellen Sie sicher, dass der Schlüssel **PriorityQueueinEnabled** in der Datei "EdgeTransport.exe.config" den Wert `"true"` aufweist.

2.  Erstellen Sie in Outlook eine Testnachricht mit hoher Priorität, deren Größe den im Schlüssel **MaxHighPriorityMessageSize** angegebenen Wert übersteigt, und prüfen Sie, ob die Nachricht mit normaler Priorität zugestellt wird.

3.  Versuchen Sie zu ermitteln, ob Nachrichten höherer Priorität vor den Nachrichten niedrigerer Priorität an denselben Empfänger oder dasselbe Ziel zugestellt werden. Sie können versuchen, mehrere ähnliche Testnachrichten mit unterschiedlichen Prioritätswerten über mehrere Postfächer gleichzeitig an denselben Empfänger zu senden.

