---
title: 'Bewährte Meth. für Konfig. von Nachrichtenflussregeln: Exchange Online-Hilfe'
TOCTitle: Bewährte Methoden für die Konfiguration von Nachrichtenflussregeln
ms:assetid: abd863c3-c0ce-42f3-9470-a573adc3cbba
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn960147(v=EXCHG.150)
ms:contentKeyID: 65234660
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Bewährte Methoden für die Konfiguration von Nachrichtenflussregeln

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Befolgen Sie diese empfohlenen bewährten Methoden für Exchange-Transportregeln, um allgemeine Konfigurationsfehler zu vermeiden. Jede Empfehlung enthält einen Link zum Thema mit einem Beispiel und schrittweisen Anleitungen.

## Testen der Regeln

Führen Sie gründliche Test durch, um sicherzustellen, dass keine unerwarteten Ereignisse in Bezug auf E-Mails auftreten und die Regeln den geschäftlichen, rechtlichen und Complianceabsichten entsprechen. Es gibt viele Möglichkeiten, und Regeln können miteinander interagieren. Deshalb ist es wichtig zu testen, ob die erwarteten Nachrichten gleichzeitig einer Regel entsprechen und nicht entsprechen können, wenn eine Regel unbeabsichtigt zu allgemein definiert ist. Alle Möglichkeiten zum Testen von Regeln finden Sie unter [Testen einer Nachrichtenflussregel](test-a-mail-flow-rule-exchange-2013-help.md).

## Regelbereich

Stellen Sie sicher, dass die Regel nur auf vorgesehene Nachrichten angewendet wird. Beispiel:

  - **Schränken Sie eine Regel auf Nachrichten ein, die entweder an die Organisation oder aus der Organisation gesendet werden.**
    
    Standardmäßig wird eine neue Regel auf Nachrichten angewendet, die entweder von Personen in der Organisation gesendet oder empfangen werden. Wenn die Regel nur auf eine Weise angewendet werden soll, müssen Sie dies in den Bedingungen für diese Regel festlegen. Ein Beispiel finden Sie unter [Standardszenarien für Anlagensperre](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/common-attachment-blocking-scenarios).

  - **Einschränken einer Regel auf Grundlage der Absender- oder Empfängerdomäne**
    
    Standardmäßig wird eine neue Regel auf Nachrichten angewendet, die von einer beliebigen Domäne gesendet oder empfangen wird. In einigen Fällen möchten Sie ggf. eine Regel auf alle Domänen bis auf eine oder nur auf eine Domäne anwenden. Beispiele finden Sie unter [Erstellen einer domänen- oder benutzerbasierten Liste sicherer Absender oder gesperrter Absender mithilfe von Transportregeln](https://technet.microsoft.com/de-de/library/dn198251\(v=exchg.150\)).

Eine vollständige Liste aller Bedingungen und Ausnahmen, die für Transportregeln verfügbar sind, finden Sie unter:

  - [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\))

  - [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

  - [Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj919234\(v=exchg.150\))

## Fälle, in denen zwei Regeln notwendig sind

Manchmal benötigen Sie zwei Regeln, um eine gewünschte Aktion zu erzielen. Transportregeln werden der Reihe nach verarbeitet, sodass mehrere Regeln auf dieselbe Nachricht angewendet werden können. Wenn z. B. eine Aktion zum Blockieren der Nachricht dient, und eine weitere Aktion wie Kopieren der Nachricht an den Vorgesetzten des Absenders oder Ändern des Betreffs für die Benachrichtigungs-E-Mail angewendet werden soll, benötigen Sie zwei Regeln. Die erste Regel könnte dann das Kopieren der Nachricht an den Vorgesetzten des Absenders und das Ändern des Betreffs umfassen, und die zweite Regel das Blockieren der Nachricht.

Achten Sie darauf, dass die Bedingungen identisch sind, wenn Sie zwei Regeln dieser Art verwenden. Beispiele hierzu finden Sie im Beispiel 3 unter [Gängige Szenarien der Nachrichtengenehmigung](common-message-approval-scenarios-exchange-2013-help.md), im Beispiel 3 unter [Standardszenarien für Anlagensperre](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/common-attachment-blocking-scenarios) und unter [Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen](organization-wide-disclaimers-signatures-footers-or-headers-exchange-online-help.md).

## Führen Sie keine Wiederholung einer Aktion für alle E-Mails in einer Unterhaltung durch.

Eine Unterhaltung kann viele einzelne Nachrichten enthalten, und die Wiederholung der Aktion für jede Nachricht im Thread kann als lästig empfunden werden. Eine Aktion wie beispielsweise das Hinzufügen eines Haftungsausschlusses soll möglicherweise nur auf die erste Nachricht im Thread angewendet werden. Wenn dies der Fall ist, müssen Sie eine Ausnahme für Nachrichten hinzufügen, die den Text des Haftungsausschlusses bereits enthalten. Ein Beispiel finden Sie unter [Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen](organization-wide-disclaimers-signatures-footers-or-headers-exchange-online-help.md).

## Beenden der Regelverarbeitung

Manchmal ist es sinnvoll, die Verarbeitung einer Regel zu beenden, nachdem eine Regel erfüllt wurde. Wenn Sie z. B. eine Regel zum Blockieren von Nachrichten mit Anlage und eine zum Einfügen eines Haftungsausschlusses in Nachrichten haben, die einem Muster entsprechen, sollten Sie die Verarbeitung der Regel ggf. beenden, nachdem die Nachricht blockiert wurde. Es ist keine weitere Aktion erforderlich.

Aktivieren Sie zum Beenden der Regelverarbeitung innerhalb der Regel das Kontrollkästchen **Verarbeitung weiterer Regeln beenden**.

## Wenn bei einer Regel eine Übereinstimmung mit zahlreichen Schlüsselwörtern oder Mustern notwendig ist, laden Sie diese aus einer Datei.

Möglicherweise möchten Sie z. B. verhindern, dass E-Mails gesendet werden, die bestimmte unzulässige Wörter enthalten. Sie können eine Textdatei mit diesen Wörtern und Ausdrücken erstellen und dann mit Windows PowerShell eine Transportregel erstellen, die Nachrichten mit diesen blockiert.

Die Textdatei kann reguläre Ausdrücke für Muster enthalten. Für diese Ausdrücke wird nicht zwischen Groß- und Kleinschreibung unterschieden. Allgemeine reguläre Ausdrücke umfassen Folgendes:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Ausdruck</strong></p></td>
<td><p><strong>Übereinstimmungen</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>.</strong></p></td>
<td><p>Einen einzelnen Buchstaben</p></td>
</tr>
<tr class="odd">
<td><p><strong>*</strong></p></td>
<td><p>Alle zusätzlichen Zeichen</p></td>
</tr>
<tr class="even">
<td><p><strong>\d</strong></p></td>
<td><p>Eine Dezimalzahl</p></td>
</tr>
<tr class="odd">
<td><p>[<em>character_group</em>]</p></td>
<td><p>Ein einzelnes Zeichen in <em>character_group</em>.</p></td>
</tr>
</tbody>
</table>


Ein Beispiel für eine Textdatei mit regulären Ausdrücken und die im Exchange-Modul zu verwendenden Windows PowerShell-Befehle finden Sie unter [Verwenden von Nachrichtenflussregeln zum Routen von E-Mails basierend auf einer Liste von Wörtern, Begriffen oder Mustern](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/use-rules-to-route-email).

Informationen zum Angeben von Mustern mithilfe von regulären Ausdrücken finden Sie unter [Referenz zu regulären Ausdrücken](https://go.microsoft.com/fwlink/p/?linkid=532394).

