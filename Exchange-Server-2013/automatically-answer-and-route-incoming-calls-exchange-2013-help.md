---
title: 'Autom. Beantworten und Weiterleiten eingehender Anrufe: Exchange 2013-Hilfe'
TOCTitle: Automatisches Beantworten und Weiterleiten eingehender Anrufe
ms:assetid: d3dcd488-bd57-44cc-bdd4-ddee42a69dde
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124724(v=EXCHG.150)
ms:contentKeyID: 50476786
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Automatisches Beantworten und Weiterleiten eingehender Anrufe

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-08-26_

Microsoft Exchange Unified Messaging (UM) ermöglicht je nach den Anforderungen Ihrer Organisation die Einrichtung einer oder mehrerer automatischer UM-Telefonzentralen. Im Gegensatz zu anderen Unified Messaging-Komponenten, z. B. UM-Wähleinstellungen und UM-IP-Gateways, ist die Einrichtung automatischer UM-Telefonzentralen nicht unbedingt erforderlich. Automatische Telefonzentralen helfen internen und externen Anrufern jedoch beim Auffinden von Benutzern oder Abteilungen in einer Organisation, um Anrufe an diese weiterzuleiten. In diesem Thema wird das automatische UM-Telefonzentralenfeature in Unified Messaging erläutert.

**Inhalt**

Automatische Telefonzentralen

Automatische UM-Telefonzentralen

Automatische Telefonzentrale mit mehreren Sprachen

Begrüßungen für außerhalb und während der Geschäftszeiten

Menünavigationseinträge

Beispiele für automatische Telefonzentralen

## Automatische Telefonzentralen

In Telefonie- bzw. Unified Messaging-Umgebungen verbindet eine automatische Telefonzentrale bzw. deren Menüsystem Anrufer mit der Durchwahl eines Benutzers oder einer Abteilung ohne Eingriffe durch Mitarbeiter der Vermittlungsstelle. Bei vielen automatischen Telefonzentralensystemen kann durch das Drücken von bzw. die Spracheingabe "Null" eine Verbindung mit der Telefonvermittlung hergestellt werden. Eine automatische Telefonzentrale ist in den meisten modernen Nebenstellenanlagen, IP-Nebenstellenanlagen und Unified Messaging-Lösungen vorhanden.

Bei einigen automatischen Telefonzentralensystemen gibt es rein informative Ansagemenüs und Sprachmenüs, über die eine Organisation ihre Geschäftszeiten, Hinweise zur Anfahrt zu ihren Standorten, Informationen zu freien Stellen und Antworten auf häufig gestellte Fragen bekannt geben kann. Nach Wiedergabe der Ansage wird der Anrufer mit der Vermittlungsstelle verbunden oder kann zum Hauptmenü zurückkehren.

In komplexeren automatischen Telefonzentralensystemen dient das Menüsystem zum Suchen nach anderen Menüs der automatischen Telefonzentrale, zum Auffinden eines Benutzers im System oder zum Verbinden mit einer anderen Amtsleitung. Das Menüsystem ermöglicht dem Anrufer auch die Interaktion mit dem System in bestimmen Situationen, z. B. wenn ein Student sich bei einem Seminar anmeldet, seine Noten abfragt oder eine Kreditkarte per Telefon aktiviert wird.

Obgleich automatische Telefonzentralen meist sehr nützlich sind, können sie bei falscher Planung und Konfiguration Anrufer verwirren und frustrieren. Insbesondere in großen Organisationen können Anrufer bei nicht ordnungsgemäß konfigurierter automatischer Telefonzentrale durch eine Vielzahl von Fragen und Menüansagen geführt werden, ehe sie letztlich mit einer Person verbunden werden, die ihre Frage beantworten kann.

## Automatische UM-Telefonzentralen

Unified Messaging ermöglicht je nach den Anforderungen Ihrer Organisation die Einrichtung einer oder mehrerer automatischer UM-Telefonzentralen. Automatische UM-Telefonzentralen dienen zum Erstellen eines sprachgesteuerten Menüsystems für eine Organisation, mit dessen Hilfe sich interne und externe Anrufer im Menüsystem der automatischen UM-Telefonzentrale bewegen können, um Benutzer und Abteilungen in einer Organisation auffinden und Anrufe an diese richten oder weiterleiten zu können.

Wenn anonyme oder nicht authentifizierte Benutzer eine externe geschäftliche Telefonnummer oder interne Anrufer eine bestimmte Durchwahlnummer anrufen, wird eine Folge von Ansagen wiedergegeben, mit deren Hilfe sie sich mit einem Benutzer verbinden bzw. einen Benutzer in der Organisation auffinden und sich anschließend mit diesem Benutzer verbinden können. Die automatische UM-Telefonzentrale gibt eine Folge von Telefonansagen bzw. WAV-Dateien wieder, die Anrufer anstelle eines Mitarbeiters der Vermittlungsstelle hören, wenn sie eine Organisation anrufen, die mit Unified Messaging arbeitet. Die automatische UM-Telefonzentrale ermöglicht Anrufern, sich mithilfe von MFV-Tasten- oder Spracheingaben durch das Menüsystem zu bewegen, Anrufe zu tätigen oder Benutzer aufzufinden. Damit die automatische Spracherkennung oder Spracheingaben verwendet werden können, muss die automatische Spracherkennung jedoch für die automatische UM-Telefonzentrale aktiviert werden.

Eine automatische UM-Telefonzentrale bietet Folgendes:

  - Geschäftliche oder informative Begrüßungsansagen.

  - Benutzerdefinierte unternehmensbezogene Menüs. Sie können diese Menüs auf mehrere Ebenen erweitern.

  - Eine Telefonbuchsuchfunktion, mit deren Hilfe ein Anrufer das Telefonbuch der Organisation nach einem Namen durchsuchen kann.

  - Eine Möglichkeit für den Anrufer, sich mit einem Mitarbeiter verbinden zu lassen oder diesem eine Nachricht zu hinterlassen.

Sie können eine unbegrenzte Anzahl von automatischen UM-Telefonzentralen erstellen. Jede automatische Unified Messaging-Telefonzentrale kann eine unbeschränkte Anzahl von Durchwahlnummern unterstützen. Eine automatische UM-Telefonzentrale kann nur auf einen einzigen Satz mit UM-Wähleinstellungen verweisen. Automatische UM-Telefonzentralen können auch auf andere automatische UM-Telefonzentralen verweisen oder mit diesen verknüpft werden.

Ein eingehender Anruf von einer externen Telefonnummer oder eine interne Telefondurchwahl werden zwischen Exchange-Servern übergeben und anschließend an eine automatische UM-Telefonzentrale gesendet. Die automatische UM-Telefonzentrale wird vom Administrator für die Verwendung von vorab aufgezeichneten Sprachdateien (WAV-Dateien) konfiguriert, die für Anrufer wiedergegeben werden und ihnen ermöglichen, durch das Unified Messaging-Menüsystem zu navigieren. Sie können bei der Konfiguration einer automatischen UM-Telefonzentrale alle verwendeten WAV-Dateien an die Anforderungen Ihrer Organisation anpassen.

Zurück zum Seitenanfang

## Automatische Telefonzentrale mit mehreren Sprachen

Es sind Situationen vorstellbar, in denen Sie für Anrufer automatische Telefonzentralen in verschiedenen Sprachen bereitstellen müssen. Mit der für eine automatische UM-Telefonzentrale verfügbaren Spracheinstellung können Sie die Standardansagesprache für die automatische Telefonzentrale konfigurieren. Wenn Sie die Standardsystemansagen für die automatische Telefonzentrale verwenden, ist dies die Sprache, die ein Anrufer hört, wenn die automatische Telefonzentrale den eingehenden Anruf beantwortet. Diese Spracheinstellung wirkt sich nur auf die verfügbaren standardmäßigen Systemansagen aus. Diese Spracheinstellung wirkt sich nicht auf benutzerdefinierte Ansagen aus, die für eine automatische Telefonzentrale konfiguriert werden.

Wenn Sie bei lokalen oder Hybridbereitstellungen die US-englische Version installieren, ist Englisch (USA) die einzige Sprache, die zum Konfigurieren automatischer UM-Telefonzentralen verfügbar ist. Wenn Sie eine lokalisierte Version installieren, beispielsweise Japanisch, können Sie für die von Ihnen erstellte automatische Telefonzentrale festlegen, ob als Standardsprache Japanisch oder Englisch (USA) verwendet wird. Auf einem Unified Messaging-Server können zusätzliche UM-Sprachpakete installiert werden, um andere Standardsprachen für eine automatische Telefonzentrale zu verwenden.

Wenn Sie z. B. ein Geschäft an einem Standort in den Vereinigten Staaten betreiben und dennoch ein Menüsystem erforderlich ist, das für Anrufer die Optionen Englisch (USA), Spanisch und Französisch bereitstellt, müssen Sie zuerst die benötigten UM-Sprachpakete installieren. Wenn Sie die englische Version (USA) installiert haben, installieren Sie in diesem Fall die UM-Sprachpakete für Spanisch und Französisch. Da für eine automatische Unified Messaging-Telefonzentrale jedoch immer nur jeweils eine Sprache konfiguriert sein kann, müssen vier automatische Telefonzentralen erstellt werden: eine automatische Haupttelefonzentrale, die für die Verwendung von Englisch (USA) konfiguriert ist, sowie eine weitere automatische Telefonzentrale für jede weitere Sprache: Englisch (USA), Spanisch und Französisch. Anschließend konfigurieren Sie die automatische Haupttelefonzentrale so, dass sie über die richtigen Tastenzuordnungen bzw. die richtige Menünavigation für den Zugriff auf die anderen automatischen Telefonzentralen verfügt, die Sie für jede Sprache erstellt haben. In diesem Beispiel beantwortet die automatische Haupttelefonzentrale den eingehenden Anruf, und der Anrufer hört "Welcome to Contoso, Ltd. For English, press or say 1. For Spanish, press or say 2. For French, press or say 3."


> [!TIP]
> In Exchange UM können authentifizierte und nicht authentifizierte Outlook Voice Access Benutzer nicht in allen Sprachen per Sprachangabe im Verzeichnis nach Benutzern suchen. Anrufer, die in einer automatischen Telefonzentrale anrufen, können die Spracheingabe jedoch in mehreren Sprachen für die Navigation im Menü der automatischen Telefonzentrale und die Suche nach Benutzern in dem Verzeichnis verwenden.



Zurück zum Seitenanfang

## Begrüßungen für außerhalb und während der Geschäftszeiten

Nachdem Sie eine automatische UM-Telefonzentrale erstellt haben, wird für Anrufer eine Standardsystemansage als Begrüßungsansage für das Hauptmenü außerhalb der Geschäftszeiten wiedergegeben, nachdem die Begrüßung außerhalb der Geschäftszeiten wiedergegeben wurde. Auch wenn Systemansagen nicht ersetzt oder geändert werden dürfen, möchten Sie möglicherweise die Begrüßungen und Ansagen für das Menü anpassen, die für automatische UM-Telefonzentralen verwendet werden. Häufig möchten Sie wahrscheinlich nicht nur eine benutzerdefinierte Begrüßung außerhalb der Geschäftszeiten konfigurieren, sondern auch eine benutzerdefinierte Ansage für das Hauptmenü außerhalb der Geschäftszeiten erstellen und konfigurieren. Nachdem Sie eine benutzerdefinierte Ansage für das Hauptmenü außerhalb der Geschäftszeiten konfiguriert haben, müssen Sie für die automatische UM-Telefonzentrale Tastenzuordnungen außerhalb der Geschäftszeiten aktivieren.

Eine benutzerdefinierte Ansage für das Hauptmenü außerhalb der Geschäftszeiten ist eine Liste der Optionen, die außerhalb der Geschäftszeiten für Anrufer wiedergegeben werden. Damit für Anrufer eine Telefonansage für das Hauptmenü außerhalb der Geschäftszeiten wiedergegeben wird, müssen Sie zuerst in der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **Set-UMAutoAttendant** in der Shell den Zeitplan für die Geschäftszeiten und die Zeiten außerhalb der Geschäftszeiten konfigurieren. Beispiel: "Sie rufen Trey Research außerhalb der normalen Geschäftszeiten an. Wenn es sich um einen medizinischen Notfall handelt, legen Sie auf und rufen dann 110 an. Um einem unserer Ärzte eine Nachricht zu hinterlassen, drücken Sie die 1. Um einem unserer Physiotherapeuten eine Nachricht zu hinterlassen, drücken Sie die 2. Um eine allgemeine Nachricht für das Empfangspersonal zu hinterlassen, drücken Sie die 3. Um mit einer Vermittlung verbunden zu werden, die außerhalb der Geschäftszeiten verfügbar ist, drücken Sie die 0."

Wenn Sie eine automatische UM-Telefonzentrale erstellen, sind standardmäßig die Begrüßungen und Telefonansagen innerhalb und außerhalb der Geschäftszeiten nicht konfiguriert, und es sind keine Menünavigationseinträge für Telefonansagen für das Hauptmenü innerhalb und außerhalb der Geschäftszeiten definiert. Um die benutzerdefinierten Begrüßungen und Ansagen für das Hauptmenü außerhalb der Geschäftszeiten ordnungsgemäß zu konfigurieren, müssen Sie die folgenden Aufgaben ausführen:

1.  Konfigurieren der Zeiten während und außerhalb der Geschäftszeiten auf der Seite **Geschäftszeiten**.

2.  Erstellen der Begrüßungsdatei, die für die Begrüßung außerhalb der Geschäftszeiten verwendet wird.

3.  Konfigurieren der Begrüßung außerhalb der Geschäftszeiten auf der Seite **Begrüßungen**.

4.  Erstellen der Begrüßungsdatei, die für die Ansage für das Hauptmenü außerhalb der Geschäftszeiten verwendet wird.

5.  Konfigurieren der Begrüßungsansage für das Hauptmenü außerhalb der Geschäftszeiten auf der Seite **Begrüßungen**.

6.  Aktivieren der Menünavigation und Hinzufügen von Menünavigationseinträgen auf der Seite **Menünavigation**.

Zurück zum Seitenanfang

## Menünavigationseinträge

Wenn Sie die standardmäßige Telefonansage für das Hauptmenü verwenden und einen oder mehrere Menünavigationseinträge definieren, synthetisiert das UM-TTS-Modul (Text-zu-Sprache) eine Telefonansage für das Hauptmenü. Das TTS-Modul synthetisiert eine Telefonansage für das Hauptmenü jedoch nur, wenn die Standardbegrüßung konfiguriert und mindestens ein Menünavigationseintrag definiert wurde. Das TTS-Modul synthetisiert keine Telefonansage für das Hauptmenü, wenn Sie eine benutzerdefinierte Telefonansage für das Hauptmenü verwenden. Beispiel: "Drücken Sie die 1, wenn Sie mit der Vertriebsabteilung sprechen möchten. Drücken Sie die 2, wenn Sie mit dem Kundensupport sprechen möchten." Zum Erstellen dieser Telefonansage für das Hauptmenü müssen Sie zwei Menünavigationseinträge erstellen: eine mit der Bezeichnung "Vertriebsabteilung" und eine weitere mit der Bezeichnung "Kundensupport". Anschließend wird der Tastenzuordnungseintrag zum Abspielen einer Audiodatei, zur Weiterleitung an eine Durchwahl oder zur Weiterleitung des Anrufers an eine andere automatische Telefonzentrale konfiguriert.

Beim Konfigurieren von Menünavigationseinträgen definieren Sie die Optionen und Vorgänge, die durchgeführt werden, wenn ein Anrufer bei Verwendung einer sprachaktivierten automatischen Telefonzentrale ein bestimmtes Wort sagt oder bei Verwendung einer nicht sprachaktivierten automatischen Telefonzentrale eine Taste auf der Telefontastatur drückt. Zum Konfigurieren von Menünavigationseinträgen für eine automatische Telefonzentrale müssen Sie folgende Aktionen ausführen:

  - Aktivieren die Menünavigation während der Geschäftszeit.

  - Hinzufügen von Menünavigationseinträgen.

  - Eingeben des Namens des Menünavigationseintrags.

  - Auswählen einer Option in der Liste **Wenn diese Taste gedrückt wird** und Hochladen der wiederzugebenden Audiodatei über das Feld **Folgende Audiodatei wiedergeben**.

  - Konfigurieren der auszuführenden Aktion:
    
      - Weiterleiten an diese Durchwahl
    
      - Weiterleiten an diese automatische UM-Telefonzentrale
    
      - Sprachnachricht für diesen Benutzer hinterlassen
    
      - Unternehmensstandort ansagen
    
      - Geschäftszeiten ansagen

Zurück zum Seitenanfang

## Beispiele für automatische Telefonzentralen

Die folgenden Beispiele veranschaulichen die Verwendung von automatischen UM-Telefonzentralen mit Unified Messaging:

  - **Beispiel 1**   Bei dem Unternehmen Contoso, Ltd. können externe Kunden drei externe Telefonnummern wählen: 01234 555 0111 (Unternehmensstandorte), 01234 555 0122 (Produktsupport) und 01234 555 0133 (Vertrieb). Die Abteilungen "Personalabteilung", "Verwaltung" und "Buchführung" verfügen über interne Durchwahlnummern, auf die über die automatische UM-Telefonzentrale "Unternehmensstandorte" zugegriffen werden muss.
    
    Um eine automatische UM-Telefonzentralenstruktur einzurichten, die dieses Szenario unterstützt, müssen drei automatische UM-Telefonzentralen mit jeweils der entsprechenden externen Telefonnummer erstellt und konfiguriert werden. Erstellen Sie für jede Abteilung von "Unternehmensstandorte" drei weitere automatische UM-Telefonzentralen. Anschließend konfigurieren Sie jede weitere automatische UM-Telefonzentrale basierend auf den jeweiligen Anforderungen, z. B. mit einer Begrüßungsansage oder anderen Informationen zur Navigation.

  - **Beispiel 2**   Bei dem Unternehmen Contoso, Ltd. müssen externe Kunden die zentrale Telefonnummer 0425 555 0100 anrufen. Ruft ein externer Anrufer die zentrale Nummer an, nimmt die automatische UM-Telefonzentrale den Anruf an und gibt die folgende Ansage wieder: "Willkommen bei Contoso, Ltd. Drücken oder sagen Sie 'Eins', um mit der Unternehmensverwaltung verbunden zu werden. Drücken oder sagen Sie 'Zwei', um mit dem Produktsupport verbunden zu werden. Drücken oder sagen Sie 'Drei', um mit der Informationszentrale verbunden zu werden. Drücken oder sagen Sie 'Null', um mit einem Mitarbeiter der Vermittlungsstelle verbunden zu werden." Um eine automatische UM-Telefonzentralenstruktur einzurichten, die dieses Szenario unterstützt, müssen Sie eine automatische UM-Telefonzentrale mit angepassten Durchwahlnummern einrichten, damit der Anruf an die entsprechende Durchwahlnummer weitergeleitet werden kann.

Zurück zum Seitenanfang

