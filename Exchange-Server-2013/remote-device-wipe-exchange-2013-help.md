---
title: 'Remotegerätezurücksetzung: Exchange 2013 Help'
TOCTitle: Remotegerätezurücksetzung
ms:assetid: cd615210-cd8a-48de-b3e3-8f9ec39ca380
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124591(v=EXCHG.150)
ms:contentKeyID: 50476743
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Remotegerätezurücksetzung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-19_

Mobiltelefone, Tablets und andere Geräte können vertrauliche Geschäftsdaten speichern und bieten den Zugriff auf viele Unternehmensressourcen. Wenn ein mobiles Gerät verloren geht oder gestohlen wird, sind die Daten gefährdet. Sie können dem mobilen Gerät mithilfe der Microsoft Exchange-Postfachrichtlinien für mobile Geräte eine Kennwortanforderung hinzufügen. Dann muss der Benutzer ein Kennwort eingeben, um auf das mobile Gerät zugreifen zu können. Es wird empfohlen, dass Sie zusätzlich zum Anfordern eines Gerätekennworts Ihre mobilen Geräte auch so konfigurieren, dass diese nach einer Phase der Inaktivität automatisch zur Eingabe eines Kennworts auffordern. Die Kombination aus Gerätekennwort und Sperrung bei Inaktivität bietet eine erhöhte Sicherheit für die Geschäftsdaten.

Zusätzlich zu diesen Features bietet Exchange Server 2013 ein Feature für die Remotegerätzurücksetzung. Sie können einen Befehl für die Remotegerätzurücksetzung über die Exchange-Verwaltungsshell oder die Exchange-Verwaltungskonsole (Exchange Administration Center, EAC) ausführen. Benutzer können ihre eigenen Befehle für die Remotegerätzurücksetzung über die MicrosoftOutlook Web App-Benutzeroberfläche ausführen.

Die Remotegerätzurücksetzung umfasst auch eine Bestätigungsfunktion, die einen Zeitstempel in die Synchronisierungsstatusdaten des Benutzerpostfachs schreibt. Dieser Zeitstempel wird in Outlook Web App und im Dialogfeld mit den Eigenschaften des Mobiltelefons des Benutzers in der Exchange-Verwaltungskonsole angezeigt.


> [!IMPORTANT]
> Mit der Remotegerätzurücksetzung kann ein Mobiltelefon auf den werkseitig eingestellten Standardzustand zurückgesetzt werden. Auch wenn das Protokoll für die Remotegerätzurücksetzung, so wie sie in Exchange 2013 implementiert ist, nur das Löschen aller persönlichen Geschäftsdaten erfordert, interpretieren alle Hersteller aktueller mobiler Geräte den Befehl so, als ob er alle Daten vom Telefon entfernen würde. Viele Betriebssysteme von mobilen Geräten entfernen auch alle Daten von einer Speicherkarte, die in das mobile Gerät eingesetzt wurde. Wenn Sie eine Remotegerätzurücksetzung für ein in Ihrem Besitz befindliches Mobiltelefon durchführen und die Daten auf der Speicherkarte erhalten bleiben sollen, sollten Sie die Speicherkarte entfernen, bevor die Remotegerätzurücksetzung gestartet wird.




> [!WARNING]
> Nach einer Remotegerätzurücksetzung ist es äußerst schwierig, Daten wiederherzustellen. Es gibt jedoch keinen Datenentfernungsvorgang, der ein mobiles Gerät so vollständig von Daten befreit, dass es wieder wie neu ist. Die Wiederherstellung der Daten eines mobilen Geräts kann mithilfe von Spezialtools auch weiterhin möglich sein.



## Remotegerätzurücksetzung oder lokale Gerätzurücksetzung

Eine lokale Gerätzurücksetzung tritt ein, wenn ein mobiles Gerät seine Daten selbst, ohne Aufforderung vom Server löscht. Wenn Ihre Organisation Postfachrichtlinien für mobile Geräte implementiert hat, die eine maximale Anzahl von nicht erfolgreichen Versuchen für die Kennworteingabe festlegen, und dieser Höchstwert überschritten wird, dann führt das mobile Gerät eine lokale Gerätzurücksetzung durch. Das Ergebnis einer lokalen Gerätzurücksetzung entspricht dem einer Remotegerätzurücksetzung. Der werkseitig eingestellte Standardzustand des Geräts wird wiederhergestellt. Wenn ein mobiles Gerät eine lokale Gerätzurücksetzung durchführt, wird keine Bestätigung an den Exchange-Server gesendet.

