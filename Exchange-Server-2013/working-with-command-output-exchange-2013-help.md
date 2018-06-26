---
title: 'Arbeiten mit Ausgaben von Befehlen: Exchange 2013 Help'
TOCTitle: Arbeiten mit Ausgaben von Befehlen
ms:assetid: 8320e1a5-d3f5-4615-878d-b23e2aaa6b1e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123533(v=EXCHG.150)
ms:contentKeyID: 50476131
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Arbeiten mit Ausgaben von Befehlen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die Exchange-Verwaltungsshell bietet verschiedene Methoden zum Formatieren der Befehlsausgabe. In diesem Thema werden die folgenden Punkte behandelt:

  - How to format data   Hier wird erläutert, wie die angezeigten Daten mit den Cmdlets **Format-List**, **Format-Table** und **Format-Wide** formatiert werden können.

  - How to output data   Hier wird erläutert, wie mit den Cmdlets **Out-Host** und **Out-File** festgelegt wird, ob die Daten an das Konsolenfenster der Shell oder an eine Datei ausgegeben werden. Dieser Abschnitt enthält auch ein Beispielskript für die Ausgabe von Daten an Microsoft Internet Explorer.

  - How to filter data   Hier wird beschrieben, wie Sie Daten mithilfe einer der folgenden Filtermethoden filtern können:
    
      - Serverseitige Filterung, verfügbar bei bestimmten Cmdlets.
    
      - Clientseitige Filterung, verfügbar bei allen Cmdlets, indem die Ergebnisse eines Befehls mittels Pipe an das Cmdlet **Where-Object** übergeben werden.

Wenn Sie die in diesem Thema beschriebene Funktionalität nutzen möchten, müssen Sie mit den folgenden Konzepten vertraut sein:

  - [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\))

  - [Shellvariablen](https://technet.microsoft.com/de-de/library/bb124036\(v=exchg.150\))

  - [Vergleichsoperatoren](https://technet.microsoft.com/de-de/library/bb125229\(v=exchg.150\))

## Formatieren von Daten

Wenn Sie Cmdlets für die Formatierung am Ende der Pipeline aufrufen, kann die Standardformatierung außer Kraft gesetzt werden, mit der bestimmt wird, welche Daten angezeigt und wie die Daten dargestellt werden. Die Cmdlets für die Formatierung lauten **Format-List**, **Format-Table** und **Format-Wide**. Jedes Cmdlet weist einen eigenen Ausgabestil auf, der sich von dem der anderen Cmdlets für die Formatierung unterscheidet.

## Format-List

Das Cmdlet **Format-List** akzeptiert Eingaben aus der Pipeline und gibt eine Liste mit senkrechten Spalten aus, die alle angegebenen Eigenschaften jedes Objekts enthält. Mit dem Parameter *Property* kann festgelegt werden, welche Eigenschaften angezeigt werden sollen. Wenn das Cmdlet **Format-List** ohne Parameter aufgerufen wird, werden alle Eigenschaften ausgegeben. Bei Verwendung des Cmdlets **Format-List** werden Zeilen nicht abgeschnitten, sondern es erfolgt ein Umbruch. Eine der besten Einsatzmöglichkeiten für das Cmdlet **Format-List** besteht darin, die Standardausgabe eines Cmdlets außer Kraft zu setzen, sodass weitere oder wesentlichere Informationen abgerufen werden können.

Beispiel: Wenn Sie das Cmdlet **Get-Mailbox** aufrufen, werden nur in begrenztem Umfang Informationen im Tabellenformat angezeigt. Sie können jedoch die gewünschte Ausgabe abrufen, indem Sie die Ausgabe des Cmdlets **Get-Mailbox** mittels Pipe an das Cmdlet **Format-List** übergeben und Parameter für die gewünschten zusätzlichen oder spezifischeren Informationen hinzufügen.

Darüber hinaus kann auch ein Platzhalterzeichen (\*) mit einem Teil eines Eigenschaftennamens angegeben werden. Bei Angabe eines Platzhalterzeichens können mehrere Eigenschaften zugeordnet werden, ohne dass die Eigenschaften einzeln eingegeben werden müssen. Beispiel: `Get-Mailbox | Format-List -Property Email* ` gibt alle Eigenschaften zurück, die mit `Email` beginnen.

In den folgenden Beispiele wird gezeigt, wie dieselben von dem Cmdlet **Get-Mailbox** zurückgegebenen Daten auf unterschiedliche Weise angezeigt werden können.

    Get-Mailbox TestUser1
    
    Name                      Alias                ServerName       ProhibitSendQuo
                                                                    ta
    ----                      -----                ----------       ---------------
    TestUser1                 TestUser1            mbx              unlimited

Im ersten Beispiel wird das Cmdlet **Get-Mailbox** ohne spezielle Formatierung aufgerufen, sodass die Standardausgabe im Tabellenformat erfolgt und einen vordefinierten Satz von Eigenschaften enthält.

    Get-Mailbox TestUser1 | Format-List -Property Name,Alias,EmailAddresses
    
    Name           : TestUser1
    Alias          : TestUser1
    EmailAddresses : {SMTP:TestUser1@contoso.com}

Im zweiten Beispiel wird die Ausgabe des Cmdlets **Get-Mailbox** zusammen mit bestimmten Eigenschaften mittels Pipe an das Cmdlet **Format-List** übergeben. Format und Inhalt der Ausgabe sind bei diesem Beispiel völlig anders.

    Get-Mailbox TestUser1 | Format-List -Property Name, Alias, Email*
    Name                      : Test User
    Alias                     : TestUser1
    EmailAddresses            : {SMTP:TestUser1@contoso.com}
    EmailAddressPolicyEnabled : True

Im letzten Beispiel wird die Ausgabe des Cmdlets **Get-Mailbox** wie im zweiten Beispiel mittels Pipe an das Cmdlet **Format-List** übergeben. Bei dem letzten Beispiel wird jedoch ein Platzhalterzeichen verwendet, um alle Eigenschaften zuzuordnen, die mit `Email` beginnen.

Wenn mehrere Objekte an das Cmdlet **Format-List** übergeben werden, werden alle für ein Objekt angegebenen Eigenschaften nach Objekt gruppiert und angezeigt. Die Anzeigereihenfolge richtet sich nach dem Standardparameter für das Cmdlet. Standardparameter ist meist der Parameter *Name* oder der Parameter *Identity*. Beispiel: Wenn das Cmdlet **Get-Childitem** aufgerufen wird, werden die Dateinamen in der Standardanzeige in alphabetischer Reihenfolge angezeigt. Damit dieses Verhalten geändert werden kann, muss das Cmdlet **Format-List** zusammen mit dem Parameter *GroupBy* und einem Eigenschaftswert, nach dem die Ausgabe gruppiert werden soll, aufgerufen werden. Im folgenden Befehl werden zum Beispiel alle Dateien in einem Verzeichnis aufgelistet und anschließend nach ihrer Dateierweiterung gruppiert.

    Get-Childitem | Format-List Name,Length -GroupBy Extension
    
        Extension: .xml
    
    Name   : Config_01.xml
    Length : 5627
    
    Name   : Config_02.xml
    Length : 3901
    
    
        Extension: .bmp
    
    Name   : Image_01.bmp
    Length : 746550
    
    Name   : Image_02.bmp
    Length : 746550
    
    
        Extension: .txt
    
    Name   : Text_01.txt
    Length : 16822
    
    Name   : Text_02.txt
    Length : 9835

In diesem Beispiel hat das Cmdlet **Format-List** die Elemente nach der Eigenschaft *Extension* gruppiert, die vom Parameter *GroupBy* angegeben wird. Der Parameter *GroupBy* kann mit jeder gültigen Eigenschaft für die Objekte im Pipelinestream verwendet werden.

## Format-Table

Das Cmdlet **Format-Table** ermöglicht die Darstellung von Elementen im Tabellenformat mit Spaltenüberschriften und verschiedenen Spalten mit Eigenschaftendaten. Viele Cmdlets, beispielsweise **Get-Process** und **Get-Service**, verwenden standardmäßig das Tabellenformat für die Ausgabe. Zu den Parametern für das Cmdlet **Format-Table** zählen *Properties* und *GroupBy*. Die Funktionsweise dieser Parameter ist bei diesem Cmdlet dieselbe wie beim Cmdlet **Format-List**.

In Verbindung mit dem Cmdlet **Format-Table** wird auch der Parameter *Wrap* verwendet. Dieser ermöglicht die vollständige Anzeige von Eigenschaftendaten in langen Zeilen, d. h., die Information wird nicht am Ende einer Zeile abgeschnitten. Sie können die Funktionsweise des Parameters *Wrap* bei der Darstellung zurückgegebener Informationen sehen, wenn Sie die Ausgabe des Befehls **Get-Command** in den folgenden beiden Beispielen vergleichen.

Im ersten Beispiel werden bei Verwendung des Cmdlets **Get-Command** zum Anzeigen der Befehlsinformationen für das Cmdlet **Get-Process** die Informationen zur Eigenschaft *Definition* abgeschnitten.

    Get-Command Get-Process | Format-Table Name,Definition
    
    Name                                    Definition
    ----                                    ----------
    get-process                             get-process [[-ProcessName] String[]...

Im zweiten Beispiel erhält der Befehl den Parameter *Wrap*, um die vollständige Anzeige des Inhalts der Eigenschaft *Definition* zu erzwingen.

    Get-Command Get-Process | Format-Table Name,Definition -Wrap
    
    Get-Process                             Get-Process [[-Name] <String[]>] [-Comp
                                            uterName <String[]>] [-Module] [-FileVe
                                            rsionInfo] [-Verbose] [-Debug] [-ErrorA
                                            ction <ActionPreference>] [-WarningActi
                                            on <ActionPreference>] [-ErrorVariable
                                            <String>] [-WarningVariable <String>] [
                                            -OutVariable <String>] [-OutBuffer <Int
                                            32>]
                                            Get-Process -Id <Int32[]> [-ComputerNam
                                            e <String[]>] [-Module] [-FileVersionIn
                                            fo] [-Verbose] [-Debug] [-ErrorAction <
                                            ActionPreference>] [-WarningAction <Act
                                            ionPreference>] [-ErrorVariable <String
                                            >] [-WarningVariable <String>] [-OutVar
                                            iable <String>] [-OutBuffer <Int32>]
                                            Get-Process [-ComputerName <String[]>]
                                            [-Module] [-FileVersionInfo] -InputObje
                                            ct <Process[]> [-Verbose] [-Debug] [-Er
                                            rorAction <ActionPreference>] [-Warning
                                            Action <ActionPreference>] [-ErrorVaria
                                            ble <String>] [-WarningVariable <String
                                            >] [-OutVariable <String>] [-OutBuffer
                                            <Int32>]

Wie bei dem Cmdlet **Format-List** können Sie auch hier ein Platzhalterzeichen (`*`) zusammen mit einem Teil eines Eigenschaftennamens angeben. Durch Angabe eines Platzhalterzeichens können mehrere Eigenschaften zugeordnet werden, ohne dass die Eigenschaften einzeln eingegeben werden müssen.

## Format-Wide

Das Cmdlet **Format-Wide** ermöglicht eine wesentlich einfachere Ausgabesteuerung als die übrigen Format-Cmdlets. Standardmäßig versucht das Cmdlet **Format-Wide**, so viele Spalten mit Eigenschaftswert wie möglich in einer Ausgabezeile anzuzeigen. Durch Hinzufügen von Parametern können Sie die Anzahl der Spalten festlegen und steuern, wie der Ausgabebereich verwendet wird.

Wird das Cmdlet **Format-Wide** in seiner einfachsten Form ganz ohne Parameter aufgerufen, wird die Ausgabe in so vielen Spalten angeordnet, wie auf die Seite passen. Beispiel: Wenn das Cmdlet **Get-Childitem** ausgeführt und dessen Ausgabe mittels Pipe an das Cmdlet **Format-Wide** übergeben wird, werden die Informationen wie folgt dargestellt:

    Get-ChildItem | Format-Wide
    
        Directory: FileSystem::C:\WorkingFolder
    
    Config_01.xml                           Config_02.xml
    Config_03.xml                           Config_04.xml
    Config_05.xml                           Config_06.xml
    Config_07.xml                           Config_08.xml
    Config_09.xml                           Image_01.bmp
    Image_02.bmp                            Image_03.bmp
    Image_04.bmp                            Image_05.bmp
    Image_06.bmp                            Text_01.txt
    Text_02.txt                             Text_03.txt
    Text_04.txt                             Text_05.txt
    Text_06.txt                             Text_07.txt
    Text_08.txt                             Text_09.txt
    Text_10.txt                             Text_11.txt
    Text_12.txt

Im Allgemeinen werden bei Aufruf des Cmdlets **Get-Childitem** ohne Parameter die Namen aller Dateien in dem Verzeichnis in einer Tabelle mit Eigenschaften angezeigt. Da in diesem Beispiel die Ausgabe des Cmdlets **Get-Childitem** mittels Pipe an das Cmdlet **Format-Wide** übergeben wurde, wurde die Ausgabe in zwei Spalten mit Namen angezeigt. Beachten Sie, dass zur gleichen Zeit jeweils nur ein Eigenschaftentyp angezeigt werden kann, der durch einen Eigenschaftennamen gemäß dem Cmdlet **Format-Wide** angegeben wurde. Durch Hinzufügen des Parameters *Autosize* wird die Ausgabe von zwei Spalten in so viele Spalten geändert, wie die Bildschirmbreite zulässt.

    Get-ChildItem | Format-Wide -AutoSize
    
        Directory: FileSystem::C:\WorkingFolder
    
    Config_01.xml   Config_02.xml   Config_03.xml   Config_04.xml   Config_05.xml
    Config_06.xml   Config_07.xml   Config_08.xml   Config_09.xml   Image_01.bmp
    Image_02.bmp    Image_03.bmp    Image_04.bmp    Image_05.bmp    Image_06.bmp
    Text_01.txt     Text_02.txt     Text_03.txt     Text_04.txt     Text_05.txt
    Text_06.txt     Text_07.txt     Text_08.txt     Text_09.txt     Text_10.txt
    Text_11.txt     Text_12.txt

In diesem Beispiel enthält die Tabelle nicht zwei, sondern fünf Spalten. Der Parameter *Column* bietet weitergehende Steuermöglichkeiten. Mit diesem Parameter können Sie die maximale Spaltenanzahl für die Anzeige von Informationen folgendermaßen angeben:

    Get-ChildItem | Format-Wide -Column 4
    
        Directory: FileSystem::C:\WorkingFolder
    
    Config_01.xml       Config_02.xml       Config_03.xml       Config_04.xml
    Config_05.xml       Config_06.xml       Config_07.xml       Config_08.xml
    Config_09.xml       Image_01.bmp        Image_02.bmp        Image_03.bmp
    Image_04.bmp        Image_05.bmp        Image_06.bmp        Text_01.txt
    Text_02.txt         Text_03.txt         Text_04.txt         Text_05.txt
    Text_06.txt         Text_07.txt         Text_08.txt         Text_09.txt
    Text_10.txt         Text_11.txt         Text_12.txt

In diesem Beispiel wird die vierspaltige Ansicht durch den Parameter *Column* erzwungen.

## Datenausgabe

## Cmdlets "Out-Host" und "Out-File"

Bei dem Cmdlet **Out-Host** handelt es sich um ein nicht angezeigtes Standard-Cmdlet am Ende der Pipeline. Nachdem sämtliche Formatierungen angewendet wurden, sendet das Cmdlet **Out-Host** die finale Ausgabe zur Anzeige an das Konsolenfenster. Das Cmdlet **Out-Host** muss nicht explizit aufgerufen werden, da es sich hierbei um die Standardausgabe handelt. Das Senden der Ausgabe an das Konsolenfenster kann außer Kraft gesetzt werden, indem das Cmdlet **Out-File** als letztes Cmdlet im Befehl aufgerufen wird. Das Cmdlet **Out-File** schreibt dann die Ausgabe in die Datei, die in dem Befehl angegeben wurde (siehe folgendes Beispiel):

    Get-ChildItem | Format-Wide -Column 4 | Out-File c:\OutputFile.txt

In diesem Beispiel werden vom Cmdlet **Out-File** die mit dem Befehl **Get-ChildItem | Format-Wide -Column 4** angezeigten Informationen in die Datei "`OutputFile.txt`" geschrieben. Die Ausgabe einer Pipeline kann auch mit dem Umleitungsoperator, also der spitzen Klammer rechts (`>`), in eine Datei umgeleitet werden. Zum Anfügen der Pipelineausgabe eines Befehls an eine vorhandene Datei, ohne dass die Originaldatei ersetzt wird, verwenden Sie die doppelten spitzen Klammern rechts (`>>`), wie im folgenden Beispiel dargestellt:

    Get-ChildItem | Format-Wide -Column 4 >> C:\OutputFile.txt

In diesem Beispiel wird die Ausgabe des Cmdlets **Get-Childitem** mittels Pipe zur Formatierung an das Cmdlet **Format-Wide** übergeben und dann an das Ende der Datei "`OutputFile.txt`" geschrieben. Wenn die Datei "`OutputFile.txt`" nicht vorhanden ist, wird sie bei Verwendung doppelter spitzer Klammern rechts (`>>`) erstellt.

Weitere Informationen zu Pipelines finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

Weitere Informationen zu der in den obigen Beispielen verwendeten Syntax finden Sie unter [Syntax](https://technet.microsoft.com/de-de/library/bb123552\(v=exchg.150\)).

## Anzeigen von Daten in Internet Explorer

Aufgrund der Flexibilität und Unkompliziertheit von Skripts in der Exchange-Verwaltungsshell können die von Befehlen zurückgegebenen Daten auf beinahe unbegrenzte Weise formatiert und ausgegeben werden.

Im folgenden Beispiel wird gezeigt, wie die von einem Befehl zurückgegebenen Daten mithilfe eines einfachen Skripts ausgegeben und in Internet Explorer angezeigt werden können. Dieses Skript verwendet die mittels Pipe übergebenen Objekte, öffnet ein Internet Explorer-Fenster und zeigt die Daten anschließend in Internet Explorer an:

    $Ie = New-Object -Com InternetExplorer.Application
    $Ie.Navigate("about:blank")
    While ($Ie.Busy) { Sleep 1 }
    $Ie.Visible = $True
    $Ie.Document.Write("$Input")
    # If the previous line doesn't work on your system, uncomment the line below.
    # $Ie.Document.IHtmlDocument2_Write(\"$Input\")
    $Ie

Zur Verwendung des Skripts speichern Sie dieses auf dem Computer, auf dem es ausgeführt werden soll, im Verzeichnis "`C:\Program Files\Microsoft\Exchange Server\V15\Scripts`". Legen Sie für die Datei den Namen "`Out-Ie.ps1`" fest. Nachdem die Datei gespeichert wurde, kann das Skript als reguläres Cmdlet verwendet werden.


> [!NOTE]
> Zum Ausführen von Skripts in Exchange 2013 müssen die Skripts zunächst zu einer Verwaltungsrolle ohne Bereichseinschränkung hinzugefügt werden. Die Verwaltungsrolle muss Ihnen anschließend entweder direkt oder durch eine Verwaltungsrollengruppe zugewiesen werden. Weitere Informationen finden Sie unter <A href="understanding-management-roles-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollen</A>.



Für das Skript `Out-Ie` wird davon ausgegangen, dass es sich bei den erhaltenen Daten um gültige HTML-Daten handelt. Zur Umwandlung der anzuzeigenden Daten in das HTML-Format müssen die Ergebnisse des Befehls mittels Pipe an das Cmdlet **ConvertTo-Html** übergeben werden. Die Ergebnisse des Befehls können dann mittels Pipe an das Skript `Out-Ie` übergeben werden. Im folgenden Beispiel wird gezeigt, wie eine Verzeichnisauflistung in einem Internet Explorer-Fenster angezeigt wird:

    Get-ChildItem | Select Name,Length | ConvertTo-Html | Out-Ie

## Filtern von Daten

Die Shell ermöglicht den Zugriff auf umfangreiche Informationen zu Ihren Servern, Postfächern, Active Directory und zu weiteren Objekten in der Organisation. Zwar hilft der Zugang zu diesen Informationen dabei, die Umgebung besser zu verstehen, die riesige Informationsmenge kann jedoch auch eine Überforderung bedeuten. Über die Shell können Sie steuern, welche Informationen ausgegeben werden, und mithilfe von Filtern nur die gewünschten Informationen anzeigen. Die folgenden Filterungsarten stehen zur Verfügung:

  - **Serverseitige Filterung**   Bei der serverseitigen Filterung wird der gewünschte Filter in der Befehlszeile eingegeben und an den Exchange-Server übergeben, der abgefragt wird. Der Server verarbeitet die Abfrage und gibt nur die Daten zurück, die dem angegebenen Filter entsprechen.
    
    Die serverseitige Filterung wird nur bei Objekten ausgeführt, bei denen möglicherweise Zehn- oder Hunderttausende von Ergebnissen zurückgegeben werden. Daher unterstützen nur die Cmdlets für die Empfängerverwaltung, wie das Cmdlet **Get-Mailbox**, und Cmdlets für die Warteschlangenverwaltung, wie das Cmdlet **Get-Queue**, die serverseitige Filterung. Diese Cmdlets unterstützen den Parameter *Filter*. Dieser Parameter übernimmt den von Ihnen angegebenen Filterausdruck und übergibt ihn zur Verarbeitung an den Server.

  - **Clientseitige Filterung**   Die clientseitige Filterung wird an den Objekten im lokalen Konsolenfenster, in dem Sie zurzeit arbeiten, durchgeführt. Bei der clientseitigen Filterung ruft das Cmdlet alle Objekte ab, die der von Ihnen im lokalen Konsolenfenster durchgeführten Aufgabe entsprechen. Die Shell übernimmt anschließend alle zurückgegebenen Ergebnisse, wendet den clientseitigen Filter auf diese Ergebnisse an und gibt nur die Ergebnisse zurück, die dem Filter entsprechen. Alle Cmdlets unterstützen die clientseitige Filterung. Diese wird aufgerufen, indem die Ergebnisse eines Befehls mittels Pipe an das Cmdlet **Where-Object** übergeben werden.

## Serverseitige Filterung

Die Implementierung der serverseitigen Filterung bezieht sich speziell auf das Cmdlet, von dem sie unterstützt wird. Die serverseitige Filterung ist nur für bestimmte Eigenschaften der zurückgegebenen Objekte aktiviert. Weitere Informationen finden Sie in der Hilfe für die folgenden Cmdlets:


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Get-ActiveSyncDevice</p></td>
<td><p>Get-ActiveSyncDeviceClass</p></td>
<td><p>Get-CASMailbox</p></td>
<td><p>Get-Contact</p></td>
<td><p>Get-DistributionGroup</p></td>
</tr>
<tr class="even">
<td><p>Get-DynamicDistributionGroup</p></td>
<td><p>Get-Group</p></td>
<td><p>Get-Mailbox</p></td>
<td><p>Get-MailboxStatistics</p></td>
<td><p>Get-MailContact</p></td>
</tr>
<tr class="odd">
<td><p>Get-MailPublicFolder</p></td>
<td><p>Get-MailUser</p></td>
<td><p>Get-Message</p></td>
<td><p>Get-MobileDevice</p></td>
<td><p>Get-Queue</p></td>
</tr>
<tr class="even">
<td><p>Get-QueueDigest</p></td>
<td><p>Get-Recipient</p></td>
<td><p>Get-RemoteMailbox</p></td>
<td><p>Get-RoleGroup</p></td>
<td><p>Get-SecurityPrincipal</p></td>
</tr>
<tr class="odd">
<td><p>Get-StoreUsageStatistics</p></td>
<td><p>Get-UMMailbox</p></td>
<td><p>Get-User</p></td>
<td><p>Get-UserPhoto</p></td>
<td><p>Remove-Message</p></td>
</tr>
<tr class="even">
<td><p>Resume-Message</p></td>
<td><p>Resume-Queue</p></td>
<td><p>Retry-Queue</p></td>
<td><p>Suspend-Message</p></td>
<td><p>Suspend-Queue</p></td>
</tr>
</tbody>
</table>


## Clientseitige Filterung

Die clientseitige Filterung kann mit jedem beliebigen Cmdlet verwendet werden. Hierzu zählen auch die Cmdlets, die ebenfalls die serverseitige Filterung unterstützen. Wie bereits weiter oben erläutert, werden bei der clientseitigen Filterung alle Daten akzeptiert, die von einem früheren Befehl in der Pipeline zurückgegeben wurden. Anschließend werden nur die Ergebnisse zurückgegeben, die dem angegebenen Filter entsprechen. Diese Art der Filterung wird mit dem Cmdlet **Where-Object** durchgeführt. Es kann zu **Where** verkürzt werden.

Wenn Daten die Pipeline durchlaufen, empfängt das Cmdlet **Where** die Daten von dem vorherigen Objekt und filtert sie anschließend, bevor sie an das nächste Objekt übergeben werden. Der Filterung liegt ein Skriptblock zugrunde, der im Befehl **Where** definiert ist. Der Skriptblock filtert Daten anhand der Eigenschaften und Werte des Objekts.

Das Cmdlet **Clear-Host** dient zum Löschen des Inhalts des Konsolenfensters. In diesem Beispiel werden alle definierten Aliase für das Cmdlet **Clear-Host** angezeigt, wenn Sie den folgenden Befehl ausführen:

    Get-Alias | Where {$_.Definition -eq "Clear-Host"}
    
    CommandType     Name                            Definition
    -----------     ----                            ----------
    Alias           clear                           clear-host
    Alias           cls                             clear-host

Das Cmdlet **Get-Alias** und der Befehl **Where** werden zusammen verwendet, um die Liste der Aliase zurückzugeben, die nur für das Cmdlet **Clear-Host** definiert sind. Die folgende Tabelle enthält die einzelnen Elemente des im Beispiel verwendeten Befehls **Where**.

### Elemente des Befehls "Where"

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>{ }</code></p></td>
<td><p>Der Skriptblock, der den Filter definiert, wird in geschweifte Klammern eingeschlossen.</p></td>
</tr>
<tr class="even">
<td><p><code>$_</code></p></td>
<td><p>Diese spezielle Variable wird automatisch initiiert und an die Objekte in der Pipeline gebunden.</p></td>
</tr>
<tr class="odd">
<td><p><code>Definition</code></p></td>
<td><p>Bei der Eigenschaft <code>Definition</code> handelt es sich um die Eigenschaft der aktuellen Pipelineobjekte, in der der Name der Aliasdefinition gespeichert wird. Wenn <code>Definition</code> mit der Variablen <code>$_</code> verwendet wird, steht vor dem Namen der Eigenschaft ein Punkt.</p></td>
</tr>
<tr class="even">
<td><p><code>-eq</code></p></td>
<td><p>Dieser Vergleichsoperator (&quot;gleich&quot;) wird verwendet, um anzugeben, dass die Ergebnisse genau mit dem im Ausdruck übergebenen Eigenschaftswert übereinstimmen müssen.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;<strong>Clear-Host</strong>&quot;</p></td>
<td><p>In diesem Beispiel ist &quot;<strong>Clear-Host</strong>&quot; der Wert, für den der Befehl die Analyse durchführt.</p></td>
</tr>
</tbody>
</table>


In dem Beispiel stellen die durch das Cmdlet **Get-Alias** zurückgegebenen Werte alle definierten Aliase im System dar. Die Aliase werden zwar nicht in der Befehlszeile angezeigt, sie werden jedoch erfasst und mittels Pipe an das Cmdlet **Where** übergeben. Die Informationen im Skriptblock werden vom Cmdlet **Where** verwendet, um einen Filter auf die Aliasobjekte anzuwenden.

Die spezielle Variable `$`\_ stellt die Objekte dar, die übergeben werden. Die Variable `$_` wird von der Shell automatisch initiiert und an das aktuelle Pipelineobjekt gebunden. Weitere Informationen zu dieser speziellen Variablen finden Sie unter [Shellvariablen](https://technet.microsoft.com/de-de/library/bb124036\(v=exchg.150\)).

Bei Verwendung der standardmäßigen Schreibweise mit Punkt (Objekt.Eigenschaft) wird die Eigenschaft `Definition` hinzugefügt, um die genaue Eigenschaft des auszuwertenden Objekts zu definieren. Der Vergleichsoperator `-eq` vergleicht anschließend den Wert dieser Eigenschaft mit `"Clear-Host"`. Nur die Objekte mit der Eigenschaft `Definition`, die dieses Kriterium erfüllen, werden zur Ausgabe an das Konsolenfenster übergeben. Weitere Informationen zu Vergleichsoperatoren finden Sie unter [Vergleichsoperatoren](https://technet.microsoft.com/de-de/library/bb125229\(v=exchg.150\)).

Nachdem der Befehl **Where** die vom Cmdlet **Get-Alias** zurückgegebenen Objekte gefiltert hat, können die gefilterten Objekte mittels Pipe an einen anderen Befehl übergeben werden. Der nächste Befehl verarbeitet nur die gefilterten Objekte, die vom Befehl "Where" zurückgegeben wurden.

