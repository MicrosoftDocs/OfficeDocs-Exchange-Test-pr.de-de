---
title: 'Anzeigen von Statistiken für öffentliche Ordner und Elemente öffentlicher Ordner: Exchange 2013 Help'
TOCTitle: Anzeigen von Statistiken für öffentliche Ordner und Elemente öffentlicher Ordner
ms:assetid: 4e412710-9a74-4649-ab01-502e969a7eda
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997949(v=EXCHG.150)
ms:contentKeyID: 50475616
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von Statistiken für öffentliche Ordner und Elemente öffentlicher Ordner

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-14_

In diesem Thema wird das Abrufen von Statistikdaten zu öffentlichen Ordnern (z. B. Anzeigename, Erstellungszeitpunkt, Zeitpunkt der letzten Änderung, letzter Benutzerzugriff und Elementgröße) erläutert. Anhand dieser Informationen können Sie Entscheidungen zum Löschen oder Aufbewahren von öffentlichen Ordnern treffen.


> [!NOTE]
> In der Exchange-Verwaltungskonsole können Sie einige der Kontingent- und Nutzungsinformationen für öffentliche Ordner anzeigen. Wechseln Sie hierzu zu <STRONG>Öffentliche Ordner</STRONG> &gt; <STRONG>Bearbeiten</STRONG><IMG title=Bearbeitungssymbol alt=Bearbeitungssymbol src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif"> &gt; <STRONG>Postfachnutzung</STRONG>. Diese Informationen sind jedoch nicht vollständig, und es empfiehlt sich, die Statistiken zu öffentlichen Ordnern mithilfe der Shell anzuzeigen.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit öffentlichen Ordnern finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Statistikdaten von öffentlichen Ordnern können nicht in der Exchange-Verwaltungskonsole abgerufen werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Abrufen der Statistikdaten von Öffentlichen Ordnern

In diesem Beispiel werden die Statistikdaten für den Öffentlichen Ordner "Marketing" mit einem anschließenden Befehl (hinter dem senkrechten Strich) zum Formatieren der Liste abgerufen.

    Get-PublicFolderStatistics -Identity \Marketing | Format-List


> [!NOTE]
> Der Wert für den Parameter <EM>Identity</EM> muss die Pfadangabe für den öffentlichen Ordner enthalten. Wenn der Öffentliche Ordner "Marketing" z. B. unter dem übergeordneten Ordner "Business" gespeichert ist, geben Sie den folgenden Wert an: <CODE>\Business\Marketing</CODE>



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-PublicFolderStatistics](https://technet.microsoft.com/de-de/library/aa998663\(v=exchg.150\)).

## Anzeigen von Statistikdaten zu öffentlichen Ordnern mithilfe der Shell

Sie können die folgenden Informationen zu Elementen in einem öffentlichen Ordner anzeigen:

  - Typ des Elements

  - Betreff

  - Uhrzeit der letzten Änderung durch einen Benutzer

  - Zeitpunkt des letzten Benutzerzugriffs

  - Erstellungszeit

  - Anlagen

  - Nachrichtengröße

Mithilfe dieser Informationen können Sie Entscheidungen dazu treffen, welche Aktionen für Ihre Öffentlichen Ordner durchgeführt werden sollen, wie z. B., welche Öffentlichen Ordner gelöscht werden sollen. Beispielsweise können Sie festlegen, dass ein Öffentlicher Ordner gelöscht werden soll, wenn für mehr als 2 Jahre nicht auf die enthaltenen Elemente zugegriffen wurde, oder Sie können einen Öffentlichen Ordner, der als Dokumentrepository verwendet wird, für eine andere Clientzugriffsanwendung konvertieren.

In diesem Beispiel werden Standardstatistiken zu allen Elementen im öffentlichen Ordner "Pamphlets" im Pfad "\\Marketing\\2013" zurückgegeben. Standardinformationen sind u. a. Identität, Erstellungszeit und Betreff.

    Get-PublicFolderItemStatistics -Identity "\Marketing\2013\Pamphlets"

In diesem Beispiel werden zusätzliche Informationen zu den Elementen im öffentlichen Ordner "Pamphlets" zurückgegeben, z. B. Betreff, Zeitpunkt der letzten Änderung, Erstellungszeit, Anlagen, Nachrichtengröße und Elementtyp. Darüber hinaus umfasst es einen weitergeleiteten Befehl zum Formatieren der Liste.

    Get-PublicFolderItemStatistics -Identity "\Marketing\2010\Pamphlets" | Format-List

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-PublicFolderItemStatistics](https://technet.microsoft.com/de-de/library/ee332344\(v=exchg.150\)).

## Verwenden der Shell zum Exportieren der Ausgabe des Cmdlets "Get-PublicFolderItemStatistics" in eine CSV-Datei

In diesem Beispiel wird die Ausgabe des Cmdlets in die Datei "PFItemStats.csv" exportiert, die die folgenden Informationen für alle Elemente im öffentlichen Ordner "\\Marketing\\Reports" enthält:

  - Betreff der Nachricht (`Subject`)

  - Datum und Uhrzeit der letzten Änderung des Elements (`LastModificationTime`)

  - Information, ob das Element Anlagen enthält (`HasAttachments`)

  - Typ des Elements (`ItemType)`

  - Größe des Elements (`MessageSize`)

<!-- end list -->

    Get-PublicFolderItemStatistics -Identity "\Marketing\Reports" | Select Subject,LastModificationTime,HasAttachments,ItemType,MessageSize | Export-CSV C:\PFItemStats.csv

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-PublicFolderItemStatistics](https://technet.microsoft.com/de-de/library/ee332344\(v=exchg.150\)).

