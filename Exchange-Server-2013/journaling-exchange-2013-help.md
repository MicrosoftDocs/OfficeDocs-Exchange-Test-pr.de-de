---
title: 'Journale: Exchange 2013 Help'
TOCTitle: Journale
ms:assetid: 6a20f207-4485-44ef-b010-ec760eb5165b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998649(v=EXCHG.150)
ms:contentKeyID: 50475901
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Journale

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe der Aufzeichnung eingehender und ausgehender E-Mail-Kommunikation in Journalen kann Ihre Organisation rechtlichen, regulatorischen und organisatorischen Auflagen genügen. Bei der Planung von Nachrichtenaufbewahrung und Richtlinientreue ist es wichtig zu wissen, was Journale sind, wie sie in die Konformitätsrichtlinien Ihrer Organisation passen und wie MicrosoftExchange Server 2013 Ihnen bei der Sicherung von Nachrichten hilft, die in einem Journal erfasst sind.

**Inhalt**

Why journaling is important

Journaling agent

Journal rules

Journal rule replication

Journal reports

Interoperability with Exchange 2010 and Exchange 2007

Troubleshooting

## Warum sind Journale wichtig?

Es ist wichtig, den Unterschied zwischen Journaling- und Datenarchivierungsstrategie zu verstehen:

  - *Journale* bedeuten die Fähigkeit, alle Kommunikationsvorgänge in einer Organisation, einschließlich der E-Mail-Kommunikation, aufzuzeichnen, um sie im Rahmen der Aufbewahrungs- oder der Archivstrategie einer Organisation verwenden zu können. Um eine zunehmende Anzahl behördlicher Auflagen und Anforderungen zur Einhaltung von Vorschriften erfüllen zu können, müssen viele Organisationen die Kommunikationsdatensätze aufbewahren, die beim Ausführen täglicher geschäftlicher Aufgaben durch Mitarbeiter erstellt werden.

  - *Datenarchivierung* bezieht sich auf das Sichern der Daten. Sie werden aus ihrer nativen Umgebung entfernt und an anderer Stelle gespeichert, um die mit der Datenspeicherung einhergehende Last zu reduzieren. Sie können Exchange-Journaling als Tool für Ihre E-Mail-Aufbewahrungs- oder Archivstrategien verwenden.

Obwohl es keine spezielle Vorschriften gibt, die Journale zwingend erfordert, können bestimmte Bedingungen durch die Aufzeichnung in Journalen erfüllt werden. In einigen Finanzsektoren können Führungskräfte beispielsweise für die Forderungen ihrer Mitarbeiter an ihre Kunden haftbar gemacht werden. Ein Vorstandsmitglied kann sich daher entscheiden, ein System einzurichten, bei dem Manager einen Teil der Kommunikation von Mitarbeitern mit Kunden auf regelmäßiger Basis überprüfen. Jedes Quartal überprüfen die Manager die Einhaltung der Vorschriften und genehmigen das Verhalten ihrer Mitarbeiter. Nachdem alle Manager dem Vorstandsmitglied Bericht erstattet haben, meldet dieser der Aufsichtsbehörde die Einhaltung der Vorschriften seitens des Unternehmens. In diesem Beispiel können E-Mails eine Form der Kommunikation zwischen Mitarbeitern und Kunden sein, die Manager überprüfen müssen. Deshalb können Journale verwendet werden, um sämtliche E-Mails von Mitarbeitern mit Kundenkontakt zu erfassen. Zu den weiteren Verfahren der Kundenkommunikation können Faxe und Telefongespräche gehören, die ebenfalls den Bestimmungen unterliegen. Die Fähigkeit, alle Kategorien von Daten in einem Unternehmen in Journalen zu erfassen, ist eine wertvolle Funktion der IT-Architektur.

Die folgende Liste enthält einige der bekannteren US-amerikanischen und internationalen Bestimmungen, bei denen Journale Bestandteil der Strategien für die Einhaltung von Vorschriften sein können:

  - Sarbanes-Oxley Act von 2002 (SOX)

  - Security Exchange Commission Rule 17a-4 (SEC Rule 17 A-4)

  - National Association of Securities Dealers 3010 & 3110 (NASD 3010 & 3110)

  - Gramm-Leach-Bliley Act (Financial Modernization Act)

  - Financial Institution Privacy Protection Act von 2001

  - Financial Institution Privacy Protection Act von 2003

  - Health Insurance Portability and Accountability Act von 1996 (HIPAA)

  - Uniting and Strengthening America by Providing Appropriate Tools Required to Intercept and Obstruct Terrorism Act von 2001 (Patriot Act)

  - Datenschutzrichtlinie der EU (European Union Data Protection Directive, EUDPD)

  - Personal Information Protection Act (Japan)

Zurück zum Seitenanfang

## Journal-Agent

In einer Exchange 2013-Organisation wird sämtlicher E-Mail-Datenverkehr von Postfachservern geroutet. Alle Nachrichten durchlaufen während ihres Lebenszyklus mindestens einen Server, auf dem der Transportdienst installiert ist. Der *Journal-Agent* ist ein auf Richtlinientreue ausgelegter Transport-Agent, der Nachrichten auf Postfachservern verarbeitet. Er wird bei den Ereignissen **OnSubmittedMessage** und **OnRoutedMessage** ausgelöst.


> [!NOTE]
> In Exchange 2013 ist der Journal-Agent ein integrierter Agent. Integrierte Agents sind nicht in der Agent-Liste enthalten, die vom Cmdlet <STRONG>Get-TransportAgent</STRONG> zurückgegeben wird. Weitere Informationen finden Sie unter <A href="transport-agents-exchange-2013-help.md">Transport-Agents</A>.



Exchange 2013 stellt die folgenden Journaloptionen bereit:

  - **Standardjournale**   Standardjournale werden für eine Postfachdatenbank konfiguriert. Dadurch kann der Journal-Agent alle Nachrichten in Journalen erfassen, die an und von Postfächern in einer bestimmten Postfachdatenbank gesendet werden. Wenn alle Nachrichten an alle Empfänger und von allen Absendern in Journalen aufgezeichnet werden sollen, müssen Sie Journale für alle Postfachdatenbanken auf allen Postfachservern in der Organisation konfigurieren.

  - **Premium-Journale**   Mit Premium-Journalen kann der Journal-Agent mithilfe von Journalregeln Journale mit größerer Granularität erstellen. Anstatt alle Postfächer in einer Postfachdatenbank in Journalen aufzuzeichnen, können Sie in Abstimmung auf die Anforderungen Ihrer Organisation Journalregeln konfigurieren, mit denen einzelne Empfänger oder Mitglieder von Verteilergruppen in Journalen erfasst werden. Zur Verwendung der Premium-Journalfunktion müssen Sie eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) besitzen.

Wenn Sie Standardjournale für eine Postfachdatenbank aktivieren, werden diese Informationen in Active Directory gespeichert und vom Journal-Agent gelesen. Ebenso werden Journalregeln, die mithilfe der Premium-Journalfunktion konfiguriert wurden, in Active Directory gespeichert und vom Journal-Agent angewendet. Weitere Informationen zum Konfigurieren von Standard- und Premium-Journalen finden Sie unter [Verwalten des Journalings](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/journaling/manage-journaling).

Zurück zum Seitenanfang

## Journalregeln

Folgende sind wichtige Aspekte von Journalregeln:

  - **Journalregelbereich**   Definiert, welche Nachrichten vom Journal-Agent in einem Journal erfasst werden sollen.

  - **Journalempfänger**   Gibt die SMTP-Adresse des Empfängers an, der in einem Journal erfasst werden soll.

  - **Journalpostfach**   Gibt mindestens ein Postfach an, das zum Sammeln von Journalberichten verwendet wird.

## Journalregelbereich

Mithilfe von Journalregeln können Sie nur interne, nur externe oder sowohl interne als auch externe Nachrichten in einem Journal erfassen. In der folgenden Liste sind diese Bereiche beschrieben:

  - **Nur interne Nachrichten**   Journalregeln, mit denen interne Nachrichten in einem Journal erfasst werden, die zwischen Empfängern innerhalb Ihrer Exchange-Organisation gesendet werden.

  - **Nur externe Nachrichten**   Journalregeln, mit denen externe Nachrichten in einem Journal erfasst werden, die an Empfänger oder von Absendern außerhalb Ihrer Exchange-Organisation gesendet werden.

  - **Alle Nachrichten**   Journalregeln, mit denen unabhängig von der Quelle oder dem Ziel alle Nachrichten in einem Journal erfasst werden, die Ihre Organisation durchlaufen. Dies umfasst Nachrichten, die möglicherweise bereits von Journalregeln in den internen und externen Bereichen verarbeitet wurden.

## Journalempfänger

Durch Angabe der SMTP-Adresse des Empfängers, der im Journal erfasst werden soll, können Sie zielgerichtete Journalregeln implementieren. Beim Empfänger kann es sich um ein Postfach, eine Verteilergruppe, einen E-Mail-Benutzer oder einen Kontakt in Exchange handeln. Diese Empfänger unterliegen möglicherweise besonderen rechtlichen Bestimmungen oder sind in juristische Verfahren involviert, bei denen E-Mails und andere Kommunikationsmittel als Beweismittel erfasst werden. Durch gezielte Auswahl bestimmter Empfänger oder Empfängergruppen können Sie auf einfache Weise eine Journalerfassungsumgebung konfigurieren, die den Prozessen Ihrer Organisation entspricht und rechtliche Bestimmungen und Vorschriften erfüllt. Indem Sie nur bestimmte Empfänger auswählen, deren Nachrichten in einem Journal erfasst werden müssen, können Sie auch den erforderlichen Speicherplatz sowie andere Kosten in Zusammenhang mit der Aufbewahrung großer Datenmengen reduzieren.

Alle Nachrichten, die von den in einer Journalregel angegebenen Empfängern gesendet oder empfangen werden, werden im Journal erfasst. Wenn Sie eine Verteilergruppe als Journalempfänger angeben, werden alle Nachrichten in einem Journal erfasst, die an die Mitglieder oder von den Mitgliedern der Verteilergruppe gesendet werden. Wenn Sie keinen Empfänger angeben, werden alle Nachrichten, die zwischen Empfängern und Absendern ausgetauscht werden, die dem Journalregelbereich entsprechen, im Journal erfasst.

**Unified Messaging-aktivierte Journalempfänger**

Viele Organisationen, die die Journalfunktion implementieren, verwenden möglicherweise auch Unified Messaging (UM), um ihre E-Mail-, Voicemail- und Faxinfrastruktur zu konsolidieren. Möglicherweise wünschen Sie jedoch nicht, dass der Journalvorgang Journalberichte für Nachrichten erzeugt, die von Unified Messaging generiert werden. In diesen Fällen können Sie entscheiden, ob Voicemailnachrichten und Benachrichtigungen über verpasste Anrufe, die von einem Exchange-Server mit dem Unified Messaging-Dienst verarbeitet werden, im Journal erfasst oder ausgelassen werden sollen. Wenn in Ihrer Organisation derartige Nachrichten nicht in einem Journal erfasst werden müssen, können Sie den Festplattenspeicherplatz, der zum Speichern von Journalberichten erforderlich ist, durch Ignorieren dieser Nachrichten verringern.


> [!NOTE]
> Nachrichten, die von einem Unified Messaging-Dienst generierte Faxnachrichten enthalten, werden immer in einem Journal erfasst, auch wenn Sie das Journaling von Unified Messaging-Voicemail und Benachrichtigungen über verpasste Anrufe deaktivieren.



Weitere Informationen zum Aktivieren bzw. Deaktivieren von Voicemailnachrichten und Benachrichtigungen über verpasste Anrufe finden Sie unter [Deaktivieren oder Aktivieren der Journalfunktion für Voicemail und Benachrichtigungen über verpasste Anrufe](disable-or-enable-journaling-of-voice-mail-and-missed-call-notifications-exchange-2013-help.md).

## Journalpostfach

Das Journalingpostfach dient zum Erfassen von Journalberichten. Wie das Journalingpostfach konfiguriert wird, hängt von den Richtlinien in Ihrer Organisation sowie den behördlichen und gesetzlichen Bestimmungen ab. Sie können ein Journalpostfach zum Erfassen der Nachrichten von allen in der Organisation konfigurierten Journalregeln angeben oder verschiedene Journalpostfächer für unterschiedliche Journalregeln oder Journalregelgruppen verwenden.


> [!IMPORTANT]
> Sie können ein Office 365-Postfach nicht als ein Journalpostfach festlegen. Sie können Journalberichte an ein lokales Archivierungssystem oder den Archivierungsdienst eines Drittanbieters senden. In einer Hybridbereitstellung, in der sich Postfächer sowohl auf lokalen Servern als auch in Office&nbsp;365 befinden, können Sie ein lokales Postfach als Journalpostfach für Ihre lokalen und Office&nbsp;365-Postfächer festlegen.




> [!IMPORTANT]
> Journalpostfächer enthalten sehr sensible Informationen. Journalpostfächer müssen geschützt werden, da in ihnen Nachrichten gesammelt werden, die von Empfängern und an Empfänger in Ihrer Organisation gesendet werden. Diese Nachrichten werden möglicherweise in juristischen Verfahren benötigt oder unterliegen gesetzlichen Bestimmungen. Verschiedene Gesetze schreiben vor, dass Nachrichten nicht verändert werden dürfen, bevor sie an eine Untersuchungsbehörde übergeben werden. Es wird empfohlen, dass Sie Richtlinien erstellen, die regeln, wer in der Organisation auf die Journalpostfächer zugreifen kann und dass Sie den Zugriff nur auf die Personen beschränken, die unmittelbaren Bedarf für den Zugriff haben. Beraten Sie sich mit den Rechtsberatern Ihrer Organisation, um sicherzustellen, dass Ihre Journallösung allen Gesetzen und Bestimmungen entspricht, denen die Organisation unterliegt.




> [!IMPORTANT]
> Journalpostfächer sollten Nachrichten bis zu einer Größe zulassen, die gleich der oder größer als die in Ihrer Organisation festgelegte maximale Nachrichtengröße ist. Wenn Sie für die MaxSendSize- und MaxReceiveSize-Parameter für ein Benutzerpostfach Ausnahmen konfiguriert haben, die größer als die grundlegende Einstellung in TransportConfig sind, sollten Sie die MaxSendSize- und MaxReceiveSize-Parameter für das Journalpostfach entsprechend anpassen, damit die an das Journalpostfach gesendeten Nachrichten zugelassen werden, und nicht zurückgewiesen oder in Warteschlange gestellt werden. Für Nachrichten, die vom Journalpostfach zurückgewiesen werden, werden regelmäßig Wiederholungszustellversuche durchgeführt, was zu unnötigem Datenbankwachstum und Verschwendung von Ressourcen führt. Darüber hinaus wird empfohlen, ein alternatives Journalpostfach einzurichten, um zu verhindern, dass Nachrichten nicht zugestellt werden können.



## Alternatives Journalpostfach

Wenn das Journalpostfach nicht verfügbar ist, möchten Sie eventuell nicht, dass unzustellbare Journalberichte in E-Mail-Warteschlangen auf Postfachservern gesammelt werden. Stattdessen können Sie ein alternatives Journalpostfach konfigurieren, in dem diese Journalberichte gespeichert werden. Das alternative Journalpostfach empfängt die Journalberichte als Anlage zu den Unzustellbarkeitsberichten, die generiert werden, wenn das Journalpostfach bzw. der Server, auf dem es sich befindet, die Zustellung des Journalberichts zurückweist oder nicht länger verfügbar ist.

Sobald das Journalingpostfach wieder verfügbar ist, können Sie die Funktion **Erneut senden** von OfficeOutlook verwenden, um die an das Journalingpostfach zu übermittelnden Journalberichte zu senden.

Wenn Sie ein alternatives Journalpostfach konfigurieren, werden alle Journalberichte, die innerhalb Ihrer gesamten Exchange-Organisation zurückgewiesen oder nicht zugestellt werden, an das alternative Journalpostfach übermittelt. Sie müssen deshalb sicherstellen, dass das alternative Journalpostfach und der Postfachserver, auf dem es sich befindet, zahlreiche Journalberichte unterstützen können.


> [!WARNING]
> Wenn Sie ein alternatives Journalpostfach konfigurieren, müssen Sie das Postfach überwachen, um sicherzustellen, dass Postfach und Journalpostfächer nicht gleichzeitig nicht verfügbar sind. Wenn das alternative Journalpostfach nicht verfügbar ist oder gleichzeitig Journalberichte zurückweist, gehen die zurückgewiesenen Journalberichte verloren und können nicht abgerufen werden.



Da in dem alternativen Journalpostfach alle zurückgewiesenen Journalberichte der gesamten Exchange-Organisation gesammelt werden, müssen Sie sicherstellen, dass dadurch nicht gegen Gesetze oder Vorschriften verstoßen wird, denen Ihre Organisation unterliegt. Falls Gesetze oder Vorschriften Ihrer Organisation untersagen, dass Journalberichte, die an verschiedene Journalpostfächer gesendet werden, im selben alternativen Journalpostfach gespeichert werden, können Sie ggf. kein alternatives Journalpostfach konfigurieren. Besprechen Sie sich mit Ihrer Rechtsabteilung, um festzustellen, ob Sie ein alternatives Journalpostfach verwenden dürfen.

Beim Konfigurieren des alternativen Journalpostfachs müssen dieselben Kriterien wie beim Konfigurieren des Journalpostfachs beachtet werden.


> [!IMPORTANT]
> Die alternativen Journalingpostfächer sollten als ein spezielles dediziertes Postfach behandelt werden. Alle Nachrichten, die direkt an das alternative Journalingpostfach gerichtet sind, werden nicht im Journal erfasst.



Zurück zum Seitenanfang

## Replikation von Journalregeln

Journalregeln werden in Active Directory gespeichert und von allen Postfachservern in der Exchange 2013-Organisation angewendet. Wenn Sie eine Journalregel erstellen, ändern oder entfernen, wird diese Änderung auf alle Active Directory-Server in der Organisation repliziert. Alle Postfachserver in der Organisation rufen die aktualisierte Journalregelkonfiguration von den Active Directory-Servern ab und wenden die neuen oder modifizierten Journalregeln an.

Durch Replizieren aller Journalregeln in der gesamten Organisation ermöglicht Exchange 2013 Ihnen das Bereitstellen einer konsistenten Menge von Journalregeln in der gesamten Organisation. Alle Nachrichten, die Ihre Exchange 2013-Organisation durchlaufen, werden den gleichen Journalregeln unterworfen.


> [!IMPORTANT]
> Replikation von Journalregeln innerhalb einer Organisation ist davon abhängig Active Directory Replikation. Zeitpunkt der Replikation zwischen Domänencontrollern Active Directory variiert je nach der Anzahl von Websites in der Organisation sowie die Geschwindigkeit von Hyperlinks und anderen Faktoren außerhalb des Microsoft Exchange-Steuerelements. Berücksichtigen Sie beim Implementieren von Journalregeln in Ihrer Organisation Replikation verzögert. Weitere Informationen zur Replikation Active Directory finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=274904">Einführung in Active Directory-Replikation und Topologie Management Using Windows PowerShell</A>.




> [!IMPORTANT]
> Jeder Postfachserver speichert Informationen zu den Mitgliedern einer Verteilergruppe zwischen, um wiederholte Roundtrips zu Active Directory zu vermeiden. Der erweiterte Gruppencache verringert die Anzahl von Anforderungen, die jeder Postfachserver an einen Active Directory-Domänencontroller senden muss. Standardmäßig laufen Einträge im erweiterten Gruppencache nach vier Stunden ab. Wenn Sie daher eine Verteilergruppe als Journalempfänger angeben, kommen Änderungen an der Verteilergruppenmitgliedschaft möglicherweise erst nach der Aktualisierung des erweiterten Gruppencaches zur Anwendung. Sie müssen den Microsoft Exchange-Transportdienst beenden und dann neu starten, um ein sofortiges Update des Empfängercaches zu erzwingen. Sie müssen diesen Schritt für jeden Postfachserver durchführen, auf dem das Update des Empfängercaches erzwungen werden soll.



Zurück zum Seitenanfang

## Journalberichte

Ein *Journalbericht* ist die Mitteilung, die der Journal-Agent generiert, wenn eine Nachricht einer Journalregel entspricht und an das Journalpostfach übermittelt werden soll. Die Originalnachricht, die der Journalregel entspricht, wird unverändert als Anlage in den Journalbericht aufgenommen. Der Text eines Journalberichts enthält Informationen aus der ursprünglichen Nachricht wie die E-Mail-Adresse des Absenders, den Betreff der Nachricht, die Nachrichten-ID und die E-Mail-Adressen der Empfänger. Dies wird auch als Umschlagsjournal bezeichnet und ist die einzige Journalmethode, die von Exchange 2013 unterstützt wird.

## Journalberichte und IRM-geschützte Nachrichten

Bei der Implementierung der Journalfunktion in einer Exchange 2013-Umgebung müssen Sie Journalberichte und IRM-geschützte Nachrichten berücksichtigen. IRM-geschützte Nachrichten wirken sich auf die Such- und Discoveryfunktionen von Drittanbietersystemen für die Archivierung aus, die nicht über integrierte RMS-Unterstützung verfügen. In Exchange 2013 können Sie die Journalberichtentschlüsselung konfigurieren, um eine unverschlüsselte Kopie einer Nachricht in einem Journalbericht zu speichern.

Zurück zum Seitenanfang

## Interoperabilität mit Exchange 2007

Die Journalfunktionen von Exchange 2013, Exchange 2010 und Exchange 2007 unterscheiden sich nur geringfügig. In Exchange 2010 und höher erstellt das Setup jedoch einen separaten Container in Active Directory, um Journalregeln zu speichern. Wenn Sie den ersten Server mit Exchange 2010 oder höher in einer Exchange 2007-Organisation einrichten, erstellt das Setup eine Kopie der vorhandenen Journalregeln in Exchange 2007 und speichert diese in einem neuen Container. Nach Abschluss des Setup sind die Journalregeln in beiden Versionen von Exchange konsistent.

Wenn Sie nach dem Setup die Journalregelkonfiguration in Exchange 2010 (oder höher) ändern, müssen Sie die gleiche Änderung auch auf den Exchange 2007-Servern durchführen, um die Konsistenz sicherzustellen. Ebenso müssen unter Exchange 2007 vorgenommene Änderungen an den Journalregeln auch in Exchange 2010 oder höher durchgeführt werden. Sie können Journalregeln auch aus Exchange 2007 exportieren und in Exchange 2013 importieren.

Zurück zum Seitenanfang

## Problembehandlung

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351). Wenn Sie Probleme mit dem **JournalingReportDNRTo**-Postfach haben, finden Sie weitere Informationen unter [Transport- und Postfachregeln in Exchange Online funktionieren nicht wie erwartet](https://go.microsoft.com/fwlink/p/?linkid=331674).

