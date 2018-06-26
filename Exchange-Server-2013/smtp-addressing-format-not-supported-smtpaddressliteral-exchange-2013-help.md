---
title: 'Das SMTP-Adressierungsformat wird nicht unterstützt_SMTPAdressLiteral: Exchange 2013 Help'
TOCTitle: Das SMTP-Adressierungsformat wird nicht unterstützt_SMTPAdressLiteral
ms:assetid: b8b55917-d81f-4c0a-ad65-7bb10ac58df8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.smtpaddressliteral(v=EXCHG.150)
ms:contentKeyID: 50476551
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Das SMTP-Adressierungsformat wird nicht unterstützt\_SMTPAdressLiteral

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 und Exchange Server 2010 kann nicht fortgesetzt werden, weil die angegebene Empfängerrichtlinie ein nicht unterstütztes SMTP-Adressformat (Simple Mail Transfer Protocol) verwendet.

Das Setup von Exchange 2007 und Exchange 2010 erfordert, dass alle SMTP-Adressen, die für E-Mail-Adressenrichtlinien verwendet werden, keine IP-Adressliterale enthalten. Beispiel: *user@\[10.10.1.1\]*.

Um dieses Problem zu beheben, ändern Sie den Wert der SMTP-Adresse in der Empfängerrichtlinie so, dass sie keine IP-Adressliterale enthält. Ersetzen Sie eckige Klammern (\[\]) und Ziffern (10.10.1.1) der IP-Adressliterale durch Angaben im DNS-Namensformat (Domain Name System). Beispiel: *user@contoso.com*. Führen Sie dann das Setup von Exchange erneut aus.

Weitere Informationen zum Verwalten von Empfängerrichtlinien in Exchange Server 2007 finden Sie unter "Verwalten von E-Mail-Adressenrichtlinien" ([https://go.microsoft.com/fwlink/?LinkId=86653](https://go.microsoft.com/fwlink/?linkid=86653)).

Weitere Informationen zum Verwalten von Empfängerrichtlinien in Exchange Server 2010 finden Sie unter "Verwalten von E-Mail-Adressenrichtlinien" (([https://go.microsoft.com/fwlink/?LinkId=179519](https://go.microsoft.com/fwlink/?linkid=179519)).

