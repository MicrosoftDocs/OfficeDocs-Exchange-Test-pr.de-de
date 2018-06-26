---
title: 'Auf dem lokalen Computer wird Exchange Server bereits ausgeführt_ExchangeAlreadyInstalled: Exchange 2013 Help'
TOCTitle: Auf dem lokalen Computer wird Exchange Server bereits ausgeführt_ExchangeAlreadyInstalled
ms:assetid: 3f168b5d-9910-418f-86fb-e99d852dcb5e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.exchangealreadyinstalled(v=EXCHG.150)
ms:contentKeyID: 50475527
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Auf dem lokalen Computer wird Exchange Server bereits ausgeführt\_ExchangeAlreadyInstalled

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da auf dem lokalen Computer vorherige Microsoft Exchange-Komponenten installiert sind.

Für das Setup von Microsoft® Exchange Server 2007 ist erforderlich, dass auf dem lokalen Computer keine vorherigen Microsoft Exchange-Komponenten installiert sind.

Um dieses Problem zu beheben, entfernen Sie Microsoft Exchange 2000 Server- oder Microsoft Exchange Server 2003-Komponenten und führen anschließend das Microsoft Exchange-Setup erneut aus.

So entfernen Sie Microsoft Exchange-Komponenten

1.  Klicken Sie auf **Start**, zeigen Sie auf**Einstellungen**, und klicken Sie auf **Systemsteuerung**.

2.  Doppelklicken Sie auf **Software**.

3.  Klicken Sie in der Liste **Zurzeit installierte Programme** auf **Microsoft Exchange**, und klicken Sie dann auf **Ändern/Entfernen**.

4.  Klicken Sie im Microsoft Exchange-Installations-Assistenten auf **Weiter**.

5.  Klicken Sie in der Liste „Aktion\&quot; auf der Seite „Auswahl der Komponenten\&quot; auf den Nach-Unten-Pfeil neben jeder installierten Komponente, und klicken Sie dann auf **Entfernen**.
    

    > [!NOTE]
    > Bei installierten Komponenten wird in der Liste „Aktion&amp;quot; ein Häkchen angezeigt. Wenn Sie auf <STRONG>Entfernen</STRONG> klicken, wird das Häkchen durch das Wort <STRONG>Entfernen</STRONG> ersetzt.



6.  Klicken Sie zweimal auf **Weiter**.

7.  Klicken Sie auf **Fertig stellen**.

