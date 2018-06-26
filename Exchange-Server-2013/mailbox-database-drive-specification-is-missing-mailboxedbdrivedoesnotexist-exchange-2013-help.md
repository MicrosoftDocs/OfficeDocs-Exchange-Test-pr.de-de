---
title: 'Laufwerksangabe für Postfachdatenbank fehlt_MailboxEDBDriveDoesNotExist: Exchange 2013 Help'
TOCTitle: Laufwerksangabe für Postfachdatenbank fehlt_MailboxEDBDriveDoesNotExist
ms:assetid: 0e487aa1-3194-4a14-b255-a8b9f9afbf0e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.mailboxedbdrivedoesnotexist(v=EXCHG.150)
ms:contentKeyID: 50475012
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Laufwerksangabe für Postfachdatenbank fehlt\_MailboxEDBDriveDoesNotExist

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup zur Wiederherstellung nach Datenverlust von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da dieses Setup nicht auf die Laufwerksangabe der Postfachdatenbank zugreifen kann, die bei der vorherigen Installation dieses Serverprogramms verwendet wurde.

Das Setup zur Wiederherstellung nach Datenverlust von Microsoft Exchange erfordert, dass die zuvor für diesen Server verwendeten Laufwerksangaben für die Postfachdatenbank während der Wiederherstellung verfügbar sind.

Konfigurieren Sie zum Beheben dieses Problems die Laufwerke so, dass diese der ursprünglichen logischen Laufwerkskonfiguration entsprechen, und führen Sie das Microsoft Exchange-Setup zur Wiederherstellung nach Datenverlust erneut aus.

Zuweisen oder Ändern eines Laufwerksbuchstaben

1.  Öffnen Sie **Computerverwaltung(Lokal)**.

2.  Klicken Sie in der Konsolenstruktur auf **Computerverwaltung (Lokal)**, klicken Sie auf **Datenspeicher**, und klicken Sie dann auf **Datenträgerverwaltung**.

3.  Klicken Sie mit der rechten Maustaste auf eine Partition, ein logisches Laufwerk oder ein Volume, und klicken Sie dann auf **Laufwerkbuchstaben und -pfade ändern**.

4.  Verwenden Sie eines der folgenden Verfahren:
    
      - Um einen Laufwerksbuchstaben zuzuweisen, klicken Sie auf **Hinzufügen**, dann auf den gewünschten Laufwerksbuchstaben und schließlich auf **OK**.
    
      - Um einen Laufwerksbuchstaben zu ändern, klicken Sie auf **Ändern**, dann auf den gewünschten Laufwerksbuchstaben und schließlich auf **OK**.

Weitere Informationen dazu, wie Sie Laufwerkbuchstaben zuweisen, finden Sie unter "Zuweisen, ändern oder Entfernen von Laufwerkbuchstaben" ([https://go.microsoft.com/fwlink/?LinkId=66764](https://go.microsoft.com/fwlink/?linkid=66764)).

