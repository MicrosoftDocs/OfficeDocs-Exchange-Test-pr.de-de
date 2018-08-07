---
title: 'Versch. einer Postfachdatenbank m. Datenbankportabilität: Exchange 2013-Hilfe'
TOCTitle: Verschieben einer Postfachdatenbank mithilfe der Datenbankportabilität
ms:assetid: a765ead1-43bc-4786-ae93-1835cacfc8fc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876926(v=EXCHG.150)
ms:contentKeyID: 51409326
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verschieben einer Postfachdatenbank mithilfe der Datenbankportabilität

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-16_

Mithilfe von Datenbankportabilität können Sie eine Microsoft Exchange Server 2013-Postfachdatenbank zwischen Exchange 2013-Postfachservern innerhalb derselben Organisation verschieben. Auf diese Weise können allgemeine Wiederherstellungszeiten für einige Fehlerszenarien reduziert werden. Weitere Informationen finden Sie unter [Datenbankportabilität](database-portability-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten, zuzüglich der erforderlichen Zeit zum Wiederherstellen der Daten, Verschieben der Datenbankdateien und Warten auf den Abschluss der Active Directory-Replikation.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Verschieben von Benutzerpostfächern in eine wiederhergestellte oder Dial Tone-Datenbank mithilfe von Datenbankportabilität verwendet werden.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Verschieben von Benutzerpostfächern in eine wiederhergestelllte oder Dial Tone-Datenbank mithilfe von Datenbankportabilität

1.  Stellen Sie sicher, dass sich die Datenbank, die verschoben werden soll, im Status für fehlerfreies Herunterfahren befindet. Wenn sich die Datenbank nicht im Status für fehlerfreies Herunterfahren befindet, führen Sie einen Soft Recovery-Vorgang aus.
    

    > [!NOTE]
    > Beim Ausführen eines Soft Recovery-Vorgangs wird für alle nicht ausgeführten Protokolldateien ein Commit in der Datenbank ausgeführt. Wenn Sie nicht über alle erforderlichen Protokolldateien verfügen, können Sie den Soft Recovery-Vorgang nicht abschließen. Fahren Sie mit Schritt&nbsp;2 fort.

    
    Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus, um einen Commit für alle nicht übergebenen Protokolldateien in die Datenbank auszuführen.
    
        ESEUTIL /R <Enn>
    

    > [!NOTE]
    > &lt;E<EM>nn</EM>&gt; gibt das Protokolldateipräfix für die Datenbank an, in die die Protokolldateien wiedergegeben werden sollen. Das durch &lt;E<EM>nn</EM>&gt; angegebene Protokolldateipräfix ist ein erforderlicher Parameter für Eseutil /r.



2.  Erstellen Sie eine Datenbank auf einem Server mit der folgenden Syntax:
    
        New-MailboxDatabase -Name <DatabaseName> -Server <ServerName> -EdbFilePath <DatabaseFileNameandPath> -LogFolderPath <LogFilesPath>

3.  Legen Sie das Attribut *This database can be over written by restore* mithilfe der folgenden Syntax fest:
    
        Set-MailboxDatabase <DatabaseName> -AllowFileRestore $true

4.  Verschieben Sie die Datenbankdateien (EDB-Datei, Protokolldateien und Exchange-Suchkatalog) in den Datenbankordner, die Sie bei der Erstellung der neuen Datenbank oben angegeben haben.

5.  Binden Sie die Datenbank mithilfe der folgenden Syntax ein:
    
        Mount-Database <DatabaseName>

6.  Nachdem die Datenbank eingebunden wurde, ändern Sie die Benutzerkonteneinstellungen mit dem Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) so, dass das Konto auf das Postfach auf dem neuen Postfachserver verweist. Verwenden Sie die folgende Syntax, um alle Benutzer aus der alten in die neue Datenbank zu verschieben.
    
        Get-Mailbox -Database <SourceDatabase> |where {$_.ObjectClass -NotMatch '(SystemAttendantMailbox|ExOleDbSystemMailbox)'}| Set-Mailbox -Database <TargetDatabase>

7.  Sendeauslöser für Nachrichten mithilfe der folgenden Syntax.
    
        Get-Queue <QueueName> | Retry-Queue -Resubmit $true

Nach dem Abschluss der Active Directory-Replikation können alle Benutzer auf ihre Postfächer auf dem neuen Exchange-Server zugreifen. Die meisten Clients werden über AutoErmittlung umgeleitet. Microsoft Office Outlook Web App-Benutzer werden ebenfalls automatisch umgeleitet.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Sie ein Postfach erfolgreich verschoben haben:

  - Öffnen Sie das Postfach in Outlook Web App.

  - Öffnen Sie das Postfach mit Microsoft Outlook.

