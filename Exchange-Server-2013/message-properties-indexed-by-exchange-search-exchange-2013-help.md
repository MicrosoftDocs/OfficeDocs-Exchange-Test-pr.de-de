---
title: 'Von der Exchange-Suche indizierte Nachrichteneigenschaften: Exchange 2013 Help'
TOCTitle: Von der Exchange-Suche indizierte Nachrichteneigenschaften
ms:assetid: a9754dc1-44aa-4076-8b59-a5d39246d5b0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ983804(v=EXCHG.150)
ms:contentKeyID: 52062891
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Von der Exchange-Suche indizierte Nachrichteneigenschaften

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-17_

Die Exchange-Suche indiziert zahlreiche Elementeigenschaften wie Absender, Empfänger, Nachrichtentext und E-Mail-Anlagen.

## Von der Exchange-Suche indizierte Eigenschaften

Die folgende Tabelle enthält eine Liste aller von der Exchange-Suche indizierten Elementeigenschaften.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Typ</th>
<th>Abfragbar</th>
<th>Durchsuchbar</th>
<th>Abrufbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Account</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Assistantname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Attachment</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Attachmentfilenames</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Attachmentmetaproperties</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Attachmentcount</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Bcc</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Body</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Businessaddress</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Businessmainphone</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Businessphonenumber</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Carphonenumber</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Category</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Cc</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Companyname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Compositeitemid</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Conversationid</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Conversationtopic</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Departmentname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Displayname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Displaynameprefix</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Documentid</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Emailaddress</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Emaildisplayname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Emailoriginaldisplayname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Errorcode</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Fileas</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Firstname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Folderid</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>From</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Homeaddress</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Homephone</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Importance</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Ispartiallyprocessed</p></td>
<td><p>Boolescher Wert</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Ispermanentfailure</p></td>
<td><p>Boolescher Wert</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Itemclass</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Art</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Lastattempttime</p></td>
<td><p>DateTime</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Lastname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Mailboxguid</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Manager</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Meetinglocation</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Middlename</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Mobilephonenumber</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Nickname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Officelocation</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Otheraddress</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Participants</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Primarytelephonenumber</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Received</p></td>
<td><p>DateTime</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Receivedby</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Receivedrepresenting</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Recipients</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Sent</p></td>
<td><p>DateTime</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Sharinginfo</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Size</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Subject</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Tasktitle</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Title</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>To</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Umaudionotes</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Watermark</p></td>
<td><p>Ganze Zahl</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Yomicompanyname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Yomifirstname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Yomilastname</p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
</tbody>
</table>


**Hinweise zu indizierten Eigenschaften**:

  - **Abfragbare Eigenschaften** können in AQS-Abfragen von Suchclients wie Outlook Web App in `property:value`-Paaren, z. B. `from:bsuneja@cotoso.com`, verwendet werden. Eine Teilmenge der in der vorherigen Tabelle aufgeführten abfragbaren Eigenschaften kann auch in den Suchabfragen für Compliance-eDiscovery verwendet werden. Eine Liste dieser Eigenschaften finden Sie unter [Nachrichteneigenschaften und Suchoperatoren für Compliance-eDiscovery](message-properties-and-search-operators-for-in-place-ediscovery-exchange-2013-help.md).

  - **Durchsuchbare Eigenschaften** sind Eigenschaften, die nicht in `property:value`-Paaren angegeben werden können, doch eine Schlüsselwortsuche gibt den Wert zurück, sofern dieser in einer durchsuchbaren Eigenschaft gefunden wird. Sie können beispielsweise nicht `body:Contoso` zur Suche nach der Zeichenfolge `contoso` in ausschließlich dem Nachrichtentext verwenden. Eine Suche nach dieser Zeichenfolge gibt jedoch alle Elemente zurück, bei denen die Eigenschaft in einer beliebigen durchsuchbaren Eigenschaft gefunden wird.

  - **Abrufbare Eigenschaften** wie `documenteid` und `ispartiallyprocessed` werden bei allen Suchvorgängen zurückgegeben.

