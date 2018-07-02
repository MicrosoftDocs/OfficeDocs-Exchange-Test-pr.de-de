---
title: 'Standardszenarien für Anlagensperre: Exchange Online Help'
TOCTitle: Standardszenarien für Anlagensperre
ms:assetid: 5c576439-d55b-4c7f-90ed-a7f72cbb16c2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn950026(v=EXCHG.150)
ms:contentKeyID: 65207668
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Standardszenarien für Anlagensperre

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-02-23_

In Ihrer Organisation müssen möglicherweise bestimmte Arten von Nachrichten blockiert oder abgelehnt werden, um rechtliche Anforderungen zu erfüllen, Vorschriften einzuhalten oder einen bestimmten Geschäftsworkflow zu implementieren. Nachfolgend finden Sie einige Beispiele für gängige Szenarien beim Blockieren aller Anlagen, die Sie mithilfe von Transportregeln in Exchange einrichten können:

  -  
    Example 1: Block messages with attachments, and notify the sender

  -  
    Example 2: Notify intended recipients when an inbound message is blocked

  -  
    Example 3: Modify the subject line for notifications

  -  
    Example 4: Apply a rule with a time limit

Weitere Beispiele für das Blockieren bestimmter Anlagen finden Sie unter:

  - [Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md) (Exchange Server 2013)

  - [Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\)) (Exchange Online, Exchange Online Protection)

Der Schadsoftwarefilter enthält einen Filter für gängige Anlagentypen. Klicken Sie in der Exchange-Verwaltungskonsole (EAC) auf **Schutz**, und klicken Sie dann auf **Neu** (![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")), um Filter hinzuzufügen. Navigieren Sie im Exchange Online-Portal zu **Schutz**, und wählen Sie dann **Schadsoftwarefilter** aus.

Führen Sie die folgenden Aktionen durch, um mit dem Implementieren eines dieser Szenarien zum Blockieren bestimmter Nachrichtentypen zu beginnen:

1.  Melden Sie sich bei der Exchange-Verwaltungskonsole an.

2.  Wechseln Sie zu **Nachrichtenfluss** \>**Regeln**.

3.  Klicken Sie auf **Neu** (![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")), und wählen Sie dann **Neue Regel erstellen** aus.

4.  Geben Sie im Feld **Name** einen Namen für die Regel an, und klicken Sie dann auf **Weitere Optionen**.

5.  Wählen Sie die gewünschten Bedingungen und Aktionen aus.

**Hinweis:**  In der Exchange-Verwaltungskonsole (EAC) beträgt die kleinste Größe von Anlagen, die Sie eingeben können, 1 Kilobyte. Hiermit sollten die meisten Anlagen erkannt werden. Wenn Sie jedoch jede Anlage beliebiger Größe erkennen möchten, müssen Sie PowerShell verwenden, um die Analgengröße auf 1 Byte zu erhöhen, nachdem Sie die Regel in der Exchange-Verwaltungskonsole erstellt haben. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online Protection herstellen, können Sie unter [Verbinden mit PowerShell in Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=627290) nachlesen.

Ersetzen Sie *\<Rule Name\>* durch den Namen der vorhandenen Regel, und führen Sie den folgenden Befehl aus, um die Größe von Anlagen auf 1 Byte festzulegen:

    Set-TransportRule -Identity "<Rule Name>" -AttachmentSizeOver 1B

Nachdem Sie die Größe von Anlagen auf 1 Byte angepasst haben, wird als Wert für die Regel in der Exchange-Verwaltungskonsole **0,00 KB** angezeigt.

## Beispiel 1: Blockieren von Nachrichten mit Anlagen und Benachrichtigen des Absenders

Wenn Sie nicht möchten, dass Personen in Ihrer Organisation Anlagen senden oder empfangen, können Sie eine Transportregel einrichten, mit der alle Nachrichten mit Anlagen blockiert werden.

In diesem Beispiel werden alle Nachrichten mit Anlagen blockiert, die an die oder aus der Organisation gesendet wurden.

![Regel, die alle Anlagen blockiert](images/Dn950026.38094183-166f-4ba5-a9cf-242e7d0f4e04(EXCHG.150).png "Regel, die alle Anlagen blockiert")

Wenn Sie die Nachricht lediglich blockieren möchten, müssen Sie möglicherweise die Verarbeitung der Regel beenden, sobald diese Regel erfüllt ist. Scrollen Sie im Dialogfeld „Regel\&quot; nach unten, und aktivieren Sie das Kontrollkästchen **Verarbeitung weiterer Regeln beenden**.

## Beispiel 2: Benachrichtigen der vorgesehenen Empfänger, wenn eine eingehende Nachricht blockiert wird

Wenn Sie eine Nachricht ablehnen möchten, den vorgesehenen Empfänger jedoch darüber in Kenntnis setzen möchten, können Sie hierzu die Aktion **Den Empfänger benachrichtigen** verwenden.

Sie können Platzhalter in der Benachrichtigung verwenden, sodass diese Informationen über die ursprüngliche Nachricht enthält. Die Platzhalter müssen in zwei Prozentzeichen (%%) eingeschlossen sein. Wenn die Benachrichtigungs-E-Mail gesendet wird, werden die Platzhalter mit Informationen aus der ursprünglichen Nachricht ersetzt. Sie können auch einfachen HTML-Code in der Nachricht verwenden, z. B.\<br\>, \<b\>, \<i\> und \<img\>.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Art der Information</strong></p></td>
<td><p><strong>Platzhalter</strong></p></td>
</tr>
<tr class="even">
<td><p>Der Absender der Nachricht.</p></td>
<td><p>%%From%%</p></td>
</tr>
<tr class="odd">
<td><p>Die im Feld „An&amp;quot; aufgeführten Empfänger.</p></td>
<td><p>%%To%%</p></td>
</tr>
<tr class="even">
<td><p>Die im Feld „Cc&amp;quot; aufgeführten Empfänger.</p></td>
<td><p>%%Cc%%</p></td>
</tr>
<tr class="odd">
<td><p>Betreff der ursprünglichen Nachricht.</p></td>
<td><p>%%Subject%%</p></td>
</tr>
<tr class="even">
<td><p>Kopfzeilen aus der ursprünglichen Nachricht. Dies ist mit der Liste von Kopfzeilen in einer Benachrichtigung über den Zustellungsstatus (Delivery Status Notification, DSN) vergleichbar, die für die ursprüngliche Nachricht generiert wurde.</p></td>
<td><p>%%Headers%%</p></td>
</tr>
<tr class="odd">
<td><p>Datum, an dem die ursprüngliche Nachricht gesendet wurde.</p></td>
<td><p>%%MessageDate%%</p></td>
</tr>
</tbody>
</table>


In diesem Beispiel werden alle Nachrichten mit Anlagen blockiert, die an Personen innerhalb Ihrer Organisation gesendet wurden, und eine Benachrichtigung an die Empfänger gesendet.

![Regel, die Empfänger benachrichtigt, wenn eine eingehende Nachricht blockiert wird](images/Dn950026.f9a14733-d68a-4528-a736-206325881c47(EXCHG.150).png "Regel, die Empfänger benachrichtigt, wenn eine eingehende Nachricht blockiert wird")

## Beispiel 3: Ändern der Betreffzeile für Benachrichtigungen

Wenn eine Benachrichtigung an den Empfänger gesendet wird, entspricht die Betreffzeile dem Betreff der ursprünglichen Nachricht. Wenn Sie den Betreff ändern möchten, damit dieser für den Empfänger klarer ist, müssen Sie zwei Transportregeln verwenden:

  - Die erste Regel fügt das Wort „Unzustellbar\&quot; an den Anfang des Betreffs von Nachrichten mit Anlagen.

  - Die zweite Regel blockiert die Nachricht und sendet eine Benachrichtigung an den Absender mit dem neuen Betreff der ursprünglichen Nachricht.


> [!IMPORTANT]
> Beide Regeln müssen über die gleichen Bedingungen verfügen. Regeln werden der Reihe nach verarbeitet, sodass die erste Regel das Wort „Unzustellbar&amp;quot; hinzufügt, und die zweite Regel die Nachricht blockiert und eine Benachrichtigung an den Empfänger sendet.



Die erste Regel könnte folgendermaßen aussehen, wenn Sie das Wort „Unzustellbar\&quot; zum Betreff hinzufügen möchten:

![Regel, mit der Nachrichten mit Anlagen „Unzustellbar\&quot; vorangestellt wird](images/Dn950026.2552b0bd-c69d-48b4-9e69-267fcaf20e70(EXCHG.150).png "Regel, mit der Nachrichten mit Anlagen „Unzustellbar&quot; vorangestellt wird")

Und die zweite Regel führt das Blockieren und die Benachrichtigung aus (die gleiche Regel aus Beispiel 2):

![Regel, die Empfänger benachrichtigt, wenn eine eingehende Nachricht blockiert wird](images/Dn950026.f9a14733-d68a-4528-a736-206325881c47(EXCHG.150).png "Regel, die Empfänger benachrichtigt, wenn eine eingehende Nachricht blockiert wird")

## Beispiel 4: Anwenden einer Regel mit einer Zeitbegrenzung

Bei einem Schadsoftwareausbruch müssen Sie ggf. eine Regel mit einer Zeitbegrenzung anwenden, damit Anlagen vorübergehend blockiert werden. Die folgende Regel verfügt beispielsweise über einen Start- und Endzeitpunkt:

![Regel mit einem Zeitlimit](images/Dn950026.bdc8c4d8-72fa-4c5b-97f2-5fe76d50e643(EXCHG.150).png "Regel mit einem Zeitlimit")

## Siehe auch


[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))  


[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)  
[Nachrichtenflussregeln (Transportregeln) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/dn271424\(v=exchg.150\))

