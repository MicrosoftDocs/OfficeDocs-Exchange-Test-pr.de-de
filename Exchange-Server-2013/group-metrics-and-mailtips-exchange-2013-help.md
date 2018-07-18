---
title: 'Gruppe Metriken und e-Mail-Infos: Exchange 2013 Help'
TOCTitle: Gruppe Metriken sowie e-Mail-Infos
ms:assetid: 74a55072-4ba9-45bb-a18f-41afbf3de30b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674302(v=EXCHG.150)
ms:contentKeyID: 50476017
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Gruppe Metriken und e-Mail-Infos

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

Bei der Gruppenmetrik handelt es sich um eine Sammlung der folgenden Informationen zu Verteilergruppen und dynamischen Verteilergruppen in Ihrer Organisation:

  - Anzahl der Mitglieder

  - Anzahl der Mitglieder außerhalb Ihrer Organisation

Gruppenmetrikdaten werden verwendet, um E-Mail-Infos in Microsoft Exchange Server 2013 zu unterstützen. E-Mail-Infos sind informative Meldungen, die dem Absender beim Verfassen einer Nachricht angezeigt werden. Weitere Informationen zu E-Mail-Infos sowie eine vollständige Liste aller in Exchange 2013 verfügbaren E-Mail-Infos finden Sie unter [MailTips](mailtips-exchange-2013-help.md).

Gruppenmetrikdaten werden von den folgenden E-Mail-Infos verwendet:

  - **Große Benutzergruppe**   Diese E-Mail-Info wird angezeigt, wenn ein Absender eine Verteilergruppe hinzufügt, bei der die Anzahl an Mitgliedern dem Wert entspricht, der in Ihrer Organisation für "Große Benutzergruppe" konfiguriert ist. Standardmäßig werden mehr als 25 Empfänger als "Große Benutzergruppe" eingestuft.

  - **Externe Empfänger**   Diese E-Mail-Info wird angezeigt, wenn ein Absender eine Verteilergruppe hinzufügt, deren Mitglieder außerhalb Ihrer Organisation sind.

E-Mail-Infos werden immer dann ausgewertet, wenn ein Absender einen Empfänger zu einer Nachricht hinzufügt. Zum Bereitstellen dieser Informationen berechnet Exchange Gruppenmetrikdaten mit einem Hintergrundprozess, der zur Ausführung außerhalb der regulären Geschäftszeiten Ihrer Organisation geplant werden kann. Beim Auswerten der Empfänger für E-Mail-Infos liest Exchange Gruppenmetrikdaten.

## Generieren von Gruppenmetrikdaten

In Exchange 2013 werden Gruppenmetrikdaten in den Attributen **msExchGroupMemberCount** und **msExchGroupExternalMemberCount** im Gruppenobjekt in Active Directory gespeichert. Folgende Dateien im Ordner "%ExchangeInstallPath%GroupMetrics" sind einer Gruppenmetrik zugeordnet:

  - **Cookie\_*\<nnnnnnnn\>*.dsc**   Diese Textdatei enthält Informationen über den Postfachserver, der zur Generierung der Gruppenmetrikdaten konfiguriert wurde, und den Zeitpunkt der letzten erfolgreichen Generierung der Gruppenmetrik. Auf diese Weise können Gruppenmetrikdaten für Gruppen generiert werden, die seit der letzten Generierung der Gruppenmetrikdaten geändert wurden.

  - **ChangedGroups.txt**   Diese Datei enthält eine Liste der Gruppen, die seit der letzten Generierung der Gruppenmetrikdaten aktualisiert wurden.

Die Generierung der Gruppenmetrikdaten wird durch ein Vermittlungspostfach verarbeitet, das auch als Organisationspostfach bezeichnet wird. Wenn der Paramater *GMGen* in einem Vermittlungspostfach auf `$true` festgelegt ist, ist das Vermittlungspostfach für die Generierung der Gruppenmetrikdaten zuständig.

Der Postfachserver generiert bei der ersten Ausführung des Postfach-Assistenten für Gruppenmetrikdaten vollständige Gruppenmetrikdaten für alle Verteilergruppen und dynamischen Verteilergruppen; inkrementelle Updates werden für alle Gruppen generiert, die seit der letzten vollständigen Generierung geändert wurden. Standardmäßig werden Gruppenmetrikdaten täglich zu einem zufälligen Zeitpunkt generiert, wenn die Arbeitsauslastung des Exchange-Servers gering ist. Wenn die Arbeitsauslastung konstant hoch ist, kann die Generierung der Gruppenmetrikdaten übersprungen werden.

Informationen zur Generierung der Gruppenmetrikdaten finden unter [Konfigurieren der Gruppenmetrik](configure-group-metrics-exchange-2013-help.md).

