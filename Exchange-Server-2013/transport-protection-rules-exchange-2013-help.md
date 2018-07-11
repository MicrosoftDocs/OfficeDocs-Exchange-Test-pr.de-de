---
title: 'Transportschutzregeln: Exchange 2013 Help'
TOCTitle: Transportschutzregeln
ms:assetid: 9bd6d049-165e-4e51-a79f-3b8ff409da55
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298166(v=EXCHG.150)
ms:contentKeyID: 50476304
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportschutzregeln

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

E-Mail-Nachrichten und Anlagen enthalten in zunehmendem Maß geschäftswichtige Informationen wie Produktspezifikationen, Dokumente zur Unternehmensstrategie und Finanzdaten oder persönlich identifizierbare Informationen wie Kontaktdetails, Sozialversicherungsnummern, Kreditkartennummern und Personalakten. In zahlreichen Teilen der Welt existiert eine Vielzahl branchenspezifischer und lokaler Bestimmungen, die das Sammeln, Speichern und Veröffentlichen von Informationen, die eine persönliche Identifizierung ermöglichen, regeln.

Damit vertrauliche Daten geschützt werden, erstellen Organisationen Messagingrichtlinien, die einen Leitfaden zum Behandeln dieser Daten bereitstellen. In MicrosoftExchange Server 2013 können Sie mithilfe von Transportschutzregeln diese Messagingrichtlinien umsetzen, indem Nachrichteninhalte untersucht werden, vertrauliche E-Mail-Inhalte verschlüsselt werden und mithilfe der Rechteverwaltung der Zugriff auf die Inhalte gesteuert wird.

Verwaltungsaufgaben im Zusammenhang mit der Verwaltung von IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Transportschutzregeln und AD RMS

Transportschutzregeln versehen Nachrichten mit IRM-Schutz, indem eine Vorlage für [Active Directory Rights Management Services (AD RMS)](https://go.microsoft.com/fwlink/p/?linkid=129823)-Benutzerrechterichtlinien angewendet wird.


> [!NOTE]
> AD&nbsp;RMS ist eine Technologie für den Schutz von Informationen, die mit RMS-aktivierten (Rights Management Service, Rechteverwaltungsdienst) Anwendungen und Clients arbeiten, damit vertrauliche Daten online und offline geschützt sind. Zum Anwenden des IRM-Schutzes bei einer lokalen Exchange-Bereitstellung benötigt Exchange 2013 eine lokale Bereitstellung von AD&nbsp;RMS, die unter Windows Server 2008 oder höher ausgeführt wird.



AD RMS verwendet XML-basierte Richtlinienvorlagen, um es kompatiblen IRM-aktivierten Anwendungen zu ermöglichen, konsistente Schutzrichtlinien anzuwenden. In Windows Server 2008 und höher stellt der AD RMS-Server einen Webdienst bereit, der zum Aufzählen und Abrufen von Vorlagen verwendet werden kann. Im Funktionsumfang von Exchange 2013 ist die Vorlage "Nicht weiterleiten" enthalten.

Wenn die Vorlage "Nicht weiterleiten" auf eine Nachricht angewendet wird, können nur die Empfänger die Nachricht entschlüsseln, die in der Nachricht angegeben sind. Die Empfänger können die Nachricht nicht an beliebige Personen weiterleiten, Inhalte aus der Nachricht kopieren oder die Nachricht drucken.

Es können weitere RMS-Vorlagen in der lokalen AD RMS-Bereitstellung erstellt werden, um den Anforderungen für den Rechteschutz in Ihrer Organisation zu entsprechen.


> [!IMPORTANT]
> Wenn eine Rechterichtlinienvorlage vom AD&nbsp;RMS-Server entfernt wird, müssen Sie sämtliche Transportschutzregeln ändern, die diese entfernte Vorlage verwenden. Wenn eine Transportschutzregel weiterhin versucht, eine bereits entfernte Rechterichtlinienvorlage zu verwenden, kann der AD&nbsp;RMS-Server den Inhalt für keinen der Empfänger lizenzieren, woraufhin dem Absender ein Unzustellbarkeitsbericht zugestellt wird.<BR>In Windows Server 2008 und höher können Vorlagen für Benutzerrechterichtlinien archiviert werden, statt dass sie gelöscht werden. Archivierte Vorlagen können weiterhin zum Lizenzieren von Inhalten verwendet werden. Wenn Sie jedoch eine Transportschutzregel erstellen oder ändern, werden archivierte Vorlagen nicht in die Liste der Vorlagen einbezogen.



Weitere Informationen zum Erstellen von AD RMS-Vorlagen finden Sie unter [Schrittweise Anleitung zum Erstellen und Bereitstellen von Active Directory-Rechteverwaltungsdienste-Vorlagen für Benutzerrechterichtlinien](https://go.microsoft.com/fwlink/p/?linkid=136593).

## Automatischer Schutz mithilfe von Transportschutzregeln

Nachrichten, die wichtige Geschäftsdaten oder Informationen enthalten, die eine persönliche Identifizierung ermöglichen, können mithilfe einer Kombination aus Transportregelbedingungen erkannt werden, einschließlich regulärer Ausdrücke zum Erkennen von Textmustern, z. B. Sozialversicherungsnummern. Organisationen fordern unterschiedliche Schutzgrade für vertrauliche Informationen. Einige Informationen sind möglicherweise auf Mitarbeiter, Vertragsnehmer oder Partner beschränkt, während andere Informationen auf Vollzeitmitarbeiter beschränkt sein können. Der gewünschte Schutzgrad kann mithilfe einer entsprechenden Rechterichtlinienvorlage auf Nachrichten angewendet werden. Beispielsweise können Benutzer Nachrichten oder E-Mail-Anlage als "Firma (vertraulich)" kennzeichnen. Wie in der nachfolgenden Abbildung veranschaulicht, können Sie eine Transportschutzregel erstellen, um Nachrichteninhalte auf die Wörter "Unternehmensintern vertraulich" zu überprüfen und die Nachricht automatisch mithilfe der Verwaltung von Informationsrechten zu schützen.

Weitere Informationen zum Erstellen von Transportschutzregeln zum Erzwingen des Rechteschutzes finden Sie unter [Erstellen einer Transportschutzregel](create-a-transport-protection-rule-exchange-2013-help.md).

## Dauerhafter Schutz von E-Mail-Anlagen

Benutzer senden geschäftswichtige und persönlich identifizierbare Informationen mithilfe gängiger Microsoft Office-Dateiformate wie Microsoft OfficeWord, Excel und PowerPoint. Sämtliche dieser Dateiformate unterstützen den dauerhaften Schutz mithilfe der Verwaltung von Informationsrechten, und Sie können sicherstellen, dass die vertraulichen Geschäftsinformationen und Informationen, die eine persönliche Identifizierung ermöglichen, in diesen Dokumenten ordnungsgemäß geschützt sind. Transportschutzregeln bieten denselben Schutz für E-Mail-Nachrichten und Anlagen in unterstützten Dateiformaten.

## Transportregel-Agent und Verschlüsselungs-Agent

Wenn Sie Nachrichten mithilfe von Transportschutzregeln basierend auf Regelbedingungen mit IRM-Schutz versehen, untersucht der Transportregel-Agent für den Transportdienst Nachrichten. Falls sie allen Bedingungen und keiner Ausnahme entsprechen, wird die Nachricht als "IRM-geschützt" gekennzeichnet. Der Verschlüsselungs-Agent, ein integrierter Transport-Agent, der beim Ereignis **OnRoutedMessage** ausgelöst wird, wendet den IRM-Schutz tatsächlich auf die Nachricht an. Der Verschlüsselungs-Agent wird nur auf Nachrichten angewendet, wenn IRM für interne Nachrichten aktiviert ist. Weitere Informationen zum Aktivieren der Verwaltung von Informationsrechten finden Sie unter [Aktivieren oder Deaktivieren von IRM für interne Nachrichten](enable-or-disable-irm-for-internal-messages-exchange-2013-help.md).

Wenn der Transportdienst neu gestartet wird und die erste Nachricht verarbeitet, die eine IRM-Verschlüsselung erfordert, dann muss der Verschlüsselungs-Agent auf einen AD RMS-Server in der Organisation zugreifen können. Der Agent muss den AD RMS-Server für nachfolgende Nachrichten nicht kontaktieren. Wenn eine Nachricht aufgrund vorübergehender Bedingungen nicht verschlüsselt werden kann, wiederholt Exchange den Vorgang für die Nachricht drei Mal in Intervallen von zehn Minuten. Nach drei Versuchen wird die Nachricht den Empfängern nicht zugestellt, wenn sie nicht verschlüsselt werden konnte. Dem Absender wird ein Unzustellbarkeitsbericht gesendet. Es wird empfohlen, dass Sie Ihre AD RMS-Bereitstellung für eine hohe Verfügbarkeit planen, damit sichergestellt ist, dass der Meldungsfluss nicht betroffen ist.

Wenn Sie Transportschutzregeln verwenden möchten, müssen Sie den Typ der zu schützenden Informationen berücksichtigen und dementsprechend die Erstellung von Regeln planen. In Exchange 2013 gibt es für Transportregeln eine große Vielzahl von Prädikaten zum Untersuchen des Nachrichteninhalts, einschließlich unterstützter Anlagen, Nachrichtenkopfzeilen, Absender- und Empfängeradressen, ihrer Active Directory-Attribute wie Abteilung, Verteilergruppenmitgliedschaft und Hierarchie zwischen Absender und Empfänger. Weitere Einzelheiten zu Transportregelprädikaten in Exchange 2013 finden Sie unter [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md).

Sie müssen auch den Messagingdatenverkehr in Ihrer Organisation und die Anzahl der Nachrichten berücksichtigen, die mithilfe von Transportschutzregeln geschützt werden. Für das Anwenden des IRM-Schutzes auf eine große Anzahl von Nachrichten sind auf dem Postfachserver weitere Ressourcen erforderlich. Darüber hinaus hat das Schützen sehr vieler oder aller Nachrichten negative Auswirkungen auf die Clientumgebung, insbesondere für Benutzer von Microsoft Outlook.

