---
title: 'Verwalten von lokalen Verschiebungen: Exchange 2013 Help'
TOCTitle: Verwalten von lokalen Verschiebungen
ms:assetid: 1691b658-f5af-49c6-9170-5c3cb66c7306
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150487(v=EXCHG.150)
ms:contentKeyID: 50475087
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von lokalen Verschiebungen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-25_

Als Verschiebungsanforderung wird das Verschieben eines Postfachs von einer Postfachdatenbank in eine andere bezeichnet. Eine lokale Verschiebungsanforderung ist eine Postfachverschiebung, die in einer einzelnen Gesamtstruktur erfolgt. In Microsoft Exchange Server 2013 können Postfächer und persönliche Archivpostfächer in unterschiedlichen Datenbanken gespeichert werden. Mithilfe der Funktion für Verschiebungsanforderungen können Sie das primäre Postfach und das zugeordnete Archiv in dieselbe Datenbank oder in unterschiedliche Datenbanken verschieben. Die Verfahren in diesem Thema helfen Ihnen beim Verschieben lokaler Postfächer.

Verwenden Sie die folgenden Verfahren, um Postfächer in Ihrer lokalen Organisation zu verschieben. In diesen Verfahren werden die Exchange-Verwaltungsshell und die Exchange-Verwaltungskonsole verwendet.

Wenn Sie Postfächer mithilfe von Verschiebungsanforderungen verschieben, werden diese Verschiebungsanforderungen von den folgenden beiden Diensten verarbeitet:

  - Microsoft Exchange-Postfachreplikationsdienst

  - Microsoft Exchange-Proxydienst für die Postfachreplikation

Weitere Informationen zu Postfachreplikationsserver und -proxy finden Sie unter [Weitere Informationen über den Proxy für den Postfachreplikationsdienst](https://technet.microsoft.com/de-de/library/jj156451\(v=exchg.150\)).

Weitere Informationen zum Verschieben von Postfächern finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 20 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für Postfachverschiebung und -migration" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Testen, ob ein Postfach für die Verschiebung bereit ist

In diesem Beispiel wird die Option *WhatIf* verwendet, um zu testen, ob das Postfach von Tony Smith bereit ist, in die neue Datenbank DB01 verschoben zu werden, und ob der Befehl Fehler aufweist. Wenn Sie die Option *WhatIf* verwenden, führt das System mehrere Prüfungen für das Postfach durch. Wenn das Postfach nicht für die Verschiebung bereit ist, wird eine Fehlermeldung angezeigt.

    New-MoveRequest -Identity 'tony@alpineskihouse.com' -TargetDatabase DB01 -WhatIf

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Erstellen einer lokalen Verschiebungsanforderung

## Erstellen einer lokalen Verschiebungsanforderung mithilfe der Exchange-Verwaltungskonsole

Melden Sie sich bei der Exchange-Verwaltungskonsole an, und führen Sie die folgenden Schritte aus, um eine lokale Verschiebungsanforderung zu erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungenden Benutzer aus, der verschoben werden soll, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie die gewünschten Optionen für das Archivpostfach sowie den Speicherort der Postfachdatenbank, und klicken Sie auf **Neu**.

## Erstellen einer lokalen Verschiebungsanforderung mithilfe der Shell

Ein Beispiel für die Erstellung einer lokalen Verschiebungsanforderung finden Sie in Beispiel 2 in [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Migration**.

  - Überprüfen Sie, ob die Verschiebung erfolgreich durchgeführt wurde, indem Sie in der Exchange-Verwaltungskonsole auf **Status für alle Batches** klicken.

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Erstellen einer Batchverschiebungsanforderung

## Erstellen einer Batchverschiebungsanforderung mithilfe der Exchange-Verwaltungskonsole

Melden Sie sich bei der Exchange-Verwaltungskonsole an, und führen Sie die folgenden Schritte aus:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungendie Benutzer aus, die verschoben werden sollen, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie die gewünschten Optionen für das Archivpostfach sowie den Speicherort der Postfachdatenbank, und klicken Sie auf **Neu**.


> [!WARNING]
> Stellen Sie sicher, dass der Grenzwert für ungültige Elemente nicht auf über 50 Elemente eingestellt ist. Andernfalls tritt beim Verschieben eventuell ein Fehler auf. Wenn Sie den Grenzwert für ungültige Elemente auf über 50 Elemente festlegen, müssen Sie den Parameter –<EM>AcceptLargeDataLoss</EM> in der Exchange-Verwaltungsshell auf "true" einstellen.



## Erstellen einer Batchverschiebungsanforderung mithilfe der Shell

In diesem Beispiel wird ein Migrationsbatch für eine lokale Verschiebung erstellt, bei der die Postfächer in der angegebenen CSV-Datei in eine andere Postfachdatenbank verschoben werden. Diese CSV-Datei enthält eine einzige Spalte mit den E-Mail-Adressen der Postfächer, die verschoben werden sollen. Die Kopfzeile dieser Spalte muss **EmailAddress** lauten. Der Migrationsbatch in diesem Beispiel muss manuell mithilfe des Cmdlets **Start-MigrationBatch** oder über die Exchange-Verwaltungskonsole gestartet werden. Alternativ dazu können Sie auch den Parameter *AutoStart* verwenden, um den Batch automatisch zu starten.

    New-MigrationBatch -Local -Name LocalMove1 -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\LocalMove1.csv")) -TargetDatabases MBXDB2 -TimeZone "Pacific Standard Time"

    Start-MigrationBatch -Identity LocalMove1

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [Start-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219165\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Überprüfen Sie, ob die Verschiebung erfolgreich durchgeführt wurde, indem Sie in der Exchange-Verwaltungskonsole auf **Status für alle Batches** klicken.

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Anzeigen von Migrationsbatches

Ein Beispiel für das Anzeigen eines Migrationsbatches mithilfe der Shell finden Sie in Beispiel 2 in [Get-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219164\(v=exchg.150\)).

## Verschieben des primären Postfachs eines Benutzers

## Verwenden der Exchange-Verwaltungskonsole, um lediglich das primäre Postfach eines Benutzers zu verschieben

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungen den Benutzer aus, dessen primäres Postfach verschoben werden soll, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie **Nur primäres Postfach verschieben**, geben Sie die gewünschten Optionen für den Speicherort der Postfachdatenbank an, und klicken Sie auf **Neu**.

## Verwenden der Shell, um lediglich das primäre Postfach eines Benutzers zu verschieben

In diesem Beispiel wird lediglich das primäre Postfach von Tony Smith in die Datenbank "DB01" verschoben. Das Archiv wird nicht verschoben.

    New-MoveRequest -Identity 'tony@alpineskihouse.com' -PrimaryOnly -TargetDatabase "DB01"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Klicken Sie in der Exchange-Verwaltungskonsole auf **Status für alle Batches**.

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Erstellen einer gesamtstrukturübergreifenden Verschiebung mithilfe einer CSV-Batchdatei

In diesem Beispiel wird der Migrationsendpunkt konfiguriert und anschließend mithilfe einer CSV-Datei eine gesamtstrukturübergreifende Batchverschiebung von der Quellgesamtstruktur in die Zielgesamtstruktur erstellt.

    New-MigrationEndpoint -Name Fabrikam -ExchangeRemote -Autodiscover -EmailAddress tonysmith@fabrikam.com -Credentials (Get-Credential fabrikam\tonysmith) 
    
    $csvData=[System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\batch.csv")
    New-MigrationBatch -CSVData $csvData -Timezone "Pacific Standard Time" -Name FabrikamMerger -SourceEndpoint Fabrikam -TargetDeliveryDomain "mail.contoso.com"

Weitere Informationen zur Vorbereitung Ihrer Gesamtstruktur für gesamtstrukturübergreifende Verschiebungen finden Sie in den folgenden Themen:

  - [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen](prepare-mailboxes-for-cross-forest-move-requests-exchange-2013-help.md)

  - [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode](prepare-mailboxes-for-cross-forest-moves-using-sample-code-exchange-2013-help.md)

  - [Vorbereiten von Postfächern für eine standortübergreifende Verschiebung mit dem Skript „Prepare-MoveRequest.ps1“ in der Shell](prepare-mailboxes-for-cross-forest-moves-using-the-prepare-moverequest-ps1-script-in-the-shell-exchange-2013-help.md)

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Verschieben eines Archivpostfachs

## Verwenden der Exchange-Verwaltungskonsole, um lediglich ein Archivpostfach zu verschieben

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungenden Benutzer aus, dessen Archivpostfach verschoben werden soll, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie **Nur Archivpostfach verschieben**, geben Sie die gewünschten Optionen für den Speicherort der Postfachdatenbank an, und klicken Sie auf **Neu**.

## Verwenden der Shell, um lediglich ein Archivpostfach zu verschieben

In diesem Beispiel wird lediglich das Archivpostfach von Tony Smith in die Datenbank "DB03" verschoben. Das primäre Postfach wird nicht verschoben.

    New-MoveRequest -Identity 'tony@alpineskihouse.com' -ArchiveOnly -ArchiveTargetDatabase "DB03"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Verschieben des primären Postfachs eines Benutzers und des Archivpostfachs in separate Datenbanken

In diesem Beispiel werden das primäre Postfach und das Archivpostfach der Benutzerin "Ayla" in separate Datenbanken verschoben. Das primäre Postfach wird in die Datenbank "DB01", das Archiv in die Datenbank "DB03" verschoben.

    New-MoveRequest -Identity 'ayla@humongousinsurance.com' -TargetDatabase DB01 -ArchiveTargetDatabase -DB03

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

## Verschieben des primären Postfachs eines Benutzers und Festlegen eines hohen Grenzwerts für ungültige Elemente

## Verschieben des primären Postfachs eines Benutzers und Festlegen eines hohen Grenzwerts für ungültige Elemente mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungen den Benutzer aus, dessen primäres Postfach verschoben werden soll, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie **Nur primäres Postfach verschieben** aus, und geben Sie die gewünschten Optionen für den Speicherort der Postfachdatenbank an.

4.  Klicken Sie auf **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)"), geben Sie den Grenzwert für ungültige Elemente ein, und klicken Sie auf **OK**.

## Verschieben des primären Postfachs eines Benutzers und Festlegen eines hohen Grenzwerts für ungültige Elemente mithilfe der Shell

In diesem Beispiel wird das primäre Postfach von Lisa in die Postfachdatenbank "DB01" verschoben, und der Grenzwert für ungültige Elemente wird auf `100` festgelegt. Um einen hohen Grenzwert für ungültige Elemente festzulegen, muss der Parameter *AcceptLargeDataLoss* verwendet werden.

    New-MoveRequest -Identity 'Lisa' -PrimaryOnly -TargetDatabase "DB01" -BadItemLimit 100 -AcceptLargeDataLoss

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\)) und [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Führen Sie in der Shell folgenden Befehl aus, um Informationen zur Verschiebung des Postfachs abzurufen.
    
        Get-MigrationUserStatistics -Identity BatchName -Status | Format-List

Weitere Informationen finden Sie unter [Get-MigrationUserStatistics](https://technet.microsoft.com/de-de/library/jj218695\(v=exchg.150\)).

