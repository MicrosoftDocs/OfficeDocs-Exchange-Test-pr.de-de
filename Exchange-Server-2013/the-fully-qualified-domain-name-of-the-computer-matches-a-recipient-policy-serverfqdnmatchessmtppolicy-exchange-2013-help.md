---
title: 'Der vollqualifizierte Domänenname des Computers entspricht einer Empfängerrichtlinie_ServerFQDNMatchesSMTPPolicy: Exchange 2013 Help'
TOCTitle: Der vollqualifizierte Domänenname des Computers entspricht einer Empfängerrichtlinie_ServerFQDNMatchesSMTPPolicy
ms:assetid: f3ea61f8-1788-4cbf-814e-f7c088c1ac47
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.serverfqdnmatchessmtppolicy(v=EXCHG.150)
ms:contentKeyID: 50477058
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Der vollqualifizierte Domänenname des Computers entspricht einer Empfängerrichtlinie\_ServerFQDNMatchesSMTPPolicy

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da der vollqualifizierte Domänenname des lokalen Computers der SMTP-Adresse (Simple Mail Transfer Protocol) einer Empfängerrichtlinie entspricht.

Für das Microsoft Exchange-Setup ist erforderlich, dass der vollqualifizierte Domänenname der Server in einer Exchange-Organisation keinen SMTP-Adressen von Empfängerrichtlinien in derselben Exchange-Organisation entspricht.

Wenn der vollqualifizierte Domänenname eines Computers der SMTP-Adresse einer Empfängerrichtlinie entspricht, kann diese Übereinstimmung dazu führen, dass der Mailtransport über SMTP fehlschlägt und Verzögerungen in den MTA-Warteschlangen auftreten.

Um dieses Problem zu beheben, können Sie den lokalen Computer umbenennen bzw. die Empfängerrichtlinie entfernen oder umbenennen. Führen Sie anschließend das Microsoft Exchange-Setup erneut aus.

**So benennen Sie den lokalen Computer um**

1.  Wählen Sie in **Systemsteuerung** die Option **System** aus.

2.  Klicken Sie auf der Registerkarte **Computername** auf **Ändern**.

3.  Geben Sie unter **Computername** einen neuen Namen für den Computer ein, und klicken Sie anschließend auf **OK**. Sie werden aufgefordert, einen Benutzernamen und ein Kennwort anzugeben, um den Computer in der Domäne umzubenennen.

4.  Klicken Sie auf **OK**, um das Dialogfeld **Systemeigenschaften** zu schließen. Sie werden aufgefordert, den Computer neu zu starten, damit die Änderungen wirksam werden.


> [!IMPORTANT]
> Wenn der umzubenennende Computer ein Domänencontroller ist, lesen Sie "Rename a domain controller" (<A href="https://go.microsoft.com/fwlink/?linkid=66828">https://go.microsoft.com/fwlink/?LinkId=66828</A>).



**So ändern Sie die SMTP-Adresse der Empfängerrichtlinie**

1.  Starten Sie Exchange-System-Manager.

2.  Klicken Sie auf **Organisation**, klicken Sie anschließend auf **Empfänger** und dann auf **Empfängerrichtlinien**.

3.  Doppelklicken Sie auf die zu ändernde Richtlinie.

4.  Klicken Sie auf die Registerkarte **E-Mail-Adressen**, und ändern Sie die entsprechende SMTP-Adresse.

Weitere Informationen zu Umbenennungsproblemen bei Empfängerrichtlinien finden Sie im Microsoft Knowledge Base-Artikel 288175 „XCON: Recipient Policy Cannot Match the FQDN of Any Server in the Organization, 5.4.8 NDRs" ([http://go.microsoft.com/fwlink/?linkid=3052\&kbid=288175](http://go.microsoft.com/fwlink/?linkid=3052&kbid=288175)).

