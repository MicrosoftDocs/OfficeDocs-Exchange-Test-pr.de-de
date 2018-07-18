---
title: 'Sicherung, Wiederherstellung und Notfallwiederherstellung: Exchange 2013 Help'
TOCTitle: Sicherung, Wiederherstellung und Notfallwiederherstellung
ms:assetid: 394fc4ed-fa02-41fa-9159-cc2754ff8875
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876874(v=EXCHG.150)
ms:contentKeyID: 50475329
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Sicherung, Wiederherstellung und Notfallwiederherstellung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Bei Ihrer Planung des Schutzes von Daten müssen Sie Kenntnisse darüber besitzen, wie Daten geschützt werden können und wie Sie die für die Anforderungen Ihrer Organisation am besten geeignete Methode auswählen. Die Planung des Schutzes von Daten ist ein komplexer Vorgang, der auf zahlreichen Entscheidungen beruht, die Sie in der Planungsphase Ihrer Bereitstellung treffen.

Bisher wurden Sicherungen für die folgenden Szenarien verwendet:

  - **Notfallwiederherstellung**   Bei einem Hardware- oder Softwareausfall ermöglicht das Vorhandensein mehrerer Datenbankkopien in einer DAG eine hohe Verfügbarkeit mit schnellem Failover und geringen oder keinen Datenverlusten. So werden Downtime und die entsprechenden Produktivitätsverluste vermieden, die wesentlich zu den Kosten einer Wiederherstellung einer Sicherung auf Festplatte oder Band beitragen, die zu einem vergangenen Zeitpunkt erstellt wurde. DAGs können auf mehrere Standorte erweitert werden und können Schutz vor dem Ausfall von Datenträgern, Servern, Netzwerken und Rechenzentren bieten.

  - **Wiederherstellung versehentlich gelöschter Elemente**   Wenn ein Benutzer Elemente gelöscht hatte, die später wiederhergestellt werden sollten, mussten früher die Sicherungsmedien mit diesen Daten gefunden werden, und die gewünschten Elemente mussten abgerufen und dem Benutzer bereitgestellt werden. Mit dem neuen Ordner "Wiederherstellbare Elemente" in Exchange 2013 und der Aufbewahrungsrichtlinie, die auf ihn angewendet werden kann, können alle gelöschten und geänderten Daten für einen angegebenen Zeitraum aufbewahrt werden, sodass die Wiederherstellung dieser Elemente leichter und schneller möglich ist. Dies entlastet Exchange-Administratoren und IT-Helpdesk, indem Endbenutzern ermöglicht wird, versehentlich gelöschte Elemente selbst wiederherzustellen und so die Komplexität und die Verwaltungskosten der Wiederherstellung einzelner Elemente zu senken. Weitere Informationen finden Sie unter [Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md) und [Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md).

  - **Langfristige Datenspeicherung**   Sicherungen werden auch als Archiv verwendet. Im Allgemeinen werden Momentaufnahmen von Daten für lange Zeiträume auf Band aufbewahrt, um entsprechende Vorschriften zu erfüllen. Die neuen Funktionen für Archivierung, Suche in mehreren Postfächern und Nachrichtenaufbewahrung in Exchange 2013 stellen einen Mechanismus für die effiziente langfristige Aufbewahrung von Daten bereit, wobei die Endbenutzer auf die Daten zugreifen können. Dadurch werden kostenintensive Wiederherstellungen von Band vermieden, und die Produktivität wird gesteigert. Weitere Informationen finden Sie unter [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md), [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md) und [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md).

  - **Datenbankmomentaufnahme**   Wenn für Ihre Organisation eine Zeitpunktkopie von Postfachdaten erforderlich ist, können Sie mit Exchange eine verzögerte Datenbankkopie in einer DAG-Umgebung erstellen. Dies kann in dem seltenen Fall nützlich sein, dass eine logische Beschädigung des Speichers auf mehrere Datenbankkopien in der DAG repliziert wird, sodass die Rückkehr zu einem bestimmten Zeitpunkt in der Vergangenheit erforderlich ist. Es kann auch hilfreich sein, wenn ein Administrator versehentlich Postfächer oder Benutzerdaten löscht. Die Wiederherstellung von einer verzögerten Kopie kann schneller sein als die Wiederherstellung von einer Sicherung, weil für verzögerte Kopien kein zeitaufwändiger Kopiervorgang vom Sicherungsserver zum Exchange-Server erforderlich ist. Dies kann zu einer deutlichen Reduzierung der Gesamtbetriebskosten führen, indem die Downtime reduziert wird.

Da es systemeigene Exchange 2013-Features gibt, die jedes dieser Anforderungsszenarien effizient und kosteneffektiv erfüllen, können Sie den Einsatz herkömmlicher Sicherungen in Ihrer Umgebung möglicherweise reduzieren oder einstellen.

Systemeigener Exchange-Datenschutz

Unterstützte Sicherungstechnologien

Exchange 2013-VSS-Writer

Exchange Server-Wiederherstellung

Wiederherstellung des einheitlichen Kontaktspeichers

Wiederherstellungsdatenbank

Datenbankportabilität

Dial Tone-Portabilität

## Systemeigener Exchange-Datenschutz

Die [bevorzugte Architektur](https://blogs.technet.com/b/exchange/archive/2014/04/21/the-preferred-architecture.aspx) von Microsoft für Exchange Server 2013 verwendet ein Konzept, das als systemeigener Exchange-Datenschutz bezeichnet wird. Systemeigener Exchange-Datenschutz basiert auf integrierten Exchange-Features, um Ihre Postfachdaten ohne den Einsatz herkömmlicher Backups zu schützen (wobei Sie diese Features weiterhin verwenden und Sicherungen erstellen können). In Exchange 2013 sind verschiedene neue Funktionen und grundlegende Änderungen enthalten, die bei ordnungsgemäßer Bereitstellung und Konfiguration einen Schutz systemeigener Daten bieten können, der die Notwendigkeit beseitigt, herkömmliche Sicherungen Ihrer Daten zu erstellen. Durch die Verwendung der in Exchange 2013 integrierten Funktionen für hohe Verfügbarkeit zum Minimieren von Ausfallzeiten und Datenverlusten bei Notfällen können auch die Gesamtkosten des Messagingsystems verringert werden. Die Kombination dieser Funktionen mit anderen integrierten Funktionen, z. B. der rechtlichen Aufbewahrungspflicht, ermöglicht Ihnen, den Einsatz herkömmlicher Sicherungen zu bestimmten Zeitpunkten zu verringern oder einzustellen und die entsprechenden Kosten zu senken.

Zusätzlich zu der Feststellung, ob Sie mit Exchange 2013 die herkömmlichen Sicherungen zu bestimmten Zeitpunkten ersetzen können, wird empfohlen, die Kosten für die aktuelle Sicherungsinfrastruktur abzuschätzen. Beachten Sie die Kosten der Downtime für Endbenutzer und der Datenverluste bei dem Versuch der Wiederherstellung nach einem Notfall unter Verwendung der vorhandenen Sicherungsinfrastruktur. Berücksichtigen Sie auch die Kosten für Hardware, Installation und Lizenzen sowie die Verwaltungskosten, die mit der Wiederherstellung von Daten und der Pflege von Sicherungen einhergehen. In Abhängigkeit von den Anforderungen in Ihrem Unternehmen ist es sehr wahrscheinlich, dass eine reine Exchange 2013-Umgebung mit mindestens drei Postfachdatenbankkopien geringere Gesamtkosten mit sich bringt als eine Umgebung mit Sicherungen.

Sie sollten verschiedene Aspekte berücksichtigen, bevor Sie die integrierten Features von Exchange 2013 als Ersatz für herkömmliche Sicherungen verwenden. Manche Überlegungen treffen möglicherweise nur für Ihre Organisation zu. Berücksichtigen Sie die folgenden Punkte. Beachten Sie dabei, dass diese Liste nicht vollständig ist:

  - Sie sollten bestimmen, wie viele Kopien der Datenbank bereitgestellt werden müssen. Es wird dringend empfohlen, mindestens drei (nicht verzögerte) Kopien einer Postfachdatenbank bereitzustellen, bevor Sie herkömmliche Arten des Schutzes für die Datenbank aufgeben, z. B. RAID (Redundant Array of Independent Disks) oder herkömmliche VSS-basierte Sicherungen.

  - Sie sollten die angestrebte Wiederherstellungsdauer und den angestrebten Wiederherstellungszeitpunkt klar definieren, und Sie sollten sich vergewissern, dass eine Kombination integrierter Features statt herkömmlicher Sicherungen Ihnen das Erreichen dieser Ziele ermöglicht.

  - Sie sollten bestimmen, wie viele Kopien jeder Datenbank erforderlich sind, um die unterschiedlichen Ausfallszenarien abzudecken, gegen die Ihr System einen Schutz darstellen soll.

  - Sie sollten bestimmen, ob Sie durch den Verzicht auf eine DAG oder einiger ihrer Mitglieder ausreichend Kosten einsparen, um eine herkömmliche Sicherungslösung zu unterstützen. Falls dies der Fall ist, sollten Sie bestimmen, ob diese Lösung Ihre in den Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) angestrebte Wiederherstellungsdauer oder Ihren angestrebten Wiederherstellungszeitpunkt verbessert.

  - Sie sollten bestimmen, ob Sie es sich leisten können, eine zu einem bestimmten Zeitpunkt erstellte Kopie zu verlieren, wenn auf dem DAG-Mitglied, das als Host der Kopie dient, ein Fehler auftritt, der die Kopie oder die Integrität der Kopie beeinflusst.

  - Exchange 2013 ermöglicht die Bereitstellung sehr viel größerer Postfächer, wobei die empfohlene Maximalgröße für Postfachdatenbanken bei 2 Terabyte liegt (wenn zwei oder mehr hoch verfügbare Postfachdatenbankkopien verwendet werden). Basierend auf den größeren Postfächern, die die meisten Organisationen bereitstellen werden, sollten Sie den angestrebten Wiederherstellungszeitpunkt bestimmen, wenn Sie bei der Aktivierung einer Datenbankkopie oder einer verzögerten Datenbankkopie zahlreiche Protokolldateien wiedergeben müssen.

  - Sie sollten bestimmen, wie Sie erkennen und verhindern, dass eine logische Beschädigung einer aktiven Datenbankkopie in die passiven Kopien der Datenbank repliziert wird. Dazu gehört, einen Wiederherstellungsplan für diese Situation festzulegen und herauszufinden, wie häufig dieses Szenario in der Vergangenheit eingetreten ist. Wenn in Ihrer Organisation häufig logische Beschädigungen auftreten, sollten Sie dieses Szenario in Ihrem Entwurf berücksichtigen, indem Sie mindestens eine verzögerte Kopie verwenden und das Zeitfenster für die Wiedergabeverzögerung ausreichend groß wählen, um das Auftreten logischer Beschädigungen zu erkennen und zu handeln, bevor diese Beschädigungen an andere Datenbankkopien repliziert werden.

Eine der Funktionen, die am Ende einer erfolgreichen vollständigen oder inkrementellen Sicherung ausgeführt werden, ist das Abschneiden der Transaktionsprotokolldateien, die nicht mehr für die Datenbankwiederherstellung benötigt werden. Wenn Sicherungen nicht ausgeführt werden, erfolgt kein Abschneiden von Protokollen. Wenn Sie verhindern möchten, dass die Protokolldateien immer umfangreicher werden, aktivieren Sie die Umlaufprotokollierung für die replizierten Datenbanken. Wenn Sie die Umlaufprotokollierung mit der fortlaufenden Replikation kombinieren, erhalten Sie eine neue Art der Umlaufprotokollierung mit der Bezeichnung CRCL (Continuous Replication Circular Logging, Umlaufprotokollierung bei fortlaufender Replikation), die sich von der ESE-Umlaufprotokollierung (Extensible Storage Engine) unterscheidet. Im Gegensatz zur ESE-Umlaufprotokollierung, die vom Microsoft Exchange-Informationsspeicherdienst ausgeführt und verwaltet wird, wird CRCL vom Microsoft Exchange-Replikationsdienst ausgeführt und verwaltet. Wenn aktiviert, generiert die ESE-Umlaufprotokollierung keine zusätzlichen Protokolldateien und überschreibt stattdessen im Bedarfsfall die aktuelle Protokolldatei. Allerdings werden in einer Umgebung mit fortlaufender Replikation Protokolldateien für den Protokollversand und die Protokollwiedergabe benötigt. Dementsprechend wird, wenn Sie CRCL aktivieren, die aktuelle Protokolldatei nicht überschrieben, und es werden geschlossene Protokolldateien für Protokollversand und -wiedergabe generiert.

Der Microsoft Exchange-Replikationsdienst verwaltet CRCL so, dass die Protokollkontinuität beibehalten wird, und Protokolle werden nicht gelöscht, wenn sie noch für die Replikation benötigt werden. Der Microsoft Exchange-Replikationsdienst und der Microsoft Exchange-Informationsspeicherdienst kommunizieren über Remoteprozeduraufrufe (Remote Procedure Calls, RPCs) darüber, welche Protokolldateien gelöscht werden können.

Damit das Abschneiden bei Postfachdatenbankkopien mit hoher Verfügbarkeit (nicht verzögert) erfolgt, muss Folgendes gelten:

  - Die Protokolldatei wurde gesichert, oder CRCL ist aktiviert.

  - Die Protokolldatei liegt unter dem Prüfpunkt.

  - Die anderen, nicht verzögerten Kopien der Datenbank stimmen dem Löschvorgang zu.

  - Die Protokolldatei wurde von allen verzögerten Kopien der Datenbank untersucht.

Damit das Abschneiden bei verzögerten Postfachdatenbankkopien erfolgt, muss Folgendes gelten:

  - Die Protokolldatei liegt unter dem Prüfpunkt.

  - Die Protokolldatei ist älter als "ReplayLagTime" + "TruncationLagTime".

  - Die Protokolldatei wurde in der aktiven Kopie der Datenbank gelöscht.

Systemeigener Exchange-Datenschutz

## Unterstützte Sicherungstechnologien

Exchange 2013 unterstützt nur Exchange-fähige, VSS-basierte Sicherungen. Exchange 2013 enthält ein Plug-In für Windows Server-Sicherung, mit der Sie VSS-basierte Sicherungen von Exchange-Daten erstellen können. Zum Sichern und Wiederherstellen von Exchange 2013 müssen Sie eine Exchange-fähige Anwendung verwenden, die den VSS Writer für Exchange 2013 unterstützt, z. B. die Windows Server-Sicherung (mit dem VSS-Plug-In), Microsoft System Center 2012 Data Protection Manager oder eine VSS-basierte Drittanbieteranwendung mit Exchange-Unterstützung.

Genaue Anweisungen zum Sichern und Wiederherstellen von Exchange-Daten mit der Windows Server-Sicherung finden Sie unter [Sichern und Wiederherstellen von Exchange-Daten mithilfe der Windows Server-Sicherung](using-windows-server-backup-to-back-up-and-restore-exchange-data-exchange-2013-help.md).

Systemeigener Exchange-Datenschutz

## Exchange 2013-VSS-Writer

In Exchange 2013 wird gegenüber Exchange 2010 und Exchange 2007 eine signifikante Änderung an der VSS Writer-Architektur eingeführt. Diese früheren Versionen von Exchange umfassten zwei VSS Writer: einen VSS Writer innerhalb des Microsoft Exchange-Informationsspeicherdiensts (store.exe) und einen VSS Writer innerhalb des Microsoft Exchange-Replikationsdiensts (msexchangerepl.exe). In Exchange wird die vormalige VSS Writer-Funktionalität aus dem Microsoft Exchange-Informationsspeicherdienst in den Microsoft Exchange-Replikationsdienst verschoben. Der neue Writer, Microsoft Exchange Writer, wird jetzt von Exchange-fähigen, VSS-basierten Anwendungen zur Sicherung von aktiven und passiven Datenbankkopien sowie zur Wiederherstellung von gesicherten Datenbankkopien verwendet. Wenngleich der neue Writer im Microsoft Exchange-Replikationsdienst ausgeführt wird, muss der Microsoft Exchange-Informationsspeicherdienst ausgeführt werden, damit der Writer angekündigt wird. Es sind also beide Dienste erforderlich, um Exchange-Datenbanken zu sichern oder wiederherzustellen.

Systemeigener Exchange-Datenschutz

## Exchange Server-Wiederherstellung

Nahezu alle Konfigurationseinstellungen für Postfach- und Clientzugriffsserver sind in Active Directory gespeichert. Wie frühere Versionen von Exchange schließt Exchange 2013 einen Setupparameter für die Wiederherstellung verlorener Server ein. Dieser Parameter, */m:RecoverServer*, wird verwendet, um einen verlorenen Server mithilfe der in Active Directory gespeicherten Einstellungen und Konfigurationsinformationen neu zu erstellen. Beachten Sie allerdings, dass es zahlreiche Einstellungen gibt, die nicht wiederhergestellt werden, etwa Änderungen an der lokalen "web.config"-Datei und anderen Konfigurationsdateien. Darüber hinaus werden benutzerdefinierte Registrierungseinträge nicht wiederhergestellt Es wird empfohlen, diese Änderungen anhand eines zuverlässigen Änderungsverwaltungsprozesses zu verfolgen und neu zu erstellen.

Genaue Anweisungen zum Durchführen einer Serverwiederherstellung eines verlorenen Exchange 2013-Servers finden Sie unter [Wiederherstellen eines Exchange-Servers](recover-an-exchange-server-exchange-2013-help.md). Genaue Anweisungen zum Wiederherstellen eines verlorenen Servers, der Mitglied einer Database Availability Group (DAG) ist, finden Sie unter [Wiederherstellen von Mitgliedsservern einer Datenbankverfügbarkeitsgruppe](recover-a-database-availability-group-member-server-exchange-2013-help.md).

Systemeigener Exchange-Datenschutz

## Wiederherstellung des einheitlichen Kontaktspeichers

Wenn Microsoft Lync Server 2013 in einer Exchange 2013-Umgebung verwendet wird, werden die Lync-Kontaktinformationen des Benutzers in einem besonderen Kontaktordner im Benutzerpostfach gespeichert. Dieser wird als einheitlicher Kontaktspeicher (Unified Contact Store, UCS) bezeichnet. Wenn Sie ein UCS-migriertes Postfach wiederherstellen, kann sich dies auf die Chatkontaktliste des Zielbenutzers auswirken. Wenn der Benutzer nach der letzten Sicherung migriert wurde, führt die Wiederherstellung des Postfachs zum vollständige Verlust der Benutzerkontaktliste. In weniger schweren Fällen gehen nur die Änderungen an der Kontaktliste verloren, die der Benutzer seit der letzten Sicherung durchgeführt hat. Zur Vermeidung eines potenziellen Datenverlusts müssen Sie sicherstellen, dass der Benutzer auf den Chatserver zurückmigriert wird, bevor das Postfach wiederhergestellt wird.

Systemeigener Exchange-Datenschutz

## Wiederherstellungsdatenbank

Eine Wiederherstellungsdatenbank ist eine spezielle Art von Postfachdatenbank, mit der Sie eine wiederhergestellte Postfachdatenbank einbinden und im Rahmen einer Wiederherstellung Daten aus der wiederhergestellten Datenbank extrahieren können. Verwenden Sie das Cmdlet [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)), um Daten aus einer Wiederherstellungsdatenbank zu extrahieren. Anschließend können die Daten in einen Ordner exportiert oder mit einem vorhandenen Postfach zusammengeführt werden. Mithilfe von Wiederherstellungsdatenbanken können Sie Daten aus einer Sicherung oder Kopie der Datenbank wiederherstellen, ohne den Benutzerzugriff auf aktuelle Daten zu stören.

Die Verwendung einer Wiederherstellungsdatenbank für eine Postfachdatenbank einer früheren Version von Exchange wird nicht unterstützt. Außerdem muss sich das Zielpostfach, das zur Datenzusammenführung und -extraktion verwendet wird, in derselben Active Directory-Gesamtstruktur befinden wie die in der Wiederherstellungsdatenbank eingebundene Datenbank.

Weitere Informationen finden Sie unter [Wiederherstellungsdatenbanken](recovery-databases-exchange-2013-help.md). Genaue Anweisungen zum Erstellen einer Wiederherstellungsdatenbank finden Sie unter [Erstellen einer Wiederherstellungsdatenbank](create-a-recovery-database-exchange-2013-help.md). Genaue Anweisungen zum Verwenden einer Wiederherstellungsdatenbank finden Sie unter [Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank](restore-data-using-a-recovery-database-exchange-2013-help.md).

Systemeigener Exchange-Datenschutz

## Datenbankportabilität

Die Datenbankportabilität ist eine Funktion, mit der eine Exchange 2013-Postfachdatenbank auf einen beliebigen anderen Exchange 2013-Postfachserver in derselben Organisation verschoben und dort eingebunden werden kann. Mithilfe der Datenbankportabilität wird die Zuverlässigkeit verbessert, indem auf verschiedene fehleranfällige manuelle Schritte bei den Wiederherstellungsprozessen verzichtet werden kann. Darüber hinaus verringert die Datenbankportabilität die Gesamtwiederherstellungsdauer für verschiedene Fehlerszenarien.

Weitere Informationen finden Sie unter [Datenbankportabilität](database-portability-exchange-2013-help.md). Genaue Anweisungen zur Verwendung der Datenbankportabilität finden Sie unter [Verschieben einer Postfachdatenbank mithilfe der Datenbankportabilität](move-a-mailbox-database-using-database-portability-exchange-2013-help.md).

Systemeigener Exchange-Datenschutz

## Dial Tone-Portabilität

Die Funktion für die Dial Tone-Portabilität bietet eine eingeschränkte Geschäftskontinuitätslösung für Ausfälle, die sich auf eine Postfachdatenbank, einen Server oder einen ganzen Standort auswirken. Durch die Dial Tone-Portabilität erhalten Benutzer die Möglichkeit, ein temporäres Postfach zum Senden und Empfangen von E-Mails zu nutzen, während ihr ursprüngliches Postfach wiederhergestellt oder repariert wird. Das temporäre Postfach kann sich auf demselben Exchange 2013-Postfachserver oder auf einem beliebigen anderen Exchange 2013-Postfachserver in der Organisation befinden. Somit kann ein alternativer Server die Postfächer von Benutzern hosten, die sich zuvor auf einem anderen Server befunden haben, der jetzt nicht mehr verfügbar ist. Clients mit Unterstützung der AutoErmittlung, z. B. Microsoft Outlook, werden automatisch auf den neuen Server umgeleitet, ohne dass das Desktopprofil des Benutzers manuell aktualisiert werden muss. Nach der Wiederherstellung der eigentlichen Postfachdaten des Benutzers kann ein Administrator das wiederhergestellte Postfach und das Dial Tone-Postfach des Benutzers in ein einziges, aktuelles Postfach zusammenführen.

Das Verfahren zur Verwendung der Dial Tone-Portabilität wird als *Dial Tone-Wiederherstellung* bezeichnet. Eine Dial Tone-Wiederherstellung umfasst das Erstellen einer leeren Datenbank auf einem Postfachserver, um eine fehlerhafte Datenbank zu ersetzen. Mithilfe dieser leeren Datenbank, die auch als *Dial Tone-Datenbank* bezeichnet wird, können Benutzer E-Mails senden und empfangen, während die fehlerhafte Datenbank wiederhergestellt wird. Nach der Wiederherstellung der fehlerhaften Datenbank werden die Dial Tone-Datenbank und die wiederhergestellte Datenbank ausgetauscht, und die Daten aus der Dial Tone-Datenbank werden dann mit denen in der wiederhergestellten Datenbank zusammengeführt.

Weitere Informationen finden Sie unter [Dial Tone-Portabilität](dial-tone-portability-exchange-2013-help.md). Genaue Anweisungen zum Durchführen einer Dial Tone-Wiederherstellung finden Sie unter [Durchführen einer "Dial Tone"-Wiederherstellung](perform-a-dial-tone-recovery-exchange-2013-help.md).

Systemeigener Exchange-Datenschutz

