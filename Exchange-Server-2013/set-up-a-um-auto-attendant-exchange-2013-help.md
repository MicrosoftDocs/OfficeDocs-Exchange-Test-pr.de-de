---
title: 'Einrichten einer automatischen UM-Telefonzentrale: Exchange 2013 Help'
TOCTitle: Einrichten einer automatischen UM-Telefonzentrale
ms:assetid: 0a3492f8-8aba-4904-96fd-6e023175012a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673508(v=EXCHG.150)
ms:contentKeyID: 50475042
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichten einer automatischen UM-Telefonzentrale

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Bei Verwendung von Unified Messaging (UM) können Benutzer nicht nur auf Voicemail zugreifen, sondern Sie können darüber hinaus abhängig von den Anforderungen Ihrer Organisation eine oder mehrere automatische UM-Telefonzentralen erstellen. Automatische UM-Telefonzentralen dienen zum Erstellen eines sprachgesteuerten Menüsystems für eine Organisation, mit dessen Hilfe externe und interne Anrufer Benutzer und Abteilungen in einer Organisation suchen und Anrufe an diese tätigen oder durchstellen können.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Automatische Telefonzentralen

In Telefonie- bzw. Unified Messaging-Umgebungen verbindet eine automatische Telefonzentrale bzw. deren Menüsystem Anrufer mit der Durchwahl eines Benutzers oder einer Abteilung ohne Eingriffe durch Mitarbeiter der Vermittlungsstelle. Bei vielen automatischen Telefonzentralensystemen kann durch das Drücken von bzw. die Spracheingabe "Null" eine Verbindung mit der Telefonvermittlung hergestellt werden. Bei einigen automatischen Telefonzentralensystemen gibt es rein informative Ansagemenüs und Sprachmenüs, über die eine Organisation ihre Geschäftszeiten, Hinweise zur Anfahrt zu ihren Standorten, Informationen zu freien Stellen und Antworten auf häufig gestellte Fragen bekannt geben kann. Nach Wiedergabe der Ansage wird der Anrufer mit der Vermittlungsstelle verbunden oder kann zum Hauptmenü zurückkehren.

Obgleich automatische Telefonzentralen meist sehr nützlich sind, können sie bei falscher Planung und Konfiguration Anrufer verwirren und frustrieren. Insbesondere in großen Organisationen können Anrufer bei nicht ordnungsgemäß konfigurierter automatischer Telefonzentrale durch eine Vielzahl von Fragen und Menüansagen geführt werden, ehe sie letztlich mit einer Person verbunden werden, die ihre Frage beantworten kann.

## Wie richte ich eine automatische Telefonzentrale ein?

In der Exchange-Verwaltungskonsole können Sie automatische UM-Telefonzentralen einrichten und verwalten, um Anrufe für die Organisation automatisch annehmen zu lassen und Anrufern die Auswahl verschiedener Optionen mit den Tasten auf ihrem Telefon zu ermöglichen. Sie können eine einzelne automatische UM-Telefonzentrale einrichten, die Anrufern grundlegende Menünavigation bietet, oder Sie können mehrere geschachtelte und sich verzweigende automatische Telefonzentralen einrichten, die Anrufern eine umfangreichere Erfahrung bieten. In beiden Fällen müssen Sie Ihre automatischen Telefonzentralen jedoch sorgfältig planen und einrichten.

Gehen Sie folgendermaßen vor, um eine neue automatische UM-Telefonzentrale zu planen und zu erstellen:

1.  Entscheiden Sie, ob Benutzer die Möglichkeit haben sollen, über Spracheingaben mit der automatischen Telefonzentrale zu interagieren.

2.  Entscheiden Sie, welche Sprache für Ihre automatische Haupttelefonzentrale verwendet werden soll und ob weitere automatische Telefonzentralen zur Unterstützung zusätzlicher Sprachen erstellt werden müssen.

3.  Entscheiden Sie, welche Geschäftszeiten für die automatische Telefonzentrale gelten sollen, und legen Sie diese über die Option **Geschäftszeiten** fest. Wenngleich dies nicht erforderlich ist, können Sie auch einen Feiertagszeitplan für diese automatische Telefonzentrale festlegen.
    

    > [!NOTE]
    > Außerdem sollten Sie die Zeitzone für die Telefonzentrale angeben.



4.  Entscheiden Sie, ob standardmäßige, vom System generierte Begrüßungen während und außerhalb der Geschäftszeiten verwendet werden sollen, oder ob Sie benutzerdefinierte Aufzeichnungen erstellen möchten.
    
    Wenn Sie benutzerdefinierte Begrüßungen verwenden möchten, sollten Sie die Begrüßungen planen und aufzeichnen, die während und außerhalb der Geschäftszeiten für Anrufer wiedergegeben werden. Bei Bedarf können Sie auch eine benutzerdefinierte Informationsansage als Begrüßung erstellen. Beispielsweise können Sie als Begrüßung während der Geschäftszeiten folgende Ansage aufzeichnen: „Herzlich willkommen bei Contoso. Wenn Sie technischen Support benötigen, drücken oder sagen Sie 1. Wenn Sie mit einem Vertriebsmitarbeiter sprechen möchten, drücken oder sagen Sie 2.“ Für eine Begrüßung außerhalb der Geschäftszeiten können Sie beispielsweise das folgende Skript aufzeichnen: "Herzlich willkommen bei Contoso. Unser Büro ist vorübergehend geschlossen. Wir sind ab Montag, 8:00 Uhr, wieder für Sie da.“

5.  Planen Sie die Struktur Ihrer automatischen Telefonzentrale gemäß Ihren individuellen Geschäftsanforderungen. Ein multinationales Unternehmen mit Niederlassungen in Deutschland und Großbritannien würde z. B. eine Struktur mit mehreren Sprachen benötigen. Und ein Unternehmen mit verschiedenen Niederlassungen für Zentrale, Vertrieb und Kundendienst würde eine automatische Telefonzentrale benötigen, die direkt mit der Unternehmensstruktur verknüpft ist.

6.  Entscheiden Sie, ob Sie automatische DTMF-Fallback-Telefonzentralen oder andere automatische Telefonzentralen benötigen, wenn die Sprachbefehle der automatischen Telefonzentrale nicht funktionieren.

7.  Planen Sie die Menünavigation für Zeitspannen innerhalb und außerhalb der Geschäftszeiten. Für jede automatische Telefonzentrale (einschließlich automatische DTMF-Telefonzentralen) müssen Menüansagen und Einträge für die Menünavigation geplant und konfiguriert werden. Diese Schritte sind sowohl für Zeitspannen innerhalb als auch außerhalb der Geschäftszeiten erforderlich.

8.  Folgendes ist ein Beispiel für ein Arbeitsblatt, mit dem Sie die Menünavigation außerhalb der Geschäftszeiten planen können.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><strong>Taste</strong></th>
    <th><strong>Name der Ansage/des Eintrags im Navigationsmenü</strong></th>
    <th><strong>Antwort auf Aufzeichnung</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>1</p></td>
    <td><p>Sprachauswahl für Englisch.</p></td>
    <td><p>&quot;Drücken oder sagen Sie 1, um zur englischen Navigation zu wechseln.&quot;</p></td>
    </tr>
    <tr class="even">
    <td><p>2</p></td>
    <td><p>Kontostand</p></td>
    <td><p>&quot;Drücken oder sagen Sie 2, um Ihren Kontostand abzurufen.&quot;</p></td>
    </tr>
    <tr class="odd">
    <td><p>3</p></td>
    <td><p>Weiterleitung zum Vertrieb</p></td>
    <td><p>&quot;Drücken oder sagen Sie 3, um zu unserer Verkaufsabteilung durchgestellt zu werden.&quot;</p></td>
    </tr>
    <tr class="even">
    <td><p>4</p></td>
    <td><p>Weiterleitung zum Kundendienst</p></td>
    <td><p>“Drücken oder sagen Sie 4, um mit einem Kundendienstmitarbeiter verbunden zu werden.”</p></td>
    </tr>
    <tr class="odd">
    <td><p>5</p></td>
    <td><p>Geschäftszeiten</p></td>
    <td><p>Keine Antwort erforderlich.</p></td>
    </tr>
    <tr class="even">
    <td><p>6</p></td>
    <td><p>Geschäftsstandort</p></td>
    <td><p>Keine Antwort erforderlich.</p></td>
    </tr>
    </tbody>
    </table>


9.  Zeichnen Sie anhand des Menünavigationsplans Ansagen auf, mit denen die Anrufer über ihre Optionen informiert werden: Zum Beispiel können Sie bei der in der Tabelle dargestellten Menünavigation außerhalb der Geschäftszeiten das folgende Skript aufzeichnen: "Um eine Nachricht an die Vertriebsabteilung zu hinterlassen, drücken Sie die Eins. Drücken Sie die Zwei, um unsere Geschäftszeiten zu erfahren. Drücken Sie die Drei, um unsere Adresse zu erfahren."

10. Legen Sie fest, wie Anrufer auf Ihre Organisation zugreifen werden. Berücksichtigen Sie, wie diese Anrufer nach Benutzern in Ihrer Organisation suchen und diese kontaktieren werden. Berücksichtigen Sie außerdem, wie Anrufer weitergeleitet werden. Dies umfasst u. a., wie Anrufer mit einem Mitarbeiter verbunden werden bzw. ob Anrufer während und außerhalb der Geschäftszeiten an eine Vermittlungsstelle weitergeleitet werden.

11. Legen Sie fest, welche Anrufe Anrufer tätigen können, wenn sie eine bestimmte automatische Telefonzentrale verwenden. Bestimmen Sie z. B., ob Anrufer Benutzer in einem einzigen Wählplan oder mit einer beliebigen Durchwahl anrufen dürfen bzw. ob externe Anrufe getätigt werden können.

12. Nachdem Sie die Einstellungen für die automatische Telefonzentrale, Begrüßungen und Menünavigation geplant haben und Audiodateien mit den aufgezeichneten Begrüßungen sowie den Menünavigationsansagen und -antworten erstellt haben, kann die automatische Telefonzentrale erstellt und konfiguriert werden. Vorgehensweise:
    
      - [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant)
    
      - [Verwalten einer automatischen UM-Telefonzentrale](manage-a-um-auto-attendant-exchange-2013-help.md)

13. Wenn Sie die Struktur und die Einstellungen der automatischen Telefonzentrale erstellt und konfiguriert haben, aktivieren Sie die automatische UM-Telefonzentrale, sodass Anrufe entgegengenommen werden können.

