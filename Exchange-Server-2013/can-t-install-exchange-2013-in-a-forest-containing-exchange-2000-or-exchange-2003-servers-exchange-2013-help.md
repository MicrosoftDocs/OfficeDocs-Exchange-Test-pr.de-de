---
title: 'Exchange 2013 kann nicht in einer Gesamtstruktur mit Exchange 2000- oder Exchange 2003-Servern installiert werden.: Exchange 2013 Help'
TOCTitle: Exchange 2013 kann nicht in einer Gesamtstruktur mit Exchange 2000- oder Exchange 2003-Servern installiert werden.
ms:assetid: a115b182-cbd2-4d31-aa0e-375240939301
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.exchange2000or2003presentinorg(v=EXCHG.150)
ms:contentKeyID: 50476330
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013 kann nicht in einer Gesamtstruktur mit Exchange 2000- oder Exchange 2003-Servern installiert werden.

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft Exchange Server 2013 kann nicht fortgesetzt werden, da ein oder mehrere Computer mit Exchange 2000 Server oder Exchange Server 2003 in der Active Directory-Gesamtstruktur gefunden wurden. Vor der Installation von Exchange 2013 müssen alle Exchange 2000- und Exchange 2003-Server aus der Gesamtstruktur entfernt werden. Postfächer, öffentliche Ordner und alle anderen Exchange-Objekte oder -Komponenten müssen entweder auf Exchange Server 2007 oder auf Exchange Server 2010 aktualisiert werden. Sie können kein direktes Upgrade von Exchange 2000 oder Exchange 2003 auf Exchange 2013 ausführen.

Der Pfad für die Installation von Exchange 2013 in Ihrer Organisation hängt von der Exchange-Version ab, die derzeit in der Gesamtstruktur installiert ist. Weitere Informationen finden Sie in der folgenden Tabelle.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Installiert in Ihrer Organisation</th>
<th>Pfad zum Upgrade auf Exchange 2013</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2000</p></td>
<td><ol>
<li><p>Installieren Sie Exchange 2007 in Ihrer Exchange 2000-Organisation.</p></li>
<li><p>Konfigurieren Sie die Koexistenz von Exchange 2007 und Exchange 2000.</p></li>
<li><p>Migrieren Sie Postfächer, öffentliche Ordner und andere Komponenten von Exchange 2000 zu Exchange 2007.</p></li>
<li><p>Setzen Sie alle Exchange 2000-Server außer Betrieb, und entfernen Sie sie.</p></li>
<li><p>Installieren Sie Exchange 2013 in Ihrer Exchange 2007-Organisation.</p></li>
<li><p>Konfigurieren Sie die Koexistenz von Exchange 2013 und Exchange 2007.</p></li>
<li><p>Migrieren Sie Postfächer, öffentliche Ordner und andere Komponenten von Exchange 2007 zu Exchange 2013.</p></li>
<li><p>Setzen Sie alle Exchange 2007-Server außer Betrieb, und entfernen Sie sie.</p></li>
</ol>
<p>Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=103281">Aktualisieren auf Exchange 2007</a> und <a href="upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Aktualisieren von Exchange 2007 auf Exchange 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2003</p></td>
<td><ol>
<li><p>Installieren Sie Exchange 2010 in Ihrer Exchange 2003-Organisation.</p></li>
<li><p>Konfigurieren Sie die Koexistenz von Exchange 2010 und Exchange 2003.</p></li>
<li><p>Migrieren Sie Postfächer, öffentliche Ordner und andere Komponenten von Exchange 2003 zu Exchange 2010.</p></li>
<li><p>Setzen Sie alle Exchange 2003-Server außer Betrieb, und entfernen Sie sie.</p></li>
<li><p>Installieren Sie Exchange 2013 in Ihrer Exchange 2010-Organisation.</p></li>
<li><p>Konfigurieren Sie die Koexistenz von Exchange 2013 und Exchange 2010.</p></li>
<li><p>Migrieren Sie Postfächer, öffentliche Ordner und andere Komponenten von Exchange 2010 zu Exchange 2013.</p></li>
<li><p>Setzen Sie alle Exchange 2010-Server außer Betrieb, und entfernen Sie sie.</p></li>
</ol>
<p>Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=268414">Exchange 2003 – Planungswegweiser für Upgrade und Koexistenz</a> und <a href="upgrade-from-exchange-2010-to-exchange-2013-exchange-2013-help.md">Aktualisieren von Exchange 2010 auf Exchange 2013</a>.</p></td>
</tr>
</tbody>
</table>


Beim Upgrade auf Exchange 2010 oder Exchange 2013 können Sie den Exchange-Bereitstellungs-Assistenten verwenden, um die Bereitstellung abzuschließen. Weitere Informationen finden Sie unter den folgenden Links:

  - [Exchange 2010-Bereitstellungs-Assistent](https://go.microsoft.com/fwlink/p/?linkid=171086)

  - [Exchange 2013-Bereitstellungs-Assistent](https://go.microsoft.com/fwlink/p/?linkid=277105)

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

