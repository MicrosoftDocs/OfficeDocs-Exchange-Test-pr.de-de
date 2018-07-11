---
title: 'Installation von Exchange 2007-Rollen nach der Vorbereitung von Active Directory für Exchange 2010 nicht möglich_NoE12ServerWarning: Exchange 2013 Help'
TOCTitle: Installation von Exchange 2007-Rollen nach der Vorbereitung von Active Directory für Exchange 2010 nicht möglich_NoE12ServerWarning
ms:assetid: 4e579f69-0de9-421c-ba31-4e63a25e6a45
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.noe12serverwarning(v=EXCHG.150)
ms:contentKeyID: 50475617
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installation von Exchange 2007-Rollen nach der Vorbereitung von Active Directory für Exchange 2010 nicht möglich\_NoE12ServerWarning

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Wenn Sie Microsoft Exchange Server 2010**Setup /PrepareAD** ausführen, fragt das Microsoft Exchange Server Analyzer-Tool die vorhandene Active Directory-Topologie ab, um festzustellen, ob Microsoft Exchange Server 2007-Serverrollen vorhanden sind. Wenn keine Exchange 2007-Serverrollen erkannt wurden, wird die folgende Fehlermeldung angezeigt:


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Setup is going to prepare the organization for Exchange Server 2010 via 'Setup /PrepareAD' and no Exchange Server 2007 roles have been detected in this topology. After this operation, it will be impossible to install any Exchange Server 2007 roles. (Setup bereitet die Organisation für Exchange Server 2010 mithilfe von 'Setup /PrepareAD' vor, und es wurden keine Exchange Server 2007-Serverrollen in dieser Topologie erkannt. Nach diesem Vorgang ist es nicht mehr möglich, Exchange Server 2007-Serverrollen zu installieren.)</p></td>
</tr>
</tbody>
</table>


Beachten Sie vor dem Bereitstellen von Exchange Server 2010 die folgenden Faktoren, die Sie möglicherweise vor der Bereitstellung von Exchange 2007 zwingen, einen Exchange 2007-Server mit allen installierten Serverrollen bereitzustellen:

  - **Drittanbieter- oder selbst entwickelte Anwendungen**   Für Exchange 2003 entwickelte Anwendungen sind möglicherweise nicht mit Exchange 2010 kompatibel und müssen daher aktualisiert oder ersetzt werden. Sie können diese Anwendungen und die zugehörige Benutzerauffüllung auf Exchange 2003 verwalten, zu Exchange 2007 verschieben oder die Software durch eine kompatible Version für Exchange 2010 ersetzen.

  - **Koexistenz- oder Migrationsanforderungen**   Wenn Sie planen, Postfächer zu Ihrer Organisation zu migrieren, können Sie entweder Exchange 2007 bereitstellen und Microsoft Transporter Suite verwenden, oder Sie können eine Drittanbieterkoexistenz- oder -migrationslösung verwenden. Navigieren Sie zum Herunterladen von Microsoft Transporter Suite [Microsoft Transporter Suite](http://go.microsoft.com/fwlink/?linkid=82688) im Microsoft Download Center.

Stellen Sie zudem beim Auswerten der Option für Ihre Organisation sicher, dass Sie die folgenden Fragen berücksichtigt haben:

  - Verfügen Sie über eine Strategie zum Verschieben von abhängigen Anwendungen zu Exchange 2010, bevor Exchange 2003 den Ablauf des Supports erreicht. Weitere Informationen finden Sie auf der Microsoft Support Lifecycle-Webseite ([https://go.microsoft.com/fwlink/?LinkID=55839](https://go.microsoft.com/fwlink/?linkid=55839)).

  - Ist für Ihre Strategie eine WebDAV- und Webdienstkoexistenz (Exchange 2007) erforderlich?

  - Haben Sie Drittanbieterprodukte berücksichtigt, die Exchange oder andere Microsoft-Technologien unterstützen, die Ihnen ermöglichen, Ihre Koexistenz- oder Migrationsanforderungen zu erfüllen?

  - Wie sieht Ihr Lebenszyklusansatz (weiterhin möglichst viele vorhandene 32-Bit-Server verwenden oder neue 64-Bit-Server erwerben) für Ihre Hardware aus?

  - Wie sieht Ihr Plan für die Migration (alle Server schnellstmöglich migrieren oder die Migration gemäß einer gestuften Strategie vornehmen) aus? Wie sehen analog dazu Ihre Zeitvorgaben für die Koexistenz von unterschiedlichen Exchange-Versionen aus?

Wenn Sie beschließen, dass Sie einen Exchange 2007-Server vor der Bereitstellung von Exchange 2010 bereitstellen müssen, ist die Bereitstellung eines einzelnen Exchange 2007s mit allen Serverrollen ausreichend, um die Bereitstellung für künftige Exchange 2007-Server in der Organisation zu ermöglichen. Befolgen Sie zum Bereitstellen des Exchange 2007-Servers in Ihrer Exchange 2003-Organisation die folgenden Schritte:

1.  Führen Sie Exchange 2007**Setup /PrepareSchema** aus.

2.  Führen Sie Exchange 2007**Setup /PrepareAD** aus.

3.  Führen Sie Exchange 2007**Setup /PrepareDomain** auf allen Domänen aus, die Empfänger, Exchange 2003-Server oder globale Kataloge enthalten, die durch einen Exchange-Server verwendet werden könnten.

4.  Installieren Sie einen Exchange 2007-Server mit allen vier Serverrollen (Hub-Transport, Clientzugriff, Postfach und Unified Messaging)

