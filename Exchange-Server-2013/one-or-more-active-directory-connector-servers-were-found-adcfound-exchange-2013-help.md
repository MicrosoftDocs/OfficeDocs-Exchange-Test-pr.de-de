---
title: 'Einen oder mehrere ADC-Server (Active Directory Connector) gefunden_ADCFound: Exchange 2013 Help'
TOCTitle: Einen oder mehrere ADC-Server (Active Directory Connector) gefunden_ADCFound
ms:assetid: a874f51f-09a2-4a76-9695-d61fb1ee6c1c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.adcfound(v=EXCHG.150)
ms:contentKeyID: 50476429
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Einen oder mehrere ADC-Server (Active Directory Connector) gefunden\_ADCFound

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2016-12-15_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 und Exchange Server 2010 kann nicht fortgesetzt werden, da ein oder mehrere Active Directory Connectors (ADC) in der aktuellen Microsoft Exchange-Umgebung gefunden wurden.

Ein ADC repliziert Objekte aus Exchange Server, Version 5.5, in den Verzeichnisdienst Active Directory in einer Microsoft Exchange-Umgebung im gemischten Modus und wird von Exchange 2007 oder Exchange 2010 nicht unterstützt.

Für das Microsoft Exchange 2007- oder Exchange 2010-Setup ist erforderlich, dass sämtliche ADC-Komponenten entfernt werden.

Um dieses Problem zu beheben, entfernen Sie alle ADC-Komponenten und führen das Exchange 2007- oder Exchange 2010-Setup erneut aus.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>So entfernen Sie Active Directory Connector-Komponenten</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Um den ADC-Dienst auf dem Server zu deaktivieren, auf dem er ausgeführt wird, klicken Sie mit der rechten Maustaste auf dem Desktop auf <strong>Arbeitsplatz</strong>, und klicken Sie dann auf <strong>Verwalten</strong>.</p></li>
<li><p>Erweitern Sie den Knoten <strong>Dienste und Anwendungen</strong>, und klicken Sie dann auf den Knoten <strong>Dienste</strong>.</p></li>
<li><p>Klicken Sie mit der rechten Maustaste im rechten Bereich auf <strong>Microsoft Active Directory Connector</strong>, und klicken Sie dann auf <strong>Eigenschaften</strong>.</p></li>
<li><p>Ändern Sie <strong>Starttyp</strong> in <strong>Deaktiviert</strong>. Beim nächsten Start des Computers wird der ADC-Dienst nicht gestartet.</p></li>
<li><p>Klicken Sie auf <strong>Übernehmen</strong> und dann auf <strong>OK</strong>.</p></li>
<li><p>Um den ADC-Dienst zu deinstallieren, verwenden Sie den Assistenten für die Installation von Active Directory auf der Microsoft Exchange 2000- oder Microsoft Exchange Server 2003-CD. Öffnen Sie den Ordner <strong>\ADC\I386</strong>, und doppelklicken Sie auf das Programm <strong>Setup.exe</strong>. Folgen Sie den Eingabeaufforderungen, um alle ADC-Dienstkomponenten zu entfernen.</p>

> [!IMPORTANT]
> Sie müssen Schritt&nbsp;6 abschließen und alle ADC-Komponenten über <STRONG>Alle entfernen</STRONG> entfernen, um dieses Problem zu beheben. Es reicht nicht aus, den ADC-Dienst zu deaktivieren.


</li>
</ol></td>
</tr>
</tbody>
</table>


Weitere Informationen zum ADC finden Sie in den folgenden Microsoft Knowledge Base-Artikeln:

  - 325300, "support WebCast: Einführung in den Active Directory Connector" ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=325300](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=325300)).

  - 325221, "support WebCast: Microsoft Advanced Active Directory Connector" ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=325221](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=325221)).

  - 312632, so wird "Wie installieren und Konfigurieren von Active Directory Connector in Exchange 2000 Server" ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=312632](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=312632)).

