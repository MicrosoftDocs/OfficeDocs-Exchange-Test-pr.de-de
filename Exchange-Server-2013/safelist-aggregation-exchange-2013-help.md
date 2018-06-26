---
title: 'Aggregation von Listen sicherer Adressen: Exchange 2013 Help'
TOCTitle: Aggregation von Listen sicherer Adressen
ms:assetid: f05430a0-0405-4b65-a18d-18c9e86a13c4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125168(v=EXCHG.150)
ms:contentKeyID: 50477034
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aggregation von Listen sicherer Adressen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-09-30_

In Microsoft Exchange Server 2013 bezeichnet der Begriff *Aggregation von Listen sicherer Adressen* die gemeinsamen Antispamfunktionen von Microsoft Outlook und Exchange. Diese Funktion erfasst Daten aus den Listen "Sichere Empfänger", "Sichere Absender" und "Geblockte Absender" zur Abwehr von Spam sowie aus den Kontaktdaten, die von Outlook-Benutzern konfiguriert werden, und stellt diese den Exchange-Agents zur Spambekämpfung zur Verfügung.

Wenn Sie die Aggregation von Listen sicherer Adressen aktivieren und ordnungsgemäß konfigurieren, übergibt der Inhaltsfilter-Agent sichere E-Mail-Nachrichten ohne weitere Verarbeitung an das Unternehmenspostfach. E-Mail-Nachrichten, die Outlook-Benutzer von Kontakten erhalten, die diese Benutzer ihrer Liste sicherer Empfänger und Absender sowie vertrauenswürdiger Kontakte in Outlook hinzugefügt haben, werden vom Inhaltsfilter-Agent als sicher eingestuft. Ein Outlook-*Kontakt* ist eine Person in oder außerhalb der Organisation des Benutzers, zu der der Benutzer mehrere Informationen speichern kann, z. B. die E-Mail- und postalische Adresse, Telefon- und Faxnummer sowie URLs von Webseiten.

In Exchange 2013 ermöglicht die Aggregation von Listen sicherer Adressen dem Absenderfilter-Agent auch, eingehende Nachrichten in der empfängerbezogenen blockierten Absenderliste zu blockieren.

Sie kann dazu beitragen, dass die Anzahl der von der Exchange-Spamfilterung fälschlicherweise herausgefilterten (falsch positiven) E-Mail-Nachrichten verringert wird. Bei der Spamfilterung liegt ein *falsch positives Ergebnis* vor, wenn ein Spamfilter eine erwünschte Nachricht fälschlicherweise als Spam identifiziert.

Bei Organisationen, die täglich Hunderttausende von Nachrichten aus dem Internet filtern, kann selbst ein kleiner Prozentsatz falsch positiver Ergebnisse bedeuten, dass Benutzer viele Nachrichten nicht empfangen, die fälschlicherweise als Spam identifiziert wurden, wenn diese in Quarantäne verschoben oder gelöscht werden.

Die Aggregation von Listen sicherer Adressen ist wahrscheinlich die effektivste Maßnahme zur Vermeidung falsch positiver Meldungen. In Outlook 2010 oder neueren Versionen können Benutzer *Listen sicherer Absender* erstellen. In Listen sicherer Absender werden Domänennamen und E-Mail-Adressen angegeben, von denen der Outlook-Benutzer Nachrichten empfangen möchte. Standardmäßig enthält diese Liste E-Mail-Adressen in Outlook-Kontakten und in der globalen Adressliste von Exchange. Outlook fügt der Liste sicherer Absender standardmäßig alle externen Kontakte hinzu, an die der Benutzer E-Mail-Nachrichten sendet.

**Inhalt**

Information stored in the Outlook user's safelist collection

How Exchange uses the safelist collection

Hashing of safelist collection entries

Enabling safelist aggregation

## In der Sammlung von Listen sicherer Adressen des Outlook-Benutzers gespeicherte Informationen

Eine *Sammlung von Listen sicherer Adressen* enthält die zusammengefassten Daten aus den Listen sicherer Absender, sicherer Empfänger, blockierter Absender und externer Kontakte. Diese Daten werden in Outlook und im Exchange-Postfach gespeichert.

Die folgenden Informationen werden in einer Sammlung von Listen sicherer Adressen eines Outlook-Benutzers gespeichert:

  - **Sichere Absender und Empfänger**   Der Nachrichtenkopf Von: gibt einen Absender an. Das Feld "An:" der E-Mail-Nachricht gibt einen Empfänger an. Sichere Absender und Empfänger werden durch vollständige SMTP-Adressen (Simple Mail Transfer Protocol) angegeben, z. B. "masato@contoso.com". Outlook-Benutzer können Absender und Empfänger ihren Listen sicherer Adressen hinzufügen.

  - **Blockierte Absender**   Wie bei den sicheren Absendern können Benutzer unerwünschte Absender ihren Listen blockierter Absender hinzufügen und sie auf diese Weise blockieren.

  - **Sichere Domäne**   Die Domäne ist Teil einer SMTP-Adresse, die auf das Symbol "@" folgt. Beispielsweise ist "contoso.com" die Domäne in der Adresse "masato@contoso.com". Outlook-Benutzer können Absenderdomänen ihren Listen sicherer Adressen hinzufügen.
    

    > [!IMPORTANT]
    > Standardmäßig schließt Exchange bei der Aggregation von Listen sicherer Adressen die Domänen nicht ein. Sie können jedoch die Aggregation von Listen sicherer Adressen so konfigurieren, dass sie sicheren Domänendaten für die Antispam-Agents mit einschließt. Weitere Informationen finden Sie unter <A href="configure-content-filtering-to-use-safe-domain-data-exchange-2013-help.md">Konfigurieren der Inhaltsfilterung für eine Verwendung sicherer Domänendaten</A>.



  - **Externe Kontakte**   Zwei Typen externer Kontakte können der Aggregation von Listen sicherer Adressen hinzugefügt werden. Der erste externe Kontakttyp enthält Kontakte, an die Outlook-Benutzer E-Mail-Nachrichten gesendet haben. Diese Gruppe von Kontakten wird der Liste sicherer Absender nur dann hinzugefügt, wenn ein Outlook-Benutzer die entsprechende Option in den Junk-E-Mail-Einstellungen in Outlook 2007 auswählt.
    
    Der zweite externe Kontakttyp enthält die Outlook-Kontakte des Benutzers. Benutzer können diese Kontakte Outlook hinzufügen oder in das Programm importieren. Diese Gruppe von Kontakten wird der Liste sicherer Absender nur dann hinzugefügt, wenn ein Outlook-Benutzer die entsprechende Option in den Junk-E-Mail-Filtereinstellungen in Outlook 2010 oder Outlook 2007 auswählt.

Zurück zum Seitenanfang

## Verwendung der Sammlung von Listen sicherer Adressen durch Exchange

Die Sammlung von Listen sicherer Adressen wird auf dem Postfachserver des Benutzers gespeichert. Exchange 2013 enthält einen Postfach-Assistenten, den Assistenten für Junk-E-Mail-Optionen, der Änderungen an der Sammlung von Listen sicherer Adressen für Ihre Postfächer überwacht. Der Assistent repliziert diese Änderungen in Active Directory. Hier ist die Sammlung von Listen sicherer Adressen für jedes Benutzerobjekt gespeichert. Beim Speichern der Sammlung von Listen sicherer Adressen für das Benutzerobjekt in Active Directory wird diese mit den Antispamfunktionen von Exchange 2013 aggregiert und zur Minimierung von Speicher und Replikation optimiert. Exchange verwendet die Sammlungsdaten von Listen sicherer Adressen bei der Inhaltsfilterung. Wenn in Ihrem Umkreisnetzwerk ein abonnierter Edge-Transport-Server vorhanden ist, repliziert der Microsoft Exchange EdgeSync-Dienst die Sammlung von Listen sicherer Adressen in der AD LDS-Instanz (Active Directory Lightweight Directory Services) auf dem Edge-Transport-Server.


> [!IMPORTANT]
> Obwohl die Daten von sicheren Empfängern in Outlook gespeichert werden und in der Sammlung von Listen sicherer Adressen aggregiert werden können, arbeiten die Inhaltsfilterungsfunktionen nicht mit den Daten sicherer Empfänger.



Zurück zum Seitenanfang

## Hashing von Einträgen in der Sammlung von Listen sicherer Adressen

Die Einträge in der Sammlung von Listen sicherer Adressen werden einem unidirektionalen Hashvorgang (SHA-256) unterzogen, bevor sie als Arraysätze auf drei Benutzerobjektattribute, **msExchSafeSenderHash**, **msExchSafeRecipientHash** und **msExchBlockedSendersHash**, verteilt als Binary Large Object (BLOB) gespeichert werden. Beim Hashvorgang für Daten wird eine Ausgabe fester Länge generiert, die meist auch eindeutig ist. Beim Hashen von Einträgen in der Sammlung von Listen sicherer Adressen wird ein 4-Byte-Hash generiert. Wird eine Nachricht aus dem Internet empfangen, unterzieht Exchange die Absenderadresse einem Hashvorgang und vergleicht diese mit den Hashwerten, die für den Outlook-Benutzer gespeichert sind, an den die Nachricht gesendet wurde. Wenn der Absender dem Hash für sichere Absender entspricht, wird für die Nachricht keine Inhaltsfilterung ausgeführt. Stimmt der Absender mit dem Hash für blockierte Absender überein, wird die Nachricht blockiert.

Beim unidirektionalen Hashen von Einträgen in der Sammlung von Listen sicherer Adressen werden die folgenden wichtigen Aufgaben ausgeführt:

  - **Minimieren von Speicher und Replikationsspeicherplatz**   Meistens wird durch das Hashen die Größe der Daten verringert, die diesem Vorgang unterzogen werden. Dadurch wird beim Speichern und Übertragen einer Hashversion einer Sammlung von Listen sicherer Adressen Speicherplatz und Replikationszeit eingespart. Ein Benutzer mit 200 Einträgen in der Sammlung von Listen sicherer Adressen generiert beispielsweise 800 Byte an Hashdaten, die in Active Directory gespeichert und repliziert werden.

  - **Verhinderung der Ausnutzung von Sammlungen von Listen sicherer Adressen durch bösartige Benutzer**   Da unidirektionale Hashwerte nicht per Reverse Engineering in die ursprüngliche SMTP-Adresse oder Domäne zurückgesetzt werden können, haben Sammlungen von Listen sicherer Adressen keinen Wert für böswillige Benutzer, die ggf. einen Angriff auf den Exchange-Server starten.

Zurück zum Seitenanfang

## Aktivieren der Aggregation von Listen sicherer Adressen

Die Aggregation von Listen sicherer Adressen ist in Exchange 2013 standardmäßig aktiviert. Im Gegensatz zu Exchange Server 2007 müssen Sie das Cmdlet **Update-SafeList** nicht manuell ausführen, um das Hashing zu initiieren und die Sammlung von Listen sicherer Adressen in Active Directory zu schreiben. In Exchange 2013 werden die Sammlungsdaten von Listen sicherer Adressen vom Assistenten für Junk-E-Mail-Optionen in Active Directory geschrieben.

Um die Daten der Aggregation von Listen sicherer Adressen in Active Directory den Edge-Transport-Servern im Umkreisnetzwerk zur Verfügung zu stellen, müssen Sie den Microsoft Exchange EdgeSync-Dienst installieren und so konfigurieren, dass die Daten der Aggregation von Listen sicherer Adressen nach AD LDS repliziert werden.

Sie können die Aggregation von Listen sicherer Adressen dennoch manuell mithilfe des Cmdlets **UpdateSafelist** ausführen. Berücksichtigen Sie dabei jedoch den Netzwerk- und Replikationsdatenverkehr, den Sie bei der Ausführung dieses Befehls hervorrufen können. Wenn **Update-Safelist** für mehrere Postfächer ausgeführt wird, die in großem Umfang von Listen sicherer IP-Adressen Gebrauch machen, kann dies einen erheblichen Datenverkehr verursachen. Wenn der Befehl für mehrere Postfächer ausgeführt werden soll, ist es empfehlenswert, den Befehl außerhalb von Spitzen- und Arbeitszeiten auszuführen.

Das Cmdlet **Update-SafeList** liest die Sammlung von Listen sicherer Adressen im Postfach des Benutzers, wendet einen Hashvorgang auf alle Einträge an, sortiert die Einträge zur Vereinfachung von Suchvorgängen und konvertiert den Hashwert in ein binäres Attribut. Schließlich vergleicht das Cmdlet **Update-SafeList** das erstellte binäre Attribut mit allen in dem Attribut gespeicherten Werten. Stimmen die beiden Werte überein, aktualisiert das Cmdlet **Update-SafeList** den Benutzerattributwert nicht mit den Daten der Aggregation von Listen sicherer Adressen. Unterscheiden sich die beiden Attributwerte, aktualisiert das Cmdlet **Update-SafeList** den Wert der Aggregation von Listen sicherer Adressen.

Zurück zum Seitenanfang

