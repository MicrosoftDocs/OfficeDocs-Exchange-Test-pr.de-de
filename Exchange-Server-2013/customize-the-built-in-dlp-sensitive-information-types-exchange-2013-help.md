---
title: 'Anpassen d. integrierten vertr. DLP-Informationstypen: Exchange 2013-Hilfe'
TOCTitle: Anpassen der integrierten vertraulichen DLP-Informationstypen
ms:assetid: 3f8bf141-2e7c-4ea7-b102-dfd6c41539da
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn781122(v=EXCHG.150)
ms:contentKeyID: 62757560
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anpassen der integrierten vertraulichen DLP-Informationstypen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-05-26_

Bei der Suche nach vertraulichen Informationen in E-Mails müssen Sie die in einer so genannten *Regel* enthaltenen Informationen beschreiben. DLP (Data Loss Prevention, Verhinderung von Datenverlust) umfasst ein Paket von 51 Regeln für die gängigsten vertraulichen Informationstypen, das Sie sofort nutzen können. Um diese Regeln zu verwenden, müssen Sie sie in eine Richtlinie aufnehmen. Möglicherweise möchten Sie die integrierten Regeln an die spezifischen Anforderungen Ihrer Organisation anpassen. Zu diesem Zweck können Sie benutzerdefinierte vertrauliche Informationstypen erstellen. In diesem Thema erfahren Sie, wie Sie die XML-Datei anpassen, die die vorhandene Regelsammlung enthält, damit ein größerer Bereich potenzieller Kreditkarteninformationen erkannt wird.

Dieses Beispiel können Sie auf weitere integrierte vertrauliche Informationstypen anwenden. Eine Liste der standardmäßigen vertraulichen Informationstypen und XML-Definitionen finden Sie unter [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md).

Dieses Thema umfasst die folgenden Abschnitte, die sich mit der Anpassung von XML-Regeln beschäftigen:

  - Export XML of current rules

  - Find the rule that you want to modify in the XML

  - Modify the XML and create a new sensitive information type

  - Require less additional evidence

  - Look for keywords that are specific to your organization

  - Upload your rule

Informationen zu den verschiedenen Teilen von Regeln und deren Funktionen finden Sie am Ende dieses Themas unter Term glossary.

## Exportieren der XML-Datei der aktuellen Regeln

Um die XML-Datei zu exportieren, verwenden Sie die Exchange-Verwaltungsshell oder . Weitere Informationen zu Exchange Server 2013 finden Sie unter [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)). Weitere Informationen zu Exchange Online finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)).

1.  Geben Sie in der Exchange-Verwaltungsshell- oder Exchange Online-PowerShell **Get-ClassificationRuleCollection** ein, um die Regeln Ihrer Organisation anzuzeigen. Falls Sie keine eigenen Regeln erstellt haben, werden nur die integrierten Standardregeln mit der Bezeichnung "Microsoft-Regelpaket" angezeigt.

2.  Speichern Sie die Regeln Ihrer Organisation in einer Variablen, indem Sie **$ruleCollections = Get-ClassificationRuleCollection** eingeben. Durch das Speichern in einer Variablen kann später problemlos auf die Daten in einem Format zugegriffen werden, das sich für Remote-PowerShell-Befehle eignet.

3.  Erstellen Sie eine formatierte XML-Datei mit all diesen Daten, indem Sie **Set-Content -path "C:\\custompath\\exportedRules.xml" -Encoding Byte -Value $ruleCollections.SerializedClassificationRuleCollection** eingeben. (**Set-content** ist der Teil des Cmdlets, das den XML-Code in die Datei schreibt.)
    

    > [!IMPORTANT]
    > Stellen Sie sicher, dass der Dateispeicherort verwendet wird, in dem das Regelpaket tatsächlich gespeichert ist. <STRONG>C:\custompath&#92;</STRONG> ist ein Platzhalter.



## Suchen der Regel, die in der XML-Datei geändert werden soll

Mit den obigen Cmdlets wurde die gesamte *Regelsammlung* exportiert, die die 51 Standardregeln umfasst. Anschließend müssen Sie speziell nach der Regel für die Kreditkartennummer suchen, die Sie ändern möchten.

1.  Verwenden Sie einen Texteditor, um die im vorherigen Abschnitt exportierte XML-Datei zu öffnen.

2.  Führen Sie einen Bildlauf bis zum Tag **\<Rules\>** durch, mit dem der Abschnitt beginnt, der die DLP-Regeln enthält. (Da diese XML-Datei die Informationen für die gesamte Regelsammlung enthält, sind am Anfang weitere Informationen enthalten, über die Sie hinweg blättern müssen, um zu den Regeln zu gelangen.)

3.  Suchen Sie nach **Func\_credit\_card**, um die Regeldefinition für die Kreditkartennummer zu suchen. (In der XML-Datei dürfen Regelnamen keine Leerzeichen enthalten, sodass die Leerzeichen üblicherweise durch Unterstriche ersetzt und die Regelnamen manchmal abgekürzt werden. Ein Beispiel hierfür ist die Regel für die US-Sozialversicherungsnummer, die als "SSN" abgekürzt wird. Die XML-Datei der Kreditkartennummer-Regel sollte wie das folgende Codebeispiel aussehen.
    
        <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
               patternsProximity="300" recommendedConfidence="85">
              <Pattern confidenceLevel="85">
               <IdMatch idRef="Func_credit_card" />
                <Any minMatches="1">
                  <Match idRef="Keyword_cc_verification" />
                  <Match idRef="Keyword_cc_name" />
                  <Match idRef="Func_expiration_date" />
                </Any>
              </Pattern>
            </Entity>

Nachdem Sie die Regeldefinition für die Kreditkartennummer in der XML-Datei ermittelt haben, können Sie die XML-Datei der Regel an Ihre Anforderungen anpassen. (Eine Wiederholung zu den XML-Definitionen finden Sie am Ende dieses Themas unter Term glossary.)

## Ändern der XML-Datei und Erstellen eines neuen vertraulichen Informationstyps

Zuerst müssen Sie einen neuen vertraulichen Informationstyp erstellen, da Sie die Standardregeln nicht direkt ändern können. Sie können eine Vielzahl von Maßnahmen im Zusammenhang mit benutzerdefinierten vertraulichen Informationstypen ergreifen. Diese werden unter [Entwickeln von Regelpaketen für sensible Informationen](technical-description-of-xml-schema-for-dlp-rule-packages.md) beschrieben. In diesem Beispiel machen wir es nicht kompliziert, sondern entfernen nur den bestätigenden Nachweis und fügen der Regel für die Kreditkartennummer Schlüsselwörter hinzu.

Alle XML-Regeldefinitionen werden anhand der folgenden allgemeinen Vorlage erstellt. Sie müssen die XML-Definition der Kreditkartennummer in der Vorlage kopieren und einfügen, einige Werte ändern (beachten Sie die Platzhalter ". . .” im folgenden Beispiel) und anschließend die geänderte XML-Datei als neue Regel hochladen, die in Richtlinien verwendet werden kann.

    <?xml version="1.0" encoding="utf-16"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
      <RulePack id=". . .">
        <Version major="1" minor="0" build="0" revision="0" />
        <Publisher id=". . ." /> 
        <Details defaultLangCode=". . .">
          <LocalizedDetails langcode=" . . . ">
             <PublisherName>. . .</PublisherName>
             <Name>. . .</Name>
             <Description>. . .</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
      
     <Rules>
       <!-- Paste the Credit Card Number rule definition here.--> 
    
          <LocalizedStrings>
             <Resource idRef=". . .">
               <Name default="true" langcode=" . . . ">. . .</Name>
               <Description default="true" langcode=". . ."> . . .</Description>
             </Resource>
          </LocalizedStrings>
    
       </Rules>
    </RulePackage>

Sie verfügen nun über eine XML-Datei, die der Folgenden ähnelt. Da Regelpakete und Regeln anhand ihrer eindeutigen GUIDs identifiziert werden, müssen Sie zwei GUIDs generieren: eine für das Regelpaket und eine zum Ersetzen der GUID für die Kreditkartennummer-Regel. (Die GUID für die Entitäts-ID im folgenden Codebeispiel ist die für unsere integrierte Regeldefinition, die Sie durch eine neue GUID ersetzen müssen.) Es gibt verschiedene Wege zum Generieren von GUIDs. Sie können dies jedoch unkompliziert in PowerShell bewerkstelligen, indem Sie **\[guid\]::NewGuid()** eingeben.

    <?xml version="1.0" encoding="utf-16"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
      <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
        <Version major="1" minor="0" build="0" revision="0" />
        <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
        <Details defaultLangCode="en">
          <LocalizedDetails langcode="en">
            <PublisherName>Contoso Ltd.</PublisherName>
            <Name>Financial Information</Name>
            <Description>Modified versions of the Microsoft rule package</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
      
     <Rules>
        <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
           patternsProximity="300" recommendedConfidence="85">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
            <Any minMatches="1">
              <Match idRef="Keyword_cc_verification" />
              <Match idRef="Keyword_cc_name" />
              <Match idRef="Func_expiration_date" />
            </Any>
          </Pattern>
        </Entity>
    
          <LocalizedStrings>
             <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f"> 
    <!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
               <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
               <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
             </Resource>
          </LocalizedStrings>
    
       </Rules>
    </RulePackage>

## Entfernen der Anforderung für einen bestätigenden Nachweis von einem vertraulichen Informationstyp

Nachdem ein neuer vertraulicher Informationstyp erstellt wurde, den Sie in Ihre Exchange-Umgebung hochladen können, besteht der nächste Schritte darin, spezifischere Angaben für die Regel festzulegen. Ändern Sie die Regel so, dass sie nur nach einer 16-stelligen Zahl sucht, die die Prüfsummenprüfung passiert, für die aber kein weiterer (bestätigender) Nachweis erforderlich ist (beispielsweise Schlüsselwörter). Hierfür müssen Sie den Teil der XML-Datei entfernen, der nach dem bestätigenden Nachweis sucht. Der bestätigende Nachweis ist sehr hilfreich bei der Verringerung falsch positiver Ergebnisse, da sich üblicherweise bestimmte Schlüsselwörter oder ein Ablaufdatum in der Nähe der Kreditkartennummer befinden. Wenn Sie den Nachweis entfernen, sollten Sie auch anpassen, wie sicher Sie sind, dass Sie eine Kreditkartennummer gefunden haben, indem Sie das **confidenceLevel** senken (in dem Beispiel ist dies 85).

    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
          </Pattern>
        </Entity>

## Suchen nach Schlüsselwörtern speziell für Ihre Organisation

Sie möchten möglicherweise festlegen, dass der bestätigende Nachweis erforderlich ist, aber andere oder zusätzliche Schlüsselwörter angeben. Möglicherweise möchten Sie auch ändern, wo nach diesem Nachweis gesucht werden soll. Sie können das Attribut **patternsProximity** anpassen, um das Fenster für den bestätigenden Nachweis um die 16-stellige Zahl herum zu erweitern oder zu verkleinern. Um Ihre eigenen Schlüsselwörter hinzuzufügen, müssen Sie eine Schlüsselwortliste definieren und in Ihrer Regel darauf verweisen. Mit der folgenden XML-Datei werden die Schlüsselwörter "company card" (Firmenkarte) und "Contoso card" (Contoso-Karte) hinzugefügt, sodass jede Nachricht, die diese Phrasen im Umkreis von 150 Zeichen von einer Kreditkartennummer enthält, als Kreditkartennummer erkannt wird.

    <Rules>
    <! -- Modify the patternsProximity to be "150" rather than "300." -->
        <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
            <Any minMatches="1">
              <Match idRef="Keyword_cc_verification" />
              <Match idRef="Keyword_cc_name" />
    <!-- Add the following XML, which references the keywords at the end of the XML sample. -->
              <Match idRef="My_Additional_Keywords" />
              <Match idRef="Func_expiration_date" />
            </Any>
          </Pattern>
        </Entity>
    <!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
        <Keyword id="My_Additional_Keywords">
          <Group matchStyle="word">
            <Term caseSensitive="false">company card</Term>
            <Term caseSensitive="false">Contoso card</Term>
          </Group>
        </Keyword>

## Hochladen der Regel

Zum Hochladen der Regel müssen Sie wie folgt vorgehen.

1.  Speichern Sie sie als XML-Datei mit Unicode-Codierung. Dies ist wichtig, da die Regel nicht funktioniert, wenn die Datei mit einer anderen Codierung gespeichert wird.

2.  Stellen Sie eine Verbindung mit der Exchange-Verwaltungsshell- oder der Exchange Online-PowerShell her. Weitere Informationen zu Exchange Server 2013 finden Sie unter [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)). Weitere Informationen zu Exchange Online finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)).

3.  Geben Sie in der Exchange-Verwaltungsshell- oder der Exchange Online-PowerShell **New-ClassificationRuleCollection -FileData (Get-Content -Path "C:\\custompath\\MyNewRulePack.xml " -Encoding Byte)** ein.
    

    > [!IMPORTANT]
    > Stellen Sie sicher, dass der Dateispeicherort verwendet wird, in dem das Regelpaket tatsächlich gespeichert ist. <STRONG>C:\custompath\</STRONG> ist ein Platzhalter.



4.  Geben Sie zur Bestätigung **Y** ein, und drücken Sie die EINGABETASTE.

5.  Überprüfen Sie, ob die neue Regel hochgeladen wurde, indem Sie **Get-DataClassification** eingeben. Daraufhin wird der Name der Regel angezeigt.

Sie müssen die Regel einer DLP-Richtlinie hinzufügen, um damit zu beginnen, die Regel zum Erkennen vertraulicher Informationen zu verwenden. Informationen zum Hinzufügen einer Regel zu einer Richtlinie finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md).

## Glossar

Nachfolgend finden Sie Definitionen der Begriffe, die in diesem Verfahren vorkommen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Begriff</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Entität</p></td>
<td><p>Entitäten sind vertrauliche Informationstypen, wie beispielsweise Kreditkartennummern. Jede Entität verfügt über eine eindeutige GUID als ID. Wenn Sie eine GUID kopieren und in der XML-Datei danach suchen, finden Sie die XML-Regeldefinition und alle lokalisierten Übersetzungen dieser XML-Regel. Diese Definition können Sie auch finden, indem Sie die GUID für die Übersetzung ermitteln und dann nach dieser GUID suchen.</p></td>
</tr>
<tr class="even">
<td><p>Funktionen</p></td>
<td><p>Die XML-Datei verweist auf <strong>Func_credit_card</strong>, eine Funktion im kompilierten Code. Funktionen dienen zur Ausführung komplexer regulärer Ausdrücke und prüfen, ob Prüfsummen mit den integrierten Regeln übereinstimmen. Da dies im Code geschieht, werden einige der Variablen nicht in der XML-Datei angezeigt.</p></td>
</tr>
<tr class="odd">
<td><p>IdMatch</p></td>
<td><p>Dies ist die Kennung, die das Muster abgleichen möchte – beispielsweise eine Kreditkartennummer. Mehr Informationen zu diesem Thema und zu den <strong>Match</strong>-Tags finden Sie unter <a href="technical-description-of-xml-schema-for-dlp-rule-packages.md">Entity rules</a>.</p></td>
</tr>
<tr class="even">
<td><p>Schlüsselwortliste</p></td>
<td><p>Die XML-Datei verweist außerdem auf <strong>keyword_cc_verification</strong> und <strong>keyword_cc_name</strong>. Dies sind Schlüsselwortlisten, anhand derer nach Übereinstimmungen mit dem Attribut <strong>patternsProximity</strong> für die Entität gesucht wird. Diese werden zurzeit nicht in der XML-Datei angezeigt.</p></td>
</tr>
<tr class="odd">
<td><p>Muster</p></td>
<td><p>Das Muster enthält die Liste der Informationen, anhand derer der vertrauliche Informationstyp sucht. Hierzu zählen Schlüsselwörter, reguläre Ausdrücke und interne Funktionen (die Aufgaben ausführen, wie beispielsweise die Überprüfung von Prüfsummen). Vertrauliche Informationstypen können mehrere Muster mit eindeutigen Angaben zur Vertrauenswürdigkeit aufweisen. Dies ist nützlich, wenn ein vertraulicher Informationstyp erstellt wird, der eine hohe Vertrauenswürdigkeit zurückgibt, falls ein bestätigender Nachweis gefunden wurde, und der eine niedrige Vertrauenswürdigkeit zurückgibt, wenn nur ein geringer oder gar kein bestätigender Nachweis gefunden wurde.</p></td>
</tr>
<tr class="even">
<td><p>Pattern confidenceLevel</p></td>
<td><p>Dies ist die Vertrauensstufe, für die das DLP-Modul eine Übereinstimmung gefunden hat. Diese Vertrauensstufe wird einer Übereinstimmung für das Muster zugeordnet, wenn die Anforderungen des Musters erfüllt sind. Es handelt sich hierbei um das Maß an Vertrauenswürdigkeit, das Sie bei Verwendung von Exchange-Transportregeln (ETRs) erwägen sollten.</p></td>
</tr>
<tr class="odd">
<td><p>patternsProximity</p></td>
<td><p>Wird etwas gefunden, das wie ein Kreditkartennummer-Muster aussieht, handelt es sich bei dem Attribut <strong>patternsProximity</strong> um die Umgebung der Nummer, in der nach einem bestätigenden Nachweis gesucht wird.</p></td>
</tr>
<tr class="even">
<td><p>recommendedConfidence</p></td>
<td><p>Dies ist die Vertrauensstufe, die für diese Regel empfohlen wird. Die empfohlene Vertrauensstufe gilt für Entitäten und Affinitäten. Für Entitäten wird diese Zahl niemals anhand des Attributs <strong>confidenceLevel</strong> für das Muster ausgewertet. Es ist lediglich eine Empfehlung, die Ihnen bei der Auswahl einer Vertrauensstufe helfen soll, falls Sie eine solche zuweisen möchten. Für Affinitäten muss das Attribut <strong>confidenceLevel</strong> des Musters höher sein als die Zahl des Attributs <strong>recommendedConfidence</strong> für eine aufzurufende ETR-Aktion. Das Attribut <strong>recommendedConfidence</strong> ist die in ETRs verwendete Standardvertrauensstufe, die eine Aktion aufruft. Bei Bedarf können Sie stattdessen die aufzurufende ETR manuell basierend auf der Vertrauensstufe des Musters ändern.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

  - [Anwenden von DLP-Regeln zur Auswertung von Nachrichten](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/dlp-rule-application)

  - [Erstellen einer benutzerdefinierten DLP-Richtlinie](create-a-custom-dlp-policy-exchange-2013-help.md)

  - [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

