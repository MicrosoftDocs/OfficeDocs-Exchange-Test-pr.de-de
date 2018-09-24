---
title: 'Betriebssystem im Debugmodus_OSCheckedBuild: Exchange 2013-Hilfe'
TOCTitle: Das Betriebssystem befindet sich im Debugmodus_OSCheckedBuild
ms:assetid: 93a1380f-1388-494d-8f78-92dfefd069bd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.oscheckedbuild(v=EXCHG.150)
ms:contentKeyID: 50476206
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Das Betriebssystem befindet sich im Debugmodus\_OSCheckedBuild

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-15_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server Analyzer fragt die Microsoft WMI-Klasse (Windows® Management Instrumentation – Windows®-Verwaltungsinstrumentation) **Win32\_OperatingSystem** ab, um zu bestimmen, ob für die Eigenschaft **Debug** ein Wert festgelegt wurde. Falls der Wert für diesen Schlüssel auf einem Exchange Server-Computer auf **True** festgelegt wurde, wird ein Fehler angezeigt.

Der Windows-Debug-Modus wird durch Hizufügen des Parameters **/debug** in der Datei „Boot.ini“ aktiviert oder deaktiviert. Wenn in der Datei „Boot.ini“ eines Windows Server-Computers **/debug** angegeben ist, wird der Kernel-Debugger während des Starts geladen und permanent im Speicher behalten. Dadurch können die Mitarbeitern des technischen Supports von Microsoft sich in das System einwählen, in dem gerade der Debug-Prozess ausgeführt wird, und den Debugger abbrechen. Dies ist selbst dann möglich, wenn das System nicht über eine Kernel-STOP-Anzeige angehalten wird. Der Schalter **/debug** verwendet im Gegensatz zum Schalter **/crashdebug** den COM-Anschluss, unabhängig davon, ob ein Debuggen erfolgt oder nicht. Dieser Schalter wird beim Debuggen von regulär reproduzierbaren Problemen verwendet. Der Parameter **/debug** wurde voraussichtlich zum Zweck der Fehlerbehebung für ein Problem festgelegt und wurde unabsichtlich beibehalten.

Das Ausführen zusätzlicher Prozesse wirkt sich negativ auf die Systemleistung aus. Es ist daher nicht empfehlenswert, Exchange Server auf einem Computer auszuführen, auf dem Windows im Debugmodus ausgeführt wird.

Um diesen Fehler zu beheben, bearbeiten Sie die Datei „Boot.ini“, und löschen Sie den Parameter **/debug**.

## So beheben Sie diesen Fehler

1.  Navigieren Sie in Windows Explorer zur Systempartition. Auf dieser Partition befinden sich hardwarespezifische Dateien wie „Boot.ini“ und „NTLDR“.

2.  Wenn die Boot.ini-Datei nicht angezeigt wird, hat das möglicherweise die Ursache, dass die Ordneroptionen für das Ausblenden geschützter Betriebssystemdateien eingestellt sind. Wenn dies der Fall ist, klicken Sie in Windows Explorer-Fenster auf **Extras** und **Ordneroptionen**, und klicken Sie dann auf **Ansicht**. Deaktivieren Sie das Kontrollkästchen **Geschützte Systemdateien ausblenden (empfohlen)**. Klicken Sie auf **Ja**, wenn Sie dazu aufgefordert werden.

3.  Wenn die Datei „Boot.ini“ in Windows Explorer angezeigt wird, klicken Sie mit der rechten Maustaste auf die Datei, klicken dann auf **Öffnen mit** und schließlich auf **Editor**, um die Datei zu öffnen.

4.  Entfernen Sie im Abschnitt **\[Operating Systems\]** den Parameter **/debug**.

5.  Speichern Sie die Datei, und schließen Sie sie. Starten Sie dann den Exchange Server-Computer neu, damit die Änderung wirksam wird.

Weitere Informationen zu den Parametern, die in der Datei „Boot.ini“ verwendet werden können, finden Sie im Microsoft Knowledge Base-Artikel 833721 „Verfügbare Befehlszeilenoptionen für die Boot.ini-Dateien von Windows XP und Windows Server 2003“ ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=833721](https://go.microsoft.com/fwlink/?linkid=3052&kbid=833721)).

