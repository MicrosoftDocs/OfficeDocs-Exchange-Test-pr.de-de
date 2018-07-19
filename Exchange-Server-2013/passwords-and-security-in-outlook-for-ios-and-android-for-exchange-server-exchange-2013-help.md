---
title: 'Passwords and Security in Outlook for iOS and Android for Exchange Server: Exchange 2013 Help'
TOCTitle: Passwords and Security in Outlook for iOS and Android for Exchange Server
ms:assetid: e5565beb-7ef3-47c4-8daf-6d8f1d22dceb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt465750(v=EXCHG.150)
ms:contentKeyID: 70086936
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Passwords and Security in Outlook for iOS and Android for Exchange Server

 

_**Gilt für:** Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-01_

**Zusammenfassung:**  In diesem Artikel wird die Funktionsweise von Kennwörtern und Sicherheitseinstellungen in Outlook für iOS und Android in Exchange Server-Umgebungen erläutert.

Bei der ersten Ausführung der Outlook-App für iOS und Android in einer lokalen Exchange-Umgebung generiert Outlook einen zufälligen AES-128-Schlüssel. Dieser Schlüssel wird als *Geräteschlüssel* bezeichnet und ausschließlich auf dem Gerät des Benutzers gespeichert.

## Erstellen eines Kontos und Absichern von Kennwörtern

Meldet sich ein Benutzer bei Exchange an, sendet das Gerät des Benutzers den Benutzernamen, das Kennwort und einen eindeutigen AES-128-Geräteschlüssel über eine TLS-Verbindung an den Outlook-Dienst. Hier wird der Geräteschlüssel im Laufzeitspeicher abgelegt. Sobald der Outlook-Dienst das Kennwort beim Exchange-Server verifiziert hat, verschlüsselt er es mithilfe des Geräteschlüssels. Anschließend wird das verschlüsselte Kennwort im Dienst gespeichert. Der Geräteschlüssel wird endgültig aus dem Laufzeitspeicher gelöscht und zu keinem Zeitpunkt im Outlook-Dienst gespeichert. (Der Schlüssel wird ausschließlich auf dem Gerät des Benutzers gespeichert.)

Versucht der Benutzer nun, Postfachdaten von Exchange abzurufen, übergibt das Gerät den Geräteschlüssel erneut über eine TLS-gesicherte Verbindung an den Outlook-Dienst. Dieser entschlüsselt mithilfe des Schlüssels das Kennwort im Laufzeitspeicher. Das entschlüsselte Kennwort wird zu keinem Zeitpunkt im Dienst gespeichert oder auf ein lokales Speichermedium geschrieben, und der Geräteschlüssel wird erneut endgültig aus dem Laufzeitspeicher gelöscht.

Sobald der Outlook-Dienst das Kennwort zur Laufzeit entschlüsselt hat, kann er eine Verbindung zum Exchange-Server herstellen und E-Mails, Kalender sowie andere Postfachdaten synchronisieren. Solange der Benutzer Outlook regelmäßig öffnet und benutzt, speichert der Outlook-Dienst eine Kopie des entschlüsselten Benutzerkennworts im Laufzeitspeicher, um die Verbindung zum Exchange-Server aufrechtzuerhalten.

## Kontoinaktivität und Löschen von Kennwörtern aus dem Laufzeitspeicher

Nach drei Tagen Inaktivität löscht der Outlook-Dienst das entschlüsselte Kennwort aus dem Laufzeitspeicher. Ist das geschehen, kann der Outlook-Dienst nicht mehr auf das Postfach des Benutzers zugreifen. Das verschlüsselte Kennwort bleibt im Outlook-Dienst gespeichert, kann aber ohne den Geräteschlüssel nicht entschlüsselt werden. Dieser wiederum kann nur vom Gerät des Benutzers bereitgestellt werden.

Es gibt drei Gründe, aus denen ein Benutzerkonto inaktiv werden kann:

  - Der Benutzer deinstalliert Outlook für iOS und Android.

  - Der Benutzer deaktiviert die Hintergrundaktualisierung für Apps in den Einstellungen und erzwingt anschließend das Beenden von Outlook.

  - Das Gerät des Benutzers hat keine Internetverbindung, sodass Outlook sich nicht mit Exchange synchronisieren kann.


> [!NOTE]
> Outlook wird nicht als inaktiv eingestuft, nur weil der Benutzer die App über einen längeren Zeitraum nicht öffnet, beispielsweise während des Wochenendes oder im Urlaub. Solange die Hintergrundaktualisierung für Apps aktiviert ist (Standardeinstellung für Outlook&nbsp;für&nbsp;iOS&nbsp;und&nbsp;Android), zählen Funktionen wie Pushbenachrichtigungen und die Hintergrundsynchronisierung von E-Mails als Aktivität.



**Löschen des verschlüsselten Kennworts und des Nachrichtencaches von Speichermedien**

Der Outlook-Dienst löscht im wöchentlichen Rhythmus inaktive Konten. Sobald ein Benutzerkonto inaktiv wird, löscht der Outlook-Dienst sowohl das verschlüsselte Kennwort als auch alle zwischengespeicherten Postfachinhalte des Benutzers aus dem Dienst.

**Kombination aus Sicherheitsfunktionen auf Geräte- und Dienstseite**

Der eindeutige Geräteschlüssel des Benutzers wird zu keinem Zeitpunkt im Outlook-Dienst gespeichert. Gleichzeitig gilt, dass das Exchange-Kennwort des Benutzers zu keinem Zeitpunkt auf seinem Gerät gespeichert wird. Will ein Angreifer Zugriff auf das Benutzerkennwort erhalten, müsste er sich dank dieser Architektur nicht nur unautorisierten Zugriff auf den Outlook-Dienst verschaffen, sondern auch das Gerät des Benutzers in seinen Besitz bringen.

Wenn Sie zusätzlich PIN-Richtlinien und Verschlüsselung auf den Geräten in Ihrer Organisation erzwingen, müsste der Angreifer außerdem noch die Geräteverschlüsselung knacken, um sich zunächst den Geräteschlüssel zu verschaffen. All das müsste passieren, bevor der Benutzer den Diebstahl oder die Kompromittierung des Geräts bemerkt und eine Remotezurücksetzung anfordert.

## Häufig gestellte Fragen zur Kennwortsicherheit

In diesem Abschnitt finden Sie häufig gestellte Fragen zur Sicherheitsarchitektur sowie zu den Sicherheitseinstellungen von Outlook für iOS und Android.

## Werden die Benutzeranmeldeinformationen im Outlook-Dienst gespeichert, wenn ich den Outlook-Zugriff auf meinen Exchange-Server blockiere?

Wenn Sie den Zugriff auf Ihre lokalen Exchange-Server für Outlook für iOS und Android blockiert haben, wird bereits der erste Verbindungsversuch von Exchange abgelehnt. Die Benutzeranmeldeinformationen werden nicht vom Outlook-Dienst gespeichert. Die während des fehlgeschlagenen Verbindungsversuchs übermittelten Anmeldeinformationen werden sofort aus dem Laufzeitspeicher gelöscht.

## Wie werden der eindeutige Geräteschlüssel und das Benutzerkennwort während der Übermittlung an den Outlook-Dienst verschlüsselt?

Die gesamte Kommunikation zwischen der Outlook-App und dem Outlook-Dienst läuft über eine verschlüsselte TLS-Verbindung. Outlook für iOS und Android kann sich ausschließlich mit dem Outlook-Dienst verbinden.

## Wie kann ich die Anmeldeinformationen und Postfachdaten eines Benutzers aus dem Outlook-Dienst entfernen?

Es gibt drei Möglichkeiten, Informationen aus dem Outlook-Dienst zu entfernen:

  - Option 1: Sie stoßen eine Remotezurücksetzung für jeden Benutzer an, der über die App eine Verbindung zu Exchange hergestellt hat.

  - Option 2: Sie weisen alle Benutzer an, Outlook für iOS und Android zu löschen. Anschließend werden alle Daten innerhalb von etwa 3 bis 7 Tagen aus dem Outlook-Dienst entfernt.

  - Option 3: Sie weisen die Benutzer an, ihr Konto aus der Outlook-App zu entfernen und anschließend die App von ihrem Gerät zu löschen. Hierzu müssen die Benutzer in der App **Einstellungen** aufrufen und auf **Kontoeinstellungen** tippen. Dann müssen sie auf **Konto auswählen** und anschließend auf **Konto löschen** tippen.

## Die App ist geschlossen oder wurde deinstalliert, versucht aber immer noch, sich mit meinem Exchange-Server zu verbinden. Wie kann das sein?

Der Outlook-Dienst entschlüsselt die Benutzerkennwörter im Laufzeitspeicher und nutzt anschließend die entschlüsselten Kennwörter, um eine Verbindung mit Exchange herzustellen. Da der Outlook-Dienst sich im Namen des Geräts mit Exchange verbindet, um Postfachdaten abzurufen und zwischenzuspeichern, kann es eine kurze Weile dauern, bis der Dienst bemerkt, dass Outlook keine Daten mehr anfordert.

Deinstalliert der Benutzer die App, ohne zuvor die Option **Konto löschen** zu verwenden, bleibt der Outlook-Dienst mit dem Exchange-Server verbunden, bis das Konto inaktiv wird (siehe Abschnitt „Löschen des verschlüsselten Kennworts und des Nachrichtencaches von Speichermedien\&quot; oben). Möchten Sie diese Aktivität stoppen, können Sie einfach Option 1 oder Option 3 aus der Antwort weiter oben durchführen oder die App wie im Artikel [Blockieren von Outlook für iOS und Android](https://technet.microsoft.com/de-de/library/mt759239\(v=exchg.150\)) beschrieben blockieren.

## Ist ein Benutzerkennwort in Outlook für iOS und Android weniger sicher als bei Verwendung anderer Exchange ActiveSync-Clients?

Nein. EAS-Clients speichern die Benutzeranmeldeinformationen generell lokal auf dem Gerät des Benutzers. Wird ein Gerät gestohlen oder kompromittiert, könnte ein Angreifer also Zugang zum Kennwort des Benutzers erhalten. Dank der Sicherheitsarchitektur von Outlook für iOS und Android müsste sich der Angreifer dafür jedoch unautorisierten Zugriff auf den Outlook-Clouddienst **und** physischen Zugang zum Gerät des Benutzers verschaffen.

## Was passiert, wenn ein Benutzer versucht, Outlook für iOS und Android zu verwenden, nachdem seine Daten aus dem Outlook-Dienst gelöscht wurden?

Wird ein Benutzerkonto inaktiv (z. B. durch die Deaktivierung der Hintergrundaktualisierung für Apps auf dem Gerät oder einen länger andauernden Wegfall der Internetverbindung auf dem Gerät), verbindet sich die Outlook-App bei ihrem nächsten Start mit dem Outlook-Dienst. Damit wird der Prozess zur Kennwortverschlüsselung und E-Mail-Zwischenspeicherung neu angestoßen. Dieser Vorgang ist für den Benutzer transparent.

## Wie werden die vorübergehend im Outlook-Dienst zwischengespeicherten Postfachdaten geschützt?

Sie erhalten Informationen über unsere Daten wie derzeit an der [Azure Trust Center](https://azure.microsoft.com/support/trust-center/)geschützt ist. Wie bereits erwähnt, sind wir von Azure in Office 365 verschoben. Die Sicherheit dieser Dienste wird an [Die Office 365-Trust Center](https://go.microsoft.com/fwlink/p/?linkid=525776)behandelt.

