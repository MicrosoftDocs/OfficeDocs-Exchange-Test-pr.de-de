---
title: 'Aufbewahrungstags und Aufbewahrungsrichtlinien: Exchange 2013 Help'
TOCTitle: Aufbewahrungstags und Aufbewahrungsrichtlinien
ms:assetid: 48c13be5-3f01-4849-a089-766210e54f89
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297955(v=EXCHG.150)
ms:contentKeyID: 50475559
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aufbewahrungstags und Aufbewahrungsrichtlinien

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Microsoft Exchange Server 2013 und Exchange Online unterstützt die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) Organisationen dabei, den E-Mail-Lebenszyklus zu verwalten und die rechtlichen Risiken zu verringern, die mit der E-Mail-Kommunikation und anderen Kommunikationsmethoden einhergehen. MRM vereinfacht die Aufbewahrung von Nachrichten, die zum Erfüllen der Anforderungen von Unternehmensrichtlinien, amtlichen Vorschriften oder rechtlichen Vorgaben notwendig sind, sowie das Entfernen von Inhalten, die keinen juristischen oder geschäftlichen Nutzen mehr haben.

Sehen Sie sich dieses [Video](http://go.microsoft.com/fwlink/?linkid=825854) an, das eine Schnellübersicht über das Anwenden von Aufbewahrungstags und einer Aufbewahrungsrichtlinie auf ein Postfach in Exchange Online enthält.

Sie suchen nach schrittweisen Verfahren zum Verwalten der Messaging-Datensatzverwaltung (MRM)? Weitere Informationen finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

**Inhalt**

Strategie für die Messaging-Datensatzverwaltung

Aufbewahrungstags

Aufbewahrungsrichtlinien

Assistent für verwaltete Ordner

Anhalten der Aufbewahrungszeit

## Strategie für die Messaging-Datensatzverwaltung

In Exchange 2013 und Exchange Online wird MRM mithilfe von *Aufbewahrungstags* und *Aufbewahrungsrichtlinien* implementiert. Bevor die einzelnen Aufbewahrungsfunktionen ausführlicher behandelt werden, ist es zunächst wichtig, die Verwendung der Funktionen in der MRM-Gesamtstrategie zu verstehen. Diese Strategie basiert auf Folgendem:

  - Zuweisen von *Aufbewahrungsrichtlinientags* zu Standardordnern, beispielsweise dem Posteingang und dem Ordner für gelöschte Elemente.

  - Anwenden von *Standardrichtlinientags* auf Postfächer, um die Aufbewahrung aller nicht markierten Elemente zu verwalten.

  - Möglichkeit für Benutzer, benutzerdefinierten Ordnern und einzelnen Elementen *persönliche Tags* zuzuweisen.

  - Trennen der MRM-Funktionalität von den Verwaltungs- und Archivierungsvorgängen, die Benutzer für ihren Posteingang durchführen. Benutzer müssen Nachrichten nicht anhand von Aufbewahrungsanforderungen in verwalteten Ordnern ablegen. Einzelne Nachrichten können ein anderes Aufbewahrungstag aufweisen als die Ordner, in denen sie enthalten sind.

Die folgende Abbildung zeigt die Aufgaben im Zusammenhang mit der Implementierung dieser Strategie.

![Verwenden von Aufbewahrungsrichtlinien für Nachrichten](images/Dd297955.429b51d5-51b8-4816-b8a4-221e0915d0c0(EXCHG.150).gif "Verwenden von Aufbewahrungsrichtlinien für Nachrichten")

Zurück zum Seitenanfang

## Aufbewahrungstags

Wie in der vorhergehenden Abbildung veranschaulicht, werden Aufbewahrungstags dazu verwendet, Aufbewahrungseinstellungen auf Ordner und einzelne Elemente wie E-Mail- und Voicemailnachrichten anzuwenden. Mit diesen Einstellungen wird angegeben, wie lange eine Nachricht in einem Postfach verbleibt und welche Aktion durchgeführt werden soll, wenn der angegebene Aufbewahrungszeitraum der Nachricht abgelaufen ist. Wenn der Aufbewahrungszeitraum einer Nachricht abläuft, wird sie in das Compliance-Archiv des Benutzers verschoben oder gelöscht.

![Einstellungen in einem Aufbewahrungstag](images/Dd297955.936edd6a-8bc4-4c03-94a3-c240ffe7dd6a(EXCHG.150).png "Einstellungen in einem Aufbewahrungstag")

Mithilfe von Aufbewahrungstags können Benutzer ihre eigenen Postfachordner und einzelne Elemente für die Aufbewahrung kennzeichnen. Die Benutzer müssen Elemente nicht länger in verwalteten Ordnern archivieren, die von einem Administrator auf Grundlage der Anforderungen für die Nachrichtenaufbewahrung bereitgestellt werden.

## Typen von Aufbewahrungstags

Aufbewahrungstags werden in die folgenden drei Typen unterteilt, je nachdem, wer sie anwenden kann und wo in einem Postfach sie angewendet werden können.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Typ des Aufbewahrungstags</th>
<th>Angewendet...</th>
<th>Angewendet von...</th>
<th>Verfügbare Aktionen...</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standardrichtlinientag</p></td>
<td><p>Automatisch auf das gesamte Postfach</p>
<p>Ein Standardrichtlinientag wird auf <em>nicht gekennzeichnete</em> Elemente angewendet, d. h. Elemente, auf die Aufbewahrungstags weder direkt noch durch Vererbung über den Ordner angewendet wurden.</p></td>
<td><p>Administrator</p></td>
<td><ul>
<li><p>In Archiv verschieben</p></li>
<li><p>Löschen und Wiederherstellung zulassen</p></li>
<li><p>Permanent löschen</p></li>
</ul></td>
<td><p>Benutzer können auf ein Postfach angewendete Standardrichtlinientags nicht ändern.</p></td>
</tr>
<tr class="even">
<td><p>Aufbewahrungsrichtlinientag</p></td>
<td><p>Automatisch auf einen Standardordner</p>
<p>Standardordner sind Ordner, die in allen Postfächern automatisch erstellt werden. Beispiel: <strong>Posteingang</strong>, <strong>Gelöschte Elemente</strong> und <strong>Gesendete Elemente</strong>. Eine Liste der unterstützten Standardorder finden Sie unter <a href="default-folders-that-support-retention-policy-tags-exchange-2013-help.md">Standardordner, die Aufbewahrungsrichtlinientags unterstützen</a>.</p></td>
<td><p>Administrator</p></td>
<td><ul>
<li><p>Löschen und Wiederherstellung zulassen</p></li>
<li><p>Permanent löschen</p></li>
</ul></td>
<td><p>Benutzer können auf einen Standardordner angewendete Standardrichtlinientags nicht ändern.</p></td>
</tr>
<tr class="odd">
<td><p>Persönliches Tag</p></td>
<td><p>Manuell auf Elemente und Ordner</p>
<p>Benutzer können die Kennzeichnung mithilfe von Posteingangsregeln automatisieren, um eine Nachricht entweder in einen Ordner zu verschieben, der über ein bestimmtes Tag verfügt, oder um ein persönliches Tag auf die Nachricht anzuwenden.</p></td>
<td><p>Benutzer</p></td>
<td><ul>
<li><p>In Archiv verschieben</p></li>
<li><p>Löschen und Wiederherstellung zulassen</p></li>
<li><p>Permanent löschen</p></li>
</ul></td>
<td><p>Persönliche Tags ermöglichen Benutzern zu bestimmen, wie lange ein Element beibehalten werden soll. Beispiel: Das Postfach kann über ein Standardrichtlinientag verfügen, damit Elemente nach sieben Jahren gelöscht werden. Benutzer können jedoch eine Ausnahme für Elemente wie beispielsweise Newsletter oder automatische Benachrichtigungen erstellen, indem sie ein persönliches Tag anwenden, sodass diese Elemente nach drei Tagen gelöscht werden.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen zu persönlichen Tags

Persönliche Tags stehen Benutzern von Outlook 2010 und Outlook Web App als Bestandteil ihrer Aufbewahrungsrichtlinie zur Verfügung. In Outlook 2010 und Outlook Web App werden persönliche Tags mit der Aktion **In Archiv verschieben** als **Archivrichtlinie** und persönliche Tags mit der Aktion **Löschen und Wiederherstellung zulassen** oder **Endgültig löschen** als **Aufbewahrungsrichtlinie** angezeigt, wie in der folgenden Abbildung dargestellt ist.

![Persönliche Tags in Outlook 2010 und Outlook Web App](images/Dd297955.2dbaee13-fdd0-4c30-b821-e662ce2587bb(EXCHG.150).gif "Persönliche Tags in Outlook 2010 und Outlook Web App")

Benutzer können persönliche Tags auf von ihnen erstellte Ordner oder auf einzelnen Elemente anwenden. Nachrichten, auf die persönliche Tags angewendet sind, werden immer auf der Basis der Einstellungen der persönlichen Tags verarbeitet. Benutzer können ein persönliches Tag auf eine Nachricht anwenden, sodass diese früher oder später verschoben oder gelöscht wird, als durch das Standardrichtlinientag oder die Aufbewahrungsrichtlinientags angegeben ist, die auf das Postfach dieses Benutzers angewendet wurden. Sie können außerdem persönliche Tags erstellen, in denen die Aufbewahrung deaktiviert ist. Hierdurch ist es Benutzern möglich, Elemente so zu kennzeichnen, dass diese nie in ein Archiv verschoben werden oder nie ablaufen.


> [!NOTE]
> Benutzer können Archivrichtlinien auf Standardordner, auf von Benutzern erstellte Ordner oder Unterordner und auf einzelne Elemente anwenden. Benutzer können eine Aufbewahrungsrichtlinie auf von Benutzern erstellte Ordner oder Unterordner und auf einzelne Elemente (was auch Unterordner und Elemente in einem Unterordner einschließt), jedoch nicht auf Standardordner anwenden.



Benutzer können mithilfe der Exchange-Verwaltungskonsole zusätzliche persönliche Tags auswählen, die nicht mit ihrer Aufbewahrungsrichtlinie verknüpft sind. Die ausgewählten Tags sind anschließend in Outlook 2010 und Outlook Web App verfügbar. Damit Benutzer zusätzliche Tags in der Exchange-Verwaltungskonsole auswählen können, müssen Sie die [Rolle „MyRetentionPolicies“](myretentionpolicies-role-exchange-2013-help.md) zur Rollenzuweisungsrichtlinie des Benutzers hinzufügen. Weitere Informationen zu Rollenzuweisungsrichtlinien für Benutzer finden Sie unter [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md). Wenn Sie Benutzern die Auswahl zusätzlicher persönlicher Tags erlauben, werden alle persönlichen Tags in Ihrer Exchange-Organisation für die Benutzer verfügbar.


> [!NOTE]
> Persönliche Tags sind ein Premium-Feature. Für Postfächer mit Richtlinien, die diese Tags enthalten (oder diese Tags aufweisen, weil Benutzer die Tags zu ihrem Postfach hinzugefügt haben), ist eine Exchange Enterprise-Clientzugriffslizenz (CAL) erforderlich.



Zurück zum Seitenanfang

## Aufbewahrungszeitraum

Wenn Sie ein Aufbewahrungstag aktivieren, müssen Sie einen Aufbewahrungszeitraum für das Tag angeben. Dieser Zeitraum gibt die Anzahl der Tage an, die eine Nachricht aufbewahrt wird, nachdem sie im Postfach des Benutzers eingegangen ist.

Der Aufbewahrungszeitraum für nicht wiederkehrende Elemente (z. B. E-Mail-Nachrichten) wird anders berechnet als für Elemente mit Enddatum oder für Serienelemente (z. B. Besprechungen und Aufgaben). Informationen zum Berechnen des Aufbewahrungszeitraums für verschiedene Elementtypen finden Sie unter [Berechnung von Aufbewahrungszeiträumen](how-retention-age-is-calculated-exchange-2013-help.md).

Sie können auch Aufbewahrungstags mit deaktivierter Aufbewahrung erstellen oder die Tags nach der Erstellung deaktivieren. Da Nachrichten mit deaktiviertem Tag nicht verarbeitet werden, findet keine Aufbewahrungsaktion statt. Daher können Benutzer ein deaktiviertes persönliches Tag als **Nie verschieben**- oder **Nie löschen**-Tag verwenden, um ein Standardrichtlinientag oder ein Aufbewahrungsrichtlinientag außer Kraft zu setzen, das ansonsten auf die Nachricht angewendet werden würde.

## Aufbewahrungsaktionen

Beim Erstellen oder Konfigurieren eines Aufbewahrungstags können Sie eine der folgenden Aufbewahrungsaktionen auswählen, die ausgeführt werden, wenn für ein Element das Ende des Aufbewahrungszeitraums erreicht ist:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Aufbewahrungsaktion</th>
<th>Ausgeführte Aktion...</th>
<th>Mit Ausnahme von...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>In Archiv verschieben</strong> 1</p></td>
<td><ul>
<li><p>Verschiebt die Nachricht in das Archivpostfach des Benutzers</p></li>
<li><p>Nur verfügbar für Standardrichtlinientags und persönliche Tags</p></li>
</ul>
<p>Weitere Informationen zur Archivierung finden Sie unter:</p>
<ul>
<li><p><a href="in-place-archiving-in-exchange-2013-exchange-2013-help.md">In-Situ-Archivierung in Exchange 2013</a></p></li>
<li><p><a href="https://technet.microsoft.com/de-de/library/dn922147(v=exchg.150)">Archivieren von Postfächern in Exchange Online</a></p></li>
</ul></td>
<td><ul>
<li><p>Wenn der Benutzer nicht über ein Archivpostfach verfügt, wird keine Aktion durchgeführt.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Löschen und Wiederherstellung zulassen</strong></p></td>
<td><ul>
<li><p>Emuliert das Verhalten, wenn der Benutzer den Ordner &quot;Gelöschte Elemente&quot; leert.</p></li>
<li><p>Elemente werden in den <a href="recoverable-items-folder-exchange-2013-help.md">Ordner &quot;Wiederherstellbare Elemente&quot;</a> im Postfach verschoben und bis zum Ablauf der <em>Aufbewahrungszeit für gelöschte Objekte</em> aufbewahrt.</p></li>
<li><p>Der Benutzer erhält eine zweite Möglichkeit, das Element im Dialogfeld <strong>Gelöschte Elemente wiederherstellen</strong> in Outlook oder in Outlook Web App wiederherzustellen.</p></li>
</ul></td>
<td><ul>
<li><p>Wenn Sie die Aufbewahrungszeit für gelöschte Elemente auf null Tage festlegen, werden Elemente dauerhaft gelöscht. Weitere Informationen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/dn163584(v=exchg.150)">Ändern des Aufbewahrungszeitraums für gelöschte Elemente für ein Exchange Online-Postfach</a>.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Permanent löschen</strong></p></td>
<td><ul>
<li><p>Nachrichten werden dauerhaft gelöscht.</p></li>
<li><p>Nachrichten können nicht wiederhergestellt werden, nachdem sie dauerhaft gelöscht wurden.</p></li>
</ul></td>
<td><ul>
<li><p>Wenn für das Postfach <a href="in-place-hold-and-litigation-hold-exchange-2013-help.md">In-Place Hold and Litigation Hold</a> oder das Beweissicherungsverfahren aktiviert wurde, werden Elemente im Ordner &quot;Wiederherstellbare Elemente&quot; basierend auf den entsprechenden Parametern beibehalten. <a href="in-place-ediscovery-exchange-2013-help.md">Compliance-eDiscovery</a> gibt diese Elemente weiterhin in den Suchergebnissen zurück.</p>
<p></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Als nach dem Aufbewahrungslimit liegend markieren</strong></p></td>
<td><ul>
<li><p>Markiert eine Nachricht als abgelaufen. In Outlook 2010 (oder höher) und Outlook Web App werden abgelaufene Elemente mit der Benachrichtigung &quot;Dieses Element ist abgelaufen&quot; und &quot;Dieses Element läuft in 0 Tagen ab&quot; angezeigt. In Outlook 2007 werden als abgelaufen gekennzeichnete Elemente mithilfe von durchgestrichenem Text angezeigt.</p></li>
</ul></td>
<td><p>N/V</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 1&nbsp;&nbsp;&nbsp;In einer Exchange-Hybridbereitstellung können Sie ein cloudbasiertes Archivpostfach für ein lokales primäres Postfach aktiveren. Beim Zuweisen einer Archivrichtlinie zu einem lokalen Postfach werden die Elemente zum cloudbasierten Archiv verschoben. Wenn ein Element in das Archivpostfach verschoben wird, wird im lokalen Postfach keine Kopie davon beibehalten. Wenn das lokale Postfach ausgesetzt wird, werden Elemente anhand einer Archivrichtlinie weiterhin in das cloudbasierte Archivpostfach verschoben, in dem sie so lange aufbewahrt werden, wie dies durch die In-Situ-Speicherung festgelegt wurde.



Weitere Informationen zum Erstellen von Aufbewahrungstags finden Sie unter [Erstellen einer Aufbewahrungsrichtlinie](create-a-retention-policy-exchange-2013-help.md).

Zurück zum Seitenanfang

## Aufbewahrungsrichtlinien

Zur Anwendung von mindestens einem Aufbewahrungstag auf ein Postfach müssen Sie die Tags zu einer Aufbewahrungsrichtlinie hinzufügen und anschließend die Richtlinie auf das Postfach anwenden. Ein Postfach kann nur eine Aufbewahrungsrichtlinie aufweisen. Aufbewahrungstags können jederzeit mit einer Aufbewahrungsrichtlinie verknüpft bzw. eine derartige Verknüpfung kann jederzeit aufgehoben werden. Die Änderungen werden dann für alle Postfächer automatisch wirksam, auf die die Richtlinie angewendet wird.

Eine Aufbewahrungsrichtlinie kann die folgenden Aufbewahrungstags aufweisen:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Aufbewahrungstagtyp</th>
<th>Tags in einer Richtlinie</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standardrichtlinientag</p></td>
<td><ul>
<li><p>Ein Standardrichtlinientag mit der Aktion <strong>In Archiv verschieben</strong></p></li>
<li><p>Ein Standardrichtlinientag mit der Aktion <strong>Löschen und Wiederherstellung zulassen</strong> oder <strong>Endgültig löschen</strong></p></li>
<li><p>Ein Standardrichtlinientag für Voicemailnachrichten mit der Aktion <strong>Löschen und Wiederherstellung zulassen</strong> oder <strong>Endgültig löschen</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Aufbewahrungsrichtlinientags</p></td>
<td><ul>
<li><p>Ein Aufbewahrungsrichtlinientag für jeden unterstützten Standardordner</p>

> [!NOTE]
> Sie können nicht mehr als ein Aufbewahrungsrichtlinientag für einen bestimmten Standardordner (z.&nbsp;B. <STRONG>Gelöschte Elemente</STRONG>) mit derselben Aufbewahrungsrichtlinie verknüpfen.


</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Persönliche Tags</p></td>
<td><ul>
<li><p>Eine beliebige Anzahl von persönlichen Tags</p></li>
</ul>

> [!TIP]
> Viele persönliche Tags in einer Richtlinie können für Benutzer verwirrend sein. Es wird empfohlen, einer Aufbewahrungsrichtlinie nicht mehr als 10&nbsp;persönliche Tags hinzuzufügen.


</td>
</tr>
</tbody>
</table>



> [!NOTE]
> Auch wenn Sie eine Aufbewahrungsrichtlinie nicht zwingend mit Aufbewahrungstags verknüpfen müssen; wird ein solches Szenario trotzdem nicht empfohlen. Wenn keine Aufbewahrungstags mit Postfächern mit Aufbewahrungsrichtlinien verknüpft sind, kann dies dazu führen, dass die Postfachelemente niemals ablaufen.



Eine Aufbewahrungsrichtlinie kann sowohl Archivtags (Tags, mit denen Elemente in das persönliche Archivpostfach verschoben werden) als auch Löschungstags (Tags, die Elemente löschen) enthalten. Auf ein Postfachelement können ebenfalls beide Arten von Tags angewendet werden. Archivpostfächer verfügen über keine separate Aufbewahrungsrichtlinie. Dieselbe Aufbewahrungsrichtlinie wird auf das primäre und das Archivpostfach angewendet.

Wenn Sie planen, Aufbewahrungsrichtlinien zu erstellen, müssen Sie berücksichtigen, ob diese sowohl Archiv- als auch Löschungstags einbeziehen werden. Wie bereits erwähnt, kann eine Aufbewahrungsrichtlinie über ein Standardrichtlinientag, das die Aktion **In Archiv verschieben** verwendet, und über ein Standardrichtlinientag verfügen, das entweder die Aktion **Löschen und Wiederherstellung zulassen** oder **Endgültig löschen** verwendet. Das Standardrichtlinientag mit der Aktion **In Archiv verschieben** muss einen kürzeren Aufbewahrungszeitraum aufweisen als das Standardrichtlinientag mit einem Löschvorgang. Sie können z. B. ein Standardrichtlinientag mit der Aktion **In Archiv verschieben** verwenden, um Elemente in zwei Jahren in das Archivpostfach zu verschieben, während Sie ein Standardrichtlinientag mit einem Löschvorgang verwenden, um Elemente in sieben Jahren aus dem Postfach zu entfernen. Elemente in primären und Archivpostfächern werden nach sieben Jahren gelöscht.

Eine Liste der Verwaltungsaufgaben im Zusammenhang mit den Aufbewahrungsrichtlinien finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Standardaufbewahrungsrichtlinie

Exchange-Setup erstellt eine **MRM-Standardrichtlinie** für die Aufbewahrung. Die MRM-Standardrichtlinie wird automatisch auf alle neuen Postfächer in Exchange Online angewendet. In Exchange Server wird die Richtlinie automatisch angewendet, wenn Sie ein Archiv für den neuen Benutzer erstellen und keine Aufbewahrungs-Richtlinie angeben.

Sie können Tags modifizieren, die in der MRM-Standardrichtlinie enthalten sind, z. B., indem Sie die Verfallszeit für die Aufbewahrung oder die Aufbewahrungsaktion ändern, ein Tag deaktivieren oder die Richtlinie ändern, indem Sie Tags zu ihr hinzufügen oder aus ihr entfernen. Die aktualisierte Richtlinie wird ab der nächsten Verarbeitung von Postfächern durch den Assistent für verwaltete Ordner auf die Postfächer angewendet.

Genauere Informationen, darunter eine Liste von mit der Richtlinie verknüpften Aufbewahrungs-Tags finden Sie unter [Standardaufbewahrungsrichtlinie in Exchange Online und Exchange Server](default-retention-policy-in-exchange-online-and-exchange-server-exchange-2013-help.md).

Zurück zum Seitenanfang

## Assistent für verwaltete Ordner

Der Assistent für verwaltete Ordner, ein auf Postfachservern ausgeführter Postfach-Assistent, verarbeitet Postfächer, auf die eine Aufbewahrungsrichtlinie angewendet wird.

Der Assistent für verwaltete Ordner wendet die Aufbewahrungsrichtlinie an, indem die Elemente im Postfach untersucht werden und somit ermittelt wird, ob diese aufbewahrt werden müssen. Elemente, die der Aufbewahrung unterliegen, werden dann mit den entsprechenden Aufbewahrungstags versehen, und die angegebene Aufbewahrungsaktion wird für Elemente ausgeführt, deren Aufbewahrungslimit überschritten wurde.

Der Assistent für verwaltete Ordner ist ein einschränkungsbasierter Assistent. Einschränkungsbasierte Assistenten werden immer ausgeführt und müssen nicht eingeplant werden. Die Systemressourcen, die von ihnen beansprucht werden können, sind eingeschränkt. Sie können den Assistenten für verwaltete Ordner so konfigurieren, dass dieser alle Postfächer auf dem Postfachserver innerhalb eines bestimmten Zeitraums verarbeitet (auch als *Arbeitszyklus* bezeichnet). Zusätzlich aktualisiert der Assistent in einem angegebenen Intervall (auch als *Arbeitszyklusprüfpunkt* bezeichnet) die Liste der zu verarbeitenden Postfächer. Während der Aktualisierung fügt der Assistent neu erstellte oder verschobene Postfächer zur Warteschlange hinzu. Er weist vorhandenen Postfächern auch neue Prioritäten zu, die aufgrund von Fehlern nicht erfolgreich verarbeitet wurden und verschiebt sie in der Warteschlange nach vorne, damit Sie im gleichen Arbeitszyklus verarbeitet werden können.

Sie können auch das Cmdlet [Start-ManagedFolderAssistant](https://technet.microsoft.com/de-de/library/aa998864\(v=exchg.150\)) verwenden, um den Assistenten für die Verarbeitung eines Postfachs manuell auszulösen. Weitere Informationen finden Sie unter [Konfigurieren des Assistenten für verwaltete Ordner](configure-the-managed-folder-assistant-exchange-2013-help.md).


> [!NOTE]
> Der Assistent für verwaltete Ordner führt keine Aktion für Nachrichten aus, die nicht der Aufbewahrung unterliegen, was durch Deaktivieren des Aufbewahrungstags angegeben wird. Sie können ein Aufbewahrungstag auch deaktivieren, um die Verarbeitung von Elementen mit diesem Tag temporär einzustellen.



## Verschieben von Elementen zwischen Ordnern

Ein Postfachelement, das von einem Ordner in einen anderen verschoben wird, erbt ggf. alle Tags, die auf den Zielordner angewendet wurden. Wenn ein Element in einen Ordner verschoben wird, dem kein Tag zugewiesen wurde, wird das Standardrichtlinientag angewendet. Wenn dem Element ein Tag explizit zugewiesen wurde, hat dieses Tag immer Vorrang gegenüber allen Tags auf Ordnerebene sowie gegenüber dem Standardtag.

## Anwenden eines Aufbewahrungstags auf einen Ordner im Archiv

Wenn der Benutzer ein persönliches Tag auf einen Ordner im Archiv anwendet und im primären Postfach ein Ordner mit dem gleichen Namen, aber einem anderen Tag existiert, wird das Tag für diesen Ordner im Archiv so geändert, dass es mit dem im primären Postfach übereinstimmt. Dadurch wird Verwechslungen bei Elementen in einem Ordner im Archiv vorgebeugt, die ein anderes Ablaufverhalten aufweisen als der gleiche Ordner im primären Postfach des Benutzers. Beispiel: Der Benutzer besitzt im primären Postfach einen Ordner mit dem Namen "Project Contoso" und dem Tag *Löschen – 3 Jahre*. Außerdem enthält auch das Archivpostfach einen Ordner mit dem Namen "Project Contoso". Der Benutzer wendet ein persönliches *Löschen – 1 Jahr*-Tag an, um Elemente im Ordner nach 1 Jahr zu löschen. Wenn das Postfach erneut verarbeitet wird, wird der Ordner auf das Tag "Löschen – 3 Jahre" zurückgesetzt.

## Entfernen oder Löschen eines Aufbewahrungstags aus einer Aufbewahrungsrichtlinie

Wenn ein Aufbewahrungstag aus der auf ein Postfach angewendeten Aufbewahrungsrichtlinie entfernt wird, steht das Tag nicht mehr für den Benutzer zur Verfügung und kann nicht auf Elemente im Postfach angewendet werden.

Vorhandene Elemente, auf die dieses Tag angewendet wurde, werden weiterhin anhand dieser Einstellungen vom Assistenten für verwaltete Ordner verwaltet, und alle im Tag angegebenen Aufbewahrungsaktionen werden auf diese Nachrichten angewendet.

Wenn Sie das Tag jedoch löschen, wird die in Active Directory gespeicherte Definition entfernt. Das führt dazu, dass der Assistent für verwaltete Ordner alle Elemente in einem Postfach verarbeitet und diejenigen mit einem neuen Tag versieht, auf die das entfernte Tag angewendet wurde. Je nach Anzahl von Postfächern und Nachrichten kann dieser Prozess erhebliche Ressourcen auf allen Postfachservern in Anspruch nehmen, die Postfächer mit Aufbewahrungsrichtlinien enthalten, in denen das entfernte Tag enthalten war.


> [!IMPORTANT]
> Wenn ein Aufbewahrungstag aus einer Aufbewahrungsrichtlinie entfernt wird, verlieren ggf. alle vorhandenen Postfachelemente, auf die das Tag angewendet wurde, ihre Gültigkeit weiterhin laut den Einstellungen im Tag. Wenn Sie verhindern möchten, dass die Einstellungen des Tags weiterhin auf Elemente angewendet werden, sollten Sie das Tag löschen. Indem Sie ein Tag löschen, entfernen Sie es aus allen Aufbewahrungsrichtlinien, in denen es enthalten ist.



## Deaktivieren eines Aufbewahrungstags

Wenn Sie ein Aufbewahrungstag deaktivieren, ignoriert der Assistent für verwaltete Ordner Elemente, auf die dieses Tag angewendet wurde. Elemente mit einem Aufbewahrungstag, für das die Aufbewahrung deaktiviert ist, werden in Abhängigkeit von der angegebenen Aufbewahrungsaktion entweder nie verschoben oder nie gelöscht. Da diese Elemente weiterhin als mit einem Tag markierte Elemente angesehen werden, wird auf sie nicht das Standardrichtlinientag angewendet. Wenn Sie beispielsweise eine Problembehandlung für Einstellungen von Aufbewahrungstags durchführen möchten, können Sie ein Aufbewahrungstag vorübergehend deaktivieren, um zu verhindern, dass der Assistent für verwaltete Ordner Nachrichten mit diesem Tag verarbeitet.


> [!NOTE]
> Der Aufbewahrungszeitraum für ein deaktiviertes Aufbewahrungstag wird dem Benutzer als <STRONG>Nie</STRONG> angezeigt. Wenn ein Benutzer ein Element markiert, von dem er annimmt, dass es nie gelöscht wird, kann das nachträgliche Aktivieren des Tags dazu führen, dass Elemente ungewollt gelöscht werden. Das Gleiche gilt für Tags mit der Aktion <STRONG>In Archiv verschieben</STRONG>.



Zurück zum Seitenanfang

## Anhalten der Aufbewahrungszeit

Wenn Benutzer sich vorübergehend nicht am Arbeitsplatz befinden und nicht über Zugriff auf ihre E-Mails verfügen, können Aufbewahrungseinstellungen auf neue Nachrichten angewendet werden, bevor der jeweilige Benutzer zum Arbeitsplatz zurückkehrt oder über E-Mail-Zugriff verfügt. Abhängig von der Aufbewahrungsrichtlinie können Nachrichten gelöscht oder in das persönliche Archiv des Benutzers verschoben werden. Sie können die Verarbeitung eines Postfachs durch Aufbewahrungsrichtlinien für einen angegebenen Zeitraum anhalten, indem Sie die Aufbewahrungszeit für das Postfach anhalten. Wenn Sie die Aufbewahrungszeit für ein Postfach anhalten, können Sie außerdem einen Aufbewahrungskommentar angeben, mit dem der Postfachbenutzer (oder ein anderer Benutzer, der zum Zugreifen auf das Postfach autorisiert ist) über das Anhalten der Aufbewahrungszeit informiert wird (einschließlich des geplanten Anfangs und Endes). Aufbewahrungskommentare werden auf unterstützten Outlook-Clients angezeigt. Sie können den Aufbewahrungskommentar auch in die bevorzugte Sprache des Benutzers lokalisieren.


> [!NOTE]
> Das Anhalten der Aufbewahrungszeit für ein Postfach hat keine Auswirkung auf die Verarbeitung von Speicherkontingenten für das Postfach. Abhängig von der Speicherverwendung des Postfachs und den anwendbaren Postfachkontingenten sollten Sie möglicherweise das Speicherkontingent des Postfachs für Benutzer erhöhen, die für längere Zeit in Urlaub sind oder nicht über Zugriff auf E-Mail verfügen. Weitere Informationen zu Speicherkontingenten für Postfächer finden Sie unter <A href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">Konfigurieren von Speicherkontingenten für ein Postfach</A>.



Für Benutzer, die lange nicht am Arbeitsplatz sind, können sich sehr viele E-Mails ansammeln. Abhängig von der Anzahl der E-Mails und der Dauer der Abwesenheit können diese Benutzer einige Wochen benötigen, um ihre Nachrichten durchzusehen. Berücksichtigen Sie in diesen Fällen die zusätzliche Zeit, die die Benutzer möglicherweise benötigen, um ihre E-Mails aufzuarbeiten, bevor Sie das Anhalten der Aufbewahrungszeit beenden.

Wenn in Ihrem Unternehmen keine Messaging-Datensatzverwaltung implementiert wurde und die Benutzer mit deren Funktionen nicht vertraut sind, können Sie während der anfänglichen *Aufwärm- und Schulungsphase* für die Bereitstellung der Messaging-Datensatzverwaltung auch Aufbewahrungszeiten verwenden. Sie können Aufbewahrungsrichtlinien erstellen und bereitstellen sowie die Benutzer über die Richtlinien in Kenntnis setzen, ohne zu riskieren, dass Elemente verschoben oder gelöscht werden, bevor diese von Benutzern markiert werden können. Wenige Tage vor dem Ende der Aufwärm- und Schulungsphase sollten Sie die Benutzer an die Aufwärmfrist erinnern. Nachdem die Frist abgelaufen ist, können Sie die Aufbewahrungszeit für Postfächer entfernen, wodurch der Assistent für verwaltete Ordner die Möglichkeit erhält, Postfachelemente zu verarbeiten und die angegebene Aufbewahrungsaktion durchzuführen.

Weitere Informationen zum Anhalten der Aufbewahrungszeit für ein Postfach finden Sie unter [Anhalten der Aufbewahrungszeit für ein Postfach](place-a-mailbox-on-retention-hold-exchange-2013-help.md).

Zurück zum Seitenanfang

