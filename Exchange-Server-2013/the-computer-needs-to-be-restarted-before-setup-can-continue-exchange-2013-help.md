---
title: 'Computer muss neu gestartet werden, bevor Setup fortgesetzt wird'
TOCTitle: Computer muss neu gestartet werden, bevor das Setup fortgesetzt werden kann
ms:assetid: d5c73280-4e54-473a-b328-9673af11e2c0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.rebootpending(v=EXCHG.150)
ms:contentKeyID: 50476808
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Computer muss neu gestartet werden, bevor das Setup fortgesetzt werden kann

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das Setup von Microsoft Exchange Server 2013 kann nicht fortgesetzt werden, da festgestellt wurde, dass der lokale Computer neu gestartet werden muss, damit die Installation anderer Programme oder von Windows-Updates abgeschlossen werden kann.

## Wie kommt das?

Wenn Programme und Windows-Updates installiert werden, nehmen sie Änderungen an Dateien vor, die auf Ihrem Computer gespeichert sind. Während der Installation muss ein Programm oder Windows-Update mitunter eine Änderung an einer Datei vornehmen, die verwendet wird. In diesem Fall müssen Sie den Computer neu starten, bevor andere Programme, wie z. B. Exchange 2013, installiert werden können. Das Setup von Exchange erfordert, dass alle anderen Installationen abgeschlossen sind, damit es überprüfen kann, ob alle Komponenten, die für einen ordnungsgemäßen Betrieb benötigt werden, installiert wurden.

Mitunter wird die Installation eines vorherigen Programms oder Windows-Updates möglicherweise nicht erfolgreich abgeschlossen. Wenn dies geschieht, können Änderungen zurückbleiben, die Windows und andere Programme zu einem Neustart veranlassen. Leider kann die Installation von Windows-Updates und anderen Programmen blockiert werden, da bei einer misslungenen Installation diese Änderungen nie korrigiert werden. Wenn dies geschieht, wird dieser Fehler weiter jedes Mal angezeigt, wenn Sie das Exchange-Setup ausführen.

## Problemlösung

In den meisten Fällen müssen Sie den Computer neu starten, um diesen Fehler zu beseitigen. Es kommt jedoch vor, dass dieser Fehler erneut auftritt, obwohl Sie den Computer bereits neu gestartet haben. Dies kann passieren, wenn die Installation eines Programms oder Windows-Updates zusätzliche Änderungen vornehmen muss, und diese Änderungen außerdem erfordern, dass der Computer neu gestartet werden muss. Wenn dieser Fehler angezeigt wird, nachdem Sie den Computer neu gestartet haben, starten Sie ihn erneut.

Wenn Sie den Computer mehr als zwei- oder dreimal neu gestartet haben und diese Fehlermeldung immer noch angezeigt wird, versuchen Sie, Programme oder Windows-Updates neu zu installieren, die Sie vor Kurzem installiert haben. Dadurch kann eine fehlerhafte Installation ggf. erfolgreich abgeschlossen werden.

Wenn Sie nach dem Neustart des Computers und der Neuinstallation alle zuletzt installierten Programme oder Windows-Updates *weiter* diese Fehlermeldung erhalten, empfehlen wir, dass Sie sich an den Microsoft-Support wenden. Unsere Mitarbeiter helfen Ihnen beim Feststellen, warum Windows und andere Programme meinen, dass der Computer neu gestartet werden muss. Besuchen Sie [Support für Microsoft Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=525940), um den Microsoft-Support zu kontaktieren.


> [!WARNING]
> Obwohl es verlockend sein kann, raten wir dringend davon ab, dieses Problem zu umgehen, indem Sie Schlüssel oder Werte in der Windows-Registrierung manuell löschen oder ändern. Obwohl dieses Problem dadurch vielleicht behoben wird, ergeben sich möglicherweise später Probleme. Dies gilt insbesondere, wenn die misslungene Installation ein Windows-Update war.


