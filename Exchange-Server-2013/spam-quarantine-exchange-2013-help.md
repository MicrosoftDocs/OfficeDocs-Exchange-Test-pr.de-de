---
title: 'Quarantänepostfach für Spam: Exchange 2013 Help'
TOCTitle: Quarantänepostfach für Spam
ms:assetid: 4535496f-de6a-43df-8e53-c9a97f65cccc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997692(v=EXCHG.150)
ms:contentKeyID: 50475564
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Quarantänepostfach für Spam

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

Viele Unternehmen sind durch gesetzliche Bestimmungen oder Vorschriften verpflichtet, alle rechtlich relevanten E-Mail-Nachrichten aufzubewahren oder zuzustellen. In Microsoft Exchange Server 2013 ist die Spamquarantäne eine Funktion des Inhaltsfilter-Agents, durch die das Risiko reduziert wird, dass legitime Nachrichten verloren gehen. Die Spamquarantäne stellt einen temporären Speicherort für Nachrichten bereit, die als Spam erkannt wurden und nicht an ein Benutzerpostfach in der Organisation gesendet werden sollen.

Nachrichten, die vom Inhaltsfilter-Agent als Spam erkannt werden, werden in einen Unzustellbarkeitsbericht eingeschlossen und an ein Spam-Quarantänepostfach innerhalb der Organisation übermittelt. Sie können Nachrichten, die an das Spam-Quarantänepostfach übermittelt werden, verwalten und geeignete Maßnahmen ergreifen. Sie können Nachrichten z. B. löschen oder Nachrichten, die durch den Antispamfilter fälschlicherweise als positives Ergebnis gekennzeichnet wurden, an den ursprünglichen Empfänger weiterleiten. Darüber hinaus können Sie das Spam-Quarantänepostfach so konfigurieren, dass Nachrichten nach einem festgelegten Zeitraum automatisch gelöscht werden.

**Inhalt**

Spam confidence level

Spam quarantine

## SCL-Bewertung

Wenn ein externer Benutzer E-Mail-Nachrichten an einen Exchange-Server sendet, auf dem die Antispamfunktionen ausgeführt werden, werten die Antispamfunktionen Merkmale der Nachrichten kumulativ aus und gehen dann wie folgt vor:

  - Nachrichten, bei denen es sich vermutlich um Spam handelt, werden herausgefiltert.

  - Basierend auf der Wahrscheinlichkeit, dass es sich um Spam handelt, wird den Nachrichten eine Bewertung zugewiesen. Diese Bewertung wird zusammen mit der Nachricht als Nachrichteneigenschaft gespeichert, die als SCL-Bewertung (Spam Confidence Level) bezeichnet wird.

Die Spamquarantäne verwendet die SCL-Bewertung, um die Wahrscheinlichkeit zu bestimmen, dass es sich bei einer E-Mail um Spam handelt. Die SCL-Bewertung ist ein numerischer Wert zwischen 0 und 9, wobei 0 als geringe Wahrscheinlichkeit und 9 als hohe Wahrscheinlichkeit für Spam gilt.

Sie können nun festlegen, dass E-Mail-Nachrichten mit einer bestimmten SCL-Bewertung gelöscht, abgelehnt oder in das Quarantänepostfach verschoben werden. Die Bewertung, die eine dieser Aktionen auslöst, wird als *SCL-Schwellenwert zum Isolieren* bezeichnet. Im Rahmen der Inhaltsfilterung können Sie den Inhaltsfilter-Agent so konfigurieren, dass er seine Aktionen am SCL-Schwellenwert zum Isolieren ausrichtet. Sie können die folgenden Bedingungen festlegen:

  - Der SCL-Schwellenwert zum Löschen ist auf 8 festgelegt.

  - Der SCL-Schwellenwert zum Zurückweisen ist auf 7 festgelegt.

  - Der SCL-Schwellenwert zum Isolieren ist auf 6 festgelegt.

  - Der SCL-Schwellenwert des Junk-E-Mail-Ordners wird auf 5 festgelegt.

Basierend auf den vorstehenden SCL-Schwellenwerten werden alle E-Mail-Nachrichten mit dem SCL-Wert 6 an das Spam-Quarantänepostfach übermittelt.

Weitere Informationen finden Sie unter [Verwalten der Inhaltsfilterung](manage-content-filtering-exchange-2013-help.md).

Zurück zum Seitenanfang

## Quarantänepostfach für Spam

Wenn Nachrichten von dem Exchange-Server empfangen werden, auf dem die standardmäßigen Antispam-Agents ausgeführt werden, wird der Inhaltsfilter wie folgt angewendet:

  - Wenn die SCL-Bewertung größer oder gleich dem SCL-Schwellenwert zum Isolieren, jedoch kleiner als einer der SCL-Schwellenwerte zum Löschen oder Zurückweisen ist, wird die Nachricht an das Spam-Quarantänepostfach übermittelt.

  - Wenn die SCL-Bewertung niedriger ist als der Schwellenwert zum Isolieren, wird die Nachricht an das Postfach des Empfängers zugestellt.

Der Nachrichtenadministrator verwendet Microsoft Outlook, um das Spam-Quarantänepostfach im Hinblick auf Nachrichten zu überwachen, die fälschlicherweise als Spam bewertet wurden. Wenn so eine Nachricht gefunden wird, kann der Administrator die Nachricht an das Postfach des Empfängers senden.

Der Nachrichtenadministrator sollte die Antispamstempel überprüfen, wenn eine der folgenden Bedingungen zutrifft:

  - Es werden zu viele Nachrichten fälschlicherweise als Spam herausgefiltert und in das Spam-Quarantänepostfach verschoben.

  - Es werden zu wenig Spamnachrichten zurückgewiesen oder gelöscht.

Weitere Informationen finden Sie unter [Antispamstempel](anti-spam-stamps-exchange-2013-help.md).

Anschließend können Sie die SCL-Einstellungen anpassen, damit Spam, der die Organisation erreicht, präziser herausgefiltert wird. Weitere Informationen finden Sie unter [SCL-Schwellenwert](spam-confidence-level-threshold-exchange-2013-help.md).

Führen Sie die folgenden Schritte aus, um das Quarantänepostfach für Spam zu konfigurieren:

1.  Überprüfen Sie, ob die Inhaltsfilterung aktiviert ist.

2.  Erstellen Sie ein dediziertes Postfach für die Spamquarantäne.

3.  Geben Sie das Quarantänepostfach für Spam an.

4.  Konfigurieren Sie den SCL-Isolierungsschwellenwert.

5.  Verwalten Sie das Spam-Quarantänepostfach.

6.  Passen Sie den SCL-Isolierungsschwellenwert nach Bedarf an.

Ausführliche Anweisungen finden Sie unter [Konfigurieren eines Spamquarantänepostfachs](configure-a-spam-quarantine-mailbox-exchange-2013-help.md).

Zurück zum Seitenanfang

