---
title: 'Nicht durchsuchbare Elemente in Exchange eDiscovery: Exchange 2013 Help'
TOCTitle: Nicht durchsuchbare Elemente in Exchange eDiscovery
ms:assetid: 32550081-9af9-474b-ae7b-28f1e68cad41
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn602498(v=EXCHG.150)
ms:contentKeyID: 61071985
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nicht durchsuchbare Elemente in Exchange eDiscovery

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Compliance-eDiscover für Exchange Server 2013 und Exchange Online sind nicht durchsuchbare Elemente Postfachelemente, die von der Exchange-Suche nicht indiziert werden können oder die nur teilweise indiziert wurden. Ein nicht durchsuchbares Element enthält in der Regel eine Datei, die nicht indiziert werden kann, als Anlage zu einer E-Mail-Nachricht. Dies sind einige Gründe, warum Dateien nicht für die Suche indiziert werden können und als nicht durchsuchbares Element zurückgegeben werden, wenn sie an eine E-Mail-Nachricht angehängt sind.

  - Der Dateityp wird nicht für die Indizierung unterstützt, da ein Suchfilter (auch als *IFilter* bezeichnet) zur Indizierung des Dateiformats nicht installiert ist.

  - Der Dateityp ist für die Indizierung deaktiviert.

  - Der Dateityp wird für die Indizierung unterstützt, aber es ist ein Indizierungsfehler für eine bestimmte Datei aufgetreten.

  - Eine Datei wurde mit Nicht-Microsoft-Technologien verschlüsselt.

  - Eine Datei ist kennwortgeschützt.

Für eine erfolgreiche eDiscovery-Suche muss Ihre Organisation nicht durchsuchbare Elemente möglicherweise überprüfen. Wenn Sie Compliance-eDiscovery-Suchergebnisse in ein Discoverypostfach kopieren oder Suchergebnisse in eine PST-Datei exportieren, können Sie angeben, ob die nicht durchsuchbaren Elemente eingeschlossen werden sollen.

## Nicht unterstützte Dateitypen für die Suche

Bestimmte Dateitypen wie Bitmap- oder MP3-Dateien enthalten keinen zu indizierenden Inhalt. Daher führt die Exchange-Suche keine Volltextindizierung für diese Dateitypen durch. Diese Dateitypen werden als nicht unterstützte Dateitypen betrachtet. Es gibt außerdem Dateitypen, für die Volltextindizierung deaktiviert wurde (entweder standardmäßig oder durch den Administrator). Nicht unterstützte und deaktivierte Dateitypen werden in eDiscovery-Suchen als nicht durchsuchbare Elemente betrachtet. Diese Dateitypen, die in der Regel an E-Mail-Nachrichten angehängt sind, sind im Ergebnissatz enthalten, wenn Sie nicht durchsuchbare Elemente beim Kopieren oder Exportieren von Suchergebnissen einschließen. Eine Liste von unterstützten und deaktivierten Dateiformaten finden Sie unter [Von der Exchange-Suche indizierte Dateiformate](file-formats-indexed-by-exchange-search-exchange-2013-help.md). In Exchange Server 2013 können Administratoren die Indizierung für ein unterstütztes Dateiformat unter Verwendung des Cmdlets [Set-SearchDocumentFormat](https://technet.microsoft.com/de-de/library/jj873756\(v=exchg.150\)) deaktivieren. Dieses Cmdlet ist in Exchange Online nicht verfügbar.

Zur Identifizierung von nicht durchsuchbaren Elementen in einem bestimmten Postfach können Sie das Cmdlet [Get-FailedContentIndexDocuments](https://technet.microsoft.com/de-de/library/dd351154\(v=exchg.150\)) ausführen, um eine Liste der Elemente zu erhalten, die kopiert oder exportiert würden, wenn Sie nicht durchsuchbare Elemente einschließen.

## Nachrichten mit nicht unterstützten Dateitypen, die in den Suchergebnissen zurückgegeben werden

Nicht jede Nachricht mit einer nicht unterstützten Dateianlage wird automatisch als nicht durchsuchbares Element zurückgegeben. Das liegt daran, dass andere Dateieigenschaften wie der Dateiname indiziert werden und für die Suche zur Verfügung stehen. Beispielsweise gibt die Suche nach dem Schlüsselwort "Finanz" Nachrichten mit einem nicht unterstützten Dateianhang zurück, wenn dieses Schlüsselwort im Dateinamen enthalten ist. Wenn das Schlüsselwort jedoch nur im Text der angehängten Datei erscheint, wird die Nachricht als nicht durchsuchbares Element zurückgegeben.

Genauso werden Nachrichten mit nicht unterstützten Dateianhängen in die Suchergebnisse eingeschlossen, wenn andere Eigenschaften eines Postfachelements, die indizierbar und durchsuchbar sind, den Suchkriterien entsprechen. Zu den Nachrichteneigenschaften, die für die Suche indiziert werden, gehören Sende- und Empfangsdatum, Absender und Empfänger, Dateiname von Anlagen sowie der Nachrichtentext. Obwohl also die Nachrichtenanlage nicht durchsuchbar ist, wird die Nachricht in die regulären Suchergebnisse aufgenommen, wenn der Wert anderer Nachrichteneigenschaften den Suchkriterien entspricht. Tatsächlich sind also Nachrichten mit nicht durchsuchbaren Anlagen häufig in den regulären Suchergebnissen enthalten.

Eine Liste der indizierbaren Eigenschaften von E-Mail-Nachrichten finden Sie unter [Von der Exchange-Suche indizierte Nachrichteneigenschaften](message-properties-indexed-by-exchange-search-exchange-2013-help.md).

## Einschließen von nicht durchsuchbaren Elementen in die Suchergebnisse

Möglicherweise ist Ihre Organisation verpflichtet, eine zusätzliche Identifikation und Verarbeitung von nicht durchsuchbaren Elementen durchzuführen, um zu bestimmen, was sie sind, was sie enthalten und ob sie relevant sind. Um nicht durchsuchbare Elemente in die eDiscovery-Suchergebnisse einzuschließen, können Sie die Option für nicht durchsuchbare Elemente verwenden, wenn Sie Suchergebnisse kopieren oder exportieren. Wenn Sie Compliance-eDiscovery-Suchergebnisse in Exchange oder Exchange Online verwenden und nicht durchsuchbare Elemente einschließen möchten, aktivieren Sie die Option **Nicht durchsuchbare Elemente einschließen**, um die Suchergebnisse in ein Discoverypostfach zu kopieren oder sie in eine PST-Datei zu exportieren. Wenn Sie das eDiscovery Center in SharePoint oder SharePoint Online verwenden und nicht durchsuchbare Elemente einschließen möchten, aktivieren Sie die Option für Elemente, die verschlüsselt sind oder ein unbekanntes Format aufweisen.

Beachten Sie beim Kopieren oder Exportieren von nicht durchsuchbaren Elementen Folgendes:

  - Wenn Sie nicht durchsuchbare Elemente in ein Discoverypostfach kopieren, werden die nicht durchsuchbaren Elemente in einen separaten Ordner namens **Nicht durchsuchbar** kopiert, der sich unterhalb des Ordners mit den Suchergebnissen befindet. Wenn Sie Suchergebnisse exportieren und nicht durchsuchbare Elemente einschließen, werden die nicht durchsuchbaren Elemente in eine separate PST-Datei exportiert.

  - Falls Sie die nicht durchsuchbaren Elemente in die Suchergebnisse einschließen, werden alle nicht durchsuchbaren Elemente in den durchsuchten Postfächern zurückgegeben, unabhängig von den Suchkriterien.

  - Wenn Sie alle Postfachelemente in die Suchergebnisse einschließen möchten, oder wenn eine Suchabfrage keine Schlüsselwörter enthält bzw. nur einen Datumsbereich angibt, werden die nicht durchsuchbaren Elemente möglicherweise nicht in den Ordner **Nicht durchsuchbar** kopiert, wenn Sie die Option zum Einschließen von nicht durchsuchbaren Elementen aktivieren. Das liegt daran, dass alle Elemente, auch die nicht durchsuchbaren, automatisch in die regulären Suchergebnisse einbezogen werden.

  - Wie bereits erwähnt, kann eine Schlüsselwortsuche Ergebnisse zurückgeben, wenn das Schlüsselwort in den Eigenschaften oder Metadaten einer Nachricht mit einer nicht durchsuchbaren Dateianlage erscheint, da die Nachrichteneigenschaften und -metadaten indiziert werden. In diesem Fall werden zwei Kopien desselben Postfachelements in die Suchergebnisse eingeschlossen. Um diese Dopplung zu vermeiden und nur eine Kopie des Elements in den regulären Suchergebnissen anzuzeigen, können Sie beim Kopieren oder Exportieren der Suchergebnisse die Option **Entfernung von Duplikaten aktivieren** verwenden.

  - Das Einschließen von nicht durchsuchbaren Elementen in die Suchergebnisse kann sich auch auf die geschätzte Anzahl der angezeigten Suchergebnisse auswirken. Wenn Sie beim Kopieren der Suchergebnisse nicht durchsuchbare Elemente einschließen, enthalten die geschätzte Gesamtanzahl und die geschätzte Gesamtgröße auch die nicht durchsuchbaren Elemente.

Weitere Informationen zum Einschließen von nicht durchsuchbaren Elementen in Suchergebnissen finden Sie unter:

  - [Erstellen einer Compliance-eDiscovery-Suche](create-an-in-place-ediscovery-search-exchange-2013-help.md)

  - [Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](export-ediscovery-search-results-to-a-pst-file-exchange-2013-help.md)

  - [SharePoint: Exportieren von eDiscovery-Inhalten und Erstellen von Berichte](https://go.microsoft.com/fwlink/p/?linkid=324757)

## Weitere Informationen zu nicht durchsuchbaren Elementen

  - Auch wenn ein vollständig von der Exchange-Suche unterstützter Dateityp volltextindiziert wird, kann es zu Indizierungs- oder Suchfehlern kommen, die dazu führen, dass eine Datei als nicht durchsuchbares Element zurückgegeben wird. Beispielsweise kann das Durchsuchen einer sehr großen Excel-Datei zwar teilweise erfolgreich verlaufen, schlägt aber dann fehl, sobald die Größenbeschränkung überschritten wird. In diesem Fall ist es möglich, dass dieselbe Datei sowohl in den Suchergebnissen als auch als nicht durchsuchbares Element zurückgegeben wird.

  - Mit Microsoft-Technologien verschlüsselte Dateianlagen werden von der Exchange-Suche indiziert und durchsucht. Mit Nicht-Microsoft-Technologien verschlüsselte Dateien werden als nicht durchsuchbar zurückgegeben.

  - Mit S/MIME verschlüsselte E-Mail-Nachrichten werden nicht indiziert und werden als nicht durchsuchbare Elemente betrachtet. Dazu gehören verschlüsselte Nachrichten mit oder ohne Dateianlagen.

  - Durch die Verwaltung von Informationsrechten (Information Rights Management, IRM) geschützte Nachrichten werden von der Exchange-Suche indiziert und daher in die Suchergebnisse eingeschlossen, wenn sie den Abfrageparametern entsprechen. Weitere Informationen zur Verwaltung von Informationsrechten finden Sie unter [Verwaltung von Informationsrechten](information-rights-management-exchange-2013-help.md).

  - Wie bereits erwähnt, kann eine Schlüsselwortsuche Ergebnisse zurückgeben, wenn das Schlüsselwort in den indizierten Metadaten erscheint, da die Nachrichteneigenschaften und -metadaten indiziert werden. Dieselbe Schlüsselwortsuche kann jedoch nicht dasselbe Element zurückgeben, wenn das Schlüsselwort nur im Inhalt eines angehängten Elements mit einem nicht unterstützten Dateityp vorhanden ist. In diesem Fall wird das Element nur als nicht durchsuchbares Element zurückgegeben.

  - In eDiscovery in Exchange 2010 gibt es das Konzept der *Liste sicherer Adressen*. Dies sind Dateitypen, die nicht durchsuchbare Inhalte enthalten und daher nicht von der Exchange-Suche indiziert werden, z. B. Windows Media Video (.wmv)- und Waveform Audio (.wav)-Dateien. Da diese Dateitypen keinen durchsuchbaren Inhalt enthalten, werden sie in Exchange 2010 nicht als nicht durchsuchbare Elemente betrachtet. Postfachelemente, die diese Dateitypen enthalten, werden nicht als nicht durchsuchbare Elemente zurückgegeben und auch nicht in ein Discoverypostfach kopiert.
    
    In Exchange 2013 und Exchange Online gibt es keine Listen sicherer Adressen mehr. Dateitypen werden entweder für die Indizierung aktiviert bzw. deaktiviert oder sie werden nicht unterstützt. Deaktivierte und nicht unterstützte Dateitypen gelten als nicht durchsuchbare Elemente.

