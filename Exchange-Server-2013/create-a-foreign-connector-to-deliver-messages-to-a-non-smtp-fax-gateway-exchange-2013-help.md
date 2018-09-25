---
title: 'Erstellen fremder Connectors z. Übermitt. v. Nachr. an Nicht-SMTP-Faxgateway'
TOCTitle: Erstellen eines fremden Connectors zum Übermitteln von Nachrichten an ein Nicht-SMTP-Faxgateway
ms:assetid: 589db487-3c4c-409a-92e3-c78dd8f639b6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ710163(v=EXCHG.150)
ms:contentKeyID: 50475738
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines fremden Connectors zum Übermitteln von Nachrichten an ein Nicht-SMTP-Faxgateway

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-17_

Es kann Szenarien geben, in denen Nachrichten an ein Faxgateway gesendet und von diesem empfangen werden, das nicht SMTP als primären Transportmechanismus verwendet. Führen Sie die in diesem Verfahren beschriebenen Schritte aus, um einen fremden Connector zu erstellen, der den Nachrichtenversand an das und den Empfang von Nachrichten durch das fremde System ermöglicht.


> [!TIP]
> Wenn ausgehende Nachrichten an ein Nicht-SMTP-System gesendet werden müssen, empfehlen sich üblicherweise Zustellungs-Agent-Connectors, weil Nachrichten in einer Warteschlange verwaltet werden können, sie nicht in das Dateisystem geschrieben werden müssen, und weil es weitere Vorteile gibt. Im Thema <A href="delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md">Zustellungs-Agents und Zustellungs-Agent-Connectors</A> finden Sie weitere Informationen.



Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Fremde Connectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines fremden Connectors zum Senden von Nachrichten an einen Nicht-SMTP-Gatewayserver mithilfe der Shell

1.  Führen Sie den folgenden Befehl aus, um den fremden Connector zu erstellen:
    
    ```powershell
        New-ForeignConnector -Name "Contoso Foreign Connector" -AddressSpaces "X400:c=US;a=Fabrikam;P=Contoso;5" -SourceTransportServers Hub01,Hub02
    ```
    
    In diesem Beispiel sind "Hub01" und "Hub02" Quellserver in Ihrer Organisation, die Sie zur Nachrichtenzustellung an das fremde System einsetzen. Die Verwendung von mehr als einem Quellserver bietet Fehlertoleranz.

Nachdem Sie den fremden Connector erstellt haben, können Sie basierend auf den Anforderungen Ihrer Organisation die Ablage-, PICKUP- und Wiedergabeverzeichnisse konfigurieren.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie den folgenden Befehl aus, um sicherzustellen, dass der fremde Connector erfolgreich erstellt wurde:

```powershell
Get-ForeignConnector | Format-List Name
```

Überprüfen Sie, ob der Name des erstellten fremden Connectors angezeigt wird.

## Schritt 2: Konfigurieren des Ablageverzeichnisses für einen Postfachserver mit Transportdienst mithilfe der Shell

Das Ablageverzeichnis für einen Postfachserver, auf dem der Transportdienst ausgeführt wird, wird für die Zustellung ausgehender Nachrichten von Ihrem fremden Connector verwendet.

Sie erstellen das Verzeichnis, das als Ablageverzeichnis verwendet werden soll, auf Ihrem lokalen Dateisystem. Sie können auch ein Verzeichnis auf einer Netzwerkfreigabe verwenden.

1.  Führen Sie das folgende Skript aus, um das Ablageverzeichnis für Ihren fremden Connector anzugeben (ändern Sie den Wert für den Parameter *DropDirectory* in einen geeigneten Pfad für Ihre Umgebung):
    
    ```powershell
        Set-ForeignConnector "Contoso Foreign Connector" -DropDirectory "C:\Drop Directory"
    ```
    
## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können das folgende Cmdlet-Skript ausführen und den Wert des Parameters *DropDirectory* überprüfen, um die ordnungsgemäße Einrichtung des Ablageverzeichnisses zu überprüfen:

```powershell
Get-ForeignConnector "Contoso Foreign Connector" | Format-List
```

Nachdem Sie den fremden Connector erstellt und das Ablageverzeichnis angegeben haben, können Sie über den Postfachserver, auf dem Sie den fremden Connector erstellt haben, eine Nachricht senden und überprüfen, ob eine Datei an das Ablageverzeichnis zugestellt wurde.

## Schritt 3: Konfigurieren des PICKUP-Verzeichnisses für den Transportdienst auf einem Postfachserver mithilfe der Shell

Das PICKUP-Verzeichnis für den Transportdienst auf einem Postfachserver wird zur Erfassung von Nachrichten verwendet, die von Nicht-SMTP-Systemen generiert werden. Verwenden Sie dieses Verfahren in Fällen, in denen Sie durch ein Nicht-SMTP-System – z. B. einen Faxgatewayserver – generierte neue Nachrichten per Dateiübertragung abrufen möchten.

Ausführliche Anweisungen zum Konfigurieren Ihres PICKUP-Verzeichnisses finden Sie unter [Konfigurieren des PICKUP-Verzeichnisses und des Wiedergabeverzeichnisses](configure-the-pickup-directory-and-the-replay-directory-exchange-2013-help.md).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können den folgenden Befehl ausführen und den Wert des Parameters *PickupDirectoryPath* überprüfen, um die ordnungsgemäße Einrichtung des PICKUP-Verzeichnisses zu überprüfen:

```powershell
Get-TransportService | Format-List PickupDirectoryPath
```

## Schritt 4: Konfigurieren des Wiedergabeverzeichnisses für den Transportdienst auf einem Postfachserver mithilfe der Shell

Das Wiedergabeverzeichnis für den Transportdienst auf einem Postfachserver wird zur Erfassung von Nachrichten verwendet, die von Nicht-SMTP-Systemen generiert werden. Verwenden Sie dieses Verfahren zur Konfiguration des Wiedergabeverzeichnisses in Fällen, in denen Sie – typischerweise von einem fremden Nicht-SMTP-Gatewayserver stammende – E-Mail-Nachrichten erneut übertragen möchten, die in Ihrer Exchange-Umgebung generiert und vom Exchange-Transport exportiert wurden.

Ausführliche Anweisungen zum Konfigurieren Ihres PICKUP-Verzeichnisses finden Sie unter [Konfigurieren des PICKUP-Verzeichnisses und des Wiedergabeverzeichnisses](configure-the-pickup-directory-and-the-replay-directory-exchange-2013-help.md).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können den folgenden Befehl ausführen und den Wert des Parameters *ReplayDirectoryPath* überprüfen, um die ordnungsgemäße Einrichtung des Wiedergabeverzeichnisses zu überprüfen:

```powershell
Get-TransportService | Format-List ReplayDirectoryPath
```

## Weitere Informationen

[Fremde Connectors](foreign-connectors-exchange-2013-help.md)

[Zustellungs-Agents und Zustellungs-Agent-Connectors](delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md)

