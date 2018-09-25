---
title: 'Recreating arbitration mailboxes: Exchange 2013 Help'
TOCTitle: Recreating arbitration mailboxes
ms:assetid: bb6b8524-aaee-4be8-a04e-e61cd2ab3465
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt829264(v=EXCHG.150)
ms:contentKeyID: 74518128
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Recreating arbitration mailboxes

 

_**Letztes Änderungsdatum des Themas:** 2018-01-17_

**Zusammenfassung:**  Informationen zu Vermittlungspostfächern in Exchange 2013 und ihrer Neuerstellung.

Exchange 2013 enthält fünf Systempostfächer, die als *Vermittlungspostfächer* bezeichnet werden. Vermittlungspostfächer werden zum Speichern unterschiedlicher Typen von Systemdaten und für die Verwaltung des Nachrichtengenehmigungsworkflows verwendet. Im folgenden Diagramm werden die verschiedenen Vermittlungspostfächer und ihre Aufgaben aufgeführt.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Vermittlungspostfachs</th>
<th>Anzeigename</th>
<th>Dauerhafte Funktionen</th>
<th>Funktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042</p></td>
<td><p>Microsoft Exchange-Verbundpostfach</p></td>
<td><p>{}</p></td>
<td><p>In diesem Postfach werden Daten gespeichert, die zur Verwaltung des Verbunds zwischen verschiedenen Exchange-Organisationen verwendet werden. Dies umfasst Rights Management Services, standortübergreifende Nachrichtenfluss-Überwachungstests und Antworten, Benachrichtigungen, Online-Archive, Messaging-Datensatzverwaltung und standortübergreifende Frei/Gebucht-Informationen.</p></td>
</tr>
<tr class="even">
<td><p>SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109}</p></td>
<td><p>Microsoft Exchange-Genehmigungs-Assistent</p></td>
<td><p>{}</p></td>
<td><p>Dieses Postfach wird zur Verwendung durch das Exchange-Genehmigungsframework für die Empfängermoderation und Anforderungen zur automatischen Gruppengenehmigung bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Migration.8f3e7716-2011-43e4-96b1-aba62d229136</p></td>
<td><p>Microsoft Exchange-Migration</p></td>
<td><p>{OrganizationCapabilityManagement}</p></td>
<td><p>In diesem Postfach werden Daten für den Exchange-Migrationsdienst gespeichert, die beim Verschieben von Postfächern in Batches verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}</p></td>
<td><p>Microsoft Exchange</p></td>
<td><p>{OrganizationCapabilityUMDataStorage}</p></td>
<td><p>Discoverysystempostfach.</p>
<p>Dieses Postfach wird für die Verwendung durch das eDiscovery-Feature bereitgestellt, mit dem von Compliance Officern nach Nachrichten gesucht wird, die bestimmten Auswahlkriterien entsprechen. Das Postfach wird auch von Unified Messaging für das Speichern von an der UM-Konsole beteiligten Dateien und anderen Informationen verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}</p></td>
<td><p>Microsoft Exchange</p></td>
<td><p>{OrganizationCapabilityUMGrammarReady, OrganizationCapabilityPstProvider, OrganizationCapabilityMessageTracking, OrganizationCapabilityMailRouting, OrganizationCapabilityClientExtensions, OrganizationCapabilityGMGen, OrganizationCapabilityOABGen, OrganizationCapabilityUMGrammar}</p></td>
<td><p>Dies wird als Organisationspostfach bezeichnet. Es dient zum Erstellen von Offline-Adressbüchern (OABs). Für einen Lastenausgleich der OAB-Generierung in Ihrer Organisation, auch in geografisch verteilten Standorten, können Sie zusätzliche Organisationspostfächer erstellen.</p></td>
</tr>
</tbody>
</table>


Wenn Sie eines oder mehrere dieser Vermittlungspostfächer neu erstellen müssen, lesen Sie die folgenden Anweisungen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit zur Durchführung: 10 Minuten pro Verfahren.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Neuerstellen eines Vermittlungspostfachs mit Exchange-Verwaltungsshell

Verwenden Sie die folgenden Anweisungen, um eine bestimmte Art von Vermittlungspostfach neu zu erstellen.


> [!NOTE]
> Alle Schritte in den folgenden Abschnitten müssen in demselben Verzeichnis ausgeführt werden, in dem Sie die Exchange-Installationsmedien extrahiert haben.



## Neuerstellen des Microsoft Exchange-Verbundpostfachs

So erstellen Sie das Vermittlungspostfach FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042 neu

1.  Wenn Vermittlungspostfächer fehlen, führen Sie den folgenden Befehl aus:
    
    ```powershell
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```
    
2.  Führen Sie in Exchange-Verwaltungsshell den folgenden Befehl aus:
    
    ```powershell
    Enable-Mailbox -Arbitration -Identity "FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042"
    ```

## Neuerstellen des Postfachs des Microsoft Exchange-Genehmigungs-Assistenten

So erstellen Sie das Vermittlungspostfach SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109} neu

1.  Wenn Vermittlungspostfächer fehlen, führen Sie den folgenden Befehl aus:

    ```powershell
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2.  Führen Sie in Exchange-Verwaltungsshell den folgenden Befehl aus:
    ```powershell
        Get-User | Where-Object {$_.Name -like "SystemMailbox{1f05a927-7709-4e35-9dbe-d0f608fb781a}"} | Enable-Mailbox -Arbitration
    ```

## Neuerstellen des Microsoft Exchange-Migrationspostfachs

So erstellen Sie das Vermittlungspostfach Migration.8f3e7716-2011-43e4-96b1-aba62d229136 neu

1.  Wenn Vermittlungspostfächer fehlen, führen Sie den folgenden Befehl aus:
    ```powershell
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2.  Führen Sie in Exchange-Verwaltungsshell den folgenden Befehl aus:
    
    ```powershell
     Enable-Mailbox -Arbitration -Identity "Migration.8f3e7716-2011-43e4-96b1-aba62d229136"
    ```

3.  Legen Sie in Exchange-Verwaltungsshell die dauerhaften Funktionen (MsExchCapabilityIdentifiers) fest, indem Sie den folgendem Befehl ausführen:
    
    ```powershell
     Set-Mailbox "Migration.8f3e7716-2011-43e4-96b1-aba62d229136" -Arbitration -Management:$True -Force
    ```

## Neuerstellen des Systempostfachs der Microsoft Exchange-Suche

So erstellen Sie das Vermittlungspostfach SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9} neu

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

## Neuerstellen des Microsoft Exchange-Organisationspostfachs für OABs

So erstellen Sie das Vermittlungspostfach SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c} neu

1.  Wenn Vermittlungspostfächer fehlen, führen Sie den folgenden Befehl aus:
    
    ```powershell
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```
    
2.  Führen Sie in Exchange-Verwaltungsshell den folgenden Befehl aus:
    
    ```powershell
     Enable-Mailbox -Arbitration -Identity "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}"
    ```

3.  Legen Sie in Exchange-Verwaltungsshell die dauerhaften Funktionen (MsExchCapabilityIdentifiers) fest, indem Sie den folgendem Befehl ausführen:
        
    ```powershell
        Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration | Set-Mailbox -Arbitration -UMGrammar:$True -OABGen:$True -GMGen:$True -ClientExtensions:$True -MessageTracking:$True -PstProvider:$True -MaxSendSize 1GB -Force
    ```
    
Wenn Sie anschließend den Befehl `$OABMBX = Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration (Get-ADUser $OABMBX.SamAccountName -Properties *).msExchCapabilityIdentifiers` ausführen, werden Sie sehen, dass 46, 47 und 51 fehlen. Führen Sie den folgenden Befehl aus, um alle Funktionen wieder hinzuzufügen:

    ```powershell
    Set-ADUser $OABMBX.SamAccountName -Add @{"msExchCapabilityIdentifiers"="40","42","43","44","47","51","52","46"}
    ```
    
## Woher weiß ich, dass der Vorgang erfolgreich war?

Zur Überprüfung, dass Sie das Vermittlungspostfach erfolgreich neu erstellt haben, verwenden Sie das Cmdlet **Get-Mailbox** mit dem Schalter *Arbitration*, um die Systempostfächer abzurufen.

```powershell
Get-Mailbox -Arbitration | Format-Table Name, DisplayName
```

Überprüfen Sie anhand der Ergebnisse des Befehls, ob das betreffende Systempostfach mit dem Namen oder Anzeigenamen in der vorstehenden Tabelle neu erstellt wurde.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


