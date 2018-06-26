---
title: 'FAQ: Exchange Admin Center: Exchange 2013 Help'
TOCTitle: 'FAQ: Exchange Admin Center'
ms:assetid: 3de0042f-74a6-458f-947c-3cd6eeacd6ab
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ552409(v=EXCHG.150)
ms:contentKeyID: 50475440
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# FAQ: Exchange Admin Center

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

In diesem Thema wird eine Liste mit häufig gestellten Fragen zur neuen Exchange-Verwaltungskonsole in Microsoft Exchange Server 2013 bereitgestellt. Haben Sie weitere Fragen zur Exchange-Verwaltungskonsole, die hier nicht beantwortet wurden? Senden Sie uns eine E-Mail an [Ex2013HelpFeedback@microsoft.com](mailto:ex2013helpfeedback@microsoft.com).

## Wurde die Exchange-Verwaltungskonsole ausschließlich für Exchange Online entwickelt?

Die Exchange-Verwaltungskonsole kann für alle Bereitstellungsoptionen von Exchange 2013 eingesetzt werden. Dies schließt lokale Bereitstellungen, Cloudbereitstellungen mit Exchange Online und Hybridbereitstellungen ein.

## Wurde die vorherige Version der Exchange-Verwaltungskonsole ersetzt, da die Oberfläche primär für kleine und mittelständische Kunden entwickelt wurde?

Die neue Exchange-Verwaltungskonsole wurde entwickelt, um allen Kunden ein einheitliches, intuitives Verwaltungserlebnis zu bieten, und ist dazu konzipiert, Benutzern die Ausführung der gängigsten Verwaltungsaufgaben zu erleichtern.

Es wurde eine einzige Benutzerschnittstelle entwickelt, die eine Obermenge der Szenarien bereitstellt, die mit der vorherigen Exchange-Verwaltungskonsole und der Exchange-Systemsteuerung (ECP) abgedeckt wurden, und mit der die wichtigsten Herausforderungen und Szenarien für die Kunden adressiert werden können.

Zusätzlich wurde das Feedback von Kundenunternehmen jeder Größe berücksichtigt, indem den folgenden Aspekten Rechnung getragen wurde:

  - Das Verwalten und Herunterladen von Patches für den Betrieb eines Verwaltungstools führt zu einem administrativen Mehraufwand auf Kundenseite und erhöht so die Betriebskosten.

  - IT-Abteilungen werden immer mobiler, und Kunden erwarten, dass sie ihre Umgebungen von beliebigen Standorten und nicht lediglich von den Desktops und Servern aus verwalten können, auf denen die Verwaltungstools installiert sind.

  - Die Verwendung mehrerer Tools für verschiedene Bereitstellungsoptionen führt zu Verwirrung und erhöht die Schulungs- und Betriebskosten

## Werden PowerShell-Protokollierung und Cmdlets wieder in die neue Exchange-Verwaltungskonsole aufgenommen?

Wir haben ein erstes Kundenfeedback hierzu gesammelt und werten die Möglichkeit aus, diese Funktionen in einem zukünftigen Update einzubeziehen.

## Wird die ursprüngliche Exchange-Verwaltungskonsole in einem bevorstehenden Service Pack wieder eingeführt?

Nein. Es wird ausschließlich die neue Exchange-Verwaltungskonsole unterstützt.

## Kann die Exchange 2010-Verwaltungskonsole zum Verwalten von Exchange 2013-Objekten verwendet werden?

Nein. Sie können die Exchange 2010-Verwaltungskonsole nicht zum Verwalten von Exchange 2013-Objekten und -Servern einsetzen. Während des Kundenupgrades auf Exchange 2013 sollte die neue Exchange-Verwaltungskonsole für folgende Aufgaben verwendet werden:

1.  Verwalten von Exchange 2013-Postfächern, -Servern und zugehörigen Diensten.

2.  Anzeigen und Aktualisieren von Exchange 2010-Postfächern und -Eigenschaften.

3.  Anzeigen und Aktualisieren von Exchange 2007-Postfächern und -Eigenschaften.

Kunden wird empfohlen, Exchange 2010-Postfächer über die Exchange 2010-Verwaltungskonsole zu erstellen und zu verwalten.

Kunden wird empfohlen, Exchange 2007-Postfächer über die Exchange 2007-Verwaltungskonsole zu erstellen und zu verwalten.

Kunden können Verwaltungsaufgaben weiterhin mit der Exchange-Verwaltungsshell und mithilfe von Skripts ausführen.

## Warum ist das Suchfeld nicht immer sichtbar?

Einer der Gestaltungsgrundsätze für Exchange 2013 lautet, dass Elemente nicht störend wirken und nur dann angezeigt werden sollen, wenn sie benötigt werden. Diese Einfachheit kommt auf allen Benutzeroberflächen (auch in der Exchange-Verwaltungskonsole) zum Ausdruck. Das Suchfeld öffnet sich, sobald Sie auf das Symbol klicken. Der Benutzer erhält dadurch im Textfeld mehr Platz zur Eingabe der Abfrage. Außerdem werden während der Eingabe Vorschläge in Echtzeit angezeigt. Durch diese Verbesserung erscheint die Oberfläche weniger komplex, ohne dass das Verwaltungserlebnis beeinträchtigt wird. Die Gestaltungskonzepte werden weiterhin basierend auf dem Kundenfeedback verbessert.

## Kann die Exchange-Verwaltungskonsole auch auf Tablets eingesetzt werden?

Die Verwaltung über Tablets und mobile Geräte wird zu diesem Zeitpunkt nicht unterstützt.

## Warum wird die Exchange 2010-Systemsteuerung geöffnet, wenn ich versuche, auf die Exchange 2013-Verwaltungskonsole zuzugreifen?

Wenn Ihr Postfach sich auf einem Exchange 2010-Postfachserver befindet, wird automatisch die Exchange 2010-Systemsteuerung in Ihrem Browser geladen. Dies ist so beabsichtigt. Sie können auf die Exchange-Verwaltungskonsole zugreifen, indem Sie die Exchange-Version in der URL hinzufügen. Verwenden Sie beispielsweise die folgende URL, um auf die Exchange-Verwaltungskonsole zuzugreifen, deren virtuelles Verzeichnis auf dem Clientzugriffsserver "CAS01-NA" gehostet wird: `https://CAS01-NA/ecp?ExchClientVer=15`.

## Wie wird eingeschränkt, wo die Exchange-Verwaltungskonsole verwendet werden kann?

Um den Internetzugriff im Vergleich zum Intranetzugriff zu beschränken, ermöglicht Exchange eine Partitionierung auf der Ebene des virtuellen Verzeichnisses in IIS. Administratoren können die Ausführung von IT-Verwaltungsaufgaben über externe Internetclients – beispielsweise Clients, die keiner Domäne innerhalb der Unternehmensfirewall angehören – explizit zulassen oder explizit verweigern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf das EAC](turn-off-access-to-the-exchange-admin-center-exchange-2013-help.md).

## Welche Änderungen gelten für die Exchange 2013-Toolbox?

In Exchange 2007 und Exchange 2010 umfasste die Exchange-Verwaltungskonsole die Toolbox, die Zugriff auf verschiedene Werkzeuge zur Verwaltung der Exchange-Organisation bot. Die Exchange 2013-Toolbox wurde im Vergleich zu den vorherigen Versionen deutlich gestrafft. Der Detailvorlagen-Editor, die Remoteverbindungsuntersuchung und die Warteschlangenanzeige stehen in der Exchange 2013-Toolbox weiterhin zur Verfügung. Die übrigen Tools wurden entweder für einen anderen Zweck umfunktioniert oder in die neue Exchange-Verwaltungskonsole verschoben.

In der nachstehenden Tabelle werden die Änderungen an der Exchange 2013-Toolbox aufgeführt:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tool</th>
<th>Wo ist das Tool jetzt?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Best Practices Analyzer (ExBPA)</p></td>
<td><p>Der ExBPA wurde ausgemustert. Der ExBPA wurde durch Überprüfungen der Bereitschaft ersetzt, um sicherzustellen, dass die Active Directory-Gesamtstruktur und die Exchange-Server auf die Installation von Exchange 2013 vorbereitet sind. In jedem Thema zu den Überprüfungen der Bereitschaft werden die Maßnahmen beschrieben, die Sie zum Beheben von Problemen ergreifen können, die bei Ausführung der Überprüfungen der Bereitschaft ermittelt werden. Führen Sie die in einem Thema zur Überprüfung der Bereitschaft erläuterten Schritte nur aus, wenn diese Überprüfung während des Setups angezeigt wurde.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenfluss-Problembehandlung</p></td>
<td><p>Die Nachrichtenfluss-Problembehandlung wurde eingestellt. Sie können jetzt die Nachrichtenverfolgungsfunktion in der Exchange-Verwaltungskonsole nutzen. Wechseln Sie zu <strong>Nachrichtenfluss</strong> &gt; <strong>Zustellungsberichte</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Systemmonitor</p></td>
<td><p>Der Systemmonitor wurde aus der Toolbox herausgenommen. Sie finden den Systemmonitor weiterhin unter <strong>Verwaltung</strong> in Windows Server 2008 und Windows Server 2012.</p></td>
</tr>
<tr class="even">
<td><p>Leistungsproblembehandlung</p></td>
<td><p>Die Leistungsproblembehandlung wurde aus der Toolbox herausgenommen.</p></td>
</tr>
<tr class="odd">
<td><p>Routingprotokollanzeige</p></td>
<td><p>Die Routingprotokollanzeige wurde eingestellt.</p></td>
</tr>
<tr class="even">
<td><p>Öffentliche Ordner-Verwaltungskonsole</p></td>
<td><p>Öffentliche Ordner werden nun mithilfe der Exchange-Verwaltungskonsole verwaltet. Wechseln Sie in der Exchange-Verwaltungskonsole zu <strong>Öffentliche Ordner</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Benutzereditor für die rollenbasierte Zugriffssteuerung</p></td>
<td><p>RBAC wird jetzt über die Exchange-Verwaltungskonsole verwaltet. Wechseln Sie in der Exchange-Verwaltungskonsole zu <strong>Berechtigungen</strong>.</p></td>
</tr>
</tbody>
</table>

