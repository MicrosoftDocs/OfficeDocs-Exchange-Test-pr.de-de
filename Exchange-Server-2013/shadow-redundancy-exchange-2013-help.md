---
title: 'Shadow-Redundanz: Exchange 2013 Help'
TOCTitle: Shadow-Redundanz
ms:assetid: a40dbe61-2a18-48a8-b2e0-4e81a6678d11
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351027(v=EXCHG.150)
ms:contentKeyID: 50476361
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Shadow-Redundanz

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Shadow-Redundanz wurde in Microsoft Exchange Server 2010 eingeführt, um redundante Nachrichtenkopien zu erstellen, bevor die Nachrichten an Postfächer übermittelt werden. In Exchange 2010 verzögert die Shadow-Redundanz die Löschung einer Nachricht aus der Transportdatenbank auf einem Transportserver, bis der nächste Hop im Übermittlungspfad die Übermittlung beendet hat. Wenn beim nächsten Hop ein Fehler auftritt, bevor der Hop dem Transportserver die erfolgreiche Übermittlung bestätigt, übermittelt der Transportserver die Nachricht erneut an diesen nächsten Hop. Exchange 2010-Server verwenden das Verb XSHADOW, um anzukündigen, dass sie die Shadow-Redundanz unterstützen. Wenn ein SMTP-Server die Shadow-Redundanz nicht unterstützt, verzögert Exchange 2010 die Bestätigung basierend auf einem auf dem Empfangsconnector konfigurierten Zeitintervall, um eine redundante Nachrichtenkopie zu erstellen.

Die wichtigste Verbesserung der Shadow-Redundanz in Microsoft Exchange Server 2013 ist, dass der Transportserver jetzt eine redundante Kopie aller empfangenen Nachrichten erstellt, bevor dem sendenden Server der Empfang der Nachricht bestätigt wird. Ob der sendende Server die Shadow-Redundanz unterstützt oder nicht, spielt keine Rolle. So wird sichergestellt, dass von allen Nachrichten in der Exchange 2013-Transportpipeline eine redundante Kopie erstellt wird, während sie übermittelt werden. Wenn Exchange 2013 ermittelt, dass die ursprüngliche Nachricht während der Übertragung verloren gegangen ist, wird die redundante Kopie der Nachricht übermittelt.

**Inhalt**

Komponenten der Shadow-Redundanz

Anforderungen für die Shadow-Redundanz

Die Shadow-Redundanz ist standardmäßig aktiviert

Erstellen von Shadow-Nachrichten

SMTP-Timeouts

Verwalten von Shadow-Nachrichten

Nachrichtenverarbeitung nach einem Ausfall

## Komponenten der Shadow-Redundanz

In der folgenden Tabelle werden die Komponenten der Shadow-Redundanz beschrieben. Die folgenden Begriffe werden in diesem Thema verwendet.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Begriff</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transportserver</p></td>
<td><p>Ein Exchange-Server, der über Nachrichtenwarteschlangen verfügt und für die Weiterleitung von Nachrichten zuständig ist. In Exchange 2013 handelt es sich bei einem Transportserver um einen Postfachserver (den Transportdienst auf dem Postfachserver).</p></td>
</tr>
<tr class="even">
<td><p>Transportdatenbank</p></td>
<td><p>Die Warteschlangendatenbank für Nachrichten auf einem Exchange 2013-Transportserver. Shadow-Warteschlangen und das Sicherheitsnetz werden ebenfalls in der Transportdatenbank gespeichert.</p></td>
</tr>
<tr class="odd">
<td><p>Transportgrenze für Hochverfügbarkeit</p></td>
<td><p>Eine Database Availability Group (DAG) in Umgebungen mit DAGs oder ein Active Directory-Standort in Umgebungen ohne DAGs. Wenn eine Nachricht von einem Transportserver innerhalb der Transportgrenze für Hochverfügbarkeit empfangen wird, versucht Exchange, zwei redundante Kopien der Nachricht auf den Transportservern innerhalb der Grenze beizubehalten. Wenn eine Nachricht die Transportgrenze für Hochverfügbarkeit überschreitet, behält Exchange die redundanten Nachrichtenkopien nicht mehr bei.</p></td>
</tr>
<tr class="even">
<td><p>Primäre Nachricht</p></td>
<td><p>Die Nachricht, die zur Zustellung an die Transportpipeline übermittelt wird.</p></td>
</tr>
<tr class="odd">
<td><p>Shadow-Nachricht</p></td>
<td><p>Die redundante Kopie der Nachricht, die der Shadow-Server beibehält, bis bestätigt wird, dass die primäre Nachricht erfolgreich durch den primären Server verarbeitet wurde.</p></td>
</tr>
<tr class="even">
<td><p>Primärer Server</p></td>
<td><p>Der Transportserver, der zurzeit die primäre Nachricht verarbeitet.</p></td>
</tr>
<tr class="odd">
<td><p>Shadow-Server</p></td>
<td><p>Die Transportserver, der die Shadow-Nachricht für den primären Server enthält. Ein Transportserver kann der primäre Server für einige Nachrichten und gleichzeitig der Shadow-Server für andere Nachrichten sein.</p></td>
</tr>
<tr class="even">
<td><p>Shadow-Warteschlange</p></td>
<td><p>Die Zustellungswarteschlange, in der der Shadow-Server die Shadow-Nachrichten speichert. Bei Nachrichten mit mehreren Empfängern erfordert jeder nächste Hop für die primäre Nachricht eine separate Shadow-Warteschlange.</p></td>
</tr>
<tr class="odd">
<td><p>Löschstatus</p></td>
<td><p>Die für Shadow-Nachrichten auf einem Transportserver gespeicherte Information, die angibt, dass die primäre Nachricht erfolgreich verarbeitet wurde.</p></td>
</tr>
<tr class="even">
<td><p>Löschbenachrichtigung</p></td>
<td><p>Die von einem primären Server an einen Shadow-Server gesendete Antwort, dass eine Shadow-Nachricht gelöscht werden kann.</p></td>
</tr>
<tr class="odd">
<td><p>Sicherheitsnetz</p></td>
<td><p>Die in Exchange 2013 verbesserte Version der Transportdumpsters. Nachrichten, die vom Transportdienst auf einem Postfachserver erfolgreich verarbeitet oder an einen Postfachempfänger übermittelt wurden, werden in das Sicherheitsnetz verschoben. Weitere Informationen finden Sie unter <a href="safety-net-exchange-2013-help.md">Sicherheitsnetz</a>.</p></td>
</tr>
<tr class="even">
<td><p>Shadow-Redundanz-Manager</p></td>
<td><p>Die Transportkomponente, die die Shadow-Redundanz verwaltet.</p></td>
</tr>
<tr class="odd">
<td><p>Taktsignal</p></td>
<td><p>Der Prozess, der es primären und Shadow-Servern ermöglicht, ihre gegenseitige Verfügbarkeit zu überprüfen.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Anforderungen für die Shadow-Redundanz

Für die Shadow-Redundanz sind mehrere Exchange 2013-Postfachserver erforderlich. Bei den Postfachservern kann es sich um eigenständige Server oder um Postfach- und Clientzugriffsserver handeln, die auf dem gleichen Computer installiert sind.

  - Wenn der Postfachserver kein Mitglied einer DAG ist, müssen sich die anderen Postfachserver am lokalen Active Directory-Standort befinden.

  - Wenn der Postfachserver Mitglied einer DAG ist, müssen die anderen Postfachserver zur gleichen DAG gehören. Die anderen Postfachserver, die zur DAG gehören, können sich am lokalen Active Directory-Standort oder an einem Active Directory-Remotestandort befinden. Wenn sich die DAG über mehrere Active Directory-Standorte erstreckt, wird die redundante Kopie der Nachricht bevorzugt an einem Active Directory-Remotestandort erstellt, um die Standortausfallsicherheit zu gewährleisten.

In folgenden Situationen bietet die Shadow-Redundanz keinen Schutz für Nachrichten während der Übermittlung:

  - In Umgebungen mit einem einzelnen Exchange-Server.

  - In DAGs mit unzureichenden Ressourcen

  - Beim gleichzeitigen Ausfall von mindestens zwei Transportservern, die an der Shadow-Redundanz einer Nachricht beteiligt sind.

Zurück zum Seitenanfang

## Die Shadow-Redundanz ist standardmäßig aktiviert

Standardmäßig wird die Shadow-Redundanz über den Parameter *ShadowRedundancyEnabled* des Cmdlets **Set-TransportConfig** in den Transportdiensten auf allen Postfachservern global aktiviert. Standardmäßig gilt: Wenn der Transportdienst auf einem Postfachserver keine redundante Kopie einer Nachricht erstellen kann, wird die Nachricht nicht zurückgewiesen. Sie können Exchange 2013 jedoch so konfigurieren, dass eine Nachricht zurückgewiesen wird, auch wenn keine redundante Nachrichtenkopie erstellt wurde. Verwenden Sie hierfür den Parameter *RejectMessageOnShadowFailure* im Cmdlet **Set-TransportConfig**. Die Nachricht wird mit einem vorübergehenden Fehler zurückgewiesen, der sendende Server kann die Nachricht jedoch erneut übertragen. Der SMTP-Antwortcode lautet `451 4.4.0 Message failed to be made redundant.` Sie sollten Exchange 2013 so konfigurieren, dass Nachrichten, von denen keine redundante Kopie erstellt werden kann, nur dann zurückgewiesen werden, wenn Ihre Organisation über mehrere Exchange 2013-Postfachserver verfügt.

Die folgende Tabelle beschreibt die Parameter, die die Shadow-Redundanz aktivieren.

### Parameter, die die Shadow-Redundanz aktivieren

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ShadowRedundancyEnabled</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p><code>$true</code></p></td>
<td><ul>
<li><p><code>$true</code> aktiviert die Shadow-Redundanz auf allen Transportservern in der Organisation.</p></li>
<li><p><code>$false</code> deaktiviert die Shadow-Redundanz auf allen Transportservern in der Organisation.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><em>RejectMessageOnShadowFailure</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p><code>$false</code></p></td>
<td><ul>
<li><p><code>$false</code>   Wenn keine Shadow-Kopie der Nachricht erstellt werden kann, wird die primäre Nachricht trotzdem von den Transportservern in der Organisation akzeptiert. Diese Nachrichten werden nicht dauerhaft redundant beibehalten, während sie übermittelt werden.</p></li>
<li><p><code>$true</code>   Nachrichten werden von keinem Transportserver in der Organisation akzeptiert oder bestätigt, bis eine Shadow-Kopie der Nachricht erstellt wurde. Wenn keine Shadow-Kopie der Nachricht erstellt werden kann, wird die primäre Nachricht mit einem vorübergehenden Fehler zurückgewiesen. Alle Nachrichten in der Organisation werden dauerhaft redundant beibehalten, während sie übermittelt werden.</p>
<p>Sie sollten diesen Wert nur auf <code>$true</code> festlegen, wenn Sie über mehrere Exchange 2013-Postfachserver in einer DAG oder an einem Active Directory-Standort verfügen, in der bzw. an dem eine Shadow-Kopie der Nachricht erstellt werden kann.</p></li>
</ul>
<p>Dieser Parameter ist nur von Bedeutung, wenn der Parameter <em>ShadowRedundancyEnabled</em> auf <code>$true</code> festgelegt ist.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Erstellen von Shadow-Nachrichten

Das Hauptziel der Shadow-Redundanz besteht darin, immer über zwei Kopien einer Nachricht innerhalb einer Transportgrenze für Hochverfügbarkeit zu verfügen, während die Nachricht übermittelt wird. Wo und wann die redundante Nachrichtenkopie erstellt wird, richtet sich danach, von wo die Nachricht empfangen wurde und wohin die Nachricht gesendet wird. Hierbei gelten drei wichtige bestimmende Faktoren:

  - Nachrichten, die von Absendern außerhalb einer Transportgrenze für Hochverfügbarkeit empfangen werden.

  - Nachrichten, die an Empfänger außerhalb einer Transportgrenze für Hochverfügbarkeit gesendet werden.

  - Nachrichten, die vom Dienst für die Postfachtransportübermittlung von einem Postfachserver innerhalb der Transportgrenze für Hochverfügbarkeit empfangen werden.

Bei einer *Transportgrenze für Hochverfügbarkeit* kann es sich um Folgendes handeln:

  - Eine DAG für Postfachserver, die Mitglieder einer DAG sind. Hierzu gehören auch DAGs, die sich über mehrere Active Directory-Standorte erstrecken.

  - Ein Active Directory-Standort für Postfachserver, die zu keiner DAG gehören.

Die Shadow-Redundanz verfolgt nie Shadow-Nachrichten über eine Transportgrenze für Hochverfügbarkeit hinweg. Wenn eine Nachricht die Transportgrenze für Hochverfügbarkeit überschreit, beginnt die Shadow-Redundanz oder wird neu gestartet. Dadurch wird der Datenverkehr durch Shadow-Nachrichten reduziert und verhindert, dass Shadow-Nachrichten über die Transportgrenze für Hochverfügbarkeit hinweg erneut gesendet werden. Exchange 2010-Hub-Transport-Server sind ein Sonderfall und werden weiter unten in diesem Thema erläutert.

## Nachrichten, die von Absendern außerhalb einer Transportgrenze für Hochverfügbarkeit empfangen werden

Wenn der Transportdienst auf einem Exchange 2013-Postfachserver eine Nachricht von einem Absender außerhalb der Transportgrenze für Hochverfügbarkeit empfängt, spielt es für den Postfachserver keine Rolle, ob der sendende Server die Shadow-Redundanz unterstützt oder nicht. Solange die Shadow-Redundanz aktiviert ist, erstellt der Postfachserver, der die Nachricht empfängt, eine redundante Kopie der Nachricht auf einem anderen Postfachserver innerhalb der Transportgrenze für Hochverfügbarkeit, und bestätigt danach dem sendenden Server den Empfang der Nachricht. Hier finden Sie ein Beispiel für die Funktionsweise des Verfahrens:

![Erzeugen von Shadow-Nachrichten](images/Dd351027.a97d383b-6ae4-458d-af3a-1ac0a41cd52b(EXCHG.150).gif "Erzeugen von Shadow-Nachrichten")

1.  Ein SMTP-Server überträgt eine Nachricht an den Transportdienst auf einem Postfachserver. Der Postfach ist der primäre Server, und die Nachricht ist die primäre Nachricht.

2.  Während die ursprüngliche SMTP-Sitzung mit dem SMTP-Server noch aktiv ist, öffnet der Transportdienst auf dem primären Server eine neue, gleichzeitige SMTP-Sitzung mit dem Transportdienst auf einem anderen Postfachserver in der Organisation, um eine redundante Kopie der Nachricht zu erstellen.
    
      - Wenn der primäre Server Mitglied einer DAG ist, stellt der primäre Server eine Verbindung zu einem anderen Postfachserver in der gleichen DAG her. Wenn die DAG sich über mehrere Active Directory-Standorte erstreckt, wird standardmäßig ein Postfachserver an einem anderen Active Directory-Standort bevorzugt. Diese Einstellung wird über den Parameter *ShadowMessagePreference* im Cmdlet **Set-TransportService** gesteuert. Der Standardwert lautet `PreferRemote`, Sie können diesen jedoch zu `RemoteOnly` oder `LocalOnly` ändern.
    
      - Wenn der primäre Server kein Mitglied einer DAG ist, stellt der primäre Server eine Verbindung zu einem anderen Postfachserver am gleichen Active Directory-Standort fest, unabhängig vom Wert des Parameters *ShadowMessagePreference*.

3.  Der primäre Server überträgt eine Kopie der Nachricht an den Transportdienst auf einem anderen Postfachserver, und dieser Transportdienst bestätigt die erfolgreiche Erstellung der Nachrichtenkopie. Die Kopie der Nachricht ist die Shadow-Kopie, und der Postfachserver, auf dem die Kopie gespeichert ist, ist der Shadow-Server für den primären Server. Die Nachricht befindet sich in einer Shadow-Warteschlange auf dem Shadow-Server.

4.  Nachdem der primäre Server die Bestätigung vom Shadow-Server erhalten hat, bestätigt der primäre Server dem ursprünglichen SMTP-Server in der ursprünglichen SMTP-Sitzung den Empfang der primären Nachricht, und die SMTP-Sitzung wird geschlossen.

## Nachrichten, die an Empfänger außerhalb einer Transportgrenze für Hochverfügbarkeit gesendet werden

Wenn ein Exchange 2013-Transportserver eine Nachricht an einen Empfänger außerhalb der Transportgrenze für Hochverfügbarkeit überträgt und der SMTP-Server auf der anderen Seite den Empfang der Nachricht bestätigt, verschiebt der Transportserver die Nachricht in das Sicherheitsnetz. Die Nachricht kann aus dem Sicherheitsnetz nicht erneut übermittelt werden, nachdem die primäre Nachricht erfolgreich über die Transportgrenze für Hochverfügbarkeit hinweg übertragen wurde. Weitere Informationen zum Sicherheitsnetz finden Sie unter [Sicherheitsnetz](safety-net-exchange-2013-help.md).

## Nachrichten, die innerhalb einer Transportgrenze für Hochverfügbarkeit übertragen werden

Das Nachrichtenrouting wurde in Exchange 2013 optimiert: Wenn es sich beim endgültigen Ziel um eine DAG oder einen Active Directory-Standort handelt, sind im Allgemeinen nicht mehrere Hops zwischen dem Transportdienst auf den Postfachservern in dieser DAG oder an diesem Active Directory-Standort erforderlich. Sobald die Nachricht vom Transportdienst auf einem Postfachserver in der DAG oder am Active Directory-Standort akzeptiert wurde, in der bzw. dem sich das endgültige Ziel für die Nachricht befindet, ist der nächste Hop für die Nachricht normalerweise das Ziel selbst. Das Ziel der Shadow-Redundanz, während der Übermittlung zwei Kopien einer Nachricht beizubehalten, ist erfüllt, wenn sich eine Shadow-Kopie der Nachricht an einer beliebigen Stelle innerhalb der DAG oder des Active Directory-Standorts befindet. Üblicherweise erfordern nur Failoverszenarien in einer DAG, in denen das Cmdlet **Redirect-Message** die aktiven Warteschlangen auf einem Postfachserver verkleinern muss, mehrere Hops innerhalb einer Transportgrenze für Hochverfügbarkeit.

## Shadow-Redundanz mit Exchange 2010-Hub-Transport-Servern am gleichen Active Directory-Standort

Wenn ein Exchange 2010-Hub-Transport-Server eine Nachricht an einen Exchange 2013-Postfachserver am gleichen Active Directory-Standort überträgt, kündigt der Exchange 2010-Hub-Transport-Server über den XSHADOW-Befehl Unterstützung für die Shadow-Redundanz an, der Postfachserver kündigt jedoch keine Unterstützung für die Shadow-Redundanz an. Dies verhindert, dass der Exchange 2010-Hub-Transport-Server eine Shadow-Kopie der Nachricht auf einem Exchange 2013-Postfachserver erstellt.

Wenn der Transportdienst auf einem Exchange 2013-Postfachserver eine Nachricht an einen Exchange 2010-Hub-Transport-Server am gleichen Active Directory-Standort überträgt, erstellt der Exchange 2013-Postfachserver eine Shadow-Kopie der Nachricht für den Exchange 2010-Hub-Transport-Server. Nachdem der Exchange 2013-Postfachserver die Bestätigung vom Exchange 2010-Hub-Transport-Server über den Empfang der Nachricht erhalten hat, verschiebt der Exchange 2013-Postfachserver die erfolgreich verarbeitete Nachricht in das Sicherheitsnetz. Die erfolgreich verarbeiteten Nachrichten, die vom Exchange 2013-Postfachserver im Sicherheitsnetz gespeichert werden, werden jedoch niemals erneut an die Exchange 2010-Hub-Transport-Server übertragen.

Zurück zum Seitenanfang

## SMTP-Timeouts

Während des Versuchs, die redundante Kopie einer Nachricht zu erstellen, könnte in der SMTP-Verbindung zwischen dem sendenden SMTP-Server und dem primären Server oder in der SMTP-Sitzung zwischen dem primären Server und dem Shadow-Server ein Timeout auftreten. Sowohl Empfangs- als auch Sendeconnectors verfügen über einen *ConnectionInactivityTimeOut*-Parameter für die tatsächlichen Übertragungszeiträume für Daten auf dem Connector. Empfangsconnectors verfügen auch über einen absoluten *ConnectionTimeOut*-Parameter.

Wenn in einer der SMTP-Sitzungen ein Timeout auftritt, bevor die Shadow-Kopie der Nachricht erstellt und bestätigt wurde, wird das Ergebnis über den Parameter *RejectMessageOnShadowFailure* im Cmdlet **Set-TransportConfig** gesteuert. Standardmäßig lautet der Wert dieses Parameters `$false`, d. h. die primäre Nachricht wird akzeptiert, ohne dass eine Shadow-Kopie erstellt wird. Wenn der Wert dieses Parameters `$true` lautet, wird die primäre Nachricht mit dem vorübergehenden Fehler `451 4.4.0` zurückgewiesen.

Wenn die Shadow-Kopie einer Nachricht erfolgreich erstellt wurde, aber ein Timeout in der SMTP-Sitzung zwischen dem sendenden SMTP-Server und dem primären Server auftritt, akzeptiert und verarbeitet der primäre Server die primäre Nachricht. Der sendende SMTP-Server übermittelt die unbestätigte Nachricht erneut, die Funktion der Erkennung von Nachrichtenduplikaten verhindert jedoch, dass Exchange-Postfachbenutzern die Nachricht doppelt angezeigt wird. Wenn der sendende SMTP-Server die Nachricht erneut übermittelt, erstellt der primäre Server eine weitere Shadow-Kopie der Nachricht. Es besteht keine Beziehung zwischen den Shadow-Nachrichten, die erstellt werden, wenn der sendende SMTP-Server Nachrichten erneut überträgt.

In der folgenden Tabelle werden die Parameter beschrieben, die die Erstellung von Shadow-Nachrichten steuern

### Parameter für die Erstellung von Shadow-Nachrichten

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ShadowMessagePreferenceSetting</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p><code>PreferRemote</code></p></td>
<td><ul>
<li><p><code>PreferRemote</code>   Versucht, eine Shadow-Kopie der Nachricht auf einem Postfachserver an einem anderen Active Directory-Standort zu erstellen. Wenn dieser Vorgang fehlschlägt, wird versucht, eine Shadow-Kopie der Nachricht auf einem Server am lokalen Active Directory-Standort zu erstellen.</p></li>
<li><p><code>LocalOnly</code>   Eine Shadow-Kopie der Nachricht sollte nur auf einem Transportserver am lokalen Active Directory-Standort erstellt werden.</p></li>
<li><p><code>RemoteOnly</code>   Eine Shadow-Kopie der Nachricht sollte nur auf einem Transportserver an einem anderen lokalen Active Directory-Standort erstellt werden.</p></li>
</ul>
<p>Dieser Parameter ist nur von Bedeutung, wenn es sich bei dem primären Server, der versucht, eine Shadow-Kopie der Nachricht zu erstellen, um einen Postfachserver handelt, der Mitglied einer sich über mehrere Active Directory-Standorte erstreckenden DAG ist.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxRetriesForRemoteSiteShadow</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>4</p></td>
<td><p>Dieser Parameter wird verwendet, wenn der Postfachserver Mitglied einer sich über mehrere Active Directory-Standorte erstreckenden DAG ist.</p>
<ul>
<li><p>Wenn der Parameter <em>ShadowMessagePreferenceSetting</em> auf <code>PreferRemote</code> festgelegt ist, versucht der Postfachserver zuerst so oft, wie in <em>MaxRetriesForRemoteSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver an einem Active Directory-Remotestandort zu erstellen. Wenn dies nicht funktioniert, versucht der Postfachserver so oft, wie in <em>MaxRetriesForLocalSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver am lokalen Active Directory-Standort zu erstellen.</p></li>
<li><p>Wenn der Parameter <em>ShadowMessagePreferenceSetting</em> auf <code>RemoteOnly</code> festgelegt ist, versucht der Postfachserver so oft, wie in <em>MaxRetriesForRemoteSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem Postfachserver an einem Active Directory-Remotestandort zu erstellen.</p></li>
<li><p>Der</p></li>
</ul>
<p>Wenn eine Shadow-Kopie der Nachricht nicht erfolgreich erstellt werden kann, gilt Folgendes:</p>
<ul>
<li><p>Wenn <em>RejectMessageOnShadowFailure</em> auf <code>$true</code> festgelegt ist, wird die primäre Nachricht mit einem vorübergehenden Fehler zurückgewiesen.</p></li>
<li><p>Wenn <em>RejectMessageOnShadowFailure</em> auf <code>$false</code> festgelegt ist, wird die primäre Nachricht akzeptiert, aber nicht dauerhaft gespeichert.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><em>MaxRetriesForLocalSiteShadow</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>2</p></td>
<td><p>Dieser Parameter wird unter folgenden Umständen verwendet:</p>
<ul>
<li><p>Wenn der Postfachserver Mitglied einer sich über mehrere Active Directory-Standorte erstreckenden DAG ist.</p>
<ol>
<li><p>Wenn der Parameter <em>ShadowMessagePreferenceSetting</em> auf <code>PreferRemote</code> festgelegt ist, versucht der Postfachserver zuerst so oft, wie in <em>MaxRetriesForRemoteSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver an einem Active Directory-Remotestandort zu erstellen. Wenn dies nicht funktioniert, versucht der Postfachserver so oft, wie in <em>MaxRetriesForLocalSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver am lokalen Active Directory-Standort zu erstellen.</p></li>
<li><p>Wenn der Parameter <em>ShadowMessagePreferenceSetting</em> auf <code>LocalOnly</code> festgelegt ist, versucht der Postfachserver so oft, wie in <em>MaxRetriesForLocalSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver am lokalen Active Directory-Standort zu erstellen.</p></li>
</ol></li>
<li><p>Wenn der Postfachserver kein Mitglied einer DAG oder Mitglied einer DAG ist, die sich an einem einzigen Active Directory-Standort befindet, versucht der Postfachserver so oft, wie in <em>MaxRetriesForLocalSiteShadow</em> angegeben, eine Shadow-Kopie der Nachricht auf einem anderen Postfachserver am lokalen Active Directory-Standort zu erstellen.</p></li>
</ul>
<p>Wenn eine Shadow-Kopie der Nachricht nicht erfolgreich erstellt werden kann, gilt Folgendes:</p>
<ul>
<li><p>Wenn <em>RejectMessageOnShadowFailure</em> auf <code>$true</code> festgelegt ist, wird die primäre Nachricht mit einem vorübergehenden Fehler zurückgewiesen.</p></li>
<li><p>Wenn <em>RejectMessageOnShadowFailure</em> auf <code>$false</code> festgelegt ist, wird die primäre Nachricht akzeptiert, aber nicht dauerhaft gespeichert.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><em>ConnectionInactivityTimeout</em> für <strong>Set-ReceiveConnector</strong></p></td>
<td><p>5 Minuten im Transportdienst auf Postfachservern</p>
<p>5 Minuten im Front-End-Transport-Dienst auf Clientzugriffsservern.</p>
<p>1 Minute auf Edge-Transport-Servern.</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine geöffnete SMTP-Verbindung zu einem Quellmessagingserver im Leerlauf bleiben kann, bis die Verbindung geschlossen wird. Der Wert dieses Parameters muss kleiner sein als der durch den Parameter <em>ConnectionTimeout</em> angegebene Wert.</p></td>
</tr>
<tr class="odd">
<td><p><em>ConnectionTimeout</em> für <strong>Set-ReceiveConnector</strong></p></td>
<td><p>10 Minuten im Transportdienst auf Postfachservern</p>
<p>10 Minuten im Front-End-Transport-Dienst auf Clientzugriffsservern.</p>
<p>5 Minuten auf Edge-Transport-Servern.</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine SMTP-Verbindung zu einem Quellmessagingserver geöffnet bleiben kann, und zwar auch dann, wenn der Messagingserver Daten überträgt. Der Wert dieses Parameters muss größer sein als der durch den Parameter <em>ConnectionInactivityTimeout</em> angegebene Wert.</p></td>
</tr>
<tr class="even">
<td><p><em>ConnectionInactivityTimeOut</em> für <strong>Set-SendConnector</strong></p></td>
<td><p>10 Minuten</p></td>
<td><p>Mit diesem Parameter wird die maximale Zeit angegeben, für die eine geöffnete SMTP-Verbindung zu einem Zielmessagingserver im Leerlauf bleiben kann, bis die Verbindung geschlossen wird.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Verwalten von Shadow-Nachrichten

Nachdem eine Shadow-Nachricht erstellt wurde, müssen verschiedene weitere Aufgaben ausgeführt werden. Der primäre Server und der Shadow-Server müssen in Kontakt bleiben, um den Fortschritt der Nachricht nachzuverfolgen.

Wenn der primäre Server die Nachricht erfolgreich an den nächsten Hop übertragen hat und dieser Hop den Empfang der Nachricht bestätigt hat, aktualisiert der primäre Server den *Löschstatus* der Nachricht in "Übertragung abgeschlossen". Beim Löschstatus handelt es sich im Grunde um eine Nachricht, die eine Liste von Nachrichten enthält, die überwacht werden. Eine erfolgreich übermittelte Nachricht muss nicht in der Shadow-Warteschlange verbleiben. Sobald der Shadow-Server also die Bestätigung erhalten hat, dass der primäre Server die Nachricht erfolgreich an den nächsten Hop übertragen hat, verschiebt der Shadow-Server die Shadow-Nachricht aus der Shadow-Warteschlange in das Sicherheitsnetz.

Der Shadow-Server ermittelt den Löschstatus der Shadow-Nachrichten in den Shadow-Warteschlangen, indem der primäre Server abgefragt wird. Wenn der Shadow-Server eine SMTP-Sitzung mit dem primären Server öffnet, beispielsweise zur Übertragung sonstiger nicht zugeordneter Nachrichten, führt der Shadow-Server den Befehl **XQDISCARD** aus, um den Löschstatus der primären Nachrichten zu ermitteln. Wenn der Shadow-Server innerhalb eines konfigurierten Zeitintervalls keine SMTP-Sitzung mit dem primären Server geöffnet hat, öffnet der Shadow-Server eine SMTP-Sitzung mit dem primären Server und führt den **XQDISCARD**-Befehl aus. Das Zeitintervall wird über den Parameter *ShadowHeartbeatFrequentcy* im Cmdlet **Set-TransportConfig** gesteuert. Der Standardwert beträgt 2 Minuten. Nachdem der Shadow-Server eine SMTP-Sitzung mit dem primären Server geöffnet hat, antwortet der primäre Server mit den *Löschbenachrichtigungen* für Nachrichten, die für den abfragenden Shadow-Server relevant sind. In Exchange 2013 werden Löschbenachrichtigungen nicht im Arbeitsspeicher, sondern auf einem Datenträger gespeichert. Aus diesem Grund bleiben die Löschbenachrichtigungen nach einem Neustart des Microsoft Exchange-Transportdiensts erhalten. Nach dem Start des Diensts stehen die Informationen zu erfolgreich verarbeiteten Nachrichten sowohl dem primären Server als auch dem Shadow-Server weiterhin zur Verfügung.

Die SMTP-Kommunikation zwischen dem Shadow-Server und dem primären Server wird als *Takt* eingesetzt, der die Verfügbarkeit der Server bestimmt. Wenn der Shadow-Server nach einem konfigurierten Zeitintervall keine SMTP-Sitzung mit dem primären Server öffnen kann oder wenn die Transportdatenbank des primären Servers eine andere Datenbank-ID aufweist, stuft sich der Shadow-Server selbst zum primären Server herauf, stuft die Shadow-Nachrichten zu primären Nachrichten herauf und überträgt die Nachrichten an den nächsten Hop. Das Zeitintervall wird über den Parameter *ShadowResubmitTimeSpan* im Cmdlet **Set-TransportConfig** gesteuert. Der Standardwert ist 3 Stunden.

Der *Shadow-Redundanz-Manager* ist die Kernkomponente eines Exchange 2013-Transportservers, der für die Verwaltung der Shadow-Redundanz sorgt. Der Shadow-Redundanz-Manager verwaltet die folgenden Informationen für alle primären Nachrichten, die ein Server aktuell verarbeitet:

  - Informationen zum Shadow-Server für jede primäre Nachricht, die verarbeitet wird.

  - Löschstatus, der an die Shadow-Server gesendet wird.

Der Shadow-Redundanz-Manager übernimmt für alle Shadow-Nachrichten, die ein Shadow-Server in seiner Shadow-Warteschlange verwaltet, die folgenden Aufgaben:

  - Verwalten der Liste primärer Server für jede Shadow-Nachricht.

  - Vergleichen der ursprünglichen Datenbank-ID mit der aktuellen Datenbank-ID für die Warteschlangendatenbank, in der primäre Kopie der Nachricht gespeichert ist.

  - Überprüfen der Verfügbarkeit aller primären Server, für die sich eine Shadow-Nachricht in der Warteschlange befindet.

  - Verarbeiten von Löschbenachrichtigungen von primären Servern.

  - Entfernen der Shadow-Nachrichten aus den Shadow-Warteschlangen, nachdem alle erwarteten Löschbenachrichtigungen empfangen wurden.

  - Entscheidung darüber, ob der Shadow-Server den Besitz von Shadow-Nachrichten übernimmt und zu einem primären Server wird.

  - Nachverfolgen von Nachrichtenverzweigungen und sonstigen Nachrichten, wie z. B. Benachrichtigungen über den Zustellungsstatus (Delivery Status Notification, DSN) und Journalberichten, um sicherzustellen, dass die redundante Nachrichtenkopie erst freigegeben wird, wenn alle Kopien der Nachricht vollständig verarbeitet wurden.

In der folgenden Tabelle werden die Parameter beschrieben, die die Beibehaltung von Shadow-Nachrichten steuern.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ShadowHeartbeatFrequency</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>2 Minuten</p></td>
<td><p>Die maximale Zeitspanne, die ein Shadow-Server wartet, bevor er eine SMTP-Verbindung mit dem primären Server herstellt, um den Löschstatus von Nachrichten zu überprüfen.</p></td>
</tr>
<tr class="even">
<td><p><em>ShadowResubmitTimeSpan</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>3 Stunden</p></td>
<td><p>Gibt an, wie lange ein Server wartet, bevor er entscheidet, dass beim primären Server ein Fehler aufgetreten ist, und den Besitz für die Shadow-Nachrichten in der Shadow-Warteschlange des nicht erreichbaren primären Servers übernimmt.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShadowMessageAutoDiscardInterval</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>2 Tage</p></td>
<td><p>Gibt an, wie lange ein Server Löschereignisse für erfolgreich übermittelte Nachrichten beibehält. Ein primärer Server stellt Löschereignisse so lange in Warteschlangen, bis er vom Shadow-Server abgefragt wird. Wenn der Shadow-Server den primären Server jedoch nicht während des in diesem Parameter festgelegten Zeitraums abfragt, löscht der primäre Server die Löschereignisse in der Warteschlange.</p></td>
</tr>
<tr class="even">
<td><p><em>SafetyNetHoldTime</em> für <strong>Set-TransportConfig</strong></p></td>
<td><p>2 Tage</p></td>
<td><p>Gibt an, wie lange erfolgreich verarbeitete Nachrichten im Sicherheitsnetz aufbewahrt werden. Unbestätigte Shadow-Nachrichten werden nach Ablauf der Summe von <em>SafetyNetHoldTime</em> und <em>MessageExpirationTimeout</em> für <strong>Set-TransportService</strong> aus dem Sicherheitsnetz gelöscht.</p></td>
</tr>
<tr class="odd">
<td><p><em>MessageExpirationTimeout</em> für <strong>Set-TransportService</strong></p></td>
<td><p>2 Tage</p></td>
<td><p>Gibt an, wie lange eine Nachricht in einer Warteschlange verbleiben kann, bevor sie abläuft.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Nachrichtenverarbeitung nach einem Ausfall

Die Shadow-Redundanz minimiert den Nachrichtenverlust aufgrund von Serverausfällen. Wenn ein Transportserver nach einem Ausfall wieder online geschaltet wird, gibt es zwei Szenarien:

  - **Der Server wird mit einer neuen Transportdatenbank online geschaltet**   In diesem Szenario kann die Transportdatenbank aufgrund von Datenbeschädigung oder eines Hardwarefehlers nicht wiederhergestellt werden. Da der Transportserver in diesem Fall über eine neue Datenbank-ID verfügt, wird er von den anderen Transportservern in der Organisation als neue Route erkannt. Dies gilt auch für Situationen, in denen ein Server nicht wiederhergestellt werden kann und als Ersatz ein neuer Server bereitgestellt wird.

  - **Der Server wird mit derselben Transportdatenbank online geschaltet**   In diesem Szenario ist der betreffende Transportserver nicht ausgefallen, sondern war so lange offline, dass der Shadow-Server den Besitz für die Nachrichten übernommen und diese erneut übermittelt hat. Dieses Szenario kann beispielsweise durch einen Netzwerkkartenfehler oder eine längere Wartung des Servers verursacht werden.

In der folgenden Tabelle wird zusammengefasst, wie die Shadow-Redundanz in diesen beiden Szenarien reagiert. Es wird hierbei angenommen, dass es sich bei dem ausgefallenen Server um den Server "Mailbox01" handelt.

### Nachrichtenverarbeitung in Wiederherstellungsszenarien

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Szenario für die Wiederherstellung</th>
<th>Durchgeführte Aktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mailbox01 wird mit einer neuen Datenbank wieder online geschaltet.</p></td>
<td><p>Wenn Mailbox01 nicht mehr verfügbar ist, übernimmt jeder Server, der Shadow-Nachrichten für Mailbox01 in die Warteschlange eingereiht hat, den Besitz für diese Nachrichten und übermittelt die Nachrichten erneut. Die Nachrichten werden an ihre Ziele übermittelt.</p>
<p>Die maximale Verzögerung für Nachrichten entspricht dem Wert des Parameters <em>ShadowHeartbeatFrequency</em> im Cmdlet <strong>Set-TransportConfig</strong>. Der Standardwert beträgt 2 Minuten.</p></td>
</tr>
<tr class="even">
<td><p>Mailbox01 wird mit derselben Datenbank wieder online geschaltet.</p></td>
<td><p>Nachdem Mailbox01 wieder online geschaltet wurde, übermittelt der Server die Nachrichten in seiner Warteschlange, die bereits von denjenigen Servern übermittelt wurden, auf denen Shadow-Kopien der Nachrichten für Mailbox01 gespeichert sind. Dies führt zur doppelten Zustellung dieser Nachrichten. Exchange-Postfachbenutzer erhalten aufgrund der Funktion zur Erkennung von Nachrichtenduplikaten keine doppelten Nachrichten. Empfänger in anderen Messagingsystemen als Exchange erhalten jedoch möglicherweise Duplikate ihrer Nachrichten.</p>
<p>Die maximale Verzögerung für Nachrichten entspricht dem Wert des Parameters <em>ShadowResubmitTimeSpan</em> im Cmdlet <strong>Set-TransportConfig</strong>. Der Standardwert ist 3 Stunden.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

