---
title: 'Wiedergabe über Telefon: Exchange 2013 Help'
TOCTitle: Wiedergabe über Telefon
ms:assetid: 511e4950-340a-48cc-a020-35d11e76b993
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn205136(v=EXCHG.150)
ms:contentKeyID: 54651505
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiedergabe über Telefon

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-25_

Nachdem eine Voicemailnachricht eingegangen ist, können Benutzer die Voicemailnachricht über die Lautsprecher oder den Kopfhörer Ihres Computers wiedergeben oder die Funktion zur Wiedergabe über Telefon verwenden. Die Funktion zur Wiedergabe über Telefon ist in Microsoft Outlook und Outlook Web App enthalten, und Einstellungen für Wiedergabe über Telefon sind im Abschnitte **Wiedergabe über Telefon** unter den Optionen für **Voicemail** verfügbar. In diesem Thema wird erläutert, wie ein UM-aktivierter Benutzer die Funktion zur Wiedergabe über Telefon verwenden kann.

## Was ist Wiedergabe über Telefon?

Die Funktion zur Wiedergabe über Telefon ermöglicht UM-aktivierten Benutzern die Wiedergabe der Sprachnachricht über ein Telefon. Wenn ein UM-aktivierter Benutzer in einem Großraumbüro arbeitet, einen öffentlichen Computer bzw. einen Computer verwendet, der nicht für Multimedia aktiviert ist, oder eine vertrauliche Sprachnachricht wiedergibt, möchte er die Wiedergabe der Sprachnachricht möglicherweise nicht über die Computerlautsprecher vornehmen. Alternativ kann er die Sprachnachricht mithilfe eines privaten, geschäftlichen oder Mobiltelefons wiedergeben. Wechseln Sie zur Überprüfung der Einstellungen für die Wiedergabe über Telefon in Outlook zu **Datei** \> **Info** \> **Voicemail verwalten**. Mit einem Klick auf die Schaltfläche **Voicemail verwalten** werden Sie automatisch bei Outlook Web App angemeldet, oder Sie können sich mit einem Webbrowser bei Outlook Web App anmelden. Wechseln Sie in Outlook Web App zum Abschnitt **Optionen** \> **Telefon** \> **Voicemail** \> **Wiedergabe über Telefon** auf der Seite **Voicemail**.

Wenn der Benutzer im Voicemailformular auf die Symbolleistenoption "Wiedergabe über Telefon" klickt, wird das Dialogfeld **Wiedergabe über Telefon** angezeigt. Das Dialogfeld **Wiedergabe über Telefon** stellt die Steuerelemente zum Auswählen oder Eingeben der Rufnummer, die für die Wiedergabe einer Sprachnachricht verwendet werden soll, ebenso wie die Steuerelemente zum Starten und Beenden des Anrufs sowie die Statusmeldung zum Überwachen des Anrufs zur Verfügung. Ist der Benutzer mit einem SIP-URI-Wählplan verknüpft, wird die SIP-Adresse im Feld **Wählen** angezeigt. Ist der Benutzer mit einem E.164-Wählplan verknüpft, erscheint die vollständige E.164-Nummer im Feld **Wählen**.


> [!NOTE]
> Es kann jeweils nur eine Sprachnachricht wiedergegeben werden. Wenn der Benutzer versucht, einen zweiten Anruf über Telefon wiederzugeben, während ein vorheriger Anruf noch verarbeitet wird, wird eine Fehlermeldung angezeigt.



## Liste der zuletzt verwendeten Rufnummern

Benutzer können eine Liste der Rufnummern im Feld **Wählen** anzeigen, die sie zuletzt verwendet haben. Die im Abschnitt **Wiedergabe über Telefon** angegebene Rufnummer wird immer als erster Eintrag angezeigt und für den Benutzer automatisch als primäre Rufnummer ausgewählt. Benutzer können das Dropdownmenü zum Auswählen anderer Rufnummern verwenden, die anstelle der als primäre Rufnummer konfigurierten Rufnummer verwendet werden sollen.


> [!NOTE]
> Wenn es Benutzern, die das Feature "Wiedergabe über Telefon" verwenden, möglich sein soll, eine externe Rufnummer ohne einen Zugangscode für die Amtsleitung wählen zu können (z. B. 0425-555-1234 anstelle von 0-0425-555-1234) konfigurieren Sie nationale/regionale Wählregeln für einen UM-Wählplan, die die folgende Zeile enthalten: group1, 9xxxxxxxxxx, 91xxxxxxxxxx. Nachdem Sie die nationalen/regionalen Wählregeln konfiguriert haben, fügen Sie diese Liste der UM-Postfachrichtlinie hinzu.



## Schaltflächen für "Wiedergabe über Telefon"

Das Dialogfeld **Wiedergabe über Telefon** stellt Benutzern die Optionen **Wählen** und **Auflegen** zur Verfügung. Beim erstmaligen Öffnen des Dialogfelds **Wiedergabe über Telefon** ist die Schaltfläche **Wählen** aktiviert, und die Schaltfläche **Auflegen** ist deaktiviert. Nachdem der Anruf eingeleitet wurde, bleibt die Schaltfläche **Wählen** deaktiviert, bis der Anruf beendet wurde. Der Anruf kann durch Klicken auf die Schaltfläche **Auflegen** oder durch physisches Auflegen des Telefons beendet werden. Wenn Sie das Dialogfeld **Wiedergabe über Telefon** mithilfe der Schaltfläche **Schließen** schließen, wird der ggf. zurzeit stattfindende Anruf beendet. Die Option **Wiedergabe über Telefon** sowie weitere Optionen sind auch in der **Lesebereich**-Vorschau in Outlook verfügbar. Wenn Sie die Voicemailnachricht in einem eigenen Fenster aufrufen, ist die Schaltfläche **Wiedergabe über Telefon** auf der Symbolleiste vorhanden.

## Betreff, Gesendet und Status

Der untere Abschnitt des Dialogfelds **Wiedergabe über Telefon** zeigt den Betreff der Sprachnachricht, Datum und Uhrzeit der Übermittlung sowie eine Nachricht an, die den aktuellen Status des Anrufs angibt. Fehler, die sich auf den Vorgang der Wiedergabe über Telefon beziehen, werden dem Benutzer ggf. in diesem Abschnitt des Dialogfelds **Wiedergabe über Telefon** angezeigt.

## Rufnummerüberprüfung

Bei der Wiedergabe über Telefon wird nur eine einfache Überprüfung der Eingabe im Dialogfeld **Wiedergabe über Telefon** vorgenommen. "Wiedergabe über Telefon" überprüft keine Rufnummern. Ist eine Rufnummer nicht gültig, gibt der Microsoft Exchange Unified Messaging-Dienst einen aussagekräftigen Fehlercode an den Benutzer zurück.

