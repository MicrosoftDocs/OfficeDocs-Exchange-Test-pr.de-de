---
title: 'Unterstützte Zeichensätze für Remotedomänen: Exchange 2013 Help'
TOCTitle: Unterstützte Zeichensätze für Remotedomänen
ms:assetid: 66023a62-1fd3-4019-be2b-4e7147db148a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998600(v=EXCHG.150)
ms:contentKeyID: 52062725
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Unterstützte Zeichensätze für Remotedomänen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die folgenden Zeichensätze können für Nachrichten angegeben werden, die am Remotedomänen gesendet werden.

  - Wählen Sie im Exchange Admin Center (EAC) auf der Einstellungsseite für **Remotedomänen** den Namen aus den Dropdownlisten **MIME-Zeichensatz** und **Nicht-MIME-Zeichensatz** aus.

  - Verwenden Sie in der Shell den Wert in der Spalte "Name" in der folgenden Tabelle für den Parameter *CharacterSet* oder den Parameter *NonMimeCharacterSet* im Cmdlet [Set-RemoteDomain](https://technet.microsoft.com/de-de/library/aa997857\(v=exchg.150\)).

### Unterstützte Zeichensätze für die Konfiguration von Remotedomänen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>big5</p></td>
<td><p>Chinesisch Traditionell (Big5)</p></td>
</tr>
<tr class="even">
<td><p>DIN_66003</p></td>
<td><p>Deutsch (IA5)</p></td>
</tr>
<tr class="odd">
<td><p>euc-jp</p></td>
<td><p>Japanisch (EUC)</p></td>
</tr>
<tr class="even">
<td><p>euc-kr</p></td>
<td><p>Koreanisch (EUC)</p></td>
</tr>
<tr class="odd">
<td><p>GB18030</p></td>
<td><p>Chinesisch Vereinfacht (GB18030)</p></td>
</tr>
<tr class="even">
<td><p>gb2312</p></td>
<td><p>Chinesisch Vereinfacht (GB2312)</p></td>
</tr>
<tr class="odd">
<td><p>hz-gb-2312</p></td>
<td><p>Chinesisch Vereinfacht (HZ)</p></td>
</tr>
<tr class="even">
<td><p>ISO-2022-JP</p></td>
<td><p>Japanisch (JIS)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-2022-KR</p></td>
<td><p>Koreanisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-1</p></td>
<td><p>Westeuropäisch (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-8859-2</p></td>
<td><p>Mitteleuropäisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-3</p></td>
<td><p>Lateinisch 3 (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-8859-4</p></td>
<td><p>Baltisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-5</p></td>
<td><p>Kyrillisch (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-8859-6</p></td>
<td><p>Arabisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-7</p></td>
<td><p>Griechisch (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-8859-8</p></td>
<td><p>Hebräisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-9</p></td>
<td><p>Türkisch (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>ISO-8859-13</p></td>
<td><p>Estnisch (ISO)</p></td>
</tr>
<tr class="even">
<td><p>ISO-8859-15</p></td>
<td><p>Lateinisch 9 (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>KOI8-R</p></td>
<td><p>Kyrillisch (KOI8-R)</p></td>
</tr>
<tr class="even">
<td><p>KOI8-U</p></td>
<td><p>Kyrillisch (KOI8-U)</p></td>
</tr>
<tr class="odd">
<td><p>KS_C_5601-1987</p></td>
<td><p>Koreanisch (Windows)</p></td>
</tr>
<tr class="even">
<td><p>NS_4551-1</p></td>
<td><p>Norwegisch (IA5)</p></td>
</tr>
<tr class="odd">
<td><p>SEN_850200_B</p></td>
<td><p>Schwedisch (IA5)</p></td>
</tr>
<tr class="even">
<td><p>Shift_JIS</p></td>
<td><p>Japanisch (Shift-JIS)</p></td>
</tr>
<tr class="odd">
<td><p>UTF-8</p></td>
<td><p>Unicode (UTF-8)</p></td>
</tr>
<tr class="even">
<td><p>Windows-1250</p></td>
<td><p>Mitteleuropäisch (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>Windows-1251</p></td>
<td><p>Kyrillisch (Windows)</p></td>
</tr>
<tr class="even">
<td><p>Windows-1252</p></td>
<td><p>Westeuropäisch (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>Windows-1253</p></td>
<td><p>Griechisch (Windows)</p></td>
</tr>
<tr class="even">
<td><p>Windows-1254</p></td>
<td><p>Türkisch (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>Windows-1255</p></td>
<td><p>Hebräisch (Windows)</p></td>
</tr>
<tr class="even">
<td><p>Windows-1256</p></td>
<td><p>Arabisch (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>Windows-1257</p></td>
<td><p>Baltisch (Windows)</p></td>
</tr>
<tr class="even">
<td><p>Windows-1258</p></td>
<td><p>Vietnamesisch (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>Windows-874</p></td>
<td><p>Thailändisch (Windows)</p></td>
</tr>
</tbody>
</table>

