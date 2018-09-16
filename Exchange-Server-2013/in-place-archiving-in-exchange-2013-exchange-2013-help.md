---
title: 'In-Situ-Archivierung in Exchange 2013: Exchange 2013 Help'
TOCTitle: In-Situ-Archivierung in Exchange 2013
ms:assetid: b5e4c0e9-0558-4b90-bc12-f67adbfb59ac
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979800(v=EXCHG.150)
ms:contentKeyID: 50476537
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# In-Situ-Archivierung in Exchange 2013

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die *Compliance-Archivierung* unterstützt Sie dabei, die Kontrolle über die Messagingdaten Ihrer Organisation zurückzuerhalten, da keine PST-Dateien mehr benötigt werden. Außerdem gestattet sie es Benutzern, Nachrichten in einem *Archivpostfach* zu speichern, auf das in MicrosoftOutlook 2010 und Microsoft OfficeOutlook Web App zugegriffen werden kann.

In Microsoft Exchange Server 2013 bietet die Compliance-Archivierung den Benutzern einen alternativen Speicherplatz zum Speichern von älteren Messagingdaten. Ein Compliance-Archiv ist ein zusätzliches Postfach (auch als Archivpostfach bezeichnet), das für einen Postfachbenutzer aktiviert ist. Benutzer von Outlook 2007 und höher sowie von Outlook Web App haben einen nahtlosen Zugriff auf ihr Archivpostfach. Bei Verwendung einer dieser Clientanwendungen können die Benutzer ein Archivpostfach anzeigen und Nachrichten zwischen ihrem primären Postfach und dem Archiv kopieren oder verschieben. Die Compliance-Archivierung bietet Benutzern eine konsistente Ansicht ihrer Messagingdaten und lässt den Benutzeraufwand für die Verwaltung von PST-Dateien überflüssig werden.

Sie können das Archiv eines Benutzers in der gleichen Postfachdatenbank wie das primäre Postfach des Benutzers, in einer anderen Postfachdatenbank auf dem gleichen Postfachserver oder in einer Postfachdatenbank auf einem anderen Postfachserver am gleichen Active Directory-Standort bereitstellen. In Exchange 2010-Hybridbereitstellungen können Sie auch ein cloudbasiertes Archiv für Postfächer bereitstellen, die sich auf Ihren lokalen Postfachservern befinden.

**Inhalt**

Messagingdaten und PST-Dateien

Clientzugriff auf Archivpostfächer

Stellvertretungszugriff

Verschieben von Nachrichten in das Archivpostfach

Archiv- und Aufbewahrungsrichtlinien

Standard-MRM-Richtlinie

Archivierungskontingente

Compliance-Archive und weitere Exchange-Features

Verwalten von Archivpostfächern

## Messagingdaten und PST-Dateien

Outlook verwendet PST-Dateien, um Daten lokal auf den Computern oder Netzwerkfreigaben von Benutzern zu speichern. Im Gegensatz zu Offlinespeicherdateien (OST-Dateien, die von Outlook im Exchange-Cache-Modus zum Speichern einer Kopie des Postfachs für den Offlinezugriff verwendet werden) werden PST-Dateien nicht mit dem Exchange-Postfach des Benutzers synchronisiert. Wenn ein Benutzer Nachrichten in eine PST-Datei verschiebt, werden diese Nachrichten aus dem Postfach entfernt.

Die Verwendung von PST-Dateien zum Verwalten von Messagingdaten kann zu folgenden Problemen führen:

  - **Nicht verwaltete Dateien**   Im Allgemeinen werden PST-Dateien von Benutzern erstellt und befinden sich auf deren Computern oder Netzwerkfreigaben. Sie werden nicht von Ihrer Organisation verwaltet. Daher können Benutzer verschiedene PST-Dateien erstellen, die dieselben oder andere Nachrichten enthalten, und diese ohne organisatorische Steuerung an anderen Speicherorten speichern.

  - **Erhöhte Discoverykosten**   Rechtsstreitigkeiten und andere geschäftliche oder gesetzliche Bestimmungen führen gelegentlich zu Discoveryanforderungen. Die Suche nach Messagingdaten, die sich in PST-Dateien auf den Computern der Benutzer befinden, kann sich als kostspieliger manueller Aufwand erweisen. Da sich die Nachverfolgung nicht verwalteter PST-Dateien als schwierig erweisen kann, sind PST-Daten in vielen Fällen möglicherweise unauffindbar. Dies kann für Ihre Organisation unter Umständen rechtliche und finanzielle Risiken nach sich ziehen.

  - **Fehlende Möglichkeit zum Anwenden von Nachrichtenaufbewahrungsrichtlinien**   Aufbewahrungsrichtlinien für Nachrichten können nicht auf Nachrichten angewendet werden, die sich in PST-Dateien befinden. Je nach geschäftlichen oder anwendbaren Bestimmungen entspricht Ihre Organisation daher möglicherweise nicht den geltenden Vorschriften.

  - **Risiko des Datendiebstahls**   Die in PST-Dateien gespeicherten Messagingdaten sind für Datendiebstähle anfällig. PST-Dateien werden z. B. häufig auf portablen Geräten wie Laptops und Wechsellaufwerken sowie auf portablen Medien (USB-Laufwerken, CDs und DVDs) gespeichert.

  - **Bruchstückhafte Ansicht der Nachrichtendaten**   Benutzer, die Informationen in PST-Dateien speichern, erhalten keine einheitliche Ansicht ihrer Daten. Die in PST-Dateien gespeicherten Nachrichten sind im Allgemeinen nur auf dem Computer verfügbar, auf dem sich die PST-Dateien befinden. Wenn Benutzer mithilfe von Outlook Web App oder Outlook auf ihre Postfächer auf einem anderen Computer zugreifen, sind die in ihren PST-Dateien gespeicherten Nachrichten daher nicht verfügbar.

## Clientzugriff auf Archivpostfächer

In der folgenden Tabelle sind die Clientanwendungen aufgeführt, die für den Zugriff auf Archivpostfächer verwendet werden können.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Zugriff auf Archivpostfach</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook-2013, Outlook 2010, Outlook 2007 und Outlook Web App</p></td>
<td><p>Ja. Benutzer von Outlook 2013, Outlook 2010, Outlook 2007 oder Outlook Web App können Elemente aus ihrem primären Postfach in ihr Archivpostfach kopieren oder verschieben und Elemente auch mithilfe von Aufbewahrungsrichtlinien in das Archiv verschieben.</p>

> [!NOTE]
> Benutzer von Outlook 2010 und höher oder Outlook 2007 können ebenfalls Elemente aus PST-Dateien in ihr Archivpostfach kopieren oder verschieben. Outlook 2007-Benutzer benötigen das kumulative Office 2007-Update von Februar 2011. Es gibt einige Unterschiede bei der Archivunterstützung zwischen Outlook 2010 und höher sowie Outlook 2007. Weitere Informationen hierzu finden Sie im Exchange Team Blog-Artikel <A href="https://blogs.technet.com/b/exchange/archive/2010/12/20/3411710.aspx">Ja Virginia, Exchange 2010-Archive werden in Outlook 2007 unterstützt</A>.


</td>
</tr>
<tr class="even">
<td><p>Exchange ActiveSync</p></td>
<td><p>Nein</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> "Compliance-Archiv" ist eine Premiumfunktion, für die eine Exchange Enterprise-Clientzugriffslizenz (CAL) erforderlich ist. Ausführliche Informationen zur Lizenzierung von Exchange finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=237292">Exchange-Server-Lizenzierung</A>. Ausführliche Informationen zu den Versionen von Outlook, die für den Zugriff auf ein Archivpostfach erforderlich sind, finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=237276">Lizenzierungsanforderungen für persönliche Archive und Aufbewahrungsrichtlinien</A>.



Outlook erstellt keine lokale Kopie des Archivpostfachs auf dem Computer eines Benutzers, auch wenn dieser für die Verwendung des Exchange-Cachemodus konfiguriert ist. Benutzer können nur im Onlinemodus auf ein Archivpostfach zugreifen.

## Stellvertretungszugriff

Beim *Stellvertretungszugriff* wird einem Benutzer oder einer Gruppe von Benutzern der Zugriff auf das Postfach eines anderen Benutzers gewährt. Es gibt verschiedene Szenarien zum Bereitstellen des Stellvertretungszugriffs. Dazu zählen:

  - Bereitstellen des Zugriffs für mindestens einen Benutzer auf das Postfach eines Benutzers, der nicht länger im Unternehmen angestellt ist. In diesem Fall gehören zu den Benutzern mit Stellvertretungszugriff z. B. der Vorgesetzte oder Abteilungsleiter des ehemaligen Benutzers bzw. ein anderer Benutzer, der die Aufgaben des ehemaligen Benutzers übernimmt.

  - Bereitstellen des Zugriffs auf ein freigegebenes Postfach für mindestens einen Benutzer.

  - Bereitstellen des Zugriffs auf die Postfächer von Führungskräften für deren Assistenten.

Wenn Sie in Exchange 2013 die Berechtigungen für den Vollzugriff auf ein Postfach erteilen, kann die Stellvertretung, der die Berechtigungen zugewiesen wurden, auch auf das Archiv des Benutzers zugreifen. Stellvertretungen müssen Outlook verwenden, um auf das Postfach zuzugreifen. Außerdem müssen sie für die AutoErmittlung eine Verbindung mit einem Clientzugriffsserver mit Exchange 2010 SP1 oder höher herstellen. Die AutoErmittlung ist ein Exchange-Dienst, der Konfigurationseinstellungen für die automatische Konfiguration von Outlook-Clients bereitstellt. Wenn Stellvertretungen mithilfe von Outlook auf ein Exchange 2013-Postfach zugreifen, kann sowohl das primäre Postfach als auch das Archiv, auf die sie zugreifen können, in Outlook angezeigt werden.

## Verschieben von Nachrichten in das Archivpostfach

Es gibt verschiedene Möglichkeiten, um Nachrichten in Archivpostfächer zu verschieben:

  - **Nachrichten manuell verschieben oder kopieren**   Postfachbenutzer können Nachrichten manuell aus ihrem primären Postfach oder eine PST-Datei in ihr Archivpostfach verschieben oder kopieren. Das Archivpostfach wird in Outlook und Outlook Web App als weiteres Postfach oder als PST-Datei angezeigt.

  - **Nachrichten mithilfe von Posteingangsregeln verschieben oder kopieren**   Postfachbenutzer können in Outlook oder Outlook Web App Posteingangsregeln erstellen, um Nachrichten automatisch in ihr Archivpostfach zu verschieben. Weitere Informationen finden Sie unter [Informationen zu Posteingangsregeln](http://help.outlook.com/de-de/140/bb899620.aspx).

  - **Nachrichten mithilfe von Aufbewahrungsrichtlinien verschieben**   Sie können Nachrichten mithilfe von Aufbewahrungsrichtlinien automatisch in das Archiv verschieben. Benutzer können auch ein persönliches Tag anwenden, um Nachrichten in das Archiv zu verschieben. Weitere Informationen zu Archiv- und Aufbewahrungsrichtlinien finden Sie unter Archiv- und Aufbewahrungsrichtlinien weiter unten in diesem Thema.
    

    > [!NOTE]
    > Persönliche Tags sind nur in Outlook Web App und Outlook 2010 und höher verfügbar.



  - **Nachrichten aus PST-Dateien importieren**   In Exchange 2013 können Sie Nachrichten mithilfe einer Postfachimportanforderung aus einer PST-Datei in das Archiv- oder primäre Postfach des Benutzers importieren. Weitere Informationen finden Sie unter [Import- und Exportanforderungen für Postfächer](mailbox-import-and-export-requests-exchange-2013-help.md). Sie können auch das Tool "PST Capture" verwenden, um auf Computern in Ihrer Organisation nach PST-Dateien zu suchen und Daten aus PST-Dateien in Archive von Benutzern zu importieren.

## Archiv- und Aufbewahrungsrichtlinien

In Exchange 2013 können Sie Archivrichtlinien auf ein Postfach anwenden, um Nachrichten automatisch nach einem angegebenen Zeitraum aus dem primären Postfach eines Benutzers in das Archivpostfach zu verschieben. Archivrichtlinien werden durch Erstellen von Aufbewahrungstags implementiert, die die Aufbewahrungsaktion **In Archiv verschieben** verwenden.

Nachrichten werden in einen Ordner im Archivpostfach verschoben, dessen Name mit dem Namen des Quellordners im primären Postfach übereinstimmt. Wenn im Archivpostfach ein Ordner mit demselben Namen vorhanden ist, wird dieser erstellt, sobald eine Nachricht vom Assistenten für verwaltete Ordner verschoben wird. Wenn im Archivpostfach dieselbe Ordnerhierarchie erstellt wird, können Benutzer Nachrichten einfach finden.

Weitere Informationen zu Aufbewahrungsrichtlinien, Aufbewahrungstags und zur Aufbewahrungsaktion **In Archiv verschieben** finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](https://technet.microsoft.com/de-de/library/Dd297955(v=EXCHG.150)).

## Standard-MRM-Richtlinie

Exchange 2013-Setup erstellt die Standardarchiv- und -aufbewahrungsrichtlinie **MRM-Standardrichtlinie**. Diese Richtlinie enthält Aufbewahrungstags, die über die Aktion **In Archiv verschieben** verfügen, wie in der folgenden Tabelle veranschaulicht.


> [!NOTE]
> In Exchange 2010 hat die von Exchange-Setup erstellte Standardarchiv- und -aufbewahrungsrichtlinie den Namen <STRONG>Standardarchiv- und -aufbewahrungsrichtlinie</STRONG>.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Aufbewahrungstagname</th>
<th>Tagtyp</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Standard, 2 Jahre, in Archiv verschieben</strong></p></td>
<td><p>Standard (DPT)</p></td>
<td><p>Nachrichten werden nach zwei Jahren automatisch in das Archivpostfach verschoben. Gilt für Elemente im gesamten Postfach, auf die kein Aufbewahrungstag explizit angewendet oder vom Ordner geerbt wurde.</p></td>
</tr>
<tr class="even">
<td><p><strong>Persönlich, 1 Jahre, in Archiv verschieben</strong></p></td>
<td><p>Persönlich</p></td>
<td><p>Nachrichten werden nach einem Jahr automatisch in das Archivpostfach verschoben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Persönlich, 5 Jahre, in Archiv verschieben</strong></p></td>
<td><p>Persönlich</p></td>
<td><p>Nachrichten werden nach fünf Jahren automatisch in das Archivpostfach verschoben.</p></td>
</tr>
<tr class="even">
<td><p><strong>Persönlich, nie in Archiv verschieben</strong></p></td>
<td><p>Persönlich</p></td>
<td><p>Nachrichten werden niemals in das Archivpostfach verschoben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Wiederherstellbare Elemente, 14 Tage, in Archiv verschieben</strong></p></td>
<td><p>Ordner &quot;Wiederherstellbare Elemente&quot;</p></td>
<td><p>Nachrichten werden aus dem Ordner &quot;Wiederherstellbare Elemente&quot; des primären Postfachs in den Ordner &quot;Wiederherstellbare Elemente&quot; des Archivpostfachs des Benutzers verschoben. Benutzer, die gelöschte Elemente im Archiv wiederherstellen möchten, müssen die Funktion &quot;Gelöschte Elemente wiederherstellen&quot; für das Archivpostfach verwenden.</p></td>
</tr>
</tbody>
</table>


Wenn Sie ein Compliance-Archiv für einen Postfachbenutzer aktivieren und dem Postfach nicht bereits eine Aufbewahrungsrichtlinie zugewiesen ist, wird automatisch die Standardarchiv- und -aufbewahrungsrichtlinie zugewiesen. Nachdem der Assistent für verwaltete Ordner das Postfach verarbeitet hat, werden diese Tags dem Benutzer zur Verfügung gestellt, der dann Ordner oder Nachrichten markieren kann, die in das Archivpostfach verschoben werden sollen. Standardmäßig werden E-Mail-Nachrichten aus dem gesamten Postfach nach zwei Jahren verschoben.

Es wird empfohlen, dass Sie Ihre Benutzer vor der Bereitstellung der Archivpostfächer über die Archivrichtlinien informieren, die auf ihr Postfach angewendet werden, und ihnen anschließende Schulungen oder Dokumentationen bereitstellen, um ihren Anforderungen zu entsprechen. Das sollte Details zu den folgenden Themen umfassen:

  - Innerhalb des Archivs verfügbare Funktionalität, die Standardarchiv- und -aufbewahrungsrichtlinien.

  - Informationen dazu, wann Nachrichten automatisch in das Archiv verschoben werden.

  - Informationen zur Ordnerhierarchie, die im Archivpostfach erstellt wurde.

  - Informationen zum Anwenden von persönlichen Tags (werden in Outlook und Outlook Web App im Menü "Archivrichtlinie" angezeigt).


> [!NOTE]
> Wenn Sie eine Aufbewahrungsrichtlinie auf Benutzer anwenden, die über ein Archivpostfach verfügen, wird die Standard-MRM-Richtlinie durch die Aufbewahrungsrichtlinie ersetzt. Sie können mithilfe der Aktion <STRONG>In Archiv verschieben</STRONG> ein oder mehrere Aufbewahrungstags erstellen und die Tags dann mit der Aufbewahrungsrichtlinie verknüpfen. Sie können auch die <STRONG>In Archiv verschieben</STRONG>-Standardtags (die von Setup erstellt und mit der Standard-MRM-Richtlinie verknüpft werden) zu jeder von Ihnen erstellten Aufbewahrungsrichtlinie hinzufügen.



Informationen zur Einhaltung von Vorschriften und der Archivierung in Outlook 2010 und höher finden Sie unter [Planen der Einhaltung von Vorschriften und der Archivierung in Outlook 2010](https://go.microsoft.com/fwlink/?linkid=210902).

## Archivierungskontingente

Archivpostfächer sind dazu gedacht, dass Benutzer ältere Messagingdaten außerhalb ihres primären Postfachs speichern können. Benutzer verwenden aufgrund geringer Kontingente für die Postfachspeicherung und der Einschränkungen beim Überschreiten dieser Kontingente häufig PST-Dateien. Benutzer können z. B. am Senden von Nachrichten gehindert werden, wenn die Größe ihres Postfachs das *Kontingent für Senden verbieten* übersteigt. Ähnlich können Benutzer am Senden und Empfangen von Nachrichten gehindert werden, wenn die Größe ihres Postfachs das *Kontingent für das Sende- und Empfangsverbot* übersteigt.

Sie können ein Archivpostfach mit Speichergrenzwerten bereitstellen, die den Anforderungen der Benutzer entsprechen, damit keine PST-Dateien mehr benötigt werden. Sie möchten jedoch möglicherweise die Kontrolle über die Speicherkontingente und über das Wachstum der Archivpostfächer behalten, um bei der Überwachung der Kosten und der Erweiterung zu helfen.

Zu diesem Zweck können Sie Archivpostfächer mit einem *Kontingentgrenzwert für Archive* und einem *Archivierungskontingent* konfigurieren. Wenn die Größe eines Archivpostfachs den Kontingentgrenzwert für Archive überschreitet, wird im Anwendungsereignisprotokoll ein Warnereignis protokolliert. Wenn ein Archivpostfach das angegebene Archivierungskontingent überschreitet, werden Nachrichten nicht mehr in das Archiv verschoben, ein Warnereignis im Anwendungsereignisprotokoll protokolliert und der Postfachbenutzer erhält eine Kontingentmeldung. In Exchange 2013 ist der Kontingentgrenzwert für Archive standardmäßig auf 45 GB (Gigabyte) und das Archivierungskontingent auf 50 GB festgelegt.

In der folgenden Tabelle sind die protokollierten Ereignisse und Warnmeldungen aufgeführt, die beim Erreichen des Kontingentgrenzwerts für Archive und des Archivierungskontingents gesendet werden.


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Kontingent</th>
<th>Ereignis-ID</th>
<th>Typ</th>
<th>Quelle</th>
<th>Kategorie</th>
<th>Meldung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kontingentgrenzwert für Archive</p></td>
<td><p>10022</p></td>
<td><p>Warnung</p></td>
<td><p>MSExchangeMailboxAssistants</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Das Archivpostfach '&lt;Anzeigename&gt;:&lt;GUID&gt;:&lt;Postfachdatenbank&gt;:&lt;Server-FQDN&gt;' hat den Kontingentgrenzwert für Archive '&lt;Kontingentgrenzwert für Archive&gt;' überschritten. Die Größe für das Archivpostfach beträgt '&lt;Größe&gt;' Byte.</p></td>
</tr>
<tr class="even">
<td><p>Archivierungskontingent</p></td>
<td><p>8537</p></td>
<td><p>Warnung</p></td>
<td><p>MSExchangeIS</p></td>
<td><p>Allgemein</p></td>
<td><p>Das Archivpostfach für &lt;Legacy-DN&gt; hat die maximale Größe für das Archivpostfach überschritten. Sie können keine Elemente in das Archivpostfach kopieren oder verschieben. Alle Aufbewahrungsaktionen für Nachrichten, durch die Elemente in das Archivpostfach verschoben werden, schlagen fehl, und das primäre Postfach enthält möglicherweise Elemente mit abgelaufenen Aufbewahrungstags, solange das Archivpostfach innerhalb des maximalen Größengrenzwerts liegt. Der Postfachbesitzer sollte über diesen Zustand des Archivpostfachs informiert werden.</p></td>
</tr>
</tbody>
</table>


## Compliance-Archive und weitere Exchange-Features

In diesem Abschnitt wird die Funktionalität zwischen Compliance-Archiven und verschiedenen Exchange-Features erläutert:

  - **Exchange-Suche   **Die Möglichkeit zur schnellen Suche nach Nachrichten ist bei Archivpostfächern noch wichtiger. Bei der Exchange-Suche gibt es keinen Unterschied zwischen dem primären und dem Archivpostfach. Der Inhalt in beiden Postfächern wird indiziert. Da das Archivpostfach auf dem Computer eines Benutzers nicht zwischengespeichert wird (auch nicht, wenn mit Outlook im Exchange-Cache-Modus gearbeitet wird), werden die Suchergebnisse für das Archiv immer von der Exchange-Suche bereitgestellt. Wenn Sie das gesamte Postfach in Outlook 2010 und höher sowie in Outlook Web App durchsuchen, umfassen die Suchergebnisse das primäre und das Archivpostfach des Benutzers.

  - **Compliance-eDiscovery**   Wenn ein Discovery-Manager eine Compliance-eDiscovery-Suche ausführt, werden auch die Archivpostfächer der Benutzer durchsucht. Es gibt keine Option, Archivpostfächer auszuschließen, wenn in der Exchange-Verwaltungskonsole eine Discoverysuche erstellt wird. Wenn Sie mit der Exchange-Verwaltungsshell eine Discoverysuche erstellen, können Sie das Archiv mithilfe der Option *DoNotIncludeArchive* ausschließen. Weitere Informationen finden Sie unter [New-MailboxSearch](https://technet.microsoft.com/de-de/library/dd298064\(v=exchg.150\)). Weitere Informationen finden Sie unter [Compliance-eDiscovery](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery).
    

    > [!IMPORTANT]
    > Sie können Compliance-eDiscovery nicht dazu verwenden, ein getrenntes Postfach zu durchsuchen.



  - **Compliance-Archiv und Beweissicherungsverfahren**   Wenn Sie für ein Postfach ein Compliance-Archiv oder das Beweissicherungsverfahren festlegen, gilt diese Archivierung sowohl für das primäre als auch das Archivpostfach. Weitere Informationen zu Compliance-Archiv und Beweissicherungsverfahren finden Sie unter [In-Place Hold and Litigation Hold](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-and-litigation-holds).

  - **Ordner für wiederherstellbare Elemente   **Das Archivpostfach enthält einen eigenen Ordner für wiederherstellbare Elemente und unterliegt denselben Kontingenten wie der Ordner "Wiederherstellbare Elemente" des primären Postfachs. Weitere Informationen zu wiederherstellbaren Elementen finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

  - **Archivieren von Lync-Inhalten in Exchange**   Sie können Chatunterhaltungen und zu freigegebenen Onlinebesprechungen gehörige Dokumente im primären Postfach des Benutzers archivieren. Das Postfach muss sich auf einem Exchange 2013-Postfachserver befinden, und in Ihrer Organisation muss Microsoft Lync 2013 bereitgestellt werden. Weitere Informationen finden Sie unter [Integration in SharePoint und Lync](integration-with-sharepoint-and-lync-exchange-2013-help.md).

## Verwalten von Archivpostfächern

In Exchange 2013 ist das Erstellen und Verwalten von Archivpostfächern in die allgemeinen Aufgaben zur Postfachverwaltung integriert, wie z. B.:

  - **Erstellen eines Archivpostfachs**   Sie können ein Archivpostfach beim Erstellen eines Postfachs erstellen oder ein Archivpostfach für ein vorhandenes Postfach aktivieren. Weitere Informationen finden Sie unter [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md).

  - **Verschieben eines Archivpostfachs**   Sie können das Archivpostfach eines Benutzers in eine andere Postfachdatenbank auf dem gleichen Postfachserver oder auf einem anderen Server verschieben (unabhängig vom primären Postfach). Sie müssen eine Verschiebungsanforderung für ein Postfach erstellen, um das Archivpostfach eines Benutzers zu verschieben. Weitere Informationen finden Sie unter [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Das Auffinden des Postfachs und Archivs eines Benutzers in verschiedenen Versionen von Exchange Server wird nicht unterstützt.



  - **Deaktivieren eines Archivpostfachs**   Möglicherweise müssen Sie das Archivpostfach eines Benutzers deaktivieren, weil Sie eine Problembehandlung vornehmen oder das primäre Postfach in eine Exchange-Version verschieben möchten, die keine Compliance-Archivierung unterstützt. Das Deaktivieren eines Archivs ist mit dem Deaktivieren eines primären Postfachs vergleichbar. Weitere Informationen finden Sie unter [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md). In lokalen Bereitstellungen bleibt ein deaktiviertes Archivpostfach in der Postfachdatenbank erhalten, bis der Aufbewahrungszeitraum für gelöschte Postfächer für diese Datenbank erreicht wird. Während dieses Zeitraums können Sie das Archiv erneut mit einem Postfachbenutzer verbinden. Wenn der Aufbewahrungszeitraum für das gelöschte Postfach erreicht ist, wird das getrennte Archivpostfach dauerhaft aus der Postfachdatenbank gelöscht.

  - **Abrufen von Postfach- und Ordnerstatistiken**   Sie können Statistiken für das Postfach und den Postfachordner für das Archivpostfach eines Benutzers mithilfe der Option *Archive* über die Cmdlets [Get-MailboxStatistics](https://technet.microsoft.com/de-de/library/bb124612\(v=exchg.150\)) und [Get-MailboxFolderStatistics](https://technet.microsoft.com/de-de/library/aa996762\(v=exchg.150\)) abrufen.

  - **Archivkonnektivität testen**   In Exchange 2013 können Sie mit dem Cmdlet [Test-ArchiveConnectivity](https://technet.microsoft.com/de-de/library/hh529914\(v=exchg.150\)) die Konnektivität mit dem jeweils angegebenen lokalen oder cloudbasierten Archiv des Benutzer testen.

