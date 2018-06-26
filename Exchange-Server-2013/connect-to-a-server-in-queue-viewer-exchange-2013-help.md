---
title: 'Herstellen einer Verbindung mit einem Server in der Warteschlangenanzeige: Exchange 2013 Help'
TOCTitle: Herstellen einer Verbindung mit einem Server in der Warteschlangenanzeige
ms:assetid: 6c1ad574-9ab5-4dcc-9398-ec10eca4fd11
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998669(v=EXCHG.150)
ms:contentKeyID: 50475893
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Herstellen einer Verbindung mit einem Server in der Warteschlangenanzeige

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-03_

Wenn Sie die Warteschlangenanzeige in der Exchange Toolbox auf einem Microsoft Exchange Server 2013-Server verwenden, der sich innerhalb der Exchange-Organisation befindet, können Sie eine Verbindung mit anderen Postfachservern herstellen. Standardmäßig stellt die Warteschlangenanzeige beim Öffnen auf einem Postfachserver eine Verbindung mit der Warteschlangendatenbank auf dem lokalen Server her. Sie können jedoch mehrere Instanzen der Warteschlangenanzeige öffnen, sodass jede Instanz auf einen anderen Server fokussiert. Die Fenster der Warteschlangenanzeige lassen sich überlappend anordnen. So können Sie problemlos mehrere Postfachserver gleichzeitig überwachen.

Sie können auch den Server angeben, der von Remote PowerShell zur Ausführung der angegebenen Aufgaben in der Warteschlangenanzeige verwendet werden soll. Dies muss nicht notwendigerweise der Remoteserver sein, den Sie in der Warteschlangenanzeige verwalten.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Verfahren in diesem Thema gelten nicht für Edge-Transport-Server. Bei Ausführung der Warteschlangenanzeige auf einem Edge-Transport-Server kann der Schwerpunkt des Tools nicht geändert werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Angeben des in der Warteschlangenanzeige zu verwaltenden Servers mithilfe der Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**.

3.  Klicken Sie im Aktionsbereich auf **Verbindung mit dem Server herstellen**.

4.  Klicken Sie im Fenster **Verbindung mit dem Server herstellen** auf **Durchsuchen**, um eine Liste der verfügbaren Postfachserver anzuzeigen.

5.  Wählen Sie im Fenster **Exchange-Server auswählen** einen Postfachserver aus. Gehen Sie folgendermaßen vor, um nach einem Postfachserver zu suchen:
    
      - Geben Sie im Feld **Suchen** den exakten Servernamen oder die ersten Buchstaben des Servernamens ein, und klicken Sie dann auf **Jetzt suchen**. Wählen Sie im Ergebnisbereich einen Server aus.
    
      - Wählen Sie das Menü **Ansicht** aus, und klicken Sie dann auf **Filter anzeigen**. Klicken Sie in der Spalte **Name** oder **Version** auf das Filtersymbol, und wählen Sie dann den Filteroperator aus. Geben Sie die Filterkriterien im Feld **Geben Sie Text hier ein** ein. Drücken Sie die EINGABETASTE. Wählen Sie im Ergebnisbereich einen Server aus.

6.  Klicken Sie auf **OK**, um das Fenster **Exchange-Server auswählen** zu schließen.

7.  Aktivieren Sie nach dem Auswählen eines Servers im Fenster **Verbindung mit dem Server herstellen** das Kontrollkästchen **Als Standardserver festlegen**, wenn der Schwerpunkt der Warteschlangenanzeige bei jedem Öffnen der Warteschlangenanzeige auf diesem Server liegen soll.

8.  Klicken Sie im Fenster **Verbindung mit dem Server herstellen** auf **Verbinden**.

## Verwenden der Exchange Toolbox, um den Server anzugeben, der von der Warteschlangenanzeige zur Ausführung von Remote PowerShell Servers verwendet werden soll

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**.

3.  Klicken Sie im Aktionsbereich auf **Eigenschaften**.

4.  Wählen Sie im Dialogfeld **Warteschlangenanzeige - \<Servername\> Eigenschaften** eine der folgenden Optionen aus:
    
      - **Verbindung mit dem automatisch ausgewählten Server herstellen**   Wählen Sie diese Option aus, um zum Ausführen von Remote PowerShell automatisch eine Verbindung mit dem Server herzustellen, auf dem die Warteschlangen verwaltet werden.
    
      - **Einen Server zum Verbinden auswählen**   Wählen Sie diese Option aus, um einen Server zum Ausführen von Remote PowerShell anzugeben. Klicken Sie bei Auswahl dieser Option auf **Durchsuchen**, um das Dialogfeld **Exchange-Server auswählen** zu öffnen. Wählen Sie den Server aus, auf dem Remote PowerShell ausgeführt werden soll, und klicken Sie auf **OK**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie sollten jetzt in der Lage sein, die Warteschlangen auf dem Postfachserver zu verwalten, den Sie angegeben haben.

