---
title: 'Kopieren d. eDiscovery-Suchergebn. in Discoverypostfach: Exchange 2013-Hilfe'
TOCTitle: Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach
ms:assetid: bff2ce89-9e6f-494a-bd6a-2f2011507845
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn624163(v=EXCHG.150)
ms:contentKeyID: 61183401
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-24_

Nachdem Sie eine Compliance-eDiscovery-Suche erstellt haben, können Sie die Suchergebnisse mithilfe der EAC in ein Zielpostfach kopieren. Sie können auch die Shell verwenden, um eine eDiscovery-Suche zu starten, die mithilfe des Cmdlets **New-MailboxSearch** erstellt wurde. Dieses kopiert die Ergebnisse in das Discoverypostfach, das Sie bei der Erstellung der Suche angegeben haben.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten oder länger, je nach der Anzahl der Postfachelemente, die in den Suchergebnissen zurückgegeben werden.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Compliance-eDiscovery" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Eine eDiscovery-Suche muss mithilfe der EAC oder der Shell erstellt werden, bevor Sie die Suchergebnisse kopieren können. Weitere Informationen finden Sie unter [Erstellen einer Compliance-eDiscovery-Suche](https://technet.microsoft.com/de-de/library/Dd353189(v=EXCHG.150)).

  - Das Exchange 2013-Setup erstellt ein Discoverypostfach namens **Discoverysuchpostfach**, um Suchergebnisse zu kopieren. Das Postfach für die Discoverysuche wird standardmäßig in Exchange Online erstellt. Sie können zusätzliche Discoverypostfächer erstellen. Weitere Informationen finden Sie unter [Erstellen eines Discoverypostfachs](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/create-a-discovery-mailbox).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Kopieren von Suchergebnissen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der EAC zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Wählen Sie in der Listenansicht eine eDiscovery-Suche aus.

3.  Klicken Sie auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") und anschließend in der Dropdownliste auf **Suchergebnisse kopieren**.

4.  Wählen Sie unter **Suchergebnisse kopieren** aus den folgenden Optionen:
    
      - **Nicht durchsuchbare Elemente einschließen**   Wählen Sie dieses Kontrollkästchen aus, um Postfachelemente zu berücksichtigen, die nicht durchsucht werden konnten (z. B. Nachrichten mit Anhängen, die Dateitypen enthalten, die von der Exchange-Suche nicht indiziert werden konnten). Weitere Informationen finden Sie unter [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md).
    
      - **Deduplizierung aktivieren**   Wählen Sie dieses Kontrollkästchen aus, um doppelte Nachrichten auszuschließen. Es wird nur eine einzelne Instanz einer Nachricht in das Discovery-Postfach kopiert.
    
      - **Vollständige Protokollierung aktivieren**   Wählen Sie dieses Kontrollkästchen aus, um ein vollständiges Protokoll in die Suchergebnisse einzufügen.
    
      - **Nach Abschluss des Kopiervorgangs E-Mail an mich senden**   Wählen Sie dieses Kontrollkästchen aus, um eine E-Mail-Benachrichtigung zu erhalten, wenn die Suche abgeschlossen ist.
    
      - **Ergebnisse in dieses Discoverypostfach kopieren**   Klicken Sie auf **Durchsuchen**, um das Discoverypostfach auszuwählen, in das die Suchergebnisse kopiert werden sollen.
        
        ![Suchergebnisse kopieren](images/Dn624163.875e25ed-8308-408c-92c4-8c76fc9d9bfc(EXCHG.150).gif "Suchergebnisse kopieren")  

5.  Klicken Sie auf **Kopieren**, um den Prozess zum Kopieren der Suchergebnisse in das angegebene Discoverypostfach zu starten.

6.  Klicken Sie **Aktualisieren**![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)"), um die Informationen über den Kopierstatus zu aktualisieren, die im Detailbereich angezeigt werden.

7.  Wenn der Kopiervorgang abgeschlossen ist, klicken Sie auf **Öffnen**, um das Discoverypostfach zu öffnen und die Suchergebnisse anzuzeigen.

## Verwenden der Shell zum Kopieren von Suchergebnissen

Nachdem Sie mithilfe des Cmdlets **New-MailboxSearch** eine Compliance-eDiscovery-Suche erstellt haben, müssen Sie die Suche starten, um Nachrichten in das im Parameter *TargetMailbox* angegebene Discoverypostfach zu kopieren. Informationen über die Erstellung von eDiscovery-Suchen mithilfe der Shell erhalten Sie unter:

  - [Use the Shell to create an In-Place eDiscovery search](https://technet.microsoft.com/de-de/library/Dd353189(v=EXCHG.150))

  - [New-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298064\(v=exchg.150\))

Sie würden z. B. den folgenden Befehl ausführen, um eine eDiscovery-Suche namens *Fabrikam Investigation* zu starten und die Suchergebnisse in das angegebene Discoverypostfach zu kopieren.

```powershell
Start-MailboxSearch "Fabrikam Investigation"
```

Wenn Sie die Option *EstimateOnly* verwenden, um eine Schätzung der Suchergebnisse zu erhalten, müssen Sie die Option entfernen, bevor Sie die Suchergebnisse kopieren können. Sie müssen auch ein Discoverypostfach angeben, in das die Suchergebnisse kopiert werden sollen. Sie könnten z. B. eine nur auf Schätzung beruhende Suche mithilfe des folgenden Befehls erstellen:

```powershell
    New-MailboxSearch "FY13 Q2 Financial Results" -StartDate "04/01/2013" -EndDate "06/30/2013" -SourceMailboxes "DG-Finance" -SearchQuery '"Financial" AND "Fabrikam"' -EstimateOnly -IncludeUnsearchableItems
```

Um die Ergebnisse dieser Suche in ein Discoverypostfach zu kopieren, würden Sie dann die folgenden Befehle ausführen:

  ```powershell
  Set-MailboxSearch "FY13 Q2 Financial Results" -EstimateOnly $false -TargetMailbox "Discovery Search Mailbox"
  ```

  ```powershell
  Start-MailboxSearch "FY13 Q2 Financial Results"
  ```

## Weitere Informationen über das Kopieren von Suchergebnissen

  - Wenn Sie Suchergebnisse in das Discoverypostfach kopiert haben, können Sie sie in eine PST-Datei exportieren. Weitere Informationen finden Sie unter [Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](https://technet.microsoft.com/de-de/library/Dn440164(v=EXCHG.150)).

  - Weitere Informationen zu nicht durchsuchbaren Elementen finden Sie unter [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md).

  - Wenn Sie sämtliche Postfachinhalte innerhalb eines bestimmten Datumsbereichs (bei Weglassen der Angabe von Schlüsselwörtern in den Suchkriterien) kopieren, werden alle nicht durchsuchbaren Elemente in diesem Datumsbereich automatisch in die Suchergebnisse einbezogen. Aktivieren Sie deshalb nicht das Kontrollkästchen **Nicht durchsuchbare Elemente einschließen**, wenn Sie Suchergebnisse kopieren. Andernfalls wird eine doppelte Kopie aller nicht durchsuchbaren Elemente in das Discoverypostfach kopiert.

  - Zusätzlich zum Kopieren der Suchergebnisse in ein Discoverypostfach können Sie auch die Sucherergebnisse für eine ausgewählte Suche schätzen oder in einer Vorschau anzeigen.
    
      - **Suchergebnisse schätzen**   Diese Option liefert eine Schätzung der Gesamtgröße und -anzahl der Objekte, die von der Suche auf der Grundlage der angegebenen Kriterien zurückgegeben werden. Schätzungen werden im Detailbereich der EAC angezeigt.
    
      - **Suchergebnisse in Vorschau anzeigen**   Mit dieser Option können Sie die zurückgegebenen Suchergebnisse in einer Vorschau anzeigen, anstatt Sie zur Anzeige in ein Discoverypostfach kopieren zu müssen. Auf diese Weise können Sie schnell bestimmen, ob die Suchergebnisse relevant sind. Nachdem Sie eine Vorschau der Ergebnisse angezeigt haben, können Sie die Suchabfrage überarbeiten, um die Suchergebnisse einzugrenzen, und die Suche erneut ausführen. Die Elemente auf der Vorschauseite sind schreibgeschützte Versionen der tatsächlichen Suchergebnisse. Sie können sie auf der Vorschauseite also nicht verschieben, bearbeiten, löschen oder weiterleiten.
    
    Weitere Informationen finden Sie unter [Estimate or preview search results](https://technet.microsoft.com/de-de/library/Dd353189(v=EXCHG.150)).

