---
title: 'Grundlegendes zu Verwaltungsrollen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollen
ms:assetid: 887b0a64-84b1-4b8c-9547-e456ea6f5dbd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298116(v=EXCHG.150)
ms:contentKeyID: 50476181
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Verwaltungsrollen sind ein Teil des Berechtigungsmodells für rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC), das in Microsoft Exchange Server 2013 verwendet wird. Rollen fungieren als eine logische Gruppierung von Cmdlets, die kombiniert werden, um auf die Konfiguration von Exchange 2013-Komponenten wie Postfächern, Transportregeln und Empfängern zuzugreifen, sie anzuzeigen oder zu ändern. Verwaltungsrollen können in größere Gruppierungen weiter zusammengefasst werden, die als Verwaltungsrollengruppen und Verwaltungsrollen-Zuweisungsrichtlinien bezeichnet werden. Diese ermöglichen die Verwaltung von Funktionsbereichen und die Empfängerkonfiguration. Rollengruppen und Rollenzuweisungsrichtlinien weisen Administratoren und Benutzern Berechtigungen zu. Weitere Informationen zu Verwaltungsrollengruppen und Zuweisungsrichtlinien für Verwaltungsrollen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



**Inhalt**

Integrierte Verwaltungsrollen

Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung

Benutzerdefinierte Verwaltungsrollen

Hierarchie der Verwaltungsrollen

Verwaltungsrolleneinträge

Rolleneinträge auf oberster Ebene ohne Bereichseinschränkung

Verwaltungsrollentypen

Weitere Informationen

Verwaltungsrollenbereiche und Verwaltungsrollenzuweisungen sind wichtige Komponenten für den Einsatz von Verwaltungsrollen. Weitere Informationen zu diesen Komponenten finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md)

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Verwaltungsrollen gibt? Weitere Informationen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

## Integrierte Verwaltungsrollen

Exchange 2013 stellt eine Vielzahl von integrierten Verwaltungsrollen bereit, die Sie zum Verwalten Ihrer Organisation verwenden können. Zu jeder Rolle gehören Cmdlets und Parameter, die die Benutzer zum Verwalten bestimmter Exchange-Komponenten benötigen. Im Folgenden sind Beispiele für einige integrierte Verwaltungsrollen aufgeführt:

  - **E-Mail-Empfänger**   Ermöglicht Administratoren das Verwalten von Postfächern, Kontakten und E-Mail-Benutzern.

  - **Transportregeln**   Ermöglicht Administratoren und spezialisierten Benutzern die Verwaltung der Transportregelfunktion.

  - **Verteilergruppen**   Ermöglicht Administratoren oder spezialisierten Benutzern die Verwaltung von Verteilergruppen und Mitgliedern von Verteilergruppen.

  - **MyPersonalInformation**   Ermöglicht es Endbenutzern, ihre eigene private Telefonnummer und Websiteadresse zu ändern.

Eine vollständige Liste der im Lieferumfang von Exchange 2013 enthaltenen Verwaltungsrollen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

Sie können die in Exchange 2013 bereitgestellten integrierten Rollen beliebig kombinieren und damit das für Ihren Geschäftsbereich passende Berechtigungsmodell erstellen. Wenn beispielsweise die Mitglieder einer Gruppe in der Lage sein sollen, Empfänger und Öffentliche Ordner zu verwalten, müssen Sie der Rollengruppe die Rollen "E-Mail-Empfänger" und "Öffentliche Ordner" zuweisen. In den meisten Fällen weisen Sie Rollen Rollengruppen oder Rollenzuweisungsrichtlinien zu. Sie können Benutzern Verwaltungsrollen auch direkt zuweisen, wenn Sie Berechtigungen gezielt vergeben möchten. Es wird jedoch empfohlen, Rollengruppen und Rollenzuweisungsrichtlinien zu verwenden, anstatt Benutzern direkt Rollen zuzuweisen, da das Berechtigungsmodell dadurch vereinfacht wird.


> [!NOTE]
> Rollenzuweisungsrichtlinien können nur Endbenutzerverwaltungsrollen zugewiesen werden.



Integrierte Verwaltungsrollen können nicht geändert werden. Sie können jedoch Verwaltungsrollen auf Basis von integrierten Verwaltungsrollen erstellen und diese dann Rollengruppen oder Rollenzuweisungsrichtlinien zuweisen. Anschließend können Sie die neuen Verwaltungsrollen entsprechend Ihren Anforderungen ändern. Dabei handelt es sich allerdings um eine sehr spezielle Aufgabe, die Sie nur selten (wenn überhaupt) ausführen werden.

Weitere Informationen zum Erstellen benutzerdefinierter Rollen auf Basis von integrierten Exchange-Rollen finden Sie unter Benutzerdefinierte Verwaltungsrollen weiter unten in diesem Thema.

Sie müssen Verwaltungsrollen zuweisen, damit sie wirksam werden. In den meisten Fällen weisen Sie Verwaltungsrollen Rollengruppen und Rollenzuweisungsrichtlinien zu. In bestimmten Fällen werden Rollen auch direkt einem Benutzer zugewiesen. Dabei handelt es sich allerdings um eine sehr spezielle Aufgabe, die Sie (wenn überhaupt) nur selten ausführen werden.

Weitere Informationen zum Zuweisen von Verwaltungsrollen finden Sie unter den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

Weitere Informationen zu Verwaltungsrollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung

Bei Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung handelt es sich um eine besondere Form von Verwaltungsrollen, mit denen Sie unter Verwendung von RBAC Zugriff auf benutzerdefinierte Skripts und auf Nicht-Exchange-Cmdlets erteilen können. Reguläre Verwaltungsrollen ermöglichen nur den Zugriff auf Exchange-Cmdlets. Wenn Sie Zugriff auf andere als Exchange-Cmdlets erteilen müssen, die auf einem Exchange-Server ausgeführt werden, oder ein Skript veröffentlichen müssen, das von Ihren Benutzern ausgeführt werden kann, müssen sie einer Rolle ohne Bereichseinschränkung hinzugefügt werden. Dieser Rollentyp wird als Rolle auf oberster Ebene bezeichnet, da sie bei ihrer Erstellung nicht von einer übergeordneten Rolle abgeleitet wird und daher keine übergeordnete Rolle aufweist. Sie ist den in Exchange 2013 bereitgestellten integrierten Verwaltungsrollen gleichgestellt. Um anzugeben, dass ein Eintrag für eine Rolle auf oberster Ebene ohne Bereichseinschränkung erstellt werden soll, müssen Sie die Option *UnscopedTopLevel* mit dem Cmdlet **New-ManagementRole** verwenden.

Rollen ohne Bereichseinschränkung haben diese Bezeichnung, da sie (anders als reguläre Verwaltungsrollen) nicht auf ein bestimmtes Ziel beschränkt werden können. Rollen ohne Bereichseinschränkung sind immer innerhalb der gesamten Organisation gültig. Ein Benutzer, dem eine Rolle ohne Bereichseinschränkung zugewiesen wird, kann also alle Objekte in der Exchange 2013-Organisation ändern. Daher müssen Sie sicherstellen, dass Skripts und Cmdlets, die über eine Rolle ohne Bereichseinschränkung verfügbar gemacht werden, gründlich getestet wurden, um genau zu wissen, welche Änderungen durch sie vorgenommen werden. Außerdem müssen Sie sorgfältig bei der Zuweisung von Rollen ohne Bereichseinschränkung vorgehen.

Rollen ohne Bereichseinschränkung können Rollenempfängern wie Rollengruppen, Verwaltungsrollen, Benutzern und universellen Sicherheitsgruppen (USGs) zugewiesen werden. Sie können keinen Zuweisungsrichtlinien für Verwaltungsrollen zugewiesen werden.

Exchange-Cmdlets können einer Rolle ohne Bereichseinschränkung nicht als Verwaltungsrolleneintrag hinzugefügt werden. Sie können jedoch in Skripts eingefügt werden, die als Rolleneinträge hinzugefügt werden. Dadurch können Sie benutzerdefinierte Skripts erstellen, mit denen Exchange-Aufgaben ausgeführt werden und die Benutzern zugewiesen werden. Dies ist beispielsweise sinnvoll, wenn ein Benutzer eine vertrauliche Aufgabe ausführen muss, die normalerweise außerhalb seines Zuständigkeitsbereichs liegt und für die die Erstellung einer neuen Verwaltungsrolle oder Rollengruppe problematisch wäre. In diesem Fall können Sie ein Skript erstellen, das diese spezifische Funktion ausführt, dieses Skript einer Rolle ohne Bereichseinschränkung hinzufügen und diese Rolle anschließend dem Benutzer zuweisen. Der Benutzer kann nur diese spezifische Funktion in dem Skript ausführen.

Die Rolleneinträge, die Sie einer Rolle ohne Bereichseinschränkung hinzufügen, müssen außerdem als Eintrag für eine Rolle auf oberster Ebene ohne Bereichseinschränkung gekennzeichnet werden. Weitere Informationen zu Rolleneinträgen auf oberster Ebene ohne Bereichseinschränkung finden Sie unter Rolleneinträge auf oberster Ebene ohne Bereichseinschränkung weiter unten in diesem Thema.

Die Rollengruppe Organisationsverwaltung verfügt standardmäßig nicht über die Berechtigungen zum Erstellen oder Verwalten von Rollengruppen ohne Bereichseinschränkung. Damit soll verhindert werden, dass Rollengruppen ohne Bereichseinschränkung versehentlich erstellt oder geändert werden. Die Rollengruppe Organisationsverwaltung kann die Verwaltungsrolle "Rollenverwaltung ohne Bereichseinschränkung" sich selbst oder anderen Rollenempfängern zuweisen. Weitere Informationen zum Erstellen einer Verwaltungsrolle auf oberster Ebene ohne Bereichseinschränkung finden Sie unter [Erstellen einer Rolle ohne Bereichseinschränkung](create-an-unscoped-role-exchange-2013-help.md).

Zurück zum Seitenanfang

## Benutzerdefinierte Verwaltungsrollen

Sie können benutzerdefinierte Verwaltungsrollen auf Basis von integrierten Exchange-Rollen erstellen, wenn die integrierten Verwaltungsrollen nicht den Anforderungen Ihrer Benutzer entsprechen. Bei der Erstellung einer benutzerdefinierten Verwaltungsrolle erbt die neue untergeordnete Rolle alle Verwaltungsrolleneinträge der übergeordneten Rolle. Sie können anschließend wählen, welche Verwaltungsrolleneinträge in der benutzerdefinierten Verwaltungsrolle beibehalten werden sollen, und alle Einträge entfernen, die Sie nicht benötigen.

Benutzerdefinierte Rollen werden zu untergeordneten Rollen der Rolle, die zum Erstellen der neuen Rolle verwendet wird. Sie können nur Verwaltungsrolleneinträge in der neuen untergeordneten Rolle verwenden, die auch in der übergeordneten Rolle enthalten sind. Weitere Informationen finden Sie unter den folgenden Abschnitten weiter unten in diesem Thema:

  - Hierarchie der Verwaltungsrollen

  - Verwaltungsrolleneinträge

Die Erstellung benutzerdefinierter Verwaltungsrollen erfolgt in mehreren Schritten. Dies ist eine anspruchsvolle Aufgabe, die Sie (wenn überhaupt) nur selten ausführen werden. Vor der Erstellung einer benutzerdefinierten Verwaltungsrolle müssen Sie sicherstellen, dass keine der bereits vorhandenen integrierten Verwaltungsrollen die benötigten Berechtigungen bereitstellt. Weitere Informationen zu den integrierten Verwaltungsrollen oder zum Erstellen benutzerdefinierter Verwaltungsrollen finden Sie unter den folgenden Themen:

  - [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md)

  - [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md)

Weitere Informationen zum Erstellen einer Verwaltungsrolle finden Sie unter [Erstellen einer Rolle](create-a-role-exchange-2013-help.md).

Zurück zum Seitenanfang

## Hierarchie der Verwaltungsrollen

Verwaltungsrollen stellen eine Hierarchie von unter- und übergeordneten Elementen dar. Dabei stellen die standardmäßig in Exchange 2013 bereitgestellten integrierten Verwaltungsrollen die oberste Ebene dar. Bei der Erstellung einer Rolle wird eine Kopie einer übergeordneten Rolle erstellt. Die neue Rolle ist ein untergeordnetes Element der Rolle, aus der sie kopiert wurde. Sie können die neue Rolle anschließend entsprechend den Anforderungen der Administratoren oder Benutzer anpassen, denen sie zugeordnet werden soll.

Benutzerdefinierte Rollen können verwendet werden, um Rollen zu erstellen. Wenn Sie eine Rolle auf Basis einer bereits vorhandenen benutzerdefinierten Rolle erstellen, ist diese benutzerdefinierte Rolle weiterhin ein untergeordnetes Element der übergeordneten Rolle, stellt aber gleichzeitig auch die übergeordnete Rolle der neuen Rolle dar. Jedesmal, wenn eine Rolle kopiert wird, kann die neue untergeordnete Rolle nur die Rolleneinträge enthalten, die in der unmittelbar übergeordneten Rolle vorhanden sind.

Jeder Verwaltungsrolle wird ein Rollentyp zugewiesen, der nicht geändert werden kann. Der Rollentyp definiert den Basiskontext für die Verwendung der Rolle. Der Rollentyp kann bei der Erstellung der untergeordneten Rolle aus der übergeordneten Rolle kopiert werden.

**Hierarchie der Verwaltungsrollen**

![Hierarchiediagramm für RBAC-Verwaltungsrollen](images/Dd298116.6851c829-ca8f-40e7-a67c-cc9e85c33953(EXCHG.150).gif "Hierarchiediagramm für RBAC-Verwaltungsrollen")

Die vorhergehende Abbildung verdeutlicht die hierarchische Beziehung mehrerer Verwaltungsrollen. Die Rollen "E-Mail-Empfänger" und "Helpdesk" sind integrierte Rollen. Alle untergeordneten Rollen, die von diesen Rollen abgeleitet werden, erben den Rollentyp der einzelnen integrierten Rollen. Beispielsweise erben alle untergeordneten Rollen, die direkt oder indirekt von der Rolle "E-Mail-Empfänger" abgeleitet werden, den Rollentyp `MailRecipients`.

Die benutzerdefinierte Rolle "Seattle Empfängeradministratoren" ist eine untergeordnete Rolle der integrierten Rolle "E-Mail-Empfänger", stellt aber auch die übergeordnete Rolle der benutzerdefinierten Rollen "Seattle Empfängeradministratoren 'Vertrieb'" und "Seattle Empfängeradministratoren 'Rechtsabteilung'" dar. Die benutzerdefinierte Rolle "Seattle Empfängeradministratoren" enthält nur einige der Cmdlets, die in der Rolle "E-Mail-Empfänger" verfügbar sind. Die untergeordneten Rollen der benutzerdefinierten Rolle "Seattle Empfängeradministratoren" können nur die Cmdlets enthalten, die auch in der übergeordneten Rolle vorhanden sind. Wenn in der Rolle "E-Mail-Empfänger" beispielsweise ein Cmdlet vorhanden ist, das nicht in der benutzerdefinierten Rolle "Seattle Empfängeradministratoren" enthalten ist, kann dieses Cmdlet auch nicht der benutzerdefinierten Rolle "Seattle Empfängeradministratoren 'Vertrieb'" hinzugefügt werden.

Alle benutzerdefinierten Rollen folgen demselben Muster wie die oben beschriebenen Rollen. Weitere Informationen dazu, wie der Zugriff auf Cmdlets für Verwaltungsrollen gesteuert wird, finden Sie unter Verwaltungsrolleneinträge in diesem Thema.

Zurück zum Seitenanfang

## Verwaltungsrolleneinträge

Für jede Verwaltungsrolle, unabhängig davon, ob es sich um benutzerdefinierte Exchange-Rollen oder um Rollen ohne Bereichseinschränkung handelt, muss mindestens ein Verwaltungsrolleneintrag vorhanden sein. Ein Eintrag besteht aus einem einzelnen Cmdlet und dessen Parametern, einem Skript oder einer speziellen Berechtigung, die zur Verfügung gestellt werden soll. Wenn ein Cmdlet oder Skript nicht als Eintrag für eine Verwaltungsrolle vorhanden ist, kann über diese Rolle auch nicht auf das Cmdlet oder das Skript zugegriffen werden. Ebenso ist über diese Rolle kein Zugriff auf einen Parameter in dem Cmdlet oder Skript möglich, wenn dieser Parameter nicht in einem Eintrag vorhanden ist.

Mit Exchange 2013 können Sie Rolleneinträge basierend auf integrierten Exchange-Verwaltungsrollen der obersten Ebene oder auf Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung verwalten. Rollen, die auf integrierten Exchange-Rollen auf oberster Ebene basieren, können nur Rolleneinträge enthalten, bei denen es sich um Exchange 2013-Cmdlets handelt. Damit die Benutzer benutzerdefinierte Skripts oder Nicht-Exchange-Cmdlets verwenden können, müssen Sie sie einer Rolle auf oberster Ebene ohne Bereichseinschränkung als Rolleneinträge ohne Bereichseinschränkung hinzufügen. Weitere Informationen zu Rolleneinträgen ohne Bereichseinschränkung finden Sie unter Rolleneinträge auf oberster Ebene ohne Bereichseinschränkung weiter unten in diesem Thema.

Für alle Rolleneinträge, unabhängig davon, ob es sich um einen Exchange-Cmdlet-basierten Rolleneintrag oder einen Rolleneintrag ohne Bereichseinschränkung handelt, gelten die in den folgenden Abschnitten erläuterten Prinzipien.

Weitere Informationen zu Verwaltungsrolleneinträgen finden Sie unter [Verwaltungsrollen und Rolleneinträge](management-roles-and-role-entries-exchange-2013-help.md).

## Beziehung zwischen über- und untergeordneten Verwaltungsrollen

Wie oben erwähnt, muss ein Verwaltungsrolleneintrag, einschließlich des Cmdlets und dessen Parameter, in der unmittelbar übergeordneten Rolle enthalten sein, damit er der untergeordneten Rolle hinzugefügt werden kann. Wenn die übergeordnete Rolle beispielsweise keinen Eintrag für **New-Mailbox** enthält, kann dieses Cmdlet der untergeordneten Rolle nicht zugewiesen werden. Wenn die übergeordnete Rolle zwar einen Eintrag für **Set-Mailbox** enthält, der Parameter *Database* aber aus dem Eintrag entfernt wurde, kann der Parameter *Database* im Cmdlet **Set-Mailbox** nicht dem Eintrag in der untergeordneten Rolle hinzugefügt werden.

Da Verwaltungsrolleneinträge untergeordneten Rollen nicht hinzugefügt werden können, wenn sie nicht in den übergeordneten Rollen enthalten sind, und da die Rolle auf einem bestimmten Rollentyp basiert, müssen Sie bei der Erstellung einer benutzerdefinierten Rolle die übergeordnete Rolle, die kopiert werden soll, sorgfältig auswählen.

Zurück zum Seitenanfang

## Namen der Verwaltungsrolleneinträge

Die Namen von Verwaltungsrolleneinträgen setzen sich aus der Verwaltungsrolle, der sie zugeordnet sind, und dem Namen des Cmdlets oder Skripts zusammen. Der Rollenname und der Name des Cmdlets oder Skripts sind durch einen umgekehrten Schrägstrich (\\) getrennt. Der Name des Rolleneintrags für das Cmdlet **Set-Mailbox** in der Rolle "E-Mail-Empfänger" lautet beispielsweise `Mail Recipients\Set-Mailbox`. Wenn der Name eines Rolleneintrags Leerzeichen enthält, müssen Sie den gesamten Namen in Anführungszeichen (") setzen.

Das Platzhalterzeichen (\*) kann im Namen des Rolleneintrags verwendet werden, um alle Rolleneinträge abzurufen, die der von Ihnen eingegebenen Zeichenfolge entsprechen. Dabei kann das Platzhalterzeichen entweder vor oder hinter dem umgekehrten Schrägstrich eingegeben werden. Die folgende Tabelle enthält einige Beispiele dafür, wie ein Platzhalterzeichen im Namen eines Rolleneintrags verwendet werden kann.

**Namen von Verwaltungsrolleneinträgen mit Platzhalterzeichen**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Beispiel</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>*\*</code></p></td>
<td><p>Gibt eine Liste aller Rolleneinträge für alle Rollen zurück.</p></td>
</tr>
<tr class="even">
<td><p><code>*\Set-Mailbox</code></p></td>
<td><p>Gibt eine Liste aller Rolleneinträge zurück, die das Cmdlet <strong>Set-Mailbox</strong> enthalten.</p></td>
</tr>
<tr class="odd">
<td><p><code>Mail Recipients\*</code></p></td>
<td><p>Gibt eine Liste aller Rolleneinträge für die Rolle &quot;E-Mail-Empfänger&quot; zurück.</p></td>
</tr>
<tr class="even">
<td><p><code>Mail Recipients\*Mailbox</code></p></td>
<td><p>Gibt eine Liste aller Rolleneinträge für die Rolle &quot;E-Mail-Empfänger&quot; zurück, die Cmdlets enthalten, die mit &quot;Mailbox&quot; enden.</p></td>
</tr>
<tr class="odd">
<td><p><code>My*\*Group*</code></p></td>
<td><p>Gibt für alle Rollen, die mit &quot;My&quot; beginnen, eine Liste aller Rolleneinträge zurück, die die Zeichenfolge &quot;Group&quot; im Cmdlet-Namen enthalten.</p></td>
</tr>
</tbody>
</table>


## Rolleneinträge auf oberster Ebene ohne Bereichseinschränkung

Rolleneinträge auf oberster Ebene ohne Bereichseinschränkung werden zusammen mit Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung verwendet, um Rollen auf Basis von benutzerdefinierten Skripts oder von Cmdlets zu erstellen, bei denen es sich nicht um Exchange-Cmdlets handelt. Jeder Rolleneintrag ohne Bereichseinschränkung ist einem einzigen benutzerdefinierten Skript oder einem Nicht-Exchange-Cmdlet zugeordnet. Um anzuzeigen, dass ein Rolleneintrag ohne Bereichseinschränkung in einer Rolle ohne Bereichseinschränkung erstellt werden soll, müssen Sie im Cmdlet **Add-ManagementRoleEntry** den Parameter *UnscopedTopLevel* angeben.

Wenn Sie den Rolleneintrag ohne Bereichseinschränkung hinzufügen, müssen Sie alle Parameter angeben, die mit dem Skript oder dem Nicht-Exchange-Cmdlet verwendet werden können. Wenn Sie den Rolleneintrag hinzufügen, unternimmt Exchange den Versuch, die von Ihnen angegebenen Parameter zu überprüfen. Für die Benutzer, die der Rolle ohne Bereichseinschränkung zugewiesen werden, sind nur die Parameter verfügbar, die Sie dem Rolleneintrag bei dessen Erstellung hinzufügen. Wenn Sie dem Skript oder dem Nicht-Exchange-Cmdlet Parameter hinzufügen oder einen Parameter umbenennen, müssen Sie den Rolleneintrag manuell aktualisieren. Exchange überprüft nicht, ob vorhandene Parameter in einem Rolleneintrag ohne Bereichsbeschränkung geändert wurden. Wenn ein Parameter in einem Rolleneintrag in einem Skript geändert wurde und Sie diesen Parameter verwenden möchten, schlägt der Befehl fehl.

Skripts, die einem Rolleneintrag ohne Bereichseinschränkung hinzugefügt werden, müssen sich auf jedem Server, mit dem Administratoren und Benutzer unter Verwendung der Exchange 2013-Verwaltungskonsole eine Verbindung herstellen, im Verzeichnis für Exchange-Skripts befinden. Angenommen Sie versuchen, einen Rolleneintrag ohne Bereichseinschränkung auf einem Server hinzuzufügen. Dieser Rolleneintrag basiert jedoch auf einem Skript, das sich nicht im Verzeichnis für Exchange 2013-Skripts auf dem Server befindet. Dann tritt in diesem Fall ein Fehler auf. Das Standardinstallationsverzeichnis für Exchange 2013-Skripts ist "C:\\Programme\\Microsoft\\Exchange Server\\V15\\RemoteScripts".

Cmdlets, bei denen es sich nicht um Exchange-Cmdlets handelt, und die einem Rolleneintrag ohne Bereichseinschränkung hinzugefügt werden, müssen auf jedem Server mit Exchange 2013 installiert sein, mit dem Administratoren und Benutzer unter Verwendung der Shell eine Verbindung herstellen und auf dem sie diese Cmdlets verwenden möchten. Angenommen Sie versuchen, einen Rolleneintrag ohne Bereichseinschränkung auf einem hinzuzufügen. Dieser Rolleneintrag basiert jedoch auf einem Nicht-Exchange-Cmdlet, das nicht auf dem Server mit Exchange 2013 installiert ist. Dann tritt in diesem Fall ein Fehler auf. Wenn Sie ein Nicht-Exchange-Cmdlet hinzufügen, müssen Sie den Namen des Windows PowerShell-Snap-Ins angeben, das dieses Nicht-Exchange-Cmdlet enthält.

Weitere Informationen zum Hinzufügen von Verwaltungsrolleneinträgen ohne Bereichseinschränkung finden Sie unter [Hinzufügen eines Rolleneintrags zu einer Rolle](add-a-role-entry-to-a-role-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verwaltungsrollentypen

Verwaltungsrollentypen stellen die Grundlage aller Verwaltungsrollen dar. Typen definieren die impliziten Bereiche, die in allen Verwaltungsrollen eines bestimmten Rollentyps definiert sind, und dienen außerdem zur logischen Gruppierung zusammengehöriger Rollen. Alle Verwaltungsrollen, die von übergeordneten integrierten Verwaltungsrollen abgeleitet sind, verfügen über denselben Rollentyp. Diese Beziehung wird in der Abbildung oben veranschaulicht, in der die Hierarchie der Verwaltungsrollen dargestellt ist. Verwaltungsrollentypen stellen außerdem die maximale Anzahl von Cmdlets und ihren Parametern dar, die einer einem Rollentyp zugeordneten Rolle hinzugefügt werden kann.

Verwaltungsrollentypen sind in die folgenden Kategorien unterteilt:

  - **Administrator- oder Spezialistenrollen**   Rollen des Administrator- oder Spezialistenrollentyps haben einen größeren Wirkungsbereich in der Exchange-Organisation. Rollen dieses Rollentyps ermöglichen die Ausführung von Aufgaben wie die Verwaltung von Servern oder Empfängern, die Konfiguration der Organisation, die Verwaltung der Richtlinientreue, Überwachung usw.

  - **Benutzerspezifische Rollen**   Rollen eines benutzerspezifischen Rollentyps haben einen eng an den einzelnen Benutzer gebundenen Wirkungsbereich. Rollen dieses Rollentyps ermöglichen die Ausführung von Aufgaben wie die Konfiguration von Benutzerprofilen und die Selbstverwaltung, Verwaltung der benutzerspezifischen Verteilergruppen usw.
    
    Die Namen von Rollen dieses Rollentyps sowie die Namen dieses Rollentyps beginnen mit "My".

  - **Sonderrollen**   Rollen dieses Rollentyps ermöglichen die Ausführung von Aufgaben, die nicht in den Bereich von Verwaltungsrollentypen oder benutzerspezifischen Rollentypen fallen. Rollen dieses Rollentyps ermöglichen die Ausführung von Aufgaben wie Anwendungsidentitätswechsel und die Verwendung von Nicht-Exchange-Cmdlets und -Skripts.

In der folgenden Tabellen sind alle Verwaltungsrollentypen der Kategorie "Administratorrollen" in Exchange 2013 aufgeführt. Außerdem ist angegeben, ob die mit diesem Rollentyp vorgenommenen Konfigurationen für die gesamte Exchange-Organisation gelten oder nur für einen bestimmten Benutzer. Weitere Informationen zu den einzelnen Verwaltungsrollen mit diesen Rollentypen, einschließlich einer Beschreibung der einzelnen Rollen, Hinweisen, für wen die Zuweisung dieser Rolle sinnvoll ist, und weitere Informationen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

**Administratorrollentypen**


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrollentyp</th>
<th>Integrierte Verwaltungsrolle</th>
<th>Beschreibung</th>
<th>Organisation oder Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>ActiveDirectoryPermissions</code></p></td>
<td><p><a href="active-directory-permissions-role-exchange-2013-help.md">Rolle „Active Directory-Berechtigungen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Active Directory-Berechtigungen in einer Organisation konfigurieren können. Einige Funktionen, die Active Directory-Berechtigungen oder eine Zugriffssteuerungsliste (Access Control List, ACL) verwenden, enthalten Sende- und Empfangsconnectors für den Transport sowie die Berechtigungen &quot;Senden als&quot; und &quot;Senden im Auftrag von&quot; für Postfächer.</p>

> [!NOTE]
> Berechtigungen, die direkt für Active Directory-Objekte gesetzt werden, dürfen nicht durch rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC).


</td>
<td><p>Organisation</p></td>
</tr>
<tr class="even">
<td><p><code>AddressLists</code></p></td>
<td><p><a href="address-lists-role-exchange-2013-help.md">Rolle „Adresslisten“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Adresslisten, globale Adresslisten (Global Address List, GAL) sowie Offlineadresslisten in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>ApplicationImpersonation</code></p></td>
<td><p><a href="applicationimpersonation-role-exchange-2013-help.md">Rolle „ApplicationImpersonation“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Anwendungen die Identität anderer Benutzer in einer Organisation annehmen können, um im Namen dieser Benutzer Aufgaben auszuführen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>ArchiveApplication</code></p></td>
<td><p><a href="archiveapplication-role-exchange-2013-help.md">Rolle „ArchiveApplication“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die Partneranwendungen die Archivierung von Elementen in Benutzerpostfächern in einer Organisation ermöglichen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>AuditLogs</code></p></td>
<td><p><a href="audit-logs-role-exchange-2013-help.md">Rolle „Überwachungsprotokolle“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Administratorüberwachungsprotokollierung in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>CmdletExtensionAgents</code></p></td>
<td><p><a href="cmdlet-extension-agents-role-exchange-2013-help.md">Rolle „Cmdlet-Erweiterungs-Agents“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Cmdlet-Erweiterungs-Agents in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>DataLossPrevention</code></p></td>
<td><p><a href="data-loss-prevention-role-exchange-2013-help.md">Rolle „Verhinderung von Datenverlust“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die DLP-Richtlinien (Data Loss Prevention) sowie die darin enthaltenen Regeln in einer Organisation erstellen und verwalten.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>DatabaseAvailabilityGroups</code></p></td>
<td><p><a href="database-availability-groups-role-exchange-2013-help.md">Rolle „Datenbankverfügbarkeitsgruppen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Database Availability Groups (DAGs) in einer Organisation verwalten können. Die dieser Rolle zugewiesenen Administratoren sind entweder direkt oder indirekt die Administratoren der höchsten Ebene, die für die Hochverfügbarkeitskonfiguration in einem Unternehmen zuständig sind.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>DatabaseCopies</code></p></td>
<td><p><a href="database-copies-role-exchange-2013-help.md">Rolle „Datenbankkopien“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Datenbankkopien auf einzelnen Servern verwalten können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p><code>Databases</code></p></td>
<td><p><a href="databases-role-exchange-2013-help.md">Rolle „Datenbanken“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfachdatenbanken auf einzelnen Servern erstellen, verwalten und einbinden bzw. deren Einbindung aufheben können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p><code>DisasterRecovery</code></p></td>
<td><p><a href="disaster-recovery-role-exchange-2013-help.md">Rolle „Notfallwiederherstellung“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfächer und Postfachdatenbanken wiederherstellen, Postfachdatenbanken erstellen und Datencenter-Switchovervorgänge und -Switchbacks für Database Availability Groups in einer Organisation durchführen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>DistributionGroups</code></p></td>
<td><p><a href="distribution-groups-role-exchange-2013-help.md">Rolle „Verteilergruppen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Verteilergruppen und Mitglieder von Verteilergruppen in einer Organisation erstellen und verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>EdgeSubscriptions</code></p></td>
<td><p><a href="edge-subscriptions-role-exchange-2013-help.md">Rolle „Edge-Abonnements“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Konfiguration von Edge-Synchronisierung und -Abonnement zwischen Exchange 2010-Edge-Transport-Servern und Exchange 2013-Postfachservern in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>EmailAddressPolicies</code></p></td>
<td><p><a href="e-mail-address-policies-role-exchange-2013-help.md">Rolle „E-Mail-Adressrichtlinien“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die E-Mail-Adressrichtlinien in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>ExchangeConnectors</code></p></td>
<td><p><a href="exchange-connectors-role-exchange-2013-help.md">Rolle „Exchange-Connectors“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die Administratoren das Erstellen, Ändern, Anzeigen und Entfernen von Zustellungs-Agent-Connectors ermöglichen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>ExchangeServerCertificates</code></p></td>
<td><p><a href="exchange-server-certificates-role-exchange-2013-help.md">Rolle „Exchange Server-Zertifikate“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Exchange-Serverzertifikate auf einzelnen Servern erstellen, importieren und exportieren können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p><code>ExchangeServers</code></p></td>
<td><p><a href="exchange-servers-role-exchange-2013-help.md">Rolle „Exchange-Server“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Exchange-Serverkonfiguration auf einzelnen Servern verwalten können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p><code>ExchangeVirtualDirectories</code></p></td>
<td><p><a href="exchange-virtual-directories-role-exchange-2013-help.md">Rolle „Virtuelle Exchange-Verzeichnisse“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren virtuelle Verzeichnisse für Outlook Web App, Microsoft ActiveSync, OAB (Offlineadressbuch), AutoErmittlung, Windows PowerShell und die Exchange-Verwaltungskonsole auf einzelnen Servern verwalten können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p><code>FederatedSharing</code></p></td>
<td><p><a href="federated-sharing-role-exchange-2013-help.md">Rolle „Verbundfreigabe“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die gesamtstruktur- und organisationsweite Freigabe in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>InformationRightsManagement</code></p></td>
<td><p><a href="information-rights-management-role-exchange-2013-help.md">Rolle „Information Rights Management“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die IRM-Funktionen (Information Rights Management, Verwaltung von Informationsrechten) von Exchange in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>Journaling</code></p></td>
<td><p><a href="journaling-role-exchange-2013-help.md">Rolle „Journaling“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Journalkonfiguration in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>LegalHold</code></p></td>
<td><p><a href="legal-hold-role-exchange-2013-help.md">Rolle „Gesetzliche Aufbewahrungspflicht“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren konfigurieren können, ob Daten in einem Postfach zur Beweissicherung in einer Organisation beibehalten werden sollen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>MailboxImportExport</code></p></td>
<td><p><a href="mailbox-import-export-role-exchange-2013-help.md">Rolle „Postfachimport/-export“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfachinhalte importieren und exportieren sowie unerwünschte Inhalte aus einem Postfach entfernen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>MailboxSearch</code></p></td>
<td><p><a href="mailbox-search-role-exchange-2013-help.md">Rolle „Postfachsuche“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren den Inhalt eines oder mehrerer Postfächer in einer Organisation durchsuchen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>MailboxSearchApplication</code></p></td>
<td><p><a href="mailboxsearchapplication-role-exchange-2013-help.md">Rolle „MailboxSearchApplication“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die Partneranwendungen das Einstellen und Anzeigen des Status der gesetzlichen Aufbewahrung eines Postfachs in einer Organisation ermöglichen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>MailEnabledPublicFolders</code></p></td>
<td><p><a href="mail-enabled-public-folders-role-exchange-2013-help.md">Rolle „E-Mail-fähige öffentliche Ordner“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren konfigurieren können, ob einzelne Öffentliche Ordner in einer Organisation E-Mail-aktiviert oder E-Mail-deaktiviert werden sollen.</p>
<p>Mit diesem Rollentyp können Sie nur die E-Mail-Eigenschaften öffentlicher Ordner verwalten. Er ermöglicht nicht die Verwaltung anderer Eigenschaften öffentlicher Ordner. Wenn Sie Eigenschaften öffentlicher Ordner verwalten möchten, bei denen es sich nicht um E-Mail-Eigenschaften handelt, muss Ihnen eine dem Rollentyp <code>PublicFolders</code> zugeordnete Rolle zugewiesen werden.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>MailRecipientCreation</code></p></td>
<td><p><a href="mail-recipient-creation-role-exchange-2013-help.md">Rolle „Erstellung von E-Mail-Empfängern“</a></p>
<p></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfächer, E-Mail-Benutzer, E-Mail-Kontakte, Verteilergruppen und dynamische Verteilergruppen in einer Organisation erstellen können. Rollen mit diesem Rollentyp können zusammen mit Rollen des Rollentyps <code>MailRecipients</code> kombiniert werden, um die Erstellung und Verwaltung von Empfängern zu ermöglichen.</p>
<p>Mit diesem Rollentyp können keine Öffentlichen Ordner E-Mail-aktiviert werden. Damit Öffentliche Ordner E-Mail-aktiviert werden können, muss Ihnen eine Rolle des Rollentyps <code>MailEnabledPublicFolders</code> zugewiesen sein.</p>
<p>Wenn in Ihrer Organisation ein Modell mit geteilten Berechtigungen verwendet wird, bei dem die Erstellung von Empfängern und die Verwaltung von Empfängern jeweils von einer eigenen Gruppe übernommen wird, müssen Sie der Gruppe, die für die Empfängererstellung zuständig ist, die Rolle <code>MailRecipientCreation</code> und der Gruppe, die für die Empfängerverwaltung zuständig ist, die Rolle <code>MailRecipients</code> zuweisen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>MailRecipients</code></p></td>
<td><p><a href="mail-recipients-role-exchange-2013-help.md">Rolle „Nachrichtenempfänger“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die in einer Organisation vorhandenen Postfächer, E-Mail-Benutzer, E-Mail-Kontakte, Verteilergruppen und dynamische Verteilergruppen verwalten können. Mit Rollen dieses Rollentyps können diese Empfänger nicht erstellt werden. In Kombination mit Rollen des Rollentyps <code>MailRecipientCreation</code> ist mit ihnen jedoch die Erstellung und Verwaltung von Empfängern möglich.</p>
<p>Dieser Rollentyp gestattet es Ihnen nicht, E-Mail-aktivierte Öffentliche Ordner oder Verteilergruppen zu verwalten. Für die Verwaltung E-Mail-aktivierter Öffentlicher Ordner muss Ihnen eine Rolle des Rollentyps <code>MailEnabledPublicFolders</code> zugewiesen sein. Für die Verwaltung von Verteilergruppen benötigen Sie eine Rolle des Rollentyps <code>DistributionGroups</code>.</p>
<p>Wenn in Ihrer Organisation ein Modell mit geteilten Berechtigungen verwendet wird, bei dem die Erstellung von Empfängern und die Verwaltung von Empfängern jeweils von einer eigenen Gruppe übernommen wird, müssen Sie der Gruppe, die für die Empfängererstellung zuständig ist, die Rolle <code>MailRecipientCreation</code> und der Gruppe, die für die Empfängerverwaltung zuständig ist, die Rolle <code>MailRecipients</code> zuweisen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>MailTips</code></p></td>
<td><p><a href="mail-tips-role-exchange-2013-help.md">Rolle „E-Mail-Infos“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren E-Mail-Infos in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>MessageTracking</code></p></td>
<td><p><a href="message-tracking-role-exchange-2013-help.md">Rolle „Nachrichtenverfolgung“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Nachrichten in einer Organisation verfolgen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>Migration</code></p></td>
<td><p><a href="migration-role-exchange-2013-help.md">Rolle „Migration“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfächer und den Inhalt von Postfächern in einen oder aus einem Server migrieren können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p><code>Monitoring</code></p></td>
<td><p><a href="monitoring-role-exchange-2013-help.md">Rolle „Überwachung“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Verfügbarkeit von Microsoft Exchange-Diensten und -Komponenten in einer Organisation überwachen können. Darüber hinaus können Rollen dieses Rollentyps zusammen mit dem Dienstkonto von Überwachungsanwendungen verwendet werden, um Informationen zum Zustand von Exchange-Servern zu erfassen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>MoveMailboxes</code></p></td>
<td><p><a href="move-mailboxes-role-exchange-2013-help.md">Rolle „Postfächer verschieben“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Postfächer zwischen Servern innerhalb einer Organisation und zwischen der lokalen und einer anderen Organisation verschieben können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>OfficeExtensionApplication</code></p></td>
<td><p><a href="officeextensionapplication-role-exchange-2013-help.md">Rolle „OfficeExtensionApplication“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die Microsoft Office-Erweiterungsanwendungen den Zugriff auf Benutzerpostfächer in einer Organisation ermöglichen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>OrgCustomApps</code></p></td>
<td><p><a href="org-custom-apps-role-exchange-2013-help.md">Rolle „Benutzerdefinierte Apps einer Organisation“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren benutzerdefinierte Apps ihrer Organisation in einer Organisation anzeigen und ändern können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>OrgMarketplaceApps</code></p></td>
<td><p><a href="org-marketplace-apps-role-exchange-2013-help.md">Rolle „Marketplace-Apps einer Organisation“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Marketplace-Apps ihrer Organisation in einer Organisation anzeigen und ändern können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>OrganizationClientAccess</code></p></td>
<td><p><a href="organization-client-access-role-exchange-2013-help.md">Rolle „Organisationsclientzugriff“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Einstellungen der Clientzugriffsserver in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>OrganizationConfiguration</code></p></td>
<td><p><a href="organization-configuration-role-exchange-2013-help.md">Rolle „Organisationskonfiguration“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die organisationsweiten Einstellungen in einer Organisation verwalten können. Zu den organisationsweiten Konfigurationseinstellungen, die mit diesem Rollentyp gesteuert werden können, gehören unter anderem folgende:</p>
<ul>
<li><p>Ob E-Mail-Infos für die Organisation aktiviert oder deaktiviert sind.</p></li>
<li><p>URL der Homepage für verwaltete Ordner.</p></li>
<li><p>Die Microsoft Exchange-SMTP-Empfängeradresse und alternative E-Mail-Adressen.</p></li>
<li><p>Konfiguration des Eigenschaftenschemas für Ressourcenpostfächer.</p></li>
<li><p>Hilfe-URLs für die Exchange-Verwaltungskonsole und Outlook Web App.</p></li>
</ul>
<p>Dieser Rollentyp verfügt nicht über die in den Rollentypen <code>OrganizationClientAccess</code> oder <code>OrganizationTransportSettings</code> enthaltenen Berechtigungen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>OrganizationTransportSettings</code></p></td>
<td><p><a href="organization-transport-settings-role-exchange-2013-help.md">Rolle „Organisationstransporteinstellungen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren organisationsweite Transporteinstellungen wie Systemmeldungen, Active Directory-Standortkonfiguration sowie weitere Transporteinstellungen in einer Organisation verwalten können.</p>
<p>Diese Rolle gestattet es Ihnen nicht, Transport-Empfangs- oder Sendeconnectors, Warteschlangen, Schutz, Agents, Remote- und akzeptierte Domänen oder Rollen zu erstellen oder zu verwalten. Um die einzelnen Transportfunktionen zu erstellen oder zu verwalten, müssen Ihnen Rollen der folgenden Rollentypen zugewiesen sein:</p>
<ul>
<li><p><strong>Empfangsconnectors</strong> <code>ReceiveConnectors</code></p></li>
<li><p><strong>Sendeconnectors</strong> <code>SendConnectors</code></p></li>
<li><p><strong>Transportwarteschlangen</strong> <code>TransportQueues</code></p></li>
<li><p><strong>Transportschutz</strong> <code>TransportHygiene</code></p></li>
<li><p><strong>Transport-Agents</strong> <code>TransportAgents</code></p></li>
<li><p><strong>Remote- und akzeptierte Domänen</strong> <code>RemoteAndAcceptedDomains</code></p></li>
<li><p><strong>Transportregeln</strong> <code>TransportRules</code></p></li>
</ul></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>POP3AndIMAP4Protocols</code></p></td>
<td><p><a href="pop3-and-imap4-protocols-role-exchange-2013-help.md">Rolle „POP3- und IMAP4-Protokolle“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die POP3- und IMAP4-Konfiguration (beispielsweise Authentifizierungs- und Verbindungseinstellungen) auf einzelnen Servern verwalten können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p><code>PublicFolders</code></p></td>
<td><p><a href="public-folders-role-exchange-2013-help.md">Rolle „Öffentliche Ordner“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Öffentliche Ordner in einer Organisation verwalten können.</p>
<p>Mit diesem Rollentyp kann nicht die E-Mail-Aktivierung öffentlicher Ordner verwaltet werden. Damit Öffentliche Ordner E-Mail-aktiviert oder E-Mail-deaktiviert werden können, muss Ihnen eine Rolle des Rollentyps <code>MailEnabledPublicFolders</code> zugewiesen sein.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>ReceiveConnectors</code></p></td>
<td><p><a href="receive-connectors-role-exchange-2013-help.md">Rolle „Empfangsconnectors“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Empfangsconnectorkonfiguration für den Transport wie Größenbeschränkungen auf einem einzelnen Server verwalten.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="odd">
<td><p><code>RecipientPolicies</code></p></td>
<td><p><a href="recipient-policies-role-exchange-2013-help.md">Rolle „Empfängerrichtlinien“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Empfängerrichtlinien wie Bereitstellungsrichtlinien und Richtlinien für mobile Geräte in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>RemoteAndAcceptedDomains</code></p></td>
<td><p><a href="remote-and-accepted-domains-role-exchange-2013-help.md">Rolle „Remote- und akzeptierte Domänen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Remote- und akzeptierte Domänen in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>ResetPassword</code></p></td>
<td><p><a href="reset-password-role-exchange-2013-help.md">Rolle „Kennwort zurücksetzen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Kennwörter und Administratoren die Benutzerkennwörter in einer Organisation zurücksetzen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>RetentionManagement</code></p></td>
<td><p><a href="retention-management-role-exchange-2013-help.md">Rolle „Aufbewahrungsmanagement“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Aufbewahrungsrichtlinien in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>RoleManagement</code></p></td>
<td><p><a href="role-management-role-exchange-2013-help.md">Rolle „Rollenverwaltung“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Verwaltungsrollengruppen, Rollenzuweisungsrichtlinien, Verwaltungsrollen, Rolleneinträge, Zuweisungen und Bereiche in einer Organisation verwalten können.</p>
<p>Benutzer, denen Rollen dieses Rollentyps zugewiesen sind, können die Eigenschaft <strong>role group managed by</strong> außer Kraft setzen, Rollengruppen konfigurieren oder einer Rollengruppe Mitglieder hinzufügen bzw. Mitglieder aus einer Rollengruppe entfernen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>SecurityGroupCreationAndMembership</code></p></td>
<td><p><a href="security-group-creation-and-membership-role-exchange-2013-help.md">Rolle „Sicherheitsgruppenerstellung und -mitgliedschaft“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren universelle Sicherheitsgruppen und die Mitgliedschaft zu diesen Gruppen in einer Organisation erstellen und verwalten können.</p>
<p>Wenn in Ihrer Organisation ein Modell mit geteilten Berechtigungen verwendet wird, bei dem universelle Sicherheitsgruppen von einer anderen Gruppe erstellt und verwaltet werden als der für die Verwaltung von Exchange-Servern zuständigen Gruppe, müssen Sie der Gruppe Rollen dieses Rollentyps zuweisen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>SendConnectors</code></p></td>
<td><p><a href="send-connectors-role-exchange-2013-help.md">Rolle „Sendeconnectors“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Sendeconnectors für den Transport in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>SupportDiagnostics</code></p></td>
<td><p><a href="support-diagnostics-role-exchange-2013-help.md">Rolle &quot;Diagnoseunterstützung&quot;</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren erweiterte Diagnosefunktionen unter Anleitung der Microsoft Support Services in einer Organisation ausführen.</p>

> [!WARNING]
> Rollen, denen dieser Rollentyp zugeordnet ist, erteilen Berechtigungen für Cmdlets und Skripts, die nur unter Anleitung des Microsoft Customer Service and Support verwendet werden dürfen.


</td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>TeamMailboxes</code></p></td>
<td><p><a href="team-mailboxes-role-exchange-2013-help.md">Rolle „Teampostfächer“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren eine oder mehrere Bereitstellungsrichtlinien für Websitepostfächer definieren und Websitepostfächer in einer Organisation verwalten können. Administratoren, denen diesem Rollentyp zugeordnete Rollen zugewiesen werden, können Websitepostfächer verwalten, die ihnen nicht gehören.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>TeamMailboxLifecycleApplication</code></p></td>
<td><p><a href="teammailboxlifecycleapplication-role-exchange-2013-help.md">Rolle „TeamMailboxLifecycleApplication“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, die Partneranwendungen die Aktualisierung des Lebenszyklusstatus von Websitepostfächern in einer Organisation ermöglichen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>TransportAgents</code></p></td>
<td><p><a href="transport-agents-role-exchange-2013-help.md">Rolle „Transport-Agents“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Transport-Agents in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>TransportHygiene</code></p></td>
<td><p><a href="transport-hygiene-role-exchange-2013-help.md">Rolle „Transportschutz“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Antispam- und Antischadsoftwarefunktionen in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>TransportQueues</code></p></td>
<td><p><a href="transport-queues-role-exchange-2013-help.md">Rolle „Transportwarteschlangen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Transportwarteschlangen auf einem bestimmten Server verwalten können.</p></td>
<td><p>Server</p></td>
</tr>
<tr class="even">
<td><p><code>TransportRules</code></p></td>
<td><p><a href="transport-rules-role-exchange-2013-help.md">Rolle „Transportregeln“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Transportregeln in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>UMMailboxes</code></p></td>
<td><p><a href="um-mailboxes-role-exchange-2013-help.md">Rolle „UM-Postfächer“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die UM-Konfiguration (Unified Messaging) von Postfächern und anderen Empfängern in einer Organisation verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>UMPrompts</code></p></td>
<td><p><a href="um-prompts-role-exchange-2013-help.md">Rolle „UM-Ansagen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren benutzerdefinierte UM-Sprachansagen in einer Organisation erstellen und verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>UnifiedMessaging</code></p></td>
<td><p><a href="unified-messaging-role-exchange-2013-help.md">Serverrolle UnifiedMessaging</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Unified Messaging-Dienste in einer Organisation verwalten können.</p>
<p>Diese Rolle gestattet es Ihnen nicht, UM-spezifische Postfachkonfigurationen oder UM-Ansagen zu verwalten. Für die Verwaltung der UM-spezifischen Postfachkonfiguration müssen Sie Rollen des Rollentyps <code>UMMailboxes</code> verwenden. Für die Verwaltung von UM-Ansagen müssen Sie Rollen des Rollentyps <code>UMPrompts</code> verwenden.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>UnScopedRoleManagement</code></p></td>
<td><p><a href="unscoped-role-management-role-exchange-2013-help.md">Rolle „Rollenverwaltung ohne Bereichseinschränkung“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Verwaltungsrollen auf oberster Ebene ohne Bereichseinschränkung in einer Organisation erstellen und verwalten können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>UserOptions</code></p></td>
<td><p><a href="user-options-role-exchange-2013-help.md">Rolle „Benutzeroptionen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Outlook Web App-Optionen eines Benutzers in einer Organisation anzeigen können. Rollen dieses Rollentyps können dazu verwendet werden, Benutzern bei der Diagnose von Problemen in Zusammenhang mit ihrer Konfiguration zu unterstützen.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>UserApplication</code></p></td>
<td><p><a href="userapplication-role-exchange-2013-help.md">Rolle „UserApplication“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Partneranwendungen im Namen von Endbenutzern in einer Organisation agieren können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>ViewOnlyAuditLogs</code></p></td>
<td><p><a href="view-only-audit-logs-role-exchange-2013-help.md">Rolle „Überwachungsprotokolle nur anzeigen“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren das Administrator-Überwachungsprotokoll in einer Organisation durchsuchen können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>ViewOnlyConfiguration</code></p></td>
<td><p><a href="view-only-configuration-role-exchange-2013-help.md">Rolle „Konfiguration (nur Anzeige)“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren alle Exchange-Konfigurationseinstellungen in einer Organisation anzeigen können, bei denen es sich nicht um empfängerspezifische Einstellungen handelt. Beispiele für anzeigbare Konfigurationen sind Serverkonfigurationen, Transportkonfigurationen, Datenbankkonfigurationen und unternehmensweite Konfigurationen.</p>
<p>Rollen dieses Rollentyps können zusammen mit Rollen des Rollentyps <code>ViewOnlyRecipients</code> verwendet werden, um eine Rolle zu erstellen, mit der alle Objekte in einer Organisation angezeigt werden können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="odd">
<td><p><code>ViewOnlyRecipients</code></p></td>
<td><p><a href="view-only-recipients-role-exchange-2013-help.md">Rolle „Empfänger mit Leserechten“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren die Konfiguration von Empfängern wie Postfächer, E-Mail-Benutzer, E-Mail-Kontakte, Verteilergruppen und dynamische Verteilergruppen anzeigen können.</p>
<p>Rollen dieses Rollentyps können zusammen mit Rollen des Rollentyps <code>ViewOnlyConfiguration</code> verwendet werden, um eine Rolle zu erstellen, mit der alle Objekte in der Organisation angezeigt werden können.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
<tr class="even">
<td><p><code>WorkloadManagement</code></p></td>
<td><p><a href="workloadmanagement-role-exchange-2013-help.md">Rolle „WorkloadManagement“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Administratoren Richtlinien zur Verwaltung der Arbeitsauslastung in einer Organisation verwalten können. Administratoren können Definitionen für die Ressourcenintegrität sowie Klassifikationen für die Arbeitsauslastung konfigurieren und die Verwaltung der Arbeitsauslastung aktivieren oder deaktivieren.</p></td>
<td><p>Organization (Organisation)</p></td>
</tr>
</tbody>
</table>


In der folgenden Tabelle sind alle benutzerspezifischen Verwaltungsrollentypen und die zugeordneten integrierten Verwaltungsrollen in Exchange 2013 aufgelistet.

**Benutzerdefinierte Rollentypen**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrollentyp</th>
<th>Integrierte benutzerspezifische Rollen</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>MyBaseOptions</code></p></td>
<td><p><a href="mybaseoptions-role-exchange-2013-help.md">Rolle „MyBaseOptions“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer die Basiskonfiguration ihres eigenen Postfachs und die entsprechenden Einstellungen anzeigen und ändern können.</p></td>
</tr>
<tr class="even">
<td><p><code>MyContactInformation</code></p></td>
<td><p><a href="myaddressinformation-role-exchange-2013-help.md">MyAddressInformation-Rolle</a></p>
<p><a href="mycontactinformation-role-exchange-2013-help.md">Rolle „MyContactInformation“</a></p>
<p><a href="mymobileinformation-role-exchange-2013-help.md">MyMobileInformation-Rolle</a></p>
<p><a href="mypersonalinformation-role-exchange-2013-help.md">MyPersonalInformation-Rolle</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Kontaktinformationen ändern können. Zu diesen Informationen gehören Adresse und Telefonnummern.</p></td>
</tr>
<tr class="odd">
<td><p>MyCustomApps</p></td>
<td><p><a href="my-custom-apps-role-exchange-2013-help.md">Rolle „Eigene benutzerdefinierte Apps“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen einzelne Benutzer ihre benutzerdefinierten Apps anzeigen und ändern können.</p></td>
</tr>
<tr class="even">
<td><p>MyDiagnostics</p></td>
<td><p><a href="mydiagnostics-role-exchange-2013-help.md">Rolle „MyDiagnostics“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen einzelne Benutzern einfache Diagnoseaufgaben für ihr Postfach ausführen können, z. B. das Abrufen von Kalenderdiagnoseinformationen.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyDistributionGroupMembership</code></p></td>
<td><p><a href="mydistributiongroupmembership-role-exchange-2013-help.md">Rolle „MyDistributionGroupMembership“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Mitgliedschaft in Verteilergruppen in einer Organisation anzeigen und ändern können, sofern die Bearbeitung der Mitgliedschaft für diese Verteilergruppen gestattet ist.</p></td>
</tr>
<tr class="even">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><a href="mydistributiongroups-role-exchange-2013-help.md">Rolle „MyDistributionGroups“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer Verteilergruppen erstellen, ändern und anzeigen können. Außerdem können sie die Mitglieder in den Verteilergruppen, deren Eigner sie sind, ändern, anzeigen, diesen Verteilergruppen hinzufügen oder aus diesen Verteilergruppen entfernen.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyProfileInformation</code></p></td>
<td><p><a href="mydisplayname-role-exchange-2013-help.md">MyDisplayName-Rolle</a></p>
<p><a href="myname-role-exchange-2013-help.md">MyName Rolle</a></p>
<p><a href="myprofileinformation-role-exchange-2013-help.md">Rolle „MyProfileInformation“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Namen ändern können.</p></td>
</tr>
<tr class="even">
<td><p>MyMarketplaceApps</p></td>
<td><p><a href="my-marketplace-apps-role-exchange-2013-help.md">Rolle „Eigene Marketplace-Apps“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen einzelne Benutzer ihre Marketplace-Apps anzeigen und ändern können.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyRetentionPolicies</code></p></td>
<td><p><a href="myretentionpolicies-role-exchange-2013-help.md">Rolle „MyRetentionPolicies“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Aufbewahrungstags anzeigen sowie die Einstellungen und Standardeinstellungen ihrer Aufbewahrungstags anzeigen und ändern können.</p></td>
</tr>
<tr class="even">
<td><p>MyTeamMailboxes</p></td>
<td><p><a href="myteammailboxes-role-exchange-2013-help.md">Rolle „MyTeamMailboxes“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen einzelne Benutzer Websitepostfächer erstellen und mit Microsoft SharePoint-Websites verbinden können.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyTextMessaging</code></p></td>
<td><p><a href="mytextmessaging-role-exchange-2013-help.md">Rolle „MyTextMessaging“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Textnachrichteneinstellungen erstellen, anzeigen und ändern können.</p></td>
</tr>
<tr class="even">
<td><p><code>MyVoiceMail</code></p></td>
<td><p><a href="myvoicemail-role-exchange-2013-help.md">Rolle „MyVoiceMail“</a></p></td>
<td><p>Dieser Rollentyp ist Rollen zugeordnet, mit denen Benutzer ihre Voicemail-Einstellungen anzeigen und ändern können.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Weitere Informationen

[New-ManagementRole](https://technet.microsoft.com/de-de/library/dd298073\(v=exchg.150\))

[New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\))

[Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\))

[New-ManagementScope](https://technet.microsoft.com/de-de/library/dd335137\(v=exchg.150\))

[Set-ManagementScope](https://technet.microsoft.com/de-de/library/dd297996\(v=exchg.150\))

[New-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335193\(v=exchg.150\))

[Set-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd335173\(v=exchg.150\))

