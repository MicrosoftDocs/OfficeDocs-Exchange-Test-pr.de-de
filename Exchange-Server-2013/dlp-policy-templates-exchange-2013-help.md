---
title: 'DLP-Richtlinienvorlagen: Exchange 2013 Help'
TOCTitle: DLP-Richtlinienvorlagen
ms:assetid: c7b1a8e4-30d9-4409-85c5-f85ae023737d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657730(v=EXCHG.150)
ms:contentKeyID: 50476671
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DLP-Richtlinienvorlagen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-14_

Sie können DLP-Richtlinienvorlagen (Data Loss Prevention, Verhinderung von Datenverlust) verwenden, um mit der Erstellung Ihrer DLP-Lösung in Microsoft Exchange 2013 zu beginnen. Eine DLP-Richtlinienvorlage ist ein Modell für eine Richtlinie. Sie können eine Vorlage auswählen, um mit der Erstellung einer eigenen angepassten DLP-Richtlinie zu beginnen. Innerhalb der DLP-Richtlinie können Sie die Regeln anpassen, um sicherzustellen, dass sie Ihre Geschäftsanforderungen an die Verhinderung von Datenverlust erfüllt. Verschiedene Richtlinienvorlagen werden von Microsoft bereitgestellt. Sie stellen aber nicht die einzige Möglichkeit dar, eine Lösung für die Verhinderung von Datenverlust in Exchange zu implementieren.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit DLP-Richtlinienvorlagen gibt? Weitere Informationen finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md).

**Inhalt**

Erweitern der Vorlagen und Informationstypen entsprechend Ihrer Anforderungen

Erstellen eigener neuer DLP-Richtlinienvorlagen oder eigener Typen vertraulicher Informationen in einem Klassifizierungsregelpaket

Einbinden der DLP-Funktionalität in vorhandene Transportregeln

Verwenden der von Microsoft erstellten DLP-Richtlinien

Weitere Informationen

## Erweitern der Vorlagen und Informationstypen entsprechend Ihrer Anforderungen

Sie können Definitionen vertraulicher Inhalte und Richtlinienvorlagen von Microsoft-Partnern oder aus von Ihnen selbst entwickelten Dateien als eine Ergänzung der DLP-Richtlinienvorlagen, Informationstypen und Regeln, die bereits in Exchange 2013 vorhanden sind, einbinden. Hier werden verschiedene Möglichkeiten vorgestellt, nach denen Sie Ihren eigenen DLP-Inhalt hinzufügen und die DLP-Funktionalität erweitern können. Die bereits von Microsoft bereitgestellten Vorlagen sind eine bequeme Methode, mit der Entwicklung einer DLP-Lösung zu beginnen. Um die DLP-Features mit Ihren eigenen DLP-Richtlinienvorlagendateien zu erweitern, müssen Sie die XML-Schemaanforderungen für Richtlinienvorlagen verstehen, die unabhängig von Exchange erstellt werden. Weitere Informationen zu den Cmdlets in der Exchange-Verwaltungsshell, die mit DLP-Richtlinienvorlagen in Zusammenhang stehen, finden Sie in den Abschnitten zu `Get-DlpPolicyTemplate`-Cmdlets unter [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\)). Darüber hinaus können Sie eigene Typen vertraulicher Inhalte erstellen, sobald Sie das Format und das Verfahren für deren Einbindung kennen. Weitere Informationen zu den Cmdlets in der Exchange-Verwaltungsshell, die mit DLP-Richtlinienvorlagen in Zusammenhang stehen, finden Sie in den Abschnitten zu `Get-ClassificationRuleCollection`-Cmdlets unter [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\)).


> [!WARNING]
> Sie sollten Ihre DLP-Richtlinien im Testmodus aktivieren, bevor Sie sie in der Produktionsumgebung durchsetzen. Während dieser Tests empfehlen wir, dass Sie Beispielbenutzerpostfächer konfigurieren und Testnachrichten senden, die Ihre Testrichtlinien aufrufen, um die Ergebnisse zu bestätigen.



## Erstellen eigener neuer DLP-Richtlinienvorlagen oder eigener Typen vertraulicher Informationen in einem Klassifizierungsregelpaket

Sie können eine DLP-Richtlinienvorlagendatei unabhängig von Exchange erstellen, die der speziellen von Microsoft bereitgestellten XML-Schemadefinition entspricht, und dann die Datei in Ihr System importieren, um daraus DLP-Richtlinien zu erstellen. Indem Sie Ihre eigenen Vorlagendateien erstellen, können Sie ein eigenes Modell für DLP-Richtlinien erstellen, das von Microsoft noch nicht zur Verfügung gestellt wurde. Dies unterscheidet sich von der Erstellung einer DLP-Richtlinie mit der Exchange-Verwaltungskonsole, bei der üblicherweise verfügbare Richtlinienvorlagen verwendet werden. Wenn Sie eine Richtlinienvorlage unabhängig von Exchange erstellen, müssen Sie sie importieren, bevor Sie damit Nachrichten überprüfen können. Sie können auch eigene Definitionen vertraulicher Informationen erstellen, um die von Microsoft in Exchange definierten zu ergänzen. Es gibt eine gesonderte XML-Schemadefinition für DLP-Richtlinienvorlagendateien und Klassifikationsregelpakete. Lesen Sie für einen Einstieg in die Thematik folgende Informationen:

  -  
    [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

  -  
    [Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

## Einbinden der DLP-Funktionalität in vorhandene Transportregeln

Sie können die DLP-Erkennungsfunktionen in herkömmliche Transportregeln einbinden, ohne eine neue DLP-Richtlinie zu erstellen. Wenn Sie in einer früheren Version von Exchange einen komplexen Regelsatz erstellt haben und ihn in Exchange 2013 duplizieren oder die Erkennung vertraulicher Informationen hinzufügen möchten, können Sie den Editor für Transportregeln in der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell zum Einbinden dieser beiden Features verwenden. Lesen Sie für einen Einstieg in die Thematik folgende Informationen:

  -  
    [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange Server 2013)

  -  
    [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online)

  -  
    [Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md)
    
    [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\))

## Verwenden der von Microsoft erstellten DLP-Richtlinien

Zahlreiche DLP-Richtlinien werden von Microsoft bereitgestellt. Sie stellen die einfachste Möglichkeit dar, mit der Erstellung einer DLP-Lösung zu beginnen, die flexibel ist und leicht implementiert werden kann. Sie können die bereitgestellten Richtlinien immer als Ausgangspunkt verwenden und sie an Ihre Anforderungen anpassen. Lesen Sie für einen Einstieg in die Thematik folgende Informationen:

  - [In Exchange bereitgestellte DLP-Richtlinienvorlagen](dlp-policy-templates-supplied-in-exchange-exchange-2013-help.md)

  - [Erstellen einer DLP-Richtlinie aus einer Vorlage](how-to-new-dlp-data-loss-prevention-policy-template.md)

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

