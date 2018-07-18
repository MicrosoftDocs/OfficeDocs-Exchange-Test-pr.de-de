---
title: 'Messaging-Datensatzverwaltung: Exchange Online Help'
TOCTitle: Messaging-Datensatzverwaltung
ms:assetid: 0dd92e9c-881e-43c0-9bbf-f41fdc9dfd87
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335093(v=EXCHG.150)
ms:contentKeyID: 50475070
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Messaging-Datensatzverwaltung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-02-01_

Benutzer senden und empfangen jeden Tag E-Mails. Wenn diese große Menge an E-Mails, die jeden Tag verfasst und empfangen werden, nicht verwaltet wird, kann dies Benutzer belasten, ihre Produktivität beeinträchtigen und zu Risiken für Ihre Organisation führen. Daher ist die Verwaltung des E-Mail-Lebenszyklus eine entscheidende Komponente für die meisten Organisationen.

Messaging-Datensatzverwaltung (Messaging Records Management, MRM) ist die Technologie für die Verwaltung von Datensätzen in Exchange Server 2013 und Exchange Online, die Organisationen dabei unterstützt, den E-Mail-Lebenszyklus zu verwalten und die mit E-Mail einhergehenden rechtlichen Risiken zu verringern. Die Bereitstellung von MRM kann Ihrer Organisation auf verschiedene Arten helfen:

  - **Erfüllen von Unternehmensanforderungen**   Abhängig von den Richtlinien für Nachrichten in Ihrer Organisation müssen Sie möglicherweise wichtige E-Mails für einen bestimmten Zeitraum aufbewahren. Beispielsweise kann das Postfach eines Benutzers wichtige Nachrichten im Zusammenhang mit der Unternehmensstrategie, Transaktionen, Produktentwicklungen oder Kundeninteraktionen enthalten.

  - **Erfüllen rechtlicher und behördlicher Auflagen**   Für viele Organisationen gelten rechtliche oder behördliche Auflagen, aufgrund derer Nachrichten für einen bestimmten Zeitraum gespeichert und nach dieser Frist gelöscht werden müssen. Wenn Nachrichten länger als erforderlich gespeichert werden, können die rechtlichen oder finanziellen Risiken einer Organisation steigen.

  - **Steigern der Benutzerproduktivität**   Wenn das ständig steigende Volumen an E-Mails in den Postfächern Ihrer Benutzer nicht verwaltet wird, kann sich dies auch auf die Benutzerproduktivität auswirken. Auch wenn beispielsweise Newsletterabonnements und automatisierte Benachrichtigungen beim Empfang einen informativen Nutzen haben, werden sie nach dem Lesen möglicherweise nicht von den Benutzern entfernt (oder sie werden erst gar nicht gelesen). Viele dieser Arten von Nachrichten sollten nur einige Tage aufbewahrt werden. Wenn Sie solche Nachrichten mithilfe von MRM entfernen, können Sie den Informationsdatenmüll in den Postfächern der Benutzer reduzieren und dadurch deren Produktivität steigern.

  - **Verbessern der Speicherverwaltung**   Aufgrund ihrer Erfahrungen mit kostenlosen E-Mail-Diensten im privaten Bereich gehen viele Benutzer davon aus, dass alte Nachrichten für eine lange Zeit aufbewahrt werden können bzw. nie gelöscht werden müssen. Das Aufbewahren großer Postfächer wird zunehmend zur Norm, und Benutzer sollten nicht gezwungen werden, ihre Arbeitsgewohnheiten aufgrund von strikten Postfachkontingenten zu ändern. Wenn Nachrichten länger aufbewahrt werden als aus geschäftlicher oder rechtlicher Sicht erforderlich, steigen jedoch auch die Speicherkosten.

Mit MRM können Sie die Richtlinie für die Datensatzverwaltung implementieren, mit der die Anforderungen Ihrer Organisation am besten erfüllt werden. Wenn Sie sich mit MRM und Compliance-Archiven vertraut machen, sind Sie in der Lage, Ihre Ziele beim Verwalten des Postfachspeichers zu erreichen und Vorschriften im Hinblick auf die Nachrichtenaufbewahrung einzuhalten.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit MRM gibt? Weitere Informationen finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## MRM in Exchange Server 2013 und Exchange Online

In Exchange Server 2013 und Exchange Online wird MRM durch die Verwendung von Aufbewahrungstags und Aufbewahrungsrichtlinien erzielt. Aufbewahrungstags werden verwendet, um Aufbewahrungseinstellungen auf ein vollständiges Postfach und standardmäßige Postfachordner wie "Posteingang" und "Gelöschte Elemente" anzuwenden. Sie können außerdem Aufbewahrungstags erstellen und bereitstellen, die Benutzer mit Outlook 2010 und höher sowie Outlook Web App-Benutzer auf Ordner oder einzelne Nachrichten anwenden können. Nach der Erstellung fügen Sie Aufbewahrungstags zu einer Aufbewahrungsrichtlinie hinzu und wenden dann die Richtlinie auf Benutzer an. Der Assistent für verwaltete Ordner verarbeitet Postfächer und wendet Aufbewahrungseinstellungen in der Aufbewahrungsrichtlinie des Benutzers an. Weitere Informationen zu Aufbewahrungsrichtlinien finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md).

Wenn eine Nachricht den im jeweiligen Aufbewahrungstag angegebenen Aufbewahrungszeitraum erreicht, führt der Assistent für verwaltete Ordner die im Tag festgelegte Aufbewahrungsaktion aus. Nachrichten können dann endgültig gelöscht werden oder wiederherstellbar bleiben. Wenn für den Benutzer ein Archiv bereitgestellt wurde, können Sie mit Aufbewahrungstags auch Elemente in das Compliance-Archiv des Benutzers verschieben.

## MRM-Strategien

Mithilfe von Aufbewahrungsrichtlinien können Sie grundlegende Einstellungen für die Aufbewahrung von Nachrichten für ein vollständiges Postfach und für bestimmte Standardordner durchsetzen. Es gibt verschiedene Strategien für die MRM-Bereitstellung. Die gängigsten werden im Folgenden dargestellt:

**Alle Nachrichten nach einem angegebenen Zeitraum entfernen**   Bei dieser Strategie implementieren Sie eine einzelne MRM-Richtlinie, die alle Nachrichten nach einem bestimmten Zeitraum entfernt. Bei dieser Strategie erfolgt keine Klassifizierung der Nachrichten. Zur Implementierung dieser Richtlinie können Sie ein einziges Standardrichtlinientag für das Postfach erstellen. Damit wird jedoch nicht sichergestellt, dass die Nachrichten für den angegebenen Zeitraum aufbewahrt werden. Benutzer können weiterhin Nachrichten löschen, bevor die Aufbewahrungsfrist erreicht wurde.

**Nachrichten in Archivierungspostfächer verschieben**   Bei dieser Strategie implementieren Sie MRM-Richtlinien, die Elemente zum Archivierungspostfach des Benutzers verschieben. Ein Archivpostfach bietet zusätzlichen Speicherplatz, sodass Benutzer ältere Inhalte oder Inhalte, auf die selten zugegriffen wird, aufbewahren können. Aufbewahrungstags, mit denen Elemente verschoben werden, werden auch als *Archivrichtlinien* bezeichnet. Zum Verschieben oder Löschen von Elementen in derselben Aufbewahrungsrichtlinie können Sie ein Standardrichtlinientag und persönliche Tags bzw. ein Standardrichtlinientag, Aufbewahrungsrichtlinientags und persönliche Tags kombinieren. Weitere Informationen zu Archivrichtlinien finden Sie unter:

  - **Exchange Server 2013:**  [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md)

  - **Exchange Online:**  [Archivieren von Postfächern in Exchange Online](https://technet.microsoft.com/de-de/library/dn922147\(v=exchg.150\))


> [!NOTE]
> In einer Exchange-Hybridbereitstellung können Sie ein cloudbasiertes Archivpostfach für ein lokales primäres Postfach aktiveren. Beim Zuweisen einer Archivrichtlinie zu einem lokalen Postfach werden die Elemente zum cloudbasierten Archiv verschoben. Wenn ein Element in das Archivpostfach verschoben wird, wird im lokalen Postfach keine Kopie davon beibehalten. Wenn das lokale Postfach ausgesetzt wird, werden Elemente anhand einer Archivrichtlinie weiterhin in das cloudbasierte Archivpostfach verschoben, in dem sie so lange aufbewahrt werden, wie dies durch die In-Situ-Speicherung festgelegt wurde.



**Nachrichten basierend auf dem Order entfernen, in dem sie sich befinden**   In dieser Stratege implementieren Sie MRM-Richtlinien auf Grundlage des E-Mail-Speicherorts. Beispielsweise können Sie angeben, dass Nachrichten im Posteingang für ein Jahr aufbewahrt werden, Nachrichten im Ordner für Junk-E-Mails aber nur 60 Tage. Zur Implementierung dieser Richtlinie können Sie eine Kombination aus Aufbewahrungsrichtlinientags für jeden Standardordner, den Sie konfigurieren möchten, und einem Standardrichtlinientag für das gesamte Postfach verwenden. Das Standardrichtlinientag gilt für alle benutzerdefinierten Ordner und alle Standardordner, auf die keine Aufbewahrungsrichtlinientags angewendet wurden.


> [!NOTE]
> In Exchange&nbsp;2013 können Aufbewahrungsrichtlinientags für die Ordner "Kalender" und "Aufgaben" erstellt werden. Wenn Sie für Elemente in diesen oder anderen Standardordnern kein Aufbewahrungslimit festlegen möchten, können Sie für den jeweiligen Standardordner ein deaktiviertes Aufbewahrungstag erstellen.



**Benutzer dürfen Nachrichten klassifizieren**   Bei dieser Strategie implementieren Sie MRM-Richtlinien, die eine grundlegende Aufbewahrungseinstellung für alle Nachrichten umfassen, erlauben Benutzern jedoch, Nachrichten auf Grundlage von Geschäfts oder rechtlichen Anforderungen zu klassifizieren. In diesem Fall werden die Benutzer zu einem wichtigen Bestandteil in Ihrer Strategie für die Datensatzverwaltung. Häufig wissen sie am besten, wie lange eine Nachricht aufbewahrt werden sollte.

Benutzer können unterschiedliche Aufbewahrungseinstellungen auf Nachrichten anwenden, die für einen längeren oder kürzeren Zeitraum aufbewahrt werden müssen. Sie können diese Richtlinie mit einer Kombination der folgenden Tags implementieren:

  - Ein Standardrichtlinientag für das Postfach

  - Persönliche Tags, die Benutzer auf benutzerdefinierte Ordner oder einzelne Nachrichten anwenden können

  - (Optional) Zusätzliche Aufbewahrungsrichtlinientags, um für Elemente in bestimmten Standardordnern ein Aufbewahrungslimit festzulegen

Beispielsweise können Sie eine Aufbewahrungsrichtlinie mit persönlichen Tags verwenden, die einen kürzeren Aufbewahrungszeitraum festlegen (z. B. 2 Tage, 1 Woche oder 1 Monat), sowie mit persönlichen Tags, in denen ein längerer Aufbewahrungszeitraum (z. B. 1 Jahr, 2 Jahre, 5 Jahre) definiert ist. Die Benutzer können persönliche Tags mit kürzeren Aufbewahrungszeiträumen auf Elemente wie Newsletterabonnements anwenden, die innerhalb von Tagen nach dem Empfang ihren Nutzen verlieren. Mithilfe von Tags mit längeren Zeiträumen können dagegen Elemente aufbewahrt werden, die einen großen geschäftlichen Nutzen aufweisen. Sie können den Vorgang auch mithilfe von Posteingangsregeln in Outlook automatisieren, um ein persönliches Tag auf Nachrichten anzuwenden, die die Regelbedingungen erfüllen.

**Nachrichten für eDiscovery-Zwecke speichern**   Bei dieser Strategie implementieren Sie MRM-Richtlinien, die Nachrichten nach einem angegebenen Zeitraum aus Postfächern entfernen, sie jedoch auch im Ordner „Wiederherstellbare Elemente\&quot; für [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)-Zwecke aufbewahren, selbst wenn die Nachrichten durch den Benutzer oder einen anderen Prozess gelöscht werden.

Sie können diese Anforderung erfüllen, indem Sie eine Kombination aus Aufbewahrungsrichtlinien und [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md) oder Beweissicherungsverfahren verwenden. Über Aufbewahrungsrichtlinien werden Nachrichten nach dem angegebenen Zeitraum aus dem Postfach entfernt. Mit einem zeitbasierten In-Situ-Speicher oder Beweissicherungsverfahren werden Nachrichten für diesen Zeitraum auch dann beibehalten, wenn sie gelöscht oder geändert wurden. Beispiel: Um Nachrichten für sieben Jahre aufzubewahren, können Sie eine Aufbewahrungsrichtlinie mit einem DPT erstellen, über das Nachrichten nach sieben Jahren gelöscht werden. Gleichzeitig erstellen Sie einen In-Situ-Speicher, in dem Nachrichten sieben Jahre aufbewahrt werden. Nachrichten, die von den Benutzern nicht entfernt werden, werden nach sieben Jahren gelöscht, und Nachrichten, die von den Benutzern vor dieser Frist gelöscht werden, werden für sieben Jahre im Ordner "Wiederherstellbare Elemente" gespeichert. Weitere Informationen zu diesem Ordner finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

Optional können Sie es Benutzern mit Aufbewahrungsrichtlinientags und persönlichen Tags ermöglichen, ihre Postfächer zu bereinigen. Jedoch bleiben die gelöschten Nachrichten im In-Situ-Speicher und im Beweissicherungsverfahren erhalten, bis der Aufbewahrungszeitraum beendet ist.


> [!NOTE]
> Ein zeitbasierter In-Situ-Speicher oder ein Beweissicherungsverfahren ist mit der sogenannten <EM>rollierenden gesetzlichen Aufbewahrungspflicht</EM> in Exchange&nbsp;2010 vergleichbar (bitte beachten Sie, dass dies nicht der offizielle Begriff ist). Zur Implementierung der gesetzlichen Aufbewahrungspflicht wurde der Aufbewahrungszeitraum für gelöschte Elemente für eine Postfachdatenbank oder einzelne Postfächer konfiguriert. Bei der Aufbewahrung gelöschter Elemente werden gelöschte und geänderte Elemente jedoch basierend auf dem Löschdatum beibehalten. Der In-Situ-Speicher und das Beweissicherungsverfahren bewahren Elemente basierend auf dem Datum des Empfangs oder der Erstellung auf. Dadurch wird sichergestellt, dass Nachrichten mindestens für den angegebenen Zeitraum beibehalten werden.



## Weitere Informationen

[Terminologie für die Messaging-Datensatzverwaltung in Exchange 2013](messaging-records-management-terminology-in-exchange-2013-exchange-2013-help.md)

[Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md)

