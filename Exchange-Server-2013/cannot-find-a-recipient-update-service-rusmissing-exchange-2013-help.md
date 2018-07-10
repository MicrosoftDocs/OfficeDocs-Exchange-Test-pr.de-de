---
title: 'Suchen eines Diensts zum Aktualisieren eines Empfängers nicht möglich_RUSMissing: Exchange 2013 Help'
TOCTitle: Suchen eines Diensts zum Aktualisieren eines Empfängers nicht möglich_RUSMissing
ms:assetid: 920fbf51-d5e4-4ac6-869f-7f1c5d9a3024
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.rusmissing(v=EXCHG.150)
ms:contentKeyID: 50476242
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Suchen eines Diensts zum Aktualisieren eines Empfängers nicht möglich\_RUSMissing

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-15_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 oder Exchange Server 2010 kann nicht fortgesetzt werden, da der für eine Domäne zuständige Empfängerupdatedienst in der vorhandenen Exchange-Organisation nicht gefunden werden kann.

Das Microsoft Exchange-Setup fordert an, dass jede Domäne in der vorhandenen Exchange-Organisation eine Instanz des Empfängerupdatesdiensts aufweist.

Wenn eine Instanz des Empfängerupdatesdiensts für eine Domäne fehlt, erhalten neue in der Domäne erstellte Benutzerobjekte die für sie ausgestellten E-Mail-Nachrichten nicht.

Um dieses Problem zu beheben, stellen Sie sicher, dass eine Instanz des Empfängerupdatesdiensts für jede Domäne vorhanden ist. Erstellen Sie eine Instanz des Empfängerupdatesdiensts für die Domänen, die über keine verfügen, und führen Sie das Microsoft Exchange-Setup erneut aus.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>So erstellen Sie eine Instanz des Empfängerupdatesdiensts für eine Domäne</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Öffnen Sie den Exchange-System-Manager.</p></li>
<li><p>Erweitern Sie <strong>Empfänger</strong>.</p></li>
<li><p>Klicken Sie mit der rechten Maustaste auf den Knoten <strong>Empfängerupdatesdienste</strong>, klicken Sie auf <strong>Neu</strong> und dann auf <strong>Empfängerupdatesdienst</strong>.</p></li>
<li><p>Klicken Sie im Fenster Neues Objekt auf <strong>Durchsuchen</strong>, um zum Namen der Domäne zu wechseln.</p></li>
<li><p>Wählen Sie den Namen der Domäne aus, und klicken Sie dann auf <strong>OK</strong>.</p></li>
<li><p>Klicken Sie im Fenster Neues Objekt auf <strong>Weiter</strong> und anschließend auf <strong>Fertig stellen</strong>.</p></li>
</ol></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Empfängerupdatesdienst finden Sie in den folgenden Microsoft Knowledge Base-Artikeln:

  - „Wie wendet der Empfängeraktualisierungsdienst Empfängerrichtlinien“ ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=328738](https://go.microsoft.com/fwlink/?linkid=3052&kbid=328738)).

  - „Wie der Empfängeraktualisierungsdienst Adresslisten aufgefüllt“ ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=253828](https://go.microsoft.com/fwlink/?linkid=3052&kbid=253828)).

  - „Gewusst wie: Überprüfen Sie den Status der Exchange-Empfängeraktualisierungsdienst“ ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=246127](https://go.microsoft.com/fwlink/?linkid=3052&kbid=246127)).

  - „Aufgaben, die Exchange-Empfängeraktualisierungsdienst“ ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=253770](https://go.microsoft.com/fwlink/?linkid=3052&kbid=253770)).

