---
title: 'Zulassen d. Weiterleitung v. Anr. für Voicemailbenutzer: Exchange 2013-Hilfe'
TOCTitle: Zulassen, dass Voice Mailbenutzer Anrufe weitergeleitet werden sollen
ms:assetid: 1f8e0a53-3d9d-4f8c-9be3-9f1e2a4347a3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335138(v=EXCHG.150)
ms:contentKeyID: 50554814
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Zulassen, dass Voice Mailbenutzer Anrufe weitergeleitet werden sollen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Das Feature für Mailboxansageregeln wurde erstmals in Exchange 2010 vorgestellt. Mit diesem Feature können für Voicemail aktivierte Benutzer steuern, wie eingehende Anrufe behandelt werden sollen. Mailboxansageregeln werden auf ähnliche Weise auf eingehende Anrufe angewendet wie Posteingangsregeln auf eingehende E-Mails.

Mailboxansageregeln werden für einen für Voicemail aktivierten Benutzer mit Outlook oder Outlook Web App erstellt und konfiguriert. Die Regeln werden zusammen mit anderen Spracheinstellungen im Postfach des Benutzers gespeichert. Für ein UM-aktiviertes Postfach können insgesamt neun Mailboxansageregeln eingerichtet werden. Diese Regeln gelten unabhängig von den Posteingangsregeln, die vom Benutzer eingerichtet werden, und schmälern nicht das Speicherkontingent für Posteingangsregeln.

Wenn ein Benutzer für Unified Messaging (UM) und Voicemail aktiviert ist, werden standardmäßig keine Mailboxansageregeln konfiguriert. Wird ein eingehender Anruf vom Voicemailsystem entgegengenommen, wird der Anrufer aufgefordert, eine Sprachnachricht zu hinterlassen. Aber auch wenn der Anrufer keine Aufforderung erhält, kann er eine Sprachnachricht für den Benutzer hinterlassen.

Wenn das Voicemailsystem nur die eingehenden Anrufe der Benutzer entgegennehmen soll und die Benutzer nur eine Sprachnachricht aufzeichnen möchten, müssen Sie keine Mailboxansageregeln erstellen. Wenn Sie jedoch Bedingungen oder Aktionen einrichten möchten, können Sie dazu den Abschnitt **Mailboxansageregeln** auf der Seite **Voicemail** in Outlook Web App verwenden. Verwenden Sie zum Erstellen, Bearbeiten und Löschen von Mailboxansageregeln den Abschnitt **Mailboxansageregeln**.

## Anatomie der Mailboxansageregeln

Eine Mailboxansageregel besteht aus zwei Teilen: Bedingungen und Aktionen. Sie können eine oder mehrere Bedingungen mit einer einzelnen Mailboxansageregel verknüpfen. Die Mailboxansageregel wird nur verarbeitet, wenn alle Bedingungen für die Regel erfüllt sind. Sie können auch eine oder mehrere Aktionen mit einer einzelnen Mailboxansageregel verknüpfen. Diese Aktionen bestimmen, welche Optionen dem Anrufer bei Verarbeiten der Mailboxansageregel angeboten werden.

Mailboxansageregeln unterstützen die folgenden Bedingungen:

  - Von wem der eingehende Anruf stammt

  - Die Tageszeit

  - Frei/Gebucht-Kalenderstatus

  - Ob automatische Antworten für E-Mail aktiviert sind

Die folgenden Aktionen werden unterstützt:

  - Mich anrufen

  - Anrufer an eine andere Person übergeben

  - Eine Sprachnachricht hinterlassen

Wenn Benutzer eine benutzerdefinierte Begrüßung für eine Mailboxansageregel aufzeichnen, müssen sie beim Konfigurieren der Mailboxansageregel die Menüoption in die benutzerdefinierte Begrüßung integrieren. Andernfalls generiert Unified Messaging keine Menüansage, um den Anrufer darüber zu informieren, welche Optionen er wählen kann. Nachdem die benutzerdefinierte Begrüßung wiedergegeben wurde, wartet der Server auf die Eingabe des Anrufers. Ist keine Menüoption in der Begrüßung enthalten, erfolgt keine Eingabe durch den Anrufer, und dieser wird vom Server gefragt, ob er noch in der Leitung ist.

## Bedingungen

Bedingungen sind Regeln, die auf Mailboxansageregeln angewendet werden können. Durch eine Kombination von Bedingungen können Sie mehrere Mailboxansageregeln erstellen, die bei Erfüllung der Bedingungen ausgelöst werden. Wenn Sie eine Standardregel erstellen möchten, die bei jedem Anruf angewendet wird, erstellen Sie eine Regel ohne jegliche Bedingungen.

Zum Einrichten von Mailboxansageregeln können drei Bedingungen verwendet werden:

  - Anrufer-ID

  - Tageszeit

  - Frei/Gebucht-Status

## Aktionen

Anhand von Aktionen wird definiert, was geschehen soll, wenn eine Bedingung erfüllt wird. Es gibt zwei Aktionsarten:

  - Suchanruf

  - Anrufweiterleitung

**Hinzufügen einer Aktion für "Mich suchen"**

Wenn ein Anrufer "Mich suchen" auswählt, versucht das Voicemailsystem, Sie unter bis zu zwei verschiedenen Telefonnummern zu erreichen, und anschließend wird der Anrufer mit Ihnen verbunden (sofern Sie unter einer der Telefonnummern erreichbar sind).

  - Sie können Text angeben, der dem Anrufer vorgelesen wird. Wenn Sie z. B. "In dringenden Fällen" eingeben, um Anrufer zu informieren, dass sie diese Aktion nur dann auswählen sollen, wenn Sie ein wirklich wichtiges Anliegen haben, lautet die Ansage des Voicemailsystems "Drücken Sie in dringenden Fällen die Taste 1."

  - Sie müssen die Aktion für "Mich suchen" mit der Nummer auf der Telefontastatur verknüpfen, die der Anrufer zur Auswahl dieser Aktion drückt. Im obigen Beispiel ist die Nummer, die der Anrufer drücken muss, um Sie unter der oder den angegebenen Telefonnummern zu erreichen, die Taste **1**.

  - Als Nächstes müssen Sie ein oder zwei Telefonnummern eingeben, die vom Voicemailsystem gewählt werden sollen. Wenn Sie zwei Telefonnummern angeben, wird die zweite Nummer gewählt, wenn Sie unter der ersten Telefonnummer nicht erreichbar sind. Jeder angegebenen Telefonnummer ist eine Dauer zugeordnet. Die Dauer ist der Zeitraum, in dem das Voicemailsystem die Telefonnummer anwählt, ehe es mit der nächsten Telefonnummer fortfährt. Alternativ kehrt das Voicemailsystem zum Optionsmenü zurück, wenn Sie nicht erreichbar sind.

  - Nachdem Sie diese Informationen eingegeben haben, klicken Sie auf **Übernehmen**, um die Einstellungen für "Mich suchen" zu speichern.

**Hinzufügen von Aktionen für die Anrufweiterleitung**

Durch Einrichten einer Aktion des Typs "Anrufweiterleitung" haben Anrufer die Möglichkeit, an die Telefonnummer einer anderen Person weitergeleitet zu werden. Wenn Sie einen eingehenden Anruf an eine andere Telefonnummer oder einen anderen Kontakt weiterleiten möchten, sind verschiedene Optionen verfügbar.

  - Sie können Text angeben, der dem Anrufer vorgelesen wird. Sie können z. B. "In wichtigen Fällen" eingeben, um den Anrufer zu informieren, dass er diese Option nur auswählen soll, wenn er ein wichtiges Anliegen hat, das er mit jemandem besprechen muss.

  - Sie müssen die Aktion **Anrufweiterleitung** der Nummer auf der Telefontastatur zuordnen, die der Anrufer zur Auswahl dieser Aktion drückt.

  - Wenn Sie die Anrufweiterleitung auswählen, müssen Sie eine Person oder Telefonnummer angeben, an die der Anrufer weitergeleitet wird. Sie können eine Telefonnummer oder einen Kontakt auswählen, die bzw. der angerufen werden soll, wenn der Anrufer die richtige Taste auf der Telefontastatur drückt. Wenn Sie einen Kontakt angeben, der sich im Unternehmensverzeichnis befindet, versucht das Voicemailsystem, den Anruf an die Durchwahl dieses Kontakts weiterzuleiten.

  - Neben einer Person oder Telefonnummer, an die der Anrufer weitergeleitet wird, müssen Sie auch die Nummer der Taste auf der Telefontastatur angeben, die der Anrufer zur Auswahl der Anrufweiterleitung drückt.

  - Wenn Sie diese Informationen eingegeben haben, klicken Sie auf **Übernehmen**, um die Einstellungen für die Anrufweiterleitung zu speichern.

## Auswählen einer Mailboxansageregel für jeden eingehenden Anruf

Nach dem Erstellen und Konfigurieren von Mailboxansageregeln geht Unified Messaging wie folgt vor:

1.  Bestimmen, ob der Benutzer Mailboxansageregeln erstellt hat. Ist dies nicht der Fall, bietet UM dem Anrufer die Option an, eine Sprachnachricht zu hinterlassen.

2.  Wurden eine oder mehrere Mailboxansageregeln konfiguriert, wertet UM jede dieser Regeln aus. Die erste Regel, deren Bedingungen erfüllt sind, wird verarbeitet.

3.  Findet UM nach der Auswertung aller Regeln keine Regel, deren Bedingungen alle erfüllt sind, fordert UM den Anrufer auf, eine Sprachnachricht zu hinterlassen.

## Wählregeln

Je nach Konfiguration einer Mailboxansageregel kann ein eingehender Anruf zu einer Anrufübergabe führen. In diesem Fall unterliegt die Zieltelefonnummer für die Übergabe den Wählregeln und -einschränkungen der UM-Postfachrichtlinie, der die angerufene Partei zugeordnet ist. Weitere Informationen zu Outdialing- und Wählregeln und -einschränkungen finden Sie unter [Autorisieren von Benutzern für Anrufe](allow-users-to-make-calls-exchange-2013-help.md).

## Aktivieren/Deaktivieren von Mailboxansageregeln

Standardmäßig werden Mailboxansageregeln automatisch für UM-aktivierte Benutzer aktiviert. Sie können Mailboxansageregeln jedoch für Benutzer deaktivieren, indem Sie das Feature in einer UM-Postfachrichtlinie oder im Postfach des Benutzers deaktivieren. Ausführliche Informationen zum Aktivieren oder Deaktivieren von Mailboxansageregeln finden Sie in folgenden Themen:

  - [Ermöglichen Sie oder verhindern Sie, dass Benutzer in der gleichen UM-Postfachrichtlinie erstellen Aufruf von mailboxansageregeln](allow-or-prevent-users-in-the-same-um-mailbox-policy-from-creating-call-answering-rules-exchange-2013-help.md)

  - [Ermöglichen Sie oder verhindern Sie, dass einen Benutzer erstellen Aufruf von mailboxansageregeln](allow-or-prevent-a-user-from-creating-call-answering-rules-exchange-2013-help.md)

