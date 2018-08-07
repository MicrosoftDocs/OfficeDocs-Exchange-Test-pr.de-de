---
title: 'Vorb. v. Postfäch. f. ges.str.übergr. Versch.anford.: Exchange 2013-Hilfe'
TOCTitle: Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen
ms:assetid: fdbed4fc-a77e-40d5-a211-863b05d74784
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633491(v=EXCHG.150)
ms:contentKeyID: 50477145
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-11-22_

**Zusammenfassung:**  erfahren Sie mehr über vorbereiten Postfächer für gesamtstrukturübergreifende in Exchange 2013 verschoben.

Microsoft Exchange 2013 unterstützt das Verschieben von Postfächern und Migrationen mithilfe der Exchange-Verwaltungsshell, insbesondere die **New-MoveRequest** und **New-MigrationBatch** -Cmdlets. Sie können auch das Postfach über Exchange Administration Center (EAC) verschieben. Beachten Sie, dass Sie Exchange 2010 und Exchange 2013-Postfächer in einer Gesamtstruktur Exchange 2013 verschieben können.

Um ein Postfach aus einer Gesamtstruktur Exchange in einer Gesamtstruktur Exchange 2013 zu verschieben, muss die Zielgesamtstruktur Exchange 2013 einen gültigen e-Mail-aktivierten Benutzer mit einem angegebenen Satz von Active Directory Attribute enthalten. Ist mindestens ein Exchange 2013-Clientzugriffs-Server in der Gesamtstruktur bereitgestellt, gilt die Gesamtstruktur eine Exchange 2013-Gesamtstruktur.

Zur Vorbereitung der Postfachverschiebung müssen E-Mail-aktivierte Benutzer mit den erforderlichen Attributen in der Zielgesamtstruktur erstellt werden. Im Folgenden werden die empfohlenen Vorgehensweisen zum Erstellen von E-Mail-aktivierten Benutzern mit den erforderlichen Attributen beschrieben:

  - Wenn Microsoft Identity Lifecycle Manager (ILM) für die gesamtstrukturübergreifende GAL-Synchronisierung bereitgestellt wurde, ist die empfohlene Vorgehensweise zum Erstellen des E-Mail-aktivierten Benutzers die Verwendung von Service Pack 1 (SP1) für ILM 2007 Feature Pack 1 (FP1). Anhand von Beispielcode können Sie ermitteln, wie ILM für die Synchronisierung des Quellpostfachbenutzers und des Ziel-E-Mail-Benutzers angepasst wird.
    
    Weitere Informationen, u. a. zum Herunterladen des Beispielcodes, finden Sie unter [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode](prepare-mailboxes-for-cross-forest-moves-using-sample-code-exchange-2013-help.md).

  - Wenn Sie den Ziel-E-Mail-Benutzer mithilfe eines anderen Active Directory-Tools als ILM/MIIS erstellt haben, verwenden Sie das Cmdlet **Update-Recipient** mit dem Parameter *Identity*, um den Adresslistendienst auszuführen und **LegacyExchangeDN** für den Ziel-E-Mail-Benutzer zu generieren. Wir haben ein Windows PowerShell-Beispielscript erstellt, das Lese- und Schreibvorgänge für Active Directory ausführt und das Cmdlet **Update-Recipient** aufruft.
    
    Weitere Informationen zum Verwenden des Beispielskripts finden Sie unter [Vorbereiten von Postfächern für eine standortübergreifende Verschiebung mit dem Skript „Prepare-MoveRequest.ps1\&quot; in der Shell](prepare-mailboxes-for-cross-forest-moves-using-the-prepare-moverequest-ps1-script-in-the-shell-exchange-2013-help.md).

Nach dem Erstellen des Ziel-E-Mail-Benutzers können Sie die Cmdlets **New-MoveRequest** oder **New-MigrationBatch** ausführen, um das Postfach in die Exchange 2013-Zielgesamtstruktur zu verschieben.

Weitere Informationen zu Remoteverschiebungsanforderungen finden Sie unter den folgenden Themen:

  - [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\))

  - [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\))

Weitere Informationen zu Remotepostfachverschiebungen und Remote-Legacyverschiebungen finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

Im Rest dieses Kapitels werden die Attribute von Active Directory-E-Mail-Benutzern erläutert, die für eine Postfachverschiebung erforderlich sind. Diese Attribute werden konfiguriert, wenn Sie entweder den Code oder das Skript zur Vorbereitung der Postfachverschiebung nutzen. Die Attribute können jedoch auch manuell mithilfe eines Active Directory-Editors kopiert werden.

## Für eine Postfachverschiebung erforderliche Active Directory-Benutzerattribute

Um eine Remotepostfachverschiebung zu unterstützen, muss das E-Mail-Benutzerobjekt in der Exchange 2013-Zielgesamtstruktur über die in diesem Abschnitt beschriebenen Active Directory-Attribute verfügen:

  - Erforderliche Attribute

  - Optionale Attribute

  - Verknüpfte Attribute

  - Attribute verknüpfter Benutzer

  - Ressourcenpostfachattribute

  - Weitere Attribute

## Erforderliche Attribute

In der folgenden Tabelle sind die mindestens erforderlichen Attribute aufgeführt, die für eine ordnungsgemäße Funktionsweise des Cmdlets **New-MoveRequest** in ILM für den Ziel-E-Mail-Benutzer konfiguriert werden müssen.

### Attribute des E-Mail-Benutzers

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>displayName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs, oder generieren Sie einen neuen Wert.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mail</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>mailNickname</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs, oder generieren Sie einen neuen Wert.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchArchiveGUID and msExchArchiveName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs. Attribute sind nur verfügbar, wenn es sich bei dem Quellpostfach um ein Exchange 2010-Postfach handelt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMailboxGUID</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>-2147483642 (Dezimalwert) //entspricht 0x80000006 (Hexadezimalwert).</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchRecipientTypeDetails</strong></p></td>
<td><p>128 (Dezimalwert) /0x80 (Hexadezimalwert).</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchUserCulture</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchVersion</strong></p></td>
<td><p>44220983382016 (Dezimalwert).</p></td>
</tr>
<tr class="even">
<td><p><strong>cn</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs, oder generieren Sie einen neuen Wert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>proxyAddresses</strong></p></td>
<td><p>Kopieren Sie das Attribut <strong>proxyAddresses</strong> des Quellpostfachs. Kopieren Sie zusätzlich das Attribut <strong>LegacyExchangeDN</strong> des Quellpostfachs als X500-Adresse in das Attribut <strong>proxyAddresses</strong> des Ziel-E-Mail-Benutzers.</p>

> [!NOTE]
> Das Attribut <STRONG>proxyAddresses</STRONG> des Quellpostfachbenutzers muss eine SMTP-Adresse enthalten, die mit der autoritativen Domäne der Zielgesamtstruktur übereinstimmt. So kann das Cmdlet <STRONG>New-MoveRequest</STRONG> den <STRONG>targetAddress</STRONG>-Wert des E-Mail-aktivierten Quellbenutzers (der nach Abschluss der Postfachverschiebungsanforderung aus dem Quellpostfachbenutzer konvertiert wird) ordnungsgemäß auswählen, um die E-Mail-Routingfunktionalität sicherzustellen.


</td>
</tr>
<tr class="even">
<td><p><strong>sAMAccountName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs, oder generieren Sie einen neuen Wert.</p>
<p>Stellen Sie sicher, dass der Wert innerhalb der Zielgesamtstrukturdomäne, zu welcher der Ziel-E-Mail-Benutzer gehört, eindeutig ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>targetAddress</strong></p></td>
<td><p>Legen Sie den Wert auf eine SMTP-Adresse im Attribut <strong>proxyAddresses</strong> des Quellpostfachs fest.</p>
<p>Diese SMTP-Adresse muss zur autoritativen Domäne der Quellgesamtstruktur gehören.</p></td>
</tr>
<tr class="even">
<td><p><strong>userAccountControl</strong></p></td>
<td><p>Konstante: 514 //entspricht 0x202, ACCOUNTDISABLE | NORMAL_ACCOUNT.</p></td>
</tr>
<tr class="odd">
<td><p><strong>userPrincipalName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs, oder generieren Sie einen neuen Wert. Da die Anmeldung für den E-Mail-Benutzer deaktiviert ist, wird <strong>userPrincipalName</strong> nicht verwendet.</p></td>
</tr>
</tbody>
</table>


## Optionale Attribute

Die Konfiguration der folgenden Attribute ist für eine ordnungsgemäße Funktionsweise des Cmdlets **New-MoveRequest** nicht erforderlich. Dennoch bietet die Synchronisierung dieser Attribute ein besseres Benutzererlebnis nach dem Verschieben des Postfachs. Da dieser Ziel-E-Mail-Benutzer in der globalen Adressliste der Zielgesamtstruktur angezeigt wird, sollten die folgenden GAL-bezogenen Attribute gesetzt werden.

### GAL-bezogene Attribute

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>c</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>co</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>countryCode</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>company</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>department</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>facsimileTelephoneNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>givenName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>homePhone</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>info</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>initials</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>l</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>mobile</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchAssistantName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchHideFromAddressLists</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherHomePhone</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherTelephone</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>pager</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>physicalDeliveryOfficeName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>postalCode</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>sn</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>st</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>streetAddress</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>telephoneAssistant</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>telephoneNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>title</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
</tbody>
</table>


## Verknüpfte Attribute

Bei einem verknüpften Attribut handelt es sich um ein Active Directory-Attribut, das andere Active Directory-Objekte in der lokalen Gesamtstruktur referenziert. Die verknüpften Attributwerte können nicht direkt aus einem Postfach in der Quellgesamtstruktur in einen E-Mail-Benutzer in der Zielgesamtstruktur kopiert werden. Zunächst müssen Sie die Active Directory-Objekte in der Quellgesamtstruktur ermitteln, die das Quellpostfachattribut referenziert. Anschließend müssen Sie die entsprechenden Active Directory-Objekte in der Zielgesamtstruktur für die oben genannten Active Directory-Objekte in der Quellgesamtstruktur ermitteln. Abschließend legen Sie das Attribut des Ziel-E-Mail-Benutzers so fest, dass die Active Directory-Objekte in der Zielgesamtstruktur referenziert werden.

### Verknüpfte Attribute

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>altRecipient</strong></p></td>
<td><p>Entsprechen dem Attribut <strong>altRecipient</strong> des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>deliverAndRedirect</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs. Bei diesem Attribut handelt es sich um einen boolschen Wert, der mit <strong>altRecipient</strong> festgelegt werden sollte.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Manager</strong> (sowie die dazugehörigen Backlinks)</p></td>
<td><p>Entsprechen dem Manager-Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>MemberOf</strong> (Backlinks)</p></td>
<td><p>Dies ist der Backlink des Gruppenmitgliedattributs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>publicDelegates</strong> (sowie die dazugehörigen Backlinks)</p></td>
<td><p>Entsprechen dem Attribut <strong>publicDelegates</strong> des Quellpostfachs.</p></td>
</tr>
</tbody>
</table>


## Attribute verknüpfter Benutzer

Wenn ein Postfach in eine Exchange 2013-Ressourcengesamtstruktur verschoben werden soll, wird das Postfach in der Ressourcengesamtstruktur als *verknüpftes Postfach* betrachtet. In diesem Szenario muss ein verknüpfter E-Mail-Benutzer in der (Ziel-) Ressourcengesamtstruktur erstellt werden. Zum Erstellen eines verknüpften E-Mail-Benutzers müssen die in der folgenden Tabelle aufgeführten Attribute gesetzt werden.

### Attribute verknüpfter E-Mail-Benutzer

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>msExchMasterAccountHistory</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMasterAccountSid</strong></p></td>
<td><p>Wenn das Quellpostfach über ein Attribut <strong>msExchMasterAccountSid</strong> verfügt, kopieren Sie dieses. Kopieren Sie anderenfalls das Attribut <strong>objectSid</strong> des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>Konstante: -1073741818 (Dezimalwert) //entspricht &quot;*unsigned* 0xC0000006&quot;.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Ein verknüpftes Postfach kann nur erstellt werden, wenn zwischen der Quell- und der Zielgesamtstruktur eine Gesamtstrukturvertrauensstellung besteht.



Wenn das Quellobjekt deaktiviert und das Attribut **msExchMasterAccountSid** auf "Self" (Ressourcenpostfach, freigegebenes Postfach) festgelegt ist, versehen Sie den Zielbenutzer nicht mit einem Stempel.

Wenn das Quellobjekt deaktiviert und das Attribut **msExchMasterAccountSid** nicht gesetzt ist, ist das Postfach ungültig.

Wenn das Quellobjekt aktiviert und das Attribut **msExchMasterAccountSid** gesetzt ist, ist das Postfach ungültig.

## Ressourcenpostfachattribute

Wenn Sie ein Ressourcenpostfach in eine Exchange 2013-Gesamtstruktur verschieben möchten, müssen die in der folgenden Tabelle aufgeführten Attribute für den Ziel-E-Mail-Benutzer gesetzt werden.

### Ressourcenpostfachattribute

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>Wenn es sich beim Quellpostfach um einen Konferenzraum handelt:</p>
<ul>
<li><p><strong>Konstante</strong>   -2147481850 (Dezimalwert) //entspricht &quot;*unsigned* 0x80000706&quot;.</p></li>
</ul>
<p>Wenn es sich beim Quellpostfach um ein Gerätepostfach handelt:</p>
<ul>
<li><p><strong>Konstante</strong>   -2147481594 (Dezimalwert) //entspricht &quot;*unsigned* 0x80000806&quot;.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>msExchResourceCapacity</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchResourceDisplay</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchResourceMetaData</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchResourceSearchProperties</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
</tbody>
</table>


## Weitere Attribute

In Exchange 2007 wurden beim Verschieben eines Postfachs über das Cmdlet **Move-Mailbox** auch die in der folgenden Tabelle aufgeführten Attribute kopiert. Wenn diese Attribute von Ihrer Organisation benötigt werden, können Sie sie optional kopieren.

### Ressourcenpostfachattribute

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Attribute des E-Mail-Benutzers</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>comment</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>deletedItemFlags</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>delivContLength</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>departmentNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>description</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>division</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>employeeID</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>employeeNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>employeeType</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>extensionAttribute1-15</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>homePostalAddress</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>internationalISDNNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ipPhone</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>language</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>lmPwdHistory</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>localeID</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>mAPIRecipient</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>middleName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticCompanyName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msDS-PhoneticDepartment</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticDisplayName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msDS-PhoneticFirstName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticLastName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchBlockedSendersHash</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchELCExpirySuspensionEnd</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchELCExpirySuspensionStart</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchELCMailboxFlags</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchExternalOOFOptions</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneFlags</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMessageHygieneSCLDeleteThreshold</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneSCLJunkThreshold</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMessageHygieneSCLQuarantineThreshold</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneSCLRejectThreshold</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMDBRulesQuota</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchPoliciesExcluded</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchSafeRecipientsHash</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchSafeSendersHash</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchUMSpokenName</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherFacsimileTelephoneNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherIpPhone</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherMobile</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherPager</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>preferredDeliveryMethod</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>personalPager</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>personalTitle</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>photo</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>pOPCharacterSet</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>pOPContentFormat</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>postalAddress</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>postOfficeBox</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>primaryInternationalISDNNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>primaryTelexNumber</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>showInAdvancedViewOnly</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>street</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>terminalServer</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>textEncodedORAddress</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>thumbnailLogo</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>thumbnailPhoto</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>url</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>userCert</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>userCertificate</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="even">
<td><p><strong>userSMIMECertificate</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>wWWHomePage</strong></p></td>
<td><p>Kopieren Sie das entsprechende Attribut des Quellpostfachs.</p></td>
</tr>
</tbody>
</table>

