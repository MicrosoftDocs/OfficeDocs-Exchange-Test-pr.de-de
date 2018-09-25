---
title: 'Websitepostfächer: Exchange 2013 Help'
TOCTitle: Websitepostfächer
ms:assetid: 2c4393f4-d274-4e6c-bd09-9577e68c5a33
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150499(v=EXCHG.150)
ms:contentKeyID: 50475394
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Websitepostfächer

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

E-Mails und Dokumente werden herkömmlicherweise in zwei voneinander getrennten Datenrepositorys gespeichert. Die meisten Organisationen arbeiten über beide Medien zusammen. Die Herausforderung liegt darin, dass auf E-Mails und Dokumente mit unterschiedlichen Clients zugegriffen wird. Dies reduziert üblicherweise sowohl die Benutzerfreundlichkeit als auch die Benutzerproduktivität.

Das *Websitepostfach* ist ein neues Konzept in Exchange 2013, mit dem dieses Problem gelöst werden soll. Websitepostfächer verbessern die Zusammenarbeit und Benutzerproduktivität, indem sie den Zugriff auf Microsoft SharePoint 2013-Dokumente und Exchange-E-Mails über die gleiche Clientschnittstelle ermöglichen. Ein Websitepostfach umfasst eine Mitgliedschaft in einer SharePoint 2013-Website (Besitzer und Mitglieder), gemeinsam genutzten Speicher in einem Exchange 2013-Postfach für E-Mails und einer SharePoint 2013-Website für Dokumente, sowie eine Verwaltungsschnittstelle für die Bereitstellungs- und Lebenszyklusanforderungen.

Websitepostfächer erfordern die Integration und Konfiguration von Exchange 2013 und SharePoint Server 2013. Weitere Informationen dazu, wie Sie Ihre Exchange 2013-Organisation für die Zusammenarbeit mit Ihrer SharePoint Server 2013-Organisation konfigurieren, finden Sie in den folgenden Themen:

  - [Konfigurieren von Websitepostfächern in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?linkid=258264).

  - [Integration in SharePoint und Lync](integration-with-sharepoint-and-lync-exchange-2013-help.md)

Weitere Informationen zu den Zusammenarbeitsfunktionen in Exchange Server 2013 finden Sie unter [Zusammenarbeit](collaboration-exchange-2013-help.md).

**Inhalt**

Wie funktionieren Websitepostfächer?

Bereitstellungsrichtlinien für Websitepostfächer

## Wie funktionieren Websitepostfächer?

Wenn ein Mitglied einer Projektgruppe E-Mails oder Dokumente im Websitepostfach speichert, kann jedes andere Mitglied der Projektgruppe auf diese Inhalte zugreifen. Websitepostfächer sind in Outlook 2013 sichtbar und ermöglichen Benutzern den einfachen Zugriff auf E-Mails und Dokumenten zu den Projekten, die sie bearbeiten. Außerdem kann auf diesen Inhalt direkt über die SharePoint-Website zugegriffen werden. In Websitepostfächern wird der Inhalt an der richtigen Stelle gespeichert. Exchange speichert die E-Mail, sodass Benutzer dieselbe Nachrichtenansicht für E-Mail-Unterhaltungen angezeigt wird, die sie tagtäglich für ihre eigenen Postfächer verwenden. SharePoint speichert die Dokumente und ermöglicht eine gemeinsame Dokumenterstellung sowie Versionsverwaltung. Exchange synchronisiert gerade so viele Metadaten von SharePoint, damit die Dokumentansicht in Outlook erstellt werden kann (beispielsweise Dokumenttitel, Datum der letzten Änderung, Autor der letzten Änderung und Größe).

![Diagramm zur Speicherung und Nutzung von Websitepostfächern](images/JJ150499.b98be571-d2e0-4ebd-9fe2-440a14e91e35(EXCHG.150).gif "Diagramm zur Speicherung und Nutzung von Websitepostfächern")

## Bereitstellungsrichtlinien für Websitepostfächer

Mithilfe des Cmdlets **SiteMailboxProvisioningPolicy** in der Exchange-Verwaltungsshell können Kontingente für Websitepostfächer festgelegt werden. Die Bereitstellungsrichtlinien für Websitepostfächer gelten für nur E-Mails, die an das Websitepostfach und von dem Websitepostfach gesendet werden, sowie für die Größe des Websitepostfachs auf dem Exchange-Server. Die Einstellungen für das Dokumentrepository werden in SharePoint konfiguriert. Wenngleich Sie mithilfe des Cmdlets **New-SiteMailboxProvisioningPolicy** mehrere Bereitstellungsrichtlinien für Websitepostfächer erstellen können, wird nur die standardmäßige Bereitstellungsrichtlinie auf alle Websitepostfächer angewendet. Sie können nicht mehrere Richtlinien in Ihrem Unternehmen anwenden. Mithilfe von Bereitstellungsrichtlinien können Sie die folgenden Kontingente festlegen:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Kontingent</th>
<th>Beschreibung</th>
<th>Standardeinstellung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IssueWarningQuota</p></td>
<td><p>Der Parameter <em>IssueWarningQuota</em> gibt die Größe des Websitepostfachs an, bei der eine Warnmeldung an das Websitepostfach gesendet wird</p></td>
<td><p>4,5 GB</p></td>
</tr>
<tr class="even">
<td><p>MaxReceiveSize</p></td>
<td><p>Der Parameter <em>MaxReceiveSize</em> gibt die maximale Größe von E-Mails an, die von dem Websitepostfach empfangen werden können.</p></td>
<td><p>36 MB</p></td>
</tr>
<tr class="odd">
<td><p>ProhibitSendReceiveQuota</p></td>
<td><p>Der Parameter <em>ProhibitSendReceiveQuota</em> gibt die Größe an, ab der das Websitepostfach nicht länger Nachrichten senden oder empfangen kann.</p></td>
<td><p>5 GB</p></td>
</tr>
</tbody>
</table>


Weitere Informationen dazu, wie Sie die Bereitstellungsrichtlinien für ein Websitepostfach konfigurieren, finden Sie unter [Verwalten von Bereitstellungsrichtlinien für Websitepostfächer](manage-site-mailbox-provisioning-policies-exchange-2013-help.md).

Wie funktionieren Websitepostfächer?

## Lebenszyklusrichtlinien und Aufbewahrung

Der Lebenszyklus eines Websitepostfachs wird über eine SharePoint-Website verwaltet. Über diese SharePoint-Website sollten Sie alle Aufgaben in Bezug auf Websitepostfächer verwalten, wie z. B. die Erstellung und Entfernung eines Websitepostfachs. Darüber hinaus können Sie in der SharePoint-Website eine Lebenszyklusrichtlinie erstellen, um den Lebenszyklus eines Websitepostfachs zu verwalten. Sie können z. B. in SharePoint eine Lebenszyklusrichtlinie erstellen, die alle Websitepostfächer automatisch nach 6 Monaten schließt. Wenn ein Benutzer ein solches Websitepostfach weiterhin nutzen möchten, kann er das Postfach über SharePoint erneut aktivieren. Es empfiehlt sich, die Lebenszyklusanwendung in der Farm zu verwenden. Durch manuelles Löschen aktiver Websitepostfächer aus Exchange entstehen verwaiste Websitepostfächer. .

Wenn eine Lebenszyklusanwendung in SharePoint ein Websitepostfach schließt, wird dieses Postfach so lange im geschlossenen Status beibehalten, wie in der Lebenszyklusrichtlinie angegeben. Während dieses Zeitraums kann das Postfach durch einen Endbenutzer oder einen Administrator über SharePoint erneut aktiviert werden. Nach Ablauf des Aufbewahrungszeitraums wird dem Namen des Exchange-Websitepostfachs, das in der Postfachdatenbank gespeichert ist, die Zeichenfolge **MDEL:**  vorangestellt: um anzugeben, dass es zum Löschen markiert wurde. Sie müssen diese Websitepostfächer manuell aus der Postfachdatenbank entfernen, um den Speicherplatz und den Aliasnamen freizugeben. Wenn Sie keine SharePoint-Lebenszyklusrichtlinie eingerichtet haben, können Sie nicht bestimmen, welche Websitepostfächer zum Löschen markiert sind. Sofern das Websitepostfach nicht durch einen Administrator entfernt wurde, lässt sich der Postfachinhalt weiterhin wiederherstellen.

Mit folgendem Befehl können Sie nach Websitepostfächern suchen, die zum Löschen markiert wurden, und diese entfernen.

```powershell
    Get-Mailbox MDEL:* | ?{$_.RecipientTypeDetails -eq "TeamMailbox"} | Remove-Mailbox -Confirm:$false
```

Websitepostfächer unterstützen keine Aufbewahrung auf Elementebene. Die Aufbewahrung für Websitepostfächer funktioniert auf Projektebene, wenn also das gesamte Websitepostfach gelöscht wird, werden auch die aufbewahrten Elemente gelöscht.

## Richtlinientreue

Wenn Sie die eDiscovery-Konsole in SharePoint verwenden, können Sie Websitepostfächer in die Compliance-eDiscovery einschließen und Schlüsselwortsuchläufe in Benutzer- oder Websitepostfächern durchführen. Darüber hinaus können Sie ein Websitepostfach der gesetzlichen Aufbewahrungspflicht unterwerfen. Weitere Informationen finden Sie unter [Compliance-eDiscovery](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery).


> [!NOTE]
> Um das Beweissicherungsverfahren für ein Websitepostfach in Office 365 zu aktivieren, muss diesem eine Exchange Online (Plan 2)-Lizenz zugewiesen sein. Wenn einem Websitepostfach eine Exchange Online (Plan 1)-Lizenz zugewiesen ist, müssen Sie diesem eine separate Exchange Online-Archivierungslizenz zuweisen, um für dieses die Aufbewahrungspflicht festzulegen.



Wie funktionieren Websitepostfächer?

## Sichern und Wiederherstellen

Für die Sicherung und Wiederherstellung der auf dem Postfachserver gespeicherten Exchange-Websitepostfächer werden die gleichen Sicherungs- und Wiederherstellungsmethoden verwendet wie für alle Exchange-Postfächer. Weitere Informationen finden Sie unter [Database Availability Groups (DAGs)](database-availability-groups-dags-exchange-2013-help.md).

SharePoint-Dokumente sollten Sie am gleichen Speicherort sichern und wiederherstellen. Wenn Sie Ihre SharePoint-Inhalte unter Verwendung der gleichen URLs wiederherstellen, funktioniert das Websitepostfach wie bisher, und es ist keine weitere Konfiguration erforderlich. Wenn Sie eine andere URL zur Wiederherstellung verwenden, müssen Sie das Cmdlet **Set-SiteMailbox** ausführen, um die Eigenschaft *SharePointURL* zu aktualisieren. Es empfiehlt sich, SharePoint nicht in einer neuen Gesamtstruktur wiederherzustellen.

