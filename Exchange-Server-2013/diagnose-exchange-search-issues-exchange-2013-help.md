---
title: 'Problemdiagnose für die Exchange-Suche: Exchange 2013 Help'
TOCTitle: Problemdiagnose für die Exchange-Suche
ms:assetid: 8cfa26f4-ccf0-42dd-8570-67018188b4e8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123701(v=EXCHG.150)
ms:contentKeyID: 52062877
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problemdiagnose für die Exchange-Suche

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Die Exchange-Suche indiziert Postfächer und unterstützte Anlagen in Exchange-Postfächern. Bei zunehmenden E-Mail-Mengen, größer werdenden Postfächern und Speicherkontingenten, der Bereitstellung von Archivpostfächern für Benutzer und der In-Situ-eDiscovery für das Ausführen von Discoverysuchen ist die Exchange-Suche eine entscheidende Komponente des Postfachservers in Ihrer Microsoft Exchange Server 2013-Organisation. Probleme im Zusammenhang mit der Exchange-Suche können sich auf die Benutzerproduktivität auswirken und die In-Situ-eDiscovery-Funktionalität beeinträchtigen.

Weitere Informationen zur Exchange-Suche finden Sie unter [Exchange-Suche](exchange-search-exchange-2013-help.md).

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit der Exchange-Suche gibt? Informationen hierzu finden Sie unter [Exchange-Suchverfahren](exchange-search-procedures-exchange-2013-help.md).

## Verwenden des Cmdlets "Test-ExchangeSearch"

In Schritt 5 des Verfahrens in diesem Thema wird beschrieben, wie Sie das Cmdlet **Test-ExchangeSearch** ausführen, um Probleme bei der Exchange-Suche festzustellen. Sie können das Cmdlet **Test-ExchangeSearch** verwenden, um die Funktionalität der Exchange-Suche für einen Postfachserver, eine Postfachdatenbank oder ein bestimmtes Postfach zu testen. Das Cmdlet übermittelt eine Testnachricht an das angegebene Postfach (oder an das Postfach eines Datenbanksystems, wenn kein Postfach angegeben ist) und führt dann eine Suche durch, um zu bestimmen, ob die Nachricht indiziert ist und wie lange ihre Indizierung gedauert hat. Unter normalen Bedingungen indiziert die Exchange-Suche eine Nachricht innerhalb von ca. 10 Sekunden, nachdem die Nachricht erstellt oder an ein Postfach übermittelt wurde. Die Testnachricht wird nach dem Test automatisch gelöscht.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Test-ExchangeSearch](https://technet.microsoft.com/de-de/library/bb124733\(v=exchg.150\)).

## Abrufen von nicht durchsuchbaren Elementen

Sie können das Cmdlet [Get-FailedContentIndexDocuments](https://technet.microsoft.com/de-de/library/dd351154\(v=exchg.150\)) verwenden, um eine Liste von nicht durchsuchbaren Postfachelementen abzurufen, die von der Exchange-Suche nicht erfolgreich indiziert werden konnten. Sie können das Cmdlet für einen Postfachserver, eine Postfachdatenbank oder ein bestimmtes Postfach ausführen. Das Cmdlet gibt Details zu den einzelnen Elementen zurück, die nicht durchsucht werden konnten. Es gibt verschiedene Gründe, weshalb ein Postfachelement nicht gesucht werden kann, beispielsweise kann eine E-Mail einen Anhangsdateityp enthalten, der für die Suche nicht indiziert werden kann, oder es kann auch an einem nicht installierten oder deaktivierten Suchfilter liegen. Wenn ein Suchfilter für diesen Dateityp verfügbar ist, können Sie ihn auf den exExchangeNoVersionExchange-Servern installieren.


> [!IMPORTANT]
> Von Microsoft bereitgestellte Suchfilter werden von Microsoft getestet und unterstützt. Sie sollten jegliche Suchfilter von Drittanbietern in einer Testumgebung testen, bevor Sie sie auf exExchangeNoVersionExchange-Servern in einer Produktionsumgebung installieren.



Weitere Informationen zu nicht durchsuchbaren Elementen finden Sie unter:

  - [Von der Exchange-Suche indizierte Dateiformate](file-formats-indexed-by-exchange-search-exchange-2013-help.md)

  - [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md)

## Problemdiagnose für die Exchange-Suche

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange-Suche" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

1.  **Überprüfen des Dienststatus**   Wurde der Dienst Microsoft Exchange-Suche (MSExchangeFastSearch) auf dem Postfachserver gestartet? Ist dies der Fall, fahren Sie mit Schritt 2 fort. Andernfalls verwenden Sie wie folgt das MMC-Snap-In "Dienste", um zu überprüfen, ob der Dienst MSExchangeFastSearch ausgeführt wird:
    
    1.  Klicken Sie auf **Start**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**.
    
    2.  Überprüfen Sie unter **Dienste**, ob als **Status** für den Dienst **Microsoft Exchange-Suche** der Wert **Gestartet** angegeben ist.

2.  **Überprüfen der Postfachdatenbank-Konfiguration**   Ist der Parameter *IndexEnabled* für die Postfachdatenbank des Benutzers auf "True" festgelegt? Ist dies der Fall, fahren Sie mit Schritt 3 fort. Andernfalls führen Sie den folgenden Befehl in der Shell aus, um zu überprüfen, ob die Kennzeichnung *IndexEnabled* auf TRUE festgelegt wurde:
    
        Get-MailboxDatabase | Format-Table Name,IndexEnabled
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb124924\(v=exchg.150\)).

3.  **Überprüfen des Durchforstungsstatus der Postfachdatenbank**   Wurde die Exchange-Datenbank durchforstet? Wenn dies der Fall ist, wechseln Sie zu Schritt 4. Wenn dies nicht der Fall ist, verwenden Sie die Zuverlässigkeits- und Leistungsüberwachung zum Überprüfen des Zählers **Crawler: Verbleibende Postfächer** des **MSExchange Search Indexes**-Leistungsobjekts. Führen Sie die folgenden Schritte aus:
    
    1.  Öffnen Sie **Systemmonitor** („perfmon.exe“).
    
    2.  Klicken Sie in der Konsolenstruktur unter **Überwachungsprogramme** auf **Systemmonitor**.
    
    3.  Klicken Sie im Systemmonitorbereich auf **Hinzufügen** (grünes Pluszeichen).
    
    4.  Wählen Sie unter **Leistungsindikatoren hinzufügen** in der Liste **Leistungsindikatoren auswählen von Computer** den Server aus, auf dem sich die zu überwachende Postfachdatenbank befindet.
    
    5.  Wählen Sie im nicht beschrifteten Feld unter der Liste **Leistungsindikatoren auswählen von Computer** das Leistungsobjekt **MSExchange-Suchindizes** aus.
    
    6.  Wählen Sie im Feld **Instanzen des ausgewählten Objekts** die Instanz für die Postfachdatenbank des Benutzers aus.
    
    7.  Klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.
        
        Im Systemmonitorbereich wird das Leistungsobjekt **MSExchange-Suchindizes** in der Spalte **Objekt** aufgeführt, und die zugehörigen Leistungsindikatoren werden in der Spalte **Leistungsindikator** aufgeführt.
    
    8.  Zeigen Sie den Zähler **Crawler: Verbleibende Postfächer** an. Ein Wert von mindestens „1“ zeigt an, dass die Postfächer in der Datenbank weiterhin durchforstet werden. Wenn die Durchforstung abgeschlossen ist, ist der Wert **0**.
    
    Informationen zur Verwendung des Systemmonitors finden Sie unter [Schrittweise Anleitung für die Leistungs- und Zuverlässigkeitsüberwachung in Windows Server 2008](https://go.microsoft.com/fwlink/p/?linkid=178005)

4.  **Statusüberprüfung der Indizierung für die Datenbankkopie**   Ist der Inhaltsindex fehlerfrei? Verwenden Sie das Cmdlet **Get-MailboxDatabaseCopyStatus**, um den Status der Inhaltsindizierung für eine Datenbankkopie zu überprüfen.
    
        Get-MailboxDatabaseCopyStatus -Server $env:ComputerName | Format-Table Name,Status,ContentIndex* -Auto
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MailboxDatabaseCopyStatus](https://technet.microsoft.com/de-de/library/dd298044\(v=exchg.150\)).

5.  **Ausführung des Cmdlets "Test-ExchangeSearch"**   Wenn die Postfachdatenbank bereits durchforstet wurde, können Sie das Cmdlet **Test-ExchangeSearch** für die Postfachdatenbank oder für ein bestimmtes Postfach ausführen.
    
        Test-ExchangeSearch -Identity AlanBrewer@contoso.com
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Test-ExchangeSearch](https://technet.microsoft.com/de-de/library/bb124733\(v=exchg.150\)).

6.  **Überprüfung des Anwendungsereignisprotokolls**   Überprüfen Sie mithilfe der Ereignisanzeige oder der Shell das Anwendungsereignisprotokoll auf Fehlermeldungen im Zusammenhang mit der Suche. Nehmen Sie eine Überprüfung hinsichtlich der folgenden Ereignisquellen vor.
    
      - **MSExchangeFastSearch**
    
      - **MSExchangeIS**
    
    Weitere Informationen erhalten Sie, wenn Sie dem Link zum Ereignisprotokolleintrag folgen.

7.  **Neustart des Microsoft Exchange-Suchdiensts**   Verwenden Sie das MMC-Snap-In "Dienste" oder die Shell, um den Microsoft Exchange-Suchdienst (MSExchangeFastSearch) zu beenden und dann neu zu starten:
    
    1.  Klicken Sie auf **Start**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**.
    
    2.  Klicken Sie unter **Dienste** mit der rechten Maustaste auf **Microsoft Exchange-Suche**, und klicken Sie dann auf **Beenden**. Nachdem der Dienst beendet wurde, klicken Sie nochmals mit der rechten Maustaste auf den Dienst, und klicken Sie dann auf **Starten**.

8.  **Ausführung eines erneuten Seedings für den Suchkatalog**   In einigen Fällen, wie z. B. bei Beschädigung des Suchkatalogs, müssen Sie möglicherweise ein erneutes Seeding für den Katalog ausführen. Wenn ein erneutes Seeding für einen Suchkatalog erforderlich ist, werden Sie von der Exchange-Suche durch Protokollierung von Einträgen im Anwendungsereignisprotokoll benachrichtigt. Weitere Informationen zum erneuten Seeding des Suchkatalogs finden Sie unter [Durchführen eines erneuten Seedings des Suchkatalogs](reseed-the-search-catalog-exchange-2013-help.md).

