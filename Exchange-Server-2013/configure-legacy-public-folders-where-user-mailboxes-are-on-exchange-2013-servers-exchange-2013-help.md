---
title: 'Konfig. älterer öfftl. Ordner, wenn Postf. auf Exchange 2013-Servern exist.'
TOCTitle: Konfigurieren älterer öffentlicher Ordner, wenn sich die Postfächer der Benutzer auf Exchange 2013-Servern befinden
ms:assetid: 1d5ca19e-696e-4054-a634-15dd34d952b7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn690134(v=EXCHG.150)
ms:contentKeyID: 62281107
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren älterer öffentlicher Ordner, wenn sich die Postfächer der Benutzer auf Exchange 2013-Servern befinden

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-03-27_

Informationen zum Aktivieren von Exchange 2013 oder Exchange 2016 Benutzer Zugriff auf Exchange 2010 oder früheren öffentlichen Ordnern (auch bekannt als ältere öffentliche Ordner).

## Was sollten Sie wissen, bevor Sie beginnen?

Benutzer, deren Postfächer auf Exchange Server 2013 oder Exchange Server 2016 sind, nicht auf ältere öffentliche Ordner von Outlook Web App, Outlook im Web oder Outlook für Mac zugreifen Die Schritte in diesem Artikel Arbeit für Exchange 2013 und Exchange 2016.


> [!NOTE]
> Benutzer von Outlook 2016 für Mac können auf ältere öffentliche Ordner zugreifen, nachdem Sie die Schritte in diesem Artikel durchgeführt haben. Wenn Clients in Ihrer Organisation Outlook 2016 für Mac verwenden, stellen Sie sicher, dass sie das Update von April 2016 installiert haben. Andernfalls können diese Benutzer nicht auf öffentliche Ordner in einer Koexistenz oder einer Hybrid-Topologie zugreifen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/access-public-folders-with-outlook-2016-for-mac">Zugreifen auf öffentliche Ordner mit Outlook&nbsp;2016&nbsp;für&nbsp;Mac</A>.



## Schritt 1: Öffentliche Ordner in Exchange 2010 sichtbar machen

1.  Wenn sich Ihre öffentlichen Ordner auf Exchange 2010-Servern oder höher befinden, müssen Sie die Clientzugriffs-Serverrolle auf allen Postfachservern installieren, auf denen sich eine Datenbank für öffentliche Ordner befindet. Dadurch kann der Microsoft Exchange RpcClientAccess-Dienst ausgeführt werden, der allen Clients Zugriff auf öffentliche Ordner ermöglicht. Die Clientzugriffsrolle ist für Server für öffentliche Ordner in Exchange 2007 nicht erforderlich, und dieser Schritt ist nicht notwendig. Weitere Informationen finden Sie unter [Installieren von Exchange Server 2010](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md).
    

    > [!NOTE]
    > Dieser Server muss nicht Teil des Lastenausgleichs von Clientzugriffsservern sein. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/ff625247(v=exchg.141).aspx">Grundlegendes zum Lastenausgleich in Exchange 2010</A>.



2.  Erstellen Sie eine leere Postfachdatenbank auf jedem Server für öffentliche Ordner.
    
    Führen Sie bei Exchange 2010 den folgenden Befehl aus: Durch diesen Befehl wird die Postfachdatenbank vom Lastenausgleich für Postfachbereitstellung ausgeschlossen. Dadurch wird verhindert, dass neue Postfächer automatisch zu dieser Datenbank hinzugefügt werden.
    
        New-MailboxDatabase -Server <PFServerName_with_CASRole> -Name <NewMDBforPFs> -IsExcludedFromProvisioning $true 
    
    Führen Sie bei Exchange 2007 den folgenden Befehl aus:
    
        New-MailboxDatabase -StorageGroup "<PFServerName>\StorageGroup>" -Name <NewMDBforPFs>
    

    > [!NOTE]
    > Es wird empfohlen, dass Sie nur das Proxypostfach, das Sie in Schritt&nbsp;3 erstellen, zu dieser Datenbank hinzufügen. In dieser Postfachdatenbank sollten keine anderen Postfächer erstellt werden.



3.  Erstellen Sie in der neuen Postfachdatenbank ein Proxypostfach, und blenden Sie das Postfach im Adressbuch aus. Das SMTP dieses Postfachs wird von der AutoErmittlung als das *DefaultPublicFolderMailbox*-SMTP zurückgegeben, sodass der Client durch Auflösung dieses SMTP den Exchange-Legacyserver erreichen kann, um Zugriff auf öffentliche Ordner zu erhalten.
    
	```
		New-Mailbox -Name <PFMailbox1> -Database <NewMDBforPFs> 
	```

	```
		Set-Mailbox -Identity <PFMailbox1> -HiddenFromAddressListsEnabled $true
	```

4.  Aktivieren Sie bei Exchange 2010 die AutoErmittlung, um die Proxypostfächer für öffentliche Ordner zurückzugeben. Dieser Schritt ist bei Exchange 2007 nicht erforderlich.
    
        Set-MailboxDatabase <NewMDBforPFs> -RPCClientAccessServer <PFServerName_with_CASRole>

5.  Wiederholen Sie die vorhergehenden Schritte für jeden Server für öffentliche Ordner in Ihrer Organisation.

## Schritt 2: Konfigurieren von Benutzerpostfächern für den Zugriff auf ältere öffentliche Ordner

Beim letzten Schritt dieses Verfahren werden die Benutzerpostfächer konfiguriert, um den Zugriff auf die älteren lokalen öffentlichen Ordner zu gewähren.

Aktivieren Sie die lokalen Exchange Server 2013-Benutzer für den Zugriff auf die älteren öffentlichen Ordner. Sie zeigen auf alle Proxypostfächer für öffentliche Ordne, die Sie in [Step 2: Make remote public folders discoverable](https://review.docs.microsoft.com/de-de/exchange/collaboration-exo/public-folders/set-up-legacy-hybrid-public-folders) erstellt haben. Führen Sie den folgenden Befehl auf einem Exchange 2013-Server mit dem Update CU5 oder höher aus.

    Set-OrganizationConfig -PublicFoldersEnabled Remote -RemotePublicFolderMailboxes ProxyMailbox1,ProxyMailbox2,ProxyMailbox3


> [!NOTE]
> Die Änderungen werden erst angezeigt, wenn die Active Directory-Synchronisierung abgeschlossen ist. Dieser Vorgang kann mehrere Stunden in Anspruch nehmen.



## Woher weiß ich, dass der Vorgang erfolgreich war?

Melden Sie sich bei Outlook für einen Benutzer an, dessen Postfach sich auf einem Server mit Exchange Server 2013 CU5 oder höher befindet und führen Sie die folgenden Tests für öffentliche Ordner durch:

1.  Stellen Sie sicher, dass der Outlook-Client ausgeführt wird.

2.  Klicken Sie bei gedrückter STRG-Taste mit der rechten Maustaste auf das Outlook-Symbol im Benachrichtigungsbereich auf der rechten Seite der Windows-Taskleiste.

3.  Wählen Sie die Option zum automatischen Testen der E-Mail-Konfiguration aus.

4.  Vergewissern Sie sich, dass das Tool zum Testen der automatischen E-Mail-Konfiguration auf der XML-Registerkarte die folgenden Informationen anzeigt:
    
      - \<PublicFolderInformation\>
    
      - \<SmtpAddress\>\<SMTP-Adresse für das Öffentliche Ordner-Postfach\</SmtpAddress\>
    
      - \</PublicFolderInformation\>

5.  Führen Sie im Outlook-Client die folgenden Aufgaben durch:
    
      - Zeigen Sie die Hierarchie öffentlicher Ordner an.
    
      - Prüfen Sie die Berechtigungen.
    
      - Erstellen und löschen Sie Öffentliche Ordner.
    
      - Veröffentlichen Sie Inhalte in einem Öffentlichen Ordner, und löschen Sie diese.

