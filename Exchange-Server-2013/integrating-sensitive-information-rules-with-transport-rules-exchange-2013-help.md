---
title: 'Integrieren von Regeln für vertrauliche Informationen in Transportregeln'
TOCTitle: Integrieren von Regeln für vertrauliche Informationen in Transportregeln
ms:assetid: feb014a7-89dd-4f2d-a06d-52806ce435d4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150583(v=EXCHG.150)
ms:contentKeyID: 50474916
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Integrieren von Regeln für vertrauliche Informationen in Transportregeln

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-14_

In Microsoft Exchange können Sie DLP-Richtlinien erstellen, die nicht nur Regeln für herkömmliche Nachrichtenklassifikationen und vorhandene Transportregeln enthalten, sondern diese Regeln zum Schutz vertraulicher Informationen in Nachrichten auch kombinieren. Das vorhandene Transportregelframework stellt zahlreiche Funktionen für die Definition von Nachrichtenrichtlinien bereit, die das gesamte Spektrum weicher bis harter Steuerungsmöglichkeiten abdecken. Beispiele sind:

  - Begrenzen der Interaktionen zwischen Empfängern und Absendern, einschließlich Interaktionen zwischen einzelnen Abteilungen innerhalb einer Organisation.

  - Anwenden separater Richtlinien für die Kommunikation innerhalb und außerhalb einer Organisation.

  - Vermeiden des Ein- oder Ausgangs unangemessener Inhalte in die und aus einer Organisation.

  - Filtern von vertraulichen Informationen.

  - Nachverfolgen oder Archivieren von Nachrichten, die von bestimmten Einzelpersonen gesendet oder empfangen werden.

  - Umleiten von eingehenden und ausgehenden Nachrichten für die Untersuchung vor der Zustellung.

  - Anwenden von Haftungsausschlüssen auf Nachrichten während des Transports innerhalb der Organisation.

Mithilfe von Transportregeln können Sie Messagingrichtlinien auf E-Mail-Nachrichten anwenden, die über die Transportpipeline im Transportdienst auf Postfachservern und Edge-Transport-Servern geleitet werden. Diese Regeln erlauben Systemadministratoren, Nachrichtenrichtlinien durchzusetzen, die Sicherheit von Nachrichten zu verbessern, den Schutz von Nachrichtensystemen zu unterstützen und unbeabsichtigte Datenverluste zu vermeiden. Weitere Informationen zu Transportregeln finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange Server 2013) oder [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online).

## Regeln für vertrauliche Informationen im Transportregelframework

Regeln für vertrauliche Informationen werden in das Transportregelframework mithilfe einer neu eingeführten, anpassbaren Bedingung integriert: **Wenn die Nachricht vertrauliche Informationen enthält**. Diese Bedingung kann für eine Art oder mehrere Arten von vertraulichen Informationen konfiguriert werden, die in den Nachrichten enthalten sind. Wenn mehrere DLP-Richtlinien oder Regeln in einer Richtlinie mit dieser Bedingung konfiguriert werden, wird die Richtlinie oder Regel erfüllt, sobald eine der Bedingungen zutrifft. Exchange-Richtlinienregeln prüfen den Betreff, den Textkörper und alle Anhänge einer Nachricht. Wenn die Regel für eine dieser Nachrichtenkomponenten zutrifft, werden die entsprechenden Regelaktionen angewendet.

Die Bedingung für vertrauliche Informationen kann mit beliebigen, bereits vorhandenen Transportregeln kombiniert werden, um Nachrichtenrichtlinien zu definieren. In diesen Fällen wird die Bedingung in Verbindung mit anderen Regeln ausgeführt und weist die AND-Semantik auf. Werden beispielsweise zwei verschiedene Bedingungen mithilfe einer AND-Anweisung miteinander addiert, müssen beide Bedingungen zutreffen, damit die entsprechende Aktion angewendet wird. Es können beliebige Transportregelaktionen als Ergebnis von Regeln zum Abgleich des Typs von vertraulichen Informationen kombiniert werden. Es können viele verschiedene Dateitypen vom Transportregelassistenten durchsucht werden, der Nachrichten daraufhin überprüft, ob Transportregeln durchgesetzt werden müssen. Weitere Informationen zu den unterstützten Dateitypen finden Sie unter [Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md) (Exchange Server 2013) oder [Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\)) (Exchange Online).

Die Regeln können auch im Abschnitt mit den Ausnahmen einer Regeldefinition verwendet werden. Ihre Verwendung in der Ausnahmedefinition ist unabhängig von ihrer Verwendung als Bedingung innerhalb der Regel. Auf diese Weise können Sie flexibel Regeln mit der Bedingung definieren, wobei Sie verschiedene, als Teil der Bedingung anzuwendende Typen von Informationen sowie davon abweichende Typen von Informationen in der Bedingung angeben. Dies ermöglicht beispielsweise das Anwenden von Richtlinien, die mit bestimmten Regeln für herkömmliche Nachrichtenklassifikationen übereinstimmen, aber nicht mit anderen Typen vertraulicher Informationen, bevor Aktionen ausgeführt werden, die Sie innerhalb einer Richtlinie definieren.

## Weitere Informationen

[Verhinderung von Datenverlust](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)

[Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)Exchange Server 2013

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))Exchange Online

[Erstellen einer benutzerdefinierten DLP-Richtlinie](create-a-custom-dlp-policy-exchange-2013-help.md)

