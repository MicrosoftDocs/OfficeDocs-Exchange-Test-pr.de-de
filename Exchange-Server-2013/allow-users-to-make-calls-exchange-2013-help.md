---
title: 'Autorisieren von Benutzern für Anrufe: Exchange 2013 Help'
TOCTitle: Autorisieren von Benutzern für Anrufe
ms:assetid: b6e696ce-c848-475b-a598-9035677497e2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232172(v=EXCHG.150)
ms:contentKeyID: 51409333
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Autorisieren von Benutzern für Anrufe

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

*Outdialing* wird der Vorgang genannt, bei dem sich Benutzer über eine Outlook Voice Access-Nummer in einen UM-Wählplan einwählen und einen Anruf einer internen oder externen Telefonnummer einleiten oder diesen weiterleiten. Unified Messaging verwendet viele Outdialingeinstellungen, um Anrufe für Benutzer zu tätigen. Zum Konfigurieren des Outdialings müssen Sie Wählregeln, Wählregelgruppen und Wählautorisierungen für Unified Messaging-Wählpläne (UM) konfigurieren und anschließend das Outdialing für UM-Wählpläne, UM-Postfachrichtlinien und automatische Telefonzentralen autorisieren. Darüber hinaus können Sie UM-Wählpläne so konfigurieren, dass sie über Kurzwahlnummern oder Zugriffscodes, ein nationales Rufnummernpräfix und ein nationales/regionales bzw. internationales Nummernformat verfügen, mit deren Hilfe Sie das Outdialing in Ihrer Organisation steuern können. In diesem Thema werden Wählregeln, Wählregelgruppen und Wählautorisierungen sowie deren Verwendung zur Autorisierung und Steuerung des Outdialings in Ihrer Organisation behandelt.

**Inhalt**

Übersicht

Benutzertypen

Outdialingeinstellungen

Konfigurieren des Outdialings

Anwenden konfigurierter Wählregelgruppen

Anwenden von Wählregeln

## Übersicht

Outdialing passiert, wenn:

  - Ein Anruf einer externen Telefonnummer eingeleitet wird.

  - Ein Anruf an eine automatische Telefonzentrale weitergeleitet wird.

  - Ein Anruf an einen Benutzer in Ihrer Organisation weitergeleitet wird.

  - Ein UM-aktivierter Benutzer die Funktion "Wiedergabe über Telefon" verwendet.

Damit das Outdialing ordnungsgemäß funktioniert, müssen folgende Einstellungen richtig konfiguriert sein:

  - **Wählregeln**   Wählregeln definieren die Nummer, die vom UM-aktivierten Benutzer gewählt wird, sowie die Nummer, die von der Nebenstellenanlage bzw. IP-Nebenstellenanlage gewählt wird.

  - **Wählregelgruppen**   Wählregelgruppen bestimmen die Arten der Anrufe, die Benutzer innerhalb einer Wählgruppe tätigen können.

  - **Wählautorisierungen**   Wählautorisierungen bestimmen die Einschränkungen, die aktiviert werden, um zu verhindern, dass Benutzer unnötige Telefongebühren verursachen oder Ferngespräche führen.

Zum Aktivieren des Outdialings für Benutzer, die sich in einen Wählplan oder eine automatische Telefonzentrale einwählen, führen Sie die folgenden Schritte aus.

  - Vergewissern Sie sich, dass die VoIP-Gateways von einem UM-IP-Gateway abgebildet werden, das mit einem Wählplan verknüpft ist, der ausgehende Anrufe zulässt.

  - Erstellen Sie Wählregelgruppen, indem Sie Wählregeln für den UM-Wählplan definieren.

  - Fügen Sie Wählautorisierungen für nationale/regionale und internationale Wählregelgruppen für den UM-Wählplan, die UM-Postfachrichtlinie oder automatische Telefonzentrale hinzu, der/die demselben Wählplan wie das UM-IP-Gateway zugeordnet ist.

## Benutzertypen

Zwei Typen von Benutzern können die Outdialingfunktion in Unified Messaging verwenden: authentifizierte Benutzer und nicht authentifizierte Benutzer. Alle Benutzer, die bei einer automatischen UM-Telefonzentrale anrufen, sind nicht authentifiziert. Wenn Benutzer eine Outlook Voice Access-Nummer anrufen, gelten sie als nicht authentifiziert, weil sie nicht ihre Durchwahlnummer und PIN angegeben und sich nicht bei ihrem Postfach angemeldet haben. Benutzer sind authentifiziert, nachdem sie ihre Durchwahlnummer und PIN angegeben und sich erfolgreich bei ihrem Postfach angemeldet haben.

Wenn Benutzer eine Outlook Voice Access-Nummer anrufen, die in einem UM-Wählplan konfiguriert ist, und versuchen, einen Anruf einzuleiten oder weiterzuleiten, ohne sich bei ihrem Postfach anzumelden, werden nur die Outdialingeinstellungen des UM-Wählplans auf den Anruf angewendet. Wenn ein anonymer oder nicht authentifizierter Benutzer eine automatische UM-Telefonzentrale anruft, werden sowohl die für die automatische Telefonzentrale als auch die im der automatischen Telefonzentrale zugeordneten Wählplan konfigurierten Outdialingeinstellungen auf den Anruf angewendet.

Wenn Benutzer eine Outlook Voice Access-Nummer anrufen, die in einem Wählplan konfiguriert ist, und sich erfolgreich bei ihrem Postfach anmelden, gelten sie als authentifiziert. Nach ihrer Authentifizierung werden in den Anrufeinstellungen für das Outdialing die Wählregel- und Wählautorisierungseinstellungen in der UM-Postfachrichtlinie verwendet, die mit diesen Benutzern verknüpft ist.

Zurück zum Seitenanfang

## Outdialingeinstellungen

Sie müssen mehrere Einstellungen konfigurieren, um Outdialingregeln für Ihre Organisation zu aktivieren. Zusätzlich zur Konfiguration der UM-Wählpläne, automatischen UM-Telefonzentralen und UM-Postfachrichtlinien, die Sie mit den ordnungsgemäßen Wählregeln und -autorisierungen erstellt haben, müssen Sie Kurzwahlnummern, Nummernpräfixe und -formate in den UM-Wählplänen konfigurieren. Folgende Outdialingeinstellungen werden für Wählpläne, automatische Telefonzentralen und UM-Postfachrichtlinien konfiguriert:

  - Amtskennziffer, nationale/regionale und internationale Zugriffscodes

  - Nationales Rufnummernpräfix

  - Nationale/regionale und internationale Nummernformate

  - Konfigurierte nationale/regionale und internationale Wählregelgruppen

  - Zulässige nationale/regionale und internationale Wählregelgruppen

  - Wählregeleinträge

  - Wählautorisierungen

Damit Sie das Outdialing erfolgreich für Ihre Organisation konfigurieren können, müssen Sie zunächst die Einsatzmöglichkeiten jeder Komponente beim Outdialing kennen und wissen, wie diese zu konfigurieren sind. In der folgenden Tabelle werden alle Komponenten vorgestellt, die für UM-Wählpläne, automatische UM-Telefonzentralen und UM-Postfachrichtlinien konfiguriert sein müssen, damit das Outdialing ordnungsgemäß funktioniert.

### Outdialingkomponenten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kurzwahlnummern, Rufnummernpräfixe und Nummernformate</p></td>
<td><p>UM verwendet beim Einleiten eines ausgehenden Anrufs Kurzwahlnummern, Rufnummernpräfixe und Nummernformate zum Bestimmen der zu wählenden Nummer. Sie können Kurzwahlnummern, Rufnummernpräfixe und Nummernformate so konfigurieren, dass ausgehende Anrufe von Benutzern, die bei einer automatischen UM-Telefonzentrale anrufen, die einem UM-Wählplan zugeordnet ist, oder von Benutzern, die die im Wählplan konfigurierte Outlook Voice Access-Nummer anrufen, eingeschränkt werden.</p></td>
</tr>
<tr class="even">
<td><p>Wählregelgruppen</p></td>
<td><p>Wählregelgruppen werden erstellt, um Rufnummern ändern zu können, bevor sie bei ausgehenden Anrufen an die Nebenstellenanlage gesendet werden. Wählregelgruppen entfernen Nummern aus Rufnummern, die von UM angerufen werden, oder fügen diesen Nummern hinzu. So können Sie beispielsweise eine Wählregelgruppe erstellen, die einer 7-stelligen Rufnummer automatisch eine 0 als Präfix hinzufügt, um den Zugriff auf eine Amtsleitung zu gewähren. In diesem Beispiel müssen Benutzer, die ausgehende Anrufe tätigen, keine 0 vorwählen, um die externe Rufnummer einer Person außerhalb der Organisation zu erreichen.</p>
<p>Jede Wählregelgruppe enthält Wählregeln, die die Arten von Inlands-, Fern- und Auslandsgesprächen bestimmen, die Benutzer innerhalb einer Wählregelgruppe tätigen können. Wählregelgruppen gelten für die Benutzer, die einem UM-Wählplan zugeordnet sind, oder für automatische UM-Telefonzentralen und UM-Postfachrichtlinien, die dem UM-Wählplan zugeordnet sind. Jede Wählregelgruppe muss mindestens eine Wählregel enthalten.</p></td>
</tr>
<tr class="odd">
<td><p>Wählregeleinträge</p></td>
<td><p>Mithilfe einer Wählregel wird die Art der Anrufe bestimmt, die Benutzer innerhalb einer Wählregelgruppe tätigen können. Beim Erstellen einer Wählregelgruppe konfigurieren Sie mindestens eine Wählregel.</p>
<p>Beim Konfigurieren einer Wählregel müssen Sie deren Namen, ein umzuwandelndes Nummernmuster (die <em>Nummernmaske</em>) und die gewählte Nummer eingeben. Zusätzlich können Sie auch einen Kommentar eingeben. Mithilfe von Kommentaren können Sie beschreiben, wie die Wählregel verwendet wird, oder eine Gruppe von Benutzern benennen, für die die Wählregel gilt. Wenn Sie einer Wählregel eine Nummernmaske und die gewählte Nummer hinzufügen, können Sie den Buchstaben &quot;x&quot; durch eine Ziffer einer Rufnummer ersetzen, beispielsweise 01425xxxxxxx. Sie können auch ein Sternchen (*) als Platzhalterzeichen verwenden, z. B. 01425*.</p></td>
</tr>
<tr class="even">
<td><p>Wählautorisierungen</p></td>
<td><p>Eine Wählautorisierung verwendet Wählregelgruppen, um Wähleinschränkungen für Benutzer anzuwenden, die einer bestimmten UM-Postfachrichtlinie, einem UM-Wählplan oder einer automatischen Telefonzentrale zugeordnet sind. Wähleinschränkungen können ebenfalls verwendet werden, um Benutzern Anrufe an nationale/regionale bzw. internationale Rufnummern zu gestatten.</p>
<p>Nachdem Sie die Wählregeln für einen UM-Wählplan erstellt haben, fügen Sie die Wählregelgruppe einer UM-Postfachrichtlinie, einem Wählplan oder einer automatischen Telefonzentrale hinzu. Im Anschluss an das Hinzufügen der Wählregelgruppe zu einer UM-Postfachrichtlinie gelten alle definierten Einstellungen bzw. Regeln für UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Konfigurieren des Outdialings

Eine Wählregelgruppe ist eine Sammlung mit mindestens einer Wählregel, die für einen UM-Wählplan konfiguriert ist. Zwei Arten von Wählregelgruppen können für UM-Wählpläne konfiguriert werden: national/regional und international. Nationale/regionale Wählregelgruppen gelten für Rufnummern, die innerhalb desselben Landes bzw. derselben Region gewählt werden. Internationale Wählregelgruppen gelten für internationale Rufnummern, die aus einem Land bzw. einer Region in einem anderen Land bzw. einer anderen Region gewählt werden.

Jeder Wählplan kann mindestens eine Wählregelgruppe enthalten. Um eine Wählregelgruppe auf eine Gruppe von Benutzern anzuwenden, müssen Sie nach dem Erstellen der Wählregelgruppe diese der Liste der zulässigen Wählregelgruppen für den UM-Wählplan und für die automatischen UM-Telefonzentralen und UM-Postfachrichtlinien hinzufügen, die dem UM-Wählplan zugeordnet sind.

Wählregelgruppen ermöglichen Ihnen das Angeben von Wählregeln, die auf eine Gruppe UM-aktivierter Benutzer angewendet werden sollen, die zu einer bestimmten Kategorie gehören. Beispielsweise kann mithilfe von Wählregelgruppen angegeben werden, welche Gruppe von Benutzern internationale Anrufe tätigen darf und welche Gruppe nur nationale bzw. Ortsgespräche führen darf. Sie können eine Wählregelgruppe unter Verwendung der Exchange-Verwaltungskonsole oder des Cmdlets **Set-UMDialPlan** in der Exchange-Verwaltungsshell erstellen. Beim Erstellen einer Wählregelgruppe müssen Sie mindestens eine Wählregel für die Gruppe definieren.

Wenn ein Benutzer eine Rufnummer wählt, gleicht UM diese Nummer mit den Wählregeln ab. Wenn eine Übereinstimmung gefunden wird, verwendet UM die Wählregel, um die zu wählende Nummer zu bestimmen, indem die Telefonnummer oder Ziffern im Abschnitt **Gewählte Nummer** der Wählregel untersucht werden. Die Nummer im Feld **Gewählte Nummer** der Wählregel wird gewählt.

In der folgenden Tabelle finden Sie ein Beispiel für Wählregelgruppen und Wählregeln. In diesem Beispiel sind **Nur Ortsgespräche** und **Billigtarif** die erstellten Wählregelgruppen. Die Wählregelgruppe **Nur Ortsgespräche** verfügt über zwei Wählregeln: 01425\* und 01206\*. Die Wählregelgruppe **Billigtarif** verfügt ebenfalls über zwei Wählregeln: 01509\* und 01360\*.

### Wählregelgruppen und Wählregeln

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>NumberMask</th>
<th>DialedNumber</th>
<th>Comment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nur Ortsgespräche</p></td>
<td><p>91425*</p></td>
<td><p>91*</p></td>
<td><p>Ortsgespräche</p></td>
</tr>
<tr class="even">
<td><p>Nur Ortsgespräche</p></td>
<td><p>91206*</p></td>
<td><p>91*</p></td>
<td><p>Ortsgespräche</p></td>
</tr>
<tr class="odd">
<td><p>Billigtarif</p></td>
<td><p>91509*</p></td>
<td><p>9*</p></td>
<td><p>Nationale Anrufe</p></td>
</tr>
<tr class="even">
<td><p>Billigtarif</p></td>
<td><p>91360*</p></td>
<td><p>9*</p></td>
<td><p>Nationale Anrufe</p></td>
</tr>
</tbody>
</table>


Wählt ein Benutzer beispielsweise die Nummer 0-1-425-555-1234, wählt UM 4255551234. UM entfernt alle nicht numerischen Zeichen (in diesem Beispiel die Bindestriche) und wendet die Nummernmaske aus dem Wählregeln an. In diesem Beispiel wendet UM die Nummernmaske 01\* an. Diese weist UM an, weder die 0 noch die 1 zu wählen, sondern alle anderen in der Rufnummer enthaltenen Ziffern, die der 1 nachgestellt sind. Hierzu gehören alle Ziffern, die durch das Sternchen (\*) dargestellt werden.

Sie können mithilfe der Exchange-Verwaltungskonsole oder der Shell einzelne oder mehrere nationale/regionale und internationale Wählregelgruppen und Wählregeln erstellen und konfigurieren. Wenn Sie allerdings viele oder komplexe Wählregelgruppen und Wählregeln erstellen, können Sie eine CSV-Datei (Comma-Separated Value, durch Trennzeichen getrennt) in der Shell verwenden. Sie können eine Liste mit Wählregelgruppen und Wählregeln importieren oder exportieren.

Zum Importieren einer Liste mit Wählregelgruppen und Wählregeln, die in einer CSV-Datei definiert wurden, führen Sie das Cmdlet **Set-UMDialPlan** wie folgt aus:

    Set-UMDialPlan "MyUMDialPlan" -ConfiguredInCountryOrRegionGroups $(IMPORT-CSV c:\dialrules\InCountryRegion.csv)

Zum Abrufen einer Liste der für einen Wählplan konfigurierten Wählregelgruppen führen Sie das Cmdlet **Get-UMDialPlan** wie folgt aus:

    (Get-UMDialPlan -id "MyUMDialPlan").ConfiguredInCountryOrRegionGroups | EXPORT-CSV C:\incountryorregion.csv

Die CSV-Datei muss im richtigen Format erstellt und gespeichert werden. Jede Zeile in der CSV-Datei stellt eine Wählregel dar. Jede Wählregel wird jedoch in derselben Wählregelgruppe konfiguriert. Jede Regel in der Datei besteht aus vier Abschnitten, die durch Kommas voneinander getrennt sind. Bei diesen Abschnitten handelt es sich um den Namen, die Nummernmaske, die gewählte Nummer und einen Kommentar. Mit Ausnahme des Kommentars ist jeder Abschnitt erforderlich und muss mit richtigen Informationen ausgefüllt werden. Zwischen dem jeweiligen Texteintrag und dem Komma des nächsten Abschnitts darf kein Leerzeichen stehen. Es dürfen auch keine Leerzeilen zwischen den Regeln oder am Ende der Datei vorhanden sein. Im Folgenden sehen Sie ein Beispiel für eine CSV-Datei, die zum Erstellen von nationalen/regionalen Wählregelgruppen und Wählregeln verwendet werden kann.

**Name,NumberMask,DialedNumber,Comment**

**Low-rate,91425xxxxxxx,9xxxxxxx,Local call**

**Low-rate,9425xxxxxxx,9xxxxxxx,Local call**

**Low-rate,9xxxxxxx,9xxxxxxx,Local call**

**Any,91\*,91\*,Open access to in-country/region numbers**

**Long-distance,91408\*,91408\*,long distance**

Im Folgenden sehen Sie ein Beispiel für eine CSV-Datei, die zum Erstellen von internationalen Wählregelgruppen und Wählregeleinträgen verwendet werden kann.

**Name,NumberMask,DialedNumber,Comment**

**International, 901144\*, 901144\*, international call**

**International, 901133\*, 901133\*, international call**

Zurück zum Seitenanfang

## Anwenden konfigurierter Wählregelgruppen

Wählregelgruppen werden für UM-Wählpläne erstellt. Sie können nationale/regionale bzw. internationale Wählregelgruppen unter Verwendung der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **Set-UMDialPlan** in der Shell erstellen. Nachdem die geeigneten Wählregelgruppen für einen UM-Wählplan erstellt und die Wählregeleinträge definiert wurden, können die erstellten Wählregelgruppen auf einen UM-Wählplan, eine automatische UM-Telefonzentrale oder Benutzer, die einer UM-Postfachrichtlinie zugeordnet sind, angewendet werden und das Outdialing abhängig davon autorisieren, wie Benutzer auf das Voicemailsystem zugreifen.

Die für einen Wählplan erstellten Wählregelgruppen können auf Folgendes angewendet werden:

  - **Gleicher Wählplan**   Die Einstellungen gelten für alle Benutzer, die über eine Outlook Voice Access-Nummer anrufen, sich aber nicht bei ihrem Postfach anmelden. Zum Anwenden einer nationalen/regionalen Wählregelgruppe namens `MyAllowedDialRuleGroup` auf denselben Wählplan verwenden Sie das Shell-Cmdlet **Set-UMDialPlan** wie folgt.
    
        Set-UMDialPlan -Identity MyUMDialPlan -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup

  - **Eine einzelne oder mehrere UM-Postfachrichtlinien**   Die für eine UM-Postfachrichtlinie konfigurierten Einstellungen gelten für alle Benutzer, die der angegebenen UM-Postfachrichtlinie zugeordnet sind. Die für eine UM-Postfachrichtlinie konfigurierten Einstellungen gelten für Benutzer, die über eine Outlook Voice Access-Nummer anrufen und sich bei ihrem Postfach anmelden. Zum Anwenden einer nationalen/regionalen Wählregelgruppe namens `MyAllowedDialRuleGroup` auf eine einzelne UM-Postfachrichtlinie verwenden Sie die Registerkarte **Wählautorisierung** für die UM-Postfachrichtlinie in der Exchange-Verwaltungskonsole oder das Cmdlet **Set-UMMailboxPolicy** in der Shell wie folgt.
    
        Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup

  - **Eine einzelne oder mehrere automatische Telefonzentralen, die den UM-Wählpläne zugeordnet sind**   Dies gilt für alle Benutzer, die bei einer automatischen UM-Telefonzentrale anrufen. Zum Anwenden der nationalen/regionalen Wählregelgruppe namens `MyAllowedDialRuleGroup` auf eine einzelne automatische UM-Telefonzentrale verwenden Sie die Registerkarte **Wählautorisierung** für die automatische Telefonzentrale in der Exchange-Verwaltungskonsole oder das Cmdlet **Set-UMAutoAttendant** in der Shell wie folgt.
    
        Set-UMAutoAttendant -Identity MyUMAutoAttendant -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup

Die folgende Tabelle fasst die Anwendungsmöglichkeiten von Wählregelgruppen in Unified Messaging zusammen.

### Anwendung von Outdialingregeln

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Anrufertyp</th>
<th>Geltungsbereich</th>
<th>Angewendete Outdialingeinstellungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook Voice Access-Nummer</p></td>
<td><p>Der Benutzer wählt eine Outlook Voice Access-Nummer im Wählplan und meldet sich bei seinem Postfach an</p></td>
<td><p>UM-Postfachrichtlinie</p></td>
</tr>
<tr class="even">
<td><p>Anonymer Anrufer</p></td>
<td><p>Der Benutzer wählt eine Outlook Voice Access-Nummer im Wählplan</p></td>
<td><p>UM-Wählplan</p></td>
</tr>
<tr class="odd">
<td><p>Anonymer Anrufer</p></td>
<td><p>Der Benutzer wählt sich über die Pilot- oder Durchwahlnummer einer automatischen Telefonzentrale ein</p></td>
<td><p>Automatische UM-Telefonzentrale</p></td>
</tr>
<tr class="even">
<td><p>Anrufer von innerhalb der Organisation</p></td>
<td><p>Der Benutzer wählt sich über die Nummer für die Wiedergabe über Telefon ein</p></td>
<td><p>UM-Postfachrichtlinie</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Anwenden von Wählregeln

Der Outdialingprozess wird in den folgenden Fällen ausgeführt:

  - Unified Messaging leitet einen Anruf einer externen Telefonnummer für einen Anrufer ein.

  - Unified Messaging vermittelt einen Anruf an eine automatische Telefonzentrale.

  - Unified Messaging vermittelt einen Anruf an einen Benutzer in Ihrer Organisation.

  - Ein UM-aktivierter Benutzer verwendet die Funktion "Wiedergabe über Telefon".

In jedem Outdialingszenario wendet UM die konfigurierten Wählregeln an und leitet dann den Anruf für den Benutzer ein. Je nach Szenario sowie der Art der Anrufeinleitung durch den Benutzer wendet UM jedoch möglicherweise nur einige der Wählregeln auf die gewählte Rufnummer an. In anderen Outdialingszenarien wendet UM möglicherweise alle konfigurierten Outdialingregeln auf die gewählte Rufnummer an.

Zurück zum Seitenanfang

