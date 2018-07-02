---
title: 'Verschieben eines öffentlichen Ordners in ein anderes Postfach für öffentliche Ordner: Exchange 2013 Help'
TOCTitle: Verschieben eines öffentlichen Ordners in ein anderes Postfach für öffentliche Ordner
ms:assetid: b8744934-a3cb-443e-acce-a9a6ca5d88f6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ906435(v=EXCHG.150)
ms:contentKeyID: 51409334
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verschieben eines öffentlichen Ordners in ein anderes Postfach für öffentliche Ordner

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-11-16_

Wenn der Umfang des Inhalts eines Postfachs für öffentliche Ordner beginnt, die geltenden Postfachkontingente zu überschreiten, können Sie öffentliche Ordner in ein andere Postfach für öffentliche Ordner verschieben. Hierfür gibt es mehrere Möglichkeiten. Zum Verschieben eines oder mehrerer öffentlicher Ordner ohne Unterordner können Sie die Cmdlets **PublicFolderMoveRequest** verwenden. Wenn Sie eine gesamte Verzweigung öffentlicher Ordner (mit dem übergeordneten öffentlichen Ordner und allen Unterordnern) verschieben müssen, können Sie dazu das Skript `Move-PublicFolderBranch.ps1` verwenden, das zur Standardinstallation von Exchange 2013 gehört.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Die geschätzte Dauer des Vorgangs hängt von der Größe des öffentlichen Ordners ab.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Diese Verfahren können nicht mit der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Wenn der zu verschiebende Ordner Unterordner enthält, werden diese Unterordner nicht standardmäßig verschoben. Wenn Sie einen öffentlichen Ordner und alle seine Unterordner verschieben möchten, verwenden Sie das Skript **Move-PublicFolderBranch.ps1**.

  - Beim Verschieben öffentlicher Ordner wird nur der physische Inhalt des öffentlichen Ordners verschoben, ohne dass sich die logische Hierarchie ändert.

  - Je nach Größe des öffentlichen Ordners und des Inhaltsumfangs kann der Verschiebevorgang mehrere Stunden dauern. Während dieser Zeit können Benutzer nicht auf die öffentlichen Ordner zugreifen. Außerdem können Benutzer für einen kurzen Zeitraum nicht auf öffentliche Ordner zugreifen, solange der Ordner den Status "Fertigstellung wird ausgeführt" hat.

  - Sie können immer nur eine Anforderung zum Verschieben eines öffentlichen Ordners erfüllen. Sie müssen das Cmdlet **Remove-PublicFolderMoveRequest** verwenden, um die Anforderung nach ihrer Erfüllung zu entfernen.

  - Führen Sie das Cmdlet [Get-PublicFolderMoveRequest](https://technet.microsoft.com/de-de/library/jj878076\(v=exchg.150\)) aus, um den Status einer laufenden Verschiebung eines öffentlichen Ordners anzuzeigen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Einen einzelnen öffentlichen Ordner verschieben

Dieses Beispiel startet die Verschiebungsanforderung für den öffentlichen Ordner "\\CustomerEnagagements" aus dem Postfach für öffentliche Ordner "DeveloperReports" in das Postfach "DeveloperReports01"

    New-PublicFolderMoveRequest -Folders \DeveloperReports\CustomerEngagements -TargetMailbox DeveloperReports01


> [!NOTE]
> Das Zielpostfach für öffentliche Ordner ist gesperrt, während die Verschiebungsanforderung aktiv ist.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-PublicFolderMoveRequest](https://technet.microsoft.com/de-de/library/jj878081\(v=exchg.150\)).

## Mehrere öffentliche Ordner verschieben

Dieses Beispiel startet die Verschiebungsanforderung für öffentlichen Ordner unter der Verzweigung "\\Dev public" in das Zielpostfach "DeveloperReports01". Bei diesem Beispiel wird der öffentlichen Ordner "\\Dev" nicht verschoben.

    New-PublicFolderMoveRequest -Folders \Dev\CustomerEngagements,\Dev\RequestsforChange,\Dev\Usability -TargetMailbox DeveloperReports01


> [!NOTE]
> Das Zielpostfach für öffentliche Ordner ist gesperrt, während die Verschiebungsanforderung aktiv ist.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-PublicFolderMoveRequest](https://technet.microsoft.com/de-de/library/jj878081\(v=exchg.150\)).

## Eine Verzweigung öffentlicher Ordner verschieben

In diesem Beispiel wird das Skript `Move-PublicFolderBranch.ps1` zum Verschieben einer Verzweigung öffentlicher Ordner verwendet. Dieses Beispiel startet die Verschiebungsanforderung für den öffentlichen Ordner "\\Dev" und alle seine Unterordner aus dem Postfach für öffentliche Ordner "DeveloperReports01". Das Skript befindet sich im Ordner "scripts" und muss an diesem Speicherort ausgeführt werden.

    CD $env:ExchangeInstallPath\scripts
    
    .\Move-PublicFolderBranch.ps1 -FolderRoot \Dev -TargetPublicFolderMailbox DeveloperReports01

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um sicherzustellen, dass die Verschiebungsanforderung für öffentliche Ordner erfolgreich war:

    Get-PublicFolderMoveRequest | Format-List Status

Der Status `Completed` bedeutet, dass die Verschiebungsanforderung erfolgreich war.

Wenn die Verschiebungsanforderung keinen Erfolg hatte, müssen Sie den öffentlichen Ordner oder seinen Inhalt ggf. wiederherstellen. Weitere Informationen finden Sie unter [Wiederherstellen von öffentlichen Ordnern und Postfächern für öffentliche Ordner aus fehlerhaften Verschiebungen](restore-public-folders-and-public-folder-mailboxes-from-failed-moves-exchange-2013-help.md).

