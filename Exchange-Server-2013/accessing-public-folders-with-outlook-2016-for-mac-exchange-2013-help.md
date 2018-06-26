---
title: 'Zugreifen auf öffentliche Ordner mit Outlook 2016 für Mac: Exchange 2013 Help'
TOCTitle: Zugreifen auf öffentliche Ordner mit Outlook 2016 für Mac
ms:assetid: bc9b8226-bd8b-4edc-882b-4f19cfe118eb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt788631(v=EXCHG.150)
ms:contentKeyID: 74115365
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zugreifen auf öffentliche Ordner mit Outlook 2016 für Mac

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016, Office 365_

_**Letztes Änderungsdatum des Themas:**2017-05-19_

**Zusammenfassung:** Dieser Artikel führt die neuesten unterstützten Exchange-Topologien auf, in denen Benutzer mit Outlook 2016 für Mac auf öffentliche Ordner zugreifen können.

Mit der Veröffentlichung des [Updates vom April 2016](https://go.microsoft.com/fwlink/?linkid=82920) für Outlook 2016 für Mac-Clients, des [kumulativen Updates 14 (CU14)](https://go.microsoft.com/fwlink/?linkid=84943) für Exchange 2013 und des [kumulativen Updates 2 (CU 2)](https://go.microsoft.com/fwlink/p/?linkid=84979) für Exchange 2016 für Mac können Benutzer von Outlook 2016 für Mac jetzt in mehr Topologien als zuvor auf öffentliche Ordner zugreifen.

## Einschränkungen bei Outlook für Mac

Grundsätzlich können alle Versionen von Outlook für Mac auf öffentliche Exchange-Ordner zugreifen. Bis vor Kurzem konnten diese Clients jedoch in den folgenden Bereitstellungsszenarien nicht auf öffentliche Ordner zugreifen:

  - **Koexistenz mit öffentlichen Ordnern in Legacy-Versionen:** Befand sich das Postfach eines Benutzers auf einem Exchange 2013- oder Exchange 2016-Server, konnte der Benutzer mit Outlook für Mac nicht auf öffentliche Ordner zugreifen, die auf Servern mit 2010 SP3 oder höher bereitgestellt waren. Andere Clients können in einem solchen Szenario auf öffentliche Ordner in der Legacy-Version zugreifen.

  - **Hybridtopologien:** Lokale Benutzer mit einem Exchange Online-Postfach konnten mit Outlook für Mac nicht auf lokale moderne öffentliche Ordner zugreifen. Ebenso konnten Benutzer mit einem lokalen Exchange 2013- oder Exchange 2016-Postfach mit Outlook für Mac nicht auf öffentliche Ordner in Exchange Online zugreifen.

## Outlook 2016 für Mac

Mit der Veröffentlichung des Updates vom April 2016 für Outlook 2016 für Mac sowie des kumulativen Updates CU14 für Exchange 2013 und CU2 für Exchange 2016 funktionieren die oben beschriebenen Szenarien jetzt auch mit Outlook 2016 für Mac-Clients.

Die folgende Tabelle gibt einen Überblick über die unterstützten Topologien für Benutzer mit Outlook 2016 für Mac-Clients, die auf öffentliche Ordner in Exchange 2013, Exchange 2016 oder Exchange Online zugreifen möchten.


> [!NOTE]
> Für die in der nachfolgenden Tabelle dargestellten Szenarien setzen wir voraus, dass das Update vom April&nbsp;2016 für Outlook&nbsp;2016&nbsp;für&nbsp;Mac auf allen Clients installiert wurde.




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
<th>Öffentliche Ordner bereitgestellt in:</th>
<th>Benutzerpostfach in Exchange 2010 SP3 oder höher</th>
<th>Benutzerpostfach in Exchange 2013 CU13 oder höher</th>
<th>Benutzerpostfach in Exchange 2016 CU2 oder höher</th>
<th>Benutzerpostfach in Office 365/Exchange Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Server 2010 SP3 oder höher</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Exchange Server 2013 CU13 oder höher</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td><p>Exchange Server 2016 CU2 oder höher</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Office 365/Exchange Online</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
</tr>
</tbody>
</table>


In den folgenden Artikeln wird beschrieben, wie Sie in Ihrer Exchange-Organisation öffentliche Ordner in einer Koexistenztopologie oder einer Hybridtopologie bereitstellen können. Sofern auf Ihren Outlook 2016 für Mac-Clients das Update vom April 2016 installiert ist, können die Clients auf öffentliche Ordner in den in diesen Artikeln beschriebenen Konfigurationen zugreifen:

  - [Konfigurieren älterer öffentlicher Ordner, wenn sich die Postfächer der Benutzer auf Exchange 2013-Servern befinden](configure-legacy-public-folders-where-user-mailboxes-are-on-exchange-2013-servers-exchange-2013-help.md)

  - [Konfigurieren öffentlicher Exchange 2013-Ordner für eine Hybridbereitstellung](configure-exchange-2013-public-folders-for-a-hybrid-deployment-exchange-2013-help.md)

  - [Konfigurieren öffentlicher Exchange Online-Ordner für eine Hybridbereitstellung](configure-exchange-online-public-folders-for-a-hybrid-deployment-exchange-2013-help.md)

