---
title: Handbuch zu XML-Regelschemas und -Regelstrukturen für DLP-Richtliniendateien
TOCTitle: Entwickeln von Vorlagendateien für DLP-Richtlinien
ms:assetid: 4b263547-aef4-4ee8-aa4f-fa64a5863189
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674703(v=EXCHG.150)
ms:contentKeyID: 50475625
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entwickeln von Vorlagendateien für DLP-Richtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In dieser Übersicht werden die Komponenten einer XML-Schemadefinition für Richtlinienvorlagendateien zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) erläutert, und es wird eine Beispielrichtliniendatei im XML-Format bereitgestellt. Bevor Sie beginnen, sollten Sie sich mit den Grundlagen der DLP-Architektur und der Regelentwicklung vertraut machen. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md) und [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

Zur einfachen Einführung und Verwaltung von DLP-Lösungen wurde in Microsoft Exchange Server 2013 ein konzeptionelles Modell aus DLP-Richtlinien und -Richtlinienvorlagen eingeführt. DLP-Richtlinienvorlagen bieten einen vorläufigen Entwurf für die beabsichtigte DLP-Richtlinie. Um von Nutzen zu sein, muss eine DLP-Richtlinienvorlage alle Direktiven und Datenobjekte kapseln, die zur Erfüllung eines spezifischen Richtlinienziels benötigt werden, beispielsweise eine Vorschrift oder eine Geschäftsanforderung. Die Vorlage ist nicht an eine bestimmte Umgebung gebunden. Es handelt sich lediglich um eine Definition oder ein Modell einer Richtlinie, die als Bestandteil der Produktkonfiguration oder über unabhängige Softwareanbieter und Partner bereitgestellt werden kann. DLP-Richtlinien hingegen sind Laufzeitinstanzen der Vorlagen, die speziell auf die Bereitstellungsumgebung abgestimmt sind. DLP-Richtlinien können über die Verwendung von Transportregeln in Ihr vorhandenes Framework für Messagingrichtlinien eingebunden werden. Transportregeln bieten große Flexibilität bei der Anpassung und Umsetzung aller Aspekte Ihrer DLP-Lösungen.

## Quellen und Struktur für Richtlinienvorlagen

DLP-Richtlinienvorlagen werden üblicherweise über mehrere Quellen beeinflusst, beispielsweise durch serverbasierte Verarbeitungsdirektiven, Clientcomputerrichtlinien oder weitere Richtlinienkonstrukten, wie nachfolgend dargestellt wird:

![Faktoren mit Auswirkung auf Richtlinienvorlagen](images/JJ674703.12f48e4f-d7b8-4ddd-87e8-8477983252ec(EXCHG.150).gif "Faktoren mit Auswirkung auf Richtlinienvorlagen")

Einfache Verwaltungsaufgaben für DLP-Richtlinienvorlagen können sowohl über die Exchange-Verwaltungsshell als auch über internetbasierte Schnittstellen durchgeführt werden, z. B. über die Exchange-Verwaltungskonsole, die Funktionen für Import, Export, Löschvorgänge und Abfragen bietet. Eine DLP-Richtlinie wird erstellt, indem während der Erstellung eine DLP-Richtlinienvorlage referenziert wird. Diese referenzierten DLP-Richtlinienvorlagen können im System installierte Vorlagen sein, die in Active Directory-Domänendiensten gespeichert sind, oder sie können als direkte Eingabe aus extern bereitgestellten Richtlinien zur Verfügung stehen.

DLP-Richtlinienvorlagen werden als XML-Dokumente dargestellt. Ein einzelnes XML-Schema wird für sowohl für innerhalb von Exchange bereitgestellte als auch für extern bereitgestellte Richtlinien verwendet. Die konzeptionelle Struktur des XML-Dokuments wird in der folgenden Tabelle dargestellt, in der die wichtigsten Elemente aufgeführt werden. Mithilfe des Satzes an Definitionen für Richtlinienkomponenten können Sie ein spezifisches Richtlinienziel erreichen, beispielsweise eine Vorschrift oder eine Geschäftsanforderung.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Strukturelement</th>
<th>Bedeutung oder Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Herausgeber</p></td>
<td><p>Microsoft oder Partner</p></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>15.0.1.0</p></td>
</tr>
<tr class="odd">
<td><p>Policy Name</p></td>
<td><p>PCI-DSS</p></td>
</tr>
<tr class="even">
<td><p>Description</p></td>
<td><p>Die DLP-Richtlinie &quot;PCI-DSS&quot; hilft bei der Erkennung von Informationen, die dem PCI Data Security Standard (PCI DSS) unterliegen. Dazu zählen Kredit- und Debitkartennummern. Die Nutzung dieser Richtlinie stellt nicht die Einhaltung von Bestimmungen sicher. Nehmen Sie nach Abschluss der Testphase die erforderlichen Konfigurationsänderungen in Exchange vor, damit die Übertragung von Informationen mit den Richtlinien Ihrer Organisation übereinstimmt. Beispiele dafür sind die Konfiguration von TLS mit bekannten Geschäftspartnern oder die Hinzufügung restriktiverer Transportregelaktionen, z. B. die Hinzufügung eines Rechteschutzes zu Nachrichten, die diesen Datentyp enthalten.</p></td>
</tr>
<tr class="odd">
<td><p>Metadata</p></td>
<td><p>Tags zum Beschreiben von lokalen Vorschriften, Land oder Region, Schlüsselwörtern usw.</p></td>
</tr>
<tr class="even">
<td><p>Set of policy constructs</p></td>
<td><ol>
<li><p>Definitionen für Transportregeln, z. B. Bedingungen und Aktionen.</p></li>
<li><p>Definitionen für das E-Mail-Clientverhalten, die das Clientverhalten über interaktive Benachrichtigungen steuern.</p></li>
<li><p>(Optional) Konfigurationsreferenzen, die auf die spezifischen Einstellungen der Clientumgebung abgestimmt werden müssen.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Set of data classifications</p></td>
<td><ol>
<li><p>Gibt Klassifikationsentitäten oder Affinitäten an.</p></li>
<li><p>Entitäten weisen Anzahl und Bewertung auf, Affinitäten ausschließlich eine Bewertung.</p></li>
<li><p>Umfasst einen eigenen Satz an Eigenschaften und ein Klassifikationsschema.</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Definition des Formats für Richtlinienvorlagen

DLP-Richtlinienvorlagen werden als XML-Dokumente dargestellt, die dem folgenden Schema entsprechen. Bei XML wird zwischen Groß- und Kleinschreibung unterschieden. `dlpPolicyTemplates` funktioniert beispielsweise, `DlpPolicyTemplates` dagegen nicht.

    <?xml version="1.0" encoding="UTF-8"?>
    <dlpPolicyTemplates>
      <dlpPolicyTemplate id="F7C29AEC-A52D-4502-9670-141424A83FAB" mode="Audit" state="Enabled" version="15.0.2.0">
        <contentVersion>4</contentVersion>
        <publisherName>Microsoft</publisherName>
        <name>
          <localizedString lang="en">PCI-DSS</localizedString>
        </name>
        <description>
          <localizedString lang="en">Detects the presence of information subject to Payment Card Industry Data Security Standard (PCI-DSS) compliance requirements.</localizedString>
        </description>
        <keywords></keywords>
        <ruleParameters></ruleParameters>
        <ruleParameters/>
        <policyCommands>
          <!-- The contents below are applied/executed as rules directly in PS - -->
          <commandBlock>
            <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Outside" -DlpPolicy "%%DlpPolicyName%%" -SentToScope NotInOrganization -SetAuditSeverity High -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } -Comments "Monitors payment card information sent to outside the organization as part of the PCI-DSS DLP Policy."]]>
          </commandBlock>
          <commandBlock>
            <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "%%DlpPolicyName%%" -Comments "Monitors payment card information sent inside the organization as part of the PCI-DSS DLP Policy." -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]>
          </commandBlock>
        </policyCommands>
        <policyCommandsResources></policyCommandsResources>
      </dlpPolicyTemplate>
    </dlpPolicyTemplates>

Wenn ein Parameter, den Sie in Ihre XML-Datei für ein Element aufnehmen, ein Leerzeichen enthält, muss der Parameter in doppelte Anführungszeichen eingeschlossen sein, um ordnungsgemäß zu funktionieren. Im nachfolgenden Beispiel ist der Parameter nach `-SentToScope` zulässig und benötigt keine doppelten Anführungszeichen, weil es sich um eine durchgängige Zeichenfolge ohne Leerzeichen handelt. Der für –`Comments` bereitgestellte Parameter wird in der Exchange-Verwaltungskonsole hingegen nicht angezeigt, weil er Leerzeichen enthält und nicht in Anführungszeichen eingeschlossen ist.

    <CommandBlock><![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "PCI-DSS" -Comments Monitors payment card information sent inside the organization -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]> </CommandBlock>

## localizedString Element

Das Vorlagenformat bietet die Möglichkeit zur Lokalisierung von Zeichenfolgen in der Vorlage, die möglicherweise dem Endbenutzer angezeigt werden – beispielsweise bei der Auswahl der zu installierenden DLP-Richtlinienvorlagen. Das localizedString-Element kann zur Bereitstellung mehrerer Definitionen für die Namens- und Beschreibungsfelder verwendet werden.

## ruleParameters Node

Hierbei handelt es sich um einen optionalen Satz an Parametern, die während der Vorlageninstanziierung beim Erstellen einer DLP-Richtlinie für die Zuordnung zu bereitstellungsspezifischen Objekten angegeben werden müssen. Beispielsweise kann dies eine tatsächliche Verteilergruppe sein, die in der Bereitstellung verfügbar ist.

## dlpPolicyTemplate Element

Dies ist das Stammelement für die DLP-Richtlinienvorlage, dieses ist für jede Vorlage erforderlich. In der folgenden Tabelle werden die verfügbaren Attribute aufgeführt:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Attributname</th>
<th>Erforderlich?</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Ja</p></td>
<td><p>Die Versionsnummer, die in diesem DLP-Richtlinienvorlagendokument verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>State</p></td>
<td><p>Nein</p></td>
<td><p>(Optional) Standardkonfiguration für den Status der Richtlinie.</p></td>
</tr>
<tr class="odd">
<td><p>Mode</p></td>
<td><p>Nein</p></td>
<td><p>(Optional) Standardkonfiguration für den Modus der Richtlinie.</p></td>
</tr>
<tr class="even">
<td><p>Id</p></td>
<td><p>Nein</p></td>
<td><p>Eine GUID zur eindeutigen Identifizierung dieser DLP-Richtlinienvorlagendefinition im folgenden Format: &quot;A29C69BF-4F98-47F1-9A99-5771DFD2C27F&quot;.</p></td>
</tr>
</tbody>
</table>


Untergeordnete Elemente enthalten die nachstehende Abfolge von Elementen.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnetes Element</th>
<th>(Mindestwert, Maximalwert)</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PublisherName</p></td>
<td><p>(1, 1)</p></td>
<td><p>Metadaten für den Herausgeber der Vorlage</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>(1, 1)</p></td>
<td><p>Lokalisierbarer Name für diese Vorlage.</p></td>
</tr>
<tr class="odd">
<td><p>Description</p></td>
<td><p>(1, 1)</p></td>
<td><p>Lokalisierbare Beschreibung für diese Vorlage.</p></td>
</tr>
<tr class="even">
<td><p>Keywords</p></td>
<td><p>(1, 1)</p></td>
<td><p>Liste der Schlüsselwörter, die für diese Vorlage gelten. Eine Vorlage kann eine leere Schlüsselwortliste umfassen.</p></td>
</tr>
<tr class="odd">
<td><p>RuleParameters</p></td>
<td><p>(0, 1)</p></td>
<td><p>Liste der Vorlagenparameter, die in der Richtliniendefinition verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>PolicyCommands</p></td>
<td><p>(0, 1)</p></td>
<td><p>Liste der Transportregeldefinitionen für diese Richtlinie. Dies ist ein optionales Element.</p></td>
</tr>
</tbody>
</table>


## DLP-Richtlinienvorlage: PolicyCommands

Dieser Bestandteil der Richtlinienvorlage enthält die Liste der Befehle für die Exchange-Verwaltungsshell, die zum Instanziieren der Richtliniendefinition verwendet werden. Der Importvorgang führt jeden der Befehle als Bestandteil der Instanziierung aus. Nachfolgend finden Sie einige Beispielbefehle für Richtlinien.

    <PolicyCommands>
        <!-- The contents below are applied/executed as rules directly in PS - -->
          <CommandBlock> <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Outside" -DlpPolicy "PCI-DSS" -SentToScope NotInOrganization -SetAuditSeverity High -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } -Comments "Monitors payment card information sent to outside the organization as part of the PCI-DSS DLP policy."]]></CommandBlock>
          <CommandBlock><![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "PCI-DSS" -Comments "Monitors payment card information sent inside the organization as part of the PCI-DSS DLP policy." -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]> </CommandBlock>
      </PolicyCommands> 

Das Format der Cmdlets entspricht der Standardsyntax für Cmdlets der Exchange-Verwaltungsshell. Die Befehle werden nacheinander ausgeführt. Jeder Befehlsknoten kann einen Skriptblock umfassen, der mehrere Befehle enthalten kann. Das nachstehende Beispiel zeigt, wie ein Klassifikationsregelpaket in eine DLP-Richtlinienvorlage eingebettet und das Regelpaket im Rahmen der Richtlinienerstellung installiert wird. Das Klassifikationsregelpaket wird in die Richtlinienvorlage eingebettet und anschließend als Parameter an das Cmdlet in der Vorlage übergeben:

``` 
<CommandBlock>
  <![CDATA[
$rulePack = [system.Text.Encoding]::Unicode.GetBytes('<?xml version="1.0" encoding="utf-16"?>
<rulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">

  <RulePack id="c3f021a3-c265-4dc2-b3a7-41a1800bf518">
    <Version major="1" minor="0" build="0" revision="0"/>
    <Publisher id="e17451d3-9648-4117-a0b1-493a6d5c73ad"/>
    <Details defaultLangCode="en-us">
      <LocalizedDetails langcode="en-us">
        <PublisherName>Contoso</PublisherName>
        <Name>Contoso Sample Rule Pack</Name>
        <Description>This is a sample rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

  <Rules>
    <Entity id="7cc35258-6b35-4415-baff-a76d1a018980" patternsProximity="300" recommendedConfidence="85" workload="Exchange">     

      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_Contoso" />
        <Any minMatches="1">
          <Match idRef="Regex_conf" />
        </Any>
      </Pattern>
    </Entity>

    <Regex id="Regex_Contoso">(?i)(\bContoso\b)</Regex>
    <Regex id="Regex_conf">(?i)(\bConfidential\b)</Regex>

    <LocalizedStrings>
      <Resource idRef="7cc35258-6b35-4415-baff-a76d1a018980">
        <Name default="true" langcode="en-us">
          Confidential Information Rule
        </Name>
        <Description default="true" langcode="en-us">
          Sample rule pack - Detects Contoso confidential information
        </Description>
      </Resource>
    </LocalizedStrings>
  </Rules>

</RulePackage>

')


New-ClassificationRuleCollection -FileData $rulePack 
New-TransportRule -name "customEntity" -DlpPolicy "%%DlpPolicyName%%" -SentToScope NotInOrganization -MessageContainsDataClassifications @{Name="Confidential Information Rule"} -SetAuditSeverity High]]>
</CommandBlock> 
```

Untergeordnete Elemente enthalten die folgenden Abfolge von Elementen.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnetes Element</th>
<th>(Mindestwert, Maximalwert)</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CommandBlock</p></td>
<td><p>(1, n)</p></td>
<td><p>Ein Befehlsblock, der in der PowerShell ausgeführt wird. Die Befehlsblöcke werden nach der Reihe ausgeführt.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

[Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

