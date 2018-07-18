---
title: 'Cmdlet-Erweiterungs-Agents: Exchange 2013 Help'
TOCTitle: Cmdlet-Erweiterungs-Agents
ms:assetid: 0257790d-3988-46c3-8882-25ca11559e84
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335054(v=EXCHG.150)
ms:contentKeyID: 50554763
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Cmdlet-Erweiterungs-Agents

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Cmdlet-Erweiterungs-Agents sind Komponenten in Microsoft Exchange Server 2013, die bei der Ausführung von Exchange 2013-Cmdlets aufgerufen werden. Wie der Name sagt, erweitern Cmdlet-Erweiterungs-Agents die Funktionen der aufrufenden Cmdlets, indem sie ihnen beim Verarbeiten von Daten oder bei der Durchführung zusätzlicher Aktionen helfen, die auf den Anforderungen des Cmdlets basieren. Cmdlet-Erweiterungs-Agents sind für alle Serverrollen verfügbar.

Agents können die Funktionalität von Cmdlets der Exchange-Verwaltungsshell ändern, ersetzen oder erweitern. Ein Agent kann einen Wert für einen erforderlichen Parameter bereitstellen, der für einen Befehl nicht bereitgestellt wurde, einen von einem Benutzer bereitgestellten Wert außer Kraft setzen, während der Ausführung eines Cmdlets weitere Aktionen außerhalb des Cmdlet-Workflows durchführen usw.

Beispielsweise akzeptiert das Cmdlet **New-Mailbox** den Parameter *Database*, mit dem die Postfachdatenbank angegeben wird, in der ein neues Postfach erstellt werden soll. Wenn Sie in Microsoft Exchange Server 2007 den Parameter *Database* bei der Ausführung des Cmdlets **New-Mailbox** nicht angeben, missling der Befehl. In Exchange 2013 ruft das Cmdlet **New-Mailbox** jedoch bei seiner Ausführung den `Mailbox Resources Management`-Agent auf. Wenn der Parameter *Database* nicht angegeben ist, bestimmt der `Mailbox Resources Management`-Agent automatisch eine geeignete Postfachdatenbank, in der das neue Postfach erstellt werden soll, und fügt diesen Wert in den Parameter *Database* ein.

Cmdlet-Erweiterungs-Agents können nur von Exchange 2013- und Microsoft Exchange Server 2010-Cmdlets aufgerufen werden. Exchange 2007-Cmdlets und Cmdlets anderer Microsoft- und Drittanbieterprodukte können keine Cmdlet-Erweiterungs-Agents aufrufen. Auch über Skripts können Cmdlet-Erweiterungs-Agents nicht direkt aufgerufen werden. Wenn Skripts jedoch Exchange 2013-Cmdlets enthalten, können diese Cmdlets die Cmdlet-Erweiterungs-Agents aufrufen.

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Cmdlet-Erweiterungs-Agents gibt? Weitere Informationen finden Sie unter [Verwalten von Cmdlet-Erweiterungs-Agents](manage-cmdlet-extension-agents-exchange-2013-help.md).

## Priorität von Agents

Die Priorität eines Agents bestimmt, in welcher Reihenfolge der Agent bei der Ausführung eines Cmdlets aufgerufen wird. Ein Agent mit höherer Priorität (näher an 0) wird früher aufgerufen. Die Priorität eines Agents ist von Bedeutung, wenn mindestens zwei Agents versuchen, den Wert derselben Eigenschaft festzulegen. Der Agent mit der höchsten Priorität, der einen Eigenschaftswert festzulegen versucht, ist erfolgreich. Alle nachfolgenden Versuche von Agents mit geringerer Priorität, dieselbe Eigenschaft festzulegen, werden ignoriert. Wenn beispielsweise die Eigenschaft **Name** eines Objekts von einem Agent mit Priorität 3 geändert wird und ein anderer Agent mit Priorität 6 dasselbe Objekt ändert, wird die Änderung des Agents mit Priorität 6 ignoriert.

Wenn Sie den `Scripting agent` verwenden möchten, um die Werte von Eigenschaften festzulegen, die möglicherweise von anderen Agents mit höherer Priorität festgelegt werden, haben Sie folgende Optionen:

  - Deaktivieren Sie den Agent, der die Eigenschaft zurzeit festlegt.

  - Legen Sie für den `Scripting agent` eine höhere Priorität als für den zu ersetzenden Agent fest.

  - Legen Sie die Prioritäten beider Agents auf denselben Wert fest, und stellen Sie sicher, dass das Skript, das der `Scripting agent` ausführt, den von anderen Agents bereitgestellten Wert beibehält.


> [!WARNING]
> Das Ändern der Priorität oder das Ersetzen der Funktionalität eines integrierten Agents stellt einen erweiterten Vorgang dar. Stellen Sie sicher, dass Sie die Auswirkungen der Änderungen vollständig verstehen, die Sie vornehmen.



Weitere Informationen zum Ändern der Priorität eines Agents finden Sie unter [Verwalten von Cmdlet-Erweiterungs-Agents](manage-cmdlet-extension-agents-exchange-2013-help.md).

## Integrierte Agents

Exchange 2013 enthält mehrere Agents, die bei der Ausführung eines Cmdlets aufgerufen werden können. In der folgenden Tabelle werden die Agents, ihre Reihenfolge und die Information, ob die Agents standardmäßig aktiviert sind, aufgeführt. Auf einem Server mit Exchange 2013 können Sie keine Agents hinzufügen oder entfernen. Sie können allerdings den `Scripting agent` zum Ausführen von Windows PowerShell-Skripts nutzen, um die Funktionalität der Cmdlets zu erweitern, die ihn verwenden. Weitere Informationen zum `Scripting agent` finden Sie weiter unten in diesem Thema im Abschnitt "Skript-Agent".

Sie können die meisten Agents aktivieren oder deaktivieren oder die Priorität der Agents ändern, wenn Sie die Funktionalität eines bestimmten Agents durch Funktionalität in einem benutzerdefinierten Skript ersetzen möchten, das der `Scripting agent` aufruft. Einige Agents können jedoch nicht deaktiviert werden. Agents, die nicht deaktiviert werden können, heißen *System-Agents*. Ihre Eigenschaft *IsSystem* ist auf `$True` festgelegt. Die folgende Tabelle enthält Informationen zu Erweiterungs-Agents für Exchange 2013-Cmdlets, einschließlich System-Agents.

Die Konfiguration für Agents wird auf der Organisationsebene gespeichert. Wenn Sie einen Agent aktivieren, deaktivieren oder seine Priorität festlegen, legen Sie die entsprechende Agentkonfiguration für jeden Server in der Organisation fest. Die Ausnahme ist das Hinzufügen von Skripts im `Scripting agent`. Sie müssen die Skripts auf jedem Server einzeln aktualisieren. Weitere Informationen zum Konfigurieren von Skripts für die Verwendung mit dem `Scripting agent` finden Sie weiter unten in diesem Thema im Abschnitt "Skript-Agent".


> [!WARNING]
> Wenn Sie die Priorität von Agents ändern oder Agents aktivieren oder deaktivieren, ohne vollständig zu verstehen, welche Aktionen jeder Agent ausführt und wie die Agents mit Exchange-Cmdlets interagieren, können unbeabsichtigte Auswirkungen auftreten. Stellen Sie vor dem Ändern einer Agentkonfiguration sicher, dass Sie die Änderungen und die gewünschten Ergebnisse vollständig verstehen, und überprüfen Sie, ob Ihr benutzerdefiniertes Skript Ihren Absichten gemäß arbeitet.



### Cmdlet-Erweiterungs-Agents von Exchange 2013

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Agents</th>
<th>Priorität</th>
<th>Standardmäßig aktiviert</th>
<th>System-Agent</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Admin Audit Log agent</code></p></td>
<td><p>255</p></td>
<td><p>True</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><code>Scripting agent</code></p></td>
<td><p>6</p></td>
<td><p>False</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p><code>Mailbox Resources Management agent</code></p></td>
<td><p>5</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p><code>OAB Resources Management agent</code></p></td>
<td><p>4</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p><code>Query Base DN agent</code></p></td>
<td><p>3</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p><code>Provisioning Policy agent</code></p></td>
<td><p>2</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p><code>Rus agent</code></p></td>
<td><p>1</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p><code>Mailbox Creation Time agent</code></p></td>
<td><p>0</p></td>
<td><p>True</p></td>
<td><p>Nein</p></td>
</tr>
</tbody>
</table>


## Skript-Agent

Mithilfe des Cmdlet-Erweiterungs-Agents `Scripting agent` in Exchange 2013 können Sie Ihre eigene Skriptlogik in die Ausführung von Exchange-Cmdlets einbringen. Mit dem `Scripting agent` können Sie Bedingungen hinzufügen, Werte außer Kraft setzen und die Berichterstellung einrichten.


> [!WARNING]
> Wenn Sie den Cmdlet-Erweiterungs-Agent <CODE>Scripting agent</CODE> aktivieren, wird dieser immer aufgerufen, wenn ein Cmdlet auf einem Server ausgeführt wird, auf dem wiederum Exchange 2013 ausgeführt wird. Dies umfasst nicht nur Cmdlets, die von Ihnen direkt in der Exchange-Verwaltungsshell ausgeführt werden, sondern auch Cmdlets, die von Exchange-Diensten und der Exchange-Verwaltungskonsole ausgeführt werden. Es wird dringend empfohlen, dass Sie Ihre Skripts und alle an der Konfigurationsdatei vorgenommenen Änderungen testen, bevor Sie die aktualisierte Konfigurationsdatei auf Ihre Exchange 2013-Server kopieren und den Cmdlet-Erweiterungs-Agent <CODE>Scripting agent</CODE> aktivieren.



Sobald ein Exchange-Cmdlet ausgeführt wird, ruft das Cmdlet den Cmdlet-Erweiterungs-Agent `Scripting agent` auf. Wenn dieser Agent aufgerufen wird, überprüft das Cmdlet, ob Skripts konfiguriert sind, die vom Cmdlet aufgerufen werden können. Wenn ein Skript für ein Cmdlet ausgeführt werden soll, versucht das Cmdlet, alle im Skript definierten APIs aufzurufen. Die folgenden APIs sind verfügbar und werden in der folgenden Reihenfolge aufgerufen:

1.  **ProvisionDefaultProperties**   Mithilfe dieser API können Werte von Eigenschaften für Objekte bei deren Erstellung festgelegt werden. Wenn Sie einen Wert festlegen, wird dieser Wert an das Cmdlet zurückgegeben, und das Cmdlet legt den Wert für die Eigenschaft fest. Sie können Werte für Eigenschaften ausfüllen, wenn der Benutzer keinen Wert angegeben hat, oder Sie können den vom Benutzer angegebenen Wert außer Kraft setzen. Diese API berücksichtigt die Werte, die von Agents mit höherer Priorität festgelegt wurden. Der Cmdlet-Erweiterungs-Agent `Scripting agent` setzt keine Werte außer Kraft, die von Agents mit höherer Priorität festgelegt wurden.

2.  **UpdateAffectedIConfigurable**   Mithilfe dieser API können die Werte von Eigenschaften für Objekte festgelegt werden, nachdem alle anderen Verarbeitungsschritte abgeschlossen sind, aber die `Validate`-API noch nicht aufgerufen wurde. Diese API berücksichtigt die Werte, die von Agents mit höherer Priorität festgelegt wurden. Der Cmdlet-Erweiterungs-Agent `Scripting agent` setzt keine Werte außer Kraft, die von Agents mit höherer Priorität festgelegt wurden.

3.  **Validate**   Mithilfe dieser API können die Werte der Eigenschaften eines Objekts bestätigt werden, die vom Cmdlet festgelegt werden sollen. Diese API wird aufgerufen, kurz bevor ein Cmdlet mit dem Schreiben von Daten beginnt. Sie können Datenprüfungen konfigurieren, mit denen ein Cmdlet entweder erfolgreich ausgeführt werden oder fehlschlagen kann. Wenn ein Cmdlet die Datenprüfungen in dieser API besteht, darf das Cmdlet die Daten schreiben. Wenn das Cmdlet die Datenprüfungen nicht besteht, gibt es alle in dieser API definierten Fehler zurück.

4.  **OnComplete**   Diese API wird verwendet, nachdem sämtliche Cmdlet-Verarbeitungen abgeschlossen sind. Mit ihrer Hilfe können Nachbearbeitungsaufgaben ausgeführt werden, z. B. das Schreiben von Daten in eine externe Datenbank.


> [!NOTE]
> Der Cmdlet-Erweiterungs-Agent <CODE>Scripting agent</CODE> wird nicht aufgerufen, wenn die Cmdlets mit dem Verb <CODE>Get</CODE> ausgeführt werden.



## Konfigurationsdatei des Skript-Agents

Die `Scripting agent`-Konfigurationsdatei enthält alle Skripts, die der `Scripting agent` ausführen soll. Skripts in der Konfigurationsdatei sind innerhalb von XML-Tags enthalten, die den Anfang und das Ende des Skripts und verschiedene Eingabeparameter definieren, die zum Übergeben von Daten an das Skript erforderlich sind. Skripts werden mithilfe der Windows PowerShell-Syntax geschrieben. Die Konfigurationsdatei ist eine XML-Datei, die die Elemente oder Attribute in der folgenden Tabelle verwendet.

### Attribute der Skript-Agent-Konfigurationsdatei

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Attribut</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Configuration</code></p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Dieses Element enthält alle Skripts, die vom Cmdlet-Erweiterungs-Agent <code>Scripting agent</code> ausgeführt werden können. Das <code>Feature</code>-Tag ist ein untergeordnetes Element dieses Tags.</p>
<p>Es gibt nur ein <code>Configuration</code>-Tag in der Konfigurationsdatei.</p></td>
</tr>
<tr class="even">
<td><p><code>Feature</code></p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Dieses Element enthält eine Reihe von Skripts, die sich auf eine Funktion beziehen. Jedes im untergeordneten <code>ApiCall</code>-Tag definierte Skript erweitert einen bestimmten Teil der Cmdlet-Ausführungspipeline. Dieses Tag enthält die Attribute <code>Name</code> und <code>Cmdlets</code>.</p>
<p>Es kann mehrere <code>Feature</code>-Tags unter dem <code>Configuration</code>-Tag geben.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>Name</code></p></td>
<td><p>Dieses Attribut enthält den Namen der Funktion. Mithilfe dieses Attributs können Sie bei der Ermittlung helfen, welche Funktion von den im Tag enthaltenen Skripts erweitert wird.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>Cmdlets</code></p></td>
<td><p>Dieses Attribut enthält eine Liste der Exchange-Cmdlets, von denen die Skripts in dieser Funktionserweiterung verwendet werden. Mehrere Cmdlets können durch Kommata getrennt angegeben werden.</p></td>
</tr>
<tr class="odd">
<td><p><code>ApiCall</code></p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Dieses Element enthält Skripts, die einen Teil der Cmdlet-Ausführungspipeline erweitern können. Jedes Skript wird durch den API-Aufrufnamen in der Cmdlet-Ausführungspipeline definiert, die dieses erweitert. Nachfolgend finden Sie die API-Namen, die ausgeführt werden können:</p>
<ul>
<li><p><code>ProvisionDefaultProperties</code></p></li>
<li><p><code>UpdateAffectedIConfigurable</code></p></li>
<li><p><code>Validate</code></p></li>
<li><p><code>OnComplete</code></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>Name</code></p></td>
<td><p>Dieses Attribut umfasst den Namen des API-Aufrufs, der die Cmdlet-Ausführungspipeline erweitert.</p></td>
</tr>
<tr class="odd">
<td><p><code>Common</code></p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Dieses Element enthält Funktionen, die von einem beliebigen Skript in der Konfigurationsdatei verwendet werden können.</p></td>
</tr>
</tbody>
</table>


Jeder Exchange 2013-Server enthält die Datei "ScriptingAgentConfig.xml.sample" im Ordner "\<*installation path*\>\\V15\\Bin\\CmdletExtensionAgents". Diese Datei muss auf jedem Exchange 2013-Server in "ScriptingAgentConfig.xml" umbenannt werden, wenn Sie den Cmdlet-Erweiterungs-Agent "Skript-Agent" aktivieren. Die Beispielkonfigurationsdatei enthält Beispielskripts, mit denen Sie herausfinden können, wie Skripts zur Konfigurationsdatei hinzugefügt werden.

Nachdem Sie ein Skript zur Konfigurationsdatei hinzugefügt oder eine Änderung an der Konfigurationsdatei vorgenommen haben, müssen Sie die Datei auf jedem Exchange 2013-Server im Unternehmen aktualisieren. Dies muss durchgeführt werden, um sicherzustellen, dass jeder Server eine aktuelle Version der Skripts enthält, die vom Cmdlet-Erweiterungs-Agent `Scripting Agent` ausgeführt werden.

Einige Zeichen, die typischerweise in Skripts verwendet werden, haben in XML auch eine spezielle Bedeutung. Verwenden Sie Escapefolgen, um diese Zeichen in Ihrem Skript zu verwenden. Die folgenden Zeichen verwenden z. B. eine Escapefolge:

  - Verwenden Sie anstelle des Größer-als-Zeichens (`>`) die Folge `&gt;`

  - Verwenden Sie anstelle des Kleiner-als-Zeichens (`<`) die Folge `$lt;`

  - Verwenden Sie anstelle eines kaufmännischen Und-Zeichens (`&`) die Folge `&amp;`

## Aktivieren des Skript-Agents

Der Cmdlet-Erweiterungs-Agent `Scripting agent` ist standardmäßig deaktiviert. Wenn Sie den `Scripting agent` aktivieren, ist der Agent für die gesamte Exchange 2013-Organisation aktiviert. Bevor Sie den `Scripting agent` aktivieren, überprüfen Sie, ob die Konfigurationsdatei des `Scripting agent`s ordnungsgemäß umbenannt und mit Ihren Skripts auf jedem Exchange 2013-Server aktualisiert wurde. Sie erhalten bei jeder Ausführung eines Cmdlets eine Fehlermeldung, wenn Sie die Konfigurationsdatei nicht ordnungsgemäß umbenennen oder eine Konfigurationsdatei von einem anderen Exchange 2013-Server auf diesen Computer kopieren.

Gehen Sie wie folgt vor, um den `Scripting agent` zu aktivieren:

1.  Benennen Sie die Beispieldatei "ScriptingAgentConfig.xml.sample" in **\<Installationspfad\>\\V15\\Bin\\CmdletExtensionAgents** auf jedem Exchange 2013-Server in Ihrem Unternehmen in "ScriptingAgentConfig.xml" um.
    

    > [!NOTE]
    > Sie können die Konfigurationsdatei von einem Exchange 2013-Server auf andere Exchange 2013-Server kopieren. Stellen Sie sicher, dass Sie die zu kopierende Konfigurationsdatei aktualisieren, bevor Sie sie kopieren.



2.  Fügen Sie Ihr Skript auf jedem Exchange 2013-Server im Unternehmen zur umbenannten Konfigurationsdatei hinzu.

3.  Aktivieren Sie den Cmdlet-Erweiterungs-Agent `Scripting agent`. Weitere Informationen zum Aktivieren von Cmdlet-Erweiterungs-Agents finden Sie unter [Verwalten von Cmdlet-Erweiterungs-Agents](manage-cmdlet-extension-agents-exchange-2013-help.md).

## Skript-Agent-Priorität

Der Cmdlet-Erweiterungs-Agent `Scripting agent` wird standardmäßig nach jedem anderen Agent ausgeführt, mit Ausnahme des Agents `Scripting agent`. Wenn ein von Ihnen erstelltes Skript einen vorhandenen Agent ersetzen soll, müssen Sie den anderen Agent entweder deaktivieren oder die Priorität eines der Agents ändern, damit der Cmdlet-Erweiterungs-Agent `Scripting agent` zuerst ausgeführt wird. Weitere Informationen zum Deaktivieren oder Ändern der Priorität von Agents finden Sie unter [Verwalten von Cmdlet-Erweiterungs-Agents](manage-cmdlet-extension-agents-exchange-2013-help.md).

