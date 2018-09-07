---
title: 'Verwalten der Nachrichtengenehmigung: Exchange 2013 Help'
TOCTitle: Verwalten der Nachrichtengenehmigung
ms:assetid: 43a89f71-8002-4cb0-b3c8-1c2b2597f227
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297936(v=EXCHG.150)
ms:contentKeyID: 50475551
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten der Nachrichtengenehmigung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-05-04_

Manchmal ist es sinnvoll, eine Nachricht von einer zweiten Person überprüfen zu lassen (Vier-Augen-Prinzip), bevor sie zugestellt wird. Als Exchange-Administrator können Sie dies festlegen. Dieses Verfahren wird als *Moderation* bezeichnet, und die genehmigende Person ist der *Moderator*. Je nachdem, welche Nachrichten genehmigt werden müssen, können Sie zwei verschiedene Ansätze zugrunde legen:

  - Ändern der Verteilergruppeneigenschaften

  - Erstellen einer Nachrichtenflussregel

In diesem Artikel wird Folgendes erläutert:

  - Entscheiden, welche Vorgehensweise für die Genehmigung verwendet werden soll

  - Funktionsweise des Genehmigungsvorgangs

Informationen zum Implementieren gängiger Szenarien finden Sie unter [Gängige Szenarien der Nachrichtengenehmigung](common-message-approval-scenarios-exchange-2013-help.md).

## Entscheiden, welche Vorgehensweise für die Genehmigung verwendet werden soll

Es folgt ein Vergleich der beiden Ansätze für die Nachrichtengenehmigung.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Was möchten Sie machen?</th>
<th>Ansatz</th>
<th>Erster Schritt</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Erstellen einer moderierten Verteilergruppe, wobei alle Nachrichten an die Gruppe moderiert werden müssen</p></td>
<td><p>Einrichten der Nachrichtengenehmigung für die Verteilergruppe</p></td>
<td><p>Navigieren Sie zum Exchange-Verwaltungskonsole (EAC) &gt; <strong>Empfänger</strong> &gt;<strong> Gruppen</strong>, bearbeiten Sie die Verteilergruppe, und wählen Sie dann <strong>Nachrichtengenehmigung</strong> aus.</p></td>
</tr>
<tr class="even">
<td><p>Festlegen, dass Nachrichten genehmigt werden müssen, die bestimmten Kriterien entsprechen oder an eine bestimmte Person gesendet werden</p></td>
<td><p>Erstellen Sie eine Transportregel mithilfe der Aktion <strong>Die Nachricht zur Genehmigung weiterleiten</strong>.</p>
<p>Sie können Kriterien für Nachrichten angeben, wie beispielsweise Textmuster, Absender und Empfänger. Die Kriterien können auch Ausnahmen enthalten.</p></td>
<td><p>Navigieren Sie zum EAC &gt; <strong>Nachrichtenfluss</strong> &gt; <strong>Regeln</strong>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Funktionsweise des Genehmigungsvorgangs

Wenn Benutzer eine Nachricht, die genehmigt werden muss, an eine Person oder eine Gruppe senden, werden sie benachrichtigt, dass die Nachricht möglicherweise mit Verzögerung zugestellt wird, sofern sie Outlook Web Access verwenden.

![Nachricht, mit der Nachrichtengenehmigungsbenachrichtigung anzeigt wird](images/Dd297936.80e2e5f1-0a1e-4c37-9076-794581155405(EXCHG.150).png "Nachricht, mit der Nachrichtengenehmigungsbenachrichtigung anzeigt wird")

Der Moderator erhält eine E-Mail mit der Aufforderung, die Nachricht zu genehmigen oder abzulehnen. Die Nachricht enthält Schaltflächen, über die die Nachricht genehmigt oder abgelehnt werden kann, und die ursprüngliche Nachricht ist zur Überprüfung in der Anlage enthalten.

![Genehmigungsanforderungsnachricht mit Anhang](images/Dd297936.bf517f5a-b10e-40df-a48a-403b395b5962(EXCHG.150).png "Genehmigungsanforderungsnachricht mit Anhang")

Der Moderator kann eine der drei folgenden Maßnahmen ergreifen:

![Workflow, mit dem Optionen für Genehmigung einer Nachricht angezeigt werden](images/Dd297936.dc7a6ca9-c67d-487a-8713-4d628e07f4b3(EXCHG.150).png "Workflow, mit dem Optionen für Genehmigung einer Nachricht angezeigt werden")

1.  Wenn die Nachricht genehmigt wurde, wird sie an die ursprünglich vorgesehenen Empfänger zugestellt. Der ursprüngliche Absender wird nicht benachrichtigt.

2.  Wenn die Nachricht abgelehnt wurde, wird eine Ablehnungsnachricht an den Absender gesendet. Der Moderator kann eine Erklärung hinzufügen:
    
    ![Ablehnungsbenachrichtigung mit Kommentaren vom Moderator](images/Dd297936.a663d36a-c67d-4155-b8f6-4b5dc8e105d9(EXCHG.150).png "Ablehnungsbenachrichtigung mit Kommentaren vom Moderator")  

3.  Wenn die genehmigende Person die Nachricht entweder löscht oder ignoriert, wird eine Ablaufnachricht an den Absender gesendet. Dies geschieht in Exchange Online nach zwei Tagen und in Exchange Server 2013 nach fünf Tagen. (In Exchange Server 2013 können Sie diesen Zeitraum ändern).

Die zur Genehmigung anstehende Nachricht wird vorübergehend in einem als *Vermittlungspostfach* bezeichneten Systempostfach gespeichert. Die ursprüngliche Nachricht wird so lange im Vermittlungspostfach aufbewahrt, bis der Moderator die Nachricht genehmigt oder ablehnt, die Genehmigungsnachricht löscht oder zulässt, dass die Genehmigungsnachricht abläuft.

Zurück zum Seitenanfang

## Fragen und Antworten

**Welcher Unterschied besteht zwischen der genehmigenden Person und dem Besitzer einer Verteilergruppe?**

Der Besitzer einer Verteilergruppe ist für die Verwaltung der Mitgliedschaft in der Verteilergruppe verantwortlich, kann aber möglicherweise keine an sie gesendeten Nachrichten moderieren. Beispiel: Eine Person in der IT-Abteilung ist der Besitzer einer Verteilergruppe namens "All Employees", aber nur der Manager der Personalabteilung ist als Moderator eingerichtet.

**Was geschieht, wenn der Moderator oder die genehmigende Person eine Nachricht an die Verteilergruppe sendet?**

Die Nachricht wird unter Umgehung des Genehmigungsvorgangs direkt an die Gruppe gesendet.

**Was geschieht, wenn nur für einen Teil der Empfänger eine Genehmigung erforderlich ist?**

Sie können eine Nachricht an eine Gruppe von Empfängern senden, wenn nur für eine Teilmenge der Empfänger eine Genehmigung benötigt wird. Betrachten Sie beispielsweise eine Nachricht, die an 12 Empfänger gesendet wird, von denen einer eine moderierte Verteilergruppe ist. Die Nachricht wird automatisch in zwei Kopien aufgeteilt. Eine Nachricht wird sofort an die 11 Empfänger gesendet, für die keine Genehmigung erforderlich ist, während die zweite Nachricht an den Genehmigungsvorgang für die moderierte Verteilergruppe übermittelt wird. Ist eine Nachricht für mehrere moderierte Empfänger vorgesehen, wird automatisch eine separate Kopie der Nachricht für jeden moderierten Empfänger erstellt, und jede Kopie durchläuft den entsprechenden Genehmigungsvorgang.

**Was muss ich tun, wenn meine Verteilergruppe moderierte Empfänger enthält, für die eine Genehmigung erforderlich ist?**

Eine Verteilergruppe kann moderierte Empfänger enthalten, für die eine Genehmigung durchgeführt werden muss. In diesem Fall wird nach der Genehmigung der Nachricht an die Verteilergruppe ein separater Genehmigungsvorgang für jeden moderierten Empfänger durchgeführt, der Mitglied der Verteilergruppe ist. Sie können jedoch auch die automatische Genehmigung für die Mitglieder der Verteilergruppe im Anschluss an die Genehmigung der Nachricht an die moderierte Verteilergruppe aktivieren. Verwenden Sie hierfür den Parameter *BypassNestedModerationEnabled* im Cmdlet [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\)).

**Ist das Verfahren ein anderes, wenn wir über unsere eigenen Exchange-Server verfügen?**

Standardmäßig wird für jede Exchange-Organisation ein Vermittlungspostfach verwendet. Wenn Sie über eigene Exchange-Server verfügen und für den Lastenausgleich weitere Vermittlungspostfächer benötigen, befolgen Sie die Anweisungen zum Hinzufügen von Vermittlungspostfächern unter [Verwalten und Problembehandlung der Nachrichtengenehmigung](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/ttroubleshoot-message-approval). Vermittlungspostfächer sind Systempostfächer, für die keine Exchange-Lizenz erforderlich ist.


> [!NOTE]
> <STRONG>Bei Verwendung von Exchange 2007:</STRONG> Microsoft Exchange Server&nbsp;2007 bietet keine Unterstützung für moderierte Empfänger. Wenn eine Nachricht, die an eine moderierte Verteilergruppe gesendet wurde, auf einem Exchange 2007-Hub-Transport-Server erweitert wird, umgeht die Nachricht die Moderation und wird an alle Mitglieder der Verteilergruppe zugestellt. Wenn Sie Exchange 2007-Hub-Transport-Server in Ihrer Exchange-Organisation verwenden, müssen Sie einen Exchange Server&nbsp;2013-Postfachserver als Server für die Aufgliederung für moderierte Verteilergruppen festlegen. Auf diese Weise wird sichergestellt, dass alle an die Verteilergruppe gesendeten Nachrichten moderiert werden.



Zurück zum Seitenanfang

## Benötigen Sie weitere Informationen?

[Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md)

[Kurzübersicht über die Exchange-Verwaltungsshell für Exchange 2013](exchange-management-shell-quick-reference-for-exchange-2013-exchange-2013-help.md)

[Exchange Online PowerShell](https://technet.microsoft.com/de-de/library/jj200677\(v=exchg.150\))

