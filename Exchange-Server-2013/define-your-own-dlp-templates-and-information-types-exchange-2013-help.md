---
title: 'Definition eigener DLP-Vorlagen und Informationstypen: Exchange 2013 Help'
TOCTitle: Definition eigener DLP-Vorlagen und Informationstypen
ms:assetid: f4622dba-3347-4758-b4a2-f01b043c908c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674310(v=EXCHG.150)
ms:contentKeyID: 50477068
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Definition eigener DLP-Vorlagen und Informationstypen

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-01-14_

Sie können von Microsoft Exchange Server 2013 unabhängige Richtlinienvorlagen für die Verhinderung von Datenverlusten (Data Loss Prevention, DLP) als XML-Dateien entwickeln und diese dann mithilfe der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell importieren. In diesem Abschnitt werden das Verfahren und die Details der Erstellung und Feinabstimmung von XML-Dateien für die Verhinderung von Datenverlusten zur Verwendung in einer DLP-Lösung beschrieben. Sie müssen keine eigenen XML-Dateien für die Verhinderung von Datenverlusten entwickeln. In der Exchange-Verwaltungskonsole können Sie vorhandene DLP-Richtlinienvorlagen und Transportregeln zur Überprüfung von Nachrichten anpassen.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit DLP-Richtlinienvorlagen gibt? Weitere Informationen finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md) (Exchange Server 2013) oder [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\)) (Exchange Online).


> [!NOTE]
> Exchange 2013: DLP ist ein Premium-Feature, für das eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) erforderlich ist. Weitere Informationen zu Clientzugriffslizenzen und zur Serverlizenzierung finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</A>.<BR>Exchange Online: DLP ist ein Premium-Feature, für das ein Abonnement des Typs Exchange Online (Plan 2) erforderlich ist. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=286154">Exchange Online-Lizenzierung</A>.




> [!IMPORTANT]
> Eine Empfehlung eines Geschäftsmodells oder Informationen zum Packen von Dateien bzw. Richtlinien zum Bereitstellen von Regeln für vertrauliche Informationen sowie die Erörterung der Verteilung dieser Regeln würde über den Rahmen dieser Dokumentation hinausgehen. In dieser Dokumentation werden auch keine Schutzmechanismen, wie Verschlüsselung, für benutzerdefinierte Regeln oder der Einsatz solcher Regeln behandelt.



## Erweitern der Informationstypen entsprechend Ihren Anforderungen

In den folgenden Abschnitten werden Konzepte und die XML-Schemadefinition beschrieben, die Sie kennen und verstehen müssen, um eigene XML-Dateien für DLP-Richtlinienvorlagen und für Regelpakete vertraulicher Daten zu erstellen, die in Exchange 2013 importiert und als DLP-Richtlinien verwendet werden können.

DLP in Microsoft Exchange unterstützt Sie beim Anwenden von organisationsspezifischen Richtlinien auf vertrauliche Informationen. Ein wesentlicher Faktor für die Stärke einer DLP-Lösung ist die Möglichkeit, vertrauliche und sensible Informationen im Zusammenhang mit der Organisation, gesetzlichen Bestimmungen, der Geografie oder anderen geschäftlichen Aspekten korrekt zu identifizieren. Zwar stellt Microsoft Richtlinienvorlagen und Typen vertraulicher Informationen im Produkt bereit, die für den Anfang ausreichen, aber langfristig ist für Ihre individuellen Geschäftsanforderungen eine benutzerdefinierte Lösung zur Verhinderung von Datenverlusten erforderlich. Microsoft bietet deshalb die Möglichkeit, eigene DLP-Richtlinienvorlagen oder eigene Definitionen für vertrauliche Informationen in Klassifizierungsregelpaketen zu erstellen und zu importieren. Eine präzise DLP-Lösung basiert auf der Konfiguration von exakten Regeln für das Modul zur Erkennung von vertraulichen Informationen, die hohen Schutz bei gleichzeitiger Minimierung falsch positiver und falsch negativer Ergebnisse bieten.

## Entwickeln von eigenen DLP-Richtlinienvorlagen

Sie können eine eigene XML-Datei mit DLP-Richtlinienvorlagen erstellen und importieren. Mit dieser in Exchange vorgesehenen Methode zur Erweiterung der DLP-Lösung können Sie Ihren DLP-Anforderungen entsprechende DLP-Richtlinien erstellen.

Das Verwalten benutzerdefinierter Vorlagen und der damit verbundenen Richtlinien ähnelt dem Verwalten der DLP-Richtlinien, die Sie auf der Basis der von Microsoft bereitgestellten Vorlagen erstellen. In einem typischen DLP-Richtlinienlebenszyklus würden Sie wie folgt vorgehen:

1.  Erstellen Sie Ihre eigene DLP-Richtlinienvorlage, eine benutzerdefinierte XML-Datei. Weitere Informationen finden Sie unter [Entwickeln von Vorlagendateien für DLP-Richtlinien](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

2.  Importieren Sie Ihre benutzerdefinierte Vorlage. Weitere Informationen finden Sie unter [Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md).

3.  Erstellen Sie eine DLP-Richtlinie auf der Basis Ihrer benutzerdefinierten Vorlage. Weitere Informationen finden Sie unter [Erstellen einer DLP-Richtlinie aus einer Vorlage](how-to-new-dlp-data-loss-prevention-policy-template.md).

4.  Aktualisieren Sie Ihre benutzerdefinierte Vorlage, indem Sie die Schritte 1 und 2 wiederholen.

5.  Entfernen Sie Ihre benutzerdefinierte Vorlage. Weitere Informationen finden Sie unter [Remove-DlpPolicyTemplate](https://technet.microsoft.com/de-de/library/jj215739\(v=exchg.150\)).

Weitere Informationen zur XML-Schemadefinition und zu Konzepten im Zusammenhang mit der Entwicklung eigener Vorlagen finden Sie unter [Entwickeln von Vorlagendateien für DLP-Richtlinien](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

## Entwickeln eigener Typen vertraulicher Informationen und der entsprechenden Logik in Klassifizierungsregelpaketen

Sie können eigene Definitionen für vertrauliche Informationen in einem Klassifizierungsregelpaket (einer XML-Datei) verfassen und als Teil Ihrer DLP-Lösung importieren. Das Modul zur Erkennung von vertraulichen Informationen verfügt über Funktionen für eingehende Inhaltsanalysen zur Identifizierung vertraulicher Informationen, wie Kreditkartennummern, Sozialversicherungsnummern und geistiges Eigentum des Unternehmens. Das Modul wird durch konfigurierbare Anweisungen oder Regeln zum Durchsuchen und Analysieren des Inhalts gesteuert. Die Regeln sind in einem Klassifizierungsregelpaket (einem XML-Dokument) gemäß einer standardisierten XML-Schemadefinition für Regelpakete zusammengefasst. Im Folgenden erfahren Sie, wie Sie eigene Typen erstellen.

1.  Erstellen Sie eigene Typen vertraulicher Informationen, eine benutzerdefinierte XML-Datei. Weitere Informationen finden Sie unter [Entwickeln von Regelpaketen für sensible Informationen](technical-description-of-xml-schema-for-dlp-rule-packages.md).

2.  Importieren Sie Ihren Typ vertraulicher Informationen. Weitere Informationen finden Sie unter [New-ClassificationRuleCollection](https://technet.microsoft.com/de-de/library/jj218619\(v=exchg.150\)).

3.  Erstellen Sie eine benutzerdefinierte Vorlage auf der Basis Ihrer Informationstypen. Weitere Informationen finden Sie unter [Entwickeln von Regelpaketen für sensible Informationen](technical-description-of-xml-schema-for-dlp-rule-packages.md).

4.  Aktualisieren Sie Ihre benutzerdefinierte Vorlage, indem Sie die Schritte 1 und 2 wiederholen.

5.  Entfernen Sie Ihre benutzerdefinierte Vorlage. Weitere Informationen finden Sie unter [Remove-ClassificationRuleCollection](https://technet.microsoft.com/de-de/library/jj218670\(v=exchg.150\)).

Weitere Informationen zu Regelpaketen finden Sie unter [Entwickeln von Regelpaketen für sensible Informationen](technical-description-of-xml-schema-for-dlp-rule-packages.md) und [Abgleichen von Methoden und Techniken für Regelpakete](technical-description-of-xsd-rule-matching-for-dlp-rule-packages.md).

## Grundlegendes zu Regeltypen in Regelpaketen

Mit den Regeln in einem Regelpaket wird der Prozess des Erkennens von genau festgelegten Inhaltsmerkmalen konfiguriert, z. B. Regeln zum Suchen einer Führerscheinnummer. Zwei Hauptregeltypen sind verfügbar: Entität und Affinität.

*Entitätsregeln* sind auf genau festgelegte (und oftmals gesetzlich geregelte) Bezeichner, wie US-Sozialversicherungsnummern, ausgerichtet. Eine Entität wird durch eine Sammlung von zählbaren Mustern dargestellt. Ein Muster legt eine Sammlung von Treffern mit einem expliziten, primären Trefferbezeichner fest. Ein Beispiel für eine Entität ist ein Führerschein.

*Affinitätsregeln* sind auf bestimmte Dokumenttypen, wie Unternehmensfinanzberichte, ausgerichtet. Eine Affinität wird als Sammlung von unabhängigen Nachweisen dargestellt. Als Nachweis gilt eine Häufung von erforderlichen Treffern innerhalb einer bestimmten Näherung. Ein Beispiel für Affinität ist das US-Bundesgesetz "Sarbanes-Oxley Act".

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

[New-ClassificationRuleCollection](https://technet.microsoft.com/de-de/library/jj218619\(v=exchg.150\))

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)Exchange Server 2013

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))Exchange Online

[Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

