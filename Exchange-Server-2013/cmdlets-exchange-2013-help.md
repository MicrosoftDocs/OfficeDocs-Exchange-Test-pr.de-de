---
title: 'Cmdlets: Exchange 2013 Help'
TOCTitle: Cmdlets
ms:assetid: 1d741dea-1eb8-4909-850f-63d4efaa1a32
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996589(v=EXCHG.150)
ms:contentKeyID: 50475157
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Cmdlets

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Ein *Cmdlet*, gesprochen "Commandlet", ist die kleinste Funktionseinheit der Exchange-Verwaltungsshell. Cmdlets sind mit den Befehlen vergleichbar, die in andere Shells integriert sind, z. B. der `dir`-Befehl, der von `cmd.exe` bereitgestellt wird. Wie diese bekannten Befehle können auch Cmdlets direkt über die Befehlszeile der Shell aufgerufen werden. Hier werden sie im Kontext der Shell und nicht als separater Prozess ausgeführt.


> [!NOTE]
> Gegenüber Microsoft&nbsp;Exchange Server&nbsp;2007 haben sich Änderungen an der internen Verwendung von Cmdlets durch Exchange 2013 ergeben, da die Remotingfunktionalität von Windows&nbsp;PowerShell verwendet wird. Diese Änderungen haben keine oder nur geringe Auswirkungen auf Ihre Verwendung von Cmdlets. Sie ermöglichen Ihnen jedoch zusätzliche Flexibilität bei der Verwaltung Ihrer Exchange-Server.



Cmdlets werden normalerweise für sich wiederholende Verwaltungsaufgaben entwickelt, und die Shell umfasst mehrere Hundert Cmdlets für Exchange-spezifische Verwaltungsaufgaben. Diese Cmdlets stehen zusätzlich zu den nicht aus dem Exchange-System stammenden Cmdlets zur Verfügung, die Bestandteil des grundlegenden Windows PowerShell-Designs sind. Weitere Informationen zum Öffnen der Exchange-Verwaltungsshell finden Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

Alle Cmdlets in der Shell werden als Verb-Nomen-Paare dargestellt. Das Verb-Nomen-Paar ist immer durch einen Bindestrich (-) ohne Leerzeichen verbunden, und das Nomen des Cmdlets steht immer im Singular. Die Verben beziehen sich auf die Aktion, die das Cmdlet durchführt. Die Nomen beziehen sich auf das Objekt, für das das Cmdlet die Aktion durchführt. Im Namen des Cmdlets **Get-SystemMessage** ist beispielsweise **Get** das Verb und **SystemMessage** das Nomen. Alle Cmdlets in der Shell, mit denen eine bestimmte Funktion verwaltet wird, weisen das gleiche Nomen auf. Die folgende Tabelle enthält Beispiele für einige in der Shell verfügbare Verben.


> [!NOTE]
> Ist kein Verb angegeben, wird in der Shell standardmäßig <STRONG>Get</STRONG> als Verb angenommen. So erhalten Sie mit dem Aufruf von <STRONG>Mailbox</STRONG> beispielsweise die gleichen Ergebnisse wie mit dem Aufruf von <STRONG>Get-Mailbox</STRONG>.



### Beispiele für Verben in der Exchange-Verwaltungsshell

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verb</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Disable</strong></p></td>
<td><p>Cmdlets mit dem Verb <strong>Disable</strong> legen den Status <code>Enabled</code> des angegebenen Exchange-Objekts auf <code>$False</code> fest. Hiermit wird verhindert, dass das Objekt Daten verarbeitet, obwohl das Objekt dennoch vorhanden ist.</p></td>
</tr>
<tr class="even">
<td><p><strong>Enable</strong></p></td>
<td><p>Cmdlets mit dem Verb <strong>Enable</strong> legen den Status &quot;Enabled&quot; des angegebenen Exchange-Objekts auf <code>$True</code> fest. Hiermit wird das Objekt für die Datenverarbeitung aktiviert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Get</strong></p></td>
<td><p>Cmdlets mit dem Verb <strong>Get</strong> rufen Informationen zu einem bestimmten Exchange-Objekt ab.</p>

> [!NOTE]
> Die meisten Cmdlets des Typs <STRONG>Get</STRONG> geben nur zusammengefasste Informationen zurück, wenn sie ausgeführt werden. Um das Cmdlet <STRONG>Get</STRONG> anzuweisen, bei Befehlsausführung ausführliche Informationen zurückzugeben, leiten Sie den Befehl an das Cmdlet <STRONG>Format-List</STRONG> um. Weitere Informationen zum Befehl <STRONG>Format-List</STRONG> finden Sie unter <A href="working-with-command-output-exchange-2013-help.md">Arbeiten mit Ausgaben von Befehlen</A>. Weitere Informationen zum Pipelining finden Sie unter <A href="https://technet.microsoft.com/de-de/library/aa998260(v=exchg.150)">Pipelining</A>.


</td>
</tr>
<tr class="even">
<td><p><strong>Install</strong></p></td>
<td><p>Mit Cmdlets vom Typ <strong>Install</strong> installieren neue Objekte oder Funktionen auf einem Exchange-Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Move</strong></p></td>
<td><p>Mit Cmdlets vom Typ <strong>Move</strong> verschieben das angegebene Exchange-Objekt von einem Container oder Server zu einem anderen.</p></td>
</tr>
<tr class="even">
<td><p><strong>New</strong></p></td>
<td><p>Mit Cmdlets vom Typ <strong>New</strong> wird ein neues Exchange-Objekt erstellt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Remove</strong></p></td>
<td><p>Mit <strong>Remove</strong>-Cmdlets wird das angegebene Exchange-Objekt gelöscht.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set</strong></p></td>
<td><p>Mit <strong>Set</strong>-Cmdlets werden die Eigenschaften eines vorhandenen Exchange-Objekts geändert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Test</strong></p></td>
<td><p>Cmdlets vom Typ <strong>Test</strong> ermöglichen das Testen von bestimmten Exchange-Komponenten und erzeugen Protokolldateien, die Sie prüfen können.</p></td>
</tr>
<tr class="even">
<td><p><strong>Uninstall</strong></p></td>
<td><p>Mit Cmdlets vom Typ <strong>Uninstall</strong> wird ein Objekt oder eine Funktion von einem Exchange-Server entfernt.</p></td>
</tr>
</tbody>
</table>


Die folgende Liste mit Cmdlets ist ein Beispiel für einen vollständigen Satz Cmdlets. Dieser Satz Cmdlets wird zum Verwalten der Funktionen für DSN-Nachrichten (Benachrichtigungen über den Zustellungsstatus) und Postfachkontingentmeldungen von Exchange 2013 verwendet:

  - **Get-SystemMessage**

  - **New-SystemMessage**

  - **Remove-SystemMessage**

  - **Set-SystemMessage**

