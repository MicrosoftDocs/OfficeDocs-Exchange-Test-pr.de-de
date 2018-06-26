---
title: 'Importieren von Adressumschreibungseinträgen auf Edge-Transport-Server: Exchange 2013 Help'
TOCTitle: Importieren von Adressumschreibungseinträgen auf Edge-Transport-Server
ms:assetid: bd0942c6-9c66-4b4c-b9bc-2f5f783def76
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb331966(v=EXCHG.150)
ms:contentKeyID: 61061222
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Importieren von Adressumschreibungseinträgen auf Edge-Transport-Server

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie können Adressumschreibungsinformationen per Massenvorgang erstellen oder in einen Edge-Transport-Server importieren, indem Sie eine Datei mit kommagetrennten Werten (CSV-Datei) verwenden. In der folgenden Liste sind einige häufige Szenarien aufgeführt, bei denen dies notwendig ist:

  - Sie ersetzen eine Adressenumschreibungslösung durch einen Edge-Transport-Server.

  - Sie treffen eine Vereinbarung mit einem externen Lösungsanbieter, die ein Umschreiben dessen E-Mail-Adressen erforderlich macht.

  - Sie erwerben eine andere Organisation und müssen die E-Mail-Adressen in dieser Organisation vorübergehend umschreiben.

Sie können einen beliebigen Texteditor (z. B. den Editor von Windows) oder eine Anwendung wie z. B. Microsoft Excel zu Erstellen der CSV-Datei verwenden. Formatieren Sie die Datei wie in diesem Thema beschreiben, und speichern Sie sie als CSV-Datei.

In der ersten Zeile, der *Kopfzeile*, der CSV-Datei werden die Namen der Parameter aufgeführt. Die einzelnen Parameter werden jeweils durch ein Komma getrennt. Die erforderlichen und optionalen Parameter sind der folgenden Tabelle aufgeführt.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Erforderlich oder optional</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Ein eindeutiger, beschreibender Name für den Adressenumschreibungseintrag.</p></td>
</tr>
<tr class="even">
<td><p><em>InternalAddress</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Die zu ändernde Adresse. Folgende Werte können verwendet werden:</p>
<ul>
<li><p>Eine einzelne E-Mail-Adresse (chris@contoso.com)</p></li>
<li><p>Eine einzelne Domäne oder Unterdomäne (contoso.com oder sales.contoso.com)</p></li>
<li><p>Eine Domäne und alle Unterdomänen (*.contoso.com)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><em>ExternalAddress</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Die endgültige E-Mail-Adresse. Folgende Werte können verwendet werden:</p>
<ul>
<li><p>Eine einzelne E-Mail-Adresse, wenn Sie für <em>InternalAddress</em> eine einzelne E-Mail-Adresse angegeben haben</p></li>
<li><p>Eine einzelne Domäne oder Unterdomäne für alle anderen Werte von <em>InternalAddress</em></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><em>ExceptionList</em></p></td>
<td><p>Optional</p></td>
<td><p>Nur verfügbar, wenn Sie E-Mail-Adressen in einer Domäne und allen Unterdomänen umschreiben (*.contoso.com). Gibt eine oder mehrere Unterdomänen an, die Sie aus der Adressenumschreibung ausschließen möchten. Schließen Sie den Wert in doppelte Anführungszeichen ein, und trennen Sie die Werte durch Kommas. Beispiel: <code>&quot;marketing.contoso.com&quot;</code> oder <code>&quot;marketing.contoso.com,legal.contoso.com&quot;</code>.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundOnly</em></p></td>
<td><p>Optional</p></td>
<td><p><code>False</code> bedeutet, dass die Adressen für eingehende und ausgehende Mails umgeschrieben werden. <code>True</code> bedeutet, dass Adressen nur für ausgehende Mails umgeschrieben werden. Sie müssen die umgeschriebenen E-Mail-Adressen dann manuell als Proxyadressen der betroffenen Empfänger konfigurieren.</p>
<p>Der Standardwert ist <code>False</code>. Sie müssen jedoch <code>True</code> festlegen, wenn <em>InternalAddress</em> das Platzhalterzeichen umfasst (*.contoso.com).</p>
<p>Der <em>OutboundOnly</em>-Parameterwert in der CSV-Datei ist <code>True</code> oder <code>False</code>, nicht <code>$True</code> oder <code>$False</code>.</p></td>
</tr>
</tbody>
</table>


Jede Zeile unterhalb der Kopfzeile stellt einen einzelnen Adressenumschreibungseintrag dar. Die Werte in jeder einzelnen Zeile müssen die gleiche Reihenfolge aufweisen wie die Parameternamen in der Kopfzeile. Die einzelnen Werte werden jeweils durch ein Komma getrennt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten

  - Stellen Sie sicher, dass Sie die Auswirkungen der Adressenumschreibung kennen. So müssen die umgeschriebenen E-Mail-Adressen in Ihrer Exchange-Organisation zum Beispiel eindeutig sein, und Sie müssen für die betroffenen Empfänger möglicherweise Proxyadressen konfigurieren. Weitere Informationen finden Sie unter [Adressumschreibung auf Edge-Transport-Servern](address-rewriting-on-edge-transport-servers-exchange-2013-help.md) und [Verwalten der Adressumschreibung auf Edge-Transport-Servern](manage-address-rewriting-on-edge-transport-servers-exchange-2013-help.md).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adressumschreibungs-Agent" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Wenn Sie über mehr als einen Edge-Transport-Server verfügen, wird die Verwendung der Verfahren in diesem Thema zum Importieren von Einträgen zum Umschreiben von Adressen in einen einzelnen Edge-Transport-Server und das anschließende Klonen der Konfiguration dieses Edge-Transport-Servers auf die anderen Edge-Transport-Server in der Organisation empfohlen. Weitere Informationen zum Klonen eines Edge-Transport-Servers finden Sie unter [Geklonte Edge-Transport-Server-Konfiguration](edge-transport-server-cloned-configuration-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen Sie die CSV-Datei.

Wenn Sie die CSV-Datei erstellen, berücksichtigen Sie Folgendes:

  - Wenn Sie Werte für optionale Parameter in der CSV-Datei angeben, muss jede Zeile einen Wert in der betreffenden Spalte enthalten. Wenn Sie mehrere Einträge zum Umschreiben von Adressen erstellen möchten, wobei einige Einträge über optionale Parameter verfügen, andere jedoch nicht, müssen Sie diese Einträge zum Umschreiben von Adressen trennen und zwei separate CSV-Dateien erstellen und anschließend die einzelnen CSV-Dateien importieren.

  - Wenn die CSV-Datei Nicht-ASCII-Zeichen enthält, stellen Sie sicher, dass Sie die CSV-Datei mit UTF-8-Codierung oder einer anderen Unicode-Codierung speichern. Abhängig von der Anwendung ist es möglicherweise leichter, die CSV-Datei mit UTF-8-Codierung oder einer anderen Unicode-Codierung zu speichern, wenn das Systemgebietsschema des Computers der in der CSV-Datei verwendeten Sprache entspricht.

Im folgenden Beispiel wird dargestellt, wie eine CSV-Datei mit den optionalen Parametern *ExceptionList* und *OutboundOnly* mit Werten aufgefüllt werden kann:

    Name,InternalAddress,ExternalAddress,ExceptionList,OutboundOnly
    "Wingtip UK",*.wingtiptoys.co.uk,tailspintoys.com,"legal.wingtiptoys.co.uk,finance.wingtiptoys.co.uk,support.wingtiptoys.co.uk",True
    "Wingtip USA",*.wingtiptoys.com,tailspintoys.com,"legal.wingtiptoys.com,finance.wingtiptoys.com,support.wingtiptoys.com,corp.wingtiptoys.com",True
    "Wingtip Canada",*.wingtiptoys.ca,tailspintoys.com,"legal.wingtiptoys.ca,finance.wingtiptoys.ca,support.wingtiptoys.ca",True

## Schritt 2: Importieren Sie die CSV-Datei.

Verwenden Sie die folgende Syntax, um die CSV-Datei zu importieren:

    Import-Csv <FileNameAndPath> | ForEach {New-AddressRewriteEntry -Name $_.Name -InternalAddress $_.InternalAddress -ExternalAddress $_.ExternalAddress -OutboundOnly ([Bool]::Parse($_.OutboundOnly)) -ExceptionList $_.ExceptionList}

Dieses Beispiel importiert die Einträge für die Adressenumschreibung von C:\\Eigene Dateien\\ImportAddressRewriteEntries.csv.

    Import-Csv "C:\My Documents\ImportAddressRewriteEntries.csv" | ForEach {New-AddressRewriteEntry -Name $_.Name -InternalAddress $_.InternalAddress -ExternalAddress $_.ExternalAddress -OutboundOnly ([Bool]::Parse($_.OutboundOnly)) -ExceptionList $_.ExceptionList}

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Um zu überprüfen, ob die Einträge für die Adressenumschreibung erfolgreich aus einer CSV-Datei importiert wurden, gehen Sie wie folgt vor:

1.  Führen Sie den Befehl `Get-AddressRewriteEntry` aus, um alle Einträge der Adressenumschreibung anzuzeigen.

2.  Um Details zu einem bestimmten Eintrag der Adressenumschreibung anzuzeigen, führen Sie den Befehl `Get-AddressRewriteEntry <AddressRewriteIdentity> | Format-List` aus.

