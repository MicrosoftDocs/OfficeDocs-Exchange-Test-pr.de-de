---
title: 'Neuerungen bei Transportregeln: Exchange 2013 Help'
TOCTitle: Neuerungen bei Transportregeln
ms:assetid: 0c2fc0b5-3cd2-4d79-aa2b-0c7622ae15a8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150483(v=EXCHG.150)
ms:contentKeyID: 50475002
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Neuerungen bei Transportregeln

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-10-03_

In Microsoft Exchange Server 2013 wurden bei den Transportregeln eine Reihe von Verbesserungen vorgenommen. Dieses Thema bietet eine kurze Übersicht über einige der wichtigsten Änderungen und Verbesserungen. Weitere Informationen zu Transportregeln finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md).

## Unterstützung für DLP-Richtlinien

Mit den DLP-Funktionen (Data Loss Prevention) in Exchange 2013 können Organisationen die unbeabsichtigte Offenlegung vertraulicher Daten verhindern. Transportregeln wurden aktualisiert und unterstützen nun die Erstellung von Regeln, um DLP-Richtlinien zu ergänzen und zu erzwingen. Weitere Informationen zur DLP-Unterstützung in Transportregeln finden Sie in den folgenden Themen:

[Integrieren von Regeln für vertrauliche Informationen in Transportregeln](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/integrate-sensitive-information-rules)

[Verhinderung von Datenverlust](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)

## Neue Prädikate und Aktionen

Die Funktionalität von Transportregeln wurde durch neue Prädikate und Aktionen erweitert. Jedes der unten aufgeführten Prädikate kann beim Erstellen von Transportregeln als Bedingung oder Ausnahme verwendet werden.

Einzelheiten zur Verwendung dieser neuen Prädikate und Aktionen finden Sie unter [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md) und [Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md).

## Neue Prädikate

  -  **AttachmentExtensionMatchesWords**   Dieses Prädikat wird zum Ermitteln von Anlagen mit bestimmten Erweiterungen verwendet.

  -  **AttachmentHasExecutableContent**   Dieses Prädikat wird zum Ermitteln von Anlagen mit bestimmten ausführbaren Inhalten verwendet.

  -  **HasSenderOverride** Dieses Prädikat wird zum Ermitteln von Nachrichten verwendet, deren Absender eine DLP-Richtlinieneinschränkung außer Kraft gesetzt hat.

  -  **MessageContainsDataClassifications**   Dieses Prädikat wird zum Ermitteln vertraulicher Informationen im Nachrichtentext und in den Anlagen verwendet. Eine Liste mit den verfügbaren Datenklassifikationen finden Sie unter [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md).

  -  **MessageSizeOver**   Dieses Prädikat wird zum Ermitteln von Nachrichten verwendet, deren Gesamtgröße mit dem angegebenen Grenzwert identisch ist bzw. diesen überschreitet.

  -  **SenderIPRanges**   Dieses Prädikat wird zum Ermitteln von Nachrichten verwendet, die von einer bestimmten Gruppe aus IP-Adressbereichen gesendet wurden.

## Neue Aktionen

  -  **GenerateIncidentReport**   Diese Aktion generiert einen Vorfallsbericht, der an eine angegebene SMTP-Adresse gesendet wird. Die Aktion verfügt zudem über den Parameter *IncidentReportOriginalMail*, für den zwei Werte zulässig sind: "IncludeOriginalMail" oder "DoNotIncludeOriginalMail".

  -  **NotifySender**   Diese Aktion steuert, wie der Absender einer Nachricht benachrichtigt wird, die gegen eine DLP-Richtlinie verstößt. Sie können den Absender lediglich informieren und die Nachricht weiterleiten, oder Sie können die Nachricht zurückweisen und den Absender entsprechend benachrichtigen.

  -  **StopRuleProcessing**   Diese Aktion hält die Verarbeitung aller nachfolgenden Regeln für die Nachricht an.

  -  **ReportSeverityLevel**   Diese Aktion legt den angegebenen Schweregrad im Vorfallsbericht fest. Für diese Aktion sind die folgenden Werte zulässig: "Informational", "Low", "Medium", "High" und "Off".

  -  **RouteMessageOutboundRequireTLS**   Bei dieser Aktion ist eine TLS-Verschlüsselung (Transport Layer Security) erforderlich, wenn die Nachricht an einen externen Empfänger weitergeleitet wird. Wenn die TLS-Verschlüsselung nicht unterstützt wird, wird die Nachricht zurückgewiesen und nicht übermittelt.

## Weitere Änderungen bei Transportregeln

  - **Unterstützung der erweiterten Syntax regulärer Ausdrücke**   Die Transportregeln in Exchange 2013 basieren auf der Microsoft .NET Framework-RegEx-Funktionalität und unterstützen nun eine erweiterte Syntax für reguläre Ausdrücke.

  - **Aufruf des Transportregel-Agents**   Eine wichtige Änderung der Architektur in Exchange 2013 für Transportregeln ist, dass der Transportregel-Agent nun bei "onResolvedMessage" aufgerufen wird. In früheren Exchange-Versionen wurde der Regel-Agent bei "OnRoutedMessage" aufgerufen. Durch diese Änderung konnten neue Aktionen (z. B. das Voraussetzen einer TLS-Verschlüsselung) hinzugefügt werden, mit denen die Art der Weiterleitung für eine Nachricht geändert werden kann. Weitere Informationen zur Architektur der Transportregeln in Exchange 2013 finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md).

  - **Detaillierte Informationen zu Transportregeln in Nachrichtenverfolgungsprotokollen**   In den Nachrichtenverfolgungsprotokollen sind nun ausführliche Informationen zu Transportregeln enthalten. Dies umfasst u. a., welche Regeln für eine bestimmte Nachricht ausgelöst wurden, sowie die Aktionen, die aufgrund der Verarbeitung dieser Regeln ausgeführt wurden.

  - **Neue Funktion zur Regelüberwachung**Exchange 2013 überwacht konfigurierte Transportregeln und berechnet die Kosten der Ausführung dieser Regeln sowohl bei der Erstellung der Regel als auch beim normalen Betrieb. Exchange kann Warnungen für Regeln ermitteln und generieren, die Verzögerungen bei der E-Mail-Übermittlung zur Folge haben.

