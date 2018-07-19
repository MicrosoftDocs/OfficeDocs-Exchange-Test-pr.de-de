---
title: 'Laufwerksangabe für Speichergruppe fehlt_MailboxLogDriveDoesNotExist: Exchange 2013 Help'
TOCTitle: Laufwerksangabe für Speichergruppe fehlt_MailboxLogDriveDoesNotExist
ms:assetid: fe210f29-60cb-4d34-877e-1356a21dc02a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.mailboxlogdrivedoesnotexist(v=EXCHG.150)
ms:contentKeyID: 50477146
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Laufwerksangabe für Speichergruppe fehlt\_MailboxLogDriveDoesNotExist

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup zur Wiederherstellung nach Datenverlust von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da dieses Setup nicht auf die Laufwerksangabe der Speichergruppe zugreifen kann, die bei der vorherigen Installation dieses Serverprogramms verwendet wurde.

Das Setup zur Wiederherstellung nach Datenverlust von Microsoft Exchange erfordert, dass die zuvor für diesen Server verwendeten Laufwerksangaben für die Speichergruppe während der Wiederherstellung verfügbar sind.

Konfigurieren Sie zum Beheben dieses Problems die Laufwerke so, dass diese der ursprünglichen logischen Laufwerkskonfiguration entsprechen, und führen Sie das Microsoft Exchange-Setup zur Wiederherstellung nach Datenverlust erneut aus.

**Zuweisen oder Ändern eines Laufwerksbuchstaben**

1.  Öffnen Sie **Computerverwaltung(Lokal)**.

2.  Klicken Sie in der Konsolenstruktur auf **Computerverwaltung (Lokal)**, klicken Sie auf **Datenspeicher**, und klicken Sie dann auf **Datenträgerverwaltung**.

3.  Klicken Sie mit der rechten Maustaste auf eine Partition, ein logisches Laufwerk oder ein Volume, und klicken Sie dann auf **Laufwerkbuchstaben und -pfade ändern**.

4.  Verwenden Sie eines der folgenden Verfahren:
    
      - Um einen Laufwerksbuchstaben zuzuweisen, klicken Sie auf **Hinzufügen**, dann auf den gewünschten Laufwerksbuchstaben und schließlich auf **OK**.
    
      - Um einen Laufwerksbuchstaben zu ändern, klicken Sie auf **Ändern**, dann auf den gewünschten Laufwerksbuchstaben und schließlich auf **OK**.

Weitere Informationen zum Zuweisen von Laufwerksbuchstaben finden Sie in „Zuweisen, Ändern und Entfernen von Laufwerkbuchstaben“ ([https://go.microsoft.com/fwlink/?LinkId=66764](https://go.microsoft.com/fwlink/?linkid=66764)).

