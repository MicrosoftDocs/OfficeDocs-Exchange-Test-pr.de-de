---
title: 'Unified Messaging: Exchange 2013 Help'
TOCTitle: Unified Messaging
ms:assetid: 004b5d1a-cae8-4034-ab65-db41bd2f7b97
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150478(v=EXCHG.150)
ms:contentKeyID: 50474929
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Unified Messaging

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit Unified Messaging (UM) können Benutzer Voicemail- und andere Funktionen wie u. a. Outlook Voice Access und Mailboxansageregeln verwenden. Unified Messaging kombiniert Voicemessaging und E-Mails in einem Postfach, auf das über verschiedene Geräte zugegriffen werden kann. Benutzer können die Nachrichten über ihren E-Mail-Posteingang oder mit Outlook Voice Access auf einem beliebigen Telefon abhören. Sie können steuern, wie Benutzer ausgehende Anrufe über UM tätigen, und festlegen, wie Anrufe bei der Organisation behandelt werden.

IT-Administratoren verwalten die Voicemail- oder Telefonienetzwerke und die E-Mail-Systeme oder Datennetzwerke für ihre Organisationen heute häufig als getrennte Systeme. Voicemail und E-Mail sind als getrennte Posteingänge vorhanden, die auf getrennten Servern gehostet werden. Der Zugriff auf E-Mails erfolgt über den Desktop, der Zugriff auf Voicemail über das Telefon.

Mit Unified Messaging können Exchange-Administratoren Voicemessaging und E-Mails in einem Postfach kombinieren, sodass Benutzer ihre Voicemailnachrichten sowohl über ihren E-Mail-Posteingang als auch über Outlook Voice Access auf einem beliebigen Telefon abhören können. Diese Funktion verwendet den Exchange-Informationsspeicher sowohl für E-Mails als auch für Sprachnachrichten.

**Inhalt**

Neue Features

Unified Messaging-Funktionen

Planen und Bereitstellen von Unified Messaging

Verwalten von Unified Messaging mithilfe der Exchange-Verwaltungskonsole und der Shell

Dokumentation zu Unified Messaging

## Neue Features

Unified Messaging (UM) wurde in Microsoft Exchange Server 2007 erstmalig eingeführt und war auch in Exchange 2010 verfügbar. Die Unified Messaging-Funktionen in Exchange 2013 sind mit vorherigen Versionen von Exchange vergleichbar. Allerdings wurden neue Funktionen hinzugefügt, und die Architektur wurde überarbeitet. Unified Messaging wird nun als Komponente oder Teilfunktion der sprachbezogenen Funktionen betrachtet, die in Exchange 2013 verfügbar sind. Der Begriff *Unified Messaging* wird weiterhin umfassend in den Cmdlets der Exchange-Verwaltungsshell und UM-bezogenen Diensten verwendet. Alle Unified Messaging-Komponenten (einschließlich Wählpläne, automatische Telefonzentralen, UM-Postfachrichtlinien und UM-IP-Gateways) sowie die Verwaltungsoptionen für diese UM-Komponenten befinden sich im Navigationsbereich der Exchange-Verwaltungskonsole unterhalb des Unified Messaging-Knotens.

Die folgenden Themen liefern Informationen zu neuen oder erweiterten Exchange 2013 Unified Messaging-Funktionen:

  - [Änderungen an der Spracharchitektur](voice-architecture-changes-exchange-2013-help.md)

  - [IPv6-Unterstützung in Unified Messaging](ipv6-support-in-unified-messaging-exchange-2013-help.md)

  - [Voicemail-Vorschau Erweiterungen](voice-mail-preview-enhancements-exchange-2013-help.md)

  - [Updates für Unified Messaging-Cmdlets](unified-messaging-cmdlet-updates-exchange-2013-help.md)

Zurück zum Seitenanfang

## Unified Messaging-Funktionen

Die Voicemailfunktionen in Unified Messaging bieten sowohl für Endbenutzer als auch für IT-Administratoren Vorteile.

## Funktionen für Endbenutzer

Wenn Sie Unified Messaging bereitstellen, können Benutzer auf Voicemail-, E-Mail- und Kalenderinformationen in ihrem Postfach über einen E-Mail-Client (beispielsweise Outlook oder MicrosoftOutlook Web App), von einem Mobiltelefon mit eingerichtetem MicrosoftExchange ActiveSync (beispielsweise Windows Phone) oder von einem Telefon aus zugreifen. Darüber hinaus können Benutzer die folgenden Funktionen nutzen:

  - **Zugriff auf Exchange-Informationen   **UM-aktivierte Benutzer können über internetfähige Mobiltelefone, MicrosoftOffice Outlook 2007 oder höher und Outlook Web App auf einen umfangreichen Satz an Voicemailfunktionen zugreifen. Zu diesen Funktionen gehören zahlreiche Voicemail-Konfigurationsoptionen sowie die Möglichkeit der Wiedergabe einer Sprachnachricht entweder im Lesebereich mithilfe eines integrierten Windows Media Players oder in der Nachrichtenliste mithilfe der Computerlautsprecher .

  - **Wiedergabe über Telefon**   Diese Funktion ermöglicht UM-aktivierten Benutzern die Wiedergabe von Sprachnachrichten über ein Telefon. Wenn der Benutzer in einem Großraumbüro arbeitet, einen öffentlichen bzw. einen nicht multimediafähigen Computer verwendet oder eine vertrauliche Sprachnachricht wiedergibt, möchte er die Sprachnachricht möglicherweise nicht über die Computerlautsprecher wiedergeben. Er kann die Sprachnachricht mithilfe eines privaten oder geschäftlichen Telefons oder eines Mobiltelefons wiedergeben.

  - **Voicemailformular**   Das Voicemailformular ähnelt dem E-Mail-Standardformular. Es stellt Benutzern eine Schnittstelle zum Ausführen von Aktionen bereit wie das Wiedergeben, Beenden oder Anhalten von Sprachnachrichten, die Wiedergabe von Sprachnachrichten über ein Telefon sowie das Hinzufügen und Bearbeiten von Notizen.
    
    Das Voicemailformular enthält den eingebetteten Windows Media Player und ein Feld Audionotizen. Der eingebettete Windows Media Player und das Feld "Audionotizen" werden entweder bei der Vorschau einer Sprachnachricht im Lesebereich angezeigt oder in einem gesonderten Fenster, wenn die Sprachmitteilung vom Benutzer geöffnet wird. Wenn Benutzer nicht für Unified Messaging aktiviert sind oder auf dem Clientcomputer kein unterstützter E-Mail-Client installiert ist, werden Sprachnachrichten nur als E-Mail-Anlagen angezeigt, und das Voicemailformular ist nicht verfügbar.

  - **Benutzerkonfiguration**   Ein für Unified Messaging aktivierter Benutzer kann mithilfe von Outlook Web App mehrere Voicemailoptionen für Unified Messaging konfigurieren. Beispielsweise kann der Benutzer Telefonzugriffsnummern und die Nummer für die Wiedergabe von Voicemail über das Telefon konfigurieren und anschließend eine PIN für den Voicemailzugriff zurücksetzen.

  - **Mailboxansage   **Die Mailboxansage umfasst die Beantwortung eingehender Anrufe im Auftrag eines Benutzers, die Wiedergabe einer persönlichen Begrüßung, das Aufzeichnen von Nachrichten und deren Zustellung an das Benutzerpostfach als E-Mail.

  - **Mailboxansageregeln**   Über Mailboxansageregeln können für Voicemail aktivierte Benutzer festlegen, wie eingehende Anrufe durch die Mailboxansage verarbeitet werden. Mailboxansageregeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails. Standardmäßig sind keine Mailboxansageregeln konfiguriert. Wenn der Postfachserver einen eingehenden Anruf entgegennimmt, wird der Anrufer aufgefordert, eine Sprachnachricht für den angerufenen Teilnehmer zu hinterlassen. Mit Mailboxansageregeln kann ein Anrufer folgende Aktionen durchführen:
    
      - Hinterlassen einer Sprachnachricht für den UM-aktivierten Benutzer.
    
      - Umleiten an einen alternativen Kontakt des UM-aktivierten Benutzers.
    
      - Umleiten an die Voicemail des alternativen Kontakts.
    
      - Umleiten an andere Telefonnummern, die der UM-aktivierte Benutzer konfiguriert hat.
    
      - Verwenden der Suchanruffunktion oder Ermitteln des UM-aktivierten Benutzers per Umleitung von einer Vermittlungsstelle.

  - **Voicemailvorschau**   Der Postfachserver verwendet für neu erstellte Voicemailnachrichten die automatische Spracherkennung. Wenn Benutzer Sprachnachrichten erhalten, sind darin sowohl eine Aufzeichnung als auch Text enthalten, der aus der Sprachaufzeichnung erstellt wurde. Der Text einer Sprachnachricht wird für die Benutzer in einer E-Mail in Outlook Web App oder einem anderen unterstützten E-Mail-Client angezeigt.

  - **Message Waiting Indicator**   Der Message Waiting Indicator ist eine Funktion, die in den meisten älteren Voicemailsystemen zu finden ist. Der Begriff bezieht sich auf jeden Mechanismus, der auf den Eingang einer neuen Nachricht hinweist. In Exchange 2007 wurde diese Funktionalität von einer Drittanbieteranwendung bereitgestellt, die den Empfang einer neuen Sprachnachricht durch eine Leuchte am Telefonapparat anzeigte. Diese Funktion wurde zu Exchange 2010 hinzugefügt, Software anderer Anbieter wird nicht länger benötigt. Der MWI (Message Waiting Indicator) kann über das Postfach des Benutzers oder durch eine UM-Postfachrichtlinie aktiviert oder deaktiviert werden.

  - **SMS-Benachrichtigungen über verpasste Anrufe und Voicemail**   Wenn Benutzer, die Teil einer Hybrid- oder Office 365-Bereitstellung sind, ihre Voicemaileinstellungen mit ihrer Mobiltelefonnummer konfigurieren und die Anrufweiterleitung festlegen, können diese Benutzer auf ihren Mobiltelefonen Benachrichtigungen zu verpassten Anrufen und neuen Sprachnachrichten in einer SMS-Nachricht (Short Messaging Service) erhalten. Hierzu müssen die Benutzer zunächst jedoch Textnachrichten konfigurieren und Benachrichtigungen für ihr Konto aktivieren.

  - **Geschützte Voicemail**   Geschützte Voicemail ist eine Unified Messaging-Funktionalität, mit deren Hilfe Benutzer private E-Mails senden können. Solche Nachrichten werden durch AD RMS (Active Directory Rights Management Services) geschützt, und Benutzer können die Sprachdatei aus der E-Mail nicht weiterleiten, kopieren oder extrahieren. Geschützte Voicemail erhöht die Diskretion von Unified Messaging, und Benutzer können die Empfänger von Sprachnachrichten einschränken. Diese Funktionalität ähnelt der Verarbeitung privater E-Mails in Exchange 2007, gilt nun jedoch auch für Voicemailnachrichten.

  - **Outlook Voice Access   **UM-aktivierten Benutzern stehen zwei Unified Messaging-Benutzerschnittstellen zur Verfügung: die Benutzerschnittstelle für Telefoneingabe (Telephone User Interface, TUI) und die Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI). Die Kombination dieser beiden Schnittstellen wird als Outlook Voice Access bezeichnet. Outlook Voice Access-Benutzer können Outlook Voice Access beim Zugriff auf das Voicemailsystem über ein externes oder internes Telefon nutzen. UM-aktivierte Benutzer, die sich beim Voicemailsystem einwählen, können mithilfe von Outlook Voice Access auf ihr Postfach zugreifen. Mit einem Telefon kann ein UM-aktivierter Benutzer Folgendes durchführen:
    
      - Zugreifen auf Voicemail
    
      - Abhören, Weiterleiten oder Beantworten von E-Mails
    
      - Abhören von Kalenderinformationen
    
      - Zugreifen auf Kontakte im Verzeichnis der Organisation oder auf einzelne Kontakte bzw. Kontaktgruppen, die in den persönlichen Kontakten des Benutzers gespeichert sind bzw. Wählen der entsprechenden Rufnummern.
    
      - Annehmen oder Stornieren von Besprechungsanfragen
    
      - Festlegen einer Sprachnachricht, um Anrufer über die Abwesenheit des angerufenen Teilnehmers zu informieren
    
      - Festlegen von Sicherheitseinstellungen und persönlichen Benutzeroptionen

  - **Gruppenadressierung über Outlook Voice Access**   In Exchange 2007 konnten Benutzer entweder die Benutzerschnittstelle für die Telefoneingabe (Telephone User Interface, TUI) oder die Benutzerschnittstelle für die Spracheingabe (Voice User Interface, VUI) in Outlook Voice Access verwenden, um nach der Anmeldung bei ihrem Postfach E-Mails und Sprachnachrichten zu senden. Allerdings konnten Benutzer nur eine einzige E-Mail an einen einzelnen Benutzer in ihren persönlichen Kontakten oder an mehrere Empfänger aus dem Verzeichnis senden, entweder durch Hinzufügen jedes einzelnen Empfängers oder durch Hinzufügen des Namens einer Verteilerliste aus dem Verzeichnis der Organisation. Wenn ein Benutzer sich in Exchange 2013 über Outlook Voice Access bei seinem Postfach anmeldet, kann er auch E-Mails und Sprachnachrichten an Benutzer in einer Gruppe senden, die in den persönlichen Kontakten gespeichert ist.

Zurück zum Seitenanfang

## Verwaltungsfunktionen

Derzeit verwalten die meisten Benutzer und IT-Abteilungen ihre Voicemail getrennt von ihrer E-Mail. Voicemail und E-Mail sind als getrennte Posteingänge vorhanden, die auf getrennten Servern gehostet werden und auf die über den Desktop (bei E-Mail) und über ein Telefon (bei Voicemail) zugegriffen wird. Unified Messaging stellt einen integrierten Informationsspeicher für alle Nachrichten und Zugriff auf Inhalte über den Computer und das Telefon bereit.

Exchange-Administratoren können Unified Messaging über dieselbe Schnittstelle verwalten, die auch zur Verwaltung der übrigen Exchange-Funktionen verwendet wird, die Exchange-Verwaltungskonsole und die Exchange-Verwaltungsshell. Sie können die folgenden Aufgaben durchführen:

  - Verwalten von Voicemail und E-Mail von einer einzigen Plattform aus

  - Verwalten von Unified Messaging mithilfe skriptfähiger Befehle

  - Erstellen hoch verfügbarer und zuverlässiger Unified Messaging-Infrastrukturen

Exchange 2013 Unified Messaging bietet Administratoren folgende Vorteile:

  - **Ein vollständiges Voicemailsystem**   Unified Messaging bietet eine umfassende Voicemaillösung, die eine einzige Informationsspeicher-, Transport- und Verzeichnisinfrastruktur verwendet. Der Informationsspeicher wird von einem Postfachserver bereitgestellt, und eingehende Anrufe von einem VoIP-Gateway oder einer IP-Nebenstellenanlage werden von einem Clientzugriffsserver weitergeleitet. Alle E-Mails und Voicemailnachrichten können mithilfe einer einzigen Verwaltungsschnittstelle und Toolsammlung von einem einzigen Verwaltungspunkt aus verwaltet werden.

  - **Ein Exchange-Sicherheitsmodell   **Der MicrosoftExchange Unified Messaging-Dienst auf einem Postfachserver und der MicrosoftExchange Unified Messaging-Call-Router-Dienst auf einem Clientzugriffsserver werden als ein einziges Exchange-Serverkonto ausgeführt.

  - **Konsolidierung von Voicemailsystemen**   Zurzeit müssen bei den meisten Voicemessagingsystemen alle Voicemessagingkomponenten an allen physischen Unternehmensstandorten innerhalb einer Organisation installiert sein. Bei solchen Architekturen befinden sich die Voicemessagingsysteme in Zweigstellen außerhalb des Hauptsitzes und müssen vor Ort verwaltet werden. Dies führt häufig zu höheren Verwaltungskosten und mehr Komplexität. Mit Unified Messaging können Sie Ihr Voicemailsystem von einem zentralen Standort aus verwalten. Zum Aufbau eines zentralisierten Verwaltungssystems für Unified Messaging können Sie einige Ihrer Exchange-Server in einem Datencenter oder an einem anderen Standort und die übrigen Exchange-Server lokal platzieren und dann in jeder Zweigstelle VoIP-Gateways, IP-Nebenstellenanlagen oder Session Border Controller (SBC) bereitstellen, durch die das Voicemessagingsystem der jeweiligen Zweigstelle ersetzt wird. Durch eine solche Bereitstellung eines zentralisierten Voicemessagingsystems können erhebliche Einsparungen bei Hardware und Verwaltungskosten erzielt werden.

  - **Integrierte Unified Messaging-Administratorrollen**   Eine Reihe von UM-spezifischen Administratorrollen zur Verwaltung von Unified Messaging- und Voicemailfunktionen, wie z. B.:
    
      - UM-Postfächer
    
      - UM-Telefonansagen
    
      - Unified Messaging

  - **Unterstützung eingehender Faxnachrichten**Exchange 2013 bietet integrierte Unterstützung für eingehende Faxnachrichten für Benutzer, die über ein UM-aktiviertes Postfach verfügen. Diese Benutzer können über Anrufe, die über ihre Durchwahl eingehen, Faxnachrichten empfangen.
    
    Kunden, die eine Faxlösung benötigen, müssen auf eine Faxpartnerlösung zurückgreifen. Faxpartnerlösungen sind von mehreren Faxpartnern erhältlich. Die Faxpartnerlösungen werden nahtlos in Exchange integriert und ermöglichen UM-aktivierten Benutzern den Empfang eingehender Faxnachrichten. Eine Liste mit Links zu Faxpartnerlösungen finden Sie unter [Microsoft Pinpoint für Faxpartner](https://go.microsoft.com/fwlink/?linkid=190238).

  - **Unterstützung für mehrere Sprachen   **   Alle verfügbaren Sprachpakete enthalten das TTS-Modul (Text-to-Speech) sowie vorab aufgezeichnete Ansagen für die betreffende Sprache sowie ASR-Unterstützung. Allerdings umfassen nur einige Sprachpakete Unterstützung für die Voicemailvorschau. Das US-englische Sprachpaket (en-US) ist auf dem Installationsmedium enthalten. Weitere UM-Sprachpakete können aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=266542) heruntergeladen werden.

  - **Automatische Telefonzentrale**   Eine automatische Telefonzentrale ist eine Sammlung von Sprachansagen, die externen und internen Benutzern den Zugriff auf das Voicemailsystem ermöglicht. Mithilfe der Telefontastatur oder mit Spracheingaben können Benutzer im Menü der automatischen Telefonzentrale navigieren, einen Benutzer anrufen oder nach einem Benutzer in der Organisation suchen und diesen dann anrufen. Eine automatische Telefonzentrale gibt dem Administrator folgende Möglichkeiten:
    
      - Erstellen eines angepassten Menüs für externe Benutzer.
    
      - Definieren von Informationsansagen, von Ansagen während der Geschäftszeiten und von Ansagen außerhalb der Geschäftszeiten.
    
      - Definieren von Urlaubszeitplänen.
    
      - Beschreiben der Suche im Verzeichnis der Organisation.
    
      - Beschreiben der Verbindung mit der Durchwahl eines Benutzers, damit externe Anrufer einen Benutzer durch Angabe seiner Durchwahl anrufen können.
    
      - Beschreiben der Suche im Verzeichnis der Organisation, damit externe Anrufer das Verzeichnis der Organisation durchsuchen und einen bestimmten Benutzer anrufen können.
    
      - Ermöglichen von Anrufen externer Benutzer bei der Vermittlungsstelle.

Zurück zum Seitenanfang

## Planen und Bereitstellen von Unified Messaging

Unified Messaging erfordert die Integration Ihrer Exchange Server-Bereitstellung mit dem vorhandenen Telefoniesystem Ihrer Organisation. Für eine erfolgreiche Bereitstellung und die Durchführung der richtigen Planungsschritte für die Bereitstellung und Verwaltung von Voicemail in Unified Messaging ist eine sorgfältige Analyse Ihrer vorhandenen Telefonieinfrastruktur erforderlich.

Wenn Sie die Unified Messaging-Bereitstellung planen, müssen Sie Design- und andere Fragen berücksichtigen, die sich auf die Möglichkeit auswirken, Ihre Unternehmensziele zu erreichen, wenn Sie Unified Messaging bereitstellen. Im Allgemeinen bedeutet eine einfache Unified Messaging-Topologie auch eine einfache Bereitstellung und Verwaltung von Unified Messaging. Installieren Sie so wenig Clientzugriffs- und Postfachserver wie möglich, und erstellen Sie so wenig Unified Messaging-Komponenten (z. B. UM-Wählpläne, automatische Telefonzentralen und UM-Postfachrichtlinien) wie möglich, um Ihre geschäftlichen und organisatorischen Ziele zu erreichen. Große Unternehmen mit komplexen Netzwerk- und Telefonieumgebungen, mehreren Geschäftseinheiten oder anderen komplizierten Strukturen erfordern eine ausführlichere Planung als kleine Organisationen mit relativ einfachen Unified Messaging-Anforderungen.

Es müssen zahlreiche Bereiche berücksichtigt und ausgewertet werden, damit Sie Unified Messaging erfolgreich bereitstellen können. Sie müssen die verschiedenen Aspekte von Unified Messaging sowie jede Komponente und jede Funktion verstehen, damit Sie die Unified Messaging-Infrastruktur und -Bereitstellung entsprechend planen können. Wenn Sie Zeit für die Planung und die Analyse von Einzelaspekten vorsehen, können Sie Probleme bei der Bereitstellung von Unified Messaging in Ihrer Organisation verhindern. Die folgenden Bereiche sollten z. B. bei der Planung von Unified Messaging in Ihrer Organisation berücksichtigt und ausgewertet werden:

  - Die Anforderungen Ihrer Organisation.

  - Die Sicherheitsanforderungen Ihrer Organisation.

  - Ihr vorhandenes leitungsvermitteltes Telefonienetzwerk sowie Ihr aktuelles Voicemailsystem.

  - Ihr aktuelles paketvermitteltes IP-Netzwerkdesign. Dies umfasst Ihre lokalen LAN- (Local Area Network) und WAN-Verbindungen und -Geräte.

  - Ihre aktuelle Active Directory-Umgebung.

  - Die Anzahl von Benutzern, die unterstützt werden müssen.

  - Die Anzahl von erforderlichen Clientzugriffs- und Postfachservern.

  - Die Frage, ob Unified Messaging mit Microsoft Lync Server integriert werden soll, um Enterprise-VoIP zu aktivieren.

  - Die Platzierung von VoIP-Gateways, Telefoniegeräten sowie Clientzugriffs- und Postfachservern.

  - Der Typ der Unified Messaging-Bereitstellung: lokal oder hybrid.

  - Die Speicheranforderungen für Voicemailbenutzer.

Zurück zum Seitenanfang

## Verwalten von Unified Messaging mithilfe der Exchange-Verwaltungskonsole und der Shell

**Verwaltung über die Exchange-Verwaltungskonsole**

Exchange 2013 verfügt über eine einzige einheitliche Verwaltungskonsole für Ihre Organisation, die alle UM-Komponenten und -Funktionen umfasst. Die Exchange-Verwaltungskonsole bietet eine optimierte Schnittstelle für die Verwaltung lokaler, Online- oder Hybridbereitstellungen. Die Exchange-Verwaltungskonsole in Exchange 2013 ersetzt die Exchange-Verwaltungskonsole und die Exchange-Systemsteuerung aus Exchange 2010. Zu den Funktionen der Exchange-Verwaltungskonsole gehören die Folgenden:

  - **Listenansicht**   In der Listenansicht der Exchange-Verwaltungskonsole wurden die Einschränkungen der Exchange-Systemsteuerung entfernt. In der Exchange-Systemsteuerung konnten nur bis zu 500 Objekte angezeigt werden, und um Objekte anzuzeigen, die im Detailbereich nicht aufgeführt wurden, mussten Sie mithilfe von Such- und Filterfunktionen nach diesen Objekten suchen. In Exchange 2013 können in der Listenansicht der Exchange-Verwaltungskonsole gut 20.000 Objekte angezeigt werden. Außerdem wurde die Seitenverwaltung hinzugefügt, sodass Sie die Ergebnisse in Seiten einteilen können. Außerdem können Sie die Seitengröße konfigurieren und Inhalte in eine CSV-Datei exportieren.

  - **Hinzufügen/Entfernen von Spalten in der Empfängerlistenansicht**   Sie können festlegen, welche Spalten angezeigt werden sollen, und Ihre benutzerdefinierten Listenansichten speichern.

  - **Absichern des virtuellen Verzeichnisses der Exchange-Systemsteuerung**   Sie können den Zugriff über das Internet und Intranets innerhalb des virtuellen IIS-Verzeichnisses der Exchange-Systemsteuerung partitionieren, um Verwaltungsfunktionen zuzulassen oder zu sperren. Mit dieser Funktion können Sie den Zugriff für Benutzer zulassen oder verweigern, die von außerhalb Ihrer Organisationsumgebung über das Internet auf die Exchange-Verwaltungskonsole zugreifen möchten. Gleichzeitig können Sie den Zugriff auf die Outlook Web App-Optionen eines Endbenutzers weiterhin zulassen.

  - **Verwaltung von öffentlichen Ordnern**   In Exchange 2010 und Exchange 2007 wurden öffentliche Ordner über die Verwaltungskonsole für öffentliche Ordner verwaltet. Öffentliche Ordner befinden sich nun in der Exchange-Verwaltungskonsole, und Sie benötigen kein separates Tool mehr für deren Verwaltung.

  - **Benachrichtigungen**   In Exchange 2013 weist die Exchange-Verwaltungskonsole eine Benachrichtigungsanzeige auf, sodass Sie den Status lang dauernder Prozesse anzeigen können und, falls gewünscht, per E-Mail darüber benachrichtigt werden, wenn ein Prozess abgeschlossen ist.

  - **Benutzereditor für die rollenbasierte Zugriffssteuerung**   In Exchange 2010 konnte der Benutzereditor für die rollenbasierte Zugriffssteuerung verwendet werden, um Benutzer zu Verwaltungsrollengruppen hinzuzufügen. In Exchange 2013 ist die Funktionalität des Benutzereditors für die rollenbasierte Zugriffssteuerung nun in der Exchange-Verwaltungskonsole enthalten, sodass kein separates Tool zur Verwaltung der rollenbasierten Zugriffssteuerung erforderlich ist.

  - **Unified Messaging-Tools**   In Exchange 2010 konnten die Anrufstatistik und die Benutzeranrufprotokolle verwendet werden, um UM-Statistiken und -Informationen zu bestimmten Anrufen für einen UM-aktivierten Benutzer abzurufen. In Exchange 2013 sind die Anrufstatistik und die Benutzeranrufprotokolle nun in der Exchange-Verwaltungskonsole enthalten, sodass kein separates Tool erforderlich ist, um diese Informationen zu verwalten.

**Verwaltung über die Shell**

Die Exchange-Verwaltungsshell, die auf der Windows PowerShell-Technologie basiert, ist eine leistungsstarke Befehlszeilenschnittstelle, die die Automatisierung von Verwaltungsaufgaben ermöglicht. Mit der Shell können Sie jeden Aspekt von Exchange verwalten. Sie können neue E-Mail-Konten aktivieren, Sende- und Empfangsconnectors erstellen, Datenbankeigenschaften konfigurieren, sämtliche Aspekte von Unified Messaging verwalten und mehr. Mit der Shell können alle über die Exchange-Verwaltungskonsole ausführbaren Aufgaben ausgeführt werden sowie weitere Aufgaben, die Sie in der Exchange-Verwaltungskonsole nicht ausführen können. Wenn Sie eine Aufgabe in der Exchange-Verwaltungskonsole ausführen, ist es in Wirklichkeit die Shell, die im Hintergrund tätig ist.

Zurück zum Seitenanfang

## Dokumentation zu Unified Messaging

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zu Exchange Unified Messaging sowie zur Verwaltung dieser Funktion finden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="new-voice-mail-features-exchange-2013-help.md">Neue Voicemailfeatures</a></p></td>
<td><p>Informationen zu den neuen Features in Microsoft Exchange 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="planning-for-unified-messaging-exchange-2013-help.md">Planen von Unified Messaging</a></p></td>
<td><p>Informationen zu den Konzepten und zur Planung einer Unified Messaging-Bereitstellung.</p></td>
</tr>
<tr class="odd">
<td><p><a href="deploying-voice-mail-and-um-exchange-2013-help.md">Bereitstellen von Voicemail und UM</a></p></td>
<td><p>Informationen zu den Anforderungen und Schritten zum Bereitstellen von Voicemail und Unified Messaging.</p></td>
</tr>
<tr class="even">
<td><p><a href="um-languages-prompts-and-greetings-exchange-2013-help.md">UM-Sprachen, -Telefonansagen und -Begrüßungen</a></p></td>
<td><p>Informationen zu UM-Sprachpaketen und -Spracheinstellungen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephone-system-integration-with-um">Telefonsystemintegration mit UM</a></p></td>
<td><p>Informationen zur Integration Ihres Telefonienetzwerks in UM.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/connect-voice-mail-system">Verbinden Ihres Voicemailsystems mit Ihrem Telefonnetz</a></p></td>
<td><p>Informationen zur Verwendung und Konfiguration von UM-Komponenten, um Ihr Telefonienetzwerk mit Exchange Unified Messaging zu verbinden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls">Automatisches Beantworten und Weiterleiten eingehender Anrufe</a></p></td>
<td><p>Informationen zum Erstellen von automatischen UM-Telefonzentralen und Verwalten von Einstellungen für Navigationsmenüs, Begrüßungen und Geschäftszeiten.</p></td>
</tr>
<tr class="even">
<td><p><a href="set-up-https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/voice-mail-for-users">Einrichten von Voicemail für Benutzer</a></p></td>
<td><p>Informationen zum Erstellen und Verwalten von UM-Postfachrichtlinien und zum Aktivieren von Benutzern für UM.</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-up-client-voice-mail-features-exchange-2013-help.md">Einrichten von Client-Voicemailfunktionen</a></p></td>
<td><p>Informationen zum Einrichten von Clientfeatures zum Aktivieren von Benutzern für den Zugriff und die Verwaltung ihrer Voicemailnachrichten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-outlook-voice-access-pin-security/set-outlook-voice-access-pin-security">Festlegen von Outlook Voice Access-PIN-Sicherheit</a></p></td>
<td><p>Informationen zum Einrichten von PIN-Anforderungen für Outlook Voice Access-Benutzer.</p></td>
</tr>
<tr class="odd">
<td><p><a href="protect-voice-mail-exchange-2013-help.md">Schützen von Voicemail</a></p></td>
<td><p>Informationen zur Verwendung von UM zum Schutz von Sprachnachrichten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/run-voice-mail-call-reports/run-voice-mail-call-reports">Erstellen von Berichten für Sprachanrufe mail</a></p></td>
<td><p>Informationen zu UM-Anrufberichten.</p></td>
</tr>
</tbody>
</table>

