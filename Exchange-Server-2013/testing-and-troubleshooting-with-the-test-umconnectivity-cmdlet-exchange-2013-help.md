---
title: 'Testen und Problembehandlung mit dem Cmdlet "Test-UMConnectivity": Exchange 2013 Help'
TOCTitle: Testen und Problembehandlung mit dem Cmdlet "Test-UMConnectivity"
ms:assetid: 08e67a99-e37f-4afd-bd58-455b62580af7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995978(v=EXCHG.150)
ms:contentKeyID: 56271559
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Testen und Problembehandlung mit dem Cmdlet \"Test-UMConnectivity\"

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-06-25_

Nachdem Sie den Clientzugriffsserver und den Postfachserver installiert haben sowie Unified Messaging (UM) konfiguriert haben, können Sie mehrere Diagnosetests und eine softwarebasierte Telefonieanwendung verwenden, um die Telefonieverbindungen und den Betrieb des Unified Messaging-Dienstes zu testen.

## Test-UMConnectivity

Das Cmdlet **Test-UMConnectivity** kann abhängig von den mit dem Cmdlet verwendeten Parametern auf verschiedene Weise zum Überprüfen der Verbindungen mit Clientzugriffsservern und Postfachservern verwendet werden. Zum Testen der Unified Messaging-Funktionen sind folgende Tests verfügbar:

  - **Lokal**   Das Cmdlet **Test-UMConnectivity** überprüft die VoIP-Kommunikation (Voice over IP) mit den Postfachservern, die auf dem gleichen lokalen Computer ausgeführt werden.

  - **Lokal mit TUILogon**   Das Cmdlet **Test-UMConnectivity** versucht, die VoIP-Kommunikation mit dem Postfachserver herzustellen, der auf dem gleichen Computer ausgeführt wird. Wird die Verbindung hergestellt, versucht das Cmdlet, sich an mindestens einem UM-aktivierten Postfach anzumelden, indem die Durchwahlnummer und PIN des Postfachs gesendet werden. Wird der Parameter *–TUILogon* angegeben, müssen die folgenden Parameterwerte ebenfalls mit den entsprechenden Informationen für das Testpostfach angegeben werden:
    
      - *–Phone*   Dieser Parameter muss die Durchwahlnummer für das Testpostfach enthalten.
    
      - *–PIN*   Dieser Parameter muss die PIN des UM-aktivierten Postfachs enthalten.
    
      - *–UMDialPlan   *Dieser Parameter muss die Wähleinstellungen enthalten, die dem Testpostfach zugeordnet sind.

  - **Remote**   Das Cmdlet **Test-UMConnectivity** versucht, eine Verbindung mit einem Remote-Clientzugriffsserver herzustellen, indem ein Anruf über ein VoIP-Gateway vorgenommen wird. Nachdem die Verbindung hergestellt wurde, werden Verbindungsüberprüfungen auf dem Remote-Clientzugriffsserver und für die Medienpfade durchgeführt.
    

    > [!NOTE]
    > Wenn die folgende Meldung angezeigt wird, sollten Sie den Microsoft&nbsp;Exchange Unified Messaging-Dienst neu starten, da er beendet wurde oder nicht reagiert: "Fehler beim Ausführen eines Anrufs durch den Test-UMConnectivity-Task. Details: Es konnte keine Verbindung hergestellt werden."


