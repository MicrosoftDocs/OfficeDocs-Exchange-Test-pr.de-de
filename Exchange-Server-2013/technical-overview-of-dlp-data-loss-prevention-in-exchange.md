---
title: 'Verhinderung von Datenverlust: Exchange 2013 Help'
TOCTitle: Verhinderung von Datenverlust
ms:assetid: 7c8ed3c1-ca91-4d9b-b16b-0a2b8ac89730
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150527(v=EXCHG.150)
ms:contentKeyID: 50474871
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verhinderung von Datenverlust

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Informationen zu DLP-Richtlinien in Exchange Server 2013 und Exchange Online, einschließlich Inhalt und Informationen zum Testen von diesen. Des Weiteren erhalten Sie hier Informationen zu einem neuen Feature in Exchange DLP.

Die Verhinderung von Datenverlust (Data Loss Prevention, DLP) ist ein wichtiger Aspekt in Messagingsystemen von Unternehmen, da E-Mails in sehr hohem Maß in der geschäftskritischen Kommunikation verwendet werden, die häufig vertrauliche Daten umfasst. DLP-Funktionen vereinfachen die Verwaltung von vertraulichen Daten erheblich und tragen so dazu bei, die Anforderungen an die Richtlinientreue für solche Daten einzuhalten und die Verwendung dieser Daten in E-Mails zu verwalten, ohne die Produktivität der Benutzer einzuschränken. Sehen Sie sich das folgende Video an, um einen konzeptionellen Überblick über DLP zu erhalten.

> [!VIDEO https://www.microsoft.com/de-de/videoplayer/embed/31f2b48e-93ed-4be3-b46d-e7230c0fed8f]

DLP-Richtlinien sind einfache Pakete mit Bedingungen, die aus Transportregeln, Aktionen und Ausnahmen zusammengestellt sind, die Sie in der Exchange-Verwaltungskonsole erstellen und dann aktivieren, damit E-Mails und Anhänge gefiltert werden. Sie können eine DLP-Richtlinie erstellen, sie aber zunächst nicht aktivieren. Dadurch können Sie Ihre Richtlinien testen, ohne die Nachrichtenübermittlung zu beeinträchtigen. DLP-Richtlinien können die umfassenden Funktionen vorhandener Transportregeln nutzen. In Microsoft Exchange Server 2013 und Exchange Online wurden viele neue Arten von Transportregeln erstellt, um neue DLP-Funktionen bereitzustellen. Ein wichtiges neues Feature bei Transportregeln ist eine neue Methode zum Klassifizieren vertraulicher Informationen, die in die Verarbeitung des Nachrichtenflusses integriert werden kann. Diese neue DLP-Funktion führt eine eingehende Inhaltsanalyse anhand von Schlüsselwortübereinstimmungen, Wörterbuchübereinstimmungen, regulären Ausdrücken sowie anderen Untersuchungsmethoden aus, um Inhalte zu ermitteln, die die DLP-Richtlinien der Organisation verletzen. Mit dieser neuesten Version von Exchange Online und Exchange 2013 SP1 Add [Dokumentfingerabdrücke](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/document-fingerprinting) können Sie sensible Information in Standardformularen ermitteln. Weitere Informationen zu Transportregeln finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange 2013) oder [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online) und [Integrieren von Regeln für vertrauliche Informationen in Transportregeln](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/integrate-sensitive-information-rules). Sie können die DLP-Richtlinien auch über Cmdlets in der Exchange-Verwaltungsshell verwalten. Weitere Informationen zu Cmdlets für Richtlinien und Richtlinientreue finden Sie unter [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\)).

Zusätzlich zu den anpassbaren DLP-Richtlinien können Sie auch E-Mail-Absender informieren, dass sie möglicherweise eine Ihrer Richtlinien verletzen. Dies ist sogar möglich, bevor die Absender eine Richtlinien verletzende Nachricht senden. Konfigurieren Sie dazu Richtlinientipps. Richtlinientipps funktionieren ähnlich wie E-Mail-Infos und können so konfiguriert werden, dass im Microsoft Outlook 2013-Client ein Hinweis mit Informationen über eine mögliche Richtlinienverletzung angezeigt wird, wenn ein Benutzer eine Nachricht erstellt. In der neuesten Version von Exchange Online und in Exchange 2013 SP1 werden Richtlinieninfos auch in Outlook Web App und OWA für Geräte angezeigt. Weitere Informationen finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).


> [!NOTE]
> Exchange Online: DLP ist ein Premium-Feature, für das ein Abonnement des Typs Exchange Online (Plan 2) erforderlich ist. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=286154">Exchange Online-Lizenzierung</A>.<BR>Exchange 2013: DLP ist ein Premium-Feature, für das eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) erforderlich ist. Weitere Informationen zu Clientzugriffslizenzen und zur Serverlizenzierung finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=237292">Exchange Server-Lizenzierung</A>.<BR><STRONG>Exchange Enterprise-CAL mit Diensten:</STRONG> Es gibt einen Unterschied im Verhalten, den Sie behalten sollten, wenn Sie ein Kunde von Exchange Enterprise-CAL mit Diensten und einer Hybridbereitstellung sind und Postfächer haben, die sich lokal oder auch in Exchange Online befinden. In Exchange Online gelten DLP-Richtlinien. Aus diesem Grund gelten für Nachrichten von einem lokalen Benutzer zu einem anderen lokalen Benutzer keine DLP-Richtlinien, da die Nachricht die lokale Infrastruktur nicht verlässt.



Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit DLP gibt? Weitere Informationen finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md) (Exchange 2013) oder [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\)) (Exchange Online).

**Inhalt**

Einrichten von Richtlinien zum Schutz vertraulicher Daten

Arten von vertraulichen Informationen in DLP-Richtlinien

Erkennen von vertraulichen Informationen und herkömmliche Nachrichtenklassifikation

Sensible Daten mit Dokument Fingerprinting erkannt

Richtlinientipps zur Benachrichtigung der Benutzer über die Erwartungen hinsichtlich vertraulicher Inhalte

Informationen zu über DLP verarbeiteten Nachrichten

Installationsvoraussetzungen

Weitere Informationen

## Einrichten von Richtlinien zum Schutz vertraulicher Daten

Mit den Funktionen zur Verhinderung von Datenverlust können Sie verschiedene Kategorien vertraulicher Informationen ermitteln und überwachen, die Sie im Rahmen Ihrer Richtlinienbedingungen definiert haben, z. B. Personalausweis- oder Kreditkartennummern. Sie können entweder selbst benutzerdefinierte Richtlinien und Transportregeln erstellen oder die vordefinierten DLP-Richtlinienvorlagen verwenden, die von Microsoft für den schnellen Einstieg bereitgestellt werden. Weitere Informationen zu den integrierten Richtlinienvorlagen finden Sie unter [In Exchange bereitgestellte DLP-Richtlinienvorlagen](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/dlp-policy-templates). Eine *Richtlinienvorlage* umfasst eine Reihe von Bedingungen, Regeln und Aktionen, mit denen Sie eine DLP-Richtlinie zur Untersuchung von Nachrichten erstellen und speichern können. Bei den Richtlinienvorlagen handelt es sich um Modelle, aus denen Sie Regeln auswählen oder die Sie mit eigenen Regeln anpassen können, um eine Richtlinie zu erstellen, die Ihre Anforderungen an die Verhinderung von Datenverlust erfüllt.

Ihnen stehen drei verschiedene Methoden zur Verfügung, um mit der Verwendung von DLP-Richtlinien zu beginnen:

1.  **Wenden Sie eine von Microsoft bereitgestellte vorgefertigte Vorlage an.**   Die schnellste Möglichkeit, um mit der Verwendung von DLP-Richtlinien zu beginnen, ist die Erstellung und Implementierung einer neuen Richtlinie anhand einer Vorlage. Dies erspart Ihnen die Mühe, einen vollständig neuen Satz an Regeln erstellen zu müssen. Sie müssen wissen, welche Datentypen geprüft werden sollen und welche Vorschriften zur Richtlinientreue eingehalten werden müssen. Sie müssen auch die Vorgaben Ihrer Organisation hinsichtlich der Verarbeitung solcher Daten kennen. Weitere Informationen finden Sie unter [In Exchange bereitgestellte DLP-Richtlinienvorlagen](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/dlp-policy-templates) und [Erstellen einer DLP-Richtlinie aus einer Vorlage](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/create-dlp-policy-from-template).

2.  **Importieren Sie eine vordefinierte Richtliniendatei von einer Quelle außerhalb Ihrer Organisation.**   Sie können Richtlinien importieren, die außerhalb Ihrer Messagingumgebung von unabhängigen Softwareanbietern erstellt wurden. Auf diese Weise können Sie die DLP-Lösung erweitern und an Ihre geschäftlichen Anforderungen anpassen. Weitere Informationen finden Sie unter [Richtlinienvorlagen von Microsoft-Partnern](policy-templates-from-microsoft-partners-exchange-2013-help.md), [Definition eigener DLP-Vorlagen und Informationstypen](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md) und [Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md).

3.  **Erstellen Sie eine benutzerdefinierte Richtlinie ohne bereits vorhandene Bedingungen.**   Ihr Unternehmen hat möglicherweise spezielle Anforderungen an die Überwachung bestimmter Datentypen, die bekanntermaßen in Messagingsystemen existieren. Sie können selbst eine benutzerdefinierte Richtlinie erstellen, um die spezifischen Messagingdaten in Ihrer Organisation zu überprüfen und geeignete Aktionen auszuführen. Sie müssen die Anforderungen und Einschränkungen der Umgebung kennen, in der die DLP-Richtlinie erzwungen werden soll, um eine solche benutzerdefinierte Richtlinie zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten DLP-Richtlinie](create-a-custom-dlp-policy-exchange-2013-help.md).

Nachdem Sie eine Richtlinie hinzugefügt haben, können Sie die enthaltenen Regeln prüfen und ändern, die Richtlinie inaktiv setzen oder die Richtlinie vollständig entfernen. Die Verfahren für diese Aktionen werden im Thema [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md) beschrieben.

## Arten von vertraulichen Informationen in DLP-Richtlinien

Wenn Sie DLP-Richtlinien erstellen oder ändern, können Sie Regeln verwenden, die eine Überprüfung auf vertrauliche Daten einschließen. Im Thema [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md) werden die Arten von vertraulichen Informationen beschrieben, die Sie in Ihren Richtlinien verwenden können. Sie können die Bedingungen Ihrer Richtlinien – z. B. wie oft ein Element gefunden werden muss, damit eine Aktion ausgeführt wird, oder welche Aktion ausgeführt werden soll – benutzerdefiniert anpassen, um die spezifischen Richtlinienanforderungen in Ihrer Organisation zu erfüllen. Weitere Informationen zum Erstellen von DLP-Richtlinien finden Sie unter [Erstellen einer benutzerdefinierten DLP-Richtlinie](create-a-custom-dlp-policy-exchange-2013-help.md). Weitere Informationen zu allen verfügbaren Transportregeln finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange 2013) oder [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online).

Damit Sie die Regeln in Bezug auf vertrauliche Daten einfacher verwenden können, stellt Microsoft Richtlinienvorlagen bereit, die bereits einige Arten vertraulicher Informationen beinhalten. Sie können nicht für alle hier aufgeführten Arten von vertraulichen Informationen Bedingungen zu den Richtlinienvorlagen hinzufügen, da die Vorlagen für diejenigen Datentypen entworfen wurden, die in Ihrer Organisation in Zusammenhang mit der Richtlinientreue wahrscheinlich am häufigsten untersucht werden müssen. Weitere Informationen zu den vordefinierten Vorlagen finden Sie unter [In Exchange bereitgestellte DLP-Richtlinienvorlagen](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/dlp-policy-templates). Sie können eine Vielzahl von DLP-Richtlinien für Ihre Organisation erstellen und aktivieren, sodass viele verschiedene Arten von Informationen untersucht werden. Sie können auch DLP-Richtlinien erstellen, die nicht auf vorhandenen Vorlagen basieren. Informationen dazu, wie Sie eine solche Richtlinie erstellen, finden Sie unter [Erstellen einer benutzerdefinierten DLP-Richtlinie](create-a-custom-dlp-policy-exchange-2013-help.md). Weitere Informationen über Arten von vertraulichen Informationen finden Sie unter [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md).

## Sensible Daten mit Dokument Fingerprinting erkannt

Mit Exchange 2013 SP1 und der neuesten Version von Exchange Online können Sie [Dokumentfingerabdrücke](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/document-fingerprinting) verwenden, um sensible Informationsarten auf der Grundlage eines Standardformulars problemlos zu erstellen. Informationen zum Schützen von Formulardaten finden Sie unter [Schutz von Formulardaten durch Dokumentfingerabdrücke](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/protect-data-with-fingerprinting).

## Richtlinientipps zur Benachrichtigung der Benutzer über die Erwartungen hinsichtlich vertraulicher Inhalte

Sie können Richtlinientipp-Benachrichtigungen verwenden, um E-Mail-Absender über mögliche Probleme mit der Richtlinientreue zu informieren, während diese eine Nachricht erstellen. Wenn Sie einen Richtlinientipp in einer DLP-Richtlinie konfigurieren, wird die Benachrichtigung nur angezeigt, wenn ein Element in der E-Mail des Absenders die in der Richtlinie festgelegten Bedingungen erfüllt. Richtlinientipps ähneln den E-Mail-Infos, die in Microsoft Exchange 2010 eingeführt wurden. Weitere Informationen finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).

## Erkennen von vertraulichen Informationen und herkömmliche Nachrichtenklassifikation

Exchange 2013 und Exchange Online bieten gegenüber der herkömmlichen Nachrichtenklassifikation eine neue Methode zur Verwaltung von Nachrichtendaten und Anhängen. Ein entscheidender Vorteil der DLP-Lösung ist die Möglichkeit, vertrauliche Inhalte ordnungsgemäß identifizieren zu können, die für die Organisation, für rechtliche Anforderungen, in der Geografie oder für andere geschäftliche Anforderungen einzigartig sind. Exchange 2013 ermöglicht dies durch eine neue Architektur für die eingehende Inhaltsanalyse in Kombination mit Erkennungskriterien, die Sie durch die Regeln in Ihren DLP-Richtlinien festlegen. Die Verhinderung von Datenverlust in Exchange 2013 basiert auf der Konfiguration des richtigen Satzes an Regeln für vertrauliche Informationen, damit diese Regeln ein hohes Maß an Schutz bieten können und gleichzeitig unnötige Unterbrechungen der Nachrichtenübermittlung durch falsch-positive oder negative Ergebnisse minimieren. Diese Regeltypen, die in der DLP-Lösung für die Erkennung vertraulicher Daten verantwortlich sind, sorgen im Framework aus Transportregeln für die Bereitstellung von DLP-Funktionalität.

Weitere Informationen zu diesen neuen Funktionen finden Sie unter [Integrieren von Regeln für vertrauliche Informationen in Transportregeln](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/integrate-sensitive-information-rules). Die herkömmlichen Felder zur Nachrichtenklassifikation können in Exchange weiterhin auf Nachrichten angewendet werden. Diese Felder lassen sich mit der neuen Funktion zu Erkennung vertraulicher Daten kombinieren und in einer einzigen DLP-Richtlinie zusammen mit der neuen Funktion ausführen. Sie können aber auch getrennt ausgeführt und ausgewertet werden. Weitere Informationen zu den Exchange 2010-Nachrichtenklassifikationen finden Sie in der TechNet-Bibliothek unter [Grundlegendes zur Nachrichtenklassifikation](https://go.microsoft.com/fwlink/?linkid=266612).

## Informationen zu über DLP verarbeiteten Nachrichten

Damit Exchange 2013 Informationen zu Nachrichten und möglichen Regelverletzungen, die durch DLP-Richtlinien ermittelt werden, finden Sie weitere Informationen unter [Anzeigen von DLP-Richtlinienerkennungsberichten](view-dlp-policy-detection-reports-exchange-2013-help.md) und [Erstellen von Schadensberichten für DLP-Richtlinienerkennungen](create-incident-reports-for-dlp-policy-detections-exchange-2013-help.md). Daten in Bezug auf die DLP-Ergebnisse sind eng in Zustellungsberichte integriert, das Nachrichtenverfolgungstool von Exchange 2013.

Weitere Informationen zu Exchange Online finden Sie unter [Anzeigen von DLP-Richtlinienerkennungsberichten](https://technet.microsoft.com/de-de/library/dn904484\(v=exchg.150\)) und [Erstellen von Schadensberichten für die DLP-Richtlinienerkennung](https://technet.microsoft.com/de-de/library/dn904486\(v=exchg.150\)).

## Installationsvoraussetzungen

Exchange 2013 oder Exchange Online muss mit mindestens einem Absenderpostfach konfiguriert sein, um die DLP-Funktionen nutzen zu können. Verhinderung von Datenverlust ist ein Premium-Feature, für das eine Enterprise-Clientzugriffslizenz (Client Access License, CAL) erforderlich ist. Weitere Informationen zu den ersten Schritten mit Exchange 2013 finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md). Weitere Informationen zu den ersten Schritten mit Exchange Online finden Sie unter [Exchange Online](https://technet.microsoft.com/de-de/library/jj200580\(v=exchg.150\)).

## Weitere Informationen

Exchange 2013

  - [Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md)

  - [DLP-Verfahren](dlp-procedures-exchange-2013-help.md)

  - [Anzeigen von DLP-Richtlinienerkennungsberichten](view-dlp-policy-detection-reports-exchange-2013-help.md)

  - [Dokumentfingerabdrücke](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/document-fingerprinting)

  - [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\))

Exchange Online

  - [Sicherheit und Richtlinientreue für Exchange Online](https://technet.microsoft.com/de-de/library/jj200706\(v=exchg.150\))

  - [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\))

  - [Anzeigen von DLP-Richtlinienerkennungsberichten](https://technet.microsoft.com/de-de/library/dn904484\(v=exchg.150\))

  - [Dokumentfingerabdrücke](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/document-fingerprinting)

