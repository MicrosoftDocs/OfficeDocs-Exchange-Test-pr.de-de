---
title: 'Konfigurieren von Proxyfunktionen für Pushbenachrichtigungen in OWA for Devices: Exchange 2013 Help'
TOCTitle: Konfigurieren von Proxyfunktionen für Pushbenachrichtigungen in OWA for Devices
ms:assetid: c0f4912d-8bd3-4a54-9097-03619c645c6a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn511017(v=EXCHG.150)
ms:contentKeyID: 59954258
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Proxyfunktionen für Pushbenachrichtigungen in OWA for Devices

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Durch das Aktivieren von Pushbenachrichtigungen für OWA für Geräte (OWA für iPhone und OWA für iPad) einer lokalen Bereitstellung von Microsoft Exchange 2013 kann der Benutzer Updates für das Outlook Web App-Symbol in OWA für iPhone und OWA für iPad empfangen, sodass es die Anzahl ungelesener Nachrichten im Posteingang des Benutzers anzeigt. Wenn Pushbenachrichtigungen nicht konfiguriert und aktiviert sind, ist ein OWA für Geräte-Benutzer nicht in der Lage, ungelesene Nachrichten in seinem Posteingang zu erkennen, ohne die App zu starten. Wenn eine neue Nachricht verfügbar ist, wird das OWA für Geräte-Badge auf dem Gerät des Benutzers aktualisiert und sieht folgendermaßen aus.

![OWA for Devices Badge](images/Dn511017.f399ba74-5395-4d24-ae7d-d16bf0ac7b35(EXCHG.150).png "OWA for Devices Badge")

## Wie aktivieren Sie Pushbenachrichtigungen?

Um Pushbenachrichtigungen zu aktivieren, müssen sich die lokalen Exchange 2013-Server mit dem Office 365-Pushbenachrichtigungsdienst verbinden, um Pushbenachrichtigungen an iPhones und iPads senden zu können. Lokale Exchange 2013-Server leiten ihre Updatebenachrichtigungen über die Office 365-Benachrichtigungsdienste weiter, damit keine Entwicklerkonten für Pushbenachrichtigungsdienste von Drittanbietern erforderlich sind. Im folgenden Diagramm wird aufgezeigt, wie der Prozess zum Abrufen von Badge-Updates zum Anzeigen neuer Nachrichten für das iPhone und iPad funktioniert.

![Prozess für Pushbenachrichtigungen](images/Dn511017.36764ce6-7351-492f-a17e-c42b781e2781(EXCHG.150).jpg "Prozess für Pushbenachrichtigungen")

Um Push-Benachrichtigungen zu aktivieren, muss der Administrator:

1.  Registrieren Sie Ihre Organisation in Office 365 für Unternehmen.

2.  Aktualisieren Sie alle lokalen Server auf die Version Exchange Server 2013 Kumulatives Update 3 (CU3) oder höher.

3.  Einrichten von lokalen Exchange 2013 auf Office 365-Authentifizierung

4.  Aktivieren Sie Pushbenachrichtigungen von den lokalen Exchange Server 2013 auf Office 365 und stellen Sie überprüfen Sie sie auf ihre Funktion.

## Registrieren Sie Ihre Organisation in Office 365 für Unternehmen

Office 365 ist ein cloudbasierter Dienst, der dabei helfen soll, die Anforderungen Ihrer Organisation im Hinblick auf hohe Sicherheit, Zuverlässigkeit und Benutzerproduktivität zu erfüllen. Office 365 verweist auf Abonnementpläne, zu deren Funktionsumfang der Zugriff auf Office-Anwendungen und weitere Produktivitätsdienste gehört, die über das Internet (Clouddienste) aktiviert werden, z. B. Lync Webkonferenzen und Exchange Online Gehostete E-Mail-Dienste für Unternehmen.

Viele Office 365-Pläne enthalten außerdem die Desktopversion der neuesten Office-Anwendungen, die Benutzer auf mehreren Computern und Geräten installieren können. Alle Office 365-Pläne können auf Abonnementbasis monatlich oder jährlich bezogen werden. Weitere Informationen zur Registrierung in Office 365 für Ihre Organisation finden Sie unter [Was ist Office 365 für Unternehmen?](http://go.microsoft.com/fwlink/?linkid=335705). Weitere Informationen zu den über Office 365 angebotenen Diensten finden Sie unter [Office 365-Dienstbeschreibungen](http://go.microsoft.com/fwlink/?linkid=335704).

## Aktualisieren Sie auf CU3 oder höher

Das kumulative Update 3 (CU3) für Exchange Server 2013 behebt Probleme, die in Exchange Server 2013 seit Veröffentlichung der RTM gefunden wurden. Es enthält alle Korrekturen von CU1 und CU2 sowie weitere Korrekturen und Aktualisierungen, die seit Veröffentlichung von CU2 bereitgestellt wurden. Dieses Update wird dringend für alle Kunden empfohlen, die einen lokalen Exchange Server 2013 einsetzen, außerdem ist es für Pushbenachrichtigungen erforderlich. Kumulative Updates, einschließlich CU3, Informationen finden Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md).

## Einrichten von lokalen Exchange 2013 auf Office 365-Authentifizierung

Der Einsatz einer einzelnen, standardisierten Methode für die Server-zu-Server-Authentifizierung ist die von Exchange Server 2013 verwendete Herangehensweise. [Exchange Server 2013](http://go.microsoft.com/fwlink/?linkid=290946) (und [Lync Server 2013](http://go.microsoft.com/fwlink/?linkid=273796) und [SharePoint 2013](http://go.microsoft.com/fwlink/?linkid=335701)) und [Office 2013](http://go.microsoft.com/fwlink/?linkid=335696) unterstützen das OAuth-Protokoll (Offene Authorisierung) zur Server-zu-Server-Authentifizierung und Autorisierung. OAuth ist ein Standard-Autorisierungsprotokoll, das von einigen großen Websites verwendet wird, bei dem Benutzeranmeldeinformationen und Kennwörter nicht von einem Computer an einen anderen übergeben werden. Stattdessen basieren Authentifizierung und Autorisierung auf den OAuth-Sicherheitstoken; diese Token gewähren für einen bestimmten Zeitraum den Zugriff auf einen bestimmten Satz an Ressourcen.

OAuth-Authentifizierung umfasst normalerweise drei Komponenten: einen Server mit Einzelanmeldung und zwei Bereiche, die miteinander kommunizieren müssen. Sicherheitstoken werden vom Authorisierungsserver (auch als Sicherheitstokenserver bezeichnet) an die zwei Bereiche ausgegeben, die kommunizieren müssen; diese Token prüfen, ob die Kommunikation des einen Bereichs für den anderen Bereich vertrauenswürdig ist. Der Authorisierungsserver kann beispielsweise Token ausgeben, die prüfen, ob Benutzer von einem bestimmten Bereich von Lync Server 2013 auf einen bestimmten Bereich von Exchange 2013 zugreifen können und umgekehrt.


> [!TIP]
> Ein Bereich ist ein Container für die Sicherheit.



Bei der lokalen Server-zu-Server-Authentifizierung ist jedoch kein Tokenserver eines Drittanbieters erforderlich. Serverprodukte wie Lync Server 2013 und Exchange 2013 verfügen über einen integrierten Tokenserver, der zu Authentifizierungszwecken mit anderen Microsoft-Servern (z. B. SharePoint-Server) verwendet werden kann, die die Server-zu-Server-Authentifizierung unterstützen. Lync Server 2013 kann beispielsweise alleine ein Sicherheitstoken ausgeben und signieren, sowie dieses Token anschließend zum Kommunizieren mit Exchange 2013 einsetzen. In diesem Fall ist kein Tokenserver eines Drittanbieters erforderlich.

Um eine Server-zu-Server-Authentifizierung für eine lokale Implementierung von Exchange Server 2013 auf Office 365 konfigurieren zu können, müssen Sie zwei Schritte durchführen:

  -  
    **Schritt 1 – Weisen Sie dem integrierten Aussteller des Tokens des lokalen Exchange Servers ein Zertifikat zu.** Zunächst muss der lokale Exchange-Administrator zum Erstellen eines Zertifikats folgendes Exchange-Verwaltungsshellskript verwenden, falls noch keines erstellt wurde und es dem Aussteller des integrierten Tokens des lokalen Exchange Servers zuweisen. Hierbei handelt es sich um einen einmaligen Prozess; nachdem das Zertifikat erstellt wurde, sollte das Zertifikat erneut für weitere Authentifizierungsszenarios verwendet und nicht ersetzt werden. Stellen Sie sicher, den Wert der *$tenantDomain* entsprechend des Namens Ihrer Domäne zu aktualisieren. Dazu kopieren Sie und fügen Sie den folgenden Code ein.
    

    > [!WARNING]
    > Kopieren und Fügen Sie den Code in einen Text-Editor wie Notepad ein, speichern Sie die Datei dann mit der Erweiterung .PS1, so wird das Ausführen von Shellskripts vereinfacht.

    
        # Make sure to update the following $tenantDomain with your Office 365 tenant domain.
        
        $tenantDomain = "Fabrikam.com"
        
        # Check whether the cert returned from Get-AuthConfig is valid and keysize must be >= 2048
        
        $c = Get-ExchangeCertificate | ?{$_.CertificateDomains -eq $env:USERDNSDOMAIN -and $_.Services -ge "SMTP" -and $_.PublicKeySize -ge 2048 -and $_.FriendlyName -match "OAuth"}
        If ($c.Count -eq 0)
        {
            Write-Host "Creating certificate for oAuth..."
            $ski = [System.Guid]::NewGuid().ToString("N")
            $friendlyName = "Exchange S2S OAuth"
            New-ExchangeCertificate -FriendlyName $friendlyName -DomainName $env:USERDNSDOMAIN -Services Federation -KeySize 2048 -PrivateKeyExportable $true -SubjectKeyIdentifier $ski
            $c = Get-ExchangeCertificate | ?{$_.friendlyname -eq $friendlyName}
        }
        ElseIf ($c.Count -gt 1)
        {
            $c = $c[0]
        }
        
        $a = $c | ?{$_.Thumbprint -eq (get-authconfig).CurrentCertificateThumbprint}
        If ($a.Count -eq 0)
        {
            Set-AuthConfig -CertificateThumbprint $c.Thumbprint
        }
        Write-Host "Configured Certificate Thumbprint is:"(get-authconfig).CurrentCertificateThumbprint
        
        # Export the certificate
        
        Write-Host "Exporting certificate..."
        if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
        {
            md $env:SYSTEMDRIVE\OAuthConfig
        }
        cd $env:SYSTEMDRIVE\OAuthConfig
        
        $oAuthCert = (dir Cert:\LocalMachine\My) | where {$_.FriendlyName -match "OAuth"}
        $certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
        $certBytes = $oAuthCert.Export($certType)
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        [System.IO.File]::WriteAllBytes($CertFile, $certBytes)
        
        # Set AuthServer
        $authServer = Get-AuthServer MicrosoftSts;
        if ($authServer.Length -eq 0)
        {
            Write-Host "Creating AuthServer Config..."
            New-AuthServer MicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain
        }
        elseif ($authServer.AuthMetadataUrl -ne "https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain")
        {
            Write-Warning "AuthServer config already exists but the AuthMetdataUrl doesn't match the appropriate value. Updating..."
            Set-AuthServer MicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain
        }
        else
        {
            Write-Host "AuthServer Config already exists."
        }
        Write-Host "Complete."
    
    Das erwartete Ergebnis sollte der folgenden Ausgabe ähnlich sein.
    
        Configured Certificate Thumbprint is: 7595DBDEA83DACB5757441D44899BCDB9911253C
        Exporting certificate...
        Complete.
    

    > [!WARNING]
    > Bevor Sie fortfahren, sind die Cmdlets Azure Active Directory-Modul für Windows PowerShell erforderlich. Wenn die Cmdlets Azure Active Directory-Modul für Windows PowerShell (früher bekannt als Microsoft Online Services-Modul für Windows PowerShell) nicht installiert wurden, können Sie sie unter <A href="http://aka.ms/aadposh">Verwalten von Azure AD mit Windows PowerShell</A> herunterladen.



  -  
    **Schritt 2 – Konfigurieren von Office 365 zum Kommunizieren mit lokalem Exchange 2013.** Den Office 365-Server so konfigurieren, dass er als Partneranwendung mit Exchange Server 2013 kommuniziert. Wenn beispielsweise ein lokaler Exchange Server 2013 mit Office 365 kommuniziert, müssen Sie den lokalen Exchange-Server als Partneranwendung konfigurieren. Bei einer Partneranwendung handelt es sich um eine Anwendung, die direkt Sicherheitstoken mit Exchange 2013 austauscht, ohne dafür einen Sicherheitstokenserver eines Drittanbieters verwenden zu müssen. Ein Administrator eines lokalen Exchange 2013-Servers muss folgendes Exchange-Verwaltungsshellskript verwenden, um den Office 365-Mandanten so zu konfigurieren, dass als Partneranwendung mit Exchange 2013 kommuniziert. Während der Ausführung erscheint eine Aufforderung zur Eingabe des Administrator-Benutzernamens und des Kennworts der Office 365-Mandantendomäne—z. B. administrator@fabrikam.com. Stellen Sie sicher, den Wert der *$CertFile* auf den Speicherort des Zertifikats zu aktualisieren, falls dies noch nicht mit dem vorherigen Skript geschehen ist. Dazu kopieren Sie und fügen Sie den folgenden Code ein.
    
        # Make sure to update the following $CertFile with the path to the cert if not using the previous script.
        
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        
        If (Test-Path $CertFile)
        {
            $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
        
            $objFSO = New-Object -ComObject Scripting.FileSystemObject;
            $CertFile = $objFSO.GetAbsolutePathName($CertFile);
        
            $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
            $cer.Import($CertFile);
            $binCert = $cer.GetRawCertData();
            $credValue = [System.Convert]::ToBase64String($binCert);
        
            Write-Host "Please enter the administrator user name and password of the Office 365 tenant domain..."
        
            Connect-MsolService;
            Import-Module msonlineextended;
        
            Write-Host "Adding a key to Service Principal..."
        
            $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
            New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue -StartDate $cer.GetEffectiveDateString() -EndDate $cer.GetExpirationDateString()
        }
        Else
        {
            Write-Error "Cannot find certificate."
        } 
    
    Das erwartete Ergebnis sollte wie folgt aussehen.
    
        Please enter the administrator user name and password of the Office 365 tenant domain...
        Adding a key to Service Principal...
        Complete.

## Aktivieren der Proxyfunktion für Pushbenachrichtigungen

Nachdem die OAuth-Authentifizierung erfolgreich mit den zuvor erläuterten Schritten eingerichtet wurde, muss ein lokaler Administrator die Proxyfunktion für Pushbenachrichtigungen mit folgendem Skript aktivieren. Stellen Sie sicher, den Wert der *$tenantDomain* entsprechend des Namens Ihrer Domäne zu aktualisieren. Dazu kopieren Sie und fügen Sie den folgenden Code ein.

    $tenantDomain = "Fabrikam.com"
    Enable-PushNotificationProxy -Organization:$tenantDomain

Das erwartete Ergebnis sollte der folgenden Ausgabe ähnlich sein.

    RunspaceId        : 4f2eb5cc-b696-482f-92bb-5b254cd19d60
    DisplayName       : On Premises Proxy app
    Enabled           : True
    Organization      : fabrikam.com
    Uri               : https://outlook.office365.com/PushNotifications
    Identity          : OnPrem-Proxy
    IsValid           : True
    ExchangeVersion   : 0.20 (15.0.0.0)
    Name              : OnPrem-Proxy
    DistinguishedName : CN=OnPrem-Proxy,CN=Push Notifications Settings,CN=First Organization,CN=Microsoft
                        Exchange,CN=Services,CN=Configuration,DC=Domain,DC=extest,DC=microsoft,DC=com
    Guid              : 8b567958-58a4-403c-a8f0-524d7f1e9279
    ObjectCategory    : fabrikam.com/Configuration/Schema/ms-Exch-Push-Notifications-App
    ObjectClass       : {top, msExchPushNotificationsApp}
    WhenChanged       : 8/27/2013 7:23:47 PM
    WhenCreated       : 8/14/2013 1:30:27 PM
    WhenChangedUTC    : 8/28/2013 2:23:47 AM
    WhenCreatedUTC    : 8/14/2013 8:30:27 PM
    OrganizationId    :
    OriginatingServer : server.fabrikam.com
    ObjectState       : Unchanged

## Prüfen Sie die Pushbenachrichtigungen

Nachdem Sie die zuvor aufgeführten Schritte abgeschlossen haben, können Sie die Pushbenachrichtigungsfunktion folgendermaßen testen:

  - **Senden einer e-Mail-Testnachricht an das Postfach des Benutzers:** 
    
    1.  Richten Sie auf einem mobilen Gerät ein Konto in OWA for Devices ein, um die Benachrichtigungen zu abonnieren.
    
    2.  Kehren Sie auf den Startbildschirm des Geräts zurück, sodass OWA for Devices in den Hintergrund verschoben wird.
    
    3.  Senden Sie eine E-Mail-Nachricht von einem anderen Gerät, z. B. einem PC, die an den Posteingang des auf dem mobilen Gerät eingerichteten Kontos gesendet wird.
    
    4.  In einigen Augenblicken sollte am App-Symbol eine Anzahl ungelesener Nachrichten angezeigt werden.

  - **Aktivieren der Überwachung.** Hierbei handelt es sich um eine alternative Methode zum Testen von Pushbenachrichtigungen oder zum Untersuchen der Fehlerursache, falls keine Benachrichtigungen ankommen. Darüber wird die Überwachung eines Postfachservers in Ihrer Organisation aktiviert. Der Administrator eines lokalen Exchange 2013-Servers muss die Proxyüberwachung für Pushbenachrichtigungen mit folgendem Skript aufrufen. Dazu kopieren Sie und fügen Sie den folgenden Code ein.
    
        # Send a push notification to verify connectivity.
        
        $s = Get-ExchangeServer | ?{$_.ServerRole -match "Mailbox"}
        If ($s.Count -gt 1)
        {
            $s = $s[0]
        }
        If ($s.Count -ne 0)
        {
            # Restart the monitoring service to clear the cache from when push was previously disabled.
            Restart-Service MSExchangeHM
        
            # Give the monitoring service enough time to load.
            Start-Sleep -Seconds:120
        
            Invoke-MonitoringProbe PushNotifications.Proxy\PushNotificationsEnterpriseConnectivityProbe -Server:$s.Fqdn | fl ResultType, Error, Exception
        }
        Else
        {
            Write-Error "Cannot find a Mailbox server in the current site."
        }
    
    Das erwartete Ergebnis sollte der folgenden Ausgabe ähnlich sein.
    
        ResultType : Succeeded
        Error      :
        Exception  :

