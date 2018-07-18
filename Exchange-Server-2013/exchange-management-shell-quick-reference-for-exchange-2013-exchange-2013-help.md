---
title: 'Kurzübersicht über die Exchange-Verwaltungsshell für Exchange 2013: Exchange 2013 Help'
TOCTitle: Kurzübersicht über die Exchange-Verwaltungsshell für Exchange 2013
ms:assetid: 3ea4a105-a93c-48ba-96ce-6170125354e1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ619302(v=EXCHG.150)
ms:contentKeyID: 50475456
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Kurzübersicht über die Exchange-Verwaltungsshell für Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In diesem Thema werden die am häufigsten verwendeten Cmdlets beschrieben, die in der RTM-Version (Release to Manufacturing) und höheren Versionen von Microsoft Exchange Server 2013 verfügbar sind, und es werden Beispiele zu deren Verwendung bereitgestellt.


> [!NOTE]
> Weitere Inhalte zu anderen Bereichen von Exchange 2013 werden in Kürze zur Verfügung gestellt.



Weitere Informationen zur Exchange-Verwaltungsshell in Exchange 2013 und allen verfügbaren Cmdlets finden Sie unter den folgenden Themen:

  - [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\))

  - [Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\))

## Was möchten Sie erfahren?

## Allgemeine Cmdlet-Aktionen

Die folgenden Verben werden von den meisten Cmdlets unterstützt und sind einer bestimmten Aktion zugeordnet.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>New</p></td>
<td><p>Mit dem Verb New wird eine Instanz eines Elements erstellt, z. B. eine neue Konfigurationseinstellung, eine neue Datenbank oder ein neuer SMTP-Connector.</p></td>
</tr>
<tr class="even">
<td><p>Remove</p></td>
<td><p>Mit dem Verb Remove wird eine Instanz eines Elements entfernt, z. B. ein Postfach oder eine Transportregel.</p>
<p>Alle Cmdlets vom Typ Remove unterstützen den Parameter <em>WhatIf</em> und den Parameter <em>Confirm</em>. Weitere Informationen zu diesen Parametern finden Sie unter Important Parameters.</p></td>
</tr>
<tr class="odd">
<td><p>Enable</p></td>
<td><p>Mit dem Verb Enable wird eine Einstellung aktiviert oder ein Empfänger E-Mail-aktiviert.</p></td>
</tr>
<tr class="even">
<td><p>Disable</p></td>
<td><p>Mit dem Verb Disable wird eine Einstellung deaktiviert oder ein Empfänger E-Mail-deaktiviert.</p>
<p>Alle Tasks vom Typ Disable unterstützen den Parameter <em>WhatIf</em> und den Parameter <em>Confirm</em>. Weitere Informationen zu diesen Parametern finden Sie unter Important Parameters.</p></td>
</tr>
<tr class="odd">
<td><p>Set</p></td>
<td><p>Mit dem Verb Set werden bestimmte Einstellungen eines Objekts bearbeitet, z. B. der Alias eines Kontakts oder die Aufbewahrungszeit für gelöschte Elemente einer Postfachdatenbank.</p></td>
</tr>
<tr class="even">
<td><p>Get</p></td>
<td><p>Mit dem Verb Get wird die Abfrage eines bestimmten Objekts oder einer Teilmenge eines Objekttyps ausgeführt, z. B. eines bestimmten Postfachs, aller Postfachbenutzer oder von Postfachbenutzern in einer Domäne.</p></td>
</tr>
</tbody>
</table>


## Wichtige Parameter

Die folgenden Parameter unterstützen Sie bei der Steuerung der Befehlsausführung und liefern genaue Angaben über die Auswirkungen eines Befehls, bevor Daten geändert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Identity</p></td>
<td><p>Der Parameter <em>Identity</em> identifiziert das eindeutige Objekt für den Task. Er wird in der Regel mit den Cmdlets Enable, Disable, Remove, Set und Get verwendet. <em>Identity</em> ist auch ein Positionsparameter, d. h., <em>Identity</em> muss nicht angegeben werden, wenn Sie den Wert des Parameters in der Befehlszeile angeben.</p>
<p>Beispielsweise führt <em>Get-Mailbox -Identity user1</em> eine Abfrage des Postfachs von <em>user1</em> aus. <em>Get-Mailbox user1</em> entspricht <em>Get-Mailbox -Identity user1</em>.</p></td>
</tr>
<tr class="even">
<td><p>WhatIf</p></td>
<td><p>Der Parameter <em>WhatIf</em> weist das Cmdlet an, die für das Objekt auszuführenden Aktionen lediglich zu simulieren. Durch Verwendung des Parameters <em>WhatIf</em> können Sie die sich ergebenden Änderungen anzeigen, ohne diese Änderungen tatsächlich anzuwenden. Der Standardwert lautet <em>$true</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Confirm</p></td>
<td><p>Der Parameter <em>Confirm</em> führt dazu, dass das Cmdlet die Verarbeitung unterbricht und vom Administrator die Bestätigung der Cmdlet-Aktion anfordert, bevor die Verarbeitung fortgesetzt wird. Der Standardwert lautet <em>$true</em>.</p></td>
</tr>
<tr class="even">
<td><p>Validate</p></td>
<td><p>Der Parameter <em>Validate</em> führt dazu, dass das Cmdlet überprüft, ob alle Voraussetzungen zur Ausführung des Vorgangs erfüllt sind und der Vorgang erfolgreich abgeschlossen wird.</p></td>
</tr>
</tbody>
</table>


## Tipps und Tricks

Die folgenden Befehle sind verschiedenen Tasks zugeordnet, die Sie beim Verwalten von Exchange 2013 nutzen können.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Get-Command</p></td>
<td><p>Dieses Cmdlet ruft alle Tasks ab, die in Exchange 2013 ausgeführt werden können.</p></td>
</tr>
<tr class="even">
<td><p>Get-Command *<em>Schlüsselwort</em>*</p></td>
<td><p>Dieses Cmdlet ruft Tasks ab, bei denen der Cmdlet-Name das <em>Schlüsselwort</em> enthält.</p></td>
</tr>
<tr class="odd">
<td><p>Get-<em>Task</em> | Get-Member</p></td>
<td><p>Dieses Cmdlet ruft alle Eigenschaften und Methoden von <em>Task</em> ab.</p></td>
</tr>
<tr class="even">
<td><p>Get-<em>Task</em> | Format-List</p></td>
<td><p>Dieses Cmdlet zeigt das Ergebnis der Abfrage in einer formatierten Liste an. Sie können die Ausgabe aller Get-Cmdlets an Format-List umleiten, um alle Eigenschaften für das Objekt anzuzeigen, die von diesem Befehl zurückgegeben werden. Alternativ können Sie bestimmte Eigenschaften angeben, die Sie anzeigen möchten. Trennen Sie die einzelnen Eigenschaften hierbei durch ein Komma, wie im folgenden Beispiel gezeigt: <em>Get-Mailbox *john* | Format-List alias,*quota</em></p></td>
</tr>
<tr class="odd">
<td><p>Help <em>Task</em></p></td>
<td><p>Dieses Cmdlet ruft Hilfeinformationen der Exchange-Verwaltungsshell zu jedem Task in Exchange 2013 ab, wie im folgenden Beispiel gezeigt: <em>Help Get-Mailbox</em></p></td>
</tr>
<tr class="even">
<td><p>Get-<em>Task</em> | Format-List &gt; <em>Datei.txt</em></p></td>
<td><p>Dieses Cmdlet exportiert die Ausgabe von <em>Task</em> in eine Textdatei: <em>Datei.txt</em></p></td>
</tr>
</tbody>
</table>


## Berechtigungen


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Get-RoleGroupMember &quot;<em>Organisationsverwaltung</em>&quot;</p></td>
<td><p>Mit diesem Befehl werden die Mitglieder der Verwaltungsrollengruppe <em>Organisationsverwaltung</em> abgerufen.</p></td>
</tr>
<tr class="even">
<td><p>Get-ManagementRoleAssignment -Role &quot;<em>Erstellung von E-Mail-Empfängern</em>&quot; -GetEffectiveUsers</p></td>
<td><p>Mit diesem Befehl wird eine Liste aller Benutzer abgerufen, denen über die Verwaltungsrolle <em>Erstellung von E-Mail-Empfängern</em> Berechtigungen erteilt wurden. Dies schließt Benutzer ein, die Mitglieder von Rollengruppen oder universellen Sicherheitsgruppen (Universal Security Group, USG) sind, denen die Rolle Erstellung von E-Mail-Empfängern zugewiesen ist. Es werden keine Benutzer aufgeführt, die Mitglieder verknüpfter Rollengruppen in einer anderen Gesamtstruktur sind.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -RoleAssignee <em>Administrator</em> | Get-ManagementRole | Get-ManagementRoleEntry</p></td>
<td><p>Mit diesem Befehl wird eine Liste der Cmdlets abgerufen, die der Benutzer <em>Administrator</em> ausführen kann.</p></td>
</tr>
<tr class="even">
<td><p>ForEach ($RoleEntry in Get-ManagementRoleEntry *\<em>Remove-Mailbox</em> -parameters Identity) {Get-ManagementRoleAssignment -Role $RoleEntry.Role -GetEffectiveUsers -Delegating $False | Where-Object {$_.EffectiveUserName -Ne &quot;All Group Members&quot;} | FL Role, EffectiveUserName, AssignmentChain}</p></td>
<td><p>Mit diesem Befehl wird eine Liste aller Benutzer abgerufen, die das Cmdlet <em>Remove-Mailbox</em> ausführen können.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -WritableRecipient <em>kima</em> -GetEffectiveUsers | FT RoleAssigneeName, EffectiveUserName, Role, AssignmentChain</p></td>
<td><p>Mit diesem Befehl wird eine Liste aller Benutzer abgerufen, die das Postfach von <em>kima</em> ändern können.</p></td>
</tr>
<tr class="even">
<td><p>New-ManagementScope &quot;<em>Seattle Users</em>&quot; -RecipientRestrictionFilter { <em>City</em> -Eq &quot;<em>Seattle</em>&quot; }</p>
<p>New-RoleGroup &quot;<em>Seattle Admins</em>&quot; -Roles &quot;<em>E-Mail-Empfänger</em>&quot;, &quot;<em>Erstellung von E-Mail-Empfängern</em>&quot;, &quot;<em>Postfachimport/-export</em>&quot;, -CustomRecipientWriteScope &quot;<em>Seattle Users</em>&quot;</p></td>
<td><p>Mit diesem Befehl werden ein neuer Verwaltungsbereich sowie eine Verwaltungsrollengruppe erstellt, um Mitgliedern der Rollengruppe die Verwaltung von Empfängern in Seattle zu ermöglichen.</p>
<p>Zunächst wird der Verwaltungsbereich <em>Seattle Users</em> erstellt, der nur Empfänger einschließt, für die im Attribut <em>City</em> des zugehörigen Benutzerobjekts der Wert <em>Seattle</em> angegeben ist.</p>
<p>Anschließend wird eine neue Rollengruppe namens <em>Seattle Admins</em> erstellt, der die Rollen <em>E-Mail-Empfänger</em>, <em>Erstellung von E-Mail-Empfängern</em> und <em>Postfachimport/-export</em> zugewiesen werden. Der Bereich der Rollengruppe ist so festgelegt, dass ihre Mitglieder nur Benutzer verwalten können, die dem Empfängerfilterbereich <em>Seattle Users</em> entsprechen.</p></td>
</tr>
<tr class="odd">
<td><p>New-ManagementScope &quot;<em>Vancouver Servers</em>&quot; -ServerRestrictionFilter { <em>ServerSite</em> -Eq &quot;<em>Vancouver</em>&quot; }</p>
<p>$RoleGroup = Get-RoleGroup &quot;<em>Serververwaltung</em>&quot;</p>
<p>New-RoleGroup &quot;<em>Vancouver Server Management</em>&quot; -Roles $RoleGroup.Roles -CustomConfigWriteScope &quot;<em>Vancouver Servers</em>&quot;</p></td>
<td><p>Mit diesem Befehl wird ein neuer Verwaltungsbereich erstellt und eine vorhandene Rollengruppe kopiert, um Mitgliedern der neuen Rollengruppe ausschließlich das Verwalten von Server am Active Directory-Standort Vancouver zu ermöglichen.</p>
<p>Zunächst wird der Verwaltungsbereich <em>Vancouver Servers</em> erstellt, der nur Server umfasst, die sich am Active Directory-Standort <em>Vancouver</em> befinden. Der Active Directory-Standort wird im Attribut <em>ServerSite</em> der Serverobjekte angegeben.</p>
<p>Anschließend wird eine neue Rollengruppe namens <em>Vancouver Server Management</em> erstellt, bei der es sich um eine Kopie der Rollengruppe <em>Serververwaltung</em> handelt. Diese neue Rollengruppe wird jedoch so konfiguriert, dass ihre Mitglieder nur die Server verwalten können, die dem Empfängerfilterbereich <em>Vancouver Servers</em> entsprechen.</p></td>
</tr>
<tr class="even">
<td><p>Add-RoleGroupMember &quot;<em>Organisationsverwaltung</em>&quot; -Member <em>davids</em></p></td>
<td><p>Mit diesem Befehl wird der Benutzer <em>davids</em> zur Rollengruppe <em>Organisationsverwaltung</em> hinzugefügt.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -Role &quot;<em>Erstellung von E-Mail-Empfängern</em>&quot; -RoleAssignee &quot;<em>Seattle Admins</em>&quot; | Remove-ManagementRoleAssignment</p></td>
<td><p>Mit diesem Befehl wird die Rolle <em>Erstellung von E-Mail-Empfängern</em> aus der Rollengruppe <em>Seattle Admins</em> entfernt. Dieser Befehl ist nützlich, da Sie den Namen der Verwaltungsrollenzuweisung nicht kennen müssen, mit welcher die Rolle zur Rollengruppe zugewiesen wird.</p></td>
</tr>
</tbody>
</table>


## Remoteshell


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://<em>ExServer.contoso.com</em>/PowerShell/ -Authentication Kerberos</p>
<p>Import-PSSession $Session</p></td>
<td><p>Mit diesen Befehlen wird eine neue Remoteshellsitzung zwischen einem lokalen Computer in der Domäne und einem Exchange 2013-Remoteserver mit dem FQDN <em>ExServer.contoso.com</em> geöffnet. Verwenden Sie diesen Befehl, wenn Sie einen Exchange 2013-Remoteserver verwalten möchten und auf Ihrem lokalen Computer nur das Windows Management Framework installiert ist, das die Windows PowerShell-Befehlszeilenschnittstelle umfasst. Dieser Befehl verwendet Ihre aktuellen Anmeldeinformationen für die Authentifizierung beim Exchange 2013-Remoteserver.</p></td>
</tr>
<tr class="even">
<td><p>$UserCredential = Get-Credential</p>
<p>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://<em>ExServer.contoso.com</em>/PowerShell/ -Authentication Kerberos -Credential $UserCredential</p>
<p>Import-PSSession $Session</p></td>
<td><p>Mit diesen Befehlen wird eine neue Remoteshellsitzung zwischen einem lokalen Computer in der Domäne und einem Exchange 2013-Remoteserver mit dem FQDN <em>ExServer.contoso.com</em> geöffnet. Verwenden Sie diesen Befehl, wenn Sie einen Exchange 2013-Remoteserver verwalten möchten und auf Ihrem lokalen Computer nur das Windows Management Framework installiert ist, das Windows PowerShell umfasst. Dieser Befehl verwendet die von Ihnen angegebenen Anmeldeinformationen für die Authentifizierung beim Exchange 2013-Remoteserver.</p></td>
</tr>
<tr class="odd">
<td><p>Remove-PSSession $Session</p></td>
<td><p>Mit diesem Befehl wird die Remoteshellsitzung zwischen einem lokalen Computer und dem Exchange 2013-Remoteserver beendet.</p></td>
</tr>
<tr class="even">
<td><p>Import-RecipientDataProperty -Identity &quot;Tony Smith&quot; -SpokenName -FileData <em>([Byte[]]$(Get-Content -Path &quot;M:\AudioFiles\TonySmith.wma&quot; -Encoding Byte -ReadCount 0))</em></p></td>
<td><p>Dieser Befehl zeigt ein Syntaxbeispiel, dargestellt in Kursivformatierung, das zum Importieren einer Datei auf einen Exchange 2013-Remoteserver erforderlich ist. Im Beispiel wird der Cmdlet-Parameter FileData verwendet. Die Syntax kapselt die in der Datei <em>M:\AudioFiles\TonySmith.wma</em> enthaltenen Daten und streamt die Daten an die Eigenschaft FileData des Cmdlets Import-RecipientDataProperty.</p>
<p>Der Parameter FileData akzeptiert bei Verwendung dieser Syntax für die meisten Cmdlets Daten aus einer Datei auf Ihrem lokalen Computer.</p></td>
</tr>
<tr class="odd">
<td><p>Export-RecipientDataProperty -Identity tony@contoso.com -SpokenName <em>| ForEach { $_.FileData | Add-Content C:\tonysmith.wma -Encoding Byte}</em></p></td>
<td><p>Dieser Befehl zeigt ein Syntaxbeispiel, dargestellt in Kursivformatierung, das zum Exportieren einer Datei von einem Exchange 2013-Remoteserver erforderlich ist. Die Syntax kapselt die in der Eigenschaft FileData des vom Cmdlet zurückgegebenen Objekts gespeicherten Daten und streamt die Daten auf Ihren lokalen Computer. Die Daten werden anschließend in der Datei <em>C:\tonysmith.wma</em> gespeichert.</p>
<p>Die meisten Cmdlets, die Objekte mit einer Eigenschaft FileData ausgeben, verwenden diese Syntax zum Exportieren von Daten in eine Datei auf Ihrem lokalen Computer.</p></td>
</tr>
</tbody>
</table>

