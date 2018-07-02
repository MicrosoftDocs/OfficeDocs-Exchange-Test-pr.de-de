---
title: 'Messagingrichtlinie und -kompatibilität: Exchange 2013 Help'
TOCTitle: Messagingrichtlinie und -kompatibilität
ms:assetid: 65f20a20-27a4-4f6e-9b27-f8705d65b8d9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998599(v=EXCHG.150)
ms:contentKeyID: 50475843
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Messagingrichtlinie und -kompatibilität

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

E-Mails sind für Information-Worker in Organisationen aller Größen ein zuverlässiges und allgegenwärtiges Kommunikationsmedium. Nachrichtenspeicher und Postfächer sind heute Repositorys mit wertvollen Daten. Organisationen müssen Messagingrichtlinien formulieren, die die regelkonforme Verwendung ihrer Nachrichtensysteme vorschreiben, den Benutzern Anleitungen zur Umsetzung der Richtlinien bereitstellen und ggf. Details zu den Kommunikationsarten bereitstellen, die nicht zulässig sind.

Organisationen müssen auch Richtlinien zum Lebenszyklus von E-Mails erstellen, Nachrichten so lange aufbewahren, wie es aus geschäftlichen oder rechtlichen Gründen notwendig ist, E-Mail-Datensätze zu Beweissicherungs- und Untersuchungszwecken aufbewahren und darauf vorbereitet sein, jegliche E-Mail-Datensätze zu finden und bereitzustellen, die zur Erfüllung von eDiscovery-Anforderungen benötigt werden.

Vertrauliche Informationen wie geistiges Eigentum, Betriebsgeheimnisse, Geschäftspläne sowie personenbezogene Informationen (Personally Identifiable Information, PII), die von Ihrer Organisation erfasst oder verarbeitet werden, müssen vor Lecks geschützt werden.

## Messagingrichtlinien und Richtlinientreue in Exchange 2013

Die folgende Tabelle bietet einen Überblick über die Funktionen für Messagingrichtlinien und Richtlinientreue in Microsoft Exchange Server 2013 und enthält Links zu Themen, in denen Sie weitere Informationen zu diesen Funktionen und ihrer Verwaltung finden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Beschreibung</th>
<th>Ressourcen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Messaging-Datensatzverwaltung (Messaging Records Management, MRM)</p></td>
<td><p>Organisationen erstellen im Rahmen ihrer Messagingrichtlinien auch Richtlinien zu E-Mail-Lebenszyklen, um entsprechende Vorschriften einzuhalten sowie rechtliche oder geschäftliche Anforderungen zu erfüllen. Diese Richtlinien sollten u. a. folgende allgemeine Fragen berücksichtigen:</p>
<ul>
<li><p>Wie lange sollen Nachrichten aufbewahrt werden?</p></li>
<li><p>Wo sollen die Nachrichten aufbewahrt werden?</p></li>
<li><p>Sollen alle Nachrichten über den gleichen Zeitraum aufbewahrt werden?</p></li>
</ul>
<p>Exchange 2013 enthält MRM-Funktionen, mit denen Sie die E-Mail-Lebenszyklusrichtlinien Ihrer Organisation implementieren können. Sie können über die Messaging-Datensatzverwaltung einheitliche Aufbewahrungseinstellungen auf alle Nachrichten anwenden, oder Sie verwenden benutzerdefinierte Aufbewahrungsrichtlinien, um eine grundlegende Aufbewahrungskonfiguration auf ein Postfach anzuwenden. Optional können Sie auch Benutzern ermöglichen, Nachrichten zu klassifizieren, damit diese für einen bestimmten Zeitraum aufbewahrt werden.</p></td>
<td><p><a href="messaging-records-management-exchange-2013-help.md">Messaging-Datensatzverwaltung</a></p></td>
</tr>
<tr class="even">
<td><p>Compliance-Archivierung</p></td>
<td><p><em>Compliance-Archive</em> unterstützen Sie dabei, die Kontrolle über die Messagingdaten Ihrer Organisation zurückzuerhalten, da keine PST-Dateien mehr benötigt werden. Außerdem gestatten sie es Benutzern, Nachrichten in einem <em>Archivpostfach</em> zu speichern, auf das in Outlook 2010 und höher sowie in Outlook Web App zugegriffen werden kann.</p></td>
<td><p><a href="in-place-archiving-in-exchange-2013-exchange-2013-help.md">In-Situ-Archivierung in Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Compliance-Archiv</p></td>
<td><p>Wenn Rechtsstreitigkeiten zu erwarten sind, sind Organisationen dazu verpflichtet, die für den Fall relevanten elektronisch gespeicherten Informationen einschließlich E-Mail aufzubewahren. Compliance-Archive ermöglichen Ihnen das Suchen und Aufbewahren von Nachrichten, die bestimmten Abfrageparametern entsprechen. Nachrichten werden vor jeglicher Löschung, Veränderung und Manipulation geschützt und können unbegrenzt oder über einen bestimmten Zeitraum aufbewahrt werden.</p></td>
<td><p><a href="in-place-hold-and-litigation-hold-exchange-2013-help.md">In-Place Hold and Litigation Hold</a></p></td>
</tr>
<tr class="even">
<td><p>Compliance-eDiscovery</p></td>
<td><p>Mit Compliance-eDiscovery können Sie Postfachdaten in Ihrer gesamten Exchange-Organisation durchsuchen, eine Vorschau der Suchergebnisse anzeigen und diese in ein Discoverypostfach kopieren.</p></td>
<td><p><a href="in-place-ediscovery-exchange-2013-help.md">Compliance-eDiscovery</a></p></td>
</tr>
<tr class="odd">
<td><p>Journale</p></td>
<td><p>Mithilfe der Aufzeichnung eingehender und ausgehender E-Mail-Kommunikation in Journalen kann Ihre Organisation rechtlichen, regulatorischen und organisatorischen Auflagen genügen. Bei der Planung von Nachrichtenaufbewahrung und Richtlinientreue ist es wichtig zu wissen, was Journale sind, wie sie in die Konformitätsrichtlinien Ihrer Organisation passen und wie Exchange 2013 Ihnen bei der Sicherung von Nachrichten hilft, die in einem Journal erfasst sind.</p></td>
<td><p><a href="journaling-exchange-2013-help.md">Journale</a></p></td>
</tr>
<tr class="even">
<td><p>Transportregeln</p></td>
<td><p>Mithilfe von Transportregeln können Sie nach bestimmten Bedingungen für Nachrichten suchen, die Ihre Organisation durchlaufen, und anschließend geeignete Aktionen für diese Nachrichten ausführen. Mit Transportregeln können Sie Messagingrichtlinien auf E-Mails anwenden, Nachrichten sichern, Nachrichtensysteme schützen und Informationsverluste vermeiden.</p></td>
<td><p><a href="mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md">Nachrichtenfluss- oder Transportregeln</a></p></td>
</tr>
<tr class="odd">
<td><p>Verhinderung von Datenverlust (Data Loss Prevention, DLP)</p></td>
<td><p>DLP-Funktionen helfen Ihnen dabei, Ihre vertraulichen Daten zu schützen und Benutzer über Ihre Richtlinien und Vorschriften zu informieren. Mit diesen Funktionen können Sie auch verhindern, dass Benutzer versehentlich vertrauliche Informationen an nicht autorisierte Personen senden. Wenn Sie DLP-Richtlinien konfigurieren, können Sie vertrauliche Daten ermitteln und schützen, indem Sie die Inhalte Ihres Messagingsystems analysieren, das eine Vielzahl von verschiedenen Dateitypen umfasst. Die in Exchange 2013 bereitgestellten DLP-Richtlinienvorlagen basieren auf gesetzlichen Standards z. B. zu personenbezogenen Daten (PII) sowie Datensicherheitsstandards der Kreditkartenbranche (PCI DSS). DLP ist erweiterbar, sodass Sie weitere Richtlinien hinzufügen können, die für Ihre Organisation wichtig sind. Darüber hinaus ermöglicht die neue Funktion der Richtlinientipps Ihnen, Ihre Benutzer über mögliche Richtlinienverletzungen zu informieren, bevor vertrauliche Daten gesendet werden.</p></td>
<td><p><a href="technical-overview-of-dlp-data-loss-prevention-in-exchange.md">Verhinderung von Datenverlust</a></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung von Informationsrechten (Information Rights Management, IRM)</p></td>
<td><p>Die Verwaltung von Informationsrechten stellt einen beständigen Online- und Offlineschutz für E-Mails und E-Mail-Anlagen unter Verwendung der Active Directory-Rechteverwaltungsdienste (AD RMS) bereit.</p></td>
<td><p><a href="information-rights-management-exchange-2013-help.md">Verwaltung von Informationsrechten</a></p></td>
</tr>
<tr class="odd">
<td><p>S/MIME</p></td>
<td><p>S/MIME (Secure/Multipurpose Internet Mail Extensions) ermöglicht Personen, die Office 365-Postfächer besitzen und Exchange 2013 und Exchange Online nutzen, vertrauliche Informationen durch das Senden signierter und verschlüsselter E-Mail innerhalb ihrer Organisation zu schützen. Administratoren können S/MIME für Office 365-Postfächer aktivieren, indem sie Benutzerzertifikate zwischen Office 365 und dem lokalen Server synchronisieren und dann die S/MIME-Unterstützung in Outlook Online konfigurieren.</p></td>
<td><p><a href="s-mime-for-message-signing-and-encryption-exchange-2013-help.md">S/MIME für die Nachrichtensignierung und -verschlüsselung</a></p></td>
</tr>
<tr class="even">
<td><p>Postfachüberwachungsprotokollierung</p></td>
<td><p>Da Postfächer vertrauliche und für das Unternehmen zentrale Informationen sowie personenbezogene Informationen enthalten können, ist es wichtig, zu verfolgen, wer sich an den Postfächern in Ihrer Organisation anmeldet und welche Aktionen ausgeführt werden. Eine besondere Rolle spielt hierbei die Verfolgung des Postfachzugriffs durch Benutzer, die nicht mit dem Postfachbesitzer identisch sind (sogenannte Stellvertretungsbenutzer). Mithilfe der Postfachüberwachungsprotokollierung können Sie den durch Postfachbesitzer, Stellvertretungen (einschließlich Administratoren mit vollständigen Postfachzugriffsberechtigungen) und Administratoren erfolgten Postfachzugriff protokollieren.</p></td>
<td><p><a href="mailbox-audit-logging-exchange-2013-help.md">Überwachungsprotokollierung von Postfächern</a></p>
<p><a href="exchange-auditing-reports-exchange-2013-help.md">Exchange-Überwachungsberichte</a></p></td>
</tr>
<tr class="odd">
<td><p>Administratorüberwachungsprotokollierung</p></td>
<td><p>Administrator-Überwachungsprotokolle ermöglichen es Ihnen, Änderungen zu protokollieren, die von Administratoren an der Exchange-Server- und Organisationskonfiguration und an Exchange-Empfängern vorgenommen werden. Sie können die Überwachungsprotokollierung in Ihren Prozess zur Änderungssteuerung einbinden, um Änderungen sowie den Zugriff auf die Konfiguration und Empfänger zum Nachweis der Richtlinientreue nachzuverfolgen.</p></td>
<td><p><a href="administrator-audit-logging-exchange-2013-help.md">Administratorüberwachungsprotokollierung</a></p></td>
</tr>
</tbody>
</table>

