---
title: 'Primäres DNS-Suffix fehlt: Exchange 2013 Help'
TOCTitle: Primäres DNS-Suffix fehlt
ms:assetid: 310765bf-a650-4a3d-a5e4-6173b559d4f6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.fqdnmissing(v=EXCHG.150)
ms:contentKeyID: 61201336
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Primäres DNS-Suffix fehlt

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2014-01-15_

Microsoft Exchange Server 2013 Setup kann nicht fortgesetzt werden, da das primäre DNS-Suffix (Domänennamensystem, Domain Name System) für den Computer, auf dem Sie Exchange installieren, nicht konfiguriert wurde.

Fügen Sie zum Beheben dieses Problems mithilfe der folgenden Schritte ein primäres DNS-Suffix auf dem Computer hinzu, und führen Sie das Setup anschließend erneut aus.


> [!IMPORTANT]
> Das Ändern des Computernamens oder des primären DNS-Suffixes nach der Installation von Exchange 2013 wird nicht unterstützt.



1.  Melden Sie sich an dem Computer, auf dem Sie die Rolle "Edge-Transport" installieren möchten, als ein Benutzer an, der Mitglied der lokalen Administratorengruppe ist.

2.  Öffnen Sie die **Systemsteuerung**, und doppelklicken Sie dann auf **System**.

3.  Klicken Sie im Abschnitt **Einstellungen für Computername, Domäne und Arbeitsgruppe** auf **Einstellungen ändern**.

4.  Stellen Sie im Fenster **Systemeigenschaften** sicher, dass die Registerkarte **Computername** ausgewählt ist, und klicken Sie dann auf **Ändern…**.

5.  Klicken Sie in **Computernamen- bzw. -domänenänderungen** auf **Weitere...**.

6.  Geben Sie im Feld **Primäres DNS-Suffix dieses Computers** den DNS-Domänennamen für den Edge-Transport-Server ein. Beispiel: "contoso.com".

7.  Klicken Sie auf **OK**, um alle Fenster zu schließen.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

