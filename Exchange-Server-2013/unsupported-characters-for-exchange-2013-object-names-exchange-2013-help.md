---
title: 'Nicht unterstützte Zeichen in Exchange 2013-Objektnamen: Exchange 2013 Help'
TOCTitle: Nicht unterstützte Zeichen in Exchange 2013-Objektnamen
ms:assetid: 76fa4e23-f0f6-473b-9227-70ded907578f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn169553(v=EXCHG.150)
ms:contentKeyID: 54652692
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nicht unterstützte Zeichen in Exchange 2013-Objektnamen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Dieser Artikel beschreibt die Zeichen, die in Objektnamen oder Komponentennamen in Exchange 2013 nicht verwendet werden können. Wenn Sie Namen für Objekte oder Komponenten in Exchange 2013 erstellen, dürfen die Namen nur unterstützten Zeichen enthalten, selbst wenn Sie Objekte mit nicht unterstützten Zeichen erstellen können. Auch wenn Sie versuchen, Objekte zu importieren oder damit eine Verbindung herzustellen, deren Namen Zeichen enthalten, die nicht unterstützt werden, erhalten Sie möglicherweise eine Fehlermeldung, oder es kann zu unerwartetem Verhalten kommen.

## Nicht unterstützte Zeichen

In der folgenden Tabelle werden Zeichen aufgelistet, die bei Namen für Exchange-bezogene Objekte oder Komponenten nicht unterstützt werden. Die Tabelle enthält ebenfalls ein Szenario, in dem Probleme auftreten könnten, falls nicht unterstützte Zeichen verwendet werden. Beachten Sie, dass jedes Objekt in der Tabelle nur maximal 64 Zeichen lang sein darf.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange-Objekt oder -Komponente</th>
<th>Exchange-Szenario</th>
<th>Nicht unterstützte Zeichen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E-Mail-Domänenname</p></td>
<td><p>SMTP-Connector (Simple Mail Transfer Protocol)</p></td>
<td><p><code>~ ` ! @ # $ % ^ &amp; * ( ) + = { } | [ ] \ : &quot; ; &lt; &gt; , . ? /</code></p></td>
</tr>
<tr class="even">
<td><p>Hostname des Connectoradressraums</p></td>
<td><p>Nachrichtenübermittlung</p></td>
<td><p><code>..</code> (zwei Punkte)</p></td>
</tr>
<tr class="odd">
<td><p>Hostname für Exchange-Server</p></td>
<td><p>SMTP</p></td>
<td><p><code>_</code> (Unterstrich)</p></td>
</tr>
<tr class="even">
<td><p>Organisations- oder Standortname</p></td>
<td><p>Ausführen des Installationsprogramms und Verschieben von Postfächern</p></td>
<td><p><code>~ ` ! @ # $ % ^ &amp; * ( ) _ + = { } | [ ] \ : &quot; ; '  &lt; &gt; , . ? /</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsinterner Verzeichnisname</p></td>
<td><p>Verzeichnis</p></td>
<td><p><code>~ ` ! @ # $ % ^ &amp; * ( ) _ + = { } | [ ] \ : &quot; ; '  &lt; &gt; , . ? /</code></p></td>
</tr>
<tr class="even">
<td><p>Name der Öffentlichen Ordner-Struktur</p></td>
<td><p>Anzeigen und Erstellen des Öffentlichen Ordners</p></td>
<td><p><code>: ;</code></p></td>
</tr>
<tr class="odd">
<td><p>Empfängername</p></td>
<td><p>SMTP</p></td>
<td><p><code>' &quot;</code></p></td>
</tr>
<tr class="even">
<td><p>SMTP-Adresse der Empfängerrichtlinie</p></td>
<td><p>Anzeigen der Öffentlichen Ordner-Hierarchie</p></td>
<td><p><code>~ ` ! @ # $ % ^ &amp; * ( ) + = { } | [ ] \ : &quot; ; &lt; &gt; , . ? /</code></p></td>
</tr>
<tr class="odd">
<td><p>Hostname der SMTP-Adresse der Empfängerrichtlinie</p></td>
<td><p>Nachrichtenübermittlung</p></td>
<td><p><code>..</code> (zwei Punkte)</p></td>
</tr>
<tr class="even">
<td><p>Standortinterner Verzeichnisname</p></td>
<td><p>Anzeigen der Öffentlichen Ordner-Hierarchie</p></td>
<td><p><code>? ( ) *</code></p></td>
</tr>
<tr class="odd">
<td><p>Smarthostname</p></td>
<td><p>SMTP</p></td>
<td><p>Voran- oder nachgestellte Leerzeichen</p></td>
</tr>
</tbody>
</table>

