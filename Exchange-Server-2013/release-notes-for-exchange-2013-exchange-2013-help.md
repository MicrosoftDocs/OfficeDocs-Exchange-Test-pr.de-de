---
title: 'Versionshinweise zu Exchange 2013: Exchange 2013 Help'
TOCTitle: Versionshinweise zu Exchange 2013
ms:assetid: 1879fd5e-3d63-4264-9cc2-9c050c6ab3c5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150489(v=EXCHG.150)
ms:contentKeyID: 50475101
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Versionshinweise zu Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-16_

Willkommen bei Microsoft Exchange Server 2013\! Dieses Thema enthält wichtige Informationen, die Sie für eine erfolgreiche Bereitstellung von Exchange 2013 benötigen. Bitte lesen Sie dieses Thema vollständig, bevor Sie mit der Bereitstellung beginnen.

Dieses Thema enthält die folgenden Abschnitte:

  - Setup und Bereitstellung

  - Exchange-Verwaltungsshell

  - Postfach

  - Öffentliche Ordner

  - Nachrichtenübermittlung

  - Client-Konnektivität

  - Exchange 2010-Koexistenz

## Setup und Bereitstellung

  - **msExchProductId berücksichtigt nicht installierte Exchange 2013-Version** Nachdem Exchange Ihr Active Directory-Schema erweitert und Active Directory für Exchange vorbereitet, werden verschiedene Eigenschaften aktualisiert, um anzuzeigen, dass die Vorbereitung abgeschlossen ist. Eine dieser Eigenschaften ist *msExchangeProductId* unter dem Container `CN=<your organization>, CN=Microsoft Exchange, CN=Services, CN=Configuration, DC=<domain>` im Namenskontext `Configuration`. Wenn in der von Ihnen zu installierenden Exchange 2013-Version keine Active Directory-Schemaänderungen vorgenommen wurden, wird diese Eigenschaft nicht aktualisiert oder zeigt möglicherweise einen unerwarteten Wert an. Dies könnte Verwirrung stiften, wenn der Wert nicht mit dem der zu installierenden Exchange 2013-Version übereinstimmt.
    
    Dieses Verhalten wird erwartet, wenn der Wert von *msExchProductId* die zu installierende Exchange 2013-Version nicht berücksichtigt. Diese Eigenschaft berücksichtigt die Exchange 2013-Version, die zuletzt Änderungen am Active Directory-Schema vorgenommen hat. Um Verwirrung zu vermeiden, sollten Sie die Schritte im Abschnitt [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) von [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md) befolgen. Somit können Sie sicherstellen, dass Ihr Active Directory aktualisiert wurde und für die von Ihnen zu installierende Exchange 2013-Version bereit ist.

  - **Setup fordert fälschlicherweise .NET Framework 4.0** an   Beim Versuch, Exchange 2013 auf einem Computer .NET Framework zu installieren, fordert Setup Sie fälschlicherweise zur Installation von .NET Framework 4.0 auf, obwohl die Version .NET Framework 4.5 oder höher benötigt wird.
    
    Um dieses Problem zu umgehen, installieren Sie .NET Framework 4.5 oder höher. Sie müssen .NET Framework nicht installieren. Eine vollständige Liste der Voraussetzungen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - **Exchange XML-Anwendungskonfigurationsdateien werden während der Installation kumulativer Updates überschrieben**   Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an "web.config"-Dateien auf Clientzugriffsservern bzw. an der Datei "EdgeTransport.exe.config" auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates oder Service Packs überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates oder Service Packs müssen Sie diese Einstellungen neu konfigurieren.

  - **Installieren von Exchange mithilfe von stellvertretenden Administratorrechten führt zum Setupfehler** Wenn ein Benutzer, der nur Mitglied der Rollengruppe „Stellvertretender Administrator“ ist, versucht Exchange auf einem bereitgestellten Server zu installieren, tritt ein Setupfehler auf. Dies liegt daran, dass die Gruppe „Delegiertes Setup“ nicht über die erforderlichen Berechtigungen zum Erstellen und Konfigurieren bestimmter Objekte in Active Directory verfügt.
    
    Führen Sie einen der folgenden Schritte aus, um das Problem zu umgehen:
    
      - Fügen Sie den Benutzer, der Exchange installiert, der Active Directory-Sicherheitsgruppe „Domänenadministratoren“ hinzu.
    
      - Installieren Sie Exchange unter Verwendung eines Benutzers, der Mitglied der Rollengruppe „Organisationsverwaltung“ ist.

Weitere Informationen zur Installation von Exchange 2013 finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

## Exchange-Verwaltungsshell

  - **Die Shell lädt unerwartet Exchange 2007- oder Exchange 2010-Cmdlets** Zuvor wurde beim Öffnen der Shell auf einem Exchange 2013-Server eine Verbindung mit einem lokalen Server oder einem anderen Server mit Exchange 2013 hergestellt. Nachdem die Verbindung hergestellt wurde, wurden Exchange 2013-Cmdlets geladen. Ab Exchange 2013 kumulatives Update 11 stellt die Shell eine Verbindung mit dem Exchange-Server her, auf dem sich das Postfach des angemeldeten Benutzers befindet. Wenn der angemeldete Benutzer über kein Postfach verfügt, stellt die Shell eine Verbindung mit dem Server her, auf dem sich das SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}-Vermittlungspostfach befindet. Der Zielserver kann über eine beliebige unterstützte Version von Exchange verfügen. Dies bedeutet, wenn sich das Postfach des angemeldeten Benutzers (oder das Vermittlungspostfach, wenn der Benutzer über kein Postfach verfügt) auf einem Exchange 2010-Server befindet, stellt die Shell eine Verbindung mit diesem Server her und lädt Exchange 2010-Cmdlets. Dies kann Sie daran hindern, bestimmte Aufgaben durchzuführen, da mit Exchange 2010-Cmdlets nicht die Exchange 2013-Konfiguration oder Server verwaltet werden können.
    
    Ab Exchange 2013 kumulatives Update 11 ist dieses Verhalten so beabsichtigt. Wenn Sie sicherstellen möchten, dass die Shell Exchange 2013-Cmdlets lädt, müssen Sie das Postfach des angemeldeten Benutzers zu Exchange 2013 verschieben. Wenn der angemeldete Benutzer über kein Postfach verfügt, müssen Sie das SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}-Vermittlungspostfach auf einen Exchange 2013-Server verschieben.
    
    Detaillierte Informationen zur Verschiebung des Vermittlungspostfachs finden Sie im englischsprachigen Artikel [Exchange Management Shell and Mailbox Anchoring](https://go.microsoft.com/fwlink/?linkid=717722) im Blog des Exchange-Teams.

## Postfach

  - **Postfachserver, auf denen verschiedene Versionen von Exchange ausgeführt werden, können derselben Datenbankverfügbarkeitsgruppe hinzugefügt werden** Das Cmdlet **Add-DatabaseAvailabilityGroupServer** und die Exchange-Verwaltungskonsole ermöglichen fälschlicherweise, dass ein Exchange 2013-Server einer Exchange 2016-basierten Datenbankverfügbarkeitsgruppe (DAG) hinzugefügt wird und umgekehrt. Exchange unterstützt nur das Hinzufügen von Postfachservern, auf denen die gleiche Version (z. B. Exchange 2013 im Vergleich zu Exchange 2016) ausgeführt wird, zu einer DAG. Darüber hinaus zeigt die Exchange-Verwaltungskonsole sowohl den Exchange 2013-Server als auch den Exchange 2016-Server in der Liste der Server an, die einer DAG hinzugefügt werden können. Damit könnte ein Administrator versehentlich einen Server, auf dem eine inkompatible Version von Exchange ausgeführt wird, zu einer DAG hinzufügen (beispielsweise das Hinzufügen eines Exchange 2013-Servers zu einer Exchange 2016-basierten DAG).
    
    Derzeit gibt es keine Abhilfe für dieses Problem. Administratoren müssen beim Hinzufügen eines Postfachservers zu einer DAG sorgfältig sein. Fügen Sie nur Exchange 2013-Server zu Exchange 2013-basierten DAGs hinzu, und nur Exchange 2016-Server zu Exchange 2016-basierten DAGs. Sie können jede einzelne Version von Exchange unterscheiden, indem Sie die Spalte **Version** in der Liste der Server in der Exchange-Verwaltungskonsole betrachten. Im Folgenden werden die Serverversionen für Exchange 2013 und Exchange 2016 angegeben:
    
      - **Exchange 2013** 15.0 (Build xxx.xx)
    
      - **Exchange 2016** 15.1 (Build xxx.xx)

  - **Erhöhung der Postfachgröße bei der Migration von früheren Exchange-Versionen**   Beim Verschieben eines Postfachs von einer früheren Version von Exchange auf Exchange 2013 steigt die angezeigte Postfachgröße möglicherweise um 30 bis 40 %. Der von der Postfachdatenbank belegte Festplattenspeicherplatz bleibt unverändert, lediglich die zugeordnete Größe der einzelnen Postfächer ist gestiegen. Der Grund für die Erhöhung der Postfachgröße ist die Aufnahme aller Elementeigenschaften in Kontingentberechnungen, sodass der durch die Elemente innerhalb eines Postfachs belegte Speicherplatz präziser berechnet werden kann. Aufgrund dieser Erhöhung überschreiten einige Benutzer beim Verschieben ihrer Postfächer nach Exchange 2013 möglicherweise die für die Postfachgröße festgelegten Kontingente.
    
    Erhöhen Sie die Kontingentwerte für die Datenbank oder die Postfächer, um die neue Kontingentberechnung zu ermöglichen, ohne dass die Benutzer die für die Postfachgröße festgelegten Kontingente überschreiten. Verwenden Sie die Parameter *IssueWarningQuota*, *ProhibitSendQuota* und *ProhibitSendReceiveQuota* mit den Cmdlets **Set-MailboxDatabase** und **Set-Mailbox**, um die Kontingentwerte für die Datenbank bzw. die Postfächer festzulegen.

  - **Outlook 2007- und Outlook 2010-Clients können das Offlineadressbuch möglicherweise nicht herunterladen**   Wenn die interne URL des Offlineadressbuchs (OAB) über das Internet nicht zugänglich ist, können Outlook 2007- und Outlook 2010-Clients das OAB möglicherweise nicht herunterladen.
    
    Machen Sie die interne URL des OAB über das Internet zugänglich, um dieses Problem bei Outlook 2007- und Outlook 2010-Clients zu umgehen. Outlook 2013 ist von diesem Problem nicht betroffen.

  - **Durch die Installation von Exchange 2013 in einer bestehenden Exchange-Organisation wird das OAB möglicherweise von allen Clients heruntergeladen**   Wenn Sie den ersten Exchange 2013-Server in einer bestehenden Exchange 2007- oder Exchange 2010-Organisation installieren, führt dies möglicherweise dazu, dass alle Clients in der Organisation eine neue Kopie des OAB herunterladen. Dies kann zu Netzwerküberlastung und Problemen mit der Serverleistung führen. Dieses Problem tritt auf, weil Exchange 2013 ein neues Standard-OAB in der Organisation erstellt, welches Vorrang vor dem Exchange 2007- bzw. Exchange 2010-OAB besitzt. Postfächer, denen kein bestimmtes OAB zugewiesen ist oder die in einer Postfachdatenbank ohne besondere OAB-Zuweisung gespeichert sind, laden das neue Standard-OAB herunter.
    
    Damit Clients bei der Installation von Exchange 2013 keine neue Kopie des OAB herunterladen, weisen Sie jedem Postfach oder der Postfachdatenbank, in der die Postfächer gespeichert sind, ein OAB zu. Dies muss vor der Installation von Exchange 2013 in der Organisation erfolgen.

  - **Benutzer werden möglicherweise an ein OAB-Generierungspostfach weitergeleitet, das für das angeforderte OAB nicht zuständig ist**   Mit Exchange 2013 CU5 und späteren kumulativen Updates wurde geändert, wie Offlineadressbücher mit OAB-Generierungspostfächern verknüpft sind. Durch diese Änderung wird es möglich, dass ein Benutzer an ein OAB-Generierungspostfach weitergeleitet wird, das nicht für das vom Benutzer angeforderte Offlineadressbuch zuständig ist. Dieses Problem kann auftreten, wenn alle nachstehenden Bedingungen zutreffen:
    
      - In Ihrer Organisation gibt es mehrere OAB-Generierungspostfächer.
    
      - Sie führen ein Upgrade der Postfachserver durch, die OAB-Generierungspostfächer hosten, bevor Sie ein Upgrade Ihrer Clientzugriffsserver durchführen.
    
      - Sie führen ein Upgrade Ihrer Exchange 2013-Server von einer Version vor CU5 auf eine höhere Version durch (beispielsweise Upgrade von Exchange 2013 CU3 auf Exchange 2013 CU6).
    
      - Auf den Clientzugriffsservern wird eine Version vor CU5 ausgeführt.
    
    Um dieses Problem zu umgehen, müssen Sie unbedingt vor dem Upgrade Ihrer Postfachserver ein Upgrade Ihrer Clientzugriffsserver auf Exchange 2013 KU6 oder höher durchführen. Dadurch wird sichergestellt, dass die Clientzugriffsserver wissen, wie Sie die Anforderungen an das OAB-Generierungspostfach, das für die Generierung des Offlineadressbuchs des Benutzer zuständig ist, mittels Proxy weiterleiten müssen.
    
    Weitere Informationen zu den OAB-Änderungen in Exchange 2013 CU5 finden Sie im englischsprachigen Artikel [OAB Improvements in Exchange 2013 Cumulative Update 5](https://go.microsoft.com/fwlink/p/?linkid=400642).

## Öffentliche Ordner

  - **Unautorisierte Absender können Nachrichten an öffentliche Ordner senden**   Vor Exchange 2013 CU6 konnten unautorisierte Absender Nachrichten an E-Mail-aktivierte öffentliche Ordner senden. Dadurch bestand die Möglichkeit, dass externe Absender, unabhängig von den für den öffentlichen Ordner festgelegten Berechtigungen, E-Mails an E-Mail-aktivierte öffentliche Ordner senden.
    
    Ab Exchange 2013 CU6 muss dem Benutzer mit dem Status **Anonym** zumindest die Berechtigung **Objekte erstellen** erteilt werden, wenn Sie zulassen möchten, dass externe Absender E-Mails an E-Mail-aktivierte öffentliche Ordner senden können. Wenn Sie E-Mail-aktivierte öffentliche Ordner eingerichtet und diese Berechtigung nicht erteilt haben, erhalten externe Absender eine Zustellungsfehlerbenachrichtung, und die Nachrichten werden dem E-Mail-aktivierten öffentlichen Ordner nicht zugestellt.
    
    Sie können die Shell oder Outlook verwenden, um die Berechtigungen für den anonymen Benutzer festzulegen. Weitere Informationen zum Festlegen der Berechtigungen für anonyme Benutzer finden Sie unter [E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern](mail-enable-or-mail-disable-a-public-folder-exchange-2013-help.md).

  - Die maximale Anzahl von öffentlichen Ordnern, die von Exchange-Legacyservern zu Exchange 2013 migriert werden können, beträgt 500.000. Weitere Informationen zur Migration öffentlicher Ordner finden Sie unter [Verwenden der Batchmigration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen](use-batch-migration-to-migrate-public-folders-to-exchange-2013-from-previous-versions-exchange-2013-help.md).

## Nachrichtenübermittlung

  - **Die TransportAgent-Cmdlets erfordern auf Clientzugriffsservern die Verwendung der lokalen Windows PowerShell**   Bei den Cmdlets **\*-TransportAgent** besteht ein Problem, aufgrund dessen diese Cmdlets nicht mit der Exchange-Verwaltungsshell verwendet werden können, um Transport-Agents auf Clientzugriffsservern zu installieren, zu deinstallieren und zu verwalten. Für die Installation, Deinstallation und Verwaltung von Transport-Agents auf Clientzugriffsservern müssen Sie das ExchangeWindows PowerShell-Snap-In manuell laden und anschließend die **\*-TransportAgent**-Cmdlets ausführen. Beim Versuch, Transport-Agents über die Exchange-Verwaltungsshell zu installieren, zu deinstallieren oder zu verwalten, werden die Änderungen auf den Exchange 2013-Postfachserver angewendet, mit dem Sie verbunden sind.
    
    Führen Sie auf dem Clientzugriffsserver, der verwaltet werden soll, die folgenden Schritte aus, um Transport-Agents auf diesem Server zu installieren, zu deinstallieren oder zu verwalten:
    

    > [!WARNING]
    > Das Laden des <CODE>Microsoft.Exchange.Management.PowerShell.SnapIn</CODE>Windows PowerShell-Snap-Ins und das Ausführen von anderen Cmdlets als den <STRONG>*-TransportAgent</STRONG>-Cmdlets wird nicht unterstützt und kann irreparable Schäden an der Exchange-Bereitstellung zur Folge haben.<BR>Sie müssen Mitglied der lokalen Administratorgruppe auf dem Clientzugriffsserver sein, auf dem Transport-Agents installiert, deinstalliert oder verwaltet werden sollen. Änderungen an Zugriffssteuerungslisten für Exchange-Dateien, Verzeichnisse oder Active Directory-Objekte werden nicht unterstützt.

    

    > [!IMPORTANT]
    > Führen Sie die folgenden Schritte ausschließlich auf einem Clientzugriffsserver aus. Das ExchangeWindows PowerShell-Snap-In muss nicht geladen werden, wenn Transport-Agents auf Postfachservern verwaltet werden sollen.

    
    1.  Öffnen Sie ein neues Windows PowerShell-Fenster.
    
    2.  Führen Sie den folgenden Befehl aus.
        
            Add-PSSnapin Microsoft.Exchange.Management.PowerShell.SnapIn
    
    3.  Führen Sie die Verwaltungsaufgaben für Transport-Agents wie gewohnt aus.
    
    4.  Wiederholen Sie diese Schritte auf jedem Clientzugriffsserver, der verwaltet werden soll.

## Client-Konnektivität

  - **NTLM-Authentifizierung misslingt bei Clients, die nicht der Domäne beigetreten sind**   Die Authentifizierung zwischen einem Client wie Windows Live Mail und Exchange 2013 kann misslingen, wenn die folgenden Bedingungen vorliegen:
    
      - Die Authentifizierungsmethode, die der Client verwendet, ist NTLM.
    
      - Der Computer ist nicht der Domäne beigetreten.
    
    Um dieses Problem zu umgehen, können Sie eine der folgenden Aufgaben ausführen:
    
      - Lassen Sie den Computer, auf dem der Client ausgeführt wird, der Domäne beitreten.
    
      - Ändern Sie den Authentifizierungstyp des Clients von "NTLM" in "Standardauthentifizierung über TLS".

  - **Die GSSAPI-Authentifizierung schlägt bei Verwendung mit dem Cmdlet "Send-MailMessage" fehl**   Die GSSAPI-Authentifizierung (Generic Security Service Application Program Interface) kann fehlschlagen, wenn das Cmdlet **Send-MailMessage**, das zur Standardinstallation von Windows PowerShell gehört, verwendet wird, um authentifizierte E-Mails an Exchange 2013 zu senden. Wenn dies geschieht, wird im Ereignisprotokoll **Anwendung** auf dem Exchange 2013-Clientzugriffsserver, der die Verbindung empfangen hat, ein Ereignis mit folgenden Informationen angezeigt:
    
      - **Quelle**   MSExchangeFrontEndTransport
    
      - **Ereignis-ID**   1035
    
      - **Beschreibung**   Fehler `IllegalMessage` bei der eingehenden Authentifizierung für den Empfangsconnector "Client-Front-End \<*Servername*\>". Der Authentifizierungsmechanismus ist Gssapi. Die Quell-IP-Adresse des Clients, der die Authentifizierung bei Exchange versucht hat, lautet \[\<*IP-Adresse des Clients*\>\].
    
    Zum Beheben dieses Problems müssen Sie die Authentifizierungsmethode `Integrated` aus dem Clientempfangsconnector für Ihre Exchange 2013-Clientzugriffsserver entfernen. Führen Sie zum Entfernen der Authentifizierungsmethode `Integrated` aus einem Clientempfangsconnector auf allen Exchange 2013-Clientzugriffsservern, die Verbindungen von Computern empfangen können, mithilfe des Cmdlets **Send-MailMessage** den folgenden Befehl aus:
    
        Set-ReceiveConnector "<server name>\Client Frontend <server name>" -AuthMechanism Tls, BasicAuth, BasicAuthRequireTLS

  - **Nach einem Upgrade auf Exchange 2013 SP1 kann es zu einer schlechten Leistung von MAPI über HTTP kommen**   Wenn Sie ein Upgrade von einem kumulativen Update für Exchange 2013 auf Exchange 2013 SP1 durchführen und MAPI über HTTP aktivieren, kann es zu schlechter Leistung kommen, wenn Clients über dieses Protokoll eine Verbindung mit einem Exchange 2013 SP1-Server herstellen. Der Grund dafür ist, dass erforderliche Einstellungen bei einem Upgrade von einem kumulativen Update auf Exchange 2013 SP1 nicht konfiguriert werden. Dieses Problem tritt nicht auf, wenn Sie ein Upgrade von Exchange 2013 RTM auf Exchange 2013 SP1 durchführen oder einen neuen Server mit Exchange 2013 SP1 oder höher installieren.
    

    > [!NOTE]
    > Dies ist nur dann ein Problem, wenn das Protokoll MAPI über HTTP auf Ihren Client Access-Servern aktiviert ist. Es ist standardmäßig deaktiviert. Wenn MAPI über HTTP deaktiviert ist, verwenden Clients stattdessen das Protokoll RPC über HTTP.

    
    Um dieses Problem zu beheben, führen Sie folgende Schritte aus:
    
    1.  Führen Sie auf Servern, auf denen die Clientzugriffs-Serverrolle installiert ist, in einer Windows-Eingabeaufforderung die folgenden Befehle aus:
        
            set AppCmdLocation=%windir%\System32\inetsrv
            set ExchangeLocation=%ProgramFiles%\Microsoft\Exchange Server\V15
            
            %AppCmdLocation%\appcmd.exe SET AppPool "MSExchangeMapiFrontEndAppPool" /CLRConfigFile:"%ExchangeLocation%\bin\MSExchangeMapiFrontEndAppPool_CLRConfig.config"
            %AppCmdLocation%\appcmd.exe RECYCLE AppPool "MSExchangeMapiFrontEndAppPool"
    
    2.  Führen Sie auf Servern, auf denen die Serverrolle Mailbox installiert ist, in einer Windows-Eingabeaufforderung die folgenden Befehle aus:
        
            set AppCmdLocation=%windir%\System32\inetsrv
            set ExchangeLocation=%ProgramFiles%\Microsoft\Exchange Server\V15
            
            %AppCmdLocation%\appcmd.exe SET AppPool "MSExchangeMapiMailboxAppPool" /CLRConfigFile:"%ExchangeLocation%\bin\MSExchangeMapiMailboxAppPool_CLRConfig.config"
            %AppCmdLocation%\appcmd.exe RECYCLE AppPool "MSExchangeMapiMailboxAppPool"
            
            %AppCmdLocation%\appcmd.exe SET AppPool "MSExchangeMapiAddressBookAppPool" /CLRConfigFile:"%ExchangeLocation%\bin\MSExchangeMapiAddressBookAppPool_CLRConfig.config"
            %AppCmdLocation%\appcmd.exe RECYCLE AppPool "MSExchangeMapiAddressBookAppPool"

## Exchange 2010-Koexistenz

  - **Anforderungen für den Zugriff auf Exchange 2010-Postfächer misslingen möglicherweise, wenn sie mittels Proxyweiterleitung durch Exchange 2013-Clientzugriffsserver gesendet werden**   Mitunter funktioniert die Proxyanforderung zwischen den Exchange 2013- und Exchange 2010 Service Pack 3 (SP3)-Clientzugriffsservern ohne die Installation von Updaterollups möglicherweise nicht einwandfrei, und es wird ein Fehler angezeigt. Dieses Problem kann auftreten, wenn alle nachstehenden Bedingungen zutreffen:
    
      - Ein Benutzer mit einem Exchange 2013-Postfach versucht, Exchange 2010-Postfach mit einer der folgenden Methoden zu öffnen:
        
          - mit der Option **Anderes Postfach öffnen** in Outlook Web App**-ODER-**
        
          - mit der Option **Anderer Benutzer** im Exchange Admin Center.
    
      - Auf dem Clientzugriffsserver, mit dem der Benutzer eine Verbindung hergestellt hat, läuft Exchange 2013.
    
      - Der Exchange 2010-Clientzugriffsserver wurde auf Exchange 2010 SP3 aktualisiert aus der RTM-Version (Release to Manufacturing) von Exchange 2010 oder einem früheren Exchange 2010 Service Pack.
    
    Falls alle voranstehenden Bedingungen zutreffen, kann der Benutzer nicht auf die Exchange 2010Outlook Web App-Optionen eines anderen Benutzers zugreifen, und es erscheint ggf. eine leere Seite.
    
    Installieren Sie zum Beheben dieses Problems auf allen Exchange 2010-Servern das Exchange 2010 SP3 Updaterollup 1 oder höher.

