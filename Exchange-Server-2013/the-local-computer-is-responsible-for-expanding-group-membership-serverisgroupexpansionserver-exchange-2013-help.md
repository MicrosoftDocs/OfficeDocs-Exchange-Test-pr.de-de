---
title: 'The local computer is responsible for expanding group membership_ServerIsGroupExpansionServer: Exchange 2013 Help'
TOCTitle: The local computer is responsible for expanding group membership_ServerIsGroupExpansionServer
ms:assetid: 52872561-60e6-4f3d-bbc6-6de0edf74b09
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.serverisgroupexpansionserver(v=EXCHG.150)
ms:contentKeyID: 50475658
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# The local computer is responsible for expanding group membership\_ServerIsGroupExpansionServer

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da der Versuch der Deinstallation einer Hub-Transport-Serverrolle fehlgeschlagen ist, die für die Aufgliederung der Gruppenmitgliedschaft zuständig ist.

Für das Setup von Exchange 2007 ist erforderlich, dass die Verteilerlistenaufgliederung vom aktuellen Bridgeheadserver entfernt wird, bevor die Hub-Transport-Serverrolle deinstalliert werden kann.

Die Aufgliederung von Verteilerlisten ermöglicht die Identifikation einzelner Empfänger, die zu der zu identifizierenden Verteilerliste gehören, bzw. die Identifikation weiterer aufzugliedernder Verteilerlisten. Eine aufgegliederte Verteilerliste kann den Pfad beliebiger erforderlicher Benachrichtigungen über den Übermittlungsstatus zurückgeben. Benachrichtigungen über den Übermittlungsstatus informieren den Microsoft Exchange-Administrator oder E-Mail-Absender über den Status einer bestimmten E-Mail-Nachricht. Darüber hinaus bestimmt die Aufgliederung von Verteilerlisten, ob Abwesenheitsnachrichten oder automatisch generierte Antworten an den Absender der ursprünglichen Nachricht gesendet werden sollen.

Um dieses Problem zu beheben, verschieben Sie die Verteilerlistenaufgliederung auf einen anderen Server und führen das Microsoft Exchange-Setup erneut aus.

**So ändern Sie den Server für die Aufgliederung einer Verteilergruppe bzw. dynamischen Verteilergruppe**

1.  Öffnen Sie die Exchange-Verwaltungskonsole.

2.  Erweitern Sie in der Konsolenstruktur die Option **Empfängerkonfiguration**.

3.  Klicken Sie in der Konsolenstruktur auf **Verteilergruppe**.

4.  Erstellen Sie einen Filter zum Anzeigen aller Verteilergruppen und dynamischen Verteilergruppen, die den aktuellen Bridgeheadserver gegenwärtig als Server für die Aufgliederung der Verteilerlisten verwenden.
    
    1.  Klicken Sie im Aktionsbereich auf **Filter erstellen**.
    
    2.  Klicken Sie in der Eigenschaften-Dropdownliste auf **Server für die Aufgliederung der Verteilerlisten**.
    
    3.  Klicken Sie in der Operator-Dropdownliste auf **Gleich**.
    
    4.  Klicken Sie im Wertfeld auf **Durchsuchen**, um den Bridgeheadserver auszuwählen, der gegenwärtig als Server für die Aufgliederung der Verteilerlisten fungiert.


> [!NOTE]
> Der folgende Schritt ist optional.



1.  Klicken Sie auf **Ausdruck hinzufügen**, um weitere Filterkriterien anzugeben. Es werden nur Nachrichten angezeigt, die allen Filterkriterien entsprechen.

2.  Klicken Sie auf **Filter anwenden**. Die Ergebnisse, die die Filterkriterien erfüllen, werden angezeigt.

<!-- end list -->

1.  Klicken Sie im Ergebnisbereich auf die Verteilergruppe, deren Server für die Aufgliederung der Verteilerlisten Sie ändern möchten, und anschließend im Aktionsbereich auf **Eigenschaften**.

2.  Klicken Sie im Dialogfeld **Eigenschaften** auf die Registerkarte **Erweitert**.

3.  Wählen Sie in der Dropdownliste der Server für die Aufgliederung der Verteilerlisten einen bestimmten Server in der Liste oder **Alle Server in der Organisation** aus.

4.  Wiederholen Sie die Schritte 5 bis 7 für alle Verteilergruppen und dynamischen Verteilergruppen, die den aktuellen Bridgeheadserver gegenwärtig als Server für die Aufgliederung der Verteilerlisten verwenden.

