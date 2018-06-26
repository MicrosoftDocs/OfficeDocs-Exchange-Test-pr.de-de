---
title: 'Importieren und Exportieren von Dateien in der Exchange-Verwaltungsshell: Exchange 2013 Help'
TOCTitle: Importieren und Exportieren von Dateien in der Exchange-Verwaltungsshell
ms:assetid: b4b669e8-a3aa-4b0b-ad34-f1f15d9c9369
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638170(v=EXCHG.150)
ms:contentKeyID: 50554907
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Importieren und Exportieren von Dateien in der Exchange-Verwaltungsshell

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Microsoft Exchange Server 2013 verwendet Windows PowerShell-Befehlszeilenschnittstellen-Remoting zum Herstellen einer Verbindung zwischen dem Server oder Computer zum Verwalten von Exchange und dem Server mit Exchange 2013, den Sie verwalten. In Exchange 2013 wird dies als Exchange-Remoteverwaltungshell oder Remoteshell bezeichnet. Selbst wenn Sie den lokalen Exchange 2013-Server verwalten, wird die Remoteshell zum Herstellen der Verbindung verwendet. Weitere Informationen zur lokalen und die Remoteshell finden Sie unter [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)).

Das Importieren und Exportieren von Dateien auf einen und von einem Exchange-Server in Exchange 2013 unterscheidet sich von diesen Vorgängen in Exchange Server 2007. Der Grund ist der Einsatz von Remoteshell in Exchange 2013. In diesem Thema wird erläutert, warum dieser neue Prozess erforderlich ist und wie Dateien zwischen einem lokalen Server oder Computer und einem Exchange 2013-Server im- und exportiert werden.

## Windows PowerShell-Sitzungen

Um zu verstehen, warum in der Remoteshell eine besondere Syntax zum Im- und Exportieren von Dateien benötigt wird, müssen Sie wissen, wie die Shell in Exchange 2013 implementiert ist. Die Shell verwendet Windows PowerShell-Sitzungen, bei denen es sich um die Umgebungen handelt, in denen Variablen, Cmdlets usw. Informationen gemeinsam nutzen können. Bei jedem Öffnen eines neuen Shellfensters wird eine neue Sitzung erstellt. Die in den verschiedenen Fenstern ausgeführten Cmdlets können auf Variablen und andere Informationen zugreifen, die in diesen Fenstern gespeichert sind. Ein Zugriff auf Variablen in anderen offenen Shellfenstern ist jedoch nicht möglich. Der Grund dafür ist, dass sie sich in ihren eigenen Windows PowerShell-Sitzungen befinden. Windows PowerShell-Sitzungen können auch als Runspaces bezeichnet werden.

Die Remoteshell in Exchange 2013 weist zwei Sitzungen auf, die lokale Sitzung und die Remotesitzung. Die lokale Sitzung ist die Windows PowerShell-Sitzung, die auf Ihrem lokalen Computer ausgeführt wird. Diese Sitzung enthält alle Cmdlets, die im Lieferumfang von Windows PowerShell enthalten sind. Sie verfügt zudem über Zugriff auf das lokale Dateisystem.

Die Remotesitzung ist die Windows PowerShell-Sitzung, die auf dem Exchange-Remoteserver ausgeführt wird. In dieser Sitzung werden alle Exchange-Cmdlets ausgeführt. Sie hat Zugriff auf das Dateisystem des Exchange-Servers.

Wenn Sie eine Verbindung mit einem Exchange-Remoteserver herstellen, erfolgt eine Verbindung zwischen Ihrer lokalen Sitzung auf Ihrem Computer und der Remotesitzung auf dem Exchange-Server. Diese Verbindung ermöglicht Ihnen die Ausführung von Exchange-Cmdlets auf dem Exchange-Remoteserver in Ihrer lokalen Sitzung, obwohl auf Ihrem lokalen Computer keine Exchange-Cmdlets installiert sind. Auch wenn die Exchange-Cmdlets anscheinend auf Ihrem lokalen Computer ausgeführt werden, werden sie tatsächlich auf dem Exchange-Server ausgeführt.


> [!IMPORTANT]
> Selbst wenn Sie die Shell auf einem Exchange 2013-Server öffnen, erfolgt derselbe Verbindungsprozess, und zwei Sitzungen werden eingerichtet. Das heißt, dass Sie dieselbe neue Syntax zum Im- und Exportieren von Dateien verwenden müssen, wenn Sie die Shell auf einem Exchange 2013-Server oder einem Remoteclient-Computer öffnen.



Die Exchange-Cmdlets, die in der Remotesitzung auf dem Exchange-Remoteserver ausgeführt werden, haben keinen Zugriff auf Ihr lokales Dateisystem. Das bedeutet, dass Sie Exchange-Cmdlets im lokalen Datensystem nicht eigenständig zum Im- oder Exportieren von Dateien verwenden können. Weitere Syntax ist erforderlich, um Dateien aus und in das lokale Dateisystem zu übertragen, damit die Exchange-Cmdlets, die auf dem Exchange-Remoteserver ausgeführt werden, die Daten nutzen können. Weitere Informationen zur erforderlichen Syntax finden Sie unter "Im- und Exportieren von Dateien in der Remoteshell" weiter unten in diesem Thema.

## Im- und Exportieren von Dateien in der Remoteshell

Das Im- und Exportieren von Dateien erfordert eine besondere Syntax, da Postfach- und Clientzugriffsserver die Remoteshell verwenden und keinen Zugriff auf das Dateisystem des lokalen Computers haben.

## Importieren von Dateien in die Remoteshell

Die Syntax zum Importieren von Dateien in Exchange 2013 wird immer dann verwendet, wenn Sie auf Ihrem lokalen Computer oder Server eine Datei an ein auf einem Exchange 2013-Server ausgeführtes Cmdlet senden. Cmdlets, die Daten einer Datei auf Ihrem lokalen Computer akzeptieren, weisen den Parameter *FileData* (o. ä.) auf. Lesen Sie zum Bestimmen des ordnungsgemäßen zu verwendenden Parameter die Hilfeinformationen zum verwendeten Cmdlet.

Die Shell muss wissen, welche Datei Sie an das Exchange 2013-Cmdlet senden und welcher Parameter Daten akzeptiert. Verwenden Sie zu diesem Zweck die folgende Syntax.

    <Cmdlet> -FileData ([Byte[]]$(Get-Content -Path <local path to file> -Encoding Byte -ReadCount 0))

Über den folgenden Befehl wird z. B. die Datei C:\\MyData.dat in den Parameter *FileData* des fiktionalen Cmdlets **Import-SomeData** importiert.

    Import-SomeData -FileData (Byte[]]$(Get-Content -Path "C:\MyData.dat" -Encoding Byte -ReadCount 0))

Wenn der Befehl ausgeführt wird, werden folgende Aktionen ausgeführt:

1.  Der Befehl wird von der Remoteshell akzeptiert.

2.  Die Remoteshell wertet den Befehl aus und ermittelt, dass der für den Parameter *FileData* bereitgestellte Wert einen eingebetteten Befehl enthält.

3.  Die Remoteshell beendet die Auswertung des Befehls **Import-SomeData** und führt den Befehl **Get-Content** aus. Der Befehl **Get-Content** liest die Daten aus der Datei MyData.dat.

4.  Die Remoteshell speichert die Daten aus dem Befehl **Get-Content** vorübergehend als `Byte[]`-Objekt, sodass sie an das Cmdlet **Import-SomeData** übergeben werden können.

5.  Die Ausführung des Befehls **Import-SomeData** wird fortgesetzt. Die Remoteshell sendet die Anforderung zum Ausführen des Cmdlets **Import-SomeData** zusammen mit dem vom Cmdlet **Get-Content** erstellten Objekt an den Exchange 2013-Remoteserver.

6.  Auf dem Exchange 2013-Remoteserver wird das Cmdlet **Import-SomeData** ausgeführt, und die Daten, die im vom Cmdlet **Get-Content** erstellten temporären Objekt gespeichert werden, werden an den Parameter *FileData* übergeben. Das Cmdlet **Import-SomeData** verarbeitet die Eingabe und führt die erforderlichen Aktionen aus.

Einige Cmdlets verwenden die folgende alternative Syntax, mit der dieselben Aktionen ausgeführt werden wie bei Verwendung der vorhergehenden Syntax.

    [Byte[]]$Data = Get-Content -Path <local path to file> -Encoding Byte -ReadCount 0
    Import-SomeData -FileData $Data

Mit dieser alternativen Syntax wird derselbe Vorgang ausgeführt. Der einzige Unterschied besteht darin, dass nicht umgehend der gesamte Vorgang ausgeführt wird. Die aus der lokalen Datei abgerufenen Daten werden in einer Variablen gespeichert, die nach der Erstellung referenziert werden kann. Die Variable wird anschließend im Importbefehl verwendet, um die Inhalte der lokalen Datei an das Cmdlet **Import-SomeData** zu übergeben. Dieser zwei Schritte umfassende Vorgang ist nützlich, wenn Sie die Daten aus der lokalen Datei in mehreren Befehlen verwenden möchten.

Beim Importieren von Dateien müssen einige Einschränkungen berücksichtigt werden. Weitere Informationen finden Sie weiter unten in diesem Thema unter "Einschränkungen für das Importieren von Dateien".

Spezifische Informationen zum Importieren von Daten in Exchange 2013 finden Sie in den Hilfethemen zur Funktion, die Sie verwalten.

## Einschränkungen für das Importieren von Dateien

Beim Importieren von Daten in der Remoteshell müssen Grenzwerte festgelegt werden, um die Integrität der übertragenen Daten zu erhalten. Gegenwärtig ausgeführte Übertragungen, die unterbrochen werden, können nicht fortgesetzt werden. Da die übertragenen Daten im Arbeitsspeicher des Remoteservers gespeichert werden, muss der Server gegen Speichererschöpfung aufgrund von extrem großen Datenmengen geschützt werden.

Aus diesen Gründen wird die Datenmenge, die von einem lokalen Computer oder Server an einen Exchange 2013-Remoteserver übertragen wird, auf folgende Größe begrenzt:

  - 500 Megabytes (MB) für jedes Cmdlet, das ausgeführt wird

  - 75 MB für jedes Objekt, das an ein Cmdlet übergeben wird

Wenn diese Grenzwerte überschritten werden, werden die Ausführung des Cmdlets und die verknüpfte Pipeline angehalten, und es wird ein Fehler ausgegeben. Anhand der Beispiele in der folgenden Tabelle soll die Funktionsweise dieser Grenzwerte veranschaulicht werden.

### Beispiele für Grenzwerte beim Importieren von Daten

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Anzahl von Objekten</th>
<th>Objektgröße (MB)</th>
<th>Gesamtgröße (MB)</th>
<th>Ergebnis des Vorgangs</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>10</p></td>
<td><p>40</p></td>
<td><p>400</p></td>
<td><p>Der Vorgang wird erfolgreich ausgeführt, da weder die Größe der einzelnen Objekte den Wert 75 MB noch die Gesamtgröße der an das Cmdlet übergebenen Daten den Wert 500 MB übersteigt.</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>80</p></td>
<td><p>400</p></td>
<td><p>Der Vorgang wird nicht erfolgreich ausgeführt. Wenngleich die Gesamtgröße der an das Cmdlet übergebenen Daten nur 400 MB beträgt, überschreitet die Größe der einzelnen Objekte den Grenzwert von 75 MB.</p></td>
</tr>
<tr class="odd">
<td><p>120</p></td>
<td><p>5</p></td>
<td><p>600</p></td>
<td><p>Der Vorgang wird nicht erfolgreich ausgeführt. Wenngleich die Größe der einzelnen Objekte nur 5 MB beträgt, überschreitet die Gesamtgröße der an das Cmdlet übergebenen Daten den Grenzwert von 500 MB.</p></td>
</tr>
</tbody>
</table>


Aufgrund der Größenbeschränkung der Datenmenge, die zwischen einem Exchange 2013-Remoteserver und einem lokalen Computer übertragen werden kann, unterstützen nicht alle Cmdlets, die zuvor Importvorgänge unterstützt haben, diese Datenübertragungsmethode. In den Hilfeinformationen zum jeweiligen Cmdlet wird erklärt, ob ein bestimmtes Cmdlet diese Methode unterstützt.

Diese Grenzwerte sollten die Mehrzahl der üblichen Vorgänge abdecken, die auf einem Exchange 2013-Server erfolgen können. Wenn geringere Grenzwerte festgelegt werden, können einige normale Vorgänge möglicherweise nicht erfolgreich ausgeführt werden, da sie die neuen Grenzwerte überschreiten. Wenn höhere Grenzwerte festgelegt werden, kann die Übertragung der Daten länger dauern, und das Risiko vorübergehender Zustände wird erhöht, die zu einer Unterbrechung der Datenübertragung führen. Zudem kann auf dem Remoteserver eine Speichererschöpfung auftreten, wenn keine ausreichende Arbeitsspeicherkapazität verfügbar ist, um während der Datenübertragung den gesamten Datenblock zu speichern. Da diese Situationen zu Datenverlust führen können, sollten die Grenzwerte nicht geändert werden.

## Exportieren von Dateien in der Remoteshell

Die Syntax zum Exportieren von Dateien in Exchange 2013 wird immer dann verwendet, wenn Sie Daten von einem auf einem Exchange 2013-Remoteserver ausgeführten Cmdlet akzeptieren und die Daten auf Ihrem lokalen Computer oder Server speichern möchten. Cmdlets, die Daten bereitstellen, die Sie in einer lokalen Datei speichern können, geben ein Objekt aus, das die Eigenschaft **FileData** (o. ä.) enthält. Abhängig vom Cmdlet wird die Eigenschaft **FileData** nur für das Objekt gefüllt, das in spezifischen Situationen ausgegeben wird. Lesen Sie zum Bestimmen der ordnungsgemäßen zu verwendenden Eigenschaft die Hilfeinformationen zum verwendeten Cmdlet.

Die Shell muss wissen, dass Sie die in der Eigenschaft **FileData** gespeicherten Daten auf Ihrem lokalen Computer speichern möchten. Verwenden Sie zu diesem Zweck die folgende Syntax.

    <cmdlet> | ForEach { $_.FileData | Add-Content <local path to file> -Encoding Byte }

Über den folgenden Befehl werden die in der Eigenschaft **FileData** gespeicherten Daten für das Objekt exportiert, das über das fiktionale Cmdlet **Export-SomeData** erstellt wurde. Die exportierten Daten werden in einer von Ihnen angegebenen Datei auf dem lokalen Computer gespeichert, in diesem Fall MyData.dat.


> [!NOTE]
> Für dieses Verfahren werden das Cmdlet <STRONG>ForEach</STRONG>, Objekte und das Pipelining verwendet. Weitere Informationen zu diesen Cmdlets finden Sie unter <A href="https://technet.microsoft.com/de-de/library/aa998260(v=exchg.150)">Pipelining</A> und <A href="https://technet.microsoft.com/de-de/library/aa996386(v=exchg.150)">Strukturierte Daten</A>.



    Export-SomeData | ForEach { $_.FileData | Add-Content C:\MyData.dat -Encoding Byte }

Wenn der Befehl ausgeführt wird, werden folgende Aktionen ausgeführt:

1.  Der Befehl wird von der Remoteshell akzeptiert.

2.  Die Remoteshell ruft das Cmdlet **Export-SomeData** auf dem Exchange 2013-Remoteserver auf.

3.  Das vom Cmdlet **Export-SomeData** erstellte Ausgabeobjekt wird über die Pipeline erneut an die lokale Shellsitzung übergeben.

4.  Das Ausgabeobjekt wird dann mittels Pipe an das Cmdlet **ForEach** übergeben, das über einen Skriptblock verfügt.

5.  Innerhalb des Skriptblocks wird auf die Eigenschaft **FileData** für das aktuelle Objekt in der Pipeline zugegriffen. Die in der Eigenschaft **FileData** enthaltenen Daten werden mittels Pipe an das Cmdlet **Add-Content** übergeben.

6.  Das Cmdlet **Add-Content** speichert die mittels Pipe aus der Eigenschaft **FileData** übergebenen Daten in der Datei MyData.dat im lokalen Dateisystem.

Spezifische Informationen zum Exportieren von Daten aus Exchange 2013 finden Sie in den Hilfethemen zur Funktion, die Sie verwalten.

