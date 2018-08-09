---
title: 'WWW-Publishingdienst ist deaktiviert oder nicht vorhanden'
TOCTitle: The World Wide Web Publishing Service is disabled or missing_W3SVCDisabledOrNotInstalled
ms:assetid: 2d26d778-ddf1-4225-b5e2-f6b49d819c94
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.w3svcdisabledornotinstalled(v=EXCHG.150)
ms:contentKeyID: 50475258
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# The World Wide Web Publishing Service is disabled or missing\_W3SVCDisabledOrNotInstalled

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da beim Versuch der Installation derPostfach- bzw. der Clientzugriffs-Serverrolle festgestellt wurde, dass der WWW-Veröffentlichungsdienst entweder deaktiviert oder nicht auf diesem Computer installiert ist.

Für das Setup von Exchange 2007 ist erforderlich, dass auf dem Computer, auf dem Sie Microsoft Exchange installieren, der WWW-Veröffentlichungsdienst installiert ist und keinen deaktivierten Status hat.

Um dieses Problem zu beheben, vergewissern Sie sich, dass der WWW-Veröffentlichungsdienst auf dem lokalen Computer installiert und nicht deaktiviert ist, und führen anschließend das Microsoft Exchange-Setup erneut aus.

**So überprüfen Sie, ob der WWW-Veröffentlichungsdienst installiert und nicht deaktiviert ist**

1.  Klicken Sie auf dem Desktop mit der rechten Maustaste auf **Arbeitsplatz**, und klicken Sie dann auf **Verwalten**.

2.  Erweitern Sie den Knoten **Dienste und Anwendungen**, und klicken Sie dann auf den Knoten **Dienste**.

3.  Suchen Sie im rechten Bereich **WWW-Veröffentlichungsdienst**.
    
    Wenn **WWW-Veröffentlichungsdienst** in der Liste der installierten Dienste nicht angezeigt wird, befolgen Sie die nachfolgenden Anweisungen, um den Dienst zu installieren.

4.  Wird **WWW-Veröffentlichungsdienst** angezeigt, verfügt aber über einen anderen Status als **Gestartet**, fahren Sie mit den nachfolgenden Schritten fort, um den Dienst zu starten.

5.  Klicken Sie mit der rechten Maustaste auf **WWW-Veröffentlichungsdienst**, und klicken Sie dann auf **Eigenschaften**.

6.  Stellen Sie sicher, dass **Starttype** auf **Automatisch** und der **Dienststatus** auf **Gestartet** festgelegt ist.

7.  Klicken Sie auf **Anwenden**, und klicken Sie dann auf **OK**.

**So installieren Sie den WWW-Veröffentlichungsdienst**

1.  Klicken Sie im Menü **Start** auf **Einstellungen**, **Systemsteuerung** und dann auf **Software**.

2.  Klicken Sie auf **Windows-Komponenten hinzufügen/entfernen**.

3.  Aktivieren Sie in der Liste **Komponenten** das Kontrollkästchen **Anwendungsserver**, und klicken Sie dann auf **Details**.

4.  Wählen Sie **Internetinformationsdienste-Manager** aus, und klicken Sie dann auf **Details**.

5.  Wählen Sie **WWW-Veröffentlichungsdienst** aus, und aktivieren Sie das Kontrollkästchen.

6.  Klicken Sie zum zweimal auf **OK**, um zur Liste **Komponenten** zurückzukehren, und klicken Sie dann auf**Weiter**.

7.  Klicken Sie auf **Fertig stellen**, wenn der IIS-Dienst installiert ist.

