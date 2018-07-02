---
title: 'Der COM+-Ereignissystemdienst muss gestartet werden, bevor Setup fortgesetzt werden kann_EventSystemStopped: Exchange 2013 Help'
TOCTitle: Der COM+-Ereignissystemdienst muss gestartet werden, bevor Setup fortgesetzt werden kann_EventSystemStopped
ms:assetid: 3b8d2ba3-87fb-4749-b4d1-5dfec97e1ca4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.eventsystemstopped(v=EXCHG.150)
ms:contentKeyID: 50475364
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Der COM+-Ereignissystemdienst muss gestartet werden, bevor Setup fortgesetzt werden kann\_EventSystemStopped

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, da beim Versuch der Installation der Clientzugriffs-Serverrolle bzw. der Edge-Transport-Serverrolle ein Fehler aufgetreten ist, weil der COM+-Ereignissystemdienst auf dem Zielcomputer nicht gestartet wurde.

Das Setup von Exchange 2007 erfordert, dass auf dem Computer, auf dem Sie Microsoft Exchange installieren, der Status des COM+-Ereignissystemdiensts auf **Gestartet** festgelegt ist.

Der COM+-Ereignissystemdienst unterstützt die Systemereignisbenachrichtigung für COM+-Komponenten, die die automatische Verteilung von Ereignissen an abonnierende COM-Komponenten bereitstellen.

Die Clientzugriffs-Serverrolle bzw. die Edge-Transport-Serverrolle hängen von COM+-Komponenten ab, die den COM+-Ereignissystemdienst abonnieren.

Um dieses Problem zu beheben, vergewissern Sie sich, dass der Status des COM+-Ereignissystemdiensts auf dem lokalen Computer auf **Gestartet** festgelegt ist, und führen anschließend das Microsoft Exchange-Setup erneut aus.

So legen Sie den Status des COM+-Ereignissystemdiensts auf "Gestartet" fest

1.  Klicken Sie mit der rechten Maustaste auf **Arbeitsplatz**, und klicken Sie dann auf **Verwalten**.

2.  Erweitern Sie den Knoten **Dienste und Anwendungen**, und klicken Sie dann auf den Knoten **Dienste**.

3.  Suchen Sie im rechten Bereich das **Com+-Ereignissystem**.

4.  Klicken Sie mit der rechten Maustaste auf **Com+-Ereignissystem**, und klicken Sie dann auf **Eigenschaften**.

5.  Legen Sie den **Starttyp** auf **Automatisch** und den **Dienststatus** auf **Gestartet** fest.

6.  Klicken Sie auf **Übernehmen** und dann auf **OK**.

