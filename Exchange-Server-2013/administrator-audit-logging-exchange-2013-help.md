---
title: 'Administratorüberwachungsprotokollierung: Exchange 2013 Help'
TOCTitle: Administratorüberwachungsprotokollierung
ms:assetid: 22b17eb8-d8ee-4599-b202-d6a7928c20d9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335144(v=EXCHG.150)
ms:contentKeyID: 50554797
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Administratorüberwachungsprotokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-03-05_

Mit der Administrator-Überwachungsprotokollierung in Microsoft Exchange Server 2013 können Sie protokollieren, wann ein Benutzer oder ein Administrator eine Änderung an der Organisation vornimmt. Indem Sie ein Protokoll der Änderungen führen, können Sie u. a. Änderungen der Person zuordnen, die sie vorgenommen hat, Änderungsprotokollen ausführliche Datensätze der implementierten Änderung hinzufügen, rechtliche Bestimmungen einhalten und Auskunftserteilungsanforderungen erfüllen.

Standardmäßig ist die Überwachungsprotokollierung in Neuinstallationen von Exchange 2013 aktiviert.

**Inhalt**

What gets audited

Audit logging configuration

Audit logs

Manual audit log entries

Active Directory replication

Admin Audit Log agent

## Was wird überwacht

Cmdlets, die direkt in der Exchange-Verwaltungsshell ausgeführt werden, werden überwacht. Darüber hinaus werden auch Vorgänge protokolliert, die mit der Exchange-Verwaltungskonsole ausgeführt werden, da diese Vorgänge Cmdlets im Hintergrund ausführen.

Cmdlets, unabhängig davon, in dem sie ausgeführt werden, überwacht werden sollen, wenn ein Cmdlet ist, im Cmdlet Überwachung Liste und eine oder mehrere Parameter für dieses Cmdlet auf Parameter Überwachungsliste befinden. Überwachungsprotokollierung ist für die direkte Verwendung anzeigen, welche Aktionen durchgeführt worden sind, ändern Sie Objekte in einer Organisation Exchange statt, welche Objekte angezeigt wurden.


> [!IMPORTANT]
> Ein Cmdlet wird möglicherweise nicht protokolliert, wenn ein Fehler auftritt, bevor das Cmdlet den Cmdlet-Erweiterungs-Agent für das Administratorüberwachungsprotokoll aufruft. Tritt ein Fehler auf, nachdem der Administratorüberwachungsprotokoll-Agent aufgerufen wurde, wird das Cmdlet zusammen mit dem zugeordneten Fehler protokolliert. Weitere Informationen finden Sie im Abschnitt Admin Audit Log Agent weiter unten in diesem Thema.<BR>Änderungen, die mit Microsoft Exchange Server 2010-Verwaltungstools vorgenommen wurden, werden protokolliert. Jedoch werden Änderungen, die mit Microsoft Exchange Server&nbsp;2007-Verwaltungstools vorgenommen wurden, nicht protokolliert.<BR>Änderungen an der Überwachungsprotokollkonfiguration werden alle 60 Minuten auf Computern aktualisiert, deren Shell zum Zeitpunkt einer Konfigurationsänderung geöffnet ist. Wenn Sie die Änderungen sofort anwenden möchten, schließen Sie die Shell auf den einzelnen Computern, und öffnen sie dann wieder.<BR>Es dauert bis zu 15 Minuten nach dem Ausführen eines Befehls, bis dieser in den Suchergebnissen in des Überwachungsprotokolls angezeigt wird. Der Grund hierfür liegt darin, dass Überwachungsprotokolleinträge indiziert werden müssen, bevor sie durchsucht werden können. Wenn ein Befehl nicht im Administratorüberwachungsprotokoll aufgeführt wird, warten Sie einige Minuten, und führen Sie dann die Suche erneut aus.



## Konfiguration der Überwachungsprotokollierung

Wenn die überwachungsprotokollierung aktiviert ist, wird standardmäßig ein Protokolleintrag erstellt jedes Mal, wenn eine beliebige Cmdlet ausgeführt wird. Wenn Sie nicht jedes Cmdlet überwachen, die ausgeführt wird, möchten, können Sie konfigurieren, überwachungsprotokollierung zum Überwachen von nur den Cmdlets und Parameter, die, denen Sie interessiert sind. Konfigurieren der überwachungsprotokollierung mit dem Cmdlet **Set-AdminAuditLogConfig** . Der Parameter verwiesen wird, in den folgenden Abschnitten werden die mit diesem Cmdlet verwendet.


> [!IMPORTANT]
> Änderungen an der Administrator-Überwachungsprotokollkonfiguration werden unabhängig davon, ob das Cmdlet <STRONG>Set-AdministratorAuditLog</STRONG> in der Liste der zu protokollierenden Cmdlets enthalten ist und ob die Überwachungsprotokollierung aktiviert oder deaktiviert ist, immer protokolliert.



Wenn ein Befehl ausgeführt wird, prüft Exchange das verwendete Cmdlet. Wenn das ausgeführte Cmdlet mit einem Cmdlet übereinstimmt, das mit dem Parameter *AdminAuditLogConfigCmdlets* bereitgestellt wurde, überprüft Exchange die Parameter, die im Parameter *AdminAuditLogConfigParameters* angegeben sind. Stimmt mindestens ein Parameter in der Parameterliste überein, protokolliert Exchange das ausgeführte Cmdlet im Postfach, das mit dem Parameter *AdminAuditLogMailbox* angegeben wird. Die folgenden Abschnitte enthalten weitere Informationen zu den einzelnen Aspekten der Konfiguration der Überwachungsprotokollierung.

Weitere Informationen zum Verwalten der Konfiguration der Überwachungsprotokollierung finden Sie unter [Verwalten der Administratorüberwachungsprotokollierung](manage-administrator-audit-logging-exchange-2013-help.md).

Zurück zum Seitenanfang

## Cmdlets

Sie können steuern, welche Cmdlets überwacht werden, indem Sie eine Liste der Cmdlets mit deren Parametern angeben, die Sie protokollieren möchten. Wenn Sie die Überwachungsprotokollierung konfigurieren, können Sie angeben, dass alle Cmdlets überwacht werden sollen. Mit dem Parameter *AdminAuditLogConfigCmdlets* können Sie aber auch spezielle Cmdlets angeben, die überwacht werden sollen. Sie können die vollständigen Namen der Cmdlets angeben, z. B. **New-Mailbox**, oder Sie können Teilnamen von Cmdlets angeben und in diese Namen Platzhalter wie ein Sternchen (`*`) einschließen. Wenn Sie beispielsweise protokollieren möchten, wann ein Cmdlet ausgeführt wird, das die Zeichenfolge `Transport` enthält, können Sie den Wert `*Transport*` angeben. Sie können eine Mischung aus vollständigen Namen und Teilnamen von Cmdlets gleichzeitig angeben, um die Konfiguration der Überwachungsprotokollierung auf Ihren Bedarf zuzuschneiden.

## Parameter

Neben der Angabe der Cmdlets, die Sie protokollieren möchten, können Sie auch die Cmdlets kennzeichnen, die nur protokolliert werden sollen, wenn bestimmte Parameter dieser Cmdlets verwendet werden. Verwenden Sie den Parameter *AdminAuditLogConfigParameters*, um anzugeben, welche Parameter protokolliert werden sollen. Wie bei den Cmdlets können Sie vollständige Namen von Parametern, z. B. `Database`, oder Teilnamen von Parametern mit Platzhaltern (`*`), z. B. `*Address*`, oder eine Kombination aus beidem angeben.

## Verfallszeit für Überwachungsprotokolle

Standardmäßig ist die Überwachungsprotokollierung so konfiguriert, dass Überwachungsprotokolleinträge 90 Tage lang gespeichert werden. Nach 90 Tagen wird der Überwachungsprotokolleintrag gelöscht. Sie können die Verfallszeit für Überwachungsprotokolle mithilfe des Parameters *AdminAuditLogAgeLimit* ändern. Sie können die Anzahl der Tage, Stunden, Minuten und Sekunden angeben, die Überwachungsprotokolleinträge gespeichert werden. Verwenden Sie zum Angeben eines Werts das Format `dd.hh:mm:ss`, wobei Folgendes gilt:

  - **dd**   Die Anzahl der Tage, die der Überwachungsprotokolleintrag gespeichert werden soll.

  - **hh**   Die Anzahl der Stunden, die der Überwachungsprotokolleintrag gespeichert werden soll.

  - **mm**   Die Anzahl der Minuten, die der Überwachungsprotokolleintrag gespeichert werden soll.

  - **ss**   Die Anzahl der Sekunden, die der Überwachungsprotokolleintrag gespeichert werden soll.

Geben Sie mehrere Jahre im Feld `dd` ein. So ergeben beispielsweise 365 Tage ein Jahr, 730 Tage zwei Jahre und 913 Tage zwei Jahre und sechs Monate. Verwenden Sie beispielsweise die Syntax `913.00:00:00`, um die Verfallszeit für Überwachungsprotokolle auf zwei Jahre und sechs Monate festzulegen.


> [!WARNING]
> Sie können die Verfallszeit für Überwachungsprotokolle auch auf einen Wert unter der derzeitigen Verfallszeit festlegen. In diesem Fall wird jeder Überwachungsprotokolleintrag, der die neue Verfallszeit überschreitet, gelöscht.<BR>Wenn Sie die Verfallszeit auf 0 festlegen, löscht Exchange alle Einträge im Überwachungsprotokoll.<BR>Es wird empfohlen, nur äußerst vertrauenswürdigen Benutzern die Berechtigung zur Konfiguration der Verfallszeit für Überwachungsprotokolle zu erteilen.



## Ausführliche Protokollierung

Standardmäßig werden im Administrator-Überwachungsprotokoll nur der Cmdlet-Name, Cmdlet-Parameter (und angegebene Werte), das geänderte Objekt, der Benutzer, der das Cmdlet ausgeführt hat, der Zeitpunkt der Cmdlet-Ausführung und der Server, auf dem das Cmdlet ausgeführt wurde, aufgezeichnet. Im Administrator-Überwachungsprotokoll wird nicht protokolliert, welche Eigenschaften des Objekts geändert wurden. Wenn das Überwachungsprotokoll auch die geänderten Eigenschaften des Objekts enthalten soll, können Sie die ausführliche Protokollierung aktivieren, indem Sie den Parameter *LogLevel* auf `Verbose` festlegen. Wenn Sie die ausführliche Protokollierung aktivieren, werden neben den standardmäßig protokollieren Informationen auch die geänderten Eigenschaften eines Objekts, einschließlich der alten und neuen Werte, in das Überwachungsprotokoll aufgenommen.

## Test-Cmdlets

Cmdlets, die mit dem Verb **Test** beginnen, werden nicht standardmäßig protokolliert. Sie können angeben, dass **Test**-Cmdlets protokolliert werden sollen, indem Sie den Parameter *TestCmdletLoggingEnabled* auf `$true` festlegen. Zwar ist es möglich, die Protokollierung von Test-Cmdlets zu aktivieren, dies wird jedoch nur für kurze Zeit empfohlen, da Test-Cmdlets in großem Umfang Informationen erzeugen können.

## Überwachungsprotokolle

Jedes Mal, wenn ein Cmdlet protokolliert wird, wird ein Überwachungsprotokoll erstellt. Überwachungsprotokolle werden in einem verborgenen, dedizierten Vermittlungspostfach gespeichert, auf das nur über die Exchange-Verwaltungskonsole oder die Cmdlets **Search-AdminAuditLog** und **New-AdminAuditLogSearch** zugegriffen werden kann. Es kann nicht über Microsoft Outlook Web App oder Microsoft Outlook geöffnet werden. In den folgenden Abschnitten finden Sie weitere Informationen zu folgenden Themen:

  - Was ist in den Protokollen enthalten?

  - Auf der Seite **Überwachung** der Exchange-Verwaltungskonsole verfügbare Berichte

  - Cmdlets "Audit log search"

## Inhalte des Überwachungsprotokolls

Jeder Überwachungsprotokolleintrag enthält die Informationen, die in der folgenden Tabelle beschrieben sind. Das Überwachungsprotokoll enthält mindestens einen Überwachungsprotokolleintrag. Die Anzahl der Überwachungsprotokolleinträge wird von der Verfallszeit für Überwachungsprotokolle mithilfe des Cmdlets **Set-AdminAuditLogConfig** gesteuert. Alle Überwachungsprotokolleinträge, die die Verfallszeit überschreiten, werden gelöscht.

### Felder für Überwachungsprotokolleinträge

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feld</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>RunspaceId</code></p></td>
<td><p>Dieses Feld wird intern von Exchange verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>ObjectModified</code></p></td>
<td><p>Dieses Feld enthält das Objekt, das von dem im Feld <code>CmdletName</code> angegebenen Cmdlet geändert wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>CmdletName</code></p></td>
<td><p>Das Feld enthält den Namen des Cmdlets, das vom Benutzer im Feld <code>Caller</code> ausgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p><code>CmdletParameters</code></p></td>
<td><p>Dieses Feld enthält die Parameter, die angegeben wurden, als das Cmdlet im Feld <code>CmdletName</code> ausgeführt wurde. In diesem Feld wird auch, falls vorhanden, der in diesem Parameter angegebene Wert gespeichert, er wird jedoch nicht in der Standardausgabe angezeigt. Weitere Informationen zum Zugriff auf die zusätzlichen Informationen in diesem Feld finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes">Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle</a>.</p></td>
</tr>
<tr class="odd">
<td><p><code>ModifiedProperties</code></p></td>
<td><p>Dieses Feld enthält die Eigenschaften, die auf dem Objekt im Feld <code>ObjectModified</code> geändert wurden. In diesem Feld werden auch der alte Wert der Eigenschaft und der neue gespeicherte Wert gespeichert, sie werden jedoch nicht in der Standardausgabe angezeigt. Weitere Informationen zum Zugriff auf die zusätzlichen Informationen in diesem Feld finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes">Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle</a>.</p>

> [!IMPORTANT]
> Dieses Feld wird nur gefüllt, wenn der Parameter <EM>LogLevel</EM> für das Cmdlet <STRONG>Set-AdminAuditLogConfig</STRONG> auf <CODE>Verbose</CODE> festgelegt ist.


</td>
</tr>
<tr class="even">
<td><p><code>Caller</code></p></td>
<td><p>Dieses Feld enthält das Benutzerkonto des Benutzers, der das Cmdlet im Feld <code>CmdletName</code> ausgeführt hat.</p></td>
</tr>
<tr class="odd">
<td><p><code>Succeeded</code></p></td>
<td><p>Dieses Feld gibt an, ob das Cmdlet im Feld <code>CmdletName</code> erfolgreich ausgeführt wurde. Mögliche Werte sind <code>True</code> und <code>False</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>Error</code></p></td>
<td><p>Dieses Feld enthält die generierte Fehlermeldung, wenn das Cmdlet im Feld <code>CmdletName</code> nicht erfolgreich ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>RunDate</code></p></td>
<td><p>Dieses Feld enthält das Datum und die Uhrzeit, zu dem/der das Cmdlet im Feld <code>CmdletName</code> ausgeführt wurde. Datum und Uhrzeit werden im UTC-Format (Coordinated Universal Time, koordinierte Weltzeit) gespeichert.</p></td>
</tr>
<tr class="even">
<td><p><code>OriginatingServer</code></p></td>
<td><p>In diesem Feld wird der Server angegeben, auf dem das im Feld <code>CmdletName</code> angegebene Cmdlet ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>Identity</code></p></td>
<td><p>Dieses Feld wird intern von Exchange verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>IsValid</code></p></td>
<td><p>Dieses Feld wird intern von Exchange verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><code>ObjectState</code></p></td>
<td><p>Dieses Feld wird intern von Exchange verwendet.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Überwachungsberichte der Exchange-Verwaltungskonsole

Die Seite **Überwachung** der Exchange-Verwaltungskonsole umfasst verschiedene Berichte mit Informationen zu unterschiedlichen Arten von Konfigurationsänderungen bei der Richtlinientreue und der Verwaltung. Die folgenden Berichte enthalten Informationen zu Konfigurationsänderungen in der Organisation:

  - **Administrator-Rollengruppenbericht**   Dieser Bericht ermöglicht die Suche nach Änderungen an Verwaltungsrollengruppen, die Sie innerhalb eines bestimmten Zeitraums angeben. Die zurückgegebenen Ergebnisse umfassen Informationen zu geänderten Rollengruppen, dazu wer sie geändert hat, zum Zeitpunkt sowie zur Art der Änderungen. Es können maximal 3.000 Einträgen zurückgegeben werden. Wenn Ihre Suche möglicherweise mehr als 3.000 Einträge zurückgibt, verwenden Sie den Bericht **Administrator-Überwachungsprotokoll** oder das Cmdlet **Search-AdminAuditLog**.

  - **Administrator-Überwachungsprotokoll**   Dieser Bericht ermöglicht den Export von Überwachungsprotokolleinträgen, die in einem bestimmten Zeitraum aufgezeichnet wurden, in eine XML-Datei und das anschließende Versenden per E-Mail an die angegebenen Empfänger. Weitere Informationen zu Inhalten der XML-Datei finden Sie unter [Administrator-Überwachungsprotokollstruktur](administrator-audit-log-structure-exchange-2013-help.md).

Weitere Informationen zum Verwenden dieser Berichte finden Sie unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes).

Weitere Informationen zu den anderen Berichten auf der Seite **Überwachung** finden Sie unter [Exchange-Überwachungsberichte](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## Cmdlet "Search-AdminAuditLog"

Beim Ausführen des Cmdlets **Search-AdminAuditLog** werden alle Überwachungsprotokolleinträge, die den angegebenen Suchkriterien entsprechen, zurückgegeben. Sie können folgende Suchkriterien festlegen:

  - **Cmdlets**   Gibt die Cmdlets an, nach denen im Administrator-Überwachungsprotokoll gesucht werden soll.

  - **Parameter**   Gibt die Parameter (durch Kommas getrennt) an, nach denen im Administrator-Überwachungsprotokoll gesucht werden soll. Sie können nur nach Parametern suchen, wenn Sie ein Cmdlet, nach dem gesucht werden soll, angeben.

  - **Enddatum**   Umfasst die Administrator-Überwachungsprotokollergebnisse zum Protokollieren von Einträgen am oder vor dem angegebenen Datum.

  - **Startdatum**   Umfasst die Administrator-Überwachungsprotokollergebnisse zum Protokollieren von Einträgen am oder nach dem angegebenen Datum.

  - **Objekt-IDs**   Gibt an, dass nur Administrator-Überwachungsprotokolleinträge zurückgegeben werden, die die angegebenen geänderten Objekte enthalten

  - **Benutzer-IDs**   Gibt an, dass nur Administrator-Überwachungsprotokolleinträge zurückgegeben werden, die die angegebenen IDs des Benutzers enthalten, der das Cmdlet ausgeführt hat.

  - **Erfolgreicher Abschluss**   Gibt an, ob nur Administrator-Überwachungsprotokolleinträge zurückgegeben werden sollen, die einen erfolgreichen bzw. einen nicht erfolgreichen Vorgang anzeigen.

Jeder zurückgegebene Überwachungsprotokolleintrag enthält die Informationen, die in der Tabelle Audit Log Contents beschrieben sind. Standardmäßig werden nur die ersten 1.000 Protokolleinträge, die den angegebenen Suchergebnissen entsprechen, zurückgegeben. Sie können diesen Standardwert jedoch überschreiben und mehr oder weniger Einträge mithilfe des Parameters *ResultSize* zurückgeben lassen. Sie können einen Wert von `Unlimited` mit dem Parameter *ResultSize* angeben, um alle Protokolleinträge zurückgeben zu lassen, die den angegebenen Kriterien entsprechen.

Weitere Informationen zum Verwenden des Cmdlets **Search-AdminAuditLog** finden Sie unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes).

## Cmdlet "New-AdminAuditLogSearch"

Das Cmdlet **New-AdminAuditLogSearch** durchsucht das Überwachungsprotokoll wie das Cmdlet **Search-AdminAuditLog**. Anstatt die Ergebnisse der Suche im Überwachungsprotokoll jedoch in der Shell anzuzeigen, führt das Cmdlet **New-AdminAuditLogSearch** die Suche aus und sendet die Suchergebnisse per E-Mail an die angegebenen Empfänger. Die Ergebnisse werden als XML-Anlage in die E-Mail aufgenommen.

Sie können dieselben Suchkriterien beim Cmdlet **New-AdminAuditLogSearch** verwenden, die im Cmdlet **Search-AdminAuditLog** verwendet werden. Eine Liste mit Suchkriterien finden Sie unter Search-AdminAuditLog Cmdlet.

Nach dem Ausführen des Cmdlets **New-AdminAuditLogSearch** dauert es möglicherweise bis zu 15 Minuten, bis Exchange einen Bericht an den angegebenen Empfänger übermittelt. Die an den Bericht angehängte XML-Datei ist maximal 10 MB (Megabyte) groß. Die XML-Datei enthält dieselben Informationen wie in der Tabelle in Audit Log Contents beschrieben. Weitere Informationen zur Struktur der XML-Datei finden Sie unter [Administrator-Überwachungsprotokollstruktur](administrator-audit-log-structure-exchange-2013-help.md).


> [!NOTE]
> In Outlook Web App ist es standardmäßig nicht möglich, XML-Anlagen zu öffnen. Sie können Exchange entweder so konfigurieren, dass XML-Anlagen mit Outlook Web App angezeigt werden können, oder Sie verwenden einen anderen E-Mail-Client, beispielsweise Microsoft Outlook, um die Anlage anzuzeigen. Informationen zum Konfigurieren von Outlook Web App zum Zulassen der Anzeige einer XML-Anlage finden Sie unter <A href="view-or-configure-outlook-web-app-virtual-directories-exchange-2013-help.md">Anzeigen oder Konfigurieren der virtuellen Outlook Web App-Verzeichnisse</A>.



Weitere Informationen zum Verwenden des Cmdlets **New-AdminAuditLogSearch** finden Sie unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes).

Zurück zum Seitenanfang

## Manuelle Einträge im Überwachungsprotokoll

Zusätzlich zum Protokollieren der Ausführung von Exchange-Cmdlets ermöglicht Exchange 2013 das manuelle Schreiben von Protokolleinträgen in das Überwachungsprotokoll. Diese Funktion wird in Exchange 2013 über das Cmdlet **Write-AdminAuditLog** unterstützt. In folgenden Situationen werden Sie möglicherweise einen manuellen Protokolleintrag hinzufügen:

  - Benutzerdefinierter Skripteingang und -ausgang

  - Ändern von Steuerinformationen

  - Anfangs- und Endzeiten für Wartung

Mit dem Cmdlet **Write-AdminAuditLog** können Sie eine Textzeichenfolge mithilfe des Parameters *Comment* im Überwachungsprotokoll angeben. Der Parameter *Comment* akzeptiert eine alphanumerische Zeichenfolge aus bis zu 500 Zeichen. Im manuellen Überwachungsprotokolleintrag werden dieselben Informationen zusammen mit der Kommentarzeichenfolge erfasst, wie bei der Protokollierung eines Exchange-Cmdlets. Eine Beschreibung zu jedem Feld im Überwachungsprotokoll finden Sie in der Tabelle unter Audit Log Contents.

Sie können einen manuellen Überwachungsprotokolleintrag genau so abrufen wie einen anderen Protokolleintrag. Verwenden Sie dazu die Seite **Überwachung** der Exchange-Verwaltungskonsole oder die Cmdlets **Search-AdminAuditLog** und **New-AdminAuditLogSearch**.

Zum Anzeigen der Inhalte des Parameters *Comment* im Cmdlet **Write-AdminAuditLog** in einem manuellen Überwachungsprotokolleintrag finden Sie weitere Informationen unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes).

## Active Directory-Replikation

Die Administrator-Überwachungsprotokollierung verwendet die Active Directory-Replikation für die Replikation von Konfigurationseinstellungen, die Sie für die Domänencontroller in Ihrer Organisation festlegen. Je nach Replikationseinstellungen werden von Ihnen vorgenommene Änderungen möglicherweise nicht sofort auf alle Server mit Exchange 2013 oder Exchange 2010 in der Organisation angewendet.

## Administrator-Überwachungsprotokoll-Agent

Der integrierte Cmdlet-Erweiterungs-Agent für das Administratorüberwachungsprotokoll führt die Administratorüberwachungsprotokollierung von Cmdlet-Vorgängen in Exchange 2013 durch. Dieser Agent liest die Konfiguration der Überwachungsprotokolle und führt eine Bewertung der einzelnen Cmdlets aus, die in der Organisation ausgeführt werden. Wenn die Kriterien, die Sie in der Konfiguration des Überwachungsprotokolls angegeben haben, mit dem ausgeführten Cmdlet übereinstimmen, generiert der Agent ein Überwachungsprotokoll.

Der Administratorüberwachungsprotokoll-Agent ist standardmäßig aktiviert. Dies ist erforderlich, damit die Überwachungsprotokollierung funktioniert. Er kann nicht deaktiviert werden, und seine Priorität kann nicht geändert werden. Weitere Informationen zu Cmdlet-Erweiterungs-Agents finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).

