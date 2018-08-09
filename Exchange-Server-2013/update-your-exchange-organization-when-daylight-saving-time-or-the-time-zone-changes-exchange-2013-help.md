---
title: 'Aktual. v. Exchange-Organisation bei Änd. der Sommerzeit oder der Zeitzone'
TOCTitle: Aktualisieren einer Exchange-Organisation bei Änderungen im Zusammenhang mit der Sommerzeit oder der Zeitzone
ms:assetid: 5b12615c-24cf-4f46-bf3c-2334dc734ef8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh530051(v=EXCHG.150)
ms:contentKeyID: 66452410
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren einer Exchange-Organisation bei Änderungen im Zusammenhang mit der Sommerzeit oder der Zeitzone

 

_**Gilt für:** Exchange Online, Exchange Server, Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Wenn in dem Land oder der Region, in dem bzw. der sich Ihre Organisation oder einige Ihrer Benutzer befinden, die Regelungen in Bezug auf die Sommerzeit oder die Zeitverschiebung der lokalen Zone zur UTC-Zeit (Coordinated Universal Time, koordinierte Weltzeit) geändert wird, müssen Sie möglicherweise Microsoft Windows, Microsoft Exchange, Microsoft Outlook oder andere Programme aktualisieren, um diesen Änderungen Rechnung zu tragen.

Weitere Informationen über Änderungen im Zusammenhang mit der Sommerzeit weltweit, einschließlich Links, finden Sie unter [Hilfe und Support zur Sommerzeit](https://go.microsoft.com/fwlink/p/?linkid=99640). Wenn Sie Software anderer Hersteller verwenden, sollten Sie auch deren Websites besuchen, um herauszufinden, ob für die betreffenden Programme zusätzliche Updates nötig sind.

Auch wenn sich Ihre Zeitzone nicht geändert hat, muss Ihr Computer in der Lage sein, genaue Datums- und Uhrzeitberechnungen für Ereignisse an anderen Orten in der Welt auszuführen, wenn Sie mit anderen Computer oder Benutzern weltweit kommunizieren.

Durch die zeitnahe Installation von Zeitzonenupdates wird die Anzahl von Besprechungen oder Terminen, die während des Übergangs von alten Uhrzeit- und Datumsangaben auf neue Uhrzeit- und Datumsangaben angesetzt werden, minimiert.

## Wie gehen Sie dazu vor?

## Schritt 1: Installieren des Windows-Sommerzeitupdates auf allen Client- und Desktopcomputern

Da das Office 365-Authentifizierungssystem bei Sommerzeit- oder Zeitzonenänderungen aktualisiert wird, müssen alle Office 365-Clientcomputer aktualisiert werden. Andernfalls können Verbindungsprobleme auftreten.

  - Stellen Sie sicher, dass das Windows-Sommerzeitupdate auf allen Client- und Desktopcomputern installiert ist. Weitere Informationen finden Sie unter [Konfigurieren der Sommerzeit für Microsoft Windows-Betriebssysteme](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=914387).

## Schritt 2: Installieren des Windows-Sommerzeitupdates auf allen Servern

1.  Aktualisieren Sie alle lokalen Server mit dem Windows-Sommerzeitupdate.

2.  Wenn Sie Office 365 ausführen, aktualisieren Sie alle Server, die mit dem Office 365-Authentifizierungssystem kommunizieren, z. B. DirSync- oder AD FS-Server. Diese Server müssen aktualisiert werden, um die Betriebsbereitschaft sicherzustellen.

**Hinweis:**  Befolgen Sie bei der Aktualisierung von Serverclustern unbedingt den regulären Prozess zur Clusteraktualisierung. Sie aktualisieren zunächst den passiven Server, führen anschließend ein Failover auf den passiven Server durch (der somit aktiv wird) und aktualisieren dann den bisher aktiven (und nun passiven) Server. Weitere Informationen zur Aktualisierung von Serverclustern und Serverclustern mit Hochverfügbarkeit finden Sie unter [Aktualisieren von Exchange-Serverclustern und Servern für hohe Verfügbarkeit](https://technet.microsoft.com/de-de/library/hh530052\(v=exchg.150\)) und [How to update Windows Server failover clusters](https://support.microsoft.com/en-us/kb/174799).

## Schritt 3: Aktualisieren von Exchange und Outlook auf Client- und Desktopcomputern (falls nötig)

1.  Falls Ihre Benutzer Outlook 2007 oder ältere Clients verwenden: Ermitteln Sie anhand der Tabelle unter dieser Anleitung, welche der Exchange- oder Outlook-Zeitzonentools ausgeführt werden müssen.

2.  Senden Sie an die Benutzer, die ihre Computer aktualisieren müssen, eine Nachricht mit einem Link zum entsprechenden Tool.

Der folgenden Tabelle können Sie entnehmen, wann Benutzer das [Exchange Calendar Update Tool](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=930879) und wann das [Time Zone Data Update Tool für Microsoft Office Outlook](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667) ausführen sollten. Ermitteln Sie, welche Version auf den Servern Ihrer Organisation ausgeführt wird und welche Clientprogramme Ihre Benutzer ausführen.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>Clientversion</strong></p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>Version in der Organisation</strong></p></td>
<td><p><strong>Outlook 2003 oder Outlook 2007</strong></p></td>
<td><p><strong>Outlook 2010</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Exchange 2003 lokal</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=930879">Exchange Calendar Tool</a> or</p>
<p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="even">
<td><p><strong>Exchange 2007 lokal</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=930879">Exchange Calendar Tool</a> or</p>
<p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="odd">
<td><p><strong>Exchange 2010 lokal</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=930879">Exchange Calendar Tool</a> or</p>
<p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="even">
<td><p><strong>Exchange 2013 lokal</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="odd">
<td><p><strong>BPOS-S (Exchange 2007)</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="even">
<td><p><strong>BPOS-D (Exchange 2010)</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a></p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="odd">
<td><p><strong>Office 365 (Exchange 2010)</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a> (nicht unterstützt von Outlook 2003)</p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="even">
<td><p><strong>Office 365 (Exchange 2013)</strong></p></td>
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=931667">Time Zone Data Update Tool für Microsoft Office Outlook</a> (nicht unterstützt von Outlook 2003)</p></td>
<td><p>Keine Aktion erforderlich</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

