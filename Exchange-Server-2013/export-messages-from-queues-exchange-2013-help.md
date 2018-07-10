---
title: 'Nachrichten aus Warteschlangen exportieren: Exchange 2013 Help'
TOCTitle: Nachrichten aus Warteschlangen exportieren
ms:assetid: 688b342c-f380-4fe0-afce-7e38cf490627
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998625(v=EXCHG.150)
ms:contentKeyID: 51409309
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Nachrichten aus Warteschlangen exportieren

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-05-05_

Beim Exportieren einer Nachricht aus einer Warteschlange in eine Datei wird die Nachricht nicht aus der Warteschlange entfernt. Im angegebenen Verzeichnis wird eine Kopie der Nachricht in Form einer Nur-Text-Datei erstellt. Die erstellte Datei kann in einer Anwendung, beispielsweise in einem Text-Editor oder in einer E-Mail-Clientanwendung, angezeigt werden. Die Nachrichtendatei kann auch mithilfe des Wiedergabeverzeichnisses auf jedem anderen Postfach- oder Edge-Transport-Server innerhalb oder außerhalb der Exchange-Organisation erneut übermittelt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Nachrichten müssen sich im Zustand "Angehalten" befinden, damit der Nachrichtenexportprozess erfolgreich verlaufen kann. Sie können Nachrichten aus Zustellungswarteschlangen, der Nicht-erreichbar-Warteschlange und der Warteschlange für nicht verarbeitbare Nachrichten exportieren. Nachrichten in der Warteschlange für nicht verarbeitete Nachrichten befinden sich bereits im Zustand "Angehalten". Nachrichten in der Übermittlungswarteschlange können weder angehalten noch exportiert werden.

  - Sie können nicht die Warteschlangenanzeige in der Exchange-Toolbox zum Exportieren von Nachrichten verwenden. Sie können jedoch über die Warteschlangenanzeige Nachrichten suchen, identifizieren und anhalten, bevor Sie sie über die Shell exportieren.

  - Überprüfen Sie folgende Informationen zum Speicherort des Zielverzeichnisses für die Nachrichtendateien:
    
      - Das Zielverzeichnis muss vorhanden sein, bevor Nachrichten exportiert werden können. Dieses Verzeichnis müssen Sie selbst erstellen. Wenn kein absoluter Pfad angegeben ist, wird das aktuelle Arbeitsverzeichnis der Exchange-Verwaltungsshell verwendet.
    
      - Es kann sich um einen lokalen Pfad auf dem Server mit Exchange oder um einen UNC-Pfad (Universal Naming Convention) zu einer Freigabe auf einem Remoteserver handeln.
    
      - Ihr Konto muss über die Berechtigung **Write** für das Zielverzeichnis verfügen.
    
      - Stellen Sie beim Angeben eines Dateinamens für die exportierten Nachrichten sicher, dass die Datei die Dateinamenerweiterung EML aufweist, damit die Datei problemlos in E-Mail-Clientanwendungen geöffnet oder ordnungsgemäß vom Wiedergabeverzeichnis verarbeitet werden kann.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Exportieren einer bestimmten Nachricht aus einer bestimmten Warteschlange

Führen Sie den folgenden Befehl aus, um eine bestimmte Nachricht aus einer bestimmten Warteschlange zu exportieren:

    Export-Message -Identity <MessageIdentity> | AssembleMessage -Path <FilePath>\<FileName>.eml

In diesem Beispiel wird eine Kopie einer Nachricht mit dem **InternalMessageID**-Wert "1234", die sich in der Zustellungswarteschlange für "Contoso.com" auf dem Server "Mailbox01" befindet, in "D:\\Contoso Export\\export.eml" exportiert.

    Export-Message -Identity Exchange01\Contoso.com\1234 | AssembleMessage -Path "D:\Contoso Export\export.eml"

## Verwenden der Shell zum Exportieren aller Nachrichten aus einer bestimmten Warteschlange

Wenn Sie alle Nachrichten aus einer bestimmten Warteschlange exportieren und den **InternetMessageID**-Wert jeder Nachricht als Dateinamen verwenden möchten, wählen Sie die folgende Syntax.

    Get-Message -Queue <QueueIdentity> | ForEach-Object {$Temp=<Path>+$_.InternetMessageID+".eml";$Temp=$Temp.Replace("<","_");$Temp=$Temp.Replace(">","_");Export-Message $_.Identity | AssembleMessage -Path $Temp}

Beachten Sie, dass der **InternetMessageID**-Wert eckige Klammern (\> und \<) enthält, die entfernt werden müssen, da sie in Dateinamen unzulässig sind.

Dieser Beispielbefehl exportiert eine Kopie aller Nachrichten aus der Zustellungswarteschlange auf dem Server "Mailbox01" in das lokale Verzeichnis "D:\\Contoso Export".

    Get-Message -Queue Mailbox01\Contoso.com | ForEach-Object {$Temp="D:\Contoso Export\"+$_.InternetMessageID+".eml";$Temp=$Temp.Replace("<","_");$Temp=$Temp.Replace(">","_");Export-Message $_.Identity | AssembleMessage -Path $Temp}

## Verwenden der Shell zum Exportieren bestimmter Nachrichten aus allen Warteschlangen auf einem Server

Wenn Sie bestimmte Nachrichten aus allen Warteschlangen auf einem Server exportieren und den **InternetMessageID**-Wert jeder Nachricht als Dateinamen verwenden möchten, wählen Sie die folgende Syntax.

    Get-Message -Filter {<MessageFilter>} [-Server <ServerIdentity>] | ForEach-Object {$Temp=<Path>+$_.InternetMessageID+".eml";$Temp=$Temp.Replace("<","_");$Temp=$Temp.Replace(">","_");Export-Message $_.Identity | AssembleMessage -Path $Temp}

Beachten Sie, dass der **InternetMessageID**-Wert eckige Klammern (\> und \<) enthält, die entfernt werden müssen, da sie in Dateinamen unzulässig sind.

Dieser Beispielbefehl exportiert eine Kopie aller Nachrichten von Absendern in der Domäne "contoso.com" aus allen Warteschlangen auf dem Server "Mailbox01" in das lokale Verzeichnis "D:\\Contoso Export".

    Get-Message -Filter {FromAddress -like "*@contoso.com"} -Server Mailbox01 | ForEach-Object {$Temp="D:\Contoso Export\"+$_.InternetMessageID+".eml";$Temp=$Temp.Replace("<","_");$Temp=$Temp.Replace(">","_");Export-Message $_.Identity | AssembleMessage -Path $Temp}


> [!NOTE]
> Wenn Sie den Parameter <EM>Server</EM> weglassen, wird der Befehl auf den lokalen Server angewendet.


