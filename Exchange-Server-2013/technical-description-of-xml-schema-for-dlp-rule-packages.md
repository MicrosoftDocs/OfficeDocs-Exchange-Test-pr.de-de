---
title: 'Entwickeln von Regelpaketen für sensible Informationen: Exchange Online Help'
TOCTitle: Entwickeln von Regelpaketen für sensible Informationen
ms:assetid: c4ab8707-0839-4855-9390-3dbcb43475a7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674704(v=EXCHG.150)
ms:contentKeyID: 50476664
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entwickeln von Regelpaketen für sensible Informationen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-07-28_

Das XML-Schema und die Anleitungen in diesem Artikel sollen Ihnen beim Einstieg in die Erstellung eigener grundlegender XML-Dateien zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) helfen, in denen Sie in einem Klassifizierungsregelpaket Ihre eigenen Typen vertraulicher Informationen definieren. Nachdem Sie eine wohlgeformte XML-Datei erstellt haben, können Sie sie entweder mit der die Exchange-Verwaltungskonsole oder mit der Exchange-Verwaltungsshell importieren, um mit ihrer Hilfe eine Exchange Server 2013-DLP-Lösung zu erstellen. Eine XML-Datei, die als benutzerdefinierte DLP-Richtlinienvorlage dient, kann das XML enthalten, das sich in Ihrem Klassifizierungsregelpaket befindet. Eine Übersicht über die Definition eigener DLP-Vorlagen als XML-Dateien finden Sie unter [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

**Inhalt**

Overview of the rule authoring process

Rule description

Basic rule structure

Using local languages in your XML file

Classification rule pack XML schema definition

For more information

## Übersicht über das Regelerstellungsverfahren

Das Regelerstellungsverfahren setzt sich aus den folgenden allgemeinen Schritte zusammen.

1.  Bereiten Sie eine Reihe von Testdokumenten vor, die repräsentativ für die jeweilige Zielumgebung sind. Wichtige Merkmale für Testdokumente, die zu berücksichtigen sind: Eine Teilmenge der Dokumente enthält die Entität oder Affinität, für die die Regel erstellt wird, und eine Teilmenge der Dokumente enthält nicht die Entität oder Affinität, für die die Regel erstellt wird.

2.  Ermitteln Sie die Regeln, die den Akzeptanzanforderungen (Genauigkeit und Rückruf) entsprechen, um qualifizierende Inhalte zu identifizieren. Dies setzt ggf die Erstellung mehrerer Bedingungen innerhalb einer Regel voraus, die mit boolescher Logik verbunden werden und gemeinsam die minimalen Entsprechungskriterien zur Identifizierung von Zieldokumenten erfüllen.

3.  Legen Sie die empfohlene Zuverlässigkeitsstufe für die Regeln basierend auf den Akzeptanzanforderungen (Genauigkeit und Rückruf) fest. Das empfohlene Zuverlässigkeitselement kann als standardmäßige Zuverlässigkeitsstufe für die Regel betrachtet werden.

4.  Überprüfen Sie die Regeln, indem Sie hiermit eine Richtlinie in Kraft setzen und den Inhalt des Tests überwachen. Passen Sie die Regeln oder die Zuverlässigkeitsstufe basierend auf den Ergebnissen an, um ein Maximum an Inhalten zu erkennen und gleichzeitig falsch positive und negative Ergebnisse zu minimieren. Setzen Sie die Überprüfung und Anpassung der Regeln so lange fort, bis ein zufriedenstellendes Niveau an Inhaltserkennung sowohl für positive als auch für negative Beispiele erreicht ist.

Informationen zur XML-Schemadefinition für Richtlinienvorlagendateien finden Sie unter [Entwickeln von Vorlagendateien für DLP-Richtlinien](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

## Regelbeschreibung

Für das DLP-Modul zur Erkennung vertraulicher Informationen können zwei Hauptregeltypen erstellt werden: Entität und Affinität. Der gewählte Regel typ basiert auf der Art der Verarbeitungslogik, die bei der Verarbeitung des Inhalts wie in den vorstehenden Abschnitten beschrieben angewendet werden sollte. Die Regeldefinitionen werden in einem XML-Dokument in dem Format konfiguriert, das von der standardisierten Regel-XSD vorgegeben wird. Die Regeln beschreiben sowohl den Inhaltstyp, der verglichen werden soll, als auch die Zuverlässigkeitsstufe, die die beschriebene Übereinstimmung im Zielinhalt repräsentiert. Die Zuverlässigkeit stufe gibt die Wahrscheinlichkeit ein, mit der die Entität vorhanden ist, wenn im Inhalt ein Muster gefunden wird, oder die Wahrscheinlichkeit, mit der die Affinität vorhanden ist, wenn im Inhalt ein Nachweis gefunden wird.

## Grundlegende Regelstruktur

Die Regeldefinition setzt sich aus drei Hauptkomponenten zusammen:

1.  **Entität**   definiert die Übereinstimmungs- und Zählungslogik für diese Regel

2.  **Affinität**   definiert die Übereinstimmungslogik für die Regel

3.  **Lokalisierte Zeichenfolgen**   Lokalisierung von Regelnamen und deren Beschreibungen

Es werden drei weitere unterstützende Elemente verwendet, mit denen die Details der Verarbeitung definiert werden und auf die in den Hauptkomponenten verwiesen wird: Schlüsselwort, RegEx und Funktion. Mithilfe von Verweisen kann eine einzige Definition der unterstützenden Elemente, wie eine Sozialversicherungsnummer, in mehreren Entitäts- oder Affinitätsregeln verwendet werden. Die grundlegende Regelstruktur im XML-Format kann wie folgt beschrieben werden.

    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
    
      <RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
        <Version major="1" minor="0" build="0" revision="0"/>
        <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
        <Details defaultLangCode="en-us">
          <LocalizedDetails langcode="en-us">
            <PublisherName>DLP by EPG</PublisherName>
            <Name>CSO Custom Rule Pack</Name>
            <Description>This is a rule package for a EPG demo.</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
    
      <Rules>
    
        <!-- Employee ID -->
        <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_employee_id" />
            <Match idRef="Keyword_employee" />
          </Pattern>
        </Entity>
    
        <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
        <Keyword id="Keyword_employee">
          <Group matchStyle="word">
            <Term>Identification</Term>
            <Term>Contoso Employee</Term>
          </Group>
        </Keyword>
    
    
        <LocalizedStrings>
    
          <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
            <Name default="true" langcode="en-us">
              Employee ID
            </Name>
            <Description default="true" langcode="en-us">
              A custom classification for detecting Employee ID's
            </Description>
          </Resource>
    
        </LocalizedStrings>
      </Rules>
    </RulePackage>

## Entitätsregeln

Entitätsregeln beziehen sich auf ordnungsgemäß definierte Kennungen wie die Sozialversicherungsnummer und werden durch eine Sammlung zählbarer Muster repräsentiert. Entitätsregeln geben die Anzahl sowie die Zuverlässigkeitsstufe einer Übereinstimmung zurück, wobei die Anzahl gleich der Gesamtanzahl Vorkommen der Entität ist, die gefunden wurde, und die Vertraulichkeitsstufe für die Wahrscheinlichkeit steht, dass die angegebene Entität im jeweiligen Dokument vorkommt. Entitäten enthalten das Attribut "id" als eindeutigen Bezeichner. Der Bezeichner wird für Lokalisierung, Versionierung und Abfragen verwendet. Bei der Entitäten-ID muss es sich um eine GUID handeln, die in anderen Entitäten oder Affinitäten nicht dupliziert werden sollte. Hierauf wird im Abschnitt "LocalizedStrings" verwiesen.

Entitätsregeln enthalten das optionale Attribut "patternsProximity" (Standard = 300), das bei der Anwendung von boolescher Logik verwendet wird, um die Näherung mehrerer Muster anzugeben, die erforderlich ist, damit die Übereinstimmungsbedingung erfüllt ist. Das Entity-Element enthält ein oder mehrere untergeordnete Pattern-Elemente, wobei jedes Muster eine eindeutige Darstellung der Entität wie "Kreditkarte" oder "Führerschein" ist. Das Pattern-Element weist das obligatorische Attribut "confidenceLevel" auf, welches die Genauigkeit des Musters basierend auf dem Beispieldatenset repräsentiert. Das Pattern-Element kann drei untergeordnete Elemente aufweisen:

1.  IdMatch – Dieser Wert ist erforderlich.

2.  Match

3.  Any

Wenn ein beliebiges Pattern-Element den Wert "true" zurückgibt, ist das Muster erfüllt. Die Anzahl des Entity-Elements entspricht der Summe aller erkannten Pattern-Elemente.

![Mathematische Formel für Entitätsanzahl](images/JJ674704.25309939-98bc-4460-8f89-8560bbad7981(EXCHG.150).gif "Mathematische Formel für Entitätsanzahl")

"k" ist dabei die Anzahl von Pattern-Elementen für die Entität ist.

Ein Pattern-Element muss über genau ein IdMatch-Element verfügen. "IdMatch" steht für den Bezeichner, der mit dem Muster verglichen werden soll, z. B. eine Kreditkartennummer oder eine ITIN-Nummer. Die Anzahl eines Pattern-Elements ist gleich der Anzahl von IdMatches, die mit dem Pattern-Element verglichen wurden. Das IdMatch-Element verankert das Näherungsfenster für die Match-Elemente.

Ein anderes optionales untergeordnete Element des Elements Muster ist das Match-Element, das bestätigende Nachweis, die erforderlich ist darstellt, um die Unterstützung von Entwicklern das Element IdMatch abgeglichen. Die höhere Confidence Regel erfordern beispielsweise, dass neben suchen eine Kreditkartennummer, zusätzliche Artefakte im Dokument in einem Fenster Nähe der Kreditkarte wie Adresse und den Namen vorhanden sind. Diese zusätzliche Artefakte würde über die Match Element oder ein beliebiges Element (diese werden im Abschnitt Matching Methods and Techniques genauer beschrieben) dargestellt. Mehrere Match-Elemente können in der Musterdefinition eines enthalten sein können direkt in das Muster-Element eingeschlossen werden oder übereinstimmenden Semantik definieren mithilfe des keinem Elements kombiniert. True, wenn eine Übereinstimmung, klicken Sie im Fenster Nähe platziert, um den Inhalt IdMatch gefunden wird gibt es zurück.

Die Details dazu, welche Inhalte verglichen werden müssen, werden weder im IdMatch- noch im Match-Element definiert, sondern es wird über das idRef-Attribut darauf verwiesen. Dies fördert die Wiederverwendbarkeit von Definitionen in mehreren Pattern-Konstrukten.

    <Entity id="..." patternsProximity="300" > 
        <Pattern confidenceLevel="85">
            <IdMatch idRef="FormattedSSN" />
            <Any minMatches="1">
                <Match idRef="SSNKeyword" />
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>  
        <Pattern confidenceLevel="65">
            <IdMatch idRef="UnformattedSSN" />
            <Match idRef="SSNKeyword" />
            <Any minMatches="1">        
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>
    </Entity> 

Das Element "Entity id", das in der vorherigen XML von "..." repräsentiert wurde, sollte eine GUID sein, und es wird im Abschnitt "LocalizedStrings" darauf verwiesen.

## Näherungsfenster für das Entity-Muster

"Entity" enthält den optionalen Attributwert "patternsProximity" (ganze Zahl, Standardwert = 300), der für die Suche nach Mustern verwendet wird. Der Attributwert definiert für jedes Muster den Abstand (in Unicode-Zeichen) von der IdMatch-Position für alle anderen Übereinstimmungen, die für dieses Muster angegeben wurden. Das Näherungsfenster wird von der IdMatch-Position verankert, wobei das Fenster links und rechts von "IdMatch" erweitert wird.

![Textmuster mit hervorgehobenen übereinstimmenden Elementen](images/JJ674704.65d52989-f50f-4097-b39a-9612f860d727(EXCHG.150).gif "Textmuster mit hervorgehobenen übereinstimmenden Elementen")

Im nachstehenden Beispiel wird gezeigt, in welcher Weise das Näherungsfenster den Überstimmungsalgorithmus beeinflusst, wobei das Element "SSN IdMatch" mindestens eine bestätigende Übereinstimmung von Adresse, Name oder Datum erfordert. Aufgrund von SSN2 und SSN3 gibt es nur Übereinstimmungen für SSN1 und SSN4, und im Näherungsfenster wird kein oder nur ein teilweise bestätigender Nachweis gefunden.

![Beispiele für Übereinstimmungen und Nicht-Übereinstimmungen mit Regeln](images/JJ674704.8117deb3-d8c8-4d4e-a011-ac5f9990b08e(EXCHG.150).gif "Beispiele für Übereinstimmungen und Nicht-Übereinstimmungen mit Regeln")

Beachten Sie, dass der Nachrichtentext und jede Anlage als unabhängige Artikel behandelt werden. Dies bedeutet, dass das Fenster Nähe zum Ende des jeden dieser Bereiche nicht überschreitet. Für jedes Element (Anlage oder Text) muss die IdMatch und die bestätigende Nachweis innerhalb der einzelnen befinden.

## Zuverlässigkeitsstufe für "Entity"

Die Zuverlässigkeitsstufe des Entity-Elements ist die Kombination aus allen bestätigten Zuverlässigkeitsstufen von "Pattern". Die Zuverlässigkeitsstufen werden mithilfe der folgenden Gleichung kombiniert:

![Mathematische Formel für die Entitätszuverlässigkeitsstufe](images/JJ674704.9b8bb9c8-3ded-4ea5-a609-71d8034b1017(EXCHG.150).gif "Mathematische Formel für die Entitätszuverlässigkeitsstufe")

"k" ist dabei die Anzahl von Pattern-Elementen für die Entität und ein Muster, das keine Rückgaben mit einer Zuverlässigkeitsstufe von 0 vergleicht.

Rückbezüglich auf das Codebeispiel für die Struktur des Entity-Elements gilt, dass die Zuverlässigkeitsstufe der Entität bei 94,75 % liegt, wenn beide Muster verglichen werden, basierend auf der folgenden Berechnung:

CLEntität= 1-\[(1-CLPattern1) x (1-CLPattern1)\]

*= 1-\[(1-0,85) x (1-0,65)\]*

*= 1-(0,15 x 0,35)*

*= 94.75%*

Ebenso gilt, dass die Zuverlässigkeitsstufe der Entität 65 % beträgt, wenn nur das zweite Muster eine Übereinstimmung ergibt, und zwar basierend auf der folgenden Berechnung:

CLEntität= 1 – \[(1 – CLPattern1) X (1 – CLPattern1)\]

*= 1 – \[(1 – 0) X (1 – 0,65)\]*

*= 1 – (1 X 0,35)*

*= 65%*

Diese Zuverlässigkeitsstufenwerte werden in den Regeln für einzelne Muster zugewiesen, und zwar basierend auf der Sammlung der Testdokumente, die als Teil des Regelerstellungsverfahrens ausgewertet wurden.

## Affinitätsregeln

Affinitätsregel beziehen sich auf Inhalte ohne ordnungsgemäß definierte Bezeichner, z. B. Sarbanes-Oxley oder Finanzdokumente des Unternehmens. In diesen Inhalten kann kein eigenständiger, konsistenter Bezeichner gefunden werden; stattdessen muss analysiert werden, ob eine Sammlung von Nachweisen vorhanden ist. Mit Affinitätsregeln wird keine Anzahl zurückgegeben; stattdessen geben sie die vorhandenen Nachweise und die zugeordnete Zuverlässigkeitsstufe zurück. Affinitätsinhalte werden als eine Sammlung von unabhängigen Nachweisen dargestellt. Als Nachweis gilt eine Häufung von erforderlichen Treffern innerhalb einer bestimmten Näherung. Für eine Affinitätsregel werden die Näherung mit dem Attribut "evidencesProximity" (Standardwert 600) und die minimale Zuverlässigkeitsstufe mit dem Attribut "thresholdConfidenceLevel" definiert.

Affinitätsregeln enthalten das id-Attribut für den eindeutigen Bezeichner, der für Lokalisierung, Versionierung und Abfragen verwendet wird. Im Gegensatz zu Entitätsregeln enthalten Affinitätsregeln nicht das IdMatch-Element, da sie nicht auf ordnungsgemäß definierten Bezeichnern aufsetzen.

Jede Affinitätsregel enthält mindestens ein untergeordnetes Evidence-Element, mit dem der Nachweis definiert wird, der gefunden werden soll, und die Zuverlässigkeitsstufe, die in der Affinitätsregel bezeichnet wurde. Die Affinität gilt als nicht bewiesen, wenn die sich ergebende Zuverlässigkeitsstufe unter dem Schwellenwert liegt. Jeder Nachweis stellt logisch einen bestätigenden Nachweis für diesen "Typ" Dokument dar, und das Attribut "confidenceLevel" steht für die Genauigkeit dieses Nachweises im Testdatenset.

Evidence-Elemente weisen ein oder mehrere untergeordnete Match- oder Any-Elemente auf. Wenn es eine Übereinstimmung mit allen untergeordneten Match- und Any-Elementen gibt, gilt der Nachweis als erbracht, und die Zuverlässigkeitsstufe geht in die Berechnung der Zuverlässigkeitsstufe der Regel ein. Für die Match- oder Any-Elemente in Affinitätsregeln gilt dieselbe Beschreibung wie bei Entitätsregeln.

    <Affinity id="..." 
              evidencesProximity="1000"
              thresholdConfidenceLevel="65">
        <Evidence confidenceLevel="40">
            <Any> 
                <Match idRef="AssetsTerms" /> 
                <Match idRef="BalanceSheetTerms" /> 
                <Match idRef="ProfitAndLossTerms" /> 
            </Any> 
        </Evidence>
        <Evidence confidenceLevel="40">
            <Any minMatches="2"> 
                <Match idRef="TaxTerms" /> 
                <Match idRef="DollarAmountTerms" /> 
                <Match idRef="SECTerms" /> 
                <Match idRef="SECFilingFormTerms" /> 
                <Match idRef="DollarTotalRegex" /> 
            </Any> 
        </Evidence>
    </Affinity>

## Näherungsfenster für Affinität

Das Näherungsfenster für die Affinität wird anders berechnet als für Entity-Muster. Bei der Affinität folgt die Näherung einem gleitenden Fenster-Modell. Mit dem Näherungsalgorithmus für die Affinität wird versucht, in einem bestimmten Fenster die maximale Anzahl von übereinstimmenden Nachweisen zu finden. Die Nachweise im Näherungsfenster müssen über eine Zuverlässigkeitsstufe verfügen, die größer als der Schwellenwert der verwendeten Affinitätsregel ist.

![Text in der Nähe einer Affinitätsregelübereinstimmung](images/JJ674704.2601ec86-0094-43fa-8d22-9d97f7465942(EXCHG.150).gif "Text in der Nähe einer Affinitätsregelübereinstimmung")

## Zuverlässigkeit stufe für Affinität

Die Zuverlässigkeitsstufe für die Affinität entspricht der Kombination der Nachweise, die im Näherungsfenster der Affinitätsregel gefunden wurden. Dies ist zwar mit der Zuverlässigkeitsstufe der Entitätsregel vergleichbar, der Hauptunterschied liegt jedoch in der Anwendung des Näherungsfensters. Ebenso wie bei Entitätsregeln ist die Zuverlässigkeitsstufe des Affinity-Elements eine Kombination aus allen erfüllten Zuverlässigkeitsstufe des Evidence-Elements, bei der Affinitätsregel steht dies jedoch nur für die höchste Kombination aus Evidence-Elementen, die im Näherungsfenster gefunden wurden. Die Zuverlässigkeitsstufen des Evidence-Elements werden mit der folgenden Gleichung kombiniert:

![Mathematische Formel für Affinitätsregelzuverlässigkeit](images/JJ674704.8a5da4ca-af02-4c5a-ab60-0072dc7e7a0f(EXCHG.150).gif "Mathematische Formel für Affinitätsregelzuverlässigkeit")

"k" ist dabei die Anzahl von Evidence-Elementen für die Affinität, für die im Näherungsfenster eine Übereinstimmung gefunden wurde.

Rückblickend auf Abbildung 4, "Beispiel für die Struktur einer Affinitätsregel", gilt: Wenn es für alle drei Nachweise im gleitenden Näherungsfenster Übereinstimmungen gibt, beträgt die Zuverlässigkeit stufe der Affinität basierend auf der nachstehenden Berechnung 85,6 %. Damit wird der Schwellenwert der Affinitätsregel von 65 % überschritten, was dazu führt, dass die Regel übereinstimmt.

CLAffinität= 1 – \[(1 – CLNachweis 1) X (1 – CLNachweis 2) X (1 – CLNachweis 2)\]

*= 1 – \[(1 – 0,6) X (1 – 0,4) X (1 – 0,4)\]*

*= 1 – (0,4 X 0,6 X 0,6)*

*= 85.6%*

![Beispiel für die Affinitätregelübereinstimmung mit hoher Zuverlässigkeit](images/JJ674704.e17b2e22-18c3-40c4-8f19-0993bb556675(EXCHG.150).gif "Beispiel für die Affinitätregelübereinstimmung mit hoher Zuverlässigkeit")

Ausgehend von derselben Beispielregeldefinition gilt: Wenn nur der erste Nachweis eine Übereinstimmung ergibt, da der zweite Nachweis außerhalb des Näherungsfensters liegt, liegt die höchste Zuverlässigkeitsstufe für die Affinität basierend auf der nachstehenden Berechnung bei 60 %, und die Affinitätsregel stimmt nicht überein, da der Schwellenwert von 65 % nicht erreicht wurde.

CLAffinität= 1 – \[(1 – CLNachweis 1) X (1 – CLNachweis 2) X (1 – CLNachweis 2)\]

*= 1 – \[(1 – 0,6) X (1 – 0) X (1 – 0)\]*

*= 1 – (0,4 X 1 X 1)*

*= 60%*

![Beispiel für eine Affinitätsregelübereinstimmung mit geringer Zuverlässigkeit](images/JJ674704.077095b1-6eb0-40df-b254-f33437725720(EXCHG.150).gif "Beispiel für eine Affinitätsregelübereinstimmung mit geringer Zuverlässigkeit")

## Optimieren von Zuverlässigkeitsstufen

Einer der wichtigsten Aspekte im Regelerstellungsverfahren besteht darin, die Zuverlässigkeitsstufen für Entitäts- und Affinitätsregeln zu optimieren. Nach der Erstellung der Regeldefinitionen sollten Sie die Regel auf repräsentative Inhalte anwenden und die Daten im Hinblick auf die Genauigkeit überprüfen. Vergleichen Sie die zurückgegebenen Ergebnisse für jedes Muster oder jeden Nachweis mit den für die Testdokumente zu erwartenden Ergebnissen.

![Tabelle zum Vergleich von Regelübereinstimmungen](images/JJ674704.25a7d9a1-d02f-447e-a88b-8e78bdc0413a(EXCHG.150).gif "Tabelle zum Vergleich von Regelübereinstimmungen")

Wenn die Regeln den Akzeptanzanforderungen entsprechen, d. h. Muster oder Nachweis liegen bei einer Zuverlässigkeitsrate oberhalb des angegebenen Schwellenwerts (z. B. 75 %), ist der Match-Ausdruck vollständig und kann in die nächste Phase überführt werden.

Wenn Muster oder Nachweis nicht der Zuverlässigkeitsstufe entsprechen, überarbeiten Sie beides (fügen Sie z. B. weitere bestätigende Nachweise hinzu, oder entfernen Sie Muster/Nachweise bzw. fügen Sie weitere hinzu usw.), und wiederholen Sie diesen Schritt.

Optimieren Sie im nächsten Schritt die Zuverlässigkeitsstufe für jedes Muster oder jeden Nachweis in Ihren Regeln basierend auf den Ergebnissen des vorherigen Schritts. Aggregieren Sie für jedes Muster oder jeden Nachweis folgende Werte: die Anzahl von richtig positiven Ergebnissen (True Positives, TP), die Teilmenge der Dokumente, die die Entität oder Affinität enthalten, für die die Regel erstellt wurde und die zu Übereinstimmung führten, die Anzahl von falsch positiven Ergebnissen (False Positives, FP) und die Teilmenge der Dokumente, die die Entität oder Affinität nicht enthalten, für die die Regel erstellt wurde und die ebenfalls eine Übereinstimmung zurückgegeben haben. Legen Sie die Zuverlässigkeitsstufe für jedes Muster/jeden Nachweis mithilfe der folgenden Berechnung fest:

*Zuverlässigkeitsstufe = richtig positive Ergebnisse / (richtig positive Ergebnisse + falsch positive Ergebnisse)*


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Muster oder Nachweise</th>
<th>Richtig positive Ergebnisse</th>
<th>Falsch positive Ergebnisse</th>
<th>Zuverlässigkeitsstufe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>P1oder E1</p></td>
<td><p>4</p></td>
<td><p>1</p></td>
<td><p>80%</p></td>
</tr>
<tr class="even">
<td><p>P2oder E2</p></td>
<td><p>2</p></td>
<td><p>2</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Pnoder En</p></td>
<td><p>9</p></td>
<td><p>10</p></td>
<td><p>47%</p></td>
</tr>
</tbody>
</table>


## Verwenden von lokalen Sprachen in einer XML-Datei

Das Regelschema unterstützt die Speicherung von lokalisierten Namen und Beschreibungen für alle Entity- und Affinity-Elemente. Für jedes Entity- und Affinity-Element muss es ein entsprechendes Element im Abschnitt "LocalizedStrings" geben. Zum Lokalisieren der einzelnen Elemente schließen Sie ein Resource-Element als untergeordnetes Element des LocalizedStrings-Elements ein, um den Namen und die Beschreibungen für mehrere Gebietsschemas für jedes Element zu speichern. Das Resource-Element enthält ein erforderliches idRef-Attribut, das dem zugehörigen idRef-Attribut jedes lokalisierten Elements entspricht. Die untergeordneten Elemente "Locale" des Elements "Resource" enthalten den lokalisierten Namen und die Beschreibungen für jedes angegebene Gebietsschema.

    <LocalizedStrings>
        <Resource idRef="guid">
            <Locale langcode="en-US" default="true"> 
                <Name>affinity name en-us</Name> 
                <Description>
                    affinity description en-us
                </Description> 
            </Locale> 
            <Locale langcode="de"> 
                <Name>affinity name de</Name> 
                <Description>
                    affinity description de
                </Description> 
            </Locale> 
        </Resource>
    </LocalizedStrings>

## XML-Schema-Definition des Klassifizierungsregelpakets

    <?xml version="1.0" encoding="utf-8"?>
    <xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
               targetNamespace="http://schemas.microsoft.com/office/2011/mce" 
               xmlns:xs="http://www.w3.org/2001/XMLSchema"
               elementFormDefault="qualified"
               attributeFormDefault="unqualified"
               id="RulePackageSchema">
      <xs:simpleType name="LangType">
        <xs:union memberTypes="xs:language">
          <xs:simpleType>
            <xs:restriction base="xs:string">
              <xs:enumeration value=""/>
            </xs:restriction>
          </xs:simpleType>
        </xs:union>
      </xs:simpleType>
      <xs:simpleType name="GuidType" final="#all">
        <xs:restriction base="xs:token">
          <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RulePackageType">
        <xs:sequence>
          <xs:element name="RulePack" type="mce:RulePackType"/>
          <xs:element name="Rules" type="mce:RulesType">
            <xs:key name="UniqueRuleId">
              <xs:selector xpath="mce:Entity|mce:Affinity"/>
              <xs:field xpath="@id"/>
            </xs:key>
            <xs:key name="UniqueProcessorId">
              <xs:selector xpath="mce:Regex|mce:Keyword"></xs:selector>
              <xs:field xpath="@id"/>
            </xs:key>
            <xs:key name="UniqueResourceIdRef">
              <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
              <xs:field xpath="@idRef"/>
            </xs:key>        
            <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
              <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
              <xs:field xpath="@idRef"/>
            </xs:keyref>
            <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
              <xs:selector xpath="mce:Entity|mce:Affinity"/>
              <xs:field xpath="@id"/>
            </xs:keyref>
          </xs:element>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="RulePackType">
        <xs:sequence>
          <xs:element name="Version" type="mce:VersionType"/>
          <xs:element name="Publisher" type="mce:PublisherType"/>
          <xs:element name="Details" type="mce:DetailsType">
            <xs:key name="UniqueLangCodeInLocalizedDetails">
              <xs:selector xpath="mce:LocalizedDetails"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
            <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
              <xs:selector xpath="."/>
              <xs:field xpath="@defaultLangCode"/>
            </xs:keyref>
          </xs:element>
          <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="VersionType">
        <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
      </xs:complexType>
      <xs:complexType name="PublisherType">
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="LocalizedDetailsType">
        <xs:sequence>
          <xs:element name="PublisherName" type="mce:NameType"/>
          <xs:element name="Name" type="mce:RulePackNameType"/>
          <xs:element name="Description" type="mce:OptionalNameType"/>
        </xs:sequence>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:complexType>
      <xs:complexType name="DetailsType">
        <xs:sequence>
          <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
      </xs:complexType>
      <xs:complexType name="EncryptionType">
        <xs:sequence>
          <xs:element name="Key" type="xs:normalizedString"/>
          <xs:element name="IV" type="xs:normalizedString"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="RulePackNameType">
        <xs:restriction base="xs:token">
          <xs:minLength value="1"/>
          <xs:maxLength value="64"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="NameType">
        <xs:restriction base="xs:normalizedString">
          <xs:minLength value="1"/>
          <xs:maxLength value="256"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="OptionalNameType">
        <xs:restriction base="xs:normalizedString">
          <xs:minLength value="0"/>
          <xs:maxLength value="256"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="RestrictedTermType">
        <xs:restriction base="xs:string">
          <xs:minLength value="1"/>
          <xs:maxLength value="512"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RulesType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Entity" type="mce:EntityType"/>
            <xs:element name="Affinity" type="mce:AffinityType"/>
          </xs:choice>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="Regex" type="mce:RegexType"/>
            <xs:element name="Keyword" type="mce:KeywordType"/>
          </xs:choice>
          <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="EntityType">
        <xs:sequence>
          <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
        <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
        <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
        <xs:attribute name="workload" type="mce:WorkloadType"/>
      </xs:complexType>
      <xs:complexType name="PatternType">
        <xs:sequence>
          <xs:element name="IdMatch" type="mce:IdMatchType"/>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
      </xs:complexType>
      <xs:complexType name="AffinityType">
        <xs:sequence>
          <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
        <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
        <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="workload" type="mce:WorkloadType"/>
      </xs:complexType>
      <xs:complexType name="EvidenceType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
      </xs:complexType>
      <xs:complexType name="IdMatchType">
        <xs:attribute name="idRef" type="xs:string" use="required"/>
      </xs:complexType>
      <xs:complexType name="MatchType">
        <xs:attribute name="idRef" type="xs:string" use="required"/>
      </xs:complexType>
      <xs:complexType name="AnyType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
        <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
      </xs:complexType>
      <xs:simpleType name="ProximityType">
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="ProbabilityType">
        <xs:restriction base="xs:integer">
          <xs:minInclusive value="1"/>
          <xs:maxInclusive value="100"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="WorkloadType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="Exchange"/>
          <xs:enumeration value="Outlook"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RegexType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="id" type="xs:token" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="KeywordType">
        <xs:sequence>
          <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:complexType>
      <xs:complexType name="GroupType">
        <xs:sequence>
          <xs:choice>
            <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="matchStyle" default="word">
          <xs:simpleType>
            <xs:restriction base="xs:NMTOKEN">
              <xs:enumeration value="word"/>
              <xs:enumeration value="string"/>
            </xs:restriction>
          </xs:simpleType>
        </xs:attribute>
      </xs:complexType>
      <xs:complexType name="TermType">
        <xs:simpleContent>
          <xs:extension base="mce:RestrictedTermType">
            <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="LocalizedStringsType">
        <xs:sequence>
          <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
            <xs:key name="UniqueLangCodeUsedInNamePerResource">
              <xs:selector xpath="mce:Name"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
            <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
              <xs:selector xpath="mce:Description"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
          </xs:element>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="ResourceType">
        <xs:sequence>
          <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
          <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="ResourceNameType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="default" type="xs:boolean" default="false"/>
            <xs:attribute name="langcode" type="mce:LangType" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="DescriptionType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="default" type="xs:boolean" default="false"/>
            <xs:attribute name="langcode" type="mce:LangType" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
    </xs:schema>

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

