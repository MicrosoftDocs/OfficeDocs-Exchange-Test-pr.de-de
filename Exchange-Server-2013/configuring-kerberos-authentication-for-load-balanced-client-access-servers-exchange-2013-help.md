---
title: 'Konfigurieren der Kerberos-Authentifizierung für Clientzugriffsserver mit Lastenausgleich: Exchange 2013 Help'
TOCTitle: Konfigurieren der Kerberos-Authentifizierung für Clientzugriffsserver mit Lastenausgleich
ms:assetid: 8f4faeea-a825-438d-97dc-1c398ce7aba5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff808312(v=EXCHG.150)
ms:contentKeyID: 62835943
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Kerberos-Authentifizierung für Clientzugriffsserver mit Lastenausgleich

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

**Zusammenfassung:** Beschreibt, wie die Kerberos-Authentifizierung mit Clientzugriffsservern mit Lastenausgleich in Exchange 2013 verwendet wird.

Um die Kerberos-Authentifizierung mit Clientzugriffsservern mit Lastenausgleich verwenden zu können, müssen Sie die folgenden in diesem Artikel beschriebenen Schritte ausführen.

## Erstellen von alternativen Dienstkontoanmeldeinformationen in Active Directory Domain Services

Alle Clientzugriffsserver, die dieselben Namespaces und URLs gemeinsam nutzen, müssen dieselben alternativen Dienstkontoanmeldeinformationen verwenden. Im Allgemeinen ist es ausreichend, über ein einziges Konto für eine Gesamtstruktur für jede Version von Exchange zu verfügen. *Alternative Dienstkontoanmeldeinformationen* oder *ASA-Anmeldeinformationen*.


> [!IMPORTANT]
> Exchange 2010 und Exchange 2013 können nicht dieselben ASA-Anmeldeinformationen gemeinsam nutzen. Sie müssen neue ASA-Anmeldeinformationen für Exchange 2013 erstellen.




> [!IMPORTANT]
> CNAME-Datensätze werden für freigegebene Namespaces zwar unterstützt, Microsoft empfiehlt jedoch die Verwendung von A-Datensätzen. Dadurch wird sichergestellt, dass der Client ordnungsgemäß eine Kerberos-Ticketanforderung basierend auf dem freigegebenen Namen und nicht auf dem Server-FQDN ausstellt.



Wenn Sie die ASA-Anmeldeinformationen einrichten, beachten Sie diese Richtlinien:

  - **Kontotyp.** Sie sollten ein Computerkonto anstelle eines Benutzerkontos erstellen. Ein Computerkonto lässt die interaktive Anmeldung nicht zu und hat möglicherweise einfachere Sicherheitsrichtlinien als ein Benutzerkonto. Wenn Sie ein Computerkonto erstellen, läuft das Kennwort nicht ab, es wird jedoch empfohlen, das Kennwort regelmäßig zu aktualisieren. Sie können eine lokale Gruppenrichtlinie verwenden, um ein Höchstalter für das Computerkonto und Skripts anzugeben, um Computerkonten, die den aktuellen Richtlinien nicht entsprechen, regelmäßig zu löschen. Ihre lokale Sicherheitsrichtlinie bestimmt auch, wann Sie das Kennwort ändern müssen. Obwohl Sie ein Computerkonto verwenden sollten, können Sie auch ein Benutzerkonto erstellen.

  - **Kontoname.** An den Namen des Kontos gibt es keine Anforderungen. Sie können einen beliebigen Namen verwenden, der dem Namensschema entspricht.

  - **Kontogruppe.** Das Konto, das Sie für die ASA-Anmeldeinformationen verwenden, benötigt keine speziellen Sicherheitsberechtigungen. Wenn Sie ein Computerkonto verwenden, muss das Konto nur Mitglied der Sicherheitsgruppe "Domain Computers" sein. Wenn Sie ein Benutzerkonto verwenden, muss das Konto nur Mitglied der Sicherheitsgruppe "Domain Users" sein.

  - **Kontokennwort.** Das von Ihnen beim Erstellen des Kontos bereitgestellte Kennwort wird verwendet. Daher sollten Sie beim Erstellen des Kontos ein komplexes Kennwort verwenden und sicherstellen, dass das Kennwort den Kennwortrichtlinien Ihrer Organisation entspricht.

**So erstellen Sie ASA-Anmeldeinformationen als Computerkonto**

1.  Führen Sie auf einem Computer in der Domäne Windows PowerShell oder die Exchange-Verwaltungshell aus.
    
    Verwenden Sie das **Import-Module**-Cmdlet, um das Active Directory-Modul zu importieren.
    
        Import-Module ActiveDirectory

2.  Verwenden Sie das **New-ADComputer**-Cmdlet, um ein neues Active Directory-Computerkonto mithilfe dieser Cmdlet-Syntax zu erstellen:
    
        New-ADComputer [-Name] <string> [-AccountPassword <SecureString>] [-AllowReversiblePasswordEncryption <System.Nullable[boolean]>] [-Description <string>] [-Enabled <System.Nullable[bool]>]
    
    **Beispiel:**
    
        New-ADComputer -Name EXCH2013ASA -AccountPassword (Read-Host 'Enter password' -AsSecureString) -Description 'Alternate Service Account credentials for Exchange' -Enabled:$True -SamAccountName EXCH2013ASA
    
    Wobei *EXCH2013ASA* der Name des Kontos ist, *Alternative Anmeldeinformationen für ein Dienstkonto für Exchange* eine beliebige Beschreibung ist, und der Wert für den *SamAccountName*-Parameter, in diesem Fall *EXCH2013ASA*, im Verzeichnis eindeutig sein muss.

3.  Verwenden Sie das **Set-ADComputer**-Cmdlet, um mithilfe der folgenden Cmdlet-Syntax die Unterstützung des AES 256-Verschlüsselungsverfahrens zu aktivieren, das von Kerberos verwendet wird:
    
        Set-ADComputer [-Name] <string> [-add @{<attributename>="<value>"]
    
    **Beispiel:**
    
        Set-ADComputer EXCH2013ASA -add @{"msDS-SupportedEncryptionTypes"="28"}
    
    Wobei *EXCH2013ASA* der Name des Kontos ist und das zu änderte Attribut ist *msDS-SupportedEncryptionTypes* mit einem Dezimalwert von 28, der die folgenden Verschlüsselungen ermöglicht: RC4-HMAC, AES128-CTS-HMAC-SHA1-96, AES256-CTS-HMAC-SHA1-96.

Weitere Informationen zu diesen Cmdlets finden Sie unter [Import-Module](https://technet.microsoft.com/de-de/library/hh849725.aspx) und [New-ADComputer](https://technet.microsoft.com/de-de/library/ee617245.aspx).

## Gesamtstrukturübergreifende Szenarios

Bei einer gesamtstrukturübergreifenden oder Ressourcengesamtstruktur-Bereitstellung mit Benutzern außerhalb der Active Directory-Gesamtstruktur, die Exchange enthält, müssen Sie eine Gesamtstruktur-Vertrauensstellung zwischen den Gesamtstrukturen konfigurieren. Außerdem müssen Sie für jede Gesamtstruktur in der Bereitstellung eine Weiterleitungsregel einrichten, die die Vertrauensstellung zwischen allen Namenssuffixes innerhalb der Gesamtstruktur und gesamtstrukturübergreifend aktiviert. Weitere Informationen zum Verwalten von gesamtstrukturübergreifenden Vertrauensstellungen finden Sie unter [Verwalten von Gesamtstruktur-Vertrauensstellungen](https://technet.microsoft.com/de-de/library/cc772440.aspx).

## Identifizieren der zu den ASA-Anmeldeinformationen gehörenden Dienstprinzipalnamen

Nach dem Erstellen von ASA-Anmeldeinformationen müssen Sie den ASA-Anmeldeinformationen Exchange-Dienstprinzipalnamen (SPN) zuordnen. Die Liste der Exchange-SPNs variiert je nach Konfiguration. Sie sollte jedoch mindestens folgende Angaben enthalten:

  - **http/**   Verwenden Sie diesen Dienstprinzipalnamen für Outlook Anywhere, MAPI über HTTP, Exchange-Webdienste, den automatischen Erkennungsdienst von Exchange und Offline Address Book.

Die SPN-Werte müssen dem Dienstnamen im Netzwerklastenausgleich anstatt auf den einzelnen Servern entsprechen. Betrachten Sie die folgenden Szenarios, damit diese Ihnen bei der Planung helfen, welche SPN-Werte verwendet werden sollen:

  - Einzelner Active Directory-Standort

  - Mehrere Active Directory-Standorte

In jedem dieser Szenarien wird angenommen, dass vollqualifizierte Domänennamen (Fully Qualified Domain Name, FQDN) mit Lastenausgleich für die internen URLs, externen URLs und für die AutoErmittlung des internen URIs bereitgestellt wurden, die von Mitgliedern des Clientzugriffsservers verwendet werden. Weitere Informationen finden Sie unter Informationen zur Verwendung als Proxy und Umleitung.

## Einzelner Active Directory-Standort

Wenn Sie einen einzelnen Active Directory-Standort haben, kann Ihre Umgebung der in der folgenden Abbildung entsprechen:

![CAS-Array mit einem AD und Kerberos-Authentifizierung](images/Ff808312.97a1a926-f4ac-4498-bc6b-32e7fb1b70f1(EXCHG.150).jpg "CAS-Array mit einem AD und Kerberos-Authentifizierung")

Basierend auf den FQDNs, die von den internen Outlook-Clients in der Abbildung oben verwendet werden, müssen Sie die folgenden SPNs den ASA-Anmeldeinformationen zuordnen:

  - http/mail.corp.tailspintoys.com

  - http/autodiscover.corp.tailspintoys.com

## Mehrere Active Directory-Standorte

Wenn Sie mehrere Active Directory-Standorte haben, kann Ihre Umgebung der in der folgenden Abbildung entsprechen:

![CAS-Array mit mehreren AD-Standorten und Kerberos-Authentifizierung](images/Ff808312.95b52bd8-7074-4055-8bd2-e6bf1f112b42(EXCHG.150).jpg "CAS-Array mit mehreren AD-Standorten und Kerberos-Authentifizierung")

Basierend auf den FQDNs, die von den Outlook-Clients in der Abbildung oben verwendet werden, müssen Sie die folgenden SPNs den ASA-Anmeldeinformationen zuordnen, die von den Clientzugriffsservern in ADSite 1 verwendet werden:

  - http/mail.corp.tailspintoys.com

  - http/autodiscover.corp.tailspintoys.com

Außerdem müssen Sie die folgenden SPNs den ASA-Anmeldeinformationen zuordnen, die von den Clientzugriffsservern in ADSite 2 verwendet werden:

  - http/mailsdc.corp.tailspintoys.com

  - http/autodiscoversdc.corp.tailspintoys.com

## Konfigurieren und Überprüfen der Konfiguration der ASA-Anmeldeinformationen auf den einzelnen Clientzugriffsservern

Nachdem Sie das Konto erstellt haben, müssen Sie überprüfen, ob das Konto auf alle AD DS-Domänencontroller repliziert wurde. Das Konto muss speziell auf allen Clientzugriffsservern vorhanden sein, die die ASA-Anmeldeinformationen verwenden. Danach konfigurieren Sie das Konto als ASA-Anmeldeinformationen auf den einzelnen Clientzugriffsservern in der Bereitstellung.

Sie konfigurieren die ASA-Anmeldeinformationen mithilfe der Exchange-Verwaltungsshell, wie in einer dieser Verfahrensweisen beschrieben wird:

  - Bereitstellen der ASA-Anmeldeinformationen für den ersten Exchange 2013-Clientzugriffsserver

  - Bereitstellen der ASA-Anmeldeinformationen an nachfolgende Exchange 2013-Clientzugriffsserver

Die einzige unterstützte Methode für die Bereitstellung der ASA-Anmeldeinformationen ist die Verwendung des Skripts RollAlternateServiceAcountPassword.ps1. Weitere Informationen finden Sie unter [Verwenden des Skripts "RollAlternateserviceAccountCredential.ps1" in der Shell](using-the-rollalternateserviceaccountcredential-ps1-script-in-the-shell-exchange-2013-help.md). Nach der Ausführung des Skripts sollten Sie überprüfen, ob alle Zielserver ordnungsgemäß aktualisiert wurden.

## Bereitstellen der ASA-Anmeldeinformationen für den ersten Exchange 2013-Clientzugriffsserver

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Exchange 2013-Server.

2.  Wechseln Sie zum Verzeichnis *\<Exchange 2013-Installationsverzeichnis\>*\\V15\\Scripts.

3.  Führen Sie den folgenden Befehl aus, um die ASA-Anmeldeinformationen für den ersten Exchange 2013-Clientzugriffsserver bereitzustellen:
    
        .\RollAlternateServiceAccountPassword.ps1 -ToSpecificServer cas-1.corp.tailspintoys.com -GenerateNewPasswordFor tailspin\EXCH2013ASA$

4.  Wenn Sie gefragt werden, ob Sie das Kennwort für das alternative Dienstkonto ändern möchten, antworten Sie **Ja**.

Im Folgenden finden Sie ein Beispiel der Ausgabe, die beim Ausführen des Skripts RollAlternateServiceAccountPassword.ps1 angezeigt wird.

    ========== Starting at 01/12/2015 10:17:47 ==========
    Creating a new session for implicit remoting of "Get-ExchangeServer" command...
    Destination servers that will be updated:
    
    Name                                                        PSComputerName
    ----                                                        --------------
    cas-1                                                   cas-1.corp.tailspintoys.com
    
    
    Credentials that will be pushed to every server in the specified scope (recent first):
    
    UserName                                                                                                        
    Password
    --------                                                                                                        
    --------
    tailspin\EXCH2013ASA$                                                                             
    System.Security.SecureString
    
    
    Prior to pushing new credentials, all existing credentials that are invalid or no longer work will be removed from  the destination servers.
    Pushing credentials to server cas-1
    Setting a new password on Alternate Serice Account in Active Directory
    
    Password change
    Do you want to change password for tailspin\EXCH2013ASA$ in Active Directory at this time?
    [Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
    Preparing to update Active Directory with a new password for tailspin\EXCH2013ASA$ ...
    Resetting a password in the Active Directory for tailspin\EXCH2013ASA$ ...
    New password was successfully set to Active Directory.
    Retrieving the current Alternate Service Account configuration from servers in scope
    Alternate Service Account properties:
    
    StructuralObjectClass QualifiedUserName Last Pwd Update       SPNs
    --------------------- ----------------- ---------------       ----
    computer              tailspin\EXCH2013ASA$   1/12/2015 10:19:53 AM
    
    Per-server Alternate Service Account configuration as of the time of script completion:
    
    
       Array: {mail.corp.tailspintoys.com}
    
    Identity  AlternateServiceAccountConfiguration
    --------  ------------------------------------
    cas-1 Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
              ...
    
    ========== Finished at 01/12/2015 10:20:00 ==========
    
            THE SCRIPT HAS SUCCEEDED

## Bereitstellen der ASA-Anmeldeinformationen an einen weiteren Exchange 2013-Clientzugriffsserver

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Exchange 2013-Server.

2.  Wechseln Sie zum Verzeichnis *\<Exchange 2013-Installationsverzeichnis\>*\\V15\\Scripts.

3.  Führen Sie den folgenden Befehl aus, um die ASA-Anmeldeinformationen für einen weiteren Exchange 2013-Clientzugriffsserver bereitzustellen:
    
        .\RollAlternateServiceAccountPassword.ps1 -ToSpecificServer cas-2.corp.tailspintoys.com -CopyFrom cas-1.corp.tailspintoys.com

4.  Wiederholen Sie Schritt 3 für jeden Clientzugriffsserver, für den Sie die ASA-Anmeldeinformationen bereitstellen möchten.

Im Folgenden finden Sie ein Beispiel der Ausgabe, die beim Ausführen des Skripts RollAlternateServiceAccountPassword.ps1 angezeigt wird.

    ========== Starting at 01/12/2015 10:34:35 ==========
    Destination servers that will be updated:
    
    Name                                                        PSComputerName
    ----                                                        --------------
    cas-2                                                   cas-2.corp.tailspintoys.com
    
    
    Credentials that will be pushed to every server in the specified scope (recent first):
    
    UserName                                                                                                        
    Password
    --------                                                                                                        
    --------
    tailspin\EXCH2013ASA$                                                                             
    System.Security.SecureString
    
    Prior to pushing new credentials, all existing credentials will be removed from the destination servers.
    Pushing credentials to server cas-2
    Retrieving the current Alternate Service Account configuration from servers in scope
    Alternate Service Account properties:
    
    StructuralObjectClass QualifiedUserName Last Pwd Update       SPNs
    --------------------- ----------------- ---------------       ----
    computer              tailspin\EXCH2013ASA$   1/12/2015 10:19:53 AM
    
    Per-server Alternate Service Account configuration as of the time of script completion:
    
    
       Array: cas-2.corp.tailspintoys.com
    
    Identity  AlternateServiceAccountConfiguration
    --------  ------------------------------------
    cas-2 Latest: 1/12/2015 10:37:59 AM, tailspin\EXCH2013ASA$
              ...
    
    
    ========== Finished at 01/12/2015 10:38:13 ==========
    
            THE SCRIPT HAS SUCCEEDED

## Überprüfen der Bereitstellung von ASA-Anmeldeinformationen

  - Öffnen Sie die Exchange-Verwaltungsshell auf einem Exchange 2013-Server.

  - Führen Sie den folgenden Befehl aus, um die Einstellungen auf einem Clientzugriffsserver zu überprüfen:
    
        Get-ClientAccessServer CAS-3 -IncludeAlternateServiceAccountCredentialStatus | Format-List Name, AlternateServiceAccountConfiguration

  - Wiederholen Sie Schritt 2 für jeden Clientzugriffsserver, auf dem Sie die Bereitstellung von ASA-Anmeldeinformationen überprüfen möchten.

Im Folgenden finden Sie ein Beispiel der Ausgabe, die angezeigt wird, wenn Sie den obigen Get-ClientAccessServer-Befehl ausführen und keine früheren ASA-Anmeldeinformationen festgelegt wurden.

    Name                                 : CAS-1
    AlternateServiceAccountConfiguration : Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
                                           Previous: <Not set>
                                               ...

Im Folgenden finden Sie ein Beispiel der Ausgabe, die angezeigt wird, wenn Sie den obigen Get-ClientAccessServer-Befehl ausführen und frühere ASA-Anmeldeinformationen festgelegt wurden. Die früheren ASA-Anmeldeinformationen und das Datum und die Uhrzeit, zu denen sie festgelegt wurden, werden zurückgegeben.

    Name                                 : CAS-3
    AlternateServiceAccountConfiguration : Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
                                           Previous: 7/15/2014 12:58:35 PM, tailspin\oldSharedServiceAccountName$
                                               ...

## Zuordnen von Dienstprinzipalnamen (Service Principal Names, SPNs) zu den ASA-Anmeldeinformationen


> [!IMPORTANT]
> Ordnen Sie SPNs erst dann ASA-Anmeldeinformationen zu, wenn Sie diese Anmeldeinformationen mindestens einen Exchange Server bereitgestellt haben, wie zuvor unter Bereitstellen der ASA-Anmeldeinformationen für den ersten Exchange 2013-Clientzugriffsserver beschrieben. Andernfalls treten Kerberos-Authentifizierungsfehler auf.



Bevor Sie die SPNs den ASA-Anmeldeinformationen zuordnen, müssen Sie sicherstellen, dass die Ziel-SPNs noch keinem anderen Konto in der Gesamtstruktur zugeordnet sind. Die ASA-Anmeldeinformationen müssen das einzige Konto in der Gesamtstruktur darstellen, denen diese SPNs zugeordnet sind. Sie können überprüfen, ob einem anderen Konto in der Gesamtstruktur die SPNs zugeordnet sind, indem Sie den **setspn**-Befehl an der Befehlszeile ausführen.

**Überprüfen Sie durch Ausführen des Befehls "setspn", ob bereits ein SPN einem Konto in einer Gesamtstruktur zugeordnet ist**

1.  Klicken Sie auf **Start**. Geben Sie im Feld **Suchen** das Wort **Eingabeaufforderung** ein, und wählen Sie dann in der Ergebnisliste **Eingabeaufforderung** aus.

2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:
    
        setspn -F -Q <SPN>
    
    Wobei \<SPN\> der Dienstprinzipalname ist, den Sie den ASA-Anmeldeinformationen zuordnen möchten. Beispiel:
    
        setspn -F -Q http/mail.corp.tailspintoys.com
    
    Der Befehl sollte nichts zurückgeben. Wenn er etwas zurückgibt, ist bereits ein anderes Konto dem SPN zugeordnet. Wiederholen Sie diesen Schritt einmal für jeden SPN, den Sie den ASA-Anmeldeinformationen zuordnen möchten.

**Zuordnen eines SPN zu den ASA-Anmeldeinformationen mithilfe des Befehls "setspn"**

1.  Klicken Sie auf **Start**. Geben Sie im Feld **Suchen** das Wort **Eingabeaufforderung** ein, und wählen Sie dann in der Ergebnisliste **Eingabeaufforderung** aus.

2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:
    
        setspn -S <SPN> <Account>$
    
    Wobei \<SPN\> der Dienstprinzipalname ist, den Sie den ASA-Anmeldeinformationen zuordnen möchten, und \<Account\> das Konto ist, das den ASA-Anmeldeinformationen zugeordnet ist. Beispiel:
    
        setspn -S http/mail.corp.tailspintoys.com tailspin\EXCH2013ASA$
    
    Führen Sie diesen Befehl einmal für jeden SPN aus, den Sie den ASA-Anmeldeinformationen zuordnen möchten.

**Überprüfen mithilfe des Befehls "setspn", ob Sie die SPNs den ASA-Anmeldeinformationen zugeordnet haben**

1.  Klicken Sie auf **Start**. Geben Sie im Feld **Suchen** das Wort **Eingabeaufforderung** ein, und wählen Sie dann in der Ergebnisliste **Eingabeaufforderung** aus.

2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:
    
        setspn -L <Account>$
    
    Wobei \<Account\> das Konto ist, das den ASA-Anmeldeinformationen zugeordnet ist. Beispiel:
    
        setspn -L tailspin\EXCH2013ASA$
    
    Diesen Befehl müssen Sie nur einmal ausführen.

## Aktivieren der Kerberos-Authentifizierung für Outlook-Clients

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Exchange 2013-Server.

2.  Führen Sie den folgenden Befehl auf dem Clientzugriffsserver aus, um die Kerberos-Authentifizierung für Outlook Anywhere-Clients zu aktivieren:
    
        Get-OutlookAnywhere -server CAS-1 | Set-OutlookAnywhere -InternalClientAuthenticationMethod  Negotiate

3.  Führen Sie Folgendes auf Ihrem Exchange 2013-Clientzugriffsserver aus, um die Kerberos-Authentifizierung für MAPI über HTTP-Clients zu aktivieren:
    
        Get-MapiVirtualDirectory -Server CAS-1 | Set-MapiVirtualDirectory -IISAuthenticationMethods Ntlm, Negotiate

4.  Wiederholen Sie die Schritte 2 und 3 für jeden Exchange 2013 Clientzugriffsserver, auf dem Sie die Kerberos-Authentifizierung aktivieren möchten.

## Überprüfen der Kerberos-Authentifizierung des Exchange-Clients

Nachdem Sie Kerberos und die ASA-Anmeldeinformationen erfolgreich konfiguriert haben, überprüfen Sie, ob sich Clients wie in diesen Aufgaben beschrieben authentifizieren können.

## Überprüfen, ob der Microsoft Exchange-Diensthost ausgeführt wird

Der Dienst "Microsoft Exchange-Diensthost" (MSExchangeServiceHost) auf den Clientzugriffsservern ist für die Verwaltung der ASA-Anmeldeinformationen zuständig. Wenn dieser Dienst nicht ausgeführt wird, kann die Kerberos-Authentifizierung nicht verwendet werden. Der Dienst ist standardmäßig so konfiguriert, dass er automatisch beim Start des Computers gestartet wird.

**So überprüfen Sie, ob der Microsoft Exchange-Diensthost ausgeführt wird**

1.  Klicken Sie auf **Start**, geben Sie **services.msc** ein, und wählen Sie dann **services.msc** in der Liste aus.

2.  Suchen Sie im Fenster **Dienste** den Dienst **Microsoft Exchange-Diensthost** in der Liste der Dienste.

3.  Der Status des Diensts sollte **Gestartet** lauten. Wenn der Status nicht **Gestartet** lautet, klicken Sie mit der rechten Maustaste auf den Dienst, und klicken Sie dann auf **Starten**.

## Überprüfen von Kerberos vom Clientzugriffsserver

Wenn Sie die ASA-Anmeldeinformationen auf den einzelnen Clientzugriffsservern konfiguriert haben, haben Sie das **set-ClientAccessServer**-Cmdlet ausgeführt. Sobald Sie dieses Cmdlet ausgeführt haben, können Sie die Protokolle verwenden, um erfolgreiche Kerberos-Verbindungen zu überprüfen.

**So überprüfen Sie mithilfe der HttpProxy-Protokolldatei, ob Kerberos ordnungsgemäß funktioniert**

1.  Wechseln Sie in einem Text-Editor zu dem Ordner, in dem das HttpProxy-Protokoll gespeichert ist. Standardmäßig befindet sich das Protokoll im folgenden Ordner:
    
    %ExchangeInstallPath%\\Logging\\HttpProxy\\RpcHttp

2.  Öffnen Sie die neueste Protokolldatei, und suchen Sie das Wort **Negotiate**. Die Zeile in der Protokolldatei sollte der folgenden ähneln:
    
        2014-02-19T13:30:49.219Z,e19d08f4-e04c-42da-a6be-b7484b396db0,15,0,775,22,,RpcHttp,mail.corp.tailspintoys.com,/rpc/rpcproxy.dll,,Negotiate,True,tailspin\Wendy,tailspintoys.com,MailboxGuid~ad44b1e0-e44f-4a16-9396-3a437f594f88,MSRPC,192.168.1.77,EXCH1,200,200,,RPC_OUT_DATA,Proxy,exch2.tailspintoys.com,15.00.0775.000,IntraForest,MailboxGuidWithDomain,,,,76,462,1,,1,1,,0,,0,,0,0,16272.3359,0,0,3,0,23,0,25,0,16280,1,16274,16230,16233,16234,16282,?ad44b1e0-e44f-4a16-9396-3a437f594f88@tailspintoys.com:6001,,BeginRequest=2014-02-19T13:30:32.946Z;BeginGetRequestStream=2014-02-19T13:30:32.946Z;OnRequestStreamReady=2014-02-19T13:30:32.946Z;BeginGetResponse=2014-02-19T13:30:32.946Z;OnResponseReady=2014-02-19T13:30:32.977Z;EndGetResponse=2014-02-19T13:30:32.977Z;,PossibleException=IOException;
    
    Wenn Sie feststellen, dass der Wert von **AuthenticationTypeNegotiate** ist, erstellt der Server erfolgreich von Kerberos authentifizierte Verbindungen.

## Beibehalten der ASA-Anmeldeinformationen

Wenn Sie das Kennwort für die ASA-Anmeldeinformationen regelmäßig aktualisieren müssen, verwenden Sie die Schritte für das Konfigurieren der ASA-Anmeldeinformationen in diesem Artikel. Sie können auch eine geplante Aufgabe einrichten, um das Kennwort regelmäßig zu warten. Stellen Sie sicher, dass die geplante Aufgabe für die rechtzeitigen Kennwortrollover überwacht wird und mögliche Authentifizierungsausfälle verhindert werden.

## Deaktivieren der Kerberos-Authentifizierung

Um den Clientzugriffsserver so zu konfigurieren, dass Kerberos nicht verwendet wird, trennen oder entfernen Sie die SPNs von den ASA-Anmeldeinformationen. Nach dem Entfernen der SPNs versuchen die Clients keine Kerberos-Authentifizierung, und Clients, für die die Negotiate-Authentifizierung konfiguriert ist, verwenden stattdessen NTLM. Clients, für die ausschließlich die Verwendung von Kerberos konfiguriert ist, können keine Verbindung herstellen. Nach dem Entfernen der SPNs sollten Sie auch das Konto löschen.

**So entfernen die ASA-Anmeldeinformationen**

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Exchange 2013-Server, und führen Sie den folgenden Befehl aus:
    
        Set-ClientAccessServer CAS-1 -RemoveAlternateServiceAccountCredentials

2.  Obwohl dies nicht sofort erforderlich ist, sollten Sie alle Clientcomputer neu starten, um den Kerberos-Ticketcache von den Computern zu löschen.

