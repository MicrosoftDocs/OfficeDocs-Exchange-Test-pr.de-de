---
title: 'In Exchange bereitgestellte DLP-Richtlinienvorlagen: Exchange 2013 Help'
TOCTitle: In Exchange bereitgestellte DLP-Richtlinienvorlagen
ms:assetid: 7e1917ab-1920-4a52-97d1-7dfe2add6198
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150530(v=EXCHG.150)
ms:contentKeyID: 50474872
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# In Exchange bereitgestellte DLP-Richtlinienvorlagen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In Microsoft Exchange Server 2013 und Exchange Online können Sie DLP-Richtlinienvorlagen (Data Loss Prevention, Verhinderung von Datenverlust) als Ausgangspunkt verwenden, um eigene DLP-Richtlinien zu erstellen, die die spezifischen rechtlichen und geschäftlichen Anforderungen Ihrer Organisation erfüllen. Sie können diese Vorlagen entsprechend den Anforderungen Ihrer Organisation bearbeiten.


> [!WARNING]
> Sie sollten Ihre DLP-Richtlinien im Testmodus aktivieren, bevor Sie sie in der Produktionsumgebung ausführen. Während dieser Tests wird empfohlen, dass Sie Beispielbenutzerpostfächer konfigurieren und Testnachrichten senden, die Ihre Testrichtlinien aufrufen, um die Ergebnisse zu bestätigen.<BR>Die Nutzung dieser Richtlinien stellt nicht die Einhaltung von Bestimmungen sicher. Nehmen Sie nach Abschluss der Testphase die erforderlichen Konfigurationsänderungen in Exchange vor, damit die Übertragung von Informationen mit den Richtlinien Ihrer Organisation übereinstimmt. Ein Beispiel: Möglicherweise müssen Sie die TLS-Verschlüsselung für die Kommunikation mit bekannten Geschäftspartnern konfigurieren oder striktere Transportregelaktionen hinzufügen, etwa einen zusätzlichen Rechteschutz für Nachrichten, die einen bestimmten Datentyp enthalten.



## Für DLP verfügbare Vorlagen

In der folgenden Tabelle sind die DLP-Richtlinienvorlagen in Exchange aufgeführt. Weitere Informationen zum Anpassen dieser Vorlagen zur Erstellung von DLP-Richtlinien finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Vorlage</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Finanzdaten – Australien</p></td>
<td><p>Erkennt Informationen, die in Australien üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Kreditkarteninformationen und SWIFT-Codes.</p></td>
</tr>
<tr class="even">
<td><p>Australien: Health Records Act (HRIP Act)</p></td>
<td><p>Erkennt Informationen, die in Australien üblicherweise unter den Health Records and Information Privacy (HRIP) Act fallen. Dazu zählen Informationen wie die Medical Account-Nummer und die Steuernummer (Tax File Number).</p></td>
</tr>
<tr class="odd">
<td><p>Personenbezogene Informationen (PII-Daten) – Australien</p></td>
<td><p>Erkennt Informationen, die in Australien üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Steuernummern (Tax File Number) und Führerscheinnummern.</p></td>
</tr>
<tr class="even">
<td><p>Datenschutzgesetz – Australien</p></td>
<td><p>Erkennt Informationen, die in Australien üblicherweise unter das Datenschutzgesetz fallen. Dazu zählen Informationen wie Führerschein- und Reisepassnummern.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Kanada</p></td>
<td><p>Erkennt Informationen, die in Kanada üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Bankkontonummern und Kreditkarteninformationen.</p></td>
</tr>
<tr class="even">
<td><p>Health Information Act (HIA) – Kanada</p></td>
<td><p>Erkennt Informationen, die in Kanada unter den Health Information Act (HIA) für Alberta fallen. Dazu zählen Informationen wie Reisepassnummern und Gesundheitsinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>Kanada: Personal Health Act (PHIPA) – Ontario</p></td>
<td><p>Erkennt Informationen, die in Kanada unter den Personal Health Information Protection Act (PHIPA) für Ontario fallen. Dazu zählen Informationen wie Reisepassnummern und Gesundheitsinformationen.</p></td>
</tr>
<tr class="even">
<td><p>Personal Health Information Act (PHIA) – Manitoba, Kanada</p></td>
<td><p>Erkennt Informationen, die in Kanada unter den Personal Health Information Act (PHIA) für Manitoba fallen. Dazu zählen Informationen wie Gesundheitsinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>Personal Information Protection Act (PIPA) – Kanada</p></td>
<td><p>Erkennt Informationen, die in Kanada unter den Personal Information Protection Act (PIPA) für British Columbia fallen. Dazu zählen Informationen wie Reisepassnummern und Gesundheitsinformationen.</p></td>
</tr>
<tr class="even">
<td><p>Kanada: Personal Information Protection Act (PIPEDA)</p></td>
<td><p>Erkennt Informationen, die in Kanada unter den Personal Information Protection and Electronic Documents Act (PIPEDA) fallen. Dazu zählen Informationen wie Reisepassnummern und Gesundheitsinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>Personenbezogene Informationen (PII-Daten) – Kanada</p></td>
<td><p>Erkennt Informationen, die in Kanada üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Health Identification-Nummern und Sozialversicherungsnummern.</p></td>
</tr>
<tr class="even">
<td><p>Datenschutzgesetz – Frankreich</p></td>
<td><p>Erkennt Informationen, die in Frankreich üblicherweise unter das Datenschutzgesetz fallen. Dazu zählen Informationen wie die Nummer der Krankenversicherungskarte.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Frankreich</p></td>
<td><p>Erkennt Informationen, die in Frankreich üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Kreditkarteninformationen, Kontoinformationen und Debitkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>Frankreich: Personenbezogene Informationen (PII-Daten)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die in Frankreich üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Reisepassnummern.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Deutschland</p></td>
<td><p>Erkennt Informationen, die in Deutschland üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie EU-Debitkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>Deutschland: Personenbezogene Informationen (PII-Daten)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die in Deutschland üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Führerschein- und Reisepassnummern.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Israel</p></td>
<td><p>Erkennt Informationen, die in Israel üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Bankkontonummern und SWIFT-Codes.</p></td>
</tr>
<tr class="even">
<td><p>Personenbezogene Informationen (PII-Daten) – Israel</p></td>
<td><p>Erkennt Informationen, die in Israel üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie nationale IDs.</p></td>
</tr>
<tr class="odd">
<td><p>Datenschutzgesetz – Israel</p></td>
<td><p>Erkennt Informationen, die in Israel üblicherweise unter den Datenschutz fallen. Dazu zählen Informationen wie Bankkontonummern und internationale IDs.</p></td>
</tr>
<tr class="even">
<td><p>Finanzdaten – Japan</p></td>
<td><p>Erkennt Informationen, die in Japan üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Kreditkarteninformationen, Kontoinformationen und Debitkartennummern.</p></td>
</tr>
<tr class="odd">
<td><p>Japan: Personenbezogene Informationen (PII-Daten)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die in Japan üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Führerschein- und Reisepassnummern.</p></td>
</tr>
<tr class="even">
<td><p>Schutz persönlicher Informationen – Japan</p></td>
<td><p>Erkennt Informationen, die in Japan unter den Schutz persönlicher Informationen fallen. Dazu zählen Informationen wie Melderegistrierungsnummern.</p></td>
</tr>
<tr class="odd">
<td><p>PCI Data Security Standard (PCI DSS)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die dem PCI Data Security Standard (PCI DSS) unterliegen. Dazu zählen Kredit- und Debitkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>Gesetz gegen Internetkriminalität – Saudi-Arabien</p></td>
<td><p>Erkennt Informationen, die in Saudi-Arabien üblicherweise unter das Gesetz gegen Internetkriminalität fallen. Dazu zählen Informationen wie internationale Bankkontonummern und SWIFT-Codes.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Saudi-Arabien</p></td>
<td><p>Erkennt Informationen, die in Saudi-Arabien üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie internationale Bankkontonummern und SWIFT-Codes.</p></td>
</tr>
<tr class="even">
<td><p>Personenbezogene Informationen (PII-Daten) – Saudi-Arabien</p></td>
<td><p>Erkennt Informationen, die in Saudi-Arabien üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie nationale IDs.</p></td>
</tr>
<tr class="odd">
<td><p>Access to Medical Reports Act – Vereinigtes Königreich</p></td>
<td><p>Erkennt Informationen, die im Vereinigten Königreich unter den Access to Medical Reports Act fallen. Dazu zählen Informationen wie Nummern des National Health Service.</p></td>
</tr>
<tr class="even">
<td><p>Datenschutzgesetz – Vereinigtes Königreich</p></td>
<td><p>Erkennt Informationen, die im Vereinigten Königreich unter das Datenschutzgesetz fallen. Dazu zählen Informationen wie Sozialversicherungsnummern.</p></td>
</tr>
<tr class="odd">
<td><p>Finanzdaten – Vereinigtes Königreich</p></td>
<td><p>Erkennt Informationen, die im Vereinigten Königreich üblicherweise als Finanzdaten betrachtet werden. Dazu zählen Informationen wie Kreditkarteninformationen, Kontoinformationen und Debitkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>Online-Verhaltenskodex für persönliche Informationen – U.K.</p></td>
<td><p>Erkennt Informationen, die im Vereinigten Königreich unter den Online-Verhaltenskodex für persönliche Informationen (Personal Information Online Code of Practice) fallen. Dazu zählen Informationen wie Gesundheitsinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>Vereinigtes Königreich: Personenbezogene Informationen (PII)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die im Vereinigten Königreich üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Führerschein- und Reisepassnummern.</p></td>
</tr>
<tr class="even">
<td><p>Richtlinien für Datenschutz und elektronische Kommunikation – UK</p></td>
<td><p>Erkennt Informationen, die im Vereinigten Königreich unter die Richtlinien für Datenschutz und elektronische Kommunikation (Privacy and Electronic Communications Regulations) fallen. Dazu zählen Informationen wie Finanzdaten.</p></td>
</tr>
<tr class="odd">
<td><p>Verbraucherbestimmungen der Federal Trade Commission (FTC) – USA</p></td>
<td><p>Erkennt Informationen, die in den USA unter die Verbraucherbestimmungen der Federal Trade Commission (FTC) fallen. Dazu zählen Informationen wie Kreditkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>USA: Finanzdaten</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die in den USA üblicherweise als Finanzinformationen gewertet werden. Dazu zählen Kreditkarteninformationen, Kontoangaben und Debitkartennummern.</p></td>
</tr>
<tr class="odd">
<td><p>Gramm-Leach-Bliley Act (GLBA) – USA</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die dem Gramm-Leach-Bliley Act (GLBA) unterliegen. Dazu zählen Sozialversicherungs- oder Kreditkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>USA: Health Insurance Act (HIPAA)</p></td>
<td><p>Erkennt Informationen, die in den USA unter den Health Insurance Portability and Accountability Act (HIPAA) fallen. Dazu zählen Informationen wie Sozialversicherungsnummern und Finanzdaten.</p></td>
</tr>
<tr class="odd">
<td><p>Patriot Act – USA</p></td>
<td><p>Erkennt Informationen, die in den USA üblicherweise unter den Patriot Act fallen. Dazu zählen Informationen wie Kreditkartennummern und Steueridentifikationsnummern.</p></td>
</tr>
<tr class="even">
<td><p>USA: Personenbezogene Informationen (PII-Daten)</p></td>
<td><p>Hilft bei der Erkennung von Informationen, die in den USA üblicherweise als personenbezogene Informationen betrachtet werden. Dazu zählen Informationen wie Sozialversicherungs- und Führerscheinnummern.</p></td>
</tr>
<tr class="odd">
<td><p>USA: State Breach Notification Laws</p></td>
<td><p>Erkennt Informationen, die in den USA unter die Gesetze zur Benachrichtigung bei Datenschutzverletzungen (State Breach Notification Laws) fallen. Dazu zählen Informationen wie Sozialversicherungs- und Kreditkartennummern.</p></td>
</tr>
<tr class="even">
<td><p>USA: State Social Security Number Confidentiality Laws</p></td>
<td><p>Erkennt Informationen, die in den USA unter die Gesetze zur Vertraulichkeit von Sozialversicherungsnummern (State Social Security Number Confidentiality Laws) fallen. Dazu zählen Informationen wie Sozialversicherungsnummern.</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Erstellen einer DLP-Richtlinie aus einer Vorlage](how-to-new-dlp-data-loss-prevention-policy-template.md)

[Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

