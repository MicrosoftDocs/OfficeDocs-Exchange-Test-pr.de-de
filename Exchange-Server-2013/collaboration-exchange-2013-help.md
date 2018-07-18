---
title: 'Zusammenarbeit: Exchange 2013 Help'
TOCTitle: Zusammenarbeit
ms:assetid: f45c1be1-2a66-4610-a28d-4adc6d212769
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218725(v=EXCHG.150)
ms:contentKeyID: 50477079
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zusammenarbeit

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Exchange 2013 bieten die folgenden umfassenden Funktionen zur Erleichterung der Zusammenarbeit per E-Mail:

  - Websitepostfächer

  - Öffentliche Ordner

  - Freigegebene Postfächer

  - Verteilergruppen

Jede dieser Funktionen weist eine andere Herangehensweise und einen anderen Umfang auf und sollte auf Basis dessen genutzt werden, was der Benutzer erreichen muss und was von Ihrer Organisation bereitgestellt werden kann. Websitepostfächer eignen sich beispielsweise besonders für die Zusammenarbeit an Dokumentation. Für Websitepostfächer ist allerdings SharePoint Server 2013 erforderlich. Wenn Sie nicht vorhaben, SharePoint bereitzustellen, sollten Sie für die Freigabe von Dokumenten öffentliche Ordner nutzen.

In diesem Thema werden diese Funktionen für die Zusammenarbeit verglichen, um Sie bei der Entscheidung zu unterstützen, was Sie Ihren Benutzern anbieten möchten.

## Websitepostfächer

Ein Websitepostfach basiert auf der Mitgliedschaft in einer SharePoint 2013-Website (Besitzer und Mitglieder), über ein Exchange 2013-Postfach für E-Mail-Nachrichten freigegebenem Speicher und einer SharePoint 2013-Website für Speicherung und Freigabe. In einem Websitepostfach werden im Wesentlichen Exchange-E-Mail und SharePoint-Dokumente zusammengeführt. Für Benutzer dient ein Websitepostfach als zentrale Projektablage, die einen Speicherort für Projekt-E-Mails und -dokumente bereitstellt, die nur von Websitemitgliedern aufgerufen und bearbeitet werden können. Außerdem haben Websitepostfächer einen bestimmten Lebenszyklus und sind für Projekte optimiert, die ein Start- und Enddatum aufweisen. Endnutzer müssen Outlook 2013 verwenden, um Websitepostfächer vollständig zu implementieren.

Weitere Informationen finden Sie unter [Websitepostfächer](site-mailboxes-exchange-2013-help.md).

## Öffentliche Ordner

Öffentliche Ordner ermöglichen den gemeinsamen Zugriff und stellen ein einfaches und effektives Mittel zum Erfassen, Organisieren und Freigeben von Informationen für andere Personen in der Arbeitsgruppe oder Organisation dar.

Dieser Inhalt wird mithilfe öffentlicher Ordner in einer Hierarchie angeordnet, die einfach zu durchsuchen ist. Benutzer können interessante und relevante Inhalte finden, indem Sie die für sie relevanten Unterordner dieser Hierarchie durchsuchen. Den Benutzern wird immer die vollständige Hierarchie in ihrer Outlook-Ordneransicht angezeigt. Öffentliche Ordner sind eine großartige Möglichkeit zur Archivierung von Verteilergruppen. Öffentliche Ordner können E-Mail-aktiviert und als Mitglied der Verteilergruppe hinzugefügt werden. Die an die Verteilergruppe gesendeten E-Mails werden automatisch für den späteren Zugriff zum öffentlichen Ordner hinzugefügt. Öffentliche Ordner bieten außerdem eine einfache Dokumentfreigabe und setzen nicht die Installation von SharePoint Server 2013 in Ihrer Organisation voraus. Schließlich können Endbenutzer öffentliche Ordner mit den folgenden unterstützten Outlook-Clients nutzen: Outlook 2007, Outlook 2010 und Outlook 2013.

Weitere Informationen finden Sie unter [Öffentliche Ordner](public-folders-exchange-2013-help.md).

## Freigegebene Postfächer

Ein freigegebenes Postfach ist ein Postfach, auf das mehrere vorgesehene Benutzer zum Lesen und Senden von E-Mail-Nachrichten zugreifen und das sie zum Freigeben eines gemeinsamen Kalenders nutzen können. Freigegebene Postfächer können eine allgemeine E-Mail-Adresse (wie "info@contoso.com" oder "vertrieb@contoso.com") bereitstellen, über die Kunden Anfragen an das Unternehmen senden können. Wenn dem freigegebenen Postfach die Berechtigung "Senden als" zugewiesen ist, wenn ein angegebener Benutzer auf die E-Mail-Nachricht antwortet, kann es so aussehen, als ob das Postfach (z. B. "vertrieb@contoso.com") und nicht der eigentliche Benutzer antwortet.

Weitere Informationen finden Sie unter [Freigegebene Postfächer](shared-mailboxes-exchange-2013-help.md).

## Gruppen

Gruppen, auch Verteilergruppen genannt, sind eine Zusammenstellung von mindestens zwei Personen, die im freigegebenen Adressbuch angezeigt wird. Wenn eine E-Mail-Nachricht an eine Gruppe gesendet wird, wird sie von allen Mitgliedern der Gruppe empfangen. Verteilergruppen können nach einem bestimmten Diskussionsthema wie "Tierfreunde" oder nach Benutzern mit einer gemeinsamen Arbeitsstruktur angeordnet werden, die eine regelmäßige Kommunikation untereinander erfordert.

Weitere Informationen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

## Auswahl der richtigen Option

Die folgende Tabelle bietet einen schnellen Überblick über die einzelnen Funktionen für die Zusammenarbeit, um Ihnen die Auswahl der richtigen Option zu erleichtern.


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
<th></th>
<th>Websitepostfächer</th>
<th>Öffentliche Ordner</th>
<th>Freigegebene Postfächer</th>
<th>Gruppen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Art der Gruppe</strong></p></td>
<td><p>Zusammenarbeit als Team an einem bestimmten Projekt mit konkretem Start- und Enddatum.</p></td>
<td><p>Bei entsprechenden Berechtigungen können alle Personen in Ihrer Organisation auf öffentliche Ordner zugreifen und diese durchsuchen. Öffentliche Ordner eignen sich ideal für die Verwaltung des Verlaufs oder von Unterhaltungen in Verteilergruppen.</p></td>
<td><p>Stellvertretungen, die im Namen einer virtuellen Identität arbeiten und als diese freigegebene Postfachidentität auf E-Mails antworten können. Beispiel: support@tailspintoys.com</p></td>
<td><p>Benutzer, die E-Mails an eine Gruppe von Empfängern mit gemeinsamen Interessen oder Merkmalen senden müssen.</p></td>
</tr>
<tr class="even">
<td><p><strong>Ideale Gruppengröße</strong></p></td>
<td><p>Klein</p></td>
<td><p>Groß</p></td>
<td><p>Klein</p></td>
<td><p>Groß</p></td>
</tr>
<tr class="odd">
<td><p><strong>Zugriff</strong></p></td>
<td><p>Websitepostfachbesitzer und -mitglieder.</p></td>
<td><p>Der Zugriff ist allen Benutzern in Ihrer Organisation möglich.</p></td>
<td><p>Benutzern können Berechtigungen für den Vollzugriff und/oder zum Senden erteilt werden. Wenn Benutzer die Berechtigungen für den Vollzugriff erhalten, müssen Sie das freigegebene Postfach auch zu ihrem Outlook-Profil hinzufügen, um darauf zugreifen zu können.</p></td>
<td><p>Verteilergruppen müssen Mitglieder manuell hinzugefügt werden. Für dynamische Verteilergruppen werden die Mitglieder anhand von Filterkriterien hinzugefügt.</p></td>
</tr>
<tr class="even">
<td><p><strong>Freigegebener Kalender?</strong></p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p><strong>E-Mail-Eingang im persönlichen Posteingang des Benutzers?</strong></p></td>
<td><p>Nein, E-Mails gehen im Websitepostfach ein.</p></td>
<td><p>Nein, E-Mails gehen im öffentlichen Ordner ein.</p></td>
<td><p>Nein, E-Mails gehen im Posteingang des freigegebenen Postfachs ein.</p></td>
<td><p>Ja. Ja, E-Mails gehen im Posteingang des Mitglieds einer Verteilergruppe ein.</p></td>
</tr>
<tr class="even">
<td><p><strong>Unterstützte Clients</strong></p></td>
<td><ul>
<li><p>Outlook 2013</p></li>
<li><p>SharePoint 2013</p></li>
</ul></td>
<td><ul>
<li><p>Outlook 2013</p></li>
<li><p>Outlook 2010</p></li>
<li><p>Outlook 2007</p></li>
</ul></td>
<td><ul>
<li><p>Outlook 2013</p></li>
<li><p>Outlook Web App</p></li>
<li><p>Outlook 2010</p></li>
<li><p>Outlook 2007</p></li>
</ul></td>
<td><ul>
<li><p>Outlook 2013</p></li>
<li><p>Outlook Web App</p></li>
<li><p>Outlook 2010</p></li>
<li><p>Outlook 2007</p></li>
</ul></td>
</tr>
</tbody>
</table>

