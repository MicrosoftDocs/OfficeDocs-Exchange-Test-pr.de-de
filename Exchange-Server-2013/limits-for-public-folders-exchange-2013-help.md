---
title: 'Grenzwerte für öffentliche Ordner: Exchange 2013 Help'
TOCTitle: Grenzwerte für öffentliche Ordner
ms:assetid: 709b075e-9584-484b-bcaa-e781c26497b4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn594582(v=EXCHG.150)
ms:contentKeyID: 61170901
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grenzwerte für öffentliche Ordner

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In Exchange Server 2013 wurden Öffentliche Ordner aus einer herkömmlichen Datenbankarchitektur in eine Postfacharchitektur verschoben. Dadurch profitieren Öffentliche Ordner beispielsweise von der Flexibilität einer Database Availability Group (DAG) und anderen, im Laufe der Jahre vorgenommenen Postfachverbesserungen. Allerdings sind neue Begrenzungen und Leistungsbedenken zu beachten. Dieses Dokument enthält einige generelle Empfehlungen für die Behandlung von Konfigurationsoptionen, die Auswirkungen auf die Leistung und Konfiguration Öffentlicher Ordner haben können.

## Grenzwerte

In der folgenden Tabelle sind die Beschränkungen öffentlicher Ordner im lokalen Exchange Server 2013 aufgeführt. Sofern die aufgeführten Werte nicht ausdrücklich als „empfohlen“ vermerkt sind, handelt es sich bei den Werten in der Tabelle um die für öffentliche Ordner unterstützten Grenzwerte.


> [!IMPORTANT]
> Angaben zu den Begrenzungen von Exchange&nbsp;Online für Office&nbsp;365 finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=391188">Exchange Online-Begrenzungen</A>.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Grenzwerte</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Gesamtzahl der Postfächer für Öffentliche Ordner</p></td>
<td><p>100</p></td>
<td><p>Sie können zwar mehr als 100 Postfächer für Öffentliche Ordner anlegen, allerdings werden diese nicht unterstützt. <a href="https://docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/create-public-folder-mailbox">Erstellen eines Postfachs für öffentliche Ordner</a></p></td>
</tr>
<tr class="even">
<td><p>Gesamtzahl Öffentlicher Ordner in der Hierarchie</p></td>
<td><p>1,000,000</p></td>
<td><p>Sie können zwar mehr als 1.000.000 öffentliche Ordner erstellen, diese werden jedoch nicht unterstützt. Es empfiehlt sich, <a href="considerations-when-deploying-public-folders-exchange-2013-help.md">Hinweise für das Bereitstellen von öffentlichen Ordnern</a> zu lesen, wenn eine Bereitstellung mehr als 100.000 öffentliche Ordner aufweist.</p></td>
</tr>
<tr class="odd">
<td><p>Unterordner unter dem übergeordneten Ordner</p></td>
<td><p>10,000</p></td>
<td><p>Sie können zwar mehr als 1.000 Unterordner unter einem übergeordneten Ordner erstellen, doch wir raten davon ab.</p>
<p>Parameter <em>FolderHierarchyChildrenCountReceiveQuota</em> im Cmdlet <a href="https://technet.microsoft.com/de-de/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="even">
<td><p>Ordnerhierarchietiefe</p></td>
<td><p>300</p></td>
<td><p>Die Ordnerhierarchietiefe ist die Anzahl der Ebenen geschachtelter Ordner, die in einem Zweig einer öffentlichen Ordnerstruktur vorhanden sein können. Parameter <em>FolderHierarchyDepthRecieveQuota</em> im Cmdlet <a href="https://technet.microsoft.com/de-de/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Maximal zulässige Nachrichten pro Öffentlicher Ordner</p></td>
<td><p>1 Million</p></td>
<td><p>Parameter <em>MailboxMessagesPerFolderCountRecieveQuota</em> im Cmdlet <a href="https://technet.microsoft.com/de-de/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="even">
<td><p>Maximale Größe der einzelnen Öffentlichen Ordner</p></td>
<td><p>10 GB</p></td>
<td><p>Diese Beschränkung schließt Unterordner eines einzelnen Ordners nicht mit ein.</p>
<p><a href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">Konfigurieren von Speicherkontingenten für ein Postfach</a></p></td>
</tr>
<tr class="odd">
<td><p>Größe der Postfächer für Öffentliche Ordner</p></td>
<td><p>100 GB</p></td>
<td><p><a href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">Konfigurieren von Speicherkontingenten für ein Postfach</a></p></td>
</tr>
<tr class="even">
<td><p>Anzahl der Benutzeranmeldungen pro Postfach für öffentliche Ordner</p></td>
<td><p>2.000 gleichzeitige Benutzeranmeldungen</p></td>
<td><p>Empfohlen wird die Konfiguration einer Hierarchie mit maximal 2.000 Benutzern pro Postfach eines Öffentlichen Ordners. Für 20.000 Benutzer brauchen Sie beispielsweise 10 Postfächer für Öffentliche Ordner.</p></td>
</tr>
<tr class="odd">
<td><p>Aufbewahrung verschobener Elemente</p></td>
<td><p>14 Tage empfohlen</p></td>
<td><p>Verwenden Sie den Parameter <em>DefaultPublicFolderMovedItemRetention</em> im Cmdlet <strong>Set-OrganizationConfig</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Verfallszeit</p></td>
<td><p>Geben Sie hier denselben Standardwert ein wie für normale Postfächer.</p></td>
<td><p>Diese Einstellungen können auf den folgenden Ebenen erfolgen:</p>
<ul>
<li><p><strong>Organisationsebene:</strong> Parameter <em>DefaultPublicFolderAgeLimit</em> im Cmdlet <strong>Set-OrganizationConfig</strong>.</p></li>
<li><p><strong>Postfachebene:</strong> Parameter <em>AgeLimit</em> im Cmdlet <strong>Set-Mailbox</strong>.</p></li>
<li><p><strong>Ordnerebene:</strong> Parameter <em>AgeLimit</em> im Cmdlet <strong>Set-PublicFolder</strong>.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Aufbewahrungszeit für gelöschte Elemente</p></td>
<td><p>Geben Sie hier denselben Standardwert ein wie für normale Postfächer.</p></td>
<td><p>Diese Einstellungen können auf den folgenden Ebenen erfolgen:</p>
<ul>
<li><p><strong>Organisationsebene:Parameter</strong> <em>DefaultPublicFolderMovedItemRetention</em> im Cmdlet <strong>Set-OrganizationConfig</strong>.</p></li>
<li><p><strong>Postfachebene:</strong> Parameter <em>RetainDeletedItemsFor</em> im Cmdlet <strong>Set-Mailbox</strong>.</p></li>
<li><p><strong>Ordnerebene:</strong> Parameter <em>RetainDeleteItemsFor</em> im Cmdlet <strong>Set-PublicFolder</strong>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Maximale Anzahl von öffentlichen Ordnern, die zu Exchange 2013 migriert werden können</p></td>
<td><p>500,000</p></td>
<td><p>Dies ist die maximale Anzahl von öffentlichen Ordnern, die Sie in einer einzigen Migration von einer Legacy-Version von Exchange zu Exchange 2013 verschieben können. Ausführliche Informationen zur Migration öffentlicher Ordner finden Sie unter <a href="use-batch-migration-to-migrate-public-folders-to-exchange-2013-from-previous-versions-exchange-2013-help.md">Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen</a>.</p></td>
</tr>
</tbody>
</table>

