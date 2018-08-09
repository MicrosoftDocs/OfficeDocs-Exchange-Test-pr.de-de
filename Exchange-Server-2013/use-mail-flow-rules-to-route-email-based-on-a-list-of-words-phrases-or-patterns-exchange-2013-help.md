---
title: 'Nach.flussregeln z. Routen von E-Mails bas. auf Wörtern, Begriffen o. Mustern'
TOCTitle: Verwenden von Nachrichtenflussregeln zum Routen von E-Mails basierend auf einer Liste von Wörtern, Begriffen oder Mustern
ms:assetid: 4c5bee1b-58b5-4152-baef-86fa103050ae
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn951131(v=EXCHG.150)
ms:contentKeyID: 65218636
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden von Nachrichtenflussregeln zum Routen von E-Mails basierend auf einer Liste von Wörtern, Begriffen oder Mustern

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-10-30_

Damit Benutzer die E-Mail-Richtlinien Ihrer Organisation einhalten können, können Sie Exchange-Transportregeln verwenden, die festlegen, wie E-Mails mit bestimmten Wörtern oder Mustern weitergeleitet werden. Für eine kurze Liste von Wörtern oder Ausdrücken können Sie das Exchange-Verwaltungskonsole verwenden. Für eine längere Liste, müssen Sie ggf. das Exchange-Modul für Windows PowerShell verwenden, um die Liste aus einer Datei zu laden.

  - Beispiel 1: Verwenden einer kurzen Liste mit nicht zulässigen Wörtern

  - Beispiel 2: Verwenden einer langen Liste mit nicht zulässigen Wörtern

Wenn Ihre Organisation Verhinderung von Datenverlust (Data Loss Prevention, DLP) verwendet, finden Sie unter [Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md) weitere Optionen für die Identifizierung und das Routing von E-Mails mit vertraulichen Informationen.

## Beispiel 1: Verwenden einer kurzen Liste mit nicht zulässigen Wörtern

Wenn die Liste der Wörter oder Ausdrücke kurz ist, können Sie eine Regel mithilfe des Exchange-Verwaltungskonsole erstellen. Wenn Sie z. B. sicherstellen möchten, dass keine E-Mails mit Schimpfwörtern oder mit falscher Schreibweise Ihres Unternehmensnamens, mit internen Akronymen oder Produktnamen gesendet werden, können Sie eine Regel erstellen, mit der solche Nachrichten blockiert werden und eine Benachrichtigung an den Absender geschickt wird. Beachten Sie, dass die Groß-/Kleinschreibung bei Wörtern, Ausdrücken und Mustern nicht berücksichtigt wird.

In diesem Beispiel werden Nachrichten mit häufig vorkommenden Tippfehlern blockiert.

![Regel, die das Blockieren einer Nachricht basierend auf Textmustern anzeigt.](images/Dn951131.a8489cbb-be59-4890-ae30-1431703eeb88(EXCHG.150).png "Regel, die das Blockieren einer Nachricht basierend auf Textmustern anzeigt.")

## Beispiel 2: Verwenden einer langen Liste mit nicht zulässigen Wörtern

Wenn die Liste der Wörter, Sätze oder Muster lang ist, können Sie sie in einer Textdatei so platzieren, dass in einer Zeile nur ein Wort, Ausdruck oder Muster steht. Verwenden Sie das Exchange für Windows PowerShell, um die Liste der Schlüsselwörter in eine Variable zu laden, eine Transportregel zu erstellen, und die Variable mit den Schlüsselwörtern der Bedingung für die Transportregel zuzuordnen. Das folgende Skript verwendet beispielsweise eine Liste von Rechtschreibfehlern aus einer Datei namens „misspelled\_companyname.csv“.

    $keywords=Import-Content  .\misspelled_companyname.txt
    New-TransportRule -Name "Block messages with unacceptable words" -SubjectOrBodyContainsWords $keywords -SentToScope "NotInOrganization" -RejectMessageReasonText "Do not use internal acronyms, product names, or misspellings in external communications."

## Verwenden von Ausdrücken und Mustern in der Textdatei

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


Diese Datei enthält beispielsweise die häufigsten falschen Schreibweisen von Microsoft.

    [mn]sft
    [mn]icrosft
    [mn]icro soft
    [mn].crosoft

Informationen zum Angeben von Mustern mithilfe von regulären Ausdrücken finden Sie unter [Referenz zu regulären Ausdrücken](https://go.microsoft.com/fwlink/p/?linkid=532394).

