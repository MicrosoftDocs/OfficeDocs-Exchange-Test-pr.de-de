---
title: 'In-Place Hold and Litigation Hold: Exchange 2013 Help'
TOCTitle: In-Place Hold and Litigation Hold
ms:assetid: 71031c06-852d-44d8-b558-dff444eaef8c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff637980(v=EXCHG.150)
ms:contentKeyID: 50475931
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# In-Place Hold and Litigation Hold

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-11-15_


> [!NOTE]
> Wir haben den Stichtag (1. Juli 2017) für das Erstellen neuer In-Situ-Speicher in Exchange Online (in Office 365 und eigenständigen Exchange Online-Plänen) verschoben. Im späteren Verlauf dieses Jahres oder Anfang des nächsten Jahres können Sie keine neuen In-Situ-Speicher mehr in Exchange Online erstellen. Als Alternative zur Verwendung von In-Situ-Speichern können Sie <A href="https://go.microsoft.com/fwlink/?linkid=780738">eDiscovery-Fälle</A> oder <A href="https://go.microsoft.com/fwlink/?linkid=827811">Aufbewahrungsrichtlinien</A> im Office 365-Sicherheit &amp; Compliance Center verwenden. Sobald die Erstellung neuer In-Situ-Speicher eingestellt ist, können vorhandene In-Situ-Speicher weiterhin geändert werden, und das Erstellen neuer In-Situ-Speicher in Exchange Server&nbsp;2013- und Exchange-Hybridbereitstellungen wird weiterhin unterstützt. Und Sie können weiterhin Postfächer im Beweissicherungsverfahren platzieren.



Wenn Rechtsstreitigkeiten zu erwarten sind, sind Organisationen dazu verpflichtet, die für den Fall relevanten elektronisch gespeicherten Informationen einschließlich E-Mail aufzubewahren. Diese Erwartung ist häufig vorhanden, bevor die Details des Falls bekannt werden, und die Menge der aufzubewahrenden Daten ist häufig groß. Organisationen müssen möglicherweise alle E-Mails zu einem bestimmten Thema oder alle E-Mails für bestimmte Personen aufbewahren. Abhängig von den eDiscovery-Verfahren der jeweiligen Organisation können folgende Maßnahmen zur Aufbewahrung von E-Mails angewendet werden:

  - Endbenutzer werden gebeten, E-Mails aufzubewahren und keine Nachrichten zu löschen. Allerdings können Benutzer E-Mails dennoch bewusst oder versehentlich löschen.

  - Automatische Löschmechanismen wie Messaging-Datensatzverwaltung (Messaging Records Management, MRM) können angehalten werden. Dies kann dazu führen, dass große Mengen an E-Mails das Benutzerpostfach füllen und so die Produktivität des Benutzers beeinträchtigen. Durch das Anhalten des automatischen Löschvorgangs kann außerdem nicht verhindert werden, dass die Benutzer E-Mails manuell löschen.

  - Einige Organisationen kopieren oder verschieben E-Mails in ein Archiv, um sicherzustellen, dass sie nicht gelöscht, verändert oder manipuliert werden. Dies führt zu einem Kostenanstieg aufgrund des manuellen Aufwands, der zum Kopieren oder Verschieben von Nachrichten in ein Archiv erforderlich ist, oder aufgrund der zum Sammeln und Speichern von E-Mails außerhalb von Exchange verwendeten Drittanbietersoftware.

Fehler bei der Aufbewahrung von E-Mails können für eine Organisation rechtliche und finanzielle Folgen haben, beispielsweise die Prüfung der Aufbewahrungs- und Offenlegungsverfahren für Datensätze in der Organisation, nachteilige Gerichtsurteile, Strafmaßnahmen oder Bußgelder.

Sie können den In-Situ-Speicher oder das Beweissicherungsverfahren verwenden, um folgende Ziele zu erreichen:

  - Platzieren von Benutzerpostfächern in Archiven und Beibehalten von Postfachelementen in unveränderbarer Form

  - Beibehalten von Postfachelementen, die von Benutzern oder automatischen Löschprozessen wie z. B. MRM gelöscht werden

  - Verwenden abfragebasierter Compliance-Archive zum Suchen nach und Aufbewahren von Elementen anhand bestimmter Kriterien

  - Beibehalten von Elementen auf unbestimmte Zeit oder über einen bestimmten Zeitraum

  - Platzieren von Benutzerpostfächern in verschiedenen Archiven für verschiedene Fälle oder Untersuchungen

  - Das Halten für den Benutzer transparent halten, ohne MRM anhalten zu müssen

  - Ermöglichen der In-Situ-eDiscovery-Suche nach Elementen, die der Aufbewahrungspflicht unterliegen

**Inhalt**

Compliance-Archiv-Szenarien

In-Situ-Speicher und Beweissicherungsverfahren

Platzieren eines Postfachs in einem Compliance-Archiv

Platzieren von öffentlichen Ordnern im Archiv

Archive und der Ordner "Wiederherstellbare Elemente"

Archive und Postfachkontingente

Aufbewahrung und E-Mail-Weiterleitung

Aufbewahren von archivierten Lync-Inhalten

Löschen eines aufzubewahrenden Postfachs

Migrieren von aufzubewahrenden Postfächern aus Exchange 2013 zu Office 365

## Compliance-Archiv-Szenarien

In Exchange Server 2010 wird die gesetzliche Aufbewahrungspflicht umgesetzt, indem Postfachdaten für einen Benutzer dauerhaft oder bis zur Beendigung eines Verfahrens archiviert werden. In Exchange 2013 wird mit Compliance-Archiven ein neues Modell eingeführt, in dem Sie folgende Parameter angeben können:

  - **Aufzubewahrende Elemente**   Sie können angeben, welche Elemente aufbewahrt werden sollen, indem Sie Abfrageparameter wie z. B. Schlüsselwörter, Absender und Empfänger, Start- und Enddaten sowie den Typ der Elemente angeben, wie z. B. E-Mails oder Kalenderelemente.

  - **Aufbewahrungszeitraum**   Sie können angeben, wie lange Elemente aufbewahrt werden sollen.

Mit diesem neuen Modell ermöglichen Compliance-Archive es Ihnen, detaillierte Aufbewahrungsrichtlinien zu erstellen, um Postfachelemente in den folgenden Szenarien beizubehalten:

  - **Dauerhafte Aufbewahrung**   Das Szenario der dauerhaften Aufbewahrung entspricht dem Beweissicherungsverfahren. Es ist für die Aufbewahrung von Postfachelementen bestimmt, damit Sie Anforderungen der eDiscovery erfüllen können. Während der Dauer eines Beweissicherungsverfahrens oder einer Untersuchung werden Elemente nie gelöscht. Die Dauer ist im Vorfeld nicht bekannt, daher wird kein Enddatum konfiguriert. Um alle E-Mail-Elemente dauerhaft aufzubewahren, dürfen Sie beim Erstellen eines In-Situ-Speichers keine Abfrageparameter oder Zeiträume angeben.

  - **Abfragebasiertes Archiv**   Wenn Ihre Organisation Elemente auf Basis von angegebenen Abfrageparametern aufbewahrt, können Sie ein abfragebasiertes Compliance-Archiv verwenden. Sie können Abfrageparameter wie z. B. Schlüsselwörter, Start- und Enddaten, Absender- und Empfängeradressen sowie Nachrichtentypen angeben. Nach dem Erstellen eines abfragebasierten Compliance-Archivs werden alle vorhandenen und zukünftig erstellten Postfachelemente, die der Abfrage entsprechen, beibehalten (einschließlich der Nachrichten, die nach einem in der Abfrage angegebenen Datum empfangen werden).
    

    > [!IMPORTANT]
    > Elemente, die als nicht durchsuchbar markiert wurden, im Allgemeinen, wenn ein Anhang nicht indiziert werden konnte, werden ebenso beibehalten, da nicht entschieden werden kann, ob sie mit Abfrageparametern übereinstimmen. Weitere Informationen über nicht durchsuchbare Elemente finden Sie unter <A href="unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md">Nicht durchsuchbare Elemente in Exchange eDiscovery</A>.



  - **Zeitbasierte Aufbewahrung**   Der In-Situ-Speicher und das Beweissicherungsverfahren ermöglichen Ihnen, eine Dauer anzugeben, in der die Elemente aufbewahrt werden sollen. Der Zeitraum beginnt mit dem Datum, an dem das Postfachelement empfangen oder erstellt wurde.
    
    Wenn es in Ihrer Organisation erforderlich ist, alle Postfachelemente über einen bestimmten Zeitraum, z. B. 7 Jahre, aufzubewahren, können Sie eine zeitbasierte Aufbewahrung erstellen. In Exchange 2013 können Sie einen Zeitraum angeben, den Elemente im Archiv aufbewahrt werden. Das Alter von archivierten Elemente basiert auf dem Empfangsdatum. Stellen Sie sich z. B. ein Postfach vor, das in einem zeitbasierten Compliance-Archiv mit einer Aufbewahrungszeit von 365 Tagen platziert wurde. Wird ein Element dieses Postfachs 300 Tage nach Empfangsdatum gelöscht, bleibt es für weitere 65 Tage im Archiv, bevor es endgültig gelöscht wird. Sie können ein zeitbasiertes Compliance-Archiv zusammen mit einer Aufbewahrungsrichtlinie verwenden, um sicherzustellen, dass Elemente während des angegebenen Zeitraums beibehalten und anschließend endgültig entfernt werden.

Sie können In-Situ-Speicher dazu verwenden, Benutzerpostfächer in mehreren Speichern zu platzieren. Wenn ein Benutzer in mehreren In-Situ-Speichern platziert wird, werden die Suchabfragen von einem abfragebasierten Archiv kombiniert (mit **OR**-Operatoren). In diesem Fall beträgt die maximale Anzahl von Stichwörtern in allen abfragebasierten Archiven für ein Postfach 500. Bei mehr als 500 Stichwörtern werden sämtliche Inhalte des Postfachs archiviert (nicht bloß die Inhalte, die mit den Suchkriterien übereinstimmen). Alle Inhalte werden archiviert, bis die Gesamtzahl von Stichwörtern auf 500 oder weniger verringert wird.

Zurück zum Seitenanfang

## In-Situ-Speicher und Beweissicherungsverfahren

Das Beweissicherungsverfahren, die in Exchange 2010 eingeführte Funktion zur Aufbewahrung von Daten für die eDiscovery, ist in Exchange 2013 weiterhin verfügbar. Für das Beweissicherungsverfahren wird die **LitigationHoldEnabled**-Eigenschaft eines Postfachs verwendet. Während ein In-Situ-Speicher detaillierte Einstellungen für die Aufbewahrung bereitstellt, die auf Abfrageparametern und der Möglichkeit zur Einrichtung mehrerer Archive basieren, können Sie mit dem Beweissicherungsverfahren nur alle Elemente dauerhaft oder bis zur Beendigung des Beweissicherungsverfahrens beibehalten. Sie können auch eine Dauer für die Aufbewahrung von Elementen angeben, wenn für ein Postfach das Beweissicherungsverfahren aktiviert wurde. Der Zeitraum beginnt mit dem Datum, an dem das Postfachelement empfangen oder erstellt wurde. Wenn keine Dauer festgelegt ist, werden die Elemente entweder unbegrenzt aufbewahrt oder bis die Aufbewahrung entfernt wird.

Wenn ein Postfach in mindestens einen In-Situ-Speicher platziert wird und für das Postfach gleichzeitig das Beweissicherungsverfahren (ohne Zeitdauer) aktiviert wird, werden alle Elemente unbegrenzt oder solange aufbewahrt, bis die Aufbewahrung aufgehoben wird. Wenn Sie ein Benutzerpostfach aus einem Beweissicherungsverfahren entfernen, dieses jedoch weiterhin in mindestens einem In-Situ-Speicher platziert ist, werden Elemente, die den Kriterien für die In-Situ-Speicher entsprechen, während des in den Archiveigenschaften angegebenen Zeitraums beibehalten. Wenn Sie ein Postfach, das in Exchange 2010 für ein Beweissicherungsverfahren aktiviert ist, auf einen Exchange 2013-Postfachserver verschieben, gelten die Einstellungen für das Beweissicherungsverfahren weiterhin. So ist sichergestellt, dass die entsprechenden Richtlinien während und nach der Verschiebung eingehalten werden.


> [!NOTE]
> Wenn Sie für ein Postfach den In-Situ-Speicher oder das Beweissicherungsverfahren aktivieren, wird diese Einstellung auf das primäre und das Archivpostfach angewendet. Wenn Sie ein lokales primäres Postfach in einer Exchange-Hybridbereitstellung aussetzen, wird auch das cloudbasierte Archivpostfach (sofern aktiviert) ausgesetzt.



Weitere Informationen finden Sie unter:

  - [Aktivieren des Beweissicherungsverfahrens für ein Postfach](place-a-mailbox-on-litigation-hold-exchange-2013-help.md)

  - [Platzieren aller Postfächer im Archiv](place-all-mailboxes-on-hold-exchange-2013-help.md)

## Platzieren eines Postfachs in einem Compliance-Archiv

Autorisierte Benutzer, die der Rollengruppe für die rollenbasierte Remotezugriffssteuerung (Remote Role-Based Access Control, RBAC) [Erkennungsverwaltung](discovery-management-exchange-2013-help.md) hinzugefügt wurden oder denen die Verwaltungsrollen für gesetzliche Aufbewahrungspflicht und Postfachsuche zugewiesen wurden, können Benutzerpostfächer in Compliance-Archiven platzieren. Sie können die Aufgabe an Datensatz-Manager, an für die Einhaltung von Vorschriften zuständige Mitarbeiter oder an Anwälte in der Rechtsabteilung Ihrer Organisation delegieren und dabei die niedrigsten Berechtigungen zuweisen. Weitere Informationen zum Zuweisen der Discoveryverwaltung-Rollengruppe finden Sie unter [Zuweisen von eDiscovery-Berechtigungen in Exchange](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/assign-ediscovery-permissions).


> [!IMPORTANT]
> In Exchange 2010 bietet die Rolle für gesetzliche Aufbewahrungspflicht ausreichende Berechtigungen für Benutzer, um Postfächer für Beweissicherungsverfahren zu aktivieren. In Exchange 2013 können Sie die gleiche Berechtigung verwenden, um Postfächer in dauerhaften oder zeitbasierten Compliance-Archive zu platzieren. Dem Benutzer muss jedoch die Rolle "Postfachsuche" zugewiesen sein, damit er ein abfragebasiertes Compliance-Archiv erstellen kann. Der Rollengruppe Discoveryverwaltung sind beide Rollen zugewiesen.



In Exchange 2013 ist die Compliance-Archivierung in die Compliance-eDiscovery-Suche integriert. Sie können den Assistenten für **Compliance-eDiscovery & -Archiv** in der Exchange-Verwaltungskonsole oder das Cmdlet **New-MailboxSearch** bzw. verwandte Cmdlets in der Exchange-Verwaltungsshell verwenden, um ein Postfach in einem Compliance-Archiv zu platzieren. Informationen zum Platzieren eines Postfachs in einem Compliance-Archiv finden Sie unter [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md).


> [!NOTE]
> Wenn Sie die Exchange Online-Archivierung verwenden, um ein cloudbasiertes Archiv für Ihre lokalen Postfächer bereitzustellen, müssen Sie den In-Situ-Speicher über Ihre lokale Exchange 2013-Organisation verwalten. Aufbewahrungseinstellungen werden über DirSynch automatisch an das cloudbasierte Archiv weitergegeben. Wie bereits erläutert, wird beim Anwenden der Aufbewahrungspflicht auf ein lokales Postfach diese auch auf das entsprechende cloudbasierte Archiv angewendet.



In vielen Organisationen ist es erforderlich, dass Benutzer informiert werden, wenn ihre Elemente in Archiven platziert werden. Darüber hinaus müssen die für das Postfach geltenden Aufbewahrungsrichtlinien nicht angehalten werden, wenn ein Postfach in einem Archiv platziert wurde. Da Nachrichten wie erwartet weiter gelöscht werden, merken die Benutzer ggf. nicht, dass ihr Postfach in einem Archiv platziert wurde. Wenn es in Ihrer Organisation erforderlich ist, dass Benutzer informiert werden, wenn ihr Postfach in einem Archiv platziert wurde, können Sie der **Retention Comment**-Eigenschaft des Benutzers eine Benachrichtigung hinzufügen und über die Eigenschaft **RetentionUrl** einen Link zu einer Webseite mit weiteren Informationen bereitstellen. Outlook 2010 und höhere Versionen zeigen die Benachrichtigung und die URL im Backstagebereich an. Zum Hinzufügen und Verwalten dieser Eigenschaften für ein Postfach müssen Sie die Shell verwenden.

Zurück zum Seitenanfang

## Platzieren von öffentlichen Ordnern im Archiv

In Exchange Online können Sie öffentliche Ordner mithilfe eines In-Situ-Speichers im Archiv platzieren. Eine Verwendung des Beweissicherungsverfahren für öffentliche Ordner wird nicht unterstützt. Wenn Sie einen In-Situ-Speicher erstellen, besteht die einzige Option darin, alle öffentlichen Ordner in Ihrer Organisation im Archiv zu platzieren. Das Ergebnis ist, dass in allen Postfächern für Öffentliche Ordner ein In-Situ-Speicher platziert wird.

Wenn Sie außerdem öffentliche Ordner im In-Situ-Speicher platzieren, werden E-Mail-Nachrichten im Zusammenhang mit dem Hierarchiesynchronisierungsprozess für öffentliche Ordner ebenfalls gespeichert. Auf diese Weise können Tausende von E-Mail-Elementen im Zusammenhang mit der Hierarchiesynchronisierung gespeichert werden. Diese Nachrichten können das Speicherkontingent für den Ordner „Wiederherstellbare Elemente“ für Postfächer für Öffentlicher Ordner auffüllen. Um dies zu verhindern, können Sie einen abfragebaiserten In-Situ-Speicher erstellen und das folgende `property:value`-Paar zur Suchabfrage hinzufügen:

    NOT(subject:HierarchySync*)

Das Ergebnis ist, dass alle Nachrichten (im Zusammenhang mit der Synchronisierung der Hierarchie der öffentlichen Ordner), die den Ausdruck“HierarchySync“ in der Betreffzeile aufweisen, nicht im Archiv platziert werden.

## Archive und der Ordner "Wiederherstellbare Elemente"

Der In-Situ-Speicher und das Beweissicherungsverfahren verwenden den Ordner "Wiederherstellbare Elemente", um Elemente beizubehalten. Dieser Ordner ersetzt die Funktion, die in früheren Versionen von Exchange als *Dumpster* bezeichnet wurde. Der Ordner "Wiederherstellbare Elemente" wird in der Standardansicht von Outlook, Outlook Web App und anderen E-Mail-Clients angezeigt. Weitere Informationen zum Ordner **Wiederherstellbare Elemente** finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

Standardmäßig wird eine Nachricht, die von einem Benutzer aus einem anderen Ordner als dem Ordner **Gelöschte Elemente** gelöscht wird, in den Ordner **Gelöschte Elemente** verschoben. Dies wird als *Verschiebung* bezeichnet. Wenn ein Benutzer ein Element *vorläufig löscht* (durch Drücken der UMSCHALT- und LÖSCHTASTE) oder ein Element aus dem Ordner **Gelöschte Elemente** löscht, wird die Nachricht in den Ordner **Wiederherstellbare Elemente** verschoben und dadurch aus der Ansicht des Benutzers entfernt.

Elemente im Ordner **Wiederherstellbare Elemente** werden über den Zeitraum aufbewahrt, der für die Postfachdatenbank des Benutzers als Aufbewahrungszeitraum für gelöschte Elemente konfiguriert wurde. Standardmäßig ist der Aufbewahrungszeitraum für gelöschte Elemente für Postfachdatenbanken auf 14 Tage festgelegt. Sie können auch ein Speicherkontingent für den Ordner **Wiederherstellbare Elemente** konfigurieren. Dies schützt die Organisation vor einem möglichen DoS-Angriff (Denial of Service) aufgrund einer zunehmenden Datenmenge im Ordner **Wiederherstellbare Elemente** und dadurch auch in der Postfachdatenbank. Wenn ein Postfach nicht in einem In-Situ-Speicher platziert oder für ein Beweissicherungsverfahren aktiviert ist, werden Elemente auf FIFO-Basis (First in, First out) endgültig aus dem Ordner "Wiederherstellbare Elemente" gelöscht, wenn der dazugehörige Kontingentgrenzwert überschritten wird oder sich das Element länger in dem Ordner befunden hat, als vom Aufbewahrungszeitraum des gelöschten Elements vorgesehen.

Der Ordner "Wiederherstellbare Elemente" enthält folgende Unterordner zum Speichern gelöschter Elemente an verschiedenen Standorten und zum Erleichtern von In-Situ-Speichern und Beweissicherungsverfahren:

  - **Deletions**   Elemente, die aus dem Ordner "Gelöschte Elemente" entfernt oder aus anderen Ordnern vorläufig gelöscht wurden, werden in den Unterordner "Deletions" verschoben und dem Benutzer angezeigt, wenn er in Outlook und Outlook Web App das Feature "Gelöschte Elemente wiederherstellen" verwendet. Standardmäßig verbleiben Elemente in diesem Ordner, bis der für die Postfachdatenbank oder das Postfach konfigurierte Aufbewahrungszeitraum für gelöschte Elemente abläuft.

  - **Purges**   Wenn ein Benutzer ein Element aus dem Ordner **Wiederherstellbare Elemente** löscht (durch Verwendung des Tools zur Wiederherstellung gelöschter Elemente in Outlook und Outlook Web App), wird das Element in den Ordner **Purges** verschoben. Elemente, die den für die Postfachdatenbank oder das Postfach konfigurierten Aufbewahrungszeitraum für gelöschte Elemente überschreiten, werden ebenfalls in den Ordner **Purges** verschoben. Elemente in diesem Ordner werden Benutzern, die das Tool zur Wiederherstellung gelöschter Elemente verwenden, nicht angezeigt. Wenn der Postfach-Assistent das Postfach verarbeitet, werden Elemente im Ordner **Purges** endgültig aus der Postfachdatenbank gelöscht. Wenn ein Postfach für ein Beweissicherungsverfahren aktiviert ist, löscht der Postfach-Assistent die Elemente nicht aus diesem Ordner.

  - **DiscoveryHold**   Wenn ein Benutzerpostfach in einem Compliance-Archiv platziert wurde, werden gelöschte Elemente in diesen Ordner verschoben. Beim Verarbeiten des Postfachs wertet der Postfach-Assistent Nachrichten in diesem Ordner aus. Elemente, die Abfrageparametern eines Compliance-Archivs entsprechen, werden während des in der Abfrage angegebenen Aufbewahrungszeitraums beibehalten. Wenn kein Aufbewahrungszeitraum angegeben wurde, werden Elemente dauerhaft oder so lange aufbewahrt, bis das Benutzerpostfach aus dem Archiv entfernt wird.

  - **Versions**   Wenn ein Benutzerpostfach in einem In-Situ-Speicher platziert oder für ein Beweissicherungsverfahren aktiviert wurde, müssen die Postfachelemente vor Manipulation oder Veränderung durch den Benutzer oder einen Prozess geschützt werden. Dies erfolgt über eine *Kopie bei Schreibvorgang*. Wenn ein Benutzer oder ein Prozess bestimmte Eigenschaften eines Postfachelements ändert, wird eine Kopie des ursprünglichen Elements im Ordner **Versions** gespeichert, bevor die Änderung durchgeführt wird. Der Vorgang wird für nachfolgende Änderungen wiederholt. Elemente im Ordner **Versions** werden indiziert und bei einer Compliance-eDiscovery-Suche zurückgegeben. Nachdem die Archivierung oder das Beweissicherungsverfahren beendet wurde, werden die Kopien im Ordner **Versions** durch den Assistenten für verwaltete Ordner entfernt.

### Eigenschaften, die eine Kopie bei Schreibvorgang auslösen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elementtyp</th>
<th>Eigenschaften, die eine Kopie bei Schreibvorgang auslösen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nachrichten (IPM.Note*)</p>
<p>Beiträge (IPM.Post*)</p></td>
<td><ul>
<li><p>Betreff</p></li>
<li><p>Text</p></li>
<li><p>Anlagen</p></li>
<li><p>Absender/Empfänger</p></li>
<li><p>Sende-/Empfangsdatum</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Andere Elemente als Nachrichten und Beiträge</p></td>
<td><p>Jede Änderung an einer sichtbaren Eigenschaft mit folgenden Ausnahmen:</p>
<ul>
<li><p>Speicherort des Elements (wenn ein Element zwischen Ordnern verschoben wird)</p></li>
<li><p>Statusänderung des Elements (gelesen oder ungelesen)</p></li>
<li><p>Änderungen an dem einem Element zugewiesenen Aufbewahrungstag</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Elemente im Standardordner <strong>Entwürfe</strong></p></td>
<td><p>Keine (Elemente im Ordner &quot;Entwürfe&quot; sind von der Kopie bei Schreibvorgang ausgenommen)</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> Die Kopie-bei-Schreibvorgang-Funktion ist für Kalenderelemente im Postfach des Organisators deaktiviert, wenn Besprechungsantworten von Teilnehmern empfangen werden und die Nachverfolgungsinformationen für die Besprechung aktualisiert werden. Für Kalenderelemente und Elemente mit Erinnerungseinstellungen ist die Kopie-bei-Schreibvorgang-Funktion für die Eigenschaften "ReminderTime" und "ReminderSignalTime" deaktiviert. Änderungen an diesen Eigenschaften werden nicht von der Kopie-bei-Schreibvorgang-Funktion erfasst. Änderungen an RSS-Feeds werden nicht von der Kopie-bei-Schreibvorgang-Funktion erfasst.



Auch wenn die Ordner "DiscoveryHold", "Purges" und "Versions" für die Benutzer nicht zu sehen sind, werden alle Elemente im Ordner "Wiederherstellbare Elemente" von der Exchange-Suche indiziert und können über die Compliance-eDiscovery gefunden werden. Nachdem der In-Situ-Speicher oder das Beweissicherungsverfahren für das Postfach eines Benutzers beendet wurde, werden Elemente in den Ordnern "Purges" und "Versions" durch den Assistenten für verwaltete Ordner gelöscht.

Zurück zum Seitenanfang

## Archive und Postfachkontingente

Elemente im Ordner **Wiederherstellbare Elemente** werden nicht in das Postfachkontingent des Benutzers eingerechnet. In Exchange besitzt der Ordner "Wiederherstellbare Elemente" ein eigenes Kontingent. Für Exchange werden die Standardwerte für die Postfacheigenschaften *RecoverableItemsWarningQuota* und *RecoverableItemsQuota* auf 20 GB bzw. 30 GB festgelegt. Zum Ändern dieser Werte für eine Postfachdatenbank für Exchange Server 2013 verwenden Sie das Cmdlet [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)). Zum Ändern dieser Werte für einzelne Postfächer verwenden Sie das Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

Überschreitet der Ordner Wiederherstellbare Elemente eines Benutzers das Kontingent für wiederherstellbare Elemente, ab dem eine Warnmeldung ausgegeben wird (festgelegt über den Parameter RecoverableItemsWarningQuota), wird im Anwendungsereignisprotokoll des Postfachservers ein Ereignis protokolliert. Überschreitet der Ordner das Kontingent für wiederherstellbare Elemente (wie im Parameter RecoverableItemsQuota festgelegt), können Benutzer den Ordner Gelöschte Elemente nicht mehr leeren und Postfachelemente nicht länger dauerhaft löschen. Mithilfe der Kopie-bei-Schreibvorgang-Funktion können keine Kopien geänderter Elemente erstellt werden. Deshalb müssen Sie die Kontingente für wiederherstellbare Elemente für Postfachbenutzer überwachen, die in einem Compliance-Archiv platziert wurden.

In Exchange Online wird das Kontingent für den Ordner „Wiederherstellbare Elemente“ (im primären Benutzerpostfach) automatisch auf 100 GB erhöht, wenn Sie für ein Postfach das Beweissicherungsverfahren aktivieren oder es im In-Situ-Speicher platzieren. Wenn das Speicherkontingent für den Ordner „Wiederherstellbare Elemente“ im primären Postfach eines aufzubewahrenden Postfachs seinen Grenzwert bald erreicht, können Sie Folgendes ausführen:

  - **Aktivieren des Archivpostfachs und Aktivieren der sich automatisch erweiternden Archivierung** Sie können eine unbegrenzte Speicherkapazität für den Ordner „Wiederherstellbare Elemente“ aktivieren, indem Sie einfach das Archivpostfach aktivieren und dann das Feature für die sich automatisch erweiternde Archivierung in ExchangeOnline aktivieren. Dies führt zu 100 GB für den Ordner „Wiederherstellbare Elemente“ im primären Postfach und zu einer unbegrenzten Speicherkapazität für den Ordner „Wiederherstellbare Elemente“ im Archiv des Benutzers. Weitere Informationen finden Sie unter: [Aktivieren von Archivpostfächern im Office 365 Security & Compliance Center](https://go.microsoft.com/fwlink/p/?linkid=863320) and [Aktivieren Sie die unbegrenzte Archivierung in Office 365 - Administratorhilfe](https://go.microsoft.com/fwlink/p/?linkid=844569).
    
    **Hinweise:** 
    
      - Nachdem Sie das Archiv für ein Postfach aktiviert haben, das bald sein Speicherkontingent für den Ordner „Wiederherstellbare Elemente“ erreicht, können Sie den Assistenten für verwaltete Ordner ausführen, um den Assistenten manuell dazu zu veranlassen, das Postfach zu verarbeiten, damit abgelaufene Elemente in den Ordner „Wiederherstellbare Elemente“ im Archivpostfach verschoben werden. Anweisungen finden Sie unter Schritt 4 [Erhöhen des Speicherkontingents des Ordners "Wiederherstellbare Elemente" für im In-Situ-Speicher abgelegte Postfächer](https://go.microsoft.com/fwlink/p/?linkid=786479).
    
      - Beachten Sie, dass weitere Elemente im Postfach des Benutzers in das neue Archivpostfach verschoben werden können. Sie sollten in Betracht ziehen, dem Benutzer mitzuteilen, das dies passieren kann, nachdem Sie das Archivpostfach aktiviert haben.

  - **Erstellen einer benutzerdefinierten Aufbewahrungsrichtlinie für aufzubewahrende Postfächer** Zusätzlich zu der Aktivierung des Archivpostfachs und der sich automatisch erweiternden Archivierung für Postfächer im Beweissicherungsverfahren oder für Postfächer im In-Situ-Speicher können Sie auch eine benutzerdefinierte Aufbewahrungsrichtlinie für aufzubewahrende Postfächer erstellen. Auf diese Weise können Sie eine Aufbewahrungsrichtlinie auf aufzubewahrende Postfächer anwenden, die sich von der Standard-MRM-Richtlinie unterscheidet, die auf nicht aufzubewahrende Postfächer angewendet wird. Auf diese Weise können Sie Aufbewahrungstags anwenden, die speziell für aufzubewahrende Postfächer entwickelt wurden. Dies umfasst das Erstellen eines neuen Aufbewahrungstags für den Ordner „Wiederherstellbare Elemente“.

Weitere Informationen finden Sie unter [Erhöhen des Kontingents für Ordner „Wiederherstellbare Elemente“ für aufzubewahrende Postfächer](https://go.microsoft.com/fwlink/p/?linkid=786479).

## Aufbewahrung und E-Mail-Weiterleitung

Benutzer können Outlook und Outlook Web App zum Einrichten der E-Mail-Weiterleitung für ihr Postfach verwenden. Bei der E-Mail-Weiterleitung können Benutzer ein Postfach so konfigurieren, sodass an dieses Postfach gesendete E-Mail-Nachrichten an das Postfach eines anderen Benutzers innerhalb oder außerhalb ihrer Organisation weitergeleitet werden. Die E-Mail-Weiterleitung kann so konfiguriert werden, sodass alle Nachrichten, die an das ursprüngliche Postfach gesendet werden, nicht in das Postfach kopiert werden und nur an die Weiterleitungsadresse gesendet werden.

Was passiert beim Aktivieren der Aufbewahrungspflicht für das Postfach, wenn E-Mail-Weiterleitung für ein Postfach eingerichtet ist und Nachrichten nicht in das ursprüngliche Postfach kopiert werden? Das Verhalten unterscheidet sich je nachdem, ob sich das Postfach in einer Exchange 2013- oder Exchange Online-Organisation befindet.

  - **Exchange Online**   Die Aufbewahrungseinstellungen für das Postfach werden beim Übermittlungsprozess geprüft. Wenn die Nachricht den Aufbewahrungskriterien für das Postfach entspricht, wird eine Kopie der Nachricht im Ordner „Wiederherstellbare Elemente“ gespeichert. Das bedeutet, dass Sie In-Situ-eDiscovery verwenden können, um das ursprüngliche Postfach nach Nachrichten zu durchsuchen, die an ein anderes Postfach weitergeleitet wurden.

  - **Exchange 2013**   Wenn Nachrichten an ein anderes Postfach weitergeleitet und nicht in das ursprüngliche Postfach kopiert werden, werden sie nicht in den Ordner „Wiederherstellbare Elemente“ kopiert, und somit nicht in diesem erfasst. Dass bedeutet, dass weitergeleitete Nachrichten nicht in einer In-Situ-eDiscovery-Suche zurückgegeben werden. Zur Behebung dieses Problems kann in Exchange 2013-Organisationen ggf. die Option zum Konfigurieren der E-Mail-Weiterleitung für Benutzer entfernt werden.

Zurück zum Seitenanfang

## Aufbewahren von archivierten Lync-Inhalten

Exchange 2013, Microsoft Lync 2013 und Microsoft SharePoint 2013 stellen integrierte Aufbewahrungs- und eDiscovery-Funktionen bereit, mit denen Sie Elemente über die verschiedenen Datenspeicher hinweg aufbewahren und danach suchen können. Exchange 2013 ermöglicht die Archivierung von Lync Server 2013-Inhalten in Exchange, sodass keine separate SQL Server-Datenbank zur Speicherung von Lync-Inhalten mehr erforderlich ist. Die integrierte Aufbewahrungs- und eDiscovery-Funktion in SharePoint 2013 ermöglicht das Aufbewahren und Suchen von Daten in allen Speichern über eine einzige Konsole.

Wenn Sie ein Exchange 2013-Postfach in einem In-Situ-Speicher platzieren oder für ein Beweissicherungsverfahren aktivieren, werden Microsoft Lync 2013-Inhalte (wie z. B. Chatunterhaltungen und Dateien, die bei einer Onlinebesprechung freigegeben wurden) im Postfach archiviert. Wenn Sie das Postfach über das eDiscovery Center in Microsoft SharePoint 2013 oder über die Compliance-eDiscovery in Exchange 2013 durchsuchen, werden in den Ergebnissen auch archivierte Lync-Inhalte zurückgegeben, die den Suchkriterien entsprechen. Sie können die Suche auch auf im Postfach archivierte Lync-Inhalte beschränken.

Zum Aktivieren der Archivierung von Lync-Inhalten in einem Exchange 2013-Postfach müssen Sie die Lync 2013-Integration in Exchange 2013 konfigurieren. Weitere Informationen finden Sie in den folgenden Themen:

  - [Planen der Archivierung](https://technet.microsoft.com/de-de/library/jj205069\(v=ocs.15\))

  - [Bereitstellen der Archivierung](https://technet.microsoft.com/de-de/library/jj205147\(v=ocs.15\))

Zurück zum Seitenanfang

## Löschen eines aufzubewahrenden Postfachs

Wenn Sie ein Postfach löschen, das im In-Situ-Speicher platziert wurde oder auf das das Beweissicherungsverfahren angewendet wurde, variiert das Ergebnis abhängig davon, ob sich das Postfach in einer Exchange 2013- oder Exchange Online-Organisation befindet.

  - **Exchange 2013**   Wenn ein Administrator ein Benutzerkonto mit einem Postfach löscht, erkennt der Exchange-Informationsspeicher nach einiger Zeit, dass das Postfach nicht mehr mit einem Benutzerkonto verbunden ist, und markiert dieses Postfach zur Löschung, auch wenn es ein aufzubewahrendes Postfach ist. Wenn Sie das Postfach beibehalten möchten, gehen Sie wie folgt vor:
    
    1.  Deaktivieren Sie das Benutzerkonto, anstatt es zu löschen.
    
    2.  Ändern Sie die Eigenschaften des Postfachs, um seine Verwendung und den Zugriff darauf einzuschränken. Setzen Sie z. B. das Sende- und das Empfangskontingent gleich 1, blockieren Sie die Sendung von Nachrichten an das Postfach, und begrenzen sie den Zugriff auf die Mailbox.
    
    3.  Behalten Sie das Postfach bei, bis alle Daten entfernt sind oder die Aufbewahrung der Daten nicht mehr notwendig ist.

  - **Exchange Online**   Wenn das Postfach eines Benutzers im In-Situ-Speicher platziert oder das Beweissicherungsverfahren auf dieses Postfach angewendet wird und das entsprechende Office 365-Konto gelöscht wird, wird das Postfach in ein *inaktives Postfach*, konvertiert, das eine Art vorläufig gelöschtes Postfach ist. Inaktive Postfächer dienen zur Aufbewahrung von Postfachinhalten eines Benutzers, nachdem dieser die Organisation verlassen hat. Die Elemente in einem inaktiven Postfach werden für die Dauer der Aufbewahrung beibehalten, die für das Postfach aktiviert wurde, bevor es zu einem inaktiven Postfach wurde. Administratoren, Compliance Officer oder Datensatzverwaltungsmanager können dann In-Situ-eDiscovery verwenden, um auf die Inhalte eines inaktiven Postfachs zuzugreifen. Inaktive Postfächer können keine E-Mails empfangen und werden nicht im freigegebenen Adressbuch Ihrer Organisation oder in anderen Listen angezeigt. Weitere Informationen finden Sie unter [Inaktive Postfächer in Exchange Online](https://technet.microsoft.com/de-de/library/dn798632\(v=exchg.150\)).

Zurück zum Seitenanfang

## Migrieren von aufzubewahrenden Postfächern aus Exchange 2013 zu Office 365

Wenn Sie über eine Exchange-Hybridbereitstellung verfügen, treffen beim Verschieben eines (integrierten) lokalen Exchange 2013-Postfachs zu Exchange Online in Office 365 die folgenden Bedingungen zu:

  - Wenn das lokale Postfach im In-Situ-Speicher platziert wurde oder das Beweissicherungsverfahren für das Postfach aktiviert wurde, bleiben die Aufbewahrungseinstellungen erhalten, nachdem das Postfach zu Exchange Online verschoben wurde.

  - Wenn das lokale Postfach im In-Situ-Speicher platziert wurde oder das Beweissicherungsverfahren für das Postfach aktiviert wurde, werden alle Inhalte im Ordner „Wiederherstellbare Elemente“ in das Exchange Online-Postfach verschoben.


> [!NOTE]
> Aufbewahrungseinstellungen und Inhalte im Ordner „Wiederherstellbare Elemente“ werden auch beibehalten, wenn Sie ein Exchange Online-Postfach (extern) in Ihre lokale Exchange 2013-Organisation verschieben.



Es gibt andere Möglichkeiten zum Migrieren lokaler E-Mail-Daten zu Office 365, z. B. die phasenweise Exchange-Migration oder die Exchange-Übernahmemigration.

  - Eine mehrstufige Migration kann zum Migrieren von Postfächern aus Exchange 2003 oder Exchange 2007 zu Office 365 verwendet werden. In diesen Versionen von Exchange ist der Ordner „Wiederherstellbare Elemente“ (und seine Funktionalität) nicht vorhanden. Bei der Migration von Exchange 2003- oder Exchange 2007-Postfächern zu Office 365 sind im Ordner „Wiederherstellbare Elemente“ keine zu verschiebenden Inhalte vorhanden.

  - Die Übernahmemigration kann zum Migrieren von Postfächern aus Exchange 2003, Exchange 2007 und Exchange 2010 zu Office 365 verwendet werden. Wie bereits erläutert, verfügen Exchange 2003- und Exchange 2007-Postfächer über keinen Ordner „Wiederherstellbare Elemente“, der migriert werden kann. Da der Ordner „Wiederherstellbare Elemente“ in Exchange 2010 eingeführt wurde, werden bei Verwendung der Übernahmemigration zum Migrieren vonExchange 2010-Postfächern die Inhalte im Ordner „ Wiederherstellbare Elemente“ zu Office 365 migriert.


> [!TIP]
> Für Exchange 2013 und Exchange 2010 wird die Exchange-Hybridbereitstellung zum Migrieren von lokalen Postfächern zu Office 365 empfohlen.



Zurück zum Seitenanfang

