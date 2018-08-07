---
title: 'Verschieben eines Postfachs für öffent. Ordner in andere Postfachdatenbank'
TOCTitle: Verschieben eines Postfachs für öffentliche Ordner in eine andere Postfachdatenbank
ms:assetid: 67601d45-4824-4ae6-9a7e-b645ec3af4d3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ906434(v=EXCHG.150)
ms:contentKeyID: 51409308
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verschieben eines Postfachs für öffentliche Ordner in eine andere Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-07-21_

Sie müssen ein Postfach für öffentliche Ordner ggf. in eine andere Postfachdatenbank verschieben, wenn Sie den Lastenausgleich verbessern oder Ressourcen näher an ihren geografischen Standort verschieben möchten. Ähnlich wie zum Verschieben eines herkömmlichen Postfachs verwenden Sie die **MoveRequest**-Cmdlets zum Verschieben eines Postfachs für öffentliche Ordner. Weitere Informationen zum Verschieben von Postfächern finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Die geschätzte Dauer des Vorgangs hängt von der Größe des Postfachs für öffentliche Ordner ab.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für Postfachverschiebungen und -migrationen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht im EAC ausgeführt werden. Es kann nur über die Shell erfolgen.

  - Je nach der Größe des Postfachs für öffentlichen Ordner kann der Verschiebevorgang mehrere Stunden dauern. Während dieser Zeit können Benutzer nicht auf die öffentlichen Ordner zugreifen. Außerdem können Benutzer für einen kurzen Zeitraum nicht auf öffentliche Ordner zugreifen, solange der Ordner den Status "Fertigstellung wird ausgeführt" hat.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Verschiebungsanforderung

Das Cmdlet **New-MoveRequest** reiht das Postfach für öffentliche Ordner in die Warteschlange des Microsoft Exchange-Postfachreplikationsdiensts ein. Sobald der Microsoft Exchange-Postfachreplikationsdienst verfügbar ist, beginnt er mit der Verarbeitung der Verschiebungsanforderung und dem Verschieben des Postfachs für öffentliche Ordner. Der Dienst wickelt die gesamte Anforderung von Anfang bis Ende ab.

In diesen Beispiel wird die Verschiebungsanforderung des Postfachs für öffentliche Ordner "PF\_SanFrancisco" in die Postfachdatenbank MBX\_DB01 begonnen.

    New-MoveRequest -Identity "PF_SanFrancisco" -TargetDatabase MBX_DB01

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

## Erstellen einer Verschiebungsanforderung, die zu einem späteren Zeitpunkt abgeschlossen werden soll

In der letzten Phase der Verschiebungsanforderung mit dem Namen `CompletionInProgress` wird das Postfach für öffentliche Ordner für Benutzer gesperrt. Falls erforderlich, können Sie die Verschiebungsanforderung vor Erreichen dieser Phase anhalten und zu einem Zeitpunkt fortsetzen, zu dem Benutzer nicht beeinträchtigt werden.

In diesen Beispiel wird die Verschiebungsanforderung des Postfachs für öffentliche Ordner "PF\_SanFrancisco" in die Postfachdatenbank MBX\_DB01 begonnen und angehalten, wenn die Verschiebungsanforderung kurz vor dem Abschluss steht.

    New-MoveRequest -Identity "PF_SanFrancisco" -TargetDatabase MBX_DB01 -SuspendWhenReadyToComplete

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\)).

In diesem Beispiel wird der Status der laufenden Postfachverschiebung für das Postfach für öffentliche Ordner "PF\_SanFrancisco" abgerufen.

    Get-MoveRequest -Identity "PF_SanFrancisco"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-MoveRequest](https://technet.microsoft.com/de-de/library/dd335227\(v=exchg.150\)).

Wenn die Verschiebungsanforderung den Status "Angehalten" erreicht, können Sie die Anforderung fortsetzen. In diesem Beispiel wird die Verschiebungsanforderung für das Postfach für öffentliche Ordner "PF\_SanFrancisco" fortgesetzt.

    Resume-MoveRequest -Identity "PF_SanFrancisco"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Resume-MoveRequest](https://technet.microsoft.com/de-de/library/ee332320\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um sicherzustellen, dass die Verschiebungsanforderung erfolgreich erstellt wurde:

    Get-MoveRequestStatistics -Identity PF_SanFrancisco | Format-List Status

Der Status `Completed` bedeutet, dass die Verschiebungsanforderung erfolgreich war.

Wenn die Verschiebung keinen Erfolg hatte, müssen Sie den öffentlichen Ordner ggf. wiederherstellen. Weitere Informationen finden Sie unter [Wiederherstellen von öffentlichen Ordnern und Postfächern für öffentliche Ordner aus fehlerhaften Verschiebungen](restore-public-folders-and-public-folder-mailboxes-from-failed-moves-exchange-2013-help.md).

