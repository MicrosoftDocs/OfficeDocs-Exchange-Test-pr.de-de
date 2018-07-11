---
title: 'Durchführen einer "Dial Tone"-Wiederherstellung: Exchange 2013 Help'
TOCTitle: Durchführen einer "Dial Tone"-Wiederherstellung
ms:assetid: 158817fa-4b17-4fa9-8341-a86609e6a388
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979810(v=EXCHG.150)
ms:contentKeyID: 51409269
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Durchführen einer \"Dial Tone\"-Wiederherstellung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-27_

Durch die Dial Tone-Portabilität erhalten Benutzer die Möglichkeit, ein temporäres Postfach zum Senden und Empfangen von E-Mails zu nutzen, während ihr ursprüngliches Postfach wiederhergestellt oder repariert wird. Das temporäre Postfach kann sich auf demselben Exchange 2013-Postfachserver oder auf einem beliebigen anderen Exchange 2013-Postfachserver in der Organisation befinden. Der Vorgang der Verwendung der Dial Tone-Portabilität wird als Dial Tone-Wiederherstellung bezeichnet. Zu diesem Vorgang gehört auch das Erstellen einer leeren Datenbank auf einem Postfachserver, durch die eine fehlerhafte Datenbank ersetzt wird. Weitere Informationen finden Sie unter [Dial Tone-Portabilität](dial-tone-portability-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten, plus die Zeit, die zum Wiederherstellen und Verschieben der Daten benötigt wird.

  - Zum Erstellen einer Dial Tone-Datenbank darf die Anzahl der Datenbanken nicht die Anzahl der bereitgestellten Datenbanken überschreiten. Exchange 2013 Standard Edition unterstützt maximal fünf Datenbanken pro Server. Exchange 2013 Die Enterprise Edition unterstützt maximal 50 Datenbanken pro Server in RTM und CU1 und 100 Datenbanken pro Server in CU 2 und höher.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Ausführen einer Dial Tone-Wiederherstellung auf einem einzelnen Server


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Ausführen einer Dial Tone-Wiederherstellung auf einem einzelnen Server verwendet werden.



1.  Stellen Sie sicher, dass alle vorhandenen Dateien für die wiederherzustellende Datenbank erhalten bleiben, falls sie später für weitere Wiederherstellungsoperationen benötigt werden.

2.  Verwenden Sie das Cmdlet [New-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997976\(v=exchg.150\)), um eine Dial Tone-Datenbank zu erstellen, wie im folgenden Beispiel dargestellt.
    
        New-MailboxDatabase -Name DTDB1 -EdbFilePath D:\DialTone\DTDB1.EDB

3.  Verwenden Sie das Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)), um die Benutzerpostfächer, die in der wiederherzustellenden Datenbank gehostet werden, zuzuweisen, wie im folgenden Beispiel dargestellt.
    
        Get-Mailbox -Database DB1 | Set-Mailbox -Database DTDB1

4.  Verwenden Sie das Cmdlet [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\)), um die Datenbank einzubinden, sodass Clientcomputer auf die Datenbank zugreifen und Nachrichten senden und empfangen können, wie im folgenden Beispiel dargestellt.
    
        Mount-Database -Identity DTDB1

5.  Erstellen Sie eine Wiederherstellungsdatenbank (Recovery Database, RDB), und stellen Sie die Datenbank und Protokolldateien wieder her (bzw. kopieren Sie sie), in denen die Daten enthalten sind, die in der RDB wiederhergestellt werden sollen. Weitere Informationen finden Sie unter [Erstellen einer Wiederherstellungsdatenbank](create-a-recovery-database-exchange-2013-help.md).

6.  Nachdem Sie die Daten in die RDB kopiert haben, jedoch bevor Sie die wiederhergestellte Datenbank einbinden, kopieren Sie die Protokolldateien aus der fehlerhaften Datenbank in den Protokollordner der Wiederherstellungsdatenbank, sodass sie mit der wiederhergestellten Datenbank abgeglichen werden können.

7.  Binden Sie die RDB ein, und verwenden Sie dann das Cmdlet [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\)), um die Einbindung der Datenbank aufzuheben, wie im folgenden Beispiel dargestellt.
    
        Mount-Database -Identity RDB1
        Dismount-Database -Identity RDB1

8.  Nachdem Sie die Einbindung der RDB aufgehoben haben, verschieben Sie die aktuelle Datenbank und die Protokolldateien aus dem Ordner der RDB an einen sicheren Ort. Dieser Schritt gilt als Vorbereitung für den Austausch von wiederhergestellter Datenbank und Dial Tone-Datenbank.

9.  Heben Sie die Einbindung der Dial Tone-Datenbank auf, wie im folgenden Beispiel dargestellt. Bei den Endbenutzern kommt es zu einer Betriebsunterbrechung, während Sie die Einbindung der Datenbank aufheben.
    
        Dismount-Database -Identity DTDB1

10. Verschieben Sie die Datenbank und die Protokolldateien aus dem Ordner der Dial Tone-Datenbank in der Ordner der RDB.

11. Verschieben Sie die Datenbank und die Protokolldateien von dem sicheren Ort, an dem sich die wiederhergestellte Datenbank befindet, in den Ordner der Dial Tone-Datenbank, und binden Sie dann die Datenbank ein, wie im folgenden Beispiel dargestellt.
    
        Mount-Database -Identity DTDB1
    
    Hierdurch wird die Betriebsunterbrechung für die Endbenutzer beendet. Diese können nun wieder auf die ursprüngliche Produktionsdatenbank zugreifen und Nachrichten senden und empfangen.

12. Binden Sie die RDB ein, wie im folgenden Beispiel dargestellt.
    
        Mount-Database -Identity RDB1

13. Verwenden Sie die Cmdlets [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) und [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)), um die Daten aus der RDB zu exportieren und in die wiederhergestellte Datenbank zu importieren, wie im folgenden Beispiel dargestellt. Durch diesen Vorgang werden alle mithilfe der Dial Tone-Datenbank gesendeten und empfangenen Nachrichten in die Produktionsdatenbank importiert.
    
```
    $mailboxes = Get-Mailbox -Database DTDB1
```

```
    $mailboxes | %{ New-MailboxRestoreRequest -SourceStoreMailbox $_.ExchangeGuid -SourceDatabase RDB1 -TargetMailbox $_ }
```

14. Sobald der Wiederherstellungsvorgang beendet ist, können Sie die Einbindung der RDB aufheben und sie entfernen, wie im folgenden Beispiel dargestellt.
    
        Dismount-Database -Identity RDB1
        Remove-MailboxDatabase -Identity RDB1

Ausführliche Informationen zu Syntax und Parametern finden Sie unter den folgenden Themen:

  - [New-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997976\(v=exchg.150\))

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Mount-Database](https://technet.microsoft.com/de-de/library/aa998871\(v=exchg.150\))

  - [Dismount-Database](https://technet.microsoft.com/de-de/library/bb124936\(v=exchg.150\))

  - [Remove-MailboxDatabase](https://technet.microsoft.com/de-de/library/aa997931\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Sie ein Postfach erfolgreich verschoben haben:

  - Öffnen Sie das Postfach mithilfe von Microsoft Office Outlook Web App.

  - Öffnen Sie das Postfach mit Microsoft Outlook.

