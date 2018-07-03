---
title: 'Abgleichen von Methoden und Techniken für Regelpakete: Exchange Online Help'
TOCTitle: Abgleichen von Methoden und Techniken für Regelpakete
ms:assetid: 09fe9278-d077-452c-b7e5-729b3dc70b1b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674702(v=EXCHG.150)
ms:contentKeyID: 50474995
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Abgleichen von Methoden und Techniken für Regelpakete

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-07-28_

In diesem Thema werden Verfahren beschrieben, um einen Abgleich für Muster- und Nachweiselemente innerhalb einer DLP-XML-Datei (Data Loss Prevention) durchzuführen, die Ihr benutzerdefiniertes Regelpaket für vertrauliche Informationen enthält. Nachdem Sie eine ordnungsgemäß formatierte XML-Datei erstellt haben, können Sie die Datei über die Exchange-Verwaltungskonsole oder die Exchange-Verwaltungsshell importieren, um Ihre Microsoft Exchange Server 2013-DLP-Lösung zu erstellen. Sie sollten bereits mit der Erstellung einer DLP-XML-Datei begonnen haben, um die hier beschriebenen Methoden für den Abgleich zu verwenden. Weitere Informationen zum Definieren eigener DLP-Vorlagen und XML-Dateien finden Sie unter [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

## Das Element "Match"

Das Element `Match` wird innerhalb der Elemente `Pattern` und `Evidence` zur Darstellung der zugrunde liegenden Schlüsselworte, regulären Ausdrücke oder Funktionen verwendet, für die ein Abgleich durchgeführt werden soll. Die Definition des Abgleichs selbst wird außerhalb des Elements `Rule` gespeichert und über das erforderliche Attribut `idRef` referenziert. In einer Musterdefinition können mehrere Elemente vom Typ `Match` enthalten sein. Diese können direkt in das Element `Pattern` aufgenommen werden oder mithilfe des Elements `Any` kombiniert werden, um eine Semantik für den Abgleich zu definieren.

    <?xml version="1.0" encoding="utf-8"?>
    <Rules packageId="...">
            ...
    <Entity id="...">
      <Pattern confidenceLevel="85">
                 <IdMatch idRef="FormattedSSN" />
                 <Match idRef="USDate" />
                 <Match idRef="USAddress" />
      </Pattern>
    </Entity>
            ...
             <Keyword id="FormattedSSN "> ... </Keyword>
             <Regex id=" USDate "> ... </Regex>
             <Regex id="USAddress"> ... </Regex>
            ...
    
    </Rules>

## Definieren eines schlüsselwortbasierten Abgleichs

Eine gängige Regelanforderung ist ein Abgleich, der auf bekannten Ausdrücken in Form von Schlüsselwortzeichenfolgen basiert. Zu diesem Zweck wird das Element `Keyword` verwendet. Das Element "Keyword" verfügt über ein Attribut "id", das in den zugehörigen Regeln vom Typ "Entity" oder "Affinity" als Referenz verwendet wird. Ein einzelnes Element "Keyword" kann in mehreren Regeln vom Typ "Entity" und "Affinity" referenziert werden.

Beim Abgleich kann mit einer genauen Übereinstimmung oder Word Übereinstimmung Algorithmen ausgeführt werden. Genaue Übereinstimmung verwendet einen Groß-/Kleinschreibung beachtet Algorithmus, der durchsucht für den Text in der angegebenen Sprache. Wort wendet einen übereinstimmenden Algorithmus basierend auf Word-Grenzen. Die Begriffe zu vergleichende können die Stichwortdefinition Inlineschema mit dem Begriff untergeordnete Element entsprechen.


> [!TIP]
> Damit eine bessere Effizienz und Leistung erzielt werden, sollten Sie das konstantenbasierte Format für Übereinstimmungen über RegEx verwenden. Verwenden Sie RegEx-Übereinstimmungen nur dann, wenn konstantenbasierte Übereinstimmungen nicht ausreichen und die Flexibilität von regulären Ausdrücken erforderlich ist.



    <Keyword id="Word_Example">
        <Group matchStyle="word">
           <Term>card verification</Term>
           <Term>cvn</Term>
           <Term>cid</Term>
           <Term>cvc2</Term>
           <Term>cvv2</Term>
           <Term>pin block</Term>
           <Term>security code</Term>
        </Group>
    </Keyword>
    ...
    <Keyword id="String_Example">
        <Group matchStyle="string">
           <Term>card</Term>
           <Term>pin</Term>
           <Term>security</Term>
        </Group>
    </Keyword>

## Definieren eines Abgleichs auf Basis regulärer Ausdrücke

Eine weitere gängige Methode für den Abgleich basiert auf regulären Ausdrücken. Aufgrund der Flexibilität, die ein Abgleich auf Basis regulärer Ausdrücke bietet, ist dies eine gängige Methode für den Abgleich von Daten wie Führerscheinnummern oder Adressen. Zur Definition der RegEx-Muster wird eine gängige Syntax für reguläre Ausdrücke verwendet. In der folgenden Tabelle sind Beispiele für einige der gängigsten Token aufgeführt, die für reguläre Ausdrücke verfügbar sind.


> [!TIP]
> Damit eine bessere Effizienz und Leistung erzielt werden, sollten Sie das konstantenbasierte Format für Übereinstimmungen über RegEx verwenden. Verwenden Sie RegEx-Übereinstimmungen nur dann, wenn konstantenbasierte Übereinstimmungen nicht ausreichen und die Flexibilität von regulären Ausdrücken erforderlich ist.




<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Symbol</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>c</p></td>
<td><p>Einmalige Entsprechung für das Zeichenliteral &quot;c&quot;, sofern es sich nicht um ein Sonderzeichen handelt.</p></td>
</tr>
<tr class="even">
<td><p>^</p></td>
<td><p>Entsprechung am Anfang einer Zeile.</p></td>
</tr>
<tr class="odd">
<td><p>.</p></td>
<td><p>Entsprechung für alle Zeichen, bei denen es sich nicht um eine neue Zeile handelt.</p></td>
</tr>
<tr class="even">
<td><p>$</p></td>
<td><p>Entsprechung am Ende einer Zeile.</p></td>
</tr>
<tr class="odd">
<td><p>|</p></td>
<td><p>Logisches OR zwischen Ausdrücken.</p></td>
</tr>
<tr class="even">
<td><p>()</p></td>
<td><p>Gruppieren von Unterausdrücken.</p></td>
</tr>
<tr class="odd">
<td><p>[]</p></td>
<td><p>Definieren einer Zeichenklasse.</p></td>
</tr>
<tr class="even">
<td><p>*</p></td>
<td><p>Entsprechung für den vorstehenden Ausdruck (nullmal oder mehrere Male).</p></td>
</tr>
<tr class="odd">
<td><p>+</p></td>
<td><p>Mindestens einmalige Entsprechung für den vorstehenden Ausdruck.</p></td>
</tr>
<tr class="even">
<td><p>?</p></td>
<td><p>Entsprechung für den vorstehenden Ausdruck (null- oder einmal).</p></td>
</tr>
<tr class="odd">
<td><p>{<em>n</em>}</p></td>
<td><p>Entsprechung für den vorstehenden Ausdruck (<em>n</em>-mal).</p></td>
</tr>
<tr class="even">
<td><p>{<em>n,</em>}</p></td>
<td><p>Entsprechung für den vorstehenden Ausdruck (mindestens <em>n</em>-mal).</p></td>
</tr>
<tr class="odd">
<td><p>{<em>n, m</em>}</p></td>
<td><p>Entsprechung für den vorstehenden Ausdruck (mindestens <em>n</em>-mal und maximal <em>m</em>-mal).</p></td>
</tr>
<tr class="even">
<td><p>\d</p></td>
<td><p>Entsprechung für eine Ziffer.</p></td>
</tr>
<tr class="odd">
<td><p>\D</p></td>
<td><p>Entsprechung für ein Zeichen, bei dem es sich nicht um eine Ziffer handelt.</p></td>
</tr>
<tr class="even">
<td><p>\w</p></td>
<td><p>Entsprechung für einen Buchstaben, einschließlich Unterstrich.</p></td>
</tr>
<tr class="odd">
<td><p>\W</p></td>
<td><p>Entsprechung für ein Zeichen, bei dem es sich nicht um einen Buchstaben handelt.</p></td>
</tr>
<tr class="even">
<td><p>\s</p></td>
<td><p>Entsprechung für ein Leerraumzeichen (\t, \n, \r oder \f).</p></td>
</tr>
<tr class="odd">
<td><p>\S</p></td>
<td><p>Entsprechung für ein Zeichen, bei dem es sich nicht um ein Leerraumzeichen handelt.</p></td>
</tr>
<tr class="even">
<td><p>\t</p></td>
<td><p>Tabulator.</p></td>
</tr>
<tr class="odd">
<td><p>\n</p></td>
<td><p>Neue Zeile.</p></td>
</tr>
<tr class="even">
<td><p>\r</p></td>
<td><p>Wagenrücklauf.</p></td>
</tr>
<tr class="odd">
<td><p>\f</p></td>
<td><p>Seitenvorschub.</p></td>
</tr>
<tr class="even">
<td><p>\<em>m</em></p></td>
<td><p>Escaping für <em>m</em>, wobei <em>m</em> eins der oben beschriebenen Metazeichen ist: ^, ., $, |, (), [], *, +, ?, \ oder /.</p></td>
</tr>
</tbody>
</table>


Das Element "Regex" verfügt über ein Attribut "id", das in den zugehörigen Regeln vom Typ "Entity" oder "Affinity" als Referenz verwendet wird. Ein einzelnes Element "Regex" kann in mehreren Regeln vom Typ "Entity" und "Affinity" referenziert werden. Der RegEx-Ausdruck wird als Wert des Elements "Regex" definiert.

    <Regex id="CCRegex">
         \bcc\#\s|\bcc\#\:\s
    </Regex>
    ...
    <Regex id="ItinFormatted">
        (?:^|[\s\,\:])(?:9\d{2})[- ](?:[78]\d[-       ]\d{4})(?:$|[\s\,]|\.\s)
    </Regex>
    ...
    <Regex id="NorthCarolinaDriversLicenseNumber">
        (^|\s|\:)(\d{1,8})($|\s|\.\s)
    </Regex>

## Kombinieren mehrerer Elemente für den Abgleich

Eine gängige Methode, um die Zuverlässigkeit des Abgleichs zu erhöhen, ist die Definition einer Semantik aus mehreren Match-Elementen, z. B. die Festlegung, dass eine oder mehrere Entsprechungen ermittelt werden müssen. Zur Definition der Logik zwischen mehreren Übereinstimmungen kann das Element "Any" verwendet werden. Das Any-Element kann als Unterelement im Pattern-Element verwendet werden. Es enthält mindestens ein untergeordnetes Match-Element und definiert die Logik für die Übereinstimmungen zwischen diesen Elementen. Im Folgenden finden Sie XML-Codebeispiele für die Any-Elemente mit allen Entsprechungen, Nicht-Logik und der exakten Anzahl von Entsprechungen.

Das optionale minMatches-Attribut kann verwendet werden (Standardwert = 1), um die Mindestanzahl von Match-Elementen anzugeben, für die eine Übereinstimmung ermittelt werden muss. Gleichermaßen kann das optionale maxMatches-Attribut verwendet werden (Standardwert = Anzahl von untergeordneten Match-Elementen), um die maximale Anzahl von Match-Elementen anzugeben, für die eine Übereinstimmung ermittelt werden muss. Diese Bedingungen werden mithilfe logischer Operatoren basierend auf der Verwendung der Attribute "minMatches" und "maxMatches" kombiniert, sodass die folgende Semantik möglich ist:

  - Entsprechung für alle untergeordneten Match-Elemente
    
    Keine Entsprechung für untergeordnete Match-Elemente
    
    Entsprechung für die genaue Untermenge beliebiger untergeordneter Match-Elemente

<!-- end list -->

    <Any minMatches="3" maxMatches="3">
        <Match idRef="USDate" />
        <Match idRef="USAddress" />
        <Match idRef="Name" />
    </Any>

    <Any maxMatches="0">
        <Match idRef="USDate" />
        <Match idRef="USAddress" />
        <Match idRef="Name" />
    </Any>

    <Any minMatches="1" maxMatches="1">
        <Match idRef="USDate" />
        <Match idRef="USAddress" />
        <Match idRef="Name" />
    </Any>

## Höhere Zuverlässigkeitsstufe durch mehr Nachweise

Für Entity-basierte Regeln kann die Zuverlässigkeitsstufe außerdem erhöht werden, indem mehrere Pattern-Elemente definiert werden, für die je eine steigende Anzahl von Nachweisen festgelegt wird. Zu diesem Zweck werden die Attribute "minMatches" und "maxMatches" für das Any-Element verwendet, um unabhängige Muster mit steigender Zuverlässigkeitsstufe basierend auf einer steigenden Anzahl von Nachweisen zu erstellen. Beispiel:

  - Bei Ermittlung eines Nachweises: Zuverlässigkeitsstufe ist 65 %

  - Bei Ermittlung von zwei Nachweisen: Zuverlässigkeitsstufe ist 75%

  - Bei Ermittlung von drei Nachweisen: Zuverlässigkeitsstufe ist 85%

<!-- end list -->

    <Entity id="..." patternsProximity="300" >
        <Pattern confidenceLevel="65">
            <IdMatch idRef="UnformattedSSN" />
            <Any maxMatches="1">
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
            <IdMatch idRef="UnformattedSSN" />
            <Any minMatches="2" maxMatches="2">
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
            <IdMatch idRef="UnformattedSSN" />
            <Any minMatches="3">
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>
    </Entity>

## Beispiel: Regel für den Abgleich von Sozialversicherungsnummern der USA (Social Security Number, SSN)

In diesem Abschnitt finden Sie eine Einführung in die Erstellung einer Regel zum Abgleich einer Sozialversicherungsnummer. Beschreiben Sie zunächst, wie Inhalte mit einer Sozialversicherungsnummer ermittelt werden. Eine Sozialversicherungsnummer wird ermittelt, wenn:

1.  der reguläre Ausdruck mit einer formatierten Sozialversicherungsnummer übereinstimmt (und im zulässigen Sozialversicherungsnummernbereich liegt)

2.  Nachweis   In unmittelbarer Nähe wird eins der folgenden Elemente ermittelt:
    
    1.  Schlüsselwortübereinstimmung {Social Security, Soc Sec, SSN, SSNS, SSN\#, SS\#, SSID}
    
    2.  Text zur Darstellung einer Adresse in den USA
    
    3.  Text zur Darstellung eines Datums
    
    4.  Text zur Darstellung eines Namens

Übersetzen Sie die Beschreibung anschließend in eine Regelschemadarstellung:

    <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77"
             patternsProximity="300" RecommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="FormattedSSN" />
          <Any minMatches="1">
              <Match idRef="SSNKeywords" />
              <Match idRef="USDate" />
              <Match idRef="USAddress" />
              <Match idRef="Name" />
          </Any>
        </Pattern>
    </Entity>

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

[Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

