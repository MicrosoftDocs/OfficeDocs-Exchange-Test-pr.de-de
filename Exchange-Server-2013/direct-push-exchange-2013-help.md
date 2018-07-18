---
title: 'Direct Push: Exchange 2013 Help'
TOCTitle: Direct Push
ms:assetid: 373c1629-3d4b-4828-b014-9e103de4ef25
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997252(v=EXCHG.150)
ms:contentKeyID: 50475472
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Direct Push

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-07-11_

Direct Push ist eine in Microsoft Exchange Server 2013 integrierte Funktion. Direct Push hält ein mobiles Gerät über eine Mobilfunk- oder Drahtlosnetzwerkverbindung auf dem neusten Stand. Über diese Funktion wird das mobile Gerät benachrichtigt, wenn neue Inhalte zur Synchronisierung bereitstehen.

**Inhalt**

Übersicht

Direct Push-Topologie

Konfigurieren von Direct Push für das Arbeiten hinter einer Firewall

## Übersicht

Damit Direct Push funktionieren kann, muss das mobile Gerät Direct Push unterstützen. Zu diesen Geräten gehören die folgenden:

  - Alle Versionen von Windows Phone

  - Mobiltelefone, die von MicrosoftExchange ActiveSync-Lizenznehmern hergestellt werden und speziell für Direct Push konzipiert wurden

Direct Push ist in Exchange 2013 standardmäßig aktiviert. Mobile Geräte, die Direct Push unterstützen, senden eine langlebige HTTPS-Anforderung an den Microsoft Exchange-Server. Der Exchange-Server überwacht die Aktivität für das Postfach des Benutzers und sendet eine Antwort an das mobile Gerät, wenn Änderungen vorliegen, z. B. neue oder geänderte E-Mail-Nachrichten, Kalender-, Kontakt- oder Aufgabenelemente. Wenn Änderungen während der Lebensdauer der HTTPS-Anforderung auftreten, gibt der Servercomputer mit Exchange eine Antwort an das Gerät aus, die besagt, dass Änderungen aufgetreten sind und das Gerät die Synchronisierung mit dem Servercomputer mit Exchange einleiten sollte. Das Gerät gibt diese Anforderung dann an den Server aus. Nachdem der Synchronisierungsvorgang abgeschlossen wurde, wird eine neue lange bestehende HTTPS-Anforderung generiert, um das Verfahren zu wiederholen. Auf diese Weise wird garantiert, dass E-Mail-, Kalender, Kontakt- und Aufgabenelemente schnell an das mobile Gerät übermittelt werden und das Gerät immer mit dem Exchange-Server synchronisiert ist.

## Direct Push-Topologie

Direct Push funktioniert folgendermaßen:

1.  Ein mobiles Gerät, das für die Synchronisierung mit einem Exchange 2013-Server konfiguriert ist, sendet eine HTTPS-Anforderung an den Server. Diese Anforderung wird als PING-Befehl bezeichnet. Die Anforderung informiert den Server, dass das Gerät benachrichtigt werden soll, wenn sich in den nächsten 15 Minuten Elemente in einem beliebigen Ordner ändern, der für die Synchronisierung konfiguriert ist. Andernfalls sollte der Server die Nachricht "HTTP 200 OK" zurückgeben. Das mobile Gerät befindet sich nun im Standbymodus. Die Zeitspanne von 15 Minuten wird als *Taktintervall* bezeichnet.

2.  Wenn sich innerhalb der 15 Minuten keine Elemente ändern, gibt der Server die Antwort "HTTP 200 OK" zurück. Das mobile Gerät empfängt diese Antwort, nimmt seine Aktivität wieder auf (dies wird als *Aktivierung* bezeichnet) und sendet die Anforderung erneut. Auf diese Weise wird der Vorgang erneut gestartet.

3.  Wenn sich Elemente ändern oder innerhalb des Taktintervalls von 15 Minuten neue Elemente empfangen werden, sendet der Server eine Antwort, die das mobile Gerät darüber informiert, dass ein neues oder geändertes Element vorhanden ist. Außerdem wird der Name des Ordners übermittelt, in dem das neue oder geänderte Element gespeichert ist. Nachdem das mobile Gerät diese Antwort empfangen hat, sendet es eine Synchronisierungsanforderung für den Ordner, der die neuen oder geänderten Elemente enthält. Nachdem der Synchronisierungsvorgang abgeschlossen ist, sendet das mobile Gerät eine neue PING-Anforderung, und das Verfahren beginnt von vorn.

Direct Push ist von Netzwerkbedingungen abhängig, die eine lange bestehende HTTPS-Anforderung unterstützen. Wenn das Trägernetzwerk für das mobile Gerät oder die Firewall langlebige HTTPS-Anforderungen nicht unterstützen, wird die HTTPS-Anforderung beendet. Die folgenden Schritte beschreiben, wie Direct Push funktioniert, wenn das Trägernetzwerk eines mobilen Geräts einen Timeoutwert von 13 Minuten besitzt.

1.  Ein mobiles Gerät gibt eine HTTPS-Anforderung an den Server aus. Die Anforderung informiert den Server, dass das Gerät benachrichtigt werden soll, wenn sich in den nächsten 15 Minuten Elemente in einem beliebigen Ordner ändern, der für die Synchronisierung konfiguriert ist. Andernfalls sollte der Server die Nachricht "HTTP 200 OK" zurückgeben. Das mobile Gerät befindet sich nun im Standbymodus.

2.  Wenn der Server nach 15 Minuten nicht antwortet, wird das mobile Gerät aktiviert; es erkennt, dass die Verbindung mit dem Server durch einen Timeout des Netzwerks unterbrochen wurde. Das Gerät gibt die HTTPS-Anforderung erneut aus, verwendet nun jedoch ein Taktintervall von 8 Minuten.

3.  Nach 8 Minuten sendet der Server die Nachricht "HTTP 200 OK". Das Gerät versucht anschließend, eine längere Verbindung herzustellen, indem es eine neue HTTPS-Anforderung an den Server mit einem Taktintervall von 12 Minuten ausgibt.

4.  Nach 4 Minuten wird eine neue E-Mail-Nachricht empfangen, und der Server antwortet durch das Senden einer HTTPS-Anforderung, die das Gerät zur Synchronisierung auffordert. Das Gerät führt die Synchronisierung durch und gibt erneut eine HTTPS-Anforderung mit einem Taktintervall von 12 Minuten aus.

5.  Nach 12 Minuten antwortet der Server durch Senden einer Nachricht "HTTP 200 OK", wenn keine neuen oder geänderten Elemente vorhanden sind. Das Gerät wird aktiviert und erkennt, dass die Netzwerkbedingungen ein Taktintervall von 12 Minuten unterstützen. Das Gerät versucht anschließend, eine längere Verbindung herzustellen, indem es erneut eine HTTPS-Anforderung mit einem Taktintervall von 16 Minuten ausgibt.

6.  Nach 16 Minuten wird keine Antwort vom Server empfangen. Das Gerät wird aktiviert und erkennt, dass die Netzwerkbedingungen ein Taktintervall von 16 Minuten nicht unterstützen. Da dieser Fehler unmittelbar nach dem Versuch des Geräts aufgetreten ist, das Taktintervall zu vergrößern, folgert das Gerät, dass das Taktintervall seinem maximalen Grenzwert erreicht hat. Das Gerät gibt dann eine HTTPS-Anforderung aus, die ein Taktintervall von 12 Minuten besitzt, da dieser Wert das letzte erfolgreiche Taktintervall war.

Das mobile Gerät versucht, das längstmögliche Taktintervall zu verwenden, das das Netzwerk unterstützt. Auf diese Weise wird die Lebensdauer des Geräteakkus verlängert und die Datenmenge verringert, die über das Netzwerk übertragen wird. Mobile Trägernetzwerke können einen maximalen, minimalen und anfänglichen Taktwert in den Registrierungseinstellungen für das mobile Gerät angeben.

## Konfigurieren von Direct Push für das Arbeiten hinter einer Firewall

Damit Direct Push hinter einer Firewall funktioniert, muss der TCP-Port 443 geöffnet werden. Dieser Port 443 ist für SSL (Secure Sockets Layer) erforderlich und muss zwischen dem Internet und dem Clientzugriffsserver geöffnet werden.

Sie sollten nicht nur die Ports auf der Firewall öffnen, sondern für optimale Direct Push-Leistung auch den Timeoutwert für die Firewall vom Standardwert von 15 Minuten auf 30 Minuten erhöhen. Die maximale Länge der HTTPS-Anforderung wird durch die folgenden Einstellungen bestimmt:

  - Den maximalen Timeoutwert, der für die Firewalls festgelegt wird, die den Datenverkehr aus dem Internet zum Clientzugriffsserver steuern

  - Den Timeoutwerten für die Firewall, die vom Mobilfunkanbieter festgelegt werden

