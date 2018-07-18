---
title: 'Verwenden von Outlook Web App-Webparts: Exchange 2013 Help'
TOCTitle: Verwenden von Outlook Web App-Webparts
ms:assetid: 7272e3ab-430c-4d6c-8621-9535236ce463
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt574711(v=EXCHG.150)
ms:contentKeyID: 70086933
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden von Outlook Web App-Webparts

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-31_

Mit MicrosoftOfficeOutlook Web App-Webparts können Sie festlegen, welches Postfach geöffnet werden soll, welcher Ordner in diesem Postfach geöffnet werden soll und welche Inhaltsansicht verwendet werden soll.

Über Outlook Web App-Webparts können Sie direkt über eine URL auf Outlook Web App-Inhalte zugreifen. Die URL kann in einen Webbrowser eingegeben oder in eine Anwendung eingebettet werden. Im Allgemeinen werden Webparts nicht manuell erstellt. Stattdessen werden sie programmgesteuert basierend auf der Auswahl erstellt, die in einer Benutzeroberfläche getroffen wird. Alternativ können sie auch direkt in eine Anwendung eingebettet werden, beispielsweise in eine SharePoint Server-Seite. Anhand des der Benutzeroberfläche zugrunde liegenden Codes wird die URL erstellt. Outlook Web App-Webparts können unter anderem dazu verwendet werden, den Posteingang oder Kalender eines Benutzers auf einer SharePoint-Seite anzuzeigen.


> [!NOTE]
> Damit Outlook Web App-Webparts verwendet werden können, müssen sich das Postfach des Benutzers und das Postfach, das über das betreffende Webpart geöffnet wird, in derselben Active Directory-Gesamtstruktur befinden.



## Berechtigungen für die Verwendung von Outlook Web Access-Webparts

Damit Sie Outlook Web App-Webparts verwenden können, muss für die zu öffnenden Inhalte mindestens das Zugriffsrecht "Prüfer" an Sie delegiert worden sein. Haben Sie in eine Anwendung ein Outlook Web App-Webpart eingebettet, das eine Authentifizierung erfordert, müssen Sie mit der Anforderung des Webparts auch Authentifizierungsinformationen übergeben. Dazu können Sie beispielsweise das virtuelle Outlook Web App-Verzeichnis so konfigurieren, dass die integrierte Windows-Authentifizierung verwendet wird. Mit der integrierten Windows-Authentifizierung können Benutzer, die sich bereits mit ihrem Active Directory-Konto angemeldet haben, Outlook Web App verwenden, ohne ihre Anmeldeinformationen erneut eingeben zu müssen.

## Syntax von Outlook Web Access-Webparts

Outlook Web App in Exchange 2013 verwendet ein bestimmtes URL-Format für Anforderungen an das virtuelle Verzeichnis "/owa". Diese Anforderungen können erfolgen, indem die URL direkt in einen Webbrowser eingegeben wird oder indem die URL in eine Webanwendung (z. B. eine SharePoint Server-Seite) eingebettet wird.

Mit Outlook Web App-Webparts lassen sich URLs verschiedenster Komplexitätsstufen erstellen. Eine einfache Webpart-URL kann zum Öffnen des Posteingangs eines beliebigen Postfachs verwendet werden. Eine komplexere Webpart-URL kann verwendet werden, um das zu öffnende Postfach, den Ordner innerhalb des zu öffnenden Postfachs sowie die zu verwendende Inhaltsansicht anzugeben.

Je nach den Sicherheitsvorkehrungen, die für Ihr Netzwerk getroffen wurden, müssen Sie für die Webpart-URLs eventuell eine Codierung konfigurieren. Nachdem Sie die Codierung konfiguriert haben, erstellt der der Benutzeroberfläche zugrunde liegende Code die URL unter Verwendung der URL-codierten Parameter. Bei URL-codierten Parametern wird "%20" anstelle des Leerzeichens und "%2f" anstelle des Pfadtrennzeichens "/" verwendet. In allen Beispielen in diesem Artikel werden codierte Parameter verwendet.

Die folgende Tabelle enthält die Parameter eines Webparts sowie Beispiele für deren Verwendung.

### Webpartparameter und deren Verwendung

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>URL-Parameter</th>
<th>Beschreibung</th>
<th>Werte und Beispiele</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servername und Verzeichnis (erforderlich)</p></td>
<td><p>Die URL des virtuellen Outlook Web App-Verzeichnisses</p></td>
<td><p>Hierbei kann es sich um dieselbe URL handeln, die die Benutzer zur Anmeldung bei Outlook Web App verwenden, beispielsweise:</p>
<p>https://&lt;<em>server name</em>&gt;/owa</p></td>
</tr>
<tr class="even">
<td><p>Bezeichner des Exchange 2013-Postfachs, bei dem eine explizite Anmeldung durchgeführt werden soll (optional)</p></td>
<td><p>Eine beliebige SMTP-Adresse, die dem zu öffnenden Postfach zugeordnet ist.</p>
<p>Wenn dieser Teil der URL fehlt, wird das Standardpostfach des authentifizierten Benutzers geöffnet.</p>
<p>Werden keine weiteren Parameter angegeben, besteht das Standardverhalten im Öffnen des Posteingangs.</p></td>
<td><p>Zum Öffnen des Postfachs mit der SMTP-Adresse tsmith@fourthcoffee.com würden Sie die folgende URL verwenden:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/tsmith@fourthcoffee.com</p></td>
</tr>
<tr class="odd">
<td><p>cmd (erforderlich, wenn Sie andere Parameter als den Bezeichner des Postfachs angeben, bei dem eine explizite Anmeldung durchgeführt werden soll)</p></td>
<td><p>Mit &quot;?cmd=contents&quot; wird statt der vollständigen Outlook Web App-Benutzeroberfläche das Outlook Web App-Webpart angezeigt, das über die Parameter festgelegt wurde.</p></td>
<td><p>Wenn kein Postfach angegeben wird, folgt der Parameter &quot;cmd&quot; auf die Anmeldeadresse. Beispiel:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/?cmd=contents</p>
<p>Wenn ein Postfach angegeben wird, folgt der Parameter &quot;cmd&quot; auf den Bezeichner des Postfachs, bei dem die explizite Anmeldung durchgeführt werden soll. Beispiel:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/&lt;<em>SMTP address</em>&gt;/?cmd=contents</p>
<p>Werden keine weiteren Parameter angegeben, besteht das Standardverhalten im Öffnen des Posteingangs.</p></td>
</tr>
<tr class="even">
<td><p>exsvurl</p></td>
<td><p>Dieser Parameter muss angegeben werden, wenn die Live ID-Authentifizierung verwendet wird.</p>
<p>Wenn Sie &quot;exsvurl=1&quot; nicht angeben, werden während der Live ID-Authentifizierung sämtliche Parameter verworfen. Dieser Parameter kann nur auf Office 365-Postfächer angewendet werden.</p></td>
<td><p>https://&lt;server name&gt;/owa/?cmd=contents&amp;exsvurl=1</p></td>
</tr>
<tr class="odd">
<td><p>fpath (optional)</p></td>
<td><p>Dieser Teil der URL muss eventuell URL-codiert angegeben werden, damit er Firewalls passieren kann.</p>
<p>Bei Verwendung der URL-Codierung wird für ein Leerzeichen &quot;%20&quot; und für das Pfadtrennzeichen (/) &quot;%2f&quot; verwendet.</p>
<p>Die Ordnerhierarchie sollte mit dem Postfachstamm beginnen.</p>
<p>Dieser Ordnerpfad kann auf gewöhnliche Ordner oder Suchordner verweisen.</p></td>
<td><p>Verwenden Sie die folgende URL, um den Unterordner &quot;Projects&quot; im Posteingang zu öffnen:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/?cmd=contents&amp;fpath= inbox%2fprojects</p></td>
</tr>
<tr class="even">
<td><p>module (optional)</p></td>
<td><p>Mit diesem Parameter können Sie die Standardordner angeben, auch wenn sie deren lokalisierte Namen nicht kennen.</p></td>
<td><p>Bei den Werten für den Parameter &quot;module&quot; wird die Groß-/Kleinschreibung nicht berücksichtigt. Hierzu gehören die Folgenden:</p>
<ul>
<li><p>Inbox</p></li>
<li><p>Calendar</p></li>
<li><p>Teammailbox</p></li>
</ul>
<p>Mit der folgenden URL öffnen Sie den Kalender eines Postfachs ungeachtet seines lokalisierten Namens:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/?cmd=contents&amp;module=calendar</p></td>
</tr>
<tr class="odd">
<td><p>view (optional)</p></td>
<td><p>Mit diesem Parameter wird die Ansicht angegeben, in der der Ordner angezeigt werden soll.</p>
<p>Wird der Parameter nicht angegeben, gelten die folgenden Standardansichten:</p>
<ul>
<li><p>Kalender: Daily</p></li>
<li><p>Nachrichten: Messages</p></li>
</ul>

> [!NOTE]
> Die Zeichenfolgen für die Standardansichten werden automatisch URL-codiert.


<p>Die Standardsortierung für eine Ansicht ist die Art und Weise, wie der Ordner sortiert würde, wenn er im Outlook Web App-Client geöffnet würde.</p>
<p>Die Zeichenfolgen, mit denen die Ansichten identifiziert werden, werden nicht lokalisiert, und die Groß- und Kleinschreibung wird nicht berücksichtigt.</p></td>
<td><p>Die verfügbaren Ansichten sind je nach Ordnertyp unterschiedlich.</p>
<p>Kalenderansichten:</p>
<ul>
<li><p>Daily: Kalenderansicht nach Tagen</p></li>
<li><p>Weekly: Kalenderansicht nach Wochen</p></li>
<li><p>Monthly: Kalenderansicht nach Monaten</p></li>
</ul>
<p>Nachrichtenansichten:</p>
<ul>
<li><p>Messages: Nachrichtenansicht mit Standardsortierung</p></li>
<li><p>By%20Sender: Nachrichtenansicht sortiert nach Absender, beginnend mit Absendernamen mit dem Anfangsbuchstaben &quot;a&quot;</p></li>
<li><p>By%20Subject: Nachrichtenansicht sortiert nach Betreff, beginnend mit Betreffzeilen mit dem Anfangsbuchstaben &quot;a&quot;</p></li>
<li><p>By%20Conversation%20Topic: Unterhaltungsansicht, nicht verfügbar in der Light-Version von Outlook Web App</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>d, m, y (optional)</p></td>
<td><p>Gibt das Datum an, für das der Kalender angezeigt werden soll. Diese Parameter können in beliebiger Reihenfolge eingegeben und einzeln oder gemeinsam verwendet werden.</p>
<p>Wird einer dieser Parameter nicht angegeben, sind die Standardwerte der aktuelle Tag im aktuellen Monat und im aktuellen Jahr. Wenn heute also der 3. Mai 2016 wäre und Sie für den Monat eine &quot;9&quot; für September angeben würden, würde der 3. September 2016 angezeigt.</p></td>
<td><p>Folgende Werte sind für den Datumsparameter gültig:</p>
<p>d=[1-31]</p>
<p>m=[1-12]</p>
<p>y=[vierstelliges Jahr]</p>
<p>Wenn Sie das Datum 3. Mai 2016 in einem Kalender öffnen möchten, würden Sie die folgende URL verwenden: https://&lt;<em>server name</em>&gt;/owa/?cmd=content&amp;fpath=calendar&amp;view=daily&amp;d=3&amp;m=5&amp;y=2016</p></td>
</tr>
<tr class="odd">
<td><p>part (optional)</p></td>
<td><p>Gibt an, dass Outlook Web App ein kleineres Webpart anzeigen soll.</p></td>
<td><p>Wenn Sie Webparts für den Zugriff auf Outlook Web App-Inhalte verwenden, wird eine Benutzeroberfläche angezeigt, die kleiner ist als die vollständige Outlook Web App-Benutzeroberfläche. Mit dem Parameter &quot;part&quot; wird die Benutzeroberfläche noch kleiner dargestellt. Das nachstehende Beispiel zeigt die Aufgabenliste im kleinsten Webpartformat:</p>
<p>https://&lt;<em>server name</em>&gt;/owa/?cmd=contents&amp;part=1</p>
<p>Der Parameter &quot;part&quot; kann nicht auf das Modul &quot;calendar&quot; angewendet werden.</p></td>
</tr>
<tr class="even">
<td><p>FolderList</p></td>
<td><p>Dieser Parameter des Typs &quot;part&quot; enthält das Steuerelement für die Ordnerliste, mit dem Benutzer zwischen Unterordnern wechseln können. Der Parameter kann nur auf E-Mail-Ordner angewendet werden.</p></td>
<td><p>https://&lt;server name&gt;/owa/?cmd=contents&amp;folderlist=1</p></td>
</tr>
</tbody>
</table>


## Manuelles Eingeben von Outlook Web App-Webparts

Outlook Web App-Webparts können auch manuell in einen Webbrowser eingegeben werden. So kann ein Benutzer beispielsweise über eine Outlook Web App-Webpart-URL den Kalender eines anderen Benutzers öffnen.

Die folgenden Beispielen zeigen, wie Sie direkt auf häufige Outlook Web App-Ansichten zugreifen können:

  - **Posteingang:**  https://*\<server name\>*/owa/?cmd=contents\&module=inbox

  - **Calendar (today):** https://*\<server name\>*/owa/?cmd=contents\&module=calendar\&exsvurl=1

  - **Calendar (weekly):**  https://*\<server name\>*/owa/?cmd=contents\&module=calendar\&view=weekly\&exsvurl=1

  - **Calendar (monthly):**  https://*\<server name\>*/owa/?cmd=contents\&module=calendar\&view=monthly\&exsvurl=1

## Weitere Informationen

  - [Anpassen der Outlook Web App-Seiten für Anmeldung, Sprachauswahl und Fehler](customize-the-outlook-web-app-sign-in-language-selection-and-error-pages-exchange-2013-help.md)

  - [Erstellen eines Designs für Outlook Web App](create-a-theme-for-outlook-web-app-exchange-2013-help.md)

