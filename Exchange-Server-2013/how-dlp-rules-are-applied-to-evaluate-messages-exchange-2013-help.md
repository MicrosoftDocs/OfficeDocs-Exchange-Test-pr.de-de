---
title: 'Anwenden von DLP-Regeln zur Auswertung von Nachrichten: Exchange 2013 Help'
TOCTitle: Anwenden von DLP-Regeln zur Auswertung von Nachrichten
ms:assetid: 1ac77020-26ff-410c-ab09-4f28a99d67a1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn329050(v=EXCHG.150)
ms:contentKeyID: 56269050
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anwenden von DLP-Regeln zur Auswertung von Nachrichten

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Sie können in Ihren Microsoft Exchange-Richtlinien zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) Regeln für vertrauliche Informationen einrichten, um ganz spezielle Daten in E-Mail-Nachrichten zu erkennen. In diesem Thema wird erklärt, wie diese Regeln angewendet werden und wie die Auswertung der Nachrichten erfolgt. Sie können Workflowunterbrechungen für Ihre E-Mail-Benutzer vermeiden und ein hohes Maß an Präzision bei Ihren DLP-Erkennungen erzielen, wenn Sie wissen, wie Ihre Regeln durchgesetzt werden. Wir verwenden hier als Beispiel die von Microsoft bereitgestellte Regel für Kreditkarteninformationen. Wenn Sie eine Transportregel oder DLP-Richtlinie aktivieren, vergleicht der Exchange-Transportregel-Agent sämtliche von Ihren Benutzern gesendeten Nachrichten mit den von Ihnen erstellten Regelsätzen.

## Halten Sie sich genau an Ihre Anforderungen

Nehmen wir einmal an, Sie müssen bei Kreditkarteninformationen in den Nachrichten tätig werden. Die Aktionen, die nach dem Auffinden der Informationen ergriffen werden, sollen in diesem Thema nicht weiter interessieren, aber Sie finden weitere Informationen dazu unter [Aktionen für Nachrichtenflussregeln in Exchange Online](https://technet.microsoft.com/de-de/library/jj919237\(v=exchg.150\)). Sie müssen mit der größtmöglichen Sicherheit gewährleisten, dass es sich bei den in einer Nachricht erkannten Daten tatsächlich um Kreditkartendaten handelt und nicht um etwas anderes, das eine völlig legitime Verwendung von Zahlengruppen ist, die lediglich Kreditkartendaten ähneln, also zum Beispiel ein Buchungscode oder eine Fahrzeug-Identifizierungsnummer. Um diese Anforderung zu erfüllen, müssen wir dafür sorgen, dass die folgenden Informationen als eine Kreditkarte klassifiziert werden sollen:

**    Margies Reisepläne,  
    Ich habe aktuelle Kreditkarteninformationen von Spencer erhalten.  
    Spencer Badillo  
    Visa: 4111 1111 1111 1111  
    Gültig bis: 2/2012  
    Bitte aktualisiere sein Reiseprofil.**

Wir müssen auch dafür sorgen, dass die folgenden Informationen nicht als Kreditkarte klassifiziert werden sollen:

**    Hi Alex,  
    Ich gehe mal davon aus, dass ich auch nach Hawaii komme. Mein Buchungscode lautet 1234 1234 1234 1234, und ich werde 3/2012 dort eintreffen.  
    Beste Grüße, Lisa**

Der folgende XML-Codeausschnitt zeigt, wie die oben formulierten Bedürfnisse aktuell in einer Regel für vertrauliche Informationen definiert sind. Diese Regel wird mit Exchange geliefert und ist in eine der DLP-Richtlinienvorlagen aus dem Lieferumfang eingebettet.

    <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
            <Any minMatches="1">
              <Match idRef="Keyword_cc_verification" />
              <Match idRef="Keyword_cc_name" />
              <Match idRef="Func_expiration_date" />
            </Any>
          </Pattern>
        </Entity>

## Mustervergleich in Ihrer Lösung

Die zuvor gezeigte XML-Regeldefinition enthält einen Mustervergleich, mit dem die Wahrscheinlichkeit steigt, dass die Regel nur die wichtigen Informationen erkennt und keine vagen, nur verwandten Informationen. Weitere Informationen zum XML-Schema für DLP-Regeln und -Vorlagen finden Sie unter [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

In der Kreditkartenregel gibt es einen Abschnitt des XML-Codes für Muster, der einen primäre Bezeichnervergleich und einige weitere bestätigende Nachweise enthält. Diese drei Anforderungen werden hier erklärt:

1.  `<IdMatch idRef="Func_credit_card" />  ` – Dies erfordert eine Übereinstimmung einer Funktion mit dem Titel „Kreditkarte“, die intern definiert ist. Diese Funktion umfasst ein paar Überprüfungen, nämlich folgende:
    
    1.  Sie vergleicht einen regulären Ausdruck – in diesem Fall mit 16 Ziffern –, die auch Variationen enthalten können, z. B. ein Trennzeichen, sodass auch **4111 1111 1111 1111** als Übereinstimmung gilt, oder einen Bindestrich, sodass auch **4111-1111-1111-1111** als Übereinstimmung gilt.
    
    2.  Sie wertet die Prüfsumme nach dem Lhun-Algorithmus gegen die 26-stellige Nummer aus, um mit hoher Wahrscheinlichkeit zu gewährleisten, dass es sich um eine Kreditkartennummer handelt.
    
    3.  Sie erfordert eine zwingende Übereinstimmung, und danach wird der bestätigende Nachweis ausgewertet.

2.  `<Any minMatches="1">  ` – Dieser Abschnitt gibt an, dass das Vorhandensein von mindesten einem der folgenden Nachweiselemente erforderlich ist.

3.  Der bestätigende Nachweis kann eine Übereinstimmung bei einem der folgenden drei sein:
    
    `<Match idRef="Keyword_cc_verification" />`
    
    `<Match idRef="Keyword_cc_name" />`
    
    `<Match idRef="Func_expiration_date" />`
    
    Diese drei bedeuten ganz einfach eine Liste von Schlüsselwörtern für Kreditkarten, die Namen der Kreditkarten oder die Notwendigkeit eines Ablaufdatums. Das Ablaufdatum wird intern als eine weitere Funktion definiert und ausgewertet.

## Der Prozess des Auswertens von Inhalten in Bezug auf Regeln

Die hier gezeigten fünf Schritte repräsentieren Aktionen, die Exchange durchführt, um Ihre Regel mit E-Mails zu vergleichen. Für unser Beispiel mit der Kreditkartennummer werden die nachfolgend angegebenen Schritte durchgeführt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Schritt</th>
<th>Aktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1. Inhalt abrufen</p></td>
<td><p>Spencer Badillo</p>
<p>Visa: 4111 1111 1111 1111</p>
<p>Gültig bis: 2/2012</p></td>
</tr>
<tr class="even">
<td><p>2. Analyse regulärer Ausdrücke</p></td>
<td><p>4111 1111 1111 1111 -&gt; eine 16-stellige Zahl wird erkannt</p></td>
</tr>
<tr class="odd">
<td><p>3. Funktionsanalyse</p></td>
<td><ul>
<li><p>4111 1111 1111 1111 -&gt; stimmt mit Prüfsumme überein</p></li>
<li><p>1234 1234 1234 1234 -&gt; stimmt nicht überein</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>4. Zusätzlicher Nachweis</p></td>
<td><ol>
<li><p>Das Schlüsselwort &quot;Visa&quot; ist der Zahl nahe.</p></li>
<li><p>Ein regulärer Ausdruck für das Datum (2/2012) ist der Zahl nahe.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>5. Erkenntnis</p></td>
<td><ol>
<li><p>Es ist ein regulärer Ausdruck, der mit einer Prüfsumme übereinstimmt.</p></li>
<li><p>Weitere Nachweise erhöhen das Vertrauen.</p></li>
</ol>
<p></p></td>
</tr>
</tbody>
</table>


Durch die Art, wie diese Regel von Microsoft eingerichtet wurde, wird vorausgesetzt, dass bestätigende Nachweise wie z. B. Schlüsselwörter Bestandteil des Inhalts der E-Mail-Nachricht sind, damit die Regel eine Übereinstellung erkennt. Deshalb würde für den folgenden E-Mail-Inhalt nicht erkannt werden, dass er eine Kreditkartennummer enthält:

**    Margies Reisepläne,  
    Ich habe aktuelle Informationen von Spencer erhalten.  
    Spencer Burillo  
    4111 1111 1111 1111  
    Bitte aktualisiere sein Reiseprofil.**

Sie können eine benutzerdefinierte Regel einsetzen, mit der ein Muster ohne zusätzliche Nachweise definiert wird, wie das im nächsten Beispiel gezeigt wird. Damit würden Meldungen erkannt werden, die nur die Kreditkartennummer enthält und keine weiteren Nachweise.

``` 
      <Pattern confidenceLevel="85">
         <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

Das Beispiel der Kreditkartennummern in diesem Artikel kann auch auf andere Regeln für vertrauliche Informationen ausgeweitet werden. Um die vollständige Liste der von Microsoft in Exchange bereitgestellten Regeln anzuzeigen, können Sie das Cmdlet[Get-ClassificationRuleCollection](https://technet.microsoft.com/de-de/library/jj218696\(v=exchg.150\)) in der Exchange-Verwaltungsshell folgendermaßen verwenden:

```
    $rule_collection = Get-ClassificationRuleCollection
```

```
    $rule_collection[0].SerializedClassificationRuleCollection | Set-Content oob_classifications.xml -Encoding byte
```

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))

[Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\))

[Exchange Online PowerShell](https://technet.microsoft.com/de-de/library/jj200677\(v=exchg.150\))

